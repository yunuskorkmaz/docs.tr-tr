---
title: İstek-Yanıt Hizmetleri
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation [WCF], request-reply services
- contracts [WCF], request-reply services
- WCF [WCF], request-reply services
- request-reply contracts [WCF]
ms.assetid: 2fa710f1-47f4-4598-b063-3ab3bd22ebba
ms.openlocfilehash: 1ff11b1cae4ec8f6fe886a55cb0add27831048d0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59177820"
---
# <a name="request-reply-services"></a><span data-ttu-id="22ab9-102">İstek-Yanıt Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="22ab9-102">Request-Reply Services</span></span>
<span data-ttu-id="22ab9-103">İstek-yanıt Hizmetleri işlem anlaşması Windows Communication Foundation (WCF) varsayılan türüdür.</span><span class="sxs-lookup"><span data-stu-id="22ab9-103">Request-reply services are the default type of operation contract in Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="22ab9-104">İstemcilerin hizmet işlemlerine aramaları yapmak ve hizmetten bir yanıt bekler.</span><span class="sxs-lookup"><span data-stu-id="22ab9-104">Clients make calls to service operations and wait for a response from the service.</span></span> <span data-ttu-id="22ab9-105">Bir hizmet işlemi çağrısına ya da zaman uyumlu olarak gerçekleştirebileceğiniz, istemci kadar engeller, hizmet veya çağrısı süreleri bir yanıt alır veya zaman uyumsuz olarak, istemci bir hizmet işlemi çağrıda burada çalışmaya devam eder ve alır başka bir iş parçacığında hizmetinden gelen yanıt.</span><span class="sxs-lookup"><span data-stu-id="22ab9-105">You can perform calls to a service operation either synchronously, where the client blocks until it receives a response from the service or the call times, or asynchronously, where the client makes a call to the service operation, continues working, and receives the response from the service on another thread.</span></span>  
  
 <span data-ttu-id="22ab9-106">İstek-yanıt hizmeti sözleşme oluşturmak için hizmet sözleşmesini tanımlama ve uygulama <xref:System.ServiceModel.OperationContractAttribute> aşağıdaki örnek kodda gösterildiği gibi her işlem için sınıf.</span><span class="sxs-lookup"><span data-stu-id="22ab9-106">To create a request-reply service contract, define your service contract, and apply the <xref:System.ServiceModel.OperationContractAttribute> class to each operation, as shown in the following sample code.</span></span>  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IRequestReplyCalculator  
{  
    [OperationContract]  
    double Add(double n1, double n2);  
}  
```  
  
 <span data-ttu-id="22ab9-107">Ayarlamak zorunda değilsiniz <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> özelliğini `false` çünkü bu varsayılan davranışı.</span><span class="sxs-lookup"><span data-stu-id="22ab9-107">You do not have to set the  <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property to `false` because this is the default behavior.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22ab9-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="22ab9-108">See also</span></span>

- [<span data-ttu-id="22ab9-109">Tek Yönlü Hizmetler</span><span class="sxs-lookup"><span data-stu-id="22ab9-109">One-Way Services</span></span>](../../../../docs/framework/wcf/feature-details/one-way-services.md)
- [<span data-ttu-id="22ab9-110">Çift Yönlü Hizmetler</span><span class="sxs-lookup"><span data-stu-id="22ab9-110">Duplex Services</span></span>](../../../../docs/framework/wcf/feature-details/duplex-services.md)
