---
title: "아두이노에서 객체지향 활용하기"

categories: [프로그래밍, 튜토리얼]
tags: [프로그래밍, 아두이노, 객체지향]
start_with_ads: true

toc: false
toc_sticky: true

lang: ko-KR
 
date: 2022-11-04 13:48:00 +0900
last_modified_at: 2023-04-12 20:38:00 +0900

redirect_from:
  - /posts/%EC%95%84%EB%91%90%EC%9D%B4%EB%85%B8%EC%97%90%EC%84%9C-%EA%B0%9D%EC%B2%B4%EC%A7%80%ED%96%A5/
---

개인적으로 아두이노를 별로 좋아하는 편은 아닙니다. 하드웨어에 의한 오류가 너무 빈번하게 일어나기 때문인데, 최근에 아두이노를 사용할 기회가 한 번 더 있었습니다.

"이왕 하는거 새로운 것에 도전해서 뭐라도 배워가자" 하는 마음에 객체지향 설계를 적용해봤습니다. 아두이노는 C++을 기반으로 동작하는데, 파이썬이나 C#과는 다른 모습이 있어 조금 생소했네요. 어려움은 있었지만 그래도 잘 동작하는 모습까지 확인하고 나니 뿌듯합니다. 혹시라도 나중에 C++을 다루게 된다면 도움이 되면 좋겠습니다.

## **예시 코드**

```cpp
#include "Arduino.h"

class MainFunctions
{
  public:
    AddFiveHundreadWon(int Money);
    AddOneHundreadWon(int Money);
    AddFiftyWon(int Money);
};
```
{: file="MainFunctions.cpp" }

```cpp

#include "Arduino.h"
#include "MainFunctions.h"

int MainFunctions::AddFiftyWon(int Money)
{
  Money += 500;
  return Money;
}

int MainFunctions::AddOneHundreadWon(int Money)
{
  Money += 1000;
  return Money;
}

int MainFunctions::AddFiveHundreadWon(int Money)
{
  Money += 2000;
  return Money;
}
```
{: file="MainFunctions.h" }

```cpp
void setup()
{
    ...
}

void loop()
{
    Money = MainFunctions.AddFiveHundreadWon(Money);
    Money = MainFunctions.AddOneHundreadWon(Money);
    Money = MainFunctions.AddFiftyWon(Money);
}
```
{: file="Arduino_OOP.ino" }

간단한 금액을 추가하는 기능의 코드를 낱개로 분할한 구현한 예시입니다. 클래스의 선언부인 `MainFunctions.h`에서 메서드를 선언하고, `MainFunctions.h`에서는 선언된 메서드를 정의하는 역할을, `Arduino_OOP.ino`에서는 정의된 메서드를 호출하는 역할을 맡도록 작성했습니다.

결과적으로 잘 작동합니다. 각각의 함수는 호출될 때마다 `AddFiveHundreadWon()`에서는 500원, `AddFiveHundreadWon()`에서는 100원, `AddFiftyWon()`에서는 50원이 더해집니다.