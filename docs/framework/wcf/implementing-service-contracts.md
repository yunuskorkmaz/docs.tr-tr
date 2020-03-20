---
title: Hizmet Sözleşmelerini Uygulama
ms.date: 03/30/2017
helpviewer_keywords:
- implementing service contracts [WCF]
ms.assetid: aefb6f56-47e3-4f24-ab0a-9bc07bf9885f
ms.openlocfilehash: aefe146a8941d98d7d9138e4ece83c330c967034
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183998"
---
# <a name="implementing-service-contracts"></a><span data-ttu-id="713ef-102">Hizmet Sözleşmelerini Uygulama</span><span class="sxs-lookup"><span data-stu-id="713ef-102">Implementing Service Contracts</span></span>
<span data-ttu-id="713ef-103">Hizmet, istemcilerin bir veya daha fazla uç noktada kullanabileceği işlevselliği ortaya çıkaran bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="713ef-103">A service is a class that exposes functionality available to clients at one or more endpoints.</span></span> <span data-ttu-id="713ef-104">Bir hizmet oluşturmak için, Windows Communication Foundation (WCF) sözleşmesini uygulayan bir sınıf yazın.</span><span class="sxs-lookup"><span data-stu-id="713ef-104">To create a service, write a class that implements a Windows Communication Foundation (WCF) contract.</span></span> <span data-ttu-id="713ef-105">Bunu iki yoldan birini kullanarak yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="713ef-105">You can do this in one of two ways.</span></span> <span data-ttu-id="713ef-106">Sözleşmeyi ayrı ayrı arabirim olarak tanımlayabilir ve ardından bu arabirimi uygulayan bir sınıf oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="713ef-106">You can define the contract separately as an interface and then create a class that implements that interface.</span></span> <span data-ttu-id="713ef-107">Alternatif olarak, sınıfın kendisine özniteliği ve <xref:System.ServiceModel.ServiceContractAttribute> hizmet istemcileri için kullanılabilir <xref:System.ServiceModel.OperationContractAttribute> yöntemlere öznitelik yerleştirerek sınıf ve sözleşme doğrudan oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="713ef-107">Alternatively, you can create the class and contract directly by placing the <xref:System.ServiceModel.ServiceContractAttribute> attribute on the class itself and the <xref:System.ServiceModel.OperationContractAttribute> attribute on the methods available to the clients of the service.</span></span>  
  
## <a name="creating-a-service-class"></a><span data-ttu-id="713ef-108">Hizmet sınıfı oluşturma</span><span class="sxs-lookup"><span data-stu-id="713ef-108">Creating a service class</span></span>  
 <span data-ttu-id="713ef-109">Aşağıda, ayrı olarak tanımlanmış bir sözleşme `IMath` uygulayan bir hizmet örneği verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="713ef-109">The following is an example of a service that implements an `IMath` contract that has been defined separately.</span></span>  
  
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
  
 <span data-ttu-id="713ef-110">Alternatif olarak, bir hizmet doğrudan bir sözleşme ortaya çıkarabilir.</span><span class="sxs-lookup"><span data-stu-id="713ef-110">Alternatively, a service can expose a contract directly.</span></span> <span data-ttu-id="713ef-111">Aşağıda, bir `MathService` sözleşmetanımlayan ve uygulayan bir hizmet sınıfı örneği verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="713ef-111">The following is an example of a service class that defines and implements a `MathService` contract.</span></span>  
  
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
  
 <span data-ttu-id="713ef-112">Sözleşme adları farklı olduğundan, önceki hizmetlerin farklı sözleşmeler ortaya çıkardığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="713ef-112">Note that the preceding services expose different contracts because the contract names are different.</span></span> <span data-ttu-id="713ef-113">İlk durumda, açıkta kalan sözleşme`IMath`" " olarak adlandırılırken,`MathService`ikinci durumda sözleşme " " olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="713ef-113">In the first case, the exposed contract is named "`IMath`" while in the second case the contract is named "`MathService`".</span></span>  
  
 <span data-ttu-id="713ef-114">Eşzamanlılık ve instancing gibi hizmet ve işlem uygulama düzeylerinde birkaç şey ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="713ef-114">You can set a few things at the service and operation implementation levels, such as concurrency and instancing.</span></span> <span data-ttu-id="713ef-115">Daha fazla bilgi için [bkz.](designing-and-implementing-services.md)</span><span class="sxs-lookup"><span data-stu-id="713ef-115">For more information, see [Designing and Implementing Services](designing-and-implementing-services.md).</span></span>  
  
 <span data-ttu-id="713ef-116">Bir hizmet sözleşmesi uyguladıktan sonra, hizmet için bir veya daha fazla uç nokta oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="713ef-116">After implementing a service contract, you must create one or more endpoints for the service.</span></span> <span data-ttu-id="713ef-117">Daha fazla bilgi için Bkz. [Endpoint Oluşturma Genel Bakış.](endpoint-creation-overview.md)</span><span class="sxs-lookup"><span data-stu-id="713ef-117">For more information, see [Endpoint Creation Overview](endpoint-creation-overview.md).</span></span> <span data-ttu-id="713ef-118">Bir hizmeti nasıl çalıştırabileceğiniz hakkında daha fazla bilgi için [Barındırma Hizmetleri'ne](hosting-services.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="713ef-118">For more information about how to run a service, see [Hosting Services](hosting-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="713ef-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="713ef-119">See also</span></span>

- [<span data-ttu-id="713ef-120">Hizmetleri Tasarlama ve Uygulama</span><span class="sxs-lookup"><span data-stu-id="713ef-120">Designing and Implementing Services</span></span>](designing-and-implementing-services.md)
- [<span data-ttu-id="713ef-121">Nasıl yapılır: Anlaşma Sınıfı ile Hizmet Oluşturma</span><span class="sxs-lookup"><span data-stu-id="713ef-121">How to: Create a Service with a Contract Class</span></span>](./feature-details/how-to-create-a-wcf-contract-with-a-class.md)
- [<span data-ttu-id="713ef-122">Nasıl yapılır: Anlaşma Arabirimi ile Hizmet Oluşturma</span><span class="sxs-lookup"><span data-stu-id="713ef-122">How to: Create a Service with a Contract Interface</span></span>](./feature-details/how-to-create-a-service-with-a-contract-interface.md)
- [<span data-ttu-id="713ef-123">Hizmet Çalışma Zamanı Davranışını Belirtme</span><span class="sxs-lookup"><span data-stu-id="713ef-123">Specifying Service Run-Time Behavior</span></span>](specifying-service-run-time-behavior.md)
