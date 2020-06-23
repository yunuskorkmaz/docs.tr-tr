---
title: DependentTransaction ile Eşzamanlılığı Yönetme
description: .NET 'teki DependentTransaction sınıfını kullanarak zaman uyumsuz görevler de dahil olmak üzere işlem Eşzamanlılığını yönetin.
ms.date: 03/30/2017
ms.assetid: b85a97d8-8e02-4555-95df-34c8af095148
ms.openlocfilehash: 9c825c977419718c8b9870b40699c4d3516e8533
ms.sourcegitcommit: 6219b1e1feccb16d88656444210fed3297f5611e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/22/2020
ms.locfileid: "85141894"
---
# <a name="managing-concurrency-with-dependenttransaction"></a><span data-ttu-id="d576a-103">DependentTransaction ile Eşzamanlılığı Yönetme</span><span class="sxs-lookup"><span data-stu-id="d576a-103">Managing Concurrency with DependentTransaction</span></span>
<span data-ttu-id="d576a-104"><xref:System.Transactions.Transaction> Nesnesi kullanılarak oluşturulan <xref:System.Transactions.Transaction.DependentClone%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d576a-104">The <xref:System.Transactions.Transaction> object is created using the <xref:System.Transactions.Transaction.DependentClone%2A> method.</span></span> <span data-ttu-id="d576a-105">Tek amacı, bazı kod parçaları (örneğin, bir çalışan iş parçacığı) işlem üzerinde hala iş gerçekleştirirken işlem gerçekleştiremeyeceği garantisi sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="d576a-105">Its sole purpose is to guarantee that the transaction cannot commit while some other pieces of code (for example, a worker thread) are still performing work on the transaction.</span></span> <span data-ttu-id="d576a-106">Klonlanan işlem içinde yapılan iş tamamlandığında ve bu işleme hazırlanmaya hazırsanız, yöntemini kullanarak işlemin oluşturucusuna bildirimde bulunabilir <xref:System.Transactions.DependentTransaction.Complete%2A> .</span><span class="sxs-lookup"><span data-stu-id="d576a-106">When the work done within the cloned transaction is complete and ready to be committed, it can notify the creator of the transaction using the <xref:System.Transactions.DependentTransaction.Complete%2A> method.</span></span> <span data-ttu-id="d576a-107">Bu nedenle, tutarlılık ve veri doğruluğunu saklayabilir.</span><span class="sxs-lookup"><span data-stu-id="d576a-107">Thus, you can preserve the consistency and correctness of data.</span></span>  
  
 <span data-ttu-id="d576a-108"><xref:System.Transactions.DependentTransaction> Sınıf ayrıca zaman uyumsuz görevler arasında eşzamanlılık yönetmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d576a-108">The <xref:System.Transactions.DependentTransaction> class can also be used to manage concurrency between asynchronous tasks.</span></span> <span data-ttu-id="d576a-109">Bu senaryoda, kendi görevlere bağımlı kopya çalışırken herhangi bir kod yürütmek üst devam edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d576a-109">In this scenario, the parent can continue to execute any code while the dependent clone works on its own tasks.</span></span> <span data-ttu-id="d576a-110">Diğer bir deyişle, üst öğenin yürütme bağımlı tamamlanıncaya kadar engellenmemiş.</span><span class="sxs-lookup"><span data-stu-id="d576a-110">In other words, the parent's execution is not blocked until the dependent completes.</span></span>  
  
## <a name="creating-a-dependent-clone"></a><span data-ttu-id="d576a-111">Bağımlı bir kopya oluşturma</span><span class="sxs-lookup"><span data-stu-id="d576a-111">Creating a Dependent Clone</span></span>  
 <span data-ttu-id="d576a-112">Bağımlı bir işlem oluşturmak için, yöntemini çağırın <xref:System.Transactions.Transaction.DependentClone%2A> ve <xref:System.Transactions.DependentCloneOption> sabit listesini parametre olarak geçirin.</span><span class="sxs-lookup"><span data-stu-id="d576a-112">To create a dependent transaction, call the <xref:System.Transactions.Transaction.DependentClone%2A> method and pass the <xref:System.Transactions.DependentCloneOption> enumeration as a parameter.</span></span> <span data-ttu-id="d576a-113">Bu parametre, `Commit` bağımlı kopya işlemin işleme için hazırlandığını (yöntemi çağırarak) işaret etmeden önce üst işlem üzerinde çağrılırsa işlemin davranışını tanımlar <xref:System.Transactions.DependentTransaction.Complete%2A> .</span><span class="sxs-lookup"><span data-stu-id="d576a-113">This parameter defines the behavior of the transaction if `Commit` is called on the parent transaction before the dependent clone indicates that it is ready for the transaction to commit (by calling the <xref:System.Transactions.DependentTransaction.Complete%2A> method).</span></span> <span data-ttu-id="d576a-114">Bu parameTRe için şu değerler geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="d576a-114">The following values are valid for this parameter:</span></span>  
  
- <span data-ttu-id="d576a-115"><xref:System.Transactions.DependentCloneOption.BlockCommitUntilComplete>üst işlemin zaman aşımına uğrayana işlemin işleme işlemini engelleyen bağımlı bir işlem oluşturur veya <xref:System.Transactions.DependentTransaction.Complete%2A> Tüm bağımlıların tamamlanmasını belirten tüm bağımlılara çağırılır.</span><span class="sxs-lookup"><span data-stu-id="d576a-115"><xref:System.Transactions.DependentCloneOption.BlockCommitUntilComplete> creates a dependent transaction that blocks the commit process of the parent transaction until the parent transaction times out, or until <xref:System.Transactions.DependentTransaction.Complete%2A> is called on all dependents indicating their completion.</span></span> <span data-ttu-id="d576a-116">Bu, istemci, bağımlı işlemler tamamlanana kadar üst işlemin işlemesini istemediğinizde yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="d576a-116">This is useful when the client does not want the parent transaction to commit until the dependent transactions have completed.</span></span> <span data-ttu-id="d576a-117">Üst öğe bağımlı işlemden ve işlem üzerindeki çağrılardan daha önceki işini <xref:System.Transactions.CommittableTransaction.Commit%2A> tamamlarsa, işleme işlemi, işlem üzerinde ek iş yapılabileceği ve tüm bağımlılar çağrılana kadar yeni kayıtlar oluşturabileceğiniz bir durumda engellenir <xref:System.Transactions.DependentTransaction.Complete%2A> .</span><span class="sxs-lookup"><span data-stu-id="d576a-117">If the parent finishes its work earlier than the dependent transaction and calls <xref:System.Transactions.CommittableTransaction.Commit%2A> on the transaction, the commit process is blocked in a state where additional work can be done on the transaction and new enlistments can be created, until all of the dependents call <xref:System.Transactions.DependentTransaction.Complete%2A>.</span></span> <span data-ttu-id="d576a-118">Bunların hepsi işlerini ve çağrısını tamamladıktan hemen sonra <xref:System.Transactions.DependentTransaction.Complete%2A> , işlem için işleme işlemi başlar.</span><span class="sxs-lookup"><span data-stu-id="d576a-118">As soon as all of them have finished their work and call <xref:System.Transactions.DependentTransaction.Complete%2A>, the commit process for the transaction begins.</span></span>  
  
- <span data-ttu-id="d576a-119"><xref:System.Transactions.DependentCloneOption.RollbackIfNotComplete>, diğer yandan, <xref:System.Transactions.CommittableTransaction.Commit%2A> çağrılmadan önce üst işlem üzerinde çağrılırsa otomatik olarak iptal edilen bağımlı bir işlem oluşturur <xref:System.Transactions.DependentTransaction.Complete%2A> .</span><span class="sxs-lookup"><span data-stu-id="d576a-119"><xref:System.Transactions.DependentCloneOption.RollbackIfNotComplete>, on the other hand, creates a dependent transaction that automatically aborts if <xref:System.Transactions.CommittableTransaction.Commit%2A> is called on the parent transaction before <xref:System.Transactions.DependentTransaction.Complete%2A> is called.</span></span> <span data-ttu-id="d576a-120">Bu durumda, bağımlı işlemde yapılan tüm işler tek bir işlem ömrü içinde bozulmadan, hiç kimse yalnızca bir kısmını işleme şansı vermez.</span><span class="sxs-lookup"><span data-stu-id="d576a-120">In this case, all the work done in the dependent transaction is intact within one transaction lifetime, and no one has a chance to commit just a portion of it.</span></span>  
  
 <span data-ttu-id="d576a-121"><xref:System.Transactions.DependentTransaction.Complete%2A>Yöntemi, uygulamanız bağımlı işlem üzerinde çalışmasını bitirdiğinde yalnızca bir kez çağrılmalıdır; Aksi takdirde, bir oluşturulur <xref:System.InvalidOperationException> .</span><span class="sxs-lookup"><span data-stu-id="d576a-121">The <xref:System.Transactions.DependentTransaction.Complete%2A> method must be called only once when your application finishes its work on the dependent transaction; otherwise, a <xref:System.InvalidOperationException> is thrown.</span></span> <span data-ttu-id="d576a-122">Bu çağrı çağrıldıktan sonra işlem üzerinde herhangi bir ek iş denememelidir veya bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="d576a-122">After this call is invoked, you must not attempt any additional work on the transaction, or an exception is thrown.</span></span>  
  
 <span data-ttu-id="d576a-123">Aşağıdaki kod örneği, bağımlı bir işlemi kopyalayarak ve bir çalışan iş parçacığına geçirerek iki eş zamanlı görevi yönetmek için bir bağımlı işlemin nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d576a-123">The following code example shows how to create a dependent transaction to manage two concurrent tasks by cloning a dependent transaction and passing it to a worker thread.</span></span>  
  
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
  
 <span data-ttu-id="d576a-124">İstemci kodu, aynı zamanda çevresel işlemi ayarlayan bir işlem kapsamı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d576a-124">The client code creates a transactional scope that also sets the ambient transaction.</span></span> <span data-ttu-id="d576a-125">Ortam işlemini çalışan iş parçacığına iletmemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="d576a-125">You should not pass the ambient transaction to the worker thread.</span></span> <span data-ttu-id="d576a-126">Bunun yerine, geçerli işlem üzerinde yöntemini çağırarak geçerli (çevresel) işlemi klonlamanız gerekir <xref:System.Transactions.Transaction.DependentClone%2A> ve bağımlı iş parçacığına geçirin.</span><span class="sxs-lookup"><span data-stu-id="d576a-126">Instead, you should clone the current (ambient) transaction by calling the <xref:System.Transactions.Transaction.DependentClone%2A> method on the current transaction, and pass the dependent to the worker thread.</span></span>  
  
 <span data-ttu-id="d576a-127">`ThreadMethod` Yeni iş parçacığı üzerinde yöntemini yürütür.</span><span class="sxs-lookup"><span data-stu-id="d576a-127">The `ThreadMethod` method executes on the new thread.</span></span> <span data-ttu-id="d576a-128">İstemci yeni bir iş parçacığı başlatır ve bağımlı işlem parametre olarak geçer `ThreadMethod` .</span><span class="sxs-lookup"><span data-stu-id="d576a-128">The client starts a new thread, passing the dependent transaction as the `ThreadMethod` parameter.</span></span>  
  
 <span data-ttu-id="d576a-129">Bağımlı işlem ile oluşturulduğundan <xref:System.Transactions.DependentCloneOption.BlockCommitUntilComplete> , ikinci iş parçacığında gerçekleştirilen tüm işlem işleri tamamlanana ve <xref:System.Transactions.DependentTransaction.Complete%2A> Bağımlı işlem üzerinde çağrılana kadar işlemin uygulanamadığı garanti edilir.</span><span class="sxs-lookup"><span data-stu-id="d576a-129">Because the dependent transaction is created with <xref:System.Transactions.DependentCloneOption.BlockCommitUntilComplete>, you are guaranteed that the transaction cannot be committed until all of the transactional work done on the second thread is finished and <xref:System.Transactions.DependentTransaction.Complete%2A> is called on the dependent transaction.</span></span> <span data-ttu-id="d576a-130">Bu, istemcinin kapsamı sona erdiğinde (deyimin sonunda işlem nesnesini atmayı denediğinde `using` ), yeni iş parçacığı <xref:System.Transactions.DependentTransaction.Complete%2A> bağımlı işlemde çağrılmadan önce, istemci kodu bağımlı işlem için çağrılana kadar engeller <xref:System.Transactions.DependentTransaction.Complete%2A> .</span><span class="sxs-lookup"><span data-stu-id="d576a-130">This means that if the client's scope ends (when it tries to dispose of the transaction object at the end of the `using` statement) before the new thread calls <xref:System.Transactions.DependentTransaction.Complete%2A> on the dependent transaction, the client code blocks until <xref:System.Transactions.DependentTransaction.Complete%2A> is called on the dependent.</span></span> <span data-ttu-id="d576a-131">Sonra işlem işlemi bitirirebilir veya iptal edebilir.</span><span class="sxs-lookup"><span data-stu-id="d576a-131">Then the transaction can finish committing or aborting.</span></span>  
  
## <a name="concurrency-issues"></a><span data-ttu-id="d576a-132">Eşzamanlılık sorunları</span><span class="sxs-lookup"><span data-stu-id="d576a-132">Concurrency Issues</span></span>  
 <span data-ttu-id="d576a-133">İlgili sorunlar var. kullanırken farkında olması gereken birkaç ek eşzamanlılık <xref:System.Transactions.DependentTransaction> sınıfı:</span><span class="sxs-lookup"><span data-stu-id="d576a-133">There are a few additional concurrency issues that you need to be aware of when using the <xref:System.Transactions.DependentTransaction> class:</span></span>  
  
- <span data-ttu-id="d576a-134">Çalışan iş parçacığı işlemi geri alıyorsa, ancak üst öğe bunu kaydetmeye çalışırsa, bir oluşturulur <xref:System.Transactions.TransactionAbortedException> .</span><span class="sxs-lookup"><span data-stu-id="d576a-134">If the worker thread rolls back the transaction but the parent tries to commit it, a <xref:System.Transactions.TransactionAbortedException> is thrown.</span></span>  
  
- <span data-ttu-id="d576a-135">İşlemdeki her çalışan iş parçacığı için yeni bir bağımlı kopya oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d576a-135">You should create a new dependent clone for each worker thread in the transaction.</span></span> <span data-ttu-id="d576a-136">Yalnızca biri çağırabilirsiniz çünkü aynı bağımlı kopya birden çok iş parçacığı için geçmeyin <xref:System.Transactions.DependentTransaction.Complete%2A> üzerindeki.</span><span class="sxs-lookup"><span data-stu-id="d576a-136">Do not pass the same dependent clone to multiple threads, because only one of them can call <xref:System.Transactions.DependentTransaction.Complete%2A> on it.</span></span>  
  
- <span data-ttu-id="d576a-137">Yeni bir iş parçacığı çalışan iş parçacığı olarak çoğaltılır, bağımlı bir kopya bağımlı oluşturmak ve yeni bir dizi için iletmektir emin olun.</span><span class="sxs-lookup"><span data-stu-id="d576a-137">If the worker thread spawns a new worker thread, make sure to create a dependent clone from the dependent clone and pass it to the new thread.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d576a-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d576a-138">See also</span></span>

- <xref:System.Transactions.DependentTransaction>
