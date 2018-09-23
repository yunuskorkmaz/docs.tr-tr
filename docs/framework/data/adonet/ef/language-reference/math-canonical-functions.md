---
title: Kurallı matematik işlevleri
ms.date: 03/30/2017
ms.assetid: 6f6cddc6-b561-4ebe-84b6-841ef5b4113b
ms.openlocfilehash: 0fc9f4942c3f76f139ab7e4400005f0bfe80204e
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2018
ms.locfileid: "46579342"
---
# <a name="math-canonical-functions"></a>Kurallı matematik işlevleri

Entity SQL aşağıdaki kurallı matematik işlevleri içerir:
  
## <a name="absvalue"></a>Abs(Value)

Mutlak değerini döndürür `value`.

**Bağımsız Değişkenler**

Bir `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, ve `Decimal`.

**Dönüş değeri**

Türünü `value`.

**Örnek**

`Abs(-2)`

## <a name="ceilingvalue"></a>Ceiling(Value)

Küçük olmayan en küçük tamsayı döndürür daha `value`.

**Bağımsız Değişkenler**

A `Single`, `Double`, ve `Decimal`.

**Dönüş değeri**

Türünü `value`.

**Örnek**

[!code-csharp[DP EntityServices Concepts#EDM_CEILING](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_ceiling)]
[!code-sql[DP EntityServices Concepts#EDM_CEILING](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_ceiling)]

## <a name="floorvalue"></a>Floor(Value)

Değerinden büyük olmayan en büyük tamsayı döndürür `value`.

**Bağımsız Değişkenler**

A `Single`, `Double`, ve `Decimal`.

**Dönüş değeri**

Türünü `value`.

**Örnek**

[!code-csharp[DP EntityServices Concepts#EDM_FLOOR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_floor)]
[!code-sql[DP EntityServices Concepts#EDM_FLOOR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_floor)]

## <a name="powervalue-exponent"></a>Güç (değeri, üs)

Belirtilen sonuç döndüren `value` belirtilen `exponent`.

**Bağımsız Değişkenler**

|  |  |
|--|--|
|`value` | Bir `Int32, Int64, Double`, veya `Decimal`. |
|`exponent` | Bir `Int64`, `Double`, veya `Decimal`. |

**Dönüş değeri**

Türünü `value`.

**Örnek**

`Power(748.58,2)`

## <a name="roundvalue"></a>Round(Value)

Tamsayı bölümünü döndürür `value`, en yakın tamsayıya yuvarlanır.

**Bağımsız Değişkenler**

A `Single`, `Double`, ve `Decimal`.

**Dönüş değeri**

Türünü `value`.

**Örnek**

`Round(748.58)`

## <a name="roundvalue-digits"></a>Round (değer, basamak)

Döndürür `value`, yuvarlanır yakın belirtilen `digits`.

**Bağımsız Değişkenler**

|  |  |
|--|--|
|`value`|`Double` veya `Decimal`.|
|`digits`|`Int16` veya `Int32`.|

**Dönüş değeri**

Türünü `value`.

**Örnek**

`Round(748.58,1)`

## <a name="truncatevalue-digits"></a>(Değer, basamak) Kes

Döndürür `value`, kesilmiş yakın belirtilen `digits`.

**Bağımsız Değişkenler**

|  |  |
|--|--|
|`value`|`Double` veya `Decimal`.|
|`digits`|`Int16` veya `Int32`.|

**Dönüş değeri**

Türünü `value`.

**Örnek**

`Truncate(748.58,1)`  
  
 Bu işlevler döndüreceği `null` verildiyse `null` giriş.  
  
 Microsoft SQL istemci yönetilen sağlayıcısında eşdeğer bir işlevselliği kullanılabilir. Daha fazla bilgi için [Entity Framework işlevleri için SqlClient](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kurallı İşlevler](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)
