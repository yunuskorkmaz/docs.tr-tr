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
ms.openlocfilehash: 30d746d739654ecad2b485b9d69cfe300caca2ff
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291194"
---
# <a name="managed-threading-best-practices"></a><span data-ttu-id="5a739-102">Yönetilen iş parçacığı en iyi uygulamaları</span><span class="sxs-lookup"><span data-stu-id="5a739-102">Managed threading best practices</span></span>
<span data-ttu-id="5a739-103">Çoklu iş parçacığı dikkatli bir programlama gerektirir.</span><span class="sxs-lookup"><span data-stu-id="5a739-103">Multithreading requires careful programming.</span></span> <span data-ttu-id="5a739-104">Çoğu görev için, iş parçacığı havuzu iş parçacıklarının yürütülmesi için istekleri sıraya alarak karmaşıklığı azaltabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5a739-104">For most tasks, you can reduce complexity by queuing requests for execution by thread pool threads.</span></span> <span data-ttu-id="5a739-105">Bu konu, birden çok iş parçacığının çalışmasını koordine etme ya da engelleyen iş parçacıklarını işleme gibi daha zor durumları ele almaktadır.</span><span class="sxs-lookup"><span data-stu-id="5a739-105">This topic addresses more difficult situations, such as coordinating the work of multiple threads, or handling threads that block.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5a739-106">.NET Framework 4 ' te başlayarak, paralel kitaplığı ve PLıNQ görevi, çok iş parçacıklı programlamaya ait karmaşıklığın ve risklerden bazılarını azaltan API 'Ler sağlar.</span><span class="sxs-lookup"><span data-stu-id="5a739-106">Starting with the .NET Framework 4, the Task Parallel Library and PLINQ provide APIs that reduce some of the complexity and risks of multi-threaded programming.</span></span> <span data-ttu-id="5a739-107">Daha fazla bilgi için bkz. [.net 'Te paralel programlama](../parallel-programming/index.md).</span><span class="sxs-lookup"><span data-stu-id="5a739-107">For more information, see [Parallel Programming in .NET](../parallel-programming/index.md).</span></span>  
  
## <a name="deadlocks-and-race-conditions"></a><span data-ttu-id="5a739-108">Kilitlenmeler ve yarış koşulları</span><span class="sxs-lookup"><span data-stu-id="5a739-108">Deadlocks and race conditions</span></span>  
 <span data-ttu-id="5a739-109">Çoklu iş parçacığı işleme ve yanıt verme sorunlarını çözer, ancak bunu yaparken yeni sorunlar ortaya koymaktadır: Kilitlenmeler ve yarış koşulları.</span><span class="sxs-lookup"><span data-stu-id="5a739-109">Multithreading solves problems with throughput and responsiveness, but in doing so it introduces new problems: deadlocks and race conditions.</span></span>  
  
### <a name="deadlocks"></a><span data-ttu-id="5a739-110">Çık</span><span class="sxs-lookup"><span data-stu-id="5a739-110">Deadlocks</span></span>  
 <span data-ttu-id="5a739-111">İki iş parçacığının her biri zaten kilitlediği bir kaynağı kilitlemeyi denediğinde bir kilitlenme oluşur.</span><span class="sxs-lookup"><span data-stu-id="5a739-111">A deadlock occurs when each of two threads tries to lock a resource the other has already locked.</span></span> <span data-ttu-id="5a739-112">Ne iş parçacığı başka bir işlem yapabilir.</span><span class="sxs-lookup"><span data-stu-id="5a739-112">Neither thread can make any further progress.</span></span>  
  
 <span data-ttu-id="5a739-113">Yönetilen iş parçacığı sınıflarının birçok yöntemi, kilitlenmeleri tespit etmenize yardımcı olmak için zaman aşımı sağlar.</span><span class="sxs-lookup"><span data-stu-id="5a739-113">Many methods of the managed threading classes provide time-outs to help you detect deadlocks.</span></span> <span data-ttu-id="5a739-114">Örneğin, aşağıdaki kod adlı bir nesne üzerinde bir kilit edinmeye çalışır `lockObject` .</span><span class="sxs-lookup"><span data-stu-id="5a739-114">For example, the following code attempts to acquire a lock on an object named `lockObject`.</span></span> <span data-ttu-id="5a739-115">Kilit 300 milisaniye içinde alınamıyorsa, <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> döndürür `false` .</span><span class="sxs-lookup"><span data-stu-id="5a739-115">If the lock is not obtained in 300 milliseconds, <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> returns `false`.</span></span>  
  
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
  
### <a name="race-conditions"></a><span data-ttu-id="5a739-116">Yarış durumları</span><span class="sxs-lookup"><span data-stu-id="5a739-116">Race conditions</span></span>  
 <span data-ttu-id="5a739-117">Yarış durumu, bir programın sonucu, ilk olarak iki veya daha fazla iş parçacığının belirli bir kod bloğuna eriştiği durumlarda oluşan hatadır.</span><span class="sxs-lookup"><span data-stu-id="5a739-117">A race condition is a bug that occurs when the outcome of a program depends on which of two or more threads reaches a particular block of code first.</span></span> <span data-ttu-id="5a739-118">Programı birçok kez çalıştırmak farklı sonuçlar üretir ve belirli bir çalıştırmanın sonucu tahmin edilemez.</span><span class="sxs-lookup"><span data-stu-id="5a739-118">Running the program many times produces different results, and the result of any given run cannot be predicted.</span></span>  
  
 <span data-ttu-id="5a739-119">Yarış koşulunun basit bir örneği bir alanı artırdığında.</span><span class="sxs-lookup"><span data-stu-id="5a739-119">A simple example of a race condition is incrementing a field.</span></span> <span data-ttu-id="5a739-120">Bir sınıfın bir örneği oluşturulduğunda (Visual Basic**paylaşılan** ), **static** `objCt++;` (C#) veya `objCt += 1` (Visual Basic) gibi bir kod kullanarak, sınıfın bir örneği oluşturulduğu her seferinde artan bir özel statik alana sahip olduğunu varsayalım.</span><span class="sxs-lookup"><span data-stu-id="5a739-120">Suppose a class has a private **static** field (**Shared** in Visual Basic) that is incremented every time an instance of the class is created, using code such as `objCt++;` (C#) or `objCt += 1` (Visual Basic).</span></span> <span data-ttu-id="5a739-121">Bu işlem, değeri `objCt` bir kayda yüklemeyi, değeri arttırmanızı ve içinde depolamayı gerektirir `objCt` .</span><span class="sxs-lookup"><span data-stu-id="5a739-121">This operation requires loading the value from `objCt` into a register, incrementing the value, and storing it in `objCt`.</span></span>  
  
 <span data-ttu-id="5a739-122">Çok iş parçacıklı bir uygulamada, değeri yüklemiş ve arttırılan bir iş parçacığı, üç adımı da gerçekleştiren başka bir iş parçacığı tarafından önlenebilir. ilk iş parçacığı yürütmeyi sürdürür ve değerini depoladığında `objCt` değeri, değerin geçici olarak değiştiğini dikkate almadan geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="5a739-122">In a multithreaded application, a thread that has loaded and incremented the value might be preempted by another thread which performs all three steps; when the first thread resumes execution and stores its value, it overwrites `objCt` without taking into account the fact that the value has changed in the interim.</span></span>  
  
 <span data-ttu-id="5a739-123">Bu belirli yarış durumu, sınıfının yöntemleri kullanılarak kolayca kaçınılmaz <xref:System.Threading.Interlocked> <xref:System.Threading.Interlocked.Increment%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="5a739-123">This particular race condition is easily avoided by using methods of the <xref:System.Threading.Interlocked> class, such as <xref:System.Threading.Interlocked.Increment%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="5a739-124">Birden çok iş parçacığı arasında verileri eşitlemeye yönelik diğer teknikler hakkında bilgi edinmek için bkz. [Çoklu Iş parçacıklı verileri eşitleme](synchronizing-data-for-multithreading.md).</span><span class="sxs-lookup"><span data-stu-id="5a739-124">To read about other techniques for synchronizing data among multiple threads, see [Synchronizing Data for Multithreading](synchronizing-data-for-multithreading.md).</span></span>  
  
 <span data-ttu-id="5a739-125">Yarış durumları, birden çok iş parçacığının etkinliklerini eşitlediğinizde de gerçekleşebilir.</span><span class="sxs-lookup"><span data-stu-id="5a739-125">Race conditions can also occur when you synchronize the activities of multiple threads.</span></span> <span data-ttu-id="5a739-126">Her bir kod satırı yazdığınızda, bir iş parçacığının satırı yürütmeden önce (veya satırı oluşturan tek bir makine yönergelerinden önce) önceden atıldıktan sonra ne olabileceğini göz önünde bulundurmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="5a739-126">Whenever you write a line of code, you must consider what might happen if a thread were preempted before executing the line (or before any of the individual machine instructions that make up the line), and another thread overtook it.</span></span>  
  
## <a name="static-members-and-static-constructors"></a><span data-ttu-id="5a739-127">Statik üyeler ve statik oluşturucular</span><span class="sxs-lookup"><span data-stu-id="5a739-127">Static members and static constructors</span></span>  
 <span data-ttu-id="5a739-128">Sınıf Oluşturucusu (C# ' deki `static` oluşturucu `Shared Sub New` Visual Basic) çalışmayı bitirene kadar bir sınıf başlatılmaz.</span><span class="sxs-lookup"><span data-stu-id="5a739-128">A class is not initialized until its class constructor (`static` constructor in C#, `Shared Sub New` in Visual Basic) has finished running.</span></span> <span data-ttu-id="5a739-129">Başlatılmamış bir türdeki kodun yürütülmesini engellemek için, ortak dil çalışma zamanı, sınıf oluşturucusunun çalışmayı bitirene kadar diğer iş parçacıklarından gelen tüm çağrıları `static` sınıf üyelerine ( `Shared` Visual Basic Üyeler) engeller.</span><span class="sxs-lookup"><span data-stu-id="5a739-129">To prevent the execution of code on a type that is not initialized, the common language runtime blocks all calls from other threads to `static` members of the class (`Shared` members in Visual Basic) until the class constructor has finished running.</span></span>  
  
 <span data-ttu-id="5a739-130">Örneğin, bir sınıf Oluşturucusu yeni bir iş parçacığı başlatır ve iş parçacığı yordamı sınıfının bir üyesini çağırırsa `static` , sınıf oluşturucusu tamamlanana kadar yeni iş parçacığı engeller.</span><span class="sxs-lookup"><span data-stu-id="5a739-130">For example, if a class constructor starts a new thread, and the thread procedure calls a `static` member of the class, the new thread blocks until the class constructor completes.</span></span>  
  
 <span data-ttu-id="5a739-131">Bu, Oluşturucusu olan herhangi bir tür için geçerlidir `static` .</span><span class="sxs-lookup"><span data-stu-id="5a739-131">This applies to any type that can have a `static` constructor.</span></span>  

## <a name="number-of-processors"></a><span data-ttu-id="5a739-132">İşlemci sayısı</span><span class="sxs-lookup"><span data-stu-id="5a739-132">Number of processors</span></span>

<span data-ttu-id="5a739-133">Birden çok işlemci olup olmadığı veya sistemde yalnızca bir işlemcinin kullanılabilir olması çok iş parçacıklı mimariyi etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="5a739-133">Whether there are multiple processors or only one processor available on a system can influence multithreaded architecture.</span></span> <span data-ttu-id="5a739-134">Daha fazla bilgi için bkz. [Işlemci sayısı](https://docs.microsoft.com/previous-versions/dotnet/netframework-1.1/1c9txz50(v%3dvs.71)#number-of-processors).</span><span class="sxs-lookup"><span data-stu-id="5a739-134">For more information, see [Number of Processors](https://docs.microsoft.com/previous-versions/dotnet/netframework-1.1/1c9txz50(v%3dvs.71)#number-of-processors).</span></span>

<span data-ttu-id="5a739-135"><xref:System.Environment.ProcessorCount?displayProperty=nameWithType>Çalışma zamanında kullanılabilir işlemcilerin sayısını öğrenmek için özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="5a739-135">Use the <xref:System.Environment.ProcessorCount?displayProperty=nameWithType> property to determine the number of processors available at run time.</span></span>
  
## <a name="general-recommendations"></a><span data-ttu-id="5a739-136">Genel öneriler</span><span class="sxs-lookup"><span data-stu-id="5a739-136">General recommendations</span></span>  
 <span data-ttu-id="5a739-137">Birden çok iş parçacığı kullanırken aşağıdaki yönergeleri göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="5a739-137">Consider the following guidelines when using multiple threads:</span></span>  
  
- <span data-ttu-id="5a739-138"><xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>Diğer iş parçacıklarını sonlandırmak için kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="5a739-138">Don't use <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> to terminate other threads.</span></span> <span data-ttu-id="5a739-139">Başka bir iş parçacığında **iptali** çağırmak, bu iş parçacığı üzerinde bir özel durum oluşturmak için, iş parçacığının işleme göre hangi noktaya ulaşılmadığını bilmeksizin kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="5a739-139">Calling **Abort** on another thread is akin to throwing an exception on that thread, without knowing what point that thread has reached in its processing.</span></span>  
  
- <span data-ttu-id="5a739-140"><xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> <xref:System.Threading.Thread.Resume%2A?displayProperty=nameWithType> Birden çok iş parçacığının etkinliklerini eşitlememe ve kullanma.</span><span class="sxs-lookup"><span data-stu-id="5a739-140">Don't use <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> and <xref:System.Threading.Thread.Resume%2A?displayProperty=nameWithType> to synchronize the activities of multiple threads.</span></span> <span data-ttu-id="5a739-141">,, <xref:System.Threading.Mutex> <xref:System.Threading.ManualResetEvent> Ve kullanın <xref:System.Threading.AutoResetEvent> <xref:System.Threading.Monitor> .</span><span class="sxs-lookup"><span data-stu-id="5a739-141">Do use <xref:System.Threading.Mutex>, <xref:System.Threading.ManualResetEvent>, <xref:System.Threading.AutoResetEvent>, and <xref:System.Threading.Monitor>.</span></span>  
  
- <span data-ttu-id="5a739-142">Ana programınızdaki çalışan iş parçacıklarının yürütülmesini denetleme (örneğin, olayları kullanarak).</span><span class="sxs-lookup"><span data-stu-id="5a739-142">Don't control the execution of worker threads from your main program (using events, for example).</span></span> <span data-ttu-id="5a739-143">Bunun yerine, programınızı, çalışan iş parçacıklarının iş için kullanılabilir olana kadar beklemekten sorumlu olması, yürütülmesi ve işiniz bittiğinde programınızın diğer bölümlerine bildirimde bulunmak için tasarlayın.</span><span class="sxs-lookup"><span data-stu-id="5a739-143">Instead, design your program so that worker threads are responsible for waiting until work is available, executing it, and notifying other parts of your program when finished.</span></span> <span data-ttu-id="5a739-144">Çalışan iş parçacılarınız engellenmiyor ise, iş parçacığı havuzu iş parçacıklarını kullanmayı göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="5a739-144">If your worker threads do not block, consider using thread pool threads.</span></span> <span data-ttu-id="5a739-145"><xref:System.Threading.Monitor.PulseAll%2A?displayProperty=nameWithType>, çalışan iş parçacıklarının engel olduğu durumlarda faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="5a739-145"><xref:System.Threading.Monitor.PulseAll%2A?displayProperty=nameWithType> is useful in situations where worker threads block.</span></span>  
  
- <span data-ttu-id="5a739-146">Türleri kilit nesneleri olarak kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="5a739-146">Don't use types as lock objects.</span></span> <span data-ttu-id="5a739-147">Diğer bir deyişle, `lock(typeof(X))` C# veya Visual Basic gibi koddan `SyncLock(GetType(X))` ya da <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> nesneleri ile kullanımını önleyin <xref:System.Type> .</span><span class="sxs-lookup"><span data-stu-id="5a739-147">That is, avoid code such as `lock(typeof(X))` in C# or `SyncLock(GetType(X))` in Visual Basic, or the use of <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> with <xref:System.Type> objects.</span></span> <span data-ttu-id="5a739-148">Belirli bir tür için, <xref:System.Type?displayProperty=nameWithType> uygulama etki alanı başına yalnızca bir örnek vardır.</span><span class="sxs-lookup"><span data-stu-id="5a739-148">For a given type, there is only one instance of <xref:System.Type?displayProperty=nameWithType> per application domain.</span></span> <span data-ttu-id="5a739-149">Bir kilidi aldığınız tür herkese açık ise, kendi dışında bir kod, kilitlenmeleri için bir kilit alabilir.</span><span class="sxs-lookup"><span data-stu-id="5a739-149">If the type you take a lock on is public, code other than your own can take locks on it, leading to deadlocks.</span></span> <span data-ttu-id="5a739-150">Ek sorunlar için bkz. [Güvenilirlik En Iyi uygulamaları](../../framework/performance/reliability-best-practices.md).</span><span class="sxs-lookup"><span data-stu-id="5a739-150">For additional issues, see [Reliability Best Practices](../../framework/performance/reliability-best-practices.md).</span></span>  
  
- <span data-ttu-id="5a739-151">Örneğin, C# veya Visual Basic gibi örneklerde kilitleme yaparken dikkatli olun `lock(this)` `SyncLock(Me)` .</span><span class="sxs-lookup"><span data-stu-id="5a739-151">Use caution when locking on instances, for example `lock(this)` in C# or `SyncLock(Me)` in Visual Basic.</span></span> <span data-ttu-id="5a739-152">Uygulamanızdaki diğer kod, türü dışında, nesne üzerinde bir kilit alırsa, kilitlenmeler meydana gelebilir.</span><span class="sxs-lookup"><span data-stu-id="5a739-152">If other code in your application, external to the type, takes a lock on the object, deadlocks could occur.</span></span>  
  
- <span data-ttu-id="5a739-153">İş parçacığı izleyicisinde olduğunda bir özel durum olsa bile, bir izleyici girmiş olan bir iş parçacığının her zaman bu izleyiciden ayrılmasından emin olun.</span><span class="sxs-lookup"><span data-stu-id="5a739-153">Do ensure that a thread that has entered a monitor always leaves that monitor, even if an exception occurs while the thread is in the monitor.</span></span> <span data-ttu-id="5a739-154">C# [Lock](../../csharp/language-reference/keywords/lock-statement.md) ve Visual Basic [SyncLock](../../visual-basic/language-reference/statements/synclock-statement.md) deyimleri, bir **finally** bloğu kullanarak bu davranışı otomatik olarak sağlar <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="5a739-154">The C# [lock](../../csharp/language-reference/keywords/lock-statement.md) statement and the Visual Basic [SyncLock](../../visual-basic/language-reference/statements/synclock-statement.md) statement provide this behavior automatically, employing a **finally** block to ensure that <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType> is called.</span></span> <span data-ttu-id="5a739-155">**Çıkış** çağrısı yapıldığından emin değilseniz, tasarımınızı **mutex**kullanacak şekilde değiştirmeyi düşünün.</span><span class="sxs-lookup"><span data-stu-id="5a739-155">If you cannot ensure that **Exit** will be called, consider changing your design to use **Mutex**.</span></span> <span data-ttu-id="5a739-156">Şu anda sahibi olan iş parçacığı sonlandırıldığında bir mutex otomatik olarak serbest bırakılır.</span><span class="sxs-lookup"><span data-stu-id="5a739-156">A mutex is automatically released when the thread that currently owns it terminates.</span></span>  
  
- <span data-ttu-id="5a739-157">Farklı kaynaklar gerektiren görevler için birden çok iş parçacığı kullanın ve tek bir kaynağa birden çok iş parçacığı atamaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="5a739-157">Do use multiple threads for tasks that require different resources, and avoid assigning multiple threads to a single resource.</span></span> <span data-ttu-id="5a739-158">Örneğin, iş parçacığı g/ç işlemleri sırasında engelleyecağından ve bu nedenle diğer iş parçacıklarının yürütülmesine izin vereceğinden, g/ç 'nin sağladığı her türlü görev kendi iş parçacığına sahip olur.</span><span class="sxs-lookup"><span data-stu-id="5a739-158">For example, any task involving I/O benefits from having its own thread, because that thread will block during I/O operations and thus allow other threads to execute.</span></span> <span data-ttu-id="5a739-159">Kullanıcı girişi, adanmış bir iş parçacığından faydalanan başka bir kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="5a739-159">User input is another resource that benefits from a dedicated thread.</span></span> <span data-ttu-id="5a739-160">Tek işlemcili bir bilgisayarda, Kullanıcı girişiyle ve g/ç içeren görevlerle yoğun bir hesaplama birlikte bulunur, ancak birden fazla hesaplama yoğun görev, birbirleriyle devam eden bir görevdir.</span><span class="sxs-lookup"><span data-stu-id="5a739-160">On a single-processor computer, a task that involves intensive computation coexists with user input and with tasks that involve I/O, but multiple computation-intensive tasks contend with each other.</span></span>  
  
- <span data-ttu-id="5a739-161"><xref:System.Threading.Interlocked>İfadesini kullanmak yerine, basit durum değişiklikleri için sınıfın yöntemlerini kullanmayı düşünün `lock` ( `SyncLock` Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="5a739-161">Consider using methods of the <xref:System.Threading.Interlocked> class for simple state changes, instead of using the `lock` statement (`SyncLock` in Visual Basic).</span></span> <span data-ttu-id="5a739-162">`lock`İfade, iyi bir genel amaçlı araçtır, ancak <xref:System.Threading.Interlocked> sınıfı atomik olması gereken güncelleştirmeler için daha iyi performans sağlar.</span><span class="sxs-lookup"><span data-stu-id="5a739-162">The `lock` statement is a good general-purpose tool, but the <xref:System.Threading.Interlocked> class provides better performance for updates that must be atomic.</span></span> <span data-ttu-id="5a739-163">Bir çekişme yoksa, dahili olarak tek bir kilit öneki yürütür.</span><span class="sxs-lookup"><span data-stu-id="5a739-163">Internally, it executes a single lock prefix if there is no contention.</span></span> <span data-ttu-id="5a739-164">Kod İncelemeleri bölümünde aşağıdaki örneklerde gösterildiği gibi kodu izleyin.</span><span class="sxs-lookup"><span data-stu-id="5a739-164">In code reviews, watch for code like that shown in the following examples.</span></span> <span data-ttu-id="5a739-165">İlk örnekte, bir durum değişkeni artırılır:</span><span class="sxs-lookup"><span data-stu-id="5a739-165">In the first example, a state variable is incremented:</span></span>  
  
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
  
     <span data-ttu-id="5a739-166"><xref:System.Threading.Interlocked.Increment%2A>Aşağıdaki gibi, yöntemi yerine yöntemini kullanarak performansı artırabilirsiniz `lock` :</span><span class="sxs-lookup"><span data-stu-id="5a739-166">You can improve performance by using the <xref:System.Threading.Interlocked.Increment%2A> method instead of the `lock` statement, as follows:</span></span>  
  
    ```vb  
    System.Threading.Interlocked.Increment(myField)  
    ```  
  
    ```csharp  
    System.Threading.Interlocked.Increment(myField);  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="5a739-167">.NET Framework 2,0 ve sonrasında, <xref:System.Threading.Interlocked.Add%2A> 1 ' den büyük atomik artışlarla yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="5a739-167">In the .NET Framework 2.0 and later, use the <xref:System.Threading.Interlocked.Add%2A> method for atomic increments larger than 1.</span></span>  
  
     <span data-ttu-id="5a739-168">İkinci örnekte, bir başvuru türü değişkeni yalnızca bir null başvurusu ( `Nothing` Visual Basic) ise güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="5a739-168">In the second example, a reference type variable is updated only if it is a null reference (`Nothing` in Visual Basic).</span></span>  
  
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
  
     <span data-ttu-id="5a739-169"><xref:System.Threading.Interlocked.CompareExchange%2A>Aşağıdaki gibi yöntemi kullanılarak performans artırılabilir:</span><span class="sxs-lookup"><span data-stu-id="5a739-169">Performance can be improved by using the <xref:System.Threading.Interlocked.CompareExchange%2A> method instead, as follows:</span></span>  
  
    ```vb  
    System.Threading.Interlocked.CompareExchange(x, y, Nothing)  
    ```  
  
    ```csharp  
    System.Threading.Interlocked.CompareExchange(ref x, y, null);  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="5a739-170">.NET Framework 2,0 ' den başlayarak, <xref:System.Threading.Interlocked.CompareExchange%60%601%28%60%600%40%2C%60%600%2C%60%600%29> yöntem aşırı yüklemesi başvuru türleri için tür açısından güvenli bir alternatif sağlar.</span><span class="sxs-lookup"><span data-stu-id="5a739-170">Beginning with .NET Framework 2.0, the <xref:System.Threading.Interlocked.CompareExchange%60%601%28%60%600%40%2C%60%600%2C%60%600%29> method overload provides a type-safe alternative for reference types.</span></span>
  
## <a name="recommendations-for-class-libraries"></a><span data-ttu-id="5a739-171">Sınıf kitaplıkları için öneriler</span><span class="sxs-lookup"><span data-stu-id="5a739-171">Recommendations for class libraries</span></span>  
 <span data-ttu-id="5a739-172">Çoklu iş parçacığı için sınıf kitaplıkları tasarlarken aşağıdaki yönergeleri göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="5a739-172">Consider the following guidelines when designing class libraries for multithreading:</span></span>  
  
- <span data-ttu-id="5a739-173">Mümkünse eşitleme gereksinimini önleyin.</span><span class="sxs-lookup"><span data-stu-id="5a739-173">Avoid the need for synchronization, if possible.</span></span> <span data-ttu-id="5a739-174">Bu, özellikle de yoğun olarak kullanılan kod için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="5a739-174">This is especially true for heavily used code.</span></span> <span data-ttu-id="5a739-175">Örneğin, bir algoritma ortadan kaldırmak yerine bir yarış durumuna göre ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="5a739-175">For example, an algorithm might be adjusted to tolerate a race condition rather than eliminate it.</span></span> <span data-ttu-id="5a739-176">Gereksiz eşitleme performansı düşürür ve Kilitlenmeler ve yarış koşullarından oluşan olasılığı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5a739-176">Unnecessary synchronization decreases performance and creates the possibility of deadlocks and race conditions.</span></span>  
  
- <span data-ttu-id="5a739-177">Statik verileri ( `Shared` Visual Basic) iş parçacığında varsayılan olarak güvenli hale getirin.</span><span class="sxs-lookup"><span data-stu-id="5a739-177">Make static data (`Shared` in Visual Basic) thread safe by default.</span></span>  
  
- <span data-ttu-id="5a739-178">Örnek veri parçacığını varsayılan olarak güvenli hale getirme.</span><span class="sxs-lookup"><span data-stu-id="5a739-178">Do not make instance data thread safe by default.</span></span> <span data-ttu-id="5a739-179">İş parçacığı açısından güvenli kod oluşturmak için kilitlerin eklenmesi performansı düşürür, kilit çekişmesini artırır ve kilitlenmeleri oluşma olasılığını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5a739-179">Adding locks to create thread-safe code decreases performance, increases lock contention, and creates the possibility for deadlocks to occur.</span></span> <span data-ttu-id="5a739-180">Ortak uygulama modellerinde, aynı anda yalnızca bir iş parçacığı Kullanıcı kodunu yürütür ve bu da iş parçacığı güvenliği gereksinimini en aza indirir.</span><span class="sxs-lookup"><span data-stu-id="5a739-180">In common application models, only one thread at a time executes user code, which minimizes the need for thread safety.</span></span> <span data-ttu-id="5a739-181">Bu nedenle, .NET Framework sınıf kitaplıkları varsayılan olarak iş parçacığı güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="5a739-181">For this reason, the .NET Framework class libraries are not thread safe by default.</span></span>  
  
- <span data-ttu-id="5a739-182">Statik durumu değiştirecek statik yöntemler sağlamaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="5a739-182">Avoid providing static methods that alter static state.</span></span> <span data-ttu-id="5a739-183">Ortak sunucu senaryolarında, statik durum istekler arasında paylaşılır, bu da birden çok iş parçacığının aynı anda bu kodu yürütebileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="5a739-183">In common server scenarios, static state is shared across requests, which means multiple threads can execute that code at the same time.</span></span> <span data-ttu-id="5a739-184">Bu, hataları iş parçacığı olma olasılığını açar.</span><span class="sxs-lookup"><span data-stu-id="5a739-184">This opens up the possibility of threading bugs.</span></span> <span data-ttu-id="5a739-185">İstekler arasında paylaşılmayan örneklere veri kapsülleyen bir tasarım kalıbı kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="5a739-185">Consider using a design pattern that encapsulates data into instances that are not shared across requests.</span></span> <span data-ttu-id="5a739-186">Ayrıca, statik veriler eşitlenirse, durumu alter static Yöntemler arasındaki çağrılar kilitlenmeleri veya yedekli eşitlemeye neden olabilir ve bu da performansı olumsuz etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="5a739-186">Furthermore, if static data are synchronized, calls between static methods that alter state can result in deadlocks or redundant synchronization, adversely affecting performance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a739-187">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5a739-187">See also</span></span>

- [<span data-ttu-id="5a739-188">İş Parçacığı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="5a739-188">Threading</span></span>](index.md)
- [<span data-ttu-id="5a739-189">İş Parçacıkları ve İş Parçacığı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="5a739-189">Threads and Threading</span></span>](threads-and-threading.md)
