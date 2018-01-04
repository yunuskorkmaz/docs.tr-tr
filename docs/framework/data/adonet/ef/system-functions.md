---
title: "Sistem işlevleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b7c71b58-09e6-44ce-a3e5-a0fdb892fb86
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: dda704e70fc7927f382e851189073ffa5dececb9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="system-functions"></a>Sistem işlevleri
SQL Server (SqlClient) için .NET Framework veri sağlayıcısı aşağıdaki sistem işlevleri sağlar:  
  
|İşlev|Açıklama|  
|--------------|-----------------|  
|`CHECKSUM (` `value`, [`value`, [`value`]]`)`|Sağlama toplamı değeri döndürür. `CHECKSUM`karma dizinleri oluşturmanın kullanıma yöneliktir.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `value`: Bir `Boolean`, `Byte`, `Int16`, `Int32`, `Int64`, `Single`, `Decimal`, `Double`, `DateTime`, `String`, `Binary`, veya `Guid`. Bir, iki veya üç değerlerini belirtebilirsiniz.<br /><br /> **Dönüş değeri**<br /><br /> Belirtilen ifade mutlak değeri.<br /><br /> **Örnek**<br /><br /> `SqlServer.CHECKSUM(10,100,1000.0)`|  
|`CURRENT_TIMESTAMP ()`|Geçerli tarih ve saat için SQL Server dahili biçiminde üretir `DateTime` kesinliği 7 SQL Server 2008 ve SQL Server 2005'te 3 kesinliğini değerlerle.<br /><br /> **Dönüş değeri**<br /><br /> Geçerli sistem tarihi ve saati olarak bir `DateTime`.<br /><br /> **Örnek**<br /><br /> `SqlServer.CURRENT_TIMESTAMP()`|  
|`CURRENT_ USER``()`|Geçerli kullanıcı adını döndürür.<br /><br /> **Dönüş değeri**<br /><br /> Bir ASCII `String`.<br /><br /> **Örnek**<br /><br /> `SqlServer.CURRENT_USER()`|  
|`DATALENGTH` `(` `expression` `)`|Herhangi bir ifade göstermek için kullanılan bayt sayısını döndürür.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `expression`: Bir `Boolean`, `Byte`, `Int16`, `Int32`, `Int64`, `Single`, `Decimal`, `Double`, `DateTime`, `Time`, `DateTimeOffset`, `String`, `Binary`, veya `Guid`.<br /><br /> **Dönüş değeri**<br /><br /> Özellikleri olarak boyutunu bir `Int32`.<br /><br /> **Örnek**<br /><br /> `SELECT VALUE SqlServer.DATALENGTH(P.Name)FROM`<br /><br /> `AdventureWorksEntities.Product AS P`|  
|`HOST_NAME()`|İş istasyonu adı döndürür.<br /><br /> **Dönüş değeri**<br /><br /> Bir Unicode `String`.<br /><br /> **Örnek**<br /><br /> `SqlServer.HOST_NAME()`|  
|`ISDATE(` `expression` `)`|Bir giriş ifadesi geçerli bir tarih olup olmadığını belirler.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `expression`: Bir `Boolean`, `Byte`, `Int16`, `Int32`, `Int64`, `Single`, `Decimal`, `Double`, `DateTime`, `Time`, `DateTimeOffset`, `String`, `Binary`, veya `Guid`.<br /><br /> **Dönüş değeri**<br /><br /> Bir `Int32`. Bir giriş ifadesi geçerli bir tarih olması durumunda (1). Sıfır (0) Aksi takdirde.<br /><br /> **Örnek**<br /><br /> `SqlServer.ISDATE('1/1/2006')`|  
|`ISNUMERIC(` `expression` `)`|Bir ifade geçerli bir sayısal tür olup olmadığını belirler.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `expression`: Bir `Boolean`, `Byte`, `Int16`, `Int32`, `Int64`, `Single`, `Decimal`, `Double`, `DateTime`, `Time`, `DateTimeOffset`, `String`, `Binary`, veya `Guid`.<br /><br /> **Dönüş değeri**<br /><br /> Bir `Int32`. Bir giriş ifadesi geçerli bir tarih olması durumunda (1). Sıfır (0) Aksi takdirde.<br /><br /> **Örnek**<br /><br /> `SqlServer.ISNUMERIC('21')`|  
|`NEWID()`|Guid türünde benzersiz bir değer oluşturur.<br /><br /> **Dönüş değeri**<br /><br /> A `Guid`.<br /><br /> **Örnek**<br /><br /> `SqlServer.NEWID()`|  
|`USER_NAME(` `id` `)`|Veritabanı kullanıcı adı belirtilen kimliği numarasından döndürür.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `expression`: Bir `Int32` bir veritabanı kullanıcısı ile ilişkili kimlik numarası.<br /><br /> **Dönüş değeri**<br /><br /> Bir Unicode `String`.<br /><br /> **Örnek**<br /><br /> `SqlServer.USER_NAME(0)`|  
  
 SqlClient destekleyen dize işlevleri hakkında daha fazla bilgi için SqlClient sağlayıcısı bildiriminde belirtilen SQL Server sürümü için belgelere bakın:  
  
|SQL Server 2000|SQL Server 2005|SQL Server 2008|  
|---------------------|---------------------|---------------------|  
|[Sistem işlevleri Transact-SQL)](http://go.microsoft.com/fwlink/?LinkId=115918)|[Sistem işlevleri Transact-SQL)](http://go.microsoft.com/fwlink/?LinkId=115917)|[Sistem işlevleri (Transact-SQL)](http://go.microsoft.com/fwlink/?LinkId=115919)|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Entity SQL Dili](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)  
 [Entity Framework için SqlClient İşlevleri](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md)
