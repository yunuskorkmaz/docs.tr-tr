---
title: İstek-Yanıt Hizmetleri
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation [WCF], request-reply services
- contracts [WCF], request-reply services
- WCF [WCF], request-reply services
- request-reply contracts [WCF]
ms.assetid: 2fa710f1-47f4-4598-b063-3ab3bd22ebba
ms.openlocfilehash: 8fe1343a4b3590622becf71f1167f4b19dbc67af
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33490951"
---
# <a name="request-reply-services"></a><span data-ttu-id="798bb-102">İstek-Yanıt Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="798bb-102">Request-Reply Services</span></span>
<span data-ttu-id="798bb-103">İstek-yanıt Hizmetleri işlemi sözleşme Windows Communication Foundation (WCF) varsayılan türüdür.</span><span class="sxs-lookup"><span data-stu-id="798bb-103">Request-reply services are the default type of operation contract in Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="798bb-104">İstemcileri hizmet işlemleri çağrı yapmak ve hizmetinden bir yanıt bekleyin.</span><span class="sxs-lookup"><span data-stu-id="798bb-104">Clients make calls to service operations and wait for a response from the service.</span></span> <span data-ttu-id="798bb-105">Bir hizmet işlemi çağrıları ya da zaman uyumlu olarak gerçekleştirebileceğiniz, kadar istemci engeller burada bu hizmetin veya çağrı süreleri bir yanıt alır veya zaman uyumsuz olarak, istemci hizmet işlemi için bir çağrı yapar burada çalışmaya devam eder ve alır başka bir iş parçacığında hizmetinden gelen yanıt.</span><span class="sxs-lookup"><span data-stu-id="798bb-105">You can perform calls to a service operation either synchronously, where the client blocks until it receives a response from the service or the call times, or asynchronously, where the client makes a call to the service operation, continues working, and receives the response from the service on another thread.</span></span>  
  
 <span data-ttu-id="798bb-106">İstek-yanıt hizmeti sözleşme oluşturmak için hizmet sözleşmesini tanımlama ve uygulama <xref:System.ServiceModel.OperationContractAttribute> aşağıdaki örnek kodda gösterildiği gibi her işlem için sınıf.</span><span class="sxs-lookup"><span data-stu-id="798bb-106">To create a request-reply service contract, define your service contract, and apply the <xref:System.ServiceModel.OperationContractAttribute> class to each operation, as shown in the following sample code.</span></span>  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IRequestReplyCalculator  
{  
    [OperationContract]  
    double Add(double n1, double n2);  
}  
```  
  
 <span data-ttu-id="798bb-107">Ayarlama gerekmez <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> özelliğine `false` bu varsayılan davranış olduğu için.</span><span class="sxs-lookup"><span data-stu-id="798bb-107">You do not have to set the  <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property to `false` because this is the default behavior.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="798bb-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="798bb-108">See Also</span></span>  
 [<span data-ttu-id="798bb-109">Tek Yönlü Hizmetler</span><span class="sxs-lookup"><span data-stu-id="798bb-109">One-Way Services</span></span>](../../../../docs/framework/wcf/feature-details/one-way-services.md)  
 [<span data-ttu-id="798bb-110">Çift Yönlü Hizmetler</span><span class="sxs-lookup"><span data-stu-id="798bb-110">Duplex Services</span></span>](../../../../docs/framework/wcf/feature-details/duplex-services.md)
