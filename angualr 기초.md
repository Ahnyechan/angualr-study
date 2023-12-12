https://angular.kr/guide/what-is-angular


Angular는 [TypeScript](https://www.typescriptlang.org/)를 기반으로 개발된 개발 플랫폼:

- 확장가능한 컴포넌트 구조로 웹 애플리케이션을 만드는 프레임워크
- 라우팅, 폼 관리, 클라이언트-서버 통신 등 웹 개발에 필요한 라이브러리를 조화롭게 통합한 모음집
- 애플리케이션 개발, 빌드, 테스트, 수정에 필요한 개발자 도구를 제공
## Angular 애플리케이션: 기초

#### Angualr CLI 설치
  
```shell
npm install -g @angular/cli  
npm i -g @angular/cli
```

- angular version 확인
```shell
ng -v            
ng --version
```

| 옵션|기능|사용 예|
|---|:---|:---:|
|--dry-run( alias: -d )|생성 전에 생성 할 파일들을 보여준다.|$ng new <project_name> --dry-run|
|--inline-style(alias: -is)|css file을 생성하지 않고 line으로 style을 삽입|$ng new <project_name> -is|
|--inlin-template(alias: -it)|html file을 생성하지 않고 line으로 template을 삽입|$ng new <project_name> -it|
|--directory(alias: -dir)|앱의 디렉토리 이름을 지어줌|$ng new <project_name> -dir <dir_name>|
|--prefix(alias: -p)|selector에 지정 해준 접미사를 삽입|$ng new <project_name> -p <prefix_name>|
|--routing|Routing module을 자동 생성|$ng new <project_name>|
|--skip-git|git 의 초기화를  건너뜀|$ng new <project_name>|
|--skip-commit|git의 첫번째 커밋을 건너뜀|$ng new <project_name>|
|--skip-install|node_modules생성을 건너뜀 즉, npm install을 하지 않음|$ng new <project_name>|
|--skip-tests|spec file을 생성하지 않음|$ng new <project_name>|

#### ng serve
serve는 build와 webserver를 start 해주는 명령어

|옵션|기능|사용 예|
|---|---|---|
|--host( alias: -h )|기본 localhost:4200으로 실행|$ng serve --host|
|--live-reload ( alias: -lr )|수정시 페이지를 자동으로다시 로드 할 지 여부|$ng serve --live-reload|
|--open ( alias: -o )|웹서버를 가동 할 때 페이지를 오픈 해 준다.|$ng serve -o|
|--port ( alias: -p )|임의의 포트번호를 지정해 줄 수 있다.|$ng serve -p <port_number>|
|--ssl|HTTPS로 서버를 가동한다.|$ng serve --ssl|
|--watch ( alias: -w )|파일이 수정 되면 자동 빌드 한다.|$ng serve -w|
#### ng generate

generate는 컴포넌트, 서비스, 클래스, 디렉티브, 파이프, 모듈, 인터페이스 등을 자동으로 만들어 주는 명령어
generate는 기본적으로 다음과 같이 사용 할 수 있음
```shell
ng generate <generate_name> <name> [option]

- class - $ng generate class <name> 
- component - $ng generate component <name>
- directive - $ng generate directive <name>
- enum  - $ng generate enum  <name>
- guard - $ng generate guard <name>
- interface - $ng generate interface <name>
- module - $ng generate module  <name>
- pipe - $ng generate pipe <name>
- service - $ng generate service <name>

```


* 참고 - ng generate 대신 ng g로 대체해서 사용 가능


애플리케이션을 효율적으로 설계하고 구현하기 위해선 Angular의 기본 개념알아야 함

### 컴포넌트(Component)

컴포넌트는 애플리케이션을 구성하는 기본 단위
컴포넌트는 `@Component()` 데코레이터가 붙는 TypeScript 클래스, HTML 템플릿, 스타일로 구성됨
`@Component()` 데코레이터는 다음과 같이 Angular에 필요한 정보를 지정하는 역할을 함:

- 컴포넌트가 템플릿에 사용될 CSS 셀렉터를 지정함, 템플릿에서 이 셀렉터에 해당되는 HTML 엘리먼트마다 컴포넌트 인스턴스가 생성됨

- Angular가 컴포넌트 내용으로 렌더링할 HTML 템플릿을 지정함
    
- 템플릿 HTML 엘리먼트의 모습을 지정해야 한다면 이 때 필요한 CSS 스타일을 지정함
    

기본 내용만 담아 Angular 컴포넌트를 만들어보면 이렇게 구성할 수 있습니다.

```typescript
import { Component } from '@angular/core'; 

@Component({ 
	selector: 'hello-world', 
	template: ` 
		<h2>Hello World</h2> 
		<p>This is my first component!</p> ` 
}) 
export class HelloWorldComponent { 
	// 여기에는 컴포넌트의 동작을 정의하는 코드가 들어갑니다. 
}
```

이 컴포넌트를 사용하려면 템플릿에 아래 코드를 추가 해야함:
```html
<hello-world></hello-world>
```

Angular가 컴포넌트를 렌더링하고 나면 DOM이 아래와 같이 보임:

```html
<hello-world>
    <h2>Hello World</h2>
    <p>This is my first component!</p>
</hello-world>
```

Angular 컴포넌트는 강력하게 캡슐화되어 있지만 애플리케이션 구조에 맞게 직관적으로 구성
컴포넌트를 사용하면 애플리케이션에 유닛 테스트를 적용하기 쉽고, 코드의 가독성도 높일 수 있음

### 템플릿(Templates)[](https://angular.kr/guide/what-is-angular#%ED%85%9C%ED%94%8C%EB%A6%BFtemplates "Link to this heading")

컴포넌트는 이 컴포넌트가 어떻게 렌더링될지 정의하기 위해 HTML 템플릿이 존재함
템플릿은 인라인으로 정의하거나 별도 파일로 작성해서 불러올 수 있음

템플릿은 HTML 문법을 기본으로 작성하며 컴포넌트에 있는 값을 동적으로 반영하도록 구성
그래서 컴포넌트의 상태가 변경되면 Angular가 자동으로 렌더링된 DOM을 갱신됨 

#### Rendering Dynamic Data
아래 예제 코드는 문자열을 동적으로 렌더링하는 컴포넌트의 템플릿 코드임:

```html
<p>{{ message }}</p>
```

이 문자열은 컴포넌트 클래스에서 전달됨:

```typescript
import { Component } from '@angular/core';

@Component ({
  selector: 'hello-world-interpolation',
  templateUrl: './hello-world-interpolation.component.html'
})

export class HelloWorldInterpolationComponent {
    message = 'Hello, World!';
}
```

애플리케이션이 컴포넌트와 템플릿을 로드하고 나면 사용자가 아래와 같은 코드로 보임:

```html
<p>Hello, World!</p>
```


#### Dynamic Properties and Attributes

템플릿에 이중 중괄호(`{{`, `}}`)가 사용된 것은 템플릿에 문자열을 바인딩(interpolation)하는 문법

문자열 바인딩 외에도, Angular는 HTML 엘리먼트의 프로퍼티나 어트리뷰트에 값을 할당하는 프로퍼티 바인딩(property binding) 문법도 제공:

```html
<p
  [id]="sayHelloId"
  [style.color]="fontColor">
  You can set my color in the component!
</p>
```

대괄호(`[`, `]`)가 사용된 것을 확인해 보세요. 이 문법은 컴포넌트 클래스에 있는 값을 프로퍼티나 어트리뷰트로 바인딩하는 문법입니다.

#### Event Handling

키입력, 마우스 이동, 클릭, 터치 등과 같은 사용자의 동작을 감지하고 이 동작에 반응하기 위해 이벤트 리스터를 추가할 수도 있습니다. 감지하려는 이벤트 이름을 소괄호(`(`, `)`)로 감싸면 됩니다:

```html
<button
  type="button"
  [disabled]="canClick"
  (click)="sayMessage()">
  Trigger alert message
</button>
```
그리고 아래 코드는 이벤트가 발생했을 때 실행될 메서드를 컴포넌트 클래스에 구현한 코드입니다:

```typescript
sayMessage() {
    alert(this.message);
  }
```

Angular 템플릿에 문자열 바인딩과 프로퍼티 바인딩, 이벤트 바인딩이 어떻게 사용되는지 예제를 보면:
src/app/hello-world-bindings.component.ts
```typescript
import { Component } from '@angular/core';

@Component ({
  selector: 'hello-world-bindings',
  templateUrl: './hello-world-bindings.component.html'
})

export class HelloWorldBindingsComponent {
  fontColor = 'blue';
  sayHelloId = 1;
  canClick = false;
  message = 'Hello, World';
  
  sayMessage() {
    alert(this.message);
  }
}
```
src/app/hello-world-bindings.component.html
```html
<button
  type="button"
  [disabled]="canClick"
  (click)="sayMessage()">
  Trigger alert message
</button>

<p
  [id]="sayHelloId"
  [style.color]="fontColor">
  You can set my color in the component!
</p>

<p>My color is {{ fontColor }}</p>
```

## Directives

템플릿에 추가 기능을 구현하려면 [디렉티브(directives)](https://angular.kr/guide/built-in-directives)를 사용하면 됩니다. 
Angular 디렉티브 중에서 가장 많이 사용되는 디렉티브는 `*[ngIf]`와 `*[ngFor]`가 있습니다. 
렉티브를 활용하면 DOM 구조를 동적으로 변경할 수 있기 때문에 다양한 용도로 활용할 수 있습니다. 
사용자 경험을 더 좋게 만드는 용도로도 커스텀 디렉티브를 활용할 수 있습니다.

### Conditional rendering
아래 코드는 `*[ngIf]` 디렉티브를 사용하는 예제 코드입니다:

```ts
import { Component } from '@angular/core';
  
@Component({
  selector: 'hello-world-ngif',
  templateUrl: './hello-world-ngif.component.html'
})

export class HelloWorldNgIfComponent {
  message = "I'm read only!";
  canEdit = false;
  
  onEditClick() {
    this.canEdit = !this.canEdit;
    if (this.canEdit) {
      this.message = 'You can edit me!';
    } else {
      this.message = "I'm read only!";
    }
  }
}
```

```html
<h2>Hello World: ngIf!</h2>
  
<button type="button" (click)="onEditClick()">Make text editable!</button>
  
<div *ngIf="canEdit; else noEdit">
    <p>You can edit the following paragraph.</p>
</div>
  
<ng-template #noEdit>
    <p>The following paragraph is read only. Try clicking the button!</p>
</ng-template>
  
<p [contentEditable]="canEdit">{{ message }}</p>
```

JavaScript의 if 제어 블록과 유사하게 Angular는 표현식이 실제 값을 반환하는 경우 요소를 렌더링할지 여부를 제어하는 ​​내장 ngIf 지시문을 제공
```ts
<section class="admin-controls" *ngIf="hasAdminPrivileges">
  The content you are looking for is here.
</section>
```
hasAdminPrivileges가 true이면 애플리케이션은 사용자에게 콘텐츠를 표시하고, 그렇지 않으면 해당 요소가 DOM에서 완전히 제거됨


### Rendering a list
또 다른 일반적인 시나리오는 동적 데이터를 기반으로 항목 목록을 렌더링하는 것
JavaScript의 for 루프와 유사하게 Angular는 ngFor라는 또 다른 내장 지시문을 제공
다음 코드는 taskList의 각 항목에 대해 하나의 `<li>` 요소를 렌더링하는 것임:
```ts
<ul class="ingredient-list"> 
	<li *ngFor="let task of taskList">{{ task }}</li>
</ul>
```

Angular는 선언적인 템플릿 문법을 사용하기 때문에 화면에 표시되는 단위로 애플리케이션 로직을 깔끔하게 분리할 수 있음
템플릿에는 표준 HTML 문법을 활용하기 때문에 구성하기 쉽고, 관리하기도 쉬우며, 나중에 수정하기도 쉬움


### 의존성 주입(Dependency injection, DI)

- Angular는 TypeScript 클래스를 활용하는 의존성 주입 시스템을 제공하기 때문에, 컴포넌트에 필요한 객체의 인스턴스를 어떻게 생성하는지 직접 신경쓸 필요가 없음
- 인스턴스 생성은 Angular가 알아서 처리
- 이런 패턴 덕분에 애플리케이션 코드를 좀 더 유연하게 작성할 수 있으며, 테스트하기도 쉬움 
- Angular 애플리케이션을 개발할 때 의존성 주입 시스템을 반드시 알아야 하는 것은 아니지만 모범사례를 보면서 의존성 주입 시스템을 활용했을 때 얻는 장점에 대해 알아야함


- 의존성 주입 시스템이 동작하는 방식을 간단한 예제로 확인해보면, 첫 번째 파일 `logger.service.ts` 에는 `Logger` 클래스가 정의되어 있음
- 이 클래스에는 인자로 받은 숫자를 콘솔에 출력하는 `writeCount` 함수가 정의되어 있음

```ts
import { Injectable } from '@angular/core';

@Injectable({providedIn: 'root'})
export class Logger {
  writeCount(count: number) {
    console.warn(count);
  }
}
```


- 그리고 `hello-world-di.component.ts` 파일에는 Angular 컴포넌트가 정의되어 있음
- 이 컴포넌트에는 버튼이 하나 있는데, 이 버튼을 클릭하면 Logger 클래스에 있는 `writeCount` 함수를 실행하려고 한다면 `HelloWorldDI` 클래스 생성자에 `private logger: Logger`라는 코드를 추가해서 `Logger` 서비스가 의존성 객체로 주입되도록 요청할 수 있음

```ts
import { Component } from '@angular/core';
import { Logger } from '../logger.service';

@Component({
  selector: 'hello-world-di',
  templateUrl: './hello-world-di.component.html'
})
export class HelloWorldDependencyInjectionComponent  {
  count = 0;

  constructor(private logger: Logger) { }

  onLogMe() {
    this.logger.writeCount(this.count);
    this.count++;
  }
}
```

