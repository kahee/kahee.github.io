---
layout: post
title:  "후니의 쉽게쓴 시스코 네트워킹 - Part3"
date: 2019-07-19 00:00:00
img:
categories:
- Network
tags: [Network Basic]
---

## 후니의 쉽게쓴 시스코 네트워킹
### Part3. TCP/IP 와의 만남

--- 

1. TCP/IP
- Transmission Control Protocoal/Internet Protocoal 
- 각각의 네트워크에 접속되는 호스트들은 고유의 주소를 가지고 있어서 자신이 속해 잇는 네트워크 뿐만 아니라 다른 네트워크에 연결되어있는 호스트까지도 서로 데이터를 주소받을 수 있도록 만들어져있는 것이 특징 
- 고유 주소는 Internet Network Information Center 단체에서 관리
- TCP/IP 계층
    - 애플리케이션 계층 (Telnet, FTP, HTTP 등)
    - 트랜스포트 계층 (TCP, IP)
    - 인터넷 계층 (IP)
    - 네트워크 액세스 계층

2. IP 
- 전세계에서 유일하게 나만 가지고 있는 것 
- NAT(Networkt Address Translation): 내부 네트워크에서는 공인되지 않은 IP 주소를 사용하고, 인터넷으로 나갈대만 공인 주소를 사용하는 방식
- DHCP(Dynamic Host Configuration Protocol): 호스트 IP 구성 관리를 단순화하는 IP 표준이다.

3. 망분리
- 물리적 망 분리: 인터넷용과 내부용으로 장비를 각가 따로 가져가는 방식
- 논리적 망 분리
    - CBC(Client Based Computin): PC 안에서 업무 영역과 인터넷 영역을 구분 = PC 기반의 가상화
    - SBC(Server Based Computing): 작업은 서버에서 진행하면서 화면만 PC로 뿌려주는 것 = 서버 기반의 가상화
- [참고](https://m.blog.naver.com/PostView.nhn?blogId=s2kiess&logNo=220679395249&proxyReferer=https%3A%2F%2Fwww.google.com%2F)