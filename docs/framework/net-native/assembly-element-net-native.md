---
title: <Assembly> öğesi (.NET Native)
ms.date: 03/30/2017
ms.assetid: cfe629eb-1106-4113-86e1-052f402d8d8b
ms.openlocfilehash: bad2286c5306b9f8a8955ebef12e5e99aec5bb89
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128504"
---
# <a name="assembly-element-net-native"></a>\<assembly > öğesi (.NET Native)
Belirtilen derlemedeki tüm türlere çalışma zamanı yansıma ilkesini uygular.  
  
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
|`Activate`|Yansıma|İsteğe bağlı öznitelik. Örneklerin etkinleştirilmesini sağlamak için oluşturuculara çalışma zamanı erişimini denetler.|  
|`Browse`|Yansıma|İsteğe bağlı öznitelik. Derlemedeki türler hakkında bilgi sorgulamayı veya numaralandırma denetimleri yapar, ancak çalışma zamanında hiçbir dinamik erişimi etkinleştirmez.|  
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
|*assembly_name*|Derlemenin, dosya uzantısı olmadan basit adı. Bu öznitelik <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> özelliğine karşılık gelir. Örneğin, Extensions. dll adlı bir derlemenin adı "Uzantılar" dır.<br /><br /> Ayrıca, bu derlemelerin yüklenip yüklenmediğini, uygulama paketinizdeki tüm derlemelere ilke uygulamak için `*Application*` değişmez değer dizesini de belirtebilirsiniz. `*Application*` hiçbir koşulda .NET Framework derlemelere ilke uygulamaz.|  
  
## <a name="all-other-attributes"></a>Diğer tüm öznitelikler  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|*policy_setting*|Derlemedeki tüm türler için bu ilke türüne uygulanacak ayar. Olası değerler şunlardır `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`ve `Required All`. Daha fazla bilgi için bkz. [çalışma zamanı yönergesi Ilke ayarları](runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<ad alanı >](namespace-element-net-native.md)|Bir alt ad alanındaki tüm türlere yansıma ilkesi uygular.|  
|[\<türü >](type-element-net-native.md)|Yansıma ilkesini bir türe uygular.|  
|[\<Typeörneklemesi >](typeinstantiation-element-net-native.md)|Yansıma ilkesini oluşturulmuş genel bir türe uygular.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<uygulama >](application-element-net-native.md)|Uygulama genelinde türler için bir kapsayıcı görevi görür ve meta verileri çalışma zamanında yansıma için kullanılabilir olan üyeleri yazın. [\<uygulama >](application-element-net-native.md) öğesi sıfır, bir veya daha fazla `<Assembly>` öğesine sahip olabilir.|  
|[\<kitaplığı >](library-element-net-native.md)|Meta verileri çalışma zamanında yansıma için kullanılabilir olan türleri ve tür üyelerini içeren derlemeyi tanımlar. [\<Library >](library-element-net-native.md) öğesi sıfır veya bir `<Assembly>` öğesine sahip olabilir.|  
  
## <a name="remarks"></a>Açıklamalar  
 `<Assembly>` öğesi bir derlemedeki tüm türler için çalışma zamanı ilkesini tanımlar. Bu, bir kitaplığı belirten, ancak çalışma zamanı yansıtma ilkesini tanımlamak için alt öğelerine bağımlı [\<kitaplığı >](library-element-net-native.md) öğesinden farklıdır. `<Assembly>` öğesi bir alt öğe tarafından geçersiz kılınmadıkça derlemedeki tüm türlere uygulanır.  
  
 Aşağıdaki örnek, `Name` özniteliği bir "* Application\*" değeri atayarak uygulama paketinizdeki derlemelerdeki tüm türlere çalışma zamanı ilkesini nasıl uygulayacağınızı gösterir. `<Assembly>` öğesi [\<uygulama >](application-element-net-native.md) öğesinin bir alt öğesi olmalıdır.  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">   
  <Application>   
     <Assembly Name="*Application*" Dynamic="Required All" />   
  </Application>   
</Directives>  
```  
  
 `Activate`, `Browse`, `Dynamic`ve `Serialize` özniteliklerinin tümü isteğe bağlıdır. Ancak `<Assembly>` öğesi bu özniteliklerden en az birini içermelidir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma Zamanı Yönerge İlkesi Ayarları](runtime-directive-policy-settings.md)
- [Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu](runtime-directives-rd-xml-configuration-file-reference.md)
- [Çalışma Zamanı Yönerge Öğeleri](runtime-directive-elements.md)
