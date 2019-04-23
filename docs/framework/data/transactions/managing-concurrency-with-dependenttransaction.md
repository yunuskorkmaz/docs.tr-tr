---
title: DependentTransaction ile Eşzamanlılığı Yönetme
ms.date: 03/30/2017
ms.assetid: b85a97d8-8e02-4555-95df-34c8af095148
ms.openlocfilehash: b06470ed76c15208f019874db8573d0ed4778d33
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59216307"
---
# <a name="managing-concurrency-with-dependenttransaction"></a>DependentTransaction ile Eşzamanlılığı Yönetme
<xref:System.Transactions.Transaction> Nesnesi kullanılarak oluşturulan <xref:System.Transactions.Transaction.DependentClone%2A> yöntemi. Tek amacı, bazı bir kod (örneğin, bir iş parçacığı) parçalarını hala iş üzerinde işlem gerçekleştirirken işlem tamamlanamaz garanti sağlamaktır. Kopyalanan işlemin içinde çalışmanın tam ve yürütülemediğinden hazır olduğunda hareket kullanarak Oluşturucusu bildirebilir <xref:System.Transactions.DependentTransaction.Complete%2A> yöntemi. Bu nedenle, tutarlılık ve veri doğruluğunu saklayabilir.  
  
 <xref:System.Transactions.DependentTransaction> Sınıf ayrıca zaman uyumsuz görevler arasında eşzamanlılık yönetmek için kullanılabilir. Bu senaryoda, kendi görevlere bağımlı kopya çalışırken herhangi bir kod yürütmek üst devam edebilirsiniz. Diğer bir deyişle, üst öğenin yürütme bağımlı tamamlanıncaya kadar engellenmemiş.  
  
## <a name="creating-a-dependent-clone"></a>Bağımlı bir kopya oluşturma  
 Bağımlı bir işlem oluşturmak için arama <xref:System.Transactions.Transaction.DependentClone%2A> yöntemi ve pass <xref:System.Transactions.DependentCloneOption> parametre olarak numaralandırması. Bu parametre işlem davranışını tanımlar `Commit` üst işlem yürütme işlemi için hazır olduğunu bağımlı kopya gösterir önce çağrılır (çağırarak <xref:System.Transactions.DependentTransaction.Complete%2A> yöntemi). Bu parameTRe için şu değerler geçerlidir:  
  
-   <xref:System.Transactions.DependentCloneOption.BlockCommitUntilComplete> üst işlem süreleri kadar üst hareketin kaydetme işlemi aşımına veya kadar engeller bağımlı bir işlem oluşturur <xref:System.Transactions.DependentTransaction.Complete%2A> kendi tamamlama belirten tüm bağımlılıklar üzerinde çağrılır. İstemci bağımlı işlemleri tamamlanana kadar tamamlamaya üst işlem istemediği gerektiğinde kullanışlıdır. Üst çalışmasını bağımlı işlem ve çağrıları'den önceki bitirildikten <xref:System.Transactions.CommittableTransaction.Commit%2A> hareket üzerindeki kaydetme işlemi burada ek iş üzerinde işlem yapılabilir ve yeni liste oluşturulabilir, tüm kadar bir durumda engellendi Bağımlılıklar arama <xref:System.Transactions.DependentTransaction.Complete%2A>. Bunların tümünü çalışma ve araması bitirdikten hemen sonra <xref:System.Transactions.DependentTransaction.Complete%2A>, hareketin kaydetme işlemi başlar.  
  
-   <xref:System.Transactions.DependentCloneOption.RollbackIfNotComplete>, diğer yandan, yoksa otomatik olarak durdurur bağımlı bir işlem oluşturur <xref:System.Transactions.CommittableTransaction.Commit%2A> önce üst işlem çağrılır <xref:System.Transactions.DependentTransaction.Complete%2A> çağrılır. Bu durumda, bağımlı işlemde tüm çalışmanın bir işlem yaşam süresi içinde olduğu ve hiç kimse yalnızca bir bölümü yürütme şansına sahip olamaz.  
  
 <xref:System.Transactions.DependentTransaction.Complete%2A> Yöntemi yalnızca uygulamanızın bağımlı hareketi; çalışmasını bittiğinde sonra çağrılmalıdır Aksi halde, bir <xref:System.InvalidOperationException> oluşturulur. Bu çağrı çağrıldıktan sonra işlem üzerinde herhangi bir ek çalışmayı kullanmamanız gerekir veya bir özel durum oluşturulur.  
  
 Aşağıdaki kod örneğinde bağımlı bir işlem kopyalamayı ve bir iş parçacığı geçirerek tarafından iki eşzamanlı görevlerini yönetmek için bağımlı bir işlem nasıl oluşturulacağını gösterir.  
  
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
  
 Ayrıca ortam işlem ayarlar bir işlem kapsamı istemci kodu oluşturur. Ortam işlem için iş parçacığı geçirmeniz değil. Bunun yerine, çağırarak geçerli (ortam) işlem klonlayın <xref:System.Transactions.Transaction.DependentClone%2A> geçerli işlem ve iş parçacığı bağımlı geçişine yöntemi.  
  
 `ThreadMethod` Yeni iş parçacığı üzerinde yöntemini yürütür. Bağımlı işlem olarak geçirerek yeni bir iş parçacığı istemci başlatır `ThreadMethod` parametresi.  
  
 Bağımlı işlem ile oluşturulduğundan <xref:System.Transactions.DependentCloneOption.BlockCommitUntilComplete>, işlem kadar tüm yürütülemiyor olmasını garanti iş parçacığı tamamlandıktan ikinci işlem çalışmanın ve <xref:System.Transactions.DependentTransaction.Complete%2A> bağımlı işlem çağrılır. Bunun anlamı istemcinin kapsam sona ererse (olduğunda çalışır sonunda işlem nesnenin silmek **kullanarak** bildirimi) yeni dizi çağrıları önce <xref:System.Transactions.DependentTransaction.Complete%2A> bağımlı işlem, istemci kodu kadarengeller<xref:System.Transactions.DependentTransaction.Complete%2A> bağlıdır çağrılır. Ardından işlem Sistemi'ne veya iptal ediliyor tamamlayabilir.  
  
## <a name="concurrency-issues"></a>Eşzamanlılık sorunları  
 İlgili sorunlar var. kullanırken farkında olması gereken birkaç ek eşzamanlılık <xref:System.Transactions.DependentTransaction> sınıfı:  
  
-   Çalışan iş parçacığı geri işlem yapar, ancak üst, tamamlamaya çalışır bir <xref:System.Transactions.TransactionAbortedException> oluşturulur.  
  
-   İşlem sırasında her iş parçacığı için yeni bir bağımlı kopya oluşturmanız gerekir. Yalnızca biri çağırabilirsiniz çünkü aynı bağımlı kopya birden çok iş parçacığı için geçmeyin <xref:System.Transactions.DependentTransaction.Complete%2A> üzerindeki.  
  
-   Yeni bir iş parçacığı çalışan iş parçacığı olarak çoğaltılır, bağımlı bir kopya bağımlı oluşturmak ve yeni bir dizi için iletmektir emin olun.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Transactions.DependentTransaction>
