---
title: Kurumsal Hizmetler İşlemsel Bileşenlerini Tümleştirme
ms.date: 03/30/2017
ms.assetid: 05dab277-b8b2-48cf-b40c-826be128b175
ms.openlocfilehash: 5914f76639adc3ff569a3bfb8d6eb1db14313e76
ms.sourcegitcommit: 09b4090b78f52fd09b0e430cd4b26576f1fdf96e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2020
ms.locfileid: "76211946"
---
# <a name="integrating-enterprise-services-transactional-components"></a><span data-ttu-id="a2c6b-102">Kurumsal Hizmetler İşlemsel Bileşenlerini Tümleştirme</span><span class="sxs-lookup"><span data-stu-id="a2c6b-102">Integrating Enterprise Services Transactional Components</span></span>

<span data-ttu-id="a2c6b-103">Windows Communication Foundation (WCF), Enterprise Services ile tümleştirme için otomatik bir mekanizma sağlar (bkz. [com+ uygulamalarıyla tümleştirme](integrating-with-com-plus-applications.md)).</span><span class="sxs-lookup"><span data-stu-id="a2c6b-103">Windows Communication Foundation (WCF) provides an automatic mechanism for integrating with Enterprise Services (see [Integrating with COM+ Applications](integrating-with-com-plus-applications.md)).</span></span> <span data-ttu-id="a2c6b-104">Ancak, kurumsal hizmetlerde barındırılan işlemsel bileşenleri dahili olarak kullanan hizmetler geliştirme esnekliği de isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a2c6b-104">However, you may want the flexibility to develop services that internally use transactional components hosted within Enterprise Services.</span></span> <span data-ttu-id="a2c6b-105">WCF Işlemler özelliği <xref:System.Transactions> altyapısında oluşturulduğundan, Enterprise Services 'ı WCF ile tümleştirme işlemi, [Kurumsal Hizmetler ve com+ işlemleri Ile birlikte çalışabilirlik](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/ms229974(v=vs.85))bölümünde açıklandığı gibi, <xref:System.Transactions> ve Enterprise hizmetleri arasında birlikte çalışabilirlik belirtmeyle aynıdır.</span><span class="sxs-lookup"><span data-stu-id="a2c6b-105">Because the WCF Transactions feature is built on the <xref:System.Transactions> infrastructure, the process for integrating Enterprise Services with WCF is identical to that for specifying interoperability between <xref:System.Transactions> and Enterprise Services, as outlined in [Interoperability with Enterprise Services and COM+ Transactions](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/ms229974(v=vs.85)).</span></span>  
  
 <span data-ttu-id="a2c6b-106">Gelen akışlı işlem ve COM+ bağlam işlemi arasında istediğiniz birlikte çalışabilirlik düzeyini sağlamak için, hizmet uygulamasının bir <xref:System.Transactions.TransactionScope> örneği oluşturması ve <xref:System.Transactions.EnterpriseServicesInteropOption> numaralandırmasından uygun değeri kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a2c6b-106">To provide the desired level of interoperability between the incoming flowed transaction and the COM+ context transaction, the service implementation must create a <xref:System.Transactions.TransactionScope> instance and use the appropriate value from the <xref:System.Transactions.EnterpriseServicesInteropOption> enumeration.</span></span>  
  
## <a name="integrating-enterprise-services-with-a-service-operation"></a><span data-ttu-id="a2c6b-107">Kurumsal Hizmetleri bir hizmet Işlemi ile tümleştirme</span><span class="sxs-lookup"><span data-stu-id="a2c6b-107">Integrating Enterprise Services with a Service Operation</span></span>  
 <span data-ttu-id="a2c6b-108">Aşağıdaki kod, <xref:System.Transactions.EnterpriseServicesInteropOption.Full> seçeneğiyle bir <xref:System.Transactions.TransactionScope> oluşturan, Izin verilen işlem akışına sahip bir işlemi gösterir.</span><span class="sxs-lookup"><span data-stu-id="a2c6b-108">The following code demonstrates an operation, with Allowed transaction flow, that creates a <xref:System.Transactions.TransactionScope> with the <xref:System.Transactions.EnterpriseServicesInteropOption.Full> option.</span></span> <span data-ttu-id="a2c6b-109">Bu senaryoda aşağıdaki koşullar geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="a2c6b-109">The following conditions apply in this scenario:</span></span>  
  
- <span data-ttu-id="a2c6b-110">İstemci bir işlem akışa alıyorsa, Enterprise Services bileşenine yapılan çağrı dahil olmak üzere işlem bu işlemin kapsamı içinde yürütülür.</span><span class="sxs-lookup"><span data-stu-id="a2c6b-110">If the client flows a transaction, the operation, including the call to the Enterprise Services component, is executed within the scope of that transaction.</span></span> <span data-ttu-id="a2c6b-111"><xref:System.Transactions.EnterpriseServicesInteropOption.Full> kullanmak, işlemin <xref:System.EnterpriseServices> bağlamla eşitlenmesini sağlar. Bu, <xref:System.Transactions> ve <xref:System.EnterpriseServices> ortam işleminin aynı olduğu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="a2c6b-111">Using <xref:System.Transactions.EnterpriseServicesInteropOption.Full> ensures that the transaction is synchronized with the <xref:System.EnterpriseServices> context, which means that the ambient transaction for <xref:System.Transactions> and the <xref:System.EnterpriseServices> is the same.</span></span>  
  
- <span data-ttu-id="a2c6b-112">İstemci bir işlem akiçermiyorsa, <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> `true` ayarı, işlem için yeni bir işlem kapsamı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a2c6b-112">If the client does not flow a transaction, setting <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> to `true` creates a new transaction scope for the operation.</span></span> <span data-ttu-id="a2c6b-113">Benzer şekilde, <xref:System.Transactions.EnterpriseServicesInteropOption.Full> kullanmak işlemin işleminin, <xref:System.EnterpriseServices> bileşenin bağlamı içinde kullanılan işlemle aynı olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="a2c6b-113">Similarly, using <xref:System.Transactions.EnterpriseServicesInteropOption.Full> ensures that the operation’s transaction is the same as the transaction used inside the <xref:System.EnterpriseServices> component's context.</span></span>  
  
 <span data-ttu-id="a2c6b-114">Aynı işlemin işleminin kapsamı içinde ek yöntem çağrıları da oluşur.</span><span class="sxs-lookup"><span data-stu-id="a2c6b-114">Any additional method calls also occur within the scope of the same operation’s transaction.</span></span>  
  
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
  
 <span data-ttu-id="a2c6b-115">Bir işlemin geçerli işlemi ve işlemsel kurumsal hizmetler bileşenlerine çağrılar arasında eşitleme gerekmiyorsa, <xref:System.Transactions.TransactionScope> örneğini örneklemesinde <xref:System.Transactions.EnterpriseServicesInteropOption.None> seçeneğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="a2c6b-115">If no synchronization is required between an operation’s current transaction and calls to transactional Enterprise Services components, then use the <xref:System.Transactions.EnterpriseServicesInteropOption.None> option when instantiating the <xref:System.Transactions.TransactionScope> instance.</span></span>  
  
## <a name="integrating-enterprise-services-with-a-client"></a><span data-ttu-id="a2c6b-116">Kurumsal Hizmetleri bir Istemciyle tümleştirme</span><span class="sxs-lookup"><span data-stu-id="a2c6b-116">Integrating Enterprise Services with a Client</span></span>  
 <span data-ttu-id="a2c6b-117">Aşağıdaki kod, <xref:System.Transactions.EnterpriseServicesInteropOption.Full> ayarıyla bir <xref:System.Transactions.TransactionScope> örneği kullanarak istemci kodunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="a2c6b-117">The following code demonstrates client code using a <xref:System.Transactions.TransactionScope> instance with the <xref:System.Transactions.EnterpriseServicesInteropOption.Full> setting.</span></span> <span data-ttu-id="a2c6b-118">Bu senaryoda, işlem akışını destekleyen hizmet işlemlerine yapılan çağrılar, Enterprise Services bileşenlerine yapılan çağrılarla aynı işlemin kapsamı içinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="a2c6b-118">In this scenario, calls to service operations that support transaction flow occur within the scope of the same transaction as the calls to Enterprise Services components.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a2c6b-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a2c6b-119">See also</span></span>

- [<span data-ttu-id="a2c6b-120">COM+ Uygulamaları ile Tümleştirme</span><span class="sxs-lookup"><span data-stu-id="a2c6b-120">Integrating with COM+ Applications</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="a2c6b-121">COM Uygulamaları ile Tümleştirme</span><span class="sxs-lookup"><span data-stu-id="a2c6b-121">Integrating with COM Applications</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-applications.md)
