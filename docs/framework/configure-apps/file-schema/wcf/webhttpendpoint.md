---
title: <webHttpEndpoint>
ms.date: 03/30/2017
ms.assetid: ecaaeb6f-ebd0-411d-8b53-92477cd45347
ms.openlocfilehash: 6fb31fca6ac38f6cb92ef087cc277a4d5066521c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59182461"
---
# <a name="webhttpendpoint"></a>\<webHttpEndpoint >
Bu yapılandırma öğesi ile bir sabit bir standart uç nokta tanımlar [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) otomatik olarak bağlama ekler [ \<webHttp >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md) davranışı. Bir REST hizmeti yazarken Bu uç noktayı kullanın.  
  
\<system.ServiceModel>  
\<standardEndpoints >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <webHttpEndpoint>
      <standardEndpoint automaticFormatSelectionEnabled="String"
                        defaultOutgoingResponseFormat="Xml/Json"
                        helpEnabled="Boolean"
                        webEndpointType="String" />
    </webHttpEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|automaticFormatSelectionEnabled|Otomatik Biçim Seçimi etkin olup olmadığını gösteren bir Boole değeri.<br /><br /> Otomatik Biçim Seçimi etkinleştirildiğinde altyapı ayrıştırır `Accept` istek iletisinin üst bilgi ve en uygun yanıt biçimi belirler. Varsa `Accept` üstbilgisi, uygun yanıt biçimi belirtmiyor, altyapısını kullanan `Content-Type` istek iletisi veya işlemin varsayılan yanıt biçimi.|  
|defaultOutgoingResponseFormat|Varsayılan giden yanıt biçimini belirten bir özniteliği. Bu özniteliktir <xref:System.ServiceModel.Web.WebMessageFormat> türü|  
|helpEnabled|Uç nokta için HTTP Yardım sayfasının etkinleştirilip etkinleştirilmeyeceğini gösteren bir Boole değeri.|  
|webEndpointType|Uç nokta türünü belirten bir dize.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<standardEndpoints >](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|Daha fazla (adresi, bağlama, anlaşma) kendi özellik sabit veya olan standart uç noktaları koleksiyonu uç noktaları biriyle önceden tanımlanmış.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Description.WebHttpEndpoint>
- <xref:System.ServiceModel.Configuration.WebHttpEndpointElement>
