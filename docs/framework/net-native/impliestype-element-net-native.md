---
title: <ImpliesType> öğesi (.NET Native)
ms.date: 03/30/2017
ms.assetid: 3abd2071-0f28-40ba-b9a0-d52bd94cd2f6
ms.openlocfilehash: 2f0ce1a1587e190627212cba07db298c12f4b30e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128387"
---
# <a name="impliestype-element-net-native"></a>\<ımpliestype > öğesi (.NET Native)
İlke kapsayan tür veya yönteme uygulanmışsa ilkeyi bir türe uygular.  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml
<ImpliesType Name="type_name"  
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
|`Activate`|Yansıma|İsteğe bağlı öznitelik. Örneklerin etkinleştirilmesini sağlamak için oluşturuculara çalışma zamanı erişimini denetler.|  
|`Browse`|Yansıma|İsteğe bağlı öznitelik. Program öğeleri hakkında bilgi sorgulamayı denetler, ancak hiçbir çalışma zamanı erişimini etkinleştirmez.|  
|`Dynamic`|Yansıma|İsteğe bağlı öznitelik. Dinamik programlamayı etkinleştirmek için oluşturucular, Yöntemler, alanlar, Özellikler ve olaylar dahil olmak üzere tüm tür üyelerine çalışma zamanı erişimini denetler.|  
|`Serialize`|Serileştirme|İsteğe bağlı öznitelik. Tür örneklerinin, Newtonsoft JSON serileştirici gibi kitaplıklar tarafından serileştirilmesi ve seri durumdan çıkarılmakta olması için oluşturuculara, alanlara ve özelliklere çalışma zamanı erişimini denetler.|  
|`DataContractSerializer`|Serileştirme|İsteğe bağlı öznitelik. <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> sınıfını kullanan serileştirme için ilkeyi denetler.|  
|`DataContractJsonSerializer`|Serileştirme|İsteğe bağlı öznitelik. <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> sınıfını kullanan JSON serileştirme için ilkeyi denetler.|  
|`XmlSerializer`|Serileştirme|İsteğe bağlı öznitelik. <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> sınıfını kullanan XML serileştirme ilkesini denetler.|  
|`MarshalObject`|Interop|İsteğe bağlı öznitelik. Windows Çalışma Zamanı ve COM 'a başvuru türlerini hazırlama ilkesini denetler.|  
|`MarshalDelegate`|Interop|İsteğe bağlı öznitelik. Temsilci türlerini yerel koda işlev işaretçileri olarak hazırlama ilkesini denetler.|  
|`MarshalStructure`|Interop|İsteğe bağlı öznitelik. Değer türlerini yerel koda hazırlama ilkesini denetler.|  
  
## <a name="name-attribute"></a>Ad özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|*type_name*|Tür adı. Bu `<ImpliesType>` öğesi tarafından temsil edilen tür, kendisini içeren `<Type>` öğesiyle aynı ad alanında bulunuyorsa, *type_name* ad alanı olmadan türün adını içerebilir. Aksi halde, *type_name* tam nitelikli tür adını içermelidir.|  
  
## <a name="all-other-attributes"></a>Diğer tüm öznitelikler  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|*policy_setting*|Bu ilke türüne uygulanacak ayar. Olası değerler şunlardır `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`ve `Required All`. Daha fazla bilgi için bkz. [çalışma zamanı yönergesi Ilke ayarları](runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<türü >](type-element-net-native.md)|Yansıma ilkesini bir türe ve tüm üyelerine uygular.|  
|[\<Typeörneklemesi >](typeinstantiation-element-net-native.md)|Oluşturulan genel türe ve tüm üyelerine yansıma ilkesi uygular.|  
|[\<yöntemi >](method-element-net-native.md)|Bir yönteme yansıma ilkesi uygular.|  
  
## <a name="remarks"></a>Açıklamalar  
 `<ImpliesType>` öğesi öncelikle kitaplıklar tarafından kullanılmak üzere tasarlanmıştır. Aşağıdaki senaryoyu ele alınmaktadır:  
  
- Bir yordamın bir tür üzerinde yansıtılması gerekiyorsa, ikinci bir tür üzerinde yansıtılması gerekir.  
  
- Statik analiz bunun gerekli olduğunu belirtmediği için, ikinci türün örtük olarak belirtilen örneklenmesi için meta veriler kullanılamaz durumda değildir.  
  
 En yaygın olarak, iki tür paylaşılan tür bağımsız değişkenleriyle genel örneklemelerdir.  
  
 `<ImpliesType>` öğesi, kendi üst öğesi tarafından belirtilen türde yansıma için ihtiyacı olan ve `<ImpliesType>` öğesi tarafından belirtilen türde yansıma gereksinimini ifade eden varsayımıyla tanımlanmıştır. Örneğin, aşağıdaki yansıma yönergeleri iki tür için geçerlidir `Explicit<T>` ve `Implicit<T>`.  
  
```xml  
<Type Name="Explicit{ET}">  
    <ImpliesType Name="Implicit{ET}" Dynamic="Required Public" />  
</Type>  
```  
  
 `Explicit` örneklemesinin tanımlanmış bir `Dynamic` ilkesi ayarı yoksa, bu yönergenin etkisi yoktur. Örneğin, bu durum `Explicit<Int32>`için ise, `Implicit<Int32>` ortak üyeleri kök olarak oluşturulur ve meta verileri dinamik programlama için erişilebilir hale getirilir.  
  
 Aşağıda, en az bir seri hale getirici için geçerli olan gerçek dünyada bir örnek verilmiştir. Yönergeler *`IList<`olarak yazılmış bir şeyi yansıtan* gereksinimi yakalar`>` aynı zamanda ilgili `List<`herhangi bir uygulama için gerekli olmadan`>` *bir* tür üzerinde yansıtılıyor ek açıklama.  
  
```xml  
<Type Name="System.Collections.Generic.IList{T}">  
   <ImpliesType Name="System.Collections.Generic.List{T}" Serialize="Public" />  
</Type>  
```  
  
 `<ImpliesType>` öğesi, bir `<Method>` öğesi içinde de görünebilir, çünkü bazı durumlarda genel bir yöntemi örneklemede bir tür örneklemesi yansıtılıyor olması gerekir. Örneğin, belirli bir kitaplığın ilişkili <xref:System.Collections.Generic.List%601> ve <xref:System.Array> türleriyle birlikte dinamik olarak erişdiğinin `IEnumerable<T> MakeEnumerable<T>(string spelling, T defaultValue)` genel bir yöntem düşünün. Bu, şöyle ifade edilebilir:  
  
```xml  
<Type Name="MyType">  
    <Method Name="MakeEnumerable{T}" Signature="(System.String, T)" Dynamic="Included">  
        <ImpliesType Name="T[]" Dynamic="Public" />  
        <ImpliesType Name="System.Collections.Generic.List{T}" Dynamic="Public" />  
    </Method>  
</Type>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu](runtime-directives-rd-xml-configuration-file-reference.md)
- [Çalışma Zamanı Yönerge Öğeleri](runtime-directive-elements.md)
- [Çalışma Zamanı Yönerge İlkesi Ayarları](runtime-directive-policy-settings.md)
