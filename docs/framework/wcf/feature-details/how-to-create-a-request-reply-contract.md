---
title: "Nasıl yapılır: İstek-Yanıt Sözleşmesi Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 801d90da-3d45-4284-9c9f-56c8aadb4060
caps.latest.revision: "19"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1ad32807227844e379dd44e63c61b3ff15d2a2ef
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-request-reply-contract"></a><span data-ttu-id="4568e-102">Nasıl yapılır: İstek-Yanıt Sözleşmesi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="4568e-102">How to: Create a Request-Reply Contract</span></span>
<span data-ttu-id="4568e-103">İstek-yanıt sözleşmesi yanıt döndüren bir yöntem belirtir.</span><span class="sxs-lookup"><span data-stu-id="4568e-103">A request-reply contract specifies a method that returns a reply.</span></span> <span data-ttu-id="4568e-104">Yanıt gönderilir ve bu sözleşmenin koşulları altında isteğine bağıntılı.</span><span class="sxs-lookup"><span data-stu-id="4568e-104">The reply must be sent and correlated to the request under the terms of this contract.</span></span> <span data-ttu-id="4568e-105">Yanıt yöntem olsa bile (`void` C# ' ta, veya bir `Sub` Visual Basic'te), altyapı oluşturur ve çağırana boş iletisi gönderir.</span><span class="sxs-lookup"><span data-stu-id="4568e-105">Even if the method returns no reply (`void` in C#, or a `Sub` in Visual Basic), the infrastructure creates and sends an empty message to the caller.</span></span> <span data-ttu-id="4568e-106">Bir boş yanıt iletisini göndermeyi önlemek için işlem için tek yönlü sözleşme kullanın.</span><span class="sxs-lookup"><span data-stu-id="4568e-106">To prevent the sending of an empty reply message, use a one-way contract for the operation.</span></span>  
  
### <a name="to-create-a-request-reply-contract"></a><span data-ttu-id="4568e-107">İstek-yanıt sözleşmesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="4568e-107">To create a request-reply contract</span></span>  
  
1.  <span data-ttu-id="4568e-108">Arabirim tercih ettiğiniz programlama dilinde oluşturun.</span><span class="sxs-lookup"><span data-stu-id="4568e-108">Create an interface in the programming language of your choice.</span></span>  
  
2.  <span data-ttu-id="4568e-109">Uygulama <xref:System.ServiceModel.ServiceContractAttribute> özniteliği için arabirim.</span><span class="sxs-lookup"><span data-stu-id="4568e-109">Apply the <xref:System.ServiceModel.ServiceContractAttribute> attribute to the interface.</span></span>  
  
3.  <span data-ttu-id="4568e-110">Uygulama <xref:System.ServiceModel.OperationContractAttribute> özniteliği istemcileri çağırabileceği her yöntemi.</span><span class="sxs-lookup"><span data-stu-id="4568e-110">Apply the <xref:System.ServiceModel.OperationContractAttribute> attribute to each method that clients can invoke.</span></span>  
  
4.  <span data-ttu-id="4568e-111">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="4568e-111">Optional.</span></span> <span data-ttu-id="4568e-112">Değerini <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> özelliğine `true` bir boş yanıt iletisini göndermeyi önlemek için.</span><span class="sxs-lookup"><span data-stu-id="4568e-112">Set the value of the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property to `true` to prevent the sending of an empty reply message.</span></span> <span data-ttu-id="4568e-113">Varsayılan olarak, tüm, istek-yanıt sözleşmeleriyle işlemleridir.</span><span class="sxs-lookup"><span data-stu-id="4568e-113">By default, all operations are request-reply contracts.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4568e-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="4568e-114">Example</span></span>  
 <span data-ttu-id="4568e-115">Aşağıdaki örnek sağlayan hesaplayıcı hizmet için bir sözleşmede tanımlar `Add` ve `Subtract` yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="4568e-115">The following sample defines a contract for a calculator service that provides `Add` and `Subtract` methods.</span></span> <span data-ttu-id="4568e-116">`Multiply` Yöntemi değil sözleşmesinin bir parçası olarak işaretlenmediğinden <xref:System.ServiceModel.OperationContractAttribute> sınıfı ve böylece bu istemciler için erişilebilir değil.</span><span class="sxs-lookup"><span data-stu-id="4568e-116">The `Multiply` method is not part of the contract because it is not marked by the <xref:System.ServiceModel.OperationContractAttribute> class and so it is not accessible to clients.</span></span>  
  
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
  
-   [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="4568e-117">işlemi sözleşmeleri belirtin nasıl <xref:System.ServiceModel.OperationContractAttribute> sınıfı ve <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="4568e-117"> how to specify operation contracts, see the <xref:System.ServiceModel.OperationContractAttribute> class and the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property.</span></span>  
  
-   <span data-ttu-id="4568e-118">Uygulama <xref:System.ServiceModel.ServiceContractAttribute> ve <xref:System.ServiceModel.OperationContractAttribute> öznitelikleri neden olan hizmet sözleşmesi tanımları otomatik olarak oluşturulmasını Web Hizmetleri Açıklama Dili (WSDL) belgede hizmet dağıtıldıktan sonra.</span><span class="sxs-lookup"><span data-stu-id="4568e-118">Applying the <xref:System.ServiceModel.ServiceContractAttribute> and <xref:System.ServiceModel.OperationContractAttribute> attributes causes the automatic generation of service contract definitions in a Web Services Description Language (WSDL) document once the service is deployed.</span></span> <span data-ttu-id="4568e-119">Belge ekleyerek karşıdan `?wsdl` HTTP temel adresi hizmeti.</span><span class="sxs-lookup"><span data-stu-id="4568e-119">The document is downloaded by appending `?wsdl` to the HTTP base address for the service.</span></span> <span data-ttu-id="4568e-120">Örneğin, `http://microsoft/CalculatorService?wsdl`</span><span class="sxs-lookup"><span data-stu-id="4568e-120">For example, `http://microsoft/CalculatorService?wsdl`</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4568e-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4568e-121">See Also</span></span>  
 <xref:System.ServiceModel.OperationContractAttribute>  
 [<span data-ttu-id="4568e-122">Hizmet sözleşmeleri tasarlama</span><span class="sxs-lookup"><span data-stu-id="4568e-122">Designing Service Contracts</span></span>](../../../../docs/framework/wcf/designing-service-contracts.md)  
 [<span data-ttu-id="4568e-123">Nasıl yapılır: çift yönlü sözleşme oluşturma</span><span class="sxs-lookup"><span data-stu-id="4568e-123">How to: Create a Duplex Contract</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)
