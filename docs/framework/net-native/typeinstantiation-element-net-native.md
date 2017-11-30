---
title: "&lt;TypeInstantiation&gt; Öğesi (.NET Yerel)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a5eada64-075b-4162-9655-ded84e4681f2
caps.latest.revision: "21"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 442970c8253147313a38e1a1518219a96ec41945
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="lttypeinstantiationgt-element-net-native"></a>&lt;TypeInstantiation&gt; Öğesi (.NET Yerel)
Çalışma zamanı yansıma İlkesi oluşturulmuş bir genel türü için geçerlidir.  
  
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
|`Arguments`|Genel|Gerekli öznitelik. Genel tür bağımsız değişkenleri belirtir. Birden fazla bağımsız değişken varsa, bunların virgülle ayrılır.|  
|`Activate`|Yansıma|İsteğe bağlı öznitelik. Oluşturucular örneklerinin etkinleştirmesi için çalışma zamanı erişimi kontrol eder.|  
|`Browse`|Yansıma|İsteğe bağlı öznitelik. Program öğeleri hakkında bilgi için sorgulama kontrol eder, ancak herhangi bir çalışma zamanı erişim sağlamaz.|  
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
|*TYPE_NAME*|Tür adı. Bu `<TypeInstantiation>` alt öğesi olan bir [ \<Namespace >](../../../docs/framework/net-native/namespace-element-net-native.md) öğesi, bir [ \<türü >](../../../docs/framework/net-native/type-element-net-native.md) öğesi veya başka bir `<TypeInstantiation>` öğesi, *type_ ad* kendi ad olmadan türünün adı belirtebilirsiniz. Aksi takdirde, *type_name* tam olarak nitelenmiş tür adını içermelidir. Tür adı donatılmış değil. Örneğin, bir <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> nesnesi `<TypeInstantiation>` öğesi şu şekilde görünebilir:<br /><br /> `\<TypeInstantiation Name=System.Collections.Generic.List Dynamic="Required Public" />`|  
  
## <a name="arguments-attribute"></a>Bağımsız değişkenler özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|*type_argument*|Genel tür bağımsız değişkenleri belirtir. Birden fazla bağımsız değişken varsa, bunların virgülle ayrılır. Her bağımsız değişken tam olarak nitelenmiş tür adını oluşmalıdır.|  
  
## <a name="all-other-attributes"></a>Tüm diğer özniteliklerle  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|*policy_setting*|Oluşturulan genel tür için bu ilke türü için geçerli ayar. Olası değerler şunlardır: `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, ve `Required All`. Daha fazla bilgi için bkz: [çalışma zamanı yönerge İlkesi ayarları](../../../docs/framework/net-native/runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Olay >](../../../docs/framework/net-native/event-element-net-native.md)|Bu türe ait bir olay yansıma ilke uygulanır.|  
|[\<Alanı >](../../../docs/framework/net-native/field-element-net-native.md)|Bu türe ait bir alana yansıma ilke uygulanır.|  
|[\<Impliestype >](../../../docs/framework/net-native/impliestype-element-net-native.md)|İlke türü içeren tarafından gösterilir Bu ilkeyi uygulandığı bir türü için geçerlidir `<TypeInstantiation>` öğesi.|  
|[\<Yöntem >](../../../docs/framework/net-native/method-element-net-native.md)|Bu türe ait bir yöntem yansıma ilke uygulanır.|  
|[\<Methodınstantiation >](../../../docs/framework/net-native/methodinstantiation-element-net-native.md)|Bu türe ait bir oluşturulmuş genel yöntem yansıma ilke uygulanır.|  
|[\<Özellik >](../../../docs/framework/net-native/property-element-net-native.md)|Bu türe ait bir özellik yansıma ilke uygulanır.|  
|[\<Türü >](../../../docs/framework/net-native/type-element-net-native.md)|Yansıma İlkesi iç içe bir türü için geçerlidir.|  
|`<TypeInstantiation>`|Yansıma İlkesi iç içe geçmiş bir oluşturulmuş genel türü için geçerlidir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Uygulama >](../../../docs/framework/net-native/application-element-net-native.md)|Uygulama çapında türleri ve tür üyeleri olan meta verilerini yansıma çalışma zamanında yüklenebilir için kapsayıcı görevi görür.|  
|[\<Derleme >](../../../docs/framework/net-native/assembly-element-net-native.md)|Belirtilen derleme içindeki tüm türler için yansıma ilke uygulanır.|  
|[\<Kitaplık >](../../../docs/framework/net-native/library-element-net-native.md)|Türleri ve tür üyeleri olan meta verilerini yansıma çalışma zamanında yüklenebilir içeren derlemenin tanımlar.|  
|[\<Namespace >](../../../docs/framework/net-native/namespace-element-net-native.md)|Bir ad alanındaki tüm türleri yansıma ilke uygulanır.|  
|[\<Türü >](../../../docs/framework/net-native/type-element-net-native.md)|Yansıma ilke türü ve tüm üyeleri için geçerlidir.|  
|`<TypeInstantiation>`|Yansıma İlkesi, yapılandırılmış bir genel tür ve tüm üyeleri için geçerlidir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Yansıma, seri hale getirme ve birlikte çalışma özniteliklerini tüm isteğe bağlıdır. Ancak, en az birinin mevcut olması gerekir.  
  
 Varsa bir `<TypeInstantiation>` alt öğesi olan bir [ \<derleme >](../../../docs/framework/net-native/assembly-element-net-native.md), [ \<Namespace >](../../../docs/framework/net-native/namespace-element-net-native.md), veya [ \<türü >](../../../docs/framework/net-native/type-element-net-native.md), öğesi Bu üst öğesi tarafından tanımlanan ilke ayarları geçersiz kılar. Varsa bir [ \<türü >](../../../docs/framework/net-native/type-element-net-native.md) öğesi tanımlar karşılık gelen bir genel tür tanımında `<TypeInstantiation>` öğesi yalnızca belirtilen oluşturulan genel türde örneklemesi için çalışma zamanı yansıma ilkesini geçersiz kılar.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, genel tür tanımında oluşturulan almak için yansıma kullanır <xref:System.Collections.Generic.Dictionary%602> nesnesi. Hakkında bilgi görüntülemek için de kullanır yansıma <xref:System.Type> oluşturulan genel türler ve genel tür tanımları temsil eden nesneler. Değişkeni `b` örnekte bir [TextBlock](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.textblock.aspx) denetim.  
  
 [!code-csharp[ProjectN_Reflection#2](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/makegenerictype1.cs#2)]  
  
 Derleme ile sonra [!INCLUDE[net_native](../../../includes/net-native-md.md)] örnek araç zinciri oluşturur bir [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) özel durum çağrı satırında <xref:System.Type.GetGenericTypeDefinition%2A?displayProperty=nameWithType> yöntemi. Özel durum ortadan kaldırmak ve aşağıdaki ekleyerek gerekli meta verilerini sağlamak `<TypeInstantiation>` çalışma zamanı yönergeleri dosya öğesine:  
  
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
 [Çalışma zamanı yönergeleri (rd.xml) yapılandırma dosyası başvurusu](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [Çalışma zamanı yönerge öğeleri](../../../docs/framework/net-native/runtime-directive-elements.md)  
 [Çalışma zamanı yönerge İlkesi ayarları](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
