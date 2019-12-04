---
title: PLıNQ ile olası tehlikeli
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, pitfalls
ms.assetid: 75a38b55-4bc4-488a-87d5-89dbdbdc76a2
ms.openlocfilehash: 3ddc0c013335e6a7b4708a5dd8be0b2247b2f60c
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716248"
---
# <a name="potential-pitfalls-with-plinq"></a><span data-ttu-id="f5147-102">PLıNQ ile olası tehlikeli</span><span class="sxs-lookup"><span data-stu-id="f5147-102">Potential pitfalls with PLINQ</span></span>

<span data-ttu-id="f5147-103">Birçok durumda PLıNQ, sıralı LINQ to Objects sorguları üzerinde önemli performans geliştirmeleri sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="f5147-103">In many cases, PLINQ can provide significant performance improvements over sequential LINQ to Objects queries.</span></span> <span data-ttu-id="f5147-104">Ancak, sorgu yürütmeyi paralelleştirme işi, ardışık kodda yaygın olmayan veya hiç karşılaşılmayan sorunlara yol açabilecek karmaşıklığa neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="f5147-104">However, the work of parallelizing the query execution introduces complexity that can lead to problems that, in sequential code, are not as common or are not encountered at all.</span></span> <span data-ttu-id="f5147-105">Bu konu başlığı altında, PLıNQ sorgularını yazarken kaçınılacak bazı yöntemler listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="f5147-105">This topic lists some practices to avoid when you write PLINQ queries.</span></span>

## <a name="dont-assume-that-parallel-is-always-faster"></a><span data-ttu-id="f5147-106">Parallel öğesinin her zaman daha hızlı olduğunu varsaymayın</span><span class="sxs-lookup"><span data-stu-id="f5147-106">Don't assume that parallel is always faster</span></span>

<span data-ttu-id="f5147-107">Paralelleştirme bazen bir PLıNQ sorgusunun LINQ to Objects eşinden daha yavaş çalışmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="f5147-107">Parallelization sometimes causes a PLINQ query to run slower than its LINQ to Objects equivalent.</span></span> <span data-ttu-id="f5147-108">Thumb 'in temel kuralı, az sayıda kaynak öğe ve Hızlı Kullanıcı temsilcileri olan sorguların çok daha hızlı bir şekilde hızlanmasından düşüktür.</span><span class="sxs-lookup"><span data-stu-id="f5147-108">The basic rule of thumb is that queries that have few source elements and fast user delegates are unlikely to speedup much.</span></span> <span data-ttu-id="f5147-109">Ancak, birçok etken performansa dahil edildiğinden, PLıNQ kullanmaya karar vermeden önce gerçek sonuçları ölçmenizi öneririz.</span><span class="sxs-lookup"><span data-stu-id="f5147-109">However, because many factors are involved in performance, we recommend that you measure actual results before you decide whether to use PLINQ.</span></span> <span data-ttu-id="f5147-110">Daha fazla bilgi için bkz. [PLıNQ 'Te hızlı Hızlandırlamayı anlama](understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="f5147-110">For more information, see [Understanding Speedup in PLINQ](understanding-speedup-in-plinq.md).</span></span>

## <a name="avoid-writing-to-shared-memory-locations"></a><span data-ttu-id="f5147-111">Paylaşılan bellek konumlarına yazmayı önleyin</span><span class="sxs-lookup"><span data-stu-id="f5147-111">Avoid writing to shared memory locations</span></span>

<span data-ttu-id="f5147-112">Ardışık kodda, statik değişkenlerle veya sınıf alanlarından okumak veya yazmak yaygın olmayan bir durumdur.</span><span class="sxs-lookup"><span data-stu-id="f5147-112">In sequential code, it is not uncommon to read from or write to static variables or class fields.</span></span> <span data-ttu-id="f5147-113">Ancak, birden çok iş parçacığı bu tür değişkenlere eşzamanlı olarak eriştiği zaman, yarış koşullarında büyük bir olasılık vardır.</span><span class="sxs-lookup"><span data-stu-id="f5147-113">However, whenever multiple threads are accessing such variables concurrently, there is a big potential for race conditions.</span></span> <span data-ttu-id="f5147-114">Erişimi değişkene eşitlemek için kilitleri da kullanabilirsiniz, ancak eşitleme maliyeti performansı zarar verebilir.</span><span class="sxs-lookup"><span data-stu-id="f5147-114">Even though you can use locks to synchronize access to the variable, the cost of synchronization can hurt performance.</span></span> <span data-ttu-id="f5147-115">Bu nedenle, bir PLıNQ sorgusunda mümkün olduğunca, paylaşılan duruma erişimi önlemenize veya en azından sınırlamanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="f5147-115">Therefore, we recommend that you avoid, or at least limit, access to shared state in a PLINQ query as much as possible.</span></span>

## <a name="avoid-over-parallelization"></a><span data-ttu-id="f5147-116">Fazla paralelleştirme kullanmaktan kaçının</span><span class="sxs-lookup"><span data-stu-id="f5147-116">Avoid over-parallelization</span></span>

<span data-ttu-id="f5147-117">`AsParallel` yöntemi kullanılarak, kaynak koleksiyonun bölümlenmesi ve çalışan iş parçacıklarını eşitlemek için ek ücret maliyetlerine tabi olursunuz.</span><span class="sxs-lookup"><span data-stu-id="f5147-117">By using the `AsParallel` method, you incur the overhead costs of partitioning the source collection and synchronizing the worker threads.</span></span> <span data-ttu-id="f5147-118">Paralelleştirme avantajları, bilgisayardaki işlemci sayısıyla daha fazla sınırlandırılır.</span><span class="sxs-lookup"><span data-stu-id="f5147-118">The benefits of parallelization are further limited by the number of processors on the computer.</span></span> <span data-ttu-id="f5147-119">Yalnızca bir işlemcide birden çok işlem ile sınırlı iş parçacığı çalıştırılarak kazanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f5147-119">There is no speedup to be gained by running multiple compute-bound threads on just one processor.</span></span> <span data-ttu-id="f5147-120">Bu nedenle, paralel hale getirmek bir sorgu üzerinde bulunmamaya dikkat etmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f5147-120">Therefore, you must be careful not to over-parallelize a query.</span></span>

<span data-ttu-id="f5147-121">Aşağıdaki kod parçacığında gösterildiği gibi, aşırı paralel hale getirme işleminin gerçekleşebileceği en yaygın senaryo iç içe sorgularda yer alabilir.</span><span class="sxs-lookup"><span data-stu-id="f5147-121">The most common scenario in which over-parallelization can occur is in nested queries, as shown in the following snippet.</span></span>

[!code-csharp[PLINQ#20](~/samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#20)]
[!code-vb[PLINQ#20](~/samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#20)]

<span data-ttu-id="f5147-122">Bu durumda, aşağıdaki koşullardan biri veya birkaçı geçerli olmadığı için yalnızca dış veri kaynağına (müşteriler) paralel hale getirmek en iyi seçenektir:</span><span class="sxs-lookup"><span data-stu-id="f5147-122">In this case, it is best to parallelize only the outer data source (customers) unless one or more of the following conditions apply:</span></span>

- <span data-ttu-id="f5147-123">İç veri kaynağı (Müşt. Siparişler) çok uzun olduğu bilinmektedir.</span><span class="sxs-lookup"><span data-stu-id="f5147-123">The inner data source (cust.Orders) is known to be very long.</span></span>

- <span data-ttu-id="f5147-124">Her sırada pahalı bir hesaplama gerçekleştirçalışıyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="f5147-124">You are performing an expensive computation on each order.</span></span> <span data-ttu-id="f5147-125">(Örnekte gösterilen işlem pahalı değildir.)</span><span class="sxs-lookup"><span data-stu-id="f5147-125">(The operation shown in the example is not expensive.)</span></span>

- <span data-ttu-id="f5147-126">Hedef sistemin, `cust.Orders`sorguyu paralelleştirerek üretilecek iş parçacığı sayısını işlemek için yeterli işlemcisi olduğu bilinmektedir.</span><span class="sxs-lookup"><span data-stu-id="f5147-126">The target system is known to have enough processors to handle the number of threads that will be produced by parallelizing the query on `cust.Orders`.</span></span>

<span data-ttu-id="f5147-127">Her durumda, en uygun sorgu şeklinin belirlenmesi için en iyi yol test ve ölçüdür.</span><span class="sxs-lookup"><span data-stu-id="f5147-127">In all cases, the best way to determine the optimum query shape is to test and measure.</span></span> <span data-ttu-id="f5147-128">Daha fazla bilgi için bkz. [nasıl yapılır: PLıNQ sorgu performansını ölçme](../../../docs/standard/parallel-programming/how-to-measure-plinq-query-performance.md).</span><span class="sxs-lookup"><span data-stu-id="f5147-128">For more information, see [How to: Measure PLINQ Query Performance](../../../docs/standard/parallel-programming/how-to-measure-plinq-query-performance.md).</span></span>

## <a name="avoid-calls-to-non-thread-safe-methods"></a><span data-ttu-id="f5147-129">İş parçacığı olmayan güvenli yöntemlere yapılan çağrılardan kaçının</span><span class="sxs-lookup"><span data-stu-id="f5147-129">Avoid calls to non-thread-safe methods</span></span>

<span data-ttu-id="f5147-130">Bir PLıNQ sorgusundan iş parçacığı açısından güvenli olmayan örnek yöntemlerine yazmak, programınızda algılanamayan veya algılanamayan veri bozulmasına yol açabilir.</span><span class="sxs-lookup"><span data-stu-id="f5147-130">Writing to non-thread-safe instance methods from a PLINQ query can lead to data corruption which may or may not go undetected in your program.</span></span> <span data-ttu-id="f5147-131">Ayrıca özel durumlara da yol açabilir.</span><span class="sxs-lookup"><span data-stu-id="f5147-131">It can also lead to exceptions.</span></span> <span data-ttu-id="f5147-132">Aşağıdaki örnekte, birden çok iş parçacığı, sınıf tarafından desteklenmeyen aynı anda `FileStream.Write` yöntemini çağırmaya çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="f5147-132">In the following example, multiple threads would be attempting to call the `FileStream.Write` method simultaneously, which is not supported by the class.</span></span>

```vb
Dim fs As FileStream = File.OpenWrite(…)
a.AsParallel().Where(...).OrderBy(...).Select(...).ForAll(Sub(x) fs.Write(x))
```

```csharp
FileStream fs = File.OpenWrite(...);
a.AsParallel().Where(...).OrderBy(...).Select(...).ForAll(x => fs.Write(x));
```

## <a name="limit-calls-to-thread-safe-methods"></a><span data-ttu-id="f5147-133">İş parçacığı güvenli yöntemleriyle yapılan çağrıları sınırlayın</span><span class="sxs-lookup"><span data-stu-id="f5147-133">Limit calls to thread-safe methods</span></span>

<span data-ttu-id="f5147-134">.NET Framework çoğu statik yöntem iş parçacığı açısından güvenlidir ve aynı anda birden çok iş parçacığından çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="f5147-134">Most static methods in the .NET Framework are thread-safe and can be called from multiple threads concurrently.</span></span> <span data-ttu-id="f5147-135">Ancak, bu durumlarda bile ilgili eşitleme, sorgudaki önemli yavaşlama oluşmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="f5147-135">However, even in these cases, the synchronization involved can lead to significant slowdown in the query.</span></span>

> [!NOTE]
> <span data-ttu-id="f5147-136">Sorgularınızdaki <xref:System.Console.WriteLine%2A> bazı çağrılar ekleyerek bunu kendiniz test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f5147-136">You can test for this yourself by inserting some calls to <xref:System.Console.WriteLine%2A> in your queries.</span></span> <span data-ttu-id="f5147-137">Bu yöntem, Gösterim amacıyla belge örneklerinde kullanılmasına karşın, bunu PLıNQ sorgularında kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="f5147-137">Although this method is used in the documentation examples for demonstration purposes, do not use it in PLINQ queries.</span></span>

## <a name="avoid-unnecessary-ordering-operations"></a><span data-ttu-id="f5147-138">Gereksiz sıralama işlemlerinden kaçının</span><span class="sxs-lookup"><span data-stu-id="f5147-138">Avoid unnecessary ordering operations</span></span>

<span data-ttu-id="f5147-139">PLıNQ bir sorguyu paralel olarak yürüttüğünde, kaynak diziyi birden çok iş parçacığında eşzamanlı olarak işletilebilir bölümlere böler.</span><span class="sxs-lookup"><span data-stu-id="f5147-139">When PLINQ executes a query in parallel, it divides the source sequence into partitions that can be operated on concurrently on multiple threads.</span></span> <span data-ttu-id="f5147-140">Varsayılan olarak, bölümlerin işlenme sırası ve sonuçlar teslim edilebilir değildir (örneğin, `OrderBy`gibi işleçler hariç).</span><span class="sxs-lookup"><span data-stu-id="f5147-140">By default, the order in which the partitions are processed and the results are delivered is not predictable (except for operators such as `OrderBy`).</span></span> <span data-ttu-id="f5147-141">PLıNQ ile herhangi bir kaynak dizinin sıralamasını koruyabilir, ancak bu performans üzerinde olumsuz bir etkiye sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="f5147-141">You can instruct PLINQ to preserve the ordering of any source sequence, but this has a negative impact on performance.</span></span> <span data-ttu-id="f5147-142">En iyi yöntem, mümkün olduğunda, sorgu siparişi saklama üzerine güvenmemesi için sorguları yapısal olarak kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="f5147-142">The best practice, whenever possible, is to structure queries so that they do not rely on order preservation.</span></span> <span data-ttu-id="f5147-143">Daha fazla bilgi için bkz. [PLıNQ 'Te sıra koruma](order-preservation-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="f5147-143">For more information, see [Order Preservation in PLINQ](order-preservation-in-plinq.md).</span></span>

## <a name="prefer-forall-to-foreach-when-it-is-possible"></a><span data-ttu-id="f5147-144">Bu mümkün olduğunda, ForAll öğesini ForEach olarak tercih et</span><span class="sxs-lookup"><span data-stu-id="f5147-144">Prefer ForAll to ForEach when it is possible</span></span>

<span data-ttu-id="f5147-145">PLıNQ birden çok iş parçacığında bir sorgu yürütüyordu, ancak sonuçları bir `foreach` döngüsünde (`For Each` Visual Basic) kullandıysanız, sorgu sonuçlarının bir iş parçacığında geri birleştirilmesi ve Numaralandırıcının seri hale getirilene erişilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="f5147-145">Although PLINQ executes a query on multiple threads, if you consume the results in a `foreach` loop (`For Each` in Visual Basic), then the query results must be merged back into one thread and accessed serially by the enumerator.</span></span> <span data-ttu-id="f5147-146">Bazı durumlarda bu durum kaçınılmaz; Ancak mümkün olduğunda, her bir iş parçacığının kendi sonuçlarını çıktısına (örneğin, <xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType>gibi iş parçacığı güvenli bir koleksiyona yazarak) izin vermek için `ForAll` yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="f5147-146">In some cases, this is unavoidable; however, whenever possible, use the `ForAll` method to enable each thread to output its own results, for example, by writing to a thread-safe collection such as <xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="f5147-147">Aynı sorun <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="f5147-147">The same issue applies to <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="f5147-148">Diğer bir deyişle, `Parallel.ForEach(source.AsParallel().Where(), ...)`için `source.AsParallel().Where().ForAll(...)` kesinlikle tercih edilmelidir.</span><span class="sxs-lookup"><span data-stu-id="f5147-148">In other words, `source.AsParallel().Where().ForAll(...)` should be strongly preferred to `Parallel.ForEach(source.AsParallel().Where(), ...)`.</span></span>

## <a name="be-aware-of-thread-affinity-issues"></a><span data-ttu-id="f5147-149">İş parçacığı benzeşim sorunlarından haberdar olun</span><span class="sxs-lookup"><span data-stu-id="f5147-149">Be aware of thread affinity issues</span></span>

<span data-ttu-id="f5147-150">Tek iş parçacıklı Apartment (STA) bileşenleri, Windows Forms ve Windows Presentation Foundation (WPF) için COM birlikte çalışabilirlik gibi bazı teknolojiler, kodun belirli bir iş parçacığında çalıştırılmasını gerektiren iş parçacığı benzeşim kısıtlamalarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="f5147-150">Some technologies, for example, COM interoperability for Single-Threaded Apartment (STA) components, Windows Forms, and Windows Presentation Foundation (WPF), impose thread affinity restrictions that require code to run on a specific thread.</span></span> <span data-ttu-id="f5147-151">Örneğin, hem Windows Forms hem de WPF 'de, bir denetime yalnızca oluşturulduğu iş parçacığında erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="f5147-151">For example, in both Windows Forms and WPF, a control can only be accessed on the thread on which it was created.</span></span> <span data-ttu-id="f5147-152">Bir PLıNQ sorgusunda Windows Forms denetiminin paylaşılan durumuna erişmeye çalışırsanız, hata ayıklayıcıda çalıştırıyorsanız bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="f5147-152">If you try to access the shared state of a Windows Forms control in a PLINQ query, an exception is raised if you are running in the debugger.</span></span> <span data-ttu-id="f5147-153">(Bu ayar kapatılabilir.) Ancak, Sorgunuz UI iş parçacığında kullanılıyorsa, bu kod yalnızca bir iş parçacığında yürütüldüğü için sorgu sonuçlarını numaralandırır `foreach` döngüsünden denetime erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f5147-153">(This setting can be turned off.) However, if your query is consumed on the UI thread, then you can access the control from the `foreach` loop that enumerates the query results because that code executes on just one thread.</span></span>

## <a name="dont-assume-that-iterations-of-foreach-for-and-forall-always-execute-in-parallel"></a><span data-ttu-id="f5147-154">ForEach, for ve ForAll yinelemelerinin her zaman paralel olarak yürütüleceğini varsayın</span><span class="sxs-lookup"><span data-stu-id="f5147-154">Don't assume that iterations of ForEach, For, and ForAll always execute in parallel</span></span>

<span data-ttu-id="f5147-155"><xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>veya <xref:System.Linq.ParallelEnumerable.ForAll%2A> döngüsündeki tek tek yinelemelerin, ancak paralel olarak yürütülmesi gerekmez olduğunu göz önünde bulundurmanız önemlidir.</span><span class="sxs-lookup"><span data-stu-id="f5147-155">It is important to keep in mind that individual iterations in a <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>, or <xref:System.Linq.ParallelEnumerable.ForAll%2A> loop may but do not have to execute in parallel.</span></span> <span data-ttu-id="f5147-156">Bu nedenle, tekrarların paralel olarak yürütülmesi veya yinelemeler üzerinde herhangi bir sıraya göre yürütülmesi açısından doğruluğu için herhangi bir kod yazmadan kaçınmalısınız.</span><span class="sxs-lookup"><span data-stu-id="f5147-156">Therefore, you should avoid writing any code that depends for correctness on parallel execution of iterations or on the execution of iterations in any particular order.</span></span>

<span data-ttu-id="f5147-157">Örneğin, bu kodun kilitlenmesi olasıdır:</span><span class="sxs-lookup"><span data-stu-id="f5147-157">For example, this code is likely to deadlock:</span></span>

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

<span data-ttu-id="f5147-158">Bu örnekte, bir yineleme bir olay ayarlıyor ve diğer tüm yinelemeler olayda bekler.</span><span class="sxs-lookup"><span data-stu-id="f5147-158">In this example, one iteration sets an event, and all other iterations wait on the event.</span></span> <span data-ttu-id="f5147-159">Olay ayarı yinelemesi tamamlanana kadar bekleyen yinelemeden hiçbiri tamamlanamaz.</span><span class="sxs-lookup"><span data-stu-id="f5147-159">None of the waiting iterations can complete until the event-setting iteration has completed.</span></span> <span data-ttu-id="f5147-160">Ancak, bekleyen yinelemeler, olay ayarı yinelemesi yürütme şansı vermeden önce paralel döngüyü yürütmek için kullanılan tüm iş parçacıklarını engelliyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="f5147-160">However, it is possible that the waiting iterations block all threads that are used to execute the parallel loop, before the event-setting iteration has had a chance to execute.</span></span> <span data-ttu-id="f5147-161">Bu, bir kilitlenme ile sonuçlanır: olay ayarı yinelemesi hiçbir şekilde yürütülmez ve bekleyen yinelemeler hiçbir şekilde çağrılmaz.</span><span class="sxs-lookup"><span data-stu-id="f5147-161">This results in a deadlock – the event-setting iteration will never execute, and the waiting iterations will never wake up.</span></span>

<span data-ttu-id="f5147-162">Özellikle, bir paralel döngünün bir yinelemesi, ilerleme yapmak için döngünün başka bir yinelemesinin asla beklemelidir.</span><span class="sxs-lookup"><span data-stu-id="f5147-162">In particular, one iteration of a parallel loop should never wait on another iteration of the loop to make progress.</span></span> <span data-ttu-id="f5147-163">Paralel döngü, yinelemeleri sırayla zamanlamaya karar verirse, ters sırada bir kilitlenme meydana gelir.</span><span class="sxs-lookup"><span data-stu-id="f5147-163">If the parallel loop decides to schedule the iterations sequentially but in the opposite order, a deadlock will occur.</span></span>

## <a name="see-also"></a><span data-ttu-id="f5147-164">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f5147-164">See also</span></span>

- [<span data-ttu-id="f5147-165">Paralel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="f5147-165">Parallel LINQ (PLINQ)</span></span>](parallel-linq-plinq.md)
