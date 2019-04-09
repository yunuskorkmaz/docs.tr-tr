---
title: <behaviors> İş akışı
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 3c6017b6-0c4f-4192-bd67-9515f5d1ec82
ms.openlocfilehash: b7c5cf93a82ac88c25f9c478ad52cf41eb6f6d65
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59129213"
---
# <a name="behaviors-of-workflow"></a>\<davranışlar > İş akışı
Bu öğeyi içeren **serviceBehaviors** koleksiyonu.  Koleksiyondaki her öğe iş akışı hizmetler tarafından kullanılan davranışı öğeleri tanımlar. Her davranışı öğesi kendi benzersiz tarafından tanımlanır **adı** özniteliği.  
  
 \<system.ServiceModel>  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
  </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
 Yok.  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<serviceBehaviors>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/servicebehaviors-of-workflow.md)|Bu yapılandırma bölümü, belirli bir iş akışı hizmeti için tanımlanan tüm davranışları temsil eder.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<system.serviceModel>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|Tüm iş akışı yapılandırma öğelerinin kök öğe.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.BehaviorsSection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>
- [Çalışma Zamanını Davranışlarla Yapılandırma ve Genişletme](../../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
