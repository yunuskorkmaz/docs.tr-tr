---
title: F# kodlama kuralları
description: 'F # kodu yazarken genel kılavuzları ve deyimleri öğrenin.'
ms.date: 01/15/2020
ms.openlocfilehash: 47e9183ce22689a050878cf10d7a9bcf3b929ec6
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/28/2020
ms.locfileid: "84143542"
---
# <a name="f-coding-conventions"></a>F# kodlama kuralları

Aşağıdaki kurallar, büyük F # codetabanlarla çalışma deneyiminden alınmıştır. Her bir önerinin temelini, [Iyi F # kodu olan beş ilkeden](index.md#five-principles-of-good-f-code) oluşur. Bunlar [f # bileşen tasarım yönergeleriyle](component-design-guidelines.md)ilgilidir, ancak yalnızca kitaplıklar gibi bileşenler değil herhangi bir f # kodu için geçerlidir.

## <a name="organizing-code"></a>Kodu düzenleme

F # kodu düzenlemenin iki birincil yolunu sunar: modüller ve ad alanları. Bunlar benzerdir, ancak aşağıdaki farklılıklara sahiptir:

* Ad alanları .NET ad alanları olarak derlenir. Modüller statik sınıflar olarak derlenir.
* Ad alanları her zaman en üst düzeydir. Modüller en üst düzey ve diğer modüller içinde iç içe olabilir.
* Ad alanları birden çok dosyaya yayılabilir. Modüller.
* Modüller ve ile donatılmış olabilir `[<RequireQualifiedAccess>]` `[<AutoOpen>]` .

Aşağıdaki yönergeler kodunuzu düzenlemek için bunları kullanmanıza yardımcı olur.

### <a name="prefer-namespaces-at-the-top-level"></a>En üst düzeyde ad alanlarını tercih et

Genel kullanım düzeylerine sahip herhangi bir kod için, ad alanları en üst düzeydeki modüllerle tercihe göre yapılır. .NET ad alanları olarak derlendiğinden, hiçbir sorun olmadan C# ' den tüketilebilir.

```fsharp
// Good!
namespace MyCode

type MyClass() =
    ...
```

En üst düzey modülün kullanılması yalnızca F # ' dan çağrıldığında farklı görünmeyebilir, ancak C# tüketicileri için, bu, modüle uygun hale getirmek zorunda kalmadan çağıranlar olabilir `MyClass` `MyCode` .

```fsharp
// Bad!
module MyCode

type MyClass() =
    ...
```

### <a name="carefully-apply-autoopen"></a>Dikkatle Uygula`[<AutoOpen>]`

`[<AutoOpen>]`Yapı, çağıranlar için kullanılabilir olan kapsamı ve bir şeyin geldiği yanıtın "Magic" olduğunu pollute olabilir. Bu iyi bir şey değildir. Bu kural için bir özel durum, F # Çekirdek kitaplığının kendisidir (Bu olgu aynı zamanda bir bit controversıal).

Ancak, bu genel API 'den ayrı olarak düzenlemek istediğiniz ortak API için yardımcı işlevselliğe sahipseniz kolaylık vardır.

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

Bu, her çağırdığınızda bir yardımcıyı tam olarak nitelendirmek zorunda kalmadan, bir işlevin ortak API 'sinden uygulama ayrıntılarını düzgün bir şekilde ayırmanızı sağlar.

Ek olarak, ad alanı düzeyinde uzantı yöntemlerinin ve ifade oluşturucuların kullanıma sunulması ile birlikte ifade edilebilir `[<AutoOpen>]` .

### <a name="use-requirequalifiedaccess-whenever-names-could-conflict-or-you-feel-it-helps-with-readability"></a>`[<RequireQualifiedAccess>]`Adların ne zaman çakıştığını veya okunabilirlik konusunda yardımcı olduğunu düşünüyorsanız kullanın

`[<RequireQualifiedAccess>]`Özniteliği bir modüle eklemek, modülün açılamayabilir ve modülün öğelerine yapılan başvuruların açık nitelikli erişim gerektirdiğini gösterir. Örneğin, `Microsoft.FSharp.Collections.List` modülün bu özniteliği vardır.

Bu, modüldeki işlevlerin ve değerlerin diğer modüllerdeki adlarla çakışabilecek adlara sahip olduğu durumlarda faydalıdır. Tam erişim gerektirmek, bir kitaplığın uzun süreli bakım ve gelişmesini büyük ölçüde artırabilir.

```fsharp
[<RequireQualifiedAccess>]
module StringTokenization =
    let parse s = ...

...

let s = getAString()
let parsed = StringTokenization.parse s // Must qualify to use 'parse'
```

### <a name="sort-open-statements-topologically"></a>Sort `open` deyimleri topologically

F # ' da, deyimler dahil olmak üzere bildirimlerin sırası önemlidir `open` . Bu, `using` ve efektinin bir dosyadaki deyimlerin sıralarından bağımsız olduğu C# ' nin aksine `using static` .

F # ' da, bir kapsamda açılan öğeler başkalarının daha önceden var olan öğelerini gölgelendirebilir. Bu, yeniden sıralama `open` deyimlerinin kodun anlamını değiştirebilecek anlamına gelir. Sonuç olarak, tüm `open` deyimlerin (örneğin, alfasayısal) herhangi bir rastgele sıralanması önerilmez, en uzun işlem, bekleneceğiniz farklı davranışlar oluşturur.

Bunun yerine, [topologically](https://en.wikipedia.org/wiki/Topological_sorting); diğer bir deyişle, `open` deyimlerinizi sisteminizin _katmanlarının_ tanımlandığı sırada sıralayın. Farklı topolojik katmanlarda Alfasayısal sıralama yapmak de göz önünde bulundurulmayabilir.

Örnek olarak, F # derleyicisi hizmeti ortak API dosyası için topik sıralama aşağıda verilmiştir:

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

Bir satır sonu, her katmana daha sonra alfasayısal olarak sıralanmakta olan topik katmanları ayırır. Bu, yanlışlıkla gölgeleme değerleri olmadan kodu düzgün bir şekilde düzenler.

## <a name="use-classes-to-contain-values-that-have-side-effects"></a>Yan etkileri olan değerleri içermesi için sınıfları kullanma

Bir değerin başlatılması, bir veritabanı veya başka bir uzak kaynak için bir bağlamı örneklendirirken birçok zaman olabilir. Bu tür şeyleri bir modülde başlatmak ve sonraki işlevlerde kullanmak önemlidir:

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

Bu, birkaç nedenden dolayı çoğunlukla kötü bir fikir olabilir:

İlk olarak, uygulama yapılandırması, ve ile kod tabanına `dep1` gönderilir `dep2` . Daha büyük kod tabanlarında bakım yapmak zordur.

İkinci olarak, bileşen birden çok iş parçacığı kullanıyorsa, statik olarak başlatılan veriler iş parçacığı güvenli olmayan değerler içermemelidir. Bu, tarafından açıkça ihlal edilir `dep3` .

Son olarak, modül başlatması tüm derleme birimi için statik bir oluşturucuya derlenir. Bu modülde izin-bağlandeğer başlatma bölümünde herhangi bir hata oluşursa, bu, `TypeInitializationException` daha sonra uygulamanın kullanım ömrü boyunca önbelleğe alınmış bir olarak bildirim oluşturulur. Bunu tanılamak zor olabilir. Genellikle bunun nedenini deneyebilmeniz için bir iç özel durum vardır, ancak yoksa, kök nedenin ne olduğunu söylemez.

Bunun yerine, bağımlılıkları tutmak için basit bir sınıf kullanmanız yeterlidir:

```fsharp
type MyParametricApi(dep1, dep2, dep3) =
    member _.Function1 arg1 = doStuffWith dep1 dep2 dep3 arg1
    member _.Function2 arg2 = doStuffWith dep1 dep2 dep3 arg2
```

Bu, şunları sunar:

1. Herhangi bir bağımlı durumu API 'nin dışında iletme.
2. Yapılandırma artık API dışında yapılabilir.
3. Bağımlı değerler için başlatma hatası, bir olarak bildirimde bulunma olasılığı yoktur `TypeInitializationException` .
4. API artık test etmek daha kolay.

## <a name="error-management"></a>Hata yönetimi

Büyük sistemlerde hata yönetimi karmaşık ve anormal bir Endeavor ve sistemlerinizin hataya dayanıklı ve iyi davranmasını sağlamaya yönelik gümüş bir madde işareti yoktur. Aşağıdaki kılavuzlar, bu zor alanda gezinmek için rehberlik sunmalıdır.

### <a name="represent-error-cases-and-illegal-state-in-types-intrinsic-to-your-domain"></a>Etki alanınız için iç türlerde hata durumlarını ve geçersiz durumu temsil eder

[Ayrılmış birleşimler](../language-reference/discriminated-unions.md)ile, F #, tür sisteminizde hatalı program durumunu temsil etme olanağı sunar. Örneğin:

```fsharp
type MoneyWithdrawalResult =
    | Success of amount:decimal
    | InsufficientFunds of balance:decimal
    | CardExpired of DateTime
    | UndisclosedFailure
```

Bu durumda, bir banka hesabından paranın bir şekilde çizmesinin başarısız olması için üç bilinen yol vardır. Her bir hata durumu, türünde temsil edilir ve bu nedenle program genelinde güvenle ele alınabilir.

```fsharp
let handleWithdrawal amount =
    let w = withdrawMoney amount
    match w with
    | Success am -> printfn "Successfully withdrew %f" am
    | InsufficientFunds balance -> printfn "Failed: balance is %f" balance
    | CardExpired expiredDate -> printfn "Failed: card expired on %O" expiredDate
    | UndisclosedFailure -> printfn "Failed: unknown"
```

Genel olarak, etki alanındaki bir şeyin **başarısız olmasına** yönelik farklı yollar modelleyebilir, daha sonra hata işleme kodu artık normal program akışına ek olarak uğraşmanız gereken bir şey olarak değerlendirilmez. Yalnızca normal program akışının bir parçasıdır ve **olağanüstü**olarak kabul edilmez. Bunun başlıca iki avantajı vardır:

1. Etki alanınız zaman içinde değiştikçe bakım daha kolay olur.
2. Hata durumlarının birim testi daha kolay.

### <a name="use-exceptions-when-errors-cannot-be-represented-with-types"></a>Hatalar türlerle gösterilemeyeceği durumlarda özel durumlar kullanın

Hatalar bir sorun etki alanında gösterilemez. Bu tür hatalar doğası gereği *, bu* nedenle F # içinde özel durum tetikleyebilme ve yakalayamaz.

İlk olarak, [özel durum tasarım kılavuzunu](../../standard/design-guidelines/exceptions.md)okumanız önerilir. Bunlar F # için de geçerlidir.

Özel durumları tetikme amaçları için F # ' da kullanılabilen ana yapılar, aşağıdaki tercih sırasına göre düşünülmelidir:

| İşlev | Sözdizimi | Amaç |
|----------|--------|---------|
| `nullArg` | `nullArg "argumentName"` | `System.ArgumentNullException`Belirtilen bağımsız değişken adına sahip bir oluşturur. |
| `invalidArg` | `invalidArg "argumentName" "message"` | `System.ArgumentException`Belirtilen bağımsız değişken adı ve iletisiyle bir ile başlatır. |
| `invalidOp` | `invalidOp "message"` | `System.InvalidOperationException`Belirtilen iletiyle bir oluşturur. |
|`raise`| `raise (ExceptionType("message"))` | Özel durum oluşturmak için genel amaçlı mekanizma. |
| `failwith` | `failwith "message"` | `System.Exception`Belirtilen iletiyle bir oluşturur. |
| `failwithf` | `failwithf "format string" argForFormatString` | , `System.Exception` Biçim dizesi ve girişleri tarafından belirlenen bir ileti ile başlatır. |

`nullArg`' İ `invalidArg` ve ' yi `invalidOp` oluşturmak için gereken mekanizmayı ve `ArgumentNullException` `ArgumentException` `InvalidOperationException` uygun olduğunda kullanın.

`failwith`Ve `failwithf` işlevlerinin genellikle kaçınılması gerekir `Exception` , çünkü belirli bir özel durum değil temel türü yükseltir. [Özel durum tasarım yönergelerine](../../standard/design-guidelines/exceptions.md)göre,, ' yi kullanırken daha özel özel durumlar da yapmak istersiniz.

### <a name="using-exception-handling-syntax"></a>Özel durum işleme söz dizimini kullanma

F #, sözdizimi aracılığıyla özel durum düzenlerini destekler `try...with` :

```fsharp
try
    tryGetFileContents()
with
| :? System.IO.FileNotFoundException as e -> // Do something with it here
| :? System.Security.SecurityException as e -> // Do something with it here
```

Bir özel durumun açık olması için işlevselliği karşılaştırma, kod temizlemeyi sağlamak istiyorsanız biraz karmaşık olabilir. Bunu işlemenin bir yolu, [etkin desenleri](../language-reference/active-patterns.md) bir özel durum ile bir hata durumu çevreleyen işlevselliği gruplandırmak için bir yol olarak kullanmaktır. Örneğin, bir özel durum oluşturduğunda, önemli bilgileri özel durum meta verilerinde kapsayan bir API kullanıyor olabilirsiniz. Etkin düzenin içindeki yakalanan özel durum gövdesinde yararlı bir değeri sarmalama ve bu değeri döndürme bazı durumlarda yararlı olabilir.

### <a name="do-not-use-monadic-error-handling-to-replace-exceptions"></a>Özel durumları değiştirmek için monadıc hata işleme kullanmayın

Özel durumlar fonksiyonel programlamada biraz Taboo olarak görülür. Aslında özel durumlar ihlal ediyor, bu nedenle bunları çok işlevli olarak düşünmek güvenlidir. Ancak, bu durum kodun çalışması gereken gerçekliği yoksayar ve çalışma zamanı hataları oluşabilir. Genel olarak, önemli sürprleri en aza indirmek için çoğu şeyin saf veya toplam olmadığı varsayımına göre kod yazın.

.NET çalışma zamanı ve çapraz dil ekosisteminde bir bütün olarak ilgi ve uygunluk açısından, özel durumların önem derecesine/yönlerini göz önünde bulundurmanız önemlidir.

1. Bu kişiler, bir sorun ayıklanırken çok yararlı olan ayrıntılı tanılama bilgilerini içerirler.
2. Çalışma zamanı ve diğer .NET dilleri tarafından iyi anlaşılabilirler.
3. Bu kişiler, semantiğinin bazı alt kümelerini geçici olarak uygulayarak özel durumların *önüne* geçen kodla karşılaştırıldığında önemli ortak bir şekilde azalabilir.

Bu üçüncü nokta kritiktir. Önemsiz olmayan karmaşık işlemler için, özel durumları kullanmayan durumlar, şunun gibi yapılarla ilgileniyor:

```fsharp
Result<Result<MyType, string>, string list>
```

Bu, "stringly-yazılan" hatalarda model eşleştirme gibi kırılmamış koda kolayca yol açabilir:

```fsharp
let result = doStuff()
match result with
| Ok r -> ...
| Error e ->
    if e.Contains "Error string 1" then ...
    elif e.Contains "Error string 2" then ...
    else ... // Who knows?
```

Ayrıca, "Nicer" türü döndüren bir "basit" işlevi için istenen özel duruma izin verebilir.

```fsharp
// This is bad!
let tryReadAllText (path : string) =
    try System.IO.File.ReadAllText path |> Some
    with _ -> None
```

Ne yazık ki, `tryReadAllText` bir dosya sisteminde gerçekleşebilecek şeyler hakkında çok sayıda özel durum oluşturabilir ve bu kod ortamınızda gerçekten yanlış duruma gelmiş olabilecek bilgileri atar. Bu kodu bir sonuç türüyle değiştirirseniz, "stringly-Typed" hata iletisi ayrıştırma ' ya geri dönebilirsiniz:

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

Ayrıca, özel durum nesnesinin kendisini oluşturucuya yerleştirilmesi, `Error` işlev yerine çağrı sitesindeki özel durum türüyle düzgün bir şekilde uğraşmaya zorlar. Bunu etkin hale getirmek, bir API çağıranı olarak ele alınması için önemli ölçüde eğlenceli olmayan, denetlenen özel durumlar oluşturur.

Yukarıdaki örneklere iyi bir alternatif, *belirli* özel durumları yakalamak ve bu özel durumun bağlamına anlamlı bir değer döndürmemelidir. `tryReadAllText`İşlevi aşağıdaki gibi değiştirirseniz, `None` daha fazla anlamı vardır:

```fsharp
let tryReadAllTextIfPresent (path : string) =
    try System.IO.File.ReadAllText path |> Some
    with :? FileNotFoundException -> None
```

Catch-all olarak çalışmak yerine, bu işlev artık bir dosya bulunamadığı ve bu anlamı bir return öğesine atayan durumu doğru şekilde işleymeyecektir. Bu dönüş değeri bu hata durumuyla eşleşirken, herhangi bir bağlamsal bilgileri atmakla veya çağıranların koddaki bu noktada ilgisi olmayan bir servis talebiyle uğraşmak üzere zorlanmamalıdır.

Gibi türler `Result<'Success, 'Error>` , iç içe olmadıkları durumlarda temel işlemler için uygundur ve F # isteğe bağlı türleri *bir şeyi* veya *hiç*birini döndürene zaman dönebileceği temsil etmek için mükemmeldir. Özel durumların yerini almaz, ancak özel durumları değiştirme girişiminde kullanılmamalıdır. Bunun yerine, özel durum ve hata yönetimi ilkesinin hedeflenen yollarla belirli yönlerini karşılamak için bozacağından uygulanmalıdır.

## <a name="partial-application-and-point-free-programming"></a>Kısmi uygulama ve noktadan ücretsiz programlama

F # kısmi uygulamayı destekler ve bu nedenle, noktadan farklı stilde programlama için çeşitli yollar sunar. Bu, bir modül içindeki kod yeniden kullanımı veya bir şeyin uygulanması için faydalı olabilir, ancak genel kullanıma sunulmayı bir şey değildir. Genel olarak, ücretsiz programlama, ve içinde bir virtuale değildir ve stilde sarmalanmış olmayan kişiler için önemli bir bilişsel engel ekleyebilir.

### <a name="do-not-use-partial-application-and-currying-in-public-apis"></a>Kısmi uygulama kullanmayın ve ortak API 'lerde currying kullanın

Küçük bir özel durumla, genel API 'lerde kısmi uygulama kullanımı, tüketiciler için kafa karıştırıcı olabilir. Genellikle, `let` F # kodundaki bağlantılı değerler, **işlev değerleri**değil **değerlerdir**. Değerleri ve işlev değerlerini birlikte karıştırmak, özellikle de işlevleri oluşturmak için gibi işleçlerle birleştirildiğinde, çok sayıda bilişsel ek yük için Exchange 'de küçük miktarda kod satırı kaydedilmesine neden olabilir `>>` .

### <a name="consider-the-tooling-implications-for-point-free-programming"></a>Noktadan noktaya ücretsiz programlama için araç etkilerini göz önünde bulundurun

Curried işlevleri bağımsız değişkenlerini etiketetmez. Bu, etkilerini olumsuz etkiler. Aşağıdaki iki işlevi göz önünde bulundurun:

```fsharp
let func name age =
    printfn "My name is %s and I am %d years old!" name age

let funcWithApplication =
    printfn "My name is %s and I am %d years old!"
```

Her ikisi de geçerli işlevlerdir, ancak `funcWithApplication` curried bir işlevdir. Bir düzenleyicide türlerin üzerine geldiğinizde şunu görürsünüz:

```fsharp
val func : name:string -> age:int -> unit

val funcWithApplication : (string -> int -> unit)
```

Çağrı sitesinde, Visual Studio gibi araç ipuçları, `string` ve `int` Giriş türlerinin gerçekten temsil ettiği şekilde size anlamlı bilgiler vermeyecektir.

Herkese açık şekilde tüketilebilir gibi nokta içermeyen `funcWithApplication` bir kodla karşılaşırsanız, araç, bağımsız değişkenler için anlamlı adlara sahip olması için tam η genişletmesi yapmanız önerilir.

Ayrıca, hata ayıklama noktası ücretsiz kod, mümkün değilse zor olabilir. Hata ayıklama araçları, adlara bağlı değerleri kullanır (örneğin, `let` bağlamalar) ve böylece ara değerleri, yürütme aracılığıyla bir şekilde inceleyebilirsiniz. Kodunuzun incelenecek bir değeri olmadığında hata ayıklamanın bir şey yoktur. Gelecekte, hata ayıklama araçları, daha önce yürütülen yollara göre bu değerleri sentezleştirmek üzere gelişiyor, ancak sonuçlarınızı *olası* hata ayıklama işlevselliğine göre eklemek iyi bir fikir değildir.

### <a name="consider-partial-application-as-a-technique-to-reduce-internal-boilerplate"></a>İç ortak uygulamayı azaltmak için kısmi uygulamayı bir teknik olarak düşünün

Önceki noktanın aksine kısmi uygulama, bir uygulamanın içindeki demirbaş veya bir API 'nin daha derin iç içe geçmiş olması için harika bir araçtır. Daha karmaşık API 'lerin uygulanması yararlı olabilir; burada ortak, genellikle ilgileniyor bir sorun. Örneğin, aşağıdaki kod, en fazla bir çerçeve için bir dış bağımlılık almadan ve ilgili bir beste API öğrenmeye gerek kalmadan size en fazla ne kadar çok şey sağladığını nasıl gerçekleştirebileceğinizi göstermektedir.

Örneğin, aşağıdaki çözüm topografisini göz önünde bulundurun:

```
MySolution.sln
|_/ImplementationLogic.fsproj
|_/ImplementationLogic.Tests.fsproj
|_/API.fsproj
```

`ImplementationLogic.fsproj`Şu gibi bir kod açığa çıkabilir:

```fsharp
module Transactions =
    let doTransaction txnContext txnType balance =
        ...

type Transactor(ctx, currentBalance) =
    member _.ExecuteTransaction(txnType) =
        Transactions.doTransaction ctx txtType currentBalance
        ...
```

`Transactions.doTransaction`' De birim testi `ImplementationLogic.Tests.fsproj` kolaydır:

```fsharp
namespace TransactionsTestingUtil

open Transactions

module TransactionsTestable =
    let getTestableTransactionRoutine mockContext = Transactions.doTransaction mockContext
```

`doTransaction`Bir sahte işlem bağlam nesnesiyle kısmen uygulamak, her seferinde bir mocıng bağlamı oluşturmaya gerek kalmadan, işlevi tüm birim testlerinizde çağırmanıza olanak sağlar:

```fsharp
namespace TransactionTests

open Xunit
open TransactionTypes
open TransactionsTestingUtil
open TransactionsTestingUtil.TransactionsTestable

let testableContext =
    { new ITransactionContext with
        member _.TheFirstMember() = ...
        member _.TheSecondMember() = ... }

let transactionRoutine = getTestableTransactionRoutine testableContext

[<Fact>]
let ``Test withdrawal transaction with 0.0 for balance``() =
    let expected = ...
    let actual = transactionRoutine TransactionType.Withdraw 0.0
    Assert.Equal(expected, actual)
```

Bu teknik, tüm kod tabanınıza evrensel olarak uygulanmamalıdır, ancak karmaşık iç yapılar ve bu iç yapıları için ortak bir yoldur.

## <a name="access-control"></a>Erişim denetimi

F #, [erişim denetimi](../language-reference/access-control.md)için birden fazla seçeneğe sahiptir ve .NET çalışma zamanında kullanılabilir olan öğeden devralınır. Bunlar yalnızca türler için kullanılamaz. bunları işlevler için de kullanabilirsiniz.

* `public`Türleri ve üyeleri, herkese açık bir şekilde tüketilene kadar tercih edin. Bu Ayrıca, hangi tüketicilerin için de en aza indirir.
* Tüm yardımcı işlevleri tutmak için çaba harcar `private` .
* `[<AutoOpen>]`Çok sayıda hale gelirse, yardımcı işlevlerin özel modülünde kullanımını göz önünde bulundurun.

## <a name="type-inference-and-generics"></a>Tür çıkarımı ve genel türler

Tür çıkarımı, çok sayıda demirbaş yazmanız için sizi kaydedebilir. F # derleyicisinde otomatik Genelleştirme, sizin bölüminizdeki neredeyse hiç fazla çaba olmadan daha fazla genel kod yazmanıza yardımcı olabilir. Ancak, bu özellikler evrensel olarak iyi değildir.

* Bağımsız değişken adlarını ortak API 'lerde açık türlerle etiketlemeyi düşünün ve bunun için tür çıkarımı kullanmayın.

    Bunun nedeni, derleyicinin değil, API 'nizin şeklinin denetiminde **olması gerekir.** Derleyici, sizin için türler üzerinde ince bir iş yapabilse de, bağımlı olduğu iç işlem tür türleri değiştiyse API 'nizin şeklinin değiştirilmesi mümkündür. Bu, istediğiniz gibi olabilir, ancak aşağı akış tüketicilerinin daha sonra uğraşmak zorunda olacağı bir API değişikliğine neredeyse tamamen neden olur. Bunun yerine, ortak API 'nizin şeklini açıkça kontrol ediyorsanız, bu son değişiklikleri denetleyebilirsiniz. DDD terimlerinde, bu, bozulma önleyici bir katman olarak düşünülebilir.

* Genel bağımsız değişkenlerinize anlamlı bir ad vermeyi düşünün.

    Belirli bir etki alanına özgü olmayan gerçekten genel kod yazmadığınız takdirde anlamlı bir ad, diğer programcıların çalıştıkları etki alanını anlamasına yardımcı olabilir. Örneğin, `'Document` bir belge veritabanıyla etkileşim bağlamında adlı bir tür parametresi, genel belge türlerinin, çalıştığınız işlev veya üye tarafından kabul edilebilir olmasını sağlar.

* Genel tür parametrelerini PascalCase ile adlandırmayı düşünün.

    Bu, .NET ' te şeyler yapmanın genel yoludur. bu nedenle, snake_case veya camelCase yerine PascalCase kullanmanız önerilir.

Son olarak, otomatik Genelleştirme, F # veya büyük bir kod temeli için yeni olan kişiler için her zaman bir Boon değildir. Genel olan bileşenleri kullanırken bilişsel ek yükü vardır. Ayrıca, otomatik olarak Genelleştirilmiş işlevler farklı giriş türleriyle kullanılmazsa (Bu şekilde kullanılması amaçlanıyorsa tek başına izin ver), bu noktada bu noktada genel olan gerçek bir avantaj yoktur. Yazmakta olduğunuz kodun gerçekten genel olmasının yararlı olacağını her zaman göz önünde bulundurun.

## <a name="performance"></a>Performans

### <a name="prefer-structs-for-small-data-types"></a>Küçük veri türleri için yapıları tercih et

Yapıları (değer türleri olarak da bilinir) kullanmak, genellikle nesne ayırmayı önlediği için bazı kodlar için daha yüksek performans oluşmasına neden olabilir. Ancak, yapılar her zaman bir "daha hızlı git" düğmesi değildir: bir yapı içindeki verilerin boyutu 16 baytı aşarsa, verilerin kopyalanması genellikle başvuru türü kullanmaktan daha fazla CPU süresi harcanmasına neden olabilir.

Yapısını kullanıp kullanmadığını öğrenmek için aşağıdaki koşulları göz önünde bulundurun:

- Verilerinizin boyutu 16 bayt veya daha küçükse.
- Büyük olasılıkla, çalışan bir programda bellekte yerleşik olarak bulunan bu veri türlerinden birçoğuna sahip olabilirsiniz.

İlk koşul geçerliyse, genellikle bir struct kullanmanız gerekir. Her ikisi de varsa, neredeyse her zaman bir struct kullanmanız gerekir. Önceki koşulların geçerli olduğu bazı durumlar olabilir, ancak bir yapının kullanılması bir başvuru türü kullanmaktan daha iyi veya daha kötütür değildir ancak nadir olabilir. Bu, ancak bu gibi değişiklikler yaparken her zaman ölçülmek önemlidir, ancak varsayım veya ıntukon üzerinde çalışmaz.

#### <a name="prefer-struct-tuples-when-grouping-small-value-types"></a>Küçük değer türlerini gruplarken yapı tanımlama gruplarını tercih et

Aşağıdaki iki işlevi göz önünde bulundurun:

```fsharp
let rec runWithTuple t offset times =
    let offsetValues x y z offset =
        (x + offset, y + offset, z + offset)

    if times <= 0 then
        t
    else
        let (x, y, z) = t
        let r = offsetValues x y z offset
        runWithTuple r offset (times - 1)

let rec runWithStructTuple t offset times =
    let offsetValues x y z offset =
        struct(x + offset, y + offset, z + offset)

    if times <= 0 then
        t
    else
        let struct(x, y, z) = t
        let r = offsetValues x y z offset
        runWithStructTuple r offset (times - 1)
```

Bu işlevleri [Benchmarkdotnet](https://benchmarkdotnet.org/)gibi istatistiksel bir değerlendirme aracı ile kıyasladığınızda, `runWithStructTuple` Yapı tanımlama gruplarını kullanan işlevin %40 daha hızlı çalıştığını ve bellek ayırdığını fark edeceksiniz.

Ancak, bu sonuçlar her zaman kendi kodunuzda durum değildir. Bir işlevi olarak işaretlerseniz `inline` , başvuru tanımlama gruplarını kullanan kod bazı ek iyileştirmeler alabilir veya ayrılacak kod yalnızca en iyi duruma getirilebilir. Performans açısından her zaman sonuçları ölçmelisiniz ve varsayım ya da ıntuksiz göre hiçbir zaman çalışmaz.

#### <a name="prefer-struct-records-when-the-data-type-is-small"></a>Veri türü küçük olduğunda yapı kayıtlarını tercih et

Daha önce açıklanan Thumb kuralı [F # kayıt türleri](../language-reference/records.md)için de geçerlidir. Aşağıdaki veri türlerini ve bunları işleyen işlevleri göz önünde bulundurun:

```fsharp
type Point = { X: float; Y: float; Z: float }

[<Struct>]
type SPoint = { X: float; Y: float; Z: float }

let rec processPoint (p: Point) offset times =
    let inline offsetValues (p: Point) offset =
        { p with X = p.X + offset; Y = p.Y + offset; Z = p.Z + offset }

    if times <= 0 then
        p
    else
        let r = offsetValues p offset
        processPoint r offset (times - 1)

let rec processStructPoint (p: SPoint) offset times =
    let inline offsetValues (p: SPoint) offset =
        { p with X = p.X + offset; Y = p.Y + offset; Z = p.Z + offset }

    if times <= 0 then
        p
    else
        let r = offsetValues p offset
        processStructPoint r offset (times - 1)
```

Bu, önceki demet koduna benzerdir, ancak bu kez örnek kayıtları ve satır içi bir iç işlevi kullanır.

Bu işlevleri [Benchmarkdotnet](https://benchmarkdotnet.org/)gibi istatistiksel bir değerlendirme aracı ile kıyaslandığınızda, `processStructPoint` %60 daha hızlı bir şekilde çalıştığını ve yönetilen yığında hiçbir şey ayırdığını görürsünüz.

#### <a name="prefer-struct-discriminated-unions-when-the-data-type-is-small"></a>Veri türü küçük olduğunda struct ayrılmış birleşimler tercih et

Struct tanımlama grupları ve kayıtlarıyla performans hakkında önceki gözlemler Ayrıca, [F # ayrılmış birleşimler](../language-reference/discriminated-unions.md)için de geçerlidir. Aşağıdaki kodu inceleyin:

```fsharp
    type Name = Name of string

    [<Struct>]
    type SName = SName of string

    let reverseName (Name s) =
        s.ToCharArray()
        |> Array.rev
        |> string
        |> Name

    let structReverseName (SName s) =
        s.ToCharArray()
        |> Array.rev
        |> string
        |> SName
```

Bu, etki alanı modelleme için bunun gibi tek büyük harfli ayırt edici birleşimler tanımlamak yaygındır. Bu işlevleri [Benchmarkdotnet](https://benchmarkdotnet.org/)gibi istatistiksel bir değerlendirme aracı ile kıyaslandığınızda, `structReverseName` `reverseName` küçük dizeler için %25 daha hızlı bir şekilde çalıştığını fark edeceksiniz. Büyük dizeler için her ikisi de aynı şekilde gerçekleştirilir. Bu nedenle, bu durumda her zaman bir struct kullanılması tercih edilir. Daha önce belirtildiği gibi, varsayımlar veya ıntuklarda her zaman ölçüm ve işlem kullanmayın.

Önceki örnekte, bir yapının ayırt edici UNION birleşimi daha iyi performans olduğunu gösterdi, ancak bir etki alanını modellemesi sırasında daha büyük ayırt edici birleşimler olması yaygındır. Daha büyük veri türleri, daha fazla kopyalama söz konusu olduğundan, bunlar üzerinde işlemlere göre yapılar olmaları halinde de gerçekleştirilemeyebilir.

### <a name="functional-programming-and-mutation"></a>Fonksiyonel programlama ve mutasyon

F # değerleri varsayılan olarak sabittir. Bu, belirli hata sınıflarından kaçınmanızı sağlar (özellikle eşzamanlılık ve paralellik dahil olanlar). Bununla birlikte, belirli durumlarda, yürütme süresi veya bellek ayırmaları için en iyi (veya hatta makul) verimlilik elde etmek üzere bir iş yayılımı en iyi duruma geçen durum ile uygulanabilir. Bu, anahtar sözcüğü ile F # ile bir katılım temelinde mümkündür `mutable` .

`mutable`F # içinde öğesinin kullanımı, gürültü 'yi işlevsel bir şekilde kullanabilir. Bu, anlaşılır değildir ancak her yerde işlevsel anlaya, performans hedeflerine sahip gürültü 'de bulunabilir. Bir uzlaşma, çağrı yapanların bir işlevi çağırdıkları sırada ne olacağı hakkında İlgilenmemeleri gereken her şeyi kapsüllemesidir. Bu, performans açısından kritik kod için bir mutasyon tabanlı uygulama üzerinde işlevsel bir arabirim yazmanızı sağlar.

#### <a name="wrap-mutable-code-in-immutable-interfaces"></a>Değişmez arabirimlerde kesilebilir kodu sarın

Amaç olarak bilgi saydamlığı ile, performans açısından kritik işlevlerin değişebilir işlevlerini açığa çıkaran bir kod yazmak çok önemlidir. Örneğin, aşağıdaki kod `Array.contains` Işlevi F # Çekirdek Kitaplığı 'nda uygular:

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

Bu işlevi birden çok kez çağırmak, temel alınan diziyi değiştirmez veya onu tükettiği herhangi bir kesilebilir durumu korumanıza gerek duyar. Neredeyse her bir kod satırı mutation kullandığından bile, bu değer saydam bir şekilde görünür.

#### <a name="consider-encapsulating-mutable-data-in-classes"></a>Sınıflarda kesilebilir verileri kapsüllemek için kullanın

Önceki örnekte, değiştirilebilir verileri kullanarak işlemleri kapsüllemek için tek bir işlev kullanılmıştır. Bu, daha karmaşık veri kümeleri için her zaman yeterli değildir. Aşağıdaki işlev kümelerini göz önünde bulundurun:

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

Bu kod performanyadır, ancak çağıranların korunmasından sorumlu olduğu mutasyon tabanlı veri yapısını kullanıma sunar. Bu, değiştireyebilecek temel üye olmadan bir sınıfın içine sarmalanabilir:

```fsharp
open System.Collections.Generic

/// The results of computing the LALR(1) closure of an LR(0) kernel
type Closure1Table() =
    let t = Dictionary<Item0, HashSet<TerminalIndex>>()

    member _.Add(key, value) =
        if not (t.ContainsKey(key)) then
            t.Add(key, value)
        else
            t.[key] <- value

    member _.Count = t.Count

    member _.Contains(key, value) =
        match t.TryGetValue(key) with
        | (true, v) -> v.Equals(value)
        | (false, _) -> false
```

`Closure1Table`temel alınan mutasyon tabanlı veri yapısını kapsüller, böylece çağıranlar temel alınan veri yapısını sürdürmek üzere zorlar. Sınıflar, çağıranların ayrıntılarını açığa çıkarmadan tabanlı verileri ve yordamları kapsüllemek için güçlü bir yoldur.

#### <a name="prefer-let-mutable-to-reference-cells"></a>Hücrelere başvuru yapmayı tercih et `let mutable`

Başvuru hücreleri değerin kendisi yerine bir değere başvuruyu temsil etmenin bir yoludur. Performans açısından kritik kod için kullanılabilmesine rağmen, bunlar önerilmez. Aşağıdaki örneği inceleyin:

```fsharp
let kernels =
    let acc = ref Set.empty

    processWorkList startKernels (fun kernel ->
        if not ((!acc).Contains(kernel)) then
            acc := (!acc).Add(kernel)
        ...)

    !acc |> Seq.toList
```

Başvuru hücresinin kullanımı artık "pollutes", temel alınan verilere başvuru yapmak ve yeniden başvuru yapmak zorunda olan tüm izleyen koddur. Bunun yerine şunları göz önünde bulundurun `let mutable` :

```fsharp
let kernels =
    let mutable acc = Set.empty

    processWorkList startKernels (fun kernel ->
        if not (acc.Contains(kernel)) then
            acc <- acc.Add(kernel)
        ...)

    acc |> Seq.toList
```

Lambda ifadesinin ortasında yer alan tek bir noktadan sonra, dokunduğu diğer tüm kodlar, `acc` normal `let` bağlantılı sabit değerin kullanılmasına farklı olmayan bir şekilde bunu yapabilir. Bu, zaman içinde değişiklik yapmayı kolaylaştırır.

## <a name="object-programming"></a>Nesne programlama

F #, nesneler ve nesne yönelimli (OO) kavramları için tam desteğe sahiptir. Birçok OO kavramı güçlü ve yararlı olsa da, bunların hepsi kullanım için idealdir. Aşağıdaki listeler, en yüksek düzeyde, OO özelliklerinin kategorileri üzerinde rehberlik sunar.

**Bu özellikleri birçok durumda kullanmayı göz önünde bulundurun:**

* Nokta gösterimi ( `x.Length` )
* Örnek üyeleri
* Örtük oluşturucular
* Statik üyeler
* Dizin Oluşturucu gösterimi ( `arr.[x]` )
* Adlandırılmış ve Isteğe bağlı bağımsız değişkenler
* Arabirimler ve arabirim uygulamaları

**Önce bu özelliklere ulaşmayın, ancak bir sorunu çözmek için uygun olmaları durumunda bozacağından uygulayın:**

* Yöntem aşırı yüklemesi
* Encapsulated kesilebilir veriler
* Türlerde işleçler
* Otomatik Özellikler
* Uygulama `IDisposable` ve`IEnumerable`
* Tür uzantıları
* Olaylar
* Yapılar
* Temsilciler
* Numaralandırmalar

**Bunları kullanmanız gerekmedikçe bu özelliklerden genellikle kaçının:**

* Devralma tabanlı tür hiyerarşileri ve uygulama devralma
* Null değerleri ve`Unchecked.defaultof<_>`

### <a name="prefer-composition-over-inheritance"></a>Devralma üzerine oluşturmayı tercih et

[Devralma üzerinden bileşim](https://en.wikipedia.org/wiki/Composition_over_inheritance) , Iyi bir F # kodunun bağlı kalacağının uzun sürme deyimidir. Temel prensibi, temel bir sınıfı kullanıma sunmamalıdır ve arayanların işlevselliği almak için bu temel sınıftan devralmasını zorlamaktır.

### <a name="use-object-expressions-to-implement-interfaces-if-you-dont-need-a-class"></a>Sınıf gerekmiyorsa arabirim uygulamak için nesne ifadelerini kullanın

[Nesne ifadeleri](../language-reference/object-expressions.md) , bir sınıfın içinde olması gerekmeden uygulanan arabirimi bir değere bağlayarak, anında arabirim uygulamanıza olanak tanır. Bu, özellikle de _yalnızca_ arabirimini uygulamanız gerekiyorsa ve tam sınıfa gerek duygerekmiyorsa kullanışlı bir yöntemdir.

Örneğin, bir deyiminiz olmayan bir sembol eklediyseniz bir kod düzelme eylemi sağlamak için [ıonıde](https://ionide.io/) 'de çalıştırılan kod aşağıda verilmiştir `open` :

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

Visual Studio Code API ile etkileşim kurarken bir sınıfa gerek olmadığından, nesne Ifadeleri bunun için ideal bir araçtır. Ayrıca, test yordamlarına sahip bir arabirimi geçici olarak bir şekilde sağlamak istediğinizde birim testi için de değerlidir.

## <a name="consider-type-abbreviations-to-shorten-signatures"></a>İmzaları kısaltmak için kısaltmalar türlerini göz önünde bulundurun

[Tür kısaltmaları](../language-reference/type-abbreviations.md) , bir etiketi bir işlev imzası veya daha karmaşık bir tür gibi başka bir türe atamak için kullanışlı bir yoldur. Örneğin, aşağıdaki diğer ad, derin bir öğrenme kitaplığı olan [Cntk](https://docs.microsoft.com/cognitive-toolkit/)ile bir hesaplama tanımlamak için gereken bir etiketi atar:

```fsharp
open CNTK

// DeviceDescriptor, Variable, and Function all come from CNTK
type Computation = DeviceDescriptor -> Variable -> Function
```

Ad, daha `Computation` sonra gelen imzayla eşleşen herhangi bir işlevi göstermek için uygun bir yoldur. Bu gibi tür kısaltmalarının kullanılması kullanışlıdır ve daha fazla kısa kodu sağlar.

### <a name="avoid-using-type-abbreviations-to-represent-your-domain"></a>Etki alanınızı temsil etmek için tür kısaltmalarının kullanmaktan kaçının

Tür kısaltmaları işlev imzalara bir ad vermek için uygun olsa da, abbreviating diğer türler olduğunda kafa karıştırıcı olabilir. Bu kısaltmayı göz önünde bulundurun:

```fsharp
// Does not actually abstract integers.
type BufferSize = int
```

Bu, birden çok şekilde kafa karıştırıcı olabilir:

* `BufferSize`bir soyutlama değil; tamsayı için yalnızca başka bir addır.
* `BufferSize`Ortak BIR API 'de açığa çıkarılacası, kolayca yanlışlıkla büyük bir şekilde yorumlanabilmektedir `int` . Genellikle, etki alanı türlerinin kendileri için birden çok özniteliği vardır ve gibi basit türler değildir `int` . Bu kısaltma Bu varsayımını ihlal ediyor.
* Büyük/küçük harf `BufferSize` (PascalCase), bu türün daha fazla veri bulundurduğunu gösterir.
* Bu diğer ad, bir işleve adlandırılmış bir bağımsız değişken sağlamaya kıyasla daha fazla açıklık sunmaz.
* Kısaltma derlenmiş Il 'de bildirim içermez; yalnızca bir tamsayıdır ve bu diğer ad derleme zamanı yapısıdır.

```fsharp
module Networking =
    ...
    let send data (bufferSize: int) = ...
```

Özet olarak, tür kısaltmalarıyla birlikte, abbreviating oldukları türler üzerinde soyutlamalar **değildir** . Önceki örnekte, daha `BufferSize` `int` fazla veri olmadan ve tür sisteminden zaten sahip olduğu gibi herhangi bir avantajın altında yer alır `int` .

Bir etki alanını temsil etmek için tür kısaltmalarının kullanılmasına alternatif bir yaklaşım, tek büyük harf ayrılmış birleşimler kullanmaktır. Önceki örnek aşağıdaki gibi modellenebilir:

```fsharp
type BufferSize = BufferSize of int
```

`BufferSize`Ve temel aldığı değer bakımından çalışan kodu yazarsanız, herhangi bir rastgele tamsayı geçirmek yerine bir tane oluşturmanız gerekir:

```fsharp
module Networking =
    ...
    let send data (BufferSize size) =
    ...
```

Bu, `send` çağıran `BufferSize` işlevi çağırmadan önce bir değeri kaydırmak üzere bir tür oluşturmasının gerektiği için, yanlışlıkla rastgele bir tamsayıyı işleve dönüştürmek olasılığını azaltır.
