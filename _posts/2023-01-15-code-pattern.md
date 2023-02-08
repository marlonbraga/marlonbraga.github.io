---
layout: post
title: Code Pattern
lang: en
ref: 3
date: 2023-01-31 15:09:00
description: Possible code guidance for teams
tags: code
categories: sample-posts
disqus_comments: true
---
### <img src="https://cdn-icons-png.flaticon.com/512/6132/6132221.png" width="20" height="20"> Back-End  
Blablablabla blablabla blabalbla blablabla

Here is a formating os code than I most like to work in my professional path

#### Nomenclature  

| **ELEMENT**        | **PART OF SPEECH** | **RULE**       | **EXAMPLE**     |
| ------------------ |:------------------:|:--------------:| --------------- |
| Class              | Substantive        | PascalCase     | `Product`       |
| Interface          | Substantive        | `I`+PascalCase | `IProduct`      |
| Method             | Verb               | PascalCase     | `ListTickets`   |
| Property           | -                  | PascalCase     | `Tickets`       |
| Public Variables   | -                  | camelCase      | `idProduct`     |
| Private Variables  | -                  | `_`+camelCase  | `_totalReceipt` |
| Constant           | -                  | PascalCase     | `PageTitle`     |
  


##### Indentation and Spacing

```
{
    workingDays++; // ✅ 4 spaces
workingDays++;     // ❌ no spacing
  workingDays++;   // ❌ 2 spaces
}
```
#####   

Each line should contain only one code statement.  
❌  
```
i++; counter++; _totalReceipt=0;  
```

✅  
```
i++;  
counter++;  
_totalReceipt=0;  
```

#### General rules
- Numeric type of monetary values must be `decimal`  
✅ `private decimal annualBilling;`  
❌ `private double annualBilling;`  
❌ `private float annualBilling;`  
- Every `Exception` must be logged.  

#### Performance
- Avoid using `ToList()`, it causes all records to be loaded into memory. Prefer `IQueryable` and `IEnumerable` returns, and only pop into memory when needed.
- Release the resources you take, using `Using` in the `IDisposable` classes (Example: `sqlConnetion`). Prefer `using` to `try/finally`.
- Use `early return` instead of multiple nested IFs.

#### Automated tests
- Automated tests should be easy to read, short and only test one thing. Use the default `Arrange/Act/Assert`.