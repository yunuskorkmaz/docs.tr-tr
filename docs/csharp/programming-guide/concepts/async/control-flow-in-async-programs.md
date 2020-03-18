---
title: Async Programlarında Kontrol Akışı (C#)
ms.date: 07/20/2015
ms.assetid: fc92b08b-fe1d-4d07-84ab-5192fafe06bb
ms.openlocfilehash: 99f80a86f14179c5f270064a9f96e35f8611ef13
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "70204448"
---
# <a name="control-flow-in-async-programs-c"></a><span data-ttu-id="44f37-102">Async programlarında kontrol akışı (C#)</span><span class="sxs-lookup"><span data-stu-id="44f37-102">Control flow in async programs (C#)</span></span>

<span data-ttu-id="44f37-103">Anahtar kelimeleri kullanarak eşzamanlı programları daha kolay `async` yazabilir `await` ve sürdürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="44f37-103">You can write and maintain asynchronous programs more easily by using the `async` and `await` keywords.</span></span> <span data-ttu-id="44f37-104">Ancak, programınızın nasıl çalıştığını anlamazsanız sonuçlar sizi şaşırtabilir.</span><span class="sxs-lookup"><span data-stu-id="44f37-104">However, the results might surprise you if you don't understand how your program operates.</span></span> <span data-ttu-id="44f37-105">Bu konu, denetimin bir yöntemden diğerine ne zaman taşındığını ve her seferinde hangi bilgilerin aktarıldığını göstermek için basit bir async programı aracılığıyla denetim akışını izler.</span><span class="sxs-lookup"><span data-stu-id="44f37-105">This topic traces the flow of control through a simple async program to show you when control moves from one method to another and what information is transferred each time.</span></span>

<span data-ttu-id="44f37-106">Genel olarak, [async (C#)](../../../language-reference/keywords/async.md) değiştirici ile asynchronous kodu içeren yöntemleri işaretlersiniz.</span><span class="sxs-lookup"><span data-stu-id="44f37-106">In general, you mark methods that contain asynchronous code with the [async (C#)](../../../language-reference/keywords/async.md) modifier.</span></span> <span data-ttu-id="44f37-107">Async değiştirici ile işaretlenmiş bir yöntemde, yöntemin tamamlanmasını beklemek için nerede duraklatılır söyleniyor belirtmek için bir [bekleme (C#)](../../../language-reference/operators/await.md) işleci kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="44f37-107">In a method that's marked with an async modifier, you can use an [await (C#)](../../../language-reference/operators/await.md) operator to specify where the method pauses to wait for a called asynchronous process to complete.</span></span> <span data-ttu-id="44f37-108">Daha fazla bilgi için, [async ile Asynchronous Programming bakın ve bekliyor (C#)](./index.md).</span><span class="sxs-lookup"><span data-stu-id="44f37-108">For more information, see [Asynchronous Programming with async and await (C#)](./index.md).</span></span>

<span data-ttu-id="44f37-109">Aşağıdaki örnek, belirli bir web sitesinin içeriğini dize olarak indirmek ve dize uzunluğunu görüntülemek için async yöntemlerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="44f37-109">The following example uses async methods to download the contents of a specified website as a string and to display the length of the string.</span></span> <span data-ttu-id="44f37-110">Örnek, aşağıdaki iki yöntemi içerir.</span><span class="sxs-lookup"><span data-stu-id="44f37-110">The example contains the following two methods.</span></span>

- <span data-ttu-id="44f37-111">`startButton_Click`, sonucu `AccessTheWebAsync` arar ve görüntüler.</span><span class="sxs-lookup"><span data-stu-id="44f37-111">`startButton_Click`, which calls `AccessTheWebAsync` and displays the result.</span></span>

- <span data-ttu-id="44f37-112">`AccessTheWebAsync`, bir web sitesinin içeriğini dize olarak indirir ve dize uzunluğunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="44f37-112">`AccessTheWebAsync`, which downloads the contents of a website as a string and returns the length of the string.</span></span> <span data-ttu-id="44f37-113">`AccessTheWebAsync`içeriğini indirmek için <xref:System.Net.Http.HttpClient> bir <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>eşzamanlı yöntem kullanır.</span><span class="sxs-lookup"><span data-stu-id="44f37-113">`AccessTheWebAsync` uses an asynchronous <xref:System.Net.Http.HttpClient> method, <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>, to download the contents.</span></span>

<span data-ttu-id="44f37-114">Program boyunca stratejik noktalarda numaralanmış ekran çizgileri görünür ve programın nasıl çalıştığını anlamanıza ve işaretlenen her noktada neler olduğunu açıklamanıza yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="44f37-114">Numbered display lines appear at strategic points throughout the program to help you understand how the program runs and to explain what happens at each point that is marked.</span></span> <span data-ttu-id="44f37-115">Ekran çizgileri "Bİr" ile "ALTI" arasında etiketlenir.</span><span class="sxs-lookup"><span data-stu-id="44f37-115">The display lines are labeled "ONE" through "SIX."</span></span> <span data-ttu-id="44f37-116">Etiketler, programın bu kod satırlarına ulaşma sırasını temsil ediyor.</span><span class="sxs-lookup"><span data-stu-id="44f37-116">The labels represent the order in which the program reaches these lines of code.</span></span>

<span data-ttu-id="44f37-117">Aşağıdaki kod, programın anahatlarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="44f37-117">The following code shows an outline of the program.</span></span>

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

<span data-ttu-id="44f37-118">Etiketli konumların her biri, "BİR" ile "ALTI" arasında, programın geçerli durumu hakkında bilgi görüntüler.</span><span class="sxs-lookup"><span data-stu-id="44f37-118">Each of the labeled locations, "ONE" through "SIX," displays information about the current state of the program.</span></span> <span data-ttu-id="44f37-119">Aşağıdaki çıktı üretilir:</span><span class="sxs-lookup"><span data-stu-id="44f37-119">The following output is produced:</span></span>

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

## <a name="set-up-the-program"></a><span data-ttu-id="44f37-120">Programı ayarlama</span><span class="sxs-lookup"><span data-stu-id="44f37-120">Set up the program</span></span>

<span data-ttu-id="44f37-121">Bu konunun kullandığı kodu MSDN'den indirebilir veya kendiniz oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="44f37-121">You can download the code that this topic uses from MSDN, or you can build it yourself.</span></span>

> [!NOTE]
> <span data-ttu-id="44f37-122">Örneği çalıştırmak için Visual Studio 2012 veya daha yeni ve .NET Framework 4.5 veya daha yeni bilgisayarınıza yüklü olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="44f37-122">To run the example, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>

### <a name="download-the-program"></a><span data-ttu-id="44f37-123">Programı indirin</span><span class="sxs-lookup"><span data-stu-id="44f37-123">Download the program</span></span>

<span data-ttu-id="44f37-124">Bu konu yla ilgili uygulamayı [Async Sample: Control Flow in Async Programs'dan](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0)indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="44f37-124">You can download the application for this topic from [Async Sample: Control Flow in Async Programs](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0).</span></span> <span data-ttu-id="44f37-125">Aşağıdaki adımlar programı açın ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="44f37-125">The following steps open and run the program.</span></span>

1. <span data-ttu-id="44f37-126">İndirilen dosyanın zip'ini açın ve Ardından Visual Studio'yu başlatın.</span><span class="sxs-lookup"><span data-stu-id="44f37-126">Unzip the downloaded file, and then start Visual Studio.</span></span>

2. <span data-ttu-id="44f37-127">Menü çubuğunda **Dosya** > **Aç** > **Projesi/Çözümü'nü**seçin.</span><span class="sxs-lookup"><span data-stu-id="44f37-127">On the menu bar, choose **File** > **Open** > **Project/Solution**.</span></span>

3. <span data-ttu-id="44f37-128">Sıkıştırılmamış örnek kodu tutan klasöre gidin, çözüm (.sln) dosyasını açın ve ardından projeyi oluşturmak ve çalıştırmak için **F5** tuşunu seçin.</span><span class="sxs-lookup"><span data-stu-id="44f37-128">Navigate to the folder that holds the unzipped sample code, open the solution (.sln) file, and then choose the **F5** key to build and run the project.</span></span>

### <a name="create-the-program-yourself"></a><span data-ttu-id="44f37-129">Programı Kendiniz oluşturun</span><span class="sxs-lookup"><span data-stu-id="44f37-129">Create the program Yourself</span></span>

<span data-ttu-id="44f37-130">Aşağıdaki Windows Sunu Temeli (WPF) projesi, bu konu için kod örneğini içerir.</span><span class="sxs-lookup"><span data-stu-id="44f37-130">The following Windows Presentation Foundation (WPF) project contains the code example for this topic.</span></span>

<span data-ttu-id="44f37-131">Projeyi çalıştırmak için aşağıdaki adımları gerçekleştirin:</span><span class="sxs-lookup"><span data-stu-id="44f37-131">To run the project, perform the following steps:</span></span>

1. <span data-ttu-id="44f37-132">Visual Studio’yu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="44f37-132">Start Visual Studio.</span></span>

2. <span data-ttu-id="44f37-133">Menü çubuğunda**Yeni** > **Proje** **yi seçin.** > </span><span class="sxs-lookup"><span data-stu-id="44f37-133">On the menu bar, choose **File** > **New** > **Project**.</span></span>

     <span data-ttu-id="44f37-134">**Yeni Proje** iletişim kutusu açılır.</span><span class="sxs-lookup"><span data-stu-id="44f37-134">The **New Project** dialog box opens.</span></span>

3. <span data-ttu-id="44f37-135">**Yüklü** > **Görsel C#** > **Windows Masaüstü** kategorisini seçin ve ardından proje şablonları listesinden **WPF Uygulamasını** seçin.</span><span class="sxs-lookup"><span data-stu-id="44f37-135">Choose the **Installed** > **Visual C#** > **Windows Desktop** category, and then choose **WPF App** from the list of project templates.</span></span>

4. <span data-ttu-id="44f37-136">Projenin `AsyncTracer` adı olarak girin ve sonra **Tamam** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="44f37-136">Enter `AsyncTracer` as the name of the project, and then choose the **OK** button.</span></span>

     <span data-ttu-id="44f37-137">Yeni proje Çözüm **Gezgini'nde**görünür.</span><span class="sxs-lookup"><span data-stu-id="44f37-137">The new project appears in **Solution Explorer**.</span></span>

5. <span data-ttu-id="44f37-138">Visual Studio Code Editor'da **MainWindow.xaml** sekmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="44f37-138">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>

     <span data-ttu-id="44f37-139">Sekme görünmüyorsa, **Solution Explorer'da**MainWindow.xaml için kısayol menüsünü açın ve ardından **Kodu Görüntüle'yi**seçin.</span><span class="sxs-lookup"><span data-stu-id="44f37-139">If the tab isn’t visible, open the shortcut menu for MainWindow.xaml in **Solution Explorer**, and then choose **View Code**.</span></span>

6. <span data-ttu-id="44f37-140">MainWindow.xaml'ın **XAML** görünümünde kodu aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="44f37-140">In the **XAML** view of MainWindow.xaml, replace the code with the following code.</span></span>

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

     <span data-ttu-id="44f37-141">MainWindow.xaml'ın **Tasarım** görünümünde metin kutusu ve düğme içeren basit bir pencere görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="44f37-141">A simple window that contains a text box and a button appears in the **Design** view of MainWindow.xaml.</span></span>

7. <span data-ttu-id="44f37-142">Için <xref:System.Net.Http>bir başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="44f37-142">Add a reference for <xref:System.Net.Http>.</span></span>

8. <span data-ttu-id="44f37-143">**Çözüm Gezgini'nde,** MainWindow.xaml.cs için kısayol menüsünü açın ve ardından **Kodu Görüntüle'yi**seçin.</span><span class="sxs-lookup"><span data-stu-id="44f37-143">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.cs, and then choose **View Code**.</span></span>

9. <span data-ttu-id="44f37-144">MainWindow.xaml.cs kodu aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="44f37-144">In MainWindow.xaml.cs, replace the code with the following code.</span></span>

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

10. <span data-ttu-id="44f37-145">Programı çalıştırmak için **F5** tuşunu seçin ve ardından **Başlat** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="44f37-145">Choose the **F5** key to run the program, and then choose the **Start** button.</span></span>

    <span data-ttu-id="44f37-146">Şu çıktı görünür:</span><span class="sxs-lookup"><span data-stu-id="44f37-146">The following output appears:</span></span>

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

## <a name="trace-the-program"></a><span data-ttu-id="44f37-147">Programı izleme</span><span class="sxs-lookup"><span data-stu-id="44f37-147">Trace the program</span></span>

### <a name="steps-one-and-two"></a><span data-ttu-id="44f37-148">Bir ve İkİ Adım</span><span class="sxs-lookup"><span data-stu-id="44f37-148">Steps ONE and TWO</span></span>

<span data-ttu-id="44f37-149">İlk iki görüntü satırı yolu `startButton_Click` `AccessTheWebAsync`çağrı `AccessTheWebAsync` olarak izler ve <xref:System.Net.Http.HttpClient> eşsenkronize yöntemi <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>çağırır.</span><span class="sxs-lookup"><span data-stu-id="44f37-149">The first two display lines trace the path as `startButton_Click` calls `AccessTheWebAsync`, and `AccessTheWebAsync` calls the asynchronous <xref:System.Net.Http.HttpClient> method <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>.</span></span> <span data-ttu-id="44f37-150">Aşağıdaki resimde yöntemden yönteme çağrılar özetleniyor.</span><span class="sxs-lookup"><span data-stu-id="44f37-150">The following image outlines the calls from method to method.</span></span>

<span data-ttu-id="44f37-151">![Bir ve İkİ Adım](./media/asynctrace-onetwo.png "AsyncTrace-ONETWO")</span><span class="sxs-lookup"><span data-stu-id="44f37-151">![Steps ONE and TWO](./media/asynctrace-onetwo.png "AsyncTrace-ONETWO")</span></span>

<span data-ttu-id="44f37-152">Her ikisinin `AccessTheWebAsync` de `client.GetStringAsync` <xref:System.Threading.Tasks.Task%601>dönüş türü ve .</span><span class="sxs-lookup"><span data-stu-id="44f37-152">The return type of both `AccessTheWebAsync` and `client.GetStringAsync` is <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="44f37-153">Için `AccessTheWebAsync`, TResult bir sayıdır.</span><span class="sxs-lookup"><span data-stu-id="44f37-153">For `AccessTheWebAsync`, TResult is an integer.</span></span> <span data-ttu-id="44f37-154">Için `GetStringAsync`, TResult bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="44f37-154">For `GetStringAsync`, TResult is a string.</span></span> <span data-ttu-id="44f37-155">Async yöntemi iade türleri hakkında daha fazla bilgi [için, Bkz. Async Return Types (C#)](./async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="44f37-155">For more information about async method return types, see [Async Return Types (C#)](./async-return-types.md).</span></span>

<span data-ttu-id="44f37-156">Görev döndüren async yöntemi, denetim arayana geri kaydığında bir görev örneği döndürür.</span><span class="sxs-lookup"><span data-stu-id="44f37-156">A task-returning async method returns a task instance when control shifts back to the caller.</span></span> <span data-ttu-id="44f37-157">Denetim, çağrılan yöntemde bir `await` işleçle karşılaşıldığında veya çağrılan yöntem sona erdiğinde async yönteminden arayana geri döner.</span><span class="sxs-lookup"><span data-stu-id="44f37-157">Control returns from an async method to its caller either when an `await` operator is encountered in the called method or when the called method ends.</span></span> <span data-ttu-id="44f37-158">"ALTI" ile "ÜÇ" etiketli ekran çizgileri işlemin bu bölümünü izler.</span><span class="sxs-lookup"><span data-stu-id="44f37-158">The display lines that are labeled "THREE" through "SIX" trace this part of the process.</span></span>

### <a name="step-three"></a><span data-ttu-id="44f37-159">Üçüncü Adım</span><span class="sxs-lookup"><span data-stu-id="44f37-159">Step THREE</span></span>

<span data-ttu-id="44f37-160">, `AccessTheWebAsync`asynchronous yöntemi <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> hedef web sayfasının içeriğini indirmek için denir.</span><span class="sxs-lookup"><span data-stu-id="44f37-160">In `AccessTheWebAsync`, the asynchronous method <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> is called to download the contents of the target webpage.</span></span> <span data-ttu-id="44f37-161">Denetim döndüğünden `AccessTheWebAsync` `client.GetStringAsync` ne zaman ait sayılsın. `client.GetStringAsync`</span><span class="sxs-lookup"><span data-stu-id="44f37-161">Control returns from `client.GetStringAsync` to `AccessTheWebAsync` when `client.GetStringAsync` returns.</span></span>

 <span data-ttu-id="44f37-162">Yöntem, `client.GetStringAsync` `getStringTask` `AccessTheWebAsync`'deki değişkene atanan dize görevini döndürür</span><span class="sxs-lookup"><span data-stu-id="44f37-162">The `client.GetStringAsync` method returns a task of string that’s assigned to the `getStringTask` variable in `AccessTheWebAsync`.</span></span> <span data-ttu-id="44f37-163">Örnek programdaki aşağıdaki satır, atamaya yapılan çağrıyı `client.GetStringAsync` ve atamayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="44f37-163">The following line in the example program shows the call to `client.GetStringAsync` and the assignment.</span></span>

```csharp
Task<string> getStringTask = client.GetStringAsync("https://msdn.microsoft.com");
```

 <span data-ttu-id="44f37-164">Görevi, sonunda gerçek bir dize üreterek `client.GetStringAsync` bir söz olarak düşünebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="44f37-164">You can think of the task as a promise by `client.GetStringAsync` to produce an actual string eventually.</span></span> <span data-ttu-id="44f37-165">Bu arada, `AccessTheWebAsync` bu iş varsa bu söz dize bağlı `client.GetStringAsync`değildir , bu `client.GetStringAsync` iş beklerken devam edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="44f37-165">In the meantime, if `AccessTheWebAsync` has work to do that doesn't depend on the promised string from `client.GetStringAsync`, that work can continue while  `client.GetStringAsync` waits.</span></span> <span data-ttu-id="44f37-166">Örnekte, "ÜÇ" olarak etiketlenen aşağıdaki çıktı satırları, bağımsız çalışma yapma fırsatını temsil</span><span class="sxs-lookup"><span data-stu-id="44f37-166">In the example, the following lines of output, which are labeled "THREE," represent the opportunity to do independent work</span></span>

```output
THREE: Back in AccessTheWebAsync.
           Task getStringTask is started.
           About to await getStringTask & return a Task<int> to startButton_Click.
```

 <span data-ttu-id="44f37-167">Aşağıdaki ifade, beklenen `AccessTheWebAsync` zaman `getStringTask` ilerlemeyi askıya adatır.</span><span class="sxs-lookup"><span data-stu-id="44f37-167">The following statement suspends progress in `AccessTheWebAsync` when `getStringTask` is awaited.</span></span>

```csharp
string urlContents = await getStringTask;
```

 <span data-ttu-id="44f37-168">Aşağıdaki resimde, bir bekleme `client.GetStringAsync` işlecinin `getStringTask` `getStringTask` uygulanmasına ve oluşturulmasına kadar denetim akışı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="44f37-168">The following image shows the flow of control from `client.GetStringAsync` to the assignment to `getStringTask` and from the creation of `getStringTask` to the application of an await operator.</span></span>

 <span data-ttu-id="44f37-169">![Üçüncü Adım](./media/asynctrace-three.png "AsyncTrace-Üç")</span><span class="sxs-lookup"><span data-stu-id="44f37-169">![Step THREE](./media/asynctrace-three.png "AsyncTrace-Three")</span></span>

 <span data-ttu-id="44f37-170">Bekleyen ifade dönene `client.GetStringAsync` kadar askıya alınır. `AccessTheWebAsync`</span><span class="sxs-lookup"><span data-stu-id="44f37-170">The await expression suspends `AccessTheWebAsync` until `client.GetStringAsync` returns.</span></span> <span data-ttu-id="44f37-171">Bu arada, kontrol arayan döner `AccessTheWebAsync` `startButton_Click`, .</span><span class="sxs-lookup"><span data-stu-id="44f37-171">In the meantime, control returns to the caller of `AccessTheWebAsync`, `startButton_Click`.</span></span>

> [!NOTE]
> <span data-ttu-id="44f37-172">Genellikle, hemen bir eşzamanlı yöntem için çağrı bekliyor.</span><span class="sxs-lookup"><span data-stu-id="44f37-172">Typically, you await the call to an asynchronous method immediately.</span></span> <span data-ttu-id="44f37-173">Örneğin, aşağıdaki atama oluşturan önceki kodu değiştirebilir ve sonra `getStringTask`bekliyor:`string urlContents = await client.GetStringAsync("https://msdn.microsoft.com");`</span><span class="sxs-lookup"><span data-stu-id="44f37-173">For example, the following assignment could replace the previous code that creates and then awaits `getStringTask`: `string urlContents = await client.GetStringAsync("https://msdn.microsoft.com");`</span></span>
>
> <span data-ttu-id="44f37-174">Bu konuda, program aracılığıyla denetim akışını işaretleyen çıkış hatlarını karşılamak için bekleme işleci daha sonra uygulanır.</span><span class="sxs-lookup"><span data-stu-id="44f37-174">In this topic, the await operator is applied later to accommodate the output lines that mark the flow of control through the program.</span></span>

### <a name="step-four"></a><span data-ttu-id="44f37-175">Dördüncü Adım</span><span class="sxs-lookup"><span data-stu-id="44f37-175">Step FOUR</span></span>

<span data-ttu-id="44f37-176">Beyan edilen dönüş `AccessTheWebAsync` `Task<int>`türü.</span><span class="sxs-lookup"><span data-stu-id="44f37-176">The declared return type of `AccessTheWebAsync` is `Task<int>`.</span></span> <span data-ttu-id="44f37-177">Bu nedenle, askıya alındığınızda, `AccessTheWebAsync` tamsayı görevini `startButton_Click`döndürür.</span><span class="sxs-lookup"><span data-stu-id="44f37-177">Therefore, when `AccessTheWebAsync` is suspended, it returns a task of integer to `startButton_Click`.</span></span> <span data-ttu-id="44f37-178">Döndürülen görevin `getStringTask`.</span><span class="sxs-lookup"><span data-stu-id="44f37-178">You should understand that the returned task isn’t `getStringTask`.</span></span> <span data-ttu-id="44f37-179">Döndürülen görev, askıya alınan yöntemde yapılması gerekenleri temsil eden yeni `AccessTheWebAsync`bir tamsayı görevidir.</span><span class="sxs-lookup"><span data-stu-id="44f37-179">The returned task is a new task of integer that represents what remains to be done in the suspended method, `AccessTheWebAsync`.</span></span> <span data-ttu-id="44f37-180">Görev tamamlandığında bir `AccessTheWebAsync` tamsayı üretmek için bir sözdür.</span><span class="sxs-lookup"><span data-stu-id="44f37-180">The task is a promise from `AccessTheWebAsync` to produce an integer when the task is complete.</span></span>

<span data-ttu-id="44f37-181">Aşağıdaki deyim, bu görevi `getLengthTask` değişkene atar.</span><span class="sxs-lookup"><span data-stu-id="44f37-181">The following statement assigns this task to the `getLengthTask` variable.</span></span>

```csharp
Task<int> getLengthTask = AccessTheWebAsync();
```

 <span data-ttu-id="44f37-182">Olduğu `AccessTheWebAsync`gibi `startButton_Click` , görev beklenene kadar eşzamanlı görevin sonuçlarına bağlı`getLengthTask`olmayan çalışmalara devam edebilir .</span><span class="sxs-lookup"><span data-stu-id="44f37-182">As in `AccessTheWebAsync`, `startButton_Click` can continue with work that doesn’t depend on the results of the asynchronous task (`getLengthTask`) until the task is awaited.</span></span> <span data-ttu-id="44f37-183">Aşağıdaki çıktı satırları bu çalışmayı temsil ediyor.</span><span class="sxs-lookup"><span data-stu-id="44f37-183">The following output lines represent that work.</span></span>

```output
FOUR:  Back in startButton_Click.
           Task getLengthTask is started.
           About to await getLengthTask -- no caller to return to.
```

 <span data-ttu-id="44f37-184">Beklenen `startButton_Click` ilerleme `getLengthTask` askıya alınır.</span><span class="sxs-lookup"><span data-stu-id="44f37-184">Progress in `startButton_Click` is suspended when `getLengthTask` is awaited.</span></span> <span data-ttu-id="44f37-185">Aşağıdaki atama deyimi `startButton_Click` tamamlanana kadar `AccessTheWebAsync` askıya alınır.</span><span class="sxs-lookup"><span data-stu-id="44f37-185">The following assignment statement suspends `startButton_Click` until `AccessTheWebAsync` is complete.</span></span>

```csharp
int contentLength = await getLengthTask;
```

 <span data-ttu-id="44f37-186">Aşağıdaki resimde, oklar bekleme ifadesinden bir değerin `AccessTheWebAsync` atanmasına `getLengthTask`kadar denetim akışını gösterir , `startButton_Click` beklenene kadar `getLengthTask` normal işleme takip eder.</span><span class="sxs-lookup"><span data-stu-id="44f37-186">In the following illustration, the arrows show the flow of control from the await expression in `AccessTheWebAsync` to the assignment of a value to `getLengthTask`, followed by normal processing in `startButton_Click` until `getLengthTask` is awaited.</span></span>

 <span data-ttu-id="44f37-187">![Dördüncü Adım](./media/asynctrace-four.png "AsyncTrace-DÖRT")</span><span class="sxs-lookup"><span data-stu-id="44f37-187">![Step FOUR](./media/asynctrace-four.png "AsyncTrace-FOUR")</span></span>

### <a name="step-five"></a><span data-ttu-id="44f37-188">Adım BEŞ</span><span class="sxs-lookup"><span data-stu-id="44f37-188">Step FIVE</span></span>

<span data-ttu-id="44f37-189">`client.GetStringAsync` Sinyaller tamamlandığında, işlem `AccessTheWebAsync` askıya alındı ve bekleme deyimini geçmeye devam edebilir.</span><span class="sxs-lookup"><span data-stu-id="44f37-189">When `client.GetStringAsync` signals that it’s complete, processing in `AccessTheWebAsync` is released from suspension and can continue past the await statement.</span></span> <span data-ttu-id="44f37-190">Aşağıdaki çıktı satırları işlemin yeniden başlamasını temsil emzdir.</span><span class="sxs-lookup"><span data-stu-id="44f37-190">The following lines of output represent the resumption of processing.</span></span>

```output
FIVE:  Back in AccessTheWebAsync.
           Task getStringTask is complete.
           Processing the return statement.
           Exiting from AccessTheWebAsync.
```

 <span data-ttu-id="44f37-191">İade deyiminin operand'ı, `urlContents.Length`döndüren `AccessTheWebAsync` görevde depolanır.</span><span class="sxs-lookup"><span data-stu-id="44f37-191">The operand of the return statement, `urlContents.Length`, is stored in the task that  `AccessTheWebAsync` returns.</span></span> <span data-ttu-id="44f37-192">Bekleyen ifade bu değeri `getLengthTask` 'den `startButton_Click`alır.</span><span class="sxs-lookup"><span data-stu-id="44f37-192">The await expression retrieves that value from `getLengthTask` in `startButton_Click`.</span></span>

 <span data-ttu-id="44f37-193">Aşağıdaki resim, (ve) `client.GetStringAsync` `getStringTask`tamamlandıktan sonra denetim aktarımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="44f37-193">The following image shows the transfer of control after `client.GetStringAsync` (and `getStringTask`) are complete.</span></span>

 <span data-ttu-id="44f37-194">![Adım BEŞ](./media/asynctrace-five.png "AsyncTrace-BEŞ")</span><span class="sxs-lookup"><span data-stu-id="44f37-194">![Step FIVE](./media/asynctrace-five.png "AsyncTrace-FIVE")</span></span>

 <span data-ttu-id="44f37-195">`AccessTheWebAsync`tamamlanmasını sağlar ve denetim `startButton_Click`tamamlanmayı bekleyen e dönüşlere döner.</span><span class="sxs-lookup"><span data-stu-id="44f37-195">`AccessTheWebAsync` runs to completion, and control returns to `startButton_Click`, which is awaiting the completion.</span></span>

### <a name="step-six"></a><span data-ttu-id="44f37-196">Altıncı Adım</span><span class="sxs-lookup"><span data-stu-id="44f37-196">Step SIX</span></span>

<span data-ttu-id="44f37-197">`AccessTheWebAsync` Tamamlandığında, işleme bekleme deyimini `startButton_Async`'de geçmiş olarak devam edebilir.</span><span class="sxs-lookup"><span data-stu-id="44f37-197">When `AccessTheWebAsync` signals that it’s complete, processing can continue past the await statement in `startButton_Async`.</span></span> <span data-ttu-id="44f37-198">Aslında, programın yapacak başka bir şeyi yok.</span><span class="sxs-lookup"><span data-stu-id="44f37-198">In fact, the program has nothing more to do.</span></span>

<span data-ttu-id="44f37-199">Aşağıdaki çıktı satırları aşağıdaki işlemin `startButton_Async`devamını temsil eden:</span><span class="sxs-lookup"><span data-stu-id="44f37-199">The following lines of output represent the resumption of processing in `startButton_Async`:</span></span>

```output
SIX:   Back in startButton_Click.
           Task getLengthTask is finished.
           Result from AccessTheWebAsync is stored in contentLength.
           About to display contentLength and exit.
```

 <span data-ttu-id="44f37-200">Bekleyen ifade, `getLengthTask` `AccessTheWebAsync`'deki iade deyiminin operand'ı olan sonda değerinden alır.</span><span class="sxs-lookup"><span data-stu-id="44f37-200">The await expression retrieves from `getLengthTask` the integer value that’s the operand of the return statement in `AccessTheWebAsync`.</span></span> <span data-ttu-id="44f37-201">Aşağıdaki deyim, bu değeri `contentLength` değişkene atar.</span><span class="sxs-lookup"><span data-stu-id="44f37-201">The following statement assigns that value to the `contentLength` variable.</span></span>

```csharp
int contentLength = await getLengthTask;
```

 <span data-ttu-id="44f37-202">Aşağıdaki resimde denetimin 'den `AccessTheWebAsync` `startButton_Click`'e geri dönüşü gösterilmektedir</span><span class="sxs-lookup"><span data-stu-id="44f37-202">The following image shows the return of control from `AccessTheWebAsync` to `startButton_Click`.</span></span>

 <span data-ttu-id="44f37-203">![Altıncı Adım](./media/asynctrace-six.png "AsyncTrace-ALTI")</span><span class="sxs-lookup"><span data-stu-id="44f37-203">![Step SIX](./media/asynctrace-six.png "AsyncTrace-SIX")</span></span>

## <a name="see-also"></a><span data-ttu-id="44f37-204">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="44f37-204">See also</span></span>

- [<span data-ttu-id="44f37-205">Async ve await ile Asynchronous Programlama (C#)</span><span class="sxs-lookup"><span data-stu-id="44f37-205">Asynchronous Programming with async and await (C#)</span></span>](./index.md)
- [<span data-ttu-id="44f37-206">Async İade Türleri (C#)</span><span class="sxs-lookup"><span data-stu-id="44f37-206">Async Return Types (C#)</span></span>](./async-return-types.md)
- [<span data-ttu-id="44f37-207">Walkthrough: Async kullanarak Web'e erişim ve bekleme (C#)</span><span class="sxs-lookup"><span data-stu-id="44f37-207">Walkthrough: Accessing the Web by Using async and await (C#)</span></span>](./walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="44f37-208">Async Örnek: Async Programları (C # ve Visual Basic) Kontrol Akışı</span><span class="sxs-lookup"><span data-stu-id="44f37-208">Async Sample: Control Flow in Async Programs (C# and Visual Basic)</span></span>](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0)
