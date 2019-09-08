---
title: SQL Server ile System.Transactions Tümleştirmesi
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b555544e-7abb-4814-859b-ab9cdd7d8716
ms.openlocfilehash: 075eea42c65a822fc46ca14f820599567c35d231
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70791371"
---
# <a name="systemtransactions-integration-with-sql-server"></a><span data-ttu-id="3c159-102">SQL Server ile System.Transactions Tümleştirmesi</span><span class="sxs-lookup"><span data-stu-id="3c159-102">System.Transactions Integration with SQL Server</span></span>
<span data-ttu-id="3c159-103">.NET Framework sürüm 2,0, <xref:System.Transactions> ad alanı aracılığıyla erişilebilen bir işlem çerçevesi sunmuştur.</span><span class="sxs-lookup"><span data-stu-id="3c159-103">The .NET Framework version 2.0 introduced a transaction framework that can be accessed through the <xref:System.Transactions> namespace.</span></span> <span data-ttu-id="3c159-104">Bu çerçeve, ADO.NET dahil olmak üzere .NET Framework, işlemleri tam olarak tümleştirilmiş bir şekilde kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="3c159-104">This framework exposes transactions in a way that is fully integrated in the .NET Framework, including ADO.NET.</span></span>  
  
 <span data-ttu-id="3c159-105">Programlama iyileştirmelerine ek olarak, <xref:System.Transactions> işlemler ile çalışırken iyileştirmeleri koordine etmek için ADO.net birlikte çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="3c159-105">In addition to the programmability enhancements, <xref:System.Transactions> and ADO.NET can work together to coordinate optimizations when you work with transactions.</span></span> <span data-ttu-id="3c159-106">Bir promotable işlemi, tam olarak dağıtılan bir işlem için gereken bir şekilde otomatik olarak yükseltilabilecek hafif (yerel) bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="3c159-106">A promotable transaction is a lightweight (local) transaction that can be automatically promoted to a fully distributed transaction on an as-needed basis.</span></span>  
  
 <span data-ttu-id="3c159-107">ADO.NET 2,0 ile başlayarak, <xref:System.Data.SqlClient> SQL Server çalışırken promotable işlemlerini destekler.</span><span class="sxs-lookup"><span data-stu-id="3c159-107">Starting with ADO.NET 2.0, <xref:System.Data.SqlClient> supports promotable transactions when you work with SQL Server.</span></span> <span data-ttu-id="3c159-108">Bir promotable işlemi, eklenen ek yük gerekmediği takdirde dağıtılmış bir işlemin ek yükünü çağırmaz.</span><span class="sxs-lookup"><span data-stu-id="3c159-108">A promotable transaction does not invoke the added overhead of a distributed transaction unless the added overhead is required.</span></span> <span data-ttu-id="3c159-109">Promotable işlemleri otomatiktir ve geliştiriciden müdahale gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="3c159-109">Promotable transactions are automatic and require no intervention from the developer.</span></span>  
  
 <span data-ttu-id="3c159-110">Promotable işlemleri yalnızca SQL Server ile SQL Server (`SqlClient`) için .NET Framework veri sağlayıcısı kullandığınızda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3c159-110">Promotable transactions are only available when you use the .NET Framework Data Provider for SQL Server (`SqlClient`) with SQL Server.</span></span>  
  
## <a name="creating-promotable-transactions"></a><span data-ttu-id="3c159-111">Promotable Işlemleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="3c159-111">Creating Promotable Transactions</span></span>  
 <span data-ttu-id="3c159-112">SQL Server için .NET Framework sağlayıcısı, .NET Framework <xref:System.Transactions> ad alanındaki sınıflar aracılığıyla işlenen promotable işlemleri için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="3c159-112">The .NET Framework Provider for SQL Server provides support for promotable transactions, which are handled through the classes in the .NET Framework <xref:System.Transactions> namespace.</span></span> <span data-ttu-id="3c159-113">Promotable işlemleri, dağıtılmış bir işlemin oluşturulması gerekene kadar erteleyerek dağıtılmış işlemleri iyileştirir.</span><span class="sxs-lookup"><span data-stu-id="3c159-113">Promotable transactions optimize distributed transactions by deferring creating a distributed transaction until it is needed.</span></span> <span data-ttu-id="3c159-114">Yalnızca bir kaynak yöneticisi gerekliyse, dağıtılmış işlem gerçekleşmez.</span><span class="sxs-lookup"><span data-stu-id="3c159-114">If only one resource manager is required, no distributed transaction occurs.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3c159-115">Kısmen güvenilen bir senaryoda <xref:System.Transactions.DistributedTransactionPermission> , bir işlem dağıtılmış bir işleme yükseltildiğinde gereklidir.</span><span class="sxs-lookup"><span data-stu-id="3c159-115">In a partially trusted scenario, the <xref:System.Transactions.DistributedTransactionPermission> is required when a transaction is promoted to a distributed transaction.</span></span>  
  
## <a name="promotable-transaction-scenarios"></a><span data-ttu-id="3c159-116">Promotable Işlem senaryoları</span><span class="sxs-lookup"><span data-stu-id="3c159-116">Promotable Transaction Scenarios</span></span>  
 <span data-ttu-id="3c159-117">Dağıtılmış işlemler genellikle Microsoft Dağıtılmış İşlem Düzenleyicisi (MS DTC) tarafından yönetilmekte olan önemli sistem kaynaklarını kullanır ve böylece işlem sırasında erişilen tüm kaynak yöneticileri tümleştirilir.</span><span class="sxs-lookup"><span data-stu-id="3c159-117">Distributed transactions typically consume significant system resources, being managed by Microsoft Distributed Transaction Coordinator (MS DTC), which integrates all the resource managers accessed in the transaction.</span></span> <span data-ttu-id="3c159-118">Bir promotable işlemi, işi etkin bir şekilde basit <xref:System.Transactions> bir SQL Server işlem olarak temsil eden bir işlemin özel bir biçimidir.</span><span class="sxs-lookup"><span data-stu-id="3c159-118">A promotable transaction is a special form of a <xref:System.Transactions> transaction that effectively delegates the work to a simple SQL Server transaction.</span></span> <span data-ttu-id="3c159-119"><xref:System.Transactions>, <xref:System.Data.SqlClient>ve SQL Server işlem işleme dahil işi koordine etmek ve gerektiğinde tam dağıtılmış bir işleme yükseltmek.</span><span class="sxs-lookup"><span data-stu-id="3c159-119"><xref:System.Transactions>, <xref:System.Data.SqlClient>, and SQL Server coordinate the work involved in handling the transaction, promoting it to a full distributed transaction as needed.</span></span>  
  
 <span data-ttu-id="3c159-120">Promotable işlemlerini kullanmanın avantajı, bir bağlantının etkin <xref:System.Transactions.TransactionScope> bir işlem kullanılarak açıldığı ve başka hiçbir bağlantının açılmadığı durumlarda, işlemin ek bir işlem yapmak yerine hafif bir işlem olarak işleme yaptığı bir işlemdir. tam dağıtılmış işlemin yükü.</span><span class="sxs-lookup"><span data-stu-id="3c159-120">The benefit of using promotable transactions is that when a connection is opened by using an active <xref:System.Transactions.TransactionScope> transaction, and no other connections are opened, the transaction commits as a lightweight transaction, instead of incurring the additional overhead of a full distributed transaction.</span></span>  
  
### <a name="connection-string-keywords"></a><span data-ttu-id="3c159-121">Bağlantı dizesi anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="3c159-121">Connection String Keywords</span></span>  
 <span data-ttu-id="3c159-122">Özelliği, işlem bağlamlarının etkinleştirilip `Enlist`etkinleştirilmeyeceğini ve bağlantıyı dağıtılmış <xref:System.Data.SqlClient> bir işlemde otomatik olarak Enlist olup olmayacağını gösteren bir anahtar sözcüğü destekler. <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A></span><span class="sxs-lookup"><span data-stu-id="3c159-122">The <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> property supports a keyword, `Enlist`, which indicates whether <xref:System.Data.SqlClient> will detect transactional contexts and automatically enlist the connection in a distributed transaction.</span></span> <span data-ttu-id="3c159-123">Varsa `Enlist=true`, bağlantı, açma iş parçacığının geçerli işlem bağlamına otomatik olarak kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="3c159-123">If `Enlist=true`, the connection is automatically enlisted in the opening thread's current transaction context.</span></span> <span data-ttu-id="3c159-124">`Enlist=false` Varsa`SqlClient` , bağlantı dağıtılmış bir işlemle etkileşime girmez.</span><span class="sxs-lookup"><span data-stu-id="3c159-124">If `Enlist=false`, the `SqlClient` connection does not interact with a distributed transaction.</span></span> <span data-ttu-id="3c159-125">Varsayılan değeri `Enlist` true 'dur.</span><span class="sxs-lookup"><span data-stu-id="3c159-125">The default value for `Enlist` is true.</span></span> <span data-ttu-id="3c159-126">`Enlist` Bağlantı dizesinde belirtilmemişse bağlantı, bağlantı açıldığında algılanan bir dağıtılmış işlemde otomatik olarak kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="3c159-126">If `Enlist` is not specified in the connection string, the connection is automatically enlisted in a distributed transaction if one is detected when the connection is opened.</span></span>  
  
 <span data-ttu-id="3c159-127">`System.Transactions` Bir `Transaction Binding` bağlantıdizesindeki<xref:System.Data.SqlClient.SqlConnection> anahtar sözcükler, kayıtlı bir işlemle bağlantının ilişkilendirmesini denetler.</span><span class="sxs-lookup"><span data-stu-id="3c159-127">The `Transaction Binding` keywords in a <xref:System.Data.SqlClient.SqlConnection> connection string control the connection's association with an enlisted `System.Transactions` transaction.</span></span> <span data-ttu-id="3c159-128">Ayrıca, <xref:System.Data.SqlClient.SqlConnectionStringBuilder.TransactionBinding%2A> <xref:System.Data.SqlClient.SqlConnectionStringBuilder>öğesinin özelliği aracılığıyla da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3c159-128">It is also available through the <xref:System.Data.SqlClient.SqlConnectionStringBuilder.TransactionBinding%2A> property of a <xref:System.Data.SqlClient.SqlConnectionStringBuilder>.</span></span>  
  
 <span data-ttu-id="3c159-129">Aşağıdaki tabloda olası değerler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3c159-129">The following table describes the possible values.</span></span>  
  
|<span data-ttu-id="3c159-130">Anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="3c159-130">Keyword</span></span>|<span data-ttu-id="3c159-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3c159-131">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3c159-132">Örtük bağlantı kesme</span><span class="sxs-lookup"><span data-stu-id="3c159-132">Implicit Unbind</span></span>|<span data-ttu-id="3c159-133">Varsayılan.</span><span class="sxs-lookup"><span data-stu-id="3c159-133">The default.</span></span> <span data-ttu-id="3c159-134">Bağlantı, sona erdiğinde işlemden ayrıldığında, tekrar tekrar yürütme moduna geçiş yapın.</span><span class="sxs-lookup"><span data-stu-id="3c159-134">The connection detaches from the transaction when it ends, switching back to autocommit mode.</span></span>|  
|<span data-ttu-id="3c159-135">Açık ciltten çıkarma</span><span class="sxs-lookup"><span data-stu-id="3c159-135">Explicit Unbind</span></span>|<span data-ttu-id="3c159-136">İşlem kapatılıncaya kadar bağlantı işleme bağlı kalır.</span><span class="sxs-lookup"><span data-stu-id="3c159-136">The connection remains attached to the transaction until the transaction is closed.</span></span> <span data-ttu-id="3c159-137">İlişkili işlem etkin değilse veya eşleşmezse <xref:System.Transactions.Transaction.Current%2A>bağlantı başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="3c159-137">The connection will fail if the associated transaction is not active or does not match <xref:System.Transactions.Transaction.Current%2A>.</span></span>|  
  
## <a name="using-transactionscope"></a><span data-ttu-id="3c159-138">TransactionScope kullanma</span><span class="sxs-lookup"><span data-stu-id="3c159-138">Using TransactionScope</span></span>  
 <span data-ttu-id="3c159-139">Sınıfı <xref:System.Transactions.TransactionScope> , dağıtılmış bir işlemdeki bağlantıları örtülü olarak listeleyerek bir kod bloğunu işlem yapar.</span><span class="sxs-lookup"><span data-stu-id="3c159-139">The <xref:System.Transactions.TransactionScope> class makes a code block transactional by implicitly enlisting connections in a distributed transaction.</span></span> <span data-ttu-id="3c159-140">Uygulamadan çıkmadan önce, <xref:System.Transactions.TransactionScope.Complete%2A> <xref:System.Transactions.TransactionScope> bloğunun sonundaki yöntemini çağırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3c159-140">You must call the <xref:System.Transactions.TransactionScope.Complete%2A> method at the end of the <xref:System.Transactions.TransactionScope> block before leaving it.</span></span> <span data-ttu-id="3c159-141">Bloğundan ayrıldığınızda <xref:System.Transactions.TransactionScope.Dispose%2A> yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="3c159-141">Leaving the block invokes the <xref:System.Transactions.TransactionScope.Dispose%2A> method.</span></span> <span data-ttu-id="3c159-142">Kodun kapsam olmasına neden olan bir özel durum oluşturulursa, işlem durduruldu olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="3c159-142">If an exception has been thrown that causes the code to leave scope, the transaction is considered aborted.</span></span>  
  
 <span data-ttu-id="3c159-143">Using bloğunun çıkış sırasında `using` <xref:System.Transactions.TransactionScope> nesne üzerinde çağrıldığından <xref:System.Transactions.TransactionScope.Dispose%2A> emin olmak için bir blok kullanmanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="3c159-143">We recommend that you use a `using` block to make sure that <xref:System.Transactions.TransactionScope.Dispose%2A> is called on the <xref:System.Transactions.TransactionScope> object when the using block is exited.</span></span> <span data-ttu-id="3c159-144">Bekleyen işlemleri tamamlama veya geri alma hatası, <xref:System.Transactions.TransactionScope> için varsayılan zaman aşımı bir dakika olduğundan performansı önemli ölçüde zarar verebilir.</span><span class="sxs-lookup"><span data-stu-id="3c159-144">Failure to commit or roll back pending transactions can significantly damage performance because the default time-out for the <xref:System.Transactions.TransactionScope> is one minute.</span></span> <span data-ttu-id="3c159-145">Bir `using` ifade kullanmıyorsanız, tüm işleri bir `Try` <xref:System.Transactions.TransactionScope.Dispose%2A> blokta gerçekleştirmeniz ve `Finally` blok içindeki yöntemi açıkça çağırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3c159-145">If you do not use a `using` statement, you must perform all work in a `Try` block and explicitly call the <xref:System.Transactions.TransactionScope.Dispose%2A> method in the `Finally` block.</span></span>  
  
 <span data-ttu-id="3c159-146">İçinde bir özel durum oluşursa <xref:System.Transactions.TransactionScope>, işlem tutarsız olarak işaretlenir ve terk edilir.</span><span class="sxs-lookup"><span data-stu-id="3c159-146">If an exception occurs in the <xref:System.Transactions.TransactionScope>, the transaction is marked as inconsistent and is abandoned.</span></span> <span data-ttu-id="3c159-147">Bırakıldığında <xref:System.Transactions.TransactionScope> geri alınacaktır.</span><span class="sxs-lookup"><span data-stu-id="3c159-147">It will be rolled back when the <xref:System.Transactions.TransactionScope> is disposed.</span></span> <span data-ttu-id="3c159-148">Özel durum oluşursa, katılım işlemleri işleme.</span><span class="sxs-lookup"><span data-stu-id="3c159-148">If no exception occurs, participating transactions commit.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3c159-149">Sınıfı `TransactionScope` , varsayılan `Serializable` olarak ' a <xref:System.Transactions.Transaction.IsolationLevel%2A> sahip bir işlem oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3c159-149">The `TransactionScope` class creates a transaction with a <xref:System.Transactions.Transaction.IsolationLevel%2A> of `Serializable` by default.</span></span> <span data-ttu-id="3c159-150">Uygulamanıza bağlı olarak, uygulamanızda yüksek çekişmeyi önlemek için yalıtım düzeyini azaltmayı düşünmek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3c159-150">Depending on your application, you might want to consider lowering the isolation level to avoid high contention in your application.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3c159-151">Dağıtılmış işlemler içinde yalnızca güncelleştirme, ekleme ve silme işlemlerini gerçekleştirmenizi öneririz, çünkü bunlar önemli veritabanı kaynakları tüketir.</span><span class="sxs-lookup"><span data-stu-id="3c159-151">We recommend that you perform only updates, inserts, and deletes within distributed transactions because they consume significant database resources.</span></span> <span data-ttu-id="3c159-152">Select deyimleri veritabanı kaynaklarını gereksiz şekilde kilitleyebilir ve bazı senaryolarda, seçim için işlemleri kullanmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="3c159-152">Select statements may lock database resources unnecessarily, and in some scenarios, you may have to use transactions for selects.</span></span> <span data-ttu-id="3c159-153">Veritabanı olmayan herhangi bir iş, diğer işlenen kaynak yöneticilerini içermiyorsa, işlem kapsamı dışında yapılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3c159-153">Any non-database work should be done outside the scope of the transaction, unless it involves other transacted resource managers.</span></span> <span data-ttu-id="3c159-154">İşlemin kapsamındaki bir özel durum işlemin uygulanmasını engelliyorsa, <xref:System.Transactions.TransactionScope> sınıfın, kodunuzun işlem kapsamı dışında yaptığı tüm değişiklikleri geri almak için bir sağlama yoktur.</span><span class="sxs-lookup"><span data-stu-id="3c159-154">Although an exception in the scope of the transaction prevents the transaction from committing, the <xref:System.Transactions.TransactionScope> class has no provision for rolling back any changes your code has made outside the scope of the transaction itself.</span></span> <span data-ttu-id="3c159-155">İşlem geri alındığında biraz işlem yapmanız gerekiyorsa, <xref:System.Transactions.IEnlistmentNotification> arabirimin kendi uygulamanızı yazmanız ve işlem içinde açıkça listelenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="3c159-155">If you have to take some action when the transaction is rolled back, you must write your own implementation of the <xref:System.Transactions.IEnlistmentNotification> interface and explicitly enlist in the transaction.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3c159-156">Örnek</span><span class="sxs-lookup"><span data-stu-id="3c159-156">Example</span></span>  
 <span data-ttu-id="3c159-157">İle <xref:System.Transactions> çalışma, System. Transactions. dll için bir başvuruya sahip olmanızı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="3c159-157">Working with <xref:System.Transactions> requires that you have a reference to System.Transactions.dll.</span></span>  
  
 <span data-ttu-id="3c159-158">Aşağıdaki işlev, iki farklı SQL Server örneğine karşı, bir <xref:System.Data.SqlClient.SqlConnection> <xref:System.Transactions.TransactionScope> blokta kaydırılan iki farklı nesne ile temsil edilen bir promotable işlemi oluşturmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="3c159-158">The following function demonstrates how to create a promotable transaction against two different SQL Server instances, represented by two different <xref:System.Data.SqlClient.SqlConnection> objects, which are wrapped in a <xref:System.Transactions.TransactionScope> block.</span></span> <span data-ttu-id="3c159-159">Kod, <xref:System.Transactions.TransactionScope> bloğu bir `using` ifadesiyle oluşturur ve ' de <xref:System.Transactions.TransactionScope>otomatik olarak listeleyen ilk bağlantıyı açar.</span><span class="sxs-lookup"><span data-stu-id="3c159-159">The code creates the <xref:System.Transactions.TransactionScope> block with a `using` statement and opens the first connection, which automatically enlists it in the <xref:System.Transactions.TransactionScope>.</span></span> <span data-ttu-id="3c159-160">İşlem başlangıçta, tam bir dağıtılmış işlem değil, hafif bir işlem olarak kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="3c159-160">The transaction is initially enlisted as a lightweight transaction, not a full distributed transaction.</span></span> <span data-ttu-id="3c159-161">İkinci bağlantı <xref:System.Transactions.TransactionScope> yalnızca ilk bağlantı içindeki komut bir özel durum oluşturmadığından kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="3c159-161">The second connection is enlisted in the <xref:System.Transactions.TransactionScope> only if the command in the first connection does not throw an exception.</span></span> <span data-ttu-id="3c159-162">İkinci bağlantı açıldığında, işlem otomatik olarak tam dağıtılmış bir işleme yükseltilir.</span><span class="sxs-lookup"><span data-stu-id="3c159-162">When the second connection is opened, the transaction is automatically promoted to a full distributed transaction.</span></span> <span data-ttu-id="3c159-163"><xref:System.Transactions.TransactionScope.Complete%2A> Yöntemi çağrılır, bu işlem yalnızca özel durum atılmadıkça işlemi kaydeder.</span><span class="sxs-lookup"><span data-stu-id="3c159-163">The <xref:System.Transactions.TransactionScope.Complete%2A> method is invoked, which commits the transaction only if no exceptions have been thrown.</span></span> <span data-ttu-id="3c159-164"><xref:System.Transactions.TransactionScope> Bir özel durum, `Complete` bloktaki herhangi bir noktada oluşturulursa, çağrılmaz ve bu, <xref:System.Transactions.TransactionScope> `using` bloğunun sonunda atıldığı zaman dağıtılmış işlem geri alınacaktır.</span><span class="sxs-lookup"><span data-stu-id="3c159-164">If an exception has been thrown at any point in the <xref:System.Transactions.TransactionScope> block, `Complete` will not be called, and the distributed transaction will roll back when the <xref:System.Transactions.TransactionScope> is disposed at the end of its `using` block.</span></span>  
  
```csharp  
// This function takes arguments for the 2 connection strings and commands in order  
// to create a transaction involving two SQL Servers. It returns a value > 0 if the  
// transaction committed, 0 if the transaction rolled back. To test this code, you can   
// connect to two different databases on the same server by altering the connection string,  
// or to another RDBMS such as Oracle by altering the code in the connection2 code block.  
static public int CreateTransactionScope(  
    string connectString1, string connectString2,  
    string commandText1, string commandText2)  
{  
    // Initialize the return value to zero and create a StringWriter to display results.  
    int returnValue = 0;  
    System.IO.StringWriter writer = new System.IO.StringWriter();  
  
    // Create the TransactionScope in which to execute the commands, guaranteeing  
    // that both commands will commit or roll back as a single unit of work.  
    using (TransactionScope scope = new TransactionScope())  
    {  
        using (SqlConnection connection1 = new SqlConnection(connectString1))  
        {  
            try  
            {  
                // Opening the connection automatically enlists it in the   
                // TransactionScope as a lightweight transaction.  
                connection1.Open();  
  
                // Create the SqlCommand object and execute the first command.  
                SqlCommand command1 = new SqlCommand(commandText1, connection1);  
                returnValue = command1.ExecuteNonQuery();  
                writer.WriteLine("Rows to be affected by command1: {0}", returnValue);  
  
                // if you get here, this means that command1 succeeded. By nesting  
                // the using block for connection2 inside that of connection1, you  
                // conserve server and network resources by opening connection2   
                // only when there is a chance that the transaction can commit.     
                using (SqlConnection connection2 = new SqlConnection(connectString2))  
                    try  
                    {  
                        // The transaction is promoted to a full distributed  
                        // transaction when connection2 is opened.  
                        connection2.Open();  
  
                        // Execute the second command in the second database.  
                        returnValue = 0;  
                        SqlCommand command2 = new SqlCommand(commandText2, connection2);  
                        returnValue = command2.ExecuteNonQuery();  
                        writer.WriteLine("Rows to be affected by command2: {0}", returnValue);  
                    }  
                    catch (Exception ex)  
                    {  
                        // Display information that command2 failed.  
                        writer.WriteLine("returnValue for command2: {0}", returnValue);  
                        writer.WriteLine("Exception Message2: {0}", ex.Message);  
                    }  
            }  
            catch (Exception ex)  
            {  
                // Display information that command1 failed.  
                writer.WriteLine("returnValue for command1: {0}", returnValue);  
                writer.WriteLine("Exception Message1: {0}", ex.Message);  
            }  
        }  
  
        // If an exception has been thrown, Complete will not   
        // be called and the transaction is rolled back.  
        scope.Complete();  
    }  
  
    // The returnValue is greater than 0 if the transaction committed.  
    if (returnValue > 0)  
    {  
        writer.WriteLine("Transaction was committed.");  
    }  
    else  
    {  
        // You could write additional business logic here, notify the caller by  
        // throwing a TransactionAbortedException, or log the failure.  
        writer.WriteLine("Transaction rolled back.");  
    }  
  
    // Display messages.  
    Console.WriteLine(writer.ToString());  
  
    return returnValue;  
}  
```  
  
```vb  
' This function takes arguments for the 2 connection strings and commands in order  
' to create a transaction involving two SQL Servers. It returns a value > 0 if the  
' transaction committed, 0 if the transaction rolled back. To test this code, you can   
' connect to two different databases on the same server by altering the connection string,  
' or to another RDBMS such as Oracle by altering the code in the connection2 code block.  
Public Function CreateTransactionScope( _  
  ByVal connectString1 As String, ByVal connectString2 As String, _  
  ByVal commandText1 As String, ByVal commandText2 As String) As Integer  
  
    ' Initialize the return value to zero and create a StringWriter to display results.  
    Dim returnValue As Integer = 0  
    Dim writer As System.IO.StringWriter = New System.IO.StringWriter  
  
    ' Create the TransactionScope in which to execute the commands, guaranteeing  
    ' that both commands will commit or roll back as a single unit of work.  
    Using scope As New TransactionScope()  
        Using connection1 As New SqlConnection(connectString1)  
            Try  
                ' Opening the connection automatically enlists it in the   
                ' TransactionScope as a lightweight transaction.  
                connection1.Open()  
  
                ' Create the SqlCommand object and execute the first command.  
                Dim command1 As SqlCommand = New SqlCommand(commandText1, connection1)  
                returnValue = command1.ExecuteNonQuery()  
                writer.WriteLine("Rows to be affected by command1: {0}", returnValue)  
  
                ' If you get here, this means that command1 succeeded. By nesting  
                ' the Using block for connection2 inside that of connection1, you  
                ' conserve server and network resources by opening connection2   
                ' only when there is a chance that the transaction can commit.     
                Using connection2 As New SqlConnection(connectString2)  
                    Try  
                        ' The transaction is promoted to a full distributed  
                        ' transaction when connection2 is opened.  
                        connection2.Open()  
  
                        ' Execute the second command in the second database.  
                        returnValue = 0  
                        Dim command2 As SqlCommand = New SqlCommand(commandText2, connection2)  
                        returnValue = command2.ExecuteNonQuery()  
                        writer.WriteLine("Rows to be affected by command2: {0}", returnValue)  
  
                    Catch ex As Exception  
                        ' Display information that command2 failed.  
                        writer.WriteLine("returnValue for command2: {0}", returnValue)  
                        writer.WriteLine("Exception Message2: {0}", ex.Message)  
                    End Try  
                End Using  
  
            Catch ex As Exception  
                ' Display information that command1 failed.  
                writer.WriteLine("returnValue for command1: {0}", returnValue)  
                writer.WriteLine("Exception Message1: {0}", ex.Message)  
            End Try  
        End Using  
  
        ' If an exception has been thrown, Complete will   
        ' not be called and the transaction is rolled back.  
        scope.Complete()  
    End Using  
  
    ' The returnValue is greater than 0 if the transaction committed.  
    If returnValue > 0 Then  
        writer.WriteLine("Transaction was committed.")  
    Else  
        ' You could write additional business logic here, notify the caller by  
        ' throwing a TransactionAbortedException, or log the failure.  
       writer.WriteLine("Transaction rolled back.")  
     End If  
  
    ' Display messages.  
    Console.WriteLine(writer.ToString())  
  
    Return returnValue  
End Function  
```  
  
## <a name="see-also"></a><span data-ttu-id="3c159-165">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3c159-165">See also</span></span>

- [<span data-ttu-id="3c159-166">İşlemler ve Eşzamanlılık</span><span class="sxs-lookup"><span data-stu-id="3c159-166">Transactions and Concurrency</span></span>](transactions-and-concurrency.md)
- [<span data-ttu-id="3c159-167">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="3c159-167">ADO.NET Overview</span></span>](ado-net-overview.md)
