---
title: İşlem ve Toplu Kopyalama İşlemleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f6f0cbc9-f7bf-4d6e-875f-ad1ba0b4aa62
ms.openlocfilehash: 27fafc0ef45b80eddd993229f52d119b40b4956f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91155451"
---
# <a name="transaction-and-bulk-copy-operations"></a>İşlem ve Toplu Kopyalama İşlemleri

Toplu kopyalama işlemleri yalıtılmış işlemler olarak veya birden çok adımlı işlemin bir parçası olarak gerçekleştirilebilir. Bu ikinci seçenek aynı işlem içinde birden fazla toplu kopyalama işlemi gerçekleştirmenizi ve diğer veritabanı işlemlerini (ekleme, güncelleştirme ve silme gibi) gerçekleştirmeye devam ederken işlemin tamamını kaydetmeye veya geri almaya devam etmenize olanak sağlar.  
  
 Varsayılan olarak, toplu kopyalama işlemi yalıtılmış bir işlem olarak gerçekleştirilir. Toplu kopyalama işlemi, işlem temelli olmayan bir şekilde gerçekleşir ve geri alınması için hiçbir fırsat yoktur. Bir hata oluştuğunda toplu kopyalama işleminin tamamını veya bir kısmını geri almanız gerekiyorsa, <xref:System.Data.SqlClient.SqlBulkCopy> yönetilen bir işlem kullanabilir, toplu kopyalama işlemini var olan bir işlem içinde gerçekleştirebilir veya bir **System. Transactions**içinde listeye girebilirsiniz <xref:System.Transactions.Transaction> .  
  
## <a name="performing-a-non-transacted-bulk-copy-operation"></a>İşlem temelli olmayan toplu kopyalama Işlemi gerçekleştiriliyor  

 Aşağıdaki konsol uygulaması, işlem sırasında işlem sırasında bir hatayla karşılaştığında işlem temelli olmayan toplu kopyalama işlemi olduğunda ne olacağını gösterir.  
  
 Örnekte, kaynak tablo ve hedef tablo `Identity` **ProductID**adlı bir sütun içerir. Kod, ilk olarak tüm satırları silerek ve sonra **ProductID** 'nin kaynak tabloda bulunduğu bilinen tek bir satır ekleyerek hedef tabloyu hazırlar. Varsayılan olarak, sütun için yeni bir değer, `Identity` eklenen her satır için hedef tabloda oluşturulur. Bu örnekte, bağlantı açıldığında, toplu yükleme işlemini kaynak tablodaki değerleri kullanmak üzere zorlayan bir seçenek ayarlanır `Identity` .  
  
 Toplu kopyalama işlemi, <xref:System.Data.SqlClient.SqlBulkCopy.BatchSize%2A> özelliği 10 olarak ayarlanmış şekilde yürütülür. İşlem geçersiz bir satırla karşılaştığında, bir özel durum oluşturulur. Bu ilk örnekte toplu kopyalama işlemi işlem temelli değildir. Hatanın noktasına kopyalanmış tüm toplu işler kaydedilir; Yinelenen anahtarı içeren toplu işlem geri alınır ve toplu kopyalama işlemi başka hiçbir toplu işlem işlenmeden önce durdurulur.  
  
> [!NOTE]
> Bu örnek, [toplu kopyalama örnek kurulumu](bulk-copy-example-setup.md)bölümünde açıklandığı gibi iş tablolarını oluşturmadığınız sürece çalıştırılmaz. Bu kod, yalnızca **SqlBulkCopy** kullanma sözdizimini göstermek için verilmiştir. Kaynak ve hedef tablolar aynı SQL Server örneğinde yer alıyorsa, verileri kopyalamak için Transact-SQL ifadesinin kullanılması daha kolay ve hızlıdır `INSERT … SELECT` .  
  
 [!code-csharp[DataWorks SqlBulkCopy.DefaultTransaction#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.DefaultTransaction/CS/source.cs#1)]
 [!code-vb[DataWorks SqlBulkCopy.DefaultTransaction#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.DefaultTransaction/VB/source.vb#1)]  
  
## <a name="performing-a-dedicated-bulk-copy-operation-in-a-transaction"></a>Bir Işlemde adanmış bir toplu kopyalama Işlemi gerçekleştirme  

 Varsayılan olarak, toplu kopyalama işlemi kendi hareketinden olur. Adanmış bir toplu kopyalama işlemi gerçekleştirmek istediğinizde, bir bağlantı dizesiyle yeni bir örneğini oluşturun <xref:System.Data.SqlClient.SqlBulkCopy> veya etkin bir işlem olmadan var olan bir nesneyi kullanın <xref:System.Data.SqlClient.SqlConnection> . Her senaryoda toplu kopyalama işlemi oluşturulur ve sonra işlemi tamamlar veya geri kaydeder.  
  
 Toplu <xref:System.Data.SqlClient.SqlBulkCopyOptions.UseInternalTransaction> <xref:System.Data.SqlClient.SqlBulkCopy> kopyalama işleminin ayrı bir işlem içinde yürütülmesine neden olacak şekilde, bir toplu kopyalama işleminin kendi işleminde yürütülmesine neden olacak şekilde sınıf oluşturucusunda seçeneğini açıkça belirtebilirsiniz.  
  
> [!NOTE]
> Farklı işlemler farklı işlemlerde yürütüldüğünden, toplu kopyalama işlemi sırasında bir hata oluşursa, geçerli toplu işteki tüm satırlar geri alınacaktır, ancak önceki toplu işlerin satırları veritabanında kalır.  
  
 Aşağıdaki konsol uygulaması, bir önceki örneğe benzer ve tek bir özel durumla benzerdir: Bu örnekte, toplu kopyalama işlemi kendi işlemlerini yönetir. Hatanın noktasına kopyalanmış tüm toplu işler kaydedilir; Yinelenen anahtarı içeren toplu işlem geri alınır ve toplu kopyalama işlemi başka hiçbir toplu işlem işlenmeden önce durdurulur.  
  
> [!IMPORTANT]
> Bu örnek, [toplu kopyalama örnek kurulumu](bulk-copy-example-setup.md)bölümünde açıklandığı gibi iş tablolarını oluşturmadığınız sürece çalıştırılmaz. Bu kod, yalnızca **SqlBulkCopy** kullanma sözdizimini göstermek için verilmiştir. Kaynak ve hedef tablolar aynı SQL Server örneğinde yer alıyorsa, verileri kopyalamak için Transact-SQL ifadesinin kullanılması daha kolay ve hızlıdır `INSERT … SELECT` .  
  
 [!code-csharp[DataWorks SqlBulkCopy.InternalTransaction#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.InternalTransaction/CS/source.cs#1)]
 [!code-vb[DataWorks SqlBulkCopy.InternalTransaction#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.InternalTransaction/VB/source.vb#1)]  
  
## <a name="using-existing-transactions"></a>Mevcut Işlemleri kullanma  

 Bir <xref:System.Data.SqlClient.SqlTransaction> oluşturucuda bir parametre olarak varolan bir nesne belirtebilirsiniz <xref:System.Data.SqlClient.SqlBulkCopy> . Bu durumda, toplu kopyalama işlemi var olan bir işlemde gerçekleştirilir ve işlem durumunda hiçbir değişiklik yapılmaz (yani, hiçbir şekilde uygulanmaz veya durdurulmaz). Bu, bir uygulamanın toplu kopyalama işlemini diğer veritabanı işlemleriyle bir işleme eklemesine olanak tanır. Ancak, bir <xref:System.Data.SqlClient.SqlTransaction> nesnesi belirtmezseniz ve null bir başvuru geçirmezseniz ve bağlantı etkin bir işlem içeriyorsa, bir özel durum oluşturulur.  
  
 Bir hata oluşması nedeniyle toplu kopyalama işleminin tamamını geri almanız gerekiyorsa veya toplu kopyalama geri alınacak daha büyük bir işlemin parçası olarak yürütülegerekliyse, <xref:System.Data.SqlClient.SqlTransaction> oluşturucuya bir nesne sağlayabilirsiniz <xref:System.Data.SqlClient.SqlBulkCopy> .  
  
 Aşağıdaki konsol uygulaması, birinci (işlem temelli olmayan) örnekle benzerdir, tek bir istisna: Bu örnekte, toplu kopyalama işlemi daha büyük, dış bir işleme dahil edilmiştir. Birincil anahtar ihlali hatası oluştuğunda, tüm işlem geri alınır ve hedef tabloya hiçbir satır eklenmez.  
  
> [!IMPORTANT]
> Bu örnek, [toplu kopyalama örnek kurulumu](bulk-copy-example-setup.md)bölümünde açıklandığı gibi iş tablolarını oluşturmadığınız sürece çalıştırılmaz. Bu kod, yalnızca **SqlBulkCopy** kullanma sözdizimini göstermek için verilmiştir. Kaynak ve hedef tablolar aynı SQL Server örneğinde yer alıyorsa, verileri kopyalamak için Transact-SQL ifadesinin kullanılması daha kolay ve hızlıdır `INSERT … SELECT` .  
  
 [!code-csharp[DataWorks SqlBulkCopy.SqlTransaction#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.SqlTransaction/CS/source.cs#1)]
 [!code-vb[DataWorks SqlBulkCopy.SqlTransaction#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.SqlTransaction/VB/source.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [SQL Server’da Toplu Kopyalama İşlemleri](bulk-copy-operations-in-sql-server.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
