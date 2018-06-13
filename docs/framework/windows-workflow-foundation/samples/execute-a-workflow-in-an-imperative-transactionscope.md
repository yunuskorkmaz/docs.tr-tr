---
title: Kesinlik temelli bir hareket bir iş akışı yürütme
ms.date: 03/30/2017
ms.assetid: bd0e8686-c1d0-4400-a541-da94ed03afc7
ms.openlocfilehash: 44efc13efaa45274068fb44cc154b515bd774a35
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33516965"
---
# <a name="execute-a-workflow-in-an-imperative-transactionscope"></a>Kesinlik temelli bir hareket bir iş akışı yürütme
Bu örnek, bir iş akışını kullanarak yürütmek gösterilmiştir <xref:System.Activities.WorkflowInvoker> altında bir <xref:System.Transactions.Transaction> kesinlik temelli C# kodundan.  
  
## <a name="sample-details"></a>Örnek Ayrıntıları  
 Kesinlik temelli C# kod, <xref:System.Transactions.TransactionScope> aynı işlemde yürüten iş kümesi kapsüllemek için kullanılır. <xref:System.Transactions.TransactionScope> Bir ortam işlem oluşturma ve başlatma çalışır <xref:System.Transactions.Transaction.Current%2A> sonra o iş parçacığı üzerinde yürütülmekte olan herhangi bir iş tarafından erişilebilecek özelliği.  
  
 İş akışında eşdeğer davranışı elde etmek üzere başlatma ek işlemlerini yapmak çalışma zamanı sahip <xref:System.Transactions.Transaction.Current%2A> bir iş akışı etkinlikleri arasındaki iş parçacığı benzeşimini korumaz çünkü her etkinlik yürütmeden önce. Bu çalışma zamanı desteği ile sonuç davranışına sahip bir iş akışı yürütülürken olan <xref:System.Activities.WorkflowInvoker> içinde bir <xref:System.Transactions.TransactionScope>, tüm etkinlikleri tarafından oluşturulan ortam işlem bağlamı altında çalışmasını garanti <xref:System.Transactions.TransactionScope>.  
  
 Bir iş akışı yalnızca tek bir ortam işlem her iş akışı örneği olabilir; iç içe geçmiş işlemler kullanılabilir değil. İş akışı içeriyor olsa bile bir <xref:System.Activities.Statements.TransactionScope> etkinlik, bu oluşturmaz yeni bir iç işlemi. Bunun yerine, bu iş akışının dışında oluşturulduğu ortam işlem yeniden kullanır.  
  
 Örnek bir yeni başlayan <xref:System.Transactions.TransactionScope>, işlem kimliği yazdırır ve iş akışını kullanarak başlar <xref:System.Activities.WorkflowInvoker>. İş akışı kimliği yeniden şekilde gösteren aynı işlem, sonra çalışan işlem yazdırır bir <xref:System.Activities.Statements.TransactionScope>, ardından tamamlar. <xref:System.Activities.WorkflowInvoker.Invoke%2A> Çağırmak <xref:System.Activities.WorkflowInvoker> iş akışı tamamlanana kadar özgün iş parçacığı engeller şekilde uyumludur. İş akışı tamamlandıktan sonra işlem tamamlanmadan ve kaynakları atıldı.  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], ImperativeTransactionSample.sln çözüm dosyasını açın.  
  
2.  Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.  
  
3.  Çözümü çalıştırmak için F5 tuşuna basın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Transactions\ImperativeTransaction`