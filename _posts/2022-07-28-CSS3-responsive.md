---
layout: single
title: "반응형 웹"
categories: Front-end
tag: CSS
author_profile: false
sidebar:
  nav: "docs"
# search: false
toc: true
---

**[공지사항]** 잘못된 정보나 오타에 피드백 주시면 감사하겠습니다.:)
{: .notice--info}

# 🔎 개요

사용자들을 같은 웹 콘텐츠를 이용하더라도 PC와 모바일 기기에서 동등한 서비스를 받기를 원한다. 이에 대한 대응 방안인 반응형 웹에 대해 알아보고자 한다.

# Responsive Web

디바이스 종류에 따라 웹페이지의 크기가 자동으로 재조정 되는 것을 말한다.

## Media Query

모바일에 대응되는 반응형 또는 적응형 웹 사이트를 만들 때 사용되는 CSS 구문이다.

### 문법

![미디어 쿼리 문법](https://www.nextree.co.kr/content/images/2021/01/jsseo-140329-CSS-02-1024x167.png)

1. `only | not`  
   only 키워드는 뒤의 조건일 경우만, not 키워드는 뒤의 조건을 제외한 조건

2. 미디어 타입의 종류

   미디어 타입은 쉼표를 통해서 나열하여 사용할 수 있다.

   `all`  
    모든 미디어 타입

   `screen`  
    컴퓨터 스크린

   `print`  
    인쇄 용도

   `aural`  
    음성 합성 장치

   `braille`  
    점자 표시 장치

   `handheld`  
    손으로 들고 다니면서 볼 수 있는 작은 스크린에 대응하는 용도

   `projection`  
    프로젝터

   `tty`  
    디스플레이 능력이 한정된 텔렉스, 터미널, 또는 수동 이동 장치 등 고정된 글자를 사용하는 미디어

   `tv`  
    음성과 영상이 동시 출력되는 장치

   `embossed`  
    페이지에 인쇄된 점자 표지 장치

3. 속성과 속성값  
   `width`  
   웹 페이지의 가로 길이

   `height`  
   웹 페이지의 세로 길이

   `device-width`  
   기기의 실제 가로 길이

   `device-height`  
   기기의 실제 세로 길이

   `orientation`  
   width와 height를 구하여 width 값이 길면 landscape로, height 값이 길면 portrait로 판단

   `aspect-ratio`  
   width/height 비율을 판단

   `device-aspect-ratio`  
   단말기의 물리적인 화면 비율을 판단

   `color-index`  
   단말기에서 사용하는 최대 색상 수를 판단

   `monochrome`  
   흑백 컬러만을 사용하는 단말기에서 흰색과 검은색 사이의 단계를 판단

   `resolution`  
   지원하는 해상도를 판단

   `color`  
   단말기에서 사용하는 최대 색상 수의 비트 수를 판단

### 적용 방법

- `<link>`  
  `<head>` 태그 안에 위치하여 media 속성 안 조건에 만족할 때 해당 CSS 파일을 불러온다.

  ```html
  <link
    href="cssfile.css"
    media="screen and (min-width: 768px)"
    rel="stylesheet"
  />
  ```

- `<style>`  
  `<head>` 태그 안에 위치하여 media 속성 안 조건에 만족할 때 스타일을 적용한다.

  ```html
  <style type="text/css" media="screen and (min-width: 512px)">
    <!-- style -->
  </style>
  ```

- `<style>-@import`  
  `@import`를 사용하여 뒷부분의 미디어 쿼리를 만족할 때 해당 CSS 파일을 불러온다.

  ```html
  <style>
    @import url(cssfile.css) screen and (min-width: 152px) and
      (max-width: 1024px);
  </style>
  ```

- CSS 파일  
  불러온 CSS 파일 안 혹은 `<style>` 태그 안에서 직접 미디어 쿼리를 작성하여 만족할 때 해당 스타일을 적용 한다.
  ```css
  @media screen and (min-width: 768px);
  ```

### 주의할 점

가로 폭 조정을 위해서 HTML 문서의 `<head>` 태그 사이에 다음의 코드를 넣어야 한다.

```html
<meta name="viewport" content="width=device-width, initial-scale=1" />
```

# 💭 느낀 점

반응형 웹을 Bootstrap과 tailwind를 사용해서 구현해왔었다. 왜 지금까지 사용한 프레임워크가 반응형 웹을 구현하는 데 도움을 주는지 아는 계기가 되었다.

P.S. 추가적인 배치들은 출처에 있는 사이트에 잘 설명되어 있다.

---

출처

- [https://www.codingfactory.net/10534](https://www.codingfactory.net/10534)
- [https://www.nextree.co.kr/p8622/](https://www.nextree.co.kr/p8622/)
