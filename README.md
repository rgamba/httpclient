# httpclient
PHP Http Client is a fully featured HTTP client created 100% in PHP. It doesn't use cURL or other external libraries.

## Usage
A very basic http request:
```php
<?php
require_once('httpclient.php');
$http = new HttpClient("http://mydomain.com");
$http->get("/info.php");
echo $http->getBody(); // Just print the response body
```
### Headers and response status codes
```php
<?php
require_once('httpclient.php');
$http = new HttpClient("http://mydomain.com");
$http->setHeader("Content-Type","application/x-www-form-urlencoded");
$http->post("/login.php", array(
  "username" => "rgamba@gmail.com",
  "password" => "mypasswd123"
));
echo "The response status code is: " . $http->status()->number . " with the message: " . $http->status()->msg;
echo $http->getBody(); // Just print the response body
echo "The Server response header is: " . $http->getHeader("Server");
```
### Authorization
```php
<?php
require_once('httpclient.php');
$http = new HttpClient("http://mydomain.com");
$http->basicAuth("username","passwd");
// Or use digest auth...
// http->digestAuth("username","passwd"); 
$http->get("/secure")
echo $http->getBody(); // Just print the response body
```
### Allow redirects and accept cookies
```php
<?php
require_once('httpclient.php');
$http = new HttpClient("http://mydomain.com");
$http->allowRedirects(true, 2);
$http->acceptCookies(true)
$http->get("/main")
echo $http->getBody(); // Just print the response body
```
