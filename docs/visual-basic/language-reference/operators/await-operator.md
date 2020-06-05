---
title: Await İşleci
ms.date: 07/20/2015
f1_keywords:
- vb.Await
helpviewer_keywords:
- Await operator [Visual Basic]
- Await [Visual Basic]
ms.assetid: 6b1ce283-e92b-4ba7-b081-7be7b3d37af9
ms.openlocfilehash: 9d55ba82547dfcb0336c3a3fd12521c0dcb3eb58
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84371836"
---
# <a name="await-operator-visual-basic"></a><span data-ttu-id="715bc-102">Await İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="715bc-102">Await Operator (Visual Basic)</span></span>

<span data-ttu-id="715bc-103">`Await` operatörünü awaited görevi tamamlanıncaya kadar, metodun yürütülmesini askıya almak için bir zaman uyumsuz metod veya lambda ifadesinde bir işlenene uygularsınız.</span><span class="sxs-lookup"><span data-stu-id="715bc-103">You apply the `Await` operator to an operand in an asynchronous method or lambda expression to suspend execution of the method until the awaited task completes.</span></span> <span data-ttu-id="715bc-104">Görev, devam eden işi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="715bc-104">The task represents ongoing work.</span></span>

<span data-ttu-id="715bc-105">' In kullanıldığı yöntemin `Await` [zaman uyumsuz](../modifiers/async.md) değiştiricisi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="715bc-105">The method in which `Await` is used must have an [Async](../modifiers/async.md) modifier.</span></span> <span data-ttu-id="715bc-106">Bu tür bir yöntem, değiştirici kullanılarak tanımlanır `Async` ve genellikle bir veya daha fazla ifade içeren bir `Await` *zaman uyumsuz yöntem*olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="715bc-106">Such a method, defined by using the `Async` modifier, and usually containing one or more `Await` expressions, is referred to as an *async method*.</span></span>

> [!NOTE]
> <span data-ttu-id="715bc-107">`Async`Ve `Await` anahtar sözcükleri Visual Studio 2012 ' de tanıtılmıştı.</span><span class="sxs-lookup"><span data-stu-id="715bc-107">The `Async` and `Await` keywords were introduced in Visual Studio 2012.</span></span> <span data-ttu-id="715bc-108">Zaman uyumsuz programlamaya giriş için bkz. [Async ve await Ile zaman uyumsuz programlama](../../programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="715bc-108">For an introduction to async programming, see [Asynchronous Programming with Async and Await](../../programming-guide/concepts/async/index.md).</span></span>

<span data-ttu-id="715bc-109">Genellikle, işlecini uyguladığınız görev, `Await` [görev tabanlı zaman uyumsuz model](https://www.microsoft.com/download/details.aspx?id=19957), yani, bir veya olarak uygulayan bir yönteme yapılan çağrıdan dönüş değeridir <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601> .</span><span class="sxs-lookup"><span data-stu-id="715bc-109">Typically, the task to which you apply the `Await` operator is the return value from a call to a method that implements the [Task-Based Asynchronous Pattern](https://www.microsoft.com/download/details.aspx?id=19957), that is, a <xref:System.Threading.Tasks.Task> or a <xref:System.Threading.Tasks.Task%601>.</span></span>

<span data-ttu-id="715bc-110">Aşağıdaki kodda, <xref:System.Net.Http.HttpClient> yöntemi <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A>, `getContentsTask`, bir `Task(Of Byte())` döndürür.</span><span class="sxs-lookup"><span data-stu-id="715bc-110">In the following code, the <xref:System.Net.Http.HttpClient> method <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> returns `getContentsTask`, a `Task(Of Byte())`.</span></span> <span data-ttu-id="715bc-111">Görev, işlem tamamlandığında gerçek bayt dizisini üretmek için bir vaattir.</span><span class="sxs-lookup"><span data-stu-id="715bc-111">The task is a promise to produce the actual byte array when the operation is complete.</span></span> <span data-ttu-id="715bc-112">`Await`İşleci `getContentsTask` tamamlanana kadar içinde yürütmeyi askıya almak için öğesine `SumPageSizesAsync` uygulanır `getContentsTask` .</span><span class="sxs-lookup"><span data-stu-id="715bc-112">The `Await` operator is applied to `getContentsTask` to suspend execution in `SumPageSizesAsync` until `getContentsTask` is complete.</span></span> <span data-ttu-id="715bc-113">Bu sırada denetim, çağıran öğesine döndürülür `SumPageSizesAsync` .</span><span class="sxs-lookup"><span data-stu-id="715bc-113">In the meantime, control is returned to the caller of `SumPageSizesAsync`.</span></span> <span data-ttu-id="715bc-114">`getContentsTask`Bittiğinde, `Await` ifade bir bayt dizisi olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="715bc-114">When `getContentsTask` is finished, the `Await` expression evaluates to a byte array.</span></span>

```vb
Private Async Function SumPageSizesAsync() As Task

    ' To use the HttpClient type in desktop apps, you must include a using directive and add a
    ' reference for the System.Net.Http namespace.
    Dim client As HttpClient = New HttpClient()
    ' . . .
    Dim getContentsTask As Task(Of Byte()) = client.GetByteArrayAsync(url)
    Dim urlContents As Byte() = Await getContentsTask

    ' Equivalently, now that you see how it works, you can write the same thing in a single line.
    'Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)
    ' . . .
End Function
```

> [!IMPORTANT]
> <span data-ttu-id="715bc-115">Tüm örnek için bkz. [Izlenecek yol: Async ve await kullanarak Web 'e erişme](../../programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="715bc-115">For the complete example, see [Walkthrough: Accessing the Web by Using Async and Await](../../programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span> <span data-ttu-id="715bc-116">Örneği, Microsoft Web sitesindeki [Geliştirici kodu örneklerinden](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f) indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="715bc-116">You can download the sample from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f) on the Microsoft website.</span></span> <span data-ttu-id="715bc-117">Örnek, AsyncWalkthrough_HttpClient projem.</span><span class="sxs-lookup"><span data-stu-id="715bc-117">The example is in the AsyncWalkthrough_HttpClient project.</span></span>

<span data-ttu-id="715bc-118">`Await` getiren bir metot çağrısının sonucuna `Task(Of TResult)` uygulanırsa, `Await` ifadesinin türü TResult olur.</span><span class="sxs-lookup"><span data-stu-id="715bc-118">If `Await` is applied to the result of a method call that returns a `Task(Of TResult)`, the type of the `Await` expression is TResult.</span></span> <span data-ttu-id="715bc-119">`Await`, bir `Task` getiren bir metot çağrısının sonucuna uygulanırsa, `Await` ifadesi bir değer getirmez.</span><span class="sxs-lookup"><span data-stu-id="715bc-119">If `Await` is applied to the result of a method call that returns a `Task`, the `Await` expression doesn't return a value.</span></span> <span data-ttu-id="715bc-120">Aşağıdaki örnek, farkı göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="715bc-120">The following example illustrates the difference.</span></span>

```vb
' Await used with a method that returns a Task(Of TResult).
Dim result As TResult = Await AsyncMethodThatReturnsTaskTResult()

' Await used with a method that returns a Task.
Await AsyncMethodThatReturnsTask()
```

<span data-ttu-id="715bc-121">Bir `Await` ifadesi veya açıklaması, üzerinde yürütme yaptığı iş parçacığını engellemez.</span><span class="sxs-lookup"><span data-stu-id="715bc-121">An `Await` expression or statement does not block the thread on which it is executing.</span></span> <span data-ttu-id="715bc-122">Bunun yerine, `Await` ifadesinden sonra, bekleyen görevlerin bir devamı olarak, derleyicinin zaman uyumsuz yöntemin geri kalanını imzalamasına yol açar.</span><span class="sxs-lookup"><span data-stu-id="715bc-122">Instead, it causes the compiler to sign up the rest of the async method, after the `Await` expression, as a continuation on the awaited task.</span></span> <span data-ttu-id="715bc-123">Sonra Denetim zaman uyumsuz yöntemi çağırana döner.</span><span class="sxs-lookup"><span data-stu-id="715bc-123">Control then returns to the caller of the async method.</span></span> <span data-ttu-id="715bc-124">Görev tamamlandığında, devamlılığını çağırır ve zaman uyumsuz yöntemin yürütülmesi kaldığınız yerden devam eder.</span><span class="sxs-lookup"><span data-stu-id="715bc-124">When the task completes, it invokes its continuation, and execution of the async method resumes where it left off.</span></span>

<span data-ttu-id="715bc-125">Bir `Await` ifadesi yalnızca bir `Async` değiştiricisiyle işaretlenmiş bir anında kapatma metodunun veya lambda ifadesinin gövdesinde gerçekleşebilir.</span><span class="sxs-lookup"><span data-stu-id="715bc-125">An `Await` expression can occur only in the body of an immediately enclosing method or lambda expression that is marked by an `Async` modifier.</span></span> <span data-ttu-id="715bc-126">*Await* terimi yalnızca söz konusu bağlamda anahtar sözcük olarak işlev görür.</span><span class="sxs-lookup"><span data-stu-id="715bc-126">The term *Await* serves as a keyword only in that context.</span></span> <span data-ttu-id="715bc-127">Başka bir yerde, tanımlayıcı olarak yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="715bc-127">Elsewhere, it is interpreted as an identifier.</span></span> <span data-ttu-id="715bc-128">`Async`Yöntem veya lambda ifadesinde bir `Await` ifade, `Catch` `Finally` bir [TRY... içinde veya bloğunda bir sorgu ifadesinde gerçekleşemez. Yakala... Finally deyimi](../statements/try-catch-finally-statement.md), bir veya döngüsünün döngü denetim değişkeni ifadesinde `For` `For Each` veya bir [SyncLock](../statements/synclock-statement.md) deyiminin gövdesinde.</span><span class="sxs-lookup"><span data-stu-id="715bc-128">Within the `Async` method or lambda expression, an `Await` expression cannot occur in a query expression, in the `Catch` or `Finally` block of a [Try…Catch…Finally statement](../statements/try-catch-finally-statement.md), in the loop control variable expression of a `For` or `For Each` loop, or in the body of a [SyncLock](../statements/synclock-statement.md) statement.</span></span>

## <a name="exceptions"></a><span data-ttu-id="715bc-129">Özel durumlar</span><span class="sxs-lookup"><span data-stu-id="715bc-129">Exceptions</span></span>

<span data-ttu-id="715bc-130">En zaman uyumsuz yöntemler bir <xref:System.Threading.Tasks.Task> veya döndürür <xref:System.Threading.Tasks.Task%601> .</span><span class="sxs-lookup"><span data-stu-id="715bc-130">Most async methods return a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="715bc-131">Döndürülen görevin özellikleri, görevin tamamlanıp tamamlanmayacağı, zaman uyumsuz yöntemin bir özel durum mi olduğunu, yoksa iptal edildiğini mi olduğunu ve nihai sonucun ne olduğunu belirtir gibi durum ve geçmişi hakkındaki bilgileri taşır.</span><span class="sxs-lookup"><span data-stu-id="715bc-131">The properties of the returned task carry information about its status and history, such as whether the task is complete, whether the async method caused an exception or was canceled, and what the final result is.</span></span> <span data-ttu-id="715bc-132">`Await`İşleci bu özelliklere erişir.</span><span class="sxs-lookup"><span data-stu-id="715bc-132">The `Await` operator accesses those properties.</span></span>

<span data-ttu-id="715bc-133">Bir özel duruma neden olan bir görev döndüren zaman uyumsuz yöntemi beklelerseniz, `Await` işleç özel durumu yeniden oluşturur.</span><span class="sxs-lookup"><span data-stu-id="715bc-133">If you await a task-returning async method that causes an exception, the  `Await` operator rethrows the exception.</span></span>

<span data-ttu-id="715bc-134">İptal edilen bir görev döndüren zaman uyumsuz yöntemi beklerseniz, `Await` operatörü yeniden bir <xref:System.OperationCanceledException> oluşturur.</span><span class="sxs-lookup"><span data-stu-id="715bc-134">If you await a task-returning async method that is canceled, the `Await` operator rethrows an <xref:System.OperationCanceledException>.</span></span>

<span data-ttu-id="715bc-135">Hatalı durumda olan tek bir görev birden çok özel durumu yansıtabilir.</span><span class="sxs-lookup"><span data-stu-id="715bc-135">A single task that is in a faulted state can reflect multiple exceptions.</span></span>  <span data-ttu-id="715bc-136">Örneğin, görev bir çağrısının sonucu olabilir <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="715bc-136">For example, the task might be the result of a call to <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="715bc-137">Böyle bir görevi beklelerseniz, await işlemi özel durumların yalnızca birini yeniden oluşturur.</span><span class="sxs-lookup"><span data-stu-id="715bc-137">When you await such a task, the await operation rethrows only one of the exceptions.</span></span> <span data-ttu-id="715bc-138">Ancak, özel durumların hangisinin yeniden oluşturulduğu tahmin edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="715bc-138">However, you can't predict which of the exceptions is rethrown.</span></span>

<span data-ttu-id="715bc-139">Zaman uyumsuz yöntemlerde hata işleme örnekleri için bkz [. TRY... Yakala... Finally ekstresi](../statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="715bc-139">For examples of error handling in async methods, see [Try...Catch...Finally Statement](../statements/try-catch-finally-statement.md).</span></span>

## <a name="example"></a><span data-ttu-id="715bc-140">Örnek</span><span class="sxs-lookup"><span data-stu-id="715bc-140">Example</span></span>

<span data-ttu-id="715bc-141">Aşağıdaki Windows Forms örnek, `Await` zaman uyumsuz bir yöntemde kullanımını gösterir `WaitAsynchronouslyAsync` .</span><span class="sxs-lookup"><span data-stu-id="715bc-141">The following Windows Forms example illustrates the use of `Await` in an async method, `WaitAsynchronouslyAsync`.</span></span> <span data-ttu-id="715bc-142">Davranışı ile bu yöntemin davranışını kontrast `WaitSynchronously` .</span><span class="sxs-lookup"><span data-stu-id="715bc-142">Contrast the behavior of that method with the behavior of `WaitSynchronously`.</span></span> <span data-ttu-id="715bc-143">Bir `Await` operatörü olmadan, `WaitSynchronously` zaman uyumlu olarak çalışır, tanımında `Async` değiştiricisinin ve gövdesinde bir <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> çağrısı kullanılmasına rağmen.</span><span class="sxs-lookup"><span data-stu-id="715bc-143">Without an `Await` operator, `WaitSynchronously` runs synchronously despite the use of the `Async` modifier in its definition and a call to <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> in its body.</span></span>

```vb
Private Async Sub Button1_Click(sender As Object, e As EventArgs) Handles Button1.Click
    ' Call the method that runs asynchronously.
    Dim result As String = Await WaitAsynchronouslyAsync()

    ' Call the method that runs synchronously.
    'Dim result As String = Await WaitSynchronously()

    ' Display the result.
    TextBox1.Text &= result
End Sub

' The following method runs asynchronously. The UI thread is not
' blocked during the delay. You can move or resize the Form1 window
' while Task.Delay is running.
Public Async Function WaitAsynchronouslyAsync() As Task(Of String)
    Await Task.Delay(10000)
    Return "Finished"
End Function

' The following method runs synchronously, despite the use of Async.
' You cannot move or resize the Form1 window while Thread.Sleep
' is running because the UI thread is blocked.
Public Async Function WaitSynchronously() As Task(Of String)
    ' Import System.Threading for the Sleep method.
    Thread.Sleep(10000)
    Return "Finished"
End Function
```

## <a name="see-also"></a><span data-ttu-id="715bc-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="715bc-144">See also</span></span>

- [<span data-ttu-id="715bc-145">Async ve await ile zaman uyumsuz programlama</span><span class="sxs-lookup"><span data-stu-id="715bc-145">Asynchronous Programming with Async and Await</span></span>](../../programming-guide/concepts/async/index.md)
- [<span data-ttu-id="715bc-146">İzlenecek yol: Async ve await kullanarak Web 'e erişme</span><span class="sxs-lookup"><span data-stu-id="715bc-146">Walkthrough: Accessing the Web by Using Async and Await</span></span>](../../programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="715bc-147">Eş</span><span class="sxs-lookup"><span data-stu-id="715bc-147">Async</span></span>](../modifiers/async.md)
