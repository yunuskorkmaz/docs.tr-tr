---
title: "Hizmetler ve İşlemler"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: service contracts [WCF], designing services and transactions
ms.assetid: 864813ff-2709-4376-912d-f5c8d318c460
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f6256db06825a79b5235b92e2ed205608f04aac7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="services-and-transactions"></a>Hizmetler ve İşlemler
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)]uygulamalar bir istemci bir hareketi başlatabilir ve hizmet işlemi işlemde koordine. İstemciler bir işlem başlatır ve birkaç hizmet işlemlerini çağırma ve hizmet işlemleri kaydedilmiş veya tek bir birim olarak geri emin olun.  
  
 Hizmet sözleşmesi işlem davranış belirterek etkinleştirebilirsiniz bir <xref:System.ServiceModel.ServiceBehaviorAttribute> ve ayarı kendi <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> ve <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> istemci işlemleri gerektiren hizmet işlemleri için özellikleri. <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> Parametresi, hiçbir işlenmeyen özel durumlar varsa, yöntem yürütür işlem otomatik olarak tamamlandı olup olmadığını belirtir. [!INCLUDE[crabout](../../../includes/crabout-md.md)]Bu öznitelikler bkz [ServiceModel işlem öznitelikleri](../../../docs/framework/wcf/feature-details/servicemodel-transaction-attributes.md).  
  
 Hizmet işlemlerinde gerçekleştirilen ve veritabanı güncelleştirmelerin günlük kaydı gibi bir kaynak yöneticisi tarafından yönetilen iş istemcinin işlem bir parçasıdır.  
  
 Aşağıdaki örnek kullanımını gösteren <xref:System.ServiceModel.ServiceBehaviorAttribute> ve <xref:System.ServiceModel.OperationBehaviorAttribute> Hizmet tarafı işlem davranışını denetlemek için öznitelikler.  
  
```  
[ServiceBehavior(TransactionIsolationLevel = System.Transactions.IsolationLevel.Serializable)]  
public class CalculatorService: ICalculatorLog  
{  
    [OperationBehavior(TransactionScopeRequired = true,  
                           TransactionAutoComplete = true)]  
    public double Add(double n1, double n2)  
    {  
        recordToLog(String.Format("Added {0} to {1}", n1, n2));  
        return n1 + n2;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true,   
                               TransactionAutoComplete = true)]  
    public double Subtract(double n1, double n2)  
    {  
        recordToLog(String.Format("Subtracted {0} from {1}", n1, n2));  
        return n1 - n2;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true,   
                                       TransactionAutoComplete = true)]  
    public double Multiply(double n1, double n2)  
    {  
        recordToLog(String.Format("Multiplied {0} by {1}", n1, n2));  
        return n1 * n2;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true,   
                                       TransactionAutoComplete = true)]  
    public double Divide(double n1, double n2)  
    {  
        recordToLog(String.Format("Divided {0} by {1}", n1, n2));  
        return n1 / n2;  
    }  
  
}  
```  
  
 İşlemler etkinleştirebilir ve işlem akışı istemci yapılandırarak ve WS-AtomicTransaction protokolünü kullanmak için bağlamalar ve ayarı hizmet [ \<transactionFlow >](../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) öğesine `true`gösterildiği gibi Aşağıdaki örnek yapılandırmada.  
  
```xml  
<client>  
    <endpoint address="net.tcp://localhost/ServiceModelSamples/service"   
          binding="netTcpBinding"   
          bindingConfiguration="netTcpBindingWSAT"   
          contract="Microsoft.ServiceModel.Samples.ICalculatorLog" />  
</client>  
  
<bindings>  
    <netTcpBinding>  
        <binding name="netTcpBindingWSAT"  
                transactionFlow="true"  
                transactionProtocol="WSAtomicTransactionOctober2004" />  
     </netTcpBinding>  
</bindings>  
```  
  
 İstemciler, bir işlem oluşturarak başlayabilir bir <xref:System.Transactions.TransactionScope> ve işlem kapsamı içinde hizmet işlemlerini çağırma.  
  
```  
using (TransactionScope ts = new TransactionScope(TransactionScopeOption.RequiresNew))  
{  
    //Do work here  
    ts.Complete();  
}  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [System.ServiceModel İşlemsel Desteği](../../../docs/framework/wcf/feature-details/transactional-support-in-system-servicemodel.md)  
 [İşlem Modelleri](../../../docs/framework/wcf/feature-details/transaction-models.md)  
 [WS İşlem Akışı](../../../docs/framework/wcf/samples/ws-transaction-flow.md)
