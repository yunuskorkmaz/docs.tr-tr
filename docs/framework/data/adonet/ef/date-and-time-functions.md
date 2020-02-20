---
title: Tarih ve Saat İşlevleri
ms.date: 03/30/2017
ms.assetid: 971762d0-663b-4b64-8c61-352a8e6d3949
ms.openlocfilehash: 39bbc2bff378ff4434df6f33a1b175055f2e5800
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452519"
---
# <a name="date-and-time-functions"></a>Tarih ve Saat İşlevleri
SQL Server (SqlClient) için .NET Framework Veri Sağlayıcısı, bir `System.DateTime` giriş değeri üzerinde işlemler gerçekleştiren ve `string`, numeric veya `System.DateTime` değer sonucu döndüren tarih ve saat işlevleri sağlar. Bu işlevler, SqlClient kullandığınızda kullanılabilir olan SqlServer ad alanıdır. Bir sağlayıcının ad alanı özelliği Entity Framework, bu sağlayıcı tarafından türler ve işlevler gibi belirli yapılar için kullanılan öneki bulmasını sağlar. Aşağıdaki tabloda, SqlClient tarih ve saat işlevleri gösterilmektedir.  
  
|İşlev|Açıklama|  
|--------------|-----------------|  
|`DATEADD(datepart, number, date)`|Belirtilen tarihe bir Aralık eklemeye dayalı yeni bir `DateTime` değeri döndürür.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `datepart`: yeni bir değer döndürmek için tarihin parçasını temsil eden bir `String`.<br /><br /> `number`: `Double` artırmak için kullanılan `Int32`, `Int64`, `Decimal`veya `datepart`değeri.<br /><br /> bir `DateTime`veya `DateTimeOffset`ya da duyarlık = [0-7] ile `Time` veya tarih biçiminde bir karakter dizesi döndüren bir ifade `date:`.<br /><br /> **Dönüş değeri**<br /><br /> Yeni bir `DateTime`veya `DateTimeOffset`ya da duyarlık = [0-7] olan `Time` değeri.<br /><br /> **Örnek**<br /><br /> `SqlServer.DATEADD('day', 22, cast('6/9/2006' as DateTime))`|  
|`DATEDIFF(datepart,startdate,enddate)`|Belirtilen iki tarih arasında çapraz tarih ve saat sınırları sayısını döndürür.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `datepart`: farkı hesaplamak için tarihin parçasını temsil eden bir `String`.<br /><br /> `startdate`: hesaplama için başlangıç tarihi, bir `DateTime`veya `DateTimeOffset`ya da duyarlık = [0-7] ile `Time` değeri veya tarih biçiminde bir karakter dizesi döndüren bir ifadedir.<br /><br /> hesaplama için bitiş tarihi `enddate:`, bir `DateTime`veya `DateTimeOffset`ya da duyarlık = [0-7] ile `Time` değeri veya tarih biçiminde bir karakter dizesi döndüren bir ifadedir.<br /><br /> **Dönüş değeri**<br /><br /> Bir `Int32`.<br /><br /> **Örnek**<br /><br /> `SqlServer.DATEDIFF('day', cast('6/9/2006' as DateTime),`<br /><br /> `cast('6/20/2006' as DateTime))`|  
|`DATENAME(datepart, date)`|Belirtilen tarihin belirtilen datepart 'ı temsil eden bir karakter dizesi döndürür.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `datepart`: yeni bir değer döndürmek için tarihin parçasını temsil eden bir `String`.<br /><br /> `date`: bir `DateTime,` veya `DateTimeOffset`ya da duyarlık = [0-7] ile `Time` değeri veya tarih biçiminde bir karakter dizesi döndüren bir ifade.<br /><br /> **Dönüş değeri**<br /><br /> Belirtilen tarihin belirtilen datepart 'ı temsil eden karakter dizesi.<br /><br /> **Örnek**<br /><br /> `SqlServer.DATENAME('year', cast('6/9/2006' as DateTime))`|  
|`DATEPART(datepart, date)`|Belirtilen tarihin belirtilen datepart 'ı temsil eden bir tamsayı döndürür.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `datepart`: yeni bir değer döndürmek için tarihin parçasını temsil eden bir `String`.<br /><br /> `date`: duyarlık = [0-7] veya bir tarih biçiminde karakter dizesi olan bir `DateTime,` veya `DateTimeOffset,` ya da `Time` değeri döndüren bir ifade.<br /><br /> **Dönüş değeri**<br /><br /> `Int32`olarak belirtilen tarihin belirtilen datepart 'ı.<br /><br /> **Örnek**<br /><br /> `SqlServer.DATEPART('year', cast('6/9/2006' as DateTime))`|  
|`DAY(date)`|Belirtilen tarihin gününü bir tamsayı olarak döndürür.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `date`: duyarlık = 0-7 ile `DateTime` veya `DateTimeOffset` türünde bir ifade.<br /><br /> **Dönüş değeri**<br /><br /> `Int32`olarak belirtilen tarihin günü.<br /><br /> **Örnek**<br /><br /> `SqlServer.DAY(cast('6/9/2006' as DateTime))`|  
|`GETDATE()`|Tarih saat değerleri için SQL Server iç biçimde geçerli tarih ve saati üretir.<br /><br /> **Dönüş değeri**<br /><br /> Geçerli sistem tarih ve saati ile bir `DateTime` olarak 3 duyarlığına sahip.<br /><br /> **Örnek**<br /><br /> `SqlServer.GETDATE()`|  
|`GETUTCDATE()`|UTC (Eşgüdümlü Evrensel Saat veya Greenwich saati) biçiminde tarih saat değeri üretir.<br /><br /> **Dönüş değeri**<br /><br /> UTC biçiminde 3 kesinliğine sahip `DateTime` değeri.<br /><br /> **Örnek**<br /><br /> `SqlServer.GETUTCDATE()`|  
|`MONTH(date)`|Belirtilen tarihin ayını tamsayı olarak döndürür.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `date`: duyarlık = 0-7 ile `DateTime` veya `DateTimeOffset` türünde bir ifade.<br /><br /> **Dönüş değeri**<br /><br /> `Int32`olarak belirtilen tarihin ayı.<br /><br /> **Örnek**<br /><br /> `SqlServer.MONTH(cast('6/9/2006' as DateTime))`|  
|`YEAR(date)`|Belirtilen tarihin yılını tamsayı olarak döndürür.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `date`: duyarlık = 0-7 ile `DateTime` veya `DateTimeOffset` türünde bir ifade.<br /><br /> **Dönüş değeri**<br /><br /> `Int32`olarak belirtilen tarihin yılı.<br /><br /> **Örnek**<br /><br /> `SqlServer.YEAR(cast('6/9/2006' as DateTime))`|  
|`SYSDATETIME()`|7 duyarlığına sahip `DateTime` bir değer döndürür.<br /><br /> **Dönüş değeri**<br /><br /> 7 duyarlığına sahip bir `DateTime` değeri.<br /><br /> **Örnek**<br /><br /> `SqlServer.SYSDATETIME()`|  
|`SYSUTCDATE()`|UTC (Eşgüdümlü Evrensel Saat veya Greenwich saati) biçiminde tarih saat değeri üretir.<br /><br /> **Dönüş değeri**<br /><br /> UTC biçimindeki `DateTime` değeri duyarlık = 7.<br /><br /> **Örnek**<br /><br /> `SqlServer.SYSUTCDATE()`|  
|`SYSDATETIMEOFFSET()`|7 duyarlığına sahip bir `DateTimeOffset` döndürür.<br /><br /> **Dönüş değeri**<br /><br /> UTC biçiminde 7 duyarlığına sahip bir `DateTimeOffset` değeri.<br /><br /> **Örnek**<br /><br /> `SqlServer.SYSDATETIMEOFFSET()`|  
  
 SqlClient 'ın desteklediği tarih ve saat işlevleri hakkında daha fazla bilgi için bkz. [Tarih ve saat veri türleri ve işlevleri (Transact-SQL)](/sql/t-sql/functions/date-and-time-data-types-and-functions-transact-sql).
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity Framework için SqlClient İşlevleri](sqlclient-for-ef-functions.md)
