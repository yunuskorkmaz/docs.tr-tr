---
title: <Assembly>Eleman (.NET Yerel)
ms.date: 03/30/2017
ms.assetid: cfe629eb-1106-4113-86e1-052f402d8d8b
ms.openlocfilehash: f3cf65b185b1db3289a0dbb785c2b91431951cc2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181076"
---
# <a name="assembly-element-net-native"></a>\<Montaj> Elemanı (.NET Yerli)
Belirli bir derlemedeki tüm türlere çalışma zamanı yansıtma ilkesi uygular.  
  
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
|`Name`|Genel|Gerekli öznitelik. Derlemenin basit adını belirtir.|  
|`Activate`|Yansıma|İsteğe bağlı öznitelik. Örneklerin etkinleştirilmesini etkinleştirmek için çalışan zamanında kuruculara erişimi denetler.|  
|`Browse`|Yansıma|İsteğe bağlı öznitelik. Derlemedeki türler hakkında bilgi için sorgulamayı veya derecelendirmeyi denetler, ancak çalışma zamanında dinamik erişim emmez.|  
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
|*Assembly_name*|Dosya uzantısı olmadan derlemenin basit adı. Bu öznitelik <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> özelliğe karşılık gelir. Örneğin, Extensions.dll adlı bir derlemenin adı "Uzantılar"dır.<br /><br /> Ayrıca, bu derlemeler `*Application*` yüklenmiş olsun veya olmasın, uygulama paketinizdeki tüm derlemelere ilke uygulamak için gerçek dizeyi de belirtebilirsiniz. `*Application*`.NET Framework derlemelerine hiçbir zaman ilke uygulamaz.|  
  
## <a name="all-other-attributes"></a>Diğer tüm öznitelikler  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|*policy_setting*|Derlemedeki tüm türler için bu ilke türüne uygulanacak ayar. Olası değerler `All` `Auto`, `Excluded` `Public`, `PublicAndInternal` `Required Public`, `Required PublicAndInternal`, `Required All`, , , ve . Daha fazla bilgi için [Runtime Yönergesi İlke Ayarları'na](runtime-directive-policy-settings.md)bakın.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Namespace>](namespace-element-net-native.md)|Alt ad alanındaki tüm türlere yansıma ilkesi uygular.|  
|[\<Tip>](type-element-net-native.md)|Yansıma ilkesini bir türe uygular.|  
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|Yapılı genel bir türe yansıma ilkesi uygular.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Başvuru>](application-element-net-native.md)|Uygulama genelindeki türler ve meta verileri çalışma zamanında yansımaiçin kullanılabilir tür üyeleri için bir kapsayıcı görevi görehizmet eder. Uygulama>öğesi sıfır, bir veya `<Assembly>` daha fazla öğeye sahip olabilir. [ \<](application-element-net-native.md)|  
|[\<Kütüphane>](library-element-net-native.md)|Meta verileri çalışma zamanında yansıtılamaya hazır olan türleri ve tür üyelerini içeren derlemeyi tanımlar. Kitaplık>öğesi sıfır `<Assembly>` veya bir öğeolabilir. [ \<](library-element-net-native.md)|  
  
## <a name="remarks"></a>Açıklamalar  
 Öğe, `<Assembly>` bir derlemedeki tüm türler için çalışma zamanı ilkesini tanımlar. Kitaplık>öğesinden farklıdır, bu öğe kitaplığı belirtir, ancak çalışma zamanı yansıtma ilkesini tanımlamak için alt öğelerine bağlıdır. [ \<](library-element-net-native.md) Öğe, `<Assembly>` bir alt öğe tarafından geçersiz kılınmadığı sürece derlemedeki tüm türler için geçerlidir.  
  
 Aşağıdaki örnek, "*Application `Name` \*" özniteliğini atayarak uygulama paketinizdeki derlemelerdeki tüm türlere çalışma zamanı ilkesini nasıl uygulayabileceğinizi gösterir. Öğe, `<Assembly>` [ \<Uygulama>](application-element-net-native.md) öğesinin bir alt öğesi olmalıdır.  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">
  <Application>
     <Assembly Name="*Application*" Dynamic="Required All" />
  </Application>
</Directives>  
```  
  
 , `Activate` `Browse`, `Dynamic`ve `Serialize` özniteliklerin tümü isteğe bağlıdır. Ancak, `<Assembly>` öğe bu özniteliklerden en az birini içermelidir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma Zamanı Yönerge İlkesi Ayarları](runtime-directive-policy-settings.md)
- [Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu](runtime-directives-rd-xml-configuration-file-reference.md)
- [Çalışma Zamanı Yönerge Öğeleri](runtime-directive-elements.md)
