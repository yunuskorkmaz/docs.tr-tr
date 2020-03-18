---
title: Yönetilen İş Parçacığı Oluşturma En İyi Yöntemleri
ms.date: 10/15/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- threading [.NET Framework], design guidelines
- threading [.NET Framework], best practices
- managed threading
ms.assetid: e51988e7-7f4b-4646-a06d-1416cee8d557
ms.openlocfilehash: a76cc40f308ac2f636a650cd4a17da0e94e23a34
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78160267"
---
# <a name="managed-threading-best-practices"></a><span data-ttu-id="47afd-102">Yönetilen iş parçacığı en iyi uygulamalar</span><span class="sxs-lookup"><span data-stu-id="47afd-102">Managed threading best practices</span></span>
<span data-ttu-id="47afd-103">Multithreading dikkatli programlama gerektirir.</span><span class="sxs-lookup"><span data-stu-id="47afd-103">Multithreading requires careful programming.</span></span> <span data-ttu-id="47afd-104">Çoğu görev için, iş parçacığı havuzu iş parçacıkları tarafından yürütme isteklerini sıraya alarak karmaşıklığı azaltabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="47afd-104">For most tasks, you can reduce complexity by queuing requests for execution by thread pool threads.</span></span> <span data-ttu-id="47afd-105">Bu konu, birden çok iş parçacığının çalışmasını koordine etmek veya engelleyen iş parçacıklarını işlemek gibi daha zor durumları gidermektedir.</span><span class="sxs-lookup"><span data-stu-id="47afd-105">This topic addresses more difficult situations, such as coordinating the work of multiple threads, or handling threads that block.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="47afd-106">.NET Framework 4'ten başlayarak, Görev Paralel Kitaplığı ve PLINQ, çok iş parçacığı lı programlamanın karmaşıklığını ve risklerini azaltan API'ler sağlar.</span><span class="sxs-lookup"><span data-stu-id="47afd-106">Starting with the .NET Framework 4, the Task Parallel Library and PLINQ provide APIs that reduce some of the complexity and risks of multi-threaded programming.</span></span> <span data-ttu-id="47afd-107">Daha fazla bilgi için [.NET'teki Paralel Programlama'ya](../../../docs/standard/parallel-programming/index.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="47afd-107">For more information, see [Parallel Programming in .NET](../../../docs/standard/parallel-programming/index.md).</span></span>  
  
## <a name="deadlocks-and-race-conditions"></a><span data-ttu-id="47afd-108">Kilitlenmeler ve yarış koşulları</span><span class="sxs-lookup"><span data-stu-id="47afd-108">Deadlocks and race conditions</span></span>  
 <span data-ttu-id="47afd-109">Multithreading, iş gücü ve yanıt verme ile ilgili sorunları çözer, ancak bunu yaparken yeni sorunlar sunar: kilitlenmeler ve Yarış koşulları.</span><span class="sxs-lookup"><span data-stu-id="47afd-109">Multithreading solves problems with throughput and responsiveness, but in doing so it introduces new problems: deadlocks and race conditions.</span></span>  
  
### <a name="deadlocks"></a><span data-ttu-id="47afd-110">Kilitlenmeleri</span><span class="sxs-lookup"><span data-stu-id="47afd-110">Deadlocks</span></span>  
 <span data-ttu-id="47afd-111">İki iş parçacığının her biri diğerinin kilitlemiş olduğu bir kaynağı kilitlemeye çalıştığında kilitlenme oluşur.</span><span class="sxs-lookup"><span data-stu-id="47afd-111">A deadlock occurs when each of two threads tries to lock a resource the other has already locked.</span></span> <span data-ttu-id="47afd-112">Ne iş parçacığı daha fazla ilerleme yapabilir.</span><span class="sxs-lookup"><span data-stu-id="47afd-112">Neither thread can make any further progress.</span></span>  
  
 <span data-ttu-id="47afd-113">Yönetilen iş parçacığı sınıflarının birçok yöntemi, kilitlenmeleri algılamanıza yardımcı olmak için zaman zaman larını sağlar.</span><span class="sxs-lookup"><span data-stu-id="47afd-113">Many methods of the managed threading classes provide time-outs to help you detect deadlocks.</span></span> <span data-ttu-id="47afd-114">Örneğin, aşağıdaki kod adlı `lockObject`bir nesne üzerinde kilit elde etmeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="47afd-114">For example, the following code attempts to acquire a lock on an object named `lockObject`.</span></span> <span data-ttu-id="47afd-115">Kilit 300 milisaniye içinde elde <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> edilmezse, döndürür. `false`</span><span class="sxs-lookup"><span data-stu-id="47afd-115">If the lock is not obtained in 300 milliseconds, <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> returns `false`.</span></span>  
  
```vb  
If Monitor.TryEnter(lockObject, 300) Then  
    Try  
        ' Place code protected by the Monitor here.  
    Finally  
        Monitor.Exit(lockObject)  
    End Try  
Else  
    ' Code to execute if the attempt times out.  
End If  
```  
  
```csharp  
if (Monitor.TryEnter(lockObject, 300)) {  
    try {  
        // Place code protected by the Monitor here.  
    }  
    finally {  
        Monitor.Exit(lockObject);  
    }  
}  
else {  
    // Code to execute if the attempt times out.  
}  
```  
  
### <a name="race-conditions"></a><span data-ttu-id="47afd-116">Yarış koşulları</span><span class="sxs-lookup"><span data-stu-id="47afd-116">Race conditions</span></span>  
 <span data-ttu-id="47afd-117">Yarış koşulu, bir programın sonucu iki veya daha fazla iş parçacığının önce belirli bir kod bloğuna eriştiğine bağlı olduğunda oluşan bir hatadır.</span><span class="sxs-lookup"><span data-stu-id="47afd-117">A race condition is a bug that occurs when the outcome of a program depends on which of two or more threads reaches a particular block of code first.</span></span> <span data-ttu-id="47afd-118">Programı birçok kez çalıştırmak farklı sonuçlar üretir ve belirli bir çalıştırmanın sonucu tahmin edilemez.</span><span class="sxs-lookup"><span data-stu-id="47afd-118">Running the program many times produces different results, and the result of any given run cannot be predicted.</span></span>  
  
 <span data-ttu-id="47afd-119">Bir yarış koşulu basit bir örnek bir alan artış olduğunu.</span><span class="sxs-lookup"><span data-stu-id="47afd-119">A simple example of a race condition is incrementing a field.</span></span> <span data-ttu-id="47afd-120">Bir sınıfın (C#) `objCt++;` veya `objCt += 1` (Visual Basic) gibi kodlar kullanılarak sınıfın her örneğinde artılan özel bir **statik** alanı (Visual Basic'te**Paylaşılan)** olduğunu varsayalım.</span><span class="sxs-lookup"><span data-stu-id="47afd-120">Suppose a class has a private **static** field (**Shared** in Visual Basic) that is incremented every time an instance of the class is created, using code such as `objCt++;` (C#) or `objCt += 1` (Visual Basic).</span></span> <span data-ttu-id="47afd-121">Bu işlem, değeri `objCt` bir kasaya yüklemeyi, değeri artarak ve `objCt`'de depolamayı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="47afd-121">This operation requires loading the value from `objCt` into a register, incrementing the value, and storing it in `objCt`.</span></span>  
  
 <span data-ttu-id="47afd-122">Çok iş parçacığı uygulamasında, değeri yüklemiş ve artan bir iş parçacığı, üç adımı da gerçekleştiren başka bir iş parçacığı tarafından engellenebilir; ilk iş parçacığı yürütme devam eder ve değerini `objCt` depolar, bu değer geçici olarak değişti gerçeğini dikkate almadan üzerine yazar.</span><span class="sxs-lookup"><span data-stu-id="47afd-122">In a multithreaded application, a thread that has loaded and incremented the value might be preempted by another thread which performs all three steps; when the first thread resumes execution and stores its value, it overwrites `objCt` without taking into account the fact that the value has changed in the interim.</span></span>  
  
 <span data-ttu-id="47afd-123">Bu özel yarış koşulu gibi <xref:System.Threading.Interlocked> sınıfın yöntemleri kullanılarak kolayca <xref:System.Threading.Interlocked.Increment%2A?displayProperty=nameWithType>önlenir.</span><span class="sxs-lookup"><span data-stu-id="47afd-123">This particular race condition is easily avoided by using methods of the <xref:System.Threading.Interlocked> class, such as <xref:System.Threading.Interlocked.Increment%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="47afd-124">Birden çok iş parçacığı arasında veri eşitleme için diğer teknikler hakkında okumak [için, Multithreading için Veri Eşitleme](../../../docs/standard/threading/synchronizing-data-for-multithreading.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="47afd-124">To read about other techniques for synchronizing data among multiple threads, see [Synchronizing Data for Multithreading](../../../docs/standard/threading/synchronizing-data-for-multithreading.md).</span></span>  
  
 <span data-ttu-id="47afd-125">Birden çok iş parçacığının etkinliklerini eşitlediğinizde yarış koşulları da oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="47afd-125">Race conditions can also occur when you synchronize the activities of multiple threads.</span></span> <span data-ttu-id="47afd-126">Bir kod satırı yazdığınızda, satırı yürütmeden önce (veya satırı oluşturan tek tek makine yönergelerinden herhangi biri) ve başka bir iş parçacığı nın önüne geçtiğinde ne olabileceğini göz önünde bulundurmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="47afd-126">Whenever you write a line of code, you must consider what might happen if a thread were preempted before executing the line (or before any of the individual machine instructions that make up the line), and another thread overtook it.</span></span>  
  
## <a name="static-members-and-static-constructors"></a><span data-ttu-id="47afd-127">Statik üyeler ve statik yapıcılar</span><span class="sxs-lookup"><span data-stu-id="47afd-127">Static members and static constructors</span></span>  
 <span data-ttu-id="47afd-128">Bir sınıf, sınıf oluşturucusu (Visual`static` `Shared Sub New` Basic'te C#'daki oluşturucu) çalışma tamamlanana kadar başharfe fişi değildir.</span><span class="sxs-lookup"><span data-stu-id="47afd-128">A class is not initialized until its class constructor (`static` constructor in C#, `Shared Sub New` in Visual Basic) has finished running.</span></span> <span data-ttu-id="47afd-129">Başharflere geçirilmeyen bir türde kodun yürütülmesini önlemek için, ortak dil `static` çalışma süresi,`Shared` sınıf oluşturucu çalışmaya devam edene kadar diğer iş parçacıklarından sınıf üyelerine (Visual Basic'teki üyeler) tüm çağrıları engeller.</span><span class="sxs-lookup"><span data-stu-id="47afd-129">To prevent the execution of code on a type that is not initialized, the common language runtime blocks all calls from other threads to `static` members of the class (`Shared` members in Visual Basic) until the class constructor has finished running.</span></span>  
  
 <span data-ttu-id="47afd-130">Örneğin, bir sınıf oluşturucu yeni bir iş parçacığı başlatır ve iş parçacığı yordamı sınıfın bir `static` üyesiçağırırsa, sınıf oluşturucu tamamlanana kadar yeni iş parçacığı engeller.</span><span class="sxs-lookup"><span data-stu-id="47afd-130">For example, if a class constructor starts a new thread, and the thread procedure calls a `static` member of the class, the new thread blocks until the class constructor completes.</span></span>  
  
 <span data-ttu-id="47afd-131">Bu, bir oluşturucu olabilir `static` herhangi bir tür için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="47afd-131">This applies to any type that can have a `static` constructor.</span></span>  

## <a name="number-of-processors"></a><span data-ttu-id="47afd-132">İşlemci sayısı</span><span class="sxs-lookup"><span data-stu-id="47afd-132">Number of processors</span></span>

<span data-ttu-id="47afd-133">Birden çok işlemci veya bir sistemde yalnızca bir işlemci olup olmadığını çok iş parçacığı mimarisi etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="47afd-133">Whether there are multiple processors or only one processor available on a system can influence multithreaded architecture.</span></span> <span data-ttu-id="47afd-134">Daha fazla bilgi için [İşlemci Sayısı'na](https://docs.microsoft.com/previous-versions/dotnet/netframework-1.1/1c9txz50(v%3dvs.71)#number-of-processors)bakın.</span><span class="sxs-lookup"><span data-stu-id="47afd-134">For more information, see [Number of Processors](https://docs.microsoft.com/previous-versions/dotnet/netframework-1.1/1c9txz50(v%3dvs.71)#number-of-processors).</span></span>

<span data-ttu-id="47afd-135">Çalışma <xref:System.Environment.ProcessorCount?displayProperty=nameWithType> zamanında kullanılabilen işlemci sayısını belirlemek için özelliği kullanın.</span><span class="sxs-lookup"><span data-stu-id="47afd-135">Use the <xref:System.Environment.ProcessorCount?displayProperty=nameWithType> property to determine the number of processors available at runtime.</span></span>
  
## <a name="general-recommendations"></a><span data-ttu-id="47afd-136">Genel öneriler</span><span class="sxs-lookup"><span data-stu-id="47afd-136">General recommendations</span></span>  
 <span data-ttu-id="47afd-137">Birden çok iş parçacığı kullanırken aşağıdaki yönergeleri göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="47afd-137">Consider the following guidelines when using multiple threads:</span></span>  
  
- <span data-ttu-id="47afd-138">Diğer iş <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> parçacıklarını sonlandırmak için kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="47afd-138">Don't use <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> to terminate other threads.</span></span> <span data-ttu-id="47afd-139">**Abort'u** başka bir iş parçacığıüzerinde çağırmak, iş parçacığının işlenmesinde hangi noktaya ulaştığını bilmeden bu iş parçacığına özel bir özel durum atmaya benzer.</span><span class="sxs-lookup"><span data-stu-id="47afd-139">Calling **Abort** on another thread is akin to throwing an exception on that thread, without knowing what point that thread has reached in its processing.</span></span>  
  
- <span data-ttu-id="47afd-140">Birden çok <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> iş <xref:System.Threading.Thread.Resume%2A?displayProperty=nameWithType> parçacığının etkinliklerini kullanmayın ve eşitlemayın.</span><span class="sxs-lookup"><span data-stu-id="47afd-140">Don't use <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> and <xref:System.Threading.Thread.Resume%2A?displayProperty=nameWithType> to synchronize the activities of multiple threads.</span></span> <span data-ttu-id="47afd-141">, <xref:System.Threading.Mutex>, <xref:System.Threading.ManualResetEvent> <xref:System.Threading.AutoResetEvent>, <xref:System.Threading.Monitor>ve .</span><span class="sxs-lookup"><span data-stu-id="47afd-141">Do use <xref:System.Threading.Mutex>, <xref:System.Threading.ManualResetEvent>, <xref:System.Threading.AutoResetEvent>, and <xref:System.Threading.Monitor>.</span></span>  
  
- <span data-ttu-id="47afd-142">Ana programınızdan (örneğin olayları kullanarak) çalışan iş parçacıklarının yürütülmesini denetlemeyin.</span><span class="sxs-lookup"><span data-stu-id="47afd-142">Don't control the execution of worker threads from your main program (using events, for example).</span></span> <span data-ttu-id="47afd-143">Bunun yerine, çalışma kullanılabilir olana kadar beklemek, çalıştırın ve bittiğinde programın diğer bölümlerini bildirmekiçin çalışan iş parçacıklarının sorumlu olması için programınızı tasarla.</span><span class="sxs-lookup"><span data-stu-id="47afd-143">Instead, design your program so that worker threads are responsible for waiting until work is available, executing it, and notifying other parts of your program when finished.</span></span> <span data-ttu-id="47afd-144">Alt iş parçacığınız engellemiyorsa, iş parçacığı havuzu iş parçacıklarını kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="47afd-144">If your worker threads do not block, consider using thread pool threads.</span></span> <span data-ttu-id="47afd-145"><xref:System.Threading.Monitor.PulseAll%2A?displayProperty=nameWithType>işçi iş parçacıklarının engellendiği durumlarda yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="47afd-145"><xref:System.Threading.Monitor.PulseAll%2A?displayProperty=nameWithType> is useful in situations where worker threads block.</span></span>  
  
- <span data-ttu-id="47afd-146">Türleri kilit nesnesi olarak kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="47afd-146">Don't use types as lock objects.</span></span> <span data-ttu-id="47afd-147">Diğer bir deyişle, `lock(typeof(X))` C# veya `SyncLock(GetType(X))` Visual Basic gibi kodlardan veya <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> nesnelerle <xref:System.Type> kullanmaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="47afd-147">That is, avoid code such as `lock(typeof(X))` in C# or `SyncLock(GetType(X))` in Visual Basic, or the use of <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> with <xref:System.Type> objects.</span></span> <span data-ttu-id="47afd-148">Belirli bir tür için, uygulama <xref:System.Type?displayProperty=nameWithType> etki alanı başına yalnızca bir örnek vardır.</span><span class="sxs-lookup"><span data-stu-id="47afd-148">For a given type, there is only one instance of <xref:System.Type?displayProperty=nameWithType> per application domain.</span></span> <span data-ttu-id="47afd-149">Kilitlediğiniz tür herkese açıksa, sizinki dışındaki kod kilitler alabilir ve bu da kilitlenmeye yol açabilir.</span><span class="sxs-lookup"><span data-stu-id="47afd-149">If the type you take a lock on is public, code other than your own can take locks on it, leading to deadlocks.</span></span> <span data-ttu-id="47afd-150">Ek sorunlar için Güvenilirlik [En İyi Uygulamaları'na](../../../docs/framework/performance/reliability-best-practices.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="47afd-150">For additional issues, see [Reliability Best Practices](../../../docs/framework/performance/reliability-best-practices.md).</span></span>  
  
- <span data-ttu-id="47afd-151">Örneğin `lock(this)` C# veya `SyncLock(Me)` Visual Basic'te gibi örnekleri kilitlerken dikkatli olun.</span><span class="sxs-lookup"><span data-stu-id="47afd-151">Use caution when locking on instances, for example `lock(this)` in C# or `SyncLock(Me)` in Visual Basic.</span></span> <span data-ttu-id="47afd-152">Uygulamanızdaki diğer kod, türün dışında, nesneye kilitlenirse, kilitlenmeler oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="47afd-152">If other code in your application, external to the type, takes a lock on the object, deadlocks could occur.</span></span>  
  
- <span data-ttu-id="47afd-153">İzparçacığı monitördeyken bir özel durum oluşsa bile, monitöre giren bir iş parçacığının her zaman bu monitörden ayrıldığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="47afd-153">Do ensure that a thread that has entered a monitor always leaves that monitor, even if an exception occurs while the thread is in the monitor.</span></span> <span data-ttu-id="47afd-154">C# [kilit](../../csharp/language-reference/keywords/lock-statement.md) deyimi ve Visual Basic [SyncLock](../../visual-basic/language-reference/statements/synclock-statement.md) deyimi bu davranışı **finally** otomatik olarak <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType> sağlar ve bu davranışı n için çağrıldığından emin olmak için son bir blok kullanır.</span><span class="sxs-lookup"><span data-stu-id="47afd-154">The C# [lock](../../csharp/language-reference/keywords/lock-statement.md) statement and the Visual Basic [SyncLock](../../visual-basic/language-reference/statements/synclock-statement.md) statement provide this behavior automatically, employing a **finally** block to ensure that <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType> is called.</span></span> <span data-ttu-id="47afd-155">**Exit'in** çağrılmasını sağlayamazsanız, **Mutex'i**kullanmak için tasarımınızı değiştirmeyi düşünün.</span><span class="sxs-lookup"><span data-stu-id="47afd-155">If you cannot ensure that **Exit** will be called, consider changing your design to use **Mutex**.</span></span> <span data-ttu-id="47afd-156">Şu anda sahibi olan iş parçacığı sona erdiğinde bir mutex otomatik olarak serbest bırakılır.</span><span class="sxs-lookup"><span data-stu-id="47afd-156">A mutex is automatically released when the thread that currently owns it terminates.</span></span>  
  
- <span data-ttu-id="47afd-157">Farklı kaynaklar gerektiren görevler için birden çok iş parçacığı kullanın ve tek bir kaynağa birden çok iş parçacığı atamaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="47afd-157">Do use multiple threads for tasks that require different resources, and avoid assigning multiple threads to a single resource.</span></span> <span data-ttu-id="47afd-158">Örneğin, G/Ç içeren herhangi bir görev kendi iş parçacığına sahip olmaktan yararlanır, çünkü bu iş parçacığı G/Ç işlemleri sırasında engellenir ve böylece diğer iş parçacıklarının yürütülmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="47afd-158">For example, any task involving I/O benefits from having its own thread, because that thread will block during I/O operations and thus allow other threads to execute.</span></span> <span data-ttu-id="47afd-159">Kullanıcı girişi, özel bir iş parçacığından yararlanan başka bir kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="47afd-159">User input is another resource that benefits from a dedicated thread.</span></span> <span data-ttu-id="47afd-160">Tek işlemcili bir bilgisayarda, yoğun hesaplama içeren bir görev, kullanıcı girişi ve G/Ç içeren görevlerle bir arada bulunur, ancak birden çok hesaplama yoğun görev birbiriyle uğraşır.</span><span class="sxs-lookup"><span data-stu-id="47afd-160">On a single-processor computer, a task that involves intensive computation coexists with user input and with tasks that involve I/O, but multiple computation-intensive tasks contend with each other.</span></span>  
  
- <span data-ttu-id="47afd-161">İfadeyi <xref:System.Threading.Interlocked> (Visual `lock` `SyncLock` Basic'te) kullanmak yerine basit durum değişiklikleri için sınıfın yöntemlerini kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="47afd-161">Consider using methods of the <xref:System.Threading.Interlocked> class for simple state changes, instead of using the `lock` statement (`SyncLock` in Visual Basic).</span></span> <span data-ttu-id="47afd-162">`lock` İfade iyi bir genel amaçlı araçtır, ancak <xref:System.Threading.Interlocked> sınıf atomik olması gereken güncelleştirmeler için daha iyi performans sağlar.</span><span class="sxs-lookup"><span data-stu-id="47afd-162">The `lock` statement is a good general-purpose tool, but the <xref:System.Threading.Interlocked> class provides better performance for updates that must be atomic.</span></span> <span data-ttu-id="47afd-163">İçsel olarak, çekişme yoksa tek bir kilit öneki yürütür.</span><span class="sxs-lookup"><span data-stu-id="47afd-163">Internally, it executes a single lock prefix if there is no contention.</span></span> <span data-ttu-id="47afd-164">Kod incelemelerinde, aşağıdaki örneklerde gösterilen gibi kodlara dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="47afd-164">In code reviews, watch for code like that shown in the following examples.</span></span> <span data-ttu-id="47afd-165">İlk örnekte, bir durum değişkeni artımlı:</span><span class="sxs-lookup"><span data-stu-id="47afd-165">In the first example, a state variable is incremented:</span></span>  
  
    ```vb  
    SyncLock lockObject  
        myField += 1  
    End SyncLock  
    ```  
  
    ```csharp  
    lock(lockObject)
    {  
        myField++;  
    }  
    ```  
  
     <span data-ttu-id="47afd-166">Aşağıdaki gibi, deyimi <xref:System.Threading.Interlocked.Increment%2A> yerine yöntemi kullanarak performansı artırabilirsiniz: `lock`</span><span class="sxs-lookup"><span data-stu-id="47afd-166">You can improve performance by using the <xref:System.Threading.Interlocked.Increment%2A> method instead of the `lock` statement, as follows:</span></span>  
  
    ```vb  
    System.Threading.Interlocked.Increment(myField)  
    ```  
  
    ```csharp  
    System.Threading.Interlocked.Increment(myField);  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="47afd-167">.NET Framework 2.0 ve sonraki <xref:System.Threading.Interlocked.Add%2A> durumlarda, 1'den büyük atomik artışlar için yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="47afd-167">In the .NET Framework 2.0 and later, use the <xref:System.Threading.Interlocked.Add%2A> method for atomic increments larger than 1.</span></span>  
  
     <span data-ttu-id="47afd-168">İkinci örnekte, bir başvuru türü değişkeni yalnızca null`Nothing` reference (Visual Basic'te) ise güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="47afd-168">In the second example, a reference type variable is updated only if it is a null reference (`Nothing` in Visual Basic).</span></span>  
  
    ```vb  
    If x Is Nothing Then  
        SyncLock lockObject  
            If x Is Nothing Then  
                x = y  
            End If  
        End SyncLock  
    End If  
    ```  
  
    ```csharp  
    if (x == null)  
    {  
        lock (lockObject)  
        {  
            x ??= y;
        }  
    }  
    ```  
  
     <span data-ttu-id="47afd-169">Performans, aşağıdaki gibi, <xref:System.Threading.Interlocked.CompareExchange%2A> bunun yerine yöntem kullanılarak artırılabilir:</span><span class="sxs-lookup"><span data-stu-id="47afd-169">Performance can be improved by using the <xref:System.Threading.Interlocked.CompareExchange%2A> method instead, as follows:</span></span>  
  
    ```vb  
    System.Threading.Interlocked.CompareExchange(x, y, Nothing)  
    ```  
  
    ```csharp  
    System.Threading.Interlocked.CompareExchange(ref x, y, null);  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="47afd-170">.NET Framework 2.0 ile <xref:System.Threading.Interlocked.CompareExchange%60%601%28%60%600%40%2C%60%600%2C%60%600%29> başlayarak, yöntem aşırı başvuru türleri için tür güvenli bir alternatif sağlar.</span><span class="sxs-lookup"><span data-stu-id="47afd-170">Beginning with .NET Framework 2.0, the <xref:System.Threading.Interlocked.CompareExchange%60%601%28%60%600%40%2C%60%600%2C%60%600%29> method overload provides a type-safe alternative for reference types.</span></span>
  
## <a name="recommendations-for-class-libraries"></a><span data-ttu-id="47afd-171">Sınıf kitaplıkları için öneriler</span><span class="sxs-lookup"><span data-stu-id="47afd-171">Recommendations for class libraries</span></span>  
 <span data-ttu-id="47afd-172">Çok iş parçacığı için sınıf kitaplıkları tasarlarken aşağıdaki yönergeleri göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="47afd-172">Consider the following guidelines when designing class libraries for multithreading:</span></span>  
  
- <span data-ttu-id="47afd-173">Mümkünse eşitleme gereksiniminden kaçının.</span><span class="sxs-lookup"><span data-stu-id="47afd-173">Avoid the need for synchronization, if possible.</span></span> <span data-ttu-id="47afd-174">Bu, özellikle ağır kullanılan kod için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="47afd-174">This is especially true for heavily used code.</span></span> <span data-ttu-id="47afd-175">Örneğin, bir algoritma bir yarış koşulunu ortadan kaldırmak yerine tolere etmek için ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="47afd-175">For example, an algorithm might be adjusted to tolerate a race condition rather than eliminate it.</span></span> <span data-ttu-id="47afd-176">Gereksiz eşitleme performansı düşürür ve kilitlenmeler ve yarış koşulları olasılığını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="47afd-176">Unnecessary synchronization decreases performance and creates the possibility of deadlocks and race conditions.</span></span>  
  
- <span data-ttu-id="47afd-177">Statik verileri`Shared` (Visual Basic'te) varsayılan olarak güvenli hale getirin.</span><span class="sxs-lookup"><span data-stu-id="47afd-177">Make static data (`Shared` in Visual Basic) thread safe by default.</span></span>  
  
- <span data-ttu-id="47afd-178">Örnek veri iş parçacığı varsayılan olarak güvenli yapmayın.</span><span class="sxs-lookup"><span data-stu-id="47afd-178">Do not make instance data thread safe by default.</span></span> <span data-ttu-id="47afd-179">İş parçacığı güvenli kod oluşturmak için kilitler eklemek performansı azaltır, kilit çekişmesini artırır ve kilitlenmelerin oluşma olasılığını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="47afd-179">Adding locks to create thread-safe code decreases performance, increases lock contention, and creates the possibility for deadlocks to occur.</span></span> <span data-ttu-id="47afd-180">Yaygın uygulama modellerinde, aynı anda yalnızca bir iş parçacığı kullanıcı kodunu yürütür ve bu da iş parçacığı güvenliği gereksinimini en aza indirir.</span><span class="sxs-lookup"><span data-stu-id="47afd-180">In common application models, only one thread at a time executes user code, which minimizes the need for thread safety.</span></span> <span data-ttu-id="47afd-181">Bu nedenle, .NET Framework sınıf kitaplıkları varsayılan olarak iş parçacığı güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="47afd-181">For this reason, the .NET Framework class libraries are not thread safe by default.</span></span>  
  
- <span data-ttu-id="47afd-182">Statik durumu değiştiren statik yöntemler sağlamaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="47afd-182">Avoid providing static methods that alter static state.</span></span> <span data-ttu-id="47afd-183">Yaygın sunucu senaryolarında statik durum istekler arasında paylaşılır, bu da birden çok iş parçacığının bu kodu aynı anda yürütebileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="47afd-183">In common server scenarios, static state is shared across requests, which means multiple threads can execute that code at the same time.</span></span> <span data-ttu-id="47afd-184">Bu, hataların iş parçacığı olasılığını açar.</span><span class="sxs-lookup"><span data-stu-id="47afd-184">This opens up the possibility of threading bugs.</span></span> <span data-ttu-id="47afd-185">Verileri istekler arasında paylaşılmayan örneklere kapsülleyen bir tasarım deseni kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="47afd-185">Consider using a design pattern that encapsulates data into instances that are not shared across requests.</span></span> <span data-ttu-id="47afd-186">Ayrıca, statik veriler eşitlenirse, durumu değiştiren statik yöntemler arasındaki çağrılar kilitlenmeye veya gereksiz eşitlemeyle sonuçlanabilir ve performansı olumsuz yönde etkiler.</span><span class="sxs-lookup"><span data-stu-id="47afd-186">Furthermore, if static data are synchronized, calls between static methods that alter state can result in deadlocks or redundant synchronization, adversely affecting performance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47afd-187">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="47afd-187">See also</span></span>

- [<span data-ttu-id="47afd-188">İş Parçacığı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="47afd-188">Threading</span></span>](../../../docs/standard/threading/index.md)
- [<span data-ttu-id="47afd-189">İş Parçacıkları ve İş Parçacığı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="47afd-189">Threads and Threading</span></span>](../../../docs/standard/threading/threads-and-threading.md)
