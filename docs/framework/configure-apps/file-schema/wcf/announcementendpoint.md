---
title: <announcementEndpoint>
ms.date: 03/30/2017
ms.assetid: 034b7c69-a770-4502-8cef-38007bbcd025
ms.openlocfilehash: decaaa1cea5345ff971b16cbb20a85dd803a52d5
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850290"
---
# \<announcementEndpoint>
Bu yapılandırma öğesi, bir sabit duyuru sözleşmesiyle standart uç noktayı tanımlar. Bir hizmet, isteğe bağlı olarak açık veya kapalı olduğunda bir çevrimiçi ve çevrimdışı duyuru iletisi göndererek kullanılabilirliğini duyurur. Windows Communication Foundation (WCF) hizmeti, öğesindeki duyuru uç noktalarını belirtir [\<serviceDiscovery>](servicediscovery.md) ve duyuruları gerçekleştirmek Için AnnouncementClient kullanır. Diğer hizmetten gelen duyuruyu dinlemek isteyen bir istemci aslında bir WCF hizmeti olarak davranır; Bu nedenle, bölümünde söz konusu istemcinin duyuru uç noktalarını yapılandırmanız gerekir [\<services>](services.md) .  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<announcementEndpoint>**  
  
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
|name|Standart uç nokta yapılandırmasının adını belirten bir dize. Ad, `endpointConfiguration` bir standart uç noktayı yapılandırmaya bağlamak için hizmet uç noktasının özniteliğinde kullanılır.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|Özelliklerinden biri veya daha fazlası (adres, bağlama, sözleşme) düzeltilen, önceden tanımlanmış uç noktalar koleksiyonu.|  
  
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
