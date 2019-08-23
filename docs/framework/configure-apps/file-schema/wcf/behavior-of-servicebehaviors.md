---
title: <behavior> / <serviceBehaviors>
ms.date: 03/30/2017
ms.assetid: 78fc0a08-55de-416a-ac12-a5e6ffc9a987
ms.openlocfilehash: 8c847368934cc4cd8ccaab017ede00b7b8963897
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926412"
---
# <a name="behavior-of-servicebehaviors"></a>\<\<ServiceBehavior > davranış >
`behavior` Öğesi içeren bir koleksiyon için bir hizmet davranışını ayarlar. Her davranış tarafından dizine kendi `name`. Hizmetler, `behaviorConfiguration` [ \<uç nokta >](endpoint-element.md) öğesinin özniteliğini kullanarak bu ad aracılığıyla her davranışa bağlanabilir. Bu ayarları yeniden tanımlama olmadan davranışı yapılandırmaların paylaşmak uç noktaları sağlar. İle [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)]başlayarak, bağlamaların ve davranışların bir ada sahip olması gerekmez. Varsayılan yapılandırma ve ad Less bağlamaları ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../../../wcf/samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../../../wcf/simplified-configuration.md) ve Basitleştirilmiş yapılandırma.  
  
> [!NOTE]
> [ \< \<](../windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md) [ \<SendMessageChannelCache >](../windows-workflow-foundation/sendmessagechannelcache.md) öğesi gibi Windows Workflow etkinliklerine özgü davranış öğeleri ServiceBehavior > sayfasının davranış > belgelenmiştir.  
  
 \<system.ServiceModel>  
\<davranışlar >  
\<serviceBehaviors>  
\<davranış >  
  
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
|name|Davranışın yapılandırma adını içeren benzersiz bir dize. Bu değer, öğe için kimlik dizesi olarak davrandığından, benzersiz olması gereken kullanıcı tanımlı bir dizedir. İle [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)]başlayarak, bağlamaların ve davranışların bir ada sahip olması gerekmez. Varsayılan yapılandırma ve ad Less bağlamaları ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../../../wcf/samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../../../wcf/simplified-configuration.md) ve Basitleştirilmiş yapılandırma.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<dataContractSerializer >](datacontractserializer-element.md)|DataContractSerializer için yapılandırma verilerini içerir.|  
|[\<persistenceProvider >](persistenceprovider.md)|Kullanılacak kalıcılık sağlayıcısı uygulamasının türünü ve Kalıcılık işlemleri için kullanılacak zaman aşımını belirtir.|  
|[\<Yönlendirme >](routing-of-servicebehavior.md)|Yönlendirme yapılandırmasına dinamik değişiklik yapılmasına izin vermek için yönlendirme hizmetine çalışma zamanı erişimi sağlar.|  
|[\<serviceAuthenticationManager >](serviceauthenticationmanager.md)|, Hizmet düzeyinde bir iletim, ileti veya gönderen için geçerliliği belirleyen bir iş akışı yapılandırma öğesi sağlar.|  
|[\<serviceAuthorization >](serviceauthorization-element.md)|Hizmet işlemlerine erişim yetkisi veren ayarları belirtir.|  
|[\<serviceCredentials >](servicecredentials.md)|Hizmetin kimliğini doğrulamak için kullanılacak kimlik bilgisini ve istemci kimlik bilgileri doğrulaması ile ilgili ayarları belirtir.|  
|[\<serviceDebug >](servicedebug.md)|Bir Windows Communication Foundation (WCF) hizmeti için hata ayıklama ve yardım bilgileri özelliklerini belirtir.|  
|[\<serviceDiscovery >](servicediscovery.md)|Hizmet uç noktalarının bulunabilirliğini belirtir.|  
|[\<serviceMetadata >](servicemetadata.md)|Hizmet meta verilerinin ve ilgili bilgilerin yayınlanmasını belirtir.|  
|[\<Servicesecurityauıdıt >](servicesecurityaudit.md)|Hizmet işlemleri sırasında güvenlik olaylarının denetlenmesini etkinleştiren ayarları belirtir.|  
|[\<Serviceazaltma >](servicethrottling.md)|Bir WCF hizmetinin azaltma mekanizmasını belirtir.|  
|[\<Servicetimeaşımları >](servicetimeouts.md)|Bir hizmet için zaman aşımını belirtir.|  
|[\<workflowRuntime >](workflowruntime.md)|İş akışı tabanlı WCF hizmetlerini barındırmak için bir WorkflowRuntime örneğine yönelik ayarları belirtir.|  
|[\<useRequestHeadersForMetadataAddress >](userequestheadersformetadataaddress.md)|İstek iletisi başlıklarından meta veri adresi bilgilerinin alınmasına izin vermez.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Servicedavranışlar >](servicebehaviors.md)|Hizmet davranışı öğelerinin koleksiyonu.|
