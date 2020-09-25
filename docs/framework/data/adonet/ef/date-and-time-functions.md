---
title: Tarih ve Saat İşlevleri
ms.date: 03/30/2017
ms.assetid: 971762d0-663b-4b64-8c61-352a8e6d3949
ms.openlocfilehash: aa024ad748db26cb75111984abdb61fdbd538ef9
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198463"
---
# <a name="date-and-time-functions"></a>Tarih ve Saat İşlevleri

SQL Server (SqlClient) için .NET Framework Veri Sağlayıcısı, bir giriş değeri üzerinde işlemler gerçekleştiren `System.DateTime` ve bir `string` , sayısal ya da değer sonucu döndüren tarih ve saat işlevleri sağlar `System.DateTime` . Bu işlevler, SqlClient kullandığınızda kullanılabilir olan SqlServer ad alanıdır. Bir sağlayıcının ad alanı özelliği Entity Framework, bu sağlayıcı tarafından türler ve işlevler gibi belirli yapılar için kullanılan öneki bulmasını sağlar. Aşağıdaki tabloda, SqlClient tarih ve saat işlevleri gösterilmektedir.  
  
|İşlev|Açıklama|  
|--------------|-----------------|  
|`DATEADD(datepart, number, date)`|`DateTime`Belirtilen tarihe bir Aralık eklemeye dayalı yeni bir değer döndürür.<br /><br /> **Arguments**<br /><br /> `datepart`: `String` Yeni bir değer döndürmek için tarihin parçasını temsil eden bir.<br /><br /> `number`: `Int32` `Int64` `Decimal` `Double` Artırmak için kullanılan,, veya değeri `datepart` .<br /><br /> `date:` Bir `DateTime` , 0-7 veya veya bir `DateTimeOffset` `Time` tarih biçiminde karakter dizesi döndüren bir ifade.<br /><br /> **Dönüş Değeri**<br /><br /> `DateTime` `DateTimeOffset` `Time` Kesinlik = [0-7] ile yeni bir veya veya değeri.<br /><br /> **Örnek**<br /><br /> `SqlServer.DATEADD('day', 22, cast('6/9/2006' as DateTime))`|  
|`DATEDIFF(datepart,startdate,enddate)`|Belirtilen iki tarih arasında çapraz tarih ve saat sınırları sayısını döndürür.<br /><br /> **Arguments**<br /><br /> `datepart`: `String` Farkı hesaplamak için tarihin parçasını temsil eder.<br /><br /> `startdate`: Hesaplama için başlangıç tarihi `DateTime` `DateTimeOffset` `Time` duyarlık = [0-7] veya tarih biçimindeki bir karakter dizesi içeren bir, veya veya değeri döndüren bir ifadedir.<br /><br /> `enddate:` Hesaplama için bir bitiş tarihi `DateTime` `DateTimeOffset` `Time` duyarlık = [0-7] veya tarih biçimindeki bir karakter dizesi içeren bir, veya veya değeri döndüren bir ifadedir.<br /><br /> **Dönüş Değeri**<br /><br /> Bir `Int32` .<br /><br /> **Örnek**<br /><br /> `SqlServer.DATEDIFF('day', cast('6/9/2006' as DateTime),`<br /><br /> `cast('6/20/2006' as DateTime))`|  
|`DATENAME(datepart, date)`|Belirtilen tarihin belirtilen datepart 'ı temsil eden bir karakter dizesi döndürür.<br /><br /> **Arguments**<br /><br /> `datepart`: `String` Yeni bir değer döndürmek için tarihin parçasını temsil eden bir.<br /><br /> `date`: Bir veya veya bir `DateTime,` `DateTimeOffset` `Time` Tarih biçimindeki bir karakter dizesi 0-7 olan veya değerini döndüren bir ifade.<br /><br /> **Dönüş Değeri**<br /><br /> Belirtilen tarihin belirtilen datepart 'ı temsil eden karakter dizesi.<br /><br /> **Örnek**<br /><br /> `SqlServer.DATENAME('year', cast('6/9/2006' as DateTime))`|  
|`DATEPART(datepart, date)`|Belirtilen tarihin belirtilen datepart 'ı temsil eden bir tamsayı döndürür.<br /><br /> **Arguments**<br /><br /> `datepart`: `String` Yeni bir değer döndürmek için tarihin parçasını temsil eden bir.<br /><br /> `date`: `DateTime,` `DateTimeOffset,` `Time` Duyarlık = [0-7] veya bir tarih biçiminde karakter dizesi olan bir veya ya da değeri döndüren bir ifade.<br /><br /> **Dönüş Değeri**<br /><br /> Belirtilen tarihin, olarak belirtilen datepart 'ı `Int32` .<br /><br /> **Örnek**<br /><br /> `SqlServer.DATEPART('year', cast('6/9/2006' as DateTime))`|  
|`DAY(date)`|Belirtilen tarihin gününü bir tamsayı olarak döndürür.<br /><br /> **Arguments**<br /><br /> `date`: `DateTime` Ya da `DateTimeOffset` duyarlık = 0-7 olan bir ifade.<br /><br /> **Dönüş Değeri**<br /><br /> Belirtilen tarihin bitiş günü `Int32` .<br /><br /> **Örnek**<br /><br /> `SqlServer.DAY(cast('6/9/2006' as DateTime))`|  
|`GETDATE()`|Tarih saat değerleri için SQL Server iç biçimde geçerli tarih ve saati üretir.<br /><br /> **Dönüş Değeri**<br /><br /> Geçerli sistem tarih ve saati `DateTime` ile bir duyarlık 3.<br /><br /> **Örnek**<br /><br /> `SqlServer.GETDATE()`|  
|`GETUTCDATE()`|UTC (Eşgüdümlü Evrensel Saat veya Greenwich saati) biçiminde tarih saat değeri üretir.<br /><br /> **Dönüş Değeri**<br /><br /> `DateTime`UTC biçiminde 3 kesinliğine sahip değer.<br /><br /> **Örnek**<br /><br /> `SqlServer.GETUTCDATE()`|  
|`MONTH(date)`|Belirtilen tarihin ayını tamsayı olarak döndürür.<br /><br /> **Arguments**<br /><br /> `date`: `DateTime` Ya da `DateTimeOffset` duyarlık = 0-7 olan bir ifade.<br /><br /> **Dönüş Değeri**<br /><br /> Belirtilen tarihin ayı olarak `Int32` .<br /><br /> **Örnek**<br /><br /> `SqlServer.MONTH(cast('6/9/2006' as DateTime))`|  
|`YEAR(date)`|Belirtilen tarihin yılını tamsayı olarak döndürür.<br /><br /> **Arguments**<br /><br /> `date`: `DateTime` Ya da `DateTimeOffset` duyarlık = 0-7 olan bir ifade.<br /><br /> **Dönüş Değeri**<br /><br /> Belirtilen tarihin yıl olarak yılı `Int32` .<br /><br /> **Örnek**<br /><br /> `SqlServer.YEAR(cast('6/9/2006' as DateTime))`|  
|`SYSDATETIME()`|`DateTime`7 duyarlığına sahip bir değer döndürür.<br /><br /> **Dönüş Değeri**<br /><br /> `DateTime`7 duyarlığına sahip bir değer.<br /><br /> **Örnek**<br /><br /> `SqlServer.SYSDATETIME()`|  
|`SYSUTCDATE()`|UTC (Eşgüdümlü Evrensel Saat veya Greenwich saati) biçiminde tarih saat değeri üretir.<br /><br /> **Dönüş Değeri**<br /><br /> `DateTime`UTC biçiminde duyarlık = 7 olan değer.<br /><br /> **Örnek**<br /><br /> `SqlServer.SYSUTCDATE()`|  
|`SYSDATETIMEOFFSET()`|`DateTimeOffset`7 duyarlığına sahip bir döndürür.<br /><br /> **Dönüş Değeri**<br /><br /> `DateTimeOffset`UTC biçiminde 7 duyarlığına sahip bir değer.<br /><br /> **Örnek**<br /><br /> `SqlServer.SYSDATETIMEOFFSET()`|  
  
 SqlClient 'ın desteklediği tarih ve saat işlevleri hakkında daha fazla bilgi için bkz. [Tarih ve saat veri türleri ve işlevleri (Transact-SQL)](/sql/t-sql/functions/date-and-time-data-types-and-functions-transact-sql).
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity Framework için SqlClient İşlevleri](sqlclient-for-ef-functions.md)
