---
title: İşlem ve Toplu Kopyalama İşlemleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f6f0cbc9-f7bf-4d6e-875f-ad1ba0b4aa62
ms.openlocfilehash: f30974e020545a69ad20c03bc05ac6a28f289b01
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59074631"
---
# <a name="transaction-and-bulk-copy-operations"></a>İşlem ve Toplu Kopyalama İşlemleri
Toplu kopyalama işlemleri birden çok adım işlemlerinin bir parçası olarak veya yalıtılmış işlemleri gerçekleştirilebilir. Bu ikinci seçeneği yanı sıra aynı işlem içinde birden fazla toplu kopyalama işlemini gerçekleştirmek hala işleme ya da işlemin tümü geri olmanın yanı sıra (örneğin, ekleme, güncelleştirme ve silme) diğer veritabanı işlemlerini gerçekleştirmek sağlar.  
  
 Varsayılan olarak, toplu kopyalama işlemi, yalıtılmış bir işlem olarak gerçekleştirilir. Toplu kopyalama işlemi geri alma için fırsat ile işlem temelli olmayan bir şekilde gerçekleşir. Bir hata oluştuğunda toplu kopyalama bir kısmını veya tamamını geri alma gerekiyorsa, kullanabileceğiniz bir <xref:System.Data.SqlClient.SqlBulkCopy>-yönetilen işlem, toplu kopyalama işlemi var olan bir işlem içinde ya da kayıtlı bir **System.Transactions** <xref:System.Transactions.Transaction>.  
  
## <a name="performing-a-non-transacted-bulk-copy-operation"></a>Bir işlem temelli olmayan toplu kopyalama işlemi gerçekleştirme  
 Aşağıdaki konsol uygulamasında, bir işlem temelli olmayan toplu kopyalama işlemi kadar işlemle bir hatayla karşılaştığında ne olacağını gösterir.  
  
 Örnekte, kaynak tablosu ve hedef tablo içeren bir `Identity` adlı sütun **ProductID**. İlk kod tüm satırları silerek hedef tablo hazırlar ve sonra tek bir ekleme, satır ayarlanmış **ProductID** kaynak tablosunda bilinmektedir. Varsayılan olarak, yeni bir değer için `Identity` sütunu hedef tabloda eklenen her satır için oluşturulur. Bu örnekte, bir seçenek ayarlanır, bu bağlantıyı kullanmak için toplu yükleme işlemi zorlayan açıldığında `Identity` bunun yerine kaynak tablosundan değerleri.  
  
 Toplu kopyalama işlemi ile yürütülür <xref:System.Data.SqlClient.SqlBulkCopy.BatchSize%2A> özelliği 10'a ayarlayın. İşlemi geçersiz satır karşılaştığında, bir özel durum oluşturulur. Bu ilk örnekte, işlem temelli olmayan toplu kopyalama işlemi. Hata noktası kadar kopyalanan tüm toplu kaydedilmiş; Yinelenen anahtar içeren toplu geri alınır ve başka bir toplu işlemler işlenmeden önce toplu kopyalama işlemi durduruldu.  
  
> [!NOTE]
>  Bu örnekte açıklandığı gibi çalışma tabloları oluşturmadığınız sürece çalışmaz [toplu kopyalama örnek Kurulumu](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md). Bu kodu kullanmaya ilişkin sözdizimini göstermek için sağlanan **SqlBulkCopy** yalnızca. Kaynak ve hedef tablo aynı SQL Server örneğinde bulunuyorsa daha kolay ve daha hızlı kullanmak için bunu bir [!INCLUDE[tsql](../../../../../includes/tsql-md.md)]`INSERT … SELECT` verileri kopyalamak için deyimi.  
  
 [!code-csharp[DataWorks SqlBulkCopy.DefaultTransaction#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.DefaultTransaction/CS/source.cs#1)]
 [!code-vb[DataWorks SqlBulkCopy.DefaultTransaction#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.DefaultTransaction/VB/source.vb#1)]  
  
## <a name="performing-a-dedicated-bulk-copy-operation-in-a-transaction"></a>Bir işlemde bir adanmış toplu kopyalama işlemi gerçekleştirme  
 Varsayılan olarak, toplu kopyalama işlemi kendi işlemdir. Adanmış toplu kopyalama işlemini gerçekleştirmek istediğinizde, yeni bir örneğini oluşturma <xref:System.Data.SqlClient.SqlBulkCopy> bağlantı dizesi ya da mevcut bir kullanım ile <xref:System.Data.SqlClient.SqlConnection> etkin bir işlem olmadan nesne. Her bir senaryoda, toplu kopyalama işlemi oluşturur ve ardından kaydeder veya geri işlem yapar.  
  
 Açıkça belirtebilirsiniz <xref:System.Data.SqlClient.SqlBulkCopyOptions.UseInternalTransaction> seçeneğini <xref:System.Data.SqlClient.SqlBulkCopy> sınıf oluşturucusu her toplu işin ayrı bir işlem içinde çalıştırmak için toplu kopyalama işleminin neden kendi işlemde çalıştırmak bir toplu kopyalama işlemi açıkça neden olacak.  
  
> [!NOTE]
>  Toplu kopyalama işlemi sırasında bir hata oluşursa, farklı işlemlerde farklı toplu çalıştırıldığından, geçerli toplu işlemdeki tüm satırları geri alınır, ancak önceki toplu işlerin satırlardan veritabanında kalır.  
  
 Aşağıdaki konsol uygulamasında, bir özel durum dışında önceki örneğe benzer: Bu örnekte, toplu kopyalama işlemi kendi işlemleri yönetir. Hata noktası kadar kopyalanan tüm toplu kaydedilmiş; Yinelenen anahtar içeren toplu geri alınır ve başka bir toplu işlemler işlenmeden önce toplu kopyalama işlemi durduruldu.  
  
> [!IMPORTANT]
>  Bu örnekte açıklandığı gibi çalışma tabloları oluşturmadığınız sürece çalışmaz [toplu kopyalama örnek Kurulumu](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md). Bu kodu kullanmaya ilişkin sözdizimini göstermek için sağlanan **SqlBulkCopy** yalnızca. Kaynak ve hedef tablo aynı SQL Server örneğinde bulunuyorsa daha kolay ve daha hızlı kullanmak için bunu bir [!INCLUDE[tsql](../../../../../includes/tsql-md.md)]`INSERT … SELECT` verileri kopyalamak için deyimi.  
  
 [!code-csharp[DataWorks SqlBulkCopy.InternalTransaction#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.InternalTransaction/CS/source.cs#1)]
 [!code-vb[DataWorks SqlBulkCopy.InternalTransaction#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.InternalTransaction/VB/source.vb#1)]  
  
## <a name="using-existing-transactions"></a>Var olan işlemleri kullanma  
 Mevcut bir belirtebilirsiniz <xref:System.Data.SqlClient.SqlTransaction> nesnesi bir parametre olarak bir <xref:System.Data.SqlClient.SqlBulkCopy> Oluşturucusu. Bu durumda, var olan bir işlemde toplu kopyalama işlemi gerçekleştirilir ve işlem durumu için hiçbir değişiklik (diğer bir deyişle, kaydedilen iptal ne). Bu, diğer veritabanı işlemleri ile bir işlemde toplu kopyalama işlemi eklemek bir uygulama sağlar. Ancak, belirtmezseniz, bir <xref:System.Data.SqlClient.SqlTransaction> nesne ve geçişi bir null başvurusu ve bağlantısı etkin bir işlem olduğundan, bir özel durum oluşturulur.  
  
 Geri almak ihtiyacınız varsa tüm toplu bir hata oluşursa veya toplu kopyalama geri alınması daha büyük bir işleminin bir parçası yürütülecek, sağlayabilir olduğundan, işlem kopyalama bir <xref:System.Data.SqlClient.SqlTransaction> nesnesini <xref:System.Data.SqlClient.SqlBulkCopy> Oluşturucusu.  
  
 Aşağıdaki konsol uygulamasında örneğe benzer şekilde ilk (işlem temelli olmayan), bir özel durum: Bu örnekte, bir büyük, dış işlemde toplu kopyalama işlemi dahildir. Birincil anahtar ihlali hatası oluştuğunda, işlemin tümü geri alınır ve hiçbir satırları hedef tabloya eklenir.  
  
> [!IMPORTANT]
>  Bu örnekte açıklandığı gibi çalışma tabloları oluşturmadığınız sürece çalışmaz [toplu kopyalama örnek Kurulumu](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md). Bu kodu kullanmaya ilişkin sözdizimini göstermek için sağlanan **SqlBulkCopy** yalnızca. Kaynak ve hedef tablo aynı SQL Server örneğinde bulunuyorsa daha kolay ve daha hızlı kullanmak için bunu bir [!INCLUDE[tsql](../../../../../includes/tsql-md.md)]`INSERT … SELECT` verileri kopyalamak için deyimi.  
  
 [!code-csharp[DataWorks SqlBulkCopy.SqlTransaction#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.SqlTransaction/CS/source.cs#1)]
 [!code-vb[DataWorks SqlBulkCopy.SqlTransaction#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.SqlTransaction/VB/source.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [SQL Server’da Toplu Kopyalama İşlemleri](../../../../../docs/framework/data/adonet/sql/bulk-copy-operations-in-sql-server.md)
- [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
