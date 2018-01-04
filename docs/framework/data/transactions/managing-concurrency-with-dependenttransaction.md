---
title: "Eşzamanlılık DependentTransaction ile yönetme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b85a97d8-8e02-4555-95df-34c8af095148
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ffda721459ef81d148d55359362fe1aeaf9e699e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="managing-concurrency-with-dependenttransaction"></a><span data-ttu-id="b8a77-102">Eşzamanlılık DependentTransaction ile yönetme</span><span class="sxs-lookup"><span data-stu-id="b8a77-102">Managing Concurrency with DependentTransaction</span></span>
<span data-ttu-id="b8a77-103"><xref:System.Transactions.Transaction> Nesnesi kullanılarak oluşturulan <xref:System.Transactions.Transaction.DependentClone%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b8a77-103">The <xref:System.Transactions.Transaction> object is created using the <xref:System.Transactions.Transaction.DependentClone%2A> method.</span></span> <span data-ttu-id="b8a77-104">Tek amacı, bazı bir kod (örneğin, bir çalışan iş parçacığı) parçalarını hala iş üzerinde işlem gerçekleştirirken işlem tamamlanamaz garanti olmaktır.</span><span class="sxs-lookup"><span data-stu-id="b8a77-104">Its sole purpose is to guarantee that the transaction cannot commit while some other pieces of code (for example, a worker thread) are still performing work on the transaction.</span></span> <span data-ttu-id="b8a77-105">Kopyalanan işlem içinde çalışmanın tam ve kabul edilebilmesi için hazır olduğunda, hareket kullanarak Oluşturucusu bildirebilir <xref:System.Transactions.DependentTransaction.Complete%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b8a77-105">When the work done within the cloned transaction is complete and ready to be committed, it can notify the creator of the transaction using the <xref:System.Transactions.DependentTransaction.Complete%2A> method.</span></span> <span data-ttu-id="b8a77-106">Bu nedenle, tutarlılık ve veri doğruluğunu saklayabilir.</span><span class="sxs-lookup"><span data-stu-id="b8a77-106">Thus, you can preserve the consistency and correctness of data.</span></span>  
  
 <span data-ttu-id="b8a77-107"><xref:System.Transactions.DependentTransaction> Sınıf ayrıca zaman uyumsuz görevler arasında eşzamanlılık yönetmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b8a77-107">The <xref:System.Transactions.DependentTransaction> class can also be used to manage concurrency between asynchronous tasks.</span></span> <span data-ttu-id="b8a77-108">Bu senaryoda, kendi görevlere bağımlı kopya çalışırken herhangi bir kod yürütmek üst devam edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b8a77-108">In this scenario, the parent can continue to execute any code while the dependent clone works on its own tasks.</span></span> <span data-ttu-id="b8a77-109">Diğer bir deyişle, üst öğenin yürütme bağımlı tamamlanıncaya kadar engellenmemiş.</span><span class="sxs-lookup"><span data-stu-id="b8a77-109">In other words, the parent's execution is not blocked until the dependent completes.</span></span>  
  
## <a name="creating-a-dependent-clone"></a><span data-ttu-id="b8a77-110">Bağımlı bir kopya oluşturma</span><span class="sxs-lookup"><span data-stu-id="b8a77-110">Creating a Dependent Clone</span></span>  
 <span data-ttu-id="b8a77-111">Bağımlı bir işlem oluşturmak için arama <xref:System.Transactions.Transaction.DependentClone%2A> yöntemi ve geçişi <xref:System.Transactions.DependentCloneOption> bir parametre olarak numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="b8a77-111">To create a dependent transaction, call the <xref:System.Transactions.Transaction.DependentClone%2A> method and pass the <xref:System.Transactions.DependentCloneOption> enumeration as a parameter.</span></span> <span data-ttu-id="b8a77-112">Bu parametre işlem davranışını tanımlar `Commit` bağımlı kopya işlemi yürütmek hazır olduğunu belirten önce üst işlem çağrılır (çağırarak <xref:System.Transactions.DependentTransaction.Complete%2A> yöntemi).</span><span class="sxs-lookup"><span data-stu-id="b8a77-112">This parameter defines the behavior of the transaction if `Commit` is called on the parent transaction before the dependent clone indicates that it is ready for the transaction to commit (by calling the <xref:System.Transactions.DependentTransaction.Complete%2A> method).</span></span> <span data-ttu-id="b8a77-113">Bu parameTRe için şu değerler geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="b8a77-113">The following values are valid for this parameter:</span></span>  
  
-   <span data-ttu-id="b8a77-114"><xref:System.Transactions.DependentCloneOption.BlockCommitUntilComplete>üst işlem süreleri kadar üst işlemin kaydetme işlemi out veya kadar engeller bağımlı bir işlem oluşturur <xref:System.Transactions.DependentTransaction.Complete%2A> kendi tamamlama gösteren tüm bağımlıları üzerinde olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="b8a77-114"><xref:System.Transactions.DependentCloneOption.BlockCommitUntilComplete> creates a dependent transaction that blocks the commit process of the parent transaction until the parent transaction times out, or until <xref:System.Transactions.DependentTransaction.Complete%2A> is called on all dependents indicating their completion.</span></span> <span data-ttu-id="b8a77-115">Bu, istemci bağımlı işlemleri tamamlanana kadar tamamlamaya üst işlemin istemediği durumunda faydalı olur.</span><span class="sxs-lookup"><span data-stu-id="b8a77-115">This is useful when the client does not want the parent transaction to commit until the dependent transactions have completed.</span></span> <span data-ttu-id="b8a77-116">Üst çalışmasını çağrıları ve bağımlı işlem'den önceki bittikten varsa <xref:System.Transactions.CommittableTransaction.Commit%2A> işleme, burada ek iş üzerinde işlem yapılabilir ve yeni kayıtlar oluşturulabilir, tüm kadar bir durumda kaydetme işlemi engellendi Bağımlılıklar çağrı <xref:System.Transactions.DependentTransaction.Complete%2A>.</span><span class="sxs-lookup"><span data-stu-id="b8a77-116">If the parent finishes its work earlier than the dependent transaction and calls <xref:System.Transactions.CommittableTransaction.Commit%2A> on the transaction, the commit process is blocked in a state where additional work can be done on the transaction and new enlistments can be created, until all of the dependents call <xref:System.Transactions.DependentTransaction.Complete%2A>.</span></span> <span data-ttu-id="b8a77-117">Bunların tümünün iş ve çağrı tamamladıktan hemen sonra <xref:System.Transactions.DependentTransaction.Complete%2A>, işlem yürütme işlemi başlar.</span><span class="sxs-lookup"><span data-stu-id="b8a77-117">As soon as all of them have finished their work and call <xref:System.Transactions.DependentTransaction.Complete%2A>, the commit process for the transaction begins.</span></span>  
  
-   <span data-ttu-id="b8a77-118"><xref:System.Transactions.DependentCloneOption.RollbackIfNotComplete>, diğer yandan, otomatik olarak durdurur bağımlı bir işlem oluşturur <xref:System.Transactions.CommittableTransaction.Commit%2A> önce üst işlem olarak adlandırılan <xref:System.Transactions.DependentTransaction.Complete%2A> olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="b8a77-118"><xref:System.Transactions.DependentCloneOption.RollbackIfNotComplete>, on the other hand, creates a dependent transaction that automatically aborts if <xref:System.Transactions.CommittableTransaction.Commit%2A> is called on the parent transaction before <xref:System.Transactions.DependentTransaction.Complete%2A> is called.</span></span> <span data-ttu-id="b8a77-119">Bu durumda, bağımlı işlem içinde tüm çalışmanın bir işlem ömrü içinde olduğu gibi olup hiç kimse yalnızca bir kısmını uygulamak için bir fırsat içerir.</span><span class="sxs-lookup"><span data-stu-id="b8a77-119">In this case, all the work done in the dependent transaction is intact within one transaction lifetime, and no one has a chance to commit just a portion of it.</span></span>  
  
 <span data-ttu-id="b8a77-120"><xref:System.Transactions.DependentTransaction.Complete%2A> Yalnızca uygulamanızı bağımlı işlem; işini tamamlandığında sonra yöntemi çağrılmalıdır Aksi halde, bir <xref:System.InvalidOperationException> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="b8a77-120">The <xref:System.Transactions.DependentTransaction.Complete%2A> method must be called only once when your application finishes its work on the dependent transaction; otherwise, a <xref:System.InvalidOperationException> is thrown.</span></span> <span data-ttu-id="b8a77-121">Bu çağrı çağrıldıktan sonra işlem üzerinde herhangi bir ek çalışmayı çalışmamalısınız ya da bir özel durum.</span><span class="sxs-lookup"><span data-stu-id="b8a77-121">After this call is invoked, you must not attempt any additional work on the transaction, or an exception is thrown.</span></span>  
  
 <span data-ttu-id="b8a77-122">Aşağıdaki kod örneğinde, bağımlı işlem kopyalama ve onu bir çalışan iş parçacığı tarafından iki eş zamanlı görevleri yönetmek için bağımlı bir işlem oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b8a77-122">The following code example shows how to create a dependent transaction to manage two concurrent tasks by cloning a dependent transaction and passing it to a worker thread.</span></span>  
  
```csharp  
public class WorkerThread  
{  
    public void DoWork(DependentTransaction dependentTransaction)  
    {  
        Thread thread = new Thread(ThreadMethod);  
        thread.Start(dependentTransaction);   
    }  
  
    public void ThreadMethod(object transaction)   
    {   
        DependentTransaction dependentTransaction = transaction as DependentTransaction;  
        Debug.Assert(dependentTransaction != null);   
        try  
        {  
            using(TransactionScope ts = new TransactionScope(dependentTransaction))  
            {  
                /* Perform transactional work here */   
                ts.Complete();  
            }  
        }  
        finally  
        {  
            dependentTransaction.Complete();   
             dependentTransaction.Dispose();   
        }  
    }  
  
//Client code   
using(TransactionScope scope = new TransactionScope())  
{  
    Transaction currentTransaction = Transaction.Current;  
    DependentTransaction dependentTransaction;      
    dependentTransaction = currentTransaction.DependentClone(DependentCloneOption.BlockCommitUntilComplete);  
    WorkerThread workerThread = new WorkerThread();  
    workerThread.DoWork(dependentTransaction);  
    /* Do some transactional work here, then: */  
    scope.Complete();  
}  
```  
  
 <span data-ttu-id="b8a77-123">İstemci kodu ayrıca ortam işlem ayarlar işlemsel bir kapsam oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b8a77-123">The client code creates a transactional scope that also sets the ambient transaction.</span></span> <span data-ttu-id="b8a77-124">Ortam işlem iş parçacığı başarılı.</span><span class="sxs-lookup"><span data-stu-id="b8a77-124">You should not pass the ambient transaction to the worker thread.</span></span> <span data-ttu-id="b8a77-125">Çağırarak geçerli (ortam) işlem bunun yerine, kopyalamalıdır <xref:System.Transactions.Transaction.DependentClone%2A> geçerli işlem ve çalışan iş parçacığı bağımlı geçişine yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b8a77-125">Instead, you should clone the current (ambient) transaction by calling the <xref:System.Transactions.Transaction.DependentClone%2A> method on the current transaction, and pass the dependent to the worker thread.</span></span>  
  
 <span data-ttu-id="b8a77-126">`ThreadMethod` Yeni iş parçacığı üzerinde yöntemini yürütür.</span><span class="sxs-lookup"><span data-stu-id="b8a77-126">The `ThreadMethod` method executes on the new thread.</span></span> <span data-ttu-id="b8a77-127">Bir istemci, bağımlı işlem olarak geçirme yeni bir iş parçacığı çalışmaya başladığı `ThreadMethod` parametresi.</span><span class="sxs-lookup"><span data-stu-id="b8a77-127">The client starts a new thread, passing the dependent transaction as the `ThreadMethod` parameter.</span></span>  
  
 <span data-ttu-id="b8a77-128">Bağımlı işlem ile oluşturulduğundan <xref:System.Transactions.DependentCloneOption.BlockCommitUntilComplete>, işlem tüm kadar yürütülemiyor olduğunu garanti iş parçacığı ikinci gerçekleştirilen işlem çalışma tamamlandı ve <xref:System.Transactions.DependentTransaction.Complete%2A> bağımlı işlem adı verilir.</span><span class="sxs-lookup"><span data-stu-id="b8a77-128">Because the dependent transaction is created with <xref:System.Transactions.DependentCloneOption.BlockCommitUntilComplete>, you are guaranteed that the transaction cannot be committed until all of the transactional work done on the second thread is finished and <xref:System.Transactions.DependentTransaction.Complete%2A> is called on the dependent transaction.</span></span> <span data-ttu-id="b8a77-129">İstemcinin kapsam ererse anlamına gelir (Bu işlem nesnesini sonunda elden çalıştığında **kullanarak** deyimi) yeni iş parçacığı çağrıları önce <xref:System.Transactions.DependentTransaction.Complete%2A> bağımlı işleme istemci kodu engeller kadar<xref:System.Transactions.DependentTransaction.Complete%2A> bağlı olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="b8a77-129">This means that if the client's scope ends (when it tries to dispose of the transaction object at the end of the **using** statement) before the new thread calls <xref:System.Transactions.DependentTransaction.Complete%2A> on the dependent transaction, the client code blocks until <xref:System.Transactions.DependentTransaction.Complete%2A> is called on the dependent.</span></span> <span data-ttu-id="b8a77-130">Ardından işlem yapılıyor veya durduruluyor bitirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b8a77-130">Then the transaction can finish committing or aborting.</span></span>  
  
## <a name="concurrency-issues"></a><span data-ttu-id="b8a77-131">Eşzamanlılık sorunları</span><span class="sxs-lookup"><span data-stu-id="b8a77-131">Concurrency Issues</span></span>  
 <span data-ttu-id="b8a77-132">İlgili sorunlar var. kullanırken farkında olması gereken birkaç ek eşzamanlılık <xref:System.Transactions.DependentTransaction> sınıfı:</span><span class="sxs-lookup"><span data-stu-id="b8a77-132">There are a few additional concurrency issues that you need to be aware of when using the <xref:System.Transactions.DependentTransaction> class:</span></span>  
  
-   <span data-ttu-id="b8a77-133">Çalışan iş parçacığı geri işlem yapar, ancak bunu gerçekleştirmeyi üst çalışır bir <xref:System.Transactions.TransactionAbortedException> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="b8a77-133">If the worker thread rolls back the transaction but the parent tries to commit it, a <xref:System.Transactions.TransactionAbortedException> is thrown.</span></span>  
  
-   <span data-ttu-id="b8a77-134">Her iş parçacığı için yeni bir bağımlı kopya işlemde oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b8a77-134">You should create a new dependent clone for each worker thread in the transaction.</span></span> <span data-ttu-id="b8a77-135">Yalnızca biri çağırabilirsiniz çünkü aynı bağımlı kopya birden çok iş parçacığı için geçmeyin <xref:System.Transactions.DependentTransaction.Complete%2A> üzerindeki.</span><span class="sxs-lookup"><span data-stu-id="b8a77-135">Do not pass the same dependent clone to multiple threads, because only one of them can call <xref:System.Transactions.DependentTransaction.Complete%2A> on it.</span></span>  
  
-   <span data-ttu-id="b8a77-136">Yeni bir iş parçacığı çalışan iş parçacığı olarak çoğaltılır, bağımlı bir kopya bağımlı oluşturmak ve yeni bir dizi için iletmektir emin olun.</span><span class="sxs-lookup"><span data-stu-id="b8a77-136">If the worker thread spawns a new worker thread, make sure to create a dependent clone from the dependent clone and pass it to the new thread.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8a77-137">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b8a77-137">See Also</span></span>  
 <xref:System.Transactions.DependentTransaction>
