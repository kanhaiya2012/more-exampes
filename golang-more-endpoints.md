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
 
```go
package main

import(
	"pepipost_lib/pepipost_pkg"
	"time"
	"encoding/json"
	"pepipost_lib/configuration_pkg"
	"pepipost_lib/models_pkg"
)

func main(){
    ApiKey := "your api_key here"
    
    client := PepipostClient.NewPEPIPOSTCLIENT(ApiKey)
    
    events := client.Events()
    
    Startdate := "2016-03-13T12:52:32.123Z"
    Events := models_pkg.Events_SENT
    Sort := models_pkg.Sort_ASC
    Offset := int64(111)
    Limit := int64(1)
    Subject := "test"
    Email := "email@gmail.com"
    
    var err error
    var result interface{}
    result, err = events.GetEventsGET(Startdate, Events, Sort, nil, Offset, Limit, Subject, nil, nil, Email)
    
    if err != nil{
        //TODO: Use err variable here
    }else{
        //TODO: Use result variable here
        println(result)
    }
    
    

}
```

<a name="example2"></a>
 
```go
package main

import(
	"pepipost_lib/pepipost_pkg"
	"time"
	"encoding/json"
	"pepipost_lib/configuration_pkg"
	"pepipost_lib/models_pkg"
)

func main(){
    ApiKey := "your api_key here"
    
    client := PepipostClient.NewPEPIPOSTCLIENT(ApiKey)
    
    stats := client.Stats()
    
    Startdate := "2016-03-13T12:52:32.123Z"
    AggregatedBy := models_pkg.AggregatedBy_MONTH
    Offset := int64(111)
    Limit := int64(1)
    
    var err error
    var result interface{}
    result, err = stats.GetStatsGET(Startdate, nil, AggregatedBy, Offset, Limit)
    
    if err != nil{
        //TODO: Use err variable here
    }else{
        //TODO: Use result variable here
        println(result)
    }
    
    

}
```
<a name="example3"></a>
 
```go
package main

import(
	"pepipost_lib/pepipost_pkg"
	"time"
	"encoding/json"
	"pepipost_lib/configuration_pkg"
	"pepipost_lib/models_pkg"
)

func main(){
    ApiKey := "your api_key here"
    
    client := PepipostClient.NewPEPIPOSTCLIENT(ApiKey)
    
    domain := client.Domain()
    
    Body := &models_pkg.DomainStruct{}
    Body.Domain = "example.com"
    Body.EnvelopeName = "test"
    
    var err error
    var result interface{}
    result, err = domain.AddDomain(Body)
    
    if err != nil{
        //TODO: Use err variable here
    }else{
        //TODO: Use result variable here
        println(result)
    }
    
    

}
```

<a name="example4"></a>
 
```go
package main

import(
	"pepipost_lib/pepipost_pkg"
	"time"
	"encoding/json"
	"pepipost_lib/configuration_pkg"
	"pepipost_lib/models_pkg"
)

func main(){
    ApiKey := "your api_key here"
    
    client := PepipostClient.NewPEPIPOSTCLIENT(ApiKey)
    
    domainDelete := client.DomainDelete()
    
    Body := &models_pkg.DeleteDomain{}
    Body.Domain = "example.com"
    
    var err error
    var result interface{}
    result, err = domainDelete.DeleteDomain(Body)
    
    if err != nil{
        //TODO: Use err variable here
    }else{
        //TODO: Use result variable here
        println(result)
    }
    
    

}
```

<a name="example5"></a>
 
```go
package main

import(
	"pepipost_lib/pepipost_pkg"
	"time"
	"encoding/json"
	"pepipost_lib/configuration_pkg"
	"pepipost_lib/models_pkg"
)

func main(){
    ApiKey := "your api_key here"
    
    client := PepipostClient.NewPEPIPOSTCLIENT(ApiKey)
    
    suppression := client.Suppression()
    
    Body := &models_pkg.AddEmailOrDomainToSuppressionList{}
    Body.Domain = "example.com"
    Body.Email = "email@gmail.com"
    
    var err error
    var result interface{}
    result, err = suppression.AddDomainOrEmailToSuppressionList(Body)
    
    if err != nil{
        //TODO: Use err variable here
    }else{
        //TODO: Use result variable here
        println(result)
    }
    
    

}
```

<a name="example6"></a>
 
```go
package main

import(
	"pepipost_lib/pepipost_pkg"
	"time"
	"encoding/json"
	"pepipost_lib/configuration_pkg"
	"pepipost_lib/models_pkg"
)

func main(){
    ApiKey := "your api_key here"
    
    client := PepipostClient.NewPEPIPOSTCLIENT(ApiKey)
    
    suppression := client.Suppression()
    
    Body := &models_pkg.RemoveEmailOrDomainToSuppressionList{}
    Body.Domain = "example.com"
    Body.Email = "email@gmail.com"
    
    var err error
    var result interface{}
    result, err = suppression.RemoveDomainOrEmailToSuppressionList(Body)
    
    if err != nil{
        //TODO: Use err variable here
    }else{
        //TODO: Use result variable here
        println(result)
    }
    
    

}
```

<a name="example7"></a>
 
```go
package main

import(
	"pepipost_lib/pepipost_pkg"
	"time"
	"encoding/json"
	"pepipost_lib/configuration_pkg"
	"pepipost_lib/models_pkg"
)

func main(){
    ApiKey := "your api_key here"
    
    client := PepipostClient.NewPEPIPOSTCLIENT(ApiKey)
    
    subaccountsCreateSubaccount := client.SubaccountsCreateSubaccount()
    
    Body := &models_pkg.CreateSubaccount{}
    Body.Username = "name"
    Body.Email = "email1.gmail.com"
    Body.Setpassword = "setpassword8"
    Body.Password = "pwd"
    
    var err error
    var result interface{}
    result, err = subaccountsCreateSubaccount.CreateSubaccountsCreateSubaccountPOST(Body)
    
    if err != nil{
        //TODO: Use err variable here
    }else{
        //TODO: Use result variable here
        println(result)
    }
    
    

}
```

<a name="example8"></a>
 
```go
package main

import(
	"pepipost_lib/pepipost_pkg"
	"time"
	"encoding/json"
	"pepipost_lib/configuration_pkg"
	"pepipost_lib/models_pkg"
)

func main(){
    ApiKey := "your api_key here"
    
    client := PepipostClient.NewPEPIPOSTCLIENT(ApiKey)
    
    subaccountsUpdateSubaccount := client.SubaccountsUpdateSubaccount()
    
    Body := &models_pkg.UpdateSubaccount{}
    Body.Username = "username"
    Body.NewEmail = "email@gmail.com"
    Body.NewPassword = "pwd"
    Body.ConfirmPassword = "pwd"
    
    var err error
    var result interface{}
    result, err = subaccountsUpdateSubaccount.CreateSubaccountsUpdateSubaccountPOST(Body)
    
    if err != nil{
        //TODO: Use err variable here
    }else{
        //TODO: Use result variable here
        println(result)
    }
    
    

}
```

<a name="example9"></a>
 
```go
package main

import(
	"pepipost_lib/pepipost_pkg"
	"time"
	"encoding/json"
	"pepipost_lib/configuration_pkg"
	"pepipost_lib/models_pkg"
)

func main(){
    ApiKey := "your api_key here"
    
    client := PepipostClient.NewPEPIPOSTCLIENT(ApiKey)
    
    subaccounts := client.Subaccounts()
    
    Body := &models_pkg.EnableOrDisableSubacoount{}
    Body.Username = "username"
    Body.Disabled = true
    
    var err error
    var result interface{}
    result, err = subaccounts.UpdateSubaccountsPATCH(Body)
    
    if err != nil{
        //TODO: Use err variable here
    }else{
        //TODO: Use result variable here
        println(result)
    }
    
    

}
```

<a name="example10"></a>
 
```go
package main

import(
	"pepipost_lib/pepipost_pkg"
	"time"
	"encoding/json"
	"pepipost_lib/configuration_pkg"
	"pepipost_lib/models_pkg"
)

func main(){
    ApiKey := "your api_key here"
    
    client := PepipostClient.NewPEPIPOSTCLIENT(ApiKey)
    
    subaccountsDelete := client.SubaccountsDelete()
    
    Body := &models_pkg.DeleteSubacoount{}
    Body.Username = "username"
    
    var err error
    var result interface{}
    result, err = subaccountsDelete.DeleteSubaccountsDeleteDELETE(Body)
    
    if err != nil{
        //TODO: Use err variable here
    }else{
        //TODO: Use result variable here
        println(result)
    }
    
    

}
```

<a name="example11"></a>
 
```go
package main

import(
	"pepipost_lib/pepipost_pkg"
	"time"
	"encoding/json"
	"pepipost_lib/configuration_pkg"
	"pepipost_lib/models_pkg"
)

func main(){
    ApiKey := "your api_key here"
    
    client := PepipostClient.NewPEPIPOSTCLIENT(ApiKey)
    
    setrecurringcreditddetails := client.Setrecurringcreditddetails()
    
    Body := &models_pkg.UpdateRecurringCredisOfSubaccount{}
    Body.Username = "username"
    Body.RecurringCredit = int64(100)
    Body.Timeperiod = models_pkg.Timeperiod_WEEKLY
    
    var err error
    var result interface{}
    result, err = setrecurringcreditddetails.CreateSetrecurringcreditddetailsPOST(Body)
    
    if err != nil{
        //TODO: Use err variable here
    }else{
        //TODO: Use result variable here
        println(result)
    }
    
    

}
```

<a name="example12"></a>
 
```go
package main

import(
	"pepipost_lib/pepipost_pkg"
	"time"
	"encoding/json"
	"pepipost_lib/configuration_pkg"
	"pepipost_lib/models_pkg"
)

func main(){
    ApiKey := "your api_key here"
    
    client := PepipostClient.NewPEPIPOSTCLIENT(ApiKey)
    
    subaccountsSetsubaccountcredit := client.SubaccountsSetsubaccountcredit()
    
    Body := &models_pkg.UpdateCredisOfSubaccount{}
    Body.Username = "username"
    Body.Action = models_pkg.Action_DECREASE
    Body.Amount = int64(100)
    
    var err error
    var result interface{}
    result, err = subaccountsSetsubaccountcredit.CreateSubaccountsSetsubaccountcreditPOST(Body)
    
    if err != nil{
        //TODO: Use err variable here
    }else{
        //TODO: Use result variable here
        println(result)
    }
    
    

}
```

<a name="example13"></a>
 
```go
package main

import(
	"pepipost_lib/pepipost_pkg"
	"time"
	"encoding/json"
	"pepipost_lib/configuration_pkg"
	"pepipost_lib/models_pkg"
)

func main(){
    ApiKey := "your api_key here"
    
    client := PepipostClient.NewPEPIPOSTCLIENT(ApiKey)
    
    subaccountsGetSubAccounts := client.SubaccountsGetSubAccounts()
    
    Limit := "100"
    Offset := "1"
    
    var err error
    var result interface{}
    result, err = subaccountsGetSubAccounts.GetSubaccountsGetSubAccountsGET(Limit, Offset)
    
    if err != nil{
        //TODO: Use err variable here
    }else{
        //TODO: Use result variable here
        println(result)
    }
    
    

}
```