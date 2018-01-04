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
# <a name="managing-concurrency-with-dependenttransaction"></a>Eşzamanlılık DependentTransaction ile yönetme
<xref:System.Transactions.Transaction> Nesnesi kullanılarak oluşturulan <xref:System.Transactions.Transaction.DependentClone%2A> yöntemi. Tek amacı, bazı bir kod (örneğin, bir çalışan iş parçacığı) parçalarını hala iş üzerinde işlem gerçekleştirirken işlem tamamlanamaz garanti olmaktır. Kopyalanan işlem içinde çalışmanın tam ve kabul edilebilmesi için hazır olduğunda, hareket kullanarak Oluşturucusu bildirebilir <xref:System.Transactions.DependentTransaction.Complete%2A> yöntemi. Bu nedenle, tutarlılık ve veri doğruluğunu saklayabilir.  
  
 <xref:System.Transactions.DependentTransaction> Sınıf ayrıca zaman uyumsuz görevler arasında eşzamanlılık yönetmek için kullanılabilir. Bu senaryoda, kendi görevlere bağımlı kopya çalışırken herhangi bir kod yürütmek üst devam edebilirsiniz. Diğer bir deyişle, üst öğenin yürütme bağımlı tamamlanıncaya kadar engellenmemiş.  
  
## <a name="creating-a-dependent-clone"></a>Bağımlı bir kopya oluşturma  
 Bağımlı bir işlem oluşturmak için arama <xref:System.Transactions.Transaction.DependentClone%2A> yöntemi ve geçişi <xref:System.Transactions.DependentCloneOption> bir parametre olarak numaralandırması. Bu parametre işlem davranışını tanımlar `Commit` bağımlı kopya işlemi yürütmek hazır olduğunu belirten önce üst işlem çağrılır (çağırarak <xref:System.Transactions.DependentTransaction.Complete%2A> yöntemi). Bu parameTRe için şu değerler geçerlidir:  
  
-   <xref:System.Transactions.DependentCloneOption.BlockCommitUntilComplete>üst işlem süreleri kadar üst işlemin kaydetme işlemi out veya kadar engeller bağımlı bir işlem oluşturur <xref:System.Transactions.DependentTransaction.Complete%2A> kendi tamamlama gösteren tüm bağımlıları üzerinde olarak adlandırılır. Bu, istemci bağımlı işlemleri tamamlanana kadar tamamlamaya üst işlemin istemediği durumunda faydalı olur. Üst çalışmasını çağrıları ve bağımlı işlem'den önceki bittikten varsa <xref:System.Transactions.CommittableTransaction.Commit%2A> işleme, burada ek iş üzerinde işlem yapılabilir ve yeni kayıtlar oluşturulabilir, tüm kadar bir durumda kaydetme işlemi engellendi Bağımlılıklar çağrı <xref:System.Transactions.DependentTransaction.Complete%2A>. Bunların tümünün iş ve çağrı tamamladıktan hemen sonra <xref:System.Transactions.DependentTransaction.Complete%2A>, işlem yürütme işlemi başlar.  
  
-   <xref:System.Transactions.DependentCloneOption.RollbackIfNotComplete>, diğer yandan, otomatik olarak durdurur bağımlı bir işlem oluşturur <xref:System.Transactions.CommittableTransaction.Commit%2A> önce üst işlem olarak adlandırılan <xref:System.Transactions.DependentTransaction.Complete%2A> olarak adlandırılır. Bu durumda, bağımlı işlem içinde tüm çalışmanın bir işlem ömrü içinde olduğu gibi olup hiç kimse yalnızca bir kısmını uygulamak için bir fırsat içerir.  
  
 <xref:System.Transactions.DependentTransaction.Complete%2A> Yalnızca uygulamanızı bağımlı işlem; işini tamamlandığında sonra yöntemi çağrılmalıdır Aksi halde, bir <xref:System.InvalidOperationException> oluşturulur. Bu çağrı çağrıldıktan sonra işlem üzerinde herhangi bir ek çalışmayı çalışmamalısınız ya da bir özel durum.  
  
 Aşağıdaki kod örneğinde, bağımlı işlem kopyalama ve onu bir çalışan iş parçacığı tarafından iki eş zamanlı görevleri yönetmek için bağımlı bir işlem oluşturulacağını gösterir.  
  
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
  
 İstemci kodu ayrıca ortam işlem ayarlar işlemsel bir kapsam oluşturur. Ortam işlem iş parçacığı başarılı. Çağırarak geçerli (ortam) işlem bunun yerine, kopyalamalıdır <xref:System.Transactions.Transaction.DependentClone%2A> geçerli işlem ve çalışan iş parçacığı bağımlı geçişine yöntemi.  
  
 `ThreadMethod` Yeni iş parçacığı üzerinde yöntemini yürütür. Bir istemci, bağımlı işlem olarak geçirme yeni bir iş parçacığı çalışmaya başladığı `ThreadMethod` parametresi.  
  
 Bağımlı işlem ile oluşturulduğundan <xref:System.Transactions.DependentCloneOption.BlockCommitUntilComplete>, işlem tüm kadar yürütülemiyor olduğunu garanti iş parçacığı ikinci gerçekleştirilen işlem çalışma tamamlandı ve <xref:System.Transactions.DependentTransaction.Complete%2A> bağımlı işlem adı verilir. İstemcinin kapsam ererse anlamına gelir (Bu işlem nesnesini sonunda elden çalıştığında **kullanarak** deyimi) yeni iş parçacığı çağrıları önce <xref:System.Transactions.DependentTransaction.Complete%2A> bağımlı işleme istemci kodu engeller kadar<xref:System.Transactions.DependentTransaction.Complete%2A> bağlı olarak adlandırılır. Ardından işlem yapılıyor veya durduruluyor bitirebilirsiniz.  
  
## <a name="concurrency-issues"></a>Eşzamanlılık sorunları  
 İlgili sorunlar var. kullanırken farkında olması gereken birkaç ek eşzamanlılık <xref:System.Transactions.DependentTransaction> sınıfı:  
  
-   Çalışan iş parçacığı geri işlem yapar, ancak bunu gerçekleştirmeyi üst çalışır bir <xref:System.Transactions.TransactionAbortedException> oluşturulur.  
  
-   Her iş parçacığı için yeni bir bağımlı kopya işlemde oluşturmanız gerekir. Yalnızca biri çağırabilirsiniz çünkü aynı bağımlı kopya birden çok iş parçacığı için geçmeyin <xref:System.Transactions.DependentTransaction.Complete%2A> üzerindeki.  
  
-   Yeni bir iş parçacığı çalışan iş parçacığı olarak çoğaltılır, bağımlı bir kopya bağımlı oluşturmak ve yeni bir dizi için iletmektir emin olun.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Transactions.DependentTransaction>
