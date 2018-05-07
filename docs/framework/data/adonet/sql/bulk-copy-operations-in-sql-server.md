---
title: SQL Server toplu kopyalama işlemleri
ms.date: 03/30/2017
ms.assetid: 83a7a0d2-8018-4354-97b9-0b1d99f8342b
ms.openlocfilehash: 87373f55181742a243c60bc4b471334535d88ff7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
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
 [Toplu Kopyalama Örnek Kurulumu](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md)  
 Toplu kopyalama örneklerde kullanılan tablolar açıklar ve tabloları AdventureWorks veritabanını oluşturmak için SQL komut dosyaları sağlar.  
  
 [Tekil Toplu Kopyalama İşlemleri](../../../../../docs/framework/data/adonet/sql/single-bulk-copy-operations.md)  
 SQL Server'ı kullanarak, bir örneğine tek toplu kopyalama veri yapmak açıklar <xref:System.Data.SqlClient.SqlBulkCopy> sınıfı ve Transact-SQL deyimlerini kullanarak toplu kopyalama işlemi gerçekleştirme ve <xref:System.Data.SqlClient.SqlCommand> sınıfı.  
  
 [Çoklu Toplu Kopyalama İşlemleri](../../../../../docs/framework/data/adonet/sql/multiple-bulk-copy-operations.md)  
 Birden çok toplu kopyalama işlemleri veri SQL Server'ı kullanarak bir örneğini içine nasıl açıklar <xref:System.Data.SqlClient.SqlBulkCopy> sınıfı.  
  
 [İşlem ve Toplu Kopyalama İşlemleri](../../../../../docs/framework/data/adonet/sql/transaction-and-bulk-copy-operations.md)  
 Toplu kopyalama işlemi nasıl yürütme veya geri alma işlemi de dahil olmak üzere bir işlem içinde açıklar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [SQL Server ve ADO.NET](../../../../../docs/framework/data/adonet/sql/index.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
