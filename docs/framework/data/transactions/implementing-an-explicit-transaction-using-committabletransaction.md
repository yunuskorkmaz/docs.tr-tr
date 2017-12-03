---
title: "Açık bir CommittableTransaction kullanarak işlem uygulama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 29efe5e5-897b-46c2-a35f-e599a273acc8
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cc6f039ffbdeaef70e3bc4eb71aa5046105f4ee9
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="implementing-an-explicit-transaction-using-committabletransaction"></a><span data-ttu-id="81003-102">Açık bir CommittableTransaction kullanarak işlem uygulama</span><span class="sxs-lookup"><span data-stu-id="81003-102">Implementing an Explicit Transaction using CommittableTransaction</span></span>
<span data-ttu-id="81003-103"><xref:System.Transactions.CommittableTransaction> Sınıfı kullanarak bir işlem kullanmak üzere uygulamalar için açık bir yol sağlar <xref:System.Transactions.TransactionScope> örtük olarak sınıf.</span><span class="sxs-lookup"><span data-stu-id="81003-103">The <xref:System.Transactions.CommittableTransaction> class provides an explicit way for applications to use a transaction, as opposed to using the <xref:System.Transactions.TransactionScope> class implicitly.</span></span> <span data-ttu-id="81003-104">Birden çok işlev çağrıları veya birden çok iş parçacığı çağrıları arasında aynı işlem kullanmak istediğiniz uygulamalar için kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="81003-104">It is useful for applications that want to use the same transaction across multiple function calls or multiple thread calls.</span></span> <span data-ttu-id="81003-105">Farklı <xref:System.Transactions.TransactionScope> uygulama yazıcısı sınıfının gerekir özellikle çağırmak <xref:System.Transactions.CommittableTransaction.Commit%2A> ve <xref:System.Transactions.Transaction.Rollback%2A> yürütün veya işlem iptal etmek için yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="81003-105">Unlike the <xref:System.Transactions.TransactionScope> class, the application writer needs to specifically call the <xref:System.Transactions.CommittableTransaction.Commit%2A> and <xref:System.Transactions.Transaction.Rollback%2A> methods in order to commit or abort the transaction.</span></span>  
  
## <a name="overview-of-the-committabletransaction-class"></a><span data-ttu-id="81003-106">CommittableTransaction sınıfı genel bakış</span><span class="sxs-lookup"><span data-stu-id="81003-106">Overview of the CommittableTransaction class</span></span>  
 <span data-ttu-id="81003-107"><xref:System.Transactions.CommittableTransaction> Sınıf türetilir <xref:System.Transactions.Transaction> sınıfı, bu nedenle tüm işlevselliğini ikincisi sağlama.</span><span class="sxs-lookup"><span data-stu-id="81003-107">The <xref:System.Transactions.CommittableTransaction> class derives from the <xref:System.Transactions.Transaction> class, therefore providing all the functionality of the latter.</span></span> <span data-ttu-id="81003-108">Özellikle yararlıdır <xref:System.Transactions.Transaction.Rollback%2A> yöntemi <xref:System.Transactions.Transaction> geri almak için de kullanılabilir sınıf bir <xref:System.Transactions.CommittableTransaction> nesne.</span><span class="sxs-lookup"><span data-stu-id="81003-108">Specifically useful is the <xref:System.Transactions.Transaction.Rollback%2A> method on the <xref:System.Transactions.Transaction> class that can also be used to rollback a <xref:System.Transactions.CommittableTransaction> object.</span></span>  
  
 <span data-ttu-id="81003-109"><xref:System.Transactions.Transaction> Sınıf benzer <xref:System.Transactions.CommittableTransaction> sınıfının ancak teklif değil bir `Commit` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="81003-109">The  <xref:System.Transactions.Transaction> class is similar to the <xref:System.Transactions.CommittableTransaction> class but does not offer a `Commit` method.</span></span> <span data-ttu-id="81003-110">Bu, işlem nesnesini (veya bunu klonlar) diğer yöntemleri (büyük olasılıkla diğer iş parçacıkları) hala hareket kaydedilmiş olduğunda denetleme sırasında geçirilecek sağlar.</span><span class="sxs-lookup"><span data-stu-id="81003-110">This enables you to pass the transaction object (or clones of it) to other methods (potentially on other threads) while still controlling when the transaction is committed.</span></span> <span data-ttu-id="81003-111">Çağrılan kodu listeleme ve işlem ancak yalnızca oluşturan oy verin <xref:System.Transactions.CommittableTransaction> nesnenin hareketi olanağı vardır.</span><span class="sxs-lookup"><span data-stu-id="81003-111">The called code is able to enlist and vote on the transaction, but only the creator of the <xref:System.Transactions.CommittableTransaction> object has the ability to commit the transaction.</span></span>  
  
 <span data-ttu-id="81003-112">Followings ile çalışırken dikkat etmelisiniz <xref:System.Transactions.CommittableTransaction> sınıfı</span><span class="sxs-lookup"><span data-stu-id="81003-112">You should note the followings when working with the <xref:System.Transactions.CommittableTransaction> class,</span></span>  
  
-   <span data-ttu-id="81003-113">Oluşturma bir <xref:System.Transactions.CommittableTransaction> işlem ortam işlem ayarlı değil.</span><span class="sxs-lookup"><span data-stu-id="81003-113">Creating a <xref:System.Transactions.CommittableTransaction> transaction does not set the ambient transaction.</span></span> <span data-ttu-id="81003-114">Özel olarak ayarlayın ve kaynak yöneticileri doğru işlem bağlamı altında uygun olduğunda çalışması emin olmak için ortam işlem sıfırlamak gerekir.</span><span class="sxs-lookup"><span data-stu-id="81003-114">You need to specifically set and reset the ambient transaction, to ensure that resource managers operate under the right transaction context when appropriate.</span></span> <span data-ttu-id="81003-115">Geçerli ortam işlem ayarlamak için statik ayarlayarak yoludur <xref:System.Transactions.Transaction.Current%2A> genel özellikte <xref:System.Transactions.Transaction> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="81003-115">The way to set the current ambient transaction is by setting the static <xref:System.Transactions.Transaction.Current%2A> property on the global <xref:System.Transactions.Transaction> object.</span></span>  
  
-   <span data-ttu-id="81003-116">Bir <xref:System.Transactions.CommittableTransaction> nesne olamaz yeniden kullanılabilecek.</span><span class="sxs-lookup"><span data-stu-id="81003-116">A <xref:System.Transactions.CommittableTransaction> object cannot be reused.</span></span> <span data-ttu-id="81003-117">Bir kez bir <xref:System.Transactions.CommittableTransaction> nesne yürütülmeli veya geri, yeniden işlemde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="81003-117">Once a <xref:System.Transactions.CommittableTransaction> object has been committed or rolled back, it cannot be used again in a transaction.</span></span> <span data-ttu-id="81003-118">Diğer bir deyişle, geçerli ortam işlem bağlamı olarak ayarlanamaz.</span><span class="sxs-lookup"><span data-stu-id="81003-118">That is, it cannot be set as the current ambient transaction context.</span></span>  
  
## <a name="creating-a-committabletransaction"></a><span data-ttu-id="81003-119">Bir CommittableTransaction oluşturma</span><span class="sxs-lookup"><span data-stu-id="81003-119">Creating a CommittableTransaction</span></span>  
 <span data-ttu-id="81003-120">Aşağıdaki örnek, yeni bir oluşturur <xref:System.Transactions.CommittableTransaction> ve onu kaydeder.</span><span class="sxs-lookup"><span data-stu-id="81003-120">The following sample creates a new <xref:System.Transactions.CommittableTransaction> and commits it.</span></span>  
  
 [!code-csharp[Tx_CommittableTx#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/tx_committabletx/cs/committabletxwithsql.cs#1)]
 [!code-vb[Tx_CommittableTx#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/tx_committabletx/vb/committabletxwithsql.vb#1)]  
  
 <span data-ttu-id="81003-121">Örneği oluşturmayı <xref:System.Transactions.CommittableTransaction> otomatik olarak ortam işlem bağlamı ayarlı değil.</span><span class="sxs-lookup"><span data-stu-id="81003-121">Creating an instance of <xref:System.Transactions.CommittableTransaction> does not automatically set the ambient transaction context.</span></span> <span data-ttu-id="81003-122">Bu nedenle, bir Kaynak Yöneticisi'ni üzerinde herhangi bir işlemi bu işlemin bir parçası değil.</span><span class="sxs-lookup"><span data-stu-id="81003-122">Therefore, any operation on a resource manager is not part of that transaction.</span></span> <span data-ttu-id="81003-123">Statik <xref:System.Transactions.Transaction.Current%2A> genel özellikte <xref:System.Transactions.Transaction> nesnesi ayarlamak veya ortam işlem almak için kullanılır ve uygulamayı el ile kaynak yöneticileri işlemde katılabilir emin olmak için ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="81003-123">The static <xref:System.Transactions.Transaction.Current%2A> property on the global <xref:System.Transactions.Transaction> object is used to set or retrieve the ambient transaction and the application must manually set it to ensure that resource managers can participate in the transaction.</span></span> <span data-ttu-id="81003-124">Eski ortam işlem kaydetme ve kullanarak bitirdikten sonra geri yükleme içinde iyi bir uygulamadır <xref:System.Transactions.CommittableTransaction> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="81003-124">It is also a good practice to save the old ambient transaction and restore it when you finish using the <xref:System.Transactions.CommittableTransaction> object.</span></span>  
  
 <span data-ttu-id="81003-125">İşlem gerçekleştirmeyi açıkça çağırması gerekir <xref:System.Transactions.CommittableTransaction.Commit%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="81003-125">To commit the transaction, you need to explicitly call the <xref:System.Transactions.CommittableTransaction.Commit%2A> method.</span></span> <span data-ttu-id="81003-126">Bir işlemin geri alınması için çağırmalısınız <xref:System.Transactions.Transaction.Rollback%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="81003-126">For rolling back a transaction, you should call the <xref:System.Transactions.Transaction.Rollback%2A> method.</span></span> <span data-ttu-id="81003-127">Başarılı olana dek dikkate almak önemlidir bir <xref:System.Transactions.CommittableTransaction> kabul edildiğini veya işlem hala kilitli, söz konusu tüm kaynakları geri alınamaz.</span><span class="sxs-lookup"><span data-stu-id="81003-127">It is important to note that until a <xref:System.Transactions.CommittableTransaction> has been committed or rolled back, all the resources involved in that transaction are still locked.</span></span>  
  
 <span data-ttu-id="81003-128">Bir <xref:System.Transactions.CommittableTransaction> işlev çağrıları ve dizileri arasında nesne kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="81003-128">A <xref:System.Transactions.CommittableTransaction> object can be used across function calls and threads.</span></span> <span data-ttu-id="81003-129">Ancak, bu özel durumları işlemek ve özellikle çağırmak için uygulama geliştiricisi kadar kadar <xref:System.Transactions.Transaction.Rollback%28System.Exception%29> yöntemi hataları durumunda.</span><span class="sxs-lookup"><span data-stu-id="81003-129">However, it is up to the application developer to handle exceptions and specifically call the <xref:System.Transactions.Transaction.Rollback%28System.Exception%29> method in case of failures.</span></span>  
  
## <a name="asynchronous-commit"></a><span data-ttu-id="81003-130">Zaman uyumsuz tamamlama</span><span class="sxs-lookup"><span data-stu-id="81003-130">Asynchronous Commit</span></span>  
 <span data-ttu-id="81003-131"><xref:System.Transactions.CommittableTransaction> Sınıfı zaman uyumsuz bir işlem gerçekleştirmeden için bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="81003-131">The <xref:System.Transactions.CommittableTransaction> class also provides a mechanism for committing a transaction asynchronously.</span></span> <span data-ttu-id="81003-132">Birden çok veritabanı erişimi ve olası ağ gecikmesi gerektirebilir gibi bir işlem yürütme önemli ölçüde zaman alabilir.</span><span class="sxs-lookup"><span data-stu-id="81003-132">A transaction commit can take substantial time, as it might involve multiple database access and possible network latency.</span></span> <span data-ttu-id="81003-133">Yüksek verimlilik uygulamalarında kilitlenmeleri yapmak istemiyorsanız, işlem iş mümkün olan en kısa sürede tamamlamak için zaman uyumsuz tamamlama kullanın ve yürütme işlemi bir arka plan görevi olarak çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="81003-133">When you want to avoid deadlocks in high throughput applications, you can use asynchronous commit to finish the transactional work as soon as possible, and run the commit operation as a background task.</span></span> <span data-ttu-id="81003-134"><xref:System.Transactions.CommittableTransaction.BeginCommit%2A> Ve <xref:System.Transactions.CommittableTransaction.EndCommit%2A> yöntemlerinin <xref:System.Transactions.CommittableTransaction> sınıfı, bunu yapmak izin.</span><span class="sxs-lookup"><span data-stu-id="81003-134">The <xref:System.Transactions.CommittableTransaction.BeginCommit%2A> and <xref:System.Transactions.CommittableTransaction.EndCommit%2A> methods of the <xref:System.Transactions.CommittableTransaction> class allow you to do so.</span></span>  
  
 <span data-ttu-id="81003-135">Çağırabilirsiniz <xref:System.Transactions.CommittableTransaction.BeginCommit%2A> yürütme Soyguncu iş parçacığı havuzu için bir iş parçacığı gönderme.</span><span class="sxs-lookup"><span data-stu-id="81003-135">You can call <xref:System.Transactions.CommittableTransaction.BeginCommit%2A> to dispatch the commit holdup to a thread from the thread pool.</span></span> <span data-ttu-id="81003-136">Ayrıca, çağırabilirsiniz <xref:System.Transactions.CommittableTransaction.EndCommit%2A> işlem gerçekte kaydedilmiş olup olmadığını belirlemek için.</span><span class="sxs-lookup"><span data-stu-id="81003-136">You can also call <xref:System.Transactions.CommittableTransaction.EndCommit%2A> to determine if the transaction has actually been committed.</span></span> <span data-ttu-id="81003-137">İşlem herhangi bir nedenle başarısız oldu, <xref:System.Transactions.CommittableTransaction.EndCommit%2A> bir işlem özel durumu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="81003-137">If the transaction failed to commit for whatever reason, <xref:System.Transactions.CommittableTransaction.EndCommit%2A> raises a transaction exception.</span></span> <span data-ttu-id="81003-138">İşlem henüz zamanına göre gerçekleştirilir değil, <xref:System.Transactions.CommittableTransaction.EndCommit%2A> olduğu adlı hareket kaydedilmiş veya iptal kadar arayan engellendi.</span><span class="sxs-lookup"><span data-stu-id="81003-138">If the transaction is not yet committed by the time <xref:System.Transactions.CommittableTransaction.EndCommit%2A> is called, the caller is blocked until the transaction is committed or aborted.</span></span>  
  
 <span data-ttu-id="81003-139">Bir zaman uyumsuz tamamlama yapmak için kolay Sistemi'ne tamamlandığında çağrılacak bir geri çağırma yöntemi sağlayarak yoludur.</span><span class="sxs-lookup"><span data-stu-id="81003-139">The easiest way to do an asynchronous commit is by providing a callback method, to be called when committing is finished.</span></span> <span data-ttu-id="81003-140">Ancak, çağırmalıdır <xref:System.Transactions.CommittableTransaction.EndCommit%2A> özgün yöntemini <xref:System.Transactions.CommittableTransaction> arama çağırmak için kullanılan nesne.</span><span class="sxs-lookup"><span data-stu-id="81003-140">However, you must call the <xref:System.Transactions.CommittableTransaction.EndCommit%2A> method on the original <xref:System.Transactions.CommittableTransaction> object used to invoke the call.</span></span> <span data-ttu-id="81003-141">Bu nesne elde etmek için alta yapabilecekleriniz *IAsyncResult* geri çağırma yöntemi parametresinin beri <xref:System.Transactions.CommittableTransaction> sınıfını uygular <xref:System.IAsyncResult> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="81003-141">To obtain that object, you can downcast the *IAsyncResult* parameter of the callback method, since the <xref:System.Transactions.CommittableTransaction> class implements <xref:System.IAsyncResult> class.</span></span>  
  
 <span data-ttu-id="81003-142">Aşağıdaki örnek, bir zaman uyumsuz tamamlama nasıl yapılacağı gösterir.</span><span class="sxs-lookup"><span data-stu-id="81003-142">The following example shows how an asynchronous commit can be done.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="81003-143">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="81003-143">See Also</span></span>  
 [<span data-ttu-id="81003-144">Örtük bir işlem kapsamı kullanarak işlem uygulama</span><span class="sxs-lookup"><span data-stu-id="81003-144">Implementing an Implicit Transaction using Transaction Scope</span></span>](../../../../docs/framework/data/transactions/implementing-an-implicit-transaction-using-transaction-scope.md)  
 [<span data-ttu-id="81003-145">İşlem</span><span class="sxs-lookup"><span data-stu-id="81003-145">Transaction Processing</span></span>](../../../../docs/framework/data/transactions/index.md)
