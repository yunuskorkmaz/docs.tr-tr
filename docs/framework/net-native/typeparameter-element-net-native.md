---
title: <TypeParameter> Öğesi (.NET yerel)
ms.date: 03/30/2017
ms.assetid: d37bb1b7-1ddc-4c6d-8ecf-583f804a2479
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b03c87c70fa1bfcd331f468d369632f4164300bb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61982468"
---
# <a name="typeparameter-element-net-native"></a>\<TypeParameter > öğesi (.NET yerel)
Bir yönteme geçirilen tür bağımsız değişkeni tarafından temsil edilen bir türün ilke uygulanır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<Parameter Name="parameter_name"  
           Activate="policy_type"  
           Browse="policy_type"  
           Dynamic="policy_type"  
           Serialize="policy_type"  
           DataContractSerializer="policy_type"  
           DataContractJsonSerializer="policy_type"  
           XmlSerializer="policy_type"  
           MarshalObject="policy_type"  
           MarshalDelegate="policy_type"  
           MarshalStructure="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Öznitelik türü|Açıklama|  
|---------------|--------------------|-----------------|  
|`Name`|Genel|Gerekli öznitelik. Tür parametresinin adı <xref:System.Type>. Örneğin, yöntem imzası için `Type.GetInterfaceMap(Type interfaceType)`, değerini `Name` özniteliktir "InterfaceType".|  
|`Activate`|Yansıma|İsteğe bağlı öznitelik. Oluşturucular örneklerinin etkinleştirmesi için çalışma zamanı erişimi denetler.|  
|`Browse`|Yansıma|İsteğe bağlı öznitelik. Program öğeleri hakkında bilgi için sorgulama kontrol eder, ancak herhangi bir çalışma zamanı erişim sağlamaz.|  
|`Dynamic`|Yansıma|İsteğe bağlı öznitelik. Dinamik programlama etkinleştirmek için Oluşturucular, yöntemler, alanlar, özellikler ve olaylar, tüm tür üyelerini, çalışma zamanı erişimi denetler.|  
|`Serialize`|Serileştirme|İsteğe bağlı öznitelik. Oluşturucular, alanları ve tür örnekleri sıralanabilir ve kitaplıkları gibi Newtonsoft JSON seri hale getirici tarafından serisi etkinleştirmek için özellikler, çalışma zamanı erişimi denetler.|  
|`DataContractSerializer`|Serileştirme|İsteğe bağlı öznitelik. Denetimleri İlkesi kullanan Serileştirmenin <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> sınıfı.|  
|`DataContractJsonSerializer`|Serileştirme|İsteğe bağlı öznitelik. İlke kullanan bir JSON serileştirme denetleyen <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> sınıfı.|  
|`XmlSerializer`|Serileştirme|İsteğe bağlı öznitelik. İlke kullanan bir XML serileştirme denetleyen <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> sınıfı.|  
|`MarshalObject`|Birlikte çalışma|İsteğe bağlı öznitelik. Windows çalışma zamanı ve COM başvuru türlerini hazırlama denetimleri İlkesi|  
|`MarshalDelegate`|Birlikte çalışma|İsteğe bağlı öznitelik. Yerel kod için işlev işaretçileri olarak temsilci türleri hazırlama için ilke denetler.|  
|`MarshalStructure`|Birlikte çalışma|İsteğe bağlı öznitelik. Yerel kod için değer türlerini hazırlama için ilke denetler.|  
  
## <a name="name-attribute"></a>Ad özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|*parameter_name*|Tür parametresinin adı <xref:System.Type>. Örneğin, yöntem imzası için `Type.GetInterfaceMap(Type interfaceType)`, değerini `Name` özniteliktir "InterfaceType".|  
  
## <a name="all-other-attributes"></a>Diğer tüm öznitelikler  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|*policy_setting*|Bu ilke türü için geçerli ayar. Olası değerler `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, ve `Required All`. Daha fazla bilgi için [çalışma zamanı yönerge İlkesi ayarları](../../../docs/framework/net-native/runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Yöntem >](../../../docs/framework/net-native/method-element-net-native.md)|Çalışma zamanı yansıma ilkesini yapıcıya veya yönteme için geçerlidir.|  
  
## <a name="remarks"></a>Açıklamalar  
 `<TypeParameter>` Öğesi benzer [ \<parametresi >](../../../docs/framework/net-native/parameter-element-net-native.md) BT'nin yalnızca tür parametreleri için uygulanabilir dışında öğesi <xref:System.Type>. Hangi tür çalışma zamanında tarafından belirtilen tür bağımsız değişkeni tarafından temsil edilen için ilke uygulanır `Name` özniteliği.  
  
 Örneğin, bir statik NewtonSoft JSON serileştirici içerir `JsonConvert.DeserializeObject(String value, Type type)` yöntemi. Aşağıdaki yansıma yönergeleri:  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Type Name="Newtonsoft.Json.JsonConvert" >  
      <Method Name="DeserializeObject">  
         <GenericParameter Name="type" Serialize="Required All" />  
      </Method>  
   </Type>  
</Directives>  
```  
  
 tarafından temsil edilen çalışma zamanı türü için meta verilerin belirtin `type` bağımsız değişkeni seri hale getirme için kullanılabilir hale. Bu çalışma zamanı yönergeleri aşağıdaki kaynak kodunu içeren bir projeye uygularsanız:  
  
```csharp  
Type t = typeof(StockQuote);  
Object obj = JsonConvert.DeserializeObject(data, t);  
```  
  
 Yansıma yönergeleri meta verileri oluşturmak için `StockQuote` türü NewtonSoft JSON serileştirici çalışma zamanında kullanılabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [\<Yöntem > öğesi](../../../docs/framework/net-native/method-element-net-native.md)
- [Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [Çalışma Zamanı Yönerge İlkesi Ayarları](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
- [Çalışma Zamanı Yönerge Öğeleri](../../../docs/framework/net-native/runtime-directive-elements.md)
