---
title: "İşlemi geri alma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7f377147-7529-4689-a588-608cee87fdf8
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 654f0e46dc5ec5d40588f8571e8f31d04184bc4d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="transaction-rollback"></a>İşlemi geri alma
Bu örnek özel bir oluşturulacağını gösterir <xref:System.Activities.NativeActivity> ortam erişen <xref:System.Activities.RuntimeTransactionHandle> ortam işlem almak ve açıkça geri alma.  
  
## <a name="sample-details"></a>Örnek Ayrıntıları  
 İş akışı içinde otomatik olarak bir işlem olduğu zaman tamamlandı dıştaki <xref:System.Activities.Statements.TransactionScope> veya <xref:System.ServiceModel.Activities.TransactedReceiveScope> tamamlar.  İşlenmeyen bir özel durum kapsam sınırından geri yayar zaman örtük olarak bir işlem yapar. Ancak, ne zaman açıkça bir işlem bir özel durum gerek kalmadan geri almak için bir anlam zamanlar olabilir. Bu durumda, bu örnekteki gibi özel geri alma etkinlik açıkça ortam işlem iptal etmek ve isteğe bağlı özel durum nedeni sağlamak için kullanabilirsiniz.  
  
 `RollbackActivity` Olan bir <xref:System.Activities.NativeActivity> ortam almak için yürütme özelliklerine erişim gerektirdiği şekilde <xref:System.Activities.RuntimeTransactionHandle>. İçinde `Execute` yöntemi alır <xref:System.Activities.RuntimeTransactionHandle> ve olup olmadığını denetler `null`, etkinlik bir ortam çalıştırma işlem olmadan kullanıldığını belirtir. Daha sonra yeniden denetlemeden işlemin edinir olup olmadığını `null` mevcuttur. Bir ortam olması mümkündür <xref:System.Activities.RuntimeTransactionHandle> olmadan herhangi bir zamanda bir çalışma zamanı işlemi başlatılıyor. Son olarak çağırarak işlemi iptal <xref:System.Transactions.Transaction.Rollback%2A> ve bir kullanıcı tarafından sağlanan özel veya etkinlik işlem geri alındı durumları genel bir özel durum belirtme.  
  
 Tanıtım iş akışı oluşan bir <xref:System.Activities.Statements.TransactionScope> , gövde önce ve sonra işlem durumu yazdırır `RollbackActivity` yürütür. İşlem geri alınamaz olsa bile unutmayın <xref:System.Activities.Statements.TransactionScope> tamamlanıncaya kadar yürütür ve gövde tamamlanana kadar iş akışı iptal değil. İş akışı olduğundan iptal <xref:System.Activities.Statements.TransactionScope.AbortInstanceOnTransactionFailure%2A> özelliği varsayılan olarak `true`.  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  TransactionRollback.sln çözümde yük [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.  
  
3.  Uygulamayı çalıştırmak için CTRL + F5 tuşuna basın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Transactions\TransactionRollback`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İşlemler](../../../../docs/framework/windows-workflow-foundation/workflow-transactions.md)
