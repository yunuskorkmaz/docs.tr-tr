---
title: SQL Server ile System.Transactions Tümleştirmesi
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b555544e-7abb-4814-859b-ab9cdd7d8716
ms.openlocfilehash: 4ff415adf57bf72cb4da6d405f652a4a50c19041
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62033377"
---
# <a name="systemtransactions-integration-with-sql-server"></a><span data-ttu-id="c435c-102">SQL Server ile System.Transactions Tümleştirmesi</span><span class="sxs-lookup"><span data-stu-id="c435c-102">System.Transactions Integration with SQL Server</span></span>
<span data-ttu-id="c435c-103">[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Sürüm 2.0 kullanılmaya aracılığıyla erişilebilen bir işlem framework <xref:System.Transactions> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="c435c-103">The [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] version 2.0 introduced a transaction framework that can be accessed through the <xref:System.Transactions> namespace.</span></span> <span data-ttu-id="c435c-104">Bu çerçeve işlemleri, tamamen tümleşik bir şekilde kullanıma sunan [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]de dahil olmak üzere [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c435c-104">This framework exposes transactions in a way that is fully integrated in the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], including [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)].</span></span>  
  
 <span data-ttu-id="c435c-105">Programlanabilirlik geliştirmeleri yanı sıra <xref:System.Transactions> ve [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] işlemleri ile çalışırken en iyi duruma getirme koordine etmek için birlikte çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="c435c-105">In addition to the programmability enhancements, <xref:System.Transactions> and [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] can work together to coordinate optimizations when you work with transactions.</span></span> <span data-ttu-id="c435c-106">Otomatik olarak tam olarak dağıtılmış bir işlem gerekli olarak yükseltilebilir basit bir (yerel) işlem bir promotable işlemdir.</span><span class="sxs-lookup"><span data-stu-id="c435c-106">A promotable transaction is a lightweight (local) transaction that can be automatically promoted to a fully distributed transaction on an as-needed basis.</span></span>  
  
 <span data-ttu-id="c435c-107">İle başlayarak [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] 2.0 <xref:System.Data.SqlClient> SQL Server ile çalışırken promotable işlemleri destekler.</span><span class="sxs-lookup"><span data-stu-id="c435c-107">Starting with [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] 2.0, <xref:System.Data.SqlClient> supports promotable transactions when you work with SQL Server.</span></span> <span data-ttu-id="c435c-108">Bir promotable işlem eklenen çağırmadığı işlemlerinin ek yükü dağıtılmış işlem ek yükü gerekli olmadığı sürece.</span><span class="sxs-lookup"><span data-stu-id="c435c-108">A promotable transaction does not invoke the added overhead of a distributed transaction unless the added overhead is required.</span></span> <span data-ttu-id="c435c-109">Promotable işlemleri otomatik olarak yapılır ve geliştiriciden herhangi bir müdahalesi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="c435c-109">Promotable transactions are automatic and require no intervention from the developer.</span></span>  
  
 <span data-ttu-id="c435c-110">Promotable işlemleri bulunan ve yalnızca kullandığınız zaman [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] SQL Server için veri sağlayıcısı (`SqlClient`) SQL Server ile.</span><span class="sxs-lookup"><span data-stu-id="c435c-110">Promotable transactions are only available when you use the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider for SQL Server (`SqlClient`) with SQL Server.</span></span>  
  
## <a name="creating-promotable-transactions"></a><span data-ttu-id="c435c-111">Promotable işlemleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="c435c-111">Creating Promotable Transactions</span></span>  
 <span data-ttu-id="c435c-112">[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] SQL Server için sağlayıcısı sınıfları aracılığıyla işlenir promotable işlemler için destek sağlar [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] <xref:System.Transactions> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="c435c-112">The [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Provider for SQL Server provides support for promotable transactions, which are handled through the classes in the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] <xref:System.Transactions> namespace.</span></span> <span data-ttu-id="c435c-113">Promotable işlemleri, gerekli olana kadar bir dağıtılmış işlem oluşturma erteleyerek dağıtılmış işlemler iyileştirin.</span><span class="sxs-lookup"><span data-stu-id="c435c-113">Promotable transactions optimize distributed transactions by deferring creating a distributed transaction until it is needed.</span></span> <span data-ttu-id="c435c-114">Yalnızca biri resource manager gerekliyse, hiçbir dağıtılmış işlem gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="c435c-114">If only one resource manager is required, no distributed transaction occurs.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c435c-115">Kısmen güvenilen bir senaryoda <xref:System.Transactions.DistributedTransactionPermission> dağıtılmış bir işlem için bir işlem yükseltildiğinde gereklidir.</span><span class="sxs-lookup"><span data-stu-id="c435c-115">In a partially trusted scenario, the <xref:System.Transactions.DistributedTransactionPermission> is required when a transaction is promoted to a distributed transaction.</span></span>  
  
## <a name="promotable-transaction-scenarios"></a><span data-ttu-id="c435c-116">Promotable işlem senaryoları</span><span class="sxs-lookup"><span data-stu-id="c435c-116">Promotable Transaction Scenarios</span></span>  
 <span data-ttu-id="c435c-117">Dağıtılmış işlemler genellikle Microsoft Dağıtılmış işlem işlemde erişilen tüm kaynak yöneticileri tümleşen Düzenleyicisi (MS DTC) tarafından yönetilen önemli sistem kaynaklarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="c435c-117">Distributed transactions typically consume significant system resources, being managed by Microsoft Distributed Transaction Coordinator (MS DTC), which integrates all the resource managers accessed in the transaction.</span></span> <span data-ttu-id="c435c-118">Özel bir promotable harekettir bir <xref:System.Transactions> etkili bir şekilde basit bir SQL Server işlem işi temsilciler işlem.</span><span class="sxs-lookup"><span data-stu-id="c435c-118">A promotable transaction is a special form of a <xref:System.Transactions> transaction that effectively delegates the work to a simple SQL Server transaction.</span></span> <span data-ttu-id="c435c-119"><xref:System.Transactions>, <xref:System.Data.SqlClient>, ve SQL Server, tam bir dağıtılmış işlem için gereken şekilde yükseltmek işlem işlenmesiyle ilgili iş koordine etmek.</span><span class="sxs-lookup"><span data-stu-id="c435c-119"><xref:System.Transactions>, <xref:System.Data.SqlClient>, and SQL Server coordinate the work involved in handling the transaction, promoting it to a full distributed transaction as needed.</span></span>  
  
 <span data-ttu-id="c435c-120">Bir bağlantı etkin bir kullanarak promotable işlemleri kullanmanın avantajı, açıldığında <xref:System.Transactions.TransactionScope> işlem ve başka bir bağlantı açıldığında, ek sunucular yerine basit bir işlem olarak işlem yürütmeleri tam bir dağıtılmış işlem ek yükü.</span><span class="sxs-lookup"><span data-stu-id="c435c-120">The benefit of using promotable transactions is that when a connection is opened by using an active <xref:System.Transactions.TransactionScope> transaction, and no other connections are opened, the transaction commits as a lightweight transaction, instead of incurring the additional overhead of a full distributed transaction.</span></span>  
  
### <a name="connection-string-keywords"></a><span data-ttu-id="c435c-121">Bağlantı dizesi anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="c435c-121">Connection String Keywords</span></span>  
 <span data-ttu-id="c435c-122"><xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> Özelliğini destekleyen bir anahtar sözcük `Enlist`, gösteren olmadığını <xref:System.Data.SqlClient> işlem bağlamları algılar ve bir dağıtılmış işlem bağlantı otomatik olarak listeleme.</span><span class="sxs-lookup"><span data-stu-id="c435c-122">The <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> property supports a keyword, `Enlist`, which indicates whether <xref:System.Data.SqlClient> will detect transactional contexts and automatically enlist the connection in a distributed transaction.</span></span> <span data-ttu-id="c435c-123">Varsa `Enlist=true`, bağlantı otomatik olarak açılırken iş parçacığının geçerli işlem bağlamında kayıtlıdır.</span><span class="sxs-lookup"><span data-stu-id="c435c-123">If `Enlist=true`, the connection is automatically enlisted in the opening thread's current transaction context.</span></span> <span data-ttu-id="c435c-124">Varsa `Enlist=false`, `SqlClient` bağlantı ile dağıtılmış bir işlem etkileşimli değil.</span><span class="sxs-lookup"><span data-stu-id="c435c-124">If `Enlist=false`, the `SqlClient` connection does not interact with a distributed transaction.</span></span> <span data-ttu-id="c435c-125">İçin varsayılan değer `Enlist` geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="c435c-125">The default value for `Enlist` is true.</span></span> <span data-ttu-id="c435c-126">Varsa `Enlist` belirtilmezse bağlantı dizesinde bağlantıyı açıldığında bir algılanırsa bağlantı dağıtılmış bir işlem içinde otomatik olarak kayıtlı.</span><span class="sxs-lookup"><span data-stu-id="c435c-126">If `Enlist` is not specified in the connection string, the connection is automatically enlisted in a distributed transaction if one is detected when the connection is opened.</span></span>  
  
 <span data-ttu-id="c435c-127">`Transaction Binding` Anahtar bir <xref:System.Data.SqlClient.SqlConnection> bağlantı dizesini kontrol kayıtlı bir bağlantının ilişkilendirmesini `System.Transactions` işlem.</span><span class="sxs-lookup"><span data-stu-id="c435c-127">The `Transaction Binding` keywords in a <xref:System.Data.SqlClient.SqlConnection> connection string control the connection's association with an enlisted `System.Transactions` transaction.</span></span> <span data-ttu-id="c435c-128">Ayrıca aracılığıyla <xref:System.Data.SqlClient.SqlConnectionStringBuilder.TransactionBinding%2A> özelliği bir <xref:System.Data.SqlClient.SqlConnectionStringBuilder>.</span><span class="sxs-lookup"><span data-stu-id="c435c-128">It is also available through the <xref:System.Data.SqlClient.SqlConnectionStringBuilder.TransactionBinding%2A> property of a <xref:System.Data.SqlClient.SqlConnectionStringBuilder>.</span></span>  
  
 <span data-ttu-id="c435c-129">Olası değerler aşağıdaki tabloda açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c435c-129">The following table describes the possible values.</span></span>  
  
|<span data-ttu-id="c435c-130">Anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="c435c-130">Keyword</span></span>|<span data-ttu-id="c435c-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c435c-131">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c435c-132">Örtük Unbind</span><span class="sxs-lookup"><span data-stu-id="c435c-132">Implicit Unbind</span></span>|<span data-ttu-id="c435c-133">Varsayılan.</span><span class="sxs-lookup"><span data-stu-id="c435c-133">The default.</span></span> <span data-ttu-id="c435c-134">Commıtted moduna geçiş sona erdiğinde bağlantıyı bir işlemden ayırır.</span><span class="sxs-lookup"><span data-stu-id="c435c-134">The connection detaches from the transaction when it ends, switching back to autocommit mode.</span></span>|  
|<span data-ttu-id="c435c-135">Açık Unbind</span><span class="sxs-lookup"><span data-stu-id="c435c-135">Explicit Unbind</span></span>|<span data-ttu-id="c435c-136">İşlem kapatılana kadar bağlantı harekete iliştirilmiş olarak kalır.</span><span class="sxs-lookup"><span data-stu-id="c435c-136">The connection remains attached to the transaction until the transaction is closed.</span></span> <span data-ttu-id="c435c-137">Bağlantı başarısız olur, ilişkili işlem etkin değil ya da eşleşmiyor <xref:System.Transactions.Transaction.Current%2A>.</span><span class="sxs-lookup"><span data-stu-id="c435c-137">The connection will fail if the associated transaction is not active or does not match <xref:System.Transactions.Transaction.Current%2A>.</span></span>|  
  
## <a name="using-transactionscope"></a><span data-ttu-id="c435c-138">TransactionScope kullanma</span><span class="sxs-lookup"><span data-stu-id="c435c-138">Using TransactionScope</span></span>  
 <span data-ttu-id="c435c-139"><xref:System.Transactions.TransactionScope> Sınıfı yapacağı bir kod bloğu işlem bir dağıtılmış işlemde bağlantı kaydetme tarafından örtük olarak.</span><span class="sxs-lookup"><span data-stu-id="c435c-139">The <xref:System.Transactions.TransactionScope> class makes a code block transactional by implicitly enlisting connections in a distributed transaction.</span></span> <span data-ttu-id="c435c-140">Çağırmalısınız <xref:System.Transactions.TransactionScope.Complete%2A> yöntemi sonunda <xref:System.Transactions.TransactionScope> , çıkmadan önce blok.</span><span class="sxs-lookup"><span data-stu-id="c435c-140">You must call the <xref:System.Transactions.TransactionScope.Complete%2A> method at the end of the <xref:System.Transactions.TransactionScope> block before leaving it.</span></span> <span data-ttu-id="c435c-141">Blok bırakarak çağırır <xref:System.Transactions.TransactionScope.Dispose%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="c435c-141">Leaving the block invokes the <xref:System.Transactions.TransactionScope.Dispose%2A> method.</span></span> <span data-ttu-id="c435c-142">Kod kapsamı, işlem bırakmak kabul neden iptal edildiğini bir özel durumun durumunda.</span><span class="sxs-lookup"><span data-stu-id="c435c-142">If an exception has been thrown that causes the code to leave scope, the transaction is considered aborted.</span></span>  
  
 <span data-ttu-id="c435c-143">Kullanmanızı öneririz bir `using` emin olmak için blok <xref:System.Transactions.TransactionScope.Dispose%2A> üzerinde çağrılır <xref:System.Transactions.TransactionScope> nesnesini kullanarak engelliyken çıkıldı.</span><span class="sxs-lookup"><span data-stu-id="c435c-143">We recommend that you use a `using` block to make sure that <xref:System.Transactions.TransactionScope.Dispose%2A> is called on the <xref:System.Transactions.TransactionScope> object when the using block is exited.</span></span> <span data-ttu-id="c435c-144">Hata işleme veya işlemleri geri önemli ölçüde zarar performans çünkü için varsayılan zaman aşımı <xref:System.Transactions.TransactionScope> bir dakikadır.</span><span class="sxs-lookup"><span data-stu-id="c435c-144">Failure to commit or roll back pending transactions can significantly damage performance because the default time-out for the <xref:System.Transactions.TransactionScope> is one minute.</span></span> <span data-ttu-id="c435c-145">Kullanmıyorsanız, bir `using` deyimi, tüm iş gerçekleştirmelisiniz bir `Try` engelleme ve açıkça çağırmak <xref:System.Transactions.TransactionScope.Dispose%2A> yönteminde `Finally` blok.</span><span class="sxs-lookup"><span data-stu-id="c435c-145">If you do not use a `using` statement, you must perform all work in a `Try` block and explicitly call the <xref:System.Transactions.TransactionScope.Dispose%2A> method in the `Finally` block.</span></span>  
  
 <span data-ttu-id="c435c-146">Bir özel durum oluşursa <xref:System.Transactions.TransactionScope>, işlem tutarsız olarak işaretlenir ve terk edilir.</span><span class="sxs-lookup"><span data-stu-id="c435c-146">If an exception occurs in the <xref:System.Transactions.TransactionScope>, the transaction is marked as inconsistent and is abandoned.</span></span> <span data-ttu-id="c435c-147">Kullanıma sunulacak geri <xref:System.Transactions.TransactionScope> atıldı.</span><span class="sxs-lookup"><span data-stu-id="c435c-147">It will be rolled back when the <xref:System.Transactions.TransactionScope> is disposed.</span></span> <span data-ttu-id="c435c-148">Hiçbir özel durum oluşursa, katılımcı işlemleri işleyin.</span><span class="sxs-lookup"><span data-stu-id="c435c-148">If no exception occurs, participating transactions commit.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c435c-149">`TransactionScope` Sınıfı ile bir işlem oluşturur bir <xref:System.Transactions.Transaction.IsolationLevel%2A> , `Serializable` varsayılan olarak.</span><span class="sxs-lookup"><span data-stu-id="c435c-149">The `TransactionScope` class creates a transaction with a <xref:System.Transactions.Transaction.IsolationLevel%2A> of `Serializable` by default.</span></span> <span data-ttu-id="c435c-150">Uygulamanızın bağlı olarak, uygulamanızda yüksek çekişmesinden kaçınmak için yalıtım düzeyini düşünmek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c435c-150">Depending on your application, you might want to consider lowering the isolation level to avoid high contention in your application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c435c-151">Yalnızca güncelleştirmeleri ekler, gerçekleştirme ve önemli veritabanı kaynakları kullandıkları çünkü siler içinde dağıtılmış işlemler öneririz.</span><span class="sxs-lookup"><span data-stu-id="c435c-151">We recommend that you perform only updates, inserts, and deletes within distributed transactions because they consume significant database resources.</span></span> <span data-ttu-id="c435c-152">SELECT deyimleri veritabanı kaynaklarının gereksiz yere Kilitle ve bazı senaryolarda, işlemler için seçer kullanmak zorunda kalabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c435c-152">Select statements may lock database resources unnecessarily, and in some scenarios, you may have to use transactions for selects.</span></span> <span data-ttu-id="c435c-153">Diğer işlenen kaynak yöneticileri içerdiği sürece işlem kapsamı dışında herhangi bir veritabanı olmayan iş yapılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c435c-153">Any non-database work should be done outside the scope of the transaction, unless it involves other transacted resource managers.</span></span> <span data-ttu-id="c435c-154">İşlem kapsamı içindeki bir özel durum işleme, gelen işlem engeller ancak <xref:System.Transactions.TransactionScope> değişikliklerin, kodunuzun geri işlem kapsamı dışında hale getirdiği için hiçbir sınıfı vardır.</span><span class="sxs-lookup"><span data-stu-id="c435c-154">Although an exception in the scope of the transaction prevents the transaction from committing, the <xref:System.Transactions.TransactionScope> class has no provision for rolling back any changes your code has made outside the scope of the transaction itself.</span></span> <span data-ttu-id="c435c-155">İşlem geri alınır, bazı işlemler yapması gerekiyorsa, kendi uygulamasını yazmanız gereken <xref:System.Transactions.IEnlistmentNotification> arabirim ve açıkça işleme.</span><span class="sxs-lookup"><span data-stu-id="c435c-155">If you have to take some action when the transaction is rolled back, you must write your own implementation of the <xref:System.Transactions.IEnlistmentNotification> interface and explicitly enlist in the transaction.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c435c-156">Örnek</span><span class="sxs-lookup"><span data-stu-id="c435c-156">Example</span></span>  
 <span data-ttu-id="c435c-157">Çalışma <xref:System.Transactions> System.Transactions.dll başvurusu olmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="c435c-157">Working with <xref:System.Transactions> requires that you have a reference to System.Transactions.dll.</span></span>  
  
 <span data-ttu-id="c435c-158">Aşağıdaki işlevi bir promotable işlem iki tarafından temsil edilen iki farklı SQL Server örneği karşı farklı nasıl oluşturulacağını gösterir <xref:System.Data.SqlClient.SqlConnection> sarmalanır nesneleri, bir <xref:System.Transactions.TransactionScope> blok.</span><span class="sxs-lookup"><span data-stu-id="c435c-158">The following function demonstrates how to create a promotable transaction against two different SQL Server instances, represented by two different <xref:System.Data.SqlClient.SqlConnection> objects, which are wrapped in a <xref:System.Transactions.TransactionScope> block.</span></span> <span data-ttu-id="c435c-159">Kod oluşturur <xref:System.Transactions.TransactionScope> ile engelleyecek bir `using` deyimi içinde otomatik olarak kaydeder ilk bağlantıyı açar <xref:System.Transactions.TransactionScope>.</span><span class="sxs-lookup"><span data-stu-id="c435c-159">The code creates the <xref:System.Transactions.TransactionScope> block with a `using` statement and opens the first connection, which automatically enlists it in the <xref:System.Transactions.TransactionScope>.</span></span> <span data-ttu-id="c435c-160">İşlem başlangıçta, tam bir dağıtılmış işlem yok gibi basit bir işlem olarak kayıtlıdır.</span><span class="sxs-lookup"><span data-stu-id="c435c-160">The transaction is initially enlisted as a lightweight transaction, not a full distributed transaction.</span></span> <span data-ttu-id="c435c-161">İkinci bir bağlantı kayıtlı <xref:System.Transactions.TransactionScope> varsa yalnızca ilk bağlantı komut bir özel durum oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="c435c-161">The second connection is enlisted in the <xref:System.Transactions.TransactionScope> only if the command in the first connection does not throw an exception.</span></span> <span data-ttu-id="c435c-162">İkinci bağlantı açıldığında, işlem bir tam dağıtılmış işlem için otomatik olarak yükseltilir.</span><span class="sxs-lookup"><span data-stu-id="c435c-162">When the second connection is opened, the transaction is automatically promoted to a full distributed transaction.</span></span> <span data-ttu-id="c435c-163"><xref:System.Transactions.TransactionScope.Complete%2A> Yöntemi çağrılır, eğer yalnızca hiçbir özel durum harekete hangi hareketi tamamlar.</span><span class="sxs-lookup"><span data-stu-id="c435c-163">The <xref:System.Transactions.TransactionScope.Complete%2A> method is invoked, which commits the transaction only if no exceptions have been thrown.</span></span> <span data-ttu-id="c435c-164">Herhangi bir noktada bir özel durum oluştuktan varsa <xref:System.Transactions.TransactionScope> bloğu `Complete` değil çağrılması sağlar ve geri dağıtılmış işlem olacak geri <xref:System.Transactions.TransactionScope> sonunda elden kendi `using` blok.</span><span class="sxs-lookup"><span data-stu-id="c435c-164">If an exception has been thrown at any point in the <xref:System.Transactions.TransactionScope> block, `Complete` will not be called, and the distributed transaction will roll back when the <xref:System.Transactions.TransactionScope> is disposed at the end of its `using` block.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c435c-165">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c435c-165">See also</span></span>

- [<span data-ttu-id="c435c-166">İşlemler ve Eşzamanlılık</span><span class="sxs-lookup"><span data-stu-id="c435c-166">Transactions and Concurrency</span></span>](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)
- [<span data-ttu-id="c435c-167">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="c435c-167">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
