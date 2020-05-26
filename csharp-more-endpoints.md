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
 
```cs
using System;
using System.Collections.Generic;
using System.Globalization;
using System.Threading.Tasks;

using Pepipost.Standard;
using Pepipost.Standard.Utilities;
using Pepipost.Standard.Models;
using Pepipost.Standard.Controllers;
using Pepipost.Standard.Exceptions;
using System.IO;

namespace Testing
{
    class Program {
        static void Main(string[] args){
            Configuration.ApiKey = "your api_key here";
            PepipostClient client = new PepipostClient();
            EventsController events = client.Events;
            
            DateTime startdate = DateTime.Parse("2016-03-13");
            EventsEnum? events = Events.PROCESSED;
            SortEnum? sort = Sort.DESC;
            DateTime? enddate = DateTime.Parse("2020-05-26");
            string subject = "test";
            string email = "email@gmail.com";
            
            try 
            {
                object result = events.GetEventsGETAsync(startdate, events, sort, enddate, null, null, subject, null, null, email).Result;
            }
            catch (APIException e){};        
        }
    }
}
```

<a name="example2"></a>
 
```cs
using System;
using System.Collections.Generic;
using System.Globalization;
using System.Threading.Tasks;

using Pepipost.Standard;
using Pepipost.Standard.Utilities;
using Pepipost.Standard.Models;
using Pepipost.Standard.Controllers;
using Pepipost.Standard.Exceptions;
using System.IO;

namespace Testing
{
    class Program {
        static void Main(string[] args){
            Configuration.ApiKey = "your api_key here";
            PepipostClient client = new PepipostClient();
            StatsController stats = client.Stats;
            
            DateTime startdate = DateTime.Parse("2016-03-13");
            DateTime? enddate = DateTime.Parse("2020-05-26");
            AggregatedByEnum? aggregatedBy = AggregatedBy.WEEK;
            
            try 
            {
                object result = stats.GetStatsGETAsync(startdate, enddate, aggregatedBy, null, null).Result;
            }
            catch (APIException e){};        
        }
    }
}
```
<a name="example3"></a>
 
```cs
using System;
using System.Collections.Generic;
using System.Globalization;
using System.Threading.Tasks;

using Pepipost.Standard;
using Pepipost.Standard.Utilities;
using Pepipost.Standard.Models;
using Pepipost.Standard.Controllers;
using Pepipost.Standard.Exceptions;
using System.IO;

namespace Testing
{
    class Program {
        static void Main(string[] args){
            Configuration.ApiKey = "your api_key here";
            PepipostClient client = new PepipostClient();
            DomainController domain = client.Domain;
            
            DomainStruct body = new DomainStruct();
            body.Domain = "example.com";
            body.EnvelopeName = "test";
            
            try 
            {
                object result = domain.AddDomainAsync(body).Result;
            }
            catch (APIException e){};        
        }
    }
}
```

<a name="example4"></a>
 
```cs
using System;
using System.Collections.Generic;
using System.Globalization;
using System.Threading.Tasks;

using Pepipost.Standard;
using Pepipost.Standard.Utilities;
using Pepipost.Standard.Models;
using Pepipost.Standard.Controllers;
using Pepipost.Standard.Exceptions;
using System.IO;

namespace Testing
{
    class Program {
        static void Main(string[] args){
            Configuration.ApiKey = "your api_key here";
            PepipostClient client = new PepipostClient();
            DomainDeleteController domainDelete = client.DomainDelete;
            
            DeleteDomain body = new DeleteDomain();
            body.Domain = "example.com";
            
            try 
            {
                object result = domainDelete.DeleteDomainAsync(body).Result;
            }
            catch (APIException e){};        
        }
    }
}
```

<a name="example5"></a>
 
```cs
using System;
using System.Collections.Generic;
using System.Globalization;
using System.Threading.Tasks;

using Pepipost.Standard;
using Pepipost.Standard.Utilities;
using Pepipost.Standard.Models;
using Pepipost.Standard.Controllers;
using Pepipost.Standard.Exceptions;
using System.IO;

namespace Testing
{
    class Program {
        static void Main(string[] args){
            Configuration.ApiKey = "your api_key here";
            PepipostClient client = new PepipostClient();
            SuppressionController suppression = client.Suppression;
            
            AddEmailOrDomainToSuppressionList body = new AddEmailOrDomainToSuppressionList();
            body.Domain = "example.com";
            body.Email = "email@gmail.com";
            
            try 
            {
                object result = suppression.AddDomainOrEmailToSuppressionListAsync(body).Result;
            }
            catch (APIException e){};        
        }
    }
}
```

<a name="example6"></a>
 
```cs
using System;
using System.Collections.Generic;
using System.Globalization;
using System.Threading.Tasks;

using Pepipost.Standard;
using Pepipost.Standard.Utilities;
using Pepipost.Standard.Models;
using Pepipost.Standard.Controllers;
using Pepipost.Standard.Exceptions;
using System.IO;

namespace Testing
{
    class Program {
        static void Main(string[] args){
            Configuration.ApiKey = "your api_key here";
            PepipostClient client = new PepipostClient();
            SuppressionController suppression = client.Suppression;
            
            RemoveEmailOrDomainToSuppressionList body = new RemoveEmailOrDomainToSuppressionList();
            body.Domain = "example.com";
            body.Email = "email@gmail.com";
            
            try 
            {
                object result = suppression.RemoveDomainOrEmailToSuppressionListAsync(body).Result;
            }
            catch (APIException e){};        
        }
    }
}
```

<a name="example7"></a>
 
```cs
using System;
using System.Collections.Generic;
using System.Globalization;
using System.Threading.Tasks;

using Pepipost.Standard;
using Pepipost.Standard.Utilities;
using Pepipost.Standard.Models;
using Pepipost.Standard.Controllers;
using Pepipost.Standard.Exceptions;
using System.IO;

namespace Testing
{
    class Program {
        static void Main(string[] args){
            Configuration.ApiKey = "your api_key here";
            PepipostClient client = new PepipostClient();
            SubaccountsCreateSubaccountController subaccountsCreateSubaccount = client.SubaccountsCreateSubaccount;
            
            CreateSubaccount body = new CreateSubaccount();
            body.Username = "name";
            body.Email = "email1.gmail.com";
            body.Setpassword = "1";
            body.Password = "pwd";
            
            try 
            {
                object result = subaccountsCreateSubaccount.CreateSubaccountsCreateSubaccountPOSTAsync(body).Result;
            }
            catch (APIException e){};        
        }
    }
}
```

<a name="example8"></a>
 
```cs
using System;
using System.Collections.Generic;
using System.Globalization;
using System.Threading.Tasks;

using Pepipost.Standard;
using Pepipost.Standard.Utilities;
using Pepipost.Standard.Models;
using Pepipost.Standard.Controllers;
using Pepipost.Standard.Exceptions;
using System.IO;

namespace Testing
{
    class Program {
        static void Main(string[] args){
            Configuration.ApiKey = "your api_key here";
            PepipostClient client = new PepipostClient();
            SuppressionController suppression = client.Suppression;
            
            RemoveEmailOrDomainToSuppressionList body = new RemoveEmailOrDomainToSuppressionList();
            body.Domain = "example.com";
            body.Email = "email@gmail.com";
            
            try 
            {
                object result = suppression.RemoveDomainOrEmailToSuppressionListAsync(body).Result;
            }
            catch (APIException e){};        
        }
    }
}
```

<a name="example9"></a>
 
```cs
using System;
using System.Collections.Generic;
using System.Globalization;
using System.Threading.Tasks;

using Pepipost.Standard;
using Pepipost.Standard.Utilities;
using Pepipost.Standard.Models;
using Pepipost.Standard.Controllers;
using Pepipost.Standard.Exceptions;
using System.IO;

namespace Testing
{
    class Program {
        static void Main(string[] args){
            Configuration.ApiKey = "your api_key here";
            PepipostClient client = new PepipostClient();
            SubaccountsController subaccounts = client.Subaccounts;
            
            EnableOrDisableSubacoount body = new EnableOrDisableSubacoount();
            body.Username = "username";
            body.Disabled = true;
            
            try 
            {
                object result = subaccounts.UpdateSubaccountsPATCHAsync(body).Result;
            }
            catch (APIException e){};        
        }
    }
}
```

<a name="example10"></a>
 
```cs
using System;
using System.Collections.Generic;
using System.Globalization;
using System.Threading.Tasks;

using Pepipost.Standard;
using Pepipost.Standard.Utilities;
using Pepipost.Standard.Models;
using Pepipost.Standard.Controllers;
using Pepipost.Standard.Exceptions;
using System.IO;

namespace Testing
{
    class Program {
        static void Main(string[] args){
            Configuration.ApiKey = "your api_key here";
            PepipostClient client = new PepipostClient();
            SubaccountsDeleteController subaccountsDelete = client.SubaccountsDelete;
            
            DeleteSubacoount body = new DeleteSubacoount();
            body.Username = "username";
            
            try 
            {
                object result = subaccountsDelete.DeleteSubaccountsDeleteDELETEAsync(body).Result;
            }
            catch (APIException e){};        
        }
    }
}
```

<a name="example11"></a>
 
```cs
using System;
using System.Collections.Generic;
using System.Globalization;
using System.Threading.Tasks;

using Pepipost.Standard;
using Pepipost.Standard.Utilities;
using Pepipost.Standard.Models;
using Pepipost.Standard.Controllers;
using Pepipost.Standard.Exceptions;
using System.IO;

namespace Testing
{
    class Program {
        static void Main(string[] args){
            Configuration.ApiKey = "your api_key here";
            PepipostClient client = new PepipostClient();
            SetrecurringcreditddetailsController setrecurringcreditddetails = client.Setrecurringcreditddetails;
            
            UpdateRecurringCredisOfSubaccount body = new UpdateRecurringCredisOfSubaccount();
            body.Username = "username";
            body.RecurringCredit = 100;
            body.Timeperiod = Timeperiod.WEEKLY;
            
            try 
            {
                object result = setrecurringcreditddetails.CreateSetrecurringcreditddetailsPOSTAsync(body).Result;
            }
            catch (APIException e){};        
        }
    }
}
```

<a name="example12"></a>
 
```cs
using System;
using System.Collections.Generic;
using System.Globalization;
using System.Threading.Tasks;

using Pepipost.Standard;
using Pepipost.Standard.Utilities;
using Pepipost.Standard.Models;
using Pepipost.Standard.Controllers;
using Pepipost.Standard.Exceptions;
using System.IO;

namespace Testing
{
    class Program {
        static void Main(string[] args){
            Configuration.ApiKey = "your api_key here";
            PepipostClient client = new PepipostClient();
            SubaccountsSetsubaccountcreditController subaccountsSetsubaccountcredit = client.SubaccountsSetsubaccountcredit;
            
            UpdateCredisOfSubaccount body = new UpdateCredisOfSubaccount();
            body.Username = "username";
            body.Action = Action.DECREASE;
            body.Amount = 100;
            
            try 
            {
                object result = subaccountsSetsubaccountcredit.CreateSubaccountsSetsubaccountcreditPOSTAsync(body).Result;
            }
            catch (APIException e){};        
        }
    }
}
```

<a name="example13"></a>
 
```cs
using System;
using System.Collections.Generic;
using System.Globalization;
using System.Threading.Tasks;

using Pepipost.Standard;
using Pepipost.Standard.Utilities;
using Pepipost.Standard.Models;
using Pepipost.Standard.Controllers;
using Pepipost.Standard.Exceptions;
using System.IO;

namespace Testing
{
    class Program {
        static void Main(string[] args){
            Configuration.ApiKey = "your api_key here";
            PepipostClient client = new PepipostClient();
            SubaccountsGetSubAccountsController subaccountsGetSubAccounts = client.SubaccountsGetSubAccounts;
            
            string limit = "100";
            string offset = "1";
            
            try 
            {
                object result = subaccountsGetSubAccounts.GetSubaccountsGetSubAccountsGETAsync(limit, offset).Result;
            }
            catch (APIException e){};        
        }
    }
}
```