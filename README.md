# Calling Returned Methods From An IIFE with Protected Methods
[See the original repo here](https://github.com/jdinitto/crmfaiife). 

I'm adding this particular repo as a compliment to the original, after a discussion with @pkrall520 about protecting the methods from being overwritten. Now the methods are properly scoped and privatized.

Below is the modified IIFE expression. Notice that what's returned is a new function object, with protected classes that reference the private `_self` methods. The returned methods can be overwritten, but `ding`'s classes are protected.

As with the original, the `this.ponk` class is the ideal way of returning a usable method, since it is available right at the `window.onload` event onward.

[View in action here](https://jdinitto.github.io/crmfaiifewpm/).

```
var ding = (function() {
    var tink = 5,
        _self = this;
        _self.woof = function() {
            return tink * 5;
        };
        _self.zonk = function(){
            six.innerHTML += ' ' + woof();
        };
        _self.mank = function(id){
            if(id){document.getElementById(id).innerHTML += ' ' + woof(); return false;}
            nine.innerHTML += ' ' + woof();
        };
        _self.ponk = function(butt){
            if (butt){return tink * 7}
            return tink * 6;
        };
    return new function() {
        this.woof = function() {_self.woof()};
        this.zonk = function() {_self.zonk()};
        this.mank = function(id) {_self.mank(id)};
        this.ponk = function(butt) {return _self.ponk(butt)};
    }
})();
```
