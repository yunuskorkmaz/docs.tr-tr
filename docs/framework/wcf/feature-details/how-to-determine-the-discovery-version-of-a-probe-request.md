---
title: 'Nasıl yapılır: Bir Araştırma İsteğinin Keşif sürümünü Belirleme'
ms.date: 03/30/2017
ms.assetid: b3c4e2e2-2957-4074-ae6a-776a5ca84278
ms.openlocfilehash: 2b7e42714ae1d16a84bcb6f0fc79cf5b376a7a16
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595420"
---
# <a name="how-todetermine-the-discovery-version-of-a-probe-request"></a><span data-ttu-id="49f6b-102">Nasıl yapılır: Bir Araştırma İsteğinin Keşif sürümünü Belirleme</span><span class="sxs-lookup"><span data-stu-id="49f6b-102">How to:Determine the Discovery Version of a Probe Request</span></span>

<span data-ttu-id="49f6b-103">Keşif proxy 'si, farklı keşif sürümlerini kullanarak birden çok bulma uç noktası sunabilir.</span><span class="sxs-lookup"><span data-stu-id="49f6b-103">A discovery proxy may expose multiple discovery endpoints using different discovery versions.</span></span> <span data-ttu-id="49f6b-104">Proxy 'ye bir UDP çok noktaya yayın araştırması isteği ulaştığında, ara sunucu çok noktaya yayın gizleme iletisiyle yanıt vermelidir.</span><span class="sxs-lookup"><span data-stu-id="49f6b-104">When a UDP multicast Probe request arrives at the proxy, the proxy should respond with a multicast suppression message.</span></span> <span data-ttu-id="49f6b-105">Bunu yapmak için isteğin bulma sürümünü bilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="49f6b-105">In order to do this, it would have to know the discovery version of the request.</span></span>

## <a name="to-determine-the-discovery-version-of-a-probe-request"></a><span data-ttu-id="49f6b-106">Bir araştırma Isteğinin keşif sürümünü belirleme</span><span class="sxs-lookup"><span data-stu-id="49f6b-106">To Determine the Discovery Version of a Probe Request</span></span>

<span data-ttu-id="49f6b-107">Bir araştırma isteğine yanıt veren yönteminde (örneğin <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A?displayProperty=nameWithType> ) <xref:System.ServiceModel.OperationContext.Current%2A?displayProperty=nameWithType> <xref:System.ServiceModel.Discovery.DiscoveryOperationContextExtension> , aşağıdaki kodda gösterildiği gibi bir için arama yapmak üzere statik özelliği kullanın.</span><span class="sxs-lookup"><span data-stu-id="49f6b-107">In the method that responds to a Probe request (for example <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A?displayProperty=nameWithType>) use the static <xref:System.ServiceModel.OperationContext.Current%2A?displayProperty=nameWithType> property to search for a <xref:System.ServiceModel.Discovery.DiscoveryOperationContextExtension>, as shown in the following code.</span></span>

```csharp
DiscoveryOperationContextExtension doce = OperationContext.Current.Extensions.Find<DiscoveryOperationContextExtension>();
// Access the discovery version from the DiscoveryOperationContextExtension
doce.DiscoveryVersion;
```

## <a name="see-also"></a><span data-ttu-id="49f6b-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="49f6b-108">See also</span></span>

- <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion%2A>
- [<span data-ttu-id="49f6b-109">Keşif Proxy'si Ekleme</span><span class="sxs-lookup"><span data-stu-id="49f6b-109">Implementing a Discovery Proxy</span></span>](implementing-a-discovery-proxy.md)
