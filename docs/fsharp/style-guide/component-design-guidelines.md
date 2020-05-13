---
title: F# bileşen tasarımı yönergeleri
description: 'Diğer çağıranlar tarafından tüketim için tasarlanan F # bileşenlerini yazma yönergelerini öğrenin.'
ms.date: 05/14/2018
ms.openlocfilehash: 590bda0660d54ea73c590d31e694f3d499e0fd9f
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209142"
---
# <a name="f-component-design-guidelines"></a>F# bileşen tasarımı yönergeleri

Bu belge f # programlamasında, f # bileşeni tasarım yönergeleri, v14, Microsoft Research ve F # Software Foundation tarafından oluşturulan ve korunan bir sürümü temel alan bir bileşen tasarım yönergeleri kümesidir.

Bu belge, F # programlama hakkında bilgi sahibi olduğunuzu varsayar. Birçok, bu kılavuzun çeşitli sürümleriyle ilgili katkılarına ve yararlı bildirimlere yönelik olarak F # topluluğu için teşekkürler.

## <a name="overview"></a>Genel Bakış

Bu belge F # bileşen tasarımı ve kodlama ile ilgili bazı sorunları inceler. Bir bileşen, aşağıdakilerden herhangi biri anlamına gelebilir:

* F # projenizdeki, bu proje içinde harici tüketicilerle olan bir katman.
* Derleme sınırları genelinde F # kodu tarafından tüketime için tasarlanan bir kitaplık.
* Derleme sınırları genelinde herhangi bir .NET dili tarafından tüketimine yönelik bir kitaplık.
* [NuGet](https://nuget.org)gibi bir paket deposu aracılığıyla dağıtıma yönelik bir kitaplık.

Bu makalede açıklanan teknikler, [Iyi F # kodunun beş prensipini](index.md#five-principles-of-good-f-code)izler ve bu nedenle hem işlevsel hem de nesne programlamayı uygun şekilde kullanır.

Metodolojiden bağımsız olarak, bileşen ve kitaplık Tasarımcısı, geliştiriciler tarafından en kolay şekilde kullanılabilen bir API 'yi oluşturmaya çalışırken bir dizi pratik ve prosaic sorunu ortaya yayınlar. [.NET kitaplığı tasarım yönergelerinden](../../standard/design-guidelines/index.md) oluşan yarışma, kullanım açısından uygun olan tutarlı bir API kümesi oluşturmak için size yardımcı olacaktır.

## <a name="general-guidelines"></a>Genel yönergeler

Kitaplık için amaçlanan kitleden bağımsız olarak F # kitaplıkları için uygulanan birkaç evrensel yönerge vardır.

### <a name="learn-the-net-library-design-guidelines"></a>.NET kitaplığı tasarım yönergelerini öğrenin

Yaptığınız F # kodlamasının türü ne olursa olsun, [.NET kitaplığı tasarım yönergeleriyle](../../standard/design-guidelines/index.md)çalışan bir bilgiye sahip olmak önemlidir. Diğer tüm F # ve .NET programcılarının çoğu bu kılavuzla tanıdık gelecektir ve .NET kodunun bunlara uymasını bekler.

.NET kitaplığı tasarım yönergeleri, adlandırma, sınıfları ve arabirimleri tasarlama, üye tasarımı (özellikler, Yöntemler, olaylar, vb.) ve daha fazlası ile ilgili genel yönergeler sağlar ve çeşitli tasarım kılavuzlarından oluşan yararlı bir ilk başvuru noktasıdır.

### <a name="add-xml-documentation-comments-to-your-code"></a>Kodunuza XML belge açıklamaları ekleme

Ortak API 'lerde XML belgeleri, kullanıcıların bu türleri ve üyeleri kullanırken harika IntelliSense ve QuickInfo almasını ve kitaplık için belge dosyaları oluşturmayı etkinleştirmesini sağlar. XmlDoc açıklamaları içinde ek biçimlendirme için kullanılabilecek çeşitli XML etiketleri hakkında [XML belgelerine](../language-reference/xml-documentation.md) bakın.

```fsharp
/// A class for representing (x,y) coordinates
type Point =

    /// Computes the distance between this point and another
    member DistanceTo: otherPoint:Point -> float
```

Kısa form XML açıklamalarını ( `/// comment` ) ya da standart XML açıklamalarını ( `///<summary>comment</summary>` ) kullanabilirsiniz.

### <a name="consider-using-explicit-signature-files-fsi-for-stable-library-and-component-apis"></a>Kararlı kitaplık ve bileşen API 'Leri için açık imza dosyaları (. fsi) kullanmayı düşünün

Bir F # kitaplığındaki açık imzalar dosyalarının kullanılması, genel API 'nin kısa bir özetini sağlar. Bu, kitaplığınızın tam genel yüzeyini bilmenizi sağlamaya yardımcı olur ve ortak belgeler ile iç uygulama ayrıntıları arasında temiz bir ayrım sağlar. İmza dosyaları, hem uygulama hem de imza dosyalarında değişiklik yapılmasını gerektiren ortak API 'yi değiştirmeye yönelik uçuşmayı ekler. Sonuç olarak, imza dosyaları genellikle yalnızca bir API 'nin tahmin edildiğinde ve önemli ölçüde değişmemesi beklendiğinde tanıtılmalıdır.

### <a name="always-follow-best-practices-for-using-strings-in-net"></a>.NET 'teki dizeleri kullanmak için her zaman en iyi uygulamaları izleyin

[.Net Kılavuzu 'Nda dizeleri kullanmak Için En Iyi uygulamaları](../../standard/base-types/best-practices-strings.md) izleyin. Özellikle, dizelerin dönüştürülmesine ve karşılaştırmasına göre (uygulanabilir olduğunda) her zaman açık bir *şekilde eyalet.*

## <a name="guidelines-for-f-facing-libraries"></a>F # ile bağlantılı kitaplıklar için yönergeler

Bu bölümde, genel F # ile ilgili kitaplıkların geliştirilmesi için öneriler sunulmaktadır; diğer bir deyişle, F # geliştiricileri tarafından tüketilmesi amaçlanan genel API 'Leri kullanıma sunan kitaplıklardır. Özellikle F # için geçerli olan çok sayıda kitaplık tasarımı önerisi vardır. Aşağıdaki belirli önerilerin yokluğunda, .NET kitaplığı tasarım yönergeleri, geri dönüş kılavuzluğu ' dir.

### <a name="naming-conventions"></a>Adlandırma kuralları

#### <a name="use-net-naming-and-capitalization-conventions"></a>.NET adlandırma ve büyük/küçük harf kuralları kullanma

Aşağıdaki tabloda .NET adlandırma ve büyük/küçük harf kuralları yer verilmiştir. F # yapılarını da içeren küçük eklemeler vardır.

| Oluştur | Case (Olay) | Bölüm | Örnekler | Notlar |
|-----------|------|------|----------|-------|
| Somut türler | PascalCase | Ad/sıfatıcı | List, Double, Complex | Somut türler yapılar, sınıflar, numaralandırmalar, temsilciler, kayıtlar ve birleşimler. Tür adları OCaml 'de geleneksel olarak küçük olsa da, F # türler için .NET adlandırma şemasını benimsemiştir.
| DLL'ler           | PascalCase |                 | Fabrikam. Core. dll |  |
| Birleşim etiketleri     | PascalCase | İsim | Bazıları, ekleme, başarı | Genel API 'lerde bir ön ek kullanmayın. İsteğe bağlı olarak, iç zaman bir önek kullanın, örneğin`type Teams = TAlpha | TBeta | TDelta.` |
| Olay          | PascalCase | Fiil | ValueChanged/ValueChanging |  |
| Özel durumlar     | PascalCase |      | Gönderdi | Ad "Exception" ile bitmelidir. |
| Alan          | PascalCase | İsim | CurrentName  | |
| Arabirim türleri |  PascalCase | Ad/sıfatıcı | IDisposable | Ad "I" ile başlamalıdır. |
| Yöntem |  PascalCase |  Fiil | ToString | |
| Ad Alanı | PascalCase | | Microsoft. FSharp. Core | Genellikle `<Organization>.<Technology>[.<Subnamespace>]` teknolojisini kullanır, ancak teknolojinin kuruluştan bağımsız olması halinde organizasyonu bırakın. |
| Parametreler | camelCase | İsim |  typeName, Transform, Aralık | |
| izin ver (iç) | camelCase veya PascalCase | Ad/fiil |  getValue, myTable |
| değerlere izin ver (dış) | camelCase veya PascalCase | Ad/fiil  | List. map, tarihlere. bugün | daha geleneksel işlevsel tasarım desenleri aşağıdaki durumlarda, izin-bağlanacak değerler genellikle genel kullanıma açıktır. Ancak, tanımlayıcı diğer .NET dillerinden kullanılabilecek şekilde genellikle PascalCase kullanın. |
| Özellik  | PascalCase  | Ad/sıfatıcı  | Ienddoffile, BackColor  | Boolean özellikleri genellikle ' dir ve ' in IsNotEndOfFile değil, ıenddoffile dosyasında olduğu gibi, bunun da bir değerlendirme olması gerekir.

#### <a name="avoid-abbreviations"></a>Kısaltmaların önleyin

.NET yönergeleri kısaltmaların kullanımını önleyin (örneğin, " `OnButtonClick` yerine kullanın `OnBtnClick` "). `Async`"Zaman uyumsuz" gibi yaygın kısaltmalar toleranslı olarak sağlanır. Bu kılavuz bazen işlevsel programlama için yok sayılır; Örneğin, `List.iter` "ITERATE" için bir kısaltma kullanır. Bu nedenle, kısaltmaların kullanılması F #-to-F # programlamada daha büyük bir ölçüde toleranslı hale gelmelidir, ancak genel bileşen tasarımında yine de kaçınılmalıdır.

#### <a name="avoid-casing-name-collisions"></a>Büyük küçük harf çakışmalarını önleyin

.NET yönergeleri, bazı istemci dilleri (örneğin, Visual Basic) büyük/küçük harfe duyarsız olduğundan, tek başına büyük küçük harf olarak ad çakışmalarını ortadan kaldırmak için kullanılamaz.

#### <a name="use-acronyms-where-appropriate"></a>Uygun yerlerde kısaltmalar kullanın

XML gibi kısaltmalar kısaltmalar değildir ve .NET kitaplıklarında büyük harfli olmayan biçimde (XML) yaygın olarak kullanılır. Yalnızca iyi bilinen, yaygın olarak tanınan kısaltmalar kullanılmalıdır.

#### <a name="use-pascalcase-for-generic-parameter-names"></a>Genel parametre adları için PascalCase kullanın

F # kullanan kitaplıklar dahil genel API 'lerde genel parametre adları için PascalCase kullanın. Özellikle,,,,, `T` `U` `T1` `T2` rastgele genel parametreler için, ve belirli adların anlamlı olduğu durumlarda gibi adları kullanın, F # ile bağlantılı kitaplıklar için `Key` , `Value` `Arg` (örneğin, değil) adlarını kullanın `TKey` .

#### <a name="use-either-pascalcase-or-camelcase-for-public-functions-and-values-in-f-modules"></a>F # modüllerinde ortak işlevler ve değerler için PascalCase ya da camelCase kullanın

camelCase, nitelenmemiş kullanılacak şekilde tasarlanan (örneğin, `invalidArg` ) ve "Standart koleksiyon işlevleri" (örneğin, List. Map) için kullanılan genel işlevler için kullanılır. Bu iki durumda da işlev adları, dildeki anahtar sözcüklere çok benzer şekilde davranır.

### <a name="object-type-and-module-design"></a>Nesne, tür ve modül tasarımı

#### <a name="use-namespaces-or-modules-to-contain-your-types-and-modules"></a>Türlerinizi ve modüllerinizi içerecek şekilde ad alanlarını veya modülleri kullanın

Bir bileşendeki her F # dosyası, bir ad alanı bildirimiyle veya bir modül bildirimiyle başlamalıdır.

```fsharp
namespace Fabrikam.BasicOperationsAndTypes

type ObjectType1() =
    ...

type ObjectType2() =
     ...

module CommonOperations =
    ...
```

veya

```fsharp
module Fabrikam.BasicOperationsAndTypes

type ObjectType1() =
    ...

type ObjectType2() =
    ...

module CommonOperations =
    ...
```

En üst düzeyde kod düzenlemek için modüller ve ad alanları kullanma arasındaki farklar şunlardır:

* Ad alanları birden çok dosyaya yayılabilir
* Ad alanları, bir iç modül içinde olmadıkları müddetçe F # işlevleri içeremez
* Belirli bir modülün kodu tek bir dosya içinde bulunmalıdır
* Üst düzey modüller, bir iç modüle gerek olmadan F # işlevleri içerebilir

Üst düzey bir ad alanı veya modül arasındaki seçim, kodun derlenmiş biçimini etkiler ve bu nedenle API 'nizin sonunda F # kodu dışında tüketilmesi için diğer .NET dillerinden görünümü etkiler.

#### <a name="use-methods-and-properties-for-operations-intrinsic-to-object-types"></a>Nesne türlerine yönelik işlemler için yöntemleri ve özellikleri kullanın

Nesnelerle çalışırken, tüketilebilir işlevselliğin bu tür üzerinde Yöntemler ve özellikler olarak uygulandığından emin olmak en iyisidir.

```fsharp
type HardwareDevice() =

    member this.ID = ...

    member this.SupportedProtocols = ...

type HashTable<'Key,'Value>(comparer: IEqualityComparer<'Key>) =

    member this.Add(key, value) = ...

    member this.ContainsKey(key) = ...

    member this.ContainsValue(value) = ...
```

Belirli bir üye için işlevselliğin toplu olması, söz konusu üyeye uygulanmamalıdır, ancak söz konusu işlevin tüketilebilir olması gerekir.

#### <a name="use-classes-to-encapsulate-mutable-state"></a>Kesilebilir durumu kapsüllemek için sınıfları kullanma

F # ' da, bu durumun yalnızca bir kapanış, sıra ifadesi veya zaman uyumsuz hesaplama gibi başka bir dil yapısı tarafından kapsüllenmediğinden yapılması gerekir.

```fsharp
type Counter() =
    // let-bound values are private in classes.
    let mutable count = 0

    member this.Next() =
        count <- count + 1
        count
```

#### <a name="use-interfaces-to-group-related-operations"></a>İlgili işlemleri gruplamak için arabirimler kullanın

Bir dizi işlemi temsil etmek için arabirim türlerini kullanın. Bu, işlevlerin veya işlev kayıtlarının başlıkları gibi diğer seçeneklere tercih edilir.

```fsharp
type Serializer =
    abstract Serialize<'T>: preserveRefEq: bool -> value: 'T -> string
    abstract Deserialize<'T>: preserveRefEq: bool -> pickle: string -> 'T
```

Tercihe göre:

```fsharp
type Serializer<'T> = {
    Serialize: bool -> 'T -> string
    Deserialize: bool -> string -> 'T
}
```

Arabirimler, .NET 'teki birinci sınıf kavramlardır ve bu sayede, Funların normalde size nasıl sağlayabileceklerini elde edebilirsiniz. Ayrıca, varlıksal türlerini programınıza kodlamak için kullanılabilirler, bu da işlev kayıtları olamaz.

#### <a name="use-a-module-to-group-functions-that-act-on-collections"></a>Koleksiyonlar üzerinde hareket eden işlevleri gruplandırmak için bir modül kullanın

Bir koleksiyon türü tanımladığınızda, `CollectionType.map` `CollectionType.iter` Yeni koleksiyon türleri için ve gibi standart bir işlem kümesi sağlamayı düşünün.

```fsharp
module CollectionType =
    let map f c =
        ...
    let iter f c =
        ...
```

Böyle bir modül eklerseniz, FSharp. Core 'da bulunan işlevler için standart adlandırma kurallarını izleyin.

#### <a name="use-a-module-to-group-functions-for-common-canonical-functions-especially-in-math-and-dsl-libraries"></a>Özellikle matematik ve DSL kitaplıklarında ortak, kurallı işlevler için işlevleri gruplamak üzere bir modül kullanın

Örneğin, `Microsoft.FSharp.Core.Operators` `abs` `sin` FSharp. Core. dll tarafından belirtilen en üst düzey işlevlerin (ve gibi) otomatik olarak açılmış bir koleksiyonudur.

Benzer şekilde, bir istatistik kitaplığı işlevleri olan bir modül içerebilir `erf` ve `erfc` Bu modül açıkça veya otomatik olarak açılacak şekilde tasarlanmıştır.

#### <a name="consider-using-requirequalifiedaccess-and-carefully-apply-autoopen-attributes"></a>RequireQualifiedAccess kullanmayı düşünün ve oto aç özniteliklerini dikkatle uygulayın

`[<RequireQualifiedAccess>]`Özniteliği bir modüle eklemek, modülün açılamayabilir ve modülün öğelerine yapılan başvuruların açık nitelikli erişim gerektirdiğini gösterir. Örneğin, `Microsoft.FSharp.Collections.List` modülün bu özniteliği vardır.

Bu, modüldeki işlevlerin ve değerlerin diğer modüllerdeki adlarla çakışabilecek adlara sahip olduğu durumlarda faydalıdır. Tam erişim gerektirmek, bir kitaplığın uzun süreli bakım ve gelişmesini büyük ölçüde artırabilir.

`[<AutoOpen>]`Özniteliği bir modüle eklemek, kapsayan ad alanı açıldığında modülün açılıp açılmayacağı anlamına gelir. `[<AutoOpen>]`Özniteliği, derlemeye başvuruluyorsa otomatik olarak açılan bir modülü göstermek için bir derlemeye de uygulanabilir.

Örneğin, bir istatistik Kitaplığı **MathsHeaven. STATISTICS** bir `module MathsHeaven.Statistics.Operators` kapsayan işlevler `erf` ve içerebilir `erfc` . Bu modülün olarak işaretlenmesi mantıklıdır `[<AutoOpen>]` . Bu, `open MathsHeaven.Statistics` Ayrıca bu modülün açılacağı ve adları ve kapsamına getirecek anlamına gelir `erf` `erfc` . Uygulamasının başka bir kullanımı `[<AutoOpen>]` , uzantı yöntemleri içeren modüller içindir.

`[<AutoOpen>]`Kirletilmişti ad alanlarına müşteri adayları fazla kullanımı ve özniteliği dikkatli olarak kullanılmalıdır. Belirli etki alanlarındaki belirli kitaplıklar için, imdicemlik kullanımı `[<AutoOpen>]` daha iyi kullanılabilirlik elde edebilir.

#### <a name="consider-defining-operator-members-on-classes-where-using-well-known-operators-is-appropriate"></a>İyi bilinen işleçlerin kullanılması uygun olan sınıflarda işleç üyelerini tanımlamayı düşünün

Bazen sınıflar, vektör gibi matematik yapılarını modellemek için kullanılır. Modellenen etki alanının iyi bilinen işleçleri olduğunda, bunları sınıfa iç üye olarak tanımlamak faydalı olur.

```fsharp
type Vector(x: float) =

    member v.X = x

    static member (*) (vector: Vector, scalar: float) = Vector(vector.X * scalar)

    static member (+) (vector1: Vector, vector2: Vector) = Vector(vector1.X + vector2.X)

let v = Vector(5.0)

let u = v * 10.0
```

Bu kılavuz, bu türler için genel .NET yönergelerine karşılık gelir. Bununla birlikte, F # kodlamasına ek olarak da önemli olabilir. Bu, bu türlerin F # işlevleriyle ve List. sumBy gibi üye kısıtlamalarına sahip yöntemlerle birlikte kullanılmasına olanak tanır.

#### <a name="consider-using-compiledname-to-provide-a-net-friendly-name-for-other-net-language-consumers"></a>Bir sağlamak için CompiledName kullanmayı düşünün. Diğer .NET dil tüketicileri için NET-kolay ad

Bazen F # tüketicilerinin (modül bağlantılı işlevmiş gibi görünmesi için bir statik üye gibi) bir stili bir stil olarak adlandırmak isteyebilirsiniz, ancak bir derlemeye derlendiğinde ad için farklı bir stile sahip olabilirsiniz. `[<CompiledName>]`Derlemeyi kullanan F # olmayan kod için farklı bir stil sağlamak üzere özniteliğini kullanabilirsiniz.

```fsharp
type Vector(x:float, y:float) =

    member v.X = x
    member v.Y = y

    [<CompiledName("Create")>]
    static member create x y = Vector (x, y)

let v = Vector.create 5.0 3.0
```

Kullanarak `[<CompiledName>]` , derlemenin F # tüketicilerine yönelik .net adlandırma kurallarını kullanabilirsiniz.

#### <a name="use-method-overloading-for-member-functions-if-doing-so-provides-a-simpler-api"></a>Daha basit bir API sağlayan üye işlevleri için yöntem aşırı yüklemesini kullanın

Yöntem aşırı yüklemesi, farklı seçeneklerle veya bağımsız değişkenlerle benzer işlevler gerçekleştirmesi gerekebilecek bir API 'YI basitleştirmek için güçlü bir araçtır.

```fsharp
type Logger() =

    member this.Log(message) =
        ...
    member this.Log(message, retryPolicy) =
        ...
```

F # ' da, bağımsız değişken türleri yerine bağımsız değişken sayısında aşırı yükleme daha yaygındır.

#### <a name="hide-the-representations-of-record-and-union-types-if-the-design-of-these-types-is-likely-to-evolve"></a>Bu türlerin tasarımı gelişmeye olasılığı varsa, kayıt ve birleşim türlerinin temsillerini gizleyin

Nesnelerin somut gösterimlerini göstermeden kaçının. Örneğin, değerlerin somut gösterimi <xref:System.DateTime> .NET kitaplığı tasarımının dış, ortak API 'si tarafından görünmez. Çalışma zamanında, ortak dil çalışma zamanı yürütme sırasında kullanılacak kaydedilmiş uygulamayı bilir. Ancak, derlenmiş kod kendisi somut gösterimdeki bağımlılıkları almaz.

#### <a name="avoid-the-use-of-implementation-inheritance-for-extensibility"></a>Genişletilebilirlik için uygulama devralmanın kullanılmasını önleyin

F # ' da, uygulama devralma nadiren kullanılır. Ayrıca, devralma hiyerarşileri genellikle karmaşık ve yeni gereksinimler geldiğinde değişme zor olur. Devralma işlemi, uyumluluk için F # içinde ve soruna en iyi çözüm olduğu nadir durumlar için de mevcuttur, ancak arabirim uygulama gibi çok biçimlilik için tasarlanırken alternatif teknikler, F # programlarınızda elde edilmelidir.

### <a name="function-and-member-signatures"></a>İşlev ve üye imzaları

#### <a name="use-tuples-for-return-values-when-returning-a-small-number-of-multiple-unrelated-values"></a>Çok sayıda ilişkisiz değer döndürürken dönüş değerleri için tanımlama grupları kullanın

Aşağıda, bir dönüş türünde tanımlama grubu kullanmanın iyi bir örneği verilmiştir:

```fsharp
val divrem: BigInteger -> BigInteger -> BigInteger * BigInteger
```

Birçok bileşeni içeren dönüş türleri veya bileşenlerin tek bir tanınabilir varlıkla ilişkili olduğu durumlarda, tanımlama grubu yerine adlandırılmış bir tür kullanmayı düşünün.

#### <a name="use-asynct-for-async-programming-at-f-api-boundaries"></a>`Async<T>`F # API sınırlarında zaman uyumsuz programlama için kullanın

' I döndüren karşılık gelen bir zaman uyumlu işlem varsa `Operation` `T` , zaman uyumsuz işlem, döndürürse veya döndürürse adlandırılmış olmalıdır `AsyncOperation` `Async<T>` `OperationAsync` `Task<T>` . Başlangıç/bitiş yöntemlerini ortaya çıkaran yaygın olarak kullanılan .NET türleri için, `Async.FromBeginEnd` F # Async programlama modelini bu .NET API 'lerine sağlamak üzere bir façlade olarak uzantı yöntemleri yazmak için kullanmayı düşünün.

```fsharp
type SomeType =
    member this.Compute(x:int): int =
        ...
    member this.AsyncCompute(x:int): Async<int> =
        ...

type System.ServiceModel.Channels.IInputChannel with
    member this.AsyncReceive() =
        ...
```

### <a name="exceptions"></a>Özel durumlar

Özel durumların, sonuçların ve seçeneklerin uygun kullanımı hakkında bilgi edinmek için bkz. [hata yönetimi](conventions.md#error-management) .

### <a name="extension-members"></a>Uzantı üyeleri

#### <a name="carefully-apply-f-extension-members-in-f-to-f-components"></a>F #-to-F # bileşenlerinde F # uzantı üyelerini dikkatle uygulama

F # uzantısı üyeleri genellikle yalnızca kullanım modlarının çoğunluğunda bulunan bir türle ilişkili iç işlemleri kapanışdaki işlemler için kullanılmalıdır. Yaygın olarak kullanılan bir kullanım, çeşitli .NET türleri için F # ile daha fazla deyim içeren API 'Ler sağlamaktır:

```fsharp
type System.ServiceModel.Channels.IInputChannel with
    member this.AsyncReceive() =
        Async.FromBeginEnd(this.BeginReceive, this.EndReceive)

type System.Collections.Generic.IDictionary<'Key,'Value> with
    member this.TryGet key =
        let ok, v = this.TryGetValue key
        if ok then Some v else None
```

### <a name="union-types"></a>Birleşim türleri

#### <a name="use-discriminated-unions-instead-of-class-hierarchies-for-tree-structured-data"></a>Ağaç yapılandırılmış veriler için sınıf hiyerarşileri yerine ayrılmış birleşimler kullanın

Ağaç benzeri yapılar yinelemeli olarak tanımlanır. Bu, devralmayla birlikte, ayırt edici birleşimler ile zarif.

```fsharp
type BST<'T> =
    | Empty
    | Node of 'T * BST<'T> * BST<'T>
```

Ayrılmış birleşimlerle ağaç benzeri verilerin temsil edilmesi, aynı zamanda, model eşleştirme sırasında tüketme özelliğinden faydalanabilmeniz de sağlar.

#### <a name="use-requirequalifiedaccess-on-union-types-whose-case-names-are-not-sufficiently-unique"></a>`[<RequireQualifiedAccess>]`Büyük/küçük harf adları yeterince benzersiz olmayan birleşim türlerinde kullanın

Kendinizi, ayırt edici birleşim durumları gibi farklı şeyler için aynı adın en iyi adı olduğu bir etki alanında bulabilirsiniz. `[<RequireQualifiedAccess>]`Deyimlerin sıralamasına bağlı olarak gölgeleme nedeniyle karışık hataları tetiklememeniz için büyük/küçük harf adlarını ayırt etmek için kullanabilirsiniz `open`

#### <a name="hide-the-representations-of-discriminated-unions-for-binary-compatible-apis-if-the-design-of-these-types-is-likely-to-evolve"></a>Bu türlerin tasarımı gelişmeye olasılığı varsa, ikili uyumlu API 'Ler için ayrılmış birleşimlerin sunumlarını gizleyin

Birleşimler türleri bir kısa programlama modeli için F # örüntü eşleşen formları kullanır. Daha önce bahsedildiği gibi, bu türlerin tasarımı gelişdiğinde somut veri gösterimlerini önlemeyi kullanmaktan kaçının.

Örneğin, ayrılmış bir birleşimin temsili özel veya iç bildirim kullanılarak veya bir imza dosyası kullanılarak gizlenebilir.

```fsharp
type Union =
    private
    | CaseA of int
    | CaseB of string
```

Ayrılmış birleşimler sayısının fark gözetmeden ortaya çıkardıysanız, kitaplığınızı Kullanıcı kodunu bozmadan sürüm olarak kullanabilirsiniz. Bunun yerine, bir veya daha fazla etkin deseni, bu türden değerler üzerinde desen eşleştirmeye izin vermek için kullanmayı düşünün.

Etkin desenler, f # tüketicilerini doğrudan gösterme sırasında desen eşleştirme ile F # tüketicilerinin sağlanması için alternatif bir yol sağlar.

### <a name="inline-functions-and-member-constraints"></a>Satır içi Işlevler ve üye kısıtlamaları

#### <a name="define-generic-numeric-algorithms-using-inline-functions-with-implied-member-constraints-and-statically-resolved-generic-types"></a>Örtülü üye kısıtlamaları ve statik olarak çözümlenen genel türler içeren satır içi işlevleri kullanarak genel sayısal algoritmaları tanımlayın

Aritmetik üye kısıtlamaları ve F # karşılaştırma kısıtlamaları F # programlama için standarttır. Örneğin, aşağıdaki kodu göz önünde bulundurun:

```fsharp
let inline highestCommonFactor a b =
    let rec loop a b =
        if a = LanguagePrimitives.GenericZero<_> then b
        elif a < b then loop a (b - a)
        else loop (a - b) b
    loop a b
```

Bu işlevin türü aşağıdaki gibidir:

```fsharp
val inline highestCommonFactor : ^T -> ^T -> ^T
                when ^T : (static member Zero : ^T)
                and ^T : (static member ( - ) : ^T * ^T -> ^T)
                and ^T : equality
                and ^T : comparison
```

Bu, bir matematik kitaplığındaki ortak API için uygun bir işlevdir.

#### <a name="avoid-using-member-constraints-to-simulate-type-classes-and-duck-typing"></a>Tür sınıflarının benzetimini yapmak için üye kısıtlamalarını kullanmaktan kaçının ve Duck yazma

F # üye kısıtlamaları kullanılarak "Duck yazma" benzetimi yapılabilir. Ancak, bunu kullanan Üyeler F #-to-F # kitaplığı tasarımlarında genel olarak kullanılmamalıdır. Bunun nedeni, bilmediğiniz veya standart olmayan örtük kısıtlamaları temel alan kitaplık tasarımlarının, Kullanıcı kodu ile belirli bir çerçeve düzenine bağlı olmasına neden olur.

Ayrıca, üye kısıtlamalarının bu şekilde büyük bir şekilde kullanılması çok uzun derleme sürelerine neden olabilir.

### <a name="operator-definitions"></a>İşleç tanımları

#### <a name="avoid-defining-custom-symbolic-operators"></a>Özel sembolik işleçler tanımlamayı önleyin

Özel işleçler bazı durumlarda gereklidir ve büyük bir uygulama kodu gövdesinde çok yararlı notational cihazlarıdır. Bir kitaplığın yeni kullanıcıları için, adlandırılmış işlevlerin kullanımı genellikle daha kolaydır. Buna ek olarak, özel sembolik operatörler belge açısından zor olabilir ve kullanıcılar, IDE ve arama altyapılarındaki mevcut sınırlamalar nedeniyle, operatörlerle ilgili yardım aramak daha zor olabilir.

Sonuç olarak, işlevlerinizi adlandırılmış işlevler ve Üyeler olarak yayımlamak en iyisidir ve ayrıca, notational avantajları bu işlevselliğe sahip olan belge ve bilişsel maliyetlerini açığa çıkarır.

### <a name="units-of-measure"></a>Ölçü Birimleri

#### <a name="carefully-use-units-of-measure-for-added-type-safety-in-f-code"></a>F # kodunda eklenen tür güvenliği için ölçü birimlerini dikkatle kullanın

Ölçü birimleri için ek yazma bilgileri, diğer .NET dilleri tarafından görüntülendiklerinde silinir. .NET bileşenlerinin, araçların ve yansımanın türler-sans-units olduğunu unutmayın. Örneğin, C# tüketicileri yerine burada görünür `float` `float<kg>` .

### <a name="type-abbreviations"></a>Tür Kısaltmaları

#### <a name="carefully-use-type-abbreviations-to-simplify-f-code"></a>F # kodunu basitleştirmek için tür kısaltmalarını dikkatle kullanın

.NET bileşenleri, araçları ve Reflection türler için kısaltılmış adları görmez. Tür kısaltmalarının önemli kullanımları, bir etki alanının gerçekten olduğu kadar karmaşık görünmesini sağlayabilir ve bu da tüketicileri karıştırabilir.

#### <a name="avoid-type-abbreviations-for-public-types-whose-members-and-properties-should-be-intrinsically-different-to-those-available-on-the-type-being-abbreviated"></a>Üyeleri ve özellikleri, kısaltılmakta olan türden bulunanlarla farklı doğası gereği olması gereken genel türlerin tür kısaltmalarını önleyin

Bu durumda, kısaltılmakta olan tür, tanımlanmakta olan gerçek türün temsili hakkında çok fazla görünür. Bunun yerine, kısaltmayı bir sınıf türü veya tek büyük harf ayrılmış bir Union içinde sarmalayın (ya da performans önemli olduğunda, kısaltmayı kaydırmak için bir struct türü kullanmayı düşünün).

Örneğin, bir F # eşlemesinin özel durumu olarak çok eşleme tanımlamak, örneğin:

```fsharp
type MultiMap<'Key,'Value> = Map<'Key,'Value list>
```

Ancak, bu tür üzerindeki mantıksal nokta gösterimi işlemleri bir haritadaki işlemlerle aynı değildir. Örneğin, arama işlecinin eşleşmesi mantıklı değildir. [key] anahtar sözlükte değilse, bir özel durumu yükseltmek yerine boş listeyi döndürür.

## <a name="guidelines-for-libraries-for-use-from-other-net-languages"></a>Diğer .NET dillerinden kullanım için kitaplıklara yönelik yönergeler

Kitaplıkları diğer .NET dillerinden kullanılmak üzere tasarlarken, [.NET kitaplığı tasarım yönergelerine](../../standard/design-guidelines/index.md)uymamak önemlidir. Bu belgede, kısıtlama olmadan F # yapılarını kullanan F # temelli kitaplıkların aksine, bu kitaplıklar Vanilla .NET kitaplıkları olarak etiketlenir. Vanilla .NET kitaplıklarını tasarlamak, genel API 'de F # özel yapıların kullanımını en aza indirerek, .NET Framework geri kalanı ile tutarlı tanıdık ve idmatik API 'Lerin sağlanması anlamına gelir. Kurallar aşağıdaki bölümlerde açıklanmıştır.

### <a name="namespace-and-type-design-for-libraries-for-use-from-other-net-languages"></a>Ad alanı ve tür tasarımı (diğer .NET dillerinden kullanılacak kitaplıklar için)

#### <a name="apply-the-net-naming-conventions-to-the-public-api-of-your-components"></a>Bileşenlerinizin genel API 'sine .NET adlandırma kuralları uygulayın

Kısaltılmış adların kullanımı ve .NET büyük/küçük harf yönergeleri için özel dikkat ödeyin.

```fsharp
type pCoord = ...
    member this.theta = ...

type PolarCoordinate = ...
    member this.Theta = ...
```

#### <a name="use-namespaces-types-and-members-as-the-primary-organizational-structure-for-your-components"></a>Bileşenleriniz için birincil kuruluş yapısı olarak ad alanları, türler ve Üyeler kullanın

Ortak işlevselliği içeren tüm dosyalar bir `namespace` bildirimle başlamalıdır ve ad alanlarındaki genel kullanıma yönelik varlıkların türleri olmalıdır. F # modülleri kullanmayın.

Uygulama kodu, yardımcı program türleri ve yardımcı program işlevlerini barındırmak için ortak olmayan modüller kullanın.

Statik türler, API 'nin gelecekteki gelişiminde ve F # modülleri içinde kullanılamayan diğer .NET API tasarımı kavramlarını kullanmasına izin verdiklerinden, modüller üzerinden tercih edilmelidir.

Örneğin, aşağıdaki ortak API 'nin yerine:

```fsharp
module Fabrikam

module Utilities =
    let Name = "Bob"
    let Add2 x y = x + y
    let Add3 x y z = x + y + z
```

Bunun yerine göz önünde bulundurun:

```fsharp
namespace Fabrikam

[<AbstractClass; Sealed>]
type Utilities =
    static member Name = "Bob"
    static member Add(x,y) = x + y
    static member Add(x,y,z) = x + y + z
```

#### <a name="use-f-record-types-in-vanilla-net-apis-if-the-design-of-the-types-wont-evolve"></a>Türlerin tasarımı geliştirimayacaksa, Vanilla .NET API 'Lerinde F # kayıt türlerini kullanın

F # kayıt türleri basit bir .NET sınıfına derlenir. Bunlar, API 'lerde bazı basit ve kararlı türler için uygundur. `[<NoEquality>]` `[<NoComparison>]` Arabirimlerin otomatik olarak oluşturulmasını engellemek için ve özniteliklerini kullanmayı düşünün. Ayrıca, Vanilla .NET API 'Lerinde kesilebilir kayıt alanlarını kullanmaktan kaçının, bunlar ortak bir alanı kullanıma sunar. Her zaman bir sınıfın, API 'nin gelecekteki gelişiminde daha esnek bir seçenek sağlayıp sağlamamadığını düşünün.

Örneğin, aşağıdaki F # kodu bir C# tüketicisi için ortak API 'yi kullanıma sunar:

F#:

```fsharp
[<NoEquality; NoComparison>]
type MyRecord =
    { FirstThing: int
        SecondThing: string }
```

C#:

```csharp
public sealed class MyRecord
{
    public MyRecord(int firstThing, string secondThing);
    public int FirstThing { get; }
    public string SecondThing { get; }
}
```

#### <a name="hide-the-representation-of-f-union-types-in-vanilla-net-apis"></a>Vanilla .NET API 'Lerinde F # birleşim türlerinin gösterimini gizleyin

F # birleşim türleri, F #-F # kodlaması için bile bileşen sınırları boyunca yaygın olarak kullanılmaz. Bunlar, dahili olarak bileşenler ve kitaplıklar içinde kullanıldığında harika bir uygulama cihazlarıdır.

Bir Vanilla .NET API 'SI tasarlarken, bir özel bildirim veya imza dosyası kullanarak bir birleşim türü gösterimini gizlemeyi düşünün.

```fsharp
type PropLogic =
    private
    | And of PropLogic * PropLogic
    | Not of PropLogic
    | True
```

Ayrıca, istenen bir birleşim temsili olan türleri, Üyeler ile dahili olarak kullanarak da genişletebilirsiniz. NET 'e yönelik API.

```fsharp
type PropLogic =
    private
    | And of PropLogic * PropLogic
    | Not of PropLogic
    | True

    /// A public member for use from C#
    member x.Evaluate =
        match x with
        | And(a,b) -> a.Evaluate && b.Evaluate
        | Not a -> not a.Evaluate
        | True -> true

    /// A public member for use from C#
    static member CreateAnd(a,b) = And(a,b)
```

#### <a name="design-gui-and-other-components-using-the-design-patterns-of-the-framework"></a>Framework 'ün tasarım düzenlerini kullanarak GUI ve diğer bileşenleri tasarlama

.NET içinde WinForms, WPF ve ASP.NET gibi birçok farklı çerçeve mevcuttur. Her birinin adlandırma ve tasarım kuralları, bu çerçevelerde kullanılmak üzere bileşen tasarlıyorsanız kullanılmalıdır. Örneğin, WPF programlama için, tasarlamakta olduğunuz sınıflar için WPF tasarım düzenlerini benimseyin. Kullanıcı arabirimi programlamadaki modeller için, içinde bulunan olaylar ve bildirim tabanlı Koleksiyonlar gibi tasarım düzenlerini kullanın <xref:System.Collections.ObjectModel> .

### <a name="object-and-member-design-for-libraries-for-use-from-other-net-languages"></a>Nesne ve üye tasarımı (diğer .NET dillerinden kullanılacak kitaplıklar için)

#### <a name="use-the-clievent-attribute-to-expose-net-events"></a>.NET olaylarını göstermek için CLIEvent özniteliğini kullanın

Bir `DelegateEvent` nesnesi alan ve `EventArgs` (yalnızca türü varsayılan olarak kullanan) belirli bir .NET temsilci türüyle oluşturun `Event` , `FSharpHandler` böylece olaylar diğer .NET dillerine tanıdık bir şekilde yayımlanır.

```fsharp
type MyBadType() =
    let myEv = new Event<int>()

    [<CLIEvent>]
    member this.MyEvent = myEv.Publish

type MyEventArgs(x: int) =
    inherit System.EventArgs()
    member this.X = x

    /// A type in a component designed for use from other .NET languages
type MyGoodType() =
    let myEv = new DelegateEvent<EventHandler<MyEventArgs>>()

    [<CLIEvent>]
    member this.MyEvent = myEv.Publish
```

#### <a name="expose-asynchronous-operations-as-methods-that-return-net-tasks"></a>Zaman uyumsuz işlemleri .NET görevleri döndüren yöntemler olarak kullanıma sunma

Görevler, .NET 'te etkin zaman uyumsuz hesaplamaları göstermek için kullanılır. Görevler `Async<T>` , "zaten yürütülmekte olan" görevleri temsil ettiğinden ve paralel bileşim yapan ya da iptal sinyallerinin ve diğer bağlamsal parametrelerin yayılmasını gizleyemediğinden, F # nesnelerinden genel olarak daha az bileşimdir.

Ancak, bu şekilde, görevleri döndüren yöntemler .NET üzerinde zaman uyumsuz programlama için standart gösterimidir.

```fsharp
/// A type in a component designed for use from other .NET languages
type MyType() =

    let compute (x: int): Async<int> = async { ... }

    member this.ComputeAsync(x) = compute x |> Async.StartAsTask
```

Ayrıca, açık bir iptal belirtecini de kabul etmek isteyeceksiniz:

```fsharp
/// A type in a component designed for use from other .NET languages
type MyType() =
    let compute(x: int): Async<int> = async { ... }
    member this.ComputeAsTask(x, cancellationToken) = Async.StartAsTask(compute x, cancellationToken)
```

#### <a name="use-net-delegate-types-instead-of-f-function-types"></a>F # işlev türleri yerine .NET temsilci türlerini kullanın

Burada "F # işlev türleri", gibi "ok" türler anlamına gelir `int -> int` .

Bunun yerine:

```fsharp
member this.Transform(f: int->int) =
    ...
```

Bunu yapın:

```fsharp
member this.Transform(f: Func<int,int>) =
    ...
```

F # işlev türü `class FSharpFunc<T,U>` diğer .NET dilleri gibi görünür ve temsilci türlerini anlayan dil özellikleri ve araçlar için daha az uygundur. .NET Framework 3,5 veya üzeri bir şekilde hedef alan daha yüksek sıralı bir yöntem yazarken, `System.Func` ve `System.Action` temsilcileri, .NET geliştiricilerinin bu API 'leri düşük bir şekilde kullanmasını sağlamak için yayımlanacak doğru API 'lardır. (.NET Framework 2,0 ' i hedeflerken, sistem tarafından tanımlanan temsilci türleri daha sınırlıdır; gibi önceden tanımlanmış temsilci türlerini kullanmayı düşünün `System.Converter<T,U>` veya belirli bir temsilci türü tanımlar.)

Ters çevir tarafında, F # ile bağlantılı kitaplıklar için .NET temsilcileri doğal değildir (F # ile bağlantılı kitaplıkların sonraki bölümüne bakın). Sonuç olarak, Vanilla .NET kitaplıkları için daha yüksek sıralı Yöntemler geliştirilirken yaygın bir uygulama stratejisi, F # işlev türlerini kullanarak tüm uygulamayı yazar ve ardından temsilcileri kullanarak ortak API 'yi bir ince façlade üzerine gerçek F # uygulamasını olarak oluşturur.

#### <a name="use-the-trygetvalue-pattern-instead-of-returning-f-option-values-and-prefer-method-overloading-to-taking-f-option-values-as-arguments"></a>F # seçenek değerlerini döndürmek yerine TryGetValue modelini kullanın ve F # seçenek değerlerini bağımsız değişken olarak almak için yöntem aşırı yüklemesini tercih edin

API 'lerde F # seçenek türü için kullanılan yaygın kullanım desenleri, standart .NET tasarım teknikleri kullanılarak Vanilla .NET API 'Lerinde daha iyi uygulanır. Bir F # seçenek değeri döndürmek yerine, bool dönüş türünü ve "TryGetValue" düzeninde olduğu gibi bir out parametresini kullanmayı düşünün. F # seçenek değerlerini parametre olarak almak yerine, yöntem aşırı yüklemesini veya isteğe bağlı bağımsız değişkenleri kullanmayı düşünün.

```fsharp
member this.ReturnOption() = Some 3

member this.ReturnBoolAndOut(outVal: byref<int>) =
    outVal <- 3
    true

member this.ParamOption(x: int, y: int option) =
    match y with
    | Some y2 -> x + y2
    | None -> x

member this.ParamOverload(x: int) = x

member this.ParamOverload(x: int, y: int) = x + y
```

#### <a name="use-the-net-collection-interface-types-ienumerablet-and-idictionarykeyvalue-for-parameters-and-return-values"></a>.NET koleksiyon arabirim türleri IEnumerable \< T \> ve IDictionary \< anahtarı, \> Parametreler ve dönüş değerleri için değer kullanın

.NET dizileri, F # türleri ve gibi somut koleksiyon türlerinin kullanılmasını önleyin `T[]` ve gibi `list<T>` `Map<Key,Value>` `Set<T>` .net somut koleksiyon türleri `Dictionary<Key,Value>` . .NET kitaplığı tasarım yönergeleri, gibi çeşitli koleksiyon türlerinin ne zaman kullanılacağı konusunda iyi öneriler sağlar `IEnumerable<T>` . Bazı durumlarda dizilerin () bazı kullanımı, performans miktarı ' nda `T[]` bazı koşullarda kabul edilebilir. Özellikle `seq<T>` için yalnızca F # diğer adı olduğunu unutmayın `IEnumerable<T>` ve bu nedenle, bir Vanilla .NET API 'si için sıra, genellikle uygun bir türdür.

F # listeleri yerine:

```fsharp
member this.PrintNames(names: string list) =
    ...
```

F # dizilerini kullan:

```fsharp
member this.PrintNames(names: seq<string>) =
    ...
```

#### <a name="use-the-unit-type-as-the-only-input-type-of-a-method-to-define-a-zero-argument-method-or-as-the-only-return-type-to-define-a-void-returning-method"></a>Sıfır değişkenli bir yöntemi tanımlamak için bir metodun tek giriş türü olarak veya void döndüren bir yöntemi tanımlamak için tek dönüş türü olarak birim türünü kullanın

Birim türünün diğer kullanımkullanmaktan kaçının. Bunlar iyidir:

```fsharp
✔ member this.NoArguments() = 3

✔ member this.ReturnVoid(x: int) = ()
```

Bu hatalı:

```fsharp
member this.WrongUnit( x: unit, z: int) = ((), ())
```

#### <a name="check-for-null-values-on-vanilla-net-api-boundaries"></a>Vanilla .NET API sınırları üzerinde null değerleri denetle

F # uygulama kodu, sabit tasarım desenleri ve F # türleri için null sabit değerler kullanımıyla ilgili kısıtlamalar nedeniyle daha az null değere sahip olacak şekilde eğilimindedir. Diğer .NET dilleri genellikle null değeri çok daha sık kullanır. Bu nedenle, bir Vanilla .NET API 'sini kullanıma sunan F # kodu, API sınırında null için parametreleri denetlemelidir ve bu değerlerin F # uygulama koduna daha derin akmasını önler. `isNull`Düzende eşleşen işlev veya desenler `null` kullanılabilir.

```fsharp
let checkNonNull argName (arg: obj) =
    match arg with
    | null -> nullArg argName
    | _ -> ()

let checkNonNull` argName (arg: obj) =
    if isNull arg then nullArg argName
    else ()
```

#### <a name="avoid-using-tuples-as-return-values"></a>Bir dönüş değeri olarak tanımlama gruplarını kullanmaktan kaçının

Bunun yerine, Birleşik verileri tutan adlandırılmış bir tür döndürmeyi veya birden çok değer döndürmek için out parametrelerini kullanmayı tercih edin. Tanımlama grupları ve yapı tanımlama grupları .NET 'te bulunmasına rağmen (struct tanımlama grupları için C# dil desteği dahil), en sık, .NET geliştiricileri için ideal ve beklenen API 'YI sağlamayacak.

#### <a name="avoid-the-use-of-currying-of-parameters"></a>Parametrelerin currying kullanımını önleyin

Bunun yerine, .NET çağırma kurallarını kullanın `Method(arg1,arg2,…,argN)` .

```fsharp
member this.TupledArguments(str, num) = String.replicate num str
```

İpucu: kitaplıkları herhangi bir .NET dilinden kullanılmak üzere tasarlıyorsanız, kitaplıklarınızın bu dillerden "doğru" olduğundan emin olmak için bazı deneysel C# ve Visual Basic programlamasına yönelik bir yedek yoktur. Ayrıca, kitaplıkların ve belgelerinin geliştiriciler tarafından beklendiği gibi göründüğünden emin olmak için .NET yansıtıcısı ve Visual Studio Nesne Tarayıcısı gibi araçları da kullanabilirsiniz.

## <a name="appendix"></a>Ek

### <a name="end-to-end-example-of-designing-f-code-for-use-by-other-net-languages"></a>Diğer .NET dilleri tarafından kullanılmak üzere F # kodu tasarlamaya yönelik uçtan uca örnek

Aşağıdaki sınıfı göz önünde bulundurun:

```fsharp
open System

type Point1(angle,radius) =
    new() = Point1(angle=0.0, radius=0.0)
    member x.Angle = angle
    member x.Radius = radius
    member x.Stretch(l) = Point1(angle=x.Angle, radius=x.Radius * l)
    member x.Warp(f) = Point1(angle=f(x.Angle), radius=x.Radius)
    static member Circle(n) =
        [ for i in 1..n -> Point1(angle=2.0*Math.PI/float(n), radius=1.0) ]
```

Bu sınıfın çıkarılan F # türü aşağıdaki gibidir:

```fsharp
type Point1 =
    new : unit -> Point1
    new : angle:double * radius:double -> Point1
    static member Circle : n:int -> Point1 list
    member Stretch : l:double -> Point1
    member Warp : f:(double -> double) -> Point1
    member Angle : double
    member Radius : double
```

Bu F # türünün başka bir .NET dilini kullanarak bir programcıya nasıl göründüğüne göz atalım. Örneğin, yaklaşık C# "imza" şu şekildedir:

```csharp
// C# signature for the unadjusted Point1 class
public class Point1
{
    public Point1();

    public Point1(double angle, double radius);

    public static Microsoft.FSharp.Collections.List<Point1> Circle(int count);

    public Point1 Stretch(double factor);

    public Point1 Warp(Microsoft.FSharp.Core.FastFunc<double,double> transform);

    public double Angle { get; }

    public double Radius { get; }
}
```

Burada F # yapıları nasıl temsil ettiğini fark eden bazı önemli noktaları vardır. Örneğin:

* Bağımsız değişken adları gibi meta veriler korunur.

* İki bağımsız değişken alan F # yöntemleri iki bağımsız değişken içeren C# yöntemi haline gelir.

* İşlevler ve listeler, F # kitaplığındaki ilgili türlere başvuru haline gelir.

Aşağıdaki kod, bu kodun bu işlemleri hesaba çekmek için nasıl ayarlanacağını gösterir.

```fsharp
namespace SuperDuperFSharpLibrary.Types

type RadialPoint(angle:double, radius:double) =

    /// Return a point at the origin
    new() = RadialPoint(angle=0.0, radius=0.0)

    /// The angle to the point, from the x-axis
    member x.Angle = angle

    /// The distance to the point, from the origin
    member x.Radius = radius

    /// Return a new point, with radius multiplied by the given factor
    member x.Stretch(factor) =
        RadialPoint(angle=angle, radius=radius * factor)

    /// Return a new point, with angle transformed by the function
    member x.Warp(transform:Func<_,_>) =
        RadialPoint(angle=transform.Invoke angle, radius=radius)

    /// Return a sequence of points describing an approximate circle using
    /// the given count of points
    static member Circle(count) =
        seq { for i in 1..count ->
                RadialPoint(angle=2.0*Math.PI/float(count), radius=1.0) }
```

Kodun çıkarılan F # türü aşağıdaki gibidir:

```fsharp
type RadialPoint =
    new : unit -> RadialPoint
    new : angle:double * radius:double -> RadialPoint
    static member Circle : count:int -> seq<RadialPoint>
    member Stretch : factor:double -> RadialPoint
    member Warp : transform:System.Func<double,double> -> RadialPoint
    member Angle : double
    member Radius : double
```

C# imzası artık şu şekildedir:

```csharp
public class RadialPoint
{
    public RadialPoint();

    public RadialPoint(double angle, double radius);

    public static System.Collections.Generic.IEnumerable<RadialPoint> Circle(int count);

    public RadialPoint Stretch(double factor);

    public RadialPoint Warp(System.Func<double,double> transform);

    public double Angle { get; }

    public double Radius { get; }
}
```

Bu tür bir Vanilla .NET kitaplığının parçası olarak kullanılmak üzere hazırlanmaya yapılan düzeltmeler aşağıdaki gibidir:

* Birkaç ad düzeltildi: `Point1` , `n` , `l` , ve `f` sırasıyla,, `RadialPoint` `count` `factor` , ve `transform` .

* Kullanarak bir `seq<RadialPoint>` `RadialPoint list` liste oluşturmayı kullanarak bir sıra oluşturma için kullanarak bir liste oluşturma yerine bir dönüş türü kullandınız `[ ... ]` `IEnumerable<RadialPoint>` .

* `System.Func`F # işlev türü yerine .NET temsilci türü kullanıldı.

Bu, C# kodunda tüketilmesini sağlar.
