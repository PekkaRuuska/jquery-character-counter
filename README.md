# jquery-character-counter

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.1202437.svg)](https://doi.org/10.5281/zenodo.1202437)

A simple character counter.
Works with inputfields and textareas as well as DOM-elements that work with contenteditable attribute.

- Author: Pekka Ruuska
- License: MIT


### Features

 - Support for textarea
 - Support for input fields
 - Support for DOM elements that support *contenteditable*-attribute
 - Custom minimum and maximum length for character string
 - Customizable counter indicator text and location
 - Prevent text input after string has reached its maximum desired length
 - Callback functions for when string length goes over limit values
 - Updates on *input* and *propertychange* events


### Compatibility

- jQuery 1.7.0 and up
- IE8 and up (might work on previous versions too)


### Getting started

```html
<script src="//ajax.googleapis.com/ajax/libs/jquery/1.7.0/jquery.min.js"></script>	
<script type="text/javascript" src="jquery.character-counter.js"></script>
```


### Usage

Basic initialization:

```javascript
$('element').characterCounter();
```


Or purely with data-attributes:

```html
<textarea id="elementId" data-charcounter-enable="true"></textarea>
```


You can even combine the two methods:
```html
<textarea id="elementId" data-charcounter-minlength="2" data-charcounter-maxlength="10"></textarea>

<script type="text/javascript">
$('#elementId').characterCounter({
    blockextra: true
});
</script>
```


### Options

Same settings can be given by data atributes or option-parameters.

```javascript
{
minlength: 0,
maxlength: 160,
blockextra: false,
position: 'bottom',
counterclass: 'character-counter-indicator',
alertclass: 'out-of-range',
textformat: '[used]/[max]',
onOutOfRange: function(count, min, max){},
onBackToRange: function (count, min, max){}
}
```


Data-atributes override options-parameters.

```html
<textarea id="textareaExample"
data-charcounter-enable="true"
data-charcounter-minlength="0"
data-charcounter-maxlength="160"
data-charcounter-blockextra="false"
data-charcounter-position="bottom"
data-charcounter-counterclass="character-counter-indicator"
data-charcounter-alertclass="out-of-range"
data-charcounter-textformat="[used]/[max]">
</textarea>
```


| Option| Type | Value alternatives | Description |
| ------ | ------ | ------ |------ |
| enable | boolean |  | Enables character counter to element without javascript initialization. Only works with data-attributes. |
| minlength | int |  | Minimum number of characters. Most useful when used with alertclass value You can always have 0 characters no matter || what the minlength value is. 0 = no minimum. |
| maxlength | int |  | Maximum number of characters. 0 = no maximum. |
| blockextra | boolean  |  | Blocks characters that go over the maxlength value. |
| position | string |  | Create the counter to desired position or insert to element. |
|  |  | 'top' | Creates the counter element on top of the field. |
|  |  | 'bottom' | Creates the counter element on betow of the field. |
|  |  | '#elementId' | Creates the counter element in another, specified, element. |
| counterclass | string |  | Adds class defined to the counter element. |
| alertclass |  string |  | Adds class defined to the counter element when over maxlength value or under minlength value. |
| textformat | string |  | Format of the counter's text. |
|  |  | '[used]' | The number of characters used. |
|  |  | '[under]' | The number of characters the current count id below the minlength value. (minlength - count) |
|  |  | '[over]' | The number of characters the current count id above the maxlength value. (count - maxlength) |
|  |  | '[left]' | The number of characters left to the maxlength value. (maxlength - count) |
|  |  | '[min]' | The minlength value. |
|  |  | '[max]' | The maxlength value. |
| onOutOfRange | function |  | Function that is called when the character count goes above maxlength value or below minlength value. Only works with option parameters. |
| onBackToRange | function |  | Function that is called when the character count returns to the desired range. |
