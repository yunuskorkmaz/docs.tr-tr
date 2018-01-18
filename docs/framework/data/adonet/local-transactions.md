---
title: "Yerel işlemler"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 8ae3712f-ef5e-41a1-9ea9-b3d0399439f1
caps.latest.revision: "5"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 3d7865675871bafb527bb9ee85de1f96e9847402
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="local-transactions"></a>Yerel işlemler
İşlemlerde [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] iş tek bir birim olarak execute birden çok görev birbirine bağlamak istediğinizde kullanılır. Örneğin, bir uygulama iki görevleri gerçekleştirir düşünün. İlk olarak, bir tablo sipariş bilgilerle güncelleştirir. İkinci olarak, Envanter bilgilerini içeren bir tablo güncelleştirmeleri, öğeleri borçlandırılacağı sıralı. Her iki görev başarısız olursa, güncelleştirmelerinin her ikisini de geri alınır.  
  
## <a name="determining-the-transaction-type"></a>İşlem türünü belirleme  
 Bir işlem tek aşamalı bir işlemdir ve veritabanı tarafından doğrudan gerçekleştirilir yerel bir işlem olarak kabul edilir. Bir işlem, bir işlem İzleyici tarafından düzenlenir ve işlem çözümlemesi için (örneğin, iki aşamalı kaydetme) yedek operatördür mekanizmaları kullanan bir dağıtılmış işlem olarak kabul edilir.  
  
 Her biri [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] veri sağlayıcıları sahip kendi `Transaction` yerel işlemler gerçekleştirmek için nesne. Bir SQL Server veritabanında gerçekleştirilecek bir işlem gerekiyorsa seçin bir <xref:System.Data.SqlClient> işlem. Bir Oracle hareket kullanmak <xref:System.Data.OracleClient> sağlayıcısı. Ayrıca, bir <xref:System.Data.Common.DbTransaction> işlemleri gerektirir sağlayıcısı bağımsız kod yazmak için kullanılabilir sınıfı.  
  
> [!NOTE]
>  Sunucuda gerçekleştirildiğinde işlemleri en iyi yoldur. Açık işlemleri kapsamlı kullanımını yapan bir SQL Server veritabanı ile çalışıyorsanız, Transact-SQL BEGIN TRANSACTION deyimiyle depolanmış yordam olarak yazma göz önünde bulundurun. Sunucu tarafı işlemleri gerçekleştirme hakkında daha fazla bilgi için SQL Server Books Online'a bakın.  
  
## <a name="performing-a-transaction-using-a-single-connection"></a>Tek bir bağlantı kullanarak işlem gerçekleştirme  
 İçinde [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)], işlemleri kontrol `Connection` nesnesi. Yerel bir işlemle başlatabilirsiniz `BeginTransaction` yöntemi. Bir işlem başlamıştır sonra bu işlemle komutta listeleme `Transaction` özelliği bir `Command` nesnesi. Ardından yürütün veya başarı veya başarısızlık işlem bileşenlerinin durumuna göre veri kaynağında yapılan değişiklikleri geri alma.  
  
> [!NOTE]
>  `EnlistDistributedTransaction` Yöntemi yerel bir işlem için kullanılmamalıdır.  
  
 İşlem kapsamını bağlantısı sınırlıdır. Aşağıdaki örnekte iki ayrı komutlarda oluşan açık bir işlem gerçekleştirir `try` bloğu. Komutlar Production.ScrapReason tabloya INSERT deyimleri AdventureWorks yürütülürken [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] hiçbir özel durumlar varsa, kaydedilmiş olan örnek veritabanı. Kodda `catch` blok yapar geri işlem bir özel durum varsa. İşlem iptal edildi veya işlem tamamlanmadan önce bağlantı kapatıldığında, onu otomatik olarak geri alınır.  
  
## <a name="example"></a>Örnek  
 Bir işlem gerçekleştirmek için aşağıdaki adımları izleyin.  
  
1.  Çağrı <xref:System.Data.SqlClient.SqlConnection.BeginTransaction%2A> yöntemi <xref:System.Data.SqlClient.SqlConnection> işlem başlangıcı işaretlemek için nesne. <xref:System.Data.SqlClient.SqlConnection.BeginTransaction%2A> Yöntemi işlem için bir başvuru döndürür. Bu başvuru atandığı <xref:System.Data.SqlClient.SqlCommand> işlemde listeye kayıtlı nesneler.  
  
2.  Ata `Transaction` nesnesini <xref:System.Data.SqlClient.SqlCommand.Transaction%2A> özelliği <xref:System.Data.SqlClient.SqlCommand> yürütülecek. Etkin bir işlem ile bir bağlantı üzerindeki bir komut yürütülürse ve `Transaction` nesnesi değil atanmış için `Transaction` özelliği `Command` nesnesi, bir özel durum oluşur.  
  
3.  Gerekli komutları yürütün.  
  
4.  Çağrı <xref:System.Data.SqlClient.SqlTransaction.Commit%2A> yöntemi <xref:System.Data.SqlClient.SqlTransaction> işlemi tamamlamak için nesne veya arama <xref:System.Data.SqlClient.SqlTransaction.Rollback%2A> işlem sona erdirmek için yöntem. Bağlantı kapalı veya önce ya da elden <xref:System.Data.SqlClient.SqlTransaction.Commit%2A> veya <xref:System.Data.SqlClient.SqlTransaction.Rollback%2A> yöntemleri yürütülen, işlem geri alındı.  
  
 Aşağıdaki kod örneğinde işlem mantığı kullanarak gösterilmektedir [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] Microsoft SQL Server ile.  
  
 [!code-csharp[DataWorks SqlTransaction.Local#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTransaction.Local/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTransaction.Local#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTransaction.Local/VB/source.vb#1)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İşlemler ve Eşzamanlılık](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)  
 [Dağıtılmış İşlemler](../../../../docs/framework/data/adonet/distributed-transactions.md)  
 [SQL Server ile System.Transactions Tümleştirmesi](../../../../docs/framework/data/adonet/system-transactions-integration-with-sql-server.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
