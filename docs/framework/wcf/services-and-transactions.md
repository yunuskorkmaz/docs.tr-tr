---
title: Hizmetler ve İşlemler
ms.date: 03/30/2017
helpviewer_keywords:
- service contracts [WCF], designing services and transactions
ms.assetid: 864813ff-2709-4376-912d-f5c8d318c460
ms.openlocfilehash: 9110198fa64e43c20e1e6ba0dcf158dddeac93a6
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321145"
---
# <a name="services-and-transactions"></a>Hizmetler ve İşlemler
Windows Communication Foundation (WCF) uygulamaları, istemci içinden bir işlem başlatabilir ve işlemi hizmet işlemi içinde koordine edebilir. İstemciler bir işlem başlatabilir ve çeşitli hizmet işlemlerini çağırabilir ve hizmet işlemlerinin tek bir birim olarak yapıldığından ya da geri alındığından emin olabilir.  
  
 @No__t-0 belirterek ve istemci işlemleri gerektiren hizmet işlemleri için <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> ve <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> özelliklerini ayarlayarak, hizmet sözleşmesindeki işlem davranışını etkinleştirebilirsiniz. @No__t-0 parametresi, işlenmeyen özel durumlar atıldıysa yöntemin yürütüldüğü işlemin otomatik olarak tamamlanıp tamamlanmadığını belirtir. Bu öznitelikler hakkında daha fazla bilgi için bkz. [ServiceModel Işlem öznitelikleri](./feature-details/servicemodel-transaction-attributes.md).  
  
 Hizmet işlemlerinde gerçekleştirilen ve veritabanı güncelleştirmelerini günlüğe kaydetme gibi bir kaynak yöneticisi tarafından yönetilen iş, istemci işleminin bir parçasıdır.  
  
 Aşağıdaki örnek, hizmet tarafı işlem davranışını denetlemek için <xref:System.ServiceModel.ServiceBehaviorAttribute> ve <xref:System.ServiceModel.OperationBehaviorAttribute> özniteliklerinin kullanımını gösterir.  
  
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
  
 İstemci ve hizmet bağlamalarını WS-AtomicTransaction protokolünü kullanacak şekilde yapılandırarak işlemleri ve işlem akışını etkinleştirebilir ve aşağıdaki örnekte gösterildiği gibi [\<transactionFlow >](../configure-apps/file-schema/wcf/transactionflow.md) öğesini `true` olarak ayarlayabilirsiniz yapılandırmada.  
  
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
  
 İstemciler bir <xref:System.Transactions.TransactionScope> oluşturarak ve işlem kapsamındaki hizmet işlemlerini çağırarak bir işlem başlatabilir.  
  
```csharp
using (TransactionScope ts = new TransactionScope(TransactionScopeOption.RequiresNew))  
{  
    //Do work here  
    ts.Complete();  
}  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [System.ServiceModel İşlemsel Desteği](./feature-details/transactional-support-in-system-servicemodel.md)
- [İşlem Modelleri](./feature-details/transaction-models.md)
- [WS İşlem Akışı](./samples/ws-transaction-flow.md)
