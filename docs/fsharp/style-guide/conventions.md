---
title: F# kodlama kuralları
description: Kod yazarken F# genel kılavuzları ve deyimleri öğrenin.
ms.date: 10/22/2019
ms.openlocfilehash: 6700f64aa61308cbfc0b7a38724d69a281a088db
ms.sourcegitcommit: 9bd1c09128e012b6e34bdcbdf3576379f58f3137
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2019
ms.locfileid: "72799106"
---
# <a name="f-coding-conventions"></a>F# kodlama kuralları

Aşağıdaki kurallar, büyük F# kod tabanlarında çalışma deneyiminden alınmıştır. [Beş iyi F# kod ilkeleri](index.md#five-principles-of-good-f-code) her bir önerinin temelidir. Bunlar [ F# bileşen tasarım yönergeleriyle](component-design-guidelines.md)ilgilidir, ancak yalnızca kitaplıklar gibi bileşenler değil tüm F# kodlar için geçerlidir.

## <a name="organizing-code"></a>Kodu düzenleme

F#kodu düzenlemenin iki birincil yolunu sunar: modüller ve ad alanları. Bunlar benzerdir, ancak aşağıdaki farklılıklara sahiptir:

* Ad alanları .NET ad alanları olarak derlenir. Modüller statik sınıflar olarak derlenir.
* Ad alanları her zaman en üst düzeydir. Modüller en üst düzey ve diğer modüller içinde iç içe olabilir.
* Ad alanları birden çok dosyaya yayılabilir. Modüller.
* Modüller `[<RequireQualifiedAccess>]` ve `[<AutoOpen>]`ile donatılmış olabilir.

Aşağıdaki yönergeler kodunuzu düzenlemek için bunları kullanmanıza yardımcı olur.

### <a name="prefer-namespaces-at-the-top-level"></a>En üst düzeyde ad alanlarını tercih et

Genel kullanım düzeylerine sahip herhangi bir kod için, ad alanları en üst düzeydeki modüllerle tercihe göre yapılır. .NET ad alanları olarak derlendiğinden, bunlar sorun olmadan tüketilebilir C# .

```fsharp
// Good!
namespace MyCode

type MyClass() =
    ...
```

En üst düzey bir modülün kullanılması yalnızca öğesinden F#çağrıldığında farklı görünmeyebilir, ancak Tüketicileriniz için C# ,`MyClass``MyCode`modülle nitelendirmek için arayanlar olabilir.

```fsharp
// Bad!
module MyCode

type MyClass() =
    ...
```

### <a name="carefully-apply-autoopen"></a>`[<AutoOpen>]` dikkatle uygulayın

`[<AutoOpen>]` yapısı, çağıranlar için kullanılabilir olan kapsamı ve bir şeyin geldiği yanıtın "Magic" olduğunu pollute. Bu genellikle iyi bir şeydir. Bu kural için bir özel durum, F# temel kitaplığın kendisidir (Bu olgu aynı zamanda bir bit controversıal).

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

Ek olarak, ad alanı düzeyinde uzantı yöntemlerinin ve ifade oluşturucuların kullanıma sunulması, `[<AutoOpen>]`ile ifade edilebilir.

### <a name="use-requirequalifiedaccess-whenever-names-could-conflict-or-you-feel-it-helps-with-readability"></a>Adlar her çakışıyorsa `[<RequireQualifiedAccess>]` kullanın veya okunabilirlik ile yardımcı olduğunu düşünüyorsanız

`[<RequireQualifiedAccess>]` özniteliğini bir modüle eklemek, modülün açılamayabilir ve modülün öğelerine yapılan başvuruların açık nitelikli erişim gerektirdiğini gösterir. Örneğin, `Microsoft.FSharp.Collections.List` modülü bu özniteliğe sahiptir.

Bu, modüldeki işlevlerin ve değerlerin diğer modüllerdeki adlarla çakışabilecek adlara sahip olduğu durumlarda faydalıdır. Tam erişim gerektirmek, bir kitaplığın uzun süreli bakım ve gelişmesini büyük ölçüde artırabilir.

```fsharp
[<RequireQualifiedAccess>]
module StringTokenization =
    let parse s = ...

...

let s = getAString()
let parsed = StringTokenization.parse s // Must qualify to use 'parse'
```

### <a name="sort-open-statements-topologically"></a>Sıralama `open` deyimleri topologically

İçinde F#, `open`deyimleriyle birlikte bildirimlerin önemli sırası. Bu,`using`C#ve`using static`efektinin bir dosyadaki deyimlerin sıralarından bağımsız olduğu şekilde farklı olur.

' F#De, bir kapsamda açılan öğeler, diğerlerinin zaten mevcut olduğu öğeleri gölgelendirebilir. Bu, yeniden sıralama `open` deyimlerinin kodun anlamını değiştirebilecek anlamına gelir. Sonuç olarak, tüm `open` deyimlerinin (örneğin, alfasayısal) herhangi bir rastgele sıralanması genellikle önerilmez, en uzun zaman beklemeniz gerekebilecek farklı davranışlar oluşturabilirsiniz.

Bunun yerine, [topologically](https://en.wikipedia.org/wiki/Topological_sorting); diğer bir deyişle, `open` deyimlerinizi sisteminizin _katmanlarının_ tanımlandığı sırada sıralayın. Farklı topolojik katmanlarda Alfasayısal sıralama yapmak de göz önünde bulundurulmayabilir.

Örnek olarak, F# derleyici HIZMETI ortak API dosyası için topik sıralama aşağıda verilmiştir:

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

İlk olarak, uygulama yapılandırması `dep1` ve `dep2`kod tabanına gönderilir. Daha büyük kod tabanlarında bakım yapmak zordur.

İkinci olarak, bileşen birden çok iş parçacığı kullanıyorsa, statik olarak başlatılan veriler iş parçacığı güvenli olmayan değerler içermemelidir. Bu, `dep3`tarafından açıkça ihlal edilir.

Son olarak, modül başlatması tüm derleme birimi için statik bir oluşturucuya derlenir. Bu modülde izin-bağlanan değer başlatma bölümünde herhangi bir hata oluşursa, uygulamanın kullanım ömrü boyunca önbelleğe alınmış bir `TypeInitializationException` olarak bildirim oluşturulur. Bunu tanılamak zor olabilir. Genellikle bunun nedenini deneyebilmeniz için bir iç özel durum vardır, ancak yoksa, kök nedenin ne olduğunu söylemez.

Bunun yerine, bağımlılıkları tutmak için basit bir sınıf kullanmanız yeterlidir:

```fsharp
type MyParametricApi(dep1, dep2, dep3) =
    member __.Function1 arg1 = doStuffWith dep1 dep2 dep3 arg1
    member __.Function2 arg2 = doStuffWith dep1 dep2 dep3 arg2
```

Bu, şunları sunar:

1. Herhangi bir bağımlı durumu API 'nin dışında iletme.
2. Yapılandırma artık API dışında yapılabilir.
3. Bağımlı değerler için başlatma hatalarının büyük olasılıkla `TypeInitializationException`olarak bildirimine izin verilmez.
4. API artık test etmek daha kolay.

## <a name="error-management"></a>Hata yönetimi

Büyük sistemlerde hata yönetimi karmaşık ve anormal bir Endeavor ve sistemlerinizin hataya dayanıklı ve iyi davranmasını sağlamaya yönelik gümüş bir madde işareti yoktur. Aşağıdaki kılavuzlar, bu zor alanda gezinmek için rehberlik sunmalıdır.

### <a name="represent-error-cases-and-illegal-state-in-types-intrinsic-to-your-domain"></a>Etki alanınız için iç türlerde hata durumlarını ve geçersiz durumu temsil eder

[Ayrılmış birleşimler](../language-reference/discriminated-unions.md)sayesinde, F# tür sisteminizde hatalı program durumunu temsil etme olanağı sunar. Örneğin:

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

Hatalar bir sorun etki alanında gösterilemez. Bu tür hataların doğası gereği *, bu* nedenle özel durumları ' de F#tetikleyebilme ve yakalayabilme özelliği vardır.

İlk olarak, [özel durum tasarım kılavuzunu](../../standard/design-guidelines/exceptions.md)okumanız önerilir. Bunlar için F#de geçerlidir.

Özel durumları oluşturma amaçları için F# ' de kullanılabilen ana yapılar, aşağıdaki tercih sırasına göre düşünülmelidir:

| İşlev | Sözdizimi | Amaç |
|----------|--------|---------|
| `nullArg` | `nullArg "argumentName"` | Belirtilen bağımsız değişken adıyla bir `System.ArgumentNullException` oluşturur. |
| `invalidArg` | `invalidArg "argumentName" "message"` | Belirtilen bağımsız değişken adı ve iletisiyle bir `System.ArgumentException` oluşturur. |
| `invalidOp` | `invalidOp "message"` | Belirtilen iletiyle bir `System.InvalidOperationException` oluşturur. |
|`raise`| `raise (ExceptionType("message"))` | Özel durum oluşturmak için genel amaçlı mekanizma. |
| `failwith` | `failwith "message"` | Belirtilen iletiyle bir `System.Exception` oluşturur. |
| `failwithf` | `failwithf "format string" argForFormatString` | Biçim dizesi ve girişleri tarafından belirlenen iletiyle bir `System.Exception` oluşturur. |

`nullArg`, `invalidArg` ve `invalidOp` uygun olduğunda `ArgumentNullException`, `ArgumentException` ve `InvalidOperationException` throw mekanizması olarak kullanın.

`failwith` ve `failwithf` işlevleri, belirli bir özel durum değil, temel `Exception` türünü yükselttiğinden genellikle kaçınılmalıdır. [Özel durum tasarım yönergelerine](../../standard/design-guidelines/exceptions.md)göre,, ' yi kullanırken daha özel özel durumlar da yapmak istersiniz.

### <a name="using-exception-handling-syntax"></a>Özel durum işleme söz dizimini kullanma

F#`try...with`söz dizimi aracılığıyla özel durum desenlerini destekler:

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

Ne yazık ki `tryReadAllText`, bir dosya sisteminde gerçekleşebilecek nesnelerin sayısız temelinde çok sayıda özel durum oluşturabilir ve bu kod, ortamınızda gerçekten yanlış duruma gelmiş olabilecek bilgilerin hiçbirini atar. Bu kodu bir sonuç türüyle değiştirirseniz, "stringly-Typed" hata iletisi ayrıştırma ' ya geri dönebilirsiniz:

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

Ayrıca, özel durum nesnesinin kendisini `Error` oluşturucuya yerleştirmek yalnızca, işlev yerine çağrı sitesindeki özel durum türüyle doğru şekilde uğraşmaya zorlar. Bunu etkin hale getirmek, bir API çağıranı olarak ele alınması için önemli ölçüde eğlenceli olmayan, denetlenen özel durumlar oluşturur.

Yukarıdaki örneklere iyi bir alternatif, *belirli* özel durumları yakalamak ve bu özel durumun bağlamına anlamlı bir değer döndürmemelidir. `tryReadAllText` işlevini aşağıdaki şekilde değiştirirseniz, `None` daha fazla anlamı vardır:

```fsharp
let tryReadAllTextIfPresent (path : string) =
    try System.IO.File.ReadAllText path |> Some
    with :? FileNotFoundException -> None
```

Catch-all olarak çalışmak yerine, bu işlev artık bir dosya bulunamadığı ve bu anlamı bir return öğesine atayan durumu doğru şekilde işleymeyecektir. Bu dönüş değeri bu hata durumuyla eşleşirken, herhangi bir bağlamsal bilgileri atmakla veya çağıranların koddaki bu noktada ilgisi olmayan bir servis talebiyle uğraşmak üzere zorlanmamalıdır.

`Result<'Success, 'Error>` gibi türler, iç içe olmadıkları temel işlemler için uygundur ve F# isteğe bağlı türler *bir şeyi* veya *hiç*birini döndürene zaman dönebileceği göstermek için idealdir. Özel durumların yerini almaz, ancak özel durumları değiştirme girişiminde kullanılmamalıdır. Bunun yerine, özel durum ve hata yönetimi ilkesinin hedeflenen yollarla belirli yönlerini karşılamak için bozacağından uygulanmalıdır.

## <a name="partial-application-and-point-free-programming"></a>Kısmi uygulama ve noktadan ücretsiz programlama

F#kısmi uygulamayı destekler ve bu nedenle, noktadan farklı stilde programlama için çeşitli yollar sunar. Bu, bir modül içindeki kod yeniden kullanımı veya bir şeyin uygulanması için yararlı olabilir, ancak genel olarak kullanıma sunulmayan bir şey değildir. Genel olarak, ücretsiz programlama, ve içinde bir virtuale değildir ve stilde sarmalanmış olmayan kişiler için önemli bir bilişsel engel ekleyebilir.

### <a name="do-not-use-partial-application-and-currying-in-public-apis"></a>Kısmi uygulama kullanmayın ve ortak API 'lerde currying kullanın

Küçük bir özel durumla, genel API 'lerde kısmi uygulama kullanımı, tüketiciler için kafa karıştırıcı olabilir. Genellikle, F# koddaki `let`bağlantılı değerler, **işlev değerleri**değil, **değerlerdir**. Değer ve işlev değerlerini bir araya getirmek, özellikle de işlevler oluşturmak için `>>` gibi işleçlerle birleştirildiğinde, çok sayıda bilişsel ek yük için Exchange 'de küçük miktarda kod satırı kaydedilmesine neden olabilir.

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

Çağrı sitesinde, Visual Studio gibi araç ipuçları, `string` ve `int` giriş türlerinin gerçekten temsil ettiği anlamlı bilgiler vermeyecektir.

Herkese açık şekilde tüketilebilir `funcWithApplication` gibi nokta içermeyen bir kodla karşılaşırsanız, araç, bağımsız değişkenlerin anlamlı adlarını görebilmesi için tam bir η genişletmesi yapmanız önerilir.

Ayrıca, hata ayıklama noktası ücretsiz kod, mümkün değilse zor olabilir. Hata ayıklama araçları, adlara bağlı değerleri kullanır (örneğin, `let` bağlamaları) ve böylece ara değerleri, yürütme aracılığıyla bir şekilde inceleyebilirsiniz. Kodunuzun incelenecek bir değeri olmadığında hata ayıklamanın bir şey yoktur. Gelecekte, hata ayıklama araçları, daha önce yürütülen yollara göre bu değerleri sentezleştirmek üzere gelişiyor, ancak sonuçlarınızı *olası* hata ayıklama işlevselliğine göre eklemek iyi bir fikir değildir.

### <a name="consider-partial-application-as-a-technique-to-reduce-internal-boilerplate"></a>İç ortak uygulamayı azaltmak için kısmi uygulamayı bir teknik olarak düşünün

Önceki noktanın aksine kısmi uygulama, bir uygulamanın içindeki demirbaş veya bir API 'nin daha derin iç içe geçmiş olması için harika bir araçtır. Daha karmaşık API 'lerin uygulanması yararlı olabilir; burada ortak, genellikle ilgileniyor bir sorun. Örneğin, aşağıdaki kod, en fazla bir çerçeve için bir dış bağımlılık almadan ve ilgili bir beste API öğrenmeye gerek kalmadan size en fazla ne kadar çok şey sağladığını nasıl gerçekleştirebileceğinizi göstermektedir.

Örneğin, aşağıdaki çözüm topografisini göz önünde bulundurun:

```
MySolution.sln
|_/ImplementationLogic.fsproj
|_/ImplementationLogic.Tests.fsproj
|_/API.fsproj
```

`ImplementationLogic.fsproj`, şu gibi bir kod açığa çıkabilir:

```fsharp
module Transactions =
    let doTransaction txnContext txnType balance =
        ...

type Transactor(ctx, currentBalance) =
    member __.ExecuteTransaction(txnType) =
        Transactions.doTransaction ctx txtType currentBalance
        ...
```

`ImplementationLogic.Tests.fsproj` birim testi `Transactions.doTransaction` kolaydır:

```fsharp
namespace TransactionsTestingUtil

open Transactions

module TransactionsTestable =
    let getTestableTransactionRoutine mockContext = Transactions.doTransaction mockContext
```

Bir sahte işlem bağlam nesnesiyle `doTransaction` kısmen uygulamak, her seferinde bir moclenmiş bağlam oluşturulmasına gerek kalmadan, işlevi tüm birim testlerinizde çağırmanıza olanak sağlar:

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

Bu teknik, tüm kod tabanınıza evrensel olarak uygulanmamalıdır, ancak karmaşık iç yapılar ve bu iç yapıları için ortak bir yoldur.

## <a name="access-control"></a>Erişim denetimi

F#, .NET çalışma zamanında kullanılabilir olan öğeden devralınan [erişim denetimi](../language-reference/access-control.md)için birden çok seçeneğe sahiptir. Bunlar yalnızca türler için kullanılamaz. bunları işlevler için de kullanabilirsiniz.

* `public` olmayan türleri ve üyeleri, herkese açık bir şekilde tüketilene kadar tercih edin. Bu Ayrıca, hangi tüketicilerin için de en aza indirir.
* Tüm yardımcı işlevleri `private`tutmak için çaba harcar.
* Çok sayıda hale gelirse, yardım işlevlerinin özel modülünde `[<AutoOpen>]` kullanımını göz önünde bulundurun.

## <a name="type-inference-and-generics"></a>Tür çıkarımı ve genel türler

Tür çıkarımı, çok sayıda demirbaş yazmanız için sizi kaydedebilir. Ve derleyicide otomatik Genelleştirme F# , sizin bölümlük üzerinde neredeyse hiç fazla çaba olmadan daha fazla genel kod yazmanıza yardımcı olabilir. Ancak, bu özellikler evrensel olarak iyi değildir.

* Bağımsız değişken adlarını ortak API 'lerde açık türlerle etiketlemeyi düşünün ve bunun için tür çıkarımı kullanmayın.

    Bunun nedeni, derleyicinin değil, API 'nizin şeklinin denetiminde **olması gerekir.** Derleyici, sizin için türler üzerinde ince bir iş yapabilse de, bağımlı olduğu iç işlem tür türleri değiştiyse API 'nizin şeklinin değiştirilmesi mümkündür. Bu, istediğiniz gibi olabilir, ancak aşağı akış tüketicilerinin daha sonra uğraşmak zorunda olacağı bir API değişikliğine neredeyse tamamen neden olur. Bunun yerine, ortak API 'nizin şeklini açıkça kontrol ediyorsanız, bu son değişiklikleri denetleyebilirsiniz. DDD terimlerinde, bu, bozulma önleyici bir katman olarak düşünülebilir.

* Genel bağımsız değişkenlerinize anlamlı bir ad vermeyi düşünün.

    Belirli bir etki alanına özgü olmayan gerçekten genel kod yazmadığınız takdirde anlamlı bir ad, diğer programcıların çalıştıkları etki alanını anlamasına yardımcı olabilir. Örneğin, bir belge veritabanıyla etkileşim bağlamında `'Document` adlı bir tür parametresi, genel belge türlerinin, çalıştığınız işlev veya üye tarafından kabul edilebilir olmasını sağlar.

* Genel tür parametrelerini PascalCase ile adlandırmayı düşünün.

    Bu, .NET ' te şeyler yapmanın genel yoludur, bu nedenle snake_case veya camelCase yerine PascalCase kullanmanız önerilir.

Son olarak, otomatik Genelleştirme her zaman için F# yeni olan veya büyük bir kod temeli olan kişiler için bir Boon değildir. Genel olan bileşenleri kullanırken bilişsel ek yükü vardır. Ayrıca, otomatik olarak Genelleştirilmiş işlevler farklı giriş türleriyle kullanılmazsa (Bu şekilde kullanılması amaçlanıyorsa tek başına izin ver), bu noktada bu noktada genel olan gerçek bir avantaj yoktur. Yazmakta olduğunuz kodun gerçekten genel olmasının yararlı olacağını her zaman göz önünde bulundurun.

## <a name="performance"></a>Performans

F#değerler, bazı hata sınıflarından kaçınmanıza izin veren (özellikle eşzamanlılık ve paralellik olanlar) varsayılan olarak sabittir. Bununla birlikte, belirli durumlarda, yürütme süresi veya bellek ayırmaları için en iyi (veya hatta makul) verimlilik elde etmek üzere bir iş yayılımı en iyi duruma geçen durum ile uygulanabilir. Bu,`mutable`anahtar sözcüğüyle birlikte F# kabul etme esasına göre yapılabilir.

Bununla birlikte, ' de `mutable` F# kullanımı, işlev takiresinin gürültü 'de olabilir. Bu, önemli olan beklentileri [bilgi saydamlığına](https://en.wikipedia.org/wiki/Referential_transparency)ayarlarsanız bu kadar iyidir. Bilgi saydamlığı-önemli değildir; işlevler yazılırken F# son hedeftir. Bu, performans açısından kritik kod için bir mutasyon tabanlı uygulama üzerinde işlevsel bir arabirim yazmanızı sağlar.

### <a name="wrap-mutable-code-in-immutable-interfaces"></a>Değişmez arabirimlerde kesilebilir kodu sarın

Amaç olarak bilgi saydamlığı ile, performans açısından kritik işlevlerin değişebilir işlevlerini açığa çıkaran bir kod yazmak çok önemlidir. Örneğin, aşağıdaki kod F# çekirdek kitaplığındaki `Array.contains` işlevini uygular:

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

### <a name="consider-encapsulating-mutable-data-in-classes"></a>Sınıflarda kesilebilir verileri kapsüllemek için kullanın

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

`Closure1Table` temel alınan mutasyon tabanlı veri yapısını kapsüller, böylece çağıranlar temel alınan veri yapısını sürdürmek üzere zorlar. Sınıflar, çağıranların ayrıntılarını açığa çıkarmadan tabanlı verileri ve yordamları kapsüllemek için güçlü bir yoldur.

### <a name="prefer-let-mutable-to-reference-cells"></a>Hücrelere başvurmak için `let mutable` tercih et

Başvuru hücreleri değerin kendisi yerine bir değere başvuruyu temsil etmenin bir yoludur. Performans açısından kritik kod için kullanılabilmesine rağmen, genellikle önerilmez. Aşağıdaki örneği göz önünde bulundurun:

```fsharp
let kernels =
    let acc = ref Set.empty

    processWorkList startKernels (fun kernel ->
        if not ((!acc).Contains(kernel)) then
            acc := (!acc).Add(kernel)
        ...)

    !acc |> Seq.toList
```

Başvuru hücresinin kullanımı artık "pollutes", temel alınan verilere başvuru yapmak ve yeniden başvuru yapmak zorunda olan tüm izleyen koddur. Bunun yerine `let mutable`göz önünde bulundurun:

```fsharp
let kernels =
    let mutable acc = Set.empty

    processWorkList startKernels (fun kernel ->
        if not (acc.Contains(kernel)) then
            acc <- acc.Add(kernel)
        ...)

    acc |> Seq.toList
```

Lambda ifadesinin ortasında yer alan tek bir noktadan sonra, `acc` dokunduğu diğer tüm kodlar, normal `let`bağlantılı sabit değerin kullanılmasına göre değil, bunu yapabilir. Bu, zaman içinde değişiklik yapmayı kolaylaştırır.

## <a name="object-programming"></a>Nesne programlama

F#nesneler ve nesne yönelimli (OO) kavramları için tam desteğe sahiptir. Birçok OO kavramı güçlü ve yararlı olsa da, bunların hepsi kullanım için idealdir. Aşağıdaki listeler, en yüksek düzeyde, OO özelliklerinin kategorileri üzerinde rehberlik sunar.

**Bu özellikleri birçok durumda kullanmayı göz önünde bulundurun:**

* Nokta gösterimi (`x.Length`)
* Örnek üyeleri
* Örtük oluşturucular
* Statik üyeler
* Dizin Oluşturucu gösterimi (`arr.[x]`)
* Adlandırılmış ve Isteğe bağlı bağımsız değişkenler
* Arabirimler ve arabirim uygulamaları

**Önce bu özelliklere ulaşmayın, ancak bir sorunu çözmek için uygun olmaları durumunda bozacağından uygulayın:**

* Yöntem aşırı yüklemesi
* Encapsulated kesilebilir veriler
* Türlerde işleçler
* Otomatik Özellikler
* `IDisposable` ve `IEnumerable` uygulama
* Tür uzantıları
* Olaylar
* Yapılar
* Temsilciler
* Numaralandırmalar

**Bunları kullanmanız gerekmedikçe bu özelliklerden genellikle kaçının:**

* Devralma tabanlı tür hiyerarşileri ve uygulama devralma
* Null değerler ve `Unchecked.defaultof<_>`

### <a name="prefer-composition-over-inheritance"></a>Devralma üzerine oluşturmayı tercih et

[Devralmayla Ilgili birleşim](https://en.wikipedia.org/wiki/Composition_over_inheritance) , iyi F# kodun bağlı olduğu uzun süreli bir deyimdir. Temel prensibi, temel bir sınıfı kullanıma sunmamalıdır ve arayanların işlevselliği almak için bu temel sınıftan devralmasını zorlamaktır.

### <a name="use-object-expressions-to-implement-interfaces-if-you-dont-need-a-class"></a>Sınıf gerekmiyorsa arabirim uygulamak için nesne ifadelerini kullanın

[Nesne ifadeleri](../language-reference/object-expressions.md) , bir sınıfın içinde olması gerekmeden uygulanan arabirimi bir değere bağlayarak, anında arabirim uygulamanıza olanak tanır. Bu, özellikle de _yalnızca_ arabirimini uygulamanız gerekiyorsa ve tam sınıfa gerek duygerekmiyorsa kullanışlı bir yöntemdir.

Örneğin, için `open` deyiminiz olmayan bir sembol eklediyseniz bir kod düzelme eylemi sağlamak üzere [ıonıde](http://ionide.io/) 'de çalıştırılan kod aşağıda verilmiştir:

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

`Computation` adı, diğer bir deyişle, daha sonra gelen imzayla eşleşen herhangi bir işlevi göstermek için uygun bir yoldur. Bu gibi tür kısaltmalarının kullanılması kullanışlıdır ve daha fazla kısa kodu sağlar.

### <a name="avoid-using-type-abbreviations-to-represent-your-domain"></a>Etki alanınızı temsil etmek için tür kısaltmalarının kullanmaktan kaçının

Tür kısaltmaları işlev imzalara bir ad vermek için uygun olsa da, abbreviating diğer türler olduğunda kafa karıştırıcı olabilir. Bu kısaltmayı göz önünde bulundurun:

```fsharp
// Does not actually abstract integers.
type BufferSize = int
```

Bu, birden çok şekilde kafa karıştırıcı olabilir:

* `BufferSize` bir soyutlama değil; tamsayı için yalnızca başka bir addır.
* `BufferSize` ortak bir API 'de sunulmazda, çok daha fazla `int`büyük bir şekilde yanlış yorumlanabilmektedir. Genellikle, etki alanı türlerinin kendileri için birden çok özniteliği vardır ve `int`gibi temel türler değildir. Bu kısaltma Bu varsayımını ihlal ediyor.
* `BufferSize` büyük küçük harf (PascalCase), bu türün daha fazla veri bulundurduğunu gösterir.
* Bu diğer ad, bir işleve adlandırılmış bir bağımsız değişken sağlamaya kıyasla daha fazla açıklık sunmaz.
* Kısaltma derlenmiş Il 'de bildirim içermez; yalnızca bir tamsayıdır ve bu diğer ad derleme zamanı yapısıdır.

```fsharp
module Networking =
    ...
    let send data (bufferSize: int) = ...
```

Özet olarak, tür kısaltmalarıyla birlikte, abbreviating oldukları türler üzerinde soyutlamalar **değildir** . Önceki örnekte `BufferSize`, hiçbir ek veri olmadan veya `int` zaten sahip olduğu gibi tür sisteminden herhangi bir avantajdan yalnızca bir `int`.

Bir etki alanını temsil etmek için tür kısaltmalarının kullanılmasına alternatif bir yaklaşım, tek büyük harf ayrılmış birleşimler kullanmaktır. Önceki örnek aşağıdaki gibi modellenebilir:

```fsharp
type BufferSize = BufferSize of int
```

`BufferSize` ve temel aldığı değer bakımından çalışan bir kod yazarsanız, herhangi bir rastgele tamsayı geçirmek yerine bir tane oluşturmanız gerekir:

```fsharp
module Networking =
    ...
    let send data (BufferSize size) =
    ...
```

Bu, çağıran işlevi çağırmak için bir değeri sarmadan önce bir `BufferSize` türü oluşturmasının gerektiğinden, yanlışlıkla rastgele bir tamsayıyı `send` işlevine geçirme olasılığını azaltır.
