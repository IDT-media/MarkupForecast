# ProcessWire MarkupForecast

Display weather forecast using Forecast.io Weather API in ProcessWire.
To be able to use the Forecast.io API you will have to signup at [https://darksky.net/dev/](darksky.net) for an API Key.

## How to install

Unzip/copy module directory to /site/modules/ directory.

Click "Refresh" on ProcessWire Admin Modules page and Forecast will appear in the Module list. Click "Install" button to install the module.

## How to use

Once you have saved the Forecast.io API Key in the Module settings and have configured available module options you can call the module in your template as following.

```php
<?php
    $forecast = $modules->get('MarkupForecast');
    $currently = $forecast->currently();
?>
```
This will return a multidimensional array of the current weather forecast.

Retrieving complete weather forecast which will return complete response from forecast.io:
`$forecast->complete();`

Retrieving minutely weather forecast:
`$forecast->minutely();`

Retrieving hourly weather forecast:
`$forecast->hourly();`

Retrieving daily weather forecast:
`$forecast->daily();`

Retrieving alerts:
`$forecast->alerts();`

If you need to make another call, in example retrieving forecast data for another city and overriding default module settings you can either use one of above mentioned methods using address or comma separated latitude and longitude string as function parameter `$forecast->currently('My address');` or fetching complete forecast.

```php
<?php
    $forecast = $modules->get('MarkupForecast');
    /**
     * @param string $location A full address or comma separated latitude and longitude values
     * @param int $time Optional UNIX time period for requested forecast
     * @param array $options Optional options for forecast request url in exmaple units (possible values are,
     *                       auto, ca, uk2, us, si) or lang, see https://darksky.net/dev/docs/forecast Documentation
     * @param string $key  Optional with this parameter results will be returned by a given array key
     * @param bool $type Optional when true, results will be returned in JSON string
     * @return array|string
     */
    $fetch = $forecast->fetch('Some address');
?>
```

## Defaul settings options

### API Key (required)
A Forecast.io API Key

### Address
The address of a location (in exmaple: Address, ZIP code, Country).
To retrieve latitude and longitude of the location a Google Maps Geocode API will be used.

### Latitude
The latitude of a location (in decimal degrees). Positive is north, negative is south.

### Longitude
The longitude of a location (in decimal degrees). Positive is east, negative is west.

### Language
Returns summary properties in the desired language.

### Units
Returns weather conditions in the requested units.

### Cache lifetime
A value in seconds for how long a cache of weather request should be preserved.



