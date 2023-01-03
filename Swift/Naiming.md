# TIL(22.12.28)

[영어 변수명을 잘 지어보자](https://www.youtube.com/watch?v=rbSnkiqPnJI)을 참고하여 작성하였습니다.

## **영어변수 Naming**

잘읽히는 코드 = 영어+컨벤션

1. 올바른 품사를 사용하자.
    
    ```
    view.insertSubview(gradientView, at: 2)
    //주어     동사        형용사+명사     전치사
    ```
    
    1-1 동사의 변형
    
    | 동사 원형 | 과거형 | 과거 분사형 |
    | --- | --- | --- |
    | request | requested | requested |
    | make | made | made |
    | hide | hid | hidden |
    - 동사를 변형해서 쓰는 특징이 있다.
    - 동사원형
        - 함수/메서드에 사용
        - 조동사(can/should 등) 뒤에 사용 ex) canBecomeFirstResponder
        - Life Cycle 관련 delegate ex) didReceive, willAppear, didComplete
    - 과거 분사형
        - 과거 분사 = 형용사로 인식하자
        - 수동의 의미 ex) requestedData, hiddenView
        - Bool 변수 ex) isHidden, isSelected
    
    1-2 명사와 동사가 같은 경우
    
    | 명사 | 동사 |
    | --- | --- |
    | request | request |
    | start | start |
    | play | play |

1. Bool
    
    ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/464682d6-254e-41b0-b7f1-b835d7ee71ae/Untitled.png)
    
2. 단수와 복수
    1. 하나는 단수, array 타입은 복수
    
    ```swift
    let album: Album // 명확
    let albums: [Album]
    
    for album in albums { } / 명확
    
    var album: Album? / 불명확
    let artwork = album.map { downloader.image(from: $0.artworkURL) }
    
    var album: [Album] / 불명확
    let coverSongs = album.map { $0.coverSong }
    ```
    
    3.1 불규칙 복수형
    
    ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/93c47941-cc1a-476f-a0ee-33ff69b5f211/Untitled.png)
    
3. 타입별 Naming Convention
    1. URL
        
        ```swift
        var fullSizeImageURL: URL?
        var renderedContentURL : URL
        ```
        
    2. UIImage
        
        ```swift
        var referenceImage: ARReferenceImage?
        var displaySizeImage: UIImage?
        ```
        
    3. Size(16.53)
    4. Date
    5. Data