---
title: Bu çağrı beklenmediğinden, çağrı tamamlanmadan geçerli yöntemin çalıştırılması devam eder
ms.date: 07/20/2015
f1_keywords:
- bc42358
- vbc42358
helpviewer_keywords:
- BC42358
ms.assetid: 43342515-c3c8-4155-9263-c302afabcbc2
ms.openlocfilehash: 754fc6750e63f6d9f39da94041fc452829bca46d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33591440"
---
# <a name="because-this-call-is-not-awaited-the-current-method-continues-to-run-before-the-call-is-completed"></a><span data-ttu-id="86f4d-102">Bu çağrı beklenmediğinden, çağrı tamamlanmadan geçerli yöntemin çalıştırılması devam eder</span><span class="sxs-lookup"><span data-stu-id="86f4d-102">Because this call is not awaited, the current method continues to run before the call is completed</span></span>
<span data-ttu-id="86f4d-103">Bu çağrı beklenmediğinden, çağrı tamamlanmadan geçerli yöntemin çalıştırılması devam eder.</span><span class="sxs-lookup"><span data-stu-id="86f4d-103">Because this call is not awaited, execution of the current method continues before the call is completed.</span></span> <span data-ttu-id="86f4d-104">'Bekleme' işleci çağrı sonucunu uygulamayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="86f4d-104">Consider applying the 'Await' operator to the result of the call.</span></span>  
  
 <span data-ttu-id="86f4d-105">Geçerli yöntemi döndüren bir zaman uyumsuz yöntem çağırır bir <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601> ve uygulanmaz [bekleme](../../../visual-basic/language-reference/operators/await-operator.md) sonucu işleci.</span><span class="sxs-lookup"><span data-stu-id="86f4d-105">The current method calls an async method that returns a <xref:System.Threading.Tasks.Task> or a <xref:System.Threading.Tasks.Task%601> and doesn’t apply the [Await](../../../visual-basic/language-reference/operators/await-operator.md) operator to the result.</span></span> <span data-ttu-id="86f4d-106">Zaman uyumsuz yöntem çağrısı zaman uyumsuz bir görev başlatır.</span><span class="sxs-lookup"><span data-stu-id="86f4d-106">The call to the async method starts an asynchronous task.</span></span> <span data-ttu-id="86f4d-107">Ancak, çünkü hiçbir `Await` program görevinin tamamlanmasını beklemeden devam işleci uygulanır.</span><span class="sxs-lookup"><span data-stu-id="86f4d-107">However, because no `Await` operator is applied, the program continues without waiting for the task to complete.</span></span> <span data-ttu-id="86f4d-108">Çoğu durumda, bu davranışı beklenen değil.</span><span class="sxs-lookup"><span data-stu-id="86f4d-108">In most cases, that behavior isn't expected.</span></span> <span data-ttu-id="86f4d-109">Genellikle diğer yönlerini arama yöntemi arama sonuçlarına bağlı veya, çağrılan yöntemin çağrı içerir yönteminden döndürmeden önce tamamlamak için en azından beklenir.</span><span class="sxs-lookup"><span data-stu-id="86f4d-109">Usually other aspects of the calling method depend on the results of the call or, minimally, the called method is expected to complete before you return from the method that contains the call.</span></span>  
  
 <span data-ttu-id="86f4d-110">Eşit oranda önemli bir sorun çağrılan zaman uyumsuz yöntemde oluşan özel durumlara sahip olur.</span><span class="sxs-lookup"><span data-stu-id="86f4d-110">An equally important issue is what happens with exceptions that are raised in the called async method.</span></span> <span data-ttu-id="86f4d-111">Döndüren bir yöntemde oluşan bir özel durum bir <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601> döndürülen görevde depolanır.</span><span class="sxs-lookup"><span data-stu-id="86f4d-111">An exception that’s raised in a method that returns a <xref:System.Threading.Tasks.Task> or  <xref:System.Threading.Tasks.Task%601> is stored in the returned task.</span></span> <span data-ttu-id="86f4d-112">Görev await yok veya açıkça özel durumlar için denetleyin, özel durum kaybolur.</span><span class="sxs-lookup"><span data-stu-id="86f4d-112">If you don't await the task or explicitly check for exceptions, the exception is lost.</span></span> <span data-ttu-id="86f4d-113">Görev await, kendi özel durum işlenemezse.</span><span class="sxs-lookup"><span data-stu-id="86f4d-113">If you await the task, its exception is rethrown.</span></span>  
  
 <span data-ttu-id="86f4d-114">En iyi uygulama, her zaman çağrıyı beklemek.</span><span class="sxs-lookup"><span data-stu-id="86f4d-114">As a best practice, you should always await the call.</span></span>  
  
 <span data-ttu-id="86f4d-115">Varsayılan olarak, bu iletiyi bir uyarıdır.</span><span class="sxs-lookup"><span data-stu-id="86f4d-115">By default, this message is a warning.</span></span> <span data-ttu-id="86f4d-116">Uyarıları gizleme veya uyarıları hata olarak davranma hakkında daha fazla bilgi için bkz: [yapılandırma uyarılarını Visual Basic'te](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="86f4d-116">For more information about hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="86f4d-117">**Hata Kimliği:** BC42358</span><span class="sxs-lookup"><span data-stu-id="86f4d-117">**Error ID:** BC42358</span></span>  
  
### <a name="to-address-this-warning"></a><span data-ttu-id="86f4d-118">Bu uyarıyı gidermek için</span><span class="sxs-lookup"><span data-stu-id="86f4d-118">To address this warning</span></span>  
  
-   <span data-ttu-id="86f4d-119">Yalnızca zaman uyumsuz çağrının tamamlanmasını beklemek istemiyorsanız ve çağrılan yöntemin özel durumlar Yükselt olmaz eminseniz, uyarı gizleme göz önünde bulundurmalısınız.</span><span class="sxs-lookup"><span data-stu-id="86f4d-119">You should consider suppressing the warning only if you're sure that you don't want to wait for the asynchronous call to complete and that the called method won't raise any exceptions.</span></span> <span data-ttu-id="86f4d-120">Bu durumda, bir değişken çağrısı görev sonucu atayarak uyarı gizleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="86f4d-120">In that case, you can suppress the warning by assigning the task result of the call to a variable.</span></span>  
  
     <span data-ttu-id="86f4d-121">Aşağıdaki örnekte nasıl uyarı neden, onu gizlemek nasıl ve çağrı beklemek nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="86f4d-121">The following example shows how to cause the warning, how to suppress it, and how to await the call.</span></span>  
  
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
  
     <span data-ttu-id="86f4d-122">Örnekte çağrı #1 veya çağrı #2 unawaited async yöntemi seçerseniz, (`CalledMethodAsync`) tamamlandıktan sonra her iki arayan (`CallingMethodAsync`) ve arayanın arayan (`StartButton_Click`) tamamlandığından.</span><span class="sxs-lookup"><span data-stu-id="86f4d-122">In the example, if you choose Call #1 or Call #2, the unawaited async method (`CalledMethodAsync`) finishes after both its caller (`CallingMethodAsync`) and the caller's caller (`StartButton_Click`) are complete.</span></span> <span data-ttu-id="86f4d-123">Aşağıdaki çıkış son satırında çağrılan Yöntem sonlandığında gösterir.</span><span class="sxs-lookup"><span data-stu-id="86f4d-123">The last line in the following output shows you when the called method finishes.</span></span> <span data-ttu-id="86f4d-124">İçin giriş ve çıkış çağırır olay işleyicisinden `CallingMethodAsync` tam örnek çıktıda işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="86f4d-124">Entry to and exit from the event handler that calls `CallingMethodAsync` in the full example are marked in the output.</span></span>  
  
    ```  
    Entering the Click event handler.  
      Entering calling method.  
        Entering called method, starting and awaiting Task.Delay.  
      Returning from calling method.  
    Exiting the Click event handler.  
        Task.Delay is finished--returning from called method.  
    ```  
  
## <a name="example"></a><span data-ttu-id="86f4d-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="86f4d-125">Example</span></span>  
 <span data-ttu-id="86f4d-126">Aşağıdaki Windows Presentation Foundation (WPF) uygulama önceki örnekten yöntemler içerir.</span><span class="sxs-lookup"><span data-stu-id="86f4d-126">The following Windows Presentation Foundation (WPF) application contains the methods from the previous example.</span></span> <span data-ttu-id="86f4d-127">Aşağıdaki adımları uygulama ayarlama.</span><span class="sxs-lookup"><span data-stu-id="86f4d-127">The following steps set up the application.</span></span>  
  
1.  <span data-ttu-id="86f4d-128">WPF uygulaması oluşturun ve adlandırın `AsyncWarning`.</span><span class="sxs-lookup"><span data-stu-id="86f4d-128">Create a WPF application, and name it `AsyncWarning`.</span></span>  
  
2.  <span data-ttu-id="86f4d-129">Visual Studio Kod Düzenleyicisi'nde seçin **MainWindow.xaml** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="86f4d-129">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>  
  
     <span data-ttu-id="86f4d-130">Sekme görünür değilse, kısayol menüsünde MainWindow.xaml içinde açık **Çözüm Gezgini**ve ardından **görünümü kodu**.</span><span class="sxs-lookup"><span data-stu-id="86f4d-130">If the tab isn't visible, open the shortcut menu for MainWindow.xaml in **Solution Explorer**, and then choose **View Code**.</span></span>  
  
3.  <span data-ttu-id="86f4d-131">Kodla **XAML** MainWindow.xaml görünümünü aşağıdaki kod ile.</span><span class="sxs-lookup"><span data-stu-id="86f4d-131">Replace the code in the **XAML** view of MainWindow.xaml with the following code.</span></span>  
  
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
  
     <span data-ttu-id="86f4d-132">Bir düğme ve bir metin kutusu içeren basit bir pencere görünür **tasarım** MainWindow.xaml görünümü.</span><span class="sxs-lookup"><span data-stu-id="86f4d-132">A simple window that contains a button and a text box appears in the **Design** view of MainWindow.xaml.</span></span>  
  
     <span data-ttu-id="86f4d-133">XAML Tasarımcısı hakkında daha fazla bilgi için bkz: [XAML Tasarımcısını kullanarak bir kullanıcı Arabirimi oluşturma](/visualstudio/designers/creating-a-ui-by-using-xaml-designer-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="86f4d-133">For more information about the XAML Designer, see [Creating a UI by using XAML Designer](/visualstudio/designers/creating-a-ui-by-using-xaml-designer-in-visual-studio).</span></span> <span data-ttu-id="86f4d-134">Basit kendi kullanıcı Arabirimi oluşturma hakkında daha fazla bilgi için bkz: "WPF uygulaması oluşturmak için" ve "Basit bir WPF MainWindow tasarlamak için" bölümlerini [izlenecek yol: Web kullanarak zaman uyumsuz ve bekleme tarafından erişme](http://msdn.microsoft.com/library/25879a6d-fdee-4a38-bc98-bb8c24d16042).</span><span class="sxs-lookup"><span data-stu-id="86f4d-134">For information about how to build your own simple UI, see the "To create a WPF application" and "To design a simple WPF MainWindow" sections of [Walkthrough: Accessing the Web by Using Async and Await](http://msdn.microsoft.com/library/25879a6d-fdee-4a38-bc98-bb8c24d16042).</span></span>  
  
4.  <span data-ttu-id="86f4d-135">MainWindow.xaml.vb kodu aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="86f4d-135">Replace the code in MainWindow.xaml.vb with the following code.</span></span>  
  
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
  
5.  <span data-ttu-id="86f4d-136">Programını çalıştırın ve ardından için F5 tuşuna seçin **Başlat** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="86f4d-136">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
     <span data-ttu-id="86f4d-137">Beklenen çıkış kodu sonunda görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="86f4d-137">The expected output appears at the end of the code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86f4d-138">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="86f4d-138">See Also</span></span>  
 [<span data-ttu-id="86f4d-139">Await İşleci</span><span class="sxs-lookup"><span data-stu-id="86f4d-139">Await Operator</span></span>](../../../visual-basic/language-reference/operators/await-operator.md)  
 [<span data-ttu-id="86f4d-140">Async ve Await ile Zaman Uyumsuz Programlama</span><span class="sxs-lookup"><span data-stu-id="86f4d-140">Asynchronous Programming with Async and Await</span></span>](../../../visual-basic/programming-guide/concepts/async/index.md)
