---
title: <Assembly> Öğesi (.NET yerel)
ms.date: 03/30/2017
ms.assetid: cfe629eb-1106-4113-86e1-052f402d8d8b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c0788c05edace2142d348c679c73aa1b4404ce75
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59137858"
---
# <a name="assembly-element-net-native"></a>\<Derleme > öğesi (.NET yerel)
Çalışma zamanı yansıma ilkesini belirtilen bir derlemedeki tüm türleri için geçerlidir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<Assembly Name="assembly_name"   
          Activate="policy_setting"  
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
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Öznitelik türü|Açıklama|  
|---------------|--------------------|-----------------|  
|`Name`|Genel|Gerekli öznitelik. Bir derlemenin basit adını belirtir.|  
|`Activate`|Yansıma|İsteğe bağlı öznitelik. Oluşturucular örneklerinin etkinleştirmesi için çalışma zamanı erişimi denetler.|  
|`Browse`|Yansıma|İsteğe bağlı öznitelik. Hakkında bilgi için sorgulama veya derlemedeki türleri numaralandırma kontrol eder, ancak çalışma zamanında herhangi bir dinamik erişim sağlamaz.|  
|`Dynamic`|Yansıma|İsteğe bağlı öznitelik. Dinamik programlama etkinleştirmek için Oluşturucular, yöntemler, alanlar, özellikler ve olaylar, tüm tür üyelerini, çalışma zamanı erişimi denetler.|  
|`Serialize`|Serileştirme|İsteğe bağlı öznitelik. Oluşturucular, alanları ve tür örnekleri sıralanabilir ve kitaplıkları gibi Newtonsoft JSON seri hale getirici tarafından serisi etkinleştirmek için özellikler, çalışma zamanı erişimi denetler.|  
|`DataContractSerializer`|Serileştirme|İsteğe bağlı öznitelik. Denetimleri İlkesi kullanan Serileştirmenin <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> sınıfı.|  
|`DataContractJsonSerializer`|Serileştirme|İsteğe bağlı öznitelik. İlke kullanan bir JSON serileştirme denetleyen <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> sınıfı.|  
|`XmlSerializer`|Serileştirme|İsteğe bağlı öznitelik. İlke kullanan bir XML serileştirme denetleyen <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> sınıfı.|  
|`MarshalObject`|Birlikte çalışma|İsteğe bağlı öznitelik. Windows çalışma zamanı ve COM başvuru türlerini hazırlama denetimleri İlkesi|  
|`MarshalDelegate`|Birlikte çalışma|İsteğe bağlı öznitelik. Yerel kod için işlev işaretçileri olarak temsilci türleri hazırlama için ilke denetler.|  
|`MarshalStructure`|Birlikte çalışma|İsteğe bağlı öznitelik. Yerel kod yapılarına hazırlama için ilke denetler.|  
  
## <a name="name-attribute"></a>Ad özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|*assembly_name*|Dosya uzantısı olmadan derlemenin basit adını. Bu özniteliğe karşılık gelen <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> özelliği. Örneğin, Extensions.dll adlı bir derleme adı "Uzantıları" dir.<br /><br /> Değişmez değer dize belirtebilirsiniz `*Application*` bu derlemeler yüklü olsun olmasın tüm derlemeleri uygulama paketinizle ilkesi uygulamak için. `*Application*` hiçbir zaman ilkesi .NET Framework derlemeleri için geçerlidir.|  
  
## <a name="all-other-attributes"></a>Diğer tüm öznitelikler  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|*policy_setting*|Bu ilke türü derleme içindeki tüm türler için geçerli ayar. Olası değerler `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, ve `Required All`. Daha fazla bilgi için [çalışma zamanı yönerge İlkesi ayarları](../../../docs/framework/net-native/runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Namespace >](../../../docs/framework/net-native/namespace-element-net-native.md)|Alt ad alanında tüm türlerin yansıma ilkesini uygular.|  
|[\<türü >](../../../docs/framework/net-native/type-element-net-native.md)|Yansıma ilkesini bir türü için geçerlidir.|  
|[\<Typeınstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|Yansıma İlkesi oluşturulmuş bir genel türü için geçerlidir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Uygulama >](../../../docs/framework/net-native/application-element-net-native.md)|Birçok farklı uygulama türleri ve tür üyeleri olan meta verilerini yansıma çalışma zamanında kullanılabilir için kapsayıcı görevi görür. [ \<Uygulama >](../../../docs/framework/net-native/application-element-net-native.md) öğesi sıfır, bir veya daha fazla olabilir `<Assembly>` öğeleri.|  
|[\<Kitaplık >](../../../docs/framework/net-native/library-element-net-native.md)|Türler ve tür üyeleri olan meta verilerini yansıma çalışma zamanında kullanılabilir içeren derlemeyi tanımlar. [ \<Kitaplığı >](../../../docs/framework/net-native/library-element-net-native.md) öğesi sıfır veya bir olabilir `<Assembly>` öğesi.|  
  
## <a name="remarks"></a>Açıklamalar  
 `<Assembly>` Öğesi, bir derlemede tüm türler için çalışma zamanı ilkesini tanımlar. Bu farklıdır [ \<kitaplığı >](../../../docs/framework/net-native/library-element-net-native.md) kitaplık belirtiyor, ancak çalışma zamanı yansıma ilkesini tanımlamak için alt öğeleri üzerinde bağlıdır öğesi. `<Assembly>` Öğesi geçerli derlemedeki tüm türleri için bir alt öğesi tarafından geçersiz kılınmadığı sürece.  
  
 Aşağıdaki örnek nasıl çalışma zamanı İlkesi bütünleştirilmiş kodlar içindeki tüm türleri, uygulama paketi içinde atayarak uygulayabileceğiniz gösterir `Name` özniteliği değeri "* uygulama\*". `<Assembly>` Öğesi alt öğesi olmalıdır [ \<uygulama >](../../../docs/framework/net-native/application-element-net-native.md) öğesi.  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">   
  <Application>   
     <Assembly Name="*Application*" Dynamic="Required All" />   
  </Application>   
</Directives>  
```  
  
 `Activate`, `Browse`, `Dynamic`, Ve `Serialize` öznitelikleri tüm isteğe bağlı. Ancak, `<Assembly>` öğesi bu öznitelikler en az birini içermelidir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma Zamanı Yönerge İlkesi Ayarları](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
- [Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [Çalışma Zamanı Yönerge Öğeleri](../../../docs/framework/net-native/runtime-directive-elements.md)
