---
description: 'Daha fazla bilgi edinin: bulma sürümü oluşturma'
title: Keşif Sürümü Oluşturma
ms.date: 03/30/2017
ms.assetid: f91c6d0a-3af2-45c5-9a5c-e75390619836
ms.openlocfilehash: 075fefce0477810336c8b857343984070ed89b37
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99743193"
---
# <a name="discovery-versioning"></a>Keşif Sürümü Oluşturma

Bu konu, bazı yeni keşif özelliklerinin uygulanmasına ilişkin kısa bir genel bakış sağlar. Ayrıca, kullanılacak bulma sürümünün nasıl kullanılacağına ilişkin bir genel bakış sunar.

## <a name="discovery-versioning"></a>Keşif Sürümü Oluşturma

Bulma özelliği, WS_Discovery protokolünün üç sürümü için destek içerir. Bulma API 'Leri, kullanmak istediğiniz protokolün sürümünü seçmenizi sağlar. Bu belge, sürüm oluşturma ile ilgili ayarları kısaca açıklar.

Aşağıdaki bulgu sınıfları artık bir özelliğe sahiptir <xref:System.ServiceModel.Discovery.DiscoveryVersion> ve <xref:System.ServiceModel.Discovery.DiscoveryVersion> oluşturucularında bir bağımsız değişken alır:

- <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>

- <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>

- <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>

- <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>

### <a name="discoveryversionwsdiscoveryapril2005"></a>DiscoveryVersion. WSDiscoveryApril2005

<xref:System.ServiceModel.Discovery.DiscoveryVersion.WSDiscoveryApril2005>Oluşturucu parametresi olarak sağlanması, uygulamanın WS-Discovery protokolünün April2005 sürümünü kullanmasını sağlar. Bu sürüm, WS-Discovery protokol belirtiminin yayımlanmış sürümüne karşılık gelir. Bu sürüm, WS-Discovery April2005 sürümünü kullanan eski uygulamayla birlikte çalışmak için kullanılmalıdır.

### <a name="discoveryversionwsdiscovery11"></a>DiscoveryVersion. WSDiscovery11

API 'Ler tarafından kullanılan varsayılan bulma sürümü <xref:System.ServiceModel.Discovery.DiscoveryVersion.WSDiscovery11> . Bu, WS-Discovery protokolünün geçerli standartlaştırılmış sürümüdür.

## <a name="discoveryversionwsdiscoverycd1"></a>DiscoveryVersion. WSDiscoveryCD1

<xref:System.ServiceModel.Discovery.DiscoveryVersion.WSDiscoveryCD1>Oluşturucu parametresi olarak sağlanması, uygulamanın WS-Discovery protokolünün komite taslak 1 sürümünü kullanmasını sağlar. Protokolün bu sürümü, WS-Discovery protokolünün CD1 sürümünü çalıştıran uygulamalarla birlikte çalışmak için kullanılmalıdır.

## <a name="supporting-multiple-udp-discovery-endpoints-for-different-discovery-versions-on-a-single-service-host"></a>Tek bir hizmet konağında farklı bulma sürümleri için birden çok UDP bulma uç noktası destekleme

Tek bir hizmet konağında farklı bulma sürümleri için birden çok UDP bulma uç noktası göstermek isteyebilirsiniz. Bunu yapmak için, her bir UDP bulma uç noktası için benzersiz bir adres belirtmeniz gerekir. Aşağıdaki örnek bunun nasıl yapılacağını göstermektedir.

```csharp
UdpDiscoveryEndpoint newVersionUdpEndpoint = new UdpDiscoveryEndpoint(DiscoveryVersion.WSDiscovery11);
UdpDiscoveryEndpoint oldVersionUdpEndpoint = new UdpDiscoveryEndpoint(DiscoveryVersion.WSDiscoveryApril2005);

newVersionUdpEndpoint.Address = new EndpointAddress(newVersionUdpEndpoint.Address.Uri.ToString() + "/version11");
oldVersionUdpEndpoint.Address = new EndpointAddress(oldVersionUdpEndpoint.Address.Uri.ToString() + "/versionApril2005");

serviceHost.AddServiceEndpoint(newVersionUdpEndpoint);
serviceHost.AddServiceEndpoint(oldVersionUdpEndpoint);
```
