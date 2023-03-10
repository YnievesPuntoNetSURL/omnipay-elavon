# Omnipay: Elavon

**Elavon payment processing driver for the Omnipay PHP payment processing library**

[![Build Status](https://travis-ci.org/ynievespuntonetsurl/omnipay-elavon.svg)](https://travis-ci.org/ynievespuntonetsurl/omnipay-elavon) [![Coverage Status](https://coveralls.io/repos/github/ynievespuntonetsurl/omnipay-elavon/badge.svg?branch=master)](https://coveralls.io/github/ynievespuntonetsurl/omnipay-elavon?branch=master) [![Latest Stable Version](https://poser.pugx.org/ynievespuntonetsurl/omnipay-elavon/v/stable.svg)](https://packagist.org/packages/ynievespuntonetsurl/omnipay-elavon) [![Total Downloads](https://poser.pugx.org/ynievespuntonetsurl/omnipay-elavon/downloads)](https://packagist.org/packages/ynievespuntonetsurl/omnipay-elavon)

[Omnipay](https://github.com/thephpleague/omnipay)  is a framework agnostic, multi-gateway payment processing library for PHP. This package implements Elavon Payments support for Omnipay. Please see the full [Converge documentation](https://www.myvirtualmerchant.com/VirtualMerchant/download/developerGuide.pdf) for more information.

## Installation

Omnipay is installed via [Composer](http://getcomposer.org/). To install, simply require `league/omnipay` and `ynievespuntonetsurl/omnipay-elavon`

```bash
composer require league/omnipay ynievespuntonetsurl/omnipay-elavon
```

## Basic Usage

The following gateways are provided by this package:

* Converge

```php
<?php
    $gateway = \Omnipay\Omnipay::create('Elavon_Converge')->initialize([
        'merchantId' => '000000',
        'username' => 'USERNAME',
        'password' => 'PASSWORD',
        'testMode' => true,// False by default
    ]);

    $params = array(
        'amount'                => 10.00,
        'card'                  => $card,
        'ssl_invoice_number'    => 1,
        'ssl_show_form'         => 'false',
        'ssl_result_format'     => 'ASCII',
    );

    $response = $gateway->purchase($params)->send();

    if ($response->isSuccessful()) {
        // successful
        $reference = $response->getTransactionReference();
        // ...
    } else {
        throw new ApplicationException($response->getMessage());
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

If you believe you have found a bug, please report it using the [GitHub issue tracker](https://github.com/ynievespuntonetsurl/omnipay-elavon/issues),
or better yet, fork the library and submit a pull request.
