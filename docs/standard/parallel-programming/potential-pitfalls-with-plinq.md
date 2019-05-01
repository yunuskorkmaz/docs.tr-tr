---
title: PLINQ'te Olası Tuzaklar
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, pitfalls
ms.assetid: 75a38b55-4bc4-488a-87d5-89dbdbdc76a2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2b996b09ed3973125d4d848d5e00c18ab02a6967
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61908719"
---
# <a name="potential-pitfalls-with-plinq"></a><span data-ttu-id="c5d07-102">PLINQ'te Olası Tuzaklar</span><span class="sxs-lookup"><span data-stu-id="c5d07-102">Potential Pitfalls with PLINQ</span></span>

<span data-ttu-id="c5d07-103">Çoğu durumda, PLINQ, sıralı LINQ-Plınq sorgularının üzerinde önemli performans geliştirmeleri sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="c5d07-103">In many cases, PLINQ can provide significant performance improvements over sequential LINQ to Objects queries.</span></span> <span data-ttu-id="c5d07-104">Ancak, paralel sorgu yürütme işi, sıralı kodda olarak genel olmayan ya da hiç karşılaşılan değil sorunlara yol açabilecek daha karmaşık hâle getirir.</span><span class="sxs-lookup"><span data-stu-id="c5d07-104">However, the work of parallelizing the query execution introduces complexity that can lead to problems that, in sequential code, are not as common or are not encountered at all.</span></span> <span data-ttu-id="c5d07-105">Bu konuda, PLINQ sorguları yazarken önlemek için bazı yöntemler listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="c5d07-105">This topic lists some practices to avoid when you write PLINQ queries.</span></span>

## <a name="do-not-assume-that-parallel-is-always-faster"></a><span data-ttu-id="c5d07-106">Paralel her zaman daha hızlı olan varsaymayın</span><span class="sxs-lookup"><span data-stu-id="c5d07-106">Do Not Assume That Parallel Is Always Faster</span></span>

<span data-ttu-id="c5d07-107">Bazen paralelleştirme bir PLINQ sorgusu nesneleri eşdeğer kendi LINQ göre daha yavaş çalışmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="c5d07-107">Parallelization sometimes causes a PLINQ query to run slower than its LINQ to Objects equivalent.</span></span> <span data-ttu-id="c5d07-108">Temel birkaç kaynak öğeleri ve Hızlı Kullanıcı temsilcileri sorguları çok hızlandırmayı için olası udur.</span><span class="sxs-lookup"><span data-stu-id="c5d07-108">The basic rule of thumb is that queries that have few source elements and fast user delegates are unlikely to speedup much.</span></span> <span data-ttu-id="c5d07-109">Ancak, birçok faktöre performans katılan olduğundan, PLINQ kullanıp kullanmayacağınızı karar vermeden önce gerçek sonuçlar ölçmek öneririz.</span><span class="sxs-lookup"><span data-stu-id="c5d07-109">However, because many factors are involved in performance, we recommend that you measure actual results before you decide whether to use PLINQ.</span></span> <span data-ttu-id="c5d07-110">Daha fazla bilgi için [plınq'te hızlandırmayı anlama](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="c5d07-110">For more information, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>

## <a name="avoid-writing-to-shared-memory-locations"></a><span data-ttu-id="c5d07-111">Paylaşılan bellek konumlarına yazılmasını kaçının</span><span class="sxs-lookup"><span data-stu-id="c5d07-111">Avoid Writing to Shared Memory Locations</span></span>

<span data-ttu-id="c5d07-112">Sıralı kodda, okuma veya yazma statik değişkenler veya sınıf alanlar için yaygın görülen değil.</span><span class="sxs-lookup"><span data-stu-id="c5d07-112">In sequential code, it is not uncommon to read from or write to static variables or class fields.</span></span> <span data-ttu-id="c5d07-113">Ancak, birden çok iş parçacığı gibi değişkenleri eriştiği her seferde, büyük bir olası yarış durumlarını yoktur.</span><span class="sxs-lookup"><span data-stu-id="c5d07-113">However, whenever multiple threads are accessing such variables concurrently, there is a big potential for race conditions.</span></span> <span data-ttu-id="c5d07-114">Değişkene erişimi eşitlemek için kilit kullanabilirsiniz, ancak eşitleme maliyetini performansı olumsuz etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="c5d07-114">Even though you can use locks to synchronize access to the variable, the cost of synchronization can hurt performance.</span></span> <span data-ttu-id="c5d07-115">Bu nedenle, öneririz, kaçının, veya en az sınırlamak, paylaşılan erişimi mümkün olduğunca bir PLINQ sorgusu durumda olmadığını.</span><span class="sxs-lookup"><span data-stu-id="c5d07-115">Therefore, we recommend that you avoid, or at least limit, access to shared state in a PLINQ query as much as possible.</span></span>

## <a name="avoid-over-parallelization"></a><span data-ttu-id="c5d07-116">Aşırı Paralelleştirme kaçının</span><span class="sxs-lookup"><span data-stu-id="c5d07-116">Avoid Over-Parallelization</span></span>

<span data-ttu-id="c5d07-117">Kullanarak `AsParallel` işleci, kaynak koleksiyonu bölümleme ve çalışan iş parçacığı eşitleme yüksek maliyetleri doğurur.</span><span class="sxs-lookup"><span data-stu-id="c5d07-117">By using the `AsParallel` operator, you incur the overhead costs of partitioning the source collection and synchronizing the worker threads.</span></span> <span data-ttu-id="c5d07-118">Paralelleştirme avantajlarını daha fazla bilgisayara işlemci sayısı sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="c5d07-118">The benefits of parallelization are further limited by the number of processors on the computer.</span></span> <span data-ttu-id="c5d07-119">Tek bir işlemci üzerinde birden fazla hesaplama bağlantılı iş parçacığı çalıştırarak kazanılacak hiçbir hızlandırmayı yoktur.</span><span class="sxs-lookup"><span data-stu-id="c5d07-119">There is no speedup to be gained by running multiple compute-bound threads on just one processor.</span></span> <span data-ttu-id="c5d07-120">Bu nedenle, bir sorguyu aşırı paralel olmayan dikkatli olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c5d07-120">Therefore, you must be careful not to over-parallelize a query.</span></span>

<span data-ttu-id="c5d07-121">En yaygın senaryoda hangi aşırı paralelleştirme oluşabilir iç içe geçmiş sorgularda aşağıdaki kod parçacığında gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="c5d07-121">The most common scenario in which over-parallelization can occur is in nested queries, as shown in the following snippet.</span></span>

[!code-csharp[PLINQ#20](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#20)]
[!code-vb[PLINQ#20](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#20)]

<span data-ttu-id="c5d07-122">Bu durumda, bir veya daha fazla aşağıdaki koşullardan biri uygulamadığınız sürece yalnızca dış veri kaynağı (müşteri) paralel hale getirmek idealdir:</span><span class="sxs-lookup"><span data-stu-id="c5d07-122">In this case, it is best to parallelize only the outer data source (customers) unless one or more of the following conditions apply:</span></span>

- <span data-ttu-id="c5d07-123">İç veri kaynağı (müşteri. Siparişler) çok uzun olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="c5d07-123">The inner data source (cust.Orders) is known to be very long.</span></span>

- <span data-ttu-id="c5d07-124">Her bir order pahalı bir hesaplama yapıyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="c5d07-124">You are performing an expensive computation on each order.</span></span> <span data-ttu-id="c5d07-125">(Örnekte gösterilen işlemi pahalı değildir.)</span><span class="sxs-lookup"><span data-stu-id="c5d07-125">(The operation shown in the example is not expensive.)</span></span>

- <span data-ttu-id="c5d07-126">Hedef sistem üzerinde sorguyu paralelleştirmek tarafından üretilen iş parçacığı sayısını işlemek için yeterli işlemci sahip olduğu bilinmektedir `cust.Orders`.</span><span class="sxs-lookup"><span data-stu-id="c5d07-126">The target system is known to have enough processors to handle the number of threads that will be produced by parallelizing the query on `cust.Orders`.</span></span>

<span data-ttu-id="c5d07-127">Her durumda en iyi sorgu şeklini belirlemek için en iyi test ve ölçmek için yoludur.</span><span class="sxs-lookup"><span data-stu-id="c5d07-127">In all cases, the best way to determine the optimum query shape is to test and measure.</span></span> <span data-ttu-id="c5d07-128">Daha fazla bilgi için [nasıl yapılır: PLINQ sorgu performansını ölçme](../../../docs/standard/parallel-programming/how-to-measure-plinq-query-performance.md).</span><span class="sxs-lookup"><span data-stu-id="c5d07-128">For more information, see [How to: Measure PLINQ Query Performance](../../../docs/standard/parallel-programming/how-to-measure-plinq-query-performance.md).</span></span>

## <a name="avoid-calls-to-non-thread-safe-methods"></a><span data-ttu-id="c5d07-129">İş parçacığı güvenli olmayan yöntemlere yapılan çağrılar kaçının</span><span class="sxs-lookup"><span data-stu-id="c5d07-129">Avoid Calls to Non-Thread-Safe Methods</span></span>

<span data-ttu-id="c5d07-130">İş parçacığı güvenli olmayan örnek yöntemleri için bir PLINQ yazma sorgu programınızda saptanamayabilir değil veya verilerin bozulmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="c5d07-130">Writing to non-thread-safe instance methods from a PLINQ query can lead to data corruption which may or may not go undetected in your program.</span></span> <span data-ttu-id="c5d07-131">Özel durumlar da neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="c5d07-131">It can also lead to exceptions.</span></span> <span data-ttu-id="c5d07-132">Aşağıdaki örnekte, birden çok iş parçacığı çağrı çalışıyor `FileStream.Write` yöntemi, aynı anda sınıfı tarafından desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="c5d07-132">In the following example, multiple threads would be attempting to call the `FileStream.Write` method simultaneously, which is not supported by the class.</span></span>

```vb
Dim fs As FileStream = File.OpenWrite(…)
a.AsParallel().Where(...).OrderBy(...).Select(...).ForAll(Sub(x) fs.Write(x))
```

```csharp
FileStream fs = File.OpenWrite(...);
a.AsParallel().Where(...).OrderBy(...).Select(...).ForAll(x => fs.Write(x));
```

## <a name="limit-calls-to-thread-safe-methods"></a><span data-ttu-id="c5d07-133">İş parçacığı açısından güvenli yöntemlere yapılan çağrılar sınırı</span><span class="sxs-lookup"><span data-stu-id="c5d07-133">Limit Calls to Thread-Safe Methods</span></span>

<span data-ttu-id="c5d07-134">.NET Framework'teki en statik yöntemler iş parçacığı bakımından güvenlidir ve aynı anda birden fazla iş parçacığından çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="c5d07-134">Most static methods in the .NET Framework are thread-safe and can be called from multiple threads concurrently.</span></span> <span data-ttu-id="c5d07-135">Ancak bu durumlarda bile ilgili eşitleme sorgu önemli yol açabilir.</span><span class="sxs-lookup"><span data-stu-id="c5d07-135">However, even in these cases, the synchronization involved can lead to significant slowdown in the query.</span></span>

> [!NOTE]
> <span data-ttu-id="c5d07-136">Bunun için kendiniz bazı çağrıları ekleyerek test edebilirsiniz <xref:System.Console.WriteLine%2A> sorgularınızı içinde.</span><span class="sxs-lookup"><span data-stu-id="c5d07-136">You can test for this yourself by inserting some calls to <xref:System.Console.WriteLine%2A> in your queries.</span></span> <span data-ttu-id="c5d07-137">Bu yöntem belgeleri örneklerde tanıtım amacıyla kullanılsa da PLINQ sorguları kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="c5d07-137">Although this method is used in the documentation examples for demonstration purposes, do not use it in PLINQ queries.</span></span>

## <a name="avoid-unnecessary-ordering-operations"></a><span data-ttu-id="c5d07-138">Gereksiz sıralama işlemlerden kaçının</span><span class="sxs-lookup"><span data-stu-id="c5d07-138">Avoid Unnecessary Ordering Operations</span></span>

<span data-ttu-id="c5d07-139">PLINQ'nun bir sorguyu paralel olarak yürütüldüğünde, kaynak sırası birden çok iş parçacığı üzerinde eşzamanlı olarak üzerinde işletilebilir bölümlere böler.</span><span class="sxs-lookup"><span data-stu-id="c5d07-139">When PLINQ executes a query in parallel, it divides the source sequence into partitions that can be operated on concurrently on multiple threads.</span></span> <span data-ttu-id="c5d07-140">Varsayılan olarak, bölümleri işlenir ve sonuçlarının teslim edildiği sıra tahmin edilebilir değildir (işleçler gibi dışında `OrderBy`).</span><span class="sxs-lookup"><span data-stu-id="c5d07-140">By default, the order in which the partitions are processed and the results are delivered is not predictable (except for operators such as `OrderBy`).</span></span> <span data-ttu-id="c5d07-141">PLINQ'nun kaynak dizi sıralamasını korumak için bildirebilirsiniz, ancak bu performansı üzerinde olumsuz bir etkiye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="c5d07-141">You can instruct PLINQ to preserve the ordering of any source sequence, but this has a negative impact on performance.</span></span> <span data-ttu-id="c5d07-142">Sıra koruması üzerinde güvenmeyin en iyi uygulama, mümkün olduğunda, yapısı sorguları, böylelikle.</span><span class="sxs-lookup"><span data-stu-id="c5d07-142">The best practice, whenever possible, is to structure queries so that they do not rely on order preservation.</span></span> <span data-ttu-id="c5d07-143">Daha fazla bilgi için [plınq'te sıra koruma](../../../docs/standard/parallel-programming/order-preservation-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="c5d07-143">For more information, see [Order Preservation in PLINQ](../../../docs/standard/parallel-programming/order-preservation-in-plinq.md).</span></span>

## <a name="prefer-forall-to-foreach-when-it-is-possible"></a><span data-ttu-id="c5d07-144">ForAll ForEach olduğunda mümkündür için tercih et</span><span class="sxs-lookup"><span data-stu-id="c5d07-144">Prefer ForAll to ForEach When It Is Possible</span></span>

<span data-ttu-id="c5d07-145">Sonuçlarda kazanabilirsiniz PLINQ sorgu birden çok iş parçacığında yürütülür. ancak bir `foreach` döngü (`For Each` Visual Basic'te), sorgu sonuçlarını bir akışına birleştirilir ve seri olarak numaralandırıcı tarafından erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="c5d07-145">Although PLINQ executes a query on multiple threads, if you consume the results in a `foreach` loop (`For Each` in Visual Basic), then the query results must be merged back into one thread and accessed serially by the enumerator.</span></span> <span data-ttu-id="c5d07-146">Bazı durumlarda, kaçınılmaz budur; Ancak, mümkün olduğunda kullanın `ForAll` kendi sonuçları, örneğin, bir iş parçacığı güvenli koleksiyonu yazarak çıktısını almak her bir iş parçacığı etkinleştirmek için yöntemi <xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c5d07-146">In some cases, this is unavoidable; however, whenever possible, use the `ForAll` method to enable each thread to output its own results, for example, by writing to a thread-safe collection such as <xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="c5d07-147">Aynı sorunu uygulandığı <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> başka bir deyişle, `source.AsParallel().Where().ForAll(...)` kesin tercih edilmelidir</span><span class="sxs-lookup"><span data-stu-id="c5d07-147">The same issue applies to <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> In other words, `source.AsParallel().Where().ForAll(...)` should be strongly preferred to</span></span>

<span data-ttu-id="c5d07-148">`Parallel.ForEach(source.AsParallel().Where(), ...)`.</span><span class="sxs-lookup"><span data-stu-id="c5d07-148">`Parallel.ForEach(source.AsParallel().Where(), ...)`.</span></span>

## <a name="be-aware-of-thread-affinity-issues"></a><span data-ttu-id="c5d07-149">İş parçacığı benzeşimini sorunlarından haberdar olmalı</span><span class="sxs-lookup"><span data-stu-id="c5d07-149">Be Aware of Thread Affinity Issues</span></span>

<span data-ttu-id="c5d07-150">Örneğin, COM birlikte çalışabilirliği Single-Threaded grubu (STA) bileşenler, Windows Forms ve Windows Presentation Foundation (WPF) için bazı teknolojiler belirli bir iş parçacığı üzerinde çalıştırılacak kodu gerektiren iş parçacığı benzeşimini kısıtlamaları dayatır.</span><span class="sxs-lookup"><span data-stu-id="c5d07-150">Some technologies, for example, COM interoperability for Single-Threaded Apartment (STA) components, Windows Forms, and Windows Presentation Foundation (WPF), impose thread affinity restrictions that require code to run on a specific thread.</span></span> <span data-ttu-id="c5d07-151">Örneğin, Windows Forms ve WPF bir denetim yalnızca üzerinde oluşturulmuş iş parçacığı üzerinde erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="c5d07-151">For example, in both Windows Forms and WPF, a control can only be accessed on the thread on which it was created.</span></span> <span data-ttu-id="c5d07-152">Paylaşılan bir PLINQ sorgusu Windows Forms denetiminde durumunu erişmeye çalışırsanız, hata ayıklayıcıda çalıştırıyorsanız bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="c5d07-152">If you try to access the shared state of a Windows Forms control in a PLINQ query, an exception is raised if you are running in the debugger.</span></span> <span data-ttu-id="c5d07-153">(Bu ayar kapatılabilir.) Sorgunuzu UI iş parçacığı üzerinde kullanılır, ancak ardından denetiminden erişebilirsiniz `foreach` sorgu listesini numaralandıran bir döngüye neden olur çünkü bu kod yalnızca bir iş parçacığında yürütülür.</span><span class="sxs-lookup"><span data-stu-id="c5d07-153">(This setting can be turned off.) However, if your query is consumed on the UI thread, then you can access the control from the `foreach` loop that enumerates the query results because that code executes on just one thread.</span></span>

## <a name="do-not-assume-that-iterations-of-foreach-for-and-forall-always-execute-in-parallel"></a><span data-ttu-id="c5d07-154">Değil varsayılır, ForEach, yinelemeleri için ve ForAll her zaman Paralel yürütme</span><span class="sxs-lookup"><span data-stu-id="c5d07-154">Do Not Assume that Iterations of ForEach, For and ForAll Always Execute in Parallel</span></span>

<span data-ttu-id="c5d07-155">Bu tek tek yinelemelerde göz önünde bulundurmanız önemlidir bir <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> veya <xref:System.Linq.ParallelEnumerable.ForAll%2A> döngü Mayıs ancak paralel olarak yürütmek izniniz yok.</span><span class="sxs-lookup"><span data-stu-id="c5d07-155">It is important to keep in mind that individual iterations in a <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> or <xref:System.Linq.ParallelEnumerable.ForAll%2A> loop may but do not have to execute in parallel.</span></span> <span data-ttu-id="c5d07-156">Bu nedenle, yinelemelerin Paralel yürütme ya da yineleme herhangi bir sırayla yürütülmesi doğruluğu bağlıdır herhangi bir kod yazmadan kaçınmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c5d07-156">Therefore, you should avoid writing any code that depends for correctness on parallel execution of iterations or on the execution of iterations in any particular order.</span></span>

<span data-ttu-id="c5d07-157">Örneğin, bu kodu kilitlenme olasılığı bulunur:</span><span class="sxs-lookup"><span data-stu-id="c5d07-157">For example, this code is likely to deadlock:</span></span>

```vb
Dim mre = New ManualResetEventSlim()
Enumerable.Range(0, Environment.ProcessorCount * 100).AsParallel().ForAll(Sub(j)
   If j = Environment.ProcessorCount Then
       Console.WriteLine("Set on {0} with value of {1}", Thread.CurrentThread.ManagedThreadId, j)
       mre.Set()
   Else
       Console.WriteLine("Waiting on {0} with value of {1}", Thread.CurrentThread.ManagedThreadId, j)
       mre.Wait()
   End If
End Sub) ' deadlocks
```

```csharp
ManualResetEventSlim mre = new ManualResetEventSlim();
Enumerable.Range(0, Environment.ProcessorCount * 100).AsParallel().ForAll((j) =>
{
    if (j == Environment.ProcessorCount)
    {
        Console.WriteLine("Set on {0} with value of {1}", Thread.CurrentThread.ManagedThreadId, j);
        mre.Set();
    }
    else
    {
        Console.WriteLine("Waiting on {0} with value of {1}", Thread.CurrentThread.ManagedThreadId, j);
        mre.Wait();
    }
}); //deadlocks
```

<span data-ttu-id="c5d07-158">Bu örnekte, bir olay bir yineleme ayarlar ve diğer tüm yinelemeleri olay üzerinde bekleyin.</span><span class="sxs-lookup"><span data-stu-id="c5d07-158">In this example, one iteration sets an event, and all other iterations wait on the event.</span></span> <span data-ttu-id="c5d07-159">Olay ayarı yineleme tamamlanmasını bekleme yinelemeleri hiçbiri tamamlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c5d07-159">None of the waiting iterations can complete until the event-setting iteration has completed.</span></span> <span data-ttu-id="c5d07-160">Ancak, bekleme yinelemeleri önce olay ayarı yineleme yürütmek için bir fırsat paralel bir döngüden yürütmek için kullanılan tüm iş parçacıklarının block mümkündür.</span><span class="sxs-lookup"><span data-stu-id="c5d07-160">However, it is possible that the waiting iterations block all threads that are used to execute the parallel loop, before the event-setting iteration has had a chance to execute.</span></span> <span data-ttu-id="c5d07-161">Bu bir kilitlenmeyle sonuçlanır: olay ayarı yineleme hiçbir zaman yürütülür ve bekleme yinelemeler hiç uyandıracağına.</span><span class="sxs-lookup"><span data-stu-id="c5d07-161">This results in a deadlock – the event-setting iteration will never execute, and the waiting iterations will never wake up.</span></span>

<span data-ttu-id="c5d07-162">Özellikle, bir yineleme, paralel bir döngüden hiçbir zaman başka bir döngü ilerleme beklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="c5d07-162">In particular, one iteration of a parallel loop should never wait on another iteration of the loop to make progress.</span></span> <span data-ttu-id="c5d07-163">Yinelemeleri ardışık olarak ancak ters sırada zamanlamak paralel bir döngüden karar verirse, karşılıklı bir kilitlenme ortaya çıkar.</span><span class="sxs-lookup"><span data-stu-id="c5d07-163">If the parallel loop decides to schedule the iterations sequentially but in the opposite order, a deadlock will occur.</span></span>

## <a name="see-also"></a><span data-ttu-id="c5d07-164">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c5d07-164">See also</span></span>

- [<span data-ttu-id="c5d07-165">Paralel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="c5d07-165">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
