---
title: DependentTransaction ile Eşzamanlılığı Yönetme
ms.date: 03/30/2017
ms.assetid: b85a97d8-8e02-4555-95df-34c8af095148
ms.openlocfilehash: a8ddcab4b065c3400f9f9f7ec9ce04befdd0f29b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174387"
---
# <a name="managing-concurrency-with-dependenttransaction"></a><span data-ttu-id="37ebc-102">DependentTransaction ile Eşzamanlılığı Yönetme</span><span class="sxs-lookup"><span data-stu-id="37ebc-102">Managing Concurrency with DependentTransaction</span></span>
<span data-ttu-id="37ebc-103"><xref:System.Transactions.Transaction> Nesnesi kullanılarak oluşturulan <xref:System.Transactions.Transaction.DependentClone%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="37ebc-103">The <xref:System.Transactions.Transaction> object is created using the <xref:System.Transactions.Transaction.DependentClone%2A> method.</span></span> <span data-ttu-id="37ebc-104">Tek amacı, diğer bazı kod parçaları (örneğin, bir alt iş parçacığı) hareket üzerinde hala iş yaparken işlemin işlemez garanti etmektir.</span><span class="sxs-lookup"><span data-stu-id="37ebc-104">Its sole purpose is to guarantee that the transaction cannot commit while some other pieces of code (for example, a worker thread) are still performing work on the transaction.</span></span> <span data-ttu-id="37ebc-105">Klonlanan işlem içinde yapılan iş tamamlandığında ve taahhüt edilmeye hazır olduğunda, <xref:System.Transactions.DependentTransaction.Complete%2A> yöntemi kullanarak hareketin oluşturucusu bildirebilir.</span><span class="sxs-lookup"><span data-stu-id="37ebc-105">When the work done within the cloned transaction is complete and ready to be committed, it can notify the creator of the transaction using the <xref:System.Transactions.DependentTransaction.Complete%2A> method.</span></span> <span data-ttu-id="37ebc-106">Bu nedenle, tutarlılık ve veri doğruluğunu saklayabilir.</span><span class="sxs-lookup"><span data-stu-id="37ebc-106">Thus, you can preserve the consistency and correctness of data.</span></span>  
  
 <span data-ttu-id="37ebc-107"><xref:System.Transactions.DependentTransaction> Sınıf ayrıca zaman uyumsuz görevler arasında eşzamanlılık yönetmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="37ebc-107">The <xref:System.Transactions.DependentTransaction> class can also be used to manage concurrency between asynchronous tasks.</span></span> <span data-ttu-id="37ebc-108">Bu senaryoda, kendi görevlere bağımlı kopya çalışırken herhangi bir kod yürütmek üst devam edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="37ebc-108">In this scenario, the parent can continue to execute any code while the dependent clone works on its own tasks.</span></span> <span data-ttu-id="37ebc-109">Diğer bir deyişle, üst öğenin yürütme bağımlı tamamlanıncaya kadar engellenmemiş.</span><span class="sxs-lookup"><span data-stu-id="37ebc-109">In other words, the parent's execution is not blocked until the dependent completes.</span></span>  
  
## <a name="creating-a-dependent-clone"></a><span data-ttu-id="37ebc-110">Bağımlı bir kopya oluşturma</span><span class="sxs-lookup"><span data-stu-id="37ebc-110">Creating a Dependent Clone</span></span>  
 <span data-ttu-id="37ebc-111">Bağımlı bir hareket oluşturmak <xref:System.Transactions.Transaction.DependentClone%2A> için, yöntemi <xref:System.Transactions.DependentCloneOption> çağırın ve numaralandırmayı parametre olarak geçirin.</span><span class="sxs-lookup"><span data-stu-id="37ebc-111">To create a dependent transaction, call the <xref:System.Transactions.Transaction.DependentClone%2A> method and pass the <xref:System.Transactions.DependentCloneOption> enumeration as a parameter.</span></span> <span data-ttu-id="37ebc-112">Bu parametre, bağımlı klon işlemin `Commit` işlemeye hazır olduğunu <xref:System.Transactions.DependentTransaction.Complete%2A> (yöntemi çağırarak) önce ana hareket çağrıldığında hareketin davranışını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="37ebc-112">This parameter defines the behavior of the transaction if `Commit` is called on the parent transaction before the dependent clone indicates that it is ready for the transaction to commit (by calling the <xref:System.Transactions.DependentTransaction.Complete%2A> method).</span></span> <span data-ttu-id="37ebc-113">Bu parameTRe için şu değerler geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="37ebc-113">The following values are valid for this parameter:</span></span>  
  
- <span data-ttu-id="37ebc-114"><xref:System.Transactions.DependentCloneOption.BlockCommitUntilComplete>ana işlem zamanları bitene kadar veya tamamlanmasını gösteren tüm bağımlılara <xref:System.Transactions.DependentTransaction.Complete%2A> çağrılana kadar ana işlemin işleme işlemini engelleyen bağımlı bir işlem oluşturur.</span><span class="sxs-lookup"><span data-stu-id="37ebc-114"><xref:System.Transactions.DependentCloneOption.BlockCommitUntilComplete> creates a dependent transaction that blocks the commit process of the parent transaction until the parent transaction times out, or until <xref:System.Transactions.DependentTransaction.Complete%2A> is called on all dependents indicating their completion.</span></span> <span data-ttu-id="37ebc-115">Bu, istemci bağımlı hareketler tamamlanana kadar üst işlemin işlemesini istemediğinde yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="37ebc-115">This is useful when the client does not want the parent transaction to commit until the dependent transactions have completed.</span></span> <span data-ttu-id="37ebc-116">Üst öğe, çalışmasını bağımlı işlemden daha <xref:System.Transactions.CommittableTransaction.Commit%2A> erken bitirir ve hareketi çağırırsa, tüm bağımlılar çağırana <xref:System.Transactions.DependentTransaction.Complete%2A>kadar işlem üzerinde ek çalışmanın yapılabileceğini ve yeni askere almaların oluşturulabileceği bir durumda işleme işlemi engellenir.</span><span class="sxs-lookup"><span data-stu-id="37ebc-116">If the parent finishes its work earlier than the dependent transaction and calls <xref:System.Transactions.CommittableTransaction.Commit%2A> on the transaction, the commit process is blocked in a state where additional work can be done on the transaction and new enlistments can be created, until all of the dependents call <xref:System.Transactions.DependentTransaction.Complete%2A>.</span></span> <span data-ttu-id="37ebc-117">En kısa sürede hepsi işlerini bitmiş <xref:System.Transactions.DependentTransaction.Complete%2A>ve arama , işlem için commit süreci başlar.</span><span class="sxs-lookup"><span data-stu-id="37ebc-117">As soon as all of them have finished their work and call <xref:System.Transactions.DependentTransaction.Complete%2A>, the commit process for the transaction begins.</span></span>  
  
- <span data-ttu-id="37ebc-118"><xref:System.Transactions.DependentCloneOption.RollbackIfNotComplete>, diğer taraftan, ana hareket çağrılmadan önce <xref:System.Transactions.CommittableTransaction.Commit%2A> <xref:System.Transactions.DependentTransaction.Complete%2A> çağrıldığında otomatik olarak iptal eden bağımlı bir işlem oluşturur.</span><span class="sxs-lookup"><span data-stu-id="37ebc-118"><xref:System.Transactions.DependentCloneOption.RollbackIfNotComplete>, on the other hand, creates a dependent transaction that automatically aborts if <xref:System.Transactions.CommittableTransaction.Commit%2A> is called on the parent transaction before <xref:System.Transactions.DependentTransaction.Complete%2A> is called.</span></span> <span data-ttu-id="37ebc-119">Bu durumda, bağımlı işlemde yapılan tüm işler tek bir işlem ömrü içinde bozulmamış tır ve hiç kimsenin işlemin yalnızca bir kısmını işleme şansı yoktur.</span><span class="sxs-lookup"><span data-stu-id="37ebc-119">In this case, all the work done in the dependent transaction is intact within one transaction lifetime, and no one has a chance to commit just a portion of it.</span></span>  
  
 <span data-ttu-id="37ebc-120">Yöntem, <xref:System.Transactions.DependentTransaction.Complete%2A> uygulamanız bağımlı hareket üzerindeki çalışmasını tamamladığında yalnızca bir kez çağrılmalıdır; aksi takdirde, bir <xref:System.InvalidOperationException> atılır.</span><span class="sxs-lookup"><span data-stu-id="37ebc-120">The <xref:System.Transactions.DependentTransaction.Complete%2A> method must be called only once when your application finishes its work on the dependent transaction; otherwise, a <xref:System.InvalidOperationException> is thrown.</span></span> <span data-ttu-id="37ebc-121">Bu çağrı çağrıldıktan sonra, hareket üzerinde herhangi bir ek çalışma denememelisiniz veya bir özel durum atılır.</span><span class="sxs-lookup"><span data-stu-id="37ebc-121">After this call is invoked, you must not attempt any additional work on the transaction, or an exception is thrown.</span></span>  
  
 <span data-ttu-id="37ebc-122">Aşağıdaki kod örneği, bağımlı bir hareketi klonlayarak ve bir alt iş parçacığına geçirerek iki eşzamanlı görevi yönetmek için bağımlı bir işlemin nasıl oluşturulurunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="37ebc-122">The following code example shows how to create a dependent transaction to manage two concurrent tasks by cloning a dependent transaction and passing it to a worker thread.</span></span>  
  
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
  
 <span data-ttu-id="37ebc-123">İstemci kodu, ortam işlemini de ayarlayan bir işlem kapsamı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="37ebc-123">The client code creates a transactional scope that also sets the ambient transaction.</span></span> <span data-ttu-id="37ebc-124">Ortam işlemini alt iş parçacığına geçirmemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="37ebc-124">You should not pass the ambient transaction to the worker thread.</span></span> <span data-ttu-id="37ebc-125">Bunun yerine, geçerli hareket yöntemini çağırarak <xref:System.Transactions.Transaction.DependentClone%2A> geçerli (ortam) hareketi klonlamanız ve bağımlıyı alt iş parçacığına geçirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="37ebc-125">Instead, you should clone the current (ambient) transaction by calling the <xref:System.Transactions.Transaction.DependentClone%2A> method on the current transaction, and pass the dependent to the worker thread.</span></span>  
  
 <span data-ttu-id="37ebc-126">`ThreadMethod` Yeni iş parçacığı üzerinde yöntemini yürütür.</span><span class="sxs-lookup"><span data-stu-id="37ebc-126">The `ThreadMethod` method executes on the new thread.</span></span> <span data-ttu-id="37ebc-127">İstemci, bağımlı hareketi `ThreadMethod` parametre olarak geçirerek yeni bir iş parçacığı başlatır.</span><span class="sxs-lookup"><span data-stu-id="37ebc-127">The client starts a new thread, passing the dependent transaction as the `ThreadMethod` parameter.</span></span>  
  
 <span data-ttu-id="37ebc-128">Bağımlı hareket ile <xref:System.Transactions.DependentCloneOption.BlockCommitUntilComplete>oluşturulduğundan, ikinci iş parçacığı üzerinde yapılan tüm işlem çalışması tamamlanana ve <xref:System.Transactions.DependentTransaction.Complete%2A> bağımlı işleme çağrılıncaya kadar işlemin işlenemeyeceği garanti edilir.</span><span class="sxs-lookup"><span data-stu-id="37ebc-128">Because the dependent transaction is created with <xref:System.Transactions.DependentCloneOption.BlockCommitUntilComplete>, you are guaranteed that the transaction cannot be committed until all of the transactional work done on the second thread is finished and <xref:System.Transactions.DependentTransaction.Complete%2A> is called on the dependent transaction.</span></span> <span data-ttu-id="37ebc-129">Bu, istemcinin kapsamı sona erdiğinde `using` (ekstrenin sonundahareket nesnesini elden çıkarmaya çalıştığında) yeni <xref:System.Transactions.DependentTransaction.Complete%2A> iş parçacığı bağımlı hareketi çağırmadan önce, istemci kodu bağımlı ya da bağımlı ya da çağrılana kadar <xref:System.Transactions.DependentTransaction.Complete%2A> bloklar anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="37ebc-129">This means that if the client's scope ends (when it tries to dispose of the transaction object at the end of the `using` statement) before the new thread calls <xref:System.Transactions.DependentTransaction.Complete%2A> on the dependent transaction, the client code blocks until <xref:System.Transactions.DependentTransaction.Complete%2A> is called on the dependent.</span></span> <span data-ttu-id="37ebc-130">Daha sonra işlem taahhüt veya iptal bitirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="37ebc-130">Then the transaction can finish committing or aborting.</span></span>  
  
## <a name="concurrency-issues"></a><span data-ttu-id="37ebc-131">Eşzamanlılık sorunları</span><span class="sxs-lookup"><span data-stu-id="37ebc-131">Concurrency Issues</span></span>  
 <span data-ttu-id="37ebc-132">İlgili sorunlar var. kullanırken farkında olması gereken birkaç ek eşzamanlılık <xref:System.Transactions.DependentTransaction> sınıfı:</span><span class="sxs-lookup"><span data-stu-id="37ebc-132">There are a few additional concurrency issues that you need to be aware of when using the <xref:System.Transactions.DependentTransaction> class:</span></span>  
  
- <span data-ttu-id="37ebc-133">Alt iş parçacığı hareketi geri alır ancak üst işlem <xref:System.Transactions.TransactionAbortedException> işlemeye çalışırsa, bir atılır.</span><span class="sxs-lookup"><span data-stu-id="37ebc-133">If the worker thread rolls back the transaction but the parent tries to commit it, a <xref:System.Transactions.TransactionAbortedException> is thrown.</span></span>  
  
- <span data-ttu-id="37ebc-134">Hareketteki her alt iş parçacığı için yeni bir bağımlı klon oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="37ebc-134">You should create a new dependent clone for each worker thread in the transaction.</span></span> <span data-ttu-id="37ebc-135">Yalnızca biri çağırabilirsiniz çünkü aynı bağımlı kopya birden çok iş parçacığı için geçmeyin <xref:System.Transactions.DependentTransaction.Complete%2A> üzerindeki.</span><span class="sxs-lookup"><span data-stu-id="37ebc-135">Do not pass the same dependent clone to multiple threads, because only one of them can call <xref:System.Transactions.DependentTransaction.Complete%2A> on it.</span></span>  
  
- <span data-ttu-id="37ebc-136">Yeni bir iş parçacığı çalışan iş parçacığı olarak çoğaltılır, bağımlı bir kopya bağımlı oluşturmak ve yeni bir dizi için iletmektir emin olun.</span><span class="sxs-lookup"><span data-stu-id="37ebc-136">If the worker thread spawns a new worker thread, make sure to create a dependent clone from the dependent clone and pass it to the new thread.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37ebc-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="37ebc-137">See also</span></span>

- <xref:System.Transactions.DependentTransaction>
