---
title: <behaviors>
ms.date: 03/30/2017
ms.assetid: 0e5da4e6-1aa5-466c-924e-f10efee57f0b
ms.openlocfilehash: 8fcb5ac0c552d1ac2e849c95a5c0757d0c142f3d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926389"
---
# <a name="behaviors"></a>\<davranışlar >
Bu öğe, ve `endpointBehaviors` `serviceBehaviors`adlı iki alt koleksiyonu tanımlar.  Her koleksiyon, sırasıyla bitiş noktaları ve hizmetler tarafından tüketilen davranış öğelerini tanımlar. Her davranış öğesi, benzersiz `name` özniteliği tarafından tanımlanır. İle [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)]başlayarak, bağlamaların ve davranışların bir ada sahip olması gerekmez. Varsayılan yapılandırma ve ad Less bağlamaları ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../../../wcf/samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../../../wcf/simplified-configuration.md) ve Basitleştirilmiş yapılandırma.  
  
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
 Yok.  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Endpointdavranışlar >](endpointbehaviors.md)|Bu yapılandırma bölümü, belirli bir uç nokta için tanımlanan tüm davranışları temsil eder.|  
|[\<Servicedavranışlar >](servicebehaviors.md)|Bu yapılandırma bölümü için belirli bir hizmet tanımlanan tüm davranışları temsil eder.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<system.serviceModel>](system-servicemodel.md)|Tüm Windows Communication Foundation (WCF) yapılandırma öğelerinin kök öğesi.|  
  
## <a name="remarks"></a>Açıklamalar  
 Koleksiyondan belirli bir davranışı `<remove>` kaldırmak için öğesini kullanabilirsiniz. Bunu yapmak için, `name` `<remove>` öğesinin özniteliğinde kaldırılacak davranışın adını sağlamanız yeterlidir.  Ayrıca, `<clear>` bir davranış koleksiyonunun, koleksiyonun tüm içeriğini temizleyerek boş bir şekilde başlamasını sağlamak için öğesini de kullanabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.BehaviorsSection>
- <xref:System.ServiceModel.Configuration.EndpointBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.EndpointBehaviorElement>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>
- [Çalışma Zamanını Davranışlarla Yapılandırma ve Genişletme](../../../wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
- [İstemci Davranışlarını Yapılandırma](../../../wcf/configuring-client-behaviors.md)
- [İstemci Çalışma Zamanı Davranışını Belirtme](../../../wcf/specifying-client-run-time-behavior.md)
- [Hizmet Çalışma Zamanı Davranışını Belirtme](../../../wcf/specifying-service-run-time-behavior.md)
- [Güvenlik Davranışları](../../../wcf/feature-details/security-behaviors-in-wcf.md)
