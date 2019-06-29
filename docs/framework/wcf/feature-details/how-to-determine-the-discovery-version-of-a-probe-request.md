---
title: 'Nasıl yapılır: Bir Araştırma İsteğinin Keşif sürümünü Belirleme'
ms.date: 03/30/2017
ms.assetid: b3c4e2e2-2957-4074-ae6a-776a5ca84278
ms.openlocfilehash: 8fbc3936278a5c6f403f48b59390c69c64378004
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67425262"
---
# <a name="how-todetermine-the-discovery-version-of-a-probe-request"></a>Nasıl yapılır: Bir Araştırma İsteğinin Keşif sürümünü Belirleme

Keşif proxy'si farklı bulma sürümlerini kullanan birden fazla bulma uç noktası getirebilir. Bir UDP, çok noktaya yayın araştırma isteğinin proxy, proxy bir çok noktaya yayın gizleme ileti ile yanıt vermelidir ulaşır. Bunu yapmak için isteğinin keşif sürümünü bilmesi gerekir.

## <a name="to-determine-the-discovery-version-of-a-probe-request"></a>Bir araştırma isteğinin keşif sürümünü belirleme

Bir araştırma isteğine yanıt vermeden yöntem (örneğin <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A?displayProperty=nameWithType>) statik <xref:System.ServiceModel.OperationContext.Current%2A?displayProperty=nameWithType> aramak için özellik bir <xref:System.ServiceModel.Discovery.DiscoveryOperationContextExtension>aşağıdaki kodda gösterildiği gibi.

```csharp
DiscoveryOperationContextExtension doce = OperationContext.Current.Extensions.Find<DiscoveryOperationContextExtension>();
// Access the discovery version from the DiscoveryOperationContextExtension
doce.DiscoveryVersion;
```

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion%2A>
- [Keşif Proxy'si Ekleme](../../../../docs/framework/wcf/feature-details/implementing-a-discovery-proxy.md)
