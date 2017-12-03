---
title: "Hizmet Sözleşmelerini Uygulama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: implementing service contracts [WCF]
ms.assetid: aefb6f56-47e3-4f24-ab0a-9bc07bf9885f
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 688637ae54e92296d103a681715dd491ba8782ba
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="implementing-service-contracts"></a><span data-ttu-id="61143-102">Hizmet Sözleşmelerini Uygulama</span><span class="sxs-lookup"><span data-stu-id="61143-102">Implementing Service Contracts</span></span>
<span data-ttu-id="61143-103">Bir hizmet bir veya daha fazla uç noktaları istemcilerinde kullanımına işlevselliği kullanıma sunan bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="61143-103">A service is a class that exposes functionality available to clients at one or more endpoints.</span></span> <span data-ttu-id="61143-104">Bir hizmet oluşturmak için uygulayan bir sınıf yazma bir [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] sözleşme.</span><span class="sxs-lookup"><span data-stu-id="61143-104">To create a service, write a class that implements a [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] contract.</span></span> <span data-ttu-id="61143-105">Bunu iki yoldan biriyle yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="61143-105">You can do this in one of two ways.</span></span> <span data-ttu-id="61143-106">Sözleşme ayrı ayrı bir arabirim tanımlayın ve ardından arabirimi uygulayan bir sınıf oluşturun.</span><span class="sxs-lookup"><span data-stu-id="61143-106">You can define the contract separately as an interface and then create a class that implements that interface.</span></span> <span data-ttu-id="61143-107">Alternatif olarak, sınıf ve sözleşme doğrudan koyarak oluşturabileceğiniz <xref:System.ServiceModel.ServiceContractAttribute> sınıfı özniteliği ve <xref:System.ServiceModel.OperationContractAttribute> hizmetinin istemciler için kullanılabilen yöntemler özniteliği.</span><span class="sxs-lookup"><span data-stu-id="61143-107">Alternatively, you can create the class and contract directly by placing the <xref:System.ServiceModel.ServiceContractAttribute> attribute on the class itself and the <xref:System.ServiceModel.OperationContractAttribute> attribute on the methods available to the clients of the service.</span></span>  
  
## <a name="creating-a-service-class"></a><span data-ttu-id="61143-108">Hizmet sınıfı oluşturma</span><span class="sxs-lookup"><span data-stu-id="61143-108">Creating a service class</span></span>  
 <span data-ttu-id="61143-109">Aşağıdaki uygulayan bir hizmetin örneğidir bir `IMath` ayrı olarak tanımlanan sözleşme.</span><span class="sxs-lookup"><span data-stu-id="61143-109">The following is an example of a service that implements an `IMath` contract that has been defined separately.</span></span>  
  
```csharp  
// Define the IMath contract.  
[ServiceContract]  
public interface IMath  
{  
    [OperationContract]   
    double Add(double A, double B);  
  
    [OperationContract]  
    double Multiply (double A, double B);  
}  
  
// Implement the IMath contract in the MathService class.  
public class MathService : IMath  
{  
    public double Add (double A, double B) { return A + B; }  
    public double Multiply (double A, double B) { return A * B; }  
}  
```  
  
 <span data-ttu-id="61143-110">Alternatif olarak, bir hizmet, bir sözleşme doğrudan getirebilir.</span><span class="sxs-lookup"><span data-stu-id="61143-110">Alternatively, a service can expose a contract directly.</span></span> <span data-ttu-id="61143-111">Aşağıdaki tanımlayan ve uygulayan bir hizmet sınıf örnektir bir `MathService` sözleşme.</span><span class="sxs-lookup"><span data-stu-id="61143-111">The following is an example of a service class that defines and implements a `MathService` contract.</span></span>  
  
```csharp  
// Define the MathService contract directly on the service class.  
[ServiceContract]  
class MathService  
{  
    [OperationContract]  
    public double Add(double A, double B) { return A + B; }  
    [OperationContract]  
    private double Multiply (double A, double B) { return A * B; }  
}  
```  
  
 <span data-ttu-id="61143-112">Önceki hizmetleri sözleşmesi adları farklı olduğundan farklı sözleşmeleri kullanıma unutmayın.</span><span class="sxs-lookup"><span data-stu-id="61143-112">Note that the preceding services expose different contracts because the contract names are different.</span></span> <span data-ttu-id="61143-113">İlk durumda gösterilen sözleşme adında "`IMath`"İkinci durumda sözleşme adlı sırada"`MathService`".</span><span class="sxs-lookup"><span data-stu-id="61143-113">In the first case, the exposed contract is named "`IMath`" while in the second case the contract is named "`MathService`".</span></span>  
  
 <span data-ttu-id="61143-114">Birkaç hizmet ve işlem eşzamanlılık ve örnek oluşturma gibi uygulama düzeyleri ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="61143-114">You can set a few things at the service and operation implementation levels, such as concurrency and instancing.</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="61143-115">[Hizmetleri Tasarlama ve uygulama](../../../docs/framework/wcf/designing-and-implementing-services.md).</span><span class="sxs-lookup"><span data-stu-id="61143-115"> [Designing and Implementing Services](../../../docs/framework/wcf/designing-and-implementing-services.md).</span></span>  
  
 <span data-ttu-id="61143-116">Bir hizmet sözleşmesini uyguladıktan sonra hizmet için bir veya daha fazla uç noktalar oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="61143-116">After implementing a service contract, you must create one or more endpoints for the service.</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="61143-117">[Uç noktası oluşturma genel bakış](../../../docs/framework/wcf/endpoint-creation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="61143-117"> [Endpoint Creation Overview](../../../docs/framework/wcf/endpoint-creation-overview.md).</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="61143-118">bir hizmet farklı çalıştır nasıl [barındırma hizmetleri](../../../docs/framework/wcf/hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="61143-118"> how to run a service, see [Hosting Services](../../../docs/framework/wcf/hosting-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61143-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="61143-119">See Also</span></span>  
 [<span data-ttu-id="61143-120">Hizmetleri Tasarlama ve uygulama</span><span class="sxs-lookup"><span data-stu-id="61143-120">Designing and Implementing Services</span></span>](../../../docs/framework/wcf/designing-and-implementing-services.md)  
 [<span data-ttu-id="61143-121">Nasıl yapılır: Sözleşme sınıfı ile hizmet oluşturma</span><span class="sxs-lookup"><span data-stu-id="61143-121">How to: Create a Service with a Contract Class</span></span>](../../../docs/framework/wcf/feature-details/how-to-create-a-wcf-contract-with-a-class.md)  
 [<span data-ttu-id="61143-122">Nasıl yapılır: sözleşme arabirimi ile bir hizmet oluşturma</span><span class="sxs-lookup"><span data-stu-id="61143-122">How to: Create a Service with a Contract Interface</span></span>](../../../docs/framework/wcf/feature-details/how-to-create-a-service-with-a-contract-interface.md)  
 [<span data-ttu-id="61143-123">Hizmet çalışma zamanı davranışını belirtme</span><span class="sxs-lookup"><span data-stu-id="61143-123">Specifying Service Run-Time Behavior</span></span>](../../../docs/framework/wcf/specifying-service-run-time-behavior.md)
