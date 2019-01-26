---
title: F#Bileşen tasarım yönergeleri
description: Yazmak için kılavuzları edinin F# diğer çağıranlar tarafından tüketim için hazırlanmış bileşenleri.
ms.date: 05/14/2018
ms.openlocfilehash: c61e4cd9098388b356c71c325d66c760fa866cf0
ms.sourcegitcommit: d9a0071d0fd490ae006c816f78a563b9946e269a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55066031"
---
# <a name="f-component-design-guidelines"></a>F#Bileşen tasarım yönergeleri

Bu belge için bileşen tasarım yönergeleri kümesidir F# temel programlama, F# bileşen tasarım yönergeleri, v14, Microsoft Research ve [başka bir sürümü](https://fsharp.org/specs/component-design-guidelines/) başlangıçta seçkin ve destekleyen F# Yazılım Foundation.

Bu belge hakkında bilgi sahibi olduğunuz varsayılır F# programlama. Çoğu performanstan F# topluluk Katkıları ve bu kılavuz çeşitli sürümlerinde yararlı geri bildirim.

## <a name="overview"></a>Genel Bakış

Bu belge ilgili sorunlardan bazılarını bakar F# bileşen tasarım ve kodlama. Bir bileşen, aşağıdakilerden herhangi birini gelebilir:

* Bir katmana, F# dış tüketicileri bir proje olan proje.
* Tüketimi yönelik bir kitaplık F# bütünleştirilmiş kod sınırları arasında kod.
* Bütünleştirilmiş kod sınırları arasında herhangi bir .NET dil tarafından tüketim için hazırlanmış bir kitaplık.
* Gibi bir paket deposu aracılığıyla dağıtım için hedeflenen bir kitaplık [NuGet](https://nuget.org).

Bu makalede açıklanan teknikleri izleyin [beş iyi prensipleri F# kod](index.md#five-principles-of-good-f-code), böylece her ikisi de işlevsel yazılımınız ve uygun şekilde programlama nesnesi.

Metodoloji bağımsız olarak, geliştiriciler tarafından kullanılabilen en kolay bir API'si çalışıyorlardı çalışırken bir dizi pratik ve prosaic soruna bileşen ve kitaplık Tasarımcı yüzler. Sertifikasyonuna uygulamasının [.NET kitaplığı tasarım yönergeleri](../../standard/design-guidelines/index.md) kullanmak eğlenceli API'lerden tutarlı özellik kümesi oluşturma doğrultusunda faaliyetidir.

## <a name="general-guidelines"></a>Genel yönergeler

Geçerli birkaç Evrensel yönergeleri vardır F# kitaplıkları, kitaplığı için hedef kitle ne olursa olsun.

### <a name="learn-the-net-library-design-guidelines"></a>.NET kitaplığı tasarım yönergeleri edinin

Türü ne olursa olsun, F# kodlama bilgisine sahip değerlidir, yapmakta olduğunuz [.NET kitaplığı tasarım yönergeleri](../../standard/design-guidelines/index.md). Çoğu diğer F# ve .NET programcıları bu yönergelere hakkında bilgi sahibi olmanız ve .NET kodu için uygun olması için bekler.

.NET kitaplığı tasarım yönergeleri adlandırma, sınıflar ve arabirimler, üye tasarım (Özellikler, yöntemler, olaylar, vb.) ve daha fazlasını tasarımı ile ilgili genel rehberlik sağlar ve tasarım kılavuzu çeşitli başvuru yararlı ilk noktası olan.

### <a name="add-xml-documentation-comments-to-your-code"></a>XML belge açıklamaları için kodunuzu ekleyin

XML belgeleri ortak API'lerde emin olmak için kitaplık dosyaları bu türleri ve üyeleri ve etkinleştirme yapı belgeleri kullanarak kullanıcıların harika IntelliSense ve Hızlıbilgi alabilirsiniz. Bkz: [XML belgeleri](../language-reference/xml-documentation.md) xmldoc Açıklamalar içinde ek biçimlendirme için kullanılabilen çeşitli xml etiketleri hakkında.

```fsharp
/// A class for representing (x,y) coordinates
type Point =

    /// Computes the distance between this point and another
    member DistanceTo: otherPoint:Point -> float
```

Kısa form XML açıklamaları kullanabilirsiniz (`/// comment`), veya standart XML açıklamaları (`///<summary>comment</summary>`).

### <a name="consider-using-explicit-signature-files-fsi-for-stable-library-and-component-apis"></a>Kararlı kitaplığı ve bileşen API'leri için açık imza dosyalarını (.fsi) kullanmayı düşünün

Açık imzaları dosyalarını kullanan bir F# Kitaplığı hem tam genel kitaplığınızın, de yüzey gibi ortak belgeler arasında NET bir ayrım sağlar ve iç bildiğinizden emin olun yardımcı olan genel API birleştiren bir özetini sunar Uygulama Ayrıntıları. Genel API değiştirmek için hem uygulama hem de imza dosyalarında yapılacak değişiklikler gerektirerek imza dosyalarını uyuşmazlıkları eklediğiniz unutmayın. Bir API solidified haline gelir ve bundan böyle önemli bir değişiklik beklenen sonuç olarak, imza dosyalarını genellikle yalnızca tanıtılmak.

### <a name="always-follow-best-practices-for-using-strings-in-net"></a>Her zaman .NET dizeleri kullanmak için en iyi uygulamaları izleyin

İzleyin [kullanarak dizeleri de .NET için en iyi](../../standard/base-types/best-practices-strings.md) Kılavuzu. Özellikle, her zaman açık durum *kültürel hedefi* dönüştürme ve karşılaştırma dizeleri, (uygunsa).

## <a name="guidelines-for-f-facing-libraries"></a>Yönergeler için F#-karşılıklı kitaplıkları

Bu bölümde genel geliştirmeye yönelik öneriler sunan F#-karşılıklı kitaplıkları; diğer bir deyişle, genel API tarafından tüketilmesi amaçlanan gösterme kitaplıkları F# geliştiriciler. Kitaplık tasarım önerileri çeşitli özellikle ilgili F#. Aşağıdaki öneriler olmaması durumunda .NET kitaplığı tasarım geri dönüş Kılavuzu yönergelerdir.

### <a name="naming-conventions"></a>Adlandırma kuralları

#### <a name="use-net-naming-and-capitalization-conventions"></a>.NET adlandırma ve büyük/küçük harf kuralları kullanma

Aşağıdaki tablo, .NET adlandırma ve büyük/küçük harf kurallarını izler. Ayrıca içerecek şekilde küçük eklemeler yapılmıştır F# oluşturur.

| Oluştur | Servis talebi | Bölümü | Örnekler | Notlar |
|-----------|------|------|----------|-------|
| Somut türleri | PascalCase | İsim / sıfat | Liste, çift, karmaşık | Yapılar, sınıflar, numaralandırmalar, temsilciler, kayıtlar ve birleşimler bunun somut türleridir. Tür adları içinde OCaml, geleneksel olarak küçük olsa F# türleri için .NET adlandırma şeması BENİMSEDİ.
| DLL'ler           | PascalCase |                 | Fabrikam.Core.dll |  |
| Birleşim etiketleri     | PascalCase | İsim | Bazı, ekleme, başarılı | Bir ön ek, genel API'ler kullanmayın. İsteğe bağlı olarak öneki gibi iç zaman kullanmak `takımlar yazın = TAlpha | TBeta | TDelta.` |
| Olay          | PascalCase | Fiili | ValueChanged / ValueChanging |  |
| Özel Durumlar     | PascalCase |      | WebException ise | Adı "Özel durum" ile bitmelidir. |
| Alan          | PascalCase | İsim | Geçerli ad  | |
| Arabirim türleri |  PascalCase | İsim / sıfat | IDisposable | Adı "I" ile başlamalıdır. |
| Yöntem |  PascalCase |  Fiili | ToString | |
| Ad Alanı | PascalCase | | Microsoft.FSharp.Core | Genellikle kullanması `<Organization>.<Technology>[.<Subnamespace>]`, kuruluş teknolojisi organizasyonu bağımsız ise, ancak bırakın. |
| Parametreler | camelCase | İsim |  typeName, dönüştürme ve aralığı | |
| izin değerleri (iç) | camelCase veya PascalCase | İsim / fiili |  getValue, myTable |
| izin değerleri (Dış) | camelCase veya PascalCase | İsim/fiili  | List.map, Dates.Today | let bağlı değerleri genellikle geleneksel işlevsel tasarım desenleri izlerken ortaktır. Ancak, diğer .NET dillerinden tanımlayıcısı kullanılabilir olduğunda genellikle PascalCase kullanın. |
| Özellik  | PascalCase  | İsim / sıfat  | IsEndOfFile, arka plan rengi  | Boole özellikleri genellikle olduğu ve olabilir ve olumlu değil IsNotEndOfFile IsEndOfFile olduğu gibi olması gerekir.

#### <a name="avoid-abbreviations"></a>Kısaltmalar kaçının

.NET Kılavuzu kısaltmalar kullanımını engelleyin (örneğin, "kullanmak `OnButtonClick` yerine `OnBtnClick`"). Ortak kısaltmalar gibi `Async` "Zaman uyumsuz için", izin verilir. Bu kılavuz, işlevsel programlama bazen yoksayıldı; Örneğin, `List.iter` "yinelemek için" bir kısaltma kullanır. İçinde büyük ölçüde edileceği kısaltmalar kullanarak bu nedenle, eğilimlidir F#- için -F# programlama, ancak genel bileşen tasarım hala genellikle kaçınılmalıdır.

#### <a name="avoid-casing-name-collisions"></a>Ad çakışması büyük/küçük harfleri kaçının

.NET Kılavuzu, tek başına büyük/küçük harfleri bazı istemci dillerini (örneğin, Visual Basic) büyük/küçük harfe duyarsızdır beri ad çakışmalarını belirsizliğini ortadan kaldırmak için kullanılamayacağını varsayalım.

#### <a name="use-acronyms-where-appropriate"></a>Uygun yerlerde kısaltmalar kullanın.

Kısaltmalar gibi XML kısaltmalar değildir ve .NET kitaplıkları eden formunda (Xml), yaygın olarak kullanılır. Yalnızca bilinen, tanınmış kısaltmalar kullanılmalıdır.

#### <a name="use-pascalcase-for-generic-parameter-names"></a>Genel parametre adları için PascalCase kullanın

Genel parametre adları dahil olmak üzere, ortak API'lerde PascalCase kullanma F#-kitaplıkları karşılıklı. Özellikle, adları gibi kullanın `T`, `U`, `T1`, `T2` rastgele genel parametreler için ve belirli adları, ardından mantıklı zaman F#-karşılıklı kitaplıklarını kullanma gibi adları `Key`, `Value`, `Arg` (ancak değil örneğin `TKey`).

#### <a name="use-either-pascalcase-or-camelcase-for-public-functions-and-values-in-f-modules"></a>Genel işlevler ve değerleri PascalCase ya da camelCase kullanılmaya F# modülleri

camelCase kullanılmak üzere tasarlanmış genel işlevleri için kullanılan nitelenmemiş (örneğin, `invalidArg`) ve "standart toplama işlevleri için" (örneğin, List.map). Her iki bu durumda, işlev adlarını çok dil anahtar sözcükleri gibi davranır.

### <a name="object-type-and-module-design"></a>Nesne, türü ve modül tasarım

#### <a name="use-namespaces-or-modules-to-contain-your-types-and-modules"></a>Türler ve modüller içerecek şekilde ad alanları veya modülleri kullanma

Her F# bir bileşen dosyasında, bir ad alanı bildirimi veya modül bildirimi ile başlamalıdır.

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

Kod en üst düzeyde düzenlemek için modüller ve ad alanları'nı kullanarak arasındaki farklar aşağıdaki gibidir:

* Ad alanlarında birden çok dosya yayılabilir.
* Ad alanları içeremez F# içinde bir iç modül olmadıkları sürece işlevleri
* Herhangi bir modülden kodunu tek bir dosyada yer almalıdır
* Üst düzey modüller içerebilir F# bir iç modül gerek kalmadan işlevleri

Bir üst düzey ad alanında veya modülde arasında seçim kodun derlenmiş form etkiler ve bu nedenle diğer .NET dilleri görünümünden API'nizi sonunda kullanılması dışında etkiler F# kod.

#### <a name="use-methods-and-properties-for-operations-intrinsic-to-object-types"></a>Nesne türleri için iç işlemler için yöntemleri ve özellikleri kullanın

Nesneleriyle çalışırken tüketilebilir işlevselliği yöntemleri ve özellikleri türdeki olarak uygulandığından emin olmak en iyisidir.

```fsharp
type HardwareDevice() =

    member this.ID = ...

    member this.SupportedProtocols = ...

type HashTable<'Key,'Value>(comparer: IEqualityComparer<'Key>) =

    member this.Add(key, value) = ...

    member this.ContainsKey(key) = ...

    member this.ContainsValue(value) = ...
```

İşlevlerin toplu belirli bir üye için mutlaka bu üye uygulanmadı, ancak bu işlevsellik tüketilebilir parçası olmalıdır.

#### <a name="use-classes-to-encapsulate-mutable-state"></a>Değişebilir durum kapsüllemek için sınıfları kullanma

İçinde F#, bu yalnızca bir durumu zaten bir kapanış, sıralama ifadesi veya zaman uyumsuz bir hesaplama gibi başka bir dil yapısı yalıtılan değil, yapılması gerekir.

```fsharp
type Counter() =
    // let-bound values are private in classes.
    let mutable count = 0

    member this.Next() =
        count <- count + 1
        count
```

#### <a name="use-interfaces-to-group-related-operations"></a>Arabirimleri kullanın ilgili işlemler

Arabirim türlerinde işlemler kümesini temsil etmek için kullanın. Bu işlevlerin diziler veya işlevlerin kayıtlar gibi diğer seçenekleri için tercih edilir.

```fsharp
type Serializer =
    abstract Serialize<'T>: preserveRefEq: bool -> value: 'T -> string
    abstract Deserialize<'T>: preserveRefEq: bool -> pickle: string -> 'T
```

Preference için:

```fsharp
type Serializer<'T> = {
    Serialize: bool -> 'T -> string
    Deserialize: bool -> string -> 'T
}
```

Hangi işlev nesneleri normalde verirsiniz elde etmek için kullanabileceğiniz bir .NET birinci sınıf kavramları arabirimdir. Ayrıca, bunlar işlevlerin kayıtları olamaz, programa varlıksal türleri kodlamada kullanılabilir.

#### <a name="use-a-module-to-group-functions-which-act-on-collections"></a>Koleksiyonlarda davranan grubun işlevleri için bir modül kullanma

Bir koleksiyon türü tanımladığınızda, standart bir dizi işlemlerini ister sağlamayı göz önüne alın `CollectionType.map` ve `CollectionType.iter`) için yeni koleksiyon türleri.

```fsharp
module CollectionType =
    let map f c =
        ...
    let iter f c =
        ...
```

Böyle bir modül eklerseniz, FSharp.core'da bulunan işlevleri için standart adlandırma kurallarını uygulayın.

#### <a name="use-a-module-to-group-functions-for-common-canonical-functions-especially-in-math-and-dsl-libraries"></a>Matematik ve DSL kitaplıkları, özellikle ortak, kurallı işlevler için grubun işlevleri için bir modül kullanın

Örneğin, `Microsoft.FSharp.Core.Operators` en üst düzey işlevleri otomatik olarak açılan bir koleksiyonudur (gibi `abs` ve `sin`) FSharp.Core.dll tarafından sağlanan.

Benzer şekilde, istatistikleri kitaplığı işlevleri sahip bir modül içerebilir `erf` ve `erfc`, bu modül burada açıkça ya da otomatik olarak açılacak şekilde tasarlanmıştır.

#### <a name="consider-using-requirequalifiedaccess-and-carefully-apply-autoopen-attributes"></a>RequireQualifiedAccess kullanmayı göz önünde bulundurun ve dikkatli bir şekilde AutoOpen öznitelikleri uygulama

Ekleme `[<RequireQualifiedAccess>]` özniteliği bir modül için modülü açılamadı ve erişimi nitelenmiş modülünün öğelere başvurular açık gerektiğini gösterir. Örneğin, `Microsoft.FSharp.Collections.List` modülü, bu öznitelik içeriyor.

İşlevleri ve değerleri modüldeki diğer modüllerin adlarla çakışma olasılığı adlara sahip olduğunda bu kullanışlıdır. Koşullu erişim gerektiren bir kitaplığı geliştirilebilirlik ve uzun vadede sürdürülebilirliğini önemli ölçüde artırabilirsiniz.

Ekleme `[<AutoOpen>]` özniteliği bir modül için modülü içeren ad alanı açıldığında açılacak anlamına gelir. `[<AutoOpen>]` Özniteliği da uygulanabilir olduğunda derlemeye başvurulduğundan otomatik olarak açıldığında bir modül belirtmek için bir derleme.

Örneğin, bir istatistik Kitaplığı **MathsHeaven.Statistics** içerebilir bir `module MathsHeaven.Statistics.Operators` işlevler içeren `erf` ve `erfc`. Bu modül olarak işaretlemek makul `[<AutoOpen>]`. Başka bir deyişle `open MathsHeaven.Statistics` Ayrıca bu modül açılacak ve adları Getir `erf` ve `erfc` kapsama. Başka bir iyi kullanımını `[<AutoOpen>]` için genişletme yöntemleri içeren modüllere.

Aşırı `[<AutoOpen>]` kirletilmiş ad alanları ve özniteliklerini müşteri adaylarını dikkatli kullanılmalıdır. Belirli alanlarında kullanmalıdır belirli kitaplıkları için `[<AutoOpen>]` için daha iyi kullanılabilirlik yol açabilir.

#### <a name="consider-defining-operator-members-on-classes-where-using-well-known-operators-is-appropriate"></a>İyi bilinen işleçleri kullanarak uygun olduğu sınıflarında işleci üyelerini tanımlama göz önünde bulundurun

Bazen sınıfları, matematik yapıları vektörleri gibi model oluşturmak için kullanılır. İyi bilinen işleçleri modellenmiş etki alanı varsa, bunları sınıfı iç üyeleri olarak tanımlama yararlıdır.

```fsharp
type Vector(x: float) =

    member v.X = x

    static member (*) (vector: Vector, scalar: float) = Vector(vector.X * scalar)

    static member (+) (vector1: Vector, vector2: Vector) = Vector(vector1.X + vector2.X)

let v = Vector(5.0)

let u = v * 10.0
```

Bu kılavuz, bu tür için genel .NET rehberliği karşılık gelir. Ancak, ayrıca önemli olabilir F# ile birlikte kullanılmak üzere bu tür böylece olarak kodlama F# işlevlere ve metotlara List.sumBy gibi üye kısıtlamaları ile.

#### <a name="consider-using-compiledname-to-provide-a-net-friendly-name-for-other-net-language-consumers"></a>CompiledName sağlamak üzere kullanmayı göz önünde bulundurun bir. Diğer .NET dil Tüketiciler için NET kolay adı

Bazen bir stili için bir ad isteyebilirsiniz F# tüketiciler (gibi BT'nin görünecek şekilde küçük bir statik üye modülü bağlı işlevi gibi), ancak bütünleştirilmiş kod içine derlenmiş olan farklı bir stil adı vardır. Kullanabileceğiniz `[<CompiledName>]` için farklı bir stil sağlamak için özniteliği olmayan F# derlemenin tüketme kod.

```fsharp
type Vector(x:float, y:float) =

    member v.X = x
    member v.Y = y

    [<CompiledName("Create")>]
    static member create x y = Vector (x, y)

let v = Vector.create 5.0 3.0
```

Kullanarak `[<CompiledName>]`, .NET adlandırma kuralları için kullanabileceğiniz olmayan F# derlemenin tüketicileri.

#### <a name="use-method-overloading-for-member-functions-if-doing-so-provides-a-simpler-api"></a>Bunu yapmak, böylece daha basit bir API sağlar kullanırsanız, üye işlevleri için yöntemi aşırı yüklemesi

Yöntem aşırı yükü benzer işlevleri gerçekleştirmek için gereken API basitleştirmek için ancak farklı seçenekler ya da bağımsız değişkenler ile güçlü bir araç olan.

```fsharp
type Logger() =

    member this.Log(message) =
        ...
    member this.Log(message, retryPolicy) =
        ...
```

İçinde F#, bağımsız değişken türleri yerine bağımsız değişken sayısı aşırı daha yaygındır.

#### <a name="hide-the-representations-of-record-and-union-types-if-the-design-of-these-types-is-likely-to-evolve"></a>Bu tür tasarım geliştirilebilen olasılığı varsa, kayıt ve birleşim türlerini temsillerini Gizle

Nesneleri somut temsillerini açıklanmaması Örneğin, somut gösterimini <xref:System.DateTime> değerlerin değil .NET kitaplığı tasarım harici, genel API tarafından göstermiştir. Çalışma zamanında, ortak dil çalışma zamanı yürütme kullanılan taahhüt uygulama bilir. Ancak, derlenmiş kod kendisini somut gösterimi bağımlılıkları yerden devam edebiliyorduk değil.

#### <a name="avoid-the-use-of-implementation-inheritance-for-extensibility"></a>Uygulama devralma genişletilebilirliği için kullanmaktan kaçının

İçinde F#, uygulama devralma nadiren kullanılır. Ayrıca, devralma hiyerarşilerini çoğunlukla karmaşık ve yeni gereksinimleri geldiğinde değiştirmek zor olur. Devralma uygulama hala var F# uyumluluğu ve burada bir sorun için en iyi çözüm olduğundan, ancak diğer teknikleri Aranan nadir durumlarda, F# arabirimi gibi çok biçimlilik için tasarlarken programları uygulama.

### <a name="function-and-member-signatures"></a>İşlev ve üyesi imzaları

#### <a name="use-tuples-for-return-values-when-returning-a-small-number-of-multiple-unrelated-values"></a>Diziler için dönüş değerlerini, birden çok ilişkisiz değer az sayıda döndürülürken kullanın.

Bir dönüş türü bir tanımlama grubu kullanımı iyi bir örnek aşağıda verilmiştir:

```fsharp
val divrem: BigInteger -> BigInteger -> BigInteger * BigInteger
```

İçin dönüş türleri birçok bileşen içeren veya bileşenleri tek bir tanımlanabilen varlıkla ilgili yerlerde, adlandırılmış tür yerine bir demet kullanmayı göz önünde bulundurun.

#### <a name="use-asynct-for-async-programming-at-f-api-boundaries"></a>Kullanım `Async<T>` için zaman uyumsuz programlama, F# API sınırları

Adlı karşılık gelen eşzamanlı bir işlem olup olmadığını `Operation` döndüren bir `T`, zaman uyumsuz işlem adlı sonra `AsyncOperation` döndürürse `Async<T>` veya `OperationAsync` döndürürse `Task<T>`. Başlangıç/bitiş yöntemleri açığa yaygın olarak kullanılan .NET türleri göz önünde bulundurun için kullanarak `Async.FromBeginEnd` genişletme yöntemleri sağlamak için bir cephe yazmak için F# bu .NET API'ları için zaman uyumsuz programlama modeli.

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

### <a name="exceptions"></a>Özel Durumlar

Bkz: [hata Yönetimi](conventions.md#error-management) özel durumlar, sonuçları ve seçenekleri uygun kullanımı hakkında bilgi edinmek için.

### <a name="extension-members"></a>Uzantı üyeleri

#### <a name="carefully-apply-f-extension-members-in-f-to-f-components"></a>Dikkatli bir şekilde uygulama F# uzantı üyeleri F#- için -F# bileşenleri

F#Uzantı üyeleri genellikle yalnızca bir türü modlarından kullanım çoğu ile ilişkili iç işlemlerinin kabini içinde işlemleri için kullanılmalıdır. Yaygın olarak kullanıldığı olduğundan fazla deyimsel API'lerden sağlamak F# çeşitli .NET türleri için:

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

#### <a name="use-discriminated-unions-instead-of-class-hierarchies-for-tree-structured-data"></a>Ayrılmış birleşimler ağaç yapılandırılmış veriler için sınıf Hiyerarşiler yerine kullanın.

Ağaç benzeri, yinelemeli olarak tanımlanan yapılardır. Devralma ile garip, ancak ayırt edici birleşimler ile Zarif budur.

```fsharp
type BST<'T> =
    | Empty
    | Node of 'T * BST<'T> * BST<'T>
```

Ayırt edici birleşimler ağaç benzeri verileri temsil eden da Desen eşleştirme içinde exhaustiveness yararlanmasını sağlar.

#### <a name="use-requirequalifiedaccess-on-union-types-whose-case-names-are-not-sufficiently-unique"></a>Kullanım `[<RequireQualifiedAccess>]` adları büyük/küçük harf yeterince benzersiz olmayan birleşim türleri

Bir etki alanında aynı adı ayrılmış birlik vakaları gibi farklı işlemler için en iyi ad olduğu kendinizi bulabilirsiniz. Kullanabileceğiniz `[<RequireQualifiedAccess>]` gölgeleme nedeniyle kafa karıştırıcı hataları sıralamasını, bağımlı tetikleme önlemek için büyük/küçük harf adlarını ayırt etmek için `open` deyimleri

#### <a name="hide-the-representations-of-discriminated-unions-for-binary-compatible-apis-if-the-design-of-these-types-is-likely-to-evolve"></a>Bu tür tasarım geliştirilebilen olasılığı varsa, ayrılmış birleşimler temsillerini ikili uyumlu API'leri için Gizle

Birleşimler türleri Bel F# desen eşleştirme forms birleştiren bir programlama modeli için. Daha önce bahsedildiği gibi tasarım bu tür geliştirilebilen olasılığı varsa, somut veri gösterimleri devamlılığımız kaçınmanız gerekir.

Örneğin, ayrılmış bir birleşim gösterimini kullanarak özel veya iç bildirimi gizlenebilir veya bir imza dosyası kullanarak.

```fsharp
type Union =
    private
    | CaseA of int
    | CaseB of string
```

Ayrılmış birleşimler incelemelerin çıkıyorsa, bu sürüm için sabit kitaplığınızı kullanıcı kodu bozmadan bulabilirsiniz. Bunun yerine, değer türünüz üzerinde desen izin vermek için bir veya daha fazla Etkin desenler, devamlılığımız göz önünde bulundurun.

Etkin desenler sağlamak için alternatif bir yolu sağlamak F# gösterme kaçınarak desen tüketicileriyle F# doğrudan birleşim türleri.

### <a name="inline-functions-and-member-constraints"></a>Satır içi işlevleri ve üye kısıtlamaları

#### <a name="define-generic-numeric-algorithms-using-inline-functions-with-implied-member-constraints-and-statically-resolved-generic-types"></a>Satır içi işlevleri statik olarak çözümlenmiş genel türler ve örtük üye kısıtlamaları ile kullanarak genel sayısal algoritmalarının tanımlayın

Aritmetik üye kısıtlamaları ve F# karşılaştırma kısıtlamaları için bir standart olan F# programlama. Örneğin, aşağıdaki kodu düşünün:

```fsharp
let inline highestCommonFactor a b =
    let rec loop a b =
        if a = LanguagePrimitives.GenericZero<_> then b
        elif a < b then loop a (b - a)
        else loop (a - b) b
    loop a b
```

Bu işlev türü şu şekildedir:

```fsharp
val inline highestCommonFactor : ^T -> ^T -> ^T
                when ^T : (static member Zero : ^T)
                and ^T : (static member ( - ) : ^T * ^T -> ^T)
                and ^T : equality
                and ^T : comparison
```

Bu, bir matematik Kitaplığı'ndaki Genel API için uygun bir işlevdir.

#### <a name="avoid-using-member-constraints-to-simulate-type-classes-and-duck-typing"></a>Üye kısıtlamaları türü sınıfları ve yazmaya duck benzetimini yapmak için kullanmaktan kaçının

"Yazarak duck" kullanarak benzetimi mümkündür F# üye kısıtlamaları. Ancak, olun üyeleri bu içinde olmayan genel kullanılması gerekir kullanın F#- için -F# kitaplığı tasarımları. Bilinmeyen ya da standart dışı örtük kısıtlamalarına göre kitaplığı tasarımları eğilimindedir faaliyetini ve belirli bir framework desene bağlı olmak kullanıcı kodu neden olmasıdır.

Ayrıca, bu şekilde üye kısıtlamaları ağır olarak kullanan çok uzun derleme sürelerini sonuçlanabilen olasılığı yoktur.

### <a name="operator-definitions"></a>İşleç tanımları

#### <a name="avoid-defining-custom-symbolic-operators"></a>Özel sembolik işleçleri tanımlamamaya özen gösterin

Özel işleçleri, bazı durumlarda gereklidir ve uygulama kodu büyük bir gövdesi içinde çok kullanışlı notational cihazlar. Yeni bir kitaplık kullanıcıları için adlandırılan işlevlerin genellikle kullanımı daha kolay. Ayrıca, özel sembolik işleçleri belgeye zor olabilir ve kullanıcılar IDE ve arama motorları mevcut kısıtlamalar nedeniyle, işleçler hakkında Yardım aramanızı daha zor bulur.

Sonuç olarak, işlevinizi olarak adlandırılan işlevlerin ve üyeleri yayımlamak ve yalnızca notational belgeler ve bunları sahip bilişsel maliyeti basıyor, ayrıca işleçler için bu işlevi göstermek idealdir.

### <a name="units-of-measure"></a>Ölçü Birimleri

#### <a name="carefully-use-units-of-measure-for-added-type-safety-in-f-code"></a>Ölçü birimleri eklenen tür dikkatli bir şekilde kullanmak F# kod

Ölçü birimleri için ek çok yazma bilgilerini, diğer .NET dilleri ile görüntülendiğinde silinir. .NET bileşenleri, araçları ve yansıma türlerini SAN birimleri göreceği dikkat edin. Örneğin, C# tüketiciler görürsünüz `float` yerine `float<kg>`.

### <a name="type-abbreviations"></a>Tür Kısaltmaları

#### <a name="carefully-use-type-abbreviations-to-simplify-f-code"></a>Tür kısaltmaları'basitleştirmek için dikkatli kullanın F# kod

.NET bileşenleri, araçları ve yansıma kısaltılmış türleri tarafından görülmez. Tür kısaltmaları önemli kullanımını daha karmaşık daha aslında, tüketicilerin karıştırır görünen bir etki alanı da yapabilirsiniz.

#### <a name="avoid-type-abbreviations-for-public-types-whose-members-and-properties-should-be-intrinsically-different-to-those-available-on-the-type-being-abbreviated"></a>Tür kısaltmaları genel türleri, üyeleri ve özellikler için kısaltılmış türünde mevcut kodlar doğası gereği farklı olmalıdır kaçının

Bu durumda, tanımlanan asıl tür gösterimi hakkında çok fazla kısaltılmış türü ortaya çıkarır. Bunun yerine, bir sınıf türü ya da tek örneği ayrılmış bir birleşim kısaltması sarmalama göz önünde bulundurun (ya da performans gerekli olduğunda, bir yapı türü kısaltması sarmalamak için kullanmayı göz önünde bulundurun).

Örneğin, bir çoklu eşlem özel bir durum olarak tanımlamak için daha cazip bir F# eşleyin, örneğin:

```fsharp
type MultiMap<'Key,'Value> = Map<'Key,'Value list>
```

Ancak, mantıksal nokta gösterimi işlemleri bu tür bir harita üzerindeki işlemler aynı değildir: Örneğin, arama işleci eşlendiğini makul. [Temel] anahtar sözlükte yerine bir özel durum oluşturma değilse boş liste döndürür.

## <a name="guidelines-for-libraries-for-use-from-other-net-languages"></a>Diğer .NET dilleri kullanımdan kitaplıkları için yönergeler

Diğer .NET dilleri kullanımdan kitaplıkları tasarlarken, bağlı kalacağını önemli olduğu [.NET kitaplığı tasarım yönergeleri](../../standard/design-guidelines/index.md). Bu belgede, tersine, temel alınan .NET kitaplıkları Bu kitaplıklar etiketlenir F#-kullanan kitaplıkları karşılıklı F# kısıtlama oluşturur. Temel alınan .NET kitaplıkları tasarlama anlamına gelir kullanımını en aza indirerek, tanıdık ve deyimsel API'ler .NET Framework geri kalanı ile tutarlı sağlama F#-Genel API belirli yapılardan. Kurallar, aşağıdaki bölümlerde açıklanmıştır.

### <a name="namespace-and-type-design-for-libraries-for-use-from-other-net-languages"></a>Namespace ve türü tasarım (için diğer .NET dilleri kullanımdan kitaplıkları)

#### <a name="apply-the-net-naming-conventions-to-the-public-api-of-your-components"></a>.NET adlandırma kuralları bileşenlerinizi Genel API için geçerlidir.

Özel kısaltılmış ve .NET büyük/küçük harf kuralları kullanımına dikkat edin.

```fsharp
type pCoord = ...
    member this.theta = ...

type PolarCoordinate = ...
    member this.Theta = ...
```

#### <a name="use-namespaces-types-and-members-as-the-primary-organizational-structure-for-your-components"></a>Ad alanları, türler ve üyeler birincil ait düzenlenmiş yapıyı bileşenleriniz için kullanın.

Genel işlevler içeren tüm dosyaları ile başlaması gereken bir `namespace` bildirimi ve yalnızca genel kullanıma yönelik varlıklar ad alanlarında türleri olması gerekir. Kullanmayın F# modüller.

Genel olmayan modülleri, uygulama kodu, yardımcı program türlerini ve yardımcı işlevlerini tutmak için kullanın.

Statik türler olmalıdır tercih edilen modülleri, bunlar içinde kullanılamaz aşırı yüklerken ve diğer .NET API tasarım kavramları kullanılacak API gelecekteki evrimi izin F# modüller.

Örneğin, aşağıdaki genel API yerine:

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

#### <a name="use-f-record-types-in-vanilla-net-apis-if-the-design-of-the-types-wont-evolve"></a>Kullanım F# türlerinin tasarım evrim Geçiren kalmaz, .NET API vanilla içinde kayıt türleri

F#kayıt türleri, basit bir .NET sınıfı için derleyin. Bu, bazı API'leri basit, kararlı türler için uygundur. Kullanmayı düşünmelisiniz `[<NoEquality>]` ve `[<NoComparison>]` arabirimleri otomatik olarak oluşturulmasını engellemek için öznitelikler. Ayrıca .NET API'lerini vanilla değişebilir kayıt alanları bu kullanıma sunan bir ortak alan kullanarak kaçının. Her zaman bir sınıf gelecekteki gelişimine için daha esnek bir seçenek API'sinin sağlayacağını olup olmadığını göz önünde bulundurun.

Örneğin, aşağıdaki F# kod için genel API sunan bir C# tüketici:

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

#### <a name="hide-the-representation-of-f-union-types-in-vanilla-net-apis"></a>Gösterimini Gizle F# birleşim türleri vanilla .NET API'leri

F#Birleşim türleri genellikle kullanılmaz bileşen sınırları boyunca için bile F#- için -F# kodlama. Bunlar, bileşenler ve kitaplıkları içinde dahili olarak kullanılan bir mükemmel uygulama cihazı.

Bir vanilla .NET API'si tasarlarken, özel bir bildirim ya da bir imza dosyası kullanarak bir birleşim türünün temsili gizleme göz önünde bulundurun.

```fsharp
type PropLogic =
    private
    | And of PropLogic * PropLogic
    | Not of PropLogic
    | True
```

Ayrıca, bir birleşim gösterimi üyeleriyle dahili olarak bir istenen sağlamak için kullandığınız türleri büyütmek. NET yönelik API.

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

#### <a name="design-gui-and-other-components-using-the-design-patterns-of-the-framework"></a>Tasarım GUI ve diğer bileşenleri framework'ün tasarım desenlerini kullanma

Birçok farklı çerçeveler, WinForms, WPF ve ASP.NET gibi .NET içinde kullanılabilir. Bu çerçeveler kullanmak için bileşenleri tasarlıyorsanız adlandırma ve tasarım kuralları her biri için kullanılmalıdır. Örneğin, WPF programlama WPF tasarlarken sınıfları için Tasarım desenleri benimseyin. Kullanıcı arabirimi programlama modelleri için Tasarım desenleri gibi olayları kullanın ve bildirim tabanlı koleksiyonlar olanlar gibi bulunan <xref:System.Collections.ObjectModel>.

### <a name="object-and-member-design-for-libraries-for-use-from-other-net-languages"></a>Nesne ve üye tasarımı (diğer .NET dilleri kullanımdan kitaplıkları)

#### <a name="use-the-clievent-attribute-to-expose-net-events"></a>CLIEvent özniteliği .NET olaylar oluşturmak için kullanın

Oluşturmak bir `DelegateEvent` belirli bir .NET ile temsilci türü bir nesneyi alır ve `EventArgs` (yerine `Event`, yalnızca kullanan `FSharpHandler` türü varsayılan olarak) ve böylece diğer .NET dilleri için benzer şekilde olayların yayımlandığı.

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

#### <a name="expose-asynchronous-operations-as-methods-which-return-net-tasks"></a>Zaman uyumsuz işlemler .NET görevleri döndüren yöntemler olarak kullanıma sunma

Görevler,. NET'te etkin zaman uyumsuz hesaplamalar temsil etmek için kullanılır. Genel olarak daha az bileşimsel görevleridir F# `Async<T>` nesneleri "zaten yürütülüyor." görevleri temsil eder ve paralel bileşim gerçekleştiren veya iptal etme sinyaller yayılmasını Gizle yollarla birlikte oluşturulan olamaz ve diğer bağlam parametreleri.

Ancak, bu rağmen görev döndüren zaman uyumsuz programlama .NET üzerinde standart gösterimi yöntemlerdir.

```fsharp
/// A type in a component designed for use from other .NET languages
type MyType() =

    let compute (x: int): Async<int> = async { ... }

    member this.ComputeAsync(x) = compute x |> Async.StartAsTask
```

Sık olacaktır ayrıca bir açık iptal belirtecini kabul etmek istiyorsanız:

```fsharp
/// A type in a component designed for use from other .NET languages
type MyType() =
    let compute(x: int): Async<int> = async { ... }
    member this.ComputeAsTask(x, cancellationToken) = Async.StartAsTask(compute x, cancellationToken)
```

#### <a name="use-net-delegate-types-instead-of-f-function-types"></a>.NET temsilci türleri yerine kullanmak F# işlev türleri

Burada "F# işlev türleri" ortalama "OK" türleri ister `int -> int`.

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

F# İşlev türü olarak görünür `class FSharpFunc<T,U>` diğer .NET dilleri için dil özelliklerinin ve araçları için temsilci türleri anlayan daha az uygundur. .NET Framework 3.5 veya sonraki bir sürümünü hedefleyen bir daha yüksek sıralı yöntemi yazarken `System.Func` ve `System.Action` temsilcileri, doğru API'lerden bir düşük uyuşmazlıkları şekilde bu API'leri kullanmak, .NET geliştiricilerinin etkinleştirmek için yayımlayın. (.NET Framework 2.0 hedeflenirken sistem tarafından tanımlanan temsilci türleriyle daha sınırlıdır; gibi önceden tanımlanmış temsilci türleri kullanmayı düşünün `System.Converter<T,U>` veya belirli bir temsilci türü tanımlama.)

Diğer taraftan, .NET temsilciler için doğal olmayan F#-kitaplıkları'e yönelik (sonraki bölümüne F#-kitaplıkları'e yönelik). Sonuç olarak, tüm uygulama kullanarak yazmak için temel alınan .NET kitaplıkları için daha yüksek sıralı yöntemleri geliştirirken yaygın bir uygulama stratejisi olan F# işlev türleri ve sonra gerçek F#uygulaması.

#### <a name="use-the-trygetvalue-pattern-instead-of-returning-f-option-values-and-prefer-method-overloading-to-taking-f-option-values-as-arguments"></a>TryGetValue deseni döndürmek yerine kullanmak F# seçenek değerleri ve alma için yöntem aşırı yükü tercih F# seçenek değerleri bağımsız değişkenleri olarak

Kullanım için ortak desenler F# seçenek türünde API'leri daha iyi vanilla içinde uygulanan .NET standart .NET kullanarak API'leri teknikleri tasarlayın. Döndürmek yerine bir F# seçeneği değeri, dönüş türü bool artı out parametresi "TryGetValue" deseni olduğu gibi kullanmayı düşünün. Alma yerine F# seçenek değerleri parametre olarak, yöntem aşırı yüklerken veya isteğe bağlı bağımsız değişkenleri kullanmayı düşünün.

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

#### <a name="use-the-net-collection-interface-types-ienumerablet-and-idictionarykeyvalue-for-parameters-and-return-values"></a>.NET koleksiyonu arabirimini kullanın türleri IEnumerable\<T\> ve IDictionary\<anahtar, değer\> için parametreler ve dönüş değerleri

.NET dizileri gibi somut koleksiyon türlerini kullanmaktan kaçının `T[]`, F# türleri `list<T>`, `Map<Key,Value>` ve `Set<T>`, ve .NET beton koleksiyon türleri gibi `Dictionary<Key,Value>`. .NET kitaplığı tasarım yönergeleri ile ilgili gibi çeşitli koleksiyon türlerini kullanmak iyi bir öneri sahip `IEnumerable<T>`. Diziler bazı kullanımını (`T[]`) grounds performans üzerinde bazı durumlarda, kabul edilebilir. Özellikle dikkat `seq<T>` olduğundan yalnızca F# için diğer ad `IEnumerable<T>`, ve bu nedenle seq genellikle bir vanilla .NET API'si için uygun bir tür.

Yerine F# listeler:

```fsharp
member this.PrintNames(names: string list) =
    ...
```

Kullanım F# dizileri:

```fsharp
member this.PrintNames(names: seq<string>) =
    ...
```

#### <a name="use-the-unit-type-as-the-only-input-type-of-a-method-to-define-a-zero-argument-method-or-as-the-only-return-type-to-define-a-void-returning-method"></a>Birim türü sıfır bağımsız değişken yöntemi tanımlamak için bir yöntem yalnızca giriş türü olarak kullanmak ya da yalnızca dönüş türü void döndüren bir yöntemi tanımlamak için

Birim türü diğer kullanımları kaçının. İyi şunlardır:

```fsharp
✔ member this.NoArguments() = 3

✔ member this.ReturnVoid(x: int) = ()
```

Bu hatalı.

```fsharp
member this.WrongUnit( x: unit, z: int) = ((), ())
```

#### <a name="check-for-null-values-on-vanilla-net-api-boundaries"></a>Temel alınan .NET API sınırlarındaki null değerler olup olmadığını denetleyin

F#uygulama kodu eğilimlidir sabit tasarım desenleri ve kullanım kısıtlamaları için null değişmez değerlerinin nedeniyle daha az boş değerlerle sahip F# türleri. Diğer .NET dilleri genellikle bir değer olarak null çok daha sık kullanın. Bu nedenle, F# bir vanilla .NET API gösterme kod API sınırında null parametreleri denetleyin ve bu değerleri ile geçmesini engellemek F# uygulama kodu. `isNull` İşlevi veya üzerinde desen `null` deseni kullanılabilir.

```fsharp
let checkNonNull argName (arg: obj) =
    match arg with
    | null -> nullArg argName
    | _ -> ()

let checkNonNull` argName (arg: obj) =
    if isNull arg then nullArg argName
    else ()
```

#### <a name="avoid-using-tuples-as-return-values"></a>Dönüş değerleri diziler kullanmaktan kaçının

Bunun yerine, toplama verileri tutan veya birden çok değerleri döndürülecek out parametreleri kullanarak adlandırılmış bir tür döndüren tercih eder. Diziler ve yapı demetleri. NET'te mevcut olmasına karşın (C# dil desteği için çalışan yapı demetleri dahil), bunlar ideal ve beklenen API .NET geliştiricileri için sağlamaz çoğunlukla.

#### <a name="avoid-the-use-of-currying-of-parameters"></a>Parametreleri currying kullanmaktan kaçının

Bunun yerine, çağırma kuralları .NET kullanın `Method(arg1,arg2,…,argN)`.

```fsharp
member this.TupledArguments(str, num) = String.replicate num str
```

İpucu: Herhangi bir .NET dil kullanımdan kitaplıkları tasarladığınız sonra aslında hiçbir yerine bazı Deneysel C# ve Visual Basic Kitaplıklarınızı "Genel Görünüm hemen" Bu dillerin emin olmak için programlama. Ayrıca, kitaplıkları, belgeleri geliştiricileri için beklendiği gibi göründüğünden emin olmak için .NET Reflector ve Visual Studio nesne tarayıcısı gibi araçları da kullanabilirsiniz.

## <a name="appendix"></a>Ek

### <a name="end-to-end-example-of-designing-f-code-for-use-by-other-net-languages"></a>Uçtan uca örnek tasarlama F# diğer .NET dilleri ile kullanmak için kodu

Aşağıdaki sınıf göz önünde bulundurun:

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

Çıkarsanan F# Bu sınıf türü şu şekildedir:

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

Nasıl bir göz atalım bu F# başka bir .NET dilini kullanarak programcıya türü görüntülenir. Örneğin, yaklaşık C# "SIGNATURE" aşağıdaki gibidir:

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

Hakkında dikkat edin gereken bazı önemli noktalar vardır F# burada yapıları temsil eder. Örneğin:

* Bağımsız değişken adları gibi meta veriler korunur.

* F#haline iki bağımsız değişken almaz yöntemleri C# iki bağımsız değişken almaz yöntemleri.

* İşlevler ve listeleri duruma karşılık gelen türler için başvuru F# kitaplığı.

Aşağıdaki kod, bunları hesaba katması için bu kodu ayarlama konusunda gösterir.

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

Çıkarsanan F# kodun türünü şu şekildedir:

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

C# imza artık şu şekilde olur:

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

Temel alınan bir .NET kitaplığının bir parçası olduğu gibi bu tür kullanıma hazırlamak düzeltmeler yaptınız:

* Birden fazla ad ayarlanır: `Point1`, `n`, `l`, ve `f` dönüştü `RadialPoint`, `count`, `factor`, ve `transform`sırasıyla.

* Dönüş türü kullanılan `seq<RadialPoint>` yerine `RadialPoint list` listesini kullanarak yapı değiştirerek `[ ... ]` sırası kullanarak oluşturma `IEnumerable<RadialPoint>`.

* .NET temsilci türü kullanılan `System.Func` yerine bir F# işlev türü.

Bu, çok daha Hoş görünmesi C# kodunda kullanmasını sağlar.
