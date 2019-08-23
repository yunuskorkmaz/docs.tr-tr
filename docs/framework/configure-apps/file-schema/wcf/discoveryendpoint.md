---
title: <discoveryEndpoint>
ms.date: 03/30/2017
ms.assetid: fae2f48b-a635-4e4b-859d-a1432ac37e1c
ms.openlocfilehash: 6bb5be09ea598296f01e186280c45757dee9405d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919141"
---
# <a name="discoveryendpoint"></a>\<discoveryEndpoint >

Bu yapılandırma öğesi, sabit bir bulma sözleşmesiyle standart uç noktayı tanımlar. Hizmet yapılandırmasına eklendiğinde, bulma iletilerinin nerede dinleneceğini belirtir. İstemci yapılandırmasına eklendiğinde, bulma sorgularının nereye gönderileceğini belirtir.  
  
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
| discoveryMode    | Bulma protokolünün modunu belirten bir dize. Geçerli değerler şunlardır "geçici" ve "yönetilen". Yönetilen modda protokol, keşfedilebilir hizmetlerin bir deposu görevi gören bir bulma proxy 'Sine dayanır. Geçici mod, kullanılabilir hizmetleri bulmak için protokolün UDP çok noktaya yayın mekanizmasını kullanmasını gerektirir. Özelliği hakkında daha fazla bilgi için bkz <xref:System.ServiceModel.Discovery.DiscoveryEndpoint.DiscoveryMode%2A>. |  
| discoveryVersion | WS-Discovery protokolünün iki sürümünden birini belirten bir dize. Geçerli değerler WSDiscovery11 ve WSDiscoveryApril2005. Bu değer türünde <xref:System.ServiceModel.Discovery.DiscoveryVersion>. |  
| maxResponseDelay | Bulma protokolünün, araştırma eşleşmesi veya eşleşmeyi çözme gibi belirli iletileri göndermeden önce bekleyeceği gecikme süresinin en büyük değerini belirten bir TimeSpan değeri.<br /><br /> Tüm Probeeşleri aynı anda gönderiliyorsa, bir ağ fırtınası sonuç verebilir. Bunun oluşmasını önlemek için, Probeeşleşmelerin her bir ProbeMatch arasında rastgele bir gecikmeyle gönderilmesi gerekir. Rastgele gecikme, bu öznitelik tarafından ayarlanan değere 0 aralığındadır. Bu öznitelik 0 olarak ayarlandıysa, Probeeşleşmelerin iletileri herhangi bir gecikme olmadan sıkı bir döngüde gönderilir. Aksi takdirde, Probeeşleşmelerin iletileri, tüm Probeeşleşmelerin iletilerini göndermek için geçen toplam süre maxResponseDelay değerini aşmadığı için bazı rastgele gecikmeyle gönderilir. Bu değer yalnızca hizmetler için geçerlidir, istemciler tarafından kullanılmaz. |  
| `name`           | Standart uç nokta yapılandırmasının adını belirten bir dize. Ad, bir standart uç noktayı `endpointConfiguration` yapılandırmaya bağlamak için hizmet uç noktasının özniteliğinde kullanılır. |  
  
### <a name="child-elements"></a>Alt öğeleri

Yok.  
  
### <a name="parent-elements"></a>Üst öğeler

| Öğe | Açıklama |  
| ------- | ----------- |  
| [\<standardEndpoints >](standardendpoints.md) | Özelliklerinden biri veya daha fazlası (adres, bağlama, sözleşme) düzeltilen, önceden tanımlanmış uç noktalar koleksiyonu. |  
  
## <a name="example"></a>Örnek

Aşağıdaki örnek, bir eş ağ çok noktaya yayın aktarımı üzerinden keşif iletilerini dinleyen bir hizmeti gösterir. Örnek, WS-Discovery Nisan 2005 sürümünü açıkça belirtir.  
  
Standart uç nokta yapılandırması hizmet başına tanımlanır ve hizmet genelinde paylaştırılamaz. Başka bir hizmet aynı bulma uç noktasına sahip olmak istiyorsanız, bu hizmetin bölümüne aynı yapılandırmanın eklenmesi gerekir.  
  
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
