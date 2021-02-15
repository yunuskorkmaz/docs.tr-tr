---
description: 'Daha fazla bilgi edinin: zaman uyumsuz dönüş türleri (Visual Basic)'
title: Zaman Uyumsuz Dönüş Türleri
ms.date: 07/20/2015
ms.assetid: 07890291-ee72-42d3-932a-fa4d312f2c60
ms.openlocfilehash: 12a7f577a89ff8f8037de879f9e37d6fdb917aa8
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100438924"
---
# <a name="async-return-types-visual-basic"></a><span data-ttu-id="df329-103">Zaman uyumsuz dönüş türleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="df329-103">Async Return Types (Visual Basic)</span></span>

<span data-ttu-id="df329-104">Zaman uyumsuz metotlarda üç olası dönüş türü vardır: <xref:System.Threading.Tasks.Task%601> , <xref:System.Threading.Tasks.Task> ve void.</span><span class="sxs-lookup"><span data-stu-id="df329-104">Async methods have three possible return types: <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.Task>, and void.</span></span> <span data-ttu-id="df329-105">Visual Basic, void dönüş türü bir [alt](../../language-features/procedures/sub-procedures.md) yordam olarak yazılır.</span><span class="sxs-lookup"><span data-stu-id="df329-105">In Visual Basic, the void return type is written as a [Sub](../../language-features/procedures/sub-procedures.md) procedure.</span></span> <span data-ttu-id="df329-106">Zaman uyumsuz yöntemler hakkında daha fazla bilgi için bkz. [Async ve await Ile zaman uyumsuz programlama (Visual Basic)](index.md).</span><span class="sxs-lookup"><span data-stu-id="df329-106">For more information about async methods, see [Asynchronous Programming with Async and Await (Visual Basic)](index.md).</span></span>

<span data-ttu-id="df329-107">Her dönüş türü aşağıdaki bölümlerden birinde incelenir ve konunun sonunda her üç türü kullanan tam bir örnek bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="df329-107">Each return type is examined in one of the following sections, and you can find a full example that uses all three types at the end of the topic.</span></span>

> [!NOTE]
> <span data-ttu-id="df329-108">Örneği çalıştırmak için, bilgisayarınızda Visual Studio 2012 veya daha yeni bir sürümü ve .NET Framework 4,5 ya da daha yeni bir sürümü yüklü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="df329-108">To run the example, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>

## <a name="taskt-return-type"></a><a name="BKMK_TaskTReturnType"></a> <span data-ttu-id="df329-109">Görev (T) dönüş türü</span><span class="sxs-lookup"><span data-stu-id="df329-109">Task(T) Return Type</span></span>

<span data-ttu-id="df329-110"><xref:System.Threading.Tasks.Task%601>Dönüş türü, işlenenin türü olan bir [Return](../../../language-reference/statements/return-statement.md) ifadesini içeren zaman uyumsuz bir yöntem için kullanılır `TResult` .</span><span class="sxs-lookup"><span data-stu-id="df329-110">The <xref:System.Threading.Tasks.Task%601> return type is used for an async method that contains a [Return](../../../language-reference/statements/return-statement.md) statement in which the operand has type `TResult`.</span></span>

<span data-ttu-id="df329-111">Aşağıdaki örnekte, `TaskOfT_MethodAsync` Async yöntemi bir tamsayı döndüren return ifadesini içerir.</span><span class="sxs-lookup"><span data-stu-id="df329-111">In the following example, the `TaskOfT_MethodAsync` async method contains a return statement that returns an integer.</span></span> <span data-ttu-id="df329-112">Bu nedenle, metot bildiriminin bir dönüş türü belirtmesi gerekir `Task(Of Integer)` .</span><span class="sxs-lookup"><span data-stu-id="df329-112">Therefore, the method declaration must specify a return type of `Task(Of Integer)`.</span></span>

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

<span data-ttu-id="df329-113">`TaskOfT_MethodAsync`Await ifadesi içinden çağrıldığında, await ifadesi `leisureHours` tarafından döndürülen görevde depolanan tamsayı değerini (değeri) alır `TaskOfT_MethodAsync` .</span><span class="sxs-lookup"><span data-stu-id="df329-113">When `TaskOfT_MethodAsync` is called from within an await expression, the await expression retrieves the integer value (the value of `leisureHours`) that's stored in the task that's returned by `TaskOfT_MethodAsync`.</span></span> <span data-ttu-id="df329-114">Await ifadeleri hakkında daha fazla bilgi için bkz. [Await işleci](../../../language-reference/operators/await-operator.md).</span><span class="sxs-lookup"><span data-stu-id="df329-114">For more information about await expressions, see [Await Operator](../../../language-reference/operators/await-operator.md).</span></span>

<span data-ttu-id="df329-115">Aşağıdaki kod çağrıları ve Await yöntemi `TaskOfT_MethodAsync` .</span><span class="sxs-lookup"><span data-stu-id="df329-115">The following code calls and awaits method `TaskOfT_MethodAsync`.</span></span> <span data-ttu-id="df329-116">Sonuç `result1` değişkenine atanır.</span><span class="sxs-lookup"><span data-stu-id="df329-116">The result is assigned to the `result1` variable.</span></span>

```vb
' Call and await the Task(Of T)-returning async method in the same statement.
Dim result1 As Integer = Await TaskOfT_MethodAsync()
```

<span data-ttu-id="df329-117">`TaskOfT_MethodAsync` `Await` Aşağıdaki kodda gösterildiği gibi, çağrısını uygulamasından ayırarak bunun nasıl gerçekleştiğini daha iyi anlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="df329-117">You can better understand how this happens by separating the call to `TaskOfT_MethodAsync` from the application of `Await`, as the following code shows.</span></span> <span data-ttu-id="df329-118">`TaskOfT_MethodAsync`Yönteminin bildiriminden bekleyebileceğiniz için hemen beklenen bir yönteme çağrı bir döndürür `Task(Of Integer)` .</span><span class="sxs-lookup"><span data-stu-id="df329-118">A call to method `TaskOfT_MethodAsync` that isn't immediately awaited returns a `Task(Of Integer)`, as you would expect from the declaration of the method.</span></span> <span data-ttu-id="df329-119">Görev `integerTask` örnekteki değişkenine atanır.</span><span class="sxs-lookup"><span data-stu-id="df329-119">The task is assigned to the `integerTask` variable in the example.</span></span> <span data-ttu-id="df329-120">`integerTask`Bir olduğundan <xref:System.Threading.Tasks.Task%601> , türünde bir özelliği içerir <xref:System.Threading.Tasks.Task%601.Result> `TResult` .</span><span class="sxs-lookup"><span data-stu-id="df329-120">Because `integerTask` is a <xref:System.Threading.Tasks.Task%601>, it contains a <xref:System.Threading.Tasks.Task%601.Result> property of type `TResult`.</span></span> <span data-ttu-id="df329-121">Bu durumda, TResult bir tamsayı türünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="df329-121">In this case, TResult represents an integer type.</span></span> <span data-ttu-id="df329-122">`Await`Öğesine uygulandığında `integerTask` , await ifadesi <xref:System.Threading.Tasks.Task%601.Result%2A> öğesinin özelliğinin içeriğini değerlendirir `integerTask` .</span><span class="sxs-lookup"><span data-stu-id="df329-122">When `Await` is applied to `integerTask`, the await expression evaluates to the contents of the <xref:System.Threading.Tasks.Task%601.Result%2A> property of `integerTask`.</span></span> <span data-ttu-id="df329-123">Değer `result2` değişkenine atanır.</span><span class="sxs-lookup"><span data-stu-id="df329-123">The value is assigned to the `result2` variable.</span></span>

> [!WARNING]
> <span data-ttu-id="df329-124"><xref:System.Threading.Tasks.Task%601.Result%2A>Özelliği engelleyici bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="df329-124">The <xref:System.Threading.Tasks.Task%601.Result%2A> property is a blocking property.</span></span> <span data-ttu-id="df329-125">Görevi tamamlanmadan önce ona erişmeye çalışırsanız, etkin olan iş parçacığı, görev tamamlanana ve değer kullanılabilir olana kadar engellenir.</span><span class="sxs-lookup"><span data-stu-id="df329-125">If you try to access it before its task is finished, the thread that's currently active is blocked until the task completes and the value is available.</span></span> <span data-ttu-id="df329-126">Çoğu durumda, `Await` özelliğine doğrudan erişmek yerine kullanarak değere erişmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="df329-126">In most cases, you should access the value by using `Await` instead of accessing the property directly.</span></span>

```vb
' Call and await in separate statements.
Dim integerTask As Task(Of Integer) = TaskOfT_MethodAsync()

' You can do other work that does not rely on resultTask before awaiting.
textBox1.Text &= "Application can continue working while the Task(Of T) runs. . . . " & vbCrLf

Dim result2 As Integer = Await integerTask
```

<span data-ttu-id="df329-127">Aşağıdaki koddaki Display deyimleri, `result1` değişkenin değerlerinin, `result2` değişkenin ve `Result` özelliğinin aynı olduğunu doğrular.</span><span class="sxs-lookup"><span data-stu-id="df329-127">The display statements in the following code verify that the values of the `result1` variable, the `result2` variable, and the `Result` property are the same.</span></span> <span data-ttu-id="df329-128">`Result`Özelliğin engelleme özelliği olduğunu ve görevi beklenmeden önce erişilmemesi gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="df329-128">Remember that the `Result` property is a blocking property and shouldn't be accessed before its task has been awaited.</span></span>

```vb
' Display the values of the result1 variable, the result2 variable, and
' the resultTask.Result property.
textBox1.Text &= vbCrLf & $"Value of result1 variable:   {result1}" & vbCrLf
textBox1.Text &= $"Value of result2 variable:   {result2}" & vbCrLf
textBox1.Text &= $"Value of resultTask.Result:  {integerTask.Result}" & vbCrLf
```

## <a name="task-return-type"></a><a name="BKMK_TaskReturnType"></a> <span data-ttu-id="df329-129">Görev dönüş türü</span><span class="sxs-lookup"><span data-stu-id="df329-129">Task Return Type</span></span>

<span data-ttu-id="df329-130">Dönüş açıklaması içermeyen veya bir işleneni döndürmeyen bir return ifadesini içeren zaman uyumsuz yöntemler genellikle dönüş türüne sahiptir <xref:System.Threading.Tasks.Task> .</span><span class="sxs-lookup"><span data-stu-id="df329-130">Async methods that don't contain a return statement or that contain a return statement that doesn't return an operand usually have a return type of <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="df329-131">Bu tür yöntemler, zaman uyumlu olarak çalışmak üzere yazılmışsa [alt](../../language-features/procedures/sub-procedures.md) yordamlar olur.</span><span class="sxs-lookup"><span data-stu-id="df329-131">Such methods would be [Sub](../../language-features/procedures/sub-procedures.md) procedures if they were written to run synchronously.</span></span> <span data-ttu-id="df329-132">`Task`Zaman uyumsuz bir yöntem için dönüş türü kullanırsanız, çağıran `Await` zaman uyumsuz yöntem bitene kadar çağıranın tamamlanmasını askıya almak için bir operatör kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="df329-132">If you use a `Task` return type for an async method, a calling method can use an `Await` operator to suspend the caller's completion until the called async method has finished.</span></span>

<span data-ttu-id="df329-133">Aşağıdaki örnekte, Async yöntemi `Task_MethodAsync` return ifadesini içermez.</span><span class="sxs-lookup"><span data-stu-id="df329-133">In the following example, async method `Task_MethodAsync` doesn't contain a return statement.</span></span> <span data-ttu-id="df329-134">Bu nedenle, `Task` beklenmeye olanak tanıyan yöntemi için dönüş türü belirtirsiniz `Task_MethodAsync` .</span><span class="sxs-lookup"><span data-stu-id="df329-134">Therefore, you specify a return type of `Task` for the method, which enables `Task_MethodAsync` to be awaited.</span></span> <span data-ttu-id="df329-135">`Task`Türün tanımı `Result` bir dönüş değeri depolamak için bir özellik içermez.</span><span class="sxs-lookup"><span data-stu-id="df329-135">The definition of the `Task` type doesn't include a `Result` property to store a return value.</span></span>

```vb
' TASK EXAMPLE
Async Function Task_MethodAsync() As Task

    ' The body of an async method is expected to contain an awaited
    ' asynchronous call.
    ' Task.Delay is a placeholder for actual work.
    Await Task.Delay(2000)
    textBox1.Text &= vbCrLf & "Sorry for the delay. . . ." & vbCrLf

    ' This method has no return statement, so its return type is Task.
End Function
```

<span data-ttu-id="df329-136">`Task_MethodAsync` , zaman uyumlu veya void döndüren bir yöntem için çağırma deyimine benzer bir await ifadesi yerine await deyimi kullanılarak çağrılır ve bekletildi `Sub` .</span><span class="sxs-lookup"><span data-stu-id="df329-136">`Task_MethodAsync` is called and awaited by using an await statement instead of an await expression, similar to the calling statement for a synchronous `Sub` or void-returning method.</span></span> <span data-ttu-id="df329-137">`Await`Bu durumda bir işlecin uygulaması bir değer üretmez.</span><span class="sxs-lookup"><span data-stu-id="df329-137">The application of an `Await` operator in this case doesn't produce a value.</span></span>

<span data-ttu-id="df329-138">Aşağıdaki kod çağrıları ve Await yöntemi `Task_MethodAsync` .</span><span class="sxs-lookup"><span data-stu-id="df329-138">The following code calls and awaits method `Task_MethodAsync`.</span></span>

```vb
' Call and await the Task-returning async method in the same statement.
Await Task_MethodAsync()
```

<span data-ttu-id="df329-139">Önceki örnekte olduğu gibi <xref:System.Threading.Tasks.Task%601> , `Task_MethodAsync` `Await` aşağıdaki kodda gösterildiği gibi, çağrısını bir işlecin uygulamasından ayırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="df329-139">As in the previous <xref:System.Threading.Tasks.Task%601> example, you can separate the call to `Task_MethodAsync` from the application of an `Await` operator, as the following code shows.</span></span> <span data-ttu-id="df329-140">Ancak, bir `Task` özelliğine sahip olmadığını `Result` ve bir Await işleci uygulandığında hiçbir değer üretilmediğini unutmayın `Task` .</span><span class="sxs-lookup"><span data-stu-id="df329-140">However, remember that a `Task` doesn't have a `Result` property, and that no value is produced when an await operator is applied to a `Task`.</span></span>

<span data-ttu-id="df329-141">Aşağıdaki kod, çağırma `Task_MethodAsync` görevinin döndürdüğü görevi bekleten ayırır `Task_MethodAsync` .</span><span class="sxs-lookup"><span data-stu-id="df329-141">The following code separates calling `Task_MethodAsync` from awaiting the task that `Task_MethodAsync` returns.</span></span>

```vb
' Call and await in separate statements.
Dim simpleTask As Task = Task_MethodAsync()

' You can do other work that does not rely on simpleTask before awaiting.
textBox1.Text &= vbCrLf & "Application can continue working while the Task runs. . . ." & vbCrLf

Await simpleTask
```

## <a name="void-return-type"></a><a name="BKMK_VoidReturnType"></a> <span data-ttu-id="df329-142">Void dönüş türü</span><span class="sxs-lookup"><span data-stu-id="df329-142">Void Return Type</span></span>

<span data-ttu-id="df329-143">Yordamların birincil kullanımı, `Sub` dönüş türü olmayan (diğer dillerde void dönüş türü olarak ifade edilen) olay işleyicileridir.</span><span class="sxs-lookup"><span data-stu-id="df329-143">The primary use of `Sub` procedures is in event handlers, where there is no return type (referred to as a void return type in other languages).</span></span> <span data-ttu-id="df329-144">Void Return Ayrıca, void döndüren yöntemleri geçersiz kılmak için veya "Fire ve unut" olarak kategorilere ayrılmamış etkinlikler gerçekleştiren yöntemler için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="df329-144">A void return also can be used to override void-returning methods or for methods that perform activities that can be categorized as "fire and forget."</span></span> <span data-ttu-id="df329-145">Ancak, `Task` void döndüren zaman uyumsuz bir yöntem beklenmediğinden, mümkün olan her yerde dönebilmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="df329-145">However, you should return a `Task` wherever possible, because a void-returning async method can't be awaited.</span></span> <span data-ttu-id="df329-146">Bu tür bir yöntemi çağıran, çağrılan zaman uyumsuz yöntemin tamamlanmasını beklemeden tamamlamaya devam edebilmelidir ve çağıranın, zaman uyumsuz yöntemin ürettiği herhangi bir değerden veya özel durumlardan bağımsız olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="df329-146">Any caller of such a method must be able to continue to completion without waiting for the called async method to finish, and the caller must be independent of any values or exceptions that the async method generates.</span></span>

<span data-ttu-id="df329-147">Void döndüren zaman uyumsuz bir yöntemi çağıran, yöntemden oluşturulan özel durumları yakalayabilir ve bu tür işlenmemiş özel durumlar uygulamanızın başarısız olmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="df329-147">The caller of a void-returning async method can't catch exceptions that are thrown from the method, and such unhandled exceptions are likely to cause your application to fail.</span></span> <span data-ttu-id="df329-148">Bir veya döndüren zaman uyumsuz bir yöntemde özel durum oluşursa <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601> , özel durum döndürülen görevde depolanır ve görev beklendiğinde yeniden oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="df329-148">If an exception occurs in an async method that returns a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>, the exception is stored in the returned task, and rethrown when the task is awaited.</span></span> <span data-ttu-id="df329-149">Bu nedenle, bir özel durum üretemeyen herhangi bir zaman uyumsuz metodun, veya dönüş türüne sahip olduğundan ve metoda yapılan çağrıların beklenmediğinden emin olun <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601> .</span><span class="sxs-lookup"><span data-stu-id="df329-149">Therefore, make sure that any async method that can produce an exception has a return type of <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> and that calls to the method are awaited.</span></span>

<span data-ttu-id="df329-150">Zaman uyumsuz yöntemlerde özel durumları yakalama hakkında daha fazla bilgi için bkz [. TRY... Yakala... Finally ekstresi](../../../language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="df329-150">For more information about how to catch exceptions in async methods, see [Try...Catch...Finally Statement](../../../language-reference/statements/try-catch-finally-statement.md).</span></span>

<span data-ttu-id="df329-151">Aşağıdaki kod zaman uyumsuz bir olay işleyicisini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="df329-151">The following code defines an async event handler.</span></span>

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

## <a name="complete-example"></a><a name="BKMK_Example"></a> <span data-ttu-id="df329-152">Örnek Tamam</span><span class="sxs-lookup"><span data-stu-id="df329-152">Complete Example</span></span>

<span data-ttu-id="df329-153">Aşağıdaki Windows Presentation Foundation (WPF) projesi bu konudan kod örneklerini içerir.</span><span class="sxs-lookup"><span data-stu-id="df329-153">The following Windows Presentation Foundation (WPF) project contains the code examples from this topic.</span></span>

 <span data-ttu-id="df329-154">Projeyi çalıştırmak için aşağıdaki adımları gerçekleştirin:</span><span class="sxs-lookup"><span data-stu-id="df329-154">To run the project, perform the following steps:</span></span>

1. <span data-ttu-id="df329-155">Visual Studio’yu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="df329-155">Start Visual Studio.</span></span>

2. <span data-ttu-id="df329-156">Menü çubuğunda **Dosya**, **Yeni**, **Proje**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="df329-156">On the menu bar, choose **File**, **New**, **Project**.</span></span>

     <span data-ttu-id="df329-157">**Yeni proje** iletişim kutusu açılır.</span><span class="sxs-lookup"><span data-stu-id="df329-157">The **New Project** dialog box opens.</span></span>

3. <span data-ttu-id="df329-158">**Yüklü**, **Şablonlar** kategorisinde **Visual Basic** ve ardından **Windows**' u seçin.</span><span class="sxs-lookup"><span data-stu-id="df329-158">In the **Installed**, **Templates** category, choose **Visual Basic**, and then choose **Windows**.</span></span> <span data-ttu-id="df329-159">Proje türleri listesinden **WPF uygulaması** ' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="df329-159">Choose **WPF Application** from the list of project types.</span></span>

4. <span data-ttu-id="df329-160">`AsyncReturnTypes`Projenin adı olarak girin ve **Tamam** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="df329-160">Enter `AsyncReturnTypes` as the name of the project, and then choose the **OK** button.</span></span>

     <span data-ttu-id="df329-161">Yeni proje **Çözüm Gezgini** görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="df329-161">The new project appears in **Solution Explorer**.</span></span>

5. <span data-ttu-id="df329-162">Visual Studio Code düzenleyicisinde **MainWindow. xaml** sekmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="df329-162">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>

     <span data-ttu-id="df329-163">Sekme görünür değilse, **Çözüm Gezgini**' de MainWindow. xaml için kısayol menüsünü açın ve **Aç**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="df329-163">If the tab is not visible, open the shortcut menu for MainWindow.xaml in **Solution Explorer**, and then choose **Open**.</span></span>

6. <span data-ttu-id="df329-164">MainWindow. xaml ' nin **xaml** penceresinde, kodu aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="df329-164">In the **XAML** window of MainWindow.xaml, replace the code with the following code.</span></span>

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

     <span data-ttu-id="df329-165">Bir metin kutusu ve bir düğme içeren basit bir pencere, MainWindow. xaml **Tasarım** penceresinde görünür.</span><span class="sxs-lookup"><span data-stu-id="df329-165">A simple window that contains a text box and a button appears in the **Design** window of MainWindow.xaml.</span></span>

7. <span data-ttu-id="df329-166">**Çözüm Gezgini**, MainWindow. xaml. vb için kısayol menüsünü açın ve **kodu görüntüle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="df329-166">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.vb, and then choose **View Code**.</span></span>

8. <span data-ttu-id="df329-167">MainWindow. xaml. vb içindeki kodu aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="df329-167">Replace the code in MainWindow.xaml.vb with the following code.</span></span>

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
            textBox1.Text &= "Application can continue working while the Task(Of T) runs. . . . " & vbCrLf

            Dim result2 As Integer = Await integerTask

            ' Display the values of the result1 variable, the result2 variable, and
            ' the resultTask.Result property.
            textBox1.Text &= vbCrLf & $"Value of result1 variable:   {result1}" & vbCrLf
            textBox1.Text &= $"Value of result2 variable:   {result2}" & vbCrLf
            textBox1.Text &= $"Value of resultTask.Result:  {integerTask.Result}" & vbCrLf

            ' Task
            ' Call and await the Task-returning async method in the same statement.
            Await Task_MethodAsync()

            ' Call and await in separate statements.
            Dim simpleTask As Task = Task_MethodAsync()

            ' You can do other work that does not rely on simpleTask before awaiting.
            textBox1.Text &= vbCrLf & "Application can continue working while the Task runs. . . ." & vbCrLf

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
            textBox1.Text &= vbCrLf & "Sorry for the delay. . . ." & vbCrLf

            ' This method has no return statement, so its return type is Task.
        End Function

    End Class
    ```

9. <span data-ttu-id="df329-168">Programı çalıştırmak için F5 tuşunu seçin ve sonra **Başlat** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="df329-168">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>

     <span data-ttu-id="df329-169">Aşağıdaki çıkışın görünmesi gerekir:</span><span class="sxs-lookup"><span data-stu-id="df329-169">The following output should appear:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="df329-170">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="df329-170">See also</span></span>

- <xref:System.Threading.Tasks.Task.FromResult%2A>
- [<span data-ttu-id="df329-171">İzlenecek yol: Async ve await kullanarak Web 'e erişme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="df329-171">Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)</span></span>](walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="df329-172">Zaman uyumsuz programlarda denetim akışı (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="df329-172">Control Flow in Async Programs (Visual Basic)</span></span>](control-flow-in-async-programs.md)
- [<span data-ttu-id="df329-173">Eş</span><span class="sxs-lookup"><span data-stu-id="df329-173">Async</span></span>](../../../language-reference/modifiers/async.md)
- [<span data-ttu-id="df329-174">Await Işleci</span><span class="sxs-lookup"><span data-stu-id="df329-174">Await Operator</span></span>](../../../language-reference/operators/await-operator.md)
