---
title: <Namespace>Eleman (.NET Yerel)
ms.date: 03/30/2017
ms.assetid: 57c614e5-18a9-4e87-bfd5-d0fe3396a192
ms.openlocfilehash: 06d88a7b0f95c7c1dbe98818b847c92e08a57a19
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180964"
---
# <a name="namespace-element-net-native"></a>\<Ad Alanı> Öğesi (.NET Yerli)
Belirli bir ad alanındaki tüm türlere çalışma zamanı yansıtma ilkesi uygular.  
  
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
|`Activate`|Yansıma|İsteğe bağlı öznitelik. Örneklerin etkinleştirilmesini etkinleştirmek için çalışan zamanında kuruculara erişimi denetler.|  
|`Browse`|Yansıma|İsteğe bağlı öznitelik. Program öğeleri hakkında bilgi için sorgu denetimleri, ancak herhangi bir çalışma zamanı erişim etkinleştirmez.|  
|`Dynamic`|Yansıma|İsteğe bağlı öznitelik. Dinamik programlamayı etkinleştirmek için oluşturucular, yöntemler, alanlar, özellikler ve olaylar dahil olmak üzere tüm tür üyelerine çalışma zamanı erişimi denetler.|  
|`Serialize`|Serileştirme|İsteğe bağlı öznitelik. Newtonsoft JSON serileştiricisi gibi kitaplıklar tarafından seri hale getirilecek ve deserialized türü örnekleri etkinleştirmek için, yapıcılar, alanlar ve özelliklere çalışma zamanı erişimi denetler.|  
|`DataContractSerializer`|Serileştirme|İsteğe bağlı öznitelik. Sınıfı kullanan serileştirme ilkesini <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> denetler.|  
|`DataContractJsonSerializer`|Serileştirme|İsteğe bağlı öznitelik. Sınıfı kullanan JSON serileştirme <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> ilkesini denetler.|  
|`XmlSerializer`|Serileştirme|İsteğe bağlı öznitelik. Sınıfı kullanan XML serileştirme <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> ilkesini denetler.|  
|`MarshalObject`|Interop|İsteğe bağlı öznitelik. Başvuru türlerini Windows Runtime ve COM'a göre mareşalleme ilkesini denetler.|  
|`MarshalDelegate`|Interop|İsteğe bağlı öznitelik. Temsilci türlerini işlev işaretçisi olarak yerel koda göre işaretetmek için ilkeyi denetler.|  
|`MarshalStructure`|Interop|İsteğe bağlı öznitelik. Yapıları yerel koda göre mareşalleme ilkesini denetler.|  
  
## <a name="name-attribute"></a>Ad özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|*namespace_name*|Ad alanı adı. \<Ad alanı> öğesi bir [ \<Uygulama>, ](application-element-net-native.md) [ \<Kitaplık>](library-element-net-native.md)veya [ \<Derleme>](assembly-element-net-native.md) öğesinin bir alt öğesi ise, *namespace_name* tam nitelikli bir ad alanı adı olmalıdır. \<Namespace> öğesi başka \<bir Ad alanı> öğesinin çocuğuysa, *namespace_name* göreli bir ad alanı adı olmalıdır.|  
  
## <a name="all-other-attributes"></a>Diğer tüm öznitelikler  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|*policy_setting*|Ad alanındaki tüm türler için bu ilke türüne uygulanacak ayar. Olası değerler `All` `Auto`, `Excluded` `Public`, `PublicAndInternal` `Required Public`, `Required PublicAndInternal`, `Required All`, , , ve . Daha fazla bilgi için [Runtime Yönergesi İlke Ayarları'na](runtime-directive-policy-settings.md)bakın.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`<Namespace>`|Bir üst ad alanındaki tüm türlere çalışma zamanı yansıtma ilkesi uygular.|  
|[\<Tip>](type-element-net-native.md)|Yansıma ilkesini bir türe uygular.|  
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|Yapılı genel bir türe yansıma ilkesi uygular.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Başvuru>](application-element-net-native.md)|Uygulama genelindeki türler ve meta verileri çalışma zamanında yansımaiçin kullanılabilir tür üyeleri için bir kapsayıcı görevi görehizmet eder. Uygulama>öğesi sıfır, bir veya [ \<](assembly-element-net-native.md) daha fazla Derleme>öğesi olabilir. [ \<](application-element-net-native.md)|  
|[\<Montaj>](assembly-element-net-native.md)|Belirli bir derlemedeki tüm türlere çalışma zamanı yansıtma ilkesi uygular.|  
|[\<Kütüphane>](library-element-net-native.md)|Meta verileri çalışma zamanında yansıtılamaya hazır olan türleri ve tür üyelerini içeren derlemeyi tanımlar. Kitaplık>öğesi sıfır [ \<](assembly-element-net-native.md) veya bir Derleme>öğesi olabilir. [ \<](library-element-net-native.md)|  
|`<Namespace>`|Bir üst ad alanındaki tüm türlere yansıma ilkesi uygular.|  
  
## <a name="remarks"></a>Açıklamalar  
 , `Activate` `Browse`, `Dynamic`ve `Serialize` özniteliklerin tümü isteğe bağlıdır. Hiçbiri yoksa, `<Namespace>` öğe yalnızca alt öğeler için bir kapsayıcı olarak hizmet vermektedir. Bunlar varsa, `<Namespace>` öğe belirtilen ad alanındaki tüm türlere çalışma zamanı yansıtma ilkesi uygular.  
  
 Derleme>öğesinin bir alt öğesi `<Namespace>` olduğunda, öğe, [ \<Derleme>](assembly-element-net-native.md) öğesi tarafından tanımlanan çalışma zamanı yansıtma ilkesini geçersiz kılar. [ \<](assembly-element-net-native.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma Zamanı Yönerge İlkesi Ayarları](runtime-directive-policy-settings.md)
- [Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu](runtime-directives-rd-xml-configuration-file-reference.md)
- [Çalışma Zamanı Yönerge Öğeleri](runtime-directive-elements.md)
