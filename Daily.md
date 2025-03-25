# 250325
## 주요내역
### Project07_360Panorama
#### ImageSlider.cs 수정
- StreamingAssets 경로에서 특정 이미지들을 순차적으로 호출
- 불러온 이미지 개수 만큼 Content Width 조절하여 Slide 가능하게
- 특정 Button 클릭 시 경로 변경하여 이미지 전체 수정 및 이미지에 할당된 Transform 모두 수정
```
using UnityEngine;
using UnityEngine.UI;
using System.Collections;
using System.Collections.Generic;
using System.IO;
using System.Linq;

[System.Serializable]
public class CategoryData
{
    public string subfolderName;
    public GameObject transformParentObject;
}

public class ImageSlider : MonoBehaviour
{
    [SerializeField] private GameObject buttonPrefab;
    [SerializeField] private Transform contentParent;
    [SerializeField] private List<CategoryData> categoryDataList;

    [SerializeField] private Transform playerTransform;
    [SerializeField] private Transform cameraTransform;

    [Header("Smooth Movement Settings")]
    [SerializeField] private float movementDuration = 2f;
    [SerializeField] private float rotationDuration = 2f;
    [SerializeField] private AnimationCurve movementCurve = AnimationCurve.EaseInOut(0, 0, 1, 1);
    [SerializeField] private AnimationCurve rotationCurve = AnimationCurve.EaseInOut(0, 0, 1, 1);

    private List<string> imagePaths = new List<string>();
    private List<Transform> availableTransforms = new List<Transform>();
    private ScrollRect scrollRect;
    private int currentCategoryIndex = 0;
    private bool isTransitioning = false;

    private void Start()
    {
        scrollRect = GetComponent<ScrollRect>();

        LoadImagesFromStreamingAssets(currentCategoryIndex);
        CreateImageButtons();
    }

    public void ChangeImageCategory(int categoryIndex)
    {
        if (categoryIndex < 0 || categoryIndex >= categoryDataList.Count)
        {
            Debug.LogError("Invalid category index");
            return;
        }

        currentCategoryIndex = categoryIndex;
        LoadImagesFromStreamingAssets(currentCategoryIndex);
        CreateImageButtons();
    }

    private void LoadImagesFromStreamingAssets(int categoryIndex)
    {
        imagePaths.Clear();
        availableTransforms.Clear();

        try
        {
            CategoryData currentCategory = categoryDataList[categoryIndex];

            string folderPath = Path.Combine(Application.streamingAssetsPath, currentCategory.subfolderName);

            string[] imageExtensions = { ".png", ".jpg", ".jpeg", ".bmp", ".gif" };

            imagePaths = Directory.GetFiles(folderPath)
                .Where(path => imageExtensions.Contains(Path.GetExtension(path).ToLower()))
                .ToList();

            availableTransforms = currentCategory.transformParentObject
                .GetComponentsInChildren<Transform>()
                .Where(t => t.parent == currentCategory.transformParentObject.transform)
                .ToList();
        }
        catch (System.Exception e)
        {
            Debug.LogError($"Failed to load images or transforms: {e.Message}");
        }
    }

    private void CreateImageButtons()
    {
        // 기존 자식 오브젝트들 모두 제거  
        foreach (Transform child in contentParent)
        {
            Destroy(child.gameObject);
        }

        // 이미지 개수와 사용 가능한 트랜스폼 개수 중 작은 값으로 아이템 수 결정  
        int itemCount = Mathf.Min(imagePaths.Count, availableTransforms.Count);

        // 콘텐츠 부모의 RectTransform 가져오기  
        RectTransform contentRectTransform = contentParent.GetComponent<RectTransform>();

        // 버튼 프리팹의 RectTransform 가져오기  
        RectTransform buttonPrefabRectTransform = buttonPrefab.GetComponent<RectTransform>();

        // 버튼의 높이와 너비 계산  
        float buttonHeight = buttonPrefabRectTransform.rect.height;
        float buttonWidth = buttonPrefabRectTransform.rect.width;

        // 버튼 사이의 수직, 수평 간격 설정 (필요에 따라 조정 가능)  
        float verticalSpacing = 10f;
        float horizontalSpacing = 10f;

        // 수평 레이아웃 설정 (원하는 레이아웃에 따라 조정)  
        int columnsCount = 4; // 예: 4개의 열로 배치  
        int rowsCount = Mathf.CeilToInt((float)itemCount / columnsCount);

        // 총 높이와 너비 계산  
        float totalHeight = (buttonHeight + verticalSpacing) * rowsCount;
        //float totalWidth = (buttonWidth + horizontalSpacing) * Mathf.Min(itemCount, columnsCount);
        float totalWidth = (buttonWidth + horizontalSpacing) * itemCount + (horizontalSpacing * 6);

        // 콘텐츠 부모의 높이와 너비 설정  
        contentRectTransform.SetSizeWithCurrentAnchors(RectTransform.Axis.Vertical, totalHeight);
        contentRectTransform.SetSizeWithCurrentAnchors(RectTransform.Axis.Horizontal, totalWidth);

        for (int i = 0; i < itemCount; i++)
        {
            // 버튼 프리팹을 콘텐츠 부모에 인스턴스화  
            GameObject buttonObject = Instantiate(buttonPrefab, contentParent);

            // 버튼 위치 계산 (그리드 레이아웃 스타일)  
            int row = i / columnsCount;
            int col = i % columnsCount;

            RectTransform buttonRectTransform = buttonObject.GetComponent<RectTransform>();
            buttonRectTransform.anchoredPosition = new Vector2(
                col * (buttonWidth + horizontalSpacing),
                -row * (buttonHeight + verticalSpacing)
            );

            // 이미지 로딩 및 버튼 클릭 이벤트 설정 (이전 코드와 동일)  
            Image buttonImage = buttonObject.GetComponent<Image>();
            if (buttonImage != null)
            {
                StartCoroutine(LoadImageCoroutine(imagePaths[i], buttonImage));
            }

            int index = i;
            Button button = buttonObject.GetComponent<Button>();
            if (button != null)
            {
                button.onClick.AddListener(() => OnButtonClicked(index));
            }
        }
    }

    private IEnumerator LoadImageCoroutine(string path, Image targetImage)
    {
        UnityEngine.Networking.UnityWebRequest request =
            UnityEngine.Networking.UnityWebRequestTexture.GetTexture("file://" + path);

        yield return request.SendWebRequest();

        if (request.result == UnityEngine.Networking.UnityWebRequest.Result.Success)
        {
            Texture2D texture = UnityEngine.Networking.DownloadHandlerTexture.GetContent(request);
            Sprite sprite = Sprite.Create(texture, new Rect(0, 0, texture.width, texture.height), new Vector2(0.5f, 0.5f));
            targetImage.sprite = sprite;
        }
        else
        {
            Debug.LogError($"Failed to load image: {path}");
        }
    }

    private void OnButtonClicked(int index)
    {
        if (index >= 0 && index < availableTransforms.Count && !isTransitioning)
        {
            StartCoroutine(SmoothTransition(availableTransforms[index]));
        }
    }

    private IEnumerator SmoothTransition(Transform targetTransform)
    {
        isTransitioning = true;

        Vector3 startPlayerPosition = playerTransform.position;
        Vector3 startCameraPosition = cameraTransform.position;
        Quaternion startPlayerRotation = playerTransform.rotation;
        Quaternion startCameraRotation = cameraTransform.rotation;

        Vector3 targetPlayerPosition = targetTransform.position;
        Vector3 targetCameraPosition = targetTransform.position;
        Quaternion targetPlayerRotation = targetTransform.rotation;
        Quaternion targetCameraRotation = targetTransform.rotation;

        float elapsedTime = 0f;
        while (elapsedTime < movementDuration)
        {
            float t = movementCurve.Evaluate(elapsedTime / movementDuration);

            if (playerTransform != null)
            {
                playerTransform.position = Vector3.Lerp(startPlayerPosition, targetPlayerPosition, t);
                playerTransform.rotation = Quaternion.Slerp(startPlayerRotation, targetPlayerRotation, t);
            }

            if (cameraTransform != null)
            {
                cameraTransform.position = Vector3.Lerp(startCameraPosition, targetCameraPosition, t);
                cameraTransform.rotation = Quaternion.Slerp(startCameraRotation, targetCameraRotation, t);
            }

            elapsedTime += Time.deltaTime;
            yield return null;
        }

        if (playerTransform != null)
        {
            playerTransform.position = targetPlayerPosition;
            playerTransform.rotation = targetPlayerRotation;
        }

        if (cameraTransform != null)
        {
            cameraTransform.position = targetCameraPosition;
            cameraTransform.rotation = targetCameraRotation;
        }

        isTransitioning = false;
    }
}
```
