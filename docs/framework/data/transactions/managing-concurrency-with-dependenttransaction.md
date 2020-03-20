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
# <a name="managing-concurrency-with-dependenttransaction"></a>DependentTransaction ile Eşzamanlılığı Yönetme
<xref:System.Transactions.Transaction> Nesnesi kullanılarak oluşturulan <xref:System.Transactions.Transaction.DependentClone%2A> yöntemi. Tek amacı, diğer bazı kod parçaları (örneğin, bir alt iş parçacığı) hareket üzerinde hala iş yaparken işlemin işlemez garanti etmektir. Klonlanan işlem içinde yapılan iş tamamlandığında ve taahhüt edilmeye hazır olduğunda, <xref:System.Transactions.DependentTransaction.Complete%2A> yöntemi kullanarak hareketin oluşturucusu bildirebilir. Bu nedenle, tutarlılık ve veri doğruluğunu saklayabilir.  
  
 <xref:System.Transactions.DependentTransaction> Sınıf ayrıca zaman uyumsuz görevler arasında eşzamanlılık yönetmek için kullanılabilir. Bu senaryoda, kendi görevlere bağımlı kopya çalışırken herhangi bir kod yürütmek üst devam edebilirsiniz. Diğer bir deyişle, üst öğenin yürütme bağımlı tamamlanıncaya kadar engellenmemiş.  
  
## <a name="creating-a-dependent-clone"></a>Bağımlı bir kopya oluşturma  
 Bağımlı bir hareket oluşturmak <xref:System.Transactions.Transaction.DependentClone%2A> için, yöntemi <xref:System.Transactions.DependentCloneOption> çağırın ve numaralandırmayı parametre olarak geçirin. Bu parametre, bağımlı klon işlemin `Commit` işlemeye hazır olduğunu <xref:System.Transactions.DependentTransaction.Complete%2A> (yöntemi çağırarak) önce ana hareket çağrıldığında hareketin davranışını tanımlar. Bu parameTRe için şu değerler geçerlidir:  
  
- <xref:System.Transactions.DependentCloneOption.BlockCommitUntilComplete>ana işlem zamanları bitene kadar veya tamamlanmasını gösteren tüm bağımlılara <xref:System.Transactions.DependentTransaction.Complete%2A> çağrılana kadar ana işlemin işleme işlemini engelleyen bağımlı bir işlem oluşturur. Bu, istemci bağımlı hareketler tamamlanana kadar üst işlemin işlemesini istemediğinde yararlıdır. Üst öğe, çalışmasını bağımlı işlemden daha <xref:System.Transactions.CommittableTransaction.Commit%2A> erken bitirir ve hareketi çağırırsa, tüm bağımlılar çağırana <xref:System.Transactions.DependentTransaction.Complete%2A>kadar işlem üzerinde ek çalışmanın yapılabileceğini ve yeni askere almaların oluşturulabileceği bir durumda işleme işlemi engellenir. En kısa sürede hepsi işlerini bitmiş <xref:System.Transactions.DependentTransaction.Complete%2A>ve arama , işlem için commit süreci başlar.  
  
- <xref:System.Transactions.DependentCloneOption.RollbackIfNotComplete>, diğer taraftan, ana hareket çağrılmadan önce <xref:System.Transactions.CommittableTransaction.Commit%2A> <xref:System.Transactions.DependentTransaction.Complete%2A> çağrıldığında otomatik olarak iptal eden bağımlı bir işlem oluşturur. Bu durumda, bağımlı işlemde yapılan tüm işler tek bir işlem ömrü içinde bozulmamış tır ve hiç kimsenin işlemin yalnızca bir kısmını işleme şansı yoktur.  
  
 Yöntem, <xref:System.Transactions.DependentTransaction.Complete%2A> uygulamanız bağımlı hareket üzerindeki çalışmasını tamamladığında yalnızca bir kez çağrılmalıdır; aksi takdirde, bir <xref:System.InvalidOperationException> atılır. Bu çağrı çağrıldıktan sonra, hareket üzerinde herhangi bir ek çalışma denememelisiniz veya bir özel durum atılır.  
  
 Aşağıdaki kod örneği, bağımlı bir hareketi klonlayarak ve bir alt iş parçacığına geçirerek iki eşzamanlı görevi yönetmek için bağımlı bir işlemin nasıl oluşturulurunu gösterir.  
  
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
  
 İstemci kodu, ortam işlemini de ayarlayan bir işlem kapsamı oluşturur. Ortam işlemini alt iş parçacığına geçirmemelisiniz. Bunun yerine, geçerli hareket yöntemini çağırarak <xref:System.Transactions.Transaction.DependentClone%2A> geçerli (ortam) hareketi klonlamanız ve bağımlıyı alt iş parçacığına geçirmeniz gerekir.  
  
 `ThreadMethod` Yeni iş parçacığı üzerinde yöntemini yürütür. İstemci, bağımlı hareketi `ThreadMethod` parametre olarak geçirerek yeni bir iş parçacığı başlatır.  
  
 Bağımlı hareket ile <xref:System.Transactions.DependentCloneOption.BlockCommitUntilComplete>oluşturulduğundan, ikinci iş parçacığı üzerinde yapılan tüm işlem çalışması tamamlanana ve <xref:System.Transactions.DependentTransaction.Complete%2A> bağımlı işleme çağrılıncaya kadar işlemin işlenemeyeceği garanti edilir. Bu, istemcinin kapsamı sona erdiğinde `using` (ekstrenin sonundahareket nesnesini elden çıkarmaya çalıştığında) yeni <xref:System.Transactions.DependentTransaction.Complete%2A> iş parçacığı bağımlı hareketi çağırmadan önce, istemci kodu bağımlı ya da bağımlı ya da çağrılana kadar <xref:System.Transactions.DependentTransaction.Complete%2A> bloklar anlamına gelir. Daha sonra işlem taahhüt veya iptal bitirebilirsiniz.  
  
## <a name="concurrency-issues"></a>Eşzamanlılık sorunları  
 İlgili sorunlar var. kullanırken farkında olması gereken birkaç ek eşzamanlılık <xref:System.Transactions.DependentTransaction> sınıfı:  
  
- Alt iş parçacığı hareketi geri alır ancak üst işlem <xref:System.Transactions.TransactionAbortedException> işlemeye çalışırsa, bir atılır.  
  
- Hareketteki her alt iş parçacığı için yeni bir bağımlı klon oluşturmanız gerekir. Yalnızca biri çağırabilirsiniz çünkü aynı bağımlı kopya birden çok iş parçacığı için geçmeyin <xref:System.Transactions.DependentTransaction.Complete%2A> üzerindeki.  
  
- Yeni bir iş parçacığı çalışan iş parçacığı olarak çoğaltılır, bağımlı bir kopya bağımlı oluşturmak ve yeni bir dizi için iletmektir emin olun.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Transactions.DependentTransaction>
