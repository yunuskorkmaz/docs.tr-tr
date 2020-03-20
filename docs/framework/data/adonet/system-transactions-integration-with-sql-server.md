---
title: SQL Server ile System.Transactions Tümleştirmesi
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b555544e-7abb-4814-859b-ab9cdd7d8716
ms.openlocfilehash: 42007dafbdc9f61b9fc0776e0aaa2987551b704a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174244"
---
# <a name="systemtransactions-integration-with-sql-server"></a><span data-ttu-id="f73a9-102">SQL Server ile System.Transactions Tümleştirmesi</span><span class="sxs-lookup"><span data-stu-id="f73a9-102">System.Transactions Integration with SQL Server</span></span>
<span data-ttu-id="f73a9-103">.NET Framework sürüm <xref:System.Transactions> 2.0, ad alanı üzerinden erişilebilen bir işlem çerçevesi tanıttı.</span><span class="sxs-lookup"><span data-stu-id="f73a9-103">The .NET Framework version 2.0 introduced a transaction framework that can be accessed through the <xref:System.Transactions> namespace.</span></span> <span data-ttu-id="f73a9-104">Bu çerçeve, ADO.NET de dahil olmak üzere .NET Çerçevesi'ne tam olarak entegre edilmiş bir şekilde hareketleri ortaya çıkarır.</span><span class="sxs-lookup"><span data-stu-id="f73a9-104">This framework exposes transactions in a way that is fully integrated in the .NET Framework, including ADO.NET.</span></span>  
  
 <span data-ttu-id="f73a9-105">Programlanabilirlik geliştirmelerine ek <xref:System.Transactions> olarak ve ADO.NET, hareketlerle çalışırken optimizasyonları koordine etmek için birlikte çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="f73a9-105">In addition to the programmability enhancements, <xref:System.Transactions> and ADO.NET can work together to coordinate optimizations when you work with transactions.</span></span> <span data-ttu-id="f73a9-106">Tanıtılabilir işlem, gerektiğinde tam olarak dağıtılmış bir işlemiçin otomatik olarak yükseltilebilen hafif (yerel) bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="f73a9-106">A promotable transaction is a lightweight (local) transaction that can be automatically promoted to a fully distributed transaction on an as-needed basis.</span></span>  
  
 <span data-ttu-id="f73a9-107">2.0ADO.NET ile <xref:System.Data.SqlClient> başlayarak, SQL Server ile çalışırken tanıtılabilir işlemleri destekler.</span><span class="sxs-lookup"><span data-stu-id="f73a9-107">Starting with ADO.NET 2.0, <xref:System.Data.SqlClient> supports promotable transactions when you work with SQL Server.</span></span> <span data-ttu-id="f73a9-108">Eklenebilir bir işlem, eklenen ek yükü gerekli olmadıkça dağıtılmış bir işlemin eklenen ek yükü çağırmaz.</span><span class="sxs-lookup"><span data-stu-id="f73a9-108">A promotable transaction does not invoke the added overhead of a distributed transaction unless the added overhead is required.</span></span> <span data-ttu-id="f73a9-109">Tanıtılabilir işlemler otomatiktir ve geliştiricinin müdahalesi gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="f73a9-109">Promotable transactions are automatic and require no intervention from the developer.</span></span>  
  
 <span data-ttu-id="f73a9-110">Tanıtılabilir işlemler yalnızca SQL Server için .NET Framework Data`SqlClient`Provider () ile SQL Server ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f73a9-110">Promotable transactions are only available when you use the .NET Framework Data Provider for SQL Server (`SqlClient`) with SQL Server.</span></span>  
  
## <a name="creating-promotable-transactions"></a><span data-ttu-id="f73a9-111">Teşvik Edilebilir İşlemler Oluşturma</span><span class="sxs-lookup"><span data-stu-id="f73a9-111">Creating Promotable Transactions</span></span>  
 <span data-ttu-id="f73a9-112">SQL Server için .NET Framework Provider, .NET Framework <xref:System.Transactions> ad alanındaki sınıflar aracılığıyla işlenen teşvik edilebilir hareketler için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="f73a9-112">The .NET Framework Provider for SQL Server provides support for promotable transactions, which are handled through the classes in the .NET Framework <xref:System.Transactions> namespace.</span></span> <span data-ttu-id="f73a9-113">Tanıtılabilir hareketler, dağıtılmış bir hareket oluşturmayı gerekli olana kadar erteleyerek dağıtılmış hareketleri en iyi duruma getirin.</span><span class="sxs-lookup"><span data-stu-id="f73a9-113">Promotable transactions optimize distributed transactions by deferring creating a distributed transaction until it is needed.</span></span> <span data-ttu-id="f73a9-114">Yalnızca bir kaynak yöneticisi gerekiyorsa, dağıtılmış hareket oluşmaz.</span><span class="sxs-lookup"><span data-stu-id="f73a9-114">If only one resource manager is required, no distributed transaction occurs.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f73a9-115">Kısmen güvenilen bir senaryoda, <xref:System.Transactions.DistributedTransactionPermission> bir hareket dağıtılmış bir hareket için yükseltildiğinde gereklidir.</span><span class="sxs-lookup"><span data-stu-id="f73a9-115">In a partially trusted scenario, the <xref:System.Transactions.DistributedTransactionPermission> is required when a transaction is promoted to a distributed transaction.</span></span>  
  
## <a name="promotable-transaction-scenarios"></a><span data-ttu-id="f73a9-116">Teşvik Edilebilir İşlem Senaryoları</span><span class="sxs-lookup"><span data-stu-id="f73a9-116">Promotable Transaction Scenarios</span></span>  
 <span data-ttu-id="f73a9-117">Dağıtılmış hareketler genellikle, harekette erişilen tüm kaynak yöneticilerini tümleştiren Microsoft Dağıtılmış Hareket Koordinatörü (MS DTC) tarafından yönetilen önemli sistem kaynaklarını tüketir.</span><span class="sxs-lookup"><span data-stu-id="f73a9-117">Distributed transactions typically consume significant system resources, being managed by Microsoft Distributed Transaction Coordinator (MS DTC), which integrates all the resource managers accessed in the transaction.</span></span> <span data-ttu-id="f73a9-118">Tanıtılabilir işlem, işi basit <xref:System.Transactions> bir SQL Server hareketine etkili bir şekilde devreden özel bir işlem biçimidir.</span><span class="sxs-lookup"><span data-stu-id="f73a9-118">A promotable transaction is a special form of a <xref:System.Transactions> transaction that effectively delegates the work to a simple SQL Server transaction.</span></span> <span data-ttu-id="f73a9-119"><xref:System.Transactions>, <xref:System.Data.SqlClient>ve SQL Server, hareketi işlemede yer alan işi koordine ederek gerektiğinde tam dağıtılmış bir işleme teşvik etmeyi sağlar.</span><span class="sxs-lookup"><span data-stu-id="f73a9-119"><xref:System.Transactions>, <xref:System.Data.SqlClient>, and SQL Server coordinate the work involved in handling the transaction, promoting it to a full distributed transaction as needed.</span></span>  
  
 <span data-ttu-id="f73a9-120">Tanıtılabilir hareketleri kullanmanın yararı, bir bağlantı etkin <xref:System.Transactions.TransactionScope> bir işlem kullanılarak açıldığında ve başka bağlantı açılmadığında, hareketin tam dağıtılmış bir işlemin ek ek yüküne maruz kalarak hafif bir işlem olarak işlemesidir.</span><span class="sxs-lookup"><span data-stu-id="f73a9-120">The benefit of using promotable transactions is that when a connection is opened by using an active <xref:System.Transactions.TransactionScope> transaction, and no other connections are opened, the transaction commits as a lightweight transaction, instead of incurring the additional overhead of a full distributed transaction.</span></span>  
  
### <a name="connection-string-keywords"></a><span data-ttu-id="f73a9-121">Bağlantı String Anahtar Kelimeler</span><span class="sxs-lookup"><span data-stu-id="f73a9-121">Connection String Keywords</span></span>  
 <span data-ttu-id="f73a9-122">Özellik, <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> `Enlist`işlem bağlamlarını algılayıp <xref:System.Data.SqlClient> algılamayacağını ve dağıtılmış bir hareketteki bağlantıyı otomatik olarak kaydedip kaydetmeyeceğini belirten bir anahtar kelimeyi destekler.</span><span class="sxs-lookup"><span data-stu-id="f73a9-122">The <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> property supports a keyword, `Enlist`, which indicates whether <xref:System.Data.SqlClient> will detect transactional contexts and automatically enlist the connection in a distributed transaction.</span></span> <span data-ttu-id="f73a9-123">`Enlist=true`, bağlantı otomatik olarak açılış iş parçacığının geçerli hareket bağlamında kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="f73a9-123">If `Enlist=true`, the connection is automatically enlisted in the opening thread's current transaction context.</span></span> <span data-ttu-id="f73a9-124">`Enlist=false`, bağlantı dağıtılmış bir hareketle etkileşime girmiyorsa. `SqlClient`</span><span class="sxs-lookup"><span data-stu-id="f73a9-124">If `Enlist=false`, the `SqlClient` connection does not interact with a distributed transaction.</span></span> <span data-ttu-id="f73a9-125">Varsayılan değer `Enlist` doğrudur.</span><span class="sxs-lookup"><span data-stu-id="f73a9-125">The default value for `Enlist` is true.</span></span> <span data-ttu-id="f73a9-126">Bağlantı `Enlist` dizesinde belirtilmemişse, bağlantı açıldığında biri algılanırsa, bağlantı otomatik olarak dağıtılmış bir harekette kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="f73a9-126">If `Enlist` is not specified in the connection string, the connection is automatically enlisted in a distributed transaction if one is detected when the connection is opened.</span></span>  
  
 <span data-ttu-id="f73a9-127">Bağlantı dizesindeki anahtar kelimeler, bağlantının `System.Transactions` kayıtlı bir hareketle ilişkisini denetler. `Transaction Binding` <xref:System.Data.SqlClient.SqlConnection></span><span class="sxs-lookup"><span data-stu-id="f73a9-127">The `Transaction Binding` keywords in a <xref:System.Data.SqlClient.SqlConnection> connection string control the connection's association with an enlisted `System.Transactions` transaction.</span></span> <span data-ttu-id="f73a9-128">Ayrıca bir <xref:System.Data.SqlClient.SqlConnectionStringBuilder.TransactionBinding%2A> <xref:System.Data.SqlClient.SqlConnectionStringBuilder>özelliği üzerinden kullanılabilir .</span><span class="sxs-lookup"><span data-stu-id="f73a9-128">It is also available through the <xref:System.Data.SqlClient.SqlConnectionStringBuilder.TransactionBinding%2A> property of a <xref:System.Data.SqlClient.SqlConnectionStringBuilder>.</span></span>  
  
 <span data-ttu-id="f73a9-129">Aşağıdaki tabloda olası değerler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f73a9-129">The following table describes the possible values.</span></span>  
  
|<span data-ttu-id="f73a9-130">Anahtar kelime</span><span class="sxs-lookup"><span data-stu-id="f73a9-130">Keyword</span></span>|<span data-ttu-id="f73a9-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f73a9-131">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f73a9-132">Örtük Unbind</span><span class="sxs-lookup"><span data-stu-id="f73a9-132">Implicit Unbind</span></span>|<span data-ttu-id="f73a9-133">Varsayılan.</span><span class="sxs-lookup"><span data-stu-id="f73a9-133">The default.</span></span> <span data-ttu-id="f73a9-134">Bağlantı sona erdiğinde işlemden ayrılır ve otomatik işleme moduna geri döner.</span><span class="sxs-lookup"><span data-stu-id="f73a9-134">The connection detaches from the transaction when it ends, switching back to autocommit mode.</span></span>|  
|<span data-ttu-id="f73a9-135">Açık Unbind</span><span class="sxs-lookup"><span data-stu-id="f73a9-135">Explicit Unbind</span></span>|<span data-ttu-id="f73a9-136">Hareket kapanana kadar bağlantı hareketbağlı kalır.</span><span class="sxs-lookup"><span data-stu-id="f73a9-136">The connection remains attached to the transaction until the transaction is closed.</span></span> <span data-ttu-id="f73a9-137">İlişkili hareket etkin değilse veya eşleşmezse <xref:System.Transactions.Transaction.Current%2A>bağlantı başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="f73a9-137">The connection will fail if the associated transaction is not active or does not match <xref:System.Transactions.Transaction.Current%2A>.</span></span>|  
  
## <a name="using-transactionscope"></a><span data-ttu-id="f73a9-138">İşlem Kapsamını Kullanma</span><span class="sxs-lookup"><span data-stu-id="f73a9-138">Using TransactionScope</span></span>  
 <span data-ttu-id="f73a9-139">Sınıf, <xref:System.Transactions.TransactionScope> dağıtılmış bir hareketteki bağlantıları dolaylı olarak kaydederek bir kod bloğu hareketi yapar.</span><span class="sxs-lookup"><span data-stu-id="f73a9-139">The <xref:System.Transactions.TransactionScope> class makes a code block transactional by implicitly enlisting connections in a distributed transaction.</span></span> <span data-ttu-id="f73a9-140">Ayrılmadan <xref:System.Transactions.TransactionScope.Complete%2A> önce <xref:System.Transactions.TransactionScope> yöntemi bloğun sonundan aramalısınız.</span><span class="sxs-lookup"><span data-stu-id="f73a9-140">You must call the <xref:System.Transactions.TransactionScope.Complete%2A> method at the end of the <xref:System.Transactions.TransactionScope> block before leaving it.</span></span> <span data-ttu-id="f73a9-141">Bloğu terk etme <xref:System.Transactions.TransactionScope.Dispose%2A> yöntemi çağırır.</span><span class="sxs-lookup"><span data-stu-id="f73a9-141">Leaving the block invokes the <xref:System.Transactions.TransactionScope.Dispose%2A> method.</span></span> <span data-ttu-id="f73a9-142">Kodun kapsam bırakmasına neden olan bir özel durum atılırsa, işlem iptal edilmiş sayılır.</span><span class="sxs-lookup"><span data-stu-id="f73a9-142">If an exception has been thrown that causes the code to leave scope, the transaction is considered aborted.</span></span>  
  
 <span data-ttu-id="f73a9-143">Kullanma bloğu çıkarıldığında `using` <xref:System.Transactions.TransactionScope.Dispose%2A> <xref:System.Transactions.TransactionScope> nesneüzerinde çağrıldığınızdan emin olmak için bir blok kullanmanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="f73a9-143">We recommend that you use a `using` block to make sure that <xref:System.Transactions.TransactionScope.Dispose%2A> is called on the <xref:System.Transactions.TransactionScope> object when the using block is exited.</span></span> <span data-ttu-id="f73a9-144">Bekleyen işlemlerin yapılmaması veya geri alınmaması, varsayılan zaman <xref:System.Transactions.TransactionScope> kaybı bir dakika olduğundan performansa önemli ölçüde zarar verebilir.</span><span class="sxs-lookup"><span data-stu-id="f73a9-144">Failure to commit or roll back pending transactions can significantly damage performance because the default time-out for the <xref:System.Transactions.TransactionScope> is one minute.</span></span> <span data-ttu-id="f73a9-145">Bir `using` deyim kullanmazsanız, tüm çalışmaları bir `Try` blokta gerçekleştirmeniz <xref:System.Transactions.TransactionScope.Dispose%2A> ve `Finally` yöntemin açıkça blokta çağrılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f73a9-145">If you do not use a `using` statement, you must perform all work in a `Try` block and explicitly call the <xref:System.Transactions.TransactionScope.Dispose%2A> method in the `Finally` block.</span></span>  
  
 <span data-ttu-id="f73a9-146">Bir özel durum <xref:System.Transactions.TransactionScope>oluşursa, hareket tutarsız olarak işaretlenir ve terk edilir.</span><span class="sxs-lookup"><span data-stu-id="f73a9-146">If an exception occurs in the <xref:System.Transactions.TransactionScope>, the transaction is marked as inconsistent and is abandoned.</span></span> <span data-ttu-id="f73a9-147">Bertaraf edildiğinde <xref:System.Transactions.TransactionScope> geri alınır.</span><span class="sxs-lookup"><span data-stu-id="f73a9-147">It will be rolled back when the <xref:System.Transactions.TransactionScope> is disposed.</span></span> <span data-ttu-id="f73a9-148">Bir istisna oluşmazsa, katılımcı hareketler gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="f73a9-148">If no exception occurs, participating transactions commit.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f73a9-149">Sınıf `TransactionScope` varsayılan olarak a <xref:System.Transactions.Transaction.IsolationLevel%2A> `Serializable` ile bir hareket oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f73a9-149">The `TransactionScope` class creates a transaction with a <xref:System.Transactions.Transaction.IsolationLevel%2A> of `Serializable` by default.</span></span> <span data-ttu-id="f73a9-150">Uygulamanıza bağlı olarak, uygulamanızda yüksek çekişmeyi önlemek için yalıtım düzeyini düşürmeyi düşünebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f73a9-150">Depending on your application, you might want to consider lowering the isolation level to avoid high contention in your application.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f73a9-151">Önemli veritabanı kaynaklarını tükettikleri için yalnızca dağıtılmış hareketler içinde güncelleştirmeler, ekler ve silmeler gerçekleştirmenizi öneririz.</span><span class="sxs-lookup"><span data-stu-id="f73a9-151">We recommend that you perform only updates, inserts, and deletes within distributed transactions because they consume significant database resources.</span></span> <span data-ttu-id="f73a9-152">Select deyimleri veritabanı kaynaklarını gereksiz yere kilitleyebilir ve bazı senaryolarda, hareketlerin seçim için kullanılması gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="f73a9-152">Select statements may lock database resources unnecessarily, and in some scenarios, you may have to use transactions for selects.</span></span> <span data-ttu-id="f73a9-153">Diğer işlenen kaynak yöneticileri içermediği sürece, veritabanı dışındaki tüm çalışmalar işlemin kapsamı dışında yapılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f73a9-153">Any non-database work should be done outside the scope of the transaction, unless it involves other transacted resource managers.</span></span> <span data-ttu-id="f73a9-154">İşlem kapsamındaki bir özel durum işlemin yapılmasını engellese <xref:System.Transactions.TransactionScope> de, sınıfın kodunuzun hareketin kapsamı dışında yaptığı değişiklikleri geri alma hükmü yoktur.</span><span class="sxs-lookup"><span data-stu-id="f73a9-154">Although an exception in the scope of the transaction prevents the transaction from committing, the <xref:System.Transactions.TransactionScope> class has no provision for rolling back any changes your code has made outside the scope of the transaction itself.</span></span> <span data-ttu-id="f73a9-155">İşlem geri alınırken bazı işlemler yapmak zorundaysanız, <xref:System.Transactions.IEnlistmentNotification> arabirimin kendi uygulamanızı yazmanız ve açıkça harekete kaydolmalısınız.</span><span class="sxs-lookup"><span data-stu-id="f73a9-155">If you have to take some action when the transaction is rolled back, you must write your own implementation of the <xref:System.Transactions.IEnlistmentNotification> interface and explicitly enlist in the transaction.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f73a9-156">Örnek</span><span class="sxs-lookup"><span data-stu-id="f73a9-156">Example</span></span>  
 <span data-ttu-id="f73a9-157">Birlikte <xref:System.Transactions> çalışmak, System.Transactions.dll adresine bir referansıniz olmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="f73a9-157">Working with <xref:System.Transactions> requires that you have a reference to System.Transactions.dll.</span></span>  
  
 <span data-ttu-id="f73a9-158">Aşağıdaki işlev, bir bloksarılmış iki farklı nesne tarafından temsil edilen iki farklı <xref:System.Data.SqlClient.SqlConnection> SQL Server örneğine karşı <xref:System.Transactions.TransactionScope> nasıl teşvik edilebilir bir işlem oluşturulabilir olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="f73a9-158">The following function demonstrates how to create a promotable transaction against two different SQL Server instances, represented by two different <xref:System.Data.SqlClient.SqlConnection> objects, which are wrapped in a <xref:System.Transactions.TransactionScope> block.</span></span> <span data-ttu-id="f73a9-159">Kod bir <xref:System.Transactions.TransactionScope> `using` deyimle bloğu oluşturur ve ilk bağlantıyı açar ve bu <xref:System.Transactions.TransactionScope>bağlantı otomatik olarak .</span><span class="sxs-lookup"><span data-stu-id="f73a9-159">The code creates the <xref:System.Transactions.TransactionScope> block with a `using` statement and opens the first connection, which automatically enlists it in the <xref:System.Transactions.TransactionScope>.</span></span> <span data-ttu-id="f73a9-160">Hareket başlangıçta tam dağıtılmış bir işlem olarak değil, hafif bir işlem olarak kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="f73a9-160">The transaction is initially enlisted as a lightweight transaction, not a full distributed transaction.</span></span> <span data-ttu-id="f73a9-161">İkinci bağlantı, yalnızca ilk <xref:System.Transactions.TransactionScope> bağlantıdaki komut bir özel durum atmazsa kaydolur.</span><span class="sxs-lookup"><span data-stu-id="f73a9-161">The second connection is enlisted in the <xref:System.Transactions.TransactionScope> only if the command in the first connection does not throw an exception.</span></span> <span data-ttu-id="f73a9-162">İkinci bağlantı açıldığında, hareket otomatik olarak tam dağıtılmış bir hareket için yükseltilir.</span><span class="sxs-lookup"><span data-stu-id="f73a9-162">When the second connection is opened, the transaction is automatically promoted to a full distributed transaction.</span></span> <span data-ttu-id="f73a9-163">Yöntem, <xref:System.Transactions.TransactionScope.Complete%2A> yalnızca özel durumlar atılmadıysa hareketi gerçekleştiren çağrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="f73a9-163">The <xref:System.Transactions.TransactionScope.Complete%2A> method is invoked, which commits the transaction only if no exceptions have been thrown.</span></span> <span data-ttu-id="f73a9-164"><xref:System.Transactions.TransactionScope> Bloğun herhangi bir noktasında bir özel durum `Complete` atılırsa, çağrılmaz ve dağıtılmış hareket <xref:System.Transactions.TransactionScope> `using` bloğunun sonunda imha edildiğinde geri döner.</span><span class="sxs-lookup"><span data-stu-id="f73a9-164">If an exception has been thrown at any point in the <xref:System.Transactions.TransactionScope> block, `Complete` will not be called, and the distributed transaction will roll back when the <xref:System.Transactions.TransactionScope> is disposed at the end of its `using` block.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f73a9-165">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f73a9-165">See also</span></span>

- [<span data-ttu-id="f73a9-166">İşlemler ve Eşzamanlılık</span><span class="sxs-lookup"><span data-stu-id="f73a9-166">Transactions and Concurrency</span></span>](transactions-and-concurrency.md)
- [<span data-ttu-id="f73a9-167">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="f73a9-167">ADO.NET Overview</span></span>](ado-net-overview.md)
