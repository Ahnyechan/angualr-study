# Create Home component

- Angular 앱은 Angular의 빌딩 블록인 컴포넌트를 중심으로 구축
- 컴포넌트에는 앱에서 요소의 기능과 모양을 제공하는 코드, HTML 레이아웃 및 CSS 스타일 정보가 포함되어 있음
- Angular에서 컴포넌트는 다른 컴포넌트를 포함할 수 있음
- 앱의 기능과 모양을 컴포넌트로 나누고 분할할 수 있음

- lesson_01에서는 다른 모든 컴포넌트를 포함하는 기능을 하는 앱 컴포넌트를 업데이트함
- 이번 lesson에서 앱의 홈 페이지를 표시하는 `HomeComponent`를 만든 후 앱에 더 많은 기능을 제공하기 위해 더 많은 컴포넌트를 만들도록 함

![[Pasted image 20231211105524.png]]

Angular에서 컴포넌트에는 그 속성을 정의하는 메타데이터가 있음

home.component를 만들 때 이러한 속성을 사용:

	- selector: 템플릿에서 Angular가 컴포넌트를 참조하는 방법을 설명
	- standalone: 컴포넌트에 ngModule이 필요한지 여부를 설명  
	- import: 컴포넌트의 종속성을 설명
	- template: 컴포넌트의 HTML 마크업과 레이아웃을 설명
	- styleUrls: 컴포넌트가 사용하는 CSS 파일의 URL을 배열로 나열


###   Step 2 - Add the new component to your app's layout

새로운 컴포넌트를 만들어보면, `HomeComponent` app의 root component `AppComponent`에 만들면되고 앱의 레이아웃이 표시되도록 해보자

In the **Edit** pane of your IDE:

1. Open `app.component.ts` in the editor.
    
2. In `app.component.ts`, import `HomeComponent` by adding this line to the file level imports.
`src/app/app.component.ts`
```ts
import { HomeComponent } from './home/home.component';
```
3. In `app.component.ts`, in `@Component`, update the `imports` array property and add `HomeComponent`.

Replace in src/app/app.component.ts
```ts
@Component({
  imports: [
    HomeComponent,
  ],
 })
```

4. In `app.component.ts`, in `@Component`, update the `template` property to include the following HTML code.

Replace in src/app/app.component.ts
```ts
import { Component } from '@angular/core';
import { CommonModule } from '@angular/common';
  
@Component({
  selector: 'app-home',
  standalone: true,
  imports: [
    CommonModule,
  ],
  template: `
    <section>
      <form>
        <input type="text" placeholder="Filter by city">
        <button class="primary" type="button">Search</button>
      </form>
    </section>
  `,
  styleUrls: ['./home.component.css'],
})
  
export class HomeComponent {
  
}
```

5. Save your changes to `app.component.ts`.
    
6. If `ng serve` is running, the app should update. If `ng serve` is not running, start it again. _Hello world_ in your app should change to _home works!_ from the `HomeComponent`.
    
7. Check the running app in the browser and confirm that the app has been updated.
![[Pasted image 20231211152223.png]]
### Step 3 - Add features to `HomeComponent`

이 단계에서는 홈 컴포넌트에 기능을 추가합니다.

이전 단계에서는 앱의 템플릿에 기본 홈 컴포넌트를 추가하여 앱에 기본 HTML이 표시되도록 함

이 단계에서는 이후 단원에서 사용할 검색 필터와 버튼을 추가
지금은 홈 컴포넌트에 이것이 전부임므로 이 단계에서는 아직 어떤 기능도 없이 레이아웃에 검색 요소만 추가함

1. In the `first-app` directory, open `home.component.ts` in the editor.
    
2. In `home.component.ts`, in `@Component`, update the `template` property with this code.

Replace in `src/app/home/home.component.ts`
```ts
template: `
  <section>
    <form>
      <input type="text" placeholder="Filter by city">
      <button class="primary" type="button">Search</button>
    </form>
  </section>
`,
```

3. Next, open `home.component.css` in the editor and update the content with these styles.

Replace in `src/app/home/home.component.css`
```ts
.results {
  display: grid;
  column-gap: 14px;
  row-gap: 14px;
  grid-template-columns: repeat(auto-fill, minmax(400px, 400px));
  margin-top: 50px;
  justify-content: space-around;
}

input[type="text"] {
  border: solid 1px var(--primary-color);
  padding: 10px;
  border-radius: 8px;
  margin-right: 4px;
  display: inline-block;
  width: 30%;
}

button {
  padding: 10px;
  border: solid 1px var(--primary-color);
  background: var(--primary-color);
  color: white;
  border-radius: 8px;
}

@media (min-width: 500px) and (max-width: 768px) {
  .results {
      grid-template-columns: repeat(2, 1fr);
  }
  input[type="text"] {
      width: 70%;
  }   
}

@media (max-width: 499px) {
  .results {
      grid-template-columns: 1fr;
  }    
}
```

4. 앱이 오류 없이 빌드되는지 확인

![[Pasted image 20231211152207.png]]

