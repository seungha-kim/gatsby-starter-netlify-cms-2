# 객체 (Object)

객체는 이름 값 쌍 을 담을수있는 통이다. 

통안에 이름 값 쌍 을 객체의 속성(property)이라고한다.

```
const name = '윤아준'

const person = {
  name, // `name: name`과 똑같이 동작합니다.
  age: 19,
  // ...
};
```



## 점 표기법

```
const person = {}; // 빈 객체

// 점 표기법 (Dot notation)
person.name = '윤아준';
person.age = 19;
person.languages = ['Korean', 'English'];
```

빈객체를 생성한뒤 점표기법을 통해 속성을 갱신해줄수있다.

## 대괄호 표기법

식별자로 허용되지 않는 문자가 들어간 속성이름은 반드시 대괄호 표기법을 사용해야 한다.

```
// 대괄호 표기법 (Bracket notation)
person['한국 나이'] = 20;
```

## 객체 다루기

```
const person = {
  name: '윤아준',
  age: 19,
  languages: ['Korean', 'English']
};


// 속성 읽기
person.name; // '윤아준'
person.age; // 19
persion.languages[0] // 'Korean'
객체의 이름뒤에 . key값을 부르면 그객체에들어있는 value 값을 알수있다.

// 속성 쓰기
person.name = '신하경';
person.age = 20;
객체의 이름뒤에 .key 값에 새로운 value값을 넣을수도 있다.

// 새 속성 추가하기
person.address = '서울특별시 강남구 신사동';
새로운 key 값을 추가할수도 있다.

// 속성 삭제하기
delete person.address;
객체안에 key값을 삭제할수도있다.

// 속성이 객체에 존재하는지 확인하기
'name' in person; // true
'phoneNumber' in person; // false
```

## 메소드

메소드는 객체의 속성값으로 사용하는 함수를 메소드라고한다.

## this

this 키워드를 사용하면 메소드 호출시에 해당 메소드를 갖고있는 객체에 접근할수있다.

```
const person = {
  name: '윤아준',
  age: 19,
  introduce() {
    // `this`를 사용해서 객체의 속성에 접근함
    return `안녕하세요, 제 이름은 ${this.name}입니다. 제 나이는 ${this.age}살 입니다.`
  },
  getOlder() {
    // `this`를 사용해서 객체의 속성을 갱신함
    this.age++;
  }
};
person.introduce(); // '안녕하세요, 제 이름은 윤아준입니다. 제 나이는 19살 입니다.'
person.getOlder(); // undefined
person.introduce(); // '안녕하세요, 제 이름은 윤아준입니다. 제 나이는 20살 입니다.'
```

함수가 객체 내부의 정의 되어있어도 실행이되고

함수가 객체 외부의 있어도 메소드는 사용된다.

```
function introduce() {
  return `안녕하세요, 제 이름은 ${this.name}입니다.`;
}

const person1 = {
  name: '윤아준',
  introduce
};
person1.introduce(); // 안녕하세요, 제 이름은 운아준입니다.
```

다만 화살표함수는 this 키워드를 전혀 다르게 취급하기 때문에 위와같은 방식으로는 사용될수없다.

## 프로토타입

모르겟다....

## 생성자

new 키워드와 함께 사용하는 함수를 생성자 라고부른다.

생성자의 이름으로는 식별자로 사용될수있는것이면 뭐든지 사용가능하지만 변수와는 다르게 대문자로 시작하여야 한다.

### 인스턴스

생성자를 통해 생성된 객체를 그생성자에 인스턴스라고한다.

instanceof 연산자를 사용하여 객체가 특정 생성자의 인스턴스가 맞는지 확인할수있다.

## 정적 메소드

JavaScript의 함수는 객체이기도 하다는 사실을 앞에서 언급했습니다. 생성자의 속성에 직접 지정된 메소드를 가지고 정적 메소드(static method)라고 합니다. 우리가 이제까지 유용하게 사용했던 `Number.isNaN`, `Object.getPropertyOf` 등의 함수들은 모두 정적 메소드입니다. 정적 메소드는 특정 인스턴스에 대한 작업이 아니라, 해당 생성자와 관련된 일반적인 작업을 정의하고 싶을 때 사용됩니다.