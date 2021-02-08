---
description: 'Hakkında daha fazla bilgi edinin: <standardEndpoints>'
title: <standardEndpoints>
ms.date: 03/30/2017
ms.assetid: d62153d7-a6e6-462a-a784-cca61e9c2ba1
ms.openlocfilehash: f792f55b2c0c76727f4aaee50df072ee0c8bdbc5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786661"
---
# \<standardEndpoints>

Bu yapılandırma bölümü, yeniden kullanılabilir önceden yapılandırılmış uç noktalar olan standart uç noktaların bir koleksiyonunu tanımlamanızı sağlar. Standart bir uç noktada bir veya daha fazla adres, bağlama ve anlaşma özniteliği sabit bir değere ayarlanmış olur. Örneğin, bulma uç noktasında sözleşmenin düzeltilmesi. Ayrıca, özel bağlamaları tanımlamaya benzer yeni özelliklerle hizmet uç noktasını genişletmek için standart uç noktaları kullanabilirsiniz.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<standardEndpoints>**  
  
## <a name="syntax"></a>Syntax  
  
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
|[\<announcementEndpoint>](announcementendpoint.md)|Sabit bir duyuru sözleşmesiyle standart uç noktayı tanımlar. Bir hizmet, isteğe bağlı olarak açık veya kapalı olduğunda bir çevrimiçi ve çevrimdışı duyuru iletisi göndererek kullanılabilirliğini duyurur. Windows Communication Foundation (WCF) hizmeti, öğesindeki duyuru uç noktalarını belirtir [\<serviceDiscovery>](servicediscovery.md) ve duyuruları gerçekleştirmek Için AnnouncementClient kullanır. Diğer hizmetten gelen duyuruyu dinlemek isteyen bir istemci aslında bir WCF hizmeti olarak davranır; Bu nedenle, bölümünde söz konusu istemcinin duyuru uç noktalarını yapılandırmanız gerekir [\<services>](services.md) .|  
|[\<discoveryEndpoint>](discoveryendpoint.md)|Sabit bir bulma sözleşmesiyle standart uç noktayı tanımlar. Hizmet yapılandırmasına eklendiğinde, bulma iletilerinin nerede dinleneceğini belirtir. İstemci yapılandırmasına eklendiğinde, bulma sorgularının nereye gönderileceğini belirtir.|  
|[\<dynamicEndpoint>](dynamicendpoint.md)|Bu yapılandırma öğesi, bir uygulamanın, çalışma zamanında dinamik olarak uç nokta adresini bulabilmesini sağlayan bir istemci program olarak çalışmasını sağlamak için bilgi içeren bir standart uç nokta tanımlar.|  
|[\<mexEndpoint>](mexendpoint.md)|Sabit bir IMetadataExchange sözleşmesiyle bir standart uç nokta tanımlar. Tüm meta veri değişimi uç noktaları, sözleşmesi olarak IMetadataExchange belirtduğundan, kendiniz için bir tane tanımlamak yerine bu standart noktayı kullanabilirsiniz.|  
|[\<udpAnnouncementEndpoint>](udpannouncementendpoint.md)|Bir UDP bağlaması üzerinden duyuru iletileri göndermek için hizmetler tarafından kullanılan standart bir uç nokta tanımlar. Bu, sabit bir sözleşmeye sahiptir ve iki keşif sürümünü destekler. Ayrıca, bir sabit UDP bağlaması ve WS-Discovery belirtimleri (WS-Discovery Nisan 2005 veya WS-Discovery sürüm 1,1) belirtilen şekilde varsayılan bir adres değeri vardır. Duyuru iletilerini göndermek ve almak için kullanılacak çok noktaya yayın adresini belirtebilirsiniz.|  
|[\<udpDiscoveryEndpoint>](udpdiscoveryendpoint.md)|Bir UDP çok noktaya yayın bağlaması üzerinde bulma işlemleri için önceden yapılandırılmış bir standart uç nokta tanımlar. Bu uç nokta, sabit bir sözleşmeye sahiptir ve iki WS-Discovery protokol sürümünü destekler. Ayrıca, WS-Discovery belirtimleri (WS-Discovery Nisan 2005 veya WS-Discovery V 1.1) içinde belirtilen şekilde, sabit bir UDP bağlaması ve varsayılan bir adres vardır.|  
|[\<webHttpEndpoint>](webhttpendpoint.md)|[\<webHttpBinding>](webhttpbinding.md)Davranışı otomatik olarak ekleyen bir sabit bağlamaya sahip standart uç nokta tanımlar [\<webHttp>](webhttp.md) . Bir REST hizmeti yazarken bu uç noktayı kullanın.|  
|[\<webScriptEndpoint>](webscriptendpoint.md)|[\<webHttpBinding>](webhttpbinding.md)Davranışı otomatik olarak ekleyen bir sabit bağlamaya sahip standart uç nokta tanımlar [\<enableWebScript>](enablewebscript.md) . Bir ASP.NET AJAX uygulamasından çağrılan bir hizmet yazarken bu uç noktayı kullanın.|  
|[\<workflowControlEndpoint>](workflowcontrolendpoint.md)|İş akışı örneklerinin yürütülmesini denetlemek için standart bir uç nokta tanımlar (oluşturma, çalıştırma, askıya alma, sonlandırma, vb.).|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|\<system.ServiceModel>|Tüm WCF yapılandırma öğelerinin kök öğesi.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Standart Uç Noktaları](../../../wcf/feature-details/standard-endpoints.md)
