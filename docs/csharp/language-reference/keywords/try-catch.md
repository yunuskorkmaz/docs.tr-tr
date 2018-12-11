---
title: try-catch (C# Başvurusu)
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
ms.openlocfilehash: 727c57c95d29f7133c492a1593f35d3b8d7bb74a
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53131566"
---
# <a name="try-catch-c-reference"></a><span data-ttu-id="c33f6-102">try-catch (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="c33f6-102">try-catch (C# Reference)</span></span>

<span data-ttu-id="c33f6-103">Try-catch deyiminin oluşan bir `try` blok izlenen bir veya daha fazla tarafından `catch` farklı özel durumlar için işleyiciler belirten yan tümceleri.</span><span class="sxs-lookup"><span data-stu-id="c33f6-103">The try-catch statement consists of a `try` block followed by one or more `catch` clauses, which specify handlers for different exceptions.</span></span>

## <a name="remarks"></a><span data-ttu-id="c33f6-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c33f6-104">Remarks</span></span>

<span data-ttu-id="c33f6-105">Ortak dil çalışma zamanı (CLR) bir özel durum oluştuğunda arar `catch` bu özel durumu işleyen bir ifade.</span><span class="sxs-lookup"><span data-stu-id="c33f6-105">When an exception is thrown, the common language runtime (CLR) looks for the `catch` statement that handles this exception.</span></span> <span data-ttu-id="c33f6-106">Şu anda yürütülen yöntemi gibi içermiyorsa bir `catch` engelleme, vb. çağrı yığınında yukarı geçerli bir yöntemi çağıran yönteme CLR bakar.</span><span class="sxs-lookup"><span data-stu-id="c33f6-106">If the currently executing method does not contain such a `catch` block, the CLR looks at the method that called the current method, and so on up the call stack.</span></span> <span data-ttu-id="c33f6-107">Hayır ise `catch` bloğu bulundu ve ardından CLR kullanıcıya bir işlenmeyen özel durum iletisi görüntüler ve programın yürütülmesini durdurur.</span><span class="sxs-lookup"><span data-stu-id="c33f6-107">If no `catch` block is found, then the CLR displays an unhandled exception message to the user and stops execution of the program.</span></span>

<span data-ttu-id="c33f6-108">`try` Bloğu özel durumuna neden olabilir korunan kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="c33f6-108">The `try` block contains the guarded code that may cause the exception.</span></span> <span data-ttu-id="c33f6-109">Blok, bir özel durum veya başarıyla tamamlanana kadar yürütülür.</span><span class="sxs-lookup"><span data-stu-id="c33f6-109">The block is executed until an exception is thrown or it is completed successfully.</span></span> <span data-ttu-id="c33f6-110">Aşağıdaki örnek, atama yapmayı bir `null` nesne harekete geçirirse <xref:System.NullReferenceException> özel durum:</span><span class="sxs-lookup"><span data-stu-id="c33f6-110">For example, the following attempt to cast a `null` object raises the <xref:System.NullReferenceException> exception:</span></span>

```csharp
object o2 = null;
try
{
    int i2 = (int)o2;   // Error
}
```

<span data-ttu-id="c33f6-111">Ancak `catch` yan tümcesi bağımsız değişkenler herhangi bir türde özel durum yakalamak için kullanılabilir, bu kullanım önerilmez.</span><span class="sxs-lookup"><span data-stu-id="c33f6-111">Although the `catch` clause can be used without arguments to catch any type of exception, this usage is not recommended.</span></span> <span data-ttu-id="c33f6-112">Genel olarak, yalnızca, kurtarılır biliyorsunuz özel durumları yakalamalısınız.</span><span class="sxs-lookup"><span data-stu-id="c33f6-112">In general, you should only catch those exceptions that you know how to recover from.</span></span> <span data-ttu-id="c33f6-113">Bu nedenle, her zaman türetilen bir nesne bağımsız değişkeni belirtmeniz gerekir <xref:System.Exception?displayProperty=nameWithType> örneğin:</span><span class="sxs-lookup"><span data-stu-id="c33f6-113">Therefore, you should always specify an object argument derived from <xref:System.Exception?displayProperty=nameWithType> For example:</span></span>

```csharp
catch (InvalidCastException e)
{
}
```

<span data-ttu-id="c33f6-114">Birden fazla özel kullanmak da mümkündür `catch` aynı try-catch deyiminin yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="c33f6-114">It is possible to use more than one specific `catch` clause in the same try-catch statement.</span></span> <span data-ttu-id="c33f6-115">Bu durumda, sırası `catch` yan tümceleri önemlidir çünkü `catch` yan tümceleri sırayla incelenir.</span><span class="sxs-lookup"><span data-stu-id="c33f6-115">In this case, the order of the `catch` clauses is important because the `catch` clauses are examined in order.</span></span> <span data-ttu-id="c33f6-116">Less yazımına özgü olanlardan önce daha özel istisnaları yakalayın.</span><span class="sxs-lookup"><span data-stu-id="c33f6-116">Catch the more specific exceptions before the less specific ones.</span></span> <span data-ttu-id="c33f6-117">Böylece bir sonraki bloğuna hiç ulaşılmadı, catch engeller sipariş, derleyici bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c33f6-117">The compiler produces an error if you order your catch blocks so that a later block can never be reached.</span></span>

<span data-ttu-id="c33f6-118">Kullanarak `catch` bağımsız değişkenler, işlemek istediğiniz özel durumları filtrelemek için bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="c33f6-118">Using `catch` arguments is one way to filter for the exceptions you want to handle.</span></span>  <span data-ttu-id="c33f6-119">Daha fazla uygulayacağınıza karar vermek için özel durum inceleyen bir özel durum filtresi de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c33f6-119">You can also use an exception filter that further examines the exception to decide whether to handle it.</span></span>  <span data-ttu-id="c33f6-120">Ardından, özel durum filtresi false döndürürse, işleyici için arama devam eder.</span><span class="sxs-lookup"><span data-stu-id="c33f6-120">If the exception filter returns false, then the search for a handler continues.</span></span>

```csharp
catch (ArgumentException e) when (e.ParamName == "…")
{
}
```

<span data-ttu-id="c33f6-121">Özel durum filtreleri yakalama ve filtreleri yaralanmadığı türde yığın bıraktığınızdan (aşağıda anlatıldığı) yeniden atma tercih edilir.</span><span class="sxs-lookup"><span data-stu-id="c33f6-121">Exception filters are preferable to catching and rethrowing (explained below) because filters leave the stack unharmed.</span></span>  <span data-ttu-id="c33f6-122">Bir sonraki işleyici yığın dökümleri, nereden özel durumun ilk olarak, bunu döndükten hemen son yer yerine geldiğini görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c33f6-122">If a later handler dumps the stack, you can see where the exception originally came from, rather than just the last place it was rethrown.</span></span>  <span data-ttu-id="c33f6-123">Özel durum filtre ifadeleri yaygın kullanımı günlüğe kaydetme.</span><span class="sxs-lookup"><span data-stu-id="c33f6-123">A common use of exception filter expressions is logging.</span></span>  <span data-ttu-id="c33f6-124">Her zaman yeniden oluşturma ve bunları işlemek zorunda kalmadan ilerledikçe özel durumları günlüğe kaydetmek bir günlük için de çıkarır false döndüren bir filtre oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c33f6-124">You can create a filter that always returns false that also outputs to a log, you can log exceptions as they go by without having to handle them and rethrow.</span></span>

<span data-ttu-id="c33f6-125">A [throw](throw.md) deyimi kullanılabilir bir `catch` blok tarafından yakalanan özel durumu yeniden harekete geçirileceğini `catch` deyimi.</span><span class="sxs-lookup"><span data-stu-id="c33f6-125">A [throw](throw.md) statement can be used in a `catch` block to re-throw the exception that is caught by the `catch` statement.</span></span> <span data-ttu-id="c33f6-126">Aşağıdaki örnekte kaynak bilgileri ayıklayan bir <xref:System.IO.IOException> özel durum ve ardından üst yöntemi özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c33f6-126">The following example extracts source information from an <xref:System.IO.IOException> exception, and then throws the exception to the parent method.</span></span>

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

<span data-ttu-id="c33f6-127">Bir özel durumu yakalar ve farklı bir özel durum.</span><span class="sxs-lookup"><span data-stu-id="c33f6-127">You can catch one exception and throw a different exception.</span></span> <span data-ttu-id="c33f6-128">Bunu yaptığınızda, aşağıdaki örnekte gösterildiği gibi iç özel durum Yakalanan özel durum belirtin.</span><span class="sxs-lookup"><span data-stu-id="c33f6-128">When you do this, specify the exception that you caught as the inner exception, as shown in the following example.</span></span>

```csharp
catch (InvalidCastException e) 
{
    // Perform some action here, and then throw a new exception.
    throw new YourCustomException("Put your error message here.", e);
}
```

<span data-ttu-id="c33f6-129">Belirtilen bir koşul true olduğunda aşağıdaki örnekte gösterildiği gibi ayrıca bir özel durum yeniden oluşturabilecek.</span><span class="sxs-lookup"><span data-stu-id="c33f6-129">You can also re-throw an exception when a specified condition is true, as shown in the following example.</span></span>

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
> <span data-ttu-id="c33f6-130">Genellikle daha net bir şekilde (aynı zamanda bu belgede daha önce açıklandığı gibi yığını değiştirme değil) benzer bir sonuç almak için bir özel durum filtresi kullanmak da mümkündür.</span><span class="sxs-lookup"><span data-stu-id="c33f6-130">It is also possible to use an exception filter to get a similar result in an often cleaner fashion (as well as not modifying the stack, as explained earlier in this document).</span></span> <span data-ttu-id="c33f6-131">Aşağıdaki örnek, önceki örnek olarak arayanlar için benzer bir davranış sahiptir.</span><span class="sxs-lookup"><span data-stu-id="c33f6-131">The following example has a similar behavior for callers as the previous example.</span></span> <span data-ttu-id="c33f6-132">İşlevin `InvalidCastException` çağırana geri olduğunda `e.Data` olduğu `null`.</span><span class="sxs-lookup"><span data-stu-id="c33f6-132">The function throws the `InvalidCastException` back to the caller when `e.Data` is `null`.</span></span>
> 
> ```csharp
> catch (InvalidCastException e) when (e.Data != null) 
> {
>     // Take some action.
> }
> ``` 

<span data-ttu-id="c33f6-133">Gelen içinde bir `try` sıralamadaki bildirilen değişkenlerini başlatmak, engelleyin.</span><span class="sxs-lookup"><span data-stu-id="c33f6-133">From inside a `try` block, initialize only variables that are declared therein.</span></span> <span data-ttu-id="c33f6-134">Aksi takdirde, bloğun yürütülmesini tamamlanmadan önce bir özel durum ortaya çıkabilir.</span><span class="sxs-lookup"><span data-stu-id="c33f6-134">Otherwise, an exception can occur before the execution of the block is completed.</span></span> <span data-ttu-id="c33f6-135">Örneğin, aşağıdaki kod örneği, değişken içinde `n` içinde başlatılan `try` blok.</span><span class="sxs-lookup"><span data-stu-id="c33f6-135">For example, in the following code example, the variable `n` is initialized inside the `try` block.</span></span> <span data-ttu-id="c33f6-136">Bu değişken dışında kullanma girişimi `try` engelleyin `Write(n)` deyimi bir derleyici hatası üretir.</span><span class="sxs-lookup"><span data-stu-id="c33f6-136">An attempt to use this variable outside the `try` block in the `Write(n)` statement will generate a compiler error.</span></span>

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

<span data-ttu-id="c33f6-137">Yakalama hakkında daha fazla bilgi için bkz: [try-catch-finally](try-catch-finally.md).</span><span class="sxs-lookup"><span data-stu-id="c33f6-137">For more information about catch, see [try-catch-finally](try-catch-finally.md).</span></span>

## <a name="exceptions-in-async-methods"></a><span data-ttu-id="c33f6-138">Zaman uyumsuz yöntemlerde özel durumları</span><span class="sxs-lookup"><span data-stu-id="c33f6-138">Exceptions in Async Methods</span></span>
<span data-ttu-id="c33f6-139">Zaman uyumsuz bir yöntem tarafından işaretlenen bir [zaman uyumsuz](async.md) değiştiricisi ve genellikle bir içeriyor ya da daha fazla await ifadeler veya deyimler.</span><span class="sxs-lookup"><span data-stu-id="c33f6-139">An async method is marked  by an  [async](async.md) modifier and usually contains one or more await expressions or statements.</span></span> <span data-ttu-id="c33f6-140">Await ifadesi geçerli [await](await.md) işleci bir <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="c33f6-140">An await expression applies the [await](await.md) operator to a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>.</span></span>

<span data-ttu-id="c33f6-141">Ulaştığında denetlemek bir `await` awaited görevi tamamlanıncaya kadar zaman uyumsuz yöntemin yöntem ediyor askıya alındı.</span><span class="sxs-lookup"><span data-stu-id="c33f6-141">When control reaches an `await` in the async method, progress in the method is suspended until the awaited task completes.</span></span> <span data-ttu-id="c33f6-142">Görev tamamlandığında, yürütme yönteminde devam edebilir.</span><span class="sxs-lookup"><span data-stu-id="c33f6-142">When the task  is complete, execution can resume in the method.</span></span> <span data-ttu-id="c33f6-143">Daha fazla bilgi için [Asynchronous Programming with async ve await](../../programming-guide/concepts/async/index.md) ve [zaman uyumsuz programlarda akış kontrolü](../../programming-guide/concepts/async/control-flow-in-async-programs.md).</span><span class="sxs-lookup"><span data-stu-id="c33f6-143">For more information, see [Asynchronous Programming with async and await](../../programming-guide/concepts/async/index.md) and [Control Flow in Async Programs](../../programming-guide/concepts/async/control-flow-in-async-programs.md).</span></span>

<span data-ttu-id="c33f6-144">Tamamlanan görev `await` uygulanan hatalı bir durumda, görev döndüren yöntem içinde işlenmeyen bir özel durum nedeniyle olabilir.</span><span class="sxs-lookup"><span data-stu-id="c33f6-144">The completed task to which `await` is applied might be in a faulted state because of an unhandled exception in the method that returns the task.</span></span> <span data-ttu-id="c33f6-145">Bekleyen görev özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c33f6-145">Awaiting the task throws an exception.</span></span> <span data-ttu-id="c33f6-146">Bunu döndüren zaman uyumsuz işlem iptal edilirse bir görev bir iptal edildi durumunda da kalabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c33f6-146">A task can also end up in a canceled state if the asynchronous process that returns it is canceled.</span></span> <span data-ttu-id="c33f6-147">Bekleyen iptal edilen bir görev oluşturur bir `OperationCanceledException`.</span><span class="sxs-lookup"><span data-stu-id="c33f6-147">Awaiting a canceled task throws  an `OperationCanceledException`.</span></span> <span data-ttu-id="c33f6-148">Zaman uyumsuz bir işlem iptal etme hakkında daha fazla bilgi için bkz. [Fine-Tuning Async uygulamanızda](../../programming-guide/concepts/async/fine-tuning-your-async-application.md).</span><span class="sxs-lookup"><span data-stu-id="c33f6-148">For more information about how to cancel an asynchronous process, see [Fine-Tuning Your Async Application](../../programming-guide/concepts/async/fine-tuning-your-async-application.md).</span></span>

<span data-ttu-id="c33f6-149">Özel durum yakalamak için görev await bir `try` engelleyin ve özel durum ilişkili catch `catch` blok.</span><span class="sxs-lookup"><span data-stu-id="c33f6-149">To catch the exception, await the task in a `try` block, and catch the exception in the associated `catch` block.</span></span> <span data-ttu-id="c33f6-150">Örneğin, "Örnek" bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="c33f6-150">For an example, see the "Example" section.</span></span>

<span data-ttu-id="c33f6-151">Beklenen zaman uyumsuz yöntemin birden çok özel durum oluştuğu için bir görev hatalı bir durumda olabilir.</span><span class="sxs-lookup"><span data-stu-id="c33f6-151">A task can be in a faulted state because multiple exceptions occurred in the awaited async method.</span></span> <span data-ttu-id="c33f6-152">Örneğin, görev yapılan bir çağrının sonucu olabilir <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c33f6-152">For example, the task might be the result of a call to <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="c33f6-153">Böyle bir görevi beklerken, yakalanan özel durumlardan yalnızca birini ve özel durum yakalandı tahmin edemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="c33f6-153">When you await such a task, only one of the exceptions is caught, and you can't predict which exception will be caught.</span></span> <span data-ttu-id="c33f6-154">Örneğin, "Örnek" bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="c33f6-154">For an example, see the "Example" section.</span></span>

## <a name="example"></a><span data-ttu-id="c33f6-155">Örnek</span><span class="sxs-lookup"><span data-stu-id="c33f6-155">Example</span></span>

<span data-ttu-id="c33f6-156">Aşağıdaki örnekte, `try` bloğu içeren bir çağrı `ProcessString` yönteminin bir özel durumuna neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="c33f6-156">In the following example, the `try` block contains a call to the `ProcessString` method that may cause an exception.</span></span> <span data-ttu-id="c33f6-157">`catch` Yan tümcesi içeren özel durum işleyici, yalnızca ekranda bir ileti görüntüler.</span><span class="sxs-lookup"><span data-stu-id="c33f6-157">The `catch` clause contains the exception handler that just displays a message on the screen.</span></span> <span data-ttu-id="c33f6-158">Zaman `throw` deyimi çağrılır içindeki `MyMethod`, sistem arar `catch` deyimi ve iletisini görüntüler `Exception caught`.</span><span class="sxs-lookup"><span data-stu-id="c33f6-158">When the `throw` statement is called from inside `MyMethod`, the system looks for the `catch` statement and displays the message `Exception caught`.</span></span>

[!code-csharp[csrefKeywordsExceptions#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#2)]

## <a name="example"></a><span data-ttu-id="c33f6-159">Örnek</span><span class="sxs-lookup"><span data-stu-id="c33f6-159">Example</span></span>

<span data-ttu-id="c33f6-160">Aşağıdaki örnekte, iki catch blokları kullanılır ve ilk birlikte gelen en özel durum yakalandı.</span><span class="sxs-lookup"><span data-stu-id="c33f6-160">In the following example, two catch blocks are used, and the most specific exception, which comes first, is caught.</span></span>

<span data-ttu-id="c33f6-161">En az spesifiğe istisna yakalamak için throw deyiminde değiştirebilirsiniz `ProcessString` şu ifadeyle: `throw new Exception()`.</span><span class="sxs-lookup"><span data-stu-id="c33f6-161">To catch the least specific exception, you can replace the throw statement in `ProcessString` with the following statement: `throw new Exception()`.</span></span>

<span data-ttu-id="c33f6-162">En az Özel catch bloğu ilk örnekte yerleştirirseniz aşağıdaki hata iletisi görüntülenir: `A previous catch clause already catches all exceptions of this or a super type ('System.Exception')`.</span><span class="sxs-lookup"><span data-stu-id="c33f6-162">If you place the least-specific catch block first in the example, the following  error message appears: `A previous catch clause already catches all exceptions of this or a super type ('System.Exception')`.</span></span>

[!code-csharp[csrefKeywordsExceptions#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#3)]

## <a name="example"></a><span data-ttu-id="c33f6-163">Örnek</span><span class="sxs-lookup"><span data-stu-id="c33f6-163">Example</span></span>

<span data-ttu-id="c33f6-164">Aşağıdaki örnekte, özel durum işleme için zaman uyumsuz yöntemler gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="c33f6-164">The following example illustrates exception handling for async methods.</span></span> <span data-ttu-id="c33f6-165">Zaman uyumsuz bir görev oluşturan bir özel durum yakalamak için yerleştirin `await` ifadesinde bir `try` blok ve özel durumu bir `catch` blok.</span><span class="sxs-lookup"><span data-stu-id="c33f6-165">To catch an exception that an async task throws, place the `await` expression in a `try` block, and catch the exception in a `catch` block.</span></span>

<span data-ttu-id="c33f6-166">Açıklamadan çıkarın `throw new Exception` özel durum işleme göstermek için örnek satır.</span><span class="sxs-lookup"><span data-stu-id="c33f6-166">Uncomment the `throw new Exception` line in the example to demonstrate exception handling.</span></span> <span data-ttu-id="c33f6-167">Görevin `IsFaulted` özelliği `True`, görevin `Exception.InnerException` özelliği, özel duruma ayarlanır ve özel durum yakalandı `catch` blok.</span><span class="sxs-lookup"><span data-stu-id="c33f6-167">The task's `IsFaulted` property is set to `True`, the task's `Exception.InnerException` property is set to the exception, and the exception is caught in the `catch` block.</span></span>

<span data-ttu-id="c33f6-168">Açıklamadan çıkarın `throw new OperationCancelledException` zaman uyumsuz bir işlem iptal ettiğinizde ne göstermek için satır.</span><span class="sxs-lookup"><span data-stu-id="c33f6-168">Uncomment the `throw new OperationCancelledException` line to demonstrate what happens when you cancel an asynchronous process.</span></span> <span data-ttu-id="c33f6-169">Görevin `IsCanceled` özelliği `true`, ve özel durum yakalandı `catch` blok.</span><span class="sxs-lookup"><span data-stu-id="c33f6-169">The task's `IsCanceled` property is set to `true`, and the exception is caught in the `catch` block.</span></span> <span data-ttu-id="c33f6-170">Bu örnek için görev ait uygulama bazı koşullar altında `IsFaulted` özelliği `true` ve `IsCanceled` ayarlanır `false`.</span><span class="sxs-lookup"><span data-stu-id="c33f6-170">Under some conditions that don't apply to this example, the task's `IsFaulted` property is set to `true` and `IsCanceled` is set to `false`.</span></span>

[!code-csharp[csAsyncExceptions#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csasyncexceptions/cs/class1.cs#2)]  

## <a name="example"></a><span data-ttu-id="c33f6-171">Örnek</span><span class="sxs-lookup"><span data-stu-id="c33f6-171">Example</span></span>

<span data-ttu-id="c33f6-172">Aşağıdaki örnek, özel durum işleme birden çok görev içinde birden çok özel durum burada sonuçlanabilir gösterir.</span><span class="sxs-lookup"><span data-stu-id="c33f6-172">The following example illustrates exception handling where multiple tasks can result in multiple exceptions.</span></span> <span data-ttu-id="c33f6-173">`try` Bloğu için bir çağrı tarafından döndürülen görev bekler <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c33f6-173">The `try` block awaits the task that's returned by a call to <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="c33f6-174">WhenAll uygulandığı üç görev tamamlandığında, görev tamamlandıysa.</span><span class="sxs-lookup"><span data-stu-id="c33f6-174">The task is complete when the three tasks to which WhenAll is applied are complete.</span></span>

<span data-ttu-id="c33f6-175">Her biri üç görev, bir özel durum neden olur.</span><span class="sxs-lookup"><span data-stu-id="c33f6-175">Each of the three tasks causes an exception.</span></span> <span data-ttu-id="c33f6-176">`catch` Blok yinelenir bulunan özel durumlar üzerinden `Exception.InnerExceptions` özelliği tarafından döndürülen görevin <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c33f6-176">The `catch` block iterates through the exceptions, which are found in the `Exception.InnerExceptions` property of the task that was returned by <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>.</span></span>

[!code-csharp[csAsyncExceptions#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csasyncexceptions/cs/class1.cs#4)]

## <a name="c-language-specification"></a><span data-ttu-id="c33f6-177">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="c33f6-177">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="c33f6-178">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c33f6-178">See also</span></span>

- [<span data-ttu-id="c33f6-179">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="c33f6-179">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="c33f6-180">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="c33f6-180">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="c33f6-181">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="c33f6-181">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="c33f6-182">try, throw ve catch Deyimleri (C++)</span><span class="sxs-lookup"><span data-stu-id="c33f6-182">try, throw, and catch Statements (C++)</span></span>](/cpp/cpp/try-throw-and-catch-statements-cpp)
- [<span data-ttu-id="c33f6-183">Özel Durum İşleme Deyimleri</span><span class="sxs-lookup"><span data-stu-id="c33f6-183">Exception Handling Statements</span></span>](exception-handling-statements.md)
- [<span data-ttu-id="c33f6-184">throw</span><span class="sxs-lookup"><span data-stu-id="c33f6-184">throw</span></span>](throw.md)
- [<span data-ttu-id="c33f6-185">try-finally</span><span class="sxs-lookup"><span data-stu-id="c33f6-185">try-finally</span></span>](try-finally.md)
- [<span data-ttu-id="c33f6-186">Nasıl Yapılır: Açıkça özel durumlar oluşturma</span><span class="sxs-lookup"><span data-stu-id="c33f6-186">How to: Explicitly Throw Exceptions</span></span>](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)