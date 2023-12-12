
# Hello world

### Step 1 - Test the default app

```shell
npm install -g @angular/cli
ng new first-app
ng serve
```


### Step 2 - Review the files in the project

이 단계에서는 기본 Angular 앱을 구성하는 파일에 대해 알아보자

IDE의 탐색기 창에서:

1. 프로젝트 디렉토리에서 첫 번째 앱 디렉토리로 이동합니다.

![img](/assets/Pasted_image_20231211105722.png)

2. src 디렉터리를 열어 파일을 확인

	a. 파일 탐색기에서 Angular 앱 파일(/src)을 찾습니다.

		- index.html은 앱의 최상위 HTML 템플릿
		- style.css는 앱의 최상위 스타일 시트
		- main.ts는 앱 실행이 시작되는 곳
		- favicon.ico는 웹 사이트에서 볼 수 있는 앱의 아이콘

	b. 파일 탐색기에서 Angular 앱의 컴포넌트 파일(/app)

		- app.component.ts는 앱 루트 컴포넌트를 설명하는 소스 파일
		- 앱의 최상위 Angular 컴포넌트 
		- 컴포넌트는 Angular 애플리케이션의 기본 빌딩 블록
		- 컴포넌트 설명에는 컴포넌트의 코드, HTML 템플릿 및 스타일이 포함되며, 이 파일 또는 별도의 파일에 설명할 수 있음
		- 이 앱에서는 컴포넌트의 코드와 HTML 템플릿이 이 파일에 있는 반면 스타일은 별도의 파일로 구성
		- app.component.css는 이 컴포넌트의 스타일 시트임
		- 새 컴포넌트는 이 디렉터리에 추가해야함

	c. 파일 탐색기에서 앱에서 사용하는 이미지가 포함된 이미지 디렉토리(/assets)

	d. 파일 탐색기에서 일반적인 상호 작용하는 파일이 아닌 파일들:

		- .angular에는 Angular 앱을 빌드하는 데 필요한 파일이 있음
		- .e2e에는 앱 테스트에 사용되는 파일이 있음
		- .node_modules에는 앱에서 사용하는 node.js 패키지가 있음
		- angular.json은 앱 빌드 도구에 대한 Angular 앱을 설명함
		- package.json은 완성된 앱을 실행하기 위해 npm(노드 패키지 관리자)에서 사용함
		- tsconfig.*는 TypeScript 컴파일러에 앱의 구성을 설명하는 파일

src/index.html
```html
<title>Homes</title>
```

first-app/src/app/app.component.ts
```ts
import { Component } from '@angular/core';

@Component({
  selector: 'app-root',
  standalone: true,
  imports: [],
  template: `<h1>Hello world!</h1>`,        // <- 
  styleUrls: ['./app.component.css'],
})

export class AppComponent {
  title = 'homes';
}
```

