---
title: '&lt;udpDiscoveryEndpoint&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1f485329-2771-43bc-88de-df8f2faa3bb7
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8d8758e5126be13d61f2b3dd85f0b3b472c42ae1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltudpdiscoveryendpointgt"></a>&lt;udpDiscoveryEndpoint&gt;
Bu yapılandırma öğesi UDP üzerinden bulma işlemleri için önceden yapılandırılmış olan standart bir uç nokta tanımlayan çok noktaya yayın bağlama. Bu uç noktaya sabit bir sözleşme var ve iki WS bulma protokolünü sürümlerini destekler. Ayrıca, sabit bir UDP bağlama ve WS-bulma belirtimleri (WS-bulma Nisan 2005 veya WS-bulma V1.1) belirtildiği gibi varsayılan bir adresi olan...  
  
 \<Sistem. ServiceModel >  
\<standardEndpoints >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<system.serviceModel>  
    <standardEndpoints>       <discoveryEndpoint>           <standardEndpoint                  discoveryMode="Adhoc/Managed"                  discoveryVersion="WSDiscovery11/WSDiscoveryApril2005"                  maxResponseDelay="Timespan"                  multicastAddress="Uri"                   name="String" />       </discoveryEndpoint>            </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|discoveryMode|Keşif Protokolü modu belirten bir dize. Geçerli değerler "Geçici" ve "Yönetilen" dir. Yönetilen modunda bulunabilirlik Hizmetleri depo olarak davranan bir keşif proxy'si, protokolünü kullanır. Adhoc modu, UDP kullanılacak protokolü gerektirir kullanılabilir hizmetler bulmak için çok noktaya yayın mekanizması. Bu değer türünde <xref:System.ServiceModel.Discovery.ServiceDiscoveryMode>.|  
|discoveryVersion|WS bulma protokolünü iki sürümü birini belirten bir dize. Geçerli değerler WSDiscovery11 ve WSDiscoveryApril2005 ' dir. Bu değer türünde <xref:System.ServiceModel.Discovery.DiscoveryVersion>.|  
|maxResponseDelay|Keşif Protokolü gecikme için maksimum değeri belirten bir Timespan değerine araştırma eşleşme veya eşleşme çözmek gibi belirli iletileri göndermeden önce bekler.<br /><br /> Aynı anda tüm ProbeMatches gönderirse ağ storm neden olabilir. Bu oluşmasını önlemek için her ProbeMatch arasında rastgele bir gecikme ile ProbeMatches gönderilir. Bu öznitelik tarafından ayarlanan değer için 0 aralığı rastgele gecikmeyi kullanılıyor. Bu öznitelik 0 olarak ayarlanırsa, ProbeMatches iletileri sıkı bir döngü herhangi bir gecikme olmadan gönderilir. Aksi takdirde, tüm ProbeMatches iletileri göndermek için geçen toplam süre maxResponseDelay aşmadığından emin ProbeMatches iletileri bazı rastgele gecikme ile gönderilir. Bu değer yalnızca Hizmetleri için geçerlidir, istemciler tarafından kullanılmaz.|  
|multicastAddress|Bulma ileti alma ve gönderme için kullanılacak bir çok noktaya yayın adresini belirtir URI. Varsayılan değer uyumluluğunu protokolü belirtimi için çok noktaya yayın adresi gibidir.|  
|`name`|Standart uç noktasının yapılandırma adını belirten dize. Adı kullanılıyor `endpointConfiguration` yapılandırmasına standart bir uç noktasını bağlamak için hizmet uç noktası özniteliği.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Udpannouncementendpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/udptransportsettings.md)|UDP taşıma UDP uç noktası için yapılandırmanıza olanak tanıyan ayarlar koleksiyonu.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<standardEndpoints >](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|Standart uç noktalar koleksiyonu uç noktaları biriyle önceden tanımlanmış veya bunların özelliklerinin (adresi, bağlama, sözleşme) daha fazla sabit.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir UDP üzerinden bulma iletiler için dinleme hizmeti gösterir çok noktaya yayın taşıma.  
  
```xml
<services>  
  <service name="CalculatorService"  
           behaviorConfiguration="CalculatorServiceBehavior">  
    <endpoint binding="basicHttpBinding"   
              address="calculator" 
              contract="ICalculatorService" />  
    <endpoint name="DiscoveryEndpoint"  
              kind="udpDiscoveryEndpoint" />  
  </service>  
  <standardEndpoints>  
    <udpDiscoveryEndpoint>  
      <standardEndpoint name="DiscoveryEndpoint"                         
                        version="WSDiscoveryApril2005" />  
    </udpDiscoveryEndpoint>  
  </standardEndpoints>
</services>
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>
