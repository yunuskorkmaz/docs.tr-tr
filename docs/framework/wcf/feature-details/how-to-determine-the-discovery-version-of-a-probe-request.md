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
# <a name="how-todetermine-the-discovery-version-of-a-probe-request"></a>Nasıl yapılır: Bir Araştırma İsteğinin Keşif sürümünü Belirleme

Keşif proxy 'si, farklı keşif sürümlerini kullanarak birden çok bulma uç noktası sunabilir. Proxy 'ye bir UDP çok noktaya yayın araştırması isteği ulaştığında, ara sunucu çok noktaya yayın gizleme iletisiyle yanıt vermelidir. Bunu yapmak için isteğin bulma sürümünü bilmesi gerekir.

## <a name="to-determine-the-discovery-version-of-a-probe-request"></a>Bir araştırma Isteğinin keşif sürümünü belirleme

Bir araştırma isteğine yanıt veren yönteminde (örneğin <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A?displayProperty=nameWithType> ) <xref:System.ServiceModel.OperationContext.Current%2A?displayProperty=nameWithType> <xref:System.ServiceModel.Discovery.DiscoveryOperationContextExtension> , aşağıdaki kodda gösterildiği gibi bir için arama yapmak üzere statik özelliği kullanın.

```csharp
DiscoveryOperationContextExtension doce = OperationContext.Current.Extensions.Find<DiscoveryOperationContextExtension>();
// Access the discovery version from the DiscoveryOperationContextExtension
doce.DiscoveryVersion;
```

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion%2A>
- [Keşif Proxy'si Ekleme](implementing-a-discovery-proxy.md)
