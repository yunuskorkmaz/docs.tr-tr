---
title: <behavior> / <serviceBehaviors>
ms.date: 03/30/2017
ms.assetid: 78fc0a08-55de-416a-ac12-a5e6ffc9a987
ms.openlocfilehash: 115f94fc3f17dc5b4dd1ee3a090f2c9d121f810b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "74139727"
---
# <a name="behavior-of-servicebehaviors"></a>\<behavior> / \<serviceBehaviors>
`behavior` Öğesi içeren bir koleksiyon için bir hizmet davranışını ayarlar. Her davranış tarafından dizine kendi `name`. Hizmetler, bu ad aracılığıyla her davranışa `behaviorConfiguration` , öğesinin özniteliğini kullanarak bağlanabilir [\<endpoint>](endpoint-element.md) . Bu ayarları yeniden tanımlama olmadan davranışı yapılandırmaların paylaşmak uç noktaları sağlar. .NET Framework 4 ' den başlayarak bağlamalar ve davranışlar bir ada sahip olmak için gerekli değildir. Varsayılan yapılandırma ve ad Less bağlamaları ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../../../wcf/samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../../../wcf/simplified-configuration.md) ve Basitleştirilmiş yapılandırma.  
  
> [!NOTE]
> Öğesi gibi Windows Workflow etkinliklerine özgü davranış öğeleri [\<sendMessageChannelCache>](../windows-workflow-foundation/sendmessagechannelcache.md) sayfasında belgelenmiştir. [ \<behavior> \<serviceBehaviors> ](../windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<behavior>**  
  
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
|name|Davranışın yapılandırma adını içeren benzersiz bir dize. Bu değer, öğe için kimlik dizesi olarak davrandığından, benzersiz olması gereken kullanıcı tanımlı bir dizedir. .NET Framework 4 ' den başlayarak bağlamalar ve davranışlar bir ada sahip olmak için gerekli değildir. Varsayılan yapılandırma ve ad Less bağlamaları ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../../../wcf/samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../../../wcf/simplified-configuration.md) ve Basitleştirilmiş yapılandırma.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<dataContractSerializer>](datacontractserializer-element.md)|DataContractSerializer için yapılandırma verilerini içerir.|  
|[\<persistenceProvider>](persistenceprovider.md)|Kullanılacak kalıcılık sağlayıcısı uygulamasının türünü ve Kalıcılık işlemleri için kullanılacak zaman aşımını belirtir.|  
|[\<routing>](routing-of-servicebehavior.md)|Yönlendirme yapılandırmasına dinamik değişiklik yapılmasına izin vermek için yönlendirme hizmetine çalışma zamanı erişimi sağlar.|  
|[\<serviceAuthenticationManager>](serviceauthenticationmanager.md)|, Hizmet düzeyinde bir iletim, ileti veya gönderen için geçerliliği belirleyen bir iş akışı yapılandırma öğesi sağlar.|  
|[\<serviceAuthorization>](serviceauthorization-element.md)|Hizmet işlemlerine erişim yetkisi veren ayarları belirtir.|  
|[\<serviceCredentials>](servicecredentials.md)|Hizmetin kimliğini doğrulamak için kullanılacak kimlik bilgisini ve istemci kimlik bilgileri doğrulaması ile ilgili ayarları belirtir.|  
|[\<serviceDebug>](servicedebug.md)|Bir Windows Communication Foundation (WCF) hizmeti için hata ayıklama ve yardım bilgileri özelliklerini belirtir.|  
|[\<serviceDiscovery>](servicediscovery.md)|Hizmet uç noktalarının bulunabilirliğini belirtir.|  
|[\<serviceMetadata>](servicemetadata.md)|Hizmet meta verilerinin ve ilgili bilgilerin yayınlanmasını belirtir.|  
|[\<serviceSecurityAudit>](servicesecurityaudit.md)|Hizmet işlemleri sırasında güvenlik olaylarının denetlenmesini etkinleştiren ayarları belirtir.|  
|[\<serviceThrottling>](servicethrottling.md)|Bir WCF hizmetinin azaltma mekanizmasını belirtir.|  
|[\<serviceTimeouts>](servicetimeouts.md)|Bir hizmet için zaman aşımını belirtir.|  
|[\<workflowRuntime>](workflowruntime.md)|İş akışı tabanlı WCF hizmetlerini barındırmak için bir WorkflowRuntime örneğine yönelik ayarları belirtir.|  
|[\<useRequestHeadersForMetadataAddress>](userequestheadersformetadataaddress.md)|İstek iletisi başlıklarından meta veri adresi bilgilerinin alınmasına izin vermez.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<serviceBehaviors>](servicebehaviors.md)|Hizmet davranışı öğelerinin koleksiyonu.|
