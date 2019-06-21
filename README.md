[![Build Status](https://travis-ci.com/payconn/common.svg?branch=master)](https://travis-ci.com/payconn/common)

[Payconn](https://github.com/payconn/common) is a framework agnostic, multi-gateway payment
processing library for PHP. This package implements common classes required by Payconn.

## Supported payment gateways and banks

- [Nestpay (EST)](#nestpay)
- [Vakıf](#vakif)
- [iPara](#ipara)
- [Garanti](#garanti)

## Installation

    $ composer require payconn/common

## Basic Usage

```php
use Payconn\Common\CreditCard;
use Payconn\Garanti;
use Payconn\Garanti\Currency;
use Payconn\Garanti\Model\Purchase;
use Payconn\Garanti\Token;

$token = new Token('30691297', '7000679', '123qweASD/');
$creditCard = new CreditCard('4824894728063019', '23', '07', '172');
$purchase = new Purchase();
$purchase->setTestMode(true);
$purchase->setCreditCard($creditCard);
$purchase->setCurrency(Currency::TRY);
$purchase->setAmount(100);
$purchase->setInstallment(1);
$purchase->generateOrderId();
$response = (new Garanti($token))->purchase($purchase);
if($response->isSuccessful()){
    // success!
}
```

## Change log

Please see [UPGRADE](UPGRADE.md) for more information on how to upgrade to the latest version.

## Support

If you are having general issues with Payconn, we suggest posting on
[Stack Overflow](http://stackoverflow.com/). Be sure to add the

If you believe you have found a bug, please report it using the [GitHub issue tracker](https://github.com/payconn/common/issues),
or better yet, fork the library and submit a pull request.


## Security

If you discover any security related issues, please email muratsac@mail.com instead of using the issue tracker.


## License

The MIT License (MIT). Please see [License File](LICENSE.md) for more information.
