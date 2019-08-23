---
title: <serviceDiscovery>
ms.date: 03/30/2017
ms.assetid: a3c68a4a-fc95-43c5-aacb-785936c0cf39
ms.openlocfilehash: a99edd3a62a40c2efbc63a166b8c0b0d124e8a72
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936270"
---
# <a name="servicediscovery"></a>\<serviceDiscovery >
Hizmet uç noktalarının bulunabilirliğini belirtir.  
  
 \<system.ServiceModel>  
\<davranışlar >  
\<serviceBehaviors>  
\<davranış >  
\<serviceDiscovery >  
  
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
|[\<announcementEndpoint >](announcementendpoint.md)|Duyuru uç noktaları koleksiyonu. Duyuru iletileri göndermek için kullanılacak uç noktaları belirtmek için bu bölümü kullanın.|  
|[\<discoveryEndpoint >](discoveryendpoint.md)|Bulma uç noktaları koleksiyonu. Bulma iletilerinin dinleyeceği uç noktaları belirtmek için bu bölümü kullanın.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<davranış >](behavior-of-endpointbehaviors.md)|Bir davranış öğesi belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Hizmetin davranış yapılandırmasına eklendiğinde, bu yapılandırma öğesi bu hizmetin tüm uç noktalarını bulunabilir hale getirir. Bu uç noktaların bulma özelliklerini, [ \<DiscoveryEndpoint >](discoveryendpoint.md) veya [ \<AnnouncementEndpoint >](announcementendpoint.md) alt öğelerini kullanarak daha ayrıntılı bir şekilde yapılandırabilirsiniz. Hizmet duyuruları göndermek için kullanılacak uç nokta yapılandırmasını belirterek duyuruları yapılandırmak için [ AnnouncementEndpoint>bölümünükullanın(çevrimiçi/Merhabaveçevrimdışı/bye).\<](announcementendpoint.md) Bulma iletilerinin dinleyeceği uç noktayı el ile belirtmek için [ DiscoveryEndpoint>bölümünükullanın.\<](discoveryendpoint.md)  
  
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
