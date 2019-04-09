---
title: SQL Server’da Toplu Kopyalama İşlemleri
ms.date: 03/30/2017
ms.assetid: 83a7a0d2-8018-4354-97b9-0b1d99f8342b
ms.openlocfilehash: 086b3b997cf0915be7cfa603a651eb412d52e985
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59194805"
---
# <a name="bulk-copy-operations-in-sql-server"></a>SQL Server’da Toplu Kopyalama İşlemleri
Microsoft SQL Server adlandırılmış bir popüler komut satırı yardımcı programını içeren **bcp** için hızlı bir şekilde toplu tabloları veya görünümleri SQL Server veritabanları ile büyük dosyaları kopyalanıyor. <xref:System.Data.SqlClient.SqlBulkCopy> Sınıfı benzer işlevler sağlayan çözümler yönetilen kod yazmanıza olanak verir. Verileri bir SQL Server tablosunu (örneğin, INSERT deyimleri) yüklemek için farklı yöntemleri vardır ancak <xref:System.Data.SqlClient.SqlBulkCopy> bir önemli performans avantajı onları sunar.  
  
 <xref:System.Data.SqlClient.SqlBulkCopy> Sınıfı, yalnızca SQL Server tablolarına veri yazmak için kullanılabilir. Ancak, veri kaynağı SQL Server için sınırlı değildir. için verilerin yüklenmesi sürece herhangi bir veri kaynağı kullanılabilir bir <xref:System.Data.DataTable> örneği veya ile okunan bir <xref:System.Data.IDataReader> örneği.  
  
 Kullanarak <xref:System.Data.SqlClient.SqlBulkCopy> sınıfı gerçekleştirebilirsiniz:  
  
-   Tekil toplu kopyalama işlemi  
  
-   Çoklu toplu kopyalama işlemleri  
  
-   Bir işlem içinde bir toplu kopyalama işlemi  
  
> [!NOTE]
>  .NET Framework sürüm 1.1 veya önceki bir sürümünü kullanırken (desteklemeyen <xref:System.Data.SqlClient.SqlBulkCopy> sınıfı), SQL Server Transact-SQL yürütmek **BULK INSERT** using deyimi <xref:System.Data.SqlClient.SqlCommand> nesne.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Toplu Kopyalama Örnek Kurulumu](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md)  
 Toplu kopyalama örneklerde kullanılan tablolar açıklar ve AdventureWorks veritabanı içinde tablolar oluşturmak için SQL komut dosyaları sağlar.  
  
 [Tekil Toplu Kopyalama İşlemleri](../../../../../docs/framework/data/adonet/sql/single-bulk-copy-operations.md)  
 SQL Server'ı kullanarak bir örneğine bir tekil toplu kopyalama veri bunu nasıl yapacağınız açıklanmaktadır <xref:System.Data.SqlClient.SqlBulkCopy> sınıfı ve Transact-SQL deyimlerini kullanarak toplu kopyalama işlemi gerçekleştirme ve <xref:System.Data.SqlClient.SqlCommand> sınıfı.  
  
 [Çoklu Toplu Kopyalama İşlemleri](../../../../../docs/framework/data/adonet/sql/multiple-bulk-copy-operations.md)  
 Çoklu toplu kopyalama işlemleri veri örneği SQL Server'ı kullanarak bunu nasıl yapacağınız açıklanmaktadır <xref:System.Data.SqlClient.SqlBulkCopy> sınıfı.  
  
 [İşlem ve Toplu Kopyalama İşlemleri](../../../../../docs/framework/data/adonet/sql/transaction-and-bulk-copy-operations.md)  
 Toplu kopyalama işlemi nasıl işleyin veya geri alma işlemi dahil olmak üzere, bir işlem içinde açıklar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [SQL Server ve ADO.NET](../../../../../docs/framework/data/adonet/sql/index.md)
- [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
