---
title: Yerel İşlemler
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8ae3712f-ef5e-41a1-9ea9-b3d0399439f1
ms.openlocfilehash: a0cb72913c10712ece188a782095b93f98cdc0b2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955780"
---
# <a name="local-transactions"></a>Yerel İşlemler
ADO.NET içindeki işlemler, tek bir iş birimi olarak yürütülmesi için birden çok görevi birbirine bağlamak istediğinizde kullanılır. Örneğin, bir uygulama iki görevleri gerçekleştirir düşünün. İlk olarak, sipariş bilgilerini içeren bir tabloyu günceller. İkinci olarak, sipariş edilen öğeleri borçlandırarak envanter bilgilerini içeren bir tabloyu günceller. Her iki görev başarısız olursa, her iki güncelleştirme de geri alınır.  
  
## <a name="determining-the-transaction-type"></a>Işlem türünü belirleme  
 Bir işlem, tek aşamalı bir işlem olduğunda ve veritabanı tarafından doğrudan işlendiği zaman yerel bir işlem olarak değerlendirilir. Bir işlem, bir işlem İzleyicisi tarafından koordine edildiğinde dağıtılmış bir işlem olarak kabul edilir ve işlem çözümlemesi için başarısız güvenli mekanizmalar (örneğin, iki aşamalı işleme) kullanır.  
  
 .NET Framework veri sağlayıcılarının her biri, yerel işlemleri gerçekleştirmek `Transaction` için kendi nesnesine sahiptir. Bir SQL Server veritabanında gerçekleştirilecek bir işlem gerekiyorsa, bir <xref:System.Data.SqlClient> işlem seçin. Bir Oracle işlemi için <xref:System.Data.OracleClient> sağlayıcıyı kullanın. Ayrıca, işlem gerektiren sağlayıcıya bağımsız <xref:System.Data.Common.DbTransaction> kod yazmak için kullanılabilen bir sınıf vardır.  
  
> [!NOTE]
> İşlemler, sunucuda gerçekleştirildiklerinde en verimli yoldur. Açık işlemlerin kapsamlı kullanımını yapan bir SQL Server veritabanıyla çalışıyorsanız, Transact-SQL BEGIN TRANSACTION ifadesini kullanarak bunları saklı yordamlar olarak yazmayı göz önünde bulundurun.
  
## <a name="performing-a-transaction-using-a-single-connection"></a>Tek bir bağlantı kullanarak Işlem gerçekleştirme  
 ADO.NET içinde, `Connection` nesne ile işlemleri kontrol edersiniz. `BeginTransaction` Yöntemiyle yerel işlem başlatabilirsiniz. Bir işlem başladıktan sonra, bu işlem içindeki bir komutun bir `Transaction` `Command` nesnenin özelliği ile listelenmesi gerçekleştirebilirsiniz. Daha sonra veri kaynağında yapılan değişiklikleri işleme veya işlemin bileşenlerinin başarısını veya başarısızlığından sonra geri alabilirsiniz.  
  
> [!NOTE]
> `EnlistDistributedTransaction` Yöntemi yerel bir işlem için kullanılmamalıdır.  
  
 İşlemin kapsamı bağlantıyla sınırlıdır. Aşağıdaki örnek, `try` bloktaki iki ayrı komuttan oluşan açık bir işlem gerçekleştirir. Komutlar, özel durum oluşmayan bir istisna yoksa yürütülen AdventureWorks SQL Server örnek veritabanındaki Production. ScrapReason tablosuna göre INSERT deyimlerini yürütür. Bir özel durum oluşturulursa `catch` , bloktaki kod işlemi geri alır. İşlem iptal edilmişse veya işlem tamamlanmadan önce bağlantı kapalıysa, otomatik olarak geri alınır.  
  
## <a name="example"></a>Örnek  
 Bir işlem gerçekleştirmek için bu adımları izleyin.  
  
1. İşlemin başlangıcını işaretlemek için <xref:System.Data.SqlClient.SqlConnection> nesnenin yönteminiçağırın.<xref:System.Data.SqlClient.SqlConnection.BeginTransaction%2A> <xref:System.Data.SqlClient.SqlConnection.BeginTransaction%2A> Yöntemi, işleme bir başvuru döndürür. Bu başvuru, işlemde kayıtlı olan <xref:System.Data.SqlClient.SqlCommand> nesnelere atanır.  
  
2. Yürütülecek olan öğesinin <xref:System.Data.SqlClient.SqlCommand.Transaction%2A> özelliğine<xref:System.Data.SqlClient.SqlCommand> nesneyi atayın. `Transaction` Bir komut etkin bir işlem ile bağlantı üzerinde yürütülürse ve `Transaction` nesnesi `Command` nesnenin `Transaction` özelliğine atanmamışsa, bir özel durum oluşturulur.  
  
3. Gerekli komutları yürütün.  
  
4. İşlemi gerçekleştirmek için <xref:System.Data.SqlClient.SqlTransaction> nesnesinin <xref:System.Data.SqlClient.SqlTransaction.Commit%2A> yöntemini çağırın veya işlemi sonlandırmak için yöntemi çağırın. <xref:System.Data.SqlClient.SqlTransaction.Rollback%2A> <xref:System.Data.SqlClient.SqlTransaction.Commit%2A> Ya<xref:System.Data.SqlClient.SqlTransaction.Rollback%2A> da yöntemleri yürütülmeden önce bağlantı kapatılırsa veya atıldıysa, işlem geri alınır.  
  
 Aşağıdaki kod örneği, Microsoft SQL Server ile ADO.NET kullanarak işlem mantığını gösterir.  
  
 [!code-csharp[DataWorks SqlTransaction.Local#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTransaction.Local/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTransaction.Local#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTransaction.Local/VB/source.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İşlemler ve Eşzamanlılık](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)
- [Dağıtılmış İşlemler](../../../../docs/framework/data/adonet/distributed-transactions.md)
- [SQL Server ile System.Transactions Tümleştirmesi](../../../../docs/framework/data/adonet/system-transactions-integration-with-sql-server.md)
- [ADO.NET yönetilen sağlayıcılar ve veri kümesi Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
