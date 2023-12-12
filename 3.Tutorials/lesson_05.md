
# Add an input parameter to the component



@Input() 컴포넌트를 생성하고, 데이터를 컴포넌트에 전달하여 커스터마이징하는 방법에 대해 알아보자


## Conceptual preview of Inputs

- Input 을 통해 컴포넌트가 데이터를 공유할 수 있음
- 데이터 공유의 방향은 parent component에서 child component로 이루어짐

- 부모 컴포넌트로부터 데이터를 받으려면 자식 컴포넌트가 클래스 프로퍼티를 `@Input()` 데코레이터로 표시해야 함
- 이 데코레이터는 컴포넌트와 지시어에서 사용할 수 있음

더 자세한 설명은 자식과 부모 지시어 및 컴포넌트 간 데이터 공유 가이드를 참조하세요.

이 단원에서는 `HousingLocationComponent`에서 `@Input()` 속성을 정의하여 컴포넌트에 표시되는 데이터를 사용자 정의하는 방법을 알아보자




### Step 1 - Import the Input decorator

`src/app/housing-location/housing-location.component.ts`

```ts
import { Component, Input } from '@angular/core';
import { CommonModule } from '@angular/common';
import { HousingLocation } from '../housinglocation';

```

### Step 2 - Add the Input property

동일한 파일에서 `HousingLocationComponent` 클래스에 `HousingLocation` 유형의 `housingLocation` 속성을 추가합니다. 
속성 이름 뒤에 ! 를 추가하고 `@Input()` 데코레이터를 접두사로 붙임:

Import `HousingLocationComponent` and Input in `src/app/housing-location/housing-location.component.ts`
```ts
export class HousingLocationComponent {
  @Input() housingLocation!: HousingLocation;
}
```

- 입력값이 전달될 것으로 예상되므로 !를 추가해야 함
- 이 경우 기본값(default value)은 없음
- 예제 애플리케이션에서는 값이 전달될 것이라는 것을 알고 있으며 이는 의도된 것입니다. 
- 느낌표는 non-null assertion operator라고 불리며 이 속성 값이 Null이 아니거나 정의되지 않았음을 타입스크립트 컴파일러에 알려줌