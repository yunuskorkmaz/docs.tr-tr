---
title: <Event>Eleman (.NET Yerel)
ms.date: 03/30/2017
ms.assetid: e53b029c-9d6d-4c0a-9cdc-5cfca8a5ca47
ms.openlocfilehash: 60da48d5872d7ce61afcffa7977411bc6e1efc7f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181034"
---
# <a name="event-element-net-native"></a>\<Olay> Elemanı (.NET Yerli)
Bir olay için çalışma zamanı yansıtma ilkesi uygular.  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<Event Name="event_name"
       Browse="policy_type"
       Dynamic="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Öznitelik türü|Açıklama|  
|---------------|--------------------|-----------------|  
|`Name`|Genel|Gerekli öznitelik. Olay adını belirtir.|  
|`Browse`|Yansıma|İsteğe bağlı öznitelik. Olay hakkında bilgi için sorgulamayı veya olayı sayısallandırmayı denetler, ancak çalışma zamanında dinamik erişim emmez.|  
|`Dynamic`|Yansıma|İsteğe bağlı öznitelik. Dinamik programlamayı etkinleştirmek için etkinliğe çalışma zamanı erişimini denetler. Bu ilke, bir olayın çalışma zamanında dinamik olarak ele alınabilmesini sağlar.|  
  
## <a name="name-attribute"></a>Ad özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|*method_name*|Olay adı. Olayın türü ana [ \<Type>](type-element-net-native.md) veya [ \<TypeInstantiation>](typeinstantiation-element-net-native.md) öğesi tarafından tanımlanır.|  
  
## <a name="all-other-attributes"></a>Diğer tüm öznitelikler  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|*policy_setting*|Olay için bu ilke türüne uygulanacak ayar. Olası değerler `Auto` `Excluded`, `Included`, `Required`, ve . Daha fazla bilgi için [Runtime Yönergesi İlke Ayarları'na](runtime-directive-policy-settings.md)bakın.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Tip>](type-element-net-native.md)|Yansıma ilkesini bir türe ve tüm üyelerine uygular.|  
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|Yapılı genel bir türe ve tüm üyelerine yansıma ilkesi uygular.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir olayın ilkesi açıkça tanımlanmamışsa, üst öğesinin çalışma zamanı ilkesini devralır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu](runtime-directives-rd-xml-configuration-file-reference.md)
- [Çalışma Zamanı Yönerge Öğeleri](runtime-directive-elements.md)
- [Çalışma Zamanı Yönerge İlkesi Ayarları](runtime-directive-policy-settings.md)
