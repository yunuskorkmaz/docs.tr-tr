---
title: <TypeInstantiation>Öğesi (.NET Native)
ms.date: 03/30/2017
ms.assetid: a5eada64-075b-4162-9655-ded84e4681f2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 375c95a30f4f60bb711e176cb6c2d0c5fd763e2f
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71049106"
---
# <a name="typeinstantiation-element-net-native"></a>\<Typeörneklemesi > öğesi (.NET Native)
Oluşturulmuş genel bir türe çalışma zamanı yansıtma ilkesi uygular.  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<TypeInstantiation Name="type_name"  
                   Arguments="type_arguments"  
                   Activate="policy_type"  
                   Browse="policy_type"  
                   Dynamic="policy_type"  
                   Serialize="policy_type"  
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
|`Name`|Genel|Gerekli öznitelik. Tür adını belirtir.|  
|`Arguments`|Genel|Gerekli öznitelik. Genel tür bağımsız değişkenlerini belirtir. Birden çok bağımsız değişken varsa, bunlar virgülle ayrılır.|  
|`Activate`|Yansıma|İsteğe bağlı öznitelik. Örneklerin etkinleştirilmesini sağlamak için oluşturuculara çalışma zamanı erişimini denetler.|  
|`Browse`|Yansıma|İsteğe bağlı öznitelik. Program öğeleri hakkında bilgi sorgulamayı denetler, ancak hiçbir çalışma zamanı erişimini etkinleştirmez.|  
|`Dynamic`|Yansıma|İsteğe bağlı öznitelik. Dinamik programlamayı etkinleştirmek için oluşturucular, Yöntemler, alanlar, Özellikler ve olaylar dahil olmak üzere tüm tür üyelerine çalışma zamanı erişimini denetler.|  
|`Serialize`|Serileştirme|İsteğe bağlı öznitelik. Tür örneklerinin, Newtonsoft JSON serileştirici gibi kitaplıklar tarafından serileştirilmesi ve seri durumdan çıkarılmakta olması için oluşturuculara, alanlara ve özelliklere çalışma zamanı erişimini denetler.|  
|`DataContractSerializer`|Serileştirme|İsteğe bağlı öznitelik. <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> Sınıfını kullanan serileştirme için ilkeyi denetler.|  
|`DataContractJsonSerializer`|Serileştirme|İsteğe bağlı öznitelik. <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> Sınıfını kullanan JSON serileştirme için ilkeyi denetler.|  
|`XmlSerializer`|Serileştirme|İsteğe bağlı öznitelik. <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> Sınıfını kullanan XML serileştirme ilkesini denetler.|  
|`MarshalObject`|Interop|İsteğe bağlı öznitelik. Windows Çalışma Zamanı ve COM 'a başvuru türlerini hazırlama ilkesini denetler.|  
|`MarshalDelegate`|Interop|İsteğe bağlı öznitelik. Temsilci türlerini yerel koda işlev işaretçileri olarak hazırlama ilkesini denetler.|  
|`MarshalStructure`|Interop|İsteğe bağlı öznitelik. Yapıları yerel koda hazırlama ilkesini denetler.|  
  
## <a name="name-attribute"></a>Ad özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|*type_name*|Tür adı. Bu `<TypeInstantiation>` öğe `<TypeInstantiation>` [ \<](type-element-net-native.md) [ ,bir\<ad alanı >](namespace-element-net-native.md) öğesi, bir tür > öğesi ya da başka bir öğe ise, type_name ad alanı olmadan türün adını belirtebilir. Aksi halde, *type_name* tam nitelikli tür adını içermelidir. Tür adı süslenmiş değildir. Örneğin, bir <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> nesnesi `<TypeInstantiation>` için öğesi şu şekilde görünebilir:<br /><br /> `\<TypeInstantiation Name=System.Collections.Generic.List Dynamic="Required Public" />`|  
  
## <a name="arguments-attribute"></a>Arguments özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|*type_argument*|Genel tür bağımsız değişkenlerini belirtir. Birden çok bağımsız değişken varsa, bunlar virgülle ayrılır. Her bağımsız değişken tam nitelikli tür adından oluşmalıdır.|  
  
## <a name="all-other-attributes"></a>Diğer tüm öznitelikler  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|*policy_setting*|Oluşturulan genel tür için bu ilke türüne uygulanacak ayar. Olası değerler şunlardır `All` `Auto` ,,`Excluded`,,,, ve`Required All`. `Public` `PublicAndInternal` `Required Public` `Required PublicAndInternal` Daha fazla bilgi için bkz. [çalışma zamanı yönergesi Ilke ayarları](runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Olay >](event-element-net-native.md)|Bu türe ait bir olaya yansıma ilkesi uygular.|  
|[\<Alan >](field-element-net-native.md)|Bu türe ait olan bir alana yansıma ilkesi uygular.|  
|[\<Impliestype >](impliestype-element-net-native.md)|İlke, kapsayan `<TypeInstantiation>` öğe tarafından temsil edilen türe uygulanmışsa ilkeyi bir türe uygular.|  
|[\<Yöntem >](method-element-net-native.md)|Bu türe ait bir yönteme yansıma ilkesi uygular.|  
|[\<Methodörneklemesi >](methodinstantiation-element-net-native.md)|Bu türe ait oluşturulmuş bir genel metoda yansıma ilkesi uygular.|  
|[\<Özellik >](property-element-net-native.md)|Yansıma ilkesini bu türe ait olan bir özelliğe uygular.|  
|[\<Tür >](type-element-net-native.md)|Yansıtma ilkesini iç içe bir türe uygular.|  
|`<TypeInstantiation>`|Yansıtma ilkesini, iç içe oluşturulmuş bir genel türe uygular.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Uygulama >](application-element-net-native.md)|Uygulama genelinde türler için bir kapsayıcı görevi görür ve meta verileri çalışma zamanında yansıma için kullanılabilir olan üyeleri yazın.|  
|[\<Bütünleştirilmiş kod >](assembly-element-net-native.md)|Belirtilen derlemedeki tüm türlere yansıma ilkesi uygular.|  
|[\<Kitaplık >](library-element-net-native.md)|Meta verileri çalışma zamanında yansıma için kullanılabilir olan türleri ve tür üyelerini içeren derlemeyi tanımlar.|  
|[\<Ad alanı >](namespace-element-net-native.md)|Bir ad alanındaki tüm türlere yansıma ilkesi uygular.|  
|[\<Tür >](type-element-net-native.md)|Yansıma ilkesini bir türe ve tüm üyelerine uygular.|  
|`<TypeInstantiation>`|Oluşturulan genel türe ve tüm üyelerine yansıma ilkesi uygular.|  
  
## <a name="remarks"></a>Açıklamalar  
 Yansıma, serileştirme ve birlikte çalışma özniteliklerinin tümü isteğe bağlıdır. Ancak, en az bir tane bulunmalıdır.  
  
 Bir `<TypeInstantiation>` öğe [ \<](type-element-net-native.md) [ \<](namespace-element-net-native.md)bir [bütünleştirilmiş kod >, ad alanı > veya tür >, öğesi ise, üst öğe tarafından tanımlanan ilke ayarlarını geçersiz kılar. \<](assembly-element-net-native.md) `<TypeInstantiation>` [ Bir\<tür >](type-element-net-native.md) öğesi karşılık gelen genel tür tanımını tanımlıyorsa, öğe yalnızca belirtilen oluşturulmuş genel türün örneklemeleri için çalışma zamanı yansıtma ilkesini geçersiz kılar.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, oluşturulmuş <xref:System.Collections.Generic.Dictionary%602> bir nesneden genel tür tanımını almak için yansıma kullanır. Ayrıca, oluşturulan genel türleri ve genel tür <xref:System.Type> tanımlarını temsil eden nesneler hakkındaki bilgileri göstermek için de yansıma kullanır. Örnekteki değişken `b` bir <xref:Windows.UI.Xaml.Controls.TextBlock> denetimdir.  
  
 [!code-csharp[ProjectN_Reflection#2](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/makegenerictype1.cs#2)]  
  
 .NET Native araç zinciri ile derlemeden sonra, örnek, <xref:System.Type.GetGenericTypeDefinition%2A?displayProperty=nameWithType> yöntemi çağıran satırda bir [MissingMetadataException](missingmetadataexception-class-net-native.md) özel durumu oluşturur. Çalışma zamanı yönergeleri dosyasına aşağıdaki `<TypeInstantiation>` öğeyi ekleyerek özel durumu ortadan kaldırabilir ve gerekli meta verileri sağlayabilirsiniz:  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Application>  
    <Assembly Name="*Application*" Dynamic="Required All" />  
     <TypeInstantiation Name="System.Collections.Generic.Dictionary"  
                        Arguments="System.String,GenericType.Example"  
                        Dynamic="Required Public" />  
  </Application>  
</Directives>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu](runtime-directives-rd-xml-configuration-file-reference.md)
- [Çalışma Zamanı Yönerge Öğeleri](runtime-directive-elements.md)
- [Çalışma Zamanı Yönerge İlkesi Ayarları](runtime-directive-policy-settings.md)
