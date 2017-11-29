---
title: "Matematik işlevleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b040c7cb-156d-40f2-9152-61065b18148c
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 8390f1e1822d7581ab0352a8c81acbc7ce545507
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="mathematical-functions"></a>Matematik işlevleri
SQL Server (SqlClient) için .NET Framework veri sağlayıcısı bağımsız değişken olarak sağlanır ve bir sayısal değer sonuç giriş değerleri hesaplamalar matematik işlevleri sağlar. Bu SqlServer ad alanında SqlClient kullandığınızda kullanılabilir olduğu işlevlerdir. Bir sağlayıcının ad özelliği, hangi önekin türler ve işlevler gibi belirli yapıları için bu sağlayıcı tarafından kullanılan bulmak Entity Framework sağlar. Aşağıdaki tabloda SqlClient matematik işlevleri açıklanmaktadır.  
  
|İşlev|Açıklama|  
|--------------|-----------------|  
|`ABS(` `expression` `)`|Mutlak değerini işlevi gerçekleştirir.<br /><br /> **Bağımsız değişkenler**<br /><br /> `expression`: Bir `Int32`, `Int64`, `Double`, veya `Decimal`.<br /><br /> **Dönüş değeri**<br /><br /> Belirtilen ifade mutlak değeri.<br /><br /> **Örnek**<br /><br /> `SqlServer.ABS(-2)`|  
|`ACOS(` `expression` `)`|Belirtilen ifade arkkosinüsünü değerini döndürür.<br /><br /> **Bağımsız değişkenler**<br /><br /> `expression`: BİR `Double`.<br /><br /> **Dönüş değeri**<br /><br /> A `Double`.<br /><br /> **Örnek**<br /><br /> `SqlServer.ACOS(.9)`|  
|`ASIN(` `expression` `)`|Belirtilen ifade arksinüsünü değerini döndürür.<br /><br /> **Bağımsız değişkenler**<br /><br /> `expression`: BİR `Double`.<br /><br /> **Dönüş değeri**<br /><br /> A `Double`.<br /><br /> **Örnek**<br /><br /> `SqlServer.ASIN(.9)`|  
|`ATAN(` `expression` `)`|Belirtilen sayısal ifade arktanjantını değerini döndürür.<br /><br /> **Bağımsız değişkenler**<br /><br /> `expression`: BİR `Double`.<br /><br /> **Dönüş değeri**<br /><br /> A `Double`.<br /><br /> **Örnek**<br /><br /> `SqlServer.ATAN(9)`|  
|`ATN2(` `expression`, `expression``)`|Tanjantı arasında iki belirtilen sayısal ifadeye olduğu radyan cinsinden açı döndürür.<br /><br /> **Bağımsız değişkenler**<br /><br /> `expression`: BİR `Double`.<br /><br /> **Dönüş değeri**<br /><br /> A `Double`.<br /><br /> **Örnek**<br /><br /> `SqlServer.ATN2(9, 8)`|  
|`CEILING(` `expression` `)`|Belirtilen ifade büyük veya ona eşit en küçük tamsayı dönüştürür.<br /><br /> **Bağımsız değişkenler**<br /><br /> `expression`: Bir `Int32`, `Int64`, `Double`, veya `Decimal`.<br /><br /> **Dönüş değeri**<br /><br /> Bir `Int32`, `Int64`, `Double`, veya `Decimal`.<br /><br /> **Örnek**<br /><br /> [!code-csharp[DP EntityServices Concepts#SQLSERVER_CEILING](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_ceiling)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_CEILING](../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_ceiling)]|  
|`COS(` `expression` `)`|Trigonometrik radyan cinsinden belirtilen açının kosinüsünü hesaplar.<br /><br /> **Bağımsız değişkenler**<br /><br /> `expression`: BİR `Double`.<br /><br /> **Dönüş değeri**<br /><br /> A `Double`.<br /><br /> **Örnek**<br /><br /> `SqlServer.COS(45)`|  
|`COT(` `expression` `)`|Trigonometrik kotanjantını radyan cinsinden belirtilen açının hesaplar.<br /><br /> **Bağımsız değişkenler**<br /><br /> `expression`: BİR `Double`.<br /><br /> **Dönüş değeri**<br /><br /> A `Double`.<br /><br /> **Örnek**<br /><br /> `SqlServer.COT(60)`|  
|`DEGREES(` `radians` `)`|Karşılık gelen açıyı derece cinsinden döndürür.<br /><br /> **Bağımsız değişkenler**<br /><br /> `expression`: Bir `Int32`, `Int64`, `Double`, veya `Decimal`.<br /><br /> **Dönüş değeri**<br /><br /> Bir `Int32`, `Int64`, `Double`, veya `Decimal`.<br /><br /> **Örnek**<br /><br /> `SqlServer.DEGREES(3.1)`|  
|`EXP(` `expression` `)`|Belirtilen bir sayısal ifade üstel değerini hesaplar.<br /><br /> **Bağımsız değişkenler**<br /><br /> `expression`: BİR `Double`.<br /><br /> **Dönüş değeri**<br /><br /> A `Double`.<br /><br /> **Örnek**<br /><br /> `SqlServer.EXP(1)`|  
|`FLOOR(` `expression` `)`|Belirtilen ifadenin en büyük tamsayı daha az eşit veya onu dönüştürür.<br /><br /> **Bağımsız değişkenler**<br /><br /> `expression`: BİR `Double`.<br /><br /> **Dönüş değeri**<br /><br /> A `Double`.<br /><br /> **Örnek**<br /><br /> [!code-csharp[DP EntityServices Concepts#SQLSERVER_FLOOR](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_floor)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_FLOOR](../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_floor)]|  
|`LOG(` `expression` `)`|Belirtilen doğal logaritmasını hesaplar `float` ifade.<br /><br /> **Bağımsız değişkenler**<br /><br /> `expression`: BİR `Double`.<br /><br /> **Dönüş değeri**<br /><br /> A `Double`.<br /><br /> **Örnek**<br /><br /> `SqlServer.LOG(100)`|  
|`LOG10(` `expression` `)`|Belirtilen 10 tabanında logaritmasını döndürür `Double` ifade.<br /><br /> **Bağımsız değişkenler**<br /><br /> `expression`: BİR `Double`.<br /><br /> **Dönüş değeri**<br /><br /> A `Double`.<br /><br /> **Örnek**<br /><br /> `SqlServer.LOG10(100)`|  
|`PI()`|Sabit değer pi'nin döndürür bir `Double`.<br /><br /> **Dönüş değeri**<br /><br /> A `Double`.<br /><br /> **Örnek**<br /><br /> `SqlServer.PI()`|  
|`POWER(` `numeric_expression, power_expression` `)`|Belirtilen güç için belirtilen bir ifadenin değerini hesaplar.<br /><br /> **Bağımsız değişkenler**<br /><br /> `numeric_expression`: Bir `Int32`, `Int64`, `Double`, veya `Decimal`.<br /><br /> `power_expression`: Bir `Double` yükseltmek için gücünü temsil eden `numeric_expression`.<br /><br /> **Dönüş değeri**<br /><br /> Belirtilen değeri `numeric_expression` belirtilen `power_expression`.<br /><br /> **Örnek**<br /><br /> `SqlServer.POWER(2,7)`|  
|`RADIANS(` `expression` `)`|Derece radyan için dönüştürür.<br /><br /> **Bağımsız değişkenler**<br /><br /> `expression`: Bir `Int32`, `Int64`, `Double`, veya `Decimal`.<br /><br /> **Dönüş değeri**<br /><br /> Bir `Int32`, `Int64`,<br /><br /> `Double`, veya<br /><br /> `Decimal`.<br /><br /> **Örnek**<br /><br /> `SqlServer.RADIANS(360.0)`|  
|`RAND(`[Temel]`)`|0 ile 1 arasında rastgele bir değeri döndürür.<br /><br /> **Bağımsız değişkenler**<br /><br /> Retruns Çekirdek değer olarak bir `Int32`. Çekirdek değer belirtilmezse, SQL Server veritabanı altyapısı bir çekirdek değer rastgele atar. İçin belirtilen çekirdek değer, döndürülen sonuç her zaman aynıdır.<br /><br /> **Dönüş değeri**<br /><br /> Bir rastgele `Double` 0 ile 1 arasında bir değer.<br /><br /> **Örnek**<br /><br /> `SqlServer.RAND()`|  
|`ROUND(` `numeric_expression, length` [ ,`function` ]`)`|Belirtilen uzunluk veya duyarlık yuvarlanmasını sayısal bir ifade döndürür.<br /><br /> **Bağımsız değişkenler**<br /><br /> `numeric_expression`: Bir `Int32`, `Int64`, `Double`, veya `Decimal`.<br /><br /> `length`: Bir `Int32` duyarlık olduğu temsil eden `numeric_expression` yuvarlanmasını sağlamaktır. Zaman `length` pozitif bir sayı olan `numeric_expression` tarafından belirtilen ondalık konumlar sayısına yuvarlanır `length`. Zaman `length` negatif bir sayı `numeric_expression` tarafından belirtilen Ondalık ayırıcının sol tarafındaki yuvarlanır `length`.<br /><br /> `function`: (isteğe bağlı) bir `Int32` işlemi gerçekleştirmek için türünü temsil eder. İşlevi atlanmış veya 0 (varsayılan) değerine sahip olduğunda `numeric_expression` yuvarlanır. 0 dışında bir değer belirtilirse, `numeric_expression` kesilir.<br /><br /> **Dönüş değeri**<br /><br /> Belirtilen değeri `numeric_expression` belirtilen `power_expression`.<br /><br /> **Örnek**<br /><br /> `SqlServer.ROUND(748.58, -3)`|  
|`SIGN(` `expression` `)`|Artı (+ 1), sıfır (0) veya belirtilen ifadenin eksi (-1) işareti döndürür.<br /><br /> **Bağımsız değişkenler**<br /><br /> `expression`: `Int32`, `Int64`, `Double`, veya`Decimal`<br /><br /> **Dönüş değeri**<br /><br /> Bir `Int32`, `Int64`, `Double`, veya `Decimal`.<br /><br /> **Örnek**<br /><br /> `SqlServer.SIGN(-10)`|  
|`SIN(` `expression` `)`|Trigonometrik radyan cinsinden belirtilen açının sinüsünü hesaplar ve döndüren bir `Double` ifade.<br /><br /> **Bağımsız değişkenler**<br /><br /> `expression`: BİR `Double`.<br /><br /> **Dönüş değeri**<br /><br /> A `Double`.<br /><br /> **Örnek**<br /><br /> `SqlServer.SIN(20)`|  
|`SQRT(` `expression` `)`|Belirtilen ifade'nin kare kökünü döndürür.<br /><br /> **Bağımsız değişkenler**<br /><br /> `expression`: BİR `Double`.<br /><br /> **Dönüş değeri**<br /><br /> A `Double`.<br /><br /> **Örnek**<br /><br /> `SqlServer.SQRT(3600)`|  
|`SQUARE(` `expression` `)`|Belirtilen ifadenin kare döndürür.<br /><br /> **Bağımsız değişkenler**<br /><br /> `expression`: BİR `Double`.<br /><br /> **Dönüş değeri**<br /><br /> A `Double`.<br /><br /> **Örnek**<br /><br /> `SqlServer.SQUARE(25)`|  
|`TAN(` `expression` `)`|Belirtilen ifadeye tanjantını hesaplar.<br /><br /> **Bağımsız değişkenler**<br /><br /> `expression`: `Double`<br /><br /> **Dönüş değeri**<br /><br /> `Double`<br /><br /> **Örnek**<br /><br /> `SqlServer.TAN(45.0)`|  
  
 SqlClient destekleyen matematik işlevleri hakkında daha fazla bilgi için SqlClient sağlayıcısı bildiriminde belirtilen SQL Server sürümü için belgelere bakın:  
  
|SQL Server 2000|SQL Server 2005|SQL Server 2008|  
|---------------------|---------------------|---------------------|  
|[Matematik işlevleri (Transact-SQL)](http://go.microsoft.com/fwlink/?LinkId=115913)|[Matematik işlevleri (Transact-SQL)](http://go.microsoft.com/fwlink/?LinkId=115911)|[Matematik işlevleri (Transact-SQL)](http://go.microsoft.com/fwlink/?LinkId=115912)|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Entity Framework işlevleri için SqlClient](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md)
