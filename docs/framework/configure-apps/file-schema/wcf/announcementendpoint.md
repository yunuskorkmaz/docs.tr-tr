---
title: <announcementEndpoint>
ms.date: 03/30/2017
ms.assetid: 034b7c69-a770-4502-8cef-38007bbcd025
ms.openlocfilehash: aa4cd8f4d7dcfa438ede71c394f1d0b0ac6faa50
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926545"
---
# <a name="announcementendpoint"></a>\<announcementEndpoint >
Bu yapılandırma öğesi, bir sabit duyuru sözleşmesiyle standart uç noktayı tanımlar. Bir hizmet, isteğe bağlı olarak açık veya kapalı olduğunda bir çevrimiçi ve çevrimdışı duyuru iletisi göndererek kullanılabilirliğini duyurur. Windows Communication Foundation (WCF) hizmeti, [ \<servicediscovery >](servicediscovery.md) öğesindeki duyuru uç noktalarını belirtir ve duyuruları gerçekleştirmek için AnnouncementClient 'ı kullanır. Diğer hizmetten gelen duyuruyu dinlemek isteyen bir istemci aslında bir WCF hizmeti olarak davranır; Bu nedenle, [ \<Hizmetler >](services.md) bölümünde söz konusu istemcinin duyuru uç noktalarını yapılandırmanız gerekir.  
  
\<system.ServiceModel>  
\<standardEndpoints >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <announcementEndpoint>
      <standardEndpoint discoveryVersion="WSDiscovery11/WSDiscoveryApril2005"
                        maxAnnouncementDelay="Timespan"
                        name="String" />
    </announcementEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|discoveryVersion|WS-Discovery protokolünün iki sürümünden birini belirten bir dize. Geçerli değerler WSDiscovery11 ve WSDiscoveryApril2005. Bu değer türünde <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion>.|  
|maxAnnouncementDelay|Bulma protokolünün bir Merhaba ileti göndermeden önce bekleyeceği en büyük değeri belirten bir TimeSpan değeri. İletiler, gönderilmeden önce 0 ile bu özniteliğin değeri arasında rastgele bir zaman değeri bekler. Bu öznitelik, ağ fırtınalarını 'yi engellemek için küçük, rastgele bir gecikme ayarlamak için kullanılır ve tüm hizmetler aynı anda yeniden çevrimiçi duruma gelir.|  
|name|Standart uç nokta yapılandırmasının adını belirten bir dize. Ad, bir standart uç noktayı `endpointConfiguration` yapılandırmaya bağlamak için hizmet uç noktasının özniteliğinde kullanılır.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<standardEndpoints >](standardendpoints.md)|Özelliklerinden biri veya daha fazlası (adres, bağlama, sözleşme) düzeltilen, önceden tanımlanmış uç noktalar koleksiyonu.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, http ve PEERNET üzerinden bildiri iletilerini dinleyen bir istemciyi gösterir.  
  
```xml  
<services>
  <service name="ServiceAnnouncementListener">
    <endpoint name="httpAnnouncementEndpoint"
              kind="announcementEndpoint"
              binding="basicHttpBinding"
              address="announcements" />
    <endpoint name="peerNetAnnouncementEndpoint"
              kind="announcementEndpoint"
              binding="peerTcpBinding"
              address="net.p2p://discoveryMesh/multicast"
              bindingConfiguration="discoveryPeerTcpBindingConfig" />
  ...
  </service>
</services>

<standardEndpoints>
  <announcementEndpoint>
    <standardEndpoint name="httpAnnouncementEndpoint"
                      version="WSDiscoveryApril2005" />
    <standardEndpoint name="peerNetAnnouncementEndpoint"
                      version="WSDiscoveryApril2005" />
  </announcementEndpoint>
</standardEndpoints>
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>
