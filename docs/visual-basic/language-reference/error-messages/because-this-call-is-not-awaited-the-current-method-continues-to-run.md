---
title: Bu çağrı beklenmediğinden, çağrı tamamlanmadan geçerli yöntemin çalıştırılması devam eder
ms.date: 07/20/2015
f1_keywords:
- bc42358
- vbc42358
helpviewer_keywords:
- BC42358
ms.assetid: 43342515-c3c8-4155-9263-c302afabcbc2
ms.openlocfilehash: 5870a9a3a598c67badc9868af1486b52c76a9906
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72523917"
---
# <a name="because-this-call-is-not-awaited-the-current-method-continues-to-run-before-the-call-is-completed"></a><span data-ttu-id="f31c3-102">Bu çağrı beklenmediğinden, çağrı tamamlanmadan geçerli yöntemin çalıştırılması devam eder</span><span class="sxs-lookup"><span data-stu-id="f31c3-102">Because this call is not awaited, the current method continues to run before the call is completed</span></span>

<span data-ttu-id="f31c3-103">Bu çağrı beklenmediğinden, çağrı tamamlanmadan önce geçerli yöntemin yürütülmesi devam eder.</span><span class="sxs-lookup"><span data-stu-id="f31c3-103">Because this call is not awaited, execution of the current method continues before the call is completed.</span></span> <span data-ttu-id="f31c3-104">Çağrının sonucuna ' await ' işlecini uygulamayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="f31c3-104">Consider applying the 'Await' operator to the result of the call.</span></span>

<span data-ttu-id="f31c3-105">Geçerli yöntem bir <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601> döndüren zaman uyumsuz bir yöntemi çağırır ve sonuca [await](../../../visual-basic/language-reference/operators/await-operator.md) işlecini uygulamaz.</span><span class="sxs-lookup"><span data-stu-id="f31c3-105">The current method calls an async method that returns a <xref:System.Threading.Tasks.Task> or a <xref:System.Threading.Tasks.Task%601> and doesn’t apply the [Await](../../../visual-basic/language-reference/operators/await-operator.md) operator to the result.</span></span> <span data-ttu-id="f31c3-106">Zaman uyumsuz metoda yapılan çağrı zaman uyumsuz bir görev başlatır.</span><span class="sxs-lookup"><span data-stu-id="f31c3-106">The call to the async method starts an asynchronous task.</span></span> <span data-ttu-id="f31c3-107">Ancak, `Await` işleci uygulanmadığından, program görevin tamamlanmasını beklemeden devam eder.</span><span class="sxs-lookup"><span data-stu-id="f31c3-107">However, because no `Await` operator is applied, the program continues without waiting for the task to complete.</span></span> <span data-ttu-id="f31c3-108">Çoğu durumda, bu davranış beklenmez.</span><span class="sxs-lookup"><span data-stu-id="f31c3-108">In most cases, that behavior isn't expected.</span></span> <span data-ttu-id="f31c3-109">Genellikle çağıran yöntemin diğer yönleri çağrının sonuçlarına bağlıdır veya, çağrıyı içeren yöntemden döndürmeden önce çağrılan yöntemin tamamlanmasının beklenmez.</span><span class="sxs-lookup"><span data-stu-id="f31c3-109">Usually other aspects of the calling method depend on the results of the call or, minimally, the called method is expected to complete before you return from the method that contains the call.</span></span>

<span data-ttu-id="f31c3-110">Eşit ölçüde önemli bir sorun, çağrılan zaman uyumsuz yöntemde oluşturulan özel durumlarla gerçekleşen şeydir.</span><span class="sxs-lookup"><span data-stu-id="f31c3-110">An equally important issue is what happens with exceptions that are raised in the called async method.</span></span> <span data-ttu-id="f31c3-111">Döndürülen görevde bir <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601> döndüren bir yöntemde oluşturulan bir özel durum.</span><span class="sxs-lookup"><span data-stu-id="f31c3-111">An exception that’s raised in a method that returns a <xref:System.Threading.Tasks.Task> or  <xref:System.Threading.Tasks.Task%601> is stored in the returned task.</span></span> <span data-ttu-id="f31c3-112">Görevi beklemezseniz veya özel durumları açıkça denetmezseniz, özel durum kaybolur.</span><span class="sxs-lookup"><span data-stu-id="f31c3-112">If you don't await the task or explicitly check for exceptions, the exception is lost.</span></span> <span data-ttu-id="f31c3-113">Görevi beklekullanacaksanız, özel durumu yeniden oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="f31c3-113">If you await the task, its exception is rethrown.</span></span>

<span data-ttu-id="f31c3-114">En iyi uygulama olarak, her zaman çağrıyı beklemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="f31c3-114">As a best practice, you should always await the call.</span></span>

<span data-ttu-id="f31c3-115">Bu ileti, varsayılan olarak bir uyarıdır.</span><span class="sxs-lookup"><span data-stu-id="f31c3-115">By default, this message is a warning.</span></span> <span data-ttu-id="f31c3-116">Uyarıları gizleme veya uyarıları hata olarak değerlendirme hakkında daha fazla bilgi için bkz. [Visual Basic uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="f31c3-116">For more information about hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>

<span data-ttu-id="f31c3-117">**Hata kimliği:** BC42358</span><span class="sxs-lookup"><span data-stu-id="f31c3-117">**Error ID:** BC42358</span></span>

### <a name="to-address-this-warning"></a><span data-ttu-id="f31c3-118">Bu uyarıyı çözmek için</span><span class="sxs-lookup"><span data-stu-id="f31c3-118">To address this warning</span></span>

- <span data-ttu-id="f31c3-119">Yalnızca zaman uyumsuz çağrının tamamlanmasını beklemek istemediğiniz ve çağrılan yöntemin herhangi bir özel durum tetiklemediğinizden emin değilseniz, uyarının görüntülenmesini düşünmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="f31c3-119">You should consider suppressing the warning only if you're sure that you don't want to wait for the asynchronous call to complete and that the called method won't raise any exceptions.</span></span> <span data-ttu-id="f31c3-120">Bu durumda, çağrının görev sonucunu bir değişkene atayarak uyarıyı bastırın.</span><span class="sxs-lookup"><span data-stu-id="f31c3-120">In that case, you can suppress the warning by assigning the task result of the call to a variable.</span></span>

     <span data-ttu-id="f31c3-121">Aşağıdaki örnek, uyarıya nasıl neden olduğunu, nasıl bastırılacağını ve çağrının nasıl bekleleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="f31c3-121">The following example shows how to cause the warning, how to suppress it, and how to await the call.</span></span>

    ```vb
    Async Function CallingMethodAsync() As Task

        ResultsTextBox.Text &= vbCrLf & "  Entering calling method."

        ' Variable delay is used to slow down the called method so that you
        ' can distinguish between awaiting and not awaiting in the program's output.
        ' You can adjust the value to produce the output that this topic shows
        ' after the code.
        Dim delay = 5000

        ' Call #1.
        ' Call an async method. Because you don't await it, its completion isn't
        ' coordinated with the current method, CallingMethodAsync.
        ' The following line causes the warning.
        CalledMethodAsync(delay)

        ' Call #2.
        ' To suppress the warning without awaiting, you can assign the
        ' returned task to a variable. The assignment doesn't change how
        ' the program runs. However, the recommended practice is always to
        ' await a call to an async method.
        ' Replace Call #1 with the following line.
        'Task delayTask = CalledMethodAsync(delay)

        ' Call #3
        ' To contrast with an awaited call, replace the unawaited call
        ' (Call #1 or Call #2) with the following awaited call. The best
        ' practice is to await the call.

        'Await CalledMethodAsync(delay)

        ' If the call to CalledMethodAsync isn't awaited, CallingMethodAsync
        ' continues to run and, in this example, finishes its work and returns
        ' to its caller.
        ResultsTextBox.Text &= vbCrLf & "  Returning from calling method."
    End Function

    Async Function CalledMethodAsync(howLong As Integer) As Task

        ResultsTextBox.Text &= vbCrLf & "    Entering called method, starting and awaiting Task.Delay."
        ' Slow the process down a little so you can distinguish between awaiting
        ' and not awaiting. Adjust the value for howLong if necessary.
        Await Task.Delay(howLong)
        ResultsTextBox.Text &= vbCrLf & "    Task.Delay is finished--returning from called method."
    End Function
    ```

     <span data-ttu-id="f31c3-122">Örnekte, çağır #1 veya #2 çağır ' ı seçerseniz, geri beklemiş zaman uyumsuz Yöntem (`CalledMethodAsync`) hem çağıranı (`CallingMethodAsync`) hem de arayanın çağıranı (`StartButton_Click`) tamamlandıktan sonra biter.</span><span class="sxs-lookup"><span data-stu-id="f31c3-122">In the example, if you choose Call #1 or Call #2, the unawaited async method (`CalledMethodAsync`) finishes after both its caller (`CallingMethodAsync`) and the caller's caller (`StartButton_Click`) are complete.</span></span> <span data-ttu-id="f31c3-123">Aşağıdaki çıktıda yer aldığı son satırda, çağrılan yöntemin ne zaman bittiği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f31c3-123">The last line in the following output shows you when the called method finishes.</span></span> <span data-ttu-id="f31c3-124">Tam örnekte `CallingMethodAsync` çağıran olay işleyicisinden giriş ve çıkış çıkış, çıkışta işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f31c3-124">Entry to and exit from the event handler that calls `CallingMethodAsync` in the full example are marked in the output.</span></span>

    ```console
    Entering the Click event handler.
      Entering calling method.
        Entering called method, starting and awaiting Task.Delay.
      Returning from calling method.
    Exiting the Click event handler.
        Task.Delay is finished--returning from called method.
    ```

## <a name="example"></a><span data-ttu-id="f31c3-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="f31c3-125">Example</span></span>

<span data-ttu-id="f31c3-126">Aşağıdaki Windows Presentation Foundation (WPF) uygulaması, önceki örnekteki yöntemleri içerir.</span><span class="sxs-lookup"><span data-stu-id="f31c3-126">The following Windows Presentation Foundation (WPF) application contains the methods from the previous example.</span></span> <span data-ttu-id="f31c3-127">Aşağıdaki adımlar uygulamayı ayarlar.</span><span class="sxs-lookup"><span data-stu-id="f31c3-127">The following steps set up the application.</span></span>

1. <span data-ttu-id="f31c3-128">Bir WPF uygulaması oluşturun ve `AsyncWarning` adlandırın.</span><span class="sxs-lookup"><span data-stu-id="f31c3-128">Create a WPF application, and name it `AsyncWarning`.</span></span>

2. <span data-ttu-id="f31c3-129">Visual Studio Code düzenleyicisinde **MainWindow. xaml** sekmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="f31c3-129">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>

     <span data-ttu-id="f31c3-130">Sekme görünür değilse, **Çözüm Gezgini**' de MainWindow. xaml için kısayol menüsünü açın ve **kodu görüntüle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="f31c3-130">If the tab isn't visible, open the shortcut menu for MainWindow.xaml in **Solution Explorer**, and then choose **View Code**.</span></span>

3. <span data-ttu-id="f31c3-131">MainWindow. xaml **xaml** görünümündeki kodu aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="f31c3-131">Replace the code in the **XAML** view of MainWindow.xaml with the following code.</span></span>

    ```vb
    <Window x:Class="MainWindow"
            xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
            xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
            Title="MainWindow" Height="350" Width="525">
        <Grid>
            <Button x:Name="StartButton" Content="Start" HorizontalAlignment="Left" Margin="214,28,0,0" VerticalAlignment="Top" Width="75" HorizontalContentAlignment="Center" FontWeight="Bold" FontFamily="Aharoni" Click="StartButton_Click" />
            <TextBox x:Name="ResultsTextBox" Margin="0,80,0,0" TextWrapping="Wrap" FontFamily="Lucida Console"/>
        </Grid>
    </Window>
    ```

     <span data-ttu-id="f31c3-132">Bir düğme içeren basit bir pencere ve MainWindow. xaml **Tasarım** görünümünde bir metin kutusu görünür.</span><span class="sxs-lookup"><span data-stu-id="f31c3-132">A simple window that contains a button and a text box appears in the **Design** view of MainWindow.xaml.</span></span>

     <span data-ttu-id="f31c3-133">XAML Tasarımcısı hakkında daha fazla bilgi için, bkz. [XAML Tasarımcısı kullanarak Kullanıcı arabirimi oluşturma](/visualstudio/designers/creating-a-ui-by-using-xaml-designer-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="f31c3-133">For more information about the XAML Designer, see [Creating a UI by using XAML Designer](/visualstudio/designers/creating-a-ui-by-using-xaml-designer-in-visual-studio).</span></span> <span data-ttu-id="f31c3-134">Kendi basit kullanıcı arabiriminizi derleme hakkında daha fazla bilgi için, bkz. "WPF uygulaması oluşturmak Için" ve [Izlenecek yol: Async ve await kullanarak Web 'e erişme](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="f31c3-134">For information about how to build your own simple UI, see the "To create a WPF application" and "To design a simple WPF MainWindow" sections of [Walkthrough: Accessing the Web by Using Async and Await](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span>

4. <span data-ttu-id="f31c3-135">MainWindow. xaml. vb içindeki kodu aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="f31c3-135">Replace the code in MainWindow.xaml.vb with the following code.</span></span>

    ```vb
    Class MainWindow

        Private Async Sub StartButton_Click(sender As Object, e As RoutedEventArgs)

            ResultsTextBox.Text &= vbCrLf & "Entering the Click event handler."
            Await CallingMethodAsync()
            ResultsTextBox.Text &= vbCrLf & "Exiting the Click event handler."
        End Sub

        Async Function CallingMethodAsync() As Task

            ResultsTextBox.Text &= vbCrLf & "  Entering calling method."

            ' Variable delay is used to slow down the called method so that you
            ' can distinguish between awaiting and not awaiting in the program's output.
            ' You can adjust the value to produce the output that this topic shows
            ' after the code.
            Dim delay = 5000

            ' Call #1.
            ' Call an async method. Because you don't await it, its completion isn't
            ' coordinated with the current method, CallingMethodAsync.
            ' The following line causes the warning.
            CalledMethodAsync(delay)

            ' Call #2.
            ' To suppress the warning without awaiting, you can assign the
            ' returned task to a variable. The assignment doesn't change how
            ' the program runs. However, the recommended practice is always to
            ' await a call to an async method.

            ' Replace Call #1 with the following line.
            'Task delayTask = CalledMethodAsync(delay)

            ' Call #3
            ' To contrast with an awaited call, replace the unawaited call
            ' (Call #1 or Call #2) with the following awaited call. The best
            ' practice is to await the call.

            'Await CalledMethodAsync(delay)

            ' If the call to CalledMethodAsync isn't awaited, CallingMethodAsync
            ' continues to run and, in this example, finishes its work and returns
            ' to its caller.
            ResultsTextBox.Text &= vbCrLf & "  Returning from calling method."
        End Function

        Async Function CalledMethodAsync(howLong As Integer) As Task

            ResultsTextBox.Text &= vbCrLf & "    Entering called method, starting and awaiting Task.Delay."
            ' Slow the process down a little so you can distinguish between awaiting
            ' and not awaiting. Adjust the value for howLong if necessary.
            Await Task.Delay(howLong)
            ResultsTextBox.Text &= vbCrLf & "    Task.Delay is finished--returning from called method."
        End Function

    End Class

    ' Output

    ' Entering the Click event handler.
    '   Entering calling method.
    '     Entering called method, starting and awaiting Task.Delay.
    '   Returning from calling method.
    ' Exiting the Click event handler.
    '     Task.Delay is finished--returning from called method.

    ' Output

    ' Entering the Click event handler.
    '   Entering calling method.
    '     Entering called method, starting and awaiting Task.Delay.
    '     Task.Delay is finished--returning from called method.
    '   Returning from calling method.
    ' Exiting the Click event handler.
    ```

5. <span data-ttu-id="f31c3-136">Programı çalıştırmak için F5 tuşunu seçin ve sonra **Başlat** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="f31c3-136">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>

     <span data-ttu-id="f31c3-137">Beklenen çıkış kodun sonunda görünür.</span><span class="sxs-lookup"><span data-stu-id="f31c3-137">The expected output appears at the end of the code.</span></span>

## <a name="see-also"></a><span data-ttu-id="f31c3-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f31c3-138">See also</span></span>

- [<span data-ttu-id="f31c3-139">Await İşleci</span><span class="sxs-lookup"><span data-stu-id="f31c3-139">Await Operator</span></span>](../../../visual-basic/language-reference/operators/await-operator.md)
- [<span data-ttu-id="f31c3-140">Async ve Await ile Zaman Uyumsuz Programlama</span><span class="sxs-lookup"><span data-stu-id="f31c3-140">Asynchronous Programming with Async and Await</span></span>](../../../visual-basic/programming-guide/concepts/async/index.md)
