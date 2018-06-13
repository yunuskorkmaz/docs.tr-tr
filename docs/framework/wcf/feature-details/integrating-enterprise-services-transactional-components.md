---
title: Kurumsal Hizmetler İşlemsel Bileşenlerini Tümleştirme
ms.date: 03/30/2017
ms.assetid: 05dab277-b8b2-48cf-b40c-826be128b175
ms.openlocfilehash: 8453b4199f5e6eae263ebc3fc1c457429c868d7f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33492518"
---
# <a name="integrating-enterprise-services-transactional-components"></a><span data-ttu-id="9a80e-102">Kurumsal Hizmetler İşlemsel Bileşenlerini Tümleştirme</span><span class="sxs-lookup"><span data-stu-id="9a80e-102">Integrating Enterprise Services Transactional Components</span></span>
<span data-ttu-id="9a80e-103">Windows Communication Foundation (WCF) Kuruluş Hizmetleri ile tümleştirme için otomatik bir mekanizma sağlar (bkz [COM + uygulamaları ile tümleştirme](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)).</span><span class="sxs-lookup"><span data-stu-id="9a80e-103">Windows Communication Foundation (WCF) provides an automatic mechanism for integrating with Enterprise Services (see [Integrating with COM+ Applications](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)).</span></span> <span data-ttu-id="9a80e-104">Ancak, dahili Kurumsal Hizmetler içinde barındırılan işlemsel bileşenlerini kullanan hizmetler geliştirmek için esneklik isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9a80e-104">However, you may want the flexibility to develop services that internally use transactional components hosted within Enterprise Services.</span></span> <span data-ttu-id="9a80e-105">WCF işlemleri özelliği oluşturulduğundan <xref:System.Transactions> altyapı, Kurumsal Hizmetler WCF ile tümleştirmek için işlemidir arasında birlikte çalışabilirlik belirtmek için aynı <xref:System.Transactions> ve kurumsal kısmında özetlendiği gibi hizmetler [Kurumsal Hizmetler ve COM + işlemleri ile birlikte çalışabilirlik](http://go.microsoft.com/fwlink/?LinkId=94949).</span><span class="sxs-lookup"><span data-stu-id="9a80e-105">Because the WCF Transactions feature is built on the <xref:System.Transactions> infrastructure, the process for integrating Enterprise Services with WCF is identical to that for specifying interoperability between <xref:System.Transactions> and Enterprise Services, as outlined in [Interoperability with Enterprise Services and COM+ Transactions](http://go.microsoft.com/fwlink/?LinkId=94949).</span></span>  
  
 <span data-ttu-id="9a80e-106">Gelen akışlı işlem ve COM + bağlam işlemi arasında birlikte çalışabilirlik istenen düzeyini sağlamak için hizmet uygulaması oluşturmanız gerekir bir <xref:System.Transactions.TransactionScope> örneği ve uygun değerini kullanın <xref:System.Transactions.EnterpriseServicesInteropOption> numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="9a80e-106">To provide the desired level of interoperability between the incoming flowed transaction and the COM+ context transaction, the service implementation must create a <xref:System.Transactions.TransactionScope> instance and use the appropriate value from the <xref:System.Transactions.EnterpriseServicesInteropOption> enumeration.</span></span>  
  
## <a name="integrating-enterprise-services-with-a-service-operation"></a><span data-ttu-id="9a80e-107">Kurumsal Hizmetler bir hizmet işlemi ile tümleştirme</span><span class="sxs-lookup"><span data-stu-id="9a80e-107">Integrating Enterprise Services with a Service Operation</span></span>  
 <span data-ttu-id="9a80e-108">Aşağıdaki kod bir işlemle oluşturan izin verilen işlem akışını göstermektedir bir <xref:System.Transactions.TransactionScope> ile <xref:System.Transactions.EnterpriseServicesInteropOption.Full> seçeneği.</span><span class="sxs-lookup"><span data-stu-id="9a80e-108">The following code demonstrates an operation, with Allowed transaction flow, that creates a <xref:System.Transactions.TransactionScope> with the <xref:System.Transactions.EnterpriseServicesInteropOption.Full> option.</span></span> <span data-ttu-id="9a80e-109">Bu senaryoda aşağıdaki koşullar geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="9a80e-109">The following conditions apply in this scenario:</span></span>  
  
-   <span data-ttu-id="9a80e-110">İstemci bir işlem akışlar, Kurumsal hizmetleri bileşeni çağrısı dahil olmak üzere işlemi, bu işlem kapsamı içinde yürütülür.</span><span class="sxs-lookup"><span data-stu-id="9a80e-110">If the client flows a transaction, the operation, including the call to the Enterprise Services component, is executed within the scope of that transaction.</span></span> <span data-ttu-id="9a80e-111">Kullanarak <xref:System.Transactions.EnterpriseServicesInteropOption.Full> işlem ile eşitlenir sağlar <xref:System.EnterpriseServices> için ortam işlem anlamına bağlam <xref:System.Transactions> ve <xref:System.EnterpriseServices> aynıdır.</span><span class="sxs-lookup"><span data-stu-id="9a80e-111">Using <xref:System.Transactions.EnterpriseServicesInteropOption.Full> ensures that the transaction is synchronized with the <xref:System.EnterpriseServices> context, which means that the ambient transaction for <xref:System.Transactions> and the <xref:System.EnterpriseServices> is the same.</span></span>  
  
-   <span data-ttu-id="9a80e-112">İstemci bir işlem akış değil, ayarı <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> için `true` işlemi için yeni bir işlem kapsamı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9a80e-112">If the client does not flow a transaction, setting <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> to `true` creates a new transaction scope for the operation.</span></span> <span data-ttu-id="9a80e-113">Benzer şekilde, kullanarak <xref:System.Transactions.EnterpriseServicesInteropOption.Full> işlemin işlem içinde kullanılan işlem ile aynı olmasını sağlar <xref:System.EnterpriseServices> bileşenin bağlamı.</span><span class="sxs-lookup"><span data-stu-id="9a80e-113">Similarly, using <xref:System.Transactions.EnterpriseServicesInteropOption.Full> ensures that the operation’s transaction is the same as the transaction used inside the <xref:System.EnterpriseServices> component's context.</span></span>  
  
 <span data-ttu-id="9a80e-114">Hiçbir ek yöntem çağrıları de aynı işlem işlem kapsamı içinde gerçekleşmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="9a80e-114">Any additional method calls also occur within the scope of the same operation’s transaction.</span></span>  
  
```  
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
  
 <span data-ttu-id="9a80e-115">Bir işlemin geçerli işlem ve Kurumsal Hizmetler işlemsel bileşenlerini çağrıları arasında eşitleme işlemi gerekiyorsa, daha sonra kullanmak <xref:System.Transactions.EnterpriseServicesInteropOption.None> seçeneği başlatılırken <xref:System.Transactions.TransactionScope> örneği.</span><span class="sxs-lookup"><span data-stu-id="9a80e-115">If no synchronization is required between an operation’s current transaction and calls to transactional Enterprise Services components, then use the <xref:System.Transactions.EnterpriseServicesInteropOption.None> option when instantiating the <xref:System.Transactions.TransactionScope> instance.</span></span>  
  
## <a name="integrating-enterprise-services-with-a-client"></a><span data-ttu-id="9a80e-116">Kurumsal Hizmetler istemcisi ile tümleştirme</span><span class="sxs-lookup"><span data-stu-id="9a80e-116">Integrating Enterprise Services with a Client</span></span>  
 <span data-ttu-id="9a80e-117">Aşağıdaki kod, istemci kodu kullanarak gösterir bir <xref:System.Transactions.TransactionScope> örneği <xref:System.Transactions.EnterpriseServicesInteropOption.Full> ayarı.</span><span class="sxs-lookup"><span data-stu-id="9a80e-117">The following code demonstrates client code using a <xref:System.Transactions.TransactionScope> instance with the <xref:System.Transactions.EnterpriseServicesInteropOption.Full> setting.</span></span> <span data-ttu-id="9a80e-118">Bu senaryoda, işlem akışı destek hizmet işlemlerine çağrıları Kuruluş Hizmetleri bileşenleri çağrılar aynı işlem kapsamı içinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="9a80e-118">In this scenario, calls to service operations that support transaction flow occur within the scope of the same transaction as the calls to Enterprise Services components.</span></span>  
  
```  
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
  
## <a name="see-also"></a><span data-ttu-id="9a80e-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9a80e-119">See Also</span></span>  
 [<span data-ttu-id="9a80e-120">COM+ Uygulamaları ile Tümleştirme</span><span class="sxs-lookup"><span data-stu-id="9a80e-120">Integrating with COM+ Applications</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)  
 [<span data-ttu-id="9a80e-121">COM Uygulamaları ile Tümleştirme</span><span class="sxs-lookup"><span data-stu-id="9a80e-121">Integrating with COM Applications</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-applications.md)
