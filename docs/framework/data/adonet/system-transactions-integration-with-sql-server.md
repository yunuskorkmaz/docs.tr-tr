---
description: 'Hakkında daha fazla bilgi edinin: SQL Server ile System. Transactions tümleştirmesi'
title: SQL Server ile System.Transactions Tümleştirmesi
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b555544e-7abb-4814-859b-ab9cdd7d8716
ms.openlocfilehash: 977ff18600256613dabc0212c2f7aa1bc2650408
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99766783"
---
# <a name="systemtransactions-integration-with-sql-server"></a><span data-ttu-id="55b41-103">SQL Server ile System.Transactions Tümleştirmesi</span><span class="sxs-lookup"><span data-stu-id="55b41-103">System.Transactions Integration with SQL Server</span></span>

<span data-ttu-id="55b41-104">.NET Framework sürüm 2,0, ad alanı aracılığıyla erişilebilen bir işlem çerçevesi sunmuştur <xref:System.Transactions> .</span><span class="sxs-lookup"><span data-stu-id="55b41-104">The .NET Framework version 2.0 introduced a transaction framework that can be accessed through the <xref:System.Transactions> namespace.</span></span> <span data-ttu-id="55b41-105">Bu çerçeve, ADO.NET dahil olmak üzere .NET Framework, işlemleri tam olarak tümleştirilmiş bir şekilde kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="55b41-105">This framework exposes transactions in a way that is fully integrated in the .NET Framework, including ADO.NET.</span></span>  
  
 <span data-ttu-id="55b41-106">Programlama iyileştirmelerine ek olarak, <xref:System.Transactions> işlemler ile çalışırken iyileştirmeleri koordine etmek için ADO.net birlikte çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="55b41-106">In addition to the programmability enhancements, <xref:System.Transactions> and ADO.NET can work together to coordinate optimizations when you work with transactions.</span></span> <span data-ttu-id="55b41-107">Bir promotable işlemi, tam olarak dağıtılan bir işlem için gereken bir şekilde otomatik olarak yükseltilabilecek hafif (yerel) bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="55b41-107">A promotable transaction is a lightweight (local) transaction that can be automatically promoted to a fully distributed transaction on an as-needed basis.</span></span>  
  
 <span data-ttu-id="55b41-108">ADO.NET 2,0 ile başlayarak, <xref:System.Data.SqlClient> SQL Server çalışırken promotable işlemlerini destekler.</span><span class="sxs-lookup"><span data-stu-id="55b41-108">Starting with ADO.NET 2.0, <xref:System.Data.SqlClient> supports promotable transactions when you work with SQL Server.</span></span> <span data-ttu-id="55b41-109">Bir promotable işlemi, eklenen ek yük gerekmediği takdirde dağıtılmış bir işlemin ek yükünü çağırmaz.</span><span class="sxs-lookup"><span data-stu-id="55b41-109">A promotable transaction does not invoke the added overhead of a distributed transaction unless the added overhead is required.</span></span> <span data-ttu-id="55b41-110">Promotable işlemleri otomatiktir ve geliştiriciden müdahale gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="55b41-110">Promotable transactions are automatic and require no intervention from the developer.</span></span>  
  
 <span data-ttu-id="55b41-111">Promotable işlemleri yalnızca SQL Server ile SQL Server () için .NET Framework Veri Sağlayıcısı kullandığınızda kullanılabilir `SqlClient` .</span><span class="sxs-lookup"><span data-stu-id="55b41-111">Promotable transactions are only available when you use the .NET Framework Data Provider for SQL Server (`SqlClient`) with SQL Server.</span></span>  
  
## <a name="creating-promotable-transactions"></a><span data-ttu-id="55b41-112">Promotable Işlemleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="55b41-112">Creating Promotable Transactions</span></span>  

 <span data-ttu-id="55b41-113">SQL Server için .NET Framework sağlayıcısı, .NET Framework ad alanındaki sınıflar aracılığıyla işlenen promotable işlemleri için destek sağlar <xref:System.Transactions> .</span><span class="sxs-lookup"><span data-stu-id="55b41-113">The .NET Framework Provider for SQL Server provides support for promotable transactions, which are handled through the classes in the .NET Framework <xref:System.Transactions> namespace.</span></span> <span data-ttu-id="55b41-114">Promotable işlemleri, dağıtılmış bir işlemin oluşturulması gerekene kadar erteleyerek dağıtılmış işlemleri iyileştirir.</span><span class="sxs-lookup"><span data-stu-id="55b41-114">Promotable transactions optimize distributed transactions by deferring creating a distributed transaction until it is needed.</span></span> <span data-ttu-id="55b41-115">Yalnızca bir kaynak yöneticisi gerekliyse, dağıtılmış işlem gerçekleşmez.</span><span class="sxs-lookup"><span data-stu-id="55b41-115">If only one resource manager is required, no distributed transaction occurs.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="55b41-116">Kısmen güvenilen bir senaryoda, <xref:System.Transactions.DistributedTransactionPermission> bir işlem dağıtılmış bir işleme yükseltildiğinde gereklidir.</span><span class="sxs-lookup"><span data-stu-id="55b41-116">In a partially trusted scenario, the <xref:System.Transactions.DistributedTransactionPermission> is required when a transaction is promoted to a distributed transaction.</span></span>  
  
## <a name="promotable-transaction-scenarios"></a><span data-ttu-id="55b41-117">Promotable Işlem senaryoları</span><span class="sxs-lookup"><span data-stu-id="55b41-117">Promotable Transaction Scenarios</span></span>  

 <span data-ttu-id="55b41-118">Dağıtılmış işlemler genellikle Microsoft Dağıtılmış İşlem Düzenleyicisi (MS DTC) tarafından yönetilmekte olan önemli sistem kaynaklarını kullanır ve böylece işlem sırasında erişilen tüm kaynak yöneticileri tümleştirilir.</span><span class="sxs-lookup"><span data-stu-id="55b41-118">Distributed transactions typically consume significant system resources, being managed by Microsoft Distributed Transaction Coordinator (MS DTC), which integrates all the resource managers accessed in the transaction.</span></span> <span data-ttu-id="55b41-119">Bir promotable işlemi, <xref:System.Transactions> işi etkin bir şekilde basit bir SQL Server işlem olarak temsil eden bir işlemin özel bir biçimidir.</span><span class="sxs-lookup"><span data-stu-id="55b41-119">A promotable transaction is a special form of a <xref:System.Transactions> transaction that effectively delegates the work to a simple SQL Server transaction.</span></span> <span data-ttu-id="55b41-120"><xref:System.Transactions>, <xref:System.Data.SqlClient> ve SQL Server işlem işleme dahil işi koordine etmek ve gerektiğinde tam dağıtılmış bir işleme yükseltmek.</span><span class="sxs-lookup"><span data-stu-id="55b41-120"><xref:System.Transactions>, <xref:System.Data.SqlClient>, and SQL Server coordinate the work involved in handling the transaction, promoting it to a full distributed transaction as needed.</span></span>  
  
 <span data-ttu-id="55b41-121">Promotable işlemleri kullanmanın avantajı, bir bağlantının etkin bir işlem kullanılarak açıldığı <xref:System.Transactions.TransactionScope> ve başka hiçbir bağlantının açılmadığı durumlarda, bir tam dağıtılmış işlemin ek yükünü ortadan kaldırarak, işlemin hafif bir işlem olarak işlemeleridir.</span><span class="sxs-lookup"><span data-stu-id="55b41-121">The benefit of using promotable transactions is that when a connection is opened by using an active <xref:System.Transactions.TransactionScope> transaction, and no other connections are opened, the transaction commits as a lightweight transaction, instead of incurring the additional overhead of a full distributed transaction.</span></span>  
  
### <a name="connection-string-keywords"></a><span data-ttu-id="55b41-122">Bağlantı dizesi anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="55b41-122">Connection String Keywords</span></span>  

 <span data-ttu-id="55b41-123"><xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>Özelliği, `Enlist` <xref:System.Data.SqlClient> işlem bağlamlarının etkinleştirilip etkinleştirilmeyeceğini ve bağlantıyı dağıtılmış bir işlemde otomatik olarak Enlist olup olmayacağını gösteren bir anahtar sözcüğü destekler.</span><span class="sxs-lookup"><span data-stu-id="55b41-123">The <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> property supports a keyword, `Enlist`, which indicates whether <xref:System.Data.SqlClient> will detect transactional contexts and automatically enlist the connection in a distributed transaction.</span></span> <span data-ttu-id="55b41-124">Varsa `Enlist=true` , bağlantı, açma iş parçacığının geçerli işlem bağlamına otomatik olarak kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="55b41-124">If `Enlist=true`, the connection is automatically enlisted in the opening thread's current transaction context.</span></span> <span data-ttu-id="55b41-125">Varsa `Enlist=false` , `SqlClient` bağlantı dağıtılmış bir işlemle etkileşime girmez.</span><span class="sxs-lookup"><span data-stu-id="55b41-125">If `Enlist=false`, the `SqlClient` connection does not interact with a distributed transaction.</span></span> <span data-ttu-id="55b41-126">Varsayılan değeri `Enlist` true 'dur.</span><span class="sxs-lookup"><span data-stu-id="55b41-126">The default value for `Enlist` is true.</span></span> <span data-ttu-id="55b41-127">Bağlantı `Enlist` dizesinde belirtilmemişse bağlantı, bağlantı açıldığında algılanan bir dağıtılmış işlemde otomatik olarak kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="55b41-127">If `Enlist` is not specified in the connection string, the connection is automatically enlisted in a distributed transaction if one is detected when the connection is opened.</span></span>  
  
 <span data-ttu-id="55b41-128">`Transaction Binding`Bir bağlantı dizesindeki anahtar sözcükler, <xref:System.Data.SqlClient.SqlConnection> kayıtlı bir işlemle bağlantının ilişkilendirmesini denetler `System.Transactions` .</span><span class="sxs-lookup"><span data-stu-id="55b41-128">The `Transaction Binding` keywords in a <xref:System.Data.SqlClient.SqlConnection> connection string control the connection's association with an enlisted `System.Transactions` transaction.</span></span> <span data-ttu-id="55b41-129">Ayrıca, öğesinin özelliği aracılığıyla da kullanılabilir <xref:System.Data.SqlClient.SqlConnectionStringBuilder.TransactionBinding%2A> <xref:System.Data.SqlClient.SqlConnectionStringBuilder> .</span><span class="sxs-lookup"><span data-stu-id="55b41-129">It is also available through the <xref:System.Data.SqlClient.SqlConnectionStringBuilder.TransactionBinding%2A> property of a <xref:System.Data.SqlClient.SqlConnectionStringBuilder>.</span></span>  
  
 <span data-ttu-id="55b41-130">Aşağıdaki tabloda olası değerler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="55b41-130">The following table describes the possible values.</span></span>  
  
|<span data-ttu-id="55b41-131">Sözcükle</span><span class="sxs-lookup"><span data-stu-id="55b41-131">Keyword</span></span>|<span data-ttu-id="55b41-132">Description</span><span class="sxs-lookup"><span data-stu-id="55b41-132">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="55b41-133">Örtük bağlantı kesme</span><span class="sxs-lookup"><span data-stu-id="55b41-133">Implicit Unbind</span></span>|<span data-ttu-id="55b41-134">Varsayılan.</span><span class="sxs-lookup"><span data-stu-id="55b41-134">The default.</span></span> <span data-ttu-id="55b41-135">Bağlantı, sona erdiğinde işlemden ayrıldığında, tekrar tekrar yürütme moduna geçiş yapın.</span><span class="sxs-lookup"><span data-stu-id="55b41-135">The connection detaches from the transaction when it ends, switching back to autocommit mode.</span></span>|  
|<span data-ttu-id="55b41-136">Açık ciltten çıkarma</span><span class="sxs-lookup"><span data-stu-id="55b41-136">Explicit Unbind</span></span>|<span data-ttu-id="55b41-137">İşlem kapatılıncaya kadar bağlantı işleme bağlı kalır.</span><span class="sxs-lookup"><span data-stu-id="55b41-137">The connection remains attached to the transaction until the transaction is closed.</span></span> <span data-ttu-id="55b41-138">İlişkili işlem etkin değilse veya eşleşmezse bağlantı başarısız olur <xref:System.Transactions.Transaction.Current%2A> .</span><span class="sxs-lookup"><span data-stu-id="55b41-138">The connection will fail if the associated transaction is not active or does not match <xref:System.Transactions.Transaction.Current%2A>.</span></span>|  
  
## <a name="using-transactionscope"></a><span data-ttu-id="55b41-139">TransactionScope kullanma</span><span class="sxs-lookup"><span data-stu-id="55b41-139">Using TransactionScope</span></span>  

 <span data-ttu-id="55b41-140"><xref:System.Transactions.TransactionScope>Sınıfı, dağıtılmış bir işlemdeki bağlantıları örtülü olarak listeleyerek bir kod bloğunu işlem yapar.</span><span class="sxs-lookup"><span data-stu-id="55b41-140">The <xref:System.Transactions.TransactionScope> class makes a code block transactional by implicitly enlisting connections in a distributed transaction.</span></span> <span data-ttu-id="55b41-141"><xref:System.Transactions.TransactionScope.Complete%2A>Uygulamadan çıkmadan önce, bloğunun sonundaki yöntemini çağırmanız gerekir <xref:System.Transactions.TransactionScope> .</span><span class="sxs-lookup"><span data-stu-id="55b41-141">You must call the <xref:System.Transactions.TransactionScope.Complete%2A> method at the end of the <xref:System.Transactions.TransactionScope> block before leaving it.</span></span> <span data-ttu-id="55b41-142">Bloğundan ayrıldığınızda yöntemini çağırır <xref:System.Transactions.TransactionScope.Dispose%2A> .</span><span class="sxs-lookup"><span data-stu-id="55b41-142">Leaving the block invokes the <xref:System.Transactions.TransactionScope.Dispose%2A> method.</span></span> <span data-ttu-id="55b41-143">Kodun kapsam olmasına neden olan bir özel durum oluşturulursa, işlem durduruldu olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="55b41-143">If an exception has been thrown that causes the code to leave scope, the transaction is considered aborted.</span></span>  
  
 <span data-ttu-id="55b41-144">`using` <xref:System.Transactions.TransactionScope.Dispose%2A> <xref:System.Transactions.TransactionScope> Using bloğunun çıkış sırasında nesne üzerinde çağrıldığından emin olmak için bir blok kullanmanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="55b41-144">We recommend that you use a `using` block to make sure that <xref:System.Transactions.TransactionScope.Dispose%2A> is called on the <xref:System.Transactions.TransactionScope> object when the using block is exited.</span></span> <span data-ttu-id="55b41-145">Bekleyen işlemleri tamamlama veya geri alma hatası, için varsayılan zaman aşımı bir dakika olduğundan performansı önemli ölçüde zarar verebilir <xref:System.Transactions.TransactionScope> .</span><span class="sxs-lookup"><span data-stu-id="55b41-145">Failure to commit or roll back pending transactions can significantly damage performance because the default time-out for the <xref:System.Transactions.TransactionScope> is one minute.</span></span> <span data-ttu-id="55b41-146">Bir `using` ifade kullanmıyorsanız, tüm işleri bir `Try` blokta gerçekleştirmeniz ve <xref:System.Transactions.TransactionScope.Dispose%2A> blok içindeki yöntemi açıkça çağırmanız gerekir `Finally` .</span><span class="sxs-lookup"><span data-stu-id="55b41-146">If you do not use a `using` statement, you must perform all work in a `Try` block and explicitly call the <xref:System.Transactions.TransactionScope.Dispose%2A> method in the `Finally` block.</span></span>  
  
 <span data-ttu-id="55b41-147">İçinde bir özel durum oluşursa <xref:System.Transactions.TransactionScope> , işlem tutarsız olarak işaretlenir ve terk edilir.</span><span class="sxs-lookup"><span data-stu-id="55b41-147">If an exception occurs in the <xref:System.Transactions.TransactionScope>, the transaction is marked as inconsistent and is abandoned.</span></span> <span data-ttu-id="55b41-148">Bırakıldığında geri alınacaktır <xref:System.Transactions.TransactionScope> .</span><span class="sxs-lookup"><span data-stu-id="55b41-148">It will be rolled back when the <xref:System.Transactions.TransactionScope> is disposed.</span></span> <span data-ttu-id="55b41-149">Özel durum oluşursa, katılım işlemleri işleme.</span><span class="sxs-lookup"><span data-stu-id="55b41-149">If no exception occurs, participating transactions commit.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="55b41-150">`TransactionScope`Sınıfı, <xref:System.Transactions.Transaction.IsolationLevel%2A> Varsayılan olarak ' a sahip bir işlem oluşturur `Serializable` .</span><span class="sxs-lookup"><span data-stu-id="55b41-150">The `TransactionScope` class creates a transaction with a <xref:System.Transactions.Transaction.IsolationLevel%2A> of `Serializable` by default.</span></span> <span data-ttu-id="55b41-151">Uygulamanıza bağlı olarak, uygulamanızda yüksek çekişmeyi önlemek için yalıtım düzeyini azaltmayı düşünmek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="55b41-151">Depending on your application, you might want to consider lowering the isolation level to avoid high contention in your application.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="55b41-152">Dağıtılmış işlemler içinde yalnızca güncelleştirme, ekleme ve silme işlemlerini gerçekleştirmenizi öneririz, çünkü bunlar önemli veritabanı kaynakları tüketir.</span><span class="sxs-lookup"><span data-stu-id="55b41-152">We recommend that you perform only updates, inserts, and deletes within distributed transactions because they consume significant database resources.</span></span> <span data-ttu-id="55b41-153">Select deyimleri veritabanı kaynaklarını gereksiz şekilde kilitleyebilir ve bazı senaryolarda, seçim için işlemleri kullanmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="55b41-153">Select statements may lock database resources unnecessarily, and in some scenarios, you may have to use transactions for selects.</span></span> <span data-ttu-id="55b41-154">Veritabanı olmayan herhangi bir iş, diğer işlenen kaynak yöneticilerini içermiyorsa, işlem kapsamı dışında yapılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="55b41-154">Any non-database work should be done outside the scope of the transaction, unless it involves other transacted resource managers.</span></span> <span data-ttu-id="55b41-155">İşlemin kapsamındaki bir özel durum işlemin uygulanmasını engelliyorsa, <xref:System.Transactions.TransactionScope> sınıfın, kodunuzun işlem kapsamı dışında yaptığı tüm değişiklikleri geri almak için bir sağlama yoktur.</span><span class="sxs-lookup"><span data-stu-id="55b41-155">Although an exception in the scope of the transaction prevents the transaction from committing, the <xref:System.Transactions.TransactionScope> class has no provision for rolling back any changes your code has made outside the scope of the transaction itself.</span></span> <span data-ttu-id="55b41-156">İşlem geri alındığında biraz işlem yapmanız gerekiyorsa, arabirimin kendi uygulamanızı yazmanız <xref:System.Transactions.IEnlistmentNotification> ve işlem içinde açıkça listelenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="55b41-156">If you have to take some action when the transaction is rolled back, you must write your own implementation of the <xref:System.Transactions.IEnlistmentNotification> interface and explicitly enlist in the transaction.</span></span>  
  
## <a name="example"></a><span data-ttu-id="55b41-157">Örnek</span><span class="sxs-lookup"><span data-stu-id="55b41-157">Example</span></span>  

 <span data-ttu-id="55b41-158">İle çalışma <xref:System.Transactions> , System.Transactions.dll bir başvuruya sahip olmanızı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="55b41-158">Working with <xref:System.Transactions> requires that you have a reference to System.Transactions.dll.</span></span>  
  
 <span data-ttu-id="55b41-159">Aşağıdaki işlev, iki farklı SQL Server örneğine karşı, bir blokta kaydırılan iki farklı nesne ile temsil edilen bir promotable işlemi oluşturmayı gösterir <xref:System.Data.SqlClient.SqlConnection> <xref:System.Transactions.TransactionScope> .</span><span class="sxs-lookup"><span data-stu-id="55b41-159">The following function demonstrates how to create a promotable transaction against two different SQL Server instances, represented by two different <xref:System.Data.SqlClient.SqlConnection> objects, which are wrapped in a <xref:System.Transactions.TransactionScope> block.</span></span> <span data-ttu-id="55b41-160">Kod, <xref:System.Transactions.TransactionScope> bloğu bir `using` ifadesiyle oluşturur ve ' de otomatik olarak listeleyen ilk bağlantıyı açar <xref:System.Transactions.TransactionScope> .</span><span class="sxs-lookup"><span data-stu-id="55b41-160">The code creates the <xref:System.Transactions.TransactionScope> block with a `using` statement and opens the first connection, which automatically enlists it in the <xref:System.Transactions.TransactionScope>.</span></span> <span data-ttu-id="55b41-161">İşlem başlangıçta, tam bir dağıtılmış işlem değil, hafif bir işlem olarak kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="55b41-161">The transaction is initially enlisted as a lightweight transaction, not a full distributed transaction.</span></span> <span data-ttu-id="55b41-162">İkinci bağlantı <xref:System.Transactions.TransactionScope> yalnızca ilk bağlantı içindeki komut bir özel durum oluşturmadığından kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="55b41-162">The second connection is enlisted in the <xref:System.Transactions.TransactionScope> only if the command in the first connection does not throw an exception.</span></span> <span data-ttu-id="55b41-163">İkinci bağlantı açıldığında, işlem otomatik olarak tam dağıtılmış bir işleme yükseltilir.</span><span class="sxs-lookup"><span data-stu-id="55b41-163">When the second connection is opened, the transaction is automatically promoted to a full distributed transaction.</span></span> <span data-ttu-id="55b41-164"><xref:System.Transactions.TransactionScope.Complete%2A>Yöntemi çağrılır, bu işlem yalnızca özel durum atılmadıkça işlemi kaydeder.</span><span class="sxs-lookup"><span data-stu-id="55b41-164">The <xref:System.Transactions.TransactionScope.Complete%2A> method is invoked, which commits the transaction only if no exceptions have been thrown.</span></span> <span data-ttu-id="55b41-165">Bir özel durum, bloktaki herhangi bir noktada oluşturulursa, <xref:System.Transactions.TransactionScope> `Complete` çağrılmaz ve bu, <xref:System.Transactions.TransactionScope> bloğunun sonunda atıldığı zaman dağıtılmış işlem geri alınacaktır `using` .</span><span class="sxs-lookup"><span data-stu-id="55b41-165">If an exception has been thrown at any point in the <xref:System.Transactions.TransactionScope> block, `Complete` will not be called, and the distributed transaction will roll back when the <xref:System.Transactions.TransactionScope> is disposed at the end of its `using` block.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="55b41-166">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="55b41-166">See also</span></span>

- [<span data-ttu-id="55b41-167">İşlemler ve Eşzamanlılık</span><span class="sxs-lookup"><span data-stu-id="55b41-167">Transactions and Concurrency</span></span>](transactions-and-concurrency.md)
- [<span data-ttu-id="55b41-168">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="55b41-168">ADO.NET Overview</span></span>](ado-net-overview.md)
