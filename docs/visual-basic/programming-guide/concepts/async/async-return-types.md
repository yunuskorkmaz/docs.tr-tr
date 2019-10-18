---
title: Zaman uyumsuz dönüş türleri (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 07890291-ee72-42d3-932a-fa4d312f2c60
ms.openlocfilehash: f85b3ec536033fd6d3cdec8f5a6ac4f9f66077f3
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524335"
---
# <a name="async-return-types-visual-basic"></a><span data-ttu-id="6604a-102">Zaman uyumsuz dönüş türleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6604a-102">Async Return Types (Visual Basic)</span></span>

<span data-ttu-id="6604a-103">Zaman uyumsuz metotlarda üç olası dönüş türü vardır: <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.Task> ve void.</span><span class="sxs-lookup"><span data-stu-id="6604a-103">Async methods have three possible return types: <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.Task>, and void.</span></span> <span data-ttu-id="6604a-104">Visual Basic, void dönüş türü bir [alt](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) yordam olarak yazılır.</span><span class="sxs-lookup"><span data-stu-id="6604a-104">In Visual Basic, the void return type is written as a [Sub](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) procedure.</span></span> <span data-ttu-id="6604a-105">Zaman uyumsuz yöntemler hakkında daha fazla bilgi için bkz. [Async ve await Ile zaman uyumsuz programlama (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="6604a-105">For more information about async methods, see [Asynchronous Programming with Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md).</span></span>

<span data-ttu-id="6604a-106">Her dönüş türü aşağıdaki bölümlerden birinde incelenir ve konunun sonunda her üç türü kullanan tam bir örnek bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6604a-106">Each return type is examined in one of the following sections, and you can find a full example that uses all three types at the end of the topic.</span></span>

> [!NOTE]
> <span data-ttu-id="6604a-107">Örneği çalıştırmak için, bilgisayarınızda Visual Studio 2012 veya daha yeni bir sürümü ve .NET Framework 4,5 ya da daha yeni bir sürümü yüklü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6604a-107">To run the example, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>

## <a name="BKMK_TaskTReturnType"></a><span data-ttu-id="6604a-108">Görev (T) dönüş türü</span><span class="sxs-lookup"><span data-stu-id="6604a-108">Task(T) Return Type</span></span>

<span data-ttu-id="6604a-109">@No__t_0 dönüş türü, işleneninin tür `TResult` sahip olduğu bir [Return](../../../../visual-basic/language-reference/statements/return-statement.md) ifadesini içeren zaman uyumsuz bir yöntem için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6604a-109">The <xref:System.Threading.Tasks.Task%601> return type is used for an async method that contains a [Return](../../../../visual-basic/language-reference/statements/return-statement.md) statement in which the operand has type `TResult`.</span></span>

<span data-ttu-id="6604a-110">Aşağıdaki örnekte, `TaskOfT_MethodAsync` async yöntemi bir Integer döndüren return ifadesini içerir.</span><span class="sxs-lookup"><span data-stu-id="6604a-110">In the following example, the `TaskOfT_MethodAsync` async method contains a return statement that returns an integer.</span></span> <span data-ttu-id="6604a-111">Bu nedenle, yöntem bildirimi `Task(Of Integer)` bir dönüş türü belirtmelidir.</span><span class="sxs-lookup"><span data-stu-id="6604a-111">Therefore, the method declaration must specify a return type of `Task(Of Integer)`.</span></span>

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

<span data-ttu-id="6604a-112">Bir await ifadesi içinden `TaskOfT_MethodAsync` çağrıldığında await ifadesi, `TaskOfT_MethodAsync` tarafından döndürülen görevde depolanan tamsayı değerini (`leisureHours` değeri) alır.</span><span class="sxs-lookup"><span data-stu-id="6604a-112">When `TaskOfT_MethodAsync` is called from within an await expression, the await expression retrieves the integer value (the value of `leisureHours`) that's stored in the task that's returned by `TaskOfT_MethodAsync`.</span></span> <span data-ttu-id="6604a-113">Await ifadeleri hakkında daha fazla bilgi için bkz. [Await işleci](../../../../visual-basic/language-reference/operators/await-operator.md).</span><span class="sxs-lookup"><span data-stu-id="6604a-113">For more information about await expressions, see [Await Operator](../../../../visual-basic/language-reference/operators/await-operator.md).</span></span>

<span data-ttu-id="6604a-114">Aşağıdaki kod çağrıları ve await metodu `TaskOfT_MethodAsync`.</span><span class="sxs-lookup"><span data-stu-id="6604a-114">The following code calls and awaits method `TaskOfT_MethodAsync`.</span></span> <span data-ttu-id="6604a-115">Sonuç `result1` değişkenine atanır.</span><span class="sxs-lookup"><span data-stu-id="6604a-115">The result is assigned to the `result1` variable.</span></span>

```vb
' Call and await the Task(Of T)-returning async method in the same statement.
Dim result1 As Integer = Await TaskOfT_MethodAsync()
```

<span data-ttu-id="6604a-116">Aşağıdaki kodun gösterdiği gibi, `TaskOfT_MethodAsync` çağrısını `Await` uygulamasından ayırarak bunun nasıl gerçekleştiğini daha iyi anlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6604a-116">You can better understand how this happens by separating the call to `TaskOfT_MethodAsync` from the application of `Await`, as the following code shows.</span></span> <span data-ttu-id="6604a-117">Yönteminin bildiriminden bekleyebileceğiniz gibi, hemen beklenmiş olmayan bir yöntem `TaskOfT_MethodAsync` çağrısı `Task(Of Integer)` döndürür.</span><span class="sxs-lookup"><span data-stu-id="6604a-117">A call to method `TaskOfT_MethodAsync` that isn't immediately awaited returns a `Task(Of Integer)`, as you would expect from the declaration of the method.</span></span> <span data-ttu-id="6604a-118">Görev, örnekteki `integerTask` değişkenine atanır.</span><span class="sxs-lookup"><span data-stu-id="6604a-118">The task is assigned to the `integerTask` variable in the example.</span></span> <span data-ttu-id="6604a-119">@No__t_0 bir <xref:System.Threading.Tasks.Task%601> olduğundan, `TResult` türünde bir <xref:System.Threading.Tasks.Task%601.Result> özelliği içerir.</span><span class="sxs-lookup"><span data-stu-id="6604a-119">Because `integerTask` is a <xref:System.Threading.Tasks.Task%601>, it contains a <xref:System.Threading.Tasks.Task%601.Result> property of type `TResult`.</span></span> <span data-ttu-id="6604a-120">Bu durumda, TResult bir tamsayı türünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="6604a-120">In this case, TResult represents an integer type.</span></span> <span data-ttu-id="6604a-121">@No__t_0 `integerTask` uygulandığında, await ifadesi `integerTask` <xref:System.Threading.Tasks.Task%601.Result%2A> özelliğinin içeriğini değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="6604a-121">When `Await` is applied to `integerTask`, the await expression evaluates to the contents of the <xref:System.Threading.Tasks.Task%601.Result%2A> property of `integerTask`.</span></span> <span data-ttu-id="6604a-122">Değer `result2` değişkenine atanır.</span><span class="sxs-lookup"><span data-stu-id="6604a-122">The value is assigned to the `result2` variable.</span></span>

> [!WARNING]
> <span data-ttu-id="6604a-123">@No__t_0 özelliği engelleyici bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="6604a-123">The <xref:System.Threading.Tasks.Task%601.Result%2A> property is a blocking property.</span></span> <span data-ttu-id="6604a-124">Görevi tamamlanmadan önce ona erişmeye çalışırsanız, etkin olan iş parçacığı, görev tamamlanana ve değer kullanılabilir olana kadar engellenir.</span><span class="sxs-lookup"><span data-stu-id="6604a-124">If you try to access it before its task is finished, the thread that's currently active is blocked until the task completes and the value is available.</span></span> <span data-ttu-id="6604a-125">Çoğu durumda, özelliği doğrudan erişmek yerine `Await` kullanarak değere erişmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="6604a-125">In most cases, you should access the value by using `Await` instead of accessing the property directly.</span></span>

```vb
' Call and await in separate statements.
Dim integerTask As Task(Of Integer) = TaskOfT_MethodAsync()

' You can do other work that does not rely on resultTask before awaiting.
textBox1.Text &= String.Format("Application can continue working while the Task(Of T) runs. . . . " & vbCrLf)

Dim result2 As Integer = Await integerTask
```

<span data-ttu-id="6604a-126">Aşağıdaki koddaki görüntüleme deyimleri `result1` değişkeninin değerlerinin, `result2` değişkeninin ve `Result` özelliğinin aynı olduğunu doğrular.</span><span class="sxs-lookup"><span data-stu-id="6604a-126">The display statements in the following code verify that the values of the `result1` variable, the `result2` variable, and the `Result` property are the same.</span></span> <span data-ttu-id="6604a-127">@No__t_0 özelliğinin engelleme özelliği olduğunu ve görevi beklenmeden önce erişilmeyeceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="6604a-127">Remember that the `Result` property is a blocking property and shouldn't be accessed before its task has been awaited.</span></span>

```vb
' Display the values of the result1 variable, the result2 variable, and
' the resultTask.Result property.
textBox1.Text &= String.Format(vbCrLf & "Value of result1 variable:   {0}" & vbCrLf, result1)
textBox1.Text &= String.Format("Value of result2 variable:   {0}" & vbCrLf, result2)
textBox1.Text &= String.Format("Value of resultTask.Result:  {0}" & vbCrLf, integerTask.Result)
```

## <a name="BKMK_TaskReturnType"></a><span data-ttu-id="6604a-128">Görev dönüş türü</span><span class="sxs-lookup"><span data-stu-id="6604a-128">Task Return Type</span></span>

<span data-ttu-id="6604a-129">Dönüş açıklaması içermeyen veya bir işleneni döndürmeyen bir return ifadesini içeren zaman uyumsuz metotlar genellikle <xref:System.Threading.Tasks.Task> dönüş türüne sahiptir.</span><span class="sxs-lookup"><span data-stu-id="6604a-129">Async methods that don't contain a return statement or that contain a return statement that doesn't return an operand usually have a return type of <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="6604a-130">Bu tür yöntemler, zaman uyumlu olarak çalışmak üzere yazılmışsa [alt](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) yordamlar olur.</span><span class="sxs-lookup"><span data-stu-id="6604a-130">Such methods would be [Sub](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) procedures if they were written to run synchronously.</span></span> <span data-ttu-id="6604a-131">Zaman uyumsuz bir yöntem için `Task` dönüş türü kullanırsanız, çağıran bir yöntem, çağrılan zaman uyumsuz yöntem tamamlanana kadar arayanın tamamlanmasını askıya almak için bir `Await` işleci kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="6604a-131">If you use a `Task` return type for an async method, a calling method can use an `Await` operator to suspend the caller's completion until the called async method has finished.</span></span>

<span data-ttu-id="6604a-132">Aşağıdaki örnekte, zaman uyumsuz yöntem `Task_MethodAsync` return ifadesini içermez.</span><span class="sxs-lookup"><span data-stu-id="6604a-132">In the following example, async method `Task_MethodAsync` doesn't contain a return statement.</span></span> <span data-ttu-id="6604a-133">Bu nedenle, `Task_MethodAsync` beklenmesine olanak sağlayan, yöntemi için `Task` dönüş türünü belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6604a-133">Therefore, you specify a return type of `Task` for the method, which enables `Task_MethodAsync` to be awaited.</span></span> <span data-ttu-id="6604a-134">@No__t_0 türünün tanımı bir dönüş değeri depolamak için bir `Result` özelliği içermiyor.</span><span class="sxs-lookup"><span data-stu-id="6604a-134">The definition of the `Task` type doesn't include a `Result` property to store a return value.</span></span>

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

<span data-ttu-id="6604a-135">`Task_MethodAsync`, zaman uyumlu bir `Sub` veya void döndüren bir yöntem için çağırma deyimine benzer bir await ifadesi yerine await deyimi kullanılarak çağrılır ve bekletildi.</span><span class="sxs-lookup"><span data-stu-id="6604a-135">`Task_MethodAsync` is called and awaited by using an await statement instead of an await expression, similar to the calling statement for a synchronous `Sub` or void-returning method.</span></span> <span data-ttu-id="6604a-136">Bu durumda `Await` işlecinin uygulaması bir değer üretmez.</span><span class="sxs-lookup"><span data-stu-id="6604a-136">The application of an `Await` operator in this case doesn't produce a value.</span></span>

<span data-ttu-id="6604a-137">Aşağıdaki kod çağrıları ve await metodu `Task_MethodAsync`.</span><span class="sxs-lookup"><span data-stu-id="6604a-137">The following code calls and awaits method `Task_MethodAsync`.</span></span>

```vb
' Call and await the Task-returning async method in the same statement.
Await Task_MethodAsync()
```

<span data-ttu-id="6604a-138">Önceki <xref:System.Threading.Tasks.Task%601> örneğinde olduğu gibi, aşağıdaki kodun gösterdiği gibi, bir `Await` işlecinin uygulamasından `Task_MethodAsync` çağrısını ayırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6604a-138">As in the previous <xref:System.Threading.Tasks.Task%601> example, you can separate the call to `Task_MethodAsync` from the application of an `Await` operator, as the following code shows.</span></span> <span data-ttu-id="6604a-139">Ancak, bir `Task` bir `Result` özelliğine sahip olmadığını ve bir `Task` bir Await işleci uygulandığında hiçbir değer üretilmediğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="6604a-139">However, remember that a `Task` doesn't have a `Result` property, and that no value is produced when an await operator is applied to a `Task`.</span></span>

<span data-ttu-id="6604a-140">Aşağıdaki kod, `Task_MethodAsync` döndürdüğü görevi bekleyen çağrıyı `Task_MethodAsync` ayırır.</span><span class="sxs-lookup"><span data-stu-id="6604a-140">The following code separates calling `Task_MethodAsync` from awaiting the task that `Task_MethodAsync` returns.</span></span>

```vb
' Call and await in separate statements.
Dim simpleTask As Task = Task_MethodAsync()

' You can do other work that does not rely on simpleTask before awaiting.
textBox1.Text &= String.Format(vbCrLf & "Application can continue working while the Task runs. . . ." & vbCrLf)

Await simpleTask
```

## <a name="BKMK_VoidReturnType"></a><span data-ttu-id="6604a-141">Void dönüş türü</span><span class="sxs-lookup"><span data-stu-id="6604a-141">Void Return Type</span></span>

<span data-ttu-id="6604a-142">@No__t_0 yordamların birincil kullanımı, dönüş türü olmayan (diğer dillerde void dönüş türü olarak ifade edilen) olay işleyicileridir.</span><span class="sxs-lookup"><span data-stu-id="6604a-142">The primary use of `Sub` procedures is in event handlers, where there is no return type (referred to as a void return type in other languages).</span></span> <span data-ttu-id="6604a-143">Void Return Ayrıca, void döndüren yöntemleri geçersiz kılmak için veya "Fire ve unut" olarak kategorilere ayrılmamış etkinlikler gerçekleştiren yöntemler için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6604a-143">A void return also can be used to override void-returning methods or for methods that perform activities that can be categorized as "fire and forget."</span></span> <span data-ttu-id="6604a-144">Ancak, void döndüren zaman uyumsuz bir yöntem beklenmediğinden, mümkün olan her yerde `Task` döndürmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="6604a-144">However, you should return a `Task` wherever possible, because a void-returning async method can't be awaited.</span></span> <span data-ttu-id="6604a-145">Bu tür bir yöntemi çağıran, çağrılan zaman uyumsuz yöntemin tamamlanmasını beklemeden tamamlamaya devam edebilmelidir ve çağıranın, zaman uyumsuz yöntemin ürettiği herhangi bir değerden veya özel durumlardan bağımsız olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="6604a-145">Any caller of such a method must be able to continue to completion without waiting for the called async method to finish, and the caller must be independent of any values or exceptions that the async method generates.</span></span>

<span data-ttu-id="6604a-146">Void döndüren zaman uyumsuz bir yöntemi çağıran, yöntemden oluşturulan özel durumları yakalayabilir ve bu tür işlenmemiş özel durumlar uygulamanızın başarısız olmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="6604a-146">The caller of a void-returning async method can't catch exceptions that are thrown from the method, and such unhandled exceptions are likely to cause your application to fail.</span></span> <span data-ttu-id="6604a-147">Bir <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601> döndüren zaman uyumsuz yöntemde bir özel durum oluşursa, özel durum döndürülen görevde depolanır ve görev beklendiğinde yeniden oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="6604a-147">If an exception occurs in an async method that returns a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>, the exception is stored in the returned task, and rethrown when the task is awaited.</span></span> <span data-ttu-id="6604a-148">Bu nedenle, bir özel durum üretemeyen herhangi bir zaman uyumsuz yöntemin <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601> dönüş türüne sahip olduğundan ve yönteme yapılan çağrıların beklenmediğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="6604a-148">Therefore, make sure that any async method that can produce an exception has a return type of <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> and that calls to the method are awaited.</span></span>

<span data-ttu-id="6604a-149">Zaman uyumsuz yöntemlerde özel durumları yakalama hakkında daha fazla bilgi için bkz [. TRY... Yakala... Finally ekstresi](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="6604a-149">For more information about how to catch exceptions in async methods, see [Try...Catch...Finally Statement](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>

<span data-ttu-id="6604a-150">Aşağıdaki kod zaman uyumsuz bir olay işleyicisini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6604a-150">The following code defines an async event handler.</span></span>

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

## <a name="BKMK_Example"></a><span data-ttu-id="6604a-151">Örnek Tamam</span><span class="sxs-lookup"><span data-stu-id="6604a-151">Complete Example</span></span>

<span data-ttu-id="6604a-152">Aşağıdaki Windows Presentation Foundation (WPF) projesi bu konudan kod örneklerini içerir.</span><span class="sxs-lookup"><span data-stu-id="6604a-152">The following Windows Presentation Foundation (WPF) project contains the code examples from this topic.</span></span>

 <span data-ttu-id="6604a-153">Projeyi çalıştırmak için aşağıdaki adımları gerçekleştirin:</span><span class="sxs-lookup"><span data-stu-id="6604a-153">To run the project, perform the following steps:</span></span>

1. <span data-ttu-id="6604a-154">Visual Studio 'Yu başlatın.</span><span class="sxs-lookup"><span data-stu-id="6604a-154">Start Visual Studio.</span></span>

2. <span data-ttu-id="6604a-155">Menü çubuğunda **Dosya**, **Yeni**, **Proje**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="6604a-155">On the menu bar, choose **File**, **New**, **Project**.</span></span>

     <span data-ttu-id="6604a-156">**Yeni proje** iletişim kutusu açılır.</span><span class="sxs-lookup"><span data-stu-id="6604a-156">The **New Project** dialog box opens.</span></span>

3. <span data-ttu-id="6604a-157">**Yüklü**, **Şablonlar** kategorisinde **Visual Basic**ve ardından **Windows**' u seçin.</span><span class="sxs-lookup"><span data-stu-id="6604a-157">In the **Installed**, **Templates** category, choose **Visual Basic**, and then choose **Windows**.</span></span> <span data-ttu-id="6604a-158">Proje türleri listesinden **WPF uygulaması** ' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="6604a-158">Choose **WPF Application** from the list of project types.</span></span>

4. <span data-ttu-id="6604a-159">Projenin adı olarak `AsyncReturnTypes` girin ve **Tamam** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="6604a-159">Enter `AsyncReturnTypes` as the name of the project, and then choose the **OK** button.</span></span>

     <span data-ttu-id="6604a-160">Yeni proje **Çözüm Gezgini**görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="6604a-160">The new project appears in **Solution Explorer**.</span></span>

5. <span data-ttu-id="6604a-161">Visual Studio Code düzenleyicisinde **MainWindow. xaml** sekmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="6604a-161">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>

     <span data-ttu-id="6604a-162">Sekme görünür değilse, **Çözüm Gezgini**' de MainWindow. xaml için kısayol menüsünü açın ve **Aç**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="6604a-162">If the tab is not visible, open the shortcut menu for MainWindow.xaml in **Solution Explorer**, and then choose **Open**.</span></span>

6. <span data-ttu-id="6604a-163">MainWindow. xaml ' nin **xaml** penceresinde, kodu aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="6604a-163">In the **XAML** window of MainWindow.xaml, replace the code with the following code.</span></span>

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

     <span data-ttu-id="6604a-164">Bir metin kutusu ve bir düğme içeren basit bir pencere, MainWindow. xaml **Tasarım** penceresinde görünür.</span><span class="sxs-lookup"><span data-stu-id="6604a-164">A simple window that contains a text box and a button appears in the **Design** window of MainWindow.xaml.</span></span>

7. <span data-ttu-id="6604a-165">**Çözüm Gezgini**, MainWindow. xaml. vb için kısayol menüsünü açın ve **kodu görüntüle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="6604a-165">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.vb, and then choose **View Code**.</span></span>

8. <span data-ttu-id="6604a-166">MainWindow. xaml. vb içindeki kodu aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="6604a-166">Replace the code in MainWindow.xaml.vb with the following code.</span></span>

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

9. <span data-ttu-id="6604a-167">Programı çalıştırmak için F5 tuşunu seçin ve sonra **Başlat** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="6604a-167">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>

     <span data-ttu-id="6604a-168">Aşağıdaki çıkışın görünmesi gerekir:</span><span class="sxs-lookup"><span data-stu-id="6604a-168">The following output should appear:</span></span>

    ```console
    Application can continue working while the Task<T> runs. . . .

    Value of result1 variable:   5
    Value of result2 variable:   5
    Value of integerTask.Result: 5

    Sorry for the delay. . . .

    Application can continue working while the Task runs. . . .

    Sorry for the delay. . . .

    All done, exiting button-click event handler.
    ```

## <a name="see-also"></a><span data-ttu-id="6604a-169">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6604a-169">See also</span></span>

- <xref:System.Threading.Tasks.Task.FromResult%2A>
- [<span data-ttu-id="6604a-170">İzlenecek yol: Async ve await kullanarak Web 'e erişme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6604a-170">Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="6604a-171">Zaman uyumsuz programlarda denetim akışı (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6604a-171">Control Flow in Async Programs (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)
- [<span data-ttu-id="6604a-172">Async</span><span class="sxs-lookup"><span data-stu-id="6604a-172">Async</span></span>](../../../../visual-basic/language-reference/modifiers/async.md)
- [<span data-ttu-id="6604a-173">Await İşleci</span><span class="sxs-lookup"><span data-stu-id="6604a-173">Await Operator</span></span>](../../../../visual-basic/language-reference/operators/await-operator.md)
