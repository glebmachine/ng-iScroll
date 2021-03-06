ng-iScroller v1.3
============

AngularJS Module that enables iScroll 5.x to work using a directive

Demos
------------

See demo/ Directory
Note: Recommended to be used with iOS or Android devices only


Dependencies
------------
- [AngularJS 1.2+](http://angularjs.org/) (Tested with AngularJs 1.3 & 1.4)
- [iScroll 5.1.x](https://github.com/cubiq/iscroll)

Installation
------------
 - **Bower**:
 Install the package by adding `ng-iScroll` to your `bower.json` file.

Reporting Issues
-------------
- Issues can be reported at the Github project.

Features
-------------

* Option to set time delay on binding of iScroll to dom
* Support for multiple iScrolls per page
	* See demo/demo_multiple_iscrolls.htm for how to use multiple iScroll divs on the same page
* Support for setting iScroll specific options via App Controller
	* See demo/app.js or demo/app_multi.js for how
* Support for iScroll 'refresh' and other functions via App Controller
* iScroll Options can be set via App Controller


Usage
---------

* Include ng-iscroll.js or ng-iscroll.min.js in your html header or existing file before your application main js file
* Add 'ng-iscroll' to your Angular app's dependencies
 * Example ```var App = angular.module('App', ['ng-iscroll']);```

* Add directive `ng-iscroll` to the ```<div id="wrapper">```
 * Example: ```<div id="wrapper" ng-iscroll>```


Options
-------------
#### HTML Directive Settings

**Binding Delay**:
If you want to delay the iScroll binding due to having animations or using another JS Library to modify the Angular view you can add a timeout value by using the attribute ```ng-iscroll-delay='{delayInMiliseconds}'```.  The default delay is 5ms.

**Forms**:
Forms within an iScroll has certain issues with editing Text values or Select boxes.  To enable support for forms add the following option to the wrapper div: ```ng-iscroll-form='true'``` the default is set to 'false'

**Naming of Instance**:
When multiple iScrolls are present on a single page and each needs different runtime settings or functions there is a need to identify each instance.  This is done either by setting the 'ng-iscroll="{instanceName}"' or if not set it will default to the id of the div.

*Note:* This breaks version 1.0's usage of the ng-iscroll value to define the delay in dom binding.  Please update your code to use ng-iscroll-delay to change the default delay.

See demos/ directory for examples of both


#### Angular Controller Settings

iScroll exposes both runtime and other functions that can change the appearance or behavior of the iScroll.  These can be set via the AppController to further configure iScroll.

Example:

HTML:
```
<div id="wrapper" ng-iscroll='wrapper' ng-iscroll-delay='50'>
	<button ng-click="refreshiScroll()">Refresh</button>
</div>
```

AppController:
```
$scope.$parent.myScrollOptions = {
	'wrapper': {
		snap: false,
		onScrollEnd: function ()
		{
			alert('finshed scrolling wrapper');
	}},
};

$scope.refreshiScroll = function ()
{
	$scope.$parent.myScroll['wrapper'].refresh();
	alert('wrapper refreshed');
};
```

The default settings for ng-iScroll are the following:
- snap: true
- momentum: true
- hScrollbar: false
- mouseWheel: true

The above can be overridden using the $scope.$parent.myScrollOptions option in your Controller.

For more examples see the demo directory.


License
--------------

ng-IScroll is released under the [MIT License](http://opensource.org/licenses/MIT).


Special Thanks
---------------

Thanks to the following help for submitting bugs and suggesting new features:

[Rodrigo Mesquita de Abreu](https://github.com/rodmabreu)

[Robert](https://github.com/rtpm)

[Andre Meyering](https://github.com/archer96)

[Brandon Benson](https://github.com/bensane)
