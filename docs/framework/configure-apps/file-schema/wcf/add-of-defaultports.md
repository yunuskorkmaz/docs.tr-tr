---
title: <add> / <defaultPorts>
ms.date: 03/30/2017
ms.assetid: f162ce42-963b-4779-96a7-d6d8b4ea0d2f
ms.openlocfilehash: 5200c8893a89488b72c2c71d1a3703bf2aad1235
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704563"
---
# <a name="add-of-defaultports"></a>\<Ekle >, \<defaultPorts >
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
