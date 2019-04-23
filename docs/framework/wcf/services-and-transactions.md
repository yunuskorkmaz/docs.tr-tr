---
title: Hizmetler ve İşlemler
ms.date: 03/30/2017
helpviewer_keywords:
- service contracts [WCF], designing services and transactions
ms.assetid: 864813ff-2709-4376-912d-f5c8d318c460
ms.openlocfilehash: 9dfe34406bfda2c16bd2f0cd53796b2fcef07b57
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59138339"
---
# <a name="services-and-transactions"></a>Hizmetler ve İşlemler
Windows Communication Foundation (WCF) uygulamaları bir istemci bir hareketi başlatabilir ve işlem içinde hizmet işlemini koordine edin. İstemciler bir işlem başlatmak ve birkaç hizmet işlemlerini çağırma ve hizmet işlemleri kaydedilmiş veya geri tek bir birim olarak emin olun.  
  
 İşlem davranışı hizmet sözleşmesindeki belirterek etkinleştirebilirsiniz bir <xref:System.ServiceModel.ServiceBehaviorAttribute> ve ayarı kendi <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> ve <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> istemci işlemleri gerektiren hizmet işlemleri için özellikleri. <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> Parametresi, eğer işlenmeyen özel durumlar harekete yöntemi yürütür işlem otomatik olarak tamamlanıp tamamlanmadığını belirtir. Bu öznitelikler hakkında daha fazla bilgi için bkz: [ServiceModel işlem öznitelikleri](../../../docs/framework/wcf/feature-details/servicemodel-transaction-attributes.md).  
  
 Hizmet işlemleri gerçekleştirilir ve istemcinin işlemin bir parçası olan veritabanının güncelleştirmelerini günlüğe kaydetme gibi bir kaynak yöneticisi tarafından yönetilen çalışma.  
  
 Aşağıdaki örnek, kullanımını gösterir <xref:System.ServiceModel.ServiceBehaviorAttribute> ve <xref:System.ServiceModel.OperationBehaviorAttribute> Hizmet tarafı işlem davranışını denetlemek için öznitelikleri.  
  
```csharp
[ServiceBehavior(TransactionIsolationLevel = System.Transactions.IsolationLevel.Serializable)]  
public class CalculatorService: ICalculatorLog  
{  
    [OperationBehavior(TransactionScopeRequired = true,  
                           TransactionAutoComplete = true)]  
    public double Add(double n1, double n2)  
    {  
        recordToLog($"Added {n1} to {n2}");
        return n1 + n2;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true,   
                               TransactionAutoComplete = true)]  
    public double Subtract(double n1, double n2)  
    {  
        recordToLog($"Subtracted {n1} from {n2}");
        return n1 - n2;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true,   
                                       TransactionAutoComplete = true)]  
    public double Multiply(double n1, double n2)  
    {  
        recordToLog($"Multiplied {n1} by {n2}");
        return n1 * n2;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true,   
                                       TransactionAutoComplete = true)]  
    public double Divide(double n1, double n2)  
    {  
        recordToLog($"Divided {n1} by {n2}", n1, n2);
        return n1 / n2;  
    }  
  
}  
```  
  
 İşlem etkinleştirebilir ve işlem akışı istemci yapılandırarak ve hizmet bağlamaları WS-AtomicTransaction protokolünü kullanmak için ve ayarı [ \<transactionFlow >](../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) öğesine `true`gösterildiği gibi Aşağıdaki örnek yapılandırmada.  
  
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
  
 İstemciler, bir işlem oluşturarak başlayabilirsiniz bir <xref:System.Transactions.TransactionScope> ve işlemin kapsamı içinde hizmet işlemleri çağırma.  
  
```csharp
using (TransactionScope ts = new TransactionScope(TransactionScopeOption.RequiresNew))  
{  
    //Do work here  
    ts.Complete();  
}  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [System.ServiceModel İşlemsel Desteği](../../../docs/framework/wcf/feature-details/transactional-support-in-system-servicemodel.md)
- [İşlem Modelleri](../../../docs/framework/wcf/feature-details/transaction-models.md)
- [WS İşlem Akışı](../../../docs/framework/wcf/samples/ws-transaction-flow.md)
