---
layout: post
title: "암호화"
subtitle: 암호화(encryption)란 일상적인 문자로 쓰이는 평문을 암호키를 소유하지 않은 사람이 알아볼 수 없도록 암호문으로 변환하는 것이다
categories: Code
tags: [velog, code, encryption]
---


# 암호화

그냥 TIL처럼 프로그래밍 공부하면서 배운거 간단하게 적을거야.

## 2022.10.27.

```python
import bcrypt

ex_id = "member1"
ex_password = 'password1234'
bpass = bcrypt.hashpw(ex_password.encode('utf-8'), bcrypt.gensalt())

# 디비 구현 귀찮아서 딕셔너리로 만드는 디비 ;;
dic = {}
dic[ex_id] = bpass.decode('utf-8')

cid = input("plz input your id: ")
if cid in dic:
  while 1:
    cpass = input("plz input your password: ")
    answer = bcrypt.checkpw(cpass.encode('utf-8'), dic[cid].encode('utf-8'))
    if answer:
      print("log in")
      break
    else:
      print("plz re input")
else:
  print("there is no id")

```

> Q.
DB에 넣을 때 decode 해서 넣어야 된다고 하는데, 왜 그런가. byte로 들어가면 안되나..?
로그인 한 다음에 JWT로 토큰을 발행한다는데 왜?? 로그인 하면 인증이 끝난거 아닌가

## 2022.00.00.

## ref

[2021 백엔드 개발자 로드맵 中 웹 보안 지식](https://velog.io/@geeneve/2021-%EB%B0%B1%EC%97%94%EB%93%9C-%EA%B0%9C%EB%B0%9C%EC%9E%90-%EB%A1%9C%EB%93%9C%EB%A7%B5#%EC%9B%B9-%EB%B3%B4%EC%95%88-%EC%A7%80%EC%8B%9D)

[안전한 패스워드 보안(패스워드 암호화 저장법 /bcrypt, scrypt, pdkdf2 )](https://junho94.tistory.com/30)

[replit](https://replit.com/@jongjinna/StudyCryption#main.py)

