---
layout: post
title: 람다표현식 문법
--- 

자바는 타입 결합이 강한 언어이기 때문에 파라미터 타입을 지정해야한다.
람다표현식의 결과타입은 지정하지 않는다. 결과타입은 항상 문맥으로 추정된다. 
예를 들어 다음 표현식은 int 타입 결과를 기대하는 문맥에서 사용할 수 있다.

{% highlight js %} 
(String first, String second) 
    -> Integer.compare(first.length(), second.length())
{% endhighlight %}

### 만일 표현식이 1줄 이상이라면 {} 로 감싼다.
{% highlight js %}
(String first, String second) -> {
    if (first.length() < second.length()) return -1;
    else if (first.length() > second.length()) return 1;
    else return 0;
}
{% endhighlight %}

### 람다표현식이 파라미터를 받지 않을때 빈 괄호를 사용한다.
{% highlight js %} 
() -> { for (int i = 0; i < 1000; i ++) doWork(); }
{% endhighlight %}

### 파라미터 타입을 추정할 수 있는 경우에는 타입을 생략할 수 있다.
{% highlight js %} 
Comparator<String> comp
    = (first, second) // (String first, String second) 와 같다.
        -> Integer.compare(first.length(), second.length())
{% endhighlight %}

### 추정 가능한 파라미터 1개를 받으면 괄호를 생략할 수 있다.
{% highlight js %} 
EventHandler<ActionEvent> listener = 
    event -> System.out.println("Thanks for clicking!");
    // (event) -> 또는 (ActionEvent event) -> 
{% endhighlight %}


### Note
* 메소드 파라미터와 마찬가지 방식으로 람다 파라미터에 애노테이션이나 final 를 붙일 수 있다.
{% highlight js %}
(final String name) -> ... 
(@NonNull String name) -> ... 
{% endhighlight %}
* 람다 표현식에서 어떤 경우에는 값을 리턴하고, 다른 경우에는 리턴하지 않는 것은 규칙에 어긋난다.
예를 들어 (int x) -> { if (x >= 0) return 1; } 은 잘못된 것이다.