---
description: 'Hakkında daha fazla bilgi edinin: <webHttp>'
title: <webHttp>
ms.date: 03/30/2017
ms.assetid: 1f9d0754-d41e-44ce-a298-e51cb3096c64
ms.openlocfilehash: acd8d77e00828d132d076c867ff3164ca1ba7230
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99664385"
---
# \<webHttp>

Bu öğe, <xref:System.ServiceModel.Description.WebHttpBehavior> yapılandırma yoluyla bir uç nokta üzerinde belirtir. Bu davranış, [\<webHttpBinding>](webhttpbinding.md) Standart bağlama birlikte kullanıldığında, bir Windows Communication Foundation (WCF) hizmeti Için Web programlama modeline izin vermez.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webHttp>**  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<webHttp />
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  

 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|automaticFormatSelectionEnabled etkin|Bu özellik olarak ayarlandığında `true` , WCF altyapısı kullanılacak en iyi biçimi belirler. Otomatik Biçim seçimi, geriye doğru uyumluluk için varsayılan olarak devre dışıdır. Otomatik Biçim Seçimi programlı bir şekilde veya yapılandırma aracılığıyla etkinleştirilebilir.|  
|defaultBodyStyle|Döndürülen iletilerin varsayılan gövde stilini belirtir. Daha fazla bilgi için bkz <xref:System.ServiceModel.Web.WebMessageBodyStyle> . ve [WCF Web http biçimlendirmesi](../../../wcf/feature-details/wcf-web-http-formatting.md).|  
|defaultOutgoingResponseFormat|İletiler için varsayılan giden yanıt biçimini belirtir. Daha fazla bilgi için bkz. [WCF Web http biçimlendirmesi](../../../wcf/feature-details/wcf-web-http-formatting.md).|  
|faultExceptionEnabled|Bir iç sunucu hatası (HTTP durum kodu: 500) oluştuğunda bir FaultException oluşturulup oluşturulmayacağını belirten bayrağı alır veya ayarlar.|  
|Yardım etkin|Yardım sayfasının etkinleştirilip etkinleştirilmediğini belirleyen bir değer alır veya ayarlar.|  
  
### <a name="child-elements"></a>Alt Öğeler  

 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|Uç nokta davranışları kümesini belirtir.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.WebHttpElement>
- <xref:System.ServiceModel.Description.WebHttpBehavior>
- [AJAX Tümleştirme ve JSON Desteği](../../../wcf/feature-details/ajax-integration-and-json-support.md)
- [\<webHttpBinding>](webhttpbinding.md)
