---
title: ÜST (varlık SQL)
ms.date: 03/30/2017
ms.assetid: 4a4a0954-82e2-4eae-bcaf-7c4552f3532d
ms.openlocfilehash: e7c6cf6b67dc3af29f7ca8fb22af419235a9b833
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61879768"
---
# <a name="top-entity-sql"></a>ÜST (varlık SQL)

SELECT yan tümcesi, isteğe bağlı tüm/DISTINCT değiştirici izleyen bir isteğe bağlı TOP alt yan tümcesinin olabilir. TOP alt yan tümcesi yalnızca ilk satır kümesini sorgu sonuç döndüren belirtir.

## <a name="syntax"></a>Sözdizimi

```
[ TOP (n) ]
```

## <a name="arguments"></a>Arguments

`n` Sayısal ifade döndürülecek satır sayısını belirtir. `n` tek bir sayısal değişmez değerin veya tek bir parametre olabilir.

## <a name="remarks"></a>Açıklamalar

TOP ifadesi tek sayısal sabit değer ya da tek bir parametre olmalıdır. Sabit bir hazır değer kullandıysanız, değişmez değer türü örtük olarak promotable EDM.Int64 (byte, Int16, Int32 veya Int64 veya promotable için EDM.Int64 türüne eşlenen herhangi bir sağlayıcı türü) için ve değeri büyük veya sıfıra eşit olmalıdır. Aksi takdirde bir özel durum oluşturulur. Bir parametre bir ifade kullanılırsa, parametre türü de EDM.Int64 için örtük olarak promotable olmalı, ancak parametre değerlerini geç sınırlanmış çünkü derleme sırasında gerçek parametre değerinin hiçbir doğrulama olacaktır.

Sabit üst ifadesi örneği verilmiştir:

```sql
select distinct top(10) c.a1, c.a2 from T as a
```

Parametreli TOP ifadesi örneği verilmiştir:

```sql
select distinct top(@topParam) c.a1, c.a2 from T as a
```

Sorgu sıralanmış sürece üst belirleyici değildir. Kararlı bir sonuç gerekiyorsa kullanın [atla](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md) ve [sınırı](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md) alt yan tümceleri içinde [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) yan tümcesi. TOP ve SKIP/LIMIT birbirini dışlar.

## <a name="example"></a>Örnek

Aşağıdaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu, sorgu sonucu döndürülecek bir en üst satır belirlemek için üst kullanır. Sorgu, AdventureWorks satış modelini temel alıyor. Derleme ve bu sorguyu çalıştırmak için bu adımları izleyin:

1. Verilen yordamı izleyin [nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).

2. Aşağıdaki sorguda bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:

    [!code-csharp[DP EntityServices Concepts 2#TOP](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#top)]

## <a name="see-also"></a>Ayrıca bkz.

- [SELECT](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)
- [SKIP](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md)
- [LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md)
- [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)
- [Entity SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
