---
title: "[Unity2D] 충돌 문제 해결"
excerpt: "연결 리스트"

categories:
    - Unity2D
tags:
    - [Unity2D, ErrorFix]

toc: true
toc_sticky: true

date: 2022-07-22
last_modified_at: 2022-07-22
---
#충돌 처리 관련 이슈

##문제 상황 : 자식 오브젝트의 충돌을 부모 오브젝트의 스크립트에서 잡아내지 못함. 두 오브젝트 모두 collider와 rigidbody가 있었음.

##해결: 유니티에서 자식 오브젝트의 충돌 처리를 부모 오브젝트가 스크립트 (OnTriggerEnter2D) 를 통해 감지하려면

자식 오브젝트엔 collider가 존재해야한다. 하지만 rigidbody는 존재하면 안된다.

rigidbody는 충돌을 감지할 부모 오브젝트에 있어야 한다.