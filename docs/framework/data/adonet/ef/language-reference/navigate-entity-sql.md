---
description: GEZINME hakkında daha fazla bilgi edinin (Entity SQL)
title: GIT (Entity SQL)
ms.date: 03/30/2017
ms.assetid: f107f29d-005f-4e39-a898-17f163abb1d0
ms.openlocfilehash: 7fa39a988429fe0a658b01078d2369ad4767f4a7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99696509"
---
# <a name="navigate-entity-sql"></a>GIT (Entity SQL)

Varlıklar arasında belirlenen ilişkinin üzerine gider.

## <a name="syntax"></a>Söz dizimi

```sql
navigate(instance-expression, [relationship-type], [to-end [, from-end] ])
```

## <a name="arguments"></a>Bağımsız değişkenler

`instance-expression` Bir varlık örneği.

`relationship-type` Kavramsal şema tanım dili (CSDL) dosyasından ilişkinin tür adı. , `relationship-type` Olarak nitelenir \<namespace> . \<relationship type name> ..

`to` İlişkinin sonu.

`from` İlişkinin başlangıcı.

## <a name="return-value"></a>Dönüş Değeri

To end 'in kardinalitesi 1 ise, dönüş değeri olacaktır `Ref<T>` . To end 'in kardinalitei n ise, dönüş değeri olacaktır `Collection<Ref<T>>` .

## <a name="remarks"></a>Açıklamalar

İlişkiler Varlık Veri Modeli (EDM) ilk sınıf yapılardır. İki veya daha fazla varlık türü arasında ilişkiler kurulabilir ve kullanıcılar bir uçtan diğerine (varlık) ilişki üzerinde gezinebilirsiniz. `from` ve `to` ilişki içinde ad çözümlemesinde hiçbir belirsizlik olmadığında koşullu olarak isteğe bağlıdır.

GIT, O ve C alanında geçerlidir.

Bir gezinti yapısının genel formu aşağıdaki şekildedir:

Git ( `instance-expression` , `relationship-type` , [ `to-end` [, `from-end` ]])

Örneğin:

```sql
Select o.Id, navigate(o, OrderCustomer, Customer, Order)
From LOB.Orders as o
```

Burada OrderCustomer, `relationship` ve müşteri ve sipariş `to-end` ilişkinin (müşteri) ve `from-end` (sipariş) olduğu yerdir. OrderCustomer bir n:1 ilişkisiyse, gezinme ifadesinin sonuç türü ref ' dir \<Customer> .

Bu ifadenin daha basit biçimi aşağıdaki şekildedir:

```sql
Select o.Id, navigate(o, OrderCustomer)
From LOB.Orders as o
```

Benzer şekilde, aşağıdaki formun bir sorgusunda, gezinme ifadesi bir koleksiyon<başvuru \<Order>> oluşturur.

```sql
Select c.Id, navigate(c, OrderCustomer, Order, Customer)
From LOB.Customers as c
```

Örnek ifadesi bir varlık/başvuru türü olmalıdır.

## <a name="example"></a>Örnek

Aşağıdaki Entity SQL sorgusu, Address ve SalesOrderHeader varlık türleri arasında belirlenen ilişki üzerinde gezinmek için GEZINME işlecini kullanır. Sorgu AdventureWorks Sales modelini temel alır. Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:

1. [Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.

2. Aşağıdaki sorguyu yöntemine bir bağımsız değişken olarak geçirin `ExecuteStructuralTypeQuery` :

 [!code-sql[DP EntityServices Concepts#NAVIGATE](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#navigate)]

## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](entity-sql-reference.md)
- [Nasıl yapılır: gezinme Işleçle Ilişkilerde gezinme](navigate-entity-sql.md)
