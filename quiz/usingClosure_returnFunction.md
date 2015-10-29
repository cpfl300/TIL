문제풀이 - 2015. 10. 29.
1. 문제
 You are writing a function that takes two sets of arguments of arbitrary length. The return value will be the sum of the values of all of the arguments.

 The function should contain at least 1 argument per set.

	``` 
		example)
		calculate(1)(1) // should return 2
		calculate(1,1)(1) // should return 3
		calculate(1,1)(1,-1) // should return 2
		calculate(2,4)(3,7,1) // should return 17
	```

2. 나의 풀이
 function calculate() {
  var arg = Array.prototype.slice.call(arguments);
  var prevTotal = 0;
  arg.forEach(function(el){
    prevTotal += el;
  });
  return function(){
    var arg = Array.prototype.slice.call(arguments);
    var total = 0;
    arg.forEach(function(el){
      total += el;
    });
    return prevTotal + total;
  }
}

3. best practices
	거의 위와 비슷한 경우가 많았으나 reduce를 사용했으면 조금 더 깔끔하게 해결 할 수 있었을 것이다. 
	내 풀이에서는 prevTotal, total이라는 두 변수를 사용하였는데, 변수명은 차치하고, 결과적으로 두 변수의 합을 던져주는 만큼 변수를 하나로 사용하는 것도 고려할만 해 보인다.
	
/*
 *
 * 참조: http://www.codewars.com/kata/javascript-mathematician/solutions/javascript
 *
 */
