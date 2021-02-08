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
# <a name="services-and-transactions"></a><span data-ttu-id="1f958-103">Hizmetler ve İşlemler</span><span class="sxs-lookup"><span data-stu-id="1f958-103">Services and Transactions</span></span>

<span data-ttu-id="1f958-104">Windows Communication Foundation (WCF) uygulamaları, istemci içinden bir işlem başlatabilir ve işlemi hizmet işlemi içinde koordine edebilir.</span><span class="sxs-lookup"><span data-stu-id="1f958-104">Windows Communication Foundation (WCF) applications can initiate a transaction from within a client and coordinate the transaction within the service operation.</span></span> <span data-ttu-id="1f958-105">İstemciler bir işlem başlatabilir ve çeşitli hizmet işlemlerini çağırabilir ve hizmet işlemlerinin tek bir birim olarak yapıldığından ya da geri alındığından emin olabilir.</span><span class="sxs-lookup"><span data-stu-id="1f958-105">Clients can initiate a transaction and invoke several service operations and ensure that the service operations are either committed or rolled back as a single unit.</span></span>  
  
 <span data-ttu-id="1f958-106">Hizmet sözleşmesindeki işlem davranışını, bir belirterek <xref:System.ServiceModel.ServiceBehaviorAttribute> ve <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> istemci işlemleri gerektiren hizmet işlemleri için ve özelliklerini ayarlayarak etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1f958-106">You can enable the transaction behavior in the service contract by specifying a <xref:System.ServiceModel.ServiceBehaviorAttribute> and setting its <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> and <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> properties for service operations that require client transactions.</span></span> <span data-ttu-id="1f958-107"><xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A>Parametresi, işlenmeyen özel durumlar oluşursa yöntemin yürütme işleminin otomatik olarak tamamlanıp tamamlanmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="1f958-107">The <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> parameter specifies whether the transaction in which the method executes is automatically completed if no unhandled exceptions are thrown.</span></span> <span data-ttu-id="1f958-108">Bu öznitelikler hakkında daha fazla bilgi için bkz. [ServiceModel Işlem öznitelikleri](./feature-details/servicemodel-transaction-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="1f958-108">For more information about these attributes, see [ServiceModel Transaction Attributes](./feature-details/servicemodel-transaction-attributes.md).</span></span>  
  
 <span data-ttu-id="1f958-109">Hizmet işlemlerinde gerçekleştirilen ve veritabanı güncelleştirmelerini günlüğe kaydetme gibi bir kaynak yöneticisi tarafından yönetilen iş, istemci işleminin bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="1f958-109">The work that is performed in the service operations and managed by a resource manager, such as logging database updates, is part of the client’s transaction.</span></span>  
  
 <span data-ttu-id="1f958-110">Aşağıdaki örnek, <xref:System.ServiceModel.ServiceBehaviorAttribute> <xref:System.ServiceModel.OperationBehaviorAttribute> hizmet tarafı işlem davranışını denetlemek için ve özniteliklerinin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="1f958-110">The following sample demonstrates usage of the <xref:System.ServiceModel.ServiceBehaviorAttribute> and <xref:System.ServiceModel.OperationBehaviorAttribute> attributes to control service-side transaction behavior.</span></span>  
  
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
  
 <span data-ttu-id="1f958-111">[\<transactionFlow>](../configure-apps/file-schema/wcf/transactionflow.md) `true` Aşağıdaki örnek yapılandırmada gösterildiği gibi, istemci ve hizmet bağlamalarını WS-AtomicTransaction protokolünü kullanacak şekilde yapılandırarak ve öğesini öğesine ayarlayarak işlemleri ve işlem akışını etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1f958-111">You can enable transactions and transaction flow by configuring the client and service bindings to use the WS-AtomicTransaction protocol, and setting the [\<transactionFlow>](../configure-apps/file-schema/wcf/transactionflow.md) element to `true`, as shown in the following sample configuration.</span></span>  
  
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
  
 <span data-ttu-id="1f958-112">İstemciler işlem <xref:System.Transactions.TransactionScope> kapsamında bir hizmet işlemleri oluşturarak ve çağırarak bir işlem başlatabilir.</span><span class="sxs-lookup"><span data-stu-id="1f958-112">Clients can begin a transaction by creating a <xref:System.Transactions.TransactionScope> and invoking service operations within the scope of the transaction.</span></span>  
  
```csharp
using (TransactionScope ts = new TransactionScope(TransactionScopeOption.RequiresNew))  
{  
    //Do work here  
    ts.Complete();  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="1f958-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1f958-113">See also</span></span>

- [<span data-ttu-id="1f958-114">System.ServiceModel İşlemsel Desteği</span><span class="sxs-lookup"><span data-stu-id="1f958-114">Transactional Support in System.ServiceModel</span></span>](./feature-details/transactional-support-in-system-servicemodel.md)
- [<span data-ttu-id="1f958-115">İşlem Modelleri</span><span class="sxs-lookup"><span data-stu-id="1f958-115">Transaction Models</span></span>](./feature-details/transaction-models.md)
- [<span data-ttu-id="1f958-116">WS İşlem Akışı</span><span class="sxs-lookup"><span data-stu-id="1f958-116">WS Transaction Flow</span></span>](./samples/ws-transaction-flow.md)
