angular-selectize
==================
This is an Angular.js directive for Brian Reavis's selectize jQuery plugin (http://brianreavis.github.io/selectize.js/).

* Selectize is ~7kb (gzipped)
* Snappy performance even with 10k+ options (refer to demo)
* Smart Ranking / Multi-Property Searching & Sorting
* Angular models & bindings
* Skinnable
* Keyboard Compatible

###[Try the Demos on Plunker](http://plnkr.co/edit/X2YYPX?p=preview)

![selectize](https://cloud.githubusercontent.com/assets/4087667/5509244/dc6c4526-876a-11e4-8bf2-0edf33091147.png)




## Dependencies

- [AngularJS](http://angularjs.org/)
- [JQuery](http://jquery.com/)
- [Selectize](http://brianreavis.github.io/selectize.js/)

## Install

We use [bower](https://github.com/bower/bower) for dependency management. Install Angular-selectize into your project by running the command

`$ bower install angular-selectize2`

If you use a `bower.json` file in your project, you can have Bower save angular-selectize2 as a dependency by passing the `--save` or `--save-dev` flag with the above command.

This will copy the angular-selectize2 files into your `bower_components` folder, along with its dependencies. Load the script files in your application:
```html
<link rel="stylesheet" href="bower_components/selectize/dist/css/selectize.default.css ">
<script type="text/javascript" src="bower_components/jquery/jquery.js"></script>
<script type="text/javascript" src="bower_components/selectize/dist/js/standalone/selectize.min.js"></script>
<script type="text/javascript" src="bower_components/angular/angular.js"></script>
<script type="text/javascript" src="bower_components/angular-selectize2/dist/selectize.js"></script>
```

(Note that `jquery` must be loaded before `angular` so that it doesn't use `jqLite` internally)


Add the selectize module as a dependency to your application module:

```javascript
var myAppModule = angular.module('MyApp', ['selectize']);
```

##Please Note!
Add the directive to `<div>` elements. It will not work with `<select>` because of conflicts with ngOptions.

## Usage
Setup your controller variables:

```javascript
$scope.myModel = 1;

$scope.myOptions = [
  {id: 1, title: 'Spectrometer'},
  {id: 2, title: 'Star Chart'},
  {id: 3, title: 'Laser Pointer'}
];

$scope.config = {
  create: true,
  valueField: 'id',
  labelField: 'title',
  delimiter: '|',
  placeholder: 'Pick something'
  // maxItems: 1
}
```

Add the select element to your view template:

```html
<div selectize="config" options='myOptions' ng-model="myModel"></div>
```

##Config
Theoretically, all of the config options from the original selectize should work. But I have not been able to test them all.

- [Selectize config options](https://github.com/brianreavis/selectize.js/blob/master/docs/usage.md)
- [Selectize API](https://github.com/brianreavis/selectize.js/blob/master/docs/api.md)


### Inline Config

```html
<div selectize="{create:true, maxItems:10}" options='myOptions' ng-model="myModel"></div>
```

### Tag editor

```javascript
$scope.myModel = 1;

$scope.myOptions = [
  {value: 1, text: 'Spectrometer'},
  {value: 2, text: 'Star Chart'},
  {value: 3, text: 'Laser Pointer'}
];

$scope.config = {
  create: true
}
```

##Global Defaults
To define global defaults, you can configure the `selectize` injectable:

```javascript
MyApp.value('selectizeConfig', {
  delimiter: '|'
});
```
