---
title: <Application> Öğesi (.NET yerel)
ms.date: 03/30/2017
ms.assetid: b4e9b37a-059b-4076-8f56-cb3f9cef0cd9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 366878fbfbfbe3e3951095c9ad82c1260638a0cb
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55270816"
---
# <a name="application-element-net-native"></a>\<Uygulama > öğesi (.NET yerel)
Birçok farklı uygulama türleri ve olan meta verilerini yansıma çalışma zamanında kullanılabilir ve tüm program öğeleri bir uygulama çalışma zamanı yansıma ilkenin uygulanacağı tür üyeleri için kapsayıcı görevi görür.  
  
 \<Yönergeleri > öğesi  
\<Uygulama > öğesi (rd.xml)  
  
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
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır. Alt öğeleri tabloda, ilke çalışma zamanında belirli program öğelerini için kullanılabilir hale getirileceğini meta veri türünü ifade eder.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Öznitelik türü|Açıklama|  
|---------------|--------------------|-----------------|  
|`Activate`|Yansıma|İsteğe bağlı öznitelik. Oluşturucular örneklerinin etkinleştirmesi için çalışma zamanı erişimi denetler.|  
|`Browse`|Yansıma|İsteğe bağlı öznitelik. Hakkında bilgi için sorgulama veya numaralandırma türleri kontrol eder, ancak çalışma zamanında herhangi bir dinamik erişim sağlamaz.|  
|`Dynamic`|Yansıma|İsteğe bağlı öznitelik. Dinamik programlama etkinleştirmek için Oluşturucular, yöntemler, alanlar, özellikler ve olaylar, tüm tür üyelerini, çalışma zamanı erişimi denetler.|  
|`Serialize`|Serileştirme|İsteğe bağlı öznitelik. Oluşturucular, alanları ve tür örnekleri sıralanabilir ve kitaplıkları gibi Newtonsoft JSON seri hale getirici tarafından serisi etkinleştirmek için özellikler, çalışma zamanı erişimi denetler.|  
|`DataContractSerializer`|Serileştirme|İsteğe bağlı öznitelik. Denetimleri İlkesi kullanan Serileştirmenin <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> sınıfı.|  
|`DataContractJsonSerializer`|Serileştirme|İsteğe bağlı öznitelik. İlke kullanan bir JSON serileştirme denetleyen <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> sınıfı.|  
|`XmlSerializer`|Serileştirme|İsteğe bağlı öznitelik. İlke kullanan bir XML serileştirme denetleyen <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> sınıfı.|  
|`MarshalObject`|Birlikte çalışma|İsteğe bağlı öznitelik. Windows çalışma zamanı ve COM başvuru türlerini hazırlama denetimleri İlkesi|  
|`MarshalDelegate`|Birlikte çalışma|İsteğe bağlı öznitelik. Yerel kod için işlev işaretçileri olarak temsilci türleri hazırlama için ilke denetler.|  
|`MarshalStructure`|Birlikte çalışma|İsteğe bağlı öznitelik. Yerel kod yapılarına hazırlama için ilke denetler.|  
  
## <a name="all-attributes"></a>Tüm öznitelikler  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|*policy_setting*|Uygulama türlerini uygulamak için bu ilke ayarı. Olası değerler `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, ve `Required All`. Daha fazla bilgi için [çalışma zamanı yönerge İlkesi ayarları](../../../docs/framework/net-native/runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Derleme >](../../../docs/framework/net-native/assembly-element-net-native.md)|İlke, belirli bir derlemedeki tüm türleri için geçerlidir.|  
|[\<Namespace >](../../../docs/framework/net-native/namespace-element-net-native.md)|İlke, belirli bir ad alanındaki tüm türlere uygulanır.|  
|[\<türü >](../../../docs/framework/net-native/type-element-net-native.md)|İlke, bir sınıf veya yapı gibi belirli bir türe uygulanır.|  
|[\<Typeınstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|İlke oluşturulmuş bir genel türü için geçerlidir. Örneğin, bir [ \<Typeınstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) öğesi için ilke tanımlamak için kullanılabilir bir `List<String>` türü.|  
|[\<Yöntem >](../../../docs/framework/net-native/method-element-net-native.md)|İlke, belirli bir tür üzerindeki bir yöntem uygular.|  
|[\<Methodınstantiation >](../../../docs/framework/net-native/methodinstantiation-element-net-native.md)|İlke oluşturulmuş bir genel yöntem için geçerlidir.|  
|[\<Özellik >](../../../docs/framework/net-native/property-element-net-native.md)|İlke, belirli bir tür üzerindeki bir özellik için geçerlidir.|  
|[\<alan >](../../../docs/framework/net-native/field-element-net-native.md)|Belirli bir tür bir alan ilke uygulanır.|  
|[\<Olay >](../../../docs/framework/net-native/event-element-net-native.md)|Belirli bir tür bir olayda ilke uygulanır.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Yönergeleri >](../../../docs/framework/net-native/directives-element-net-native.md)|Bir çalışma zamanı yönergeleri dosyasının kök öğe.|  
  
## <a name="remarks"></a>Açıklamalar  
 [ \<Yönergeleri >](../../../docs/framework/net-native/directives-element-net-native.md) sıfır veya bir öğe içerebilir `<Application>` öğesi. Birden çok `<Application>` tek yansıma yönergeleri dosyasındaki öğeleri desteklenmez.  
  
 `<Application>` Öğesi iki yoldan biriyle kullanılabilir:  
  
-   Program öğelerine olan meta verileri tanımlamak için bir kapsayıcı çalışma zamanında gereklidir. Bu durumda, `<Application>` öğesi herhangi bir özniteliği sahip. Derleme zamanında derleyici araçları alt öğeler tarafından tanıtılan program öğeler için .NET Framework Çekirdek kitaplıkları dahil olmak üzere tüm kitaplıkları arama `<Application>` öğesi. Buna karşılık, derleyici araçları yalnızca belirlenen kitaplık arama [ \<kitaplığı >](../../../docs/framework/net-native/library-element-net-native.md) öğesi için alt öğeler tarafından tanıtılan program öğelerine [ \<kitaplığı >](../../../docs/framework/net-native/library-element-net-native.md).  
  
-   Yansıma, seri hale getirme ve birlikte çalışma için birçok farklı uygulama ilkesini ayarlar bir öğe. Özniteliklerini `<Application>` define öğesi tarafından tanımlanan alt öğeler tarafından geçersiz kılınabilir birçok farklı uygulama ilkesi `<Application>` veya [ \<kitaplığı >](../../../docs/framework/net-native/library-element-net-native.md) öğesi.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [\<Kitaplık > öğesi](../../../docs/framework/net-native/library-element-net-native.md)
- [\<Yönergeleri > öğesi](../../../docs/framework/net-native/directives-element-net-native.md)
- [Çalışma Zamanı Yönerge Öğeleri](../../../docs/framework/net-native/runtime-directive-elements.md)
- [Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
