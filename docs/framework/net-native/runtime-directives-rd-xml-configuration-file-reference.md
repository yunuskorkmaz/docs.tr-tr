---
title: Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu
ms.date: 03/30/2017
ms.assetid: 8241523f-d8e1-4fb6-bf6a-b29bfe07b38a
ms.openlocfilehash: e74d34693446cca645003a9f93bc1777849e3182
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
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

Bir [kitaplık](library-element-net-native.md) öğesi, `Name` dosya uzantısı olmadan bir kitaplığın veya derlemenin adını belirten tek bir özniteliğe sahiptir. Örneğin, aşağıdaki [kitaplık](library-element-net-native.md) öğesi Extensions. dll adlı bir derleme için geçerlidir.

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

[Uygulama](application-element-net-native.md) öğesinin kendisi ve [kitaplık](library-element-net-native.md) ve [uygulama](application-element-net-native.md) öğeleri Express ilkesinin alt öğeleri; diğer bir deyişle, bir uygulamanın bir program öğesine yansıma uygulayabileceği şekilde tanımlar. İlke türü, öğesinin bir özniteliği tarafından tanımlanır (örneğin, `Serialize` ). İlke değeri özniteliğin değeri (örneğin,) tarafından tanımlanır `Serialize="Required"` .

Bir öğenin özniteliği tarafından belirtilen herhangi bir ilke, bu ilke için bir değer belirtmeyen tüm alt öğeler için geçerlidir. Örneğin, bir ilke bir [tür](type-element-net-native.md) öğesiyle belirtilmişse, bu ilke, bir ilkenin açıkça belirtilmediği tüm içerilen türler ve Üyeler için geçerlidir.

[Uygulama](application-element-net-native.md), [derleme](assembly-element-net-native.md), [attributeby](attributeimplies-element-net-native.md), [Namespace](namespace-element-net-native.md), alt [türler](subtypes-element-net-native.md)ve [tür](type-element-net-native.md) öğeleri tarafından Ifade edilen ilke, ayrı Üyeler Için ifade edilebilir ilkeden farklıdır ( [Yöntem](method-element-net-native.md), [özellik](property-element-net-native.md), [alan](field-element-net-native.md)ve [olay](event-element-net-native.md) öğeleri tarafından).

### <a name="specifying-policy-for-assemblies-namespaces-and-types"></a>Derlemeler, ad alanları ve türler için ilke belirtme

[Uygulama](application-element-net-native.md), [derleme](assembly-element-net-native.md), [attributeme](attributeimplies-element-net-native.md), [Namespace](namespace-element-net-native.md), alt [türleri](subtypes-element-net-native.md)ve [tür](type-element-net-native.md) öğeleri aşağıdaki ilke türlerini destekler:

- `Activate`. Örneklerin etkinleştirilmesini sağlamak için oluşturuculara çalışma zamanı erişimini denetler.

- `Browse`. Program öğeleri hakkında bilgi sorgulamayı denetler, ancak hiçbir çalışma zamanı erişimini etkinleştirmez.

- `Dynamic`. Dinamik programlamayı etkinleştirmek için oluşturucular, Yöntemler, alanlar, Özellikler ve olaylar dahil olmak üzere tüm tür üyelerine çalışma zamanı erişimini denetler.

- `Serialize`. Tür örneklerinin, Newtonsoft JSON serileştirici gibi üçüncü taraf kitaplıklara serileştirilmesi ve serileştirilmesi için oluşturuculara, alanlara ve özelliklere çalışma zamanı erişimini denetler.

- `DataContractSerializer`. Sınıfını kullanan serileştirme için ilkeyi denetler <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> .

- `DataContractJsonSerializer`. Sınıfını kullanan JSON serileştirme için ilkeyi denetler <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> .

- `XmlSerializer`. Sınıfını kullanan XML serileştirme ilkesini denetler <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> .

- `MarshalObject`. WinRT ve COM 'a başvuru türlerini hazırlama ilkesini denetler.

- `MarshalDelegate`. Temsilci türlerini yerel koda işlev işaretçileri olarak hazırlama ilkesini denetler.

- `MarshalStructure` . Yapıları yerel koda hazırlama ilkesini denetler.

Bu ilke türleriyle ilişkili ayarlar şunlardır:

- `All`. Araç zincirinin kaldıramayan tüm türler ve Üyeler için ilkeyi etkinleştirin.

- `Auto`. Varsayılan davranışı kullanın. (İlke belirtilmemeksizin `Auto` , ilke geçersiz kılınmadıkça, örneğin bir üst öğe ile, bu ilkeyi ayarlamaya eşdeğerdir.)

- `Excluded`. Program öğesi için ilkeyi devre dışı bırakın.

- `Public`. Araç zinciri üyenin gereksiz olduğunu belirlerse ve bu nedenle uygulamayı kaldırmadığı müddetçe ortak türler veya Üyeler için ilkeyi etkinleştirin. (İkinci durumda, `Required Public` üyenin tutulduğundan ve yansıma özelliklerine sahip olduğundan emin olmak için kullanmanız gerekir.)

- `PublicAndInternal`. Araç zinciri onları kaldırmazsa ortak ve iç türler veya Üyeler için ilkeyi etkinleştirin.

- `Required Public`. Ortak türleri ve üyeleri, kullanıldıkları ve kullanılmayacağı gibi tutmak ve ilke için etkinleştirmek üzere araç zinciri gerektirir.

- `Required PublicAndInternal`. Araç zincirinin hem ortak hem de iç türleri ve üyeleri, kullanılmalarına bakılmaksızın ve bunları kendileri için etkinleştirin.

- `Required All`. Araç zincirinin tüm türleri ve üyeleri kullanıp kullanmadığını ve bunların kullanılmadığını ve ilke için etkin olmasını gerektir.

Örneğin, aşağıdaki çalışma zamanı yönergeleri dosyası, veri sınıfları. dll dosyasındaki tüm türler ve Üyeler için ilkeyi tanımlar. Tüm ortak özelliklerin serileştirilmesi için yansıma kullanımını, tüm türler ve tür üyeleri için gözatmayı etkinleştirmek, tüm türler için etkinleştirmeyi etkinleştirmek ( `Dynamic` özniteliği nedeniyle) ve tüm genel türler ve Üyeler için yansıma 'yi etkinleştirmek.

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

- `Browse`-Bu üye hakkında bilgi sorgulamayı denetler, ancak hiçbir çalışma zamanı erişimini etkinleştirmez.

- `Dynamic`-Dinamik programlamayı etkinleştirmek için oluşturucular, Yöntemler, alanlar, Özellikler ve olaylar dahil olmak üzere tüm tür üyelerine çalışma zamanı erişimini denetler. Ayrıca, kapsayan tür hakkındaki bilgileri sorgulamayı denetler.

- `Serialize`-Tür örneklerinin, Newtonsoft JSON serileştirici gibi kitaplıklar tarafından serileştirilmesi ve seri durumdan çıkarılmakta olması için üyeye çalışma zamanı erişimini denetler. Bu ilke oluşturucular, alanlar ve özelliklere uygulanabilir.

[Yöntemi](method-element-net-native.md) ve [olay](event-element-net-native.md) öğeleri aşağıdaki ilke türlerini destekler:

- `Browse`-Bu üye hakkında bilgi sorgulamayı denetler, ancak hiçbir çalışma zamanı erişimini etkinleştirmez.

- `Dynamic`-Dinamik programlamayı etkinleştirmek için oluşturucular, Yöntemler, alanlar, Özellikler ve olaylar dahil olmak üzere tüm tür üyelerine çalışma zamanı erişimini denetler. Ayrıca, kapsayan tür hakkındaki bilgileri sorgulamayı denetler.

 Bu ilke türleriyle ilişkili ayarlar şunlardır:

- `Auto`-Varsayılan davranışı kullanın. (Bir ilke belirtmeksizin, bir `Auto` öğe geçersiz kılınmadığı takdirde bu ilkeyi ayarlamaya eşdeğerdir.)

- `Excluded`-Üyenin meta verilerini hiçbir şekilde eklemeyin.

- `Included`-Üst tür çıktıda varsa ilkeyi etkinleştirin.

- `Required`-Araç zincirinin, kullanılmamış gibi görünse bile bu üyeyi tutması gerekir ve ilkeyi etkinleştirir.

## <a name="runtime-directives-file-semantics"></a>Çalışma zamanı yönergeleri dosya semantiği

İlke, hem daha yüksek hem de alt düzey öğeler için eşzamanlı olarak tanımlanabilir. Örneğin, ilke bir derleme için ve bu derlemede yer alan bazı türler için tanımlanabilir. Belirli bir alt düzey öğe gösterilmediğinden, üst öğesinin ilkesini devralır. Örneğin, bir `Assembly` öğe mevcutsa ancak `Type` öğeler yoksa, öğesinde belirtilen ilke `Assembly` derlemedeki her tür için geçerlidir. Aynı program öğesine aynı zamanda birden çok öğe ilke uygulayabilir. Örneğin, ayrı [derleme](assembly-element-net-native.md) öğeleri aynı derleme için aynı ilke öğesini farklı şekilde tanımlayabilir. Aşağıdaki bölümlerde, belirli bir türün ilkesinin bu durumlarda nasıl çözümlendiğini açıklanmaktadır.

Genel bir türün veya yöntemin [tür](type-element-net-native.md) veya [Yöntem](method-element-net-native.md) öğesi, kendi ilkesi olmayan tüm örneklemelerde ilkesini uygular. Örneğin, `Type` ilkesini belirten bir öğe, belirli bir <xref:System.Collections.Generic.List%601> oluşturulan genel tür için geçersiz kılınmadığı sürece (örneğin, bir `List<Int32>` öğesi tarafından), bu genel türün tüm oluşturulan örneklerine uygulanır `TypeInstantiation` . Aksi takdirde, öğeleri adlı program öğesi için ilkeyi tanımlar.

Bir öğe belirsiz olduğunda, motor eşleşme arar ve tam eşleşme bulursa onu kullanacaktır. Birden çok eşleşme bulunursa bir uyarı veya hata olur.

### <a name="if-two-directives-apply-policy-to-the-same-program-element"></a>İki yönergeler aynı program öğesine ilke uygualıyorsa

Farklı çalışma zamanı yönergeleri dosyalarındaki iki öğe aynı program öğesi (bir derleme veya tür gibi) için aynı ilke türünü farklı değerlere ayarlamaya çalışıyorsa, çakışma aşağıdaki gibi çözümlenir:

1. `Excluded`Öğe varsa, önceliğe sahip olur.

2. `Required`, öğesinden önceliklidir `Required` .

3. `All`önceliğe sahip olan `PublicAndInternal` , önceliği olan `Public` .

4. Herhangi bir açık ayar önceliklidir `Auto` .

Örneğin, tek bir proje aşağıdaki iki çalışma zamanı yönergeleri dosyasını içeriyorsa, DataClasses. dll serileştirme ilkesi hem hem de olarak ayarlanır `Required Public` `All` . Bu durumda, serileştirme ilkesi olarak çözümlenir `Required All` .

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

Alt öğeler, ayarı da dahil olmak üzere üst öğelerini geçersiz kılar `Excluded` . Geçersiz kılma, belirtmek istediğiniz ana nedendir `Auto` .

Aşağıdaki örnekte, içinde olmayan her şey için serileştirme ilkesi ayarı `DataClasses` `DataClasses.ViewModels` , ve `Required Public` her ikisinde de olan her şey olacaktır `DataClasses` `DataClasses.ViewModels` `All` .

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

Aşağıdaki örnekte, `Dictionary<int,int>` `Browse` ilke yalnızca altyapının ilkeyi vermesi için başka bir nedeniniz varsa `Browse` (Aksi takdirde varsayılan davranış olur), ' ın her bir örneği için <xref:System.Collections.Generic.Dictionary%602> tüm üyeleri göz atılamaz olur.

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

`Browse`İlkeyi bir türe uygulamak aşağıdaki ilke değişikliklerini içerir:

- Türün temel türü `Browse` ilkeyle işaretlenir.

- Tür bir genel ise, türün örneklenmemiş sürümü `Browse` ilkeyle işaretlenir.

- Tür bir `Invoke` temsilciyise, türdeki yöntem `Dynamic` ilkeyle işaretlenir.

- Türün her arabirimi `Browse` ilkeyle işaretlenir.

- Türe uygulanan her bir özniteliğin türü `Browse` ilkeyle işaretlenir.

- Tür geneldir ise, her kısıtlama türü `Browse` ilkeyle işaretlenir.

- Tür geneldir ise, türün örneklendiği türler `Browse` ilkeyle işaretlenir.

`Browse`İlkeyi bir yönteme uygulamak aşağıdaki ilke değişikliklerini içerir:

- Yöntemin her bir parametre türü `Browse` ilkeyle işaretlenir.

- Metodun dönüş türü `Browse` ilkeyle işaretlenir.

- Yöntemin kapsayan türü `Browse` ilkeyle işaretlenir.

- Yöntem, örneklenmiş genel bir yöntem ise, örneklenmiş genel yöntem `Browse` ilkeyle işaretlenir.

- Yöntemine uygulanan her bir özniteliğin türü `Browse` ilkeyle işaretlenir.

- Yöntem geneldir ise, her kısıtlama türü `Browse` ilkeyle işaretlenir.

- Yöntem genel ise, yöntemin örneklendiği türler `Browse` ilkeyle işaretlenir.

`Browse`İlkeyi bir alana uygulamak aşağıdaki ilke değişikliklerini içerir:

- Alana uygulanan her bir özniteliğin türü `Browse` ilkeyle işaretlenir.

- Alanın türü `Browse` ilkeyle işaretlenir.

- Alanın ait olduğu tür `Browse` ilkeyle işaretlenir.

#### <a name="the-effect-of-dynamic-policy"></a>Dinamik ilkenin etkisi

`Dynamic`İlkeyi bir türe uygulamak aşağıdaki ilke değişikliklerini içerir:

- Türün temel türü `Dynamic` ilkeyle işaretlenir.

- Tür bir genel ise, türün örneklenmemiş sürümü `Dynamic` ilkeyle işaretlenir.

- Tür bir temsilci türü ise, `Invoke` türdeki yöntem `Dynamic` ilkeyle işaretlenir.

- Türün her arabirimi `Browse` ilkeyle işaretlenir.

- Türe uygulanan her bir özniteliğin türü `Browse` ilkeyle işaretlenir.

- Tür geneldir ise, her kısıtlama türü `Browse` ilkeyle işaretlenir.

- Tür geneldir ise, türün örneklendiği türler `Browse` ilkeyle işaretlenir.

`Dynamic`İlkeyi bir yönteme uygulamak aşağıdaki ilke değişikliklerini içerir:

- Yöntemin her bir parametre türü `Browse` ilkeyle işaretlenir.

- Metodun dönüş türü `Dynamic` ilkeyle işaretlenir.

- Yöntemin kapsayan türü `Dynamic` ilkeyle işaretlenir.

- Yöntem, örneklenmiş genel bir yöntem ise, örneklenmiş genel yöntem `Browse` ilkeyle işaretlenir.

- Yöntemine uygulanan her bir özniteliğin türü `Browse` ilkeyle işaretlenir.

- Yöntem geneldir ise, her kısıtlama türü `Browse` ilkeyle işaretlenir.

- Yöntem genel ise, yöntemin örneklendiği türler `Browse` ilkeyle işaretlenir.

- Yöntemi tarafından çağrılabilir `MethodInfo.Invoke` ve temsilci oluşturma tarafından mümkün hale gelir <xref:System.Reflection.MethodInfo.CreateDelegate%2A?displayProperty=nameWithType> .

`Dynamic`İlkeyi bir alana uygulamak aşağıdaki ilke değişikliklerini içerir:

- Alana uygulanan her bir özniteliğin türü `Browse` ilkeyle işaretlenir.

- Alanın türü `Dynamic` ilkeyle işaretlenir.

- Alanın ait olduğu tür `Dynamic` ilkeyle işaretlenir.

#### <a name="the-effect-of-activation-policy"></a>Etkinleştirme ilkesinin etkisi

Etkinleştirme ilkesini bir türe uygulamak aşağıdaki ilke değişikliklerini içerir:

- Tür bir genel ise, türün örneklenmemiş sürümü `Browse` ilkeyle işaretlenir.

- Tür bir temsilci türü ise, `Invoke` türdeki yöntem `Dynamic` ilkeyle işaretlenir.

- Türün oluşturucuları `Activation` ilkeyle işaretlenir.

`Activation`İlkeyi bir yönteme uygulamak aşağıdaki ilke değişikliğini içerir:

- Oluşturucu <xref:System.Reflection.ConstructorInfo.Invoke%2A?displayProperty=nameWithType> ve yöntemleri tarafından çağrılabilir <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> . Yöntemler için, `Activation` ilke yalnızca oluşturucuları etkiler.

`Activation`İlkeyi bir alana uygulamak hiçbir etkiye sahip değildir.

#### <a name="the-effect-of-serialize-policy"></a>Seri hale getirme ilkesinin etkisi

`Serialize`İlke, yaygın yansıma tabanlı serileştiricilerin kullanımını sunar. Ancak, Microsoft dışı serileştiricilerin tam yansıma erişimi desenleri Microsoft tarafından bilinmediğinden, bu ilke tamamen etkili olmayabilir.

`Serialize`İlkeyi bir türe uygulamak aşağıdaki ilke değişikliklerini içerir:

- Türün temel türü `Serialize` ilkeyle işaretlenir.

- Tür bir genel ise, türün örneklenmemiş sürümü `Browse` ilkeyle işaretlenir.

- Tür bir temsilci türü ise, `Invoke` türdeki yöntem `Dynamic` ilkeyle işaretlenir.

- Tür bir sabit listesi ise, bir tür dizisi `Serialize` ilkeyle işaretlenir.

- Türü uygularsa <xref:System.Collections.Generic.IEnumerable%601> `T` `Serialize` ilkeyle işaretlenir.

- Türü,,, <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Collections.Generic.IList%601> <xref:System.Collections.Generic.ICollection%601> <xref:System.Collections.Generic.IReadOnlyCollection%601> , veya <xref:System.Collections.Generic.IReadOnlyList%601> , `T[]` <xref:System.Collections.Generic.List%601> `Serialize` ilkesiyle işaretlenir., ancak arabirim türünün hiçbir üyesi `Serialize` ilkeyle işaretlenir.

- Tür ise, bu <xref:System.Collections.Generic.List%601> tür hiçbir üye `Serialize` ilkeyle işaretlenir.

- Tür ise <xref:System.Collections.Generic.IDictionary%602> <xref:System.Collections.Generic.Dictionary%602> `Serialize` ilkeyle işaretlenir. Ancak, türdeki hiçbir üye `Serialize` ilkeyle işaretlenir.

- Tür ise, bu <xref:System.Collections.Generic.Dictionary%602> tür hiçbir üye `Serialize` ilkeyle işaretlenir.

- Türü uygularsa <xref:System.Collections.Generic.IDictionary%602> `TKey` ve `TValue` `Serialize` ilkeyle işaretlenir.

- Her bir Oluşturucu, her özellik erişimcisi ve her bir alan `Serialize` ilkeyle işaretlenir.

`Serialize`İlkeyi bir yönteme uygulamak aşağıdaki ilke değişikliklerini içerir:

- Kapsayan tür `Serialize` ilkeyle işaretlenir.

- Metodun dönüş türü `Serialize` ilkeyle işaretlenir.

`Serialize`İlkeyi bir alana uygulamak aşağıdaki ilke değişikliklerini içerir:

- Kapsayan tür `Serialize` ilkeyle işaretlenir.

- Alanın türü `Serialize` ilkeyle işaretlenir.

#### <a name="the-effect-of-xmlserializer-datacontractserializer-and-datacontractjsonserializer-policies"></a>XmlSerializer, DataContractSerializer ve DataContractJsonSerializer ilkelerinin etkisi

`Serialize`Yansıma tabanlı serileştiriciler için tasarlanan ilkenin aksine,, <xref:System.Xml.Serialization.XmlSerializer> <xref:System.Runtime.Serialization.DataContractSerializer> ve <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> ilkeleri .NET Native araç zinciri tarafından bilinen bir seri hale getiriciler kümesini etkinleştirmek için kullanılır. Bu serileştiriciler yansıma kullanılarak uygulanmaz, ancak çalışma zamanında seri hale getirilebildiğiniz türler kümesi, yansıma \ olan türler gibi benzer şekilde belirlenir.

Bu ilkelerin bir türe uygulanması, türün eşleşen serileştirici ile serileştirilmesine olanak sağlar. Ayrıca, serileştirme altyapısının serileştirilmesi gereken şekilde statik olarak belirleyebilmesi için herhangi bir tür de serileştirilebilir olur.

Bu ilkelerin Yöntemler veya alanlar üzerinde hiçbir etkisi yoktur.

Daha fazla bilgi için [Windows mağazası uygulamanızı .NET Native geçirme](migrating-your-windows-store-app-to-net-native.md)konusunun "Serileştiricilerle ilgili farklılıklar" bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma Zamanı Yönerge Öğeleri](runtime-directive-elements.md)
- [Yansıma ve .NET Yerel](reflection-and-net-native.md)
