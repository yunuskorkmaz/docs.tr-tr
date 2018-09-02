---
title: Matematik işlevleri
ms.date: 03/30/2017
ms.assetid: b040c7cb-156d-40f2-9152-61065b18148c
ms.openlocfilehash: e6c58d781d7138f8295f2d0a2f0db110ad4b1dd6
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43456457"
---
# <a name="mathematical-functions"></a>Matematik işlevleri

SQL Server (SqlClient) için .NET Framework veri sağlayıcısı, bağımsız değişken olarak sağlanır ve bir sayısal değer sonuç giriş değerleri üzerinde hesaplamalar matematik işlevleri sağlar. Bu işlevler SqlServer ad alanında SqlClient kullanırken, kullanılabilir bağımlıdır. Bir sağlayıcının ad özelliği, hangi önekin türleri ve işlevleri gibi belirli yapılar için bu sağlayıcı tarafından kullanılan bulmak Entity Framework sağlar. Aşağıdaki tabloda SqlClient matematik işlevleri açıklanmaktadır.  
  
## <a name="absexpression"></a>Abs(Expression)

Mutlak değeri işlevi görür.

**Bağımsız Değişkenler**

`expression`: Bir `Int32`, `Int64`, `Double`, veya `Decimal`.

**Dönüş değeri**

Belirtilen ifadenin mutlak değeri.

**Örnek**

`SqlServer.ABS(-2)`

## <a name="acosexpression"></a>ACOS(Expression)

Belirtilen ifade arkkosinüsünü değerini döndürür.

**Bağımsız Değişkenler**

`expression`: BİR `Double`.

**Dönüş değeri**

A `Double`.

**Örnek**

`SqlServer.ACOS(.9)`

## <a name="asinexpression"></a>ASIN(Expression)

Belirtilen ifade arksinüsünü değerini döndürür.

**Bağımsız Değişkenler**

`expression`: BİR `Double`.

**Dönüş değeri**

A `Double`.

**Örnek**

`SqlServer.ASIN(.9)`

## <a name="atanexpression"></a>ATAN(Expression)

Belirtilen sayısal ifade arktanjantını değerini döndürür.

**Bağımsız Değişkenler**

`expression`: BİR `Double`.

**Dönüş değeri**

A `Double`.

**Örnek**

`SqlServer.ATAN(9)`

## <a name="atn2expression-expression"></a>ATN2(Expression, Expression)

Radyan cinsinden tanjantı iki belirli sayısal ifade olan açıyı döndürür.

**Bağımsız Değişkenler**

`expression`: BİR `Double`.

**Dönüş değeri**

A `Double`.

**Örnek**

`SqlServer.ATN2(9, 8)`
 
## <a name="ceilingexpression"></a>CEILING(Expression)

Belirtilen ifade değerinden büyük veya ona eşit olan en küçük tamsayı dönüştürür.

**Bağımsız Değişkenler**

`expression`: Bir `Int32`, `Int64`, `Double`, veya `Decimal`.

**Dönüş değeri**

Bir `Int32`, `Int64`, `Double`, veya `Decimal`.

**Örnek** 

[!code-csharp[DP EntityServices Concepts#SQLSERVER_CEILING](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_ceiling)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_CEILING](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_ceiling)]

## <a name="cosexpression"></a>COS(Expression)

Trigonometrik radyan cinsinden belirtilen bir açının kosinüsünü hesaplar. 

**Bağımsız Değişkenler** 

`expression`: BİR `Double`. 

**Dönüş değeri** 

A `Double`. 

**Örnek** 

`SqlServer.COS(45)`

## <a name="cotexpression"></a>COT(Expression)

Trigonometrik radyan cinsinden belirtilen bir açının kotanjantını hesaplar. 

**Bağımsız Değişkenler** 

`expression`: BİR `Double`. 

**Dönüş değeri** 

A `Double`. 

**Örnek** 

`SqlServer.COT(60)`
  
## <a name="degreesradians"></a>DEGREES(radians)

Karşılık gelen açıyı derece cinsinden döndürür. 

**Bağımsız Değişkenler** 

`expression`: Bir `Int32`, `Int64`, `Double`, veya `Decimal`. 

**Dönüş değeri** 

Bir `Int32`, `Int64`, `Double`, veya `Decimal`. 

**Örnek** 

`SqlServer.DEGREES(3.1)`

## <a name="expexpression"></a>EXP(Expression)

Belirtilen bir sayısal ifade üs değerini hesaplar. 

**Bağımsız Değişkenler** 

`expression`: BİR `Double`. 

**Dönüş değeri** 

A `Double`. 

**Örnek** `SqlServer.EXP(1)`

## <a name="floorexpression"></a>FLOOR(Expression)

Belirtilen ifadedeki en büyük tamsayı daha az veya eşit ona dönüştürür. 

**Bağımsız Değişkenler** 

`expression`: BİR `Double`. 

**Dönüş değeri** 

A `Double`. 

**Örnek** 

[!code-csharp[DP EntityServices Concepts#SQLSERVER_FLOOR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_floor)] 
[!code-sql[DP EntityServices Concepts#SQLSERVER_FLOOR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_floor)]

## <a name="logexpression"></a>LOG(Expression)

Belirtilen doğal logaritmasını hesaplar `float` ifade. 

**Bağımsız Değişkenler** 

`expression`: BİR `Double`. 

**Dönüş değeri** 

A `Double`. 

**Örnek** 

`SqlServer.LOG(100)`

## <a name="log10expression"></a>Log10(Expression)

Belirtilen 10 tabanında logaritmasını döndürür `Double` ifade. 

**Bağımsız Değişkenler** 

`expression`: BİR `Double`. 

**Dönüş değeri** 

A `Double`. 

**Örnek** 

`SqlServer.LOG10(100)`

## <a name="pi"></a>PI()

Sabit değer pi'nin döndürür bir `Double`. 

**Dönüş değeri** 

A `Double`. 

**Örnek** 

`SqlServer.PI()`

## <a name="powernumericexpression-powerexpression"></a>GÜÇ (numeric_expression, power_expression)

Belirtilen bir ifadenin belirtilen bir kuvvete değerini hesaplar.

**Bağımsız Değişkenler** 

|  |  |
|--|--|
|`numeric_expression`| Bir `Int32`, `Int64`, `Double`, veya `Decimal`.|
|`power_expression`| A `Double` yükseltmek istediğiniz gücünü temsil eden `numeric_expression`.| 

**Dönüş değeri** 

Belirtilen değeri `numeric_expression` belirtilen `power_expression`. 

**Örnek** 

`SqlServer.POWER(2,7)`

## <a name="radiansexpression"></a>RADIANS(Expression)

Dereceyi radyana dönüştürür. 

**Bağımsız Değişkenler** 

`expression`: Bir `Int32`, `Int64`, `Double`, veya `Decimal`. 

**Dönüş değeri** 

Bir `Int32`, `Int64`, `Double`, veya `Decimal`. 

**Örnek** 

`SqlServer.RADIANS(360.0)`

## <a name="randseed"></a>RAND([seed])

0 ile 1 arasında rastgele bir değer döndürür. 

**Bağımsız Değişkenler** 

Çekirdek değeri olarak bir `Int32`. Çekirdek değer belirtilmemişse, SQL Server veritabanı altyapısı rastgele bir tohum değeri atar. Belirtilen çekirdek değeri için döndürülen sonuç her zaman aynıdır.

**Dönüş değeri** 

Rastgele bir sıra `Double` 0 ile 1 arasında bir değer. 

**Örnek** 

`SqlServer.RAND()`
  
## <a name="roundnumericexpression-lengthfunction"></a>ROUND(numeric_expression, length[,Function])

Belirtilen uzunluk veya duyarlık yuvarlak bir sayısal ifade döndürür. 

**Bağımsız Değişkenler** 

|  |  |
|--|--|
|`numeric_expression`| Bir `Int32`, `Int64`, `Double`, veya `Decimal`. 
|`length`| Bir `Int32` duyarlık olduğu temsil eden `numeric_expression` yuvarlanmasını sağlamaktır. Zaman `length` pozitif bir sayı `numeric_expression` tarafından belirtilen ondalık basamak sayısına yuvarlanır `length`. Zaman `length` negatif bir sayı `numeric_expression` belirtildiği gibi Ondalık ayırıcının sol tarafındaki yuvarlanır `length`.|
|`function` | İsteğe bağlı. Bir `Int32` gerçekleştirilecek işlem türünü temsil eder. İşlev atlanırsa veya 0 (varsayılan), değeri `numeric_expression` yuvarlanır. 0 dışında bir değer belirtilirse, `numeric_expression` kesilir. |

**Dönüş değeri** 

Belirtilen değeri `numeric_expression` belirtilen `power_expression`.

**Örnek** 

`SqlServer.ROUND(748.58, -3)`

## <a name="signexpression"></a>SIGN(Expression) 

(+ 1) pozitif, sıfır (0) veya eksi (-1) belirtilen ifade döndürür. 

**Bağımsız Değişkenler** 

`expression`: `Int32`, `Int64`, `Double`, veya `Decimal` 

**Dönüş değeri** 

Bir `Int32`, `Int64`, `Double`, veya `Decimal`. 

**Örnek** 

`SqlServer.SIGN(-10)`

## <a name="sinexpression"></a>SIN(Expression)

Trigonometrik radyan cinsinden belirtilen bir açının sinüsünü hesaplar ve döndürür bir `Double` ifade. 

**Bağımsız Değişkenler** 

`expression`: BİR `Double`. 

**Dönüş değeri** 

A `Double`. 

**Örnek** `SqlServer.SIN(20)`

## <a name="sqrtexpression"></a>Sqrt(Expression)

Belirtilen ifadenin kare kökünü döndürür. 

**Bağımsız Değişkenler** 

`expression`: BİR `Double`. 

**Dönüş değeri** 

A `Double`. 

**Örnek** `SqlServer.SQRT(3600)`

## <a name="squareexpression"></a>SQUARE(Expression)

Belirtilen ifade karesini döndürür. 

**Bağımsız Değişkenler** 

`expression`: BİR `Double`. 

**Dönüş değeri** 

A `Double`. 

**Örnek** 

`SqlServer.SQUARE(25)`

## <a name="tanexpression"></a>TAN(Expression)

Belirtilen bir ifade tanjantını hesaplar.

**Bağımsız Değişkenler** 

`expression`: `Double` 

**Dönüş değeri** 

`Double` 

**Örnek** 

`SqlServer.TAN(45.0)`
  
## <a name="see-also"></a>Ayrıca bkz.

SqlClient destekleyen matematiksel işlevler hakkında daha fazla bilgi için SqlClient sağlayıcı bildiriminde belirtilen SQL Server sürümü için belgelere bakın:  
  
**SQL Server 2005:** [matematik işlevleri (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms177516(v=sql.90))  
**SQL Server 2008:** [matematik işlevleri (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms177516(v=sql.100))  
**SQL Server 2012 ve sonraki sürümler:** [matematik işlevleri (Transact-SQL)](/sql/t-sql/functions/mathematical-functions-transact-sql?view=sql-server-2017)   

 [Entity Framework için SqlClient İşlevleri](sqlclient-for-ef-functions.md)
