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
ms.openlocfilehash: f80e6ae520ab03c0f5f4edc30c0b7102193ee6c5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73139821"
---
# <a name="consuming-the-task-based-asynchronous-pattern"></a><span data-ttu-id="c4ece-102">Görev Tabanlı Zaman Uyumsuz Desen Kullanma</span><span class="sxs-lookup"><span data-stu-id="c4ece-102">Consuming the Task-based Asynchronous Pattern</span></span>

<span data-ttu-id="c4ece-103">Asynchronous işlemleriyle çalışmak için Görev Tabanlı Eşenkron Desen'i (TAP) kullandığınızda, engellemeden beklemeyi başarmak için geri aramaları kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c4ece-103">When you use the Task-based Asynchronous Pattern (TAP) to work with asynchronous operations, you can use callbacks to achieve waiting without blocking.</span></span>  <span data-ttu-id="c4ece-104">Görevler için bu, <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c4ece-104">For tasks, this is achieved through methods such as <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="c4ece-105">Dil tabanlı eşzamanlı destek, normal denetim akışı içinde asenkron işlemlerin beklenmesine izin vererek geri aramaları gizler ve derleyici tarafından oluşturulan kod aynı API düzeyinde destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="c4ece-105">Language-based asynchronous support hides callbacks by allowing asynchronous operations to be awaited within normal control flow, and compiler-generated code provides this same API-level support.</span></span>

## <a name="suspending-execution-with-await"></a><span data-ttu-id="c4ece-106">Bekleme ile Yürütmeyi Askıya Alma</span><span class="sxs-lookup"><span data-stu-id="c4ece-106">Suspending Execution with Await</span></span>
 <span data-ttu-id="c4ece-107">.NET Framework 4.5'ten başlayarak C#'daki [bekleme](../../csharp/language-reference/operators/await.md) anahtar sözcüklerini ve Visual Basic'teki <xref:System.Threading.Tasks.Task%601> Bekleme [Operatör'üni](../../visual-basic/language-reference/operators/await-operator.md) eşzamanlı olarak bekliyor <xref:System.Threading.Tasks.Task> ve nesneleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c4ece-107">Starting with the .NET Framework 4.5, you can use the [await](../../csharp/language-reference/operators/await.md) keyword in C# and the [Await Operator](../../visual-basic/language-reference/operators/await-operator.md) in Visual Basic to asynchronously await <xref:System.Threading.Tasks.Task> and <xref:System.Threading.Tasks.Task%601> objects.</span></span> <span data-ttu-id="c4ece-108">Bir <xref:System.Threading.Tasks.Task>, `await` ifade yi beklerken. `void`</span><span class="sxs-lookup"><span data-stu-id="c4ece-108">When you're awaiting a <xref:System.Threading.Tasks.Task>, the `await` expression is of type `void`.</span></span> <span data-ttu-id="c4ece-109">Bir <xref:System.Threading.Tasks.Task%601>, `await` ifade yi beklerken. `TResult`</span><span class="sxs-lookup"><span data-stu-id="c4ece-109">When you're awaiting a <xref:System.Threading.Tasks.Task%601>, the `await` expression is of type `TResult`.</span></span> <span data-ttu-id="c4ece-110">Bir `await` ifade bir asynchronous yönteminin gövdesi içinde meydana gelmelidir.</span><span class="sxs-lookup"><span data-stu-id="c4ece-110">An `await` expression must occur inside the body of an asynchronous method.</span></span> <span data-ttu-id="c4ece-111">.NET Framework 4.5'te C# ve Visual Basic dil desteği hakkında daha fazla bilgi için C# ve Visual Basic dil belirtimleri'ne bakın.</span><span class="sxs-lookup"><span data-stu-id="c4ece-111">For more information about C# and Visual Basic language support in the .NET Framework 4.5, see the C# and Visual Basic language specifications.</span></span>

 <span data-ttu-id="c4ece-112">Kapakların altında, bekleme işlevi bir devamı kullanarak göreve bir geri arama yükler.</span><span class="sxs-lookup"><span data-stu-id="c4ece-112">Under the covers, the await functionality installs a callback on the task by using a continuation.</span></span>  <span data-ttu-id="c4ece-113">Bu geri arama süspansiyon noktasında asynchronous yöntemi devam eder.</span><span class="sxs-lookup"><span data-stu-id="c4ece-113">This callback resumes the asynchronous method at the point of suspension.</span></span> <span data-ttu-id="c4ece-114">Eşkron yöntem sürdürüldüğünde, beklenen işlem başarıyla tamamlanıp , <xref:System.Threading.Tasks.Task%601>onun `TResult` döndürülür.</span><span class="sxs-lookup"><span data-stu-id="c4ece-114">When the asynchronous method is resumed, if the awaited operation completed successfully and was a <xref:System.Threading.Tasks.Task%601>, its `TResult` is returned.</span></span>  <span data-ttu-id="c4ece-115">Beklenen <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601> beklenen <xref:System.Threading.Tasks.TaskStatus.Canceled> durumda sona erdiyse, <xref:System.OperationCanceledException> bir özel durum atılır.</span><span class="sxs-lookup"><span data-stu-id="c4ece-115">If the <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> that was awaited ended in the <xref:System.Threading.Tasks.TaskStatus.Canceled> state, an <xref:System.OperationCanceledException> exception is thrown.</span></span>  <span data-ttu-id="c4ece-116">Beklenen <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601> beklenen <xref:System.Threading.Tasks.TaskStatus.Faulted> durum sona erdiyse, hataya neden olan özel durum atılır.</span><span class="sxs-lookup"><span data-stu-id="c4ece-116">If the <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> that was awaited ended in the <xref:System.Threading.Tasks.TaskStatus.Faulted> state, the exception that caused it to fault is thrown.</span></span> <span data-ttu-id="c4ece-117">A, `Task` birden çok özel durum sonucunda hata yapabilir, ancak bu özel durumlardan yalnızca biri yayılır.</span><span class="sxs-lookup"><span data-stu-id="c4ece-117">A `Task` can fault as a result of multiple exceptions, but only one of these exceptions is propagated.</span></span> <span data-ttu-id="c4ece-118">Ancak, <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> özellik tüm <xref:System.AggregateException> hataları içeren bir özel durum döndürür.</span><span class="sxs-lookup"><span data-stu-id="c4ece-118">However, the <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> property returns an <xref:System.AggregateException> exception that contains all the errors.</span></span>

 <span data-ttu-id="c4ece-119">Bir eşitleme bağlamı<xref:System.Threading.SynchronizationContext> (nesnesi) askıya alma sırasında asenkron yöntemi ni gerçekleştiren iş parçacığıyla <xref:System.Threading.SynchronizationContext.Current%2A?displayProperty=nameWithType> ilişkilendirilirse (örneğin, özellik değilse), `null`eş zamanlı yöntem bağlamın <xref:System.Threading.SynchronizationContext.Post%2A> yöntemini kullanarak aynı eşitleme bağlamında devam eder.</span><span class="sxs-lookup"><span data-stu-id="c4ece-119">If a synchronization context (<xref:System.Threading.SynchronizationContext> object) is associated with the thread that was executing the asynchronous method at the time of suspension (for example, if the <xref:System.Threading.SynchronizationContext.Current%2A?displayProperty=nameWithType> property is not `null`), the asynchronous method resumes on that same synchronization context by using the context’s <xref:System.Threading.SynchronizationContext.Post%2A> method.</span></span> <span data-ttu-id="c4ece-120">Aksi takdirde, askıya alma sırasında<xref:System.Threading.Tasks.TaskScheduler> geçerli olan görev zamanlayıcısına (nesne) dayanır.</span><span class="sxs-lookup"><span data-stu-id="c4ece-120">Otherwise, it relies on the task scheduler (<xref:System.Threading.Tasks.TaskScheduler> object) that was current at the time of suspension.</span></span> <span data-ttu-id="c4ece-121">Genellikle, bu iş parçacığı havuzu<xref:System.Threading.Tasks.TaskScheduler.Default%2A?displayProperty=nameWithType>hedefleyen varsayılan görev zamanlayıcısı ( ), olduğunu.</span><span class="sxs-lookup"><span data-stu-id="c4ece-121">Typically, this is the default task scheduler (<xref:System.Threading.Tasks.TaskScheduler.Default%2A?displayProperty=nameWithType>), which targets the thread pool.</span></span> <span data-ttu-id="c4ece-122">Bu görev zamanlayıcısı, beklenen eşsenkronize işlemin tamamlandığı yerde devam edip etmeyeceğini veya yeniden başlamanın zamanlanıp zamanlanmayacağını belirler.</span><span class="sxs-lookup"><span data-stu-id="c4ece-122">This task scheduler determines whether the awaited asynchronous operation should resume where it completed or whether the resumption should be scheduled.</span></span> <span data-ttu-id="c4ece-123">Varsayılan zamanlayıcı genellikle devamın beklenen işlemin tamamlandığı iş parçacığında çalışmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="c4ece-123">The default scheduler typically allows the continuation to run on the thread that the awaited operation completed.</span></span>

 <span data-ttu-id="c4ece-124">Bir eşzamanlı yöntem çağrıldığında, çağrının arayana döndüğü, henüz tamamlanmamış bir bekleyen örnekte ilk bekleyen ifadeye kadar işlevin gövdesini eşzamanlı olarak yürütür.</span><span class="sxs-lookup"><span data-stu-id="c4ece-124">When an asynchronous method is called, it synchronously executes the body of the function up until the first await expression on an awaitable instance that has not yet completed, at which point the invocation returns to the caller.</span></span> <span data-ttu-id="c4ece-125">Eşsenkron yöntem geri dönmezse, `void` <xref:System.Threading.Tasks.Task> devam <xref:System.Threading.Tasks.Task%601> eden hesaplamayı temsil etmek için bir veya nesne döndürülür.</span><span class="sxs-lookup"><span data-stu-id="c4ece-125">If the asynchronous method does not return `void`, a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> object is returned to represent the ongoing computation.</span></span> <span data-ttu-id="c4ece-126">Geçersiz olmayan bir eşzamanlı yöntemde, bir iade deyimiyle karşılaşılırsa veya yöntem gövdesinin sonuna ulaşılırsa, <xref:System.Threading.Tasks.TaskStatus.RanToCompletion> görev son durumda tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="c4ece-126">In a non-void asynchronous method, if a return statement is encountered or the end of the method body is reached, the task is completed in the <xref:System.Threading.Tasks.TaskStatus.RanToCompletion> final state.</span></span> <span data-ttu-id="c4ece-127">Işlenmemiş bir özel durum denetimin eşzamanlı yöntemin gövdesinden ayrılmasına neden <xref:System.Threading.Tasks.TaskStatus.Faulted> olursa, görev durumla biter.</span><span class="sxs-lookup"><span data-stu-id="c4ece-127">If an unhandled exception causes control to leave the body of the asynchronous method, the task ends in the <xref:System.Threading.Tasks.TaskStatus.Faulted> state.</span></span> <span data-ttu-id="c4ece-128">Bu özel durum <xref:System.OperationCanceledException>bir ise, görev <xref:System.Threading.Tasks.TaskStatus.Canceled> yerine durumda sona erer.</span><span class="sxs-lookup"><span data-stu-id="c4ece-128">If that exception is an <xref:System.OperationCanceledException>, the task instead ends in the <xref:System.Threading.Tasks.TaskStatus.Canceled> state.</span></span> <span data-ttu-id="c4ece-129">Bu şekilde, sonuç veya özel durum sonunda yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="c4ece-129">In this manner, the result or exception is eventually published.</span></span>

 <span data-ttu-id="c4ece-130">Bu davranışın birkaç önemli varyasyonları vardır.</span><span class="sxs-lookup"><span data-stu-id="c4ece-130">There are several important variations of this behavior.</span></span>  <span data-ttu-id="c4ece-131">Performans nedenleriyle, görev beklenene kadar bir görev zaten tamamlanmışsa, denetim verim verilmeyecek ve işlev yürütmeye devam eder.</span><span class="sxs-lookup"><span data-stu-id="c4ece-131">For performance reasons, if a task has already completed by the time the task is awaited, control is not yielded, and the function continues to execute.</span></span>  <span data-ttu-id="c4ece-132">Ayrıca, özgün içeriğe dönmek her zaman istenen davranış değildir ve değiştirilebilir; bu sonraki bölümde daha ayrıntılı olarak açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="c4ece-132">Additionally, returning to the original context isn't always the desired behavior and can be changed; this is described in more detail in the next section.</span></span>

### <a name="configuring-suspension-and-resumption-with-yield-and-configureawait"></a><span data-ttu-id="c4ece-133">Verim ve Yapılandırma Ile Süspansiyon ve Devamı Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="c4ece-133">Configuring Suspension and Resumption with Yield and ConfigureAwait</span></span>
 <span data-ttu-id="c4ece-134">Çeşitli yöntemler, bir eşzamanlı yöntemin yürütülmesi üzerinde daha fazla denetim sağlar.</span><span class="sxs-lookup"><span data-stu-id="c4ece-134">Several methods provide more control over an asynchronous method’s execution.</span></span> <span data-ttu-id="c4ece-135">Örneğin, asynchronous <xref:System.Threading.Tasks.Task.Yield%2A?displayProperty=nameWithType> yöntemine bir verim noktası tanıtmak için yöntemi kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c4ece-135">For example, you can use the <xref:System.Threading.Tasks.Task.Yield%2A?displayProperty=nameWithType> method to introduce a yield point into the asynchronous method:</span></span>

```csharp
public class Task : …
{
    public static YieldAwaitable Yield();
    …
}
```

 <span data-ttu-id="c4ece-136">Bu, eşzamanlı olarak geçerli içeriğe yeniden deftere nakletmeye veya zamanlamaya eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="c4ece-136">This is equivalent to asynchronously posting or scheduling back to the current context.</span></span>

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

 <span data-ttu-id="c4ece-137">Ayrıca asynchronous yöntemi süspansiyon ve devamı üzerinde daha iyi kontrol için <xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=nameWithType> yöntemi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c4ece-137">You can also use the <xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=nameWithType> method for better control over suspension and resumption in an asynchronous method.</span></span>  <span data-ttu-id="c4ece-138">Daha önce de belirtildiği gibi, varsayılan olarak, geçerli bağlam bir eşzamanlı yöntem askıya alındı ve yakalanan bağlam devam ı üzerine asynchronous yöntemin devamını çağırmak için kullanılır yakalanır.</span><span class="sxs-lookup"><span data-stu-id="c4ece-138">As mentioned previously, by default, the current context is captured at the time an asynchronous  method is suspended, and that captured context is used to invoke the asynchronous  method’s continuation upon resumption.</span></span>  <span data-ttu-id="c4ece-139">Çoğu durumda, bu tam olarak istediğiniz davranıştır.</span><span class="sxs-lookup"><span data-stu-id="c4ece-139">In many cases, this is the exact behavior you want.</span></span>  <span data-ttu-id="c4ece-140">Diğer durumlarda, devam bağlamını önemsemeyebilirsiniz ve bu tür gönderileri özgün içeriğe geri döndürerek daha iyi performans elde edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c4ece-140">In other cases, you may not care about the continuation context, and you can achieve better performance by avoiding such posts back to the original context.</span></span>  <span data-ttu-id="c4ece-141">Bunu etkinleştirmek için, bekleme işlemini bağlamında yakalamamak ve devam ettirmek için değil, beklenen eşzamanlı işlemin tamamlandığı her yerde yürütmeye devam etmek için bu <xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=nameWithType> yöntemi kullanın:</span><span class="sxs-lookup"><span data-stu-id="c4ece-141">To enable this, use the <xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=nameWithType> method to inform the await operation not to capture and resume on the context, but to continue execution wherever the asynchronous operation that was being awaited completed:</span></span>

```csharp
await someTask.ConfigureAwait(continueOnCapturedContext:false);
```

## <a name="canceling-an-asynchronous-operation"></a><span data-ttu-id="c4ece-142">Eşkron İşlemi İptal Etme</span><span class="sxs-lookup"><span data-stu-id="c4ece-142">Canceling an Asynchronous Operation</span></span>
 <span data-ttu-id="c4ece-143">.NET Framework 4'ten başlayarak, iptali destekleyen TAP yöntemleri, iptal jetonu<xref:System.Threading.CancellationToken> (nesne) kabul eden en az bir aşırı yükleme sağlar.</span><span class="sxs-lookup"><span data-stu-id="c4ece-143">Starting with the .NET Framework 4, TAP methods that support cancellation provide at least one overload that accepts a cancellation token (<xref:System.Threading.CancellationToken> object).</span></span>

 <span data-ttu-id="c4ece-144">İptal belirteci, iptal jetonu kaynağı<xref:System.Threading.CancellationTokenSource> (nesne) aracılığıyla oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="c4ece-144">A cancellation token is created through a cancellation token source (<xref:System.Threading.CancellationTokenSource> object).</span></span>  <span data-ttu-id="c4ece-145">Kaynağın <xref:System.Threading.CancellationTokenSource.Token%2A> özelliği, kaynağın <xref:System.Threading.CancellationTokenSource.Cancel%2A> yöntemi çağrıldığında işaretlenecek iptal belirteci döndürür.</span><span class="sxs-lookup"><span data-stu-id="c4ece-145">The source’s <xref:System.Threading.CancellationTokenSource.Token%2A> property returns the cancellation token that will be signaled when the source’s <xref:System.Threading.CancellationTokenSource.Cancel%2A> method is called.</span></span>  <span data-ttu-id="c4ece-146">Örneğin, tek bir web sayfası indirmek istiyorsanız ve işlemi iptal etmek istiyorsanız, <xref:System.Threading.CancellationTokenSource> bir nesne oluşturursunuz, belirteciTAP yöntemine geçer <xref:System.Threading.CancellationTokenSource.Cancel%2A> ve işlemi iptal etmeye hazır olduğunuzda kaynağın yöntemini ararsınız:</span><span class="sxs-lookup"><span data-stu-id="c4ece-146">For example, if you want to download a single webpage and you want to be able to cancel the operation, you create a <xref:System.Threading.CancellationTokenSource> object, pass its token to the TAP method, and then call the source’s <xref:System.Threading.CancellationTokenSource.Cancel%2A> method when you're ready to cancel the operation:</span></span>

```csharp
var cts = new CancellationTokenSource();
string result = await DownloadStringAsync(url, cts.Token);
… // at some point later, potentially on another thread
cts.Cancel();
```

 <span data-ttu-id="c4ece-147">Birden çok eşzamanlı çağrıyı iptal etmek için, aynı belirteci tüm çağırmalara geçirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c4ece-147">To cancel multiple asynchronous invocations, you can pass the same token to all invocations:</span></span>

```csharp
var cts = new CancellationTokenSource();
    IList<string> results = await Task.WhenAll(from url in urls select DownloadStringAsync(url, cts.Token));
    // at some point later, potentially on another thread
    …
    cts.Cancel();
```

 <span data-ttu-id="c4ece-148">Veya, aynı belirteci seçici bir işlem alt kümesine geçirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c4ece-148">Or, you can pass the same token to a selective subset of operations:</span></span>

```csharp
var cts = new CancellationTokenSource();
    byte [] data = await DownloadDataAsync(url, cts.Token);
    await SaveToDiskAsync(outputPath, data, CancellationToken.None);
    … // at some point later, potentially on another thread
    cts.Cancel();
```

 <span data-ttu-id="c4ece-149">İptal talepleri herhangi bir iş parçacığı başlatılabilir.</span><span class="sxs-lookup"><span data-stu-id="c4ece-149">Cancellation requests may be initiated from any thread.</span></span>

 <span data-ttu-id="c4ece-150"><xref:System.Threading.CancellationToken.None%2A?displayProperty=nameWithType> İptal talebinde bulunulamayacağını belirtmek için değeri iptal jetonu kabul eden herhangi bir yönteme geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c4ece-150">You can pass the <xref:System.Threading.CancellationToken.None%2A?displayProperty=nameWithType> value to any method that accepts a cancellation token to indicate that cancellation will never be requested.</span></span>  <span data-ttu-id="c4ece-151">Bu özelliğin <xref:System.Threading.CancellationToken.CanBeCanceled%2A?displayProperty=nameWithType> dönmesine `false`neden olur ve çağrılan yöntem buna göre en iyi duruma getirebilir.</span><span class="sxs-lookup"><span data-stu-id="c4ece-151">This causes the <xref:System.Threading.CancellationToken.CanBeCanceled%2A?displayProperty=nameWithType> property to return `false`, and the called method can optimize accordingly.</span></span>  <span data-ttu-id="c4ece-152">Test amacıyla, belirteç zaten iptal edilmiş veya iptal edilemeyen bir durumda başlaması gerektiğini belirtmek için Boolean değerini kabul eden oluşturucuyu kullanarak anında iptal edilmiş bir iptal belirteci de geçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c4ece-152">For testing purposes, you can also pass in a pre-canceled cancellation token that is instantiated by using the constructor that accepts a Boolean value to indicate whether the token should start in an already-canceled or not-cancelable state.</span></span>

 <span data-ttu-id="c4ece-153">İptal için bu yaklaşımın birkaç avantajı vardır:</span><span class="sxs-lookup"><span data-stu-id="c4ece-153">This approach to cancellation has several advantages:</span></span>

- <span data-ttu-id="c4ece-154">Aynı iptal belirtecinizi herhangi bir sayıda ki eşzamanlı ve eşzamanlı işlemlere aktarabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c4ece-154">You can pass the same cancellation token to any number of asynchronous and synchronous operations.</span></span>

- <span data-ttu-id="c4ece-155">Aynı iptal isteği herhangi bir sayıda dinleyiciye çoğaltılabilir.</span><span class="sxs-lookup"><span data-stu-id="c4ece-155">The same cancellation request may be proliferated to any number of listeners.</span></span>

- <span data-ttu-id="c4ece-156">Eşzamanlı API'nin geliştiricisi, iptalin istenip istenmeyeceğini ve ne zaman yürürlüğe girebileceğini tam olarak kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="c4ece-156">The developer of the asynchronous API is in complete control of whether cancellation may be requested and when it may take effect.</span></span>

- <span data-ttu-id="c4ece-157">API'yi tüketen kod, iptal isteklerinin yayılacağı asynchronous davetlerini seçişle belirleyebilir.</span><span class="sxs-lookup"><span data-stu-id="c4ece-157">The code that consumes the API may selectively determine the asynchronous invocations that cancellation requests will be propagated to.</span></span>

## <a name="monitoring-progress"></a><span data-ttu-id="c4ece-158">İlerlemeyi İzleme</span><span class="sxs-lookup"><span data-stu-id="c4ece-158">Monitoring Progress</span></span>
 <span data-ttu-id="c4ece-159">Bazı eşzamanlı yöntemler, asynchronous yöntemine aktarılan ilerleme arabirimi aracılığıyla ilerlemeyi ortaya çıkarır.</span><span class="sxs-lookup"><span data-stu-id="c4ece-159">Some asynchronous methods expose progress through a progress interface passed into the asynchronous method.</span></span>  <span data-ttu-id="c4ece-160">Örneğin, eş senkronize bir metin dizesini karşıdan yükleyen ve yol boyunca şimdiye kadar tamamlanan karşıdan yükleme yüzdesini içeren ilerleme güncelleştirmelerini yükselten bir işlev düşünün.</span><span class="sxs-lookup"><span data-stu-id="c4ece-160">For example, consider a function which asynchronously downloads a string of text, and along the way raises progress updates that include the percentage of the download that has completed thus far.</span></span>  <span data-ttu-id="c4ece-161">Böyle bir yöntem bir Windows Presentation Foundation (WPF) uygulamasında aşağıdaki gibi tüketilebilir:</span><span class="sxs-lookup"><span data-stu-id="c4ece-161">Such a method could be consumed in a Windows Presentation Foundation (WPF) application as follows:</span></span>

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
## <a name="using-the-built-in-task-based-combinators"></a><span data-ttu-id="c4ece-162">Yerleşik Görev Tabanlı Kombinatörleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="c4ece-162">Using the Built-in Task-based Combinators</span></span>
 <span data-ttu-id="c4ece-163">Ad <xref:System.Threading.Tasks> alanı, görevleri oluşturmak ve çalışmak için çeşitli yöntemler içerir.</span><span class="sxs-lookup"><span data-stu-id="c4ece-163">The <xref:System.Threading.Tasks> namespace includes several methods for composing and working with tasks.</span></span>

### <a name="taskrun"></a><span data-ttu-id="c4ece-164">Görev.Çalıştır</span><span class="sxs-lookup"><span data-stu-id="c4ece-164">Task.Run</span></span>
 <span data-ttu-id="c4ece-165">Sınıf, <xref:System.Threading.Tasks.Task> örneğin <xref:System.Threading.Tasks.Task.Run%2A> iş parçacığı havuzunda <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601> çalışmayı kolayca boşaltmanızı sağlayan çeşitli yöntemler içerir:</span><span class="sxs-lookup"><span data-stu-id="c4ece-165">The <xref:System.Threading.Tasks.Task> class includes several <xref:System.Threading.Tasks.Task.Run%2A> methods that let you easily offload work as a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> to the thread pool, for example:</span></span>

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

 <span data-ttu-id="c4ece-166">Aşırı yükleme <xref:System.Threading.Tasks.Task.Run%2A> gibi bu yöntemlerden <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> bazıları yöntem için kısaltma olarak bulunur. <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="c4ece-166">Some of these <xref:System.Threading.Tasks.Task.Run%2A> methods, such as the <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType> overload, exist as shorthand for the <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> method.</span></span>  <span data-ttu-id="c4ece-167">Diğer aşırı yüklemeler, <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType>örneğin, boşaltılmış iş içinde beklemeyi kullanmanıza olanak sağlar:</span><span class="sxs-lookup"><span data-stu-id="c4ece-167">Other overloads, such as <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType>, enable you to use await within the offloaded work, for example:</span></span>

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

 <span data-ttu-id="c4ece-168">Bu tür aşırı yüklemeler, <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> Görev Paralel Kitaplığı'ndaki <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> uzantı yöntemiyle birlikte yöntemi kullanmaya mantıksal olarak eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="c4ece-168">Such overloads are logically equivalent to using the <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> method in conjunction with the <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> extension method in the Task Parallel Library.</span></span>

### <a name="taskfromresult"></a><span data-ttu-id="c4ece-169">Görev.Kaynak</span><span class="sxs-lookup"><span data-stu-id="c4ece-169">Task.FromResult</span></span>
 <span data-ttu-id="c4ece-170">Verilerin <xref:System.Threading.Tasks.Task.FromResult%2A> zaten mevcut olabileceği ve görev döndürme yönteminden döndürülmesi gereken senaryolarda yöntemi <xref:System.Threading.Tasks.Task%601>kullanın:</span><span class="sxs-lookup"><span data-stu-id="c4ece-170">Use the <xref:System.Threading.Tasks.Task.FromResult%2A> method in scenarios where data may already be available and just needs to be returned from a task-returning method lifted into a <xref:System.Threading.Tasks.Task%601>:</span></span>

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

### <a name="taskwhenall"></a><span data-ttu-id="c4ece-171">Task.WhenAll</span><span class="sxs-lookup"><span data-stu-id="c4ece-171">Task.WhenAll</span></span>
 <span data-ttu-id="c4ece-172">Görev <xref:System.Threading.Tasks.Task.WhenAll%2A> olarak temsil edilen birden çok eşzamanlı işlemi eş senkronize olarak beklemek için yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="c4ece-172">Use the <xref:System.Threading.Tasks.Task.WhenAll%2A> method to asynchronously wait on multiple asynchronous operations that are represented as tasks.</span></span>  <span data-ttu-id="c4ece-173">Yöntem, genel olmayan bir görev kümesini veya tek düze olmayan genel görevleri (örneğin, birden çok geçersiz döndüren işlemi bekleyen veya her değerin farklı bir türü olabileceği birden çok değer döndüren yöntemi bekleyen) ve tek tip genel `TResult`görevleri (eşzamanlı olarak birden çok dönen yöntemleri beklemek gibi) destekleyen birden çok fazla yüklemeye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="c4ece-173">The method has multiple overloads that support a set of non-generic tasks or a non-uniform set of generic tasks (for example, asynchronously waiting for multiple void-returning operations, or asynchronously waiting for multiple value-returning methods where each value may have a different type) and to support a uniform set of generic tasks (such as asynchronously waiting for multiple `TResult`-returning methods).</span></span>

 <span data-ttu-id="c4ece-174">Birkaç müşteriye e-posta iletisi göndermek istediğinizi varsayalım.</span><span class="sxs-lookup"><span data-stu-id="c4ece-174">Let's say you want to send email messages to several customers.</span></span> <span data-ttu-id="c4ece-175">İletileri göndermenin çakışmasını sağlayabilirsiniz, böylece bir sonraki iletiyi göndermeden önce bir iletinin tamamlanmasını beklemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="c4ece-175">You can overlap sending the messages so you're not waiting for one message to complete before sending the next.</span></span> <span data-ttu-id="c4ece-176">Ayrıca, gönderme işlemlerinin ne zaman tamamlandığını ve herhangi bir hata nın oluşup oluşmadığını da öğrenebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c4ece-176">You can also find out when the send operations have completed and whether any errors have occurred:</span></span>

```csharp
IEnumerable<Task> asyncOps = from addr in addrs select SendMailAsync(addr);
await Task.WhenAll(asyncOps);
```

 <span data-ttu-id="c4ece-177">Bu kod, oluşabilecek özel durumları açıkça işlemez, ancak özel durumlar `await` <xref:System.Threading.Tasks.Task.WhenAll%2A>' dan gelen 'den kaynaklanan görevin dışına yayılmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="c4ece-177">This code doesn't explicitly handle exceptions that may occur, but lets exceptions propagate out of the `await` on the resulting task from <xref:System.Threading.Tasks.Task.WhenAll%2A>.</span></span>  <span data-ttu-id="c4ece-178">Özel durumları işlemek için aşağıdaki gibi kod kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c4ece-178">To handle the exceptions, you can use code such as the following:</span></span>

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

 <span data-ttu-id="c4ece-179">Bu durumda, herhangi bir eşyokolün işlemi başarısız olursa, tüm <xref:System.AggregateException> özel durumlar <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task.WhenAll%2A> yöntemden döndürülen depolanan bir özel durum olarak birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="c4ece-179">In this case, if any asynchronous operation fails, all the exceptions will be consolidated in an <xref:System.AggregateException> exception, which is stored in the <xref:System.Threading.Tasks.Task> that is returned from the <xref:System.Threading.Tasks.Task.WhenAll%2A> method.</span></span>  <span data-ttu-id="c4ece-180">Ancak, bu özel durumlardan yalnızca biri `await` anahtar kelime tarafından yayılır.</span><span class="sxs-lookup"><span data-stu-id="c4ece-180">However, only one of those exceptions is propagated by the `await` keyword.</span></span>  <span data-ttu-id="c4ece-181">Tüm özel durumları incelemek istiyorsanız, önceki kodu aşağıdaki gibi yeniden yazabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c4ece-181">If you want to examine all the exceptions, you can rewrite the previous code as follows:</span></span>

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

 <span data-ttu-id="c4ece-182">Web'den eşzamanlı olarak birden fazla dosya indirme örneğini ele alalım.</span><span class="sxs-lookup"><span data-stu-id="c4ece-182">Let's consider an example of downloading multiple files from the web asynchronously.</span></span>  <span data-ttu-id="c4ece-183">Bu durumda, tüm eşzamanlı işlemlerhomojen sonuç türlerine sahiptir ve sonuçlara erişmek kolaydır:</span><span class="sxs-lookup"><span data-stu-id="c4ece-183">In this case, all the asynchronous operations have homogeneous result types, and it's easy to access the results:</span></span>

```csharp
string [] pages = await Task.WhenAll(
    from url in urls select DownloadStringAsync(url));
```

 <span data-ttu-id="c4ece-184">Önceki geçersiz döndürme senaryosunda tartıştığımız aynı özel durum işleme tekniklerini kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c4ece-184">You can use the same exception-handling techniques we discussed in the previous void-returning scenario:</span></span>

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

### <a name="taskwhenany"></a><span data-ttu-id="c4ece-185">Task.WhenAny</span><span class="sxs-lookup"><span data-stu-id="c4ece-185">Task.WhenAny</span></span>
 <span data-ttu-id="c4ece-186"><xref:System.Threading.Tasks.Task.WhenAny%2A> Tamamlanmagörevi olarak temsil edilen birden çok eşzamanlı işlemden yalnızca birini beklemek için yöntemi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c4ece-186">You can use the <xref:System.Threading.Tasks.Task.WhenAny%2A> method to asynchronously wait for just one of multiple asynchronous operations represented as tasks to complete.</span></span>  <span data-ttu-id="c4ece-187">Bu yöntem dört birincil kullanım örnekleri ne hizmet vermektedir:</span><span class="sxs-lookup"><span data-stu-id="c4ece-187">This method serves four primary use cases:</span></span>

- <span data-ttu-id="c4ece-188">Artıklık: Bir işlemi birden çok kez gerçekleştirmek ve ilk tamamlananı seçmek (örneğin, tek bir sonuç üretecek birden çok hisse senedi teklifi web hizmetleriyle iletişim kurmak ve en hızlı tamamlananı seçmek).</span><span class="sxs-lookup"><span data-stu-id="c4ece-188">Redundancy:  Performing an operation multiple times and selecting the one that completes first (for example, contacting multiple stock quote web services that will produce a single result and selecting the one that completes the fastest).</span></span>

- <span data-ttu-id="c4ece-189">Ayrılma: Birden çok işlemi başlatmak ve hepsinin tamamlanmasını beklemek, ancak tamamlandıkça işleme.</span><span class="sxs-lookup"><span data-stu-id="c4ece-189">Interleaving:  Launching multiple operations and waiting for all of them to complete, but processing them as they complete.</span></span>

- <span data-ttu-id="c4ece-190">Azaltma: Diğerleri tamamlandıkça ek işlemlerin başlamasına izin verme.</span><span class="sxs-lookup"><span data-stu-id="c4ece-190">Throttling:  Allowing additional operations to begin as others complete.</span></span>  <span data-ttu-id="c4ece-191">Bu, ayrılma senaryosunun bir uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="c4ece-191">This is an extension of the interleaving scenario.</span></span>

- <span data-ttu-id="c4ece-192">Erken kurtarma: Örneğin, görev t1 tarafından temsil edilen bir <xref:System.Threading.Tasks.Task.WhenAny%2A> işlem başka bir görev t2 ile <xref:System.Threading.Tasks.Task.WhenAny%2A> bir görev gruplandırılabilir ve görev üzerinde bekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c4ece-192">Early bailout:  For example, an operation represented by task t1 can be grouped in a <xref:System.Threading.Tasks.Task.WhenAny%2A> task with another task t2, and you can wait on the <xref:System.Threading.Tasks.Task.WhenAny%2A> task.</span></span> <span data-ttu-id="c4ece-193">Görev t2 bir zaman-out veya iptal veya t1 <xref:System.Threading.Tasks.Task.WhenAny%2A> tamamlanmadan önce görev tamamlanmasına neden başka bir sinyal temsil edebilir.</span><span class="sxs-lookup"><span data-stu-id="c4ece-193">Task t2 could represent a time-out, or cancellation, or some other signal that causes the <xref:System.Threading.Tasks.Task.WhenAny%2A> task to complete before t1 completes.</span></span>

#### <a name="redundancy"></a><span data-ttu-id="c4ece-194">Yedeklilik</span><span class="sxs-lookup"><span data-stu-id="c4ece-194">Redundancy</span></span>
 <span data-ttu-id="c4ece-195">Hisse senedi alıp almayacağınız konusunda karar vermek istediğiniz bir durumu düşünün.</span><span class="sxs-lookup"><span data-stu-id="c4ece-195">Consider a case where you want to make a decision about whether to buy a stock.</span></span>  <span data-ttu-id="c4ece-196">Güvendiğiniz birkaç hisse senedi tavsiyesi web hizmetleri vardır, ancak günlük yüke bağlı olarak, her hizmet farklı zamanlarda yavaş sona erebilir.</span><span class="sxs-lookup"><span data-stu-id="c4ece-196">There are several stock recommendation web services that you trust, but depending on daily load, each service can end up being slow at different times.</span></span>  <span data-ttu-id="c4ece-197">Herhangi bir <xref:System.Threading.Tasks.Task.WhenAny%2A> işlem tamamlandığında bildirim almak için yöntemi kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c4ece-197">You can use the <xref:System.Threading.Tasks.Task.WhenAny%2A> method to receive a notification when any operation completes:</span></span>

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

 <span data-ttu-id="c4ece-198">Başarıyla tamamlanan tüm görevlerin paketlenmemiş sonuçlarını <xref:System.Threading.Tasks.Task.WhenAll%2A>döndüren, tamamlanan görevi <xref:System.Threading.Tasks.Task.WhenAny%2A> döndürür.</span><span class="sxs-lookup"><span data-stu-id="c4ece-198">Unlike <xref:System.Threading.Tasks.Task.WhenAll%2A>, which returns the unwrapped results of all tasks that completed successfully, <xref:System.Threading.Tasks.Task.WhenAny%2A> returns the task that completed.</span></span> <span data-ttu-id="c4ece-199">Bir görev başarısız olursa, başarısız olduğunu bilmek önemlidir ve bir görev başarılı olursa, iade değerinin hangi görevle ilişkili olduğunu bilmek önemlidir.</span><span class="sxs-lookup"><span data-stu-id="c4ece-199">If a task fails, it’s important to know that it failed, and if a task succeeds, it’s important to know which task the return value is associated with.</span></span>  <span data-ttu-id="c4ece-200">Bu nedenle, döndürülen görevin sonucuna erişmeniz veya bu örneğin gösterdiği gibi daha fazla beklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="c4ece-200">Therefore, you need to access the result of the returned task, or further await it, as  this example shows.</span></span>

 <span data-ttu-id="c4ece-201">Olduğu <xref:System.Threading.Tasks.Task.WhenAll%2A>gibi, özel durumlara uyum sağlamak gerekir.</span><span class="sxs-lookup"><span data-stu-id="c4ece-201">As with <xref:System.Threading.Tasks.Task.WhenAll%2A>, you have to be able to accommodate exceptions.</span></span>  <span data-ttu-id="c4ece-202">Tamamlanan görevi geri aldığınızdan, döndürülen görevi hataların yayılmasını ve `try/catch` uygun şekilde yayılmasını bekleyebilirsiniz; örneğin:</span><span class="sxs-lookup"><span data-stu-id="c4ece-202">Because you receive the completed task back, you can await the returned task to have errors propagated, and `try/catch` them appropriately; for example:</span></span>

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

 <span data-ttu-id="c4ece-203">Ayrıca, ilk görev başarıyla tamamlaşsa bile, sonraki görevler başarısız olabilir.</span><span class="sxs-lookup"><span data-stu-id="c4ece-203">Additionally, even if a first task completes successfully, subsequent tasks may fail.</span></span>  <span data-ttu-id="c4ece-204">Bu noktada, özel durumlarla başa çıkmak için çeşitli seçenekleriniz vardır: Başlatılan tüm görevler tamamlanana <xref:System.Threading.Tasks.Task.WhenAll%2A> kadar bekleyebilir, bu durumda yöntemi kullanabilirsiniz veya tüm özel durumların önemli olduğuna ve günlüğe kaydedilmesi gerektiğine karar verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c4ece-204">At this point, you have several options for dealing with exceptions:  You can wait until all the launched tasks have completed, in which case you can use the <xref:System.Threading.Tasks.Task.WhenAll%2A> method, or you can decide that all exceptions are important and must be logged.</span></span>  <span data-ttu-id="c4ece-205">Bunun için, görevler eşeşitle tamamlandığında bildirim almak için devamları kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c4ece-205">For this, you can use continuations to receive a notification when tasks have completed asynchronously:</span></span>

```csharp
foreach(Task recommendation in recommendations)
{
    var ignored = recommendation.ContinueWith(
        t => { if (t.IsFaulted) Log(t.Exception); });
}
```

 <span data-ttu-id="c4ece-206">veya:</span><span class="sxs-lookup"><span data-stu-id="c4ece-206">or:</span></span>

```csharp
foreach(Task recommendation in recommendations)
{
    var ignored = recommendation.ContinueWith(
        t => Log(t.Exception), TaskContinuationOptions.OnlyOnFaulted);
}
```

 <span data-ttu-id="c4ece-207">hatta:</span><span class="sxs-lookup"><span data-stu-id="c4ece-207">or even:</span></span>

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

 <span data-ttu-id="c4ece-208">Son olarak, kalan tüm işlemleri iptal etmek isteyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c4ece-208">Finally, you may want to cancel all the remaining operations:</span></span>

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

#### <a name="interleaving"></a><span data-ttu-id="c4ece-209">Aralaması</span><span class="sxs-lookup"><span data-stu-id="c4ece-209">Interleaving</span></span>
 <span data-ttu-id="c4ece-210">Web'den resim indirdiğiniz ve her görüntüyü işlediğiniz (örneğin, görüntüyü ui denetimine ekleme) bir durum düşünün.</span><span class="sxs-lookup"><span data-stu-id="c4ece-210">Consider a case where you're downloading images from the web and processing each image (for example, adding the image to a UI control).</span></span>  <span data-ttu-id="c4ece-211">İşlemi UI iş parçacığıüzerinde sırayla yapmanız gerekir, ancak görüntüleri mümkün olduğunca aynı anda indirmek istersiniz.</span><span class="sxs-lookup"><span data-stu-id="c4ece-211">You have to do the processing sequentially on the UI thread, but you want to download the images as concurrently as possible.</span></span> <span data-ttu-id="c4ece-212">Ayrıca, görüntüleri indirilene kadar UI'ye eklemeyi ertelemek istemezsiniz— tamamlanırken eklemek istiyorsunuz:</span><span class="sxs-lookup"><span data-stu-id="c4ece-212">Also, you don’t want to hold up adding the images to the UI until they’re all downloaded—you want to add them as they complete:</span></span>

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

 <span data-ttu-id="c4ece-213">İndirilen görüntülerin üzerinde <xref:System.Threading.ThreadPool> hesaplama açısından yoğun işlem içeren bir senaryoya ara ayrılma da uygulayabilirsiniz; örneğin:</span><span class="sxs-lookup"><span data-stu-id="c4ece-213">You can also apply interleaving to a scenario that involves computationally intensive processing on the <xref:System.Threading.ThreadPool> of the downloaded images; for example:</span></span>

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

#### <a name="throttling"></a><span data-ttu-id="c4ece-214">Azaltma</span><span class="sxs-lookup"><span data-stu-id="c4ece-214">Throttling</span></span>
 <span data-ttu-id="c4ece-215">Kullanıcının o kadar çok resim indiriyor olması ve indirmelerin azaltılması gerektiği dışında, ara ayrılma örneğini göz önünde bulundurun; örneğin, yalnızca belirli sayıda indirmenin aynı anda gerçekleşmesini istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="c4ece-215">Consider the interleaving example, except that the user is downloading so many images that the downloads have to be throttled; for example, you want only a specific number of downloads to happen concurrently.</span></span> <span data-ttu-id="c4ece-216">Bunu başarmak için, eşzamanlı işlemlerin bir alt kümesini başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c4ece-216">To achieve this, you can start a subset of the asynchronous operations.</span></span>  <span data-ttu-id="c4ece-217">İşlemler tamamlandıkça, onların yerini almak için ek işlemler başlatabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c4ece-217">As operations complete, you can start additional operations to take their place:</span></span>

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

#### <a name="early-bailout"></a><span data-ttu-id="c4ece-218">Erken Kurtarma</span><span class="sxs-lookup"><span data-stu-id="c4ece-218">Early Bailout</span></span>
 <span data-ttu-id="c4ece-219">Bir kullanıcının iptal isteğine aynı anda yanıt verirken bir işlemin tamamlanmasını eş zamanlı olarak beklediğiniz göz önünde bulundurun (örneğin, kullanıcı bir iptal düğmesini tıklattı).</span><span class="sxs-lookup"><span data-stu-id="c4ece-219">Consider that you're waiting asynchronously for an operation to complete while simultaneously responding to a user’s cancellation request (for example, the user clicked a cancel button).</span></span> <span data-ttu-id="c4ece-220">Aşağıdaki kod bu senaryoyu göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="c4ece-220">The following code illustrates this scenario:</span></span>

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

 <span data-ttu-id="c4ece-221">Bu uygulama, siz ödemeye karar verir vermez kullanıcı arabirimini yeniden etkinleştirir, ancak temel asenkron işlemleri iptal etmez.</span><span class="sxs-lookup"><span data-stu-id="c4ece-221">This implementation re-enables the user interface as soon as you decide to bail out, but doesn't cancel the underlying asynchronous operations.</span></span>  <span data-ttu-id="c4ece-222">Başka bir alternatif, kurtarma kararı aldığınızda bekleyen işlemleri iptal etmek, ancak iptal isteği nedeniyle erken sona ermesi nedeniyle işlemler gerçekten tamamlanana kadar kullanıcı arabirimini yeniden kurmamak olacaktır:</span><span class="sxs-lookup"><span data-stu-id="c4ece-222">Another alternative would be to cancel the pending operations when you decide to bail out, but not reestablish the user interface until the operations actually complete, potentially due to ending early due to the cancellation request:</span></span>

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

 <span data-ttu-id="c4ece-223">Erken kurtarma başka bir <xref:System.Threading.Tasks.Task.WhenAny%2A> örnek, bir <xref:System.Threading.Tasks.Task.Delay%2A> sonraki bölümde ele alındığı gibi, yöntem ile birlikte yöntemi kullanarak içerir.</span><span class="sxs-lookup"><span data-stu-id="c4ece-223">Another example of early bailout involves using the <xref:System.Threading.Tasks.Task.WhenAny%2A> method in conjunction with the <xref:System.Threading.Tasks.Task.Delay%2A> method, as discussed in the next section.</span></span>

### <a name="taskdelay"></a><span data-ttu-id="c4ece-224">Task.Delay</span><span class="sxs-lookup"><span data-stu-id="c4ece-224">Task.Delay</span></span>
 <span data-ttu-id="c4ece-225">Asynchronous <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> yöntemyürütme içine duraklatma tanıtmak için yöntemi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c4ece-225">You can use the <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> method to introduce pauses into an asynchronous method’s execution.</span></span>  <span data-ttu-id="c4ece-226">Bu, yoklama döngüleri oluşturma ve kullanıcı girişinin işlenmesini önceden belirlenmiş bir süre için geciktirme de dahil olmak üzere birçok işlevsellik türü için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="c4ece-226">This is useful for many kinds of functionality, including building polling loops and delaying the handling of user input for a predetermined period of time.</span></span>  <span data-ttu-id="c4ece-227">Yöntem, <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> bekleme lerde zaman <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> çıkışları uygulamak için birlikte de yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="c4ece-227">The <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> method can also be useful in combination with <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> for implementing time-outs on awaits.</span></span>

 <span data-ttu-id="c4ece-228">Daha büyük bir eşzamanlı işlemin parçası olan bir görevin (örneğin, ASP.NET bir web hizmetinin) tamamlanması çok uzun sürerse, genel işlem özellikle tamamlanmamışsa zarar görebilir.</span><span class="sxs-lookup"><span data-stu-id="c4ece-228">If a task that’s part of a larger asynchronous operation (for example, an ASP.NET web service) takes too long to complete, the overall operation could suffer, especially if it fails to ever complete.</span></span>  <span data-ttu-id="c4ece-229">Bu nedenle, bir eşzamanlı işlemi beklerken zaman dışarı edebilmek önemlidir.</span><span class="sxs-lookup"><span data-stu-id="c4ece-229">For this reason, it’s important to be able to time out when waiting on an asynchronous operation.</span></span>  <span data-ttu-id="c4ece-230">Senkron <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Task.WaitAll%2A?displayProperty=nameWithType>ve <xref:System.Threading.Tasks.Task.WaitAny%2A?displayProperty=nameWithType> yöntemler zaman dışarı değerleri kabul, <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType> / <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> ancak karşılık gelen <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> / <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> ve daha önce belirtilen yöntemler yok.</span><span class="sxs-lookup"><span data-stu-id="c4ece-230">The synchronous <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Task.WaitAll%2A?displayProperty=nameWithType>, and <xref:System.Threading.Tasks.Task.WaitAny%2A?displayProperty=nameWithType> methods accept time-out values, but the corresponding <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType>/<xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> and the previously mentioned <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>/<xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> methods do not.</span></span>  <span data-ttu-id="c4ece-231">Bunun yerine, <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> bir <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> zaman-out uygulamak için kullanabilirsiniz ve birlikte.</span><span class="sxs-lookup"><span data-stu-id="c4ece-231">Instead, you can use <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> in combination to implement a time-out.</span></span>

 <span data-ttu-id="c4ece-232">Örneğin, Kullanıcı Arabirimi uygulamanızda, bir resim indirmek ve görüntü indirirken Kullanıcı Arabirimi'ni devre dışı bırakmak istediğinizi varsayalım.</span><span class="sxs-lookup"><span data-stu-id="c4ece-232">For example, in your UI application, let's say that you want to download an image and disable the UI while the image is downloading.</span></span> <span data-ttu-id="c4ece-233">Ancak, indirme çok uzun sürerse, UI'yi yeniden etkinleştirmek ve karşıdan yüklemeyi atmak istiyorsunuz:</span><span class="sxs-lookup"><span data-stu-id="c4ece-233">However, if the download takes too long, you want to re-enable the UI and discard the download:</span></span>

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

 <span data-ttu-id="c4ece-234">Aynı durum birden çok indirme <xref:System.Threading.Tasks.Task.WhenAll%2A> için de geçerlidir, çünkü bir görevi döndürür:</span><span class="sxs-lookup"><span data-stu-id="c4ece-234">The same applies to multiple downloads, because <xref:System.Threading.Tasks.Task.WhenAll%2A> returns a task:</span></span>

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

## <a name="building-task-based-combinators"></a><span data-ttu-id="c4ece-235">Görev Tabanlı Kombinatörler Oluşturma</span><span class="sxs-lookup"><span data-stu-id="c4ece-235">Building Task-based Combinators</span></span>
 <span data-ttu-id="c4ece-236">Bir görev tamamen bir eşzamanlı işlemi temsil edebilir ve operasyona katılmak, sonuçlarını almak ve benzeri için senkron ve eşzamanlı yetenekler sağlayabildiği için, görevleri oluşturan kombinatörlerin yararlı kitaplıklarını oluşturabilirsiniz daha büyük desenler oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c4ece-236">Because a task is able to completely represent an asynchronous operation and provide synchronous and asynchronous capabilities for joining with the operation, retrieving its results, and so on, you can build useful libraries of combinators that compose tasks to build larger patterns.</span></span>  <span data-ttu-id="c4ece-237">Önceki bölümde ele alındığı gibi, .NET Framework birkaç yerleşik kombinör içerir, ancak kendi de oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c4ece-237">As discussed in the previous section, the .NET Framework includes several built-in combinators, but you can also build your own.</span></span> <span data-ttu-id="c4ece-238">Aşağıdaki bölümlerde potansiyel kombinatör yöntemleri ve türleri birkaç örnek sağlar.</span><span class="sxs-lookup"><span data-stu-id="c4ece-238">The following sections provide several examples of potential combinator methods and types.</span></span>

### <a name="retryonfault"></a><span data-ttu-id="c4ece-239">RetryOnFault</span><span class="sxs-lookup"><span data-stu-id="c4ece-239">RetryOnFault</span></span>
 <span data-ttu-id="c4ece-240">Birçok durumda, önceki bir deneme başarısız olursa bir işlemi yeniden denemek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c4ece-240">In many situations, you may want to retry an operation if a previous attempt fails.</span></span>  <span data-ttu-id="c4ece-241">Senkron kod için, bunu gerçekleştirmek için aşağıdaki `RetryOnFault` örnekte olduğu gibi bir yardımcı yöntemi oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c4ece-241">For synchronous code, you might build a helper method such as `RetryOnFault` in the following example to accomplish this:</span></span>

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

 <span data-ttu-id="c4ece-242">TAP ile uygulanan eşzamanlı işlemler için hemen hemen aynı yardımcı yöntemi oluşturabilir ve böylece görevleri döndürebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c4ece-242">You can build an almost identical helper method for asynchronous operations that are implemented with TAP and thus return tasks:</span></span>

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

 <span data-ttu-id="c4ece-243">Daha sonra bu kombinatörün uygulamanın mantığına yeniden denemeleri kodlamak için kullanabilirsiniz; örneğin:</span><span class="sxs-lookup"><span data-stu-id="c4ece-243">You can then use this combinator to encode retries into the application’s logic; for example:</span></span>

```csharp
// Download the URL, trying up to three times in case of failure
string pageContents = await RetryOnFault(
    () => DownloadStringAsync(url), 3);
```

 <span data-ttu-id="c4ece-244">İşlevi daha `RetryOnFault` da genişletebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c4ece-244">You could extend the `RetryOnFault` function further.</span></span> <span data-ttu-id="c4ece-245">Örneğin, işlev, işlemi `Func<Task>` yeniden ne zaman deneyeceğini belirlemek için yeniden denemeler arasında çağrılacak başka bir işlevi kabul edebilir; örneğin:</span><span class="sxs-lookup"><span data-stu-id="c4ece-245">For example, the function could accept another `Func<Task>` that will be invoked between retries to determine when to try the operation again; for example:</span></span>

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

 <span data-ttu-id="c4ece-246">Daha sonra işlemi yeniden denemeden önce bir saniye beklemek için aşağıdaki işlevi kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c4ece-246">You could then use the function as follows to wait for a second before retrying the operation:</span></span>

```csharp
// Download the URL, trying up to three times in case of failure,
// and delaying for a second between retries
string pageContents = await RetryOnFault(
    () => DownloadStringAsync(url), 3, () => Task.Delay(1000));
```

### <a name="needonlyone"></a><span data-ttu-id="c4ece-247">NeedOnlyOne</span><span class="sxs-lookup"><span data-stu-id="c4ece-247">NeedOnlyOne</span></span>
 <span data-ttu-id="c4ece-248">Bazen, bir işlemin gecikmesini ve başarı şansını artırmak için artıklılılılılılılılığınızdan yararlanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c4ece-248">Sometimes, you can take advantage of redundancy to improve an operation’s latency and chances for success.</span></span>  <span data-ttu-id="c4ece-249">Hisse senedi fiyatları sağlayan birden çok web hizmetini düşünün, ancak günün çeşitli saatlerinde, her hizmet farklı kalite ve yanıt süreleri sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="c4ece-249">Consider multiple web services that provide stock quotes, but at various times of the day, each service may provide different levels of quality and response times.</span></span>  <span data-ttu-id="c4ece-250">Bu dalgalanmalarla başa çıkmak için tüm web hizmetlerine istekler verebilir ve birinden yanıt alır almaz kalan istekleri iptal edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c4ece-250">To deal with these fluctuations, you may issue requests to all the web services, and as soon as you get a response from one, cancel the remaining requests.</span></span>  <span data-ttu-id="c4ece-251">Birden çok işlem başlatma, herhangi bir bekleyen ve daha sonra geri kalanını iptal bu ortak desen uygulamak için daha kolay hale getirmek için bir yardımcı işlevi uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c4ece-251">You can implement a helper function to make it easier to implement this common pattern of launching multiple operations, waiting for any, and then canceling the rest.</span></span> <span data-ttu-id="c4ece-252">Aşağıdaki `NeedOnlyOne` örnekteki işlev bu senaryoyu göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="c4ece-252">The `NeedOnlyOne` function in the following example illustrates this scenario:</span></span>

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

 <span data-ttu-id="c4ece-253">Daha sonra aşağıdaki gibi bu işlevi kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c4ece-253">You can then use this function as follows:</span></span>

```csharp
double currentPrice = await NeedOnlyOne(
    ct => GetCurrentPriceFromServer1Async("msft", ct),
    ct => GetCurrentPriceFromServer2Async("msft", ct),
    ct => GetCurrentPriceFromServer3Async("msft", ct));
```

### <a name="interleaved-operations"></a><span data-ttu-id="c4ece-254">Ara İşlemler</span><span class="sxs-lookup"><span data-stu-id="c4ece-254">Interleaved Operations</span></span>
 <span data-ttu-id="c4ece-255">Çok büyük görev kümeleriyle <xref:System.Threading.Tasks.Task.WhenAny%2A> çalışırken, ayrılmalar arası senaryoyu desteklemek için yöntemi kullanmada olası bir performans sorunu vardır.</span><span class="sxs-lookup"><span data-stu-id="c4ece-255">There is a potential performance problem with using the <xref:System.Threading.Tasks.Task.WhenAny%2A> method to support an interleaving scenario when you're working with very large sets of tasks.</span></span> <span data-ttu-id="c4ece-256">Her arama, her göreve kaydolarak devam edilmesiyle <xref:System.Threading.Tasks.Task.WhenAny%2A> sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="c4ece-256">Every call to <xref:System.Threading.Tasks.Task.WhenAny%2A> results in a continuation being registered with each task.</span></span> <span data-ttu-id="c4ece-257">N görev sayısı için bu, ayrılma işleminin ömrü boyunca oluşturulan O(N<sup>2)</sup>devamlarına neden olur.</span><span class="sxs-lookup"><span data-stu-id="c4ece-257">For N number of tasks, this results in O(N<sup>2</sup>) continuations created over the lifetime of the interleaving operation.</span></span> <span data-ttu-id="c4ece-258">Büyük bir görev kümesiyle çalışıyorsanız, performans sorununu gidermek için`Interleaved` bir kombinatör (aşağıdaki örnekte) kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c4ece-258">If you're working with a large set of tasks, you can use a combinator (`Interleaved` in the following example) to address the performance issue:</span></span>

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

 <span data-ttu-id="c4ece-259">Daha sonra, görevlerin sonuçlarını tamamlanırken işlemek için kombinatörü kullanabilirsiniz; örneğin:</span><span class="sxs-lookup"><span data-stu-id="c4ece-259">You can then use the combinator to process the results of tasks as they complete; for example:</span></span>

```csharp
IEnumerable<Task<int>> tasks = ...;
foreach(var task in Interleaved(tasks))
{
    int result = await task;
    …
}
```

### <a name="whenallorfirstexception"></a><span data-ttu-id="c4ece-260">WhenallOrFirstException</span><span class="sxs-lookup"><span data-stu-id="c4ece-260">WhenAllOrFirstException</span></span>
 <span data-ttu-id="c4ece-261">Belirli dağılım/toplama senaryolarında, bu hatalardan biri hatalar olmadığı sürece, bir kümedeki tüm görevleri beklemek isteyebilirsiniz ve bu durumda özel durum oluşur oluşmaz beklemeyi durdurmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c4ece-261">In certain scatter/gather scenarios, you might want to wait for all tasks in a set, unless one of them faults, in which case you want to stop waiting as soon as the exception occurs.</span></span>  <span data-ttu-id="c4ece-262">Bunu aşağıdaki örnekte olduğu gibi `WhenAllOrFirstException` bir kombinatör yöntemiyle gerçekleştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c4ece-262">You can accomplish that with a combinator method such as `WhenAllOrFirstException` in the following example:</span></span>

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

## <a name="building-task-based-data-structures"></a><span data-ttu-id="c4ece-263">Görev Tabanlı Veri Yapıları Oluşturma</span><span class="sxs-lookup"><span data-stu-id="c4ece-263">Building Task-based Data Structures</span></span>
 <span data-ttu-id="c4ece-264">Özel görev tabanlı kombinleyiciler oluşturma yeteneğine ek olarak, <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601> içinde bir veri yapısına sahip ve bu da hem bir eşzamanlı işlemin sonuçlarını hem de onunla birleştirilmesi için gerekli eşitlemeyi temsil eder, bu da onu eşzamanlı senaryolarda kullanılacak özel veri yapıları oluşturmak için çok güçlü bir tür yapar.</span><span class="sxs-lookup"><span data-stu-id="c4ece-264">In addition to the ability to build custom task-based combinators, having a data structure in <xref:System.Threading.Tasks.Task> and <xref:System.Threading.Tasks.Task%601> that represents both the results of an asynchronous operation and the necessary synchronization to join with it makes it a very powerful type on which to build custom data structures to be used in asynchronous scenarios.</span></span>

### <a name="asynccache"></a><span data-ttu-id="c4ece-265">AsyncÖnbellek</span><span class="sxs-lookup"><span data-stu-id="c4ece-265">AsyncCache</span></span>
 <span data-ttu-id="c4ece-266">Bir görevin önemli bir yönü birden fazla tüketiciye dağıtılabilir, hepsi de onu bekleyebilir, onunla devam ları kaydedebilir, <xref:System.Threading.Tasks.Task%601>sonucunu veya özel durumlarını (durumunda) alabilir.</span><span class="sxs-lookup"><span data-stu-id="c4ece-266">One important aspect of a task is that it may be handed out to multiple consumers, all of whom may await it, register continuations with it, get its result or exceptions (in the case of <xref:System.Threading.Tasks.Task%601>), and so on.</span></span>  <span data-ttu-id="c4ece-267">Bu <xref:System.Threading.Tasks.Task> yapar <xref:System.Threading.Tasks.Task%601> ve mükemmel bir asynchronöz önbelleğe alma altyapısında kullanılmak üzere uygundur.</span><span class="sxs-lookup"><span data-stu-id="c4ece-267">This makes <xref:System.Threading.Tasks.Task> and <xref:System.Threading.Tasks.Task%601> perfectly suited to be used in an asynchronous caching infrastructure.</span></span>  <span data-ttu-id="c4ece-268">Burada küçük ama güçlü bir asynchronous önbellek üstüne <xref:System.Threading.Tasks.Task%601>inşa bir örnek:</span><span class="sxs-lookup"><span data-stu-id="c4ece-268">Here’s an example of a small but powerful asynchronous cache built on top of <xref:System.Threading.Tasks.Task%601>:</span></span>

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

 <span data-ttu-id="c4ece-269">[AsyncCache\<TKey,TValue>](https://devblogs.microsoft.com/pfxteam/parallelextensionsextras-tour-12-asynccache/) sınıfı, bir alır `TKey` ve bir <xref:System.Threading.Tasks.Task%601>döndürür bir işlevi oluşturucu bir temsilci olarak kabul eder.</span><span class="sxs-lookup"><span data-stu-id="c4ece-269">The [AsyncCache\<TKey,TValue>](https://devblogs.microsoft.com/pfxteam/parallelextensionsextras-tour-12-asynccache/) class accepts as a delegate to its constructor a function that takes a `TKey` and returns a <xref:System.Threading.Tasks.Task%601>.</span></span>  <span data-ttu-id="c4ece-270">Önbellekten daha önce erişilen değerler iç sözlükte depolanır ve önbelleğe aynı anda erişilmiş olsa bile anahtar başına yalnızca bir görevin oluşturulmasını `AsyncCache` sağlar.</span><span class="sxs-lookup"><span data-stu-id="c4ece-270">Any previously accessed values from the cache are stored in the internal dictionary, and the `AsyncCache` ensures that only one task is generated per key, even if the cache is accessed concurrently.</span></span>

 <span data-ttu-id="c4ece-271">Örneğin, indirilen web sayfaları için bir önbellek oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c4ece-271">For example, you can build a cache for downloaded web pages:</span></span>

```csharp
private AsyncCache<string,string> m_webPages =
    new AsyncCache<string,string>(DownloadStringAsync);
```

 <span data-ttu-id="c4ece-272">Daha sonra, bir web sayfasının içeriğine ihtiyaç duyduğunuzda bu önbelleği eşzamanlı yöntemlerle kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c4ece-272">You can then use this cache in asynchronous methods whenever you need the contents of a web page.</span></span> <span data-ttu-id="c4ece-273">Sınıf, `AsyncCache` mümkün olduğunca az sayfa indirmenizi sağlar ve sonuçları önbelleğe almaz.</span><span class="sxs-lookup"><span data-stu-id="c4ece-273">The `AsyncCache` class ensures that you’re downloading as few pages as possible, and caches the results.</span></span>

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

### <a name="asyncproducerconsumercollection"></a><span data-ttu-id="c4ece-274">AsyncProducerConsumerCollection</span><span class="sxs-lookup"><span data-stu-id="c4ece-274">AsyncProducerConsumerCollection</span></span>
 <span data-ttu-id="c4ece-275">Eşzamanlı etkinlikleri koordine etmek için veri yapıları oluşturmak için görevleri de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c4ece-275">You can also use tasks to build data structures for coordinating asynchronous activities.</span></span>  <span data-ttu-id="c4ece-276">Klasik paralel tasarım desenlerinden birini düşünün: üretici/tüketici.</span><span class="sxs-lookup"><span data-stu-id="c4ece-276">Consider one of the classic parallel design patterns: producer/consumer.</span></span>  <span data-ttu-id="c4ece-277">Bu modelde, üreticiler tüketiciler tarafından tüketilen verileri üretirler ve üreticiler ve tüketiciler paralel olarak çalışabilirler.</span><span class="sxs-lookup"><span data-stu-id="c4ece-277">In this pattern, producers generate data that is consumed by consumers, and the producers and consumers may run in parallel.</span></span> <span data-ttu-id="c4ece-278">Örneğin, tüketici, daha önce madde 2'yi üreten bir üretici tarafından oluşturulan madde 1'i işler.</span><span class="sxs-lookup"><span data-stu-id="c4ece-278">For example, the consumer processes item 1, which was previously generated by a producer who is now producing item 2.</span></span>  <span data-ttu-id="c4ece-279">Üretici/tüketici modeli için, tüketicilerin yeni verilerden haberdar edilebilmeleri ve mevcut olduğunda bulabilmeleri için üreticiler tarafından oluşturulan çalışmayı depolamak için her zaman bazı veri yapısına ihtiyacınız vardır.</span><span class="sxs-lookup"><span data-stu-id="c4ece-279">For the producer/consumer pattern, you invariably need some data structure to store the work created by producers so that the consumers may be notified of new data and find it when available.</span></span>

 <span data-ttu-id="c4ece-280">Asynchronous yöntemlerinin üretici ve tüketici olarak kullanılmasını sağlayan görevlerin üzerine inşa edilmiş basit bir veri yapısı aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="c4ece-280">Here’s a simple data structure built on top of tasks that enables asynchronous methods to be used as producers and consumers:</span></span>

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

 <span data-ttu-id="c4ece-281">Bu veri yapısı yerinde olduğundan, aşağıdaki gibi kod yazabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c4ece-281">With that data structure in place, you can write code such as the following:</span></span>

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

<span data-ttu-id="c4ece-282">Ad <xref:System.Threading.Tasks.Dataflow> alanı, <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> benzer bir şekilde kullanabileceğiniz, ancak özel bir koleksiyon türü oluşturmak zorunda kalmadan türünü içerir:</span><span class="sxs-lookup"><span data-stu-id="c4ece-282">The <xref:System.Threading.Tasks.Dataflow> namespace includes the <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> type, which you can use in a similar manner, but without having to build a custom collection type:</span></span>

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
> <span data-ttu-id="c4ece-283">İsim <xref:System.Threading.Tasks.Dataflow> alanı **NuGet**üzerinden .NET Framework 4.5'te mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="c4ece-283">The <xref:System.Threading.Tasks.Dataflow> namespace is available in the .NET Framework 4.5 through **NuGet**.</span></span> <span data-ttu-id="c4ece-284">Ad alanını içeren derlemeyi <xref:System.Threading.Tasks.Dataflow> yüklemek için Visual Studio'da projenizi açın, Proje menüsünden **NuGet Paketlerini Yönet'i** seçin ve Microsoft.Tpl.Dataflow paketini çevrimiçi olarak arayın.</span><span class="sxs-lookup"><span data-stu-id="c4ece-284">To install the assembly that contains the <xref:System.Threading.Tasks.Dataflow> namespace, open your project in Visual Studio, choose **Manage NuGet Packages** from the Project menu, and search online for the Microsoft.Tpl.Dataflow package.</span></span>

## <a name="see-also"></a><span data-ttu-id="c4ece-285">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c4ece-285">See also</span></span>

- [<span data-ttu-id="c4ece-286">Görev Tabanlı Zaman Uyumsuz Desen (TAP)</span><span class="sxs-lookup"><span data-stu-id="c4ece-286">Task-based Asynchronous Pattern (TAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)
- [<span data-ttu-id="c4ece-287">Görev Tabanlı Zaman Uyumsuz Deseni Uygulama</span><span class="sxs-lookup"><span data-stu-id="c4ece-287">Implementing the Task-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/implementing-the-task-based-asynchronous-pattern.md)
- [<span data-ttu-id="c4ece-288">Diğer Zaman Uyumsuz Desen ve Türlerle Birlikte Çalışma</span><span class="sxs-lookup"><span data-stu-id="c4ece-288">Interop with Other Asynchronous Patterns and Types</span></span>](../../../docs/standard/asynchronous-programming-patterns/interop-with-other-asynchronous-patterns-and-types.md)
