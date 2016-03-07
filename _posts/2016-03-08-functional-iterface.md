---
layout: post
title: 함수형 인터페이스
--- 

> 람다표현식을 함수형 인터페이스로 변환할 수 있다.

자바에는 Runnable, Comparator 등 코드블록을 캡슐화하는 수많은 인터페이스가 있다. 람다는 이러한 기존 인터페이스와 호환된다.

### Runnalbe 
{% highlight js %} 
class LengthComparator implemets Comparator<String> {
    public int compare(String first, String second) {
      return Integter.comapre(first.length(), second.length());
    }
}

Arrays.sort(strings, new LengthComparator());
{% endhighlight %}

{% highlight js %} 
Arrays.sort(strings, (first, second) -> 
  Integer.compare(first.length(), second.length()));
{% endhighlight %}

### Comparator

{% highlight js %} 
button.setOnAction(new EventHandler<ActionEvent>() {
    public void handle(ActionEvent event) {
        System.out.println("Thanks for clicking!")
    }
});
{% endhighlight %}

{% highlight js %} 
button.setOnAction(event -> 
  System.out.println("Thanks for clicking!"));
{% endhighlight %}


단일 추상 메소드 <sup>Single Abstarct Method</sup> 를 갖춘 인터페이스를 갖춘 인터페이스의 객체를 기대할 때 람다표현식을 사용할 수 있다. 그리고 이러한 인터페이스를 함수형 인터페이스라고 한다. 람다표현식을 객체가 아니라 함수로 생각하고, 함수형 인터페이스에 전달할 수 있다고 인식하는 것이 좋다. 

### Note
함수형 인터페이스에 @FunctionalInterface 애노테이션을 붙이면 좋다. 컴파일러가 단일 추상 메소드를 갖춘 인터페이스인지 검사한다. javadoc 페이지에서 해당 인터페이스가 함수 인터페이스임을 알리는 문장을 포함한다.
