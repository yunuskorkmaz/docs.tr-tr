---
title: Zaman uyumsuz programlarda denetim akışı (Visual Basic)
ms.date: 07/20/2015
ms.assetid: b0443af7-c586-4cb0-b476-742ae4098a96
ms.openlocfilehash: 265efde93cec87594a0407309b58b6bdf11817af
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630600"
---
# <a name="control-flow-in-async-programs-visual-basic"></a><span data-ttu-id="e1051-102">Zaman uyumsuz programlarda denetim akışı (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e1051-102">Control Flow in Async Programs (Visual Basic)</span></span>

<span data-ttu-id="e1051-103">`Async` Ve`Await` anahtar sözcüklerini kullanarak zaman uyumsuz programları daha kolay bir şekilde yazabilir ve koruyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e1051-103">You can write and maintain asynchronous programs more easily by using the `Async` and `Await` keywords.</span></span> <span data-ttu-id="e1051-104">Ancak, programınızın nasıl çalıştığını anlamıyorsanız sonuçlar sizi şaşırtabilir.</span><span class="sxs-lookup"><span data-stu-id="e1051-104">However, the results might surprise you if you don't understand how your program operates.</span></span> <span data-ttu-id="e1051-105">Bu konu, denetim bir yöntemden diğerine ne zaman taşındığını ve her seferinde hangi bilgilerin aktarılacağını göstermek için basit bir zaman uyumsuz program aracılığıyla denetim akışını izler.</span><span class="sxs-lookup"><span data-stu-id="e1051-105">This topic traces the flow of control through a simple async program to show you when control moves from one method to another and what information is transferred each time.</span></span>

> [!NOTE]
> <span data-ttu-id="e1051-106">`Async` Ve`Await` anahtar sözcükleri Visual Studio 2012 ' de tanıtılmıştı.</span><span class="sxs-lookup"><span data-stu-id="e1051-106">The `Async` and `Await` keywords were introduced in Visual Studio 2012.</span></span>

<span data-ttu-id="e1051-107">Genel olarak, zaman [uyumsuz değiştirici içeren](../../../../visual-basic/language-reference/modifiers/async.md) zaman uyumsuz kod içeren yöntemleri işaretlersiniz.</span><span class="sxs-lookup"><span data-stu-id="e1051-107">In general, you mark methods that contain asynchronous code with the [Async](../../../../visual-basic/language-reference/modifiers/async.md) modifier.</span></span> <span data-ttu-id="e1051-108">Zaman uyumsuz değiştirici ile işaretlenmiş bir yöntemde, yöntemin, çağrılan zaman uyumsuz işlemin tamamlanmasını beklemek için bekleyeceği yeri belirtmek için [await (Visual Basic)](../../../../visual-basic/language-reference/operators/await-operator.md) işlecini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e1051-108">In a method that's marked with an async modifier, you can use an [Await (Visual Basic)](../../../../visual-basic/language-reference/operators/await-operator.md) operator to specify where the method pauses to wait for a called asynchronous process to complete.</span></span> <span data-ttu-id="e1051-109">Daha fazla bilgi için bkz. zaman uyumsuz [programlama, Async ve await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="e1051-109">For more information, see [Asynchronous Programming with Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md).</span></span>

<span data-ttu-id="e1051-110">Aşağıdaki örnek, belirtilen bir Web sitesinin içeriğini bir dize olarak indirmek ve dizenin uzunluğunu göstermek için zaman uyumsuz yöntemler kullanır.</span><span class="sxs-lookup"><span data-stu-id="e1051-110">The following example uses async methods to download the contents of a specified website as a string and to display the length of the string.</span></span> <span data-ttu-id="e1051-111">Örnek aşağıdaki iki yöntemi içerir.</span><span class="sxs-lookup"><span data-stu-id="e1051-111">The example contains the following two methods.</span></span>

- <span data-ttu-id="e1051-112">`startButton_Click`, sonucu çağırır `AccessTheWebAsync` ve görüntüler.</span><span class="sxs-lookup"><span data-stu-id="e1051-112">`startButton_Click`, which calls `AccessTheWebAsync` and displays the result.</span></span>

- <span data-ttu-id="e1051-113">`AccessTheWebAsync`, bir Web sitesinin içeriğini bir dize olarak indirir ve dizenin uzunluğunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="e1051-113">`AccessTheWebAsync`, which downloads the contents of a website as a string and returns the length of the string.</span></span> <span data-ttu-id="e1051-114">`AccessTheWebAsync`, içeriğini indirmek <xref:System.Net.Http.HttpClient> için zaman uyumsuz bir yöntem kullanır. <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29></span><span class="sxs-lookup"><span data-stu-id="e1051-114">`AccessTheWebAsync` uses an asynchronous <xref:System.Net.Http.HttpClient> method, <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>, to download the contents.</span></span>

<span data-ttu-id="e1051-115">Numaralandırılmış görüntüleme satırları programın nasıl çalıştığını anlamanıza yardımcı olmak ve işaretlenen her bir noktada ne olduğunu açıklamak için programın tamamında stratejik noktalarda görünür.</span><span class="sxs-lookup"><span data-stu-id="e1051-115">Numbered display lines appear at strategic points throughout the program to help you understand how the program runs and to explain what happens at each point that is marked.</span></span> <span data-ttu-id="e1051-116">Görüntüleme satırları "BIR"-"altı" olarak etiketlenir.</span><span class="sxs-lookup"><span data-stu-id="e1051-116">The display lines are labeled "ONE" through "SIX."</span></span> <span data-ttu-id="e1051-117">Etiketler, programın bu kod satırlarına ulaştığı sırayı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e1051-117">The labels represent the order in which the program reaches these lines of code.</span></span>

<span data-ttu-id="e1051-118">Aşağıdaki kod programın bir ana hattını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e1051-118">The following code shows an outline of the program.</span></span>

```vb
Class MainWindow

    Private Async Sub StartButton_Click(sender As Object, e As RoutedEventArgs) Handles StartButton.Click

        ' ONE
        Dim getLengthTask As Task(Of Integer) = AccessTheWebAsync()

        ' FOUR
        Dim contentLength As Integer = Await getLengthTask

        ' SIX
        ResultsTextBox.Text &=
            String.Format(vbCrLf & "Length of the downloaded string: {0}." & vbCrLf, contentLength)

    End Sub

    Async Function AccessTheWebAsync() As Task(Of Integer)

        ' TWO
        Dim client As HttpClient = New HttpClient()
        Dim getStringTask As Task(Of String) =
            client.GetStringAsync("https://msdn.microsoft.com")

        ' THREE
        Dim urlContents As String = Await getStringTask

        ' FIVE
        Return urlContents.Length
    End Function

End Class
```

<span data-ttu-id="e1051-119">Etiketlenmiş konumların her biri, "BIR"-"ALTıDA", programın geçerli durumuyla ilgili bilgileri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="e1051-119">Each of the labeled locations, "ONE" through "SIX," displays information about the current state of the program.</span></span> <span data-ttu-id="e1051-120">Aşağıdaki çıktı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="e1051-120">The following output is produced.</span></span>

```
ONE:   Entering startButton_Click.
           Calling AccessTheWebAsync.

TWO:   Entering AccessTheWebAsync.
           Calling HttpClient.GetStringAsync.

THREE: Back in AccessTheWebAsync.
           Task getStringTask is started.
           About to await getStringTask & return a Task<int> to startButton_Click.

FOUR:  Back in startButton_Click.
           Task getLengthTask is started.
           About to await getLengthTask -- no caller to return to.

FIVE:  Back in AccessTheWebAsync.
           Task getStringTask is complete.
           Processing the return statement.
           Exiting from AccessTheWebAsync.

SIX:   Back in startButton_Click.
           Task getLengthTask is finished.
           Result from AccessTheWebAsync is stored in contentLength.
           About to display contentLength and exit.

Length of the downloaded string: 33946.
```

## <a name="set-up-the-program"></a><span data-ttu-id="e1051-121">Program Ayarlama</span><span class="sxs-lookup"><span data-stu-id="e1051-121">Set Up the Program</span></span>

<span data-ttu-id="e1051-122">Bu konunun kullandığı kodu MSDN 'den indirebilirsiniz veya kendiniz oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e1051-122">You can download the code that this topic uses from MSDN, or you can build it yourself.</span></span>

> [!NOTE]
> <span data-ttu-id="e1051-123">Örneği çalıştırmak için, bilgisayarınızda Visual Studio 2012 veya daha yeni bir sürümü ve .NET Framework 4,5 ya da daha yeni bir sürümü yüklü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e1051-123">To run the example, you must have Visual Studio 2012 or newer and  the .NET Framework 4.5 or newer installed on your computer.</span></span>

### <a name="download-the-program"></a><span data-ttu-id="e1051-124">Programı indir</span><span class="sxs-lookup"><span data-stu-id="e1051-124">Download the Program</span></span>

<span data-ttu-id="e1051-125">Bu konu [için uygulamayı zaman uyumsuz örnekten indirebilirsiniz: Zaman uyumsuz programlarda](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0)denetim akışı.</span><span class="sxs-lookup"><span data-stu-id="e1051-125">You can download the application for this topic from [Async Sample: Control Flow in Async Programs](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0).</span></span> <span data-ttu-id="e1051-126">Aşağıdaki adımlar programı açın ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="e1051-126">The following steps open and run the program.</span></span>

1. <span data-ttu-id="e1051-127">İndirilen dosyayı sıkıştırmasını açın ve ardından Visual Studio 'Yu başlatın.</span><span class="sxs-lookup"><span data-stu-id="e1051-127">Unzip the downloaded file, and then start Visual Studio.</span></span>

2. <span data-ttu-id="e1051-128">Menü çubuğunda **Dosya**, **Aç**, **Proje/çözüm**' ü seçin.</span><span class="sxs-lookup"><span data-stu-id="e1051-128">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>

3. <span data-ttu-id="e1051-129">Sıkıştırılmış örnek kodu tutan klasöre gidin, çözüm (. sln) dosyasını açın ve ardından projeyi derlemek ve çalıştırmak için F5 tuşunu seçin.</span><span class="sxs-lookup"><span data-stu-id="e1051-129">Navigate to the folder that holds the unzipped sample code, open the solution (.sln) file, and then choose the F5 key to build and run the project.</span></span>

### <a name="build-the-program-yourself"></a><span data-ttu-id="e1051-130">Programı kendiniz oluşturun</span><span class="sxs-lookup"><span data-stu-id="e1051-130">Build the Program Yourself</span></span>

<span data-ttu-id="e1051-131">Aşağıdaki Windows Presentation Foundation (WPF) projesi bu konunun kod örneğini içerir.</span><span class="sxs-lookup"><span data-stu-id="e1051-131">The following Windows Presentation Foundation (WPF) project contains the code example for this topic.</span></span>

<span data-ttu-id="e1051-132">Projeyi çalıştırmak için aşağıdaki adımları gerçekleştirin:</span><span class="sxs-lookup"><span data-stu-id="e1051-132">To run the project, perform the following steps:</span></span>

1. <span data-ttu-id="e1051-133">Visual Studio’yu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="e1051-133">Start Visual Studio.</span></span>

2. <span data-ttu-id="e1051-134">Menü çubuğunda, **dosya**, **yeni**, **proje**.</span><span class="sxs-lookup"><span data-stu-id="e1051-134">On the menu bar, choose **File**, **New**, **Project**.</span></span>

    <span data-ttu-id="e1051-135">**Yeni proje** iletişim kutusu açılır.</span><span class="sxs-lookup"><span data-stu-id="e1051-135">The **New Project** dialog box opens.</span></span>

3. <span data-ttu-id="e1051-136">**Yüklü şablonlar** bölmesinde **Visual Basic**öğesini seçin ve ardından Proje türleri listesinden **WPF uygulaması** ' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="e1051-136">In the **Installed Templates** pane, choose **Visual Basic**, and then choose **WPF Application** from the list of project types.</span></span>

4. <span data-ttu-id="e1051-137">Projenin `AsyncTracer` adı olarak girin ve **Tamam** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="e1051-137">Enter `AsyncTracer` as the name of the project, and then choose the **OK** button.</span></span>

    <span data-ttu-id="e1051-138">Yeni proje **Çözüm Gezgini**görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="e1051-138">The new project appears in **Solution Explorer**.</span></span>

5. <span data-ttu-id="e1051-139">Visual Studio Code düzenleyicisinde **MainWindow. xaml** sekmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="e1051-139">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>

    <span data-ttu-id="e1051-140">Sekme görünür değilse, **Çözüm Gezgini**' de MainWindow. xaml için kısayol menüsünü açın ve **kodu görüntüle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="e1051-140">If the tab isn’t visible, open the shortcut menu for MainWindow.xaml in **Solution Explorer**, and then choose **View Code**.</span></span>

6. <span data-ttu-id="e1051-141">MainWindow. xaml ' nin **xaml** görünümünde, kodu aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="e1051-141">In the **XAML** view of MainWindow.xaml, replace the code with the following code.</span></span>

    ```vb
    <Window
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008" xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006" mc:Ignorable="d" x:Class="MainWindow"
        Title="Control Flow Trace" Height="350" Width="525">
        <Grid>
            <Button x:Name="StartButton" Content="Start" HorizontalAlignment="Left" Margin="221,10,0,0" VerticalAlignment="Top" Width="75"/>
            <TextBox x:Name="ResultsTextBox" HorizontalAlignment="Left" TextWrapping="Wrap" VerticalAlignment="Bottom" Width="510" Height="265" FontFamily="Lucida Console" FontSize="10" VerticalScrollBarVisibility="Visible" d:LayoutOverrides="HorizontalMargin"/>

        </Grid>
    </Window>
    ```

    <span data-ttu-id="e1051-142">Bir metin kutusu ve bir düğme içeren basit bir pencere, MainWindow. xaml **Tasarım** görünümünde görünür.</span><span class="sxs-lookup"><span data-stu-id="e1051-142">A simple window that contains a text box and a button appears in the **Design** view of MainWindow.xaml.</span></span>

7. <span data-ttu-id="e1051-143">İçin <xref:System.Net.Http>bir başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="e1051-143">Add a reference for <xref:System.Net.Http>.</span></span>

8. <span data-ttu-id="e1051-144">**Çözüm Gezgini**, MainWindow. xaml. vb için kısayol menüsünü açın ve **kodu görüntüle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="e1051-144">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.vb, and then choose **View Code**.</span></span>

9. <span data-ttu-id="e1051-145">MainWindow. xaml. vb dosyasında, kodu aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="e1051-145">In MainWindow.xaml.vb , replace the code with the following code.</span></span>

    ```vb
    ' Add an Imports statement and a reference for System.Net.Http.
    Imports System.Net.Http

    Class MainWindow

        Private Async Sub StartButton_Click(sender As Object, e As RoutedEventArgs) Handles StartButton.Click

            ' The display lines in the example lead you through the control shifts.
            ResultsTextBox.Text &= "ONE:   Entering StartButton_Click." & vbCrLf &
                "           Calling AccessTheWebAsync." & vbCrLf

            Dim getLengthTask As Task(Of Integer) = AccessTheWebAsync()

            ResultsTextBox.Text &= vbCrLf & "FOUR:  Back in StartButton_Click." & vbCrLf &
                "           Task getLengthTask is started." & vbCrLf &
                "           About to await getLengthTask -- no caller to return to." & vbCrLf

            Dim contentLength As Integer = Await getLengthTask

            ResultsTextBox.Text &= vbCrLf & "SIX:   Back in StartButton_Click." & vbCrLf &
                "           Task getLengthTask is finished." & vbCrLf &
                "           Result from AccessTheWebAsync is stored in contentLength." & vbCrLf &
                "           About to display contentLength and exit." & vbCrLf

            ResultsTextBox.Text &=
                String.Format(vbCrLf & "Length of the downloaded string: {0}." & vbCrLf, contentLength)
        End Sub

        Async Function AccessTheWebAsync() As Task(Of Integer)

            ResultsTextBox.Text &= vbCrLf & "TWO:   Entering AccessTheWebAsync."

            ' Declare an HttpClient object.
            Dim client As HttpClient = New HttpClient()

            ResultsTextBox.Text &= vbCrLf & "           Calling HttpClient.GetStringAsync." & vbCrLf

            ' GetStringAsync returns a Task(Of String).
            Dim getStringTask As Task(Of String) = client.GetStringAsync("https://msdn.microsoft.com")

            ResultsTextBox.Text &= vbCrLf & "THREE: Back in AccessTheWebAsync." & vbCrLf &
                "           Task getStringTask is started."

            ' AccessTheWebAsync can continue to work until getStringTask is awaited.

            ResultsTextBox.Text &=
                vbCrLf & "           About to await getStringTask & return a Task(Of Integer) to StartButton_Click." & vbCrLf

            ' Retrieve the website contents when task is complete.
            Dim urlContents As String = Await getStringTask

            ResultsTextBox.Text &= vbCrLf & "FIVE:  Back in AccessTheWebAsync." &
                vbCrLf & "           Task getStringTask is complete." &
                vbCrLf & "           Processing the return statement." &
                vbCrLf & "           Exiting from AccessTheWebAsync." & vbCrLf

            Return urlContents.Length
        End Function

    End Class
    ```

10. <span data-ttu-id="e1051-146">Programı çalıştırmak için F5 tuşunu seçin ve sonra **Başlat** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="e1051-146">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>

    <span data-ttu-id="e1051-147">Aşağıdaki çıktı görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="e1051-147">The following output should appear.</span></span>

    ```
    ONE:   Entering startButton_Click.
               Calling AccessTheWebAsync.

    TWO:   Entering AccessTheWebAsync.
               Calling HttpClient.GetStringAsync.

    THREE: Back in AccessTheWebAsync.
               Task getStringTask is started.
               About to await getStringTask & return a Task<int> to startButton_Click.

    FOUR:  Back in startButton_Click.
               Task getLengthTask is started.
               About to await getLengthTask -- no caller to return to.

    FIVE:  Back in AccessTheWebAsync.
               Task getStringTask is complete.
               Processing the return statement.
               Exiting from AccessTheWebAsync.

    SIX:   Back in startButton_Click.
               Task getLengthTask is finished.
               Result from AccessTheWebAsync is stored in contentLength.
               About to display contentLength and exit.

    Length of the downloaded string: 33946.
    ```

## <a name="trace-the-program"></a><span data-ttu-id="e1051-148">Programı izleme</span><span class="sxs-lookup"><span data-stu-id="e1051-148">Trace the Program</span></span>

### <a name="steps-one-and-two"></a><span data-ttu-id="e1051-149">Adım BIR ve ıkı</span><span class="sxs-lookup"><span data-stu-id="e1051-149">Steps ONE and TWO</span></span>

<span data-ttu-id="e1051-150">İlk iki görüntüleme satırı `startButton_Click` yolu çağrı `AccessTheWebAsync`olarak izler ve `AccessTheWebAsync` zaman uyumsuz <xref:System.Net.Http.HttpClient> yöntemi <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>çağırır.</span><span class="sxs-lookup"><span data-stu-id="e1051-150">The first two display lines trace the path as `startButton_Click` calls `AccessTheWebAsync`, and `AccessTheWebAsync` calls the asynchronous <xref:System.Net.Http.HttpClient> method <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>.</span></span> <span data-ttu-id="e1051-151">Aşağıdaki görüntüde yönteminden yöntemine yapılan çağrılar özetlenmektedir.</span><span class="sxs-lookup"><span data-stu-id="e1051-151">The following image outlines the calls from method to method.</span></span>

<span data-ttu-id="e1051-152">![Adım bir ve iki](../../../../csharp/programming-guide/concepts/async/media/asynctrace-onetwo.png "Asynctrace-ONETWO")</span><span class="sxs-lookup"><span data-stu-id="e1051-152">![Steps ONE and TWO](../../../../csharp/programming-guide/concepts/async/media/asynctrace-onetwo.png "AsyncTrace-ONETWO")</span></span>

<span data-ttu-id="e1051-153">Hem hem de `AccessTheWebAsync` `client.GetStringAsync`öğesinindönüş türü. <xref:System.Threading.Tasks.Task%601></span><span class="sxs-lookup"><span data-stu-id="e1051-153">The return type of both `AccessTheWebAsync` and `client.GetStringAsync` is <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="e1051-154">İçin `AccessTheWebAsync`, TResult bir tamsayıdır.</span><span class="sxs-lookup"><span data-stu-id="e1051-154">For `AccessTheWebAsync`, TResult is an integer.</span></span> <span data-ttu-id="e1051-155">İçin `GetStringAsync`, TResult bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="e1051-155">For `GetStringAsync`, TResult is a string.</span></span> <span data-ttu-id="e1051-156">Zaman uyumsuz yöntem dönüş türleri hakkında daha fazla bilgi için bkz. [Async Return Types (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="e1051-156">For more information about async method return types, see [Async Return Types (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span></span>

<span data-ttu-id="e1051-157">Bir görev döndüren zaman uyumsuz yöntem, Denetim çağırana geri dönzaman bir görev örneği döndürür.</span><span class="sxs-lookup"><span data-stu-id="e1051-157">A task-returning async method returns a task instance when control shifts back to the caller.</span></span> <span data-ttu-id="e1051-158">Çağrılan yöntemde bir `Await` işleçle karşılaşıldığında veya çağrılan yöntem sona erdiğinde, denetim zaman uyumsuz bir yöntemden çağırana döner.</span><span class="sxs-lookup"><span data-stu-id="e1051-158">Control returns from an async method to its caller either when an `Await` operator is encountered in the called method or when the called method ends.</span></span> <span data-ttu-id="e1051-159">"Üç" ile "ALTıDAN" Etiketlenmiş görüntüleme satırları işlemin bu bölümünü izler.</span><span class="sxs-lookup"><span data-stu-id="e1051-159">The display lines that are labeled "THREE" through "SIX" trace this part of the process.</span></span>

### <a name="step-three"></a><span data-ttu-id="e1051-160">Üçüncü adım</span><span class="sxs-lookup"><span data-stu-id="e1051-160">Step THREE</span></span>

<span data-ttu-id="e1051-161">İçinde `AccessTheWebAsync`, zaman uyumsuz yöntemi <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> hedef Web sayfasının içeriğini indirmek için çağırılır.</span><span class="sxs-lookup"><span data-stu-id="e1051-161">In `AccessTheWebAsync`, the asynchronous method <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> is called to download the contents of the target webpage.</span></span> <span data-ttu-id="e1051-162">Denetim, ' `client.GetStringAsync` den `AccessTheWebAsync` `client.GetStringAsync` ' a döner.</span><span class="sxs-lookup"><span data-stu-id="e1051-162">Control returns from `client.GetStringAsync` to `AccessTheWebAsync` when `client.GetStringAsync` returns.</span></span>

<span data-ttu-id="e1051-163">Yöntemi, `getStringTask` içindeki`AccessTheWebAsync`değişkenine atanan bir dize görevi döndürür. `client.GetStringAsync`</span><span class="sxs-lookup"><span data-stu-id="e1051-163">The `client.GetStringAsync` method returns a task of string that’s assigned to the `getStringTask` variable in `AccessTheWebAsync`.</span></span> <span data-ttu-id="e1051-164">Örnek programda aşağıdaki satır, ve atama için `client.GetStringAsync` çağrıyı gösterir.</span><span class="sxs-lookup"><span data-stu-id="e1051-164">The following line in the example program shows the call to `client.GetStringAsync` and the assignment.</span></span>

```vb
Dim getStringTask As Task(Of String) = client.GetStringAsync("https://msdn.microsoft.com")
```

<span data-ttu-id="e1051-165">Son olarak gerçek bir dize oluşturmak `client.GetStringAsync` için görevi bir Promise olarak düşünebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e1051-165">You can think of the task as a promise by `client.GetStringAsync` to produce an actual string eventually.</span></span> <span data-ttu-id="e1051-166">Bu sırada, bu, `AccessTheWebAsync` ' de taahhüt edilen `client.GetStringAsync`dizeye bağlı değilse, bu iş, bekleme sırasında `client.GetStringAsync` devam edebilir.</span><span class="sxs-lookup"><span data-stu-id="e1051-166">In the meantime, if `AccessTheWebAsync` has work to do that doesn't depend on the promised string from `client.GetStringAsync`, that work can continue while  `client.GetStringAsync` waits.</span></span> <span data-ttu-id="e1051-167">Örnekte, "üç" olarak etiketlenen aşağıdaki çıktı satırları, bağımsız iş yapmak için fırsatı temsil eder</span><span class="sxs-lookup"><span data-stu-id="e1051-167">In the example, the following lines of output, which are labeled "THREE," represent the opportunity to do independent work</span></span>

```
THREE: Back in AccessTheWebAsync.
           Task getStringTask is started.
           About to await getStringTask & return a Task<int> to startButton_Click.
```

 <span data-ttu-id="e1051-168">Aşağıdaki ifade, ne zaman `AccessTheWebAsync` beklediğinde `getStringTask` ' de ilerlemeyi askıya alır.</span><span class="sxs-lookup"><span data-stu-id="e1051-168">The following statement suspends progress in `AccessTheWebAsync` when `getStringTask` is awaited.</span></span>

```vb
Dim urlContents As String = Await getStringTask
```

<span data-ttu-id="e1051-169">Aşağıdaki görüntüde denetim `client.GetStringAsync` `getStringTask` akışını, bir await işlecinin uygulamasına `getStringTask` ve oluşturma işleminden öğesine kadar gösterir.</span><span class="sxs-lookup"><span data-stu-id="e1051-169">The following image shows the flow of control from `client.GetStringAsync` to the assignment to `getStringTask` and from the creation of `getStringTask` to the application of an Await operator.</span></span>

<span data-ttu-id="e1051-170">![Üçüncü adım](../../../../csharp/programming-guide/concepts/async/media/asynctrace-three.png "Asynctrace-üç")</span><span class="sxs-lookup"><span data-stu-id="e1051-170">![Step THREE](../../../../csharp/programming-guide/concepts/async/media/asynctrace-three.png "AsyncTrace-Three")</span></span>

<span data-ttu-id="e1051-171">Await ifadesi dönüşene `AccessTheWebAsync` kadar `client.GetStringAsync` askıya alır.</span><span class="sxs-lookup"><span data-stu-id="e1051-171">The await expression suspends `AccessTheWebAsync` until `client.GetStringAsync` returns.</span></span> <span data-ttu-id="e1051-172">Bu sırada denetim, ' `AccessTheWebAsync` `startButton_Click`ın çağıranına döner.</span><span class="sxs-lookup"><span data-stu-id="e1051-172">In the meantime, control returns to the caller of `AccessTheWebAsync`, `startButton_Click`.</span></span>

> [!NOTE]
> <span data-ttu-id="e1051-173">Genellikle, zaman uyumsuz bir yöntem çağrısını hemen bekleolursunuz.</span><span class="sxs-lookup"><span data-stu-id="e1051-173">Typically, you await the call to an asynchronous method immediately.</span></span> <span data-ttu-id="e1051-174">Örneğin, aşağıdaki atama, oluşturan ve daha sonra bekleyen `getStringTask`önceki kodun yerini alır:`Dim urlContents As String = Await client.GetStringAsync("https://msdn.microsoft.com")`</span><span class="sxs-lookup"><span data-stu-id="e1051-174">For example, the following assignment could replace the previous code that creates and then awaits `getStringTask`: `Dim urlContents As String = Await client.GetStringAsync("https://msdn.microsoft.com")`</span></span>
>
> <span data-ttu-id="e1051-175">Bu konuda, Await işleci daha sonra Denetim akışını program aracılığıyla işaretleyen çıkış satırlarına uyum sağlayacak şekilde uygulanır.</span><span class="sxs-lookup"><span data-stu-id="e1051-175">In this topic, the await operator is applied later to accommodate the output lines that mark the flow of control through the program.</span></span>

### <a name="step-four"></a><span data-ttu-id="e1051-176">4\. adım</span><span class="sxs-lookup"><span data-stu-id="e1051-176">Step FOUR</span></span>

<span data-ttu-id="e1051-177">`AccessTheWebAsync` Tarafından`Task(Of Integer)`belirtilen dönüş türü.</span><span class="sxs-lookup"><span data-stu-id="e1051-177">The declared return type of `AccessTheWebAsync` is `Task(Of Integer)`.</span></span> <span data-ttu-id="e1051-178">Bu nedenle, askıya alındığında, için `startButton_Click`bir tamsayı görevi döndürür. `AccessTheWebAsync`</span><span class="sxs-lookup"><span data-stu-id="e1051-178">Therefore, when `AccessTheWebAsync` is suspended, it returns a task of integer to `startButton_Click`.</span></span> <span data-ttu-id="e1051-179">Döndürülen görevin `getStringTask`olmadığını anlamalısınız.</span><span class="sxs-lookup"><span data-stu-id="e1051-179">You should understand that the returned task isn’t `getStringTask`.</span></span> <span data-ttu-id="e1051-180">Döndürülen görev, `AccessTheWebAsync`askıya alınan yöntemde ne yapılması gerektiğini temsil eden yeni bir tamsayı görevi.</span><span class="sxs-lookup"><span data-stu-id="e1051-180">The returned task is a new task of integer that represents what remains to be done in the suspended method, `AccessTheWebAsync`.</span></span> <span data-ttu-id="e1051-181">Görev tamamlandığında bir tamsayı üretmek `AccessTheWebAsync` için görevi bir taahhüddir.</span><span class="sxs-lookup"><span data-stu-id="e1051-181">The task is a promise from `AccessTheWebAsync` to produce an integer when the task is complete.</span></span>

<span data-ttu-id="e1051-182">Aşağıdaki ifade bu görevi `getLengthTask` değişkenine atar.</span><span class="sxs-lookup"><span data-stu-id="e1051-182">The following statement assigns this task to the `getLengthTask` variable.</span></span>

```vb
Dim getLengthTask As Task(Of Integer) = AccessTheWebAsync()
```

<span data-ttu-id="e1051-183">' De `AccessTheWebAsync`olduğu `startButton_Click` gibi, görev beklenene kadar zaman uyumsuz görevin (`getLengthTask`) sonuçlarına bağlı olmayan çalışmaya devam edebilir.</span><span class="sxs-lookup"><span data-stu-id="e1051-183">As in `AccessTheWebAsync`, `startButton_Click` can continue with work that doesn’t depend on the results of the asynchronous task (`getLengthTask`) until the task is awaited.</span></span> <span data-ttu-id="e1051-184">Aşağıdaki çıktı satırları bu işi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e1051-184">The following output lines represent that work.</span></span>

```
FOUR:  Back in startButton_Click.
           Task getLengthTask is started.
           About to await getLengthTask -- no caller to return to.
```

<span data-ttu-id="e1051-185">İlerleme durumu, beklediğinde `getLengthTask` askıya alınır. `startButton_Click`</span><span class="sxs-lookup"><span data-stu-id="e1051-185">Progress in `startButton_Click` is suspended when `getLengthTask` is awaited.</span></span> <span data-ttu-id="e1051-186">Aşağıdaki atama açıklaması tamamlanana kadar `startButton_Click` `AccessTheWebAsync` askıya alınır.</span><span class="sxs-lookup"><span data-stu-id="e1051-186">The following assignment statement suspends `startButton_Click` until `AccessTheWebAsync` is complete.</span></span>

```vb
Dim contentLength As Integer = Await getLengthTask
```

<span data-ttu-id="e1051-187">Aşağıdaki `AccessTheWebAsync` çizimde, oklar bir `getLengthTask`değerin atanması için içindeki Await ifadesinden denetim akışını gösterir ve `startButton_Click` ardından beklenene kadar `getLengthTask` normal işleme gelir.</span><span class="sxs-lookup"><span data-stu-id="e1051-187">In the following illustration, the arrows show the flow of control from the await expression in `AccessTheWebAsync` to the assignment of a value to `getLengthTask`, followed by normal processing in `startButton_Click` until `getLengthTask` is awaited.</span></span>

<span data-ttu-id="e1051-188">4\. ![adım](../../../../csharp/programming-guide/concepts/async/media/asynctrace-four.png "Asynctrace-dört")</span><span class="sxs-lookup"><span data-stu-id="e1051-188">![Step FOUR](../../../../csharp/programming-guide/concepts/async/media/asynctrace-four.png "AsyncTrace-FOUR")</span></span>

### <a name="step-five"></a><span data-ttu-id="e1051-189">5\. adım</span><span class="sxs-lookup"><span data-stu-id="e1051-189">Step FIVE</span></span>

<span data-ttu-id="e1051-190">`AccessTheWebAsync` İşlemin tamamlandığını `client.GetStringAsync` işaret ederse, içindeki işleme askıya alma işleminden serbest bırakılır ve await ifadesinin ötesinde devam edebilir.</span><span class="sxs-lookup"><span data-stu-id="e1051-190">When `client.GetStringAsync` signals that it’s complete, processing in `AccessTheWebAsync` is released from suspension and can continue past the await statement.</span></span> <span data-ttu-id="e1051-191">Aşağıdaki çıktı satırları işleme sürdürme temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e1051-191">The following lines of output represent the resumption of processing.</span></span>

```
FIVE:  Back in AccessTheWebAsync.
           Task getStringTask is complete.
           Processing the return statement.
           Exiting from AccessTheWebAsync.
```

<span data-ttu-id="e1051-192">Return ifadesinin `urlContents.Length`işleneni, `AccessTheWebAsync` döndüren görevde saklanır.</span><span class="sxs-lookup"><span data-stu-id="e1051-192">The operand of the return statement, `urlContents.Length`, is stored in the task that  `AccessTheWebAsync` returns.</span></span> <span data-ttu-id="e1051-193">Await ifadesi bu değeri içindeki `getLengthTask` `startButton_Click`öğesinden alır.</span><span class="sxs-lookup"><span data-stu-id="e1051-193">The await expression retrieves that value from `getLengthTask` in `startButton_Click`.</span></span>

<span data-ttu-id="e1051-194">Aşağıdaki görüntüde (ve `client.GetStringAsync` `getStringTask`) sonra denetimin aktarımı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="e1051-194">The following image shows the transfer of control after `client.GetStringAsync` (and `getStringTask`) are complete.</span></span>

<span data-ttu-id="e1051-195">![5. adım](../../../../csharp/programming-guide/concepts/async/media/asynctrace-five.png "Asynctrace-beş")</span><span class="sxs-lookup"><span data-stu-id="e1051-195">![Step FIVE](../../../../csharp/programming-guide/concepts/async/media/asynctrace-five.png "AsyncTrace-FIVE")</span></span>

<span data-ttu-id="e1051-196">`AccessTheWebAsync`tamamlandı olarak çalışır ve denetimi `startButton_Click`' a döner, bu da tamamlamayı bekliyor.</span><span class="sxs-lookup"><span data-stu-id="e1051-196">`AccessTheWebAsync` runs to completion, and control returns to `startButton_Click`, which is awaiting the completion.</span></span>

### <a name="step-six"></a><span data-ttu-id="e1051-197">Altı adım</span><span class="sxs-lookup"><span data-stu-id="e1051-197">Step SIX</span></span>

<span data-ttu-id="e1051-198">İşlemin tamamlandığını `startButton_Async`işaret ederse, işleme ' de await ifadesinin ötesinde devam edebilir. `AccessTheWebAsync`</span><span class="sxs-lookup"><span data-stu-id="e1051-198">When `AccessTheWebAsync` signals that it’s complete, processing can continue past the await statement in `startButton_Async`.</span></span> <span data-ttu-id="e1051-199">Aslında programın daha fazla şey yoktur.</span><span class="sxs-lookup"><span data-stu-id="e1051-199">In fact, the program has nothing more to do.</span></span>

<span data-ttu-id="e1051-200">Aşağıdaki çıktı satırları içinde `startButton_Async`işleme sürdürme temsil eder:</span><span class="sxs-lookup"><span data-stu-id="e1051-200">The following lines of output represent the resumption of processing in `startButton_Async`:</span></span>

```
SIX:   Back in startButton_Click.
           Task getLengthTask is finished.
           Result from AccessTheWebAsync is stored in contentLength.
           About to display contentLength and exit.
```

<span data-ttu-id="e1051-201">Await ifadesi ' de `getLengthTask` `AccessTheWebAsync`return deyiminin işleneni olan Integer değerinden alır.</span><span class="sxs-lookup"><span data-stu-id="e1051-201">The await expression retrieves from `getLengthTask` the integer value that’s the operand of the return statement in `AccessTheWebAsync`.</span></span> <span data-ttu-id="e1051-202">Aşağıdaki ifade bu değeri `contentLength` değişkenine atar.</span><span class="sxs-lookup"><span data-stu-id="e1051-202">The following statement assigns that value to the `contentLength` variable.</span></span>

```vb
Dim contentLength As Integer = Await getLengthTask
```

<span data-ttu-id="e1051-203">Aşağıdaki görüntüde ' den `AccessTheWebAsync` ' e `startButton_Click`denetim dönüşü gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="e1051-203">The following image shows the return of control from `AccessTheWebAsync` to `startButton_Click`.</span></span>

<span data-ttu-id="e1051-204">![Altı adım](../../../../csharp/programming-guide/concepts/async/media/asynctrace-six.png "Asynctrace-altı")</span><span class="sxs-lookup"><span data-stu-id="e1051-204">![Step SIX](../../../../csharp/programming-guide/concepts/async/media/asynctrace-six.png "AsyncTrace-SIX")</span></span>

## <a name="see-also"></a><span data-ttu-id="e1051-205">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e1051-205">See also</span></span>

- [<span data-ttu-id="e1051-206">Async ve await ile zaman uyumsuz programlama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e1051-206">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/index.md)
- [<span data-ttu-id="e1051-207">Zaman uyumsuz dönüş türleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e1051-207">Async Return Types (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md)
- [<span data-ttu-id="e1051-208">İzlenecek yol: Async ve await kullanarak Web 'e erişme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e1051-208">Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="e1051-209">Zaman uyumsuz örnek: Zaman uyumsuz programlarda denetim akışı (C# ve Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e1051-209">Async Sample: Control Flow in Async Programs (C# and Visual Basic)</span></span>](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0)
