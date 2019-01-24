---
title: '&lt;Kapsamları&gt;'
ms.date: 03/30/2017
ms.assetid: 9a0dd3ce-e383-4ac3-b7be-7d604388304a
ms.openlocfilehash: 1235b483f63ab71405803c16f2d3c9926b15cfad
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54642993"
---
# <a name="ltscopesgt"></a>&lt;Kapsamları&gt;
Özel kapsam sorgu sırasında hizmet bitiş noktası süzmek için kullanılan bir URI'leri belirten yapılandırma öğelerinin bir koleksiyonunu içerir.  
  
\<system.ServiceModel>  
\<davranışlar >  
\<endpointBehaviors>  
\<davranışı >  
\<endpointDiscovery >  
\<kapsamları >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="String">
      <endpointDiscovery enable="Boolean">
        <scopes>
          <add scope="URI" />
        </scopes>
      </endpointDiscovery>
    </behavior>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
 Yok.  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|[\<Ekle >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-scopes.md)|Eşleşme ölçütlerinde Hizmetleri bulmak için kullanılabilir uç nokta için kapsam bilgileri ekler.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<endpointDiscovery >](../../../../../docs/framework/configure-apps/file-schema/wcf/endpointdiscovery.md)|Bir uç nokta bulunabilirliği, kapsamı ve meta verilerine özel uzantıları gibi çeşitli bulma ayarlarını belirtir.|  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
