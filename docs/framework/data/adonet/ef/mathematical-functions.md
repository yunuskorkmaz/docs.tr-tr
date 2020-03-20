---
title: Matematik İşlevleri
ms.date: 03/30/2017
ms.assetid: b040c7cb-156d-40f2-9152-61065b18148c
ms.openlocfilehash: 4512aaa2eeb3e715a1d6f7a8655912eb15162124
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149771"
---
# <a name="mathematical-functions"></a>Matematik İşlevleri

SQL Server için .NET Framework Data Provider (SqlClient), bağımsız değişken olarak sağlanan giriş değerleri üzerinde hesaplamalar gerçekleştiren ve sayısal bir değer sonucu döndüren matematik işlevleri sağlar. Bu işlevler, SqlClient'ı kullandığınızda kullanılabilen SqlServer ad alanındadır. Sağlayıcının ad alanı özelliği, Varlık Çerçevesi'nin bu sağlayıcı tarafından türler ve işlevler gibi belirli yapılar için hangi önek kullanıldığını keşfetmesine olanak tanır. Aşağıdaki tabloda SqlClient matematik işlevleri açıklanmaktadır.  
  
## <a name="absexpression"></a>ABS(ifade)

Mutlak değer işlevini gerçekleştirir.

**Bağımsız Değişkenler**

`expression`: `Int32`Bir `Int64` `Double`, `Decimal`, veya .

**Dönüş Değeri**

Belirtilen ifadenin mutlak değeri.

**Örnek**

`SqlServer.ABS(-2)`

## <a name="acosexpression"></a>ACOS(ifade)

Belirtilen ifadenin arccosine değerini verir.

**Bağımsız Değişkenler**

`expression`: `Double`A .

**Dönüş Değeri**

Bir `Double`.

**Örnek**

`SqlServer.ACOS(.9)`

## <a name="asinexpression"></a>ASIN(ifade)

Belirtilen ifadenin arcsine değerini verir.

**Bağımsız Değişkenler**

`expression`: `Double`A .

**Dönüş Değeri**

Bir `Double`.

**Örnek**

`SqlServer.ASIN(.9)`

## <a name="atanexpression"></a>ATAN(ifade)

Belirtilen sayısal ifadenin arctanjant değerini döndürür.

**Bağımsız Değişkenler**

`expression`: `Double`A .

**Dönüş Değeri**

Bir `Double`.

**Örnek**

`SqlServer.ATAN(9)`

## <a name="atn2expression-expression"></a>ATN2(ifade, ifade)

Radyanlarda, teğet olarak belirtilen iki sayısal ifade arasında olan açıyı döndürür.

**Bağımsız Değişkenler**

`expression`: `Double`A .

**Dönüş Değeri**

Bir `Double`.

**Örnek**

`SqlServer.ATN2(9, 8)`

## <a name="ceilingexpression"></a>TAVAN(ifade)

Belirtilen ifadeyi kendisinden büyük veya eşit olan en küçük karşıcıya dönüştürür.

**Bağımsız Değişkenler**

`expression`: `Int32`Bir `Int64` `Double`, `Decimal`, veya .

**Dönüş Değeri**

Bir `Int32` `Int64`, `Double`, `Decimal`veya .

**Örnek**

[!code-sql[DP EntityServices Concepts#SQLSERVER_CEILING](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_ceiling)]

## <a name="cosexpression"></a>COS(ifade)

Radyanlarda belirtilen açının trigonometrik kosinüsünü hesaplar.

**Bağımsız Değişkenler**

`expression`: `Double`A .

**Dönüş Değeri**

Bir `Double`.

**Örnek**

`SqlServer.COS(45)`

## <a name="cotexpression"></a>COT(ifade)

Radyanlarda belirtilen açının trigonometrik kotanjantını hesaplar.

**Bağımsız Değişkenler**

`expression`: `Double`A .

**Dönüş Değeri**

Bir `Double`.

**Örnek**

`SqlServer.COT(60)`
  
## <a name="degreesradians"></a>DERECELER(radyanlar)

Derece olarak karşılık gelen açıyı döndürür.

**Bağımsız Değişkenler**

`expression`: `Int32`Bir `Int64` `Double`, `Decimal`, veya .

**Dönüş Değeri**

Bir `Int32` `Int64`, `Double`, `Decimal`veya .

**Örnek**

`SqlServer.DEGREES(3.1)`

## <a name="expexpression"></a>EXP(ifade)

Belirtilen sayısal ifadenin üstel değerini hesaplar.

**Bağımsız Değişkenler**

`expression`: `Double`A .

**Dönüş Değeri**

Bir `Double`.

**Örnek**`SqlServer.EXP(1)`

## <a name="floorexpression"></a>KAT(ifade)

Belirtilen ifadeyi, kendisinden daha az veya eşit olan en büyük tümseciye dönüştürür.

**Bağımsız Değişkenler**

`expression`: `Double`A .

**Dönüş Değeri**

Bir `Double`.

**Örnek**

[!code-sql[DP EntityServices Concepts#SQLSERVER_FLOOR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_floor)]

## <a name="logexpression"></a>LOG(ifade)

Belirtilen `float` ifadenin doğal logaritmasını hesaplar.

**Bağımsız Değişkenler**

`expression`: `Double`A .

**Dönüş Değeri**

Bir `Double`.

**Örnek**

`SqlServer.LOG(100)`

## <a name="log10expression"></a>LOG10(ifade)

Belirtilen ifadenin base-10 logarythm döndürür. `Double`

**Bağımsız Değişkenler**

`expression`: `Double`A .

**Dönüş Değeri**

Bir `Double`.

**Örnek**

`SqlServer.LOG10(100)`

## <a name="pi"></a>PI()

Pi'nin sabit değerini `Double`bir . olarak verir

**Dönüş Değeri**

Bir `Double`.

**Örnek**

`SqlServer.PI()`

## <a name="powernumeric_expression-power_expression"></a>GÜÇ(numeric_expression, power_expression)

Belirtilen bir ifadenin değerini belirli bir güce hesaplar.

**Bağımsız Değişkenler**

|  |  |
|--|--|
|`numeric_expression`| Bir `Int32` `Int64`, `Double`, `Decimal`veya .|
|`power_expression`| Bir `Double` yükseltmek için güç temsil `numeric_expression`eder.|

**Dönüş Değeri**

Belirtilen değeri belirtilir. `numeric_expression` `power_expression`

**Örnek**

`SqlServer.POWER(2,7)`

## <a name="radiansexpression"></a>RADYANS(ifade)

Dereceyi radyana dönüştürür.

**Bağımsız Değişkenler**

`expression`: `Int32`Bir `Int64` `Double`, `Decimal`, veya .

**Dönüş Değeri**

Bir `Int32` `Int64`, `Double`, `Decimal`veya .

**Örnek**

`SqlServer.RADIANS(360.0)`

## <a name="randseed"></a>RAND([tohum])

0'dan 1'e rastgele bir değer verir.

**Bağımsız Değişkenler**

Tohum değeri olarak `Int32`bir . Tohum belirtilmemişse, SQL Server Veritabanı Altyapısı rasgele bir tohum değeri atar. Belirli bir tohum değeri için döndürülen sonuç her zaman aynıdır.

**Dönüş Değeri**

0'dan 1'e rastgele `Double` bir değer.

**Örnek**

`SqlServer.RAND()`
  
## <a name="roundnumeric_expression-lengthfunction"></a>ROUND(numeric_expression, uzunluk[,fonksiyon])

Belirtilen uzunluğa veya duyarlıka yuvarlatılmış sayısal bir ifade verir.

**Bağımsız Değişkenler**

|  |  |
|--|--|
|`numeric_expression`| Bir `Int32` `Int64`, `Double`, `Decimal`veya .
|`length`| `Int32` Yuvarlanmak için hassas `numeric_expression` temsil eden bir. Pozitif `length` bir sayı `numeric_expression` olduğunda, `length`ondalık basamak sayısına yuvarlanır. Negatif `length` bir sayı `numeric_expression` olduğunda, ondalık noktanın sol tarafında, 'de `length`belirtildiği gibi yuvarlanır.|
|`function` | İsteğe bağlı. Gerçekleştirecek `Int32` işlem türünü temsil eden bir işlem. İşlev atlandığında veya 0 (varsayılan) `numeric_expression` değeri olduğunda yuvarlanır. 0'dan başka bir değer `numeric_expression` belirtildiğinde kesilir. |

**Dönüş Değeri**

Belirtilen değeri belirtilir. `numeric_expression` `power_expression`

**Örnek**

`SqlServer.ROUND(748.58, -3)`

## <a name="signexpression"></a>SIGN(ifade)

Belirtilen ifadenin pozitif (+1), sıfır (0) veya negatif (-1) işaretini verir.

**Bağımsız Değişkenler**

`expression`: `Int32` `Int64`, `Double`, veya`Decimal`

**Dönüş Değeri**

Bir `Int32` `Int64`, `Double`, `Decimal`veya .

**Örnek**

`SqlServer.SIGN(-10)`

## <a name="sinexpression"></a>SIN(ifade)

Radyanlarda belirtilen açının trigonometrik sinüsünü hesaplar ve `Double` bir ifade döndürür.

**Bağımsız Değişkenler**

`expression`: `Double`A .

**Dönüş Değeri**

Bir `Double`.

**Örnek**`SqlServer.SIN(20)`

## <a name="sqrtexpression"></a>SQRT(ifade)

Belirtilen ifadenin kare kökünü döndürür.

**Bağımsız Değişkenler**

`expression`: `Double`A .

**Dönüş Değeri**

Bir `Double`.

**Örnek**`SqlServer.SQRT(3600)`

## <a name="squareexpression"></a>KARE(ifade)

Belirtilen ifadenin karesini döndürür.

**Bağımsız Değişkenler**

`expression`: `Double`A .

**Dönüş Değeri**

Bir `Double`.

**Örnek**

`SqlServer.SQUARE(25)`

## <a name="tanexpression"></a>TAN(ifade)

Belirtilen ifadenin teğetini hesaplar.

**Bağımsız Değişkenler**

`expression`: `Double`

**Dönüş Değeri**

`Double`

**Örnek**

`SqlServer.TAN(45.0)`
  
## <a name="see-also"></a>Ayrıca bkz.

- [Matematiksel Fonksiyonlar (Transact-SQL)](/sql/t-sql/functions/mathematical-functions-transact-sql)
- [Entity Framework için SqlClient İşlevleri](sqlclient-for-ef-functions.md)
