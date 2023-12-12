컴포넌트는 Angular 애플리케이션을 구성하는 기본 단위

개별 컴포넌트 구성요소 :
	- 화면을 렌더링하는 HTML 템플릿
	- 동작을 정의하는 TypeScript 클래스
	- 컴포넌트를 템플릿에 추가할 때 사용하는 CSS 셀렉터
	- 추가로 컴포넌트가 표시되는 모습을 정의하는 CSS 스타일
## 컴포넌트 생성하기

```shell
ng generate component <컴포넌트-이름>
```
 명령을 실행해서 컴포넌트를 생성

- 컴포넌트 이름으로 폴더가 생성됨
- `<컴포넌트-이름>.component.ts` 컴포넌트 파일 생성
- `<컴포넌트-이름>.component.html` 템플릿 파일 생성
- `<컴포넌트-이름>.component.css` CSS 스타일 파일 생성
- `<컴포넌트-이름>.component.spec.ts` 테스트 파일 생성

### 수동으로 컴포넌트 생성하기

1. Angular 프로젝트로 이동합니다.
2. `<컴포넌트-이름>.component.ts` 라는 이름으로 새 파일을 만듭니다.
3. 이 파일 시작부분에 이런 코드를 추가합니다.
```ts
import { Component } from '@angular/core';
```

4. 그리고 `import` 구문 뒤에 `@Component` 데코레이터를 추가
5. 컴포넌트에 적용할 CSS 셀렉터를 지정
6. html 템플릿 정의, 별도의 파일 이용
7. 컴포넌트 템플릿에 지정될 스타일 파일 생성, 별도의 파일 정의
8. 컴포넌트 클래스를 정의하는 `class` 구문 추가
```ts

@Component({
	selector: 'app-component-overview',
	templateUrl: './component-overview.component.html',
	styleUrls: ['./component-overview.component.css']
})

export class ComponentOverviewComponent { 
}

```


## 컴포넌트 템플릿 정의하기
```ts
@Component({
  selector: 'app-component-overview',
  template: `
    <h1>Hello World!</h1>
    <p>This template definition spans multiple lines.</p>
  `
})
```

## 컴포넌트 스타일 지정하기

컴포넌트 스타일을 별도 파일로 정의하려면 `@Component` 데코레이터의 `styleUrls` 프로퍼티를 지정
```ts
@Component({
  selector: 'app-component-overview',
  templateUrl: './component-overview.component.html',
  styleUrls: ['./component-overview.component.css']
})
```

컴포넌트 안에 스타일을 지정하려면 `@Component` 데코레이터의 `styles` 프로퍼티에 원하는 스타일을 지정
```ts
@Component({
  selector: 'app-component-overview',
  template: '<h1>Hello World!</h1>',
  styles: ['h1 { font-weight: normal; }']
})
```

