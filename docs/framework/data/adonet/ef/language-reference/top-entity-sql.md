---
title: ÜST (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4a4a0954-82e2-4eae-bcaf-7c4552f3532d
ms.openlocfilehash: 8b55519b7f95deb6463af4c0a6a2a53975e5b5a2
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248980"
---
# <a name="top-entity-sql"></a>ÜST (Entity SQL)

SELECT yan tümcesi isteğe bağlı ALL/DISTINCT değiştiricisinden sonra isteğe bağlı bir TOP Sub yan tümcesine sahip olabilir. TOP alt yan tümcesi, sorgu sonucundan yalnızca ilk satır kümesinin döndürüleceğini belirtir.

## <a name="syntax"></a>Sözdizimi

```
[ TOP (n) ]
```

## <a name="arguments"></a>Arguments

`n`Döndürülecek satır sayısını belirten sayısal ifade. `n`tek bir sayısal sabit değer veya tek bir parametre olabilir.

## <a name="remarks"></a>Açıklamalar

ÜSTTEKI ifade tek bir sayısal sabit değer veya tek bir parametre olmalıdır. Sabit bir değişmez değer kullanılırsa, değişmez değer türü Edm. Int64 (Byte, int16, Int32 veya Int64) veya Edm. Int64 'e yükseltilebilir bir tür ile eşlenen herhangi bir sağlayıcı türü olmalıdır ve değeri sıfırdan büyük veya sıfıra eşit olmalıdır. Aksi takdirde bir özel durum oluşturulur. Bir parametre bir ifade olarak kullanılıyorsa, parametre türü de Edm. Int64 öğesine örtülü olarak yükseltilebilir olmalıdır, ancak parametre değerleri geç sınırlanmış olduğundan derleme sırasında gerçek parametre değerinin doğrulaması olmayacaktır.

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

Aşağıdaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu, sorgu sonucundan döndürülecek en üstteki bir satırı belirtmek için üst öğesini kullanır. Sorgu AdventureWorks Sales modelini temel alır. Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:

1. [Aşağıdaki adımları uygulayın: StructuralType sonuçları](../how-to-execute-a-query-that-returns-structuraltype-results.md)döndüren bir sorgu yürütün.

2. Aşağıdaki sorguyu `ExecuteStructuralTypeQuery` yöntemine bir bağımsız değişken olarak geçirin:

    [!code-csharp[DP EntityServices Concepts 2#TOP](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#top)]

## <a name="see-also"></a>Ayrıca bkz.

- [SELECT](select-entity-sql.md)
- [SKIP](skip-entity-sql.md)
- [LIMIT](limit-entity-sql.md)
- [ORDER BY](order-by-entity-sql.md)
- [Entity SQL Başvurusu](entity-sql-reference.md)
