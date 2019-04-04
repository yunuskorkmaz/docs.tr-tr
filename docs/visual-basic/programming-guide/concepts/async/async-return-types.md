---
title: Zaman uyumsuz dönüş türleri (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 07890291-ee72-42d3-932a-fa4d312f2c60
ms.openlocfilehash: 7a8bc3ba98da830c8415284771460a25e0927895
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58838358"
---
# <a name="async-return-types-visual-basic"></a><span data-ttu-id="9cc5d-102">Zaman uyumsuz dönüş türleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9cc5d-102">Async Return Types (Visual Basic)</span></span>
<span data-ttu-id="9cc5d-103">Zaman uyumsuz yöntemler üç olası dönüş türüne sahiptir: <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.Task>ve void.</span><span class="sxs-lookup"><span data-stu-id="9cc5d-103">Async methods have three possible return types: <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.Task>, and void.</span></span> <span data-ttu-id="9cc5d-104">Visual Basic'te, void dönüş türü olarak yazılmış bir [alt](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) yordamı.</span><span class="sxs-lookup"><span data-stu-id="9cc5d-104">In Visual Basic, the void return type is written as a [Sub](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) procedure.</span></span> <span data-ttu-id="9cc5d-105">Zaman uyumsuz yöntemler hakkında daha fazla bilgi için bkz. [Async ve Await ile Zaman Uyumsuz Programlama (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="9cc5d-105">For more information about async methods, see [Asynchronous Programming with Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md).</span></span>  
  
 <span data-ttu-id="9cc5d-106">Her dönüş türü aşağıdaki bölümlerden birinde incelenir ve konunun sonunda üç türü kullanan bir tam örnek bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9cc5d-106">Each return type is examined in one of the following sections, and you can find a full example that uses all three types at the end of the topic.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9cc5d-107">Yeni bilgisayarınızda yüklü veya örneği çalıştırmak için Visual Studio 2012 veya daha yeni ve .NET Framework 4.5 yüklü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9cc5d-107">To run the example, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
## <a name="BKMK_TaskTReturnType"></a> <span data-ttu-id="9cc5d-108">Görev(t) dönüş türü</span><span class="sxs-lookup"><span data-stu-id="9cc5d-108">Task(T) Return Type</span></span>  
 <span data-ttu-id="9cc5d-109"><xref:System.Threading.Tasks.Task%601> Dönüş türü içeren zaman uyumsuz yöntemi için kullanılan bir [dönüş](../../../../visual-basic/language-reference/statements/return-statement.md) işlenen türü içeren ifadesi `TResult`.</span><span class="sxs-lookup"><span data-stu-id="9cc5d-109">The <xref:System.Threading.Tasks.Task%601> return type is used for an async method that contains a [Return](../../../../visual-basic/language-reference/statements/return-statement.md) statement in which the operand has type `TResult`.</span></span>  
  
 <span data-ttu-id="9cc5d-110">Aşağıdaki örnekte, `TaskOfT_MethodAsync` zaman uyumsuz yönteminde tamsayı döndüren bir return deyimi içerir.</span><span class="sxs-lookup"><span data-stu-id="9cc5d-110">In the following example, the `TaskOfT_MethodAsync` async method contains a return statement that returns an integer.</span></span> <span data-ttu-id="9cc5d-111">Bu nedenle, yöntem bildiriminde bir dönüş türü belirtmelisiniz `Task(Of Integer)`.</span><span class="sxs-lookup"><span data-stu-id="9cc5d-111">Therefore, the method declaration must specify a return type of `Task(Of Integer)`.</span></span>  
  
```vb  
' TASK(OF T) EXAMPLE  
Async Function TaskOfT_MethodAsync() As Task(Of Integer)  
  
    ' The body of an async method is expected to contain an awaited   
    ' asynchronous call.  
    ' Task.FromResult is a placeholder for actual work that returns a string.  
    Dim today As String = Await Task.FromResult(Of String)(DateTime.Now.DayOfWeek.ToString())  
  
    ' The method then can process the result in some way.  
    Dim leisureHours As Integer  
    If today.First() = "S" Then  
        leisureHours = 16  
    Else  
        leisureHours = 5  
    End If  
  
    ' Because the return statement specifies an operand of type Integer, the   
    ' method must have a return type of Task(Of Integer).   
    Return leisureHours  
End Function  
```  
  
 <span data-ttu-id="9cc5d-112">Zaman `TaskOfT_MethodAsync` çağrılır bir await ifadesi içinde await ifadesi tamsayı değerini alır (değerini `leisureHours`) tarafından döndürülen görev depolanan `TaskOfT_MethodAsync`.</span><span class="sxs-lookup"><span data-stu-id="9cc5d-112">When `TaskOfT_MethodAsync` is called from within an await expression, the await expression retrieves the integer value (the value of `leisureHours`) that's stored in the task that's returned by `TaskOfT_MethodAsync`.</span></span> <span data-ttu-id="9cc5d-113">Hakkında daha fazla bilgi için await ifadeleri, bkz: [Await işleci](../../../../visual-basic/language-reference/operators/await-operator.md).</span><span class="sxs-lookup"><span data-stu-id="9cc5d-113">For more information about await expressions, see [Await Operator](../../../../visual-basic/language-reference/operators/await-operator.md).</span></span>  
  
 <span data-ttu-id="9cc5d-114">Aşağıdaki kodu çağırır ve yöntem bekler `TaskOfT_MethodAsync`.</span><span class="sxs-lookup"><span data-stu-id="9cc5d-114">The following code calls and awaits method `TaskOfT_MethodAsync`.</span></span> <span data-ttu-id="9cc5d-115">Sonuç atandığı `result1` değişkeni.</span><span class="sxs-lookup"><span data-stu-id="9cc5d-115">The result is assigned to the `result1` variable.</span></span>  
  
```vb  
' Call and await the Task(Of T)-returning async method in the same statement.  
Dim result1 As Integer = Await TaskOfT_MethodAsync()  
```  
  
 <span data-ttu-id="9cc5d-116">Çağrı ayırarak nasıl böyle daha iyi anlamak `TaskOfT_MethodAsync` uygulamasından `Await`aşağıdaki kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="9cc5d-116">You can better understand how this happens by separating the call to `TaskOfT_MethodAsync` from the application of `Await`, as the following code shows.</span></span> <span data-ttu-id="9cc5d-117">Yöntemine yapılan bir çağrı `TaskOfT_MethodAsync` hemen beklenmeyen döndürür, değilse bir `Task(Of Integer)`, yöntem bildiriminden beklediğiniz gibi.</span><span class="sxs-lookup"><span data-stu-id="9cc5d-117">A call to method `TaskOfT_MethodAsync` that isn't immediately awaited returns a `Task(Of Integer)`, as you would expect from the declaration of the method.</span></span> <span data-ttu-id="9cc5d-118">Görevin atandığı `integerTask` örnekte değişken.</span><span class="sxs-lookup"><span data-stu-id="9cc5d-118">The task is assigned to the `integerTask` variable in the example.</span></span> <span data-ttu-id="9cc5d-119">Çünkü `integerTask` olduğu bir <xref:System.Threading.Tasks.Task%601>, içerdiği bir <xref:System.Threading.Tasks.Task%601.Result> türünün özelliği `TResult`.</span><span class="sxs-lookup"><span data-stu-id="9cc5d-119">Because `integerTask` is a <xref:System.Threading.Tasks.Task%601>, it contains a <xref:System.Threading.Tasks.Task%601.Result> property of type `TResult`.</span></span> <span data-ttu-id="9cc5d-120">Bu durumda, TResult bir tamsayı türünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="9cc5d-120">In this case, TResult represents an integer type.</span></span> <span data-ttu-id="9cc5d-121">Zaman `Await` uygulanan `integerTask`, bekleme ifadesi içeriğine göre değerlendirilir <xref:System.Threading.Tasks.Task%601.Result%2A> özelliği `integerTask`.</span><span class="sxs-lookup"><span data-stu-id="9cc5d-121">When `Await` is applied to `integerTask`, the await expression evaluates to the contents of the <xref:System.Threading.Tasks.Task%601.Result%2A> property of `integerTask`.</span></span> <span data-ttu-id="9cc5d-122">Değeri atanır `result2` değişkeni.</span><span class="sxs-lookup"><span data-stu-id="9cc5d-122">The value is assigned to the `result2` variable.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="9cc5d-123"><xref:System.Threading.Tasks.Task%601.Result%2A> Özelliği engelleyici bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="9cc5d-123">The <xref:System.Threading.Tasks.Task%601.Result%2A> property is a blocking property.</span></span> <span data-ttu-id="9cc5d-124">Kendi görevi bitmeden önce buna erişmeyi denerseniz, şu anda etkin olan iş parçacığı değeri kullanılabilir ve görev tamamlanıncaya kadar engellenir.</span><span class="sxs-lookup"><span data-stu-id="9cc5d-124">If you try to access it before its task is finished, the thread that's currently active is blocked until the task completes and the value is available.</span></span> <span data-ttu-id="9cc5d-125">Çoğu durumda, değeri kullanarak erişmeli `Await` özelliği doğrudan erişmek yerine.</span><span class="sxs-lookup"><span data-stu-id="9cc5d-125">In most cases, you should access the value by using `Await` instead of accessing the property directly.</span></span>  
  
```vb  
' Call and await in separate statements.  
Dim integerTask As Task(Of Integer) = TaskOfT_MethodAsync()  
  
' You can do other work that does not rely on resultTask before awaiting.  
textBox1.Text &= String.Format("Application can continue working while the Task(Of T) runs. . . . " & vbCrLf)  
  
Dim result2 As Integer = Await integerTask  
```  
  
 <span data-ttu-id="9cc5d-126">Aşağıdaki kodda yer alan görüntü deyimleri doğrulayın değerlerini `result1` değişken `result2` değişken ve `Result` özelliği aynıdır.</span><span class="sxs-lookup"><span data-stu-id="9cc5d-126">The display statements in the following code verify that the values of the `result1` variable, the `result2` variable, and the `Result` property are the same.</span></span> <span data-ttu-id="9cc5d-127">Unutmayın `Result` engelleyici bir özelliktir ve görevi beklenmeden önce erişilmemesi.</span><span class="sxs-lookup"><span data-stu-id="9cc5d-127">Remember that the `Result` property is a blocking property and shouldn't be accessed before its task has been awaited.</span></span>  
  
```vb  
' Display the values of the result1 variable, the result2 variable, and  
' the resultTask.Result property.  
textBox1.Text &= String.Format(vbCrLf & "Value of result1 variable:   {0}" & vbCrLf, result1)  
textBox1.Text &= String.Format("Value of result2 variable:   {0}" & vbCrLf, result2)  
textBox1.Text &= String.Format("Value of resultTask.Result:  {0}" & vbCrLf, integerTask.Result)  
```  
  
## <a name="BKMK_TaskReturnType"></a> <span data-ttu-id="9cc5d-128">Görev dönüş türü</span><span class="sxs-lookup"><span data-stu-id="9cc5d-128">Task Return Type</span></span>  
 <span data-ttu-id="9cc5d-129">Return deyimi içermeyen veya bir işleç genellikle döndürmeyen bir return deyimi içeren zaman uyumsuz yöntemlerin dönüş türüne sahip <xref:System.Threading.Tasks.Task>.</span><span class="sxs-lookup"><span data-stu-id="9cc5d-129">Async methods that don't contain a return statement or that contain a return statement that doesn't return an operand usually have a return type of <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="9cc5d-130">Bu tür yöntemler olacaktır [alt](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) eşzamanlı çalışacak biçimde yazılmışsa yordamları.</span><span class="sxs-lookup"><span data-stu-id="9cc5d-130">Such methods would be [Sub](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) procedures if they were written to run synchronously.</span></span> <span data-ttu-id="9cc5d-131">Kullanıyorsanız bir `Task` dönüş türü için zaman uyumsuz yöntemi çağıran bir yöntemi kullanabilirsiniz bir `Await` çağrılan zaman uyumsuz yöntemi bitene kadar çağıranın tamamlanmasını bekletmek için işleci.</span><span class="sxs-lookup"><span data-stu-id="9cc5d-131">If you use a `Task` return type for an async method, a calling method can use an `Await` operator to suspend the caller's completion until the called async method has finished.</span></span>  
  
 <span data-ttu-id="9cc5d-132">Aşağıdaki örnekte, zaman uyumsuz yöntem `Task_MethodAsync` bir return deyimi yok.</span><span class="sxs-lookup"><span data-stu-id="9cc5d-132">In the following example, async method `Task_MethodAsync` doesn't contain a return statement.</span></span> <span data-ttu-id="9cc5d-133">Bu nedenle, dönüş türü belirttiğiniz `Task` sağlayan yöntem için `Task_MethodAsync` beklenmesini.</span><span class="sxs-lookup"><span data-stu-id="9cc5d-133">Therefore, you specify a return type of `Task` for the method, which enables `Task_MethodAsync` to be awaited.</span></span> <span data-ttu-id="9cc5d-134">Tanımı `Task` türü içermez bir `Result` dönüş değerini depolamak için özellik.</span><span class="sxs-lookup"><span data-stu-id="9cc5d-134">The definition of the `Task` type doesn't include a `Result` property to store a return value.</span></span>  
  
```vb  
' TASK EXAMPLE  
Async Function Task_MethodAsync() As Task  
  
    ' The body of an async method is expected to contain an awaited   
    ' asynchronous call.  
    ' Task.Delay is a placeholder for actual work.  
    Await Task.Delay(2000)  
    textBox1.Text &= String.Format(vbCrLf & "Sorry for the delay. . . ." & vbCrLf)  
  
    ' This method has no return statement, so its return type is Task.   
End Function  
```  
  
 <span data-ttu-id="9cc5d-135">`Task_MethodAsync` çağrılan ve bir zaman uyumlu için çağırma deyimine benzer bir await ifadesi yerine await deyimi kullanılarak bekleniyor `Sub` veya void döndüren yöntem.</span><span class="sxs-lookup"><span data-stu-id="9cc5d-135">`Task_MethodAsync` is called and awaited by using an await statement instead of an await expression, similar to the calling statement for a synchronous `Sub` or void-returning method.</span></span> <span data-ttu-id="9cc5d-136">Uygulamayı bir `Await` işleci Bu örnekte bir değer üreten değil.</span><span class="sxs-lookup"><span data-stu-id="9cc5d-136">The application of an `Await` operator in this case doesn't produce a value.</span></span>  
  
 <span data-ttu-id="9cc5d-137">Aşağıdaki kodu çağırır ve yöntem bekler `Task_MethodAsync`.</span><span class="sxs-lookup"><span data-stu-id="9cc5d-137">The following code calls and awaits method `Task_MethodAsync`.</span></span>  
  
```vb  
' Call and await the Task-returning async method in the same statement.  
Await Task_MethodAsync()  
```  
  
 <span data-ttu-id="9cc5d-138">Önceki olduğu gibi <xref:System.Threading.Tasks.Task%601> örnek, çağrı ayırabilirsiniz `Task_MethodAsync` uygulamasından bir `Await` işleci, aşağıdaki kodun gösterdiği olarak.</span><span class="sxs-lookup"><span data-stu-id="9cc5d-138">As in the previous <xref:System.Threading.Tasks.Task%601> example, you can separate the call to `Task_MethodAsync` from the application of an `Await` operator, as the following code shows.</span></span> <span data-ttu-id="9cc5d-139">Ancak, unutmayın bir `Task` sahip olmayan bir `Result` özelliği ve bir await işleci uygulandığında, değer üretilmediğini bir `Task`.</span><span class="sxs-lookup"><span data-stu-id="9cc5d-139">However, remember that a `Task` doesn't have a `Result` property, and that no value is produced when an await operator is applied to a `Task`.</span></span>  
  
 <span data-ttu-id="9cc5d-140">Aşağıdaki kod ayırır `Task_MethodAsync` görevi bekleme işleminden, `Task_MethodAsync` döndürür.</span><span class="sxs-lookup"><span data-stu-id="9cc5d-140">The following code separates calling `Task_MethodAsync` from awaiting the task that `Task_MethodAsync` returns.</span></span>  
  
```vb  
' Call and await in separate statements.  
Dim simpleTask As Task = Task_MethodAsync()  
  
' You can do other work that does not rely on simpleTask before awaiting.  
textBox1.Text &= String.Format(vbCrLf & "Application can continue working while the Task runs. . . ." & vbCrLf)  
  
Await simpleTask  
```  
  
## <a name="BKMK_VoidReturnType"></a> <span data-ttu-id="9cc5d-141">Void dönüş türü</span><span class="sxs-lookup"><span data-stu-id="9cc5d-141">Void Return Type</span></span>  
 <span data-ttu-id="9cc5d-142">Birincil kullanım alanının `Sub` yordamları, olay işleyicileri olan (diğer dillerdeki void dönüş türü olarak adlandırılır) herhangi bir döndürme türü olduğu.</span><span class="sxs-lookup"><span data-stu-id="9cc5d-142">The primary use of `Sub` procedures is in event handlers, where there is no return type (referred to as a void return type in other languages).</span></span> <span data-ttu-id="9cc5d-143">Void dönüş void döndüren yöntemleri geçersiz kılmak için de kullanılabilir veya kategorilere ayrılabilir etkinlikleri gerçekleştiren yöntemler için olarak "Başlat ve unut."</span><span class="sxs-lookup"><span data-stu-id="9cc5d-143">A void return also can be used to override void-returning methods or for methods that perform activities that can be categorized as "fire and forget."</span></span> <span data-ttu-id="9cc5d-144">Ancak, döndürmelidir bir `Task` mümkün olduğunda, çünkü bir void döndüren zaman uyumsuz yöntem beklenemez.</span><span class="sxs-lookup"><span data-stu-id="9cc5d-144">However, you should return a `Task` wherever possible, because a void-returning async method can't be awaited.</span></span> <span data-ttu-id="9cc5d-145">Tüm bu yöntemi çağıran kişi çağrılan zaman uyumsuz yöntemin tamamlanmasını beklemeden tamamlanana kadar devam edebilir ve çağıran zaman uyumsuz yöntemin oluşturduğu özel durumları veya değerlerden bağımsız olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9cc5d-145">Any caller of such a method must be able to continue to completion without waiting for the called async method to finish, and the caller must be independent of any values or exceptions that the async method generates.</span></span>  
  
 <span data-ttu-id="9cc5d-146">Void döndüren zaman uyumsuz yöntemi çağıran kişi yöntemden atılan özel durumları yakalayamaz ve böyle işlenmeyen özel durumların, uygulamanızın başarısız olmasına neden olabilecek.</span><span class="sxs-lookup"><span data-stu-id="9cc5d-146">The caller of a void-returning async method can't catch exceptions that are thrown from the method, and such unhandled exceptions are likely to cause your application to fail.</span></span> <span data-ttu-id="9cc5d-147">Döndüren zaman uyumsuz yöntemde özel durum oluşursa bir <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601>, özel durum getirilen görevde depolanır ve görev beklenirken yeniden atılır.</span><span class="sxs-lookup"><span data-stu-id="9cc5d-147">If an exception occurs in an async method that returns a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>, the exception is stored in the returned task, and rethrown when the task is awaited.</span></span> <span data-ttu-id="9cc5d-148">Bu nedenle, bir özel durum oluşturabilecek herhangi bir zaman uyumsuz yöntem dönüş türüne sahip olduğundan emin olun <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601> ve yöntemine yönelik çağrılar beklediğinden.</span><span class="sxs-lookup"><span data-stu-id="9cc5d-148">Therefore, make sure that any async method that can produce an exception has a return type of <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> and that calls to the method are awaited.</span></span>  
  
 <span data-ttu-id="9cc5d-149">Zaman uyumsuz yöntemlerde özel durumları yakalama hakkında daha fazla bilgi için bkz. [deneyin... Catch... Finally deyimini](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="9cc5d-149">For more information about how to catch exceptions in async methods, see [Try...Catch...Finally Statement](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
 <span data-ttu-id="9cc5d-150">Aşağıdaki kod, zaman uyumsuz olay işleyicisi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="9cc5d-150">The following code defines an async event handler.</span></span>  
  
```vb  
' SUB EXAMPLE  
Async Sub button1_Click(sender As Object, e As RoutedEventArgs) Handles button1.Click  
  
    textBox1.Clear()  
  
    ' Start the process and await its completion. DriverAsync is a   
    ' Task-returning async method.  
    Await DriverAsync()  
  
    ' Say goodbye.  
    textBox1.Text &= vbCrLf & "All done, exiting button-click event handler."  
End Sub  
```  
  
## <a name="BKMK_Example"></a> <span data-ttu-id="9cc5d-151">Tam örnek</span><span class="sxs-lookup"><span data-stu-id="9cc5d-151">Complete Example</span></span>  
 <span data-ttu-id="9cc5d-152">Aşağıdaki Windows Presentation Foundation (WPF) projesi bu konudan kod örnekleri içermektedir.</span><span class="sxs-lookup"><span data-stu-id="9cc5d-152">The following Windows Presentation Foundation (WPF) project contains the code examples from this topic.</span></span>  
  
 <span data-ttu-id="9cc5d-153">Projeyi çalıştırmak için aşağıdaki adımları gerçekleştirin:</span><span class="sxs-lookup"><span data-stu-id="9cc5d-153">To run the project, perform the following steps:</span></span>  
  
1.  <span data-ttu-id="9cc5d-154">Visual Studio’yu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="9cc5d-154">Start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="9cc5d-155">Menü çubuğunda, **dosya**, **yeni**, **proje**.</span><span class="sxs-lookup"><span data-stu-id="9cc5d-155">On the menu bar, choose **File**, **New**, **Project**.</span></span>  
  
     <span data-ttu-id="9cc5d-156">**Yeni proje** iletişim kutusu açılır.</span><span class="sxs-lookup"><span data-stu-id="9cc5d-156">The **New Project** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="9cc5d-157">İçinde **yüklü**, **şablonları** kategorisi seçin **Visual Basic**ve ardından **Windows**.</span><span class="sxs-lookup"><span data-stu-id="9cc5d-157">In the **Installed**, **Templates** category, choose **Visual Basic**, and then choose **Windows**.</span></span> <span data-ttu-id="9cc5d-158">Seçin **WPF uygulaması** proje türleri listesinden.</span><span class="sxs-lookup"><span data-stu-id="9cc5d-158">Choose **WPF Application** from the list of project types.</span></span>  
  
4.  <span data-ttu-id="9cc5d-159">Girin `AsyncReturnTypes` projesinin adı olarak seçip **Tamam** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="9cc5d-159">Enter `AsyncReturnTypes` as the name of the project, and then choose the **OK** button.</span></span>  
  
     <span data-ttu-id="9cc5d-160">Yeni Proje görünür **Çözüm Gezgini**.</span><span class="sxs-lookup"><span data-stu-id="9cc5d-160">The new project appears in **Solution Explorer**.</span></span>  
  
5.  <span data-ttu-id="9cc5d-161">Visual Studio Kod Düzenleyicisi'nde seçin **MainWindow.xaml** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="9cc5d-161">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>  
  
     <span data-ttu-id="9cc5d-162">Sekme görünür değilse nde MainWindow.xaml için kısayol menüsünü açın **Çözüm Gezgini**ve ardından **açın**.</span><span class="sxs-lookup"><span data-stu-id="9cc5d-162">If the tab is not visible, open the shortcut menu for MainWindow.xaml in **Solution Explorer**, and then choose **Open**.</span></span>  
  
6.  <span data-ttu-id="9cc5d-163">İçinde **XAML** MainWindow.xaml penceresinde kodu aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="9cc5d-163">In the **XAML** window of MainWindow.xaml, replace the code with the following code.</span></span>  
  
    ```vb  
    <Window x:Class="MainWindow"  
            xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
            xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
            Title="MainWindow" Height="350" Width="525">  
        <Grid>  
            <Button x:Name="button1" Content="Start" HorizontalAlignment="Left" Margin="214,28,0,0" VerticalAlignment="Top" Width="75" HorizontalContentAlignment="Center" FontWeight="Bold" FontFamily="Aharoni" Click="button1_Click"/>  
            <TextBox x:Name="textBox1" Margin="0,80,0,0" TextWrapping="Wrap" FontFamily="Lucida Console"/>  
  
        </Grid>  
    </Window>  
    ```  
  
     <span data-ttu-id="9cc5d-164">Bir metin kutusu ve bir düğme içeren basit bir pencere **tasarım** MainWindow.xaml penceresi.</span><span class="sxs-lookup"><span data-stu-id="9cc5d-164">A simple window that contains a text box and a button appears in the **Design** window of MainWindow.xaml.</span></span>  
  
7.  <span data-ttu-id="9cc5d-165">İçinde **Çözüm Gezgini**MainWindow.xaml.vb için kısayol menüsünü açın ve ardından **kodu görüntüle**.</span><span class="sxs-lookup"><span data-stu-id="9cc5d-165">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.vb, and then choose **View Code**.</span></span>  
  
8.  <span data-ttu-id="9cc5d-166">MainWindow.xaml.vb kodu aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="9cc5d-166">Replace the code in MainWindow.xaml.vb with the following code.</span></span>  
  
    ```vb  
    Class MainWindow  
  
        ' SUB EXAMPLE  
        Async Sub button1_Click(sender As Object, e As RoutedEventArgs) Handles button1.Click  
  
            textBox1.Clear()  
  
            ' Start the process and await its completion. DriverAsync is a   
            ' Task-returning async method.  
            Await DriverAsync()  
  
            ' Say goodbye.  
            textBox1.Text &= vbCrLf & "All done, exiting button-click event handler."  
        End Sub  
  
        Async Function DriverAsync() As Task  
  
            ' Task(Of T)   
            ' Call and await the Task(Of T)-returning async method in the same statement.  
            Dim result1 As Integer = Await TaskOfT_MethodAsync()  
  
            ' Call and await in separate statements.  
            Dim integerTask As Task(Of Integer) = TaskOfT_MethodAsync()  
  
            ' You can do other work that does not rely on resultTask before awaiting.  
            textBox1.Text &= String.Format("Application can continue working while the Task(Of T) runs. . . . " & vbCrLf)  
  
            Dim result2 As Integer = Await integerTask  
  
            ' Display the values of the result1 variable, the result2 variable, and  
            ' the resultTask.Result property.  
            textBox1.Text &= String.Format(vbCrLf & "Value of result1 variable:   {0}" & vbCrLf, result1)  
            textBox1.Text &= String.Format("Value of result2 variable:   {0}" & vbCrLf, result2)  
            textBox1.Text &= String.Format("Value of resultTask.Result:  {0}" & vbCrLf, integerTask.Result)  
  
            ' Task   
            ' Call and await the Task-returning async method in the same statement.  
            Await Task_MethodAsync()  
  
            ' Call and await in separate statements.  
            Dim simpleTask As Task = Task_MethodAsync()  
  
            ' You can do other work that does not rely on simpleTask before awaiting.  
            textBox1.Text &= String.Format(vbCrLf & "Application can continue working while the Task runs. . . ." & vbCrLf)  
  
            Await simpleTask  
        End Function  
  
        ' TASK(OF T) EXAMPLE  
        Async Function TaskOfT_MethodAsync() As Task(Of Integer)  
  
            ' The body of an async method is expected to contain an awaited   
            ' asynchronous call.  
            ' Task.FromResult is a placeholder for actual work that returns a string.  
            Dim today As String = Await Task.FromResult(Of String)(DateTime.Now.DayOfWeek.ToString())  
  
            ' The method then can process the result in some way.  
            Dim leisureHours As Integer  
            If today.First() = "S" Then  
                leisureHours = 16  
            Else  
                leisureHours = 5  
            End If  
  
            ' Because the return statement specifies an operand of type Integer, the   
            ' method must have a return type of Task(Of Integer).   
            Return leisureHours  
        End Function  
  
        ' TASK EXAMPLE  
        Async Function Task_MethodAsync() As Task  
  
            ' The body of an async method is expected to contain an awaited   
            ' asynchronous call.  
            ' Task.Delay is a placeholder for actual work.  
            Await Task.Delay(2000)  
            textBox1.Text &= String.Format(vbCrLf & "Sorry for the delay. . . ." & vbCrLf)  
  
            ' This method has no return statement, so its return type is Task.   
        End Function  
  
    End Class  
    ```  
  
9. <span data-ttu-id="9cc5d-167">Programı çalıştırın ve ardından F5 tuşuna basın **Başlat** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="9cc5d-167">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
     <span data-ttu-id="9cc5d-168">Aşağıdaki çıktı görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="9cc5d-168">The following output should appear.</span></span>  
  
    ```  
    Application can continue working while the Task<T> runs. . . .   
  
    Value of result1 variable:   5  
    Value of result2 variable:   5  
    Value of integerTask.Result: 5  
  
    Sorry for the delay. . . .  
  
    Application can continue working while the Task runs. . . .  
  
    Sorry for the delay. . . .  
  
    All done, exiting button-click event handler.  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="9cc5d-169">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9cc5d-169">See also</span></span>

- <xref:System.Threading.Tasks.Task.FromResult%2A>
- [<span data-ttu-id="9cc5d-170">İzlenecek yol: Zaman uyumsuz kullanarak Web'e erişme ve Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9cc5d-170">Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="9cc5d-171">Zaman uyumsuz programlarda (Visual Basic) denetim akışı</span><span class="sxs-lookup"><span data-stu-id="9cc5d-171">Control Flow in Async Programs (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)
- [<span data-ttu-id="9cc5d-172">Async</span><span class="sxs-lookup"><span data-stu-id="9cc5d-172">Async</span></span>](../../../../visual-basic/language-reference/modifiers/async.md)
- [<span data-ttu-id="9cc5d-173">Await İşleci</span><span class="sxs-lookup"><span data-stu-id="9cc5d-173">Await Operator</span></span>](../../../../visual-basic/language-reference/operators/await-operator.md)
