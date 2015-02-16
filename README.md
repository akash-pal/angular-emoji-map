# angular-emoji-map
Convert emoji "short codes" to their unicode counterpart:

`I :heart: the Indianapolis Colts. :smile:` 

becomes  

`I \u2764 the Indianapolis Colts. \ud83d\ude04`

## Getting Started
1. Install via [bower](http://bower.io/) `bower install angular-emoji-map --save`
2. Include `angular-emoji-map.js` in your HTML file after including Angular itself.
3. Add `mm.emoji.utils` to your main module's list.

## Example Usage:

In your `index.html`:

```html
<script src="bower_components/angular/angular.js"></script>
<script src="bower_components/angular-emoji-map/angular-emoji-map.js"></script>
```

In your `app.js`:

```js
angular.module('myApp', [
  // ...
  'mm.emoji.utils'
]);
```
### Getting an associative array of short codes
```javascript
module.controller('MyCtrl', ['emojiMap', function(emojiMap) {
  var heart = emojiMap[':heart:']; // heart is now \u2764
}]);

```
### Converting short codes into an emoji with [angular-twemoji](https://github.com/scheffield/angular-twemoji)
```html
<p data-ng-bind-html="message | emojiToUnicode | twemojoi"></p>
```

### Converting short codes within a controller
```javascript
module.controller('MyCtrl', ['emojiToUnicodeFilter', function(emojiToUnicodeFilter) {
  $scope.submit = function() {
    // subsititude emoji "short codes" with it's unicode string.
    $scope.text = emojiToUnicodeFilter($scope.text);
    // use twemoji to convert the message to html.
    var html = $window.twemoji.parse($scope.text);
}]);
```


