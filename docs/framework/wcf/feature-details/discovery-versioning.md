---
title: Keşif Sürümü Oluşturma
ms.date: 03/30/2017
ms.assetid: f91c6d0a-3af2-45c5-9a5c-e75390619836
ms.openlocfilehash: 4a1ca07fc6773ce6f883d654abfedab4986341e1
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67425249"
---
# <a name="discovery-versioning"></a>Keşif Sürümü Oluşturma

Bu konu, bazı yeni bulma özelliklerinin uygulamasını kısa bir genel bakış sağlar. Ayrıca bulma sürümün kullanılacağını seçme hakkında genel bir bakış sağlar.

## <a name="discovery-versioning"></a>Keşif Sürümü Oluşturma

Bulma özelliği üç WS_Discovery Protokolü sürümleri için destek içerir. Bulma API'leri kullanmak istediğiniz protokol sürümünü seçmenize olanak tanır. Bu belgede kısaca, sürüm oluşturma ile ilgili ayarları açıklanmaktadır.

Aşağıdaki bulma sınıfları artık sahip bir <xref:System.ServiceModel.Discovery.DiscoveryVersion> özelliği ve take bir <xref:System.ServiceModel.Discovery.DiscoveryVersion> oluşturucuları bağımsız değişkeni:

- <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>

- <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>

- <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>

- <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>

### <a name="discoveryversionwsdiscoveryapril2005"></a>DiscoveryVersion.WSDiscoveryApril2005

Sağlama <xref:System.ServiceModel.Discovery.DiscoveryVersion.WSDiscoveryApril2005> Oluşturucu olarak parametresi için WS bulma protokolünü April2005 sürümünü kullanan uygulama yapar. Bu sürümü, WS-Bulma Protokolü Belirtimi yayımlanmış sürümüne karşılık gelir. Bu sürümü, WS-bulma April2005 sürümünü kullanan eski uygulaması ile çalışmak için kullanılmalıdır.

### <a name="discoveryversionwsdiscovery11"></a>DiscoveryVersion.WSDiscovery11

API'ları tarafından kullanılan varsayılan bulma sürüm <xref:System.ServiceModel.Discovery.DiscoveryVersion.WSDiscovery11>. Bu için WS bulma protokolünü geçerli standartlaştırılmış sürümüdür.

## <a name="discoveryversionwsdiscoverycd1"></a>DiscoveryVersion.WSDiscoveryCD1

Sağlama <xref:System.ServiceModel.Discovery.DiscoveryVersion.WSDiscoveryCD1> kullanan uygulama Oluşturucu parametresi getirir komitesi için WS bulma protokolünü 1 sürümü taslak. Bu protokol sürümü, WS bulma protokolünü CD1 sürümünü çalıştıran uygulamaları ile çalışmak için kullanılmalıdır.

## <a name="supporting-multiple-udp-discovery-endpoints-for-different-discovery-versions-on-a-single-service-host"></a>Birden fazla UDP bulma uç noktası bir tek hizmet konağı farklı bulma sürümleri için destek

Birden fazla UDP bulma uç noktası için bir tek hizmet konağı farklı bulma sürümlerinde kullanıma sunmak isteyebilirsiniz. Bunu yapmak için her UDP bulma uç noktası için benzersiz bir adresi belirtmeniz gerekir. Aşağıdaki örnek bunun nasıl yapılacağı gösterilmektedir.

```csharp
UdpDiscoveryEndpoint newVersionUdpEndpoint = new UdpDiscoveryEndpoint(DiscoveryVersion.WSDiscovery11);
UdpDiscoveryEndpoint oldVersionUdpEndpoint = new UdpDiscoveryEndpoint(DiscoveryVersion.WSDiscoveryApril2005);

newVersionUdpEndpoint.Address = new EndpointAddress(newVersionUdpEndpoint.Address.Uri.ToString() + "/version11");
oldVersionUdpEndpoint.Address = new EndpointAddress(oldVersionUdpEndpoint.Address.Uri.ToString() + "/versionApril2005");

serviceHost.AddServiceEndpoint(newVersionUdpEndpoint);
serviceHost.AddServiceEndpoint(oldVersionUdpEndpoint);
```
