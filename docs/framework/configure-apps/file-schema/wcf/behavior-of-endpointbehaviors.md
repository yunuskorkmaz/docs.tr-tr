---
title: '&lt;endpointBehaviors&gt; &lt;davranışı&gt;'
ms.date: 03/30/2017
ms.assetid: b90ca3bc-3c22-4174-b903-e3a39898bd27
ms.openlocfilehash: e275fbc1b14469553094a4df838930be53937de2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33363305"
---
# <a name="ltbehaviorgt-of-ltendpointbehaviorsgt"></a>&lt;endpointBehaviors&gt; &lt;davranışı&gt;
`behavior` Öğesi içeren bir uç nokta davranışını için ayarlar koleksiyonu. Her davranış tarafından dizine kendi `name`. Uç noktaları bu adı aracılığıyla her davranışını bağlayabilirsiniz. İle başlayarak [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bağlamalar ve davranışları olmayan bir adı olması için gereklidir. Varsayılan yapılandırma ve adsız bağlamalar ve davranışları hakkında daha fazla bilgi için bkz: [Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
 \<system.ServiceModel>  
\<davranışları >  
\<endpointBehaviors >  
\<davranışı >  
  
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
|name|Davranış yapılandırma adını içeren benzersiz bir dize. Öğesinin kimlik dizesi olarak davranan bu yana, benzersiz olmalıdır ve kullanıcı tanımlı bir dize değeridir. İle başlayarak [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bağlamalar ve davranışları olmayan bir adı olması için gereklidir. Varsayılan yapılandırma ve adsız bağlamalar ve davranışları hakkında daha fazla bilgi için bkz: [Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<clientCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|Bir hizmet için istemci kimlik doğrulaması için kullanılan kimlik bilgilerini belirtir.|  
|[\<callbackDebug >](../../../../../docs/framework/configure-apps/file-schema/wcf/callbackdebug.md)|Hizmet için bir Windows Communication Foundation (WCF) geri çağırma nesnesi hata ayıklama belirtir.|  
|[\<callbackTimeouts >](../../../../../docs/framework/configure-apps/file-schema/wcf/callbacktimeouts.md)|İstemci geri araması için zaman aşımını belirtir.|  
|[\<clientVia >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientvia.md)|Bir ileti rota sürmesi gerektiğini belirtir.|  
|[\<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer.md)|Yapılandırma verileri için DataContractSerializer içerir.|  
|[\<dispatcherSynchronization >](../../../../../docs/framework/configure-apps/file-schema/wcf/dispatchersynchronization.md)|Yanıtı zaman uyumsuz olarak göndermek bir hizmet sağlayan bir uç nokta davranışını belirtir.|  
|[\<enableWebScript >](../../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md)|ASP.NET AJAX web sayfalarından hizmeti kullanmak mümkün kılar uç nokta davranışını etkinleştirir. Davranış yalnızca ya da ile birlikte kullanılmalıdır \<webHttpBinding > standart bağlama veya \<webMessageEncoding > bağlama öğesi.|  
|[\<endpointDiscovery >](../../../../../docs/framework/configure-apps/file-schema/wcf/endpointdiscovery.md)|Kendi bulunabilirlik, kapsamları ve kendi meta verileri için özel uzantılar gibi bir uç nokta için çeşitli bulma ayarlarını belirtir.|  
|[\<soapProcessing >](../../../../../docs/framework/configure-apps/file-schema/wcf/soapprocessing.md)|Farklı bağlama türleri ve ileti sürümleri arasında iletileri sıralama için kullanılan istemci uç nokta davranışını tanımlar.|  
|[\<synchronousReceive >](../../../../../docs/framework/configure-apps/file-schema/wcf/synchronousreceive-element.md)|Bir hizmet veya istemci uygulamasında iletileri almak için çalışma zamanı davranışını belirtir. Herhangi bir öznitelik veya alt öğe yok.|  
|[\<transactedBatching >](../../../../../docs/framework/configure-apps/file-schema/wcf/transactedbatching.md)|İşlem toplu işlerin desteklenip desteklenmediğini belirtir alma işlemleri.|  
|[\<webHttp >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md)|Yapılandırma yoluyla bir uç noktada WebHttpBehavior belirtir. İle birlikte kullanıldığında bu davranış, \<webHttpBinding > standart bağlama bir WCF hizmeti için Web programlama modeli sağlar.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<endpointBehaviors >](../../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md)|Uç noktası davranışı öğeleri koleksiyonu.|
