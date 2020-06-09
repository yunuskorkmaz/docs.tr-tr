---
title: İstek-Yanıt Hizmetleri
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation [WCF], request-reply services
- contracts [WCF], request-reply services
- WCF [WCF], request-reply services
- request-reply contracts [WCF]
ms.assetid: 2fa710f1-47f4-4598-b063-3ab3bd22ebba
ms.openlocfilehash: df42f3fa8f5a15572987b0d4859856c7f838e632
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84586240"
---
# <a name="request-reply-services"></a><span data-ttu-id="58710-102">İstek-Yanıt Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="58710-102">Request-Reply Services</span></span>
<span data-ttu-id="58710-103">İstek-yanıt Hizmetleri, Windows Communication Foundation (WCF) ' de varsayılan işlem anlaşması türüdür.</span><span class="sxs-lookup"><span data-stu-id="58710-103">Request-reply services are the default type of operation contract in Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="58710-104">İstemciler hizmet işlemlerine çağrı yapar ve hizmetten bir yanıt bekler.</span><span class="sxs-lookup"><span data-stu-id="58710-104">Clients make calls to service operations and wait for a response from the service.</span></span> <span data-ttu-id="58710-105">İstemci, hizmetten veya çağrı sürelerinin bir yanıtını alana kadar engellediği veya zaman uyumsuz olarak, istemcinin hizmet işlemine bir çağrı yaptığı, çalışmaya devam ettiği ve diğer bir iş parçacığında hizmetten gelen yanıtı aldığı zaman uyumsuz olarak bir hizmet işlemine çağrı gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="58710-105">You can perform calls to a service operation either synchronously, where the client blocks until it receives a response from the service or the call times, or asynchronously, where the client makes a call to the service operation, continues working, and receives the response from the service on another thread.</span></span>  
  
 <span data-ttu-id="58710-106">İstek-yanıt hizmet sözleşmesi oluşturmak için, hizmet sözleşmenizi tanımlayın ve <xref:System.ServiceModel.OperationContractAttribute> Aşağıdaki örnek kodda gösterildiği gibi her bir işleme sınıfı uygulayın.</span><span class="sxs-lookup"><span data-stu-id="58710-106">To create a request-reply service contract, define your service contract, and apply the <xref:System.ServiceModel.OperationContractAttribute> class to each operation, as shown in the following sample code.</span></span>  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IRequestReplyCalculator  
{  
    [OperationContract]  
    double Add(double n1, double n2);  
}  
```  
  
 <span data-ttu-id="58710-107"><xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A>Bu varsayılan davranış olduğundan, özelliğini olarak ayarlamanız gerekmez `false` .</span><span class="sxs-lookup"><span data-stu-id="58710-107">You do not have to set the  <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property to `false` because this is the default behavior.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58710-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="58710-108">See also</span></span>

- [<span data-ttu-id="58710-109">Tek Yönlü Hizmetler</span><span class="sxs-lookup"><span data-stu-id="58710-109">One-Way Services</span></span>](one-way-services.md)
- [<span data-ttu-id="58710-110">Çift Yönlü Hizmetler</span><span class="sxs-lookup"><span data-stu-id="58710-110">Duplex Services</span></span>](duplex-services.md)
