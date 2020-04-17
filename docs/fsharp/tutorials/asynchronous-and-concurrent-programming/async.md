---
title: Async Programlama
description: F#'nın temel işlevsel programlama kavramlarından türetilen dil düzeyindebir programlama modeline dayalı olarak eş zamanlılık için nasıl temiz destek sağladığını öğrenin.
ms.date: 12/17/2018
ms.openlocfilehash: 9b2e3057c126d84474c21fde653da5bbee32938a
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/17/2020
ms.locfileid: "81608042"
---
# <a name="async-programming-in-f"></a><span data-ttu-id="99f2c-103">F'de Async programlama\#</span><span class="sxs-lookup"><span data-stu-id="99f2c-103">Async programming in F\#</span></span>

<span data-ttu-id="99f2c-104">Asynchronous programlama çeşitli nedenlerle modern uygulamalar için gerekli olan bir mekanizmadır.</span><span class="sxs-lookup"><span data-stu-id="99f2c-104">Asynchronous programming is a mechanism that is essential to modern applications for diverse reasons.</span></span> <span data-ttu-id="99f2c-105">Çoğu geliştiricinin karşılaşacağı iki birincil kullanım örnekleri vardır:</span><span class="sxs-lookup"><span data-stu-id="99f2c-105">There are two primary use cases that most developers will encounter:</span></span>

- <span data-ttu-id="99f2c-106">İstek işleme işlemi, bu işlemin dışındaki sistemlerden veya hizmetlerden gelen girişleri beklerken, meşgul olan sistem kaynaklarını en aza indirirken, önemli sayıda eşzamanlı gelen isteke hizmet verebilen bir sunucu işlemi sunmak</span><span class="sxs-lookup"><span data-stu-id="99f2c-106">Presenting a server process that can service a significant number of concurrent incoming requests, while minimizing the system resources occupied while request processing awaits inputs from systems or services external to that process</span></span>
- <span data-ttu-id="99f2c-107">Arka plan çalışmasını aynı anda ilerletirken yanıt veren bir ui veya ana iş parçacığı koruma</span><span class="sxs-lookup"><span data-stu-id="99f2c-107">Maintaining a responsive UI or main thread while concurrently progressing background work</span></span>

<span data-ttu-id="99f2c-108">Arka plan çalışmaları genellikle birden çok iş parçacığı kullanımını içerse de, eş zamanlı ve çoklu iş parçacığı kavramlarını ayrı ayrı dikkate almak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="99f2c-108">Although background work often does involve the utilization of multiple threads, it's important to consider the concepts of asynchrony and multi-threading separately.</span></span> <span data-ttu-id="99f2c-109">Aslında, onlar ayrı endişeler, ve biri diğer anlamına gelmez.</span><span class="sxs-lookup"><span data-stu-id="99f2c-109">In fact, they are separate concerns, and one does not imply the other.</span></span> <span data-ttu-id="99f2c-110">Bu makalede aşağıdaki ler bunu daha ayrıntılı olarak açıklar.</span><span class="sxs-lookup"><span data-stu-id="99f2c-110">What follows in this article describes this in more detail.</span></span>

## <a name="asynchrony-defined"></a><span data-ttu-id="99f2c-111">Asynchrony tanımlı</span><span class="sxs-lookup"><span data-stu-id="99f2c-111">Asynchrony defined</span></span>

<span data-ttu-id="99f2c-112">Önceki nokta - bu eşzamanlılık birden fazla iş parçacığı kullanımı bağımsızdır - biraz daha fazla açıklamaya değer.</span><span class="sxs-lookup"><span data-stu-id="99f2c-112">The previous point - that asynchrony is independent of the utilization of multiple threads - is worth explaining a bit further.</span></span> <span data-ttu-id="99f2c-113">Bazen ilişkili olan, ancak birbirinden tamamen bağımsız olan üç kavram vardır:</span><span class="sxs-lookup"><span data-stu-id="99f2c-113">There are three concepts that are sometimes related, but strictly independent of one another:</span></span>

- <span data-ttu-id="99f2c-114">Eşzamanlılık; çakışan dönemlerde birden çok hesaplama yürütüldüğünde.</span><span class="sxs-lookup"><span data-stu-id="99f2c-114">Concurrency; when multiple computations execute in overlapping time periods.</span></span>
- <span data-ttu-id="99f2c-115">Paralellik; birden çok hesaplama veya tek bir hesaplamanın birkaç bölümü tam olarak aynı anda çalıştırıldığında.</span><span class="sxs-lookup"><span data-stu-id="99f2c-115">Parallelism; when multiple computations or several parts of a single computation run at exactly the same time.</span></span>
- <span data-ttu-id="99f2c-116">Asynchrony; bir veya daha fazla hesaplama ana program akışından ayrı olarak yürütebilir.</span><span class="sxs-lookup"><span data-stu-id="99f2c-116">Asynchrony; when one or more computations can execute separately from the main program flow.</span></span>

<span data-ttu-id="99f2c-117">Her üç ortogonal kavramlar, ama kolayca conflated olabilir, özellikle birlikte kullanılır.</span><span class="sxs-lookup"><span data-stu-id="99f2c-117">All three are orthogonal concepts, but can be easily conflated, especially when they are used together.</span></span> <span data-ttu-id="99f2c-118">Örneğin, birden çok eşzamanlı hesaplamayı paralel olarak yürütmeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="99f2c-118">For example, you may need to execute multiple asynchronous computations in parallel.</span></span> <span data-ttu-id="99f2c-119">Bu paralellik veya eşzamanlılık birbirini ima anlamına gelmez.</span><span class="sxs-lookup"><span data-stu-id="99f2c-119">This does not mean that parallelism or asynchrony imply one another.</span></span>

<span data-ttu-id="99f2c-120">"Asynchronous" kelimesinin etimolojisini göz önünde bulundurursanız, iki parça vardır:</span><span class="sxs-lookup"><span data-stu-id="99f2c-120">If you consider the etymology of the word "asynchronous", there are two pieces involved:</span></span>

- <span data-ttu-id="99f2c-121">"a", "değil" anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="99f2c-121">"a", meaning "not".</span></span>
- <span data-ttu-id="99f2c-122">"senkron", "aynı anda" anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="99f2c-122">"synchronous", meaning "at the same time".</span></span>

<span data-ttu-id="99f2c-123">Bu iki terimi bir araya getirdiğinizde, "eşzamanlı"nın "aynı anda değil" anlamına geldiğini görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="99f2c-123">When you put these two terms together, you'll see that "asynchronous" means "not at the same time".</span></span> <span data-ttu-id="99f2c-124">İşte bu kadar!</span><span class="sxs-lookup"><span data-stu-id="99f2c-124">That's it!</span></span> <span data-ttu-id="99f2c-125">Bu tanımda eşzamanlılık veya paralellik iması yoktur.</span><span class="sxs-lookup"><span data-stu-id="99f2c-125">There is no implication of concurrency or parallelism in this definition.</span></span> <span data-ttu-id="99f2c-126">Bu uygulamada da geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="99f2c-126">This is also true in practice.</span></span>

<span data-ttu-id="99f2c-127">Pratik açıdan, F# daki eşzamanlı hesaplamalar ana program akışından bağımsız olarak yürütülecek şekilde zamanlanır.</span><span class="sxs-lookup"><span data-stu-id="99f2c-127">In practical terms, asynchronous computations in F# are scheduled to execute independently of the main program flow.</span></span> <span data-ttu-id="99f2c-128">Bu eşzamanlılık veya paralellik anlamına gelmez, ne de bir hesaplama her zaman arka planda olur anlamına gelmez.</span><span class="sxs-lookup"><span data-stu-id="99f2c-128">This doesn't imply concurrency or parallelism, nor does it imply that a computation always happens in the background.</span></span> <span data-ttu-id="99f2c-129">Aslında, eşzamanlı hesaplamalar, hesaplamanın doğasına ve hesaplamanın yürütüldettiği ortama bağlı olarak eşzamanlı olarak bile yürütülebilir.</span><span class="sxs-lookup"><span data-stu-id="99f2c-129">In fact, asynchronous computations can even execute synchronously, depending on the nature of the computation and the environment the computation is executing in.</span></span>

<span data-ttu-id="99f2c-130">Sahip olması gereken ana paket, asynchronöz hesaplamaların ana program akışından bağımsız olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="99f2c-130">The main takeaway you should have is that asynchronous computations are independent of the main program flow.</span></span> <span data-ttu-id="99f2c-131">Eşzamanlı hesaplamanın ne zaman veya nasıl yürütüldüğü konusunda az garanti olmasına rağen, bunları planlamak ve planlamak için bazı yaklaşımlar vardır.</span><span class="sxs-lookup"><span data-stu-id="99f2c-131">Although there are few guarantees about when or how an asynchronous computation executes, there are some approaches to orchestrating and scheduling them.</span></span> <span data-ttu-id="99f2c-132">Bu makalenin geri kalanında, F# eşzamanlılığı ve F# içine yerleşik tür, işlev ve ifadelerin nasıl kullanılacağı ile ilgili temel kavramlar incelenir.</span><span class="sxs-lookup"><span data-stu-id="99f2c-132">The rest of this article explores core concepts for F# asynchrony and how to use the types, functions, and expressions built into F#.</span></span>

## <a name="core-concepts"></a><span data-ttu-id="99f2c-133">Temel kavramlar</span><span class="sxs-lookup"><span data-stu-id="99f2c-133">Core concepts</span></span>

<span data-ttu-id="99f2c-134">F#'da, asynchronous programlama üç temel kavram etrafında ortalanır:</span><span class="sxs-lookup"><span data-stu-id="99f2c-134">In F#, asynchronous programming is centered around three core concepts:</span></span>

- <span data-ttu-id="99f2c-135">Tek `Async<'T>` bir eşzamanlı hesaplamayı temsil eden tür.</span><span class="sxs-lookup"><span data-stu-id="99f2c-135">The `Async<'T>` type, which represents a composable asynchronous computation.</span></span>
- <span data-ttu-id="99f2c-136">Asynchronous `Async` çalışmasını zamanlamanızı, asynchronous hesaplamaları oluşturmanızı ve eşzamanlı sonuçları dönüştürmenizi sağlayan modül işlevleri.</span><span class="sxs-lookup"><span data-stu-id="99f2c-136">The `Async` module functions, which let you schedule asynchronous work, compose asynchronous computations, and transform asynchronous results.</span></span>
- <span data-ttu-id="99f2c-137">Asynchronöz `async { }` hesaplamaları oluşturmak ve denetlemek için uygun bir sözdizimi sağlayan [hesaplama ifadesi.](../../language-reference/computation-expressions.md)</span><span class="sxs-lookup"><span data-stu-id="99f2c-137">The `async { }` [computation expression](../../language-reference/computation-expressions.md), which provides a convenient syntax for building and controlling asynchronous computations.</span></span>

<span data-ttu-id="99f2c-138">Aşağıdaki örnekte bu üç kavramı görebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="99f2c-138">You can see these three concepts in the following example:</span></span>

```fsharp
open System
open System.IO

let printTotalFileBytes path =
    async {
        let! bytes = File.ReadAllBytesAsync(path) |> Async.AwaitTask
        let fileName = Path.GetFileName(path)
        printfn "File %s has %d bytes" fileName bytes.Length
    }

[<EntryPoint>]
let main argv =
    printTotalFileBytes "path-to-file.txt"
    |> Async.RunSynchronously

    Console.Read() |> ignore
    0
```

<span data-ttu-id="99f2c-139">Örnekte, `printTotalFileBytes` işlev türü. `string -> Async<unit>`</span><span class="sxs-lookup"><span data-stu-id="99f2c-139">In the example, the `printTotalFileBytes` function is of type `string -> Async<unit>`.</span></span> <span data-ttu-id="99f2c-140">İşlev çağırma aslında asynchronous hesaplama yürütmez.</span><span class="sxs-lookup"><span data-stu-id="99f2c-140">Calling the function does not actually execute the asynchronous computation.</span></span> <span data-ttu-id="99f2c-141">Bunun yerine, `Async<unit>` eşzamanlı olarak yürütmek için işin bir *belirtimi* olarak hareket eden bir döndürür.</span><span class="sxs-lookup"><span data-stu-id="99f2c-141">Instead, it returns an `Async<unit>` that acts as a *specification* of the work that is to execute asynchronously.</span></span> <span data-ttu-id="99f2c-142">Bu `Async.AwaitTask` uygun bir tür sonucu <xref:System.IO.File.ReadAllBytesAsync%2A> dönüştürür kendi vücudunda çağırır.</span><span class="sxs-lookup"><span data-stu-id="99f2c-142">It calls `Async.AwaitTask` in its body, which converts the result of <xref:System.IO.File.ReadAllBytesAsync%2A> to an appropriate type.</span></span>

<span data-ttu-id="99f2c-143">Bir diğer önemli satır `Async.RunSynchronously`da.</span><span class="sxs-lookup"><span data-stu-id="99f2c-143">Another important line is the call to `Async.RunSynchronously`.</span></span> <span data-ttu-id="99f2c-144">Bu, f# asynchronous hesaplamasını gerçekten yürütmek istiyorsanız aramanız gereken Async modülü başlangıç işlevlerinden biridir.</span><span class="sxs-lookup"><span data-stu-id="99f2c-144">This is one of the Async module starting functions that you'll need to call if you want to actually execute an F# asynchronous computation.</span></span>

<span data-ttu-id="99f2c-145">Bu `async` programlama C # / Visual Basic tarzı ile temel bir farktır.</span><span class="sxs-lookup"><span data-stu-id="99f2c-145">This is a fundamental difference with the C#/Visual Basic style of `async` programming.</span></span> <span data-ttu-id="99f2c-146">F#'da, asenkron hesaplamalar **Soğuk görevler**olarak düşünülebilir.</span><span class="sxs-lookup"><span data-stu-id="99f2c-146">In F#, asynchronous computations can be thought of as **Cold tasks**.</span></span> <span data-ttu-id="99f2c-147">Bunlar açıkça gerçekten yürütmek için başlatılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="99f2c-147">They must be explicitly started to actually execute.</span></span> <span data-ttu-id="99f2c-148">Bu, c# veya Visual Basic'tekinden çok daha kolay bir şekilde asynchronous çalışmasını birleştirmenize ve dizilemenize olanak sağladığından bazı avantajları vardır.</span><span class="sxs-lookup"><span data-stu-id="99f2c-148">This has some advantages, as it allows you to combine and sequence asynchronous work much more easily than in C# or Visual Basic.</span></span>

## <a name="combine-asynchronous-computations"></a><span data-ttu-id="99f2c-149">Eşzamanlı hesaplamaları birleştirme</span><span class="sxs-lookup"><span data-stu-id="99f2c-149">Combine asynchronous computations</span></span>

<span data-ttu-id="99f2c-150">Aşağıda, hesaplamaları birleştirerek bir öncekinin üzerine inşa edilen bir örnek verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="99f2c-150">Here is an example that builds upon the previous one by combining computations:</span></span>

```fsharp
open System
open System.IO

let printTotalFileBytes path =
    async {
        let! bytes = File.ReadAllBytesAsync(path) |> Async.AwaitTask
        let fileName = Path.GetFileName(path)
        printfn "File %s has %d bytes" fileName bytes.Length
    }

[<EntryPoint>]
let main argv =
    argv
    |> Array.map printTotalFileBytes
    |> Async.Parallel
    |> Async.Ignore
    |> Async.RunSynchronously

    0
```

<span data-ttu-id="99f2c-151">Gördüğünüz gibi, `main` işlev yapılan oldukça birkaç arama vardır.</span><span class="sxs-lookup"><span data-stu-id="99f2c-151">As you can see, the `main` function has quite a few more calls made.</span></span> <span data-ttu-id="99f2c-152">Kavramsal olarak, aşağıdakileri yapar:</span><span class="sxs-lookup"><span data-stu-id="99f2c-152">Conceptually, it does the following:</span></span>

1. <span data-ttu-id="99f2c-153">Komut satırı bağımsız değişkenlerini ' `Async<unit>` `Array.map`ile hesaplamalara dönüştürün</span><span class="sxs-lookup"><span data-stu-id="99f2c-153">Transform the command-line arguments into `Async<unit>` computations with `Array.map`.</span></span>
2. <span data-ttu-id="99f2c-154">`printTotalFileBytes` Bir zamanlama `Async<'T[]>` ve çalışırken paralel olarak hesaplamaları çalıştırAn oluşturun.</span><span class="sxs-lookup"><span data-stu-id="99f2c-154">Create an `Async<'T[]>` that schedules and runs the `printTotalFileBytes` computations in parallel when it runs.</span></span>
3. <span data-ttu-id="99f2c-155">Paralel `Async<unit>` hesaplamayı çalıştıracak ve sonucunu yoksayacak bir oluştur.</span><span class="sxs-lookup"><span data-stu-id="99f2c-155">Create an `Async<unit>` that will run the parallel computation and ignore its result.</span></span>
4. <span data-ttu-id="99f2c-156">Son hesaplamayı açıkça çalıştırın `Async.RunSynchronously` ve tamamlanana kadar engelleyin.</span><span class="sxs-lookup"><span data-stu-id="99f2c-156">Explicitly run the last computation with `Async.RunSynchronously` and block until it is completes.</span></span>

<span data-ttu-id="99f2c-157">Bu program çalıştığında, `printTotalFileBytes` her komut satırı bağımsız değişkeni için paralel olarak çalışır.</span><span class="sxs-lookup"><span data-stu-id="99f2c-157">When this program runs, `printTotalFileBytes` runs in parallel for each command-line argument.</span></span> <span data-ttu-id="99f2c-158">Eşzamanlı hesaplamalar program akışından bağımsız olarak yürütüldeğinden, bilgilerini yazdırDıkları ve yürütmeyi bitirdikleri bir sıra yoktur.</span><span class="sxs-lookup"><span data-stu-id="99f2c-158">Because asynchronous computations execute independently of program flow, there is no order in which they print their information and finish executing.</span></span> <span data-ttu-id="99f2c-159">Hesaplamalar paralel olarak zamanlanır, ancak bunların yürütme sırası garanti edilmez.</span><span class="sxs-lookup"><span data-stu-id="99f2c-159">The computations will be scheduled in parallel, but their order of execution is not guaranteed.</span></span>

## <a name="sequence-asynchronous-computations"></a><span data-ttu-id="99f2c-160">Sıralı asenkron hesaplamalar</span><span class="sxs-lookup"><span data-stu-id="99f2c-160">Sequence asynchronous computations</span></span>

<span data-ttu-id="99f2c-161">Zaten `Async<'T>` çalışan bir görev yerine çalışmanın bir belirtimi olduğundan, daha karmaşık dönüşümleri kolayca gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="99f2c-161">Because `Async<'T>` is a specification of work rather than an already-running task, you can perform more intricate transformations easily.</span></span> <span data-ttu-id="99f2c-162">Aşağıda, bir dizi Async hesaplamasını sıralayan bir örnek ve böylece birbiri ardına çalıştırışlar.</span><span class="sxs-lookup"><span data-stu-id="99f2c-162">Here is an example that sequences a set of Async computations so they execute one after another.</span></span>

```fsharp
let printTotalFileBytes path =
    async {
        let! bytes = File.ReadAllBytesAsync(path) |> Async.AwaitTask
        let fileName = Path.GetFileName(path)
        printfn "File %s has %d bytes" fileName bytes.Length
    }

[<EntryPoint>]
let main argv =
    argv
    |> Array.map printTotalFileBytes
    |> Async.Sequential
    |> Async.Ignore
    |> Async.RunSynchronously
    |> ignore
```

<span data-ttu-id="99f2c-163">Bu, `printTotalFileBytes` bunları paralel olarak planlamak `argv` yerine öğelerin sırasına göre yürütülmesi için zamanlayacaktır.</span><span class="sxs-lookup"><span data-stu-id="99f2c-163">This will schedule `printTotalFileBytes` to execute in the order of the elements of `argv` rather than scheduling them in parallel.</span></span> <span data-ttu-id="99f2c-164">Sonraki öğe son hesaplama yürütme tamamlanana kadar zamanlanmadığından, hesaplamalar yürütmede çakışmayacak şekilde sıralanır.</span><span class="sxs-lookup"><span data-stu-id="99f2c-164">Because the next item will not be scheduled until after the last computation has finished executing, the computations are sequenced such that there is no overlap in their execution.</span></span>

## <a name="important-async-module-functions"></a><span data-ttu-id="99f2c-165">Önemli Async modülü fonksiyonları</span><span class="sxs-lookup"><span data-stu-id="99f2c-165">Important Async module functions</span></span>

<span data-ttu-id="99f2c-166">F# kodu yazdığınızda genellikle sizin için hesaplamaların zamanlamasını işleyen bir çerçeveyle etkileşime girebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="99f2c-166">When you write async code in F# you'll usually interact with a framework that handles scheduling of computations for you.</span></span> <span data-ttu-id="99f2c-167">Ancak, bu her zaman böyle değildir, bu nedenle asynchronous çalışma zamanlamak için çeşitli başlangıç işlevleri öğrenmek iyidir.</span><span class="sxs-lookup"><span data-stu-id="99f2c-167">However, this is not always the case, so it is good to learn the various starting functions to schedule asynchronous work.</span></span>

<span data-ttu-id="99f2c-168">F# asynchronous hesaplamaları, zaten yürütülmakta olan çalışmanın bir gösterimi yerine çalışmanın bir _belirtimi_ olduğundan, açıkça bir başlangıç işlevi ile başlatılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="99f2c-168">Because F# asynchronous computations are a _specification_ of work rather than a representation of work that is already executing, they must be explicitly started with a starting function.</span></span> <span data-ttu-id="99f2c-169">Farklı bağlamlarda yararlı olan birçok [Async başlangıç işlevi](https://msdn.microsoft.com/library/ee370232.aspx) vardır.</span><span class="sxs-lookup"><span data-stu-id="99f2c-169">There are many [Async starting functions](https://msdn.microsoft.com/library/ee370232.aspx) that are helpful in different contexts.</span></span> <span data-ttu-id="99f2c-170">Aşağıdaki bölümde daha yaygın başlangıç işlevlerinden bazıları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="99f2c-170">The following section describes some of the more common starting functions.</span></span>

### <a name="asyncstartchild"></a><span data-ttu-id="99f2c-171">Async.StartChild</span><span class="sxs-lookup"><span data-stu-id="99f2c-171">Async.StartChild</span></span>

<span data-ttu-id="99f2c-172">Bir eşyoknom hesaplaması içinde bir alt hesaplama başlatır.</span><span class="sxs-lookup"><span data-stu-id="99f2c-172">Starts a child computation within an asynchronous computation.</span></span> <span data-ttu-id="99f2c-173">Bu, birden çok eşzamanlı hesaplamanın aynı anda yürütülmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="99f2c-173">This allows multiple asynchronous computations to be executed concurrently.</span></span> <span data-ttu-id="99f2c-174">Alt hesaplama, üst hesaplamaile bir iptal belirteci paylaşır.</span><span class="sxs-lookup"><span data-stu-id="99f2c-174">The child computation shares a cancellation token with the parent computation.</span></span> <span data-ttu-id="99f2c-175">Üst hesaplama iptal edilirse, alt hesaplama da iptal edilir.</span><span class="sxs-lookup"><span data-stu-id="99f2c-175">If the parent computation is canceled, the child computation is also canceled.</span></span>

<span data-ttu-id="99f2c-176">İmza:</span><span class="sxs-lookup"><span data-stu-id="99f2c-176">Signature:</span></span>

```fsharp
computation: Async<'T> * timeout: ?int -> Async<Async<'T>>
```

<span data-ttu-id="99f2c-177">Ne zaman kullanılır:</span><span class="sxs-lookup"><span data-stu-id="99f2c-177">When to use:</span></span>

- <span data-ttu-id="99f2c-178">Birden çok eşzamanlı hesaplamayı aynı anda değil, aynı anda yürütmek istediğinizde, ancak bunları paralel olarak zamanlatmayın.</span><span class="sxs-lookup"><span data-stu-id="99f2c-178">When you want to execute multiple asynchronous computations concurrently rather than one at a time, but not have them scheduled in parallel.</span></span>
- <span data-ttu-id="99f2c-179">Bir çocuğun hesaplamasının ömrünü bir ebeveyn hesaplamasına bağlamak istediğinizde.</span><span class="sxs-lookup"><span data-stu-id="99f2c-179">When you wish to tie the lifetime of a child computation to that of a parent computation.</span></span>

<span data-ttu-id="99f2c-180">Dikkat et:</span><span class="sxs-lookup"><span data-stu-id="99f2c-180">What to watch out for:</span></span>

- <span data-ttu-id="99f2c-181">Birden çok hesaplamayla `Async.StartChild` başlatıcı, bunları paralel olarak zamanlamayla aynı şey değildir.</span><span class="sxs-lookup"><span data-stu-id="99f2c-181">Starting multiple computations with `Async.StartChild` isn't the same as scheduling them in parallel.</span></span> <span data-ttu-id="99f2c-182">Hesaplamaları paralel olarak zamanlamak istiyorsanız, `Async.Parallel`'yi kullanın.</span><span class="sxs-lookup"><span data-stu-id="99f2c-182">If you wish to schedule computations in parallel, use `Async.Parallel`.</span></span>
- <span data-ttu-id="99f2c-183">Bir üst hesaplamanın iptaledilmesi, başlattığı tüm alt hesaplamaların iptalini tetikler.</span><span class="sxs-lookup"><span data-stu-id="99f2c-183">Canceling a parent computation will trigger cancellation of all child computations it started.</span></span>

### <a name="asyncstartimmediate"></a><span data-ttu-id="99f2c-184">Async.StartHemen</span><span class="sxs-lookup"><span data-stu-id="99f2c-184">Async.StartImmediate</span></span>

<span data-ttu-id="99f2c-185">Geçerli işletim sistemi iş parçacığıüzerinde hemen başlayarak, bir eşzamanlı hesaplama çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="99f2c-185">Runs an asynchronous computation, starting immediately on the current operating system thread.</span></span> <span data-ttu-id="99f2c-186">Hesaplama sırasında arama iş parçacığı üzerinde bir şey güncelleştirmeniz gerekiyorsa bu yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="99f2c-186">This is helpful if you need to update something on the calling thread during the computation.</span></span> <span data-ttu-id="99f2c-187">Örneğin, bir eşzamanlı hesaplama nın bir Kullanıcı Arabirimi güncelleştirmesi gerekiyorsa (ilerleme `Async.StartImmediate` çubuğunun güncelleştirilmesi gibi), daha sonra kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="99f2c-187">For example, if an asynchronous computation must update a UI (such as updating a progress bar), then `Async.StartImmediate` should be used.</span></span>

<span data-ttu-id="99f2c-188">İmza:</span><span class="sxs-lookup"><span data-stu-id="99f2c-188">Signature:</span></span>

```fsharp
computation: Async<unit> - cancellationToken: ?CancellationToken -> unit
```

<span data-ttu-id="99f2c-189">Ne zaman kullanılır:</span><span class="sxs-lookup"><span data-stu-id="99f2c-189">When to use:</span></span>

- <span data-ttu-id="99f2c-190">Bir eşzamanlı hesaplamanın ortasındaki arama iş parçacığında bir şeyi güncelleştirmeniz gerektiğinde.</span><span class="sxs-lookup"><span data-stu-id="99f2c-190">When you need to update something on the calling thread in the middle of an asynchronous computation.</span></span>

<span data-ttu-id="99f2c-191">Dikkat et:</span><span class="sxs-lookup"><span data-stu-id="99f2c-191">What to watch out for:</span></span>

- <span data-ttu-id="99f2c-192">Asynchronous hesaplamasındaki kod, zamanlanan iş parçacığı üzerinde çalışacaktır.</span><span class="sxs-lookup"><span data-stu-id="99f2c-192">Code in the asynchronous computation will run on whatever thread one happens to be scheduled on.</span></span> <span data-ttu-id="99f2c-193">Bu iş parçacığı bir şekilde bir ui iş parçacığı gibi hassas ise bu sorunlu olabilir.</span><span class="sxs-lookup"><span data-stu-id="99f2c-193">This can be problematic if that thread is in some way sensitive, such as a UI thread.</span></span> <span data-ttu-id="99f2c-194">Bu gibi `Async.StartImmediate` durumlarda, kullanmak için büyük olasılıkla uygun değildir.</span><span class="sxs-lookup"><span data-stu-id="99f2c-194">In such cases, `Async.StartImmediate` is likely inappropriate to use.</span></span>

### <a name="asyncstartastask"></a><span data-ttu-id="99f2c-195">Async.StartAsTask</span><span class="sxs-lookup"><span data-stu-id="99f2c-195">Async.StartAsTask</span></span>

<span data-ttu-id="99f2c-196">İş parçacığı havuzunda bir hesaplama yürütür.</span><span class="sxs-lookup"><span data-stu-id="99f2c-196">Executes a computation in the thread pool.</span></span> <span data-ttu-id="99f2c-197">Hesaplama <xref:System.Threading.Tasks.Task%601> sona erdiğinde (sonucu üreten, özel durum ortaya koyan veya iptal edilen) ilgili durumda tamamlanacak bir belge döndürür.</span><span class="sxs-lookup"><span data-stu-id="99f2c-197">Returns a <xref:System.Threading.Tasks.Task%601> that will be completed on the corresponding state once the computation terminates (produces the result, throws exception, or gets canceled).</span></span> <span data-ttu-id="99f2c-198">İptal belirteci sağlanmazsa, varsayılan iptal belirteci kullanılır.</span><span class="sxs-lookup"><span data-stu-id="99f2c-198">If no cancellation token is provided, then the default cancellation token is used.</span></span>

<span data-ttu-id="99f2c-199">İmza:</span><span class="sxs-lookup"><span data-stu-id="99f2c-199">Signature:</span></span>

```fsharp
computation: Async<'T> - taskCreationOptions: ?TaskCreationOptions - cancellationToken: ?CancellationToken -> Task<'T>
```

<span data-ttu-id="99f2c-200">Ne zaman kullanılır:</span><span class="sxs-lookup"><span data-stu-id="99f2c-200">When to use:</span></span>

- <span data-ttu-id="99f2c-201">A'nın <xref:System.Threading.Tasks.Task%601> eşzamanlı bir hesaplamanın sonucunu temsil etmesini bekleyen bir .NET API'sini aramanız gerektiğinde.</span><span class="sxs-lookup"><span data-stu-id="99f2c-201">When you need to call into a .NET API that expects a <xref:System.Threading.Tasks.Task%601> to represent the result of an asynchronous computation.</span></span>

<span data-ttu-id="99f2c-202">Dikkat et:</span><span class="sxs-lookup"><span data-stu-id="99f2c-202">What to watch out for:</span></span>

- <span data-ttu-id="99f2c-203">Bu çağrı, sık `Task` sık kullanılırsa ek yükü artırabilir ek bir nesne tahsis edecektir.</span><span class="sxs-lookup"><span data-stu-id="99f2c-203">This call will allocate an additional `Task` object, which can increase overhead if it is used often.</span></span>

### <a name="asyncparallel"></a><span data-ttu-id="99f2c-204">Async.Parallel</span><span class="sxs-lookup"><span data-stu-id="99f2c-204">Async.Parallel</span></span>

<span data-ttu-id="99f2c-205">Paralel olarak yürütülecek bir eşzamanlı hesaplama dizisi zamanlar.</span><span class="sxs-lookup"><span data-stu-id="99f2c-205">Schedules a sequence of asynchronous computations to be executed in parallel.</span></span> <span data-ttu-id="99f2c-206">Paralellik `maxDegreesOfParallelism` derecesi, parametre belirtilmek suretiyle isteğe bağlı olarak ayarlanabilir/daraltılabilir.</span><span class="sxs-lookup"><span data-stu-id="99f2c-206">The degree of parallelism can be optionally tuned/throttled by specifying the `maxDegreesOfParallelism` parameter.</span></span>

<span data-ttu-id="99f2c-207">İmza:</span><span class="sxs-lookup"><span data-stu-id="99f2c-207">Signature:</span></span>

```fsharp
computations: seq<Async<'T>> - ?maxDegreesOfParallelism: int -> Async<'T[]>
```

<span data-ttu-id="99f2c-208">Ne zaman kullanılır:</span><span class="sxs-lookup"><span data-stu-id="99f2c-208">When to use it:</span></span>

- <span data-ttu-id="99f2c-209">Aynı anda bir dizi hesaplama çalıştırmanız gerekiyorsa ve bunların yürütme sırasına güvenmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="99f2c-209">If you need to run a set of computations at the same time and have no reliance on their order of execution.</span></span>
- <span data-ttu-id="99f2c-210">Hepsi tamamlanana kadar paralel olarak zamanlanan hesaplamalardan sonuç gerektirmezseniz.</span><span class="sxs-lookup"><span data-stu-id="99f2c-210">If you don't require results from computations scheduled in parallel until they have all completed.</span></span>

<span data-ttu-id="99f2c-211">Dikkat et:</span><span class="sxs-lookup"><span data-stu-id="99f2c-211">What to watch out for:</span></span>

- <span data-ttu-id="99f2c-212">Tüm hesaplamalar tamamlandıktan sonra yalnızca ortaya çıkan değerler dizisine erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="99f2c-212">You can only access the resulting array of values once all computations have finished.</span></span>
- <span data-ttu-id="99f2c-213">Hesaplamalar ancak zamanlanan alma sonunda çalıştırılacaktır.</span><span class="sxs-lookup"><span data-stu-id="99f2c-213">Computations will be run however they end up getting scheduled.</span></span> <span data-ttu-id="99f2c-214">Bu, onların idam sıralarına güvenemeyeceğiniz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="99f2c-214">This means you cannot rely on their order of their execution.</span></span>

### <a name="asyncsequential"></a><span data-ttu-id="99f2c-215">Async.Sequential</span><span class="sxs-lookup"><span data-stu-id="99f2c-215">Async.Sequential</span></span>

<span data-ttu-id="99f2c-216">Geçirilme sırasına göre yürütülecek bir eşzamanlı hesaplama dizisi zamanlar.</span><span class="sxs-lookup"><span data-stu-id="99f2c-216">Schedules a sequence of asynchronous computations to be executed in the order that they are passed.</span></span> <span data-ttu-id="99f2c-217">İlk hesaplama yürütülür, sonra sonraki, ve benzeri.</span><span class="sxs-lookup"><span data-stu-id="99f2c-217">The first computation will be executed, then the next, and so on.</span></span> <span data-ttu-id="99f2c-218">Hiçbir hesaplama paralel olarak yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="99f2c-218">No computations will be executed in parallel.</span></span>

<span data-ttu-id="99f2c-219">İmza:</span><span class="sxs-lookup"><span data-stu-id="99f2c-219">Signature:</span></span>

```fsharp
computations: seq<Async<'T>> -> Async<'T[]>
```

<span data-ttu-id="99f2c-220">Ne zaman kullanılır:</span><span class="sxs-lookup"><span data-stu-id="99f2c-220">When to use it:</span></span>

- <span data-ttu-id="99f2c-221">Sırayla birden çok hesaplama yürütmeniz gerekiyorsa.</span><span class="sxs-lookup"><span data-stu-id="99f2c-221">If you need to execute multiple computations in order.</span></span>

<span data-ttu-id="99f2c-222">Dikkat et:</span><span class="sxs-lookup"><span data-stu-id="99f2c-222">What to watch out for:</span></span>

- <span data-ttu-id="99f2c-223">Tüm hesaplamalar tamamlandıktan sonra yalnızca ortaya çıkan değerler dizisine erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="99f2c-223">You can only access the resulting array of values once all computations have finished.</span></span>
- <span data-ttu-id="99f2c-224">Hesaplamalar, bu işleve geçirilme sırasına göre çalıştırılır, bu da sonuçlar döndürülmeden önce daha fazla zamanın geçeceği anlamına gelebilir.</span><span class="sxs-lookup"><span data-stu-id="99f2c-224">Computations will be run in the order that they are passed to this function, which can mean that more time will elapse before the results are returned.</span></span>

### <a name="asyncawaittask"></a><span data-ttu-id="99f2c-225">Async.AwaitTask</span><span class="sxs-lookup"><span data-stu-id="99f2c-225">Async.AwaitTask</span></span>

<span data-ttu-id="99f2c-226">Verilenin <xref:System.Threading.Tasks.Task%601> tamamlanmasını bekleyen bir eşzamanlı hesaplama verir ve sonucunu`Async<'T>`</span><span class="sxs-lookup"><span data-stu-id="99f2c-226">Returns an asynchronous computation that waits for the given <xref:System.Threading.Tasks.Task%601> to complete and returns its result as an `Async<'T>`</span></span>

<span data-ttu-id="99f2c-227">İmza:</span><span class="sxs-lookup"><span data-stu-id="99f2c-227">Signature:</span></span>

```fsharp
task: Task<'T>  -> Async<'T>
```

<span data-ttu-id="99f2c-228">Ne zaman kullanılır:</span><span class="sxs-lookup"><span data-stu-id="99f2c-228">When to use:</span></span>

- <span data-ttu-id="99f2c-229">Bir F# asynchronous hesaplama içinde <xref:System.Threading.Tasks.Task%601> bir .NET API tüketirken.</span><span class="sxs-lookup"><span data-stu-id="99f2c-229">When you are consuming a .NET API that returns a <xref:System.Threading.Tasks.Task%601> within an F# asynchronous computation.</span></span>

<span data-ttu-id="99f2c-230">Dikkat et:</span><span class="sxs-lookup"><span data-stu-id="99f2c-230">What to watch out for:</span></span>

- <span data-ttu-id="99f2c-231">Özel durumlar Görev <xref:System.AggregateException> Paralel Kitaplığı kuralını izleyerek sarılır ve bu, F# async'in genellikle özel durumları nasıl yüzeye çıkardığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="99f2c-231">Exceptions are wrapped in <xref:System.AggregateException> following the convention of the Task Parallel Library, and this is different from how F# async generally surfaces exceptions.</span></span>

### <a name="asynccatch"></a><span data-ttu-id="99f2c-232">Async.Catch</span><span class="sxs-lookup"><span data-stu-id="99f2c-232">Async.Catch</span></span>

<span data-ttu-id="99f2c-233">Belirli `Async<'T>`bir , döndüren bir `Async<Choice<'T, exn>>`' yi yürüten bir eşzamanlı hesaplama oluşturur.</span><span class="sxs-lookup"><span data-stu-id="99f2c-233">Creates an asynchronous computation that executes a given `Async<'T>`, returning an `Async<Choice<'T, exn>>`.</span></span> <span data-ttu-id="99f2c-234">Verilen `Async<'T>` başarıyla tamamlanırsa, a `Choice1Of2` elde edilen değerle döndürülür.</span><span class="sxs-lookup"><span data-stu-id="99f2c-234">If the given `Async<'T>` completes successfully, then a `Choice1Of2` is returned with the resultant value.</span></span> <span data-ttu-id="99f2c-235">Bir özel durum tamamlanmadan önce atılırsa, a `Choice2of2` yükseltilen özel durum la döndürülür.</span><span class="sxs-lookup"><span data-stu-id="99f2c-235">If an exception is thrown before it completes, then a `Choice2of2` is returned with the raised exception.</span></span> <span data-ttu-id="99f2c-236">Kendisi birçok hesaplamadan oluşan bir eşzamanlı hesaplamada kullanılırsa ve bu hesaplamalardan biri özel bir durum oluşturursa, kapsayan hesaplama tamamen durdurulur.</span><span class="sxs-lookup"><span data-stu-id="99f2c-236">If it is used on an asynchronous computation that is itself composed of many computations, and one of those computations throws an exception, the encompassing computation will be stopped entirely.</span></span>

<span data-ttu-id="99f2c-237">İmza:</span><span class="sxs-lookup"><span data-stu-id="99f2c-237">Signature:</span></span>

```fsharp
computation: Async<'T> -> Async<Choice<'T, exn>>
```

<span data-ttu-id="99f2c-238">Ne zaman kullanılır:</span><span class="sxs-lookup"><span data-stu-id="99f2c-238">When to use:</span></span>

- <span data-ttu-id="99f2c-239">Bir özel durumla başarısız olabilecek eşzamanlı çalışma gerçekleştirirken ve bu özel durumu arayanda işlemek istediğinizde.</span><span class="sxs-lookup"><span data-stu-id="99f2c-239">When you are performing asynchronous work that may fail with an exception and you want to handle that exception in the caller.</span></span>

<span data-ttu-id="99f2c-240">Dikkat et:</span><span class="sxs-lookup"><span data-stu-id="99f2c-240">What to watch out for:</span></span>

- <span data-ttu-id="99f2c-241">Birleştirilmiş veya sıralanmış asynchronöz hesaplamalar kullanılırken, "dahili" hesaplamalarından biri özel durum oluşturursa, kapsamlı hesaplama tamamen durdurulacaktır.</span><span class="sxs-lookup"><span data-stu-id="99f2c-241">When using combined or sequenced asynchronous computations, the encompassing computation will fully stop if one of its "internal" computations throws an exception.</span></span>

### <a name="asyncignore"></a><span data-ttu-id="99f2c-242">Async.Ignore</span><span class="sxs-lookup"><span data-stu-id="99f2c-242">Async.Ignore</span></span>

<span data-ttu-id="99f2c-243">Verilen hesaplamayı çalıştıran ve sonucunu yok sayan bir eşzamanlı hesaplama oluşturur.</span><span class="sxs-lookup"><span data-stu-id="99f2c-243">Creates an asynchronous computation that runs the given computation and ignores its result.</span></span>

<span data-ttu-id="99f2c-244">İmza:</span><span class="sxs-lookup"><span data-stu-id="99f2c-244">Signature:</span></span>

```fsharp
computation: Async<'T> -> Async<unit>
```

<span data-ttu-id="99f2c-245">Ne zaman kullanılır:</span><span class="sxs-lookup"><span data-stu-id="99f2c-245">When to use:</span></span>

- <span data-ttu-id="99f2c-246">Sonucu gerekli olmayan bir eşzamanlı hesaplamanız olduğunda.</span><span class="sxs-lookup"><span data-stu-id="99f2c-246">When you have an asynchronous computation whose result is not needed.</span></span> <span data-ttu-id="99f2c-247">Bu, eşzamanlı olmayan `ignore` kod koduna benzer.</span><span class="sxs-lookup"><span data-stu-id="99f2c-247">This is analogous to the `ignore` code for non-asynchronous code.</span></span>

<span data-ttu-id="99f2c-248">Dikkat et:</span><span class="sxs-lookup"><span data-stu-id="99f2c-248">What to watch out for:</span></span>

- <span data-ttu-id="99f2c-249">Kullanmak `Async.Start` istediğiniz için bunu kullanmanız gerekiyorsa veya gerektiren `Async<unit>`başka bir işlev varsa, sonucu atmanın tamam olup olmadığını göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="99f2c-249">If you must use this because you wish to use `Async.Start` or another function that requires `Async<unit>`, consider if discarding the result is okay to do.</span></span> <span data-ttu-id="99f2c-250">Bir tür imzasını sığdırmak için sonuçları atmak genellikle yapılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="99f2c-250">Discarding results just to fit a type signature should not generally be done.</span></span>

### <a name="asyncrunsynchronously"></a><span data-ttu-id="99f2c-251">Async.RunSynchronously</span><span class="sxs-lookup"><span data-stu-id="99f2c-251">Async.RunSynchronously</span></span>

<span data-ttu-id="99f2c-252">Asynchronous hesaplaması çalıştırıyor ve arama iş parçacığında sonucunu bekliyor.</span><span class="sxs-lookup"><span data-stu-id="99f2c-252">Runs an asynchronous computation and awaits its result on the calling thread.</span></span> <span data-ttu-id="99f2c-253">Bu arama engelliyor.</span><span class="sxs-lookup"><span data-stu-id="99f2c-253">This call is blocking.</span></span>

<span data-ttu-id="99f2c-254">İmza:</span><span class="sxs-lookup"><span data-stu-id="99f2c-254">Signature:</span></span>

```fsharp
computation: Async<'T> - timeout: ?int - cancellationToken: ?CancellationToken -> 'T
```

<span data-ttu-id="99f2c-255">Ne zaman kullanılır:</span><span class="sxs-lookup"><span data-stu-id="99f2c-255">When to use it:</span></span>

- <span data-ttu-id="99f2c-256">İhtiyacınız varsa, yürütülebilir bir giriş noktasında bir uygulamada yalnızca bir kez kullanın.</span><span class="sxs-lookup"><span data-stu-id="99f2c-256">If you need it, use it only once in an application - at the entry point for an executable.</span></span>
- <span data-ttu-id="99f2c-257">Performansı önemsemiyorsanız ve aynı anda bir dizi diğer eşzamanlı işlemi yürütmek istediğinizde.</span><span class="sxs-lookup"><span data-stu-id="99f2c-257">When you don't care about performance and want to execute a set of other asynchronous operations at once.</span></span>

<span data-ttu-id="99f2c-258">Dikkat et:</span><span class="sxs-lookup"><span data-stu-id="99f2c-258">What to watch out for:</span></span>

- <span data-ttu-id="99f2c-259">Yürütme `Async.RunSynchronously` tamamlanana kadar arama iş parçacığı engeller.</span><span class="sxs-lookup"><span data-stu-id="99f2c-259">Calling `Async.RunSynchronously` blocks the calling thread until the execution completes.</span></span>

### <a name="asyncstart"></a><span data-ttu-id="99f2c-260">Async.Start</span><span class="sxs-lookup"><span data-stu-id="99f2c-260">Async.Start</span></span>

<span data-ttu-id="99f2c-261">İş parçacığı havuzunda dönen bir eşzamanlı hesaplama `unit`başlatır.</span><span class="sxs-lookup"><span data-stu-id="99f2c-261">Starts an asynchronous computation in the thread pool that returns `unit`.</span></span> <span data-ttu-id="99f2c-262">Sonucunu beklemez.</span><span class="sxs-lookup"><span data-stu-id="99f2c-262">Doesn't wait for its result.</span></span> <span data-ttu-id="99f2c-263">İç içe başlayan `Async.Start` hesaplamalar, onları çağıran ana hesaplamadan tamamen bağımsız olarak başlatılır.</span><span class="sxs-lookup"><span data-stu-id="99f2c-263">Nested computations started with `Async.Start` are started completely independently of the parent computation that called them.</span></span> <span data-ttu-id="99f2c-264">Onların ömrü herhangi bir üst hesaplama bağlı değildir.</span><span class="sxs-lookup"><span data-stu-id="99f2c-264">Their lifetime is not tied to any parent computation.</span></span> <span data-ttu-id="99f2c-265">Üst hesaplama iptal edilirse, alt hesaplamalar iptal edilir.</span><span class="sxs-lookup"><span data-stu-id="99f2c-265">If the parent computation is canceled, no child computations are cancelled.</span></span>

<span data-ttu-id="99f2c-266">İmza:</span><span class="sxs-lookup"><span data-stu-id="99f2c-266">Signature:</span></span>

```fsharp
computation: Async<unit> - cancellationToken: ?CancellationToken -> unit
```

<span data-ttu-id="99f2c-267">Yalnızca:</span><span class="sxs-lookup"><span data-stu-id="99f2c-267">Use only when:</span></span>

- <span data-ttu-id="99f2c-268">Sonuç vermeyen ve/veya bir sonuç alınmasını gerektiren bir eşzamanlı hesaplamanız var.</span><span class="sxs-lookup"><span data-stu-id="99f2c-268">You have an asynchronous computation that doesn't yield a result and/or require processing of one.</span></span>
- <span data-ttu-id="99f2c-269">Eşzamanlı hesaplamanın ne zaman tamamlaşacağını bilmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="99f2c-269">You don't need to know when an asynchronous computation completes.</span></span>
- <span data-ttu-id="99f2c-270">Asynchronous hesaplamanın hangi iş parçacığı üzerinde çalıştığı umurunda değil.</span><span class="sxs-lookup"><span data-stu-id="99f2c-270">You don't care which thread an asynchronous computation runs on.</span></span>
- <span data-ttu-id="99f2c-271">Görevden kaynaklanan özel durumları bilmeniz veya bildirmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="99f2c-271">You don't have any need to be aware of or report exceptions resulting from the task.</span></span>

<span data-ttu-id="99f2c-272">Dikkat et:</span><span class="sxs-lookup"><span data-stu-id="99f2c-272">What to watch out for:</span></span>

- <span data-ttu-id="99f2c-273">Başlatılan hesaplamalar tarafından `Async.Start` yükseltilen özel durumlar arayana yayılmaz.</span><span class="sxs-lookup"><span data-stu-id="99f2c-273">Exceptions raised by computations started with `Async.Start` aren't propagated to the caller.</span></span> <span data-ttu-id="99f2c-274">Arama yığını tamamen çözülecektir.</span><span class="sxs-lookup"><span data-stu-id="99f2c-274">The call stack will be completely unwound.</span></span>
- <span data-ttu-id="99f2c-275">Herhangi bir etkili çalışma `printfn`(arama `Async.Start` gibi) bir programın yürütülmesi nin ana iş parçacığı üzerinde gerçekleşmesine neden olmaz ile başladı.</span><span class="sxs-lookup"><span data-stu-id="99f2c-275">Any effectful work (such as calling `printfn`) started with `Async.Start` won't cause the effect to happen on the main thread of a program's execution.</span></span>

## <a name="interoperate-with-net"></a><span data-ttu-id="99f2c-276">.NET ile birlikte çalışma</span><span class="sxs-lookup"><span data-stu-id="99f2c-276">Interoperate with .NET</span></span>

<span data-ttu-id="99f2c-277">[Async/await](../../../standard/async.md)-style asynchronous programlama kullanan bir .NET kitaplığı veya C# kod tabanıyla çalışıyor olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="99f2c-277">You may be working with a .NET library or C# codebase that uses [async/await](../../../standard/async.md)-style asynchronous programming.</span></span> <span data-ttu-id="99f2c-278">C# ve .NET kitaplıklarının <xref:System.Threading.Tasks.Task%601> çoğunluğu <xref:System.Threading.Tasks.Task> çekirdek soyutlamaları yerine `Async<'T>`çekirdek soyutlamaları olarak kullandığından, bu iki eşsenkronizasyon yaklaşımı arasında bir sınırı geçmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="99f2c-278">Because C# and the majority of .NET libraries use the <xref:System.Threading.Tasks.Task%601> and <xref:System.Threading.Tasks.Task> types as their core abstractions rather than `Async<'T>`, you must cross a boundary between these two approaches to asynchrony.</span></span>

### <a name="how-to-work-with-net-async-and-taskt"></a><span data-ttu-id="99f2c-279">.NET async ve`Task<T>`</span><span class="sxs-lookup"><span data-stu-id="99f2c-279">How to work with .NET async and `Task<T>`</span></span>

<span data-ttu-id="99f2c-280">.NET async kitaplıkları ve kullanan <xref:System.Threading.Tasks.Task%601> kod tabanları (yani, iade değerlerine sahip async hesaplamaları) ile çalışmak basittir ve F# ile yerleşik desteği vardır.</span><span class="sxs-lookup"><span data-stu-id="99f2c-280">Working with .NET async libraries and codebases that use <xref:System.Threading.Tasks.Task%601> (that is, async computations that have return values) is straightforward and has built-in support with F#.</span></span>

<span data-ttu-id="99f2c-281">İşlevi `Async.AwaitTask` .NET asynchronous hesaplamasını beklemek için kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="99f2c-281">You can use the `Async.AwaitTask` function to await a .NET asynchronous computation:</span></span>

```fsharp
let getValueFromLibrary param =
    async {
        let! value = DotNetLibrary.GetValueAsync param |> Async.AwaitTask
        return value
    }
```

<span data-ttu-id="99f2c-282">İşlev, `Async.StartAsTask` bir .NET arayana eşzamanlı bir hesaplama geçirmek için kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="99f2c-282">You can use the `Async.StartAsTask` function to pass an asynchronous computation to a .NET caller:</span></span>

```fsharp
let computationForCaller param =
    async {
        let! result = getAsyncResult param
        return result
    } |> Async.StartAsTask
```

### <a name="how-to-work-with-net-async-and-task"></a><span data-ttu-id="99f2c-283">.NET async ve`Task`</span><span class="sxs-lookup"><span data-stu-id="99f2c-283">How to work with .NET async and `Task`</span></span>

<span data-ttu-id="99f2c-284">Kullanan <xref:System.Threading.Tasks.Task> API'lerle çalışmak için (yani bir değer döndürmeyen .NET async hesaplamaları), bir değeri `Async<'T>` dönüştürecek ek <xref:System.Threading.Tasks.Task>bir işlev eklemeniz gerekebilir:</span><span class="sxs-lookup"><span data-stu-id="99f2c-284">To work with APIs that use <xref:System.Threading.Tasks.Task> (that is, .NET async computations that do not return a value), you may need to add an additional function that will convert an `Async<'T>` to a <xref:System.Threading.Tasks.Task>:</span></span>

```fsharp
module Async =
    // Async<unit> -> Task
    let startTaskFromAsyncUnit (comp: Async<unit>) =
        Async.StartAsTask comp :> Task
```

<span data-ttu-id="99f2c-285">Zaten `Async.AwaitTask` bir girdi olarak <xref:System.Threading.Tasks.Task> kabul eden bir.</span><span class="sxs-lookup"><span data-stu-id="99f2c-285">There is already an `Async.AwaitTask` that accepts a <xref:System.Threading.Tasks.Task> as input.</span></span> <span data-ttu-id="99f2c-286">Bu ve daha önce `startTaskFromAsyncUnit` tanımlanmış işlevle, <xref:System.Threading.Tasks.Task> F# async hesaplamasından türleri başlatabilir ve bekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="99f2c-286">With this and the previously defined `startTaskFromAsyncUnit` function, you can start and await <xref:System.Threading.Tasks.Task> types from an F# async computation.</span></span>

## <a name="relationship-to-multi-threading"></a><span data-ttu-id="99f2c-287">Çoklu iş parçacığı ile ilişki</span><span class="sxs-lookup"><span data-stu-id="99f2c-287">Relationship to multi-threading</span></span>

<span data-ttu-id="99f2c-288">Bu makale boyunca iş parçacığı belirtilmiş olsa da, hatırlanması gereken iki önemli şey vardır:</span><span class="sxs-lookup"><span data-stu-id="99f2c-288">Although threading is mentioned throughout this article, there are two important things to remember:</span></span>

1. <span data-ttu-id="99f2c-289">Geçerli iş parçacığı üzerinde açıkça başlıkça, bir eşzamanlı hesaplama ile iş parçacığı arasında bir benzerlik yoktur.</span><span class="sxs-lookup"><span data-stu-id="99f2c-289">There is no affinity between an asynchronous computation and a thread, unless explicitly started on the current thread.</span></span>
1. <span data-ttu-id="99f2c-290">F# asynchronous programlama çoklu iş parçacığı için bir soyutlama değildir.</span><span class="sxs-lookup"><span data-stu-id="99f2c-290">Asynchronous programming in F# is not an abstraction for multi-threading.</span></span>

<span data-ttu-id="99f2c-291">Örneğin, bir hesaplama aslında işin doğasına bağlı olarak, arayan kişinin iş parçacığı üzerinde çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="99f2c-291">For example, a computation may actually run on its caller's thread, depending on the nature of the work.</span></span> <span data-ttu-id="99f2c-292">Bir hesaplama da iş parçacıkları arasında "atlama" olabilir, "bekleme" dönemleri arasında yararlı işler yapmak için zaman küçük bir miktar için ödünç (örneğin bir ağ araması transit olduğunda gibi).</span><span class="sxs-lookup"><span data-stu-id="99f2c-292">A computation could also "jump" between threads, borrowing them for a small amount of time to do useful work in between periods of "waiting" (such as when a network call is in transit).</span></span>

<span data-ttu-id="99f2c-293">F# geçerli iş parçacığı (veya açıkça geçerli iş parçacığı üzerinde değil) bir eşzamanlı hesaplama başlatmak için bazı yetenekler sağlar, asynchrony genellikle belirli bir iş parçacığı stratejisi ile ilişkili değildir.</span><span class="sxs-lookup"><span data-stu-id="99f2c-293">Although F# provides some abilities to start an asynchronous computation on the current thread (or explicitly not on the current thread), asynchrony generally is not associated with a particular threading strategy.</span></span>

## <a name="see-also"></a><span data-ttu-id="99f2c-294">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="99f2c-294">See also</span></span>

- [<span data-ttu-id="99f2c-295">F# Asynchronous Programlama Modeli</span><span class="sxs-lookup"><span data-stu-id="99f2c-295">The F# Asynchronous Programming Model</span></span>](https://www.microsoft.com/research/publication/the-f-asynchronous-programming-model)
- [<span data-ttu-id="99f2c-296">Jet.com'un F# Async Rehberi</span><span class="sxs-lookup"><span data-stu-id="99f2c-296">Jet.com's F# Async Guide</span></span>](https://medium.com/jettech/f-async-guide-eb3c8a2d180a)
- [<span data-ttu-id="99f2c-297">Eğlence ve kar için F# Asynchronous Programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="99f2c-297">F# for fun and profit's Asynchronous Programming guide</span></span>](https://fsharpforfunandprofit.com/posts/concurrency-async-and-parallel/)
- [<span data-ttu-id="99f2c-298">C# ve F#'da Async: C'de asynchronous gotchas #</span><span class="sxs-lookup"><span data-stu-id="99f2c-298">Async in C# and F#: Asynchronous gotchas in C#</span></span>](http://tomasp.net/blog/csharp-async-gotchas.aspx/)
