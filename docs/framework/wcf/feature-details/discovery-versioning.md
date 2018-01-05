---
title: "Keşif Sürümü Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f91c6d0a-3af2-45c5-9a5c-e75390619836
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: df5a15f740e9db4eb58ec4e410db9ef5e014fe0a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="discovery-versioning"></a>Keşif Sürümü Oluşturma
Bu konu, bazı yeni bulma özellikler uyarlamasını kısa bir genel bakış sağlar. Ayrıca bulma sürümün kullanılacağını seçme hakkında genel bir bakış sağlar.  
  
## <a name="discovery-versioning"></a>Keşif Sürümü Oluşturma  
 Bulma özelliği üç WS_Discovery protokol sürümleri için destek içerir. Bulma API'leri kullanmak istediğiniz protokol sürümünü seçmenize olanak tanır. Bu belgede kısaca sürüm oluşturma ile ilgili ayarları açıklanır.  
  
 Aşağıdaki bulma sınıflar şimdi sahip bir <xref:System.ServiceModel.Discovery.DiscoveryVersion> özelliği ve Al bir <xref:System.ServiceModel.Discovery.DiscoveryVersion> kendi oluşturucu bağımsız değişkeni:  
  
-   <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>  
  
-   <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>  
  
-   <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>  
  
-   <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>  
  
### <a name="discoveryversionwsdiscoveryapril2005"></a>DiscoveryVersion.WSDiscoveryApril2005  
 Sağlama <xref:System.ServiceModel.Discovery.DiscoveryVersion.WSDiscoveryApril2005> Oluşturucusu parametreyi WS bulma protokolünü April2005 sürümünü kullanmanız uygulama yapar. Bu sürüm, WS-Bulma Protokolü Belirtimi yayımlanan sürüme karşılık gelir. Bu sürüm, WS-bulma April2005 sürümünü kullanan eski uygulaması ile birlikte çalışmak için kullanılmalıdır.  
  
### <a name="discoveryversionwsdiscovery11"></a>DiscoveryVersion.WSDiscovery11  
 API tarafından kullanılan varsayılan bulma sürüm <xref:System.ServiceModel.Discovery.DiscoveryVersion.WSDiscovery11>. Bu WS bulma protokolünü geçerli standartlaştırılmış sürümüdür.  
  
## <a name="discoveryversionwsdiscoverycd1"></a>DiscoveryVersion.WSDiscoveryCD1  
 Sağlama <xref:System.ServiceModel.Discovery.DiscoveryVersion.WSDiscoveryCD1> kullanmak uygulama Oluşturucu parametresini getirir komitesi WS bulma protokolünü 1 sürümü taslak. Bu protokol sürümü WS bulma protokolünü CD1 sürümünü çalıştıran uygulamaları ile birlikte çalışmak için kullanılmalıdır.  
  
## <a name="supporting-multiple-udp-discovery-endpoints-for-different-discovery-versions-on-a-single-service-host"></a>Farklı bulma sürümlerini tek hizmet ana bilgisayarda için birden fazla UDP bulma uç noktası destekleme  
 Farklı bulma sürümlerini tek hizmet ana bilgisayarda için birden çok UDP bulma uç noktaları kullanıma sunmak isteyebilirsiniz. Bunu yapmak için her UDP bulma uç noktası için benzersiz bir adresi belirtmeniz gerekir. Aşağıdaki örnek bunun nasıl yapılacağı gösterilmektedir.  
  
```  
UdpDiscoveryEndpoint newVersionUdpEndpoint = new UdpDiscoveryEndpoint(DiscoveryVersion.WSDiscovery11);  
UdpDiscoveryEndpoint oldVersionUdpEndpoint = new UdpDiscoveryEndpoint(DiscoveryVersion.WSDiscoveryApril2005);  
  
newVersionUdpEndpoint.Address = new EndpointAddress(newVersionUdpEndpoint.Address.Uri.ToString() + "/version11");  
oldVersionUdpEndpoint.Address = new EndpointAddress(oldVersionUdpEndpoint.Address.Uri.ToString() + "/versionAril2005");  
  
serviceHost.AddServiceEndpoint(newVersionUdpEndpoint);  
serviceHost.AddServiceEndpoint(oldVersionUdpEndpoint);  
```
