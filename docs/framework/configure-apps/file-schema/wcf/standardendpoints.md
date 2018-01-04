---
title: '&lt;standardEndpoints&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d62153d7-a6e6-462a-a784-cca61e9c2ba1
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9b172accdfe644d158e201a7ceb9689d0188a979
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltstandardendpointsgt"></a>&lt;standardEndpoints&gt;
Bu yapılandırma bölümü yeniden kullanılabilir önceden yapılandırılmış uç nokta standart uç noktaları koleksiyonu tanımlamanızı sağlar. Standart bir uç noktası bir erişebilir veya adresi, bağlama ve sözleşme öznitelikleri daha fazla sabit bir değere ayarlayın. Örneğin, bulma uç sözleşme sabittir. Standart uç noktaları, özel bağlamaları tanımlamak için benzer yeni özelliklerle Hizmeti uç noktası genişletmek için de kullanabilirsiniz.  
  
 \<Sistem. ServiceModel >  
  
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
|[\<announcementEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/announcementendpoint.md)|Standart bir uç nokta sabit duyuru sözleşme ile tanımlar. Bir hizmet açıldığında veya sırasıyla kapalı bir çevrimiçi ve çevrimdışı duyuru iletisi göndererek, kullanılabilirlik isteğe bağlı olarak Duyurusu. A [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] hizmeti belirtir duyuru uç noktalardan [ \<serviceDiscovery >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) öğesi ve duyuruları gerçekleştirmek için AnnouncementClient kullanır. Başka bir hizmet duyurudan gerçekten olarak davranan için dinleme isteyen bir istemci bir [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] hizmet; böylece, bu istemci için duyuru uç noktaları yapılandırmak zorunda [ \<Hizmetleri >](../../../../../docs/framework/configure-apps/file-schema/wcf/services.md) bölümü.|  
|[\<discoveryEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryendpoint.md)|Standart bir uç nokta sabit bulma sözleşme ile tanımlar. Hizmet yapılandırmasında eklendiğinde, bulma iletilerini dinlemek konumu belirtir. İstemci yapılandırmasında eklendiğinde bulma sorguları göndermek konumu belirtir.|  
|[\<dynamicEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/dynamicendpoint.md)|Bu yapılandırma öğesi uygulama uç noktası adresi çalışma zamanında dinamik olarak bulabilirsiniz bir istemci program olarak çalışmasını etkinleştirmek için bilgileri içeren standart bir uç nokta tanımlar.|  
|[\<mexEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/mexendpoint.md)|Standart bir uç nokta sabit bir IMetadataExchange sözleşme ile tanımlar. Tüm meta veri exchange uç noktalar kendi sözleşme IMetadataExchange belirtin olduğundan, kendiniz için bir tane tanımlama yerine bu standart noktasını kullanabilir.|  
|[\<udpAnnoucementEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/udpannoucementendpoint.md)|UDP bağlama üzerinden duyuru iletileri göndermek için hizmetler tarafından kullanılan standart bir uç nokta tanımlar. Sabit bir sözleşme sahiptir ve iki bulma sürümlerini destekler. Ayrıca, sabit bir UDP bağlama ve WS-bulma belirtimleri (WS-bulma Nisan 2005 veya WS-bulma sürüm 1.1) belirtildiği gibi varsayılan adres değer içeriyor. Duyurunun ileti alma ve gönderme için kullanmak üzere çok noktaya yayın adresi belirtebilirsiniz.|  
|[\<udpDiscoveryEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/udpdiscoveryendpoint.md)|UDP üzerinden bulma işlemleri için önceden yapılandırılmış olan standart bir uç nokta tanımlayan çok noktaya yayın bağlama. Bu uç noktaya sabit bir sözleşme var ve iki WS bulma protokolünü sürümlerini destekler. Ayrıca, sabit bir UDP bağlama ve WS-bulma belirtimleri (WS-bulma Nisan 2005 veya WS-bulma V1.1) belirtildiği gibi varsayılan bir adresi vardır.|  
|[\<webHttpEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpendpoint.md)|Bir sabit ile standart bir uç nokta tanımlayan [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) otomatik olarak bağlama ekler [ \<webHttp >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md) davranışı. Bu uç noktaya bir REST hizmeti yazarken kullanın.|  
|[\<webScriptEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/webscriptendpoint.md)|Bir sabit ile standart bir uç nokta tanımlayan [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) otomatik olarak bağlama ekler [ \<enableWebScript >](../../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) davranışı. Bir ASP.NET AJAX uygulamasından adlı bir hizmet yazarken Bu uç nokta kullanın.|  
|[\<workflowControlEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/workflowcontrolendpoint.md)|İş akışı örnekleri yürütülmesini denetlemeye yönelik standart bir uç nokta tanımlar (oluşturmak, çalıştırmak, askıya almak, sonlandırma, vb.).|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|\<Sistem. ServiceModel >|Tüm WCF yapılandırma öğelerinin kök öğesi.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Standart Uç Noktalar](../../../../../docs/framework/wcf/feature-details/standard-endpoints.md)
