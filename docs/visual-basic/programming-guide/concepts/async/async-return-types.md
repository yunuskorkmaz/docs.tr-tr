---
title: Zaman uyumsuz dönüş türleri (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 07890291-ee72-42d3-932a-fa4d312f2c60
ms.openlocfilehash: 0c6c02efd282f8581f3dc85905149acf7b3ea6ac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33644088"
---
# <a name="async-return-types-visual-basic"></a><span data-ttu-id="d8ec0-102">Zaman uyumsuz dönüş türleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d8ec0-102">Async Return Types (Visual Basic)</span></span>
<span data-ttu-id="d8ec0-103">Zaman uyumsuz yöntemleri sahip üç olası dönüş türleri: <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.Task>ve void.</span><span class="sxs-lookup"><span data-stu-id="d8ec0-103">Async methods have three possible return types: <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.Task>, and void.</span></span> <span data-ttu-id="d8ec0-104">Visual Basic'te, dönüş türü void olarak yazılmış bir [alt](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) yordamı.</span><span class="sxs-lookup"><span data-stu-id="d8ec0-104">In Visual Basic, the void return type is written as a [Sub](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) procedure.</span></span> <span data-ttu-id="d8ec0-105">Zaman uyumsuz yöntemleri hakkında daha fazla bilgi için bkz: [zaman uyumsuz programlama uyumsuz ve bekleme (Visual Basic) ile](../../../../visual-basic/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="d8ec0-105">For more information about async methods, see [Asynchronous Programming with Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md).</span></span>  
  
 <span data-ttu-id="d8ec0-106">Her bir dönüş türü aşağıdaki bölümlerde biri incelenir ve konunun sonunda üç kullanan tam bir örnek bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d8ec0-106">Each return type is examined in one of the following sections, and you can find a full example that uses all three types at the end of the topic.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d8ec0-107">Örneği çalıştırmak için Visual Studio 2012 veya daha yeni ve .NET Framework 4.5 veya daha yeni bilgisayarınızda yüklü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d8ec0-107">To run the example, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
##  <a name="BKMK_TaskTReturnType"></a> <span data-ttu-id="d8ec0-108">Task(T) dönüş türü</span><span class="sxs-lookup"><span data-stu-id="d8ec0-108">Task(T) Return Type</span></span>  
 <span data-ttu-id="d8ec0-109"><xref:System.Threading.Tasks.Task%601> Dönüş türü içeren bir zaman uyumsuz yöntem için kullanılan bir [dönmek](../../../../visual-basic/language-reference/statements/return-statement.md) işleneni türüne sahip deyimi `TResult`.</span><span class="sxs-lookup"><span data-stu-id="d8ec0-109">The <xref:System.Threading.Tasks.Task%601> return type is used for an async method that contains a [Return](../../../../visual-basic/language-reference/statements/return-statement.md) statement in which the operand has type `TResult`.</span></span>  
  
 <span data-ttu-id="d8ec0-110">Aşağıdaki örnekte, `TaskOfT_MethodAsync` async yöntemi bir tamsayı döndürür bir dönüş ifadesi içeriyor.</span><span class="sxs-lookup"><span data-stu-id="d8ec0-110">In the following example, the `TaskOfT_MethodAsync` async method contains a return statement that returns an integer.</span></span> <span data-ttu-id="d8ec0-111">Bu nedenle, yöntem bildirimi dönüş türünü belirtmeniz gerekir `Task(Of Integer)`.</span><span class="sxs-lookup"><span data-stu-id="d8ec0-111">Therefore, the method declaration must specify a return type of `Task(Of Integer)`.</span></span>  
  
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
  
 <span data-ttu-id="d8ec0-112">Zaman `TaskOfT_MethodAsync` çağrılır bir bekleme ifade içinde bekleme ifade tamsayı değerini alır (değerini `leisureHours`) tarafından döndürülen görev depolanan `TaskOfT_MethodAsync`.</span><span class="sxs-lookup"><span data-stu-id="d8ec0-112">When `TaskOfT_MethodAsync` is called from within an await expression, the await expression retrieves the integer value (the value of `leisureHours`) that's stored in the task that's returned by `TaskOfT_MethodAsync`.</span></span> <span data-ttu-id="d8ec0-113">Hakkında daha fazla bilgi için ifadeleri await, bkz: [Await işleci](../../../../visual-basic/language-reference/operators/await-operator.md).</span><span class="sxs-lookup"><span data-stu-id="d8ec0-113">For more information about await expressions, see [Await Operator](../../../../visual-basic/language-reference/operators/await-operator.md).</span></span>  
  
 <span data-ttu-id="d8ec0-114">Aşağıdaki kod çağırır ve yöntem bekler `TaskOfT_MethodAsync`.</span><span class="sxs-lookup"><span data-stu-id="d8ec0-114">The following code calls and awaits method `TaskOfT_MethodAsync`.</span></span> <span data-ttu-id="d8ec0-115">Sonuç atandığı `result1` değişkeni.</span><span class="sxs-lookup"><span data-stu-id="d8ec0-115">The result is assigned to the `result1` variable.</span></span>  
  
```vb  
' Call and await the Task(Of T)-returning async method in the same statement.  
Dim result1 As Integer = Await TaskOfT_MethodAsync()  
```  
  
 <span data-ttu-id="d8ec0-116">Bu çağrı ayırarak nasıl gerçekleştiğini daha iyi anlamak `TaskOfT_MethodAsync` uygulamadan `Await`, aşağıdaki kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="d8ec0-116">You can better understand how this happens by separating the call to `TaskOfT_MethodAsync` from the application of `Await`, as the following code shows.</span></span> <span data-ttu-id="d8ec0-117">Yöntemine yapılan bir çağrı `TaskOfT_MethodAsync` hemen beklemenin döndürür değil bir `Task(Of Integer)`yöntemi bildiriminden beklediğiniz gibi.</span><span class="sxs-lookup"><span data-stu-id="d8ec0-117">A call to method `TaskOfT_MethodAsync` that isn't immediately awaited returns a `Task(Of Integer)`, as you would expect from the declaration of the method.</span></span> <span data-ttu-id="d8ec0-118">Görev atandığı `integerTask` örnekte değişken.</span><span class="sxs-lookup"><span data-stu-id="d8ec0-118">The task is assigned to the `integerTask` variable in the example.</span></span> <span data-ttu-id="d8ec0-119">Çünkü `integerTask` olan bir <xref:System.Threading.Tasks.Task%601>, içerdiği bir <xref:System.Threading.Tasks.Task%601.Result> türündeki özelliği `TResult`.</span><span class="sxs-lookup"><span data-stu-id="d8ec0-119">Because `integerTask` is a <xref:System.Threading.Tasks.Task%601>, it contains a <xref:System.Threading.Tasks.Task%601.Result> property of type `TResult`.</span></span> <span data-ttu-id="d8ec0-120">Bu durumda, TResult bir tamsayı türünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d8ec0-120">In this case, TResult represents an integer type.</span></span> <span data-ttu-id="d8ec0-121">Zaman `Await` uygulanan `integerTask`, içeriğini bekleme ifadeyi hesaplar <xref:System.Threading.Tasks.Task%601.Result%2A> özelliği `integerTask`.</span><span class="sxs-lookup"><span data-stu-id="d8ec0-121">When `Await` is applied to `integerTask`, the await expression evaluates to the contents of the <xref:System.Threading.Tasks.Task%601.Result%2A> property of `integerTask`.</span></span> <span data-ttu-id="d8ec0-122">Değer atandığı `result2` değişkeni.</span><span class="sxs-lookup"><span data-stu-id="d8ec0-122">The value is assigned to the `result2` variable.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="d8ec0-123"><xref:System.Threading.Tasks.Task%601.Result%2A> Özelliği engelleyen bir özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="d8ec0-123">The <xref:System.Threading.Tasks.Task%601.Result%2A> property is a blocking property.</span></span> <span data-ttu-id="d8ec0-124">Görevini bitmeden önce erişmeyi denerseniz, şu anda etkin olan iş parçacığının görevi tamamlandıktan ve değeri kullanılabilir kadar engellendi.</span><span class="sxs-lookup"><span data-stu-id="d8ec0-124">If you try to access it before its task is finished, the thread that's currently active is blocked until the task completes and the value is available.</span></span> <span data-ttu-id="d8ec0-125">Çoğu durumda, kullanarak değeri erişmelidir `Await` özelliği doğrudan erişimini yerine.</span><span class="sxs-lookup"><span data-stu-id="d8ec0-125">In most cases, you should access the value by using `Await` instead of accessing the property directly.</span></span>  
  
```vb  
' Call and await in separate statements.  
Dim integerTask As Task(Of Integer) = TaskOfT_MethodAsync()  
  
' You can do other work that does not rely on resultTask before awaiting.  
textBox1.Text &= String.Format("Application can continue working while the Task(Of T) runs. . . . " & vbCrLf)  
  
Dim result2 As Integer = Await integerTask  
```  
  
 <span data-ttu-id="d8ec0-126">Aşağıdaki kod görüntü deyimlerinde doğrulayın değerlerini `result1` değişkeni, `result2` , değişken ve `Result` özelliği aynıdır.</span><span class="sxs-lookup"><span data-stu-id="d8ec0-126">The display statements in the following code verify that the values of the `result1` variable, the `result2` variable, and the `Result` property are the same.</span></span> <span data-ttu-id="d8ec0-127">Unutmayın `Result` engelleyen bir özelliktir ve görevini beklemenin önce erişilen döndürmemelidir.</span><span class="sxs-lookup"><span data-stu-id="d8ec0-127">Remember that the `Result` property is a blocking property and shouldn't be accessed before its task has been awaited.</span></span>  
  
```vb  
' Display the values of the result1 variable, the result2 variable, and  
' the resultTask.Result property.  
textBox1.Text &= String.Format(vbCrLf & "Value of result1 variable:   {0}" & vbCrLf, result1)  
textBox1.Text &= String.Format("Value of result2 variable:   {0}" & vbCrLf, result2)  
textBox1.Text &= String.Format("Value of resultTask.Result:  {0}" & vbCrLf, integerTask.Result)  
```  
  
##  <a name="BKMK_TaskReturnType"></a> <span data-ttu-id="d8ec0-128">Görev dönüş türü</span><span class="sxs-lookup"><span data-stu-id="d8ec0-128">Task Return Type</span></span>  
 <span data-ttu-id="d8ec0-129">Return deyimi içeren yok veya işleneni genellikle döndürmez bir return deyimi içeren zaman uyumsuz yöntemleri dönüş türüne sahip <xref:System.Threading.Tasks.Task>.</span><span class="sxs-lookup"><span data-stu-id="d8ec0-129">Async methods that don't contain a return statement or that contain a return statement that doesn't return an operand usually have a return type of <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="d8ec0-130">Bu tür yöntemleri olur [alt](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) eşzamanlı olarak çalışmasına yazılmışsa yordamlar.</span><span class="sxs-lookup"><span data-stu-id="d8ec0-130">Such methods would be [Sub](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) procedures if they were written to run synchronously.</span></span> <span data-ttu-id="d8ec0-131">Kullanırsanız, bir `Task` dönüş türü için bir zaman uyumsuz yöntemi, bir arama yöntemi kullanabilirsiniz bir `Await` çağrılan zaman uyumsuz yöntem tamamlanana kadar arayanın tamamlama askıya almak için işleci.</span><span class="sxs-lookup"><span data-stu-id="d8ec0-131">If you use a `Task` return type for an async method, a calling method can use an `Await` operator to suspend the caller's completion until the called async method has finished.</span></span>  
  
 <span data-ttu-id="d8ec0-132">Aşağıdaki örnekte, zaman uyumsuz yöntem `Task_MethodAsync` bir dönüş ifadesi içermiyor.</span><span class="sxs-lookup"><span data-stu-id="d8ec0-132">In the following example, async method `Task_MethodAsync` doesn't contain a return statement.</span></span> <span data-ttu-id="d8ec0-133">Bu nedenle, dönüş türü belirtmek `Task` yönteminde sağlayan `Task_MethodAsync` beklemenin için.</span><span class="sxs-lookup"><span data-stu-id="d8ec0-133">Therefore, you specify a return type of `Task` for the method, which enables `Task_MethodAsync` to be awaited.</span></span> <span data-ttu-id="d8ec0-134">Tanımını `Task` türü içermez bir `Result` dönüş değeri depolamak için özellik.</span><span class="sxs-lookup"><span data-stu-id="d8ec0-134">The definition of the `Task` type doesn't include a `Result` property to store a return value.</span></span>  
  
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
  
 <span data-ttu-id="d8ec0-135">`Task_MethodAsync` çağrılan ve arama deyim için bir zaman uyumlu benzer bir bekleme deyim yerine bir bekleme deyimi kullanarak beklemenin `Sub` veya void döndüren yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d8ec0-135">`Task_MethodAsync` is called and awaited by using an await statement instead of an await expression, similar to the calling statement for a synchronous `Sub` or void-returning method.</span></span> <span data-ttu-id="d8ec0-136">Uygulamasının bir `Await` işleci bu durumda bir değer üretmek değil.</span><span class="sxs-lookup"><span data-stu-id="d8ec0-136">The application of an `Await` operator in this case doesn't produce a value.</span></span>  
  
 <span data-ttu-id="d8ec0-137">Aşağıdaki kod çağırır ve yöntem bekler `Task_MethodAsync`.</span><span class="sxs-lookup"><span data-stu-id="d8ec0-137">The following code calls and awaits method `Task_MethodAsync`.</span></span>  
  
```vb  
' Call and await the Task-returning async method in the same statement.  
Await Task_MethodAsync()  
```  
  
 <span data-ttu-id="d8ec0-138">Önceki gibi <xref:System.Threading.Tasks.Task%601> örnek, çağrısı ayırabilirsiniz `Task_MethodAsync` uygulamadan bir `Await` aşağıdaki gösterildiği gibi kod işleci.</span><span class="sxs-lookup"><span data-stu-id="d8ec0-138">As in the previous <xref:System.Threading.Tasks.Task%601> example, you can separate the call to `Task_MethodAsync` from the application of an `Await` operator, as the following code shows.</span></span> <span data-ttu-id="d8ec0-139">Ancak, unutmayın bir `Task` sahip olmayan bir `Result` özelliği ve bekleme operatörün uygulandığında herhangi bir değer üretilir bir `Task`.</span><span class="sxs-lookup"><span data-stu-id="d8ec0-139">However, remember that a `Task` doesn't have a `Result` property, and that no value is produced when an await operator is applied to a `Task`.</span></span>  
  
 <span data-ttu-id="d8ec0-140">Aşağıdaki kod arama ayıran `Task_MethodAsync` görev bekleyen gelen, `Task_MethodAsync` döndürür.</span><span class="sxs-lookup"><span data-stu-id="d8ec0-140">The following code separates calling `Task_MethodAsync` from awaiting the task that `Task_MethodAsync` returns.</span></span>  
  
```vb  
' Call and await in separate statements.  
Dim simpleTask As Task = Task_MethodAsync()  
  
' You can do other work that does not rely on simpleTask before awaiting.  
textBox1.Text &= String.Format(vbCrLf & "Application can continue working while the Task runs. . . ." & vbCrLf)  
  
Await simpleTask  
```  
  
##  <a name="BKMK_VoidReturnType"></a> <span data-ttu-id="d8ec0-141">Dönüş türü void</span><span class="sxs-lookup"><span data-stu-id="d8ec0-141">Void Return Type</span></span>  
 <span data-ttu-id="d8ec0-142">Birincil kullanımını `Sub` yordamları olan olay işleyicileri ile söz konusu olduğunda (diğer dillerdeki dönüş türü void olarak adlandırılır) bir dönüş türü.</span><span class="sxs-lookup"><span data-stu-id="d8ec0-142">The primary use of `Sub` procedures is in event handlers, where there is no return type (referred to as a void return type in other languages).</span></span> <span data-ttu-id="d8ec0-143">Void dönüş void döndüren yöntemleri geçersiz kılmak için de kullanılabilir veya kategorilere ayrılabilir etkinliklerini gerçekleştiren yöntemleri için farklı "yangın ve unuttunuz."</span><span class="sxs-lookup"><span data-stu-id="d8ec0-143">A void return also can be used to override void-returning methods or for methods that perform activities that can be categorized as "fire and forget."</span></span> <span data-ttu-id="d8ec0-144">Ancak, döndürmelidir bir `Task` mümkün olduğunda, bir geçersiz kılma döndüren zaman uyumsuz yöntem beklemenin olduğundan.</span><span class="sxs-lookup"><span data-stu-id="d8ec0-144">However, you should return a `Task` wherever possible, because a void-returning async method can't be awaited.</span></span> <span data-ttu-id="d8ec0-145">Böyle bir yöntemin herhangi bir çağırıcı tamamlanması için çağrılan zaman uyumsuz yöntemi beklemeden tamamlanıncaya kadar devam edebilirsiniz ve çağıranın tüm değerleri veya zaman uyumsuz yöntem oluşturur özel durumlar bağımsız olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d8ec0-145">Any caller of such a method must be able to continue to completion without waiting for the called async method to finish, and the caller must be independent of any values or exceptions that the async method generates.</span></span>  
  
 <span data-ttu-id="d8ec0-146">Bir geçersiz kılma döndüren zaman uyumsuz yöntem arayan yönteminden oluşturulan özel durumları yakalamak olamaz ve böyle işlenmeyen özel durumlar, uygulamanızın başarısız olmasına yol açabilir.</span><span class="sxs-lookup"><span data-stu-id="d8ec0-146">The caller of a void-returning async method can't catch exceptions that are thrown from the method, and such unhandled exceptions are likely to cause your application to fail.</span></span> <span data-ttu-id="d8ec0-147">Bir özel durum döndüren bir zaman uyumsuz yöntem oluşursa bir <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601>, özel durum döndürülen görevde depolanır ve görev beklemenin zaman işlenemezse.</span><span class="sxs-lookup"><span data-stu-id="d8ec0-147">If an exception occurs in an async method that returns a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>, the exception is stored in the returned task, and rethrown when the task is awaited.</span></span> <span data-ttu-id="d8ec0-148">Bu nedenle, bir özel durum oluşturmak üzere herhangi bir zaman uyumsuz yöntemi dönüş türüne sahip olduğundan emin olun <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601> ve yöntemine yönelik çağrılar beklemenin.</span><span class="sxs-lookup"><span data-stu-id="d8ec0-148">Therefore, make sure that any async method that can produce an exception has a return type of <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> and that calls to the method are awaited.</span></span>  
  
 <span data-ttu-id="d8ec0-149">Zaman uyumsuz yöntemleri özel durumlarını yakalama hakkında daha fazla bilgi için bkz: [deneyin... Catch... Finally ifadesi](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="d8ec0-149">For more information about how to catch exceptions in async methods, see [Try...Catch...Finally Statement](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
 <span data-ttu-id="d8ec0-150">Aşağıdaki kod bir zaman uyumsuz olay işleyicisini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d8ec0-150">The following code defines an async event handler.</span></span>  
  
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
  
##  <a name="BKMK_Example"></a> <span data-ttu-id="d8ec0-151">Tam örnek</span><span class="sxs-lookup"><span data-stu-id="d8ec0-151">Complete Example</span></span>  
 <span data-ttu-id="d8ec0-152">Aşağıdaki Windows Presentation Foundation (WPF) projesi, bu konudaki kod örnekleri içerir.</span><span class="sxs-lookup"><span data-stu-id="d8ec0-152">The following Windows Presentation Foundation (WPF) project contains the code examples from this topic.</span></span>  
  
 <span data-ttu-id="d8ec0-153">Projeyi çalıştırmak için aşağıdaki adımları gerçekleştirin:</span><span class="sxs-lookup"><span data-stu-id="d8ec0-153">To run the project, perform the following steps:</span></span>  
  
1.  <span data-ttu-id="d8ec0-154">Visual Studio'yu başlatın.</span><span class="sxs-lookup"><span data-stu-id="d8ec0-154">Start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="d8ec0-155">Menü çubuğunda seçin **dosya**, **yeni**, **proje**.</span><span class="sxs-lookup"><span data-stu-id="d8ec0-155">On the menu bar, choose **File**, **New**, **Project**.</span></span>  
  
     <span data-ttu-id="d8ec0-156">**Yeni proje** iletişim kutusu açılır.</span><span class="sxs-lookup"><span data-stu-id="d8ec0-156">The **New Project** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="d8ec0-157">İçinde **yüklü**, **şablonları** kategorisi seçin **Visual Basic**ve ardından **Windows**.</span><span class="sxs-lookup"><span data-stu-id="d8ec0-157">In the **Installed**, **Templates** category, choose **Visual Basic**, and then choose **Windows**.</span></span> <span data-ttu-id="d8ec0-158">Seçin **WPF uygulaması** proje türleri listesinden.</span><span class="sxs-lookup"><span data-stu-id="d8ec0-158">Choose **WPF Application** from the list of project types.</span></span>  
  
4.  <span data-ttu-id="d8ec0-159">Girin `AsyncReturnTypes` projesinin adı olarak ve ardından **Tamam** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="d8ec0-159">Enter `AsyncReturnTypes` as the name of the project, and then choose the **OK** button.</span></span>  
  
     <span data-ttu-id="d8ec0-160">Yeni Proje görünür **Çözüm Gezgini**.</span><span class="sxs-lookup"><span data-stu-id="d8ec0-160">The new project appears in **Solution Explorer**.</span></span>  
  
5.  <span data-ttu-id="d8ec0-161">Visual Studio Kod Düzenleyicisi'nde seçin **MainWindow.xaml** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="d8ec0-161">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>  
  
     <span data-ttu-id="d8ec0-162">Sekme görünür durumda değilse, kısayol menüsünde MainWindow.xaml içinde açık **Çözüm Gezgini**ve ardından **açmak**.</span><span class="sxs-lookup"><span data-stu-id="d8ec0-162">If the tab is not visible, open the shortcut menu for MainWindow.xaml in **Solution Explorer**, and then choose **Open**.</span></span>  
  
6.  <span data-ttu-id="d8ec0-163">İçinde **XAML** MainWindow.xaml, pencerenin kodu aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="d8ec0-163">In the **XAML** window of MainWindow.xaml, replace the code with the following code.</span></span>  
  
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
  
     <span data-ttu-id="d8ec0-164">Bir düğmeyi ve bir metin kutusu içeren basit bir pencere görünür **tasarım** MainWindow.xaml penceresi.</span><span class="sxs-lookup"><span data-stu-id="d8ec0-164">A simple window that contains a text box and a button appears in the **Design** window of MainWindow.xaml.</span></span>  
  
7.  <span data-ttu-id="d8ec0-165">İçinde **Çözüm Gezgini**MainWindow.xaml.vb için kısayol menüsünü açın ve ardından **görünümü kodu**.</span><span class="sxs-lookup"><span data-stu-id="d8ec0-165">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.vb, and then choose **View Code**.</span></span>  
  
8.  <span data-ttu-id="d8ec0-166">MainWindow.xaml.vb kodu aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="d8ec0-166">Replace the code in MainWindow.xaml.vb with the following code.</span></span>  
  
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
  
9. <span data-ttu-id="d8ec0-167">Programını çalıştırın ve ardından için F5 tuşuna seçin **Başlat** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="d8ec0-167">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
     <span data-ttu-id="d8ec0-168">Şu çıktı görünür.</span><span class="sxs-lookup"><span data-stu-id="d8ec0-168">The following output should appear.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d8ec0-169">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d8ec0-169">See Also</span></span>  
 <xref:System.Threading.Tasks.Task.FromResult%2A>  
 [<span data-ttu-id="d8ec0-170">İzlenecek yol: Async kullanarak Web'e erişme ve bekleme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d8ec0-170">Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)  
 [<span data-ttu-id="d8ec0-171">(Visual Basic) zaman uyumsuz programlarda denetim akışı</span><span class="sxs-lookup"><span data-stu-id="d8ec0-171">Control Flow in Async Programs (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)  
 [<span data-ttu-id="d8ec0-172">Async</span><span class="sxs-lookup"><span data-stu-id="d8ec0-172">Async</span></span>](../../../../visual-basic/language-reference/modifiers/async.md)  
 [<span data-ttu-id="d8ec0-173">Await İşleci</span><span class="sxs-lookup"><span data-stu-id="d8ec0-173">Await Operator</span></span>](../../../../visual-basic/language-reference/operators/await-operator.md)
