---
title: SQL Server ikili ve büyük değerli veri
ms.date: 03/30/2017
ms.assetid: e00827b3-7511-4b2d-91d7-851ca86cc6b5
ms.openlocfilehash: 9ebbe23dfbcac7825ce449dd40f62b921d13ab4a
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/16/2018
ms.locfileid: "45683277"
---
# <a name="sql-server-binary-and-large-value-data"></a>SQL Server ikili ve büyük değerli veri
SQL Server sağlayan `max` depolama kapasitesini genişletir belirticisi `varchar`, `nvarchar`, ve `varbinary` veri türleri. `varchar(max)`, `nvarchar(max)`, ve `varbinary(max)` toplu olarak adlandırılır *büyük değerli veri türleri*. Büyük değerli veri türleri en fazla 2 depolamak için kullanabileceğiniz ^ 31-1 bayt veri.  
  
 SQL Server 2008 veritabanı yerine dosya sisteminde depolanmış büyük değerli veri sağlayan değil bir veri türü FILESTREAM özniteliğine, ancak bunun yerine bir sütuna, tanımlanan bir öznitelik tanıtır.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [ADO.NET İçinde Büyük Değerli (Maks) Verileri Değiştirme](../../../../../docs/framework/data/adonet/sql/modifying-large-value-max-data.md)  
 Büyük değerli veri türleriyle çalışır açıklar.  
  
 [FILESTREAM Verileri](../../../../../docs/framework/data/adonet/sql/filestream-data.md)  
 FILESTREAM özniteliğine SQL Server 2008'de depolanan büyük değerli veri ile nasıl çalışılacağını açıklar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [SQL Server Veri Türleri ve ADO.NET](../../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)  
 [ADO.NET’te SQL Server Veri İşlemleri](../../../../../docs/framework/data/adonet/sql/sql-server-data-operations.md)  
 [ADO.NET’te Veri Alma ve Değiştirme](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
