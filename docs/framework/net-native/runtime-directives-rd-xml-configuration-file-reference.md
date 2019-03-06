---
title: Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu
ms.date: 03/30/2017
ms.assetid: 8241523f-d8e1-4fb6-bf6a-b29bfe07b38a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f8314f34f9fe0be43e7371d29cb4b366a819807c
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57356110"
---
# <a name="runtime-directives-rdxml-configuration-file-reference"></a>Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu

Bir çalışma zamanı yönergeleri (. rd.xml) belirtilen program öğelerini yansıma için kullanılabilir olup olmadığını belirten bir XML yapılandırma dosyasını bir dosyadır. Bir çalışma zamanı yönergeleri dosyasının bir örnek aşağıda verilmiştir:

```xml
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">
<Application>
  <Namespace Name="Contoso.Cloud.AppServices" Serialize="Required Public" />
  <Namespace Name="ContosoClient.ViewModels" Serialize="Required Public" />
  <Namespace Name="ContosoClient.DataModel" Serialize="Required Public" />
  <Namespace Name="Contoso.Reader.UtilityLib" Serialize="Required Public" />

  <Namespace Name="System.Collections.ObjectModel" >
    <TypeInstantiation Name="ObservableCollection"
          Arguments="ContosoClient.DataModel.ProductItem" Serialize="Public" />
    <TypeInstantiation Name="ReadOnlyObservableCollection"
          Arguments="ContosoClient.DataModel.ProductGroup" Serialize="Public" />
  </Namespace>
</Application>
</Directives>
```

## <a name="the-structure-of-a-runtime-directives-file"></a>Bir çalışma zamanı yönergeleri dosyasının yapısı

Çalışma zamanı yönergeleri kullanan dosya `http://schemas.microsoft.com/netfx/2013/01/metadata` ad alanı.

Kök öğe [yönergeleri](../../../docs/framework/net-native/directives-element-net-native.md) öğesi. Sıfır veya daha fazla içerebilir [Kitaplığı](../../../docs/framework/net-native/library-element-net-native.md) öğeleri ve sıfır veya bir [uygulama](../../../docs/framework/net-native/application-element-net-native.md) aşağıdaki yapı gösterildiği öğesi. Özniteliklerini [uygulama](../../../docs/framework/net-native/application-element-net-native.md) öğesi, birçok farklı uygulama çalışma zamanı yansıma ilkesini tanımlayabilir veya alt öğeleri için bir kapsayıcı olarak hizmet verebilir. [Kitaplığı](../../../docs/framework/net-native/library-element-net-native.md) ögesi, diğer taraftan, yalnızca bir kapsayıcıdır. Alt [uygulama](../../../docs/framework/net-native/application-element-net-native.md) ve [Kitaplığı](../../../docs/framework/net-native/library-element-net-native.md) öğe türleri, yöntemleri, alanları, özellikleri ve yansıma için kullanılabilir olan olayları tanımlayın.

Başvuru bilgileri için aşağıdaki yapısından öğeleri seçin veya bakın [çalışma zamanı yönerge öğeleri](../../../docs/framework/net-native/runtime-directive-elements.md). Aşağıdaki hiyerarşi içinde özyinelemeli yapının nokta işaretler. Bu öğe isteğe bağlı veya gerekli olup ve varsa kullanılır, köşeli ayraçlar içindeki bilgileri gösterir (bir veya daha çok) kaç örneğinin izin verilir.

[Yönergeleri](../../../docs/framework/net-native/directives-element-net-native.md) 1:1 [uygulama](../../../docs/framework/net-native/application-element-net-native.md) [0:1] [derleme](../../../docs/framework/net-native/assembly-element-net-native.md) [0:M] [Namespace](../../../docs/framework/net-native/namespace-element-net-native.md) [0:M]. biçimindeki telefon numarasıdır. biçimindeki telefon numarasıdır.
[Tür](../../../docs/framework/net-native/type-element-net-native.md) [0:M]. biçimindeki telefon numarasıdır. biçimindeki telefon numarasıdır.
[Typeınstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (genel tür oluşturulan) [0:M]. biçimindeki telefon numarasıdır. biçimindeki telefon numarasıdır.
[Namespace](../../../docs/framework/net-native/namespace-element-net-native.md) [0:M] [Namespace](../../../docs/framework/net-native/namespace-element-net-native.md) [0:M]. biçimindeki telefon numarasıdır. biçimindeki telefon numarasıdır.
[Tür](../../../docs/framework/net-native/type-element-net-native.md) [0:M]. biçimindeki telefon numarasıdır. biçimindeki telefon numarasıdır.
[Typeınstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (genel tür oluşturulan) [0:M]. biçimindeki telefon numarasıdır. biçimindeki telefon numarasıdır.
[Tür](../../../docs/framework/net-native/type-element-net-native.md) [0:M] [Subtypes](../../../docs/framework/net-native/subtypes-element-net-native.md) (kapsayan tür alt sınıflarını) [O:1] [türü](../../../docs/framework/net-native/type-element-net-native.md) [0:M]. biçimindeki telefon numarasıdır. biçimindeki telefon numarasıdır.
[Typeınstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (genel tür oluşturulan) [0:M]. biçimindeki telefon numarasıdır. biçimindeki telefon numarasıdır.
[Attributeımplies](../../../docs/framework/net-native/attributeimplies-element-net-native.md) (öznitelik değer türü içeren) [O:1] [GenericParameter](../../../docs/framework/net-native/genericparameter-element-net-native.md) [0:M] [yöntemi](../../../docs/framework/net-native/method-element-net-native.md) [0:M] [parametre](../../../docs/framework/net-native/parameter-element-net-native.md) [0:M] [ TypeParameter](../../../docs/framework/net-native/typeparameter-element-net-native.md) [0:M] [GenericParameter](../../../docs/framework/net-native/genericparameter-element-net-native.md) [0:M] [Methodınstantiation](../../../docs/framework/net-native/methodinstantiation-element-net-native.md) (genel yöntem oluşturulmuş) [0:M] [özelliği](../../../docs/framework/net-native/property-element-net-native.md) [0:M] [Alan](../../../docs/framework/net-native/field-element-net-native.md) [0:M] [olay](../../../docs/framework/net-native/event-element-net-native.md) [0:M] [Typeınstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (genel tür oluşturulan) [0:M] [türü](../../../docs/framework/net-native/type-element-net-native.md) [0:M]. biçimindeki telefon numarasıdır. biçimindeki telefon numarasıdır.
[Typeınstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (genel tür oluşturulan) [0:M]. biçimindeki telefon numarasıdır. biçimindeki telefon numarasıdır.
[Yöntemi](../../../docs/framework/net-native/method-element-net-native.md) [0:M] [parametre](../../../docs/framework/net-native/parameter-element-net-native.md) [0:M] [TypeParameter](../../../docs/framework/net-native/typeparameter-element-net-native.md) [0:M] [GenericParameter](../../../docs/framework/net-native/genericparameter-element-net-native.md) [0:M] [Methodınstantiation](../../../docs/framework/net-native/methodinstantiation-element-net-native.md) () genel yöntem oluşturulmuş) [0:M] [özelliği](../../../docs/framework/net-native/property-element-net-native.md) [0:M] [alan](../../../docs/framework/net-native/field-element-net-native.md) [0:M] [olay](../../../docs/framework/net-native/event-element-net-native.md) [0:M] [Kitaplığı](../../../docs/framework/net-native/library-element-net-native.md) [0:M] [Derleme](../../../docs/framework/net-native/assembly-element-net-native.md) [0:M] [Namespace](../../../docs/framework/net-native/namespace-element-net-native.md) [0:M]. biçimindeki telefon numarasıdır. biçimindeki telefon numarasıdır.
[Tür](../../../docs/framework/net-native/type-element-net-native.md) [0:M]. biçimindeki telefon numarasıdır. biçimindeki telefon numarasıdır.
[Typeınstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (genel tür oluşturulan) [0:M]. biçimindeki telefon numarasıdır. biçimindeki telefon numarasıdır.
[Namespace](../../../docs/framework/net-native/namespace-element-net-native.md) [0:M] [Namespace](../../../docs/framework/net-native/namespace-element-net-native.md) [0:M]. biçimindeki telefon numarasıdır. biçimindeki telefon numarasıdır.
[Tür](../../../docs/framework/net-native/type-element-net-native.md) [0:M]. biçimindeki telefon numarasıdır. biçimindeki telefon numarasıdır.
[Typeınstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (genel tür oluşturulan) [0:M]. biçimindeki telefon numarasıdır. biçimindeki telefon numarasıdır.
[Tür](../../../docs/framework/net-native/type-element-net-native.md) [0:M] [Subtypes](../../../docs/framework/net-native/subtypes-element-net-native.md) (kapsayan tür alt sınıflarını) [O:1] [türü](../../../docs/framework/net-native/type-element-net-native.md) [0:M]. biçimindeki telefon numarasıdır. biçimindeki telefon numarasıdır.
[Typeınstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (genel tür oluşturulan) [0:M]. biçimindeki telefon numarasıdır. biçimindeki telefon numarasıdır.
[Attributeımplies](../../../docs/framework/net-native/attributeimplies-element-net-native.md) (öznitelik değer türü içeren) [O:1] [GenericParameter](../../../docs/framework/net-native/genericparameter-element-net-native.md) [0:M] [yöntemi](../../../docs/framework/net-native/method-element-net-native.md) [0:M] [Methodınstantiation](../../../docs/framework/net-native/methodinstantiation-element-net-native.md) (oluşturulmuş genel yöntem) [0:M] [özelliği](../../../docs/framework/net-native/property-element-net-native.md) [0:M] [alan](../../../docs/framework/net-native/field-element-net-native.md) [0:M] [olay](../../../docs/framework/net-native/event-element-net-native.md) [0:M] [Typeınstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (genel tür oluşturulan) [0: M] [türü](../../../docs/framework/net-native/type-element-net-native.md) [0:M]. biçimindeki telefon numarasıdır. biçimindeki telefon numarasıdır.
[Typeınstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (genel tür oluşturulan) [0:M]. biçimindeki telefon numarasıdır. biçimindeki telefon numarasıdır.
[Yöntemi](../../../docs/framework/net-native/method-element-net-native.md) [0:M] [Methodınstantiation](../../../docs/framework/net-native/methodinstantiation-element-net-native.md) (genel yöntem oluşturulmuş) [0:M] [özelliği](../../../docs/framework/net-native/property-element-net-native.md) [0:M] [alan](../../../docs/framework/net-native/field-element-net-native.md) [0:M] [olay](../../../docs/framework/net-native/event-element-net-native.md)[0:M]

[Uygulama](../../../docs/framework/net-native/application-element-net-native.md) öğesi hiçbir öznitelik olabilir ya da ele İlkesi özniteliklerini olabilir [çalışma zamanı yönerge ve ilke bölümünden](#Directives).

A [Kitaplığı](../../../docs/framework/net-native/library-element-net-native.md) öğeye sahip tek bir öznitelik `Name`, bir kitaplığı veya dosya uzantısı olmadan, derleme adını belirtir. Örneğin, aşağıdaki [Kitaplığı](../../../docs/framework/net-native/library-element-net-native.md) öğesi Extensions.dll adlı bir derleme için geçerlidir.

```xml
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">
  <Application>
     <!-- Child elements go here -->
  </Application>
  <Library Name="Extensions">
     <!-- Child elements go here -->
  </Library>
</Directives>
```

<a name="Directives"></a>

## <a name="runtime-directives-and-policy"></a>Çalışma zamanı yönergeleri ve ilke

[Uygulama](../../../docs/framework/net-native/application-element-net-native.md) öğenin kendisinin ve alt öğelerinin [Kitaplığı](../../../docs/framework/net-native/library-element-net-native.md) ve [uygulama](../../../docs/framework/net-native/application-element-net-native.md) öğeleri ilke express; diğer bir deyişle, bunlar uygulama uygulayabileceğiniz şekilde tanımlayın Yansıma bir program öğesi için. Öğesinin bir öznitelik tarafından tanımlanan ilke türü (örneğin, `Serialize`). İlke değeri özniteliğin değerine göre tanımlanır (örneğin, `Serialize="Required"`).

Bir öğenin özniteliği tarafından belirtilen herhangi bir ilke, bu ilke için bir değer belirtmezseniz tüm alt öğeleri için geçerlidir. Örneğin, bir ilke tarafından belirtilen bir [türü](../../../docs/framework/net-native/type-element-net-native.md) ögesi ilke içerdiği tüm türleri ve üyeleri için bir ilke açıkça belirtilmediği için geçerlidir.

Tarafından ifade ilke [uygulama](../../../docs/framework/net-native/application-element-net-native.md), [derleme](../../../docs/framework/net-native/assembly-element-net-native.md), [Attributeımplies](../../../docs/framework/net-native/attributeimplies-element-net-native.md), [Namespace](../../../docs/framework/net-native/namespace-element-net-native.md), [ Subtypes](../../../docs/framework/net-native/subtypes-element-net-native.md), ve [türü](../../../docs/framework/net-native/type-element-net-native.md) öğeleri tek tek üyeleri için ifade ilke farklıdır (tarafından [yöntemi](../../../docs/framework/net-native/method-element-net-native.md), [özelliği](../../../docs/framework/net-native/property-element-net-native.md), [Alan](../../../docs/framework/net-native/field-element-net-native.md), ve [olay](../../../docs/framework/net-native/event-element-net-native.md) öğeleri).

### <a name="specifying-policy-for-assemblies-namespaces-and-types"></a>Derlemeler, ad alanları ve türler için ilkesini belirtme

[Uygulama](../../../docs/framework/net-native/application-element-net-native.md), [derleme](../../../docs/framework/net-native/assembly-element-net-native.md), [Attributeımplies](../../../docs/framework/net-native/attributeimplies-element-net-native.md), [Namespace](../../../docs/framework/net-native/namespace-element-net-native.md), [Subtypes](../../../docs/framework/net-native/subtypes-element-net-native.md)ve [ Tür](../../../docs/framework/net-native/type-element-net-native.md) öğeleri aşağıdaki ilke türlerinden destekler:

- `Activate`. örneklerinin etkinleştirmesi için oluşturucuları, çalışma zamanı erişimi denetler.

- `Browse`. Program öğeleri hakkında bilgi için sorgulama denetler, ancak herhangi bir çalışma zamanı erişim sağlamaz.

- `Dynamic`. Dinamik programlama etkinleştirmek için Oluşturucular, yöntemler, alanlar, özellikler ve olaylar, tüm tür üyelerini, çalışma zamanı erişimi denetler.

- `Serialize`. Oluşturucular, alanları ve tür örnekleri sıralanabilir ve üçüncü taraf kitaplıklar gibi Newtonsoft JSON seri hale getirici tarafından seri hale getirilmiş etkinleştirmek için özellikler, çalışma zamanı erişimi denetler.

- `DataContractSerializer`. Denetimleri İlkesi kullanan Serileştirmenin <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> sınıfı.

- `DataContractJsonSerializer`. İlke kullanan bir JSON serileştirme denetleyen <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> sınıfı.

- `XmlSerializer`. İlke kullanan bir XML serileştirme denetleyen <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> sınıfı.

- `MarshalObject`. Denetim İlkesi WinRT ve COM başvuru türlerini hazırlama

- `MarshalDelegate`. Yerel kod için işlev işaretçileri olarak temsilci türleri hazırlama için ilke denetler.

- `MarshalStructure` . Yerel kod yapılarına hazırlama için ilke denetler.

Bu ilke türleri ile ilişkili ayarlar şunlardır:

- `All`. Tüm türleri ve araç zinciri kaldırmaz üyeleri için ilkeyi etkinleştirin.

- `Auto`. Varsayılan davranışı kullanın. (Bir ilke belirtmeden Bu ilke ayarını eşdeğer `Auto` Bu ilke, örneğin bir üst öğe tarafından geçersiz kılınmadığı sürece.)

- `Excluded`. Bir program öğesi için ilke devre dışı bırakın.

- `Public`. Üye gereksizdir ve bu nedenle kaldırır araç zincirinizi belirler sürece genel türleri veya üyeleri için ilkeyi etkinleştirin. (İkinci durumda, kullanmalısınız `Required Public` üye tutulur ve yansıma yeteneklere sahip olmak.)

- `PublicAndInternal`. Araç zincirinizi bunları kaldırmaz, genel ve iç türleri veya üyeleri için ilkeyi etkinleştirin.

- `Required Public`. Genel türler ve üyeler olup olmadığını kullanılan tutmak araç zincirinizi gerektirir ve bunlar için ilke etkinleştirin.

- `Required PublicAndInternal`. Hem genel hem de iç türleri ve üyeleri kullanılır olup olmadığını tutmak için araç zincirinizi gerektirir ve bunlar için ilke etkinleştirin.

- `Required All`. Tüm türler ve üyeler olup olmadığını kullanılan tutmak araç zincirinizi gerektirir ve bunlar için ilke etkinleştirin.

Örneğin, aşağıdaki çalışma zamanı yönergeleri dosya DataClasses.dll derlemesinde tüm türler ve üyeler için ilke tanımlar. Tüm ortak özellikler, tüm türler ve tür üyeleri için gözatma etkinleştirir serileştirilmesi etkinleştirme tüm türleri sağlar. Bu yansıma sağlar (nedeniyle `Dynamic` özniteliği) ve tüm genel türler ve üyeler için yansıma sağlar.

```xml
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">
   <Application>
      <Assembly Name="DataClasses" Serialize="Required Public"
                Browse="All" Activate="PublicAndInternal"
                Dynamic="Public"  />
   </Application>
   <Library Name="UtilityLibrary">
     <!-- Child elements go here -->
   </Library>
</Directives>
```

### <a name="specifying-policy-for-members"></a>İlke için üyeleri belirtme

[Özelliği](../../../docs/framework/net-native/property-element-net-native.md) ve [alan](../../../docs/framework/net-native/field-element-net-native.md) öğeleri aşağıdaki ilke türlerinden destekler:

- `Browse` -Bu üyeyle ilgili bilgi için sorgulama kontrol eder ancak herhangi bir çalışma zamanı erişim sağlamaz.

- `Dynamic` -Dinamik programlama etkinleştirmek için Oluşturucular, yöntemler, alanlar, özellikler ve olaylar, tüm tür üyelerini, çalışma zamanı erişimi denetler. Ayrıca, kapsayan tür hakkında bilgi için sorgulama denetler.

- `Serialize` -Üye türü sıralanabilir ve kitaplıkları gibi Newtonsoft JSON seri hale getirici tarafından serisi örneklerinin etkinleştirmek için çalışma zamanı erişimi denetler. Bu ilke, Oluşturucular, alanlar ve özellikler için uygulanabilir.

[Yöntemi](../../../docs/framework/net-native/method-element-net-native.md) ve [olay](../../../docs/framework/net-native/event-element-net-native.md) öğeleri aşağıdaki ilke türlerinden destekler:

- `Browse` -Bu üyeyle ilgili bilgi için sorgulama kontrol eder, ancak herhangi bir çalışma zamanı erişim sağlamaz.

- `Dynamic` -Dinamik programlama etkinleştirmek için Oluşturucular, yöntemler, alanlar, özellikler ve olaylar, tüm tür üyelerini, çalışma zamanı erişimi denetler. Ayrıca, kapsayan tür hakkında bilgi için sorgulama denetler.

 Bu ilke türleri ile ilişkili ayarlar şunlardır:

- `Auto` -Varsayılan davranışı kullanın. (Bir ilke belirtmeden Bu ilke ayarını eşdeğer `Auto` sürece bir şey onu geçersiz kılar.)

- `Excluded` -Hiç üye için meta verileri içerir.

- `Included` -Çıkış üst türü varsa ilkeyi etkinleştirin.

- `Required` -Araç zinciri, bu üye tutmak için gerekli olsa bile görünür kullanılmayan ve ilke etkinleştirmek için.

## <a name="runtime-directives-file-semantics"></a>Çalışma zamanı yönergeleri dosya semantiği

İlke, aynı anda daha yüksek düzeyde ve alt düzey öğeleri için tanımlanabilir. Örneğin, ilke için bir derleme ve bazı bu derlemede bulunan türleri için tanımlanabilir. Belirli bir alt düzey öğenin temsil edilmeyen, kendi üst öğesi İlkesi devralır. Örneğin, bir `Assembly` öğe varsa ancak `Type` öğesi olmayan, ilke içinde belirtilen `Assembly` derlemedeki her tür öğesi uygular. Birden çok öğe, aynı program öğesi için ilke de uygulayabilirsiniz. Örneğin, ayrı [derleme](../../../docs/framework/net-native/assembly-element-net-native.md) öğeleri tanımlamak aynı ilke öğesi için aynı derlemenin farklı. Aşağıdaki bölümlerde, belirli bir tür için ilke bu gibi durumlarda nasıl çözümleneceğini açıklanmaktadır.

A [türü](../../../docs/framework/net-native/type-element-net-native.md) veya [yöntemi](../../../docs/framework/net-native/method-element-net-native.md) öğesi bir genel tür veya yöntemin, ilke kendi ilkesi olmayan tüm örneklemesi için geçerlidir. Örneğin, bir `Type` ilkesini belirtir öğesi <xref:System.Collections.Generic.List%601> belirli bir oluşturulan genel tür için geçersiz kılınmadığı sürece tüm yapılandırılmış, genel tür örneklerine uygulanır (aşağıdaki gibi bir `List<Int32>`) tarafından bir `TypeInstantiation` öğesi. Aksi takdirde, öğeleri adlı program öğesi için ilkeyi tanımlayın.

Bir öğenin belirsiz olduğunda altyapısı eşleşmeleri arar ve bu tam bir eşleşme bulunursa, onu kullanır. Birden fazla eşleşme bulunursa, bir uyarı veya hata olacaktır.

### <a name="if-two-directives-apply-policy-to-the-same-program-element"></a>İki yönergeleri aynı program öğesi için ilkeyi uygularsanız

Aynı ilke türü (örneğin, bir derleme veya tür) aynı program öğesi için farklı değerlere ayarlamak iki farklı çalışma zamanı yönergeleri dosyaları öğelerinde çalışırsanız çakışma gibi çözümlenir:

1. Varsa `Excluded` öğe varsa, önceliğe sahiptir.

2. `Required` önceliğe sahip üstünde değil `Required`.

3. `All` üzerinde önceliğe sahip `PublicAndInternal`, üzerinde önceliğe sahip `Public`.

4. Açık herhangi bir ayar, üzerinde önceliğe sahiptir. `Auto`.

Tek bir projede aşağıdaki iki çalışma zamanı yönergeleri dosyalar içeriyorsa, örneğin, serileştirme ilke DataClasses.dll için her iki ayarlanmışsa `Required Public` ve `All`. Bu durumda, seri hale getirme ilkesi olarak çözülmüş olacaktır `Required All`.

```xml
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">
   <Application>
      <Assembly Name="DataClasses" Serialize="Required Public"/>
   </Application>
   <Library Name="DataClasses">
      <!-- any other elements -->
   </Library>
</Directives>
```

```xml
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">
   <Application>
      <Assembly Name="DataClasses" Serialize="All" />
   </Application>
   <Library Name="DataClasses">
      <!-- any other elements -->
   </Library>
</Directives>
```

Ancak, tek bir çalışma zamanı yönergeleri dosyasında iki yönergeleri aynı program öğesi için aynı ilke türü ayarlamaya çalışırsanız, XML şema tanımı aracı bir hata iletisi görüntüler.

### <a name="if-child-and-parent-elements-apply-the-same-policy-type"></a>Alt ve üst öğeler aynı ilke türü uygularsanız

Alt öğeleri geçersiz kılan, üst öğeleri dahil olmak üzere, `Excluded` ayarı. Geçersiz kılma olduğunu belirtmek için isteyeceğiniz temel nedeni `Auto`.

Aşağıdaki örnekte, her şey için serileştirme ilkesini `DataClasses` olmayan içinde `DataClasses.ViewModels` olacaktır `Required Public`ve her ikisinde de olan her şeyi `DataClasses` ve `DataClasses.ViewModels` olacaktır `All`.

```xml
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">
   <Application>
      <Assembly Name="DataClasses" Serialize="Required Public" >
         <Namespace Name="DataClasses.ViewModels" Serialize="All" />
      </Assembly>
   </Application>
   <Library Name="DataClasses">
      <!-- any other elements -->
   </Library>
</Directives>
```

### <a name="if-open-generics-and-instantiated-elements-apply-the-same-policy-type"></a>Açık genel türler ve örneklenen öğeleri aynı ilke türü uygulanacaksa

Aşağıdaki örnekte, `Dictionary<int,int>` atanan `Browse` altyapısı vermek, diğer bir neden varsa ilke `Browse` (Aksi takdirde, varsayılan davranışı olacaktır) ilkesi; diğer her örneğinin <xref:System.Collections.Generic.Dictionary%602> sahip olur üyelerini gözatılabilir.

```xml
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">
   <Application>
      <Assembly Name="DataClasses" Serialize="Required Public" >
         <Namespace Name="DataClasses.ViewModels" Serialize="All" />
      </Assembly>
      <Namespace Name="DataClasses.Generics" />
      <Type Name="Dictionary" Browse="All" />
      <TypeInstantiation Name="Dictionary"
                         Arguments="System.Int32,System.Int32" Browse="Auto" />
   </Application>
   <Library Name="DataClasses">
      <!-- any other elements -->
   </Library>
</Directives>
```

### <a name="how-policy-is-inferred"></a>Nasıl ilke algılanır

Her ilke türü bir farklı Bu ilke türünün varolup olmadığını diğer yapıları nasıl etkilediğini belirlemek kurallara sahiptir.

#### <a name="the-effect-of-browse-policy"></a>Göz atma İlkesi etkisi

Uygulama `Browse` ilke türü için aşağıdaki ilke değişiklikleri içerir:

- Türün temel türü ile işaretlenmiş `Browse` ilkesi.

- Bir örneklenmiş genel türü ise, türü örneklenmemiş sürümü ile işaretlenmiş `Browse` ilkesi.

- Bir temsilci türü ise `Invoke` türünde yöntemi ile işaretlenmiş `Dynamic` ilkesi.

- Her arabirim türü ile işaretlenmiş `Browse` ilkesi.

- Türüne uygulanan her bir öznitelik türü ile işaretlenmiş `Browse` ilkesi.

- Tür genelse, her kısıtlama türü ile işaretlenmiş `Browse` ilkesi.

- Tür genelse, tür örneği üzerinde türleri ile işaretlenmiş `Browse` ilkesi.

Uygulama `Browse` ilke için bir yöntem aşağıdaki ilke değişiklikleri içerir:

- Her bir yöntemin parametre türü ile işaretlenmiş `Browse` ilkesi.

- Yöntemin dönüş türü ile işaretlenmiş `Browse` ilkesi.

- Yöntemin kapsayan tür ile işaretlenmiş `Browse` ilkesi.

- Örneklenen bir genel yöntem yöntem ise örneklenmemiş genel yöntem ile işaretlenmiş `Browse` ilkesi.

- Yönteme uygulanan her bir öznitelik türü ile işaretlenmiş `Browse` ilkesi.

- Yöntem genelse, her kısıtlama türü ile işaretlenmiş `Browse` ilkesi.

- Yöntem genelse, yöntemi örneği türleri ile işaretlenmiş `Browse` ilkesi.

Uygulama `Browse` bir alana ilke aşağıdaki ilke değişiklikleri içerir:

- Alana uygulanan her bir öznitelik türü ile işaretlenmiş `Browse` ilkesi.

- Alan türü ile işaretlenmiş `Browse` ilkesi.

- Alan ait olduğu tür ile işaretlenmiş `Browse` ilkesi.

#### <a name="the-effect-of-dynamic-policy"></a>Dinamik ilke etkisi

Uygulama `Dynamic` ilke türü için aşağıdaki ilke değişiklikleri içerir:

- Türün temel türü ile işaretlenmiş `Dynamic` ilkesi.

- Bir örneklenmiş genel türü ise, türü örneklenmemiş sürümü ile işaretlenmiş `Dynamic` ilkesi.

- Türü bir temsilci türü ise `Invoke` türünde yöntemi ile işaretlenmiş `Dynamic` ilkesi.

- Her arabirim türü ile işaretlenmiş `Browse` ilkesi.

- Türüne uygulanan her bir öznitelik türü ile işaretlenmiş `Browse` ilkesi.

- Tür genelse, her kısıtlama türü ile işaretlenmiş `Browse` ilkesi.

- Tür genelse, tür örneği üzerinde türleri ile işaretlenmiş `Browse` ilkesi.

Uygulama `Dynamic` ilke için bir yöntem aşağıdaki ilke değişiklikleri içerir:

- Her bir yöntemin parametre türü ile işaretlenmiş `Browse` ilkesi.

- Yöntemin dönüş türü ile işaretlenmiş `Dynamic` ilkesi.

- Yöntemin kapsayan tür ile işaretlenmiş `Dynamic` ilkesi.

- Örneklenen bir genel yöntem yöntem ise örneklenmemiş genel yöntem ile işaretlenmiş `Browse` ilkesi.

- Yönteme uygulanan her bir öznitelik türü ile işaretlenmiş `Browse` ilkesi.

- Yöntem genelse, her kısıtlama türü ile işaretlenmiş `Browse` ilkesi.

- Yöntem genelse, yöntemi örneği türleri ile işaretlenmiş `Browse` ilkesi.

- Yöntemi tarafından çağrılabilir `MethodInfo.Invoke`, ve temsilci oluşturma mümkün hale <xref:System.Reflection.MethodInfo.CreateDelegate%2A?displayProperty=nameWithType>.

Uygulama `Dynamic` bir alana ilke aşağıdaki ilke değişiklikleri içerir:

- Alana uygulanan her bir öznitelik türü ile işaretlenmiş `Browse` ilkesi.

- Alan türü ile işaretlenmiş `Dynamic` ilkesi.

- Alan ait olduğu tür ile işaretlenmiş `Dynamic` ilkesi.

#### <a name="the-effect-of-activation-policy"></a>Etkinleştirme ilkesinin etkisini

Bir türe etkinleştirme ilkesini uygulama aşağıdaki ilke değişiklikleri içerir:

- Bir örneklenmiş genel türü ise, türü örneklenmemiş sürümü ile işaretlenmiş `Browse` ilkesi.

- Türü bir temsilci türü ise `Invoke` türünde yöntemi ile işaretlenmiş `Dynamic` ilkesi.

- Oluşturucu türü ile işaretlenir `Activation` ilkesi.

Uygulama `Activation` ilke için bir yöntem aşağıdaki ilke değişikliği içerir:

- Oluşturucu tarafından çağrılabilir <xref:System.Reflection.ConstructorInfo.Invoke%2A?displayProperty=nameWithType> ve <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> yöntemleri. Yöntemleri için `Activation` ilke oluşturucular yalnızca etkiler.

Uygulama `Activation` bir alana ilke etkisi yoktur.

#### <a name="the-effect-of-serialize-policy"></a>Serileştirme ilkesinin etkisini

`Serialize` İlkesi ortak yansıma tabanlı serileştiricileri kullanımını etkinleştirir. Ancak, Microsoft dışı seri hale getiricileri genişletme tam yansıma erişim desenlerini Microsoft'a bilinmemesi nedeniyle bu ilkeyi tamamen etkili olmayabilir.

Uygulama `Serialize` ilke türü için aşağıdaki ilke değişiklikleri içerir:

- Türün temel türü ile işaretlenmiş `Serialize` ilkesi.

- Bir örneklenmiş genel türü ise, türü örneklenmemiş sürümü ile işaretlenmiş `Browse` ilkesi.

- Türü bir temsilci türü ise `Invoke` türünde yöntemi ile işaretlenmiş `Dynamic` ilkesi.

- Bir numaralandırma türü ise, bir dizi türü ile işaretlenmiş `Serialize` ilkesi.

- Türü uyguluyorsa <xref:System.Collections.Generic.IEnumerable%601>, `T` ile işaretlenmiş `Serialize` ilkesi.

- Tür ise <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.Generic.IList%601>, <xref:System.Collections.Generic.ICollection%601>, <xref:System.Collections.Generic.IReadOnlyCollection%601>, veya <xref:System.Collections.Generic.IReadOnlyList%601>, ardından `T[]` ve <xref:System.Collections.Generic.List%601> ile işaretlenen `Serialize` ilke. ancak arabirim türünün üye ileişaretlenmiş`Serialize`ilkesi.

- Tür ise <xref:System.Collections.Generic.List%601>, üye türü ile işaretlenmiş `Serialize` ilkesi.

- Tür ise <xref:System.Collections.Generic.IDictionary%602>, <xref:System.Collections.Generic.Dictionary%602> ile işaretlenmiş `Serialize` ilkesi. ancak herhangi bir türün üyeleri ile işaretlenmiş `Serialize` ilkesi.

- Tür ise <xref:System.Collections.Generic.Dictionary%602>, üye türü ile işaretlenmiş `Serialize` ilkesi.

- Türü uyguluyorsa <xref:System.Collections.Generic.IDictionary%602>, `TKey` ve `TValue` ile işaretlenmiş `Serialize` ilkesi.

- Her Oluşturucu, her bir özellik erişimcisi ve her bir alan ile işaretlenmiş `Serialize` ilkesi.

Uygulama `Serialize` ilke için bir yöntem aşağıdaki ilke değişiklikleri içerir:

- Kapsayan tür ile işaretlenmiş `Serialize` ilkesi.

- Yöntemin dönüş türü ile işaretlenmiş `Serialize` ilkesi.

Uygulama `Serialize` bir alana ilke aşağıdaki ilke değişiklikleri içerir:

- Kapsayan tür ile işaretlenmiş `Serialize` ilkesi.

- Alan türü ile işaretlenmiş `Serialize` ilkesi.

#### <a name="the-effect-of-xmlserializer-datacontractserializer-and-datacontractjsonserializer-policies"></a>XmlSerializer DataContractSerializer ve DataContractJsonSerializer ilkeleri etkisi

Farklı `Serialize` yansıma tabanlı seri hale getiricileri genişletme için tasarlanmıştır, ilke, `XmlSerializer`, `DataContractSerializer`, ve `DataContractJsonSerializer` ilkeleri bir dizi bilinen seri hale getiricileri genişletme etkinleştirmek için kullanılır [!INCLUDE[net_native](../../../includes/net-native-md.md)] araç zinciri. Bu seri hale getiricileri genişletme yansıma kullanarak uygulanmadı, ancak çalışma zamanında seri hale getirilebilir türler kümesi benzer bir şekilde reflectable türleri olarak belirlenir.

Bu ilkelerden birini uygulayarak bir türe türü ile eşleşen serileştirici serileştirilecek sağlar. Ayrıca, serileştirme motoruna, statik olarak seri hale getirme gerektiği belirleyebilirsiniz herhangi bir türü ayrıca seri hale getirilebilir olur.

Bu ilkeler, yöntemler veya alanları üzerinde etkisi yoktur.

"Serileştiricileri farklar" bölümünde daha fazla bilgi için bkz. [geçirme bilgisayarınızı Windows Store uygulaması için .NET Native](../../../docs/framework/net-native/migrating-your-windows-store-app-to-net-native.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma Zamanı Yönerge Öğeleri](../../../docs/framework/net-native/runtime-directive-elements.md)
- [Yansıma ve .NET Native](../../../docs/framework/net-native/reflection-and-net-native.md)
