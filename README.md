# PHP-Http-Class
This project help for sending GET/POST/PUT request easier, being used to crawler.
This use fsockopen, curl to execute request.
**Note**: _fsockopen_ is faster also default of the class is use _fsockopen_

* Author: Phan Thanh Cong 
* Contact: ptcong90@gmail.com
* Copyright: (c) 2011 chiplove.9xpro
* Version: 2.4

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