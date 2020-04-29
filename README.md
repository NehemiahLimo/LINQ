# LINQ
Add or Subtract date, month from current date using DateTime.Now in C#

# Error

```
   LINQ to Entities does not recognize the method 'System.DateTime AddMonths(Int32)' method, and this method cannot be translated into a store expression.

```

# Accepted answer

Usage
```
    DateTime testDate = DateTime.Now.AddMonths(-1);
return Newsletterctx.Subscribers.Count
            (o => o.Validated == false 
             && o.ValidationEmailSent == true 
             && o.SubscriptionDateTime < testDate);

```

# Using SQLFunctions

Usage
```
    today =  DateTime.Now; 
    return Newsletterctx.Subscribers.Count(o =>
    o.Validated == false &&
    o.ValidationEmailSent == true &&
    SqlFunctions.DateAdd("month",1,o.SubscriptionDateTime) <today);

```

Credits:

[website](https://entityframework.net/knowledge-base/3529361/linq-to-entities-with-addmonth-method)