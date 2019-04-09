---
title: F#kodlama kuralları
description: Genel yönergeler ve deyimleri yazılırken öğrenin F# kod.
ms.date: 05/14/2018
ms.openlocfilehash: 1ef016184180eb8d233295e8985903e07693ad26
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59186751"
---
# <a name="f-coding-conventions"></a>F#kodlama kuralları

Aşağıdaki kurallar ile büyük çalışma deneyiminden şeklide F# çıkabilirsiniz. [Beş iyi prensipleri F# kod](index.md#five-principles-of-good-f-code) önerilerin temelidir. İlişkili oldukları [ F# bileşen tasarım yönergeleri](component-design-guidelines.md), ancak için geçerli olan F# kod, kütüphane gibi değil yalnızca bileşenleri.

## <a name="organizing-code"></a>Kod düzenleme

F#kod düzenlemek için iki temel yol özellikleri: modüller ve ad alanları. Bunlar, benzer, ancak kıyasla aşağıdaki farklılıklar vardır:

* Ad alanları, .NET ad alanları derlenir. Modüller, statik sınıflar derlenir.
* Ad alanları, her zaman en üst düzey olur. Modüller, üst düzey ve diğer modüller içinde iç içe olabilir.
* Ad alanları, birden çok dosya yayılabilir. Modüller olamaz.
* Modüller düzenlenmiş ile `[<RequireQualifiedAccess>]` ve `[<AutoOpen>]`.

Aşağıdaki yönergeler, kodunuzu düzenleme şeklinizdir için bunları kullanın yardımcı olur.

### <a name="prefer-namespaces-at-the-top-level"></a>Ad alanları en üst düzeyde tercih et

Genel olarak kullanılabilir herhangi bir kod için ad alanları en üst düzeyde modüllerine tercihe bağlı. .NET ad alanları derlenmiş olduğundan, hiçbir sorun C# ' tan tüketilebilir.

```fsharp
// Good!
namespace MyCode

type MyClass() =
    ...
```

Üst düzey bir modül kullanarak görüntülenmeyebilir yalnızca çağrıldığında farklı F#, ancak C# Tüketiciler, Arayanların surprised nitelemek sağlayarak `MyClass` ile `MyCode` modülü.

```fsharp
// Bad!
module MyCode

type MyClass() =
    ...
```

### <a name="carefully-apply-autoopen"></a>Dikkatli bir şekilde uygulama `[<AutoOpen>]`

`[<AutoOpen>]` Yapısı arayanlara kullanılabilir kapsamını pollute ve burada bir şey geldiği için yanıt "Sihirli". Bu genellikle iyi bir şey değildir. Bu kuralın istisnası F# çekirdek kitaplığının kendisi (ancak bu durum ayrıca biraz tartışmalı).

Ancak, düzenlemek için ayrı olarak bu genel API istediğiniz genel API için yardımcı işlevini varsa bir kullanışlı olur.

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

Bu işlem, bir yardımcı her çağırdığında tam olarak nitelemek zorunda kalmadan indrebilirsiniz ayrı uygulama ayrıntılarından bir işlevin Genel API sağlar.

Ayrıca, uzantı yöntemleri ve ifade oluşturucular ad alanı düzeyinde gösterme düzgünce ile ifade edilebilen `[<AutoOpen>]`.

### <a name="use-requirequalifiedaccess-whenever-names-could-conflict-or-you-feel-it-helps-with-readability"></a>Kullanım `[<RequireQualifiedAccess>]` her adları çakışıyor ya da düşündüğünüzü ile okunabilirliği yardımcı olur

Ekleme `[<RequireQualifiedAccess>]` özniteliği bir modül için modülü açılamadı ve erişimi nitelenmiş modülünün öğelere başvurular açık gerektiğini gösterir. Örneğin, `Microsoft.FSharp.Collections.List` modülü, bu öznitelik içeriyor.

İşlevleri ve değerleri modüldeki diğer modüllerin adlarla çakışma olasılığı adlara sahip olduğunda bu kullanışlıdır. Koşullu erişim gerektiren bir kitaplığı geliştirilebilirlik ve uzun vadede sürdürülebilirliğini önemli ölçüde artırabilirsiniz.

```fsharp
[<RequireQualifiedAccess>]
module StringTokenization =
    let parse s = ...

...

let s = getAString()
let parsed = StringTokenization.parse s // Must qualify to use 'parse'
```

### <a name="sort-open-statements-topologically"></a>Sıralama `open` deyimleri topologically

İçinde F#, bildirimleri önemli olan konuya, dahil olmak üzere sırasını `open` deyimleri. Bu C#, burada etkisini `using` ve `using static` Bu deyimler bir dosyada sıralamasını bağımsızdır.

İçinde F#, bir kapsama açılır öğe zaten mevcut bir diğer gölge. Yani bu yeniden sıralama `open` deyimleri kod anlamını alter. Sonuç olarak, tüm sıralama her rastgele `open` deyimleri (örneğin, alfasayısal olarak) genellikle önerilmez, bekleyebileceğiniz farklı bir davranış oluşturmak ekleyin.

Bunun yerine, bunları sıralama öneririz [topologically](https://en.wikipedia.org/wiki/Topological_sorting); diğer bir deyişle, sipariş, `open` sırayı deyimlerinde _katmanları_ sisteminizi tanımlanır. Alfasayısal içindeki farklı topolojik katmanları sıralama yapmak da düşünülebilir.

Örneğin, işte topolojik sıralama için F# derleyici hizmeti ortak API dosyası:

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

Satır sonu alfasayısal olarak tüketmesi sıralanan her bir katman ile topolojik katmanları ayıran unutmayın. Bu düzgün bir şekilde kod değerleri gölgeleme olmadan yanlışlıkla düzenler.

## <a name="use-classes-to-contain-values-that-have-side-effects"></a>Yan etkisi olan değerler içermesini sınıflarını kullanma

Değer başlatma gibi bir bağlam için bir veritabanı veya başka bir uzak kaynağa örnekleme yan etkileri zaman olabilir birçok kez vardır. Modül içindeki gibi şeyler başlatıp sonraki işlevleri kullanmak için daha cazip bir:

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

Uygulama yapılandırması tabanının ilk olarak, şekilde gönderildiğinde `dep1` ve `dep2`. Bu, büyük kod tabanlarında elde etmek zordur.

İkinci, statik olarak başlatılmış veri bileşeniniz kendisini birden çok iş parçacığı kullanacaksanız, iş parçacığı güvenli olmayan bir değer içermemelidir. Bu açıkça tarafından ihlal `dep3`.

Son olarak, modül başlatma tüm derleme birimi için bir statik oluşturucuya derler. Let bağlı değer başlatma bu modüldeki herhangi bir hata oluşması halinde olarak bildirimleri bir `TypeInitializationException` , ardından önbelleğe alınma tüm uygulama ömrü boyunca. Bu tanı koymak güç olabilir. Genellikle bir iç özel durum hakkında neden girişiminde bulunabilirsiniz yoktur ancak ardından yoksa, hiçbir belirten kök nedeni nedir yok.

Bunun yerine, bağımlılıkları tutmak için yalnızca basit bir sınıfı kullanın:

```fsharp
type MyParametricApi(dep1, dep2, dep3) =
    member __.Function1 arg1 = doStuffWith dep1 dep2 dep3 arg1
    member __.Function2 arg2 = doStuffWith dep1 dep2 dep3 arg2
```

Bu aşağıdakileri sağlar:

1. API dışında herhangi bir bağımlı durumu İletiliyor.
2. Yapılandırma, artık API dışında yapılabilir.
3. Bağımlı değerleri için başlatma hataları olarak bildirim olasılığı olmayan bir `TypeInitializationException`.
4. API, artık test etmek daha kolay olur.

## <a name="error-management"></a>Hata Yönetimi

Hata Yönetimi sistemlerinde büyük olan karmaşık ve incelikli bir çaba ve sistemlerinizi sağlamak madde işaretleri de yapılandıran ve hataya dayanıklı hiçbir silver vardır. Aşağıdaki yönergeler bu zor alanı gezinme kılavuzluk sunmalıdır.

### <a name="represent-error-cases-and-illegal-state-in-types-intrinsic-to-your-domain"></a>Hata durumları ve etki alanınızı iç türleri geçersiz durumda temsil eder

İle [ayırt edici birleşimler](../language-reference/discriminated-unions.md), F# hatalı program durumunu temsil eden tür sisteminizdeki olanağı sağlar. Örneğin:

```fsharp
type MoneyWithdrawalResult =
    | Success of amount:decimal
    | InsufficientFunds of balance:decimal
    | CardExpired of DateTime
    | UndisclosedFailure
```

Bu durumda, bir banka hesaptan para geri alınmasının başarısız olabilir ve bilinen üç yolu vardır. Her bir hata durumu yazıyla gösterilir ve bu nedenle ile güvenli bir şekilde programın tamamında alınabilir.

```fsharp
let handleWithdrawal amount =
    let w = withdrawMoney amount
    match w with
    | Success am -> printfn "Successfully withdrew %f" am
    | InsufficientFunds balance -> printfn "Failed: balance is %f" balance
    | CardExpired expiredDate -> printfn "Failed: card expired on %O" expiredDate
    | UndisclosedFailure -> printfn "Failed: unknown"
```

Bu sorun genel olarak, farklı şekilde modelleyebilir, yapabilirsiniz **başarısız** etki alanınızda sonra hata işleme kodunu artık sorun, gereken işlem ile ek olarak normal program akışı olarak kabul edilir. Yalnızca normal program akışı bir parçasıdır ve dikkate alınmaz **olağanüstü**. Bu iki adet birincil avantaj vardır:

1. Etki alanınızı zamanla değiştikçe korumak daha kolaydır.
2. Hata durumları birim testine daha kolaydır.

### <a name="use-exceptions-when-errors-cannot-be-represented-with-types"></a>Hata türleri ile gösterilemez durumlarda özel durumları kullanın

Bir sorun etki alanındaki tüm hataları temsil edilebilir. Bu türde hataları *olağanüstü* yapısı, bu nedenle yükseltmek ve özel durumları yakalama olanağı F#.

İlk olarak, okumanızı önerilir [özel tasarım yönergeleri](../../standard/design-guidelines/exceptions.md). Bu da geçerli olan F#.

Ana bulunan yapıları F# özel durumlarını oluşturma amacıyla aşağıdaki tercih sırasına göre değerlendirilmesi için:

| İşlev | Sözdizimi | Amaç |
|----------|--------|---------|
| `nullArg` | `nullArg "argumentName"` | Oluşturur bir `System.ArgumentNullException` ile belirtilen bağımsız değişken adı. |
| `invalidArg` | `invalidArg "argumentName" "message"` | Oluşturur bir `System.ArgumentException` belirtilen bağımsız değişken adı ve ileti. |
| `invalidOp` | `invalidOp "message"` | Oluşturur bir `System.InvalidOperationException` belirtilen ileti. |
|`raise`| `raise (ExceptionType("message"))` | Özel durumları atma için genel amaçlı mekanizması. |
| `failwith` | `failwith "message"` | Oluşturur bir `System.Exception` belirtilen ileti. |
| `failwithf` | `failwithf "format string" argForFormatString` | Oluşturur bir `System.Exception` Biçim dizesinden veya girdilerinden tarafından belirlenen bir ileti ile. |

Kullanım `nullArg`, `invalidArg` ve `invalidOp` durum için bir mekanizma olarak `ArgumentNullException`, `ArgumentException` ve `InvalidOperationException` uygun olduğunda.

`failwith` Ve `failwithf` işlevleri, genellikle bunlar temel çünkü kaçınılmalıdır `Exception` türü, bir özel durum. Olarak başına [özel tasarım yönergeleri](../../standard/design-guidelines/exceptions.md), mümkün olduğunda daha belirli özel durumları yükseltmek istediğiniz.

### <a name="using-exception-handling-syntax"></a>Özel durum işleme sözdizimini kullanarak

F#özel durum desenleri aracılığıyla destekler `try...with` söz dizimi:

```fsharp
try
    tryGetFileContents()
with
| :? System.IO.FileNotFoundException as e -> // Do something with it here
| :? System.Security.SecurityException as e -> // Do something with it here
```

Bir özel durum desen eşleştirme ile karşılaşıldığında gerçekleştirmek için işlevleri karşılaştırma kodu temiz tutmak istiyorsanız biraz zor olabilir. Bu durumu çözmek için bir tür kullanmaktır [Etkin desenler](../language-reference/active-patterns.md) grubu işlev bir özel bir hata durumuyla çevreleyen yöntemi olarak. Örneğin, bir özel durum oluşturduğunda, özel durum meta verilerde değerli bilgiler kapsayan bir API kullanan. Yakalanan özel durumun etkin desen içinde gövdesinde yararlı bir değer çözülme ve döndürme değeri bazı durumlarda yararlı olabilir.

### <a name="do-not-use-monadic-error-handling-to-replace-exceptions"></a>Birli hata özel durum değiştirmek için işleme kullanmayın

Özel durumlar, biraz taboo işlevsel programlama olarak görülür. Aslında, sessiz değil işlevsel dikkate alınması gereken güvenli olacak şekilde özel durumları saflığa, ihlal ediyor. Ancak, bu kodu çalıştırdığı gerekir ve bu çalışma zamanı hataları oluşabilir gerçeklik yok sayar. Genel olarak, bilgilerin çoğunu saf ne sürprizlerden en aza indirmek için toplam varsayımına kod yazın.

Aşağıdaki çekirdek güçlü/yönlerini özel durumlar, ilgi düzeyi ve bir bütün olarak site .NET çalışma zamanı ve diller arası ekosistemi ile ilgili göz önünde bulundurmanız önemlidir:

1. Soruna hata ayıklanırken çok yararlı olan ayrıntılı tanılama bilgileri içerirler.
2. Bunlar, çalışma zamanı ve diğer .NET dilleri tarafından anlaşılır.
3. Bunlar giden yolu dışında bir kod ile karşılaştırıldığında önemli Demirbaş azaltabilir *önlemek* bir geçici olarak kendi semantiği bazı alt kümesi uygulayarak özel durumlar.

Bu üçüncü noktasını, kritik öneme sahiptir. Ölçeklenebilmesi kolay karmaşık işlemlerinde, özel durumlar kullanma başarısız yapıları şöyle uğraşmanızı neden olabilir:

```fsharp
Result<Result<MyType, string>, string list>
```

Hangi kolayca kırılgan kod hatalarını "yazılı stringly" desen gibi neden olabilir:

```fsharp
let result = doStuff()
match result with
| Ok r -> ...
| Error e ->
    if e.Contains "Error string 1" then ...
    elif e.Contains "Error string 2" then ...
    else ... // Who knows?
```

Ayrıca, gizliliğinizi korumayı taahhüt eder "daha Hoş görünmesi" türü döndüren "Basit" işlevi için herhangi bir özel swallow cazip olabilir:

```fsharp
// This is bad!
let tryReadAllText (path : string) =
    try System.IO.File.ReadAllText path |> Some
    with _ -> None
```

Ne yazık ki `tryReadAllText` çok sayıda dosya sisteminde oluşabilir şeyler dayalı çok sayıda özel durumlar oluşturabilecek ve bu kodu gerçekten yanlış ortamınızda neler hakkında bilgi hemen atar. Ardından bu kod bir sonuç türü değiştirirseniz, "yazılı stringly" hata iletisini geri ayrıştırma için duyuyoruz:

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

Ve özel durum nesnesi içinde `Error` Oluşturucusu yalnızca zorlar sizin için doğru çağrı sitesinde yerine işlev özel durum türüne sahip. Etkili bir şekilde bunu bir API'yi çağıran çalışılabilecek öğesinin unfun işaretli özel durum oluşturur.

Yukarıdaki örneklerde iyi bir alternatif yakalamaktır *belirli* özel durumlar ve o özel durumu bağlamında anlamlı bir değer döndürür. Değiştirirseniz `tryReadAllText` aşağıdaki gibi işlev `None` daha fazla anlamı vardır:

```fsharp
let tryReadAllTextIfPresent (path : string) =
    try System.IO.File.ReadAllText path |> Some
    with :? FileNotFoundException -> None
```

Bir dosya bulunamadı ve bu anlamı atamak için bir dönüş catch tümünü olarak çalışması için yerine, bu işlev artık düzgün şekilde çalışması işler. Bu dönüş değeri, bağlamsal bilgileri atılıyor veya bu noktada kod içinde ilgili olmayabilir bir servis talebi uğraşmanız çağıranlar zorlama sırasında bu hata çalışmasına eşleyebilirsiniz.

Gibi türleri `Result<'Success, 'Error>` nerede bunlar iç içe değil, temel işlemleri için uygun olan ve F# zamanı temsil eden bir şey olabilir ya da iade için isteğe bağlı türler mükemmel *bir şey* veya *hiçbirşey*. Bunlar özel durumlar yerine değil ve bir özel durum değiştirmek için kullanılmamalıdır. Bunun yerine, bunlar bozacağından adresi belirli yönlerini özel durum ve hata yönetimi ilkesi için hedeflenen şekilde uygulanmalıdır.

## <a name="partial-application-and-point-free-programming"></a>Kısmi uygulama ve programlama noktası-ücretsiz

F#Kısmi uygulama ve bu nedenle, program için çeşitli yollar noktası içermeyen bir stilde destekler. Bu modül veya bir şeyin uygulama içinde kodun yeniden yararlı olabilir, ancak genellikle genel olarak kullanıma sunmak için bir şey değildir. Genel olarak, noktası ücretsiz programlama içinde ve kendisinin bir virtue değil ve bilişsel ciddi bir engel stilde sarmalanmış şekilde olmayan kişiler için ekleyebilirsiniz.

### <a name="do-not-use-partial-application-and-currying-in-public-apis"></a>Kısmi uygulama ve genel API'ler currying kullanmayın

Az özel durumla ortak API'lerde kısmi uygulama kullanımını Tüketiciler için kafa karıştırıcı olabilir. Genellikle, `let`-bağlı değerleri F# kodu **değerleri**değil **işlev değerleri**. Değerleri ve işlev değerleri birlikte karıştırma sonuçlanabilir bilişsel ek yükü, olayın lisanslarınıza kod satırlarını az sayıda kaydedilirken gibi özellikle işleçleri ile birleştirildiğinde `>>` işlevleri oluşturmak için.

### <a name="consider-the-tooling-implications-for-point-free-programming"></a>Programlama noktası ücretsiz araçları etkilerini göz önünde bulundurun

Curried işlevleri kendi bir bağımsız değişken etiket değil. Bu etkileri araçlarına sahiptir. Aşağıdaki iki işlevi göz önünde bulundurun:

```fsharp
let func name age =
    printfn "My name is %s and I am %d years old!" name age

let funcWithApplication =
    printfn "My name is %s and I am %d years old!"
```

Her ikisi de geçerli işlevleri olan ancak `funcWithApplication` curried bir işlevdir. Bir düzenleyicide türleri üzerine geldiğinizde, şunu görürsünüz:

```fsharp
val func : name:string -> age:int -> unit

val funcWithApplication : (string -> int -> unit)
```

Çağıran sitede, Visual Studio gibi bir araç ipuçlarında, anlamlı bilgiler ne vermeyiz `string` ve `int` giriş türleri gerçekten temsil eder.

Kod noktası ücretsiz gibi karşılaşırsanız `funcWithApplication` , genel olarak kullanılabilir, bu araçları çekme yukarı bağımsız değişkenleri için anlamlı adlar devam bir tam η genişletme için yapmanız gerekenleri önerilir.

Ayrıca, kod noktası sorunsuz hata ayıklama, imkansız değilse zor olabilir. Hata ayıklama araçları kullanan adlarına bağlı değerleri (örneğin, `let` bağlamaları) yürütme aracılığıyla Ara değerleri midway inceleyebilmeniz. Kodunuzu incelemek için hiçbir değer olduğunda, hata ayıklamak için hiçbir şey yoktur. Gelecekte, hata ayıklama araçları evrim Geçiren kullanıp bu değerler daha önce yürütülen yollarına dayalı, ancak üzerinde kaynak yatırımlarınızın karşılığını hedge iyi bir fikir değil *olası* işlevleri hata ayıklama.

### <a name="consider-partial-application-as-a-technique-to-reduce-internal-boilerplate"></a>Kısmi uygulama yöntemi olarak iç karmaşıklığın azaltılmasına göz önünde bulundurun.

Önceki bir noktaya aksine, ortak bir uygulama ya da daha ayrıntılı bir API içyüzü içinde azaltmak için harika bir araç kısmi uygulamasıdır. Birim testi Demirbaş genellikle uğraşmanız bir sorun olduğu, daha karmaşık bir API uygulaması için yararlı olabilir. Örneğin, bu tür bir Framework'te dış bağımlılık yapmadan nasıl yapabileceğinizle aşağıdaki kodun gösterdiği en sahte hangi çerçeveleri, verin ve API bespoke ilgili öğrenmek zorunda.

Örneğin, aşağıdaki çözümü topografi göz önünde bulundurun:

```
MySolution.sln
|_/ImplementationLogic.fsproj
|_/ImplementationLogic.Tests.fsproj
|_/API.fsproj
```

`ImplementationLogic.fsproj` kod kullanıma sunma gibi:

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

Kısmen uygulama `doTransaction` işlevi tüm Birim testlerinizin her zaman sahte bir bağlam oluşturmak zorunda kalmadan çağırın ile sahte bir bağlam nesnesi sağlar:

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

Bu teknik tüm kod temelinizde yapılan Evrensel uygulanmamalıdır ancak karmaşık iç Ayrıntılar ve birim testi bu iç işlevleri için Demirbaş azaltmak için iyi bir yoludur.

## <a name="access-control"></a>Erişim denetimi

F#için birden çok seçenek vardır [erişim denetimi](../language-reference/access-control.md), .NET çalışma zamanı'nda kullanılabilir öğesinden devralınan. Bunlar yalnızca türleri için kullanılabilir değildir - bunları işlevleri için de kullanabilirsiniz.

* Tercih ettiğiniz olmayan`public` türler ve üyeler kadar genel olarak kullanılabilir olması gerekir. Bu, hangi tüketicilerin birkaç için de azaltır.
* Tüm yardımcı işlevini tutun `private`.
* Kullanımını göz önünde bulundurun `[<AutoOpen>]` çok sayıda vermediğinde yardımcı işlevleri, özel bir modül.

## <a name="type-inference-and-generics"></a>Tür çıkarımı ve genel türler

Tür çıkarımı, çok sayıda standart yazmasını kaydedebilirsiniz. Ve de otomatik Genelleştirme F# derleyici bulunmanıza neredeyse hiçbir ekstra çaba daha genel kod yazmanıza yardımcı olabilir. Ancak, bu özellikler Evrensel iyi değildir.

* Bağımsız değişken adları açık türlerinde ortak API'ler ile etiketleme göz önünde bulundurun ve bunun için tür çıkarımı güvenmeyin.

    Bunun nedeni olan **,** derleyici API'nizi şeklini denetiminde olması gerekir. Derleyici, türlerin çıkarımını yapma en iyi bir iş yapabilirse kullanır iç türleri değişip değişmediğini API değişikliğiniz şeklini olması mümkündür. Bu, istediğiniz olabilir, ancak neredeyse kesindir aşağı akış tüketicilere çalışılabilecek olacak bir API değişiklik neden. Bunun yerine, açıkça genel API'nizi şeklini denetlemek, en son değişikliklerin denetleyebilirsiniz. DDD bağlamında, bu, bir bozulma önleyici katman düşünülebilir.

* Genel, bağımsız değişkenleri için anlamlı bir ad vermeyi düşünün.

    Belirli bir etki alanına özgü değildir gerçekten genel kod yazıyorsanız sürece, anlamlı bir ad, çalışmakta olduğunuz etki alanı anlama diğer programcılar yardımcı olabilir. Örneğin, adlı bir tür parametresi `'Document` bir belge ile etkileşim kurmanın bağlamında veritabanı NET genel belge türü işlev veya birlikte çalıştığınız üyesi tarafından kabul edilebilen kolaylaştırır.

* Genel tür parametreleri ile PascalCase adlandırma göz önünde bulundurun.

    Bu, .NET, şeyler PascalCase yerine snake_case veya camelCase kullanmanız önerilir Bunu yapmak için genel yoludur.

Son olarak, otomatik Genelleştirme her zaman bir boon yeni olan kişiler değil F# veya büyük bir kod temelinde. Genel olarak bileşenleri kullanarak bilişsel yükü yoktur. Ayrıca, varsa, otomatik olarak genelleştirilmiş işlevleri farklı giriş türleri (sağlar, bu nedenle kullanılacak yönelikse tek başına) ile kullanılmaz sonra bunlara zamandaki o noktada genel olan gerçek hiçbir avantajı yoktur. Her zaman yazdığınız kodu gerçekten genel yüklenmesini Kurum için avantaj sağlayacaktır olmadığını göz önünde bulundurun.

## <a name="performance"></a>Performans

F#belirli sınıfları (özellikle bu ilgili eşzamanlılık ve paralellik) hataları önlemek izin veren varsayılan olarak, sabit değerlerdir. Ancak, bazı durumlarda, yürütme zamanı bellek ayırmaları ve en iyi (veya hatta makul) verimlilik elde etmek için bir yayılma iş en iyi durumu yerinde Mutasyon kullanarak uygulanabilir. Bu katılımı temeli ile de mümkündür F# ile `mutable` anahtar sözcüğü.

Ancak, kullanım `mutable` içinde F# at odds with işlevsel saflığa düşünüyor. Bu beklentileri saflığa için gelen ayarlarsanız ince [başvuru saydamlık](https://en.wikipedia.org/wiki/Referential_transparency). Başvuru saydamlık - saflığa değil - yazarken son hedefi olduğu F# işlevleri. Bu performans kritik kod için Mutasyon tabanlı bir uygulama üzerinde işlevsel bir arabirim yazmanıza olanak sağlar.

### <a name="wrap-mutable-code-in-immutable-interfaces"></a>Sabit arabirimler değişebilir kod Kaydır

Bir hedef olarak başvuru saydamlığı olan performans açısından kritik işlevler değişebilir underbelly kullanıma sunmuyor kod yazmak için önemlidir. Örneğin, aşağıdaki uygulayan kod `Array.contains` işlevi F# çekirdek kitaplığı:

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

Bu fonksiyonu çağıran birden çok kez temel alınan dizi değişmez ya da hangi herhangi bir kesilebilir durumu sürdürmenizi gerektirir. Her neredeyse içindeki kod satırı Mutasyon kullansa bile referentially saydam.

### <a name="consider-encapsulating-mutable-data-in-classes"></a>Değişebilir veri sınıflarında Kapsüllenen göz önünde bulundurun

Önceki örnekte, değişebilir veri kullanan işlemleri kapsüllemek için tek bir işlev kullanılır. Bu her zaman daha karmaşık veri kümeleri için yeterli değil. Aşağıdaki adımlardan birini işlevleri göz önünde bulundurun:

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

Bu kod, yüksek performanslı olmakla birlikte çağıranlar sorumlu olduğunuz Mutasyon tabanlı veri yapısını gösterir. Değiştirebileceğiniz temel alınan üye ile bir sınıf içinde sarmalanabilir:

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

`Closure1Table` temel alınan veri yapısı korumak için çağıranlar Zorlanmıyor böylece temel alınan Mutasyon tabanlı veri yapısı kapsüller. Sınıfları, veri ve ayrıntıları arayanlara sokmadan Mutasyon tabanlı yordamlarını kapsüllemek için güçlü bir yoludur.

### <a name="prefer-let-mutable-to-reference-cells"></a>Tercih ettiğiniz `let mutable` başvuru hücreleri

Başvuru hücreleri başvuru değeri yerine bir değeri temsil eden bir yoludur. Performans açısından kritik kod için kullanılabilir olsa da, genellikle önerilmez. Aşağıdaki örnek göz önünde bulundurun:

```fsharp
let kernels =
    let acc = ref Set.empty

    processWorkList startKernels (fun kernel ->
        if not ((!acc).Contains(kernel)) then
            acc := (!acc).Add(kernel)
        ...)

    !acc |> Seq.toList
```

Bir başvuru hücresi kullanımı artık "başvuru ve temel alınan verileri yeniden başvurmak zorunda olan tüm sonraki kod pollutes". Bunun yerine, göz önünde bulundurun `let mutable`:

```fsharp
let kernels =
    let mutable acc = Set.empty

    processWorkList startKernels (fun kernel ->
        if not (acc.Contains(kernel)) then
            acc <- acc.Add(kernel)
        ...)

    acc |> Seq.toList
```

Diğer tüm kod lambda ifadesi ortasında Mutasyon yanı sıra tek noktası dokunduğu `acc` normal kullanım için farklı bir şekilde bunu yapabilirsiniz `let`-bağlı sabit değer. Bu zaman içinde kolaylaştırır.

## <a name="object-programming"></a>Nesne programlama

F#nesneleri ve nesne yönelimli kavramları (Paylaşımlarınızda) için tam destek sunar. Birçok Paylaşımlarınızda kavramları güçlü ve kullanışlı olsa da, bunların hepsi kullanmak idealdir. Aşağıdaki listeler, yüksek bir düzeyde Paylaşımlarınızda özelliklerinin kategorileri hakkında rehberlik sunar.

**Çoğu durumda bu özellikleri kullanmaya göz önünde bulundurun:**

* Noktalı gösterim (`x.Length`)
* Örnek üyeleri
* Örtük Oluşturucu
* Statik üyeler
* Dizin Oluşturucu gösterimi (`arr.[x]`)
* Adlandırılmış ve isteğe bağlı bağımsız değişkenler
* Arabirimleri ve arabirim uygulamaları

**Bu özellikler için ilk ulaşmak yoktur, ancak bir sorunu çözmek uygun olmaları durumunda dikkatli uygulayabilirsiniz:**

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

### <a name="prefer-composition-over-inheritance"></a>Devralma bileşim tercih et

[Devralma üzerinden bileşim](https://en.wikipedia.org/wiki/Composition_over_inheritance) değindiği deyim bu kadar iyidir F# kod uyması için. Temel olmayan bir taban sınıfı ve gerekir işlevselliğine sahip olmak için o temel sınıftan devralınan çağrı yapanların zorlamak emin ilkesidir.

### <a name="use-object-expressions-to-implement-interfaces-if-you-dont-need-a-class"></a>Bir sınıf gerekmiyorsa arayüzleri uygulamak için Nesne ifadeleri kullanma

[Nesne ifadeleri](../language-reference/object-expressions.md) halindeyken arayüzleri uygulamak izin uygulanan arabirimin bir değere bir sınıf içinde bunu gerek kalmadan bağlama. Bu kullanışlı, özellikle de, _yalnızca_ arabirim uygular ve gerek tam bir sınıf olması gerekir.

Örneğin, içinde çalışan kod işte [Ionide](http://ionide.io/) sahip olmayan bir sembol eklediyseniz, bir kod düzeltme eylemi sağlamak için bir `open` deyimi için:

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

Bir sınıf için gerek olmadığından Visual Studio kod API'SİYLE etkileşim kurulurken nesne ifadeleri bu ideal bir araçlardır. Ayrıca birim testi, geçici bir şekilde test yordamları bir arabirimi kullanıma saplama istediğinizde için değerli.

## <a name="type-abbreviations"></a>Tür Kısaltmaları

[Tür kısaltmaları](../language-reference/type-abbreviations.md) işlev imzası veya daha karmaşık bir tür gibi başka bir tür için bir etiket atamak için kullanışlı bir yoludur. Örneğin, şu diğer ne olan hesaplamayı tanımlamak gerekli bir etiketi atar [CNTK](https://www.microsoft.com/en-us/cognitive-toolkit/), kapsamlı bir kitaplık öğrenme:

```fsharp
open CNTK

// DeviceDescriptor, Variable, and Function all come from CNTK
type Computation = DeviceDescriptor -> Variable -> Function
```

`Computation` Yumuşatma olduğu imzayla eşleşen herhangi bir işlev belirtmek için kullanışlı bir yol adıdır. Tür kısaltmaları şöyle kullanarak uygun olan ve daha Sözün kodunu sağlar.

### <a name="avoid-using-type-abbreviations-to-represent-your-domain"></a>Tür kısaltmaları etki alanınızı temsil etmek için kullanmaktan kaçının

Tür kısaltmaları işlevi imzalar için bir ad vermek için kullanışlı olsa da, bunlar diğer türleri kısaltma kafa karıştırıcı olabilir. Bu kısaltma göz önünde bulundurun:

```fsharp
// Does not actually abstract integers.
type BufferSize = int
```

Bu, birden çok yolla kafa karıştırıcı olabilir:

* `BufferSize` bir Özet değil; bir tamsayı yalnızca başka bir addır.
* Varsa `BufferSize` sunulan genel bir API'de, kolayca daha fazlasını auto'yu anlaşılabilir `int`. Genel olarak, etki alanı türleri onlara birden çok özniteliklere sahip ve gibi ilkel türleri `int`. Bu kısaltma bu varsayımı ihlal ediyor.
* Büyük küçük harfleri `BufferSize` (PascalCase), bu tür daha fazla veri bulunduran anlamına gelir.
* Bu diğer adı, adlandırılmış bir bağımsız değişken bir işleve sağlamaya göre artan netlik sunmaz.
* Kısaltması derlenmiş IL bildirilmez; bir tamsayı olduğu ve bu diğer adı, bir derleme zamanı yapıdır.

```fsharp
module Networking =
    ...
    let send data (bufferSize: int) =
        ...
```

Özet olarak, tür kısaltmaları ile durumu olduklarından emin olan **değil** kısaltma türleri üzerinden soyutlamalar. Önceki örnekte, `BufferSize` tıpkı bir `int` ek veri yok ya da herhangi bir avantaj yanı sıra ne tür sisteminden ile kapsar altında `int` zaten sahip.
