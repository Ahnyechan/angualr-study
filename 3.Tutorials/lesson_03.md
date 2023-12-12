# Create the application’s HousingLocation component

앱에 새 컴포넌트가 추가:  `HousingLocationComponent`가 추가

```shell
ng generate component HousingLocation --standalone --inline-template --skip-tests
ng serve
```

이 단계에서는 앱의 홈 컴포넌트에 새 컴포넌트인 주택 위치 컴포넌트를 추가하여 앱의 레이아웃에 표시되도록 합니다.

Import HousingLocationComponent in src/app/home/home.component.ts
```ts
import { HousingLocationComponent } from '../housing-location/housing-location.component';
```

다음으로 배열에 `HousingLocationComponent`를 추가하여 `@Component` 메타데이터의 `imports` 속성을 업데이트함

Add `HousingLocationComponent` to imports array in `src/app/home/home.component.ts`
```ts
imports: [
  CommonModule,
  HousingLocationComponent
],
```

이제 컴포넌트를 `HomeComponent`의 템플릿에서 사용할 준비가 되었습니다. 템플릿 속성을 업데이트하여 `<app-housing-location>` 태그에 대한 참조를 포함하도록 `@component` 메타데이터의 `template` 속성을 업데이트함
```ts
template: `
  <section>
    <form>
      <input type="text" placeholder="Filter by city">
      <button class="primary" type="button">Search</button>
    </form>
  </section>
  <section class="results">
    <app-housing-location></app-housing-location>
  </section>
  `,
```


`src/app/housing-location/housing-location.css`를 열고 아래 스타일을 파일에 붙여넣습니다:
Add CSS styles to housing location to the component in `src/app/housing-location/housing-location.component.css`
```css
.listing {
  background: var(--accent-color);
  border-radius: 30px;
  padding-bottom: 30px;
}
.listing-heading {
  color: var(--primary-color);
  padding: 10px 20px 0 20px;
}
.listing-photo {
  height: 250px;
  width: 100%;
  object-fit: cover;
  border-radius: 30px 30px 0 0;
}
.listing-location {
  padding: 10px 20px 20px 20px;
}
.listing-location::before {
  content: url("/assets/location-pin.svg") / "";
}

section.listing a {
  padding-left: 20px;
  text-decoration: none;
  color: var(--primary-color);
}
section.listing a::after {
  content: "\203A";
  margin-left: 5px;
}
```


### 전체 코드:

`src/app/home/home.component.ts` :
```ts
import { Component } from '@angular/core';
import { CommonModule } from '@angular/common';
import { HousingLocationComponent } from '../housing-location/housing-location.component';
@Component({
  selector: 'app-home',
  standalone: true,
  imports: [
    CommonModule,
    HousingLocationComponent
  ],
  template: `
    <section>
      <form>
        <input type="text" placeholder="Filter by city">
        <button class="primary" type="button">Search</button>
      </form>
    </section>
    <section class="results">
      <app-housing-location></app-housing-location>
    </section>
    `,
  styleUrls: ['./home.component.css'],
})
  
export class HomeComponent {
  
}
```

`src/app/housing-location/housing-location.component.css` : 

```ts
import { Component } from '@angular/core';
import { CommonModule } from '@angular/common';
  
@Component({
  selector: 'app-housing-location',
  standalone: true,
  imports: [CommonModule],
  template: `
    <p>
      housing-location works!
    </p>
  `,
  styleUrls: ['./housing-location.component.css'],
})
  
export class HousingLocationComponent {
  
}
```