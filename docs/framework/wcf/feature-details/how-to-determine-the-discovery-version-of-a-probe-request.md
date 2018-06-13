---
title: 'Nasıl yapılır: Bir Araştırma İsteğinin Keşif sürümünü Belirleme'
ms.date: 03/30/2017
ms.assetid: b3c4e2e2-2957-4074-ae6a-776a5ca84278
ms.openlocfilehash: 8ac9804b0fe46ca5fbe580d713ec82a2f9bb0128
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33489787"
---
# <a name="how-todetermine-the-discovery-version-of-a-probe-request"></a><span data-ttu-id="68cfa-102">Nasıl yapılır: Bir Araştırma İsteğinin Keşif sürümünü Belirleme</span><span class="sxs-lookup"><span data-stu-id="68cfa-102">How to:Determine the Discovery Version of a Probe Request</span></span>
<span data-ttu-id="68cfa-103">Keşif proxy'si farklı bulma sürümlerini kullanan birden fazla bulma uç noktası getirebilir.</span><span class="sxs-lookup"><span data-stu-id="68cfa-103">A discovery proxy may expose multiple discovery endpoints using different discovery versions.</span></span> <span data-ttu-id="68cfa-104">Bir UDP, çok noktaya yayın araştırma isteğinin proxy çok noktaya yayın gizleme iletisiyle yanıt vermesi gerektiğini proxy ulaştığında.</span><span class="sxs-lookup"><span data-stu-id="68cfa-104">When a UDP multicast Probe request arrives at the proxy the proxy should respond with a multicast suppression message.</span></span> <span data-ttu-id="68cfa-105">Bunu yapmak için bir istek bulma sürümü bilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="68cfa-105">In order to do this it would have to know the discovery version of the request.</span></span>  
  
### <a name="to-determine-the-discovery-version-of-a-probe-request"></a><span data-ttu-id="68cfa-106">Bir araştırma isteğinin keşif sürümünü belirleme</span><span class="sxs-lookup"><span data-stu-id="68cfa-106">To Determine the Discovery Version of a Probe Request</span></span>  
  
1.  <span data-ttu-id="68cfa-107">Bir araştırma isteğine yanıt yöntemi (örneğin <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A>) statik kullanmak <xref:System.ServiceModel.OperationContext.Current%2A> özelliğini araması için bir <xref:System.ServiceModel.Discovery.DiscoveryOperationContextExtension> aşağıdaki kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="68cfa-107">In the method that responds to a Probe request (for example <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A>) use the static <xref:System.ServiceModel.OperationContext.Current%2A> property to search for a <xref:System.ServiceModel.Discovery.DiscoveryOperationContextExtension> as shown in the following code.</span></span>  
  
    ```  
    DiscoveryOperationContextExtension doce = OperationContext.Current.Extensions.Find<DiscoveryOperationContextExtension>();  
    // Access the discovery version from the DiscoveryOperationContextExtension  
    doce.DiscoveryVersion;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="68cfa-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="68cfa-108">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion%2A>  
 [<span data-ttu-id="68cfa-109">Keşif Proxy'si Ekleme</span><span class="sxs-lookup"><span data-stu-id="68cfa-109">Implementing a Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/implementing-a-discovery-proxy.md)  
 [<span data-ttu-id="68cfa-110">Bulma Ara Sunucusu Örneği</span><span class="sxs-lookup"><span data-stu-id="68cfa-110">Discovery Proxy Sample</span></span>](../../../../docs/framework/wcf/samples/discovery-proxy-sample.md)
