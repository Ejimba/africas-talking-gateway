Africas Talking Gateway
=======================

## Introduction

Unofficial [Africas Talking Gateway](https://www.africastalking.com/) PHP package to integrate SMS, USSD, VOICE, AIRTIME in your application.

## Requirements

- PHP 5.3 or above
- cURL

## Installation

### [Composer](http://getcomposer.org/) Installation

```bash
composer require ejimba/africas-talking-gateway
```

## Usage

```php
<?php

use AfricasTalkingGateway\AfricasTalkingGateway;

// Specify your login credentials
$username   = "MyAfricasTalkingUsername";
$apikey     = "MyAfricasTalkingAPIKey";

// Specify the numbers that you want to send to in a comma-separated list
// Please ensure you include the country code (+254 for Kenya in this case)
$recipients = "+254711XXXYYY,+254733YYYZZZ";

// And of course we want our recipients to know what we really do
$message    = "I'm a lumberjack and its ok, I sleep all night and I work all day";

// Create a new instance of the gateway class
$gateway    = new AfricasTalkingGateway($username, $apikey);

// Any gateway error will be captured by the custom Exception class below, 
// so wrap the call in a try-catch block
try 
{

    $results = $gateway->sendMessage($recipients, $message);
            
    foreach( $results as $result ) {
    
        // status is either "Success" or "error message"
        echo " Number: " .$result->number;
        echo " Status: " .$result->status;
        echo " MessageId: " .$result->messageId;
        echo " Cost: "   .$result->cost."\n";
    
    }

}
catch ( AfricasTalkingGatewayException $e )
{

    echo "Encountered an error while sending: ".$e->getMessage();

}

?>
```

## Bugs and Issues

Bugs and issues are tracked on [GitHub](https://github.com/ejimba/africas-talking-gateway/issues)

## License

Licensed under [Africas Talking License](LICENSE).