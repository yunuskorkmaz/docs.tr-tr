---
description: 'Hakkında daha fazla bilgi edinin: TOP (Entity SQL)'
title: ÜST (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4a4a0954-82e2-4eae-bcaf-7c4552f3532d
ms.openlocfilehash: 51e4ce53cff4b47f6f57b6b856ccb09b38e639cf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99673446"
---
# <a name="top-entity-sql"></a>ÜST (Entity SQL)

SELECT yan tümcesi isteğe bağlı ALL/DISTINCT değiştiricisinden sonra isteğe bağlı bir TOP Sub yan tümcesine sahip olabilir. TOP alt yan tümcesi, sorgu sonucundan yalnızca ilk satır kümesinin döndürüleceğini belirtir.

## <a name="syntax"></a>Söz dizimi

```sql
[ TOP (n) ]
```

## <a name="arguments"></a>Bağımsız değişkenler

`n` Döndürülecek satır sayısını belirten sayısal ifade. `n` tek bir sayısal sabit değer veya tek bir parametre olabilir.

## <a name="remarks"></a>Açıklamalar

ÜSTTEKI ifade tek bir sayısal sabit değer veya tek bir parametre olmalıdır. Sabit bir değişmez değer kullanılırsa, değişmez değer türü Edm. Int64 (Byte, int16, Int32 veya Int64) veya Edm. Int64 'e yükseltilebilir bir tür ile eşlenen herhangi bir sağlayıcı türü olmalıdır ve değeri sıfırdan büyük veya sıfıra eşit olmalıdır. Aksi takdirde, bir özel durum oluşturulur. Bir parametre bir ifade olarak kullanılıyorsa, parametre türü de Edm. Int64 öğesine örtülü olarak yükseltilebilir olmalıdır, ancak parametre değerleri geç sınırlanmış olduğundan derleme sırasında gerçek parametre değerinin doğrulaması olmayacaktır.

Aşağıda bir sabit üst ifadeye örnek verilmiştir:

```sql
select distinct top(10) c.a1, c.a2 from T as a
```

Aşağıda parametreli üst ifadeye örnek verilmiştir:

```sql
select distinct top(@topParam) c.a1, c.a2 from T as a
```

Sorgu sıralanmadığı takdirde TOP belirleyici değildir. Belirleyici bir sonuca ihtiyacınız varsa [order by](order-by-entity-sql.md) yan tümcesindeki [SKIP](skip-entity-sql.md) ve [LIMIT](limit-entity-sql.md) alt tümcesini kullanın. TOP ve SKIP/LIMIT birbirini dışlıyor.

## <a name="example"></a>Örnek

Aşağıdaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu, sorgu sonucundan döndürülecek en üstteki bir satırı belirtmek IÇIN üst öğesini kullanır. Sorgu AdventureWorks Sales modelini temel alır. Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:

1. [Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.

2. Aşağıdaki sorguyu yöntemine bir bağımsız değişken olarak geçirin `ExecuteStructuralTypeQuery` :

    [!code-sql[DP EntityServices Concepts#TOP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#top)]

## <a name="see-also"></a>Ayrıca bkz.

- [SELECT](select-entity-sql.md)
- [ŞIMDILIK](skip-entity-sql.md)
- [SıNıRLı](limit-entity-sql.md)
- [ORDER BY](order-by-entity-sql.md)
- [Entity SQL Başvurusu](entity-sql-reference.md)
