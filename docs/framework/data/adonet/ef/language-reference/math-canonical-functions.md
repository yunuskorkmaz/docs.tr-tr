---
title: Kurallı Matematik İşlevleri
ms.date: 03/30/2017
ms.assetid: 6f6cddc6-b561-4ebe-84b6-841ef5b4113b
ms.openlocfilehash: f575785bb198251ef50ba3563e736946253c9526
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59228776"
---
# <a name="math-canonical-functions"></a>Kurallı Matematik İşlevleri

Entity SQL aşağıdaki kurallı matematik işlevleri içerir:
  
## <a name="absvalue"></a>Abs(Value)

Mutlak değerini döndürür `value`.

**Arguments**

Bir `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, ve `Decimal`.

**Dönüş Değeri**

Türünü `value`.

**Örnek**

`Abs(-2)`

## <a name="ceilingvalue"></a>Ceiling(Value)

Küçük olmayan en küçük tamsayı döndürür daha `value`.

**Arguments**

A `Single`, `Double`, ve `Decimal`.

**Dönüş Değeri**

Türünü `value`.

**Örnek**

[!code-csharp[DP EntityServices Concepts#EDM_CEILING](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_ceiling)]
[!code-sql[DP EntityServices Concepts#EDM_CEILING](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_ceiling)]

## <a name="floorvalue"></a>Floor(Value)

Değerinden büyük olmayan en büyük tamsayı döndürür `value`.

**Arguments**

A `Single`, `Double`, ve `Decimal`.

**Dönüş Değeri**

Türünü `value`.

**Örnek**

[!code-csharp[DP EntityServices Concepts#EDM_FLOOR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_floor)]
[!code-sql[DP EntityServices Concepts#EDM_FLOOR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_floor)]

## <a name="powervalue-exponent"></a>Güç (değeri, üs)

Belirtilen sonuç döndüren `value` belirtilen `exponent`.

**Arguments**

|  |  |
|--|--|
|`value` | Bir `Int32, Int64, Double`, veya `Decimal`. |
|`exponent` | Bir `Int64`, `Double`, veya `Decimal`. |

**Dönüş Değeri**

Türünü `value`.

**Örnek**

`Power(748.58,2)`

## <a name="roundvalue"></a>Round(Value)

Tamsayı bölümünü döndürür `value`, en yakın tamsayıya yuvarlanır.

**Arguments**

A `Single`, `Double`, ve `Decimal`.

**Dönüş Değeri**

Türünü `value`.

**Örnek**

`Round(748.58)`

## <a name="roundvalue-digits"></a>Round (değer, basamak)

Döndürür `value`, yuvarlanır yakın belirtilen `digits`.

**Arguments**

|  |  |
|--|--|
|`value`|`Double` veya `Decimal`.|
|`digits`|`Int16` veya `Int32`.|

**Dönüş Değeri**

Türünü `value`.

**Örnek**

`Round(748.58,1)`

## <a name="truncatevalue-digits"></a>(Değer, basamak) Kes

Döndürür `value`, kesilmiş yakın belirtilen `digits`.

**Arguments**

|  |  |
|--|--|
|`value`|`Double` veya `Decimal`.|
|`digits`|`Int16` veya `Int32`.|

**Dönüş Değeri**

Türünü `value`.

**Örnek**

`Truncate(748.58,1)`  
  
 Bu işlevler döndüreceği `null` verildiyse `null` giriş.  
  
 Microsoft SQL istemci yönetilen sağlayıcısında eşdeğer bir işlevselliği kullanılabilir. Daha fazla bilgi için [Entity Framework işlevleri için SqlClient](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kurallı İşlevler](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)
