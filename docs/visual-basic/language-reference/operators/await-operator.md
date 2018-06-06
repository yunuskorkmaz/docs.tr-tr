---
title: Await İşleci (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Await
helpviewer_keywords:
- Await operator [Visual Basic]
- Await [Visual Basic]
ms.assetid: 6b1ce283-e92b-4ba7-b081-7be7b3d37af9
ms.openlocfilehash: 8e1462c7e0097bb2f04c6833a1bb279611b24133
ms.sourcegitcommit: fc70fcb9c789b6a4aefcdace46f3643fd076450f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2018
ms.locfileid: "34805516"
---
# <a name="await-operator-visual-basic"></a><span data-ttu-id="9a9d9-102">Await İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9a9d9-102">Await Operator (Visual Basic)</span></span>
<span data-ttu-id="9a9d9-103">`Await` operatörünü awaited görevi tamamlanıncaya kadar, metodun yürütülmesini askıya almak için bir zaman uyumsuz metod veya lambda ifadesinde bir işlenene uygularsınız.</span><span class="sxs-lookup"><span data-stu-id="9a9d9-103">You apply the `Await` operator to an operand in an asynchronous method or lambda expression to suspend execution of the method until the awaited task completes.</span></span> <span data-ttu-id="9a9d9-104">Görev devam eden iş temsil eder.</span><span class="sxs-lookup"><span data-stu-id="9a9d9-104">The task represents ongoing work.</span></span>  
  
 <span data-ttu-id="9a9d9-105">Yönteminde `Await` kullanılan olmalıdır bir [zaman uyumsuz](../../../visual-basic/language-reference/modifiers/async.md) değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="9a9d9-105">The method in which `Await` is used must have an [Async](../../../visual-basic/language-reference/modifiers/async.md) modifier.</span></span> <span data-ttu-id="9a9d9-106">Kullanılarak tanımlanmış böyle bir yöntemi, `Async` değiştiricisi ve genellikle içeren bir veya daha fazla `Await` ifadeleri olarak adlandırılır bir *async yöntemi*.</span><span class="sxs-lookup"><span data-stu-id="9a9d9-106">Such a method, defined by using the `Async` modifier, and usually containing one or more `Await` expressions, is referred to as an *async method*.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9a9d9-107">`Async` Ve `Await` anahtar sözcükler, Visual Studio 2012'de sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="9a9d9-107">The `Async` and `Await` keywords were introduced in Visual Studio 2012.</span></span> <span data-ttu-id="9a9d9-108">Zaman uyumsuz programlamaya giriş için bkz: [uyumsuz ve bekleme ile zaman uyumsuz programlama](../../../visual-basic/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="9a9d9-108">For an introduction to async programming, see [Asynchronous Programming with Async and Await](../../../visual-basic/programming-guide/concepts/async/index.md).</span></span>  
  
 <span data-ttu-id="9a9d9-109">Genellikle, uygulama, görev `Await` işlecidir uygulayan bir yöntem çağrısından dönüş değeri [görev tabanlı zaman uyumsuz desen](http://go.microsoft.com/fwlink/?LinkId=204847), diğer bir deyişle, bir <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="9a9d9-109">Typically, the task to which you apply the `Await` operator is the return value from a call to a method that implements the [Task-Based Asynchronous Pattern](http://go.microsoft.com/fwlink/?LinkId=204847), that is, a <xref:System.Threading.Tasks.Task> or a <xref:System.Threading.Tasks.Task%601>.</span></span>  
  
 <span data-ttu-id="9a9d9-110">Aşağıdaki kodda, <xref:System.Net.Http.HttpClient> yöntemi <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A>, `getContentsTask`, bir `Task(Of Byte())` döndürür.</span><span class="sxs-lookup"><span data-stu-id="9a9d9-110">In the following code, the <xref:System.Net.Http.HttpClient> method <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> returns `getContentsTask`, a `Task(Of Byte())`.</span></span> <span data-ttu-id="9a9d9-111">Görev, işlem tamamlandığında gerçek bayt dizisini üretmek için bir vaattir.</span><span class="sxs-lookup"><span data-stu-id="9a9d9-111">The task is a promise to produce the actual byte array when the operation is complete.</span></span> <span data-ttu-id="9a9d9-112">`Await` İşleci uygulanan `getContentsTask` yürütme askıya almak için `SumPageSizesAsync` kadar `getContentsTask` tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="9a9d9-112">The `Await` operator is applied to `getContentsTask` to suspend execution in `SumPageSizesAsync` until `getContentsTask` is complete.</span></span> <span data-ttu-id="9a9d9-113">Bu arada, Denetim çağırana döndürülen `SumPageSizesAsync`.</span><span class="sxs-lookup"><span data-stu-id="9a9d9-113">In the meantime, control is returned to the caller of `SumPageSizesAsync`.</span></span> <span data-ttu-id="9a9d9-114">Zaman `getContentsTask` tamamlandı, `Await` ifadeyi hesaplar bir bayt dizisi.</span><span class="sxs-lookup"><span data-stu-id="9a9d9-114">When `getContentsTask` is finished, the `Await` expression evaluates to a byte array.</span></span>  
  
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
>  <span data-ttu-id="9a9d9-115">Tam bir örnek için bkz: [izlenecek yol: Web kullanarak zaman uyumsuz ve bekleme tarafından erişme](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="9a9d9-115">For the complete example, see [Walkthrough: Accessing the Web by Using Async and Await](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span> <span data-ttu-id="9a9d9-116">Örnekten indirebilirsiniz [Geliştirici kod örnekleri](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f) Microsoft Web sitesinde.</span><span class="sxs-lookup"><span data-stu-id="9a9d9-116">You can download the sample from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f) on the Microsoft website.</span></span> <span data-ttu-id="9a9d9-117">AsyncWalkthrough_HttpClient projesinde örnektir.</span><span class="sxs-lookup"><span data-stu-id="9a9d9-117">The example is in the AsyncWalkthrough_HttpClient project.</span></span>  
  
 <span data-ttu-id="9a9d9-118">`Await` getiren bir metot çağrısının sonucuna `Task(Of TResult)` uygulanırsa, `Await` ifadesinin türü TResult olur.</span><span class="sxs-lookup"><span data-stu-id="9a9d9-118">If `Await` is applied to the result of a method call that returns a `Task(Of TResult)`, the type of the `Await` expression is TResult.</span></span> <span data-ttu-id="9a9d9-119">`Await`, bir `Task` getiren bir metot çağrısının sonucuna uygulanırsa, `Await` ifadesi bir değer getirmez.</span><span class="sxs-lookup"><span data-stu-id="9a9d9-119">If `Await` is applied to the result of a method call that returns a `Task`, the `Await` expression doesn't return a value.</span></span> <span data-ttu-id="9a9d9-120">Aşağıdaki örnek fark gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="9a9d9-120">The following example illustrates the difference.</span></span>  
  
```vb  
' Await used with a method that returns a Task(Of TResult).  
Dim result As TResult = Await AsyncMethodThatReturnsTaskTResult()  
  
' Await used with a method that returns a Task.  
Await AsyncMethodThatReturnsTask()  
```  
  
 <span data-ttu-id="9a9d9-121">Bir `Await` ifadesi veya açıklaması, üzerinde yürütme yaptığı iş parçacığını engellemez.</span><span class="sxs-lookup"><span data-stu-id="9a9d9-121">An `Await` expression or statement does not block the thread on which it is executing.</span></span> <span data-ttu-id="9a9d9-122">Bunun yerine, `Await` ifadesinden sonra, bekleyen görevlerin bir devamı olarak, derleyicinin zaman uyumsuz yöntemin geri kalanını imzalamasına yol açar.</span><span class="sxs-lookup"><span data-stu-id="9a9d9-122">Instead, it causes the compiler to sign up the rest of the async method, after the `Await` expression, as a continuation on the awaited task.</span></span> <span data-ttu-id="9a9d9-123">Denetim ardından async yöntemi çağırana döndürür.</span><span class="sxs-lookup"><span data-stu-id="9a9d9-123">Control then returns to the caller of the async method.</span></span> <span data-ttu-id="9a9d9-124">Görev tamamlandığında, devamlılık ve kaldığı yerden zaman uyumsuz yöntem sürdürür yürütülmesi çağırır.</span><span class="sxs-lookup"><span data-stu-id="9a9d9-124">When the task completes, it invokes its continuation, and execution of the async method resumes where it left off.</span></span>  
  
 <span data-ttu-id="9a9d9-125">Bir `Await` ifadesi yalnızca bir `Async` değiştiricisiyle işaretlenmiş bir anında kapatma metodunun veya lambda ifadesinin gövdesinde gerçekleşebilir.</span><span class="sxs-lookup"><span data-stu-id="9a9d9-125">An `Await` expression can occur only in the body of an immediately enclosing method or lambda expression that is marked by an `Async` modifier.</span></span> <span data-ttu-id="9a9d9-126">Terim *bekleme* bu bağlamda yalnızca bir anahtar sözcük görevi görür.</span><span class="sxs-lookup"><span data-stu-id="9a9d9-126">The term *Await* serves as a keyword only in that context.</span></span> <span data-ttu-id="9a9d9-127">Başka bir yerde bir tanımlayıcı olarak yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="9a9d9-127">Elsewhere, it is interpreted as an identifier.</span></span> <span data-ttu-id="9a9d9-128">Zaman uyumsuz yöntem veya lambda ifadesinde bulunan bir `Await` ifadesi bir sorgu ifadesinde gerçekleşemez `catch` veya `finally` , engelleme bir [deneyin... Catch... Son olarak](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md) ifadesinde döngüsü denetim değişkeni deyimi bir `For` veya `For Each` döngüsü veya gövdesinde bir [SyncLock](../../../visual-basic/language-reference/statements/synclock-statement.md) deyimi.</span><span class="sxs-lookup"><span data-stu-id="9a9d9-128">Within the async method or lambda expression, an `Await` expression cannot occur in a query expression, in the `catch` or `finally` block of a [Try…Catch…Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md) statement, in the loop control variable expression of a `For` or `For Each` loop, or in the body of a [SyncLock](../../../visual-basic/language-reference/statements/synclock-statement.md) statement.</span></span>  
  
## <a name="exceptions"></a><span data-ttu-id="9a9d9-129">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="9a9d9-129">Exceptions</span></span>  
 <span data-ttu-id="9a9d9-130">Çoğu zaman uyumsuz yöntemleri döndürür bir <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="9a9d9-130">Most async methods return a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="9a9d9-131">Döndürülen görev özelliklerini durumunu ve görevin tam olup, async yöntemi bir özel durum nedeniyle veya iptal edildi ve son sonucu gibi geçmişi hakkında bilgi taşır.</span><span class="sxs-lookup"><span data-stu-id="9a9d9-131">The properties of the returned task carry information about its status and history, such as whether the task is complete, whether the async method caused an exception or was canceled, and what the final result is.</span></span> <span data-ttu-id="9a9d9-132">`Await` İşleci bu özellikleri erişir.</span><span class="sxs-lookup"><span data-stu-id="9a9d9-132">The `Await` operator accesses those properties.</span></span>  
  
 <span data-ttu-id="9a9d9-133">Bir özel duruma neden olan görev döndüren bir zaman uyumsuz yöntem bekleme durumunda `Await` işleci özel durumu yeniden oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9a9d9-133">If you await a task-returning async method that causes an exception, the  `Await` operator rethrows the exception.</span></span>  
  
 <span data-ttu-id="9a9d9-134">İptal edilen bir görev döndüren zaman uyumsuz yöntemi beklerseniz, `Await` operatörü yeniden bir <xref:System.OperationCanceledException> oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9a9d9-134">If you await a task-returning async method that is canceled, the `Await` operator rethrows an <xref:System.OperationCanceledException>.</span></span>  
  
 <span data-ttu-id="9a9d9-135">Hatalı durumda tek bir görevi birden fazla özel yansıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9a9d9-135">A single task that is in a faulted state can reflect multiple exceptions.</span></span>  <span data-ttu-id="9a9d9-136">Örneğin, görev için bir çağrı sonucunu olabilir <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="9a9d9-136">For example, the task might be the result of a call to <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="9a9d9-137">Bu tür bir görev bekleme zaman bekleme işlemi yalnızca bir özel durum yeniden oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9a9d9-137">When you await such a task, the await operation rethrows only one of the exceptions.</span></span> <span data-ttu-id="9a9d9-138">Ancak, özel durumlar hangisinin işlenemezse tahmin edilemez.</span><span class="sxs-lookup"><span data-stu-id="9a9d9-138">However, you can't predict which of the exceptions is rethrown.</span></span>  
  
 <span data-ttu-id="9a9d9-139">Zaman uyumsuz yöntemleri işleme hatası örnekleri için bkz: [deneyin... Catch... Finally ifadesi](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="9a9d9-139">For examples of error handling in async methods, see [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9a9d9-140">Örnek</span><span class="sxs-lookup"><span data-stu-id="9a9d9-140">Example</span></span>  
 <span data-ttu-id="9a9d9-141">Aşağıdaki Windows Forms örnek kullanımını göstermektedir `Await` bir zaman uyumsuz yöntem `WaitAsynchronouslyAsync`.</span><span class="sxs-lookup"><span data-stu-id="9a9d9-141">The following Windows Forms example illustrates the use of `Await` in an async method, `WaitAsynchronouslyAsync`.</span></span> <span data-ttu-id="9a9d9-142">Bu yöntem davranışını davranışını ile karşılaştırın `WaitSynchronously`.</span><span class="sxs-lookup"><span data-stu-id="9a9d9-142">Contrast the behavior of that method with the behavior of `WaitSynchronously`.</span></span> <span data-ttu-id="9a9d9-143">Bir `Await` operatörü olmadan, `WaitSynchronously` zaman uyumlu olarak çalışır, tanımında `Async` değiştiricisinin ve gövdesinde bir <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> çağrısı kullanılmasına rağmen.</span><span class="sxs-lookup"><span data-stu-id="9a9d9-143">Without an `Await` operator, `WaitSynchronously` runs synchronously despite the use of the `Async` modifier in its definition and a call to <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> in its body.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9a9d9-144">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9a9d9-144">See Also</span></span>  
 [<span data-ttu-id="9a9d9-145">Async ve Await ile Zaman Uyumsuz Programlama</span><span class="sxs-lookup"><span data-stu-id="9a9d9-145">Asynchronous Programming with Async and Await</span></span>](../../../visual-basic/programming-guide/concepts/async/index.md)  
 [<span data-ttu-id="9a9d9-146">İzlenecek yol: Async ve Await Kullanarak Web'e Erişme</span><span class="sxs-lookup"><span data-stu-id="9a9d9-146">Walkthrough: Accessing the Web by Using Async and Await</span></span>](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)  
 [<span data-ttu-id="9a9d9-147">Async</span><span class="sxs-lookup"><span data-stu-id="9a9d9-147">Async</span></span>](../../../visual-basic/language-reference/modifiers/async.md)
