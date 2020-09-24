---
title: ADO.NET ve LINQ to SQL
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 49ac6da0-f2e1-46fa-963e-1b6dcb63fef7
ms.openlocfilehash: 5dc1796b7fb7036f68c2435325c6a29d381c59f1
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91161587"
---
# <a name="adonet-and-linq-to-sql"></a><span data-ttu-id="04414-102">ADO.NET ve LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="04414-102">ADO.NET and LINQ to SQL</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="04414-103">, ADO.NET teknolojisinin bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="04414-103">is part of the ADO.NET family of technologies.</span></span> <span data-ttu-id="04414-104">Bu, ADO.NET sağlayıcı modeli tarafından sunulan hizmetleri temel alır.</span><span class="sxs-lookup"><span data-stu-id="04414-104">It is based on services provided by the ADO.NET provider model.</span></span> <span data-ttu-id="04414-105">Bu nedenle, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] kodu mevcut ADO.NET uygulamalarıyla karıştırabilir ve geçerli ADO.net çözümlerini uygulamasına geçirebilirsiniz [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="04414-105">You can therefore mix [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] code with existing ADO.NET applications and migrate current ADO.NET solutions to [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="04414-106">Aşağıdaki çizim ilişkinin üst düzey bir görünümünü sağlar.</span><span class="sxs-lookup"><span data-stu-id="04414-106">The following illustration provides a high-level view of the relationship.</span></span>  
  
 <span data-ttu-id="04414-107">![LINQ to SQL ve ADO.NET](./media/dlinq-3.png "DLinq_3")</span><span class="sxs-lookup"><span data-stu-id="04414-107">![LINQ to SQL and ADO.NET](./media/dlinq-3.png "DLinq_3")</span></span>  
  
## <a name="connections"></a><span data-ttu-id="04414-108">Bağlantılar</span><span class="sxs-lookup"><span data-stu-id="04414-108">Connections</span></span>  

 <span data-ttu-id="04414-109">Oluştururken var olan bir ADO.NET bağlantısı sağlayabilirsiniz [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.DataContext> .</span><span class="sxs-lookup"><span data-stu-id="04414-109">You can supply an existing ADO.NET connection when you create a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.DataContext>.</span></span> <span data-ttu-id="04414-110"><xref:System.Data.Linq.DataContext>(Sorgular dahil) tüm işlemler bu sağlanmış bağlantıyı kullanır.</span><span class="sxs-lookup"><span data-stu-id="04414-110">All operations against the <xref:System.Data.Linq.DataContext> (including queries) use this provided connection.</span></span> <span data-ttu-id="04414-111">Bağlantı zaten açıksa, bununla [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] işiniz bittiğinde olduğu gibi bırakır.</span><span class="sxs-lookup"><span data-stu-id="04414-111">If the connection is already open, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] leaves it as is when you are finished with it.</span></span>  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#4)]
 [!code-vb[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#4)]  
  
 <span data-ttu-id="04414-112">Aşağıdaki kodda olduğu gibi, her zaman bağlantıya erişebilir ve özelliğini kullanarak kendiniz kapatabilirsiniz <xref:System.Data.Linq.DataContext.Connection%2A> :</span><span class="sxs-lookup"><span data-stu-id="04414-112">You can always access the connection and close it yourself by using the <xref:System.Data.Linq.DataContext.Connection%2A> property, as in the following code:</span></span>  
  
 [!code-csharp[DLinqAdoNet#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#1)]
 [!code-vb[DLinqAdoNet#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#1)]  
  
## <a name="transactions"></a><span data-ttu-id="04414-113">İşlemler</span><span class="sxs-lookup"><span data-stu-id="04414-113">Transactions</span></span>  

 <span data-ttu-id="04414-114"><xref:System.Data.Linq.DataContext>Uygulamanız işlemi zaten başlatmışsa ve istediğiniz zaman dahil olmak üzere kendi veritabanı işleminizi sağlayabilirsiniz <xref:System.Data.Linq.DataContext> .</span><span class="sxs-lookup"><span data-stu-id="04414-114">You can supply your <xref:System.Data.Linq.DataContext> with your own database transaction when your application has already initiated the transaction and you want your <xref:System.Data.Linq.DataContext> to be involved.</span></span>  
  
 <span data-ttu-id="04414-115">.NET Framework ile işlem yapmanın tercih edilen yöntemi <xref:System.Transactions.TransactionScope> nesneyi kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="04414-115">The preferred method of doing transactions with the .NET Framework is to use the <xref:System.Transactions.TransactionScope> object.</span></span> <span data-ttu-id="04414-116">Bu yaklaşımı kullanarak, veritabanları ve bellekte yerleşik diğer kaynak yöneticileri arasında çalışan dağıtılmış işlemler yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="04414-116">By using this approach, you can make distributed transactions that work across databases and other memory-resident resource managers.</span></span> <span data-ttu-id="04414-117">İşlem kapsamlarının başlaması için birkaç kaynak gerekir.</span><span class="sxs-lookup"><span data-stu-id="04414-117">Transaction scopes require few resources to start.</span></span> <span data-ttu-id="04414-118">Bunlar, kendilerini dağıtılmış işlemlere yalnızca işlemin kapsamı içinde birden çok bağlantı olduğunda yükseltir.</span><span class="sxs-lookup"><span data-stu-id="04414-118">They promote themselves to distributed transactions only when there are multiple connections within the scope of the transaction.</span></span>  
  
 [!code-csharp[DLinqAdoNet#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#2)]
 [!code-vb[DLinqAdoNet#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#2)]  
  
 <span data-ttu-id="04414-119">Bu yaklaşımı tüm veritabanları için kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="04414-119">You cannot use this approach for all databases.</span></span> <span data-ttu-id="04414-120">Örneğin, SqlClient bağlantısı, bir SQL Server 2000 sunucusuyla çalışırken sistem işlemlerini yükseltemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="04414-120">For example, the SqlClient connection cannot promote system transactions when it works against a SQL Server 2000 server.</span></span> <span data-ttu-id="04414-121">Bunun yerine, kullanılan bir işlem kapsamını her gördüğünde tam ve dağıtılmış bir işlem için otomatik olarak listeler.</span><span class="sxs-lookup"><span data-stu-id="04414-121">Instead, it automatically enlists to a full, distributed transaction whenever it sees a transaction scope being used.</span></span>  
  
## <a name="direct-sql-commands"></a><span data-ttu-id="04414-122">Doğrudan SQL komutları</span><span class="sxs-lookup"><span data-stu-id="04414-122">Direct SQL Commands</span></span>  

 <span data-ttu-id="04414-123">Her zaman, <xref:System.Data.Linq.DataContext> gerçekleştirmek istediğiniz özelleştirilmiş görev için değişiklikleri sorgulama veya gönderme yeteneğinin yetersiz olduğu durumlarla karşılaşabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="04414-123">At times you can encounter situations where the ability of the <xref:System.Data.Linq.DataContext> to query or submit changes is insufficient for the specialized task you want to perform.</span></span> <span data-ttu-id="04414-124">Bu durumlarda, <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> VERITABANıNA SQL komutları vermek ve sorgu sonuçlarını nesnelere dönüştürmek için yöntemini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="04414-124">In these circumstances you can use the <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> method to issue SQL commands to the database and convert the query results to objects.</span></span>  
  
 <span data-ttu-id="04414-125">Örneğin, `Customer` sınıfın verilerinin iki tabloya yayıldığını varsayın (customer1 ve customer2).</span><span class="sxs-lookup"><span data-stu-id="04414-125">For example, assume that the data for the `Customer` class is spread over two tables (customer1 and customer2).</span></span> <span data-ttu-id="04414-126">Aşağıdaki sorgu bir nesne dizisi döndürür `Customer` :</span><span class="sxs-lookup"><span data-stu-id="04414-126">The following query returns a sequence of `Customer` objects:</span></span>  
  
 [!code-csharp[DLinqAdoNet#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#3)]
 [!code-vb[DLinqAdoNet#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#3)]  
  
 <span data-ttu-id="04414-127">Tablo sonuçlarındaki sütun adları, varlık sınıfınızın sütun özellikleriyle eşleştiği sürece, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nesnelerinizi herhangi BIR SQL sorgusundan oluşturur.</span><span class="sxs-lookup"><span data-stu-id="04414-127">As long as the column names in the tabular results match column properties of your entity class, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] creates your objects out of any SQL query.</span></span>  
  
### <a name="parameters"></a><span data-ttu-id="04414-128">Parametreler</span><span class="sxs-lookup"><span data-stu-id="04414-128">Parameters</span></span>  

 <span data-ttu-id="04414-129"><xref:System.Data.Linq.DataContext.ExecuteQuery%2A>Yöntemi parametreleri kabul eder.</span><span class="sxs-lookup"><span data-stu-id="04414-129">The <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> method accepts parameters.</span></span> <span data-ttu-id="04414-130">Aşağıdaki kod parametreli bir sorgu yürütür:</span><span class="sxs-lookup"><span data-stu-id="04414-130">The following code executes a parameterized query:</span></span>  
  
 [!code-csharp[DlinqAdoNet#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#4)]
 [!code-vb[DlinqAdoNet#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#4)]  
  
> [!NOTE]
> <span data-ttu-id="04414-131">Parametreler, ve tarafından kullanılan aynı süslü gösterimi kullanılarak sorgu metninde ifade edilir `Console.WriteLine()` `String.Format()` .</span><span class="sxs-lookup"><span data-stu-id="04414-131">Parameters are expressed in the query text by using the same curly notation used by `Console.WriteLine()` and `String.Format()`.</span></span> <span data-ttu-id="04414-132">`String.Format()` sağladığınız sorgu dizesini alır ve küme içi parametreleri,... gibi oluşturulmuş parametre adlarıyla değiştirir `@p0` `@p1` `@p(n)` .</span><span class="sxs-lookup"><span data-stu-id="04414-132">`String.Format()` takes the query string you provide and substitutes the curly-braced parameters with generated parameter names such as `@p0`, `@p1` …, `@p(n)`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04414-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="04414-133">See also</span></span>

- [<span data-ttu-id="04414-134">Arka Plan Bilgileri</span><span class="sxs-lookup"><span data-stu-id="04414-134">Background Information</span></span>](background-information.md)
- [<span data-ttu-id="04414-135">Nasıl yapılır: ADO.NET Komutu ile DataContext Arasında Bağlantıyı Yeniden Kullanma</span><span class="sxs-lookup"><span data-stu-id="04414-135">How to: Reuse a Connection Between an ADO.NET Command and a DataContext</span></span>](how-to-reuse-a-connection-between-an-ado-net-command-and-a-datacontext.md)
