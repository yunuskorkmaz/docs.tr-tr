---
title: <TypeInstantiation>Öğesi (.NET Native)
ms.date: 03/30/2017
ms.assetid: a5eada64-075b-4162-9655-ded84e4681f2
ms.openlocfilehash: 9069856b3d8739724d148b5eea5d4188c8b8b9e1
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73128675"
---
# <a name="typeinstantiation-element-net-native"></a>\<TypeInstantiation>Öğesi (.NET Native)
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
|`DataContractSerializer`|Serileştirme|İsteğe bağlı öznitelik. Sınıfını kullanan serileştirme için ilkeyi denetler <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> .|  
|`DataContractJsonSerializer`|Serileştirme|İsteğe bağlı öznitelik. Sınıfını kullanan JSON serileştirme için ilkeyi denetler <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> .|  
|`XmlSerializer`|Serileştirme|İsteğe bağlı öznitelik. Sınıfını kullanan XML serileştirme ilkesini denetler <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> .|  
|`MarshalObject`|Interop|İsteğe bağlı öznitelik. Windows Çalışma Zamanı ve COM 'a başvuru türlerini hazırlama ilkesini denetler.|  
|`MarshalDelegate`|Interop|İsteğe bağlı öznitelik. Temsilci türlerini yerel koda işlev işaretçileri olarak hazırlama ilkesini denetler.|  
|`MarshalStructure`|Interop|İsteğe bağlı öznitelik. Yapıları yerel koda hazırlama ilkesini denetler.|  
  
## <a name="name-attribute"></a>Ad özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|*type_name*|Tür adı. Bu `<TypeInstantiation>` öğe bir [\<Namespace>](namespace-element-net-native.md) öğe, [\<Type>](type-element-net-native.md) öğe veya başka bir öğesi ise, `<TypeInstantiation>` *type_name* ad alanı olmadan türün adını belirtebilir. Aksi takdirde, *type_name* tam nitelikli tür adını içermelidir. Tür adı süslenmiş değildir. Örneğin, bir nesnesi için <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> `<TypeInstantiation>` öğesi şu şekilde görünebilir:<br /><br /> `\<TypeInstantiation Name=System.Collections.Generic.List Dynamic="Required Public" />`|  
  
## <a name="arguments-attribute"></a>Arguments özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|*type_argument*|Genel tür bağımsız değişkenlerini belirtir. Birden çok bağımsız değişken varsa, bunlar virgülle ayrılır. Her bağımsız değişken tam nitelikli tür adından oluşmalıdır.|  
  
## <a name="all-other-attributes"></a>Diğer tüm öznitelikler  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|*policy_setting*|Oluşturulan genel tür için bu ilke türüne uygulanacak ayar. Olası değerler şunlardır,,,,,, `All` `Auto` `Excluded` `Public` `PublicAndInternal` `Required Public` `Required PublicAndInternal` ve `Required All` . Daha fazla bilgi için bkz. [çalışma zamanı yönergesi Ilke ayarları](runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Event>](event-element-net-native.md)|Bu türe ait bir olaya yansıma ilkesi uygular.|  
|[\<Field>](field-element-net-native.md)|Bu türe ait olan bir alana yansıma ilkesi uygular.|  
|[\<ImpliesType>](impliestype-element-net-native.md)|İlke, kapsayan öğe tarafından temsil edilen türe uygulanmışsa ilkeyi bir türe uygular `<TypeInstantiation>` .|  
|[\<Method>](method-element-net-native.md)|Bu türe ait bir yönteme yansıma ilkesi uygular.|  
|[\<MethodInstantiation>](methodinstantiation-element-net-native.md)|Bu türe ait oluşturulmuş bir genel metoda yansıma ilkesi uygular.|  
|[\<Property>](property-element-net-native.md)|Yansıma ilkesini bu türe ait olan bir özelliğe uygular.|  
|[\<Type>](type-element-net-native.md)|Yansıtma ilkesini iç içe bir türe uygular.|  
|`<TypeInstantiation>`|Yansıtma ilkesini, iç içe oluşturulmuş bir genel türe uygular.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Application>](application-element-net-native.md)|Uygulama genelinde türler için bir kapsayıcı görevi görür ve meta verileri çalışma zamanında yansıma için kullanılabilir olan üyeleri yazın.|  
|[\<Assembly>](assembly-element-net-native.md)|Belirtilen derlemedeki tüm türlere yansıma ilkesi uygular.|  
|[\<Library>](library-element-net-native.md)|Meta verileri çalışma zamanında yansıma için kullanılabilir olan türleri ve tür üyelerini içeren derlemeyi tanımlar.|  
|[\<Namespace>](namespace-element-net-native.md)|Bir ad alanındaki tüm türlere yansıma ilkesi uygular.|  
|[\<Type>](type-element-net-native.md)|Yansıma ilkesini bir türe ve tüm üyelerine uygular.|  
|`<TypeInstantiation>`|Oluşturulan genel türe ve tüm üyelerine yansıma ilkesi uygular.|  
  
## <a name="remarks"></a>Açıklamalar  
 Yansıma, serileştirme ve birlikte çalışma özniteliklerinin tümü isteğe bağlıdır. Ancak, en az bir tane bulunmalıdır.  
  
 Bir `<TypeInstantiation>` öğe,, veya öğesinin alt öğesi ise, [\<Assembly>](assembly-element-net-native.md) [\<Namespace>](namespace-element-net-native.md) [\<Type>](type-element-net-native.md) üst öğe tarafından tanımlanan ilke ayarlarını geçersiz kılar. Bir [\<Type>](type-element-net-native.md) öğe karşılık gelen genel tür tanımını tanımlıyorsa, `<TypeInstantiation>` öğe yalnızca belirtilen oluşturulmuş genel türün örneklendirmesiyle ilgili çalışma zamanı yansıma ilkesini geçersiz kılar.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, oluşturulmuş bir nesneden genel tür tanımını almak için yansıma kullanır <xref:System.Collections.Generic.Dictionary%602> . Ayrıca <xref:System.Type> , oluşturulan genel türleri ve genel tür tanımlarını temsil eden nesneler hakkındaki bilgileri göstermek için de yansıma kullanır. Örnekteki değişken `b` bir <xref:Windows.UI.Xaml.Controls.TextBlock> denetimdir.  
  
 [!code-csharp[ProjectN_Reflection#2](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/makegenerictype1.cs#2)]  
  
 .NET Native araç zinciri ile derlemeden sonra, örnek, yöntemi çağıran satırda bir [MissingMetadataException](missingmetadataexception-class-net-native.md) özel durumu oluşturur <xref:System.Type.GetGenericTypeDefinition%2A?displayProperty=nameWithType> . Çalışma zamanı yönergeleri dosyasına aşağıdaki öğeyi ekleyerek özel durumu ortadan kaldırabilir ve gerekli meta verileri sağlayabilirsiniz `<TypeInstantiation>` :  
  
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
