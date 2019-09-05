---
title: Kurallı Matematik İşlevleri
ms.date: 03/30/2017
ms.assetid: 6f6cddc6-b561-4ebe-84b6-841ef5b4113b
ms.openlocfilehash: 9417ff9836912017c9d88bb24a18849aaac2836a
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250302"
---
# <a name="math-canonical-functions"></a>Kurallı Matematik İşlevleri

Entity SQL aşağıdaki matematik kurallı işlevlerini içerir:
  
## <a name="absvalue"></a>ABS (değer)

Öğesinin `value`mutlak değerini döndürür.

**Bağımsız Değişkenler**

`Int16` ,`Byte` ,,`Decimal`,, ,Ve.`Double` `Int32` `Int64` `Single`

**Dönüş değeri**

Türü `value`.

**Örnek**

`Abs(-2)`

## <a name="ceilingvalue"></a>Tavan (değer)

Küçüktür olan `value`en küçük tamsayıyı döndürür.

**Bağımsız Değişkenler**

`Single`, ,`Double`Ve .`Decimal`

**Dönüş değeri**

Türü `value`.

**Örnek**

[!code-csharp[DP EntityServices Concepts#EDM_CEILING](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_ceiling)]
[!code-sql[DP EntityServices Concepts#EDM_CEILING](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_ceiling)]

## <a name="floorvalue"></a>Floor (değer)

Değerinden `value`büyük olmayan en büyük tamsayıyı döndürür.

**Bağımsız Değişkenler**

`Single`, ,`Double`Ve .`Decimal`

**Dönüş değeri**

Türü `value`.

**Örnek**

[!code-csharp[DP EntityServices Concepts#EDM_FLOOR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_floor)]
[!code-sql[DP EntityServices Concepts#EDM_FLOOR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_floor)]

## <a name="powervalue-exponent"></a>Güç (değer, üs)

Belirtilen öğesinin `value` sonucunu belirtilen `exponent`şekilde döndürür.

**Bağımsız Değişkenler**

|  |  |
|--|--|
|`value` | `Int32, Int64, Double`, Veya`Decimal`. |
|`exponent` | Bir `Int64`, `Double`veya .`Decimal` |

**Dönüş değeri**

Türü `value`.

**Örnek**

`Power(748.58,2)`

## <a name="roundvalue"></a>Round (değer)

Öğesinin `value`tamsayı bölümünü döndürür, en yakın tamsayıya yuvarlanır.

**Bağımsız Değişkenler**

`Single`, ,`Double`Ve .`Decimal`

**Dönüş değeri**

Türü `value`.

**Örnek**

`Round(748.58)`

## <a name="roundvalue-digits"></a>Round (değer, basamak)

`value` Belirtilen`digits`en yakın değere yuvarlanır ve döndürür.

**Bağımsız Değişkenler**

|  |  |
|--|--|
|`value`|`Double`veya `Decimal`.|
|`digits`|`Int16`veya `Int32`.|

**Dönüş değeri**

Türü `value`.

**Örnek**

`Round(748.58,1)`

## <a name="truncatevalue-digits"></a>Kes (değer, basamak)

`value` Belirtilen`digits`en yakın değere kesilen öğesini döndürür.

**Bağımsız Değişkenler**

|  |  |
|--|--|
|`value`|`Double`veya `Decimal`.|
|`digits`|`Int16`veya `Int32`.|

**Dönüş değeri**

Türü `value`.

**Örnek**

`Truncate(748.58,1)`  
  
 Bu işlevler, verilen `null` `null` giriş durumunda döndürülür.  
  
 Eşdeğer işlevsellik, Microsoft SQL Istemci tarafından yönetilen sağlayıcıda bulunur. Daha fazla bilgi için bkz. [Entity Framework işlevleri Için SqlClient](../sqlclient-for-ef-functions.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kurallı İşlevler](canonical-functions.md)
