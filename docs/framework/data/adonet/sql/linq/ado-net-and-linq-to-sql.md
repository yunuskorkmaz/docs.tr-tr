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
# <a name="adonet-and-linq-to-sql"></a><span data-ttu-id="9f52c-102">ADO.NET ve LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="9f52c-102">ADO.NET and LINQ to SQL</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="9f52c-103">, ADO.NET teknolojisinin bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="9f52c-103">is part of the ADO.NET family of technologies.</span></span> <span data-ttu-id="9f52c-104">Bu, ADO.NET sağlayıcı modeli tarafından sunulan hizmetleri temel alır.</span><span class="sxs-lookup"><span data-stu-id="9f52c-104">It is based on services provided by the ADO.NET provider model.</span></span> <span data-ttu-id="9f52c-105">Bu nedenle, mevcut ADO.NET uygulamalarıyla [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] kodu karıştırabilir ve geçerli ADO.NET çözümlerini [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9f52c-105">You can therefore mix [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] code with existing ADO.NET applications and migrate current ADO.NET solutions to [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="9f52c-106">Aşağıdaki çizim ilişkinin üst düzey bir görünümünü sağlar.</span><span class="sxs-lookup"><span data-stu-id="9f52c-106">The following illustration provides a high-level view of the relationship.</span></span>  
  
 <span data-ttu-id="9f52c-107">![LINQ to SQL ve ADO.NET](./media/dlinq-3.png "DLinq_3")</span><span class="sxs-lookup"><span data-stu-id="9f52c-107">![LINQ to SQL and ADO.NET](./media/dlinq-3.png "DLinq_3")</span></span>  
  
## <a name="connections"></a><span data-ttu-id="9f52c-108">Bağlantılar</span><span class="sxs-lookup"><span data-stu-id="9f52c-108">Connections</span></span>  
 <span data-ttu-id="9f52c-109">Bir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.DataContext>oluştururken var olan bir ADO.NET bağlantısı sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9f52c-109">You can supply an existing ADO.NET connection when you create a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.DataContext>.</span></span> <span data-ttu-id="9f52c-110"><xref:System.Data.Linq.DataContext> karşı tüm işlemler (sorgular dahil) bu sağlanmış bağlantıyı kullanır.</span><span class="sxs-lookup"><span data-stu-id="9f52c-110">All operations against the <xref:System.Data.Linq.DataContext> (including queries) use this provided connection.</span></span> <span data-ttu-id="9f52c-111">Bağlantı zaten açıksa [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], onunla işiniz bittiğinde olduğu gibi bırakır.</span><span class="sxs-lookup"><span data-stu-id="9f52c-111">If the connection is already open, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] leaves it as is when you are finished with it.</span></span>  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#4)]
 [!code-vb[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#4)]  
  
 <span data-ttu-id="9f52c-112">Her zaman bağlantıya erişebilir ve aşağıdaki kodda olduğu gibi <xref:System.Data.Linq.DataContext.Connection%2A> özelliğini kullanarak kendiniz kapatabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="9f52c-112">You can always access the connection and close it yourself by using the <xref:System.Data.Linq.DataContext.Connection%2A> property, as in the following code:</span></span>  
  
 [!code-csharp[DLinqAdoNet#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#1)]
 [!code-vb[DLinqAdoNet#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#1)]  
  
## <a name="transactions"></a><span data-ttu-id="9f52c-113">İşlemler</span><span class="sxs-lookup"><span data-stu-id="9f52c-113">Transactions</span></span>  
 <span data-ttu-id="9f52c-114">Uygulamanız işlemi zaten başlattığı ve <xref:System.Data.Linq.DataContext> dahil olmasını istediğiniz zaman kendi veritabanı hareketiyle <xref:System.Data.Linq.DataContext> sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9f52c-114">You can supply your <xref:System.Data.Linq.DataContext> with your own database transaction when your application has already initiated the transaction and you want your <xref:System.Data.Linq.DataContext> to be involved.</span></span>  
  
 <span data-ttu-id="9f52c-115">.NET Framework işlem yapmak için tercih edilen yöntem, <xref:System.Transactions.TransactionScope> nesnesini kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="9f52c-115">The preferred method of doing transactions with the .NET Framework is to use the <xref:System.Transactions.TransactionScope> object.</span></span> <span data-ttu-id="9f52c-116">Bu yaklaşımı kullanarak, veritabanları ve bellekte yerleşik diğer kaynak yöneticileri arasında çalışan dağıtılmış işlemler yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9f52c-116">By using this approach, you can make distributed transactions that work across databases and other memory-resident resource managers.</span></span> <span data-ttu-id="9f52c-117">İşlem kapsamlarının başlaması için birkaç kaynak gerekir.</span><span class="sxs-lookup"><span data-stu-id="9f52c-117">Transaction scopes require few resources to start.</span></span> <span data-ttu-id="9f52c-118">Bunlar, kendilerini dağıtılmış işlemlere yalnızca işlemin kapsamı içinde birden çok bağlantı olduğunda yükseltir.</span><span class="sxs-lookup"><span data-stu-id="9f52c-118">They promote themselves to distributed transactions only when there are multiple connections within the scope of the transaction.</span></span>  
  
 [!code-csharp[DLinqAdoNet#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#2)]
 [!code-vb[DLinqAdoNet#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#2)]  
  
 <span data-ttu-id="9f52c-119">Bu yaklaşımı tüm veritabanları için kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="9f52c-119">You cannot use this approach for all databases.</span></span> <span data-ttu-id="9f52c-120">Örneğin, SqlClient bağlantısı, bir SQL Server 2000 sunucusuyla çalışırken sistem işlemlerini yükseltemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="9f52c-120">For example, the SqlClient connection cannot promote system transactions when it works against a SQL Server 2000 server.</span></span> <span data-ttu-id="9f52c-121">Bunun yerine, kullanılan bir işlem kapsamını her gördüğünde tam ve dağıtılmış bir işlem için otomatik olarak listeler.</span><span class="sxs-lookup"><span data-stu-id="9f52c-121">Instead, it automatically enlists to a full, distributed transaction whenever it sees a transaction scope being used.</span></span>  
  
## <a name="direct-sql-commands"></a><span data-ttu-id="9f52c-122">Doğrudan SQL komutları</span><span class="sxs-lookup"><span data-stu-id="9f52c-122">Direct SQL Commands</span></span>  
 <span data-ttu-id="9f52c-123">Her zaman, değişiklikleri sorgulamak veya göndermek için <xref:System.Data.Linq.DataContext> yeteneğinin, gerçekleştirmek istediğiniz özelleştirilmiş görev için yeterli olmadığı durumlarla karşılaşabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9f52c-123">At times you can encounter situations where the ability of the <xref:System.Data.Linq.DataContext> to query or submit changes is insufficient for the specialized task you want to perform.</span></span> <span data-ttu-id="9f52c-124">Bu durumlarda, veritabanına SQL komutları vermek ve sorgu sonuçlarını nesnelere dönüştürmek için <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> yöntemini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9f52c-124">In these circumstances you can use the <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> method to issue SQL commands to the database and convert the query results to objects.</span></span>  
  
 <span data-ttu-id="9f52c-125">Örneğin, `Customer` sınıfı için verilerin iki tabloya yayıldığını varsayın (customer1 ve customer2).</span><span class="sxs-lookup"><span data-stu-id="9f52c-125">For example, assume that the data for the `Customer` class is spread over two tables (customer1 and customer2).</span></span> <span data-ttu-id="9f52c-126">Aşağıdaki sorgu `Customer` nesnelerinin bir dizisini döndürür:</span><span class="sxs-lookup"><span data-stu-id="9f52c-126">The following query returns a sequence of `Customer` objects:</span></span>  
  
 [!code-csharp[DLinqAdoNet#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#3)]
 [!code-vb[DLinqAdoNet#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#3)]  
  
 <span data-ttu-id="9f52c-127">Tablo sonuçlarındaki sütun adları, varlık sınıfınızın sütun özellikleriyle eşleşiyorsa [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], nesnelerinizi herhangi bir SQL sorgusundan oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9f52c-127">As long as the column names in the tabular results match column properties of your entity class, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] creates your objects out of any SQL query.</span></span>  
  
### <a name="parameters"></a><span data-ttu-id="9f52c-128">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9f52c-128">Parameters</span></span>  
 <span data-ttu-id="9f52c-129"><xref:System.Data.Linq.DataContext.ExecuteQuery%2A> yöntemi parametreleri kabul eder.</span><span class="sxs-lookup"><span data-stu-id="9f52c-129">The <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> method accepts parameters.</span></span> <span data-ttu-id="9f52c-130">Aşağıdaki kod parametreli bir sorgu yürütür:</span><span class="sxs-lookup"><span data-stu-id="9f52c-130">The following code executes a parameterized query:</span></span>  
  
 [!code-csharp[DlinqAdoNet#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#4)]
 [!code-vb[DlinqAdoNet#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#4)]  
  
> [!NOTE]
> <span data-ttu-id="9f52c-131">Parametreler, `Console.WriteLine()` ve `String.Format()`tarafından kullanılan aynı süslü gösterimi kullanılarak sorgu metninde ifade edilir.</span><span class="sxs-lookup"><span data-stu-id="9f52c-131">Parameters are expressed in the query text by using the same curly notation used by `Console.WriteLine()` and `String.Format()`.</span></span> <span data-ttu-id="9f52c-132">`String.Format()`, sağladığınız sorgu dizesini alır ve `@p0`, `@p1`..., `@p(n)`gibi oluşturulmuş parametre adlarıyla birlikte zorlu parametreleri yerine koyar.</span><span class="sxs-lookup"><span data-stu-id="9f52c-132">`String.Format()` takes the query string you provide and substitutes the curly-braced parameters with generated parameter names such as `@p0`, `@p1` …, `@p(n)`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f52c-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9f52c-133">See also</span></span>

- [<span data-ttu-id="9f52c-134">Arka Plan Bilgileri</span><span class="sxs-lookup"><span data-stu-id="9f52c-134">Background Information</span></span>](background-information.md)
- [<span data-ttu-id="9f52c-135">Nasıl yapılır: ADO.NET Komutu ile DataContext Arasında Bağlantıyı Yeniden Kullanma</span><span class="sxs-lookup"><span data-stu-id="9f52c-135">How to: Reuse a Connection Between an ADO.NET Command and a DataContext</span></span>](how-to-reuse-a-connection-between-an-ado-net-command-and-a-datacontext.md)
