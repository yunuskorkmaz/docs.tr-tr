---
title: Hizmetler ve İşlemler
ms.date: 03/30/2017
helpviewer_keywords:
- service contracts [WCF], designing services and transactions
ms.assetid: 864813ff-2709-4376-912d-f5c8d318c460
ms.openlocfilehash: 4c59b83448f5a2c448843c12dae99c442441441f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143284"
---
# <a name="services-and-transactions"></a>Hizmetler ve İşlemler
Windows Communication Foundation (WCF) uygulamaları istemci içinden bir işlem başlatabilir ve hizmet işlemi içinde hareketi koordine edebilir. İstemciler bir işlem başlatabilir ve çeşitli hizmet işlemlerini çağırabilir ve hizmet işlemlerinin taahhüt edilmesini veya tek bir birim olarak geri aldadığından emin olabilir.  
  
 Hizmet sözleşmesinde hareket davranışını, istemci hareketleri <xref:System.ServiceModel.ServiceBehaviorAttribute> gerektiren <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> hizmet <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> işlemleri için a belirterek ve onun ve özelliklerini ayarlayarak etkinleştirebilirsiniz. Parametre, <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> işlenmemiş özel durumlar atılmadığı nda yöntemin yürütüldettiği işlemin otomatik olarak tamamlanıp tamamlanmadığını belirtir. Bu öznitelikler hakkında daha fazla bilgi için [ServiceModel İşlem Öznitelikleri'ne](./feature-details/servicemodel-transaction-attributes.md)bakın.  
  
 Hizmet işlemlerinde gerçekleştirilen ve veritabanı güncelleştirmelerini günlüğe kaydetme gibi bir kaynak yöneticisi tarafından yönetilen çalışma, istemcinin hareketinin bir parçasıdır.  
  
 Aşağıdaki örnek, hizmet tarafı <xref:System.ServiceModel.ServiceBehaviorAttribute> <xref:System.ServiceModel.OperationBehaviorAttribute> hareket davranışını denetlemek için özniteliklerin kullanımını gösterir.  
  
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
  
 İstemci ve hizmet bağlamalarını WS-AtomicTransaction protokolünü kullanacak şekilde yapılandırarak ve [ \<işlem Akışı>](../configure-apps/file-schema/wcf/transactionflow.md) öğesini aşağıdaki örnek yapılandırmada gösterildiği gibi `true`, olarak ayarlayarak hareketleri ve işlem akışını etkinleştirebilirsiniz.  
  
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
  
 İstemciler, hareket kapsamında <xref:System.Transactions.TransactionScope> bir hizmet işlemleri oluşturarak ve çağırarak bir işlem başlatabilir.  
  
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
