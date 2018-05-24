---
title: 'F # kodlama kuralları'
description: 'Genel kurallar ve deyimleri F # kodu yazarken öğrenin.'
ms.date: 05/14/2018
ms.openlocfilehash: f3d16f735ddc1901aeaa5ebb39e2fa2b70a3d836
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/23/2018
---
# <a name="f-coding-conventions"></a>F # kodlama kuralları

Aşağıdaki kurallar büyük F # ile çalışma deneyiminde şeklide olarak kullanılabilecek kod temeli. [İyi F # kodu beş ilkeleri](index.md#five-principles-of-good-f-code) her öneri temelidir. Bunlar ilişkili [F # bileşen tasarım yönergeleri](component-design-guidelines.md), ancak hiçbir F # kodu, kitaplıklar gibi yalnızca bileşenleri için geçerlidir.

## <a name="organizing-code"></a>Kod düzenleme

F # kodu düzenlemek için iki ana yolu özellikleri: modüller ve ad alanları. Bunlar benzerdir, ancak kıyasla aşağıdaki farklılıklar vardır:

* Ad alanları .NET ad alanları derlenir. Statik sınıflar koda derlenmiş modüller.
* Ad alanları, her zaman üst düzey olur. Modüller, en üst düzey ve diğer modüller içinde iç içe olabilir.
* Ad alanları, birden çok dosya yayılabilir. Modüller olamaz.
* Modüller donatılmış ile `[<RequireQualifiedAccess>]` ve `[<AutoOpen>]`.

Aşağıdaki yönergeler, kodunuzu düzenlemek için bunları kullanın yardımcı olur.

### <a name="prefer-namespaces-at-the-top-level"></a>Ad alanları en üst düzeyinde tercih

Genel olarak tüketilebilir tüm kod için ad alanları en üst düzeyinde modüllerle tercihe bağlı olur. .NET ad alanları derlenen olduğundan, hiçbir sorun C# ' dan tüketilebilir.

```fsharp
// Good!
namespace MyCode

type MyClass() =
    ...
```

Üst düzey bir modül kullanarak görüntülenmeyebilir yalnızca F # çağrıldığında farklı ancak C# tüketicileri için arayanlar nitelemek sağlayarak sürprizle `MyClass` ile `MyCode` modülü.

```fsharp
// Bad!
module MyCode

type MyClass() =
    ...
```

### <a name="carefully-apply-autoopen"></a>Dikkatle Uygula `[<AutoOpen>]`

`[<AutoOpen>]` Yapı arayanlara kullanılabilir kapsamını pollute ve burada bir şey geldiği için yanıt "Sihirli". Bu genellikle iyi bir yöntem değildir. (Bu da biraz tartışmalı gerçeğidir rağmen) F # Core kitaplık kendisini bu kural için bir özel durumdur.

Ancak, düzenlemek için ayrı olarak bu genel API öğesinden istediğiniz ortak bir API için yardımcı işlevleri varsa bir kullanışlı olur.

```fsharp
module MyAPI =
    [<AutoOpen>]
    module private Helpers =
        let helper1 x y z =
            ...


    let myFunction1 x =
        let y = ...
        let z = ...

        helper1 x y z
```

Bu işlem, bir yardımcı her çağırdığında tam olarak nitelemek gerek kalmadan işlevinin genel API'si düzgün bir şekilde ayrı uygulama ayrıntılarından sağlar.

Ayrıca, genişletme yöntemleri ve ad alanı düzeyinde ifade oluşturuculara gösterme düzgünce ile ifade edilebilir `[<AutoOpen>]`.

### <a name="use-requirequalifiedaccess-whenever-names-could-conflict-or-you-feel-it-helps-with-readability"></a>Kullanım `[<RequireQualifiedAccess>]` her adları çakışıyor veya ile okunabilirliği yardımcı olan düşündüğünüz

Ekleme `[<RequireQualifiedAccess>]` öznitelik bir modüle, modül açılmamış ve koşullu erişim modülü öğelere başvurular açık gerektirir gösterir. Örneğin, `Microsoft.FSharp.Collections.List` modülü bu öznitelik içeriyor.

Bu, İşlevler ve değerleri modüldeki diğer modüllerdeki adlarıyla çakışma olasılığı adlara sahip durumunda faydalı olur. Koşullu erişim gerektiren bir kitaplık evolvability ve uzun süreli bakım önemli ölçüde artırabilir.

```fsharp
[<RequireQualifiedAccess>]
module StringTokenization =
    let parse s = ...

...

let s = getAString()
let parsed = StringTokenization.parse s // Must qualify to use 'parse'
```

### <a name="sort-open-statements-topologically"></a>Sıralama `open` deyimleri topologically

F #'ta bildirimleri sırası önemlidir, dahil olmak üzere `open` deyimleri. C#, budur burada etkisini `using` ve `using static` dosyasında bu deyimlerinin sıralamasını bağımsızdır.

F #'ta bir kapsam içine açılan öğeleri zaten mevcut başkalarının gölge. Bu sipariş yani `open` deyimleri kod anlamını alter. Sonuç olarak, tüm sıralama herhangi rastgele `open` deyimleri (örneğin, alfasayısal olarak) genellikle önerilmez, bekleyebilirsiniz farklı bir davranış oluşturmak ekleyin.

Bunun yerine, bunları sıralama öneririz [topologically](https://en.wikipedia.org/wiki/Topological_sorting); diğer bir deyişle, sipariş, `open` hangi sırayla deyimlerinde _katmanları_ sisteminizi tanımlanır. İçindeki farklı topolojik katmanları sıralama alfasayısal yapılması da dikkate.

Örnek olarak, işte topolojik sıralama F # derleyici hizmeti API için ortak dosyası:

```fsharp
namespace Microsoft.FSharp.Compiler.SourceCodeServices

open System
open System.Collections.Generic
open System.Collections.Concurrent
open System.Diagnostics
open System.IO
open System.Reflection
open System.Text

open Microsoft.FSharp.Compiler
open Microsoft.FSharp.Compiler.AbstractIL
open Microsoft.FSharp.Compiler.AbstractIL.Diagnostics
open Microsoft.FSharp.Compiler.AbstractIL.IL
open Microsoft.FSharp.Compiler.AbstractIL.ILBinaryReader
open Microsoft.FSharp.Compiler.AbstractIL.Internal
open Microsoft.FSharp.Compiler.AbstractIL.Internal.Library

open Microsoft.FSharp.Compiler.AccessibilityLogic
open Microsoft.FSharp.Compiler.Ast
open Microsoft.FSharp.Compiler.CompileOps
open Microsoft.FSharp.Compiler.CompileOptions
open Microsoft.FSharp.Compiler.Driver
open Microsoft.FSharp.Compiler.ErrorLogger
open Microsoft.FSharp.Compiler.Infos
open Microsoft.FSharp.Compiler.InfoReader
open Microsoft.FSharp.Compiler.Lexhelp
open Microsoft.FSharp.Compiler.Layout
open Microsoft.FSharp.Compiler.Lib
open Microsoft.FSharp.Compiler.NameResolution
open Microsoft.FSharp.Compiler.PrettyNaming
open Microsoft.FSharp.Compiler.Parser
open Microsoft.FSharp.Compiler.Range
open Microsoft.FSharp.Compiler.Tast
open Microsoft.FSharp.Compiler.Tastops
open Microsoft.FSharp.Compiler.TcGlobals
open Microsoft.FSharp.Compiler.TypeChecker
open Microsoft.FSharp.Compiler.SourceCodeServices.SymbolHelpers

open Internal.Utilities
open Internal.Utilities.Collections
```

Satır sonu topolojik katmanları, sonradan alfasayısal olarak sıralanan her bir katman ile ayıran unutmayın. Bu düzgün bir şekilde kod yanlışlıkla değerleri gölgeleme olmadan düzenler.

## <a name="use-classes-to-contain-values-that-have-side-effects"></a>Yan etkisi olan değerler içermesini sınıflarını kullanma

Bir değer başlatılırken bir veritabanı veya diğer uzak kaynak bağlamına başlatmasını gibi yan etkileri zaman olabilir birçok kez vardır. Bir modüldeki gibi şeyler başlatmak ve sonraki işlevlerini kullanmak için tempting:

```fsharp
// This is bad!
module MyApi =
    let dep1 = File.ReadAllText "/Users/{your name}/connectionstring.txt"
    let dep2 = Environment.GetEnvironmentVariable "DEP_2"

    let private r = Random()
    let dep3() = r.Next() // Problematic if multiple threads use this

    let function1 arg = doStuffWith dep1 dep2 dep3 arg
    let function2 arg = doSutffWith dep1 dep2 dep3 arg
```

Sık kötü bir fikir birkaç nedeni budur:

Uygulama yapılandırması ile codebase içine ilk olarak, gönderilen `dep1` ve `dep2`. Bu, daha büyük olarak kullanılabilecek kod temeli etmek zordur.

İkinci, statik olarak başlatılmış veri bileşeniniz kendisini birden çok iş parçacığı kullanacaksa, iş parçacığı güvenli olmayan değerleri içermemelidir. Bu açıkça tarafından ihlal `dep3`.

Son olarak, modülü başlatma tüm derleme birimi için bir statik oluşturucuya derler. Bu modüldeki olanak sağlayan sınır değeri başlatılmasında herhangi bir hata meydana gelirse, olarak bildirimleri bir `TypeInitializationException` , ardından önbelleğe alınma uygulamanın tüm yaşam süresi. Bu tanılama zor olabilir. Genellikle hakkında neden deneyebilirsiniz bir iç özel duruma yoktur, ancak ardından yoksa, hiçbir kök nedeni nedir söyleyen yoktur.

Bunun yerine, bağımlılıkları tutmak için yalnızca basit bir sınıf kullanın:

```fsharp
type MyParametricApi(dep1, dep2, dep3) =
    member __.Function1 arg1 = doStuffWith dep1 dep2 dep3 arg1
    member __.Function2 arg2 = doStuffWith dep1 dep2 dep3 arg2
```

Bu aşağıdakileri sağlar:

1. API dışında herhangi bir bağımlı durumu Ftp'den.
2. Yapılandırma şimdi dışında API yapılabilir.
3. Bağımlı değerler için başlatma hataları olarak belli etmesi olasıdır olmayan bir `TypeInitializationException`.
4. API artık test etmek daha kolay olur.

## <a name="error-management"></a>Hata Yönetimi

Büyük sistemlerinde hata Yönetimi karmaşık ve nuanced çaba olduğunu ve hiçbir Gümüş sistemlerinizi sağlamak madde işaretleri hataya dayanıklı ve iyi davranır. Aşağıdaki yönergeler bu zor alanı gezinme şu konularda rehberlik sunar.

### <a name="represent-error-cases-and-illegal-state-in-types-intrinsic-to-your-domain"></a>Hata durumları ve türleri etki alanınıza iç geçersiz durumda temsil eder

İle [ayrılmış birleşimler](../language-reference/discriminated-unions.md), F # olma imkanı sunar, hatalı program durumu türü sisteminizdeki temsil eder. Örneğin:

```fsharp
type MoneyWithdrawalResult =
    | Success of amount:decimal
    | InsufficientFunds of balance:decimal
    | CardExpired of DateTime
    | UndisclosedFailure
```

Bu durumda, para banka hesabından geri alınmasının başarısız üç bilinen yolu vardır. Her hata durumu yazıyla gösterilir ve bu nedenle ile güvenli bir şekilde program boyunca ele alınabilir.

```fsharp
let handleWithdrawal amount =
    let w = withdrawMoney amount
    match w with
    | Success am -> printfn "Successfully withdrew %f" am
    | InsufficientFunds balance -> printfn "Failed: balance is %f" balance
    | CardExpired expiredDate -> printfn "Failed: card expired on %O" expiredDate
    | UndisclosedFailure -> printfn "Failed: unknown"
```

Bu şeyin genel olarak, farklı yolları model yoksa yapabilirsiniz **başarısız** etki alanınızda sonra hata işleme kodu artık şey, gerekir Dağıt ile normal program akışı ek olarak kabul edilir. Normal program akışı yalnızca bir parçası olan ve dikkate alınmaz **olağanüstü**. Bu iki birincil avantajları vardır:

1. Etki alanınızı zaman içinde değiştikçe korumak kolaydır.
2. Hata durumlarında birim testi için daha kolay.

### <a name="use-exceptions-when-errors-cannot-be-represented-with-types"></a>Hata türleri ile temsil edilemez olduğunda özel durumlar kullanın

Tüm hataları sorun etki alanında temsil edilebilir. Bu hataları türleridir *olağanüstü* yapısı, bu nedenle yükseltmek ve özel durumlarını F #'ta yakalama olanağı.

İlk olarak, okumanız önerilir [özel tasarım yönergeleri](../../standard/design-guidelines/exceptions.md). Bunlar ayrıca F # için geçerlidir.

F #'de kullanılabilir özel durumlarını oluşturma amacıyla ana yapıları aşağıdaki tercih sırasına göre değerlendirilmesi:

| İşlev | Sözdizimi | Amaç |
|----------|--------|---------|
| `nullArg` | `nullArg "argumentName"` | Başlatır bir `System.ArgumentNullException` belirtilen bağımsız değişken ada sahip. |
| `invalidArg` | `invalidArg "argumentName" "message"` | Başlatır bir `System.ArgumentException` belirtilen bağımsız değişken adı ve ileti. |
| `invalidOp` | `invalidOp "message"` | Başlatır bir `System.InvalidOperationException` belirtilen iletiyle. |
|`raise`| `raise (ExceptionType("message"))` | Özel durumları atma için genel amaçlı mekanizması. |
| `failwith` | `failwith "message"` | Başlatır bir `System.Exception` belirtilen iletiyle. |
| `failwithf` | `failwithf "format string" argForFormatString` | Başlatır bir `System.Exception` biçim dizesi ve girdilerinden tarafından belirlenen bir iletiyle. |

Kullanım `nullArg`, `invalidArg` ve `invalidOp` throw mekanizması olarak `ArgumentNullException`, `ArgumentException` ve `InvalidOperationException` uygun olduğunda.

`failwith` Ve `failwithf` işlevleri, genelde temel yükseltmek için kaçınılmalıdır `Exception` türü, belirli bir durum değil. Göre [özel tasarım yönergeleri](../../standard/design-guidelines/exceptions.md), yapabilecekleriniz olduğunda daha belirli özel durumların yükseltmek istediğiniz.

### <a name="using-exception-handling-syntax"></a>Özel durum işleme sözdizimini kullanarak

F # aracılığıyla özel durum desenleri destekler `try...with` sözdizimi:

```fsharp
try
    tryGetFileContents()
with
| :? System.IO.FileNotFoundException as e -> // Do something with it here
| :? System.Security.SecurityException as e -> // Do something with it here
```

Desen eşleştirme ile bir özel durum karşısında gerçekleştirmek için işlevselliği karşılaştırma kodu temiz saklamak isterseniz biraz zor olabilir. Bu durumu çözmek için bu tür bir yolu kullanmaktır [Etkin desenler](../language-reference/active-patterns.md) olarak bir özel hata durumuyla çevreleyen Grup işlevine anlamına gelir. Örneğin, bir durum oluşturduğunda değerli bilgiler özel durum meta verilerde kapsayan bir API tüketen. Yakalanan özel durum etkin desen içinde gövdesinde yararlı bir değer açmak ve döndüren değer bazı durumlarda yararlı olabilir.

### <a name="do-not-use-monadic-error-handling-to-replace-exceptions"></a>Birli hata özel durum değiştirmek için işleme kullanmayın

Özel durumlar biraz taboo işlevsel programlamada olarak görülür. Aslında, not sessiz işlevsel dikkate alınması gereken güvenli olması için özel durumlar olmak üzere, ihlal ediyor. Ancak, bu kodu çalıştırdığı gerekir ve bu çalışma zamanı hataları oluşabilir harcamanız yok sayar. Genel olarak, çoğu şeyler saf ne kötü beklenmeyen durumları en aza indirmek için toplam varsayımına kod yazın.

Aşağıdaki çekirdek gücü/yönlerini özel durumlar, ilgi belirleme ve bir bütün olarak .NET çalışma zamanı ve diller arası ekosistemi site göre dikkate almak önemlidir:

1. Bir sorun ayıklarken yararlı olan ayrıntılı tanılama bilgileri içerir.
2. Çalışma zamanı ve diğer .NET dilleri tarafından anlaşılır olmaları.
3. Yolu dışında gider kod ile karşılaştırıldığında önemli Demirbaş azaltabilir *kaçının* bir geçici olarak kendi semantiği bazı alt uygulayarak özel durumları.

Üçüncü bu nokta önemlidir. Ölçeklendirebilmek kolay değildir karmaşık işlemleri için özel durumlar kullanmak başarısız olan böyle yapıları postalarla neden olabilir:

```fsharp
Result<Result<MyType, string>, string list>
```

Hangi kolayca kırılacak kod "stringly yazılan" hatalarda eşleşen kalıbı gibi neden olabilir:

```fsharp
let result = doStuff()
match result with
| Ok r -> ...
| Error e ->
    if e.Contains "Error string 1" then ...
    elif e.Contains "Error string 2" then ...
    else ... // Who knows?
```

Ayrıca, tüm özel durum "daha Hoş görünmesi" türü döndüren "Basit" işlevi için isteğini swallow tempting olabilir:

```fsharp
// This is bad!
let tryReadAllText (path : string) =
    try System.IO.File.ReadAllText path |> Some
    with _ -> None
```

Ne yazık ki, `tryReadAllText` bir dosya sisteminde oluşabilir şeyler sayıda dayalı çok sayıda istisnalar atabilirsiniz ve bu kodu hemen gerçekte ortamınızda yanlış neler hakkında bilgi atar. Daha sonra bu kodu bir sonuç türü ile değiştirirseniz, "stringly yazılan" hata iletisini geri ayrıştırmak için olduğunuz:

```fsharp
// This is bad!
let tryReadAllText (path : string) =
    try System.IO.File.ReadAllText path |> Ok
    with e -> Error e.Message

let r = tryReadAllText "path-to-file"
match r with
| Ok text -> ...
| Error e ->
    if e.Contains "uh oh, here we go again..." then ...
    else ...
```

Ve özel durum nesnesi yerleştirme içinde `Error` Oluşturucusu yalnızca zorlar, özel durum türü çağrı sitedeki yerine işlevi düzgün uğraşmanız. Etkili bir şekilde bunu bir API çağıran çalışılabilecek notoriously unfun checked özel durumları oluşturur.

Yukarıdaki örneklerde için iyi bir seçenek yakalamaktır *belirli* özel durumlar ve return başka bir özel durum bağlamında anlamlı bir değer. Değiştirirseniz `tryReadAllText` aşağıdaki gibi işlev `None` daha anlamlı vardır:

```fsharp
let tryReadAllTextIfPresent (path : string) =
    try System.IO.File.ReadAllText path |> Some
    with :? FileNotFoundException -> None
```

Bir dosya bulunamadı ve geri dönmek için bu anlamı atamak catch tümünü olarak çalışmasını yerine bu işlev artık düzgün çalışması işler. Bu dönüş değeri için hata durumda, bağlamsal bilgileri atılıyor veya bu noktada kodda ilgili olmayabilir bir servis talebi uğraşmanız arayanlar zorlama eşleyebilirsiniz.

Gibi türleri `Result<'Success, 'Error>` burada iç içe değil ve F # isteğe bağlı türleri bir şey olabilir ya da dönüş zaman temsil etmek için mükemmel temel işlemleri için uygun olan *bir şey* veya *hiçbir şey*. Bunlar özel durumlar için yenileme değildir ancak ve bir özel durum değiştirmek için kullanılmamalıdır. Bunun yerine, bunlar dikkatli adresi belirli yönlerini özel durumu ve hata yönetimi ilkesi için hedeflenen yollarla uygulanmalıdır.

## <a name="partial-application-and-point-free-programming"></a>Kısmi uygulama ve programlama noktası boş

F # kısmi uygulama ve bu nedenle, program için çeşitli şekillerde noktası Serbest stilde destekler. Bu kodu yeniden kullanma içinde bir modül veya herhangi bir şeyin uygulama için yararlı olabilir, ancak genellikle bir genel olarak kullanıma sunmak değil. Genel olarak, noktası serbest programlama virtue içinde ve kendisinin değil ve ciddi bir bilişsel engel stilde immersed değil kişiler için ekleyebilirsiniz.

### <a name="do-not-use-partial-application-and-currying-in-public-apis"></a>Kısmi uygulama ve ortak API'leri currying kullanmayın

Küçük özel durumla ortak API'ler kısmi uygulamada kullanımını Tüketiciler için Kafa karışıklığına neden olabilir. Genellikle, `let`-F # kodu ilişkili değerler **değerleri**değil **işlev değerleri**. Ve işlev değerleri birlikte karıştırma sonuçlanabilir oldukça biraz bilişsel yükünü karşılığında kod satırlarını az sayıda kaydetme işleminde gibi özellikle işleçleri ile birleştirildiğinde `>>` işlevleri oluşturmak için.

### <a name="consider-the-tooling-implications-for-point-free-programming"></a>Programlama noktası serbest araç etkilerini göz önünde bulundurun

Curried işlevleri kendi bağımsız değişkenleri etiket yok. Bu etkileri tooling sahiptir. Aşağıdaki iki işlevi göz önünde bulundurun:

```fsharp
let func name age =
    printfn "My name is %s and I am %d years old!" name age

let funcWithApplication =
    printfn "My name is %s and I am %d years old!"
```

Her ikisi de geçerli işlevleri olan ancak `funcWithApplication` curried bir işlevdir. Bir düzenleyicide türlerini üzerine geldiğinizde, bu bakın:

```fsharp
val func : name:string -> age:int -> unit

val funcWithApplication : (string -> int -> unit)
```

Çağrı sitede Visual Studio Araçları ipuçlarında, ne anlamlı bilgileri veremezsiniz `string` ve `int` giriş türleri gerçekte temsil eder.

Kod noktası serbest gibi karşılaşırsanız `funcWithApplication` olan herkese açık şekilde kaynaklarda, araç çekme yukarı bağımsız değişkenler için anlamlı adlar devam için bir tam η genişletme yapmanız önerilir.

Ayrıca, noktası serbest kodda hata ayıklama, imkansız olmasa zor olabilir. Hata ayıklama araçlarını kullanan adlarına bağlı değerleri (örneğin, `let` bağlamaları) böylece Ara değerleri yarıda yürütme aracılığıyla inceleyebilirsiniz. Kodunuzu incelemek için hiçbir değer olduğunda, hata ayıklamak için hiçbir şey yoktur. Gelecekte, hata ayıklama araçları gelişmesi daha önce yürütülen yollarına bağlı bu değerleri sentezlemek için ancak, sonuçlar üzerinde hedge için iyi bir fikir değil *olası* işlevleri hata ayıklama.

### <a name="consider-partial-application-as-a-technique-to-reduce-internal-boilerplate"></a>Bir teknik olarak kısmi uygulama iç Demirbaş azaltmak için göz önünde bulundurun

Önceki aksine, kısmi uygulama ortak bir uygulama veya bir API'nin daha derin iç içinde azaltmak için müthiş bir araçtır noktasıdır. Birim testi Demirbaş genellikle uğraşmanız bir sorun olduğu daha karmaşık API uygulaması için yararlı olabilir. Örneğin, bu tür bir Framework'te dış bağımlılık bırakmadan nasıl gerçekleştirebileceğiniz aşağıdaki kodu gösterir hangi en mocking çerçeveleri, verin ve API bespoke ilgili bilgi edinmek sahip.

Örneğin, aşağıdaki çözüm topografi göz önünde bulundurun:

```
MySolution.sln
|_/ImplementationLogic.fsproj
|_/ImplementationLogic.Tests.fsproj
|_/API.fsproj
```

`ImplementationLogic.fsproj` kod gibi doğurabilir:

```fsharp
module Transactions =
    let doTransaction txnContext txnType balance =
        ...

type Transactor(ctx, currentBalance) =
    member __.ExecuteTransaction(txnType) =
        Transactions.doTransaction ctx txtType currentBalance
        ...
```

Birim testi `Transactions.doTransaction` içinde `ImplementationLogic.Tests.fspoj` kolaydır:

```fsharp
namespace TransactionsTestingUtil

open Transactions

module TransactionsTestable =
    let getTestableTransactionRoutine mockContext = Transactions.doTransaction mockContext
```

Kısmen uygulama `doTransaction` mocking bağlamına sahip nesne, işlevi her zaman bir mocked bağlamı oluşturmak zorunda kalmadan tümünü birim testleri çağırın olanak tanır:

```fsharp
namespace TransactionTests

open Xunit
open TransactionTypes
open TransactionsTestingUtil
open TransactionsTestingUtil.TransactionsTestable

let testableContext =
    { new ITransactionContext with
        member __.TheFirstMember() = ...
        member __.TheSecondMember() = ... }

let transactionRoutine = getTestableTransactionRoutine testableContext

[<Fact>]
let ``Test withdrawal transaction with 0.0 for balance``() =
    let expected = ...
    let actual = transactionRoutine TransactionType.Withdraw 0.0
    Assert.Equal(expected, actual)
```

Bu teknik tüm temelinizde Evrensel uygulanmamalıdır ancak karmaşık iç Ayrıntılar ve birim testi bu dahili bileşenleri için Demirbaş azaltmak için iyi bir yoludur.

## <a name="access-control"></a>Erişim denetimi

F # için birden fazla seçeneği vardır [erişim denetimi](../language-reference/access-control.md), .NET çalışma zamanı'nda kullanılabilir öğesinden devralınan. Bunlar yalnızca türleri için kullanılabilir değil - bunları işlevleri için de kullanabilirsiniz.

* Tercih olmayan`public` türleri ve genel olarak tüketilebilir olması gereken kadar üyeleri. Bu ayrıca hangi tüketicileri birkaç en aza indirir
* Tüm yardımcı işlevleri tutmak çalışmalarımızı `private`.
* Kullanımını göz önünde bulundurun `[<AutoOpen>]` özel bir modül, çok sayıda hale gelirse yardımcı işlevleri üzerinde.

## <a name="type-inference-and-generics"></a>Tür çıkarımı ve genel türler

Tür çıkarımı Demirbaş çok yazarak kaydedebilirsiniz. Ve F # derleyicide otomatik Genelleştirme yapmanız neredeyse hiçbir ek çaba ile daha genel kod yazmanıza yardımcı olabilir. Ancak, bu özellikler Evrensel iyi değildir.

* Ortak API'ler açık türleriyle bağımsız değişken adları etiketleme düşünün ve bu tür çıkarımı güvenmeyin.

    Bunun nedeni olan **,** derleyici API'nizi şeklini denetiminde olması gerekir. Derleyici türleri için çıkarımını yapma en iyi iş yapabilirse kullanır. iç türleri değişip değişmediğini API değişikliğinizin şeklini olması mümkündür. Bu, istediğiniz olabilir, ancak hemen kesinlikle önemli bir API değişiklik aşağı akış Tüketiciler, uğraşmanız sahip olacağı neden. Bunun yerine, ortak API'nizi şeklini açıkça denetlerseniz, bu önemli değişiklikler denetleyebilirsiniz. DDD açısından, bu, bir koruma Bozulması katmanı olarak değerlendirilebilir.

* Anlamlı bir ad da genel bağımsız vermeye çalışın.

    Anlamlı bir ad, belirli bir etki alanına özgü değildir gerçekten genel kod yazmakta olduğunuz sürece, bunlar çalıştığınız etki alanı anlama diğer programcıları yardımcı olabilir. Örneğin, adlandırılmış bir tür parametresi `'Document` bir belgeyle etkileşim bağlamında veritabanı daha anlaşılır genel belge türü işlev veya birlikte çalıştığınız üyesi tarafından kabul edilebilir kolaylaştırır.

* Genel tür parametreleri ile PascalCase adlandırma göz önünde bulundurun.

    Bu, .NET şeyler PascalCase yerine snake_case veya camelCase kullanmanız önerilir Bunu yapmak için genel yoludur.

Son olarak, otomatik Genelleştirme her zaman katkıda bulunuyor F # veya büyük codebase için yeni olan kişiler için değil. Genel bileşenleri kullanarak bilişsel yükünü yoktur. Ayrıca, otomatik olarak genelleştirilmiş İşlevler, farklı giriş türleri (let şekilde kullanılacak yönelikse tek başına) ile birlikte kullanılan değil, sonra bunları zamandaki o noktada genel olması için gerçek fayda yoktur. Her zaman yazmakta olduğunuz kod gerçekten genel olmaktan faydalanırsınız varsa göz önünde bulundurun.

## <a name="performance"></a>Performans

F # belirli sınıfları (özellikle bu içeren eşzamanlılık ve paralellik) hataların önlemek izin veren varsayılan olarak, sabit değerlerdir. Ancak, bazı durumlarda, yürütme zamanı bellek ayırmaları ve en iyi (veya hatta makul) verimliliği elde etmek için bir aralık iş en iyi durumu yerinde mutation kullanarak uygulanabilir. Bu katılımı temel F # ile ile mümkündür `mutable` anahtar sözcüğü.

Ancak, kullanımı `mutable` F # işlevsel olmak üzere şekliyle açabilir. Bunun için olmak üzere gelen beklentilerini ayarlarsanız, uygundur [başvuru saydamlık](https://en.wikipedia.org/wiki/Referential_transparency). Başvuru saydamlık - olmak üzere değil - end F # işlevleri yazılırken hedeftir. Bu kritik kod performansı için mutation tabanlı bir uygulama üzerinden işlevsel arabirimi yazmanızı sağlar.

### <a name="wrap-mutable-code-in-immutable-interfaces"></a>Değişmez arabirimlerde değişebilir kod sarmalama

Bir hedef olarak başvuru saydamlığı olan performans açısından kritik işlevlerin değişebilir underbelly kullanıma sunmuyor kod yazmak için önemlidir. Örneğin, aşağıdaki uygulayan kod `Array.contains` işlevi F # core Kitaplığı'nda:

```fsharp
[<CompiledName("Contains")>]
let inline contains value (array:'T[]) =
    checkNonNull "array" array
    let mutable state = false
    let mutable i = 0
    while not state && i < array.Length do
        state <- value = array.[i]
        i <- i + 1
    state
```

Birden çok kez bu işlev çağırma temel alınan dizi değişmez ve onu kullanan herhangi bir değişebilir durumu bakımını bulundurmanızı gerektirmez. Neredeyse her içindeki kod satırı mutation kullanıyor olsa bile referentially saydam olacak.

### <a name="consider-encapsulating-mutable-data-in-classes"></a>Değişebilir veri sınıflarında Kapsüllenen göz önünde bulundurun

Önceki örnekte tek bir işlev değişebilir veri kullanarak işlemleri kapsüllemek için kullanılır. Bu her zaman daha karmaşık veri kümeleri için yeterli değil. Aşağıdaki adımlardan işlevlerin göz önünde bulundurun:

```fsharp
open System.Collections.Generic

let addToClosureTable (key, value) (t: Dictionary<_,_>) =
    if not (t.ContainsKey(key)) then
        t.Add(key, value)
    else
        t.[key] <- value

let closureTableCount (t: Dictionary<_,_>) = t.Count

let closureTableContains (key, value) (t: Dictionary<_, HashSet<_>>) =
    match t.TryGetValue(key) with
    | (true, v) -> v.Equals(value)
    | (false, _) -> false
```

Bu kod, kullanıcı olmakla birlikte arayanlar bakımından sorumlu mutation tabanlı veri yapısı kullanıma sunar. Bu sınıf değiştirebilirsiniz hiçbir temel üye ile içinde kaydırılan:

```fsharp
open System.Collections.Generic

/// The results of computing the LALR(1) closure of an LR(0) kernel
type Closure1Table() =
    let t = Dictionary<Item0, HashSet<TerminalIndex>>()

    member __.Add(key, value) =
        if not (t.ContainsKey(key)) then
            t.Add(key, value)
        else
            t.[key] <- value

    member __.Count = t.Count

    member __.Contains(key, value) =
        match t.TryGetValue(key) with
        | (true, v) -> v.Equals(value)
        | (false, _) -> false
```

`Closure1Table` veri yapılarını korumak için arayanlar kapanmaya böylelikle alttaki mutation tabanlı veri yapısı yalıtır. Sınıfları, veri ve ayrıntıları arayanlara sokmadan mutation tabanlı yordamları kapsülleyen güçlü bir yöntemdir.

### <a name="prefer-let-mutable-to-reference-cells"></a>Tercih `let mutable` başvuru hücreleri

Başvuru hücreleri başvuru değeri yerine bir değeri temsil etmek için bir yoldur. Performans açısından kritik kod için kullanılan olsa da, genellikle önerilmez. Aşağıdaki örnek göz önünde bulundurun:

```fsharp
let kernels =
    let acc = ref Set.empty

    processWorkList startKernels (fun kernel ->
        if not ((!acc).Contains(kernel)) then
            acc := (!acc).Add(kernel)
        ...)

    !acc |> Seq.toList
```

Bir başvuru hücresi şimdi kullanımını "dereference ve arka plandaki verilere yeniden başvurmak zorunda olan tüm izleyen kod pollutes". Bunun yerine, göz önünde bulundurun `let mutable`:

```fsharp
let kernels =
    let mutable acc = Set.empty

    processWorkList startKernels (fun kernel ->
        if not (acc.Contains(kernel)) then
            acc <- acc.Add(kernel)
        ...)

    acc |> Seq.toList
```

Diğer tüm kod lambda ifadesi ortasında mutation yanı sıra tek noktası dokunur `acc` normal kullanım için farklı bir şekilde bunu yapabilirsiniz `let`-bağlı değişmez değer. Bu, zaman içinde değişip daha kolay hale getirir.

## <a name="object-programming"></a>Nesne programlama

F # nesneleri ve nesne yönelimli (OO) kavramları için tam destek vardır. Birçok OO kavramları güçlü ve yararlı olsa da, bunları tüm kullanmak idealdir. Aşağıdaki listeler, yüksek bir düzeyde OO özelliklerinin kategorileri hakkında yönergeler sunar.

**Çoğu durumda bu özellikleri kullanarak göz önünde bulundurun:**

* Noktalı gösterim (`x.Length`)
* Örnek üyeleri
* Örtük Oluşturucu
* Statik üyeler
* Dizin Oluşturucu gösterimi (`arr.[x]`)
* Adlandırılmış ve isteğe bağlı bağımsız değişkenler
* Arabirimleri ve arabirim uygulamaları

**Bu özellikler için ilk ulaşmak yoktur, ancak bir sorunu çözmek uygun olduklarında dikkatli bunları geçerlidir:**

* Yöntemi aşırı yüklemesi
* Değişebilir veri kapsüllenmiş
* Türlerinde işleçleri
* Otomatik özellikleri
* Uygulama `IDisposable` ve `IEnumerable`
* Tür uzantıları
* Olaylar
* Yapılar
* Temsilciler
* Numaralandırmalar

**Genellikle bunları kullanmadığınız sürece bu özellikler kaçının:**

* Devralma tabanlı tür hiyerarşileri ve uygulama devralma
* Null değerler ve `Unchecked.defaultof<_>`

### <a name="prefer-composition-over-inheritance"></a>Birleşim devralma tercih

[Birleşim devralma üzerinden](https://en.wikipedia.org/wiki/Composition_over_inheritance) iyi F # kodu bağlı kalmayı artırmanın uzun süredir bilinen bir deyim değil. Temel olmayan bir taban sınıf kullanıma ve gerekir işlevselliğini kazanması için bu taban sınıftan devralın arayanlar zorlamak olduğunu ilkesidir.

### <a name="use-object-expressions-to-implement-interfaces-if-you-dont-need-a-class"></a>Bir sınıf gerekmiyorsa arabirimleri uygulamak için Nesne ifadeleri kullanma

[Nesne ifadeleri](../language-reference/object-expressions.md) anında, arabirimleri uygulamak izin uygulanan arabirimi bir değere bir sınıf içinde bunu gerek kalmadan bağlama. Bu, kullanışlıdır özellikle, _yalnızca_ arabirimini uygulayan ve tam bir sınıf için gerekli olması gerekir.

Örneğin, çalıştırmak, kod işte [Ionide](http://ionide.io/) sahip olmayan bir simge eklediyseniz kod düzeltme eylemi sağlamak için bir `open` bildirimi:

```fsharp
    let private createProvider () =
        { new CodeActionProvider with
            member this.provideCodeActions(doc, range, context, ct) =
                let diagnostics = context.diagnostics
                let diagnostic = diagnostics |> Seq.tryFind (fun d -> d.message.Contains "Unused open statement")
                let res =
                    match diagnostic with
                    | None -> [||]
                    | Some d ->
                        let line = doc.lineAt d.range.start.line
                        let cmd = createEmpty<Command>
                        cmd.title <- "Remove unused open"
                        cmd.command <- "fsharp.unusedOpenFix"
                        cmd.arguments <- Some ([| doc |> unbox; line.range |> unbox; |] |> ResizeArray)
                        [|cmd |]
                res
                |> ResizeArray
                |> U2.Case1
        }
```

Visual Studio kod API ile kullanılırken bir sınıf için gerekli olduğundan nesne ifadeleri bu ideal bir araçlardır. Ayrıca birim testi test yordamları arabirimiyle çıkışı geçici bir şekilde saplama istediğinizde faydalıdır.

## <a name="type-abbreviations"></a>Tür Kısaltmaları

[Tür kısaltmaları](../language-reference/type-abbreviations.md) başka bir tür, bir işlev imzası veya daha karmaşık bir tür gibi bir etiket atamak için kullanışlı bir yoludur. Örneğin, aşağıdaki diğer ad ile hesaplama tanımlamak neler gerekir için bir etiket atar [CNTK](https://www.microsoft.com/cognitive-toolkit/), learning kitaplığı derin:

```fsharp
open CNTK

// DeviceDescriptor, Variable, and Function all come from CNTK
type Computation = DeviceDescriptor -> Variable -> Function
```

`Computation` Adı yumuşatma olmasından imza eşleşen herhangi bir işlev belirtmek için uygun bir yoldur. Tür kısaltmaları şöyle kullanarak uygun olan ve daha kısa kodunu sağlar.

### <a name="avoid-using-type-abbreviations-to-represent-your-domain"></a>Tür kısaltmaları etki alanınızın temsil etmek için kullanmaktan kaçının

Tür kısaltmaları işlevi imzalar için bir ad vermek için kullanışlı olsa da, bunlar diğer türleri kısaltma kafa karıştırıcı olabilir. Bu kısaltma göz önünde bulundurun:

```fsharp
// Does not actually abstract integers.
type BufferSize = int
```

Bu, birden çok yolla kafa karıştırıcı olabilir:

* `BufferSize` bir Özet değildir; tamsayı yalnızca başka bir addır.
* Varsa `BufferSize` sunulan genel API'si, kolayca daha fazlasını anlamına gelir yorumlanabilir `int`. Genellikle, etki alanı türleri için onlara birden çok özniteliklere sahip ve gibi basit türler değildir `int`. Bu kısaltma Bu varsayım ihlal ediyor.
* Büyük küçük harf kullanımını `BufferSize` (PascalCase) gelir. Bu tür daha fazla verileri tutar.
* Bu diğer adı, adlandırılmış bir bağımsız değişken bir işleve sağlama ile karşılaştırıldığında daha yüksek netlik sağlamaz.
* Kısaltma derlenmiş IL bildirilmez; yalnızca bir tamsayı olan ve bu diğer adı bir derleme zamanı yapıdır.

```fsharp
module Networking =
    ...
    let send data (bufferSize: int) =
        ...
```

Özet olarak, durumu tür kısaltmaları sahip olduklarından emin olan **değil** kısaltma türleri üzerinden soyutlamalar. Önceki örnekte, `BufferSize` tıpkı bir `int` ek veri yok ya da tüm avantajları ne yanı sıra türü sisteminden ile kapsar altında `int` zaten sahip.
