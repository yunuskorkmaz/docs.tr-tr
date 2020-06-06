---
title: <serviceDiscovery>
ms.date: 03/30/2017
ms.assetid: a3c68a4a-fc95-43c5-aacb-785936c0cf39
ms.openlocfilehash: 7ac067e84f2a4d2724e3d8f2d0af9b220fd15538
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399635"
---
# \<serviceDiscovery>
Hizmet uç noktalarının bulunabilirliğini belirtir.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceDiscovery>**  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <serviceDiscovery>
        <announcementEndpoints>
          <endpoint name="String"
                    kind="Type" />
        </announcementEndpoints>
        <discoveryEndpoints>
          <endpoint name="String"
                    kind="Type" />
        </discoveryEndpoints>
      </serviceDiscovery>
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
 Yok.  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<announcementEndpoint>](announcementendpoint.md)|Duyuru uç noktaları koleksiyonu. Duyuru iletileri göndermek için kullanılacak uç noktaları belirtmek için bu bölümü kullanın.|  
|[\<discoveryEndpoint>](discoveryendpoint.md)|Bulma uç noktaları koleksiyonu. Bulma iletilerinin dinleyeceği uç noktaları belirtmek için bu bölümü kullanın.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|Bir davranış öğesi belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Hizmetin davranış yapılandırmasına eklendiğinde, bu yapılandırma öğesi bu hizmetin tüm uç noktalarını bulunabilir hale getirir. [\<discoveryEndpoint>](discoveryendpoint.md)Veya alt öğelerini kullanarak bu uç noktaların bulma özelliklerini daha fazla yapılandırabilirsiniz [\<announcementEndpoint>](announcementendpoint.md) . [\<announcementEndpoint>](announcementendpoint.md)Hizmet duyuruları göndermek için kullanılacak uç nokta yapılandırmasını belirterek duyuruları yapılandırmak için bölümünü kullanın (çevrimiçi/Merhaba ve çevrimdışı/bye). [\<discoveryEndpoint>](discoveryendpoint.md)Bulma iletilerinin dinleyeceği uç noktayı el ile belirtmek için bölümünü kullanın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki yapılandırma örneği, Hesaplatorservice 'in keşfedilecek olduğunu belirtir ve isteğe bağlı olarak kullanılacak duyuru uç noktasını belirtir.  
  
```xml  
<services>
  <service name="CalculatorService"
           behaviorConfiguration="CalculatorServiceBehavior">
    ...
  </service>
</services>
<behaviors>
  <serviceBehaviors>
    <behavior name="CalculatorServiceBehavior">
      <serviceDiscovery>
        <announcementEndpoints>
          <endpoint name="udpEndpoint"
                    kind="udpAnnouncementEndpoint" />
        </announcementEndpoints>
      </serviceDiscovery>
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>
