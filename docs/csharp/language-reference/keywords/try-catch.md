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
ms.openlocfilehash: d6dfdf14b518582388e655ec5616904928dfd8b5
ms.sourcegitcommit: 3540f614fc94f77ca4ab58df66db2d0f4d52dfee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/01/2018
ms.locfileid: "34696445"
---
# <a name="try-catch-c-reference"></a><span data-ttu-id="5be23-102">try-catch (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="5be23-102">try-catch (C# Reference)</span></span>
<span data-ttu-id="5be23-103">Try-catch deyimi oluşan bir `try` blok izlenen bir veya daha fazla tarafından `catch` yan tümceleri farklı özel durumlar için işleyiciler belirleyin.</span><span class="sxs-lookup"><span data-stu-id="5be23-103">The try-catch statement consists of a `try` block followed by one or more `catch` clauses, which specify handlers for different exceptions.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5be23-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5be23-104">Remarks</span></span>  
 <span data-ttu-id="5be23-105">Bir özel durum, ortak dil çalışma zamanı (CLR) arar `catch` bu özel durumu işler deyimi.</span><span class="sxs-lookup"><span data-stu-id="5be23-105">When an exception is thrown, the common language runtime (CLR) looks for the `catch` statement that handles this exception.</span></span> <span data-ttu-id="5be23-106">Şu anda yürütülen yöntemi gibi içermiyorsa, bir `catch` engellemek, CLR bakar ve benzeri çağrı yığını yukarı geçerli yöntemi çağrılan yöntemi.</span><span class="sxs-lookup"><span data-stu-id="5be23-106">If the currently executing method does not contain such a `catch` block, the CLR looks at the method that called the current method, and so on up the call stack.</span></span> <span data-ttu-id="5be23-107">Öyle değilse `catch` blok bulunursa, ardından CLR kullanıcıya bir işlenmeyen özel durum iletisi görüntüler ve programın yürütülmesi durdurulur.</span><span class="sxs-lookup"><span data-stu-id="5be23-107">If no `catch` block is found, then the CLR displays an unhandled exception message to the user and stops execution of the program.</span></span>  
  
 <span data-ttu-id="5be23-108">`try` Blok özel durumuna neden olabilir korunmuş kodunu içerir.</span><span class="sxs-lookup"><span data-stu-id="5be23-108">The `try` block contains the guarded code that may cause the exception.</span></span> <span data-ttu-id="5be23-109">Blok, bir özel durum veya başarıyla tamamlanıncaya kadar yürütülür.</span><span class="sxs-lookup"><span data-stu-id="5be23-109">The block is executed until an exception is thrown or it is completed successfully.</span></span> <span data-ttu-id="5be23-110">Örneğin, aşağıdaki cast denemesi bir `null` nesnesini başlatır <xref:System.NullReferenceException> özel durum:</span><span class="sxs-lookup"><span data-stu-id="5be23-110">For example, the following attempt to cast a `null` object raises the <xref:System.NullReferenceException> exception:</span></span>  
  
```csharp  
object o2 = null;  
try  
{  
    int i2 = (int)o2;   // Error  
}  
```  
  
 <span data-ttu-id="5be23-111">Ancak `catch` yan tümcesi kullanılabilir bağımsız değişkenler herhangi bir özel durum türü yakalamak için bu kullanımı önerilmez.</span><span class="sxs-lookup"><span data-stu-id="5be23-111">Although the `catch` clause can be used without arguments to catch any type of exception, this usage is not recommended.</span></span> <span data-ttu-id="5be23-112">Genel olarak, yalnızca nasıl kurtarılır bildiğiniz bu özel durumları yakalamak.</span><span class="sxs-lookup"><span data-stu-id="5be23-112">In general, you should only catch those exceptions that you know how to recover from.</span></span> <span data-ttu-id="5be23-113">Bu nedenle, her zaman türetilmiş bir nesne bağımsız değişkeni belirtmeniz <xref:System.Exception?displayProperty=nameWithType> örneğin:</span><span class="sxs-lookup"><span data-stu-id="5be23-113">Therefore, you should always specify an object argument derived from <xref:System.Exception?displayProperty=nameWithType> For example:</span></span>  
  
```csharp  
catch (InvalidCastException e)   
{  
}  
```  
  
 <span data-ttu-id="5be23-114">Birden fazla özel kullanmak da mümkündür `catch` yan tümcesinde aynı try-catch deyimi.</span><span class="sxs-lookup"><span data-stu-id="5be23-114">It is possible to use more than one specific `catch` clause in the same try-catch statement.</span></span> <span data-ttu-id="5be23-115">Bu durumda, sırasını `catch` yan tümceleri önemlidir çünkü `catch` yan tümceleri sırayla inceledi.</span><span class="sxs-lookup"><span data-stu-id="5be23-115">In this case, the order of the `catch` clauses is important because the `catch` clauses are examined in order.</span></span> <span data-ttu-id="5be23-116">Daha fazla özel durum daha az yayına önce yakalar.</span><span class="sxs-lookup"><span data-stu-id="5be23-116">Catch the more specific exceptions before the less specific ones.</span></span> <span data-ttu-id="5be23-117">Böylece daha sonra bir blok hiç üst sınırına, catch blokları siparişi derleyici bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5be23-117">The compiler produces an error if you order your catch blocks so that a later block can never be reached.</span></span>  
  
 <span data-ttu-id="5be23-118">Kullanarak `catch` bağımsız değişkenleri olan istediğiniz işlemek için özel durumlar için filtre uygulamak için bir yolu.</span><span class="sxs-lookup"><span data-stu-id="5be23-118">Using `catch` arguments is one way to filter for the exceptions you want to handle.</span></span>  <span data-ttu-id="5be23-119">Daha fazla uygulayacağınıza karar vermek için özel durum inceler bir özel durum filtresi de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5be23-119">You can also use a exception filter that further examines the exception to decide whether to handle it.</span></span>  <span data-ttu-id="5be23-120">Özel Durum Filtresi false değeri döndürülürse, bir işleyici aramaya devam eder.</span><span class="sxs-lookup"><span data-stu-id="5be23-120">If the exception filter returns false, then the search for a handler continues.</span></span>  
  
```csharp  
catch (ArgumentException e) when (e.ParamName == "…")  
{  
}  
```  
  
 <span data-ttu-id="5be23-121">Özel durum filtreleri yakalama ve filtreleri yaralanmadığı türde yığını bıraktığınızdan (aşağıda anlatıldığı) yeniden atma tercih edilir.</span><span class="sxs-lookup"><span data-stu-id="5be23-121">Exception filters are preferable to catching and rethrowing (explained below) because filters leave the stack unharmed.</span></span>  <span data-ttu-id="5be23-122">Bir sonraki işleyici yığın dökümleri, burada özel durum ilk olarak, bunu işlenemezse yalnızca en son yer yerine geldiğini görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5be23-122">If a later handler dumps the stack, you can see where the exception originally came from, rather than just the last place it was rethrown.</span></span>  <span data-ttu-id="5be23-123">Özel durum filtre ifadeleri yaygın kullanımı günlüğü.</span><span class="sxs-lookup"><span data-stu-id="5be23-123">A common use of exception filter expressions is logging.</span></span>  <span data-ttu-id="5be23-124">Her zaman, bunları işlemek ve yeniden oluşturulması gerekmeden ilerledikçe özel durumları günlüğe kaydetmek bir oturum için de çıkarır false verir bir filtre oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5be23-124">You can create a filter that always returns false that also outputs to a log, you can log exceptions as they go by without having to handle them and rethrow.</span></span>  
  
 <span data-ttu-id="5be23-125">A [throw](../../../csharp/language-reference/keywords/throw.md) deyimi içinde kullanılabilir bir `catch` tarafından yakalanan özel durum yeniden throw blok `catch` deyimi.</span><span class="sxs-lookup"><span data-stu-id="5be23-125">A [throw](../../../csharp/language-reference/keywords/throw.md) statement can be used in a `catch` block to re-throw the exception that is caught by the `catch` statement.</span></span> <span data-ttu-id="5be23-126">Aşağıdaki örnekte kaynak bilgilerini ayıklar bir <xref:System.IO.IOException> özel durum ve ardından üst yöntemi özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5be23-126">The following example extracts source information from an <xref:System.IO.IOException> exception, and then throws the exception to the parent method.</span></span>  
  
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
  
 <span data-ttu-id="5be23-127">Bunun tek istisnası yakalamak ve farklı bir özel durum.</span><span class="sxs-lookup"><span data-stu-id="5be23-127">You can catch one exception and throw a different exception.</span></span> <span data-ttu-id="5be23-128">Bunu yaptığınızda, aşağıdaki örnekte gösterildiği gibi iç özel durum olarak yakalanan özel durum belirtin.</span><span class="sxs-lookup"><span data-stu-id="5be23-128">When you do this, specify the exception that you caught as the inner exception, as shown in the following example.</span></span>  
  
```csharp  
catch (InvalidCastException e)   
{  
    // Perform some action here, and then throw a new exception.  
    throw new YourCustomException("Put your error message here.", e);  
}  
```  
  
 <span data-ttu-id="5be23-129">Belirtilen bir koşul true olduğunda aşağıdaki örnekte gösterildiği gibi aynı zamanda bir özel durum yeniden atabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5be23-129">You can also re-throw an exception when a specified condition is true, as shown in the following example.</span></span>  
  
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
> <span data-ttu-id="5be23-130">Genellikle temiz bir şekilde (aynı zamanda bu belgenin önceki bölümlerinde açıklandığı gibi yığın değiştirme değil) benzer bir sonuç almak için bir özel durum filtresi kullanmak da mümkündür.</span><span class="sxs-lookup"><span data-stu-id="5be23-130">It is also possible to use an exception filter to get a similar result in an often cleaner fashion (as well as not modifying the stack, as explained earlier in this document).</span></span> <span data-ttu-id="5be23-131">Aşağıdaki örnek, önceki örnek olarak çağıranlar için benzer bir davranışı vardır.</span><span class="sxs-lookup"><span data-stu-id="5be23-131">The following example has a similar behavior for callers as the previous example.</span></span> <span data-ttu-id="5be23-132">İşlev oluşturur `InvalidCastException` çağırana geri zaman `e.Data` olan `null`.</span><span class="sxs-lookup"><span data-stu-id="5be23-132">The function throws the `InvalidCastException` back to the caller when `e.Data` is `null`.</span></span>
> 
> ```csharp
> catch (InvalidCastException e) when (e.Data != null)   
> {  
>     // Take some action.  
> }
> ```   

 <span data-ttu-id="5be23-133">Gelen içinde bir `try` engellemek, okuduğunuzu bildirilen değişkenlerini Başlat.</span><span class="sxs-lookup"><span data-stu-id="5be23-133">From inside a `try` block, initialize only variables that are declared therein.</span></span> <span data-ttu-id="5be23-134">Aksi takdirde, bloğun yürütme tamamlanmadan önce bir özel durum meydana gelebilir.</span><span class="sxs-lookup"><span data-stu-id="5be23-134">Otherwise, an exception can occur before the execution of the block is completed.</span></span> <span data-ttu-id="5be23-135">Örneğin, aşağıdaki kod örneğinde, değişkenin içinde `n` içinde başlatılan `try` bloğu.</span><span class="sxs-lookup"><span data-stu-id="5be23-135">For example, in the following code example, the variable `n` is initialized inside the `try` block.</span></span> <span data-ttu-id="5be23-136">Bu değişken dışında kullanma girişimi `try` engelleyin `Write(n)` deyimi derleyici hatası üretir.</span><span class="sxs-lookup"><span data-stu-id="5be23-136">An attempt to use this variable outside the `try` block in the `Write(n)` statement will generate a compiler error.</span></span>  
  
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
  
 <span data-ttu-id="5be23-137">Catch hakkında daha fazla bilgi için bkz: [try-catch-finally](../../../csharp/language-reference/keywords/try-catch-finally.md).</span><span class="sxs-lookup"><span data-stu-id="5be23-137">For more information about catch, see [try-catch-finally](../../../csharp/language-reference/keywords/try-catch-finally.md).</span></span>  
  
## <a name="exceptions-in-async-methods"></a><span data-ttu-id="5be23-138">Zaman uyumsuz yöntemler özel durumlar</span><span class="sxs-lookup"><span data-stu-id="5be23-138">Exceptions in Async Methods</span></span>  
 <span data-ttu-id="5be23-139">Bir zaman uyumsuz yöntem olarak işaretlenmiş bir [zaman uyumsuz](../../../csharp/language-reference/keywords/async.md) değiştirici ve genellikle bir içeriyor ya da daha fazla ifadeler veya deyimleri bekler.</span><span class="sxs-lookup"><span data-stu-id="5be23-139">An async method is marked  by an  [async](../../../csharp/language-reference/keywords/async.md) modifier and usually contains one or more await expressions or statements.</span></span> <span data-ttu-id="5be23-140">Bir bekleme ifade geçerlidir [bekleme](../../../csharp/language-reference/keywords/await.md) işleci bir <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="5be23-140">An await expression applies the [await](../../../csharp/language-reference/keywords/await.md) operator to a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>.</span></span>  
  
 <span data-ttu-id="5be23-141">Ulaştığında denetlemek bir `await` awaited görevi tamamlanana kadar zaman uyumsuz yönteminde yöntemi ediyor askıya alınır.</span><span class="sxs-lookup"><span data-stu-id="5be23-141">When control reaches an `await` in the async method, progress in the method is suspended until the awaited task completes.</span></span> <span data-ttu-id="5be23-142">Görev tamamlandığında, yürütme yönteminde devam edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5be23-142">When the task  is complete, execution can resume in the method.</span></span> <span data-ttu-id="5be23-143">Daha fazla bilgi için bkz: [zaman uyumsuz programlama ile zaman uyumsuz ve bekleme](../../../csharp/programming-guide/concepts/async/index.md) ve [zaman uyumsuz programlarda denetim akışı](../../../csharp/programming-guide/concepts/async/control-flow-in-async-programs.md).</span><span class="sxs-lookup"><span data-stu-id="5be23-143">For more information, see [Asynchronous Programming with async and await](../../../csharp/programming-guide/concepts/async/index.md) and [Control Flow in Async Programs](../../../csharp/programming-guide/concepts/async/control-flow-in-async-programs.md).</span></span>  
  
 <span data-ttu-id="5be23-144">Tamamlanan görevin hangi `await` uygulanan görev döndüren yöntemi işlenmeyen bir özel durum nedeniyle hatalı bir durumda olabilir.</span><span class="sxs-lookup"><span data-stu-id="5be23-144">The completed task to which `await` is applied might be in a faulted state because of an unhandled exception in the method that returns the task.</span></span> <span data-ttu-id="5be23-145">Görev bekleyen bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5be23-145">Awaiting the task throws an exception.</span></span> <span data-ttu-id="5be23-146">Onu döndüren zaman uyumsuz işlemi iptal edilirse bir görevi iptal edilmiş durumda da düşebilir.</span><span class="sxs-lookup"><span data-stu-id="5be23-146">A task can also end up in a canceled state if the asynchronous process that returns it is canceled.</span></span> <span data-ttu-id="5be23-147">İptal edilen bir görevin bekleyen oluşturur bir `OperationCanceledException`.</span><span class="sxs-lookup"><span data-stu-id="5be23-147">Awaiting a canceled task throws  an `OperationCanceledException`.</span></span> <span data-ttu-id="5be23-148">Zaman uyumsuz bir işlem iptal etme hakkında daha fazla bilgi için bkz: [Fine-Tuning uygulamanız zaman uyumsuz](../../programming-guide/concepts/async/fine-tuning-your-async-application.md).</span><span class="sxs-lookup"><span data-stu-id="5be23-148">For more information about how to cancel an asynchronous process, see [Fine-Tuning Your Async Application](../../programming-guide/concepts/async/fine-tuning-your-async-application.md).</span></span>  
  
 <span data-ttu-id="5be23-149">Özel durum yakalamak için görev await bir `try` engelleme ve özel durum ilişkili catch `catch` bloğu.</span><span class="sxs-lookup"><span data-stu-id="5be23-149">To catch the exception, await the task in a `try` block, and catch the exception in the associated `catch` block.</span></span> <span data-ttu-id="5be23-150">Örneğin, "Örnek" bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="5be23-150">For an example, see the "Example" section.</span></span>  
  
 <span data-ttu-id="5be23-151">Zaman uyumsuz beklemenin yönteminde oluştuğundan, birden fazla özel bir görev hatalı bir durumda olabilir.</span><span class="sxs-lookup"><span data-stu-id="5be23-151">A task can be in a faulted state because multiple exceptions occurred in the awaited async method.</span></span> <span data-ttu-id="5be23-152">Örneğin, görev için bir çağrı sonucunu olabilir <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5be23-152">For example, the task might be the result of a call to <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="5be23-153">Bu tür bir görev await, yalnızca bir özel durum yakalandı ve hangi özel durumu yakalandı tahmin edilemez.</span><span class="sxs-lookup"><span data-stu-id="5be23-153">When you await such a task, only one of the exceptions is caught, and you can't predict which exception will be caught.</span></span> <span data-ttu-id="5be23-154">Örneğin, "Örnek" bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="5be23-154">For an example, see the "Example" section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5be23-155">Örnek</span><span class="sxs-lookup"><span data-stu-id="5be23-155">Example</span></span>  
 <span data-ttu-id="5be23-156">Aşağıdaki örnekte, `try` bloğu için bir çağrı içerir `ProcessString` yöntemi bir özel durum neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="5be23-156">In the following example, the `try` block contains a call to the `ProcessString` method that may cause an exception.</span></span> <span data-ttu-id="5be23-157">`catch` Yan tümcesi yalnızca ekranda bir ileti görüntüler özel durum işleyici içeriyor.</span><span class="sxs-lookup"><span data-stu-id="5be23-157">The `catch` clause contains the exception handler that just displays a message on the screen.</span></span> <span data-ttu-id="5be23-158">Zaman `throw` deyimi çağrılır içinde `MyMethod`, sistem arar `catch` deyimi ve iletiyi görüntüler `Exception caught`.</span><span class="sxs-lookup"><span data-stu-id="5be23-158">When the `throw` statement is called from inside `MyMethod`, the system looks for the `catch` statement and displays the message `Exception caught`.</span></span>  
  
 [!code-csharp[csrefKeywordsExceptions#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/try-catch_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="5be23-159">Örnek</span><span class="sxs-lookup"><span data-stu-id="5be23-159">Example</span></span>  
 <span data-ttu-id="5be23-160">Aşağıdaki örnekte, iki catch bloklarını kullanılır ve önce geliyorsa, en özel durum yakalandı.</span><span class="sxs-lookup"><span data-stu-id="5be23-160">In the following example, two catch blocks are used, and the most specific exception, which comes first, is caught.</span></span>  
  
 <span data-ttu-id="5be23-161">En az belirli özel durumu yakalamak için throw deyimi içinde değiştirebilirsiniz `ProcessString` aşağıdaki ifadesiyle: `throw new Exception()`.</span><span class="sxs-lookup"><span data-stu-id="5be23-161">To catch the least specific exception, you can replace the throw statement in `ProcessString` with the following statement: `throw new Exception()`.</span></span>  
  
 <span data-ttu-id="5be23-162">En az özgü catch bloğu ilk örnekte yerleştirirseniz, aşağıdaki hata iletisi görüntülenir: `A previous catch clause already catches all exceptions of this or a super type ('System.Exception')`.</span><span class="sxs-lookup"><span data-stu-id="5be23-162">If you place the least-specific catch block first in the example, the following  error message appears: `A previous catch clause already catches all exceptions of this or a super type ('System.Exception')`.</span></span>  
  
 [!code-csharp[csrefKeywordsExceptions#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/try-catch_2.cs)]  
  
## <a name="example"></a><span data-ttu-id="5be23-163">Örnek</span><span class="sxs-lookup"><span data-stu-id="5be23-163">Example</span></span>  
 <span data-ttu-id="5be23-164">Aşağıdaki örnek, özel durum işleme için zaman uyumsuz yöntemleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="5be23-164">The following example illustrates exception handling for async methods.</span></span> <span data-ttu-id="5be23-165">Zaman uyumsuz görev oluşturur bir özel durum çekmek için koyun `await` ifadesinde bir `try` engelleme ve catch özel durum bir `catch` bloğu.</span><span class="sxs-lookup"><span data-stu-id="5be23-165">To catch an exception that an async task throws, place the `await` expression in a `try` block, and catch the exception in a `catch` block.</span></span>  
  
 <span data-ttu-id="5be23-166">Açıklamadan çıkarın `throw new Exception` özel durum işleme göstermek için örnekte satır.</span><span class="sxs-lookup"><span data-stu-id="5be23-166">Uncomment the `throw new Exception` line in the example to demonstrate exception handling.</span></span> <span data-ttu-id="5be23-167">Görevin `IsFaulted` özelliği ayarlanmış `True`, görevin `Exception.InnerException` özelliği, özel durumu ayarlanır ve özel durumun yakalandığı `catch` bloğu.</span><span class="sxs-lookup"><span data-stu-id="5be23-167">The task's `IsFaulted` property is set to `True`, the task's `Exception.InnerException` property is set to the exception, and the exception is caught in the `catch` block.</span></span>  
  
 <span data-ttu-id="5be23-168">Açıklamadan çıkarın `throw new OperationCancelledException` satır zaman uyumsuz bir işlem iptal ettiğinizde ne olacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="5be23-168">Uncomment the `throw new OperationCancelledException` line to demonstrate what happens when you cancel an asynchronous process.</span></span> <span data-ttu-id="5be23-169">Görevin `IsCanceled` özelliği ayarlanmış `true`, ve özel durumun yakalandığı `catch` bloğu.</span><span class="sxs-lookup"><span data-stu-id="5be23-169">The task's `IsCanceled` property is set to `true`, and the exception is caught in the `catch` block.</span></span> <span data-ttu-id="5be23-170">Bu örnek için görev 's uygulanmaz bazı koşullarda `IsFaulted` özelliği ayarlanmış `true` ve `IsCanceled` ayarlanır `false`.</span><span class="sxs-lookup"><span data-stu-id="5be23-170">Under some conditions that don't apply to this example, the task's `IsFaulted` property is set to `true` and `IsCanceled` is set to `false`.</span></span>  
  
 [!code-csharp[csAsyncExceptions#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/try-catch_3.cs)]  
  
## <a name="example"></a><span data-ttu-id="5be23-171">Örnek</span><span class="sxs-lookup"><span data-stu-id="5be23-171">Example</span></span>  
 <span data-ttu-id="5be23-172">Aşağıdaki örnek, birden çok görev birden çok özel durumları burada sonuçlanabilir özel durum işleme gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="5be23-172">The following example illustrates exception handling where multiple tasks can result in multiple exceptions.</span></span> <span data-ttu-id="5be23-173">`try` Blok bekler yapılan bir çağrı tarafından döndürülen görev <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5be23-173">The `try` block awaits the task that's returned by a call to <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="5be23-174">WhenAll uygulandığı üç görevler tamamlandığında tam bir görevdir.</span><span class="sxs-lookup"><span data-stu-id="5be23-174">The task is complete when the three tasks to which WhenAll is applied are complete.</span></span>  
  
 <span data-ttu-id="5be23-175">Her biri üç görev bir özel durum oluşur.</span><span class="sxs-lookup"><span data-stu-id="5be23-175">Each of the three tasks causes an exception.</span></span> <span data-ttu-id="5be23-176">`catch` Blok tekrarlanan bulunan özel durumlar aracılığıyla `Exception.InnerExceptions` özellik tarafından döndürülen görev <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5be23-176">The `catch` block iterates through the exceptions, which are found in the `Exception.InnerExceptions` property of the task that was returned by <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>.</span></span>  
  
 [!code-csharp[csAsyncExceptions#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/try-catch_4.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="5be23-177">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="5be23-177">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5be23-178">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5be23-178">See Also</span></span>  
 [<span data-ttu-id="5be23-179">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="5be23-179">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="5be23-180">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="5be23-180">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="5be23-181">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="5be23-181">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="5be23-182">try, throw ve catch Deyimleri (C++)</span><span class="sxs-lookup"><span data-stu-id="5be23-182">try, throw, and catch Statements (C++)</span></span>](/cpp/cpp/try-throw-and-catch-statements-cpp)  
 [<span data-ttu-id="5be23-183">Özel Durum İşleme Deyimleri</span><span class="sxs-lookup"><span data-stu-id="5be23-183">Exception Handling Statements</span></span>](../../../csharp/language-reference/keywords/exception-handling-statements.md)  
 [<span data-ttu-id="5be23-184">throw</span><span class="sxs-lookup"><span data-stu-id="5be23-184">throw</span></span>](../../../csharp/language-reference/keywords/throw.md)  
 [<span data-ttu-id="5be23-185">try-finally</span><span class="sxs-lookup"><span data-stu-id="5be23-185">try-finally</span></span>](../../../csharp/language-reference/keywords/try-finally.md)  
 [<span data-ttu-id="5be23-186">Nasıl yapılır: Açıkça Özel Durumlar Oluşturma</span><span class="sxs-lookup"><span data-stu-id="5be23-186">How to: Explicitly Throw Exceptions</span></span>](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
