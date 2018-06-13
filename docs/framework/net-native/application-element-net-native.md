---
title: '&lt;Application&gt; Öğesi (.NET Yerel)'
ms.date: 03/30/2017
ms.assetid: b4e9b37a-059b-4076-8f56-cb3f9cef0cd9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 60145611981b53d4778e7c52c6138b6a9b58a592
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33394640"
---
# <a name="ltapplicationgt-element-net-native"></a>&lt;Application&gt; Öğesi (.NET Yerel)
Uygulama çapında türleri ve, meta verileri yansıma çalışma zamanında yüklenebilir ve bir uygulamadaki tüm program öğelerinin çalışma zamanı yansıma ilkenin uygulandığı tür üyeleri için bir kapsayıcı görevi görür.  
  
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
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır. Alt öğeler tabloda ilke çalışma zamanında belirli programın öğeler için kullanılabilir hale getirileceğini meta veri türü ifade eder.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Öznitelik türü|Açıklama|  
|---------------|--------------------|-----------------|  
|`Activate`|Yansıma|İsteğe bağlı öznitelik. Oluşturucular örneklerinin etkinleştirmesi için çalışma zamanı erişimi kontrol eder.|  
|`Browse`|Yansıma|İsteğe bağlı öznitelik. Hakkında bilgi için sorgulama veya numaralandırma türleri kontrol eder, ancak çalışma zamanında herhangi bir dinamik erişim sağlamaz.|  
|`Dynamic`|Yansıma|İsteğe bağlı öznitelik. Dinamik programlama etkinleştirmek için Oluşturucular, yöntemleri, alanları, özellikleri ve olayları dahil tüm tür üyeleri, çalışma zamanı erişimi kontrol eder.|  
|`Serialize`|Serileştirme|İsteğe bağlı öznitelik. Oluşturucular, alanları ve seri hale getirilmiş ve kitaplıklar gibi Newtonsoft JSON seri hale getirici tarafından seri türü örnekleri etkinleştirmek için özellikleri, çalışma zamanı erişimi denetler.|  
|`DataContractSerializer`|Serileştirme|İsteğe bağlı öznitelik. Denetimleri kullanan serileştirme için ilke <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> sınıfı.|  
|`DataContractJsonSerializer`|Serileştirme|İsteğe bağlı öznitelik. Denetimleri kullanan JSON serileştirmesi için ilke <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> sınıfı.|  
|`XmlSerializer`|Serileştirme|İsteğe bağlı öznitelik. Denetimleri kullanan XML serileştirme için ilke <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> sınıfı.|  
|`MarshalObject`|Birlikte çalışma|İsteğe bağlı öznitelik. Başvuru türleri Windows çalışma zamanı ve COM hazırlama denetimlerini İlkesi|  
|`MarshalDelegate`|Birlikte çalışma|İsteğe bağlı öznitelik. Yerel kod için işlev işaretçileri olarak temsilci türleri hazırlama için ilke denetler.|  
|`MarshalStructure`|Birlikte çalışma|İsteğe bağlı öznitelik. Yerel kod yapılara hazırlama için ilke denetler.|  
  
## <a name="all-attributes"></a>Tüm öznitelikleri  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|*policy_setting*|Uygulama türlerini uygulamak için bu ilke ayarı. Olası değerler şunlardır: `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, ve `Required All`. Daha fazla bilgi için bkz: [çalışma zamanı yönerge İlkesi ayarları](../../../docs/framework/net-native/runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<derleme >](../../../docs/framework/net-native/assembly-element-net-native.md)|Belirli bir derleme içindeki tüm türler için ilke uygulanır.|  
|[\<Namespace >](../../../docs/framework/net-native/namespace-element-net-native.md)|Belirli bir ad alanı içindeki tüm türler için ilke uygulanır.|  
|[\<türü >](../../../docs/framework/net-native/type-element-net-native.md)|Bir sınıf veya yapı gibi belirli türde bir ilke uygulanır.|  
|[\<Typeınstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|İlke oluşturulan genel bir tür için geçerlidir. Örneğin, bir [ \<Typeınstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) öğesi için ilke tanımlamak için kullanılan bir `List<String>` türü.|  
|[\<Yöntem >](../../../docs/framework/net-native/method-element-net-native.md)|Belirli bir türün bir yöntem ilke uygulanır.|  
|[\<Methodınstantiation >](../../../docs/framework/net-native/methodinstantiation-element-net-native.md)|İlke için yapılandırılmış bir genel yöntem uygulanır.|  
|[\<Özellik >](../../../docs/framework/net-native/property-element-net-native.md)|Belirli bir türün bir özellik için ilke uygulanır.|  
|[\<Alanı >](../../../docs/framework/net-native/field-element-net-native.md)|Belirli bir türün bir alanı ilke uygulanır.|  
|[\<Olay >](../../../docs/framework/net-native/event-element-net-native.md)|Belirli bir türü bir olayına ilke uygulanır.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Yönergeleri >](../../../docs/framework/net-native/directives-element-net-native.md)|Bir çalışma zamanı yönergeleri dosyasının kök öğesinin.|  
  
## <a name="remarks"></a>Açıklamalar  
 [ \<Yönergeleri >](../../../docs/framework/net-native/directives-element-net-native.md) sıfır veya bir öğe içerebilir `<Application>` öğesi. Birden çok `<Application>` bir tek yansıma yönergeleri dosyasındaki öğeleri desteklenmiyor.  
  
 `<Application>` Öğesi iki yoldan biriyle kullanılabilir:  
  
-   Program öğeleri, meta verileri tanımlamak için bir kapsayıcı olarak çalışma zamanında gereklidir. Bu durumda, `<Application>` öğesi öznitelikleri sahip. Derleme zamanında derleyici Araçlar alt öğeleri tarafından tanımlanan programı öğeleri için .NET Framework core kitaplıkları da dahil olmak üzere tüm kitaplıkları arama `<Application>` öğesi. Buna karşılık, yalnızca belirlenen kitaplık derleyici Araçlar arama [ \<kitaplığı >](../../../docs/framework/net-native/library-element-net-native.md) öğesi alt öğeleri tarafından tanıtılan program öğeleri için [ \<kitaplığı >](../../../docs/framework/net-native/library-element-net-native.md).  
  
-   Yansıma, seri hale getirme ve birlikte çalışma için uygulama genelinde İlkesi ayarlar bir öğe. Özniteliklerini `<Application>` öğesi tarafından tanımlanan alt öğeleri tarafından geçersiz kılınabilir uygulama genelinde İlkesi tanımlamak `<Application>` veya [ \<kitaplığı >](../../../docs/framework/net-native/library-element-net-native.md) öğesi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [\<Kitaplık > öğesi](../../../docs/framework/net-native/library-element-net-native.md)  
 [\<Yönergeleri > öğesi](../../../docs/framework/net-native/directives-element-net-native.md)  
 [Çalışma Zamanı Yönerge Öğeleri](../../../docs/framework/net-native/runtime-directive-elements.md)  
 [Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
