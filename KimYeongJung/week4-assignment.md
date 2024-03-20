## 기술 블로그 & GitHub README

### 기술 블로그
	https://kim0jung.tistory.com/

### GitHub README
	https://github.com/kim0jung
---
## Logging

### Logging이란
- 어플리케이션을 운영하던 중에 문제가 발생하였을 때 문제의 원인을 파악해야 하는데 파악하기 위해서는 날짜, 시간, 서비스, 로직 등에 대한 정보가 필요하다. 이런 정보를 얻기 위해 사용하는 것이 log로 Exception이 발생하거나 중요한 기능들이 실행되는 부분에 남긴다. 이렇게 log를 남기는 행동을 logging이라고 한다.

### 로그 출력 방법
	1. System.out.println()
	2. Logging 라이브러리

### System.out.println() 특징
	- 속도가 느리다
	- 최소한의 정보가 없다 (날짜/시간/타입 등등)
	- 콘솔창에 출력만 하므로 나중에 확인 불가능하다
	- 데이터를 쌓고 남기기 어렵다

### Logging 라이브러리 특징
	- 최소한의 정보 제공
	- 데이터를 서버에 저장 및 파일화 가능

### Log Level
- Trace > Debug > Info > Warn > Error > Fatal
- Trace : Debug보다 상세한 정보 -> Debug로 대체 가능
- Debug : 프로그램 디버깅
- Info : 상태변경과 같은 정보성 메시지
- Warn : 처리 가능한 문제(문제가 될 수 있는 것) -> Info로 대체 가능
- Error : 요청 처리 중 문제
- Fatal : 아주 심각한 에러 -> Error로 대체 가능
---
## Git Squash & Rebase

### Git Squash란
- 여러 개의 커밋을 하나의 커밋으로 합치는 방법으로 커밋을 깔끔하게 정리할 수 있도록 해준다.

### Rebase
- 한 브랜치에서 다른 브랜치로 합치는 방법으로 Merge와 비슷하다
- Merge와 실행결과는 같지만 커밋의 히스토리가 달라진다
- Rebase는 Merge와 달리 위험성이 있고 까다롭지만 커밋 히스토리를 깔끔하게 관리할 수 있다.

##### Merge와의 차이점
- Merge는 3-way Merge로 새로운 커밋을 생성하는 것이다.

Rebase는 

    git checkout 브랜치이름
    git rebase master

이 코드를 통해 내부에서는 master가 base가 되고 master와 통합할 브랜치의 차이를 임시 저장 공간(Patch)에 저장한다.
이렇게 되면 커밋 히스토리는 깔꿈하게 정리되고 마지막으로 master브랜치를 Fast-forward시키면 끝난다.

    git checkout master
    git merge experiment

##### Rebase의 위험성
- 이미 공개해서 사람들이 사용하는 커밋을 rebase하면 반드시 문제가 생긴다. (협업 없이 혼자 사용하는 경우 문제 X)
- 협업 중에서는 push전에만 rebase를 사용하는 것을 권장한다.