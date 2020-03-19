---
title: F# kodlama kuralları
description: F# kodu yazarken genel yönergeleri ve deyimleri öğrenin.
ms.date: 01/15/2020
ms.openlocfilehash: 7266211e501bdb52564220781e2347d1aceaf296
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400311"
---
# <a name="f-coding-conventions"></a>F# kodlama kuralları

Aşağıdaki sözleşmeler, büyük F# kod tabanlarıyla çalışma deneyiminden formüle edilmiştir. [İyi F# kodunun beş ilkesi](index.md#five-principles-of-good-f-code) her tavsiyenin temelidir. Bunlar [F# bileşeni tasarım yönergeleri](component-design-guidelines.md)ile ilgilidir, ancak yalnızca kitaplıklar gibi bileşenler için değil, herhangi bir F# kodu için de geçerlidir.

## <a name="organizing-code"></a>Kodu düzenleme

F# kodu düzenlemenin iki birincil yolunu sunar: modüller ve ad alanları. Bunlar benzer, ancak aşağıdaki farklılıklar var:

* Ad alanları .NET ad alanları olarak derlenir. Modüller statik sınıflar olarak derlenmiştir.
* Ad boşlukları her zaman en üst düzeydir. Modüller üst düzey olabilir ve diğer modüller içinde iç içe.
* Ad alanları birden çok dosyaya yayılabilir. Modüller yapamaz.
* Modüller ile `[<RequireQualifiedAccess>]` dekore edilebilir `[<AutoOpen>]`ve .

Aşağıdaki yönergeler, kodunuzu düzenlemek için bunları kullanmanıza yardımcı olur.

### <a name="prefer-namespaces-at-the-top-level"></a>Ad alanlarını en üst düzeyde tercih edin

Genel olarak tüketilen herhangi bir kod için ad alanları en üst düzeydeki modüllere tercih edilir. .NET ad alanları olarak derlendiklerinden, C#'dan herhangi bir sorun olmadan tüketilebilirler.

```fsharp
// Good!
namespace MyCode

type MyClass() =
    ...
```

Üst düzey bir modül kullanmak yalnızca F#'dan çağrıldığında farklı görünmeyebilir, ancak C# `MyClass` tüketicileri `MyCode` için arayanlar modüle hak kazanmak zorunda kalarak şaşırabilirler.

```fsharp
// Bad!
module MyCode

type MyClass() =
    ...
```

### <a name="carefully-apply-autoopen"></a>Dikkatlice uygulayın`[<AutoOpen>]`

Yapı `[<AutoOpen>]` arayanlar için kullanılabilir ne kapsamı kirletebilir, ve bir şey nereden geldiğinin cevabı "sihirli". Bu iyi bir şey değil. Bu kuralın bir istisnası F# Core Library kendisi (bu gerçeği de biraz tartışmalı olmasına rağmen).

Ancak, genel BIR API için, bu genel API'den ayrı ayrı düzenlemek istediğiniz yardımcı işlevselliğiniz varsa, bu bir kolaylıktır.

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

Bu, her aradığınızda bir yardımcıyı tam olarak hak lamak zorunda kalmadan uygulama ayrıntılarını bir işlevin genel API'sinden temiz bir şekilde ayırmanızı sağlar.

Ayrıca, uzantı yöntemleri ve ifade oluşturucuları ad alanı düzeyinde ortaya `[<AutoOpen>]`çıkarmak düzgünce ifade edilebilir.

### <a name="use-requirequalifiedaccess-whenever-names-could-conflict-or-you-feel-it-helps-with-readability"></a>Adlar çakışabilir veya okunabilirlik ile yardımcı olduğunu hissediyorum zaman kullanın `[<RequireQualifiedAccess>]`

Bir `[<RequireQualifiedAccess>]` modüle öznitelik eklenmesi, modülün açılmayabileceğini ve modülün öğelerine yapılan başvuruların açık nitelikli erişim gerektirdiğini gösterir. Örneğin, `Microsoft.FSharp.Collections.List` modül bu özniteliğe sahiptir.

Bu, modüldeki işlevler ve değerler diğer modüllerde adlarla çakışma olasılığı olan adlara sahipse yararlıdır. Nitelikli erişim gerektiren büyük ölçüde uzun vadeli bakım ve bir kütüphane evolvability artırabilir.

```fsharp
[<RequireQualifiedAccess>]
module StringTokenization =
    let parse s = ...

...

let s = getAString()
let parsed = StringTokenization.parse s // Must qualify to use 'parse'
```

### <a name="sort-open-statements-topologically"></a>İfadeleri topolojik olarak sıralayın `open`

F#'da, bildirimlerin sırası, ifadeler `open` de dahil olmak üzere önemlidir. Bu, etkisinin `using` bir dosyadaki `using static` bu ifadelerin sıralanmasından bağımsız olduğu C#'dan farklı değildir.

F#'da, bir kapsama açılan öğeler zaten mevcut olan diğer öğeleri gölgeleyebilir. Bu, `open` ifadeleri yeniden sıralamanın kodun anlamını değiştirebileceği anlamına gelir. Sonuç olarak, beklediğiniz farklı davranışlar `open` oluşturmanız için tüm deyimlerin (örneğin, alfasayısal olarak) rasgele sıralanması önerilmez.

Bunun yerine, bunları [topolojik olarak](https://en.wikipedia.org/wiki/Topological_sorting)sıralamanızı öneririz; diğer bir deyişle, ekstrelerinizi `open` sisteminizin _katmanlarının_ tanımlandığı sırada sıralayın. Farklı topolojik tabakalar içinde alfanümerik sıralama yapmak da düşünülebilir.

Örnek olarak, F# derleyici hizmeti genel API dosyası için topolojik sıralama aşağıda verilmiştir:

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

Bir çizgi sonu topolojik katmanları ayırır ve her katman daha sonra alfasayısal olarak sıralanır unutmayın. Bu, yanlışlıkla değerleri gölgelemeden kodu temiz bir şekilde düzenler.

## <a name="use-classes-to-contain-values-that-have-side-effects"></a>Yan etkileri olan değerleri içerecek şekilde sınıfları kullanma

Bir değerin başlatılmasının, bir bağlamı veritabanına veya başka bir uzak kaynağa anında algılama gibi yan etkileri olabileceği birçok kez vardır. Bu tür şeyleri bir modülde başlatmayı ve sonraki işlevlerde kullanmak caziptir:

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

Bu genellikle birkaç nedenden dolayı kötü bir fikirdir:

İlk olarak, uygulama yapılandırması ile `dep1` `dep2`codebase içine itilir ve . Bunu daha büyük kod tabanlarında korumak zordur.

İkinci olarak, statik olarak başlaltımılan veriler, bileşeninizin kendisi birden çok iş parçacığı kullanacaksa iş parçacığı güvenli olmayan değerleri içermemelidir. Bu açıkça tarafından `dep3`ihlal edilir.

Son olarak, modül başlatma tüm derleme birimi için statik bir oluşturucu içine derler. Bu modülde let-bound değer başlatmada herhangi bir hata oluşursa, uygulamanın tüm ömrü boyunca önbelleğe alınmış bir `TypeInitializationException` hata olarak kendini gösterir. Bu tanılamak zor olabilir. Genellikle hakkında neden deneyebilirsiniz bir iç özel durum vardır, ancak yoksa, o zaman kök neden ne olduğunu söylemek yoktur.

Bunun yerine, bağımlılıkları tutmak için basit bir sınıf kullanmanız salt

```fsharp
type MyParametricApi(dep1, dep2, dep3) =
    member _.Function1 arg1 = doStuffWith dep1 dep2 dep3 arg1
    member _.Function2 arg2 = doStuffWith dep1 dep2 dep3 arg2
```

Bu, aşağıdakileri sağlar:

1. Herhangi bir bağımlı durumu API'nin kendisi dışında itme.
2. Yapılandırma artık API dışında yapılabilir.
3. Bağımlı değerler için başlatma hataları bir `TypeInitializationException`.
4. API'yi test etmek artık daha kolay.

## <a name="error-management"></a>Hata yönetimi

Büyük sistemlerde hata yönetimi karmaşık ve nüanslı bir çabadır ve sistemlerinizin hataya dayanıklı olmasını ve iyi çalışmasını sağlamada gümüş madde işaretleri yoktur. Aşağıdaki yönergeler bu zor alanda gezinme konusunda rehberlik sunmalıdır.

### <a name="represent-error-cases-and-illegal-state-in-types-intrinsic-to-your-domain"></a>Etki alanınızın içsel türlerinde hata durumlarını ve yasa dışı durumu temsil etme

[Ayrımcı Birlikler](../language-reference/discriminated-unions.md)ile F#, türü sisteminizde hatalı program durumunu temsil etme olanağı sağlar. Örnek:

```fsharp
type MoneyWithdrawalResult =
    | Success of amount:decimal
    | InsufficientFunds of balance:decimal
    | CardExpired of DateTime
    | UndisclosedFailure
```

Bu durumda, bir banka hesabından para çekmenin başarısız olabileceği bilinen üç yol vardır. Her hata örneği türde temsil edilir ve böylece program boyunca güvenli bir şekilde ele alınabilir.

```fsharp
let handleWithdrawal amount =
    let w = withdrawMoney amount
    match w with
    | Success am -> printfn "Successfully withdrew %f" am
    | InsufficientFunds balance -> printfn "Failed: balance is %f" balance
    | CardExpired expiredDate -> printfn "Failed: card expired on %O" expiredDate
    | UndisclosedFailure -> printfn "Failed: unknown"
```

Genel olarak, bir şey etki alanınızda **başarısız** olabilir farklı şekillerde modelleyebilir, o zaman hata işleme kodu artık düzenli program akışına ek olarak uğraşmak zorunda bir şey olarak kabul edilir. Bu sadece normal program akışının bir parçasıdır ve **istisnai**olarak kabul edilmez. Bunun iki temel faydası vardır:

1. Etki alanınız zaman içinde değiştikçe bakımı daha kolaydır.
2. Hata durumlarını birleştirmek daha kolaydır.

### <a name="use-exceptions-when-errors-cannot-be-represented-with-types"></a>Hatalar türleri ile temsil edilemiyorsa özel durumlar kullanma

Tüm hatalar sorunlu bir etki alanında temsil edilemez. Bu tür hatalar doğada *istisnaidir,* bu nedenle F#'daki istisnaları yükseltme ve yakalama yeteneği.

İlk olarak, Özel Durum [Tasarım Yönergeleri'ni](../../standard/design-guidelines/exceptions.md)okumanız önerilir. Bunlar F# için de geçerlidir.

Özel durumları yükseltmek amacıyla F#'da bulunan ana yapılar aşağıdaki tercih sırasına göre ele alınmalıdır:

| İşlev | Sözdizimi | Amaç |
|----------|--------|---------|
| `nullArg` | `nullArg "argumentName"` | Belirtilen `System.ArgumentNullException` bağımsız değişken adı ile bir yükseltir. |
| `invalidArg` | `invalidArg "argumentName" "message"` | Belirli `System.ArgumentException` bir bağımsız değişken adı ve iletisi ile bir yükseltir. |
| `invalidOp` | `invalidOp "message"` | Belirtilen `System.InvalidOperationException` iletiyle bir yükseltir. |
|`raise`| `raise (ExceptionType("message"))` | Özel durumlar atmak için genel amaçlı mekanizma. |
| `failwith` | `failwith "message"` | Belirtilen `System.Exception` iletiyle bir yükseltir. |
| `failwithf` | `failwithf "format string" argForFormatString` | Biçim `System.Exception` dizesi ve girişleri tarafından belirlenen bir ileti ile yükseltir. |

Kullanın `nullArg` `invalidArg` , `invalidOp` ve atmak `ArgumentNullException`için `ArgumentException` `InvalidOperationException` mekanizma olarak , ve uygun olduğunda.

Belirli `failwith` `failwithf` bir özel durum değil, temel `Exception` türünü yükselttikleri için ve işlevlerden genellikle kaçınılmalıdır. [Özel Durum Tasarım Yönergeleri'ne](../../standard/design-guidelines/exceptions.md)göre, ne zaman yapabilirseniz daha özel özel durumlar yükseltmek istiyorsunuz.

### <a name="using-exception-handling-syntax"></a>Özel durum işleme sözdizimini kullanma

F# sözdizimi `try...with` aracılığıyla özel durum desenlerini destekler:

```fsharp
try
    tryGetFileContents()
with
| :? System.IO.FileNotFoundException as e -> // Do something with it here
| :? System.Security.SecurityException as e -> // Do something with it here
```

Kodu temiz tutmak istiyorsanız, desen eşleştirmesi ile bir özel durum karşısında gerçekleştirmek için işlevselliği uzlaştırmak biraz zor olabilir. Bunu işlemenin yollarından biri, bir hata örneğini çevreleyen işlevselliği özel bir özel durumla gruplandırmak için [etkin desenler](../language-reference/active-patterns.md) kullanmaktır. Örneğin, bir özel durum attığında, özel durum meta verilerine değerli bilgileri dahil eden bir API tüketiyor olabilirsiniz. Etkin Desen içinde yakalanan özel durum gövdesinde yararlı bir değer açma ve bu değeri döndürme bazı durumlarda yararlı olabilir.

### <a name="do-not-use-monadic-error-handling-to-replace-exceptions"></a>Özel durumları değiştirmek için monadik hata işleme kullanmayın

İstisnalar işlevsel programlamada biraz tabu olarak görülür. Gerçekten de, istisnalar saflığı ihlal, bu yüzden onları oldukça işlevsel değil dikkate almak güvenlidir. Ancak, bu kod çalışması gereken yerin gerçekliğini yok sayar ve çalışma zamanı hataları oluşabilir. Genel olarak, çoğu şey ne saf ne de toplam, tatsız sürprizler en aza indirmek için olduğu varsayımı üzerine kod yazın.

.NET çalışma zamanı ve diller arası ekosistemdeki alaka ve uygunlukları açısından İstisnaların aşağıdaki temel güçlü yanlarını/yönlerini göz önünde bulundurmak önemlidir:

1. Bunlar, bir sorunu hata ayıklarken çok yararlı olan ayrıntılı tanı bilgileri içerir.
2. Çalışma zamanı ve diğer .NET dilleri tarafından iyi anlaşılır.
3. Anlamsal etiklerinin bir alt kümesini özel olarak uygulayarak istisnalardan *kaçınmak* için yolundan çıkan kodla karşılaştırıldığında önemli bir kazan plakasını azaltabilirler.

Bu üçüncü nokta çok önemli. Önemsiz olmayan karmaşık işlemler için, özel durumları kullanmamak aşağıdaki gibi yapılarla başa çıkmaya neden olabilir:

```fsharp
Result<Result<MyType, string>, string list>
```

Hangi kolayca "dize-yazılı" hataları desen eşleşen gibi kırılgan kodyol açabilir:

```fsharp
let result = doStuff()
match result with
| Ok r -> ...
| Error e ->
    if e.Contains "Error string 1" then ...
    elif e.Contains "Error string 2" then ...
    else ... // Who knows?
```

Ayrıca, bir "güzel" türü döndürür "basit" bir işlev için arzu herhangi bir istisna yutmak için cazip olabilir:

```fsharp
// This is bad!
let tryReadAllText (path : string) =
    try System.IO.File.ReadAllText path |> Some
    with _ -> None
```

Ne `tryReadAllText` yazık ki, bir dosya sisteminde meydana gelebilecek sayısız şeye dayanarak çok sayıda özel durum atabilir ve bu kod, ortamınızda gerçekte neyin yanlış olabileceğine dair herhangi bir bilgiyi ortadan atar. Bu kodu bir sonuç türüyle değiştirirseniz, "dize yle yazılan" hata iletisini ayrıştırmaya geri dönersiniz:

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

Ayrıca, özel durum nesnesinin kendisini `Error` oluşturucuya yerleştirmek, sizi işlevyerine çağrı yerindeki özel durum türüyle düzgün bir şekilde ilgilenmeye zorlar. Bunu yapmak, bir API'yi arayan kişi olarak ele almak için oldukça eğlenceli olmayan denetlenmiş özel durumlar oluşturur.

Yukarıdaki örneklere iyi bir *alternatif, belirli* özel durumları yakalamak ve bu özel durum bağlamında anlamlı bir değer döndürmektir. `tryReadAllText` İşlevi aşağıdaki gibi değiştirirseniz, `None` daha anlamlıdır:

```fsharp
let tryReadAllTextIfPresent (path : string) =
    try System.IO.File.ReadAllText path |> Some
    with :? FileNotFoundException -> None
```

Tümlerini yakalama olarak çalışmak yerine, bu işlev artık bir dosya bulunamediğinde servis talebiyle düzgün bir şekilde işleyecek ve bu anlamı iadeye atayacaktır. Bu iade değeri, herhangi bir bağlamsal bilgi atmamadan veya arayanları kodun o noktasında alakalı olmayan bir durumla uğraşmaya zorlamazken, bu hata örneğine eşleyebilir.

İç `Result<'Success, 'Error>` içe geçmedikleri temel işlemler için uygundur ve F# isteğe bağlı türleri, bir şeyin *bir şeyi* veya hiçbir *şeyi*döndürebileceğini temsil etmek için idealdir. Ancak, özel durumların yerini almamaktadırlar ve özel durumları değiştirmek için kullanılmamalıdır. Bunun yerine, istisna ve hata yönetimi ilkesinin belirli yönlerini hedeflenen yollarla ele almak için akıllıca uygulanmalıdır.

## <a name="partial-application-and-point-free-programming"></a>Kısmi uygulama ve noktasız programlama

F# kısmi uygulamayı destekler ve böylece, noktasız bir tarzda programlamak için çeşitli yollar. Bu, bir modül içinde kod yeniden kullanımı veya bir şeyin uygulanması için yararlı olabilir, ancak kamuya açık bir şey değildir. Genel olarak, nokta-free programlama ve kendisi bir erdem değildir ve tarzı dalmış olmayan insanlar için önemli bir bilişsel engel ekleyebilirsiniz.

### <a name="do-not-use-partial-application-and-currying-in-public-apis"></a>Kamu API'lerinde kısmi uygulama ve köri kullanmayın

Küçük bir istisna dışında, kamu API'lerinde kısmi uygulama kullanımı tüketiciler için kafa karıştırıcı olabilir. Genellikle, `let`F# kodunda -bağlı **değerler, işlev değerleri**değil **değerlerdir.** Değerleri ve işlev değerlerini bir araya getirmek, özellikle işlevleri oluşturmak gibi `>>` işleçlerle birleştiğinde, biraz bilişsel ek yükü karşılığında az sayıda kod satırının kaydedilmesine neden olabilir.

### <a name="consider-the-tooling-implications-for-point-free-programming"></a>Noktasız programlama için araç lama sonuçlarını göz önünde bulundurun

Curried işlevleri kendi bağımsız değişkenleri etiketlemek yok. Bunun takımlama etkileri vardır. Aşağıdaki iki işlevi göz önünde bulundurun:

```fsharp
let func name age =
    printfn "My name is %s and I am %d years old!" name age

let funcWithApplication =
    printfn "My name is %s and I am %d years old!"
```

Her ikisi de `funcWithApplication` geçerli işlevler, ancak bir curried işlevidir. Bir editörde türlerinin üzerinde gezinirken şunları görürsünüz:

```fsharp
val func : name:string -> age:int -> unit

val funcWithApplication : (string -> int -> unit)
```

Arama sitesinde, Visual Studio gibi araç uçlarında, giriş türlerinin gerçekte `string` neyi `int` temsil ettiğini zedelemez.

Bu gibi `funcWithApplication` noktasız kodla karşılaşırsanız, genel olarak tüketilebilir, takım lamanın bağımsız değişkenler için anlamlı adlar alabilmeleri için tam bir genişletme yapmanız önerilir.

Ayrıca, noktasız kod hata ayıklama imkansız değilse, zor olabilir. Hata ayıklama araçları, yürütmenin ortasında ara `let` değerleri inceleyebilmeniz için adlara bağlı değerlere (örneğin, bağlamalar) dayanır. Kodunuzun denetlenecek değeri yoksa, hata ayıklamak için hiçbir şey yoktur. Gelecekte, hata ayıklama araçları bu değerleri daha önce yürütülmüş yollara göre sentezlemek için gelişebilir, ancak *olası* hata ayıklama işlevleri üzerine bahislerinizi hedge etmek iyi bir fikir değildir.

### <a name="consider-partial-application-as-a-technique-to-reduce-internal-boilerplate"></a>Kısmi uygulamayı iç kazan plakasını azaltmak için bir teknik olarak düşünün

Önceki noktanın aksine, kısmi uygulama bir uygulama nın içindeki kazan plakasını veya bir API'nin daha derin iç lerini azaltmak için harika bir araçtır. Daha karmaşık API'lerin uygulanmasını test eden birim için yararlı olabilir, burada kazan genellikle başa çıkmak için bir ağrıdır. Örneğin, aşağıdaki kod, böyle bir çerçeveye dışa bağımlılık yapmadan ve ilgili ısmarlama API'yi öğrenmek zorunda kalmadan, en alaycı çerçevelerin size verdiği şeyi nasıl başarabileceğinizi gösterir.

Örneğin, aşağıdaki çözüm topografyasını göz önünde bulundurun:

```
MySolution.sln
|_/ImplementationLogic.fsproj
|_/ImplementationLogic.Tests.fsproj
|_/API.fsproj
```

`ImplementationLogic.fsproj`gibi kod ortaya çıkarabilir:

```fsharp
module Transactions =
    let doTransaction txnContext txnType balance =
        ...

type Transactor(ctx, currentBalance) =
    member _.ExecuteTransaction(txnType) =
        Transactions.doTransaction ctx txtType currentBalance
        ...
```

Birim `Transactions.doTransaction` testi `ImplementationLogic.Tests.fsproj` kolaydır:

```fsharp
namespace TransactionsTestingUtil

open Transactions

module TransactionsTestable =
    let getTestableTransactionRoutine mockContext = Transactions.doTransaction mockContext
```

Alaycı bir `doTransaction` bağlam nesnesi ile kısmen uygulamak, her seferinde alay edilmiş bir bağlam oluşturmaya gerek kalmadan tüm birim testlerinizdeki işlevi aramanızı sağlar:

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

Bu teknik evrensel olarak tüm codebase uygulanmamalıdır, ancak karmaşık iç ve birim bu iç test için ortak azaltmak için iyi bir yoldur.

## <a name="access-control"></a>Erişim denetimi

F# ['nin .NET](../language-reference/access-control.md)çalışma zamanında bulunanlardan devralınan Access denetimi için birden çok seçeneği vardır. Bunlar sadece türleri için kullanılabilir değildir - işlevleri için de kullanabilirsiniz.

* Genel olarak`public` tüketilebilir olması gerekene kadar tür olmayanları ve üyeleri tercih edin. Bu aynı zamanda tüketicilerin çift ne en aza indirir.
* Tüm yardımcı işlevselliğini `private`korumak için çalışıyoruz.
* Çok sayıda `[<AutoOpen>]` olursa yardımcı işlevlerin özel bir modül üzerinde kullanımını düşünün.

## <a name="type-inference-and-generics"></a>Tür çıkarım ve jenerik

Tür çıkarım ları, çok fazla kazan plakası yazmaktan sizi kurtarabilir. Ve F# derleyicisi otomatik genelleme sizin tarafınızdan hemen hemen hiçbir ekstra çaba ile daha genel kod yazmanıza yardımcı olabilir. Ancak, bu özellikler evrensel olarak iyi değildir.

* Bağımsız değişken adlarını genel API'lerde açık türleri olan etiketlemeyi düşünün ve bunun için tür çıkarımına güvenmeyin.

    Bunun nedeni, derleyicideğil, API'nizin şeklini kontrol **altında** olması gerektiğidir. Derleyici sizin için türleri inferring iyi bir iş yapabilir, ancak dayandığı iç türleri değişti eğer API değişikliği şekli olması mümkündür. Bu ne istediğinizi olabilir, ama neredeyse kesinlikle aşağı tüketicilerin daha sonra uğraşmak zorunda kalacak bir kırılma API değişikliği neden olacaktır. Bunun yerine, genel API'nizin şeklini açıkça denetlerseniz, bu kesme değişikliklerini denetleyebilirsiniz. DDD açısından, bu bir Yolsuzlukla Mücadele katmanı olarak düşünülebilir.

* Genel bağımsız değişkenlerinize anlamlı bir ad vermeyi düşünün.

    Belirli bir etki alanına özgü olmayan gerçekten genel kod yazmadığınız sürece, anlamlı bir ad diğer programcıların çalıştıkları etki alanını anlamalarına yardımcı olabilir. Örneğin, belge veritabanıyla `'Document` etkileşim bağlamında adlandırılan bir tür parametresi, genel belge türlerinin çalıştığınız işlev veya üye tarafından kabul edilebilmiş olabileceğini daha net hale getirir.

* Genel tür parametrelerini PascalCase ile adlandırmayı düşünün.

    Bu .NET'te bir şeyler yapmanın genel yoludur, bu nedenle snake_case veya camelCase yerine PascalCase kullanmanız önerilir.

Son olarak, otomatik genelleme her zaman F # veya büyük bir codebase yeni insanlar için bir nimet değildir. Genel bileşenleri kullanarak bilişsel yükü vardır. Ayrıca, otomatik olarak genelleştirilmiş işlevler farklı giriş türleri ile kullanılmazsa (bu şekilde kullanılmak üzere tasarlanmıştır, o zaman onları zaman içinde genel olmak için gerçek bir yararı yoktur. Yazdığınız kodun gerçekten genel olmaktan fayda sağlanıncaya bilebilirsiniz.

## <a name="performance"></a>Performans

### <a name="prefer-structs-for-small-data-types"></a>Küçük veri türleri için yapıları tercih etme

Genellikle nesneleri ayırmayı önlediğinden, yapı ların (Değer Türleri olarak da adlandırılır) kullanılması, bazı kodlar için genellikle daha yüksek performansa neden olabilir. Ancak, yapı strütler her zaman bir "daha hızlı git" düğmesi değildir: bir yapıdaki verilerin boyutu 16 baytı aşıyorsa, verileri kopyalamak genellikle başvuru türünü kullanmaktan daha fazla CPU harcaması ile sonuçlanabilir.

Bir yapı kullanmanız gerekip gerekip gerekmeden karar vermek için aşağıdaki koşulları göz önünde bulundurun:

- Verilerinizin boyutu 16 bayt veya daha küçükse.
- Çalışan bir programda bu veri türlerinin çoğunun bellekte yerleşik olması olasıysa.

İlk koşul geçerliyse, genellikle bir yapı kullanmalısınız. Her ikisi de geçerliyse, hemen hemen her zaman bir yapı kullanmalısınız. Önceki koşulların geçerli olduğu bazı durumlar olabilir, ancak bir yapı kullanmak bir başvuru türünü kullanmaktan daha iyi veya daha kötü değildir, ancak nadir olma olasılığı yüksektir. Her zaman bu gibi değişiklikler yaparken ölçmek için önemlidir, rağmen, ve varsayım veya sezgi üzerinde faaliyet değil.

#### <a name="prefer-struct-tuples-when-grouping-small-value-types"></a>Küçük değer türlerini gruplandırmayaparken yapı tuples'ı tercih etme

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

Bu işlevleri [BenchmarkDotNet](https://benchmarkdotnet.org/)gibi istatistiksel bir kıyaslama aracıyla kıyasladığınızda, yapı tuples kullanan işlevin `runWithStructTuple` %40 daha hızlı çalıştığını ve bellek ayırmadığını göreceksiniz.

Ancak, bu sonuçlar her zaman kendi kodunuzda böyle olmayacaktır. Bir işlevi , `inline`başvuru tuples kullanan kod olarak işaretlerseniz bazı ek optimizasyonlar alabilir veya ayrılacak kod yalnızca uzak optimize edilebilir. Performans söz konusu olduğunda sonuçları her zaman ölçmeli ve asla varsayım adabına veya sezgilerine göre çalışmamalısınız.

#### <a name="prefer-struct-records-when-the-data-type-is-small"></a>Veri türü küçükolduğunda yapı kayıtlarını tercih etme

Daha önce açıklanan başparmak kuralı [f# kayıt türleri](../language-reference/records.md)için de geçerlidir. Bunları işleyen aşağıdaki veri türlerini ve işlevleri göz önünde bulundurun:

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

Bu önceki tuple koduna benzer, ancak bu kez örnek kayıtları ve astarlı bir iç işlevi kullanır.

Bu işlevleri [BenchmarkDotNet](https://benchmarkdotnet.org/)gibi istatistiksel bir kıyaslama aracıyla `processStructPoint` kıyasladığınızda, yaklaşık %60 daha hızlı çalıştığını ve yönetilen yığında hiçbir şey ayırmadığını görürsünüz.

#### <a name="prefer-struct-discriminated-unions-when-the-data-type-is-small"></a>Veri türü küçükolduğunda yapı ayrımcı birliş tercih

Yapı tuples ve kayıtları ile performans hakkında önceki gözlemler de [F # Ayrımcı Sendikalar](../language-reference/discriminated-unions.md)için tutar. Aşağıdaki kodu inceleyin:

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

Etki alanı modellemesi için bunun gibi tek harfli Ayrımcı Birlikler tanımlamak yaygındır. Bu işlevleri [BenchmarkDotNet](https://benchmarkdotnet.org/)gibi istatistiksel bir kıyaslama aracıyla `structReverseName` kıyasladığınızda, küçük `reverseName` dizeleri için yaklaşık% 25 daha hızlı çalışır bulacaksınız. Büyük dizeleri için, her ikisi de yaklaşık aynı gerçekleştirmek. Yani, bu durumda, her zaman bir yapı kullanmak tercih edilir. Daha önce de belirtildiği gibi, her zaman ölçmek ve varsayımlar veya sezgi üzerinde faaliyet yok.

Önceki örnek, bir yapı Nın Daha iyi performans verdiğini gösterse de, bir etki alanını modellerken daha büyük Ayrımcı Birlikler olması yaygındır. Daha fazla kopyalama söz konusu olabileceğinden, bu tür daha büyük veri türleri, üzerlerindeki işlemlere bağlı olarak yapı lıysa, iyi performans göstermeyebilir.

### <a name="functional-programming-and-mutation"></a>Fonksiyonel programlama ve mutasyon

F# değerleri varsayılan olarak değişmezdir, bu da belirli hata sınıflarından (özellikle eşzamanlılık ve paralellik içerenler) kaçınmanızı sağlar. Ancak, bazı durumlarda, yürütme süresi veya bellek ayırmaları optimal (hatta makul) verimlilik elde etmek için, iş bir süre en iyi devlet yerinde mutasyon kullanılarak uygulanabilir. Bu anahtar kelime ile F# ile `mutable` bir opt-in bazında mümkündür.

F# `mutable` kullanımı fonksiyonel saflık ile oran hissedebilirsiniz. Bu anlaşılabilir, ancak fonksiyonel saflık her yerde performans hedefleri ile oran olabilir. Bir uzlaşma, arayanların bir işlev dedikleri zaman ne olduğu yla ilgilenmemesi için mutasyonu kapsüllemektir. Bu, performans açısından kritik kod için mutasyon tabanlı bir uygulama üzerinde işlevsel bir arabirim yazmanızı sağlar.

#### <a name="wrap-mutable-code-in-immutable-interfaces"></a>Değişmez arabirimlerde mutable kodu kaydırma

Bir hedef olarak başvurusal saydamlık ile, performans açısından kritik işlevlerin mutable underbelly ortaya çıkarmaz kod yazmak önemlidir. Örneğin, aşağıdaki kod F# `Array.contains` çekirdek kitaplığında işlevi uygular:

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

Bu işlevi birden çok kez çağırmak, temel diziyi değiştirmez ve onu tüketire bağlı olarak herhangi bir değişken durumu korumanızı gerektirmez. İçindeki hemen hemen her kod satırı mutasyon kullansa da, referentially saydamdır.

#### <a name="consider-encapsulating-mutable-data-in-classes"></a>Sınıflarda sayılabilir verileri kapsüllemeyi düşünün

Önceki örnekte, mutable verileri kullanarak işlemleri kapsüllemek için tek bir işlev kullanılmıştır. Bu, daha karmaşık veri kümeleri için her zaman yeterli değildir. Aşağıdaki işlev kümelerini göz önünde bulundurun:

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

Bu kod performanttır, ancak arayanların korumaktan sorumlu olduğu mutasyon tabanlı veri yapısını ortaya çıkarır. Bu, altta yatan üyeleri olmayan bir sınıfın içine sarılmış olabilir:

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

`Closure1Table`altta yatan mutasyon tabanlı veri yapısını kapsüller, bu nedenle arayanlar altta yatan veri yapısını korumak için zorlamaz. Sınıflar, ayrıntıları arayanlara ifşa etmeden mutasyona dayalı verileri ve rutinleri kapsüllemek için güçlü bir yoldur.

#### <a name="prefer-let-mutable-to-reference-cells"></a>Hücrelere başvurmayı tercih edin `let mutable`

Başvuru hücreleri, başvuruyu değerin kendisi yerine bir değere temsil etmenin bir yoludur. Performans açısından kritik kod için kullanılabilseler de, önerilmezler. Aşağıdaki örneği inceleyin:

```fsharp
let kernels =
    let acc = ref Set.empty

    processWorkList startKernels (fun kernel ->
        if not ((!acc).Contains(kernel)) then
            acc := (!acc).Add(kernel)
        ...)

    !acc |> Seq.toList
```

Bir referans hücresinin kullanımı artık sonraki tüm kodları temel verileri dereference ve yeniden başvurmak zorunda "kirletır". Bunun yerine, düşünün: `let mutable`

```fsharp
let kernels =
    let mutable acc = Set.empty

    processWorkList startKernels (fun kernel ->
        if not (acc.Contains(kernel)) then
            acc <- acc.Add(kernel)
        ...)

    acc |> Seq.toList
```

Lambda ifadesinin ortasındaki tek mutasyon noktasının yanı sıra, dokunan diğer tüm kodlar `acc` bunu normal `let`bağlı değişmez bir değerin kullanımından farklı olmayan bir şekilde yapabilir. Bu, zaman içinde değişmeyi kolaylaştırır.

## <a name="object-programming"></a>Nesne programlama

F# nesneler ve nesne yönelimli (OO) kavramları için tam destek vardır. Birçok OO kavramı güçlü ve kullanışlı olmasına rağmen, bunların hepsi kullanmak için ideal değildir. Aşağıdaki listeler, yüksek düzeyde OO özellikleri kategorileri hakkında rehberlik sunar.

**Bu özellikleri birçok durumda kullanmayı düşünün:**

* Nokta gösterimi`x.Length`( )
* Örnek üyeler
* Örtük yapıcılar
* Statik üyeler
* Dizinleyici gösterimi (`arr.[x]`)
* Adlandırılmış ve İsteğe Bağlı bağımsız değişkenler
* Arayüzler ve arayüz uygulamaları

**Önce bu özelliklere ulaşmayın, ancak bir sorunu çözmek için uygun olduklarında bunları akıllıca uygulayın:**

* Yöntem aşırı yükleme
* Kapsüllenmiş mutable veriler
* Türler üzerinde operatörler
* Otomatik özellikler
* Uygulama `IDisposable` ve`IEnumerable`
* Tür uzantıları
* Olaylar
* Yapılar
* Temsilciler
* Numaralandırmalar

**Genellikle bunları kullanmanız gerekir sürece bu özellikleri kaçının:**

* Kalıtım tabanlı tür hiyerarşileri ve uygulama kalıtım
* Nulls ve`Unchecked.defaultof<_>`

### <a name="prefer-composition-over-inheritance"></a>Kalıtım yerine kompozisyonu tercih edin

[Devralma üzerindeki kompozisyon,](https://en.wikipedia.org/wiki/Composition_over_inheritance) iyi F# kodunun yapışabileceği uzun süreli bir deyimdir. Temel ilke, bir taban sınıf ve işlevsellik almak için bu taban sınıftan devralmak için arayanlar zorlamak olmamalıdır.

### <a name="use-object-expressions-to-implement-interfaces-if-you-dont-need-a-class"></a>Bir sınıfa ihtiyacınız yoksa arabirimleri uygulamak için nesne ifadelerini kullanma

[Nesne İfadeleri,](../language-reference/object-expressions.md) uygulanan arabirimi bir sınıfın içinde yapmaya gerek kalmadan bir değere bağlayarak arabirimleri anında uygulamanızı sağlar. Bu, özellikle _yalnızca_ arabirimi uygulamanız gerekiyorsa ve tam bir sınıfa ihtiyacınız yoksa kullanışlıdır.

Örneğin, [ionide'de](http://ionide.io/) bir kod düzeltme eylemi `open` sağlamak için çalıştırılan kod aşağıda verilmiştir:

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

Visual Studio Code API ile etkileşimde bulunmanız gerektiğinden, Nesne İfadeleri bunun için ideal bir araçtır. Bunlar, test rutinleri ile geçici bir şekilde bir arabirim saplamak istediğinizde, birim testi için de değerlidir.

## <a name="consider-type-abbreviations-to-shorten-signatures"></a>İmzaları kısaltmak için Tür Kısaltmalarını göz önünde bulundurun

[Tür kısaltmaları,](../language-reference/type-abbreviations.md) işlev imzası veya daha karmaşık bir tür gibi başka bir türe etiket atamanın kullanışlı bir yoludur. Örneğin, aşağıdaki diğer ad, derin bir öğrenme kitaplığı olan [CNTK](https://docs.microsoft.com/cognitive-toolkit/)ile bir hesaplama tanımlamak için gerekenlere bir etiket atar:

```fsharp
open CNTK

// DeviceDescriptor, Variable, and Function all come from CNTK
type Computation = DeviceDescriptor -> Variable -> Function
```

Ad, `Computation` diğer adla çalıştığı imzayla eşleşen herhangi bir işlevi belirtmek için kullanışlı bir yoldur. Bu gibi Tür Kısaltmalar kullanarak uygundur ve daha özlü kod sağlar.

### <a name="avoid-using-type-abbreviations-to-represent-your-domain"></a>Etki alanınızı temsil etmek için Tür Kısaltmalarını kullanmaktan kaçının

Tür Kısaltmaları işlev imzalarına ad vermek için uygun olsa da, diğer türleri kısaltırken kafa karıştırıcı olabilir. Bu kısaltmayı göz önünde bulundurun:

```fsharp
// Does not actually abstract integers.
type BufferSize = int
```

Bu, birden çok şekilde kafa karıştırıcı olabilir:

* `BufferSize`bir soyutlama değildir; bir tamsayı için sadece başka bir isimdir.
* `BufferSize` Genel bir API'de açıklanırsa, kolayca yanlış `int`yorumlanabilir. Genellikle, etki alanı türleri onlara birden çok öznitelikleri var ve gibi `int`ilkel türleri değildir. Bu kısaltma bu varsayımı ihlal eder.
* `BufferSize` (PascalCase) kasası, bu tür daha fazla veri tutar anlamına gelir.
* Bu diğer ad, bir işleve adlandırılmış bir bağımsız değişken sağlamayla karşılaştırıldığında daha fazla netlik sunmaz.
* Kısaltma derlenmiş IL'de tezahür etmeyecektir; sadece bir tamsayı ve bu takma ad bir derleme-zaman yapıdır.

```fsharp
module Networking =
    ...
    let send data (bufferSize: int) = ...
```

Özetle, Tür Kısaltmaları ile tuzak onlar kısaltma türleri üzerinde soyutlamalar **değildir.** Önceki örnekte, `BufferSize` sadece `int` bir kapakları altında, hiçbir ek veri ile, ne `int` de zaten ne yanında tip sisteminden herhangi bir yarar.

Bir etki alanını temsil etmek için tür kısaltmalarını kullanmaya alternatif bir yaklaşım, tek harfli ayrımcı birliş kullanmaktır. Önceki örnek aşağıdaki gibi modellenebilir:

```fsharp
type BufferSize = BufferSize of int
```

Temel değeri `BufferSize` ve açısından çalışan kod yazarsanız, rasgele bir tamsayı da geçmek yerine bir kod oluşturmanız gerekir:

```fsharp
module Networking =
    ...
    let send data (BufferSize size) =
    ...
```

Bu, `send` istemci işlevi aramadan önce bir değeri sarmak için bir `BufferSize` tür oluşturması gerektiğinden, yanlışlıkla işleve rasgele bir tamsayı geçirme olasılığını azaltır.
