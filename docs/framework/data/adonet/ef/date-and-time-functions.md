---
title: "Tarih ve saat işlevleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 971762d0-663b-4b64-8c61-352a8e6d3949
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: c3d47b4ced66a8826424cdbb75e5694fadb9038d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="date-and-time-functions"></a>Tarih ve saat işlevleri
SQL Server (SqlClient) için .NET Framework veri sağlayıcısı işlemleri yapmanız tarih ve saat işlevleri sağlayan bir `System.DateTime` giriş değeri ve dönüş bir `string`, sayısal ve veya `System.DateTime` sonuç değeri. Bu SqlServer ad alanında SqlClient kullandığınızda kullanılabilir olduğu işlevlerdir. Bir sağlayıcının ad özelliği, hangi önekin türler ve işlevler gibi belirli yapıları için bu sağlayıcı tarafından kullanılan bulmak Entity Framework sağlar. Aşağıdaki tabloda SqlClient tarih ve saat işlevleri gösterir.  
  
|İşlev|Açıklama|  
|--------------|-----------------|  
|`DATEADD(` `datepart`, `number`, `date``)`|Yeni bir döndürür `DateTime` belirtilen tarihe bir aralık eklenmesine bağlı dayalı değeri.<br /><br /> **Bağımsız değişkenler**<br /><br /> `datepart`: Bir `String` yeni bir değer döndürüleceğini tarih bölümünü temsil eder.<br /><br /> `number``Int32`, `Int64`, `Decimal`, Veya `Double` kullanılan değeri artırmak `datepart`.<br /><br /> `date:`Döndüren bir ifadeye bir `DateTime`, veya `DateTimeOffset`, veya `Time` [0-7], duyarlık ile = ya da tarih biçiminde bir karakter dizesi.<br /><br /> **Dönüş değeri**<br /><br /> Yeni bir `DateTime`, veya `DateTimeOffset`, veya `Time` duyarlık değerle = [0-7].<br /><br /> **Örnek**<br /><br /> `SqlServer.DATEADD('day', 22, cast('6/9/2006' as DateTime))`|  
|`DATEDIFF(` `datepart`, `startdate`, `enddate``)`|Belirtilen iki tarih arasında geçilen tarih ve saat sınırlarının sayısını döndürür.<br /><br /> **Bağımsız değişkenler**<br /><br /> `datepart`: Bir `String` farkını hesaplamak için tarih bölümünü temsil eder.<br /><br /> `startdate`: Döndüren bir ifadeye hesaplama için başlangıç tarihi olan bir `DateTime`, veya `DateTimeOffset`, veya `Time` duyarlık değerle = [0-7], ya da tarih biçiminde bir karakter dizesi.<br /><br /> `enddate:`Hesaplama için bir bitiş tarihi döndüren bir ifadedir bir `DateTime`, veya `DateTimeOffset`, veya `Time` duyarlık değerle = [0-7], ya da tarih biçiminde bir karakter dizesi.<br /><br /> **Dönüş değeri**<br /><br /> Bir `Int32`.<br /><br /> **Örnek**<br /><br /> `SqlServer.DATEDIFF('day', cast('6/9/2006' as DateTime),`<br /><br /> `cast('6/20/2006' as DateTime))`|  
|`DATENAME(` `datepart`, `date``)`|Belirtilen Date belirtilen datepart temsil eden bir karakter dizesi döndürür.<br /><br /> **Bağımsız değişkenler**<br /><br /> `datepart`: Bir `String` yeni bir değer döndürüleceğini tarih bölümünü temsil eder.<br /><br /> `date`: Döndürür bir ifade bir `DateTime,` veya `DateTimeOffset`, veya `Time` duyarlık değerle = [0-7], ya da tarih biçiminde bir karakter dizesi.<br /><br /> **Dönüş değeri**<br /><br /> Belirtilen Date belirtilen datepart temsil eden karakter dizesi.<br /><br /> **Örnek**<br /><br /> `SqlServer.DATENAME('year', cast('6/9/2006' as DateTime))`|  
|`DATEPART(` `datepart`, `date``)`|Belirtilen Date belirtilen datepart temsil eden bir tamsayı döndürür.<br /><br /> **Bağımsız değişkenler**<br /><br /> `datepart`: Bir `String` yeni bir değer döndürüleceğini tarih bölümünü temsil eder.<br /><br /> `date`: Döndürür bir ifade bir `DateTime,` veya `DateTimeOffset,` veya `Time` duyarlık değerle = [0-7], ya da tarih biçiminde bir karakter dizesi.<br /><br /> **Dönüş değeri**<br /><br /> Belirtilen Date belirtilen datepart olarak bir `Int32`.<br /><br /> **Örnek**<br /><br /> `SqlServer.DATEPART('year', cast('6/9/2006' as DateTime))`|  
|`DAY(` `date` `)`|Rreturns bir tamsayı olarak belirtilen tarihin gün.<br /><br /> **Bağımsız değişkenler**<br /><br /> `date`: Bir ifade türü `DateTime` veya `DateTimeOffset` ile duyarlık = 0-7.<br /><br /> **Dönüş değeri**<br /><br /> Belirtilen tarih olarak gününü bir `Int32`.<br /><br /> **Örnek**<br /><br /> `SqlServer.DAY(cast('6/9/2006' as DateTime))`|  
|`GETDATE()`|Geçerli tarih ve saat datetime değerleri için SQL Server dahili biçiminde üretir.<br /><br /> **Dönüş değeri**<br /><br /> Geçerli sistem tarihi ve saati olarak bir `DateTime` 3 kesinliğini ile.<br /><br /> **Örnek**<br /><br /> `SqlServer.GETDATE()`|  
|`GETUTCDATE()`|Tarih saat değeri UTC (Eşgüdümlü Evrensel Saat veya Greenwich saati) biçiminde üretir.<br /><br /> **Dönüş değeri**<br /><br /> `DateTime` Değer kesinliği UTC biçiminde 3 ile.<br /><br /> **Örnek**<br /><br /> `SqlServer.GETUTCDATE()`|  
|`MONTH(` `date` `)`|Bir tamsayı olarak belirtilen tarihin ayı verir.<br /><br /> **Bağımsız değişkenler**<br /><br /> `date`: Bir ifade türü `DateTime` veya `DateTimeOffset` ile duyarlık = 0-7.<br /><br /> **Dönüş değeri**<br /><br /> Belirtilen tarihi olarak ayın bir `Int32`.<br /><br /> **Örnek**<br /><br /> `SqlServer.MONTH(cast('6/9/2006' as DateTime))`|  
|`YEAR(` `date` `)`|Yıl bir tamsayı olarak belirtilen tarih değerini döndürür.<br /><br /> **Bağımsız değişkenler**<br /><br /> `date`: Bir ifade türü `DateTime` veya `DateTimeOffset` ile duyarlık = 0-7.<br /><br /> **Dönüş değeri**<br /><br /> Belirtilen tarih olarak yılın bir `Int32`.<br /><br /> **Örnek**<br /><br /> `SqlServer.YEAR(cast('6/9/2006' as DateTime))`|  
|`SYSDATETIME()`|Döndürür bir `DateTime` değer kesinliği 7 ile.<br /><br /> **Dönüş değeri**<br /><br /> A `DateTime` değer kesinliği 7 ile.<br /><br /> **Örnek**<br /><br /> `SqlServer.SYSDATETIME()`|  
|`SYSUTCDATE()`|Tarih saat değeri UTC (Eşgüdümlü Evrensel Saat veya Greenwich saati) biçiminde üretir.<br /><br /> **Dönüş değeri**<br /><br /> `DateTime` Duyarlık değerle = 7 UTC biçiminde.<br /><br /> **Örnek**<br /><br /> `SqlServer.SYSUTCDATE()`|  
|`SYSDATETIMEOFFSET()`|Döndürür bir `DateTimeOffset` 7 kesinliğini ile.<br /><br /> **Dönüş değeri**<br /><br /> A `DateTimeOffset` UTC biçiminde 7 duyarlılık değeri.<br /><br /> **Örnek**<br /><br /> `SqlServer.SYSDATETIMEOFFSET()`|  
  
 SqlClient destekleyen tarih ve saat işlevleri hakkında daha fazla bilgi için SqlClient sağlayıcısı bildiriminde belirtilen SQL Server sürümü için belgelere bakın:  
  
|SQL Server 2000|SQL Server 2005|SQL Server 2008|  
|---------------------|---------------------|---------------------|  
|[Tarih ve saat işlevlerini (Transact-SQL)](http://go.microsoft.com/fwlink/?LinkId=115908)|[Tarih ve saat işlevlerini (Transact-SQL)](http://go.microsoft.com/fwlink/?LinkId=115909)|[Tarih ve saat işlevlerini (Transact-SQL)](http://go.microsoft.com/fwlink/?LinkId=98360)|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Entity Framework işlevleri için SqlClient](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md)
