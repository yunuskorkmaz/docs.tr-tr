---
title: <Namespace> öğesi (.NET Native)
ms.date: 03/30/2017
ms.assetid: 57c614e5-18a9-4e87-bfd5-d0fe3396a192
ms.openlocfilehash: b6d7a45de14d0fb8eb2e27a02c86510f630be9e1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128258"
---
# <a name="namespace-element-net-native"></a>\<ad alanı > öğesi (.NET Native)
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
|`DataContractSerializer`|Serileştirme|İsteğe bağlı öznitelik. <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> sınıfını kullanan serileştirme için ilkeyi denetler.|  
|`DataContractJsonSerializer`|Serileştirme|İsteğe bağlı öznitelik. <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> sınıfını kullanan JSON serileştirme için ilkeyi denetler.|  
|`XmlSerializer`|Serileştirme|İsteğe bağlı öznitelik. <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> sınıfını kullanan XML serileştirme ilkesini denetler.|  
|`MarshalObject`|Interop|İsteğe bağlı öznitelik. Windows Çalışma Zamanı ve COM 'a başvuru türlerini hazırlama ilkesini denetler.|  
|`MarshalDelegate`|Interop|İsteğe bağlı öznitelik. Temsilci türlerini yerel koda işlev işaretçileri olarak hazırlama ilkesini denetler.|  
|`MarshalStructure`|Interop|İsteğe bağlı öznitelik. Yapıları yerel koda hazırlama ilkesini denetler.|  
  
## <a name="name-attribute"></a>Ad özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|*namespace_name*|Ad alanı adı. \<ad alanı > öğesi bir [\<uygulamanın](application-element-net-native.md)alt öğesidir >, [\<kitaplığı >](library-element-net-native.md)veya [\<assembly >](assembly-element-net-native.md) öğesi ise, *namespace_name* tam bir ad alanı adı olmalıdır. \<ad alanı > öğesi, başka bir \<ad alanı > öğesinin alt öğesi ise, *namespace_name* bir göreli ad alanı adı olmalıdır.|  
  
## <a name="all-other-attributes"></a>Diğer tüm öznitelikler  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|*policy_setting*|Ad alanındaki tüm türler için bu ilke türüne uygulanacak ayar. Olası değerler şunlardır `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`ve `Required All`. Daha fazla bilgi için bkz. [çalışma zamanı yönergesi Ilke ayarları](runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`<Namespace>`|Bir üst ad alanındaki tüm türlere çalışma zamanı yansıma ilkesini uygular.|  
|[\<türü >](type-element-net-native.md)|Yansıma ilkesini bir türe uygular.|  
|[\<Typeörneklemesi >](typeinstantiation-element-net-native.md)|Yansıma ilkesini oluşturulmuş genel bir türe uygular.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<uygulama >](application-element-net-native.md)|Uygulama genelinde türler için bir kapsayıcı görevi görür ve meta verileri çalışma zamanında yansıma için kullanılabilir olan üyeleri yazın. [\<uygulama >](application-element-net-native.md) öğesi sıfır, bir veya daha fazla [\<derleme >](assembly-element-net-native.md) öğesi içerebilir.|  
|[Derleme > \<](assembly-element-net-native.md)|Belirtilen derlemedeki tüm türlere çalışma zamanı yansıma ilkesini uygular.|  
|[\<kitaplığı >](library-element-net-native.md)|Meta verileri çalışma zamanında yansıma için kullanılabilir olan türleri ve tür üyelerini içeren derlemeyi tanımlar. [\<Library >](library-element-net-native.md) öğesi sıfır veya bir [\<derleme >](assembly-element-net-native.md) öğesi içerebilir.|  
|`<Namespace>`|Bir üst ad alanındaki tüm türlere yansıma ilkesi uygular.|  
  
## <a name="remarks"></a>Açıklamalar  
 `Activate`, `Browse`, `Dynamic`ve `Serialize` özniteliklerinin tümü isteğe bağlıdır. Hiçbiri yoksa `<Namespace>` öğesi yalnızca alt öğeler için bir kapsayıcı olarak hizmet verir. Varsa `<Namespace>` öğesi, çalışma zamanı yansıma ilkesini belirtilen ad alanındaki tüm türlere uygular.  
  
 [\<Assembly >](assembly-element-net-native.md) öğesinin bir alt öğesi olduğunda, `<Namespace>` öğesi [\<assembly >](assembly-element-net-native.md) öğesi tarafından tanımlanan çalışma zamanı yansıma ilkesini geçersiz kılar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma Zamanı Yönerge İlkesi Ayarları](runtime-directive-policy-settings.md)
- [Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu](runtime-directives-rd-xml-configuration-file-reference.md)
- [Çalışma Zamanı Yönerge Öğeleri](runtime-directive-elements.md)
