---
title: İşlemi geri alma
ms.date: 03/30/2017
ms.assetid: 7f377147-7529-4689-a588-608cee87fdf8
ms.openlocfilehash: 8134623248b072ec5a095ab9b10840e94a09243c
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43464129"
---
# <a name="transaction-rollback"></a>İşlemi geri alma
Bu örnek, özel bir oluşturma işlemi gösterilmektedir <xref:System.Activities.NativeActivity> , ortam erişen <xref:System.Activities.RuntimeTransactionHandle> ortam işlem almak ve açıkça geri alma.  
  
## <a name="sample-details"></a>Örnek Ayrıntıları  
 İş akışında otomatik olarak bir işlem olduğu zaman tamamlandı en dıştaki <xref:System.Activities.Statements.TransactionScope> veya <xref:System.ServiceModel.Activities.TransactedReceiveScope> tamamlar.  Geri kapsam sınırında işlenmeyen bir özel durum yayar, bir işlem örtülü olarak yapar. Ancak, açıkça bir işlem özel durum gerek kalmadan geri almak için mantıklı zaman zamanlar olabilir. Bu durumda, bu örnekteki gibi özel bir geri alma etkinlik açıkça ortam işlemi durdurmak ve isteğe bağlı bir özel durum nedeni sağlamak için kullanabilirsiniz.  
  
 `RollbackActivity` Olduğu bir <xref:System.Activities.NativeActivity> ortam almak için yürütme özelliklerine erişim gerektirdiğinden <xref:System.Activities.RuntimeTransactionHandle>. İçinde `Execute` yöntemi alır <xref:System.Activities.RuntimeTransactionHandle> ve olup olmadığını denetler `null`, etkinlik bir ortam çalıştırma işlem kullanıldığını gösterir. Daha sonra tekrar denetleme işlemin alır olmadığını `null` mevcuttur. Bir ortam olma olasılığı vardır <xref:System.Activities.RuntimeTransactionHandle> olmadan hiç olmadığı kadar çalıştırma işlemi başlatılıyor. Son olarak çağırarak işlem durdurur <xref:System.Transactions.Transaction.Rollback%2A> ve kullanıcı tarafından sağlanan bir özel durum ya da etkinliğin işlem geri alınacak bildiren genel bir özel durum belirterek.  
  
 Tanıtım iş akışı oluşan bir <xref:System.Activities.Statements.TransactionScope> gövde önce ve sonra işlem durumu yazdırır `RollbackActivity` yürütür. İşlem geri alındı olsa bile unutmayın <xref:System.Activities.Statements.TransactionScope> tamamlanana kadar yürütür ve gövde tamamlanana kadar iş akışını iptal değil. İş akışı olduğundan iptal <xref:System.Activities.Statements.TransactionScope.AbortInstanceOnTransactionFailure%2A> özelliği varsayılan olarak `true`.  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  TransactionRollback.sln çözümde yük [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.  
  
3.  Uygulamayı çalıştırmak için CTRL + F5 tuşlarına basın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Transactions\TransactionRollback`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İşlemler](../../../../docs/framework/windows-workflow-foundation/workflow-transactions.md)
