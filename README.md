# 객체 식: 무명 내부 클래스를 다른 방식으로 설정
일단 무명 객체를 정의할 때도 object 키워드를 사용한다. 무명 객체는 자바의 무명 내부 클래스를 대신한다. 예를 들어 자바에서 흔히 무명 내부 클래스로 구현하는 이벤트 리스너를 코틀린에서 구현해보자.

<code>
<pre>
 window.addMouseListener {
  object : MouseAdapter() {
    override fun mouseClicked(e: MouseEvent) {
    }
    override fun mouserEntered(e: MouseEvent) {
    }
  } 
}
</code>
</pre>

함수를 호출하면서 인자로 무명 객체를 넘기기 때문에 클래스와 인스턴스 모두 이름이 필요하지 않다. 하지만 객체에 이름을 붙여야 한다면 변수에 무명 객체를 대입하면 된다.

<code>
<pre>
val listener = object : MouserAdapter() {
  override fun mouseClicked(e: MouseEvent) {...}
  override fun mouseEntered(e: MouseEvent) {...}  
}
</code>
</pre>

객체 선언이랑 다르게 object여도 싱글턴의 형식이 아니고 찍어낼때마다 새로운 인스턴스가 생성된다고 한다.

자바의 무명 클래스와 같이 객체 식 안의 코드는 그 식이 포함된 함수의 변수에 접근할 수 있는데, 자바랑은 다르게 final이 아닌 변수도 객체 식 안에서 사용할 수 있다. 따라서 객체의 식 안에서 그 변수의 값을 변경할 수 있다.
<code>
<pre>
fun countClicks(window: Window) {
  var clickCount = 0
  
  window.addMouserListener(object: MouserAdapter() {
    override fun mouseClicked(e: MouseEvent) {
    clickCount++
    }
  })
  ....
}
</code>
</pre>

이제 람다로 프로그래밍에 들어갑니다
