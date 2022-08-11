---
layout: single
title: "렌더링 기법"
categories: Front-end
tag: React
author_profile: false
sidebar:
  nav: "docs"
# search: false
toc: true
---

**[공지사항]** 잘못된 정보나 오타에 피드백 주시면 감사하겠습니다.:)
{: .notice--info}

# 🔎 개요

React를 사용하면서 접하게 되었던 개념들을 제대로 정리해보고자 한다.

![MPA vs SPA](https://res.cloudinary.com/practicaldev/image/fetch/s--k4JUdkjP--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/g3lnd7vfb7wrtlmolmd9.png)

# SPA (Single-page Application)

하나의 페이지로 구성된 애플리케이션을 말한다. 렌더링 방식으로 클라이언트 사이드 렌더링을 채택한다.

# MPA(Multi-page Application)

두 개 이상의 페이지로 구성된 애플리케이션을 의미한다. 사용자의 클릭과 같이 인터렉션이 발생할 때마다 해당 링크로 이동하여 앱이 다시 새로고침 되는 전통적인 방식으로 작동한다. 렌더링 방식으로 SSR을 채택한다.

## CSR (Client Side Rendering)

![CSR](https://images.velog.io/images/cheal3/post/d06f66eb-aab7-4440-8cb6-c92e6d36c1db/image.png)

사용자의 요청에 따라 필요한 부분만 응답받아 렌더링하는 방식이다. 모든 JS 파일을 다운 받아야 하므로 초기 로딩 시간이 더 오래 걸린다. 특정 부분을 변경하면 변경된 부분만 응답하기 때문에 화면이 깜박이지 않고 바로 수정된 데이터가 표시된다.

### 장점

- 빠른 속도 및 서버 부하 감소  
  변경된 부분과 관련된 데이터만 요청하고 가져오기 때문

- 사용자 친화적  
  페이지 안의 콘텐츠를 클릭하여 다음 단계로 전환하는 과정에서 링크가 없기 때문에 깜박임 없이 부드러운 이동

### 단점

- SEO에 불리
  JS를 사용하여 사용자와 상호작용 후에 페이지 내용을 로드하기 때문에 웹 크롤러가 페이지를 색인화하려고 하면 내용이 빈 페이지처럼 보이게 된다.

- 느린 초기 로딩 속도  
  초기에 모든 JS 파일을 다운 받아와야 하기 때문

## SSR (Server Side Rendering)

![SSR](https://miro.medium.com/max/1400/1*Nor2JglazrtqvXLK544BFw.png)

서버로부터 완전하게 만들어진 html 파일을 받아와 페이지 전체를 렌더링하는 방식이다. 특정 부분만 변경해도 전체 요소들을 모조리 서버로부터 다시 다운받기 때문에 앱이 다시 시작되고 화면이 깜빡인 후에 표시된다.

### 장점

- SEO를 제공  
  화면을 구성하는 각각의 페이지가 있기 때문

- 빠른 초기 로딩 속도  
  서버로부터 화면을 렌더하기 위한 필수적인 요소를 먼저 가져오기 때문

### 단점

- 불편한 사용자 경험  
  매번 페이지를 요청할 때마다 새로고침이 되기 때문

- 서버 부하 증가  
  페이지를 요청할 때마다 서버에서 페이지를 구성하는 모든 리소스를 준비해서 응답하므로 서버 부담이 증가

# SSG (Static Site Generator)

정적 사이트 생성기는 누가 접속하든 항상 동일한 내용을 보여주는 웹사이트를 만드는 데 최적화된 방법이다. 비교적 소규모 웹사이트를 제작할 때 매우 유용하다. 약점을 극복하기 위해 필요한 웹페이지만 골라서 업데이트해 주는 기능을 제공하고 있다.

## 장점

- 빠른 속도  
  모든 웹페이지를 미리 모두 만들어 놓고 요청이 들어오면 만들어 놓은 웹페이지를 그대로 응답만 해주기 때문

- SEO를 제공  
  미리 웹페이지가 모두 만들어져 있기 때문

## 단점

- 자주 업데이트할 시 비효율  
  빌드 시점에 웹사이트 전체를 매번 다시 만들어 내기 때문

# 어떻게 개발해야 하는가?

콘텐츠 중심으로 개발해야 한다. 애플리케이션을 구성하는 방법에 따라 단순 정보 제공과 같은 부분은 SSR으로, 동적인 변화가 필요한 부분은 CSR 방식으로 개발하는 게 좋다.

# 💭 느낀 점

항상 헷갈렸던 개념을 확인하는 유익한 시간이었다. 나는 주로 CSR 방식으로 개발을 해왔는데 SSR 방식인 Next.js를 알아보고 싶어졌다.

---

출처

- [10분 테코톡](https://www.youtube.com/watch?v=vM_zQLnlyKw)
- [https://www.daleseo.com/spa-ssg-ssr/](https://www.daleseo.com/spa-ssg-ssr/)
