---
title: SQL Server’da Toplu Kopyalama İşlemleri
description: Büyük dosyaları SQL Server veritabanlarındaki tablolara veya görünümlere toplu olarak kopyalamanın yönetilen kod çözümlerini yazmak için SqlBulkCopy sınıfını kullanmayı öğrenin.
ms.date: 03/30/2017
ms.assetid: 83a7a0d2-8018-4354-97b9-0b1d99f8342b
ms.openlocfilehash: 43d63f3671ea8ff05da3e10580c2784fa3aae581
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91197437"
---
# <a name="bulk-copy-operations-in-sql-server"></a>SQL Server’da Toplu Kopyalama İşlemleri

Microsoft SQL Server, büyük dosyaları SQL Server veritabanlarındaki tablolara veya görünümlere hızlıca toplu olarak kopyalamak için **bcp** adlı popüler bir komut satırı yardımcı programı içerir. <xref:System.Data.SqlClient.SqlBulkCopy>Sınıfı, benzer işlevler sağlayan yönetilen kod çözümlerini yazmanızı sağlar. SQL Server tabloya veri yüklemek için başka yollar vardır (örneğin INSERT deyimleri), ancak <xref:System.Data.SqlClient.SqlBulkCopy> bunlar üzerinde önemli bir performans avantajı sunar.  
  
 <xref:System.Data.SqlClient.SqlBulkCopy>Sınıfı yalnızca SQL Server tablolarına veri yazmak için kullanılabilir. Ancak veri kaynağı SQL Server sınırlı değildir; veriler bir örneğe yüklene, <xref:System.Data.DataTable> ya da bir örnekle okunan sürece, herhangi bir veri kaynağı kullanılabilir <xref:System.Data.IDataReader> .  
  
 Sınıfını kullanarak şunları yapabilirsiniz <xref:System.Data.SqlClient.SqlBulkCopy> :  
  
- Tek bir toplu kopyalama işlemi  
  
- Birden çok toplu kopyalama işlemi  
  
- Bir işlem içindeki toplu kopyalama işlemi  
  
> [!NOTE]
> .NET Framework sürüm 1,1 veya önceki bir sürümü kullandığınızda ( <xref:System.Data.SqlClient.SqlBulkCopy> sınıfını desteklemeyen), nesneyi kullanarak SQL Server Transact-SQL **bulk INSERT** ifadesini çalıştırabilirsiniz <xref:System.Data.SqlClient.SqlCommand> .  
  
## <a name="in-this-section"></a>Bu Bölümde  

 [Toplu Kopyalama Örnek Kurulumu](bulk-copy-example-setup.md)  
 Toplu kopyalama örneklerinde kullanılan tabloları açıklar ve AdventureWorks veritabanında tabloları oluşturmak için SQL betikleri sağlar.  
  
 [Tekil Toplu Kopyalama İşlemleri](single-bulk-copy-operations.md)  
 Sınıfını kullanarak bir SQL Server örneğine verilerin tek bir toplu kopyasının nasıl yapılacağını <xref:System.Data.SqlClient.SqlBulkCopy> ve Transact-SQL deyimlerini ve sınıfını kullanarak toplu kopyalama işleminin nasıl gerçekleştirileceğini açıklar <xref:System.Data.SqlClient.SqlCommand> .  
  
 [Çoklu Toplu Kopyalama İşlemleri](multiple-bulk-copy-operations.md)  
 Sınıfını kullanarak bir SQL Server örneğine veri çoklu toplu kopyalama işlemlerinin nasıl yapılacağını açıklar <xref:System.Data.SqlClient.SqlBulkCopy> .  
  
 [İşlem ve Toplu Kopyalama İşlemleri](transaction-and-bulk-copy-operations.md)  
 İşlemin nasıl gerçekleştirileceği veya geri alınması dahil olmak üzere bir işlem içinde toplu kopyalama işleminin nasıl gerçekleştirileceğini açıklar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [SQL Server ve ADO.NET](index.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
