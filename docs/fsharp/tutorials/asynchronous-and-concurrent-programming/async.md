---
title: Zaman uyumsuz programlama
description: Bilgi nasıl F# zaman uyumsuz programlama, kullanımı kolay ve doğal dil için dil düzeyinde bir programlama modeli aracılığıyla gerçekleştirilir.
ms.date: 06/20/2016
ms.openlocfilehash: 6925a0132f9beed6be5f9dded3630b551072bea2
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59343460"
---
# <a name="async-programming-in-f"></a><span data-ttu-id="49d1e-103">Zaman uyumsuz programlamada, F\#</span><span class="sxs-lookup"><span data-stu-id="49d1e-103">Async Programming in F\#</span></span>

> [!NOTE]
> <span data-ttu-id="49d1e-104">Bu makaledeki bazı hatalar bulundu.</span><span class="sxs-lookup"><span data-stu-id="49d1e-104">Some inaccuracies have been discovered in this article.</span></span>  <span data-ttu-id="49d1e-105">Bunu yeniden yazılıyor.</span><span class="sxs-lookup"><span data-stu-id="49d1e-105">It is being rewritten.</span></span>  <span data-ttu-id="49d1e-106">Bkz: [sorun #666](https://github.com/dotnet/docs/issues/666) değişiklikler hakkında bilgi edinmek için.</span><span class="sxs-lookup"><span data-stu-id="49d1e-106">See [Issue #666](https://github.com/dotnet/docs/issues/666) to learn about the changes.</span></span>

<span data-ttu-id="49d1e-107">Zaman uyumsuz programlama F# kullanımı kolay ve doğal dil için tasarlanmış bir dil düzeyi programlama modeli aracılığıyla gerçekleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="49d1e-107">Async programming in F# can be accomplished through a language-level programming model designed to be easy to use and natural to the language.</span></span>

<span data-ttu-id="49d1e-108">Zaman uyumsuz programlama setinin F# olduğu `Async<'T>`, arka planda çalışmaya devam tetiklenen iş gösterimini burada `'T` ya da türü özel döndürülür `return` anahtar sözcüğü veya `unit` , zaman uyumsuz iş akışı döndürülecek sonuç var.</span><span class="sxs-lookup"><span data-stu-id="49d1e-108">The core of async programming in F# is `Async<'T>`, a representation of work that can be triggered to run in the background, where `'T` is either the type returned via the special `return` keyword or `unit` if the async workflow has no result to return.</span></span>

<span data-ttu-id="49d1e-109">Bir zaman uyumsuz ifadesinin türü olduğunu anlamak için en önemli kavram olan `Async<'T>`, olan yalnızca bir _belirtimi_ zaman uyumsuz bir bağlamda yapılacak iş.</span><span class="sxs-lookup"><span data-stu-id="49d1e-109">The key concept to understand is that an async expression’s type is `Async<'T>`, which is merely a _specification_ of work to be done in an asynchronous context.</span></span> <span data-ttu-id="49d1e-110">Açıkça başlangıç işlevlerden biri ile başlattığınızda kadar yürütülmez (gibi `Async.RunSynchronously`).</span><span class="sxs-lookup"><span data-stu-id="49d1e-110">It is not executed until you explicitly start it with one of the starting functions (such as `Async.RunSynchronously`).</span></span> <span data-ttu-id="49d1e-111">Bu iş yapma hakkında düşünmek için farklı bir şekilde olsa da, uygulamada oldukça basit olan sona erer.</span><span class="sxs-lookup"><span data-stu-id="49d1e-111">Although this is a different way of thinking about doing work, it ends up being quite simple in practice.</span></span>

<span data-ttu-id="49d1e-112">Örneğin, ana iş parçacığını engellemeden dotnetfoundation.org HTML indirmek istediğinizi düşünelim.</span><span class="sxs-lookup"><span data-stu-id="49d1e-112">For example, say you wanted to download the HTML from dotnetfoundation.org without blocking the main thread.</span></span> <span data-ttu-id="49d1e-113">Bunu şu şekilde gerçekleştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="49d1e-113">You can accomplish it like this:</span></span>

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

<span data-ttu-id="49d1e-114">Ve İşte bu kadar!</span><span class="sxs-lookup"><span data-stu-id="49d1e-114">And that’s it!</span></span> <span data-ttu-id="49d1e-115">Kullanımı dışında `async`, `let!`, ve `return`, bu yalnızca normal F# kod.</span><span class="sxs-lookup"><span data-stu-id="49d1e-115">Aside from the use of `async`, `let!`, and `return`, this is just normal F# code.</span></span>

<span data-ttu-id="49d1e-116">Dikkate almaya değer birkaç söz dizimi yapıları vardır:</span><span class="sxs-lookup"><span data-stu-id="49d1e-116">There are a few syntactical constructs which are worth noting:</span></span>

*   `let!` <span data-ttu-id="49d1e-117">(Bu, başka bir bağlamda çalışır) zaman uyumsuz ifadenin sonucu bağlar.</span><span class="sxs-lookup"><span data-stu-id="49d1e-117">binds the result of an async expression (which runs on another context).</span></span>
*   `use!` <span data-ttu-id="49d1e-118">yalnızca gibi çalışır `let!`, ancak kapsam dışına çıktığında bağımlı kaynaklarını siler.</span><span class="sxs-lookup"><span data-stu-id="49d1e-118">works just like `let!`, but disposes its bound resources when it goes out of scope.</span></span>
*   `do!` <span data-ttu-id="49d1e-119">hiçbir şey döndürmeyen bir zaman uyumsuz iş akışı await.</span><span class="sxs-lookup"><span data-stu-id="49d1e-119">will await an async workflow which doesn’t return anything.</span></span>
*   `return` <span data-ttu-id="49d1e-120">yalnızca bir async ifadesinden bir sonuç döndürür.</span><span class="sxs-lookup"><span data-stu-id="49d1e-120">simply returns a result from an async expression.</span></span>
*   `return!` <span data-ttu-id="49d1e-121">başka bir zaman uyumsuz iş akışı çalıştırır ve sonuç olarak, dönüş değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="49d1e-121">executes another async workflow and returns its return value as a result.</span></span>

<span data-ttu-id="49d1e-122">Ayrıca, normal `let`, `use`, ve `do` anahtar sözcükleri normal işlevinde olduğu gibi zaman uyumsuz sürümleri ile birlikte kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="49d1e-122">Additionally, normal `let`, `use`, and `do` keywords can be used alongside the async versions just as they would in a normal function.</span></span>

## <a name="how-to-start-async-code-in-f"></a><span data-ttu-id="49d1e-123">Zaman uyumsuz kod içinde F başlatma\#</span><span class="sxs-lookup"><span data-stu-id="49d1e-123">How to start Async Code in F\#</span></span>

<span data-ttu-id="49d1e-124">Daha önce bahsedildiği gibi zaman uyumsuz kodu açıkça başlatılması gereken başka bir bağlamda yapılacak iş belirtimidir.</span><span class="sxs-lookup"><span data-stu-id="49d1e-124">As mentioned earlier, async code is a specification of work to be done in another context which needs to be explicitly started.</span></span> <span data-ttu-id="49d1e-125">Bunu yapmanın birincil iki yolu vardır:</span><span class="sxs-lookup"><span data-stu-id="49d1e-125">Here are two primary ways to accomplish this:</span></span>

1. `Async.RunSynchronously` <span data-ttu-id="49d1e-126">başka bir iş parçacığında bir zaman uyumsuz iş akışı başlatılacağından ve sonucunu bekler.</span><span class="sxs-lookup"><span data-stu-id="49d1e-126">will start an async workflow on another thread and await its result.</span></span>

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

2. `Async.Start` <span data-ttu-id="49d1e-127">başka bir iş parçacığında zaman uyumsuz bir iş akışını başlatmak ve olacak **değil** sonucunu bekler.</span><span class="sxs-lookup"><span data-stu-id="49d1e-127">will start an async workflow on another thread, and will **not** await its result.</span></span>

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

<span data-ttu-id="49d1e-128">Bir zaman uyumsuz iş akışı daha özel senaryoları için kullanılabilir başlatmak için farklı yöntemleri vardır.</span><span class="sxs-lookup"><span data-stu-id="49d1e-128">There are other ways to start an async workflow available for more specific scenarios.</span></span> <span data-ttu-id="49d1e-129">Ayrıntılı olan [zaman uyumsuz başvurusu](https://msdn.microsoft.com/library/ee370232.aspx).</span><span class="sxs-lookup"><span data-stu-id="49d1e-129">They are detailed [in the Async reference](https://msdn.microsoft.com/library/ee370232.aspx).</span></span>

### <a name="a-note-on-threads"></a><span data-ttu-id="49d1e-130">İş parçacığı üzerinde Not</span><span class="sxs-lookup"><span data-stu-id="49d1e-130">A Note on Threads</span></span>

<span data-ttu-id="49d1e-131">Deyimini "başka bir iş parçacığı" yukarıda belirtilen ancak bilmek önemlidir **bu zaman uyumsuz iş akışları için bir cephe olduğunu gelmez çoklu iş parçacığı kullanımı**.</span><span class="sxs-lookup"><span data-stu-id="49d1e-131">The phrase "on another thread" is mentioned above, but it is important to know that **this does not mean that async workflows are a facade for multithreading**.</span></span> <span data-ttu-id="49d1e-132">İş akışı gerçekten "iş parçacıkları, bunları küçük bir kullanışlı kitaplıklarımızı zaman miktarı için ödünç arasında atlar".</span><span class="sxs-lookup"><span data-stu-id="49d1e-132">The workflow actually "jumps" between threads, borrowing them for a small amount of time to do useful work.</span></span> <span data-ttu-id="49d1e-133">Bir zaman uyumsuz iş akışı etkili bir şekilde "(örneğin, bir şey döndürülecek ağ arama için bekleniyor) beklediği sırada" zaman ödünç herhangi bir iş parçacığı, go yapmak yararlı iş başka bir şey kadar serbest bırakılır.</span><span class="sxs-lookup"><span data-stu-id="49d1e-133">When an async workflow is effectively "waiting" (for example, waiting for a network call to return something), any thread it was borrowing at the time is freed up to go do useful work on something else.</span></span> <span data-ttu-id="49d1e-134">Bu zaman uyumsuz iş akışları, sistem çalıştıkları mümkün olduğunca etkili bir şekilde kullanmasına izin verir ve yüksek hacimli g/ç senaryoları için özellikle güçlü hale getirir.</span><span class="sxs-lookup"><span data-stu-id="49d1e-134">This allows async workflows to utilize the system they run on as effectively as possible, and makes them especially strong for high-volume I/O scenarios.</span></span>

## <a name="how-to-add-parallelism-to-async-code"></a><span data-ttu-id="49d1e-135">Zaman uyumsuz kod için paralellik ekleme</span><span class="sxs-lookup"><span data-stu-id="49d1e-135">How to Add Parallelism to Async Code</span></span>

<span data-ttu-id="49d1e-136">Bazen, paralel olarak birden çok zaman uyumsuz işler gerçekleştirmek için sonuçlarını toplamak ve bunları başka bir yolla yorumlar.</span><span class="sxs-lookup"><span data-stu-id="49d1e-136">Sometimes you may need to perform multiple asynchronous jobs in parallel, collect their results, and interpret them in some way.</span></span> `Async.Parallel` <span data-ttu-id="49d1e-137">Bu görev paralel coerce gerek kalmadan kapsayacaktır kitaplığı kullanmak zorunda kalmadan gerçekleştirmenize izin verir `Task<'T>` ve `Async<'T>` türleri.</span><span class="sxs-lookup"><span data-stu-id="49d1e-137">allows you to do this without needing to use the Task Parallel Library, which would involve needing to coerce `Task<'T>` and `Async<'T>` types.</span></span>

<span data-ttu-id="49d1e-138">Aşağıdaki örnekte `Async.Parallel` paralel dört popüler sitelerden HTML indirmek için bu görevleri tamamlamak bekleyin ve sonra indirilen HTML yazdırın.</span><span class="sxs-lookup"><span data-stu-id="49d1e-138">The following example will use `Async.Parallel` to download the HTML from four popular sites in parallel, wait for those tasks to complete, and then print the HTML which was downloaded.</span></span>

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

## <a name="important-info-and-advice"></a><span data-ttu-id="49d1e-139">Önemli bilgiler ve öneriler</span><span class="sxs-lookup"><span data-stu-id="49d1e-139">Important Info and Advice</span></span>

*   <span data-ttu-id="49d1e-140">"Async" tükettiğiniz tüm işlevleri sonuna</span><span class="sxs-lookup"><span data-stu-id="49d1e-140">Append "Async" to the end of any functions you’ll consume</span></span>

 <span data-ttu-id="49d1e-141">Bu yalnızca bir adlandırma kuralı olsa da, API keşfedilebilirliğini gibi şeyleri kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="49d1e-141">Although this is just a naming convention, it does make things like API discoverability easier.</span></span> <span data-ttu-id="49d1e-142">Özellikle varsa aynı yordamı zaman uyumlu ve zaman uyumsuz sürümlerini açıkça adı zaman uyumsuz olduğu durum için iyi bir fikirdir.</span><span class="sxs-lookup"><span data-stu-id="49d1e-142">Particularly if there are synchronous and asynchronous versions of the same routine, it’s a good idea to explicitly state which is asynchronous via the name.</span></span>

*   <span data-ttu-id="49d1e-143">Derleyiciye dinleyin!</span><span class="sxs-lookup"><span data-stu-id="49d1e-143">Listen to the compiler!</span></span>

 <span data-ttu-id="49d1e-144">F#ın derleyici çok katı, neredeyse imkansız vericidir gibi bir şey yapmadan "async" kod eşzamanlı olarak çalıştır.</span><span class="sxs-lookup"><span data-stu-id="49d1e-144">F#’s compiler is very strict, making it nearly impossible to do something troubling like run "async" code synchronously.</span></span> <span data-ttu-id="49d1e-145">Bir uyarı arasında geliyorsa, kod nasıl çalışır düşündüğünüz yürütme olmaz işareti olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="49d1e-145">If you come across a warning, that’s a sign that the code won’t execute how you think it will.</span></span> <span data-ttu-id="49d1e-146">Derleyici mutlu yapabilirsiniz, kodunuzu büyük olasılıkla beklenen şekilde çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="49d1e-146">If you can make the compiler happy, your code will most likely execute as expected.</span></span>

## <a name="for-the-cvb-programmer-looking-into-f"></a><span data-ttu-id="49d1e-147">İçin C#/VB Programcı F aranıyor\#</span><span class="sxs-lookup"><span data-stu-id="49d1e-147">For the C#/VB Programmer Looking Into F\#</span></span>

<span data-ttu-id="49d1e-148">Bu bölümde zaman uyumsuz model hakkında bilgi sahibi olduğunuz varsayılır C#/VB.</span><span class="sxs-lookup"><span data-stu-id="49d1e-148">This section assumes you’re familiar with the async model in C#/VB.</span></span> <span data-ttu-id="49d1e-149">Kullanmıyorsanız, [zaman uyumsuz programlamada C# ](../../../csharp/async.md) bir başlangıç noktasıdır.</span><span class="sxs-lookup"><span data-stu-id="49d1e-149">If you are not, [Async Programming in C#](../../../csharp/async.md) is a starting point.</span></span>

<span data-ttu-id="49d1e-150">Bir temel fark arasında C#/VB zaman uyumsuz model ve F# zaman uyumsuz model.</span><span class="sxs-lookup"><span data-stu-id="49d1e-150">There is a fundamental difference between the C#/VB async model and the F# async model.</span></span>

<span data-ttu-id="49d1e-151">Döndüren bir işlev çağırdığınızda bir `Task` veya `Task<'T>`, o işin yürütme zaten başladı.</span><span class="sxs-lookup"><span data-stu-id="49d1e-151">When you call a function which returns a `Task` or `Task<'T>`, that job has already begun execution.</span></span> <span data-ttu-id="49d1e-152">Döndürülen tanıtıcı zaten çalışan bir zaman uyumsuz işi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="49d1e-152">The handle returned represents an already-running asynchronous job.</span></span> <span data-ttu-id="49d1e-153">Buna karşılık, çağırdığınızda bir zaman uyumsuz işlev F#, `Async<'a>` döndürülen olacağı işi temsil **oluşturulan** belirli bir noktada.</span><span class="sxs-lookup"><span data-stu-id="49d1e-153">In contrast, when you call an async function in F#, the `Async<'a>` returned represents a job which will be **generated** at some point.</span></span> <span data-ttu-id="49d1e-154">Bu model anlamak, güçlü, zaman uyumsuz işler için izin verdiğinden F# birbirine zincirlenmiş için daha kolay koşullu olarak gerçekleştirilen ve Denetim ile daha hassas bir çizgisi başlatılması.</span><span class="sxs-lookup"><span data-stu-id="49d1e-154">Understanding this model is powerful, because it allows for asynchronous jobs in F# to be chained together easier, performed conditionally, and be started with a finer grain of control.</span></span>

<span data-ttu-id="49d1e-155">Diğer bazı benzerlikler ve önemli farklar vardır.</span><span class="sxs-lookup"><span data-stu-id="49d1e-155">There are a few other similarities and differences worth noting.</span></span>

### <a name="similarities"></a><span data-ttu-id="49d1e-156">Benzerlikler</span><span class="sxs-lookup"><span data-stu-id="49d1e-156">Similarities</span></span>

*   `let!`<span data-ttu-id="49d1e-157">, `use!`, ve `do!` için benzer `await` bir zaman uyumsuz iş içinden çağrılırken bir `async{ }` blok.</span><span class="sxs-lookup"><span data-stu-id="49d1e-157">, `use!`, and `do!` are analogous to `await` when calling an async job from within an `async{ }` block.</span></span>

 <span data-ttu-id="49d1e-158">Üç anahtar sözcükler yalnızca içinde kullanılabilir bir `async { }` bloğu nasıl benzer `await` içinde yalnızca çağrılabilen bir `async` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="49d1e-158">The three keywords can only be used within an `async { }` block, similar to how `await` can only be invoked inside an `async` method.</span></span> <span data-ttu-id="49d1e-159">Kısacası, `let!` yakalamak ve bir sonucu kullanmak istediğinizde içindir `use!` aynı ancak için kaynaklarını temizlendi kullanıldığı sonra bir şeydir ve `do!` tamamlamak için hiçbir değer döndürmeyen bir zaman uyumsuz iş akışı beklemek istediğinizde içindir devam etmeden önce.</span><span class="sxs-lookup"><span data-stu-id="49d1e-159">In short, `let!` is for when you want to capture and use a result, `use!` is the same but for something whose resources should get cleaned after it’s used, and `do!` is for when you want to wait for an async workflow with no return value to finish before moving on.</span></span>

*   <span data-ttu-id="49d1e-160">F#Veri paralelliği benzer şekilde destekler.</span><span class="sxs-lookup"><span data-stu-id="49d1e-160">F# supports data-parallelism in a similar way.</span></span>

 <span data-ttu-id="49d1e-161">Çok farklı bir şekilde çalışır ancak `Async.Parallel` karşılık gelen `Task.WhenAll` tümü tamamlandığında, birtakım zaman uyumsuz işler sonuçları isteyen senaryosu için.</span><span class="sxs-lookup"><span data-stu-id="49d1e-161">Although it operates very differently, `Async.Parallel` corresponds to `Task.WhenAll` for the scenario of wanting the results of a set of async jobs when they all complete.</span></span>

### <a name="differences"></a><span data-ttu-id="49d1e-162">Farkları</span><span class="sxs-lookup"><span data-stu-id="49d1e-162">Differences</span></span>

*   <span data-ttu-id="49d1e-163">İç içe geçmiş `let!` değil izin, farklı olarak iç içe geçmiş</span><span class="sxs-lookup"><span data-stu-id="49d1e-163">Nested `let!` is not allowed, unlike nested</span></span> `await`

 <span data-ttu-id="49d1e-164">Farklı `await`, iç içe geçirilemez, `let!` olamaz ve başka içinde kullanmadan önce ilişkili sonucu olmalıdır `let!`, `do!`, veya `use!`.</span><span class="sxs-lookup"><span data-stu-id="49d1e-164">Unlike `await`, which can be nested indefinitely, `let!` cannot and must have its result bound before using it inside of another `let!`, `do!`, or `use!`.</span></span>

*   <span data-ttu-id="49d1e-165">İptal desteği basittir F# kıyasla C#/VB.</span><span class="sxs-lookup"><span data-stu-id="49d1e-165">Cancellation support is simpler in F# than in C#/VB.</span></span>

 <span data-ttu-id="49d1e-166">Bir görev sürecin yarısında, yürütme iptalini destekleyen C#/VB gerektirir denetimi `IsCancellationRequested` özelliği veya arama `ThrowIfCancellationRequested()` üzerinde bir `CancellationToken` zaman uyumsuz yönteme geçirilen nesne.</span><span class="sxs-lookup"><span data-stu-id="49d1e-166">Supporting cancellation of a task midway through its execution in C#/VB requires checking the `IsCancellationRequested` property or calling `ThrowIfCancellationRequested()` on a `CancellationToken` object that’s passed into the async method.</span></span>

<span data-ttu-id="49d1e-167">Buna karşılık, F# doğal olarak edilebilen zaman uyumsuz iş akışları.</span><span class="sxs-lookup"><span data-stu-id="49d1e-167">In contrast, F# async workflows are more naturally cancellable.</span></span> <span data-ttu-id="49d1e-168">İptal basit bir üç adımlık işlemdir.</span><span class="sxs-lookup"><span data-stu-id="49d1e-168">Cancellation is a simple three-step process.</span></span>

1. <span data-ttu-id="49d1e-169">Yeni bir `CancellationTokenSource`.</span><span class="sxs-lookup"><span data-stu-id="49d1e-169">Create a new `CancellationTokenSource`.</span></span>
2. <span data-ttu-id="49d1e-170">Bir başlangıç işlevine geçirin.</span><span class="sxs-lookup"><span data-stu-id="49d1e-170">Pass it into a starting function.</span></span>
3. <span data-ttu-id="49d1e-171">Çağrı `Cancel` belirtecine.</span><span class="sxs-lookup"><span data-stu-id="49d1e-171">Call `Cancel` on the token.</span></span>

<span data-ttu-id="49d1e-172">Örnek:</span><span class="sxs-lookup"><span data-stu-id="49d1e-172">Example:</span></span>

```fsharp
open System.Threading

// Create a workflow which will loop forever.
let workflow =
    async {
        while true do
            printfn "Working..."
            do! Async.Sleep 1000
    }
    
let tokenSource = new CancellationTokenSource()

// Start the workflow in the background
Async.Start (workflow, tokenSource.Token)

// Executing the next line will stop the workflow
tokenSource.Cancel()
```

<span data-ttu-id="49d1e-173">Ve İşte bu kadar!</span><span class="sxs-lookup"><span data-stu-id="49d1e-173">And that’s it!</span></span>

## <a name="further-resources"></a><span data-ttu-id="49d1e-174">Ek kaynaklar:</span><span class="sxs-lookup"><span data-stu-id="49d1e-174">Further resources:</span></span>

*   [<span data-ttu-id="49d1e-175">MSDN üzerinde zaman uyumsuz iş akışları</span><span class="sxs-lookup"><span data-stu-id="49d1e-175">Async Workflows on MSDN</span></span>](https://msdn.microsoft.com/library/dd233250.aspx)
*   [<span data-ttu-id="49d1e-176">Zaman uyumsuz sıraları içinF#</span><span class="sxs-lookup"><span data-stu-id="49d1e-176">Asynchronous Sequences for F#</span></span>](https://fsprojects.github.io/FSharp.Control.AsyncSeq/library/AsyncSeq.html)
*   [<span data-ttu-id="49d1e-177">F#Veri HTTP yardımcı programları</span><span class="sxs-lookup"><span data-stu-id="49d1e-177">F# Data HTTP Utilities</span></span>](https://fsharp.github.io/FSharp.Data/library/Http.html)