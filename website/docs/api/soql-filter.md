---
sidebar_position: 3
---

# Filter

Specify and adjust single condition.

## predefinied
### id

- `WHERE Id = :accountId`
- `WHERE Id IN :accountIds`

**Signature**

```apex
Filter id()
```

**Example**

```sql
SELECT Id
FROM Account
WHERE Id = :accountId
```
```apex
SOQL.of(Account.SObjectType)
    .whereAre(SOQL.Filter.id().equal(accountId))
    .toList();
```

### recordType

- `WHERE RecordType.DeveloperName = 'Partner'`

**Signature**

```apex
Filter recordType()
```

**Example**

```sql
SELECT Id
FROM Account
WHERE RecordType.DeveloperName = 'Partner'
```
```apex
SOQL.of(Account.SObjectType)
    .whereAre(SOQL.Filter.recordType().equal('Partner'))
    .toList();
```

### Name

- `WHERE Name = 'My Account'`

**Signature**

```apex
Filter name()
```

**Example**

```sql
SELECT Id
FROM Account
WHERE Name = 'My Account'
```
```apex
SOQL.of(Account.SObjectType)
    .whereAre(SOQL.Filter.name().equal('My Account'))
    .toList();
```
## fields
### with field

Specify field that should be used in the condition.

**Signature**

```apex
Filter with(SObjectField field)
```

**Example**

```sql
SELECT Id
FROM Account
WHERE Name = 'My Account'
```
```apex
SOQL.of(Account.SObjectType)
    .whereAre(SOQL.Filter.with(Account.Name).equal('My Account'))
    .toList();
```

### with related field

Specify parent field that should be used in the condition.

**Signature**

```apex
Filter with(String relationshipPath, SObjectField field);
```

**Example**

```sql
SELECT Id
FROM Contact
WHERE Account.Name = 'My Account'
```
```apex
SOQL.of(Contact.SObjectType)
    .whereAre(SOQL.Filter.with('Account', Account.Name).equal('My Account'))
    .toList();
```

## comperators

### isNull

- `WHERE Industry = NULL`

**Signature**

```apex
Filter isNull()
```

**Example**

```sql
SELECT Id
FROM Account
WHERE Account.Industry = NULL
```
```apex
SOQL.of(Account.SObjectType)
    .whereAre(SOQL.Filter.with(Account.Industry).isNull())
    .toList();
```

### isNotNull

- `WHERE Industry != NULL`

**Signature**

```apex
Filter isNotNull()
```

**Example**

```sql
SELECT Id
FROM Account
WHERE Account.Industry != NULL
```
```apex
SOQL.of(Account.SObjectType)
    .whereAre(SOQL.Filter.with(Account.Industry).isNotNull())
    .toList();
```

### isTrue

- `WHERE IsDeleted = TRUE`

**Signature**

```apex
Filter isTrue()
```

**Example**

```sql
SELECT Id
FROM Account
WHERE Account.IsDeleted = TRUE
```
```apex
SOQL.of(Account.SObjectType)
    .whereAre(SOQL.Filter.with(Account.IsDeleted).isTrue())
    .toList();
```

### isFalse

- `WHERE IsDeleted = FALSE`

**Signature**

```apex
Filter isFalse()
```

**Example**

```sql
SELECT Id
FROM Account
WHERE Account.IsDeleted != NULL
```
```apex
SOQL.of(Account.SObjectType)
    .whereAre(SOQL.Filter.with(Account.IsDeleted).isFalse())
    .toList();
```

### equal

- `WHERE Name = 'My Account'`
- `WHERE NumberOfEmployees = 10`
- `WHERE IsDeleted = true`

**Signature**

```apex
Filter equal(Object value)
```

**Example**

```sql
SELECT Id FROM Account WHERE Name = 'My Account'

SELECT Id FROM Account WHERE NumberOfEmployees = 10

SELECT Id FROM Account WHERE IsDeleted = true
```

```apex
SOQL.of(Contact.SObjectType)
    .whereAre(SOQL.Filter.with(Account.Name).equal('My Account'))
    .toList();

SOQL.of(Account.SObjectType)
    .whereAre(SOQL.Filter.with(Account.NumberOfEmployees).equal(10))
    .toList();

SOQL.of(Account.SObjectType)
    .whereAre(SOQL.Filter.with(Account.IsDeleted).equal(true))
    .toList();
```

### notEqual

- `WHERE Name != 'My Account'`
- `WHERE NumberOfEmployees != 10`
- `WHERE IsDeleted != true`

**Signature**

```apex
Filter notEqual(Object value)
```

**Example**

```sql
SELECT Id FROM Account WHERE Name != 'My Account'

SELECT Id FROM Account WHERE NumberOfEmployees != 10

SELECT Id FROM Account WHERE IsDeleted != true
```
```apex
SOQL.of(Contact.SObjectType)
    .whereAre(SOQL.Filter.with(Account.Name).notEqual('My Account'))
    .toList();

SOQL.of(Contact.SObjectType)
    .whereAre(SOQL.Filter.with(Account.NumberOfEmployees).notEqual(10))
    .toList();

SOQL.of(Contact.SObjectType)
    .whereAre(SOQL.Filter.with(Account.IsDeleted).notEqual(true))
    .toList();
```

### lessThan

- `WHERE NumberOfEmployees < 10`

**Signature**

```apex
Filter lessThan(Object value)
```

**Example**

```sql
SELECT Id
FROM Account
WHERE NumberOfEmployees < 10
```
```apex
SOQL.of(Contact.SObjectType)
    .whereAre(SOQL.Filter.with(Account.NumberOfEmployees).lessThan(10))
    .toList();
```

### greaterThan

- `WHERE NumberOfEmployees > 10`

**Signature**

```apex
Filter greaterThan(Object value)
```

**Example**

```sql
SELECT Id
FROM Account
WHERE NumberOfEmployees > 10
```
```apex
SOQL.of(Contact.SObjectType)
    .whereAre(SOQL.Filter.with(Account.NumberOfEmployees).greaterThan(10))
    toList();
```

### lessOrEqual

- `WHERE NumberOfEmployees <= 10`

**Signature**

```apex
Filter lessOrEqual(Object value)
```

**Example**

```sql
SELECT Id
FROM Account
WHERE NumberOfEmployees <= 10
```
```apex
SOQL.of(Contact.SObjectType)
    .whereAre(SOQL.Filter.with(Account.NumberOfEmployees).lessOrEqual(10))
    .toList();
```

### greaterOrEqual

- `WHERE NumberOfEmployees >= 10`

**Signature**

```apex
Filter greaterOrEqual(Object value)
```

**Example**

```sql
SELECT Id
FROM Account
WHERE NumberOfEmployees >= 10
```
```apex
SOQL.of(Contact.SObjectType)
    .whereAre(SOQL.Filter.with(Account.NumberOfEmployees).greaterOrEqual(10))
    .toList();
```

### containsSome

- `WHERE Name LIKE ('My', 'Acc')`

**Signature**

```apex
Filter containsSome(List<String> values)
```

**Example**

```sql
SELECT Id
FROM Account
WHERE Name LIKE ('My', 'Acc')
```
```apex
List<String> names = new List<String>{ 'Acc', 'My' };

SOQL.of(Contact.SObjectType)
    .whereAre(SOQL.Filter.with(Account.Name).containsSome(names))
    .toList();
```

### contains

- `WHERE Name LIKE '%My%'`

**Signature**

```apex
Filter contains(String value)
Filter contains(String prefix, String value, String suffix);
```

**Example**

```sql
SELECT Id
FROM Account
WHERE Name = '%My%'
```
```apex
SOQL.of(Contact.SObjectType)
    .whereAre(SOQL.Filter.with(Account.Name).contains('My'))
    .toList();

SOQL.of(Contact.SObjectType)
    .whereAre(SOQL.Filter.with(Account.Name).contains('_', 'My', '%'))
    .toList();
```

### endsWith

- `WHERE Name LIKE '%My'`

**Signature**

```apex
Filter endsWith(String value)
```

**Example**

```sql
SELECT Id
FROM Account
WHERE Name = '%My'
```
```apex
SOQL.of(Contact.SObjectType)
    .whereAre(SOQL.Filter.with(Account.Name).endsWith('My'))
    .toList();
```

### startsWith

- `WHERE Name LIKE 'My%'`

**Signature**

```apex
Filter startsWith(String value)
```

**Example**

```sql
SELECT Id
FROM Account
WHERE Name = 'My%'
```
```apex
SOQL.of(Contact.SObjectType)
    .whereAre(SOQL.Filter.with(Account.Name).startsWith('My'))
    .toList();
```

### isIn

- `WHERE Id IN :accountIds`

**Signature**

```apex
Filter isIn(List<Object> inList)
```

**Example**

```sql
SELECT Id
FROM Account
WHERE Id IN :accountIds
```
```apex
SOQL.of(Contact.SObjectType)
    .whereAre(SOQL.Filter.with(Account.Id).isIn(accountIds))
    .toList();
```

### notIn

- `WHERE Id NOT IN :accountIds`

**Signature**

```apex
Filter notIn(List<Object> inList)
```

**Example**

```sql
SELECT Id
FROM Account
WHERE Id NOT IN :accountIds
```
```apex
SOQL.of(Contact.SObjectType)
    .whereAre(SOQL.Filter.with(Account.Id).notIn(accountIds))
    .toList();
```

## join query

### isIn

- `WHERE Id IN (SELECT AccountId FROM Contact WHERE Name = 'My Contact')`

**Signature**

```apex
Filter isIn(JoinQuery joinQuery)
```

**Example**

```sql
SELECT Id
FROM Account
WHERE Id IN (
    SELECT AccountId
    FROM Contact
    WHERE Name = 'My Contact'
)
```
```apex
SOQL.of(Account.SObjectType)
    .whereAre(SOQL.Filter.with(Account.Id).isIn(
        SOQL.InnerJoin.of(Contact.SObjectType)
            .with(Contact.AccountId)
            .whereAre(SOQL.Filter.with(Contact.Name).equal('My Contact'))
    )).toList();
```

### notIn

- `WHERE Id NOT IN (SELECT AccountId FROM Contact WHERE Name = 'My Contact')`

**Signature**

```apex
Filter notIn(JoinQuery joinQuery)
```

**Example**

```sql
SELECT Id
FROM Account
WHERE Id NOT IN (
    SELECT AccountId
    FROM Contact
    WHERE Name = 'My Contact'
)
```
```apex
SOQL.of(Contact.SObjectType)
    .whereAre(SOQL.Filter.with(Account.Id).notIn(
        SOQL.InnerJoin.of(Contact.SObjectType)
            .with(Contact.AccountId)
            .whereAre(SOQL.Filter.with(Contact.Name).equal('My Contact'))
    )).toList();
```

## multi-select picklist

### includesAll

- `WHERE Roles INCLUDES ('Business User;Decision Maker')`

**Signature**

```apex
Filter includesAll(Iterable<String> iterable)
```

**Example**

```sql
SELECT Id
FROM AccountContactRelation
WHERE Roles INCLUDES ('Business User;Decision Maker')
```

```apex
List<String> roles = new List<String>{ 'Business User', 'Decision Maker' };

SOQL builder = SOQL.of(AccountContactRelation.SObjectType)
    .with(AccountContactRelation.Id)
    .whereAre(SOQL.Filter.with(AccountContactRelation.Roles).includesAll(roles));
 ```

### includesSome

- `WHERE Roles INCLUDES ('Business User', 'Decision Maker')`

**Signature**

```apex
Filter includesSome(Iterable<String> iterable)
```

**Example**

```sql
SELECT Id
FROM AccountContactRelation
WHERE Roles INCLUDES ('Business User', 'Decision Maker')
```

```apex
List<String> roles = new List<String>{ 'Business User', 'Decision Maker' };

SOQL builder = SOQL.of(AccountContactRelation.SObjectType)
    .with(AccountContactRelation.Id)
    .whereAre(SOQL.Filter.with(AccountContactRelation.Roles).includesSome(roles));
 ```

### excludesAll

- `WHERE Roles EXCLUDES ('Business User', 'Decision Maker')`

**Signature**

```apex
Filter excludesAll(Iterable<String> iterable)
```

**Example**

```sql
SELECT Id
FROM AccountContactRelation
WHERE Roles EXCLUDES ('Business User', 'Decision Maker')
```

```apex
List<String> roles = new List<String>{ 'Business User', 'Decision Maker' };

SOQL builder = SOQL.of(AccountContactRelation.SObjectType)
    .with(AccountContactRelation.Id)
    .whereAre(SOQL.Filter.with(AccountContactRelation.Roles).excludesAll(roles));
 ```

### excludesSome

- `WHERE Roles EXCLUDES ('Business User;Decision Maker')`

**Signature**

```apex
Filter excludesSome(Iterable<String> iterable)
```

**Example**

```sql
SELECT Id
FROM AccountContactRelation
WHERE Roles EXCLUDES ('Business User;Decision Maker')
```

```apex
List<String> roles = new List<String>{ 'Business User', 'Decision Maker' };

SOQL builder = SOQL.of(AccountContactRelation.SObjectType)
    .with(AccountContactRelation.Id)
    .whereAre(SOQL.Filter.with(AccountContactRelation.Roles).excludesSome(roles));
 ```

## additional

### removeWhenNull

Condition will be removed when filter's value is null.

**Signature**

```apex
Filter removeWhenNull()
```

**Example**

```sql
SELECT Id
FROM Account
```
```apex
String accountName = null;

SOQL.of(Account.SObjectType)
    .whereAre(SOQL.Filter.with(Account.Name).equal(accountName).removeWhenNull())
    .toList();
```
