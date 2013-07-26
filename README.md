# PHP-Http-Class
This project help for sending GET/POST/PUT request easier, being used to crawler.
This use fsockopen, curl to execute request.
**Note**: _fsockopen_ is faster also default of the class is use _fsockopen_

* Author: Phan Thanh Cong 
* Contact: ptcong90@gmail.com
* Copyright: (c) 2011 chiplove.9xpro
* Version: 2.4

## Change logs
#### Version 2.4: Jul 25, 2013
* Use namespace
* Change two static class methods (readBinary, mimeTye) to protected instance method

#### Version 2.3.4: Feb 20, 2013
* Parser header fixed (wrong typing)

#### Version 2.3.3: Nov 5, 2012
* Re-struct, something edited

#### Version 2.3.2: June 12, 2012
* Add some functions, something edited

#### Version 2.3.1: Mar 30, 2012
* Fixed some know bugs (php 5.3)

#### Version 2.3: Feb 2, 2012
* Update for picasa API

#### Version 2.2: Jan 1, 2012
* Add RawPost var to post request (upload image to picasa)

#### Version 2.1: Dec 23, 2011
* Fixed some bugs

#### Version 2.0: Jun 26, 2011
* Rewrite class to easy use
* Fixed some bugs

#### Version 1.2: April 19, 2011
* Mime-type bug on upload file fixed 

#### Version 1.1:
* Upload multi file
* Fixed some bugs

#### Version 1.0:
* Cookie
* Referer
* Proxy (only useCurl)
* SerVersion authentication
* Upload file

## Usage

### Read web content:
	$http = new \ChipVN\Http();
	$http->setTarget("http://www.yourwebsite.com/");
	$http->execute();
	print_r($http->getResponseHeaders());
	echo $http->getResponseText();
	
### Submit form:
	$http = new \ChipVN\Http();
	$http->setTarget("http://www.yourwebsite.com/");
	$http->setParam(array("fieldname"=> $value)); 
	$http->setMethod('POST');
	$http->execute();
	echo $http->getResponseText();
	
### Using Proxy: only useCurl
	$http = new \ChipVN\Http();
        $http->useCurl(true);
	$http->setTarget("http://www.yourwebsite.com/");
	$http->setProxy('proxy_ip:proxy_port');
	$http->execute();
	echo $http->getResponseText();

### Upload file:
	$filePath = getcwd().'/abc.jpg';
	$http = new \ChipVN\Http();
	$http->setTarget("http://www.yourwebsite.com/");
	$http->setSubmitMultipart();
	$http->setParam(array('fileupload'=>"@$filePath"));
	$http->execute();
	print_r($http->getResponseHeaders());
	echo $http->getResponseText();