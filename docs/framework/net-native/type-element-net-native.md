---
title: '&lt;Type&gt; Öğesi (.NET Yerel)'
ms.date: 03/30/2017
ms.assetid: 1e88d368-a886-4f1e-8eb6-6127979a9fce
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ad20cf4528f5ca7d23f80570cc34712d33b74d93
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33398085"
---
# <a name="lttypegt-element-net-native"></a>&lt;Type&gt; Öğesi (.NET Yerel)
Bir sınıf veya yapı gibi belirli türde bir çalışma zamanı ilke uygulanır.  
  
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
|`Name`|Genel|Gerekli öznitelik. Tür adını belirtir.|  
|`Activate`|Yansıma|İsteğe bağlı öznitelik. Oluşturucular örneklerinin etkinleştirmesi için çalışma zamanı erişimi kontrol eder.|  
|`Browse`|Yansıma|İsteğe bağlı öznitelik. Program öğeleri hakkında bilgi için sorgulama kontrol eder, ancak herhangi bir çalışma zamanı erişim sağlamaz.|  
|`Dynamic`|Yansıma|İsteğe bağlı öznitelik. Dinamik programlama etkinleştirmek için Oluşturucular, yöntemleri, alanları, özellikleri ve olayları dahil tüm tür üyeleri, çalışma zamanı erişimi kontrol eder.|  
|`Serialize`|Serileştirme|İsteğe bağlı öznitelik. Oluşturucular, alanları ve seri hale getirilmiş ve kitaplıklar gibi Newtonsoft JSON seri hale getirici tarafından seri türü örnekleri etkinleştirmek için özellikleri, çalışma zamanı erişimi denetler.|  
|`DataContractSerializer`|Serileştirme|İsteğe bağlı öznitelik. Denetimleri kullanan serileştirme için ilke <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> sınıfı.|  
|`DataContractJsonSerializer`|Serileştirme|İsteğe bağlı öznitelik. Denetimleri kullanan JSON serileştirmesi için ilke <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> sınıfı.|  
|`XmlSerializer`|Serileştirme|İsteğe bağlı öznitelik. Denetimleri kullanan XML serileştirme için ilke <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> sınıfı.|  
|`MarshalObject`|Birlikte çalışma|İsteğe bağlı öznitelik. Başvuru türleri Windows çalışma zamanı ve COM hazırlama denetimlerini İlkesi|  
|`MarshalDelegate`|Birlikte çalışma|İsteğe bağlı öznitelik. Yerel kod için işlev işaretçileri olarak temsilci türleri hazırlama için ilke denetler.|  
|`MarshalStructure`|Birlikte çalışma|İsteğe bağlı öznitelik. Değer türleri yerel koda hazırlama için ilke denetler.|  
  
## <a name="name-attribute"></a>Ad özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|*TYPE_NAME*|Tür adı. Bu `<Type>` ya da alt öğesi olan bir [ \<Namespace >](../../../docs/framework/net-native/namespace-element-net-native.md) öğesi veya başka bir `<Type>` öğesi, *type_name* türünün adı içerebilir, ad alanı. Aksi takdirde, *type_name* tam olarak nitelenmiş tür adını içermelidir.|  
  
## <a name="all-other-attributes"></a>Tüm diğer özniteliklerle  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|*policy_setting*|Bu ilke türü için geçerli ayar. Olası değerler şunlardır: `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, ve `Required All`. Daha fazla bilgi için bkz: [çalışma zamanı yönerge İlkesi ayarları](../../../docs/framework/net-native/runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Attributeımplies >](../../../docs/framework/net-native/attributeimplies-element-net-native.md)|Bir öznitelik içeren türde ise, öznitelik uygulandığı kod öğeleri için çalışma zamanı İlkesi tanımlar.|  
|[\<Olay >](../../../docs/framework/net-native/event-element-net-native.md)|Bu türe ait bir olay yansıma ilke uygulanır.|  
|[\<Alanı >](../../../docs/framework/net-native/field-element-net-native.md)|Bu türe ait bir alana yansıma ilke uygulanır.|  
|[\<GenericParameter >](../../../docs/framework/net-native/genericparameter-element-net-native.md)|İlke genel bir tür parametresi türü için geçerlidir.|  
|[\<Impliestype >](../../../docs/framework/net-native/impliestype-element-net-native.md)|İlke türü içeren tarafından gösterilir Bu ilkeyi uygulandığı bir türü için geçerlidir `<Type>` öğesi.|  
|[\<Yöntem >](../../../docs/framework/net-native/method-element-net-native.md)|Bu türe ait bir yöntem yansıma ilke uygulanır.|  
|[\<Methodınstantiation >](../../../docs/framework/net-native/methodinstantiation-element-net-native.md)|Bu türe ait bir oluşturulmuş genel yöntem yansıma ilke uygulanır.|  
|[\<Özellik >](../../../docs/framework/net-native/property-element-net-native.md)|Bu türe ait bir özellik yansıma ilke uygulanır.|  
|[\<Subtypes >](../../../docs/framework/net-native/subtypes-element-net-native.md)|Çalışma zamanı ilkesi içeren türünden devralınan tüm sınıflar için geçerlidir.|  
|`<Type>`|Yansıma İlkesi iç içe bir türü için geçerlidir.|  
|[\<Typeınstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|Yansıma ilke oluşturulan genel bir tür için geçerlidir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Uygulama >](../../../docs/framework/net-native/application-element-net-native.md)|Uygulama çapında türleri ve tür üyeleri olan meta verilerini yansıma çalışma zamanında yüklenebilir için kapsayıcı görevi görür.|  
|[\<derleme >](../../../docs/framework/net-native/assembly-element-net-native.md)|Belirtilen derleme içindeki tüm türler için yansıma ilke uygulanır.|  
|[\<Kitaplık >](../../../docs/framework/net-native/library-element-net-native.md)|Türleri ve tür üyeleri olan meta verilerini yansıma çalışma zamanında yüklenebilir içeren derlemenin tanımlar.|  
|[\<Namespace >](../../../docs/framework/net-native/namespace-element-net-native.md)|Bir ad alanındaki tüm türleri yansıma ilke uygulanır.|  
|`<Type>`|Yansıma ilke türü ve tüm üyeleri için geçerlidir.|  
|[\<Typeınstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|Yansıma İlkesi, yapılandırılmış bir genel tür ve tüm üyeleri için geçerlidir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Yansıma, seri hale getirme ve birlikte çalışma özniteliklerini tüm isteğe bağlıdır. Hiçbiri yoksa `<Type>` öğe olan alt türleri için ilke tanımlama tek tek üyeleri için bir kapsayıcı olarak hizmet verir.  
  
 Varsa bir `<Type>` alt öğesi olan bir [ \<derleme >](../../../docs/framework/net-native/assembly-element-net-native.md), [ \<Namespace >](../../../docs/framework/net-native/namespace-element-net-native.md), `<Type>`, veya [ \< Typeınstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) öğesi, bu geçersiz kılar üst öğesi tarafından tanımlanan ilke ayarları.  
  
 A `<Type>` genel bir tür öğesinin kendi ilke olmayan tüm örneklemesi kendi ilke uygulanır. Oluşturulan genel türler İlkesi tarafından tanımlanan [ \<Typeınstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) öğesi.  
  
 Tür genel bir tür ise adını Vurgu simge ile donatılmış (\`) sayısının üst genel parametreler tarafından izlenen. Örneğin, `Name` özniteliği bir `<Type>` öğesi için <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> sınıfı görünür olarak `Name="System.Collections.Generic.List`1"'.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, alanlar, özellikleri ve yöntemleri hakkında bilgi görüntülemek için yansıma kullanır <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> sınıfı. Değişkeni `b` örnekte bir [TextBlock](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.textblock.aspx) denetim. Örnek türü bilgileri yalnızca getireceğinden meta verilerinin kullanılabilirliği tarafından denetlenir `Browse` ilke ayarı.  
  
 [!code-csharp[ProjectN_Reflection#3](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/browsegenerictype1.cs#3)]  
  
 Çünkü meta verilerini <xref:System.Collections.Generic.List%601> sınıfı değil otomatik olarak dahil [!INCLUDE[net_native](../../../includes/net-native-md.md)] örnek araç zinciri başarısız çalışma zamanında istenen üye bilgilerini görüntülemek. Gerekli meta verilerini sağlamak için aşağıdakileri ekleyin `<Type>` çalışma zamanı yönergeleri dosyaya öğesi. Bir üst sağladık çünkü Not [< Namespace\> ](../../../docs/framework/net-native/namespace-element-net-native.md) öğesi, biz tam olarak nitelenmiş tür adları sağlamak zorunda değilsiniz `<Type>` öğesi.  
  
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
 Aşağıdaki örnek yansıma almak için kullanılır. bir <xref:System.Reflection.PropertyInfo> temsil eden nesnesi <xref:System.String.Chars%2A?displayProperty=nameWithType> özelliği. Daha sonra kullanır <xref:System.Reflection.PropertyInfo.GetValue%28System.Object%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> yöntemi bir dizedeki yedinci karakter değerini almak ve tüm karakterler dizesini görüntülemek için. Değişkeni `b` örnekte bir [TextBlock](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.textblock.aspx) denetim.  
  
 [!code-csharp[ProjectN_Reflection#1](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/propertyinfo1.cs#1)]  
  
 Olduğundan meta verilerini <xref:System.String> nesne kullanılamaz çağrısı <xref:System.Reflection.PropertyInfo.GetValue%28System.Object%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> yöntemi atar bir <xref:System.NullReferenceException> özel durum çalışma süresi ile derlendiğinde [!INCLUDE[net_native](../../../includes/net-native-md.md)] aracı zinciri. Özel durum ortadan kaldırmak ve gerekli meta verilerini sağlamak için aşağıdaki ekleyin `<Type>` çalışma zamanı yönergeleri dosya öğesine:  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Application>  
    <Assembly Name="*Application*" Dynamic="Required All" />  
    <Type Name="System.String" Dynamic="Required Public"/> -->  
  </Application>  
</Directives>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [Çalışma Zamanı Yönerge Öğeleri](../../../docs/framework/net-native/runtime-directive-elements.md)  
 [Çalışma Zamanı Yönerge İlkesi Ayarları](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
