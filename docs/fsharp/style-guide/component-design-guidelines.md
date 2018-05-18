---
title: 'F # bileşen tasarım yönergeleri'
description: 'Tüketim için diğer arayanlar tarafından kullanılmaya F # bileşenlerini yazmak için kılavuzları hakkında bilgi edinin.'
ms.date: 05/14/2018
ms.openlocfilehash: 7859baac76be01b2cfbdc8602b6cc417cfe5106f
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2018
---
# <a name="f-component-design-guidelines"></a>F # bileşen tasarım yönergeleri

Bu belge bileşen tasarım yönergeleri F programlama, F # bileşen tasarım yönergeleri, v14, Microsoft Research dayalı # kümesidir ve [başka bir sürümü](https://fsharp.org/specs/component-design-guidelines/) başlangıçta seçkin ve F # yazılım Foundation tarafından korunur.

Bu belge, F # programlama ile bildiğinizi varsayar. Çok F # topluluk katkılarına ve bu kılavuz çeşitli sürümlerinde yararlı geri bildirim teşekkür ederiz.

## <a name="overview"></a>Genel Bakış

Bu belge, F # bileşen tasarım ve kodlama ilgili sorunlardan bazıları bakar. Bir bileşenin aşağıdakilerden herhangi birini anlamına gelebilir:

* Bu proje dış tüketicileri sahip F # projenize bir katmanı.
* Derleme sınırlarında F # koduna göre tüketimi için amaçlanan bir kitaplığı.
* Tüketimi için derleme sınırları ötesinde herhangi bir .NET dil tarafından kullanılmaya kitaplığı.
* Bir paket deposu aracılığıyla dağıtım gibi yönelik bir kitaplık [NuGet](https://nuget.org).

Bu makalede açıklanan teknikleri izleyin [iyi F # kodu beş ilkeleri](index.md#five-principles-of-good-f-code), dolayısıyla her ikisi de işlevsel kullanmasına ve uygun şekilde programlama nesnesi.

Yönteme bağımsız olarak bileşeni ve kitaplık Tasarımcısı geliştiriciler tarafından en kolay kullanılabilir bir API hazırlanması çalışırken bir dizi pratik ve prosaic sorununu yüzler. Sertifikasyonuna uygulamasının [.NET kitaplığı tasarım yönergeleri](../../standard/design-guidelines/index.md) tutarlı bir dizi tüketmeye eğlenceli API oluşturma doğrultusunda ilerletebilir.

## <a name="general-guidelines"></a>Genel yönergeleri

Kitaplık için hedef kitle bağımsız olarak F # kitaplıkları, uygulamak birkaç Evrensel yönergeleri vardır.

### <a name="learn-the-net-library-design-guidelines"></a>.NET kitaplığı tasarım yönergeleri öğrenin

Kodlama F #, gittiğini türü ne olursa olsun, bir bilgiye sahip değerli [.NET kitaplığı tasarım yönergeleri](../../standard/design-guidelines/index.md). Çoğu diğer F # .NET programcıları bu yönergelere hakkında bilgi sahibi olmanız ve .NET kodu için uygun olması için bekler.

.NET kitaplığı tasarım yönergeleri adlandırma, sınıflar ve arabirimler, üye tasarım (özellikleri, yöntemleri, olaylar, vb.) ve daha fazlasını tasarımı ile ilgili genel rehberlik sağlar ve Tasarım Kılavuzu, çeşitli başvurusunu yararlı bir ilk noktası.

### <a name="add-xml-documentation-comments-to-your-code"></a>XML belge açıklamaları için kodunuzu ekleyin

XML belgeleri ortak API'ler üzerinde olun bu türleri ve üyeleri ve etkinleştir yapı belgelerinin kullanarak kitaplık için dosyaları, kullanıcıların harika IntelliSense ve Quıckınfo alabilirsiniz. Bkz: [XML belgeleri](../language-reference/xml-documentation.md) xmldoc açıklamaları içinde ek biçimlendirme için kullanılan çeşitli xml etiketleri hakkında.

```fsharp
/// A class for representing (x,y) coordinates
type Point =

    /// Computes the distance between this point and another
    member DistanceTo : otherPoint:Point -> float
```

Kısa form XML açıklamaları kullanabilirsiniz (`/// comment`), veya standart XML yorum (`///<summary>comment</summary>`).

### <a name="consider-using-explicit-signature-files-fsi-for-stable-library-and-component-apis"></a>Kararlı kitaplığı ve bileşen API'leri için açık imza dosyalarını (.fsi) kullanmayı düşünün

Bir F # kitaplığı açık imza dosyalarını kullanarak her iki, tam ortak yüzeyini kitaplığınızın bilmeniz yanı sıra, ortak belgeler arasında iç temiz bir ayrımı sağlar sağlamaya yardımcı olan genel API'si kısa bir özetini sunar Uygulama Ayrıntıları. Genel API uygulaması ve imza dosyalarında yapılacak değişiklikler gerektirerek değiştirmeye imza dosyalarını uyuşmazlık eklediğiniz unutmayın. Bir API solidified haline gelir ve artık önemli ölçüde değişiklik bekleniyor olduğunda sonuç olarak, imza dosyalarını genellikle yalnızca ortaya çıkan.

### <a name="always-follow-best-practices-for-using-strings-in-net"></a>Her zaman .NET dizeleri kullanmak için en iyi uygulamaları izleyin

İzleyin [.NET kullanarak dizelerde için en iyi uygulamaları](../../standard/base-types/best-practices-strings.md) Kılavuzu. Özellikle, her zaman açıkça durum *kültürel hedefi* dönüştürme ve dizeleri karşılaştırma (uygunsa).

## <a name="guidelines-for-f-facing-libraries"></a>F # için yönergeler-kitaplıkları karşılıklı

Bu bölüm ortak F # geliştirme için öneriler sunar-kitaplıkları; karşılıklı diğer bir deyişle, F # geliştiriciler tarafından kullanılması amaçlanan ortak API'ler gösterme kitaplıkları. Kitaplık tasarım önerilerini çeşitli özellikle F # için uygulanabilir. İzleyin belirli öneriler olmaması durumunda, .NET kitaplığı tasarım geri dönüş Kılavuzu yönergelerdir.

### <a name="naming-conventions"></a>Adlandırma kuralları

#### <a name="use-net-naming-and-capitalization-conventions"></a>.NET adlandırma ve büyük/küçük harf kuralları kullanın

Aşağıdaki tabloda .NET adlandırma ve büyük/küçük harf kuralları izler. F # yapılarını de içerecek şekilde küçük eklemeler vardır.

| Oluştur | Durumu | Bölümü | Örnekler | Notlar |
|-----------|------|------|----------|-------|
| Somut türleri | PascalCase | İsim / sıfat | Liste, Double, karmaşık | Yapılar, sınıflar, numaralandırmalar, temsilciler, kaydeder ve birleşimleri bunun somut türleridir. Tür adları OCaml geleneksel olarak küçük olmakla birlikte, F # türleri için .NET adlandırma şeması benimsemiştir.
| DLL'ler           | PascalCase |                 | Fabrikam.Core.dll |  |
| Birleşim etiketleri     | PascalCase | isim | Bazı, ekleme, başarılı | Bir önek ortak API'leri kullanmayın. İsteğe bağlı olarak bir önek gibi iç olduğunda kullanın ''' takımlar yazın TAlpha = | TBeta | TDelta.'' ' |
| Olay          | PascalCase | Fiil | ValueChanged / ValueChanging |  |
| Özel Durumlar     | PascalCase |      | WebException | Adı "Özel durum" ile bitmelidir. |
| Alan          | PascalCase | isim | Geçerli ad  | |
| Arabirim türleri |  PascalCase | İsim / sıfat | IDisposable | Adı "T" ile başlamalıdır. |
| Yöntem |  PascalCase |  Fiil | ToString | |
| Ad Alanı | PascalCase | | Microsoft.FSharp.Core | Genellikle kullanması `<Organization>.<Technology>[.<Subnamespace>]`, teknolojisi organizasyonu bağımsızsa ancak kuruluş bırakın. |
| Parametreler | camelCase | isim |  typeName, dönüştürme ve aralığı | |
| let değerleri (iç) | camelCase veya PascalCase | İsim / fiil |  getValue, myTable |
| let değerleri (harici) | camelCase veya PascalCase | İsim/fiil  | List.map, Dates.Today | let bağlı genellikle geleneksel işlevsel tasarım desenleri aşağıdaki durumlarda ortak değerlerdir. Ancak, diğer .NET dillerinden tanımlayıcı kullanılabilir olduğunda genellikle PascalCase kullanın. |
| Özellik  | PascalCase  | İsim / sıfat  | IsEndOfFile, arka plan rengi  | Boole özellikleri genellikle olduğu ve olabilir ve IsEndOfFile olduğu gibi yok IsNotEndOfFile ileticiden onaylama olması gerekir.

#### <a name="avoid-abbreviations"></a>Kısaltmalar kaçının

.NET yönergeleri kısaltmalar kullanımı önerilmemektedir (örneğin, "kullanmak `OnButtonClick` yerine `OnBtnClick`"). Ortak kısaltmalar gibi `Async` "Zaman uyumsuz için", izin verilir. Bu kılavuz için işlevsel programlama bazen göz ardı edilir; Örneğin, `List.iter` "yinelemek için" kısaltma kullanır. F # daha büyük ölçüde kabul edileceği kısaltmalar kullanarak bu nedenle, eğilimlidir-için-F # programlama, ancak hala genellikle ortak bileşen tasarımında kaçınılmalıdır.

#### <a name="avoid-casing-name-collisions"></a>Ad çakışmaları büyük/küçük harfleri kaçının

Tek başına büyük/küçük harfleri bazı istemci dillerini (örneğin, Visual Basic) büyük/küçük harfe duyarsızdır sonra ad çakışması belirsizliğini ortadan kaldırmak için kullanılamayacağını .NET yönergeleri söyleyin.

#### <a name="use-acronyms-where-appropriate"></a>Uygun olan yerlerde kısaltmalar kullanın

Kısaltmalar XML gibi kısaltmalar değildir ve .NET kitaplıklarına eden formunda (Xml) yaygın olarak kullanılır. Yalnızca iyi bilinen, tanınmış kısaltmalar kullanılmalıdır.

#### <a name="use-pascalcase-for-generic-parameter-names"></a>Genel parametre adları için PascalCase kullanın

PascalCase genel API'leri, F #'de dahil olmak üzere genel parametre adlarında kullanma-kitaplıkları karşılıklı. Özellikle, adları gibi kullanın `T`, `U`, `T1`, `T2` rasgele genel parametreler için ve belirli adları, sonra F # için anlamlı-karşılıklı kitaplıklarını kullanma gibi adları `Key`, `Value`, `Arg`(ancak olmayan örneğin `TKey`).

#### <a name="use-either-pascalcase-or-camelcase-for-public-functions-and-values-in-f-modules"></a>Genel işlevler ve F # modülleri değerleri için PascalCase veya camelCase kullanın

camelCase kullanılmak üzere tasarlanmış ortak işlevleri için kullanılan nitelenmemiş (örneğin, `invalidArg`) ve "standart toplama işlevleri için" (örneğin, List.map). Her iki bu durumda işlev adları çok dilindeki anahtar sözcükler gibi davranır.

### <a name="object-type-and-module-design"></a>Nesne, türü ve modül tasarım

#### <a name="use-namespaces-or-modules-to-contain-your-types-and-modules"></a>Ad alanları veya modülleri türleri ve modülleri içerecek şekilde kullanın

Her F # dosyasında bir bileşeni, bir ad alanı bildirimini veya bir modül bildirimi ile başlamanız gerekir.

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

Modülleri ve ad alanlarını kullanarak en üst düzeyinde kod düzenleme arasındaki farklar aşağıdaki gibidir:

* Ad alanları, birden çok dosya yayılabilir
* Bir iç modülü içinde olmadığı sürece ad alanları F # işlevleri içeremez.
* Kod belirli herhangi bir modül için tek bir dosyada yer almalıdır
* Üst düzey modüller F # işlevleri iç modül gerek kalmadan içerebilir

En üst düzey ad veya modülü arasında seçim derlenmiş formun kodunun etkiler ve böylece diğer .NET dilleri görünümünden API'nizi sonunda F # kodu dışında kullanılması etkileyecektir.

#### <a name="use-methods-and-properties-for-operations-intrinsic-to-object-types"></a>Nesne türlerine iç işlemleri için yöntemlerini ve özelliklerini kullanma

Nesneler ile çalışırken, kaynaklarda işlevselliği yöntemleri ve özellikleri ilgili türdeki olarak uygulanır sağlamak en iyisidir.

```fsharp
type HardwareDevice() =

    member this.ID = ...

    member this.SupportedProtocols = ...

type HashTable<'Key,'Value>(comparer: IEqualityComparer<'Key>) =

    member this.Add(key, value) = ...

    member this.ContainsKey(key) = ...

    member this.ContainsValue(value) = ...
```

İşlevselliği toplu belirli bir üye için mutlaka bu üyede uygulanmadı, ancak bu işlevselliği tüketilebilir parçası olması gerekir.

#### <a name="use-classes-to-encapsulate-mutable-state"></a>Değişebilir durumu kapsülleyen sınıflarını kullanma

F #'ta bu yalnızca durum zaten kapatılmak üzere, dizisi ifade veya zaman uyumsuz hesaplama gibi başka bir dil yapısı yalıtılan değil, yerine getirilmesi gerekir.

```fsharp
type Counter() =
    // let-bound values are private in classes.
    let mutable count = 0

    member this.Next() =
        count <- count + 1
        count
```

#### <a name="use-interfaces-to-group-related-operations"></a>Grubuna arabirimler kullanacak ilgili işlemler

Bir işlemler kümesini temsil eden arabirim türlerini kullanın. Bu işlevlerin diziler veya işlevlerin kayıtları gibi diğer seçenekleri için tercih edilir.

```fsharp
type Serializer =
    abstract Serialize<'T> : preserveRefEq: bool -> value: 'T -> string
    abstract Deserialize<'T> : preserveRefEq: bool -> pickle: string -> 'T
```

İçinde preference için:

```fsharp
type Serializer<'T> = {
    Serialize : bool -> 'T -> string
    Deserialize : bool -> string -> 'T
}
```

İlk sınıf kavramları ne Functors normalde verirsiniz elde etmek için kullanabileceğiniz .NET içinde arabirimlerdir. Ayrıca, bunlar işlevlerin kayıtları olamaz, programa varlıksal türleri kodlamak için kullanılabilir.

#### <a name="use-a-module-to-group-functions-which-act-on-collections"></a>Bir modül davranan Grup işlevlere koleksiyonlarında kullanın

Koleksiyon türü tanımladığınızda, standart bir işlemler kümesini ister sağlamayı düşünün `CollectionType.map` ve `CollectionType.iter`) için yeni koleksiyon türleri.

```fsharp
module CollectionType =
    let map f c =
        ...
    let iter f c =
        ...
```

Bu tür bir modül eklerseniz, FSharp.Core içinde bulunan işlevleri için standart adlandırma kuralları izleyin.

#### <a name="use-a-module-to-group-functions-for-common-canonical-functions-especially-in-math-and-dsl-libraries"></a>Ortak, kurallı işlevlerde, özellikle matematik ve DSL kitaplıkları için Grup işlevleri bir modüle kullanın

Örneğin, `Microsoft.FSharp.Core.Operators` en üst düzey işlevleri otomatik olarak açılan bir koleksiyonudur (gibi `abs` ve `sin`) FSharp.Core.dll tarafından sağlanan.

Benzer şekilde, bir istatistik kitaplık işlevleri sahip bir modül içerebilir `erf` ve `erfc`, bu modül burada açıkça veya otomatik olarak açılacak şekilde tasarlanmıştır.

#### <a name="consider-using-requirequalifiedaccess-and-carefully-apply-autoopen-attributes"></a>RequireQualifiedAccess kullanmayı düşünün ve dikkatle AutoOpen öznitelikleri uygulama

Ekleme `[<RequireQualifiedAccess>]` öznitelik bir modüle, modül açılmamış ve koşullu erişim modülü öğelere başvurular açık gerektirir gösterir. Örneğin, `Microsoft.FSharp.Collections.List` modülü bu öznitelik içeriyor.

Bu, İşlevler ve değerleri modüldeki diğer modüllerdeki adlarıyla çakışma olasılığı adlara sahip durumunda faydalı olur. Koşullu erişim gerektiren bir kitaplık evolvability ve uzun süreli bakım önemli ölçüde artırabilir.

Ekleme `[<AutoOpen>]` özniteliği bir modüle anlamına gelir içeren ad alanı açıldığında modülü açılacak. `[<AutoOpen>]` Özniteliği de uygulanabilir bir derlemeye derlemesi başvurulduğunda otomatik olarak açılan bir modülü belirtmek için.

Örneğin, bir istatistik Kitaplığı **MathsHeaven.Statistics** içerebilecek bir `module MathsHeaven.Statistics.Operators` işlevleri içeren `erf` ve `erfc`. Bu modül olarak işaretlemek makul `[<AutoOpen>]`. Yani `open MathsHeaven.Statistics` de bu modül açılır ve adlarını Getir `erf` ve `erfc` kapsam içine. Başka bir iyi kullanımını `[<AutoOpen>]` genişletme yöntemleri içeren modüller için değil.

Aşırı `[<AutoOpen>]` müşteri adayları polluted ad alanları ve öznitelik dikkatli kullanılmalıdır. Belirli alanlarında kullanmalıdır belirli kitaplıkları için `[<AutoOpen>]` daha iyi kullanılabilirlik yol açabilir.

#### <a name="consider-defining-operator-members-on-classes-where-using-well-known-operators-is-appropriate"></a>İyi bilinen işleçleri kullanarak uygun olduğu sınıflarında işleci üyelerini tanımlama göz önünde bulundurun

Bazen sınıfları vektörlerinin gibi matematiksel yapıları model oluşturmak için kullanılır. İyi bilinen işleçleri Modellenen etki alanı sahip olduğunda, onları sınıfa iç üye olarak tanımlayarak yardımcı olur.

```fsharp
type Vector(x:float) =

    member v.X = x

    static member (*) (vector:Vector, scalar:float) = Vector(vector.X * scalar)

    static member (+) (vector1:Vector, vector2:Vector) = Vector(vector1.X + vector2.X)

let v = Vector(5.0)

let u = v * 10.0
```

Bu kılavuz, bu tür için genel .NET Kılavuzu karşılık gelir. Ancak, bu F # işlevleri ile birlikte ve yöntemleri List.sumBy gibi üye kısıtlamaları ile kullanılmak üzere bu tür verdiğinden F # kodlama Ayrıca önemli olabilir.

#### <a name="consider-using-compiledname-to-provide-a-net-friendly-name-for-other-net-language-consumers"></a>CompiledName sağlamak için kullanmayı bir. Diğer .NET dil müşterileri için NET kolay ad

Bazen bir stilinde bir şey F # Tüketiciler için ad isteyebilirsiniz (statik bir üyenin alt şekilde görünmesi durumda gibi bir modül bağlı işlevi değilmiş gibi), ancak bütünleştirilmiş koda derlenmemiş adı için farklı bir stil vardır. Kullanabileceğiniz `[<CompiledName>]` özniteliği için derleme tüketen olmayan F # kodu farklı bir stil sağlayın.

```fsharp
type Vector(x:float, y:float) =

    member v.X = x
    member v.Y = y

    [<CompiledName("Create")>]
    static member create x y = Vector (x, y)

let v = Vector.create 5.0 3.0
```

Kullanarak `[<CompiledName>]`, .NET adlandırma kuralları olmayan F # tüketiciler derlemenin için kullanabilirsiniz.

#### <a name="use-method-overloading-for-member-functions-if-doing-so-provides-a-simpler-api"></a>Bunun yapılması, yöntemi kullanmak için üye işlevleri, aşırı daha basit bir API sağlar

Yöntemi aşırı yüklemesi güçlü benzer işlevleri gerçekleştirmek için gereken bir API basitleştirmek için ancak farklı seçenekler veya bağımsız bir araçtır.

```fsharp
type Logger() =

    member this.Log(message) =
        ...
    member this.Log(message, retryPolicy) =
        ...
```

F #'ta bağımsız değişken türleri yerine bağımsız değişken sayısı aşırı yüklemeyi daha yaygın bir durumdur.

#### <a name="hide-the-representations-of-record-and-union-types-if-the-design-of-these-types-is-likely-to-evolve"></a>Bu tür tasarım gelişmesi olasılığı varsa kayıt ve birleşim türlerini gösterimlerini Gizle

Nesneleri somut gösterimlerini ortaya kaçının. Örneğin, somut gösterimini <xref:System.DateTime> .NET kitaplığı tasarım dış, ortak API'si tarafından değerleri ortaya değil. Çalışma zamanında, ortak dil çalışma zamanı yürütme kullanılan kaydedilmiş uygulama bilir. Ancak, derlenmiş kod kendisini somut gösterimi bağımlılıkları alması değil.

#### <a name="avoid-the-use-of-implementation-inheritance-for-extensibility"></a>Uygulama devralma genişletilebilirliği için kullanmaktan kaçının

F #'ta uygulama devralma nadiren kullanılır. Ayrıca, devralma hiyerarşileri genellikle karmaşık ve zordur yeni gereksinimleri geldiğinde değiştirmek. Devralma uygulamasında hala F #'de uyumluluk ve burada bir sorun için en iyi çözüm olduğunu, ancak alternatif teknikleri, F # programlarında arabirim uygulaması gibi çok biçimlilik için tasarlarken Aranan nadiren bulunmaktadır.

### <a name="function-and-member-signatures"></a>İşlev ve üye imzaları

#### <a name="use-tuples-for-return-values-when-returning-a-small-number-of-multiple-unrelated-values"></a>Birden çok ilişkisiz değerleri az sayıda döndürülürken diziler için dönüş değerlerini kullanın

Aşağıda, bir dönüş türü bir tanımlama grubu kullanmak iyi bir örnek verilmiştir:

```fsharp
val divrem : BigInteger -> BigInteger -> BigInteger * BigInteger
```

Dönüş türleri birçok bileşen içeren veya bileşenleri tek bir kişisel varlık ilişkili olduğunda, bir tanımlama grubu yerine bir adlandırılmış türü kullanmayı düşünün.

#### <a name="use-asynct-for-async-programming-at-f-api-boundaries"></a>Kullanım `Async<T>` F # API sınırlarında zaman uyumsuz programlama için

Adlı karşılık gelen eşzamanlı bir işlem olup olmadığını `Operation` döndüren bir `T`, zaman uyumsuz işlemi adlı sonra `AsyncOperation` döndürürse `Async<T>` veya `OperationAsync` döndürürse `Task<T>`. Başlangıç/bitiş yöntemleri kullanıma yaygın olarak kullanılan .NET türleri göz önünde bulundurun için kullanarak `Async.FromBeginEnd` F # zaman uyumsuz programlama modeli bu .NET API'lerini sağlamak için bir cephesi olarak genişletme yöntemleri yazma.

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

Özel durumları .NET olağanüstü; diğer bir deyişle, bunlar çalışma zamanında sık oluşmamalıdır. Bunu yaptıklarında, içerdikleri bilgi faydalıdır. Özel durumlar çekirdek .NET birinci sınıf kavramını; yine de uygun istiyor musunuz? Bu nedenle BT özel durumların uygulama uygun aşağıdaki arabirimi bileşeninin tasarımının bir parçası kullanılmalıdır.

#### <a name="follow-the-net-guidelines-for-exceptions"></a>Özel durumlar için .NET yönergeleri izleyin

[.NET kitaplığı tasarım yönergeleri](../../standard/design-guidelines/exceptions.md) bağlamında tüm .NET programlama özel durumları kullanımını mükemmel önerileri verin. Bu yönergeleri bazıları şunlardır:

* Özel durumlar için normal denetim akışı kullanmayın. Bu teknik genellikle OCaml gibi dillerde kullanılsa da hataya yatkın ve .NET verimsiz olabilir. Bunun yerine, döndürme göz önünde bulundurun bir `None` seçeneği ortak veya beklenen oluşum bir hata belirten değer.

* Bir işlevin yanlış kullanıldığında, bileşenler tarafından oluşturulan özel durumları belge.

* Mümkünse, varolan özel durumlar sistemi ad alanları kullanın. Kaçının <xref:System.ApplicationException>ancak.

* Değil throw <xref:System.Exception> zaman onu kaçınmak için kullanıcı kodu. Bu kullanımını önleme içerir `failwith`, `failwithf`, hangi geliştirme altında kod ve komut dosyası kullanımı için kullanışlı işlevleri ancak kodundan daha belirli bir özel durum türü atma lehinde F # kitaplığı kaldırılmalıdır.

* Kullanım `nullArg`, `invalidArg`, ve `invalidOp` throw mekanizması olarak <xref:System.ArgumentNullException>, <xref:System.ArgumentException>, ve <xref:System.InvalidOperationException> uygun olduğunda.

#### <a name="consider-using-option-values-for-return-types-when-failure-is-not-an-exceptional-scenario"></a>Seçenek değerleri hatası olağanüstü bir senaryo değildir dönüş türleri için kullandığınızda göz önünde bulundurun

.NET özel durumlara bunlar "olağanüstü"; olacağını yaklaşımdır diğer bir deyişle, nispeten nadir oluşma. Ancak, bazı işlemler (örneğin, bir tablo arama) sık sık başarısız olabilir. F # seçenek değerleri, bu işlemlerin dönüş türleri temsil etmek için mükemmel bir yoludur. Bu işlemler, işleme, genel "deneyin" adı öneki ile başlatın:

```fsharp
// bad: throws exception if no element meets criteria
member this.FindFirstIndex(pred : 'T -> bool) : int =
    ...

// bad: returns -1 if no element meets criteria
member this.FindFirstIndex(pred : 'T -> bool) : int =
    ...

// good: returns None if no element meets criteria
member this.TryFindFirstIndex(pred : 'T -> bool) : int option =
    ...
```

### <a name="extension-members"></a>Uzantı üyeleri

#### <a name="carefully-apply-f-extension-members-in-f-to-f-components"></a>F # uzantısı üyeleri F # dikkatle geçerli-için-F # bileşenleri

F # uzantı üyeleri genellikle yalnızca modlarından kullanım çoğunluğu bir türü ile ilişkili iç işlemleri kapatması bulunan işlemler için kullanılmalıdır. Bir ortak çeşitli .NET türleri için F # için daha fazla kullanılan deyimsel API'leri sağlamak için kullanılır:

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

#### <a name="use-discriminated-unions-instead-of-class-hierarchies-for-tree-structured-data"></a>Ayrılmış birleşimler sınıf hiyerarşileri yerine ağacında yapılandırılmış veri için kullanın.

Ağaç benzeri yapıları yinelemeli olarak tanımlanmış olan. Devralma ile garip ancak ayrılmış birleşimler ile Zarif budur.

```fsharp
type BST<'T> =
    | Empty
    | Node of 'T * BST<'T> * BST<'T>
```

Ayrılmış birleşimler ağaç benzeri verilerle temsil eden desen eşleştirme içinde exhaustiveness yararlanmasını sağlar.

#### <a name="use-requirequalifiedaccess-on-union-types-whose-case-names-are-not-sufficiently-unique"></a>Kullanım `[<RequireQualifiedAccess>]` örneği adları yeterince benzersiz olmayan birleşim türleri hakkında

Kendinizi aynı adı ayrılmış birleşim durumları gibi farklı işlemler için en iyi adı olduğu bir etki alanında bulabilirsiniz. Kullanabileceğiniz `[<RequireQualifiedAccess>]` gölgeleme nedeniyle kafa karıştırıcı hataları sıralamasını üzerinde bağımlı tetikleme önlemek için büyük/küçük harfe adlarını ayırt etmek için `open` deyimleri

#### <a name="hide-the-representations-of-discriminated-unions-for-binary-compatible-apis-if-the-design-of-these-types-is-likely-to-evolve"></a>Bu tür tasarım gelişmesi olasılığı varsa ikili uyumlu API'leri için ayrılmış birleşimler gösterimlerini Gizle

Birleşimler türleri F # desen eşleştirme formlar için kısa bir programlama modeli kullanır. Daha önce belirtildiği gibi bu tür tasarım gelişmesi olasılığı olan somut veri Beyanları ortaya kaçınmalısınız.

Örneğin, ayrılmış bir birleşim gösterimini bir özel veya dahili bildirimi kullanarak gizlenebilir veya bir imza dosyası kullanarak.

```fsharp
type Union =
    private
    | CaseA of int
    | CaseB of string
```

Ayrılmış birleşimler ölçüsüzce ortaya çıkıyorsa, bu sürüm için sabit kitaplığınızın kullanıcı kodu bozmadan bulabilirsiniz. Bunun yerine, türünüz değerleri desen eşlemeyi izin vermek için bir veya daha fazla Etkin desenler ortaya göz önünde bulundurun.

Etkin desenler F # tüketicileri F # birleşim türlerini doğrudan gösterme kaçınarak eşleşen kalıbı sağlamak için alternatif bir yol sağlar.

### <a name="inline-functions-and-member-constraints"></a>Satır içi işlevler ve üye kısıtlamaları

#### <a name="define-generic-numeric-algorithms-using-inline-functions-with-implied-member-constraints-and-statically-resolved-generic-types"></a>Satır içi işlevler zımni üye kısıtlamaları ve statik olarak çözümlenmiş genel türler ile kullanarak genel sayısal algoritmaları tanımlayın

Aritmetik üye kısıtlamaları ve F # karşılaştırma kısıtlamaları F # programlama için bir standart mevcuttur. Örneğin, aşağıdaki kodu göz önünde bulundurun:

```fsharp
let inline highestCommonFactor a b =
    let rec loop a b =
        if a = LanguagePrimitives.GenericZero<_> then b
        elif a < b then loop a (b - a)
        else loop (a - b) b
    loop a b
```

Bu işlev türü aşağıdaki gibidir:

```fsharp
val inline highestCommonFactor : ^T -> ^T -> ^T
                when ^T : (static member Zero : ^T)
                and ^T : (static member ( - ) : ^T * ^T -> ^T)
                and ^T : equality
                and ^T : comparison
```

Bu bir matematik kitaplığında ortak bir API uygun bir işlevdir.

#### <a name="avoid-using-member-constraints-to-simulate-type-classes-and-duck-typing"></a>Türü sınıfları ve yazarak duck benzetimini yapmak için üye kısıtlamaları kullanmaktan kaçının

"Yazarak duck" benzetimini mümkündür F # üye kısıtlamaları kullanma. Ancak, olun üyeleri, bunun içinde değil genel kullanılmalıdır F #'ta kullanın-için-F # kitaplığı tasarımları. Kitaplık tasarımları bilmediğiniz veya standart örtük kısıtlamalarına göre esnek olmayan ve bir belirli framework desene bağlı olmasını kullanıcı kodu neden eğilimindedir olmasıdır.

Ayrıca, bu şekilde üye kısıtlamaları kullanımına ağırlık çok uzun derleme sürelerini sonuçlanabilir şansı yoktur.

### <a name="operator-definitions"></a>İşleç tanımları

#### <a name="avoid-defining-custom-symbolic-operators"></a>Özel simgesel işleçler tanımlamaktan kaçının

Özel işleçleri bazı durumlarda gereklidir ve uygulama kodu büyük gövdesi içinde çok yararlı notational aygıtlar. Bir kitaplık yeni kullanıcılar adlandırılmış işlevleri genellikle kullanmak daha kolay içindir. Ayrıca, özel simgesel işleçler belgeye zor olabilir ve kullanıcılar IDE ve arama altyapılarındaki varolan sınırlamaları nedeniyle işleçler hakkında yardım aramak daha zor bulabilirsiniz.

Sonuç olarak, işlevselliği adlandırılmış işlevler ve üyeleri olarak yayımlamak ve yalnızca belgeleri ve bunları sahip bilişsel maliyetini notational ağır basıyor varsa bu işlevler operatörleri ayrıca kullanıma sunmak en iyisidir.

### <a name="units-of-measure"></a>Ölçü Birimleri

#### <a name="carefully-use-units-of-measure-for-added-type-safety-in-f-code"></a>F # kodunda eklenen tür güvenliği için ölçü dikkatli kullanın

Ölçü birimleri için ek çok yazarak bilgilerini diğer .NET dilleri tarafından görüntülendiğinde silinir. .NET bileşenleri, araçları ve yansıma birimleri sans türleri görürsünüz unutmayın. Örneğin, C# tüketicileri görürsünüz `float` yerine `float<kg>`.

### <a name="type-abbreviations"></a>Tür Kısaltmaları

#### <a name="carefully-use-type-abbreviations-to-simplify-f-code"></a>Tür kısaltmaları F # kodu basitleştirmek için dikkatli kullanın

.NET bileşenleri, araçları ve yansıma türleri için kısaltılmış adları görmez. Tür kısaltmaları önemli kullanımını daha daha karmaşık gerçekte, Tüketicileri karıştırır olduğu görünür bir etki alanı de yapabilirsiniz.

#### <a name="avoid-type-abbreviations-for-public-types-whose-members-and-properties-should-be-intrinsically-different-to-those-available-on-the-type-being-abbreviated"></a>Tür kısaltmaları, üyeleri ve Özellikler kısaltılmış türüne kullanılabilir kişilere doğası gereği farklı olmalıdır genel türleri için kaçının

Bu durumda, kısaltılmış türü çok tanımlanmakta gerçek tür gösterimini hakkında ortaya çıkarır. Bunun yerine, bir sınıf türü ya da tek durumda ayrılmış birleşim kısaltması kaydırma göz önünde bulundurun (ya da performans gerekli olduğunda, bir yapı türü kısaltması sarmalamak kullanmayı göz önünde bulundurun).

Örneğin, bir çok harita örneğin özel bir F # eşlemesi, durum olarak tanımlamak için tempting şöyledir:

```fsharp
type MultiMap<'Key,'Value> = Map<'Key,'Value list>
```

Ancak, bu tür mantıksal noktalı gösterim işlemlerde bir harita üzerinde işlemler aynı değildir – Örneğin, arama işleci eşleme uygun olur. [anahtar] return anahtar sözlük yerine bir özel durum yükseltme değilse boş liste.

## <a name="guidelines-for-libraries-for-use-from-other-net-languages"></a>Diğer .NET dilleri kullanımdan için kitaplıkları için yönergeler

Diğer .NET dilleri kullanımdan için kitaplıkları tasarlarken, uygun daha önemlidir [.NET kitaplığı tasarım yönergeleri](../../standard/design-guidelines/index.md). Bu belgede, bu kitaplıklar aksine F # temel alınan .NET kitaplıklarına olarak etiketlenir-F # kullanan kitaplıkları karşılıklı kısıtlama olmaksızın oluşturur. Temel alınan .NET kitaplıklarına tasarlama anlamına gelir F # kullanımını en aza indirerek tanıdık ve kullanılan deyimsel API'leri .NET Framework geri kalanı ile tutarlı sağlama-genel API'si belirli yapılardan. Kurallar aşağıdaki bölümlerde açıklanmıştır.

### <a name="namespace-and-type-sesign-for-libraries-for-use-from-other-net-languages"></a>Namespace ve türü sesign (için diğer .NET dilleri kullanımdan kitaplıklar)

#### <a name="apply-the-net-naming-conventions-to-the-public-api-of-your-components"></a>Bileşenlerinizi ortak API için .NET adlandırma kuralları uygula

Özel kısaltılmış adları ve .NET büyük/küçük harf yönergeleri kullanımını dikkat edin.

```fsharp
type pCoord = ...
    member this.theta = ...

type PolarCoordinate = ...
    member this.Theta = ...
```

#### <a name="use-namespaces-types-and-members-as-the-primary-organizational-structure-for-your-components"></a>Ad alanları, türleri ve üyeleri birincil kuruluş yapısı bileşenleriniz için kullanın.

Ortak işlevsellik içeren tüm dosyaları ile başlaması gereken bir `namespace` bildirimi ve yalnızca genel kullanıma yönelik varlıkları ad alanlarında türleri olması gerekir. F # modülleri kullanmayın.

Uygulama kodu, yardımcı program türlerini ve yardımcı işlevlerini tutmak için genel olmayan modüller kullanın.

F # modülleri içinde kullanılamaz. tekrar yüklemesi ve diğer .NET API tasarım kavramları kullanmak için API gelecekteki evrimi sağlarlar statik türler modülleri, tercih edilen olması gerekir.

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

#### <a name="use-f-record-types-in-vanilla-net-apis-if-the-design-of-the-types-wont-evolve"></a>F # kayıt türleri türlerinin tasarım gelişmesi olmaz vanilla .NET API'lerini kullanın

F # kayıt türleri için basit bir .NET sınıfı derleyin. Bunlar, API'lerde bazı basit, kararlı türleri için uygundur. Kullanmayı düşünmelisiniz `[<NoEquality>]` ve `[<NoComparison>]` arabirimleri otomatik olarak oluşturulmasını gizlemek için öznitelikler. Ayrıca vanilla .NET API'lerini değişebilir kayıt alanlarında bu çıkarır ortak alan kullanarak kaçının. Her zaman bir sınıf gelecekteki evrimi için daha esnek bir seçenek API sağlayacak olup olmadığını düşünün.

Örneğin, aşağıdaki F # kodu Genel API'si bir C# tüketiciye sunar:

F #'TA:

```fsharp
[<NoEquality; NoComparison>]
type MyRecord =
    { FirstThing : int
        SecondThing : string }
```

C# ' TA:

```csharp
public sealed class MyRecord
{
    public MyRecord(int firstThing, string secondThing);
    public int FirstThing { get; }
    public string SecondThing { get; }
}
```

#### <a name="hide-the-representation-of-f-union-types-in-vanilla-net-apis"></a>F # birleşim türlerinde vanilla .NET API'lerini gösterimini Gizle

F # birleşim türleri yaygın olarak kullanılmaz bileşen sınırlarında bile F # '-için-F # kodlama. Bileşenleri ve kitaplıkları içinde dahili olarak kullanılan bir mükemmel uygulama aygıt oldukları.

Vanilla .NET API tasarlarken, özel bir bildirim veya bir imza dosyası kullanarak bir birleşim türü gösterimini gizleme göz önünde bulundurun.

```fsharp
type PropLogic =
    private
    | And of PropLogic * PropLogic
    | Not of PropLogic
    | True
```

Ayrıca bir birleşim gösterimi üyeleriyle bir istenen sağlamak için dahili olarak kullanan türlerden büyütmek. NET dönük API.

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

#### <a name="design-gui-and-other-components-using-the-design-patterns-of-the-framework"></a>Tasarım GUI ve framework'ün tasarım desenleri kullanarak diğer bileşenleri

Birçok farklı çerçeveleri WinForms, WPF ve ASP.NET gibi .NET içinde kullanılabilir. Bu çerçeveleri kullanmak için bileşenleri tanımlıyorsanız adlandırma ve tasarım kuralları her kullanılmalıdır. Örneğin, programlama WPF için WPF tasarım desenleri tasarlarken sınıfları için benimser. Kullanıcı arabirimi programlamada modelleri için Tasarım desenleri olayları gibi kullanın ve bildirim tabanlı koleksiyonlar olanlar gibi bulunan <xref:System.Collections.ObjectModel>.

### <a name="object-and-member-design-for-libraries-for-use-from-other-net-languages"></a>Nesne ve üye tasarım (için diğer .NET dilleri kullanımdan kitaplıklar)

#### <a name="use-the-clievent-attribute-to-expose-net-events"></a>CLIEvent özniteliği .NET olaylar oluşturmak için kullanın

Oluşturmak bir `DelegateEvent` belirli bir .NET ile temsilci bir nesne alan türü ve `EventArgs` (yerine bir `Event`, yalnızca kullanan `FSharpHandler` türü varsayılan olarak) diğer .NET dilleri benzer şekilde olayların yayımlandığı böylece.

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

#### <a name="expose-asynchronous-operations-as-methods-which-return-net-tasks"></a>Zaman uyumsuz işlemleri .NET görevleri döndürmesi yöntemleri olarak kullanıma sunma

Görevler .NET etkin zaman uyumsuz hesapları temsil etmek için kullanılır. Görevlerdir genel F # daha az compositional `Async<T>` nesneleri "zaten Yürütülüyor" görevleri temsil eder ve birlikte paralel birleşim gerçekleştirmek ya da iptal sinyalleri ve diğer yayılmasını Gizle yollarla oluşamaz Bağlam parametreleri.

Ancak, bu rağmen görevleri döndürmesi yöntemleri zaman uyumsuz programlama .NET üzerinde standart temsili değildir.

```fsharp
/// A type in a component designed for use from other .NET languages
type MyType() =

    let compute (x: int) : Async<int> = async { ... }

    member this.ComputeAsync(x) = compute x |> Async.StartAsTask
```

Sık olur da açık iptal belirteci kabul etmek isteyebilirsiniz:

```fsharp
/// A type in a component designed for use from other .NET languages
type MyType() =
    let compute(x:int) : Async<int> = async { ... }
    member this.ComputeAsTask(x, cancellationToken) = Async.StartAsTask(compute x, cancellationToken)
```

#### <a name="use-net-delegate-types-instead-of-f-function-types"></a>F # işlev türleri yerine .NET temsilci türleri kullanma

Burada "F # işlev türleri", "OK" türleri ister anlamına gelir `int -> int`.

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

F # işlev türü olarak görünür `class FSharpFunc<T,U>` diğer .NET dilleri için ve dil özellikleri ve araçları için temsilci türleri anlamak daha az uygundur. .NET Framework 3.5 veya daha yüksek hedefleme daha yüksek sıralı yöntemi yazarken `System.Func` ve `System.Action` temsilciler olan bir düşük uyuşmazlık şekilde bu API'leri kullanmak .NET geliştiricilerin yayımlamak için doğru API'leri. (.NET Framework 2.0 hedeflerken sistem tarafından tanımlanan temsilci türleri daha sınırlıdır; önceden tanımlanmış temsilci türleri gibi kullanmayı `System.Converter<T,U>` veya belirli bir temsilci türü tanımlama.)

Çevir tarafında .NET temsilciler F # için doğal olmayan-kitaplıkları karşılıklı (F # sonraki bölüme bakın-kitaplıkları karşılıklı). Sonuç olarak, tüm F # işlev türleri kullanarak uygulama yazmak ve temsilciler üzerinde gerçek F # ince cephesi kullanarak genel API'si oluşturmak için temel alınan .NET kitaplıkları için daha yüksek sıralı yöntemleri geliştirirken, ortak bir uygulama stratejisi olduğu uygulaması.

#### <a name="use-the-trygetvalue-pattern-instead-of-returning-f-option-values-and-prefer-method-overloading-to-taking-f-option-values-as-arguments"></a>F # seçeneği değerler döndüren yerine TryGetValue deseni kullanılacak ve F # seçenek değerleri bağımsız değişken olarak alan için yöntem aşırı yükleme tercih

F # seçenek türü için API kullanımı ortak desenler daha iyi vanilla içinde uygulanan standart .NET kullanarak .NET API'lerini teknikleri tasarlayın. Bir F # seçeneği değer döndürme yerine bool dönüş türü artı out parametresi "TryGetValue" deseni olduğu gibi kullanmayı düşünün. Ve F # seçeneği değerleri parametre olarak ayırdığınız yerine yöntemi aşırı yüklenmesi veya isteğe bağlı bağımsız değişkenler kullanmayı düşünün.

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

.NET diziler gibi somut koleksiyon türleri kullanmaktan kaçının `T[]`, F # türleri `list<T>`, `Map<Key,Value>` ve `Set<T>`, ve .NET somut koleksiyon türleri gibi `Dictionary<Key,Value>`. .NET kitaplığı tasarım yönergeleri ile ilgili çeşitli koleksiyon türleri gibi kullanmak iyi öneriler sahip `IEnumerable<T>`. Diziler bazı kullanımını (`T[]`) performans işe son verme üzerinde bazı durumlarda, kabul edilebilir. Özellikle dikkat edin `seq<T>` yalnızca F # için diğer ad olduğu `IEnumerable<T>`, ve bunun sonucunda seq genellikle vanilla .NET API için uygun bir tür.

F # yerine listeler:

```fsharp
member this.PrintNames(names : string list) =
    ...
```

F # dizileri kullanın:

```fsharp
member this.PrintNames(names : seq<string>) =
    ...
```

#### <a name="use-the-unit-type-as-the-only-input-type-of-a-method-to-define-a-zero-argument-method-or-as-the-only-return-type-to-define-a-void-returning-method"></a>Bir bağımsız değişkeni sıfır yöntemi tanımlamak için bir yöntem yalnızca girdi türü olarak birim türünü kullanın ya da yalnızca dönüş türü void döndüren bir yöntemi tanımlamak için

Diğer kullanımlar birim türü kaçının. Bunlar iyi şunlardır:

```fsharp
✔ member this.NoArguments() = 3

✔ member this.ReturnVoid(x : int) = ()
```

Bu bozuk.

```fsharp
member this.WrongUnit( x:unit, z:int) = ((), ())
```

#### <a name="check-for-null-values-on-vanilla-net-api-boundaries"></a>Temel alınan .NET API sınırları null değerler denetleyin

F # uygulama kodu değişmez tasarım desenleri ve F # türleri için null değişmez değerleri kullanma kısıtlamaları nedeniyle daha az boş değerlere sahip eğilimindedir. Diğer .NET dilleri genellikle bir değer olarak null çok daha sık kullanılır. Bu nedenle, vanilla .NET API gösterme F # kodu API sınırlar null parametreleri denetleyin ve bu değerleri daha derin F # uygulama koduna akan engelleyebilirsiniz. `isNull` İşlevi veya desen üzerinde eşleştirme `null` düzeni kullanılabilir.

```fsharp
let checkNonNull argName (arg: obj) =
    match arg with
    | null -> nullArg argName
    | _ -> ()

let checkNonNull` argName (arg: obj) =
    if isNull arg then nullArg argName
    else ()
```

#### <a name="avoid-using-tuples-as-return-values"></a>Dönüş değerleri olarak diziler kullanmaktan kaçının

Bunun yerine, veri toplama tutarak veya birden çok değer döndürmek için out parametreleri kullanarak adlandırılmış bir tür döndüren tercih eder. Diziler ve yapı diziler .NET içinde mevcut olmasına karşın (C# dil desteğini yapısı başlıkları dahil), bunlar ideal ve beklenen API .NET geliştiricileri için sağlamaz çoğunlukla.

#### <a name="avoid-the-use-of-currying-of-parameters"></a>Parametreleri currying kullanmaktan kaçının

Bunun yerine, .NET çağırma kuralları kullanın ``Method(arg1,arg2,…,argN)``.

```fsharp
member this.TupledArguments(str, num) = String.replicate num str
```

İpucu: kitaplıkları için herhangi bir .NET dil kullanımdan tasarlarken, ardından yoktur gerçekte bazı Deneysel C# ve Visual Basic Kitaplıklarınızı "kullanımında sağ" Bu dillerdeki emin olmak için programlama yapmak için hiçbir yedek. .NET Reflector ve Visual Studio nesne tarayıcısı gibi araçlar, kitaplıklar ve kendi belgelerine geliştiricilerine beklendiği gibi göründüğünden emin olmak için de kullanabilirsiniz.

## <a name="appendix"></a>Ek

### <a name="end-to-end-example-of-designing-f-code-for-use-by-other-net-languages"></a>Uçtan uca örnek F # kodu kullanmak için diğer .NET dilleri tarafından tasarlama

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

Bu sınıf oluşturulursa F # türü aşağıdaki gibidir:

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

Bu F # tür başka bir .NET dilini kullanarak bir programcı görünme bir bakalım. Örneğin, yaklaşık C# "imza" aşağıdaki gibidir:

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

Nasıl F # burada yapıları temsil eden hakkında fark edilecek bazı önemli noktalar vardır. Örneğin:

* Bağımsız değişken adları gibi meta veriler korunur.

* İki bağımsız değişkenler almayan F # yöntemleri iki bağımsız değişkenler almayan C# yöntemleri haline gelir.

* İşlevler ve listeleri karşılık gelen türlerine F # Kitaplığı'nda başvurular haline gelir.

Aşağıdaki kod bu konuları dikkate almanız için bu kodu ayarlama konusunda gösterir.

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

Çıkarılan F # türü kod aşağıdaki gibidir:

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

C# imza şimdi aşağıdaki gibidir:

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

Temel alınan bir .NET kitaplığı bir parçası olarak aşağıdaki gibi bu tür kullanıma hazırlamak düzeltmeleri yaptık:

* Birden fazla ad ayarlandı: `Point1`, `n`, `l`, ve `f` hale geldi `RadialPoint`, `count`, `factor`, ve `transform`sırasıyla.

* Dönüş türü kullanılan `seq<RadialPoint>` yerine `RadialPoint list` listesini kullanarak yapım değiştirerek `[ ... ]` dizisi kullanılarak yapımı için `IEnumerable<RadialPoint>`.

* .NET temsilci türü kullanılan `System.Func` yerine bir F # işlev türü.

Bu, çok daha Hoş görünmesi C# kodunda tüketmeye kolaylaştırır.
