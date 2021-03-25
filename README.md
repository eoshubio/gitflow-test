# Merge / Squash Merge with Fork

사람이 많아지면 git tree 의 가독성이 떨어져서 문제가 생겼을때 내려간다던지 특정 릴리즈의 커밋을 찾는데 난감함. 4명일 경우엔 문제가 작지만 50명이면 문제가 생길 것 같음. 그래서 정리해봄.

## 결론

| Merge | Squash Merge |
| --- | --- |
|![스크린샷 2021-03-25 오전 11 36 08](https://user-images.githubusercontent.com/34477359/112410290-4b051a80-8d5e-11eb-8dae-023a923b0a62.png)|![스크린샷 2021-03-25 오전 11 37 24](https://user-images.githubusercontent.com/34477359/112410387-7851c880-8d5e-11eb-85e7-f41ae97c7163.png)|
||commit 1개로 머지되지만 흔적이 남음.|


| Fork + Merge | Fork + Squash Merge |
| --- | --- |
| ![스크린샷 2021-03-25 오전 11 38 27](https://user-images.githubusercontent.com/34477359/112410504-9f0fff00-8d5e-11eb-96e4-b540ce95cbb8.png)|![스크린샷 2021-03-25 오전 11 39 43](https://user-images.githubusercontent.com/34477359/112410611-cb2b8000-8d5e-11eb-9ee1-35a9cbb62beb.png)|
|그냥 Merge 랑 똑같음 | commit 1개로 머지되고 흔적이 안남음 (로컬 git 에만 남음)|

## fork 된 git 관리

#### 1. upstream  등록
원본 git 을 upstream 으로 등록합니다.
```shell
$ git remote add upstream https://github.daumkakao.com/tistory/tistory-ios.git
$ git remote -v (잘 등록되었는지 확인)
```

#### 2. fetch + rebase
PR 전에 develop 을 원본 git 으로 rebase 합니다.
```shell
$ git checkout develop
$ git fetch upstream develop
$ git rebase upstream/develop
$ git push
```

#### 3. PR 후 Merge


