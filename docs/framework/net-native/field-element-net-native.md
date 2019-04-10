---
title: <Field> Öğesi (.NET yerel)
ms.date: 03/30/2017
ms.assetid: 6a14125f-1a8d-41a1-8a32-659ca0ad12de
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c58be27334bcb862367464475a4eade5e01bdbb2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59221619"
---
# <a name="field-element-net-native"></a>\<Alan > öğesi (.NET yerel)
Bir alan çalışma zamanı yansıma ilkesini uygular.  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<Field Name="field_name"  
       Browse="policy_type"  
       Dynamic="policy_type"  
       Serialize="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Öznitelik türü|Açıklama|  
|---------------|--------------------|-----------------|  
|`Name`|Genel|Gerekli öznitelik. Alanın adını belirtir.|  
|`Browse`|Yansıma|İsteğe bağlı öznitelik. Hakkında bilgi için sorgulama veya alan numaralandırma denetler, ancak çalışma zamanında herhangi bir dinamik erişim sağlamaz.|  
|`Dynamic`|Yansıma|İsteğe bağlı öznitelik. Programlama. alanın dinamik etkinleştirmek için çalışma zamanı erişimi denetler. Bu ilke, bir alan ayarlanabilir veya çalışma zamanında dinamik olarak alınan olduğunu sağlar.|  
|`Serialize`|Serileştirme|İsteğe bağlı öznitelik. Tür örnekleri kitaplıkları gibi Newtonsoft JSON seri hale getirici tarafından serileştirilecek veya veri bağlama için kullanılmak üzere etkinleştirmek için bir alan için çalışma zamanı erişimi denetler.|  
  
## <a name="name-attribute"></a>Ad özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|*method_name*|Alan adı. Üst öğe tarafından tanımlanan alan türünü [ \<türü >](../../../docs/framework/net-native/type-element-net-native.md) veya [ \<Typeınstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) öğesi.|  
  
## <a name="all-other-attributes"></a>Diğer tüm öznitelikler  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|*policy_setting*|Alan için bu ilke türü için geçerli ayar. Olası değerler `Auto`, `Excluded`, `Included`, ve `Required`. Daha fazla bilgi için [çalışma zamanı yönerge İlkesi ayarları](../../../docs/framework/net-native/runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<türü >](../../../docs/framework/net-native/type-element-net-native.md)|Yansıma İlkesi, bir tür ve tüm üyeleri için geçerlidir.|  
|[\<Typeınstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|Yansıma ilkesini, oluşturulmuş bir genel türü ve tüm üyeleri için geçerlidir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Alan İlkesi açıkça tanımlı değilse, kendi üst öğenin çalışma zamanı ilkesini devralır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma Zamanı Yönerge Öğeleri](../../../docs/framework/net-native/runtime-directive-elements.md)
- [Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [Çalışma Zamanı Yönerge İlkesi Ayarları](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
