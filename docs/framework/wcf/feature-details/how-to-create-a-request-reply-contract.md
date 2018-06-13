---
title: 'Nasıl yapılır: İstek-Yanıt Sözleşmesi Oluşturma'
ms.date: 03/30/2017
ms.assetid: 801d90da-3d45-4284-9c9f-56c8aadb4060
ms.openlocfilehash: 76a3bbb9415a34218896bc561066c7ac4a30e6b9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33489579"
---
# <a name="how-to-create-a-request-reply-contract"></a><span data-ttu-id="f95bb-102">Nasıl yapılır: İstek-Yanıt Sözleşmesi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="f95bb-102">How to: Create a Request-Reply Contract</span></span>
<span data-ttu-id="f95bb-103">İstek-yanıt sözleşmesi yanıt döndüren bir yöntem belirtir.</span><span class="sxs-lookup"><span data-stu-id="f95bb-103">A request-reply contract specifies a method that returns a reply.</span></span> <span data-ttu-id="f95bb-104">Yanıt gönderilir ve bu sözleşmenin koşulları altında isteğine bağıntılı.</span><span class="sxs-lookup"><span data-stu-id="f95bb-104">The reply must be sent and correlated to the request under the terms of this contract.</span></span> <span data-ttu-id="f95bb-105">Yanıt yöntem olsa bile (`void` C# ' ta, veya bir `Sub` Visual Basic'te), altyapı oluşturur ve çağırana boş iletisi gönderir.</span><span class="sxs-lookup"><span data-stu-id="f95bb-105">Even if the method returns no reply (`void` in C#, or a `Sub` in Visual Basic), the infrastructure creates and sends an empty message to the caller.</span></span> <span data-ttu-id="f95bb-106">Bir boş yanıt iletisini göndermeyi önlemek için işlem için tek yönlü sözleşme kullanın.</span><span class="sxs-lookup"><span data-stu-id="f95bb-106">To prevent the sending of an empty reply message, use a one-way contract for the operation.</span></span>  
  
### <a name="to-create-a-request-reply-contract"></a><span data-ttu-id="f95bb-107">İstek-yanıt sözleşmesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="f95bb-107">To create a request-reply contract</span></span>  
  
1.  <span data-ttu-id="f95bb-108">Arabirim tercih ettiğiniz programlama dilinde oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f95bb-108">Create an interface in the programming language of your choice.</span></span>  
  
2.  <span data-ttu-id="f95bb-109">Uygulama <xref:System.ServiceModel.ServiceContractAttribute> özniteliği için arabirim.</span><span class="sxs-lookup"><span data-stu-id="f95bb-109">Apply the <xref:System.ServiceModel.ServiceContractAttribute> attribute to the interface.</span></span>  
  
3.  <span data-ttu-id="f95bb-110">Uygulama <xref:System.ServiceModel.OperationContractAttribute> özniteliği istemcileri çağırabileceği her yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f95bb-110">Apply the <xref:System.ServiceModel.OperationContractAttribute> attribute to each method that clients can invoke.</span></span>  
  
4.  <span data-ttu-id="f95bb-111">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="f95bb-111">Optional.</span></span> <span data-ttu-id="f95bb-112">Değerini <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> özelliğine `true` bir boş yanıt iletisini göndermeyi önlemek için.</span><span class="sxs-lookup"><span data-stu-id="f95bb-112">Set the value of the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property to `true` to prevent the sending of an empty reply message.</span></span> <span data-ttu-id="f95bb-113">Varsayılan olarak, tüm, istek-yanıt sözleşmeleriyle işlemleridir.</span><span class="sxs-lookup"><span data-stu-id="f95bb-113">By default, all operations are request-reply contracts.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f95bb-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="f95bb-114">Example</span></span>  
 <span data-ttu-id="f95bb-115">Aşağıdaki örnek sağlayan hesaplayıcı hizmet için bir sözleşmede tanımlar `Add` ve `Subtract` yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="f95bb-115">The following sample defines a contract for a calculator service that provides `Add` and `Subtract` methods.</span></span> <span data-ttu-id="f95bb-116">`Multiply` Yöntemi değil sözleşmesinin bir parçası olarak işaretlenmediğinden <xref:System.ServiceModel.OperationContractAttribute> sınıfı ve böylece bu istemciler için erişilebilir değil.</span><span class="sxs-lookup"><span data-stu-id="f95bb-116">The `Multiply` method is not part of the contract because it is not marked by the <xref:System.ServiceModel.OperationContractAttribute> class and so it is not accessible to clients.</span></span>  
  
```
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
  
-   <span data-ttu-id="f95bb-117">İşlemi sözleşmeleri belirtme hakkında daha fazla bilgi için bkz: <xref:System.ServiceModel.OperationContractAttribute> sınıfı ve <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="f95bb-117">For more information about how to specify operation contracts, see the <xref:System.ServiceModel.OperationContractAttribute> class and the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property.</span></span>  
  
-   <span data-ttu-id="f95bb-118">Uygulama <xref:System.ServiceModel.ServiceContractAttribute> ve <xref:System.ServiceModel.OperationContractAttribute> öznitelikleri neden olan hizmet sözleşmesi tanımları otomatik olarak oluşturulmasını Web Hizmetleri Açıklama Dili (WSDL) belgede hizmet dağıtıldıktan sonra.</span><span class="sxs-lookup"><span data-stu-id="f95bb-118">Applying the <xref:System.ServiceModel.ServiceContractAttribute> and <xref:System.ServiceModel.OperationContractAttribute> attributes causes the automatic generation of service contract definitions in a Web Services Description Language (WSDL) document once the service is deployed.</span></span> <span data-ttu-id="f95bb-119">Belge ekleyerek karşıdan `?wsdl` HTTP temel adresi hizmeti.</span><span class="sxs-lookup"><span data-stu-id="f95bb-119">The document is downloaded by appending `?wsdl` to the HTTP base address for the service.</span></span> <span data-ttu-id="f95bb-120">Örneğin, `http://microsoft/CalculatorService?wsdl`</span><span class="sxs-lookup"><span data-stu-id="f95bb-120">For example, `http://microsoft/CalculatorService?wsdl`</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f95bb-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f95bb-121">See Also</span></span>  
 <xref:System.ServiceModel.OperationContractAttribute>  
 [<span data-ttu-id="f95bb-122">Hizmet Sözleşmeleri Tasarlama</span><span class="sxs-lookup"><span data-stu-id="f95bb-122">Designing Service Contracts</span></span>](../../../../docs/framework/wcf/designing-service-contracts.md)  
 [<span data-ttu-id="f95bb-123">Nasıl yapılır: Çift Yönlü Anlaşma Oluşturma</span><span class="sxs-lookup"><span data-stu-id="f95bb-123">How to: Create a Duplex Contract</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)
