---
title: SQL Server İkili ve Büyük Değerli Veriler
ms.date: 03/30/2017
ms.assetid: e00827b3-7511-4b2d-91d7-851ca86cc6b5
ms.openlocfilehash: 4b7a3f16726d6363cd702fb912bb7be281a25000
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59192972"
---
# <a name="sql-server-binary-and-large-value-data"></a>SQL Server İkili ve Büyük Değerli Veriler
SQL Server sağlayan `max` depolama kapasitesini genişletir belirticisi `varchar`, `nvarchar`, ve `varbinary` veri türleri. `varchar(max)`, `nvarchar(max)`, ve `varbinary(max)` toplu olarak adlandırılır *büyük değerli veri türleri*. Büyük değerli veri türleri en fazla 2 depolamak için kullanabileceğiniz ^ 31-1 bayt veri.  
  
 SQL Server 2008 veritabanı yerine dosya sisteminde depolanmış büyük değerli veri sağlayan değil bir veri türü FILESTREAM özniteliğine, ancak bunun yerine bir sütuna, tanımlanan bir öznitelik tanıtır.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [ADO.NET İçinde Büyük Değerli (Maks) Verileri Değiştirme](../../../../../docs/framework/data/adonet/sql/modifying-large-value-max-data.md)  
 Büyük değerli veri türleriyle çalışır açıklar.  
  
 [FILESTREAM Verileri](../../../../../docs/framework/data/adonet/sql/filestream-data.md)  
 FILESTREAM özniteliğine SQL Server 2008'de depolanan büyük değerli veri ile nasıl çalışılacağını açıklar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [SQL Server Veri Türleri ve ADO.NET](../../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)
- [ADO.NET’te SQL Server Veri İşlemleri](../../../../../docs/framework/data/adonet/sql/sql-server-data-operations.md)
- [ADO.NET’te Veri Alma ve Değiştirme](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
