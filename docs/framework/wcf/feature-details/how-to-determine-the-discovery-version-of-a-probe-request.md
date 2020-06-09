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
