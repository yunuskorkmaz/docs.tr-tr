---
title: ADO.NET ve LINQ to SQL
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 49ac6da0-f2e1-46fa-963e-1b6dcb63fef7
ms.openlocfilehash: 4d2376a2e32ff099497a5dbcd6cb68d8ed526884
ms.sourcegitcommit: 19014f9c081ca2ff19652ca12503828db8239d48
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/04/2020
ms.locfileid: "76980008"
---
# <a name="adonet-and-linq-to-sql"></a>ADO.NET ve LINQ to SQL
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], ADO.NET teknolojisinin bir parçasıdır. Bu, ADO.NET sağlayıcı modeli tarafından sunulan hizmetleri temel alır. Bu nedenle, mevcut ADO.NET uygulamalarıyla [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] kodu karıştırabilir ve geçerli ADO.NET çözümlerini [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]geçirebilirsiniz. Aşağıdaki çizim ilişkinin üst düzey bir görünümünü sağlar.  
  
 ![LINQ to SQL ve ADO.NET](./media/dlinq-3.png "DLinq_3")  
  
## <a name="connections"></a>Bağlantılar  
 Bir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.DataContext>oluştururken var olan bir ADO.NET bağlantısı sağlayabilirsiniz. <xref:System.Data.Linq.DataContext> karşı tüm işlemler (sorgular dahil) bu sağlanmış bağlantıyı kullanır. Bağlantı zaten açıksa [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], onunla işiniz bittiğinde olduğu gibi bırakır.  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#4)]
 [!code-vb[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#4)]  
  
 Her zaman bağlantıya erişebilir ve aşağıdaki kodda olduğu gibi <xref:System.Data.Linq.DataContext.Connection%2A> özelliğini kullanarak kendiniz kapatabilirsiniz:  
  
 [!code-csharp[DLinqAdoNet#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#1)]
 [!code-vb[DLinqAdoNet#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#1)]  
  
## <a name="transactions"></a>İşlemler  
 Uygulamanız işlemi zaten başlattığı ve <xref:System.Data.Linq.DataContext> dahil olmasını istediğiniz zaman kendi veritabanı hareketiyle <xref:System.Data.Linq.DataContext> sağlayabilirsiniz.  
  
 .NET Framework işlem yapmak için tercih edilen yöntem, <xref:System.Transactions.TransactionScope> nesnesini kullanmaktır. Bu yaklaşımı kullanarak, veritabanları ve bellekte yerleşik diğer kaynak yöneticileri arasında çalışan dağıtılmış işlemler yapabilirsiniz. İşlem kapsamlarının başlaması için birkaç kaynak gerekir. Bunlar, kendilerini dağıtılmış işlemlere yalnızca işlemin kapsamı içinde birden çok bağlantı olduğunda yükseltir.  
  
 [!code-csharp[DLinqAdoNet#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#2)]
 [!code-vb[DLinqAdoNet#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#2)]  
  
 Bu yaklaşımı tüm veritabanları için kullanamazsınız. Örneğin, SqlClient bağlantısı, bir SQL Server 2000 sunucusuyla çalışırken sistem işlemlerini yükseltemezsiniz. Bunun yerine, kullanılan bir işlem kapsamını her gördüğünde tam ve dağıtılmış bir işlem için otomatik olarak listeler.  
  
## <a name="direct-sql-commands"></a>Doğrudan SQL komutları  
 Her zaman, değişiklikleri sorgulamak veya göndermek için <xref:System.Data.Linq.DataContext> yeteneğinin, gerçekleştirmek istediğiniz özelleştirilmiş görev için yeterli olmadığı durumlarla karşılaşabilirsiniz. Bu durumlarda, veritabanına SQL komutları vermek ve sorgu sonuçlarını nesnelere dönüştürmek için <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> yöntemini kullanabilirsiniz.  
  
 Örneğin, `Customer` sınıfı için verilerin iki tabloya yayıldığını varsayın (customer1 ve customer2). Aşağıdaki sorgu `Customer` nesnelerinin bir dizisini döndürür:  
  
 [!code-csharp[DLinqAdoNet#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#3)]
 [!code-vb[DLinqAdoNet#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#3)]  
  
 Tablo sonuçlarındaki sütun adları, varlık sınıfınızın sütun özellikleriyle eşleşiyorsa [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], nesnelerinizi herhangi bir SQL sorgusundan oluşturur.  
  
### <a name="parameters"></a>Parametreler  
 <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> yöntemi parametreleri kabul eder. Aşağıdaki kod parametreli bir sorgu yürütür:  
  
 [!code-csharp[DlinqAdoNet#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#4)]
 [!code-vb[DlinqAdoNet#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#4)]  
  
> [!NOTE]
> Parametreler, `Console.WriteLine()` ve `String.Format()`tarafından kullanılan aynı süslü gösterimi kullanılarak sorgu metninde ifade edilir. `String.Format()`, sağladığınız sorgu dizesini alır ve `@p0`, `@p1`..., `@p(n)`gibi oluşturulmuş parametre adlarıyla birlikte zorlu parametreleri yerine koyar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Arka Plan Bilgileri](background-information.md)
- [Nasıl yapılır: ADO.NET Komutu ile DataContext Arasında Bağlantıyı Yeniden Kullanma](how-to-reuse-a-connection-between-an-ado-net-command-and-a-datacontext.md)
