---
title: Sistem işlevleri
ms.date: 03/30/2017
ms.assetid: b7c71b58-09e6-44ce-a3e5-a0fdb892fb86
ms.openlocfilehash: 277f2f9c69610b134f3f95787f065f65b01712d2
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2018
ms.locfileid: "46697404"
---
# <a name="system-functions"></a>Sistem işlevleri
SQL Server (SqlClient) için .NET Framework veri sağlayıcısı, aşağıdaki sistem işlevleri sağlar:  
  
|İşlev|Açıklama|  
|--------------|-----------------|  
|`CHECKSUM (` `value`, [`value`, [`value`]]`)`|Sağlama toplamı değeri döndürür. `CHECKSUM` karma dizinleri oluşturma kullanılmak üzere tasarlanmıştır.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `value`: Bir `Boolean`, `Byte`, `Int16`, `Int32`, `Int64`, `Single`, `Decimal`, `Double`, `DateTime`, `String`, `Binary`, veya `Guid`. Bir, iki veya üç değer belirtebilirsiniz.<br /><br /> **Dönüş değeri**<br /><br /> Belirtilen ifadenin mutlak değeri.<br /><br /> **Örnek**<br /><br /> `SqlServer.CHECKSUM(10,100,1000.0)`|  
|`CURRENT_TIMESTAMP ()`|Geçerli tarih ve saat için SQL Server dahili biçiminde üretir `DateTime` değerlerini kesinliği, 7'in SQL Server 2008 ve SQL Server 2005'te 3 duyarlığını.<br /><br /> **Dönüş değeri**<br /><br /> Geçerli sistem tarihi ve saati olarak bir `DateTime`.<br /><br /> **Örnek**<br /><br /> `SqlServer.CURRENT_TIMESTAMP()`|  
|`CURRENT_ USER``()`|Geçerli kullanıcı adını döndürür.<br /><br /> **Dönüş değeri**<br /><br /> Bir ASCII `String`.<br /><br /> **Örnek**<br /><br /> `SqlServer.CURRENT_USER()`|  
|`DATALENGTH` `(` `expression` `)`|Herhangi bir ifadeyi temsil etmek için kullanılan bayt sayısını döndürür.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `expression`: Bir `Boolean`, `Byte`, `Int16`, `Int32`, `Int64`, `Single`, `Decimal`, `Double`, `DateTime`, `Time`, `DateTimeOffset`, `String`, `Binary`, veya `Guid`.<br /><br /> **Dönüş değeri**<br /><br /> Özellikleri olarak boyutunu bir `Int32`.<br /><br /> **Örnek**<br /><br /> `SELECT VALUE SqlServer.DATALENGTH(P.Name)FROM`<br /><br /> `AdventureWorksEntities.Product AS P`|  
|`HOST_NAME()`|İş istasyonu adı döndürür.<br /><br /> **Dönüş değeri**<br /><br /> Bir Unicode `String`.<br /><br /> **Örnek**<br /><br /> `SqlServer.HOST_NAME()`|  
|`ISDATE(` `expression` `)`|Bir giriş ifadesi geçerli bir tarih olup olmadığını belirler.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `expression`: Bir `Boolean`, `Byte`, `Int16`, `Int32`, `Int64`, `Single`, `Decimal`, `Double`, `DateTime`, `Time`, `DateTimeOffset`, `String`, `Binary`, veya `Guid`.<br /><br /> **Dönüş değeri**<br /><br /> Bir `Int32`. Bir giriş ifadesi geçerli bir tarih ise (1). Sıfır (0) Aksi takdirde.<br /><br /> **Örnek**<br /><br /> `SqlServer.ISDATE('1/1/2006')`|  
|`ISNUMERIC(` `expression` `)`|Bir ifade geçerli bir sayısal tür olup olmadığını belirler.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `expression`: Bir `Boolean`, `Byte`, `Int16`, `Int32`, `Int64`, `Single`, `Decimal`, `Double`, `DateTime`, `Time`, `DateTimeOffset`, `String`, `Binary`, veya `Guid`.<br /><br /> **Dönüş değeri**<br /><br /> Bir `Int32`. Bir giriş ifadesi geçerli bir tarih ise (1). Sıfır (0) Aksi takdirde.<br /><br /> **Örnek**<br /><br /> `SqlServer.ISNUMERIC('21')`|  
|`NEWID()`|GUID türündeki benzersiz bir değer oluşturur.<br /><br /> **Dönüş değeri**<br /><br /> A `Guid`.<br /><br /> **Örnek**<br /><br /> `SqlServer.NEWID()`|  
|`USER_NAME(` `id` `)`|Belirtilen kimliği numarasından veritabanı kullanıcı adını döndürür.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `expression`: Bir `Int32` bir veritabanı kullanıcısı ile ilişkili kimlik numarası.<br /><br /> **Dönüş değeri**<br /><br /> Bir Unicode `String`.<br /><br /> **Örnek**<br /><br /> `SqlServer.USER_NAME(0)`|  
  
 SqlClient destekleyen dize işlevleri hakkında daha fazla bilgi için SqlClient sağlayıcı bildiriminde belirtilen SQL Server sürümü için belgelere bakın:  
  
|SQL Server 2000|SQL Server 2005|SQL Server 2008|  
|---------------------|---------------------|---------------------|  
|[Sistem işlevleri Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=115918)|[Sistem işlevleri Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=115917)|[Sistem işlevleri (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=115919)|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Entity SQL Dili](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)  
 [Entity Framework için SqlClient İşlevleri](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md)
