FlexForms Modules for PHP
=========================

Official PHP modules for [FlexForms](https://github.com/cubiclesoft/php-flexforms).  Choose from a MIT or LGPL license.

Formerly called Admin Pack Modules.  The modules in this repository extend [FlexForms](https://github.com/cubiclesoft/php-flexforms) and also [Admin Pack](https://github.com/cubiclesoft/admin-pack).

Features
--------

* Officially supported modules for FlexForms.
* Modules have a liberal open source license.  MIT or LGPL, your choice.
* Designed for relatively painless integration into your project.
* Sits on GitHub for all of that pull request and issue tracker goodness to easily submit changes and ideas respectively.

Available Modules
-----------------

* Calendar - Adds a new field type (calendar) that replaces the input array with a set of standard FlexForms tables to display a calendar.
* Chart - Adds a new field type (chart) that displays a variety of [C3.js charts](http://c3js.org/).
* HTML Editor - Adds new options to the 'textarea' field type to convert a textarea into a TinyMCE HTML editor.  Filtering content submitted to the server for cross-site scripting (XSS) injection attempts is up to the developer, but using [TagFilter](https://github.com/cubiclesoft/ultimate-web-scraper) is highly recommended.
* Stop Password Manager - Adds a new option to the 'password' field type that can be used to stop password managers from attempting to store entered passwords.
* Table Filter - Adds new options to the 'table' field type to display a search field at the top of the table to quickly find matching rows more efficiently than built-in browser searching.
* Text Counter - Adds new options to the 'text' and 'textarea' field types to display a counter that shows the number of characters (or words) entered.

Usage
-----

Copy all the files for a specific module into the same directory that FlexForms resides in (e.g. `support/flex_forms.php`).  Then use `require_once` directives to include the required functionality after including FlexForms.  Modules register themselves automatically with the FlexForms class.

The following new field types are added:

* calendar (via Calendar) - Replaces the input with one or more standard FlexForms tables to display a calendar.
* chart (via Chart) - Displays [C3.js charts](http://c3js.org/).

New type-specific options for array fields:

* startyear (calendar) - An integer containing the starting year (inclusive) (Default is date("Y")).
* startmonth (calendar) - An integer containing the starting month (inclusive) (Default is date("m")).
* endyear (calendar) - An integer containing the ending year (inclusive) (Default is date("Y")).
* endmonth (calendar) - An integer containing the ending month (inclusive) (Default is date("m")).
* cols (calendar) - An array of strings containing the column text to use for each table header (Default is array("S", "M", "T", "W", "T", "F", "S")).
* data (calendar) - An array of key-value pairs that maps date strings in YYYY-MM-DD format to custom HTML for that date (Default is array()).
* monthcallback (calendar) - A valid callback function for a callback that will have an opportunity to alter the generated table field for a specific month.  The callback function must accept three parameters - callback(&$field, $curryear, $currmonth).
* daycallback (calendar) - A valid callback function for a callback that can alter the content output for a specific day of the month.  The callback function must return a string (e.g. `return $data;`) and accept four parameters - callback($curryear, $currmonth, $currday, $data).
* chart (chart) - A string containing one of "line", "spline", "step", "area", "area-spline", "area-step", "bar", "scatter", "pie", "donut", or "gauge".
* colors (chart) - An array of strings containing HTML hex color codes.  Mostly used for gauge charts.
* thresholds (chart) - An array of strings containing percentages that correlate to the "colors" option.  Mostly used for gauge charts.
* x (chart) - An array containing x-axis values for the data points (e.g. dates in YYYY-MM-DD format).
* data (chart) - An array containing key-value pairs where values are arrays of values.
* options (chart) - An array of options to pass to [C3.js](http://c3js.org/reference.html) (e.g. array("grid.x.show" => true, "zoom.enabled" => true)).
* callbacks (chart) - An array of Javascript callbacks to pass to [C3.js](http://c3js.org/reference.html).
* html (textarea + HTML editor) - A boolean indicating whether or not to turn the textarea into a HTML editor.
* html_options (textarea + HTML editor) - An array of options to pass to [TinyMCE](https://www.tinymce.com/docs/configure/integration-and-setup/).
* html_callbacks (textarea + HTML editor) - An array of Javascript callbacks to pass to [TinyMCE](https://www.tinymce.com/docs/configure/integration-and-setup/).
* passwordmanager (password + Stop Password Manager) - A boolean indicating whether or not to allow web browser password managers to work.
* filter (table + Table Filter) - A boolean indicating whether or not to enable the table filter module on the table.
* filter_options (table + Table Filter) - An array of options to pass to [FilterTable](https://github.com/sunnywalker/jQuery.FilterTable).
* filter_callbacks (table + Table Filter) - An array of Javascript callbacks to pass to [FilterTable](https://github.com/sunnywalker/jQuery.FilterTable).
* counter (text/textarea + Text Counter) - A boolean of true or an integer containing the limit on the number of characters to allow.
* counter_options (text/textarea + Text Counter) - An array of options to pass to [TextCounter](https://github.com/cubiclesoft/php-flexforms-modules/tree/master/text-counter/jquery.textcounter.js).
* counter_callbacks (text/textarea + Text Counter) - An array of Javascript callbacks to pass to [TextCounter](https://github.com/cubiclesoft/php-flexforms-modules/tree/master/text-counter/jquery.textcounter.js).

Example code for the various modules can be found in the Admin Pack [admin.php file](https://github.com/cubiclesoft/admin-pack/blob/master/admin.php).
