---
title: 'Nasıl yapılır: İstek-Yanıt Sözleşmesi Oluşturma'
ms.date: 03/30/2017
ms.assetid: 801d90da-3d45-4284-9c9f-56c8aadb4060
ms.openlocfilehash: 793f7214f8319e87c3e344990577841fc029bc55
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185024"
---
# <a name="how-to-create-a-request-reply-contract"></a><span data-ttu-id="4ddb8-102">Nasıl yapılır: İstek-Yanıt Sözleşmesi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="4ddb8-102">How to: Create a Request-Reply Contract</span></span>
<span data-ttu-id="4ddb8-103">İstek-yanıt sözleşmesi, yanıtı döndüren bir yöntem belirtir.</span><span class="sxs-lookup"><span data-stu-id="4ddb8-103">A request-reply contract specifies a method that returns a reply.</span></span> <span data-ttu-id="4ddb8-104">Yanıt gönderilmelidir ve bu sözleşmenin şartları altında istekle ilişkilendirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="4ddb8-104">The reply must be sent and correlated to the request under the terms of this contract.</span></span> <span data-ttu-id="4ddb8-105">Yöntem yanıt vermese`void` bile (C#veya `Sub` Visual Basic'te), altyapı oluşturur ve arayana boş bir ileti gönderir.</span><span class="sxs-lookup"><span data-stu-id="4ddb8-105">Even if the method returns no reply (`void` in C#, or a `Sub` in Visual Basic), the infrastructure creates and sends an empty message to the caller.</span></span> <span data-ttu-id="4ddb8-106">Boş bir yanıt iletisi gönderilmesini önlemek için işlem için tek yönlü bir sözleşme kullanın.</span><span class="sxs-lookup"><span data-stu-id="4ddb8-106">To prevent the sending of an empty reply message, use a one-way contract for the operation.</span></span>  
  
### <a name="to-create-a-request-reply-contract"></a><span data-ttu-id="4ddb8-107">İstek-yanıt sözleşmesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="4ddb8-107">To create a request-reply contract</span></span>  
  
1. <span data-ttu-id="4ddb8-108">Seçtiğiniz programlama dilinde bir arayüz oluşturun.</span><span class="sxs-lookup"><span data-stu-id="4ddb8-108">Create an interface in the programming language of your choice.</span></span>  
  
2. <span data-ttu-id="4ddb8-109"><xref:System.ServiceModel.ServiceContractAttribute> Özniteliği arabirime uygulayın.</span><span class="sxs-lookup"><span data-stu-id="4ddb8-109">Apply the <xref:System.ServiceModel.ServiceContractAttribute> attribute to the interface.</span></span>  
  
3. <span data-ttu-id="4ddb8-110">İstemcilerin <xref:System.ServiceModel.OperationContractAttribute> çağırabileceği her yönteme öznitelik uygulayın.</span><span class="sxs-lookup"><span data-stu-id="4ddb8-110">Apply the <xref:System.ServiceModel.OperationContractAttribute> attribute to each method that clients can invoke.</span></span>  
  
4. <span data-ttu-id="4ddb8-111">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="4ddb8-111">Optional.</span></span> <span data-ttu-id="4ddb8-112">Boş bir yanıt <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> iletisi gönderilmesini önlemek için `true` özelliğin değerini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="4ddb8-112">Set the value of the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property to `true` to prevent the sending of an empty reply message.</span></span> <span data-ttu-id="4ddb8-113">Varsayılan olarak, tüm işlemler istek yanıtlama sözleşmeleridir.</span><span class="sxs-lookup"><span data-stu-id="4ddb8-113">By default, all operations are request-reply contracts.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4ddb8-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="4ddb8-114">Example</span></span>  
 <span data-ttu-id="4ddb8-115">Aşağıdaki örnek, sağlayan `Add` ve `Subtract` yöntemler sağlayan bir hesap makinesi hizmeti için bir sözleşme tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4ddb8-115">The following sample defines a contract for a calculator service that provides `Add` and `Subtract` methods.</span></span> <span data-ttu-id="4ddb8-116">Yöntem, `Multiply` <xref:System.ServiceModel.OperationContractAttribute> sınıf tarafından işaretlenmediği ve bu nedenle istemciler tarafından erişilemediği için sözleşmenin bir parçası değildir.</span><span class="sxs-lookup"><span data-stu-id="4ddb8-116">The `Multiply` method is not part of the contract because it is not marked by the <xref:System.ServiceModel.OperationContractAttribute> class and so it is not accessible to clients.</span></span>  
  
```csharp
using System.ServiceModel;

[ServiceContract]
public interface ICalculator
{
    [OperationContract]
    // It would be equivalent to write explicitly:
    // [OperationContract(IsOneWay=false)]
    int Add(int a, int b);

    [OperationContract]
    int Subtract(int a, int b);

    int Multiply(int a, int b)
}
```
  
- <span data-ttu-id="4ddb8-117">Çalışma sözleşmelerinin nasıl belirtilen hakkında <xref:System.ServiceModel.OperationContractAttribute> daha <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> fazla bilgi için sınıfa ve özelliğine bakın.</span><span class="sxs-lookup"><span data-stu-id="4ddb8-117">For more information about how to specify operation contracts, see the <xref:System.ServiceModel.OperationContractAttribute> class and the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property.</span></span>  
  
- <span data-ttu-id="4ddb8-118">Hizmet <xref:System.ServiceModel.ServiceContractAttribute> <xref:System.ServiceModel.OperationContractAttribute> dağıtıldıktan sonra web hizmetleri açıklama dili (WSDL) belgesinde otomatik hizmet sözleşmesi tanımlarının uygulanmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="4ddb8-118">Applying the <xref:System.ServiceModel.ServiceContractAttribute> and <xref:System.ServiceModel.OperationContractAttribute> attributes causes the automatic generation of service contract definitions in a Web Services Description Language (WSDL) document once the service is deployed.</span></span> <span data-ttu-id="4ddb8-119">Belge, hizmetin HTTP `?wsdl` temel adresine eklenerek indirilir.</span><span class="sxs-lookup"><span data-stu-id="4ddb8-119">The document is downloaded by appending `?wsdl` to the HTTP base address for the service.</span></span> <span data-ttu-id="4ddb8-120">Örneğin, `http://microsoft/CalculatorService?wsdl`</span><span class="sxs-lookup"><span data-stu-id="4ddb8-120">For example, `http://microsoft/CalculatorService?wsdl`</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ddb8-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4ddb8-121">See also</span></span>

- <xref:System.ServiceModel.OperationContractAttribute>
- [<span data-ttu-id="4ddb8-122">Hizmet Sözleşmeleri Tasarlama</span><span class="sxs-lookup"><span data-stu-id="4ddb8-122">Designing Service Contracts</span></span>](../../../../docs/framework/wcf/designing-service-contracts.md)
- [<span data-ttu-id="4ddb8-123">Nasıl yapılır: Çift Yönlü Sözleşme Oluşturma</span><span class="sxs-lookup"><span data-stu-id="4ddb8-123">How to: Create a Duplex Contract</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)
