---
title: <ImpliesType>Eleman (.NET Yerel)
ms.date: 03/30/2017
ms.assetid: 3abd2071-0f28-40ba-b9a0-d52bd94cd2f6
ms.openlocfilehash: 57f4208233cd5e8544b4f1c254e3b0e0eaacd508
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181010"
---
# <a name="impliestype-element-net-native"></a>\<ImpliesType> Öğesi (.NET Yerli)
Bu ilke, içeren tür veya yönteme uygulanmışsa, bir türe ilke uygular.  
  
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
|`Activate`|Yansıma|İsteğe bağlı öznitelik. Örneklerin etkinleştirilmesini etkinleştirmek için çalışan zamanında kuruculara erişimi denetler.|  
|`Browse`|Yansıma|İsteğe bağlı öznitelik. Program öğeleri hakkında bilgi için sorgu denetimleri, ancak herhangi bir çalışma zamanı erişim etkinleştirmez.|  
|`Dynamic`|Yansıma|İsteğe bağlı öznitelik. Dinamik programlamayı etkinleştirmek için oluşturucular, yöntemler, alanlar, özellikler ve olaylar dahil olmak üzere tüm tür üyelerine çalışma zamanı erişimi denetler.|  
|`Serialize`|Serileştirme|İsteğe bağlı öznitelik. Newtonsoft JSON serileştiricisi gibi kitaplıklar tarafından seri hale getirilecek ve deserialized türü örnekleri etkinleştirmek için, yapıcılar, alanlar ve özelliklere çalışma zamanı erişimi denetler.|  
|`DataContractSerializer`|Serileştirme|İsteğe bağlı öznitelik. Sınıfı kullanan serileştirme ilkesini <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> denetler.|  
|`DataContractJsonSerializer`|Serileştirme|İsteğe bağlı öznitelik. Sınıfı kullanan JSON serileştirme <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> ilkesini denetler.|  
|`XmlSerializer`|Serileştirme|İsteğe bağlı öznitelik. Sınıfı kullanan XML serileştirme <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> ilkesini denetler.|  
|`MarshalObject`|Interop|İsteğe bağlı öznitelik. Başvuru türlerini Windows Runtime ve COM'a göre mareşalleme ilkesini denetler.|  
|`MarshalDelegate`|Interop|İsteğe bağlı öznitelik. Temsilci türlerini işlev işaretçisi olarak yerel koda göre işaretetmek için ilkeyi denetler.|  
|`MarshalStructure`|Interop|İsteğe bağlı öznitelik. Değer türlerini yerel koda göre mareşalleştirmek için ilkeyi denetler.|  
  
## <a name="name-attribute"></a>Ad özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|*Type_name*|Tür adı. Bu `<ImpliesType>` öğe tarafından temsil edilen tür, içerdiği `<Type>` öğeyle aynı ad alanında bulunuyorsa, *type_name* ad alanı olmadan türün adını içerebilir. Aksi takdirde, *type_name* tam nitelikli tür adı içermelidir.|  
  
## <a name="all-other-attributes"></a>Diğer tüm öznitelikler  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|*policy_setting*|Bu ilke türüne uygulanacak ayar. Olası değerler `All` `Auto`, `Excluded` `Public`, `PublicAndInternal` `Required Public`, `Required PublicAndInternal`, `Required All`, , , ve . Daha fazla bilgi için [Runtime Yönergesi İlke Ayarları'na](runtime-directive-policy-settings.md)bakın.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Tip>](type-element-net-native.md)|Yansıma ilkesini bir türe ve tüm üyelerine uygular.|  
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|Yapılı genel bir türe ve tüm üyelerine yansıma ilkesi uygular.|  
|[\<Yöntem>](method-element-net-native.md)|Yansıma ilkesini bir yönteme uygular.|  
  
## <a name="remarks"></a>Açıklamalar  
 Öğe `<ImpliesType>` öncelikle kitaplıklar tarafından kullanılmak üzere tasarlanmıştır. Aşağıdaki senaryoyu ele alar:  
  
- Bir yordamın bir türe yansıması gerekiyorsa, mutlaka ikinci bir türe yansıtması gerekir.  
  
- Statik çözümleme gerekli olduğunu göstermez, çünkü ikinci türün zımni anlık için meta veriler, aksi takdirde kullanılamaz.  
  
 En sık, iki tür paylaşılan türü bağımsız değişkenleri ile genel anlık vardır.  
  
 Öğe, `<ImpliesType>` üst öğesi tarafından belirtilen türüzerinde yansıma `<ImpliesType>` gereksiniminin, öğe tarafından belirtilen türüzerinde yansıma gereksinimi anlamına geldiği varsayımıyla tanımlanmıştır. Örneğin, aşağıdaki yansıma yönergeleri iki tür `Explicit<T>` için `Implicit<T>`geçerlidir ve .  
  
```xml  
<Type Name="Explicit{ET}">  
    <ImpliesType Name="Implicit{ET}" Dynamic="Required Public" />  
</Type>  
```  
  
 Tanımlı `Explicit` `Dynamic` bir ilke ayarı anlık olmadığı sürece bu yönergenin hiçbir etkisi yoktur. Örneğin, bu durumda `Explicit<Int32>`, `Implicit<Int32>` genel üyeleri köklü anında ve meta verileri dinamik programlama için erişilebilir hale getirilir.  
  
 Aşağıda, en az bir serializer için geçerli olan gerçek dünya örneği verilmiştir. Yönergeler, `IList<`bir şey olarak yazılan *bir* `>` şeyi yansıtmanın, uygulama `List<`başına ek açıklama gerektirmeden ilgili *bir şey* `>` türünü yansıtmayı da içerdiği gereksinimini yakalar.  
  
```xml  
<Type Name="System.Collections.Generic.IList{T}">  
   <ImpliesType Name="System.Collections.Generic.List{T}" Serialize="Public" />  
</Type>  
```  
  
 Bazı `<ImpliesType>` durumlarda genel bir `<Method>` yöntemin anlık olarak bir tür anlık yansıması anlamına gelir, çünkü öğe de bir öğe içinde görünebilir. Örneğin, belirli bir `IEnumerable<T> MakeEnumerable<T>(string spelling, T defaultValue)` kitaplığın ilişkili <xref:System.Collections.Generic.List%601> ve <xref:System.Array> türleri ile birlikte dinamik olarak erişeceği genel bir yöntem düşünün. Bu olarak ifade edilebilir:  
  
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
