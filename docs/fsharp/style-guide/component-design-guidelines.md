---
title: 'F # bileşeni tasarım yönergeleri'
description: 'Diğer çağıranlar tarafından tüketim için hazırlanmış F # bileşenleri yazma yönergeleri hakkında bilgi edinin.'
ms.date: 05/14/2018
ms.openlocfilehash: 446cba0f810af9517b655ef5741ddf7a919676d5
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43488293"
---
# <a name="f-component-design-guidelines"></a>F # bileşeni tasarım yönergeleri

Bu belge için F programlama, F # bileşeni tasarım yönergeleri, v14, Microsoft Research dayalı # bileşen tasarım yönergeleri kümesidir ve [başka bir sürümü](https://fsharp.org/specs/component-design-guidelines/) başlangıçta seçkin ve F # Software Foundation tarafından korunur.

Bu belge, F # programlama ile ilgili bilgi sahibi olduğunuz varsayılır. Çoğu kendi Katkıları ve bu kılavuz çeşitli sürümlerini yararlı geribildirim için F # topluluğuna teşekkür ederiz.

## <a name="overview"></a>Genel Bakış

Bu belge, F # bileşeni tasarım ve kodlama ilgili sorunlardan bazılarını bakar. Bir bileşen, aşağıdakilerden herhangi birini gelebilir:

* Dış tüketicileri bir proje olan F # projesinde bir katman.
* Bütünleştirilmiş kod sınırları arasında F # kodu tarafından tüketim için hazırlanmış bir kitaplık.
* Bütünleştirilmiş kod sınırları arasında herhangi bir .NET dil tarafından tüketim için hazırlanmış bir kitaplık.
* Gibi bir paket deposu aracılığıyla dağıtım için hedeflenen bir kitaplık [NuGet](https://nuget.org).

Bu makalede açıklanan teknikleri izleyin [beş iyi F # kodu prensipleri](index.md#five-principles-of-good-f-code), böylece her ikisi de işlevsel yazılımınız ve uygun şekilde programlama nesnesi.

Metodoloji bağımsız olarak, geliştiriciler tarafından kullanılabilen en kolay bir API'si çalışıyorlardı çalışırken bir dizi pratik ve prosaic soruna bileşen ve kitaplık Tasarımcı yüzler. Sertifikasyonuna uygulamasının [.NET kitaplığı tasarım yönergeleri](../../standard/design-guidelines/index.md) kullanmak eğlenceli API'lerden tutarlı özellik kümesi oluşturma doğrultusunda faaliyetidir.

## <a name="general-guidelines"></a>Genel yönergeler

F # kitaplıkları, kitaplığı için hedef kitle bağımsız olarak geçerli birkaç Evrensel yönergeleri vardır.

### <a name="learn-the-net-library-design-guidelines"></a>.NET kitaplığı tasarım yönergeleri edinin

F #, yapıyor kodlama türü ne olursa olsun, bir bilgiye sahip değerli [.NET kitaplığı tasarım yönergeleri](../../standard/design-guidelines/index.md). Diğer çoğu F # ve .NET programcıları bu yönergelere hakkında bilgi sahibi olmanız ve .NET kodu için uygun olması için bekler.

.NET kitaplığı tasarım yönergeleri adlandırma, sınıflar ve arabirimler, üye tasarım (Özellikler, yöntemler, olaylar, vb.) ve daha fazlasını tasarımı ile ilgili genel rehberlik sağlar ve tasarım kılavuzu çeşitli başvuru yararlı ilk noktası olan.

### <a name="add-xml-documentation-comments-to-your-code"></a>XML belge açıklamaları için kodunuzu ekleyin

XML belgeleri ortak API'lerde emin olmak için kitaplık dosyaları bu türleri ve üyeleri ve etkinleştirme yapı belgeleri kullanarak kullanıcıların harika IntelliSense ve Hızlıbilgi alabilirsiniz. Bkz: [XML belgeleri](../language-reference/xml-documentation.md) xmldoc Açıklamalar içinde ek biçimlendirme için kullanılabilen çeşitli xml etiketleri hakkında.

```fsharp
/// A class for representing (x,y) coordinates
type Point =

    /// Computes the distance between this point and another
    member DistanceTo : otherPoint:Point -> float
```

Kısa form XML açıklamaları kullanabilirsiniz (`/// comment`), veya standart XML açıklamaları (`///<summary>comment</summary>`).

### <a name="consider-using-explicit-signature-files-fsi-for-stable-library-and-component-apis"></a>Kararlı kitaplığı ve bileşen API'leri için açık imza dosyalarını (.fsi) kullanmayı düşünün

Bir F # kitaplığı açık imza dosyalarını kullanarak her iki, tam genel yüzey kitaplığınızın bilmeniz yanı sıra ve iç ortak belgeler arasında bir ayrım sağlar sağlamaya yardımcı olan genel API birleştiren bir özetini sağlar Uygulama Ayrıntıları. Genel API değiştirmek için hem uygulama hem de imza dosyalarında yapılacak değişiklikler gerektirerek imza dosyalarını uyuşmazlıkları eklediğiniz unutmayın. Bir API solidified haline gelir ve bundan böyle önemli bir değişiklik beklenen sonuç olarak, imza dosyalarını genellikle yalnızca tanıtılmak.

### <a name="always-follow-best-practices-for-using-strings-in-net"></a>Her zaman .NET dizeleri kullanmak için en iyi uygulamaları izleyin

İzleyin [kullanarak dizeleri de .NET için en iyi](../../standard/base-types/best-practices-strings.md) Kılavuzu. Özellikle, her zaman açık durum *kültürel hedefi* dönüştürme ve karşılaştırma dizeleri, (uygunsa).

## <a name="guidelines-for-f-facing-libraries"></a>F # Kılavuzu-karşılıklı kitaplıkları

Bu bölümde genel F # geliştirme önerileri sunar-karşılıklı kitaplıkları; diğer bir deyişle, F # geliştiricileri tarafından tüketilmesi amaçlanan ortak API'lerde gösterme kitaplıkları. Kitaplık tasarım önerileri çeşitli özellikle F # için geçerlidir. Aşağıdaki öneriler olmaması durumunda .NET kitaplığı tasarım geri dönüş Kılavuzu yönergelerdir.

### <a name="naming-conventions"></a>Adlandırma kuralları

#### <a name="use-net-naming-and-capitalization-conventions"></a>.NET adlandırma ve büyük/küçük harf kuralları kullanma

Aşağıdaki tablo, .NET adlandırma ve büyük/küçük harf kurallarını izler. F # yapılarını de içerecek şekilde küçük eklemeler vardır.

| Oluştur | Servis talebi | Bölümü | Örnekler | Notlar |
|-----------|------|------|----------|-------|
| Somut türleri | PascalCase | İsim / sıfat | Liste, çift, karmaşık | Yapılar, sınıflar, numaralandırmalar, temsilciler, kayıtlar ve birleşimler bunun somut türleridir. Tür adları içinde OCaml geleneksel küçük olsa da, F # türleri için .NET adlandırma şeması BENİMSEDİ.
| DLL'ler           | PascalCase |                 | Fabrikam.Core.dll |  |
| Birleşim etiketleri     | PascalCase | İsim | Bazı, ekleme, başarılı | Bir ön ek, genel API'ler kullanmayın. İsteğe bağlı olarak öneki gibi iç zaman kullanmak ''' takımlar yazın TAlpha = | TBeta | TDelta.'' ' |
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

.NET Kılavuzu kısaltmalar kullanımını engelleyin (örneğin, "kullanmak `OnButtonClick` yerine `OnBtnClick`"). Ortak kısaltmalar gibi `Async` "Zaman uyumsuz için", izin verilir. Bu kılavuz, işlevsel programlama bazen yoksayıldı; Örneğin, `List.iter` "yinelemek için" bir kısaltma kullanır. F #'de büyük ölçüde edileceği kısaltmalar kullanarak bu nedenle, eğilimlidir-için-F # programlama, ancak genel bileşen tasarım hala genellikle kaçınılmalıdır.

#### <a name="avoid-casing-name-collisions"></a>Ad çakışması büyük/küçük harfleri kaçının

.NET Kılavuzu, tek başına büyük/küçük harfleri bazı istemci dillerini (örneğin, Visual Basic) büyük/küçük harfe duyarsızdır beri ad çakışmalarını belirsizliğini ortadan kaldırmak için kullanılamayacağını varsayalım.

#### <a name="use-acronyms-where-appropriate"></a>Uygun yerlerde kısaltmalar kullanın.

Kısaltmalar gibi XML kısaltmalar değildir ve .NET kitaplıkları eden formunda (Xml), yaygın olarak kullanılır. Yalnızca bilinen, tanınmış kısaltmalar kullanılmalıdır.

#### <a name="use-pascalcase-for-generic-parameter-names"></a>Genel parametre adları için PascalCase kullanın

PascalCase genel API'leri, F #'de dahil olmak üzere genel parametre adları için kullanma-karşılıklı kitaplıkları. Özellikle, adları gibi kullanın `T`, `U`, `T1`, `T2` rastgele genel parametreler ve özel adlar, ardından F # için anlamlı olduğunda-karşılıklı kitaplıklarını kullanma gibi adları `Key`, `Value`, `Arg`(ancak değil örneğin `TKey`).

#### <a name="use-either-pascalcase-or-camelcase-for-public-functions-and-values-in-f-modules"></a>Genel işlevler ve F # modüllerdeki değerleri için PascalCase ya da camelCase kullanın

camelCase kullanılmak üzere tasarlanmış genel işlevleri için kullanılan nitelenmemiş (örneğin, `invalidArg`) ve "standart toplama işlevleri için" (örneğin, List.map). Her iki bu durumda, işlev adlarını çok dil anahtar sözcükleri gibi davranır.

### <a name="object-type-and-module-design"></a>Nesne, türü ve modül tasarım

#### <a name="use-namespaces-or-modules-to-contain-your-types-and-modules"></a>Türler ve modüller içerecek şekilde ad alanları veya modülleri kullanma

Her F # dosyasında bir bileşeni, bir ad alanı bildirimi veya modül bildirimi ile başlamalıdır.

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
* Ad alanları içinde bir iç modül olmadıkları sürece F # işlevler içeremez
* Herhangi bir modülden kodunu tek bir dosyada yer almalıdır
* Üst düzey modüller F # işlevleri bir iç modül gerek kalmadan içerebilir

Bir üst düzey ad alanında veya modülde arasında seçim kodun derlenmiş form etkiler ve API'nizi sonunda F # kodu dışında kullanılması diğer .NET dilleri görünümünden böylece etkiler.

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

F #'ta bu durum zaten bir kapanış, sıralama ifadesi veya zaman uyumsuz bir hesaplama gibi başka bir dil yapısı yalıtılan değil, yerine getirilmesi yeterlidir.

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
    abstract Serialize<'T> : preserveRefEq: bool -> value: 'T -> string
    abstract Deserialize<'T> : preserveRefEq: bool -> pickle: string -> 'T
```

Preference için:

```fsharp
type Serializer<'T> = {
    Serialize : bool -> 'T -> string
    Deserialize : bool -> string -> 'T
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
type Vector(x:float) =

    member v.X = x

    static member (*) (vector:Vector, scalar:float) = Vector(vector.X * scalar)

    static member (+) (vector1:Vector, vector2:Vector) = Vector(vector1.X + vector2.X)

let v = Vector(5.0)

let u = v * 10.0
```

Bu kılavuz, bu tür için genel .NET rehberliği karşılık gelir. Ancak, bu F # işlevleri ile birlikte ve yöntemler gibi List.sumBy üye kısıtlamaları ile kullanılmak üzere bu tür şifrelemeye izin vermesi gibi F # kodlama Ayrıca önemli olabilir.

#### <a name="consider-using-compiledname-to-provide-a-net-friendly-name-for-other-net-language-consumers"></a>CompiledName sağlamak üzere kullanmayı göz önünde bulundurun bir. Diğer .NET dil Tüketiciler için NET kolay adı

Bazen bir stilde F # Tüketiciler için ad isteyebilirsiniz (gibi BT'nin görünecek şekilde küçük bir statik üye modülü bağlı işlevi gibi), ancak bütünleştirilmiş kod içine derlenmiş olan farklı bir stil adı vardır. Kullanabileceğiniz `[<CompiledName>]` derlemenin tüketme olmayan F # kodu için farklı bir stil sağlamak için özniteliği.

```fsharp
type Vector(x:float, y:float) =

    member v.X = x
    member v.Y = y

    [<CompiledName("Create")>]
    static member create x y = Vector (x, y)

let v = Vector.create 5.0 3.0
```

Kullanarak `[<CompiledName>]`, olmayan F # derlemenin tüketicileri için .NET adlandırma kuralları kullanabilirsiniz.

#### <a name="use-method-overloading-for-member-functions-if-doing-so-provides-a-simpler-api"></a>Bunu yapmak, böylece daha basit bir API sağlar kullanırsanız, üye işlevleri için yöntemi aşırı yüklemesi

Yöntem aşırı yükü benzer işlevleri gerçekleştirmek için gereken API basitleştirmek için ancak farklı seçenekler ya da bağımsız değişkenler ile güçlü bir araç olan.

```fsharp
type Logger() =

    member this.Log(message) =
        ...
    member this.Log(message, retryPolicy) =
        ...
```

F #'da türlerde bağımsız değişkenler yerine bağımsız değişken sayısı aşırı yüklemeye daha yaygındır.

#### <a name="hide-the-representations-of-record-and-union-types-if-the-design-of-these-types-is-likely-to-evolve"></a>Bu tür tasarım geliştirilebilen olasılığı varsa, kayıt ve birleşim türlerini temsillerini Gizle

Nesneleri somut temsillerini açıklanmaması Örneğin, somut gösterimini <xref:System.DateTime> değerlerin değil .NET kitaplığı tasarım harici, genel API tarafından göstermiştir. Çalışma zamanında, ortak dil çalışma zamanı yürütme kullanılan taahhüt uygulama bilir. Ancak, derlenmiş kod kendisini somut gösterimi bağımlılıkları yerden devam edebiliyorduk değil.

#### <a name="avoid-the-use-of-implementation-inheritance-for-extensibility"></a>Uygulama devralma genişletilebilirliği için kullanmaktan kaçının

F #'ta uygulama devralma nadiren kullanılır. Ayrıca, devralma hiyerarşilerini çoğunlukla karmaşık ve yeni gereksinimleri geldiğinde değiştirmek zor olur. Devralma uygulama yine de F #'ta uyumluluk ve burada bir sorun için en iyi çözüm olduğundan, ancak arabirim uygulaması gibi çok biçimlilik için tasarlarken, F # programlarınızda alternatif teknikleri şirketlerin hedefledikleri nadiren vardır.

### <a name="function-and-member-signatures"></a>İşlev ve üyesi imzaları

#### <a name="use-tuples-for-return-values-when-returning-a-small-number-of-multiple-unrelated-values"></a>Diziler için dönüş değerlerini, birden çok ilişkisiz değer az sayıda döndürülürken kullanın.

Bir dönüş türü bir tanımlama grubu kullanımı iyi bir örnek aşağıda verilmiştir:

```fsharp
val divrem : BigInteger -> BigInteger -> BigInteger * BigInteger
```

İçin dönüş türleri birçok bileşen içeren veya bileşenleri tek bir tanımlanabilen varlıkla ilgili yerlerde, adlandırılmış tür yerine bir demet kullanmayı göz önünde bulundurun.

#### <a name="use-asynct-for-async-programming-at-f-api-boundaries"></a>Kullanım `Async<T>` F # API sınırlarındaki zaman uyumsuz programlama için

Adlı karşılık gelen eşzamanlı bir işlem olup olmadığını `Operation` döndüren bir `T`, zaman uyumsuz işlem adlı sonra `AsyncOperation` döndürürse `Async<T>` veya `OperationAsync` döndürürse `Task<T>`. Başlangıç/bitiş yöntemleri açığa yaygın olarak kullanılan .NET türleri göz önünde bulundurun için kullanarak `Async.FromBeginEnd` F # zaman uyumsuz programlama modeli için bu .NET API'lerini sağlamak için bir cephe olarak genişletme yöntemlerini yazılacak.

```fsharp
type SomeType =
    member this.Compute(x:int) : int =
        ...
    member this.AsyncCompute(x:int) : Async<int> =
        ...

type System.ServiceModel.Channels.IInputChannel with
    member this.AsyncReceive() =
        ...
```

### <a name="exceptions"></a>Özel Durumlar

Bkz: [hata Yönetimi](conventions.md#error-management) özel durumlar, sonuçları ve seçenekleri uygun kullanımı hakkında bilgi edinmek için.

### <a name="extension-members"></a>Uzantı üyeleri

#### <a name="carefully-apply-f-extension-members-in-f-to-f-components"></a>F #'ta uzantı üyeleri F # dikkatli bir şekilde uygulamak-için-F # bileşenleri

F # uzantı üyeleri genellikle yalnızca bir türü modlarından kullanım çoğu ile ilişkili iç işlemlerinin kabini içinde işlemleri için kullanılmalıdır. Yaygın olarak kullanıldığı çeşitli .NET türleri için F #'tan fazla deyimsel API'lerden sağlamaktır:

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

Birleşimler türleri F # desen eşleştirme forms birleştiren bir programlama modeli için dayanır. Daha önce bahsedildiği gibi tasarım bu tür geliştirilebilen olasılığı varsa, somut veri gösterimleri devamlılığımız kaçınmanız gerekir.

Örneğin, ayrılmış bir birleşim gösterimini kullanarak özel veya iç bildirimi gizlenebilir veya bir imza dosyası kullanarak.

```fsharp
type Union =
    private
    | CaseA of int
    | CaseB of string
```

Ayrılmış birleşimler incelemelerin çıkıyorsa, bu sürüm için sabit kitaplığınızı kullanıcı kodu bozmadan bulabilirsiniz. Bunun yerine, değer türünüz üzerinde desen izin vermek için bir veya daha fazla Etkin desenler, devamlılığımız göz önünde bulundurun.

Etkin desenler, F # birleşim türleri doğrudan gösterme kaçınarak desen ile F # tüketiciler sağlamak için alternatif bir yolunu sunuyor.

### <a name="inline-functions-and-member-constraints"></a>Satır içi işlevleri ve üye kısıtlamaları

#### <a name="define-generic-numeric-algorithms-using-inline-functions-with-implied-member-constraints-and-statically-resolved-generic-types"></a>Satır içi işlevleri statik olarak çözümlenmiş genel türler ve örtük üye kısıtlamaları ile kullanarak genel sayısal algoritmalarının tanımlayın

F # programlama için bir standart şunlardır: aritmetik üye kısıtlamaları ve F # karşılaştırma kısıtlamaları. Örneğin, aşağıdaki kodu düşünün:

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

"Yazarak duck" benzetimini yapmak mümkün F # üye kısıtlamaları kullanma. Ancak, yaptığınız üyelerini bu içinde olmayan genel kullanılmalıdır F # kullanma-için-F # kitaplığı tasarımları. Bilinmeyen ya da standart dışı örtük kısıtlamalarına göre kitaplığı tasarımları eğilimindedir faaliyetini ve belirli bir framework desene bağlı olmak kullanıcı kodu neden olmasıdır.

Ayrıca, bu şekilde üye kısıtlamaları ağır olarak kullanan çok uzun derleme sürelerini sonuçlanabilen olasılığı yoktur.

### <a name="operator-definitions"></a>İşleç tanımları

#### <a name="avoid-defining-custom-symbolic-operators"></a>Özel sembolik işleçleri tanımlamamaya özen gösterin

Özel işleçleri, bazı durumlarda gereklidir ve uygulama kodu büyük bir gövdesi içinde çok kullanışlı notational cihazlar. Yeni bir kitaplık kullanıcıları için adlandırılan işlevlerin genellikle kullanımı daha kolay. Ayrıca, özel sembolik işleçleri belgeye zor olabilir ve kullanıcılar IDE ve arama motorları mevcut kısıtlamalar nedeniyle, işleçler hakkında Yardım aramanızı daha zor bulur.

Sonuç olarak, işlevinizi olarak adlandırılan işlevlerin ve üyeleri yayımlamak ve yalnızca notational belgeler ve bunları sahip bilişsel maliyeti basıyor, ayrıca işleçler için bu işlevi göstermek idealdir.

### <a name="units-of-measure"></a>Ölçü Birimleri

#### <a name="carefully-use-units-of-measure-for-added-type-safety-in-f-code"></a>F # kodunda eklenen tür güvenliği için dikkatli bir şekilde ölçü kullanın.

Ölçü birimleri için ek çok yazma bilgilerini, diğer .NET dilleri ile görüntülendiğinde silinir. .NET bileşenleri, araçları ve yansıma türlerini SAN birimleri göreceği dikkat edin. Örneğin, C# tüketiciler görürsünüz `float` yerine `float<kg>`.

### <a name="type-abbreviations"></a>Tür Kısaltmaları

#### <a name="carefully-use-type-abbreviations-to-simplify-f-code"></a>Tür kısaltmaları'F # kodu basitleştirmek için dikkatli kullanın

.NET bileşenleri, araçları ve yansıma kısaltılmış türleri tarafından görülmez. Tür kısaltmaları önemli kullanımını daha karmaşık daha aslında, tüketicilerin karıştırır görünen bir etki alanı da yapabilirsiniz.

#### <a name="avoid-type-abbreviations-for-public-types-whose-members-and-properties-should-be-intrinsically-different-to-those-available-on-the-type-being-abbreviated"></a>Tür kısaltmaları genel türleri, üyeleri ve özellikler için kısaltılmış türünde mevcut kodlar doğası gereği farklı olmalıdır kaçının

Bu durumda, tanımlanan asıl tür gösterimi hakkında çok fazla kısaltılmış türü ortaya çıkarır. Bunun yerine, bir sınıf türü ya da tek örneği ayrılmış bir birleşim kısaltması sarmalama göz önünde bulundurun (ya da performans gerekli olduğunda, bir yapı türü kısaltması sarmalamak için kullanmayı göz önünde bulundurun).

Örneğin, bir çoklu eşlem örneğin F # harita, özel bir durum olarak tanımlamak için daha cazip şöyledir:

```fsharp
type MultiMap<'Key,'Value> = Map<'Key,'Value list>
```

Ancak, mantıksal nokta gösterimi işlemleri bu tür bir harita üzerindeki işlemler aynı değildir: Örneğin, arama işleci eşlendiğini makul. [Temel] anahtar sözlükte yerine bir özel durum oluşturma değilse boş liste döndürür.

## <a name="guidelines-for-libraries-for-use-from-other-net-languages"></a>Diğer .NET dilleri kullanımdan kitaplıkları için yönergeler

Diğer .NET dilleri kullanımdan kitaplıkları tasarlarken, bağlı kalacağını önemli olduğu [.NET kitaplığı tasarım yönergeleri](../../standard/design-guidelines/index.md). Bu belgede, bu kitaplıkları F # aksine, temel alınan .NET kitaplıkları olarak etiketlenmiş-kullanan F # kitaplıkları karşılıklı kısıtlama oluşturur. Temel alınan .NET kitaplıkları tasarlama anlamına gelir F # kullanımını en aza indirerek, tanıdık ve deyimsel API'ler .NET Framework geri kalanı ile tutarlı sağlama-Genel API belirli yapılardan. Kurallar, aşağıdaki bölümlerde açıklanmıştır.

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

Genel işlevler içeren tüm dosyaları ile başlaması gereken bir `namespace` bildirimi ve yalnızca genel kullanıma yönelik varlıklar ad alanlarında türleri olması gerekir. F # modülleri kullanmayın.

Genel olmayan modülleri, uygulama kodu, yardımcı program türlerini ve yardımcı işlevlerini tutmak için kullanın.

F # modüllerde kullanılamaz aşırı yüklerken ve diğer .NET API tasarım kavramları kullanılacak API gelecekteki evrimi sağlarlar gibi statik türler modülleri tercih edilmelidir.

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

#### <a name="use-f-record-types-in-vanilla-net-apis-if-the-design-of-the-types-wont-evolve"></a>Türleri tasarımı evrim Geçiren olmaz .NET API'lerini vanilla içinde F # kayıt türleri kullanın

F # kayıt türleri, basit bir .NET sınıfı için derleyin. Bu, bazı API'leri basit, kararlı türler için uygundur. Kullanmayı düşünmelisiniz `[<NoEquality>]` ve `[<NoComparison>]` arabirimleri otomatik olarak oluşturulmasını engellemek için öznitelikler. Ayrıca .NET API'lerini vanilla değişebilir kayıt alanları bu kullanıma sunan bir ortak alan kullanarak kaçının. Her zaman bir sınıf gelecekteki gelişimine için daha esnek bir seçenek API'sinin sağlayacağını olup olmadığını göz önünde bulundurun.

Örneğin, aşağıdaki F # kodu bir C# tüketiciye Genel API sunar:

F # İÇİN:

```fsharp
[<NoEquality; NoComparison>]
type MyRecord =
    { FirstThing : int
        SecondThing : string }
```

C# İÇİN:

```csharp
public sealed class MyRecord
{
    public MyRecord(int firstThing, string secondThing);
    public int FirstThing { get; }
    public string SecondThing { get; }
}
```

#### <a name="hide-the-representation-of-f-union-types-in-vanilla-net-apis"></a>F # birleşim türleri vanilla .NET API'lerini gösterimini Gizle

F # birleşim türleri genellikle kullanılmaz bileşen sınırları boyunca bile F # '-için-F # kodlama. Bunlar, bileşenler ve kitaplıkları içinde dahili olarak kullanılan bir mükemmel uygulama cihazı.

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

type MyEventArgs(x:int) =
    inherit System.EventArgs()
    member this.X = x

    /// A type in a component designed for use from other .NET languages
type MyGoodType() =
    let myEv = new DelegateEvent<EventHandler<MyEventArgs>>()

    [<CLIEvent>]
    member this.MyEvent = myEv.Publish
```

#### <a name="expose-asynchronous-operations-as-methods-which-return-net-tasks"></a>Zaman uyumsuz işlemler .NET görevleri döndüren yöntemler olarak kullanıma sunma

Görevler,. NET'te etkin zaman uyumsuz hesaplamalar temsil etmek için kullanılır. Genel olarak F # ' az bileşimsel görevleridir `Async<T>` nesneleri "zaten yürütülüyor." görevleri temsil eder ve paralel bileşim gerçekleştiren veya iptal etme sinyaller ve diğer yayılmasını Gizle şekillerde bir araya oluşan olamaz Bağlam parametreleri.

Ancak, bu rağmen görev döndüren zaman uyumsuz programlama .NET üzerinde standart gösterimi yöntemlerdir.

```fsharp
/// A type in a component designed for use from other .NET languages
type MyType() =

    let compute (x: int) : Async<int> = async { ... }

    member this.ComputeAsync(x) = compute x |> Async.StartAsTask
```

Sık olacaktır ayrıca bir açık iptal belirtecini kabul etmek istiyorsanız:

```fsharp
/// A type in a component designed for use from other .NET languages
type MyType() =
    let compute(x:int) : Async<int> = async { ... }
    member this.ComputeAsTask(x, cancellationToken) = Async.StartAsTask(compute x, cancellationToken)
```

#### <a name="use-net-delegate-types-instead-of-f-function-types"></a>F # işlevi türleri yerine .NET temsilci türleri kullanın

Burada "F # işlevi türleri", "OK" türleri ister anlamına gelir `int -> int`.

Bunun yerine:

```fsharp
member this.Transform(f:int->int) =
    ...
```

Bunu yapın:

```fsharp
member this.Transform(f:Func<int,int>) =
    ...
```

F # işlev türüyle olarak görünür `class FSharpFunc<T,U>` diğer .NET dilleri için dil özelliklerinin ve araçları için temsilci türleri anlayan daha az uygundur. .NET Framework 3.5 veya sonraki bir sürümünü hedefleyen bir daha yüksek sıralı yöntemi yazarken `System.Func` ve `System.Action` temsilcileri, doğru API'lerden bir düşük uyuşmazlıkları şekilde bu API'leri kullanmak, .NET geliştiricilerinin etkinleştirmek için yayımlayın. (.NET Framework 2.0 hedeflenirken sistem tarafından tanımlanan temsilci türleriyle daha sınırlıdır; gibi önceden tanımlanmış temsilci türleri kullanmayı düşünün `System.Converter<T,U>` veya belirli bir temsilci türü tanımlama.)

Diğer taraftan, .NET temsilciler F # için doğal olmayan-kitaplıkları'e yönelik (F # üzerinde bir sonraki bölüme bakın-kitaplıkları'e yönelik). Sonuç olarak, tüm F # işlevi türleri kullanarak uygulama yazın ve ardından üzerine gerçek F # ince bir cephe olarak temsilcileri kullanma Genel API oluşturmak için temel alınan .NET kitaplıkları için daha yüksek sıralı yöntemleri geliştirirken yaygın bir uygulama stratejisi olduğu uygulama.

#### <a name="use-the-trygetvalue-pattern-instead-of-returning-f-option-values-and-prefer-method-overloading-to-taking-f-option-values-as-arguments"></a>F # seçenek değerlerini döndürmek yerine TryGetValue deseni kullanılacak ve F # seçenek değerleri bağımsız değişkenler olarak almak için yöntemi aşırı yüklemesi'tercih et

F # seçenek türünün API'lerindeki kullanım ortak desenleri daha iyi vanilla içinde uygulanan .NET standart .NET kullanarak API'leri teknikleri tasarlayın. Bir F # seçenek değeri döndürmek yerine, dönüş türü bool artı out parametresi "TryGetValue" deseni olduğu gibi kullanmayı düşünün. Ve F # seçeneği değerleri parametre olarak almak yerine, yöntem aşırı yükleme ya da isteğe bağlı bağımsız değişkenler kullanmayı düşünün.

```fsharp
member this.ReturnOption() = Some 3

member this.ReturnBoolAndOut(outVal : byref<int>) =
    outVal <- 3
    true

member this.ParamOption(x : int, y : int option) =
    match y with
    | Some y2 -> x + y2
    | None -> x

member this.ParamOverload(x : int) = x

member this.ParamOverload(x : int, y : int) = x + y
```

#### <a name="use-the-net-collection-interface-types-ienumerablet-and-idictionarykeyvalue-for-parameters-and-return-values"></a>.NET koleksiyonu arabirimini kullanın türleri IEnumerable\<T\> ve IDictionary\<anahtar, değer\> için parametreler ve dönüş değerleri

.NET dizileri gibi somut koleksiyon türlerini kullanmaktan kaçının `T[]`, F # türleri `list<T>`, `Map<Key,Value>` ve `Set<T>`, ve .NET beton koleksiyon türleri gibi `Dictionary<Key,Value>`. .NET kitaplığı tasarım yönergeleri ile ilgili gibi çeşitli koleksiyon türlerini kullanmak iyi bir öneri sahip `IEnumerable<T>`. Diziler bazı kullanımını (`T[]`) grounds performans üzerinde bazı durumlarda, kabul edilebilir. Özellikle dikkat `seq<T>` yalnızca F # için diğer ad `IEnumerable<T>`, ve bu nedenle seq genellikle bir vanilla .NET API'si için uygun bir tür.

F # listelerinde yerine:

```fsharp
member this.PrintNames(names : string list) =
    ...
```

F # dizileri kullanın:

```fsharp
member this.PrintNames(names : seq<string>) =
    ...
```

#### <a name="use-the-unit-type-as-the-only-input-type-of-a-method-to-define-a-zero-argument-method-or-as-the-only-return-type-to-define-a-void-returning-method"></a>Birim türü sıfır bağımsız değişken yöntemi tanımlamak için bir yöntem yalnızca giriş türü olarak kullanmak ya da yalnızca dönüş türü void döndüren bir yöntemi tanımlamak için

Birim türü diğer kullanımları kaçının. İyi şunlardır:

```fsharp
✔ member this.NoArguments() = 3

✔ member this.ReturnVoid(x : int) = ()
```

Bu hatalı.

```fsharp
member this.WrongUnit( x:unit, z:int) = ((), ())
```

#### <a name="check-for-null-values-on-vanilla-net-api-boundaries"></a>Temel alınan .NET API sınırlarındaki null değerler olup olmadığını denetleyin

F # uygulama kodu, sabit tasarım desenleri ve F # türleri için null değişmez değerlerinin kullanma kısıtlamaları nedeniyle daha az boş değerlere sahip eğilimindedir. Diğer .NET dilleri genellikle bir değer olarak null çok daha sık kullanın. Bu nedenle, bir .NET API vanilla gösterme F # kodu API sınırında null parametreleri denetleyin ve bu değerleri F # uygulama koduna daha derin geçmesini engeller. `isNull` İşlevi veya üzerinde desen `null` deseni kullanılabilir.

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

Bunun yerine, çağırma kuralları .NET kullanın ``Method(arg1,arg2,…,argN)``.

```fsharp
member this.TupledArguments(str, num) = String.replicate num str
```

İpucu: herhangi bir .NET dil kullanımdan kitaplıkları tasarlıyorsanız, ardından yoktur gerçekten bazı Deneysel C# ve Visual Basic Kitaplıklarınızı "Genel Görünüm hemen" Bu dillerin emin olmak için programlama yapmadan gibisi yoktur. Ayrıca, kitaplıkları, belgeleri geliştiricileri için beklendiği gibi göründüğünden emin olmak için .NET Reflector ve Visual Studio nesne tarayıcısı gibi araçları da kullanabilirsiniz.

## <a name="appendix"></a>Ek

### <a name="end-to-end-example-of-designing-f-code-for-use-by-other-net-languages"></a>Uçtan uca örneği kullanmak için F # kodu tarafından diğer .NET dilleri tasarlama

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

Bu sınıf çıkarsanan F # türü şu şekildedir:

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

Bu F # tür başka bir .NET dilini kullanarak programcıya görüntülenme şeklini bir bakalım. Örneğin, yaklaşık C# "SIGNATURE" aşağıdaki gibidir:

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

Nasıl F # burada yapıları temsil hakkında dikkat edin gereken bazı önemli noktalar vardır. Örneğin:

* Bağımsız değişken adları gibi meta veriler korunur.

* İki bağımsız değişken almaz F # yöntemleri iki bağımsız değişken almaz C# yöntemler olur.

* F # kitaplığı karşılık gelen türler için başvuru işlevleri ve listeleri olur.

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

Kod çıkarsanan F # türü şu şekildedir:

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

* .NET temsilci türü kullanılan `System.Func` yerine bir F # işlev türü.

Bu, çok daha Hoş görünmesi C# kodunda kullanmasını sağlar.
