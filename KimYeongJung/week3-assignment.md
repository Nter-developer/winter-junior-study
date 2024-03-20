## Markdown

### 마크 다운이란
- 텍스트 기반의 마크업 언어로 쉽게 쓰고 읽을 수 있음 & HTML로 변환이 가능
- 특수 기호와 문자를 이용한 매우 간단한 구조의 문법을 사용하여 웹에서 보다 빠르게 컨텐츠를 작성하고 보다 직관으로 인식 가능
### 사용되는 곳과 이유
- Github의 Repository에 관한 정보를 기록하는 README 파일에서 사용된다(what, when)
- 설치 방법, 소스코드 설명, 이슈 등을 간단하게 기록하고 가독성을 높일 수 있다는 강점이 있기에 사용(why)

|왼쪽 정렬|가운데 정렬|오른쪽 정렬|
|:---|:--:|---:|
|1|2|3|
|4|5|6|
|7|8|9|
---
## UI Resource

### drawable
- drawable은 상태에 따라 그래픽이나 이미지가 선택적으로 보일 수 있게 한다.
- ex) 버튼이 눌렸을 때 눌린 이미지가 보이게 설정 가능

#### 종류
- BitmapDrawable : 이미지 파일을 보여줄 때 사용
- StateListDrawable : 상태별로 다른 비트맵 그래픽을 참조
- TransitionDrawable : 두 개의 드로어블을 서로 전환 가능
- SafeDrawable : 색상과 그라데이션을 포함하여 도형 모양을 정의 가능
- InsetDrawable : 지정된 거리만큼 다른 드로어블을 들어서 보여줄 수 있음
- ClipDrawable : 레벨 값을 기준으로 다른 드로어블을 클리핑 가능
- ScaleDrawable : 레벨 값을 기준으로 다른 드로어블의 크기를 변경 가능

 ### Values
- 여러가지 값들을 저장할 수 있는 것
- 같은 값들을 여러 번 사용해야 할 때 values 값을 이용해 내가 설정해 놓은 값들을 불러올 수 있다.
- 편리성을 높일 수 있기에 사용

#### colors
- 색상 값을 저장한다
```
<color name = "MYRED">#FF0000</color>
```

#### strings
- 문자열을 저장한다 & 문자열 배열도 저장 가능
```
<string name="TEXT1">Test 첫 번째 </string>
```

#### dimens
- 치수 값을 저장
```
<dimen name="textview_height">25dp</dimen>
```

#### styles
- 스타일을 설정
```
<style name = "mySTYLE">
        <item name = "android:text">TEST</item>
        <item name = "android:textSize">30dp</item>
        <item name = "android:textColor">#ff0000</item>
</style>
```
---

## Swager

### Swager란
- 웹 서비스 명세를 문서화 해주는 오픈 소스 소프트웨어 프레임워크이다.
- 백엔드 팀이 만든 서비스를 swagger로 문서화해서 프론트 팀으로 넘겨 로직의 이해를 돕는다
- 계속해서 변경되는 명세 문서를 알아서 주기적으로 업데이트를 해주어 시간 절약을 돕는다.

---

## GitHub Actions

### CI/CD의 개념
- 개발자가 개발을 마친 후 appication을 빌드, 테스트, 원격 저장소에 코드 업데이트, 배포 등의 과정을 자동화하는 과정을 의미한다.
- 대부분의 실무 환경에서는 CI/CD를 진행

#### CI
- 지속적 통합이라는 의미로 개발자를 위해 빌드와 테스트를 자동화하는 과정이다
- 여러 명이 동시 작업하는 경우 충돌 방지 및 모니터링이 가능하다

#### CD
- 지속적 제공이라는 의미로 배포 준비가 된 코드를 자동으로 서버에 배포하는 작업을 자동화하는 것이다.
- 수작업으로 배포하지 않아도 되므로 편리성이 뛰어나다

### GitHub Actions
- 깃허브 액션은 깃허브에서 제공하는 서비스로 repository에 특정 이벤트가 발생하면 특정 작업을 하거나, 주기적으로 특정 작업을 반복할 수 있게 하는 것이다.
- ex) 코드를 업데이트하면 해당 코드에 문제가 없는지 자동으로 코드를 빌드, 테스트한 이후 배포까지 가능
- 이러한 이유로 GitHub Actions을 사용한다.