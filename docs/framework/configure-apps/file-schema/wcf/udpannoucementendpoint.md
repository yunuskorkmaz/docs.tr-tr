---
title: '&lt;udpAnnoucementEndpoint&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5b3fa9c5-f372-4df9-a9d6-1e426063b721
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8dad3ac58b92c70f32b8a0e6a81f8ebb2b23f25c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltudpannoucementendpointgt"></a>&lt;udpAnnoucementEndpoint&gt;
Bu yapılandırma öğesi üzerinde bir UDP bağlama duyuru iletileri göndermek için hizmetler tarafından kullanılan standart bir uç nokta tanımlar. Sabit bir sözleşme sahiptir ve iki bulma sürümlerini destekler. Ayrıca, sabit bir UDP bağlama ve WS-bulma belirtimleri (WS-bulma Nisan 2005 veya WS-bulma sürüm 1.1) belirtildiği gibi varsayılan adres değer içeriyor. Duyurunun ileti alma ve gönderme için kullanmak üzere çok noktaya yayın adresi belirtebilirsiniz.  
  
\<Sistem. ServiceModel >  
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
|discoveryVersion|WS bulma protokolünü iki sürümü birini belirten bir dize. Geçerli değerler WSDiscovery11 ve WSDiscoveryApril2005 ' dir. Bu değer türünde <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion>.|  
|maxAnnouncementDelay|Gecikme için maksimum değeri belirten bir Timespan değerine Bulma Protokolü Hello iletiyi göndermeden önce bekler. İleti gönderilmeden önce bir rastgele saat değeri 0 ile bu özniteliğin değeri arasında bekler. Bu öznitelik, bir ağ gider ve aynı anda tüm hizmetleri tekrar çevrimiçi duruma ağ fırtınalarını önlemek için küçük, rastgele bir gecikme ayarlamak için kullanılır.|  
|multicastAddress|Bulma ileti alma ve gönderme için kullanılacak bir çok noktaya yayın adresini belirtir URI. Varsayılan değer uyumluluğunu protokolü belirtimi için çok noktaya yayın adresi gibidir.|  
|name|Standart uç noktasının yapılandırma adını belirten dize. Adı kullanılıyor `endpointConfiguration` yapılandırmasına standart bir uç noktasını bağlamak için hizmet uç noktası özniteliği.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Udpannouncementendpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/udptransportsettings.md)|UDP taşıma UDP uç noktası için yapılandırmanıza olanak tanıyan ayarlar koleksiyonu.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<standardEndpoints >](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|Standart uç noktalar koleksiyonu uç noktaları biriyle önceden tanımlanmış veya bunların özelliklerinin (adresi, bağlama, sözleşme) daha fazla sabit.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir UDP üzerinden duyuru için dinleme istemci gösterir ile çok noktaya yayın aktarma varsayılan çok noktaya yayın adresi ve UDP belirtilen çok noktaya yayın adresi ile çok noktaya yayın aktarma.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>
