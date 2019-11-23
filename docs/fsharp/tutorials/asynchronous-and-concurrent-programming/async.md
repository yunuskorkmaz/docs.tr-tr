---
title: İçinde zaman uyumsuz programlamaF#
description: Temel fonksiyonel F# programlama kavramlarından türetilmiş bir dil düzeyi programlama modeline göre zaman uyumsuzluğu için nasıl temiz destek sağladığını öğrenin.
ms.date: 12/17/2018
ms.openlocfilehash: 1ede4a5c1e26df271ac94f9b2c216ac84fb38f59
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395786"
---
# <a name="async-programming-in-f"></a><span data-ttu-id="412c5-103">F\# 'da zaman uyumsuz programlama</span><span class="sxs-lookup"><span data-stu-id="412c5-103">Async programming in F\#</span></span>

<span data-ttu-id="412c5-104">Zaman uyumsuz programlama, farklı nedenlerle modern uygulamalar için gerekli olan bir mekanizmadır.</span><span class="sxs-lookup"><span data-stu-id="412c5-104">Asynchronous programming is a mechanism that is essential to modern applications for diverse reasons.</span></span> <span data-ttu-id="412c5-105">Çoğu geliştiricinin karşılaştığı iki birincil kullanım durumu vardır:</span><span class="sxs-lookup"><span data-stu-id="412c5-105">There are two primary use cases that most developers will encounter:</span></span>

- <span data-ttu-id="412c5-106">Çok sayıda eş zamanlı gelen isteğe hizmet veren bir sunucu işlemi sunma, ancak bu işleme ait sistemlerden veya hizmetlerden gelen bekleme girişlerini işlerken istek sırasında bulunan sistem kaynaklarını en aza indirme</span><span class="sxs-lookup"><span data-stu-id="412c5-106">Presenting a server process that can service a significant number of concurrent incoming requests, while minimizing the system resources occupied while request processing awaits inputs from systems or services external to that process</span></span>
- <span data-ttu-id="412c5-107">Eşzamanlı bir kullanıcı arabirimini veya ana iş parçacığını, arka planda çalışmaya devam ederken koruma</span><span class="sxs-lookup"><span data-stu-id="412c5-107">Maintaining a responsive UI or main thread while concurrently progressing background work</span></span>

<span data-ttu-id="412c5-108">Arka plan çalışması genellikle birden çok iş parçacığının kullanımını içerse de, zaman uyumsuzluğu ve çoklu iş parçacığı kavramlarını ayrı ayrı ele almanız önemlidir.</span><span class="sxs-lookup"><span data-stu-id="412c5-108">Although background work often does involve the utilization of multiple threads, it's important to consider the concepts of asynchrony and multi-threading separately.</span></span> <span data-ttu-id="412c5-109">Aslında bunlar ayrı kaygılardır ve diğeri diğerini göstermez.</span><span class="sxs-lookup"><span data-stu-id="412c5-109">In fact, they are separate concerns, and one does not imply the other.</span></span> <span data-ttu-id="412c5-110">Bu makalede aşağıdaki özellikler daha ayrıntılı olarak açıklanır.</span><span class="sxs-lookup"><span data-stu-id="412c5-110">What follows in this article will describe this in more detail.</span></span>

## <a name="asynchrony-defined"></a><span data-ttu-id="412c5-111">Asynchrony tanımlı</span><span class="sxs-lookup"><span data-stu-id="412c5-111">Asynchrony defined</span></span>

<span data-ttu-id="412c5-112">Önceki nokta-eşzamanlı olarak birden çok iş parçacığının kullanımından bağımsız olduğu için, biraz daha ayrıntılı bir şekilde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="412c5-112">The previous point - that asynchrony is independent of the utilization of multiple threads - is worth explaining a bit further.</span></span> <span data-ttu-id="412c5-113">Bazen birbiriyle ilgili olan ancak birbirleriyle tamamen bağımsız olan üç kavram vardır:</span><span class="sxs-lookup"><span data-stu-id="412c5-113">There are three concepts that are sometimes related, but strictly independent of one another:</span></span>

- <span data-ttu-id="412c5-114">Zamanlı birden çok hesaplama, çakışan zaman dilimlerinde yürütülür.</span><span class="sxs-lookup"><span data-stu-id="412c5-114">Concurrency; when multiple computations execute in overlapping time periods.</span></span>
- <span data-ttu-id="412c5-115">Paralellik birden çok hesaplama veya tek bir hesaplamanın çeşitli bölümleri tam olarak aynı anda çalıştığında.</span><span class="sxs-lookup"><span data-stu-id="412c5-115">Parallelism; when multiple computations or several parts of a single computation run at exactly the same time.</span></span>
- <span data-ttu-id="412c5-116">Zaman uyumsuzluğu bir veya daha fazla hesaplama ana program akışından ayrı ayrı Yürütülebilirler.</span><span class="sxs-lookup"><span data-stu-id="412c5-116">Asynchrony; when one or more computations can execute separately from the main program flow.</span></span>

<span data-ttu-id="412c5-117">Üçü de birbirine diksiz kavramlardır, ancak özellikle birlikte kullanıldığında kolayca kolayca kanatılabilir.</span><span class="sxs-lookup"><span data-stu-id="412c5-117">All three are orthogonal concepts, but can be easily conflated, especially when they are used together.</span></span> <span data-ttu-id="412c5-118">Örneğin, paralel olarak birden çok zaman uyumsuz hesaplama yürütmeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="412c5-118">For example, you may need to execute multiple asynchronous computations in parallel.</span></span> <span data-ttu-id="412c5-119">Bu, paralellik veya zaman uyumsuzluğu 'in bir diğerinin anlamı olduğunu göstermez.</span><span class="sxs-lookup"><span data-stu-id="412c5-119">This does not mean that parallelism or asynchrony imply one another.</span></span>

<span data-ttu-id="412c5-120">"Zaman uyumsuz" sözcüğünün ilgili listesini göz önünde bulundurmanız durumunda iki parça vardır:</span><span class="sxs-lookup"><span data-stu-id="412c5-120">If you consider the etymology of the word "asynchronous", there are two pieces involved:</span></span>

- <span data-ttu-id="412c5-121">"a", anlamı "Not".</span><span class="sxs-lookup"><span data-stu-id="412c5-121">"a", meaning "not".</span></span>
- <span data-ttu-id="412c5-122">"zaman uyumlu", anlamı "aynı anda".</span><span class="sxs-lookup"><span data-stu-id="412c5-122">"synchronous", meaning "at the same time".</span></span>

<span data-ttu-id="412c5-123">Bu iki terimi birlikte yerleştirdiğinizde "zaman uyumsuz", "aynı anda değil" anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="412c5-123">When you put these two terms together, you'll see that "asynchronous" means "not at the same time".</span></span> <span data-ttu-id="412c5-124">İşte bu kadar!</span><span class="sxs-lookup"><span data-stu-id="412c5-124">That's it!</span></span> <span data-ttu-id="412c5-125">Bu tanımda eşzamanlılık veya paralellik bir engel yoktur.</span><span class="sxs-lookup"><span data-stu-id="412c5-125">There is no implication of concurrency or parallelism in this definition.</span></span> <span data-ttu-id="412c5-126">Bu, pratikte de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="412c5-126">This is also true in practice.</span></span>

<span data-ttu-id="412c5-127">Pratik koşullarda, içindeki F# zaman uyumsuz hesaplamalar ana program akışından bağımsız olarak yürütülecek şekilde zamanlanır.</span><span class="sxs-lookup"><span data-stu-id="412c5-127">In practical terms, asynchronous computations in F# are scheduled to execute independently of the main program flow.</span></span> <span data-ttu-id="412c5-128">Bu, eşzamanlılık veya paralellik anlamına gelmez veya bir hesaplamanın arka planda her zaman gerçekleştiğini göstermez.</span><span class="sxs-lookup"><span data-stu-id="412c5-128">This doesn't imply concurrency or parallelism, nor does it imply that a computation always happens in the background.</span></span> <span data-ttu-id="412c5-129">Aslında, hesaplamanın yapısına ve hesaplamanın yürütüldüğü ortama bağlı olarak zaman uyumsuz hesaplamalar bile zaman uyumlu bir şekilde çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="412c5-129">In fact, asynchronous computations can even execute synchronously, depending on the nature of the computation and the environment the computation is executing in.</span></span>

<span data-ttu-id="412c5-130">Sahip olmanız gereken ana zaman uyumsuz hesaplamaların ana program akışından bağımsız olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="412c5-130">The main takeaway you should have is that asynchronous computations are independent of the main program flow.</span></span> <span data-ttu-id="412c5-131">Zaman uyumsuz hesaplamanın ne zaman ya da nasıl yürütüldüğü hakkında bazı garantiler olsa da, bunları düzenlemek ve zamanlamak için bazı yaklaşımlar vardır.</span><span class="sxs-lookup"><span data-stu-id="412c5-131">Although there are few guarantees about when or how an asynchronous computation executes, there are some approaches to orchestrating and scheduling them.</span></span> <span data-ttu-id="412c5-132">Bu makalenin geri kalanı, zaman uyumsuzluğu için F# temel kavramları ve içinde F#yerleşik olarak bulunan türleri, işlevleri ve ifadeleri nasıl kullanacağınızı anlatıyor.</span><span class="sxs-lookup"><span data-stu-id="412c5-132">The rest of this article explores core concepts for F# asynchrony and how to use the types, functions, and expressions built into F#.</span></span>

## <a name="core-concepts"></a><span data-ttu-id="412c5-133">Temel kavramlar</span><span class="sxs-lookup"><span data-stu-id="412c5-133">Core concepts</span></span>

<span data-ttu-id="412c5-134">' F#De, zaman uyumsuz programlama üç temel kavram etrafında ortalandı:</span><span class="sxs-lookup"><span data-stu-id="412c5-134">In F#, asynchronous programming is centered around three core concepts:</span></span>

- <span data-ttu-id="412c5-135">Birleştirilebilir zaman uyumsuz hesaplamayı temsil eden `Async<'T>` türü.</span><span class="sxs-lookup"><span data-stu-id="412c5-135">The `Async<'T>` type, which represents a composable asynchronous computation.</span></span>
- <span data-ttu-id="412c5-136">`Async` modülü, zaman uyumsuz iş zamanlamanıza, zaman uyumsuz hesaplamalar oluşturmanıza ve zaman uyumsuz sonuçları dönüştürmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="412c5-136">The `Async` module functions, which let you schedule asynchronous work, compose asynchronous computations, and transform asynchronous results.</span></span>
- <span data-ttu-id="412c5-137">Zaman uyumsuz hesaplamalar oluşturmak ve denetlemek için kullanışlı bir sözdizimi sağlayan `async { }` [Hesaplama ifadesi](../../language-reference/computation-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="412c5-137">The `async { }` [computation expression](../../language-reference/computation-expressions.md), which provides a convenient syntax for building and controlling asynchronous computations.</span></span>

<span data-ttu-id="412c5-138">Aşağıdaki örnekte bu üç kavramı görebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="412c5-138">You can see these three concepts in the following example:</span></span>

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

<span data-ttu-id="412c5-139">Örnekte, `printTotalFileBytes` işlevi `string -> Async<unit>`türündedir.</span><span class="sxs-lookup"><span data-stu-id="412c5-139">In the example, the `printTotalFileBytes` function is of type `string -> Async<unit>`.</span></span> <span data-ttu-id="412c5-140">İşlevin çağrılması, zaman uyumsuz hesaplamayı gerçekten yürütmez.</span><span class="sxs-lookup"><span data-stu-id="412c5-140">Calling the function does not actually execute the asynchronous computation.</span></span> <span data-ttu-id="412c5-141">Bunun yerine, zaman uyumsuz olarak yürütülecek işin \* belirtimi olarak davranan bir `Async<unit>` döndürür.</span><span class="sxs-lookup"><span data-stu-id="412c5-141">Instead, it returns an `Async<unit>` that acts as a \*specification- of the work that is to execute asynchronously.</span></span> <span data-ttu-id="412c5-142"><xref:System.IO.File.WriteAllBytesAsync%2A> sonucunu, çağrıldığında uygun bir türe dönüştürecek olan gövdesinde `Async.AwaitTask` çağırır.</span><span class="sxs-lookup"><span data-stu-id="412c5-142">It will call `Async.AwaitTask` in its body, which will convert the result of <xref:System.IO.File.WriteAllBytesAsync%2A> to an appropriate type when it is called.</span></span>

<span data-ttu-id="412c5-143">Başka bir önemli satır `Async.RunSynchronously`çağrıdır.</span><span class="sxs-lookup"><span data-stu-id="412c5-143">Another important line is the call to `Async.RunSynchronously`.</span></span> <span data-ttu-id="412c5-144">Bu, gerçekten zaman uyumsuz bir F# hesaplamayı yürütmek istiyorsanız çağırmanız gereken bir zaman uyumsuz modül başlatma işlevleridir.</span><span class="sxs-lookup"><span data-stu-id="412c5-144">This is one of the Async module starting functions that you'll need to call if you want to actually execute an F# asynchronous computation.</span></span>

<span data-ttu-id="412c5-145">Bu, `async` programlamanın C#/vb stilinde temel bir farktır.</span><span class="sxs-lookup"><span data-stu-id="412c5-145">This is a fundamental difference with the C#/VB style of `async` programming.</span></span> <span data-ttu-id="412c5-146">' F#De, zaman uyumsuz hesaplamalar **soğuk görevler**olarak düşünülebilir.</span><span class="sxs-lookup"><span data-stu-id="412c5-146">In F#, asynchronous computations can be thought of as **Cold tasks**.</span></span> <span data-ttu-id="412c5-147">Gerçekten yürütmek için açıkça başlatılmış olmaları gerekir.</span><span class="sxs-lookup"><span data-stu-id="412c5-147">They must be explicitly started to actually execute.</span></span> <span data-ttu-id="412c5-148">Bu, zaman uyumsuz çalışmayı C#/vbdan daha kolay bir şekilde birleştirip dizmenize olanak sağladığı için bazı avantajlar içerir.</span><span class="sxs-lookup"><span data-stu-id="412c5-148">This has some advantages, as it allows you to combine and sequence asynchronous work much more easily than in C#/VB.</span></span>

## <a name="combining-asynchronous-computations"></a><span data-ttu-id="412c5-149">Zaman uyumsuz hesaplamaları birleştirme</span><span class="sxs-lookup"><span data-stu-id="412c5-149">Combining asynchronous computations</span></span>

<span data-ttu-id="412c5-150">Hesaplamaları birleştirerek önceki bir örnek üzerinde derleme yapan bir örnek aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="412c5-150">Here is an example that builds upon the previous one by combining computations:</span></span>

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

<span data-ttu-id="412c5-151">Gördüğünüz gibi, `main` işlevi çok sayıda daha fazla çağrı yaptı.</span><span class="sxs-lookup"><span data-stu-id="412c5-151">As you can see, the `main` function has quite a few more calls made.</span></span> <span data-ttu-id="412c5-152">Kavramsal olarak, şunları yapar:</span><span class="sxs-lookup"><span data-stu-id="412c5-152">Conceptually, it does the following:</span></span>

1. <span data-ttu-id="412c5-153">Komut satırı bağımsız değişkenlerini `Array.map``Async<unit>` hesaplamalar olarak dönüştürün.</span><span class="sxs-lookup"><span data-stu-id="412c5-153">Transform the command-line arguments into `Async<unit>` computations with `Array.map`.</span></span>
2. <span data-ttu-id="412c5-154">`printTotalFileBytes` hesaplamaları çalışırken zamanlayan ve çalıştıran bir `Async<'T[]>` oluşturun.</span><span class="sxs-lookup"><span data-stu-id="412c5-154">Create an `Async<'T[]>` that schedules and runs the `printTotalFileBytes` computations in parallel when it runs.</span></span>
3. <span data-ttu-id="412c5-155">Paralel hesaplamayı çalıştıracak ve sonucunu yoksaymayacak bir `Async<unit>` oluşturun.</span><span class="sxs-lookup"><span data-stu-id="412c5-155">Create an `Async<unit>` that will run the parallel computation and ignore its result.</span></span>
4. <span data-ttu-id="412c5-156">Son hesaplamayı `Async.RunSynchronously` ve blok tamamlanana kadar açıkça çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="412c5-156">Explicitly run the last computation with `Async.RunSynchronously` and block until it is completes.</span></span>

<span data-ttu-id="412c5-157">Bu program çalıştığında, her komut satırı bağımsız değişkeni için `printTotalFileBytes` paralel olarak çalışır.</span><span class="sxs-lookup"><span data-stu-id="412c5-157">When this program runs, `printTotalFileBytes` runs in parallel for each command-line argument.</span></span> <span data-ttu-id="412c5-158">Zaman uyumsuz hesaplamalar program akışından bağımsız olarak yürütüldüğünden, bilgilerini yazdırdıkları ve yürütmeyi tamamlayabileceği bir sıra yoktur.</span><span class="sxs-lookup"><span data-stu-id="412c5-158">Because asynchronous computations execute independently of program flow, there is no order in which they print their information and finish executing.</span></span> <span data-ttu-id="412c5-159">Hesaplamalar paralel olarak zamanlanır, ancak yürütme sırası garanti edilmez.</span><span class="sxs-lookup"><span data-stu-id="412c5-159">The computations will be scheduled in parallel, but their order of execution is not guaranteed.</span></span>

## <a name="sequencing-asynchronous-computations"></a><span data-ttu-id="412c5-160">Zaman uyumsuz hesaplamaları sıralama</span><span class="sxs-lookup"><span data-stu-id="412c5-160">Sequencing asynchronous computations</span></span>

<span data-ttu-id="412c5-161">`Async<'T>`, zaten çalışan bir görev yerine bir iş belirtimi olduğundan, kolayca daha karmaşık dönüştürmeler gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="412c5-161">Because `Async<'T>` is a specification of work rather than an already-running task, you can perform more intricate transformations easily.</span></span> <span data-ttu-id="412c5-162">Bir dizi zaman uyumsuz hesaplamalar, bunlardan sonra çalıştırılacak bir örnek aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="412c5-162">Here is an example that sequences a set of Async computations so they execute one after another.</span></span>

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
    |> Async.RunSynchronously
    |> ignore
```

<span data-ttu-id="412c5-163">Bu, `printTotalFileBytes`, paralel olarak zamanlamak yerine `argv` öğeleri sırasıyla yürütmek üzere zamanlanır.</span><span class="sxs-lookup"><span data-stu-id="412c5-163">This will schedule `printTotalFileBytes` to execute in the order of the elements of `argv` rather than scheduling them in parallel.</span></span> <span data-ttu-id="412c5-164">Bir sonraki öğe, son hesaplamanın yürütülmesi bitinceye kadar zamanlanmayacak, bu hesaplamalar yürütmeyle ilgili bir çakışma olmaması gibi sıralanacaktır.</span><span class="sxs-lookup"><span data-stu-id="412c5-164">Because the next item will not be scheduled until after the last computation has finished executing, the computations are sequenced such that there is no overlap in their execution.</span></span>

## <a name="important-async-module-functions"></a><span data-ttu-id="412c5-165">Önemli zaman uyumsuz modül işlevleri</span><span class="sxs-lookup"><span data-stu-id="412c5-165">Important Async module functions</span></span>

<span data-ttu-id="412c5-166">Zaman uyumsuz kod F# yazdığınızda, genellikle sizin için hesaplamaların zamanlamasını işleyen bir çerçeve ile etkileşime geçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="412c5-166">When you write async code in F# you'll usually interact with a framework that handles scheduling of computations for you.</span></span> <span data-ttu-id="412c5-167">Ancak, bu her zaman durum değildir, bu nedenle zaman uyumsuz çalışmayı zamanlamak için çeşitli başlangıç işlevlerini öğrenmenizde yarar vardır.</span><span class="sxs-lookup"><span data-stu-id="412c5-167">However, this is not always the case, so it is good to learn the various starting functions to schedule asynchronous work.</span></span>

<span data-ttu-id="412c5-168">Zaman F# uyumsuz hesaplamalar zaten yürütülmekte olan çalışmanın temsili yerine bir iş _belirtimi_ olduğundan, bu, bir başlangıç işleviyle açıkça başlatılmaları gerekir.</span><span class="sxs-lookup"><span data-stu-id="412c5-168">Because F# asynchronous computations are a _specification_ of work rather than a representation of work that is already executing, they must be explicitly started with a starting function.</span></span> <span data-ttu-id="412c5-169">Farklı bağlamlarda yararlı olan çok sayıda [zaman uyumsuz başlatma işlevi](https://msdn.microsoft.com/library/ee370232.aspx) vardır.</span><span class="sxs-lookup"><span data-stu-id="412c5-169">There are many [Async starting functions](https://msdn.microsoft.com/library/ee370232.aspx) that are helpful in different contexts.</span></span> <span data-ttu-id="412c5-170">Aşağıdaki bölümde daha yaygın başlangıç işlevlerinin bazıları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="412c5-170">The following section describes some of the more common starting functions.</span></span>

### <a name="asyncstartchild"></a><span data-ttu-id="412c5-171">Async. StartChild</span><span class="sxs-lookup"><span data-stu-id="412c5-171">Async.StartChild</span></span>

<span data-ttu-id="412c5-172">Bir zaman uyumsuz hesaplama içinde bir alt hesaplama başlatır.</span><span class="sxs-lookup"><span data-stu-id="412c5-172">Starts a child computation within an asynchronous computation.</span></span> <span data-ttu-id="412c5-173">Bu, birden çok zaman uyumsuz hesaplamaların eşzamanlı olarak yürütülmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="412c5-173">This allows multiple asynchronous computations to be executed concurrently.</span></span> <span data-ttu-id="412c5-174">Alt hesaplama, bir iptal belirtecini üst hesaplama ile paylaşır.</span><span class="sxs-lookup"><span data-stu-id="412c5-174">The child computation shares a cancellation token with the parent computation.</span></span> <span data-ttu-id="412c5-175">Üst hesaplama iptal edilirse, alt hesaplama da iptal edilir.</span><span class="sxs-lookup"><span data-stu-id="412c5-175">If the parent computation is canceled, the child computation is also canceled.</span></span>

<span data-ttu-id="412c5-176">İmza:</span><span class="sxs-lookup"><span data-stu-id="412c5-176">Signature:</span></span>

```fsharp
computation: Async<'T> - timeout: ?int -> Async<Async<'T>>
```

<span data-ttu-id="412c5-177">Ne zaman kullanılır:</span><span class="sxs-lookup"><span data-stu-id="412c5-177">When to use:</span></span>

- <span data-ttu-id="412c5-178">Aynı anda birden çok zaman uyumsuz hesaplamalar çalıştırmak istediğinizde, ancak paralel olarak zamanlanamaz.</span><span class="sxs-lookup"><span data-stu-id="412c5-178">When you want to execute multiple asynchronous computations concurrently rather than one at a time, but not have them scheduled in parallel.</span></span>
- <span data-ttu-id="412c5-179">Bir alt hesaplamanın ömrünü bir üst hesaplamadan bağlamak istediğinizde.</span><span class="sxs-lookup"><span data-stu-id="412c5-179">When you wish to tie the lifetime of a child computation to that of a parent computation.</span></span>

<span data-ttu-id="412c5-180">İçin izlenecek:</span><span class="sxs-lookup"><span data-stu-id="412c5-180">What to watch out for:</span></span>

- <span data-ttu-id="412c5-181">`Async.StartChild` ile birden çok hesaplama başlatmak, bunları paralel olarak zamanlamaya göre aynı değildir.</span><span class="sxs-lookup"><span data-stu-id="412c5-181">Starting multiple computations with `Async.StartChild` isn't the same as scheduling them in parallel.</span></span> <span data-ttu-id="412c5-182">Hesaplamaları paralel olarak zamanlamak istiyorsanız `Async.Parallel`kullanın.</span><span class="sxs-lookup"><span data-stu-id="412c5-182">If you wish to schedule computations in parallel, use `Async.Parallel`.</span></span>
- <span data-ttu-id="412c5-183">Bir üst hesaplamayı iptal etmek, başlattığı tüm alt hesaplamaların iptalini tetikler.</span><span class="sxs-lookup"><span data-stu-id="412c5-183">Canceling a parent computation will trigger cancellation of all child computations it started.</span></span>

### <a name="asyncstartimmediate"></a><span data-ttu-id="412c5-184">Async. StartImmediate</span><span class="sxs-lookup"><span data-stu-id="412c5-184">Async.StartImmediate</span></span>

<span data-ttu-id="412c5-185">Geçerli işletim sistemi iş parçacığında hemen başlayarak bir zaman uyumsuz hesaplama çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="412c5-185">Runs an asynchronous computation, starting immediately on the current operating system thread.</span></span> <span data-ttu-id="412c5-186">Bu, hesaplama sırasında çağıran iş parçacığında bir şeyi güncelleştirmeniz gerekiyorsa yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="412c5-186">This is helpful if you need to update something on the calling thread during the computation.</span></span> <span data-ttu-id="412c5-187">Örneğin, bir zaman uyumsuz hesaplamanın bir kullanıcı arabirimini güncelleştirmesi gerekiyorsa (bir ilerleme çubuğunu güncelleştirme gibi), `Async.StartImmediate` kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="412c5-187">For example, if an asynchronous computation must update a UI (such as updating a progress bar), then `Async.StartImmediate` should be used.</span></span>

<span data-ttu-id="412c5-188">İmza:</span><span class="sxs-lookup"><span data-stu-id="412c5-188">Signature:</span></span>

```fsharp
computation: Async<unit> - cancellationToken: ?CancellationToken -> unit
```

<span data-ttu-id="412c5-189">Ne zaman kullanılır:</span><span class="sxs-lookup"><span data-stu-id="412c5-189">When to use:</span></span>

- <span data-ttu-id="412c5-190">Bir zaman uyumsuz hesaplamanın ortasında çağıran iş parçacığında bir şeyi güncelleştirmeniz gerektiğinde.</span><span class="sxs-lookup"><span data-stu-id="412c5-190">When you need to update something on the calling thread in the middle of an asynchronous computation.</span></span>

<span data-ttu-id="412c5-191">İçin izlenecek:</span><span class="sxs-lookup"><span data-stu-id="412c5-191">What to watch out for:</span></span>

- <span data-ttu-id="412c5-192">Zaman uyumsuz hesaplama içindeki kod, üzerinde zamanlanabilecek her iş parçacığında çalışır.</span><span class="sxs-lookup"><span data-stu-id="412c5-192">Code in the asynchronous computation will run on whatever thread one happens to be scheduled on.</span></span> <span data-ttu-id="412c5-193">Bu iş parçacığı, bir kullanıcı arabirimi iş parçacığı gibi bir şekilde hassas olduğunda sorunlu olabilir.</span><span class="sxs-lookup"><span data-stu-id="412c5-193">This can be problematic if that thread is in some way sensitive, such as a UI thread.</span></span> <span data-ttu-id="412c5-194">Bu gibi durumlarda, `Async.StartImmediate` kullanımı uygunsuz olabilir.</span><span class="sxs-lookup"><span data-stu-id="412c5-194">In such cases, `Async.StartImmediate` is likely inappropriate to use.</span></span>

### <a name="asyncstartastask"></a><span data-ttu-id="412c5-195">Async. StartAsTask</span><span class="sxs-lookup"><span data-stu-id="412c5-195">Async.StartAsTask</span></span>

<span data-ttu-id="412c5-196">İş parçacığı havuzunda bir hesaplama yürütür.</span><span class="sxs-lookup"><span data-stu-id="412c5-196">Executes a computation in the thread pool.</span></span> <span data-ttu-id="412c5-197">Hesaplama sonlandırıldığında karşılık gelen durumda tamamlanacak bir <xref:System.Threading.Tasks.Task%601> döndürür (sonucu üretir, özel durum oluşturur veya iptal edilir).</span><span class="sxs-lookup"><span data-stu-id="412c5-197">Returns a <xref:System.Threading.Tasks.Task%601> that will be completed on the corresponding state once the computation terminates (produces the result, throws exception, or gets canceled).</span></span> <span data-ttu-id="412c5-198">İptal belirteci sağlanmazsa, varsayılan iptal belirteci kullanılır.</span><span class="sxs-lookup"><span data-stu-id="412c5-198">If no cancellation token is provided, then the default cancellation token is used.</span></span>

<span data-ttu-id="412c5-199">İmza:</span><span class="sxs-lookup"><span data-stu-id="412c5-199">Signature:</span></span>

```fsharp
computation: Async<'T> - taskCreationOptions: ?TaskCreationOptions - cancellationToken: ?CancellationToken -> Task<'T>
```

<span data-ttu-id="412c5-200">Ne zaman kullanılır:</span><span class="sxs-lookup"><span data-stu-id="412c5-200">When to use:</span></span>

- <span data-ttu-id="412c5-201">Bir <xref:System.Threading.Tasks.Task%601> zaman uyumsuz bir hesaplamanın sonucunu göstermesini bekleyen bir .NET API 'sine çağrı yapmanız gerektiğinde.</span><span class="sxs-lookup"><span data-stu-id="412c5-201">When you need to call into a .NET API that expects a <xref:System.Threading.Tasks.Task%601> to represent the result of an asynchronous computation.</span></span>

<span data-ttu-id="412c5-202">İçin izlenecek:</span><span class="sxs-lookup"><span data-stu-id="412c5-202">What to watch out for:</span></span>

- <span data-ttu-id="412c5-203">Bu çağrı, sık kullanılan ek yükü artırabilen ek bir `Task` nesnesi ayırır.</span><span class="sxs-lookup"><span data-stu-id="412c5-203">This call will allocate an additional `Task` object, which can increase overhead if it is used often.</span></span>

### <a name="asyncparallel"></a><span data-ttu-id="412c5-204">Async. Parallel</span><span class="sxs-lookup"><span data-stu-id="412c5-204">Async.Parallel</span></span>

<span data-ttu-id="412c5-205">Paralel olarak yürütülecek zaman uyumsuz hesaplamalar dizisini zamanlar.</span><span class="sxs-lookup"><span data-stu-id="412c5-205">Schedules a sequence of asynchronous computations to be executed in parallel.</span></span> <span data-ttu-id="412c5-206">Paralellik derecesi, `maxDegreesOfParallelism` parametresi belirtilerek isteğe bağlı olarak ayarlanabilir/kısıtlanacaktır.</span><span class="sxs-lookup"><span data-stu-id="412c5-206">The degree of parallelism can be optionally tuned/throttled by specifying the `maxDegreesOfParallelism` parameter.</span></span>

<span data-ttu-id="412c5-207">İmza:</span><span class="sxs-lookup"><span data-stu-id="412c5-207">Signature:</span></span>

```fsharp
computations: seq<Async<'T>> - ?maxDegreesOfParallelism: int -> Async<'T[]>
```

<span data-ttu-id="412c5-208">Ne zaman kullanılmalı:</span><span class="sxs-lookup"><span data-stu-id="412c5-208">When to use it:</span></span>

- <span data-ttu-id="412c5-209">Aynı anda bir hesaplamalar kümesi çalıştırmanız gerekiyorsa ve bunların yürütme sırasına göre hiçbir rahatlık olmaz.</span><span class="sxs-lookup"><span data-stu-id="412c5-209">If you need to run a set of computations at the same time and have no reliance on their order of execution.</span></span>
- <span data-ttu-id="412c5-210">Tüm tamamlanana kadar paralel olarak zamanlanan hesaplamaların sonuçlarına gerek yoksa.</span><span class="sxs-lookup"><span data-stu-id="412c5-210">If you don't require results from computations scheduled in parallel until they have all completed.</span></span>

<span data-ttu-id="412c5-211">İçin izlenecek:</span><span class="sxs-lookup"><span data-stu-id="412c5-211">What to watch out for:</span></span>

- <span data-ttu-id="412c5-212">Yalnızca tüm hesaplamalar bittikten sonra elde edilen değer dizisine erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="412c5-212">You can only access the resulting array of values once all computations have finished.</span></span>
- <span data-ttu-id="412c5-213">Hesaplamalar çalıştırılacak, ancak zamanlanan işleri çalıştırırlar.</span><span class="sxs-lookup"><span data-stu-id="412c5-213">Computations will be run however they end up getting scheduled.</span></span> <span data-ttu-id="412c5-214">Bu, yürütmesinin sırasıyla güvenemeyeceğiniz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="412c5-214">This means you cannot rely on their order of their execution.</span></span>

### <a name="asyncsequential"></a><span data-ttu-id="412c5-215">Async. Sequential</span><span class="sxs-lookup"><span data-stu-id="412c5-215">Async.Sequential</span></span>

<span data-ttu-id="412c5-216">Bir dizi zaman uyumsuz hesaplamaların, geçirildikleri sırada yürütülecek şekilde zamanlamasını zamanlar.</span><span class="sxs-lookup"><span data-stu-id="412c5-216">Schedules a sequence of asynchronous computations to be executed in the order that they are passed.</span></span> <span data-ttu-id="412c5-217">İlk hesaplama yürütülür, sonra bir sonraki ve bu şekilde devam eder.</span><span class="sxs-lookup"><span data-stu-id="412c5-217">The first computation will be executed, then the next, and so on.</span></span> <span data-ttu-id="412c5-218">Paralel olarak hiçbir hesaplama yürütülmeyecektir.</span><span class="sxs-lookup"><span data-stu-id="412c5-218">No computations will be executed in parallel.</span></span>

<span data-ttu-id="412c5-219">İmza:</span><span class="sxs-lookup"><span data-stu-id="412c5-219">Signature:</span></span>

```fsharp
computations: seq<Async<'T>> -> Async<'T[]>
```

<span data-ttu-id="412c5-220">Ne zaman kullanılmalı:</span><span class="sxs-lookup"><span data-stu-id="412c5-220">When to use it:</span></span>

- <span data-ttu-id="412c5-221">Sırayla birden çok hesaplama yürütmeniz gerekiyorsa.</span><span class="sxs-lookup"><span data-stu-id="412c5-221">If you need to execute multiple computations in order.</span></span>

<span data-ttu-id="412c5-222">İçin izlenecek:</span><span class="sxs-lookup"><span data-stu-id="412c5-222">What to watch out for:</span></span>

- <span data-ttu-id="412c5-223">Yalnızca tüm hesaplamalar bittikten sonra elde edilen değer dizisine erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="412c5-223">You can only access the resulting array of values once all computations have finished.</span></span>
- <span data-ttu-id="412c5-224">Hesaplamalar, bu işleve geçirildikleri sırada çalıştırılır, bu da sonuçlar döndürülmeden önce geçecek daha fazla zaman geçilecektir.</span><span class="sxs-lookup"><span data-stu-id="412c5-224">Computations will be run in the order that they are passed to this function, which can mean that more time will elapse before the results are returned.</span></span>

### <a name="asyncawaittask"></a><span data-ttu-id="412c5-225">Async. AwaitTask</span><span class="sxs-lookup"><span data-stu-id="412c5-225">Async.AwaitTask</span></span>

<span data-ttu-id="412c5-226">Verilen <xref:System.Threading.Tasks.Task%601> tamamlanmasını bekleyen bir zaman uyumsuz hesaplama döndürür ve bunun sonucunu bir `Async<'T>` olarak döndürür</span><span class="sxs-lookup"><span data-stu-id="412c5-226">Returns an asynchronous computation that waits for the given <xref:System.Threading.Tasks.Task%601> to complete and returns its result as an `Async<'T>`</span></span>

<span data-ttu-id="412c5-227">İmza:</span><span class="sxs-lookup"><span data-stu-id="412c5-227">Signature:</span></span>

```fsharp
task: Task<'T>  -> Async<'T>
```

<span data-ttu-id="412c5-228">Ne zaman kullanılır:</span><span class="sxs-lookup"><span data-stu-id="412c5-228">When to use:</span></span>

- <span data-ttu-id="412c5-229">F# Zaman uyumsuz bir hesaplama içinde <xref:System.Threading.Tasks.Task%601> döndüren bir .NET API 'si kullanıyorsanız.</span><span class="sxs-lookup"><span data-stu-id="412c5-229">When you are consuming a .NET API that returns a <xref:System.Threading.Tasks.Task%601> within an F# asynchronous computation.</span></span>

<span data-ttu-id="412c5-230">İçin izlenecek:</span><span class="sxs-lookup"><span data-stu-id="412c5-230">What to watch out for:</span></span>

- <span data-ttu-id="412c5-231">Özel durumlar, görev paralel kitaplığı 'nın kuralına göre <xref:System.AggregateException> sarmalanır ve bu, F# zaman uyumsuz genel yüzeylerin özel durumlarından farklıdır.</span><span class="sxs-lookup"><span data-stu-id="412c5-231">Exceptions are wrapped in <xref:System.AggregateException> following the convention of the Task Parallel Library, and this is different from how F# async generally surfaces exceptions.</span></span>

### <a name="asynccatch"></a><span data-ttu-id="412c5-232">Async. catch</span><span class="sxs-lookup"><span data-stu-id="412c5-232">Async.Catch</span></span>

<span data-ttu-id="412c5-233">Verilen bir `Async<'T>`yürüten zaman uyumsuz bir hesaplama oluşturur ve bir `Async<Choice<'T, exn>>`döndürür.</span><span class="sxs-lookup"><span data-stu-id="412c5-233">Creates an asynchronous computation that executes a given `Async<'T>`, returning an `Async<Choice<'T, exn>>`.</span></span> <span data-ttu-id="412c5-234">Verilen `Async<'T>` başarıyla tamamlanırsa, sonuç değeri ile bir `Choice1Of2` döndürülür.</span><span class="sxs-lookup"><span data-stu-id="412c5-234">If the given `Async<'T>` completes successfully, then a `Choice1Of2` is returned with the resultant value.</span></span> <span data-ttu-id="412c5-235">Tamamlanmadan önce bir özel durum oluşturulursa, oluşturulan özel durumla bir `Choice2of2` döndürülür.</span><span class="sxs-lookup"><span data-stu-id="412c5-235">If an exception is thrown before it completes, then a `Choice2of2` is returned with the raised exception.</span></span> <span data-ttu-id="412c5-236">Bu, birçok hesaplamayı oluşturan zaman uyumsuz bir hesaplamada kullanılırsa ve bu hesaplamaların biri bir özel durum oluşturursa, dahil edilen hesaplama tamamen durdurulur.</span><span class="sxs-lookup"><span data-stu-id="412c5-236">If it is used on an asynchronous computation that is itself composed of many computations, and one of those computations throws an exception, the encompassing computation will be stopped entirely.</span></span>

<span data-ttu-id="412c5-237">İmza:</span><span class="sxs-lookup"><span data-stu-id="412c5-237">Signature:</span></span>

```fsharp
computation: Async<'T> -> Async<Choice<'T, exn>>
```

<span data-ttu-id="412c5-238">Ne zaman kullanılır:</span><span class="sxs-lookup"><span data-stu-id="412c5-238">When to use:</span></span>

- <span data-ttu-id="412c5-239">Bir özel durumla başarısız olabilecek ve çağıranın bu özel durumu işlemek istediğiniz zaman uyumsuz iş yaparken.</span><span class="sxs-lookup"><span data-stu-id="412c5-239">When you are performing asynchronous work that may fail with an exception and you want to handle that exception in the caller.</span></span>

<span data-ttu-id="412c5-240">İçin izlenecek:</span><span class="sxs-lookup"><span data-stu-id="412c5-240">What to watch out for:</span></span>

- <span data-ttu-id="412c5-241">Birleşik veya sıralı zaman uyumsuz hesaplamalar kullanılırken, "iç" hesaplamalarından biri bir özel durum oluşturursa, birlikte bulunan hesaplama tam olarak durdurulur.</span><span class="sxs-lookup"><span data-stu-id="412c5-241">When using combined or sequenced asynchronous computations, the encompassing computation will fully stop if one of its "internal" computations throws an exception.</span></span>

### <a name="asyncignore"></a><span data-ttu-id="412c5-242">Async. Ignore</span><span class="sxs-lookup"><span data-stu-id="412c5-242">Async.Ignore</span></span>

<span data-ttu-id="412c5-243">Verilen hesaplamayı çalıştıran ve sonucunu yoksayan zaman uyumsuz bir hesaplama oluşturur.</span><span class="sxs-lookup"><span data-stu-id="412c5-243">Creates an asynchronous computation that runs the given computation and ignores its result.</span></span>

<span data-ttu-id="412c5-244">İmza:</span><span class="sxs-lookup"><span data-stu-id="412c5-244">Signature:</span></span>

```fsharp
computation: Async<'T> -> Async<unit>
```

<span data-ttu-id="412c5-245">Ne zaman kullanılır:</span><span class="sxs-lookup"><span data-stu-id="412c5-245">When to use:</span></span>

- <span data-ttu-id="412c5-246">Zaman uyumsuz bir hesaplamanız olduğunda, sonucu gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="412c5-246">When you have an asynchronous computation whose result is not needed.</span></span> <span data-ttu-id="412c5-247">Bu, zaman uyumsuz kod için `ignore` koduna benzerdir.</span><span class="sxs-lookup"><span data-stu-id="412c5-247">This is analogous to the `ignore` code for non-asynchronous code.</span></span>

<span data-ttu-id="412c5-248">İçin izlenecek:</span><span class="sxs-lookup"><span data-stu-id="412c5-248">What to watch out for:</span></span>

- <span data-ttu-id="412c5-249">`Async.Start` veya `Async<unit>`gerektiren başka bir işlevi kullanmak istiyorsanız bunu kullanmanız gerekiyorsa, sonucun atılıp atılmayacağı konusunda düşünün.</span><span class="sxs-lookup"><span data-stu-id="412c5-249">If you must use this because you wish to use `Async.Start` or another function that requires `Async<unit>`, consider if discarding the result is okay to do.</span></span> <span data-ttu-id="412c5-250">Yalnızca tür imzasını sığdırmak için sonuçların atılması genellikle yapılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="412c5-250">Discarding results just to fit a type signature should not generally be done.</span></span>

### <a name="asyncrunsynchronously"></a><span data-ttu-id="412c5-251">Async. RunSynchronously</span><span class="sxs-lookup"><span data-stu-id="412c5-251">Async.RunSynchronously</span></span>

<span data-ttu-id="412c5-252">Zaman uyumsuz bir hesaplama çalıştırır ve bunun sonucunu çağıran iş parçacığında bekler.</span><span class="sxs-lookup"><span data-stu-id="412c5-252">Runs an asynchronous computation and awaits its result on the calling thread.</span></span> <span data-ttu-id="412c5-253">Bu çağrı engelleniyor.</span><span class="sxs-lookup"><span data-stu-id="412c5-253">This call is blocking.</span></span>

<span data-ttu-id="412c5-254">İmza:</span><span class="sxs-lookup"><span data-stu-id="412c5-254">Signature:</span></span>

```fsharp
computation: Async<'T> - timeout: ?int - cancellationToken: ?CancellationToken -> 'T
```

<span data-ttu-id="412c5-255">Ne zaman kullanılmalı:</span><span class="sxs-lookup"><span data-stu-id="412c5-255">When to use it:</span></span>

- <span data-ttu-id="412c5-256">İhtiyacınız varsa, çalıştırılabilir dosyanın giriş noktasında uygulamayı yalnızca bir kez kullanın.</span><span class="sxs-lookup"><span data-stu-id="412c5-256">If you need it, use it only once in an application - at the entry point for an executable.</span></span>
- <span data-ttu-id="412c5-257">Performansla ilgilenmezseniz ve aynı anda başka bir zaman uyumsuz işlem kümesi yürütmek istiyorsanız.</span><span class="sxs-lookup"><span data-stu-id="412c5-257">When you don't care about performance and want to execute a set of other asynchronous operations at once.</span></span>

<span data-ttu-id="412c5-258">İçin izlenecek:</span><span class="sxs-lookup"><span data-stu-id="412c5-258">What to watch out for:</span></span>

- <span data-ttu-id="412c5-259">`Async.RunSynchronously` çağırmak, yürütme tamamlanana kadar çağıran iş parçacığını engeller.</span><span class="sxs-lookup"><span data-stu-id="412c5-259">Calling `Async.RunSynchronously` blocks the calling thread until the execution completes.</span></span>

### <a name="asyncstart"></a><span data-ttu-id="412c5-260">Async. Start</span><span class="sxs-lookup"><span data-stu-id="412c5-260">Async.Start</span></span>

<span data-ttu-id="412c5-261">`unit`döndüren iş parçacığı havuzunda zaman uyumsuz bir hesaplama başlatır.</span><span class="sxs-lookup"><span data-stu-id="412c5-261">Starts an asynchronous computation in the thread pool that returns `unit`.</span></span> <span data-ttu-id="412c5-262">Sonucunu beklemez.</span><span class="sxs-lookup"><span data-stu-id="412c5-262">Doesn't wait for its result.</span></span> <span data-ttu-id="412c5-263">`Async.Start` ile başlatılan iç içe hesaplamalar, onları çağıran üst hesaplamadan tamamen bağımsız olarak başlatılır.</span><span class="sxs-lookup"><span data-stu-id="412c5-263">Nested computations started with `Async.Start` are started completely independently of the parent computation that called them.</span></span> <span data-ttu-id="412c5-264">Yaşam süresi herhangi bir üst hesaplamasına bağlı değildir.</span><span class="sxs-lookup"><span data-stu-id="412c5-264">Their lifetime is not tied to any parent computation.</span></span> <span data-ttu-id="412c5-265">Üst hesaplama iptal edilirse, hiçbir alt hesaplama iptal edilemez.</span><span class="sxs-lookup"><span data-stu-id="412c5-265">If the parent computation is canceled, no child computations are cancelled.</span></span>

<span data-ttu-id="412c5-266">İmza:</span><span class="sxs-lookup"><span data-stu-id="412c5-266">Signature:</span></span>

```fsharp
computation: Async<unit> - cancellationToken: ?CancellationToken -> unit
```

<span data-ttu-id="412c5-267">Yalnızca şu durumlarda kullanın:</span><span class="sxs-lookup"><span data-stu-id="412c5-267">Use only when:</span></span>

- <span data-ttu-id="412c5-268">Bir sonuç elde etmez ve/veya işlemesini gerektirmeyen zaman uyumsuz bir hesaplasahipsiniz.</span><span class="sxs-lookup"><span data-stu-id="412c5-268">You have an asynchronous computation that doesn't yield a result and/or require processing of one.</span></span>
- <span data-ttu-id="412c5-269">Zaman uyumsuz bir hesaplamanın tamamlanışında, bilmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="412c5-269">You don't need to know when an asynchronous computation completes.</span></span>
- <span data-ttu-id="412c5-270">Zaman uyumsuz bir hesaplamanın çalışacağı iş parçacığını ilgilenmezsiniz.</span><span class="sxs-lookup"><span data-stu-id="412c5-270">You don't care which thread an asynchronous computation runs on.</span></span>
- <span data-ttu-id="412c5-271">Görevden kaynaklanan özel durumları bilmeniz veya bunları raporlamak zorunda kalmazsınız.</span><span class="sxs-lookup"><span data-stu-id="412c5-271">You don't have any need to be aware of or report exceptions resulting from the task.</span></span>

<span data-ttu-id="412c5-272">İçin izlenecek:</span><span class="sxs-lookup"><span data-stu-id="412c5-272">What to watch out for:</span></span>

- <span data-ttu-id="412c5-273">`Async.Start` ile başlatılan hesaplamalar tarafından oluşturulan özel durumlar çağırana yayılmaz.</span><span class="sxs-lookup"><span data-stu-id="412c5-273">Exceptions raised by computations started with `Async.Start` aren't propagated to the caller.</span></span> <span data-ttu-id="412c5-274">Çağrı yığını tamamen kalıcı olmayacak.</span><span class="sxs-lookup"><span data-stu-id="412c5-274">The call stack will be completely unwound.</span></span>
- <span data-ttu-id="412c5-275">`Async.Start` ile başlatılan tüm etki alanı işleri (`printfn`çağırma gibi), bir program yürütmenin ana iş parçacığında etkisinin oluşmasına neden olmaz.</span><span class="sxs-lookup"><span data-stu-id="412c5-275">Any effectful work (such as calling `printfn`) started with `Async.Start` won't cause the effect to happen on the main thread of a program's execution.</span></span>

## <a name="interoperating-with-net"></a><span data-ttu-id="412c5-276">.NET ile çalışma</span><span class="sxs-lookup"><span data-stu-id="412c5-276">Interoperating with .NET</span></span>

<span data-ttu-id="412c5-277">Zaman uyumsuz [/await](../../../standard/async.md)stili zaman uyumsuz programlama kullanan C# bir .NET kitaplığı veya kod temeli ile çalışıyor olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="412c5-277">You may be working with a .NET library or C# codebase that uses [async/await](../../../standard/async.md)-style asynchronous programming.</span></span> <span data-ttu-id="412c5-278">C# .Net kitaplıklarının çoğunluğu, <xref:System.Threading.Tasks.Task%601> ve <xref:System.Threading.Tasks.Task> türlerini `Async<'T>`yerine çekirdek soyutlamaları olarak kullandığından, bu iki yaklaşım arasında bir sınırı bir sınır olarak zaman arasına almalısınız.</span><span class="sxs-lookup"><span data-stu-id="412c5-278">Because C# and the majority of .NET libraries use the <xref:System.Threading.Tasks.Task%601> and <xref:System.Threading.Tasks.Task> types as their core abstractions rather than `Async<'T>`, you must cross a boundary between these two approaches to asynchrony.</span></span>

### <a name="how-to-work-with-net-async-and-taskt"></a><span data-ttu-id="412c5-279">.NET Async ve `Task<T>` ile çalışma</span><span class="sxs-lookup"><span data-stu-id="412c5-279">How to work with .NET async and `Task<T>`</span></span>

<span data-ttu-id="412c5-280"><xref:System.Threading.Tasks.Task%601> kullanan .NET Async kitaplıkları ve codetabanlarıyla çalışma (yani, dönüş değerleri olan zaman uyumsuz hesaplamalar) basittir ve ile F#yerleşik destek vardır.</span><span class="sxs-lookup"><span data-stu-id="412c5-280">Working with .NET async libraries and codebases that use <xref:System.Threading.Tasks.Task%601> (that is, async computations that have return values) is straightforward and has built-in support with F#.</span></span>

<span data-ttu-id="412c5-281">.NET zaman uyumsuz hesaplamayı beklemek için `Async.AwaitTask` işlevini kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="412c5-281">You can use the `Async.AwaitTask` function to await a .NET asynchronous computation:</span></span>

```fsharp
let getValueFromLibrary param =
    async {
        let! value = DotNetLibrary.GetValueAsync param |> Async.AwaitTask
        return value
    }
```

<span data-ttu-id="412c5-282">Bir .NET çağıranına zaman uyumsuz bir hesaplama geçirmek için `Async.StartAsTask` işlevini kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="412c5-282">You can use the `Async.StartAsTask` function to pass an asynchronous computation to a .NET caller:</span></span>

```fsharp
let computationForCaller param =
    async {
        let! result = getAsyncResult param
        return result
    } |> Async.StartAsTask
```

### <a name="how-to-work-with-net-async-and-task"></a><span data-ttu-id="412c5-283">.NET Async ve `Task` ile çalışma</span><span class="sxs-lookup"><span data-stu-id="412c5-283">How to work with .NET async and `Task`</span></span>

<span data-ttu-id="412c5-284"><xref:System.Threading.Tasks.Task> kullanan API 'lerle çalışmak için (yani, bir değer döndürmeyen .NET zaman uyumsuz hesaplamalar), bir `Async<'T>` <xref:System.Threading.Tasks.Task>dönüştürecek ek bir işlev eklemeniz gerekebilir:</span><span class="sxs-lookup"><span data-stu-id="412c5-284">To work with APIs that use <xref:System.Threading.Tasks.Task> (that is, .NET async computations that do not return a value), you may need to add an additional function that will convert an `Async<'T>` to a <xref:System.Threading.Tasks.Task>:</span></span>

```fsharp
module Async =
    // Async<unit> -> Task
    let startTaskFromAsyncUnit (comp: Async<unit>) =
        Async.StartAsTask comp :> Task
```

<span data-ttu-id="412c5-285">Girdi olarak <xref:System.Threading.Tasks.Task> kabul eden bir `Async.AwaitTask` zaten var.</span><span class="sxs-lookup"><span data-stu-id="412c5-285">There is already an `Async.AwaitTask` that accepts a <xref:System.Threading.Tasks.Task> as input.</span></span> <span data-ttu-id="412c5-286">Bu ve daha önce tanımlanmış `startTaskFromAsyncUnit` işleviyle, zaman uyumsuz bir F# hesaplamadan <xref:System.Threading.Tasks.Task> türleri başlatabilir ve bekleolursunuz.</span><span class="sxs-lookup"><span data-stu-id="412c5-286">With this and the previously defined `startTaskFromAsyncUnit` function, you can start and await <xref:System.Threading.Tasks.Task> types from an F# async computation.</span></span>

## <a name="relationship-to-multithreading"></a><span data-ttu-id="412c5-287">Çoklu iş parçacıklı ilişki</span><span class="sxs-lookup"><span data-stu-id="412c5-287">Relationship to multithreading</span></span>

<span data-ttu-id="412c5-288">Bu makale boyunca iş parçacığına bahsedilse de, dikkat etmeniz gereken iki önemli nokta vardır:</span><span class="sxs-lookup"><span data-stu-id="412c5-288">Although threading is mentioned throughout this article, there are two important things to remember:</span></span>

1. <span data-ttu-id="412c5-289">Geçerli iş parçacığında açıkça başlamadıkça, zaman uyumsuz bir hesaplama ve bir iş parçacığı arasında benzeşim yoktur.</span><span class="sxs-lookup"><span data-stu-id="412c5-289">There is no affinity between an asynchronous computation and a thread, unless explicitly started on the current thread.</span></span>
1. <span data-ttu-id="412c5-290">İçinde F# zaman uyumsuz programlama, çoklu iş parçacığı oluşturma için bir soyutlama değildir.</span><span class="sxs-lookup"><span data-stu-id="412c5-290">Asynchronous programming in F# is not an abstraction for multi-threading.</span></span>

<span data-ttu-id="412c5-291">Örneğin, bir hesaplama, işin doğasına bağlı olarak, çağıranın iş parçacığı üzerinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="412c5-291">For example, a computation may actually run on its caller's thread, depending on the nature of the work.</span></span> <span data-ttu-id="412c5-292">Bir hesaplama Ayrıca, iş parçacıkları arasında "bekleyen" (bir ağ çağrısının aktarım aşamasında olduğu gibi) kullanım süreleri arasında yararlı bir süre için ödünç alınan "atlayabilir".</span><span class="sxs-lookup"><span data-stu-id="412c5-292">A computation could also "jump" between threads, borrowing them for a small amount of time to do useful work in between periods of "waiting" (such as when a network call is in transit).</span></span>

<span data-ttu-id="412c5-293">, F# Geçerli iş parçacığında (veya açık olarak geçerli iş parçacığında değil) zaman uyumsuz bir hesaplama başlatmak için bazı yetenekler sağlar, ancak zaman uyumsuzluğu genellikle belirli bir iş parçacığı stratejisiyle ilişkili değildir.</span><span class="sxs-lookup"><span data-stu-id="412c5-293">Although F# provides some abilities to start an asynchronous computation on the current thread (or explicitly not on the current thread), asynchrony generally is not associated with a particular threading strategy.</span></span>

## <a name="see-also"></a><span data-ttu-id="412c5-294">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="412c5-294">See also</span></span>

- [<span data-ttu-id="412c5-295">F# Zaman uyumsuz programlama modeli</span><span class="sxs-lookup"><span data-stu-id="412c5-295">The F# Asynchronous Programming Model</span></span>](https://www.microsoft.com/research/publication/the-f-asynchronous-programming-model)
- [<span data-ttu-id="412c5-296">Jet. com F# zaman uyumsuz Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="412c5-296">Jet.com's F# Async Guide</span></span>](https://medium.com/jettech/f-async-guide-eb3c8a2d180a)
- [<span data-ttu-id="412c5-297">F#eğlenceli ve karın zaman uyumsuz programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="412c5-297">F# for fun and profit's Asynchronous Programming guide</span></span>](https://fsharpforfunandprofit.com/posts/concurrency-async-and-parallel/)
- [<span data-ttu-id="412c5-298">Ve F#içinde C# zaman uyumsuz: içinde zaman uyumsuz tuzaklarıC#</span><span class="sxs-lookup"><span data-stu-id="412c5-298">Async in C# and F#: Asynchronous gotchas in C#</span></span>](http://tomasp.net/blog/csharp-async-gotchas.aspx/)
