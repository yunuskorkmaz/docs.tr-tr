---
title: ADO.NET ve LINQ to SQL
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 49ac6da0-f2e1-46fa-963e-1b6dcb63fef7
ms.openlocfilehash: b47a46f9fd9ef3ef1935fa7a88c2e60fe80db09d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964139"
---
# <a name="adonet-and-linq-to-sql"></a>ADO.NET ve LINQ to SQL
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], ADO.NET teknolojisinin bir parçasıdır. Bu, ADO.NET sağlayıcı modeli tarafından sunulan hizmetleri temel alır. Bu nedenle, kodu [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] mevcut ADO.NET uygulamalarıyla karıştırabilir ve geçerli ADO.net çözümlerini uygulamasına [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]geçirebilirsiniz. Aşağıdaki çizim ilişkinin üst düzey bir görünümünü sağlar.  
  
 ![LINQ to SQL ve ADO.net](../../../../../../docs/framework/data/adonet/sql/linq/media/dlinq-3.png "DLinq_3")  
  
## <a name="connections"></a>Bağlantılar  
 Oluştururken var olan bir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.DataContext>ADO.net bağlantısı sağlayabilirsiniz. <xref:System.Data.Linq.DataContext> (Sorgular dahil) tüm işlemler bu sağlanmış bağlantıyı kullanır. Bağlantı zaten açıksa, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] bununla işiniz bittiğinde olduğu gibi bırakır.  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#4)]
 [!code-vb[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#4)]  
  
 Aşağıdaki kodda olduğu gibi, her zaman bağlantıya erişebilir ve <xref:System.Data.Linq.DataContext.Connection%2A> özelliğini kullanarak kendiniz kapatabilirsiniz:  
  
 [!code-csharp[DLinqAdoNet#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#1)]
 [!code-vb[DLinqAdoNet#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#1)]  
  
## <a name="transactions"></a>İşlemler  
 Uygulamanız işlemi zaten başlatmışsa ve <xref:System.Data.Linq.DataContext> istediğiniz zaman dahil olmak üzere kendi veritabanı işleminizi sağlayabilirsiniz. <xref:System.Data.Linq.DataContext>  
  
 .NET Framework ile işlem yapmanın tercih edilen yöntemi <xref:System.Transactions.TransactionScope> nesneyi kullanmaktır. Bu yaklaşımı kullanarak, veritabanları ve bellekte yerleşik diğer kaynak yöneticileri arasında çalışan dağıtılmış işlemler yapabilirsiniz. İşlem kapsamlarının başlaması için birkaç kaynak gerekir. Bunlar, kendilerini dağıtılmış işlemlere yalnızca işlemin kapsamı içinde birden çok bağlantı olduğunda yükseltir.  
  
 [!code-csharp[DLinqAdoNet#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#2)]
 [!code-vb[DLinqAdoNet#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#2)]  
  
 Bu yaklaşımı tüm veritabanları için kullanamazsınız. Örneğin, SqlClient bağlantısı, bir SQL Server 2000 sunucusuyla çalışırken sistem işlemlerini yükseltemezsiniz. Bunun yerine, kullanılan bir işlem kapsamını her gördüğünde tam ve dağıtılmış bir işlem için otomatik olarak listeler.  
  
## <a name="direct-sql-commands"></a>Doğrudan SQL komutları  
 Her zaman, <xref:System.Data.Linq.DataContext> gerçekleştirmek istediğiniz özelleştirilmiş görev için değişiklikleri sorgulama veya gönderme yeteneğinin yetersiz olduğu durumlarla karşılaşabilirsiniz. Bu durumlarda, <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> veritabanına SQL komutları vermek ve sorgu sonuçlarını nesnelere dönüştürmek için yöntemini kullanabilirsiniz.  
  
 Örneğin, `Customer` sınıfın verilerinin iki tabloya yayıldığını varsayın (customer1 ve customer2). Aşağıdaki sorgu bir `Customer` nesne dizisi döndürür:  
  
 [!code-csharp[DLinqAdoNet#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#3)]
 [!code-vb[DLinqAdoNet#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#3)]  
  
 Tablo sonuçlarındaki sütun adları, varlık sınıfınızın sütun özellikleriyle eşleştiği sürece, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nesnelerinizi herhangi bir SQL sorgusundan oluşturur.  
  
### <a name="parameters"></a>Parametreler  
 <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> Yöntemi parametreleri kabul eder. Aşağıdaki kod parametreli bir sorgu yürütür:  
  
 [!code-csharp[DlinqAdoNet#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#4)]
 [!code-vb[DlinqAdoNet#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#4)]  
  
> [!NOTE]
> Parametreler, ve `Console.WriteLine()` `String.Format()`tarafından kullanılan aynı süslü gösterimi kullanılarak sorgu metninde ifade edilir. `String.Format()`sağladığınız sorgu dizesini alır ve küme içi parametreleri `@p0`, `@p1` . `@p(n)`. gibi oluşturulmuş parametre adlarıyla değiştirir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Arka Plan Bilgileri](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
- [Nasıl yapılır: Bir ADO.NET komutu ve DataContext arasındaki bağlantıyı yeniden kullanma](../../../../../../docs/framework/data/adonet/sql/linq/how-to-reuse-a-connection-between-an-ado-net-command-and-a-datacontext.md)
