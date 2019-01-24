---
title: '&lt;defaultPorts&gt; &lt;ekleme&gt;'
ms.date: 03/30/2017
ms.assetid: f162ce42-963b-4779-96a7-d6d8b4ea0d2f
ms.openlocfilehash: 8b7a4730af6690616058a91cf23bb39734d81abc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54541722"
---
# <a name="ltaddgt-of-ltdefaultportsgt"></a>&lt;defaultPorts&gt; &lt;ekleme&gt;
İstemci uygulamasının dinleyeceği bir varsayılan iletişim bitiş noktaları.  
  
 \<system.ServiceModel>  
\<davranışlar >  
\<serviceBehaviors>  
\<davranışı >  
\<useRequestHeadersForMetadataAddress >  
\<defaultPorts >  
\<Ekle >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add port="Integer"
         scheme="String" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|bağlantı noktası|Varsayılan iletişim bağlantı noktası numarasını belirten bir tamsayı|  
|düzen|Bir iletişim bağlantı noktası ile ilişkili protokol ayarları grubunu belirten bir dize.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<defaultPorts >](../../../../../docs/framework/configure-apps/file-schema/wcf/defaultports.md)|İstemci uygulamasının dinleyeceği, varsayılan iletişim bitiş noktalarını listeleyen varsayılan bağlantı noktaları koleksiyonu.|  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.ServiceModel.Configuration.DefaultPortElement>
