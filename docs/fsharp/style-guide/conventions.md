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
# <a name="f-coding-conventions"></a><span data-ttu-id="b5fd0-103">F# kodlama kuralları</span><span class="sxs-lookup"><span data-stu-id="b5fd0-103">F# coding conventions</span></span>

<span data-ttu-id="b5fd0-104">Aşağıdaki sözleşmeler, büyük F# kod tabanlarıyla çalışma deneyiminden formüle edilmiştir.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-104">The following conventions are formulated from experience working with large F# codebases.</span></span> <span data-ttu-id="b5fd0-105">[İyi F# kodunun beş ilkesi](index.md#five-principles-of-good-f-code) her tavsiyenin temelidir.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-105">The [Five principles of good F# code](index.md#five-principles-of-good-f-code) are the foundation of each recommendation.</span></span> <span data-ttu-id="b5fd0-106">Bunlar [F# bileşeni tasarım yönergeleri](component-design-guidelines.md)ile ilgilidir, ancak yalnızca kitaplıklar gibi bileşenler için değil, herhangi bir F# kodu için de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-106">They are related to the [F# component design guidelines](component-design-guidelines.md), but are applicable for any F# code, not just components such as libraries.</span></span>

## <a name="organizing-code"></a><span data-ttu-id="b5fd0-107">Kodu düzenleme</span><span class="sxs-lookup"><span data-stu-id="b5fd0-107">Organizing code</span></span>

<span data-ttu-id="b5fd0-108">F# kodu düzenlemenin iki birincil yolunu sunar: modüller ve ad alanları.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-108">F# features two primary ways to organize code: modules and namespaces.</span></span> <span data-ttu-id="b5fd0-109">Bunlar benzer, ancak aşağıdaki farklılıklar var:</span><span class="sxs-lookup"><span data-stu-id="b5fd0-109">These are similar, but do have the following differences:</span></span>

* <span data-ttu-id="b5fd0-110">Ad alanları .NET ad alanları olarak derlenir.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-110">Namespaces are compiled as .NET namespaces.</span></span> <span data-ttu-id="b5fd0-111">Modüller statik sınıflar olarak derlenmiştir.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-111">Modules are compiled as static classes.</span></span>
* <span data-ttu-id="b5fd0-112">Ad boşlukları her zaman en üst düzeydir.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-112">Namespaces are always top level.</span></span> <span data-ttu-id="b5fd0-113">Modüller üst düzey olabilir ve diğer modüller içinde iç içe.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-113">Modules can be top-level and nested within other modules.</span></span>
* <span data-ttu-id="b5fd0-114">Ad alanları birden çok dosyaya yayılabilir.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-114">Namespaces can span multiple files.</span></span> <span data-ttu-id="b5fd0-115">Modüller yapamaz.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-115">Modules cannot.</span></span>
* <span data-ttu-id="b5fd0-116">Modüller ile `[<RequireQualifiedAccess>]` dekore edilebilir `[<AutoOpen>]`ve .</span><span class="sxs-lookup"><span data-stu-id="b5fd0-116">Modules can be decorated with `[<RequireQualifiedAccess>]` and `[<AutoOpen>]`.</span></span>

<span data-ttu-id="b5fd0-117">Aşağıdaki yönergeler, kodunuzu düzenlemek için bunları kullanmanıza yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-117">The following guidelines will help you use these to organize your code.</span></span>

### <a name="prefer-namespaces-at-the-top-level"></a><span data-ttu-id="b5fd0-118">Ad alanlarını en üst düzeyde tercih edin</span><span class="sxs-lookup"><span data-stu-id="b5fd0-118">Prefer namespaces at the top level</span></span>

<span data-ttu-id="b5fd0-119">Genel olarak tüketilen herhangi bir kod için ad alanları en üst düzeydeki modüllere tercih edilir.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-119">For any publicly consumable code, namespaces are preferential to modules at the top level.</span></span> <span data-ttu-id="b5fd0-120">.NET ad alanları olarak derlendiklerinden, C#'dan herhangi bir sorun olmadan tüketilebilirler.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-120">Because they are compiled as .NET namespaces, they are consumable from C# with no issue.</span></span>

```fsharp
// Good!
namespace MyCode

type MyClass() =
    ...
```

<span data-ttu-id="b5fd0-121">Üst düzey bir modül kullanmak yalnızca F#'dan çağrıldığında farklı görünmeyebilir, ancak C# `MyClass` tüketicileri `MyCode` için arayanlar modüle hak kazanmak zorunda kalarak şaşırabilirler.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-121">Using a top-level module may not appear different when called only from F#, but for C# consumers, callers may be surprised by having to qualify `MyClass` with the `MyCode` module.</span></span>

```fsharp
// Bad!
module MyCode

type MyClass() =
    ...
```

### <a name="carefully-apply-autoopen"></a><span data-ttu-id="b5fd0-122">Dikkatlice uygulayın`[<AutoOpen>]`</span><span class="sxs-lookup"><span data-stu-id="b5fd0-122">Carefully apply `[<AutoOpen>]`</span></span>

<span data-ttu-id="b5fd0-123">Yapı `[<AutoOpen>]` arayanlar için kullanılabilir ne kapsamı kirletebilir, ve bir şey nereden geldiğinin cevabı "sihirli".</span><span class="sxs-lookup"><span data-stu-id="b5fd0-123">The `[<AutoOpen>]` construct can pollute the scope of what is available to callers, and the answer to where something comes from is "magic".</span></span> <span data-ttu-id="b5fd0-124">Bu iyi bir şey değil.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-124">This is not a good thing.</span></span> <span data-ttu-id="b5fd0-125">Bu kuralın bir istisnası F# Core Library kendisi (bu gerçeği de biraz tartışmalı olmasına rağmen).</span><span class="sxs-lookup"><span data-stu-id="b5fd0-125">An exception to this rule is the F# Core Library itself (though this fact is also a bit controversial).</span></span>

<span data-ttu-id="b5fd0-126">Ancak, genel BIR API için, bu genel API'den ayrı ayrı düzenlemek istediğiniz yardımcı işlevselliğiniz varsa, bu bir kolaylıktır.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-126">However, it is a convenience if you have helper functionality for a public API that you wish to organize separately from that public API.</span></span>

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

<span data-ttu-id="b5fd0-127">Bu, her aradığınızda bir yardımcıyı tam olarak hak lamak zorunda kalmadan uygulama ayrıntılarını bir işlevin genel API'sinden temiz bir şekilde ayırmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-127">This lets you cleanly separate implementation details from the public API of a function without having to fully qualify a helper each time you call it.</span></span>

<span data-ttu-id="b5fd0-128">Ayrıca, uzantı yöntemleri ve ifade oluşturucuları ad alanı düzeyinde ortaya `[<AutoOpen>]`çıkarmak düzgünce ifade edilebilir.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-128">Additionally, exposing extension methods and expression builders at the namespace level can be neatly expressed with `[<AutoOpen>]`.</span></span>

### <a name="use-requirequalifiedaccess-whenever-names-could-conflict-or-you-feel-it-helps-with-readability"></a><span data-ttu-id="b5fd0-129">Adlar çakışabilir veya okunabilirlik ile yardımcı olduğunu hissediyorum zaman kullanın `[<RequireQualifiedAccess>]`</span><span class="sxs-lookup"><span data-stu-id="b5fd0-129">Use `[<RequireQualifiedAccess>]` whenever names could conflict or you feel it helps with readability</span></span>

<span data-ttu-id="b5fd0-130">Bir `[<RequireQualifiedAccess>]` modüle öznitelik eklenmesi, modülün açılmayabileceğini ve modülün öğelerine yapılan başvuruların açık nitelikli erişim gerektirdiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-130">Adding the `[<RequireQualifiedAccess>]` attribute to a module indicates that the module may not be opened and that references to the elements of the module require explicit qualified access.</span></span> <span data-ttu-id="b5fd0-131">Örneğin, `Microsoft.FSharp.Collections.List` modül bu özniteliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-131">For example, the `Microsoft.FSharp.Collections.List` module has this attribute.</span></span>

<span data-ttu-id="b5fd0-132">Bu, modüldeki işlevler ve değerler diğer modüllerde adlarla çakışma olasılığı olan adlara sahipse yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-132">This is useful when functions and values in the module have names that are likely to conflict with names in other modules.</span></span> <span data-ttu-id="b5fd0-133">Nitelikli erişim gerektiren büyük ölçüde uzun vadeli bakım ve bir kütüphane evolvability artırabilir.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-133">Requiring qualified access can greatly increase the long-term maintainability and evolvability of a library.</span></span>

```fsharp
[<RequireQualifiedAccess>]
module StringTokenization =
    let parse s = ...

...

let s = getAString()
let parsed = StringTokenization.parse s // Must qualify to use 'parse'
```

### <a name="sort-open-statements-topologically"></a><span data-ttu-id="b5fd0-134">İfadeleri topolojik olarak sıralayın `open`</span><span class="sxs-lookup"><span data-stu-id="b5fd0-134">Sort `open` statements topologically</span></span>

<span data-ttu-id="b5fd0-135">F#'da, bildirimlerin sırası, ifadeler `open` de dahil olmak üzere önemlidir.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-135">In F#, the order of declarations matters, including with `open` statements.</span></span> <span data-ttu-id="b5fd0-136">Bu, etkisinin `using` bir dosyadaki `using static` bu ifadelerin sıralanmasından bağımsız olduğu C#'dan farklı değildir.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-136">This is unlike C#, where the effect of `using` and `using static` is independent of the ordering of those statements in a file.</span></span>

<span data-ttu-id="b5fd0-137">F#'da, bir kapsama açılan öğeler zaten mevcut olan diğer öğeleri gölgeleyebilir.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-137">In F#, elements opened into a scope can shadow others already present.</span></span> <span data-ttu-id="b5fd0-138">Bu, `open` ifadeleri yeniden sıralamanın kodun anlamını değiştirebileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-138">This means that reordering `open` statements could alter the meaning of code.</span></span> <span data-ttu-id="b5fd0-139">Sonuç olarak, beklediğiniz farklı davranışlar `open` oluşturmanız için tüm deyimlerin (örneğin, alfasayısal olarak) rasgele sıralanması önerilmez.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-139">As a result, any arbitrary sorting of all `open` statements (for example, alphanumerically) is not recommended, lest you generate different behavior that you might expect.</span></span>

<span data-ttu-id="b5fd0-140">Bunun yerine, bunları [topolojik olarak](https://en.wikipedia.org/wiki/Topological_sorting)sıralamanızı öneririz; diğer bir deyişle, ekstrelerinizi `open` sisteminizin _katmanlarının_ tanımlandığı sırada sıralayın.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-140">Instead, we recommend that you sort them [topologically](https://en.wikipedia.org/wiki/Topological_sorting); that is, order your `open` statements in the order in which _layers_ of your system are defined.</span></span> <span data-ttu-id="b5fd0-141">Farklı topolojik tabakalar içinde alfanümerik sıralama yapmak da düşünülebilir.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-141">Doing alphanumeric sorting within different topological layers may also be considered.</span></span>

<span data-ttu-id="b5fd0-142">Örnek olarak, F# derleyici hizmeti genel API dosyası için topolojik sıralama aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="b5fd0-142">As an example, here is the topological sorting for the F# compiler service public API file:</span></span>

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

<span data-ttu-id="b5fd0-143">Bir çizgi sonu topolojik katmanları ayırır ve her katman daha sonra alfasayısal olarak sıralanır unutmayın.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-143">Note that a line break separates topological layers, with each layer being sorted alphanumerically afterwards.</span></span> <span data-ttu-id="b5fd0-144">Bu, yanlışlıkla değerleri gölgelemeden kodu temiz bir şekilde düzenler.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-144">This cleanly organizes code without accidentally shadowing values.</span></span>

## <a name="use-classes-to-contain-values-that-have-side-effects"></a><span data-ttu-id="b5fd0-145">Yan etkileri olan değerleri içerecek şekilde sınıfları kullanma</span><span class="sxs-lookup"><span data-stu-id="b5fd0-145">Use classes to contain values that have side effects</span></span>

<span data-ttu-id="b5fd0-146">Bir değerin başlatılmasının, bir bağlamı veritabanına veya başka bir uzak kaynağa anında algılama gibi yan etkileri olabileceği birçok kez vardır.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-146">There are many times when initializing a value can have side effects, such as instantiating a context to a database or other remote resource.</span></span> <span data-ttu-id="b5fd0-147">Bu tür şeyleri bir modülde başlatmayı ve sonraki işlevlerde kullanmak caziptir:</span><span class="sxs-lookup"><span data-stu-id="b5fd0-147">It is tempting to initialize such things in a module and use it in subsequent functions:</span></span>

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

<span data-ttu-id="b5fd0-148">Bu genellikle birkaç nedenden dolayı kötü bir fikirdir:</span><span class="sxs-lookup"><span data-stu-id="b5fd0-148">This is frequently a bad idea for a few reasons:</span></span>

<span data-ttu-id="b5fd0-149">İlk olarak, uygulama yapılandırması ile `dep1` `dep2`codebase içine itilir ve .</span><span class="sxs-lookup"><span data-stu-id="b5fd0-149">First, application configuration is pushed into the codebase with `dep1` and `dep2`.</span></span> <span data-ttu-id="b5fd0-150">Bunu daha büyük kod tabanlarında korumak zordur.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-150">This is difficult to maintain in larger codebases.</span></span>

<span data-ttu-id="b5fd0-151">İkinci olarak, statik olarak başlaltımılan veriler, bileşeninizin kendisi birden çok iş parçacığı kullanacaksa iş parçacığı güvenli olmayan değerleri içermemelidir.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-151">Second, statically initialized data should not include values that are not thread safe if your component will itself use multiple threads.</span></span> <span data-ttu-id="b5fd0-152">Bu açıkça tarafından `dep3`ihlal edilir.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-152">This is clearly violated by `dep3`.</span></span>

<span data-ttu-id="b5fd0-153">Son olarak, modül başlatma tüm derleme birimi için statik bir oluşturucu içine derler.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-153">Finally, module initialization compiles into a static constructor for the entire compilation unit.</span></span> <span data-ttu-id="b5fd0-154">Bu modülde let-bound değer başlatmada herhangi bir hata oluşursa, uygulamanın tüm ömrü boyunca önbelleğe alınmış bir `TypeInitializationException` hata olarak kendini gösterir.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-154">If any error occurs in let-bound value initialization in that module, it manifests as a `TypeInitializationException` that is then cached for the entire lifetime of the application.</span></span> <span data-ttu-id="b5fd0-155">Bu tanılamak zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-155">This can be difficult to diagnose.</span></span> <span data-ttu-id="b5fd0-156">Genellikle hakkında neden deneyebilirsiniz bir iç özel durum vardır, ancak yoksa, o zaman kök neden ne olduğunu söylemek yoktur.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-156">There is usually an inner exception that you can attempt to reason about, but if there is not, then there is no telling what the root cause is.</span></span>

<span data-ttu-id="b5fd0-157">Bunun yerine, bağımlılıkları tutmak için basit bir sınıf kullanmanız salt</span><span class="sxs-lookup"><span data-stu-id="b5fd0-157">Instead, just use a simple class to hold dependencies:</span></span>

```fsharp
type MyParametricApi(dep1, dep2, dep3) =
    member _.Function1 arg1 = doStuffWith dep1 dep2 dep3 arg1
    member _.Function2 arg2 = doStuffWith dep1 dep2 dep3 arg2
```

<span data-ttu-id="b5fd0-158">Bu, aşağıdakileri sağlar:</span><span class="sxs-lookup"><span data-stu-id="b5fd0-158">This enables the following:</span></span>

1. <span data-ttu-id="b5fd0-159">Herhangi bir bağımlı durumu API'nin kendisi dışında itme.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-159">Pushing any dependent state outside of the API itself.</span></span>
2. <span data-ttu-id="b5fd0-160">Yapılandırma artık API dışında yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-160">Configuration can now be done outside of the API.</span></span>
3. <span data-ttu-id="b5fd0-161">Bağımlı değerler için başlatma hataları bir `TypeInitializationException`.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-161">Errors in initialization for dependent values are not likely to manifest as a `TypeInitializationException`.</span></span>
4. <span data-ttu-id="b5fd0-162">API'yi test etmek artık daha kolay.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-162">The API is now easier to test.</span></span>

## <a name="error-management"></a><span data-ttu-id="b5fd0-163">Hata yönetimi</span><span class="sxs-lookup"><span data-stu-id="b5fd0-163">Error management</span></span>

<span data-ttu-id="b5fd0-164">Büyük sistemlerde hata yönetimi karmaşık ve nüanslı bir çabadır ve sistemlerinizin hataya dayanıklı olmasını ve iyi çalışmasını sağlamada gümüş madde işaretleri yoktur.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-164">Error management in large systems is a complex and nuanced endeavor, and there are no silver bullets in ensuring your systems are fault-tolerant and behave well.</span></span> <span data-ttu-id="b5fd0-165">Aşağıdaki yönergeler bu zor alanda gezinme konusunda rehberlik sunmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-165">The following guidelines should offer guidance in navigating this difficult space.</span></span>

### <a name="represent-error-cases-and-illegal-state-in-types-intrinsic-to-your-domain"></a><span data-ttu-id="b5fd0-166">Etki alanınızın içsel türlerinde hata durumlarını ve yasa dışı durumu temsil etme</span><span class="sxs-lookup"><span data-stu-id="b5fd0-166">Represent error cases and illegal state in types intrinsic to your domain</span></span>

<span data-ttu-id="b5fd0-167">[Ayrımcı Birlikler](../language-reference/discriminated-unions.md)ile F#, türü sisteminizde hatalı program durumunu temsil etme olanağı sağlar.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-167">With [Discriminated Unions](../language-reference/discriminated-unions.md), F# gives you the ability to represent faulty program state in your type system.</span></span> <span data-ttu-id="b5fd0-168">Örnek:</span><span class="sxs-lookup"><span data-stu-id="b5fd0-168">For example:</span></span>

```fsharp
type MoneyWithdrawalResult =
    | Success of amount:decimal
    | InsufficientFunds of balance:decimal
    | CardExpired of DateTime
    | UndisclosedFailure
```

<span data-ttu-id="b5fd0-169">Bu durumda, bir banka hesabından para çekmenin başarısız olabileceği bilinen üç yol vardır.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-169">In this case, there are three known ways that withdrawing money from a bank account can fail.</span></span> <span data-ttu-id="b5fd0-170">Her hata örneği türde temsil edilir ve böylece program boyunca güvenli bir şekilde ele alınabilir.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-170">Each error case is represented in the type, and can thus be dealt with safely throughout the program.</span></span>

```fsharp
let handleWithdrawal amount =
    let w = withdrawMoney amount
    match w with
    | Success am -> printfn "Successfully withdrew %f" am
    | InsufficientFunds balance -> printfn "Failed: balance is %f" balance
    | CardExpired expiredDate -> printfn "Failed: card expired on %O" expiredDate
    | UndisclosedFailure -> printfn "Failed: unknown"
```

<span data-ttu-id="b5fd0-171">Genel olarak, bir şey etki alanınızda **başarısız** olabilir farklı şekillerde modelleyebilir, o zaman hata işleme kodu artık düzenli program akışına ek olarak uğraşmak zorunda bir şey olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-171">In general, if you can model the different ways that something can **fail** in your domain, then error handling code is no longer treated as something you must deal with in addition to regular program flow.</span></span> <span data-ttu-id="b5fd0-172">Bu sadece normal program akışının bir parçasıdır ve **istisnai**olarak kabul edilmez.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-172">It is simply a part of normal program flow, and not considered **exceptional**.</span></span> <span data-ttu-id="b5fd0-173">Bunun iki temel faydası vardır:</span><span class="sxs-lookup"><span data-stu-id="b5fd0-173">There are two primary benefits to this:</span></span>

1. <span data-ttu-id="b5fd0-174">Etki alanınız zaman içinde değiştikçe bakımı daha kolaydır.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-174">It is easier to maintain as your domain changes over time.</span></span>
2. <span data-ttu-id="b5fd0-175">Hata durumlarını birleştirmek daha kolaydır.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-175">Error cases are easier to unit test.</span></span>

### <a name="use-exceptions-when-errors-cannot-be-represented-with-types"></a><span data-ttu-id="b5fd0-176">Hatalar türleri ile temsil edilemiyorsa özel durumlar kullanma</span><span class="sxs-lookup"><span data-stu-id="b5fd0-176">Use exceptions when errors cannot be represented with types</span></span>

<span data-ttu-id="b5fd0-177">Tüm hatalar sorunlu bir etki alanında temsil edilemez.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-177">Not all errors can be represented in a problem domain.</span></span> <span data-ttu-id="b5fd0-178">Bu tür hatalar doğada *istisnaidir,* bu nedenle F#'daki istisnaları yükseltme ve yakalama yeteneği.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-178">These kinds of faults are *exceptional* in nature, hence the ability to raise and catch exceptions in F#.</span></span>

<span data-ttu-id="b5fd0-179">İlk olarak, Özel Durum [Tasarım Yönergeleri'ni](../../standard/design-guidelines/exceptions.md)okumanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-179">First, it is recommended that you read the [Exception Design Guidelines](../../standard/design-guidelines/exceptions.md).</span></span> <span data-ttu-id="b5fd0-180">Bunlar F# için de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-180">These are also applicable to F#.</span></span>

<span data-ttu-id="b5fd0-181">Özel durumları yükseltmek amacıyla F#'da bulunan ana yapılar aşağıdaki tercih sırasına göre ele alınmalıdır:</span><span class="sxs-lookup"><span data-stu-id="b5fd0-181">The main constructs available in F# for the purposes of raising exceptions should be considered in the following order of preference:</span></span>

| <span data-ttu-id="b5fd0-182">İşlev</span><span class="sxs-lookup"><span data-stu-id="b5fd0-182">Function</span></span> | <span data-ttu-id="b5fd0-183">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b5fd0-183">Syntax</span></span> | <span data-ttu-id="b5fd0-184">Amaç</span><span class="sxs-lookup"><span data-stu-id="b5fd0-184">Purpose</span></span> |
|----------|--------|---------|
| `nullArg` | `nullArg "argumentName"` | <span data-ttu-id="b5fd0-185">Belirtilen `System.ArgumentNullException` bağımsız değişken adı ile bir yükseltir.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-185">Raises a `System.ArgumentNullException` with the specified argument name.</span></span> |
| `invalidArg` | `invalidArg "argumentName" "message"` | <span data-ttu-id="b5fd0-186">Belirli `System.ArgumentException` bir bağımsız değişken adı ve iletisi ile bir yükseltir.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-186">Raises a `System.ArgumentException` with a specified argument name and message.</span></span> |
| `invalidOp` | `invalidOp "message"` | <span data-ttu-id="b5fd0-187">Belirtilen `System.InvalidOperationException` iletiyle bir yükseltir.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-187">Raises a `System.InvalidOperationException` with the specified message.</span></span> |
|`raise`| `raise (ExceptionType("message"))` | <span data-ttu-id="b5fd0-188">Özel durumlar atmak için genel amaçlı mekanizma.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-188">General-purpose mechanism for throwing exceptions.</span></span> |
| `failwith` | `failwith "message"` | <span data-ttu-id="b5fd0-189">Belirtilen `System.Exception` iletiyle bir yükseltir.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-189">Raises a `System.Exception` with the specified message.</span></span> |
| `failwithf` | `failwithf "format string" argForFormatString` | <span data-ttu-id="b5fd0-190">Biçim `System.Exception` dizesi ve girişleri tarafından belirlenen bir ileti ile yükseltir.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-190">Raises a `System.Exception` with a message determined by the format string and its inputs.</span></span> |

<span data-ttu-id="b5fd0-191">Kullanın `nullArg` `invalidArg` , `invalidOp` ve atmak `ArgumentNullException`için `ArgumentException` `InvalidOperationException` mekanizma olarak , ve uygun olduğunda.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-191">Use `nullArg`, `invalidArg` and `invalidOp` as the mechanism to throw `ArgumentNullException`, `ArgumentException` and `InvalidOperationException` when appropriate.</span></span>

<span data-ttu-id="b5fd0-192">Belirli `failwith` `failwithf` bir özel durum değil, temel `Exception` türünü yükselttikleri için ve işlevlerden genellikle kaçınılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-192">The `failwith` and `failwithf` functions should generally be avoided because they raise the base `Exception` type, not a specific exception.</span></span> <span data-ttu-id="b5fd0-193">[Özel Durum Tasarım Yönergeleri'ne](../../standard/design-guidelines/exceptions.md)göre, ne zaman yapabilirseniz daha özel özel durumlar yükseltmek istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-193">As per the [Exception Design Guidelines](../../standard/design-guidelines/exceptions.md), you want to raise more specific exceptions when you can.</span></span>

### <a name="using-exception-handling-syntax"></a><span data-ttu-id="b5fd0-194">Özel durum işleme sözdizimini kullanma</span><span class="sxs-lookup"><span data-stu-id="b5fd0-194">Using exception-handling syntax</span></span>

<span data-ttu-id="b5fd0-195">F# sözdizimi `try...with` aracılığıyla özel durum desenlerini destekler:</span><span class="sxs-lookup"><span data-stu-id="b5fd0-195">F# supports exception patterns via the `try...with` syntax:</span></span>

```fsharp
try
    tryGetFileContents()
with
| :? System.IO.FileNotFoundException as e -> // Do something with it here
| :? System.Security.SecurityException as e -> // Do something with it here
```

<span data-ttu-id="b5fd0-196">Kodu temiz tutmak istiyorsanız, desen eşleştirmesi ile bir özel durum karşısında gerçekleştirmek için işlevselliği uzlaştırmak biraz zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-196">Reconciling functionality to perform in the face of an exception with pattern matching can be a bit tricky if you wish to keep the code clean.</span></span> <span data-ttu-id="b5fd0-197">Bunu işlemenin yollarından biri, bir hata örneğini çevreleyen işlevselliği özel bir özel durumla gruplandırmak için [etkin desenler](../language-reference/active-patterns.md) kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-197">One such way to handle this is to use [active patterns](../language-reference/active-patterns.md) as a means to group functionality surrounding an error case with an exception itself.</span></span> <span data-ttu-id="b5fd0-198">Örneğin, bir özel durum attığında, özel durum meta verilerine değerli bilgileri dahil eden bir API tüketiyor olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-198">For example, you may be consuming an API that, when it throws an exception, encloses valuable information in the exception metadata.</span></span> <span data-ttu-id="b5fd0-199">Etkin Desen içinde yakalanan özel durum gövdesinde yararlı bir değer açma ve bu değeri döndürme bazı durumlarda yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-199">Unwrapping a useful value in the body of the captured exception inside the Active Pattern and returning that value can be helpful in some situations.</span></span>

### <a name="do-not-use-monadic-error-handling-to-replace-exceptions"></a><span data-ttu-id="b5fd0-200">Özel durumları değiştirmek için monadik hata işleme kullanmayın</span><span class="sxs-lookup"><span data-stu-id="b5fd0-200">Do not use monadic error handling to replace exceptions</span></span>

<span data-ttu-id="b5fd0-201">İstisnalar işlevsel programlamada biraz tabu olarak görülür.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-201">Exceptions are seen as somewhat taboo in functional programming.</span></span> <span data-ttu-id="b5fd0-202">Gerçekten de, istisnalar saflığı ihlal, bu yüzden onları oldukça işlevsel değil dikkate almak güvenlidir.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-202">Indeed, exceptions violate purity, so it's safe to consider them not-quite functional.</span></span> <span data-ttu-id="b5fd0-203">Ancak, bu kod çalışması gereken yerin gerçekliğini yok sayar ve çalışma zamanı hataları oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-203">However, this ignores the reality of where code must run, and that runtime errors can occur.</span></span> <span data-ttu-id="b5fd0-204">Genel olarak, çoğu şey ne saf ne de toplam, tatsız sürprizler en aza indirmek için olduğu varsayımı üzerine kod yazın.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-204">In general, write code on the assumption that most things are neither pure nor total, to minimize unpleasant surprises.</span></span>

<span data-ttu-id="b5fd0-205">.NET çalışma zamanı ve diller arası ekosistemdeki alaka ve uygunlukları açısından İstisnaların aşağıdaki temel güçlü yanlarını/yönlerini göz önünde bulundurmak önemlidir:</span><span class="sxs-lookup"><span data-stu-id="b5fd0-205">It is important to consider the following core strengths/aspects of Exceptions with respect to their relevance and appropriateness in the .NET runtime and cross-language ecosystem as a whole:</span></span>

1. <span data-ttu-id="b5fd0-206">Bunlar, bir sorunu hata ayıklarken çok yararlı olan ayrıntılı tanı bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-206">They contain detailed diagnostic information, which is very helpful when debugging an issue.</span></span>
2. <span data-ttu-id="b5fd0-207">Çalışma zamanı ve diğer .NET dilleri tarafından iyi anlaşılır.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-207">They are well-understood by the runtime and other .NET languages.</span></span>
3. <span data-ttu-id="b5fd0-208">Anlamsal etiklerinin bir alt kümesini özel olarak uygulayarak istisnalardan *kaçınmak* için yolundan çıkan kodla karşılaştırıldığında önemli bir kazan plakasını azaltabilirler.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-208">They can reduce significant boilerplate when compared with code that goes out of its way to *avoid* exceptions by implementing some subset of their semantics on an ad-hoc basis.</span></span>

<span data-ttu-id="b5fd0-209">Bu üçüncü nokta çok önemli.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-209">This third point is critical.</span></span> <span data-ttu-id="b5fd0-210">Önemsiz olmayan karmaşık işlemler için, özel durumları kullanmamak aşağıdaki gibi yapılarla başa çıkmaya neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="b5fd0-210">For nontrivial complex operations, failing to use exceptions can result in dealing with structures like this:</span></span>

```fsharp
Result<Result<MyType, string>, string list>
```

<span data-ttu-id="b5fd0-211">Hangi kolayca "dize-yazılı" hataları desen eşleşen gibi kırılgan kodyol açabilir:</span><span class="sxs-lookup"><span data-stu-id="b5fd0-211">Which can easily lead to fragile code like pattern matching on "stringly-typed" errors:</span></span>

```fsharp
let result = doStuff()
match result with
| Ok r -> ...
| Error e ->
    if e.Contains "Error string 1" then ...
    elif e.Contains "Error string 2" then ...
    else ... // Who knows?
```

<span data-ttu-id="b5fd0-212">Ayrıca, bir "güzel" türü döndürür "basit" bir işlev için arzu herhangi bir istisna yutmak için cazip olabilir:</span><span class="sxs-lookup"><span data-stu-id="b5fd0-212">Additionally, it can be tempting to swallow any exception in the desire for a "simple" function that returns a "nicer" type:</span></span>

```fsharp
// This is bad!
let tryReadAllText (path : string) =
    try System.IO.File.ReadAllText path |> Some
    with _ -> None
```

<span data-ttu-id="b5fd0-213">Ne `tryReadAllText` yazık ki, bir dosya sisteminde meydana gelebilecek sayısız şeye dayanarak çok sayıda özel durum atabilir ve bu kod, ortamınızda gerçekte neyin yanlış olabileceğine dair herhangi bir bilgiyi ortadan atar.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-213">Unfortunately, `tryReadAllText` can throw numerous exceptions based on the myriad of things that can happen on a file system, and this code discards away any information about what might actually be going wrong in your environment.</span></span> <span data-ttu-id="b5fd0-214">Bu kodu bir sonuç türüyle değiştirirseniz, "dize yle yazılan" hata iletisini ayrıştırmaya geri dönersiniz:</span><span class="sxs-lookup"><span data-stu-id="b5fd0-214">If you replace this code with a result type, then you're back to "stringly-typed" error message parsing:</span></span>

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

<span data-ttu-id="b5fd0-215">Ayrıca, özel durum nesnesinin kendisini `Error` oluşturucuya yerleştirmek, sizi işlevyerine çağrı yerindeki özel durum türüyle düzgün bir şekilde ilgilenmeye zorlar.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-215">And placing the exception object itself in the `Error` constructor just forces you to properly deal with the exception type at the call site rather than in the function.</span></span> <span data-ttu-id="b5fd0-216">Bunu yapmak, bir API'yi arayan kişi olarak ele almak için oldukça eğlenceli olmayan denetlenmiş özel durumlar oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-216">Doing this effectively creates checked exceptions, which are notoriously unfun to deal with as a caller of an API.</span></span>

<span data-ttu-id="b5fd0-217">Yukarıdaki örneklere iyi bir *alternatif, belirli* özel durumları yakalamak ve bu özel durum bağlamında anlamlı bir değer döndürmektir.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-217">A good alternative to the above examples is to catch *specific* exceptions and return a meaningful value in the context of that exception.</span></span> <span data-ttu-id="b5fd0-218">`tryReadAllText` İşlevi aşağıdaki gibi değiştirirseniz, `None` daha anlamlıdır:</span><span class="sxs-lookup"><span data-stu-id="b5fd0-218">If you modify the `tryReadAllText` function as follows, `None` has more meaning:</span></span>

```fsharp
let tryReadAllTextIfPresent (path : string) =
    try System.IO.File.ReadAllText path |> Some
    with :? FileNotFoundException -> None
```

<span data-ttu-id="b5fd0-219">Tümlerini yakalama olarak çalışmak yerine, bu işlev artık bir dosya bulunamediğinde servis talebiyle düzgün bir şekilde işleyecek ve bu anlamı iadeye atayacaktır.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-219">Instead of functioning as a catch-all, this function will now properly handle the case when a file was not found and assign that meaning to a return.</span></span> <span data-ttu-id="b5fd0-220">Bu iade değeri, herhangi bir bağlamsal bilgi atmamadan veya arayanları kodun o noktasında alakalı olmayan bir durumla uğraşmaya zorlamazken, bu hata örneğine eşleyebilir.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-220">This return value can map to that error case, while not discarding any contextual information or forcing callers to deal with a case that may not be relevant at that point in the code.</span></span>

<span data-ttu-id="b5fd0-221">İç `Result<'Success, 'Error>` içe geçmedikleri temel işlemler için uygundur ve F# isteğe bağlı türleri, bir şeyin *bir şeyi* veya hiçbir *şeyi*döndürebileceğini temsil etmek için idealdir.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-221">Types such as `Result<'Success, 'Error>` are appropriate for basic operations where they aren't nested, and F# optional types are perfect for representing when something could either return *something* or *nothing*.</span></span> <span data-ttu-id="b5fd0-222">Ancak, özel durumların yerini almamaktadırlar ve özel durumları değiştirmek için kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-222">They are not a replacement for exceptions, though, and should not be used in an attempt to replace exceptions.</span></span> <span data-ttu-id="b5fd0-223">Bunun yerine, istisna ve hata yönetimi ilkesinin belirli yönlerini hedeflenen yollarla ele almak için akıllıca uygulanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-223">Rather, they should be applied judiciously to address specific aspects of exception and error management policy in targeted ways.</span></span>

## <a name="partial-application-and-point-free-programming"></a><span data-ttu-id="b5fd0-224">Kısmi uygulama ve noktasız programlama</span><span class="sxs-lookup"><span data-stu-id="b5fd0-224">Partial application and point-free programming</span></span>

<span data-ttu-id="b5fd0-225">F# kısmi uygulamayı destekler ve böylece, noktasız bir tarzda programlamak için çeşitli yollar.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-225">F# supports partial application, and thus, various ways to program in a point-free style.</span></span> <span data-ttu-id="b5fd0-226">Bu, bir modül içinde kod yeniden kullanımı veya bir şeyin uygulanması için yararlı olabilir, ancak kamuya açık bir şey değildir.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-226">This can be beneficial for code reuse within a module or the implementation of something, but it is not something to expose publicly.</span></span> <span data-ttu-id="b5fd0-227">Genel olarak, nokta-free programlama ve kendisi bir erdem değildir ve tarzı dalmış olmayan insanlar için önemli bir bilişsel engel ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-227">In general, point-free programming is not a virtue in and of itself, and can add a significant cognitive barrier for people who are not immersed in the style.</span></span>

### <a name="do-not-use-partial-application-and-currying-in-public-apis"></a><span data-ttu-id="b5fd0-228">Kamu API'lerinde kısmi uygulama ve köri kullanmayın</span><span class="sxs-lookup"><span data-stu-id="b5fd0-228">Do not use partial application and currying in public APIs</span></span>

<span data-ttu-id="b5fd0-229">Küçük bir istisna dışında, kamu API'lerinde kısmi uygulama kullanımı tüketiciler için kafa karıştırıcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-229">With little exception, the use of partial application in public APIs can be confusing for consumers.</span></span> <span data-ttu-id="b5fd0-230">Genellikle, `let`F# kodunda -bağlı **değerler, işlev değerleri**değil **değerlerdir.**</span><span class="sxs-lookup"><span data-stu-id="b5fd0-230">Usually, `let`-bound values in F# code are **values**, not **function values**.</span></span> <span data-ttu-id="b5fd0-231">Değerleri ve işlev değerlerini bir araya getirmek, özellikle işlevleri oluşturmak gibi `>>` işleçlerle birleştiğinde, biraz bilişsel ek yükü karşılığında az sayıda kod satırının kaydedilmesine neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-231">Mixing together values and function values can result in saving a small number of lines of code in exchange for quite a bit of cognitive overhead, especially if combined with operators such as `>>` to compose functions.</span></span>

### <a name="consider-the-tooling-implications-for-point-free-programming"></a><span data-ttu-id="b5fd0-232">Noktasız programlama için araç lama sonuçlarını göz önünde bulundurun</span><span class="sxs-lookup"><span data-stu-id="b5fd0-232">Consider the tooling implications for point-free programming</span></span>

<span data-ttu-id="b5fd0-233">Curried işlevleri kendi bağımsız değişkenleri etiketlemek yok.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-233">Curried functions do not label their arguments.</span></span> <span data-ttu-id="b5fd0-234">Bunun takımlama etkileri vardır.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-234">This has tooling implications.</span></span> <span data-ttu-id="b5fd0-235">Aşağıdaki iki işlevi göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="b5fd0-235">Consider the following two functions:</span></span>

```fsharp
let func name age =
    printfn "My name is %s and I am %d years old!" name age

let funcWithApplication =
    printfn "My name is %s and I am %d years old!"
```

<span data-ttu-id="b5fd0-236">Her ikisi de `funcWithApplication` geçerli işlevler, ancak bir curried işlevidir.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-236">Both are valid functions, but `funcWithApplication` is a curried function.</span></span> <span data-ttu-id="b5fd0-237">Bir editörde türlerinin üzerinde gezinirken şunları görürsünüz:</span><span class="sxs-lookup"><span data-stu-id="b5fd0-237">When you hover over their types in an editor, you see this:</span></span>

```fsharp
val func : name:string -> age:int -> unit

val funcWithApplication : (string -> int -> unit)
```

<span data-ttu-id="b5fd0-238">Arama sitesinde, Visual Studio gibi araç uçlarında, giriş türlerinin gerçekte `string` neyi `int` temsil ettiğini zedelemez.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-238">At the call site, tooltips in tooling such as Visual Studio will not give you meaningful information as to what the `string` and `int` input types actually represent.</span></span>

<span data-ttu-id="b5fd0-239">Bu gibi `funcWithApplication` noktasız kodla karşılaşırsanız, genel olarak tüketilebilir, takım lamanın bağımsız değişkenler için anlamlı adlar alabilmeleri için tam bir genişletme yapmanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-239">If you encounter point-free code like `funcWithApplication` that is publicly consumable, it is recommended to do a full η-expansion so that tooling can pick up on meaningful names for arguments.</span></span>

<span data-ttu-id="b5fd0-240">Ayrıca, noktasız kod hata ayıklama imkansız değilse, zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-240">Furthermore, debugging point-free code can be challenging, if not impossible.</span></span> <span data-ttu-id="b5fd0-241">Hata ayıklama araçları, yürütmenin ortasında ara `let` değerleri inceleyebilmeniz için adlara bağlı değerlere (örneğin, bağlamalar) dayanır.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-241">Debugging tools rely on values bound to names (for example, `let` bindings) so that you can inspect intermediate values midway through execution.</span></span> <span data-ttu-id="b5fd0-242">Kodunuzun denetlenecek değeri yoksa, hata ayıklamak için hiçbir şey yoktur.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-242">When your code has no values to inspect, there is nothing to debug.</span></span> <span data-ttu-id="b5fd0-243">Gelecekte, hata ayıklama araçları bu değerleri daha önce yürütülmüş yollara göre sentezlemek için gelişebilir, ancak *olası* hata ayıklama işlevleri üzerine bahislerinizi hedge etmek iyi bir fikir değildir.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-243">In the future, debugging tools may evolve to synthesize these values based on previously executed paths, but it's not a good idea to hedge your bets on *potential* debugging functionality.</span></span>

### <a name="consider-partial-application-as-a-technique-to-reduce-internal-boilerplate"></a><span data-ttu-id="b5fd0-244">Kısmi uygulamayı iç kazan plakasını azaltmak için bir teknik olarak düşünün</span><span class="sxs-lookup"><span data-stu-id="b5fd0-244">Consider partial application as a technique to reduce internal boilerplate</span></span>

<span data-ttu-id="b5fd0-245">Önceki noktanın aksine, kısmi uygulama bir uygulama nın içindeki kazan plakasını veya bir API'nin daha derin iç lerini azaltmak için harika bir araçtır.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-245">In contrast to the previous point, partial application is a wonderful tool for reducing boilerplate inside of an application or the deeper internals of an API.</span></span> <span data-ttu-id="b5fd0-246">Daha karmaşık API'lerin uygulanmasını test eden birim için yararlı olabilir, burada kazan genellikle başa çıkmak için bir ağrıdır.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-246">It can be helpful for unit testing the implementation of more complicated APIs, where boilerplate is often a pain to deal with.</span></span> <span data-ttu-id="b5fd0-247">Örneğin, aşağıdaki kod, böyle bir çerçeveye dışa bağımlılık yapmadan ve ilgili ısmarlama API'yi öğrenmek zorunda kalmadan, en alaycı çerçevelerin size verdiği şeyi nasıl başarabileceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-247">For example, the following code shows how you can accomplish what most mocking frameworks give you without taking an external dependency on such a framework and having to learn a related bespoke API.</span></span>

<span data-ttu-id="b5fd0-248">Örneğin, aşağıdaki çözüm topografyasını göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="b5fd0-248">For example, consider the following solution topography:</span></span>

```
MySolution.sln
|_/ImplementationLogic.fsproj
|_/ImplementationLogic.Tests.fsproj
|_/API.fsproj
```

<span data-ttu-id="b5fd0-249">`ImplementationLogic.fsproj`gibi kod ortaya çıkarabilir:</span><span class="sxs-lookup"><span data-stu-id="b5fd0-249">`ImplementationLogic.fsproj` might expose code such as:</span></span>

```fsharp
module Transactions =
    let doTransaction txnContext txnType balance =
        ...

type Transactor(ctx, currentBalance) =
    member _.ExecuteTransaction(txnType) =
        Transactions.doTransaction ctx txtType currentBalance
        ...
```

<span data-ttu-id="b5fd0-250">Birim `Transactions.doTransaction` testi `ImplementationLogic.Tests.fsproj` kolaydır:</span><span class="sxs-lookup"><span data-stu-id="b5fd0-250">Unit testing `Transactions.doTransaction` in `ImplementationLogic.Tests.fsproj` is easy:</span></span>

```fsharp
namespace TransactionsTestingUtil

open Transactions

module TransactionsTestable =
    let getTestableTransactionRoutine mockContext = Transactions.doTransaction mockContext
```

<span data-ttu-id="b5fd0-251">Alaycı bir `doTransaction` bağlam nesnesi ile kısmen uygulamak, her seferinde alay edilmiş bir bağlam oluşturmaya gerek kalmadan tüm birim testlerinizdeki işlevi aramanızı sağlar:</span><span class="sxs-lookup"><span data-stu-id="b5fd0-251">Partially applying `doTransaction` with a mocking context object lets you call the function in all of your unit tests without needing to construct a mocked context each time:</span></span>

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

<span data-ttu-id="b5fd0-252">Bu teknik evrensel olarak tüm codebase uygulanmamalıdır, ancak karmaşık iç ve birim bu iç test için ortak azaltmak için iyi bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-252">This technique should not be universally applied to your entire codebase, but it is a good way to reduce boilerplate for complicated internals and unit testing those internals.</span></span>

## <a name="access-control"></a><span data-ttu-id="b5fd0-253">Erişim denetimi</span><span class="sxs-lookup"><span data-stu-id="b5fd0-253">Access control</span></span>

<span data-ttu-id="b5fd0-254">F# ['nin .NET](../language-reference/access-control.md)çalışma zamanında bulunanlardan devralınan Access denetimi için birden çok seçeneği vardır.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-254">F# has multiple options for [Access control](../language-reference/access-control.md), inherited from what is available in the .NET runtime.</span></span> <span data-ttu-id="b5fd0-255">Bunlar sadece türleri için kullanılabilir değildir - işlevleri için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-255">These are not just usable for types - you can use them for functions, too.</span></span>

* <span data-ttu-id="b5fd0-256">Genel olarak`public` tüketilebilir olması gerekene kadar tür olmayanları ve üyeleri tercih edin.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-256">Prefer non-`public` types and members until you need them to be publicly consumable.</span></span> <span data-ttu-id="b5fd0-257">Bu aynı zamanda tüketicilerin çift ne en aza indirir.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-257">This also minimizes what consumers couple to.</span></span>
* <span data-ttu-id="b5fd0-258">Tüm yardımcı işlevselliğini `private`korumak için çalışıyoruz.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-258">Strive to keep all helper functionality `private`.</span></span>
* <span data-ttu-id="b5fd0-259">Çok sayıda `[<AutoOpen>]` olursa yardımcı işlevlerin özel bir modül üzerinde kullanımını düşünün.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-259">Consider the use of `[<AutoOpen>]` on a private module of helper functions if they become numerous.</span></span>

## <a name="type-inference-and-generics"></a><span data-ttu-id="b5fd0-260">Tür çıkarım ve jenerik</span><span class="sxs-lookup"><span data-stu-id="b5fd0-260">Type inference and generics</span></span>

<span data-ttu-id="b5fd0-261">Tür çıkarım ları, çok fazla kazan plakası yazmaktan sizi kurtarabilir.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-261">Type inference can save you from typing a lot of boilerplate.</span></span> <span data-ttu-id="b5fd0-262">Ve F# derleyicisi otomatik genelleme sizin tarafınızdan hemen hemen hiçbir ekstra çaba ile daha genel kod yazmanıza yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-262">And automatic generalization in the F# compiler can help you write more generic code with almost no extra effort on your part.</span></span> <span data-ttu-id="b5fd0-263">Ancak, bu özellikler evrensel olarak iyi değildir.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-263">However, these features are not universally good.</span></span>

* <span data-ttu-id="b5fd0-264">Bağımsız değişken adlarını genel API'lerde açık türleri olan etiketlemeyi düşünün ve bunun için tür çıkarımına güvenmeyin.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-264">Consider labeling argument names with explicit types in public APIs and do not rely on type inference for this.</span></span>

    <span data-ttu-id="b5fd0-265">Bunun nedeni, derleyicideğil, API'nizin şeklini kontrol **altında** olması gerektiğidir.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-265">The reason for this is that **you** should be in control of the shape of your API, not the compiler.</span></span> <span data-ttu-id="b5fd0-266">Derleyici sizin için türleri inferring iyi bir iş yapabilir, ancak dayandığı iç türleri değişti eğer API değişikliği şekli olması mümkündür.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-266">Although the compiler can do a fine job at inferring types for you, it is possible to have the shape of your API change if the internals it relies on have changed types.</span></span> <span data-ttu-id="b5fd0-267">Bu ne istediğinizi olabilir, ama neredeyse kesinlikle aşağı tüketicilerin daha sonra uğraşmak zorunda kalacak bir kırılma API değişikliği neden olacaktır.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-267">This may be what you want, but it will almost certainly result in a breaking API change that downstream consumers will then have to deal with.</span></span> <span data-ttu-id="b5fd0-268">Bunun yerine, genel API'nizin şeklini açıkça denetlerseniz, bu kesme değişikliklerini denetleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-268">Instead, if you explicitly control the shape of your public API, then you can control these breaking changes.</span></span> <span data-ttu-id="b5fd0-269">DDD açısından, bu bir Yolsuzlukla Mücadele katmanı olarak düşünülebilir.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-269">In DDD terms, this can be thought of as an Anti-corruption layer.</span></span>

* <span data-ttu-id="b5fd0-270">Genel bağımsız değişkenlerinize anlamlı bir ad vermeyi düşünün.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-270">Consider giving a meaningful name to your generic arguments.</span></span>

    <span data-ttu-id="b5fd0-271">Belirli bir etki alanına özgü olmayan gerçekten genel kod yazmadığınız sürece, anlamlı bir ad diğer programcıların çalıştıkları etki alanını anlamalarına yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-271">Unless you are writing truly generic code that is not specific to a particular domain, a meaningful name can help other programmers understanding the domain they're working in.</span></span> <span data-ttu-id="b5fd0-272">Örneğin, belge veritabanıyla `'Document` etkileşim bağlamında adlandırılan bir tür parametresi, genel belge türlerinin çalıştığınız işlev veya üye tarafından kabul edilebilmiş olabileceğini daha net hale getirir.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-272">For example, a type parameter named `'Document` in the context of interacting with a document database makes it clearer that generic document types can be accepted by the function or member you are working with.</span></span>

* <span data-ttu-id="b5fd0-273">Genel tür parametrelerini PascalCase ile adlandırmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-273">Consider naming generic type parameters with PascalCase.</span></span>

    <span data-ttu-id="b5fd0-274">Bu .NET'te bir şeyler yapmanın genel yoludur, bu nedenle snake_case veya camelCase yerine PascalCase kullanmanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-274">This is the general way to do things in .NET, so it's recommended that you use PascalCase rather than snake_case or camelCase.</span></span>

<span data-ttu-id="b5fd0-275">Son olarak, otomatik genelleme her zaman F # veya büyük bir codebase yeni insanlar için bir nimet değildir.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-275">Finally, automatic generalization is not always a boon for people who are new to F# or a large codebase.</span></span> <span data-ttu-id="b5fd0-276">Genel bileşenleri kullanarak bilişsel yükü vardır.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-276">There is cognitive overhead in using components that are generic.</span></span> <span data-ttu-id="b5fd0-277">Ayrıca, otomatik olarak genelleştirilmiş işlevler farklı giriş türleri ile kullanılmazsa (bu şekilde kullanılmak üzere tasarlanmıştır, o zaman onları zaman içinde genel olmak için gerçek bir yararı yoktur.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-277">Furthermore, if automatically generalized functions are not used with different input types (let alone if they are intended to be used as such), then there is no real benefit to them being generic at that point in time.</span></span> <span data-ttu-id="b5fd0-278">Yazdığınız kodun gerçekten genel olmaktan fayda sağlanıncaya bilebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-278">Always consider if the code you are writing will actually benefit from being generic.</span></span>

## <a name="performance"></a><span data-ttu-id="b5fd0-279">Performans</span><span class="sxs-lookup"><span data-stu-id="b5fd0-279">Performance</span></span>

### <a name="prefer-structs-for-small-data-types"></a><span data-ttu-id="b5fd0-280">Küçük veri türleri için yapıları tercih etme</span><span class="sxs-lookup"><span data-stu-id="b5fd0-280">Prefer structs for small data types</span></span>

<span data-ttu-id="b5fd0-281">Genellikle nesneleri ayırmayı önlediğinden, yapı ların (Değer Türleri olarak da adlandırılır) kullanılması, bazı kodlar için genellikle daha yüksek performansa neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-281">Using structs (also called Value Types) can often result in higher performance for some code because it typically avoids allocating objects.</span></span> <span data-ttu-id="b5fd0-282">Ancak, yapı strütler her zaman bir "daha hızlı git" düğmesi değildir: bir yapıdaki verilerin boyutu 16 baytı aşıyorsa, verileri kopyalamak genellikle başvuru türünü kullanmaktan daha fazla CPU harcaması ile sonuçlanabilir.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-282">However, structs are not always a "go faster" button: if the size of the data in a struct exceeds 16 bytes, copying the data can often result in more CPU time spend than using a reference type.</span></span>

<span data-ttu-id="b5fd0-283">Bir yapı kullanmanız gerekip gerekip gerekmeden karar vermek için aşağıdaki koşulları göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="b5fd0-283">To determine if you should use a struct, consider the following conditions:</span></span>

- <span data-ttu-id="b5fd0-284">Verilerinizin boyutu 16 bayt veya daha küçükse.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-284">If the size of your data is 16 bytes or smaller.</span></span>
- <span data-ttu-id="b5fd0-285">Çalışan bir programda bu veri türlerinin çoğunun bellekte yerleşik olması olasıysa.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-285">If you're likely to have many of these data types resident in memory in a running program.</span></span>

<span data-ttu-id="b5fd0-286">İlk koşul geçerliyse, genellikle bir yapı kullanmalısınız.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-286">If the first condition applies, you should generally use a struct.</span></span> <span data-ttu-id="b5fd0-287">Her ikisi de geçerliyse, hemen hemen her zaman bir yapı kullanmalısınız.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-287">If both apply, you should almost always use a struct.</span></span> <span data-ttu-id="b5fd0-288">Önceki koşulların geçerli olduğu bazı durumlar olabilir, ancak bir yapı kullanmak bir başvuru türünü kullanmaktan daha iyi veya daha kötü değildir, ancak nadir olma olasılığı yüksektir.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-288">There may be some cases where the previous conditions apply, but using a struct is no better or worse than using a reference type, but they are likely to be rare.</span></span> <span data-ttu-id="b5fd0-289">Her zaman bu gibi değişiklikler yaparken ölçmek için önemlidir, rağmen, ve varsayım veya sezgi üzerinde faaliyet değil.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-289">It's important to always measure when making changes like this, though, and not operate on assumption or intuition.</span></span>

#### <a name="prefer-struct-tuples-when-grouping-small-value-types"></a><span data-ttu-id="b5fd0-290">Küçük değer türlerini gruplandırmayaparken yapı tuples'ı tercih etme</span><span class="sxs-lookup"><span data-stu-id="b5fd0-290">Prefer struct tuples when grouping small value types</span></span>

<span data-ttu-id="b5fd0-291">Aşağıdaki iki işlevi göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="b5fd0-291">Consider the following two functions:</span></span>

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

<span data-ttu-id="b5fd0-292">Bu işlevleri [BenchmarkDotNet](https://benchmarkdotnet.org/)gibi istatistiksel bir kıyaslama aracıyla kıyasladığınızda, yapı tuples kullanan işlevin `runWithStructTuple` %40 daha hızlı çalıştığını ve bellek ayırmadığını göreceksiniz.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-292">When you benchmark these functions with a statistical benchmarking tool like [BenchmarkDotNet](https://benchmarkdotnet.org/), you'll find that the `runWithStructTuple` function that uses struct tuples runs 40% faster and allocates no memory.</span></span>

<span data-ttu-id="b5fd0-293">Ancak, bu sonuçlar her zaman kendi kodunuzda böyle olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-293">However, these results won't always be the case in your own code.</span></span> <span data-ttu-id="b5fd0-294">Bir işlevi , `inline`başvuru tuples kullanan kod olarak işaretlerseniz bazı ek optimizasyonlar alabilir veya ayrılacak kod yalnızca uzak optimize edilebilir.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-294">If you mark a function as `inline`, code that uses reference tuples may get some additional optimizations, or code that would allocate could simply be optimized away.</span></span> <span data-ttu-id="b5fd0-295">Performans söz konusu olduğunda sonuçları her zaman ölçmeli ve asla varsayım adabına veya sezgilerine göre çalışmamalısınız.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-295">You should always measure results whenever performance is concerned, and never operate based on assumption or intuition.</span></span>

#### <a name="prefer-struct-records-when-the-data-type-is-small"></a><span data-ttu-id="b5fd0-296">Veri türü küçükolduğunda yapı kayıtlarını tercih etme</span><span class="sxs-lookup"><span data-stu-id="b5fd0-296">Prefer struct records when the data type is small</span></span>

<span data-ttu-id="b5fd0-297">Daha önce açıklanan başparmak kuralı [f# kayıt türleri](../language-reference/records.md)için de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-297">The rule of thumb described earlier also holds for [F# record types](../language-reference/records.md).</span></span> <span data-ttu-id="b5fd0-298">Bunları işleyen aşağıdaki veri türlerini ve işlevleri göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="b5fd0-298">Consider the following data types and functions that process them:</span></span>

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

<span data-ttu-id="b5fd0-299">Bu önceki tuple koduna benzer, ancak bu kez örnek kayıtları ve astarlı bir iç işlevi kullanır.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-299">This is similar to the previous tuple code, but this time the example uses records and an inlined inner function.</span></span>

<span data-ttu-id="b5fd0-300">Bu işlevleri [BenchmarkDotNet](https://benchmarkdotnet.org/)gibi istatistiksel bir kıyaslama aracıyla `processStructPoint` kıyasladığınızda, yaklaşık %60 daha hızlı çalıştığını ve yönetilen yığında hiçbir şey ayırmadığını görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-300">When you benchmark these functions with a statistical benchmarking tool like [BenchmarkDotNet](https://benchmarkdotnet.org/), you'll find that `processStructPoint` runs nearly 60% faster and allocates nothing on the managed heap.</span></span>

#### <a name="prefer-struct-discriminated-unions-when-the-data-type-is-small"></a><span data-ttu-id="b5fd0-301">Veri türü küçükolduğunda yapı ayrımcı birliş tercih</span><span class="sxs-lookup"><span data-stu-id="b5fd0-301">Prefer struct discriminated unions when the data type is small</span></span>

<span data-ttu-id="b5fd0-302">Yapı tuples ve kayıtları ile performans hakkında önceki gözlemler de [F # Ayrımcı Sendikalar](../language-reference/discriminated-unions.md)için tutar.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-302">The previous observations about performance with struct tuples and records also holds for [F# Discriminated Unions](../language-reference/discriminated-unions.md).</span></span> <span data-ttu-id="b5fd0-303">Aşağıdaki kodu inceleyin:</span><span class="sxs-lookup"><span data-stu-id="b5fd0-303">Consider the following code:</span></span>

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

<span data-ttu-id="b5fd0-304">Etki alanı modellemesi için bunun gibi tek harfli Ayrımcı Birlikler tanımlamak yaygındır.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-304">It's common to define single-case Discriminated Unions like this for domain modeling.</span></span> <span data-ttu-id="b5fd0-305">Bu işlevleri [BenchmarkDotNet](https://benchmarkdotnet.org/)gibi istatistiksel bir kıyaslama aracıyla `structReverseName` kıyasladığınızda, küçük `reverseName` dizeleri için yaklaşık% 25 daha hızlı çalışır bulacaksınız.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-305">When you benchmark these functions with a statistical benchmarking tool like [BenchmarkDotNet](https://benchmarkdotnet.org/), you'll find that `structReverseName` runs about 25% faster than `reverseName` for small strings.</span></span> <span data-ttu-id="b5fd0-306">Büyük dizeleri için, her ikisi de yaklaşık aynı gerçekleştirmek.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-306">For large strings, both perform about the same.</span></span> <span data-ttu-id="b5fd0-307">Yani, bu durumda, her zaman bir yapı kullanmak tercih edilir.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-307">So, in this case, it's always preferable to use a struct.</span></span> <span data-ttu-id="b5fd0-308">Daha önce de belirtildiği gibi, her zaman ölçmek ve varsayımlar veya sezgi üzerinde faaliyet yok.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-308">As previously mentioned, always measure and do not operate on assumptions or intuition.</span></span>

<span data-ttu-id="b5fd0-309">Önceki örnek, bir yapı Nın Daha iyi performans verdiğini gösterse de, bir etki alanını modellerken daha büyük Ayrımcı Birlikler olması yaygındır.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-309">Although the previous example showed that a struct Discriminated Union yielded better performance, it is common to have larger Discriminated Unions when modeling a domain.</span></span> <span data-ttu-id="b5fd0-310">Daha fazla kopyalama söz konusu olabileceğinden, bu tür daha büyük veri türleri, üzerlerindeki işlemlere bağlı olarak yapı lıysa, iyi performans göstermeyebilir.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-310">Larger data types like that may not perform as well if they are structs depending on the operations on them, since more copying could be involved.</span></span>

### <a name="functional-programming-and-mutation"></a><span data-ttu-id="b5fd0-311">Fonksiyonel programlama ve mutasyon</span><span class="sxs-lookup"><span data-stu-id="b5fd0-311">Functional programming and mutation</span></span>

<span data-ttu-id="b5fd0-312">F# değerleri varsayılan olarak değişmezdir, bu da belirli hata sınıflarından (özellikle eşzamanlılık ve paralellik içerenler) kaçınmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-312">F# values are immutable by default, which allows you to avoid certain classes of bugs (especially those involving concurrency and parallelism).</span></span> <span data-ttu-id="b5fd0-313">Ancak, bazı durumlarda, yürütme süresi veya bellek ayırmaları optimal (hatta makul) verimlilik elde etmek için, iş bir süre en iyi devlet yerinde mutasyon kullanılarak uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-313">However, in certain cases, in order to achieve optimal (or even reasonable) efficiency of execution time or memory allocations, a span of work may best be implemented by using in-place mutation of state.</span></span> <span data-ttu-id="b5fd0-314">Bu anahtar kelime ile F# ile `mutable` bir opt-in bazında mümkündür.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-314">This is possible in an opt-in basis with F# with the `mutable` keyword.</span></span>

<span data-ttu-id="b5fd0-315">F# `mutable` kullanımı fonksiyonel saflık ile oran hissedebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-315">Use of `mutable` in F# may feel at odds with functional purity.</span></span> <span data-ttu-id="b5fd0-316">Bu anlaşılabilir, ancak fonksiyonel saflık her yerde performans hedefleri ile oran olabilir.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-316">This is understandable, but functional purity everywhere can be at odds with performance goals.</span></span> <span data-ttu-id="b5fd0-317">Bir uzlaşma, arayanların bir işlev dedikleri zaman ne olduğu yla ilgilenmemesi için mutasyonu kapsüllemektir.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-317">A compromise is to encapsulate mutation such that callers need not care about what happens when they call a function.</span></span> <span data-ttu-id="b5fd0-318">Bu, performans açısından kritik kod için mutasyon tabanlı bir uygulama üzerinde işlevsel bir arabirim yazmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-318">This allows you to write a functional interface over a mutation-based implementation for performance-critical code.</span></span>

#### <a name="wrap-mutable-code-in-immutable-interfaces"></a><span data-ttu-id="b5fd0-319">Değişmez arabirimlerde mutable kodu kaydırma</span><span class="sxs-lookup"><span data-stu-id="b5fd0-319">Wrap mutable code in immutable interfaces</span></span>

<span data-ttu-id="b5fd0-320">Bir hedef olarak başvurusal saydamlık ile, performans açısından kritik işlevlerin mutable underbelly ortaya çıkarmaz kod yazmak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-320">With referential transparency as a goal, it is critical to write code that does not expose the mutable underbelly of performance-critical functions.</span></span> <span data-ttu-id="b5fd0-321">Örneğin, aşağıdaki kod F# `Array.contains` çekirdek kitaplığında işlevi uygular:</span><span class="sxs-lookup"><span data-stu-id="b5fd0-321">For example, the following code implements the `Array.contains` function in the F# core library:</span></span>

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

<span data-ttu-id="b5fd0-322">Bu işlevi birden çok kez çağırmak, temel diziyi değiştirmez ve onu tüketire bağlı olarak herhangi bir değişken durumu korumanızı gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-322">Calling this function multiple times does not change the underlying array, nor does it require you to maintain any mutable state in consuming it.</span></span> <span data-ttu-id="b5fd0-323">İçindeki hemen hemen her kod satırı mutasyon kullansa da, referentially saydamdır.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-323">It is referentially transparent, even though almost every line of code within it uses mutation.</span></span>

#### <a name="consider-encapsulating-mutable-data-in-classes"></a><span data-ttu-id="b5fd0-324">Sınıflarda sayılabilir verileri kapsüllemeyi düşünün</span><span class="sxs-lookup"><span data-stu-id="b5fd0-324">Consider encapsulating mutable data in classes</span></span>

<span data-ttu-id="b5fd0-325">Önceki örnekte, mutable verileri kullanarak işlemleri kapsüllemek için tek bir işlev kullanılmıştır.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-325">The previous example used a single function to encapsulate operations using mutable data.</span></span> <span data-ttu-id="b5fd0-326">Bu, daha karmaşık veri kümeleri için her zaman yeterli değildir.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-326">This is not always sufficient for more complex sets of data.</span></span> <span data-ttu-id="b5fd0-327">Aşağıdaki işlev kümelerini göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="b5fd0-327">Consider the following sets of functions:</span></span>

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

<span data-ttu-id="b5fd0-328">Bu kod performanttır, ancak arayanların korumaktan sorumlu olduğu mutasyon tabanlı veri yapısını ortaya çıkarır.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-328">This code is performant, but it exposes the mutation-based data structure that callers are responsible for maintaining.</span></span> <span data-ttu-id="b5fd0-329">Bu, altta yatan üyeleri olmayan bir sınıfın içine sarılmış olabilir:</span><span class="sxs-lookup"><span data-stu-id="b5fd0-329">This can be wrapped inside of a class with no underlying members that can change:</span></span>

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

<span data-ttu-id="b5fd0-330">`Closure1Table`altta yatan mutasyon tabanlı veri yapısını kapsüller, bu nedenle arayanlar altta yatan veri yapısını korumak için zorlamaz.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-330">`Closure1Table` encapsulates the underlying mutation-based data structure, thereby not forcing callers to maintain the underlying data structure.</span></span> <span data-ttu-id="b5fd0-331">Sınıflar, ayrıntıları arayanlara ifşa etmeden mutasyona dayalı verileri ve rutinleri kapsüllemek için güçlü bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-331">Classes are a powerful way to encapsulate data and routines that are mutation-based without exposing the details to callers.</span></span>

#### <a name="prefer-let-mutable-to-reference-cells"></a><span data-ttu-id="b5fd0-332">Hücrelere başvurmayı tercih edin `let mutable`</span><span class="sxs-lookup"><span data-stu-id="b5fd0-332">Prefer `let mutable` to reference cells</span></span>

<span data-ttu-id="b5fd0-333">Başvuru hücreleri, başvuruyu değerin kendisi yerine bir değere temsil etmenin bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-333">Reference cells are a way to represent the reference to a value rather than the value itself.</span></span> <span data-ttu-id="b5fd0-334">Performans açısından kritik kod için kullanılabilseler de, önerilmezler.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-334">Although they can be used for performance-critical code, they are not recommended.</span></span> <span data-ttu-id="b5fd0-335">Aşağıdaki örneği inceleyin:</span><span class="sxs-lookup"><span data-stu-id="b5fd0-335">Consider the following example:</span></span>

```fsharp
let kernels =
    let acc = ref Set.empty

    processWorkList startKernels (fun kernel ->
        if not ((!acc).Contains(kernel)) then
            acc := (!acc).Add(kernel)
        ...)

    !acc |> Seq.toList
```

<span data-ttu-id="b5fd0-336">Bir referans hücresinin kullanımı artık sonraki tüm kodları temel verileri dereference ve yeniden başvurmak zorunda "kirletır".</span><span class="sxs-lookup"><span data-stu-id="b5fd0-336">The use of a reference cell now "pollutes" all subsequent code with having to dereference and re-reference the underlying data.</span></span> <span data-ttu-id="b5fd0-337">Bunun yerine, düşünün: `let mutable`</span><span class="sxs-lookup"><span data-stu-id="b5fd0-337">Instead, consider `let mutable`:</span></span>

```fsharp
let kernels =
    let mutable acc = Set.empty

    processWorkList startKernels (fun kernel ->
        if not (acc.Contains(kernel)) then
            acc <- acc.Add(kernel)
        ...)

    acc |> Seq.toList
```

<span data-ttu-id="b5fd0-338">Lambda ifadesinin ortasındaki tek mutasyon noktasının yanı sıra, dokunan diğer tüm kodlar `acc` bunu normal `let`bağlı değişmez bir değerin kullanımından farklı olmayan bir şekilde yapabilir.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-338">Aside from the single point of mutation in the middle of the lambda expression, all other code that touches `acc` can do so in a manner that is no different to the usage of a normal `let`-bound immutable value.</span></span> <span data-ttu-id="b5fd0-339">Bu, zaman içinde değişmeyi kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-339">This will make it easier to change over time.</span></span>

## <a name="object-programming"></a><span data-ttu-id="b5fd0-340">Nesne programlama</span><span class="sxs-lookup"><span data-stu-id="b5fd0-340">Object programming</span></span>

<span data-ttu-id="b5fd0-341">F# nesneler ve nesne yönelimli (OO) kavramları için tam destek vardır.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-341">F# has full support for objects and object-oriented (OO) concepts.</span></span> <span data-ttu-id="b5fd0-342">Birçok OO kavramı güçlü ve kullanışlı olmasına rağmen, bunların hepsi kullanmak için ideal değildir.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-342">Although many OO concepts are powerful and useful, not all of them are ideal to use.</span></span> <span data-ttu-id="b5fd0-343">Aşağıdaki listeler, yüksek düzeyde OO özellikleri kategorileri hakkında rehberlik sunar.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-343">The following lists offer guidance on categories of OO features at a high level.</span></span>

<span data-ttu-id="b5fd0-344">**Bu özellikleri birçok durumda kullanmayı düşünün:**</span><span class="sxs-lookup"><span data-stu-id="b5fd0-344">**Consider using these features in many situations:**</span></span>

* <span data-ttu-id="b5fd0-345">Nokta gösterimi`x.Length`( )</span><span class="sxs-lookup"><span data-stu-id="b5fd0-345">Dot notation (`x.Length`)</span></span>
* <span data-ttu-id="b5fd0-346">Örnek üyeler</span><span class="sxs-lookup"><span data-stu-id="b5fd0-346">Instance members</span></span>
* <span data-ttu-id="b5fd0-347">Örtük yapıcılar</span><span class="sxs-lookup"><span data-stu-id="b5fd0-347">Implicit constructors</span></span>
* <span data-ttu-id="b5fd0-348">Statik üyeler</span><span class="sxs-lookup"><span data-stu-id="b5fd0-348">Static members</span></span>
* <span data-ttu-id="b5fd0-349">Dizinleyici gösterimi (`arr.[x]`)</span><span class="sxs-lookup"><span data-stu-id="b5fd0-349">Indexer notation (`arr.[x]`)</span></span>
* <span data-ttu-id="b5fd0-350">Adlandırılmış ve İsteğe Bağlı bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="b5fd0-350">Named and Optional arguments</span></span>
* <span data-ttu-id="b5fd0-351">Arayüzler ve arayüz uygulamaları</span><span class="sxs-lookup"><span data-stu-id="b5fd0-351">Interfaces and interface implementations</span></span>

<span data-ttu-id="b5fd0-352">**Önce bu özelliklere ulaşmayın, ancak bir sorunu çözmek için uygun olduklarında bunları akıllıca uygulayın:**</span><span class="sxs-lookup"><span data-stu-id="b5fd0-352">**Don't reach for these features first, but do judiciously apply them when they are convenient to solve a problem:**</span></span>

* <span data-ttu-id="b5fd0-353">Yöntem aşırı yükleme</span><span class="sxs-lookup"><span data-stu-id="b5fd0-353">Method overloading</span></span>
* <span data-ttu-id="b5fd0-354">Kapsüllenmiş mutable veriler</span><span class="sxs-lookup"><span data-stu-id="b5fd0-354">Encapsulated mutable data</span></span>
* <span data-ttu-id="b5fd0-355">Türler üzerinde operatörler</span><span class="sxs-lookup"><span data-stu-id="b5fd0-355">Operators on types</span></span>
* <span data-ttu-id="b5fd0-356">Otomatik özellikler</span><span class="sxs-lookup"><span data-stu-id="b5fd0-356">Auto properties</span></span>
* <span data-ttu-id="b5fd0-357">Uygulama `IDisposable` ve`IEnumerable`</span><span class="sxs-lookup"><span data-stu-id="b5fd0-357">Implementing `IDisposable` and `IEnumerable`</span></span>
* <span data-ttu-id="b5fd0-358">Tür uzantıları</span><span class="sxs-lookup"><span data-stu-id="b5fd0-358">Type extensions</span></span>
* <span data-ttu-id="b5fd0-359">Olaylar</span><span class="sxs-lookup"><span data-stu-id="b5fd0-359">Events</span></span>
* <span data-ttu-id="b5fd0-360">Yapılar</span><span class="sxs-lookup"><span data-stu-id="b5fd0-360">Structs</span></span>
* <span data-ttu-id="b5fd0-361">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="b5fd0-361">Delegates</span></span>
* <span data-ttu-id="b5fd0-362">Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="b5fd0-362">Enums</span></span>

<span data-ttu-id="b5fd0-363">**Genellikle bunları kullanmanız gerekir sürece bu özellikleri kaçının:**</span><span class="sxs-lookup"><span data-stu-id="b5fd0-363">**Generally avoid these features unless you must use them:**</span></span>

* <span data-ttu-id="b5fd0-364">Kalıtım tabanlı tür hiyerarşileri ve uygulama kalıtım</span><span class="sxs-lookup"><span data-stu-id="b5fd0-364">Inheritance-based type hierarchies and implementation inheritance</span></span>
* <span data-ttu-id="b5fd0-365">Nulls ve`Unchecked.defaultof<_>`</span><span class="sxs-lookup"><span data-stu-id="b5fd0-365">Nulls and `Unchecked.defaultof<_>`</span></span>

### <a name="prefer-composition-over-inheritance"></a><span data-ttu-id="b5fd0-366">Kalıtım yerine kompozisyonu tercih edin</span><span class="sxs-lookup"><span data-stu-id="b5fd0-366">Prefer composition over inheritance</span></span>

<span data-ttu-id="b5fd0-367">[Devralma üzerindeki kompozisyon,](https://en.wikipedia.org/wiki/Composition_over_inheritance) iyi F# kodunun yapışabileceği uzun süreli bir deyimdir.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-367">[Composition over inheritance](https://en.wikipedia.org/wiki/Composition_over_inheritance) is a long-standing idiom that good F# code can adhere to.</span></span> <span data-ttu-id="b5fd0-368">Temel ilke, bir taban sınıf ve işlevsellik almak için bu taban sınıftan devralmak için arayanlar zorlamak olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-368">The fundamental principle is that you should not expose a base class and force callers to inherit from that base class to get functionality.</span></span>

### <a name="use-object-expressions-to-implement-interfaces-if-you-dont-need-a-class"></a><span data-ttu-id="b5fd0-369">Bir sınıfa ihtiyacınız yoksa arabirimleri uygulamak için nesne ifadelerini kullanma</span><span class="sxs-lookup"><span data-stu-id="b5fd0-369">Use object expressions to implement interfaces if you don't need a class</span></span>

<span data-ttu-id="b5fd0-370">[Nesne İfadeleri,](../language-reference/object-expressions.md) uygulanan arabirimi bir sınıfın içinde yapmaya gerek kalmadan bir değere bağlayarak arabirimleri anında uygulamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-370">[Object Expressions](../language-reference/object-expressions.md) allow you to implement interfaces on the fly, binding the implemented interface to a value without needing to do so inside of a class.</span></span> <span data-ttu-id="b5fd0-371">Bu, özellikle _yalnızca_ arabirimi uygulamanız gerekiyorsa ve tam bir sınıfa ihtiyacınız yoksa kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-371">This is convenient, especially if you _only_ need to implement the interface and have no need for a full class.</span></span>

<span data-ttu-id="b5fd0-372">Örneğin, [ionide'de](http://ionide.io/) bir kod düzeltme eylemi `open` sağlamak için çalıştırılan kod aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="b5fd0-372">For example, here is the code that is run in [Ionide](http://ionide.io/) to provide a code fix action if you've added a symbol that you don't have an `open` statement for:</span></span>

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

<span data-ttu-id="b5fd0-373">Visual Studio Code API ile etkileşimde bulunmanız gerektiğinden, Nesne İfadeleri bunun için ideal bir araçtır.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-373">Because there is no need for a class when interacting with the Visual Studio Code API, Object Expressions are an ideal tool for this.</span></span> <span data-ttu-id="b5fd0-374">Bunlar, test rutinleri ile geçici bir şekilde bir arabirim saplamak istediğinizde, birim testi için de değerlidir.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-374">They are also valuable for unit testing, when you want to stub out an interface with test routines in an ad hoc manner.</span></span>

## <a name="consider-type-abbreviations-to-shorten-signatures"></a><span data-ttu-id="b5fd0-375">İmzaları kısaltmak için Tür Kısaltmalarını göz önünde bulundurun</span><span class="sxs-lookup"><span data-stu-id="b5fd0-375">Consider Type Abbreviations to shorten signatures</span></span>

<span data-ttu-id="b5fd0-376">[Tür kısaltmaları,](../language-reference/type-abbreviations.md) işlev imzası veya daha karmaşık bir tür gibi başka bir türe etiket atamanın kullanışlı bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-376">[Type Abbreviations](../language-reference/type-abbreviations.md) are a convenient way to assign a label to another type, such as a function signature or a more complex type.</span></span> <span data-ttu-id="b5fd0-377">Örneğin, aşağıdaki diğer ad, derin bir öğrenme kitaplığı olan [CNTK](https://docs.microsoft.com/cognitive-toolkit/)ile bir hesaplama tanımlamak için gerekenlere bir etiket atar:</span><span class="sxs-lookup"><span data-stu-id="b5fd0-377">For example, the following alias assigns a label to what's needed to define a computation with [CNTK](https://docs.microsoft.com/cognitive-toolkit/), a deep learning library:</span></span>

```fsharp
open CNTK

// DeviceDescriptor, Variable, and Function all come from CNTK
type Computation = DeviceDescriptor -> Variable -> Function
```

<span data-ttu-id="b5fd0-378">Ad, `Computation` diğer adla çalıştığı imzayla eşleşen herhangi bir işlevi belirtmek için kullanışlı bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-378">The `Computation` name is a convenient way to denote any function that matches the signature it is aliasing.</span></span> <span data-ttu-id="b5fd0-379">Bu gibi Tür Kısaltmalar kullanarak uygundur ve daha özlü kod sağlar.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-379">Using Type Abbreviations like this is convenient and allows for more succinct code.</span></span>

### <a name="avoid-using-type-abbreviations-to-represent-your-domain"></a><span data-ttu-id="b5fd0-380">Etki alanınızı temsil etmek için Tür Kısaltmalarını kullanmaktan kaçının</span><span class="sxs-lookup"><span data-stu-id="b5fd0-380">Avoid using Type Abbreviations to represent your domain</span></span>

<span data-ttu-id="b5fd0-381">Tür Kısaltmaları işlev imzalarına ad vermek için uygun olsa da, diğer türleri kısaltırken kafa karıştırıcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-381">Although Type Abbreviations are convenient for giving a name to function signatures, they can be confusing when abbreviating other types.</span></span> <span data-ttu-id="b5fd0-382">Bu kısaltmayı göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="b5fd0-382">Consider this abbreviation:</span></span>

```fsharp
// Does not actually abstract integers.
type BufferSize = int
```

<span data-ttu-id="b5fd0-383">Bu, birden çok şekilde kafa karıştırıcı olabilir:</span><span class="sxs-lookup"><span data-stu-id="b5fd0-383">This can be confusing in multiple ways:</span></span>

* <span data-ttu-id="b5fd0-384">`BufferSize`bir soyutlama değildir; bir tamsayı için sadece başka bir isimdir.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-384">`BufferSize` is not an abstraction; it is just another name for an integer.</span></span>
* <span data-ttu-id="b5fd0-385">`BufferSize` Genel bir API'de açıklanırsa, kolayca yanlış `int`yorumlanabilir.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-385">If `BufferSize` is exposed in a public API, it can easily be misinterpreted to mean more than just `int`.</span></span> <span data-ttu-id="b5fd0-386">Genellikle, etki alanı türleri onlara birden çok öznitelikleri var ve gibi `int`ilkel türleri değildir.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-386">Generally, domain types have multiple attributes to them and are not primitive types like `int`.</span></span> <span data-ttu-id="b5fd0-387">Bu kısaltma bu varsayımı ihlal eder.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-387">This abbreviation violates that assumption.</span></span>
* <span data-ttu-id="b5fd0-388">`BufferSize` (PascalCase) kasası, bu tür daha fazla veri tutar anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-388">The casing of `BufferSize` (PascalCase) implies that this type holds more data.</span></span>
* <span data-ttu-id="b5fd0-389">Bu diğer ad, bir işleve adlandırılmış bir bağımsız değişken sağlamayla karşılaştırıldığında daha fazla netlik sunmaz.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-389">This alias does not offer increased clarity compared with providing a named argument to a function.</span></span>
* <span data-ttu-id="b5fd0-390">Kısaltma derlenmiş IL'de tezahür etmeyecektir; sadece bir tamsayı ve bu takma ad bir derleme-zaman yapıdır.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-390">The abbreviation will not manifest in compiled IL; it is just an integer and this alias is a compile-time construct.</span></span>

```fsharp
module Networking =
    ...
    let send data (bufferSize: int) = ...
```

<span data-ttu-id="b5fd0-391">Özetle, Tür Kısaltmaları ile tuzak onlar kısaltma türleri üzerinde soyutlamalar **değildir.**</span><span class="sxs-lookup"><span data-stu-id="b5fd0-391">In summary, the pitfall with Type Abbreviations is that they are **not** abstractions over the types they are abbreviating.</span></span> <span data-ttu-id="b5fd0-392">Önceki örnekte, `BufferSize` sadece `int` bir kapakları altında, hiçbir ek veri ile, ne `int` de zaten ne yanında tip sisteminden herhangi bir yarar.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-392">In the previous example, `BufferSize` is just an `int` under the covers, with no additional data, nor any benefits from the type system besides what `int` already has.</span></span>

<span data-ttu-id="b5fd0-393">Bir etki alanını temsil etmek için tür kısaltmalarını kullanmaya alternatif bir yaklaşım, tek harfli ayrımcı birliş kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-393">An alternative approach to using type abbreviations to represent a domain is to use single-case discriminated unions.</span></span> <span data-ttu-id="b5fd0-394">Önceki örnek aşağıdaki gibi modellenebilir:</span><span class="sxs-lookup"><span data-stu-id="b5fd0-394">The previous sample can be modeled as follows:</span></span>

```fsharp
type BufferSize = BufferSize of int
```

<span data-ttu-id="b5fd0-395">Temel değeri `BufferSize` ve açısından çalışan kod yazarsanız, rasgele bir tamsayı da geçmek yerine bir kod oluşturmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="b5fd0-395">If you write code that operates in terms of `BufferSize` and its underlying value, you need to construct one rather than pass in any arbitrary integer:</span></span>

```fsharp
module Networking =
    ...
    let send data (BufferSize size) =
    ...
```

<span data-ttu-id="b5fd0-396">Bu, `send` istemci işlevi aramadan önce bir değeri sarmak için bir `BufferSize` tür oluşturması gerektiğinden, yanlışlıkla işleve rasgele bir tamsayı geçirme olasılığını azaltır.</span><span class="sxs-lookup"><span data-stu-id="b5fd0-396">This reduces the likelihood of mistakenly passing an arbitrary integer into the `send` function, because the caller must construct a `BufferSize` type to wrap a value before calling the function.</span></span>
