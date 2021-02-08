---
description: 'Daha fazla bilgi edinin: matematik Işlevleri'
title: Matematik İşlevleri
ms.date: 03/30/2017
ms.assetid: b040c7cb-156d-40f2-9152-61065b18148c
ms.openlocfilehash: 6bf1f116d6d88a8a188dc31cab91fbf26bdaea36
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795033"
---
# <a name="mathematical-functions"></a>Matematik İşlevleri

SQL Server (SqlClient) için .NET Framework Veri Sağlayıcısı, bağımsız değişken olarak sağlanan giriş değerlerinde hesaplamalar gerçekleştiren ve sayısal bir değer sonucu döndüren matematik işlevleri sağlar. Bu işlevler, SqlClient kullandığınızda kullanılabilir olan SqlServer ad alanıdır. Bir sağlayıcının ad alanı özelliği Entity Framework, bu sağlayıcı tarafından türler ve işlevler gibi belirli yapılar için kullanılan öneki bulmasını sağlar. Aşağıdaki tabloda, SqlClient matematik işlevleri açıklanmaktadır.  
  
## <a name="absexpression"></a>ABS (ifade)

Mutlak değer işlevini gerçekleştirir.

**Bağımsız değişkenler**

`expression`: Bir `Int32` , `Int64` , `Double` veya `Decimal` .

**Dönüş Değeri**

Belirtilen ifadenin mutlak değeri.

**Örnek**

`SqlServer.ABS(-2)`

## <a name="acosexpression"></a>ACOS (ifade)

Belirtilen ifadenin Arkkosinüs değerini döndürür.

**Bağımsız değişkenler**

`expression`: A `Double` .

**Dönüş Değeri**

Bir `Double`.

**Örnek**

`SqlServer.ACOS(.9)`

## <a name="asinexpression"></a>ASIN (ifade)

Belirtilen ifadenin arksinüs değerini döndürür.

**Bağımsız değişkenler**

`expression`: A `Double` .

**Dönüş Değeri**

Bir `Double`.

**Örnek**

`SqlServer.ASIN(.9)`

## <a name="atanexpression"></a>ATAN (ifade)

Belirtilen sayısal ifadenin arktanjant değerini döndürür.

**Bağımsız değişkenler**

`expression`: A `Double` .

**Dönüş Değeri**

Bir `Double`.

**Örnek**

`SqlServer.ATAN(9)`

## <a name="atn2expression-expression"></a>ATN2 (ifade, ifade)

Tanjantı belirtilen iki sayısal ifade arasında olan radyan cinsinden açıyı döndürür.

**Bağımsız değişkenler**

`expression`: A `Double` .

**Dönüş Değeri**

Bir `Double`.

**Örnek**

`SqlServer.ATN2(9, 8)`

## <a name="ceilingexpression"></a>TAVAN (ifade)

Belirtilen ifadeyi, bu değerden büyük veya ona eşit en küçük tamsayıya dönüştürür.

**Bağımsız değişkenler**

`expression`: Bir `Int32` , `Int64` , `Double` veya `Decimal` .

**Dönüş Değeri**

`Int32`,, `Int64` `Double` Veya `Decimal` .

**Örnek**

[!code-sql[DP EntityServices Concepts#SQLSERVER_CEILING](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_ceiling)]

## <a name="cosexpression"></a>COS (ifade)

Radyan cinsinden belirtilen açının trigonometrik kosinüsünü hesaplar.

**Bağımsız değişkenler**

`expression`: A `Double` .

**Dönüş Değeri**

Bir `Double`.

**Örnek**

`SqlServer.COS(45)`

## <a name="cotexpression"></a>COT (ifade)

Radyan cinsinden belirtilen açıdaki trigonometrik kovaryansı hesaplar.

**Bağımsız değişkenler**

`expression`: A `Double` .

**Dönüş Değeri**

Bir `Double`.

**Örnek**

`SqlServer.COT(60)`
  
## <a name="degreesradians"></a>DERECE (radyan)

Karşılık gelen açıyı derece cinsinden döndürür.

**Bağımsız değişkenler**

`expression`: Bir `Int32` , `Int64` , `Double` veya `Decimal` .

**Dönüş Değeri**

`Int32`,, `Int64` `Double` Veya `Decimal` .

**Örnek**

`SqlServer.DEGREES(3.1)`

## <a name="expexpression"></a>EXP (ifade)

Belirtilen bir sayısal ifadenin üstel değerini hesaplar.

**Bağımsız değişkenler**

`expression`: A `Double` .

**Dönüş Değeri**

Bir `Double`.

**Örnek**`SqlServer.EXP(1)`

## <a name="floorexpression"></a>FLOOR (ifade)

Belirtilen ifadeyi ona eşit veya ondan küçük olan en büyük tamsayıya dönüştürür.

**Bağımsız değişkenler**

`expression`: A `Double` .

**Dönüş Değeri**

Bir `Double`.

**Örnek**

[!code-sql[DP EntityServices Concepts#SQLSERVER_FLOOR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_floor)]

## <a name="logexpression"></a>GÜNLÜK (ifade)

Belirtilen ifadenin doğal logaritmasını hesaplar `float` .

**Bağımsız değişkenler**

`expression`: A `Double` .

**Dönüş Değeri**

Bir `Double`.

**Örnek**

`SqlServer.LOG(100)`

## <a name="log10expression"></a>LOG10 (ifade)

Belirtilen ifadenin 10 tabanında logaritmasını döndürür `Double` .

**Bağımsız değişkenler**

`expression`: A `Double` .

**Dönüş Değeri**

Bir `Double`.

**Örnek**

`SqlServer.LOG10(100)`

## <a name="pi"></a>PI ()

Pi değerinin sabit değerini bir olarak döndürür `Double` .

**Dönüş Değeri**

Bir `Double`.

**Örnek**

`SqlServer.PI()`

## <a name="powernumeric_expression-power_expression"></a>Güç (numeric_expression power_expression)

Belirtilen bir ifadenin değerini belirtilen bir kuvvet olarak hesaplar.

**Bağımsız değişkenler**

|  |  |
|--|--|
|`numeric_expression`| `Int32`,, `Int64` `Double` Veya `Decimal` .|
|`power_expression`| Öğesini `Double` , öğesini yükseltmek için gereken kuvveti temsil eder `numeric_expression` .|

**Dönüş Değeri**

Belirtilen değerinin `numeric_expression` belirtilen değeri `power_expression` .

**Örnek**

`SqlServer.POWER(2,7)`

## <a name="radiansexpression"></a>RADYAN (ifade)

Dereceyi radyana dönüştürür.

**Bağımsız değişkenler**

`expression`: Bir `Int32` , `Int64` , `Double` veya `Decimal` .

**Dönüş Değeri**

`Int32`,, `Int64` `Double` Veya `Decimal` .

**Örnek**

`SqlServer.RADIANS(360.0)`

## <a name="randseed"></a>S_SAYI_ÜRET ([çekirdek])

0 ile 1 arasında rastgele bir değer döndürür.

**Bağımsız değişkenler**

Çekirdek değeri bir `Int32` . Çekirdek belirtilmemişse, SQL Server veritabanı altyapısı rastgele bir çekirdek değeri atar. Belirtilen bir çekirdek değeri için döndürülen sonuç her zaman aynıdır.

**Dönüş Değeri**

`Double`0 ile 1 arasında rastgele bir değer.

**Örnek**

`SqlServer.RAND()`
  
## <a name="roundnumeric_expression-lengthfunction"></a>ROUND (numeric_expression, Uzunluk [, işlev])

Belirtilen uzunluğa veya duyarlığa yuvarlanmış bir sayısal ifade döndürür.

**Bağımsız değişkenler**

|  |  |
|--|--|
|`numeric_expression`| `Int32`,, `Int64` `Double` Veya `Decimal` .
|`length`| `Int32`Bu, yuvarlanacak duyarlığı temsil eder `numeric_expression` . `length`Pozitif bir sayı olduğunda, `numeric_expression` tarafından belirtilen ondalık konum sayısına yuvarlanır `length` . `length`Negatif bir sayı olduğunda, `numeric_expression` ondalık noktanın sol tarafında tarafından belirtildiği gibi yuvarlanır `length` .|
|`function` | İsteğe bağlı. `Int32`Gerçekleştirilecek işlemin türünü temsil eden bir. İşlev atlandığında veya 0 değerine (varsayılan) sahip olduğunda, `numeric_expression` yuvarlanır. 0 dışında bir değer belirtildiğinde, `numeric_expression` atılır. |

**Dönüş Değeri**

Belirtilen değerinin `numeric_expression` belirtilen değeri `power_expression` .

**Örnek**

`SqlServer.ROUND(748.58, -3)`

## <a name="signexpression"></a>IŞARETI (ifade)

Belirtilen ifadenin pozitif (+ 1), sıfır (0) veya negatif (-1) işaretini döndürür.

**Bağımsız değişkenler**

`expression`: `Int32` , `Int64` , `Double` , veya `Decimal`

**Dönüş Değeri**

`Int32`,, `Int64` `Double` Veya `Decimal` .

**Örnek**

`SqlServer.SIGN(-10)`

## <a name="sinexpression"></a>SIN (ifade)

Radyan cinsinden belirtilen açının trigonometrik sinüsünü hesaplar ve bir `Double` ifade döndürür.

**Bağımsız değişkenler**

`expression`: A `Double` .

**Dönüş Değeri**

Bir `Double`.

**Örnek**`SqlServer.SIN(20)`

## <a name="sqrtexpression"></a>SQRT (ifade)

Belirtilen ifadenin kare kökünü döndürür.

**Bağımsız değişkenler**

`expression`: A `Double` .

**Dönüş Değeri**

Bir `Double`.

**Örnek**`SqlServer.SQRT(3600)`

## <a name="squareexpression"></a>KARE (ifade)

Belirtilen ifadenin karesini döndürür.

**Bağımsız değişkenler**

`expression`: A `Double` .

**Dönüş Değeri**

Bir `Double`.

**Örnek**

`SqlServer.SQUARE(25)`

## <a name="tanexpression"></a>TAN (ifade)

Belirtilen bir ifadenin tanjantını hesaplar.

**Bağımsız değişkenler**

`expression`: `Double`

**Dönüş Değeri**

`Double`

**Örnek**

`SqlServer.TAN(45.0)`
  
## <a name="see-also"></a>Ayrıca bkz.

- [Matematik Işlevleri (Transact-SQL)](/sql/t-sql/functions/mathematical-functions-transact-sql)
- [Entity Framework için SqlClient İşlevleri](sqlclient-for-ef-functions.md)
