---
title: "SQL Server toplu kopyalama işlemleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 83a7a0d2-8018-4354-97b9-0b1d99f8342b
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 31da2fbc7dca4c0c2c077991ddec39e8979b08b3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="bulk-copy-operations-in-sql-server"></a>SQL Server toplu kopyalama işlemleri
Microsoft SQL Server adlandırılmış popüler bir komut satırı yardımcı programını içeren **bcp** için hızlı bir şekilde toplu tabloları ve görünümleri SQL Server veritabanlarını içine büyük dosyaların kopyalanması. <xref:System.Data.SqlClient.SqlBulkCopy> Sınıfı benzer işlevler sağlayan yönetilen kod çözümleri yazmanıza olanak verir. Verileri bir SQL Server tabloya (örneğin, INSERT deyimleri) yüklemek için başka yolları vardır, ancak <xref:System.Data.SqlClient.SqlBulkCopy> bunları üzerinde önemli performans avantaj sunar.  
  
 <xref:System.Data.SqlClient.SqlBulkCopy> Sınıfı, yalnızca SQL Server tablolarına veri yazmak için kullanılabilir. Ancak, veri kaynağı SQL Server'a sınırlı değildir; verileri için yüklenebilir sürece herhangi bir veri kaynağı kullanılabilir bir <xref:System.Data.DataTable> örneği veya okumasını bir <xref:System.Data.IDataReader> örneği.  
  
 Kullanarak <xref:System.Data.SqlClient.SqlBulkCopy> sınıfı, gerçekleştirebilirsiniz:  
  
-   Bir tek toplu kopyalama işlemi  
  
-   Birden çok toplu kopyalama işlemleri  
  
-   Bir işlem içinde toplu kopyalama işlemi  
  
> [!NOTE]
>  .NET Framework sürüm 1.1 veya önceki bir sürümünü kullanırken (desteklemeyen <xref:System.Data.SqlClient.SqlBulkCopy> sınıfı), SQL Server Transact-SQL yürütebilir **BULK INSERT** deyimiyle <xref:System.Data.SqlClient.SqlCommand> nesnesi.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Toplu kopyalama örnek Kurulumu](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md)  
 Toplu kopyalama örneklerde kullanılan tablolar açıklar ve tabloları AdventureWorks veritabanını oluşturmak için SQL komut dosyaları sağlar.  
  
 [Tek toplu kopyalama işlemleri](../../../../../docs/framework/data/adonet/sql/single-bulk-copy-operations.md)  
 SQL Server'ı kullanarak, bir örneğine tek toplu kopyalama veri yapmak açıklar <xref:System.Data.SqlClient.SqlBulkCopy> sınıfı ve Transact-SQL deyimlerini kullanarak toplu kopyalama işlemi gerçekleştirme ve <xref:System.Data.SqlClient.SqlCommand> sınıfı.  
  
 [Birden çok toplu kopyalama işlemleri](../../../../../docs/framework/data/adonet/sql/multiple-bulk-copy-operations.md)  
 Birden çok toplu kopyalama işlemleri veri SQL Server'ı kullanarak bir örneğini içine nasıl açıklar <xref:System.Data.SqlClient.SqlBulkCopy> sınıfı.  
  
 [İşlem ve toplu kopyalama işlemleri](../../../../../docs/framework/data/adonet/sql/transaction-and-bulk-copy-operations.md)  
 Toplu kopyalama işlemi nasıl yürütme veya geri alma işlemi de dahil olmak üzere bir işlem içinde açıklar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [SQL Server ve ADO.NET](../../../../../docs/framework/data/adonet/sql/index.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
