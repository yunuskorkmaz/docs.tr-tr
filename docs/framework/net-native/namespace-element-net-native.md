---
title: <Namespace>Öğesi (.NET Native)
ms.date: 03/30/2017
ms.assetid: 57c614e5-18a9-4e87-bfd5-d0fe3396a192
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7be004776d2a2fd3b4c41fb21b3ac244946f2166
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71049425"
---
# <a name="namespace-element-net-native"></a>\<Namespace > öğesi (.NET Native)
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
|`DataContractSerializer`|Serileştirme|İsteğe bağlı öznitelik. <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> Sınıfını kullanan serileştirme için ilkeyi denetler.|  
|`DataContractJsonSerializer`|Serileştirme|İsteğe bağlı öznitelik. <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> Sınıfını kullanan JSON serileştirme için ilkeyi denetler.|  
|`XmlSerializer`|Serileştirme|İsteğe bağlı öznitelik. <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> Sınıfını kullanan XML serileştirme ilkesini denetler.|  
|`MarshalObject`|Interop|İsteğe bağlı öznitelik. Windows Çalışma Zamanı ve COM 'a başvuru türlerini hazırlama ilkesini denetler.|  
|`MarshalDelegate`|Interop|İsteğe bağlı öznitelik. Temsilci türlerini yerel koda işlev işaretçileri olarak hazırlama ilkesini denetler.|  
|`MarshalStructure`|Interop|İsteğe bağlı öznitelik. Yapıları yerel koda hazırlama ilkesini denetler.|  
  
## <a name="name-attribute"></a>Ad özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|*namespace_name*|Ad alanı adı. [ \<](application-element-net-native.md) [ \<](library-element-net-native.md) [ \<](assembly-element-net-native.md) Ad alanı > öğesi bir uygulama >, kitaplık > ya da bütünleştirilmiş kod > öğesinin bir alt öğesi ise, namespace_name tam nitelenmiş olmalıdır \< ad alanı adı. Ad alanı > öğesi başka \<bir ad alanının alt öğesi > öğesi ise, *namespace_name* bir göreli ad alanı adı olmalıdır. \<|  
  
## <a name="all-other-attributes"></a>Diğer tüm öznitelikler  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|*policy_setting*|Ad alanındaki tüm türler için bu ilke türüne uygulanacak ayar. Olası değerler şunlardır `All` `Auto` ,,`Excluded`,,,, ve`Required All`. `Public` `PublicAndInternal` `Required Public` `Required PublicAndInternal` Daha fazla bilgi için bkz. [çalışma zamanı yönergesi Ilke ayarları](runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`<Namespace>`|Bir üst ad alanındaki tüm türlere çalışma zamanı yansıma ilkesini uygular.|  
|[\<Tür >](type-element-net-native.md)|Yansıma ilkesini bir türe uygular.|  
|[\<Typeörneklemesi >](typeinstantiation-element-net-native.md)|Yansıma ilkesini oluşturulmuş genel bir türe uygular.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Uygulama >](application-element-net-native.md)|Uygulama genelinde türler için bir kapsayıcı görevi görür ve meta verileri çalışma zamanında yansıma için kullanılabilir olan üyeleri yazın. Uygulama > öğesinde sıfır, bir veya daha fazla [ \<derleme >](assembly-element-net-native.md) öğesi olabilir. [ \<](application-element-net-native.md)|  
|[\<Bütünleştirilmiş kod >](assembly-element-net-native.md)|Belirtilen derlemedeki tüm türlere çalışma zamanı yansıma ilkesini uygular.|  
|[\<Kitaplık >](library-element-net-native.md)|Meta verileri çalışma zamanında yansıma için kullanılabilir olan türleri ve tür üyelerini içeren derlemeyi tanımlar. Kitaplık > öğesi sıfır veya bir [ \<bütünleştirilmiş kod >](assembly-element-net-native.md) öğesine sahip olabilir. [ \<](library-element-net-native.md)|  
|`<Namespace>`|Bir üst ad alanındaki tüm türlere yansıma ilkesi uygular.|  
  
## <a name="remarks"></a>Açıklamalar  
 ,, Ve özniteliklerinin`Serialize` tümü isteğe bağlıdır. `Browse` `Activate` `Dynamic` Hiçbiri yoksa, `<Namespace>` öğe yalnızca alt öğeler için bir kapsayıcı olarak hizmet verir. Varsa, `<Namespace>` öğesi, çalışma zamanı yansıtma ilkesini belirtilen ad alanındaki tüm türlere uygular.  
  
 Derleme > öğesinin bir alt `<Namespace>`öğesiolduğunda öğe, [ \<derleme >](assembly-element-net-native.md) öğesi tarafından tanımlanan çalışma zamanı yansıma ilkesini geçersiz kılar. [ \<](assembly-element-net-native.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma Zamanı Yönerge İlkesi Ayarları](runtime-directive-policy-settings.md)
- [Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu](runtime-directives-rd-xml-configuration-file-reference.md)
- [Çalışma Zamanı Yönerge Öğeleri](runtime-directive-elements.md)
