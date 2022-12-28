# **API Design Guidelines**


[API Design Guidelines](https://www.swift.org/documentation/api-design-guidelines/#fundamentals)

## **Fundamentals**
---

## **Naiming**
---
### Promote Clear Usage(명확한 사용을 추구하자!)
1. 모호함을 피하기 위해 필요한 모든 단어를 포함시키세요.
```swift
⛔️
extension List {
    public mutating func remove(at position: Index) -> Element
    }
    employees.romove(at: x)
```
만약 `at`을 생략하게 된다면, x가 제거해야 할 요소의 위치보다는 x와 똑같은 요소를 찾아 제거하는것으로 해석될 수 있다.
```swift
✅
employees.remove(x) // 불분명해진다.
```
2. 필요 없는 단어를 생략하세요.
이미 보유하고 있는 정보와 중복되는 단어는 생략해야 한다.
```swift
⛔️
public mutating func removeElement(_ member: Element) -> Element?
allViews.removeElement(cancelButtion)
````
이 경우 `Element`는 전혀 중요한 의미를 내포하지 않고있다.
```swift
✅
public mutating func remove(_ member: Element) -> Element?
allViews.remove(cancelButton)
```
일반적으로 유형보다는 매개변수의 역할을 설명하는 단어를 사용하면 좋다.

3. 역할에 따라 변수, 매개변수 및 관련 유형의 이름을 지정하세요.
```swift
⛔️
var string = "Hello"
protocol ViewController {
    associatedtype ViewType : View
}
class ProductionLine {
    func restock(from widgetFactory: WidgetFactory)
}
```
위의 방식으로 유형을 이름을 변경ㅇ하면 명확성과 표현력을 최적화할 수 없다.
```
string ➡️ greeting
ViewType ➡️ ContentView
widgetFactory ➡️ supplier
```
```swift
var greeting = "Hello"
protocol ViewController {
    associatedtype ContentView: View
}
class ProductionLine {
    func restock(from supplier: WidgetFactory)
}
```
4. 약한 유형 정보를 보충해라.
```swift
func add(_ observer: NSObject, for keyPath: String)
grid.add(self, for: graphics) // 모호하다.
```
각각의 약한 유형의 매개변수 앞에 역할을 설명하는 명사가 온다.
```swift
func addObserver(_ observer: NSObject, forKeyPath path: String)
grid.addObserver(self, forKeyPath: graphics) // 정확하다.
```

## **Conventions**
---
## **Special Instructions**
---