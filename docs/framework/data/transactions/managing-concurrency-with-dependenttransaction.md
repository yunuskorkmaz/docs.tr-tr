---
title: DependentTransaction ile Eşzamanlılığı Yönetme
ms.date: 03/30/2017
ms.assetid: b85a97d8-8e02-4555-95df-34c8af095148
ms.openlocfilehash: 8de7cc6257317ff7128f25968a9dcf80ae5af89d
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040423"
---
# <a name="managing-concurrency-with-dependenttransaction"></a>DependentTransaction ile Eşzamanlılığı Yönetme
<xref:System.Transactions.Transaction> Nesnesi kullanılarak oluşturulan <xref:System.Transactions.Transaction.DependentClone%2A> yöntemi. Tek amacı, bazı kod parçaları (örneğin, bir çalışan iş parçacığı) işlem üzerinde hala iş gerçekleştirirken işlem gerçekleştiremeyeceği garantisi sağlamaktır. Klonlanan işlem içinde yapılan iş tamamlandığında ve bu işleme hazırlanmaya hazırsanız, <xref:System.Transactions.DependentTransaction.Complete%2A> yöntemini kullanarak işlemin oluşturucusuna bildirimde bulunabilir. Bu nedenle, tutarlılık ve veri doğruluğunu saklayabilir.  
  
 <xref:System.Transactions.DependentTransaction> Sınıf ayrıca zaman uyumsuz görevler arasında eşzamanlılık yönetmek için kullanılabilir. Bu senaryoda, kendi görevlere bağımlı kopya çalışırken herhangi bir kod yürütmek üst devam edebilirsiniz. Diğer bir deyişle, üst öğenin yürütme bağımlı tamamlanıncaya kadar engellenmemiş.  
  
## <a name="creating-a-dependent-clone"></a>Bağımlı bir kopya oluşturma  
 Bağımlı bir işlem oluşturmak için <xref:System.Transactions.Transaction.DependentClone%2A> yöntemi çağırın ve <xref:System.Transactions.DependentCloneOption> sabit listesini parametre olarak geçirin. Bu parametre, bağımlı kopya işlemin işleme için hazırlandığını (<xref:System.Transactions.DependentTransaction.Complete%2A> yöntemini çağırarak), ana işlemde `Commit` çağrıldığında işlemin davranışını tanımlar. Bu parameTRe için şu değerler geçerlidir:  
  
- <xref:System.Transactions.DependentCloneOption.BlockCommitUntilComplete>, üst işlemin zaman aşımına uğrayana kadar ya da <xref:System.Transactions.DependentTransaction.Complete%2A> tamamlanmasını belirten tüm bağımlılar üzerinde çağrılana kadar üst işlemin işleme işlemini engelleyen bağımlı bir işlem oluşturur. Bu, istemci, bağımlı işlemler tamamlanana kadar üst işlemin işlemesini istemediğinizde yararlıdır. Üst öğe bağımlı işlemden daha önce işi tamamlarsa ve işlem üzerinde <xref:System.Transactions.CommittableTransaction.Commit%2A> çağrılarsa, işleme işlemi, işlem üzerinde ek iş yapılabileceği ve yeni kayıtlar, tüm bağımlıların oluşturulabilmesi için kullanılabilir <xref:System.Transactions.DependentTransaction.Complete%2A>çağırın. Her biri işlerini tamamladıktan hemen sonra <xref:System.Transactions.DependentTransaction.Complete%2A>çağrısı yaptıktan sonra, işlem için işleme işlemi başlar.  
  
- diğer yandan <xref:System.Transactions.DependentCloneOption.RollbackIfNotComplete>, <xref:System.Transactions.DependentTransaction.Complete%2A> çağrılmadan önce <xref:System.Transactions.CommittableTransaction.Commit%2A> üst işlem üzerinde çağrılırsa otomatik olarak iptal edilen bağımlı bir işlem oluşturur. Bu durumda, bağımlı işlemde yapılan tüm işler tek bir işlem ömrü içinde bozulmadan, hiç kimse yalnızca bir kısmını işleme şansı vermez.  
  
 <xref:System.Transactions.DependentTransaction.Complete%2A> yöntemi, uygulamanız bağımlı işlem üzerinde çalışmasını bitirdiğinde yalnızca bir kez çağrılmalıdır; Aksi takdirde, bir <xref:System.InvalidOperationException> oluşturulur. Bu çağrı çağrıldıktan sonra işlem üzerinde herhangi bir ek iş denememelidir veya bir özel durum oluşturulur.  
  
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
  
 İstemci kodu, aynı zamanda çevresel işlemi ayarlayan bir işlem kapsamı oluşturur. Ortam işlemini çalışan iş parçacığına iletmemelisiniz. Bunun yerine, geçerli (çevresel) işlemi geçerli işlem üzerinde <xref:System.Transactions.Transaction.DependentClone%2A> yöntemini çağırarak ve çalışan iş parçacığına bağımlı olarak geçirerek klonlamanız gerekir.  
  
 `ThreadMethod` Yeni iş parçacığı üzerinde yöntemini yürütür. İstemci yeni bir iş parçacığı başlatır ve bağımlı işlemi `ThreadMethod` parametresi olarak geçirerek.  
  
 Bağımlı işlem <xref:System.Transactions.DependentCloneOption.BlockCommitUntilComplete>ile oluşturulduğundan, ikinci iş parçacığında gerçekleştirilen tüm işlem işleri tamamlanana ve <xref:System.Transactions.DependentTransaction.Complete%2A> bağımlı işlem üzerinde çağrılana kadar işlemin uygulanamadığı garanti edilir. Bu, istemcinin kapsamı sona erdiğinde (`using` deyimin sonunda işlem nesnesini atmayı denediğinde), yeni iş parçacığı bağımlı işlem üzerinde <xref:System.Transactions.DependentTransaction.Complete%2A> çağrılmadan önce, istemci kodu bağımlı işlem üzerinde <xref:System.Transactions.DependentTransaction.Complete%2A> çağrılana kadar engeller. Sonra işlem işlemi bitirirebilir veya iptal edebilir.  
  
## <a name="concurrency-issues"></a>Eşzamanlılık sorunları  
 İlgili sorunlar var. kullanırken farkında olması gereken birkaç ek eşzamanlılık <xref:System.Transactions.DependentTransaction> sınıfı:  
  
- Çalışan iş parçacığı işlemi geri alıyorsa, ancak üst öğe bunu kaydetmeye çalışırsa bir <xref:System.Transactions.TransactionAbortedException> oluşturulur.  
  
- İşlemdeki her çalışan iş parçacığı için yeni bir bağımlı kopya oluşturmanız gerekir. Yalnızca biri çağırabilirsiniz çünkü aynı bağımlı kopya birden çok iş parçacığı için geçmeyin <xref:System.Transactions.DependentTransaction.Complete%2A> üzerindeki.  
  
- Yeni bir iş parçacığı çalışan iş parçacığı olarak çoğaltılır, bağımlı bir kopya bağımlı oluşturmak ve yeni bir dizi için iletmektir emin olun.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Transactions.DependentTransaction>
