---
title: CommittableTransaction Kullanarak Belirtik İşlem Uygulama
description: .NET 'teki CommittableTransaction sınıfını kullanarak açık bir işlem uygulayın. Bu sınıf, uygulamaların bir işlem kullanması için açık bir yol sağladı.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 29efe5e5-897b-46c2-a35f-e599a273acc8
ms.openlocfilehash: 7e1d78b581fcb3c4b2265f1d04cf2aba83faa28a
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91182889"
---
# <a name="implementing-an-explicit-transaction-using-committabletransaction"></a><span data-ttu-id="eec82-104">CommittableTransaction Kullanarak Belirtik İşlem Uygulama</span><span class="sxs-lookup"><span data-stu-id="eec82-104">Implementing an Explicit Transaction using CommittableTransaction</span></span>

<span data-ttu-id="eec82-105"><xref:System.Transactions.CommittableTransaction>Sınıfı, uygulamaların bir işlem kullanması için açık bir yol sağlar, bu da sınıfı örtülü olarak kullanmaktır <xref:System.Transactions.TransactionScope> .</span><span class="sxs-lookup"><span data-stu-id="eec82-105">The <xref:System.Transactions.CommittableTransaction> class provides an explicit way for applications to use a transaction, as opposed to using the <xref:System.Transactions.TransactionScope> class implicitly.</span></span> <span data-ttu-id="eec82-106">Birden çok işlev çağrısı veya birden çok iş parçacığı çağrısı genelinde aynı işlemi kullanmak isteyen uygulamalar için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="eec82-106">It is useful for applications that want to use the same transaction across multiple function calls or multiple thread calls.</span></span> <span data-ttu-id="eec82-107">Sınıfının aksine <xref:System.Transactions.TransactionScope> , uygulama yazıcısının <xref:System.Transactions.CommittableTransaction.Commit%2A> <xref:System.Transactions.Transaction.Rollback%2A> işlem yürütmek veya durdurmak için özel olarak ve yöntemlerini çağırması gerekir.</span><span class="sxs-lookup"><span data-stu-id="eec82-107">Unlike the <xref:System.Transactions.TransactionScope> class, the application writer needs to specifically call the <xref:System.Transactions.CommittableTransaction.Commit%2A> and <xref:System.Transactions.Transaction.Rollback%2A> methods in order to commit or abort the transaction.</span></span>  
  
## <a name="overview-of-the-committabletransaction-class"></a><span data-ttu-id="eec82-108">CommittableTransaction sınıfına genel bakış</span><span class="sxs-lookup"><span data-stu-id="eec82-108">Overview of the CommittableTransaction class</span></span>  

 <span data-ttu-id="eec82-109"><xref:System.Transactions.CommittableTransaction> Sınıf türetilir <xref:System.Transactions.Transaction> sınıfı, bu nedenle tüm işlevselliğini ikincisi sağlama.</span><span class="sxs-lookup"><span data-stu-id="eec82-109">The <xref:System.Transactions.CommittableTransaction> class derives from the <xref:System.Transactions.Transaction> class, therefore providing all the functionality of the latter.</span></span> <span data-ttu-id="eec82-110">Özellikle yararlıdır <xref:System.Transactions.Transaction.Rollback%2A> yöntemi <xref:System.Transactions.Transaction> geri almak için de kullanılabilir sınıf bir <xref:System.Transactions.CommittableTransaction> nesne.</span><span class="sxs-lookup"><span data-stu-id="eec82-110">Specifically useful is the <xref:System.Transactions.Transaction.Rollback%2A> method on the <xref:System.Transactions.Transaction> class that can also be used to rollback a <xref:System.Transactions.CommittableTransaction> object.</span></span>  
  
 <span data-ttu-id="eec82-111"><xref:System.Transactions.Transaction> Sınıf benzer <xref:System.Transactions.CommittableTransaction> sınıfının ancak teklif değil bir `Commit` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="eec82-111">The  <xref:System.Transactions.Transaction> class is similar to the <xref:System.Transactions.CommittableTransaction> class but does not offer a `Commit` method.</span></span> <span data-ttu-id="eec82-112">Bu işlem, işlemin ne zaman planlanmakta olduğunu denetlerken, işlem nesnesini (veya bunların klonlarını) diğer yöntemlere (potansiyel olarak diğer iş parçacıklarında) geçirmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="eec82-112">This enables you to pass the transaction object (or clones of it) to other methods (potentially on other threads) while still controlling when the transaction is committed.</span></span> <span data-ttu-id="eec82-113">Çağrılan kod, işlem üzerinde listeleme ve oy verebilir, ancak yalnızca <xref:System.Transactions.CommittableTransaction> nesnenin Oluşturucusu işlemi işleme olanağına sahiptir.</span><span class="sxs-lookup"><span data-stu-id="eec82-113">The called code is able to enlist and vote on the transaction, but only the creator of the <xref:System.Transactions.CommittableTransaction> object has the ability to commit the transaction.</span></span>  
  
 <span data-ttu-id="eec82-114">Followings ile çalışırken dikkat etmelisiniz <xref:System.Transactions.CommittableTransaction> sınıfı</span><span class="sxs-lookup"><span data-stu-id="eec82-114">You should note the followings when working with the <xref:System.Transactions.CommittableTransaction> class,</span></span>  
  
- <span data-ttu-id="eec82-115">İşlem oluşturmak <xref:System.Transactions.CommittableTransaction> çevresel işlem yapmaz.</span><span class="sxs-lookup"><span data-stu-id="eec82-115">Creating a <xref:System.Transactions.CommittableTransaction> transaction does not set the ambient transaction.</span></span> <span data-ttu-id="eec82-116">Kaynak yöneticilerinin uygun olduğunda doğru işlem bağlamında çalışmasını sağlamak için, ortam işlemini özellikle ayarlamanız ve sıfırlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="eec82-116">You need to specifically set and reset the ambient transaction, to ensure that resource managers operate under the right transaction context when appropriate.</span></span> <span data-ttu-id="eec82-117">Geçerli ortam işlemini ayarlama yöntemi, <xref:System.Transactions.Transaction.Current%2A> genel nesnede statik özelliği ayarlamadır <xref:System.Transactions.Transaction> .</span><span class="sxs-lookup"><span data-stu-id="eec82-117">The way to set the current ambient transaction is by setting the static <xref:System.Transactions.Transaction.Current%2A> property on the global <xref:System.Transactions.Transaction> object.</span></span>  
  
- <span data-ttu-id="eec82-118">Bir <xref:System.Transactions.CommittableTransaction> nesne olamaz yeniden kullanılabilecek.</span><span class="sxs-lookup"><span data-stu-id="eec82-118">A <xref:System.Transactions.CommittableTransaction> object cannot be reused.</span></span> <span data-ttu-id="eec82-119">Bir <xref:System.Transactions.CommittableTransaction> nesne kaydedildikten veya geri alındıktan sonra, bir işlem içinde yeniden kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="eec82-119">Once a <xref:System.Transactions.CommittableTransaction> object has been committed or rolled back, it cannot be used again in a transaction.</span></span> <span data-ttu-id="eec82-120">Diğer bir deyişle, geçerli ortam işlem bağlamı olarak ayarlanamaz.</span><span class="sxs-lookup"><span data-stu-id="eec82-120">That is, it cannot be set as the current ambient transaction context.</span></span>  
  
## <a name="creating-a-committabletransaction"></a><span data-ttu-id="eec82-121">CommittableTransaction oluşturma</span><span class="sxs-lookup"><span data-stu-id="eec82-121">Creating a CommittableTransaction</span></span>  

 <span data-ttu-id="eec82-122">Aşağıdaki örnek, yeni bir oluşturur <xref:System.Transactions.CommittableTransaction> ve onu kaydeder.</span><span class="sxs-lookup"><span data-stu-id="eec82-122">The following sample creates a new <xref:System.Transactions.CommittableTransaction> and commits it.</span></span>  
  
 [!code-csharp[Tx_CommittableTx#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/tx_committabletx/cs/committabletxwithsql.cs#1)]
 [!code-vb[Tx_CommittableTx#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/tx_committabletx/vb/committabletxwithsql.vb#1)]  
  
 <span data-ttu-id="eec82-123">Bir örneğinin oluşturulması, <xref:System.Transactions.CommittableTransaction> ortam işlem bağlamını otomatik olarak yapmaz.</span><span class="sxs-lookup"><span data-stu-id="eec82-123">Creating an instance of <xref:System.Transactions.CommittableTransaction> does not automatically set the ambient transaction context.</span></span> <span data-ttu-id="eec82-124">Bu nedenle, bir kaynak yöneticisi üzerinde herhangi bir işlem bu işlemin bir parçası değildir.</span><span class="sxs-lookup"><span data-stu-id="eec82-124">Therefore, any operation on a resource manager is not part of that transaction.</span></span> <span data-ttu-id="eec82-125"><xref:System.Transactions.Transaction.Current%2A>Genel nesnedeki static özelliği, <xref:System.Transactions.Transaction> ortam işlemini ayarlamak ya da almak için kullanılır ve uygulama, kaynak yöneticilerinin işleme katılmasını sağlamak için el ile ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="eec82-125">The static <xref:System.Transactions.Transaction.Current%2A> property on the global <xref:System.Transactions.Transaction> object is used to set or retrieve the ambient transaction and the application must manually set it to ensure that resource managers can participate in the transaction.</span></span> <span data-ttu-id="eec82-126">Ayrıca, eski çevresel işlemi kaydetmek ve nesneyi kullanmayı bitirdiğinizde geri yüklemek iyi bir uygulamadır <xref:System.Transactions.CommittableTransaction> .</span><span class="sxs-lookup"><span data-stu-id="eec82-126">It is also a good practice to save the old ambient transaction and restore it when you finish using the <xref:System.Transactions.CommittableTransaction> object.</span></span>  
  
 <span data-ttu-id="eec82-127">İşlemi yürütmek için yöntemi açıkça çağırmanız gerekir <xref:System.Transactions.CommittableTransaction.Commit%2A> .</span><span class="sxs-lookup"><span data-stu-id="eec82-127">To commit the transaction, you need to explicitly call the <xref:System.Transactions.CommittableTransaction.Commit%2A> method.</span></span> <span data-ttu-id="eec82-128">Bir işlemi geri almak için yöntemini çağırmanız gerekir <xref:System.Transactions.Transaction.Rollback%2A> .</span><span class="sxs-lookup"><span data-stu-id="eec82-128">For rolling back a transaction, you should call the <xref:System.Transactions.Transaction.Rollback%2A> method.</span></span> <span data-ttu-id="eec82-129">Bir <xref:System.Transactions.CommittableTransaction> işlem kaydedilene veya geri alınana kadar, bu işlemde yer alan tüm kaynakların hala kilitli olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="eec82-129">It is important to note that until a <xref:System.Transactions.CommittableTransaction> has been committed or rolled back, all the resources involved in that transaction are still locked.</span></span>  
  
 <span data-ttu-id="eec82-130">Bir <xref:System.Transactions.CommittableTransaction> işlev çağrıları ve dizileri arasında nesne kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="eec82-130">A <xref:System.Transactions.CommittableTransaction> object can be used across function calls and threads.</span></span> <span data-ttu-id="eec82-131">Ancak, bu özel durumları işlemek ve özellikle çağırmak için uygulama geliştiricisi kadar kadar <xref:System.Transactions.Transaction.Rollback%28System.Exception%29> yöntemi hataları durumunda.</span><span class="sxs-lookup"><span data-stu-id="eec82-131">However, it is up to the application developer to handle exceptions and specifically call the <xref:System.Transactions.Transaction.Rollback%28System.Exception%29> method in case of failures.</span></span>  
  
## <a name="asynchronous-commit"></a><span data-ttu-id="eec82-132">Zaman uyumsuz tamamlama</span><span class="sxs-lookup"><span data-stu-id="eec82-132">Asynchronous Commit</span></span>  

 <span data-ttu-id="eec82-133"><xref:System.Transactions.CommittableTransaction>Sınıfı ayrıca bir işlemi zaman uyumsuz olarak yürütmek için bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="eec82-133">The <xref:System.Transactions.CommittableTransaction> class also provides a mechanism for committing a transaction asynchronously.</span></span> <span data-ttu-id="eec82-134">Bir işlem işleme, birden çok veritabanı erişimi ve olası ağ gecikmesi olabileceği için önemli ölçüde zaman alabilir.</span><span class="sxs-lookup"><span data-stu-id="eec82-134">A transaction commit can take substantial time, as it might involve multiple database access and possible network latency.</span></span> <span data-ttu-id="eec82-135">Yüksek performanslı uygulamalarda kilitlenmeleri önlemek istediğinizde, işlem işini en kısa sürede tamamlamak için zaman uyumsuz yürütmeyi kullanabilir ve tamamlama işlemini bir arka plan görevi olarak çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eec82-135">When you want to avoid deadlocks in high throughput applications, you can use asynchronous commit to finish the transactional work as soon as possible, and run the commit operation as a background task.</span></span> <span data-ttu-id="eec82-136"><xref:System.Transactions.CommittableTransaction.BeginCommit%2A> Ve <xref:System.Transactions.CommittableTransaction.EndCommit%2A> yöntemlerinin <xref:System.Transactions.CommittableTransaction> sınıfı, bunu yapmak izin.</span><span class="sxs-lookup"><span data-stu-id="eec82-136">The <xref:System.Transactions.CommittableTransaction.BeginCommit%2A> and <xref:System.Transactions.CommittableTransaction.EndCommit%2A> methods of the <xref:System.Transactions.CommittableTransaction> class allow you to do so.</span></span>  
  
 <span data-ttu-id="eec82-137">Çağırabilirsiniz <xref:System.Transactions.CommittableTransaction.BeginCommit%2A> yürütme Soyguncu iş parçacığı havuzu için bir iş parçacığı gönderme.</span><span class="sxs-lookup"><span data-stu-id="eec82-137">You can call <xref:System.Transactions.CommittableTransaction.BeginCommit%2A> to dispatch the commit holdup to a thread from the thread pool.</span></span> <span data-ttu-id="eec82-138"><xref:System.Transactions.CommittableTransaction.EndCommit%2A>İşlemin gerçekten kaydedilmiş olup olmadığını belirleme çağrısı yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eec82-138">You can also call <xref:System.Transactions.CommittableTransaction.EndCommit%2A> to determine if the transaction has actually been committed.</span></span> <span data-ttu-id="eec82-139">İşlem herhangi bir nedenden dolayı işleme başarısız olursa, <xref:System.Transactions.CommittableTransaction.EndCommit%2A> bir işlem özel durumu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="eec82-139">If the transaction failed to commit for whatever reason, <xref:System.Transactions.CommittableTransaction.EndCommit%2A> raises a transaction exception.</span></span> <span data-ttu-id="eec82-140">İşlem henüz zamana göre yürütülmemişse <xref:System.Transactions.CommittableTransaction.EndCommit%2A> , işlem kaydedilene veya durduruluncaya kadar çağrı engellenir.</span><span class="sxs-lookup"><span data-stu-id="eec82-140">If the transaction is not yet committed by the time <xref:System.Transactions.CommittableTransaction.EndCommit%2A> is called, the caller is blocked until the transaction is committed or aborted.</span></span>  
  
 <span data-ttu-id="eec82-141">Bir zaman uyumsuz tamamlama yapmak için kolay Sistemi'ne tamamlandığında çağrılacak bir geri çağırma yöntemi sağlayarak yoludur.</span><span class="sxs-lookup"><span data-stu-id="eec82-141">The easiest way to do an asynchronous commit is by providing a callback method, to be called when committing is finished.</span></span> <span data-ttu-id="eec82-142">Ancak, çağırmalıdır <xref:System.Transactions.CommittableTransaction.EndCommit%2A> özgün yöntemini <xref:System.Transactions.CommittableTransaction> arama çağırmak için kullanılan nesne.</span><span class="sxs-lookup"><span data-stu-id="eec82-142">However, you must call the <xref:System.Transactions.CommittableTransaction.EndCommit%2A> method on the original <xref:System.Transactions.CommittableTransaction> object used to invoke the call.</span></span> <span data-ttu-id="eec82-143">Bu nesneyi almak için, sınıf sınıfı uyguladığı için geri çağırma yönteminin *IAsyncResult* parametresini alt türe dönüştürebilirsiniz <xref:System.Transactions.CommittableTransaction> <xref:System.IAsyncResult> .</span><span class="sxs-lookup"><span data-stu-id="eec82-143">To obtain that object, you can downcast the *IAsyncResult* parameter of the callback method, since the <xref:System.Transactions.CommittableTransaction> class implements <xref:System.IAsyncResult> class.</span></span>  
  
 <span data-ttu-id="eec82-144">Aşağıdaki örnek, bir zaman uyumsuz tamamlama nasıl yapılacağı gösterir.</span><span class="sxs-lookup"><span data-stu-id="eec82-144">The following example shows how an asynchronous commit can be done.</span></span>  
  
```csharp  
public void DoTransactionalWork()  
{  
     Transaction oldAmbient = Transaction.Current;  
     CommittableTransaction committableTransaction = new CommittableTransaction();  
     Transaction.Current = committableTransaction;  
  
     try  
     {  
          /* Perform transactional work here */  
          // No errors - commit transaction asynchronously  
          committableTransaction.BeginCommit(OnCommitted,null);  
     }  
     finally  
     {  
          //Restore the ambient transaction
          Transaction.Current = oldAmbient;  
     }  
}  
void OnCommitted(IAsyncResult asyncResult)  
{  
     CommittableTransaction committableTransaction;  
     committableTransaction = asyncResult as CommittableTransaction;
     Debug.Assert(committableTransaction != null);  
     try  
     {  
          using(committableTransaction)  
          {  
               committableTransaction.EndCommit(asyncResult);  
          }  
     }  
     catch(TransactionException e)  
     {  
          //Handle the failure to commit  
     }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="eec82-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eec82-145">See also</span></span>

- [<span data-ttu-id="eec82-146">İşlem Kapsamı Kullanarak Örtük İşlem Uygulama</span><span class="sxs-lookup"><span data-stu-id="eec82-146">Implementing an Implicit Transaction using Transaction Scope</span></span>](implementing-an-implicit-transaction-using-transaction-scope.md)
- [<span data-ttu-id="eec82-147">İşlem Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="eec82-147">Transaction Processing</span></span>](index.md)
