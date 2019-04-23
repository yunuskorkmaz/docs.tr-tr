---
title: <scopes>
ms.date: 03/30/2017
ms.assetid: 9a0dd3ce-e383-4ac3-b7be-7d604388304a
ms.openlocfilehash: 8bc720238ca3039106345783381cd26134fc46b5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59213083"
---
# <a name="scopes"></a>\<kapsamları >
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
