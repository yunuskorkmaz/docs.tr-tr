---
title: Görev Tabanlı Zaman Uyumsuz Desen Kullanma
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- .NET Framework, and TAP
- asynchronous design patterns, .NET Framework
- TAP, .NET Framework support for
- Task-based Asynchronous Pattern, .NET Framework support for
- .NET Framework, asynchronous design patterns
ms.assetid: 033cf871-ae24-433d-8939-7a3793e547bf
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5b538cb53e1cbc1fdbd8e34506710a1967e50f9d
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2018
ms.locfileid: "45615553"
---
# <a name="consuming-the-task-based-asynchronous-pattern"></a><span data-ttu-id="defdb-102">Görev Tabanlı Zaman Uyumsuz Desen Kullanma</span><span class="sxs-lookup"><span data-stu-id="defdb-102">Consuming the Task-based Asynchronous Pattern</span></span>
<span data-ttu-id="defdb-103">Zaman uyumsuz işlemler ile çalışmak için görev tabanlı zaman uyumsuz desen (TAP) kullandığınızda, geri çağırmaları engellemeden beklemeyi için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="defdb-103">When you use the Task-based Asynchronous Pattern (TAP) to work with asynchronous operations, you can use callbacks to achieve waiting without blocking.</span></span>  <span data-ttu-id="defdb-104">Görevler için bu yöntemleri gibi gerçekleştirilir <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="defdb-104">For tasks, this is achieved through methods such as <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="defdb-105">İçinde normal denetim akışını beklenmesini zaman uyumsuz işlemleri sağlayarak geri çağırmaları dil tabanlı zaman uyumsuz destek gizler ve derleyicinin ürettiği kodun bu aynı API düzeyinde destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="defdb-105">Language-based asynchronous support hides callbacks by allowing asynchronous operations to be awaited within normal control flow, and compiler-generated code provides this same API-level support.</span></span>  
  
## <a name="suspending-execution-with-await"></a><span data-ttu-id="defdb-106">Await ile yürütmeyi askıya alma</span><span class="sxs-lookup"><span data-stu-id="defdb-106">Suspending Execution with Await</span></span>  
 <span data-ttu-id="defdb-107">İle başlayarak [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], kullanabileceğiniz [await](~/docs/csharp/language-reference/keywords/await.md) C# anahtar sözcüğü ve [Await işleci](~/docs/visual-basic/language-reference/operators/await-operator.md) zaman uyumsuz olarak beklemek için Visual Basic'te <xref:System.Threading.Tasks.Task> ve <xref:System.Threading.Tasks.Task%601> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="defdb-107">Starting with the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], you can use the [await](~/docs/csharp/language-reference/keywords/await.md) keyword in C# and the [Await Operator](~/docs/visual-basic/language-reference/operators/await-operator.md) in Visual Basic to asynchronously await <xref:System.Threading.Tasks.Task> and <xref:System.Threading.Tasks.Task%601> objects.</span></span> <span data-ttu-id="defdb-108">Ne zaman bekleyen bir <xref:System.Threading.Tasks.Task>, `await` ifadesidir türünü `void`.</span><span class="sxs-lookup"><span data-stu-id="defdb-108">When you're awaiting a <xref:System.Threading.Tasks.Task>, the `await` expression is of type `void`.</span></span> <span data-ttu-id="defdb-109">Ne zaman bekleyen bir <xref:System.Threading.Tasks.Task%601>, `await` ifadesidir türünü `TResult`.</span><span class="sxs-lookup"><span data-stu-id="defdb-109">When you're awaiting a <xref:System.Threading.Tasks.Task%601>, the `await` expression is of type `TResult`.</span></span> <span data-ttu-id="defdb-110">Bir `await` ifadesi, zaman uyumsuz bir yöntem gövdesi içinde gerçekleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="defdb-110">An `await` expression must occur inside the body of an asynchronous method.</span></span> <span data-ttu-id="defdb-111">C# ve Visual Basic dili hakkında daha fazla bilgi için destek [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], C# ve Visual Basic dil özellikleri bakın.</span><span class="sxs-lookup"><span data-stu-id="defdb-111">For more information about C# and Visual Basic language support in the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], see the C# and Visual Basic language specifications.</span></span>  
  
 <span data-ttu-id="defdb-112">Perde await işlevi bir geri çağırma göreve bir devamlılık kullanarak yükler.</span><span class="sxs-lookup"><span data-stu-id="defdb-112">Under the covers, the await functionality installs a callback on the task by using a continuation.</span></span>  <span data-ttu-id="defdb-113">Bu geri çağırma zaman uyumsuz yöntem askıya alma noktasında sürdürür.</span><span class="sxs-lookup"><span data-stu-id="defdb-113">This callback resumes the asynchronous method at the point of suspension.</span></span> <span data-ttu-id="defdb-114">Zaman uyumsuz yöntemin sürdürüldü, beklenen işlemi başarıyla tamamlandı ve bir <xref:System.Threading.Tasks.Task%601>, kendi `TResult` döndürülür.</span><span class="sxs-lookup"><span data-stu-id="defdb-114">When the asynchronous method is resumed, if the awaited operation completed successfully and was a <xref:System.Threading.Tasks.Task%601>, its `TResult` is returned.</span></span>  <span data-ttu-id="defdb-115">Varsa <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601> , bekleniyor, sona erdi <xref:System.Threading.Tasks.TaskStatus.Canceled> durumu, bir <xref:System.OperationCanceledException> özel durumu oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="defdb-115">If the <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> that was awaited ended in the <xref:System.Threading.Tasks.TaskStatus.Canceled> state, an <xref:System.OperationCanceledException> exception is thrown.</span></span>  <span data-ttu-id="defdb-116">Varsa <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601> , bekleniyor, sona erdi <xref:System.Threading.Tasks.TaskStatus.Faulted> durumunda hataya neden olan özel durum harekete geçirilir.</span><span class="sxs-lookup"><span data-stu-id="defdb-116">If the <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> that was awaited ended in the <xref:System.Threading.Tasks.TaskStatus.Faulted> state, the exception that caused it to fault is thrown.</span></span> <span data-ttu-id="defdb-117">A `Task` birden çok özel durum sonucu olarak hata olabilir, ancak bu özel durumların yalnızca biri yayılır.</span><span class="sxs-lookup"><span data-stu-id="defdb-117">A `Task` can fault as a result of multiple exceptions, but only one of these exceptions is propagated.</span></span> <span data-ttu-id="defdb-118">Ancak, <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> özelliği döndürür bir <xref:System.AggregateException> içeren tüm hataları özel durum.</span><span class="sxs-lookup"><span data-stu-id="defdb-118">However, the <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> property returns an <xref:System.AggregateException> exception that contains all the errors.</span></span>  
  
 <span data-ttu-id="defdb-119">Bir eşitleme bağlamı ise (<xref:System.Threading.SynchronizationContext> nesne) zaman uyumsuz yöntem askıya alma bir anda yürütülmekte olan iş parçacığı ile ilişkili (örneğin, <xref:System.Threading.SynchronizationContext.Current%2A?displayProperty=nameWithType> özelliği değil `null`), zaman uyumsuz yöntemin oturum sürdürür bağlamın kullanarak aynı eşitleme bağlamı <xref:System.Threading.SynchronizationContext.Post%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="defdb-119">If a synchronization context (<xref:System.Threading.SynchronizationContext> object) is associated with the thread that was executing the asynchronous method at the time of suspension (for example, if the <xref:System.Threading.SynchronizationContext.Current%2A?displayProperty=nameWithType> property is not `null`), the asynchronous method resumes on that same synchronization context by using the context’s <xref:System.Threading.SynchronizationContext.Post%2A> method.</span></span> <span data-ttu-id="defdb-120">Aksi takdirde, Görev Zamanlayıcı üzerinde kullanır (<xref:System.Threading.Tasks.TaskScheduler> nesne), askıya alma zamanında geçerli.</span><span class="sxs-lookup"><span data-stu-id="defdb-120">Otherwise, it relies on the task scheduler (<xref:System.Threading.Tasks.TaskScheduler> object) that was current at the time of suspension.</span></span> <span data-ttu-id="defdb-121">Genellikle, bu varsayılan Görev Zamanlayıcısı'nı, (<xref:System.Threading.Tasks.TaskScheduler.Default%2A?displayProperty=nameWithType>), iş parçacığı havuzu hedefler.</span><span class="sxs-lookup"><span data-stu-id="defdb-121">Typically, this is the default task scheduler (<xref:System.Threading.Tasks.TaskScheduler.Default%2A?displayProperty=nameWithType>), which targets the thread pool.</span></span> <span data-ttu-id="defdb-122">Bu Görev Zamanlayıcı'yı beklenen zaman uyumsuz işlemi burada tamamlandı veya sürdürme olup zamanlanması gerektiğini sürdürme belirler.</span><span class="sxs-lookup"><span data-stu-id="defdb-122">This task scheduler determines whether the awaited asynchronous operation should resume where it completed or whether the resumption should be scheduled.</span></span> <span data-ttu-id="defdb-123">Varsayılan Zamanlayıcı genellikle beklenen işlem tamamlanmış iş parçacığı üzerinde çalıştırılacak süreklilik sağlar.</span><span class="sxs-lookup"><span data-stu-id="defdb-123">The default scheduler typically allows the continuation to run on the thread that the awaited operation completed.</span></span>  
  
 <span data-ttu-id="defdb-124">Zaman uyumsuz bir yöntem çağrıldığında, ilk await ifadesi bu noktada çağırma çağırana döner. henüz tamamlanmamış bir beklenebilir örneğinde kadar eş zamanlı olarak işlev gövdesini yürütür.</span><span class="sxs-lookup"><span data-stu-id="defdb-124">When an asynchronous method is called, it synchronously executes the body of the function up until the first await expression on an awaitable instance that has not yet completed, at which point the invocation returns to the caller.</span></span> <span data-ttu-id="defdb-125">Zaman uyumsuz yöntemin oluşmazsa `void`, <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601> sürekli hesaplama temsil etmek için nesne döndürülür.</span><span class="sxs-lookup"><span data-stu-id="defdb-125">If the asynchronous method does not return `void`, a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> object is returned to represent the ongoing computation.</span></span> <span data-ttu-id="defdb-126">Void olmayan zaman uyumsuz yönteminde return deyimi karşılaşılanaa ya da yöntem gövdesinin sonuna ulaşıldığında, görev tamamlanır <xref:System.Threading.Tasks.TaskStatus.RanToCompletion> son durumu.</span><span class="sxs-lookup"><span data-stu-id="defdb-126">In a non-void asynchronous method, if a return statement is encountered or the end of the method body is reached, the task is completed in the <xref:System.Threading.Tasks.TaskStatus.RanToCompletion> final state.</span></span> <span data-ttu-id="defdb-127">Zaman uyumsuz Yöntemin gövdesi bırakmak denetim işlenmeyen bir özel durum neden olursa, görev biten <xref:System.Threading.Tasks.TaskStatus.Faulted> durumu.</span><span class="sxs-lookup"><span data-stu-id="defdb-127">If an unhandled exception causes control to leave the body of the asynchronous method, the task ends in the <xref:System.Threading.Tasks.TaskStatus.Faulted> state.</span></span> <span data-ttu-id="defdb-128">O özel durumu ise bir <xref:System.OperationCanceledException>, görevi yerine biten <xref:System.Threading.Tasks.TaskStatus.Canceled> durumu.</span><span class="sxs-lookup"><span data-stu-id="defdb-128">If that exception is an <xref:System.OperationCanceledException>, the task instead ends in the <xref:System.Threading.Tasks.TaskStatus.Canceled> state.</span></span> <span data-ttu-id="defdb-129">Bu şekilde, sonuç ya da özel durum sonunda yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="defdb-129">In this manner, the result or exception is eventually published.</span></span>  
  
 <span data-ttu-id="defdb-130">Bu davranış birkaç önemli farklılıklar vardır.</span><span class="sxs-lookup"><span data-stu-id="defdb-130">There are several important variations of this behavior.</span></span>  <span data-ttu-id="defdb-131">Performans nedenleriyle zaman bir görev zaten tamamlandıysa görev beklenir, Denetim değil oluşturulur ve işlev yürütmeye devam eder.</span><span class="sxs-lookup"><span data-stu-id="defdb-131">For performance reasons, if a task has already completed by the time the task is awaited, control is not yielded, and the function continues to execute.</span></span>  <span data-ttu-id="defdb-132">Buna ek olarak, özgün bağlamına döndürerek her zaman istenen davranış değildir ve değiştirilebilir; Bu, sonraki bölümde daha ayrıntılı açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="defdb-132">Additionally, returning to the original context isn't always the desired behavior and can be changed; this is described in more detail in the next section.</span></span>  
  
### <a name="configuring-suspension-and-resumption-with-yield-and-configureawait"></a><span data-ttu-id="defdb-133">Askıya alma ve sürdürme ConfigureAwait Yield ile yapılandırma</span><span class="sxs-lookup"><span data-stu-id="defdb-133">Configuring Suspension and Resumption with Yield and ConfigureAwait</span></span>  
 <span data-ttu-id="defdb-134">Çeşitli yöntemler, zaman uyumsuz bir yöntemin yürütme üzerinde daha fazla denetim sağlar.</span><span class="sxs-lookup"><span data-stu-id="defdb-134">Several methods provide more control over an asynchronous method’s execution.</span></span> <span data-ttu-id="defdb-135">Örneğin, kullanabileceğiniz <xref:System.Threading.Tasks.Task.Yield%2A?displayProperty=nameWithType> yöntemi zaman uyumsuz yönteme bir bekletme noktası tanıtmak için:</span><span class="sxs-lookup"><span data-stu-id="defdb-135">For example, you can use the <xref:System.Threading.Tasks.Task.Yield%2A?displayProperty=nameWithType> method to introduce a yield point into the asynchronous method:</span></span>  
  
```csharp  
public class Task : …  
{  
    public static YieldAwaitable Yield();  
    …  
}  
```  
  
 <span data-ttu-id="defdb-136">Bu, zaman uyumsuz olarak yayınlayarak veya geçerli bağlama zamanlama eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="defdb-136">This is equivalent to asynchronously posting or scheduling back to the current context.</span></span>  
  
```csharp  
Task.Run(async delegate  
{  
    for(int i=0; i<1000000; i++)  
    {  
        await Task.Yield(); // fork the continuation into a separate work item  
        ...  
    }  
});  
```  
  
 <span data-ttu-id="defdb-137">Ayrıca <xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=nameWithType> askıya alma ve sürdürme zaman uyumsuz bir yöntemde üzerinde daha iyi denetim için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="defdb-137">You can also use the <xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=nameWithType> method for better control over suspension and resumption in an asynchronous method.</span></span>  <span data-ttu-id="defdb-138">Daha önce belirtildiği gibi varsayılan olarak, zaman uyumsuz bir yöntem askıya zaman geçerli bağlam yakalanır ve yakalanan bu bağlamı zaman uyumsuz yöntemin devamı sürdürme üzerinde çağırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="defdb-138">As mentioned previously, by default, the current context is captured at the time an asynchronous  method is suspended, and that captured context is used to invoke the asynchronous  method’s continuation upon resumption.</span></span>  <span data-ttu-id="defdb-139">Çoğu durumda, istediğiniz tam davranış budur.</span><span class="sxs-lookup"><span data-stu-id="defdb-139">In many cases, this is the exact behavior you want.</span></span>  <span data-ttu-id="defdb-140">Diğer durumlarda, devamlılık bağlamı hakkında önemsemez ve bu tür postaları orijinal bağlamdaki dön önleyerek daha iyi performans elde edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="defdb-140">In other cases, you may not care about the continuation context, and you can achieve better performance by avoiding such posts back to the original context.</span></span>  <span data-ttu-id="defdb-141">Bunu etkinleştirmek için <xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=nameWithType> yakalamak ve bağlamda sürdürmek için ancak erdirdi beklemenin zaman uyumsuz işlem tamamlanmış her yerde yürütme devam etmek için bekleme işlemi bildirmek için yöntemi:</span><span class="sxs-lookup"><span data-stu-id="defdb-141">To enable this, use the <xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=nameWithType> method to inform the await operation not to capture and resume on the context, but to continue execution wherever the asynchronous operation that was being awaited completed:</span></span>  
  
```csharp  
await someTask.ConfigureAwait(continueOnCapturedContext:false);  
```  
  
## <a name="canceling-an-asynchronous-operation"></a><span data-ttu-id="defdb-142">Zaman uyumsuz bir işlem iptal ediliyor</span><span class="sxs-lookup"><span data-stu-id="defdb-142">Canceling an Asynchronous Operation</span></span>  
 <span data-ttu-id="defdb-143">İle başlayarak [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], iptal desteği DOKUNUN yöntemler sağlar bir iptal belirteci kabul eden en az bir aşırı yükleme (<xref:System.Threading.CancellationToken> nesne).</span><span class="sxs-lookup"><span data-stu-id="defdb-143">Starting with the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], TAP methods that support cancellation provide at least one overload that accepts a cancellation token (<xref:System.Threading.CancellationToken> object).</span></span>  
  
 <span data-ttu-id="defdb-144">Bir iptal belirteci iptal belirteci kaynağı oluşturulur (<xref:System.Threading.CancellationTokenSource> nesne).</span><span class="sxs-lookup"><span data-stu-id="defdb-144">A cancellation token is created through a cancellation token source (<xref:System.Threading.CancellationTokenSource> object).</span></span>  <span data-ttu-id="defdb-145">Kaynağın <xref:System.Threading.CancellationTokenSource.Token%2A> özelliği işareti iptal belirtecini döndürür, kaynağın <xref:System.Threading.CancellationTokenSource.Cancel%2A> yöntemi çağrılır.</span><span class="sxs-lookup"><span data-stu-id="defdb-145">The source’s <xref:System.Threading.CancellationTokenSource.Token%2A> property returns the cancellation token that will be signaled when the source’s <xref:System.Threading.CancellationTokenSource.Cancel%2A> method is called.</span></span>  <span data-ttu-id="defdb-146">Örneğin, tek bir Web sayfasından indirin ve işlemi iptal edemezsiniz eklemek istiyorsanız, oluşturduğunuz bir <xref:System.Threading.CancellationTokenSource> nesne, TAP yöntemi, belirtecin geçip ve ardından kaynağın çağrısı <xref:System.Threading.CancellationTokenSource.Cancel%2A> işlemi iptal etmek hazır olduğunuzda yöntemi:</span><span class="sxs-lookup"><span data-stu-id="defdb-146">For example, if you want to download a single webpage and you want to be able to cancel the operation, you create a <xref:System.Threading.CancellationTokenSource> object, pass its token to the TAP method, and then call the source’s <xref:System.Threading.CancellationTokenSource.Cancel%2A> method when you're ready to cancel the operation:</span></span>  
  
```csharp  
var cts = new CancellationTokenSource();  
string result = await DownloadStringAsync(url, cts.Token);  
… // at some point later, potentially on another thread  
cts.Cancel();  
```  
  
 <span data-ttu-id="defdb-147">Birden çok zaman uyumsuz çağrılar iptal etmek için aynı belirteci için tüm etkinleştirmeleri geçirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="defdb-147">To cancel multiple asynchronous invocations, you can pass the same token to all invocations:</span></span>  
  
```csharp  
var cts = new CancellationTokenSource();  
    IList<string> results = await Task.WhenAll(from url in urls select DownloadStringAsync(url, cts.Token));  
    // at some point later, potentially on another thread  
    …  
    cts.Cancel();  
```  
  
 <span data-ttu-id="defdb-148">Ya da aynı belirteci için seçmeli alt işlemlerin geçirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="defdb-148">Or, you can pass the same token to a selective subset of operations:</span></span>  
  
```csharp  
var cts = new CancellationTokenSource();  
    byte [] data = await DownloadDataAsync(url, cts.Token);  
    await SaveToDiskAsync(outputPath, data, CancellationToken.None);  
    … // at some point later, potentially on another thread  
    cts.Cancel();  
```  
  
 <span data-ttu-id="defdb-149">Herhangi bir iş parçacığından iptal isteklerini başlatılabilir.</span><span class="sxs-lookup"><span data-stu-id="defdb-149">Cancellation requests may be initiated from any thread.</span></span>  
  
 <span data-ttu-id="defdb-150">Geçirebilirsiniz <xref:System.Threading.CancellationToken.None%2A?displayProperty=nameWithType> iptal hiçbir zaman istenmesi belirtmek için bir iptal belirteci kabul eden herhangi bir yöntemi için değer.</span><span class="sxs-lookup"><span data-stu-id="defdb-150">You can pass the <xref:System.Threading.CancellationToken.None%2A?displayProperty=nameWithType> value to any method that accepts a cancellation token to indicate that cancellation will never be requested.</span></span>  <span data-ttu-id="defdb-151">Bu neden <xref:System.Threading.CancellationToken.CanBeCanceled%2A?displayProperty=nameWithType> dönmesini `false`, ve çağrılan yöntemin uygun şekilde en iyi duruma getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="defdb-151">This causes the <xref:System.Threading.CancellationToken.CanBeCanceled%2A?displayProperty=nameWithType> property to return `false`, and the called method can optimize accordingly.</span></span>  <span data-ttu-id="defdb-152">Test amacıyla de belirteç zaten iptal edildi veya iptal edilebilir olmayan bir durumda başlaması göstermek için bir Boole değeri kabul eden Oluşturucusu kullanarak örneği oluşturulan bir önceden iptal edilmiş bir iptal belirteci geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="defdb-152">For testing purposes, you can also pass in a pre-canceled cancellation token that is instantiated by using the constructor that accepts a Boolean value to indicate whether the token should start in an already-canceled or not-cancelable state.</span></span>  
  
 <span data-ttu-id="defdb-153">Bu yaklaşım iptali çeşitli avantajları vardır:</span><span class="sxs-lookup"><span data-stu-id="defdb-153">This approach to cancellation has several advantages:</span></span>  
  
-   <span data-ttu-id="defdb-154">Zaman uyumsuz ve zaman uyumlu işlemler herhangi bir sayıda, aynı iptal belirtecini geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="defdb-154">You can pass the same cancellation token to any number of asynchronous and synchronous operations.</span></span>  
  
-   <span data-ttu-id="defdb-155">Aynı iptal isteği herhangi bir sayıda dinleyicileri hızla.</span><span class="sxs-lookup"><span data-stu-id="defdb-155">The same cancellation request may be proliferated to any number of listeners.</span></span>  
  
-   <span data-ttu-id="defdb-156">Zaman uyumsuz API geliştiricidir tam denetimi iptal isteğinde ve ne zaman etkili olması.</span><span class="sxs-lookup"><span data-stu-id="defdb-156">The developer of the asynchronous API is in complete control of whether cancellation may be requested and when it may take effect.</span></span>  
  
-   <span data-ttu-id="defdb-157">API kullanan kod için iptal isteklerini aktarılacaktır zaman uyumsuz çağrılar seçmeli olarak belirleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="defdb-157">The code that consumes the API may selectively determine the asynchronous invocations that cancellation requests will be propagated to.</span></span>  
  
## <a name="monitoring-progress"></a><span data-ttu-id="defdb-158">İlerlemeyi İzleme</span><span class="sxs-lookup"><span data-stu-id="defdb-158">Monitoring Progress</span></span>  
 <span data-ttu-id="defdb-159">Bazı zaman uyumsuz yöntemler, ilerleme zaman uyumsuz yönteme geçirilen bir ilerleme arabirimi aracılığıyla kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="defdb-159">Some asynchronous methods expose progress through a progress interface passed into the asynchronous method.</span></span>  <span data-ttu-id="defdb-160">Örneğin, metin ve yol boyunca bir dize zaman uyumsuz olarak indiren bir işlev, şimdiye kadarki tamamlanan indirme yüzdesini içeren devam eden güncelleştirmelerin başlatır göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="defdb-160">For example, consider a function which asynchronously downloads a string of text, and along the way raises progress updates that include the percentage of the download that has completed thus far.</span></span>  <span data-ttu-id="defdb-161">Böyle bir yöntemi gibi bir Windows Presentation Foundation (WPF) uygulamasında tüketilebilecek:</span><span class="sxs-lookup"><span data-stu-id="defdb-161">Such a method could be consumed in a Windows Presentation Foundation (WPF) application as follows:</span></span>  
  
```csharp  
private async void btnDownload_Click(object sender, RoutedEventArgs e)    
{  
    btnDownload.IsEnabled = false;  
    try  
    {  
        txtResult.Text = await DownloadStringAsync(txtUrl.Text,   
            new Progress<int>(p => pbDownloadProgress.Value = p));  
    }  
    finally { btnDownload.IsEnabled = true; }  
}  
```  
  
<a name="combinators"></a>   
## <a name="using-the-built-in-task-based-combinators"></a><span data-ttu-id="defdb-162">Yerleşik görev tabanlı Kombinatör kullanımı</span><span class="sxs-lookup"><span data-stu-id="defdb-162">Using the Built-in Task-based Combinators</span></span>  
 <span data-ttu-id="defdb-163"><xref:System.Threading.Tasks> Ad alanı oluşturma ve görevler ile çalışmak için birkaç yöntem içerir.</span><span class="sxs-lookup"><span data-stu-id="defdb-163">The <xref:System.Threading.Tasks> namespace includes several methods for composing and working with tasks.</span></span>  
  
### <a name="taskrun"></a><span data-ttu-id="defdb-164">Gt;Task.Run</span><span class="sxs-lookup"><span data-stu-id="defdb-164">Task.Run</span></span>  
 <span data-ttu-id="defdb-165"><xref:System.Threading.Tasks.Task> Sınıfı içeren birkaç <xref:System.Threading.Tasks.Task.Run%2A> kolayca olanak tanıyan yöntemler yük boşaltma iş olarak bir <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601> iş parçacığı havuzuna, örneğin:</span><span class="sxs-lookup"><span data-stu-id="defdb-165">The <xref:System.Threading.Tasks.Task> class includes several <xref:System.Threading.Tasks.Task.Run%2A> methods that let you easily offload work as a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> to the thread pool, for example:</span></span>  
  
```csharp  
public async void button1_Click(object sender, EventArgs e)  
{  
    textBox1.Text = await Task.Run(() =>  
    {  
        // … do compute-bound work here  
        return answer;  
    });  
}  
```  
  
 <span data-ttu-id="defdb-166">Bunlardan bazıları <xref:System.Threading.Tasks.Task.Run%2A> yöntemleri gibi <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType> aşırı yükleme, için kısayol olarak mevcut <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="defdb-166">Some of these <xref:System.Threading.Tasks.Task.Run%2A> methods, such as the <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType> overload, exist as shorthand for the <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> method.</span></span>  <span data-ttu-id="defdb-167">Gibi diğer aşırı <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType>, kullanmanızı await Boşaltılan işe, örneğin etkinleştir:</span><span class="sxs-lookup"><span data-stu-id="defdb-167">Other overloads, such as <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType>, enable you to use await within the offloaded work, for example:</span></span>  
  
```csharp  
public async void button1_Click(object sender, EventArgs e)  
{  
    pictureBox1.Image = await Task.Run(async() =>  
    {  
        using(Bitmap bmp1 = await DownloadFirstImageAsync())  
        using(Bitmap bmp2 = await DownloadSecondImageAsync())  
        return Mashup(bmp1, bmp2);  
    });  
}  
```  
  
 <span data-ttu-id="defdb-168">Stl'yi Bu aşırı kullanarak mantıksal eşdeğer <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> yöntemi ile birlikte <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> görev paralel Kitaplığı'nda genişletme yöntemi.</span><span class="sxs-lookup"><span data-stu-id="defdb-168">Such overloads are logically equivalent to using the <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> method in conjunction with the <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> extension method in the Task Parallel Library.</span></span>  
  
### <a name="taskfromresult"></a><span data-ttu-id="defdb-169">Task.FromResult</span><span class="sxs-lookup"><span data-stu-id="defdb-169">Task.FromResult</span></span>  
 <span data-ttu-id="defdb-170">Kullanım <xref:System.Threading.Tasks.Task.FromResult%2A> yöntemi burada verileri zaten olabilir kullanılabilir ve yalnızca senaryolarda gereken içine yükseltilmiş görev döndüren bir yöntem döndürülecek bir <xref:System.Threading.Tasks.Task%601>:</span><span class="sxs-lookup"><span data-stu-id="defdb-170">Use the <xref:System.Threading.Tasks.Task.FromResult%2A> method in scenarios where data may already be available and just needs to be returned from a task-returning method lifted into a <xref:System.Threading.Tasks.Task%601>:</span></span>  
  
```csharp  
public Task<int> GetValueAsync(string key)  
{  
    int cachedValue;  
    return TryGetCachedValue(out cachedValue) ?  
        Task.FromResult(cachedValue) :  
        GetValueAsyncInternal();  
}  
  
private async Task<int> GetValueAsyncInternal(string key)  
{  
    …  
}  
```  
  
### <a name="taskwhenall"></a><span data-ttu-id="defdb-171">Task.WhenAll</span><span class="sxs-lookup"><span data-stu-id="defdb-171">Task.WhenAll</span></span>  
 <span data-ttu-id="defdb-172">Kullanım <xref:System.Threading.Tasks.Task.WhenAll%2A> yöntemini zaman uyumsuz olarak görevleri olarak temsil edilen birden çok zaman uyumsuz işlemler üzerinde bekleyin.</span><span class="sxs-lookup"><span data-stu-id="defdb-172">Use the <xref:System.Threading.Tasks.Task.WhenAll%2A> method to asynchronously wait on multiple asynchronous operations that are represented as tasks.</span></span>  <span data-ttu-id="defdb-173">Genel olmayan görevler kümesini veya bir genel görevler Tekdüzen olmayan kümesini destekleyen birden çok aşırı yükleme yöntemi vardır (örneğin, zaman uyumsuz olarak birden çok void döndüren işlemleri bekleme veya zaman uyumsuz olarak birden çok değer döndüren yöntem için bekleyen burada Her bir değeri, farklı bir türe sahip olabilir) ve genel görevler Tekdüzen bir dizi desteklemek için (birden çok zaman uyumsuz olarak bekleyen gibi `TResult`-döndürme yöntemlerini).</span><span class="sxs-lookup"><span data-stu-id="defdb-173">The method has multiple overloads that support a set of non-generic tasks or a non-uniform set of generic tasks (for example, asynchronously waiting for multiple void-returning operations, or asynchronously waiting for multiple value-returning methods where each value may have a different type) and to support a uniform set of generic tasks (such as asynchronously waiting for multiple `TResult`-returning methods).</span></span>  
  
 <span data-ttu-id="defdb-174">Birçok müşteri için e-posta iletilerini göndermek istediğiniz varsayalım.</span><span class="sxs-lookup"><span data-stu-id="defdb-174">Let's say you want to send email messages to several customers.</span></span> <span data-ttu-id="defdb-175">Sonraki göndermeden önce tamamlamak bir ileti için bekliyorsunuz değil için gönderme binebilir.</span><span class="sxs-lookup"><span data-stu-id="defdb-175">You can overlap sending the messages so you're not waiting for one message to complete before sending the next.</span></span> <span data-ttu-id="defdb-176">Ayrıca, hata oluşup oluşmadığını ve gönderme işlemleri tamamlandığında çıkış bulabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="defdb-176">You can also find out when the send operations have completed and whether any errors have occurred:</span></span>  
  
```csharp  
IEnumerable<Task> asyncOps = from addr in addrs select SendMailAsync(addr);  
await Task.WhenAll(asyncOps);  
```  
  
 <span data-ttu-id="defdb-177">Bu kod, açıkça özel durumlar oluşabilir, ancak özel durumlar / yayılmasına olanak tanır işlemiyor `await` elde edilen görev üzerinde <xref:System.Threading.Tasks.Task.WhenAll%2A>.</span><span class="sxs-lookup"><span data-stu-id="defdb-177">This code doesn't explicitly handle exceptions that may occur, but lets exceptions propagate out of the `await` on the resulting task from <xref:System.Threading.Tasks.Task.WhenAll%2A>.</span></span>  <span data-ttu-id="defdb-178">Özel durumları işlemek için kod aşağıdaki gibi kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="defdb-178">To handle the exceptions, you can use code such as the following:</span></span>  
  
```csharp  
IEnumerable<Task> asyncOps = from addr in addrs select SendMailAsync(addr);  
try  
{  
    await Task.WhenAll(asyncOps);  
}  
catch(Exception exc)  
{  
    ...  
}  
```  
  
 <span data-ttu-id="defdb-179">Herhangi bir zaman uyumsuz işlem başarısız olursa, bu durumda, tüm özel durumları olarak birleştirilecektir bir <xref:System.AggregateException> depolanan özel durum <xref:System.Threading.Tasks.Task> sağlayıcıdan döndürülen <xref:System.Threading.Tasks.Task.WhenAll%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="defdb-179">In this case, if any asynchronous operation fails, all the exceptions will be consolidated in an <xref:System.AggregateException> exception, which is stored in the <xref:System.Threading.Tasks.Task> that is returned from the <xref:System.Threading.Tasks.Task.WhenAll%2A> method.</span></span>  <span data-ttu-id="defdb-180">Ancak, bu özel durumların yalnızca biri tarafından yayılır `await` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="defdb-180">However, only one of those exceptions is propagated by the `await` keyword.</span></span>  <span data-ttu-id="defdb-181">Tüm özel durumları incelemek isterseniz, önceki kod şu şekilde yeniden yazabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="defdb-181">If you want to examine all the exceptions, you can rewrite the previous code as follows:</span></span>  
  
```csharp  
Task [] asyncOps = (from addr in addrs select SendMailAsync(addr)).ToArray();  
try  
{  
    await Task.WhenAll(asyncOps);  
}  
catch(Exception exc)  
{  
    foreach(Task faulted in asyncOps.Where(t => t.IsFaulted))  
    {  
        … // work with faulted and faulted.Exception  
    }  
}  
```  
  
 <span data-ttu-id="defdb-182">Birden çok dosyayı Web'den zaman uyumsuz olarak yükleme, bir örnek düşünelim.</span><span class="sxs-lookup"><span data-stu-id="defdb-182">Let's consider an example of downloading multiple files from the web asynchronously.</span></span>  <span data-ttu-id="defdb-183">Bu durumda, tüm zaman uyumsuz işlemlerin homojen sonuç türleri olan ve sonuçları erişmek kolaydır:</span><span class="sxs-lookup"><span data-stu-id="defdb-183">In this case, all the asynchronous operations have homogeneous result types, and it's easy to access the results:</span></span>  
  
```csharp  
string [] pages = await Task.WhenAll(  
    from url in urls select DownloadStringAsync(url));  
```  
  
 <span data-ttu-id="defdb-184">Önceki void döndüren senaryoda ele aldığımız aynı özel durum işleme teknikleri kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="defdb-184">You can use the same exception-handling techniques we discussed in the previous void-returning scenario:</span></span>  
  
```csharp  
Task [] asyncOps =   
    (from url in urls select DownloadStringAsync(url)).ToArray();  
try  
{  
    string [] pages = await Task.WhenAll(asyncOps);  
    ...  
}  
catch(Exception exc)  
{  
    foreach(Task<string> faulted in asyncOps.Where(t => t.IsFaulted))  
    {  
        … // work with faulted and faulted.Exception  
    }  
}  
```  
  
### <a name="taskwhenany"></a><span data-ttu-id="defdb-185">Task.WhenAny</span><span class="sxs-lookup"><span data-stu-id="defdb-185">Task.WhenAny</span></span>  
 <span data-ttu-id="defdb-186">Kullanabileceğiniz <xref:System.Threading.Tasks.Task.WhenAny%2A> zaman uyumsuz olarak birden çok zaman uyumsuz işlemler yalnızca biri için beklemeniz yöntemi temsil görevleri tamamlamak için.</span><span class="sxs-lookup"><span data-stu-id="defdb-186">You can use the <xref:System.Threading.Tasks.Task.WhenAny%2A> method to asynchronously wait for just one of multiple asynchronous operations represented as tasks to complete.</span></span>  <span data-ttu-id="defdb-187">Bu yöntem, dört birincil kullanım örnekleri sunar:</span><span class="sxs-lookup"><span data-stu-id="defdb-187">This method serves four primary use cases:</span></span>  
  
-   <span data-ttu-id="defdb-188">Yedeklilik: bir işlemi birden çok kez ve birinci (örneğin, tek bir sonuç oluşturan birden çok hisse senedi web Hizmetleri ile irtibat ve hızlı tamamlayan bir seçme) tamamlayan bir seçme.</span><span class="sxs-lookup"><span data-stu-id="defdb-188">Redundancy:  Performing an operation multiple times and selecting the one that completes first (for example, contacting multiple stock quote web services that will produce a single result and selecting the one that completes the fastest).</span></span>  
  
-   <span data-ttu-id="defdb-189">Interleaving: birden çok işlem başlatma ve tüm bunları tamamlanması için bekleniyor, ancak tamamlandıkça işlemeden.</span><span class="sxs-lookup"><span data-stu-id="defdb-189">Interleaving:  Launching multiple operations and waiting for all of them to complete, but processing them as they complete.</span></span>  
  
-   <span data-ttu-id="defdb-190">Azaltma: başkalarının tamamlanmış olarak başlamak ek işlem yapılmasına olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="defdb-190">Throttling:  Allowing additional operations to begin as others complete.</span></span>  <span data-ttu-id="defdb-191">Bu bir araya senaryo uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="defdb-191">This is an extension of the interleaving scenario.</span></span>  
  
-   <span data-ttu-id="defdb-192">Erken BailOut komutunu: Örneğin, görev t1 tarafından temsil edilen bir işlem içinde gruplandırılabilir bir <xref:System.Threading.Tasks.Task.WhenAny%2A> başka bir görev t2 ve görevle bekleyebilir <xref:System.Threading.Tasks.Task.WhenAny%2A> görev.</span><span class="sxs-lookup"><span data-stu-id="defdb-192">Early bailout:  For example, an operation represented by task t1 can be grouped in a <xref:System.Threading.Tasks.Task.WhenAny%2A> task with another task t2, and you can wait on the <xref:System.Threading.Tasks.Task.WhenAny%2A> task.</span></span> <span data-ttu-id="defdb-193">Görev t2'ın temsil eden bir zaman aşımı veya iptal ya da neden olan bazı bir sinyal <xref:System.Threading.Tasks.Task.WhenAny%2A> t1 tamamlanmadan önce tamamlanması gereken görev.</span><span class="sxs-lookup"><span data-stu-id="defdb-193">Task t2 could represent a time-out, or cancellation, or some other signal that causes the <xref:System.Threading.Tasks.Task.WhenAny%2A> task to complete before t1 completes.</span></span>  
  
#### <a name="redundancy"></a><span data-ttu-id="defdb-194">Yedeklilik</span><span class="sxs-lookup"><span data-stu-id="defdb-194">Redundancy</span></span>  
 <span data-ttu-id="defdb-195">Bir hisse senedi satın alma konusunda karar istediğiniz bir durum düşünün.</span><span class="sxs-lookup"><span data-stu-id="defdb-195">Consider a case where you want to make a decision about whether to buy a stock.</span></span>  <span data-ttu-id="defdb-196">Güvendiğiniz birkaç stok öneri web hizmetleri vardır, ancak günlük yüke bağlı olarak, her hizmet farklı zamanlarda yavaş olduğundan yukarı sonlandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="defdb-196">There are several stock recommendation web services that you trust, but depending on daily load, each service can end up being slow at different times.</span></span>  <span data-ttu-id="defdb-197">Kullanabileceğiniz <xref:System.Threading.Tasks.Task.WhenAny%2A> yöntemi herhangi bir işlem tamamlandığında bir bildirim almak için:</span><span class="sxs-lookup"><span data-stu-id="defdb-197">You can use the <xref:System.Threading.Tasks.Task.WhenAny%2A> method to receive a notification when any operation completes:</span></span>  
  
```csharp  
var recommendations = new List<Task<bool>>()   
{   
    GetBuyRecommendation1Async(symbol),   
    GetBuyRecommendation2Async(symbol),  
    GetBuyRecommendation3Async(symbol)  
};  
Task<bool> recommendation = await Task.WhenAny(recommendations);  
if (await recommendation) BuyStock(symbol);  
```  
  
 <span data-ttu-id="defdb-198">Farklı <xref:System.Threading.Tasks.Task.WhenAll%2A>, başarıyla tamamlanan tüm görevleri sarmalanmış halden sonuçları döndüren <xref:System.Threading.Tasks.Task.WhenAny%2A> tamamlanan bir görev döndürür.</span><span class="sxs-lookup"><span data-stu-id="defdb-198">Unlike <xref:System.Threading.Tasks.Task.WhenAll%2A>, which returns the unwrapped results of all tasks that completed successfully, <xref:System.Threading.Tasks.Task.WhenAny%2A> returns the task that completed.</span></span> <span data-ttu-id="defdb-199">Bir görev başarısız olursa, başarısız ve bir görev başarılı olursa, dönüş değeri hangi görev ile ilişkili bilmek önemlidir bilmeniz önemlidir.</span><span class="sxs-lookup"><span data-stu-id="defdb-199">If a task fails, it’s important to know that it failed, and if a task succeeds, it’s important to know which task the return value is associated with.</span></span>  <span data-ttu-id="defdb-200">Bu nedenle, bu örnekte gösterildiği gibi döndürülen görevin sonucunu erişmek veya daha fazla, await gerekir.</span><span class="sxs-lookup"><span data-stu-id="defdb-200">Therefore, you need to access the result of the returned task, or further await it, as  this example shows.</span></span>  
  
 <span data-ttu-id="defdb-201">Olduğu gibi <xref:System.Threading.Tasks.Task.WhenAll%2A>, istisnalara uyum sağlamaya yönelik yapabilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="defdb-201">As with <xref:System.Threading.Tasks.Task.WhenAll%2A>, you have to be able to accommodate exceptions.</span></span>  <span data-ttu-id="defdb-202">Tamamlanan görevin geri alması için döndürülen görevin hataları yayılır, await ve `try/catch` bunları uygun şekilde; örneğin:</span><span class="sxs-lookup"><span data-stu-id="defdb-202">Because you receive the completed task back, you can await the returned task to have errors propagated, and `try/catch` them appropriately; for example:</span></span>  
  
```csharp  
Task<bool> [] recommendations = …;  
while(recommendations.Count > 0)  
{   
    Task<bool> recommendation = await Task.WhenAny(recommendations);      
    try  
    {  
        if (await recommendation) BuyStock(symbol);  
        break;  
    }  
    catch(WebException exc)  
    {  
        recommendations.Remove(recommendation);  
    }  
}  
```  
  
 <span data-ttu-id="defdb-203">Ayrıca, ilk görevi başarıyla tamamlandıktan olsa bile, sonraki görevleri başarısız olabilir.</span><span class="sxs-lookup"><span data-stu-id="defdb-203">Additionally, even if a first task completes successfully, subsequent tasks may fail.</span></span>  <span data-ttu-id="defdb-204">Bu noktada, özel durumlar başa çıkmak için birkaç seçeneğiniz vardır: Bu durumda kullanabileceğiniz başlatılan tüm görev tamamlanana kadar bekleyebilirsiniz <xref:System.Threading.Tasks.Task.WhenAll%2A> yöntemi veya karar verebilir tüm özel durumları önemli olduğunu ve oturum açmış olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="defdb-204">At this point, you have several options for dealing with exceptions:  You can wait until all the launched tasks have completed, in which case you can use the <xref:System.Threading.Tasks.Task.WhenAll%2A> method, or you can decide that all exceptions are important and must be logged.</span></span>  <span data-ttu-id="defdb-205">Görevler zaman uyumsuz olarak tamamlandığında bir bildirim almak için bu devamlılıklar kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="defdb-205">For this, you can use continuations to receive a notification when tasks have completed asynchronously:</span></span>  
  
```csharp  
foreach(Task recommendation in recommendations)  
{  
    var ignored = recommendation.ContinueWith(  
        t => { if (t.IsFaulted) Log(t.Exception); });  
}  
```  
  
 <span data-ttu-id="defdb-206">veya:</span><span class="sxs-lookup"><span data-stu-id="defdb-206">or:</span></span>  
  
```csharp  
foreach(Task recommendation in recommendations)  
{  
    var ignored = recommendation.ContinueWith(  
        t => Log(t.Exception), TaskContinuationOptions.OnlyOnFaulted);  
}  
```  
  
 <span data-ttu-id="defdb-207">hatta:</span><span class="sxs-lookup"><span data-stu-id="defdb-207">or even:</span></span>  
  
```  
private static async void LogCompletionIfFailed(IEnumerable<Task> tasks)  
{  
    foreach(var task in tasks)  
    {  
        try { await task; }  
        catch(Exception exc) { Log(exc); }  
    }  
}  
…  
LogCompletionIfFailed(recommendations);  
```  
  
 <span data-ttu-id="defdb-208">Son olarak, kalan tüm işlemleri iptal etmek isteyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="defdb-208">Finally, you may want to cancel all the remaining operations:</span></span>  
  
```csharp  
var cts = new CancellationTokenSource();  
var recommendations = new List<Task<bool>>()   
{   
    GetBuyRecommendation1Async(symbol, cts.Token),   
    GetBuyRecommendation2Async(symbol, cts.Token),  
    GetBuyRecommendation3Async(symbol, cts.Token)  
};  
  
Task<bool> recommendation = await Task.WhenAny(recommendations);  
cts.Cancel();  
if (await recommendation) BuyStock(symbol);  
```  
  
#### <a name="interleaving"></a><span data-ttu-id="defdb-209">Aralama</span><span class="sxs-lookup"><span data-stu-id="defdb-209">Interleaving</span></span>  
 <span data-ttu-id="defdb-210">Burada, Web'den görüntüleri ve (örneğin, bir UI denetimine görüntü ekleme) her bir görüntü işleme bir durum düşünün.</span><span class="sxs-lookup"><span data-stu-id="defdb-210">Consider a case where you're downloading images from the web and processing each image (for example, adding the image to a UI control).</span></span>  <span data-ttu-id="defdb-211">İşlem UI iş parçacığı üzerinde sıralı olarak yapmanız gereken, ancak görüntüleri olarak eşzamanlı olarak karşıdan yüklemek istediğiniz.</span><span class="sxs-lookup"><span data-stu-id="defdb-211">You have to do the processing sequentially on the UI thread, but you want to download the images as concurrently as possible.</span></span> <span data-ttu-id="defdb-212">Ayrıca, tüm indirdikten kadar görüntüleri için kullanıcı Arabirimi ekleme tutmak istemediğiniz — tamamlandıkça bunları eklemek istediğiniz:</span><span class="sxs-lookup"><span data-stu-id="defdb-212">Also, you don’t want to hold up adding the images to the UI until they’re all downloaded—you want to add them as they complete:</span></span>  
  
```csharp  
List<Task<Bitmap>> imageTasks =   
    (from imageUrl in urls select GetBitmapAsync(imageUrl)).ToList();  
while(imageTasks.Count > 0)  
{  
    try  
    {  
        Task<Bitmap> imageTask = await Task.WhenAny(imageTasks);  
        imageTasks.Remove(imageTask);  
  
        Bitmap image = await imageTask;  
        panel.AddImage(image);  
    }  
    catch{}  
}  
```  
  
 <span data-ttu-id="defdb-213">Üzerinde işlem bakımından yoğun işleme içeren bir senaryo için Aralama uygulayabilirsiniz <xref:System.Threading.ThreadPool> indirilen görüntüleri; örneğin:</span><span class="sxs-lookup"><span data-stu-id="defdb-213">You can also apply interleaving to a scenario that involves computationally intensive processing on the <xref:System.Threading.ThreadPool> of the downloaded images; for example:</span></span>  
  
```csharp  
List<Task<Bitmap>> imageTasks =   
    (from imageUrl in urls select GetBitmapAsync(imageUrl)  
         .ContinueWith(t => ConvertImage(t.Result)).ToList();  
while(imageTasks.Count > 0)  
{  
    try  
    {  
        Task<Bitmap> imageTask = await Task.WhenAny(imageTasks);  
        imageTasks.Remove(imageTask);  
  
        Bitmap image = await imageTask;  
        panel.AddImage(image);  
    }  
    catch{}  
}  
```  
  
#### <a name="throttling"></a><span data-ttu-id="defdb-214">Sınırlama</span><span class="sxs-lookup"><span data-stu-id="defdb-214">Throttling</span></span>  
 <span data-ttu-id="defdb-215">Kullanıcı çok sayıda görüntü indirmeleri kısıtlanabilir olduğunu yüklüyor dışında araya örneği göz önünde bulundurun; Örneğin, yalnızca belirli sayıda indirmeleri aynı anda gerçekleşecek istersiniz.</span><span class="sxs-lookup"><span data-stu-id="defdb-215">Consider the interleaving example, except that the user is downloading so many images that the downloads have to be throttled; for example, you want only a specific number of downloads to happen concurrently.</span></span> <span data-ttu-id="defdb-216">Bunu başarmak için zaman uyumsuz işlemler kümesini başlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="defdb-216">To achieve this, you can start a subset of the asynchronous operations.</span></span>  <span data-ttu-id="defdb-217">İşlem tamamlandı olarak bunların gerçekleşmesi için ek işlemler başlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="defdb-217">As operations complete, you can start additional operations to take their place:</span></span>  
  
```csharp  
const int CONCURRENCY_LEVEL = 15;  
Uri [] urls = …;  
int nextIndex = 0;  
var imageTasks = new List<Task<Bitmap>>();  
while(nextIndex < CONCURRENCY_LEVEL && nextIndex < urls.Length)  
{  
    imageTasks.Add(GetBitmapAsync(urls[nextIndex]));  
    nextIndex++;  
}  
  
while(imageTasks.Count > 0)  
{  
    try  
    {  
        Task<Bitmap> imageTask = await Task.WhenAny(imageTasks);  
        imageTasks.Remove(imageTask);  
  
        Bitmap image = await imageTask;  
        panel.AddImage(image);  
    }  
    catch(Exception exc) { Log(exc); }  
  
    if (nextIndex < urls.Length)  
    {  
        imageTasks.Add(GetBitmapAsync(urls[nextIndex]));  
        nextIndex++;  
    }  
}  
```  
  
#### <a name="early-bailout"></a><span data-ttu-id="defdb-218">Erken BailOut komutunu</span><span class="sxs-lookup"><span data-stu-id="defdb-218">Early Bailout</span></span>  
 <span data-ttu-id="defdb-219">Zaman uyumsuz bir işlemin aynı anda bir kullanıcının iptal isteğine yanıt çalışırken tamamlanması bekliyorsunuz olduğunu göz önünde bulundurun (örneğin, kullanıcının iptal düğmesine tıklandığında).</span><span class="sxs-lookup"><span data-stu-id="defdb-219">Consider that you're waiting asynchronously for an operation to complete while simultaneously responding to a user’s cancellation request (for example, the user clicked a cancel button).</span></span> <span data-ttu-id="defdb-220">Aşağıdaki kod, bu senaryo gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="defdb-220">The following code illustrates this scenario:</span></span>  
  
```csharp  
private CancellationTokenSource m_cts;   
  
public void btnCancel_Click(object sender, EventArgs e)  
{  
    if (m_cts != null) m_cts.Cancel();  
}  
  
public async void btnRun_Click(object sender, EventArgs e)  
{  
    m_cts = new CancellationTokenSource();  
    btnRun.Enabled = false;  
    try  
    {  
        Task<Bitmap> imageDownload = GetBitmapAsync(txtUrl.Text);   
        await UntilCompletionOrCancellation(imageDownload, m_cts.Token);  
        if (imageDownload.IsCompleted)  
        {  
            Bitmap image = await imageDownload;  
            panel.AddImage(image);  
        }  
        else imageDownload.ContinueWith(t => Log(t));  
    }  
    finally { btnRun.Enabled = true; }  
}  
  
private static async Task UntilCompletionOrCancellation(  
    Task asyncOp, CancellationToken ct)  
{  
    var tcs = new TaskCompletionSource<bool>();  
    using(ct.Register(() => tcs.TrySetResult(true)))  
        await Task.WhenAny(asyncOp, tcs.Task);  
    return asyncOp;  
}  
```  
  
 <span data-ttu-id="defdb-221">Bail karar, ancak temel alınan zaman uyumsuz işlemlerin iptal edilmiyor hemen sonra bu uygulama kullanıcı arabirimi yeniden etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="defdb-221">This implementation re-enables the user interface as soon as you decide to bail out, but doesn't cancel the underlying asynchronous operations.</span></span>  <span data-ttu-id="defdb-222">Bail, ancak kullanıcı arabirimi olasılığı nedeniyle iptal isteği nedeniyle erken bitiş gerçekten tam işlemleri kadar oluşturmayacak karar bekleyen işlemler iptal etmek için başka bir seçenek olacaktır:</span><span class="sxs-lookup"><span data-stu-id="defdb-222">Another alternative would be to cancel the pending operations when you decide to bail out, but not reestablish the user interface until the operations actually complete, potentially due to ending early due to the cancellation request:</span></span>  
  
```csharp  
private CancellationTokenSource m_cts;  
  
public async void btnRun_Click(object sender, EventArgs e)  
{  
    m_cts = new CancellationTokenSource();  
  
    btnRun.Enabled = false;  
    try  
    {  
        Task<Bitmap> imageDownload = GetBitmapAsync(txtUrl.Text, m_cts.Token);   
        await UntilCompletionOrCancellation(imageDownload, m_cts.Token);  
        Bitmap image = await imageDownload;  
        panel.AddImage(image);  
    }  
    catch(OperationCanceledException) {}  
    finally { btnRun.Enabled = true; }  
}  
```  
  
 <span data-ttu-id="defdb-223">Başka bir örneği erken BailOut komutunu kullanılmasına <xref:System.Threading.Tasks.Task.WhenAny%2A> yöntemi ile birlikte <xref:System.Threading.Tasks.Task.Delay%2A> yöntemi, sonraki bölümde açıklandığı gibi.</span><span class="sxs-lookup"><span data-stu-id="defdb-223">Another example of early bailout involves using the <xref:System.Threading.Tasks.Task.WhenAny%2A> method in conjunction with the <xref:System.Threading.Tasks.Task.Delay%2A> method, as discussed in the next section.</span></span>  
  
### <a name="taskdelay"></a><span data-ttu-id="defdb-224">Task.Delay</span><span class="sxs-lookup"><span data-stu-id="defdb-224">Task.Delay</span></span>  
 <span data-ttu-id="defdb-225">Kullanabileceğiniz <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> tanıtmak için yöntemi içinde zaman uyumsuz bir yöntemin yürütülmesine duraklatır.</span><span class="sxs-lookup"><span data-stu-id="defdb-225">You can use the <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> method to introduce pauses into an asynchronous method’s execution.</span></span>  <span data-ttu-id="defdb-226">Bu işlevsellik, yoklama döngüler oluşturmak ve kullanıcı girişini işleme önceden belirlenmiş bir süre için erteleme dahil olmak üzere birçok türdeki için kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="defdb-226">This is useful for many kinds of functionality, including building polling loops and delaying the handling of user input for a predetermined period of time.</span></span>  <span data-ttu-id="defdb-227"><xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> Yöntemi de birlikte yararlı olabilir <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> için zaman aşımları, üzerinde uygulama bekler.</span><span class="sxs-lookup"><span data-stu-id="defdb-227">The <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> method can also be useful in combination with <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> for implementing time-outs on awaits.</span></span>  
  
 <span data-ttu-id="defdb-228">Daha büyük bir zaman uyumsuz işlemi (örneğin, bir ASP.NET web hizmeti) parçası olan bir görevin tamamlanması çok uzun sürerse, genel işlem etkilese, özellikle için hiç başarısız olursa tamamlayın.</span><span class="sxs-lookup"><span data-stu-id="defdb-228">If a task that’s part of a larger asynchronous operation (for example, an ASP.NET web service) takes too long to complete, the overall operation could suffer, especially if it fails to ever complete.</span></span>  <span data-ttu-id="defdb-229">Bu nedenle, zaman uyumsuz bir işlemi beklenirken zaman aşımına görebilmek önemlidir.</span><span class="sxs-lookup"><span data-stu-id="defdb-229">For this reason, it’s important to be able to time out when waiting on an asynchronous operation.</span></span>  <span data-ttu-id="defdb-230">Zaman uyumlu <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Task.WaitAll%2A?displayProperty=nameWithType>, ve <xref:System.Threading.Tasks.Task.WaitAny%2A?displayProperty=nameWithType> yöntemleri zaman aşımı değerlerini, ancak karşılık gelen, kabul <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType> / <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> ve daha önce bahsedilen <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> / <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>yöntemleri yapın.</span><span class="sxs-lookup"><span data-stu-id="defdb-230">The synchronous <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Task.WaitAll%2A?displayProperty=nameWithType>, and <xref:System.Threading.Tasks.Task.WaitAny%2A?displayProperty=nameWithType> methods accept time-out values, but the corresponding <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType>/<xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> and the previously mentioned <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>/<xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> methods do not.</span></span>  <span data-ttu-id="defdb-231">Bunun yerine kullanabileceğiniz <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> ve <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> birlikte bir zaman aşımı uygulamak için.</span><span class="sxs-lookup"><span data-stu-id="defdb-231">Instead, you can use <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> in combination to implement a time-out.</span></span>  
  
 <span data-ttu-id="defdb-232">Örneğin, kullanıcı Arabirimi uygulamanızda bir resim indirmek ve görüntü yüklenirken kullanıcı arabirimini devre dışı bırakmak istediğinizi varsayalım.</span><span class="sxs-lookup"><span data-stu-id="defdb-232">For example, in your UI application, let's say that you want to download an image and disable the UI while the image is downloading.</span></span> <span data-ttu-id="defdb-233">Ancak, yükleme çok uzun sürerse, kullanıcı arabirimini yeniden etkinleştirme ve indirme atmak istiyor:</span><span class="sxs-lookup"><span data-stu-id="defdb-233">However, if the download takes too long, you want to re-enable the UI and discard the download:</span></span>  
  
```csharp  
public async void btnDownload_Click(object sender, EventArgs e)  
{  
    btnDownload.Enabled = false;  
    try  
    {  
        Task<Bitmap> download = GetBitmapAsync(url);  
        if (download == await Task.WhenAny(download, Task.Delay(3000)))  
        {  
            Bitmap bmp = await download;  
            pictureBox.Image = bmp;  
            status.Text = "Downloaded";  
        }  
        else  
        {  
            pictureBox.Image = null;  
            status.Text = "Timed out";  
            var ignored = download.ContinueWith(  
                t => Trace("Task finally completed"));  
        }  
    }  
    finally { btnDownload.Enabled = true; }  
}  
```  
  
 <span data-ttu-id="defdb-234">Aynı çünkü birden çok indirmeler için geçerlidir <xref:System.Threading.Tasks.Task.WhenAll%2A> bir görev döndürür:</span><span class="sxs-lookup"><span data-stu-id="defdb-234">The same applies to multiple downloads, because <xref:System.Threading.Tasks.Task.WhenAll%2A> returns a task:</span></span>  
  
```csharp  
public async void btnDownload_Click(object sender, RoutedEventArgs e)  
{  
    btnDownload.Enabled = false;  
    try  
    {  
        Task<Bitmap[]> downloads =   
            Task.WhenAll(from url in urls select GetBitmapAsync(url));  
        if (downloads == await Task.WhenAny(downloads, Task.Delay(3000)))  
        {  
            foreach(var bmp in downloads) panel.AddImage(bmp);  
            status.Text = "Downloaded";  
        }  
        else  
        {  
            status.Text = "Timed out";  
            downloads.ContinueWith(t => Log(t));  
        }  
    }  
    finally { btnDownload.Enabled = true; }  
}  
```  
  
## <a name="building-task-based-combinators"></a><span data-ttu-id="defdb-235">Görev tabanlı Kombinatör oluşturma</span><span class="sxs-lookup"><span data-stu-id="defdb-235">Building Task-based Combinators</span></span>  
 <span data-ttu-id="defdb-236">Tamamen zaman uyumsuz işlemi temsil eden ve birleştirme işlemi için zaman uyumlu ve zaman uyumsuz özellikler sağlamak için bir görev olduğundan, kendi sonuçları ve benzeri, görevler oluşturan kombinatörlere yararlı kitaplıkları oluşturabilirsiniz daha büyük düzenleri oluşturun.</span><span class="sxs-lookup"><span data-stu-id="defdb-236">Because a task is able to completely represent an asynchronous operation and provide synchronous and asynchronous capabilities for joining with the operation, retrieving its results, and so on, you can build useful libraries of combinators that compose tasks to build larger patterns.</span></span>  <span data-ttu-id="defdb-237">Önceki bölümde açıklandığı gibi .NET Framework birkaç yerleşik kombinatör içerir, ancak Ayrıca kendi oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="defdb-237">As discussed in the previous section, the .NET Framework includes several built-in combinators, but you can also build your own.</span></span> <span data-ttu-id="defdb-238">Aşağıdaki bölümler, olası combinator tarafından kurulan yöntemleri ve türleri çeşitli örneklerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="defdb-238">The following sections provide several examples of potential combinator methods and types.</span></span>  
  
### <a name="retryonfault"></a><span data-ttu-id="defdb-239">RetryOnFault</span><span class="sxs-lookup"><span data-stu-id="defdb-239">RetryOnFault</span></span>  
 <span data-ttu-id="defdb-240">Çoğu durumda, bir önceki girişim başarısız olursa bir işlemi yeniden deneyin. isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="defdb-240">In many situations, you may want to retry an operation if a previous attempt fails.</span></span>  <span data-ttu-id="defdb-241">Zaman uyumlu bir kod için bir yardımcı yöntem gibi derleme `RetryOnFault` bunu gerçekleştirmek için aşağıdaki örnekte:</span><span class="sxs-lookup"><span data-stu-id="defdb-241">For synchronous code, you might build a helper method such as `RetryOnFault` in the following example to accomplish this:</span></span>  
  
```csharp  
public static T RetryOnFault<T>(  
    Func<T> function, int maxTries)  
{  
    for(int i=0; i<maxTries; i++)  
    {  
        try { return function(); }  
        catch { if (i == maxTries-1) throw; }  
    }  
    return default(T);  
}  
```  
  
 <span data-ttu-id="defdb-242">Bir neredeyse aynı yardımcı yöntem DOKUNARAK uygulanır ve bu nedenle görevleri döndürür zaman uyumsuz işlemlerin oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="defdb-242">You can build an almost identical helper method for asynchronous operations that are implemented with TAP and thus return tasks:</span></span>  
  
```csharp  
public static async Task<T> RetryOnFault<T>(  
    Func<Task<T>> function, int maxTries)  
{  
    for(int i=0; i<maxTries; i++)  
    {  
        try { return await function().ConfigureAwait(false); }  
        catch { if (i == maxTries-1) throw; }  
    }  
    return default(T);  
}  
```  
  
 <span data-ttu-id="defdb-243">Ardından, yeniden denemeleri uygulama mantığı eklemenize kodlamak için bu combinator tarafından kurulan kullanabilirsiniz; Örneğin:</span><span class="sxs-lookup"><span data-stu-id="defdb-243">You can then use this combinator to encode retries into the application’s logic; for example:</span></span>  
  
```csharp  
// Download the URL, trying up to three times in case of failure  
string pageContents = await RetryOnFault(  
    () => DownloadStringAsync(url), 3);  
```  
  
 <span data-ttu-id="defdb-244">Genişletilebiliyordu `RetryOnFault` daha fazla işlev.</span><span class="sxs-lookup"><span data-stu-id="defdb-244">You could extend the `RetryOnFault` function further.</span></span> <span data-ttu-id="defdb-245">İşlev başka bir örneğin kabul edebilecek `Func<Task>` yeniden denemeler arasında yeniden; örneğin işlemi denemek ne zaman belirlemek için çağrılacak:</span><span class="sxs-lookup"><span data-stu-id="defdb-245">For example, the function could accept another `Func<Task>` that will be invoked between retries to determine when to try the operation again; for example:</span></span>  
  
```csharp  
public static async Task<T> RetryOnFault<T>(  
    Func<Task<T>> function, int maxTries, Func<Task> retryWhen)  
{  
    for(int i=0; i<maxTries; i++)  
    {  
        try { return await function().ConfigureAwait(false); }  
        catch { if (i == maxTries-1) throw; }  
        await retryWhen().ConfigureAwait(false);  
    }  
    return default(T);  
}  
```  
  
 <span data-ttu-id="defdb-246">Ardından işlev gibi ikinci bir işlemi yeniden denemeden önce beklenecek kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="defdb-246">You could then use the function as follows to wait for a second before retrying the operation:</span></span>  
  
```csharp  
// Download the URL, trying up to three times in case of failure,  
// and delaying for a second between retries  
string pageContents = await RetryOnFault(  
    () => DownloadStringAsync(url), 3, () => Task.Delay(1000));  
```  
  
### <a name="needonlyone"></a><span data-ttu-id="defdb-247">NeedOnlyOne</span><span class="sxs-lookup"><span data-stu-id="defdb-247">NeedOnlyOne</span></span>  
 <span data-ttu-id="defdb-248">Bazı durumlarda, bir işlemin gecikme süresi ve başarı olasılığını artırmak için yedeklilik yararlanabilir.</span><span class="sxs-lookup"><span data-stu-id="defdb-248">Sometimes, you can take advantage of redundancy to improve an operation’s latency and chances for success.</span></span>  <span data-ttu-id="defdb-249">Hisse senedi fiyatlarını sağlayan birden çok web hizmetlerinden göz önünde bulundurun, ancak günü çeşitli zamanlarda her hizmet kalitesi ve yanıt sürelerini farklı düzeylerde sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="defdb-249">Consider multiple web services that provide stock quotes, but at various times of the day, each service may provide different levels of quality and response times.</span></span>  <span data-ttu-id="defdb-250">Bu dalgalanmaları ile dağıtılacak verme isteği göndermek için tüm web hizmetleri ve birinden, yanıt alın hemen sonra kalan istekleri iptal.</span><span class="sxs-lookup"><span data-stu-id="defdb-250">To deal with these fluctuations, you may issue requests to all the web services, and as soon as you get a response from one, cancel the remaining requests.</span></span>  <span data-ttu-id="defdb-251">Birden çok işlemi başlatılıyor, için bekleyen ve ardından kalan iptal ortak Bu tasarımın daha kolay hale getirmek için bir yardımcı işlevinizi uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="defdb-251">You can implement a helper function to make it easier to implement this common pattern of launching multiple operations, waiting for any, and then canceling the rest.</span></span> <span data-ttu-id="defdb-252">`NeedOnlyOne` İşlevi aşağıdaki örnekte, bu senaryo gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="defdb-252">The `NeedOnlyOne` function in the following example illustrates this scenario:</span></span>  
  
```csharp  
public static async Task<T> NeedOnlyOne(  
    params Func<CancellationToken,Task<T>> [] functions)  
{  
    var cts = new CancellationTokenSource();  
    var tasks = (from function in functions  
                 select function(cts.Token)).ToArray();  
    var completed = await Task.WhenAny(tasks).ConfigureAwait(false);  
    cts.Cancel();  
    foreach(var task in tasks)   
    {  
        var ignored = task.ContinueWith(  
            t => Log(t), TaskContinuationOptions.OnlyOnFaulted);  
    }  
    return completed;  
}  
```  
  
 <span data-ttu-id="defdb-253">Ardından, bu işlev şu şekilde kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="defdb-253">You can then use this function as follows:</span></span>  
  
```csharp  
double currentPrice = await NeedOnlyOne(  
    ct => GetCurrentPriceFromServer1Async("msft", ct),  
    ct => GetCurrentPriceFromServer2Async("msft", ct),  
    ct => GetCurrentPriceFromServer3Async("msft", ct));  
```  
  
### <a name="interleaved-operations"></a><span data-ttu-id="defdb-254">Dönüşümlü işlemler</span><span class="sxs-lookup"><span data-stu-id="defdb-254">Interleaved Operations</span></span>  
 <span data-ttu-id="defdb-255">Kullanırken olası performans sorunu var. <xref:System.Threading.Tasks.Task.WhenAny%2A> görevleri çok büyük kümeleriyle çalışırken bir araya senaryoyu desteklemek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="defdb-255">There is a potential performance problem with using the <xref:System.Threading.Tasks.Task.WhenAny%2A> method to support an interleaving scenario when you're working with very large sets of tasks.</span></span>  <span data-ttu-id="defdb-256">Yapılan her çağrı <xref:System.Threading.Tasks.Task.WhenAny%2A> her görevle Kaydedilmekte devamlılık sonuçlanıyor.</span><span class="sxs-lookup"><span data-stu-id="defdb-256">Every call to <xref:System.Threading.Tasks.Task.WhenAny%2A> results in a continuation being registered with each task.</span></span> <span data-ttu-id="defdb-257">N pek çok görev için araya işlem yaşam süresi boyunca oluşturulan O(N2) devamlılıklar sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="defdb-257">For N number of tasks, this results in O(N2) continuations created over the lifetime of the interleaving operation.</span></span>  <span data-ttu-id="defdb-258">Çok sayıda görev ile çalışıyorsanız, bir combinator tarafından kurulan kullanabilirsiniz (`Interleaved` aşağıdaki örnekte) performans sorunu çözmek için:</span><span class="sxs-lookup"><span data-stu-id="defdb-258">If you're working with a large set of tasks, you can use a combinator  (`Interleaved` in the following example) to address the performance issue:</span></span>  
  
```csharp  
static IEnumerable<Task<T>> Interleaved<T>(IEnumerable<Task<T>> tasks)  
{  
    var inputTasks = tasks.ToList();  
    var sources = (from _ in Enumerable.Range(0, inputTasks.Count)   
                   select new TaskCompletionSource<T>()).ToList();  
    int nextTaskIndex = -1;  
    foreach (var inputTask in inputTasks)  
    {  
        inputTask.ContinueWith(completed =>  
        {  
            var source = sources[Interlocked.Increment(ref nextTaskIndex)];  
            if (completed.IsFaulted)   
                source.TrySetException(completed.Exception.InnerExceptions);  
            else if (completed.IsCanceled)   
                source.TrySetCanceled();  
            else   
                source.TrySetResult(completed.Result);  
        }, CancellationToken.None,   
           TaskContinuationOptions.ExecuteSynchronously,   
           TaskScheduler.Default);  
    }  
    return from source in sources   
           select source.Task;  
}  
```  
  
 <span data-ttu-id="defdb-259">Ardından, combinator tarafından kurulan sonuçlarını görevleri tamamlandıkça işleme için de kullanabilirsiniz; Örneğin:</span><span class="sxs-lookup"><span data-stu-id="defdb-259">You can then use the combinator to process the results of tasks as they complete; for example:</span></span>  
  
```csharp  
IEnumerable<Task<int>> tasks = ...;  
foreach(var task in Interleaved(tasks))  
{  
    int result = await task;  
    …  
}  
```  
  
### <a name="whenallorfirstexception"></a><span data-ttu-id="defdb-260">WhenAllOrFirstException</span><span class="sxs-lookup"><span data-stu-id="defdb-260">WhenAllOrFirstException</span></span>  
 <span data-ttu-id="defdb-261">Bunlardan biri, bu durumda, özel durum oluşur oluşmaz beklemeyi durdurmak istediğiniz hataları sürece belirli dağıtma/toplama senaryolarda, bir kümedeki tüm görevler için beklenecek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="defdb-261">In certain scatter/gather scenarios, you might want to wait for all tasks in a set, unless one of them faults, in which case you want to stop waiting as soon as the exception occurs.</span></span>  <span data-ttu-id="defdb-262">Bir combinator tarafından kurulan yöntemiyle gibi gerçekleştirebilirsiniz `WhenAllOrFirstException` aşağıdaki örnekte:</span><span class="sxs-lookup"><span data-stu-id="defdb-262">You can accomplish that with a combinator method such as `WhenAllOrFirstException` in the following example:</span></span>  
  
```csharp  
public static Task<T[]> WhenAllOrFirstException<T>(IEnumerable<Task<T>> tasks)  
{  
    var inputs = tasks.ToList();  
    var ce = new CountdownEvent(inputs.Count);  
    var tcs = new TaskCompletionSource<T[]>();  
  
    Action<Task> onCompleted = (Task completed) =>  
    {  
        if (completed.IsFaulted)   
            tcs.TrySetException(completed.Exception.InnerExceptions);  
        if (ce.Signal() && !tcs.Task.IsCompleted)  
            tcs.TrySetResult(inputs.Select(t => t.Result).ToArray());  
    };  
  
    foreach (var t in inputs) t.ContinueWith(onCompleted);  
    return tcs.Task;  
}  
```  
  
## <a name="building-task-based-data-structures"></a><span data-ttu-id="defdb-263">Yapı görev-tabanlı veri yapıları</span><span class="sxs-lookup"><span data-stu-id="defdb-263">Building Task-based Data Structures</span></span>  
 <span data-ttu-id="defdb-264">Özel görev tabanlı kombinatör derleme özelliğine ek olarak, bir veri yapısına sahip olmanın <xref:System.Threading.Tasks.Task> ve <xref:System.Threading.Tasks.Task%601> sonuçlarını zaman uyumsuz bir işlemin temsil eden ve çok güçlü getirir ile katılmak için gerekli eşitleme zaman uyumsuz senaryolarında kullanılmak üzere özel veri yapılarını oluşturmak için yazın.</span><span class="sxs-lookup"><span data-stu-id="defdb-264">In addition to the ability to build custom task-based combinators, having a data structure in <xref:System.Threading.Tasks.Task> and <xref:System.Threading.Tasks.Task%601> that represents both the results of an asynchronous operation and the necessary synchronization to join with it makes it a very powerful type on which to build custom data structures to be used in asynchronous scenarios.</span></span>  
  
### <a name="asynccache"></a><span data-ttu-id="defdb-265">AsyncCache</span><span class="sxs-lookup"><span data-stu-id="defdb-265">AsyncCache</span></span>  
 <span data-ttu-id="defdb-266">Biri önemli bir yönüdür bir görevin, hepsi await Bu, kayıt devamlılıklarla birden çok tüketiciye. Bu sayede, alın, sonuç ya da özel durumlar (durumunda <xref:System.Threading.Tasks.Task%601>) ve benzeri.</span><span class="sxs-lookup"><span data-stu-id="defdb-266">One important aspect of a task is that it may be handed out to multiple consumers, all of whom may await it, register continuations with it, get its result or exceptions (in the case of <xref:System.Threading.Tasks.Task%601>), and so on.</span></span>  <span data-ttu-id="defdb-267">Böylece <xref:System.Threading.Tasks.Task> ve <xref:System.Threading.Tasks.Task%601> mükemmel uygun zaman uyumsuz bir önbelleğe alma altyapısı kullanılacak.</span><span class="sxs-lookup"><span data-stu-id="defdb-267">This makes <xref:System.Threading.Tasks.Task> and <xref:System.Threading.Tasks.Task%601> perfectly suited to be used in an asynchronous caching infrastructure.</span></span>  <span data-ttu-id="defdb-268">Küçük bir örnek aşağıda verilmiştir ancak güçlü zaman uyumsuz önbelleği kurulmuştur üst kısmındaki <xref:System.Threading.Tasks.Task%601>:</span><span class="sxs-lookup"><span data-stu-id="defdb-268">Here’s an example of a small but powerful asynchronous cache built on top of <xref:System.Threading.Tasks.Task%601>:</span></span>  
  
```csharp  
public class AsyncCache<TKey, TValue>  
{  
    private readonly Func<TKey, Task<TValue>> _valueFactory;  
    private readonly ConcurrentDictionary<TKey, Lazy<Task<TValue>>> _map;  
  
    public AsyncCache(Func<TKey, Task<TValue>> valueFactory)  
    {  
        if (valueFactory == null) throw new ArgumentNullException("loader");  
        _valueFactory = valueFactory;  
        _map = new ConcurrentDictionary<TKey, Lazy<Task<TValue>>>();  
    }  
  
    public Task<TValue> this[TKey key]  
    {  
        get  
        {  
            if (key == null) throw new ArgumentNullException("key");  
            return _map.GetOrAdd(key, toAdd =>   
                new Lazy<Task<TValue>>(() => _valueFactory(toAdd))).Value;  
        }  
    }  
}  
```  
  
 <span data-ttu-id="defdb-269">[AsyncCache\<TKey, TValue >](https://blogs.msdn.microsoft.com/pfxteam/2010/04/23/parallelextensionsextras-tour-12-asynccache/) sınıf kabul oluşturucusuna bir temsilci olarak alan bir işlev bir `TKey` ve döndüren bir <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="defdb-269">The [AsyncCache\<TKey,TValue>](https://blogs.msdn.microsoft.com/pfxteam/2010/04/23/parallelextensionsextras-tour-12-asynccache/) class accepts as a delegate to its constructor a function that takes a `TKey` and returns a <xref:System.Threading.Tasks.Task%601>.</span></span>  <span data-ttu-id="defdb-270">Daha önce erişilen tüm değerleri önbellekten iç sözlükte depolanır ve `AsyncCache` anahtar başına, yalnızca bir görev oluşturulur, aynı anda bir önbelleğe eriştikten bile sağlar.</span><span class="sxs-lookup"><span data-stu-id="defdb-270">Any previously accessed values from the cache are stored in the internal dictionary, and the `AsyncCache` ensures that only one task is generated per key, even if the cache is accessed concurrently.</span></span>  
  
 <span data-ttu-id="defdb-271">Örneğin, karşıdan yüklenen web sayfaları için bir önbelleği oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="defdb-271">For example, you can build a cache for downloaded web pages:</span></span>  
  
```csharp  
private AsyncCache<string,string> m_webPages =   
    new AsyncCache<string,string>(DownloadStringAsync);  
```  
  
 <span data-ttu-id="defdb-272">Bir web sayfasının içeriğini ihtiyaç duyduğunuzda, bu zaman uyumsuz yöntemler önbellekte kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="defdb-272">You can then use this cache in asynchronous methods whenever you need the contents of a web page.</span></span> <span data-ttu-id="defdb-273">`AsyncCache` Sınıfı, olabildiğince az sayfaları mümkün ve önbellekler sonuçları karşıdan yükleme olduğunu sağlar.</span><span class="sxs-lookup"><span data-stu-id="defdb-273">The `AsyncCache` class ensures that you’re downloading as few pages as possible, and caches the results.</span></span>  
  
```csharp  
private async void btnDownload_Click(object sender, RoutedEventArgs e)   
{  
    btnDownload.IsEnabled = false;  
    try  
    {  
        txtContents.Text = await m_webPages["http://www.microsoft.com"];  
    }  
    finally { btnDownload.IsEnabled = true; }  
}  
```  
  
### <a name="asyncproducerconsumercollection"></a><span data-ttu-id="defdb-274">AsyncProducerConsumerCollection</span><span class="sxs-lookup"><span data-stu-id="defdb-274">AsyncProducerConsumerCollection</span></span>  
 <span data-ttu-id="defdb-275">Görevler de zaman uyumsuz etkinlikler koordine için veri yapıları oluşturmak için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="defdb-275">You can also use tasks to build data structures for coordinating asynchronous activities.</span></span>  <span data-ttu-id="defdb-276">Klasik paralel tasarım desenleri birini göz önünde bulundurun: üretici/tüketici.</span><span class="sxs-lookup"><span data-stu-id="defdb-276">Consider one of the classic parallel design patterns: producer/consumer.</span></span>  <span data-ttu-id="defdb-277">Bu düzen tüketiciler tarafından tüketilen veri Üreticiler oluşturmak ve üreticilerin ve tüketicilerin paralel olarak çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="defdb-277">In this pattern, producers generate data that is consumed by consumers, and the producers and consumers may run in parallel.</span></span> <span data-ttu-id="defdb-278">Örneğin, tüketici artık 2 öğesini oluşturan bir üretici tarafından daha önce oluşturulan 1 ' öğesi işler.</span><span class="sxs-lookup"><span data-stu-id="defdb-278">For example, the consumer processes item 1, which was previously generated by a producer who is now producing item 2.</span></span>  <span data-ttu-id="defdb-279">Üretici/tüketici düzeni için neredeyse şaşmaz biçimde tüketicileri yeni veri bildirilebilir ve kullanılabilir olduğunda bulmak için üreticileri tarafından oluşturulan iş depolamak için bazı veri yapısı gerekir.</span><span class="sxs-lookup"><span data-stu-id="defdb-279">For the producer/consumer pattern, you invariably need some data structure to store the work created by producers so that the consumers may be notified of new data and find it when available.</span></span>  
  
 <span data-ttu-id="defdb-280">Üreticilerin ve tüketicilerin kullanılmak üzere zaman uyumsuz yöntemler sağlayan görevleri üzerinde oluşturulmuş bir basit veri yapısı şu şekildedir:</span><span class="sxs-lookup"><span data-stu-id="defdb-280">Here’s a simple data structure built on top of tasks that enables asynchronous methods to be used as producers and consumers:</span></span>  
  
```csharp  
public class AsyncProducerConsumerCollection<T>  
{  
    private readonly Queue<T> m_collection = new Queue<T>();  
    private readonly Queue<TaskCompletionSource<T>> m_waiting =   
        new Queue<TaskCompletionSource<T>>();  
  
    public void Add(T item)  
    {  
        TaskCompletionSource<T> tcs = null;  
        lock (m_collection)  
        {  
            if (m_waiting.Count > 0) tcs = m_waiting.Dequeue();  
            else m_collection.Enqueue(item);  
        }  
        if (tcs != null) tcs.TrySetResult(item);  
    }  
  
    public Task<T> Take()  
    {  
        lock (m_collection)  
        {  
            if (m_collection.Count > 0)   
            {  
                return Task.FromResult(m_collection.Dequeue());   
            }  
            else   
            {  
                var tcs = new TaskCompletionSource<T>();  
                m_waiting.Enqueue(tcs);  
                return tcs.Task;  
            }  
        }  
    }  
}  
```  
  
 <span data-ttu-id="defdb-281">Bu yerinde veri yapısı ile aşağıdaki gibi bir kod yazabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="defdb-281">With that data structure in place, you can write code such as the following:</span></span>  
  
```csharp  
private static AsyncProducerConsumerCollection<int> m_data = …;  
…  
private static async Task ConsumerAsync()  
{  
    while(true)  
    {  
        int nextItem = await m_data.Take();  
        ProcessNextItem(nextItem);  
    }  
}  
…  
private static void Produce(int data)  
{  
    m_data.Add(data);  
}  
```  
  
 <span data-ttu-id="defdb-282"><xref:System.Threading.Tasks.Dataflow> Ad alanı içerir <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> benzer şekilde, ancak bir özel koleksiyon türü oluşturmak zorunda kalmadan kullanabileceğiniz türü:</span><span class="sxs-lookup"><span data-stu-id="defdb-282">The <xref:System.Threading.Tasks.Dataflow> namespace includes the <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> type, which you can use in a similar manner, but without having to build a custom collection type:</span></span>  
  
```csharp  
private static BufferBlock<int> m_data = …;  
…  
private static async Task ConsumerAsync()  
{  
    while(true)  
    {  
        int nextItem = await m_data.ReceiveAsync();  
        ProcessNextItem(nextItem);  
    }  
}  
…  
private static void Produce(int data)  
{  
    m_data.Post(data);  
}  
```  
  
> [!NOTE]
>  <span data-ttu-id="defdb-283"><xref:System.Threading.Tasks.Dataflow> Ad alanı kullanılabilir [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] aracılığıyla **NuGet**.</span><span class="sxs-lookup"><span data-stu-id="defdb-283">The <xref:System.Threading.Tasks.Dataflow> namespace is available in the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] through **NuGet**.</span></span> <span data-ttu-id="defdb-284">İçeren derlemeyi yüklemek için <xref:System.Threading.Tasks.Dataflow> ad içerisinde projenizi açın [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], seçin **NuGet paketlerini Yönet** proje menüsünden ve çevrimiçi Microsoft.Tpl.Dataflow paketini arayın.</span><span class="sxs-lookup"><span data-stu-id="defdb-284">To install the assembly that contains the <xref:System.Threading.Tasks.Dataflow> namespace, open your project in [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], choose **Manage NuGet Packages** from the Project menu, and search online for the Microsoft.Tpl.Dataflow package.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="defdb-285">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="defdb-285">See also</span></span>

- [<span data-ttu-id="defdb-286">Görev Tabanlı Zaman Uyumsuz Desen (TAP)</span><span class="sxs-lookup"><span data-stu-id="defdb-286">Task-based Asynchronous Pattern (TAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)  
- [<span data-ttu-id="defdb-287">Görev Tabanlı Zaman Uyumsuz Deseni Uygulama</span><span class="sxs-lookup"><span data-stu-id="defdb-287">Implementing the Task-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/implementing-the-task-based-asynchronous-pattern.md)  
- [<span data-ttu-id="defdb-288">Diğer Zaman Uyumsuz Desen ve Türlerle Birlikte Çalışma</span><span class="sxs-lookup"><span data-stu-id="defdb-288">Interop with Other Asynchronous Patterns and Types</span></span>](../../../docs/standard/asynchronous-programming-patterns/interop-with-other-asynchronous-patterns-and-types.md)
