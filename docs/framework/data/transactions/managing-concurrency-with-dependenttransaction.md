---
title: DependentTransaction ile Eşzamanlılığı Yönetme
description: .NET 'teki DependentTransaction sınıfını kullanarak zaman uyumsuz görevler de dahil olmak üzere işlem Eşzamanlılığını yönetin.
ms.date: 03/30/2017
ms.assetid: b85a97d8-8e02-4555-95df-34c8af095148
ms.openlocfilehash: 1e99006c127d83892155bd81e683f5995ac517ef
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91186750"
---
# <a name="managing-concurrency-with-dependenttransaction"></a>DependentTransaction ile Eşzamanlılığı Yönetme

<xref:System.Transactions.Transaction> Nesnesi kullanılarak oluşturulan <xref:System.Transactions.Transaction.DependentClone%2A> yöntemi. Tek amacı, bazı kod parçaları (örneğin, bir çalışan iş parçacığı) işlem üzerinde hala iş gerçekleştirirken işlem gerçekleştiremeyeceği garantisi sağlamaktır. Klonlanan işlem içinde yapılan iş tamamlandığında ve bu işleme hazırlanmaya hazırsanız, yöntemini kullanarak işlemin oluşturucusuna bildirimde bulunabilir <xref:System.Transactions.DependentTransaction.Complete%2A> . Bu nedenle, tutarlılık ve veri doğruluğunu saklayabilir.  
  
 <xref:System.Transactions.DependentTransaction> Sınıf ayrıca zaman uyumsuz görevler arasında eşzamanlılık yönetmek için kullanılabilir. Bu senaryoda, kendi görevlere bağımlı kopya çalışırken herhangi bir kod yürütmek üst devam edebilirsiniz. Diğer bir deyişle, üst öğenin yürütme bağımlı tamamlanıncaya kadar engellenmemiş.  
  
## <a name="creating-a-dependent-clone"></a>Bağımlı bir kopya oluşturma  

 Bağımlı bir işlem oluşturmak için, yöntemini çağırın <xref:System.Transactions.Transaction.DependentClone%2A> ve <xref:System.Transactions.DependentCloneOption> sabit listesini parametre olarak geçirin. Bu parametre, `Commit` bağımlı kopya işlemin işleme için hazırlandığını (yöntemi çağırarak) işaret etmeden önce üst işlem üzerinde çağrılırsa işlemin davranışını tanımlar <xref:System.Transactions.DependentTransaction.Complete%2A> . Bu parameTRe için şu değerler geçerlidir:  
  
- <xref:System.Transactions.DependentCloneOption.BlockCommitUntilComplete> üst işlemin zaman aşımına uğrayana işlemin işleme işlemini engelleyen bağımlı bir işlem oluşturur veya <xref:System.Transactions.DependentTransaction.Complete%2A> Tüm bağımlıların tamamlanmasını belirten tüm bağımlılara çağırılır. Bu, istemci, bağımlı işlemler tamamlanana kadar üst işlemin işlemesini istemediğinizde yararlıdır. Üst öğe bağımlı işlemden ve işlem üzerindeki çağrılardan daha önceki işini <xref:System.Transactions.CommittableTransaction.Commit%2A> tamamlarsa, işleme işlemi, işlem üzerinde ek iş yapılabileceği ve tüm bağımlılar çağrılana kadar yeni kayıtlar oluşturabileceğiniz bir durumda engellenir <xref:System.Transactions.DependentTransaction.Complete%2A> . Bunların hepsi işlerini ve çağrısını tamamladıktan hemen sonra <xref:System.Transactions.DependentTransaction.Complete%2A> , işlem için işleme işlemi başlar.  
  
- <xref:System.Transactions.DependentCloneOption.RollbackIfNotComplete>, diğer yandan, <xref:System.Transactions.CommittableTransaction.Commit%2A> çağrılmadan önce üst işlem üzerinde çağrılırsa otomatik olarak iptal edilen bağımlı bir işlem oluşturur <xref:System.Transactions.DependentTransaction.Complete%2A> . Bu durumda, bağımlı işlemde yapılan tüm işler tek bir işlem ömrü içinde bozulmadan, hiç kimse yalnızca bir kısmını işleme şansı vermez.  
  
 <xref:System.Transactions.DependentTransaction.Complete%2A>Yöntemi, uygulamanız bağımlı işlem üzerinde çalışmasını bitirdiğinde yalnızca bir kez çağrılmalıdır; Aksi takdirde, bir oluşturulur <xref:System.InvalidOperationException> . Bu çağrı çağrıldıktan sonra işlem üzerinde herhangi bir ek iş denememelidir veya bir özel durum oluşturulur.  
  
 Aşağıdaki kod örneği, bağımlı bir işlemi kopyalayarak ve bir çalışan iş parçacığına geçirerek iki eş zamanlı görevi yönetmek için bir bağımlı işlemin nasıl oluşturulacağını gösterir.  
  
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
  
 İstemci kodu, aynı zamanda çevresel işlemi ayarlayan bir işlem kapsamı oluşturur. Ortam işlemini çalışan iş parçacığına iletmemelisiniz. Bunun yerine, geçerli işlem üzerinde yöntemini çağırarak geçerli (çevresel) işlemi klonlamanız gerekir <xref:System.Transactions.Transaction.DependentClone%2A> ve bağımlı iş parçacığına geçirin.  
  
 `ThreadMethod` Yeni iş parçacığı üzerinde yöntemini yürütür. İstemci yeni bir iş parçacığı başlatır ve bağımlı işlem parametre olarak geçer `ThreadMethod` .  
  
 Bağımlı işlem ile oluşturulduğundan <xref:System.Transactions.DependentCloneOption.BlockCommitUntilComplete> , ikinci iş parçacığında gerçekleştirilen tüm işlem işleri tamamlanana ve <xref:System.Transactions.DependentTransaction.Complete%2A> Bağımlı işlem üzerinde çağrılana kadar işlemin uygulanamadığı garanti edilir. Bu, istemcinin kapsamı sona erdiğinde (deyimin sonunda işlem nesnesini atmayı denediğinde `using` ), yeni iş parçacığı <xref:System.Transactions.DependentTransaction.Complete%2A> bağımlı işlemde çağrılmadan önce, istemci kodu bağımlı işlem için çağrılana kadar engeller <xref:System.Transactions.DependentTransaction.Complete%2A> . Sonra işlem işlemi bitirirebilir veya iptal edebilir.  
  
## <a name="concurrency-issues"></a>Eşzamanlılık sorunları  

 İlgili sorunlar var. kullanırken farkında olması gereken birkaç ek eşzamanlılık <xref:System.Transactions.DependentTransaction> sınıfı:  
  
- Çalışan iş parçacığı işlemi geri alıyorsa, ancak üst öğe bunu kaydetmeye çalışırsa, bir oluşturulur <xref:System.Transactions.TransactionAbortedException> .  
  
- İşlemdeki her çalışan iş parçacığı için yeni bir bağımlı kopya oluşturmanız gerekir. Yalnızca biri çağırabilirsiniz çünkü aynı bağımlı kopya birden çok iş parçacığı için geçmeyin <xref:System.Transactions.DependentTransaction.Complete%2A> üzerindeki.  
  
- Yeni bir iş parçacığı çalışan iş parçacığı olarak çoğaltılır, bağımlı bir kopya bağımlı oluşturmak ve yeni bir dizi için iletmektir emin olun.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Transactions.DependentTransaction>
