---
title: <webHttpEndpoint>
ms.date: 03/30/2017
ms.assetid: ecaaeb6f-ebd0-411d-8b53-92477cd45347
ms.openlocfilehash: 866be522cb1c64142227a8d6a1a8f88551ca9105
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940479"
---
# <a name="webhttpendpoint"></a>\<webHttpEndpoint >
Bu yapılandırma öğesi [ ,\<Web http >](webhttp.md) davranışını otomatik olarak ekleyen bir fixed [ \<WebHttpBinding >](webhttpbinding.md) bağlaması ile standart bir uç nokta tanımlar. Bir REST hizmeti yazarken bu uç noktayı kullanın.  
  
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
|automaticFormatSelectionEnabled etkin|Otomatik biçim seçiminin etkin olup olmadığını gösteren bir Boole değeri.<br /><br /> Otomatik Biçim Seçimi etkinleştirildiğinde altyapı, istek iletisinin `Accept` üstbilgisini ayrıştırır ve en uygun yanıt biçimini belirler. Üst bilgi uygun bir yanıt biçimi belirtmezse, altyapı istek iletisini veya işlemin varsayılan `Content-Type` yanıt biçimini kullanır. `Accept`|  
|defaultOutgoingResponseFormat|Varsayılan giden yanıt biçimini belirten bir özniteliği. Bu öznitelik <xref:System.ServiceModel.Web.WebMessageFormat> türü|  
|Yardım etkin|Uç nokta için HTTP yardım sayfasının etkinleştirilip etkinleştirilmediğini belirten bir Boolean değer.|  
|webEndpointType|Uç noktanın türünü belirten bir dize.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<standardEndpoints >](standardendpoints.md)|Özelliklerinden biri veya daha fazlası (adres, bağlama, sözleşme) düzeltilen, önceden tanımlanmış uç noktalar koleksiyonu.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Description.WebHttpEndpoint>
- <xref:System.ServiceModel.Configuration.WebHttpEndpointElement>
