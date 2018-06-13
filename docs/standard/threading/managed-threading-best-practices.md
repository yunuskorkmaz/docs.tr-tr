---
title: Yönetilen İş Parçacığı Oluşturma En İyi Yöntemleri
ms.date: 11/30/2017
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
ms.openlocfilehash: 15261291f40b6a41e0d6033fb92e1b23b4042019
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33592476"
---
# <a name="managed-threading-best-practices"></a><span data-ttu-id="5a10c-102">Yönetilen İş Parçacığı Oluşturma En İyi Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="5a10c-102">Managed Threading Best Practices</span></span>
<span data-ttu-id="5a10c-103">Çoklu iş parçacığı kullanımı dikkatli programlama gerektirir.</span><span class="sxs-lookup"><span data-stu-id="5a10c-103">Multithreading requires careful programming.</span></span> <span data-ttu-id="5a10c-104">Çoğu görevlerde, karmaşıklık yürütme için sıraya alma istekleri iş parçacığı havuzu iş parçacıkları tarafından azaltabilir.</span><span class="sxs-lookup"><span data-stu-id="5a10c-104">For most tasks, you can reduce complexity by queuing requests for execution by thread pool threads.</span></span> <span data-ttu-id="5a10c-105">Bu konuda, birden çok iş parçacığı iş Eşgüdümleme veya iş parçacığı, blok işleme gibi daha zor durumlarda giderir.</span><span class="sxs-lookup"><span data-stu-id="5a10c-105">This topic addresses more difficult situations, such as coordinating the work of multiple threads, or handling threads that block.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5a10c-106">.NET Framework 4 ile başlayarak, görev paralel kitaplığı ve PLINQ'da bazı karmaşıklık ve çok iş parçacıklı programlama risklerini azaltmak API'ler sağlar.</span><span class="sxs-lookup"><span data-stu-id="5a10c-106">Starting with the .NET Framework 4, the Task Parallel Library and PLINQ provide APIs that reduce some of the complexity and risks of multi-threaded programming.</span></span> <span data-ttu-id="5a10c-107">Daha fazla bilgi için bkz: [.NET paralel programlama](../../../docs/standard/parallel-programming/index.md).</span><span class="sxs-lookup"><span data-stu-id="5a10c-107">For more information, see [Parallel Programming in .NET](../../../docs/standard/parallel-programming/index.md).</span></span>  
  
## <a name="deadlocks-and-race-conditions"></a><span data-ttu-id="5a10c-108">Kilitlenmeler ve yarış durumları</span><span class="sxs-lookup"><span data-stu-id="5a10c-108">Deadlocks and Race Conditions</span></span>  
 <span data-ttu-id="5a10c-109">Çoklu iş parçacığı kullanımı üretilen iş ve yanıt hızını sorunlarını çözer, ancak bunu yaparken yeni sorunları sunar: Kilitlenmeler ve yarış durumları.</span><span class="sxs-lookup"><span data-stu-id="5a10c-109">Multithreading solves problems with throughput and responsiveness, but in doing so it introduces new problems: deadlocks and race conditions.</span></span>  
  
### <a name="deadlocks"></a><span data-ttu-id="5a10c-110">Kilitlenmeleri</span><span class="sxs-lookup"><span data-stu-id="5a10c-110">Deadlocks</span></span>  
 <span data-ttu-id="5a10c-111">Her iki iş parçacığı diğer zaten kilitli bir kaynak kilitlemek çalıştığında bir kilitlenme oluşur.</span><span class="sxs-lookup"><span data-stu-id="5a10c-111">A deadlock occurs when each of two threads tries to lock a resource the other has already locked.</span></span> <span data-ttu-id="5a10c-112">Hiçbir iş parçacığı herhangi gelişme yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5a10c-112">Neither thread can make any further progress.</span></span>  
  
 <span data-ttu-id="5a10c-113">Yönetilen iş parçacığı sınıfların birçok yöntem kilitlenmeleri belirlemenize yardımcı olmak için zaman aşımlarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="5a10c-113">Many methods of the managed threading classes provide time-outs to help you detect deadlocks.</span></span> <span data-ttu-id="5a10c-114">Örneğin, aşağıdaki kodu adlı bir nesne üzerinde bir kilit edinmeye çalışır `lockObject`.</span><span class="sxs-lookup"><span data-stu-id="5a10c-114">For example, the following code attempts to acquire a lock on an object named `lockObject`.</span></span> <span data-ttu-id="5a10c-115">Kilit 300 milisaniye cinsinden alınıyorsa değil, <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> döndürür `false`.</span><span class="sxs-lookup"><span data-stu-id="5a10c-115">If the lock is not obtained in 300 milliseconds, <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> returns `false`.</span></span>  
  
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
  
### <a name="race-conditions"></a><span data-ttu-id="5a10c-116">Yarış durumları</span><span class="sxs-lookup"><span data-stu-id="5a10c-116">Race Conditions</span></span>  
 <span data-ttu-id="5a10c-117">Bir yarış durumu, iki veya daha fazla iş parçacığı belirli bir kod bloğu ilk ulaştığında üzerinde bir program sonucunu bağlı olduğunda oluşan bir hatadır.</span><span class="sxs-lookup"><span data-stu-id="5a10c-117">A race condition is a bug that occurs when the outcome of a program depends on which of two or more threads reaches a particular block of code first.</span></span> <span data-ttu-id="5a10c-118">Birçok kez programı çalıştırma farklı sonuçlar üretir ve belirli bir çalıştırma sonucu tahmin edilemez.</span><span class="sxs-lookup"><span data-stu-id="5a10c-118">Running the program many times produces different results, and the result of any given run cannot be predicted.</span></span>  
  
 <span data-ttu-id="5a10c-119">Bir yarış durumu basit bir örneği bir alan artırma.</span><span class="sxs-lookup"><span data-stu-id="5a10c-119">A simple example of a race condition is incrementing a field.</span></span> <span data-ttu-id="5a10c-120">Özel bir sınıf sahip olduğunu varsayın **statik** alan (**paylaşılan** Visual Basic'te) sınıfının bir örneği, kod gibi kullanılarak oluşturulan her zaman artar `objCt++;` (C#) veya `objCt += 1` () Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="5a10c-120">Suppose a class has a private **static** field (**Shared** in Visual Basic) that is incremented every time an instance of the class is created, using code such as `objCt++;` (C#) or `objCt += 1` (Visual Basic).</span></span> <span data-ttu-id="5a10c-121">Bu işlem değerinden yüklenmesini gerektirir `objCt` bir kasada, artan değeri ve de depolamak `objCt`.</span><span class="sxs-lookup"><span data-stu-id="5a10c-121">This operation requires loading the value from `objCt` into a register, incrementing the value, and storing it in `objCt`.</span></span>  
  
 <span data-ttu-id="5a10c-122">Birden çok iş parçacıklı bir uygulamada, tüm üç adımı gerçekleştiren başka bir iş parçacığı tarafından yüklenen ve değer artan bir iş parçacığı etkisiz; ilk iş parçacığı yürütme devam eder ve değerini depolar, bu raporun üzerine `objCt` değeri geçici değiştirildi olgu dikkate alarak olmadan.</span><span class="sxs-lookup"><span data-stu-id="5a10c-122">In a multithreaded application, a thread that has loaded and incremented the value might be preempted by another thread which performs all three steps; when the first thread resumes execution and stores its value, it overwrites `objCt` without taking into account the fact that the value has changed in the interim.</span></span>  
  
 <span data-ttu-id="5a10c-123">Bu belirli yarış durumu yöntemlerini kullanarak kolayca kaçınılması <xref:System.Threading.Interlocked> gibi sınıfı <xref:System.Threading.Interlocked.Increment%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5a10c-123">This particular race condition is easily avoided by using methods of the <xref:System.Threading.Interlocked> class, such as <xref:System.Threading.Interlocked.Increment%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="5a10c-124">Çoklu iş parçacıkları arasında veri eşitlemek için başka teknikler hakkında edinmek için bkz [çoklu iş parçacığı kullanımı için veri eşitleme](../../../docs/standard/threading/synchronizing-data-for-multithreading.md).</span><span class="sxs-lookup"><span data-stu-id="5a10c-124">To read about other techniques for synchronizing data among multiple threads, see [Synchronizing Data for Multithreading](../../../docs/standard/threading/synchronizing-data-for-multithreading.md).</span></span>  
  
 <span data-ttu-id="5a10c-125">Birden çok iş parçacığı etkinliklerini eşitlediğinizde yarış durumları da oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="5a10c-125">Race conditions can also occur when you synchronize the activities of multiple threads.</span></span> <span data-ttu-id="5a10c-126">Bir kod satırı yazdığınızda, ne gerçekleşebilir dikkate almanız gereken bir iş parçacığı etkisiz satır yürütmeden önce (veya çizgiyi oluşturan tek tek makine yönergeleri hiçbirini önce) ve onu başka bir iş parçacığı taşıyorduysa.</span><span class="sxs-lookup"><span data-stu-id="5a10c-126">Whenever you write a line of code, you must consider what might happen if a thread were preempted before executing the line (or before any of the individual machine instructions that make up the line), and another thread overtook it.</span></span>  
  
## <a name="number-of-processors"></a><span data-ttu-id="5a10c-127">İşlemci sayısı</span><span class="sxs-lookup"><span data-stu-id="5a10c-127">Number of Processors</span></span>  
 <span data-ttu-id="5a10c-128">Çoğu bilgisayar artık tabletler ve telefonlar gibi küçük aygıtlar bile (çekirdek da denir), birden çok işlemci yok.</span><span class="sxs-lookup"><span data-stu-id="5a10c-128">Most computers now have multiple processors (also called cores), even small devices such as tablets and phones.</span></span> <span data-ttu-id="5a10c-129">Ayrıca tek işlemcili bilgisayarlarda, farkında olmalıdır, çoklu iş parçacığı çalıştırılır yazılım geliştirirken biliyorsanız tek işlemcili bilgisayarlar ve çok işlemcili bilgisayarlar için farklı sorunu çözer.</span><span class="sxs-lookup"><span data-stu-id="5a10c-129">If you know you're developing software that will also run on single-processor computers, you should be aware that multithreading solves different problems for single-processor computers and multiprocessor computers.</span></span>  
  
### <a name="multiprocessor-computers"></a><span data-ttu-id="5a10c-130">Çok işlemcili bilgisayarlar</span><span class="sxs-lookup"><span data-stu-id="5a10c-130">Multiprocessor Computers</span></span>  
 <span data-ttu-id="5a10c-131">Çoklu iş parçacığı kullanımı büyük verimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="5a10c-131">Multithreading provides greater throughput.</span></span> <span data-ttu-id="5a10c-132">On işlemciler on kez on aynı anda çalışıyor bir yalnızca iş ayrılmıştır varsa ancak bir iş yapabilirsiniz; iş parçacığı işi bölün ve ek işlem gücü yararlanmak için kolay bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="5a10c-132">Ten processors can do ten times the work of one, but only if the work is divided so that all ten can be working at once; threads provide an easy way to divide the work and exploit the extra processing power.</span></span> <span data-ttu-id="5a10c-133">Kullanırsanız, çok işlemcili bir bilgisayarda çoklu iş parçacığı kullanımı:</span><span class="sxs-lookup"><span data-stu-id="5a10c-133">If you use multithreading on a multiprocessor computer:</span></span>  
  
-   <span data-ttu-id="5a10c-134">Aynı anda yürütülebilecek iş parçacığı sayısını işlemci sayısıyla sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="5a10c-134">The number of threads that can execute concurrently is limited by the number of processors.</span></span>  
  
-   <span data-ttu-id="5a10c-135">Yalnızca çalışan ön plan iş parçacıklarının sayısını işlemci sayısından küçük olduğunda bir arka plan iş parçacığı yürütür.</span><span class="sxs-lookup"><span data-stu-id="5a10c-135">A background thread executes only when the number of foreground threads executing is smaller than the number of processors.</span></span>  
  
-   <span data-ttu-id="5a10c-136">Çağırdığınızda <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> yöntemi bir iş parçacığı üzerinde o iş parçacığı olabilir veya işlemci sayısını ve çalıştırmak için şu anda bekleyen iş parçacığı sayısı bağlı olarak hemen yürütme başlatılamayabilir.</span><span class="sxs-lookup"><span data-stu-id="5a10c-136">When you call the <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> method on a thread, that thread might or might not start executing immediately, depending on the number of processors and the number of threads currently waiting to execute.</span></span>  
  
-   <span data-ttu-id="5a10c-137">Yarış durumları yalnızca iş parçacığı beklenmedik bir şekilde etkisiz, ancak iki farklı yürütme iş parçacıkları olduğundan işlemcileri aynı kod bloğunda ulaşması yarış çünkü oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="5a10c-137">Race conditions can occur not only because threads are preempted unexpectedly, but because two threads executing on different processors might be racing to reach the same code block.</span></span>  
  
### <a name="single-processor-computers"></a><span data-ttu-id="5a10c-138">Tek işlemcili bilgisayarlar</span><span class="sxs-lookup"><span data-stu-id="5a10c-138">Single-Processor Computers</span></span>  
 <span data-ttu-id="5a10c-139">Çoklu iş parçacığı kullanımı bilgisayar kullanıcı büyük yanıtlama hızı sağlar ve arka plan görevleri için boşta kalma süresi kullanır.</span><span class="sxs-lookup"><span data-stu-id="5a10c-139">Multithreading provides greater responsiveness to the computer user, and uses idle time for background tasks.</span></span> <span data-ttu-id="5a10c-140">Kullanırsanız, bir tek işlemcili bilgisayarda çoklu iş parçacığı kullanımı:</span><span class="sxs-lookup"><span data-stu-id="5a10c-140">If you use multithreading on a single-processor computer:</span></span>  
  
-   <span data-ttu-id="5a10c-141">Yalnızca bir iş parçacığı herhangi bir anlık çalışır.</span><span class="sxs-lookup"><span data-stu-id="5a10c-141">Only one thread runs at any instant.</span></span>  
  
-   <span data-ttu-id="5a10c-142">Arka plan iş parçacığı, yalnızca ana kullanıcı iş parçacığı boştayken çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="5a10c-142">A background thread executes only when the main user thread is idle.</span></span> <span data-ttu-id="5a10c-143">Sürekli olarak yürüten bir ön plan iş parçacığı arka plan iş parçacıkları işlemci zamanını starves.</span><span class="sxs-lookup"><span data-stu-id="5a10c-143">A foreground thread that executes constantly starves background threads of processor time.</span></span>  
  
-   <span data-ttu-id="5a10c-144">Çağırdığınızda <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> yöntemi bir iş parçacığında iş parçacığı kadar geçerli iş parçacığını yürütmek başlamıyor verir veya işletim sistemi tarafından etkisiz.</span><span class="sxs-lookup"><span data-stu-id="5a10c-144">When you call the <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> method on a thread, that thread does not start executing until the current thread yields or is preempted by the operating system.</span></span>  
  
-   <span data-ttu-id="5a10c-145">Programcı alışılmadık bir anda bir iş parçacığı etkisiz olduğunu olgu bazen kod bloğu ilk ulaşmak başka bir iş parçacığı izin verme öngörememiştir yarış durumları genellikle oluşur.</span><span class="sxs-lookup"><span data-stu-id="5a10c-145">Race conditions typically occur because the programmer did not anticipate the fact that a thread can be preempted at an awkward moment, sometimes allowing another thread to reach a code block first.</span></span>  
  
## <a name="static-members-and-static-constructors"></a><span data-ttu-id="5a10c-146">Statik üyeler ve statik oluşturucular</span><span class="sxs-lookup"><span data-stu-id="5a10c-146">Static Members and Static Constructors</span></span>  
 <span data-ttu-id="5a10c-147">Bir sınıf kadar sınıf oluşturucusu başlatılmadı (`static` C# ' ta, Oluşturucusu `Shared Sub New` Visual Basic'te) çalışması sona erdi.</span><span class="sxs-lookup"><span data-stu-id="5a10c-147">A class is not initialized until its class constructor (`static` constructor in C#, `Shared Sub New` in Visual Basic) has finished running.</span></span> <span data-ttu-id="5a10c-148">Başlatılmamış bir türündeki kodun yürütülmesini engellemek için ortak dil çalışma zamanı için diğer iş parçacıklarından tüm çağrıları engeller `static` sınıf üyeleri (`Shared` üyeleri Visual Basic'te) sınıfı oluşturucusu çalışan tamamlanana kadar.</span><span class="sxs-lookup"><span data-stu-id="5a10c-148">To prevent the execution of code on a type that is not initialized, the common language runtime blocks all calls from other threads to `static` members of the class (`Shared` members in Visual Basic) until the class constructor has finished running.</span></span>  
  
 <span data-ttu-id="5a10c-149">Örneğin, yeni bir iş parçacığı bir sınıf oluşturucu başlar ve iş parçacığı yordamı çağıran bir `static` sınıfı oluşturucusu tamamlanana kadar yeni bir iş parçacığı blokları sınıf üyesi.</span><span class="sxs-lookup"><span data-stu-id="5a10c-149">For example, if a class constructor starts a new thread, and the thread procedure calls a `static` member of the class, the new thread blocks until the class constructor completes.</span></span>  
  
 <span data-ttu-id="5a10c-150">Bu olabilir herhangi bir türü için geçerlidir bir `static` Oluşturucusu.</span><span class="sxs-lookup"><span data-stu-id="5a10c-150">This applies to any type that can have a `static` constructor.</span></span>  
  
## <a name="general-recommendations"></a><span data-ttu-id="5a10c-151">Genel öneriler</span><span class="sxs-lookup"><span data-stu-id="5a10c-151">General Recommendations</span></span>  
 <span data-ttu-id="5a10c-152">Çoklu iş parçacıkları kullanırken aşağıdaki yönergeleri göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="5a10c-152">Consider the following guidelines when using multiple threads:</span></span>  
  
-   <span data-ttu-id="5a10c-153">Kullanmayan <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> başka bir iş parçacığı sonlandırılacak.</span><span class="sxs-lookup"><span data-stu-id="5a10c-153">Don't use <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> to terminate other threads.</span></span> <span data-ttu-id="5a10c-154">Çağırma **Abort** iş parçacığı, ne o iş parçacığı noktası bilmeden kendi işleme sınırına ulaşmış olması bir özel durum atma benzer başka bir iş parçacığı üzerinde değil.</span><span class="sxs-lookup"><span data-stu-id="5a10c-154">Calling **Abort** on another thread is akin to throwing an exception on that thread, without knowing what point that thread has reached in its processing.</span></span>  
  
-   <span data-ttu-id="5a10c-155">Kullanmayan <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> ve <xref:System.Threading.Thread.Resume%2A?displayProperty=nameWithType> birden çok iş parçacığı etkinliklerini eşitlenecek.</span><span class="sxs-lookup"><span data-stu-id="5a10c-155">Don't use <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> and <xref:System.Threading.Thread.Resume%2A?displayProperty=nameWithType> to synchronize the activities of multiple threads.</span></span> <span data-ttu-id="5a10c-156">Kullanmak <xref:System.Threading.Mutex>, <xref:System.Threading.ManualResetEvent>, <xref:System.Threading.AutoResetEvent>, ve <xref:System.Threading.Monitor>.</span><span class="sxs-lookup"><span data-stu-id="5a10c-156">Do use <xref:System.Threading.Mutex>, <xref:System.Threading.ManualResetEvent>, <xref:System.Threading.AutoResetEvent>, and <xref:System.Threading.Monitor>.</span></span>  
  
-   <span data-ttu-id="5a10c-157">Çalışan iş parçacıkları (olaylar, örneğin kullanarak), ana programdan yürütülmesi denetim yok.</span><span class="sxs-lookup"><span data-stu-id="5a10c-157">Don't control the execution of worker threads from your main program (using events, for example).</span></span> <span data-ttu-id="5a10c-158">Bunun yerine, çalışan iş parçacığı iş kullanılabilir hale gelene kadar bekleyen, yürütülmekte ve diğer bölümleri bittiğinde programınızın bildiren sorumlu; böylece programınızı tasarlayın.</span><span class="sxs-lookup"><span data-stu-id="5a10c-158">Instead, design your program so that worker threads are responsible for waiting until work is available, executing it, and notifying other parts of your program when finished.</span></span> <span data-ttu-id="5a10c-159">Çalışan iş parçacığı engellemez, iş parçacığı havuzu iş parçacıkları kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="5a10c-159">If your worker threads do not block, consider using thread pool threads.</span></span> <span data-ttu-id="5a10c-160"><xref:System.Threading.Monitor.PulseAll%2A?displayProperty=nameWithType> Burada blok çalışan iş parçacıkları durumlarda faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="5a10c-160"><xref:System.Threading.Monitor.PulseAll%2A?displayProperty=nameWithType> is useful in situations where worker threads block.</span></span>  
  
-   <span data-ttu-id="5a10c-161">Türleri kilit nesneler olarak kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="5a10c-161">Don't use types as lock objects.</span></span> <span data-ttu-id="5a10c-162">Diğer bir deyişle, kod gibi kaçının `lock(typeof(X))` C# veya `SyncLock(GetType(X))` Visual Basic veya kullanımını <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> ile <xref:System.Type> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="5a10c-162">That is, avoid code such as `lock(typeof(X))` in C# or `SyncLock(GetType(X))` in Visual Basic, or the use of <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> with <xref:System.Type> objects.</span></span> <span data-ttu-id="5a10c-163">Belirli bir türde için yalnızca bir örneği var. <xref:System.Type?displayProperty=nameWithType> uygulama etki alanı başına.</span><span class="sxs-lookup"><span data-stu-id="5a10c-163">For a given type, there is only one instance of <xref:System.Type?displayProperty=nameWithType> per application domain.</span></span> <span data-ttu-id="5a10c-164">Bir kilit etkinleştirilir türü ortak ise, kendi dışındaki kod kilitleri üzerinde kilitlenmeye baştaki alabilir.</span><span class="sxs-lookup"><span data-stu-id="5a10c-164">If the type you take a lock on is public, code other than your own can take locks on it, leading to deadlocks.</span></span> <span data-ttu-id="5a10c-165">Ek sorunlar için bkz: [güvenilirlik en iyi yöntemleri](../../../docs/framework/performance/reliability-best-practices.md).</span><span class="sxs-lookup"><span data-stu-id="5a10c-165">For additional issues, see [Reliability Best Practices](../../../docs/framework/performance/reliability-best-practices.md).</span></span>  
  
-   <span data-ttu-id="5a10c-166">Örneklerinde, örneğin kilitleme dikkatli `lock(this)` C# veya `SyncLock(Me)` Visual Basic'te.</span><span class="sxs-lookup"><span data-stu-id="5a10c-166">Use caution when locking on instances, for example `lock(this)` in C# or `SyncLock(Me)` in Visual Basic.</span></span> <span data-ttu-id="5a10c-167">Diğer kodu, uygulamanızda türüne dış nesne üzerinde bir kilit alırsa, kilitlenmeleri meydana gelebilir.</span><span class="sxs-lookup"><span data-stu-id="5a10c-167">If other code in your application, external to the type, takes a lock on the object, deadlocks could occur.</span></span>  
  
-   <span data-ttu-id="5a10c-168">İş parçacığı İzleyicisi'nde olsa da bir özel durum oluşursa bile bir izleyici her zaman geçtiğini bir iş parçacığı bu İzleyici bırakır emin olun.</span><span class="sxs-lookup"><span data-stu-id="5a10c-168">Do ensure that a thread that has entered a monitor always leaves that monitor, even if an exception occurs while the thread is in the monitor.</span></span> <span data-ttu-id="5a10c-169">C# [kilit](~/docs/csharp/language-reference/keywords/lock-statement.md) deyimi ve Visual Basic [SyncLock](~/docs/visual-basic/language-reference/statements/synclock-statement.md) deyimi sağlamak Bu davranış otomatik olarak kullanan bir **son** emin olmak için blok <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType> olduğu çağrılır.</span><span class="sxs-lookup"><span data-stu-id="5a10c-169">The C# [lock](~/docs/csharp/language-reference/keywords/lock-statement.md) statement and the Visual Basic [SyncLock](~/docs/visual-basic/language-reference/statements/synclock-statement.md) statement provide this behavior automatically, employing a **finally** block to ensure that <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType> is called.</span></span> <span data-ttu-id="5a10c-170">Garanti edemez, **çıkış** çağrılacağı, kullanılacak tasarımınızı değiştirmeyi göz önünde bulundurun **Mutex**.</span><span class="sxs-lookup"><span data-stu-id="5a10c-170">If you cannot ensure that **Exit** will be called, consider changing your design to use **Mutex**.</span></span> <span data-ttu-id="5a10c-171">Şu anda sahip iş parçacığı sonlandırıldığında bir mutex otomatik olarak yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="5a10c-171">A mutex is automatically released when the thread that currently owns it terminates.</span></span>  
  
-   <span data-ttu-id="5a10c-172">Farklı kaynaklar gerektiren görevler için birden çok iş parçacığı kullanın ve birden çok iş parçacığı için tek kaynak atamaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="5a10c-172">Do use multiple threads for tasks that require different resources, and avoid assigning multiple threads to a single resource.</span></span> <span data-ttu-id="5a10c-173">Örneğin, g/ç içeren herhangi bir görev kendi iş parçacığı, çünkü o iş parçacığı g/ç işlemleri sırasında engellemek ve böylece yürütmek başka bir iş parçacığı izin kalmaktan fayda sağlar.</span><span class="sxs-lookup"><span data-stu-id="5a10c-173">For example, any task involving I/O benefits from having its own thread, because that thread will block during I/O operations and thus allow other threads to execute.</span></span> <span data-ttu-id="5a10c-174">Kullanıcı girişi adanmış bir iş parçacığından avantaj başka bir kaynak değil.</span><span class="sxs-lookup"><span data-stu-id="5a10c-174">User input is another resource that benefits from a dedicated thread.</span></span> <span data-ttu-id="5a10c-175">Bir tek işlemcili bilgisayarda yoğun hesaplama içeren bir görev g/ç ile ilgili görevleri ve kullanıcı girişi ile birlikte var, ancak birden fazla hesaplama yoğunluklu görevleri birbiriyle yüklüyorsa.</span><span class="sxs-lookup"><span data-stu-id="5a10c-175">On a single-processor computer, a task that involves intensive computation coexists with user input and with tasks that involve I/O, but multiple computation-intensive tasks contend with each other.</span></span>  
  
-   <span data-ttu-id="5a10c-176">Yöntemleri kullanmayı <xref:System.Threading.Interlocked> kullanmak yerine basit durum değişiklikleri için sınıf `lock` deyimi (`SyncLock` Visual Basic'te).</span><span class="sxs-lookup"><span data-stu-id="5a10c-176">Consider using methods of the <xref:System.Threading.Interlocked> class for simple state changes, instead of using the `lock` statement (`SyncLock` in Visual Basic).</span></span> <span data-ttu-id="5a10c-177">`lock` Açıklamadır iyi genel amaçlı bir aracı, ancak <xref:System.Threading.Interlocked> sınıfı atomik güncelleştirmeler için daha iyi performans sağlar.</span><span class="sxs-lookup"><span data-stu-id="5a10c-177">The `lock` statement is a good general-purpose tool, but the <xref:System.Threading.Interlocked> class provides better performance for updates that must be atomic.</span></span> <span data-ttu-id="5a10c-178">Dahili olarak, hiçbir Çekişme varsa tek kilit önek yürütür.</span><span class="sxs-lookup"><span data-stu-id="5a10c-178">Internally, it executes a single lock prefix if there is no contention.</span></span> <span data-ttu-id="5a10c-179">Aşağıdaki örneklerde gösterildiği gibi kodu için kod incelemeleri içinde izleyin.</span><span class="sxs-lookup"><span data-stu-id="5a10c-179">In code reviews, watch for code like that shown in the following examples.</span></span> <span data-ttu-id="5a10c-180">Bu örnekte, bir durum değişkeninin artırılır:</span><span class="sxs-lookup"><span data-stu-id="5a10c-180">In the first example, a state variable is incremented:</span></span>  
  
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
  
     <span data-ttu-id="5a10c-181">Kullanarak performansı artırabilir <xref:System.Threading.Interlocked.Increment%2A> yöntemi yerine `lock` şekilde deyimi:</span><span class="sxs-lookup"><span data-stu-id="5a10c-181">You can improve performance by using the <xref:System.Threading.Interlocked.Increment%2A> method instead of the `lock` statement, as follows:</span></span>  
  
    ```vb  
    System.Threading.Interlocked.Increment(myField)  
    ```  
  
    ```csharp  
    System.Threading.Interlocked.Increment(myField);  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="5a10c-182">.NET Framework sürüm 2.0, <xref:System.Threading.Interlocked.Add%2A> yöntemi 1'den büyük artışlarla atomik güncelleştirmeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="5a10c-182">In the .NET Framework version 2.0, the <xref:System.Threading.Interlocked.Add%2A> method provides atomic updates in increments larger than 1.</span></span>  
  
     <span data-ttu-id="5a10c-183">Yalnızca bir null başvuru ise ikinci örnekte, bir başvuru türü değişkeni güncelleştirilir (`Nothing` Visual Basic'te).</span><span class="sxs-lookup"><span data-stu-id="5a10c-183">In the second example, a reference type variable is updated only if it is a null reference (`Nothing` in Visual Basic).</span></span>  
  
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
  
     <span data-ttu-id="5a10c-184">Performans geliştirilmiş kullanarak <xref:System.Threading.Interlocked.CompareExchange%2A> yöntemi bunun yerine, aşağıdaki gibi:</span><span class="sxs-lookup"><span data-stu-id="5a10c-184">Performance can be improved by using the <xref:System.Threading.Interlocked.CompareExchange%2A> method instead, as follows:</span></span>  
  
    ```vb  
    System.Threading.Interlocked.CompareExchange(x, y, Nothing)  
    ```  
  
    ```csharp  
    System.Threading.Interlocked.CompareExchange(ref x, y, null);  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="5a10c-185">.NET Framework sürüm 2.0, <xref:System.Threading.Interlocked.CompareExchange%2A> yöntemi herhangi bir başvuru türü tür kullanımı uyumlu yapabilmek için kullanılabilir bir genel aşırı sahiptir.</span><span class="sxs-lookup"><span data-stu-id="5a10c-185">In the .NET Framework version 2.0, the <xref:System.Threading.Interlocked.CompareExchange%2A> method has a generic overload that can be used for type-safe replacement of any reference type.</span></span>  
  
## <a name="recommendations-for-class-libraries"></a><span data-ttu-id="5a10c-186">Sınıf kitaplıkları için öneriler</span><span class="sxs-lookup"><span data-stu-id="5a10c-186">Recommendations for Class Libraries</span></span>  
 <span data-ttu-id="5a10c-187">Sınıf kitaplıkları için tasarlarken aşağıdaki yönergeleri dikkate alın çoklu iş parçacığı kullanımı:</span><span class="sxs-lookup"><span data-stu-id="5a10c-187">Consider the following guidelines when designing class libraries for multithreading:</span></span>  
  
-   <span data-ttu-id="5a10c-188">Eşitleme, gereksinimini mümkünse kaçının.</span><span class="sxs-lookup"><span data-stu-id="5a10c-188">Avoid the need for synchronization, if possible.</span></span> <span data-ttu-id="5a10c-189">Bu, özellikle yoğun olarak kullanılan kod için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="5a10c-189">This is especially true for heavily used code.</span></span> <span data-ttu-id="5a10c-190">Örneğin, bir algoritma yerine bir yarış durumu tolerans onu ortadan kaldırmak için ayarlanmış.</span><span class="sxs-lookup"><span data-stu-id="5a10c-190">For example, an algorithm might be adjusted to tolerate a race condition rather than eliminate it.</span></span> <span data-ttu-id="5a10c-191">Gereksiz eşitleme performansı düşürür ve kilitlenmeler ve yarış durumları olasılığını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5a10c-191">Unnecessary synchronization decreases performance and creates the possibility of deadlocks and race conditions.</span></span>  
  
-   <span data-ttu-id="5a10c-192">Statik verileri yap (`Shared` Visual Basic'te) varsayılan olarak güvenli iş parçacığı.</span><span class="sxs-lookup"><span data-stu-id="5a10c-192">Make static data (`Shared` in Visual Basic) thread safe by default.</span></span>  
  
-   <span data-ttu-id="5a10c-193">Örnek veri iş parçacığı varsayılan olarak güvenli yapmayın.</span><span class="sxs-lookup"><span data-stu-id="5a10c-193">Do not make instance data thread safe by default.</span></span> <span data-ttu-id="5a10c-194">İş parçacığı kodu oluşturmak için kilitler ekleme performans azaltır, kilit çakışması artırır ve gerçekleşmesi kilitlenmeleri olasılığı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5a10c-194">Adding locks to create thread-safe code decreases performance, increases lock contention, and creates the possibility for deadlocks to occur.</span></span> <span data-ttu-id="5a10c-195">Ortak uygulama modelleri, aynı anda yalnızca bir iş parçacığı iş parçacığı güvenliği gereksinimini en aza indirir kullanıcı kodu yürütür.</span><span class="sxs-lookup"><span data-stu-id="5a10c-195">In common application models, only one thread at a time executes user code, which minimizes the need for thread safety.</span></span> <span data-ttu-id="5a10c-196">Bu nedenle, .NET Framework sınıf kitaplıkları iş parçacığı varsayılan olarak güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="5a10c-196">For this reason, the .NET Framework class libraries are not thread safe by default.</span></span>  
  
-   <span data-ttu-id="5a10c-197">Statik durumu alter statik yöntemler sağlayan kaçının.</span><span class="sxs-lookup"><span data-stu-id="5a10c-197">Avoid providing static methods that alter static state.</span></span> <span data-ttu-id="5a10c-198">Yaygın olarak kullanılan sunucu senaryosu, birden çok iş parçacığı aynı anda kod yürütebilir anlamına gelir statik durumu istekler arasında paylaşılır.</span><span class="sxs-lookup"><span data-stu-id="5a10c-198">In common server scenarios, static state is shared across requests, which means multiple threads can execute that code at the same time.</span></span> <span data-ttu-id="5a10c-199">Bu hataların iş parçacığı oluşturma olasılığını açar.</span><span class="sxs-lookup"><span data-stu-id="5a10c-199">This opens up the possibility of threading bugs.</span></span> <span data-ttu-id="5a10c-200">Veri istekler arasında paylaşılmayan örnekleri halinde yalıtan bir tasarım deseni kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="5a10c-200">Consider using a design pattern that encapsulates data into instances that are not shared across requests.</span></span> <span data-ttu-id="5a10c-201">Ayrıca, statik verileri eşitlenirse durumu alter statik yöntemler arasındaki çağrıları kilitlenmeleri veya performansını olumsuz yönde etkileyen yedekli eşitleme neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="5a10c-201">Furthermore, if static data are synchronized, calls between static methods that alter state can result in deadlocks or redundant synchronization, adversely affecting performance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a10c-202">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5a10c-202">See Also</span></span>  
 [<span data-ttu-id="5a10c-203">İş parçacığı oluşturma</span><span class="sxs-lookup"><span data-stu-id="5a10c-203">Threading</span></span>](../../../docs/standard/threading/index.md)  
 [<span data-ttu-id="5a10c-204">İş Parçacıkları ve İş Parçacığı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="5a10c-204">Threads and Threading</span></span>](../../../docs/standard/threading/threads-and-threading.md)
