---
title: 'Nasıl yapılır: Bir Araştırma İsteğinin Keşif sürümünü Belirleme'
ms.date: 03/30/2017
ms.assetid: b3c4e2e2-2957-4074-ae6a-776a5ca84278
ms.openlocfilehash: 6bd112be311eb9397ad89801be5358d67c7499fd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59332280"
---
# <a name="how-todetermine-the-discovery-version-of-a-probe-request"></a><span data-ttu-id="fc55f-102">Nasıl yapılır: Bir Araştırma İsteğinin Keşif sürümünü Belirleme</span><span class="sxs-lookup"><span data-stu-id="fc55f-102">How to:Determine the Discovery Version of a Probe Request</span></span>
<span data-ttu-id="fc55f-103">Keşif proxy'si farklı bulma sürümlerini kullanan birden fazla bulma uç noktası getirebilir.</span><span class="sxs-lookup"><span data-stu-id="fc55f-103">A discovery proxy may expose multiple discovery endpoints using different discovery versions.</span></span> <span data-ttu-id="fc55f-104">Bir UDP, çok noktaya yayın araştırma isteğinin proxy bir çok noktaya yayın gizleme ileti ile yanıt vermelidir proxy ulaşır.</span><span class="sxs-lookup"><span data-stu-id="fc55f-104">When a UDP multicast Probe request arrives at the proxy the proxy should respond with a multicast suppression message.</span></span> <span data-ttu-id="fc55f-105">Bunu yapmak için isteğinin keşif sürümünü bilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="fc55f-105">In order to do this it would have to know the discovery version of the request.</span></span>  
  
### <a name="to-determine-the-discovery-version-of-a-probe-request"></a><span data-ttu-id="fc55f-106">Bir araştırma isteğinin keşif sürümünü belirleme</span><span class="sxs-lookup"><span data-stu-id="fc55f-106">To Determine the Discovery Version of a Probe Request</span></span>  
  
1. <span data-ttu-id="fc55f-107">Bir araştırma isteğine yanıt vermeden yöntem (örneğin <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A>) statik <xref:System.ServiceModel.OperationContext.Current%2A> aramak için özellik bir <xref:System.ServiceModel.Discovery.DiscoveryOperationContextExtension> aşağıdaki kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="fc55f-107">In the method that responds to a Probe request (for example <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A>) use the static <xref:System.ServiceModel.OperationContext.Current%2A> property to search for a <xref:System.ServiceModel.Discovery.DiscoveryOperationContextExtension> as shown in the following code.</span></span>  
  
    ```  
    DiscoveryOperationContextExtension doce = OperationContext.Current.Extensions.Find<DiscoveryOperationContextExtension>();  
    // Access the discovery version from the DiscoveryOperationContextExtension  
    doce.DiscoveryVersion;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="fc55f-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fc55f-108">See also</span></span>

- <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion%2A>
- [<span data-ttu-id="fc55f-109">Keşif Proxy'si Ekleme</span><span class="sxs-lookup"><span data-stu-id="fc55f-109">Implementing a Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/implementing-a-discovery-proxy.md)
