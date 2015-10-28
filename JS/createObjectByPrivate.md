[객체 생성에서의 비공개 패턴] - 2015. 10. 28.
1. 정의
 JS는 본래 private가 없고 다 public으로 접근 가능하다.
 다만, JS의 클로져를 이용하여 접근권한을 제어할 수 있는데 이 패턴을 비공개 패턴이라 한다.

2. 사용례
 function Phone(){
 	var kind = 'iphone5s';
 	this.getPhone = function(){
 		return kind;
 	};
 }
 var myPhone = new Phone();
 myPhone.getPhone() // iphone5s
 myPhone.kind // 'undefined'

3. 주의할 점
 AS-IS.
 반환하는 비공개 변수가 객체나 배열인 경우 외부에서 수정이 가능 할 수 있다.

 function Dog(){
 	var dogInfo = {
 		age: 2,
 		color: "brown"
 	};
 	this.getDogInfo = function(){
 		return dogInfo;
 	};
 }
 var myDog = new Dog();
 var dogInfo = myDog.getDogInfo();
 dogInfo.age = 4;
 console.log(myDog.getDogInfo()); // Object {age: 4, color: "brown"}

 TO-BE.
 (객체를 복사하는 범용함수 등을 이용)비공개 변수의 복사본을 반환한다.

 function Dog(){
 	var dogInfo = {
 		age: 2,
 		color: "brown"
 	};
 	this.getDogInfo = function(){
 		return {
 			age: dogInfo.age,
 			color: dogInfo.color
 		};
 	};
 }

/*
 *
 * 참조: JavaScript Patterns, 인사이트, 115p~
 *
 */
