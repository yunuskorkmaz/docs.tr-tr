---
title: Sistem İşlevleri
ms.date: 03/30/2017
ms.assetid: b7c71b58-09e6-44ce-a3e5-a0fdb892fb86
ms.openlocfilehash: 552f374bc1824a16fb323cd19abe79c1914295a7
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248231"
---
# <a name="system-functions"></a>Sistem İşlevleri
SQL Server (SqlClient) için .NET Framework Veri Sağlayıcısı aşağıdaki sistem işlevlerini sağlar:  
  
|İşlev|Açıklama|  
|--------------|-----------------|  
|`CHECKSUM (` `value`, [`value`, [`value`]]`)`|Sağlama toplamı değerini döndürür. `CHECKSUM`, karma dizinler oluştururken kullanılmak üzere tasarlanmıştır.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `value`: A `Boolean`, `Byte`, ,`Int16` ,,`Single`, ,`Double`,,,, veya`Guid`. `Int64` `Decimal` `DateTime` `String` `Binary` `Int32` Bir, iki veya üç değer belirtebilirsiniz.<br /><br /> **Dönüş değeri**<br /><br /> Belirtilen ifadenin mutlak değeri.<br /><br /> **Örnek**<br /><br /> `SqlServer.CHECKSUM(10,100,1000.0)`|  
|`CURRENT_TIMESTAMP ()`|SQL Server iç biçiminde geçerli tarih ve saati, SQL Server 2008 ' `DateTime` de duyarlık ve SQL Server 2005 ' de bir duyarlık değeri olan değerler için üretir.<br /><br /> **Dönüş değeri**<br /><br /> Geçerli sistem tarih ve saati olarak `DateTime`.<br /><br /> **Örnek**<br /><br /> `SqlServer.CURRENT_TIMESTAMP()`|  
|`CURRENT_ USER``()`|Geçerli kullanıcının adını döndürür.<br /><br /> **Dönüş değeri**<br /><br /> ASCII `String`.<br /><br /> **Örnek**<br /><br /> `SqlServer.CURRENT_USER()`|  
|`DATALENGTH``(` `expression``)`|Herhangi bir ifadeyi temsil etmek için kullanılan bayt sayısını döndürür.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `expression`: A `Boolean`, `Byte`, ,`Int16` ,,`Single`, ,`Double`,,,,, ,`Binary`veya `Time` `DateTime` `Decimal` `Int32` `Int64` `DateTimeOffset` `String` `Guid`.<br /><br /> **Dönüş değeri**<br /><br /> Özelliklerinin `Int32`boyutu.<br /><br /> **Örnek**<br /><br /> `SELECT VALUE SqlServer.DATALENGTH(P.Name)FROM`<br /><br /> `AdventureWorksEntities.Product AS P`|  
|`HOST_NAME()`|İş istasyonu adını döndürür.<br /><br /> **Dönüş değeri**<br /><br /> Unicode `String`.<br /><br /> **Örnek**<br /><br /> `SqlServer.HOST_NAME()`|  
|`ISDATE(` `expression` `)`|Giriş ifadesinin geçerli bir tarih olup olmadığını belirler.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `expression`: A `Boolean`, `Byte`, ,`Int16` ,,`Single`, ,`Double`,,,,, ,`Binary`veya `Time` `DateTime` `Decimal` `Int32` `Int64` `DateTimeOffset` `String` `Guid`.<br /><br /> **Dönüş değeri**<br /><br /> Bir `Int32`. Giriş ifadesi geçerli bir tarihsiyse bir (1). Sıfır (0) yoksa.<br /><br /> **Örnek**<br /><br /> `SqlServer.ISDATE('1/1/2006')`|  
|`ISNUMERIC(` `expression` `)`|Bir ifadenin geçerli bir sayısal tür olup olmadığını belirler.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `expression`: A `Boolean`, `Byte`, ,`Int16` ,,`Single`, ,`Double`,,,,, ,`Binary`veya `Time` `DateTime` `Decimal` `Int32` `Int64` `DateTimeOffset` `String` `Guid`.<br /><br /> **Dönüş değeri**<br /><br /> Bir `Int32`. Giriş ifadesi geçerli bir tarihsiyse bir (1). Sıfır (0) yoksa.<br /><br /> **Örnek**<br /><br /> `SqlServer.ISNUMERIC('21')`|  
|`NEWID()`|GUID türünde benzersiz bir değer oluşturur.<br /><br /> **Dönüş değeri**<br /><br /> A `Guid`.<br /><br /> **Örnek**<br /><br /> `SqlServer.NEWID()`|  
|`USER_NAME(` `id` `)`|Belirtilen bir kimlik numarasından veritabanı kullanıcı adını döndürür.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `expression`: Bir `Int32` veritabanı kullanıcısı ile ilişkili bir kimlik numarası.<br /><br /> **Dönüş değeri**<br /><br /> Unicode `String`.<br /><br /> **Örnek**<br /><br /> `SqlServer.USER_NAME(0)`|  
  
 SqlClient tarafından desteklenen dize işlevleri hakkında daha fazla bilgi için, SqlClient sağlayıcısı bildiriminde belirttiğiniz SQL Server sürümü için belgelere bakın:  
  
|SQL Server 2000|SQL Server 2005|SQL Server 2008|  
|---------------------|---------------------|---------------------|  
|[Sistem Işlevleri Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=115918)|[Sistem Işlevleri Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=115917)|[Sistem Işlevleri (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=115919)|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Dili](./language-reference/entity-sql-language.md)
- [Entity Framework için SqlClient İşlevleri](sqlclient-for-ef-functions.md)
