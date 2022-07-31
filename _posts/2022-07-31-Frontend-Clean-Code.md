---
layout: single
title: "실무에서 사용하는 Frontend Clean Code"
categories: Front-end
tag: Info
author_profile: false
sidebar:
  nav: "docs"
# search: false
toc: true
---

**[공지사항]** 잘못된 정보나 오타에 피드백 주시면 감사하겠습니다.:)
{: .notice--info}

# 🔎 개요

개발할 때에 클린 코드를 크게 생각하지 않고 동작만을 기대하면서 하곤 했었다. 동작하면 기뻤지만 한 구석이 찝찝했었다. 그래서 클린 코드에 대해서 제대로 알아보고자 한다.

# 실무에서 클린 코드의 의의

유지보수 시간의 단축을 의미한다. 클린 코드는 짧은 코드를 의미하는 것이 아닌, 원하는 로직을 빠르게 찾을 수 있는 코드이다.

## 응집도

같은 목적의 코드는 뭉쳐 두자. 선언적 프로그래밍을 하자.

## 단일책임

하나의 일을 하는 뚜렷한 이름의 함수를 만들자. 새로운 기능을 추가할 때 기존의 함수에 추가하는 것이 아닌, 새로운 함수를 만들어 그 기능만을 실행하는 코드를 작성하자.

1. 한 가지 일만 하는 명확한 이름의 함수
2. 한 가지 일만 하는 기능성 컴포넌트
3. 조건이 많아지면 한글 이름도 유용

## 추상화

핵심 개념을 뽑아내자. 단, 추상화 수준이 섞여 있으면 코드 파악이 어렵다.

- Before(팝업 코드 제로부터 구현)

  ```jsx
  <div style={팝업스타일}>
    <button
      onClick={async () => {
        const res = await 회원가입();
        if (res.success) {
          프로필로이동();
        }
      }}
    >
      전송
    </button>
  </div>
  ```

- After(중요 개념만 남기고 추상화)

  ```jsx
  <popup onSubmit={회원가입} onSuccess={프로필로이동} />
  ```

# 액션 아이템

1. 담대하게 기존 코드 수정하기
2. 큰 그림 보는 연습하기
3. 팀과 함께 공감대 형성하기
4. 문서로 적어 보기(향후 어떤 점에서 위험할 수 있는지, 어떻게 개선할 수 있는지)

# 📃 참고

## 선언적 프로그래밍

핵심 데이터만 전달받고, 세부 구현은 뭉쳐 숨겨 두는 개발 스타일이다.
많은 선언적(Declarative) 접근 방식들의 기반에는 일종의 '명령적(Imperative) 추상화'가 존재한다.

### 명령형 vs 선언형

```js
function double(arr) {
  let results = [];
  for (let i = 0; i < arr.length; i++) {
    results.push(arr[i] * 2);
  }
  return results;
}

function add(arr) {
  let result = 0;
  for (let i = 0; i < arr.length; i++) {
    result += arr[i];
  }
  return result;
}
```

```js
function double(arr) {
  return arr.map((item) => item * 2);
}

function add(arr) {
  return arr.reduce((prev, current) => prev + current, 0);
}
```

# 💭 느낀 점

팀 프로젝트 당시에 팀원이 내 코드를 건드려야 되는 상황이 종종 있었다. 그 당시에 코드를 클린하게 짜지 않아, 코드를 건드리지 말고 차라리 내가 하겠다고 말을 했었다. 이번 시간을 통해 클린 코드 하는 방법을 알게 되었고 내 프로젝트들을 리팩토링을 해야겠다고 생각했다.

---

출처

- [https://www.youtube.com/watch?v=edWbHp_k_9Y](https://www.youtube.com/watch?v=edWbHp_k_9Y)
