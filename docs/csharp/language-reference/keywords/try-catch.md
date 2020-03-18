---
title: try-catch - C# Referans
ms.date: 07/20/2015
f1_keywords:
- try
- try_CSharpKeyword
- catch
- catch_CSharpKeyword
helpviewer_keywords:
- catch keyword [C#]
- try-catch statement [C#]
ms.assetid: cb5503c7-bfa1-4610-8fc2-ddcd2e84c438
ms.openlocfilehash: 3d4315a09869b77b4ae8cbb43646f9a96280b678
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173477"
---
# <a name="try-catch-c-reference"></a><span data-ttu-id="299b9-102">try-catch (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="299b9-102">try-catch (C# Reference)</span></span>

<span data-ttu-id="299b9-103">Try-catch deyimi, farklı `try` özel durumlar için `catch` işleyicileri belirten bir veya daha fazla yan tümcenin izlediği bir bloktan oluşur.</span><span class="sxs-lookup"><span data-stu-id="299b9-103">The try-catch statement consists of a `try` block followed by one or more `catch` clauses, which specify handlers for different exceptions.</span></span>

<span data-ttu-id="299b9-104">Bir özel durum atıldığında, ortak dil çalışma zamanı `catch` (CLR) bu özel durumu işleyen deyimi arar.</span><span class="sxs-lookup"><span data-stu-id="299b9-104">When an exception is thrown, the common language runtime (CLR) looks for the `catch` statement that handles this exception.</span></span> <span data-ttu-id="299b9-105">Şu anda yürütülen yöntem `catch` böyle bir blok içermiyorsa, CLR geçerli yöntemi denilen yönteme bakar ve böylece çağrı yığınıkadar.</span><span class="sxs-lookup"><span data-stu-id="299b9-105">If the currently executing method does not contain such a `catch` block, the CLR looks at the method that called the current method, and so on up the call stack.</span></span> <span data-ttu-id="299b9-106">Engel `catch` bulunamazsa, CLR kullanıcıya işlenmemiş bir özel durum iletisi görüntüler ve programın yürütülmesini durdurur.</span><span class="sxs-lookup"><span data-stu-id="299b9-106">If no `catch` block is found, then the CLR displays an unhandled exception message to the user and stops execution of the program.</span></span>

<span data-ttu-id="299b9-107">Blok, `try` özel durumlara neden olabilecek korumalı kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="299b9-107">The `try` block contains the guarded code that may cause the exception.</span></span> <span data-ttu-id="299b9-108">Bir özel durum atılıncaya veya başarıyla tamamlanana kadar blok yürütülür.</span><span class="sxs-lookup"><span data-stu-id="299b9-108">The block is executed until an exception is thrown or it is completed successfully.</span></span> <span data-ttu-id="299b9-109">Örneğin, bir `null` nesneyi atma girişimi <xref:System.NullReferenceException> özel durumu yükseltir:</span><span class="sxs-lookup"><span data-stu-id="299b9-109">For example, the following attempt to cast a `null` object raises the <xref:System.NullReferenceException> exception:</span></span>

```csharp
object o2 = null;
try
{
    int i2 = (int)o2;   // Error
}
```

<span data-ttu-id="299b9-110">`catch` Yan tümce, herhangi bir özel durum türünü yakalamak için bağımsız değişkenler olmadan kullanılabilse de, bu kullanım önerilmez.</span><span class="sxs-lookup"><span data-stu-id="299b9-110">Although the `catch` clause can be used without arguments to catch any type of exception, this usage is not recommended.</span></span> <span data-ttu-id="299b9-111">Genel olarak, yalnızca nasıl kurtarAcağını bildiğiniz bu özel durumları yakalamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="299b9-111">In general, you should only catch those exceptions that you know how to recover from.</span></span> <span data-ttu-id="299b9-112">Bu nedenle, her zaman <xref:System.Exception?displayProperty=nameWithType> örneğin türetilen bir nesne bağımsız değişkeni belirtmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="299b9-112">Therefore, you should always specify an object argument derived from <xref:System.Exception?displayProperty=nameWithType> For example:</span></span>

```csharp
catch (InvalidCastException e)
{
}
```

<span data-ttu-id="299b9-113">Aynı try-catch deyiminde `catch` birden fazla belirli yan tümce kullanmak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="299b9-113">It is possible to use more than one specific `catch` clause in the same try-catch statement.</span></span> <span data-ttu-id="299b9-114">Bu durumda, `catch` `catch` yan tümceler sırayla incelendiğinden, yan tümcelerin sırası önemlidir.</span><span class="sxs-lookup"><span data-stu-id="299b9-114">In this case, the order of the `catch` clauses is important because the `catch` clauses are examined in order.</span></span> <span data-ttu-id="299b9-115">Daha az spesifik olanlardan önce daha spesifik özel durumları yakalayın.</span><span class="sxs-lookup"><span data-stu-id="299b9-115">Catch the more specific exceptions before the less specific ones.</span></span> <span data-ttu-id="299b9-116">Derleyici, daha sonraki bir blota asla ulaşılamayacak şekilde yakalama bloklarınızı sipariş ederseniz bir hata üretir.</span><span class="sxs-lookup"><span data-stu-id="299b9-116">The compiler produces an error if you order your catch blocks so that a later block can never be reached.</span></span>

<span data-ttu-id="299b9-117">Bağımsız `catch` değişkenleri kullanmak, işlemek istediğiniz özel durumlara filtre uygulamanın bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="299b9-117">Using `catch` arguments is one way to filter for the exceptions you want to handle.</span></span>  <span data-ttu-id="299b9-118">Ayrıca, özel durumu işleyip işlememeye karar vermek için daha fazla inceleyen bir özel durum filtresi de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="299b9-118">You can also use an exception filter that further examines the exception to decide whether to handle it.</span></span>  <span data-ttu-id="299b9-119">Özel durum filtresi yanlış dönerse, işleyici araması devam ediyor.</span><span class="sxs-lookup"><span data-stu-id="299b9-119">If the exception filter returns false, then the search for a handler continues.</span></span>

```csharp
catch (ArgumentException e) when (e.ParamName == "…")
{
}
```

<span data-ttu-id="299b9-120">Özel durum filtreleri, yığından zarar görmeden ayrıldığından, yakalama ve yeniden atma (aşağıda açıklanan) tercih edilir.</span><span class="sxs-lookup"><span data-stu-id="299b9-120">Exception filters are preferable to catching and rethrowing (explained below) because filters leave the stack unharmed.</span></span>  <span data-ttu-id="299b9-121">Daha sonraki bir işleyici yığını boşaltıyorsa, özel durum aslında nereden geldiğini değil, sadece yeniden atıldığı son yerde görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="299b9-121">If a later handler dumps the stack, you can see where the exception originally came from, rather than just the last place it was rethrown.</span></span>  <span data-ttu-id="299b9-122">Özel durum filtresi ifadelerinin yaygın kullanımı günlüğe kaydetmedir.</span><span class="sxs-lookup"><span data-stu-id="299b9-122">A common use of exception filter expressions is logging.</span></span>  <span data-ttu-id="299b9-123">Her zaman bir günlük çıkışları yanlış döndürür bir filtre oluşturabilirsiniz, bunları işlemek ve yeniden atmak zorunda kalmadan gitmek gibi özel durumlar günlüğe kaydedebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="299b9-123">You can create a filter that always returns false that also outputs to a log, you can log exceptions as they go by without having to handle them and rethrow.</span></span>

<span data-ttu-id="299b9-124">[Bir atma](throw.md) deyimi, deyim `catch` tarafından yakalanan özel durumu yeniden atmak `catch` için bir blokta kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="299b9-124">A [throw](throw.md) statement can be used in a `catch` block to re-throw the exception that is caught by the `catch` statement.</span></span> <span data-ttu-id="299b9-125">Aşağıdaki örnek, kaynak bilgilerini <xref:System.IO.IOException> bir özel durum ayıklar ve sonra üst yönteme özel durumu atar.</span><span class="sxs-lookup"><span data-stu-id="299b9-125">The following example extracts source information from an <xref:System.IO.IOException> exception, and then throws the exception to the parent method.</span></span>

```csharp
catch (FileNotFoundException e)
{
    // FileNotFoundExceptions are handled here.
}
catch (IOException e)
{
    // Extract some information from this exception, and then
    // throw it to the parent method.
    if (e.Source != null)
        Console.WriteLine("IOException source: {0}", e.Source);
    throw;
}
```

<span data-ttu-id="299b9-126">Bir özel durum yakalamak ve farklı bir özel durum atabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="299b9-126">You can catch one exception and throw a different exception.</span></span> <span data-ttu-id="299b9-127">Bunu yaptığınızda, aşağıdaki örnekte gösterildiği gibi, iç özel durum olarak yakaladığınız özel durumu belirtin.</span><span class="sxs-lookup"><span data-stu-id="299b9-127">When you do this, specify the exception that you caught as the inner exception, as shown in the following example.</span></span>

```csharp
catch (InvalidCastException e)
{
    // Perform some action here, and then throw a new exception.
    throw new YourCustomException("Put your error message here.", e);
}
```

<span data-ttu-id="299b9-128">Aşağıdaki örnekte gösterildiği gibi, belirli bir koşul doğru olduğunda da bir özel durum yeniden atabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="299b9-128">You can also re-throw an exception when a specified condition is true, as shown in the following example.</span></span>

```csharp
catch (InvalidCastException e)
{
    if (e.Data == null)
    {
        throw;
    }
    else
    {
        // Take some action.
    }
}
```

> [!NOTE]
> <span data-ttu-id="299b9-129">Benzer bir sonucu genellikle daha temiz bir şekilde elde etmek için bir özel durum filtresi kullanmak da mümkündür (ayrıca, bu belgede daha önce açıklandığı gibi yığını değiştirmeme).</span><span class="sxs-lookup"><span data-stu-id="299b9-129">It is also possible to use an exception filter to get a similar result in an often cleaner fashion (as well as not modifying the stack, as explained earlier in this document).</span></span> <span data-ttu-id="299b9-130">Aşağıdaki örnekte, önceki örnekte olduğu gibi arayanlar için benzer bir davranış vardır.</span><span class="sxs-lookup"><span data-stu-id="299b9-130">The following example has a similar behavior for callers as the previous example.</span></span> <span data-ttu-id="299b9-131">İşlev geri `InvalidCastException` yi arayanın `e.Data` geri `null`sini atar.</span><span class="sxs-lookup"><span data-stu-id="299b9-131">The function throws the `InvalidCastException` back to the caller when `e.Data` is `null`.</span></span>
>
> ```csharp
> catch (InvalidCastException e) when (e.Data != null)
> {
>     // Take some action.
> }
> ```

<span data-ttu-id="299b9-132">Bir `try` bloğun içinden, yalnızca burada bildirilen değişkenleri başharfe ait hale getiren değişkenler.</span><span class="sxs-lookup"><span data-stu-id="299b9-132">From inside a `try` block, initialize only variables that are declared therein.</span></span> <span data-ttu-id="299b9-133">Aksi takdirde, bloğun yürütülmesi tamamlanmadan önce bir özel durum oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="299b9-133">Otherwise, an exception can occur before the execution of the block is completed.</span></span> <span data-ttu-id="299b9-134">Örneğin, aşağıdaki kod örneğinde, `n` değişken bloğun içinde `try` baş harfe doğru başlanır.</span><span class="sxs-lookup"><span data-stu-id="299b9-134">For example, in the following code example, the variable `n` is initialized inside the `try` block.</span></span> <span data-ttu-id="299b9-135">`Write(n)` İfadedeki `try` bloğun dışında bu değişkeni kullanma girişimi derleyici hatası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="299b9-135">An attempt to use this variable outside the `try` block in the `Write(n)` statement will generate a compiler error.</span></span>

```csharp
static void Main()
{
    int n;
    try
    {
        // Do not initialize this variable here.
        n = 123;
    }
    catch
    {
    }
    // Error: Use of unassigned local variable 'n'.
    Console.Write(n);
}
```

<span data-ttu-id="299b9-136">Catch hakkında daha fazla bilgi için, [try-catch-finally](try-catch-finally.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="299b9-136">For more information about catch, see [try-catch-finally](try-catch-finally.md).</span></span>

## <a name="exceptions-in-async-methods"></a><span data-ttu-id="299b9-137">Async yöntemlerindeki özel durumlar</span><span class="sxs-lookup"><span data-stu-id="299b9-137">Exceptions in async methods</span></span>

<span data-ttu-id="299b9-138">Bir async yöntemi bir [async](async.md) değiştirici tarafından işaretlenir ve genellikle bir veya daha fazla bekleyen ifadeler veya ifadeler içerir.</span><span class="sxs-lookup"><span data-stu-id="299b9-138">An async method is marked  by an  [async](async.md) modifier and usually contains one or more await expressions or statements.</span></span> <span data-ttu-id="299b9-139">Bekleyen bir ifade, [bekleme](../operators/await.md) işlecini bir <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="299b9-139">An await expression applies the [await](../operators/await.md) operator to a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>.</span></span>

<span data-ttu-id="299b9-140">Denetim async `await` yönteminde bir ulaştığında, yöntemdeki ilerleme beklenen görev tamamlanana kadar askıya alınır.</span><span class="sxs-lookup"><span data-stu-id="299b9-140">When control reaches an `await` in the async method, progress in the method is suspended until the awaited task completes.</span></span> <span data-ttu-id="299b9-141">Görev tamamlandığında, yürütme yöntemde devam edebilir.</span><span class="sxs-lookup"><span data-stu-id="299b9-141">When the task  is complete, execution can resume in the method.</span></span> <span data-ttu-id="299b9-142">Daha fazla bilgi için, [Async programları ile Asynchronous Programming](../../programming-guide/concepts/async/index.md) bakın ve bekliyor ve [Async Programları Kontrol Akışı.](../../programming-guide/concepts/async/control-flow-in-async-programs.md)</span><span class="sxs-lookup"><span data-stu-id="299b9-142">For more information, see [Asynchronous Programming with async and await](../../programming-guide/concepts/async/index.md) and [Control Flow in Async Programs](../../programming-guide/concepts/async/control-flow-in-async-programs.md).</span></span>

<span data-ttu-id="299b9-143">Görev döndüren `await` yöntemde işlenmemiş bir özel durum nedeniyle uygulanan tamamlanmış görev hatalı durumda olabilir.</span><span class="sxs-lookup"><span data-stu-id="299b9-143">The completed task to which `await` is applied might be in a faulted state because of an unhandled exception in the method that returns the task.</span></span> <span data-ttu-id="299b9-144">Görevi beklemek bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="299b9-144">Awaiting the task throws an exception.</span></span> <span data-ttu-id="299b9-145">Bir görev, iptal edilen eşsenkronize işlem iptal edilirse, iptal edilmiş durumda da sona erebilir.</span><span class="sxs-lookup"><span data-stu-id="299b9-145">A task can also end up in a canceled state if the asynchronous process that returns it is canceled.</span></span> <span data-ttu-id="299b9-146">İptal edilmiş bir görevin `OperationCanceledException`bekleyerek bir .</span><span class="sxs-lookup"><span data-stu-id="299b9-146">Awaiting a canceled task throws  an `OperationCanceledException`.</span></span> <span data-ttu-id="299b9-147">Bir eşzamanlı işlemi nasıl iptal edin, [async Uygulamanızı İyi Ayarla](../../programming-guide/concepts/async/fine-tuning-your-async-application.md)hakkında daha fazla bilgi için bkz.</span><span class="sxs-lookup"><span data-stu-id="299b9-147">For more information about how to cancel an asynchronous process, see [Fine-Tuning Your Async Application](../../programming-guide/concepts/async/fine-tuning-your-async-application.md).</span></span>

<span data-ttu-id="299b9-148">Özel durumu yakalamak için, görevi `try` bir blokta bekleyin ve `catch` ilişkili bloktaki özel durumu yakalayın.</span><span class="sxs-lookup"><span data-stu-id="299b9-148">To catch the exception, await the task in a `try` block, and catch the exception in the associated `catch` block.</span></span> <span data-ttu-id="299b9-149">Örneğin, [Async yöntemi örnek](#async-method-example) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="299b9-149">For an example, see the [Async method example](#async-method-example) section.</span></span>

<span data-ttu-id="299b9-150">Beklenen async yönteminde birden çok özel durum oluştuğundan, görev hatalı durumda olabilir.</span><span class="sxs-lookup"><span data-stu-id="299b9-150">A task can be in a faulted state because multiple exceptions occurred in the awaited async method.</span></span> <span data-ttu-id="299b9-151">Örneğin, görev <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="299b9-151">For example, the task might be the result of a call to <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="299b9-152">Böyle bir görevi beklerken, istisnalardan yalnızca biri yakalanır ve hangi özel durum yakalanacak tahmin edemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="299b9-152">When you await such a task, only one of the exceptions is caught, and you can't predict which exception will be caught.</span></span> <span data-ttu-id="299b9-153">Örneğin, [Task.WhenAll örnek](#taskwhenall-example) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="299b9-153">For an example, see the [Task.WhenAll example](#taskwhenall-example) section.</span></span>

## <a name="example"></a><span data-ttu-id="299b9-154">Örnek</span><span class="sxs-lookup"><span data-stu-id="299b9-154">Example</span></span>

<span data-ttu-id="299b9-155">Aşağıdaki örnekte, `try` blok bir özel `ProcessString` durum neden olabilir yöntemi için bir çağrı içerir.</span><span class="sxs-lookup"><span data-stu-id="299b9-155">In the following example, the `try` block contains a call to the `ProcessString` method that may cause an exception.</span></span> <span data-ttu-id="299b9-156">Yan `catch` tümce, ekranda yalnızca bir ileti görüntüleyen özel durum işleyicisini içerir.</span><span class="sxs-lookup"><span data-stu-id="299b9-156">The `catch` clause contains the exception handler that just displays a message on the screen.</span></span> <span data-ttu-id="299b9-157">`throw` İfade içeriden `MyMethod`çağrıldığında, sistem `catch` deyimi arar ve iletiyi `Exception caught`görüntüler.</span><span class="sxs-lookup"><span data-stu-id="299b9-157">When the `throw` statement is called from inside `MyMethod`, the system looks for the `catch` statement and displays the message `Exception caught`.</span></span>

[!code-csharp[csrefKeywordsExceptions#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#2)]

## <a name="two-catch-blocks-example"></a><span data-ttu-id="299b9-158">İki catch blokları örnek</span><span class="sxs-lookup"><span data-stu-id="299b9-158">Two catch blocks example</span></span>

<span data-ttu-id="299b9-159">Aşağıdaki örnekte, iki catch bloğu kullanılır ve önce gelen en özel özel durum yakalanır.</span><span class="sxs-lookup"><span data-stu-id="299b9-159">In the following example, two catch blocks are used, and the most specific exception, which comes first, is caught.</span></span>

<span data-ttu-id="299b9-160">En az özel özel durumu yakalamak için, `ProcessString` atma deyimini `throw new Exception()`aşağıdaki deyimle değiştirebilirsiniz: .</span><span class="sxs-lookup"><span data-stu-id="299b9-160">To catch the least specific exception, you can replace the throw statement in `ProcessString` with the following statement: `throw new Exception()`.</span></span>

<span data-ttu-id="299b9-161">Örnekte önce en az özel catch bloğunu yerletirseniz, `A previous catch clause already catches all exceptions of this or a super type ('System.Exception')`aşağıdaki hata iletisi görüntülenir: .</span><span class="sxs-lookup"><span data-stu-id="299b9-161">If you place the least-specific catch block first in the example, the following  error message appears: `A previous catch clause already catches all exceptions of this or a super type ('System.Exception')`.</span></span>

[!code-csharp[csrefKeywordsExceptions#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#3)]

## <a name="async-method-example"></a><span data-ttu-id="299b9-162">Async yöntemi örneği</span><span class="sxs-lookup"><span data-stu-id="299b9-162">Async method example</span></span>

<span data-ttu-id="299b9-163">Aşağıdaki örnekte, async yöntemleri için özel durum işleme gösteriş.</span><span class="sxs-lookup"><span data-stu-id="299b9-163">The following example illustrates exception handling for async methods.</span></span> <span data-ttu-id="299b9-164">Bir async görev atar bir özel durum `await` yakalamak `try` için, bir blok ifade `catch` sini yerleştirin ve bir blokta özel durum yakalamak.</span><span class="sxs-lookup"><span data-stu-id="299b9-164">To catch an exception that an async task throws, place the `await` expression in a `try` block, and catch the exception in a `catch` block.</span></span>

<span data-ttu-id="299b9-165">Özel durum `throw new Exception` işlemegöstermek için örnekteki satırı açıklamayı bırakın.</span><span class="sxs-lookup"><span data-stu-id="299b9-165">Uncomment the `throw new Exception` line in the example to demonstrate exception handling.</span></span> <span data-ttu-id="299b9-166">Görevin `IsFaulted` özelliği, görevin `True` `Exception.InnerException` özelliği özel durum olarak ayarlanır ve özel durum `catch` blokta yakalanır.</span><span class="sxs-lookup"><span data-stu-id="299b9-166">The task's `IsFaulted` property is set to `True`, the task's `Exception.InnerException` property is set to the exception, and the exception is caught in the `catch` block.</span></span>

<span data-ttu-id="299b9-167">Eşzamanlı bir `throw new OperationCanceledException` işlemi iptal ettiğinizde ne olduğunu göstermek için satırı açıklamayı bırakın.</span><span class="sxs-lookup"><span data-stu-id="299b9-167">Uncomment the `throw new OperationCanceledException` line to demonstrate what happens when you cancel an asynchronous process.</span></span> <span data-ttu-id="299b9-168">Görevin `IsCanceled` özelliği ayarlanır `true`ve özel durum `catch` blokta yakalanır.</span><span class="sxs-lookup"><span data-stu-id="299b9-168">The task's `IsCanceled` property is set to `true`, and the exception is caught in the `catch` block.</span></span> <span data-ttu-id="299b9-169">Bu örnek için geçerli olmayan bazı koşullar altında, `IsFaulted` görevin `true` özelliği `IsCanceled` ' `false`ne ayarlanır ve .</span><span class="sxs-lookup"><span data-stu-id="299b9-169">Under some conditions that don't apply to this example, the task's `IsFaulted` property is set to `true` and `IsCanceled` is set to `false`.</span></span>

[!code-csharp[csAsyncExceptions#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csasyncexceptions/cs/class1.cs#2)]  

## <a name="taskwhenall-example"></a><span data-ttu-id="299b9-170">Task.WhenAll örneği</span><span class="sxs-lookup"><span data-stu-id="299b9-170">Task.WhenAll example</span></span>

<span data-ttu-id="299b9-171">Aşağıdaki örnekte, birden çok görevin birden çok özel durumla sonuçlandığı özel durum işleme gösterilebilir.</span><span class="sxs-lookup"><span data-stu-id="299b9-171">The following example illustrates exception handling where multiple tasks can result in multiple exceptions.</span></span> <span data-ttu-id="299b9-172">Blok, `try` <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>'' için yapılan bir çağrıyla döndürülen görevi bekliyor</span><span class="sxs-lookup"><span data-stu-id="299b9-172">The `try` block awaits the task that's returned by a call to <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="299b9-173">WhenAll'ın uygulandığı üç görev tamamlandığında görev tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="299b9-173">The task is complete when the three tasks to which WhenAll is applied are complete.</span></span>

<span data-ttu-id="299b9-174">Üç görevin her biri bir özel durum neden olur.</span><span class="sxs-lookup"><span data-stu-id="299b9-174">Each of the three tasks causes an exception.</span></span> <span data-ttu-id="299b9-175">Blok, `catch` iade `Exception.InnerExceptions` <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>edilen görevin özelliğinde bulunan özel durumlar aracılığıyla yinelenir.</span><span class="sxs-lookup"><span data-stu-id="299b9-175">The `catch` block iterates through the exceptions, which are found in the `Exception.InnerExceptions` property of the task that was returned by <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>.</span></span>

[!code-csharp[csAsyncExceptions#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csasyncexceptions/cs/class1.cs#4)]

## <a name="c-language-specification"></a><span data-ttu-id="299b9-176">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="299b9-176">C# language specification</span></span>

<span data-ttu-id="299b9-177">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [try deyimi](~/_csharplang/spec/statements.md#the-try-statement) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="299b9-177">For more information, see [The try statement](~/_csharplang/spec/statements.md#the-try-statement) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="299b9-178">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="299b9-178">See also</span></span>

- [<span data-ttu-id="299b9-179">C# Referans</span><span class="sxs-lookup"><span data-stu-id="299b9-179">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="299b9-180">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="299b9-180">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="299b9-181">C# Anahtar Kelimeler</span><span class="sxs-lookup"><span data-stu-id="299b9-181">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="299b9-182">try, throw ve catch Deyimleri (C++)</span><span class="sxs-lookup"><span data-stu-id="299b9-182">try, throw, and catch Statements (C++)</span></span>](/cpp/cpp/try-throw-and-catch-statements-cpp)
- [<span data-ttu-id="299b9-183">throw</span><span class="sxs-lookup"><span data-stu-id="299b9-183">throw</span></span>](throw.md)
- [<span data-ttu-id="299b9-184">try-finally</span><span class="sxs-lookup"><span data-stu-id="299b9-184">try-finally</span></span>](try-finally.md)
- [<span data-ttu-id="299b9-185">Nasıl yapılır: Açıkça Özel Durumlar Oluşturma</span><span class="sxs-lookup"><span data-stu-id="299b9-185">How to: Explicitly Throw Exceptions</span></span>](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
