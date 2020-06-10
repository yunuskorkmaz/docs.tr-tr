---
title: 'Nasıl yapılır: İstek-Yanıt Sözleşmesi Oluşturma'
ms.date: 03/30/2017
ms.assetid: 801d90da-3d45-4284-9c9f-56c8aadb4060
ms.openlocfilehash: 8a09c265c77edc584b591477e64314f1e76e332b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593444"
---
# <a name="how-to-create-a-request-reply-contract"></a><span data-ttu-id="810f9-102">Nasıl yapılır: İstek-Yanıt Sözleşmesi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="810f9-102">How to: Create a Request-Reply Contract</span></span>
<span data-ttu-id="810f9-103">İstek-yanıt sözleşmesi, yanıt döndüren bir yöntemi belirtir.</span><span class="sxs-lookup"><span data-stu-id="810f9-103">A request-reply contract specifies a method that returns a reply.</span></span> <span data-ttu-id="810f9-104">Yanıt gönderilmesi ve bu sözleşmenin koşullarına göre istekle bağıntılı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="810f9-104">The reply must be sent and correlated to the request under the terms of this contract.</span></span> <span data-ttu-id="810f9-105">Yöntem yanıt vermez ( `void` C# veya `Sub` Visual Basic içinde), altyapı çağırana boş bir ileti oluşturur ve gönderir.</span><span class="sxs-lookup"><span data-stu-id="810f9-105">Even if the method returns no reply (`void` in C#, or a `Sub` in Visual Basic), the infrastructure creates and sends an empty message to the caller.</span></span> <span data-ttu-id="810f9-106">Boş bir yanıt iletisi gönderilmesini engellemek için, işlem için tek yönlü bir sözleşme kullanın.</span><span class="sxs-lookup"><span data-stu-id="810f9-106">To prevent the sending of an empty reply message, use a one-way contract for the operation.</span></span>  
  
### <a name="to-create-a-request-reply-contract"></a><span data-ttu-id="810f9-107">İstek-yanıt sözleşmesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="810f9-107">To create a request-reply contract</span></span>  
  
1. <span data-ttu-id="810f9-108">Seçtiğiniz programlama dilinde bir arabirim oluşturun.</span><span class="sxs-lookup"><span data-stu-id="810f9-108">Create an interface in the programming language of your choice.</span></span>  
  
2. <span data-ttu-id="810f9-109"><xref:System.ServiceModel.ServiceContractAttribute>Özniteliğini arabirimine uygulayın.</span><span class="sxs-lookup"><span data-stu-id="810f9-109">Apply the <xref:System.ServiceModel.ServiceContractAttribute> attribute to the interface.</span></span>  
  
3. <span data-ttu-id="810f9-110">Özniteliği, <xref:System.ServiceModel.OperationContractAttribute> istemcilerin çağırabileceği her metoda uygulayın.</span><span class="sxs-lookup"><span data-stu-id="810f9-110">Apply the <xref:System.ServiceModel.OperationContractAttribute> attribute to each method that clients can invoke.</span></span>  
  
4. <span data-ttu-id="810f9-111">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="810f9-111">Optional.</span></span> <span data-ttu-id="810f9-112"><xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> `true` Boş bir yanıt iletisi gönderilmesini engellemek için özelliğinin değerini olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="810f9-112">Set the value of the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property to `true` to prevent the sending of an empty reply message.</span></span> <span data-ttu-id="810f9-113">Varsayılan olarak, tüm işlemler istek-yanıt sözleşmeleri ' dir.</span><span class="sxs-lookup"><span data-stu-id="810f9-113">By default, all operations are request-reply contracts.</span></span>  
  
## <a name="example"></a><span data-ttu-id="810f9-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="810f9-114">Example</span></span>  
 <span data-ttu-id="810f9-115">Aşağıdaki örnek, ve yöntemleri sağlayan bir Hesaplayıcı hizmeti için bir sözleşme tanımlar `Add` `Subtract` .</span><span class="sxs-lookup"><span data-stu-id="810f9-115">The following sample defines a contract for a calculator service that provides `Add` and `Subtract` methods.</span></span> <span data-ttu-id="810f9-116">`Multiply`Yöntem, sınıf tarafından işaretlenmediği <xref:System.ServiceModel.OperationContractAttribute> ve istemciler tarafından erişilemediği için sözleşmenin bir parçası değil.</span><span class="sxs-lookup"><span data-stu-id="810f9-116">The `Multiply` method is not part of the contract because it is not marked by the <xref:System.ServiceModel.OperationContractAttribute> class and so it is not accessible to clients.</span></span>  
  
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
  
- <span data-ttu-id="810f9-117">İşlem sözleşmelerini belirtme hakkında daha fazla bilgi için bkz <xref:System.ServiceModel.OperationContractAttribute> . sınıfı ve <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="810f9-117">For more information about how to specify operation contracts, see the <xref:System.ServiceModel.OperationContractAttribute> class and the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property.</span></span>  
  
- <span data-ttu-id="810f9-118"><xref:System.ServiceModel.ServiceContractAttribute>Ve özniteliklerinin uygulanması, <xref:System.ServiceModel.OperationContractAttribute> hizmet dağıtıldıktan sonra bir Web Hizmetleri Açıklama DILI (wsdl) belgesinde hizmet sözleşmesi tanımlarının otomatik olarak oluşturulmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="810f9-118">Applying the <xref:System.ServiceModel.ServiceContractAttribute> and <xref:System.ServiceModel.OperationContractAttribute> attributes causes the automatic generation of service contract definitions in a Web Services Description Language (WSDL) document once the service is deployed.</span></span> <span data-ttu-id="810f9-119">Belge, `?wsdl` HIZMETIN http temel adresine eklenerek indirilir.</span><span class="sxs-lookup"><span data-stu-id="810f9-119">The document is downloaded by appending `?wsdl` to the HTTP base address for the service.</span></span> <span data-ttu-id="810f9-120">Örneğin, `http://microsoft/CalculatorService?wsdl`</span><span class="sxs-lookup"><span data-stu-id="810f9-120">For example, `http://microsoft/CalculatorService?wsdl`</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="810f9-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="810f9-121">See also</span></span>

- <xref:System.ServiceModel.OperationContractAttribute>
- [<span data-ttu-id="810f9-122">Hizmet Sözleşmeleri Tasarlama</span><span class="sxs-lookup"><span data-stu-id="810f9-122">Designing Service Contracts</span></span>](../designing-service-contracts.md)
- [<span data-ttu-id="810f9-123">Nasıl yapılır: Çift Yönlü Sözleşme Oluşturma</span><span class="sxs-lookup"><span data-stu-id="810f9-123">How to: Create a Duplex Contract</span></span>](how-to-create-a-duplex-contract.md)
