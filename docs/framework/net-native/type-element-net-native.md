---
title: <Type> Öğesi (.NET yerel)
ms.date: 03/30/2017
ms.assetid: 1e88d368-a886-4f1e-8eb6-6127979a9fce
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2d5541cc34f8967916e4896fd5f9be82edcb332f
ms.sourcegitcommit: 7e129d879ddb42a8b4334eee35727afe3d437952
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66051990"
---
# <a name="type-element-net-native"></a>\<Türü > öğesi (.NET yerel)
Çalışma zamanı İlkesi, bir sınıf veya yapı gibi belirli bir tür için geçerlidir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<Type Name="type_name"  
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
|`Activate`|Yansıma|İsteğe bağlı öznitelik. Oluşturucular örneklerinin etkinleştirmesi için çalışma zamanı erişimi denetler.|  
|`Browse`|Yansıma|İsteğe bağlı öznitelik. Program öğeleri hakkında bilgi için sorgulama kontrol eder, ancak herhangi bir çalışma zamanı erişim sağlamaz.|  
|`Dynamic`|Yansıma|İsteğe bağlı öznitelik. Dinamik programlama etkinleştirmek için Oluşturucular, yöntemler, alanlar, özellikler ve olaylar, tüm tür üyelerini, çalışma zamanı erişimi denetler.|  
|`Serialize`|Serileştirme|İsteğe bağlı öznitelik. Oluşturucular, alanları ve tür örnekleri sıralanabilir ve kitaplıkları gibi Newtonsoft JSON seri hale getirici tarafından serisi etkinleştirmek için özellikler, çalışma zamanı erişimi denetler.|  
|`DataContractSerializer`|Serileştirme|İsteğe bağlı öznitelik. Denetimleri İlkesi kullanan Serileştirmenin <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> sınıfı.|  
|`DataContractJsonSerializer`|Serileştirme|İsteğe bağlı öznitelik. İlke kullanan bir JSON serileştirme denetleyen <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> sınıfı.|  
|`XmlSerializer`|Serileştirme|İsteğe bağlı öznitelik. İlke kullanan bir XML serileştirme denetleyen <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> sınıfı.|  
|`MarshalObject`|Interop|İsteğe bağlı öznitelik. Windows çalışma zamanı ve COM başvuru türlerini hazırlama denetimleri İlkesi|  
|`MarshalDelegate`|Interop|İsteğe bağlı öznitelik. Yerel kod için işlev işaretçileri olarak temsilci türleri hazırlama için ilke denetler.|  
|`MarshalStructure`|Interop|İsteğe bağlı öznitelik. Yerel kod için değer türlerini hazırlama için ilke denetler.|  
  
## <a name="name-attribute"></a>Ad özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|*TYPE_NAME*|Tür adı. Bu `<Type>` ya da alt öğesi olan bir [ \<Namespace >](../../../docs/framework/net-native/namespace-element-net-native.md) öğesi ya da başka bir `<Type>` öğesi *type_name* olmadan tür adını içerebilir, ad alanı. Aksi takdirde, *type_name* tam olarak nitelenmiş tür adını içermelidir.|  
  
## <a name="all-other-attributes"></a>Diğer tüm öznitelikler  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|*policy_setting*|Bu ilke türü için geçerli ayar. Olası değerler `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, ve `Required All`. Daha fazla bilgi için [çalışma zamanı yönerge İlkesi ayarları](../../../docs/framework/net-native/runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Attributeımplies >](../../../docs/framework/net-native/attributeimplies-element-net-native.md)|Kapsayan tür bir öznitelik varsa, kod öğeleri, öznitelik uygulandığı için çalışma zamanı ilkesini tanımlar.|  
|[\<Olay >](../../../docs/framework/net-native/event-element-net-native.md)|Bu türe ait bir olay yansıma ilkesini uygular.|  
|[\<alan >](../../../docs/framework/net-native/field-element-net-native.md)|Bu türe ait bir alana yansıma ilke uygulanır.|  
|[\<GenericParameter >](../../../docs/framework/net-native/genericparameter-element-net-native.md)|İlke genel tür parametre türü için geçerlidir.|  
|[\<Impliestype >](../../../docs/framework/net-native/impliestype-element-net-native.md)|İlke içeren tarafından temsil edilen bir türün, ilkenin uygulandığı bir türe geçerlidir `<Type>` öğesi.|  
|[\<Yöntem >](../../../docs/framework/net-native/method-element-net-native.md)|Bu türe ait bir yöntem yansıma ilkesini uygular.|  
|[\<Methodınstantiation >](../../../docs/framework/net-native/methodinstantiation-element-net-native.md)|Bu türe ait oluşturulmuş bir genel yöntem yansıma ilkesini uygular.|  
|[\<Özellik >](../../../docs/framework/net-native/property-element-net-native.md)|Bu türe ait bir özellik yansıma ilkesini uygular.|  
|[\<Subtypes >](../../../docs/framework/net-native/subtypes-element-net-native.md)|Çalışma zamanı İlkesi kapsayan türden devralınan tüm sınıflar için geçerlidir.|  
|`<Type>`|Yansıma ilke iç içe türü için geçerlidir.|  
|[\<Typeınstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|Yansıma İlkesi oluşturulmuş bir genel türü için geçerlidir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Uygulama >](../../../docs/framework/net-native/application-element-net-native.md)|Birçok farklı uygulama türleri ve tür üyeleri olan meta verilerini yansıma çalışma zamanında kullanılabilir için kapsayıcı görevi görür.|  
|[\<Derleme >](../../../docs/framework/net-native/assembly-element-net-native.md)|Yansıma ilkesini belirtilen bir derlemedeki tüm türleri için geçerlidir.|  
|[\<Kitaplık >](../../../docs/framework/net-native/library-element-net-native.md)|Türler ve tür üyeleri olan meta verilerini yansıma çalışma zamanında kullanılabilir içeren derlemeyi tanımlar.|  
|[\<Namespace >](../../../docs/framework/net-native/namespace-element-net-native.md)|Yansıma ilke için bir ad alanındaki tüm türleri geçerlidir.|  
|`<Type>`|Yansıma İlkesi, bir tür ve tüm üyeleri için geçerlidir.|  
|[\<Typeınstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|Yansıma ilkesini, oluşturulmuş bir genel türü ve tüm üyeleri için geçerlidir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Yansıma, seri hale getirme ve birlikte çalışma özniteliklerini tümü isteğe bağlıdır. Hiçbiri yoksa `<Type>` eşleşen alt türleri ilkesi için tek tek üyeleri tanımlayan kapsayıcı öğe görür.  
  
 Varsa bir `<Type>` öğesi alt öğesi olan bir [ \<derleme >](../../../docs/framework/net-native/assembly-element-net-native.md), [ \<Namespace >](../../../docs/framework/net-native/namespace-element-net-native.md), `<Type>`, veya [ \< Typeınstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) öğesi üst öğe tarafından tanımlanan ilke ayarları geçersiz.  
  
 A `<Type>` genel bir türün öğesi kendi ilkesi olmayan tüm örneklemesi için ilke uygulanır. Oluşturulan genel türler, ilke tarafından tanımlanan [ \<Typeınstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) öğesi.  
  
 Tür, genel bir tür ise, adı bir Vurgu işareti sembolü sunulur (\`) genel parametreler, bir sayı. Örneğin, `Name` özniteliği bir `<Type>` öğesi için <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> sınıfı olarak görünür ``Name="System.Collections.Generic.List`1"``.
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, alanları, özellikleri ve yöntemleri hakkında bilgi görüntülemek için yansıtma kullanır. <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> sınıfı. Değişken `b` örnekte bir <xref:Windows.UI.Xaml.Controls.TextBlock> denetimi. Örneğin, yalnızca tür bilgilerini alır çünkü meta veri kullanılabilirliğini tarafından denetlenir `Browse` ilke ayarı.  
  
 [!code-csharp[ProjectN_Reflection#3](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/browsegenerictype1.cs#3)]  
  
 Çünkü meta verilerini <xref:System.Collections.Generic.List%601> sınıfı .NET Native araç zinciri tarafından otomatik olarak dahil değil, çalışma zamanında istenen üye bilgilerini görüntülemek örnek başarısız olur. Gerekli meta verilerini sağlamak için aşağıdaki ekleyin `<Type>` çalışma zamanı yönergeleri dosyasının öğesi. Bir üst sağladık, dikkat edin çünkü [< Namespace\> ](../../../docs/framework/net-native/namespace-element-net-native.md) öğesi, biz tam olarak nitelenmiş tür adları sağlamak zorunda değilsiniz `<Type>` öğesi.  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Application>  
      <Assembly Name="*Application*" Dynamic="Required All" />  
      <Namespace Name ="System.Collections.Generic" >  
        <Type Name="List`1" Browse="Required All" />   
     </Namespace>  
   </Application>  
</Directives>  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, alınacak yansıtma kullanır. bir <xref:System.Reflection.PropertyInfo> temsil eden nesne <xref:System.String.Chars%2A?displayProperty=nameWithType> özelliği. Ardından kullanır <xref:System.Reflection.PropertyInfo.GetValue%28System.Object%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> yedinci karakterinden dize değerini almak için ve tüm karakterleri dizesini görüntülemek için yöntemi. Değişken `b` örnekte bir <xref:Windows.UI.Xaml.Controls.TextBlock> denetimi.  
  
 [!code-csharp[ProjectN_Reflection#1](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/propertyinfo1.cs#1)]  
  
 Çünkü meta verilerini <xref:System.String> nesne kullanılamaz çağrısı <xref:System.Reflection.PropertyInfo.GetValue%28System.Object%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> yöntem bir <xref:System.NullReferenceException> çalıştırmada özel durum .NET yerel araç zinciriyle derlendiğinde zaman. Özel durum ortadan kaldırabilir ve gerekli meta verilerini sağlamak için aşağıdaki ekleyin `<Type>` çalışma zamanı yönergeleri dosyasının öğe:  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Application>  
    <Assembly Name="*Application*" Dynamic="Required All" />  
    <Type Name="System.String" Dynamic="Required Public"/> -->  
  </Application>  
</Directives>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [Çalışma Zamanı Yönerge Öğeleri](../../../docs/framework/net-native/runtime-directive-elements.md)
- [Çalışma Zamanı Yönerge İlkesi Ayarları](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
