---
title: <Application>Öğesi (.NET Native)
ms.date: 03/30/2017
ms.assetid: b4e9b37a-059b-4076-8f56-cb3f9cef0cd9
ms.openlocfilehash: e26826b3d8674b536ab0897182da58bc02cfd00b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73128527"
---
# <a name="application-element-net-native"></a>\<Application>Öğesi (.NET Native)
Uygulama genelinde türler için bir kapsayıcı görevi görür ve meta verileri çalışma zamanında yansıma için kullanılabilir olan ve çalışma zamanı yansıtma ilkesini bir uygulamadaki tüm program öğelerine uygular.  
  
 \<Directives> Öğesi  
\<Application>Öğesi (RD. xml)  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<Application Activate="policy_setting"  
             Browse="policy_setting"  
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
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır. Alt öğeler tablosunda, ilke, çalışma zamanında belirli program öğeleri için kullanılabilir hale getirilen meta veri türünü ifade eder.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Öznitelik türü|Açıklama|  
|---------------|--------------------|-----------------|  
|`Activate`|Yansıma|İsteğe bağlı öznitelik. Örneklerin etkinleştirilmesini sağlamak için oluşturuculara çalışma zamanı erişimini denetler.|  
|`Browse`|Yansıma|İsteğe bağlı öznitelik. Türler hakkında bilgi sorgulamayı denetler, ancak çalışma zamanında herhangi bir dinamik erişimi etkinleştirmez.|  
|`Dynamic`|Yansıma|İsteğe bağlı öznitelik. Dinamik programlamayı etkinleştirmek için oluşturucular, Yöntemler, alanlar, Özellikler ve olaylar dahil olmak üzere tüm tür üyelerine çalışma zamanı erişimini denetler.|  
|`Serialize`|Serileştirme|İsteğe bağlı öznitelik. Tür örneklerinin, Newtonsoft JSON serileştirici gibi kitaplıklar tarafından serileştirilmesi ve seri durumdan çıkarılmakta olması için oluşturuculara, alanlara ve özelliklere çalışma zamanı erişimini denetler.|  
|`DataContractSerializer`|Serileştirme|İsteğe bağlı öznitelik. Sınıfını kullanan serileştirme için ilkeyi denetler <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> .|  
|`DataContractJsonSerializer`|Serileştirme|İsteğe bağlı öznitelik. Sınıfını kullanan JSON serileştirme için ilkeyi denetler <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> .|  
|`XmlSerializer`|Serileştirme|İsteğe bağlı öznitelik. Sınıfını kullanan XML serileştirme ilkesini denetler <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> .|  
|`MarshalObject`|Interop|İsteğe bağlı öznitelik. Windows Çalışma Zamanı ve COM 'a başvuru türlerini hazırlama ilkesini denetler.|  
|`MarshalDelegate`|Interop|İsteğe bağlı öznitelik. Temsilci türlerini yerel koda işlev işaretçileri olarak hazırlama ilkesini denetler.|  
|`MarshalStructure`|Interop|İsteğe bağlı öznitelik. Yapıları yerel koda hazırlama ilkesini denetler.|  
  
## <a name="all-attributes"></a>Tüm öznitelikler  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|*policy_setting*|Bu ilke ayarı, uygulamadaki türlere uygulanır. Olası değerler şunlardır,,,,,, `All` `Auto` `Excluded` `Public` `PublicAndInternal` `Required Public` `Required PublicAndInternal` ve `Required All` . Daha fazla bilgi için bkz. [çalışma zamanı yönergesi Ilke ayarları](runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Assembly>](assembly-element-net-native.md)|İlkeyi belirli bir derlemedeki tüm türlere uygular.|  
|[\<Namespace>](namespace-element-net-native.md)|İlkeyi belirli bir ad alanındaki tüm türlere uygular.|  
|[\<Type>](type-element-net-native.md)|İlkeyi sınıf veya yapı gibi belirli bir türe uygular.|  
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|İlkeyi oluşturulan genel bir türe uygular. Örneğin, bir [\<TypeInstantiation>](typeinstantiation-element-net-native.md) öğe bir tür için ilke tanımlamak üzere kullanılabilir `List<String>` .|  
|[\<Method>](method-element-net-native.md)|İlkeyi belirli bir türdeki bir yönteme uygular.|  
|[\<MethodInstantiation>](methodinstantiation-element-net-native.md)|İlkeyi oluşturulmuş bir genel metoda uygular.|  
|[\<Property>](property-element-net-native.md)|İlkeyi belirli bir türdeki bir özelliğe uygular.|  
|[\<Field>](field-element-net-native.md)|İlkeyi belirli bir türdeki alana uygular.|  
|[\<Event>](event-element-net-native.md)|İlkeyi belirli bir türdeki bir olaya uygular.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Directives>](directives-element-net-native.md)|Çalışma zamanı yönergeleri dosyasının kök öğesi.|  
  
## <a name="remarks"></a>Açıklamalar  
 [\<Directives>](directives-element-net-native.md)Öğe sıfır veya bir `<Application>` öğe içerebilir. `<Application>`Tek bir yansıma yönergeleri dosyasında birden çok öğe desteklenmez.  
  
 `<Application>`Öğesi iki şekilde kullanılabilir:  
  
- Bir kapsayıcı olarak, meta verileri çalışma zamanında gerekli olan program öğelerini tanımlar. Bu durumda, `<Application>` öğesinin herhangi bir özniteliğe sahip olması gerekir. Derleme zamanında, derleyici araçları, öğenin alt öğeleri tarafından tanımlanan program öğeleri için .NET Framework Çekirdek kitaplıklar da dahil olmak üzere tüm kitaplıklarda arama yapın `<Application>` . Buna karşılık, derleyici araçları yalnızca öğesinin [\<Library>](library-element-net-native.md) alt öğeleri tarafından tanımlanan program öğeleri için öğesi tarafından belirlenen kitaplığı arar [\<Library>](library-element-net-native.md) .  
  
- Yansıma, serileştirme ve birlikte çalışma için uygulama genelinde ilke ayarlayan bir öğe olarak. Öğesinin öznitelikleri, `<Application>` veya öğesi tarafından tanımlanan alt öğeler tarafından geçersiz kılınabilen uygulama genelinde ilkeyi tanımlar `<Application>` [\<Library>](library-element-net-native.md) .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [\<Library>Dosyalarında](library-element-net-native.md)
- [\<Directives>Dosyalarında](directives-element-net-native.md)
- [Çalışma Zamanı Yönerge Öğeleri](runtime-directive-elements.md)
- [Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu](runtime-directives-rd-xml-configuration-file-reference.md)
