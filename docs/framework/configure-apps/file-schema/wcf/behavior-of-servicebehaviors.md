---
title: <behavior> , <serviceBehaviors>
ms.date: 03/30/2017
ms.assetid: 78fc0a08-55de-416a-ac12-a5e6ffc9a987
ms.openlocfilehash: 89ad23a801abce9b2fe409b7e7acb1f5e9c2ac55
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55271139"
---
# <a name="behavior-of-servicebehaviors"></a>\<davranış >, \<serviceBehaviors >
`behavior` Öğesi içeren bir koleksiyon için bir hizmet davranışını ayarlar. Her davranış tarafından dizine kendi `name`. Hizmetleri bağlantısını kullanarak bu adı aracılığıyla her davranışı `behaviorConfiguration` özniteliği [ \<uç noktası >](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) öğesi. Bu ayarları yeniden tanımlama olmadan davranışı yapılandırmaların paylaşmak uç noktaları sağlar. İle başlayarak [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bağlamalar ve davranışları için gerekli değildir bir ada sahip. Varsayılan yapılandırma ve adsız bağlamaları ve davranışları hakkında daha fazla bilgi için bkz: [Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
> [!NOTE]
>  Windows iş akışı aktivitelere özgü davranış öğelerini gibi [ \<sendMessageChannelCache >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/sendmessagechannelcache.md) öğesi, belgelenen [ \<davranışı >, \< serviceBehaviors >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md) sayfası.  
  
 \<system.ServiceModel>  
\<davranışlar >  
\<serviceBehaviors>  
\<davranışı >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<system.ServiceModel>
  <behaviors>
    <serviceBehaviors>
       <behavior name="String" />
    </serviceBehaviors>
  </behaviors>
</system.ServiceModel>
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|name|Davranış yapılandırma adını içeren benzersiz bir dize. Bu öğe için kimlik dizesi görür bu yana, benzersiz olmalıdır ve kullanıcı tanımlı bir dize değeridir. İle başlayarak [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bağlamalar ve davranışları için gerekli değildir bir ada sahip. Varsayılan yapılandırma ve adsız bağlamaları ve davranışları hakkında daha fazla bilgi için bkz: [Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)|Yapılandırma verileri için DataContractSerializer içerir.|  
|[\<persistenceProvider >](../../../../../docs/framework/configure-apps/file-schema/wcf/persistenceprovider.md)|Kullanılacak Kalıcılık sağlayıcı uygulanması yanı sıra Kalıcılık işlemleri için kullanılacak zaman aşımını türünü belirtir.|  
|[\<Yönlendirme >](../../../../../docs/framework/configure-apps/file-schema/wcf/routing-of-servicebehavior.md)|Dinamik yönlendirme yapılandırması değişikliğini izin vermek için yönlendirme hizmeti çalışma zamanı erişim sağlar.|  
|[\<serviceAuthenticationManager >](../../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthenticationmanager.md)|Hizmet düzeyinde bir iletim, ileti veya gönderen geçerliliğini kurar ve bir iş akışı yapılandırma öğesi sağlar...|  
|[\<serviceAuthorization >](../../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md)|Hizmet işlemleri erişim yetkisi ayarlarını belirtir.|  
|[\<serviceCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|Hizmet ve istemci kimlik doğrulama ile ilgili ayarlarda kullanılan kimlik bilgisini belirtir.|  
|[\<serviceDebug >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md)|Bir Windows Communication Foundation (WCF) hizmeti için hata ayıklama ve Yardım bilgileri özelliklerini belirtir.|  
|[\<serviceDiscovery >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md)|Hizmet bitiş noktası bulunabilirliğini belirtir.|  
|[\<serviceMetadata >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md)|Hizmet meta verileri ve ilgili bilgilerin yayınlanmasını belirtir.|  
|[\<serviceSecurityAudit >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md)|Hizmet işlemleri sırasında güvenlik olaylarının denetlenmesini etkinleştirme ayarlarını belirtir.|  
|[\<serviceThrottling >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicethrottling.md)|Bir WCF Hizmeti azaltma mekanizmasını belirtir.|  
|[\<serviceTimeouts >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicetimeouts.md)|Bir hizmet için zaman aşımını belirtir.|  
|[\<İş akışı workflowRuntime >](../../../../../docs/framework/configure-apps/file-schema/wcf/workflowruntime.md)|İş akışı tabanlı WCF hizmetlerini barındırmak için bir WorkflowRuntime örneğini ayarlarını belirtir.|  
|[\<useRequestHeadersForMetadataAddress >](../../../../../docs/framework/configure-apps/file-schema/wcf/userequestheadersformetadataaddress.md)|İstek iletisi başlıklarından meta verisi adresi bilgilerine alınmasını sağlar.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<serviceBehaviors >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md)|Hizmet davranışı öğelerinin koleksiyonu.|
