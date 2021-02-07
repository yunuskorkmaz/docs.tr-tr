---
description: 'Daha fazla bilgi edinin: matematik kurallı Işlevleri'
title: Kurallı Matematik İşlevleri
ms.date: 03/30/2017
ms.assetid: 6f6cddc6-b561-4ebe-84b6-841ef5b4113b
ms.openlocfilehash: 55072099f5766d48ea3067a2e9eaa187a8b3f111
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99739371"
---
# <a name="math-canonical-functions"></a>Kurallı Matematik İşlevleri

Entity SQL aşağıdaki matematik kurallı işlevlerini içerir:
  
## <a name="absvalue"></a>ABS (değer)

`value` öğesinin mutlak değerini döndürür.

**Bağımsız değişkenler**

,,,,, `Int16` `Int32` `Int64` `Byte` `Single` `Double` , Ve `Decimal` .

**Dönüş Değeri**

Türü `value` .

**Örnek**

`Abs(-2)`

## <a name="ceilingvalue"></a>Tavan (değer)

Küçüktür olan en küçük tamsayıyı döndürür `value` .

**Bağımsız değişkenler**

`Single`, `Double` , Ve `Decimal` .

**Dönüş Değeri**

Türü `value` .

**Örnek**

[!code-csharp[DP EntityServices Concepts#EDM_CEILING](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_ceiling)]
[!code-sql[DP EntityServices Concepts#EDM_CEILING](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_ceiling)]

## <a name="floorvalue"></a>Floor (değer)

Değerinden büyük olmayan en büyük tamsayıyı döndürür `value` .

**Bağımsız değişkenler**

`Single`, `Double` , Ve `Decimal` .

**Dönüş Değeri**

Türü `value` .

**Örnek**

[!code-csharp[DP EntityServices Concepts#EDM_FLOOR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_floor)]
[!code-sql[DP EntityServices Concepts#EDM_FLOOR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_floor)]

## <a name="powervalue-exponent"></a>Güç (değer, üs)

Belirtilen öğesinin sonucunu `value` belirtilen şekilde döndürür `exponent` .

**Bağımsız değişkenler**

|  |  |
|--|--|
|`value` | `Int32, Int64, Double`, Veya `Decimal` . |
|`exponent` | Bir `Int64` , `Double` veya `Decimal` . |

**Dönüş Değeri**

Türü `value` .

**Örnek**

`Power(748.58,2)`

## <a name="roundvalue"></a>Round (değer)

Öğesinin tamsayı bölümünü döndürür `value` , en yakın tamsayıya yuvarlanır.

**Bağımsız değişkenler**

`Single`, `Double` , Ve `Decimal` .

**Dönüş Değeri**

Türü `value` .

**Örnek**

`Round(748.58)`

## <a name="roundvalue-digits"></a>Round (değer, basamak)

`value`Belirtilen en yakın değere yuvarlanır ve döndürür `digits` .

**Bağımsız değişkenler**

|  |  |
|--|--|
|`value`|`Double` veya `Decimal`.|
|`digits`|`Int16` veya `Int32`.|

**Dönüş Değeri**

Türü `value` .

**Örnek**

`Round(748.58,1)`

## <a name="truncatevalue-digits"></a>Kes (değer, basamak)

`value`Belirtilen en yakın değere kesilen öğesini döndürür `digits` .

**Bağımsız değişkenler**

|  |  |
|--|--|
|`value`|`Double` veya `Decimal`.|
|`digits`|`Int16` veya `Int32`.|

**Dönüş Değeri**

Türü `value` .

**Örnek**

`Truncate(748.58,1)`  
  
 Bu işlevler, `null` verilen giriş durumunda döndürülür `null` .  
  
 Eşdeğer işlevsellik, Microsoft SQL Istemci tarafından yönetilen sağlayıcıda bulunur. Daha fazla bilgi için bkz. [Entity Framework işlevleri Için SqlClient](../sqlclient-for-ef-functions.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kurallı İşlevler](canonical-functions.md)
