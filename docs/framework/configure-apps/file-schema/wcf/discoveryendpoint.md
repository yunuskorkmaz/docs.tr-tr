---
title: '&lt;DiscoveryEndpoint&gt;'
ms.date: 03/30/2017
ms.assetid: fae2f48b-a635-4e4b-859d-a1432ac37e1c
ms.openlocfilehash: 6a352fbfced08001f76dceaff283d6bca25f56f9
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltdiscoveryendpointgt"></a>&lt;DiscoveryEndpoint&gt;

Bu yapılandırma öğesi, standart bir uç nokta sabit bulma sözleşme ile tanımlar. Hizmet yapılandırmasında eklendiğinde, bulma iletilerini dinlemek konumu belirtir. İstemci yapılandırmasında eklendiğinde bulma sorguları göndermek konumu belirtir.  
  
\<system.serviceModel>  
\<standardEndpoints >  
  
## <a name="syntax"></a>Sözdizimi

```xml
<system.serviceModel>
  <standardEndpoints>
    <discoveryEndpoint>
      <standardEndpoint discoveryMode="Adhoc/Managed" 
                        discoveryVersion="WSDiscovery11/WSDiscoveryApril2005" 
                        maxResponseDelay="Timespan" 
                        name="String" />
    </discoveryEndpoint>
  </standardEndpoints>
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler

Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler

| Öznitelik        | Açıklama |  
| ---------------- | ----------- |  
| discoveryMode    | Keşif Protokolü modu belirten bir dize. Geçerli değerler "Geçici" ve "Yönetilen" dir. Yönetilen modunda bulunabilirlik Hizmetleri depo olarak davranan bir keşif proxy'si, protokolünü kullanır. Adhoc modu, UDP kullanılacak protokolü gerektirir kullanılabilir hizmetler bulmak için çok noktaya yayın mekanizması. Özelliği hakkında daha fazla bilgi için bkz: <xref:System.ServiceModel.Discovery.DiscoveryEndpoint.DiscoveryMode%2A>. |  
| discoveryVersion | WS bulma protokolünü iki sürümü birini belirten bir dize. Geçerli değerler WSDiscovery11 ve WSDiscoveryApril2005 ' dir. Bu değer türünde <xref:System.ServiceModel.Discovery.DiscoveryVersion>. |  
| maxResponseDelay | Keşif Protokolü gecikme için maksimum değeri belirten bir Timespan değerine araştırma eşleşme veya eşleşme çözmek gibi belirli iletileri göndermeden önce bekler.<br /><br /> Aynı anda tüm ProbeMatches gönderirse ağ storm neden olabilir. Bu oluşmasını önlemek için her ProbeMatch arasında rastgele bir gecikme ile ProbeMatches gönderilir. Bu öznitelik tarafından ayarlanan değer için 0 aralığı rastgele gecikmeyi kullanılıyor. Bu öznitelik 0 olarak ayarlanırsa, ProbeMatches iletileri sıkı bir döngü herhangi bir gecikme olmadan gönderilir. Aksi takdirde, tüm ProbeMatches iletileri göndermek için geçen toplam süre maxResponseDelay aşmadığından emin ProbeMatches iletileri bazı rastgele gecikme ile gönderilir. Bu değer yalnızca Hizmetleri için geçerlidir, istemciler tarafından kullanılmaz. |  
| `name`           | Standart uç noktasının yapılandırma adını belirten dize. Adı kullanılıyor `endpointConfiguration` yapılandırmasına standart bir uç noktasını bağlamak için hizmet uç noktası özniteliği. |  
  
### <a name="child-elements"></a>Alt öğeleri

Yok.  
  
### <a name="parent-elements"></a>Üst öğeler

| Öğe | Açıklama |  
| ------- | ----------- |  
| [\<standardEndpoints >](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md) | Standart uç noktalar koleksiyonu uç noktaları biriyle önceden tanımlanmış veya bunların özelliklerinin (adresi, bağlama, sözleşme) daha fazla sabit. |  
  
## <a name="example"></a>Örnek

Aşağıdaki örnek, bulma iletileri eş net çok noktaya yayın aktarım üzerinde dinleyen bir hizmeti gösterir. WS-bulma örnek açıkça belirtir Nisan 2005 sürümü.  
  
Standart uç nokta yapılandırması her hizmeti tanımlanır ve hizmet arasında paylaşılamaz. Başka bir hizmet aynı bulma uç nokta içerecek şekilde almak istiyorsanız, aynı yapılandırmayı hizmetin bölümüne eklenmesi gerekir.  
  
```xml
<services>  
  <service name="CalculatorService"
           behaviorConfiguration="CalculatorServiceBehavior">
    <endpoint binding="basicHttpBinding" 
              address="calculator" 
              contract="ICalculatorService" />  
    <endpoint name="peerNetDiscovery"  
              binding="peerTcpBinding"  
              address="net.p2p://discoveryMesh/multicast"  
              kind="discoveryEndpoint"  
              endpointConfiguration="peerTcpDiscoveryEndpointConfiguration"  
              bindingConfiguration="discoveryPeerTcpBindingConfig" />      
  </service>  
</services>  
<standardEndpoints>  
  <discoveryEndpoint>  
    <standardEndpoint name="peerTcpDiscoveryEndpointConfiguration"                         
                      version="WSDiscoveryApril2005" />  
  </discoveryEndpoint>  
</standardEndpoints>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

<xref:System.ServiceModel.Discovery.DiscoveryEndpoint>
