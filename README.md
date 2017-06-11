# webpagetest

[![Build Status](https://travis-ci.org/WidgetsBurritos/webpagetest.svg?branch=master)](https://travis-ci.org/WidgetsBurritos/webpagetest) [![Latest Stable Version](https://poser.pugx.org/WidgetsBurritos/webpagetest/version)](https://packagist.org/packages/widgetsburritos/webpagetest) [![License](https://poser.pugx.org/widgetsburritos/webpagetest/license)](https://packagist.org/packages/widgetsburritos/webpagetest) [![composer.lock](https://poser.pugx.org/widgetsburritos/webpagetest/composerlock)](https://packagist.org/packages/widgetsburritos/webpagetest)

A php library for interacting with webpagetest.org.

*Requires PHP 5.5+*

## Usage

### Instantiating a new instance
```php
<?php

use WidgetsBurritos\WebPageTest\WebPageTest;

$wpt = new WebPageTest('YOUR_API_KEY');
```

### Running a URL test
```php
<?php

if ($response = $wpt->runTest('https://www.google.com')) {
  if ($response->statusCode == 200) {
    // All test info is available in $response->data.
    $test_id = $response->data->testId;
  }
}
```

### Getting a test's status
```php
<?php
if ($response = $wpt->getTestStatus($test_id)) {
  // All test info is available in $response->data.
  if ($response->statusCode == 200) {
    // Test is complete.
  }
  else if ($response->statusCode == 100) {
    // Test is still running.
  }
  else {
    // Test failed.
  }
}
?>
```

### Getting a test's results
```php
<?php
if ($response = $wpt->getTestResults($test_id)) {
  // All test result info is available in $response->data.
  if ($response->statusCode == 200) {
    // Test is complete.
  }
  else if ($response->statusCode == 100) {
    // Test is still running.
  }
  else {
    // Test failed.
  }
}
?>
```

### Getting test locations
```php
<?php
if ($response = $wpt->getLocations()) {
  if ($response->statusCode == 200) {
    // All locations info is available in $response->data.
  }
}
?>
```
