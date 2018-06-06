---
title: Zaman Uyumsuz (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Async
helpviewer_keywords:
- Async [Visual Basic]
- Async keyword [Visual Basic]
ms.assetid: 1be8b4b5-9689-41b5-bd33-b906bfd53bc5
ms.openlocfilehash: 244f468d9432e132c93ae8272d51098f86ad439a
ms.sourcegitcommit: d8bf4976eafe3289275be3811e7cb721bfff7e1e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34753350"
---
# <a name="async-visual-basic"></a><span data-ttu-id="f50e6-102">Zaman Uyumsuz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f50e6-102">Async (Visual Basic)</span></span>
<span data-ttu-id="f50e6-103">`Async` Değiştiricisi gösterir yöntemi veya [lambda ifadesi](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md) olduğunu değiştirdiği zaman uyumsuz olarak çağrılır.</span><span class="sxs-lookup"><span data-stu-id="f50e6-103">The `Async` modifier indicates that the method or [lambda expression](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md) that it modifies is asynchronous.</span></span> <span data-ttu-id="f50e6-104">Bu tür yöntemleri denir *zaman uyumsuz yöntemleri*.</span><span class="sxs-lookup"><span data-stu-id="f50e6-104">Such methods are referred to as *async methods*.</span></span>  
  
 <span data-ttu-id="f50e6-105">Bir zaman uyumsuz yöntem arayanın iş parçacığı engellenmeden potansiyel olarak uzun süre çalışan iş yapmak için kolay bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="f50e6-105">An async method provides a convenient way to do potentially long-running work without blocking the caller's thread.</span></span> <span data-ttu-id="f50e6-106">Zaman uyumsuz yöntem arayan async yöntemi bitmesini beklemeden işini sürdürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f50e6-106">The caller of an async method can resume its work without waiting for the async method to finish.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f50e6-107">`Async` Ve `Await` anahtar sözcükler, Visual Studio 2012'de sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="f50e6-107">The `Async` and `Await` keywords were introduced in Visual Studio 2012.</span></span> <span data-ttu-id="f50e6-108">Zaman uyumsuz programlamaya giriş için bkz: [uyumsuz ve bekleme ile zaman uyumsuz programlama](../../../visual-basic/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="f50e6-108">For an introduction to async programming, see [Asynchronous Programming with Async and Await](../../../visual-basic/programming-guide/concepts/async/index.md).</span></span>  
  
 <span data-ttu-id="f50e6-109">Aşağıdaki örnek, bir zaman uyumsuz metodun yapısını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f50e6-109">The following example shows the structure of an async method.</span></span> <span data-ttu-id="f50e6-110">Kural olarak, zaman uyumsuz metot adları "Async." ile biter.</span><span class="sxs-lookup"><span data-stu-id="f50e6-110">By convention, async method names end in "Async."</span></span>  
  
```vb  
Public Async Function ExampleMethodAsync() As Task(Of Integer)  
    ' . . .  
  
    ' At the Await expression, execution in this method is suspended and,  
    ' if AwaitedProcessAsync has not already finished, control returns  
    ' to the caller of ExampleMethodAsync. When the awaited task is   
    ' completed, this method resumes execution.   
    Dim exampleInt As Integer = Await AwaitedProcessAsync()  
  
    ' . . .  
  
    ' The return statement completes the task. Any method that is   
    ' awaiting ExampleMethodAsync can now get the integer result.  
    Return exampleInt  
End Function  
```  
  
 <span data-ttu-id="f50e6-111">Genellikle, bir yöntem değiştiren tarafından `Async` anahtar sözcüğünü içeren en az bir [bekleme](../../../visual-basic/language-reference/modifiers/async.md) ifadesi veya deyimi.</span><span class="sxs-lookup"><span data-stu-id="f50e6-111">Typically, a method modified by the `Async` keyword contains at least one [Await](../../../visual-basic/language-reference/modifiers/async.md) expression or statement.</span></span> <span data-ttu-id="f50e6-112">Bekleyen görev tamamlanıncaya kadar bekletilen nokta olan ilk `Await`'a ulaşana kadar metot zaman uyumlu olarak çalışır.</span><span class="sxs-lookup"><span data-stu-id="f50e6-112">The method runs synchronously until it reaches the first `Await`, at which point it suspends until the awaited task completes.</span></span> <span data-ttu-id="f50e6-113">Bu sırada, denetim, metodu çağırana döner.</span><span class="sxs-lookup"><span data-stu-id="f50e6-113">In the meantime, control is returned to the caller of the method.</span></span> <span data-ttu-id="f50e6-114">Metot bir `Await` ifade veya deyimi içermiyorsa, metot askıya alınmaz ve zaman uyumlu bir yöntem olarak yürütülür.</span><span class="sxs-lookup"><span data-stu-id="f50e6-114">If the method doesn’t contain an `Await` expression or statement, the method isn’t suspended and executes as a synchronous method does.</span></span> <span data-ttu-id="f50e6-115">Derleyici Uyarısı içermeyen herhangi bir zaman uyumsuz yöntem uyarıları `Await` çünkü bu durumu gösteren bir hata olabilir.</span><span class="sxs-lookup"><span data-stu-id="f50e6-115">A compiler warning alerts you to any async methods that don't contain `Await` because that situation might indicate an error.</span></span> <span data-ttu-id="f50e6-116">Daha fazla bilgi için bkz: [derleyici hatası](../../../visual-basic/language-reference/error-messages/because-this-call-is-not-awaited-the-current-method-continues-to-run.md).</span><span class="sxs-lookup"><span data-stu-id="f50e6-116">For more information, see the [compiler error](../../../visual-basic/language-reference/error-messages/because-this-call-is-not-awaited-the-current-method-continues-to-run.md).</span></span>  
  
 <span data-ttu-id="f50e6-117">`Async` anahtar kelimesi ayrılmamış bir anahtar sözcüktür.</span><span class="sxs-lookup"><span data-stu-id="f50e6-117">The `Async` keyword is an unreserved keyword.</span></span> <span data-ttu-id="f50e6-118">Bir metot veya lambda ifadesi değiştirdiği zaman bir anahtar sözcüktür.</span><span class="sxs-lookup"><span data-stu-id="f50e6-118">It is a keyword when it modifies a method or a lambda expression.</span></span> <span data-ttu-id="f50e6-119">Diğer tüm bağlamlarda bu, bir tanımlayıcı olarak yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="f50e6-119">In all other contexts, it is interpreted as an identifier.</span></span>  
  
## <a name="return-types"></a><span data-ttu-id="f50e6-120">Dönüş Türleri</span><span class="sxs-lookup"><span data-stu-id="f50e6-120">Return Types</span></span>  
 <span data-ttu-id="f50e6-121">Async yöntemi olan bir [alt](../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) yordamı, veya bir [işlevi](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md) dönüş türüne sahip yordamı <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="f50e6-121">An async method is either a [Sub](../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) procedure, or a [Function](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md) procedure that has a return type of <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="f50e6-122">Herhangi bir yöntemi bildiremez [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) parametreleri.</span><span class="sxs-lookup"><span data-stu-id="f50e6-122">The method cannot declare any [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) parameters.</span></span>  
  
 <span data-ttu-id="f50e6-123">Belirttiğiniz `Task(Of TResult)` bir zaman uyumsuz yönteminin dönüş türü için [dönmek](../../../visual-basic/language-reference/statements/return-statement.md) yöntemin ifadesi işleneni türü TResult sahiptir.</span><span class="sxs-lookup"><span data-stu-id="f50e6-123">You specify `Task(Of TResult)` for the return type of an async method if the [Return](../../../visual-basic/language-reference/statements/return-statement.md) statement of the method has an operand of type TResult.</span></span> <span data-ttu-id="f50e6-124">Kullandığınız `Task` yöntemi tamamlandığında hiçbir anlamlı değeri döndürülür.</span><span class="sxs-lookup"><span data-stu-id="f50e6-124">You use `Task` if no meaningful value is returned when the method is completed.</span></span> <span data-ttu-id="f50e6-125">Yani, yönteme bir çağrı, `Task`'i geri getirir, ancak `Task` tamamlandığı zaman, `Await`'i bekleyen herhangi bir `Task` deyimi bir sonuç değeri üretemez.</span><span class="sxs-lookup"><span data-stu-id="f50e6-125">That is, a call to the method returns a `Task`, but when the `Task` is completed, any `Await` statement that's awaiting the `Task` doesn’t produce a result value.</span></span>  
  
 <span data-ttu-id="f50e6-126">Zaman uyumsuz alt rutinler, öncelikle bir `Sub` yordamının gerekli olduğu yerde olay işleyicilerini tanımlamak için kullanılır</span><span class="sxs-lookup"><span data-stu-id="f50e6-126">Async subroutines are used primarily to define event handlers where a `Sub` procedure is required.</span></span> <span data-ttu-id="f50e6-127">Zaman uyumsuz bir alt rutinin çağırıcısı onu bekleyemez ve metodun oluşturduğu özel durumları yakalayamaz.</span><span class="sxs-lookup"><span data-stu-id="f50e6-127">The caller of an async subroutine can't await it and can't catch exceptions that the method throws.</span></span>  
  
 <span data-ttu-id="f50e6-128">Daha fazla bilgi ve örnekler için bkz: [zaman uyumsuz dönüş türleri](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="f50e6-128">For more information and examples, see [Async Return Types](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f50e6-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="f50e6-129">Example</span></span>  
 <span data-ttu-id="f50e6-130">Aşağıdaki örnekler, zaman uyumsuz bir olay işleyicisi, bir zaman uyumsuz lambda ifadesi ve bir zaman uyumsuz metot gösterir.</span><span class="sxs-lookup"><span data-stu-id="f50e6-130">The following examples show an async event handler, an async lambda expression, and an async method.</span></span> <span data-ttu-id="f50e6-131">Bu öğeleri kullanan bir tam örnek için bkz: [izlenecek yol: Web kullanarak zaman uyumsuz ve bekleme tarafından erişme](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="f50e6-131">For a full example that uses these elements, see [Walkthrough: Accessing the Web by Using Async and Await](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span> <span data-ttu-id="f50e6-132">İzlenecek yol koddan indirebilirsiniz [Geliştirici kod örnekleri](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).</span><span class="sxs-lookup"><span data-stu-id="f50e6-132">You can download the walkthrough code from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).</span></span>  
  
```vb  
' An event handler must be a Sub procedure.  
Async Sub button1_Click(sender As Object, e As RoutedEventArgs) Handles button1.Click  
    textBox1.Clear()  
    ' SumPageSizesAsync is a method that returns a Task.  
    Await SumPageSizesAsync()  
    textBox1.Text = vbCrLf & "Control returned to button1_Click."  
End Sub  
  
' The following async lambda expression creates an equivalent anonymous  
' event handler.  
AddHandler button1.Click, Async Sub(sender, e)  
                              textBox1.Clear()  
                              ' SumPageSizesAsync is a method that returns a Task.  
                              Await SumPageSizesAsync()  
                              textBox1.Text = vbCrLf & "Control returned to button1_Click."  
                          End Sub  
  
' The following async method returns a Task(Of T).  
' A typical call awaits the Byte array result:  
'      Dim result As Byte() = Await GetURLContents("http://msdn.com")  
Private Async Function GetURLContentsAsync(url As String) As Task(Of Byte())  
  
    ' The downloaded resource ends up in the variable named content.  
    Dim content = New MemoryStream()  
  
    ' Initialize an HttpWebRequest for the current URL.  
    Dim webReq = CType(WebRequest.Create(url), HttpWebRequest)  
  
    ' Send the request to the Internet resource and wait for  
    ' the response.  
    Using response As WebResponse = Await webReq.GetResponseAsync()  
        ' Get the data stream that is associated with the specified URL.  
        Using responseStream As Stream = response.GetResponseStream()  
            ' Read the bytes in responseStream and copy them to content.    
            ' CopyToAsync returns a Task, not a Task<T>.  
            Await responseStream.CopyToAsync(content)  
        End Using  
    End Using  
  
    ' Return the result as a byte array.  
    Return content.ToArray()  
End Function  
```  
  
## <a name="see-also"></a><span data-ttu-id="f50e6-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f50e6-133">See Also</span></span>  
 <xref:System.Runtime.CompilerServices.AsyncStateMachineAttribute>  
 [<span data-ttu-id="f50e6-134">Await İşleci</span><span class="sxs-lookup"><span data-stu-id="f50e6-134">Await Operator</span></span>](../../../visual-basic/language-reference/operators/await-operator.md)  
 [<span data-ttu-id="f50e6-135">Async ve Await ile Zaman Uyumsuz Programlama</span><span class="sxs-lookup"><span data-stu-id="f50e6-135">Asynchronous Programming with Async and Await</span></span>](../../../visual-basic/programming-guide/concepts/async/index.md)  
 [<span data-ttu-id="f50e6-136">İzlenecek yol: Async ve Await Kullanarak Web'e Erişme</span><span class="sxs-lookup"><span data-stu-id="f50e6-136">Walkthrough: Accessing the Web by Using Async and Await</span></span>](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
