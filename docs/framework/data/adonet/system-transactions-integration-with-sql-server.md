---
title: SQL Server ile System.Transactions tümleştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b555544e-7abb-4814-859b-ab9cdd7d8716
ms.openlocfilehash: 219a806441e0f6ce501dc691f4c965168a250aeb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33365754"
---
# <a name="systemtransactions-integration-with-sql-server"></a><span data-ttu-id="55328-102">SQL Server ile System.Transactions tümleştirme</span><span class="sxs-lookup"><span data-stu-id="55328-102">System.Transactions Integration with SQL Server</span></span>
<span data-ttu-id="55328-103">[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Üzerinden erişilen bir işlem framework sürüm 2.0 sunulan <xref:System.Transactions> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="55328-103">The [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] version 2.0 introduced a transaction framework that can be accessed through the <xref:System.Transactions> namespace.</span></span> <span data-ttu-id="55328-104">Bu çerçeve işlemleri içinde tam olarak tümleşik bir şekilde kullanıma sunan [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]gibi [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)].</span><span class="sxs-lookup"><span data-stu-id="55328-104">This framework exposes transactions in a way that is fully integrated in the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], including [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)].</span></span>  
  
 <span data-ttu-id="55328-105">Programlanabilirlik geliştirmeleri yanı sıra <xref:System.Transactions> ve [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] işlemleri ile çalışırken en iyi duruma getirme koordine etmek için birlikte çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="55328-105">In addition to the programmability enhancements, <xref:System.Transactions> and [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] can work together to coordinate optimizations when you work with transactions.</span></span> <span data-ttu-id="55328-106">Otomatik olarak bir tam olarak dağıtılmış işlem gerektiği düzenli olarak yükseltilebilmesi için basit bir (yerel) işlem buna yükseltilebilir bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="55328-106">A promotable transaction is a lightweight (local) transaction that can be automatically promoted to a fully distributed transaction on an as-needed basis.</span></span>  
  
 <span data-ttu-id="55328-107">İle başlayarak [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] 2.0 <xref:System.Data.SqlClient> SQL Server ile çalışırken yükseltilebilir işlemleri destekler.</span><span class="sxs-lookup"><span data-stu-id="55328-107">Starting with [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] 2.0, <xref:System.Data.SqlClient> supports promotable transactions when you work with SQL Server.</span></span> <span data-ttu-id="55328-108">Yükseltilebilir işlem eklenen çağrılmaz işlemlerinin ek yükü dağıtılmış işlem eklenen ek yükü gerekli olmadığı sürece.</span><span class="sxs-lookup"><span data-stu-id="55328-108">A promotable transaction does not invoke the added overhead of a distributed transaction unless the added overhead is required.</span></span> <span data-ttu-id="55328-109">Yükseltilebilir işlemleri otomatik olarak yapılır ve geliştiriciden müdahalesi gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="55328-109">Promotable transactions are automatic and require no intervention from the developer.</span></span>  
  
 <span data-ttu-id="55328-110">Yükseltilebilir işlemleri yalnızca kullanılabilir kullandığınızda [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] için SQL Server veri sağlayıcısı (`SqlClient`) SQL Server ile.</span><span class="sxs-lookup"><span data-stu-id="55328-110">Promotable transactions are only available when you use the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider for SQL Server (`SqlClient`) with SQL Server.</span></span>  
  
## <a name="creating-promotable-transactions"></a><span data-ttu-id="55328-111">Yükseltilebilir işlemler oluşturma</span><span class="sxs-lookup"><span data-stu-id="55328-111">Creating Promotable Transactions</span></span>  
 <span data-ttu-id="55328-112">[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] SQL Server için sağlayıcısı sınıfları aracılığıyla işlenmesini yükseltilebilir işlemler için destek sağlar [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] <xref:System.Transactions> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="55328-112">The [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Provider for SQL Server provides support for promotable transactions, which are handled through the classes in the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] <xref:System.Transactions> namespace.</span></span> <span data-ttu-id="55328-113">Yükseltilebilir işlemleri gerektiğinde kadar bir dağıtılmış işlem oluşturma ertelemeyi dağıtılmış işlemler en iyi duruma getirme.</span><span class="sxs-lookup"><span data-stu-id="55328-113">Promotable transactions optimize distributed transactions by deferring creating a distributed transaction until it is needed.</span></span> <span data-ttu-id="55328-114">Yalnızca bir Kaynak Yöneticisi'ni gereklidir, dağıtılmış bir işlem oluşur.</span><span class="sxs-lookup"><span data-stu-id="55328-114">If only one resource manager is required, no distributed transaction occurs.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="55328-115">Kısmen güvenilen bir senaryoda <xref:System.Transactions.DistributedTransactionPermission> dağıtılmış işlem için bir işlem yükseltildiğinde gereklidir.</span><span class="sxs-lookup"><span data-stu-id="55328-115">In a partially trusted scenario, the <xref:System.Transactions.DistributedTransactionPermission> is required when a transaction is promoted to a distributed transaction.</span></span>  
  
## <a name="promotable-transaction-scenarios"></a><span data-ttu-id="55328-116">Yükseltilebilir işlem senaryoları</span><span class="sxs-lookup"><span data-stu-id="55328-116">Promotable Transaction Scenarios</span></span>  
 <span data-ttu-id="55328-117">Dağıtılmış işlemler genellikle Microsoft Dağıtılmış işlem, işlem sırasında erişilen tüm kaynak yöneticileri tümleştirir Düzenleyicisi (MS DTC) tarafından yönetilen önemli sistem kaynaklarını tüketebilir.</span><span class="sxs-lookup"><span data-stu-id="55328-117">Distributed transactions typically consume significant system resources, being managed by Microsoft Distributed Transaction Coordinator (MS DTC), which integrates all the resource managers accessed in the transaction.</span></span> <span data-ttu-id="55328-118">Yükseltilebilir bir işlem özel bir biçimidir bir <xref:System.Transactions> etkili bir şekilde basit bir SQL Server işlem çalışmaya temsilciler işlem.</span><span class="sxs-lookup"><span data-stu-id="55328-118">A promotable transaction is a special form of a <xref:System.Transactions> transaction that effectively delegates the work to a simple SQL Server transaction.</span></span> <span data-ttu-id="55328-119"><xref:System.Transactions>, <xref:System.Data.SqlClient>, ve SQL Server, tam bir dağıtılmış işlem için gerektiği şekilde yükseltme işlem işlenmesiyle ilgili iş koordine etmek.</span><span class="sxs-lookup"><span data-stu-id="55328-119"><xref:System.Transactions>, <xref:System.Data.SqlClient>, and SQL Server coordinate the work involved in handling the transaction, promoting it to a full distributed transaction as needed.</span></span>  
  
 <span data-ttu-id="55328-120">Bağlantı etkin bir kullanarak yükseltilebilir işlemleri kullanmanın faydası, açıldığında <xref:System.Transactions.TransactionScope> işlem ve başka bir bağlantı açıldığında, ek yansıtılmasını yerine basit bir işlem olarak işlem yürütme tam bir dağıtılmış işlem yükü.</span><span class="sxs-lookup"><span data-stu-id="55328-120">The benefit of using promotable transactions is that when a connection is opened by using an active <xref:System.Transactions.TransactionScope> transaction, and no other connections are opened, the transaction commits as a lightweight transaction, instead of incurring the additional overhead of a full distributed transaction.</span></span>  
  
### <a name="connection-string-keywords"></a><span data-ttu-id="55328-121">Bağlantı dizesi anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="55328-121">Connection String Keywords</span></span>  
 <span data-ttu-id="55328-122"><xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> Özelliğini destekleyen bir anahtar sözcük `Enlist`, belirten olup olmadığını <xref:System.Data.SqlClient> işlem bağlamları algılar ve otomatik olarak bir dağıtılmış işlemde bağlantıyı kaydolunamadı.</span><span class="sxs-lookup"><span data-stu-id="55328-122">The <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> property supports a keyword, `Enlist`, which indicates whether <xref:System.Data.SqlClient> will detect transactional contexts and automatically enlist the connection in a distributed transaction.</span></span> <span data-ttu-id="55328-123">Varsa `Enlist=true`, bağlantı otomatik olarak açılırken iş parçacığının geçerli işlem bağlamda kayıtlıdır.</span><span class="sxs-lookup"><span data-stu-id="55328-123">If `Enlist=true`, the connection is automatically enlisted in the opening thread's current transaction context.</span></span> <span data-ttu-id="55328-124">Varsa `Enlist=false`, `SqlClient` bağlantı dağıtılmış bir işlem ile etkileşim değil.</span><span class="sxs-lookup"><span data-stu-id="55328-124">If `Enlist=false`, the `SqlClient` connection does not interact with a distributed transaction.</span></span> <span data-ttu-id="55328-125">İçin varsayılan değer `Enlist` doğrudur.</span><span class="sxs-lookup"><span data-stu-id="55328-125">The default value for `Enlist` is true.</span></span> <span data-ttu-id="55328-126">Varsa `Enlist` belirtilmezse bağlantı dizesinde bağlantı açıldığında bir algılanırsa, bağlantı bir dağıtılmış işlemde otomatik olarak kayıtlı.</span><span class="sxs-lookup"><span data-stu-id="55328-126">If `Enlist` is not specified in the connection string, the connection is automatically enlisted in a distributed transaction if one is detected when the connection is opened.</span></span>  
  
 <span data-ttu-id="55328-127">`Transaction Binding` Anahtar bir <xref:System.Data.SqlClient.SqlConnection> bağlantı dizesini kontrol bir kayıtlı olan bağlantının ilişkilendirmesini `System.Transactions` işlem.</span><span class="sxs-lookup"><span data-stu-id="55328-127">The `Transaction Binding` keywords in a <xref:System.Data.SqlClient.SqlConnection> connection string control the connection's association with an enlisted `System.Transactions` transaction.</span></span> <span data-ttu-id="55328-128">Ayrıca aracılığıyla kullanılabilir <xref:System.Data.SqlClient.SqlConnectionStringBuilder.TransactionBinding%2A> özelliği bir <xref:System.Data.SqlClient.SqlConnectionStringBuilder>.</span><span class="sxs-lookup"><span data-stu-id="55328-128">It is also available through the <xref:System.Data.SqlClient.SqlConnectionStringBuilder.TransactionBinding%2A> property of a <xref:System.Data.SqlClient.SqlConnectionStringBuilder>.</span></span>  
  
 <span data-ttu-id="55328-129">Aşağıdaki tabloda olası değerleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="55328-129">The following table describes the possible values.</span></span>  
  
|<span data-ttu-id="55328-130">Anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="55328-130">Keyword</span></span>|<span data-ttu-id="55328-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="55328-131">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="55328-132">Örtük bağlantı kesme</span><span class="sxs-lookup"><span data-stu-id="55328-132">Implicit Unbind</span></span>|<span data-ttu-id="55328-133">Varsayılan.</span><span class="sxs-lookup"><span data-stu-id="55328-133">The default.</span></span> <span data-ttu-id="55328-134">Otomatik kayıt işlemleri moduna geçiriliyor sona erdiğinde bağlantıyı işleminden ayırır.</span><span class="sxs-lookup"><span data-stu-id="55328-134">The connection detaches from the transaction when it ends, switching back to autocommit mode.</span></span>|  
|<span data-ttu-id="55328-135">Açık bağlantı kesme</span><span class="sxs-lookup"><span data-stu-id="55328-135">Explicit Unbind</span></span>|<span data-ttu-id="55328-136">İşlem kapatılana kadar bağlantı harekete eklenen kalır.</span><span class="sxs-lookup"><span data-stu-id="55328-136">The connection remains attached to the transaction until the transaction is closed.</span></span> <span data-ttu-id="55328-137">İlişkili işlem etkin değil veya eşleşmiyor bağlantı başarısız olur <xref:System.Transactions.Transaction.Current%2A>.</span><span class="sxs-lookup"><span data-stu-id="55328-137">The connection will fail if the associated transaction is not active or does not match <xref:System.Transactions.Transaction.Current%2A>.</span></span>|  
  
## <a name="using-transactionscope"></a><span data-ttu-id="55328-138">TransactionScope kullanma</span><span class="sxs-lookup"><span data-stu-id="55328-138">Using TransactionScope</span></span>  
 <span data-ttu-id="55328-139"><xref:System.Transactions.TransactionScope> Sınıfı yapacağı kod bloğu işlem örtük olarak bir dağıtılmış işlemde bağlantıları kaydetme tarafından.</span><span class="sxs-lookup"><span data-stu-id="55328-139">The <xref:System.Transactions.TransactionScope> class makes a code block transactional by implicitly enlisting connections in a distributed transaction.</span></span> <span data-ttu-id="55328-140">Çağırmalısınız <xref:System.Transactions.TransactionScope.Complete%2A> sonunda yöntemi <xref:System.Transactions.TransactionScope> , çıkmadan önce bloğu.</span><span class="sxs-lookup"><span data-stu-id="55328-140">You must call the <xref:System.Transactions.TransactionScope.Complete%2A> method at the end of the <xref:System.Transactions.TransactionScope> block before leaving it.</span></span> <span data-ttu-id="55328-141">Blok bırakarak çağırır <xref:System.Transactions.TransactionScope.Dispose%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="55328-141">Leaving the block invokes the <xref:System.Transactions.TransactionScope.Dispose%2A> method.</span></span> <span data-ttu-id="55328-142">Kod kapsamı, işlem bırakın kabul neden iptal edildiğini bir özel durum oluşturuldu</span><span class="sxs-lookup"><span data-stu-id="55328-142">If an exception has been thrown that causes the code to leave scope, the transaction is considered aborted.</span></span>  
  
 <span data-ttu-id="55328-143">Kullanmanızı öneririz bir `using` emin olmak için blok <xref:System.Transactions.TransactionScope.Dispose%2A> üzerinde adlı <xref:System.Transactions.TransactionScope> nesnesi kullanarak ne zaman engelleme çıkıldı.</span><span class="sxs-lookup"><span data-stu-id="55328-143">We recommend that you use a `using` block to make sure that <xref:System.Transactions.TransactionScope.Dispose%2A> is called on the <xref:System.Transactions.TransactionScope> object when the using block is exited.</span></span> <span data-ttu-id="55328-144">Yürütme veya geri işlemler için hata önemli ölçüde zarar performans çünkü için varsayılan zaman aşımı <xref:System.Transactions.TransactionScope> bir dakikadır.</span><span class="sxs-lookup"><span data-stu-id="55328-144">Failure to commit or roll back pending transactions can significantly damage performance because the default time-out for the <xref:System.Transactions.TransactionScope> is one minute.</span></span> <span data-ttu-id="55328-145">Kullanmıyorsanız, bir `using` deyimi, tüm iş gerçekleştirmelisiniz bir `Try` engellemek ve açıkça çağırın <xref:System.Transactions.TransactionScope.Dispose%2A> yönteminde `Finally` bloğu.</span><span class="sxs-lookup"><span data-stu-id="55328-145">If you do not use a `using` statement, you must perform all work in a `Try` block and explicitly call the <xref:System.Transactions.TransactionScope.Dispose%2A> method in the `Finally` block.</span></span>  
  
 <span data-ttu-id="55328-146">Bir özel durum oluşması halinde <xref:System.Transactions.TransactionScope>, işlem tutarsız olarak işaretlenir ve terk edilir.</span><span class="sxs-lookup"><span data-stu-id="55328-146">If an exception occurs in the <xref:System.Transactions.TransactionScope>, the transaction is marked as inconsistent and is abandoned.</span></span> <span data-ttu-id="55328-147">Bunu alınacak ne zaman geri <xref:System.Transactions.TransactionScope> atıldı.</span><span class="sxs-lookup"><span data-stu-id="55328-147">It will be rolled back when the <xref:System.Transactions.TransactionScope> is disposed.</span></span> <span data-ttu-id="55328-148">Hiçbir özel durum oluşursa, katılımcı işlemler uygulayın.</span><span class="sxs-lookup"><span data-stu-id="55328-148">If no exception occurs, participating transactions commit.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="55328-149">`TransactionScope` Sınıfı oluşturur bir işlemle bir <xref:System.Transactions.Transaction.IsolationLevel%2A> , `Serializable` varsayılan olarak.</span><span class="sxs-lookup"><span data-stu-id="55328-149">The `TransactionScope` class creates a transaction with a <xref:System.Transactions.Transaction.IsolationLevel%2A> of `Serializable` by default.</span></span> <span data-ttu-id="55328-150">Uygulamanızın bağlı olarak, uygulamanızda yüksek çekişmesinden kaçınmak için yalıtım düzeyini düşünmek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="55328-150">Depending on your application, you might want to consider lowering the isolation level to avoid high contention in your application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="55328-151">Yalnızca güncelleştirmeleri ekler, gerçekleştirme ve önemli veritabanı kaynaklarını tükettiği için siler içinde dağıtılmış işlemler öneririz.</span><span class="sxs-lookup"><span data-stu-id="55328-151">We recommend that you perform only updates, inserts, and deletes within distributed transactions because they consume significant database resources.</span></span> <span data-ttu-id="55328-152">SELECT deyimi veritabanı kaynakları gereksiz yere Kilitle ve bazı senaryolarda, işlemler için seçer kullanmak zorunda kalabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="55328-152">Select statements may lock database resources unnecessarily, and in some scenarios, you may have to use transactions for selects.</span></span> <span data-ttu-id="55328-153">Diğer işlem temelli kaynak yöneticileri içerir sürece herhangi bir veritabanı olmayan iş hareket kapsamı dışında yapılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="55328-153">Any non-database work should be done outside the scope of the transaction, unless it involves other transacted resource managers.</span></span> <span data-ttu-id="55328-154">Kapsamdaki istisna hareketin gerçekleştirmeden, gelen işlem engeller rağmen <xref:System.Transactions.TransactionScope> sınıfı işlem kapsamı dışında herhangi bir değişiklik kodunuzun geri yaptı için hiçbir sağlama sahiptir.</span><span class="sxs-lookup"><span data-stu-id="55328-154">Although an exception in the scope of the transaction prevents the transaction from committing, the <xref:System.Transactions.TransactionScope> class has no provision for rolling back any changes your code has made outside the scope of the transaction itself.</span></span> <span data-ttu-id="55328-155">İşlem geri alındı, bazı işlemler yapması varsa, kendi uygulamanızı yazma <xref:System.Transactions.IEnlistmentNotification> arabirim ve açıkça işleminde listelenmeyi.</span><span class="sxs-lookup"><span data-stu-id="55328-155">If you have to take some action when the transaction is rolled back, you must write your own implementation of the <xref:System.Transactions.IEnlistmentNotification> interface and explicitly enlist in the transaction.</span></span>  
  
## <a name="example"></a><span data-ttu-id="55328-156">Örnek</span><span class="sxs-lookup"><span data-stu-id="55328-156">Example</span></span>  
 <span data-ttu-id="55328-157">İle çalışma <xref:System.Transactions> System.Transactions.dll başvuru sahip olmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="55328-157">Working with <xref:System.Transactions> requires that you have a reference to System.Transactions.dll.</span></span>  
  
 <span data-ttu-id="55328-158">Aşağıdaki işlevi nasıl iki tarafından temsil edilen, iki farklı SQL Server örnekleri karşı yükseltilebilir işlem farklı oluşturulduğunu gösteren <xref:System.Data.SqlClient.SqlConnection> kaydırılır nesneleri bir <xref:System.Transactions.TransactionScope> bloğu.</span><span class="sxs-lookup"><span data-stu-id="55328-158">The following function demonstrates how to create a promotable transaction against two different SQL Server instances, represented by two different <xref:System.Data.SqlClient.SqlConnection> objects, which are wrapped in a <xref:System.Transactions.TransactionScope> block.</span></span> <span data-ttu-id="55328-159">Kod oluşturur <xref:System.Transactions.TransactionScope> ile engelleme bir `using` deyimi ve otomatik olarak içinde kaydeder ilk bağlantı açar <xref:System.Transactions.TransactionScope>.</span><span class="sxs-lookup"><span data-stu-id="55328-159">The code creates the <xref:System.Transactions.TransactionScope> block with a `using` statement and opens the first connection, which automatically enlists it in the <xref:System.Transactions.TransactionScope>.</span></span> <span data-ttu-id="55328-160">İşlem, başlangıçta, tam bir dağıtılmış işlem yok gibi basit bir işlem olarak kayıtlıdır.</span><span class="sxs-lookup"><span data-stu-id="55328-160">The transaction is initially enlisted as a lightweight transaction, not a full distributed transaction.</span></span> <span data-ttu-id="55328-161">İkinci bir bağlantı olarak kayıtlıdır <xref:System.Transactions.TransactionScope> varsa yalnızca ilk bağlantı komutta bir özel durum oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="55328-161">The second connection is enlisted in the <xref:System.Transactions.TransactionScope> only if the command in the first connection does not throw an exception.</span></span> <span data-ttu-id="55328-162">İkinci bir bağlantı açıldığında, işlem için tam bir dağıtılmış işlem otomatik olarak yükseltilir.</span><span class="sxs-lookup"><span data-stu-id="55328-162">When the second connection is opened, the transaction is automatically promoted to a full distributed transaction.</span></span> <span data-ttu-id="55328-163"><xref:System.Transactions.TransactionScope.Complete%2A> Yöntemi çağrıldığında, yalnızca hiçbir özel durum, hangi hareketi tamamlar.</span><span class="sxs-lookup"><span data-stu-id="55328-163">The <xref:System.Transactions.TransactionScope.Complete%2A> method is invoked, which commits the transaction only if no exceptions have been thrown.</span></span> <span data-ttu-id="55328-164">İçinde herhangi bir noktada bir özel durum oluşturuldu, <xref:System.Transactions.TransactionScope> bloğu `Complete` değil çağrılması olacaktır ve alma dağıtılmış işlem ne zaman geri <xref:System.Transactions.TransactionScope> sonunda atıldı kendi `using` bloğu.</span><span class="sxs-lookup"><span data-stu-id="55328-164">If an exception has been thrown at any point in the <xref:System.Transactions.TransactionScope> block, `Complete` will not be called, and the distributed transaction will roll back when the <xref:System.Transactions.TransactionScope> is disposed at the end of its `using` block.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="55328-165">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="55328-165">See Also</span></span>  
 [<span data-ttu-id="55328-166">İşlemler ve Eşzamanlılık</span><span class="sxs-lookup"><span data-stu-id="55328-166">Transactions and Concurrency</span></span>](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)  
 [<span data-ttu-id="55328-167">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="55328-167">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
