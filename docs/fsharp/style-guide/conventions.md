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
# <a name="f-coding-conventions"></a><span data-ttu-id="54b92-103">F# kodlama kuralları</span><span class="sxs-lookup"><span data-stu-id="54b92-103">F# coding conventions</span></span>

<span data-ttu-id="54b92-104">Aşağıdaki kurallar, büyük F# kod tabanlarında çalışma deneyiminden alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="54b92-104">The following conventions are formulated from experience working with large F# codebases.</span></span> <span data-ttu-id="54b92-105">[Beş iyi F# kod ilkeleri](index.md#five-principles-of-good-f-code) her bir önerinin temelidir.</span><span class="sxs-lookup"><span data-stu-id="54b92-105">The [Five principles of good F# code](index.md#five-principles-of-good-f-code) are the foundation of each recommendation.</span></span> <span data-ttu-id="54b92-106">Bunlar [ F# bileşen tasarım yönergeleriyle](component-design-guidelines.md)ilgilidir, ancak yalnızca kitaplıklar gibi bileşenler değil tüm F# kodlar için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="54b92-106">They are related to the [F# component design guidelines](component-design-guidelines.md), but are applicable for any F# code, not just components such as libraries.</span></span>

## <a name="organizing-code"></a><span data-ttu-id="54b92-107">Kodu düzenleme</span><span class="sxs-lookup"><span data-stu-id="54b92-107">Organizing code</span></span>

<span data-ttu-id="54b92-108">F#kodu düzenlemenin iki birincil yolunu sunar: modüller ve ad alanları.</span><span class="sxs-lookup"><span data-stu-id="54b92-108">F# features two primary ways to organize code: modules and namespaces.</span></span> <span data-ttu-id="54b92-109">Bunlar benzerdir, ancak aşağıdaki farklılıklara sahiptir:</span><span class="sxs-lookup"><span data-stu-id="54b92-109">These are similar, but do have the following differences:</span></span>

* <span data-ttu-id="54b92-110">Ad alanları .NET ad alanları olarak derlenir.</span><span class="sxs-lookup"><span data-stu-id="54b92-110">Namespaces are compiled as .NET namespaces.</span></span> <span data-ttu-id="54b92-111">Modüller statik sınıflar olarak derlenir.</span><span class="sxs-lookup"><span data-stu-id="54b92-111">Modules are compiled as static classes.</span></span>
* <span data-ttu-id="54b92-112">Ad alanları her zaman en üst düzeydir.</span><span class="sxs-lookup"><span data-stu-id="54b92-112">Namespaces are always top level.</span></span> <span data-ttu-id="54b92-113">Modüller en üst düzey ve diğer modüller içinde iç içe olabilir.</span><span class="sxs-lookup"><span data-stu-id="54b92-113">Modules can be top-level and nested within other modules.</span></span>
* <span data-ttu-id="54b92-114">Ad alanları birden çok dosyaya yayılabilir.</span><span class="sxs-lookup"><span data-stu-id="54b92-114">Namespaces can span multiple files.</span></span> <span data-ttu-id="54b92-115">Modüller.</span><span class="sxs-lookup"><span data-stu-id="54b92-115">Modules cannot.</span></span>
* <span data-ttu-id="54b92-116">Modüller `[<RequireQualifiedAccess>]` ve `[<AutoOpen>]`ile donatılmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="54b92-116">Modules can be decorated with `[<RequireQualifiedAccess>]` and `[<AutoOpen>]`.</span></span>

<span data-ttu-id="54b92-117">Aşağıdaki yönergeler kodunuzu düzenlemek için bunları kullanmanıza yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="54b92-117">The following guidelines will help you use these to organize your code.</span></span>

### <a name="prefer-namespaces-at-the-top-level"></a><span data-ttu-id="54b92-118">En üst düzeyde ad alanlarını tercih et</span><span class="sxs-lookup"><span data-stu-id="54b92-118">Prefer namespaces at the top level</span></span>

<span data-ttu-id="54b92-119">Genel kullanım düzeylerine sahip herhangi bir kod için, ad alanları en üst düzeydeki modüllerle tercihe göre yapılır.</span><span class="sxs-lookup"><span data-stu-id="54b92-119">For any publicly consumable code, namespaces are preferential to modules at the top level.</span></span> <span data-ttu-id="54b92-120">.NET ad alanları olarak derlendiğinden, bunlar sorun olmadan tüketilebilir C# .</span><span class="sxs-lookup"><span data-stu-id="54b92-120">Because they are compiled as .NET namespaces, they are consumable from C# with no issue.</span></span>

```fsharp
// Good!
namespace MyCode

type MyClass() =
    ...
```

<span data-ttu-id="54b92-121">En üst düzey bir modülün kullanılması yalnızca öğesinden F#çağrıldığında farklı görünmeyebilir, ancak Tüketicileriniz için C# ,`MyClass``MyCode`modülle nitelendirmek için arayanlar olabilir.</span><span class="sxs-lookup"><span data-stu-id="54b92-121">Using a top-level module may not appear different when called only from F#, but for C# consumers, callers may be surprised by having to qualify `MyClass` with the `MyCode` module.</span></span>

```fsharp
// Bad!
module MyCode

type MyClass() =
    ...
```

### <a name="carefully-apply-autoopen"></a><span data-ttu-id="54b92-122">`[<AutoOpen>]` dikkatle uygulayın</span><span class="sxs-lookup"><span data-stu-id="54b92-122">Carefully apply `[<AutoOpen>]`</span></span>

<span data-ttu-id="54b92-123">`[<AutoOpen>]` yapısı, çağıranlar için kullanılabilir olan kapsamı ve bir şeyin geldiği yanıtın "Magic" olduğunu pollute.</span><span class="sxs-lookup"><span data-stu-id="54b92-123">The `[<AutoOpen>]` construct can pollute the scope of what is available to callers, and the answer to where something comes from is "magic".</span></span> <span data-ttu-id="54b92-124">Bu genellikle iyi bir şeydir.</span><span class="sxs-lookup"><span data-stu-id="54b92-124">This is generally not a good thing.</span></span> <span data-ttu-id="54b92-125">Bu kural için bir özel durum, F# temel kitaplığın kendisidir (Bu olgu aynı zamanda bir bit controversıal).</span><span class="sxs-lookup"><span data-stu-id="54b92-125">An exception to this rule is the F# Core Library itself (though this fact is also a bit controversial).</span></span>

<span data-ttu-id="54b92-126">Ancak, bu genel API 'den ayrı olarak düzenlemek istediğiniz ortak API için yardımcı işlevselliğe sahipseniz kolaylık vardır.</span><span class="sxs-lookup"><span data-stu-id="54b92-126">However, it is a convenience if you have helper functionality for a public API that you wish to organize separately from that public API.</span></span>

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

<span data-ttu-id="54b92-127">Bu, her çağırdığınızda bir yardımcıyı tam olarak nitelendirmek zorunda kalmadan, bir işlevin ortak API 'sinden uygulama ayrıntılarını düzgün bir şekilde ayırmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="54b92-127">This lets you cleanly separate implementation details from the public API of a function without having to fully qualify a helper each time you call it.</span></span>

<span data-ttu-id="54b92-128">Ek olarak, ad alanı düzeyinde uzantı yöntemlerinin ve ifade oluşturucuların kullanıma sunulması, `[<AutoOpen>]`ile ifade edilebilir.</span><span class="sxs-lookup"><span data-stu-id="54b92-128">Additionally, exposing extension methods and expression builders at the namespace level can be neatly expressed with `[<AutoOpen>]`.</span></span>

### <a name="use-requirequalifiedaccess-whenever-names-could-conflict-or-you-feel-it-helps-with-readability"></a><span data-ttu-id="54b92-129">Adlar her çakışıyorsa `[<RequireQualifiedAccess>]` kullanın veya okunabilirlik ile yardımcı olduğunu düşünüyorsanız</span><span class="sxs-lookup"><span data-stu-id="54b92-129">Use `[<RequireQualifiedAccess>]` whenever names could conflict or you feel it helps with readability</span></span>

<span data-ttu-id="54b92-130">`[<RequireQualifiedAccess>]` özniteliğini bir modüle eklemek, modülün açılamayabilir ve modülün öğelerine yapılan başvuruların açık nitelikli erişim gerektirdiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="54b92-130">Adding the `[<RequireQualifiedAccess>]` attribute to a module indicates that the module may not be opened and that references to the elements of the module require explicit qualified access.</span></span> <span data-ttu-id="54b92-131">Örneğin, `Microsoft.FSharp.Collections.List` modülü bu özniteliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="54b92-131">For example, the `Microsoft.FSharp.Collections.List` module has this attribute.</span></span>

<span data-ttu-id="54b92-132">Bu, modüldeki işlevlerin ve değerlerin diğer modüllerdeki adlarla çakışabilecek adlara sahip olduğu durumlarda faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="54b92-132">This is useful when functions and values in the module have names that are likely to conflict with names in other modules.</span></span> <span data-ttu-id="54b92-133">Tam erişim gerektirmek, bir kitaplığın uzun süreli bakım ve gelişmesini büyük ölçüde artırabilir.</span><span class="sxs-lookup"><span data-stu-id="54b92-133">Requiring qualified access can greatly increase the long-term maintainability and evolvability of a library.</span></span>

```fsharp
[<RequireQualifiedAccess>]
module StringTokenization =
    let parse s = ...

...

let s = getAString()
let parsed = StringTokenization.parse s // Must qualify to use 'parse'
```

### <a name="sort-open-statements-topologically"></a><span data-ttu-id="54b92-134">Sıralama `open` deyimleri topologically</span><span class="sxs-lookup"><span data-stu-id="54b92-134">Sort `open` statements topologically</span></span>

<span data-ttu-id="54b92-135">İçinde F#, `open`deyimleriyle birlikte bildirimlerin önemli sırası.</span><span class="sxs-lookup"><span data-stu-id="54b92-135">In F#, the order of declarations matters, including with `open` statements.</span></span> <span data-ttu-id="54b92-136">Bu,`using`C#ve`using static`efektinin bir dosyadaki deyimlerin sıralarından bağımsız olduğu şekilde farklı olur.</span><span class="sxs-lookup"><span data-stu-id="54b92-136">This is unlike C#, where the effect of `using` and `using static` is independent of the ordering of those statements in a file.</span></span>

<span data-ttu-id="54b92-137">' F#De, bir kapsamda açılan öğeler, diğerlerinin zaten mevcut olduğu öğeleri gölgelendirebilir.</span><span class="sxs-lookup"><span data-stu-id="54b92-137">In F#, elements opened into a scope can shadow others already present.</span></span> <span data-ttu-id="54b92-138">Bu, yeniden sıralama `open` deyimlerinin kodun anlamını değiştirebilecek anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="54b92-138">This means that reordering `open` statements could alter the meaning of code.</span></span> <span data-ttu-id="54b92-139">Sonuç olarak, tüm `open` deyimlerinin (örneğin, alfasayısal) herhangi bir rastgele sıralanması genellikle önerilmez, en uzun zaman beklemeniz gerekebilecek farklı davranışlar oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="54b92-139">As a result, any arbitrary sorting of all `open` statements (for example, alphanumerically) is generally not recommended, lest you generate different behavior that you might expect.</span></span>

<span data-ttu-id="54b92-140">Bunun yerine, [topologically](https://en.wikipedia.org/wiki/Topological_sorting); diğer bir deyişle, `open` deyimlerinizi sisteminizin _katmanlarının_ tanımlandığı sırada sıralayın.</span><span class="sxs-lookup"><span data-stu-id="54b92-140">Instead, we recommend that you sort them [topologically](https://en.wikipedia.org/wiki/Topological_sorting); that is, order your `open` statements in the order in which _layers_ of your system are defined.</span></span> <span data-ttu-id="54b92-141">Farklı topolojik katmanlarda Alfasayısal sıralama yapmak de göz önünde bulundurulmayabilir.</span><span class="sxs-lookup"><span data-stu-id="54b92-141">Doing alphanumeric sorting within different topological layers may also be considered.</span></span>

<span data-ttu-id="54b92-142">Örnek olarak, F# derleyici HIZMETI ortak API dosyası için topik sıralama aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="54b92-142">As an example, here is the topological sorting for the F# compiler service public API file:</span></span>

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

<span data-ttu-id="54b92-143">Bir satır sonu, her katmana daha sonra alfasayısal olarak sıralanmakta olan topik katmanları ayırır.</span><span class="sxs-lookup"><span data-stu-id="54b92-143">Note that a line break separates topological layers, with each layer being sorted alphanumerically afterwards.</span></span> <span data-ttu-id="54b92-144">Bu, yanlışlıkla gölgeleme değerleri olmadan kodu düzgün bir şekilde düzenler.</span><span class="sxs-lookup"><span data-stu-id="54b92-144">This cleanly organizes code without accidentally shadowing values.</span></span>

## <a name="use-classes-to-contain-values-that-have-side-effects"></a><span data-ttu-id="54b92-145">Yan etkileri olan değerleri içermesi için sınıfları kullanma</span><span class="sxs-lookup"><span data-stu-id="54b92-145">Use classes to contain values that have side effects</span></span>

<span data-ttu-id="54b92-146">Bir değerin başlatılması, bir veritabanı veya başka bir uzak kaynak için bir bağlamı örneklendirirken birçok zaman olabilir.</span><span class="sxs-lookup"><span data-stu-id="54b92-146">There are many times when initializing a value can have side effects, such as instantiating a context to a database or other remote resource.</span></span> <span data-ttu-id="54b92-147">Bu tür şeyleri bir modülde başlatmak ve sonraki işlevlerde kullanmak önemlidir:</span><span class="sxs-lookup"><span data-stu-id="54b92-147">It is tempting to initialize such things in a module and use it in subsequent functions:</span></span>

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

<span data-ttu-id="54b92-148">Bu, birkaç nedenden dolayı çoğunlukla kötü bir fikir olabilir:</span><span class="sxs-lookup"><span data-stu-id="54b92-148">This is frequently a bad idea for a few reasons:</span></span>

<span data-ttu-id="54b92-149">İlk olarak, uygulama yapılandırması `dep1` ve `dep2`kod tabanına gönderilir.</span><span class="sxs-lookup"><span data-stu-id="54b92-149">First, application configuration is pushed into the codebase with `dep1` and `dep2`.</span></span> <span data-ttu-id="54b92-150">Daha büyük kod tabanlarında bakım yapmak zordur.</span><span class="sxs-lookup"><span data-stu-id="54b92-150">This is difficult to maintain in larger codebases.</span></span>

<span data-ttu-id="54b92-151">İkinci olarak, bileşen birden çok iş parçacığı kullanıyorsa, statik olarak başlatılan veriler iş parçacığı güvenli olmayan değerler içermemelidir.</span><span class="sxs-lookup"><span data-stu-id="54b92-151">Second, statically initialized data should not include values that are not thread safe if your component will itself use multiple threads.</span></span> <span data-ttu-id="54b92-152">Bu, `dep3`tarafından açıkça ihlal edilir.</span><span class="sxs-lookup"><span data-stu-id="54b92-152">This is clearly violated by `dep3`.</span></span>

<span data-ttu-id="54b92-153">Son olarak, modül başlatması tüm derleme birimi için statik bir oluşturucuya derlenir.</span><span class="sxs-lookup"><span data-stu-id="54b92-153">Finally, module initialization compiles into a static constructor for the entire compilation unit.</span></span> <span data-ttu-id="54b92-154">Bu modülde izin-bağlanan değer başlatma bölümünde herhangi bir hata oluşursa, uygulamanın kullanım ömrü boyunca önbelleğe alınmış bir `TypeInitializationException` olarak bildirim oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="54b92-154">If any error occurs in let-bound value initialization in that module, it manifests as a `TypeInitializationException` that is then cached for the entire lifetime of the application.</span></span> <span data-ttu-id="54b92-155">Bunu tanılamak zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="54b92-155">This can be difficult to diagnose.</span></span> <span data-ttu-id="54b92-156">Genellikle bunun nedenini deneyebilmeniz için bir iç özel durum vardır, ancak yoksa, kök nedenin ne olduğunu söylemez.</span><span class="sxs-lookup"><span data-stu-id="54b92-156">There is usually an inner exception that you can attempt to reason about, but if there is not, then there is no telling what the root cause is.</span></span>

<span data-ttu-id="54b92-157">Bunun yerine, bağımlılıkları tutmak için basit bir sınıf kullanmanız yeterlidir:</span><span class="sxs-lookup"><span data-stu-id="54b92-157">Instead, just use a simple class to hold dependencies:</span></span>

```fsharp
type MyParametricApi(dep1, dep2, dep3) =
    member __.Function1 arg1 = doStuffWith dep1 dep2 dep3 arg1
    member __.Function2 arg2 = doStuffWith dep1 dep2 dep3 arg2
```

<span data-ttu-id="54b92-158">Bu, şunları sunar:</span><span class="sxs-lookup"><span data-stu-id="54b92-158">This enables the following:</span></span>

1. <span data-ttu-id="54b92-159">Herhangi bir bağımlı durumu API 'nin dışında iletme.</span><span class="sxs-lookup"><span data-stu-id="54b92-159">Pushing any dependent state outside of the API itself.</span></span>
2. <span data-ttu-id="54b92-160">Yapılandırma artık API dışında yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="54b92-160">Configuration can now be done outside of the API.</span></span>
3. <span data-ttu-id="54b92-161">Bağımlı değerler için başlatma hatalarının büyük olasılıkla `TypeInitializationException`olarak bildirimine izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="54b92-161">Errors in initialization for dependent values are not likely to manifest as a `TypeInitializationException`.</span></span>
4. <span data-ttu-id="54b92-162">API artık test etmek daha kolay.</span><span class="sxs-lookup"><span data-stu-id="54b92-162">The API is now easier to test.</span></span>

## <a name="error-management"></a><span data-ttu-id="54b92-163">Hata yönetimi</span><span class="sxs-lookup"><span data-stu-id="54b92-163">Error management</span></span>

<span data-ttu-id="54b92-164">Büyük sistemlerde hata yönetimi karmaşık ve anormal bir Endeavor ve sistemlerinizin hataya dayanıklı ve iyi davranmasını sağlamaya yönelik gümüş bir madde işareti yoktur.</span><span class="sxs-lookup"><span data-stu-id="54b92-164">Error management in large systems is a complex and nuanced endeavor, and there are no silver bullets in ensuring your systems are fault-tolerant and behave well.</span></span> <span data-ttu-id="54b92-165">Aşağıdaki kılavuzlar, bu zor alanda gezinmek için rehberlik sunmalıdır.</span><span class="sxs-lookup"><span data-stu-id="54b92-165">The following guidelines should offer guidance in navigating this difficult space.</span></span>

### <a name="represent-error-cases-and-illegal-state-in-types-intrinsic-to-your-domain"></a><span data-ttu-id="54b92-166">Etki alanınız için iç türlerde hata durumlarını ve geçersiz durumu temsil eder</span><span class="sxs-lookup"><span data-stu-id="54b92-166">Represent error cases and illegal state in types intrinsic to your domain</span></span>

<span data-ttu-id="54b92-167">[Ayrılmış birleşimler](../language-reference/discriminated-unions.md)sayesinde, F# tür sisteminizde hatalı program durumunu temsil etme olanağı sunar.</span><span class="sxs-lookup"><span data-stu-id="54b92-167">With [Discriminated Unions](../language-reference/discriminated-unions.md), F# gives you the ability to represent faulty program state in your type system.</span></span> <span data-ttu-id="54b92-168">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="54b92-168">For example:</span></span>

```fsharp
type MoneyWithdrawalResult =
    | Success of amount:decimal
    | InsufficientFunds of balance:decimal
    | CardExpired of DateTime
    | UndisclosedFailure
```

<span data-ttu-id="54b92-169">Bu durumda, bir banka hesabından paranın bir şekilde çizmesinin başarısız olması için üç bilinen yol vardır.</span><span class="sxs-lookup"><span data-stu-id="54b92-169">In this case, there are three known ways that withdrawing money from a bank account can fail.</span></span> <span data-ttu-id="54b92-170">Her bir hata durumu, türünde temsil edilir ve bu nedenle program genelinde güvenle ele alınabilir.</span><span class="sxs-lookup"><span data-stu-id="54b92-170">Each error case is represented in the type, and can thus be dealt with safely throughout the program.</span></span>

```fsharp
let handleWithdrawal amount =
    let w = withdrawMoney amount
    match w with
    | Success am -> printfn "Successfully withdrew %f" am
    | InsufficientFunds balance -> printfn "Failed: balance is %f" balance
    | CardExpired expiredDate -> printfn "Failed: card expired on %O" expiredDate
    | UndisclosedFailure -> printfn "Failed: unknown"
```

<span data-ttu-id="54b92-171">Genel olarak, etki alanındaki bir şeyin **başarısız olmasına** yönelik farklı yollar modelleyebilir, daha sonra hata işleme kodu artık normal program akışına ek olarak uğraşmanız gereken bir şey olarak değerlendirilmez.</span><span class="sxs-lookup"><span data-stu-id="54b92-171">In general, if you can model the different ways that something can **fail** in your domain, then error handling code is no longer treated as something you must deal with in addition to regular program flow.</span></span> <span data-ttu-id="54b92-172">Yalnızca normal program akışının bir parçasıdır ve **olağanüstü**olarak kabul edilmez.</span><span class="sxs-lookup"><span data-stu-id="54b92-172">It is simply a part of normal program flow, and not considered **exceptional**.</span></span> <span data-ttu-id="54b92-173">Bunun başlıca iki avantajı vardır:</span><span class="sxs-lookup"><span data-stu-id="54b92-173">There are two primary benefits to this:</span></span>

1. <span data-ttu-id="54b92-174">Etki alanınız zaman içinde değiştikçe bakım daha kolay olur.</span><span class="sxs-lookup"><span data-stu-id="54b92-174">It is easier to maintain as your domain changes over time.</span></span>
2. <span data-ttu-id="54b92-175">Hata durumlarının birim testi daha kolay.</span><span class="sxs-lookup"><span data-stu-id="54b92-175">Error cases are easier to unit test.</span></span>

### <a name="use-exceptions-when-errors-cannot-be-represented-with-types"></a><span data-ttu-id="54b92-176">Hatalar türlerle gösterilemeyeceği durumlarda özel durumlar kullanın</span><span class="sxs-lookup"><span data-stu-id="54b92-176">Use exceptions when errors cannot be represented with types</span></span>

<span data-ttu-id="54b92-177">Hatalar bir sorun etki alanında gösterilemez.</span><span class="sxs-lookup"><span data-stu-id="54b92-177">Not all errors can be represented in a problem domain.</span></span> <span data-ttu-id="54b92-178">Bu tür hataların doğası gereği *, bu* nedenle özel durumları ' de F#tetikleyebilme ve yakalayabilme özelliği vardır.</span><span class="sxs-lookup"><span data-stu-id="54b92-178">These kinds of faults are *exceptional* in nature, hence the ability to raise and catch exceptions in F#.</span></span>

<span data-ttu-id="54b92-179">İlk olarak, [özel durum tasarım kılavuzunu](../../standard/design-guidelines/exceptions.md)okumanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="54b92-179">First, it is recommended that you read the [Exception Design Guidelines](../../standard/design-guidelines/exceptions.md).</span></span> <span data-ttu-id="54b92-180">Bunlar için F#de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="54b92-180">These are also applicable to F#.</span></span>

<span data-ttu-id="54b92-181">Özel durumları oluşturma amaçları için F# ' de kullanılabilen ana yapılar, aşağıdaki tercih sırasına göre düşünülmelidir:</span><span class="sxs-lookup"><span data-stu-id="54b92-181">The main constructs available in F# for the purposes of raising exceptions should be considered in the following order of preference:</span></span>

| <span data-ttu-id="54b92-182">İşlev</span><span class="sxs-lookup"><span data-stu-id="54b92-182">Function</span></span> | <span data-ttu-id="54b92-183">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="54b92-183">Syntax</span></span> | <span data-ttu-id="54b92-184">Amaç</span><span class="sxs-lookup"><span data-stu-id="54b92-184">Purpose</span></span> |
|----------|--------|---------|
| `nullArg` | `nullArg "argumentName"` | <span data-ttu-id="54b92-185">Belirtilen bağımsız değişken adıyla bir `System.ArgumentNullException` oluşturur.</span><span class="sxs-lookup"><span data-stu-id="54b92-185">Raises a `System.ArgumentNullException` with the specified argument name.</span></span> |
| `invalidArg` | `invalidArg "argumentName" "message"` | <span data-ttu-id="54b92-186">Belirtilen bağımsız değişken adı ve iletisiyle bir `System.ArgumentException` oluşturur.</span><span class="sxs-lookup"><span data-stu-id="54b92-186">Raises a `System.ArgumentException` with a specified argument name and message.</span></span> |
| `invalidOp` | `invalidOp "message"` | <span data-ttu-id="54b92-187">Belirtilen iletiyle bir `System.InvalidOperationException` oluşturur.</span><span class="sxs-lookup"><span data-stu-id="54b92-187">Raises a `System.InvalidOperationException` with the specified message.</span></span> |
|`raise`| `raise (ExceptionType("message"))` | <span data-ttu-id="54b92-188">Özel durum oluşturmak için genel amaçlı mekanizma.</span><span class="sxs-lookup"><span data-stu-id="54b92-188">General-purpose mechanism for throwing exceptions.</span></span> |
| `failwith` | `failwith "message"` | <span data-ttu-id="54b92-189">Belirtilen iletiyle bir `System.Exception` oluşturur.</span><span class="sxs-lookup"><span data-stu-id="54b92-189">Raises a `System.Exception` with the specified message.</span></span> |
| `failwithf` | `failwithf "format string" argForFormatString` | <span data-ttu-id="54b92-190">Biçim dizesi ve girişleri tarafından belirlenen iletiyle bir `System.Exception` oluşturur.</span><span class="sxs-lookup"><span data-stu-id="54b92-190">Raises a `System.Exception` with a message determined by the format string and its inputs.</span></span> |

<span data-ttu-id="54b92-191">`nullArg`, `invalidArg` ve `invalidOp` uygun olduğunda `ArgumentNullException`, `ArgumentException` ve `InvalidOperationException` throw mekanizması olarak kullanın.</span><span class="sxs-lookup"><span data-stu-id="54b92-191">Use `nullArg`, `invalidArg` and `invalidOp` as the mechanism to throw `ArgumentNullException`, `ArgumentException` and `InvalidOperationException` when appropriate.</span></span>

<span data-ttu-id="54b92-192">`failwith` ve `failwithf` işlevleri, belirli bir özel durum değil, temel `Exception` türünü yükselttiğinden genellikle kaçınılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="54b92-192">The `failwith` and `failwithf` functions should generally be avoided because they raise the base `Exception` type, not a specific exception.</span></span> <span data-ttu-id="54b92-193">[Özel durum tasarım yönergelerine](../../standard/design-guidelines/exceptions.md)göre,, ' yi kullanırken daha özel özel durumlar da yapmak istersiniz.</span><span class="sxs-lookup"><span data-stu-id="54b92-193">As per the [Exception Design Guidelines](../../standard/design-guidelines/exceptions.md), you want to raise more specific exceptions when you can.</span></span>

### <a name="using-exception-handling-syntax"></a><span data-ttu-id="54b92-194">Özel durum işleme söz dizimini kullanma</span><span class="sxs-lookup"><span data-stu-id="54b92-194">Using exception-handling syntax</span></span>

<span data-ttu-id="54b92-195">F#`try...with`söz dizimi aracılığıyla özel durum desenlerini destekler:</span><span class="sxs-lookup"><span data-stu-id="54b92-195">F# supports exception patterns via the `try...with` syntax:</span></span>

```fsharp
try
    tryGetFileContents()
with
| :? System.IO.FileNotFoundException as e -> // Do something with it here
| :? System.Security.SecurityException as e -> // Do something with it here
```

<span data-ttu-id="54b92-196">Bir özel durumun açık olması için işlevselliği karşılaştırma, kod temizlemeyi sağlamak istiyorsanız biraz karmaşık olabilir.</span><span class="sxs-lookup"><span data-stu-id="54b92-196">Reconciling functionality to perform in the face of an exception with pattern matching can be a bit tricky if you wish to keep the code clean.</span></span> <span data-ttu-id="54b92-197">Bunu işlemenin bir yolu, [etkin desenleri](../language-reference/active-patterns.md) bir özel durum ile bir hata durumu çevreleyen işlevselliği gruplandırmak için bir yol olarak kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="54b92-197">One such way to handle this is to use [active patterns](../language-reference/active-patterns.md) as a means to group functionality surrounding an error case with an exception itself.</span></span> <span data-ttu-id="54b92-198">Örneğin, bir özel durum oluşturduğunda, önemli bilgileri özel durum meta verilerinde kapsayan bir API kullanıyor olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="54b92-198">For example, you may be consuming an API that, when it throws an exception, encloses valuable information in the exception metadata.</span></span> <span data-ttu-id="54b92-199">Etkin düzenin içindeki yakalanan özel durum gövdesinde yararlı bir değeri sarmalama ve bu değeri döndürme bazı durumlarda yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="54b92-199">Unwrapping a useful value in the body of the captured exception inside the Active Pattern and returning that value can be helpful in some situations.</span></span>

### <a name="do-not-use-monadic-error-handling-to-replace-exceptions"></a><span data-ttu-id="54b92-200">Özel durumları değiştirmek için monadıc hata işleme kullanmayın</span><span class="sxs-lookup"><span data-stu-id="54b92-200">Do not use monadic error handling to replace exceptions</span></span>

<span data-ttu-id="54b92-201">Özel durumlar fonksiyonel programlamada biraz Taboo olarak görülür.</span><span class="sxs-lookup"><span data-stu-id="54b92-201">Exceptions are seen as somewhat taboo in functional programming.</span></span> <span data-ttu-id="54b92-202">Aslında özel durumlar ihlal ediyor, bu nedenle bunları çok işlevli olarak düşünmek güvenlidir.</span><span class="sxs-lookup"><span data-stu-id="54b92-202">Indeed, exceptions violate purity, so it's safe to consider them not-quite functional.</span></span> <span data-ttu-id="54b92-203">Ancak, bu durum kodun çalışması gereken gerçekliği yoksayar ve çalışma zamanı hataları oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="54b92-203">However, this ignores the reality of where code must run, and that runtime errors can occur.</span></span> <span data-ttu-id="54b92-204">Genel olarak, önemli sürprleri en aza indirmek için çoğu şeyin saf veya toplam olmadığı varsayımına göre kod yazın.</span><span class="sxs-lookup"><span data-stu-id="54b92-204">In general, write code on the assumption that most things are neither pure nor total, to minimize unpleasant surprises.</span></span>

<span data-ttu-id="54b92-205">.NET çalışma zamanı ve çapraz dil ekosisteminde bir bütün olarak ilgi ve uygunluk açısından, özel durumların önem derecesine/yönlerini göz önünde bulundurmanız önemlidir.</span><span class="sxs-lookup"><span data-stu-id="54b92-205">It is important to consider the following core strengths/aspects of Exceptions with respect to their relevance and appropriateness in the .NET runtime and cross-language ecosystem as a whole:</span></span>

1. <span data-ttu-id="54b92-206">Bu kişiler, bir sorun ayıklanırken çok yararlı olan ayrıntılı tanılama bilgilerini içerirler.</span><span class="sxs-lookup"><span data-stu-id="54b92-206">They contain detailed diagnostic information, which is very helpful when debugging an issue.</span></span>
2. <span data-ttu-id="54b92-207">Çalışma zamanı ve diğer .NET dilleri tarafından iyi anlaşılabilirler.</span><span class="sxs-lookup"><span data-stu-id="54b92-207">They are well-understood by the runtime and other .NET languages.</span></span>
3. <span data-ttu-id="54b92-208">Bu kişiler, semantiğinin bazı alt kümelerini geçici olarak uygulayarak özel durumların *önüne* geçen kodla karşılaştırıldığında önemli ortak bir şekilde azalabilir.</span><span class="sxs-lookup"><span data-stu-id="54b92-208">They can reduce significant boilerplate when compared with code that goes out of its way to *avoid* exceptions by implementing some subset of their semantics on an ad-hoc basis.</span></span>

<span data-ttu-id="54b92-209">Bu üçüncü nokta kritiktir.</span><span class="sxs-lookup"><span data-stu-id="54b92-209">This third point is critical.</span></span> <span data-ttu-id="54b92-210">Önemsiz olmayan karmaşık işlemler için, özel durumları kullanmayan durumlar, şunun gibi yapılarla ilgileniyor:</span><span class="sxs-lookup"><span data-stu-id="54b92-210">For nontrivial complex operations, failing to use exceptions can result in dealing with structures like this:</span></span>

```fsharp
Result<Result<MyType, string>, string list>
```

<span data-ttu-id="54b92-211">Bu, "stringly-yazılan" hatalarda model eşleştirme gibi kırılmamış koda kolayca yol açabilir:</span><span class="sxs-lookup"><span data-stu-id="54b92-211">Which can easily lead to fragile code like pattern matching on "stringly-typed" errors:</span></span>

```fsharp
let result = doStuff()
match result with
| Ok r -> ...
| Error e ->
    if e.Contains "Error string 1" then ...
    elif e.Contains "Error string 2" then ...
    else ... // Who knows?
```

<span data-ttu-id="54b92-212">Ayrıca, "Nicer" türü döndüren bir "basit" işlevi için istenen özel duruma izin verebilir.</span><span class="sxs-lookup"><span data-stu-id="54b92-212">Additionally, it can be tempting to swallow any exception in the desire for a "simple" function that returns a "nicer" type:</span></span>

```fsharp
// This is bad!
let tryReadAllText (path : string) =
    try System.IO.File.ReadAllText path |> Some
    with _ -> None
```

<span data-ttu-id="54b92-213">Ne yazık ki `tryReadAllText`, bir dosya sisteminde gerçekleşebilecek nesnelerin sayısız temelinde çok sayıda özel durum oluşturabilir ve bu kod, ortamınızda gerçekten yanlış duruma gelmiş olabilecek bilgilerin hiçbirini atar.</span><span class="sxs-lookup"><span data-stu-id="54b92-213">Unfortunately, `tryReadAllText` can throw numerous exceptions based on the myriad of things that can happen on a file system, and this code discards away any information about what might actually be going wrong in your environment.</span></span> <span data-ttu-id="54b92-214">Bu kodu bir sonuç türüyle değiştirirseniz, "stringly-Typed" hata iletisi ayrıştırma ' ya geri dönebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="54b92-214">If you replace this code with a result type, then you're back to "stringly-typed" error message parsing:</span></span>

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

<span data-ttu-id="54b92-215">Ayrıca, özel durum nesnesinin kendisini `Error` oluşturucuya yerleştirmek yalnızca, işlev yerine çağrı sitesindeki özel durum türüyle doğru şekilde uğraşmaya zorlar.</span><span class="sxs-lookup"><span data-stu-id="54b92-215">And placing the exception object itself in the `Error` constructor just forces you to properly deal with the exception type at the call site rather than in the function.</span></span> <span data-ttu-id="54b92-216">Bunu etkin hale getirmek, bir API çağıranı olarak ele alınması için önemli ölçüde eğlenceli olmayan, denetlenen özel durumlar oluşturur.</span><span class="sxs-lookup"><span data-stu-id="54b92-216">Doing this effectively creates checked exceptions, which are notoriously unfun to deal with as a caller of an API.</span></span>

<span data-ttu-id="54b92-217">Yukarıdaki örneklere iyi bir alternatif, *belirli* özel durumları yakalamak ve bu özel durumun bağlamına anlamlı bir değer döndürmemelidir.</span><span class="sxs-lookup"><span data-stu-id="54b92-217">A good alternative to the above examples is to catch *specific* exceptions and return a meaningful value in the context of that exception.</span></span> <span data-ttu-id="54b92-218">`tryReadAllText` işlevini aşağıdaki şekilde değiştirirseniz, `None` daha fazla anlamı vardır:</span><span class="sxs-lookup"><span data-stu-id="54b92-218">If you modify the `tryReadAllText` function as follows, `None` has more meaning:</span></span>

```fsharp
let tryReadAllTextIfPresent (path : string) =
    try System.IO.File.ReadAllText path |> Some
    with :? FileNotFoundException -> None
```

<span data-ttu-id="54b92-219">Catch-all olarak çalışmak yerine, bu işlev artık bir dosya bulunamadığı ve bu anlamı bir return öğesine atayan durumu doğru şekilde işleymeyecektir.</span><span class="sxs-lookup"><span data-stu-id="54b92-219">Instead of functioning as a catch-all, this function will now properly handle the case when a file was not found and assign that meaning to a return.</span></span> <span data-ttu-id="54b92-220">Bu dönüş değeri bu hata durumuyla eşleşirken, herhangi bir bağlamsal bilgileri atmakla veya çağıranların koddaki bu noktada ilgisi olmayan bir servis talebiyle uğraşmak üzere zorlanmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="54b92-220">This return value can map to that error case, while not discarding any contextual information or forcing callers to deal with a case that may not be relevant at that point in the code.</span></span>

<span data-ttu-id="54b92-221">`Result<'Success, 'Error>` gibi türler, iç içe olmadıkları temel işlemler için uygundur ve F# isteğe bağlı türler *bir şeyi* veya *hiç*birini döndürene zaman dönebileceği göstermek için idealdir.</span><span class="sxs-lookup"><span data-stu-id="54b92-221">Types such as `Result<'Success, 'Error>` are appropriate for basic operations where they aren't nested, and F# optional types are perfect for representing when something could either return *something* or *nothing*.</span></span> <span data-ttu-id="54b92-222">Özel durumların yerini almaz, ancak özel durumları değiştirme girişiminde kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="54b92-222">They are not a replacement for exceptions, though, and should not be used in an attempt to replace exceptions.</span></span> <span data-ttu-id="54b92-223">Bunun yerine, özel durum ve hata yönetimi ilkesinin hedeflenen yollarla belirli yönlerini karşılamak için bozacağından uygulanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="54b92-223">Rather, they should be applied judiciously to address specific aspects of exception and error management policy in targeted ways.</span></span>

## <a name="partial-application-and-point-free-programming"></a><span data-ttu-id="54b92-224">Kısmi uygulama ve noktadan ücretsiz programlama</span><span class="sxs-lookup"><span data-stu-id="54b92-224">Partial application and point-free programming</span></span>

<span data-ttu-id="54b92-225">F#kısmi uygulamayı destekler ve bu nedenle, noktadan farklı stilde programlama için çeşitli yollar sunar.</span><span class="sxs-lookup"><span data-stu-id="54b92-225">F# supports partial application, and thus, various ways to program in a point-free style.</span></span> <span data-ttu-id="54b92-226">Bu, bir modül içindeki kod yeniden kullanımı veya bir şeyin uygulanması için yararlı olabilir, ancak genel olarak kullanıma sunulmayan bir şey değildir.</span><span class="sxs-lookup"><span data-stu-id="54b92-226">This can be beneficial for code reuse within a module or the implementation of something, but it is generally not something to expose publicly.</span></span> <span data-ttu-id="54b92-227">Genel olarak, ücretsiz programlama, ve içinde bir virtuale değildir ve stilde sarmalanmış olmayan kişiler için önemli bir bilişsel engel ekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="54b92-227">In general, point-free programming is not a virtue in and of itself, and can add a significant cognitive barrier for people who are not immersed in the style.</span></span>

### <a name="do-not-use-partial-application-and-currying-in-public-apis"></a><span data-ttu-id="54b92-228">Kısmi uygulama kullanmayın ve ortak API 'lerde currying kullanın</span><span class="sxs-lookup"><span data-stu-id="54b92-228">Do not use partial application and currying in public APIs</span></span>

<span data-ttu-id="54b92-229">Küçük bir özel durumla, genel API 'lerde kısmi uygulama kullanımı, tüketiciler için kafa karıştırıcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="54b92-229">With little exception, the use of partial application in public APIs can be confusing for consumers.</span></span> <span data-ttu-id="54b92-230">Genellikle, F# koddaki `let`bağlantılı değerler, **işlev değerleri**değil, **değerlerdir**.</span><span class="sxs-lookup"><span data-stu-id="54b92-230">Usually, `let`-bound values in F# code are **values**, not **function values**.</span></span> <span data-ttu-id="54b92-231">Değer ve işlev değerlerini bir araya getirmek, özellikle de işlevler oluşturmak için `>>` gibi işleçlerle birleştirildiğinde, çok sayıda bilişsel ek yük için Exchange 'de küçük miktarda kod satırı kaydedilmesine neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="54b92-231">Mixing together values and function values can result in saving a small number of lines of code in exchange for quite a bit of cognitive overhead, especially if combined with operators such as `>>` to compose functions.</span></span>

### <a name="consider-the-tooling-implications-for-point-free-programming"></a><span data-ttu-id="54b92-232">Noktadan noktaya ücretsiz programlama için araç etkilerini göz önünde bulundurun</span><span class="sxs-lookup"><span data-stu-id="54b92-232">Consider the tooling implications for point-free programming</span></span>

<span data-ttu-id="54b92-233">Curried işlevleri bağımsız değişkenlerini etiketetmez.</span><span class="sxs-lookup"><span data-stu-id="54b92-233">Curried functions do not label their arguments.</span></span> <span data-ttu-id="54b92-234">Bu, etkilerini olumsuz etkiler.</span><span class="sxs-lookup"><span data-stu-id="54b92-234">This has tooling implications.</span></span> <span data-ttu-id="54b92-235">Aşağıdaki iki işlevi göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="54b92-235">Consider the following two functions:</span></span>

```fsharp
let func name age =
    printfn "My name is %s and I am %d years old!" name age

let funcWithApplication =
    printfn "My name is %s and I am %d years old!"
```

<span data-ttu-id="54b92-236">Her ikisi de geçerli işlevlerdir, ancak `funcWithApplication` curried bir işlevdir.</span><span class="sxs-lookup"><span data-stu-id="54b92-236">Both are valid functions, but `funcWithApplication` is a curried function.</span></span> <span data-ttu-id="54b92-237">Bir düzenleyicide türlerin üzerine geldiğinizde şunu görürsünüz:</span><span class="sxs-lookup"><span data-stu-id="54b92-237">When you hover over their types in an editor, you see this:</span></span>

```fsharp
val func : name:string -> age:int -> unit

val funcWithApplication : (string -> int -> unit)
```

<span data-ttu-id="54b92-238">Çağrı sitesinde, Visual Studio gibi araç ipuçları, `string` ve `int` giriş türlerinin gerçekten temsil ettiği anlamlı bilgiler vermeyecektir.</span><span class="sxs-lookup"><span data-stu-id="54b92-238">At the call site, tooltips in tooling such as Visual Studio will not give you meaningful information as to what the `string` and `int` input types actually represent.</span></span>

<span data-ttu-id="54b92-239">Herkese açık şekilde tüketilebilir `funcWithApplication` gibi nokta içermeyen bir kodla karşılaşırsanız, araç, bağımsız değişkenlerin anlamlı adlarını görebilmesi için tam bir η genişletmesi yapmanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="54b92-239">If you encounter point-free code like `funcWithApplication` that is publicly consumable, it is recommended to do a full η-expansion so that tooling can pick up on meaningful names for arguments.</span></span>

<span data-ttu-id="54b92-240">Ayrıca, hata ayıklama noktası ücretsiz kod, mümkün değilse zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="54b92-240">Furthermore, debugging point-free code can be challenging, if not impossible.</span></span> <span data-ttu-id="54b92-241">Hata ayıklama araçları, adlara bağlı değerleri kullanır (örneğin, `let` bağlamaları) ve böylece ara değerleri, yürütme aracılığıyla bir şekilde inceleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="54b92-241">Debugging tools rely on values bound to names (for example, `let` bindings) so that you can inspect intermediate values midway through execution.</span></span> <span data-ttu-id="54b92-242">Kodunuzun incelenecek bir değeri olmadığında hata ayıklamanın bir şey yoktur.</span><span class="sxs-lookup"><span data-stu-id="54b92-242">When your code has no values to inspect, there is nothing to debug.</span></span> <span data-ttu-id="54b92-243">Gelecekte, hata ayıklama araçları, daha önce yürütülen yollara göre bu değerleri sentezleştirmek üzere gelişiyor, ancak sonuçlarınızı *olası* hata ayıklama işlevselliğine göre eklemek iyi bir fikir değildir.</span><span class="sxs-lookup"><span data-stu-id="54b92-243">In the future, debugging tools may evolve to synthesize these values based on previously executed paths, but it's not a good idea to hedge your bets on *potential* debugging functionality.</span></span>

### <a name="consider-partial-application-as-a-technique-to-reduce-internal-boilerplate"></a><span data-ttu-id="54b92-244">İç ortak uygulamayı azaltmak için kısmi uygulamayı bir teknik olarak düşünün</span><span class="sxs-lookup"><span data-stu-id="54b92-244">Consider partial application as a technique to reduce internal boilerplate</span></span>

<span data-ttu-id="54b92-245">Önceki noktanın aksine kısmi uygulama, bir uygulamanın içindeki demirbaş veya bir API 'nin daha derin iç içe geçmiş olması için harika bir araçtır.</span><span class="sxs-lookup"><span data-stu-id="54b92-245">In contrast to the previous point, partial application is a wonderful tool for reducing boilerplate inside of an application or the deeper internals of an API.</span></span> <span data-ttu-id="54b92-246">Daha karmaşık API 'lerin uygulanması yararlı olabilir; burada ortak, genellikle ilgileniyor bir sorun.</span><span class="sxs-lookup"><span data-stu-id="54b92-246">It can be helpful for unit testing the implementation of more complicated APIs, where boilerplate is often a pain to deal with.</span></span> <span data-ttu-id="54b92-247">Örneğin, aşağıdaki kod, en fazla bir çerçeve için bir dış bağımlılık almadan ve ilgili bir beste API öğrenmeye gerek kalmadan size en fazla ne kadar çok şey sağladığını nasıl gerçekleştirebileceğinizi göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="54b92-247">For example, the following code shows how you can accomplish what most mocking frameworks give you without taking an external dependency on such a framework and having to learn a related bespoke API.</span></span>

<span data-ttu-id="54b92-248">Örneğin, aşağıdaki çözüm topografisini göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="54b92-248">For example, consider the following solution topography:</span></span>

```
MySolution.sln
|_/ImplementationLogic.fsproj
|_/ImplementationLogic.Tests.fsproj
|_/API.fsproj
```

<span data-ttu-id="54b92-249">`ImplementationLogic.fsproj`, şu gibi bir kod açığa çıkabilir:</span><span class="sxs-lookup"><span data-stu-id="54b92-249">`ImplementationLogic.fsproj` might expose code such as:</span></span>

```fsharp
module Transactions =
    let doTransaction txnContext txnType balance =
        ...

type Transactor(ctx, currentBalance) =
    member __.ExecuteTransaction(txnType) =
        Transactions.doTransaction ctx txtType currentBalance
        ...
```

<span data-ttu-id="54b92-250">`ImplementationLogic.Tests.fsproj` birim testi `Transactions.doTransaction` kolaydır:</span><span class="sxs-lookup"><span data-stu-id="54b92-250">Unit testing `Transactions.doTransaction` in `ImplementationLogic.Tests.fsproj` is easy:</span></span>

```fsharp
namespace TransactionsTestingUtil

open Transactions

module TransactionsTestable =
    let getTestableTransactionRoutine mockContext = Transactions.doTransaction mockContext
```

<span data-ttu-id="54b92-251">Bir sahte işlem bağlam nesnesiyle `doTransaction` kısmen uygulamak, her seferinde bir moclenmiş bağlam oluşturulmasına gerek kalmadan, işlevi tüm birim testlerinizde çağırmanıza olanak sağlar:</span><span class="sxs-lookup"><span data-stu-id="54b92-251">Partially applying `doTransaction` with a mocking context object lets you call the function in all of your unit tests without needing to construct a mocked context each time:</span></span>

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

<span data-ttu-id="54b92-252">Bu teknik, tüm kod tabanınıza evrensel olarak uygulanmamalıdır, ancak karmaşık iç yapılar ve bu iç yapıları için ortak bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="54b92-252">This technique should not be universally applied to your entire codebase, but it is a good way to reduce boilerplate for complicated internals and unit testing those internals.</span></span>

## <a name="access-control"></a><span data-ttu-id="54b92-253">Erişim denetimi</span><span class="sxs-lookup"><span data-stu-id="54b92-253">Access control</span></span>

<span data-ttu-id="54b92-254">F#, .NET çalışma zamanında kullanılabilir olan öğeden devralınan [erişim denetimi](../language-reference/access-control.md)için birden çok seçeneğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="54b92-254">F# has multiple options for [Access control](../language-reference/access-control.md), inherited from what is available in the .NET runtime.</span></span> <span data-ttu-id="54b92-255">Bunlar yalnızca türler için kullanılamaz. bunları işlevler için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="54b92-255">These are not just usable for types - you can use them for functions, too.</span></span>

* <span data-ttu-id="54b92-256">`public` olmayan türleri ve üyeleri, herkese açık bir şekilde tüketilene kadar tercih edin.</span><span class="sxs-lookup"><span data-stu-id="54b92-256">Prefer non-`public` types and members until you need them to be publicly consumable.</span></span> <span data-ttu-id="54b92-257">Bu Ayrıca, hangi tüketicilerin için de en aza indirir.</span><span class="sxs-lookup"><span data-stu-id="54b92-257">This also minimizes what consumers couple to.</span></span>
* <span data-ttu-id="54b92-258">Tüm yardımcı işlevleri `private`tutmak için çaba harcar.</span><span class="sxs-lookup"><span data-stu-id="54b92-258">Strive to keep all helper functionality `private`.</span></span>
* <span data-ttu-id="54b92-259">Çok sayıda hale gelirse, yardım işlevlerinin özel modülünde `[<AutoOpen>]` kullanımını göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="54b92-259">Consider the use of `[<AutoOpen>]` on a private module of helper functions if they become numerous.</span></span>

## <a name="type-inference-and-generics"></a><span data-ttu-id="54b92-260">Tür çıkarımı ve genel türler</span><span class="sxs-lookup"><span data-stu-id="54b92-260">Type inference and generics</span></span>

<span data-ttu-id="54b92-261">Tür çıkarımı, çok sayıda demirbaş yazmanız için sizi kaydedebilir.</span><span class="sxs-lookup"><span data-stu-id="54b92-261">Type inference can save you from typing a lot of boilerplate.</span></span> <span data-ttu-id="54b92-262">Ve derleyicide otomatik Genelleştirme F# , sizin bölümlük üzerinde neredeyse hiç fazla çaba olmadan daha fazla genel kod yazmanıza yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="54b92-262">And automatic generalization in the F# compiler can help you write more generic code with almost no extra effort on your part.</span></span> <span data-ttu-id="54b92-263">Ancak, bu özellikler evrensel olarak iyi değildir.</span><span class="sxs-lookup"><span data-stu-id="54b92-263">However, these features are not universally good.</span></span>

* <span data-ttu-id="54b92-264">Bağımsız değişken adlarını ortak API 'lerde açık türlerle etiketlemeyi düşünün ve bunun için tür çıkarımı kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="54b92-264">Consider labeling argument names with explicit types in public APIs and do not rely on type inference for this.</span></span>

    <span data-ttu-id="54b92-265">Bunun nedeni, derleyicinin değil, API 'nizin şeklinin denetiminde **olması gerekir.**</span><span class="sxs-lookup"><span data-stu-id="54b92-265">The reason for this is that **you** should be in control of the shape of your API, not the compiler.</span></span> <span data-ttu-id="54b92-266">Derleyici, sizin için türler üzerinde ince bir iş yapabilse de, bağımlı olduğu iç işlem tür türleri değiştiyse API 'nizin şeklinin değiştirilmesi mümkündür.</span><span class="sxs-lookup"><span data-stu-id="54b92-266">Although the compiler can do a fine job at inferring types for you, it is possible to have the shape of your API change if the internals it relies on have changed types.</span></span> <span data-ttu-id="54b92-267">Bu, istediğiniz gibi olabilir, ancak aşağı akış tüketicilerinin daha sonra uğraşmak zorunda olacağı bir API değişikliğine neredeyse tamamen neden olur.</span><span class="sxs-lookup"><span data-stu-id="54b92-267">This may be what you want, but it will almost certainly result in a breaking API change that downstream consumers will then have to deal with.</span></span> <span data-ttu-id="54b92-268">Bunun yerine, ortak API 'nizin şeklini açıkça kontrol ediyorsanız, bu son değişiklikleri denetleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="54b92-268">Instead, if you explicitly control the shape of your public API, then you can control these breaking changes.</span></span> <span data-ttu-id="54b92-269">DDD terimlerinde, bu, bozulma önleyici bir katman olarak düşünülebilir.</span><span class="sxs-lookup"><span data-stu-id="54b92-269">In DDD terms, this can be thought of as an Anti-corruption layer.</span></span>

* <span data-ttu-id="54b92-270">Genel bağımsız değişkenlerinize anlamlı bir ad vermeyi düşünün.</span><span class="sxs-lookup"><span data-stu-id="54b92-270">Consider giving a meaningful name to your generic arguments.</span></span>

    <span data-ttu-id="54b92-271">Belirli bir etki alanına özgü olmayan gerçekten genel kod yazmadığınız takdirde anlamlı bir ad, diğer programcıların çalıştıkları etki alanını anlamasına yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="54b92-271">Unless you are writing truly generic code that is not specific to a particular domain, a meaningful name can help other programmers understanding the domain they're working in.</span></span> <span data-ttu-id="54b92-272">Örneğin, bir belge veritabanıyla etkileşim bağlamında `'Document` adlı bir tür parametresi, genel belge türlerinin, çalıştığınız işlev veya üye tarafından kabul edilebilir olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="54b92-272">For example, a type parameter named `'Document` in the context of interacting with a document database makes it clearer that generic document types can be accepted by the function or member you are working with.</span></span>

* <span data-ttu-id="54b92-273">Genel tür parametrelerini PascalCase ile adlandırmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="54b92-273">Consider naming generic type parameters with PascalCase.</span></span>

    <span data-ttu-id="54b92-274">Bu, .NET ' te şeyler yapmanın genel yoludur, bu nedenle snake_case veya camelCase yerine PascalCase kullanmanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="54b92-274">This is the general way to do things in .NET, so it's recommended that you use PascalCase rather than snake_case or camelCase.</span></span>

<span data-ttu-id="54b92-275">Son olarak, otomatik Genelleştirme her zaman için F# yeni olan veya büyük bir kod temeli olan kişiler için bir Boon değildir.</span><span class="sxs-lookup"><span data-stu-id="54b92-275">Finally, automatic generalization is not always a boon for people who are new to F# or a large codebase.</span></span> <span data-ttu-id="54b92-276">Genel olan bileşenleri kullanırken bilişsel ek yükü vardır.</span><span class="sxs-lookup"><span data-stu-id="54b92-276">There is cognitive overhead in using components that are generic.</span></span> <span data-ttu-id="54b92-277">Ayrıca, otomatik olarak Genelleştirilmiş işlevler farklı giriş türleriyle kullanılmazsa (Bu şekilde kullanılması amaçlanıyorsa tek başına izin ver), bu noktada bu noktada genel olan gerçek bir avantaj yoktur.</span><span class="sxs-lookup"><span data-stu-id="54b92-277">Furthermore, if automatically generalized functions are not used with different input types (let alone if they are intended to be used as such), then there is no real benefit to them being generic at that point in time.</span></span> <span data-ttu-id="54b92-278">Yazmakta olduğunuz kodun gerçekten genel olmasının yararlı olacağını her zaman göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="54b92-278">Always consider if the code you are writing will actually benefit from being generic.</span></span>

## <a name="performance"></a><span data-ttu-id="54b92-279">Performans</span><span class="sxs-lookup"><span data-stu-id="54b92-279">Performance</span></span>

<span data-ttu-id="54b92-280">F#değerler, bazı hata sınıflarından kaçınmanıza izin veren (özellikle eşzamanlılık ve paralellik olanlar) varsayılan olarak sabittir.</span><span class="sxs-lookup"><span data-stu-id="54b92-280">F# values are immutable by default, which allows you to avoid certain classes of bugs (especially those involving concurrency and parallelism).</span></span> <span data-ttu-id="54b92-281">Bununla birlikte, belirli durumlarda, yürütme süresi veya bellek ayırmaları için en iyi (veya hatta makul) verimlilik elde etmek üzere bir iş yayılımı en iyi duruma geçen durum ile uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="54b92-281">However, in certain cases, in order to achieve optimal (or even reasonable) efficiency of execution time or memory allocations, a span of work may best be implemented by using in-place mutation of state.</span></span> <span data-ttu-id="54b92-282">Bu,`mutable`anahtar sözcüğüyle birlikte F# kabul etme esasına göre yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="54b92-282">This is possible in an opt-in basis with F# with the `mutable` keyword.</span></span>

<span data-ttu-id="54b92-283">Bununla birlikte, ' de `mutable` F# kullanımı, işlev takiresinin gürültü 'de olabilir.</span><span class="sxs-lookup"><span data-stu-id="54b92-283">However, use of `mutable` in F# may feel at odds with functional purity.</span></span> <span data-ttu-id="54b92-284">Bu, önemli olan beklentileri [bilgi saydamlığına](https://en.wikipedia.org/wiki/Referential_transparency)ayarlarsanız bu kadar iyidir.</span><span class="sxs-lookup"><span data-stu-id="54b92-284">This is fine, if you adjust expectations from purity to [referential transparency](https://en.wikipedia.org/wiki/Referential_transparency).</span></span> <span data-ttu-id="54b92-285">Bilgi saydamlığı-önemli değildir; işlevler yazılırken F# son hedeftir.</span><span class="sxs-lookup"><span data-stu-id="54b92-285">Referential transparency - not purity - is the end goal when writing F# functions.</span></span> <span data-ttu-id="54b92-286">Bu, performans açısından kritik kod için bir mutasyon tabanlı uygulama üzerinde işlevsel bir arabirim yazmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="54b92-286">This allows you to write a functional interface over a mutation-based implementation for performance critical code.</span></span>

### <a name="wrap-mutable-code-in-immutable-interfaces"></a><span data-ttu-id="54b92-287">Değişmez arabirimlerde kesilebilir kodu sarın</span><span class="sxs-lookup"><span data-stu-id="54b92-287">Wrap mutable code in immutable interfaces</span></span>

<span data-ttu-id="54b92-288">Amaç olarak bilgi saydamlığı ile, performans açısından kritik işlevlerin değişebilir işlevlerini açığa çıkaran bir kod yazmak çok önemlidir.</span><span class="sxs-lookup"><span data-stu-id="54b92-288">With referential transparency as a goal, it is critical to write code that does not expose the mutable underbelly of performance-critical functions.</span></span> <span data-ttu-id="54b92-289">Örneğin, aşağıdaki kod F# çekirdek kitaplığındaki `Array.contains` işlevini uygular:</span><span class="sxs-lookup"><span data-stu-id="54b92-289">For example, the following code implements the `Array.contains` function in the F# core library:</span></span>

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

<span data-ttu-id="54b92-290">Bu işlevi birden çok kez çağırmak, temel alınan diziyi değiştirmez veya onu tükettiği herhangi bir kesilebilir durumu korumanıza gerek duyar.</span><span class="sxs-lookup"><span data-stu-id="54b92-290">Calling this function multiple times does not change the underlying array, nor does it require you to maintain any mutable state in consuming it.</span></span> <span data-ttu-id="54b92-291">Neredeyse her bir kod satırı mutation kullandığından bile, bu değer saydam bir şekilde görünür.</span><span class="sxs-lookup"><span data-stu-id="54b92-291">It is referentially transparent, even though almost every line of code within it uses mutation.</span></span>

### <a name="consider-encapsulating-mutable-data-in-classes"></a><span data-ttu-id="54b92-292">Sınıflarda kesilebilir verileri kapsüllemek için kullanın</span><span class="sxs-lookup"><span data-stu-id="54b92-292">Consider encapsulating mutable data in classes</span></span>

<span data-ttu-id="54b92-293">Önceki örnekte, değiştirilebilir verileri kullanarak işlemleri kapsüllemek için tek bir işlev kullanılmıştır.</span><span class="sxs-lookup"><span data-stu-id="54b92-293">The previous example used a single function to encapsulate operations using mutable data.</span></span> <span data-ttu-id="54b92-294">Bu, daha karmaşık veri kümeleri için her zaman yeterli değildir.</span><span class="sxs-lookup"><span data-stu-id="54b92-294">This is not always sufficient for more complex sets of data.</span></span> <span data-ttu-id="54b92-295">Aşağıdaki işlev kümelerini göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="54b92-295">Consider the following sets of functions:</span></span>

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

<span data-ttu-id="54b92-296">Bu kod performanyadır, ancak çağıranların korunmasından sorumlu olduğu mutasyon tabanlı veri yapısını kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="54b92-296">This code is performant, but it exposes the mutation-based data structure that callers are responsible for maintaining.</span></span> <span data-ttu-id="54b92-297">Bu, değiştireyebilecek temel üye olmadan bir sınıfın içine sarmalanabilir:</span><span class="sxs-lookup"><span data-stu-id="54b92-297">This can be wrapped inside of a class with no underlying members that can change:</span></span>

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

<span data-ttu-id="54b92-298">`Closure1Table` temel alınan mutasyon tabanlı veri yapısını kapsüller, böylece çağıranlar temel alınan veri yapısını sürdürmek üzere zorlar.</span><span class="sxs-lookup"><span data-stu-id="54b92-298">`Closure1Table` encapsulates the underlying mutation-based data structure, thereby not forcing callers to maintain the underlying data structure.</span></span> <span data-ttu-id="54b92-299">Sınıflar, çağıranların ayrıntılarını açığa çıkarmadan tabanlı verileri ve yordamları kapsüllemek için güçlü bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="54b92-299">Classes are a powerful way to encapsulate data and routines that are mutation-based without exposing the details to callers.</span></span>

### <a name="prefer-let-mutable-to-reference-cells"></a><span data-ttu-id="54b92-300">Hücrelere başvurmak için `let mutable` tercih et</span><span class="sxs-lookup"><span data-stu-id="54b92-300">Prefer `let mutable` to reference cells</span></span>

<span data-ttu-id="54b92-301">Başvuru hücreleri değerin kendisi yerine bir değere başvuruyu temsil etmenin bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="54b92-301">Reference cells are a way to represent the reference to a value rather than the value itself.</span></span> <span data-ttu-id="54b92-302">Performans açısından kritik kod için kullanılabilmesine rağmen, genellikle önerilmez.</span><span class="sxs-lookup"><span data-stu-id="54b92-302">Although they can be used for performance-critical code, they are generally not recommended.</span></span> <span data-ttu-id="54b92-303">Aşağıdaki örneği göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="54b92-303">Consider the following example:</span></span>

```fsharp
let kernels =
    let acc = ref Set.empty

    processWorkList startKernels (fun kernel ->
        if not ((!acc).Contains(kernel)) then
            acc := (!acc).Add(kernel)
        ...)

    !acc |> Seq.toList
```

<span data-ttu-id="54b92-304">Başvuru hücresinin kullanımı artık "pollutes", temel alınan verilere başvuru yapmak ve yeniden başvuru yapmak zorunda olan tüm izleyen koddur.</span><span class="sxs-lookup"><span data-stu-id="54b92-304">The use of a reference cell now "pollutes" all subsequent code with having to dereference and re-reference the underlying data.</span></span> <span data-ttu-id="54b92-305">Bunun yerine `let mutable`göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="54b92-305">Instead, consider `let mutable`:</span></span>

```fsharp
let kernels =
    let mutable acc = Set.empty

    processWorkList startKernels (fun kernel ->
        if not (acc.Contains(kernel)) then
            acc <- acc.Add(kernel)
        ...)

    acc |> Seq.toList
```

<span data-ttu-id="54b92-306">Lambda ifadesinin ortasında yer alan tek bir noktadan sonra, `acc` dokunduğu diğer tüm kodlar, normal `let`bağlantılı sabit değerin kullanılmasına göre değil, bunu yapabilir.</span><span class="sxs-lookup"><span data-stu-id="54b92-306">Aside from the single point of mutation in the middle of the lambda expression, all other code that touches `acc` can do so in a manner that is no different to the usage of a normal `let`-bound immutable value.</span></span> <span data-ttu-id="54b92-307">Bu, zaman içinde değişiklik yapmayı kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="54b92-307">This will make it easier to change over time.</span></span>

## <a name="object-programming"></a><span data-ttu-id="54b92-308">Nesne programlama</span><span class="sxs-lookup"><span data-stu-id="54b92-308">Object programming</span></span>

<span data-ttu-id="54b92-309">F#nesneler ve nesne yönelimli (OO) kavramları için tam desteğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="54b92-309">F# has full support for objects and object-oriented (OO) concepts.</span></span> <span data-ttu-id="54b92-310">Birçok OO kavramı güçlü ve yararlı olsa da, bunların hepsi kullanım için idealdir.</span><span class="sxs-lookup"><span data-stu-id="54b92-310">Although many OO concepts are powerful and useful, not all of them are ideal to use.</span></span> <span data-ttu-id="54b92-311">Aşağıdaki listeler, en yüksek düzeyde, OO özelliklerinin kategorileri üzerinde rehberlik sunar.</span><span class="sxs-lookup"><span data-stu-id="54b92-311">The following lists offer guidance on categories of OO features at a high level.</span></span>

<span data-ttu-id="54b92-312">**Bu özellikleri birçok durumda kullanmayı göz önünde bulundurun:**</span><span class="sxs-lookup"><span data-stu-id="54b92-312">**Consider using these features in many situations:**</span></span>

* <span data-ttu-id="54b92-313">Nokta gösterimi (`x.Length`)</span><span class="sxs-lookup"><span data-stu-id="54b92-313">Dot notation (`x.Length`)</span></span>
* <span data-ttu-id="54b92-314">Örnek üyeleri</span><span class="sxs-lookup"><span data-stu-id="54b92-314">Instance members</span></span>
* <span data-ttu-id="54b92-315">Örtük oluşturucular</span><span class="sxs-lookup"><span data-stu-id="54b92-315">Implicit constructors</span></span>
* <span data-ttu-id="54b92-316">Statik üyeler</span><span class="sxs-lookup"><span data-stu-id="54b92-316">Static members</span></span>
* <span data-ttu-id="54b92-317">Dizin Oluşturucu gösterimi (`arr.[x]`)</span><span class="sxs-lookup"><span data-stu-id="54b92-317">Indexer notation (`arr.[x]`)</span></span>
* <span data-ttu-id="54b92-318">Adlandırılmış ve Isteğe bağlı bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="54b92-318">Named and Optional arguments</span></span>
* <span data-ttu-id="54b92-319">Arabirimler ve arabirim uygulamaları</span><span class="sxs-lookup"><span data-stu-id="54b92-319">Interfaces and interface implementations</span></span>

<span data-ttu-id="54b92-320">**Önce bu özelliklere ulaşmayın, ancak bir sorunu çözmek için uygun olmaları durumunda bozacağından uygulayın:**</span><span class="sxs-lookup"><span data-stu-id="54b92-320">**Don't reach for these features first, but do judiciously apply them when they are convenient to solve a problem:**</span></span>

* <span data-ttu-id="54b92-321">Yöntem aşırı yüklemesi</span><span class="sxs-lookup"><span data-stu-id="54b92-321">Method overloading</span></span>
* <span data-ttu-id="54b92-322">Encapsulated kesilebilir veriler</span><span class="sxs-lookup"><span data-stu-id="54b92-322">Encapsulated mutable data</span></span>
* <span data-ttu-id="54b92-323">Türlerde işleçler</span><span class="sxs-lookup"><span data-stu-id="54b92-323">Operators on types</span></span>
* <span data-ttu-id="54b92-324">Otomatik Özellikler</span><span class="sxs-lookup"><span data-stu-id="54b92-324">Auto properties</span></span>
* <span data-ttu-id="54b92-325">`IDisposable` ve `IEnumerable` uygulama</span><span class="sxs-lookup"><span data-stu-id="54b92-325">Implementing `IDisposable` and `IEnumerable`</span></span>
* <span data-ttu-id="54b92-326">Tür uzantıları</span><span class="sxs-lookup"><span data-stu-id="54b92-326">Type extensions</span></span>
* <span data-ttu-id="54b92-327">Olaylar</span><span class="sxs-lookup"><span data-stu-id="54b92-327">Events</span></span>
* <span data-ttu-id="54b92-328">Yapılar</span><span class="sxs-lookup"><span data-stu-id="54b92-328">Structs</span></span>
* <span data-ttu-id="54b92-329">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="54b92-329">Delegates</span></span>
* <span data-ttu-id="54b92-330">Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="54b92-330">Enums</span></span>

<span data-ttu-id="54b92-331">**Bunları kullanmanız gerekmedikçe bu özelliklerden genellikle kaçının:**</span><span class="sxs-lookup"><span data-stu-id="54b92-331">**Generally avoid these features unless you must use them:**</span></span>

* <span data-ttu-id="54b92-332">Devralma tabanlı tür hiyerarşileri ve uygulama devralma</span><span class="sxs-lookup"><span data-stu-id="54b92-332">Inheritance-based type hierarchies and implementation inheritance</span></span>
* <span data-ttu-id="54b92-333">Null değerler ve `Unchecked.defaultof<_>`</span><span class="sxs-lookup"><span data-stu-id="54b92-333">Nulls and `Unchecked.defaultof<_>`</span></span>

### <a name="prefer-composition-over-inheritance"></a><span data-ttu-id="54b92-334">Devralma üzerine oluşturmayı tercih et</span><span class="sxs-lookup"><span data-stu-id="54b92-334">Prefer composition over inheritance</span></span>

<span data-ttu-id="54b92-335">[Devralmayla Ilgili birleşim](https://en.wikipedia.org/wiki/Composition_over_inheritance) , iyi F# kodun bağlı olduğu uzun süreli bir deyimdir.</span><span class="sxs-lookup"><span data-stu-id="54b92-335">[Composition over inheritance](https://en.wikipedia.org/wiki/Composition_over_inheritance) is a long-standing idiom that good F# code can adhere to.</span></span> <span data-ttu-id="54b92-336">Temel prensibi, temel bir sınıfı kullanıma sunmamalıdır ve arayanların işlevselliği almak için bu temel sınıftan devralmasını zorlamaktır.</span><span class="sxs-lookup"><span data-stu-id="54b92-336">The fundamental principle is that you should not expose a base class and force callers to inherit from that base class to get functionality.</span></span>

### <a name="use-object-expressions-to-implement-interfaces-if-you-dont-need-a-class"></a><span data-ttu-id="54b92-337">Sınıf gerekmiyorsa arabirim uygulamak için nesne ifadelerini kullanın</span><span class="sxs-lookup"><span data-stu-id="54b92-337">Use object expressions to implement interfaces if you don't need a class</span></span>

<span data-ttu-id="54b92-338">[Nesne ifadeleri](../language-reference/object-expressions.md) , bir sınıfın içinde olması gerekmeden uygulanan arabirimi bir değere bağlayarak, anında arabirim uygulamanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="54b92-338">[Object Expressions](../language-reference/object-expressions.md) allow you to implement interfaces on the fly, binding the implemented interface to a value without needing to do so inside of a class.</span></span> <span data-ttu-id="54b92-339">Bu, özellikle de _yalnızca_ arabirimini uygulamanız gerekiyorsa ve tam sınıfa gerek duygerekmiyorsa kullanışlı bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="54b92-339">This is convenient, especially if you _only_ need to implement the interface and have no need for a full class.</span></span>

<span data-ttu-id="54b92-340">Örneğin, için `open` deyiminiz olmayan bir sembol eklediyseniz bir kod düzelme eylemi sağlamak üzere [ıonıde](http://ionide.io/) 'de çalıştırılan kod aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="54b92-340">For example, here is the code that is run in [Ionide](http://ionide.io/) to provide a code fix action if you've added a symbol that you don't have an `open` statement for:</span></span>

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

<span data-ttu-id="54b92-341">Visual Studio Code API ile etkileşim kurarken bir sınıfa gerek olmadığından, nesne Ifadeleri bunun için ideal bir araçtır.</span><span class="sxs-lookup"><span data-stu-id="54b92-341">Because there is no need for a class when interacting with the Visual Studio Code API, Object Expressions are an ideal tool for this.</span></span> <span data-ttu-id="54b92-342">Ayrıca, test yordamlarına sahip bir arabirimi geçici olarak bir şekilde sağlamak istediğinizde birim testi için de değerlidir.</span><span class="sxs-lookup"><span data-stu-id="54b92-342">They are also valuable for unit testing, when you want to stub out an interface with test routines in an ad hoc manner.</span></span>

## <a name="consider-type-abbreviations-to-shorten-signatures"></a><span data-ttu-id="54b92-343">İmzaları kısaltmak için kısaltmalar türlerini göz önünde bulundurun</span><span class="sxs-lookup"><span data-stu-id="54b92-343">Consider Type Abbreviations to shorten signatures</span></span>

<span data-ttu-id="54b92-344">[Tür kısaltmaları](../language-reference/type-abbreviations.md) , bir etiketi bir işlev imzası veya daha karmaşık bir tür gibi başka bir türe atamak için kullanışlı bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="54b92-344">[Type Abbreviations](../language-reference/type-abbreviations.md) are a convenient way to assign a label to another type, such as a function signature or a more complex type.</span></span> <span data-ttu-id="54b92-345">Örneğin, aşağıdaki diğer ad, derin bir öğrenme kitaplığı olan [Cntk](https://docs.microsoft.com/cognitive-toolkit/)ile bir hesaplama tanımlamak için gereken bir etiketi atar:</span><span class="sxs-lookup"><span data-stu-id="54b92-345">For example, the following alias assigns a label to what's needed to define a computation with [CNTK](https://docs.microsoft.com/cognitive-toolkit/), a deep learning library:</span></span>

```fsharp
open CNTK

// DeviceDescriptor, Variable, and Function all come from CNTK
type Computation = DeviceDescriptor -> Variable -> Function
```

<span data-ttu-id="54b92-346">`Computation` adı, diğer bir deyişle, daha sonra gelen imzayla eşleşen herhangi bir işlevi göstermek için uygun bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="54b92-346">The `Computation` name is a convenient way to denote any function that matches the signature it is aliasing.</span></span> <span data-ttu-id="54b92-347">Bu gibi tür kısaltmalarının kullanılması kullanışlıdır ve daha fazla kısa kodu sağlar.</span><span class="sxs-lookup"><span data-stu-id="54b92-347">Using Type Abbreviations like this is convenient and allows for more succinct code.</span></span>

### <a name="avoid-using-type-abbreviations-to-represent-your-domain"></a><span data-ttu-id="54b92-348">Etki alanınızı temsil etmek için tür kısaltmalarının kullanmaktan kaçının</span><span class="sxs-lookup"><span data-stu-id="54b92-348">Avoid using Type Abbreviations to represent your domain</span></span>

<span data-ttu-id="54b92-349">Tür kısaltmaları işlev imzalara bir ad vermek için uygun olsa da, abbreviating diğer türler olduğunda kafa karıştırıcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="54b92-349">Although Type Abbreviations are convenient for giving a name to function signatures, they can be confusing when abbreviating other types.</span></span> <span data-ttu-id="54b92-350">Bu kısaltmayı göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="54b92-350">Consider this abbreviation:</span></span>

```fsharp
// Does not actually abstract integers.
type BufferSize = int
```

<span data-ttu-id="54b92-351">Bu, birden çok şekilde kafa karıştırıcı olabilir:</span><span class="sxs-lookup"><span data-stu-id="54b92-351">This can be confusing in multiple ways:</span></span>

* <span data-ttu-id="54b92-352">`BufferSize` bir soyutlama değil; tamsayı için yalnızca başka bir addır.</span><span class="sxs-lookup"><span data-stu-id="54b92-352">`BufferSize` is not an abstraction; it is just another name for an integer.</span></span>
* <span data-ttu-id="54b92-353">`BufferSize` ortak bir API 'de sunulmazda, çok daha fazla `int`büyük bir şekilde yanlış yorumlanabilmektedir.</span><span class="sxs-lookup"><span data-stu-id="54b92-353">If `BufferSize` is exposed in a public API, it can easily be misinterpreted to mean more than just `int`.</span></span> <span data-ttu-id="54b92-354">Genellikle, etki alanı türlerinin kendileri için birden çok özniteliği vardır ve `int`gibi temel türler değildir.</span><span class="sxs-lookup"><span data-stu-id="54b92-354">Generally, domain types have multiple attributes to them and are not primitive types like `int`.</span></span> <span data-ttu-id="54b92-355">Bu kısaltma Bu varsayımını ihlal ediyor.</span><span class="sxs-lookup"><span data-stu-id="54b92-355">This abbreviation violates that assumption.</span></span>
* <span data-ttu-id="54b92-356">`BufferSize` büyük küçük harf (PascalCase), bu türün daha fazla veri bulundurduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="54b92-356">The casing of `BufferSize` (PascalCase) implies that this type holds more data.</span></span>
* <span data-ttu-id="54b92-357">Bu diğer ad, bir işleve adlandırılmış bir bağımsız değişken sağlamaya kıyasla daha fazla açıklık sunmaz.</span><span class="sxs-lookup"><span data-stu-id="54b92-357">This alias does not offer increased clarity compared with providing a named argument to a function.</span></span>
* <span data-ttu-id="54b92-358">Kısaltma derlenmiş Il 'de bildirim içermez; yalnızca bir tamsayıdır ve bu diğer ad derleme zamanı yapısıdır.</span><span class="sxs-lookup"><span data-stu-id="54b92-358">The abbreviation will not manifest in compiled IL; it is just an integer and this alias is a compile-time construct.</span></span>

```fsharp
module Networking =
    ...
    let send data (bufferSize: int) = ...
```

<span data-ttu-id="54b92-359">Özet olarak, tür kısaltmalarıyla birlikte, abbreviating oldukları türler üzerinde soyutlamalar **değildir** .</span><span class="sxs-lookup"><span data-stu-id="54b92-359">In summary, the pitfall with Type Abbreviations is that they are **not** abstractions over the types they are abbreviating.</span></span> <span data-ttu-id="54b92-360">Önceki örnekte `BufferSize`, hiçbir ek veri olmadan veya `int` zaten sahip olduğu gibi tür sisteminden herhangi bir avantajdan yalnızca bir `int`.</span><span class="sxs-lookup"><span data-stu-id="54b92-360">In the previous example, `BufferSize` is just an `int` under the covers, with no additional data, nor any benefits from the type system besides what `int` already has.</span></span>

<span data-ttu-id="54b92-361">Bir etki alanını temsil etmek için tür kısaltmalarının kullanılmasına alternatif bir yaklaşım, tek büyük harf ayrılmış birleşimler kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="54b92-361">An alternative approach to using type abbreviations to represent a domain is to use single-case discriminated unions.</span></span> <span data-ttu-id="54b92-362">Önceki örnek aşağıdaki gibi modellenebilir:</span><span class="sxs-lookup"><span data-stu-id="54b92-362">The previous sample can be modeled as follows:</span></span>

```fsharp
type BufferSize = BufferSize of int
```

<span data-ttu-id="54b92-363">`BufferSize` ve temel aldığı değer bakımından çalışan bir kod yazarsanız, herhangi bir rastgele tamsayı geçirmek yerine bir tane oluşturmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="54b92-363">If you write code that operates in terms of `BufferSize` and its underlying value, you need to construct one rather than pass in any arbitrary integer:</span></span>

```fsharp
module Networking =
    ...
    let send data (BufferSize size) =
    ...
```

<span data-ttu-id="54b92-364">Bu, çağıran işlevi çağırmak için bir değeri sarmadan önce bir `BufferSize` türü oluşturmasının gerektiğinden, yanlışlıkla rastgele bir tamsayıyı `send` işlevine geçirme olasılığını azaltır.</span><span class="sxs-lookup"><span data-stu-id="54b92-364">This reduces the likelihood of mistakenly passing an arbitrary integer into the `send` function, because the caller must construct a `BufferSize` type to wrap a value before calling the function.</span></span>
