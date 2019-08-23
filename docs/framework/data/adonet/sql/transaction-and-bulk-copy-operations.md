---
title: İşlem ve Toplu Kopyalama İşlemleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f6f0cbc9-f7bf-4d6e-875f-ad1ba0b4aa62
ms.openlocfilehash: fb27e11f81451d6a982edcf5b88b23861bef3c37
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69938435"
---
# <a name="transaction-and-bulk-copy-operations"></a>İşlem ve Toplu Kopyalama İşlemleri
Toplu kopyalama işlemleri yalıtılmış işlemler olarak veya birden çok adımlı işlemin bir parçası olarak gerçekleştirilebilir. Bu ikinci seçenek aynı işlem içinde birden fazla toplu kopyalama işlemi gerçekleştirmenizi ve diğer veritabanı işlemlerini (ekleme, güncelleştirme ve silme gibi) gerçekleştirmeye devam ederken işlemin tamamını kaydetmeye veya geri almaya devam etmenize olanak sağlar.  
  
 Varsayılan olarak, toplu kopyalama işlemi yalıtılmış bir işlem olarak gerçekleştirilir. Toplu kopyalama işlemi, işlem temelli olmayan bir şekilde gerçekleşir ve geri alınması için hiçbir fırsat yoktur. Bir hata oluştuğunda toplu kopyalama işleminin tamamını veya bir kısmını geri almanız gerekiyorsa, yönetilen bir <xref:System.Data.SqlClient.SqlBulkCopy>işlem kullanabilir, toplu kopyalama işlemini var olan bir işlem içinde gerçekleştirebilir veya bir **System. Transactions**<xref:System.Transactions.Transaction>içinde listeye girebilirsiniz.  
  
## <a name="performing-a-non-transacted-bulk-copy-operation"></a>İşlem temelli olmayan toplu kopyalama Işlemi gerçekleştiriliyor  
 Aşağıdaki konsol uygulaması, işlem sırasında işlem sırasında bir hatayla karşılaştığında işlem temelli olmayan toplu kopyalama işlemi olduğunda ne olacağını gösterir.  
  
 Örnekte, kaynak tablo ve hedef tablo `Identity` **ProductID**adlı bir sütun içerir. Kod, ilk olarak tüm satırları silerek ve sonra **ProductID** 'nin kaynak tabloda bulunduğu bilinen tek bir satır ekleyerek hedef tabloyu hazırlar. Varsayılan olarak, `Identity` sütun için yeni bir değer, eklenen her satır için hedef tabloda oluşturulur. Bu örnekte, bağlantı açıldığında, toplu yükleme işlemini kaynak tablodaki `Identity` değerleri kullanmak üzere zorlayan bir seçenek ayarlanır.  
  
 Toplu kopyalama işlemi, <xref:System.Data.SqlClient.SqlBulkCopy.BatchSize%2A> özelliği 10 olarak ayarlanmış şekilde yürütülür. İşlem geçersiz bir satırla karşılaştığında, bir özel durum oluşturulur. Bu ilk örnekte toplu kopyalama işlemi işlem temelli değildir. Hatanın noktasına kopyalanmış tüm toplu işler kaydedilir; Yinelenen anahtarı içeren toplu işlem geri alınır ve toplu kopyalama işlemi başka hiçbir toplu işlem işlenmeden önce durdurulur.  
  
> [!NOTE]
> Bu örnek, [toplu kopyalama örnek kurulumu](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md)bölümünde açıklandığı gibi iş tablolarını oluşturmadığınız sürece çalıştırılmaz. Bu kod, yalnızca **SqlBulkCopy** kullanma sözdizimini göstermek için verilmiştir. Kaynak ve hedef tablolar aynı SQL Server örneğinde yer alıyorsa, verileri kopyalamak için Transact-SQL`INSERT … SELECT` ifadesinin kullanılması daha kolay ve hızlıdır.  
  
 [!code-csharp[DataWorks SqlBulkCopy.DefaultTransaction#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.DefaultTransaction/CS/source.cs#1)]
 [!code-vb[DataWorks SqlBulkCopy.DefaultTransaction#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.DefaultTransaction/VB/source.vb#1)]  
  
## <a name="performing-a-dedicated-bulk-copy-operation-in-a-transaction"></a>Bir Işlemde adanmış bir toplu kopyalama Işlemi gerçekleştirme  
 Varsayılan olarak, toplu kopyalama işlemi kendi hareketinden olur. Adanmış bir toplu kopyalama işlemi gerçekleştirmek istediğinizde, bir bağlantı dizesiyle yeni bir örneğini <xref:System.Data.SqlClient.SqlBulkCopy> oluşturun veya etkin bir işlem olmadan var olan <xref:System.Data.SqlClient.SqlConnection> bir nesneyi kullanın. Her senaryoda toplu kopyalama işlemi oluşturulur ve sonra işlemi tamamlar veya geri kaydeder.  
  
 Toplu kopyalama işleminin ayrı bir <xref:System.Data.SqlClient.SqlBulkCopyOptions.UseInternalTransaction> işlem içinde yürütülmesine <xref:System.Data.SqlClient.SqlBulkCopy> neden olacak şekilde, bir toplu kopyalama işleminin kendi işleminde yürütülmesine neden olacak şekilde sınıf oluşturucusunda seçeneğini açıkça belirtebilirsiniz.  
  
> [!NOTE]
> Farklı işlemler farklı işlemlerde yürütüldüğünden, toplu kopyalama işlemi sırasında bir hata oluşursa, geçerli toplu işteki tüm satırlar geri alınacaktır, ancak önceki toplu işlerin satırları veritabanında kalır.  
  
 Aşağıdaki konsol uygulaması, bir önceki örneğe benzer ve bir özel durumla benzerdir: Bu örnekte, toplu kopyalama işlemi kendi işlemlerini yönetir. Hatanın noktasına kopyalanmış tüm toplu işler kaydedilir; Yinelenen anahtarı içeren toplu işlem geri alınır ve toplu kopyalama işlemi başka hiçbir toplu işlem işlenmeden önce durdurulur.  
  
> [!IMPORTANT]
> Bu örnek, [toplu kopyalama örnek kurulumu](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md)bölümünde açıklandığı gibi iş tablolarını oluşturmadığınız sürece çalıştırılmaz. Bu kod, yalnızca **SqlBulkCopy** kullanma sözdizimini göstermek için verilmiştir. Kaynak ve hedef tablolar aynı SQL Server örneğinde yer alıyorsa, verileri kopyalamak için Transact-SQL`INSERT … SELECT` ifadesinin kullanılması daha kolay ve hızlıdır.  
  
 [!code-csharp[DataWorks SqlBulkCopy.InternalTransaction#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.InternalTransaction/CS/source.cs#1)]
 [!code-vb[DataWorks SqlBulkCopy.InternalTransaction#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.InternalTransaction/VB/source.vb#1)]  
  
## <a name="using-existing-transactions"></a>Mevcut Işlemleri kullanma  
 Bir <xref:System.Data.SqlClient.SqlBulkCopy> oluşturucuda bir parametre olarak <xref:System.Data.SqlClient.SqlTransaction> varolan bir nesne belirtebilirsiniz. Bu durumda, toplu kopyalama işlemi var olan bir işlemde gerçekleştirilir ve işlem durumunda hiçbir değişiklik yapılmaz (yani, hiçbir şekilde uygulanmaz veya durdurulmaz). Bu, bir uygulamanın toplu kopyalama işlemini diğer veritabanı işlemleriyle bir işleme eklemesine olanak tanır. Ancak, bir <xref:System.Data.SqlClient.SqlTransaction> nesnesi belirtmezseniz ve null bir başvuru geçirmezseniz ve bağlantı etkin bir işlem içeriyorsa, bir özel durum oluşturulur.  
  
 Bir hata oluşması nedeniyle toplu kopyalama işleminin tamamını geri almanız gerekiyorsa veya toplu kopyalama geri alınacak daha büyük bir işlemin parçası olarak yürütülegerekliyse, <xref:System.Data.SqlClient.SqlTransaction> <xref:System.Data.SqlClient.SqlBulkCopy> oluşturucuya bir nesne sağlayabilirsiniz.  
  
 Aşağıdaki konsol uygulaması, birinci (işlem temelli olmayan) örnekle benzerdir, tek bir istisna: Bu örnekte, toplu kopyalama işlemi daha büyük, dış bir işleme dahil edilmiştir. Birincil anahtar ihlali hatası oluştuğunda, tüm işlem geri alınır ve hedef tabloya hiçbir satır eklenmez.  
  
> [!IMPORTANT]
> Bu örnek, [toplu kopyalama örnek kurulumu](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md)bölümünde açıklandığı gibi iş tablolarını oluşturmadığınız sürece çalıştırılmaz. Bu kod, yalnızca **SqlBulkCopy** kullanma sözdizimini göstermek için verilmiştir. Kaynak ve hedef tablolar aynı SQL Server örneğinde yer alıyorsa, verileri kopyalamak için Transact-SQL`INSERT … SELECT` ifadesinin kullanılması daha kolay ve hızlıdır.  
  
 [!code-csharp[DataWorks SqlBulkCopy.SqlTransaction#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.SqlTransaction/CS/source.cs#1)]
 [!code-vb[DataWorks SqlBulkCopy.SqlTransaction#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.SqlTransaction/VB/source.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [SQL Server’da Toplu Kopyalama İşlemleri](../../../../../docs/framework/data/adonet/sql/bulk-copy-operations-in-sql-server.md)
- [ADO.NET yönetilen sağlayıcılar ve veri kümesi Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
