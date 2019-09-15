---
title: İstek-Yanıt Hizmetleri
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation [WCF], request-reply services
- contracts [WCF], request-reply services
- WCF [WCF], request-reply services
- request-reply contracts [WCF]
ms.assetid: 2fa710f1-47f4-4598-b063-3ab3bd22ebba
ms.openlocfilehash: f58da6f1cdaad1b976659ee2e9febe12cc07726f
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991137"
---
# <a name="request-reply-services"></a><span data-ttu-id="6e59b-102">İstek-Yanıt Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="6e59b-102">Request-Reply Services</span></span>
<span data-ttu-id="6e59b-103">İstek-yanıt Hizmetleri, Windows Communication Foundation (WCF) ' de varsayılan işlem anlaşması türüdür.</span><span class="sxs-lookup"><span data-stu-id="6e59b-103">Request-reply services are the default type of operation contract in Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="6e59b-104">İstemciler hizmet işlemlerine çağrı yapar ve hizmetten bir yanıt bekler.</span><span class="sxs-lookup"><span data-stu-id="6e59b-104">Clients make calls to service operations and wait for a response from the service.</span></span> <span data-ttu-id="6e59b-105">İstemci, hizmetten veya çağrı sürelerinin bir yanıtını alana kadar engellediği veya zaman uyumsuz olarak, istemcinin hizmet işlemine bir çağrı yaptığı, çalışmaya devam ettiği ve bunu aldığı zaman uyumsuz olarak bir hizmet işlemine çağrı yapabilirsiniz. başka bir iş parçacığında hizmetten yanıt.</span><span class="sxs-lookup"><span data-stu-id="6e59b-105">You can perform calls to a service operation either synchronously, where the client blocks until it receives a response from the service or the call times, or asynchronously, where the client makes a call to the service operation, continues working, and receives the response from the service on another thread.</span></span>  
  
 <span data-ttu-id="6e59b-106">İstek-yanıt hizmet sözleşmesi oluşturmak için, hizmet sözleşmenizi tanımlayın ve aşağıdaki örnek kodda gösterildiği <xref:System.ServiceModel.OperationContractAttribute> gibi her bir işleme sınıfı uygulayın.</span><span class="sxs-lookup"><span data-stu-id="6e59b-106">To create a request-reply service contract, define your service contract, and apply the <xref:System.ServiceModel.OperationContractAttribute> class to each operation, as shown in the following sample code.</span></span>  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IRequestReplyCalculator  
{  
    [OperationContract]  
    double Add(double n1, double n2);  
}  
```  
  
 <span data-ttu-id="6e59b-107">Bu varsayılan davranış olduğundan, <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> özelliğini olarak `false` ayarlamanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="6e59b-107">You do not have to set the  <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property to `false` because this is the default behavior.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e59b-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6e59b-108">See also</span></span>

- [<span data-ttu-id="6e59b-109">Tek Yönlü Hizmetler</span><span class="sxs-lookup"><span data-stu-id="6e59b-109">One-Way Services</span></span>](../../../../docs/framework/wcf/feature-details/one-way-services.md)
- [<span data-ttu-id="6e59b-110">Çift Yönlü Hizmetler</span><span class="sxs-lookup"><span data-stu-id="6e59b-110">Duplex Services</span></span>](../../../../docs/framework/wcf/feature-details/duplex-services.md)
