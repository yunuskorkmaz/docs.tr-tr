---
title: F#kodlama kuralları
description: Genel yönergeler ve deyimleri yazılırken öğrenin F# kod.
ms.date: 05/14/2018
ms.openlocfilehash: 1ef016184180eb8d233295e8985903e07693ad26
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61902141"
---
# <a name="f-coding-conventions"></a><span data-ttu-id="72024-103">F#kodlama kuralları</span><span class="sxs-lookup"><span data-stu-id="72024-103">F# coding conventions</span></span>

<span data-ttu-id="72024-104">Aşağıdaki kurallar ile büyük çalışma deneyiminden şeklide F# çıkabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="72024-104">The following conventions are formulated from experience working with large F# codebases.</span></span> <span data-ttu-id="72024-105">[Beş iyi prensipleri F# kod](index.md#five-principles-of-good-f-code) önerilerin temelidir.</span><span class="sxs-lookup"><span data-stu-id="72024-105">The [Five principles of good F# code](index.md#five-principles-of-good-f-code) are the foundation of each recommendation.</span></span> <span data-ttu-id="72024-106">İlişkili oldukları [ F# bileşen tasarım yönergeleri](component-design-guidelines.md), ancak için geçerli olan F# kod, kütüphane gibi değil yalnızca bileşenleri.</span><span class="sxs-lookup"><span data-stu-id="72024-106">They are related to the [F# component design guidelines](component-design-guidelines.md), but are applicable for any F# code, not just components such as libraries.</span></span>

## <a name="organizing-code"></a><span data-ttu-id="72024-107">Kod düzenleme</span><span class="sxs-lookup"><span data-stu-id="72024-107">Organizing code</span></span>

<span data-ttu-id="72024-108">F#kod düzenlemek için iki temel yol özellikleri: modüller ve ad alanları.</span><span class="sxs-lookup"><span data-stu-id="72024-108">F# features two primary ways to organize code: modules and namespaces.</span></span> <span data-ttu-id="72024-109">Bunlar, benzer, ancak kıyasla aşağıdaki farklılıklar vardır:</span><span class="sxs-lookup"><span data-stu-id="72024-109">These are similar, but do have the following differences:</span></span>

* <span data-ttu-id="72024-110">Ad alanları, .NET ad alanları derlenir.</span><span class="sxs-lookup"><span data-stu-id="72024-110">Namespaces are compiled as .NET namespaces.</span></span> <span data-ttu-id="72024-111">Modüller, statik sınıflar derlenir.</span><span class="sxs-lookup"><span data-stu-id="72024-111">Modules are compiled as static classes.</span></span>
* <span data-ttu-id="72024-112">Ad alanları, her zaman en üst düzey olur.</span><span class="sxs-lookup"><span data-stu-id="72024-112">Namespaces are always top level.</span></span> <span data-ttu-id="72024-113">Modüller, üst düzey ve diğer modüller içinde iç içe olabilir.</span><span class="sxs-lookup"><span data-stu-id="72024-113">Modules can be top-level and nested within other modules.</span></span>
* <span data-ttu-id="72024-114">Ad alanları, birden çok dosya yayılabilir.</span><span class="sxs-lookup"><span data-stu-id="72024-114">Namespaces can span multiple files.</span></span> <span data-ttu-id="72024-115">Modüller olamaz.</span><span class="sxs-lookup"><span data-stu-id="72024-115">Modules cannot.</span></span>
* <span data-ttu-id="72024-116">Modüller düzenlenmiş ile `[<RequireQualifiedAccess>]` ve `[<AutoOpen>]`.</span><span class="sxs-lookup"><span data-stu-id="72024-116">Modules can be decorated with `[<RequireQualifiedAccess>]` and `[<AutoOpen>]`.</span></span>

<span data-ttu-id="72024-117">Aşağıdaki yönergeler, kodunuzu düzenleme şeklinizdir için bunları kullanın yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="72024-117">The following guidelines will help you use these to organize your code.</span></span>

### <a name="prefer-namespaces-at-the-top-level"></a><span data-ttu-id="72024-118">Ad alanları en üst düzeyde tercih et</span><span class="sxs-lookup"><span data-stu-id="72024-118">Prefer namespaces at the top level</span></span>

<span data-ttu-id="72024-119">Genel olarak kullanılabilir herhangi bir kod için ad alanları en üst düzeyde modüllerine tercihe bağlı.</span><span class="sxs-lookup"><span data-stu-id="72024-119">For any publicly consumable code, namespaces are preferential to modules at the top level.</span></span> <span data-ttu-id="72024-120">.NET ad alanları derlenmiş olduğundan, hiçbir sorun C# ' tan tüketilebilir.</span><span class="sxs-lookup"><span data-stu-id="72024-120">Because they are compiled as .NET namespaces, they are consumable from C# with no issue.</span></span>

```fsharp
// Good!
namespace MyCode

type MyClass() =
    ...
```

<span data-ttu-id="72024-121">Üst düzey bir modül kullanarak görüntülenmeyebilir yalnızca çağrıldığında farklı F#, ancak C# Tüketiciler, Arayanların surprised nitelemek sağlayarak `MyClass` ile `MyCode` modülü.</span><span class="sxs-lookup"><span data-stu-id="72024-121">Using a top-level module may not appear different when called only from F#, but for C# consumers, callers may be surprised by having to qualify `MyClass` with the `MyCode` module.</span></span>

```fsharp
// Bad!
module MyCode

type MyClass() =
    ...
```

### <a name="carefully-apply-autoopen"></a><span data-ttu-id="72024-122">Dikkatli bir şekilde uygulama `[<AutoOpen>]`</span><span class="sxs-lookup"><span data-stu-id="72024-122">Carefully apply `[<AutoOpen>]`</span></span>

<span data-ttu-id="72024-123">`[<AutoOpen>]` Yapısı arayanlara kullanılabilir kapsamını pollute ve burada bir şey geldiği için yanıt "Sihirli".</span><span class="sxs-lookup"><span data-stu-id="72024-123">The `[<AutoOpen>]` construct can pollute the scope of what is available to callers, and the answer to where something comes from is "magic".</span></span> <span data-ttu-id="72024-124">Bu genellikle iyi bir şey değildir.</span><span class="sxs-lookup"><span data-stu-id="72024-124">This is generally not a good thing.</span></span> <span data-ttu-id="72024-125">Bu kuralın istisnası F# çekirdek kitaplığının kendisi (ancak bu durum ayrıca biraz tartışmalı).</span><span class="sxs-lookup"><span data-stu-id="72024-125">An exception to this rule is the F# Core Library itself (though this fact is also a bit controversial).</span></span>

<span data-ttu-id="72024-126">Ancak, düzenlemek için ayrı olarak bu genel API istediğiniz genel API için yardımcı işlevini varsa bir kullanışlı olur.</span><span class="sxs-lookup"><span data-stu-id="72024-126">However, it is a convenience if you have helper functionality for a public API that you wish to organize separately from that public API.</span></span>

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

<span data-ttu-id="72024-127">Bu işlem, bir yardımcı her çağırdığında tam olarak nitelemek zorunda kalmadan indrebilirsiniz ayrı uygulama ayrıntılarından bir işlevin Genel API sağlar.</span><span class="sxs-lookup"><span data-stu-id="72024-127">This lets you cleanly separate implementation details from the public API of a function without having to fully qualify a helper each time you call it.</span></span>

<span data-ttu-id="72024-128">Ayrıca, uzantı yöntemleri ve ifade oluşturucular ad alanı düzeyinde gösterme düzgünce ile ifade edilebilen `[<AutoOpen>]`.</span><span class="sxs-lookup"><span data-stu-id="72024-128">Additionally, exposing extension methods and expression builders at the namespace level can be neatly expressed with `[<AutoOpen>]`.</span></span>

### <a name="use-requirequalifiedaccess-whenever-names-could-conflict-or-you-feel-it-helps-with-readability"></a><span data-ttu-id="72024-129">Kullanım `[<RequireQualifiedAccess>]` her adları çakışıyor ya da düşündüğünüzü ile okunabilirliği yardımcı olur</span><span class="sxs-lookup"><span data-stu-id="72024-129">Use `[<RequireQualifiedAccess>]` whenever names could conflict or you feel it helps with readability</span></span>

<span data-ttu-id="72024-130">Ekleme `[<RequireQualifiedAccess>]` özniteliği bir modül için modülü açılamadı ve erişimi nitelenmiş modülünün öğelere başvurular açık gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="72024-130">Adding the `[<RequireQualifiedAccess>]` attribute to a module indicates that the module may not be opened and that references to the elements of the module require explicit qualified access.</span></span> <span data-ttu-id="72024-131">Örneğin, `Microsoft.FSharp.Collections.List` modülü, bu öznitelik içeriyor.</span><span class="sxs-lookup"><span data-stu-id="72024-131">For example, the `Microsoft.FSharp.Collections.List` module has this attribute.</span></span>

<span data-ttu-id="72024-132">İşlevleri ve değerleri modüldeki diğer modüllerin adlarla çakışma olasılığı adlara sahip olduğunda bu kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="72024-132">This is useful when functions and values in the module have names that are likely to conflict with names in other modules.</span></span> <span data-ttu-id="72024-133">Koşullu erişim gerektiren bir kitaplığı geliştirilebilirlik ve uzun vadede sürdürülebilirliğini önemli ölçüde artırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="72024-133">Requiring qualified access can greatly increase the long-term maintainability and evolvability of a library.</span></span>

```fsharp
[<RequireQualifiedAccess>]
module StringTokenization =
    let parse s = ...

...

let s = getAString()
let parsed = StringTokenization.parse s // Must qualify to use 'parse'
```

### <a name="sort-open-statements-topologically"></a><span data-ttu-id="72024-134">Sıralama `open` deyimleri topologically</span><span class="sxs-lookup"><span data-stu-id="72024-134">Sort `open` statements topologically</span></span>

<span data-ttu-id="72024-135">İçinde F#, bildirimleri önemli olan konuya, dahil olmak üzere sırasını `open` deyimleri.</span><span class="sxs-lookup"><span data-stu-id="72024-135">In F#, the order of declarations matters, including with `open` statements.</span></span> <span data-ttu-id="72024-136">Bu C#, burada etkisini `using` ve `using static` Bu deyimler bir dosyada sıralamasını bağımsızdır.</span><span class="sxs-lookup"><span data-stu-id="72024-136">This is unlike C#, where the effect of `using` and `using static` is independent of the ordering of those statements in a file.</span></span>

<span data-ttu-id="72024-137">İçinde F#, bir kapsama açılır öğe zaten mevcut bir diğer gölge.</span><span class="sxs-lookup"><span data-stu-id="72024-137">In F#, elements opened into a scope can shadow others already present.</span></span> <span data-ttu-id="72024-138">Yani bu yeniden sıralama `open` deyimleri kod anlamını alter.</span><span class="sxs-lookup"><span data-stu-id="72024-138">This means that reordering `open` statements could alter the meaning of code.</span></span> <span data-ttu-id="72024-139">Sonuç olarak, tüm sıralama her rastgele `open` deyimleri (örneğin, alfasayısal olarak) genellikle önerilmez, bekleyebileceğiniz farklı bir davranış oluşturmak ekleyin.</span><span class="sxs-lookup"><span data-stu-id="72024-139">As a result, any arbitrary sorting of all `open` statements (for example, alphanumerically) is generally not recommended, lest you generate different behavior that you might expect.</span></span>

<span data-ttu-id="72024-140">Bunun yerine, bunları sıralama öneririz [topologically](https://en.wikipedia.org/wiki/Topological_sorting); diğer bir deyişle, sipariş, `open` sırayı deyimlerinde _katmanları_ sisteminizi tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="72024-140">Instead, we recommend that you sort them [topologically](https://en.wikipedia.org/wiki/Topological_sorting); that is, order your `open` statements in the order in which _layers_ of your system are defined.</span></span> <span data-ttu-id="72024-141">Alfasayısal içindeki farklı topolojik katmanları sıralama yapmak da düşünülebilir.</span><span class="sxs-lookup"><span data-stu-id="72024-141">Doing alphanumeric sorting within different topological layers may also be considered.</span></span>

<span data-ttu-id="72024-142">Örneğin, işte topolojik sıralama için F# derleyici hizmeti ortak API dosyası:</span><span class="sxs-lookup"><span data-stu-id="72024-142">As an example, here is the topological sorting for the F# compiler service public API file:</span></span>

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

<span data-ttu-id="72024-143">Satır sonu alfasayısal olarak tüketmesi sıralanan her bir katman ile topolojik katmanları ayıran unutmayın.</span><span class="sxs-lookup"><span data-stu-id="72024-143">Note that a line break separates topological layers, with each layer being sorted alphanumerically afterwards.</span></span> <span data-ttu-id="72024-144">Bu düzgün bir şekilde kod değerleri gölgeleme olmadan yanlışlıkla düzenler.</span><span class="sxs-lookup"><span data-stu-id="72024-144">This cleanly organizes code without accidentally shadowing values.</span></span>

## <a name="use-classes-to-contain-values-that-have-side-effects"></a><span data-ttu-id="72024-145">Yan etkisi olan değerler içermesini sınıflarını kullanma</span><span class="sxs-lookup"><span data-stu-id="72024-145">Use classes to contain values that have side effects</span></span>

<span data-ttu-id="72024-146">Değer başlatma gibi bir bağlam için bir veritabanı veya başka bir uzak kaynağa örnekleme yan etkileri zaman olabilir birçok kez vardır.</span><span class="sxs-lookup"><span data-stu-id="72024-146">There are many times when initializing a value can have side effects, such as instantiating a context to a database or other remote resource.</span></span> <span data-ttu-id="72024-147">Modül içindeki gibi şeyler başlatıp sonraki işlevleri kullanmak için daha cazip bir:</span><span class="sxs-lookup"><span data-stu-id="72024-147">It is tempting to initialize such things in a module and use it in subsequent functions:</span></span>

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

<span data-ttu-id="72024-148">Sık kötü bir fikir birkaç nedeni budur:</span><span class="sxs-lookup"><span data-stu-id="72024-148">This is frequently a bad idea for a few reasons:</span></span>

<span data-ttu-id="72024-149">Uygulama yapılandırması tabanının ilk olarak, şekilde gönderildiğinde `dep1` ve `dep2`.</span><span class="sxs-lookup"><span data-stu-id="72024-149">First, application configuration is pushed into the codebase with `dep1` and `dep2`.</span></span> <span data-ttu-id="72024-150">Bu, büyük kod tabanlarında elde etmek zordur.</span><span class="sxs-lookup"><span data-stu-id="72024-150">This is difficult to maintain in larger codebases.</span></span>

<span data-ttu-id="72024-151">İkinci, statik olarak başlatılmış veri bileşeniniz kendisini birden çok iş parçacığı kullanacaksanız, iş parçacığı güvenli olmayan bir değer içermemelidir.</span><span class="sxs-lookup"><span data-stu-id="72024-151">Second, statically initialized data should not include values that are not thread safe if your component will itself use multiple threads.</span></span> <span data-ttu-id="72024-152">Bu açıkça tarafından ihlal `dep3`.</span><span class="sxs-lookup"><span data-stu-id="72024-152">This is clearly violated by `dep3`.</span></span>

<span data-ttu-id="72024-153">Son olarak, modül başlatma tüm derleme birimi için bir statik oluşturucuya derler.</span><span class="sxs-lookup"><span data-stu-id="72024-153">Finally, module initialization compiles into a static constructor for the entire compilation unit.</span></span> <span data-ttu-id="72024-154">Let bağlı değer başlatma bu modüldeki herhangi bir hata oluşması halinde olarak bildirimleri bir `TypeInitializationException` , ardından önbelleğe alınma tüm uygulama ömrü boyunca.</span><span class="sxs-lookup"><span data-stu-id="72024-154">If any error occurs in let-bound value initialization in that module, it manifests as a `TypeInitializationException` that is then cached for the entire lifetime of the application.</span></span> <span data-ttu-id="72024-155">Bu tanı koymak güç olabilir.</span><span class="sxs-lookup"><span data-stu-id="72024-155">This can be difficult to diagnose.</span></span> <span data-ttu-id="72024-156">Genellikle bir iç özel durum hakkında neden girişiminde bulunabilirsiniz yoktur ancak ardından yoksa, hiçbir belirten kök nedeni nedir yok.</span><span class="sxs-lookup"><span data-stu-id="72024-156">There is usually an inner exception that you can attempt to reason about, but if there is not, then there is no telling what the root cause is.</span></span>

<span data-ttu-id="72024-157">Bunun yerine, bağımlılıkları tutmak için yalnızca basit bir sınıfı kullanın:</span><span class="sxs-lookup"><span data-stu-id="72024-157">Instead, just use a simple class to hold dependencies:</span></span>

```fsharp
type MyParametricApi(dep1, dep2, dep3) =
    member __.Function1 arg1 = doStuffWith dep1 dep2 dep3 arg1
    member __.Function2 arg2 = doStuffWith dep1 dep2 dep3 arg2
```

<span data-ttu-id="72024-158">Bu aşağıdakileri sağlar:</span><span class="sxs-lookup"><span data-stu-id="72024-158">This enables the following:</span></span>

1. <span data-ttu-id="72024-159">API dışında herhangi bir bağımlı durumu İletiliyor.</span><span class="sxs-lookup"><span data-stu-id="72024-159">Pushing any dependent state outside of the API itself.</span></span>
2. <span data-ttu-id="72024-160">Yapılandırma, artık API dışında yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="72024-160">Configuration can now be done outside of the API.</span></span>
3. <span data-ttu-id="72024-161">Bağımlı değerleri için başlatma hataları olarak bildirim olasılığı olmayan bir `TypeInitializationException`.</span><span class="sxs-lookup"><span data-stu-id="72024-161">Errors in initialization for dependent values are not likely to manifest as a `TypeInitializationException`.</span></span>
4. <span data-ttu-id="72024-162">API, artık test etmek daha kolay olur.</span><span class="sxs-lookup"><span data-stu-id="72024-162">The API is now easier to test.</span></span>

## <a name="error-management"></a><span data-ttu-id="72024-163">Hata Yönetimi</span><span class="sxs-lookup"><span data-stu-id="72024-163">Error management</span></span>

<span data-ttu-id="72024-164">Hata Yönetimi sistemlerinde büyük olan karmaşık ve incelikli bir çaba ve sistemlerinizi sağlamak madde işaretleri de yapılandıran ve hataya dayanıklı hiçbir silver vardır.</span><span class="sxs-lookup"><span data-stu-id="72024-164">Error management in large systems is a complex and nuanced endeavor, and there are no silver bullets in ensuring your systems are fault-tolerant and behave well.</span></span> <span data-ttu-id="72024-165">Aşağıdaki yönergeler bu zor alanı gezinme kılavuzluk sunmalıdır.</span><span class="sxs-lookup"><span data-stu-id="72024-165">The following guidelines should offer guidance in navigating this difficult space.</span></span>

### <a name="represent-error-cases-and-illegal-state-in-types-intrinsic-to-your-domain"></a><span data-ttu-id="72024-166">Hata durumları ve etki alanınızı iç türleri geçersiz durumda temsil eder</span><span class="sxs-lookup"><span data-stu-id="72024-166">Represent error cases and illegal state in types intrinsic to your domain</span></span>

<span data-ttu-id="72024-167">İle [ayırt edici birleşimler](../language-reference/discriminated-unions.md), F# hatalı program durumunu temsil eden tür sisteminizdeki olanağı sağlar.</span><span class="sxs-lookup"><span data-stu-id="72024-167">With [Discriminated Unions](../language-reference/discriminated-unions.md), F# gives you the ability to represent faulty program state in your type system.</span></span> <span data-ttu-id="72024-168">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="72024-168">For example:</span></span>

```fsharp
type MoneyWithdrawalResult =
    | Success of amount:decimal
    | InsufficientFunds of balance:decimal
    | CardExpired of DateTime
    | UndisclosedFailure
```

<span data-ttu-id="72024-169">Bu durumda, bir banka hesaptan para geri alınmasının başarısız olabilir ve bilinen üç yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="72024-169">In this case, there are three known ways that withdrawing money from a bank account can fail.</span></span> <span data-ttu-id="72024-170">Her bir hata durumu yazıyla gösterilir ve bu nedenle ile güvenli bir şekilde programın tamamında alınabilir.</span><span class="sxs-lookup"><span data-stu-id="72024-170">Each error case is represented in the type, and can thus be dealt with safely throughout the program.</span></span>

```fsharp
let handleWithdrawal amount =
    let w = withdrawMoney amount
    match w with
    | Success am -> printfn "Successfully withdrew %f" am
    | InsufficientFunds balance -> printfn "Failed: balance is %f" balance
    | CardExpired expiredDate -> printfn "Failed: card expired on %O" expiredDate
    | UndisclosedFailure -> printfn "Failed: unknown"
```

<span data-ttu-id="72024-171">Bu sorun genel olarak, farklı şekilde modelleyebilir, yapabilirsiniz **başarısız** etki alanınızda sonra hata işleme kodunu artık sorun, gereken işlem ile ek olarak normal program akışı olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="72024-171">In general, if you can model the different ways that something can **fail** in your domain, then error handling code is no longer treated as something you must deal with in addition to regular program flow.</span></span> <span data-ttu-id="72024-172">Yalnızca normal program akışı bir parçasıdır ve dikkate alınmaz **olağanüstü**.</span><span class="sxs-lookup"><span data-stu-id="72024-172">It is simply a part of normal program flow, and not considered **exceptional**.</span></span> <span data-ttu-id="72024-173">Bu iki adet birincil avantaj vardır:</span><span class="sxs-lookup"><span data-stu-id="72024-173">There are two primary benefits to this:</span></span>

1. <span data-ttu-id="72024-174">Etki alanınızı zamanla değiştikçe korumak daha kolaydır.</span><span class="sxs-lookup"><span data-stu-id="72024-174">It is easier to maintain as your domain changes over time.</span></span>
2. <span data-ttu-id="72024-175">Hata durumları birim testine daha kolaydır.</span><span class="sxs-lookup"><span data-stu-id="72024-175">Error cases are easier to unit test.</span></span>

### <a name="use-exceptions-when-errors-cannot-be-represented-with-types"></a><span data-ttu-id="72024-176">Hata türleri ile gösterilemez durumlarda özel durumları kullanın</span><span class="sxs-lookup"><span data-stu-id="72024-176">Use exceptions when errors cannot be represented with types</span></span>

<span data-ttu-id="72024-177">Bir sorun etki alanındaki tüm hataları temsil edilebilir.</span><span class="sxs-lookup"><span data-stu-id="72024-177">Not all errors can be represented in a problem domain.</span></span> <span data-ttu-id="72024-178">Bu türde hataları *olağanüstü* yapısı, bu nedenle yükseltmek ve özel durumları yakalama olanağı F#.</span><span class="sxs-lookup"><span data-stu-id="72024-178">These kinds of faults are *exceptional* in nature, hence the ability to raise and catch exceptions in F#.</span></span>

<span data-ttu-id="72024-179">İlk olarak, okumanızı önerilir [özel tasarım yönergeleri](../../standard/design-guidelines/exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="72024-179">First, it is recommended that you read the [Exception Design Guidelines](../../standard/design-guidelines/exceptions.md).</span></span> <span data-ttu-id="72024-180">Bu da geçerli olan F#.</span><span class="sxs-lookup"><span data-stu-id="72024-180">These are also applicable to F#.</span></span>

<span data-ttu-id="72024-181">Ana bulunan yapıları F# özel durumlarını oluşturma amacıyla aşağıdaki tercih sırasına göre değerlendirilmesi için:</span><span class="sxs-lookup"><span data-stu-id="72024-181">The main constructs available in F# for the purposes of raising exceptions should be considered in the following order of preference:</span></span>

| <span data-ttu-id="72024-182">İşlev</span><span class="sxs-lookup"><span data-stu-id="72024-182">Function</span></span> | <span data-ttu-id="72024-183">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="72024-183">Syntax</span></span> | <span data-ttu-id="72024-184">Amaç</span><span class="sxs-lookup"><span data-stu-id="72024-184">Purpose</span></span> |
|----------|--------|---------|
| `nullArg` | `nullArg "argumentName"` | <span data-ttu-id="72024-185">Oluşturur bir `System.ArgumentNullException` ile belirtilen bağımsız değişken adı.</span><span class="sxs-lookup"><span data-stu-id="72024-185">Raises a `System.ArgumentNullException` with the specified argument name.</span></span> |
| `invalidArg` | `invalidArg "argumentName" "message"` | <span data-ttu-id="72024-186">Oluşturur bir `System.ArgumentException` belirtilen bağımsız değişken adı ve ileti.</span><span class="sxs-lookup"><span data-stu-id="72024-186">Raises a `System.ArgumentException` with a specified argument name and message.</span></span> |
| `invalidOp` | `invalidOp "message"` | <span data-ttu-id="72024-187">Oluşturur bir `System.InvalidOperationException` belirtilen ileti.</span><span class="sxs-lookup"><span data-stu-id="72024-187">Raises a `System.InvalidOperationException` with the specified message.</span></span> |
|`raise`| `raise (ExceptionType("message"))` | <span data-ttu-id="72024-188">Özel durumları atma için genel amaçlı mekanizması.</span><span class="sxs-lookup"><span data-stu-id="72024-188">General-purpose mechanism for throwing exceptions.</span></span> |
| `failwith` | `failwith "message"` | <span data-ttu-id="72024-189">Oluşturur bir `System.Exception` belirtilen ileti.</span><span class="sxs-lookup"><span data-stu-id="72024-189">Raises a `System.Exception` with the specified message.</span></span> |
| `failwithf` | `failwithf "format string" argForFormatString` | <span data-ttu-id="72024-190">Oluşturur bir `System.Exception` Biçim dizesinden veya girdilerinden tarafından belirlenen bir ileti ile.</span><span class="sxs-lookup"><span data-stu-id="72024-190">Raises a `System.Exception` with a message determined by the format string and its inputs.</span></span> |

<span data-ttu-id="72024-191">Kullanım `nullArg`, `invalidArg` ve `invalidOp` durum için bir mekanizma olarak `ArgumentNullException`, `ArgumentException` ve `InvalidOperationException` uygun olduğunda.</span><span class="sxs-lookup"><span data-stu-id="72024-191">Use `nullArg`, `invalidArg` and `invalidOp` as the mechanism to throw `ArgumentNullException`, `ArgumentException` and `InvalidOperationException` when appropriate.</span></span>

<span data-ttu-id="72024-192">`failwith` Ve `failwithf` işlevleri, genellikle bunlar temel çünkü kaçınılmalıdır `Exception` türü, bir özel durum.</span><span class="sxs-lookup"><span data-stu-id="72024-192">The `failwith` and `failwithf` functions should generally be avoided because they raise the base `Exception` type, not a specific exception.</span></span> <span data-ttu-id="72024-193">Olarak başına [özel tasarım yönergeleri](../../standard/design-guidelines/exceptions.md), mümkün olduğunda daha belirli özel durumları yükseltmek istediğiniz.</span><span class="sxs-lookup"><span data-stu-id="72024-193">As per the [Exception Design Guidelines](../../standard/design-guidelines/exceptions.md), you want to raise more specific exceptions when you can.</span></span>

### <a name="using-exception-handling-syntax"></a><span data-ttu-id="72024-194">Özel durum işleme sözdizimini kullanarak</span><span class="sxs-lookup"><span data-stu-id="72024-194">Using exception-handling syntax</span></span>

<span data-ttu-id="72024-195">F#özel durum desenleri aracılığıyla destekler `try...with` söz dizimi:</span><span class="sxs-lookup"><span data-stu-id="72024-195">F# supports exception patterns via the `try...with` syntax:</span></span>

```fsharp
try
    tryGetFileContents()
with
| :? System.IO.FileNotFoundException as e -> // Do something with it here
| :? System.Security.SecurityException as e -> // Do something with it here
```

<span data-ttu-id="72024-196">Bir özel durum desen eşleştirme ile karşılaşıldığında gerçekleştirmek için işlevleri karşılaştırma kodu temiz tutmak istiyorsanız biraz zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="72024-196">Reconciling functionality to perform in the face of an exception with pattern matching can be a bit tricky if you wish to keep the code clean.</span></span> <span data-ttu-id="72024-197">Bu durumu çözmek için bir tür kullanmaktır [Etkin desenler](../language-reference/active-patterns.md) grubu işlev bir özel bir hata durumuyla çevreleyen yöntemi olarak.</span><span class="sxs-lookup"><span data-stu-id="72024-197">One such way to handle this is to use [active patterns](../language-reference/active-patterns.md) as a means to group functionality surrounding an error case with an exception itself.</span></span> <span data-ttu-id="72024-198">Örneğin, bir özel durum oluşturduğunda, özel durum meta verilerde değerli bilgiler kapsayan bir API kullanan.</span><span class="sxs-lookup"><span data-stu-id="72024-198">For example, you may be consuming an API that, when it throws an exception, encloses valuable information in the exception metadata.</span></span> <span data-ttu-id="72024-199">Yakalanan özel durumun etkin desen içinde gövdesinde yararlı bir değer çözülme ve döndürme değeri bazı durumlarda yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="72024-199">Unwrapping a useful value in the body of the captured exception inside the Active Pattern and returning that value can be helpful in some situations.</span></span>

### <a name="do-not-use-monadic-error-handling-to-replace-exceptions"></a><span data-ttu-id="72024-200">Birli hata özel durum değiştirmek için işleme kullanmayın</span><span class="sxs-lookup"><span data-stu-id="72024-200">Do not use monadic error handling to replace exceptions</span></span>

<span data-ttu-id="72024-201">Özel durumlar, biraz taboo işlevsel programlama olarak görülür.</span><span class="sxs-lookup"><span data-stu-id="72024-201">Exceptions are seen as somewhat taboo in functional programming.</span></span> <span data-ttu-id="72024-202">Aslında, sessiz değil işlevsel dikkate alınması gereken güvenli olacak şekilde özel durumları saflığa, ihlal ediyor.</span><span class="sxs-lookup"><span data-stu-id="72024-202">Indeed, exceptions violate purity, so it's safe to consider them not-quite functional.</span></span> <span data-ttu-id="72024-203">Ancak, bu kodu çalıştırdığı gerekir ve bu çalışma zamanı hataları oluşabilir gerçeklik yok sayar.</span><span class="sxs-lookup"><span data-stu-id="72024-203">However, this ignores the reality of where code must run, and that runtime errors can occur.</span></span> <span data-ttu-id="72024-204">Genel olarak, bilgilerin çoğunu saf ne sürprizlerden en aza indirmek için toplam varsayımına kod yazın.</span><span class="sxs-lookup"><span data-stu-id="72024-204">In general, write code on the assumption that most things are neither pure nor total, to minimize unpleasant surprises.</span></span>

<span data-ttu-id="72024-205">Aşağıdaki çekirdek güçlü/yönlerini özel durumlar, ilgi düzeyi ve bir bütün olarak site .NET çalışma zamanı ve diller arası ekosistemi ile ilgili göz önünde bulundurmanız önemlidir:</span><span class="sxs-lookup"><span data-stu-id="72024-205">It is important to consider the following core strengths/aspects of Exceptions with respect to their relevance and appropriateness in the .NET runtime and cross-language ecosystem as a whole:</span></span>

1. <span data-ttu-id="72024-206">Soruna hata ayıklanırken çok yararlı olan ayrıntılı tanılama bilgileri içerirler.</span><span class="sxs-lookup"><span data-stu-id="72024-206">They contain detailed diagnostic information, which is very helpful when debugging an issue.</span></span>
2. <span data-ttu-id="72024-207">Bunlar, çalışma zamanı ve diğer .NET dilleri tarafından anlaşılır.</span><span class="sxs-lookup"><span data-stu-id="72024-207">They are well-understood by the runtime and other .NET languages.</span></span>
3. <span data-ttu-id="72024-208">Bunlar giden yolu dışında bir kod ile karşılaştırıldığında önemli Demirbaş azaltabilir *önlemek* bir geçici olarak kendi semantiği bazı alt kümesi uygulayarak özel durumlar.</span><span class="sxs-lookup"><span data-stu-id="72024-208">They can reduce significant boilerplate when compared with code that goes out of its way to *avoid* exceptions by implementing some subset of their semantics on an ad-hoc basis.</span></span>

<span data-ttu-id="72024-209">Bu üçüncü noktasını, kritik öneme sahiptir.</span><span class="sxs-lookup"><span data-stu-id="72024-209">This third point is critical.</span></span> <span data-ttu-id="72024-210">Ölçeklenebilmesi kolay karmaşık işlemlerinde, özel durumlar kullanma başarısız yapıları şöyle uğraşmanızı neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="72024-210">For nontrivial complex operations, failing to use exceptions can result in dealing with structures like this:</span></span>

```fsharp
Result<Result<MyType, string>, string list>
```

<span data-ttu-id="72024-211">Hangi kolayca kırılgan kod hatalarını "yazılı stringly" desen gibi neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="72024-211">Which can easily lead to fragile code like pattern matching on "stringly-typed" errors:</span></span>

```fsharp
let result = doStuff()
match result with
| Ok r -> ...
| Error e ->
    if e.Contains "Error string 1" then ...
    elif e.Contains "Error string 2" then ...
    else ... // Who knows?
```

<span data-ttu-id="72024-212">Ayrıca, gizliliğinizi korumayı taahhüt eder "daha Hoş görünmesi" türü döndüren "Basit" işlevi için herhangi bir özel swallow cazip olabilir:</span><span class="sxs-lookup"><span data-stu-id="72024-212">Additionally, it can be tempting to swallow any exception in the desire for a "simple" function that returns a "nicer" type:</span></span>

```fsharp
// This is bad!
let tryReadAllText (path : string) =
    try System.IO.File.ReadAllText path |> Some
    with _ -> None
```

<span data-ttu-id="72024-213">Ne yazık ki `tryReadAllText` çok sayıda dosya sisteminde oluşabilir şeyler dayalı çok sayıda özel durumlar oluşturabilecek ve bu kodu gerçekten yanlış ortamınızda neler hakkında bilgi hemen atar.</span><span class="sxs-lookup"><span data-stu-id="72024-213">Unfortunately, `tryReadAllText` can throw numerous exceptions based on the myriad of things that can happen on a file system, and this code discards away any information about what might actually be going wrong in your environment.</span></span> <span data-ttu-id="72024-214">Ardından bu kod bir sonuç türü değiştirirseniz, "yazılı stringly" hata iletisini geri ayrıştırma için duyuyoruz:</span><span class="sxs-lookup"><span data-stu-id="72024-214">If you replace this code with a result type, then you're back to "stringly-typed" error message parsing:</span></span>

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

<span data-ttu-id="72024-215">Ve özel durum nesnesi içinde `Error` Oluşturucusu yalnızca zorlar sizin için doğru çağrı sitesinde yerine işlev özel durum türüne sahip.</span><span class="sxs-lookup"><span data-stu-id="72024-215">And placing the exception object itself in the `Error` constructor just forces you to properly deal with the exception type at the call site rather than in the function.</span></span> <span data-ttu-id="72024-216">Etkili bir şekilde bunu bir API'yi çağıran çalışılabilecek öğesinin unfun işaretli özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="72024-216">Doing this effectively creates checked exceptions, which are notoriously unfun to deal with as a caller of an API.</span></span>

<span data-ttu-id="72024-217">Yukarıdaki örneklerde iyi bir alternatif yakalamaktır *belirli* özel durumlar ve o özel durumu bağlamında anlamlı bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="72024-217">A good alternative to the above examples is to catch *specific* exceptions and return a meaningful value in the context of that exception.</span></span> <span data-ttu-id="72024-218">Değiştirirseniz `tryReadAllText` aşağıdaki gibi işlev `None` daha fazla anlamı vardır:</span><span class="sxs-lookup"><span data-stu-id="72024-218">If you modify the `tryReadAllText` function as follows, `None` has more meaning:</span></span>

```fsharp
let tryReadAllTextIfPresent (path : string) =
    try System.IO.File.ReadAllText path |> Some
    with :? FileNotFoundException -> None
```

<span data-ttu-id="72024-219">Bir dosya bulunamadı ve bu anlamı atamak için bir dönüş catch tümünü olarak çalışması için yerine, bu işlev artık düzgün şekilde çalışması işler.</span><span class="sxs-lookup"><span data-stu-id="72024-219">Instead of functioning as a catch-all, this function will now properly handle the case when a file was not found and assign that meaning to a return.</span></span> <span data-ttu-id="72024-220">Bu dönüş değeri, bağlamsal bilgileri atılıyor veya bu noktada kod içinde ilgili olmayabilir bir servis talebi uğraşmanız çağıranlar zorlama sırasında bu hata çalışmasına eşleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="72024-220">This return value can map to that error case, while not discarding any contextual information or forcing callers to deal with a case that may not be relevant at that point in the code.</span></span>

<span data-ttu-id="72024-221">Gibi türleri `Result<'Success, 'Error>` nerede bunlar iç içe değil, temel işlemleri için uygun olan ve F# zamanı temsil eden bir şey olabilir ya da iade için isteğe bağlı türler mükemmel *bir şey* veya *hiçbirşey*.</span><span class="sxs-lookup"><span data-stu-id="72024-221">Types such as `Result<'Success, 'Error>` are appropriate for basic operations where they aren't nested, and F# optional types are perfect for representing when something could either return *something* or *nothing*.</span></span> <span data-ttu-id="72024-222">Bunlar özel durumlar yerine değil ve bir özel durum değiştirmek için kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="72024-222">They are not a replacement for exceptions, though, and should not be used in an attempt to replace exceptions.</span></span> <span data-ttu-id="72024-223">Bunun yerine, bunlar bozacağından adresi belirli yönlerini özel durum ve hata yönetimi ilkesi için hedeflenen şekilde uygulanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="72024-223">Rather, they should be applied judiciously to address specific aspects of exception and error management policy in targeted ways.</span></span>

## <a name="partial-application-and-point-free-programming"></a><span data-ttu-id="72024-224">Kısmi uygulama ve programlama noktası-ücretsiz</span><span class="sxs-lookup"><span data-stu-id="72024-224">Partial application and point-free programming</span></span>

<span data-ttu-id="72024-225">F#Kısmi uygulama ve bu nedenle, program için çeşitli yollar noktası içermeyen bir stilde destekler.</span><span class="sxs-lookup"><span data-stu-id="72024-225">F# supports partial application, and thus, various ways to program in a point-free style.</span></span> <span data-ttu-id="72024-226">Bu modül veya bir şeyin uygulama içinde kodun yeniden yararlı olabilir, ancak genellikle genel olarak kullanıma sunmak için bir şey değildir.</span><span class="sxs-lookup"><span data-stu-id="72024-226">This can be beneficial for code reuse within a module or the implementation of something, but it is generally not something to expose publicly.</span></span> <span data-ttu-id="72024-227">Genel olarak, noktası ücretsiz programlama içinde ve kendisinin bir virtue değil ve bilişsel ciddi bir engel stilde sarmalanmış şekilde olmayan kişiler için ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="72024-227">In general, point-free programming is not a virtue in and of itself, and can add a significant cognitive barrier for people who are not immersed in the style.</span></span>

### <a name="do-not-use-partial-application-and-currying-in-public-apis"></a><span data-ttu-id="72024-228">Kısmi uygulama ve genel API'ler currying kullanmayın</span><span class="sxs-lookup"><span data-stu-id="72024-228">Do not use partial application and currying in public APIs</span></span>

<span data-ttu-id="72024-229">Az özel durumla ortak API'lerde kısmi uygulama kullanımını Tüketiciler için kafa karıştırıcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="72024-229">With little exception, the use of partial application in public APIs can be confusing for consumers.</span></span> <span data-ttu-id="72024-230">Genellikle, `let`-bağlı değerleri F# kodu **değerleri**değil **işlev değerleri**.</span><span class="sxs-lookup"><span data-stu-id="72024-230">Usually, `let`-bound values in F# code are **values**, not **function values**.</span></span> <span data-ttu-id="72024-231">Değerleri ve işlev değerleri birlikte karıştırma sonuçlanabilir bilişsel ek yükü, olayın lisanslarınıza kod satırlarını az sayıda kaydedilirken gibi özellikle işleçleri ile birleştirildiğinde `>>` işlevleri oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="72024-231">Mixing together values and function values can result in saving a small number of lines of code in exchange for quite a bit of cognitive overhead, especially if combined with operators such as `>>` to compose functions.</span></span>

### <a name="consider-the-tooling-implications-for-point-free-programming"></a><span data-ttu-id="72024-232">Programlama noktası ücretsiz araçları etkilerini göz önünde bulundurun</span><span class="sxs-lookup"><span data-stu-id="72024-232">Consider the tooling implications for point-free programming</span></span>

<span data-ttu-id="72024-233">Curried işlevleri kendi bir bağımsız değişken etiket değil.</span><span class="sxs-lookup"><span data-stu-id="72024-233">Curried functions do not label their arguments.</span></span> <span data-ttu-id="72024-234">Bu etkileri araçlarına sahiptir.</span><span class="sxs-lookup"><span data-stu-id="72024-234">This has tooling implications.</span></span> <span data-ttu-id="72024-235">Aşağıdaki iki işlevi göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="72024-235">Consider the following two functions:</span></span>

```fsharp
let func name age =
    printfn "My name is %s and I am %d years old!" name age

let funcWithApplication =
    printfn "My name is %s and I am %d years old!"
```

<span data-ttu-id="72024-236">Her ikisi de geçerli işlevleri olan ancak `funcWithApplication` curried bir işlevdir.</span><span class="sxs-lookup"><span data-stu-id="72024-236">Both are valid functions, but `funcWithApplication` is a curried function.</span></span> <span data-ttu-id="72024-237">Bir düzenleyicide türleri üzerine geldiğinizde, şunu görürsünüz:</span><span class="sxs-lookup"><span data-stu-id="72024-237">When you hover over their types in an editor, you see this:</span></span>

```fsharp
val func : name:string -> age:int -> unit

val funcWithApplication : (string -> int -> unit)
```

<span data-ttu-id="72024-238">Çağıran sitede, Visual Studio gibi bir araç ipuçlarında, anlamlı bilgiler ne vermeyiz `string` ve `int` giriş türleri gerçekten temsil eder.</span><span class="sxs-lookup"><span data-stu-id="72024-238">At the call site, tooltips in tooling such as Visual Studio will not give you meaningful information as to what the `string` and `int` input types actually represent.</span></span>

<span data-ttu-id="72024-239">Kod noktası ücretsiz gibi karşılaşırsanız `funcWithApplication` , genel olarak kullanılabilir, bu araçları çekme yukarı bağımsız değişkenleri için anlamlı adlar devam bir tam η genişletme için yapmanız gerekenleri önerilir.</span><span class="sxs-lookup"><span data-stu-id="72024-239">If you encounter point-free code like `funcWithApplication` that is publicly consumable, it is recommended to do a full η-expansion so that tooling can pick up on meaningful names for arguments.</span></span>

<span data-ttu-id="72024-240">Ayrıca, kod noktası sorunsuz hata ayıklama, imkansız değilse zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="72024-240">Furthermore, debugging point-free code can be challenging, if not impossible.</span></span> <span data-ttu-id="72024-241">Hata ayıklama araçları kullanan adlarına bağlı değerleri (örneğin, `let` bağlamaları) yürütme aracılığıyla Ara değerleri midway inceleyebilmeniz.</span><span class="sxs-lookup"><span data-stu-id="72024-241">Debugging tools rely on values bound to names (for example, `let` bindings) so that you can inspect intermediate values midway through execution.</span></span> <span data-ttu-id="72024-242">Kodunuzu incelemek için hiçbir değer olduğunda, hata ayıklamak için hiçbir şey yoktur.</span><span class="sxs-lookup"><span data-stu-id="72024-242">When your code has no values to inspect, there is nothing to debug.</span></span> <span data-ttu-id="72024-243">Gelecekte, hata ayıklama araçları evrim Geçiren kullanıp bu değerler daha önce yürütülen yollarına dayalı, ancak üzerinde kaynak yatırımlarınızın karşılığını hedge iyi bir fikir değil *olası* işlevleri hata ayıklama.</span><span class="sxs-lookup"><span data-stu-id="72024-243">In the future, debugging tools may evolve to synthesize these values based on previously executed paths, but it's not a good idea to hedge your bets on *potential* debugging functionality.</span></span>

### <a name="consider-partial-application-as-a-technique-to-reduce-internal-boilerplate"></a><span data-ttu-id="72024-244">Kısmi uygulama yöntemi olarak iç karmaşıklığın azaltılmasına göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="72024-244">Consider partial application as a technique to reduce internal boilerplate</span></span>

<span data-ttu-id="72024-245">Önceki bir noktaya aksine, ortak bir uygulama ya da daha ayrıntılı bir API içyüzü içinde azaltmak için harika bir araç kısmi uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="72024-245">In contrast to the previous point, partial application is a wonderful tool for reducing boilerplate inside of an application or the deeper internals of an API.</span></span> <span data-ttu-id="72024-246">Birim testi Demirbaş genellikle uğraşmanız bir sorun olduğu, daha karmaşık bir API uygulaması için yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="72024-246">It can be helpful for unit testing the implementation of more complicated APIs, where boilerplate is often a pain to deal with.</span></span> <span data-ttu-id="72024-247">Örneğin, bu tür bir Framework'te dış bağımlılık yapmadan nasıl yapabileceğinizle aşağıdaki kodun gösterdiği en sahte hangi çerçeveleri, verin ve API bespoke ilgili öğrenmek zorunda.</span><span class="sxs-lookup"><span data-stu-id="72024-247">For example, the following code shows how you can accomplish what most mocking frameworks give you without taking an external dependency on such a framework and having to learn a related bespoke API.</span></span>

<span data-ttu-id="72024-248">Örneğin, aşağıdaki çözümü topografi göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="72024-248">For example, consider the following solution topography:</span></span>

```
MySolution.sln
|_/ImplementationLogic.fsproj
|_/ImplementationLogic.Tests.fsproj
|_/API.fsproj
```

<span data-ttu-id="72024-249">`ImplementationLogic.fsproj` kod kullanıma sunma gibi:</span><span class="sxs-lookup"><span data-stu-id="72024-249">`ImplementationLogic.fsproj` might expose code such as:</span></span>

```fsharp
module Transactions =
    let doTransaction txnContext txnType balance =
        ...

type Transactor(ctx, currentBalance) =
    member __.ExecuteTransaction(txnType) =
        Transactions.doTransaction ctx txtType currentBalance
        ...
```

<span data-ttu-id="72024-250">Birim testi `Transactions.doTransaction` içinde `ImplementationLogic.Tests.fspoj` kolaydır:</span><span class="sxs-lookup"><span data-stu-id="72024-250">Unit testing `Transactions.doTransaction` in `ImplementationLogic.Tests.fspoj` is easy:</span></span>

```fsharp
namespace TransactionsTestingUtil

open Transactions

module TransactionsTestable =
    let getTestableTransactionRoutine mockContext = Transactions.doTransaction mockContext
```

<span data-ttu-id="72024-251">Kısmen uygulama `doTransaction` işlevi tüm Birim testlerinizin her zaman sahte bir bağlam oluşturmak zorunda kalmadan çağırın ile sahte bir bağlam nesnesi sağlar:</span><span class="sxs-lookup"><span data-stu-id="72024-251">Partially applying `doTransaction` with a mocking context object lets you call the function in all of your unit tests without needing to construct a mocked context each time:</span></span>

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

<span data-ttu-id="72024-252">Bu teknik tüm kod temelinizde yapılan Evrensel uygulanmamalıdır ancak karmaşık iç Ayrıntılar ve birim testi bu iç işlevleri için Demirbaş azaltmak için iyi bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="72024-252">This technique should not be universally applied to your entire codebase, but it is a good way to reduce boilerplate for complicated internals and unit testing those internals.</span></span>

## <a name="access-control"></a><span data-ttu-id="72024-253">Erişim denetimi</span><span class="sxs-lookup"><span data-stu-id="72024-253">Access control</span></span>

<span data-ttu-id="72024-254">F#için birden çok seçenek vardır [erişim denetimi](../language-reference/access-control.md), .NET çalışma zamanı'nda kullanılabilir öğesinden devralınan.</span><span class="sxs-lookup"><span data-stu-id="72024-254">F# has multiple options for [Access control](../language-reference/access-control.md), inherited from what is available in the .NET runtime.</span></span> <span data-ttu-id="72024-255">Bunlar yalnızca türleri için kullanılabilir değildir - bunları işlevleri için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="72024-255">These are not just usable for types - you can use them for functions, too.</span></span>

* <span data-ttu-id="72024-256">Tercih ettiğiniz olmayan`public` türler ve üyeler kadar genel olarak kullanılabilir olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="72024-256">Prefer non-`public` types and members until you need them to be publicly consumable.</span></span> <span data-ttu-id="72024-257">Bu, hangi tüketicilerin birkaç için de azaltır.</span><span class="sxs-lookup"><span data-stu-id="72024-257">This also minimizes what consumers couple to.</span></span>
* <span data-ttu-id="72024-258">Tüm yardımcı işlevini tutun `private`.</span><span class="sxs-lookup"><span data-stu-id="72024-258">Strive to keep all helper functionality `private`.</span></span>
* <span data-ttu-id="72024-259">Kullanımını göz önünde bulundurun `[<AutoOpen>]` çok sayıda vermediğinde yardımcı işlevleri, özel bir modül.</span><span class="sxs-lookup"><span data-stu-id="72024-259">Consider the use of `[<AutoOpen>]` on a private module of helper functions if they become numerous.</span></span>

## <a name="type-inference-and-generics"></a><span data-ttu-id="72024-260">Tür çıkarımı ve genel türler</span><span class="sxs-lookup"><span data-stu-id="72024-260">Type inference and generics</span></span>

<span data-ttu-id="72024-261">Tür çıkarımı, çok sayıda standart yazmasını kaydedebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="72024-261">Type inference can save you from typing a lot of boilerplate.</span></span> <span data-ttu-id="72024-262">Ve de otomatik Genelleştirme F# derleyici bulunmanıza neredeyse hiçbir ekstra çaba daha genel kod yazmanıza yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="72024-262">And automatic generalization in the F# compiler can help you write more generic code with almost no extra effort on your part.</span></span> <span data-ttu-id="72024-263">Ancak, bu özellikler Evrensel iyi değildir.</span><span class="sxs-lookup"><span data-stu-id="72024-263">However, these features are not universally good.</span></span>

* <span data-ttu-id="72024-264">Bağımsız değişken adları açık türlerinde ortak API'ler ile etiketleme göz önünde bulundurun ve bunun için tür çıkarımı güvenmeyin.</span><span class="sxs-lookup"><span data-stu-id="72024-264">Consider labeling argument names with explicit types in public APIs and do not rely on type inference for this.</span></span>

    <span data-ttu-id="72024-265">Bunun nedeni olan **,** derleyici API'nizi şeklini denetiminde olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="72024-265">The reason for this is that **you** should be in control of the shape of your API, not the compiler.</span></span> <span data-ttu-id="72024-266">Derleyici, türlerin çıkarımını yapma en iyi bir iş yapabilirse kullanır iç türleri değişip değişmediğini API değişikliğiniz şeklini olması mümkündür.</span><span class="sxs-lookup"><span data-stu-id="72024-266">Although the compiler can do a fine job at inferring types for you, it is possible to have the shape of your API change if the internals it relies on have changed types.</span></span> <span data-ttu-id="72024-267">Bu, istediğiniz olabilir, ancak neredeyse kesindir aşağı akış tüketicilere çalışılabilecek olacak bir API değişiklik neden.</span><span class="sxs-lookup"><span data-stu-id="72024-267">This may be what you want, but it will almost certainly result in a breaking API change that downstream consumers will then have to deal with.</span></span> <span data-ttu-id="72024-268">Bunun yerine, açıkça genel API'nizi şeklini denetlemek, en son değişikliklerin denetleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="72024-268">Instead, if you explicitly control the shape of your public API, then you can control these breaking changes.</span></span> <span data-ttu-id="72024-269">DDD bağlamında, bu, bir bozulma önleyici katman düşünülebilir.</span><span class="sxs-lookup"><span data-stu-id="72024-269">In DDD terms, this can be thought of as an Anti-corruption layer.</span></span>

* <span data-ttu-id="72024-270">Genel, bağımsız değişkenleri için anlamlı bir ad vermeyi düşünün.</span><span class="sxs-lookup"><span data-stu-id="72024-270">Consider giving a meaningful name to your generic arguments.</span></span>

    <span data-ttu-id="72024-271">Belirli bir etki alanına özgü değildir gerçekten genel kod yazıyorsanız sürece, anlamlı bir ad, çalışmakta olduğunuz etki alanı anlama diğer programcılar yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="72024-271">Unless you are writing truly generic code that is not specific to a particular domain, a meaningful name can help other programmers understanding the domain they're working in.</span></span> <span data-ttu-id="72024-272">Örneğin, adlı bir tür parametresi `'Document` bir belge ile etkileşim kurmanın bağlamında veritabanı NET genel belge türü işlev veya birlikte çalıştığınız üyesi tarafından kabul edilebilen kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="72024-272">For example, a type parameter named `'Document` in the context of interacting with a document database makes it clearer that generic document types can be accepted by the function or member you are working with.</span></span>

* <span data-ttu-id="72024-273">Genel tür parametreleri ile PascalCase adlandırma göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="72024-273">Consider naming generic type parameters with PascalCase.</span></span>

    <span data-ttu-id="72024-274">Bu, .NET, şeyler PascalCase yerine snake_case veya camelCase kullanmanız önerilir Bunu yapmak için genel yoludur.</span><span class="sxs-lookup"><span data-stu-id="72024-274">This is the general way to do things in .NET, so it's recommended that you use PascalCase rather than snake_case or camelCase.</span></span>

<span data-ttu-id="72024-275">Son olarak, otomatik Genelleştirme her zaman bir boon yeni olan kişiler değil F# veya büyük bir kod temelinde.</span><span class="sxs-lookup"><span data-stu-id="72024-275">Finally, automatic generalization is not always a boon for people who are new to F# or a large codebase.</span></span> <span data-ttu-id="72024-276">Genel olarak bileşenleri kullanarak bilişsel yükü yoktur.</span><span class="sxs-lookup"><span data-stu-id="72024-276">There is cognitive overhead in using components that are generic.</span></span> <span data-ttu-id="72024-277">Ayrıca, varsa, otomatik olarak genelleştirilmiş işlevleri farklı giriş türleri (sağlar, bu nedenle kullanılacak yönelikse tek başına) ile kullanılmaz sonra bunlara zamandaki o noktada genel olan gerçek hiçbir avantajı yoktur.</span><span class="sxs-lookup"><span data-stu-id="72024-277">Furthermore, if automatically generalized functions are not used with different input types (let alone if they are intended to be used as such), then there is no real benefit to them being generic at that point in time.</span></span> <span data-ttu-id="72024-278">Her zaman yazdığınız kodu gerçekten genel yüklenmesini Kurum için avantaj sağlayacaktır olmadığını göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="72024-278">Always consider if the code you are writing will actually benefit from being generic.</span></span>

## <a name="performance"></a><span data-ttu-id="72024-279">Performans</span><span class="sxs-lookup"><span data-stu-id="72024-279">Performance</span></span>

<span data-ttu-id="72024-280">F#belirli sınıfları (özellikle bu ilgili eşzamanlılık ve paralellik) hataları önlemek izin veren varsayılan olarak, sabit değerlerdir.</span><span class="sxs-lookup"><span data-stu-id="72024-280">F# values are immutable by default, which allows you to avoid certain classes of bugs (especially those involving concurrency and parallelism).</span></span> <span data-ttu-id="72024-281">Ancak, bazı durumlarda, yürütme zamanı bellek ayırmaları ve en iyi (veya hatta makul) verimlilik elde etmek için bir yayılma iş en iyi durumu yerinde Mutasyon kullanarak uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="72024-281">However, in certain cases, in order to achieve optimal (or even reasonable) efficiency of execution time or memory allocations, a span of work may best be implemented by using in-place mutation of state.</span></span> <span data-ttu-id="72024-282">Bu katılımı temeli ile de mümkündür F# ile `mutable` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="72024-282">This is possible in an opt-in basis with F# with the `mutable` keyword.</span></span>

<span data-ttu-id="72024-283">Ancak, kullanım `mutable` içinde F# at odds with işlevsel saflığa düşünüyor.</span><span class="sxs-lookup"><span data-stu-id="72024-283">However, use of `mutable` in F# may feel at odds with functional purity.</span></span> <span data-ttu-id="72024-284">Bu beklentileri saflığa için gelen ayarlarsanız ince [başvuru saydamlık](https://en.wikipedia.org/wiki/Referential_transparency).</span><span class="sxs-lookup"><span data-stu-id="72024-284">This is fine, if you adjust expectations from purity to [referential transparency](https://en.wikipedia.org/wiki/Referential_transparency).</span></span> <span data-ttu-id="72024-285">Başvuru saydamlık - saflığa değil - yazarken son hedefi olduğu F# işlevleri.</span><span class="sxs-lookup"><span data-stu-id="72024-285">Referential transparency - not purity - is the end goal when writing F# functions.</span></span> <span data-ttu-id="72024-286">Bu performans kritik kod için Mutasyon tabanlı bir uygulama üzerinde işlevsel bir arabirim yazmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="72024-286">This allows you to write a functional interface over a mutation-based implementation for performance critical code.</span></span>

### <a name="wrap-mutable-code-in-immutable-interfaces"></a><span data-ttu-id="72024-287">Sabit arabirimler değişebilir kod Kaydır</span><span class="sxs-lookup"><span data-stu-id="72024-287">Wrap mutable code in immutable interfaces</span></span>

<span data-ttu-id="72024-288">Bir hedef olarak başvuru saydamlığı olan performans açısından kritik işlevler değişebilir underbelly kullanıma sunmuyor kod yazmak için önemlidir.</span><span class="sxs-lookup"><span data-stu-id="72024-288">With referential transparency as a goal, it is critical to write code that does not expose the mutable underbelly of performance-critical functions.</span></span> <span data-ttu-id="72024-289">Örneğin, aşağıdaki uygulayan kod `Array.contains` işlevi F# çekirdek kitaplığı:</span><span class="sxs-lookup"><span data-stu-id="72024-289">For example, the following code implements the `Array.contains` function in the F# core library:</span></span>

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

<span data-ttu-id="72024-290">Bu fonksiyonu çağıran birden çok kez temel alınan dizi değişmez ya da hangi herhangi bir kesilebilir durumu sürdürmenizi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="72024-290">Calling this function multiple times does not change the underlying array, nor does it require you to maintain any mutable state in consuming it.</span></span> <span data-ttu-id="72024-291">Her neredeyse içindeki kod satırı Mutasyon kullansa bile referentially saydam.</span><span class="sxs-lookup"><span data-stu-id="72024-291">It is referentially transparent, even though almost every line of code within it uses mutation.</span></span>

### <a name="consider-encapsulating-mutable-data-in-classes"></a><span data-ttu-id="72024-292">Değişebilir veri sınıflarında Kapsüllenen göz önünde bulundurun</span><span class="sxs-lookup"><span data-stu-id="72024-292">Consider encapsulating mutable data in classes</span></span>

<span data-ttu-id="72024-293">Önceki örnekte, değişebilir veri kullanan işlemleri kapsüllemek için tek bir işlev kullanılır.</span><span class="sxs-lookup"><span data-stu-id="72024-293">The previous example used a single function to encapsulate operations using mutable data.</span></span> <span data-ttu-id="72024-294">Bu her zaman daha karmaşık veri kümeleri için yeterli değil.</span><span class="sxs-lookup"><span data-stu-id="72024-294">This is not always sufficient for more complex sets of data.</span></span> <span data-ttu-id="72024-295">Aşağıdaki adımlardan birini işlevleri göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="72024-295">Consider the following sets of functions:</span></span>

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

<span data-ttu-id="72024-296">Bu kod, yüksek performanslı olmakla birlikte çağıranlar sorumlu olduğunuz Mutasyon tabanlı veri yapısını gösterir.</span><span class="sxs-lookup"><span data-stu-id="72024-296">This code is performant, but it exposes the mutation-based data structure that callers are responsible for maintaining.</span></span> <span data-ttu-id="72024-297">Değiştirebileceğiniz temel alınan üye ile bir sınıf içinde sarmalanabilir:</span><span class="sxs-lookup"><span data-stu-id="72024-297">This can be wrapped inside of a class with no underlying members that can change:</span></span>

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

<span data-ttu-id="72024-298">`Closure1Table` temel alınan veri yapısı korumak için çağıranlar Zorlanmıyor böylece temel alınan Mutasyon tabanlı veri yapısı kapsüller.</span><span class="sxs-lookup"><span data-stu-id="72024-298">`Closure1Table` encapsulates the underlying mutation-based data structure, thereby not forcing callers to maintain the underlying data structure.</span></span> <span data-ttu-id="72024-299">Sınıfları, veri ve ayrıntıları arayanlara sokmadan Mutasyon tabanlı yordamlarını kapsüllemek için güçlü bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="72024-299">Classes are a powerful way to encapsulate data and routines that are mutation-based without exposing the details to callers.</span></span>

### <a name="prefer-let-mutable-to-reference-cells"></a><span data-ttu-id="72024-300">Tercih ettiğiniz `let mutable` başvuru hücreleri</span><span class="sxs-lookup"><span data-stu-id="72024-300">Prefer `let mutable` to reference cells</span></span>

<span data-ttu-id="72024-301">Başvuru hücreleri başvuru değeri yerine bir değeri temsil eden bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="72024-301">Reference cells are a way to represent the reference to a value rather than the value itself.</span></span> <span data-ttu-id="72024-302">Performans açısından kritik kod için kullanılabilir olsa da, genellikle önerilmez.</span><span class="sxs-lookup"><span data-stu-id="72024-302">Although they can be used for performance-critical code, they are generally not recommended.</span></span> <span data-ttu-id="72024-303">Aşağıdaki örnek göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="72024-303">Consider the following example:</span></span>

```fsharp
let kernels =
    let acc = ref Set.empty

    processWorkList startKernels (fun kernel ->
        if not ((!acc).Contains(kernel)) then
            acc := (!acc).Add(kernel)
        ...)

    !acc |> Seq.toList
```

<span data-ttu-id="72024-304">Bir başvuru hücresi kullanımı artık "başvuru ve temel alınan verileri yeniden başvurmak zorunda olan tüm sonraki kod pollutes".</span><span class="sxs-lookup"><span data-stu-id="72024-304">The use of a reference cell now "pollutes" all subsequent code with having to dereference and re-reference the underlying data.</span></span> <span data-ttu-id="72024-305">Bunun yerine, göz önünde bulundurun `let mutable`:</span><span class="sxs-lookup"><span data-stu-id="72024-305">Instead, consider `let mutable`:</span></span>

```fsharp
let kernels =
    let mutable acc = Set.empty

    processWorkList startKernels (fun kernel ->
        if not (acc.Contains(kernel)) then
            acc <- acc.Add(kernel)
        ...)

    acc |> Seq.toList
```

<span data-ttu-id="72024-306">Diğer tüm kod lambda ifadesi ortasında Mutasyon yanı sıra tek noktası dokunduğu `acc` normal kullanım için farklı bir şekilde bunu yapabilirsiniz `let`-bağlı sabit değer.</span><span class="sxs-lookup"><span data-stu-id="72024-306">Aside from the single point of mutation in the middle of the lambda expression, all other code that touches `acc` can do so in a manner that is no different to the usage of a normal `let`-bound immutable value.</span></span> <span data-ttu-id="72024-307">Bu zaman içinde kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="72024-307">This will make it easier to change over time.</span></span>

## <a name="object-programming"></a><span data-ttu-id="72024-308">Nesne programlama</span><span class="sxs-lookup"><span data-stu-id="72024-308">Object programming</span></span>

<span data-ttu-id="72024-309">F#nesneleri ve nesne yönelimli kavramları (Paylaşımlarınızda) için tam destek sunar.</span><span class="sxs-lookup"><span data-stu-id="72024-309">F# has full support for objects and object-oriented (OO) concepts.</span></span> <span data-ttu-id="72024-310">Birçok Paylaşımlarınızda kavramları güçlü ve kullanışlı olsa da, bunların hepsi kullanmak idealdir.</span><span class="sxs-lookup"><span data-stu-id="72024-310">Although many OO concepts are powerful and useful, not all of them are ideal to use.</span></span> <span data-ttu-id="72024-311">Aşağıdaki listeler, yüksek bir düzeyde Paylaşımlarınızda özelliklerinin kategorileri hakkında rehberlik sunar.</span><span class="sxs-lookup"><span data-stu-id="72024-311">The following lists offer guidance on categories of OO features at a high level.</span></span>

<span data-ttu-id="72024-312">**Çoğu durumda bu özellikleri kullanmaya göz önünde bulundurun:**</span><span class="sxs-lookup"><span data-stu-id="72024-312">**Consider using these features in many situations:**</span></span>

* <span data-ttu-id="72024-313">Noktalı gösterim (`x.Length`)</span><span class="sxs-lookup"><span data-stu-id="72024-313">Dot notation (`x.Length`)</span></span>
* <span data-ttu-id="72024-314">Örnek üyeleri</span><span class="sxs-lookup"><span data-stu-id="72024-314">Instance members</span></span>
* <span data-ttu-id="72024-315">Örtük Oluşturucu</span><span class="sxs-lookup"><span data-stu-id="72024-315">Implicit constructors</span></span>
* <span data-ttu-id="72024-316">Statik üyeler</span><span class="sxs-lookup"><span data-stu-id="72024-316">Static members</span></span>
* <span data-ttu-id="72024-317">Dizin Oluşturucu gösterimi (`arr.[x]`)</span><span class="sxs-lookup"><span data-stu-id="72024-317">Indexer notation (`arr.[x]`)</span></span>
* <span data-ttu-id="72024-318">Adlandırılmış ve isteğe bağlı bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="72024-318">Named and Optional arguments</span></span>
* <span data-ttu-id="72024-319">Arabirimleri ve arabirim uygulamaları</span><span class="sxs-lookup"><span data-stu-id="72024-319">Interfaces and interface implementations</span></span>

<span data-ttu-id="72024-320">**Bu özellikler için ilk ulaşmak yoktur, ancak bir sorunu çözmek uygun olmaları durumunda dikkatli uygulayabilirsiniz:**</span><span class="sxs-lookup"><span data-stu-id="72024-320">**Don't reach for these features first, but do judiciously apply them when they are convenient to solve a problem:**</span></span>

* <span data-ttu-id="72024-321">Yöntemi aşırı yüklemesi</span><span class="sxs-lookup"><span data-stu-id="72024-321">Method overloading</span></span>
* <span data-ttu-id="72024-322">Değişebilir veri kapsüllenmiş</span><span class="sxs-lookup"><span data-stu-id="72024-322">Encapsulated mutable data</span></span>
* <span data-ttu-id="72024-323">Türlerinde işleçleri</span><span class="sxs-lookup"><span data-stu-id="72024-323">Operators on types</span></span>
* <span data-ttu-id="72024-324">Otomatik özellikleri</span><span class="sxs-lookup"><span data-stu-id="72024-324">Auto properties</span></span>
* <span data-ttu-id="72024-325">Uygulama `IDisposable` ve `IEnumerable`</span><span class="sxs-lookup"><span data-stu-id="72024-325">Implementing `IDisposable` and `IEnumerable`</span></span>
* <span data-ttu-id="72024-326">Tür uzantıları</span><span class="sxs-lookup"><span data-stu-id="72024-326">Type extensions</span></span>
* <span data-ttu-id="72024-327">Olaylar</span><span class="sxs-lookup"><span data-stu-id="72024-327">Events</span></span>
* <span data-ttu-id="72024-328">Yapılar</span><span class="sxs-lookup"><span data-stu-id="72024-328">Structs</span></span>
* <span data-ttu-id="72024-329">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="72024-329">Delegates</span></span>
* <span data-ttu-id="72024-330">Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="72024-330">Enums</span></span>

<span data-ttu-id="72024-331">**Genellikle bunları kullanmadığınız sürece bu özellikler kaçının:**</span><span class="sxs-lookup"><span data-stu-id="72024-331">**Generally avoid these features unless you must use them:**</span></span>

* <span data-ttu-id="72024-332">Devralma tabanlı tür hiyerarşileri ve uygulama devralma</span><span class="sxs-lookup"><span data-stu-id="72024-332">Inheritance-based type hierarchies and implementation inheritance</span></span>
* <span data-ttu-id="72024-333">Null değerler ve `Unchecked.defaultof<_>`</span><span class="sxs-lookup"><span data-stu-id="72024-333">Nulls and `Unchecked.defaultof<_>`</span></span>

### <a name="prefer-composition-over-inheritance"></a><span data-ttu-id="72024-334">Devralma bileşim tercih et</span><span class="sxs-lookup"><span data-stu-id="72024-334">Prefer composition over inheritance</span></span>

<span data-ttu-id="72024-335">[Devralma üzerinden bileşim](https://en.wikipedia.org/wiki/Composition_over_inheritance) değindiği deyim bu kadar iyidir F# kod uyması için.</span><span class="sxs-lookup"><span data-stu-id="72024-335">[Composition over inheritance](https://en.wikipedia.org/wiki/Composition_over_inheritance) is a long-standing idiom that good F# code can adhere to.</span></span> <span data-ttu-id="72024-336">Temel olmayan bir taban sınıfı ve gerekir işlevselliğine sahip olmak için o temel sınıftan devralınan çağrı yapanların zorlamak emin ilkesidir.</span><span class="sxs-lookup"><span data-stu-id="72024-336">The fundamental principle is that you should not expose a base class and force callers to inherit from that base class to get functionality.</span></span>

### <a name="use-object-expressions-to-implement-interfaces-if-you-dont-need-a-class"></a><span data-ttu-id="72024-337">Bir sınıf gerekmiyorsa arayüzleri uygulamak için Nesne ifadeleri kullanma</span><span class="sxs-lookup"><span data-stu-id="72024-337">Use object expressions to implement interfaces if you don't need a class</span></span>

<span data-ttu-id="72024-338">[Nesne ifadeleri](../language-reference/object-expressions.md) halindeyken arayüzleri uygulamak izin uygulanan arabirimin bir değere bir sınıf içinde bunu gerek kalmadan bağlama.</span><span class="sxs-lookup"><span data-stu-id="72024-338">[Object Expressions](../language-reference/object-expressions.md) allow you to implement interfaces on the fly, binding the implemented interface to a value without needing to do so inside of a class.</span></span> <span data-ttu-id="72024-339">Bu kullanışlı, özellikle de, _yalnızca_ arabirim uygular ve gerek tam bir sınıf olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="72024-339">This is convenient, especially if you _only_ need to implement the interface and have no need for a full class.</span></span>

<span data-ttu-id="72024-340">Örneğin, içinde çalışan kod işte [Ionide](http://ionide.io/) sahip olmayan bir sembol eklediyseniz, bir kod düzeltme eylemi sağlamak için bir `open` deyimi için:</span><span class="sxs-lookup"><span data-stu-id="72024-340">For example, here is the code that is run in [Ionide](http://ionide.io/) to provide a code fix action if you've added a symbol that you don't have an `open` statement for:</span></span>

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

<span data-ttu-id="72024-341">Bir sınıf için gerek olmadığından Visual Studio kod API'SİYLE etkileşim kurulurken nesne ifadeleri bu ideal bir araçlardır.</span><span class="sxs-lookup"><span data-stu-id="72024-341">Because there is no need for a class when interacting with the Visual Studio Code API, Object Expressions are an ideal tool for this.</span></span> <span data-ttu-id="72024-342">Ayrıca birim testi, geçici bir şekilde test yordamları bir arabirimi kullanıma saplama istediğinizde için değerli.</span><span class="sxs-lookup"><span data-stu-id="72024-342">They are also valuable for unit testing, when you want to stub out an interface with test routines in an ad hoc manner.</span></span>

## <a name="type-abbreviations"></a><span data-ttu-id="72024-343">Tür Kısaltmaları</span><span class="sxs-lookup"><span data-stu-id="72024-343">Type Abbreviations</span></span>

<span data-ttu-id="72024-344">[Tür kısaltmaları](../language-reference/type-abbreviations.md) işlev imzası veya daha karmaşık bir tür gibi başka bir tür için bir etiket atamak için kullanışlı bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="72024-344">[Type Abbreviations](../language-reference/type-abbreviations.md) are a convenient way to assign a label to another type, such as a function signature or a more complex type.</span></span> <span data-ttu-id="72024-345">Örneğin, şu diğer ne olan hesaplamayı tanımlamak gerekli bir etiketi atar [CNTK](https://www.microsoft.com/en-us/cognitive-toolkit/), kapsamlı bir kitaplık öğrenme:</span><span class="sxs-lookup"><span data-stu-id="72024-345">For example, the following alias assigns a label to what's needed to define a computation with [CNTK](https://www.microsoft.com/en-us/cognitive-toolkit/), a deep learning library:</span></span>

```fsharp
open CNTK

// DeviceDescriptor, Variable, and Function all come from CNTK
type Computation = DeviceDescriptor -> Variable -> Function
```

<span data-ttu-id="72024-346">`Computation` Yumuşatma olduğu imzayla eşleşen herhangi bir işlev belirtmek için kullanışlı bir yol adıdır.</span><span class="sxs-lookup"><span data-stu-id="72024-346">The `Computation` name is a convenient way to denote any function that matches the signature it is aliasing.</span></span> <span data-ttu-id="72024-347">Tür kısaltmaları şöyle kullanarak uygun olan ve daha Sözün kodunu sağlar.</span><span class="sxs-lookup"><span data-stu-id="72024-347">Using Type Abbreviations like this is convenient and allows for more succinct code.</span></span>

### <a name="avoid-using-type-abbreviations-to-represent-your-domain"></a><span data-ttu-id="72024-348">Tür kısaltmaları etki alanınızı temsil etmek için kullanmaktan kaçının</span><span class="sxs-lookup"><span data-stu-id="72024-348">Avoid using Type Abbreviations to represent your domain</span></span>

<span data-ttu-id="72024-349">Tür kısaltmaları işlevi imzalar için bir ad vermek için kullanışlı olsa da, bunlar diğer türleri kısaltma kafa karıştırıcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="72024-349">Although Type Abbreviations are convenient for giving a name to function signatures, they can be confusing when abbreviating other types.</span></span> <span data-ttu-id="72024-350">Bu kısaltma göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="72024-350">Consider this abbreviation:</span></span>

```fsharp
// Does not actually abstract integers.
type BufferSize = int
```

<span data-ttu-id="72024-351">Bu, birden çok yolla kafa karıştırıcı olabilir:</span><span class="sxs-lookup"><span data-stu-id="72024-351">This can be confusing in multiple ways:</span></span>

* <span data-ttu-id="72024-352">`BufferSize` bir Özet değil; bir tamsayı yalnızca başka bir addır.</span><span class="sxs-lookup"><span data-stu-id="72024-352">`BufferSize` is not an abstraction; it is just another name for an integer.</span></span>
* <span data-ttu-id="72024-353">Varsa `BufferSize` sunulan genel bir API'de, kolayca daha fazlasını auto'yu anlaşılabilir `int`.</span><span class="sxs-lookup"><span data-stu-id="72024-353">If `BufferSize` is exposed in a public API, it can easily be misinterpreted to mean more than just `int`.</span></span> <span data-ttu-id="72024-354">Genel olarak, etki alanı türleri onlara birden çok özniteliklere sahip ve gibi ilkel türleri `int`.</span><span class="sxs-lookup"><span data-stu-id="72024-354">Generally, domain types have multiple attributes to them and are not primitive types like `int`.</span></span> <span data-ttu-id="72024-355">Bu kısaltma bu varsayımı ihlal ediyor.</span><span class="sxs-lookup"><span data-stu-id="72024-355">This abbreviation violates that assumption.</span></span>
* <span data-ttu-id="72024-356">Büyük küçük harfleri `BufferSize` (PascalCase), bu tür daha fazla veri bulunduran anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="72024-356">The casing of `BufferSize` (PascalCase) implies that this type holds more data.</span></span>
* <span data-ttu-id="72024-357">Bu diğer adı, adlandırılmış bir bağımsız değişken bir işleve sağlamaya göre artan netlik sunmaz.</span><span class="sxs-lookup"><span data-stu-id="72024-357">This alias does not offer increased clarity compared with providing a named argument to a function.</span></span>
* <span data-ttu-id="72024-358">Kısaltması derlenmiş IL bildirilmez; bir tamsayı olduğu ve bu diğer adı, bir derleme zamanı yapıdır.</span><span class="sxs-lookup"><span data-stu-id="72024-358">The abbreviation will not manifest in compiled IL; it is just an integer and this alias is a compile-time construct.</span></span>

```fsharp
module Networking =
    ...
    let send data (bufferSize: int) =
        ...
```

<span data-ttu-id="72024-359">Özet olarak, tür kısaltmaları ile durumu olduklarından emin olan **değil** kısaltma türleri üzerinden soyutlamalar.</span><span class="sxs-lookup"><span data-stu-id="72024-359">In summary, the pitfall with Type Abbreviations is that they are **not** abstractions over the types they are abbreviating.</span></span> <span data-ttu-id="72024-360">Önceki örnekte, `BufferSize` tıpkı bir `int` ek veri yok ya da herhangi bir avantaj yanı sıra ne tür sisteminden ile kapsar altında `int` zaten sahip.</span><span class="sxs-lookup"><span data-stu-id="72024-360">In the previous example, `BufferSize` is just an `int` under the covers, with no additional data, nor any benefits from the type system besides what `int` already has.</span></span>
