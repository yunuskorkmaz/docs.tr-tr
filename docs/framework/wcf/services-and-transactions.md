---
title: Hizmetler ve İşlemler
ms.date: 03/30/2017
helpviewer_keywords:
- service contracts [WCF], designing services and transactions
ms.assetid: 864813ff-2709-4376-912d-f5c8d318c460
ms.openlocfilehash: 5078e12ed5c68556a1d1d04d01c90440b57c1407
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54736409"
---
# <a name="services-and-transactions"></a><span data-ttu-id="6929e-102">Hizmetler ve İşlemler</span><span class="sxs-lookup"><span data-stu-id="6929e-102">Services and Transactions</span></span>
<span data-ttu-id="6929e-103">Windows Communication Foundation (WCF) uygulamaları bir istemci bir hareketi başlatabilir ve işlem içinde hizmet işlemini koordine edin.</span><span class="sxs-lookup"><span data-stu-id="6929e-103">Windows Communication Foundation (WCF) applications can initiate a transaction from within a client and coordinate the transaction within the service operation.</span></span> <span data-ttu-id="6929e-104">İstemciler bir işlem başlatmak ve birkaç hizmet işlemlerini çağırma ve hizmet işlemleri kaydedilmiş veya geri tek bir birim olarak emin olun.</span><span class="sxs-lookup"><span data-stu-id="6929e-104">Clients can initiate a transaction and invoke several service operations and ensure that the service operations are either committed or rolled back as a single unit.</span></span>  
  
 <span data-ttu-id="6929e-105">İşlem davranışı hizmet sözleşmesindeki belirterek etkinleştirebilirsiniz bir <xref:System.ServiceModel.ServiceBehaviorAttribute> ve ayarı kendi <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> ve <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> istemci işlemleri gerektiren hizmet işlemleri için özellikleri.</span><span class="sxs-lookup"><span data-stu-id="6929e-105">You can enable the transaction behavior in the service contract by specifying a <xref:System.ServiceModel.ServiceBehaviorAttribute> and setting its <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> and <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> properties for service operations that require client transactions.</span></span> <span data-ttu-id="6929e-106"><xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> Parametresi, eğer işlenmeyen özel durumlar harekete yöntemi yürütür işlem otomatik olarak tamamlanıp tamamlanmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6929e-106">The <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> parameter specifies whether the transaction in which the method executes is automatically completed if no unhandled exceptions are thrown.</span></span> <span data-ttu-id="6929e-107">Bu öznitelikler hakkında daha fazla bilgi için bkz: [ServiceModel işlem öznitelikleri](../../../docs/framework/wcf/feature-details/servicemodel-transaction-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="6929e-107">For more information about these attributes, see [ServiceModel Transaction Attributes](../../../docs/framework/wcf/feature-details/servicemodel-transaction-attributes.md).</span></span>  
  
 <span data-ttu-id="6929e-108">Hizmet işlemleri gerçekleştirilir ve istemcinin işlemin bir parçası olan veritabanının güncelleştirmelerini günlüğe kaydetme gibi bir kaynak yöneticisi tarafından yönetilen çalışma.</span><span class="sxs-lookup"><span data-stu-id="6929e-108">The work that is performed in the service operations and managed by a resource manager, such as logging database updates, is part of the client’s transaction.</span></span>  
  
 <span data-ttu-id="6929e-109">Aşağıdaki örnek, kullanımını gösterir <xref:System.ServiceModel.ServiceBehaviorAttribute> ve <xref:System.ServiceModel.OperationBehaviorAttribute> Hizmet tarafı işlem davranışını denetlemek için öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="6929e-109">The following sample demonstrates usage of the <xref:System.ServiceModel.ServiceBehaviorAttribute> and <xref:System.ServiceModel.OperationBehaviorAttribute> attributes to control service-side transaction behavior.</span></span>  
  
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
  
 <span data-ttu-id="6929e-110">İşlem etkinleştirebilir ve işlem akışı istemci yapılandırarak ve hizmet bağlamaları WS-AtomicTransaction protokolünü kullanmak için ve ayarı [ \<transactionFlow >](../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) öğesine `true`gösterildiği gibi Aşağıdaki örnek yapılandırmada.</span><span class="sxs-lookup"><span data-stu-id="6929e-110">You can enable transactions and transaction flow by configuring the client and service bindings to use the WS-AtomicTransaction protocol, and setting the [\<transactionFlow>](../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) element to `true`, as shown in the following sample configuration.</span></span>  
  
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
  
 <span data-ttu-id="6929e-111">İstemciler, bir işlem oluşturarak başlayabilirsiniz bir <xref:System.Transactions.TransactionScope> ve işlemin kapsamı içinde hizmet işlemleri çağırma.</span><span class="sxs-lookup"><span data-stu-id="6929e-111">Clients can begin a transaction by creating a <xref:System.Transactions.TransactionScope> and invoking service operations within the scope of the transaction.</span></span>  
  
```csharp
using (TransactionScope ts = new TransactionScope(TransactionScopeOption.RequiresNew))  
{  
    //Do work here  
    ts.Complete();  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="6929e-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6929e-112">See also</span></span>
- [<span data-ttu-id="6929e-113">System.ServiceModel İşlemsel Desteği</span><span class="sxs-lookup"><span data-stu-id="6929e-113">Transactional Support in System.ServiceModel</span></span>](../../../docs/framework/wcf/feature-details/transactional-support-in-system-servicemodel.md)
- [<span data-ttu-id="6929e-114">İşlem Modelleri</span><span class="sxs-lookup"><span data-stu-id="6929e-114">Transaction Models</span></span>](../../../docs/framework/wcf/feature-details/transaction-models.md)
- [<span data-ttu-id="6929e-115">WS İşlem Akışı</span><span class="sxs-lookup"><span data-stu-id="6929e-115">WS Transaction Flow</span></span>](../../../docs/framework/wcf/samples/ws-transaction-flow.md)
