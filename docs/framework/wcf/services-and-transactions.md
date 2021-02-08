---
description: 'Hakkında daha fazla bilgi edinin: hizmetler ve Işlemler'
title: Hizmetler ve İşlemler
ms.date: 03/30/2017
helpviewer_keywords:
- service contracts [WCF], designing services and transactions
ms.assetid: 864813ff-2709-4376-912d-f5c8d318c460
ms.openlocfilehash: 4126ca139bd2097aeaaff756de694d0ff0061b5d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792979"
---
# <a name="services-and-transactions"></a>Hizmetler ve İşlemler

Windows Communication Foundation (WCF) uygulamaları, istemci içinden bir işlem başlatabilir ve işlemi hizmet işlemi içinde koordine edebilir. İstemciler bir işlem başlatabilir ve çeşitli hizmet işlemlerini çağırabilir ve hizmet işlemlerinin tek bir birim olarak yapıldığından ya da geri alındığından emin olabilir.  
  
 Hizmet sözleşmesindeki işlem davranışını, bir belirterek <xref:System.ServiceModel.ServiceBehaviorAttribute> ve <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> istemci işlemleri gerektiren hizmet işlemleri için ve özelliklerini ayarlayarak etkinleştirebilirsiniz. <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A>Parametresi, işlenmeyen özel durumlar oluşursa yöntemin yürütme işleminin otomatik olarak tamamlanıp tamamlanmadığını belirtir. Bu öznitelikler hakkında daha fazla bilgi için bkz. [ServiceModel Işlem öznitelikleri](./feature-details/servicemodel-transaction-attributes.md).  
  
 Hizmet işlemlerinde gerçekleştirilen ve veritabanı güncelleştirmelerini günlüğe kaydetme gibi bir kaynak yöneticisi tarafından yönetilen iş, istemci işleminin bir parçasıdır.  
  
 Aşağıdaki örnek, <xref:System.ServiceModel.ServiceBehaviorAttribute> <xref:System.ServiceModel.OperationBehaviorAttribute> hizmet tarafı işlem davranışını denetlemek için ve özniteliklerinin kullanımını gösterir.  
  
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
  
 [\<transactionFlow>](../configure-apps/file-schema/wcf/transactionflow.md) `true` Aşağıdaki örnek yapılandırmada gösterildiği gibi, istemci ve hizmet bağlamalarını WS-AtomicTransaction protokolünü kullanacak şekilde yapılandırarak ve öğesini öğesine ayarlayarak işlemleri ve işlem akışını etkinleştirebilirsiniz.  
  
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
  
 İstemciler işlem <xref:System.Transactions.TransactionScope> kapsamında bir hizmet işlemleri oluşturarak ve çağırarak bir işlem başlatabilir.  
  
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
