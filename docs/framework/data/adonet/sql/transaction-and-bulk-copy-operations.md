---
title: İşlem ve toplu kopyalama işlemleri
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: f6f0cbc9-f7bf-4d6e-875f-ad1ba0b4aa62
caps.latest.revision: 4
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: 40494c887ffa48c6ebc7f020cb4d42eecbd08e75
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="transaction-and-bulk-copy-operations"></a>İşlem ve toplu kopyalama işlemleri
Toplu kopyalama işlemleri yalıtılmış operations veya birden çok adım işlemin parçası olarak gerçekleştirilebilir. Bu ikinci seçeneği yanı sıra aynı işlem içinde birden fazla toplu kopyalama işlemi gerçekleştirmek diğer veritabanı (örneğin, ekleme, güncelleştirme ve silme) hala yürütün veya işlemin tamamını geri kullanabilmeye devam ederken işlemleri sağlar.  
  
 Varsayılan olarak, yalıtılmış bir işlem olarak bir toplu kopyalama işlemi gerçekleştirilir. Toplu kopyalama işlemi geri alma için fırsat ile işlem temelli olmayan bir şekilde gerçekleşir. Hata oluştuğunda toplu kopyalama bölümünü veya tümünü geri almak gerekiyorsa, kullanabileceğiniz bir <xref:System.Data.SqlClient.SqlBulkCopy>-yönetilen işlem, var olan bir işlem içinde toplu kopyalama işlemi veya içinde kayıtlı bir **System.Transactions** <xref:System.Transactions.Transaction>.  
  
## <a name="performing-a-non-transacted-bulk-copy-operation"></a>Bir toplu işlem temelli olmayan kopyalama işlemi gerçekleştirme  
 Aşağıdaki konsol uygulaması işlem temelli olmayan toplu kopyalama işleminin kadar işlemle bir hatayla karşılaştığında ne olacağını gösterir.  
  
 Örnekte, kaynak tablosu ve hedef tablo içeren bir `Identity` adlı sütun **ProductID**. İlk kod tüm satırları silerek hedef tablo hazırlar ve tek bir ekleme, satır özelliği **ProductID** kaynak tablo mevcut bilinmektedir. Varsayılan olarak, yeni bir değer için `Identity` sütunu hedef tabloda eklenen her satır için oluşturulur. Bağlantı kullanmak için toplu yükleme işlemi zorlayan açıldığında, bu örnekte, bir seçenek kümesi `Identity` bunun yerine kaynak tablosundan değerleri.  
  
 Toplu kopyalama işlemi ile yürütülür <xref:System.Data.SqlClient.SqlBulkCopy.BatchSize%2A> özelliği 10 olarak ayarlandı. İşlemi geçersiz satır karşılaştığında, özel durum oluşur. Bu ilk, toplu kopyalama işleminin işlem temelli olmayan örneğidir. Tüm toplu hata noktaya kadar kopyalanan uygulanır; Yinelenen anahtar içeren toplu geri alınır ve başka bir toplu işlemeden önce toplu kopyalama işlemi durdu.  
  
> [!NOTE]
>  Bölümünde açıklandığı gibi iş tabloları oluşturmadıysanız Bu örnek çalışmaz [toplu kopyalama örnek Kurulum](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md). Bu kodu kullanarak söz dizimi göstermek için sağlanan **SqlBulkCopy** yalnızca. Kaynak ve hedef tablolar aynı SQL Server örneğinde bulunuyorsa, daha kolay ve hızlı kullanmak için bunu bir [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] `INSERT … SELECT` verileri kopyalamak için deyimi.  
  
 [!code-csharp[DataWorks SqlBulkCopy.DefaultTransaction#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.DefaultTransaction/CS/source.cs#1)]
 [!code-vb[DataWorks SqlBulkCopy.DefaultTransaction#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.DefaultTransaction/VB/source.vb#1)]  
  
## <a name="performing-a-dedicated-bulk-copy-operation-in-a-transaction"></a>Bir işlemde ayrılmış toplu kopyalama işlemi gerçekleştirme  
 Varsayılan olarak, toplu kopyalama işleminin kendi işlem ' dir. Ayrılmış toplu kopyalama işlemi gerçekleştirmek istediğiniz zaman yeni bir örneğini oluşturmak <xref:System.Data.SqlClient.SqlBulkCopy> bir bağlantı dizesi veya var olan kullanım <xref:System.Data.SqlClient.SqlConnection> etkin bir işlem olmadan nesnesi. Her senaryoda toplu kopyalama işlemi oluşturur ve ardından kaydeder veya geri işlem yapar.  
  
 Açıkça belirtebilirsiniz <xref:System.Data.SqlClient.SqlBulkCopyOptions.UseInternalTransaction> seçeneğini <xref:System.Data.SqlClient.SqlBulkCopy> açıkça her toplu iş içinde ayrı bir işlemde yürütmek için toplu kopyalama işleminin neden kendi işlemi yürütmek toplu kopyalama işleminin neden sınıfı oluşturucusu.  
  
> [!NOTE]
>  Toplu kopyalama işlemi sırasında bir hata oluşursa, farklı işlemlerde farklı toplu çalıştırıldığından, geçerli toplu işlem içindeki tüm satırların geri alındı, ancak önceki toplu satırları veritabanında kalır.  
  
 Aşağıdaki konsol uygulaması, önceki örnekte, bir özel durum dışında benzerdir: Bu örnekte, kendi işlemleri toplu kopyalama işlemi yönetir. Tüm toplu hata noktaya kadar kopyalanan uygulanır; Yinelenen anahtar içeren toplu geri alınır ve başka bir toplu işlemeden önce toplu kopyalama işlemi durdu.  
  
> [!IMPORTANT]
>  Bölümünde açıklandığı gibi iş tabloları oluşturmadıysanız Bu örnek çalışmaz [toplu kopyalama örnek Kurulum](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md). Bu kodu kullanarak söz dizimi göstermek için sağlanan **SqlBulkCopy** yalnızca. Kaynak ve hedef tablolar aynı SQL Server örneğinde bulunuyorsa, daha kolay ve hızlı kullanmak için bunu bir [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] `INSERT … SELECT` verileri kopyalamak için deyimi.  
  
 [!code-csharp[DataWorks SqlBulkCopy.InternalTransaction#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.InternalTransaction/CS/source.cs#1)]
 [!code-vb[DataWorks SqlBulkCopy.InternalTransaction#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.InternalTransaction/VB/source.vb#1)]  
  
## <a name="using-existing-transactions"></a>Varolan işlemleri kullanma  
 Var olan belirtebilirsiniz <xref:System.Data.SqlClient.SqlTransaction> nesnesini parametre olarak bir <xref:System.Data.SqlClient.SqlBulkCopy> Oluşturucusu. Bu durumda, mevcut bir işlemde toplu kopyalama işlemi gerçekleştirilir ve işlem durumu bir değişiklik (diğer bir deyişle, kaydedilen iptal ne). Bu, diğer veritabanı işlemleri olan bir işlemde toplu kopyalama işlemi eklenecek bir uygulama sağlar. Ancak, siz belirtmezseniz, bir <xref:System.Data.SqlClient.SqlTransaction> nesne ve geçişi bir null başvuru ve bağlantısı etkin bir işlem olan, bir özel durum.  
  
 Geri alma gerekiyorsa tüm toplu bir hata oluşursa veya toplu kopyalama geri alınamaz daha büyük bir işleminin bir parçası yürütmesini istiyorsanız sağlayabilir, işlemi kopyalama bir <xref:System.Data.SqlClient.SqlTransaction> nesnesine <xref:System.Data.SqlClient.SqlBulkCopy> Oluşturucusu.  
  
 Aşağıdaki konsol uygulaması ilk (işlem temelli olmayan) örnek, bir özel durum dışında benzerdir: Bu örnekte, daha büyük ve dış işlemde toplu kopyalama işlemi eklenmiştir. Birincil anahtar ihlali hata oluştuğunda, tüm işlem geri alındı ve hiçbir satır hedef tabloya eklenir.  
  
> [!IMPORTANT]
>  Bölümünde açıklandığı gibi iş tabloları oluşturmadıysanız Bu örnek çalışmaz [toplu kopyalama örnek Kurulum](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md). Bu kodu kullanarak söz dizimi göstermek için sağlanan **SqlBulkCopy** yalnızca. Kaynak ve hedef tablolar aynı SQL Server örneğinde bulunuyorsa, daha kolay ve hızlı kullanmak için bunu bir [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] `INSERT … SELECT` verileri kopyalamak için deyimi.  
  
 [!code-csharp[DataWorks SqlBulkCopy.SqlTransaction#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.SqlTransaction/CS/source.cs#1)]
 [!code-vb[DataWorks SqlBulkCopy.SqlTransaction#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.SqlTransaction/VB/source.vb#1)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [SQL Server’da Toplu Kopyalama İşlemleri](../../../../../docs/framework/data/adonet/sql/bulk-copy-operations-in-sql-server.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
