---
title: 'Nasıl yapılır: İstek-Yanıt Sözleşmesi Oluşturma'
ms.date: 03/30/2017
ms.assetid: 801d90da-3d45-4284-9c9f-56c8aadb4060
ms.openlocfilehash: 7a446db49dcc6a12b900292f1b19c9973835f2c1
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59327483"
---
# <a name="how-to-create-a-request-reply-contract"></a><span data-ttu-id="b1400-102">Nasıl yapılır: İstek-Yanıt Sözleşmesi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="b1400-102">How to: Create a Request-Reply Contract</span></span>
<span data-ttu-id="b1400-103">İstek-yanıt anlaşması yanıt döndüren bir yöntem belirtir.</span><span class="sxs-lookup"><span data-stu-id="b1400-103">A request-reply contract specifies a method that returns a reply.</span></span> <span data-ttu-id="b1400-104">Yanıtı gönderilir ve bu sözleşmenin koşullarına isteğine bağıntılı.</span><span class="sxs-lookup"><span data-stu-id="b1400-104">The reply must be sent and correlated to the request under the terms of this contract.</span></span> <span data-ttu-id="b1400-105">Bile yöntem hiç yanıt döndürür (`void` C# veya `Sub` Visual Basic'te), altyapıyı oluşturur ve çağırana bir boş ileti gönderir.</span><span class="sxs-lookup"><span data-stu-id="b1400-105">Even if the method returns no reply (`void` in C#, or a `Sub` in Visual Basic), the infrastructure creates and sends an empty message to the caller.</span></span> <span data-ttu-id="b1400-106">Bir boş bir yanıt iletisini göndermeyi önlemek için tek yönlü anlaşma işlemi için kullanın.</span><span class="sxs-lookup"><span data-stu-id="b1400-106">To prevent the sending of an empty reply message, use a one-way contract for the operation.</span></span>  
  
### <a name="to-create-a-request-reply-contract"></a><span data-ttu-id="b1400-107">İstek-yanıt anlaşması oluşturma</span><span class="sxs-lookup"><span data-stu-id="b1400-107">To create a request-reply contract</span></span>  
  
1. <span data-ttu-id="b1400-108">Bir arabirim, kendi seçtiğiniz programlama dilinde oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b1400-108">Create an interface in the programming language of your choice.</span></span>  
  
2. <span data-ttu-id="b1400-109">Uygulama <xref:System.ServiceModel.ServiceContractAttribute> özniteliği için arabirim.</span><span class="sxs-lookup"><span data-stu-id="b1400-109">Apply the <xref:System.ServiceModel.ServiceContractAttribute> attribute to the interface.</span></span>  
  
3. <span data-ttu-id="b1400-110">Uygulama <xref:System.ServiceModel.OperationContractAttribute> istemcileri çağırabilirsiniz her yönteme öznitelik.</span><span class="sxs-lookup"><span data-stu-id="b1400-110">Apply the <xref:System.ServiceModel.OperationContractAttribute> attribute to each method that clients can invoke.</span></span>  
  
4. <span data-ttu-id="b1400-111">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="b1400-111">Optional.</span></span> <span data-ttu-id="b1400-112">Değerini <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> özelliğini `true` bir boş bir yanıt iletisini göndermeyi önlemek için.</span><span class="sxs-lookup"><span data-stu-id="b1400-112">Set the value of the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property to `true` to prevent the sending of an empty reply message.</span></span> <span data-ttu-id="b1400-113">Varsayılan olarak, tüm işlemler istek-yanıt sözleşmeleriyle gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="b1400-113">By default, all operations are request-reply contracts.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b1400-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="b1400-114">Example</span></span>  
 <span data-ttu-id="b1400-115">Aşağıdaki örnek sağlayan bir hesap makinesi hizmet sözleşme tanımlayan `Add` ve `Subtract` yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="b1400-115">The following sample defines a contract for a calculator service that provides `Add` and `Subtract` methods.</span></span> <span data-ttu-id="b1400-116">`Multiply` Yöntemi değil sözleşmesinin bir parçası olarak işaretlenmediğinden <xref:System.ServiceModel.OperationContractAttribute> sınıfı ve bu nedenle, istemciler için erişilebilir değil.</span><span class="sxs-lookup"><span data-stu-id="b1400-116">The `Multiply` method is not part of the contract because it is not marked by the <xref:System.ServiceModel.OperationContractAttribute> class and so it is not accessible to clients.</span></span>  
  
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
  
-   <span data-ttu-id="b1400-117">İşlem sözleşmeleri belirtme hakkında daha fazla bilgi için bkz. <xref:System.ServiceModel.OperationContractAttribute> sınıfı ve <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="b1400-117">For more information about how to specify operation contracts, see the <xref:System.ServiceModel.OperationContractAttribute> class and the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property.</span></span>  
  
-   <span data-ttu-id="b1400-118">Uygulama <xref:System.ServiceModel.ServiceContractAttribute> ve <xref:System.ServiceModel.OperationContractAttribute> öznitelikleri hizmet dağıtıldıktan sonra bu hizmet sözleşmesi tanımları otomatik olarak oluşturulmasını Web Hizmetleri Açıklama Dili (WSDL) belgesinde sağlar.</span><span class="sxs-lookup"><span data-stu-id="b1400-118">Applying the <xref:System.ServiceModel.ServiceContractAttribute> and <xref:System.ServiceModel.OperationContractAttribute> attributes causes the automatic generation of service contract definitions in a Web Services Description Language (WSDL) document once the service is deployed.</span></span> <span data-ttu-id="b1400-119">Belge ekleyerek indirdiğiniz `?wsdl` HTTP temel adresi hizmeti.</span><span class="sxs-lookup"><span data-stu-id="b1400-119">The document is downloaded by appending `?wsdl` to the HTTP base address for the service.</span></span> <span data-ttu-id="b1400-120">Örneğin,</span><span class="sxs-lookup"><span data-stu-id="b1400-120">For example,</span></span> `http://microsoft/CalculatorService?wsdl`  
  
## <a name="see-also"></a><span data-ttu-id="b1400-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b1400-121">See also</span></span>

- <xref:System.ServiceModel.OperationContractAttribute>
- [<span data-ttu-id="b1400-122">Hizmet Sözleşmeleri Tasarlama</span><span class="sxs-lookup"><span data-stu-id="b1400-122">Designing Service Contracts</span></span>](../../../../docs/framework/wcf/designing-service-contracts.md)
- [<span data-ttu-id="b1400-123">Nasıl yapılır: Çift Yönlü Sözleşme Oluşturma</span><span class="sxs-lookup"><span data-stu-id="b1400-123">How to: Create a Duplex Contract</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)
