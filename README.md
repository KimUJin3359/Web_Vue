# Web_Vue

### Vue.js
#### Front-end 개발 방향
- 화면을 구성하는 Front-end
  - 웹 페이지 기능이 많아짐
  - 개발 코드량이 많아짐
- Front-end Framework의 필요성
  - 빠른 DOM 제어와 Component 기반 웹 개발을 위함
    - Component 단위로 조립식으로 웹페이지 UI 개발 (생산성 UP/가독성 UP)
    - Virtual DOM : jQuery의 비효율적 DOM 제어 개선 (웹페이지 성능 UP)
    
#### Vue.js란?    
- **Progressive** JavaScript Framework
  - JavaScript 프로젝트에서, 점진적으로 수정해 나가면서 Vue.js를 적용
  - 즉 수정하는 방식으로 적용하는 프레임워크
- {{ 변수명 }}
  - vue Instance를 하나 만들어야 함
  - el : DOM element(선택자를 써줌)
  - data : 변수들이 들어가는 속성
  ```
  let app = new Vue({
    el: '.container'
    data: {
      msg: 'This is a container'
    }
  })
  ```
- 클릭 이벤트
  - v-on:click 이벤트 등록
  - @click 이벤트 등록
  - data에 있는 변수들은 전역변수로 this를 사용하여 접근 가능
  - 값 변경을 하면 즉시 반영됨
  
  >> [Vue객체 생성 및 변수, 클릭 이벤트 활용](https://github.com/KimUJin3359/Web_Vue/blob/master/001.Vue/ex00.html)

  >> [클릭 이벤트를 활용하여 변수 값 바꾸기](https://github.com/KimUJin3359/Web_Vue/blob/master/001.Vue/ex01.html)

#### 단방향 Data Binding
- Data Binding
  - Vue Instance의 값을 수정하면 즉시 반영
  - 단방향 Binding이라 함
  - v-bind: 단방향 Binding, Tag 속성에 값을 넣을 수 있음
  
  >> [v-bind를 활용한 변수값 변경](https://github.com/KimUJin3359/Web_Vue/blob/master/001.Vue/ex02.tag_binding.html)
  
  >> [v-bind를 통한 class변경으로 글자 색깔 바꾸기](https://github.com/KimUJin3359/Web_Vue/blob/master/001.Vue/ex03.change_attribute.html)
  
#### 양방향 Data Binding
- HTML Form 또는 Vue 영역 값 동기화
  - HTML Form의 값을 바꾸면, Vue 변수에 값이 변경됨
  - Vue 변수에 값을 변경하면, HTML Form의 값이 변경됨
  - v-model: input의 값을 수정하면, HTML 출력도 변경
  
  >> [v-model과 v-bind의 Binding 확인](https://github.com/KimUJin3359/Web_Vue/blob/master/001.Vue/ex04.v_model.html)
  
  >> [v-model과 click 이벤트 활용](https://github.com/KimUJin3359/Web_Vue/blob/master/001.Vue/ex05.html)
  
### Vue.js의 기본 원리
#### Virtual DOM
- Browser가 HTML을 출력하는 원리
  1) HTML을 Parsing하여 DOM Tree 생성
  2) Render Tree 생성
    - 각 DOM Tree의 Node에 Style 정보를 입힘
  3) Layout 과정
    - 각 Render Tree Node들의 출력 할 좌표가 계산되어 정해짐
  4) Painting
    - 이미지, color를 입혀 출력을 준비하는 과정
- Virtual DOM의 필요성
  - 일반적인 DOM 변경 발생 시, Render Tree부터 재시작이 이루어짐
    - DOM을 제어할 때마다 Client Browser의 속도 저하가 발생
- Virtual DOM 동작 방식
  1) 실제의 DOM Tree를 기반으로 Virtual DOM Tree 생성
  2) DOM 제어를 Virtual DOM Tree에 모두 적용
  3) 모든 DOM 제어가 끝났을 때, Virtual DOM Tree를 실제의 DOM Tree에 적용
  4) 렌더링 시작

#### 조건문과 반복문
- 조건문
  - v-if
  - v-elseif
  - v-else
  
  >> [조건에 따른 메시지 출력](https://github.com/KimUJin3359/Web_Vue/blob/master/003.Vue(cluase)/ex00.vs-if.html)
  
  >> [조건에 따른 블록 출력](https://github.com/KimUJin3359/Web_Vue/blob/master/003.Vue(cluase)/ex01.html)

- 반복문  
  - v-for
    - LIST, 메뉴를 출력하는 용도
    ```
    <li v-for="node in list">
      {{ node.text }}
    </li>
    ```
  
  >> [배열에 있는 값을 v-for를 활용해 출력](https://github.com/KimUJin3359/Web_Vue/blob/master/003.Vue(cluase)/ex02.for.html)
  
  >> [v-for, v-if를 활용한 배열 출력](https://github.com/KimUJin3359/Web_Vue/blob/master/003.Vue(cluase)/ex03.html)
  
### MVVM 패턴
- 디자인 패턴
  - 프로그래밍 개발 시 자주 나타나는 문제를 해결하기 위한 방법, 규약을 묶어 이름을 붙인 것
  - 디자인 패턴 이용시 협업이 수월하며, 유지보수가 좋음
- MVVM 패턴  
  - Vue.js로 웹 개발하는 방식은 MVVM 패턴
  - 세 가지 역할이 존재
    - Model : 실제 데이터를 처리하는 소스코드
    - View : UI에 해당하는 소스코드
    - ViewModel : View를 표현하기 위해 만들어진 코드
- Vue.js의 역할
  - ViewModel 부분을 Vue.js가 담당
  - 동작 과정
    1) 사용자는 View를 통해 입력
    2) View에서 이벤트 발생 시, View Model의 콜백 함수를 호출
    3) ViewModel은 Model에게 필요한 데이터를 요청하고, 전달 받음
    4) ViewModel은 받은 데이터를 가공하여 저장
    5) ViewModel에서 저장하면, Binding으로 인해 View의 값이 자동 갱신
  
  >> [MVVM 모델을 구현하여 ViewModel 변경시, View의 값을 변경](https://github.com/KimUJin3359/Web_Vue/blob/master/002.DesignPattern/ex00.MVVM.html)
  
### Vue.js의 Life Cycle
![lifecycle](https://user-images.githubusercontent.com/50474972/110499787-ec278a80-813b-11eb-9eb7-986116820b49.png)
- beforeCreate
  - 가장 먼저 실행되는 라이프사이클
  - 컴포넌트가 DOM에 추가되기 전(데이터 접근 불가)
- created
  - 데이터, computed, methods에 접근은 가능하나 DOM에는 추가되지 않음
- beforeMount
  - Virtual DOM은 생성되었으나, 실제 DOM은 없는 상태
- mounted
  - 가장 많이 사용
  - 가상 DOM이 실제 DOM에 부착되고 실행
  - axios 등 통신 호출은 최소 mounted 이후에 사용
- beforeUpdate
  - data가 변해서 변화를 적용시키기 바로 전에 실행
- updated
  - data가 변경되서, DOM에 적용된 상태
  - 값에 직접 접근할 때 사용
  - 여기서 data를 변경시키면 무한 루프가 발생할 수 있음
- beforeDestroy
  - 인스턴스가 해체되기 직전
  - 이 때 eventListener 등을 해체
- destroyed
  - 해체가 끝난 이후
  - 인스턴스 속성에 접근 불가
  
  >> [Lifecycle에 따른 동작 방식 파악](https://github.com/KimUJin3359/Web_Vue/blob/master/004.Vue(life-cycle)/ex00.html)
  
  >> [Vue의 간단한 component 실습](https://github.com/KimUJin3359/Web_Vue/blob/master/005.Vue(component)/ex00.component.html)
    - v-bind:key 및 v-bind:prop을 통해 component를 불러옴

  >> [Vue를 활용한 간단한 계산기 생성](https://github.com/KimUJin3359/Web_Vue/blob/master/005.Vue(component)/ex01.calculator.html)
  
  >> [Vue를 활용한 끝말잇기 게임](https://github.com/KimUJin3359/Web_Vue/blob/master/005.Vue(component)/ex02.wordrelay.html)
  
  >> [Component를 활용한 끝말잇기 게임](https://github.com/KimUJin3359/Web_Vue/blob/master/005.Vue(component)/ex03.wordrelaycomponent.html)
  
  >> [Vue를 활용한 곱하기 게임](https://github.com/KimUJin3359/Web_Vue/blob/master/005.Vue(component)/ex04.multiple.html)
  
  
  






