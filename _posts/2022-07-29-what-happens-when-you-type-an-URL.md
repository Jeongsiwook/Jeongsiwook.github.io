---
layout: single
title: "웹 브라우저에 www.google.com을 치고 엔터를 누르면 일어나는 일"
categories: Front-end
tag: JavaScript
author_profile: false
sidebar:
  nav: "docs"
# search: false
toc: true
---

**[공지사항]** 잘못된 정보나 오타에 피드백 주시면 감사하겠습니다.:)
{: .notice--info}

# 🔎 개요

웹 개발자라면 알아야 할 인터넷 작동 원리를 알아보고자 한다.

# 동작 순서

![웹의 동작 원리](http://tcpschool.com/lectures/img_webbasic_10.png)

1. **Browser는 캐싱된 DNS 기록들을 통해 www.google.com에 대응되는 IP 주소가 있는지 확인**

   브라우저, OS, router, ISP를 순차적으로 확인해 DNS 기록들의 캐시에 접근한다.

2. **요청한 URL이 캐시에 없으면, ISP의 DNS 서버가 www.google.com을 호스팅하고 있는 서버의 IP 주소를 찾기 위해 DNS query를 전송**

   recursive search를 통해 IP 주소를 찾을 때까지 진행한다.

3. **Broswer가 서버와 TCP connection**

   브라우저는 인터넷 프로토콜을 사용해서 서버와 연결이 된다. 웹 사이트의 HTTP 요청의 경우에는 일반적으로 TCP를 사용한다.

   클라이언트와 서버간 데이터 패킷들이 오가려면 TCP connection이 되어야 한다. TCP/IP three-way handshake라는 프로세스를 통해서 클라이언트와 서버간 connection이 이뤄지게 된다.

4. **Browser가 웹 서버에 HTTP 요청**

   클라이언트의 브라우저는 GET 요청을 통해 서버에 www.google.com 웹 페이지를 요구한다.

   ![HTTP 요청](https://velog.velcdn.com/images%2Fylyl%2Fpost%2F391ca425-5c08-453b-addd-d92cc946380c%2Frequest-package.jpg)

5. **서버가 요청을 처리하고 response를 생성**

   서버는 웹 서버를 가지고 있다. 이들은 브라우저로부터 요청을 받고 request handler한테 요청을 전달해서 요청을 읽고 response를 생성하게 한다.

6. **서버가 HTTP response를 전송**

   서버의 response에는 요청한 웹 페이지, status code, compression type(content-encoding) - 어떻게 인코딩 되어 있는지, 어떻게 페이지를 캐싱할지(cache-control), 설정할 쿠키가 있다면 쿠키, 개인정보 등이 포함된다.

   ![response](https://velog.velcdn.com/images%2Fylyl%2Fpost%2F92e62bd8-e560-4fe8-9369-118089261edc%2Fimage.png)

7. **Broswer가 HTML content를 출력**

   브라우저는 HTML content를 단계적으로 보여준다. HTML의 스켈레톤, HTML tag 이 후에 추가적으로 필요한 웹페이지 요소들(이미지, CSS 스타일시트, JavaScript 파일 등) GET으로 요청한다. 이 정적인 파일들은 브라우저에 의해 캐싱이 되서 나중에 해당 페이지를 방문할 때 다시 서버로부터 불러와지지 않도록 한다.

# 📃 참고

## DNS(Domain Name System)

DNS(Domain Name System)은 URL들의 이름과 IP 주소를 저장하고 있는 데이터 베이스이다. IP 주소를 통해서 해당 웹 사이트를 호스팅하고 있는 서버 컴퓨터에 접근할 수 있다.

**DNS는 웹사이트 주소에 쉽게 접속할 수 있도록 매핑을 해주는 역할을 한다.**

## TCP(Transmission Control Protocol)

두 개의 호스트를 연결하고 데이터 스트림을 교환하게 해주는 중요한 네트워크 프로토콜이다.

**TCP는 에러 없이 패킷이 신뢰할 수 있게 전달 되었는지 보증해주는 역할을 한다.**

## Request handler

ASP.NET, PHP, Ruby 등으로 작성된 프로그램을 의미한다. 요청과 요청의 헤더, 쿠키를 읽어서 요청이 무엇인지 파악하고 필요하다면 서버에 정보를 업데이트 한다. 그 다음에 response를 특정한 포멧으로 작성한다.

## status code

- 1xx 정보만 담긴 메시지
- 2xx response가 성공적이라는 것을 의미
- 3xx 클라이언트를 다른 URL로 리다이렉트함
- 4xx 클라이언트 측에서 에러가 발생했음
- 5xx 서버 측에서 에러가 발생했음

# 💭 느낀 점

면접에서 또 자바스크립트에 대해서 물어본다면 이제는 자신있게 대답할 수 있다.

---

출처

- [TCP SCHOOL](http://www.tcpschool.com/javascript/js_intro_basic)
