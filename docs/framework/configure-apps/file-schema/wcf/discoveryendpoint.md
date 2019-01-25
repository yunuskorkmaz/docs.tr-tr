---
title: '&lt;DiscoveryEndpoint&gt;'
ms.date: 03/30/2017
ms.assetid: fae2f48b-a635-4e4b-859d-a1432ac37e1c
ms.openlocfilehash: b3254a1c3d7fa581b4f7573d693261f5a224515d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54524175"
---
# <a name="ltdiscoveryendpointgt"></a>&lt;DiscoveryEndpoint&gt;

Bu yapılandırma öğesi, bir sabit keşif sözleşmesiyle standart uç nokta tanımlar. Hizmet yapılandırmasında eklendiğinde bulma iletileri dinlemek nereye belirtir. İstemci yapılandırmasına eklendiğinde bulma sorguları gönderileceği belirtir.  
  
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
| discoveryMode    | Bulma kuralının modu belirten bir dize. Geçerli değerler şunlardır: "Geçici" ve "Yönetilen". Yönetilen modda bir bulunabilir hizmet deposu olarak hareket eden bir keşif proxy'si, protokolü kullanır. Anlık mod gerektirir UDP kullanılacak protokolü kullanılabilir hizmetleri bulmak için çok noktaya yayın mekanizması. Özelliği hakkında daha fazla bilgi için bkz. <xref:System.ServiceModel.Discovery.DiscoveryEndpoint.DiscoveryMode%2A>. |  
| DiscoveryVersion | Bir WS bulma protokolünü iki sürümünü belirten bir dize. Geçerli değerler şunlardır: WSDiscovery11 ve WSDiscoveryApril2005. Bu değer türünde <xref:System.ServiceModel.Discovery.DiscoveryVersion>. |  
| maxResponseDelay | Araştırma eşleşme veya eşleşme gidermek gibi belirli iletileri göndermeden önce gecikme Bulma Protokolü için maksimum değeri belirten bir Timespan değeri bekler.<br /><br /> Aynı anda tüm ProbeMatches gönderiliyorsa, ağ storm neden olabilir. Bunun gerçekleşmesini önlemek için her ProbeMatch arasında rastgele bir gecikme ile ProbeMatches gönderilir. Bu öznitelik tarafından ayarlanan değer için 0 aralığındaki rastgele gecikme var. Bu öznitelik 0 olarak ayarlanırsa, herhangi bir gecikme olmadan sıkı bir döngüde ProbeMatches iletileri gönderilir. Aksi takdirde, tüm ProbeMatches ileti göndermek için geçen toplam süre maxResponseDelay aşmayacak şekilde ProbeMatches iletileri rastgele bir gecikme süresi ile gönderilir. Bu değer yalnızca hizmetler için geçerlidir, istemciler tarafından kullanılmaz. |  
| `name`           | Standart uç nokta yapılandırmasını adını belirten dize. Adı kullanılıyor `endpointConfiguration` özniteliği bir standart uç noktası yapılandırmasına bağlamak için hizmet uç noktası. |  
  
### <a name="child-elements"></a>Alt öğeleri

Yok.  
  
### <a name="parent-elements"></a>Üst öğeler

| Öğe | Açıklama |  
| ------- | ----------- |  
| [\<standardEndpoints >](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md) | Daha fazla (adresi, bağlama, anlaşma) kendi özellik sabit veya olan standart uç noktaları koleksiyonu uç noktaları biriyle önceden tanımlanmış. |  
  
## <a name="example"></a>Örnek

Aşağıdaki örnek, bir ağ çok noktaya yayın eş bulma iletileri dinleyen bir hizmeti gösterir. Örneğin, WS-bulma açıkça belirtir Nisan 2005 sürümü.  
  
Standart uç nokta yapılandırması hizmete göre tanımlanır ve hizmet arasında paylaşılamaz. Başka bir hizmete sahip aynı bulma uç noktası istiyorsanız, aynı yapılandırmayı hizmetin bölümüne eklenmesi gerekir.  
  
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

- <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>
