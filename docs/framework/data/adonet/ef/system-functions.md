---
title: Sistem İşlevleri
ms.date: 03/30/2017
ms.assetid: b7c71b58-09e6-44ce-a3e5-a0fdb892fb86
ms.openlocfilehash: 0d46429ac958e6f5db4d51947669784303af783b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91156504"
---
# <a name="system-functions"></a>Sistem İşlevleri

SQL Server (SqlClient) için .NET Framework Veri Sağlayıcısı aşağıdaki sistem işlevlerini sağlar:  
  
|İşlev|Açıklama|  
|--------------|-----------------|  
|`CHECKSUM (` `value`, [`value`, [`value`]]`)`|Sağlama toplamı değerini döndürür. `CHECKSUM` , karma dizinler oluştururken kullanılmak üzere tasarlanmıştır.<br /><br /> **Arguments**<br /><br /> `value`: A `Boolean` , `Byte` , `Int16` , `Int32` , `Int64` , `Single` , `Decimal` , `Double` , `DateTime` , `String` , `Binary` , veya `Guid` . Bir, iki veya üç değer belirtebilirsiniz.<br /><br /> **Dönüş Değeri**<br /><br /> Belirtilen ifadenin mutlak değeri.<br /><br /> **Örnek**<br /><br /> `SqlServer.CHECKSUM(10,100,1000.0)`|  
|`CURRENT_TIMESTAMP ()`|SQL Server iç biçiminde geçerli tarih ve saati, `DateTime` SQL Server 2008 ' de duyarlık ve SQL Server 2005 ' de bir duyarlık değeri olan değerler için üretir.<br /><br /> **Dönüş Değeri**<br /><br /> Geçerli sistem tarih ve saati olarak `DateTime` .<br /><br /> **Örnek**<br /><br /> `SqlServer.CURRENT_TIMESTAMP()`|  
|`CURRENT_ USER` `()`|Geçerli kullanıcının adını döndürür.<br /><br /> **Dönüş Değeri**<br /><br /> ASCII `String` .<br /><br /> **Örnek**<br /><br /> `SqlServer.CURRENT_USER()`|  
|`DATALENGTH` `(` `expression` `)`|Herhangi bir ifadeyi temsil etmek için kullanılan bayt sayısını döndürür.<br /><br /> **Arguments**<br /><br /> `expression`: A `Boolean` , `Byte` , `Int16` , `Int32` , `Int64` , `Single` , `Decimal` , `Double` , `DateTime` , `Time` , `DateTimeOffset` , `String` , `Binary` , veya `Guid` .<br /><br /> **Dönüş Değeri**<br /><br /> Özelliklerinin boyutu `Int32` .<br /><br /> **Örnek**<br /><br /> `SELECT VALUE SqlServer.DATALENGTH(P.Name)FROM`<br /><br /> `AdventureWorksEntities.Product AS P`|  
|`HOST_NAME()`|İş istasyonu adını döndürür.<br /><br /> **Dönüş Değeri**<br /><br /> Unicode `String` .<br /><br /> **Örnek**<br /><br /> `SqlServer.HOST_NAME()`|  
|`ISDATE(` `expression` `)`|Giriş ifadesinin geçerli bir tarih olup olmadığını belirler.<br /><br /> **Arguments**<br /><br /> `expression`: A `Boolean` , `Byte` , `Int16` , `Int32` , `Int64` , `Single` , `Decimal` , `Double` , `DateTime` , `Time` , `DateTimeOffset` , `String` , `Binary` , veya `Guid` .<br /><br /> **Dönüş Değeri**<br /><br /> Bir `Int32` . Giriş ifadesi geçerli bir tarihsiyse bir (1). Sıfır (0) yoksa.<br /><br /> **Örnek**<br /><br /> `SqlServer.ISDATE('1/1/2006')`|  
|`ISNUMERIC(` `expression` `)`|Bir ifadenin geçerli bir sayısal tür olup olmadığını belirler.<br /><br /> **Arguments**<br /><br /> `expression`: A `Boolean` , `Byte` , `Int16` , `Int32` , `Int64` , `Single` , `Decimal` , `Double` , `DateTime` , `Time` , `DateTimeOffset` , `String` , `Binary` , veya `Guid` .<br /><br /> **Dönüş Değeri**<br /><br /> Bir `Int32` . Giriş ifadesi geçerli bir tarihsiyse bir (1). Sıfır (0) yoksa.<br /><br /> **Örnek**<br /><br /> `SqlServer.ISNUMERIC('21')`|  
|`NEWID()`|GUID türünde benzersiz bir değer oluşturur.<br /><br /> **Dönüş Değeri**<br /><br /> Bir `Guid`.<br /><br /> **Örnek**<br /><br /> `SqlServer.NEWID()`|  
|`USER_NAME(` `id` `)`|Belirtilen bir kimlik numarasından veritabanı kullanıcı adını döndürür.<br /><br /> **Arguments**<br /><br /> `expression`: `Int32` Bir veritabanı kullanıcısı ile ilişkili bir kimlik numarası.<br /><br /> **Dönüş Değeri**<br /><br /> Unicode `String` .<br /><br /> **Örnek**<br /><br /> `SqlServer.USER_NAME(0)`|  
  
 SqlClient tarafından desteklenen işlevler hakkında daha fazla bilgi için `String` bkz. [dize Işlevleri (Transact-SQL)](/sql/t-sql/functions/string-functions-transact-sql).
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Dili](./language-reference/entity-sql-language.md)
- [Entity Framework için SqlClient İşlevleri](sqlclient-for-ef-functions.md)
