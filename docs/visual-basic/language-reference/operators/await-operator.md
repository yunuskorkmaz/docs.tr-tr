---
title: Await İşleci (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Await
helpviewer_keywords:
- Await operator [Visual Basic]
- Await [Visual Basic]
ms.assetid: 6b1ce283-e92b-4ba7-b081-7be7b3d37af9
ms.openlocfilehash: 2094ba308ba384feb8542e896cb1eafcf645947c
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43524472"
---
# <a name="await-operator-visual-basic"></a><span data-ttu-id="edfaf-102">Await İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="edfaf-102">Await Operator (Visual Basic)</span></span>
<span data-ttu-id="edfaf-103">`Await` operatörünü awaited görevi tamamlanıncaya kadar, metodun yürütülmesini askıya almak için bir zaman uyumsuz metod veya lambda ifadesinde bir işlenene uygularsınız.</span><span class="sxs-lookup"><span data-stu-id="edfaf-103">You apply the `Await` operator to an operand in an asynchronous method or lambda expression to suspend execution of the method until the awaited task completes.</span></span> <span data-ttu-id="edfaf-104">Görev, devam eden çalışmayı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="edfaf-104">The task represents ongoing work.</span></span>  
  
 <span data-ttu-id="edfaf-105">Yöntem `Await` kullanılan olmalıdır bir [zaman uyumsuz](../../../visual-basic/language-reference/modifiers/async.md) değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="edfaf-105">The method in which `Await` is used must have an [Async](../../../visual-basic/language-reference/modifiers/async.md) modifier.</span></span> <span data-ttu-id="edfaf-106">Tarafından tanımlanan tür bir yöntem, `Async` değiştiricisi ve genellikle içeren bir veya daha fazla `Await` ifadeleri olarak adlandırılır bir *zaman uyumsuz yöntem*.</span><span class="sxs-lookup"><span data-stu-id="edfaf-106">Such a method, defined by using the `Async` modifier, and usually containing one or more `Await` expressions, is referred to as an *async method*.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="edfaf-107">`Async` Ve `Await` anahtar sözcükleri Visual Studio 2012'de kullanıma sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="edfaf-107">The `Async` and `Await` keywords were introduced in Visual Studio 2012.</span></span> <span data-ttu-id="edfaf-108">Zaman uyumsuz programlamaya giriş için bkz [Async ve Await ile zaman uyumsuz programlama](../../../visual-basic/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="edfaf-108">For an introduction to async programming, see [Asynchronous Programming with Async and Await](../../../visual-basic/programming-guide/concepts/async/index.md).</span></span>  
  
 <span data-ttu-id="edfaf-109">Genellikle, uyguladığınız görev `Await` işleci uygulayan bir Metoda bir çağrıdan dönüş değeridir [görev tabanlı zaman uyumsuz desen](https://go.microsoft.com/fwlink/?LinkId=204847), diğer bir deyişle, bir <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="edfaf-109">Typically, the task to which you apply the `Await` operator is the return value from a call to a method that implements the [Task-Based Asynchronous Pattern](https://go.microsoft.com/fwlink/?LinkId=204847), that is, a <xref:System.Threading.Tasks.Task> or a <xref:System.Threading.Tasks.Task%601>.</span></span>  
  
 <span data-ttu-id="edfaf-110">Aşağıdaki kodda, <xref:System.Net.Http.HttpClient> yöntemi <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A>, `getContentsTask`, bir `Task(Of Byte())` döndürür.</span><span class="sxs-lookup"><span data-stu-id="edfaf-110">In the following code, the <xref:System.Net.Http.HttpClient> method <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> returns `getContentsTask`, a `Task(Of Byte())`.</span></span> <span data-ttu-id="edfaf-111">Görev, işlem tamamlandığında gerçek bayt dizisini üretmek için bir vaattir.</span><span class="sxs-lookup"><span data-stu-id="edfaf-111">The task is a promise to produce the actual byte array when the operation is complete.</span></span> <span data-ttu-id="edfaf-112">`Await` İşleci uygulanır `getContentsTask` içindeki yürütmeyi askıya almak için `SumPageSizesAsync` kadar `getContentsTask` tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="edfaf-112">The `Await` operator is applied to `getContentsTask` to suspend execution in `SumPageSizesAsync` until `getContentsTask` is complete.</span></span> <span data-ttu-id="edfaf-113">Bu sırada, Denetim çağırana döndürülmeden `SumPageSizesAsync`.</span><span class="sxs-lookup"><span data-stu-id="edfaf-113">In the meantime, control is returned to the caller of `SumPageSizesAsync`.</span></span> <span data-ttu-id="edfaf-114">Zaman `getContentsTask` bittiğinde `Await` ifadesi bir bayt dizisine değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="edfaf-114">When `getContentsTask` is finished, the `Await` expression evaluates to a byte array.</span></span>  
  
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
>  <span data-ttu-id="edfaf-115">Tam bir örnek için bkz. [izlenecek yol: Web kullanarak Async ve Await tarafından erişim](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="edfaf-115">For the complete example, see [Walkthrough: Accessing the Web by Using Async and Await](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span> <span data-ttu-id="edfaf-116">İçinden örneği karşıdan yükleyebilirsiniz [geliştirici kodu örnekleri](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f) Microsoft Web sitesinde.</span><span class="sxs-lookup"><span data-stu-id="edfaf-116">You can download the sample from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f) on the Microsoft website.</span></span> <span data-ttu-id="edfaf-117">Örnek AsyncWalkthrough_HttpClient projesindedir.</span><span class="sxs-lookup"><span data-stu-id="edfaf-117">The example is in the AsyncWalkthrough_HttpClient project.</span></span>  
  
 <span data-ttu-id="edfaf-118">`Await` getiren bir metot çağrısının sonucuna `Task(Of TResult)` uygulanırsa, `Await` ifadesinin türü TResult olur.</span><span class="sxs-lookup"><span data-stu-id="edfaf-118">If `Await` is applied to the result of a method call that returns a `Task(Of TResult)`, the type of the `Await` expression is TResult.</span></span> <span data-ttu-id="edfaf-119">`Await`, bir `Task` getiren bir metot çağrısının sonucuna uygulanırsa, `Await` ifadesi bir değer getirmez.</span><span class="sxs-lookup"><span data-stu-id="edfaf-119">If `Await` is applied to the result of a method call that returns a `Task`, the `Await` expression doesn't return a value.</span></span> <span data-ttu-id="edfaf-120">Fark aşağıdaki örnekte gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="edfaf-120">The following example illustrates the difference.</span></span>  
  
```vb  
' Await used with a method that returns a Task(Of TResult).  
Dim result As TResult = Await AsyncMethodThatReturnsTaskTResult()  
  
' Await used with a method that returns a Task.  
Await AsyncMethodThatReturnsTask()  
```  
  
 <span data-ttu-id="edfaf-121">Bir `Await` ifadesi veya açıklaması, üzerinde yürütme yaptığı iş parçacığını engellemez.</span><span class="sxs-lookup"><span data-stu-id="edfaf-121">An `Await` expression or statement does not block the thread on which it is executing.</span></span> <span data-ttu-id="edfaf-122">Bunun yerine, `Await` ifadesinden sonra, bekleyen görevlerin bir devamı olarak, derleyicinin zaman uyumsuz yöntemin geri kalanını imzalamasına yol açar.</span><span class="sxs-lookup"><span data-stu-id="edfaf-122">Instead, it causes the compiler to sign up the rest of the async method, after the `Await` expression, as a continuation on the awaited task.</span></span> <span data-ttu-id="edfaf-123">Denetim, ardından zaman uyumsuz yöntemini çağırana döner.</span><span class="sxs-lookup"><span data-stu-id="edfaf-123">Control then returns to the caller of the async method.</span></span> <span data-ttu-id="edfaf-124">Görev tamamlandığında, devamlılık ve yürütülmesi kaldığı zaman uyumsuz yöntem sürdürür çağırır.</span><span class="sxs-lookup"><span data-stu-id="edfaf-124">When the task completes, it invokes its continuation, and execution of the async method resumes where it left off.</span></span>  
  
 <span data-ttu-id="edfaf-125">Bir `Await` ifadesi yalnızca bir `Async` değiştiricisiyle işaretlenmiş bir anında kapatma metodunun veya lambda ifadesinin gövdesinde gerçekleşebilir.</span><span class="sxs-lookup"><span data-stu-id="edfaf-125">An `Await` expression can occur only in the body of an immediately enclosing method or lambda expression that is marked by an `Async` modifier.</span></span> <span data-ttu-id="edfaf-126">Terim *Await* yalnızca bu bağlamda bir anahtar sözcük görevi görür.</span><span class="sxs-lookup"><span data-stu-id="edfaf-126">The term *Await* serves as a keyword only in that context.</span></span> <span data-ttu-id="edfaf-127">Başka bir yerde, tanımlayıcı olarak yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="edfaf-127">Elsewhere, it is interpreted as an identifier.</span></span> <span data-ttu-id="edfaf-128">Zaman uyumsuz yöntem veya lambda ifadesinde bulunan bir `Await` ifade içinde bir sorgu ifadesinde gerçekleşemez `catch` veya `finally` bloğu bir [deneyin... Catch... Son olarak](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md) deyiminde döngü denetimi değişkeni ifadesinde bir `For` veya `For Each` döngü gövdesinde veya bir [SyncLock](../../../visual-basic/language-reference/statements/synclock-statement.md) deyimi.</span><span class="sxs-lookup"><span data-stu-id="edfaf-128">Within the async method or lambda expression, an `Await` expression cannot occur in a query expression, in the `catch` or `finally` block of a [Try…Catch…Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md) statement, in the loop control variable expression of a `For` or `For Each` loop, or in the body of a [SyncLock](../../../visual-basic/language-reference/statements/synclock-statement.md) statement.</span></span>  
  
## <a name="exceptions"></a><span data-ttu-id="edfaf-129">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="edfaf-129">Exceptions</span></span>  
 <span data-ttu-id="edfaf-130">Çoğu zaman uyumsuz yöntemlerin dönüş bir <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="edfaf-130">Most async methods return a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="edfaf-131">Döndürülen görevin özelliklerini, durumunu ve geçmişini, görevin tam olup olmadığı, zaman uyumsuz yöntemin bir özel duruma neden oldu veya iptal edildi ve nihai sonucun ne olduğu gibi hakkında bilgi getirir.</span><span class="sxs-lookup"><span data-stu-id="edfaf-131">The properties of the returned task carry information about its status and history, such as whether the task is complete, whether the async method caused an exception or was canceled, and what the final result is.</span></span> <span data-ttu-id="edfaf-132">`Await` İşleci, özelliklere erişir.</span><span class="sxs-lookup"><span data-stu-id="edfaf-132">The `Await` operator accesses those properties.</span></span>  
  
 <span data-ttu-id="edfaf-133">Bir özel durum neden olan bir görev döndüren zaman uyumsuz yöntem, `Await` işleci özel durumu yeniden oluşturur.</span><span class="sxs-lookup"><span data-stu-id="edfaf-133">If you await a task-returning async method that causes an exception, the  `Await` operator rethrows the exception.</span></span>  
  
 <span data-ttu-id="edfaf-134">İptal edilen bir görev döndüren zaman uyumsuz yöntemi beklerseniz, `Await` operatörü yeniden bir <xref:System.OperationCanceledException> oluşturur.</span><span class="sxs-lookup"><span data-stu-id="edfaf-134">If you await a task-returning async method that is canceled, the `Await` operator rethrows an <xref:System.OperationCanceledException>.</span></span>  
  
 <span data-ttu-id="edfaf-135">Hatalı bir durumda olan tek bir görev birden çok özel durumu yansıtabilir.</span><span class="sxs-lookup"><span data-stu-id="edfaf-135">A single task that is in a faulted state can reflect multiple exceptions.</span></span>  <span data-ttu-id="edfaf-136">Örneğin, görev yapılan bir çağrının sonucu olabilir <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="edfaf-136">For example, the task might be the result of a call to <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="edfaf-137">Böyle bir görevi beklerken, bekleme işlemi özel durumlardan yalnızca birini yeniden oluşturur.</span><span class="sxs-lookup"><span data-stu-id="edfaf-137">When you await such a task, the await operation rethrows only one of the exceptions.</span></span> <span data-ttu-id="edfaf-138">Ancak, özel durumların fırlatılan tahmin edemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="edfaf-138">However, you can't predict which of the exceptions is rethrown.</span></span>  
  
 <span data-ttu-id="edfaf-139">Zaman uyumsuz yöntemlerdeki hata işleme örnekleri için bkz: [deneyin... Catch... Finally deyimini](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="edfaf-139">For examples of error handling in async methods, see [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="edfaf-140">Örnek</span><span class="sxs-lookup"><span data-stu-id="edfaf-140">Example</span></span>  
 <span data-ttu-id="edfaf-141">Aşağıdaki Windows Forms örnek kullanımını gösterir `Await` bir zaman uyumsuz yönteminde `WaitAsynchronouslyAsync`.</span><span class="sxs-lookup"><span data-stu-id="edfaf-141">The following Windows Forms example illustrates the use of `Await` in an async method, `WaitAsynchronouslyAsync`.</span></span> <span data-ttu-id="edfaf-142">Davranışı ile yöntemin davranışını karşılaştırın `WaitSynchronously`.</span><span class="sxs-lookup"><span data-stu-id="edfaf-142">Contrast the behavior of that method with the behavior of `WaitSynchronously`.</span></span> <span data-ttu-id="edfaf-143">Bir `Await` operatörü olmadan, `WaitSynchronously` zaman uyumlu olarak çalışır, tanımında `Async` değiştiricisinin ve gövdesinde bir <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> çağrısı kullanılmasına rağmen.</span><span class="sxs-lookup"><span data-stu-id="edfaf-143">Without an `Await` operator, `WaitSynchronously` runs synchronously despite the use of the `Async` modifier in its definition and a call to <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> in its body.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="edfaf-144">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="edfaf-144">See Also</span></span>  
 [<span data-ttu-id="edfaf-145">Async ve Await ile Zaman Uyumsuz Programlama</span><span class="sxs-lookup"><span data-stu-id="edfaf-145">Asynchronous Programming with Async and Await</span></span>](../../../visual-basic/programming-guide/concepts/async/index.md)  
 [<span data-ttu-id="edfaf-146">İzlenecek yol: Async ve Await Kullanarak Web'e Erişme</span><span class="sxs-lookup"><span data-stu-id="edfaf-146">Walkthrough: Accessing the Web by Using Async and Await</span></span>](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)  
 [<span data-ttu-id="edfaf-147">Async</span><span class="sxs-lookup"><span data-stu-id="edfaf-147">Async</span></span>](../../../visual-basic/language-reference/modifiers/async.md)
