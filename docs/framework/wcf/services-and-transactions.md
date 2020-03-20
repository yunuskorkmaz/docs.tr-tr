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
# <a name="services-and-transactions"></a><span data-ttu-id="69444-102">Hizmetler ve İşlemler</span><span class="sxs-lookup"><span data-stu-id="69444-102">Services and Transactions</span></span>
<span data-ttu-id="69444-103">Windows Communication Foundation (WCF) uygulamaları istemci içinden bir işlem başlatabilir ve hizmet işlemi içinde hareketi koordine edebilir.</span><span class="sxs-lookup"><span data-stu-id="69444-103">Windows Communication Foundation (WCF) applications can initiate a transaction from within a client and coordinate the transaction within the service operation.</span></span> <span data-ttu-id="69444-104">İstemciler bir işlem başlatabilir ve çeşitli hizmet işlemlerini çağırabilir ve hizmet işlemlerinin taahhüt edilmesini veya tek bir birim olarak geri aldadığından emin olabilir.</span><span class="sxs-lookup"><span data-stu-id="69444-104">Clients can initiate a transaction and invoke several service operations and ensure that the service operations are either committed or rolled back as a single unit.</span></span>  
  
 <span data-ttu-id="69444-105">Hizmet sözleşmesinde hareket davranışını, istemci hareketleri <xref:System.ServiceModel.ServiceBehaviorAttribute> gerektiren <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> hizmet <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> işlemleri için a belirterek ve onun ve özelliklerini ayarlayarak etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="69444-105">You can enable the transaction behavior in the service contract by specifying a <xref:System.ServiceModel.ServiceBehaviorAttribute> and setting its <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> and <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> properties for service operations that require client transactions.</span></span> <span data-ttu-id="69444-106">Parametre, <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> işlenmemiş özel durumlar atılmadığı nda yöntemin yürütüldettiği işlemin otomatik olarak tamamlanıp tamamlanmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="69444-106">The <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> parameter specifies whether the transaction in which the method executes is automatically completed if no unhandled exceptions are thrown.</span></span> <span data-ttu-id="69444-107">Bu öznitelikler hakkında daha fazla bilgi için [ServiceModel İşlem Öznitelikleri'ne](./feature-details/servicemodel-transaction-attributes.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="69444-107">For more information about these attributes, see [ServiceModel Transaction Attributes](./feature-details/servicemodel-transaction-attributes.md).</span></span>  
  
 <span data-ttu-id="69444-108">Hizmet işlemlerinde gerçekleştirilen ve veritabanı güncelleştirmelerini günlüğe kaydetme gibi bir kaynak yöneticisi tarafından yönetilen çalışma, istemcinin hareketinin bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="69444-108">The work that is performed in the service operations and managed by a resource manager, such as logging database updates, is part of the client’s transaction.</span></span>  
  
 <span data-ttu-id="69444-109">Aşağıdaki örnek, hizmet tarafı <xref:System.ServiceModel.ServiceBehaviorAttribute> <xref:System.ServiceModel.OperationBehaviorAttribute> hareket davranışını denetlemek için özniteliklerin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="69444-109">The following sample demonstrates usage of the <xref:System.ServiceModel.ServiceBehaviorAttribute> and <xref:System.ServiceModel.OperationBehaviorAttribute> attributes to control service-side transaction behavior.</span></span>  
  
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
  
 <span data-ttu-id="69444-110">İstemci ve hizmet bağlamalarını WS-AtomicTransaction protokolünü kullanacak şekilde yapılandırarak ve [ \<işlem Akışı>](../configure-apps/file-schema/wcf/transactionflow.md) öğesini aşağıdaki örnek yapılandırmada gösterildiği gibi `true`, olarak ayarlayarak hareketleri ve işlem akışını etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="69444-110">You can enable transactions and transaction flow by configuring the client and service bindings to use the WS-AtomicTransaction protocol, and setting the [\<transactionFlow>](../configure-apps/file-schema/wcf/transactionflow.md) element to `true`, as shown in the following sample configuration.</span></span>  
  
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
  
 <span data-ttu-id="69444-111">İstemciler, hareket kapsamında <xref:System.Transactions.TransactionScope> bir hizmet işlemleri oluşturarak ve çağırarak bir işlem başlatabilir.</span><span class="sxs-lookup"><span data-stu-id="69444-111">Clients can begin a transaction by creating a <xref:System.Transactions.TransactionScope> and invoking service operations within the scope of the transaction.</span></span>  
  
```csharp
using (TransactionScope ts = new TransactionScope(TransactionScopeOption.RequiresNew))  
{  
    //Do work here  
    ts.Complete();  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="69444-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="69444-112">See also</span></span>

- [<span data-ttu-id="69444-113">System.ServiceModel İşlemsel Desteği</span><span class="sxs-lookup"><span data-stu-id="69444-113">Transactional Support in System.ServiceModel</span></span>](./feature-details/transactional-support-in-system-servicemodel.md)
- [<span data-ttu-id="69444-114">İşlem Modelleri</span><span class="sxs-lookup"><span data-stu-id="69444-114">Transaction Models</span></span>](./feature-details/transaction-models.md)
- [<span data-ttu-id="69444-115">WS İşlem Akışı</span><span class="sxs-lookup"><span data-stu-id="69444-115">WS Transaction Flow</span></span>](./samples/ws-transaction-flow.md)
