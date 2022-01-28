# [TIL] Today, I learned : RxSwift에 대한 감상



최근들어 RxSwift에 대해서 열심히 공부하고 있는 중입니다. 고용시장에서 RxSwift를 공부한 사람을 왜 우대사항이나 자격요건에 작성하는 지 조금은 이해가 갑니다. 왜냐하면, RxSwift 기존의 코드를 작성하는 방식과 생각을 조금 다르게 해야하는 경향이 있는 것 같습니다.



예를들면, 기존에는 "버튼을 클릭하면 이 로직을 실행시켜줘!" 라는 로직을 구현한다고 하면, 아래와 같죠.

```swift
@IBAction func buttonDidTap(_ sender: UIButton) {
  print("해줘")
}
```



Rx로 구현할 때는, 조금 다르게 생각해야합니다.

> 버튼이 탭할 때마다 이벤트가 방출되겠군.
>
> 그러면 이 이벤트를 받아야할 대상들이 누가있지?

```swift
button.rx.tap
	.subscribe(onNext: { print("해줘")} )
	.disposed(by: bag)
```

이렇게 되면, 단순히 탭할 때마다, 그냥 프린트문만 호출되죠. 물론 저 곳에 다양한 코드를 작성해도 되지만, 보통 RxSwift를 공부하고 있다는 것은 MVVM 구조를 함꼐 공부한다는걸 뜻하기에, 원하는 로직들이 ViewModel에 있을 확률이 높겠죠.



> 그러면 ViewModel에 있는 로직을 실행시켜야 하는데 어떻게 하지?
>
> 아 근데 그거 하기전에 API 통신을 하고난 이후에, 화면전환을 해야하는데, 이거 순서는 어떻게 해야하지?



Rx라는 도구는 참 확장성을 많이 고려한 것 같습니다.

제가 원하는 로직들이 바로 다음줄 바로 다음줄 이런식으로 적혀있기도 하고(물론 완벽히 그런 것은 아니지만요. 적용안했을 때의 델리게이트 메소드 왔다갔다하는 것보다야 백번), 다양한 편리한 연산자가 있어서, 필터링하거나 액션에 대한 처리도 쉽네요.



이 다음글이나 빠른 시일에, Rx 관련 예제 프로젝트로 글을 작성해볼까합니다.



오늘은 초심자의 기억을 작성해두고 싶어서 작성했습니다.
