---
title: Tarih ve Saat İşlevleri
ms.date: 03/30/2017
ms.assetid: 971762d0-663b-4b64-8c61-352a8e6d3949
ms.openlocfilehash: 8d5bbb9577e8016d6d5f2d0bef1932f6321a1e02
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59181928"
---
# <a name="date-and-time-functions"></a>Tarih ve Saat İşlevleri
SQL Server (SqlClient) için .NET Framework veri sağlayıcısı üzerinde işlem yapabileceğiniz date ve time işlevleri sağlayan bir `System.DateTime` giriş değeri ve dönüş bir `string`, sayısal, veya `System.DateTime` değer sonucu. Bu işlevler SqlServer ad alanında SqlClient kullanırken, kullanılabilir bağımlıdır. Bir sağlayıcının ad özelliği, hangi önekin türleri ve işlevleri gibi belirli yapılar için bu sağlayıcı tarafından kullanılan bulmak Entity Framework sağlar. Aşağıdaki tabloda SqlClient date ve time işlevleri gösterir.  
  
|İşlev|Açıklama|  
|--------------|-----------------|  
|`DATEADD(datepart, number, date)`|Yeni bir `DateTime` belirtilen tarihe bir aralık eklemeye ilişkin temel değer.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `datepart`: A `String` yeni bir değer döndürmek tarih bölümünü temsil eder.<br /><br /> `number`: `Int32`, `Int64`, `Decimal`, Veya `Double` kullanılan değer Artım yapılacağını `datepart`.<br /><br /> `date:` Döndüren bir ifadeyle bir `DateTime`, veya `DateTimeOffset`, veya `Time` kesinliği ile = [0-7], ya da bir karakter dizesini bir tarih biçimi.<br /><br /> **Dönüş değeri**<br /><br /> Yeni bir `DateTime`, veya `DateTimeOffset`, veya `Time` duyarlık değeri [0-7] =.<br /><br /> **Örnek**<br /><br /> `SqlServer.DATEADD('day', 22, cast('6/9/2006' as DateTime))`|  
|`DATEDIFF(datepart,startdate,enddate)`|Belirtilen iki tarih arasında geçilen tarih ve saat sınırlarının sayısını döndürür.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `datepart`: A `String` tarih farkını hesaplamak için bölümünü temsil eder.<br /><br /> `startdate`: Hesaplama için bir başlangıç tarihi döndüren bir ifadedir bir `DateTime`, veya `DateTimeOffset`, veya `Time` duyarlık değeri [0-7] = veya tarih biçiminde bir karakter dizesi.<br /><br /> `enddate:` Hesaplama için bir bitiş tarihi döndüren bir ifadedir bir `DateTime`, veya `DateTimeOffset`, veya `Time` duyarlık değeri [0-7] = veya tarih biçiminde bir karakter dizesi.<br /><br /> **Dönüş değeri**<br /><br /> Bir `Int32`.<br /><br /> **Örnek**<br /><br /> `SqlServer.DATEDIFF('day', cast('6/9/2006' as DateTime),`<br /><br /> `cast('6/20/2006' as DateTime))`|  
|`DATENAME(datepart, date)`|Belirtilen tarihin belirtilen datepart temsil eden bir karakter dizesi döndürür.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `datepart`: A `String` yeni bir değer döndürmek tarih bölümünü temsil eder.<br /><br /> `date`: Döndüren bir ifadeyle bir `DateTime,` veya `DateTimeOffset`, veya `Time` duyarlık değeri [0-7] = veya tarih biçiminde bir karakter dizesi.<br /><br /> **Dönüş değeri**<br /><br /> Belirtilen tarihin belirtilen datepart temsil eden bir karakter dizesi.<br /><br /> **Örnek**<br /><br /> `SqlServer.DATENAME('year', cast('6/9/2006' as DateTime))`|  
|`DATEPART(datepart, date)`|Belirtilen tarihin belirtilen datepart temsil eden bir tamsayı döndürür.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `datepart`: A `String` yeni bir değer döndürmek tarih bölümünü temsil eder.<br /><br /> `date`: Döndüren bir ifadeyle bir `DateTime,` veya `DateTimeOffset,` veya `Time` duyarlık değeri [0-7] = veya tarih biçiminde bir karakter dizesi.<br /><br /> **Dönüş değeri**<br /><br /> Belirtilen tarihin belirtilen datepart olarak bir `Int32`.<br /><br /> **Örnek**<br /><br /> `SqlServer.DATEPART('year', cast('6/9/2006' as DateTime))`|  
|`DAY(date)`|Belirtilen tarihte bir tamsayı olarak gününü döndürür.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `date`: Bir ifade türü `DateTime` veya `DateTimeOffset` kesinliği ile = 0-7.<br /><br /> **Dönüş değeri**<br /><br /> Belirli bir tarih günü bir `Int32`.<br /><br /> **Örnek**<br /><br /> `SqlServer.DAY(cast('6/9/2006' as DateTime))`|  
|`GETDATE()`|Geçerli tarih ve saati datetime değerleri için SQL Server dahili biçiminde üretir.<br /><br /> **Dönüş değeri**<br /><br /> Geçerli sistem tarihi ve saati olarak bir `DateTime` 3 kesinliği ile.<br /><br /> **Örnek**<br /><br /> `SqlServer.GETDATE()`|  
|`GETUTCDATE()`|UTC (Eşgüdümlü Evrensel Saat veya Greenwich saati) biçiminde bir tarih saat değeri oluşturur.<br /><br /> **Dönüş değeri**<br /><br /> `DateTime` 3 UTC biçiminde bir duyarlık değeri.<br /><br /> **Örnek**<br /><br /> `SqlServer.GETUTCDATE()`|  
|`MONTH(date)`|Belirtilen tarihte bir tam sayı olarak ayı döndürür.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `date`: Bir ifade türü `DateTime` veya `DateTimeOffset` kesinliği ile = 0-7.<br /><br /> **Dönüş değeri**<br /><br /> Belirtilen tarihi olarak ayın bir `Int32`.<br /><br /> **Örnek**<br /><br /> `SqlServer.MONTH(cast('6/9/2006' as DateTime))`|  
|`YEAR(date)`|Bir tamsayı olarak belirtilen tarihin Yıl döndürür.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `date`: Bir ifade türü `DateTime` veya `DateTimeOffset` kesinliği ile = 0-7.<br /><br /> **Dönüş değeri**<br /><br /> Yılın belirli bir tarih bir `Int32`.<br /><br /> **Örnek**<br /><br /> `SqlServer.YEAR(cast('6/9/2006' as DateTime))`|  
|`SYSDATETIME()`|Döndürür bir `DateTime` 7 kesinliği ile değeri.<br /><br /> **Dönüş değeri**<br /><br /> A `DateTime` 7 kesinliği ile değeri.<br /><br /> **Örnek**<br /><br /> `SqlServer.SYSDATETIME()`|  
|`SYSUTCDATE()`|UTC (Eşgüdümlü Evrensel Saat veya Greenwich saati) biçiminde bir tarih saat değeri oluşturur.<br /><br /> **Dönüş değeri**<br /><br /> `DateTime` Duyarlık değeri = 7 UTC biçiminde.<br /><br /> **Örnek**<br /><br /> `SqlServer.SYSUTCDATE()`|  
|`SYSDATETIMEOFFSET()`|Döndürür bir `DateTimeOffset` 7 kesinliği ile.<br /><br /> **Dönüş değeri**<br /><br /> A `DateTimeOffset` 7 UTC biçiminde duyarlık değeri.<br /><br /> **Örnek**<br /><br /> `SqlServer.SYSDATETIMEOFFSET()`|  
  
 SqlClient destekleyen tarih ve saat işlevleri hakkında daha fazla bilgi için SqlClient sağlayıcı bildiriminde belirtilen SQL Server sürümü için belgelere bakın:  
  
|SQL Server 2000|SQL Server 2005|SQL Server 2008|  
|---------------------|---------------------|---------------------|  
|[Tarih ve saat işlevleri (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=115908)|[Tarih ve saat işlevleri (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=115909)|[Tarih ve saat işlevleri (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=98360)|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity Framework için SqlClient İşlevleri](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md)
