---
title: <behaviors>
ms.date: 03/30/2017
ms.assetid: 0e5da4e6-1aa5-466c-924e-f10efee57f0b
ms.openlocfilehash: b9d30d7e1c9d211cd57982a0f03fe855a6b53c12
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55257931"
---
# <a name="behaviors"></a>\<davranışlar >
Bu öğe adlı iki alt öğe koleksiyonlarını tanımlar `endpointBehaviors` ve `serviceBehaviors`.  Her koleksiyon sırasıyla uç noktaları ve hizmetler tarafından kullanılan davranışı öğeleri tanımlar. Her davranışı öğesi kendi benzersiz tarafından tanımlanır `name` özniteliği. İle başlayarak [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bağlamalar ve davranışları için gerekli değildir bir ada sahip. Varsayılan yapılandırma ve adsız bağlamaları ve davranışları hakkında daha fazla bilgi için bkz: [Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
 \<system.ServiceModel>  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<behaviors>
  <serviceBehaviors>
  </serviceBehaviors>
  <endpointBehaviors>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
 Hiçbiri  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<endpointBehaviors>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md)|Bu yapılandırma bölümü, belirli bir uç nokta için tanımlanan tüm davranışları temsil eder.|  
|[\<serviceBehaviors >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md)|Bu yapılandırma bölümü için belirli bir hizmet tanımlanan tüm davranışları temsil eder.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<system.serviceModel>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|Tüm Windows Communication Foundation (WCF) yapılandırma öğelerinin kök öğe.|  
  
## <a name="remarks"></a>Açıklamalar  
 Kullanabileceğiniz `<remove>` koleksiyondan belirli bir davranış öğesi. Bunu yapmak için basitçe kaldırmak için davranış adı sağlamanız `name` özniteliği `<remove>` öğesi.  Ayrıca `<clear>` koleksiyonun tüm içeriği teslim temizleyerek bir davranış koleksiyonu boş başladığını sağlamak üzere öğesi.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.ServiceModel.Configuration.BehaviorsSection>
- <xref:System.ServiceModel.Configuration.EndpointBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.EndpointBehaviorElement>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>
- [Çalışma Zamanını Davranışlarla Yapılandırma ve Genişletme](../../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
- [İstemci Davranışlarını Yapılandırma](../../../../../docs/framework/wcf/configuring-client-behaviors.md)
- [İstemci Çalışma Zamanı Davranışını Belirtme](../../../../../docs/framework/wcf/specifying-client-run-time-behavior.md)
- [Hizmet Çalışma Zamanı Davranışını Belirtme](../../../../../docs/framework/wcf/specifying-service-run-time-behavior.md)
- [Güvenlik Davranışları](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
