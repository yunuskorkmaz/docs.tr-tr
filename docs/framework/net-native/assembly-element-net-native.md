---
title: '&lt;Assembly&gt; Öğesi (.NET Yerel)'
ms.date: 03/30/2017
ms.assetid: cfe629eb-1106-4113-86e1-052f402d8d8b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fa78c7085c9c20e6a8a165c90ec9e3c2d8304581
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="ltassemblygt-element-net-native"></a>&lt;Assembly&gt; Öğesi (.NET Yerel)
Belirtilen derleme içindeki tüm türler için çalışma zamanı yansıma ilke uygulanır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<Assembly Name="assembly_name"   
          Activate="policy_setting"  
          Browse="policy_setting"  
          Dynamic="policy_setting"  
          Serialize="policy_setting" />  
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
|`Name`|Genel|Gerekli öznitelik. Basit bir bütünleştirilmiş kodun adını belirtir.|  
|`Activate`|Yansıma|İsteğe bağlı öznitelik. Oluşturucular örneklerinin etkinleştirmesi için çalışma zamanı erişimi kontrol eder.|  
|`Browse`|Yansıma|İsteğe bağlı öznitelik. Hakkında bilgi için sorgulama veya derlemesindeki türler numaralandırma kontrol eder, ancak çalışma zamanında herhangi bir dinamik erişim sağlamaz.|  
|`Dynamic`|Yansıma|İsteğe bağlı öznitelik. Dinamik programlama etkinleştirmek için Oluşturucular, yöntemleri, alanları, özellikleri ve olayları dahil tüm tür üyeleri, çalışma zamanı erişimi kontrol eder.|  
|`Serialize`|Serileştirme|İsteğe bağlı öznitelik. Oluşturucular, alanları ve seri hale getirilmiş ve kitaplıklar gibi Newtonsoft JSON seri hale getirici tarafından seri türü örnekleri etkinleştirmek için özellikleri, çalışma zamanı erişimi denetler.|  
|`DataContractSerializer`|Serileştirme|İsteğe bağlı öznitelik. Denetimleri kullanan serileştirme için ilke <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> sınıfı.|  
|`DataContractJsonSerializer`|Serileştirme|İsteğe bağlı öznitelik. Denetimleri kullanan JSON serileştirmesi için ilke <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> sınıfı.|  
|`XmlSerializer`|Serileştirme|İsteğe bağlı öznitelik. Denetimleri kullanan XML serileştirme için ilke <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> sınıfı.|  
|`MarshalObject`|Birlikte çalışma|İsteğe bağlı öznitelik. Başvuru türleri Windows çalışma zamanı ve COM hazırlama denetimlerini İlkesi|  
|`MarshalDelegate`|Birlikte çalışma|İsteğe bağlı öznitelik. Yerel kod için işlev işaretçileri olarak temsilci türleri hazırlama için ilke denetler.|  
|`MarshalStructure`|Birlikte çalışma|İsteğe bağlı öznitelik. Yerel kod yapılara hazırlama için ilke denetler.|  
  
## <a name="name-attribute"></a>Ad özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|*assembly_name*|Derlemenin dosya uzantısı olmadan basit adı. Bu özniteliğe karşılık gelen <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> özelliği. Örneğin, Extensions.dll adlı bir derleme "Uzantılarla" adıdır.<br /><br /> Değişmez değer dize de belirtebilirsiniz `*Application*` bu derlemeler yüklü olsun olmasın tüm derlemelerde uygulama paketi, ilkeyi uygulamak için. `*Application*` hiç ilke .NET Framework derlemeler için geçerlidir.|  
  
## <a name="all-other-attributes"></a>Tüm diğer özniteliklerle  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|*policy_setting*|Derleme içindeki tüm türler için bu ilke türü için geçerli ayar. Olası değerler şunlardır: `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, ve `Required All`. Daha fazla bilgi için bkz: [çalışma zamanı yönerge İlkesi ayarları](../../../docs/framework/net-native/runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Namespace >](../../../docs/framework/net-native/namespace-element-net-native.md)|Bir alt ad alanındaki tüm türleri yansıma ilke uygulanır.|  
|[\<türü >](../../../docs/framework/net-native/type-element-net-native.md)|Yansıma ilke türü için geçerlidir.|  
|[\<Typeınstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|Yansıma ilke oluşturulan genel bir tür için geçerlidir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Uygulama >](../../../docs/framework/net-native/application-element-net-native.md)|Uygulama çapında türleri ve tür üyeleri olan meta verilerini yansıma çalışma zamanında yüklenebilir için kapsayıcı görevi görür. [ \<Uygulama >](../../../docs/framework/net-native/application-element-net-native.md) öğesi sıfır, bir veya daha fazla olabilir `<Assembly>` öğeleri.|  
|[\<Kitaplık >](../../../docs/framework/net-native/library-element-net-native.md)|Türleri ve tür üyeleri olan meta verilerini yansıma çalışma zamanında yüklenebilir içeren derlemenin tanımlar. [ \<Kitaplığı >](../../../docs/framework/net-native/library-element-net-native.md) öğesi sıfır veya bir olabilir `<Assembly>` öğesi.|  
  
## <a name="remarks"></a>Açıklamalar  
 `<Assembly>` Öğesi, bir derlemede tüm türleri için çalışma zamanı İlkesi tanımlar. Bu farklı [ \<kitaplığı >](../../../docs/framework/net-native/library-element-net-native.md) , bir kitaplık belirtiyor, ancak çalışma zamanı yansıma ilkesini tanımlamak için ve alt öğeleri bağımlı öğesi. `<Assembly>` Öğesi geçerli bir derleme içindeki tüm türler için bir alt öğesi tarafından kılınmadıkça.  
  
 Aşağıdaki örnek, nasıl çalışma zamanı İlkesi derlemeleri içindeki tüm türler uygulama paketinizi içinde atayarak uygulayabileceğiniz gösterir `Name` değerini özniteliği "* uygulama\*". `<Assembly>` Öğesi bir alt öğesi olması gerekir [ \<uygulama >](../../../docs/framework/net-native/application-element-net-native.md) öğesi.  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">   
  <Application>   
     <Assembly Name="*Application*" Dynamic="Required All" />   
  </Application>   
</Directives>  
```  
  
 `Activate`, `Browse`, `Dynamic`, Ve `Serialize` öznitelikleri tüm isteğe bağlı. Ancak, `<Assembly>` öğesi bu öznitelikler en az birini içermelidir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çalışma Zamanı Yönerge İlkesi Ayarları](../../../docs/framework/net-native/runtime-directive-policy-settings.md)  
 [Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [Çalışma Zamanı Yönerge Öğeleri](../../../docs/framework/net-native/runtime-directive-elements.md)
