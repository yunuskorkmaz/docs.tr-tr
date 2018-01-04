---
title: '&lt;webHttpEndpoint&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ecaaeb6f-ebd0-411d-8b53-92477cd45347
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fc45511e0e7b4644704a834f0bc08d64ff3367f3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltwebhttpendpointgt"></a>&lt;webHttpEndpoint&gt;
Bu yapılandırma öğesi bir sabit ile standart bir uç nokta tanımlayan [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) otomatik olarak bağlama ekler [ \<webHttp >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md) davranışı. Bu uç noktaya bir REST hizmeti yazarken kullanın.  
  
\<Sistem. ServiceModel >  
\<standardEndpoints >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>
    <webHttpEndpoint>
      <standardEndpoint automaticFormatSelectionEnabled="String" 
                        defaultOutgoingResponseFormat="Xml/Json" 
                        helpEnabled="Boolean" 
                        webEndpointType="String"/>
    </webHttpEndpoint>
  </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|automaticFormatSelectionEnabled|Otomatik Biçim Seçimi etkin olup olmadığını gösteren bir Boole değeri.<br /><br /> Otomatik Biçim Seçimi etkin olduğunda, altyapı ayrıştırır `Accept` istek iletisinin üstbilgi ve en uygun yanıt biçimi belirler. Varsa `Accept` üstbilgisi, uygun yanıt biçimi belirtmiyor, altyapısını kullanan `Content-Type` istek iletisi ya da işlemi varsayılan yanıt biçimi.|  
|defaultOutgoingResponseFormat|Varsayılan giden yanıt biçimi belirten bir özniteliği. Bu özniteliktir <xref:System.ServiceModel.Web.WebMessageFormat> türü|  
|helpEnabled|HTTP Yardım sayfası uç nokta için etkinleştirilip etkinleştirilmediğini gösteren bir Boole değeri.|  
|webEndpointType|Uç nokta türünü belirten bir dize.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<standardEndpoints >](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|Standart uç noktalar koleksiyonu uç noktaları biriyle önceden tanımlanmış veya bunların özelliklerinin (adresi, bağlama, sözleşme) daha fazla sabit.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Description.WebHttpEndpoint>  
 <xref:System.ServiceModel.Configuration.WebHttpEndpointElement>
