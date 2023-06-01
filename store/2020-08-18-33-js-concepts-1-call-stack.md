---
title: '33 Concepts Every JavaScript Developer Should '
toc: true
toc_sticky: true
categories:
   - javascript
last_modified_at: 2020-06-16T08:06:00-05:00
first_writed_at: 2021-08-25T08:06:00-05:00
subtitle: 부제는 부제다
---

## 모든 자바스크립트 개발자가 알아야 하는 33가지 개념

javascript는 하나의 thread로 단 1개의 동시성만 다루는 언어.  
(한번에 1개의 작업만 다룰수있다)

{% capture fig_img %} [![Foo](https://mdn.mozillademos.org/files/17124/The_Javascript_Runtime_Environment_Example.svg)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/EventLoop) {% endcapture %}

{% capture fig_caption %}
https://developer.mozilla.org/en-US/docs/Web/JavaScript/EventLoop
{% endcapture %}

<figure>
  {{ fig_img | markdownify | remove: "<p>" | remove: "</p>" }}
  <figcaption>{{ fig_caption | markdownify | remove: "<p>" | remove: "</p>" }}</figcaption>
</figure>

### Call Stack

함수의 호출을 기록.
우리가 어떤 함수를 실행시킨다면 stack위에 무언가를 push하는 것.
함수가 호출 될 때는 이 call stack안에 쌓인 함수들이 pop되는 것.
가끔 함수를 재귀적으로 호출하다가 무한 루프에 빠지게 된다.
chrome의 경우 16000프레임의 제한된 스택을 가지고 있어서 이 범위를 넘어서게 된다면 max stack reached라는 상태가 되고 실행중이던 것을 kill해버린다

> RageError : Maximum call stack size exceeded

### Heap

object들은 Heap 내부에 할당된다.
힙은 거의 구조화 되지 않은 영역(unstructured)의 메모리
변수와 객체들의 모든 메모리 할당이 여기서 일어난다.

### Queue

javascript runtime은 message Queue를 가짐.  
message Queue는 실행될 call back함수나 실행될 메시지들에 대한 리스트.  
stack이 충분한 공간(capacity)을 갖고 있을 때, massage Queue밖으로 나오게 되고 message가 가지고 있던 function 목록들이 실행.  
이렇게 초기 stack frame이 만들어지고, stack이 다시 빌때, message 수행도 끝남.  
이벤트 들에 대한 callback함수가 제공되었다고 가정했을때 이 메시지들은 외부 비동기 이벤트들에 대한 응답으로 큐에 쌓임.

여기서 외부 비동기 이벤트 들이란 `마우스클릭`, `HTTP요청` 등을 의미.  
사용자가 버튼을 눌렀을때 아무런 콜백함수가 등록되어있지않다면 어떠한 메시지도 큐에 들어가지 않음.

### Event Loop

일반적으로 우리가 javascript code의 성능을 측정할 때, stack안에 있는 함수는 성능을 느리게도 빠르게도 만듦.
`console.log`만 있는 코드는 빠르겠지만 수천 수백만개가 넘는 for문과 while 등의 반복문을 수행한다면 코드는 느려지게 될 것.
또 그 코드들은 stack을 계속 차지하게 됨.
이런 것들을 가리켜 'Blocking Script'라 부른다.
Network, image 요청은 느리다. 비동기로 처리할 수 있어서 다행.
이러한 network요청들이 동기화 함수들을 통해서 이뤄진다면 아마 server에 접근한 요청에 대한 응답이 올때 까지 브라우저(또는 실행 어플리케이션)는 아무런 반응이 없을 것이다.
single thread language javascript는 stack에 쌓인 function들에서 어떠한 값을 반환하기 전까지는 불가능하다.
사용자를 이용한 유동적인 UI를 원한다면 이상적인 상황은 아니다.

우리는 비동기함수들을 잘 활용해야한다.
비동기콜백을 이용한다는 것은 우리가 코드의 일정부분을 실행시키고 나중에 실행될 콜백함수를 스택에 넣는 것을 말한다.
우리는 개발을 하다보면 꼭 ajax(`setTimeout()`, `setInterval()`, `Promise()`, etc...)를 만난다.
모든 비동기 callback(`console.log`, `mathematical operations`)들은 코드에서 읽히자마자 바로 실행되지 않고 잠시후에 실행된다.
동기함수들과는 다르게 stack의 내부로 push될 수 없다.
