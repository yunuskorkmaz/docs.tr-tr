---
title: Kurumsal Hizmetler İşlemsel Bileşenlerini Tümleştirme
ms.date: 03/30/2017
ms.assetid: 05dab277-b8b2-48cf-b40c-826be128b175
ms.openlocfilehash: 3fd8876de53be30f18e4fa9d7f4a1cc07ab5e220
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90554110"
---
# <a name="integrating-enterprise-services-transactional-components"></a><span data-ttu-id="ef581-102">Kurumsal Hizmetler İşlemsel Bileşenlerini Tümleştirme</span><span class="sxs-lookup"><span data-stu-id="ef581-102">Integrating Enterprise Services Transactional Components</span></span>

<span data-ttu-id="ef581-103">Windows Communication Foundation (WCF), Enterprise Services ile tümleştirme için otomatik bir mekanizma sağlar (bkz. [com+ uygulamalarıyla tümleştirme](integrating-with-com-plus-applications.md)).</span><span class="sxs-lookup"><span data-stu-id="ef581-103">Windows Communication Foundation (WCF) provides an automatic mechanism for integrating with Enterprise Services (see [Integrating with COM+ Applications](integrating-with-com-plus-applications.md)).</span></span> <span data-ttu-id="ef581-104">Ancak, kurumsal hizmetlerde barındırılan işlemsel bileşenleri dahili olarak kullanan hizmetler geliştirme esnekliği de isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ef581-104">However, you may want the flexibility to develop services that internally use transactional components hosted within Enterprise Services.</span></span> <span data-ttu-id="ef581-105">WCF Işlemler özelliği altyapıda oluşturulduğu için, Enterprise Services 'ı <xref:System.Transactions> WCF ile tümleştirme işlemi, Kurumsal Hizmetler <xref:System.Transactions> [ve com+ Işlemleri ile birlikte çalışabilirlik](/previous-versions/dotnet/netframework-3.0/ms229974(v=vs.85))bölümünde açıklandığı gibi, ve Enterprise Services arasında birlikte çalışabilirlik belirtme ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="ef581-105">Because the WCF Transactions feature is built on the <xref:System.Transactions> infrastructure, the process for integrating Enterprise Services with WCF is identical to that for specifying interoperability between <xref:System.Transactions> and Enterprise Services, as outlined in [Interoperability with Enterprise Services and COM+ Transactions](/previous-versions/dotnet/netframework-3.0/ms229974(v=vs.85)).</span></span>  
  
 <span data-ttu-id="ef581-106">Gelen akışlı işlem ve COM+ bağlam işlemi arasında istediğiniz birlikte çalışabilirlik düzeyini sağlamak için, hizmet uygulamasının bir <xref:System.Transactions.TransactionScope> örnek oluşturması ve Numaralandırmadaki uygun değeri kullanması gerekir <xref:System.Transactions.EnterpriseServicesInteropOption> .</span><span class="sxs-lookup"><span data-stu-id="ef581-106">To provide the desired level of interoperability between the incoming flowed transaction and the COM+ context transaction, the service implementation must create a <xref:System.Transactions.TransactionScope> instance and use the appropriate value from the <xref:System.Transactions.EnterpriseServicesInteropOption> enumeration.</span></span>  
  
## <a name="integrating-enterprise-services-with-a-service-operation"></a><span data-ttu-id="ef581-107">Kurumsal Hizmetleri bir hizmet Işlemi ile tümleştirme</span><span class="sxs-lookup"><span data-stu-id="ef581-107">Integrating Enterprise Services with a Service Operation</span></span>  
 <span data-ttu-id="ef581-108">Aşağıdaki kod, seçeneğiyle bir olan bir işlemi, Izin verilen işlem akışı ile gösterir <xref:System.Transactions.TransactionScope> <xref:System.Transactions.EnterpriseServicesInteropOption.Full> .</span><span class="sxs-lookup"><span data-stu-id="ef581-108">The following code demonstrates an operation, with Allowed transaction flow, that creates a <xref:System.Transactions.TransactionScope> with the <xref:System.Transactions.EnterpriseServicesInteropOption.Full> option.</span></span> <span data-ttu-id="ef581-109">Bu senaryoda aşağıdaki koşullar geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="ef581-109">The following conditions apply in this scenario:</span></span>  
  
- <span data-ttu-id="ef581-110">İstemci bir işlem akışa alıyorsa, Enterprise Services bileşenine yapılan çağrı dahil olmak üzere işlem bu işlemin kapsamı içinde yürütülür.</span><span class="sxs-lookup"><span data-stu-id="ef581-110">If the client flows a transaction, the operation, including the call to the Enterprise Services component, is executed within the scope of that transaction.</span></span> <span data-ttu-id="ef581-111">Kullanılarak <xref:System.Transactions.EnterpriseServicesInteropOption.Full> işlemin, <xref:System.EnterpriseServices> ve için ortam işleminin <xref:System.Transactions> aynı olduğu anlamına gelen bağlamla eşitlenmesi sağlanır <xref:System.EnterpriseServices> .</span><span class="sxs-lookup"><span data-stu-id="ef581-111">Using <xref:System.Transactions.EnterpriseServicesInteropOption.Full> ensures that the transaction is synchronized with the <xref:System.EnterpriseServices> context, which means that the ambient transaction for <xref:System.Transactions> and the <xref:System.EnterpriseServices> is the same.</span></span>  
  
- <span data-ttu-id="ef581-112">İstemci bir işlem akiçermiyorsa <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> `true` işlem için yeni bir işlem kapsamı oluşturur ayarı.</span><span class="sxs-lookup"><span data-stu-id="ef581-112">If the client does not flow a transaction, setting <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> to `true` creates a new transaction scope for the operation.</span></span> <span data-ttu-id="ef581-113">Benzer şekilde, kullanmak <xref:System.Transactions.EnterpriseServicesInteropOption.Full> işlemin işleminin bileşenin bağlamı içinde kullanılan işlemle aynı olmasını sağlar <xref:System.EnterpriseServices> .</span><span class="sxs-lookup"><span data-stu-id="ef581-113">Similarly, using <xref:System.Transactions.EnterpriseServicesInteropOption.Full> ensures that the operation’s transaction is the same as the transaction used inside the <xref:System.EnterpriseServices> component's context.</span></span>  
  
 <span data-ttu-id="ef581-114">Aynı işlemin işleminin kapsamı içinde ek yöntem çağrıları da oluşur.</span><span class="sxs-lookup"><span data-stu-id="ef581-114">Any additional method calls also occur within the scope of the same operation’s transaction.</span></span>  
  
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
  
 <span data-ttu-id="ef581-115">Bir işlemin geçerli işlemi ile işlem Enterprise Services bileşenlerine yapılan çağrılar arasında eşitleme gerekmiyorsa, <xref:System.Transactions.EnterpriseServicesInteropOption.None> örneği örneklemesinde seçeneğini kullanın <xref:System.Transactions.TransactionScope> .</span><span class="sxs-lookup"><span data-stu-id="ef581-115">If no synchronization is required between an operation’s current transaction and calls to transactional Enterprise Services components, then use the <xref:System.Transactions.EnterpriseServicesInteropOption.None> option when instantiating the <xref:System.Transactions.TransactionScope> instance.</span></span>  
  
## <a name="integrating-enterprise-services-with-a-client"></a><span data-ttu-id="ef581-116">Kurumsal Hizmetleri bir Istemciyle tümleştirme</span><span class="sxs-lookup"><span data-stu-id="ef581-116">Integrating Enterprise Services with a Client</span></span>  
 <span data-ttu-id="ef581-117">Aşağıdaki kod, ayarıyla bir örnek kullanan istemci kodunu gösterir <xref:System.Transactions.TransactionScope> <xref:System.Transactions.EnterpriseServicesInteropOption.Full> .</span><span class="sxs-lookup"><span data-stu-id="ef581-117">The following code demonstrates client code using a <xref:System.Transactions.TransactionScope> instance with the <xref:System.Transactions.EnterpriseServicesInteropOption.Full> setting.</span></span> <span data-ttu-id="ef581-118">Bu senaryoda, işlem akışını destekleyen hizmet işlemlerine yapılan çağrılar, Enterprise Services bileşenlerine yapılan çağrılarla aynı işlemin kapsamı içinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="ef581-118">In this scenario, calls to service operations that support transaction flow occur within the scope of the same transaction as the calls to Enterprise Services components.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ef581-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ef581-119">See also</span></span>

- [<span data-ttu-id="ef581-120">COM+ uygulamalarıyla tümleştirme</span><span class="sxs-lookup"><span data-stu-id="ef581-120">Integrating with COM+ Applications</span></span>](integrating-with-com-plus-applications.md)
- [<span data-ttu-id="ef581-121">COM Uygulamaları ile Tümleştirme</span><span class="sxs-lookup"><span data-stu-id="ef581-121">Integrating with COM Applications</span></span>](integrating-with-com-applications.md)
