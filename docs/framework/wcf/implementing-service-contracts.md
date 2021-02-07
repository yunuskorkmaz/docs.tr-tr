---
description: 'Daha fazla bilgi edinin: hizmet sözleşmelerini uygulama'
title: Hizmet Sözleşmelerini Uygulama
ms.date: 03/30/2017
helpviewer_keywords:
- implementing service contracts [WCF]
ms.assetid: aefb6f56-47e3-4f24-ab0a-9bc07bf9885f
ms.openlocfilehash: 4510c9e7b9ea3a98a37d528af4064f0e73bea89b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99752502"
---
# <a name="implementing-service-contracts"></a><span data-ttu-id="11ce5-103">Hizmet Sözleşmelerini Uygulama</span><span class="sxs-lookup"><span data-stu-id="11ce5-103">Implementing Service Contracts</span></span>

<span data-ttu-id="11ce5-104">Hizmet, bir veya daha fazla bitiş noktasında istemciler için kullanılabilir işlevselliği kullanıma sunan bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="11ce5-104">A service is a class that exposes functionality available to clients at one or more endpoints.</span></span> <span data-ttu-id="11ce5-105">Bir hizmet oluşturmak için, bir Windows Communication Foundation (WCF) sözleşmesi uygulayan bir sınıf yazın.</span><span class="sxs-lookup"><span data-stu-id="11ce5-105">To create a service, write a class that implements a Windows Communication Foundation (WCF) contract.</span></span> <span data-ttu-id="11ce5-106">Bunu iki yoldan birini kullanarak yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="11ce5-106">You can do this in one of two ways.</span></span> <span data-ttu-id="11ce5-107">Sözleşmeyi ayrı bir arabirim olarak tanımlayabilir ve ardından bu arabirimi uygulayan bir sınıf oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="11ce5-107">You can define the contract separately as an interface and then create a class that implements that interface.</span></span> <span data-ttu-id="11ce5-108">Alternatif olarak, doğrudan <xref:System.ServiceModel.ServiceContractAttribute> sınıf üzerine özniteliği ve <xref:System.ServiceModel.OperationContractAttribute> hizmetin istemcilerine sunulan yöntemlere özniteliği yerleştirerek sınıfı ve sözleşmeyi doğrudan oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="11ce5-108">Alternatively, you can create the class and contract directly by placing the <xref:System.ServiceModel.ServiceContractAttribute> attribute on the class itself and the <xref:System.ServiceModel.OperationContractAttribute> attribute on the methods available to the clients of the service.</span></span>  
  
## <a name="creating-a-service-class"></a><span data-ttu-id="11ce5-109">Hizmet sınıfı oluşturma</span><span class="sxs-lookup"><span data-stu-id="11ce5-109">Creating a service class</span></span>  

 <span data-ttu-id="11ce5-110">Aşağıda ayrı olarak tanımlanmış bir sözleşmeyi uygulayan bir hizmetin örneği verilmiştir `IMath` .</span><span class="sxs-lookup"><span data-stu-id="11ce5-110">The following is an example of a service that implements an `IMath` contract that has been defined separately.</span></span>  
  
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
  
 <span data-ttu-id="11ce5-111">Alternatif olarak, bir hizmet bir sözleşmeyi doğrudan kullanıma sunabilir.</span><span class="sxs-lookup"><span data-stu-id="11ce5-111">Alternatively, a service can expose a contract directly.</span></span> <span data-ttu-id="11ce5-112">Aşağıda, bir sözleşmeyi tanımlayan ve uygulayan bir hizmet sınıfına bir örnek verilmiştir `MathService` .</span><span class="sxs-lookup"><span data-stu-id="11ce5-112">The following is an example of a service class that defines and implements a `MathService` contract.</span></span>  
  
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
  
 <span data-ttu-id="11ce5-113">Sözleşme adları farklı olduğu için yukarıdaki hizmetlerin farklı sözleşmeleri kullanıma sunacağını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="11ce5-113">Note that the preceding services expose different contracts because the contract names are different.</span></span> <span data-ttu-id="11ce5-114">İlk durumda, "" `IMath` adlı sözleşmenin ikinci çalışmasında "" olarak adlandırılan sözleşme "" olarak adlandırılmıştır `MathService` .</span><span class="sxs-lookup"><span data-stu-id="11ce5-114">In the first case, the exposed contract is named "`IMath`" while in the second case the contract is named "`MathService`".</span></span>  
  
 <span data-ttu-id="11ce5-115">Hizmet ve işlem uygulama düzeylerinde, eşzamanlılık ve örnek oluşturma gibi birkaç şey belirleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="11ce5-115">You can set a few things at the service and operation implementation levels, such as concurrency and instancing.</span></span> <span data-ttu-id="11ce5-116">Daha fazla bilgi için bkz. [Hizmetleri tasarlama ve uygulama](designing-and-implementing-services.md).</span><span class="sxs-lookup"><span data-stu-id="11ce5-116">For more information, see [Designing and Implementing Services](designing-and-implementing-services.md).</span></span>  
  
 <span data-ttu-id="11ce5-117">Bir hizmet sözleşmesini uyguladıktan sonra, hizmet için bir veya daha fazla uç nokta oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="11ce5-117">After implementing a service contract, you must create one or more endpoints for the service.</span></span> <span data-ttu-id="11ce5-118">Daha fazla bilgi için bkz. [Endpoint oluşturmaya genel bakış](endpoint-creation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="11ce5-118">For more information, see [Endpoint Creation Overview](endpoint-creation-overview.md).</span></span> <span data-ttu-id="11ce5-119">Bir hizmetin nasıl çalıştırılacağı hakkında daha fazla bilgi için bkz. [barındırma hizmetleri](hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="11ce5-119">For more information about how to run a service, see [Hosting Services](hosting-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11ce5-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="11ce5-120">See also</span></span>

- [<span data-ttu-id="11ce5-121">Hizmetleri Tasarlama ve Uygulama</span><span class="sxs-lookup"><span data-stu-id="11ce5-121">Designing and Implementing Services</span></span>](designing-and-implementing-services.md)
- [<span data-ttu-id="11ce5-122">Nasıl yapılır: Anlaşma Sınıfı ile Hizmet Oluşturma</span><span class="sxs-lookup"><span data-stu-id="11ce5-122">How to: Create a Service with a Contract Class</span></span>](./feature-details/how-to-create-a-wcf-contract-with-a-class.md)
- [<span data-ttu-id="11ce5-123">Nasıl yapılır: Sözleşme Arabirimi ile Hizmet Oluşturma</span><span class="sxs-lookup"><span data-stu-id="11ce5-123">How to: Create a Service with a Contract Interface</span></span>](./feature-details/how-to-create-a-service-with-a-contract-interface.md)
- [<span data-ttu-id="11ce5-124">Hizmet Çalışma Zamanı Davranışını Belirtme</span><span class="sxs-lookup"><span data-stu-id="11ce5-124">Specifying Service Run-Time Behavior</span></span>](specifying-service-run-time-behavior.md)
