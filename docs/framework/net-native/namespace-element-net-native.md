---
title: <Namespace>Öğesi (.NET Native)
ms.date: 03/30/2017
ms.assetid: 57c614e5-18a9-4e87-bfd5-d0fe3396a192
ms.openlocfilehash: 06d88a7b0f95c7c1dbe98818b847c92e08a57a19
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79180964"
---
# <a name="namespace-element-net-native"></a>\<Namespace>Öğesi (.NET Native)
Çalışma zamanı yansıma ilkesini belirtilen bir ad alanındaki tüm türlere uygular.  
  
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
|`Name`|Genel|Gerekli öznitelik. Ad alanının adını belirtir.|  
|`Activate`|Yansıma|İsteğe bağlı öznitelik. Örneklerin etkinleştirilmesini sağlamak için oluşturuculara çalışma zamanı erişimini denetler.|  
|`Browse`|Yansıma|İsteğe bağlı öznitelik. Program öğeleri hakkında bilgi sorgulamayı denetler, ancak hiçbir çalışma zamanı erişimini etkinleştirmez.|  
|`Dynamic`|Yansıma|İsteğe bağlı öznitelik. Dinamik programlamayı etkinleştirmek için oluşturucular, Yöntemler, alanlar, Özellikler ve olaylar dahil olmak üzere tüm tür üyelerine çalışma zamanı erişimini denetler.|  
|`Serialize`|Serileştirme|İsteğe bağlı öznitelik. Tür örneklerinin, Newtonsoft JSON serileştirici gibi kitaplıklar tarafından serileştirilmesi ve seri durumdan çıkarılmakta olması için oluşturuculara, alanlara ve özelliklere çalışma zamanı erişimini denetler.|  
|`DataContractSerializer`|Serileştirme|İsteğe bağlı öznitelik. Sınıfını kullanan serileştirme için ilkeyi denetler <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> .|  
|`DataContractJsonSerializer`|Serileştirme|İsteğe bağlı öznitelik. Sınıfını kullanan JSON serileştirme için ilkeyi denetler <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> .|  
|`XmlSerializer`|Serileştirme|İsteğe bağlı öznitelik. Sınıfını kullanan XML serileştirme ilkesini denetler <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> .|  
|`MarshalObject`|Interop|İsteğe bağlı öznitelik. Windows Çalışma Zamanı ve COM 'a başvuru türlerini hazırlama ilkesini denetler.|  
|`MarshalDelegate`|Interop|İsteğe bağlı öznitelik. Temsilci türlerini yerel koda işlev işaretçileri olarak hazırlama ilkesini denetler.|  
|`MarshalStructure`|Interop|İsteğe bağlı öznitelik. Yapıları yerel koda hazırlama ilkesini denetler.|  
  
## <a name="name-attribute"></a>Ad özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|*namespace_name*|Ad alanı adı. \<Namespace>Öğesi,, veya öğesinin bir alt öğesi ise, [\<Application>](application-element-net-native.md) [\<Library>](library-element-net-native.md) [\<Assembly>](assembly-element-net-native.md) *namespace_name* tam bir ad alanı adı olmalıdır. \<Namespace>Öğe başka bir öğenin alt öğesi ise \<Namespace> , *namespace_name* göreli bir ad alanı adı olmalıdır.|  
  
## <a name="all-other-attributes"></a>Diğer tüm öznitelikler  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|*policy_setting*|Ad alanındaki tüm türler için bu ilke türüne uygulanacak ayar. Olası değerler şunlardır,,,,,, `All` `Auto` `Excluded` `Public` `PublicAndInternal` `Required Public` `Required PublicAndInternal` ve `Required All` . Daha fazla bilgi için bkz. [çalışma zamanı yönergesi Ilke ayarları](runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`<Namespace>`|Bir üst ad alanındaki tüm türlere çalışma zamanı yansıma ilkesini uygular.|  
|[\<Type>](type-element-net-native.md)|Yansıma ilkesini bir türe uygular.|  
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|Yansıma ilkesini oluşturulmuş genel bir türe uygular.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Application>](application-element-net-native.md)|Uygulama genelinde türler için bir kapsayıcı görevi görür ve meta verileri çalışma zamanında yansıma için kullanılabilir olan üyeleri yazın. [\<Application>](application-element-net-native.md)Öğesinde sıfır, bir veya daha fazla [\<Assembly>](assembly-element-net-native.md) öğe olabilir.|  
|[\<Assembly>](assembly-element-net-native.md)|Belirtilen derlemedeki tüm türlere çalışma zamanı yansıma ilkesini uygular.|  
|[\<Library>](library-element-net-native.md)|Meta verileri çalışma zamanında yansıma için kullanılabilir olan türleri ve tür üyelerini içeren derlemeyi tanımlar. [\<Library>](library-element-net-native.md)Öğe sıfır veya bir [\<Assembly>](assembly-element-net-native.md) öğe içerebilir.|  
|`<Namespace>`|Bir üst ad alanındaki tüm türlere yansıma ilkesi uygular.|  
  
## <a name="remarks"></a>Açıklamalar  
 `Activate`,, `Browse` `Dynamic` Ve `Serialize` özniteliklerinin tümü isteğe bağlıdır. Hiçbiri yoksa, `<Namespace>` öğe yalnızca alt öğeler için bir kapsayıcı olarak hizmet verir. Varsa, `<Namespace>` öğesi, çalışma zamanı yansıtma ilkesini belirtilen ad alanındaki tüm türlere uygular.  
  
 Öğesinin bir alt öğesi olduğunda, öğesi öğesi [\<Assembly>](assembly-element-net-native.md) `<Namespace>` tarafından tanımlanan çalışma zamanı yansıma ilkesini geçersiz kılar [\<Assembly>](assembly-element-net-native.md) .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma Zamanı Yönerge İlkesi Ayarları](runtime-directive-policy-settings.md)
- [Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu](runtime-directives-rd-xml-configuration-file-reference.md)
- [Çalışma Zamanı Yönerge Öğeleri](runtime-directive-elements.md)
