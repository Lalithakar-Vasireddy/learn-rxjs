# expand
###signature: `expand(project: function, concurrent: number, scheduler: Scheduler): Observable`
*The gist: Recursively call provided function...*

([jsBin](http://jsbin.com/fuxocepazi/1/edit?js,console) | [jsFiddle](https://jsfiddle.net/qg6qfqLz/34/) | [official docs](http://reactivex.io/rxjs/class/es6/Observable.js~Observable.html#instance-method-expand))
```js
//emit 2
const source = Rx.Observable.of(2);
const example = source
  //recursively call supplied function
  .expand(val => {
       //2,3,4,5,6
       console.log(`Passed value: ${val}`);
       //3,4,5,6
       return Rx.Observable.of(1 + val);
    })
  //call 5 times
  .take(5);
/*
	"RESULT: 2"
	"Passed value: 2"
	"RESULT: 3"
	"Passed value: 3"
	"RESULT: 4"
	"Passed value: 4"
	"RESULT: 5"
	"Passed value: 5"
	"RESULT: 6"
	"Passed value: 6"
*/
//output: 2,3,4,5,6
const subscribe = example.subscribe(val => console.log(`RESULT: ${val}`));
```