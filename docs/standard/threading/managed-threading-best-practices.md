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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 907e85d2622ea07ddbb61092f439583ed72e0c50
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54560041"
---
# <a name="managed-threading-best-practices"></a><span data-ttu-id="78297-102">Yönetilen iş parçacığı oluşturma en iyi yöntemleri</span><span class="sxs-lookup"><span data-stu-id="78297-102">Managed threading best practices</span></span>
<span data-ttu-id="78297-103">Çoklu iş parçacığı kullanımı dikkatli programlama gerektirir.</span><span class="sxs-lookup"><span data-stu-id="78297-103">Multithreading requires careful programming.</span></span> <span data-ttu-id="78297-104">Çoğu görevler için istediğiniz karmaşıklık yürütme için sıraya alma istekleri tarafından iş parçacığı havuzu iş parçacıkları tarafından azaltabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="78297-104">For most tasks, you can reduce complexity by queuing requests for execution by thread pool threads.</span></span> <span data-ttu-id="78297-105">Birden çok iş parçacığı çalışması koordine veya işleme iş parçacıkları bu blok gibi durumlarda daha zor, bu konuda ele alır.</span><span class="sxs-lookup"><span data-stu-id="78297-105">This topic addresses more difficult situations, such as coordinating the work of multiple threads, or handling threads that block.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="78297-106">.NET Framework 4 ile başlayarak, görev paralel kitaplığı ve PLINQ'da bazı karmaşıklığı ve çok iş parçacıklı programlama risklerini azaltmak API'leri sağlar.</span><span class="sxs-lookup"><span data-stu-id="78297-106">Starting with the .NET Framework 4, the Task Parallel Library and PLINQ provide APIs that reduce some of the complexity and risks of multi-threaded programming.</span></span> <span data-ttu-id="78297-107">Daha fazla bilgi için [.NET paralel programlama](../../../docs/standard/parallel-programming/index.md).</span><span class="sxs-lookup"><span data-stu-id="78297-107">For more information, see [Parallel Programming in .NET](../../../docs/standard/parallel-programming/index.md).</span></span>  
  
## <a name="deadlocks-and-race-conditions"></a><span data-ttu-id="78297-108">Kilitlenmeler ve yarış durumları</span><span class="sxs-lookup"><span data-stu-id="78297-108">Deadlocks and race conditions</span></span>  
 <span data-ttu-id="78297-109">Çoklu iş parçacığı kullanımı, aktarım hızı ve yanıt hızını sorunları çözer, ancak bunun yapılması yeni sorunlar sunar: Kilitlenmeler ve yarış durumları.</span><span class="sxs-lookup"><span data-stu-id="78297-109">Multithreading solves problems with throughput and responsiveness, but in doing so it introduces new problems: deadlocks and race conditions.</span></span>  
  
### <a name="deadlocks"></a><span data-ttu-id="78297-110">Kilitlenmeler</span><span class="sxs-lookup"><span data-stu-id="78297-110">Deadlocks</span></span>  
 <span data-ttu-id="78297-111">Her iki iş parçacığı diğer zaten kilitli bir kaynak kilitlemek çalıştığında bir kilitlenme oluşur.</span><span class="sxs-lookup"><span data-stu-id="78297-111">A deadlock occurs when each of two threads tries to lock a resource the other has already locked.</span></span> <span data-ttu-id="78297-112">Her iki iş parçacığı herhangi bir gelişme yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="78297-112">Neither thread can make any further progress.</span></span>  
  
 <span data-ttu-id="78297-113">Yönetilen iş parçacığı sınıfların birçok yöntem zaman aşımlarını kilitlenmeleri algılamanıza yardımcı olarak sağlayın.</span><span class="sxs-lookup"><span data-stu-id="78297-113">Many methods of the managed threading classes provide time-outs to help you detect deadlocks.</span></span> <span data-ttu-id="78297-114">Örneğin, aşağıdaki kodu adlı bir nesne üzerinde kilit çalışır `lockObject`.</span><span class="sxs-lookup"><span data-stu-id="78297-114">For example, the following code attempts to acquire a lock on an object named `lockObject`.</span></span> <span data-ttu-id="78297-115">Kilit 300 milisaniye cinsinden alınıyorsa değil, <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> döndürür `false`.</span><span class="sxs-lookup"><span data-stu-id="78297-115">If the lock is not obtained in 300 milliseconds, <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> returns `false`.</span></span>  
  
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
  
### <a name="race-conditions"></a><span data-ttu-id="78297-116">Yarış durumları</span><span class="sxs-lookup"><span data-stu-id="78297-116">Race conditions</span></span>  
 <span data-ttu-id="78297-117">Bir yarış durumu bir program sonucu, iki veya daha fazla iş parçacıklarının belirli bir kod bloğunun ilk ulaştığında üzerinde bağlı olduğunda oluşan bir hatadır.</span><span class="sxs-lookup"><span data-stu-id="78297-117">A race condition is a bug that occurs when the outcome of a program depends on which of two or more threads reaches a particular block of code first.</span></span> <span data-ttu-id="78297-118">Birden çok kez programı çalıştırmaya farklı sonuçlar üretir ve herhangi belirli çalıştırma sonucu tahmin edilemez.</span><span class="sxs-lookup"><span data-stu-id="78297-118">Running the program many times produces different results, and the result of any given run cannot be predicted.</span></span>  
  
 <span data-ttu-id="78297-119">Bir alan artan bir yarış durumu basit bir örneği.</span><span class="sxs-lookup"><span data-stu-id="78297-119">A simple example of a race condition is incrementing a field.</span></span> <span data-ttu-id="78297-120">Özel bir sınıf sahip olduğunu varsayın **statik** alan (**paylaşılan** Visual Basic'te) gibi kod kullanarak bir sınıf örneği oluşturulduğunda artırılır `objCt++;` (C#) veya `objCt += 1` () Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="78297-120">Suppose a class has a private **static** field (**Shared** in Visual Basic) that is incremented every time an instance of the class is created, using code such as `objCt++;` (C#) or `objCt += 1` (Visual Basic).</span></span> <span data-ttu-id="78297-121">Bu işlem değerinden yükleniyor gerektirir `objCt` artan bir yazmacına değerini ve de depolamak `objCt`.</span><span class="sxs-lookup"><span data-stu-id="78297-121">This operation requires loading the value from `objCt` into a register, incrementing the value, and storing it in `objCt`.</span></span>  
  
 <span data-ttu-id="78297-122">Çok iş parçacıklı bir uygulamada, tüm üç adımı gerçekleştirir başka bir iş parçacığı tarafından yüklenen ve değer artan bir iş parçacığı etkisiz hale; ilk iş parçacığında yürütmeyi devam ettirir ve değerini depolar, üzerine yazar `objCt` değeri bu arada değişti gerçeği göz önüne almadan.</span><span class="sxs-lookup"><span data-stu-id="78297-122">In a multithreaded application, a thread that has loaded and incremented the value might be preempted by another thread which performs all three steps; when the first thread resumes execution and stores its value, it overwrites `objCt` without taking into account the fact that the value has changed in the interim.</span></span>  
  
 <span data-ttu-id="78297-123">Bu belirli bir yarış durumu yöntemleri kullanılarak kolayca önlenmiş <xref:System.Threading.Interlocked> gibi sınıf <xref:System.Threading.Interlocked.Increment%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="78297-123">This particular race condition is easily avoided by using methods of the <xref:System.Threading.Interlocked> class, such as <xref:System.Threading.Interlocked.Increment%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="78297-124">Birden çok iş parçacığı arasında veri eşitlemek için diğer teknikler hakkında bilgi için bkz [çoklu iş parçacığı kullanımı için veri eşitleme](../../../docs/standard/threading/synchronizing-data-for-multithreading.md).</span><span class="sxs-lookup"><span data-stu-id="78297-124">To read about other techniques for synchronizing data among multiple threads, see [Synchronizing Data for Multithreading](../../../docs/standard/threading/synchronizing-data-for-multithreading.md).</span></span>  
  
 <span data-ttu-id="78297-125">Birden çok iş parçacığı etkinliklerini eşitlediğinizde yarış durumları da meydana gelebilir.</span><span class="sxs-lookup"><span data-stu-id="78297-125">Race conditions can also occur when you synchronize the activities of multiple threads.</span></span> <span data-ttu-id="78297-126">Bir satır kod yazdığınızda, ne olacağını dikkate almanız gereken bir iş parçacığı etkisiz satırı yürütülmeden önce (veya herhangi bir satır yukarı olun tek makine yönergelerine önce) ve başka bir iş parçacığı, taşıyorduysa.</span><span class="sxs-lookup"><span data-stu-id="78297-126">Whenever you write a line of code, you must consider what might happen if a thread were preempted before executing the line (or before any of the individual machine instructions that make up the line), and another thread overtook it.</span></span>  
  
## <a name="static-members-and-static-constructors"></a><span data-ttu-id="78297-127">Statik üyeleri ve statik oluşturucular</span><span class="sxs-lookup"><span data-stu-id="78297-127">Static members and static constructors</span></span>  
 <span data-ttu-id="78297-128">Bir sınıf kendi sınıf oluşturucusunda kadar başlatılmadı (`static` C# ' ta, Oluşturucuda `Shared Sub New` Visual Basic'te) çalışması sona erdi.</span><span class="sxs-lookup"><span data-stu-id="78297-128">A class is not initialized until its class constructor (`static` constructor in C#, `Shared Sub New` in Visual Basic) has finished running.</span></span> <span data-ttu-id="78297-129">Başlatılmamış bir tür üzerinde kodun yürütülmesini önlemek için ortak dil çalışma zamanı için diğer iş parçacıklarından tüm çağrıları engeller `static` sınıf üyeleri (`Shared` üyeleri Visual Basic'te) kadar sınıf oluşturucu çalışması sona erdi.</span><span class="sxs-lookup"><span data-stu-id="78297-129">To prevent the execution of code on a type that is not initialized, the common language runtime blocks all calls from other threads to `static` members of the class (`Shared` members in Visual Basic) until the class constructor has finished running.</span></span>  
  
 <span data-ttu-id="78297-130">Örneğin yeni bir iş parçacığı sınıf oluşturucusunu başlatır ve iş parçacığı yordamı çağıran bir `static` üye sınıfının, sınıf oluşturucusu tamamlanıncaya kadar yeni bir iş parçacığını engeller.</span><span class="sxs-lookup"><span data-stu-id="78297-130">For example, if a class constructor starts a new thread, and the thread procedure calls a `static` member of the class, the new thread blocks until the class constructor completes.</span></span>  
  
 <span data-ttu-id="78297-131">Bu olabilir herhangi bir tür için geçerli bir `static` Oluşturucusu.</span><span class="sxs-lookup"><span data-stu-id="78297-131">This applies to any type that can have a `static` constructor.</span></span>  

## <a name="number-of-processors"></a><span data-ttu-id="78297-132">İşlemci sayısı</span><span class="sxs-lookup"><span data-stu-id="78297-132">Number of processors</span></span>

<span data-ttu-id="78297-133">Kullanılabilir olup olmadığını birden çok işlemci veya tek bir işlemci bir sistemde çok iş parçacıklı mimarisi etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="78297-133">Whether there are multiple processors or only one processor available on a system can influence multithreaded architecture.</span></span> <span data-ttu-id="78297-134">Daha fazla bilgi için [numarası, işlemci](https://docs.microsoft.com/previous-versions/dotnet/netframework-1.1/1c9txz50(v%3dvs.71)#number-of-processors).</span><span class="sxs-lookup"><span data-stu-id="78297-134">For more information, see [Number of Processors](https://docs.microsoft.com/previous-versions/dotnet/netframework-1.1/1c9txz50(v%3dvs.71)#number-of-processors).</span></span>

<span data-ttu-id="78297-135">Kullanım <xref:System.Environment.ProcessorCount?displayProperty=nameWithType> özelliği çalışma zamanında kullanılabilir işlemci sayısını belirlemek için.</span><span class="sxs-lookup"><span data-stu-id="78297-135">Use the <xref:System.Environment.ProcessorCount?displayProperty=nameWithType> property to determine the number of processors available at runtime.</span></span>
  
## <a name="general-recommendations"></a><span data-ttu-id="78297-136">Genel öneriler</span><span class="sxs-lookup"><span data-stu-id="78297-136">General recommendations</span></span>  
 <span data-ttu-id="78297-137">Birden çok iş parçacığı kullanırken aşağıdaki yönergeleri göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="78297-137">Consider the following guidelines when using multiple threads:</span></span>  
  
-   <span data-ttu-id="78297-138">Kullanmayın <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> diğer iş parçacıklarını sonlandırma için.</span><span class="sxs-lookup"><span data-stu-id="78297-138">Don't use <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> to terminate other threads.</span></span> <span data-ttu-id="78297-139">Çağırma **iptal** iş parçacığı, hangi iş parçacığı noktası bilmeden, işleme ulaştığını bir özel durum yakındır başka bir iş parçacığında olduğu.</span><span class="sxs-lookup"><span data-stu-id="78297-139">Calling **Abort** on another thread is akin to throwing an exception on that thread, without knowing what point that thread has reached in its processing.</span></span>  
  
-   <span data-ttu-id="78297-140">Kullanmayın <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> ve <xref:System.Threading.Thread.Resume%2A?displayProperty=nameWithType> birden çok iş parçacığı etkinliklerini eşitlenecek.</span><span class="sxs-lookup"><span data-stu-id="78297-140">Don't use <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> and <xref:System.Threading.Thread.Resume%2A?displayProperty=nameWithType> to synchronize the activities of multiple threads.</span></span> <span data-ttu-id="78297-141">Kullanma <xref:System.Threading.Mutex>, <xref:System.Threading.ManualResetEvent>, <xref:System.Threading.AutoResetEvent>, ve <xref:System.Threading.Monitor>.</span><span class="sxs-lookup"><span data-stu-id="78297-141">Do use <xref:System.Threading.Mutex>, <xref:System.Threading.ManualResetEvent>, <xref:System.Threading.AutoResetEvent>, and <xref:System.Threading.Monitor>.</span></span>  
  
-   <span data-ttu-id="78297-142">Programınızdan (örneğin, olayları kullanarak) ana çalışan iş parçacıklarının yürütülmesini denetlemek yok.</span><span class="sxs-lookup"><span data-stu-id="78297-142">Don't control the execution of worker threads from your main program (using events, for example).</span></span> <span data-ttu-id="78297-143">Bunun yerine, çalışan iş parçacıkları iş kullanılabilir hale gelene kadar bekleyen, yürütme ve işiniz bittiğinde, programınız diğer bölümlerini bildiren sorumlu olacak şekilde, programınız tasarlayın.</span><span class="sxs-lookup"><span data-stu-id="78297-143">Instead, design your program so that worker threads are responsible for waiting until work is available, executing it, and notifying other parts of your program when finished.</span></span> <span data-ttu-id="78297-144">İş parçacıklarını engellemez iş parçacığı havuzu iş parçacıkları kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="78297-144">If your worker threads do not block, consider using thread pool threads.</span></span> <span data-ttu-id="78297-145"><xref:System.Threading.Monitor.PulseAll%2A?displayProperty=nameWithType> Burada blok çalışan iş parçacıkları durumlarda yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="78297-145"><xref:System.Threading.Monitor.PulseAll%2A?displayProperty=nameWithType> is useful in situations where worker threads block.</span></span>  
  
-   <span data-ttu-id="78297-146">Türleri kilit nesneler olarak kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="78297-146">Don't use types as lock objects.</span></span> <span data-ttu-id="78297-147">Diğer bir deyişle, kod gibi önlemek `lock(typeof(X))` C# veya `SyncLock(GetType(X))` Visual Basic veya kullanımını <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> ile <xref:System.Type> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="78297-147">That is, avoid code such as `lock(typeof(X))` in C# or `SyncLock(GetType(X))` in Visual Basic, or the use of <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> with <xref:System.Type> objects.</span></span> <span data-ttu-id="78297-148">Verilen tür için yalnızca bir örneği var. <xref:System.Type?displayProperty=nameWithType> her uygulama etki alanı.</span><span class="sxs-lookup"><span data-stu-id="78297-148">For a given type, there is only one instance of <xref:System.Type?displayProperty=nameWithType> per application domain.</span></span> <span data-ttu-id="78297-149">Bir kilidi almak tür genel ise, kendi dışındaki kod kilitleri üzerinde kilitlenmeler için önde gelen alabilir.</span><span class="sxs-lookup"><span data-stu-id="78297-149">If the type you take a lock on is public, code other than your own can take locks on it, leading to deadlocks.</span></span> <span data-ttu-id="78297-150">Ek sorunlar için bkz: [güvenilirlik en iyi yöntemleri](../../../docs/framework/performance/reliability-best-practices.md).</span><span class="sxs-lookup"><span data-stu-id="78297-150">For additional issues, see [Reliability Best Practices](../../../docs/framework/performance/reliability-best-practices.md).</span></span>  
  
-   <span data-ttu-id="78297-151">Örneğin örneklerinde kilitleme dikkatli `lock(this)` C# veya `SyncLock(Me)` Visual Basic'te.</span><span class="sxs-lookup"><span data-stu-id="78297-151">Use caution when locking on instances, for example `lock(this)` in C# or `SyncLock(Me)` in Visual Basic.</span></span> <span data-ttu-id="78297-152">Diğer kod uygulamanızın türü için dış nesne üzerinde bir kilit alırsa, kilitlenmeleri oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="78297-152">If other code in your application, external to the type, takes a lock on the object, deadlocks could occur.</span></span>  
  
-   <span data-ttu-id="78297-153">İzleyici olsa da iş parçacığı bir özel durum oluşursa bile bir izleyici her zaman geçtiğini bir iş parçacığı bu izleyiciyi bırakır emin olun.</span><span class="sxs-lookup"><span data-stu-id="78297-153">Do ensure that a thread that has entered a monitor always leaves that monitor, even if an exception occurs while the thread is in the monitor.</span></span> <span data-ttu-id="78297-154">C# [kilit](~/docs/csharp/language-reference/keywords/lock-statement.md) deyimi ve Visual Basic [SyncLock](~/docs/visual-basic/language-reference/statements/synclock-statement.md) deyimi sağlamak bu davranışı otomatik olarak kullanan bir **son** emin olmak için blok <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType> olduğu çağrılır.</span><span class="sxs-lookup"><span data-stu-id="78297-154">The C# [lock](~/docs/csharp/language-reference/keywords/lock-statement.md) statement and the Visual Basic [SyncLock](~/docs/visual-basic/language-reference/statements/synclock-statement.md) statement provide this behavior automatically, employing a **finally** block to ensure that <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType> is called.</span></span> <span data-ttu-id="78297-155">Garanti edemez, **çıkış** çağrılır, kullanılacak tasarımınızı değiştirmeyi göz önünde bulundurun **Mutex**.</span><span class="sxs-lookup"><span data-stu-id="78297-155">If you cannot ensure that **Exit** will be called, consider changing your design to use **Mutex**.</span></span> <span data-ttu-id="78297-156">Bir mutex, şu anda sahip iş parçacığı sonlandığında otomatik olarak yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="78297-156">A mutex is automatically released when the thread that currently owns it terminates.</span></span>  
  
-   <span data-ttu-id="78297-157">Birden çok iş parçacığı farklı kaynakları gerektiren görevler için kullanabilir ve tek bir kaynak için birden çok iş parçacığı atamaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="78297-157">Do use multiple threads for tasks that require different resources, and avoid assigning multiple threads to a single resource.</span></span> <span data-ttu-id="78297-158">Örneğin, g/ç ile ilgili herhangi bir görev kendi iş parçacığı, çünkü iş parçacığı g/ç işlemleri sırasında engelleyin ve bu nedenle diğer iş parçacıklarını yürütmek izin kalmamasını fayda sağlar.</span><span class="sxs-lookup"><span data-stu-id="78297-158">For example, any task involving I/O benefits from having its own thread, because that thread will block during I/O operations and thus allow other threads to execute.</span></span> <span data-ttu-id="78297-159">Kullanıcı girişi adanmış bir iş parçacığından yarar başka bir kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="78297-159">User input is another resource that benefits from a dedicated thread.</span></span> <span data-ttu-id="78297-160">Tek işlemcili bir bilgisayarda, yoğun hesaplama içeren bir görev ve g/ç gerektiren görevleri kullanıcı girişi ile bir arada, ancak birden fazla hesaplama açısından yoğun görevleri birbiriyle azaltması.</span><span class="sxs-lookup"><span data-stu-id="78297-160">On a single-processor computer, a task that involves intensive computation coexists with user input and with tasks that involve I/O, but multiple computation-intensive tasks contend with each other.</span></span>  
  
-   <span data-ttu-id="78297-161">Yöntemlerini kullanmayı <xref:System.Threading.Interlocked> sınıf yerine basit durum değişiklikleri için `lock` deyimi (`SyncLock` Visual Basic'te).</span><span class="sxs-lookup"><span data-stu-id="78297-161">Consider using methods of the <xref:System.Threading.Interlocked> class for simple state changes, instead of using the `lock` statement (`SyncLock` in Visual Basic).</span></span> <span data-ttu-id="78297-162">`lock` Deyimi, iyi bir genel amaçlı araçtır ancak <xref:System.Threading.Interlocked> sınıfı atomik güncelleştirmeleri için daha iyi performans sağlar.</span><span class="sxs-lookup"><span data-stu-id="78297-162">The `lock` statement is a good general-purpose tool, but the <xref:System.Threading.Interlocked> class provides better performance for updates that must be atomic.</span></span> <span data-ttu-id="78297-163">Dahili olarak, hiçbir Çekişme varsa tek kilit önek yürütür.</span><span class="sxs-lookup"><span data-stu-id="78297-163">Internally, it executes a single lock prefix if there is no contention.</span></span> <span data-ttu-id="78297-164">Kod gözden geçirmeleri, kod, aşağıdaki örneklerde gösterildiği gibi izleyin.</span><span class="sxs-lookup"><span data-stu-id="78297-164">In code reviews, watch for code like that shown in the following examples.</span></span> <span data-ttu-id="78297-165">İlk örnekte, bir durum değişkeninin artırılır:</span><span class="sxs-lookup"><span data-stu-id="78297-165">In the first example, a state variable is incremented:</span></span>  
  
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
  
     <span data-ttu-id="78297-166">Kullanarak performansı artırabilirsiniz <xref:System.Threading.Interlocked.Increment%2A> yöntemi yerine `lock` aşağıdaki gibi bir deyimi:</span><span class="sxs-lookup"><span data-stu-id="78297-166">You can improve performance by using the <xref:System.Threading.Interlocked.Increment%2A> method instead of the `lock` statement, as follows:</span></span>  
  
    ```vb  
    System.Threading.Interlocked.Increment(myField)  
    ```  
  
    ```csharp  
    System.Threading.Interlocked.Increment(myField);  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="78297-167">.NET Framework 2.0 ve sonraki sürümlerinde, kullanın <xref:System.Threading.Interlocked.Add%2A> yöntemi için 1'den daha büyük atomik artırır.</span><span class="sxs-lookup"><span data-stu-id="78297-167">In the .NET Framework 2.0 and later, use the <xref:System.Threading.Interlocked.Add%2A> method for atomic increments larger than 1.</span></span>  
  
     <span data-ttu-id="78297-168">Yalnızca bir null başvuru ise ikinci örnekte, bir başvuru türü değişkeni güncelleştirilir (`Nothing` Visual Basic'te).</span><span class="sxs-lookup"><span data-stu-id="78297-168">In the second example, a reference type variable is updated only if it is a null reference (`Nothing` in Visual Basic).</span></span>  
  
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
            if (x == null)  
            {  
                x = y;  
            }  
        }  
    }  
    ```  
  
     <span data-ttu-id="78297-169">Performansı geliştirilmiş kullanarak <xref:System.Threading.Interlocked.CompareExchange%2A> yöntemi bunun yerine, şu şekilde:</span><span class="sxs-lookup"><span data-stu-id="78297-169">Performance can be improved by using the <xref:System.Threading.Interlocked.CompareExchange%2A> method instead, as follows:</span></span>  
  
    ```vb  
    System.Threading.Interlocked.CompareExchange(x, y, Nothing)  
    ```  
  
    ```csharp  
    System.Threading.Interlocked.CompareExchange(ref x, y, null);  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="78297-170">.NET Framework 2.0 ile başlayarak <xref:System.Threading.Interlocked.CompareExchange%60%601%28%60%600%40%2C%60%600%2C%60%600%29> yöntemi aşırı yüklemesi, başvuru türleri için tür kullanımı uyumlu bir alternatif sağlar.</span><span class="sxs-lookup"><span data-stu-id="78297-170">Beginning with .NET Framework 2.0, the <xref:System.Threading.Interlocked.CompareExchange%60%601%28%60%600%40%2C%60%600%2C%60%600%29> method overload provides a type-safe alternative for reference types.</span></span>
  
## <a name="recommendations-for-class-libraries"></a><span data-ttu-id="78297-171">Sınıf kitaplıkları için öneriler</span><span class="sxs-lookup"><span data-stu-id="78297-171">Recommendations for class libraries</span></span>  
 <span data-ttu-id="78297-172">Sınıf kitaplıkları için tasarlarken aşağıdaki yönergeleri göz önünde bulundurun çoklu iş parçacığı kullanımı:</span><span class="sxs-lookup"><span data-stu-id="78297-172">Consider the following guidelines when designing class libraries for multithreading:</span></span>  
  
-   <span data-ttu-id="78297-173">Eşitleme için gereken mümkün olduğunda kaçının.</span><span class="sxs-lookup"><span data-stu-id="78297-173">Avoid the need for synchronization, if possible.</span></span> <span data-ttu-id="78297-174">Bu, özellikle yoğun olarak kullanılan kod için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="78297-174">This is especially true for heavily used code.</span></span> <span data-ttu-id="78297-175">Örneğin, bir algoritma yerine bir yarış durumu tolere bunu ortadan kaldırmak için ayarlanmış.</span><span class="sxs-lookup"><span data-stu-id="78297-175">For example, an algorithm might be adjusted to tolerate a race condition rather than eliminate it.</span></span> <span data-ttu-id="78297-176">Gereksiz eşitleme performansı azaltır ve kilitlenmeler ve yarış durumları olasılığını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="78297-176">Unnecessary synchronization decreases performance and creates the possibility of deadlocks and race conditions.</span></span>  
  
-   <span data-ttu-id="78297-177">Statik veri olun (`Shared` Visual Basic'te) varsayılan olarak güvenli iş parçacığı.</span><span class="sxs-lookup"><span data-stu-id="78297-177">Make static data (`Shared` in Visual Basic) thread safe by default.</span></span>  
  
-   <span data-ttu-id="78297-178">Örnek veri iş parçacığı, varsayılan olarak güvenli yapmayın.</span><span class="sxs-lookup"><span data-stu-id="78297-178">Do not make instance data thread safe by default.</span></span> <span data-ttu-id="78297-179">İş parçacığı açısından güvenli kod oluşturmak için kilit ekleme performansınızın, kilit çakışması artırır ve kilitlenmeleri gerçekleşmesi için olasılığını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="78297-179">Adding locks to create thread-safe code decreases performance, increases lock contention, and creates the possibility for deadlocks to occur.</span></span> <span data-ttu-id="78297-180">Ortak uygulama modellerini aynı anda yalnızca bir iş parçacığının iş parçacığı güvenliği gereksinimini en aza indirir, kullanıcı kodu yürütür.</span><span class="sxs-lookup"><span data-stu-id="78297-180">In common application models, only one thread at a time executes user code, which minimizes the need for thread safety.</span></span> <span data-ttu-id="78297-181">Bu nedenle, .NET Framework sınıf kitaplıkları, varsayılan olarak güvenli iş parçacığı değildir.</span><span class="sxs-lookup"><span data-stu-id="78297-181">For this reason, the .NET Framework class libraries are not thread safe by default.</span></span>  
  
-   <span data-ttu-id="78297-182">Statik durumu alter statik yöntemler sağlayan kaçının.</span><span class="sxs-lookup"><span data-stu-id="78297-182">Avoid providing static methods that alter static state.</span></span> <span data-ttu-id="78297-183">Senaryoları sunucusu, birden çok iş parçacığı aynı anda kod yürütebilir anlamına gelir statik durumu istekler arasında paylaşılır.</span><span class="sxs-lookup"><span data-stu-id="78297-183">In common server scenarios, static state is shared across requests, which means multiple threads can execute that code at the same time.</span></span> <span data-ttu-id="78297-184">Bu hataların iş parçacığı oluşturma olasılığını açar.</span><span class="sxs-lookup"><span data-stu-id="78297-184">This opens up the possibility of threading bugs.</span></span> <span data-ttu-id="78297-185">İstekler genelinde paylaşılmaz örnekleri içine veri kapsülleyen bir tasarım desenini kullanarak göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="78297-185">Consider using a design pattern that encapsulates data into instances that are not shared across requests.</span></span> <span data-ttu-id="78297-186">Ayrıca, statik veri eşitlenmişse durumu alter statik yöntemler arasındaki çağrıların kilitlenmeleri veya performansını olumsuz yönde etkileyen yedekli eşitleme neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="78297-186">Furthermore, if static data are synchronized, calls between static methods that alter state can result in deadlocks or redundant synchronization, adversely affecting performance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78297-187">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="78297-187">See also</span></span>

- [<span data-ttu-id="78297-188">İş parçacığı oluşturma</span><span class="sxs-lookup"><span data-stu-id="78297-188">Threading</span></span>](../../../docs/standard/threading/index.md)
- [<span data-ttu-id="78297-189">İş Parçacıkları ve İş Parçacığı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="78297-189">Threads and Threading</span></span>](../../../docs/standard/threading/threads-and-threading.md)
