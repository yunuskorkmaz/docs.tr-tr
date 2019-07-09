---
title: ADO.NET ve LINQ to SQL
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 49ac6da0-f2e1-46fa-963e-1b6dcb63fef7
ms.openlocfilehash: 6a6e057b45c1305a889ce4ed915b437a29ab2794
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67662073"
---
# <a name="adonet-and-linq-to-sql"></a><span data-ttu-id="95ef1-102">ADO.NET ve LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="95ef1-102">ADO.NET and LINQ to SQL</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="95ef1-103">teknolojileri ADO.NET ailesinin bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="95ef1-103">is part of the ADO.NET family of technologies.</span></span> <span data-ttu-id="95ef1-104">ADO.NET sağlayıcısı modeli tarafından sağlanan hizmetleri temel alır.</span><span class="sxs-lookup"><span data-stu-id="95ef1-104">It is based on services provided by the ADO.NET provider model.</span></span> <span data-ttu-id="95ef1-105">Bu nedenle karıştırabilirsiniz [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ADO.NET uygulamalarınız ile kod ve geçerli ADO.NET çözümleri geçirme [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="95ef1-105">You can therefore mix [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] code with existing ADO.NET applications and migrate current ADO.NET solutions to [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="95ef1-106">Aşağıdaki çizim, ilişki üst düzey bir görünümünü sağlar.</span><span class="sxs-lookup"><span data-stu-id="95ef1-106">The following illustration provides a high-level view of the relationship.</span></span>  
  
 <span data-ttu-id="95ef1-107">![LINQ to SQL ve ADO.NET](../../../../../../docs/framework/data/adonet/sql/linq/media/dlinq-3.png "DLinq_3")</span><span class="sxs-lookup"><span data-stu-id="95ef1-107">![LINQ to SQL and ADO.NET](../../../../../../docs/framework/data/adonet/sql/linq/media/dlinq-3.png "DLinq_3")</span></span>  
  
## <a name="connections"></a><span data-ttu-id="95ef1-108">Bağlantılar</span><span class="sxs-lookup"><span data-stu-id="95ef1-108">Connections</span></span>  
 <span data-ttu-id="95ef1-109">Oluşturduğunuzda, varolan bir ADO.NET bağlantı sağlayabilirsiniz bir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.DataContext>.</span><span class="sxs-lookup"><span data-stu-id="95ef1-109">You can supply an existing ADO.NET connection when you create a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.DataContext>.</span></span> <span data-ttu-id="95ef1-110">Tüm işlemler <xref:System.Data.Linq.DataContext> (sorgular gibi) Bu bağlantı sağlanan kullanın.</span><span class="sxs-lookup"><span data-stu-id="95ef1-110">All operations against the <xref:System.Data.Linq.DataContext> (including queries) use this provided connection.</span></span> <span data-ttu-id="95ef1-111">Bağlantı zaten açık değilse [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ile işiniz bittiğinde olduğu gibi bırakır.</span><span class="sxs-lookup"><span data-stu-id="95ef1-111">If the connection is already open, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] leaves it as is when you are finished with it.</span></span>  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#4)]
 [!code-vb[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#4)]  
  
 <span data-ttu-id="95ef1-112">Her zaman bağlantı erişebilir ve kendiniz kullanarak kapatmak <xref:System.Data.Linq.DataContext.Connection%2A> özelliğindeki, aşağıdaki kod gibi:</span><span class="sxs-lookup"><span data-stu-id="95ef1-112">You can always access the connection and close it yourself by using the <xref:System.Data.Linq.DataContext.Connection%2A> property, as in the following code:</span></span>  
  
 [!code-csharp[DLinqAdoNet#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#1)]
 [!code-vb[DLinqAdoNet#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#1)]  
  
## <a name="transactions"></a><span data-ttu-id="95ef1-113">İşlemler</span><span class="sxs-lookup"><span data-stu-id="95ef1-113">Transactions</span></span>  
 <span data-ttu-id="95ef1-114">Verebilirsiniz, <xref:System.Data.Linq.DataContext> uygulamanız zaten işlem başlattı ve istediğiniz zaman kendi veritabanı işlemi ile <xref:System.Data.Linq.DataContext> görünüyor.</span><span class="sxs-lookup"><span data-stu-id="95ef1-114">You can supply your <xref:System.Data.Linq.DataContext> with your own database transaction when your application has already initiated the transaction and you want your <xref:System.Data.Linq.DataContext> to be involved.</span></span>  
  
 <span data-ttu-id="95ef1-115">.NET Framework ile işlemleri yapmanın tercih edilen yöntem <xref:System.Transactions.TransactionScope> nesne.</span><span class="sxs-lookup"><span data-stu-id="95ef1-115">The preferred method of doing transactions with the .NET Framework is to use the <xref:System.Transactions.TransactionScope> object.</span></span> <span data-ttu-id="95ef1-116">Bu yaklaşımı kullanarak, veritabanları ve diğer bellekte kaynak yöneticileri çalışan dağıtılmış işlemler yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="95ef1-116">By using this approach, you can make distributed transactions that work across databases and other memory-resident resource managers.</span></span> <span data-ttu-id="95ef1-117">İşlem kapsamları başlatmak için birkaç kaynakları gerektirir.</span><span class="sxs-lookup"><span data-stu-id="95ef1-117">Transaction scopes require few resources to start.</span></span> <span data-ttu-id="95ef1-118">Yalnızca işlemin kapsamı içinde birden fazla bağlantı kurulduğunda, kendilerini dağıtılmış işlemler için yükseltin.</span><span class="sxs-lookup"><span data-stu-id="95ef1-118">They promote themselves to distributed transactions only when there are multiple connections within the scope of the transaction.</span></span>  
  
 [!code-csharp[DLinqAdoNet#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#2)]
 [!code-vb[DLinqAdoNet#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#2)]  
  
 <span data-ttu-id="95ef1-119">Bu yaklaşım, tüm veritabanları için kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="95ef1-119">You cannot use this approach for all databases.</span></span> <span data-ttu-id="95ef1-120">Örneğin, bir SQL Server 2000 sunucuda çalışırken SqlClient bağlantı sistem işlemleri yükseltilemiyor.</span><span class="sxs-lookup"><span data-stu-id="95ef1-120">For example, the SqlClient connection cannot promote system transactions when it works against a SQL Server 2000 server.</span></span> <span data-ttu-id="95ef1-121">Bunun yerine, kullanılan işlem kapsamı gördüğünde olduğunda otomatik olarak tam, dağıtılmış bir işlem için kaydeder.</span><span class="sxs-lookup"><span data-stu-id="95ef1-121">Instead, it automatically enlists to a full, distributed transaction whenever it sees a transaction scope being used.</span></span>  
  
## <a name="direct-sql-commands"></a><span data-ttu-id="95ef1-122">Doğrudan SQL komutları</span><span class="sxs-lookup"><span data-stu-id="95ef1-122">Direct SQL Commands</span></span>  
 <span data-ttu-id="95ef1-123">Bazen, durum karşılaşabilirsiniz burada yeteneğini <xref:System.Data.Linq.DataContext> sorgu veya değişiklikleri uygulamak istediğiniz özel bir görev için yetersiz göndermek için.</span><span class="sxs-lookup"><span data-stu-id="95ef1-123">At times you can encounter situations where the ability of the <xref:System.Data.Linq.DataContext> to query or submit changes is insufficient for the specialized task you want to perform.</span></span> <span data-ttu-id="95ef1-124">Bu durumlarda, kullanabileceğiniz <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> veritabanına SQL komutlarını vermek ve sorgu sonuçları nesnelerine dönüştürmek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="95ef1-124">In these circumstances you can use the <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> method to issue SQL commands to the database and convert the query results to objects.</span></span>  
  
 <span data-ttu-id="95ef1-125">Örneğin, varsayımında verilerini `Customer` sınıfı üzerinde iki tablo (customer1 ve customer2) yayılır.</span><span class="sxs-lookup"><span data-stu-id="95ef1-125">For example, assume that the data for the `Customer` class is spread over two tables (customer1 and customer2).</span></span> <span data-ttu-id="95ef1-126">Aşağıdaki sorgu bir dizi döndürür `Customer` nesneler:</span><span class="sxs-lookup"><span data-stu-id="95ef1-126">The following query returns a sequence of `Customer` objects:</span></span>  
  
 [!code-csharp[DLinqAdoNet#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#3)]
 [!code-vb[DLinqAdoNet#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#3)]  
  
 <span data-ttu-id="95ef1-127">Sütun özellikleri varlık sınıfınızın tablo sonuçları sütun adlarının eşleştiği sürece [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nesnelerinizi dışında herhangi bir SQL sorgu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="95ef1-127">As long as the column names in the tabular results match column properties of your entity class, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] creates your objects out of any SQL query.</span></span>  
  
### <a name="parameters"></a><span data-ttu-id="95ef1-128">Parametreler</span><span class="sxs-lookup"><span data-stu-id="95ef1-128">Parameters</span></span>  
 <span data-ttu-id="95ef1-129"><xref:System.Data.Linq.DataContext.ExecuteQuery%2A> Yöntemi parametreleri kabul eder.</span><span class="sxs-lookup"><span data-stu-id="95ef1-129">The <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> method accepts parameters.</span></span> <span data-ttu-id="95ef1-130">Aşağıdaki kod, parametreli bir sorgu yürütür:</span><span class="sxs-lookup"><span data-stu-id="95ef1-130">The following code executes a parameterized query:</span></span>  
  
 [!code-csharp[DlinqAdoNet#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#4)]
 [!code-vb[DlinqAdoNet#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#4)]  
  
> [!NOTE]
>  <span data-ttu-id="95ef1-131">Parametreleri ifade sorgu metni tarafından kullanılan aynı küme gösterimi kullanılarak `Console.WriteLine()` ve `String.Format()`.</span><span class="sxs-lookup"><span data-stu-id="95ef1-131">Parameters are expressed in the query text by using the same curly notation used by `Console.WriteLine()` and `String.Format()`.</span></span> <span data-ttu-id="95ef1-132">`String.Format()` sorgu dizesini sağlar ve oluşturulan parametre adı kaşlı küme ayracıyla belirtilen parametrelerle gibi değiştirir alan `@p0`, `@p1` ... `@p(n)`.</span><span class="sxs-lookup"><span data-stu-id="95ef1-132">`String.Format()` takes the query string you provide and substitutes the curly-braced parameters with generated parameter names such as `@p0`, `@p1` …, `@p(n)`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95ef1-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="95ef1-133">See also</span></span>

- [<span data-ttu-id="95ef1-134">Arka Plan Bilgileri</span><span class="sxs-lookup"><span data-stu-id="95ef1-134">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
- [<span data-ttu-id="95ef1-135">Nasıl yapılır: Bir ADO.NET komutu ile DataContext arasında bir bağlantı yeniden kullanma</span><span class="sxs-lookup"><span data-stu-id="95ef1-135">How to: Reuse a Connection Between an ADO.NET Command and a DataContext</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-reuse-a-connection-between-an-ado-net-command-and-a-datacontext.md)
