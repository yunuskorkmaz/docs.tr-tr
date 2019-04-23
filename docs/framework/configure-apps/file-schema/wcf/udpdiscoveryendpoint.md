---
title: <udpDiscoveryEndpoint>
ms.date: 03/30/2017
ms.assetid: 1f485329-2771-43bc-88de-df8f2faa3bb7
ms.openlocfilehash: 180763404ee9070e9ed6e5476d4568a0a018dcb3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59203372"
---
# <a name="udpdiscoveryendpoint"></a>\<udpDiscoveryEndpoint >
Bu yapılandırma öğesi, bir UDP üzerinden bulma işlemleri için önceden yapılandırılmış olan bir standart uç nokta tanımlar. çok noktaya yayın bağlaması. Bu uç nokta, sabit bir sözleşme içeriyor ve iki WS bulma protokolünü sürümlerini destekler. Ayrıca, sabit bir UDP bağlama ve WS-bulma belirtimleri (WS-bulma Nisan 2005 veya WS-bulma V1.1) belirtildiği gibi varsayılan bir adresi vardır.  
  
 \<system.ServiceModel>  
\<standardEndpoints >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <discoveryEndpoint>
      <standardEndpoint discoveryMode="Adhoc/Managed"
                        discoveryVersion="WSDiscovery11/WSDiscoveryApril2005"
                        maxResponseDelay="Timespan"
                        multicastAddress="Uri"
                        name="String" />
    </discoveryEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|discoveryMode|Bulma kuralının modu belirten bir dize. Geçerli değerler şunlardır: "Geçici" ve "Yönetilen". Yönetilen modda bir bulunabilir hizmet deposu olarak hareket eden bir keşif proxy'si, protokolü kullanır. Anlık mod gerektirir UDP kullanılacak protokolü kullanılabilir hizmetleri bulmak için çok noktaya yayın mekanizması. Bu değer türünde <xref:System.ServiceModel.Discovery.ServiceDiscoveryMode>.|  
|DiscoveryVersion|Bir WS bulma protokolünü iki sürümünü belirten bir dize. Geçerli değerler şunlardır: WSDiscovery11 ve WSDiscoveryApril2005. Bu değer türünde <xref:System.ServiceModel.Discovery.DiscoveryVersion>.|  
|maxResponseDelay|Araştırma eşleşme veya eşleşme gidermek gibi belirli iletileri göndermeden önce gecikme Bulma Protokolü için maksimum değeri belirten bir Timespan değeri bekler.<br /><br /> Aynı anda tüm ProbeMatches gönderiliyorsa, ağ storm neden olabilir. Bunun gerçekleşmesini önlemek için her ProbeMatch arasında rastgele bir gecikme ile ProbeMatches gönderilir. Bu öznitelik tarafından ayarlanan değer için 0 aralığındaki rastgele gecikme var. Bu öznitelik 0 olarak ayarlanırsa, herhangi bir gecikme olmadan sıkı bir döngüde ProbeMatches iletileri gönderilir. Aksi takdirde, tüm ProbeMatches ileti göndermek için geçen toplam süre maxResponseDelay aşmayacak şekilde ProbeMatches iletileri rastgele bir gecikme süresi ile gönderilir. Bu değer yalnızca hizmetler için geçerlidir, istemciler tarafından kullanılmaz.|  
|multicastAddress|Bulma ileti alma ve gönderme için kullanılacak bir çok noktaya yayın adresini belirten bir URI. Varsayılan değer uyumlu protokolü belirtimi için çok noktaya yayın adresi gibidir.|  
|`name`|Standart uç nokta yapılandırmasını adını belirten dize. Adı kullanılıyor `endpointConfiguration` özniteliği bir standart uç noktası yapılandırmasına bağlamak için hizmet uç noktası.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<udpTransportSettings>](../../../../../docs/framework/configure-apps/file-schema/wcf/udptransportsettings.md)|UDP taşıma için UDP uç nokta yapılandırmanıza olanak tanıyan ayarların koleksiyonudur.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<standardEndpoints >](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|Daha fazla (adresi, bağlama, anlaşma) kendi özellik sabit veya olan standart uç noktaları koleksiyonu uç noktaları biriyle önceden tanımlanmış.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir UDP üzerinden bulma iletiler için dinleme hizmet gösterir. çok noktaya yayın taşıma.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>
