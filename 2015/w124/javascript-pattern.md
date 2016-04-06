## Javascript Pattern ##

記錄一些筆記，太簡單的 pattern 就不放了...

### Object literal ###

```
person = new Object();
person.property1 = "Hello";

person = {
  property1 : "Hello"
};
```

兩種寫法產生的結果是一樣，不過推薦使用第二種寫法，
好處是減少要打的字，而且要做的事情一目瞭然，
建立 Object & 賦予 Property 值

[http://stackoverflow.com/questions/4597926/what-is-the-difference-between-new-object-and-object-literal-notation](http://stackoverflow.com/questions/4597926/what-is-the-difference-between-new-object-and-object-literal-notation)

### Enforcing new ###

```
function Waffle() {
  this.tastes = "yummy";
}

var good_morning = Waffle();
console.log(typeof good_morning); // "undefined"
console.log(window.tastes); // "yummy"
```

```
function Waffle() {
  if (!(this instanceof Waffle)) {
    return new Waffle();
  }
  this.tastes = "yummy";
}
var good_morning = new Waffle();
var good_evening = Waffle();

console.log(typeof good_morning); // "object"
console.log(good_morning.tastes); // "yummy"
console.log(typeof good_evening); // "object"
console.log(good_evening.tastes); // "yummy"
```

沒有用 New 的話，Object 裡面的 this 可是會爆走的喔！
重要度真的五顆星！

### Regular Expression Literal ###

原來有這招！

```
// antipattern
var re = new RegExp("\\\\", "gm");

// preferred
var re = /\\/gm;
```
