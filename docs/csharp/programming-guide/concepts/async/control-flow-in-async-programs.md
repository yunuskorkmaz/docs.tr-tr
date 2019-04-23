---
title: Denetim akışı zaman uyumsuz programlarda (C#)
ms.date: 07/20/2015
ms.assetid: fc92b08b-fe1d-4d07-84ab-5192fafe06bb
ms.openlocfilehash: 6a7b8f3f41b2096e3e7524d03217bdc123f26f10
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59326209"
---
# <a name="control-flow-in-async-programs-c"></a><span data-ttu-id="73cb4-102">Denetim akışı zaman uyumsuz programlarda (C#)</span><span class="sxs-lookup"><span data-stu-id="73cb4-102">Control flow in async programs (C#)</span></span>

<span data-ttu-id="73cb4-103">Yazma ve zaman uyumsuz programları daha kolay kullanarak koruduğunuz `async` ve `await` anahtar sözcükleri.</span><span class="sxs-lookup"><span data-stu-id="73cb4-103">You can write and maintain asynchronous programs more easily by using the `async` and `await` keywords.</span></span> <span data-ttu-id="73cb4-104">Ancak, nasıl programınızı anlamazsanız sonuçlar sizi şaşırtabilir.</span><span class="sxs-lookup"><span data-stu-id="73cb4-104">However, the results might surprise you if you don't understand how your program operates.</span></span> <span data-ttu-id="73cb4-105">Bu konu, her zaman denetimi başka bir ve hangi bilgileri bir yöntemden diğerine taşır. göstermek için basit bir zamanuyumsuz program aracılığıyla denetim akışını aktarılır izler.</span><span class="sxs-lookup"><span data-stu-id="73cb4-105">This topic traces the flow of control through a simple async program to show you when control moves from one method to another and what information is transferred each time.</span></span>

<span data-ttu-id="73cb4-106">Genel olarak, zaman uyumsuz kodun yer aldığı yöntemleri işaretleyin [async (C#)](../../../../csharp/language-reference/keywords/async.md) değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="73cb4-106">In general, you mark methods that contain asynchronous code with the [async (C#)](../../../../csharp/language-reference/keywords/async.md) modifier.</span></span> <span data-ttu-id="73cb4-107">Zaman uyumsuz değiştiriciyle işaretlenmiş bir yöntemde, kullandığınız bir [await (C#)](../../../../csharp/language-reference/keywords/await.md) burada yöntemin tamamlanması bir çağrılan zaman uyumsuz işlem için duraklatacağını belirtmek için işleci.</span><span class="sxs-lookup"><span data-stu-id="73cb4-107">In a method that's marked with an async modifier, you can use an [await (C#)](../../../../csharp/language-reference/keywords/await.md) operator to specify where the method pauses to wait for a called asynchronous process to complete.</span></span> <span data-ttu-id="73cb4-108">Daha fazla bilgi için [Asynchronous Programming with async ve await (C#)](../../../../csharp/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="73cb4-108">For more information, see [Asynchronous Programming with async and await (C#)](../../../../csharp/programming-guide/concepts/async/index.md).</span></span>

<span data-ttu-id="73cb4-109">Aşağıdaki örnek, bir dize olarak belirtilen bir Web sitesinin içeriklerini karşıdan yüklemek ve dizenin uzunluğu görüntülemek için zaman uyumsuz yöntemler kullanır.</span><span class="sxs-lookup"><span data-stu-id="73cb4-109">The following example uses async methods to download the contents of a specified website as a string and to display the length of the string.</span></span> <span data-ttu-id="73cb4-110">Örneğin, aşağıdaki iki yöntemi içerir.</span><span class="sxs-lookup"><span data-stu-id="73cb4-110">The example contains the following two methods.</span></span>

-   <span data-ttu-id="73cb4-111">`startButton_Click`, hangi çağrıları `AccessTheWebAsync` ve sonucu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="73cb4-111">`startButton_Click`, which calls `AccessTheWebAsync` and displays the result.</span></span>

-   <span data-ttu-id="73cb4-112">`AccessTheWebAsync`, bir dize olarak bir Web sitesinin içeriklerini karşıdan yükler ve dizenin uzunluğunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="73cb4-112">`AccessTheWebAsync`, which downloads the contents of a website as a string and returns the length of the string.</span></span> <span data-ttu-id="73cb4-113">`AccessTheWebAsync` zaman uyumsuz kullanan <xref:System.Net.Http.HttpClient> yöntemi <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>içeriğini indirmek için.</span><span class="sxs-lookup"><span data-stu-id="73cb4-113">`AccessTheWebAsync` uses an asynchronous <xref:System.Net.Http.HttpClient> method, <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>, to download the contents.</span></span>

<span data-ttu-id="73cb4-114">Numaralı ekran satırları, programın nasıl çalıştığını anlamanıza yardımcı olmak ve işaretlenmiş her noktada ne olacağını açıklamak için program boyunca stratejik noktalarda görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="73cb4-114">Numbered display lines appear at strategic points throughout the program to help you understand how the program runs and to explain what happens at each point that is marked.</span></span> <span data-ttu-id="73cb4-115">Görüntü satırları "Bir"ile "altı." olarak etiketlenmiştir</span><span class="sxs-lookup"><span data-stu-id="73cb4-115">The display lines are labeled "ONE" through "SIX."</span></span> <span data-ttu-id="73cb4-116">Etiketler, programın bu kod satırlarını ulaştığında sırayı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="73cb4-116">The labels represent the order in which the program reaches these lines of code.</span></span>

<span data-ttu-id="73cb4-117">Aşağıdaki kod, programın özetini gösterir.</span><span class="sxs-lookup"><span data-stu-id="73cb4-117">The following code shows an outline of the program.</span></span>

```csharp
public partial class MainWindow : Window
{
    // . . .
    private async void startButton_Click(object sender, RoutedEventArgs e)
    {
        // ONE
        Task<int> getLengthTask = AccessTheWebAsync();

        // FOUR
        int contentLength = await getLengthTask;

        // SIX
        resultsTextBox.Text +=
            $"\r\nLength of the downloaded string: {contentLength}.\r\n";
    }

    async Task<int> AccessTheWebAsync()
    {
        // TWO
        HttpClient client = new HttpClient();
        Task<string> getStringTask =
            client.GetStringAsync("https://msdn.microsoft.com");

        // THREE
        string urlContents = await getStringTask;

        // FIVE
        return urlContents.Length;
    }
}
```

<span data-ttu-id="73cb4-118">"ONE"ila "SIX" arasındaki etiketli konumların her biri, programın geçerli durumuyla ilgili bilgileri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="73cb4-118">Each of the labeled locations, "ONE" through "SIX," displays information about the current state of the program.</span></span> <span data-ttu-id="73cb4-119">Aşağıdaki çıkış üretilir:</span><span class="sxs-lookup"><span data-stu-id="73cb4-119">The following output is produced:</span></span>

```text
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

## <a name="set-up-the-program"></a><span data-ttu-id="73cb4-120">Program ayarlama</span><span class="sxs-lookup"><span data-stu-id="73cb4-120">Set up the program</span></span>

<span data-ttu-id="73cb4-121">Bu konuda kullanan kodu MSDN sitesinden yükleyebilir veya size kendiniz oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="73cb4-121">You can download the code that this topic uses from MSDN, or you can build it yourself.</span></span>

> [!NOTE]
> <span data-ttu-id="73cb4-122">Yeni bilgisayarınızda yüklü veya örneği çalıştırmak için Visual Studio 2012 veya daha yeni ve .NET Framework 4.5 yüklü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="73cb4-122">To run the example, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>

### <a name="download-the-program"></a><span data-ttu-id="73cb4-123">Programı indir</span><span class="sxs-lookup"><span data-stu-id="73cb4-123">Download the program</span></span>

<span data-ttu-id="73cb4-124">Bu konu için uygulamayı indirebilirsiniz [zaman uyumsuz örneği: Denetim akışı zaman uyumsuz programlarda](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0).</span><span class="sxs-lookup"><span data-stu-id="73cb4-124">You can download the application for this topic from [Async Sample: Control Flow in Async Programs](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0).</span></span> <span data-ttu-id="73cb4-125">Aşağıdaki adımlar, açın ve programı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="73cb4-125">The following steps open and run the program.</span></span>

1. <span data-ttu-id="73cb4-126">İndirilen dosyanın sıkıştırmasını açın ve sonra Visual Studio'yu başlatın.</span><span class="sxs-lookup"><span data-stu-id="73cb4-126">Unzip the downloaded file, and then start Visual Studio.</span></span>

2. <span data-ttu-id="73cb4-127">Menü çubuğunda, **dosya** > **açık** > **proje/çözüm**.</span><span class="sxs-lookup"><span data-stu-id="73cb4-127">On the menu bar, choose **File** > **Open** > **Project/Solution**.</span></span>

3. <span data-ttu-id="73cb4-128">Çözüm (.sln) dosyasını aç sıkıştırması açılmış örnek kodun bulunduğu klasöre gidin ve ardından **F5** anahtarı oluşturun ve projeyi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="73cb4-128">Navigate to the folder that holds the unzipped sample code, open the solution (.sln) file, and then choose the **F5** key to build and run the project.</span></span>

### <a name="create-the-program-yourself"></a><span data-ttu-id="73cb4-129">Programı kendiniz oluşturun</span><span class="sxs-lookup"><span data-stu-id="73cb4-129">Create the program Yourself</span></span>

<span data-ttu-id="73cb4-130">Aşağıdaki Windows Presentation Foundation (WPF) projesi Bu konu için kod örneği içerir.</span><span class="sxs-lookup"><span data-stu-id="73cb4-130">The following Windows Presentation Foundation (WPF) project contains the code example for this topic.</span></span>

<span data-ttu-id="73cb4-131">Projeyi çalıştırmak için aşağıdaki adımları gerçekleştirin:</span><span class="sxs-lookup"><span data-stu-id="73cb4-131">To run the project, perform the following steps:</span></span>

1. <span data-ttu-id="73cb4-132">Visual Studio’yu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="73cb4-132">Start Visual Studio.</span></span>

2. <span data-ttu-id="73cb4-133">Menü çubuğunda, **dosya** > **yeni** > **proje**.</span><span class="sxs-lookup"><span data-stu-id="73cb4-133">On the menu bar, choose **File** > **New** > **Project**.</span></span>

     <span data-ttu-id="73cb4-134">**Yeni proje** iletişim kutusu açılır.</span><span class="sxs-lookup"><span data-stu-id="73cb4-134">The **New Project** dialog box opens.</span></span>

3. <span data-ttu-id="73cb4-135">Seçin **yüklü** > **Visual C#** > **Windows Masaüstü** kategori seçip **WPF uygulaması** Proje şablonları listesinden.</span><span class="sxs-lookup"><span data-stu-id="73cb4-135">Choose the **Installed** > **Visual C#** > **Windows Desktop** category, and then choose **WPF App** from the list of project templates.</span></span>

4. <span data-ttu-id="73cb4-136">Girin `AsyncTracer` projesinin adı olarak seçip **Tamam** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="73cb4-136">Enter `AsyncTracer` as the name of the project, and then choose the **OK** button.</span></span>

     <span data-ttu-id="73cb4-137">Yeni Proje görünür **Çözüm Gezgini**.</span><span class="sxs-lookup"><span data-stu-id="73cb4-137">The new project appears in **Solution Explorer**.</span></span>

5. <span data-ttu-id="73cb4-138">Visual Studio Kod Düzenleyicisi'nde seçin **MainWindow.xaml** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="73cb4-138">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>

     <span data-ttu-id="73cb4-139">Sekme görünür değilse, nde MainWindow.xaml için kısayol menüsünü açın **Çözüm Gezgini**ve ardından **kodu görüntüle**.</span><span class="sxs-lookup"><span data-stu-id="73cb4-139">If the tab isn’t visible, open the shortcut menu for MainWindow.xaml in **Solution Explorer**, and then choose **View Code**.</span></span>

6. <span data-ttu-id="73cb4-140">İçinde **XAML** MainWindow.xaml görüntülemek için kodu aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="73cb4-140">In the **XAML** view of MainWindow.xaml, replace the code with the following code.</span></span>

    ```csharp
    <Window
            xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
            xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
            xmlns:d="http://schemas.microsoft.com/expression/blend/2008" xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006" mc:Ignorable="d" x:Class="AsyncTracer.MainWindow"
            Title="Control Flow Trace" Height="350" Width="592">
        <Grid>
            <Button x:Name="startButton" Content="Start
    " HorizontalAlignment="Left" Margin="250,10,0,0" VerticalAlignment="Top" Width="75" Height="24"  Click="startButton_Click" d:LayoutOverrides="GridBox"/>
            <TextBox x:Name="resultsTextBox" HorizontalAlignment="Left" TextWrapping="Wrap" VerticalAlignment="Bottom" Width="576" Height="265" FontFamily="Lucida Console" FontSize="10" VerticalScrollBarVisibility="Visible" Grid.ColumnSpan="3"/>
        </Grid>
    </Window>
    ```

     <span data-ttu-id="73cb4-141">Bir metin kutusu ve bir düğme içeren basit bir pencere **tasarım** MainWindow.xaml görünümü.</span><span class="sxs-lookup"><span data-stu-id="73cb4-141">A simple window that contains a text box and a button appears in the **Design** view of MainWindow.xaml.</span></span>

7. <span data-ttu-id="73cb4-142">İçin bir başvuru eklemeniz <xref:System.Net.Http>.</span><span class="sxs-lookup"><span data-stu-id="73cb4-142">Add a reference for <xref:System.Net.Http>.</span></span>

8. <span data-ttu-id="73cb4-143">İçinde **Çözüm Gezgini**için MainWindow.xaml.cs kısayol menüsünü açın ve ardından **kodu görüntüle**.</span><span class="sxs-lookup"><span data-stu-id="73cb4-143">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.cs, and then choose **View Code**.</span></span>

9. <span data-ttu-id="73cb4-144">MainWindow.xaml.cs kodu aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="73cb4-144">In MainWindow.xaml.cs, replace the code with the following code.</span></span>

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Linq;
    using System.Text;
    using System.Threading.Tasks;
    using System.Windows;
    using System.Windows.Controls;
    using System.Windows.Data;
    using System.Windows.Documents;
    using System.Windows.Input;
    using System.Windows.Media;
    using System.Windows.Media.Imaging;
    using System.Windows.Navigation;
    using System.Windows.Shapes;

    // Add a using directive and a reference for System.Net.Http;
    using System.Net.Http;

    namespace AsyncTracer
    {
        public partial class MainWindow : Window
        {
            public MainWindow()
            {
                InitializeComponent();
            }

            private async void startButton_Click(object sender, RoutedEventArgs e)
            {
                // The display lines in the example lead you through the control shifts.
                resultsTextBox.Text += "ONE:   Entering startButton_Click.\r\n" +
                    "           Calling AccessTheWebAsync.\r\n";

                Task<int> getLengthTask = AccessTheWebAsync();

                resultsTextBox.Text += "\r\nFOUR:  Back in startButton_Click.\r\n" +
                    "           Task getLengthTask is started.\r\n" +
                    "           About to await getLengthTask -- no caller to return to.\r\n";

                int contentLength = await getLengthTask;

                resultsTextBox.Text += "\r\nSIX:   Back in startButton_Click.\r\n" +
                    "           Task getLengthTask is finished.\r\n" +
                    "           Result from AccessTheWebAsync is stored in contentLength.\r\n" +
                    "           About to display contentLength and exit.\r\n";

                resultsTextBox.Text +=
                    $"\r\nLength of the downloaded string: {contentLength}.\r\n";
            }

            async Task<int> AccessTheWebAsync()
            {
                resultsTextBox.Text += "\r\nTWO:   Entering AccessTheWebAsync.";

                // Declare an HttpClient object.
                HttpClient client = new HttpClient();

                resultsTextBox.Text += "\r\n           Calling HttpClient.GetStringAsync.\r\n";

                // GetStringAsync returns a Task<string>.
                Task<string> getStringTask = client.GetStringAsync("https://msdn.microsoft.com");

                resultsTextBox.Text += "\r\nTHREE: Back in AccessTheWebAsync.\r\n" +
                    "           Task getStringTask is started.";

                // AccessTheWebAsync can continue to work until getStringTask is awaited.

                resultsTextBox.Text +=
                    "\r\n           About to await getStringTask and return a Task<int> to startButton_Click.\r\n";

                // Retrieve the website contents when task is complete.
                string urlContents = await getStringTask;

                resultsTextBox.Text += "\r\nFIVE:  Back in AccessTheWebAsync." +
                    "\r\n           Task getStringTask is complete." +
                    "\r\n           Processing the return statement." +
                    "\r\n           Exiting from AccessTheWebAsync.\r\n";

                return urlContents.Length;
            }
        }
    }
    ```

10. <span data-ttu-id="73cb4-145">Seçin **F5** programı çalıştırmak için anahtar ve ardından **Başlat** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="73cb4-145">Choose the **F5** key to run the program, and then choose the **Start** button.</span></span>

    <span data-ttu-id="73cb4-146">Aşağıdaki çıktı görünür:</span><span class="sxs-lookup"><span data-stu-id="73cb4-146">The following output appears:</span></span>

    ```text
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

## <a name="trace-the-program"></a><span data-ttu-id="73cb4-147">Programı İzle</span><span class="sxs-lookup"><span data-stu-id="73cb4-147">Trace the program</span></span>

### <a name="steps-one-and-two"></a><span data-ttu-id="73cb4-148">BİR ve ikinci adımlar</span><span class="sxs-lookup"><span data-stu-id="73cb4-148">Steps ONE and TWO</span></span>

<span data-ttu-id="73cb4-149">İlk iki görüntü satırı yolu olarak izleme `startButton_Click` çağrıları `AccessTheWebAsync`, ve `AccessTheWebAsync` zaman uyumsuz çağrı <xref:System.Net.Http.HttpClient> yöntemi <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>.</span><span class="sxs-lookup"><span data-stu-id="73cb4-149">The first two display lines trace the path as `startButton_Click` calls `AccessTheWebAsync`, and `AccessTheWebAsync` calls the asynchronous <xref:System.Net.Http.HttpClient> method <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>.</span></span> <span data-ttu-id="73cb4-150">Aşağıdaki resimde yöntemden yönteme çağrılar özetlenmektedir.</span><span class="sxs-lookup"><span data-stu-id="73cb4-150">The following image outlines the calls from method to method.</span></span>

<span data-ttu-id="73cb4-151">![BİR ve ikinci adımlar](../../../../csharp/programming-guide/concepts/async/media/asynctrace-onetwo.png "AsyncTrace ONETWO")</span><span class="sxs-lookup"><span data-stu-id="73cb4-151">![Steps ONE and TWO](../../../../csharp/programming-guide/concepts/async/media/asynctrace-onetwo.png "AsyncTrace-ONETWO")</span></span>

<span data-ttu-id="73cb4-152">Dönüş türü, her ikisi de `AccessTheWebAsync` ve `client.GetStringAsync` olduğu <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="73cb4-152">The return type of both `AccessTheWebAsync` and `client.GetStringAsync` is <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="73cb4-153">İçin `AccessTheWebAsync`, TResult bir tamsayı olduğu.</span><span class="sxs-lookup"><span data-stu-id="73cb4-153">For `AccessTheWebAsync`, TResult is an integer.</span></span> <span data-ttu-id="73cb4-154">İçin `GetStringAsync`, TResult olan bir dize.</span><span class="sxs-lookup"><span data-stu-id="73cb4-154">For `GetStringAsync`, TResult is a string.</span></span> <span data-ttu-id="73cb4-155">Zaman uyumsuz yöntem dönüş türleri hakkında daha fazla bilgi için bkz: [Async Return Types (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="73cb4-155">For more information about async method return types, see [Async Return Types (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md).</span></span>

<span data-ttu-id="73cb4-156">Bir görev döndüren zaman uyumsuz yöntem, Denetim arayana geri geçtiğinde bir görev örneği döndürür.</span><span class="sxs-lookup"><span data-stu-id="73cb4-156">A task-returning async method returns a task instance when control shifts back to the caller.</span></span> <span data-ttu-id="73cb4-157">Denetim, uyumsuz bir yöntemden arayanına döner ya da bir `await` çağrılan yöntem veya çağrılan yöntem sona erdiğinde işleciyle karşılaşıldığında.</span><span class="sxs-lookup"><span data-stu-id="73cb4-157">Control returns from an async method to its caller either when an `await` operator is encountered in the called method or when the called method ends.</span></span> <span data-ttu-id="73cb4-158">"Üç"ile "altı" etiketli görüntü satırları işlemin bu kısmında izleme.</span><span class="sxs-lookup"><span data-stu-id="73cb4-158">The display lines that are labeled "THREE" through "SIX" trace this part of the process.</span></span>

### <a name="step-three"></a><span data-ttu-id="73cb4-159">Adım üç</span><span class="sxs-lookup"><span data-stu-id="73cb4-159">Step THREE</span></span>

<span data-ttu-id="73cb4-160">İçinde `AccessTheWebAsync`, zaman uyumsuz yöntemin <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> hedef Web sayfasının içeriğini indirmek için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="73cb4-160">In `AccessTheWebAsync`, the asynchronous method <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> is called to download the contents of the target webpage.</span></span> <span data-ttu-id="73cb4-161">Denetim döndüğü `client.GetStringAsync` için `AccessTheWebAsync` olduğunda `client.GetStringAsync` döndürür.</span><span class="sxs-lookup"><span data-stu-id="73cb4-161">Control returns from `client.GetStringAsync` to `AccessTheWebAsync` when `client.GetStringAsync` returns.</span></span>

 <span data-ttu-id="73cb4-162">`client.GetStringAsync` Yöntemi bir görev için atanan bir dize döndürür `getStringTask` değişkeninde `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="73cb4-162">The `client.GetStringAsync` method returns a task of string that’s assigned to the `getStringTask` variable in `AccessTheWebAsync`.</span></span> <span data-ttu-id="73cb4-163">Örnek programdaki aşağıdaki satır çağrısını gösterir `client.GetStringAsync` atama.</span><span class="sxs-lookup"><span data-stu-id="73cb4-163">The following line in the example program shows the call to `client.GetStringAsync` and the assignment.</span></span>

```csharp
Task<string> getStringTask = client.GetStringAsync("https://msdn.microsoft.com");
```

 <span data-ttu-id="73cb4-164">Görevini, hedefi olarak düşünebilirsiniz `client.GetStringAsync` sonuçta gerçek bir dize oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="73cb4-164">You can think of the task as a promise by `client.GetStringAsync` to produce an actual string eventually.</span></span> <span data-ttu-id="73cb4-165">Bu arada, varsa `AccessTheWebAsync` dizeden bağımlı olmayan yapılacak çalışmaya sahipse `client.GetStringAsync`, iş devam edebilirsiniz ancak `client.GetStringAsync` bekler.</span><span class="sxs-lookup"><span data-stu-id="73cb4-165">In the meantime, if `AccessTheWebAsync` has work to do that doesn't depend on the promised string from `client.GetStringAsync`, that work can continue while  `client.GetStringAsync` waits.</span></span> <span data-ttu-id="73cb4-166">Örnekte, "Üç" etiketli, aşağıdaki çıktı satırları bağımsız iş yapma fırsatını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="73cb4-166">In the example, the following lines of output, which are labeled "THREE," represent the opportunity to do independent work</span></span>

```
THREE: Back in AccessTheWebAsync.
           Task getStringTask is started.
           About to await getStringTask & return a Task<int> to startButton_Click.
```

 <span data-ttu-id="73cb4-167">Aşağıdaki deyim ilerlemesini askıya alır `AccessTheWebAsync` olduğunda `getStringTask` beklenir.</span><span class="sxs-lookup"><span data-stu-id="73cb4-167">The following statement suspends progress in `AccessTheWebAsync` when `getStringTask` is awaited.</span></span>

```csharp
string urlContents = await getStringTask;
```

 <span data-ttu-id="73cb4-168">Aşağıdaki görüntüde, denetim akışı gösterilmektedir. `client.GetStringAsync` atamaya `getStringTask` ve oluşturulmasını `getStringTask` bir await işlecinin uygulamasına.</span><span class="sxs-lookup"><span data-stu-id="73cb4-168">The following image shows the flow of control from `client.GetStringAsync` to the assignment to `getStringTask` and from the creation of `getStringTask` to the application of an await operator.</span></span>

 <span data-ttu-id="73cb4-169">![ÜÇ adım](../../../../csharp/programming-guide/concepts/async/media/asynctrace-three.png "AsyncTrace üç")</span><span class="sxs-lookup"><span data-stu-id="73cb4-169">![Step THREE](../../../../csharp/programming-guide/concepts/async/media/asynctrace-three.png "AsyncTrace-Three")</span></span>

 <span data-ttu-id="73cb4-170">Await ifadesi askıya `AccessTheWebAsync` kadar `client.GetStringAsync` döndürür.</span><span class="sxs-lookup"><span data-stu-id="73cb4-170">The await expression suspends `AccessTheWebAsync` until `client.GetStringAsync` returns.</span></span> <span data-ttu-id="73cb4-171">Bu arada, Denetim çağırana döner `AccessTheWebAsync`, `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="73cb4-171">In the meantime, control returns to the caller of `AccessTheWebAsync`, `startButton_Click`.</span></span>

> [!NOTE]
> <span data-ttu-id="73cb4-172">Genellikle, bir zaman uyumsuz yöntem çağrısı hemen bekler.</span><span class="sxs-lookup"><span data-stu-id="73cb4-172">Typically, you await the call to an asynchronous method immediately.</span></span> <span data-ttu-id="73cb4-173">Örneğin, aşağıdaki atama oluşturan ve sonra bekleyen önceki kodun yerini alabilir `getStringTask`: `string urlContents = await client.GetStringAsync("https://msdn.microsoft.com");`</span><span class="sxs-lookup"><span data-stu-id="73cb4-173">For example, the following assignment could replace the previous code that creates and then awaits `getStringTask`: `string urlContents = await client.GetStringAsync("https://msdn.microsoft.com");`</span></span>
>
> <span data-ttu-id="73cb4-174">Bu konuda, await işleci, program aracılığıyla denetim akışını işaretleyen çıkış satırlarını yerleştirmek için daha sonra uygulanır.</span><span class="sxs-lookup"><span data-stu-id="73cb4-174">In this topic, the await operator is applied later to accommodate the output lines that mark the flow of control through the program.</span></span>

### <a name="step-four"></a><span data-ttu-id="73cb4-175">Dördüncü adım</span><span class="sxs-lookup"><span data-stu-id="73cb4-175">Step FOUR</span></span>

<span data-ttu-id="73cb4-176">Bildirilen dönüş türü `AccessTheWebAsync` olduğu `Task<int>`.</span><span class="sxs-lookup"><span data-stu-id="73cb4-176">The declared return type of `AccessTheWebAsync` is `Task<int>`.</span></span> <span data-ttu-id="73cb4-177">Bu nedenle, `AccessTheWebAsync` olan askıya alındı, bir tamsayı görevi döndürür `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="73cb4-177">Therefore, when `AccessTheWebAsync` is suspended, it returns a task of integer to `startButton_Click`.</span></span> <span data-ttu-id="73cb4-178">Döndürülen görevin olmadığını anlamanız gereken `getStringTask`.</span><span class="sxs-lookup"><span data-stu-id="73cb4-178">You should understand that the returned task isn’t `getStringTask`.</span></span> <span data-ttu-id="73cb4-179">Döndürülen görevin askıya alınmış yönteminde yapılması kalan temsil eden tamsayı, yeni bir görevdir `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="73cb4-179">The returned task is a new task of integer that represents what remains to be done in the suspended method, `AccessTheWebAsync`.</span></span> <span data-ttu-id="73cb4-180">Görev bir vaadidir `AccessTheWebAsync` görev tamamlandığında bir tamsayı üretmek için.</span><span class="sxs-lookup"><span data-stu-id="73cb4-180">The task is a promise from `AccessTheWebAsync` to produce an integer when the task is complete.</span></span>

<span data-ttu-id="73cb4-181">Bu görev için aşağıdaki deyimi atar `getLengthTask` değişkeni.</span><span class="sxs-lookup"><span data-stu-id="73cb4-181">The following statement assigns this task to the `getLengthTask` variable.</span></span>

```csharp
Task<int> getLengthTask = AccessTheWebAsync();
```

 <span data-ttu-id="73cb4-182">Olarak `AccessTheWebAsync`, `startButton_Click` zaman uyumsuz görev sonuçlarına bağlı olmayan çalışmalar ile devam edebilir (`getLengthTask`) kadar görev beklenir.</span><span class="sxs-lookup"><span data-stu-id="73cb4-182">As in `AccessTheWebAsync`, `startButton_Click` can continue with work that doesn’t depend on the results of the asynchronous task (`getLengthTask`) until the task is awaited.</span></span> <span data-ttu-id="73cb4-183">Aşağıdaki çıktı satırları bu işi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="73cb4-183">The following output lines represent that work.</span></span>

```
FOUR:  Back in startButton_Click.
           Task getLengthTask is started.
           About to await getLengthTask -- no caller to return to.
```

 <span data-ttu-id="73cb4-184">İlerlemenizi `startButton_Click` zaman askıya `getLengthTask` beklenir.</span><span class="sxs-lookup"><span data-stu-id="73cb4-184">Progress in `startButton_Click` is suspended when `getLengthTask` is awaited.</span></span> <span data-ttu-id="73cb4-185">Aşağıdaki atama deyimi askıya `startButton_Click` kadar `AccessTheWebAsync` tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="73cb4-185">The following assignment statement suspends `startButton_Click` until `AccessTheWebAsync` is complete.</span></span>

```csharp
int contentLength = await getLengthTask;
```

 <span data-ttu-id="73cb4-186">Aşağıdaki çizimde, oklar seçeneğindeki await ifadesine içinde denetim akışını gösterir. `AccessTheWebAsync` bir değer atamaya `getLengthTask`, normal işlem tarafından izlenen `startButton_Click` kadar `getLengthTask` beklenir.</span><span class="sxs-lookup"><span data-stu-id="73cb4-186">In the following illustration, the arrows show the flow of control from the await expression in `AccessTheWebAsync` to the assignment of a value to `getLengthTask`, followed by normal processing in `startButton_Click` until `getLengthTask` is awaited.</span></span>

 <span data-ttu-id="73cb4-187">![Dördüncü adım](../../../../csharp/programming-guide/concepts/async/media/asynctrace-four.png "AsyncTrace dört")</span><span class="sxs-lookup"><span data-stu-id="73cb4-187">![Step FOUR](../../../../csharp/programming-guide/concepts/async/media/asynctrace-four.png "AsyncTrace-FOUR")</span></span>

### <a name="step-five"></a><span data-ttu-id="73cb4-188">Beşinci adım</span><span class="sxs-lookup"><span data-stu-id="73cb4-188">Step FIVE</span></span>

<span data-ttu-id="73cb4-189">Zaman `client.GetStringAsync` işleme işleminin tamamlandığından emin sinyalleri `AccessTheWebAsync` askıda durumundan çıkarılır ve bekleme ifadesinin ötesine devam edebilir.</span><span class="sxs-lookup"><span data-stu-id="73cb4-189">When `client.GetStringAsync` signals that it’s complete, processing in `AccessTheWebAsync` is released from suspension and can continue past the await statement.</span></span> <span data-ttu-id="73cb4-190">Aşağıdaki çıktı satırları işlemin sürdürülmesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="73cb4-190">The following lines of output represent the resumption of processing.</span></span>

```
FIVE:  Back in AccessTheWebAsync.
           Task getStringTask is complete.
           Processing the return statement.
           Exiting from AccessTheWebAsync.
```

 <span data-ttu-id="73cb4-191">Return ifadesinin işleneni `urlContents.Length`, görevde depolanır, `AccessTheWebAsync` döndürür.</span><span class="sxs-lookup"><span data-stu-id="73cb4-191">The operand of the return statement, `urlContents.Length`, is stored in the task that  `AccessTheWebAsync` returns.</span></span> <span data-ttu-id="73cb4-192">Await ifadesi bu değeri alır. `getLengthTask` içinde `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="73cb4-192">The await expression retrieves that value from `getLengthTask` in `startButton_Click`.</span></span>

 <span data-ttu-id="73cb4-193">Aşağıdaki görüntüde, sonraki denetim aktarımı gösterilmektedir `client.GetStringAsync` (ve `getStringTask`) getirildiğinden.</span><span class="sxs-lookup"><span data-stu-id="73cb4-193">The following image shows the transfer of control after `client.GetStringAsync` (and `getStringTask`) are complete.</span></span>

 <span data-ttu-id="73cb4-194">![BEŞ adım](../../../../csharp/programming-guide/concepts/async/media/asynctrace-five.png "AsyncTrace beş")</span><span class="sxs-lookup"><span data-stu-id="73cb4-194">![Step FIVE](../../../../csharp/programming-guide/concepts/async/media/asynctrace-five.png "AsyncTrace-FIVE")</span></span>

 <span data-ttu-id="73cb4-195">`AccessTheWebAsync` çalıştırır ve denetim döner `startButton_Click`, tamamlanması bekleniyor.</span><span class="sxs-lookup"><span data-stu-id="73cb4-195">`AccessTheWebAsync` runs to completion, and control returns to `startButton_Click`, which is awaiting the completion.</span></span>

### <a name="step-six"></a><span data-ttu-id="73cb4-196">Altıncı adım</span><span class="sxs-lookup"><span data-stu-id="73cb4-196">Step SIX</span></span>

<span data-ttu-id="73cb4-197">Zaman `AccessTheWebAsync` tam işleme sinyalleri içindeki bekleme ifadesinin ötesine devam edebilir `startButton_Async`.</span><span class="sxs-lookup"><span data-stu-id="73cb4-197">When `AccessTheWebAsync` signals that it’s complete, processing can continue past the await statement in `startButton_Async`.</span></span> <span data-ttu-id="73cb4-198">Aslında, programın başka bir şey yapmak için vardır.</span><span class="sxs-lookup"><span data-stu-id="73cb4-198">In fact, the program has nothing more to do.</span></span>

<span data-ttu-id="73cb4-199">Aşağıdaki çıktı satırları içinde işlemin sürdürülmesini temsil etmektedir `startButton_Async`:</span><span class="sxs-lookup"><span data-stu-id="73cb4-199">The following lines of output represent the resumption of processing in `startButton_Async`:</span></span>

```
SIX:   Back in startButton_Click.
           Task getLengthTask is finished.
           Result from AccessTheWebAsync is stored in contentLength.
           About to display contentLength and exit.
```

 <span data-ttu-id="73cb4-200">Await ifadesi alır `getLengthTask` içindeki return deyiminin işleneni olan bir tamsayı değer `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="73cb4-200">The await expression retrieves from `getLengthTask` the integer value that’s the operand of the return statement in `AccessTheWebAsync`.</span></span> <span data-ttu-id="73cb4-201">Aşağıdaki deyim, bu değeri atar `contentLength` değişkeni.</span><span class="sxs-lookup"><span data-stu-id="73cb4-201">The following statement assigns that value to the `contentLength` variable.</span></span>

```csharp
int contentLength = await getLengthTask;
```

 <span data-ttu-id="73cb4-202">Aşağıdaki görüntüde kadar denetimin dönüşü gösterilmektedir `AccessTheWebAsync` için `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="73cb4-202">The following image shows the return of control from `AccessTheWebAsync` to `startButton_Click`.</span></span>

 <span data-ttu-id="73cb4-203">![ALTI adım](../../../../csharp/programming-guide/concepts/async/media/asynctrace-six.png "AsyncTrace altı")</span><span class="sxs-lookup"><span data-stu-id="73cb4-203">![Step SIX](../../../../csharp/programming-guide/concepts/async/media/asynctrace-six.png "AsyncTrace-SIX")</span></span>

## <a name="see-also"></a><span data-ttu-id="73cb4-204">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="73cb4-204">See also</span></span>

- [<span data-ttu-id="73cb4-205">Zaman uyumsuz programlama ile async ve await (C#)</span><span class="sxs-lookup"><span data-stu-id="73cb4-205">Asynchronous Programming with async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/index.md)
- [<span data-ttu-id="73cb4-206">Zaman uyumsuz dönüş türleri (C#)</span><span class="sxs-lookup"><span data-stu-id="73cb4-206">Async Return Types (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/async-return-types.md)
- [<span data-ttu-id="73cb4-207">İzlenecek yol: Zaman uyumsuz kullanarak Web'e erişme ve await (C#)</span><span class="sxs-lookup"><span data-stu-id="73cb4-207">Walkthrough: Accessing the Web by Using async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="73cb4-208">Zaman uyumsuz örneği: Denetim akışı zaman uyumsuz programlarda (C# ve Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="73cb4-208">Async Sample: Control Flow in Async Programs (C# and Visual Basic)</span></span>](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0)
