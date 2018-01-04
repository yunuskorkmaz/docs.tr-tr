---
title: '&lt;webHttp&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1f9d0754-d41e-44ce-a298-e51cb3096c64
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6b488d4e4884f92b107b2b6be71827a2f8b4cdbf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltwebhttpgt"></a>&lt;webHttp&gt;
Bu öğe belirtir <xref:System.ServiceModel.Description.WebHttpBehavior> yapılandırma yoluyla bir uç noktada. İle birlikte kullanıldığında bu davranış, [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) standart bağlama sağlayan Web programlama modeli için bir [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] hizmet.  
  
 \<Sistem. ServiceModel >  
\<davranışları >  
\<endpointBehaviors >  
\<davranışı >  
\<webHttp >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<webHttp />  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|automaticFormatSelectionEnabled|Bu özellik ayarlandığında `true`, WCF altyapı kullanmak için en iyi biçimini belirler. Otomatik Biçim Seçimi varsayılan olarak devre dışıdır için geriye dönük uyumluluk. Otomatik Biçim Seçimi program aracılığıyla veya yapılandırma yoluyla etkinleştirilebilir.|  
|defaultBodyStyle|Döndürülen iletilerini varsayılan gövde stilini belirtir. [!INCLUDE[crdefault](../../../../../includes/crdefault-md.md)]<xref:System.ServiceModel.Web.WebMessageBodyStyle> ve [WCF Web HTTP biçimlendirme](../../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).|  
|defaultOutgoingResponseFormat|İletileri için varsayılan giden yanıt biçimi belirtir. [!INCLUDE[crdefault](../../../../../includes/crdefault-md.md)][WCF Web HTTP biçimlendirme](../../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).|  
|faultExceptionEnabled|Bir iç sunucu hatası olduğunda bir FaultException oluşturulup oluşturulmayacağını belirten bir bayrak alır veya ayarlar (HTTP durum kodu: 500) oluşur.|  
|helpEnabled|Alır veya yardım sayfasına etkin olup olmadığını belirleyen bir değer ayarlar.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<davranışı >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Uç nokta davranışları kümesini belirtir.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Configuration.WebHttpElement>  
 <xref:System.ServiceModel.Description.WebHttpBehavior>  
 [AJAX Tümleştirme ve JSON Desteği](../../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md)  
 [\<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md)
