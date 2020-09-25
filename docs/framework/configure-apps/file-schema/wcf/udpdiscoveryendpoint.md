---
title: <udpDiscoveryEndpoint>
ms.date: 03/30/2017
ms.assetid: 1f485329-2771-43bc-88de-df8f2faa3bb7
ms.openlocfilehash: f02cbddcdd4390d754f93e6f6d9aae6646cb137b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91183630"
---
# \<udpDiscoveryEndpoint>

Bu yapılandırma öğesi, bir UDP çok noktaya yayın bağlaması üzerinde bulma işlemleri için önceden yapılandırılmış bir standart uç nokta tanımlar. Bu uç nokta, sabit bir sözleşmeye sahiptir ve iki WS-bulma protokol sürümünü destekler. Ayrıca, WS-Discovery belirtimleri (WS-Discovery Nisan 2005 veya WS-Discovery V 1.1) içinde belirtilen bir sabit UDP bağlaması ve varsayılan bir adres vardır.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<udpDiscoveryEndpoint>**  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <udpDiscoveryEndpoint>
      <standardEndpoint discoveryMode="Adhoc/Managed"
                        discoveryVersion="WSDiscovery11/WSDiscoveryApril2005"
                        maxResponseDelay="Timespan"
                        multicastAddress="Uri"
                        name="String" />
    </udpDiscoveryEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  

 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|discoveryMode|Bulma protokolünün modunu belirten bir dize. Geçerli değerler şunlardır "geçici" ve "yönetilen". Yönetilen modda protokol, keşfedilebilir hizmetlerin bir deposu görevi gören bir bulma proxy 'Sine dayanır. Geçici mod, kullanılabilir hizmetleri bulmak için protokolün UDP çok noktaya yayın mekanizmasını kullanmasını gerektirir. Bu değer türünde <xref:System.ServiceModel.Discovery.ServiceDiscoveryMode>.|  
|discoveryVersion|WS-Discovery protokolünün iki sürümünden birini belirten bir dize. Geçerli değerler WSDiscovery11 ve WSDiscoveryApril2005. Bu değer türünde <xref:System.ServiceModel.Discovery.DiscoveryVersion>.|  
|maxResponseDelay|Bulma protokolünün, araştırma eşleşmesi veya eşleşmeyi çözme gibi belirli iletileri göndermeden önce bekleyeceği gecikme süresinin en büyük değerini belirten bir TimeSpan değeri.<br /><br /> Tüm Probeeşleri aynı anda gönderiliyorsa, bir ağ fırtınası sonuç verebilir. Bunun oluşmasını önlemek için, Probeeşleşmelerin her bir ProbeMatch arasında rastgele bir gecikmeyle gönderilmesi gerekir. Rastgele gecikme, bu öznitelik tarafından ayarlanan değere 0 aralığındadır. Bu öznitelik 0 olarak ayarlandıysa, Probeeşleşmelerin iletileri herhangi bir gecikme olmadan sıkı bir döngüde gönderilir. Aksi takdirde, Probeeşleşmelerin iletileri, tüm Probeeşleşmelerin iletilerini göndermek için geçen toplam süre maxResponseDelay değerini aşmadığı için bazı rastgele gecikmeyle gönderilir. Bu değer yalnızca hizmetler için geçerlidir, istemciler tarafından kullanılmaz.|  
|multicastAddress|Bulma iletilerini göndermek ve almak için kullanılacak çok noktaya yayın adresini belirten bir URI. Varsayılan değer, protokol belirtimine uyumlu olan çok noktaya yayın adresidir.|  
|`name`|Standart uç nokta yapılandırmasının adını belirten bir dize. Ad, `endpointConfiguration` bir standart uç noktayı yapılandırmaya bağlamak için hizmet uç noktasının özniteliğinde kullanılır.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<udpTransportSettings>](udptransportsettings.md)|UDP uç noktası için UDP aktarımını yapılandırmanıza izin veren ayarların koleksiyonu.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|Özelliklerinden biri veya daha fazlası (adres, bağlama, sözleşme) düzeltilen, önceden tanımlanmış uç noktalar koleksiyonu.|  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, bir UDP çok noktaya yayın aktarımı üzerinden bulma iletilerini dinleyen bir hizmeti gösterir.  
  
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
