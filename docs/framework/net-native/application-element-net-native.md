---
title: <Application>Öğesi (.NET Native)
ms.date: 03/30/2017
ms.assetid: b4e9b37a-059b-4076-8f56-cb3f9cef0cd9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2183a64f4e30a5188940abd5108a7ca1bddfe120
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71049925"
---
# <a name="application-element-net-native"></a>\<Uygulama > öğesi (.NET Native)
Uygulama genelinde türler için bir kapsayıcı görevi görür ve meta verileri çalışma zamanında yansıma için kullanılabilir olan ve çalışma zamanı yansıtma ilkesini bir uygulamadaki tüm program öğelerine uygular.  
  
 \<Yönergeler > öğesi  
\<Uygulama > öğesi (RD. xml)  
  
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
|`DataContractSerializer`|Serileştirme|İsteğe bağlı öznitelik. <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> Sınıfını kullanan serileştirme için ilkeyi denetler.|  
|`DataContractJsonSerializer`|Serileştirme|İsteğe bağlı öznitelik. <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> Sınıfını kullanan JSON serileştirme için ilkeyi denetler.|  
|`XmlSerializer`|Serileştirme|İsteğe bağlı öznitelik. <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> Sınıfını kullanan XML serileştirme ilkesini denetler.|  
|`MarshalObject`|Interop|İsteğe bağlı öznitelik. Windows Çalışma Zamanı ve COM 'a başvuru türlerini hazırlama ilkesini denetler.|  
|`MarshalDelegate`|Interop|İsteğe bağlı öznitelik. Temsilci türlerini yerel koda işlev işaretçileri olarak hazırlama ilkesini denetler.|  
|`MarshalStructure`|Interop|İsteğe bağlı öznitelik. Yapıları yerel koda hazırlama ilkesini denetler.|  
  
## <a name="all-attributes"></a>Tüm öznitelikler  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|*policy_setting*|Bu ilke ayarı, uygulamadaki türlere uygulanır. Olası değerler şunlardır `All` `Auto` ,,`Excluded`,,,, ve`Required All`. `Public` `PublicAndInternal` `Required Public` `Required PublicAndInternal` Daha fazla bilgi için bkz. [çalışma zamanı yönergesi Ilke ayarları](runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Bütünleştirilmiş kod >](assembly-element-net-native.md)|İlkeyi belirli bir derlemedeki tüm türlere uygular.|  
|[\<Ad alanı >](namespace-element-net-native.md)|İlkeyi belirli bir ad alanındaki tüm türlere uygular.|  
|[\<Tür >](type-element-net-native.md)|İlkeyi sınıf veya yapı gibi belirli bir türe uygular.|  
|[\<Typeörneklemesi >](typeinstantiation-element-net-native.md)|İlkeyi oluşturulan genel bir türe uygular. Örneğin, [ \<](typeinstantiation-element-net-native.md) bir`List<String>` tür için ilke tanımlamak üzere bir typeörneklemesi > öğesi kullanılabilir.|  
|[\<Yöntem >](method-element-net-native.md)|İlkeyi belirli bir türdeki bir yönteme uygular.|  
|[\<Methodörneklemesi >](methodinstantiation-element-net-native.md)|İlkeyi oluşturulmuş bir genel metoda uygular.|  
|[\<Özellik >](property-element-net-native.md)|İlkeyi belirli bir türdeki bir özelliğe uygular.|  
|[\<Alan >](field-element-net-native.md)|İlkeyi belirli bir türdeki alana uygular.|  
|[\<Olay >](event-element-net-native.md)|İlkeyi belirli bir türdeki bir olaya uygular.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Yönergeler >](directives-element-net-native.md)|Çalışma zamanı yönergeleri dosyasının kök öğesi.|  
  
## <a name="remarks"></a>Açıklamalar  
 Yönergeler > öğesi sıfır veya bir `<Application>` öğe içerebilir. [ \<](directives-element-net-native.md) Tek `<Application>` bir yansıma yönergeleri dosyasında birden çok öğe desteklenmez.  
  
 `<Application>` Öğesi iki şekilde kullanılabilir:  
  
- Bir kapsayıcı olarak, meta verileri çalışma zamanında gerekli olan program öğelerini tanımlar. Bu durumda, `<Application>` öğesinin herhangi bir özniteliğe sahip olması gerekir. Derleme zamanında, derleyici araçları, `<Application>` öğenin alt öğeleri tarafından tanımlanan program öğeleri için .NET Framework Çekirdek kitaplıklar da dahil olmak üzere tüm kitaplıklarda arama yapın. Buna karşılık, derleyici araçları yalnızca kitaplık [ \<>](library-element-net-native.md)alt öğeleri tarafından tanımlanan program öğeleri için [ \<kitaplık >](library-element-net-native.md) öğesi tarafından belirlenen kitaplığı arar.  
  
- Yansıma, serileştirme ve birlikte çalışma için uygulama genelinde ilke ayarlayan bir öğe olarak. `<Application>` Öğesinin öznitelikleri, `<Application>` veya [ Library>öğesitarafındantanımlananaltöğelertarafındangeçersizkılınabilenuygulamagenelindeilkeyitanımlar.\<](library-element-net-native.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [\<Kitaplık > öğesi](library-element-net-native.md)
- [\<Yönergeler > öğesi](directives-element-net-native.md)
- [Çalışma Zamanı Yönerge Öğeleri](runtime-directive-elements.md)
- [Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu](runtime-directives-rd-xml-configuration-file-reference.md)
