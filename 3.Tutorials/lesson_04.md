
# Creating an interface

이번 장에서는 인터페이스를 만들어 앱의 컴포넌트에 포함시키는 방법에 대해 설명


## Conceptual preview of interfaces

인터페이스는 앱에 대한 사용자 지정 데이터 유형입니다.

Angular는 타입스크립트를 사용하여 강력한 타입의 프로그래밍 환경에서 작업하는 이점을 활용합니다. 강력한 유형 검사는 앱의 한 요소가 다른 요소에 잘못된 형식의 데이터를 전송할 가능성을 줄여줍니다. 이러한 유형 불일치 오류는 TypeScript 컴파일러에 의해 포착되며, IDE에서도 이러한 오류가 다수 발견될 수 있습니다.

이 단원에서는 단일 주택 위치에 대한 데이터를 나타내는 속성을 정의하는 인터페이스를 만들어 보겠습니다.

### Step 1 - Create a new Angular interface

```bash
ng generate interface housinglocation
```

### Step 2 - Add properties to the new interface

`src/app/housinglocation.ts`
`housinglocation.ts`에서 기본 콘텐츠를 다음 코드로 바꾸어 이 예제와 일치하는 새 인터페이스를 만듭니다.

```ts
export interface HousingLocation {
  id: number;
  name: string;
  city: string;
  state: string;
  photo: string;
  availableUnits: number;
  wifi: boolean;
  laundry: boolean;
}
```

  
이 시점에서 ID, 이름, 위치 정보 등 숙소 위치에 대한 데이터를 나타내는 인터페이스를 정의함

### Step 3 - Create a test house for your app

인터페이스가 있지만 아직 사용하지 않고 있음

이 단계에서는 인터페이스의 인스턴스를 만들고 몇 가지 샘플 데이터를 할당함
이 샘플 데이터는 아직 앱에 표시되지 않아 그 전에 완료해야 할 몇 가지 step이 더 있음

`src/app/home/home.component.ts`.


Import `HomeComponent` in `src/app/home/home.component.ts`
```ts
import { HousingLocation } from '../housinglocation';
```


`src/app/home/home.component.ts`에서 빈 `export class HomeComponent {}` 정의를 이 코드로 대체하여 컴포넌트에 새 인터페이스의 단일 인스턴스를 생성함
Add sample data to `src/app/home/home.component.ts` :
```ts
export class HomeComponent {
  housingLocation: HousingLocation = {
    id: 9999,
    name: 'Test Home',
    city: 'Test city',
    state: 'ST',
    photo: 'assets/example-house.jpg',
    availableUnits: 99,
    wifi: true,
    laundry: false,
  };
}
```

이 예제처럼 `home.component.ts` 파일이 일치하는지 확인합니다.

`src/app/home/home.component.ts` : 
```ts
import { Component } from '@angular/core';
import { CommonModule } from '@angular/common';
import { HousingLocationComponent } from '../housing-location/housing-location.component';
import { HousingLocation } from '../housinglocation';

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
  housingLocation: HousingLocation = {
    id: 9999,
    name: 'Test Home',
    city: 'Test city',
    state: 'ST',
    photo: 'assets/example-house.jpg',
    availableUnits: 99,
    wifi: true,
    laundry: false,
  };
}
```

`HomeComponent` 클래스에 `HousingLocation`유형의 `housingLocation` 속성을 추가하면 데이터가 인터페이스의 설명과 일치하는지 확인할 수 있음
데이터가 유용한 오류를 제공하기에 충분한 정보를 가지고 있는지 여부에 대한 설명을 충족하지 못하는 경우.

변경 사항을 저장하고 앱에 오류가 없는지 확인하고 브라우저를 열고 애플리케이션에 "housing-location works!"라는 메시지가 계속 표시되는지 확인