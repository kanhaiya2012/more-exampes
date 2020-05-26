## Table of Content
* [fetch event logs](#example1)
* [fetch summary stats](#example2)
* [Domain Add](#example3)
* [Domain delete](#example4)
* [Suppression add](#example5)
* [Suppression delete](#example6)
* [create subaccount](#example7)
* [update subaccount](#example8)
* [enable/disable subaccount](#example9)
* [delete subaccount](#example10)
* [set recurring credit in subaccount](#example11)
* [add credit in subaccount](#example12)
* [get credit details of subaccount](#example13)

<a name="example1"></a>
 
```php

<?php

require_once "vendor/autoload.php";

use PepipostLib\Models;
use PepipostLib\Exceptions;
use PepipostLib\Utils\DateTimeHelper;

$apiKey = 'your api_key here';

$client = new PepipostLib\PepipostClient($apiKey);

$eventsController = $client->getEvents();

$startdate = DateTimeHelper::fromSimpleDate('2016-03-13');
$events = Models\EventsEnum::OPEN;
$sort = Models\SortEnum::ASC;
$enddate = DateTimeHelper::fromSimpleDate('2020-05-26');
$offset = 11;
$limit = 1;
$subject = 'test';
$email = 'email@gmial.com';

try {
    $result = $eventsController->getEventsGET($startdate, $events, $sort, $enddate, $offset, $limit, $subject, null, null, $email);
} catch (PepipostLib\APIException $e) {
    echo 'Caught APIException: ',  $e->getMessage(), "\n"; 
}
```

<a name="example2"></a>
 
```php

<?php

require_once "vendor/autoload.php";

use PepipostLib\Models;
use PepipostLib\Exceptions;
use PepipostLib\Utils\DateTimeHelper;

$apiKey = 'your api_key here';

$client = new PepipostLib\PepipostClient($apiKey);

$statsController = $client->getStats();

$startdate = DateTimeHelper::fromSimpleDate('2016-03-13');
$enddate = DateTimeHelper::fromSimpleDate('2020-05-26');
$offset = 121;
$limit = 1;

try {
    $result = $statsController->getStatsGET($startdate, $enddate, null, $offset, $limit);
} catch (PepipostLib\APIException $e) {
    echo 'Caught APIException: ',  $e->getMessage(), "\n"; 
}
```
<a name="example3"></a>
 
```php
<?php

require_once "vendor/autoload.php";

use PepipostLib\Models;
use PepipostLib\Exceptions;

$apiKey = 'your api_key here';

$client = new PepipostLib\PepipostClient($apiKey);

$domainController = $client->getDomain();

$body = new Models\DomainStruct;
$body->domain = 'example.com';
$body->envelopeName = 'test';

try {
    $result = $domainController->addDomain($body);
} catch (PepipostLib\APIException $e) {
    echo 'Caught APIException: ',  $e->getMessage(), "\n"; 
}
```

<a name="example4"></a>
 
```php
<?php

require_once "vendor/autoload.php";

use PepipostLib\Models;
use PepipostLib\Exceptions;

$apiKey = 'your api_key here';

$client = new PepipostLib\PepipostClient($apiKey);

$domainDeleteController = $client->getDomainDelete();

$body = new Models\DeleteDomain;
$body->domain = 'domain.xyx';

try {
    $result = $domainDeleteController->deleteDomain($body);
} catch (PepipostLib\APIException $e) {
    echo 'Caught APIException: ',  $e->getMessage(), "\n"; 
}
```

<a name="example5"></a>
 
```php
<?php

require_once "vendor/autoload.php";

use PepipostLib\Models;
use PepipostLib\Exceptions;

$apiKey = 'your api_key here';

$client = new PepipostLib\PepipostClient($apiKey);

$suppressionController = $client->getSuppression();

$body = new Models\AddEmailOrDomainToSuppressionList;
$body->domain = 'domain.xyz';
$body->email = 'email@gmail.com';

try {
    $result = $suppressionController->addDomainOrEmailToSuppressionList($body);
} catch (PepipostLib\APIException $e) {
    echo 'Caught APIException: ',  $e->getMessage(), "\n"; 
}
```

<a name="example6"></a>
 
```php
<?php

require_once "vendor/autoload.php";

use PepipostLib\Models;
use PepipostLib\Exceptions;

$apiKey = 'your api_key here';

$client = new PepipostLib\PepipostClient($apiKey);

$suppressionController = $client->getSuppression();

$body = new Models\RemoveEmailOrDomainToSuppressionList;
$body->domain = 'domain.xyx';
$body->email = 'email@gmail.com';

try {
    $result = $suppressionController->removeDomainOrEmailToSuppressionList($body);
} catch (PepipostLib\APIException $e) {
    echo 'Caught APIException: ',  $e->getMessage(), "\n"; 
}
```

<a name="example7"></a>
 
```php
<?php

require_once "vendor/autoload.php";

use PepipostLib\Models;
use PepipostLib\Exceptions;

$apiKey = 'your api_key here';

$client = new PepipostLib\PepipostClient($apiKey);

$subaccountsCreateSubaccountController = $client->getSubaccountsCreateSubaccount();

$body = new Models\CreateSubaccount;
$body->username = 'name';
$body->email = 'email1.gmail.com';
$body->setpassword = 'setpassword8';
$body->password = 'pwd';

try {
    $result = $subaccountsCreateSubaccountController->createSubaccountsCreateSubaccountPOST($body);
} catch (PepipostLib\APIException $e) {
    echo 'Caught APIException: ',  $e->getMessage(), "\n"; 
}
```

<a name="example8"></a>
 
```php
<?php

require_once "vendor/autoload.php";

use PepipostLib\Models;
use PepipostLib\Exceptions;

$apiKey = 'your api_key here';

$client = new PepipostLib\PepipostClient($apiKey);

$subaccountsUpdateSubaccountController = $client->getSubaccountsUpdateSubaccount();

$body = new Models\UpdateSubaccount;
$body->username = 'username';
$body->newEmail = 'email@gmail.com';
$body->newPassword = 'pwd';
$body->confirmPassword = 'pwd';

try {
    $result = $subaccountsUpdateSubaccountController->createSubaccountsUpdateSubaccountPOST($body);
} catch (PepipostLib\APIException $e) {
    echo 'Caught APIException: ',  $e->getMessage(), "\n"; 
}
```

<a name="example9"></a>
 
```php

<?php

require_once "vendor/autoload.php";

use PepipostLib\Models;
use PepipostLib\Exceptions;

$apiKey = 'your api_key here';

$client = new PepipostLib\PepipostClient($apiKey);

$subaccountsController = $client->getSubaccounts();

$body = new Models\EnableOrDisableSubacoount;
$body->username = 'username';
$body->disabled = true;

try {
    $result = $subaccountsController->updateSubaccountsPATCH($body);
} catch (PepipostLib\APIException $e) {
    echo 'Caught APIException: ',  $e->getMessage(), "\n"; 
}
```

<a name="example10"></a>
 
```php

<?php

require_once "vendor/autoload.php";

use PepipostLib\Models;
use PepipostLib\Exceptions;

$apiKey = 'your api_key here';

$client = new PepipostLib\PepipostClient($apiKey);

$subaccountsDeleteController = $client->getSubaccountsDelete();

$body = new Models\DeleteSubacoount;
$body->username = 'username';

try {
    $result = $subaccountsDeleteController->deleteSubaccountsDeleteDELETE($body);
} catch (PepipostLib\APIException $e) {
    echo 'Caught APIException: ',  $e->getMessage(), "\n"; 
}

```

<a name="example11"></a>
 
```php
<?php

require_once "vendor/autoload.php";

use PepipostLib\Models;
use PepipostLib\Exceptions;

$apiKey = 'your api_key here';

$client = new PepipostLib\PepipostClient($apiKey);

$setrecurringcreditddetailsController = $client->getSetrecurringcreditddetails();

$body = new Models\UpdateRecurringCredisOfSubaccount;
$body->username = 'username';
$body->recurringCredit = 1;
$body->timeperiod = Models\TimeperiodEnum::DAILY;

try {
    $result = $setrecurringcreditddetailsController->createSetrecurringcreditddetailsPOST($body);
} catch (PepipostLib\APIException $e) {
    echo 'Caught APIException: ',  $e->getMessage(), "\n"; 
}
```

<a name="example12"></a>
 
```php
<?php

require_once "vendor/autoload.php";

use PepipostLib\Models;
use PepipostLib\Exceptions;

$apiKey = 'your api_key here';

$client = new PepipostLib\PepipostClient($apiKey);

$subaccountsSetsubaccountcreditController = $client->getSubaccountsSetsubaccountcredit();

$body = new Models\UpdateCredisOfSubaccount;
$body->username = 'username';
$body->action = Models\ActionEnum::INCREASE;
$body->amount = 1;

try {
    $result = $subaccountsSetsubaccountcreditController->createSubaccountsSetsubaccountcreditPOST($body);
} catch (PepipostLib\APIException $e) {
    echo 'Caught APIException: ',  $e->getMessage(), "\n"; 
}
```

<a name="example13"></a>
 
```php
<?php

require_once "vendor/autoload.php";

use PepipostLib\Models;
use PepipostLib\Exceptions;

$apiKey = 'your api_key here';

$client = new PepipostLib\PepipostClient($apiKey);

$subaccountsGetSubAccountsController = $client->getSubaccountsGetSubAccounts();

$limit = '4';
$offset = '0';

try {
    $result = $subaccountsGetSubAccountsController->getSubaccountsGetSubAccountsGET($limit, $offset);
} catch (PepipostLib\APIException $e) {
    echo 'Caught APIException: ',  $e->getMessage(), "\n"; 
}
```