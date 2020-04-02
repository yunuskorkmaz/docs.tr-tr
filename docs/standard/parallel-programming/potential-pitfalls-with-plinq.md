---
title: PLINQ ile potansiyel tuzaklar
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, pitfalls
ms.assetid: 75a38b55-4bc4-488a-87d5-89dbdbdc76a2
ms.openlocfilehash: 44f40d6caad9187376a790f9a0ed09e22c861e37
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588596"
---
# <a name="potential-pitfalls-with-plinq"></a><span data-ttu-id="a1196-102">PLINQ ile potansiyel tuzaklar</span><span class="sxs-lookup"><span data-stu-id="a1196-102">Potential pitfalls with PLINQ</span></span>

<span data-ttu-id="a1196-103">Çoğu durumda PLINQ, nesnelere sıralı LINQ üzerinden önemli performans iyileştirmeleri sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="a1196-103">In many cases, PLINQ can provide significant performance improvements over sequential LINQ to Objects queries.</span></span> <span data-ttu-id="a1196-104">Ancak, sorgu yürütme paralelleştirme çalışması, sıralı kod olarak, ortak olmayan veya hiç karşılaşılan sorunlara yol açabilir karmaşıklığı tanıtır.</span><span class="sxs-lookup"><span data-stu-id="a1196-104">However, the work of parallelizing the query execution introduces complexity that can lead to problems that, in sequential code, are not as common or are not encountered at all.</span></span> <span data-ttu-id="a1196-105">Bu konu, PLINQ sorguları yazarken kaçınılması gereken bazı uygulamaları listeler.</span><span class="sxs-lookup"><span data-stu-id="a1196-105">This topic lists some practices to avoid when you write PLINQ queries.</span></span>

## <a name="dont-assume-that-parallel-is-always-faster"></a><span data-ttu-id="a1196-106">Paralelin her zaman daha hızlı olduğunu düşünmeyin</span><span class="sxs-lookup"><span data-stu-id="a1196-106">Don't assume that parallel is always faster</span></span>

<span data-ttu-id="a1196-107">Paralelleştirme bazen bir PLINQ sorgusunun LINQ'dan Nesnelere eşdeğerinden daha yavaş çalışmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="a1196-107">Parallelization sometimes causes a PLINQ query to run slower than its LINQ to Objects equivalent.</span></span> <span data-ttu-id="a1196-108">Başparmak temel kuralı, az kaynak öğeleri ve hızlı kullanıcı temsilcileri olan sorguları çok hızlandırmak olası değildir.</span><span class="sxs-lookup"><span data-stu-id="a1196-108">The basic rule of thumb is that queries that have few source elements and fast user delegates are unlikely to speedup much.</span></span> <span data-ttu-id="a1196-109">Ancak, performansta birçok etken söz konusu olduğundan, PLINQ'u kullanıp kullanmamaya karar vermeden önce gerçek sonuçları ölçmenizi öneririz.</span><span class="sxs-lookup"><span data-stu-id="a1196-109">However, because many factors are involved in performance, we recommend that you measure actual results before you decide whether to use PLINQ.</span></span> <span data-ttu-id="a1196-110">Daha fazla bilgi için [PLINQ'da Çabuk'u Anlama'ya](understanding-speedup-in-plinq.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="a1196-110">For more information, see [Understanding Speedup in PLINQ](understanding-speedup-in-plinq.md).</span></span>

## <a name="avoid-writing-to-shared-memory-locations"></a><span data-ttu-id="a1196-111">Paylaşılan bellek konumlarına yazmaktan kaçının</span><span class="sxs-lookup"><span data-stu-id="a1196-111">Avoid writing to shared memory locations</span></span>

<span data-ttu-id="a1196-112">Sıralı kodda, statik değişkenlerden veya sınıf alanlarına okumak veya yazmak nadir değildir.</span><span class="sxs-lookup"><span data-stu-id="a1196-112">In sequential code, it is not uncommon to read from or write to static variables or class fields.</span></span> <span data-ttu-id="a1196-113">Ancak, birden çok iş parçacığı aynı anda bu tür değişkenlere erişiyorsa, yarış koşulları için büyük bir potansiyel vardır.</span><span class="sxs-lookup"><span data-stu-id="a1196-113">However, whenever multiple threads are accessing such variables concurrently, there is a big potential for race conditions.</span></span> <span data-ttu-id="a1196-114">Değişkene erişimi eşitlemek için kilitleri kullanabiliyor olsanız da, eşitleme maliyeti performansa zarar verebilir.</span><span class="sxs-lookup"><span data-stu-id="a1196-114">Even though you can use locks to synchronize access to the variable, the cost of synchronization can hurt performance.</span></span> <span data-ttu-id="a1196-115">Bu nedenle, plinq sorgusunda paylaşılan duruma erişimi mümkün olduğunca önlemenizi veya en azından sınırlamanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="a1196-115">Therefore, we recommend that you avoid, or at least limit, access to shared state in a PLINQ query as much as possible.</span></span>

## <a name="avoid-over-parallelization"></a><span data-ttu-id="a1196-116">Aşırı paralelleştirmeden kaçının</span><span class="sxs-lookup"><span data-stu-id="a1196-116">Avoid over-parallelization</span></span>

<span data-ttu-id="a1196-117">`AsParallel` Yöntemi kullanarak, kaynak koleksiyonunu bölümleme ve alt iş parçacıklarını eşitleme nin genel gider maliyetlerine maruz kalırsınız.</span><span class="sxs-lookup"><span data-stu-id="a1196-117">By using the `AsParallel` method, you incur the overhead costs of partitioning the source collection and synchronizing the worker threads.</span></span> <span data-ttu-id="a1196-118">Paralelleştirmenin yararları bilgisayardaki işlemci sayısıyla daha da sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="a1196-118">The benefits of parallelization are further limited by the number of processors on the computer.</span></span> <span data-ttu-id="a1196-119">Tek bir işlemcide birden çok işlemle bağlı iş parçacığı çalıştırılarak hız kazanılacak bir hız yoktur.</span><span class="sxs-lookup"><span data-stu-id="a1196-119">There is no speedup to be gained by running multiple compute-bound threads on just one processor.</span></span> <span data-ttu-id="a1196-120">Bu nedenle, bir sorguaşırı paralelleştirmemeye dikkat etmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="a1196-120">Therefore, you must be careful not to over-parallelize a query.</span></span>

<span data-ttu-id="a1196-121">Aşırı paralelleştirmenin gerçekleşebileceği en yaygın senaryo, aşağıdaki parçacıkta gösterildiği gibi iç içe dönük sorgularda dır.</span><span class="sxs-lookup"><span data-stu-id="a1196-121">The most common scenario in which over-parallelization can occur is in nested queries, as shown in the following snippet.</span></span>

[!code-csharp[PLINQ#20](~/samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#20)]
[!code-vb[PLINQ#20](~/samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#20)]

<span data-ttu-id="a1196-122">Bu durumda, aşağıdaki koşullardan biri veya birkaçı geçerli olmadıkça yalnızca dış veri kaynağını (müşterileri) paralelleştirmek en iyisidir:</span><span class="sxs-lookup"><span data-stu-id="a1196-122">In this case, it is best to parallelize only the outer data source (customers) unless one or more of the following conditions apply:</span></span>

- <span data-ttu-id="a1196-123">İç veri kaynağı (cust. Siparişler) çok uzun olduğu bilinmektedir.</span><span class="sxs-lookup"><span data-stu-id="a1196-123">The inner data source (cust.Orders) is known to be very long.</span></span>

- <span data-ttu-id="a1196-124">Her siparişte pahalı bir hesaplama gerçekleştiresiniz.</span><span class="sxs-lookup"><span data-stu-id="a1196-124">You are performing an expensive computation on each order.</span></span> <span data-ttu-id="a1196-125">(Örnekte gösterilen işlem pahalı değildir.)</span><span class="sxs-lookup"><span data-stu-id="a1196-125">(The operation shown in the example is not expensive.)</span></span>

- <span data-ttu-id="a1196-126">Hedef sistemde sorguyu paralelleştirerek üretilecek iş parçacığı sayısını işlemek için yeterli işlemciye sahip olduğu `cust.Orders`bilinmektedir.</span><span class="sxs-lookup"><span data-stu-id="a1196-126">The target system is known to have enough processors to handle the number of threads that will be produced by parallelizing the query on `cust.Orders`.</span></span>

<span data-ttu-id="a1196-127">Her durumda, en iyi sorgu şeklini belirlemenin en iyi yolu sınamak ve ölçmektir.</span><span class="sxs-lookup"><span data-stu-id="a1196-127">In all cases, the best way to determine the optimum query shape is to test and measure.</span></span> <span data-ttu-id="a1196-128">Daha fazla bilgi için [bkz: PLINQ Sorgu Performansını Ölçün.](../../../docs/standard/parallel-programming/how-to-measure-plinq-query-performance.md)</span><span class="sxs-lookup"><span data-stu-id="a1196-128">For more information, see [How to: Measure PLINQ Query Performance](../../../docs/standard/parallel-programming/how-to-measure-plinq-query-performance.md).</span></span>

## <a name="avoid-calls-to-non-thread-safe-methods"></a><span data-ttu-id="a1196-129">İş parçacığı güvenli olmayan yöntemlere yapılan çağrıları önlemek</span><span class="sxs-lookup"><span data-stu-id="a1196-129">Avoid calls to non-thread-safe methods</span></span>

<span data-ttu-id="a1196-130">PLINQ sorgusundan iş parçacığı güvenli olmayan örnek yöntemlerine yazma, programınızda algılanmayan veya görünmeyebilecek veri bozulmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="a1196-130">Writing to non-thread-safe instance methods from a PLINQ query can lead to data corruption which may or may not go undetected in your program.</span></span> <span data-ttu-id="a1196-131">Ayrıca özel durumlara yol açabilir.</span><span class="sxs-lookup"><span data-stu-id="a1196-131">It can also lead to exceptions.</span></span> <span data-ttu-id="a1196-132">Aşağıdaki örnekte, birden çok iş parçacığı aynı `FileStream.Write` anda, hangi sınıf tarafından desteklenmeyen yöntemi çağırmak için çalışıyor olacaktır.</span><span class="sxs-lookup"><span data-stu-id="a1196-132">In the following example, multiple threads would be attempting to call the `FileStream.Write` method simultaneously, which is not supported by the class.</span></span>

```vb
Dim fs As FileStream = File.OpenWrite(…)
a.AsParallel().Where(...).OrderBy(...).Select(...).ForAll(Sub(x) fs.Write(x))
```

```csharp
FileStream fs = File.OpenWrite(...);
a.AsParallel().Where(...).OrderBy(...).Select(...).ForAll(x => fs.Write(x));
```

## <a name="limit-calls-to-thread-safe-methods"></a><span data-ttu-id="a1196-133">Aramaları iş parçacığı için güvenli yöntemlerle sınırlandırın</span><span class="sxs-lookup"><span data-stu-id="a1196-133">Limit calls to thread-safe methods</span></span>

<span data-ttu-id="a1196-134">.NET Framework'deki statik yöntemlerin çoğu iş parçacığı açısından güvenlidir ve aynı anda birden çok iş parçacığından çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="a1196-134">Most static methods in the .NET Framework are thread-safe and can be called from multiple threads concurrently.</span></span> <span data-ttu-id="a1196-135">Ancak, bu gibi durumlarda bile, söz konusu eşitleme sorguda önemli yavaşlamaya neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="a1196-135">However, even in these cases, the synchronization involved can lead to significant slowdown in the query.</span></span>

> [!NOTE]
> <span data-ttu-id="a1196-136">Sorgularınıza bazı aramalar <xref:System.Console.WriteLine%2A> ekleyerek bunu kendiniz test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a1196-136">You can test for this yourself by inserting some calls to <xref:System.Console.WriteLine%2A> in your queries.</span></span> <span data-ttu-id="a1196-137">Bu yöntem belge örneklerinde gösteri amacıyla kullanılsa da, PLINQ sorgularında kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="a1196-137">Although this method is used in the documentation examples for demonstration purposes, do not use it in PLINQ queries.</span></span>

## <a name="avoid-unnecessary-ordering-operations"></a><span data-ttu-id="a1196-138">Gereksiz sipariş işlemlerinden kaçının</span><span class="sxs-lookup"><span data-stu-id="a1196-138">Avoid unnecessary ordering operations</span></span>

<span data-ttu-id="a1196-139">PLINQ bir sorguyu paralel olarak yürüttüğünde, kaynak sırasını aynı anda birden çok iş parçacığı üzerinde çalıştırılabilen bölümlere böler.</span><span class="sxs-lookup"><span data-stu-id="a1196-139">When PLINQ executes a query in parallel, it divides the source sequence into partitions that can be operated on concurrently on multiple threads.</span></span> <span data-ttu-id="a1196-140">Varsayılan olarak, bölümlerin işlendiği ve sonuçların teslim edildiği sıra öngörülebilir değildir (örneğin, `OrderBy`işleçler hariç).</span><span class="sxs-lookup"><span data-stu-id="a1196-140">By default, the order in which the partitions are processed and the results are delivered is not predictable (except for operators such as `OrderBy`).</span></span> <span data-ttu-id="a1196-141">PLINQ'a herhangi bir kaynak dizisinin sırasını korumasını emredebilirsiniz, ancak bunun performans üzerinde olumsuz bir etkisi vardır.</span><span class="sxs-lookup"><span data-stu-id="a1196-141">You can instruct PLINQ to preserve the ordering of any source sequence, but this has a negative impact on performance.</span></span> <span data-ttu-id="a1196-142">Mümkün olduğunda en iyi yöntem, sorguları sipariş korumasına güvenmemek için yapılandırmaktır.</span><span class="sxs-lookup"><span data-stu-id="a1196-142">The best practice, whenever possible, is to structure queries so that they do not rely on order preservation.</span></span> <span data-ttu-id="a1196-143">Daha fazla bilgi için [PLINQ'da Sipariş Koruma'ya](order-preservation-in-plinq.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="a1196-143">For more information, see [Order Preservation in PLINQ](order-preservation-in-plinq.md).</span></span>

## <a name="prefer-forall-to-foreach-when-it-is-possible"></a><span data-ttu-id="a1196-144">Mümkün olduğunda ForAll'ı ForEach'e tercih edin</span><span class="sxs-lookup"><span data-stu-id="a1196-144">Prefer ForAll to ForEach when it is possible</span></span>

<span data-ttu-id="a1196-145">PLINQ birden çok iş parçacığı üzerinde bir sorgu yürütür, sonuçları bir `foreach` döngüde (Visual Basic'te)`For Each` tüketirseniz, sorgu sonuçları tek bir iş parçacığında birleştirilmeli ve sayısallaştırıcı tarafından seri olarak erişilmelidir.</span><span class="sxs-lookup"><span data-stu-id="a1196-145">Although PLINQ executes a query on multiple threads, if you consume the results in a `foreach` loop (`For Each` in Visual Basic), then the query results must be merged back into one thread and accessed serially by the enumerator.</span></span> <span data-ttu-id="a1196-146">Bazı durumlarda, bu kaçınılmazdır; ancak, mümkün olduğunda, `ForAll` her iş parçacığının kendi sonuçlarını çıkarmasını sağlamak için yöntemi kullanın, örneğin, <xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a1196-146">In some cases, this is unavoidable; however, whenever possible, use the `ForAll` method to enable each thread to output its own results, for example, by writing to a thread-safe collection such as <xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="a1196-147">Aynı sorun <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a1196-147">The same issue applies to <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="a1196-148">Başka bir `source.AsParallel().Where().ForAll(...)` deyişle, şiddetle tercih `Parallel.ForEach(source.AsParallel().Where(), ...)`edilmelidir.</span><span class="sxs-lookup"><span data-stu-id="a1196-148">In other words, `source.AsParallel().Where().ForAll(...)` should be strongly preferred to `Parallel.ForEach(source.AsParallel().Where(), ...)`.</span></span>

## <a name="be-aware-of-thread-affinity-issues"></a><span data-ttu-id="a1196-149">İş parçacığı afiyeti sorunlarına dikkat edin</span><span class="sxs-lookup"><span data-stu-id="a1196-149">Be aware of thread affinity issues</span></span>

<span data-ttu-id="a1196-150">Bazı teknolojiler, örneğin, Tek İş Parçacığı Daire (STA) bileşenleri, Windows Formları ve Windows Presentation Foundation (WPF) için COM birlikte çalışabilirliği, belirli bir iş parçacığı üzerinde çalıştırmak için kod gerektiren iş parçacığı afinite kısıtlamaları uygular.</span><span class="sxs-lookup"><span data-stu-id="a1196-150">Some technologies, for example, COM interoperability for Single-Threaded Apartment (STA) components, Windows Forms, and Windows Presentation Foundation (WPF), impose thread affinity restrictions that require code to run on a specific thread.</span></span> <span data-ttu-id="a1196-151">Örneğin, hem Windows Formlarında hem de WPF'de, denetime yalnızca oluşturulduğu iş parçacığında erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="a1196-151">For example, in both Windows Forms and WPF, a control can only be accessed on the thread on which it was created.</span></span> <span data-ttu-id="a1196-152">PLINQ sorgusunda Windows Forms denetiminin paylaşılan durumuna erişmeye çalışırsanız, hata ayıklamada çalışıyorsanız bir özel durum yükseltilir.</span><span class="sxs-lookup"><span data-stu-id="a1196-152">If you try to access the shared state of a Windows Forms control in a PLINQ query, an exception is raised if you are running in the debugger.</span></span> <span data-ttu-id="a1196-153">(Bu ayar kapatılabilir.) Ancak, sorgunuz UI iş parçacığı nda tüketiliyorsa, `foreach` bu kod tek bir iş parçacığı üzerinde yürütüldettiği için sorgu sonuçlarını sayan döngüden denetime erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a1196-153">(This setting can be turned off.) However, if your query is consumed on the UI thread, then you can access the control from the `foreach` loop that enumerates the query results because that code executes on just one thread.</span></span>

## <a name="dont-assume-that-iterations-of-foreach-for-and-forall-always-execute-in-parallel"></a><span data-ttu-id="a1196-154">ForEach, For ve ForAll yinelemelerinin her zaman paralel olarak yürütüldettiğini düşünmeyin</span><span class="sxs-lookup"><span data-stu-id="a1196-154">Don't assume that iterations of ForEach, For, and ForAll always execute in parallel</span></span>

<span data-ttu-id="a1196-155">Bir <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>, veya <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> <xref:System.Linq.ParallelEnumerable.ForAll%2A> döngüdeki tek tek yinelemelerin ancak paralel olarak yürütülmesi gerekmediğini göz önünde bulundurmak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="a1196-155">It is important to keep in mind that individual iterations in a <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>, or <xref:System.Linq.ParallelEnumerable.ForAll%2A> loop may but do not have to execute in parallel.</span></span> <span data-ttu-id="a1196-156">Bu nedenle, yinelemelerin paralel yürütülmesi veya belirli bir sırada yinelemelerin yürütülmesi doğruluğa bağlı herhangi bir kod yazmaktan kaçınmalısınız.</span><span class="sxs-lookup"><span data-stu-id="a1196-156">Therefore, you should avoid writing any code that depends for correctness on parallel execution of iterations or on the execution of iterations in any particular order.</span></span>

<span data-ttu-id="a1196-157">Örneğin, bu kodun kilitlenme olasılığı yüksektir:</span><span class="sxs-lookup"><span data-stu-id="a1196-157">For example, this code is likely to deadlock:</span></span>

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

<span data-ttu-id="a1196-158">Bu örnekte, bir yineleme bir olay ayarlar ve diğer tüm yinelemeler olay üzerinde bekleyin.</span><span class="sxs-lookup"><span data-stu-id="a1196-158">In this example, one iteration sets an event, and all other iterations wait on the event.</span></span> <span data-ttu-id="a1196-159">Olay ayar yinelemesi tamamlanana kadar bekleyen yinelemelerin hiçbiri tamamlanamaz.</span><span class="sxs-lookup"><span data-stu-id="a1196-159">None of the waiting iterations can complete until the event-setting iteration has completed.</span></span> <span data-ttu-id="a1196-160">Ancak, olay ayar yinelemesi yürütme şansı olmadan önce, bekleyen yinelemeler paralel döngü yürütmek için kullanılan tüm iş parçacığı engellemek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="a1196-160">However, it is possible that the waiting iterations block all threads that are used to execute the parallel loop, before the event-setting iteration has had a chance to execute.</span></span> <span data-ttu-id="a1196-161">Bu bir kilitlenme yle sonuçlanır – olay ayar yinelemesi asla yürütülmeyecek ve bekleyen yinelemeler asla uyanmayacak.</span><span class="sxs-lookup"><span data-stu-id="a1196-161">This results in a deadlock – the event-setting iteration will never execute, and the waiting iterations will never wake up.</span></span>

<span data-ttu-id="a1196-162">Özellikle, paralel bir döngü bir yineleme ilerleme yapmak için döngü başka bir yineleme beklemek asla.</span><span class="sxs-lookup"><span data-stu-id="a1196-162">In particular, one iteration of a parallel loop should never wait on another iteration of the loop to make progress.</span></span> <span data-ttu-id="a1196-163">Paralel döngü yinelemeleri sırayla ancak ters sırada zamanlamaya karar verirse, bir kilitlenme oluşur.</span><span class="sxs-lookup"><span data-stu-id="a1196-163">If the parallel loop decides to schedule the iterations sequentially but in the opposite order, a deadlock will occur.</span></span>

## <a name="see-also"></a><span data-ttu-id="a1196-164">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a1196-164">See also</span></span>

- [<span data-ttu-id="a1196-165">Paralel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="a1196-165">Parallel LINQ (PLINQ)</span></span>](introduction-to-plinq.md)
