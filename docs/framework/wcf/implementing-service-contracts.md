---
title: Hizmet Sözleşmelerini Uygulama
ms.date: 03/30/2017
helpviewer_keywords:
- implementing service contracts [WCF]
ms.assetid: aefb6f56-47e3-4f24-ab0a-9bc07bf9885f
ms.openlocfilehash: ac27329278edc2b9ca693aa15bcc5bb58edffe05
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320155"
---
# <a name="implementing-service-contracts"></a><span data-ttu-id="b84cd-102">Hizmet Sözleşmelerini Uygulama</span><span class="sxs-lookup"><span data-stu-id="b84cd-102">Implementing Service Contracts</span></span>
<span data-ttu-id="b84cd-103">Hizmet, bir veya daha fazla bitiş noktasında istemciler için kullanılabilir işlevselliği kullanıma sunan bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="b84cd-103">A service is a class that exposes functionality available to clients at one or more endpoints.</span></span> <span data-ttu-id="b84cd-104">Bir hizmet oluşturmak için, bir Windows Communication Foundation (WCF) sözleşmesi uygulayan bir sınıf yazın.</span><span class="sxs-lookup"><span data-stu-id="b84cd-104">To create a service, write a class that implements a Windows Communication Foundation (WCF) contract.</span></span> <span data-ttu-id="b84cd-105">Bunu iki şekilde yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b84cd-105">You can do this in one of two ways.</span></span> <span data-ttu-id="b84cd-106">Sözleşmeyi ayrı bir arabirim olarak tanımlayabilir ve ardından bu arabirimi uygulayan bir sınıf oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b84cd-106">You can define the contract separately as an interface and then create a class that implements that interface.</span></span> <span data-ttu-id="b84cd-107">Alternatif olarak, sınıfının başına <xref:System.ServiceModel.ServiceContractAttribute> özniteliğini ve hizmetin istemcilerine sunulan yöntemlere <xref:System.ServiceModel.OperationContractAttribute> özniteliğini yerleştirerek doğrudan sınıfı ve sözleşmeyi oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b84cd-107">Alternatively, you can create the class and contract directly by placing the <xref:System.ServiceModel.ServiceContractAttribute> attribute on the class itself and the <xref:System.ServiceModel.OperationContractAttribute> attribute on the methods available to the clients of the service.</span></span>  
  
## <a name="creating-a-service-class"></a><span data-ttu-id="b84cd-108">Hizmet sınıfı oluşturma</span><span class="sxs-lookup"><span data-stu-id="b84cd-108">Creating a service class</span></span>  
 <span data-ttu-id="b84cd-109">Aşağıda ayrı olarak tanımlanmış `IMath` sözleşmesini uygulayan bir hizmetin örneği verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="b84cd-109">The following is an example of a service that implements an `IMath` contract that has been defined separately.</span></span>  
  
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
  
 <span data-ttu-id="b84cd-110">Alternatif olarak, bir hizmet bir sözleşmeyi doğrudan kullanıma sunabilir.</span><span class="sxs-lookup"><span data-stu-id="b84cd-110">Alternatively, a service can expose a contract directly.</span></span> <span data-ttu-id="b84cd-111">Aşağıda `MathService` sözleşmesinin tanımlandığı ve uyguladığı bir hizmet sınıfına bir örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="b84cd-111">The following is an example of a service class that defines and implements a `MathService` contract.</span></span>  
  
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
  
 <span data-ttu-id="b84cd-112">Sözleşme adları farklı olduğu için yukarıdaki hizmetlerin farklı sözleşmeleri kullanıma sunacağını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="b84cd-112">Note that the preceding services expose different contracts because the contract names are different.</span></span> <span data-ttu-id="b84cd-113">İlk durumda, sözleşmenin "`MathService`" olarak adlandırıldığından, ortaya çıkan sözleşme "`IMath`" olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="b84cd-113">In the first case, the exposed contract is named "`IMath`" while in the second case the contract is named "`MathService`".</span></span>  
  
 <span data-ttu-id="b84cd-114">Hizmet ve işlem uygulama düzeylerinde, eşzamanlılık ve örnek oluşturma gibi birkaç şey belirleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b84cd-114">You can set a few things at the service and operation implementation levels, such as concurrency and instancing.</span></span> <span data-ttu-id="b84cd-115">Daha fazla bilgi için bkz. [Hizmetleri tasarlama ve uygulama](designing-and-implementing-services.md).</span><span class="sxs-lookup"><span data-stu-id="b84cd-115">For more information, see [Designing and Implementing Services](designing-and-implementing-services.md).</span></span>  
  
 <span data-ttu-id="b84cd-116">Bir hizmet sözleşmesini uyguladıktan sonra, hizmet için bir veya daha fazla uç nokta oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b84cd-116">After implementing a service contract, you must create one or more endpoints for the service.</span></span> <span data-ttu-id="b84cd-117">Daha fazla bilgi için bkz. [Endpoint oluşturmaya genel bakış](endpoint-creation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="b84cd-117">For more information, see [Endpoint Creation Overview](endpoint-creation-overview.md).</span></span> <span data-ttu-id="b84cd-118">Bir hizmetin nasıl çalıştırılacağı hakkında daha fazla bilgi için bkz. [barındırma hizmetleri](hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="b84cd-118">For more information about how to run a service, see [Hosting Services](hosting-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b84cd-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b84cd-119">See also</span></span>

- [<span data-ttu-id="b84cd-120">Hizmetleri Tasarlama ve Uygulama</span><span class="sxs-lookup"><span data-stu-id="b84cd-120">Designing and Implementing Services</span></span>](designing-and-implementing-services.md)
- [<span data-ttu-id="b84cd-121">Nasıl yapılır: Anlaşma Sınıfı ile Hizmet Oluşturma</span><span class="sxs-lookup"><span data-stu-id="b84cd-121">How to: Create a Service with a Contract Class</span></span>](./feature-details/how-to-create-a-wcf-contract-with-a-class.md)
- [<span data-ttu-id="b84cd-122">Nasıl yapılır: Anlaşma Arabirimi ile Hizmet Oluşturma</span><span class="sxs-lookup"><span data-stu-id="b84cd-122">How to: Create a Service with a Contract Interface</span></span>](./feature-details/how-to-create-a-service-with-a-contract-interface.md)
- [<span data-ttu-id="b84cd-123">Hizmet Çalışma Zamanı Davranışını Belirtme</span><span class="sxs-lookup"><span data-stu-id="b84cd-123">Specifying Service Run-Time Behavior</span></span>](specifying-service-run-time-behavior.md)
