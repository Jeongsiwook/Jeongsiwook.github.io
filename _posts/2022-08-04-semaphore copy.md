---
layout: single
title: "Mutex(뮤텍스) vs Semaphore(세마포어)"
categories: CS
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

둘 다 OS 수업 시간에 들은 단어들이지만, 정확히 기억이 나지 않고 있었다. 검색 도중에 세마포어를 보고, 중요했던 것 같아 개념을 한 번 정리하고자 한다.

# Mutex

Mutual + exclsion.  
여러 스레드를 사용하는 환경에서 자원에 대한 접근을 강제하기 위한 동기화 메커니즘

## 특징

- Boolean 타입의 Lock 변수를 사용한다
- 공유 자원을 사용 중인 스레드가 있을 때, 다른 스레드가 공유 자원에 접근한다면 Blocking 후 대기 큐로 보낸다
- Lock을 건 스레드만 Lock을 해제할 수 있다

## Spin Lock

기본적으로 Mutex와 유사.

## 특징

- Busy-waiting(대기 큐에 들어가지 않고, 계속해서 공유 자원을 요청) 하며 대기 큐를 갖지 않는다
- Mutex-nonbloking 모델로 볼 수 있다
- 컨텍스트 스위칭 시간이 더 짧거나, 멀티 코어 프로세스에 효율적이다

# Semaphore

멀티프로그래밍 환경에서 다수의 프로세스나 스레드의 여러 개의 공유 자원에 대한 접근을 제한하는 방법

## 특징

- 세마포어 변수를 통해 wait, signal을 관리한다. 세마포어 변수는 0 이상의 정수형 변수를 갖는다
- 계수 세마포어로 사용할 수 있으며, 접근할 수 있는 공유 자원의 수가 1개일 때는 이진 세마포어로 뮤텍스처럼 사용할 수 있다
- Lock을 걸지 않은 스레드도 Signal을 보내 Lock을 해제할 수 있다
- 대기 방식엔 대기 큐와 스핀락 방식이 있다

# 📃 참고

## 교착 상태

두 가지 이상의 작업이 상대방의 작업이 끝나기를 하염없이 기다리는 상태

교착 상태가 발생하려면 4가지 조건을 모두 만족해야 한다.

1. 상호 배제
2. 점유 대기
3. 비선점
4. 순환 대기

## 상호 배제

프로세스들이 필요로 하는 자원에 대해 배타적인 통제권을 요구하는 것이다. 쉽게 말해, 하나의 프로세스가 공유 자원을 사용할 때 다른 프로세스가 공유 자원에 접근할 수 없도록 통제하는 것을 말한다.

## 임계 영역(Critical Section)

공유 자원이 속해 있어 교착 상태가 발생할 수 있는 영역

# 💭 느낀 점

잊고 있던 개념을 알게 되는 시간이었지만, 정작 이러한 것을 어디에 써야 하는지는 아직 잘 모르겠다. 언젠가 이 개념들이 도움이 되었으면 좋겠다.

---

출처

- [10분 테코톡](https://www.youtube.com/watch?v=oazGbhBCOfU)
