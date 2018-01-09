# square

## Install

Via Composer

``` bash
$ composer require kdaviesnz/square
```

## Usage

``` php

$square = new \kdaviesnz\square\Square("sandbox-sq0atb-xrWTG_wv3dJqYTQaTKgovw");

		$result = $square->getLocations();

		$locationId = $result->locations[0]->id;

		/*
		// Only works for non-sandbox
		$result = $square->listAdditionalRecipientReceivables(
			$locationId,
			"2016-01-15T00:00:00Z",
			"2016-01-31T00:00:00Z"
		);

		$result = $square->listAdditionalRecipientReceivableRefunds(
			$locationId,
			"2016-01-15T00:00:00Z",
			"2016-01-31T00:00:00Z"
		);

		*/


		// Orders
		$idempotencyKey = uniqid();
		$referenceId = "testref";

		$lineItem = new \kdaviesnz\square\OrderRequestLineItem();
		$lineItem->setBasePriceMoney(new \kdaviesnz\square\Money(20.00, "USD"));
		$lineItem->setCatalogObjectId("abcde");
		$lineItem->setName("widget");
		$lineItem->setQuantity(10);
		$discount = new \kdaviesnz\square\OrderRequestDiscount();
		$discount->setAmountMoney(new \kdaviesnz\square\Money("5.00", "USD"));
		$discount->setPercentage(5.00);
		$discounts = array(
			$discount
		);
		$tax = new \kdaviesnz\square\OrderRequestTax();
		$tax->setPercentage(2.00);
		$taxes = array($tax);
		$result = $square->createOrder($locationId, $idempotencyKey, $referenceId, array($lineItem), $taxes, $discounts);




```

## Change log

Please see CHANGELOG.md for more information on what has changed recently.

## Testing

``` bash
$ composer test
```

## Contributing

Please see CONTRIBUTING.md and CODE_OF_CONDUCT.md for details.

## Security

If you discover any security related issues, please email kdaviesnz@gmail.com instead of using the issue tracker.

## Credits

- kdaviesnz@gmail.com

## License

The MIT License (MIT). Please see LICENSE.md for more information.

# square
