---
title: GIT (Entity SQL)
ms.date: 03/30/2017
ms.assetid: f107f29d-005f-4e39-a898-17f163abb1d0
ms.openlocfilehash: 09128a367a02e1f9b206a9cc068987166c76381b
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319549"
---
# <a name="navigate-entity-sql"></a>GIT (Entity SQL)

Varlıklar arasında belirlenen ilişkinin üzerine gider.

## <a name="syntax"></a>Sözdizimi

```sql
navigate(instance-expression, [relationship-type], [to-end [, from-end] ])
```

## <a name="arguments"></a>Bağımsız Değişkenler

bir varlığın örneğini `instance-expression`.

kavramsal şema tanım dili (CSDL) dosyasından ilişkinin tür adını `relationship-type`. `relationship-type`, \<ad alanı > olarak nitelenir.\<ilişki türü adı >.

ilişkinin sonuna `to`.

ilişkinin başlangıcını `from`.

## <a name="return-value"></a>Dönüş Değeri

To end 'in kardinalitesi 1 ise, dönüş değeri `Ref<T>`olur. To end 'in kardinalitei n ise, dönüş değeri `Collection<Ref<T>>`olacaktır.

## <a name="remarks"></a>Açıklamalar

İlişkiler Varlık Veri Modeli (EDM) ilk sınıf yapılardır. İki veya daha fazla varlık türü arasında ilişkiler kurulabilir ve kullanıcılar bir uçtan diğerine (varlık) ilişki üzerinde gezinebilirsiniz. ilişki içinde ad çözümlemesinde hiçbir belirsizlik olmadığında, `from` ve `to` koşullu olarak isteğe bağlıdır.

GIT, O ve C alanında geçerlidir.

Bir gezinti yapısının genel formu aşağıdaki şekildedir:

gezinme (`instance-expression`, `relationship-type`, [`to-end` [, `from-end`]])

Örneğin:

```sql
Select o.Id, navigate(o, OrderCustomer, Customer, Order)
From LOB.Orders as o
```

Burada OrderCustomer `relationship`ve müşteri ve sipariş ilişkinin `to-end` (müşteri) ve `from-end` (sipariş). OrderCustomer bir n:1 ilişkisi ise, gezinme ifadesinin sonuç türü, başvuru\<müşteri > olur.

Bu ifadenin daha basit biçimi aşağıdaki şekildedir:

```sql
Select o.Id, navigate(o, OrderCustomer)
From LOB.Orders as o
```

Benzer şekilde, aşağıdaki formun bir sorgusunda, gezinme ifadesi bir koleksiyon < ref\<sırası > > oluşturur.

```sql
Select c.Id, navigate(c, OrderCustomer, Order, Customer)
From LOB.Customers as c
```

Örnek ifadesi bir varlık/başvuru türü olmalıdır.

## <a name="example"></a>Örnek

Aşağıdaki Entity SQL sorgusu, Address ve SalesOrderHeader varlık türleri arasında belirlenen ilişki üzerinde gezinmek için GEZINME işlecini kullanır. Sorgu AdventureWorks Sales modelini temel alır. Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:

1. [Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.

2. Aşağıdaki sorguyu `ExecuteStructuralTypeQuery` yöntemine bir bağımsız değişken olarak geçirin:

 [!code-sql[DP EntityServices Concepts#NAVIGATE](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#navigate)]

## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](entity-sql-reference.md)
- [Nasıl yapılır: gezinme Işleçle Ilişkilerde gezinme](navigate-entity-sql.md)
