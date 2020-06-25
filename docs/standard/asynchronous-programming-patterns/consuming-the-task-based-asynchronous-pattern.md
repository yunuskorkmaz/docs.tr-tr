---
title: Görev Tabanlı Zaman Uyumsuz Desen Kullanma
description: Zaman uyumsuz işlemlerle çalışırken görev tabanlı zaman uyumsuz model (dokunarak) kullanmayı öğrenin.
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- .NET Framework, and TAP
- asynchronous design patterns, .NET Framework
- TAP, .NET Framework support for
- Task-based Asynchronous Pattern, .NET Framework support for
- .NET Framework, asynchronous design patterns
ms.assetid: 033cf871-ae24-433d-8939-7a3793e547bf
ms.openlocfilehash: f1a5070c106055b268d43751300d84269fed6a36
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85326006"
---
# <a name="consuming-the-task-based-asynchronous-pattern"></a><span data-ttu-id="60c53-103">Görev Tabanlı Zaman Uyumsuz Desen Kullanma</span><span class="sxs-lookup"><span data-stu-id="60c53-103">Consuming the Task-based Asynchronous Pattern</span></span>

<span data-ttu-id="60c53-104">Zaman uyumsuz işlemlerle çalışmak için görev tabanlı zaman uyumsuz model (TAP) kullandığınızda geri çağırmaları kullanarak, engellemeden beklemeyi elde edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="60c53-104">When you use the Task-based Asynchronous Pattern (TAP) to work with asynchronous operations, you can use callbacks to achieve waiting without blocking.</span></span>  <span data-ttu-id="60c53-105">Görevler için, bu gibi yöntemler aracılığıyla elde edilir <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="60c53-105">For tasks, this is achieved through methods such as <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="60c53-106">Dil tabanlı zaman uyumsuz destek, zaman uyumsuz işlemlerin normal Denetim akışında beklemesine izin vererek geri çağırmaları gizler ve derleyicinin ürettiği kod aynı API düzeyi desteğini sağlar.</span><span class="sxs-lookup"><span data-stu-id="60c53-106">Language-based asynchronous support hides callbacks by allowing asynchronous operations to be awaited within normal control flow, and compiler-generated code provides this same API-level support.</span></span>

## <a name="suspending-execution-with-await"></a><span data-ttu-id="60c53-107">Await ile yürütmeyi askıya alma</span><span class="sxs-lookup"><span data-stu-id="60c53-107">Suspending Execution with Await</span></span>
 <span data-ttu-id="60c53-108">.NET Framework 4,5 ' den başlayarak, zaman uyumsuz olarak await ve nesneler için C# ' de [await](../../csharp/language-reference/operators/await.md) anahtar sözcüğünü ve Visual Basic [await işlecini](../../visual-basic/language-reference/operators/await-operator.md) kullanabilirsiniz <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601> .</span><span class="sxs-lookup"><span data-stu-id="60c53-108">Starting with the .NET Framework 4.5, you can use the [await](../../csharp/language-reference/operators/await.md) keyword in C# and the [Await Operator](../../visual-basic/language-reference/operators/await-operator.md) in Visual Basic to asynchronously await <xref:System.Threading.Tasks.Task> and <xref:System.Threading.Tasks.Task%601> objects.</span></span> <span data-ttu-id="60c53-109">Bir <xref:System.Threading.Tasks.Task> ' ı beklerken, `await` ifade türündedir `void` .</span><span class="sxs-lookup"><span data-stu-id="60c53-109">When you're awaiting a <xref:System.Threading.Tasks.Task>, the `await` expression is of type `void`.</span></span> <span data-ttu-id="60c53-110">Bir <xref:System.Threading.Tasks.Task%601> ' ı beklerken, `await` ifade türündedir `TResult` .</span><span class="sxs-lookup"><span data-stu-id="60c53-110">When you're awaiting a <xref:System.Threading.Tasks.Task%601>, the `await` expression is of type `TResult`.</span></span> <span data-ttu-id="60c53-111">Bir `await` ifade, zaman uyumsuz bir metodun gövdesinde gerçekleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="60c53-111">An `await` expression must occur inside the body of an asynchronous method.</span></span> <span data-ttu-id="60c53-112">.NET Framework 4,5 ' de C# ve Visual Basic dil desteği hakkında daha fazla bilgi için bkz. C# ve Visual Basic dil belirtimleri.</span><span class="sxs-lookup"><span data-stu-id="60c53-112">For more information about C# and Visual Basic language support in the .NET Framework 4.5, see the C# and Visual Basic language specifications.</span></span>

 <span data-ttu-id="60c53-113">Kapakların altında, await işlevi bir devamlılık kullanarak göreve bir geri çağırma işlemini kurar.</span><span class="sxs-lookup"><span data-stu-id="60c53-113">Under the covers, the await functionality installs a callback on the task by using a continuation.</span></span>  <span data-ttu-id="60c53-114">Bu geri çağırma, askıya alma noktasındaki zaman uyumsuz yöntemi sürdürür.</span><span class="sxs-lookup"><span data-stu-id="60c53-114">This callback resumes the asynchronous method at the point of suspension.</span></span> <span data-ttu-id="60c53-115">Zaman uyumsuz yöntem devam ettirildiğinde, abeklelen işlem başarıyla tamamlanırsa ve bir ise <xref:System.Threading.Tasks.Task%601> , `TResult` döndürülür.</span><span class="sxs-lookup"><span data-stu-id="60c53-115">When the asynchronous method is resumed, if the awaited operation completed successfully and was a <xref:System.Threading.Tasks.Task%601>, its `TResult` is returned.</span></span>  <span data-ttu-id="60c53-116">Durum, <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601> durumunda sonlandıysa <xref:System.Threading.Tasks.TaskStatus.Canceled> , bir <xref:System.OperationCanceledException> özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="60c53-116">If the <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> that was awaited ended in the <xref:System.Threading.Tasks.TaskStatus.Canceled> state, an <xref:System.OperationCanceledException> exception is thrown.</span></span>  <span data-ttu-id="60c53-117">Durum, <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601> durumunda sonlandıysa <xref:System.Threading.Tasks.TaskStatus.Faulted> , hataya neden olan özel durum atılır.</span><span class="sxs-lookup"><span data-stu-id="60c53-117">If the <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> that was awaited ended in the <xref:System.Threading.Tasks.TaskStatus.Faulted> state, the exception that caused it to fault is thrown.</span></span> <span data-ttu-id="60c53-118">Bir `Task` , birden çok özel durumun sonucu olarak hata verebilir, ancak bu özel durumların yalnızca biri yayılır.</span><span class="sxs-lookup"><span data-stu-id="60c53-118">A `Task` can fault as a result of multiple exceptions, but only one of these exceptions is propagated.</span></span> <span data-ttu-id="60c53-119">Ancak, <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> özelliği <xref:System.AggregateException> tüm hataları içeren bir özel durum döndürür.</span><span class="sxs-lookup"><span data-stu-id="60c53-119">However, the <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> property returns an <xref:System.AggregateException> exception that contains all the errors.</span></span>

 <span data-ttu-id="60c53-120">Bir eşitleme bağlamı ( <xref:System.Threading.SynchronizationContext> nesne) askıya alma sırasında zaman uyumsuz yöntemi yürüten iş parçacığıyla ilişkiliyse (örneğin, <xref:System.Threading.SynchronizationContext.Current%2A?displayProperty=nameWithType> özellik değilse `null` ), zaman uyumsuz yöntem, bağlam yöntemi kullanılarak aynı eşitleme bağlamında devam eder <xref:System.Threading.SynchronizationContext.Post%2A> .</span><span class="sxs-lookup"><span data-stu-id="60c53-120">If a synchronization context (<xref:System.Threading.SynchronizationContext> object) is associated with the thread that was executing the asynchronous method at the time of suspension (for example, if the <xref:System.Threading.SynchronizationContext.Current%2A?displayProperty=nameWithType> property is not `null`), the asynchronous method resumes on that same synchronization context by using the context's <xref:System.Threading.SynchronizationContext.Post%2A> method.</span></span> <span data-ttu-id="60c53-121">Aksi takdirde, <xref:System.Threading.Tasks.TaskScheduler> askıya alma sırasında geçerli olan görev zamanlayıcısını (nesne) kullanır.</span><span class="sxs-lookup"><span data-stu-id="60c53-121">Otherwise, it relies on the task scheduler (<xref:System.Threading.Tasks.TaskScheduler> object) that was current at the time of suspension.</span></span> <span data-ttu-id="60c53-122">Genellikle, bu, <xref:System.Threading.Tasks.TaskScheduler.Default%2A?displayProperty=nameWithType> iş parçacığı havuzunu hedefleyen varsayılan Görev Zamanlayıcı () ' dır.</span><span class="sxs-lookup"><span data-stu-id="60c53-122">Typically, this is the default task scheduler (<xref:System.Threading.Tasks.TaskScheduler.Default%2A?displayProperty=nameWithType>), which targets the thread pool.</span></span> <span data-ttu-id="60c53-123">Bu görev zamanlayıcı, beklenen zaman uyumsuz işlemin tamamlandığında veya sürdürme zamanlanıp zamanlanmayacağını belirler.</span><span class="sxs-lookup"><span data-stu-id="60c53-123">This task scheduler determines whether the awaited asynchronous operation should resume where it completed or whether the resumption should be scheduled.</span></span> <span data-ttu-id="60c53-124">Varsayılan Zamanlayıcı genellikle devamlılığın tamamlanan işlemin tamamlandığı iş parçacığında çalışmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="60c53-124">The default scheduler typically allows the continuation to run on the thread that the awaited operation completed.</span></span>

 <span data-ttu-id="60c53-125">Zaman uyumsuz bir yöntem çağrıldığında, henüz tamamlanmamış olan bir awasever örneğine ilk await ifadesi kadar zaman uyumlu olarak çalışır; bu noktada çağrı çağırana döner.</span><span class="sxs-lookup"><span data-stu-id="60c53-125">When an asynchronous method is called, it synchronously executes the body of the function up until the first await expression on an awaitable instance that has not yet completed, at which point the invocation returns to the caller.</span></span> <span data-ttu-id="60c53-126">Zaman uyumsuz yöntem döndürmezse `void` , <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601> devam eden hesaplamayı temsil eden bir veya nesnesi döndürülür.</span><span class="sxs-lookup"><span data-stu-id="60c53-126">If the asynchronous method does not return `void`, a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> object is returned to represent the ongoing computation.</span></span> <span data-ttu-id="60c53-127">Void olmayan bir zaman uyumsuz yöntemde, bir return ifadesine karşılaşılırsa veya Yöntem gövdesinin sonuna ulaşılırsa, görev <xref:System.Threading.Tasks.TaskStatus.RanToCompletion> son durumda tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="60c53-127">In a non-void asynchronous method, if a return statement is encountered or the end of the method body is reached, the task is completed in the <xref:System.Threading.Tasks.TaskStatus.RanToCompletion> final state.</span></span> <span data-ttu-id="60c53-128">İşlenmeyen bir özel durum denetimin zaman uyumsuz yöntemin gövdesinden ayrılmasına neden olursa, görev <xref:System.Threading.Tasks.TaskStatus.Faulted> durumunda sonlanır.</span><span class="sxs-lookup"><span data-stu-id="60c53-128">If an unhandled exception causes control to leave the body of the asynchronous method, the task ends in the <xref:System.Threading.Tasks.TaskStatus.Faulted> state.</span></span> <span data-ttu-id="60c53-129">Bu özel durum bir ise <xref:System.OperationCanceledException> , görev durumunda sona erer <xref:System.Threading.Tasks.TaskStatus.Canceled> .</span><span class="sxs-lookup"><span data-stu-id="60c53-129">If that exception is an <xref:System.OperationCanceledException>, the task instead ends in the <xref:System.Threading.Tasks.TaskStatus.Canceled> state.</span></span> <span data-ttu-id="60c53-130">Bu şekilde, sonuç veya özel durum sonunda yayımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="60c53-130">In this manner, the result or exception is eventually published.</span></span>

 <span data-ttu-id="60c53-131">Bu davranışın çeşitli önemli çeşitlemeleri vardır.</span><span class="sxs-lookup"><span data-stu-id="60c53-131">There are several important variations of this behavior.</span></span>  <span data-ttu-id="60c53-132">Performans nedenleriyle, görev beklenerek görevin zaten tamamlanmışsa, denetim bir şekilde uygulanmaz ve işlev yürütülmeye devam eder.</span><span class="sxs-lookup"><span data-stu-id="60c53-132">For performance reasons, if a task has already completed by the time the task is awaited, control is not yielded, and the function continues to execute.</span></span>  <span data-ttu-id="60c53-133">Ayrıca, özgün bağlamına dönmek her zaman istenen davranış değildir ve değiştirilebilir; Bu, sonraki bölümde daha ayrıntılı olarak açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="60c53-133">Additionally, returning to the original context isn't always the desired behavior and can be changed; this is described in more detail in the next section.</span></span>

### <a name="configuring-suspension-and-resumption-with-yield-and-configureawait"></a><span data-ttu-id="60c53-134">Yield ve ConfigureAwait ile askıya alma ve sürdürme yapılandırma</span><span class="sxs-lookup"><span data-stu-id="60c53-134">Configuring Suspension and Resumption with Yield and ConfigureAwait</span></span>
 <span data-ttu-id="60c53-135">Çeşitli yöntemler zaman uyumsuz yöntemin yürütülmesi üzerinde daha fazla denetim sağlar.</span><span class="sxs-lookup"><span data-stu-id="60c53-135">Several methods provide more control over an asynchronous method's execution.</span></span> <span data-ttu-id="60c53-136">Örneğin, <xref:System.Threading.Tasks.Task.Yield%2A?displayProperty=nameWithType> zaman uyumsuz metoda bir yield noktası tanıtmak için yöntemini kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="60c53-136">For example, you can use the <xref:System.Threading.Tasks.Task.Yield%2A?displayProperty=nameWithType> method to introduce a yield point into the asynchronous method:</span></span>

```csharp
public class Task : …
{
    public static YieldAwaitable Yield();
    …
}
```

 <span data-ttu-id="60c53-137">Bu, zaman uyumsuz naklin veya geçerli bağlamına yeniden zamanlama ile eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="60c53-137">This is equivalent to asynchronously posting or scheduling back to the current context.</span></span>

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

 <span data-ttu-id="60c53-138">Ayrıca, <xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=nameWithType> zaman uyumsuz bir yöntemde askıya alma ve sürdürme üzerinde daha iyi denetim için yöntemini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="60c53-138">You can also use the <xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=nameWithType> method for better control over suspension and resumption in an asynchronous method.</span></span>  <span data-ttu-id="60c53-139">Daha önce belirtildiği gibi, varsayılan olarak, geçerli bağlam zaman uyumsuz bir yöntem askıya alındığında yakalanır ve sürdürme üzerinde zaman uyumsuz yöntemin devamlılığını çağırmak için yakalanan bağlam kullanılır.</span><span class="sxs-lookup"><span data-stu-id="60c53-139">As mentioned previously, by default, the current context is captured at the time an asynchronous  method is suspended, and that captured context is used to invoke the asynchronous  method's continuation upon resumption.</span></span>  <span data-ttu-id="60c53-140">Çoğu durumda bu, istediğiniz tam davranışdır.</span><span class="sxs-lookup"><span data-stu-id="60c53-140">In many cases, this is the exact behavior you want.</span></span>  <span data-ttu-id="60c53-141">Diğer durumlarda, devamlılık bağlamıyla ilgilenmeyebilirsiniz ve bu gibi gönderilerin özgün bağlamına geri giderek daha iyi performans elde edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="60c53-141">In other cases, you may not care about the continuation context, and you can achieve better performance by avoiding such posts back to the original context.</span></span>  <span data-ttu-id="60c53-142">Bunu etkinleştirmek için, <xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=nameWithType> await işleminin bağlam üzerinde yakalanıp sürdürülmeyeceğini bilgilendirmek için yöntemini kullanın, ancak beklenen zaman uyumsuz işlemin tamamlandığı her yerde yürütmeye devam etmek için:</span><span class="sxs-lookup"><span data-stu-id="60c53-142">To enable this, use the <xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=nameWithType> method to inform the await operation not to capture and resume on the context, but to continue execution wherever the asynchronous operation that was being awaited completed:</span></span>

```csharp
await someTask.ConfigureAwait(continueOnCapturedContext:false);
```

## <a name="canceling-an-asynchronous-operation"></a><span data-ttu-id="60c53-143">Zaman uyumsuz bir Işlem iptal ediliyor</span><span class="sxs-lookup"><span data-stu-id="60c53-143">Canceling an Asynchronous Operation</span></span>
 <span data-ttu-id="60c53-144">.NET Framework 4 ' ten başlayarak, iptali destekleyen yöntemler ' e dokunarak iptal belirtecini kabul eden en az bir aşırı yükleme sağlayın ( <xref:System.Threading.CancellationToken> nesne).</span><span class="sxs-lookup"><span data-stu-id="60c53-144">Starting with the .NET Framework 4, TAP methods that support cancellation provide at least one overload that accepts a cancellation token (<xref:System.Threading.CancellationToken> object).</span></span>

 <span data-ttu-id="60c53-145">İptal belirteci bir iptal belirteci kaynağı (nesne) ile oluşturulur <xref:System.Threading.CancellationTokenSource> .</span><span class="sxs-lookup"><span data-stu-id="60c53-145">A cancellation token is created through a cancellation token source (<xref:System.Threading.CancellationTokenSource> object).</span></span>  <span data-ttu-id="60c53-146">Kaynağın özelliği, <xref:System.Threading.CancellationTokenSource.Token%2A> kaynağın yöntemi çağrıldığında işaret edilecek iptal belirtecini döndürür <xref:System.Threading.CancellationTokenSource.Cancel%2A> .</span><span class="sxs-lookup"><span data-stu-id="60c53-146">The source's <xref:System.Threading.CancellationTokenSource.Token%2A> property returns the cancellation token that will be signaled when the source's <xref:System.Threading.CancellationTokenSource.Cancel%2A> method is called.</span></span>  <span data-ttu-id="60c53-147">Örneğin, tek bir Web sayfasını indirmek isterseniz ve işlemi iptal etmek istiyorsanız, bir <xref:System.Threading.CancellationTokenSource> nesnesi oluşturur, BELIRTECINI tap yöntemine geçitirsiniz ve ardından <xref:System.Threading.CancellationTokenSource.Cancel%2A> işlemi iptal etmeye hazırsanız kaynağın metodunu çağırın:</span><span class="sxs-lookup"><span data-stu-id="60c53-147">For example, if you want to download a single webpage and you want to be able to cancel the operation, you create a <xref:System.Threading.CancellationTokenSource> object, pass its token to the TAP method, and then call the source's <xref:System.Threading.CancellationTokenSource.Cancel%2A> method when you're ready to cancel the operation:</span></span>

```csharp
var cts = new CancellationTokenSource();
string result = await DownloadStringAsync(url, cts.Token);
… // at some point later, potentially on another thread
cts.Cancel();
```

 <span data-ttu-id="60c53-148">Birden çok zaman uyumsuz çağırma işlemini iptal etmek için, tüm etkinleştirmeleri için aynı belirteci geçirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="60c53-148">To cancel multiple asynchronous invocations, you can pass the same token to all invocations:</span></span>

```csharp
var cts = new CancellationTokenSource();
    IList<string> results = await Task.WhenAll(from url in urls select DownloadStringAsync(url, cts.Token));
    // at some point later, potentially on another thread
    …
    cts.Cancel();
```

 <span data-ttu-id="60c53-149">Ya da aynı belirteci bir işlem seçmeli alt kümesine geçirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="60c53-149">Or, you can pass the same token to a selective subset of operations:</span></span>

```csharp
var cts = new CancellationTokenSource();
    byte [] data = await DownloadDataAsync(url, cts.Token);
    await SaveToDiskAsync(outputPath, data, CancellationToken.None);
    … // at some point later, potentially on another thread
    cts.Cancel();
```

 <span data-ttu-id="60c53-150">İptal istekleri herhangi bir iş parçacığından başlatılabilir.</span><span class="sxs-lookup"><span data-stu-id="60c53-150">Cancellation requests may be initiated from any thread.</span></span>

 <span data-ttu-id="60c53-151"><xref:System.Threading.CancellationToken.None%2A?displayProperty=nameWithType>Bu değeri, İptalin hiçbir şekilde istenmeyeceğini göstermek için iptal belirteci kabul eden herhangi bir yönteme geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="60c53-151">You can pass the <xref:System.Threading.CancellationToken.None%2A?displayProperty=nameWithType> value to any method that accepts a cancellation token to indicate that cancellation will never be requested.</span></span>  <span data-ttu-id="60c53-152">Bu, <xref:System.Threading.CancellationToken.CanBeCanceled%2A?displayProperty=nameWithType> özelliğin döndürülmesini sağlar `false` ve çağrılan yöntem buna göre iyileştirebilirler.</span><span class="sxs-lookup"><span data-stu-id="60c53-152">This causes the <xref:System.Threading.CancellationToken.CanBeCanceled%2A?displayProperty=nameWithType> property to return `false`, and the called method can optimize accordingly.</span></span>  <span data-ttu-id="60c53-153">Sınama amacıyla, belirtecin zaten iptal edilmiş veya iptal edilemez durumunda başlaması gerekip gerekmediğini belirtmek için bir Boole değeri kabul eden oluşturucuyu kullanarak, önceden iptal edilmiş bir iptal belirteci de geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="60c53-153">For testing purposes, you can also pass in a pre-canceled cancellation token that is instantiated by using the constructor that accepts a Boolean value to indicate whether the token should start in an already-canceled or not-cancelable state.</span></span>

 <span data-ttu-id="60c53-154">Bu iptale yönelik bu yaklaşım birkaç avantaj sağlar:</span><span class="sxs-lookup"><span data-stu-id="60c53-154">This approach to cancellation has several advantages:</span></span>

- <span data-ttu-id="60c53-155">Aynı iptal belirtecini herhangi bir sayıda zaman uyumsuz ve zaman uyumlu işleme geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="60c53-155">You can pass the same cancellation token to any number of asynchronous and synchronous operations.</span></span>

- <span data-ttu-id="60c53-156">Aynı iptal isteği herhangi bir sayıda dinleyiciyle aynı olabilir.</span><span class="sxs-lookup"><span data-stu-id="60c53-156">The same cancellation request may be proliferated to any number of listeners.</span></span>

- <span data-ttu-id="60c53-157">Zaman uyumsuz API 'nin geliştiricisi, İptalin istenip istenmeyeceğini ve ne zaman etkili olabileceğini kontrol ediyor.</span><span class="sxs-lookup"><span data-stu-id="60c53-157">The developer of the asynchronous API is in complete control of whether cancellation may be requested and when it may take effect.</span></span>

- <span data-ttu-id="60c53-158">API 'YI tüketen kod, iptal isteklerinin yayılacağı zaman uyumsuz çağırmaları seçmeli olarak belirleyebilir.</span><span class="sxs-lookup"><span data-stu-id="60c53-158">The code that consumes the API may selectively determine the asynchronous invocations that cancellation requests will be propagated to.</span></span>

## <a name="monitoring-progress"></a><span data-ttu-id="60c53-159">İlerlemeyi İzleme</span><span class="sxs-lookup"><span data-stu-id="60c53-159">Monitoring Progress</span></span>
 <span data-ttu-id="60c53-160">Bazı zaman uyumsuz yöntemler, zaman uyumsuz metoda geçirilen bir ilerleme arabirimiyle ilerlemeyi açığa çıkarır.</span><span class="sxs-lookup"><span data-stu-id="60c53-160">Some asynchronous methods expose progress through a progress interface passed into the asynchronous method.</span></span>  <span data-ttu-id="60c53-161">Örneğin, bir metin dizesini zaman uyumsuz olarak indirdiği ve bu nedenle şu ana kadar tamamlanan indirme yüzdesini içeren ilerleme güncelleştirmelerini Başlatan bir işlevi düşünün.</span><span class="sxs-lookup"><span data-stu-id="60c53-161">For example, consider a function that asynchronously downloads a string of text, and along the way raises progress updates that include the percentage of the download that has completed thus far.</span></span>  <span data-ttu-id="60c53-162">Böyle bir yöntem, aşağıdaki gibi bir Windows Presentation Foundation (WPF) uygulamasında tüketilebilir:</span><span class="sxs-lookup"><span data-stu-id="60c53-162">Such a method could be consumed in a Windows Presentation Foundation (WPF) application as follows:</span></span>

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
## <a name="using-the-built-in-task-based-combinators"></a><span data-ttu-id="60c53-163">Yerleşik görev tabanlı kombinatör kullanma</span><span class="sxs-lookup"><span data-stu-id="60c53-163">Using the Built-in Task-based Combinators</span></span>
 <span data-ttu-id="60c53-164"><xref:System.Threading.Tasks>Ad alanı, görevler oluşturmak ve bunlarla çalışmak için birkaç yöntem içerir.</span><span class="sxs-lookup"><span data-stu-id="60c53-164">The <xref:System.Threading.Tasks> namespace includes several methods for composing and working with tasks.</span></span>

### <a name="taskrun"></a><span data-ttu-id="60c53-165">Task. Run</span><span class="sxs-lookup"><span data-stu-id="60c53-165">Task.Run</span></span>
 <span data-ttu-id="60c53-166"><xref:System.Threading.Tasks.Task>Sınıfı, <xref:System.Threading.Tasks.Task.Run%2A> iş parçacığı havuzu olarak iş parçacığını kolayca boşaltmenizi sağlayan çeşitli yöntemler içerir <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601> , örneğin:</span><span class="sxs-lookup"><span data-stu-id="60c53-166">The <xref:System.Threading.Tasks.Task> class includes several <xref:System.Threading.Tasks.Task.Run%2A> methods that let you easily offload work as a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> to the thread pool, for example:</span></span>

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

 <span data-ttu-id="60c53-167">Bu yöntemlerin bazıları (aşırı yükleme gibi), <xref:System.Threading.Tasks.Task.Run%2A> <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType> yöntemi için toplu olarak mevcuttur <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="60c53-167">Some of these <xref:System.Threading.Tasks.Task.Run%2A> methods, such as the <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType> overload, exist as shorthand for the <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> method.</span></span>  <span data-ttu-id="60c53-168">Gibi diğer aşırı yüklemeler, <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType> boşaltılan iş içinde await kullanmanıza olanak sağlar, örneğin:</span><span class="sxs-lookup"><span data-stu-id="60c53-168">Other overloads, such as <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType>, enable you to use await within the offloaded work, for example:</span></span>

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

 <span data-ttu-id="60c53-169">Bu tür aşırı yüklemeler, <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> görev paralel kitaplığındaki genişletme yöntemiyle birlikte yöntemi kullanılarak mantıksal olarak eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="60c53-169">Such overloads are logically equivalent to using the <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> method in conjunction with the <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> extension method in the Task Parallel Library.</span></span>

### <a name="taskfromresult"></a><span data-ttu-id="60c53-170">Task. FromResult</span><span class="sxs-lookup"><span data-stu-id="60c53-170">Task.FromResult</span></span>
 <span data-ttu-id="60c53-171"><xref:System.Threading.Tasks.Task.FromResult%2A>Verilerin zaten kullanılabildiği senaryolarda yöntemi kullanın ve yalnızca bir görev döndüren yöntem yükseltilmemiş ' a geri döndürülüyor <xref:System.Threading.Tasks.Task%601> :</span><span class="sxs-lookup"><span data-stu-id="60c53-171">Use the <xref:System.Threading.Tasks.Task.FromResult%2A> method in scenarios where data may already be available and just needs to be returned from a task-returning method lifted into a <xref:System.Threading.Tasks.Task%601>:</span></span>

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

### <a name="taskwhenall"></a><span data-ttu-id="60c53-172">Task.WhenAll</span><span class="sxs-lookup"><span data-stu-id="60c53-172">Task.WhenAll</span></span>
 <span data-ttu-id="60c53-173"><xref:System.Threading.Tasks.Task.WhenAll%2A>Görev olarak temsil edilen birden çok zaman uyumsuz işlemde zaman uyumsuz olarak beklemek için yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="60c53-173">Use the <xref:System.Threading.Tasks.Task.WhenAll%2A> method to asynchronously wait on multiple asynchronous operations that are represented as tasks.</span></span>  <span data-ttu-id="60c53-174">Yönteminde, genel olmayan bir görev kümesini veya tek biçimli genel görev kümesini (örneğin, birden çok void döndüren işlemleri bekleniyor veya her değerin farklı bir türü olan birden çok değer döndüren yöntemler için zaman uyumsuz) destekleyen birden çok aşırı yükleme vardır ve tek bir genel görev kümesini (zaman uyumsuz olarak birden çok `TResult` dönen yöntemler için bekleyen) destekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="60c53-174">The method has multiple overloads that support a set of non-generic tasks or a non-uniform set of generic tasks (for example, asynchronously waiting for multiple void-returning operations, or asynchronously waiting for multiple value-returning methods where each value may have a different type) and to support a uniform set of generic tasks (such as asynchronously waiting for multiple `TResult`-returning methods).</span></span>

 <span data-ttu-id="60c53-175">Birkaç müşteriye e-posta iletileri göndermek istediğinizi varsayalım.</span><span class="sxs-lookup"><span data-stu-id="60c53-175">Let's say you want to send email messages to several customers.</span></span> <span data-ttu-id="60c53-176">Bir sonraki göndermeden önce bir iletinin tamamlanmasını beklemmeniz için iletilerin gönderilmesini örtüştürüyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="60c53-176">You can overlap sending the messages so you're not waiting for one message to complete before sending the next.</span></span> <span data-ttu-id="60c53-177">Gönderme işlemlerinin ne zaman tamamlandığını ve herhangi bir hata oluşup oluşmadığını da öğrenebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="60c53-177">You can also find out when the send operations have completed and whether any errors have occurred:</span></span>

```csharp
IEnumerable<Task> asyncOps = from addr in addrs select SendMailAsync(addr);
await Task.WhenAll(asyncOps);
```

 <span data-ttu-id="60c53-178">Bu kod, oluşabilecek özel durumları açıkça işlemez, ancak özel durumların `await` kaynağından elde edilen görevin dışına yayılmasını sağlar <xref:System.Threading.Tasks.Task.WhenAll%2A> .</span><span class="sxs-lookup"><span data-stu-id="60c53-178">This code doesn't explicitly handle exceptions that may occur, but lets exceptions propagate out of the `await` on the resulting task from <xref:System.Threading.Tasks.Task.WhenAll%2A>.</span></span>  <span data-ttu-id="60c53-179">Özel durumları işlemek için aşağıdakiler gibi bir kod kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="60c53-179">To handle the exceptions, you can use code such as the following:</span></span>

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

 <span data-ttu-id="60c53-180">Bu durumda, zaman uyumsuz bir işlem başarısız olursa, tüm özel durumlar, <xref:System.AggregateException> yönteminden döndürülen ' de depolanan bir özel durumla birleştirilir <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task.WhenAll%2A> .</span><span class="sxs-lookup"><span data-stu-id="60c53-180">In this case, if any asynchronous operation fails, all the exceptions will be consolidated in an <xref:System.AggregateException> exception, which is stored in the <xref:System.Threading.Tasks.Task> that is returned from the <xref:System.Threading.Tasks.Task.WhenAll%2A> method.</span></span>  <span data-ttu-id="60c53-181">Ancak, bu özel durumlardan yalnızca biri anahtar sözcük tarafından yayılır `await` .</span><span class="sxs-lookup"><span data-stu-id="60c53-181">However, only one of those exceptions is propagated by the `await` keyword.</span></span>  <span data-ttu-id="60c53-182">Tüm özel durumları incelemek istiyorsanız, önceki kodu aşağıdaki gibi yeniden yazabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="60c53-182">If you want to examine all the exceptions, you can rewrite the previous code as follows:</span></span>

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

 <span data-ttu-id="60c53-183">Web 'den zaman uyumsuz olarak birden çok dosya indirme örneği ele alalım.</span><span class="sxs-lookup"><span data-stu-id="60c53-183">Let's consider an example of downloading multiple files from the web asynchronously.</span></span>  <span data-ttu-id="60c53-184">Bu durumda, tüm zaman uyumsuz işlemlerin homojen sonuç türleri vardır ve sonuçlara erişmek kolaydır:</span><span class="sxs-lookup"><span data-stu-id="60c53-184">In this case, all the asynchronous operations have homogeneous result types, and it's easy to access the results:</span></span>

```csharp
string [] pages = await Task.WhenAll(
    from url in urls select DownloadStringAsync(url));
```

 <span data-ttu-id="60c53-185">Önceki void döndüren senaryoda açıklandığımız aynı özel durum işleme tekniklerini kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="60c53-185">You can use the same exception-handling techniques we discussed in the previous void-returning scenario:</span></span>

```csharp
Task<string> [] asyncOps =
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

### <a name="taskwhenany"></a><span data-ttu-id="60c53-186">Task.WhenAny</span><span class="sxs-lookup"><span data-stu-id="60c53-186">Task.WhenAny</span></span>
 <span data-ttu-id="60c53-187"><xref:System.Threading.Tasks.Task.WhenAny%2A>İşlem için görev olarak temsil edilen birden çok zaman uyumsuz işlemden yalnızca birini zaman uyumsuz olarak beklemek için yöntemini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="60c53-187">You can use the <xref:System.Threading.Tasks.Task.WhenAny%2A> method to asynchronously wait for just one of multiple asynchronous operations represented as tasks to complete.</span></span>  <span data-ttu-id="60c53-188">Bu yöntem dört birincil kullanım durumu sunar:</span><span class="sxs-lookup"><span data-stu-id="60c53-188">This method serves four primary use cases:</span></span>

- <span data-ttu-id="60c53-189">Yedeklilik: bir işlemi birden çok kez gerçekleştirme ve ilk olarak tamamlanan birini seçme (örneğin, tek bir sonuç üreten ve en hızlı şekilde tamamlanarak birden çok hisse senedi teklifiyle Web hizmetine bağlantı kurma).</span><span class="sxs-lookup"><span data-stu-id="60c53-189">Redundancy:  Performing an operation multiple times and selecting the one that completes first (for example, contacting multiple stock quote web services that will produce a single result and selecting the one that completes the fastest).</span></span>

- <span data-ttu-id="60c53-190">Araya ekleme: birden çok işlem başlatma ve tümünün tamamlanmasını bekleme, ancak tamamlandıkları gibi işleme.</span><span class="sxs-lookup"><span data-stu-id="60c53-190">Interleaving:  Launching multiple operations and waiting for all of them to complete, but processing them as they complete.</span></span>

- <span data-ttu-id="60c53-191">Daraltma: diğer işlemlerin, diğerleri tamamlanana kadar başlaması sağlanır.</span><span class="sxs-lookup"><span data-stu-id="60c53-191">Throttling:  Allowing additional operations to begin as others complete.</span></span>  <span data-ttu-id="60c53-192">Bu, araya ekleme senaryosunun bir uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="60c53-192">This is an extension of the interleaving scenario.</span></span>

- <span data-ttu-id="60c53-193">Erken baılout: Örneğin, görev T1 ile temsil edilen bir işlem, <xref:System.Threading.Tasks.Task.WhenAny%2A> başka bir görev T2 ile bir görevde gruplandırılabilir ve <xref:System.Threading.Tasks.Task.WhenAny%2A> görevde bekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="60c53-193">Early bailout:  For example, an operation represented by task t1 can be grouped in a <xref:System.Threading.Tasks.Task.WhenAny%2A> task with another task t2, and you can wait on the <xref:System.Threading.Tasks.Task.WhenAny%2A> task.</span></span> <span data-ttu-id="60c53-194">Görev T2, bir zaman aşımını veya iptali ya da bir görevin T1 tamamlanmadan önce tamamlanmasını sağlayan başka bir sinyali temsil ediyor <xref:System.Threading.Tasks.Task.WhenAny%2A> .</span><span class="sxs-lookup"><span data-stu-id="60c53-194">Task t2 could represent a time-out, or cancellation, or some other signal that causes the <xref:System.Threading.Tasks.Task.WhenAny%2A> task to complete before t1 completes.</span></span>

#### <a name="redundancy"></a><span data-ttu-id="60c53-195">Yedeklilik</span><span class="sxs-lookup"><span data-stu-id="60c53-195">Redundancy</span></span>
 <span data-ttu-id="60c53-196">Bir stok satın alıp almayacağı konusunda bir karar vermek istediğiniz bir durum düşünün.</span><span class="sxs-lookup"><span data-stu-id="60c53-196">Consider a case where you want to make a decision about whether to buy a stock.</span></span>  <span data-ttu-id="60c53-197">Güvendiğiniz birkaç hisse senedi önerisi Web hizmeti bulunur, ancak günlük yüküne bağlı olarak her hizmet farklı zamanlarda yavaş yavaş çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="60c53-197">There are several stock recommendation web services that you trust, but depending on daily load, each service can end up being slow at different times.</span></span>  <span data-ttu-id="60c53-198"><xref:System.Threading.Tasks.Task.WhenAny%2A>Herhangi bir işlem tamamlandığında bildirim almak için yöntemini kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="60c53-198">You can use the <xref:System.Threading.Tasks.Task.WhenAny%2A> method to receive a notification when any operation completes:</span></span>

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

 <span data-ttu-id="60c53-199"><xref:System.Threading.Tasks.Task.WhenAll%2A>Başarıyla tamamlanan tüm görevlerin sarmalanmamış sonuçlarını döndüren aksine, <xref:System.Threading.Tasks.Task.WhenAny%2A> Tamamlanan görevi döndürür.</span><span class="sxs-lookup"><span data-stu-id="60c53-199">Unlike <xref:System.Threading.Tasks.Task.WhenAll%2A>, which returns the unwrapped results of all tasks that completed successfully, <xref:System.Threading.Tasks.Task.WhenAny%2A> returns the task that completed.</span></span> <span data-ttu-id="60c53-200">Bir görev başarısız olursa, başarısız olması ve bir görevin başarılı olması durumunda, döndürülen değerin hangi görevi ilişkilendirildiğini bilmemiz önemlidir.</span><span class="sxs-lookup"><span data-stu-id="60c53-200">If a task fails, it's important to know that it failed, and if a task succeeds, it's important to know which task the return value is associated with.</span></span>  <span data-ttu-id="60c53-201">Bu nedenle, döndürülen görevin sonucuna erişmeniz veya bu örnekte gösterildiği gibi daha fazla beklemek gerekir.</span><span class="sxs-lookup"><span data-stu-id="60c53-201">Therefore, you need to access the result of the returned task, or further await it, as  this example shows.</span></span>

 <span data-ttu-id="60c53-202">İle olduğu gibi <xref:System.Threading.Tasks.Task.WhenAll%2A> , özel durumlara uyum sağlayabilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="60c53-202">As with <xref:System.Threading.Tasks.Task.WhenAll%2A>, you have to be able to accommodate exceptions.</span></span>  <span data-ttu-id="60c53-203">Tamamlanan görevi geri aldığınıza göre döndürülen görevi, hata yayılmasını ve `try/catch` bunları uygun şekilde almanızı sağlayabilirsiniz; örneğin:</span><span class="sxs-lookup"><span data-stu-id="60c53-203">Because you receive the completed task back, you can await the returned task to have errors propagated, and `try/catch` them appropriately; for example:</span></span>

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

 <span data-ttu-id="60c53-204">Ayrıca, bir ilk görev başarıyla tamamlanırsa bile sonraki görevler başarısız olabilir.</span><span class="sxs-lookup"><span data-stu-id="60c53-204">Additionally, even if a first task completes successfully, subsequent tasks may fail.</span></span>  <span data-ttu-id="60c53-205">Bu noktada, özel durumlarla uğraşmaya yönelik çeşitli seçenekleriniz vardır: tüm başlatılan görevler tamamlanana kadar bekleyebilirsiniz, bu durumda <xref:System.Threading.Tasks.Task.WhenAll%2A> yöntemini kullanabilir veya tüm özel durumların önemli olduğuna ve günlüğe kaydedilecek şekilde çalışmanıza karar verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="60c53-205">At this point, you have several options for dealing with exceptions:  You can wait until all the launched tasks have completed, in which case you can use the <xref:System.Threading.Tasks.Task.WhenAll%2A> method, or you can decide that all exceptions are important and must be logged.</span></span>  <span data-ttu-id="60c53-206">Bu şekilde, görevler zaman uyumsuz olarak tamamlandığında bir bildirim almak için devamlılıkları kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="60c53-206">For this, you can use continuations to receive a notification when tasks have completed asynchronously:</span></span>

```csharp
foreach(Task recommendation in recommendations)
{
    var ignored = recommendation.ContinueWith(
        t => { if (t.IsFaulted) Log(t.Exception); });
}
```

 <span data-ttu-id="60c53-207">veya:</span><span class="sxs-lookup"><span data-stu-id="60c53-207">or:</span></span>

```csharp
foreach(Task recommendation in recommendations)
{
    var ignored = recommendation.ContinueWith(
        t => Log(t.Exception), TaskContinuationOptions.OnlyOnFaulted);
}
```

 <span data-ttu-id="60c53-208">Hatta:</span><span class="sxs-lookup"><span data-stu-id="60c53-208">or even:</span></span>

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

 <span data-ttu-id="60c53-209">Son olarak, kalan tüm işlemleri iptal etmek isteyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="60c53-209">Finally, you may want to cancel all the remaining operations:</span></span>

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

#### <a name="interleaving"></a><span data-ttu-id="60c53-210">Araya</span><span class="sxs-lookup"><span data-stu-id="60c53-210">Interleaving</span></span>
 <span data-ttu-id="60c53-211">Web 'den görüntü indirirken ve her görüntüyü işlerken (örneğin, bir kullanıcı arabirimi denetimine görüntü ekleme) bir durum düşünün.</span><span class="sxs-lookup"><span data-stu-id="60c53-211">Consider a case where you're downloading images from the web and processing each image (for example, adding the image to a UI control).</span></span> <span data-ttu-id="60c53-212">Görüntüleri Kullanıcı arabirimi iş parçacığında sırayla işleyebilirsiniz, ancak görüntüleri mümkün olduğunca eşzamanlı olarak indirmek istersiniz.</span><span class="sxs-lookup"><span data-stu-id="60c53-212">You process the images sequentially on the UI thread, but want to download the images as concurrently as possible.</span></span> <span data-ttu-id="60c53-213">Ayrıca, tümünün indirilene kadar, Kullanıcı arabirimine de görüntü eklemek istemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="60c53-213">Also, you don't want to hold up adding the images to the UI until they're all downloaded.</span></span> <span data-ttu-id="60c53-214">Bunun yerine, bunları tamamlanmış olarak eklemek istersiniz.</span><span class="sxs-lookup"><span data-stu-id="60c53-214">Instead, you want to add them as they complete.</span></span>

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

 <span data-ttu-id="60c53-215">Ayrıca, indirilen görüntülerin üzerinde yoğun işlem tüketen işleme içeren bir senaryoya araya ekleme uygulayabilirsiniz <xref:System.Threading.ThreadPool> ; Örneğin:</span><span class="sxs-lookup"><span data-stu-id="60c53-215">You can also apply interleaving to a scenario that involves computationally intensive processing on the <xref:System.Threading.ThreadPool> of the downloaded images; for example:</span></span>

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

#### <a name="throttling"></a><span data-ttu-id="60c53-216">Azaltma</span><span class="sxs-lookup"><span data-stu-id="60c53-216">Throttling</span></span>
 <span data-ttu-id="60c53-217">Kullanıcının indirdiği, indirmelerin kısıtlanacak birçok görüntünün olması dışında, araya ekleme örneğini düşünün; Örneğin, aynı anda yalnızca belirli sayıda indirmelerin gerçekleşmesini istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="60c53-217">Consider the interleaving example, except that the user is downloading so many images that the downloads have to be throttled; for example, you want only a specific number of downloads to happen concurrently.</span></span> <span data-ttu-id="60c53-218">Bunu başarmak için, zaman uyumsuz işlemlerin bir alt kümesini başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="60c53-218">To achieve this, you can start a subset of the asynchronous operations.</span></span>  <span data-ttu-id="60c53-219">İşlemler tamamlandıktan sonra, bunların yerini almak için ek işlemler başlatabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="60c53-219">As operations complete, you can start additional operations to take their place:</span></span>

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

#### <a name="early-bailout"></a><span data-ttu-id="60c53-220">Erken Baılout</span><span class="sxs-lookup"><span data-stu-id="60c53-220">Early Bailout</span></span>
 <span data-ttu-id="60c53-221">Bir işlemin tamamlanması için zaman uyumsuz olarak bir kullanıcının iptal isteğine (örneğin, Kullanıcı bir iptal düğmesine tıkladığını) göz önünde bulundurdığınızı düşünün.</span><span class="sxs-lookup"><span data-stu-id="60c53-221">Consider that you're waiting asynchronously for an operation to complete while simultaneously responding to a user's cancellation request (for example, the user clicked a cancel button).</span></span> <span data-ttu-id="60c53-222">Aşağıdaki kod bu senaryoyu göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="60c53-222">The following code illustrates this scenario:</span></span>

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

 <span data-ttu-id="60c53-223">Bu uygulama, zaman aşımına uğrar, ancak temeldeki zaman uyumsuz işlemleri iptal etmez, Kullanıcı arabirimini yeniden sağlar.</span><span class="sxs-lookup"><span data-stu-id="60c53-223">This implementation re-enables the user interface as soon as you decide to bail out, but doesn't cancel the underlying asynchronous operations.</span></span> <span data-ttu-id="60c53-224">Diğer bir seçenek de, işlem tamamlanana kadar Kullanıcı arabirimini yeniden yüklemeden, ancak erken sona erme isteği nedeniyle erken bitebileceği için bekleyen işlemleri iptal etmek olacaktır:</span><span class="sxs-lookup"><span data-stu-id="60c53-224">Another alternative would be to cancel the pending operations when you decide to bail out, but not reestablish the user interface until the operations complete, potentially due to ending early due to the cancellation request:</span></span>

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

 <span data-ttu-id="60c53-225">Erken bailout 'ın başka bir örneği, yönteminin <xref:System.Threading.Tasks.Task.WhenAny%2A> <xref:System.Threading.Tasks.Task.Delay%2A> sonraki bölümde anlatıldığı gibi yöntemiyle birlikte kullanılmasını içerir.</span><span class="sxs-lookup"><span data-stu-id="60c53-225">Another example of early bailout involves using the <xref:System.Threading.Tasks.Task.WhenAny%2A> method in conjunction with the <xref:System.Threading.Tasks.Task.Delay%2A> method, as discussed in the next section.</span></span>

### <a name="taskdelay"></a><span data-ttu-id="60c53-226">Task.Delay</span><span class="sxs-lookup"><span data-stu-id="60c53-226">Task.Delay</span></span>
 <span data-ttu-id="60c53-227"><xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType>Bir zaman uyumsuz yöntemin yürütülmesine duraklamalar tanıtmak için yöntemini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="60c53-227">You can use the <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> method to introduce pauses into an asynchronous method's execution.</span></span>  <span data-ttu-id="60c53-228">Bu, yoklama döngüleri oluşturma ve önceden belirlenmiş bir süre için Kullanıcı girişinin işlenmesini erteleme dahil olmak üzere çok sayıda işlevsellik için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="60c53-228">This is useful for many kinds of functionality, including building polling loops and delaying the handling of user input for a predetermined period of time.</span></span>  <span data-ttu-id="60c53-229"><xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType>Yöntemi, <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> await üzerinde zaman aşımlarını uygulamak için ile birlikte da yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="60c53-229">The <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> method can also be useful in combination with <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> for implementing time-outs on awaits.</span></span>

 <span data-ttu-id="60c53-230">Daha büyük bir zaman uyumsuz işlemin (örneğin, bir ASP.NET Web hizmeti) parçası olan bir görevin tamamlanabilmesi çok uzun sürerse, bu durum özellikle tamamlanamazsa, genel işlem zarar verebilir.</span><span class="sxs-lookup"><span data-stu-id="60c53-230">If a task that's part of a larger asynchronous operation (for example, an ASP.NET web service) takes too long to complete, the overall operation could suffer, especially if it fails to ever complete.</span></span>  <span data-ttu-id="60c53-231">Bu nedenle, zaman uyumsuz bir işlem beklerken zaman aşımına uğrar.</span><span class="sxs-lookup"><span data-stu-id="60c53-231">For this reason, it's important to be able to time out when waiting on an asynchronous operation.</span></span>  <span data-ttu-id="60c53-232">Zaman uyumlu <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> , <xref:System.Threading.Tasks.Task.WaitAll%2A?displayProperty=nameWithType> ve <xref:System.Threading.Tasks.Task.WaitAny%2A?displayProperty=nameWithType> yöntemleri zaman aşımı değerlerini kabul eder, ancak karşılık gelen <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType> / <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> ve yukarıda bahsedilen <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> / <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> Yöntemler değildir.</span><span class="sxs-lookup"><span data-stu-id="60c53-232">The synchronous <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Task.WaitAll%2A?displayProperty=nameWithType>, and <xref:System.Threading.Tasks.Task.WaitAny%2A?displayProperty=nameWithType> methods accept time-out values, but the corresponding <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType>/<xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> and the previously mentioned <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>/<xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> methods do not.</span></span>  <span data-ttu-id="60c53-233">Bunun yerine, <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> zaman aşımı uygulamak için ve birleşimini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="60c53-233">Instead, you can use <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> in combination to implement a time-out.</span></span>

 <span data-ttu-id="60c53-234">Örneğin, Kullanıcı arabirimi uygulamanızda bir görüntü indirmek ve görüntü indirilirken Kullanıcı arabirimini devre dışı bırakmak istediğinizi varsayalım.</span><span class="sxs-lookup"><span data-stu-id="60c53-234">For example, in your UI application, let's say that you want to download an image and disable the UI while the image is downloading.</span></span> <span data-ttu-id="60c53-235">Ancak indirme çok uzun sürerse, Kullanıcı arabirimini yeniden etkinleştirmek ve indirmeyi atmak istersiniz:</span><span class="sxs-lookup"><span data-stu-id="60c53-235">However, if the download takes too long, you want to re-enable the UI and discard the download:</span></span>

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

 <span data-ttu-id="60c53-236">Aynı durum birden çok indirme için geçerlidir, çünkü <xref:System.Threading.Tasks.Task.WhenAll%2A> bir görevi döndürür:</span><span class="sxs-lookup"><span data-stu-id="60c53-236">The same applies to multiple downloads, because <xref:System.Threading.Tasks.Task.WhenAll%2A> returns a task:</span></span>

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

## <a name="building-task-based-combinators"></a><span data-ttu-id="60c53-237">Görev tabanlı kombinatör oluşturma</span><span class="sxs-lookup"><span data-stu-id="60c53-237">Building Task-based Combinators</span></span>
 <span data-ttu-id="60c53-238">Bir görev, zaman uyumsuz bir işlemi tamamen temsil edebildiğinden ve işlemle birleştirmek için zaman uyumlu ve zaman uyumsuz yetenekler sağladığından, sonuçlarını almakla ve bu şekilde devam ediyorsa, daha büyük desenler oluşturmak için görevler oluşturan yararlı kombinatör kitaplıkları oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="60c53-238">Because a task is able to completely represent an asynchronous operation and provide synchronous and asynchronous capabilities for joining with the operation, retrieving its results, and so on, you can build useful libraries of combinators that compose tasks to build larger patterns.</span></span>  <span data-ttu-id="60c53-239">Önceki bölümde anlatıldığı gibi .NET Framework çeşitli yerleşik kombinatör içerir, ancak kendi kodunuzu da oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="60c53-239">As discussed in the previous section, the .NET Framework includes several built-in combinators, but you can also build your own.</span></span> <span data-ttu-id="60c53-240">Aşağıdaki bölümlerde olası Combinator yöntemlerine ve türlerine birkaç örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="60c53-240">The following sections provide several examples of potential combinator methods and types.</span></span>

### <a name="retryonfault"></a><span data-ttu-id="60c53-241">RetryOnFault</span><span class="sxs-lookup"><span data-stu-id="60c53-241">RetryOnFault</span></span>
 <span data-ttu-id="60c53-242">Birçok durumda, önceki bir deneme başarısız olursa bir işlemi yeniden denemek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="60c53-242">In many situations, you may want to retry an operation if a previous attempt fails.</span></span>  <span data-ttu-id="60c53-243">Zaman uyumlu kod için, `RetryOnFault` bunu gerçekleştirmek için aşağıdaki örnekte gibi bir yardımcı yöntem oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="60c53-243">For synchronous code, you might build a helper method such as `RetryOnFault` in the following example to accomplish this:</span></span>

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

 <span data-ttu-id="60c53-244">DOKUNARAK uygulanan ve bu nedenle görevleri döndüren zaman uyumsuz işlemler için neredeyse özdeş bir yardımcı yöntem oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="60c53-244">You can build an almost identical helper method for asynchronous operations that are implemented with TAP and thus return tasks:</span></span>

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

 <span data-ttu-id="60c53-245">Daha sonra bu Combinator kullanarak yeniden denemeleri uygulamanın mantığına dönüştürebilirsiniz; Örneğin:</span><span class="sxs-lookup"><span data-stu-id="60c53-245">You can then use this combinator to encode retries into the application's logic; for example:</span></span>

```csharp
// Download the URL, trying up to three times in case of failure
string pageContents = await RetryOnFault(
    () => DownloadStringAsync(url), 3);
```

 <span data-ttu-id="60c53-246">`RetryOnFault`İşlevi daha fazla genişletebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="60c53-246">You could extend the `RetryOnFault` function further.</span></span> <span data-ttu-id="60c53-247">Örneğin, işlev `Func<Task>` işlemin ne zaman denenmesini anlamak için yeniden denemeler arasında çağrılacak bir tane kabul edebilir. Örneğin:</span><span class="sxs-lookup"><span data-stu-id="60c53-247">For example, the function could accept another `Func<Task>` that will be invoked between retries to determine when to try the operation again; for example:</span></span>

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

 <span data-ttu-id="60c53-248">Ardından, işlemi yeniden denemeden önce bir saniye beklemek için işlevini aşağıdaki şekilde kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="60c53-248">You could then use the function as follows to wait for a second before retrying the operation:</span></span>

```csharp
// Download the URL, trying up to three times in case of failure,
// and delaying for a second between retries
string pageContents = await RetryOnFault(
    () => DownloadStringAsync(url), 3, () => Task.Delay(1000));
```

### <a name="needonlyone"></a><span data-ttu-id="60c53-249">Gereksiz bir</span><span class="sxs-lookup"><span data-stu-id="60c53-249">NeedOnlyOne</span></span>
 <span data-ttu-id="60c53-250">Bazen bir işlemin gecikme süresini ve başarılı olma olasılığını artırmak için yedekliliğe sahip olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="60c53-250">Sometimes, you can take advantage of redundancy to improve an operation's latency and chances for success.</span></span>  <span data-ttu-id="60c53-251">Hisse senedi fiyatları sağlayan birden çok Web hizmeti düşünün, ancak günün çeşitli saatlerinde her hizmet farklı düzeylerde kalite ve yanıt süreleri sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="60c53-251">Consider multiple web services that provide stock quotes, but at various times of the day, each service may provide different levels of quality and response times.</span></span>  <span data-ttu-id="60c53-252">Bu dalgalanmalara ulaşmak için tüm Web hizmetlerine istek verebilir ve birinden yanıt aldığınızda, kalan istekleri iptal edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="60c53-252">To deal with these fluctuations, you may issue requests to all the web services, and as soon as you get a response from one, cancel the remaining requests.</span></span>  <span data-ttu-id="60c53-253">Birden çok işlem başlatmanın bu ortak deseninin uygulanmasını kolaylaştırmak için bir yardımcı işlevi uygulayabilir, herhangi bir bekliyor ve geri kalanını iptal edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="60c53-253">You can implement a helper function to make it easier to implement this common pattern of launching multiple operations, waiting for any, and then canceling the rest.</span></span> <span data-ttu-id="60c53-254">`NeedOnlyOne`Aşağıdaki örnekteki işlev bu senaryoyu göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="60c53-254">The `NeedOnlyOne` function in the following example illustrates this scenario:</span></span>

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

 <span data-ttu-id="60c53-255">Daha sonra bu işlevi aşağıdaki şekilde kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="60c53-255">You can then use this function as follows:</span></span>

```csharp
double currentPrice = await NeedOnlyOne(
    ct => GetCurrentPriceFromServer1Async("msft", ct),
    ct => GetCurrentPriceFromServer2Async("msft", ct),
    ct => GetCurrentPriceFromServer3Async("msft", ct));
```

### <a name="interleaved-operations"></a><span data-ttu-id="60c53-256">Araya eklemeli Işlemler</span><span class="sxs-lookup"><span data-stu-id="60c53-256">Interleaved Operations</span></span>
 <span data-ttu-id="60c53-257"><xref:System.Threading.Tasks.Task.WhenAny%2A>Büyük görev kümeleriyle çalışırken bir araya ekleme senaryosunu desteklemek için yöntemini kullanmayla ilgili olası bir performans sorunu vardır.</span><span class="sxs-lookup"><span data-stu-id="60c53-257">There is a potential performance problem with using the <xref:System.Threading.Tasks.Task.WhenAny%2A> method to support an interleaving scenario when you're working with large sets of tasks.</span></span> <span data-ttu-id="60c53-258"><xref:System.Threading.Tasks.Task.WhenAny%2A>Her bir görevde bir devamlılığın sonucunu elde etmek için her çağrı.</span><span class="sxs-lookup"><span data-stu-id="60c53-258">Every call to <xref:System.Threading.Tasks.Task.WhenAny%2A> results in a continuation being registered with each task.</span></span> <span data-ttu-id="60c53-259">N sayıda görev için, bu, araya ekleme işleminin ömrü boyunca oluşturulan (N<sup>2</sup>) devamlılıklar ile sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="60c53-259">For N number of tasks, this results in O(N<sup>2</sup>) continuations created over the lifetime of the interleaving operation.</span></span> <span data-ttu-id="60c53-260">Büyük bir görev kümesiyle çalışıyorsanız, `Interleaved` performans sorununu gidermek için bir Combinator (aşağıdaki örnekte) kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="60c53-260">If you're working with a large set of tasks, you can use a combinator (`Interleaved` in the following example) to address the performance issue:</span></span>

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

 <span data-ttu-id="60c53-261">Daha sonra, görevlerin sonuçlarını tamamlarsa işlemek için Combinator kullanabilirsiniz; Örneğin:</span><span class="sxs-lookup"><span data-stu-id="60c53-261">You can then use the combinator to process the results of tasks as they complete; for example:</span></span>

```csharp
IEnumerable<Task<int>> tasks = ...;
foreach(var task in Interleaved(tasks))
{
    int result = await task;
    …
}
```

### <a name="whenallorfirstexception"></a><span data-ttu-id="60c53-262">WhenAllOrFirstException</span><span class="sxs-lookup"><span data-stu-id="60c53-262">WhenAllOrFirstException</span></span>
 <span data-ttu-id="60c53-263">Belirli dağılım/toplama senaryolarında, bir küme içindeki tüm görevleri beklemek isteyebilirsiniz, bu durumda, özel durum meydana geldiğinde beklemeyi durdurmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="60c53-263">In certain scatter/gather scenarios, you might want to wait for all tasks in a set, unless one of them faults, in which case you want to stop waiting as soon as the exception occurs.</span></span>  <span data-ttu-id="60c53-264">Bunu, aşağıdaki örnekte olduğu gibi bir Combinator yöntemi ile gerçekleştirebilirsiniz `WhenAllOrFirstException` :</span><span class="sxs-lookup"><span data-stu-id="60c53-264">You can accomplish that with a combinator method such as `WhenAllOrFirstException` in the following example:</span></span>

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

## <a name="building-task-based-data-structures"></a><span data-ttu-id="60c53-265">Görev tabanlı veri yapıları oluşturma</span><span class="sxs-lookup"><span data-stu-id="60c53-265">Building Task-based Data Structures</span></span>
 <span data-ttu-id="60c53-266">Özel görev tabanlı kombinatör oluşturma özelliğine ek olarak, ' de bir veri yapısına sahip olmak ve <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601> hem zaman uyumsuz bir işlemin sonuçlarını hem de bununla birleştirmek için gereken eşitlemeyi temsil eden, zaman uyumsuz senaryolarda kullanılacak özel veri yapılarını oluşturmak için güçlü bir tür yapar.</span><span class="sxs-lookup"><span data-stu-id="60c53-266">In addition to the ability to build custom task-based combinators, having a data structure in <xref:System.Threading.Tasks.Task> and <xref:System.Threading.Tasks.Task%601> that represents both the results of an asynchronous operation and the necessary synchronization to join with it makes it a powerful type on which to build custom data structures to be used in asynchronous scenarios.</span></span>

### <a name="asynccache"></a><span data-ttu-id="60c53-267">AsyncCache</span><span class="sxs-lookup"><span data-stu-id="60c53-267">AsyncCache</span></span>
 <span data-ttu-id="60c53-268">Bir görevin önemli bir yönü, birden fazla tüketiciye, hepsi tarafından bekleme, devamlılık veya özel durumları (söz konusu olduğunda) elde ettirebilir <xref:System.Threading.Tasks.Task%601> .</span><span class="sxs-lookup"><span data-stu-id="60c53-268">One important aspect of a task is that it may be handed out to multiple consumers, all of whom may await it, register continuations with it, get its result or exceptions (in the case of <xref:System.Threading.Tasks.Task%601>), and so on.</span></span>  <span data-ttu-id="60c53-269">Bu <xref:System.Threading.Tasks.Task> , <xref:System.Threading.Tasks.Task%601> zaman uyumsuz bir önbelleğe alma altyapısında kullanılmasını sağlar ve idealdir.</span><span class="sxs-lookup"><span data-stu-id="60c53-269">This makes <xref:System.Threading.Tasks.Task> and <xref:System.Threading.Tasks.Task%601> perfectly suited to be used in an asynchronous caching infrastructure.</span></span>  <span data-ttu-id="60c53-270">Aşağıda, üzerine inşa eden küçük ancak güçlü bir zaman uyumsuz önbellek örneği verilmiştir <xref:System.Threading.Tasks.Task%601> :</span><span class="sxs-lookup"><span data-stu-id="60c53-270">Here's an example of a small but powerful asynchronous cache built on top of <xref:System.Threading.Tasks.Task%601>:</span></span>

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

 <span data-ttu-id="60c53-271">[AsyncCache \<TKey,TValue> ](https://devblogs.microsoft.com/pfxteam/parallelextensionsextras-tour-12-asynccache/) sınıfı, Oluşturucusu için bir temsilci olarak kabul eder `TKey` ve döndürür <xref:System.Threading.Tasks.Task%601> .</span><span class="sxs-lookup"><span data-stu-id="60c53-271">The [AsyncCache\<TKey,TValue>](https://devblogs.microsoft.com/pfxteam/parallelextensionsextras-tour-12-asynccache/) class accepts as a delegate to its constructor a function that takes a `TKey` and returns a <xref:System.Threading.Tasks.Task%601>.</span></span>  <span data-ttu-id="60c53-272">Ön belleğe daha önce erişilen tüm değerler iç sözlükte depolanır ve `AsyncCache` önbelleğe eşzamanlı olarak erişilse bile, her anahtar için yalnızca bir görevin oluşturulmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="60c53-272">Any previously accessed values from the cache are stored in the internal dictionary, and the `AsyncCache` ensures that only one task is generated per key, even if the cache is accessed concurrently.</span></span>

 <span data-ttu-id="60c53-273">Örneğin, indirilen Web sayfaları için bir önbellek oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="60c53-273">For example, you can build a cache for downloaded web pages:</span></span>

```csharp
private AsyncCache<string,string> m_webPages =
    new AsyncCache<string,string>(DownloadStringAsync);
```

 <span data-ttu-id="60c53-274">Böylece, bir Web sayfasının içeriğine ihtiyacınız olduğunda bu önbelleği zaman uyumsuz metotlarda kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="60c53-274">You can then use this cache in asynchronous methods whenever you need the contents of a web page.</span></span> <span data-ttu-id="60c53-275">`AsyncCache`Sınıfı mümkün olduğunca az sayfa indirmenizi ve sonuçları önbelleğe almanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="60c53-275">The `AsyncCache` class ensures that you're downloading as few pages as possible, and caches the results.</span></span>

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

### <a name="asyncproducerconsumercollection"></a><span data-ttu-id="60c53-276">AsyncProducerConsumerCollection</span><span class="sxs-lookup"><span data-stu-id="60c53-276">AsyncProducerConsumerCollection</span></span>
 <span data-ttu-id="60c53-277">Ayrıca, zaman uyumsuz etkinlikleri koordine etmek üzere veri yapıları oluşturmak için görevleri de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="60c53-277">You can also use tasks to build data structures for coordinating asynchronous activities.</span></span>  <span data-ttu-id="60c53-278">Klasik paralel tasarım desenlerinden birini göz önünde bulundurun: Producer/Consumer.</span><span class="sxs-lookup"><span data-stu-id="60c53-278">Consider one of the classic parallel design patterns: producer/consumer.</span></span>  <span data-ttu-id="60c53-279">Bu düzende, üreticileri tüketiciler tarafından tüketilen verileri oluşturur ve üreticileri ve tüketiciler paralel olarak çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="60c53-279">In this pattern, producers generate data that is consumed by consumers, and the producers and consumers may run in parallel.</span></span> <span data-ttu-id="60c53-280">Örneğin, tüketici daha önce öğe 2 ' yi üreten bir üretici tarafından oluşturulan öğe 1 ' i işler.</span><span class="sxs-lookup"><span data-stu-id="60c53-280">For example, the consumer processes item 1, which was previously generated by a producer who is now producing item 2.</span></span>  <span data-ttu-id="60c53-281">Üretici/tüketici düzeninde, müşteriler yeni veriler hakkında bildirim almak ve kullanılabilir olduğunda bulmak için üreticileri tarafından oluşturulan işi depolamak üzere bazı veri yapısına ihtiyacınız vardır.</span><span class="sxs-lookup"><span data-stu-id="60c53-281">For the producer/consumer pattern, you invariably need some data structure to store the work created by producers so that the consumers may be notified of new data and find it when available.</span></span>

 <span data-ttu-id="60c53-282">Aşağıda, zaman uyumsuz yöntemlerin üreticileri ve tüketiciler olarak kullanılmasını sağlayan, görevlerin üzerine inşa edilen basit bir veri yapısı verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="60c53-282">Here's a simple data structure, built on top of tasks, that enables asynchronous methods to be used as producers and consumers:</span></span>

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

 <span data-ttu-id="60c53-283">Bu veri yapısıyla birlikte, aşağıdaki gibi bir kod yazabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="60c53-283">With that data structure in place, you can write code such as the following:</span></span>

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

<span data-ttu-id="60c53-284"><xref:System.Threading.Tasks.Dataflow>Ad alanı, <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> benzer bir şekilde kullanabileceğiniz, ancak özel bir koleksiyon türü oluşturmak zorunda kalmadan türü içerir:</span><span class="sxs-lookup"><span data-stu-id="60c53-284">The <xref:System.Threading.Tasks.Dataflow> namespace includes the <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> type, which you can use in a similar manner, but without having to build a custom collection type:</span></span>

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
> <span data-ttu-id="60c53-285"><xref:System.Threading.Tasks.Dataflow>Ad alanı, **NuGet**aracılığıyla .NET Framework 4,5 ' de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="60c53-285">The <xref:System.Threading.Tasks.Dataflow> namespace is available in the .NET Framework 4.5 through **NuGet**.</span></span> <span data-ttu-id="60c53-286">Ad alanını içeren derlemeyi yüklemek için <xref:System.Threading.Tasks.Dataflow> projenizi Visual Studio 'da açın, proje menüsünden **NuGet Paketlerini Yönet** ' i seçin ve Microsoft. tpl. Dataflow paketini çevrimiçi olarak arayın.</span><span class="sxs-lookup"><span data-stu-id="60c53-286">To install the assembly that contains the <xref:System.Threading.Tasks.Dataflow> namespace, open your project in Visual Studio, choose **Manage NuGet Packages** from the Project menu, and search online for the Microsoft.Tpl.Dataflow package.</span></span>

## <a name="see-also"></a><span data-ttu-id="60c53-287">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="60c53-287">See also</span></span>

- [<span data-ttu-id="60c53-288">Görev Tabanlı Zaman Uyumsuz Desen (TAP)</span><span class="sxs-lookup"><span data-stu-id="60c53-288">Task-based Asynchronous Pattern (TAP)</span></span>](task-based-asynchronous-pattern-tap.md)
- [<span data-ttu-id="60c53-289">Görev Tabanlı Zaman Uyumsuz Deseni Uygulama</span><span class="sxs-lookup"><span data-stu-id="60c53-289">Implementing the Task-based Asynchronous Pattern</span></span>](implementing-the-task-based-asynchronous-pattern.md)
- [<span data-ttu-id="60c53-290">Diğer Zaman Uyumsuz Desen ve Türlerle Birlikte Çalışma</span><span class="sxs-lookup"><span data-stu-id="60c53-290">Interop with Other Asynchronous Patterns and Types</span></span>](interop-with-other-asynchronous-patterns-and-types.md)
