# Today I learned: 컴포지션에 대한 짧은 생각

 오늘은 아키텍처에 대한 생각을 정리해보겠습니다.



## Composition (합성 및 조립)

 앱 아키텍처에 대해서 이야기할 때, 개인적으로는 가장 중요하다고 생각합니다. 왜냐하면, 코드를 아무리 읽기 어렵다고하더라도, 주석을 참고하거나 해당 개발자에게 들으면 해결됩니다. 하지만 해당 앱에 컴포지션이 고려되어있지 않으면, 앱을 유지보수하는 것 보다 그냥 처음부터 만드는게 나을 정도인 경우도 있기 때문입니다. 그러면 제가 상상할 수 있는 것들 중에서는 가장 손실이 큰 경우가 아닐까 생각해봅니다.



> A way to combine objects and data types into more complex ones

(이 정의는 위키피디아의 정의이입니다.)



 컴포지션을 고려하지 않은 아키텍쳐는, 문제를 해결하기 정말 어렵습니다. 단순히 소프트웨어에만 국한되는 내용은 아니라고 생각합니다. 현실의 문제들도 문제를 해결할 수 없다고 판단되면, 잘게 쪼개거나 문제를 단순화합니다. 그리고 각각 해결한 다음 다시 합쳐서 큰 문제를 해결하곤 하죠.



 그렇다면 컴포지션을 고려하면 어떤 장점이 있을까요?

- 테스트가 용이하다.
- 작성한 코드를 재사용하기 쉽다.
- 코드를 유지보수하기 좋다.

 너무 당연한 이야기죠. 그러면 추가로 GoF 디자인 패턴에 있는 하나의 말을 인용하겠습니다.



> Favor object composition over class inheritance
>
> (상속보다는 객체를 합성하는 것을 우선시 해라.)



이런 이야기를 왜 작성했을까 고민했습니다. 아무래도 상속을 하게되면, 사실상 둘의 관계가 가장 강력하게 결합되는 순간이여서 그렇다고 봅니다. 상속보다 더 강력한 것이 있을까요? 상속을 받으면서 둘을 분리시키는 것은 정말 어렵습니다.



 value Type(ex. struct)는 상속이 없죠. 프로토콜 채택이죠. 그러므로 컴포지션의 성질을 활용할 수 밖에 없습니다. 상속은 없지만 컴포지션을 통해서 기능을 확장하죠.

 UIKit에서 ViewController 바로 아래 존재하는 UIView인 Superview가 있죠. 이곳에서 무언가 구성할 때, 우리가 상속을 시켜서 구성하나요? 그렇지 않죠. 원하는 것들을 조합하고 추가하기만 합니다. 그렇지만 그 안에 있다면, View가 이동하면 모두 이동하긴 하죠. 그리고 특정 어트리뷰트를 설정하면 동시에 적용받고요. 이러한 것을 컴포짓 패턴이라고 부릅니다.



## 정리

- 상속보다는 컴포지션을 지향하자



읽어주셔서 감사합니다.