---
title: SQL Server’da Toplu Kopyalama İşlemleri
ms.date: 03/30/2017
ms.assetid: 83a7a0d2-8018-4354-97b9-0b1d99f8342b
ms.openlocfilehash: efa13eb1633fce3b59040ef8da79dba0f6ea81d5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918058"
---
# <a name="bulk-copy-operations-in-sql-server"></a>SQL Server’da Toplu Kopyalama İşlemleri
Microsoft SQL Server, büyük dosyaları SQL Server veritabanlarındaki tablolara veya görünümlere hızlıca toplu olarak kopyalamak için **bcp** adlı popüler bir komut satırı yardımcı programı içerir. Sınıfı <xref:System.Data.SqlClient.SqlBulkCopy> , benzer işlevler sağlayan yönetilen kod çözümlerini yazmanızı sağlar. SQL Server tabloya veri yüklemek için başka yollar vardır (örneğin INSERT deyimleri), ancak <xref:System.Data.SqlClient.SqlBulkCopy> bunlar üzerinde önemli bir performans avantajı sunar.  
  
 <xref:System.Data.SqlClient.SqlBulkCopy> Sınıfı yalnızca SQL Server tablolarına veri yazmak için kullanılabilir. Ancak veri kaynağı SQL Server sınırlı değildir; veriler bir <xref:System.Data.DataTable> örneğe yüklene, ya da bir <xref:System.Data.IDataReader> örnekle okunan sürece, herhangi bir veri kaynağı kullanılabilir.  
  
 <xref:System.Data.SqlClient.SqlBulkCopy> Sınıfını kullanarak şunları yapabilirsiniz:  
  
- Tek bir toplu kopyalama işlemi  
  
- Birden çok toplu kopyalama işlemi  
  
- Bir işlem içindeki toplu kopyalama işlemi  
  
> [!NOTE]
> .NET Framework sürüm 1,1 veya önceki bir sürümü kullandığınızda ( <xref:System.Data.SqlClient.SqlBulkCopy> sınıfını desteklemeyen), <xref:System.Data.SqlClient.SqlCommand> nesneyi kullanarak SQL Server Transact-SQL **bulk INSERT** ifadesini çalıştırabilirsiniz.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Toplu Kopyalama Örnek Kurulumu](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md)  
 Toplu kopyalama örneklerinde kullanılan tabloları açıklar ve AdventureWorks veritabanında tabloları oluşturmak için SQL betikleri sağlar.  
  
 [Tekil Toplu Kopyalama İşlemleri](../../../../../docs/framework/data/adonet/sql/single-bulk-copy-operations.md)  
 <xref:System.Data.SqlClient.SqlBulkCopy> Sınıfını kullanarak bir SQL Server örneğine verilerin tek bir toplu kopyasının nasıl yapılacağını ve Transact-SQL deyimlerini <xref:System.Data.SqlClient.SqlCommand> ve sınıfını kullanarak toplu kopyalama işleminin nasıl gerçekleştirileceğini açıklar.  
  
 [Çoklu Toplu Kopyalama İşlemleri](../../../../../docs/framework/data/adonet/sql/multiple-bulk-copy-operations.md)  
 <xref:System.Data.SqlClient.SqlBulkCopy> Sınıfını kullanarak bir SQL Server örneğine veri çoklu toplu kopyalama işlemlerinin nasıl yapılacağını açıklar.  
  
 [İşlem ve Toplu Kopyalama İşlemleri](../../../../../docs/framework/data/adonet/sql/transaction-and-bulk-copy-operations.md)  
 İşlemin nasıl gerçekleştirileceği veya geri alınması dahil olmak üzere bir işlem içinde toplu kopyalama işleminin nasıl gerçekleştirileceğini açıklar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [SQL Server ve ADO.NET](../../../../../docs/framework/data/adonet/sql/index.md)
- [ADO.NET yönetilen sağlayıcılar ve veri kümesi Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
