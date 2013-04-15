# Chardin.js

**Simple overlay instructions for your apps.**

[Check out a demo](http://heelhook.github.com/chardin.js/).

Chardin.js is a jQuery plugin that creates a simple overlay to display instructions on existent elements. It is inspired by
the recent Gmail new composer tour which I loved.

![chardin](https://raw.github.com/heelhook/chardin.js/master/example/img/chardin.png "chardin")  
[Jean-Baptiste-Siméon Chardin](http://en.wikipedia.org/wiki/Jean-Baptiste-Sim%C3%A9on_Chardin)

## Installing

Simple! Fork this repo or download [chardinjs.css][0] and [chardinjs.min.js][1] and add the following assets to your HTML:

```HTML
<link href="chardinjs.css" rel="stylesheet">
<script src="chardinjs.min.js"></script>
```

### Installing in the rails asset pipeline (optional) 

There's a [`chardinjs-rails`](https://github.com/heelhook/chardin.js-rails) gem.

### Building (optional)

If you choose to fork the repo you can build the assets running

    rake compile


## Adding data for the instructions

Add the instructions to your elements:

`data-intro`: Text to show with the instructions  
`data-position`: (`left`, `top`, `right`, `bottom`), where to place the text with respect to the element

```HTML
<img src="img/chardin.png" data-intro="An awesome 18th-century painter, who found beauty in everyday, common things." data-position="right" />
```

## Running (single step only)

Once you have your elements ready you can show instructions running

```Javascript
$('body').chardinJs('start')
```

If you would rather run ChardinJs confined to a particular container (instead of using the whole document) you can
change `body` to some other selector.

```Javascript
$('.container').chardinJs('start')
```

## Running (multiple step tutorial)

The set up for running a multiple step tutorial is slightly different. Firstly, you have to define all the steps in the following manner

```Javascript
tutorialSteps = {
  'selector1': {
    next: 'selector2',
    intro: 'Some text here',
    position: 'right'
  },
  'selector2': {
    next: '',
    redirect: '/to_some_url',
    intro: 'Some text here',
    position: 'right'
  }
}
```

Where 'selector1' represents a selector of one step in the tutorial.

Then to start the tutorial, call the following

```Javascript
$('.container').chardinJs('start', tutorialSteps, 'selector1')
```

The 3rd argument ('selector1') should be the step that you want to start the tutorial at. Starting the tutorial will run through the steps (starting from the step in the 3rd argument) till the last step.

Do not insert the data-intro and data-position attributes into the DOM. The script will handle the insertion and removal automatically. 

## Methods

### .chardinJs('start')

Start ChardinJs in the selector.

### .chardinJs('toggle')

Toggle ChardinJs.

### .chardinJs('stop')

Make your best guess. That's right! Stops ChardinJs in the selector.

## Events

### 'chardinJs:start'

Triggered when chardinJs is correctly started.

### 'chardinJs:stop'

Triggered when chardinJs is stopped.

## Author

[Pablo Fernandez][2]

### Contributors

 * [John Weir](https://github.com/jweir)
 * [felipeclopes](https://github.com/felipeclopes)
 * [Bobby Jack](https://github.com/fiveminuteargument)
 * [Maxim Syabro](https://github.com/syabro)
 * [nmeum](https://github.com/nmeum)
 * [Jakob Miland](https://github.com/saebekassebil)
 * [printercu](https://github.com/printercu)

## Contributions

If you want to contribute, please:

  * Fork the project.
  * Make your feature addition or bug fix.
  * Add yourself to the list of contributors in the README.md.
  * Send me a pull request on Github.

## License

Copyright 2013 Pablo Fernandez

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.

 [0]: https://github.com/heelhook/chardin.js/blob/master/chardinjs.css
 [1]: https://github.com/heelhook/chardin.js/blob/master/chardinjs.min.js
 [2]: https://github.com/heelhook
