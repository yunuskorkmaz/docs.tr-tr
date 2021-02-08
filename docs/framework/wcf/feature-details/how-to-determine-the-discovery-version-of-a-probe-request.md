---
description: 'Şu konuda daha fazla bilgi edinin: nasıl yapılır: bir araştırma Isteğinin keşif sürümünü belirleme'
title: 'Nasıl yapılır: Bir Araştırma İsteğinin Keşif sürümünü Belirleme'
ms.date: 03/30/2017
ms.assetid: b3c4e2e2-2957-4074-ae6a-776a5ca84278
ms.openlocfilehash: c41283cb84d75dd2dbf7e86da0dec075ab8b6635
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793798"
---
# <a name="how-todetermine-the-discovery-version-of-a-probe-request"></a><span data-ttu-id="c42b4-103">Nasıl yapılır: Bir Araştırma İsteğinin Keşif sürümünü Belirleme</span><span class="sxs-lookup"><span data-stu-id="c42b4-103">How to:Determine the Discovery Version of a Probe Request</span></span>

<span data-ttu-id="c42b4-104">Keşif proxy 'si, farklı keşif sürümlerini kullanarak birden çok bulma uç noktası sunabilir.</span><span class="sxs-lookup"><span data-stu-id="c42b4-104">A discovery proxy may expose multiple discovery endpoints using different discovery versions.</span></span> <span data-ttu-id="c42b4-105">Proxy 'ye bir UDP çok noktaya yayın araştırması isteği ulaştığında, ara sunucu çok noktaya yayın gizleme iletisiyle yanıt vermelidir.</span><span class="sxs-lookup"><span data-stu-id="c42b4-105">When a UDP multicast Probe request arrives at the proxy, the proxy should respond with a multicast suppression message.</span></span> <span data-ttu-id="c42b4-106">Bunu yapmak için isteğin bulma sürümünü bilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="c42b4-106">In order to do this, it would have to know the discovery version of the request.</span></span>

## <a name="to-determine-the-discovery-version-of-a-probe-request"></a><span data-ttu-id="c42b4-107">Bir araştırma Isteğinin keşif sürümünü belirleme</span><span class="sxs-lookup"><span data-stu-id="c42b4-107">To Determine the Discovery Version of a Probe Request</span></span>

<span data-ttu-id="c42b4-108">Bir araştırma isteğine yanıt veren yönteminde (örneğin <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A?displayProperty=nameWithType> ) <xref:System.ServiceModel.OperationContext.Current%2A?displayProperty=nameWithType> <xref:System.ServiceModel.Discovery.DiscoveryOperationContextExtension> , aşağıdaki kodda gösterildiği gibi bir için arama yapmak üzere statik özelliği kullanın.</span><span class="sxs-lookup"><span data-stu-id="c42b4-108">In the method that responds to a Probe request (for example <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A?displayProperty=nameWithType>) use the static <xref:System.ServiceModel.OperationContext.Current%2A?displayProperty=nameWithType> property to search for a <xref:System.ServiceModel.Discovery.DiscoveryOperationContextExtension>, as shown in the following code.</span></span>

```csharp
DiscoveryOperationContextExtension doce = OperationContext.Current.Extensions.Find<DiscoveryOperationContextExtension>();
// Access the discovery version from the DiscoveryOperationContextExtension
doce.DiscoveryVersion;
```

## <a name="see-also"></a><span data-ttu-id="c42b4-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c42b4-109">See also</span></span>

- <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion%2A>
- [<span data-ttu-id="c42b4-110">Keşif Proxy'si Ekleme</span><span class="sxs-lookup"><span data-stu-id="c42b4-110">Implementing a Discovery Proxy</span></span>](implementing-a-discovery-proxy.md)
