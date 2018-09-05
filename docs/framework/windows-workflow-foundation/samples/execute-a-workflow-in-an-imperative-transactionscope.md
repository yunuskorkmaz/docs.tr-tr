---
title: Kesin bir TransactionScope içinde iş akışı yürütme
ms.date: 03/30/2017
ms.assetid: bd0e8686-c1d0-4400-a541-da94ed03afc7
ms.openlocfilehash: 2744434e807664ca93b4f5bc27a1f3b89716ce87
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43520176"
---
# <a name="execute-a-workflow-in-an-imperative-transactionscope"></a>Kesin bir TransactionScope içinde iş akışı yürütme
Bu örneği kullanarak bir iş akışı yürütmeyi göstermektedir <xref:System.Activities.WorkflowInvoker> altında bir <xref:System.Transactions.Transaction> kesinlik temelli C# kodu.  
  
## <a name="sample-details"></a>Örnek Ayrıntıları  
 Kesinlik temelli C# koduna <xref:System.Transactions.TransactionScope> aynı işlem altında yürüten çalışma kümesi kapsüllemek için kullanılır. <xref:System.Transactions.TransactionScope> Çalışır bir ortam işlem oluşturma ve başlatma <xref:System.Transactions.Transaction.Current%2A> o iş parçacığı üzerinde yürütülen herhangi bir iş tarafından erişilebilen bir özellik.  
  
 İş akışında eşdeğer davranışı sağlamak için çalışma zamanı başlatma, ek iş yapması gerekir <xref:System.Transactions.Transaction.Current%2A> bir iş akışı etkinlikleri arasındaki iş parçacığı benzeşimini içermez çünkü her Etkinliği yürütmeden önce. Bu çalışma zamanı desteği ile elde edilen, bir iş akışı yürütülürken davranıştır <xref:System.Activities.WorkflowInvoker> içinde bir <xref:System.Transactions.TransactionScope>, tüm etkinlikleri tarafından oluşturulan bir ortam işlem bağlamı altında çalıştırmak için garantili <xref:System.Transactions.TransactionScope>.  
  
 Bir iş akışı, yalnızca tek bir ortam işlem için her bir iş akışı örneği olabilir; iç içe işlemler kullanılabilir değil. İş akışı içeriyor olsa bile bir <xref:System.Activities.Statements.TransactionScope> etkinliği, bu oluşturmaz yeni bir iç işlem. Bunun yerine, bu iş akışı dışında oluşturulmuş ortam işlem kullanır.  
  
 Yeni bir örnek başlar <xref:System.Transactions.TransactionScope>, işlem kimliği yazdırır ve iş akışını kullanarak başlar <xref:System.Activities.WorkflowInvoker>. İş akışı kimliği yeniden, BT'nin gösteren aynı işlem ve ardından çalışan işlem yazdırır bir <xref:System.Activities.Statements.TransactionScope>, ardından tamamlar. <xref:System.Activities.WorkflowInvoker.Invoke%2A> Çağırmak <xref:System.Activities.WorkflowInvoker> iş akışı tamamlanana kadar özgün iş parçacığını engeller. Bu nedenle zaman uyumludur. İş akışı tamamlandıktan sonra işlem tamamlanır ve kaynakları atıldı.  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], ImperativeTransactionSample.sln çözüm dosyasını açın.  
  
2.  Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.  
  
3.  Çözümü çalıştırmak için F5 tuşuna basın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Transactions\ImperativeTransaction`