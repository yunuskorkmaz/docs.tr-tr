---
title: 'F # zaman uyumsuz programlama'
description: 'F # zaman uyumsuz programlama kullanımı kolay ve doğal dil için bir dil düzeyi programlama modeli aracılığıyla nasıl yapıldığını öğrenin.'
author: cartermp
ms.author: phcart
ms.date: 06/20/2016
ms.topic: conceptual
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: a3047b98637cb4b142f374a2a2b5e7270e850fd6
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="async-programming-in-f"></a><span data-ttu-id="52dee-103">F # zaman uyumsuz programlama</span><span class="sxs-lookup"><span data-stu-id="52dee-103">Async Programming in F#</span></span> #

> [!NOTE]
> <span data-ttu-id="52dee-104">Bu makaledeki bazı yanlışlıklar bulundu.</span><span class="sxs-lookup"><span data-stu-id="52dee-104">Some inaccuracies have been discovered in this article.</span></span>  <span data-ttu-id="52dee-105">Bunu yeniden yazılıyor.</span><span class="sxs-lookup"><span data-stu-id="52dee-105">It is being rewritten.</span></span>  <span data-ttu-id="52dee-106">Bkz: [sorunu #666](https://github.com/dotnet/docs/issues/666) değişiklikler hakkında bilgi edinmek için.</span><span class="sxs-lookup"><span data-stu-id="52dee-106">See [Issue #666](https://github.com/dotnet/docs/issues/666) to learn about the changes.</span></span>

<span data-ttu-id="52dee-107">Zaman uyumsuz programlama F #'de, kullanımı kolay ve doğal dil için olmak üzere tasarlanmış bir dil düzeyi programlama modeli aracılığıyla gerçekleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="52dee-107">Async programming in F# can be accomplished through a language-level programming model designed to be easy to use and natural to the language.</span></span>

<span data-ttu-id="52dee-108">F # zaman uyumsuz programlama çekirdeği `Async<'T>`, arka planda çalışmaya tetiklenen iş gösterimini nerede `'T` türlerinden özel döndürülen `return` anahtar sözcüğü veya `unit` zaman uyumsuz iş akışı no varsa döndürülecek sonuç.</span><span class="sxs-lookup"><span data-stu-id="52dee-108">The core of async programming in F# is `Async<'T>`, a representation of work that can be triggered to run in the background, where `'T` is either the type returned via the special `return` keyword or `unit` if the async workflow has no result to return.</span></span>

<span data-ttu-id="52dee-109">Bir zaman uyumsuz deyim türü olduğunu anlamak için anahtar kavram olan `Async<'T>`, olan yalnızca bir _belirtimi_ zaman uyumsuz bir bağlamda yapılması çalışma.</span><span class="sxs-lookup"><span data-stu-id="52dee-109">The key concept to understand is that an async expression’s type is `Async<'T>`, which is merely a _specification_ of work to be done in an asynchronous context.</span></span> <span data-ttu-id="52dee-110">Açıkça başlangıç işlevleri biriyle başlatmanız kadar yürütülür değil (gibi `Async.RunSynchronously`).</span><span class="sxs-lookup"><span data-stu-id="52dee-110">It is not executed until you explicitly start it with one of the starting functions (such as `Async.RunSynchronously`).</span></span> <span data-ttu-id="52dee-111">Bu iş yapma hakkında düşünmeye farklı bir şekilde olsa da, uygulamada oldukça basit olan sona erer.</span><span class="sxs-lookup"><span data-stu-id="52dee-111">Although this is a different way of thinking about doing work, it ends up being quite simple in practice.</span></span>

<span data-ttu-id="52dee-112">Örneğin, ana iş parçacığı engellenmeden HTML dotnetfoundation.org karşıdan yüklemek istediğinizi varsayalım.</span><span class="sxs-lookup"><span data-stu-id="52dee-112">For example, say you wanted to download the HTML from dotnetfoundation.org without blocking the main thread.</span></span> <span data-ttu-id="52dee-113">Bunu şu şekilde gerçekleştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="52dee-113">You can accomplish it like this:</span></span>

```fsharp
open System
open System.Net

let fetchHtmlAsync url = 
    async {
        let uri = Uri(url)
        use webClient = new WebClient()

        // Execution of fetchHtmlAsync won't continue until the result
        // of AsyncDownloadString is bound.
        let! html = webClient.AsyncDownloadString(uri)
        return html
    }

let html = "https://dotnetfoundation.org" |> fetchHtmlAsync |> Async.RunSynchronously
printfn "%s" html
```

<span data-ttu-id="52dee-114">Ve bu kadar!</span><span class="sxs-lookup"><span data-stu-id="52dee-114">And that’s it!</span></span> <span data-ttu-id="52dee-115">Kullanımını yanı sıra `async`, `let!`, ve `return`, yalnızca normal F # kodu budur.</span><span class="sxs-lookup"><span data-stu-id="52dee-115">Aside from the use of `async`, `let!`, and `return`, this is just normal F# code.</span></span>

<span data-ttu-id="52dee-116">Belirtmeye değer olan birkaç söz dizimi yapıları vardır:</span><span class="sxs-lookup"><span data-stu-id="52dee-116">There are a few syntactical constructs which are worth noting:</span></span>

*   <span data-ttu-id="52dee-117">`let!` (başka bir bağlamda çalışır) bir zaman uyumsuz ifadesi sonucu bağlar.</span><span class="sxs-lookup"><span data-stu-id="52dee-117">`let!` binds the result of an async expression (which runs on another context).</span></span>
*   <span data-ttu-id="52dee-118">`use!` Works olduğu gibi `let!`, ancak kapsam dışına çıktığında, ilişkili kaynakları siler.</span><span class="sxs-lookup"><span data-stu-id="52dee-118">`use!` works just like `let!`, but disposes its bound resources when it goes out of scope.</span></span>
*   <span data-ttu-id="52dee-119">`do!` herhangi bir şey döndürmez bir zaman uyumsuz iş akışı await.</span><span class="sxs-lookup"><span data-stu-id="52dee-119">`do!` will await an async workflow which doesn’t return anything.</span></span>
*   <span data-ttu-id="52dee-120">`return` yalnızca zaman uyumsuz ifadeden bir sonuç döndürür.</span><span class="sxs-lookup"><span data-stu-id="52dee-120">`return` simply returns a result from an async expression.</span></span>
*   <span data-ttu-id="52dee-121">`return!` başka bir zaman uyumsuz iş akışı çalıştırır ve sonuç olarak kendi dönüş değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="52dee-121">`return!` executes another async workflow and returns its return value as a result.</span></span>

<span data-ttu-id="52dee-122">Ayrıca, normal `let`, `use`, ve `do` anahtar sözcükleri normal bir işlevde gibi zaman uyumsuz sürümlerini kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="52dee-122">Additionally, normal `let`, `use`, and `do` keywords can be used alongside the async versions just as they would in a normal function.</span></span>

## <a name="how-to-start-async-code-in-f"></a><span data-ttu-id="52dee-123">Zaman uyumsuz kod F #'ta başlatma</span><span class="sxs-lookup"><span data-stu-id="52dee-123">How to start Async Code in F#</span></span> #

<span data-ttu-id="52dee-124">Daha önce belirtildiği gibi zaman uyumsuz açıkça başlatılması gereken başka bir bağlamda yapılacak işleri belirtimini kodudur.</span><span class="sxs-lookup"><span data-stu-id="52dee-124">As mentioned earlier, async code is a specification of work to be done in another context which needs to be explicitly started.</span></span> <span data-ttu-id="52dee-125">Bunu yapmanın iki birincil yollar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="52dee-125">Here are two primary ways to accomplish this:</span></span>

1.  <span data-ttu-id="52dee-126">`Async.RunSynchronously` işlem başka bir iş parçacığında bir zaman uyumsuz iş akışını başlatmak ve sonucunu bekler.</span><span class="sxs-lookup"><span data-stu-id="52dee-126">`Async.RunSynchronously` will start an async workflow on another thread and await its result.</span></span>

```fsharp
open System
open System.Net

let fetchHtmlAsync url = 
    async {
        let uri = Uri(url)
        use webClient = new WebClient()
        let! html = webClient.AsyncDownloadString(uri)
        return html
    }

 // Execution will pause until fetchHtmlAsync finishes
 let html = "https://dotnetfoundation.org" |> fetchHtmlAsync |> Async.RunSynchronously

 // you actually have the result from fetchHtmlAsync now!
 printfn "%s" html
 ```

2.  <span data-ttu-id="52dee-127">`Async.Start` başka bir iş parçacığında bir zaman uyumsuz iş akışını başlatmak ve olacak **değil** sonucunu bekler.</span><span class="sxs-lookup"><span data-stu-id="52dee-127">`Async.Start` will start an async workflow on another thread, and will **not** await its result.</span></span>

```fsharp
open System
open System.Net
  
let uploadDataAsync url data = 
    async {
        let uri = Uri(url)
        use webClient = new WebClient()
        webClient.UploadStringAsync(uri, data)
    }

let workflow = uploadDataAsync "https://url-to-upload-to.com" "hello, world!"

// Execution will continue after calling this!
Async.Start(workflow)

printfn "%s" "uploadDataAsync is running in the background..."
 ```

<span data-ttu-id="52dee-128">Bir zaman uyumsuz iş akışı daha belirli senaryolar için kullanılabilir başlatmak için diğer yolları vardır.</span><span class="sxs-lookup"><span data-stu-id="52dee-128">There are other ways to start an async workflow available for more specific scenarios.</span></span> <span data-ttu-id="52dee-129">Ayrıntılı olmayan [zaman uyumsuz başvurusu](https://msdn.microsoft.com/library/ee370232.aspx).</span><span class="sxs-lookup"><span data-stu-id="52dee-129">They are detailed [in the Async reference](https://msdn.microsoft.com/library/ee370232.aspx).</span></span>

### <a name="a-note-on-threads"></a><span data-ttu-id="52dee-130">İş parçacığı üzerinde Not</span><span class="sxs-lookup"><span data-stu-id="52dee-130">A Note on Threads</span></span>

<span data-ttu-id="52dee-131">"Üzerinde başka bir iş parçacığı" tümceciği yukarıda belirtilen ancak bilmek önemlidir **bu zaman uyumsuz iş akışları için cephesi olduğunu gelmez çoklu iş parçacığı kullanımı**.</span><span class="sxs-lookup"><span data-stu-id="52dee-131">The phrase "on another thread" is mentioned above, but it is important to know that **this does not mean that async workflows are a facade for multithreading**.</span></span> <span data-ttu-id="52dee-132">İş akışı gerçekte "bir küçük süreyi yararlı çalışmanız için ödünç iş parçacıkları arasında atlar".</span><span class="sxs-lookup"><span data-stu-id="52dee-132">The workflow actually "jumps" between threads, borrowing them for a small amount of time to do useful work.</span></span> <span data-ttu-id="52dee-133">Zaman uyumsuz iş akışı etkili bir şekilde "(örneğin, bir şey döndürmek ağ arama için bekleniyor) beklediği sırada" zaman ödünç herhangi bir iş parçacığı gidin yararlı çalışmaları başka bir şey kadar serbest bırakılır.</span><span class="sxs-lookup"><span data-stu-id="52dee-133">When an async workflow is effectively "waiting" (for example, waiting for a network call to return something), any thread it was borrowing at the time is freed up to go do useful work on something else.</span></span> <span data-ttu-id="52dee-134">Bu çalıştıkları olabildiğince etkili bir şekilde sistemini kullanmak için zaman uyumsuz iş akışları sağlar ve yüksek hacimli g/ç senaryoları için özellikle güçlü hale getirir.</span><span class="sxs-lookup"><span data-stu-id="52dee-134">This allows async workflows to utilize the system they run on as effectively as possible, and makes them especially strong for high-volume I/O scenarios.</span></span>

## <a name="how-to-add-parallelism-to-async-code"></a><span data-ttu-id="52dee-135">Zaman uyumsuz kodu paralellik ekleme</span><span class="sxs-lookup"><span data-stu-id="52dee-135">How to Add Parallelism to Async Code</span></span>

<span data-ttu-id="52dee-136">Bazen, paralel olarak birden çok zaman uyumsuz işlerini gerçekleştirmek için kendi sonuçlarını toplamak ve bazı şekilde yorumlamaya.</span><span class="sxs-lookup"><span data-stu-id="52dee-136">Sometimes you may need to perform multiple asynchronous jobs in parallel, collect their results, and interpret them in some way.</span></span> <span data-ttu-id="52dee-137">`Async.Parallel` Görev paralel coerce gerek içerir kitaplığı, kullanmaya gerek kalmadan bunu sayesinde `Task<'T>` ve `Async<'T>` türleri.</span><span class="sxs-lookup"><span data-stu-id="52dee-137">`Async.Parallel` allows you to do this without needing to use the Task Parallel Library, which would involve needing to coerce `Task<'T>` and `Async<'T>` types.</span></span>

<span data-ttu-id="52dee-138">Aşağıdaki örnek kullanacağı `Async.Parallel` paralel dört popüler sitelerinden HTML indirmek için bu görevin tamamlanmasını bekleyin ve sonra indirilen HTML yazdırın.</span><span class="sxs-lookup"><span data-stu-id="52dee-138">The following example will use `Async.Parallel` to download the HTML from four popular sites in parallel, wait for those tasks to complete, and then print the HTML which was downloaded.</span></span>

```fsharp
open System
open System.Net

let urlList = 
    [ "https://www.microsoft.com"
      "https://www.google.com"
      "https://www.amazon.com"
      "https://www.facebook.com" ]

let fetchHtmlAsync url = 
    async {
        let uri = Uri(url)
        use webClient = new WebClient()
        let! html = webClient.AsyncDownloadString(uri)
        return html
    }

let getHtmlList urls =
    urls
    |> Seq.map fetchHtmlAsync   // Build an Async<'T> for each site
    |> Async.Parallel           // Returns an Async<'T []>
    |> Async.RunSynchronously   // Wait for the result of the parallel work

let htmlList = getHtmlList urlList

// We now have the downloaded HTML for each site!
for html in htmlList do
    printfn "%s" html
```

## <a name="important-info-and-advice"></a><span data-ttu-id="52dee-139">Önemli bilgiler ve öneriler</span><span class="sxs-lookup"><span data-stu-id="52dee-139">Important Info and Advice</span></span>

*   <span data-ttu-id="52dee-140">"Zaman uyumsuz" tüketen işlevleri sonuna</span><span class="sxs-lookup"><span data-stu-id="52dee-140">Append "Async" to the end of any functions you’ll consume</span></span>

 <span data-ttu-id="52dee-141">Bu yalnızca bir adlandırma kuralı olsa da, API bulunabilirliği gibi şeyleri kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="52dee-141">Although this is just a naming convention, it does make things like API discoverability easier.</span></span> <span data-ttu-id="52dee-142">Özellikle varsa aynı yordamını zaman uyumlu ve zaman uyumsuz sürümlerini açıkça ad yoluyla zaman uyumsuz olduğu durum için iyi bir fikirdir.</span><span class="sxs-lookup"><span data-stu-id="52dee-142">Particularly if there are synchronous and asynchronous versions of the same routine, it’s a good idea to explicitly state which is asynchronous via the name.</span></span>

*   <span data-ttu-id="52dee-143">Derleyiciye dinleme!</span><span class="sxs-lookup"><span data-stu-id="52dee-143">Listen to the compiler!</span></span>

 <span data-ttu-id="52dee-144">F #'ın derleyici çok sıkı, bir şeyler neredeyse olanaksız hale gibi troubling "zaman uyumsuz" kod eşzamanlı olarak çalıştır.</span><span class="sxs-lookup"><span data-stu-id="52dee-144">F#’s compiler is very strict, making it nearly impossible to do something troubling like run "async" code synchronously.</span></span> <span data-ttu-id="52dee-145">Bir uyarı üzerinden geliyorsa, kodu nasıl içinde düşündüğünüz yürütme olmaz oturum olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="52dee-145">If you come across a warning, that’s a sign that the code won’t execute how you think it will.</span></span> <span data-ttu-id="52dee-146">Derleyici mutluluk yapabiliyorsanız kodunuzu beklendiği gibi büyük olasılıkla yürütülür.</span><span class="sxs-lookup"><span data-stu-id="52dee-146">If you can make the compiler happy, your code will most likely execute as expected.</span></span>

## <a name="for-the-cvb-programmer-looking-into-f"></a><span data-ttu-id="52dee-147">F # diline arayan C# /VB programcı için</span><span class="sxs-lookup"><span data-stu-id="52dee-147">For the C#/VB Programmer Looking Into F#</span></span> #

<span data-ttu-id="52dee-148">Bu bölümde, C# zaman uyumsuz modeli alışık olduğunuz varsayılır / vb</span><span class="sxs-lookup"><span data-stu-id="52dee-148">This section assumes you’re familiar with the async model in C#/VB.</span></span> <span data-ttu-id="52dee-149">Siz değilseniz, [zaman uyumsuz programlama C#](../../../csharp/async.md) bir başlangıç noktasıdır.</span><span class="sxs-lookup"><span data-stu-id="52dee-149">If you are not, [Async Programming in C#](../../../csharp/async.md) is a starting point.</span></span>

<span data-ttu-id="52dee-150">C# /VB zaman uyumsuz modeli ve F # zaman uyumsuz modeli arasındaki temel fark yoktur.</span><span class="sxs-lookup"><span data-stu-id="52dee-150">There is a fundamental difference between the C#/VB async model and the F# async model.</span></span>

<span data-ttu-id="52dee-151">Döndüren bir işlev çağırdığınızda bir `Task` veya `Task<'T>`, bu iş zaten yürütme başladı.</span><span class="sxs-lookup"><span data-stu-id="52dee-151">When you call a function which returns a `Task` or `Task<'T>`, that job has already begun execution.</span></span> <span data-ttu-id="52dee-152">Döndürülen tanıtıcı zaten çalışan zaman uyumsuz işlemi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="52dee-152">The handle returned represents an already-running asynchronous job.</span></span> <span data-ttu-id="52dee-153">Buna karşılık, çağırdığınızda async işlevi F #'ta `Async<'a>` döndürülen olacağı bir işi temsil eden **oluşturulan** belirli bir noktada.</span><span class="sxs-lookup"><span data-stu-id="52dee-153">In contrast, when you call an async function in F#, the `Async<'a>` returned represents a job which will be **generated** at some point.</span></span> <span data-ttu-id="52dee-154">Bu model anlamak, güçlü, birbirine zincirlenmesi için zaman uyumsuz işler F # için izin verdiğinden daha kolay koşullu gerçekleştirilen ve daha hassas bir denetim çizgisi ile başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="52dee-154">Understanding this model is powerful, because it allows for asynchronous jobs in F# to be chained together easier, performed conditionally, and be started with a finer grain of control.</span></span>

<span data-ttu-id="52dee-155">Diğer birkaç benzerlikler ve eşitlenmeyeceği farklar vardır.</span><span class="sxs-lookup"><span data-stu-id="52dee-155">There are a few other similarities and differences worth noting.</span></span>

### <a name="similarities"></a><span data-ttu-id="52dee-156">Benzerlikler</span><span class="sxs-lookup"><span data-stu-id="52dee-156">Similarities</span></span>

*   <span data-ttu-id="52dee-157">`let!`, `use!`, ve `do!` için benzer `await` bir zaman uyumsuz iş içinden çağrılırken bir `async{ }` bloğu.</span><span class="sxs-lookup"><span data-stu-id="52dee-157">`let!`, `use!`, and `do!` are analogous to `await` when calling an async job from within an `async{ }` block.</span></span>

 <span data-ttu-id="52dee-158">Üç anahtar sözcükler yalnızca içinde kullanılabilir bir `async { }` bloğu, nasıl benzer `await` içinde yalnızca çağrılabilir bir `async` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="52dee-158">The three keywords can only be used within an `async { }` block, similar to how `await` can only be invoked inside an `async` method.</span></span> <span data-ttu-id="52dee-159">Kısacası, `let!` yakalamak ve bir sonucu kullanmak istediğinizde içindir `use!` aynı ancak için kaynakları temizlendi kullanıldığı sonra şeydir ve `do!` tamamlamak için hiçbir değer döndürmeyen bir zaman uyumsuz iş akışı için beklenecek istediğinizde içindir devam etmeden önce.</span><span class="sxs-lookup"><span data-stu-id="52dee-159">In short, `let!` is for when you want to capture and use a result, `use!` is the same but for something whose resources should get cleaned after it’s used, and `do!` is for when you want to wait for an async workflow with no return value to finish before moving on.</span></span>

*   <span data-ttu-id="52dee-160">F # veri paralelliği benzer şekilde destekler.</span><span class="sxs-lookup"><span data-stu-id="52dee-160">F# supports data-parallelism in a similar way.</span></span>

 <span data-ttu-id="52dee-161">Çok farklı şekilde çalışır ancak `Async.Parallel` karşılık gelen `Task.WhenAll` tümü tamamlandığında sonuçları zaman uyumsuz işler kümesinin isteyen senaryoyu için.</span><span class="sxs-lookup"><span data-stu-id="52dee-161">Although it operates very differently, `Async.Parallel` corresponds to `Task.WhenAll` for the scenario of wanting the results of a set of async jobs when they all complete.</span></span>

### <a name="differences"></a><span data-ttu-id="52dee-162">Farkları</span><span class="sxs-lookup"><span data-stu-id="52dee-162">Differences</span></span>

*   <span data-ttu-id="52dee-163">İç içe geçmiş `let!` değil izin, farklı olarak iç içe geçmiş `await`</span><span class="sxs-lookup"><span data-stu-id="52dee-163">Nested `let!` is not allowed, unlike nested `await`</span></span>

 <span data-ttu-id="52dee-164">Farklı `await`, hangi iç içe geçirilemez süresiz olarak, `let!` olamaz ve içinde başka bir kullanmadan önce bağlı sonucu olmalıdır `let!`, `do!`, veya `use!`.</span><span class="sxs-lookup"><span data-stu-id="52dee-164">Unlike `await`, which can be nested indefinitely, `let!` cannot and must have its result bound before using it inside of another `let!`, `do!`, or `use!`.</span></span>

*   <span data-ttu-id="52dee-165">F # C# iptal destek basittir / vb</span><span class="sxs-lookup"><span data-stu-id="52dee-165">Cancellation support is simpler in F# than in C#/VB.</span></span>

 <span data-ttu-id="52dee-166">C# /VB görev yarıda yürütülmesinin aracılığıyla iptaline destek gerekir denetimi `IsCancellationRequested` özelliği veya arama `ThrowIfCancellationRequested()` üzerinde bir `CancellationToken` zaman uyumsuz yönteme geçirilen nesne.</span><span class="sxs-lookup"><span data-stu-id="52dee-166">Supporting cancellation of a task midway through its execution in C#/VB requires checking the `IsCancellationRequested` property or calling `ThrowIfCancellationRequested()` on a `CancellationToken` object that’s passed into the async method.</span></span>

<span data-ttu-id="52dee-167">Buna karşılık, F # zaman uyumsuz iş akışları daha doğal olarak işlem iptal edilemez.</span><span class="sxs-lookup"><span data-stu-id="52dee-167">In contrast, F# async workflows are more naturally cancellable.</span></span> <span data-ttu-id="52dee-168">İptal basit bir üç adımlık işlemdir.</span><span class="sxs-lookup"><span data-stu-id="52dee-168">Cancellation is a simple three-step process.</span></span>

1.  <span data-ttu-id="52dee-169">Yeni bir `CancellationTokenSource`.</span><span class="sxs-lookup"><span data-stu-id="52dee-169">Create a new `CancellationTokenSource`.</span></span>
2.  <span data-ttu-id="52dee-170">Başlangıç bir işlevdeki geçirin.</span><span class="sxs-lookup"><span data-stu-id="52dee-170">Pass it into a starting function.</span></span>
3.  <span data-ttu-id="52dee-171">Çağrı `Cancel` belirtecine.</span><span class="sxs-lookup"><span data-stu-id="52dee-171">Call `Cancel` on the token.</span></span>

<span data-ttu-id="52dee-172">Örnek:</span><span class="sxs-lookup"><span data-stu-id="52dee-172">Example:</span></span>

```fsharp
open System
open System.Net

let uploadDataAsync url data = 
    async {
        let uri = Uri(url)
        use webClient = new WebClient()
        webClient.UploadStringAsync(uri, data)
    }

let workflow = uploadDataAsync "https://url-to-upload-to.com" "hello, world!"

let token = new CancellationTokenSource()
Async.Start (workflow, token)

// Immediately cancel uploadDataAsync after it's been started.
token.Cancel()
```

<span data-ttu-id="52dee-173">Ve bu kadar!</span><span class="sxs-lookup"><span data-stu-id="52dee-173">And that’s it!</span></span>

## <a name="further-resources"></a><span data-ttu-id="52dee-174">Ek kaynaklar:</span><span class="sxs-lookup"><span data-stu-id="52dee-174">Further resources:</span></span>

*   [<span data-ttu-id="52dee-175">MSDN'de zaman uyumsuz iş akışları</span><span class="sxs-lookup"><span data-stu-id="52dee-175">Async Workflows on MSDN</span></span>](https://msdn.microsoft.com/library/dd233250.aspx)
*   [<span data-ttu-id="52dee-176">F # için zaman uyumsuz sıraları</span><span class="sxs-lookup"><span data-stu-id="52dee-176">Asynchronous Sequences for F#</span></span>](https://fsprojects.github.io/FSharp.Control.AsyncSeq/library/AsyncSeq.html)
*   [<span data-ttu-id="52dee-177">F # veri HTTP yardımcı programları</span><span class="sxs-lookup"><span data-stu-id="52dee-177">F# Data HTTP Utilities</span></span>](https://fsharp.github.io/FSharp.Data/library/Http.html)
