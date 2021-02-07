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
# <a name="adonet-and-linq-to-sql"></a><span data-ttu-id="c064e-103">ADO.NET ve LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="c064e-103">ADO.NET and LINQ to SQL</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="c064e-104">, ADO.NET teknolojisinin bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="c064e-104">is part of the ADO.NET family of technologies.</span></span> <span data-ttu-id="c064e-105">Bu, ADO.NET sağlayıcı modeli tarafından sunulan hizmetleri temel alır.</span><span class="sxs-lookup"><span data-stu-id="c064e-105">It is based on services provided by the ADO.NET provider model.</span></span> <span data-ttu-id="c064e-106">Bu nedenle, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] kodu mevcut ADO.NET uygulamalarıyla karıştırabilir ve geçerli ADO.net çözümlerini uygulamasına geçirebilirsiniz [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="c064e-106">You can therefore mix [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] code with existing ADO.NET applications and migrate current ADO.NET solutions to [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="c064e-107">Aşağıdaki çizim ilişkinin üst düzey bir görünümünü sağlar.</span><span class="sxs-lookup"><span data-stu-id="c064e-107">The following illustration provides a high-level view of the relationship.</span></span>  
  
 <span data-ttu-id="c064e-108">![LINQ to SQL ve ADO.NET](./media/dlinq-3.png "DLinq_3")</span><span class="sxs-lookup"><span data-stu-id="c064e-108">![LINQ to SQL and ADO.NET](./media/dlinq-3.png "DLinq_3")</span></span>  
  
## <a name="connections"></a><span data-ttu-id="c064e-109">Bağlantılar</span><span class="sxs-lookup"><span data-stu-id="c064e-109">Connections</span></span>  

 <span data-ttu-id="c064e-110">Oluştururken var olan bir ADO.NET bağlantısı sağlayabilirsiniz [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.DataContext> .</span><span class="sxs-lookup"><span data-stu-id="c064e-110">You can supply an existing ADO.NET connection when you create a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.DataContext>.</span></span> <span data-ttu-id="c064e-111"><xref:System.Data.Linq.DataContext>(Sorgular dahil) tüm işlemler bu sağlanmış bağlantıyı kullanır.</span><span class="sxs-lookup"><span data-stu-id="c064e-111">All operations against the <xref:System.Data.Linq.DataContext> (including queries) use this provided connection.</span></span> <span data-ttu-id="c064e-112">Bağlantı zaten açıksa, bununla [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] işiniz bittiğinde olduğu gibi bırakır.</span><span class="sxs-lookup"><span data-stu-id="c064e-112">If the connection is already open, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] leaves it as is when you are finished with it.</span></span>  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#4)]
 [!code-vb[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#4)]  
  
 <span data-ttu-id="c064e-113">Aşağıdaki kodda olduğu gibi, her zaman bağlantıya erişebilir ve özelliğini kullanarak kendiniz kapatabilirsiniz <xref:System.Data.Linq.DataContext.Connection%2A> :</span><span class="sxs-lookup"><span data-stu-id="c064e-113">You can always access the connection and close it yourself by using the <xref:System.Data.Linq.DataContext.Connection%2A> property, as in the following code:</span></span>  
  
 [!code-csharp[DLinqAdoNet#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#1)]
 [!code-vb[DLinqAdoNet#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#1)]  
  
## <a name="transactions"></a><span data-ttu-id="c064e-114">İşlemler</span><span class="sxs-lookup"><span data-stu-id="c064e-114">Transactions</span></span>  

 <span data-ttu-id="c064e-115"><xref:System.Data.Linq.DataContext>Uygulamanız işlemi zaten başlatmışsa ve istediğiniz zaman dahil olmak üzere kendi veritabanı işleminizi sağlayabilirsiniz <xref:System.Data.Linq.DataContext> .</span><span class="sxs-lookup"><span data-stu-id="c064e-115">You can supply your <xref:System.Data.Linq.DataContext> with your own database transaction when your application has already initiated the transaction and you want your <xref:System.Data.Linq.DataContext> to be involved.</span></span>  
  
 <span data-ttu-id="c064e-116">.NET Framework ile işlem yapmanın tercih edilen yöntemi <xref:System.Transactions.TransactionScope> nesneyi kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="c064e-116">The preferred method of doing transactions with the .NET Framework is to use the <xref:System.Transactions.TransactionScope> object.</span></span> <span data-ttu-id="c064e-117">Bu yaklaşımı kullanarak, veritabanları ve bellekte yerleşik diğer kaynak yöneticileri arasında çalışan dağıtılmış işlemler yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c064e-117">By using this approach, you can make distributed transactions that work across databases and other memory-resident resource managers.</span></span> <span data-ttu-id="c064e-118">İşlem kapsamlarının başlaması için birkaç kaynak gerekir.</span><span class="sxs-lookup"><span data-stu-id="c064e-118">Transaction scopes require few resources to start.</span></span> <span data-ttu-id="c064e-119">Bunlar, kendilerini dağıtılmış işlemlere yalnızca işlemin kapsamı içinde birden çok bağlantı olduğunda yükseltir.</span><span class="sxs-lookup"><span data-stu-id="c064e-119">They promote themselves to distributed transactions only when there are multiple connections within the scope of the transaction.</span></span>  
  
 [!code-csharp[DLinqAdoNet#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#2)]
 [!code-vb[DLinqAdoNet#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#2)]  
  
 <span data-ttu-id="c064e-120">Bu yaklaşımı tüm veritabanları için kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="c064e-120">You cannot use this approach for all databases.</span></span> <span data-ttu-id="c064e-121">Örneğin, SqlClient bağlantısı, bir SQL Server 2000 sunucusuyla çalışırken sistem işlemlerini yükseltemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="c064e-121">For example, the SqlClient connection cannot promote system transactions when it works against a SQL Server 2000 server.</span></span> <span data-ttu-id="c064e-122">Bunun yerine, kullanılan bir işlem kapsamını her gördüğünde tam ve dağıtılmış bir işlem için otomatik olarak listeler.</span><span class="sxs-lookup"><span data-stu-id="c064e-122">Instead, it automatically enlists to a full, distributed transaction whenever it sees a transaction scope being used.</span></span>  
  
## <a name="direct-sql-commands"></a><span data-ttu-id="c064e-123">Doğrudan SQL komutları</span><span class="sxs-lookup"><span data-stu-id="c064e-123">Direct SQL Commands</span></span>  

 <span data-ttu-id="c064e-124">Her zaman, <xref:System.Data.Linq.DataContext> gerçekleştirmek istediğiniz özelleştirilmiş görev için değişiklikleri sorgulama veya gönderme yeteneğinin yetersiz olduğu durumlarla karşılaşabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c064e-124">At times you can encounter situations where the ability of the <xref:System.Data.Linq.DataContext> to query or submit changes is insufficient for the specialized task you want to perform.</span></span> <span data-ttu-id="c064e-125">Bu durumlarda, <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> VERITABANıNA SQL komutları vermek ve sorgu sonuçlarını nesnelere dönüştürmek için yöntemini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c064e-125">In these circumstances you can use the <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> method to issue SQL commands to the database and convert the query results to objects.</span></span>  
  
 <span data-ttu-id="c064e-126">Örneğin, `Customer` sınıfın verilerinin iki tabloya yayıldığını varsayın (customer1 ve customer2).</span><span class="sxs-lookup"><span data-stu-id="c064e-126">For example, assume that the data for the `Customer` class is spread over two tables (customer1 and customer2).</span></span> <span data-ttu-id="c064e-127">Aşağıdaki sorgu bir nesne dizisi döndürür `Customer` :</span><span class="sxs-lookup"><span data-stu-id="c064e-127">The following query returns a sequence of `Customer` objects:</span></span>  
  
 [!code-csharp[DLinqAdoNet#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#3)]
 [!code-vb[DLinqAdoNet#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#3)]  
  
 <span data-ttu-id="c064e-128">Tablo sonuçlarındaki sütun adları, varlık sınıfınızın sütun özellikleriyle eşleştiği sürece, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nesnelerinizi herhangi BIR SQL sorgusundan oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c064e-128">As long as the column names in the tabular results match column properties of your entity class, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] creates your objects out of any SQL query.</span></span>  
  
### <a name="parameters"></a><span data-ttu-id="c064e-129">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c064e-129">Parameters</span></span>  

 <span data-ttu-id="c064e-130"><xref:System.Data.Linq.DataContext.ExecuteQuery%2A>Yöntemi parametreleri kabul eder.</span><span class="sxs-lookup"><span data-stu-id="c064e-130">The <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> method accepts parameters.</span></span> <span data-ttu-id="c064e-131">Aşağıdaki kod parametreli bir sorgu yürütür:</span><span class="sxs-lookup"><span data-stu-id="c064e-131">The following code executes a parameterized query:</span></span>  
  
 [!code-csharp[DlinqAdoNet#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#4)]
 [!code-vb[DlinqAdoNet#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#4)]  
  
> [!NOTE]
> <span data-ttu-id="c064e-132">Parametreler, ve tarafından kullanılan aynı süslü gösterimi kullanılarak sorgu metninde ifade edilir `Console.WriteLine()` `String.Format()` .</span><span class="sxs-lookup"><span data-stu-id="c064e-132">Parameters are expressed in the query text by using the same curly notation used by `Console.WriteLine()` and `String.Format()`.</span></span> <span data-ttu-id="c064e-133">`String.Format()` sağladığınız sorgu dizesini alır ve küme içi parametreleri,... gibi oluşturulmuş parametre adlarıyla değiştirir `@p0` `@p1` `@p(n)` .</span><span class="sxs-lookup"><span data-stu-id="c064e-133">`String.Format()` takes the query string you provide and substitutes the curly-braced parameters with generated parameter names such as `@p0`, `@p1` …, `@p(n)`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c064e-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c064e-134">See also</span></span>

- [<span data-ttu-id="c064e-135">Arka Plan Bilgileri</span><span class="sxs-lookup"><span data-stu-id="c064e-135">Background Information</span></span>](background-information.md)
- [<span data-ttu-id="c064e-136">Nasıl yapılır: ADO.NET Komutu ile DataContext Arasında Bağlantıyı Yeniden Kullanma</span><span class="sxs-lookup"><span data-stu-id="c064e-136">How to: Reuse a Connection Between an ADO.NET Command and a DataContext</span></span>](how-to-reuse-a-connection-between-an-ado-net-command-and-a-datacontext.md)
