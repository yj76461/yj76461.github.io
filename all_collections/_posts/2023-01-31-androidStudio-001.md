---
title: "[안드로이드 스튜디오] gradle 버전 트러블 슈팅"
excerpt: "안드로이드 공부"

categories:
    - Android Studio
tags:
    - [Android Studio, Study]

toc: true
toc_sticky: true

date: 2023-01-31
---
# 안드로이드 스튜디오 gradle 버전 트러블 슈팅

----
## 에러들

### this version only understands SDK XML versions up to 2 but an SDK XML file of version 3 was encountered.
- Gradle 버전을 최신으로 올렸더니 나타난 에러

### Unsupported class file major version 55
- 처음 깃허브에서 프로젝트 파일을 가져왔을 때 뜨기 시작

## 해결 
- Gradle 버전을 studio에서 제시한 대로 업그레이드.
- 앞자리를 유지하면서 뒷자리 버전만 업그레이드.
- 여타 다른 플러그인 버전을 변경하는 것이 아닌 Gradle 버전만 변경하여 문제 해결