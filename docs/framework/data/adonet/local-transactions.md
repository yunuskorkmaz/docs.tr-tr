---
title: Yerel İşlemler
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8ae3712f-ef5e-41a1-9ea9-b3d0399439f1
ms.openlocfilehash: a0b713ab0b81cb2f0661212dae22db34b7f9f3ae
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91175401"
---
# <a name="local-transactions"></a>Yerel İşlemler

ADO.NET içindeki işlemler, tek bir iş birimi olarak yürütülmesi için birden çok görevi birbirine bağlamak istediğinizde kullanılır. Örneğin, bir uygulama iki görevleri gerçekleştirir düşünün. İlk olarak, sipariş bilgilerini içeren bir tabloyu günceller. İkinci olarak, sipariş edilen öğeleri borçlandırarak envanter bilgilerini içeren bir tabloyu günceller. Her iki görev başarısız olursa, her iki güncelleştirme de geri alınır.  
  
## <a name="determining-the-transaction-type"></a>Işlem türünü belirleme  

 Bir işlem, tek aşamalı bir işlem olduğunda ve veritabanı tarafından doğrudan işlendiği zaman yerel bir işlem olarak değerlendirilir. Bir işlem, bir işlem İzleyicisi tarafından koordine edildiğinde dağıtılmış bir işlem olarak kabul edilir ve işlem çözümlemesi için başarısız güvenli mekanizmalar (örneğin, iki aşamalı işleme) kullanır.  
  
 .NET Framework veri sağlayıcılarının her biri, `Transaction` Yerel işlemleri gerçekleştirmek için kendi nesnesine sahiptir. Bir SQL Server veritabanında gerçekleştirilecek bir işlem gerekiyorsa, bir <xref:System.Data.SqlClient> işlem seçin. Bir Oracle işlemi için <xref:System.Data.OracleClient> sağlayıcıyı kullanın. Ayrıca, <xref:System.Data.Common.DbTransaction> işlem gerektiren sağlayıcıya bağımsız kod yazmak için kullanılabilen bir sınıf vardır.  
  
> [!NOTE]
> İşlemler, sunucuda gerçekleştirildiklerinde en verimli yoldur. Açık işlemlerin kapsamlı kullanımını yapan bir SQL Server veritabanıyla çalışıyorsanız, Transact-SQL BEGIN TRANSACTION ifadesini kullanarak bunları saklı yordamlar olarak yazmayı göz önünde bulundurun.
  
## <a name="performing-a-transaction-using-a-single-connection"></a>Tek bir bağlantı kullanarak Işlem gerçekleştirme  

 ADO.NET içinde, nesne ile işlemleri kontrol edersiniz `Connection` . Yöntemiyle yerel işlem başlatabilirsiniz `BeginTransaction` . Bir işlem başladıktan sonra, bu işlem içindeki bir komutun bir nesnenin özelliği ile listelenmesi gerçekleştirebilirsiniz `Transaction` `Command` . Daha sonra veri kaynağında yapılan değişiklikleri işleme veya işlemin bileşenlerinin başarısını veya başarısızlığından sonra geri alabilirsiniz.  
  
> [!NOTE]
> `EnlistDistributedTransaction`Yöntemi yerel bir işlem için kullanılmamalıdır.  
  
 İşlemin kapsamı bağlantıyla sınırlıdır. Aşağıdaki örnek, bloktaki iki ayrı komuttan oluşan açık bir işlem gerçekleştirir `try` . Komutlar, özel durum oluşmayan bir istisna yoksa yürütülen AdventureWorks SQL Server örnek veritabanındaki Production. ScrapReason tablosuna göre INSERT deyimlerini yürütür. `catch`Bir özel durum oluşturulursa, bloktaki kod işlemi geri alır. İşlem iptal edilmişse veya işlem tamamlanmadan önce bağlantı kapalıysa, otomatik olarak geri alınır.  
  
## <a name="example"></a>Örnek  

 Bir işlem gerçekleştirmek için bu adımları izleyin.  
  
1. <xref:System.Data.SqlClient.SqlConnection.BeginTransaction%2A> <xref:System.Data.SqlClient.SqlConnection> İşlemin başlangıcını işaretlemek için nesnenin yöntemini çağırın. <xref:System.Data.SqlClient.SqlConnection.BeginTransaction%2A>Yöntemi, işleme bir başvuru döndürür. Bu başvuru <xref:System.Data.SqlClient.SqlCommand> , işlemde kayıtlı olan nesnelere atanır.  
  
2. `Transaction` <xref:System.Data.SqlClient.SqlCommand.Transaction%2A> Yürütülecek olan öğesinin özelliğine nesneyi atayın <xref:System.Data.SqlClient.SqlCommand> . Bir komut etkin bir işlem ile bağlantı üzerinde yürütülürse ve `Transaction` nesnesi `Transaction` nesnenin özelliğine atanmamışsa, `Command` bir özel durum oluşturulur.  
  
3. Gerekli komutları yürütün.  
  
4. <xref:System.Data.SqlClient.SqlTransaction.Commit%2A> <xref:System.Data.SqlClient.SqlTransaction> İşlemi gerçekleştirmek için nesnesinin yöntemini çağırın veya <xref:System.Data.SqlClient.SqlTransaction.Rollback%2A> işlemi sonlandırmak için yöntemi çağırın. Ya da yöntemleri yürütülmeden önce bağlantı kapatılırsa veya atıldıysa <xref:System.Data.SqlClient.SqlTransaction.Commit%2A> <xref:System.Data.SqlClient.SqlTransaction.Rollback%2A> , işlem geri alınır.  
  
 Aşağıdaki kod örneği, Microsoft SQL Server ile ADO.NET kullanarak işlem mantığını gösterir.  
  
 [!code-csharp[DataWorks SqlTransaction.Local#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTransaction.Local/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTransaction.Local#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTransaction.Local/VB/source.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İşlemler ve Eşzamanlılık](transactions-and-concurrency.md)
- [Dağıtılmış İşlemler](distributed-transactions.md)
- [SQL Server ile System.Transactions Tümleştirmesi](system-transactions-integration-with-sql-server.md)
- [ADO.NET’e Genel Bakış](ado-net-overview.md)
