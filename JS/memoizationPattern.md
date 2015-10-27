[메모이제이션(Memoization) pattern] - 2015. 10. 27.
1. 정의
 한번 호출한 값에 대해 캐시를 사용하여 호출비용을 절감시킬 수 있다.

2. 사용례

var myFunc = function(){
	var cachekey = JSON.stringify(Array.prototype.slice.call(arguments)),
		result;

	if(!myFunc.cache[cachekey]){
		result = {}
		```
			연산수행
		```
		myFunc.cache[cachekey] = result;
	}
	return myFunc.cache[cachekey];

}
myFunc.cache = {};

/*
 *
 * 참조: JavaScript Patterns, 인사이트, 93p
 *
 */
