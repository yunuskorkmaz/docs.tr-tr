---
title: Zaman uyumsuz programlarda denetim akışı (C#)
description: Async ve await anahtar sözcüklerini kullanarak zaman uyumsuz programların nasıl yazılacağını ve bakımının yapıldığını anlamak için basit bir zaman uyumsuz C# programındaki denetim akışı hakkında bilgi edinin.
ms.date: 07/20/2015
ms.assetid: fc92b08b-fe1d-4d07-84ab-5192fafe06bb
ms.openlocfilehash: 3946db958466a9f9914a5fa7b37c0db3a64d4b3d
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925377"
---
# <a name="control-flow-in-async-programs-c"></a><span data-ttu-id="70dd7-103">Zaman uyumsuz programlarda denetim akışı (C#)</span><span class="sxs-lookup"><span data-stu-id="70dd7-103">Control flow in async programs (C#)</span></span>

<span data-ttu-id="70dd7-104">`async`Ve anahtar sözcüklerini kullanarak zaman uyumsuz programları daha kolay bir şekilde yazabilir ve koruyabilirsiniz `await` .</span><span class="sxs-lookup"><span data-stu-id="70dd7-104">You can write and maintain asynchronous programs more easily by using the `async` and `await` keywords.</span></span> <span data-ttu-id="70dd7-105">Ancak, programınızın nasıl çalıştığını anlamıyorsanız sonuçlar sizi şaşırtabilir.</span><span class="sxs-lookup"><span data-stu-id="70dd7-105">However, the results might surprise you if you don't understand how your program operates.</span></span> <span data-ttu-id="70dd7-106">Bu konu, denetim bir yöntemden diğerine ne zaman taşındığını ve her seferinde hangi bilgilerin aktarılacağını göstermek için basit bir zaman uyumsuz program aracılığıyla denetim akışını izler.</span><span class="sxs-lookup"><span data-stu-id="70dd7-106">This topic traces the flow of control through a simple async program to show you when control moves from one method to another and what information is transferred each time.</span></span>

<span data-ttu-id="70dd7-107">Genel olarak, [Async (C#)](../../../language-reference/keywords/async.md) değiştiricisiyle zaman uyumsuz kod içeren yöntemleri işaretlersiniz.</span><span class="sxs-lookup"><span data-stu-id="70dd7-107">In general, you mark methods that contain asynchronous code with the [async (C#)](../../../language-reference/keywords/async.md) modifier.</span></span> <span data-ttu-id="70dd7-108">Zaman uyumsuz değiştirici ile işaretlenmiş bir yöntemde, yöntemin, çağrılan zaman uyumsuz işlemin tamamlanmasını beklemek için bekleyeceği yeri belirtmek için [await (C#)](../../../language-reference/operators/await.md) işlecini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="70dd7-108">In a method that's marked with an async modifier, you can use an [await (C#)](../../../language-reference/operators/await.md) operator to specify where the method pauses to wait for a called asynchronous process to complete.</span></span> <span data-ttu-id="70dd7-109">Daha fazla bilgi için bkz. [Async ve await Ile zaman uyumsuz programlama (C#)](./index.md).</span><span class="sxs-lookup"><span data-stu-id="70dd7-109">For more information, see [Asynchronous Programming with async and await (C#)](./index.md).</span></span>

<span data-ttu-id="70dd7-110">Aşağıdaki örnek, belirtilen bir Web sitesinin içeriğini bir dize olarak indirmek ve dizenin uzunluğunu göstermek için zaman uyumsuz yöntemler kullanır.</span><span class="sxs-lookup"><span data-stu-id="70dd7-110">The following example uses async methods to download the contents of a specified website as a string and to display the length of the string.</span></span> <span data-ttu-id="70dd7-111">Örnek aşağıdaki iki yöntemi içerir.</span><span class="sxs-lookup"><span data-stu-id="70dd7-111">The example contains the following two methods.</span></span>

- <span data-ttu-id="70dd7-112">`startButton_Click`, sonucu çağırır `AccessTheWebAsync` ve görüntüler.</span><span class="sxs-lookup"><span data-stu-id="70dd7-112">`startButton_Click`, which calls `AccessTheWebAsync` and displays the result.</span></span>

- <span data-ttu-id="70dd7-113">`AccessTheWebAsync`, bir Web sitesinin içeriğini bir dize olarak indirir ve dizenin uzunluğunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="70dd7-113">`AccessTheWebAsync`, which downloads the contents of a website as a string and returns the length of the string.</span></span> <span data-ttu-id="70dd7-114">`AccessTheWebAsync`<xref:System.Net.Http.HttpClient>, içeriğini indirmek için zaman uyumsuz bir yöntem kullanır <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> .</span><span class="sxs-lookup"><span data-stu-id="70dd7-114">`AccessTheWebAsync` uses an asynchronous <xref:System.Net.Http.HttpClient> method, <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>, to download the contents.</span></span>

<span data-ttu-id="70dd7-115">Numaralandırılmış görüntüleme satırları programın nasıl çalıştığını anlamanıza yardımcı olmak ve işaretlenen her bir noktada ne olduğunu açıklamak için programın tamamında stratejik noktalarda görünür.</span><span class="sxs-lookup"><span data-stu-id="70dd7-115">Numbered display lines appear at strategic points throughout the program to help you understand how the program runs and to explain what happens at each point that is marked.</span></span> <span data-ttu-id="70dd7-116">Görüntüleme satırları "BIR"-"altı" olarak etiketlenir.</span><span class="sxs-lookup"><span data-stu-id="70dd7-116">The display lines are labeled "ONE" through "SIX."</span></span> <span data-ttu-id="70dd7-117">Etiketler, programın bu kod satırlarına ulaştığı sırayı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="70dd7-117">The labels represent the order in which the program reaches these lines of code.</span></span>

<span data-ttu-id="70dd7-118">Aşağıdaki kod programın bir ana hattını gösterir.</span><span class="sxs-lookup"><span data-stu-id="70dd7-118">The following code shows an outline of the program.</span></span>

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

<span data-ttu-id="70dd7-119">Etiketlenmiş konumların her biri, "BIR"-"ALTıDA", programın geçerli durumuyla ilgili bilgileri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="70dd7-119">Each of the labeled locations, "ONE" through "SIX," displays information about the current state of the program.</span></span> <span data-ttu-id="70dd7-120">Aşağıdaki çıktı üretilir:</span><span class="sxs-lookup"><span data-stu-id="70dd7-120">The following output is produced:</span></span>

```output
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

## <a name="set-up-the-program"></a><span data-ttu-id="70dd7-121">Programı ayarlama</span><span class="sxs-lookup"><span data-stu-id="70dd7-121">Set up the program</span></span>

<span data-ttu-id="70dd7-122">Bu konunun kullandığı kodu MSDN 'den indirebilirsiniz veya kendiniz oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="70dd7-122">You can download the code that this topic uses from MSDN, or you can build it yourself.</span></span>

> [!NOTE]
> <span data-ttu-id="70dd7-123">Örneği çalıştırmak için, bilgisayarınızda Visual Studio 2012 veya daha yeni bir sürümü ve .NET Framework 4,5 ya da daha yeni bir sürümü yüklü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="70dd7-123">To run the example, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>

### <a name="download-the-program"></a><span data-ttu-id="70dd7-124">Programı indir</span><span class="sxs-lookup"><span data-stu-id="70dd7-124">Download the program</span></span>

<span data-ttu-id="70dd7-125">Bu konu için uygulamayı [zaman uyumsuz örnek: zaman uyumsuz programlarda denetim akışı '](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0)ndan indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="70dd7-125">You can download the application for this topic from [Async Sample: Control Flow in Async Programs](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0).</span></span> <span data-ttu-id="70dd7-126">Aşağıdaki adımlar programı açın ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="70dd7-126">The following steps open and run the program.</span></span>

1. <span data-ttu-id="70dd7-127">İndirilen dosyayı sıkıştırmasını açın ve ardından Visual Studio 'Yu başlatın.</span><span class="sxs-lookup"><span data-stu-id="70dd7-127">Unzip the downloaded file, and then start Visual Studio.</span></span>

2. <span data-ttu-id="70dd7-128">Menü çubuğunda **Dosya**  >  **Aç**  >  **Proje/çözüm**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="70dd7-128">On the menu bar, choose **File** > **Open** > **Project/Solution**.</span></span>

3. <span data-ttu-id="70dd7-129">Sıkıştırılmış örnek kodu tutan klasöre gidin, çözüm (. sln) dosyasını açın ve ardından projeyi derlemek ve çalıştırmak için **F5** tuşunu seçin.</span><span class="sxs-lookup"><span data-stu-id="70dd7-129">Navigate to the folder that holds the unzipped sample code, open the solution (.sln) file, and then choose the **F5** key to build and run the project.</span></span>

### <a name="create-the-program-yourself"></a><span data-ttu-id="70dd7-130">Programı kendiniz oluşturun</span><span class="sxs-lookup"><span data-stu-id="70dd7-130">Create the program Yourself</span></span>

<span data-ttu-id="70dd7-131">Aşağıdaki Windows Presentation Foundation (WPF) projesi bu konunun kod örneğini içerir.</span><span class="sxs-lookup"><span data-stu-id="70dd7-131">The following Windows Presentation Foundation (WPF) project contains the code example for this topic.</span></span>

<span data-ttu-id="70dd7-132">Projeyi çalıştırmak için aşağıdaki adımları gerçekleştirin:</span><span class="sxs-lookup"><span data-stu-id="70dd7-132">To run the project, perform the following steps:</span></span>

1. <span data-ttu-id="70dd7-133">Visual Studio’yu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="70dd7-133">Start Visual Studio.</span></span>

2. <span data-ttu-id="70dd7-134">Menü çubuğunda **Dosya**  >  **Yeni**  >  **Proje**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="70dd7-134">On the menu bar, choose **File** > **New** > **Project**.</span></span>

     <span data-ttu-id="70dd7-135">**Yeni proje** iletişim kutusu açılır.</span><span class="sxs-lookup"><span data-stu-id="70dd7-135">The **New Project** dialog box opens.</span></span>

3. <span data-ttu-id="70dd7-136">**Yüklü**  >  **Visual C#**  >  **Windows Masaüstü** kategorisini seçin ve ardından proje şablonları listesinden **WPF uygulaması** ' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="70dd7-136">Choose the **Installed** > **Visual C#** > **Windows Desktop** category, and then choose **WPF App** from the list of project templates.</span></span>

4. <span data-ttu-id="70dd7-137">`AsyncTracer`Projenin adı olarak girin ve **Tamam** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="70dd7-137">Enter `AsyncTracer` as the name of the project, and then choose the **OK** button.</span></span>

     <span data-ttu-id="70dd7-138">Yeni proje **Çözüm Gezgini**görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="70dd7-138">The new project appears in **Solution Explorer**.</span></span>

5. <span data-ttu-id="70dd7-139">Visual Studio Code düzenleyicisinde **MainWindow. xaml** sekmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="70dd7-139">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>

     <span data-ttu-id="70dd7-140">Sekme görünür değilse, **Çözüm Gezgini**' de MainWindow. xaml için kısayol menüsünü açın ve **kodu görüntüle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="70dd7-140">If the tab isn’t visible, open the shortcut menu for MainWindow.xaml in **Solution Explorer**, and then choose **View Code**.</span></span>

6. <span data-ttu-id="70dd7-141">MainWindow. xaml ' nin **xaml** görünümünde, kodu aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="70dd7-141">In the **XAML** view of MainWindow.xaml, replace the code with the following code.</span></span>

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

     <span data-ttu-id="70dd7-142">Bir metin kutusu ve bir düğme içeren basit bir pencere, MainWindow. xaml **Tasarım** görünümünde görünür.</span><span class="sxs-lookup"><span data-stu-id="70dd7-142">A simple window that contains a text box and a button appears in the **Design** view of MainWindow.xaml.</span></span>

7. <span data-ttu-id="70dd7-143">İçin bir başvuru ekleyin <xref:System.Net.Http> .</span><span class="sxs-lookup"><span data-stu-id="70dd7-143">Add a reference for <xref:System.Net.Http>.</span></span>

8. <span data-ttu-id="70dd7-144">**Çözüm Gezgini**' de, MainWindow.xaml.cs için kısayol menüsünü açın ve **kodu görüntüle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="70dd7-144">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.cs, and then choose **View Code**.</span></span>

9. <span data-ttu-id="70dd7-145">MainWindow.xaml.cs ' de, kodu aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="70dd7-145">In MainWindow.xaml.cs, replace the code with the following code.</span></span>

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

10. <span data-ttu-id="70dd7-146">Programı çalıştırmak için **F5** tuşunu seçin ve sonra **Başlat** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="70dd7-146">Choose the **F5** key to run the program, and then choose the **Start** button.</span></span>

    <span data-ttu-id="70dd7-147">Aşağıdaki çıkış görüntülenir:</span><span class="sxs-lookup"><span data-stu-id="70dd7-147">The following output appears:</span></span>

    ```output
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

## <a name="trace-the-program"></a><span data-ttu-id="70dd7-148">Programı izleme</span><span class="sxs-lookup"><span data-stu-id="70dd7-148">Trace the program</span></span>

### <a name="steps-one-and-two"></a><span data-ttu-id="70dd7-149">Adım BIR ve ıkı</span><span class="sxs-lookup"><span data-stu-id="70dd7-149">Steps ONE and TWO</span></span>

<span data-ttu-id="70dd7-150">İlk iki görüntüleme satırı yolu çağrı olarak izler `startButton_Click` `AccessTheWebAsync` ve `AccessTheWebAsync` zaman uyumsuz <xref:System.Net.Http.HttpClient> yöntemi çağırır <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> .</span><span class="sxs-lookup"><span data-stu-id="70dd7-150">The first two display lines trace the path as `startButton_Click` calls `AccessTheWebAsync`, and `AccessTheWebAsync` calls the asynchronous <xref:System.Net.Http.HttpClient> method <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>.</span></span> <span data-ttu-id="70dd7-151">Aşağıdaki görüntüde yönteminden yöntemine yapılan çağrılar özetlenmektedir.</span><span class="sxs-lookup"><span data-stu-id="70dd7-151">The following image outlines the calls from method to method.</span></span>

<span data-ttu-id="70dd7-152">![Adım BIR ve ıkı](./media/asynctrace-onetwo.png "AsyncTrace-ONETWO")</span><span class="sxs-lookup"><span data-stu-id="70dd7-152">![Steps ONE and TWO](./media/asynctrace-onetwo.png "AsyncTrace-ONETWO")</span></span>

<span data-ttu-id="70dd7-153">Hem hem de öğesinin dönüş `AccessTheWebAsync` türü `client.GetStringAsync` <xref:System.Threading.Tasks.Task%601> .</span><span class="sxs-lookup"><span data-stu-id="70dd7-153">The return type of both `AccessTheWebAsync` and `client.GetStringAsync` is <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="70dd7-154">İçin `AccessTheWebAsync` , TResult bir tamsayıdır.</span><span class="sxs-lookup"><span data-stu-id="70dd7-154">For `AccessTheWebAsync`, TResult is an integer.</span></span> <span data-ttu-id="70dd7-155">İçin `GetStringAsync` , TResult bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="70dd7-155">For `GetStringAsync`, TResult is a string.</span></span> <span data-ttu-id="70dd7-156">Zaman uyumsuz yöntem dönüş türleri hakkında daha fazla bilgi için bkz. [Async Return Types (C#)](./async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="70dd7-156">For more information about async method return types, see [Async Return Types (C#)](./async-return-types.md).</span></span>

<span data-ttu-id="70dd7-157">Bir görev döndüren zaman uyumsuz yöntem, Denetim çağırana geri dönzaman bir görev örneği döndürür.</span><span class="sxs-lookup"><span data-stu-id="70dd7-157">A task-returning async method returns a task instance when control shifts back to the caller.</span></span> <span data-ttu-id="70dd7-158">`await`Çağrılan yöntemde bir işleçle karşılaşıldığında veya çağrılan yöntem sona erdiğinde, denetim zaman uyumsuz bir yöntemden çağırana döner.</span><span class="sxs-lookup"><span data-stu-id="70dd7-158">Control returns from an async method to its caller either when an `await` operator is encountered in the called method or when the called method ends.</span></span> <span data-ttu-id="70dd7-159">"Üç" ile "ALTıDAN" Etiketlenmiş görüntüleme satırları işlemin bu bölümünü izler.</span><span class="sxs-lookup"><span data-stu-id="70dd7-159">The display lines that are labeled "THREE" through "SIX" trace this part of the process.</span></span>

### <a name="step-three"></a><span data-ttu-id="70dd7-160">Üçüncü adım</span><span class="sxs-lookup"><span data-stu-id="70dd7-160">Step THREE</span></span>

<span data-ttu-id="70dd7-161">İçinde `AccessTheWebAsync` , zaman uyumsuz yöntemi <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> hedef Web sayfasının içeriğini indirmek için çağırılır.</span><span class="sxs-lookup"><span data-stu-id="70dd7-161">In `AccessTheWebAsync`, the asynchronous method <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> is called to download the contents of the target webpage.</span></span> <span data-ttu-id="70dd7-162">Denetim, ' den ' a döner `client.GetStringAsync` `AccessTheWebAsync` `client.GetStringAsync` .</span><span class="sxs-lookup"><span data-stu-id="70dd7-162">Control returns from `client.GetStringAsync` to `AccessTheWebAsync` when `client.GetStringAsync` returns.</span></span>

 <span data-ttu-id="70dd7-163">`client.GetStringAsync`Yöntemi, içindeki değişkenine atanan bir dize görevi döndürür `getStringTask` `AccessTheWebAsync` .</span><span class="sxs-lookup"><span data-stu-id="70dd7-163">The `client.GetStringAsync` method returns a task of string that’s assigned to the `getStringTask` variable in `AccessTheWebAsync`.</span></span> <span data-ttu-id="70dd7-164">Örnek programda aşağıdaki satır, ve atama için çağrıyı gösterir `client.GetStringAsync` .</span><span class="sxs-lookup"><span data-stu-id="70dd7-164">The following line in the example program shows the call to `client.GetStringAsync` and the assignment.</span></span>

```csharp
Task<string> getStringTask = client.GetStringAsync("https://msdn.microsoft.com");
```

 <span data-ttu-id="70dd7-165">Son olarak `client.GetStringAsync` gerçek bir dize oluşturmak için görevi bir Promise olarak düşünebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="70dd7-165">You can think of the task as a promise by `client.GetStringAsync` to produce an actual string eventually.</span></span> <span data-ttu-id="70dd7-166">Bu sırada, bu, ' de `AccessTheWebAsync` taahhüt edilen dizeye bağlı değilse `client.GetStringAsync` , bu iş, bekleme sırasında devam edebilir `client.GetStringAsync` .</span><span class="sxs-lookup"><span data-stu-id="70dd7-166">In the meantime, if `AccessTheWebAsync` has work to do that doesn't depend on the promised string from `client.GetStringAsync`, that work can continue while  `client.GetStringAsync` waits.</span></span> <span data-ttu-id="70dd7-167">Örnekte, "üç" olarak etiketlenen aşağıdaki çıktı satırları, bağımsız iş yapmak için fırsatı temsil eder</span><span class="sxs-lookup"><span data-stu-id="70dd7-167">In the example, the following lines of output, which are labeled "THREE," represent the opportunity to do independent work</span></span>

```output
THREE: Back in AccessTheWebAsync.
           Task getStringTask is started.
           About to await getStringTask & return a Task<int> to startButton_Click.
```

 <span data-ttu-id="70dd7-168">Aşağıdaki ifade, `AccessTheWebAsync` ne zaman beklediğinde ' de ilerlemeyi askıya alır `getStringTask` .</span><span class="sxs-lookup"><span data-stu-id="70dd7-168">The following statement suspends progress in `AccessTheWebAsync` when `getStringTask` is awaited.</span></span>

```csharp
string urlContents = await getStringTask;
```

 <span data-ttu-id="70dd7-169">Aşağıdaki görüntüde denetim akışını, `client.GetStringAsync` `getStringTask` `getStringTask` bir await işlecinin uygulamasına ve oluşturma işleminden öğesine kadar gösterir.</span><span class="sxs-lookup"><span data-stu-id="70dd7-169">The following image shows the flow of control from `client.GetStringAsync` to the assignment to `getStringTask` and from the creation of `getStringTask` to the application of an await operator.</span></span>

 <span data-ttu-id="70dd7-170">![Üçüncü adım](./media/asynctrace-three.png "AsyncTrace-üç")</span><span class="sxs-lookup"><span data-stu-id="70dd7-170">![Step THREE](./media/asynctrace-three.png "AsyncTrace-Three")</span></span>

 <span data-ttu-id="70dd7-171">Await ifadesi `AccessTheWebAsync` dönüşene kadar askıya alır `client.GetStringAsync` .</span><span class="sxs-lookup"><span data-stu-id="70dd7-171">The await expression suspends `AccessTheWebAsync` until `client.GetStringAsync` returns.</span></span> <span data-ttu-id="70dd7-172">Bu sırada denetim, ' ın çağıranına döner `AccessTheWebAsync` `startButton_Click` .</span><span class="sxs-lookup"><span data-stu-id="70dd7-172">In the meantime, control returns to the caller of `AccessTheWebAsync`, `startButton_Click`.</span></span>

> [!NOTE]
> <span data-ttu-id="70dd7-173">Genellikle, zaman uyumsuz bir yöntem çağrısını hemen bekleolursunuz.</span><span class="sxs-lookup"><span data-stu-id="70dd7-173">Typically, you await the call to an asynchronous method immediately.</span></span> <span data-ttu-id="70dd7-174">Örneğin, aşağıdaki atama, oluşturan ve daha sonra bekleyen önceki kodun yerini alır `getStringTask` :`string urlContents = await client.GetStringAsync("https://msdn.microsoft.com");`</span><span class="sxs-lookup"><span data-stu-id="70dd7-174">For example, the following assignment could replace the previous code that creates and then awaits `getStringTask`: `string urlContents = await client.GetStringAsync("https://msdn.microsoft.com");`</span></span>
>
> <span data-ttu-id="70dd7-175">Bu konuda, Await işleci daha sonra Denetim akışını program aracılığıyla işaretleyen çıkış satırlarına uyum sağlayacak şekilde uygulanır.</span><span class="sxs-lookup"><span data-stu-id="70dd7-175">In this topic, the await operator is applied later to accommodate the output lines that mark the flow of control through the program.</span></span>

### <a name="step-four"></a><span data-ttu-id="70dd7-176">4. adım</span><span class="sxs-lookup"><span data-stu-id="70dd7-176">Step FOUR</span></span>

<span data-ttu-id="70dd7-177">Tarafından belirtilen dönüş türü `AccessTheWebAsync` `Task<int>` .</span><span class="sxs-lookup"><span data-stu-id="70dd7-177">The declared return type of `AccessTheWebAsync` is `Task<int>`.</span></span> <span data-ttu-id="70dd7-178">Bu nedenle, `AccessTheWebAsync` askıya alındığında, için bir tamsayı görevi döndürür `startButton_Click` .</span><span class="sxs-lookup"><span data-stu-id="70dd7-178">Therefore, when `AccessTheWebAsync` is suspended, it returns a task of integer to `startButton_Click`.</span></span> <span data-ttu-id="70dd7-179">Döndürülen görevin olmadığını anlamalısınız `getStringTask` .</span><span class="sxs-lookup"><span data-stu-id="70dd7-179">You should understand that the returned task isn’t `getStringTask`.</span></span> <span data-ttu-id="70dd7-180">Döndürülen görev, askıya alınan yöntemde ne yapılması gerektiğini temsil eden yeni bir tamsayı görevi `AccessTheWebAsync` .</span><span class="sxs-lookup"><span data-stu-id="70dd7-180">The returned task is a new task of integer that represents what remains to be done in the suspended method, `AccessTheWebAsync`.</span></span> <span data-ttu-id="70dd7-181">Görev `AccessTheWebAsync` tamamlandığında bir tamsayı üretmek için görevi bir taahhüddir.</span><span class="sxs-lookup"><span data-stu-id="70dd7-181">The task is a promise from `AccessTheWebAsync` to produce an integer when the task is complete.</span></span>

<span data-ttu-id="70dd7-182">Aşağıdaki ifade bu görevi `getLengthTask` değişkenine atar.</span><span class="sxs-lookup"><span data-stu-id="70dd7-182">The following statement assigns this task to the `getLengthTask` variable.</span></span>

```csharp
Task<int> getLengthTask = AccessTheWebAsync();
```

 <span data-ttu-id="70dd7-183">' De olduğu gibi `AccessTheWebAsync` , `startButton_Click` `getLengthTask` görev beklenene kadar zaman uyumsuz görevin () sonuçlarına bağlı olmayan çalışmaya devam edebilir.</span><span class="sxs-lookup"><span data-stu-id="70dd7-183">As in `AccessTheWebAsync`, `startButton_Click` can continue with work that doesn’t depend on the results of the asynchronous task (`getLengthTask`) until the task is awaited.</span></span> <span data-ttu-id="70dd7-184">Aşağıdaki çıktı satırları bu işi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="70dd7-184">The following output lines represent that work.</span></span>

```output
FOUR:  Back in startButton_Click.
           Task getLengthTask is started.
           About to await getLengthTask -- no caller to return to.
```

 <span data-ttu-id="70dd7-185">İlerleme durumu `startButton_Click` `getLengthTask` , beklediğinde askıya alınır.</span><span class="sxs-lookup"><span data-stu-id="70dd7-185">Progress in `startButton_Click` is suspended when `getLengthTask` is awaited.</span></span> <span data-ttu-id="70dd7-186">Aşağıdaki atama açıklaması `startButton_Click` tamamlanana kadar askıya `AccessTheWebAsync` alınır.</span><span class="sxs-lookup"><span data-stu-id="70dd7-186">The following assignment statement suspends `startButton_Click` until `AccessTheWebAsync` is complete.</span></span>

```csharp
int contentLength = await getLengthTask;
```

 <span data-ttu-id="70dd7-187">Aşağıdaki çizimde, oklar bir değerin atanması için içindeki Await ifadesinden denetim akışını gösterir `AccessTheWebAsync` `getLengthTask` ve ardından `startButton_Click` beklenene kadar normal işleme gelir `getLengthTask` .</span><span class="sxs-lookup"><span data-stu-id="70dd7-187">In the following illustration, the arrows show the flow of control from the await expression in `AccessTheWebAsync` to the assignment of a value to `getLengthTask`, followed by normal processing in `startButton_Click` until `getLengthTask` is awaited.</span></span>

 <span data-ttu-id="70dd7-188">![4. adım](./media/asynctrace-four.png "AsyncTrace-dört")</span><span class="sxs-lookup"><span data-stu-id="70dd7-188">![Step FOUR](./media/asynctrace-four.png "AsyncTrace-FOUR")</span></span>

### <a name="step-five"></a><span data-ttu-id="70dd7-189">5. adım</span><span class="sxs-lookup"><span data-stu-id="70dd7-189">Step FIVE</span></span>

<span data-ttu-id="70dd7-190">`client.GetStringAsync`İşlemin tamamlandığını işaret ederse, içindeki işleme askıya alma `AccessTheWebAsync` işleminden serbest bırakılır ve await ifadesinin ötesinde devam edebilir.</span><span class="sxs-lookup"><span data-stu-id="70dd7-190">When `client.GetStringAsync` signals that it’s complete, processing in `AccessTheWebAsync` is released from suspension and can continue past the await statement.</span></span> <span data-ttu-id="70dd7-191">Aşağıdaki çıktı satırları işleme sürdürme temsil eder.</span><span class="sxs-lookup"><span data-stu-id="70dd7-191">The following lines of output represent the resumption of processing.</span></span>

```output
FIVE:  Back in AccessTheWebAsync.
           Task getStringTask is complete.
           Processing the return statement.
           Exiting from AccessTheWebAsync.
```

 <span data-ttu-id="70dd7-192">Return ifadesinin işleneni, `urlContents.Length` döndüren görevde saklanır `AccessTheWebAsync` .</span><span class="sxs-lookup"><span data-stu-id="70dd7-192">The operand of the return statement, `urlContents.Length`, is stored in the task that  `AccessTheWebAsync` returns.</span></span> <span data-ttu-id="70dd7-193">Await ifadesi bu değeri içindeki öğesinden alır `getLengthTask` `startButton_Click` .</span><span class="sxs-lookup"><span data-stu-id="70dd7-193">The await expression retrieves that value from `getLengthTask` in `startButton_Click`.</span></span>

 <span data-ttu-id="70dd7-194">Aşağıdaki görüntüde (ve) sonra denetimin aktarımı gösterilmektedir `client.GetStringAsync` `getStringTask` .</span><span class="sxs-lookup"><span data-stu-id="70dd7-194">The following image shows the transfer of control after `client.GetStringAsync` (and `getStringTask`) are complete.</span></span>

 <span data-ttu-id="70dd7-195">![5. adım](./media/asynctrace-five.png "AsyncTrace-beş")</span><span class="sxs-lookup"><span data-stu-id="70dd7-195">![Step FIVE](./media/asynctrace-five.png "AsyncTrace-FIVE")</span></span>

 <span data-ttu-id="70dd7-196">`AccessTheWebAsync`tamamlandı olarak çalışır ve denetimi ' a döner, `startButton_Click` Bu da tamamlamayı bekliyor.</span><span class="sxs-lookup"><span data-stu-id="70dd7-196">`AccessTheWebAsync` runs to completion, and control returns to `startButton_Click`, which is awaiting the completion.</span></span>

### <a name="step-six"></a><span data-ttu-id="70dd7-197">Altı adım</span><span class="sxs-lookup"><span data-stu-id="70dd7-197">Step SIX</span></span>

<span data-ttu-id="70dd7-198">`AccessTheWebAsync`İşlemin tamamlandığını işaret ederse, işleme ' de await ifadesinin ötesinde devam edebilir `startButton_Async` .</span><span class="sxs-lookup"><span data-stu-id="70dd7-198">When `AccessTheWebAsync` signals that it’s complete, processing can continue past the await statement in `startButton_Async`.</span></span> <span data-ttu-id="70dd7-199">Aslında programın daha fazla şey yoktur.</span><span class="sxs-lookup"><span data-stu-id="70dd7-199">In fact, the program has nothing more to do.</span></span>

<span data-ttu-id="70dd7-200">Aşağıdaki çıktı satırları içinde işleme sürdürme temsil eder `startButton_Async` :</span><span class="sxs-lookup"><span data-stu-id="70dd7-200">The following lines of output represent the resumption of processing in `startButton_Async`:</span></span>

```output
SIX:   Back in startButton_Click.
           Task getLengthTask is finished.
           Result from AccessTheWebAsync is stored in contentLength.
           About to display contentLength and exit.
```

 <span data-ttu-id="70dd7-201">Await ifadesi `getLengthTask` ' de return deyiminin işleneni olan Integer değerinden alır `AccessTheWebAsync` .</span><span class="sxs-lookup"><span data-stu-id="70dd7-201">The await expression retrieves from `getLengthTask` the integer value that’s the operand of the return statement in `AccessTheWebAsync`.</span></span> <span data-ttu-id="70dd7-202">Aşağıdaki ifade bu değeri `contentLength` değişkenine atar.</span><span class="sxs-lookup"><span data-stu-id="70dd7-202">The following statement assigns that value to the `contentLength` variable.</span></span>

```csharp
int contentLength = await getLengthTask;
```

 <span data-ttu-id="70dd7-203">Aşağıdaki görüntüde ' den ' e denetim dönüşü gösterilmektedir `AccessTheWebAsync` `startButton_Click` .</span><span class="sxs-lookup"><span data-stu-id="70dd7-203">The following image shows the return of control from `AccessTheWebAsync` to `startButton_Click`.</span></span>

 <span data-ttu-id="70dd7-204">![Altı adım](./media/asynctrace-six.png "AsyncTrace-altı")</span><span class="sxs-lookup"><span data-stu-id="70dd7-204">![Step SIX](./media/asynctrace-six.png "AsyncTrace-SIX")</span></span>

## <a name="see-also"></a><span data-ttu-id="70dd7-205">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="70dd7-205">See also</span></span>

- [<span data-ttu-id="70dd7-206">Async ve await ile zaman uyumsuz programlama (C#)</span><span class="sxs-lookup"><span data-stu-id="70dd7-206">Asynchronous Programming with async and await (C#)</span></span>](./index.md)
- [<span data-ttu-id="70dd7-207">Zaman uyumsuz dönüş türleri (C#)</span><span class="sxs-lookup"><span data-stu-id="70dd7-207">Async Return Types (C#)</span></span>](./async-return-types.md)
- [<span data-ttu-id="70dd7-208">İzlenecek yol: Async ve await kullanarak Web 'e erişme (C#)</span><span class="sxs-lookup"><span data-stu-id="70dd7-208">Walkthrough: Accessing the Web by Using async and await (C#)</span></span>](./walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="70dd7-209">Async örneği: zaman uyumsuz programlarda denetim akışı (C# ve Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="70dd7-209">Async Sample: Control Flow in Async Programs (C# and Visual Basic)</span></span>](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0)
