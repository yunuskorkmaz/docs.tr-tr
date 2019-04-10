---
title: DependentTransaction ile Eşzamanlılığı Yönetme
ms.date: 03/30/2017
ms.assetid: b85a97d8-8e02-4555-95df-34c8af095148
ms.openlocfilehash: b06470ed76c15208f019874db8573d0ed4778d33
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59216307"
---
# <a name="managing-concurrency-with-dependenttransaction"></a><span data-ttu-id="d9368-102">DependentTransaction ile Eşzamanlılığı Yönetme</span><span class="sxs-lookup"><span data-stu-id="d9368-102">Managing Concurrency with DependentTransaction</span></span>
<span data-ttu-id="d9368-103"><xref:System.Transactions.Transaction> Nesnesi kullanılarak oluşturulan <xref:System.Transactions.Transaction.DependentClone%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d9368-103">The <xref:System.Transactions.Transaction> object is created using the <xref:System.Transactions.Transaction.DependentClone%2A> method.</span></span> <span data-ttu-id="d9368-104">Tek amacı, bazı bir kod (örneğin, bir iş parçacığı) parçalarını hala iş üzerinde işlem gerçekleştirirken işlem tamamlanamaz garanti sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="d9368-104">Its sole purpose is to guarantee that the transaction cannot commit while some other pieces of code (for example, a worker thread) are still performing work on the transaction.</span></span> <span data-ttu-id="d9368-105">Kopyalanan işlemin içinde çalışmanın tam ve yürütülemediğinden hazır olduğunda hareket kullanarak Oluşturucusu bildirebilir <xref:System.Transactions.DependentTransaction.Complete%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d9368-105">When the work done within the cloned transaction is complete and ready to be committed, it can notify the creator of the transaction using the <xref:System.Transactions.DependentTransaction.Complete%2A> method.</span></span> <span data-ttu-id="d9368-106">Bu nedenle, tutarlılık ve veri doğruluğunu saklayabilir.</span><span class="sxs-lookup"><span data-stu-id="d9368-106">Thus, you can preserve the consistency and correctness of data.</span></span>  
  
 <span data-ttu-id="d9368-107"><xref:System.Transactions.DependentTransaction> Sınıf ayrıca zaman uyumsuz görevler arasında eşzamanlılık yönetmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d9368-107">The <xref:System.Transactions.DependentTransaction> class can also be used to manage concurrency between asynchronous tasks.</span></span> <span data-ttu-id="d9368-108">Bu senaryoda, kendi görevlere bağımlı kopya çalışırken herhangi bir kod yürütmek üst devam edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d9368-108">In this scenario, the parent can continue to execute any code while the dependent clone works on its own tasks.</span></span> <span data-ttu-id="d9368-109">Diğer bir deyişle, üst öğenin yürütme bağımlı tamamlanıncaya kadar engellenmemiş.</span><span class="sxs-lookup"><span data-stu-id="d9368-109">In other words, the parent's execution is not blocked until the dependent completes.</span></span>  
  
## <a name="creating-a-dependent-clone"></a><span data-ttu-id="d9368-110">Bağımlı bir kopya oluşturma</span><span class="sxs-lookup"><span data-stu-id="d9368-110">Creating a Dependent Clone</span></span>  
 <span data-ttu-id="d9368-111">Bağımlı bir işlem oluşturmak için arama <xref:System.Transactions.Transaction.DependentClone%2A> yöntemi ve pass <xref:System.Transactions.DependentCloneOption> parametre olarak numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="d9368-111">To create a dependent transaction, call the <xref:System.Transactions.Transaction.DependentClone%2A> method and pass the <xref:System.Transactions.DependentCloneOption> enumeration as a parameter.</span></span> <span data-ttu-id="d9368-112">Bu parametre işlem davranışını tanımlar `Commit` üst işlem yürütme işlemi için hazır olduğunu bağımlı kopya gösterir önce çağrılır (çağırarak <xref:System.Transactions.DependentTransaction.Complete%2A> yöntemi).</span><span class="sxs-lookup"><span data-stu-id="d9368-112">This parameter defines the behavior of the transaction if `Commit` is called on the parent transaction before the dependent clone indicates that it is ready for the transaction to commit (by calling the <xref:System.Transactions.DependentTransaction.Complete%2A> method).</span></span> <span data-ttu-id="d9368-113">Bu parameTRe için şu değerler geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="d9368-113">The following values are valid for this parameter:</span></span>  
  
-   <xref:System.Transactions.DependentCloneOption.BlockCommitUntilComplete> <span data-ttu-id="d9368-114">üst işlem süreleri kadar üst hareketin kaydetme işlemi aşımına veya kadar engeller bağımlı bir işlem oluşturur <xref:System.Transactions.DependentTransaction.Complete%2A> kendi tamamlama belirten tüm bağımlılıklar üzerinde çağrılır.</span><span class="sxs-lookup"><span data-stu-id="d9368-114">creates a dependent transaction that blocks the commit process of the parent transaction until the parent transaction times out, or until <xref:System.Transactions.DependentTransaction.Complete%2A> is called on all dependents indicating their completion.</span></span> <span data-ttu-id="d9368-115">İstemci bağımlı işlemleri tamamlanana kadar tamamlamaya üst işlem istemediği gerektiğinde kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="d9368-115">This is useful when the client does not want the parent transaction to commit until the dependent transactions have completed.</span></span> <span data-ttu-id="d9368-116">Üst çalışmasını bağımlı işlem ve çağrıları'den önceki bitirildikten <xref:System.Transactions.CommittableTransaction.Commit%2A> hareket üzerindeki kaydetme işlemi burada ek iş üzerinde işlem yapılabilir ve yeni liste oluşturulabilir, tüm kadar bir durumda engellendi Bağımlılıklar arama <xref:System.Transactions.DependentTransaction.Complete%2A>.</span><span class="sxs-lookup"><span data-stu-id="d9368-116">If the parent finishes its work earlier than the dependent transaction and calls <xref:System.Transactions.CommittableTransaction.Commit%2A> on the transaction, the commit process is blocked in a state where additional work can be done on the transaction and new enlistments can be created, until all of the dependents call <xref:System.Transactions.DependentTransaction.Complete%2A>.</span></span> <span data-ttu-id="d9368-117">Bunların tümünü çalışma ve araması bitirdikten hemen sonra <xref:System.Transactions.DependentTransaction.Complete%2A>, hareketin kaydetme işlemi başlar.</span><span class="sxs-lookup"><span data-stu-id="d9368-117">As soon as all of them have finished their work and call <xref:System.Transactions.DependentTransaction.Complete%2A>, the commit process for the transaction begins.</span></span>  
  
-   <xref:System.Transactions.DependentCloneOption.RollbackIfNotComplete><span data-ttu-id="d9368-118">, diğer yandan, yoksa otomatik olarak durdurur bağımlı bir işlem oluşturur <xref:System.Transactions.CommittableTransaction.Commit%2A> önce üst işlem çağrılır <xref:System.Transactions.DependentTransaction.Complete%2A> çağrılır.</span><span class="sxs-lookup"><span data-stu-id="d9368-118">, on the other hand, creates a dependent transaction that automatically aborts if <xref:System.Transactions.CommittableTransaction.Commit%2A> is called on the parent transaction before <xref:System.Transactions.DependentTransaction.Complete%2A> is called.</span></span> <span data-ttu-id="d9368-119">Bu durumda, bağımlı işlemde tüm çalışmanın bir işlem yaşam süresi içinde olduğu ve hiç kimse yalnızca bir bölümü yürütme şansına sahip olamaz.</span><span class="sxs-lookup"><span data-stu-id="d9368-119">In this case, all the work done in the dependent transaction is intact within one transaction lifetime, and no one has a chance to commit just a portion of it.</span></span>  
  
 <span data-ttu-id="d9368-120"><xref:System.Transactions.DependentTransaction.Complete%2A> Yöntemi yalnızca uygulamanızın bağımlı hareketi; çalışmasını bittiğinde sonra çağrılmalıdır Aksi halde, bir <xref:System.InvalidOperationException> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="d9368-120">The <xref:System.Transactions.DependentTransaction.Complete%2A> method must be called only once when your application finishes its work on the dependent transaction; otherwise, a <xref:System.InvalidOperationException> is thrown.</span></span> <span data-ttu-id="d9368-121">Bu çağrı çağrıldıktan sonra işlem üzerinde herhangi bir ek çalışmayı kullanmamanız gerekir veya bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="d9368-121">After this call is invoked, you must not attempt any additional work on the transaction, or an exception is thrown.</span></span>  
  
 <span data-ttu-id="d9368-122">Aşağıdaki kod örneğinde bağımlı bir işlem kopyalamayı ve bir iş parçacığı geçirerek tarafından iki eşzamanlı görevlerini yönetmek için bağımlı bir işlem nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d9368-122">The following code example shows how to create a dependent transaction to manage two concurrent tasks by cloning a dependent transaction and passing it to a worker thread.</span></span>  
  
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
  
 <span data-ttu-id="d9368-123">Ayrıca ortam işlem ayarlar bir işlem kapsamı istemci kodu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d9368-123">The client code creates a transactional scope that also sets the ambient transaction.</span></span> <span data-ttu-id="d9368-124">Ortam işlem için iş parçacığı geçirmeniz değil.</span><span class="sxs-lookup"><span data-stu-id="d9368-124">You should not pass the ambient transaction to the worker thread.</span></span> <span data-ttu-id="d9368-125">Bunun yerine, çağırarak geçerli (ortam) işlem klonlayın <xref:System.Transactions.Transaction.DependentClone%2A> geçerli işlem ve iş parçacığı bağımlı geçişine yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d9368-125">Instead, you should clone the current (ambient) transaction by calling the <xref:System.Transactions.Transaction.DependentClone%2A> method on the current transaction, and pass the dependent to the worker thread.</span></span>  
  
 <span data-ttu-id="d9368-126">`ThreadMethod` Yeni iş parçacığı üzerinde yöntemini yürütür.</span><span class="sxs-lookup"><span data-stu-id="d9368-126">The `ThreadMethod` method executes on the new thread.</span></span> <span data-ttu-id="d9368-127">Bağımlı işlem olarak geçirerek yeni bir iş parçacığı istemci başlatır `ThreadMethod` parametresi.</span><span class="sxs-lookup"><span data-stu-id="d9368-127">The client starts a new thread, passing the dependent transaction as the `ThreadMethod` parameter.</span></span>  
  
 <span data-ttu-id="d9368-128">Bağımlı işlem ile oluşturulduğundan <xref:System.Transactions.DependentCloneOption.BlockCommitUntilComplete>, işlem kadar tüm yürütülemiyor olmasını garanti iş parçacığı tamamlandıktan ikinci işlem çalışmanın ve <xref:System.Transactions.DependentTransaction.Complete%2A> bağımlı işlem çağrılır.</span><span class="sxs-lookup"><span data-stu-id="d9368-128">Because the dependent transaction is created with <xref:System.Transactions.DependentCloneOption.BlockCommitUntilComplete>, you are guaranteed that the transaction cannot be committed until all of the transactional work done on the second thread is finished and <xref:System.Transactions.DependentTransaction.Complete%2A> is called on the dependent transaction.</span></span> <span data-ttu-id="d9368-129">Bunun anlamı istemcinin kapsam sona ererse (olduğunda çalışır sonunda işlem nesnenin silmek **kullanarak** bildirimi) yeni dizi çağrıları önce <xref:System.Transactions.DependentTransaction.Complete%2A> bağımlı işlem, istemci kodu kadarengeller<xref:System.Transactions.DependentTransaction.Complete%2A> bağlıdır çağrılır.</span><span class="sxs-lookup"><span data-stu-id="d9368-129">This means that if the client's scope ends (when it tries to dispose of the transaction object at the end of the **using** statement) before the new thread calls <xref:System.Transactions.DependentTransaction.Complete%2A> on the dependent transaction, the client code blocks until <xref:System.Transactions.DependentTransaction.Complete%2A> is called on the dependent.</span></span> <span data-ttu-id="d9368-130">Ardından işlem Sistemi'ne veya iptal ediliyor tamamlayabilir.</span><span class="sxs-lookup"><span data-stu-id="d9368-130">Then the transaction can finish committing or aborting.</span></span>  
  
## <a name="concurrency-issues"></a><span data-ttu-id="d9368-131">Eşzamanlılık sorunları</span><span class="sxs-lookup"><span data-stu-id="d9368-131">Concurrency Issues</span></span>  
 <span data-ttu-id="d9368-132">İlgili sorunlar var. kullanırken farkında olması gereken birkaç ek eşzamanlılık <xref:System.Transactions.DependentTransaction> sınıfı:</span><span class="sxs-lookup"><span data-stu-id="d9368-132">There are a few additional concurrency issues that you need to be aware of when using the <xref:System.Transactions.DependentTransaction> class:</span></span>  
  
-   <span data-ttu-id="d9368-133">Çalışan iş parçacığı geri işlem yapar, ancak üst, tamamlamaya çalışır bir <xref:System.Transactions.TransactionAbortedException> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="d9368-133">If the worker thread rolls back the transaction but the parent tries to commit it, a <xref:System.Transactions.TransactionAbortedException> is thrown.</span></span>  
  
-   <span data-ttu-id="d9368-134">İşlem sırasında her iş parçacığı için yeni bir bağımlı kopya oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d9368-134">You should create a new dependent clone for each worker thread in the transaction.</span></span> <span data-ttu-id="d9368-135">Yalnızca biri çağırabilirsiniz çünkü aynı bağımlı kopya birden çok iş parçacığı için geçmeyin <xref:System.Transactions.DependentTransaction.Complete%2A> üzerindeki.</span><span class="sxs-lookup"><span data-stu-id="d9368-135">Do not pass the same dependent clone to multiple threads, because only one of them can call <xref:System.Transactions.DependentTransaction.Complete%2A> on it.</span></span>  
  
-   <span data-ttu-id="d9368-136">Yeni bir iş parçacığı çalışan iş parçacığı olarak çoğaltılır, bağımlı bir kopya bağımlı oluşturmak ve yeni bir dizi için iletmektir emin olun.</span><span class="sxs-lookup"><span data-stu-id="d9368-136">If the worker thread spawns a new worker thread, make sure to create a dependent clone from the dependent clone and pass it to the new thread.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9368-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d9368-137">See also</span></span>

- <xref:System.Transactions.DependentTransaction>
