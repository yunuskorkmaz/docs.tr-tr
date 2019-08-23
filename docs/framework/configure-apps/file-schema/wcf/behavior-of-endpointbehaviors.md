---
title: <behavior> / <endpointBehaviors>
ms.date: 03/30/2017
ms.assetid: b90ca3bc-3c22-4174-b903-e3a39898bd27
ms.openlocfilehash: f14e80798a9b088508f23d718c8b386286ad65a3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919836"
---
# <a name="behavior-of-endpointbehaviors"></a>\<\<EndpointBehavior davranış > >
Öğesi `behavior` , bir uç nokta davranışı için ayarların bir koleksiyonunu içerir. Her davranış tarafından dizine kendi `name`. Uç noktalar, bu ad aracılığıyla her davranışa bağlantı verebilir. İle [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)]başlayarak, bağlamaların ve davranışların bir ada sahip olması gerekmez. Varsayılan yapılandırma ve ad Less bağlamaları ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../../../wcf/samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../../../wcf/simplified-configuration.md) ve Basitleştirilmiş yapılandırma.  
  
 \<system.ServiceModel>  
\<davranışlar >  
\<Endpointdavranışlar >  
\<davranış >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<system.ServiceModel>
  <behaviors>
    <endpointBehaviors>
      <behavior name="String" />
    </endpointBehaviors>
  </behaviors>
</system.ServiceModel>
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|name|Davranışın yapılandırma adını içeren benzersiz bir dize. Bu değer, öğe için kimlik dizesi olarak davrandığından, benzersiz olması gereken kullanıcı tanımlı bir dizedir. İle [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)]başlayarak, bağlamaların ve davranışların bir ada sahip olması gerekmez. Varsayılan yapılandırma ve ad Less bağlamaları ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../../../wcf/samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../../../wcf/simplified-configuration.md) ve Basitleştirilmiş yapılandırma.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<clientCredentials >](clientcredentials.md)|Bir hizmette istemcinin kimliğini doğrulamak için kullanılan kimlik bilgilerini belirtir.|  
|[\<callbackDebug >](callbackdebug.md)|Windows Communication Foundation (WCF) geri çağırma nesnesi için hizmet hata ayıklamasını belirtir.|  
|[\<Callbackzamanaşımları >](callbacktimeouts.md)|İstemci geri çağırması için zaman aşımını belirtir.|  
|[\<> aracılığıyla Client](clientvia.md)|Bir iletinin gerçekleşmesi gereken yolu belirtir.|  
|[\<dataContractSerializer >](datacontractserializer.md)|DataContractSerializer için yapılandırma verilerini içerir.|  
|[\<dispatcherSynchronization >](dispatchersynchronization.md)|Bir hizmetin yanıtları zaman uyumsuz olarak göndermesini sağlayan bir uç nokta davranışı belirtir.|  
|[\<enableWebScript >](enablewebscript.md)|Hizmeti ASP.NET AJAX web sayfalarından tüketmek mümkün kılan uç nokta davranışını sağlar. Davranış yalnızca \<WebHttpBinding > Standart bağlaması \<veya webMessageEncoding > Binding öğesi ile birlikte kullanılmalıdır.|  
|[\<endpointDiscovery >](endpointdiscovery.md)|Bir uç nokta için, keşfedilebilirlik, kapsamları ve tüm özel uzantıları gibi çeşitli bulma ayarlarını belirtir.|  
|[\<soapProcessing >](soapprocessing.md)|Farklı bağlama türleri ve ileti sürümleri arasındaki iletileri sıralamak için kullanılan istemci uç noktası davranışını tanımlar.|  
|[\<synchronousReceive >](synchronousreceive-element.md)|Bir hizmet veya istemci uygulamasında ileti almak için çalışma zamanı davranışını belirtir. Hiçbir özniteliğe veya alt öğeye sahip değil.|  
|[\<Transactedtoplu işlem >](transactedbatching.md)|İşlem toplu işleminin alma işlemleri için desteklenip desteklenmediğini belirtir.|  
|[\<webHttp >](webhttp.md)|Yapılandırma yoluyla bir uç noktada WebHttpBehavior belirtir. Bu davranış, \<WebHttpBinding > Standart bağlamasıyla birlikte kullanıldığında bir WCF hizmeti için Web programlama modelini etkinleştirmenize izin vermez.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Endpointdavranışlar >](endpointbehaviors.md)|Uç nokta davranış öğelerinin koleksiyonu.|
