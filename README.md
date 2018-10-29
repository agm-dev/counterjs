# Counter.js

Counter.js is a simple plain javascript library to be used in the browser.

## Usage

As simle as this:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <!-- head stuff -->
</head>
<body>
  <!-- content -->

  <script type="text/javascript" src="path/to/counter.js"></script>

  <script>

    counter.init({
      target: '2122-01-01 00:00:00',
      days: 'counter__days',
      hours: 'counter__hours',
      minutes: 'counter__minutes',
      seconds: 'counter__seconds',
      targetText: 'counter__target',
      intl: 'en-US',
    })

    window.addEventListener('counter-update', function () {
      console.log('update!')
    })

  </script>
</body>
</html>
```

## Methods

The code is inside a closure and exposes the next interface:

| Method | Description |
|-|-|
| init | Initializes the counter with options object |
| calculate | Returns an object with calculations |
| print | Logs a time string with the calculations |
| destroy | Removes the interval that updates the counter every second |

### init(options)

This method requires an object with the next properties:

| Property | Description |
|-|-|
| target | The time string in the past or the future |
| days | The class name of the HTML element where we want the calculated days to be printed in |
| hours | The class name of the HTML element where we want the calculated hours to be printed in |
| minutes | The class name of the HTML element where we want the calculated minutes to be printed in |
| seconds | The class name of the HTML element where we want the calculated seconds to be printed in |
| targetText | The class name of the HTML element where we want the target time string to be printed in |
| intl | 'locales' param of [Intl.NumberFormat](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Objetos_globales/NumberFormat). Just used to print day values over or equal to 1000 units |

## Events

The code sets an interval each second and updates the calculations. On update, it emits a `counter-update` on `window` object. You can listen to that event with:

```javascript
window.addEventListener('counter-update', () => console.log('updated!'))
```
