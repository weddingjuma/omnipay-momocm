# Omnipay: momocm

**MTN Mobile money driver for the Omnipay PHP payment processing library**

[![Build Status](https://travis-ci.org/thephpleague/omnipay-common.svg?branch=master)](https://travis-ci.org/larrytech7/omnipay-momocm)
<!--[![Latest Stable Version](https://poser.pugx.org/omnipay/2c2p/version.png)](https://packagist.org/packages/omnipay/2c2p)-->
<!--[![Total Downloads](https://poser.pugx.org/omnipay/2c2p/d/total.png)](https://packagist.org/packages/omnipay/2c2p)-->

[Omnipay](https://github.com/thephpleague/omnipay) is a framework agnostic, multi-gateway payment
processing library for PHP 5.3+. This package implements MTN Mobile money support for Omnipay.

## Installation

Omnipay is installed via [Composer](http://getcomposer.org/). 
To install, go to your project root directory and simply run :

    $ composer require league/omnipay larrytech7/omnipay-momocm

OR you can also add the following lines to your composer.json inside the require field parameter
```
"league/omnipay": "^3.0",
"larrytech7/omnipay-momocm" : "^3.0"
```
Then run ```composer update``` to fetch it

## Basic Usage

The following methods are provided by this package:

+ purchase

```
use Omnipay\Omnipay;

$gateway = Omnipay::create('Momoc');
$gateway->setEmail(''); //enter your merchant email obtained from the MTN developer portal

$response = $gateway->purchase(array(
    '_amount' => 100, //the amount to charge
    '_tel' => '677400000' //your customer's phone number
))->send();

if($response->isSuccessful()){
    $mesage = json_decode($response->getMessage());
    //save transaction to database and notify the user
    //.....
}else{
    $message = json_decode($response->getMessage());
    //get error from the message and notify the user
    //......
}
```
For general usage instructions, please see the main [Omnipay](https://github.com/thephpleague/omnipay)
repository.


## Support

If you are having general issues with Omnipay, we suggest posting on
[Stack Overflow](http://stackoverflow.com/). Be sure to add the
[omnipay tag](http://stackoverflow.com/questions/tagged/omnipay) so it can be easily found.

If you want to keep up to date with release anouncements, discuss ideas for the project,
or ask more detailed questions, there is also a [mailing list](https://groups.google.com/forum/#!forum/omnipay) which
you can subscribe to.

If you believe you have found a bug, please report it using the [GitHub issue tracker](https://github.com/dilab/omnipay-2c2p/issues),
or better yet, fork the library and submit a pull request.
