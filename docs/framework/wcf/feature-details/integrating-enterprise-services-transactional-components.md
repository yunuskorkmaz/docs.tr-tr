---
title: "Kurumsal Hizmetler İşlemsel Bileşenlerini Tümleştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 05dab277-b8b2-48cf-b40c-826be128b175
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a236a34dd20661d62d59a3712a1800ff1f9a11ad
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="integrating-enterprise-services-transactional-components"></a><span data-ttu-id="6566b-102">Kurumsal Hizmetler İşlemsel Bileşenlerini Tümleştirme</span><span class="sxs-lookup"><span data-stu-id="6566b-102">Integrating Enterprise Services Transactional Components</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="6566b-103">Kurumsal Hizmetler ile tümleştirmek için otomatik bir mekanizma sağlar (bkz [COM + uygulamaları ile tümleştirme](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)).</span><span class="sxs-lookup"><span data-stu-id="6566b-103"> provides an automatic mechanism for integrating with Enterprise Services (see [Integrating with COM+ Applications](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)).</span></span> <span data-ttu-id="6566b-104">Ancak, dahili Kurumsal Hizmetler içinde barındırılan işlemsel bileşenlerini kullanan hizmetler geliştirmek için esneklik isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6566b-104">However, you may want the flexibility to develop services that internally use transactional components hosted within Enterprise Services.</span></span> <span data-ttu-id="6566b-105">Çünkü [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] işlemleri özelliği üzerinde oluşturulan <xref:System.Transactions> altyapısı, Kuruluş Hizmetleri ile tümleştirme için işlem [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] arasında birlikte çalışabilirlik belirtmek için aynı olan <xref:System.Transactions> ve Enterprise Kısmında özetlendiği gibi hizmetleri [Kurumsal Hizmetler ve COM + işlemleri ile birlikte çalışabilirlik](http://go.microsoft.com/fwlink/?LinkId=94949).</span><span class="sxs-lookup"><span data-stu-id="6566b-105">Because the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Transactions feature is built on the <xref:System.Transactions> infrastructure, the process for integrating Enterprise Services with [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] is identical to that for specifying interoperability between <xref:System.Transactions> and Enterprise Services, as outlined in [Interoperability with Enterprise Services and COM+ Transactions](http://go.microsoft.com/fwlink/?LinkId=94949).</span></span>  
  
 <span data-ttu-id="6566b-106">Gelen akışlı işlem ve COM + bağlam işlemi arasında birlikte çalışabilirlik istenen düzeyini sağlamak için hizmet uygulaması oluşturmanız gerekir bir <xref:System.Transactions.TransactionScope> örneği ve uygun değerini kullanın <xref:System.Transactions.EnterpriseServicesInteropOption> numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="6566b-106">To provide the desired level of interoperability between the incoming flowed transaction and the COM+ context transaction, the service implementation must create a <xref:System.Transactions.TransactionScope> instance and use the appropriate value from the <xref:System.Transactions.EnterpriseServicesInteropOption> enumeration.</span></span>  
  
## <a name="integrating-enterprise-services-with-a-service-operation"></a><span data-ttu-id="6566b-107">Kurumsal Hizmetler bir hizmet işlemi ile tümleştirme</span><span class="sxs-lookup"><span data-stu-id="6566b-107">Integrating Enterprise Services with a Service Operation</span></span>  
 <span data-ttu-id="6566b-108">Aşağıdaki kod bir işlemle oluşturan izin verilen işlem akışını göstermektedir bir <xref:System.Transactions.TransactionScope> ile <xref:System.Transactions.EnterpriseServicesInteropOption.Full> seçeneği.</span><span class="sxs-lookup"><span data-stu-id="6566b-108">The following code demonstrates an operation, with Allowed transaction flow, that creates a <xref:System.Transactions.TransactionScope> with the <xref:System.Transactions.EnterpriseServicesInteropOption.Full> option.</span></span> <span data-ttu-id="6566b-109">Bu senaryoda aşağıdaki koşullar geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="6566b-109">The following conditions apply in this scenario:</span></span>  
  
-   <span data-ttu-id="6566b-110">İstemci bir işlem akışlar, Kurumsal hizmetleri bileşeni çağrısı dahil olmak üzere işlemi, bu işlem kapsamı içinde yürütülür.</span><span class="sxs-lookup"><span data-stu-id="6566b-110">If the client flows a transaction, the operation, including the call to the Enterprise Services component, is executed within the scope of that transaction.</span></span> <span data-ttu-id="6566b-111">Kullanarak <xref:System.Transactions.EnterpriseServicesInteropOption.Full> işlem ile eşitlenir sağlar <xref:System.EnterpriseServices> için ortam işlem anlamına bağlam <xref:System.Transactions> ve <xref:System.EnterpriseServices> aynıdır.</span><span class="sxs-lookup"><span data-stu-id="6566b-111">Using <xref:System.Transactions.EnterpriseServicesInteropOption.Full> ensures that the transaction is synchronized with the <xref:System.EnterpriseServices> context, which means that the ambient transaction for <xref:System.Transactions> and the <xref:System.EnterpriseServices> is the same.</span></span>  
  
-   <span data-ttu-id="6566b-112">İstemci bir işlem akış değil, ayarı <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> için `true` işlemi için yeni bir işlem kapsamı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6566b-112">If the client does not flow a transaction, setting <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> to `true` creates a new transaction scope for the operation.</span></span> <span data-ttu-id="6566b-113">Benzer şekilde, kullanarak <xref:System.Transactions.EnterpriseServicesInteropOption.Full> işlemin işlem içinde kullanılan işlem ile aynı olmasını sağlar <xref:System.EnterpriseServices> bileşenin bağlamı.</span><span class="sxs-lookup"><span data-stu-id="6566b-113">Similarly, using <xref:System.Transactions.EnterpriseServicesInteropOption.Full> ensures that the operation’s transaction is the same as the transaction used inside the <xref:System.EnterpriseServices> component's context.</span></span>  
  
 <span data-ttu-id="6566b-114">Hiçbir ek yöntem çağrıları de aynı işlem işlem kapsamı içinde gerçekleşmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="6566b-114">Any additional method calls also occur within the scope of the same operation’s transaction.</span></span>  
  
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
  
 <span data-ttu-id="6566b-115">Bir işlemin geçerli işlem ve Kurumsal Hizmetler işlemsel bileşenlerini çağrıları arasında eşitleme işlemi gerekiyorsa, daha sonra kullanmak <xref:System.Transactions.EnterpriseServicesInteropOption.None> seçeneği başlatılırken <xref:System.Transactions.TransactionScope> örneği.</span><span class="sxs-lookup"><span data-stu-id="6566b-115">If no synchronization is required between an operation’s current transaction and calls to transactional Enterprise Services components, then use the <xref:System.Transactions.EnterpriseServicesInteropOption.None> option when instantiating the <xref:System.Transactions.TransactionScope> instance.</span></span>  
  
## <a name="integrating-enterprise-services-with-a-client"></a><span data-ttu-id="6566b-116">Kurumsal Hizmetler istemcisi ile tümleştirme</span><span class="sxs-lookup"><span data-stu-id="6566b-116">Integrating Enterprise Services with a Client</span></span>  
 <span data-ttu-id="6566b-117">Aşağıdaki kod, istemci kodu kullanarak gösterir bir <xref:System.Transactions.TransactionScope> örneği <xref:System.Transactions.EnterpriseServicesInteropOption.Full> ayarı.</span><span class="sxs-lookup"><span data-stu-id="6566b-117">The following code demonstrates client code using a <xref:System.Transactions.TransactionScope> instance with the <xref:System.Transactions.EnterpriseServicesInteropOption.Full> setting.</span></span> <span data-ttu-id="6566b-118">Bu senaryoda, işlem akışı destek hizmet işlemlerine çağrıları Kuruluş Hizmetleri bileşenleri çağrılar aynı işlem kapsamı içinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="6566b-118">In this scenario, calls to service operations that support transaction flow occur within the scope of the same transaction as the calls to Enterprise Services components.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6566b-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6566b-119">See Also</span></span>  
 [<span data-ttu-id="6566b-120">COM + uygulamaları ile tümleştirme</span><span class="sxs-lookup"><span data-stu-id="6566b-120">Integrating with COM+ Applications</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)  
 [<span data-ttu-id="6566b-121">COM uygulamaları ile tümleştirme</span><span class="sxs-lookup"><span data-stu-id="6566b-121">Integrating with COM Applications</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-applications.md)
