---
title: '&lt;ImpliesType&gt; Öğesi (.NET Yerel)'
ms.date: 03/30/2017
ms.assetid: 3abd2071-0f28-40ba-b9a0-d52bd94cd2f6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 867a11eae14c3e7b2fb09acac5849698119e72c7
ms.sourcegitcommit: d9a0071d0fd490ae006c816f78a563b9946e269a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55065979"
---
# <a name="ltimpliestypegt-element-net-native"></a>&lt;ImpliesType&gt; Öğesi (.NET Yerel)
Bu ilke kapsayan tür veya yöntem uygulanmışsa, ilke bir türe uygulanır.  
  
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
|`Name`|Genel|Gerekli öznitelik. Tür adı belirtir.|  
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
|*TYPE_NAME*|Tür adı. Türü bu tarafından temsil edilen varsa `<ImpliesType>` öğe kapsayıcı olarak aynı ad alanında bulunan `<Type>` öğesi *type_name* kendi ad alanı olmayan bir türün adını içerebilir. Aksi takdirde, *type_name* tam olarak nitelenmiş tür adını içermelidir.|  
  
## <a name="all-other-attributes"></a>Diğer tüm öznitelikler  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|*policy_setting*|Bu ilke türü için geçerli ayar. Olası değerler `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, ve `Required All`. Daha fazla bilgi için [çalışma zamanı yönerge İlkesi ayarları](../../../docs/framework/net-native/runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<türü >](../../../docs/framework/net-native/type-element-net-native.md)|Yansıma İlkesi, bir tür ve tüm üyeleri için geçerlidir.|  
|[\<Typeınstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|Yansıma ilkesini, oluşturulmuş bir genel türü ve tüm üyeleri için geçerlidir.|  
|[\<Yöntem >](../../../docs/framework/net-native/method-element-net-native.md)|Yansıma ilkesini bir yönteme uygulanır.|  
  
## <a name="remarks"></a>Açıklamalar  
 `<ImpliesType>` Öğesi kitaplığı tarafından kullanılmak üzere öncelikli olarak tasarlanmıştır. Bunu aşağıdaki senaryoyu ele alır:  
  
-   Bir yordam bir yola yansıtacak şekilde gerekiyorsa, ikinci bir türde yansıtacak şekilde mutlaka gerekir.  
  
-   İkinci tür örtük örneklemesi için meta veriler, aksi takdirde statik analiz gerekli olduğunu göstermez için kullanılamıyor.  
  
 En yaygın olarak, iki tür paylaşılan tür bağımsız değişkenleri ile genel örnek oluşturma ' dir.  
  
 `<ImpliesType>` Öğesi kendi üst öğesi tarafından belirtilen tür yansıma gereksinimini tarafından belirtilen tür yansıma gereksinimini gelir birlikte tanımlandı `<ImpliesType>` öğesi. Örneğin, aşağıdaki yansıma yönergelerini iki türleri için geçerli `Explicit<T>` ve `Implicit<T>`.  
  
```xml  
<Type Name="Explicit{ET}">  
    <ImpliesType Name="Implicit{ET}" Dynamic="Required Public" />  
</Type>  
```  
  
 Bu yönerge sürece hiçbir etkisi olmaz örneklemesi `Explicit` tanımlanan sahip `Dynamic` ilke ayarı. Örneğin, bu durum ise, `Explicit<Int32>`, `Implicit<Int32>` kendi genel örneği üyeler kök erişim izni verilmiş ve bunların meta verilerini dinamik programlama için erişilebilir hale getirdik.  
  
 En az bir seri hale getirici için geçerlidir, gerçek bir örnek verilmiştir. Üzerinde bir yansıtma olarak belirlenmiş olan gereksinim yönergeleri yakalama `IList<` *bir şey* `>` ayrıca ilgili yansıtan içerir `List<` *bir şey* `>` herhangi bir uygulama başına ek açıklama gerektirmeden türü.  
  
```xml  
<Type Name="System.Collections.Generic.IList{T}">  
   <ImpliesType Name="System.Collections.Generic.List{T}" Serialize="Public" />  
</Type>  
```  
  
 `<ImpliesType>` Öğesi içinde de görünebilir bir `<Method>` öğesi, bazı durumlarda bir genel yöntem örnekleme yansıtan bir tür örneği oluşturmada gösterdiğinden. Örneğin, bir genel yöntem Imagine `IEnumerable<T> MakeEnumerable<T>(string spelling, T defaultValue)` belirli bir kitaplık dinamik olarak ilişkili birlikte erişecek <xref:System.Collections.Generic.List%601> ve <xref:System.Array> türleri. Bu olarak ifade edilebilir:  
  
```xml  
<Type Name="MyType">  
    <Method Name="MakeEnumerable{T}" Signature="(System.String, T)" Dynamic="Included">  
        <ImpliesType Name="T[]" Dynamic="Public" />  
        <ImpliesType Name="System.Collections.Generic.List{T}" Dynamic="Public">  
    </Method>  
</Type>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [Çalışma Zamanı Yönerge Öğeleri](../../../docs/framework/net-native/runtime-directive-elements.md)
- [Çalışma Zamanı Yönerge İlkesi Ayarları](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
