---
title: Sistem İşlevleri
ms.date: 03/30/2017
ms.assetid: b7c71b58-09e6-44ce-a3e5-a0fdb892fb86
ms.openlocfilehash: 9b5455d63dca40834515b14bae2f35d3b54d2aee
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452441"
---
# <a name="system-functions"></a>Sistem İşlevleri
SQL Server (SqlClient) için .NET Framework Veri Sağlayıcısı aşağıdaki sistem işlevlerini sağlar:  
  
|İşlev|Açıklama|  
|--------------|-----------------|  
|`CHECKSUM (` `value`, [`value`, [`value`]]`)`|Sağlama toplamı değerini döndürür. `CHECKSUM`, karma dizinler oluştururken kullanılmak üzere tasarlanmıştır.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `value`: `Boolean`, `Byte`, `Int16`, `Int32`, `Int64`, `Single`, `Decimal`, `Double`, `DateTime`, `String`, `Binary`veya `Guid`. Bir, iki veya üç değer belirtebilirsiniz.<br /><br /> **Dönüş değeri**<br /><br /> Belirtilen ifadenin mutlak değeri.<br /><br /> **Örnek**<br /><br /> `SqlServer.CHECKSUM(10,100,1000.0)`|  
|`CURRENT_TIMESTAMP ()`|SQL Server 2008 ve SQL Server 2005 ' de bir duyarlığa sahip `DateTime` değerler için SQL Server iç biçimdeki geçerli tarih ve saati üretir.<br /><br /> **Dönüş değeri**<br /><br /> `DateTime`olarak geçerli sistem tarihi ve saati.<br /><br /> **Örnek**<br /><br /> `SqlServer.CURRENT_TIMESTAMP()`|  
|`CURRENT_ USER` `()`|Geçerli kullanıcının adını döndürür.<br /><br /> **Dönüş değeri**<br /><br /> ASCII `String`.<br /><br /> **Örnek**<br /><br /> `SqlServer.CURRENT_USER()`|  
|`DATALENGTH` `(` `expression` `)`|Herhangi bir ifadeyi temsil etmek için kullanılan bayt sayısını döndürür.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `expression`: `Boolean`, `Byte`, `Int16`, `Int32`, `Int64`, `Single`, `Decimal`, `Double`, `DateTime`, `Time`, `DateTimeOffset`, `String`, `Binary`veya `Guid`.<br /><br /> **Dönüş değeri**<br /><br /> `Int32`olarak özelliklerin boyutu.<br /><br /> **Örnek**<br /><br /> `SELECT VALUE SqlServer.DATALENGTH(P.Name)FROM`<br /><br /> `AdventureWorksEntities.Product AS P`|  
|`HOST_NAME()`|İş istasyonu adını döndürür.<br /><br /> **Dönüş değeri**<br /><br /> Bir Unicode `String`.<br /><br /> **Örnek**<br /><br /> `SqlServer.HOST_NAME()`|  
|`ISDATE(` `expression` `)`|Giriş ifadesinin geçerli bir tarih olup olmadığını belirler.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `expression`: `Boolean`, `Byte`, `Int16`, `Int32`, `Int64`, `Single`, `Decimal`, `Double`, `DateTime`, `Time`, `DateTimeOffset`, `String`, `Binary`veya `Guid`.<br /><br /> **Dönüş değeri**<br /><br /> Bir `Int32`. Giriş ifadesi geçerli bir tarihsiyse bir (1). Sıfır (0) yoksa.<br /><br /> **Örnek**<br /><br /> `SqlServer.ISDATE('1/1/2006')`|  
|`ISNUMERIC(` `expression` `)`|Bir ifadenin geçerli bir sayısal tür olup olmadığını belirler.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `expression`: `Boolean`, `Byte`, `Int16`, `Int32`, `Int64`, `Single`, `Decimal`, `Double`, `DateTime`, `Time`, `DateTimeOffset`, `String`, `Binary`veya `Guid`.<br /><br /> **Dönüş değeri**<br /><br /> Bir `Int32`. Giriş ifadesi geçerli bir tarihsiyse bir (1). Sıfır (0) yoksa.<br /><br /> **Örnek**<br /><br /> `SqlServer.ISNUMERIC('21')`|  
|`NEWID()`|GUID türünde benzersiz bir değer oluşturur.<br /><br /> **Dönüş değeri**<br /><br /> Bir `Guid`.<br /><br /> **Örnek**<br /><br /> `SqlServer.NEWID()`|  
|`USER_NAME(` `id` `)`|Belirtilen bir kimlik numarasından veritabanı kullanıcı adını döndürür.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `expression`: bir veritabanı kullanıcısı ile ilişkili bir `Int32` kimlik numarası.<br /><br /> **Dönüş değeri**<br /><br /> Bir Unicode `String`.<br /><br /> **Örnek**<br /><br /> `SqlServer.USER_NAME(0)`|  
  
 SqlClient tarafından desteklenen `String` işlevleri hakkında daha fazla bilgi için bkz. [dize işlevleri (Transact-SQL)](/sql/t-sql/functions/string-functions-transact-sql).
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Dili](./language-reference/entity-sql-language.md)
- [Entity Framework için SqlClient İşlevleri](sqlclient-for-ef-functions.md)
