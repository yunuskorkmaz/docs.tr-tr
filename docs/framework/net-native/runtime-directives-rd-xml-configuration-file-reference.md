---
title: Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu
ms.date: 03/30/2017
ms.assetid: 8241523f-d8e1-4fb6-bf6a-b29bfe07b38a
ms.openlocfilehash: e74d34693446cca645003a9f93bc1777849e3182
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76738412"
---
# <a name="runtime-directives-rdxml-configuration-file-reference"></a>Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu

Çalışma zamanı yönergeleri (. RD. xml) dosyası, belirtilen program öğelerinin yansıma için kullanılabilir olup olmadığını belirten bir XML yapılandırma dosyasıdır. Çalışma zamanı yönergeleri dosyasına bir örnek aşağıda verilmiştir:

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

## <a name="the-structure-of-a-runtime-directives-file"></a>Çalışma zamanı yönergeleri dosyasının yapısı

Çalışma zamanı yönergeleri dosyası `http://schemas.microsoft.com/netfx/2013/01/metadata` ad alanını kullanır.

Kök öğesi, [yönergeleri](directives-element-net-native.md) öğesidir. Aşağıdaki yapıda gösterildiği gibi sıfır veya daha fazla [kitaplık](library-element-net-native.md) öğesi ve sıfır veya bir [uygulama](application-element-net-native.md) öğesi içerebilir. [Uygulama](application-element-net-native.md) öğesinin öznitelikleri, uygulama genelinde çalışma zamanı yansıma ilkesi tanımlayabilir veya alt öğeler için bir kapsayıcı olarak görev yapabilir. Öte yandan [kitaplık](library-element-net-native.md) öğesi yalnızca bir kapsayıcıdır. [Uygulama](application-element-net-native.md) ve [kitaplık](library-element-net-native.md) öğelerinin alt öğeleri, yansıma için kullanılabilen türleri, yöntemleri, alanları, özellikleri ve olayları tanımlar.

Başvuru bilgileri için aşağıdaki yapıdaki öğeleri seçin veya [çalışma zamanı yönerge öğelerini](runtime-directive-elements.md)görüntüleyin. Aşağıdaki hiyerarşide üç nokta özyinelemeli bir yapıyı işaret ediyor. Köşeli ayraçlar içindeki bilgiler, bu öğenin isteğe bağlı veya gerekli olduğunu ve kullanılıp kullanılmadığını, kaç örneğe (bir veya daha fazla) izin verildiğini gösterir.

- [Yönergeler](directives-element-net-native.md) [1:1]
  - [Uygulama](application-element-net-native.md) [0:1]
    - [Derleme](assembly-element-net-native.md) [0: d]
      - [Ad alanı](namespace-element-net-native.md) [0: d]. . .
      - [0: d] [yazın](type-element-net-native.md) . . .
      - [Typeörneklemesi](typeinstantiation-element-net-native.md) (oluşturulmuş genel tür) [0: a]. . .
    - [Ad alanı](namespace-element-net-native.md) [0: d]
      - [Ad alanı](namespace-element-net-native.md) [0: d]. . .
      - [0: d] [yazın](type-element-net-native.md) . . .
      - [Typeörneklemesi](typeinstantiation-element-net-native.md) (oluşturulmuş genel tür) [0: a]. . .
    - [Tür](type-element-net-native.md) [0: d]
      - Alt [türler](subtypes-element-net-native.md) (kapsayan türün alt sınıfları) [o:1]
      - [0: d] [yazın](type-element-net-native.md) . . .
      - [Typeörneklemesi](typeinstantiation-element-net-native.md) (oluşturulmuş genel tür) [0: a]. . .
      - [Attributeme](attributeimplies-element-net-native.md) (tür içeren bir öznitelik) [o:1]
      - [Genericparameter](genericparameter-element-net-native.md) [0: d]
      - [Yöntem](method-element-net-native.md) [0: d]
        - [Parametre](parameter-element-net-native.md) [0: d]
        - [Typeparameter](typeparameter-element-net-native.md) [0: d]
        - [Genericparameter](genericparameter-element-net-native.md) [0: d]
      - [Methodörneklemesi](methodinstantiation-element-net-native.md) (oluşturulmuş genel yöntem) [0: a]
      - [Özellik](property-element-net-native.md) [0: d]
      - [Alan](field-element-net-native.md) [0: d]
      - [Olay](event-element-net-native.md) [0: d]
    - [Typeörneklemesi](typeinstantiation-element-net-native.md) (oluşturulmuş genel tür) [0: d]
      - [0: d] [yazın](type-element-net-native.md) . . .
      - [Typeörneklemesi](typeinstantiation-element-net-native.md) (oluşturulmuş genel tür) [0: a]. . .
      - [Yöntem](method-element-net-native.md) [0: d]
        - [Parametre](parameter-element-net-native.md) [0: d]
        - [Typeparameter](typeparameter-element-net-native.md) [0: d]
        - [Genericparameter](genericparameter-element-net-native.md) [0: d]
      - [Methodörneklemesi](methodinstantiation-element-net-native.md) (oluşturulmuş genel yöntem) [0: a]
      - [Özellik](property-element-net-native.md) [0: d]
      - [Alan](field-element-net-native.md) [0: d]
      - [Olay](event-element-net-native.md) [0: d]
  - [Kitaplık](library-element-net-native.md) [0: d]
    - [Derleme](assembly-element-net-native.md) [0: d]
      - [Ad alanı](namespace-element-net-native.md) [0: d]. . .
      - [0: d] [yazın](type-element-net-native.md) . . .
      - [Typeörneklemesi](typeinstantiation-element-net-native.md) (oluşturulmuş genel tür) [0: a]. . .
    - [Ad alanı](namespace-element-net-native.md) [0: d]
      - [Ad alanı](namespace-element-net-native.md) [0: d]. . .
      - [0: d] [yazın](type-element-net-native.md) . . .
      - [Typeörneklemesi](typeinstantiation-element-net-native.md) (oluşturulmuş genel tür) [0: a]. . .
    - [Tür](type-element-net-native.md) [0: d]
      - Alt [türler](subtypes-element-net-native.md) (kapsayan türün alt sınıfları) [o:1]
      - [0: d] [yazın](type-element-net-native.md) . . .
      - [Typeörneklemesi](typeinstantiation-element-net-native.md) (oluşturulmuş genel tür) [0: a]. . .
      - [Attributeme](attributeimplies-element-net-native.md) (tür içeren bir öznitelik) [o:1]
      - [Genericparameter](genericparameter-element-net-native.md) [0: d]
      - [Yöntem](method-element-net-native.md) [0: d]
      - [Methodörneklemesi](methodinstantiation-element-net-native.md) (oluşturulmuş genel yöntem) [0: a]
      - [Özellik](property-element-net-native.md) [0: d]
      - [Alan](field-element-net-native.md) [0: d]
      - [Olay](event-element-net-native.md) [0: d]
    - [Typeörneklemesi](typeinstantiation-element-net-native.md) (oluşturulmuş genel tür) [0: d]
      - [0: d] [yazın](type-element-net-native.md) . . .
      - [Typeörneklemesi](typeinstantiation-element-net-native.md) (oluşturulmuş genel tür) [0: a]. . .
      - [Yöntem](method-element-net-native.md) [0: d]
      - [Methodörneklemesi](methodinstantiation-element-net-native.md) (oluşturulmuş genel yöntem) [0: a]
      - [Özellik](property-element-net-native.md) [0: d]
      - [Alan](field-element-net-native.md) [0: d]
      - [Olay](event-element-net-native.md) [0: d]

[Uygulama](application-element-net-native.md) öğesinin hiç özniteliği olamaz veya [çalışma zamanı yönergesinde ve ilke bölümünde](#Directives)ele alınan ilke özniteliklerine sahip olabilir.

Bir [kitaplık](library-element-net-native.md) öğesi, dosya uzantısı olmadan bir kitaplığın veya derlemenin adını belirten tek bir özniteliğe sahiptir `Name`. Örneğin, aşağıdaki [kitaplık](library-element-net-native.md) öğesi Extensions. dll adlı bir derleme için geçerlidir.

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

## <a name="runtime-directives-and-policy"></a>Çalışma zamanı yönergeleri ve ilkesi

[Uygulama](application-element-net-native.md) öğesinin kendisi ve [kitaplık](library-element-net-native.md) ve [uygulama](application-element-net-native.md) öğeleri Express ilkesinin alt öğeleri; diğer bir deyişle, bir uygulamanın bir program öğesine yansıma uygulayabileceği şekilde tanımlar. İlke türü, öğesinin bir özniteliği tarafından tanımlanır (örneğin, `Serialize`). İlke değeri özniteliğin değeri (örneğin, `Serialize="Required"`) tarafından tanımlanır.

Bir öğenin özniteliği tarafından belirtilen herhangi bir ilke, bu ilke için bir değer belirtmeyen tüm alt öğeler için geçerlidir. Örneğin, bir ilke bir [tür](type-element-net-native.md) öğesiyle belirtilmişse, bu ilke, bir ilkenin açıkça belirtilmediği tüm içerilen türler ve Üyeler için geçerlidir.

[Uygulama](application-element-net-native.md), [derleme](assembly-element-net-native.md), [attributeby](attributeimplies-element-net-native.md), [Namespace](namespace-element-net-native.md), alt [türler](subtypes-element-net-native.md)ve [tür](type-element-net-native.md) öğeleri tarafından Ifade edilen ilke, ayrı Üyeler Için ifade edilebilir ilkeden farklıdır ( [Yöntem](method-element-net-native.md), [özellik](property-element-net-native.md), [alan](field-element-net-native.md)ve [olay](event-element-net-native.md) öğeleri tarafından).

### <a name="specifying-policy-for-assemblies-namespaces-and-types"></a>Derlemeler, ad alanları ve türler için ilke belirtme

[Uygulama](application-element-net-native.md), [derleme](assembly-element-net-native.md), [attributeme](attributeimplies-element-net-native.md), [Namespace](namespace-element-net-native.md), alt [türleri](subtypes-element-net-native.md)ve [tür](type-element-net-native.md) öğeleri aşağıdaki ilke türlerini destekler:

- `Activate`. Örneklerin etkinleştirilmesini sağlamak için oluşturuculara çalışma zamanı erişimini denetler.

- `Browse`. Program öğeleri hakkında bilgi sorgulamayı denetler, ancak hiçbir çalışma zamanı erişimini etkinleştirmez.

- `Dynamic`. Dinamik programlamayı etkinleştirmek için oluşturucular, Yöntemler, alanlar, Özellikler ve olaylar dahil olmak üzere tüm tür üyelerine çalışma zamanı erişimini denetler.

- `Serialize`. Tür örneklerinin, Newtonsoft JSON serileştirici gibi üçüncü taraf kitaplıklara serileştirilmesi ve serileştirilmesi için oluşturuculara, alanlara ve özelliklere çalışma zamanı erişimini denetler.

- `DataContractSerializer`. <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> sınıfını kullanan serileştirme için ilkeyi denetler.

- `DataContractJsonSerializer`. <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> sınıfını kullanan JSON serileştirme için ilkeyi denetler.

- `XmlSerializer`. <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> sınıfını kullanan XML serileştirme ilkesini denetler.

- `MarshalObject`. WinRT ve COM 'a başvuru türlerini hazırlama ilkesini denetler.

- `MarshalDelegate`. Temsilci türlerini yerel koda işlev işaretçileri olarak hazırlama ilkesini denetler.

- `MarshalStructure` . Yapıları yerel koda hazırlama ilkesini denetler.

Bu ilke türleriyle ilişkili ayarlar şunlardır:

- `All`. Araç zincirinin kaldıramayan tüm türler ve Üyeler için ilkeyi etkinleştirin.

- `Auto`. Varsayılan davranışı kullanın. (İlke belirtilmeden, ilke geçersiz kılınmadıkça (örneğin, bir üst öğe), bu ilke `Auto` ayarlamaya eşdeğerdir.)

- `Excluded`. Program öğesi için ilkeyi devre dışı bırakın.

- `Public`. Araç zinciri üyenin gereksiz olduğunu belirlerse ve bu nedenle uygulamayı kaldırmadığı müddetçe ortak türler veya Üyeler için ilkeyi etkinleştirin. (İkinci durumda, üyenin tutulduğundan ve yansıma özelliklerine sahip olduğundan emin olmak için `Required Public` kullanmanız gerekir.)

- `PublicAndInternal`. Araç zinciri onları kaldırmazsa ortak ve iç türler veya Üyeler için ilkeyi etkinleştirin.

- `Required Public`. Ortak türleri ve üyeleri, kullanıldıkları ve kullanılmayacağı gibi tutmak ve ilke için etkinleştirmek üzere araç zinciri gerektirir.

- `Required PublicAndInternal`. Araç zincirinin hem ortak hem de iç türleri ve üyeleri, kullanılmalarına bakılmaksızın ve bunları kendileri için etkinleştirin.

- `Required All`. Araç zincirinin tüm türleri ve üyeleri kullanıp kullanmadığını ve bunların kullanılmadığını ve ilke için etkin olmasını gerektir.

Örneğin, aşağıdaki çalışma zamanı yönergeleri dosyası, veri sınıfları. dll dosyasındaki tüm türler ve Üyeler için ilkeyi tanımlar. Tüm ortak özelliklerin serileştirilmesi için yansıma kullanımını, tüm türler ve tür üyeleri için gözatmayı etkinleştirmek, tüm türler için etkinleştirmeyi etkinleştirmek (`Dynamic` özniteliği nedeniyle) ve tüm genel türler ve Üyeler için yansıma etkinleştirmek için yansıma imkanı sunar.

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

### <a name="specifying-policy-for-members"></a>Üyeler için ilke belirtme

[Özellik](property-element-net-native.md) ve [alan](field-element-net-native.md) öğeleri aşağıdaki ilke türlerini destekler:

- `Browse`-Bu üye hakkında bilgi sorgulama denetimleri, ancak hiçbir çalışma zamanı erişimini etkinleştirmez.

- `Dynamic`-dinamik programlamayı etkinleştirmek için oluşturucular, Yöntemler, alanlar, Özellikler ve olaylar dahil olmak üzere tüm tür üyelerine çalışma zamanı erişimini denetler. Ayrıca, kapsayan tür hakkındaki bilgileri sorgulamayı denetler.

- `Serialize`-tür örneklerinin, Newtonsoft JSON serileştirici gibi kitaplıklar tarafından serileştirilmesi ve seri durumdan çıkarılmakta olması için üyeye çalışma zamanı erişimini denetler. Bu ilke oluşturucular, alanlar ve özelliklere uygulanabilir.

[Yöntemi](method-element-net-native.md) ve [olay](event-element-net-native.md) öğeleri aşağıdaki ilke türlerini destekler:

- `Browse`-Bu üye hakkında bilgi sorgulama denetimleri, ancak hiçbir çalışma zamanı erişimini etkinleştirmez.

- `Dynamic`-dinamik programlamayı etkinleştirmek için oluşturucular, Yöntemler, alanlar, Özellikler ve olaylar dahil olmak üzere tüm tür üyelerine çalışma zamanı erişimini denetler. Ayrıca, kapsayan tür hakkındaki bilgileri sorgulamayı denetler.

 Bu ilke türleriyle ilişkili ayarlar şunlardır:

- `Auto`-varsayılan davranışı kullanın. (İlke belirtmeksizin, bir öğe geçersiz kılınmadığı takdirde bu ilkenin `Auto` ayarlanmasına eşdeğerdir.)

- `Excluded`-üyenin meta verilerini hiçbir şekilde eklemeyin.

- `Included`-üst tür çıktıda varsa ilkeyi etkinleştirin.

- `Required`-araç zincirinin, kullanılmamış gibi görünse bile bu üyeyi tutması gerekir ve ilkeyi etkinleştirir.

## <a name="runtime-directives-file-semantics"></a>Çalışma zamanı yönergeleri dosya semantiği

İlke, hem daha yüksek hem de alt düzey öğeler için eşzamanlı olarak tanımlanabilir. Örneğin, ilke bir derleme için ve bu derlemede yer alan bazı türler için tanımlanabilir. Belirli bir alt düzey öğe gösterilmediğinden, üst öğesinin ilkesini devralır. Örneğin, bir `Assembly` öğesi varsa ancak `Type` öğeler yoksa, `Assembly` öğesinde belirtilen ilke derlemedeki her tür için geçerlidir. Aynı program öğesine aynı zamanda birden çok öğe ilke uygulayabilir. Örneğin, ayrı [derleme](assembly-element-net-native.md) öğeleri aynı derleme için aynı ilke öğesini farklı şekilde tanımlayabilir. Aşağıdaki bölümlerde, belirli bir türün ilkesinin bu durumlarda nasıl çözümlendiğini açıklanmaktadır.

Genel bir türün veya yöntemin [tür](type-element-net-native.md) veya [Yöntem](method-element-net-native.md) öğesi, kendi ilkesi olmayan tüm örneklemelerde ilkesini uygular. Örneğin, <xref:System.Collections.Generic.List%601> ilkesini belirten `Type` bir öğesi, belirli bir oluşturulan genel tür için (`List<Int32>`gibi) bir `TypeInstantiation` öğesi tarafından geçersiz kılınmadığı sürece, bu genel türün oluşturulan tüm örnekleri için geçerlidir. Aksi takdirde, öğeleri adlı program öğesi için ilkeyi tanımlar.

Bir öğe belirsiz olduğunda, motor eşleşme arar ve tam eşleşme bulursa onu kullanacaktır. Birden çok eşleşme bulunursa bir uyarı veya hata olur.

### <a name="if-two-directives-apply-policy-to-the-same-program-element"></a>İki yönergeler aynı program öğesine ilke uygualıyorsa

Farklı çalışma zamanı yönergeleri dosyalarındaki iki öğe aynı program öğesi (bir derleme veya tür gibi) için aynı ilke türünü farklı değerlere ayarlamaya çalışıyorsa, çakışma aşağıdaki gibi çözümlenir:

1. `Excluded` öğesi varsa önceliğe sahiptir.

2. `Required` `Required`değil önceliğe sahip.

3. `All`, `Public`öncelikli olan `PublicAndInternal`önceliklidir.

4. Herhangi bir açık ayar `Auto`önceliklidir.

Örneğin, tek bir proje aşağıdaki iki çalışma zamanı yönergeleri dosyasını içeriyorsa, DataClasses. dll için serileştirme ilkesi hem `Required Public` hem de `All`olarak ayarlanır. Bu durumda, serileştirme ilkesi `Required All`olarak çözümlenir.

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

Ancak, tek bir çalışma zamanı yönergeleri dosyasında iki yönergesi aynı program öğesi için aynı ilke türünü ayarlamaya çalışırsanız, XML şeması tanım aracında bir hata iletisi görüntülenir.

### <a name="if-child-and-parent-elements-apply-the-same-policy-type"></a>Alt ve üst öğeler aynı ilke türünü uygualıyorsa

Alt öğeler, `Excluded` ayarı da dahil olmak üzere üst öğelerini geçersiz kılar. Geçersiz kılma, `Auto`belirtmek istediğiniz ana nedendir.

Aşağıdaki örnekte, `DataClasses.ViewModels` olmayan `DataClasses` her şey için serileştirme ilkesi ayarı `Required Public`ve hem `DataClasses` hem de `DataClasses.ViewModels` içindeki her şey `All`olur.

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

### <a name="if-open-generics-and-instantiated-elements-apply-the-same-policy-type"></a>Açık genel türler ve örneklenmiş öğeler aynı ilke türünü uygular

Aşağıdaki örnekte, `Dictionary<int,int>` `Browse` ilkesine yalnızca altyapının, bu bileşene `Browse` ilkesi (Aksi takdirde varsayılan davranış) izin vermek için başka bir nedeni varsa atanır; <xref:System.Collections.Generic.Dictionary%602> diğer tüm örneklemelerinden tüm üyeleri gözatılabilir.

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

### <a name="how-policy-is-inferred"></a>İlke nasıl algılanır

Her ilke türünün, bu ilke türü varlığının diğer yapıları nasıl etkilediğini tespit eden farklı kurallar kümesi vardır.

#### <a name="the-effect-of-browse-policy"></a>Tarayıcı ilkesinin etkisi

`Browse` ilkesinin bir türe uygulanması aşağıdaki ilke değişikliklerini içerir:

- Türün temel türü `Browse` ilkesiyle işaretlenir.

- Tür bir genel ise, türün örneklenmemiş sürümü `Browse` ilkesiyle işaretlenir.

- Tür bir temsilciyiyise, türdeki `Invoke` yöntemi `Dynamic` ilkesiyle işaretlenir.

- Türün her arabirimi `Browse` ilkesiyle işaretlenir.

- Türe uygulanan her bir özniteliğin türü `Browse` ilkesiyle işaretlenir.

- Tür geneldir ise, her kısıtlama türü `Browse` ilkesiyle işaretlenir.

- Tür geneldir ise, türün örneklendiği türler `Browse` ilkesiyle işaretlenir.

`Browse` ilkesinin bir yönteme uygulanması aşağıdaki ilke değişikliklerini içerir:

- Yöntemin her bir parametre türü `Browse` ilkesiyle işaretlenir.

- Metodun dönüş türü `Browse` ilkesiyle işaretlenir.

- Yöntemin kapsayan türü `Browse` ilkesiyle işaretlenir.

- Yöntem örneklenmiş genel bir yöntem ise, örneklenmemiş genel yöntem `Browse` ilkesiyle işaretlenir.

- Yöntemine uygulanan her bir özniteliğin türü `Browse` ilkesiyle işaretlenir.

- Yöntem geneldir ise, her kısıtlama türü `Browse` ilkesiyle işaretlenir.

- Yöntem genel ise, yöntemin örneklendiği türler `Browse` ilkesiyle işaretlenir.

`Browse` ilkesinin bir alana uygulanması aşağıdaki ilke değişikliklerini içerir:

- Alana uygulanan her bir özniteliğin türü `Browse` ilkesiyle işaretlenir.

- Alanın türü `Browse` ilkesiyle işaretlenir.

- Alanın ait olduğu tür `Browse` ilkesiyle işaretlenir.

#### <a name="the-effect-of-dynamic-policy"></a>Dinamik ilkenin etkisi

`Dynamic` ilkesinin bir türe uygulanması aşağıdaki ilke değişikliklerini içerir:

- Türün temel türü `Dynamic` ilkesiyle işaretlenir.

- Tür bir genel ise, türün örneklenmemiş sürümü `Dynamic` ilkesiyle işaretlenir.

- Tür bir temsilci türü ise, türdeki `Invoke` yöntemi `Dynamic` ilkesiyle işaretlenir.

- Türün her arabirimi `Browse` ilkesiyle işaretlenir.

- Türe uygulanan her bir özniteliğin türü `Browse` ilkesiyle işaretlenir.

- Tür geneldir ise, her kısıtlama türü `Browse` ilkesiyle işaretlenir.

- Tür geneldir ise, türün örneklendiği türler `Browse` ilkesiyle işaretlenir.

`Dynamic` ilkesinin bir yönteme uygulanması aşağıdaki ilke değişikliklerini içerir:

- Yöntemin her bir parametre türü `Browse` ilkesiyle işaretlenir.

- Metodun dönüş türü `Dynamic` ilkesiyle işaretlenir.

- Yöntemin kapsayan türü `Dynamic` ilkesiyle işaretlenir.

- Yöntem örneklenmiş genel bir yöntem ise, örneklenmemiş genel yöntem `Browse` ilkesiyle işaretlenir.

- Yöntemine uygulanan her bir özniteliğin türü `Browse` ilkesiyle işaretlenir.

- Yöntem geneldir ise, her kısıtlama türü `Browse` ilkesiyle işaretlenir.

- Yöntem genel ise, yöntemin örneklendiği türler `Browse` ilkesiyle işaretlenir.

- Yöntemi `MethodInfo.Invoke`tarafından çağrılabilir ve temsilci oluşturma <xref:System.Reflection.MethodInfo.CreateDelegate%2A?displayProperty=nameWithType>tarafından mümkün hale gelir.

`Dynamic` ilkesinin bir alana uygulanması aşağıdaki ilke değişikliklerini içerir:

- Alana uygulanan her bir özniteliğin türü `Browse` ilkesiyle işaretlenir.

- Alanın türü `Dynamic` ilkesiyle işaretlenir.

- Alanın ait olduğu tür `Dynamic` ilkesiyle işaretlenir.

#### <a name="the-effect-of-activation-policy"></a>Etkinleştirme ilkesinin etkisi

Etkinleştirme ilkesini bir türe uygulamak aşağıdaki ilke değişikliklerini içerir:

- Tür bir genel ise, türün örneklenmemiş sürümü `Browse` ilkesiyle işaretlenir.

- Tür bir temsilci türü ise, türdeki `Invoke` yöntemi `Dynamic` ilkesiyle işaretlenir.

- Türün oluşturucuları `Activation` ilkesiyle işaretlenir.

`Activation` ilkesinin bir yönteme uygulanması aşağıdaki ilke değişikliğini içerir:

- Oluşturucu <xref:System.Reflection.ConstructorInfo.Invoke%2A?displayProperty=nameWithType> ve <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> yöntemlerle çağrılabilir. Yöntemler için `Activation` ilkesi yalnızca oluşturucuları etkiler.

`Activation` ilkesinin bir alana uygulanması etkisizdir.

#### <a name="the-effect-of-serialize-policy"></a>Seri hale getirme ilkesinin etkisi

`Serialize` ilkesi, yaygın yansıma tabanlı serileştiricilerin kullanımını sunar. Ancak, Microsoft dışı serileştiricilerin tam yansıma erişimi desenleri Microsoft tarafından bilinmediğinden, bu ilke tamamen etkili olmayabilir.

`Serialize` ilkesinin bir türe uygulanması aşağıdaki ilke değişikliklerini içerir:

- Türün temel türü `Serialize` ilkesiyle işaretlenir.

- Tür bir genel ise, türün örneklenmemiş sürümü `Browse` ilkesiyle işaretlenir.

- Tür bir temsilci türü ise, türdeki `Invoke` yöntemi `Dynamic` ilkesiyle işaretlenir.

- Tür bir sabit listesi ise, türün bir dizisi `Serialize` ilkesiyle işaretlenir.

- Tür <xref:System.Collections.Generic.IEnumerable%601>uygularsa, `T` `Serialize` ilkesiyle işaretlenir.

- Tür <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.Generic.IList%601>, <xref:System.Collections.Generic.ICollection%601>, <xref:System.Collections.Generic.IReadOnlyCollection%601>veya <xref:System.Collections.Generic.IReadOnlyList%601>, `T[]` ve <xref:System.Collections.Generic.List%601> `Serialize` ilkeyle işaretlenir. ancak, arabirim türünün hiçbir üyesi `Serialize` ilkesiyle işaretlenir.

- Tür <xref:System.Collections.Generic.List%601>ise, türün hiçbir üyesi `Serialize` ilkesiyle işaretlenir.

- Tür <xref:System.Collections.Generic.IDictionary%602>ise, <xref:System.Collections.Generic.Dictionary%602> `Serialize` ilkesiyle işaretlenir. Ancak türdeki hiçbir üye `Serialize` ilkesiyle işaretlenir.

- Tür <xref:System.Collections.Generic.Dictionary%602>ise, türün hiçbir üyesi `Serialize` ilkesiyle işaretlenir.

- Tür <xref:System.Collections.Generic.IDictionary%602>uygularsa `TKey` ve `TValue` `Serialize` ilkesiyle işaretlenir.

- Her bir Oluşturucu, her özellik erişimcisi ve her bir alan `Serialize` ilkesiyle işaretlenir.

`Serialize` ilkesinin bir yönteme uygulanması aşağıdaki ilke değişikliklerini içerir:

- Kapsayan tür `Serialize` ilkesiyle işaretlenir.

- Metodun dönüş türü `Serialize` ilkesiyle işaretlenir.

`Serialize` ilkesinin bir alana uygulanması aşağıdaki ilke değişikliklerini içerir:

- Kapsayan tür `Serialize` ilkesiyle işaretlenir.

- Alanın türü `Serialize` ilkesiyle işaretlenir.

#### <a name="the-effect-of-xmlserializer-datacontractserializer-and-datacontractjsonserializer-policies"></a>XmlSerializer, DataContractSerializer ve DataContractJsonSerializer ilkelerinin etkisi

Yansıma tabanlı serileştiriciler için tasarlanan `Serialize` ilkesinin aksine, .NET Native araç zinciri tarafından bilinen serileştiriciler kümesini etkinleştirmek için <xref:System.Xml.Serialization.XmlSerializer>, <xref:System.Runtime.Serialization.DataContractSerializer>ve <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> ilkeleri kullanılır. Bu serileştiriciler yansıma kullanılarak uygulanmaz, ancak çalışma zamanında seri hale getirilebildiğiniz türler kümesi, yansıma \ olan türler gibi benzer şekilde belirlenir.

Bu ilkelerin bir türe uygulanması, türün eşleşen serileştirici ile serileştirilmesine olanak sağlar. Ayrıca, serileştirme altyapısının serileştirilmesi gereken şekilde statik olarak belirleyebilmesi için herhangi bir tür de serileştirilebilir olur.

Bu ilkelerin Yöntemler veya alanlar üzerinde hiçbir etkisi yoktur.

Daha fazla bilgi için [Windows mağazası uygulamanızı .NET Native geçirme](migrating-your-windows-store-app-to-net-native.md)konusunun "Serileştiricilerle ilgili farklılıklar" bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma Zamanı Yönerge Öğeleri](runtime-directive-elements.md)
- [Yansıma ve .NET Native](reflection-and-net-native.md)
