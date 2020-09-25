---
title: SQL Server İkili ve Büyük Değerli Veriler
ms.date: 03/30/2017
ms.assetid: e00827b3-7511-4b2d-91d7-851ca86cc6b5
ms.openlocfilehash: a9296e83b0f4e4352423470433670bb2cbe5a248
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91183045"
---
# <a name="sql-server-binary-and-large-value-data"></a>SQL Server İkili ve Büyük Değerli Veriler

SQL Server,, `max` `varchar` `nvarchar` ve veri türlerinin depolama kapasitesini genişleten belirleyicisi sağlar `varbinary` . `varchar(max)`, `nvarchar(max)` ve `varbinary(max)` topluca *büyük değerli veri türleri*olarak adlandırılır. En fazla 2 ^ 31-1 bayt veri depolamak için büyük değerli veri türlerini kullanabilirsiniz.  
  
 SQL Server 2008, bir veri türü olmayan FıLESTREAM özniteliğini tanıtır, ancak bir sütunda tanımlanabilecek bir özniteliği yerine, büyük değerli verilerin veritabanı yerine dosya sisteminde depolanmasına olanak tanır.  
  
## <a name="in-this-section"></a>Bu Bölümde  

 [ADO.NET İçinde Büyük Değerli (Maks) Verileri Değiştirme](modifying-large-value-max-data.md)  
 Büyük değerli veri türleriyle nasıl çalışabileceğinizi açıklar.  
  
 [FILESTREAM Verileri](filestream-data.md)  
 FıLESTREAM özniteliğiyle SQL Server 2008 ' de depolanan büyük değerli verilerle nasıl çalışabileceğinizi açıklar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [SQL Server Veri Türleri ve ADO.NET](sql-server-data-types.md)
- [ADO.NET’te SQL Server Veri İşlemleri](sql-server-data-operations.md)
- [ADO.NET’te Veri Alma ve Değiştirme](../retrieving-and-modifying-data.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
