---
title: '&lt;standardEndpoints&gt;'
ms.date: 03/30/2017
ms.assetid: d62153d7-a6e6-462a-a784-cca61e9c2ba1
ms.openlocfilehash: f3851ed4d6a166cf698a5acf18f92e29bb7545cc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54666702"
---
# <a name="ltstandardendpointsgt"></a>&lt;standardEndpoints&gt;
Bu yapılandırma bölümü yeniden kullanılabilen önceden yapılandırılmış uç noktalar olan standart uç noktalarının bir koleksiyonunu tanımlamanıza olanak sağlar. Bir standart uç nokta gerekir veya daha fazla adresi, bağlama ve sözleşme öznitelikleri için sabit bir değer. Örneğin, bulma uç noktası sözleşme sabittir. Standart uç noktaları, yeni özellikleri benzer özel bağlamaları tanımlamak için olan hizmet uç noktası genişletmek için de kullanabilirsiniz.  
  
 \<system.ServiceModel>  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
 Yok.  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<announcementEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/announcementendpoint.md)|Bir sabit duyuru sözleşmesiyle standart uç nokta tanımlar. Bir hizmet isteğe bağlı olarak, açık veya kapalı sırasıyla bir çevrimiçi ve çevrimdışı duyuru iletisi göndererek duyurmaktan. Bir Windows Communication Foundation (WCF) hizmeti duyurusunu uç noktaların belirtir [ \<serviceDiscovery >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) öğesi ve duyuruları gerçekleştirmek için AnnouncementClient kullanır. Diğer hizmetinden duyuru için dinleme isteyen bir istemci aslında bir WCF hizmeti olarak hareket; Bu istemci için Duyurunun uç noktaları yapılandırmak zorunda böylece [ \<Hizmetleri >](../../../../../docs/framework/configure-apps/file-schema/wcf/services.md) bölümü.|  
|[\<discoveryEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryendpoint.md)|Bir sabit keşif sözleşmesiyle standart uç nokta tanımlar. Hizmet yapılandırmasında eklendiğinde bulma iletileri dinlemek nereye belirtir. İstemci yapılandırmasına eklendiğinde bulma sorguları gönderileceği belirtir.|  
|[\<dynamicEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/dynamicendpoint.md)|Bu yapılandırma öğesi, çalışma zamanında dinamik olarak uç nokta adresini bulabilirsiniz bir istemci programı olarak çalışması bir uygulamanın işlemesini etkinleştirmek için bilgi içeren bir standart uç nokta tanımlar.|  
|[\<mexEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/mexendpoint.md)|Bir sabit IMetadataExchange sözleşmesiyle standart uç nokta tanımlar. Tüm meta veri değişimi uç noktalarını IMetadataExchange sözleşmelerine belirtin. bu yana kendiniz bir tane tanımlayacaksınız yerine bu standart noktası kullanabilirsiniz.|  
|[\<udpAnnoucementEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/udpannoucementendpoint.md)|Üzerinden bir UDP bağlama Duyurunun ileti göndermek için hizmetler tarafından kullanılan standart bir uç nokta tanımlar. Bu, sabit bir sözleşme içeriyor ve iki bulma sürümlerini destekler. Buna ek olarak sabit bir UDP bağlama ve WS-bulma (WS-bulma Nisan 2005 veya WS-bulma sürüm 1.1) belirtimleri belirtilen varsayılan adresi değeri vardır. Duyurunun ileti alma ve gönderme için kullanmak üzere çok noktaya yayın adresini belirtebilirsiniz.|  
|[\<udpDiscoveryEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/udpdiscoveryendpoint.md)|UDP üzerinden bulma işlemleri için önceden yapılandırılmış olan bir standart uç noktayı tanımlar çok noktaya yayın bağlaması. Bu uç nokta, sabit bir sözleşme içeriyor ve iki WS bulma protokolünü sürümlerini destekler. Ayrıca, sabit bir UDP bağlama ve WS-bulma belirtimleri (WS-bulma Nisan 2005 veya WS-bulma V1.1) belirtildiği gibi varsayılan bir adresi vardır.|  
|[\<webHttpEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpendpoint.md)|Bir sabit ile standart bir uç nokta tanımlar [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) otomatik olarak bağlama ekler [ \<webHttp >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md) davranışı. Bir REST hizmeti yazarken Bu uç noktayı kullanın.|  
|[\<webScriptEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/webscriptendpoint.md)|Bir sabit ile standart bir uç nokta tanımlar [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) otomatik olarak bağlama ekler [ \<enableWebScript >](../../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) davranışı. Bir ASP.NET AJAX uygulamasından çağrılan hizmet yazarken Bu uç noktayı kullanın.|  
|[\<workflowControlEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/workflowcontrolendpoint.md)|İş akışı örnekleri yürütülmesini denetlemek için bir standart uç noktayı tanımlar (oluşturma, çalıştırma, askıya alma, sonlandırma, vb.).|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|\<system.ServiceModel>|Tüm WCF yapılandırma öğelerinin kök öğe.|  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Standart Uç Noktalar](../../../../../docs/framework/wcf/feature-details/standard-endpoints.md)
