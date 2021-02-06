---
description: 'Hakkında daha fazla bilgi edinin: <behaviors>'
title: <behaviors>
ms.date: 03/30/2017
ms.assetid: 0e5da4e6-1aa5-466c-924e-f10efee57f0b
ms.openlocfilehash: 3cb8edea76f6e7af3c3b387e5b04b89e58a28305
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639516"
---
# \<behaviors>

Bu öğe, ve adlı iki alt koleksiyonu tanımlar `endpointBehaviors` `serviceBehaviors` .  Her koleksiyon, sırasıyla bitiş noktaları ve hizmetler tarafından tüketilen davranış öğelerini tanımlar. Her davranış öğesi, benzersiz özniteliği tarafından tanımlanır `name` . .NET Framework 4 ' den başlayarak bağlamalar ve davranışlar bir ada sahip olmak için gerekli değildir. Varsayılan yapılandırma ve ad Less bağlamaları ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../../../wcf/samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../../../wcf/simplified-configuration.md) ve Basitleştirilmiş yapılandırma.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<behaviors>**  
  
## <a name="syntax"></a>Syntax  
  
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

 Yok  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<endpointBehaviors>](endpointbehaviors.md)|Bu yapılandırma bölümü, belirli bir uç nokta için tanımlanan tüm davranışları temsil eder.|  
|[\<serviceBehaviors>](servicebehaviors.md)|Bu yapılandırma bölümü için belirli bir hizmet tanımlanan tüm davranışları temsil eder.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<system.serviceModel>](system-servicemodel.md)|Tüm Windows Communication Foundation (WCF) yapılandırma öğelerinin kök öğesi.|  
  
## <a name="remarks"></a>Açıklamalar  

 `<remove>`Koleksiyondan belirli bir davranışı kaldırmak için öğesini kullanabilirsiniz. Bunu yapmak için, öğesinin özniteliğinde kaldırılacak davranışın adını sağlamanız yeterlidir `name` `<remove>` .  Ayrıca, `<clear>` bir davranış koleksiyonunun, koleksiyonun tüm içeriğini temizleyerek boş bir şekilde başlamasını sağlamak için öğesini de kullanabilirsiniz.  
  
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
