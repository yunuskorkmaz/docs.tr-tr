---
title: '&lt;TypeInstantiation&gt; Öğesi (.NET Yerel)'
ms.date: 03/30/2017
ms.assetid: a5eada64-075b-4162-9655-ded84e4681f2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5277b056c11de4c3e32d33c72bafc8f64ee17d05
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53154837"
---
# <a name="lttypeinstantiationgt-element-net-native"></a>&lt;TypeInstantiation&gt; Öğesi (.NET Yerel)
Çalışma zamanı yansıma ilkesini oluşturulmuş bir genel türü için geçerlidir.  
  
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
|`Name`|Genel|Gerekli öznitelik. Tür adı belirtir.|  
|`Arguments`|Genel|Gerekli öznitelik. Genel tür bağımsız değişkenlerini belirtir. Birden çok bağımsız değişkeni varsa, bunların virgülle ayrılır.|  
|`Activate`|Yansıma|İsteğe bağlı öznitelik. Oluşturucular örneklerinin etkinleştirmesi için çalışma zamanı erişimi denetler.|  
|`Browse`|Yansıma|İsteğe bağlı öznitelik. Program öğeleri hakkında bilgi için sorgulama kontrol eder, ancak herhangi bir çalışma zamanı erişim sağlamaz.|  
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
|*TYPE_NAME*|Tür adı. Bu `<TypeInstantiation>` öğesi alt öğesi olan bir [ \<Namespace >](../../../docs/framework/net-native/namespace-element-net-native.md) öğesi, bir [ \<türü >](../../../docs/framework/net-native/type-element-net-native.md) öğesi veya başka bir `<TypeInstantiation>` öğesi *type_ adı* kendi ad alanı olmayan bir türün adını belirtebilirsiniz. Aksi takdirde, *type_name* tam olarak nitelenmiş tür adını içermelidir. Tür adı düzenlenmiş değil. Örneğin, bir <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> nesnesi `<TypeInstantiation>` öğesi şu şekilde görünebilir:<br /><br /> `\<TypeInstantiation Name=System.Collections.Generic.List Dynamic="Required Public" />`|  
  
## <a name="arguments-attribute"></a>Bağımsız değişkenler özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|*type_argument*|Genel tür bağımsız değişkenlerini belirtir. Birden çok bağımsız değişkeni varsa, bunların virgülle ayrılır. Her bağımsız değişken tam olarak nitelenmiş tür adını oluşmalıdır.|  
  
## <a name="all-other-attributes"></a>Diğer tüm öznitelikler  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|*policy_setting*|Bu ilke türü için oluşturulmuş bir genel türü için geçerli ayar. Olası değerler `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, ve `Required All`. Daha fazla bilgi için [çalışma zamanı yönerge İlkesi ayarları](../../../docs/framework/net-native/runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Olay >](../../../docs/framework/net-native/event-element-net-native.md)|Bu türe ait bir olay yansıma ilkesini uygular.|  
|[\<alan >](../../../docs/framework/net-native/field-element-net-native.md)|Bu türe ait bir alana yansıma ilke uygulanır.|  
|[\<Impliestype >](../../../docs/framework/net-native/impliestype-element-net-native.md)|İlke içeren tarafından temsil edilen bir türün, ilkenin uygulandığı bir türe geçerlidir `<TypeInstantiation>` öğesi.|  
|[\<Yöntem >](../../../docs/framework/net-native/method-element-net-native.md)|Bu türe ait bir yöntem yansıma ilkesini uygular.|  
|[\<Methodınstantiation >](../../../docs/framework/net-native/methodinstantiation-element-net-native.md)|Bu türe ait oluşturulmuş bir genel yöntem yansıma ilkesini uygular.|  
|[\<Özellik >](../../../docs/framework/net-native/property-element-net-native.md)|Bu türe ait bir özellik yansıma ilkesini uygular.|  
|[\<türü >](../../../docs/framework/net-native/type-element-net-native.md)|Yansıma ilke iç içe türü için geçerlidir.|  
|`<TypeInstantiation>`|Yansıma ilke iç içe geçmiş oluşturulan genel tür için geçerlidir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Uygulama >](../../../docs/framework/net-native/application-element-net-native.md)|Birçok farklı uygulama türleri ve tür üyeleri olan meta verilerini yansıma çalışma zamanında kullanılabilir için kapsayıcı görevi görür.|  
|[\<Derleme >](../../../docs/framework/net-native/assembly-element-net-native.md)|Yansıma ilkesini belirtilen bir derlemedeki tüm türleri için geçerlidir.|  
|[\<Kitaplık >](../../../docs/framework/net-native/library-element-net-native.md)|Türler ve tür üyeleri olan meta verilerini yansıma çalışma zamanında kullanılabilir içeren derlemeyi tanımlar.|  
|[\<Namespace >](../../../docs/framework/net-native/namespace-element-net-native.md)|Yansıma ilke için bir ad alanındaki tüm türleri geçerlidir.|  
|[\<türü >](../../../docs/framework/net-native/type-element-net-native.md)|Yansıma İlkesi, bir tür ve tüm üyeleri için geçerlidir.|  
|`<TypeInstantiation>`|Yansıma ilkesini, oluşturulmuş bir genel türü ve tüm üyeleri için geçerlidir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Yansıma, seri hale getirme ve birlikte çalışma özniteliklerini tümü isteğe bağlıdır. Ancak, en az biri mevcut olmalıdır.  
  
 Varsa bir `<TypeInstantiation>` öğesi alt öğesi olan bir [ \<derleme >](../../../docs/framework/net-native/assembly-element-net-native.md), [ \<Namespace >](../../../docs/framework/net-native/namespace-element-net-native.md), veya [ \<türü >](../../../docs/framework/net-native/type-element-net-native.md), öğesi Bu, üst öğe tarafından tanımlanan ilke ayarları geçersiz kılar. Varsa bir [ \<türü >](../../../docs/framework/net-native/type-element-net-native.md) öğe tanımlar karşılık gelen bir genel tür tanımı `<TypeInstantiation>` öğesini belirtilen oluşturulan genel tür örneklemeleri için yalnızca çalışma zamanı yansıma ilkesini geçersiz kılar.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, genel tür tanımı oluşturulan almak için yansıtma kullanır. <xref:System.Collections.Generic.Dictionary%602> nesne. Hakkında bilgi görüntülemek için de kullanır yansıma <xref:System.Type> oluşturulan genel türler ve genel tür tanımları temsil eden nesneleri. Değişken `b` örnekte bir <xref:Windows.UI.Xaml.Controls.TextBlock> denetimi.  
  
 [!code-csharp[ProjectN_Reflection#2](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/makegenerictype1.cs#2)]  
  
 Derleme ile sonra [!INCLUDE[net_native](../../../includes/net-native-md.md)] örnek araç zinciri oluşturur bir [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) özel durumu çağıran satırında <xref:System.Type.GetGenericTypeDefinition%2A?displayProperty=nameWithType> yöntemi. Özel durum ortadan kaldırır ve aşağıdakileri ekleyerek gerekli meta verileri belirtin `<TypeInstantiation>` çalışma zamanı yönergeleri dosyasının öğe:  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [Çalışma Zamanı Yönerge Öğeleri](../../../docs/framework/net-native/runtime-directive-elements.md)  
 [Çalışma Zamanı Yönerge İlkesi Ayarları](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
