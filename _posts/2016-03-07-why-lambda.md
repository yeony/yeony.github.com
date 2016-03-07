---
layout: post
title: 왜 람다인가
--- 

> 람다표현식란 파라미터가 있는 코드블록이다. 코드블록을 나중에 실행하고자 할 때 람다표현식을 사용한다.

### 1
{% highlight js %} 
class Worker implements Runnalbe {
    public void run() {
      for (int i = 0; i < 1000; i++)
        doWork();
    }
  ...
}

Worker w = new Worker();
new Thread(w).start();

{% endhighlight %}

### 2
{% highlight js %} 
class LengthComparator implemets Comparator<String> {
    public int compare(String first, String second) {
      return Integter.comapre(first.length(), second.length());
    }
}

Arrays.sort(strings, new LengthComparator());
{% endhighlight %}

### 3
{% highlight js %} 
button.setOnAction(new EventHandler<ActionEvent>() {
    public void handle(ActionEvent event) {
        System.out.println("Thanks for clicking!")
    }
});
{% endhighlight %}

코드블록을 어딘가(thread pool, sort method, button) 에 전달하고 나중에 실행될 수 있다. 자바8 이전에는 (객체지향 언어이기때문에) 코드블록을 전달하려면 원하는 코드가 있는 메소드를 포함하는 클래스의 객체를 생성해야했다.
