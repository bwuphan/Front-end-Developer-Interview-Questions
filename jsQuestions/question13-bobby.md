* Explain `Function.prototype.bind`

Bind creates a new function that will have this set to the first parameter passed to bind().

Here's an example that shows how to use bind to pass a member method around that has the correct this:


#### Example
```
var Button = function(content) {
  this.content = content;
};

Button.prototype.click = function() {
  console.log(this.content + ' clicked');
}

var myButton = new Button('OK');
myButton.click();

var looseClick = myButton.click;
looseClick(); // not bound, 'this' is not myButton - it is the global object

var boundClick = myButton.click.bind(myButton);
boundClick(); // bound, 'this' is myButton
```