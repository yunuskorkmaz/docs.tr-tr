---
title: GIT (Entity SQL)
ms.date: 03/30/2017
ms.assetid: f107f29d-005f-4e39-a898-17f163abb1d0
ms.openlocfilehash: 2c6c2ae4c593da1d5fe8cdf3015eb0e31e4b12b5
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249945"
---
# <a name="navigate-entity-sql"></a>GIT (Entity SQL)

Varlıklar arasında belirlenen ilişkinin üzerine gider.

## <a name="syntax"></a>Sözdizimi

```
navigate(instance-expression, [relationship-type], [to-end [, from-end] ])
```

## <a name="arguments"></a>Arguments

`instance-expression`Bir varlık örneği.

`relationship-type`Kavramsal şema tanım dili (CSDL) dosyasından ilişkinin tür adı. , `relationship-type` Ad alanı > \<olarak nitelenir\< . ilişki türü adı >.

`to`İlişkinin sonu.

`from`İlişkinin başlangıcı.

## <a name="return-value"></a>Dönüş Değeri

To end 'in kardinalitesi 1 ise, dönüş değeri `Ref<T>`olacaktır. To end 'in kardinalitei n ise, dönüş değeri `Collection<Ref<T>>`olacaktır.

## <a name="remarks"></a>Açıklamalar

İlişkiler Varlık Veri Modeli (EDM) ilk sınıf yapılardır. İki veya daha fazla varlık türü arasında ilişkiler kurulabilir ve kullanıcılar bir uçtan diğerine (varlık) ilişki üzerinde gezinebilirsiniz. `from`ve `to` ilişki içinde ad çözümlemesinde hiçbir belirsizlik olmadığında koşullu olarak isteğe bağlıdır.

GIT, O ve C alanında geçerlidir.

Bir gezinti yapısının genel formu aşağıdaki şekildedir:

Git (`instance-expression`, `relationship-type`, [ `to-end` [, `from-end` ]])

Örneğin:

```sql
Select o.Id, navigate(o, OrderCustomer, Customer, Order)
From LOB.Orders as o
```

Burada ordercustomer `relationship`, ve müşteri ve sipariş `to-end` ilişkinin (müşteri) ve `from-end` (sipariş) olduğu yerdir. Ordercustomer bir n:1 ilişkisiyse, gezinme ifadesinin sonuç türü ref\<Customer > olur.

Bu ifadenin daha basit biçimi aşağıdaki şekildedir:

```sql
Select o.Id, navigate(o, OrderCustomer)
From LOB.Orders as o
```

Benzer şekilde, aşağıdaki formun bir sorgusunda, gezin ifadesi bir koleksiyon < başvuru\<sırası > > oluşturur.

```sql
Select c.Id, navigate(c, OrderCustomer, Order, Customer)
From LOB.Customers as c
```

Örnek ifadesi bir varlık/başvuru türü olmalıdır.

## <a name="example"></a>Örnek

Aşağıdaki Entity SQL sorgusu, Address ve SalesOrderHeader varlık türleri arasında belirlenen ilişki üzerinde gezinmek için GEZINME işlecini kullanır. Sorgu AdventureWorks Sales modelini temel alır. Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:

1. [Aşağıdaki adımları uygulayın: StructuralType sonuçları](../how-to-execute-a-query-that-returns-structuraltype-results.md)döndüren bir sorgu yürütün.

2. Aşağıdaki sorguyu `ExecuteStructuralTypeQuery` yöntemine bir bağımsız değişken olarak geçirin:

 [!code-csharp[DP EntityServices Concepts 2#NAVIGATE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#navigate)]

## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](entity-sql-reference.md)
- [Nasıl yapılır: Gezinme Işleçle Ilişkilerde gezin](navigate-entity-sql.md)
