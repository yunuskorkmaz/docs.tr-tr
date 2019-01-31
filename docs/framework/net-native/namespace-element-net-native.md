---
title: <Namespace> Öğesi (.NET yerel)
ms.date: 03/30/2017
ms.assetid: 57c614e5-18a9-4e87-bfd5-d0fe3396a192
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 647b1807957b611b9ba75ee90a7ac2257246d14c
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55261587"
---
# <a name="namespace-element-net-native"></a>\<Namespace > öğesi (.NET yerel)
Çalışma zamanı yansıma ilkesini belirtilen bir ad alanındaki tüm türleri için geçerlidir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<Namespace Name="namespace_name"   
           Activate="policy_type"   
           Browse="policy_type"  
           Dynamic="policy_setting"  
           Serialize="policy_setting"  
           DataContractSerializer="policy_setting"  
           DataContractJsonSerializer="policy_setting"  
           XmlSerializer="policy_setting"  
           MarshalObject="policy_setting"  
           MarshalDelegate="policy_setting"  
           MarshalStructure="policy_setting" />  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Öznitelik türü|Açıklama|  
|---------------|--------------------|-----------------|  
|`Name`|Genel|Gerekli öznitelik. Ad alanı adını belirtir.|  
|`Activate`|Yansıma|İsteğe bağlı öznitelik. Oluşturucular örneklerinin etkinleştirmesi için çalışma zamanı erişimi denetler.|  
|`Browse`|Yansıma|İsteğe bağlı öznitelik. Program öğeleri hakkında bilgi için sorgulama kontrol eder, ancak herhangi bir çalışma zamanı erişim sağlamaz.|  
|`Dynamic`|Yansıma|İsteğe bağlı öznitelik. Dinamik programlama etkinleştirmek için Oluşturucular, yöntemler, alanlar, özellikler ve olaylar, tüm tür üyelerini, çalışma zamanı erişimi denetler.|  
|`Serialize`|Serileştirme|İsteğe bağlı öznitelik. Oluşturucular, alanları ve tür örnekleri sıralanabilir ve kitaplıkları gibi Newtonsoft JSON seri hale getirici tarafından serisi etkinleştirmek için özellikler, çalışma zamanı erişimi denetler.|  
|`DataContractSerializer`|Serileştirme|İsteğe bağlı öznitelik. Denetimleri İlkesi kullanan Serileştirmenin <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> sınıfı.|  
|`DataContractJsonSerializer`|Serileştirme|İsteğe bağlı öznitelik. İlke kullanan bir JSON serileştirme denetleyen <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> sınıfı.|  
|`XmlSerializer`|Serileştirme|İsteğe bağlı öznitelik. İlke kullanan bir XML serileştirme denetleyen <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> sınıfı.|  
|`MarshalObject`|Birlikte çalışma|İsteğe bağlı öznitelik. Windows çalışma zamanı ve COM başvuru türlerini hazırlama denetimleri İlkesi|  
|`MarshalDelegate`|Birlikte çalışma|İsteğe bağlı öznitelik. Yerel kod için işlev işaretçileri olarak temsilci türleri hazırlama için ilke denetler.|  
|`MarshalStructure`|Birlikte çalışma|İsteğe bağlı öznitelik. Yerel kod yapılarına hazırlama için ilke denetler.|  
  
## <a name="name-attribute"></a>Ad özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|*namespace_name*|Ad alanı adı. Varsa \<Namespace > öğesi alt öğesi olan bir [ \<uygulama >](../../../docs/framework/net-native/application-element-net-native.md), [ \<kitaplığı >](../../../docs/framework/net-native/library-element-net-native.md), veya [ \<derleme >](../../../docs/framework/net-native/assembly-element-net-native.md) öğesi *namespace_name* tam ad alanı adı olmalıdır. Varsa \<Namespace > öğesi başka bir alt öğesi olan \<Namespace > öğesi *namespace_name* göreli ad alanı adı olmalıdır.|  
  
## <a name="all-other-attributes"></a>Diğer tüm öznitelikler  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|*policy_setting*|Ad alanındaki tüm türleri için bu ilke türü için geçerli ayar. Olası değerler `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, ve `Required All`. Daha fazla bilgi için [çalışma zamanı yönerge İlkesi ayarları](../../../docs/framework/net-native/runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`<Namespace>`|Çalışma zamanı yansıma ilkesini üst ad alanındaki tüm türleri için geçerlidir.|  
|[\<türü >](../../../docs/framework/net-native/type-element-net-native.md)|Yansıma ilkesini bir türü için geçerlidir.|  
|[\<Typeınstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|Yansıma İlkesi oluşturulmuş bir genel türü için geçerlidir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Uygulama >](../../../docs/framework/net-native/application-element-net-native.md)|Birçok farklı uygulama türleri ve tür üyeleri olan meta verilerini yansıma çalışma zamanında kullanılabilir için kapsayıcı görevi görür. [ \<Uygulama >](../../../docs/framework/net-native/application-element-net-native.md) öğesi sıfır, bir veya daha fazla olabilir [ \<derleme >](../../../docs/framework/net-native/assembly-element-net-native.md) öğeleri.|  
|[\<Derleme >](../../../docs/framework/net-native/assembly-element-net-native.md)|Çalışma zamanı yansıma ilkesini belirtilen bir derlemedeki tüm türleri için geçerlidir.|  
|[\<Kitaplık >](../../../docs/framework/net-native/library-element-net-native.md)|Türler ve tür üyeleri olan meta verilerini yansıma çalışma zamanında kullanılabilir içeren derlemeyi tanımlar. [ \<Kitaplığı >](../../../docs/framework/net-native/library-element-net-native.md) öğesi sıfır veya bir olabilir [ \<derleme >](../../../docs/framework/net-native/assembly-element-net-native.md) öğesi.|  
|`<Namespace>`|Yansıma ilkesini üst ad alanındaki tüm türleri için geçerlidir.|  
  
## <a name="remarks"></a>Açıklamalar  
 `Activate`, `Browse`, `Dynamic`, Ve `Serialize` öznitelikleri tüm isteğe bağlı. Hiçbiri yoksa `<Namespace>` öğesi yalnızca alt öğeleri için bir kapsayıcı olarak hizmet verir. Varsa, `<Namespace>` öğesine belirtilen ad alanındaki tüm türleri için çalışma zamanı yansıma ilkesini uygular.  
  
 Bir alt öğesi olduğunda [ \<derleme >](../../../docs/framework/net-native/assembly-element-net-native.md) öğesi `<Namespace>` öğesi tarafından tanımlanan çalışma zamanı yansıma ilkesini geçersiz kılar [ \<derleme >](../../../docs/framework/net-native/assembly-element-net-native.md) öğesi.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Çalışma Zamanı Yönerge İlkesi Ayarları](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
- [Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [Çalışma Zamanı Yönerge Öğeleri](../../../docs/framework/net-native/runtime-directive-elements.md)
