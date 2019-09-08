---
title: SQL Server’da Toplu Kopyalama İşlemleri
ms.date: 03/30/2017
ms.assetid: 83a7a0d2-8018-4354-97b9-0b1d99f8342b
ms.openlocfilehash: ae97bcdd6776d573cf9e523133c2c00a42c273bb
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782531"
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
 [Toplu Kopyalama Örnek Kurulumu](bulk-copy-example-setup.md)  
 Toplu kopyalama örneklerinde kullanılan tabloları açıklar ve AdventureWorks veritabanında tabloları oluşturmak için SQL betikleri sağlar.  
  
 [Tekil Toplu Kopyalama İşlemleri](single-bulk-copy-operations.md)  
 <xref:System.Data.SqlClient.SqlBulkCopy> Sınıfını kullanarak bir SQL Server örneğine verilerin tek bir toplu kopyasının nasıl yapılacağını ve Transact-SQL deyimlerini <xref:System.Data.SqlClient.SqlCommand> ve sınıfını kullanarak toplu kopyalama işleminin nasıl gerçekleştirileceğini açıklar.  
  
 [Çoklu Toplu Kopyalama İşlemleri](multiple-bulk-copy-operations.md)  
 <xref:System.Data.SqlClient.SqlBulkCopy> Sınıfını kullanarak bir SQL Server örneğine veri çoklu toplu kopyalama işlemlerinin nasıl yapılacağını açıklar.  
  
 [İşlem ve Toplu Kopyalama İşlemleri](transaction-and-bulk-copy-operations.md)  
 İşlemin nasıl gerçekleştirileceği veya geri alınması dahil olmak üzere bir işlem içinde toplu kopyalama işleminin nasıl gerçekleştirileceğini açıklar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [SQL Server ve ADO.NET](index.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
