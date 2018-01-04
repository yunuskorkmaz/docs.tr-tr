---
title: "&lt;davranışları&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0e5da4e6-1aa5-466c-924e-f10efee57f0b
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5a41d6134f793c2d8d02fda68a8b61b180485612
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltbehaviorsgt"></a>&lt;davranışları&gt;
Bu öğe adlı iki alt koleksiyonlar tanımlar `endpointBehaviors` ve `serviceBehaviors`.  Her koleksiyon sırasıyla uç noktaları ve hizmetler tarafından tüketilen davranışı öğeleri tanımlar. Her davranış öğesi kendi benzersiz tanımlanır `name` özniteliği. İle başlayarak [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bağlamalar ve davranışları olmayan bir adı olması için gereklidir. Varsayılan yapılandırma ve adsız bağlamalar ve davranışları hakkında daha fazla bilgi için bkz: [Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
 \<Sistem. ServiceModel >  
  
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
|[\<endpointBehaviors >](../../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md)|Bu yapılandırma bölümü belirli bir uç noktası için tanımlanmış tüm davranışları temsil eder.|  
|[\<serviceBehaviors >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md)|Bu yapılandırma bölümü için belirli bir hizmet tanımlanan tüm davranışları temsil eder.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<system.serviceModel >](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|Tüm Windows Communication Foundation (WCF) yapılandırma öğelerinin kök öğesi.|  
  
## <a name="remarks"></a>Açıklamalar  
 Kullanabileceğiniz `<remove>` belirli bir davranışı Koleksiyondan kaldırılacak öğe. Bunu yapmak için yalnızca kaldırmak için davranış adını sağlayın `name` özniteliği `<remove>` öğesi.  Aynı zamanda `<clear>` öğe koleksiyonunun tüm içeriği temizleyerek bir davranış koleksiyonu boş başladığından emin olun.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Configuration.BehaviorsSection>  
 <xref:System.ServiceModel.Configuration.EndpointBehaviorElementCollection>  
 <xref:System.ServiceModel.Configuration.EndpointBehaviorElement>  
 <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>  
 <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>  
 [Çalışma Zamanını Davranışlarla Yapılandırma ve Genişletme](../../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)  
 [İstemci Davranışlarını Yapılandırma](../../../../../docs/framework/wcf/configuring-client-behaviors.md)  
 [İstemci Çalışma Zamanı Davranışını Belirtme](../../../../../docs/framework/wcf/specifying-client-run-time-behavior.md)  
 [Hizmet Çalışma Zamanı Davranışını Belirtme](../../../../../docs/framework/wcf/specifying-service-run-time-behavior.md)  
 [Güvenlik Davranışları](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
