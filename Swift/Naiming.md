[# TIL(22.12.28)[# TIL(22.12.28)

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

2. Bool
    
    ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/464682d6-254e-41b0-b7f1-b835d7ee71ae/Untitled.png)
    
3. 단수와 복수
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
    
4. 타입별 Naming Convention
    
    4-1. URL
        
    ```swift
    var fullSizeImageURL: URL?
    var renderedContentURL : URL
    ```
        
    4-2. UIImage
        
    ```swift
    var referenceImage: ARReferenceImage?
    var displaySizeImage: UIImage?
    ```
        
    4-3. Size(16.53)
    
    4-4. Date
    
    4-5. Data
    
    ```swift    
    var physicalSize: CGSize
    var startData: Date
    var creationDate: Date?
    var arrivalData: Data
    var adjustmentData: PHAdjustmentData?
    ```    
    
    4-6. ID vs Id vs identifier(추천)
        - 세개 다 맞지만 identifier 추천
    
    4-7. isHidden(추천) vs hidden
        - isHidden 추천
    
    4-8. 중복제거
    ```swift
    // 개선전
    struct User {
        let userId: String
    }

    let id = user.userID // user가 중복된다

    // 개선 후
    struct User {
         let identifier: String
    }
        
    let id = user.identifier // 가독성 증가

    ```
        
    ```swift
    // 개선 전
    struct ImageDownloader {
        func downloadImage(from url: URL) {}
    }

    let imageDownloader = ImageDownloader()
    imageDownloader.downloadImage(from: imageURL)

    // 개선 후
    imageDownloader.download(fro: imageURL)
    imageDownloader.fetch(from: imageURL)
    imageManager.donwload(from: imageURL)
    ```
    
    4-9. get ❌ : swift 컨벤션에는 getter가 없으므로 여러가지 타입을 리턴하는 데이터에서는 유의하자
    
    ```swift
    // 개선전
    func data = formatter.date(from: dataString)
    func anchor(for node: SCNNode) -> ARAnchor?

    // 개선 후
    let data = formatter.date(from: dataString)
    let imageAnchor = sceneView.anchor(for: node)
    ```
    
    4-10. 메서드 Naiming 짓는 법
    
    ```
    fetch - 결과를 바로 return 한다
    get - 비동기 작업(handler를 받는다)
    request - 비동기 작업(handler를 받는다), fail 할 수 있다.
    execute / perform - 작업 자체가 request나 클로저에 감싸져 있을때
    ```
    
    참고자료
        
    [동의어 사전](https://www.thesaurus.com/)

    [Swift.org](https://www.swift.org/documentation/api-design-guidelines/#naming)