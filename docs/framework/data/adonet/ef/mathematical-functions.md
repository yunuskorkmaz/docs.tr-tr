---
title: Matematik İşlevleri
ms.date: 03/30/2017
ms.assetid: b040c7cb-156d-40f2-9152-61065b18148c
ms.openlocfilehash: 5e5658e28c7d806f7fd38f941bfa7254e7806e11
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71182489"
---
# <a name="mathematical-functions"></a>Matematik İşlevleri

SQL Server (SqlClient) için .NET Framework Veri Sağlayıcısı, bağımsız değişken olarak sağlanan giriş değerlerinde hesaplamalar gerçekleştiren ve sayısal bir değer sonucu döndüren matematik işlevleri sağlar. Bu işlevler, SqlClient kullandığınızda kullanılabilir olan SqlServer ad alanıdır. Bir sağlayıcının ad alanı özelliği Entity Framework, bu sağlayıcı tarafından türler ve işlevler gibi belirli yapılar için kullanılan öneki bulmasını sağlar. Aşağıdaki tabloda, SqlClient matematik işlevleri açıklanmaktadır.  
  
## <a name="absexpression"></a>ABS (ifade)

Mutlak değer işlevini gerçekleştirir.

**Bağımsız Değişkenler**

`expression`: `Int32` ,`Int64`, Veya .`Decimal` `Double`

**Dönüş değeri**

Belirtilen ifadenin mutlak değeri.

**Örnek**

`SqlServer.ABS(-2)`

## <a name="acosexpression"></a>ACOS (ifade)

Belirtilen ifadenin Arkkosinüs değerini döndürür.

**Bağımsız Değişkenler**

`expression`: A `Double`.

**Dönüş değeri**

A `Double`.

**Örnek**

`SqlServer.ACOS(.9)`

## <a name="asinexpression"></a>ASIN (ifade)

Belirtilen ifadenin arksinüs değerini döndürür.

**Bağımsız Değişkenler**

`expression`: A `Double`.

**Dönüş değeri**

A `Double`.

**Örnek**

`SqlServer.ASIN(.9)`

## <a name="atanexpression"></a>ATAN (ifade)

Belirtilen sayısal ifadenin arktanjant değerini döndürür.

**Bağımsız Değişkenler**

`expression`: A `Double`.

**Dönüş değeri**

A `Double`.

**Örnek**

`SqlServer.ATAN(9)`

## <a name="atn2expression-expression"></a>ATN2 (ifade, ifade)

Tanjantı belirtilen iki sayısal ifade arasında olan radyan cinsinden açıyı döndürür.

**Bağımsız Değişkenler**

`expression`: A `Double`.

**Dönüş değeri**

A `Double`.

**Örnek**

`SqlServer.ATN2(9, 8)`
 
## <a name="ceilingexpression"></a>TAVAN (ifade)

Belirtilen ifadeyi, bu değerden büyük veya ona eşit en küçük tamsayıya dönüştürür.

**Bağımsız Değişkenler**

`expression`: `Int32` ,`Int64`, Veya .`Decimal` `Double`

**Dönüş değeri**

`Int32` ,`Int64`, Veya .`Decimal` `Double`

**Örnek** 

[!code-csharp[DP EntityServices Concepts#SQLSERVER_CEILING](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_ceiling)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_CEILING](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_ceiling)]

## <a name="cosexpression"></a>COS (ifade)

Radyan cinsinden belirtilen açının trigonometrik kosinüsünü hesaplar. 

**Bağımsız Değişkenler** 

`expression`: A `Double`. 

**Dönüş değeri** 

A `Double`. 

**Örnek** 

`SqlServer.COS(45)`

## <a name="cotexpression"></a>COT (ifade)

Radyan cinsinden belirtilen açıdaki trigonometrik kovaryansı hesaplar. 

**Bağımsız Değişkenler** 

`expression`: A `Double`. 

**Dönüş değeri** 

A `Double`. 

**Örnek** 

`SqlServer.COT(60)`
  
## <a name="degreesradians"></a>DERECE (radyan)

Karşılık gelen açıyı derece cinsinden döndürür. 

**Bağımsız Değişkenler** 

`expression`: `Int32` ,`Int64`, Veya .`Decimal` `Double` 

**Dönüş değeri** 

`Int32` ,`Int64`, Veya .`Decimal` `Double` 

**Örnek** 

`SqlServer.DEGREES(3.1)`

## <a name="expexpression"></a>EXP (ifade)

Belirtilen bir sayısal ifadenin üstel değerini hesaplar. 

**Bağımsız Değişkenler** 

`expression`: A `Double`. 

**Dönüş değeri** 

A `Double`. 

**Örnek**`SqlServer.EXP(1)`

## <a name="floorexpression"></a>FLOOR (ifade)

Belirtilen ifadeyi ona eşit veya ondan küçük olan en büyük tamsayıya dönüştürür. 

**Bağımsız Değişkenler** 

`expression`: A `Double`. 

**Dönüş değeri** 

A `Double`. 

**Örnek** 

[!code-csharp[DP EntityServices Concepts#SQLSERVER_FLOOR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_floor)] 
[!code-sql[DP EntityServices Concepts#SQLSERVER_FLOOR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_floor)]

## <a name="logexpression"></a>GÜNLÜK (ifade)

Belirtilen `float` ifadenin doğal logaritmasını hesaplar. 

**Bağımsız Değişkenler** 

`expression`: A `Double`. 

**Dönüş değeri** 

A `Double`. 

**Örnek** 

`SqlServer.LOG(100)`

## <a name="log10expression"></a>LOG10 (ifade)

Belirtilen `Double` ifadenin 10 tabanında logaritmasını döndürür. 

**Bağımsız Değişkenler** 

`expression`: A `Double`. 

**Dönüş değeri** 

A `Double`. 

**Örnek** 

`SqlServer.LOG10(100)`

## <a name="pi"></a>PI ()

Pi değerinin sabit değerini bir `Double`olarak döndürür. 

**Dönüş değeri** 

A `Double`. 

**Örnek** 

`SqlServer.PI()`

## <a name="powernumeric_expression-power_expression"></a>Güç (numeric_expression, power_expression)

Belirtilen bir ifadenin değerini belirtilen bir kuvvet olarak hesaplar.

**Bağımsız Değişkenler** 

|  |  |
|--|--|
|`numeric_expression`| `Int32` ,`Int64`, Veya .`Decimal` `Double`|
|`power_expression`| `Double` Öğesini ,`numeric_expression`öğesini yükseltmek için gereken kuvveti temsil eder.| 

**Dönüş değeri** 

Belirtilen değerinin belirtilen `numeric_expression` `power_expression`değeri. 

**Örnek** 

`SqlServer.POWER(2,7)`

## <a name="radiansexpression"></a>RADYAN (ifade)

Dereceyi radyana dönüştürür. 

**Bağımsız Değişkenler** 

`expression`: `Int32` ,`Int64`, Veya .`Decimal` `Double` 

**Dönüş değeri** 

`Int32` ,`Int64`, Veya .`Decimal` `Double` 

**Örnek** 

`SqlServer.RADIANS(360.0)`

## <a name="randseed"></a>S_SAYI_ÜRET ([çekirdek])

0 ile 1 arasında rastgele bir değer döndürür. 

**Bağımsız Değişkenler** 

Çekirdek değeri bir `Int32`. Çekirdek belirtilmemişse, SQL Server veritabanı altyapısı rastgele bir çekirdek değeri atar. Belirtilen bir çekirdek değeri için döndürülen sonuç her zaman aynıdır.

**Dönüş değeri** 

0 ile `Double` 1 arasında rastgele bir değer. 

**Örnek** 

`SqlServer.RAND()`
  
## <a name="roundnumeric_expression-lengthfunction"></a>ROUND (numeric_expression, length [, Function])

Belirtilen uzunluğa veya duyarlığa yuvarlanmış bir sayısal ifade döndürür. 

**Bağımsız Değişkenler** 

|  |  |
|--|--|
|`numeric_expression`| `Int32` ,`Int64`, Veya .`Decimal` `Double` 
|`length`| Bu, yuvarlanacak duyarlığı `numeric_expression` temsil eder. `Int32` Pozitif `length` bir sayı olduğunda, `numeric_expression` tarafından `length`belirtilen ondalık konum sayısına yuvarlanır. Negatif `length` bir sayı olduğunda, `numeric_expression` ondalık noktanın sol tarafında tarafından `length`belirtildiği gibi yuvarlanır.|
|`function` | İsteğe bağlı. Gerçekleştirilecek `Int32` işlemin türünü temsil eden bir. İşlev atlandığında veya 0 değerine (varsayılan) sahip olduğunda, `numeric_expression` yuvarlanır. 0 dışında bir değer belirtildiğinde, `numeric_expression` atılır. |

**Dönüş değeri** 

Belirtilen değerinin belirtilen `numeric_expression` `power_expression`değeri.

**Örnek** 

`SqlServer.ROUND(748.58, -3)`

## <a name="signexpression"></a>IŞARETI (ifade) 

Belirtilen ifadenin pozitif (+ 1), sıfır (0) veya negatif (-1) işaretini döndürür. 

**Bağımsız Değişkenler** 

`expression`: `Int32`, `Int64` ,`Double`, veya`Decimal` 

**Dönüş değeri** 

`Int32` ,`Int64`, Veya .`Decimal` `Double` 

**Örnek** 

`SqlServer.SIGN(-10)`

## <a name="sinexpression"></a>SIN (ifade)

Radyan cinsinden belirtilen açının trigonometrik sinüsünü hesaplar ve bir `Double` ifade döndürür. 

**Bağımsız Değişkenler** 

`expression`: A `Double`. 

**Dönüş değeri** 

A `Double`. 

**Örnek**`SqlServer.SIN(20)`

## <a name="sqrtexpression"></a>SQRT (ifade)

Belirtilen ifadenin kare kökünü döndürür. 

**Bağımsız Değişkenler** 

`expression`: A `Double`. 

**Dönüş değeri** 

A `Double`. 

**Örnek**`SqlServer.SQRT(3600)`

## <a name="squareexpression"></a>KARE (ifade)

Belirtilen ifadenin karesini döndürür. 

**Bağımsız Değişkenler** 

`expression`: A `Double`. 

**Dönüş değeri** 

A `Double`. 

**Örnek** 

`SqlServer.SQUARE(25)`

## <a name="tanexpression"></a>TAN (ifade)

Belirtilen bir ifadenin tanjantını hesaplar.

**Bağımsız Değişkenler** 

`expression`: `Double` 

**Dönüş değeri** 

`Double` 

**Örnek** 

`SqlServer.TAN(45.0)`
  
## <a name="see-also"></a>Ayrıca bkz.

SqlClient tarafından desteklenen matematik işlevleri hakkında daha fazla bilgi için, SqlClient sağlayıcısı bildiriminde belirttiğiniz SQL Server sürümü için belgelere bakın:

- **SQL Server 2005:** [Matematik Işlevleri (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms177516(v=sql.90))
- **SQL Server 2008:** [Matematik Işlevleri (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms177516(v=sql.100))
- **SQL Server 2012 ve üzeri:** [Matematik Işlevleri (Transact-SQL)](/sql/t-sql/functions/mathematical-functions-transact-sql)

- [Entity Framework için SqlClient İşlevleri](sqlclient-for-ef-functions.md)
