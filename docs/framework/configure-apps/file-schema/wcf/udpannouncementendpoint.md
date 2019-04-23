---
title: <udpAnnouncementEndpoint>
ms.date: 03/30/2017
ms.assetid: 5b3fa9c5-f372-4df9-a9d6-1e426063b721
ms.openlocfilehash: 04f5fb27a0da7e553ff3c0308f7fb2e2df2e0b20
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59210015"
---
# <a name="udpannouncementendpoint"></a>\<Udptransportsettings >
Bu yapılandırma öğesi, bir UDP bağlama üzerinden Duyurunun ileti göndermek için hizmetler tarafından kullanılan standart bir uç nokta tanımlar. Bu, sabit bir sözleşme içeriyor ve iki bulma sürümlerini destekler. Buna ek olarak sabit bir UDP bağlama ve WS-bulma (WS-bulma Nisan 2005 veya WS-bulma sürüm 1.1) belirtimleri belirtilen varsayılan adresi değeri vardır. Duyurunun ileti alma ve gönderme için kullanmak üzere çok noktaya yayın adresini belirtebilirsiniz.  
  
\<system.ServiceModel>  
\<standardEndpoints >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <announcementEndpoint>
      <standardEndpoint discoveryVersion="WSDiscovery11/WSDiscoveryApril2005"
                        maxAnnouncementDelay="Timespan"
                        multicastAddress="Uri"
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
|DiscoveryVersion|Bir WS bulma protokolünü iki sürümünü belirten bir dize. Geçerli değerler şunlardır: WSDiscovery11 ve WSDiscoveryApril2005. Bu değer türünde <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion>.|  
|maxAnnouncementDelay|Gecikme için maksimum değeri belirten bir Timespan değeri bulma protokolünü selamlama iletisine göndermeden önce bekleyin. İleti gönderilmeden önce bir rastgele bir zaman değeri 0 ile bu özniteliğin değeri arasında bekler. Bu öznitelik, bir ağ gider ve aynı anda tüm hizmetleri yeniden çevrimiçi duruma ağ fırtınalarını önlemek için küçük, rastgele bir gecikme ayarlamak için kullanılır.|  
|multicastAddress|Bulma ileti alma ve gönderme için kullanılacak bir çok noktaya yayın adresini belirten bir URI. Varsayılan değer uyumlu protokolü belirtimi için çok noktaya yayın adresi gibidir.|  
|name|Standart uç nokta yapılandırmasını adını belirten dize. Adı kullanılıyor `endpointConfiguration` özniteliği bir standart uç noktası yapılandırmasına bağlamak için hizmet uç noktası.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<udpTransportSettings>](udptransportsettings.md)|UDP taşıma için UDP uç nokta yapılandırmanıza olanak tanıyan ayarların koleksiyonudur.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<standardEndpoints >](standardendpoints.md)|Daha fazla (adresi, bağlama, anlaşma) kendi özellik sabit veya olan standart uç noktaları koleksiyonu uç noktaları biriyle önceden tanımlanmış.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir istemci için Duyurunun bir UDP üzerinden dinlemeyi gösterir. çok noktaya yayın adresi ve UDP çok noktaya yayın taşımasıyla varsayılan belirtilen çok noktaya yayın adresi ile çok noktaya yayın aktarma.  
  
```xml  
<services>
  <service name="ServiceAnnouncementListener">
    <endpoint name="udpAnnouncementEndpointStandard"
              kind="udpAnnouncementEndpoint"
              bindingConfiguration="..." />
    <endpoint name="udpAnnouncementEndpoint2"
              kind="udpAnnouncementEndpoint"
              endpointConfiguration="AnnouncementConfiguration3702"
              bindingConfiguration="..." />
    ...
  </service>
</services>
<standardEndpoints>
  <udpAnnouncementEndpoint>
    <standardEndpoint name="AnnouncementConfiguration2"
                      version="WSDiscoveryApril2005"
                      multicastAddress="soap.udp://239.255.255.250:3703"/>
  </udpAnnouncementEndpoint>
</standardEndpoints>
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>
