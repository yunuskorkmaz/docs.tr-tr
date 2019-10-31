---
title: <Application> öğesi (.NET Native)
ms.date: 03/30/2017
ms.assetid: b4e9b37a-059b-4076-8f56-cb3f9cef0cd9
ms.openlocfilehash: e26826b3d8674b536ab0897182da58bc02cfd00b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128527"
---
# <a name="application-element-net-native"></a>\<uygulama > öğesi (.NET Native)
Uygulama genelinde türler için bir kapsayıcı görevi görür ve meta verileri çalışma zamanında yansıma için kullanılabilir olan ve çalışma zamanı yansıtma ilkesini bir uygulamadaki tüm program öğelerine uygular.  
  
 \<yönergeleri > öğesi  
\<uygulama > öğesi (RD. xml)  
  
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
|`DataContractSerializer`|Serileştirme|İsteğe bağlı öznitelik. <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> sınıfını kullanan serileştirme için ilkeyi denetler.|  
|`DataContractJsonSerializer`|Serileştirme|İsteğe bağlı öznitelik. <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> sınıfını kullanan JSON serileştirme için ilkeyi denetler.|  
|`XmlSerializer`|Serileştirme|İsteğe bağlı öznitelik. <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> sınıfını kullanan XML serileştirme ilkesini denetler.|  
|`MarshalObject`|Interop|İsteğe bağlı öznitelik. Windows Çalışma Zamanı ve COM 'a başvuru türlerini hazırlama ilkesini denetler.|  
|`MarshalDelegate`|Interop|İsteğe bağlı öznitelik. Temsilci türlerini yerel koda işlev işaretçileri olarak hazırlama ilkesini denetler.|  
|`MarshalStructure`|Interop|İsteğe bağlı öznitelik. Yapıları yerel koda hazırlama ilkesini denetler.|  
  
## <a name="all-attributes"></a>Tüm öznitelikler  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|*policy_setting*|Bu ilke ayarı, uygulamadaki türlere uygulanır. Olası değerler şunlardır `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`ve `Required All`. Daha fazla bilgi için bkz. [çalışma zamanı yönergesi Ilke ayarları](runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[Derleme > \<](assembly-element-net-native.md)|İlkeyi belirli bir derlemedeki tüm türlere uygular.|  
|[\<ad alanı >](namespace-element-net-native.md)|İlkeyi belirli bir ad alanındaki tüm türlere uygular.|  
|[\<türü >](type-element-net-native.md)|İlkeyi sınıf veya yapı gibi belirli bir türe uygular.|  
|[\<Typeörneklemesi >](typeinstantiation-element-net-native.md)|İlkeyi oluşturulan genel bir türe uygular. Örneğin, bir `List<String>` türünün ilkesini tanımlamak için bir [\<Typeörneklemesi >](typeinstantiation-element-net-native.md) öğesi kullanılabilir.|  
|[\<yöntemi >](method-element-net-native.md)|İlkeyi belirli bir türdeki bir yönteme uygular.|  
|[\<Methodörneklemesi >](methodinstantiation-element-net-native.md)|İlkeyi oluşturulmuş bir genel metoda uygular.|  
|[\<Özellik >](property-element-net-native.md)|İlkeyi belirli bir türdeki bir özelliğe uygular.|  
|[\<alan >](field-element-net-native.md)|İlkeyi belirli bir türdeki alana uygular.|  
|[\<olayı >](event-element-net-native.md)|İlkeyi belirli bir türdeki bir olaya uygular.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<yönergeler >](directives-element-net-native.md)|Çalışma zamanı yönergeleri dosyasının kök öğesi.|  
  
## <a name="remarks"></a>Açıklamalar  
 [\<yönergeleri >](directives-element-net-native.md) öğesi sıfır veya bir `<Application>` öğesi içerebilir. Tek bir yansıma yönergeleri dosyasındaki birden çok `<Application>` öğesi desteklenmez.  
  
 `<Application>` öğesi iki şekilde kullanılabilir:  
  
- Bir kapsayıcı olarak, meta verileri çalışma zamanında gerekli olan program öğelerini tanımlar. Bu durumda, `<Application>` öğesinde herhangi bir özniteliğe sahip olması gerekmez. Derleme zamanında, derleyici araçları, `<Application>` öğesinin alt öğeleri tarafından tanımlanan program öğeleri için .NET Framework Çekirdek kitaplıklar da dahil olmak üzere tüm kitaplıklarda arama yapın. Buna karşılık, derleyici araçları yalnızca [\<kitaplığı >](library-element-net-native.md)alt öğeleri tarafından tanımlanan program öğeleri Için [\<kitaplığı >](library-element-net-native.md) öğesi tarafından belirlenen kitaplığı arar.  
  
- Yansıma, serileştirme ve birlikte çalışma için uygulama genelinde ilke ayarlayan bir öğe olarak. `<Application>` öğesinin öznitelikleri, `<Application>` veya [\<kitaplığı >](library-element-net-native.md) öğesi tarafından tanımlanan alt öğeler tarafından geçersiz kılınabilen uygulama genelinde ilkeyi tanımlar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [\<kitaplığı > öğesi](library-element-net-native.md)
- [\<yönergeleri > öğesi](directives-element-net-native.md)
- [Çalışma Zamanı Yönerge Öğeleri](runtime-directive-elements.md)
- [Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu](runtime-directives-rd-xml-configuration-file-reference.md)
