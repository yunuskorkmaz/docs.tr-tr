---
title: "&lt;serviceBehaviors&gt; &lt;davranışı&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 78fc0a08-55de-416a-ac12-a5e6ffc9a987
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 78c912886b5a39fad361994a0aaa302491e71f2d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltbehaviorgt-of-ltservicebehaviorsgt"></a>&lt;serviceBehaviors&gt; &lt;davranışı&gt;
`behavior` Öğesi içeren bir koleksiyon için bir hizmet davranışını ayarlar. Her davranış tarafından dizine kendi `name`. Hizmetleri kullanarak bu ad aracılığıyla her davranış bağlanması `behaviorConfiguration` özniteliği [ \<uç noktası >](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) öğesi. Bu ayarları yeniden tanımlama olmadan davranışı yapılandırmaların paylaşmak uç noktaları sağlar. İle başlayarak [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bağlamalar ve davranışları olmayan bir adı olması için gereklidir. Varsayılan yapılandırma ve adsız bağlamalar ve davranışları hakkında daha fazla bilgi için bkz: [Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
> [!NOTE]
>  Windows iş akışı etkinlikleri için özgü davranış öğeleri gibi [ \<sendMessageChannelCache >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/sendmessagechannelcache.md) öğesi, belgelenmiştir [ \<davranışı >, \< serviceBehaviors >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md) sayfası.  
  
 \<Sistem. ServiceModel >  
\<davranışları >  
\<serviceBehaviors >  
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
|name|Davranış yapılandırma adını içeren benzersiz bir dize. Öğesinin kimlik dizesi olarak davranan bu yana, benzersiz olmalıdır ve kullanıcı tanımlı bir dize değeridir. İle başlayarak [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bağlamalar ve davranışları olmayan bir adı olması için gereklidir. Varsayılan yapılandırma ve adsız bağlamalar ve davranışları hakkında daha fazla bilgi için bkz: [Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)|Yapılandırma verileri için DataContractSerializer içerir.|  
|[\<persistenceProvider >](../../../../../docs/framework/configure-apps/file-schema/wcf/persistenceprovider.md)|Kalıcılık işlemleri için zaman aşımı yanı sıra kullanmak için Kalıcılık sağlayıcı uygulaması türünü belirtir.|  
|[\<Yönlendirme >](../../../../../docs/framework/configure-apps/file-schema/wcf/routing-of-servicebehavior.md)|Dinamik yönlendirme yapılandırması değiştirilmesine izin veren yönlendirme hizmeti çalışma zamanı erişim sağlar.|  
|[\<serviceAuthenticationManager >](../../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthenticationmanager.md)|Hizmet düzeyinde iletim, ileti veya başlatanın geçerliliğini oluşturur. iş akışı yapılandırma öğesi sağlar...|  
|[\<serviceAuthorization >](../../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md)|Hizmet işlemlerine erişimi yetkilendirme ayarlarını belirtir.|  
|[\<serviceCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|Hizmet ve istemci kimlik doğrulama ile ilgili ayarları kimlik doğrulaması kullanmak için kimlik bilgilerini belirtir.|  
|[\<serviceDebug >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md)|Hata ayıklama ve Yardım bilgileri özellikleri belirten bir [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] hizmet.|  
|[\<serviceDiscovery >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md)|Hizmet uç noktaları bulunabilirliğini belirtir.|  
|[\<serviceMetadata >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md)|Hizmet meta verilerini ve ilişkili bilgileri yayımlanmasını belirtir.|  
|[\<serviceSecurityAudit >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md)|Hizmet işlemleri sırasında güvenlik olaylarının denetlenmesini etkinleştirme ayarlarını belirtir.|  
|[\<serviceThrottling >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicethrottling.md)|Azaltma mekanizmasını belirten bir [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] hizmet.|  
|[\<serviceTimeouts >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicetimeouts.md)|Bir hizmet için zaman aşımını belirtir.|  
|[\<İş akışı workflowRuntime >](../../../../../docs/framework/configure-apps/file-schema/wcf/workflowruntime.md)|İş akışı tabanlı barındırmak için WorkflowRuntime örneği ayarlarını belirtir. [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] Hizmetleri.|  
|[\<useRequestHeadersForMetadataAddress >](../../../../../docs/framework/configure-apps/file-schema/wcf/userequestheadersformetadataaddress.md)|Meta veri adresi istek iletisi üst bilgilerinden alınmasını sağlar.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<serviceBehaviors >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md)|Hizmet davranışı öğelerinin koleksiyonu.|
