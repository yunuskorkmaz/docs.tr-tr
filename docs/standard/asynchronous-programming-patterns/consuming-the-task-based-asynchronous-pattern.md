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
ms.openlocfilehash: 08b5dee94a9a23fdd1c9e635aa2ef848f59e86cf
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2019
ms.locfileid: "70169142"
---
# <a name="consuming-the-task-based-asynchronous-pattern"></a><span data-ttu-id="6ae44-102">Görev Tabanlı Zaman Uyumsuz Desen Kullanma</span><span class="sxs-lookup"><span data-stu-id="6ae44-102">Consuming the Task-based Asynchronous Pattern</span></span>

<span data-ttu-id="6ae44-103">Zaman uyumsuz işlemlerle çalışmak için görev tabanlı zaman uyumsuz model (TAP) kullandığınızda geri çağırmaları kullanarak, engellemeden beklemeyi elde edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6ae44-103">When you use the Task-based Asynchronous Pattern (TAP) to work with asynchronous operations, you can use callbacks to achieve waiting without blocking.</span></span>  <span data-ttu-id="6ae44-104">Görevler için, bu gibi yöntemler <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType>aracılığıyla elde edilir.</span><span class="sxs-lookup"><span data-stu-id="6ae44-104">For tasks, this is achieved through methods such as <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="6ae44-105">Dil tabanlı zaman uyumsuz destek, zaman uyumsuz işlemlerin normal Denetim akışında beklemesine izin vererek geri çağırmaları gizler ve derleyicinin ürettiği kod aynı API düzeyi desteğini sağlar.</span><span class="sxs-lookup"><span data-stu-id="6ae44-105">Language-based asynchronous support hides callbacks by allowing asynchronous operations to be awaited within normal control flow, and compiler-generated code provides this same API-level support.</span></span>

## <a name="suspending-execution-with-await"></a><span data-ttu-id="6ae44-106">Await ile yürütmeyi askıya alma</span><span class="sxs-lookup"><span data-stu-id="6ae44-106">Suspending Execution with Await</span></span>
 <span data-ttu-id="6ae44-107">.NET Framework 4,5 ' den başlayarak, C# içindeki [await](../../csharp/language-reference/operators/await.md) anahtar sözcüğünü ve zaman uyumsuz olarak await <xref:System.Threading.Tasks.Task> ve <xref:System.Threading.Tasks.Task%601> nesneler için Visual Basic [await işlecini](../../visual-basic/language-reference/operators/await-operator.md) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6ae44-107">Starting with the .NET Framework 4.5, you can use the [await](../../csharp/language-reference/operators/await.md) keyword in C# and the [Await Operator](../../visual-basic/language-reference/operators/await-operator.md) in Visual Basic to asynchronously await <xref:System.Threading.Tasks.Task> and <xref:System.Threading.Tasks.Task%601> objects.</span></span> <span data-ttu-id="6ae44-108">Bir <xref:System.Threading.Tasks.Task> 'ı`void`beklerken, ifadetüründedir.`await`</span><span class="sxs-lookup"><span data-stu-id="6ae44-108">When you're awaiting a <xref:System.Threading.Tasks.Task>, the `await` expression is of type `void`.</span></span> <span data-ttu-id="6ae44-109">Bir <xref:System.Threading.Tasks.Task%601> 'ı`TResult`beklerken, ifadetüründedir.`await`</span><span class="sxs-lookup"><span data-stu-id="6ae44-109">When you're awaiting a <xref:System.Threading.Tasks.Task%601>, the `await` expression is of type `TResult`.</span></span> <span data-ttu-id="6ae44-110">Bir `await` ifade, zaman uyumsuz bir metodun gövdesinde gerçekleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="6ae44-110">An `await` expression must occur inside the body of an asynchronous method.</span></span> <span data-ttu-id="6ae44-111">.NET Framework 4,5 Visual Basic dil C# desteği hakkında daha fazla bilgi için bkz. C# ve Visual Basic dil belirtimleri.</span><span class="sxs-lookup"><span data-stu-id="6ae44-111">For more information about C# and Visual Basic language support in the .NET Framework 4.5, see the C# and Visual Basic language specifications.</span></span>

 <span data-ttu-id="6ae44-112">Kapakların altında, await işlevi bir devamlılık kullanarak göreve bir geri çağırma işlemini kurar.</span><span class="sxs-lookup"><span data-stu-id="6ae44-112">Under the covers, the await functionality installs a callback on the task by using a continuation.</span></span>  <span data-ttu-id="6ae44-113">Bu geri çağırma, askıya alma noktasındaki zaman uyumsuz yöntemi sürdürür.</span><span class="sxs-lookup"><span data-stu-id="6ae44-113">This callback resumes the asynchronous method at the point of suspension.</span></span> <span data-ttu-id="6ae44-114">Zaman uyumsuz yöntem devam ettirildiğinde, abeklelen işlem başarıyla tamamlanırsa ve bir <xref:System.Threading.Tasks.Task%601>ise `TResult` , döndürülür.</span><span class="sxs-lookup"><span data-stu-id="6ae44-114">When the asynchronous method is resumed, if the awaited operation completed successfully and was a <xref:System.Threading.Tasks.Task%601>, its `TResult` is returned.</span></span>  <span data-ttu-id="6ae44-115">Durum, durumunda sonlandıysa <xref:System.OperationCanceledException> , bir özel durum oluşturulur. <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601> <xref:System.Threading.Tasks.TaskStatus.Canceled></span><span class="sxs-lookup"><span data-stu-id="6ae44-115">If the <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> that was awaited ended in the <xref:System.Threading.Tasks.TaskStatus.Canceled> state, an <xref:System.OperationCanceledException> exception is thrown.</span></span>  <span data-ttu-id="6ae44-116"><xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.TaskStatus.Faulted> Durum, durumunda sonlandıysa, hataya neden olan özel durum atılır. <xref:System.Threading.Tasks.Task%601></span><span class="sxs-lookup"><span data-stu-id="6ae44-116">If the <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> that was awaited ended in the <xref:System.Threading.Tasks.TaskStatus.Faulted> state, the exception that caused it to fault is thrown.</span></span> <span data-ttu-id="6ae44-117">Bir `Task` , birden çok özel durumun sonucu olarak hata verebilir, ancak bu özel durumların yalnızca biri yayılır.</span><span class="sxs-lookup"><span data-stu-id="6ae44-117">A `Task` can fault as a result of multiple exceptions, but only one of these exceptions is propagated.</span></span> <span data-ttu-id="6ae44-118">Ancak, <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> özelliği tüm hataları içeren <xref:System.AggregateException> bir özel durum döndürür.</span><span class="sxs-lookup"><span data-stu-id="6ae44-118">However, the <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> property returns an <xref:System.AggregateException> exception that contains all the errors.</span></span>

 <span data-ttu-id="6ae44-119">Bir eşitleme bağlamı (<xref:System.Threading.SynchronizationContext> nesne) askıya alma sırasında zaman uyumsuz yöntemi yürüten iş parçacığıyla ilişkiliyse (örneğin, <xref:System.Threading.SynchronizationContext.Current%2A?displayProperty=nameWithType> özellik değilse `null`), zaman uyumsuz yöntem bunun üzerinde devam eder bağlam <xref:System.Threading.SynchronizationContext.Post%2A> yöntemi kullanılarak aynı eşitleme bağlamı.</span><span class="sxs-lookup"><span data-stu-id="6ae44-119">If a synchronization context (<xref:System.Threading.SynchronizationContext> object) is associated with the thread that was executing the asynchronous method at the time of suspension (for example, if the <xref:System.Threading.SynchronizationContext.Current%2A?displayProperty=nameWithType> property is not `null`), the asynchronous method resumes on that same synchronization context by using the context’s <xref:System.Threading.SynchronizationContext.Post%2A> method.</span></span> <span data-ttu-id="6ae44-120">Aksi takdirde, askıya alma sırasında geçerli olan görev<xref:System.Threading.Tasks.TaskScheduler> zamanlayıcısını (nesne) kullanır.</span><span class="sxs-lookup"><span data-stu-id="6ae44-120">Otherwise, it relies on the task scheduler (<xref:System.Threading.Tasks.TaskScheduler> object) that was current at the time of suspension.</span></span> <span data-ttu-id="6ae44-121">Genellikle, bu, iş parçacığı havuzunu hedefleyen varsayılan<xref:System.Threading.Tasks.TaskScheduler.Default%2A?displayProperty=nameWithType>Görev Zamanlayıcı () ' dır.</span><span class="sxs-lookup"><span data-stu-id="6ae44-121">Typically, this is the default task scheduler (<xref:System.Threading.Tasks.TaskScheduler.Default%2A?displayProperty=nameWithType>), which targets the thread pool.</span></span> <span data-ttu-id="6ae44-122">Bu görev zamanlayıcı, beklenen zaman uyumsuz işlemin tamamlandığında veya sürdürme zamanlanıp zamanlanmayacağını belirler.</span><span class="sxs-lookup"><span data-stu-id="6ae44-122">This task scheduler determines whether the awaited asynchronous operation should resume where it completed or whether the resumption should be scheduled.</span></span> <span data-ttu-id="6ae44-123">Varsayılan Zamanlayıcı genellikle devamlılığın tamamlanan işlemin tamamlandığı iş parçacığında çalışmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="6ae44-123">The default scheduler typically allows the continuation to run on the thread that the awaited operation completed.</span></span>

 <span data-ttu-id="6ae44-124">Zaman uyumsuz bir yöntem çağrıldığında, henüz tamamlanmamış olan bir awasever örneğine ilk await ifadesi kadar zaman uyumlu olarak çalışır; bu noktada çağrı çağırana döner.</span><span class="sxs-lookup"><span data-stu-id="6ae44-124">When an asynchronous method is called, it synchronously executes the body of the function up until the first await expression on an awaitable instance that has not yet completed, at which point the invocation returns to the caller.</span></span> <span data-ttu-id="6ae44-125">Zaman uyumsuz yöntem döndürmezse `void`, devam eden hesaplamayı temsil eden bir <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601> nesnesi döndürülür.</span><span class="sxs-lookup"><span data-stu-id="6ae44-125">If the asynchronous method does not return `void`, a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> object is returned to represent the ongoing computation.</span></span> <span data-ttu-id="6ae44-126">Void olmayan bir zaman uyumsuz yöntemde, bir return ifadesine karşılaşılırsa veya Yöntem gövdesinin sonuna ulaşılırsa, görev <xref:System.Threading.Tasks.TaskStatus.RanToCompletion> son durumda tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="6ae44-126">In a non-void asynchronous method, if a return statement is encountered or the end of the method body is reached, the task is completed in the <xref:System.Threading.Tasks.TaskStatus.RanToCompletion> final state.</span></span> <span data-ttu-id="6ae44-127">İşlenmeyen bir özel durum denetimin zaman uyumsuz yöntemin gövdesinden ayrılmasına neden olursa, görev <xref:System.Threading.Tasks.TaskStatus.Faulted> durumunda sonlanır.</span><span class="sxs-lookup"><span data-stu-id="6ae44-127">If an unhandled exception causes control to leave the body of the asynchronous method, the task ends in the <xref:System.Threading.Tasks.TaskStatus.Faulted> state.</span></span> <span data-ttu-id="6ae44-128">Bu özel durum bir <xref:System.OperationCanceledException>ise, görev <xref:System.Threading.Tasks.TaskStatus.Canceled> durumunda sona erer.</span><span class="sxs-lookup"><span data-stu-id="6ae44-128">If that exception is an <xref:System.OperationCanceledException>, the task instead ends in the <xref:System.Threading.Tasks.TaskStatus.Canceled> state.</span></span> <span data-ttu-id="6ae44-129">Bu şekilde, sonuç veya özel durum sonunda yayımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="6ae44-129">In this manner, the result or exception is eventually published.</span></span>

 <span data-ttu-id="6ae44-130">Bu davranışın çeşitli önemli çeşitlemeleri vardır.</span><span class="sxs-lookup"><span data-stu-id="6ae44-130">There are several important variations of this behavior.</span></span>  <span data-ttu-id="6ae44-131">Performans nedenleriyle, görev beklenerek görevin zaten tamamlanmışsa, denetim bir şekilde uygulanmaz ve işlev yürütülmeye devam eder.</span><span class="sxs-lookup"><span data-stu-id="6ae44-131">For performance reasons, if a task has already completed by the time the task is awaited, control is not yielded, and the function continues to execute.</span></span>  <span data-ttu-id="6ae44-132">Ayrıca, özgün bağlamına dönmek her zaman istenen davranış değildir ve değiştirilebilir; Bu, sonraki bölümde daha ayrıntılı olarak açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="6ae44-132">Additionally, returning to the original context isn't always the desired behavior and can be changed; this is described in more detail in the next section.</span></span>

### <a name="configuring-suspension-and-resumption-with-yield-and-configureawait"></a><span data-ttu-id="6ae44-133">Yield ve ConfigureAwait ile askıya alma ve sürdürme yapılandırma</span><span class="sxs-lookup"><span data-stu-id="6ae44-133">Configuring Suspension and Resumption with Yield and ConfigureAwait</span></span>
 <span data-ttu-id="6ae44-134">Çeşitli yöntemler zaman uyumsuz yöntemin yürütülmesi üzerinde daha fazla denetim sağlar.</span><span class="sxs-lookup"><span data-stu-id="6ae44-134">Several methods provide more control over an asynchronous method’s execution.</span></span> <span data-ttu-id="6ae44-135">Örneğin, zaman uyumsuz metoda bir yield <xref:System.Threading.Tasks.Task.Yield%2A?displayProperty=nameWithType> noktası tanıtmak için yöntemini kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="6ae44-135">For example, you can use the <xref:System.Threading.Tasks.Task.Yield%2A?displayProperty=nameWithType> method to introduce a yield point into the asynchronous method:</span></span>

```csharp
public class Task : …
{
    public static YieldAwaitable Yield();
    …
}
```

 <span data-ttu-id="6ae44-136">Bu, zaman uyumsuz naklin veya geçerli bağlamına yeniden zamanlama ile eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="6ae44-136">This is equivalent to asynchronously posting or scheduling back to the current context.</span></span>

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

 <span data-ttu-id="6ae44-137">Ayrıca, <xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=nameWithType> zaman uyumsuz bir yöntemde askıya alma ve sürdürme üzerinde daha iyi denetim için yöntemini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6ae44-137">You can also use the <xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=nameWithType> method for better control over suspension and resumption in an asynchronous method.</span></span>  <span data-ttu-id="6ae44-138">Daha önce belirtildiği gibi, varsayılan olarak, geçerli bağlam zaman uyumsuz bir yöntem askıya alındığında yakalanır ve sürdürme üzerinde zaman uyumsuz yöntemin devamlılığını çağırmak için yakalanan bağlam kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6ae44-138">As mentioned previously, by default, the current context is captured at the time an asynchronous  method is suspended, and that captured context is used to invoke the asynchronous  method’s continuation upon resumption.</span></span>  <span data-ttu-id="6ae44-139">Çoğu durumda bu, istediğiniz tam davranışdır.</span><span class="sxs-lookup"><span data-stu-id="6ae44-139">In many cases, this is the exact behavior you want.</span></span>  <span data-ttu-id="6ae44-140">Diğer durumlarda, devamlılık bağlamıyla ilgilenmeyebilirsiniz ve bu gibi gönderilerin özgün bağlamına geri giderek daha iyi performans elde edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6ae44-140">In other cases, you may not care about the continuation context, and you can achieve better performance by avoiding such posts back to the original context.</span></span>  <span data-ttu-id="6ae44-141">Bunu etkinleştirmek için, await işleminin <xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=nameWithType> bağlam üzerinde yakalanıp sürdürülmeyeceğini bilgilendirmek için yöntemini kullanın, ancak beklenen zaman uyumsuz işlemin tamamlandığı her yerde yürütmeye devam etmek için:</span><span class="sxs-lookup"><span data-stu-id="6ae44-141">To enable this, use the <xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=nameWithType> method to inform the await operation not to capture and resume on the context, but to continue execution wherever the asynchronous operation that was being awaited completed:</span></span>

```csharp
await someTask.ConfigureAwait(continueOnCapturedContext:false);
```

## <a name="canceling-an-asynchronous-operation"></a><span data-ttu-id="6ae44-142">Zaman uyumsuz bir Işlem iptal ediliyor</span><span class="sxs-lookup"><span data-stu-id="6ae44-142">Canceling an Asynchronous Operation</span></span>
 <span data-ttu-id="6ae44-143">.NET Framework 4 ' ten başlayarak, iptali destekleyen yöntemler ' e dokunarak iptal belirtecini kabul eden en az bir aşırı yükleme sağlayın<xref:System.Threading.CancellationToken> (nesne).</span><span class="sxs-lookup"><span data-stu-id="6ae44-143">Starting with the .NET Framework 4, TAP methods that support cancellation provide at least one overload that accepts a cancellation token (<xref:System.Threading.CancellationToken> object).</span></span>

 <span data-ttu-id="6ae44-144">İptal belirteci bir iptal belirteci kaynağı (<xref:System.Threading.CancellationTokenSource> nesne) ile oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="6ae44-144">A cancellation token is created through a cancellation token source (<xref:System.Threading.CancellationTokenSource> object).</span></span>  <span data-ttu-id="6ae44-145">Kaynağın <xref:System.Threading.CancellationTokenSource.Token%2A> özelliği, <xref:System.Threading.CancellationTokenSource.Cancel%2A> kaynağın yöntemi çağrıldığında işaret edilecek iptal belirtecini döndürür.</span><span class="sxs-lookup"><span data-stu-id="6ae44-145">The source’s <xref:System.Threading.CancellationTokenSource.Token%2A> property returns the cancellation token that will be signaled when the source’s <xref:System.Threading.CancellationTokenSource.Cancel%2A> method is called.</span></span>  <span data-ttu-id="6ae44-146">Örneğin, tek bir Web sayfasını indirmek isterseniz ve işlemi iptal etmek istiyorsanız, bir <xref:System.Threading.CancellationTokenSource> nesnesi oluşturur, belirtecini tap yöntemine geçitirsiniz ve ardından işlemi iptal etmeye hazırsanız <xref:System.Threading.CancellationTokenSource.Cancel%2A> kaynağın metodunu çağırın:</span><span class="sxs-lookup"><span data-stu-id="6ae44-146">For example, if you want to download a single webpage and you want to be able to cancel the operation, you create a <xref:System.Threading.CancellationTokenSource> object, pass its token to the TAP method, and then call the source’s <xref:System.Threading.CancellationTokenSource.Cancel%2A> method when you're ready to cancel the operation:</span></span>

```csharp
var cts = new CancellationTokenSource();
string result = await DownloadStringAsync(url, cts.Token);
… // at some point later, potentially on another thread
cts.Cancel();
```

 <span data-ttu-id="6ae44-147">Birden çok zaman uyumsuz çağırma işlemini iptal etmek için, tüm etkinleştirmeleri için aynı belirteci geçirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="6ae44-147">To cancel multiple asynchronous invocations, you can pass the same token to all invocations:</span></span>

```csharp
var cts = new CancellationTokenSource();
    IList<string> results = await Task.WhenAll(from url in urls select DownloadStringAsync(url, cts.Token));
    // at some point later, potentially on another thread
    …
    cts.Cancel();
```

 <span data-ttu-id="6ae44-148">Ya da aynı belirteci bir işlem seçmeli alt kümesine geçirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="6ae44-148">Or, you can pass the same token to a selective subset of operations:</span></span>

```csharp
var cts = new CancellationTokenSource();
    byte [] data = await DownloadDataAsync(url, cts.Token);
    await SaveToDiskAsync(outputPath, data, CancellationToken.None);
    … // at some point later, potentially on another thread
    cts.Cancel();
```

 <span data-ttu-id="6ae44-149">İptal istekleri herhangi bir iş parçacığından başlatılabilir.</span><span class="sxs-lookup"><span data-stu-id="6ae44-149">Cancellation requests may be initiated from any thread.</span></span>

 <span data-ttu-id="6ae44-150">Bu değeri, <xref:System.Threading.CancellationToken.None%2A?displayProperty=nameWithType> İptalin hiçbir şekilde istenmeyeceğini göstermek için iptal belirteci kabul eden herhangi bir yönteme geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6ae44-150">You can pass the <xref:System.Threading.CancellationToken.None%2A?displayProperty=nameWithType> value to any method that accepts a cancellation token to indicate that cancellation will never be requested.</span></span>  <span data-ttu-id="6ae44-151">Bu, <xref:System.Threading.CancellationToken.CanBeCanceled%2A?displayProperty=nameWithType> özelliğin döndürülmesini `false`sağlar ve çağrılan yöntem buna göre iyileştirebilirler.</span><span class="sxs-lookup"><span data-stu-id="6ae44-151">This causes the <xref:System.Threading.CancellationToken.CanBeCanceled%2A?displayProperty=nameWithType> property to return `false`, and the called method can optimize accordingly.</span></span>  <span data-ttu-id="6ae44-152">Sınama amacıyla, belirtecin zaten iptal edilmiş veya iptal edilemez durumunda başlaması gerekip gerekmediğini belirtmek için bir Boole değeri kabul eden oluşturucuyu kullanarak, önceden iptal edilmiş bir iptal belirteci de geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6ae44-152">For testing purposes, you can also pass in a pre-canceled cancellation token that is instantiated by using the constructor that accepts a Boolean value to indicate whether the token should start in an already-canceled or not-cancelable state.</span></span>

 <span data-ttu-id="6ae44-153">Bu iptale yönelik bu yaklaşım birkaç avantaj sağlar:</span><span class="sxs-lookup"><span data-stu-id="6ae44-153">This approach to cancellation has several advantages:</span></span>

- <span data-ttu-id="6ae44-154">Aynı iptal belirtecini herhangi bir sayıda zaman uyumsuz ve zaman uyumlu işleme geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6ae44-154">You can pass the same cancellation token to any number of asynchronous and synchronous operations.</span></span>

- <span data-ttu-id="6ae44-155">Aynı iptal isteği herhangi bir sayıda dinleyiciyle aynı olabilir.</span><span class="sxs-lookup"><span data-stu-id="6ae44-155">The same cancellation request may be proliferated to any number of listeners.</span></span>

- <span data-ttu-id="6ae44-156">Zaman uyumsuz API 'nin geliştiricisi, İptalin istenip istenmeyeceğini ve ne zaman etkili olabileceğini kontrol ediyor.</span><span class="sxs-lookup"><span data-stu-id="6ae44-156">The developer of the asynchronous API is in complete control of whether cancellation may be requested and when it may take effect.</span></span>

- <span data-ttu-id="6ae44-157">API 'YI tüketen kod, iptal isteklerinin yayılacağı zaman uyumsuz çağırmaları seçmeli olarak belirleyebilir.</span><span class="sxs-lookup"><span data-stu-id="6ae44-157">The code that consumes the API may selectively determine the asynchronous invocations that cancellation requests will be propagated to.</span></span>

## <a name="monitoring-progress"></a><span data-ttu-id="6ae44-158">İlerlemeyi İzleme</span><span class="sxs-lookup"><span data-stu-id="6ae44-158">Monitoring Progress</span></span>
 <span data-ttu-id="6ae44-159">Bazı zaman uyumsuz yöntemler, zaman uyumsuz metoda geçirilen bir ilerleme arabirimiyle ilerlemeyi açığa çıkarır.</span><span class="sxs-lookup"><span data-stu-id="6ae44-159">Some asynchronous methods expose progress through a progress interface passed into the asynchronous method.</span></span>  <span data-ttu-id="6ae44-160">Örneğin, bir metin dizesini zaman uyumsuz olarak indiren bir işlevi düşünün ve bu nedenle, şu ana kadar tamamlanan indirme yüzdesini içeren ilerleme güncellemeleri yayınlar.</span><span class="sxs-lookup"><span data-stu-id="6ae44-160">For example, consider a function which asynchronously downloads a string of text, and along the way raises progress updates that include the percentage of the download that has completed thus far.</span></span>  <span data-ttu-id="6ae44-161">Böyle bir yöntem, aşağıdaki gibi bir Windows Presentation Foundation (WPF) uygulamasında tüketilebilir:</span><span class="sxs-lookup"><span data-stu-id="6ae44-161">Such a method could be consumed in a Windows Presentation Foundation (WPF) application as follows:</span></span>

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
## <a name="using-the-built-in-task-based-combinators"></a><span data-ttu-id="6ae44-162">Yerleşik görev tabanlı kombinatör kullanma</span><span class="sxs-lookup"><span data-stu-id="6ae44-162">Using the Built-in Task-based Combinators</span></span>
 <span data-ttu-id="6ae44-163">Ad <xref:System.Threading.Tasks> alanı, görevler oluşturmak ve bunlarla çalışmak için birkaç yöntem içerir.</span><span class="sxs-lookup"><span data-stu-id="6ae44-163">The <xref:System.Threading.Tasks> namespace includes several methods for composing and working with tasks.</span></span>

### <a name="taskrun"></a><span data-ttu-id="6ae44-164">Task. Run</span><span class="sxs-lookup"><span data-stu-id="6ae44-164">Task.Run</span></span>
 <span data-ttu-id="6ae44-165">Sınıfı, iş parçacığı <xref:System.Threading.Tasks.Task.Run%2A> havuzu olarak <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601> iş parçacığını kolayca boşaltmenizi sağlayan çeşitli yöntemler içerir, örneğin: <xref:System.Threading.Tasks.Task></span><span class="sxs-lookup"><span data-stu-id="6ae44-165">The <xref:System.Threading.Tasks.Task> class includes several <xref:System.Threading.Tasks.Task.Run%2A> methods that let you easily offload work as a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> to the thread pool, for example:</span></span>

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

 <span data-ttu-id="6ae44-166">Bu <xref:System.Threading.Tasks.Task.Run%2A> yöntemlerin <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> bazıları (aşırı yükleme gibi), yöntemi için toplu olarak mevcuttur. <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="6ae44-166">Some of these <xref:System.Threading.Tasks.Task.Run%2A> methods, such as the <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType> overload, exist as shorthand for the <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> method.</span></span>  <span data-ttu-id="6ae44-167">Gibi diğer aşırı yüklemeler <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType>, boşaltılan iş içinde await kullanmanıza olanak sağlar, örneğin:</span><span class="sxs-lookup"><span data-stu-id="6ae44-167">Other overloads, such as <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType>, enable you to use await within the offloaded work, for example:</span></span>

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

 <span data-ttu-id="6ae44-168">Bu tür aşırı yüklemeler, görev paralel kitaplığındaki <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> genişletme yöntemiyle birlikte yöntemi kullanılarak mantıksal olarak eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="6ae44-168">Such overloads are logically equivalent to using the <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> method in conjunction with the <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> extension method in the Task Parallel Library.</span></span>

### <a name="taskfromresult"></a><span data-ttu-id="6ae44-169">Task. FromResult</span><span class="sxs-lookup"><span data-stu-id="6ae44-169">Task.FromResult</span></span>
 <span data-ttu-id="6ae44-170">Verilerin zaten kullanılabildiği senaryolarda <xref:System.Threading.Tasks.Task%601> yöntemikullanınveyalnızcabirgörevdöndürenyöntemyükseltilmemiş'ageridöndürülüyor:<xref:System.Threading.Tasks.Task.FromResult%2A></span><span class="sxs-lookup"><span data-stu-id="6ae44-170">Use the <xref:System.Threading.Tasks.Task.FromResult%2A> method in scenarios where data may already be available and just needs to be returned from a task-returning method lifted into a <xref:System.Threading.Tasks.Task%601>:</span></span>

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

### <a name="taskwhenall"></a><span data-ttu-id="6ae44-171">Task.WhenAll</span><span class="sxs-lookup"><span data-stu-id="6ae44-171">Task.WhenAll</span></span>
 <span data-ttu-id="6ae44-172">Görev olarak temsil edilen birden çok zaman uyumsuz işlemde zaman uyumsuz olarak beklemek için yönteminikullanın.<xref:System.Threading.Tasks.Task.WhenAll%2A></span><span class="sxs-lookup"><span data-stu-id="6ae44-172">Use the <xref:System.Threading.Tasks.Task.WhenAll%2A> method to asynchronously wait on multiple asynchronous operations that are represented as tasks.</span></span>  <span data-ttu-id="6ae44-173">Yönteminde, genel olmayan bir görev kümesini veya tek biçimli genel görevler kümesini destekleyen birden çok aşırı yükleme vardır (örneğin, zaman uyumsuz birden fazla void işlem için bekliyor veya birden çok değer döndüren yöntemler için zaman uyumsuz olarak bekleniyor) Her değer farklı bir türe sahip olabilir) ve tek bir genel görev kümesini (örneğin, birden çok `TResult`döndüren yöntemler için zaman uyumsuz) destekler.</span><span class="sxs-lookup"><span data-stu-id="6ae44-173">The method has multiple overloads that support a set of non-generic tasks or a non-uniform set of generic tasks (for example, asynchronously waiting for multiple void-returning operations, or asynchronously waiting for multiple value-returning methods where each value may have a different type) and to support a uniform set of generic tasks (such as asynchronously waiting for multiple `TResult`-returning methods).</span></span>

 <span data-ttu-id="6ae44-174">Birkaç müşteriye e-posta iletileri göndermek istediğinizi varsayalım.</span><span class="sxs-lookup"><span data-stu-id="6ae44-174">Let's say you want to send email messages to several customers.</span></span> <span data-ttu-id="6ae44-175">Bir sonraki göndermeden önce bir iletinin tamamlanmasını beklemmeniz için iletilerin gönderilmesini örtüştürüyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="6ae44-175">You can overlap sending the messages so you're not waiting for one message to complete before sending the next.</span></span> <span data-ttu-id="6ae44-176">Gönderme işlemlerinin ne zaman tamamlandığını ve herhangi bir hata oluşup oluşmadığını da öğrenebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="6ae44-176">You can also find out when the send operations have completed and whether any errors have occurred:</span></span>

```csharp
IEnumerable<Task> asyncOps = from addr in addrs select SendMailAsync(addr);
await Task.WhenAll(asyncOps);
```

 <span data-ttu-id="6ae44-177">Bu kod, oluşabilecek özel durumları açıkça işlemez, ancak özel durumların kaynağından `await` <xref:System.Threading.Tasks.Task.WhenAll%2A>elde edilen görevin dışına yayılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="6ae44-177">This code doesn't explicitly handle exceptions that may occur, but lets exceptions propagate out of the `await` on the resulting task from <xref:System.Threading.Tasks.Task.WhenAll%2A>.</span></span>  <span data-ttu-id="6ae44-178">Özel durumları işlemek için aşağıdakiler gibi bir kod kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="6ae44-178">To handle the exceptions, you can use code such as the following:</span></span>

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

 <span data-ttu-id="6ae44-179">Bu durumda, zaman uyumsuz bir işlem başarısız olursa, tüm özel durumlar, <xref:System.AggregateException> <xref:System.Threading.Tasks.Task.WhenAll%2A> yönteminden döndürülen ' <xref:System.Threading.Tasks.Task> de depolanan bir özel durumla birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="6ae44-179">In this case, if any asynchronous operation fails, all the exceptions will be consolidated in an <xref:System.AggregateException> exception, which is stored in the <xref:System.Threading.Tasks.Task> that is returned from the <xref:System.Threading.Tasks.Task.WhenAll%2A> method.</span></span>  <span data-ttu-id="6ae44-180">Ancak, bu özel durumlardan yalnızca biri `await` anahtar sözcük tarafından yayılır.</span><span class="sxs-lookup"><span data-stu-id="6ae44-180">However, only one of those exceptions is propagated by the `await` keyword.</span></span>  <span data-ttu-id="6ae44-181">Tüm özel durumları incelemek istiyorsanız, önceki kodu aşağıdaki gibi yeniden yazabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="6ae44-181">If you want to examine all the exceptions, you can rewrite the previous code as follows:</span></span>

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

 <span data-ttu-id="6ae44-182">Web 'den zaman uyumsuz olarak birden çok dosya indirme örneği ele alalım.</span><span class="sxs-lookup"><span data-stu-id="6ae44-182">Let's consider an example of downloading multiple files from the web asynchronously.</span></span>  <span data-ttu-id="6ae44-183">Bu durumda, tüm zaman uyumsuz işlemlerin homojen sonuç türleri vardır ve sonuçlara erişmek kolaydır:</span><span class="sxs-lookup"><span data-stu-id="6ae44-183">In this case, all the asynchronous operations have homogeneous result types, and it's easy to access the results:</span></span>

```csharp
string [] pages = await Task.WhenAll(
    from url in urls select DownloadStringAsync(url));
```

 <span data-ttu-id="6ae44-184">Önceki void döndüren senaryoda açıklandığımız aynı özel durum işleme tekniklerini kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="6ae44-184">You can use the same exception-handling techniques we discussed in the previous void-returning scenario:</span></span>

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

### <a name="taskwhenany"></a><span data-ttu-id="6ae44-185">Task.WhenAny</span><span class="sxs-lookup"><span data-stu-id="6ae44-185">Task.WhenAny</span></span>
 <span data-ttu-id="6ae44-186">İşlem için görev olarak <xref:System.Threading.Tasks.Task.WhenAny%2A> temsil edilen birden çok zaman uyumsuz işlemden yalnızca birini zaman uyumsuz olarak beklemek için yöntemini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6ae44-186">You can use the <xref:System.Threading.Tasks.Task.WhenAny%2A> method to asynchronously wait for just one of multiple asynchronous operations represented as tasks to complete.</span></span>  <span data-ttu-id="6ae44-187">Bu yöntem dört birincil kullanım durumu sunar:</span><span class="sxs-lookup"><span data-stu-id="6ae44-187">This method serves four primary use cases:</span></span>

- <span data-ttu-id="6ae44-188">Yedeklilik  Bir işlemi birden çok kez gerçekleştirme ve ilk olarak tamamlanan birini seçme (örneğin, tek bir sonuç üreten ve en hızlı şekilde tamamlanarak birden çok hisse senedi teklifiyle Web hizmeti ile iletişim kurma).</span><span class="sxs-lookup"><span data-stu-id="6ae44-188">Redundancy:  Performing an operation multiple times and selecting the one that completes first (for example, contacting multiple stock quote web services that will produce a single result and selecting the one that completes the fastest).</span></span>

- <span data-ttu-id="6ae44-189">Araya  Birden çok işlem başlatılıyor ve bunların tümünün tamamlanmasını bekliyor, ancak işlemler tamamlandıktan sonra işleniyor.</span><span class="sxs-lookup"><span data-stu-id="6ae44-189">Interleaving:  Launching multiple operations and waiting for all of them to complete, but processing them as they complete.</span></span>

- <span data-ttu-id="6ae44-190">YAVAŞLATMA  Diğer İşlemler tamamlanana kadar ek işlem başlatılmasına izin verme.</span><span class="sxs-lookup"><span data-stu-id="6ae44-190">Throttling:  Allowing additional operations to begin as others complete.</span></span>  <span data-ttu-id="6ae44-191">Bu, araya ekleme senaryosunun bir uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="6ae44-191">This is an extension of the interleaving scenario.</span></span>

- <span data-ttu-id="6ae44-192">Erken baılout:  Örneğin, görev T1 tarafından temsil edilen bir işlem, başka bir görev T2 <xref:System.Threading.Tasks.Task.WhenAny%2A> ile bir görevde gruplandırılabilir ve <xref:System.Threading.Tasks.Task.WhenAny%2A> görevde bekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6ae44-192">Early bailout:  For example, an operation represented by task t1 can be grouped in a <xref:System.Threading.Tasks.Task.WhenAny%2A> task with another task t2, and you can wait on the <xref:System.Threading.Tasks.Task.WhenAny%2A> task.</span></span> <span data-ttu-id="6ae44-193">Görev T2, bir zaman aşımını veya iptali ya da bir <xref:System.Threading.Tasks.Task.WhenAny%2A> görevin T1 tamamlanmadan önce tamamlanmasını sağlayan başka bir sinyali temsil ediyor.</span><span class="sxs-lookup"><span data-stu-id="6ae44-193">Task t2 could represent a time-out, or cancellation, or some other signal that causes the <xref:System.Threading.Tasks.Task.WhenAny%2A> task to complete before t1 completes.</span></span>

#### <a name="redundancy"></a><span data-ttu-id="6ae44-194">Yedeklilik</span><span class="sxs-lookup"><span data-stu-id="6ae44-194">Redundancy</span></span>
 <span data-ttu-id="6ae44-195">Bir stok satın alıp almayacağı konusunda bir karar vermek istediğiniz bir durum düşünün.</span><span class="sxs-lookup"><span data-stu-id="6ae44-195">Consider a case where you want to make a decision about whether to buy a stock.</span></span>  <span data-ttu-id="6ae44-196">Güvendiğiniz birkaç hisse senedi önerisi Web hizmeti bulunur, ancak günlük yüküne bağlı olarak her hizmet farklı zamanlarda yavaş yavaş çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="6ae44-196">There are several stock recommendation web services that you trust, but depending on daily load, each service can end up being slow at different times.</span></span>  <span data-ttu-id="6ae44-197">Herhangi bir işlem tamamlandığında <xref:System.Threading.Tasks.Task.WhenAny%2A> bildirim almak için yöntemini kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="6ae44-197">You can use the <xref:System.Threading.Tasks.Task.WhenAny%2A> method to receive a notification when any operation completes:</span></span>

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

 <span data-ttu-id="6ae44-198">Başarıyla tamamlanan tüm görevlerin sarmalanmamış sonuçlarını döndüren aksine <xref:System.Threading.Tasks.Task.WhenAll%2A>, tamamlanan görevi döndürür.<xref:System.Threading.Tasks.Task.WhenAny%2A></span><span class="sxs-lookup"><span data-stu-id="6ae44-198">Unlike <xref:System.Threading.Tasks.Task.WhenAll%2A>, which returns the unwrapped results of all tasks that completed successfully, <xref:System.Threading.Tasks.Task.WhenAny%2A> returns the task that completed.</span></span> <span data-ttu-id="6ae44-199">Bir görev başarısız olursa, başarısız olması ve bir görevin başarılı olması durumunda, döndürülen değerin hangi görevi ilişkilendirildiğini bilmemiz önemlidir.</span><span class="sxs-lookup"><span data-stu-id="6ae44-199">If a task fails, it’s important to know that it failed, and if a task succeeds, it’s important to know which task the return value is associated with.</span></span>  <span data-ttu-id="6ae44-200">Bu nedenle, döndürülen görevin sonucuna erişmeniz veya bu örnekte gösterildiği gibi daha fazla beklemek gerekir.</span><span class="sxs-lookup"><span data-stu-id="6ae44-200">Therefore, you need to access the result of the returned task, or further await it, as  this example shows.</span></span>

 <span data-ttu-id="6ae44-201">İle <xref:System.Threading.Tasks.Task.WhenAll%2A>olduğu gibi, özel durumlara uyum sağlayabilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="6ae44-201">As with <xref:System.Threading.Tasks.Task.WhenAll%2A>, you have to be able to accommodate exceptions.</span></span>  <span data-ttu-id="6ae44-202">Tamamlanan görevi geri aldığınıza göre döndürülen görevi, hata yayılmasını ve `try/catch` bunları uygun şekilde almanızı sağlayabilirsiniz; örneğin:</span><span class="sxs-lookup"><span data-stu-id="6ae44-202">Because you receive the completed task back, you can await the returned task to have errors propagated, and `try/catch` them appropriately; for example:</span></span>

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

 <span data-ttu-id="6ae44-203">Ayrıca, bir ilk görev başarıyla tamamlanırsa bile sonraki görevler başarısız olabilir.</span><span class="sxs-lookup"><span data-stu-id="6ae44-203">Additionally, even if a first task completes successfully, subsequent tasks may fail.</span></span>  <span data-ttu-id="6ae44-204">Bu noktada, özel durumlarla ilgilenirken çeşitli seçenekleriniz vardır:  Tüm başlatılan görevler tamamlanana kadar bekleyebilirsiniz, bu durumda <xref:System.Threading.Tasks.Task.WhenAll%2A> yöntemini kullanabilir veya tüm özel durumların önemli olduğuna ve günlüğe kaydedilecek şekilde seçim yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6ae44-204">At this point, you have several options for dealing with exceptions:  You can wait until all the launched tasks have completed, in which case you can use the <xref:System.Threading.Tasks.Task.WhenAll%2A> method, or you can decide that all exceptions are important and must be logged.</span></span>  <span data-ttu-id="6ae44-205">Bu şekilde, görevler zaman uyumsuz olarak tamamlandığında bir bildirim almak için devamlılıkları kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="6ae44-205">For this, you can use continuations to receive a notification when tasks have completed asynchronously:</span></span>

```csharp
foreach(Task recommendation in recommendations)
{
    var ignored = recommendation.ContinueWith(
        t => { if (t.IsFaulted) Log(t.Exception); });
}
```

 <span data-ttu-id="6ae44-206">veya:</span><span class="sxs-lookup"><span data-stu-id="6ae44-206">or:</span></span>

```csharp
foreach(Task recommendation in recommendations)
{
    var ignored = recommendation.ContinueWith(
        t => Log(t.Exception), TaskContinuationOptions.OnlyOnFaulted);
}
```

 <span data-ttu-id="6ae44-207">Hatta:</span><span class="sxs-lookup"><span data-stu-id="6ae44-207">or even:</span></span>

```csharp
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

 <span data-ttu-id="6ae44-208">Son olarak, kalan tüm işlemleri iptal etmek isteyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="6ae44-208">Finally, you may want to cancel all the remaining operations:</span></span>

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

#### <a name="interleaving"></a><span data-ttu-id="6ae44-209">Araya</span><span class="sxs-lookup"><span data-stu-id="6ae44-209">Interleaving</span></span>
 <span data-ttu-id="6ae44-210">Web 'den görüntü indirirken ve her görüntüyü işlerken (örneğin, bir kullanıcı arabirimi denetimine görüntü ekleme) bir durum düşünün.</span><span class="sxs-lookup"><span data-stu-id="6ae44-210">Consider a case where you're downloading images from the web and processing each image (for example, adding the image to a UI control).</span></span>  <span data-ttu-id="6ae44-211">İşlem arabirimini Kullanıcı arabirimi iş parçacığında sırayla yapmanız gerekir, ancak görüntüleri mümkün olduğunca eşzamanlı olarak indirmek istersiniz.</span><span class="sxs-lookup"><span data-stu-id="6ae44-211">You have to do the processing sequentially on the UI thread, but you want to download the images as concurrently as possible.</span></span> <span data-ttu-id="6ae44-212">Ayrıca, tümünün indirilene kadar Kullanıcı arabirimine eklemek istemezsiniz, ancak bunları tamamlandığı gibi eklemek istersiniz:</span><span class="sxs-lookup"><span data-stu-id="6ae44-212">Also, you don’t want to hold up adding the images to the UI until they’re all downloaded—you want to add them as they complete:</span></span>

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

 <span data-ttu-id="6ae44-213">Ayrıca, <xref:System.Threading.ThreadPool> indirilen görüntülerin üzerinde yoğun işlem tüketen işleme içeren bir senaryoya araya ekleme uygulayabilirsiniz; örneğin:</span><span class="sxs-lookup"><span data-stu-id="6ae44-213">You can also apply interleaving to a scenario that involves computationally intensive processing on the <xref:System.Threading.ThreadPool> of the downloaded images; for example:</span></span>

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

#### <a name="throttling"></a><span data-ttu-id="6ae44-214">Sınırlama</span><span class="sxs-lookup"><span data-stu-id="6ae44-214">Throttling</span></span>
 <span data-ttu-id="6ae44-215">Kullanıcının indirdiği, indirmelerin kısıtlanacak birçok görüntünün olması dışında, araya ekleme örneğini düşünün; Örneğin, aynı anda yalnızca belirli sayıda indirmelerin gerçekleşmesini istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="6ae44-215">Consider the interleaving example, except that the user is downloading so many images that the downloads have to be throttled; for example, you want only a specific number of downloads to happen concurrently.</span></span> <span data-ttu-id="6ae44-216">Bunu başarmak için, zaman uyumsuz işlemlerin bir alt kümesini başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6ae44-216">To achieve this, you can start a subset of the asynchronous operations.</span></span>  <span data-ttu-id="6ae44-217">İşlemler tamamlandıktan sonra, bunların yerini almak için ek işlemler başlatabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="6ae44-217">As operations complete, you can start additional operations to take their place:</span></span>

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

#### <a name="early-bailout"></a><span data-ttu-id="6ae44-218">Erken Baılout</span><span class="sxs-lookup"><span data-stu-id="6ae44-218">Early Bailout</span></span>
 <span data-ttu-id="6ae44-219">Bir işlemin tamamlanması için zaman uyumsuz olarak bir kullanıcının iptal isteğine (örneğin, Kullanıcı bir iptal düğmesine tıkladığını) göz önünde bulundurdığınızı düşünün.</span><span class="sxs-lookup"><span data-stu-id="6ae44-219">Consider that you're waiting asynchronously for an operation to complete while simultaneously responding to a user’s cancellation request (for example, the user clicked a cancel button).</span></span> <span data-ttu-id="6ae44-220">Aşağıdaki kod bu senaryoyu göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="6ae44-220">The following code illustrates this scenario:</span></span>

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

 <span data-ttu-id="6ae44-221">Bu uygulama, zaman aşımına uğrar, ancak temeldeki zaman uyumsuz işlemleri iptal etmez, Kullanıcı arabirimini yeniden sağlar.</span><span class="sxs-lookup"><span data-stu-id="6ae44-221">This implementation re-enables the user interface as soon as you decide to bail out, but doesn't cancel the underlying asynchronous operations.</span></span>  <span data-ttu-id="6ae44-222">Diğer bir seçenek de, iptal etme isteği nedeniyle erken bitebileceği için, işlem gerçekten tamamlanana kadar Kullanıcı arabirimini yeniden kurmamaya kadar bekleyen işlemleri iptal etmek olacaktır:</span><span class="sxs-lookup"><span data-stu-id="6ae44-222">Another alternative would be to cancel the pending operations when you decide to bail out, but not reestablish the user interface until the operations actually complete, potentially due to ending early due to the cancellation request:</span></span>

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

 <span data-ttu-id="6ae44-223">Erken bailout 'ın başka bir örneği, yönteminin <xref:System.Threading.Tasks.Task.WhenAny%2A> sonraki bölümde anlatıldığı gibi <xref:System.Threading.Tasks.Task.Delay%2A> yöntemiyle birlikte kullanılmasını içerir.</span><span class="sxs-lookup"><span data-stu-id="6ae44-223">Another example of early bailout involves using the <xref:System.Threading.Tasks.Task.WhenAny%2A> method in conjunction with the <xref:System.Threading.Tasks.Task.Delay%2A> method, as discussed in the next section.</span></span>

### <a name="taskdelay"></a><span data-ttu-id="6ae44-224">Task.Delay</span><span class="sxs-lookup"><span data-stu-id="6ae44-224">Task.Delay</span></span>
 <span data-ttu-id="6ae44-225">Bir zaman uyumsuz yöntemin <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> yürütülmesine duraklamalar tanıtmak için yöntemini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6ae44-225">You can use the <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> method to introduce pauses into an asynchronous method’s execution.</span></span>  <span data-ttu-id="6ae44-226">Bu, yoklama döngüleri oluşturma ve önceden belirlenmiş bir süre için Kullanıcı girişinin işlenmesini erteleme dahil olmak üzere çok sayıda işlevsellik için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="6ae44-226">This is useful for many kinds of functionality, including building polling loops and delaying the handling of user input for a predetermined period of time.</span></span>  <span data-ttu-id="6ae44-227">Yöntemi <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> , await üzerinde zaman aşımlarını uygulamak için <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> ile birlikte da yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="6ae44-227">The <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> method can also be useful in combination with <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> for implementing time-outs on awaits.</span></span>

 <span data-ttu-id="6ae44-228">Daha büyük bir zaman uyumsuz işlemin (örneğin, bir ASP.NET Web hizmeti) parçası olan bir görevin tamamlanabilmesi çok uzun sürerse, bu durum özellikle tamamlanamazsa, genel işlem zarar verebilir.</span><span class="sxs-lookup"><span data-stu-id="6ae44-228">If a task that’s part of a larger asynchronous operation (for example, an ASP.NET web service) takes too long to complete, the overall operation could suffer, especially if it fails to ever complete.</span></span>  <span data-ttu-id="6ae44-229">Bu nedenle, zaman uyumsuz bir işlem beklerken zaman aşımına uğrar.</span><span class="sxs-lookup"><span data-stu-id="6ae44-229">For this reason, it’s important to be able to time out when waiting on an asynchronous operation.</span></span>  <span data-ttu-id="6ae44-230">Zaman uyumlu <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Task.WaitAll%2A?displayProperty=nameWithType>ve <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> / <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType> / <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> yöntemleri zaman aşımı değerlerini kabul eder, ancak karşılık gelen ve daha önce bahsedilen <xref:System.Threading.Tasks.Task.WaitAny%2A?displayProperty=nameWithType> <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>Yöntemler değildir.</span><span class="sxs-lookup"><span data-stu-id="6ae44-230">The synchronous <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Task.WaitAll%2A?displayProperty=nameWithType>, and <xref:System.Threading.Tasks.Task.WaitAny%2A?displayProperty=nameWithType> methods accept time-out values, but the corresponding <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType>/<xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> and the previously mentioned <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>/<xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> methods do not.</span></span>  <span data-ttu-id="6ae44-231">Bunun yerine, zaman aşımı <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> uygulamak <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> için ve birleşimini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6ae44-231">Instead, you can use <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> in combination to implement a time-out.</span></span>

 <span data-ttu-id="6ae44-232">Örneğin, Kullanıcı arabirimi uygulamanızda bir görüntü indirmek ve görüntü indirilirken Kullanıcı arabirimini devre dışı bırakmak istediğinizi varsayalım.</span><span class="sxs-lookup"><span data-stu-id="6ae44-232">For example, in your UI application, let's say that you want to download an image and disable the UI while the image is downloading.</span></span> <span data-ttu-id="6ae44-233">Ancak indirme çok uzun sürerse, Kullanıcı arabirimini yeniden etkinleştirmek ve indirmeyi atmak istersiniz:</span><span class="sxs-lookup"><span data-stu-id="6ae44-233">However, if the download takes too long, you want to re-enable the UI and discard the download:</span></span>

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

 <span data-ttu-id="6ae44-234">Aynı durum birden çok indirme için geçerlidir, <xref:System.Threading.Tasks.Task.WhenAll%2A> çünkü bir görevi döndürür:</span><span class="sxs-lookup"><span data-stu-id="6ae44-234">The same applies to multiple downloads, because <xref:System.Threading.Tasks.Task.WhenAll%2A> returns a task:</span></span>

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

## <a name="building-task-based-combinators"></a><span data-ttu-id="6ae44-235">Görev tabanlı kombinatör oluşturma</span><span class="sxs-lookup"><span data-stu-id="6ae44-235">Building Task-based Combinators</span></span>
 <span data-ttu-id="6ae44-236">Bir görev, zaman uyumsuz bir işlemi tamamen temsil edebildiğinden ve işlemle birleştirmek için zaman uyumlu ve zaman uyumsuz yetenekler sağladığından, sonuçlarını almakla ve bu şekilde devam ediyorsa, görevleri oluşturan daha büyük desenler oluşturun.</span><span class="sxs-lookup"><span data-stu-id="6ae44-236">Because a task is able to completely represent an asynchronous operation and provide synchronous and asynchronous capabilities for joining with the operation, retrieving its results, and so on, you can build useful libraries of combinators that compose tasks to build larger patterns.</span></span>  <span data-ttu-id="6ae44-237">Önceki bölümde anlatıldığı gibi .NET Framework çeşitli yerleşik kombinatör içerir, ancak kendi kodunuzu da oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6ae44-237">As discussed in the previous section, the .NET Framework includes several built-in combinators, but you can also build your own.</span></span> <span data-ttu-id="6ae44-238">Aşağıdaki bölümlerde olası Combinator yöntemlerine ve türlerine birkaç örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="6ae44-238">The following sections provide several examples of potential combinator methods and types.</span></span>

### <a name="retryonfault"></a><span data-ttu-id="6ae44-239">RetryOnFault</span><span class="sxs-lookup"><span data-stu-id="6ae44-239">RetryOnFault</span></span>
 <span data-ttu-id="6ae44-240">Birçok durumda, önceki bir deneme başarısız olursa bir işlemi yeniden denemek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6ae44-240">In many situations, you may want to retry an operation if a previous attempt fails.</span></span>  <span data-ttu-id="6ae44-241">Zaman uyumlu kod için, bunu gerçekleştirmek için aşağıdaki örnekte gibi `RetryOnFault` bir yardımcı yöntem oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="6ae44-241">For synchronous code, you might build a helper method such as `RetryOnFault` in the following example to accomplish this:</span></span>

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

 <span data-ttu-id="6ae44-242">DOKUNARAK uygulanan ve bu nedenle görevleri döndüren zaman uyumsuz işlemler için neredeyse özdeş bir yardımcı yöntem oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="6ae44-242">You can build an almost identical helper method for asynchronous operations that are implemented with TAP and thus return tasks:</span></span>

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

 <span data-ttu-id="6ae44-243">Daha sonra bu Combinator kullanarak yeniden denemeleri uygulamanın mantığına dönüştürebilirsiniz; Örneğin:</span><span class="sxs-lookup"><span data-stu-id="6ae44-243">You can then use this combinator to encode retries into the application’s logic; for example:</span></span>

```csharp
// Download the URL, trying up to three times in case of failure
string pageContents = await RetryOnFault(
    () => DownloadStringAsync(url), 3);
```

 <span data-ttu-id="6ae44-244">`RetryOnFault` İşlevi daha fazla genişletebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6ae44-244">You could extend the `RetryOnFault` function further.</span></span> <span data-ttu-id="6ae44-245">Örneğin, işlev işlemin ne zaman denenmesini `Func<Task>` anlamak için yeniden denemeler arasında çağrılacak bir tane kabul edebilir. Örneğin:</span><span class="sxs-lookup"><span data-stu-id="6ae44-245">For example, the function could accept another `Func<Task>` that will be invoked between retries to determine when to try the operation again; for example:</span></span>

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

 <span data-ttu-id="6ae44-246">Ardından, işlemi yeniden denemeden önce bir saniye beklemek için işlevini aşağıdaki şekilde kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="6ae44-246">You could then use the function as follows to wait for a second before retrying the operation:</span></span>

```csharp
// Download the URL, trying up to three times in case of failure,
// and delaying for a second between retries
string pageContents = await RetryOnFault(
    () => DownloadStringAsync(url), 3, () => Task.Delay(1000));
```

### <a name="needonlyone"></a><span data-ttu-id="6ae44-247">Gereksiz bir</span><span class="sxs-lookup"><span data-stu-id="6ae44-247">NeedOnlyOne</span></span>
 <span data-ttu-id="6ae44-248">Bazen bir işlemin gecikme süresini ve başarılı olma olasılığını artırmak için yedekliliğe sahip olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6ae44-248">Sometimes, you can take advantage of redundancy to improve an operation’s latency and chances for success.</span></span>  <span data-ttu-id="6ae44-249">Hisse senedi fiyatları sağlayan birden çok Web hizmeti düşünün, ancak günün çeşitli saatlerinde her hizmet farklı düzeylerde kalite ve yanıt süreleri sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="6ae44-249">Consider multiple web services that provide stock quotes, but at various times of the day, each service may provide different levels of quality and response times.</span></span>  <span data-ttu-id="6ae44-250">Bu dalgalanmalara ulaşmak için tüm Web hizmetlerine istek verebilir ve birinden yanıt aldığınızda, kalan istekleri iptal edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6ae44-250">To deal with these fluctuations, you may issue requests to all the web services, and as soon as you get a response from one, cancel the remaining requests.</span></span>  <span data-ttu-id="6ae44-251">Birden çok işlem başlatmanın bu ortak deseninin uygulanmasını kolaylaştırmak için bir yardımcı işlevi uygulayabilir, herhangi bir bekliyor ve geri kalanını iptal edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6ae44-251">You can implement a helper function to make it easier to implement this common pattern of launching multiple operations, waiting for any, and then canceling the rest.</span></span> <span data-ttu-id="6ae44-252">Aşağıdaki `NeedOnlyOne` örnekteki işlev bu senaryoyu göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="6ae44-252">The `NeedOnlyOne` function in the following example illustrates this scenario:</span></span>

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

 <span data-ttu-id="6ae44-253">Daha sonra bu işlevi aşağıdaki şekilde kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="6ae44-253">You can then use this function as follows:</span></span>

```csharp
double currentPrice = await NeedOnlyOne(
    ct => GetCurrentPriceFromServer1Async("msft", ct),
    ct => GetCurrentPriceFromServer2Async("msft", ct),
    ct => GetCurrentPriceFromServer3Async("msft", ct));
```

### <a name="interleaved-operations"></a><span data-ttu-id="6ae44-254">Araya eklemeli Işlemler</span><span class="sxs-lookup"><span data-stu-id="6ae44-254">Interleaved Operations</span></span>
 <span data-ttu-id="6ae44-255">Çok büyük görev kümeleriyle çalışırken bir araya ekleme senaryosunu <xref:System.Threading.Tasks.Task.WhenAny%2A> desteklemek için yöntemini kullanmayla ilgili olası bir performans sorunu vardır.</span><span class="sxs-lookup"><span data-stu-id="6ae44-255">There is a potential performance problem with using the <xref:System.Threading.Tasks.Task.WhenAny%2A> method to support an interleaving scenario when you're working with very large sets of tasks.</span></span>  <span data-ttu-id="6ae44-256">Her bir görevde <xref:System.Threading.Tasks.Task.WhenAny%2A> bir devamlılığın sonucunu elde etmek için her çağrı.</span><span class="sxs-lookup"><span data-stu-id="6ae44-256">Every call to <xref:System.Threading.Tasks.Task.WhenAny%2A> results in a continuation being registered with each task.</span></span> <span data-ttu-id="6ae44-257">N sayıda görev için, bu, araya ekleme işleminin ömrü boyunca oluşturulan O (N2) devamlılıkları ile sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="6ae44-257">For N number of tasks, this results in O(N2) continuations created over the lifetime of the interleaving operation.</span></span>  <span data-ttu-id="6ae44-258">Büyük bir görev kümesiyle çalışıyorsanız, performans sorununu gidermek için bir Combinator (`Interleaved` aşağıdaki örnekte) kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="6ae44-258">If you're working with a large set of tasks, you can use a combinator  (`Interleaved` in the following example) to address the performance issue:</span></span>

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

 <span data-ttu-id="6ae44-259">Daha sonra, görevlerin sonuçlarını tamamlarsa işlemek için Combinator kullanabilirsiniz; Örneğin:</span><span class="sxs-lookup"><span data-stu-id="6ae44-259">You can then use the combinator to process the results of tasks as they complete; for example:</span></span>

```csharp
IEnumerable<Task<int>> tasks = ...;
foreach(var task in Interleaved(tasks))
{
    int result = await task;
    …
}
```

### <a name="whenallorfirstexception"></a><span data-ttu-id="6ae44-260">WhenAllOrFirstException</span><span class="sxs-lookup"><span data-stu-id="6ae44-260">WhenAllOrFirstException</span></span>
 <span data-ttu-id="6ae44-261">Belirli dağılım/toplama senaryolarında, bir küme içindeki tüm görevleri beklemek isteyebilirsiniz, bu durumda, özel durum meydana geldiğinde beklemeyi durdurmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6ae44-261">In certain scatter/gather scenarios, you might want to wait for all tasks in a set, unless one of them faults, in which case you want to stop waiting as soon as the exception occurs.</span></span>  <span data-ttu-id="6ae44-262">Bunu, aşağıdaki örnekte olduğu `WhenAllOrFirstException` gibi bir Combinator yöntemi ile gerçekleştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="6ae44-262">You can accomplish that with a combinator method such as `WhenAllOrFirstException` in the following example:</span></span>

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

## <a name="building-task-based-data-structures"></a><span data-ttu-id="6ae44-263">Görev tabanlı veri yapıları oluşturma</span><span class="sxs-lookup"><span data-stu-id="6ae44-263">Building Task-based Data Structures</span></span>
 <span data-ttu-id="6ae44-264">Özel görev tabanlı kombinatör oluşturma özelliğine ek olarak, ' de <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601> bir veri yapısına sahip olmak ve hem zaman uyumsuz bir işlemin sonuçlarını hem de bununla birleştirmek için gereken eşitlemeyi temsil eden bir çok güçlü hale getirir zaman uyumsuz senaryolarda kullanılacak özel veri yapılarını oluşturmak için yazın.</span><span class="sxs-lookup"><span data-stu-id="6ae44-264">In addition to the ability to build custom task-based combinators, having a data structure in <xref:System.Threading.Tasks.Task> and <xref:System.Threading.Tasks.Task%601> that represents both the results of an asynchronous operation and the necessary synchronization to join with it makes it a very powerful type on which to build custom data structures to be used in asynchronous scenarios.</span></span>

### <a name="asynccache"></a><span data-ttu-id="6ae44-265">AsyncCache</span><span class="sxs-lookup"><span data-stu-id="6ae44-265">AsyncCache</span></span>
 <span data-ttu-id="6ae44-266">Bir görevin önemli bir yönü, birden fazla tüketiciye, hepsi tarafından bekleme, devamlılık veya özel durumları (söz konusu olduğunda <xref:System.Threading.Tasks.Task%601>) elde ettirebilir.</span><span class="sxs-lookup"><span data-stu-id="6ae44-266">One important aspect of a task is that it may be handed out to multiple consumers, all of whom may await it, register continuations with it, get its result or exceptions (in the case of <xref:System.Threading.Tasks.Task%601>), and so on.</span></span>  <span data-ttu-id="6ae44-267">Bu, <xref:System.Threading.Tasks.Task> zaman <xref:System.Threading.Tasks.Task%601> uyumsuz bir önbelleğe alma altyapısında kullanılmasını sağlar ve idealdir.</span><span class="sxs-lookup"><span data-stu-id="6ae44-267">This makes <xref:System.Threading.Tasks.Task> and <xref:System.Threading.Tasks.Task%601> perfectly suited to be used in an asynchronous caching infrastructure.</span></span>  <span data-ttu-id="6ae44-268">Aşağıda, <xref:System.Threading.Tasks.Task%601>üzerine inşa eden küçük ancak güçlü bir zaman uyumsuz önbellek örneği verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="6ae44-268">Here’s an example of a small but powerful asynchronous cache built on top of <xref:System.Threading.Tasks.Task%601>:</span></span>

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

 <span data-ttu-id="6ae44-269">[AsyncCache\<TKey, TValue >](https://blogs.msdn.microsoft.com/pfxteam/2010/04/23/parallelextensionsextras-tour-12-asynccache/) sınıfı, oluşturucusu `TKey` için bir temsilci olarak kabul eder ve döndürür <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="6ae44-269">The [AsyncCache\<TKey,TValue>](https://blogs.msdn.microsoft.com/pfxteam/2010/04/23/parallelextensionsextras-tour-12-asynccache/) class accepts as a delegate to its constructor a function that takes a `TKey` and returns a <xref:System.Threading.Tasks.Task%601>.</span></span>  <span data-ttu-id="6ae44-270">Ön belleğe daha önce erişilen tüm değerler iç sözlükte depolanır ve önbelleğe eşzamanlı olarak erişilse `AsyncCache` bile, her anahtar için yalnızca bir görevin oluşturulmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="6ae44-270">Any previously accessed values from the cache are stored in the internal dictionary, and the `AsyncCache` ensures that only one task is generated per key, even if the cache is accessed concurrently.</span></span>

 <span data-ttu-id="6ae44-271">Örneğin, indirilen Web sayfaları için bir önbellek oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="6ae44-271">For example, you can build a cache for downloaded web pages:</span></span>

```csharp
private AsyncCache<string,string> m_webPages =
    new AsyncCache<string,string>(DownloadStringAsync);
```

 <span data-ttu-id="6ae44-272">Böylece, bir Web sayfasının içeriğine ihtiyacınız olduğunda bu önbelleği zaman uyumsuz metotlarda kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6ae44-272">You can then use this cache in asynchronous methods whenever you need the contents of a web page.</span></span> <span data-ttu-id="6ae44-273">`AsyncCache` Sınıfı mümkün olduğunca az sayfa indirmenizi ve sonuçları önbelleğe almanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="6ae44-273">The `AsyncCache` class ensures that you’re downloading as few pages as possible, and caches the results.</span></span>

```csharp
private async void btnDownload_Click(object sender, RoutedEventArgs e)
{
    btnDownload.IsEnabled = false;
    try
    {
        txtContents.Text = await m_webPages["https://www.microsoft.com"];
    }
    finally { btnDownload.IsEnabled = true; }
}
```

### <a name="asyncproducerconsumercollection"></a><span data-ttu-id="6ae44-274">AsyncProducerConsumerCollection</span><span class="sxs-lookup"><span data-stu-id="6ae44-274">AsyncProducerConsumerCollection</span></span>
 <span data-ttu-id="6ae44-275">Ayrıca, zaman uyumsuz etkinlikleri koordine etmek üzere veri yapıları oluşturmak için görevleri de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6ae44-275">You can also use tasks to build data structures for coordinating asynchronous activities.</span></span>  <span data-ttu-id="6ae44-276">Klasik paralel tasarım desenlerinden birini göz önünde bulundurun: Producer/Consumer.</span><span class="sxs-lookup"><span data-stu-id="6ae44-276">Consider one of the classic parallel design patterns: producer/consumer.</span></span>  <span data-ttu-id="6ae44-277">Bu düzende, üreticileri tüketiciler tarafından tüketilen verileri oluşturur ve üreticileri ve tüketiciler paralel olarak çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="6ae44-277">In this pattern, producers generate data that is consumed by consumers, and the producers and consumers may run in parallel.</span></span> <span data-ttu-id="6ae44-278">Örneğin, tüketici daha önce öğe 2 ' yi üreten bir üretici tarafından oluşturulan öğe 1 ' i işler.</span><span class="sxs-lookup"><span data-stu-id="6ae44-278">For example, the consumer processes item 1, which was previously generated by a producer who is now producing item 2.</span></span>  <span data-ttu-id="6ae44-279">Üretici/tüketici düzeninde, müşteriler yeni veriler hakkında bildirim almak ve kullanılabilir olduğunda bulmak için üreticileri tarafından oluşturulan işi depolamak üzere bazı veri yapısına ihtiyacınız vardır.</span><span class="sxs-lookup"><span data-stu-id="6ae44-279">For the producer/consumer pattern, you invariably need some data structure to store the work created by producers so that the consumers may be notified of new data and find it when available.</span></span>

 <span data-ttu-id="6ae44-280">Aşağıda, zaman uyumsuz yöntemlerin üreticileri ve tüketiciler olarak kullanılmasını sağlayan görevlerin üzerine oluşturulmuş basit bir veri yapısı verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="6ae44-280">Here’s a simple data structure built on top of tasks that enables asynchronous methods to be used as producers and consumers:</span></span>

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

 <span data-ttu-id="6ae44-281">Bu veri yapısıyla birlikte, aşağıdaki gibi bir kod yazabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="6ae44-281">With that data structure in place, you can write code such as the following:</span></span>

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

<span data-ttu-id="6ae44-282">Ad alanı, benzer <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> bir şekilde kullanabileceğiniz, ancak özel bir koleksiyon türü oluşturmak zorunda kalmadan türü içerir: <xref:System.Threading.Tasks.Dataflow></span><span class="sxs-lookup"><span data-stu-id="6ae44-282">The <xref:System.Threading.Tasks.Dataflow> namespace includes the <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> type, which you can use in a similar manner, but without having to build a custom collection type:</span></span>

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
> <span data-ttu-id="6ae44-283">Ad alanı, NuGet aracılığıyla .NET Framework 4,5 ' de kullanılabilir. <xref:System.Threading.Tasks.Dataflow></span><span class="sxs-lookup"><span data-stu-id="6ae44-283">The <xref:System.Threading.Tasks.Dataflow> namespace is available in the .NET Framework 4.5 through **NuGet**.</span></span> <span data-ttu-id="6ae44-284"><xref:System.Threading.Tasks.Dataflow> Ad alanını içeren derlemeyi yüklemek için projenizi Visual Studio 'da açın, proje menüsünden **NuGet Paketlerini Yönet** ' i seçin ve Microsoft. tpl. Dataflow paketini çevrimiçi olarak arayın.</span><span class="sxs-lookup"><span data-stu-id="6ae44-284">To install the assembly that contains the <xref:System.Threading.Tasks.Dataflow> namespace, open your project in Visual Studio, choose **Manage NuGet Packages** from the Project menu, and search online for the Microsoft.Tpl.Dataflow package.</span></span>

## <a name="see-also"></a><span data-ttu-id="6ae44-285">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6ae44-285">See also</span></span>

- [<span data-ttu-id="6ae44-286">Görev Tabanlı Zaman Uyumsuz Desen (TAP)</span><span class="sxs-lookup"><span data-stu-id="6ae44-286">Task-based Asynchronous Pattern (TAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)
- [<span data-ttu-id="6ae44-287">Görev Tabanlı Zaman Uyumsuz Deseni Uygulama</span><span class="sxs-lookup"><span data-stu-id="6ae44-287">Implementing the Task-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/implementing-the-task-based-asynchronous-pattern.md)
- [<span data-ttu-id="6ae44-288">Diğer Zaman Uyumsuz Desen ve Türlerle Birlikte Çalışma</span><span class="sxs-lookup"><span data-stu-id="6ae44-288">Interop with Other Asynchronous Patterns and Types</span></span>](../../../docs/standard/asynchronous-programming-patterns/interop-with-other-asynchronous-patterns-and-types.md)
