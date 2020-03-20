---
title: Kurumsal Hizmetler İşlemsel Bileşenlerini Tümleştirme
ms.date: 03/30/2017
ms.assetid: 05dab277-b8b2-48cf-b40c-826be128b175
ms.openlocfilehash: 292573f911459d8a8419e09d81fd1e54dbc6c70b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184745"
---
# <a name="integrating-enterprise-services-transactional-components"></a><span data-ttu-id="d66f3-102">Kurumsal Hizmetler İşlemsel Bileşenlerini Tümleştirme</span><span class="sxs-lookup"><span data-stu-id="d66f3-102">Integrating Enterprise Services Transactional Components</span></span>

<span data-ttu-id="d66f3-103">Windows Communication Foundation (WCF), Kurumsal Hizmetlerle tümleştirme için otomatik bir mekanizma sağlar (bkz. [COM+ Uygulamaları ile Tümleştirme).](integrating-with-com-plus-applications.md)</span><span class="sxs-lookup"><span data-stu-id="d66f3-103">Windows Communication Foundation (WCF) provides an automatic mechanism for integrating with Enterprise Services (see [Integrating with COM+ Applications](integrating-with-com-plus-applications.md)).</span></span> <span data-ttu-id="d66f3-104">Ancak, kurumsal hizmetler içinde barındırılan işlem bileşenlerini dahili olarak kullanan hizmetler geliştirme esnekliği isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d66f3-104">However, you may want the flexibility to develop services that internally use transactional components hosted within Enterprise Services.</span></span> <span data-ttu-id="d66f3-105">WCF İşlemleri özelliği <xref:System.Transactions> altyapı üzerine kurulduğundan, Kurumsal Hizmetler ile WCF'yi tümleştirme işlemi, Kurumsal <xref:System.Transactions> Hizmetler [ve COM+ İşlemleriyle Birlikte Çalışabilirlik'te](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/ms229974(v=vs.85))belirtildiği gibi, Kurumsal Hizmetler ve Kurumsal Hizmetler arasında birlikte çalışabilirlik belirtmek için de aynıdır.</span><span class="sxs-lookup"><span data-stu-id="d66f3-105">Because the WCF Transactions feature is built on the <xref:System.Transactions> infrastructure, the process for integrating Enterprise Services with WCF is identical to that for specifying interoperability between <xref:System.Transactions> and Enterprise Services, as outlined in [Interoperability with Enterprise Services and COM+ Transactions](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/ms229974(v=vs.85)).</span></span>  
  
 <span data-ttu-id="d66f3-106">Gelen akışlı işlem ile COM+ bağlam hareketi arasında istenilen birlikte çalışabilirlik düzeyini sağlamak <xref:System.Transactions.TransactionScope> için, hizmet uygulamasının <xref:System.Transactions.EnterpriseServicesInteropOption> bir örnek oluşturması ve numaralandırmadan uygun değeri kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d66f3-106">To provide the desired level of interoperability between the incoming flowed transaction and the COM+ context transaction, the service implementation must create a <xref:System.Transactions.TransactionScope> instance and use the appropriate value from the <xref:System.Transactions.EnterpriseServicesInteropOption> enumeration.</span></span>  
  
## <a name="integrating-enterprise-services-with-a-service-operation"></a><span data-ttu-id="d66f3-107">Kurumsal Hizmetleri Bir Hizmet İşlemiyle Bütünleştirme</span><span class="sxs-lookup"><span data-stu-id="d66f3-107">Integrating Enterprise Services with a Service Operation</span></span>  
 <span data-ttu-id="d66f3-108">Aşağıdaki kod, İzin Verilen hareket <xref:System.Transactions.TransactionScope> akışıyla birlikte bir <xref:System.Transactions.EnterpriseServicesInteropOption.Full> işlem gösterir ve bu işlem seçeneğiyle birlikte bir işlem oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d66f3-108">The following code demonstrates an operation, with Allowed transaction flow, that creates a <xref:System.Transactions.TransactionScope> with the <xref:System.Transactions.EnterpriseServicesInteropOption.Full> option.</span></span> <span data-ttu-id="d66f3-109">Bu senaryoda aşağıdaki koşullar geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="d66f3-109">The following conditions apply in this scenario:</span></span>  
  
- <span data-ttu-id="d66f3-110">İstemci bir hareket le hareket ederse, Kurumsal Hizmetler bileşenine yapılan çağrı da dahil olmak üzere işlem bu işlem kapsamında yürütülür.</span><span class="sxs-lookup"><span data-stu-id="d66f3-110">If the client flows a transaction, the operation, including the call to the Enterprise Services component, is executed within the scope of that transaction.</span></span> <span data-ttu-id="d66f3-111">Kullanılması, <xref:System.Transactions.EnterpriseServicesInteropOption.Full> hareketin <xref:System.EnterpriseServices> bağlamla eşitlemesini sağlar, bu da ortam hareketinin <xref:System.Transactions> aynı <xref:System.EnterpriseServices> olduğu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="d66f3-111">Using <xref:System.Transactions.EnterpriseServicesInteropOption.Full> ensures that the transaction is synchronized with the <xref:System.EnterpriseServices> context, which means that the ambient transaction for <xref:System.Transactions> and the <xref:System.EnterpriseServices> is the same.</span></span>  
  
- <span data-ttu-id="d66f3-112">İstemci bir hareket akışı <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> yoksa, ayar işlem için yeni bir işlem kapsamı `true` oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d66f3-112">If the client does not flow a transaction, setting <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> to `true` creates a new transaction scope for the operation.</span></span> <span data-ttu-id="d66f3-113">Benzer şekilde, <xref:System.Transactions.EnterpriseServicesInteropOption.Full> kullanım, işlemin <xref:System.EnterpriseServices> bileşenin bağlamı içinde kullanılan hareketle aynı olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="d66f3-113">Similarly, using <xref:System.Transactions.EnterpriseServicesInteropOption.Full> ensures that the operation’s transaction is the same as the transaction used inside the <xref:System.EnterpriseServices> component's context.</span></span>  
  
 <span data-ttu-id="d66f3-114">Ek yöntem çağrıları da aynı işlemin işlem kapsamında oluşur.</span><span class="sxs-lookup"><span data-stu-id="d66f3-114">Any additional method calls also occur within the scope of the same operation’s transaction.</span></span>  
  
```csharp
[ServiceContract()]  
public interface ICustomerServiceContract  
{  
   [OperationContract]  
   [TransactionFlow(TransactionFlowOption.Allowed)]  
   void UpdateCustomerNameOperation(int customerID, string newCustomerName);  
}  
  
[ServiceBehavior(TransactionIsolationLevel = System.Transactions.IsolationLevel.Serializable)]  
public class CustomerService : ICustomerServiceContract  
{  
   [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]  
   public void UpdateCustomerNameOperation(int customerID, string newCustomerName)  
   {  
   // Create a transaction scope with full ES interop  
      using (TransactionScope ts = new TransactionScope(  
                     TransactionScopeOption.Required,  
                     new TransactionOptions(),  
                     EnterpriseServicesInteropOption.Full))  
      {  
         // Create an Enterprise Services component  
         // Call UpdateCustomer method on an Enterprise Services
         // component
  
         // Call UpdateOtherCustomerData method on an Enterprise
         // Services component
         ts.Complete();  
      }  
  
      // Do UpdateAdditionalData on an non-Enterprise Services  
      // component  
   }  
}  
```  
  
 <span data-ttu-id="d66f3-115">Bir işlemin geçerli hareketi ile işlemsel Kurumsal Hizmetler bileşenlerine yapılan aramalar arasında <xref:System.Transactions.EnterpriseServicesInteropOption.None> eşitleme gerekmiyorsa, <xref:System.Transactions.TransactionScope> örneği anında ayarlarken seçeneği kullanın.</span><span class="sxs-lookup"><span data-stu-id="d66f3-115">If no synchronization is required between an operation’s current transaction and calls to transactional Enterprise Services components, then use the <xref:System.Transactions.EnterpriseServicesInteropOption.None> option when instantiating the <xref:System.Transactions.TransactionScope> instance.</span></span>  
  
## <a name="integrating-enterprise-services-with-a-client"></a><span data-ttu-id="d66f3-116">Kurumsal Hizmetleri Bir İstemci ile Tümleştirme</span><span class="sxs-lookup"><span data-stu-id="d66f3-116">Integrating Enterprise Services with a Client</span></span>  
 <span data-ttu-id="d66f3-117">Aşağıdaki kod, <xref:System.Transactions.TransactionScope> <xref:System.Transactions.EnterpriseServicesInteropOption.Full> ayarı olan bir örneği kullanarak istemci kodunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="d66f3-117">The following code demonstrates client code using a <xref:System.Transactions.TransactionScope> instance with the <xref:System.Transactions.EnterpriseServicesInteropOption.Full> setting.</span></span> <span data-ttu-id="d66f3-118">Bu senaryoda, hareket akışını destekleyen hizmet işlemleriçağrıları, Kurumsal Hizmetler bileşenlerine yapılan çağrılarla aynı işlem kapsamında gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="d66f3-118">In this scenario, calls to service operations that support transaction flow occur within the scope of the same transaction as the calls to Enterprise Services components.</span></span>  
  
```csharp
static void Main()  
{  
    // Create a client  
    CalculatorClient client = new CalculatorClient();  
  
    // Create a transaction scope with full ES interop  
    using (TransactionScope ts = new TransactionScope(  
          TransactionScopeOption.Required,  
          new TransactionOptions(),  
          EnterpriseServicesInteropOption.Full))  
    {  
        // Call Add calculator service operation  
  
        // Create an Enterprise Services component  
  
        // Call UpdateCustomer method on an Enterprise Services
        // component
  
        ts.Complete();  
    }  
  
    // Closing the client gracefully closes the connection and
    // cleans up resources  
    client.Close();  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="d66f3-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d66f3-119">See also</span></span>

- [<span data-ttu-id="d66f3-120">COM+ Uygulamaları ile tümleştirme</span><span class="sxs-lookup"><span data-stu-id="d66f3-120">Integrating with COM+ Applications</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="d66f3-121">COM Uygulamaları ile Tümleştirme</span><span class="sxs-lookup"><span data-stu-id="d66f3-121">Integrating with COM Applications</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-applications.md)
