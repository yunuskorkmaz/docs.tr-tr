---
description: 'Hakkında daha fazla bilgi edinin: ADO.NET ve LINQ to SQL'
title: ADO.NET ve LINQ to SQL
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 49ac6da0-f2e1-46fa-963e-1b6dcb63fef7
ms.openlocfilehash: 1f3f4a50c13af857ecd9f3195c7f431dd46ed3ee
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99712967"
---
# <a name="adonet-and-linq-to-sql"></a>ADO.NET ve LINQ to SQL

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] , ADO.NET teknolojisinin bir parçasıdır. Bu, ADO.NET sağlayıcı modeli tarafından sunulan hizmetleri temel alır. Bu nedenle, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] kodu mevcut ADO.NET uygulamalarıyla karıştırabilir ve geçerli ADO.net çözümlerini uygulamasına geçirebilirsiniz [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] . Aşağıdaki çizim ilişkinin üst düzey bir görünümünü sağlar.  
  
 ![LINQ to SQL ve ADO.NET](./media/dlinq-3.png "DLinq_3")  
  
## <a name="connections"></a>Bağlantılar  

 Oluştururken var olan bir ADO.NET bağlantısı sağlayabilirsiniz [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.DataContext> . <xref:System.Data.Linq.DataContext>(Sorgular dahil) tüm işlemler bu sağlanmış bağlantıyı kullanır. Bağlantı zaten açıksa, bununla [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] işiniz bittiğinde olduğu gibi bırakır.  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#4)]
 [!code-vb[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#4)]  
  
 Aşağıdaki kodda olduğu gibi, her zaman bağlantıya erişebilir ve özelliğini kullanarak kendiniz kapatabilirsiniz <xref:System.Data.Linq.DataContext.Connection%2A> :  
  
 [!code-csharp[DLinqAdoNet#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#1)]
 [!code-vb[DLinqAdoNet#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#1)]  
  
## <a name="transactions"></a>İşlemler  

 <xref:System.Data.Linq.DataContext>Uygulamanız işlemi zaten başlatmışsa ve istediğiniz zaman dahil olmak üzere kendi veritabanı işleminizi sağlayabilirsiniz <xref:System.Data.Linq.DataContext> .  
  
 .NET Framework ile işlem yapmanın tercih edilen yöntemi <xref:System.Transactions.TransactionScope> nesneyi kullanmaktır. Bu yaklaşımı kullanarak, veritabanları ve bellekte yerleşik diğer kaynak yöneticileri arasında çalışan dağıtılmış işlemler yapabilirsiniz. İşlem kapsamlarının başlaması için birkaç kaynak gerekir. Bunlar, kendilerini dağıtılmış işlemlere yalnızca işlemin kapsamı içinde birden çok bağlantı olduğunda yükseltir.  
  
 [!code-csharp[DLinqAdoNet#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#2)]
 [!code-vb[DLinqAdoNet#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#2)]  
  
 Bu yaklaşımı tüm veritabanları için kullanamazsınız. Örneğin, SqlClient bağlantısı, bir SQL Server 2000 sunucusuyla çalışırken sistem işlemlerini yükseltemezsiniz. Bunun yerine, kullanılan bir işlem kapsamını her gördüğünde tam ve dağıtılmış bir işlem için otomatik olarak listeler.  
  
## <a name="direct-sql-commands"></a>Doğrudan SQL komutları  

 Her zaman, <xref:System.Data.Linq.DataContext> gerçekleştirmek istediğiniz özelleştirilmiş görev için değişiklikleri sorgulama veya gönderme yeteneğinin yetersiz olduğu durumlarla karşılaşabilirsiniz. Bu durumlarda, <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> VERITABANıNA SQL komutları vermek ve sorgu sonuçlarını nesnelere dönüştürmek için yöntemini kullanabilirsiniz.  
  
 Örneğin, `Customer` sınıfın verilerinin iki tabloya yayıldığını varsayın (customer1 ve customer2). Aşağıdaki sorgu bir nesne dizisi döndürür `Customer` :  
  
 [!code-csharp[DLinqAdoNet#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#3)]
 [!code-vb[DLinqAdoNet#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#3)]  
  
 Tablo sonuçlarındaki sütun adları, varlık sınıfınızın sütun özellikleriyle eşleştiği sürece, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nesnelerinizi herhangi BIR SQL sorgusundan oluşturur.  
  
### <a name="parameters"></a>Parametreler  

 <xref:System.Data.Linq.DataContext.ExecuteQuery%2A>Yöntemi parametreleri kabul eder. Aşağıdaki kod parametreli bir sorgu yürütür:  
  
 [!code-csharp[DlinqAdoNet#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#4)]
 [!code-vb[DlinqAdoNet#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#4)]  
  
> [!NOTE]
> Parametreler, ve tarafından kullanılan aynı süslü gösterimi kullanılarak sorgu metninde ifade edilir `Console.WriteLine()` `String.Format()` . `String.Format()` sağladığınız sorgu dizesini alır ve küme içi parametreleri,... gibi oluşturulmuş parametre adlarıyla değiştirir `@p0` `@p1` `@p(n)` .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Arka Plan Bilgileri](background-information.md)
- [Nasıl yapılır: ADO.NET Komutu ile DataContext Arasında Bağlantıyı Yeniden Kullanma](how-to-reuse-a-connection-between-an-ado-net-command-and-a-datacontext.md)
