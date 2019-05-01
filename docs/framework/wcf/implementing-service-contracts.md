---
title: Hizmet Sözleşmelerini Uygulama
ms.date: 03/30/2017
helpviewer_keywords:
- implementing service contracts [WCF]
ms.assetid: aefb6f56-47e3-4f24-ab0a-9bc07bf9885f
ms.openlocfilehash: 766e0c4d30a4fa0eed9ce154ca932f5371a43211
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61928642"
---
# <a name="implementing-service-contracts"></a><span data-ttu-id="44dd6-102">Hizmet Sözleşmelerini Uygulama</span><span class="sxs-lookup"><span data-stu-id="44dd6-102">Implementing Service Contracts</span></span>
<span data-ttu-id="44dd6-103">Bir veya daha fazla uç noktası istemcilere kullanılabilir olan işlevsellik sunduğu bir sınıf bir hizmettir.</span><span class="sxs-lookup"><span data-stu-id="44dd6-103">A service is a class that exposes functionality available to clients at one or more endpoints.</span></span> <span data-ttu-id="44dd6-104">Bir hizmet oluşturmak için bir Windows Communication Foundation (WCF) sözleşmesi uygulayan bir sınıf yazın.</span><span class="sxs-lookup"><span data-stu-id="44dd6-104">To create a service, write a class that implements a Windows Communication Foundation (WCF) contract.</span></span> <span data-ttu-id="44dd6-105">İki yoldan biriyle bunu yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="44dd6-105">You can do this in one of two ways.</span></span> <span data-ttu-id="44dd6-106">Sözleşme ayrı ayrı arabirim olarak tanımlayabilir ve ardından bu arabirimi uygulayan bir sınıf oluşturun.</span><span class="sxs-lookup"><span data-stu-id="44dd6-106">You can define the contract separately as an interface and then create a class that implements that interface.</span></span> <span data-ttu-id="44dd6-107">Alternatif olarak, sınıf ve sözleşme doğrudan yerleştirerek oluşturabileceğiniz <xref:System.ServiceModel.ServiceContractAttribute> sınıfı özniteliği ve <xref:System.ServiceModel.OperationContractAttribute> hizmeti istemcilerine uygun olan yöntemler özniteliği.</span><span class="sxs-lookup"><span data-stu-id="44dd6-107">Alternatively, you can create the class and contract directly by placing the <xref:System.ServiceModel.ServiceContractAttribute> attribute on the class itself and the <xref:System.ServiceModel.OperationContractAttribute> attribute on the methods available to the clients of the service.</span></span>  
  
## <a name="creating-a-service-class"></a><span data-ttu-id="44dd6-108">Bir hizmet sınıfı oluşturma</span><span class="sxs-lookup"><span data-stu-id="44dd6-108">Creating a service class</span></span>  
 <span data-ttu-id="44dd6-109">Uygulayan bir hizmetin bir örneği verilmiştir bir `IMath` ayrı olarak tanımlanan sözleşme.</span><span class="sxs-lookup"><span data-stu-id="44dd6-109">The following is an example of a service that implements an `IMath` contract that has been defined separately.</span></span>  
  
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
  
 <span data-ttu-id="44dd6-110">Alternatif olarak, bir hizmet sözleşme doğrudan kullanıma sunabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="44dd6-110">Alternatively, a service can expose a contract directly.</span></span> <span data-ttu-id="44dd6-111">Tanımlar ve uygulayan bir hizmet sınıfın bir örneği verilmiştir bir `MathService` sözleşme.</span><span class="sxs-lookup"><span data-stu-id="44dd6-111">The following is an example of a service class that defines and implements a `MathService` contract.</span></span>  
  
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
  
 <span data-ttu-id="44dd6-112">Önceki hizmetlerin sözleşmesi adları farklı olduğundan farklı sözleşmeler kullanıma unutmayın.</span><span class="sxs-lookup"><span data-stu-id="44dd6-112">Note that the preceding services expose different contracts because the contract names are different.</span></span> <span data-ttu-id="44dd6-113">Bu durumda, kullanıma sunulan sözleşme adında "`IMath`"İkinci durumda sözleşme adlandırılırken"`MathService`".</span><span class="sxs-lookup"><span data-stu-id="44dd6-113">In the first case, the exposed contract is named "`IMath`" while in the second case the contract is named "`MathService`".</span></span>  
  
 <span data-ttu-id="44dd6-114">Hizmet ve işlem eşzamanlılık ve örnek oluşturma gibi uygulama düzeyleri birkaç şey ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="44dd6-114">You can set a few things at the service and operation implementation levels, such as concurrency and instancing.</span></span> <span data-ttu-id="44dd6-115">Daha fazla bilgi için [Hizmetleri Tasarlama ve uygulama](../../../docs/framework/wcf/designing-and-implementing-services.md).</span><span class="sxs-lookup"><span data-stu-id="44dd6-115">For more information, see [Designing and Implementing Services](../../../docs/framework/wcf/designing-and-implementing-services.md).</span></span>  
  
 <span data-ttu-id="44dd6-116">Bir hizmet sözleşmesini uyguladıktan sonra hizmeti için bir veya daha fazla uç noktası oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="44dd6-116">After implementing a service contract, you must create one or more endpoints for the service.</span></span> <span data-ttu-id="44dd6-117">Daha fazla bilgi için [uç nokta oluşturmaya genel bakış](../../../docs/framework/wcf/endpoint-creation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="44dd6-117">For more information, see [Endpoint Creation Overview](../../../docs/framework/wcf/endpoint-creation-overview.md).</span></span> <span data-ttu-id="44dd6-118">Bir hizmet çalıştırma hakkında daha fazla bilgi için bkz. [barındırma hizmetleri](../../../docs/framework/wcf/hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="44dd6-118">For more information about how to run a service, see [Hosting Services](../../../docs/framework/wcf/hosting-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44dd6-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="44dd6-119">See also</span></span>

- [<span data-ttu-id="44dd6-120">Hizmetleri Tasarlama ve Uygulama</span><span class="sxs-lookup"><span data-stu-id="44dd6-120">Designing and Implementing Services</span></span>](../../../docs/framework/wcf/designing-and-implementing-services.md)
- [<span data-ttu-id="44dd6-121">Nasıl yapılır: Bir sözleşme sınıfı ile hizmet oluşturma</span><span class="sxs-lookup"><span data-stu-id="44dd6-121">How to: Create a Service with a Contract Class</span></span>](../../../docs/framework/wcf/feature-details/how-to-create-a-wcf-contract-with-a-class.md)
- [<span data-ttu-id="44dd6-122">Nasıl yapılır: Bir sözleşme arabirimi ile hizmet oluşturma</span><span class="sxs-lookup"><span data-stu-id="44dd6-122">How to: Create a Service with a Contract Interface</span></span>](../../../docs/framework/wcf/feature-details/how-to-create-a-service-with-a-contract-interface.md)
- [<span data-ttu-id="44dd6-123">Hizmet Çalışma Zamanı Davranışını Belirtme</span><span class="sxs-lookup"><span data-stu-id="44dd6-123">Specifying Service Run-Time Behavior</span></span>](../../../docs/framework/wcf/specifying-service-run-time-behavior.md)
