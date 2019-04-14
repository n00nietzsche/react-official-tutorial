# 들어가기 전에
- 이 포스팅은 https://reactjs.org/tutorial/tutorial.html 에 있는 포스팅을 번역한 것입니다. 오역이나 의역이 있을 수 있습니다. 지적해주시면 확인 후 바로 정정하겠습니다.

- original source of this posting is from https://reactjs.org/tutorial/tutorial.html If the original author requests deletion, it will be deleted immediately.

- Translated by Jake Seo (서진규)

	- https://velog.io/@jakeseo_me
	- https://github.com/n00nietzsche
    
> 리액트 튜토리얼 공식문서 (번역)

# 튜토리얼을 시작하기 전에

이 튜토리얼을 진행하며 우리는 작은 게임을 만들어볼 것입니다. 게임을 만든다는 것이 별로 흥미롭게 느껴지지 않을 수 있지만 일단 한번 만들어보세요. 튜토리얼 동안 우리가 배우는 기술은 리액트 앱을 만드는데 있어서 매우 근본적인 기술입니다. 완벽히 이해하고 마스터한다면 리액트에 대한 깊은 이해가 생길 것입니다.

> 이 튜토리얼은 무언가 하면서 배우는 사람들을 위해 디자인되었습니다. 맨땅에서 개념부터 배우고 싶으신 분들은 [step-by-step 가이드](https://reactjs.org/docs/hello-world.html) 를 참고해주세요. 이 튜토리얼과 가이드는 상호보완적이라는 것을 알게 될 것입니다.

이 튜토리얼은 몇가지 섹션으로 나누어져있습니다.

- `튜토리얼을 위한 세팅` 에서는 튜토리얼을 따라가기 위한 시작점을 제공할 것입니다.
- `개요` 에서는 리액트 핵심 요소들 : components, props, state 에 대해 알려줄 겁니다.
- `게임 완성하기` 에서는 리액트 개발에서 쓰이는 일반적인 테크닉에 대해 알려줄 겁니다.
- `시간여행 추가하기` 에서는 리액트의 특별한 힘에 대한 더 깊은 이해를 줄 것입니다.

이 튜토리얼에 있는 모든 가치를 끌어내기 위해 모든 섹션을 한번에 완성할 필요는 없습니다. 1~2 섹션이라도 괜찮으니 할 수 있는 만큼 하세요.

## 우리는 무엇을 만드나요?

이 튜토리얼에서, 우리는 리액트를 이용하여 인터렉티브한 틱택토 게임을 만들 것입니다.

여기서 우리가 만들 [최종 결과물](https://codepen.io/gaearon/pen/gWWZgR?editors=0010)을 확인할 수 있습니다. 코드가 잘 이해되지 않거나 익숙하지 않은 문법이 나왔더라도 걱정하지 마세요! 이 튜토리얼의 목표는 그것들을 알려주는 것이니까요.

이 튜토리얼을 계속하기 전에 틱택토 게임이 어떤 것인지 확인하는 것을 추천합니다. 게임을 유심히 보면 오른쪽에 숫자로된 리스트가 있다는 것을 눈치챘을 것입니다. 그 리스트는 게임에서 움직였던 모든 기록을 갖고 있습니다. 그리고 게임이 진행되며 업데이트됩니다.

틱택토 게임이 뭔지 대충 알았다면 끄셔도 좋습니다. 이 튜토리얼에서는 우리는 더 간단한 템플릿부터 시작할 것입니다. 다음 단계는 게임을 만들기 위한 셋팅입니다.

## 튜토리얼에 필요한 선수지식

일단 HTML과 자바스크립트에 대해서는 어느정도 안다고 생각하고 진행할 것이지만 다른 언어를 하다가 왔다고 해서 튜토리얼을 진행할 수 없는 것은 아닙니다. 또 함수, 오브젝트, 배열 그리고 클래스와 같은 개념에 대해서도 어느정도 친숙하다고 가정할 것입니다.

자바스크립트를 다시 봐야할 것 같다면 [이 가이드](https://developer.mozilla.org/en-US/docs/Web/JavaScript/A_re-introduction_to_JavaScript)를 추천드립니다. 또 최신 자바스크립트 버전인 ES6에서 사용되는 개념들을 다룰 것이라는 걸 알아두세요. 이 튜토리얼에서 우리는 [화살표 함수](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions), [클래스](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes), [let](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/let), [const](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/const)를 사용할 것입니다. [Babel REPL](https://babeljs.io/repl/#?presets=react&code_lz=MYewdgzgLgBApgGzgWzmWBeGAeAFgRgD4AJRBEAGhgHcQAnBAEwEJsB6AwgbgChRJY_KAEMAlmDh0YWRiGABXVOgB0AczhQAokiVQAQgE8AkowAUAcjogQUcwEpeAJTjDgUACIB5ALLK6aRklTRBQ0KCohMQk6Bx4gA)을 이용하여 ES6코드가 어떻게 컴파일되는지 확인할 수 있습니다.

# 튜토리얼 세팅하기

이 튜토리얼을 무사히 마치기 위해선 2가지 방법이 있습니다 : 브라우저에 코드를 작성할 수도 있고, 컴퓨터에 로컬 개발 환경을 구축할 수도 있습니다.

## 옵션 1 : 브라우저에 코딩하기

튜토리얼을 시작하기 위한 가장 빠른 방법입니다!

먼저 [스타터 코드](https://codepen.io/gaearon/pen/oWWQNa?editors=0010) 창을 새 탭에 띄우고, 새 탭이 빈 코드 창을 띄우게 하세요. 이 튜토리얼에서 우리는 리액트 코드를 편집할 것입니다.

옵션 1을 선택하셨다면 옵션 2는 스킵하시고 `개요`파트로 가셔도 됩니다.

## 옵션 2 : 로컬 개발 환경

옵션 : 이건 다분히 개인이 선택해야 할 문제입니다. 이번 튜토리얼에선 절대 필수가 아닙니다.

이 세팅은 더 많은 작업을 요구하지만 우리가 에디터를 이용해 모든 튜토리얼을 끝낼 수 있게 만들어줍니다. 다음과 같이 작업하시면 됩니다.

1. 최신 버전의 [노드js](https://nodejs.org/en/)가 설치되었는지 확인해주세요.
2. [Create React App 설치 가이드](https://reactjs.org/docs/create-a-new-react-app.html#create-react-app)를 따르시고 새 프로젝트를 만드세요.

```bash
npx create-react-app my-app
```
3. 새 프로젝트의 `src/` 폴더 내부의 모든 파일을 지워주세요.

> 알아둬야 할 것 :
> src 폴더 전체를 지우지 마세요. 그냥 안에 있는 파일만 지우세요. 안에 있는 소스파일들은 다음 스텝에서 우리가 새로 작성할 예제로 채울 것입니다.

4. `index.css`파일을 `src/` 폴더에 [이 CSS코드](https://codepen.io/gaearon/pen/oWWQNa?editors=0100)로 추가해주세요.
5. `index.js`파일을 `src/` 폴더에 [이 JS코드](https://codepen.io/gaearon/pen/oWWQNa?editors=0010)로 추가해주세요.
6. `src/`폴더에 `index.js` 파일의 맨 위에 이 3줄을 추가해주세요.

```js
import React from 'react';
import ReactDOM from 'react-dom';
import './index.css';
```

이제 프로젝트 폴더에서 `npm start`를 입력하고 브라우저에서 `http://localhost:3000`으로 접속하면 빈 틱택토 게임을 볼 수 있을 것입니다.

문법 하이라이팅을 위해서 [이 가이드](https://babeljs.io/docs/en/editors/)를 따라하시는 것을 권장합니다.

## 도와주세요! 여기서 막혔어요!

막혔다면 [커뮤니티 서포트 리소스](https://reactjs.org/community/support.html)를 확인하세요. 특히, [Reactiflux Chat](https://discordapp.com/invite/0ZcbPKXt5bZjGY5n)은 즉각적인 도움을 받기에 아주 좋은 곳입니다. 만일 답을 받지 못하거나 계속 막혀있다면 이슈를 올려주세요. 저희가 도와드리겠습니다!

# 개요

이제 세팅이 끝났습니다. 리액트의 개요로 가봅시다!

## 리액트란 무엇인가요?

리액트는 UI를 만들기 위한 선언형이고 효율적이며 유연한 자바스크립트 라이브러리입니다. '컴포넌트'라고 불리는 작고 분리된 코드로부터 우리가 복잡한 UI들을 조립하게 해줄 것입니다. 

리액트는 몇가지 다른 종류의 컴포넌트를 갖고 있습니다. 하지만 우리는 `React.Component` 하위 클래스들부터 다뤄보겠습니다.

```javascript
class ShoppingList extends React.Component {
	render() {
		return (
			<div className="shopping-list">
				<h1>Shopping List for {this.props.name}</h1>
				<ul>
					<li>Instagram</li>
					<li>WhatsApp</li>
					<li>Oculus</li>
				</ul>
			</div>
		)
	}
}
```

우리는 곧 이상한 XML같은 태그를 찾게 될 것입니다. 우리는 우리가 스크린에서 무엇을 보길 원하는지 컴포넌트를 이용해 리액트에게 말합니다. 우리의 데이터가 바뀔 때, 리액트는 효율적으로 우리의 컴포넌트를 업데이트하고 재렌더링합니다.

여기 ShoppingList는 **리액트 컴포넌트 클래스** 또는 **리액트 컴포넌트 타입**입니다. 컴포넌트는 `props`라 불리는 파라미터를 받으며 `render`메소드를 통해 보여줄 뷰의 계층을 리턴합니다.

`render` 메소드는 우리가 화면에서 무엇을 보길 원했는지에 대한 *기술(description)* 을 반환합니다. 리액트는 description을 받고 결과를 보여줍니다. `render`는 무엇을 렌더링할지에 대한 간단한 description인 **리액트 엘리먼트**를 반환합니다. 대부분의 리액트 개발자들은 이 구조를 더욱 쉽게 쓸 수 있게 만들어주는 'JSX'라고 불리는 특별한 문법을 사용합니다. `<div />` 문법은 빌드될 때 `React.createElement('div')`의 형태로 변환됩니다. 위의 예제는 사실 다음 코드와 동일합니다.

```javascript
return React.createElement('div', {className: 'shopping-list'},
                           React.createElement('h1', /* ... h1 children ... */),
                           React.createElement('ul', /* ... ul children ... */)
                           );
```

[풀버전은 여기](https://babeljs.io/repl/#?presets=react&code_lz=DwEwlgbgBAxgNgQwM5IHIILYFMC8AiJACwHsAHUsAOwHMBaOMJAFzwD4AoKKYQgRlYDKJclWpQAMoyZQAZsQBOUAN6l5ZJADpKmLAF9gAej4cuwAK5wTXbg1YBJSswTV5mQ7c7XgtgOqEETEgAguTuYFamtgDyMBZmSGFWhhYchuAQrADc7EA)에 있습니다.

만일 `createElement()`에 대해 더 상세히 알고 싶으시다면, [API 레퍼런스](https://reactjs.org/docs/react-api.html#createelement)를 참조하세요. 튜토리얼에서는 함수를 직접 호출하지 않고 계속 JSX를 사용할 것입니다.

JSX에는 자바스크립트의 모든 힘이 담겨있습니다. 어떤 자바스크립트 표현식이라도 JSX의 괄호 안에 넣을 수 있습니다. 각각의 리액트 엘리먼트는 우리가 저장할 수 있고 어딘가로 넘길 수 있는 자바스크립트 오브젝트입니다. 

위의 `ShoppingList` 컴포넌트는 `<div />`나 `<li />` 같은 빌트인 DOM만을 렌더링하지만 우리는 커스텀 리액트 컴포넌트도 조합하고 렌더링 할 수 있습니다. 예를 들면, `<ShoppingList/>`를 적음으로써 우린 ShoppingList 전체 내용을 한번에 참조 할 수도 있습니다. 각각의 리액트 컴포넌트는 캡슐화되어 있고 독립적으로 동작할 수 있습니다. 이러한 특성은 우리가 간단한 컴포넌트로부터 복잡한 UI를 만들 수 있게 허용해줍니다.

## 스타터 코드 살펴보기

만일 **브라우저**에서 튜토리얼을 진행 중이라면, 이 [스타터 코드](https://codepen.io/gaearon/pen/oWWQNa?editors=0010)를 새 탭에서 열어주세요. 로컬에서 진행한다면 프로젝트 폴더의 `src/index.js`파일을 열어주세요. 

이 스타터 코드는 우리가 만들 게임의 기반이 되는 코드입니다. CSS 스타일링은 제공되어 있으니 우리는 리액트를 배우는 것과 틱택토 프로그래밍을 하는 것에만 집중하면 됩니다.

코드를 살펴보면 우리는 3가지 리액트 컴포넌트를 발견할 수 있습니다.

- Sqaure
- Board
- Game

Square 컴포넌트는 하나의 `<button>`을 렌더링하고 Board 컴포넌트는 9개의 Square 컴포넌트를 렌더링합니다. 게임 컴포넌트는 placeholder 를 가진 Board를 렌더링합니다. 이 컴포넌트는 우리가 나중에 수정하게 될 것입니다. 현재에는 어떠한 상호작용하는 컴포넌트도 존재하지 않는 상태입니다.

## Props를 통한 데이터 전달

이제 본격적으로 처음 시작하기 위해, 데이터를 Board 컴포넌트에서 Square 컴포넌트로 옮겨봅시다.

튜토리얼을 진행하며 코드는 복사 붙여넣기를 하기보다 손으로 직접 치는 것을 강력히 권장합니다. 손으로 치는 과정은 우리에게 머슬 메모리를 개발시키고 더 깊은 이해를 할 수 있게 도와줍니다.

Board의 `renderSquare` 메소드에서, Square에 `value`라 불리는 prop을 전달하기 위해 코드를 잠시 변경해주세요.

```js
class Board extends React.Component {
	renderSquare(i) {
		return <Square value={i} />;  
    }
}
```

Square의 `render` 메소드가 그 값을 보여줄 수 있도록 `{/* TODO */}` 부분을 `{this.props.value}`로 바꿔주세요.

```js
class Square extends React.Component {
	render() {
		return (
			<button className="square">
				{this.props.value}
			</button>
		)
	}
}
```

이전:

![before_prop.png](https://images.velog.io/post-images/jakeseo_me/0de28e20-5e40-11e9-8e03-551282fb0315/beforeprop.png)

이후:

![after_prop.png](https://images.velog.io/post-images/jakeseo_me/1817ed90-5e40-11e9-8e03-551282fb0315/afterprop.png)

[현재까지 한 전체 코드 보기](https://codepen.io/gaearon/pen/aWWQOG?editors=0010)

축하합니다! 방금 부모 Board 컴포넌트에서 자식 Square 컴포넌트로 prop을 넘기는데 성공하였습니다. prop을 넘기는 것은 리액트 앱에서 부모에서 자식으로 정보가 어떻게 흘러가는지를 설명합니다.

## 상호작용하는 컴포넌트 만들기

Square 컴포넌트를 클릭했을 때 그 자리에 'X'가 채워지도록 만들어봅시다. 처음으로 Square 컴포넌트의 `render` 함수에서 리턴되는 버튼 태그를 변경합시다.

```js
class Square extends React.Component {
	render() {
		return (
			<button className="square" onClick={function () { alert('click'); }}>
				{this.props.value}
			</button>
		)
    }
}
```

Square에 있는 버튼을 클릭하게되면 alert 메세지를 볼 수 있을 것입니다.

> **알아두기**
> 타이핑을 더 적게하고 [this의 헷갈리는 사용법](https://yehudakatz.com/2011/08/11/understanding-javascript-function-invocation-and-this/)을 피하기 위해서 우리는 이벤트 핸들러에 [화살표 함수](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions)를 쓸 것입니다. 
```js
class Square extends React.Component {
  render() {
    return (
      <button className="square" onClick={() => {alert('click')}>
        {this.props.value}
      </button>
    );
  }
}
```
> `onClick={() => alert('click')}`가 어떻게 쓰였는지 알아봅시다. `onClick`의 prop으로 우리는 함수를 넘겨주었습니다. 리액트는 클릭이 발생한 후에 이 함수를 실행할 것입니다. `() =>`을 적는 걸 까먹고 `onClick={alert('click')}` 만 적지 않도록 조심하세요. 흔히들 하는 실수입니다. 그리고 매번 컴포넌트가 재렌더링 될 때마다 alert가 일어날 것입니다.

다음 단계로 우리는 Square 컴포넌트가 클릭됐을 때, 클릭됐던 것을 기억하게 만들고 "X"마크를 채우고 싶습니다. 무언가를 기억하기 위해 컴포넌트는 **상태(state)** 라는 것을 사용합니다.

리액트 컴포넌트는 생성자에 `this.state`를 세팅함으로써 상태를 가질 수 있습니다. `this.state`는 정의된 리액트 컴포넌트 내부의 private 하게 적용된다고 생각하시면 됩니다. Square의 현재 값을 `this.state`에 저장해봅시다. 그리고 Square가 클릭됐을 때 그것을 변경해봅시다.

먼저, 클래스에 상태를 초기화하는 생성자를 만들 것입니다.

```js
class Square extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      value: null,  
    };
  }
  
  render() {
    return (
      <button className="square" onClick={() => alert('click')}>
        {this.props.value}
      </button>
    );
  }
}
```

> **알아두기** 
자바스크립트 클래스에서 하위 클래스의 생성자를 정의할 때는 항상 `super`를 호출해야 합니다. 생성자를 가진 모든 리액트 컴포넌트 클래스들은 `super(props)`를 호출하면서 시작해야 합니다.

이제 우리는 클릭됐을 때, 현재 상태의 값을 나타내주기 위해 Square의 `render` 메소드를 수정할 것입니다.
- `<button>`태그 안에 있는 `this.props.value`를 `this.state.value`로 바꿔주세요.
- `onClick={...}` 이벤트 핸들러를 `onClick={() => this.setState({value: 'X'})}`로 바꿔주세요.
- `className`과 `onClick`을 각각 다른 줄에 표기하는 것이 가독성이 좋습니다.

