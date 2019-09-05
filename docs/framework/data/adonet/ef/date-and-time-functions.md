---
title: Tarih ve Saat İşlevleri
ms.date: 03/30/2017
ms.assetid: 971762d0-663b-4b64-8c61-352a8e6d3949
ms.openlocfilehash: fe70795ba98cf500f2066980d259ff995c3398e0
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251636"
---
# <a name="date-and-time-functions"></a>Tarih ve Saat İşlevleri
SQL Server (SqlClient) için .NET Framework veri sağlayıcısı, bir `System.DateTime` giriş değeri üzerinde işlemler gerçekleştiren ve bir `string`, sayısal ya `System.DateTime` da değer sonucu döndüren tarih ve saat işlevleri sağlar. Bu işlevler, SqlClient kullandığınızda kullanılabilir olan SqlServer ad alanıdır. Bir sağlayıcının ad alanı özelliği Entity Framework, bu sağlayıcı tarafından türler ve işlevler gibi belirli yapılar için kullanılan öneki bulmasını sağlar. Aşağıdaki tabloda, SqlClient tarih ve saat işlevleri gösterilmektedir.  
  
|İşlev|Açıklama|  
|--------------|-----------------|  
|`DATEADD(datepart, number, date)`|Belirtilen tarihe bir `DateTime` Aralık eklemeye dayalı yeni bir değer döndürür.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `datepart`: Yeni `String` bir değer döndürmek için tarihin parçasını temsil eden bir.<br /><br /> `number`: `Int64`Arttırmak `Int32` için`datepart`kullanılan,, veya`Double`değeri. `Decimal`<br /><br /> `date:`Bir `DateTime`, 0-7 `DateTimeOffset` veya`Time` veya bir tarih biçiminde karakter dizesi döndüren bir ifade.<br /><br /> **Dönüş değeri**<br /><br /> Kesinlik = `DateTime`[0-7 `DateTimeOffset`] ile `Time` yeni bir veya veya değeri.<br /><br /> **Örnek**<br /><br /> `SqlServer.DATEADD('day', 22, cast('6/9/2006' as DateTime))`|  
|`DATEDIFF(datepart,startdate,enddate)`|Belirtilen iki tarih arasında çapraz tarih ve saat sınırları sayısını döndürür.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `datepart`: `String` Farkı hesaplamak için tarihin parçasını temsil eder.<br /><br /> `startdate`: Hesaplama için başlangıç tarihi duyarlık = [0-7] veya tarih biçimindeki `DateTime`bir karakter `DateTimeOffset`dizesi içeren `Time` bir, veya veya değeri döndüren bir ifadedir.<br /><br /> `enddate:`Hesaplama için bir bitiş tarihi duyarlık = [0-7] veya tarih `DateTime`biçimindeki bir `DateTimeOffset`karakter dizesi `Time` içeren bir, veya veya değeri döndüren bir ifadedir.<br /><br /> **Dönüş değeri**<br /><br /> Bir `Int32`.<br /><br /> **Örnek**<br /><br /> `SqlServer.DATEDIFF('day', cast('6/9/2006' as DateTime),`<br /><br /> `cast('6/20/2006' as DateTime))`|  
|`DATENAME(datepart, date)`|Belirtilen tarihin belirtilen datepart 'ı temsil eden bir karakter dizesi döndürür.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `datepart`: Yeni `String` bir değer döndürmek için tarihin parçasını temsil eden bir.<br /><br /> `date`: Bir `DateTime,` veya veya bir tarih biçimindeki `DateTimeOffset`bir karakter `Time` dizesi 0-7 olan veya değerini döndüren bir ifade.<br /><br /> **Dönüş değeri**<br /><br /> Belirtilen tarihin belirtilen datepart 'ı temsil eden karakter dizesi.<br /><br /> **Örnek**<br /><br /> `SqlServer.DATENAME('year', cast('6/9/2006' as DateTime))`|  
|`DATEPART(datepart, date)`|Belirtilen tarihin belirtilen datepart 'ı temsil eden bir tamsayı döndürür.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `datepart`: Yeni `String` bir değer döndürmek için tarihin parçasını temsil eden bir.<br /><br /> `date`: Kesinlik = [0-7] `DateTime,` veya `DateTimeOffset,` Tarih `Time` biçimindeki bir karakter dizesi ile veya ya da değeri döndüren bir ifade.<br /><br /> **Dönüş değeri**<br /><br /> Belirtilen tarihin, olarak `Int32`belirtilen datepart 'ı.<br /><br /> **Örnek**<br /><br /> `SqlServer.DATEPART('year', cast('6/9/2006' as DateTime))`|  
|`DAY(date)`|Belirtilen tarihin gününü bir tamsayı olarak döndürür.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `date`: `DateTime` Ya da `DateTimeOffset` duyarlık = 0-7 olan bir ifade.<br /><br /> **Dönüş değeri**<br /><br /> Belirtilen tarihin bitiş `Int32`günü.<br /><br /> **Örnek**<br /><br /> `SqlServer.DAY(cast('6/9/2006' as DateTime))`|  
|`GETDATE()`|Tarih saat değerleri için SQL Server iç biçimde geçerli tarih ve saati üretir.<br /><br /> **Dönüş değeri**<br /><br /> Geçerli sistem tarih ve saati ile bir `DateTime` duyarlık 3.<br /><br /> **Örnek**<br /><br /> `SqlServer.GETDATE()`|  
|`GETUTCDATE()`|UTC (Eşgüdümlü Evrensel Saat veya Greenwich saati) biçiminde tarih saat değeri üretir.<br /><br /> **Dönüş değeri**<br /><br /> UTC biçiminde 3 kesinliğine sahip değer.`DateTime`<br /><br /> **Örnek**<br /><br /> `SqlServer.GETUTCDATE()`|  
|`MONTH(date)`|Belirtilen tarihin ayını tamsayı olarak döndürür.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `date`: `DateTime` Ya da `DateTimeOffset` duyarlık = 0-7 olan bir ifade.<br /><br /> **Dönüş değeri**<br /><br /> Belirtilen tarihin ayı olarak `Int32`.<br /><br /> **Örnek**<br /><br /> `SqlServer.MONTH(cast('6/9/2006' as DateTime))`|  
|`YEAR(date)`|Belirtilen tarihin yılını tamsayı olarak döndürür.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `date`: `DateTime` Ya da `DateTimeOffset` duyarlık = 0-7 olan bir ifade.<br /><br /> **Dönüş değeri**<br /><br /> Belirtilen tarihin yıl olarak `Int32`yılı.<br /><br /> **Örnek**<br /><br /> `SqlServer.YEAR(cast('6/9/2006' as DateTime))`|  
|`SYSDATETIME()`|7 duyarlığına sahip bir `DateTime` değer döndürür.<br /><br /> **Dönüş değeri**<br /><br /> 7 `DateTime` duyarlığına sahip bir değer.<br /><br /> **Örnek**<br /><br /> `SqlServer.SYSDATETIME()`|  
|`SYSUTCDATE()`|UTC (Eşgüdümlü Evrensel Saat veya Greenwich saati) biçiminde tarih saat değeri üretir.<br /><br /> **Dönüş değeri**<br /><br /> UTC biçiminde duyarlık = 7 olan değer.`DateTime`<br /><br /> **Örnek**<br /><br /> `SqlServer.SYSUTCDATE()`|  
|`SYSDATETIMEOFFSET()`|7 duyarlığına sahip bir `DateTimeOffset` döndürür.<br /><br /> **Dönüş değeri**<br /><br /> UTC `DateTimeOffset` biçiminde 7 duyarlığına sahip bir değer.<br /><br /> **Örnek**<br /><br /> `SqlServer.SYSDATETIMEOFFSET()`|  
  
 SqlClient 'ın desteklediği tarih ve saat işlevleri hakkında daha fazla bilgi için, SqlClient sağlayıcısı bildiriminde belirttiğiniz SQL Server sürümü için belgelere bakın:  
  
|SQL Server 2000|SQL Server 2005|SQL Server 2008|  
|---------------------|---------------------|---------------------|  
|[Tarih ve saat Işlevleri (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=115908)|[Tarih ve saat Işlevleri (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=115909)|[Tarih ve saat Işlevleri (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=98360)|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity Framework için SqlClient İşlevleri](sqlclient-for-ef-functions.md)
