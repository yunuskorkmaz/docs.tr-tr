---
title: Denetim akışı zaman uyumsuz programlarda (C#)
ms.date: 07/20/2015
ms.assetid: fc92b08b-fe1d-4d07-84ab-5192fafe06bb
ms.openlocfilehash: b05bfbd231745caf9e8b6031ce8e063469d8898b
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43502508"
---
# <a name="control-flow-in-async-programs-c"></a><span data-ttu-id="27b55-102">Denetim akışı zaman uyumsuz programlarda (C#)</span><span class="sxs-lookup"><span data-stu-id="27b55-102">Control Flow in Async Programs (C#)</span></span>
<span data-ttu-id="27b55-103">Yazma ve zaman uyumsuz programları daha kolay kullanarak koruduğunuz `async` ve `await` anahtar sözcükleri.</span><span class="sxs-lookup"><span data-stu-id="27b55-103">You can write and maintain asynchronous programs more easily by using the `async` and `await` keywords.</span></span> <span data-ttu-id="27b55-104">Ancak, nasıl programınızı anlamazsanız sonuçlar sizi şaşırtabilir.</span><span class="sxs-lookup"><span data-stu-id="27b55-104">However, the results might surprise you if you don't understand how your program operates.</span></span> <span data-ttu-id="27b55-105">Bu konu, her zaman denetimi başka bir ve hangi bilgileri bir yöntemden diğerine taşır. göstermek için basit bir zamanuyumsuz program aracılığıyla denetim akışını aktarılır izler.</span><span class="sxs-lookup"><span data-stu-id="27b55-105">This topic traces the flow of control through a simple async program to show you when control moves from one method to another and what information is transferred each time.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="27b55-106">`async` Ve `await` anahtar sözcükleri Visual Studio 2012'de kullanıma sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="27b55-106">The `async` and `await` keywords were introduced in Visual Studio 2012.</span></span>  
  
 <span data-ttu-id="27b55-107">Genel olarak, zaman uyumsuz kodun yer aldığı yöntemleri işaretleyin [async (C#)](../../../../csharp/language-reference/keywords/async.md) değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="27b55-107">In general, you mark methods that contain asynchronous code with the [async (C#)](../../../../csharp/language-reference/keywords/async.md) modifier.</span></span> <span data-ttu-id="27b55-108">Zaman uyumsuz değiştiriciyle işaretlenmiş bir yöntemde, kullandığınız bir [await (C#)](../../../../csharp/language-reference/keywords/await.md) burada yöntemin tamamlanması bir çağrılan zaman uyumsuz işlem için duraklatacağını belirtmek için işleci.</span><span class="sxs-lookup"><span data-stu-id="27b55-108">In a method that's marked with an async modifier, you can use an [await (C#)](../../../../csharp/language-reference/keywords/await.md) operator to specify where the method pauses to wait for a called asynchronous process to complete.</span></span> <span data-ttu-id="27b55-109">Daha fazla bilgi için [Asynchronous Programming with async ve await (C#)](../../../../csharp/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="27b55-109">For more information, see [Asynchronous Programming with async and await (C#)](../../../../csharp/programming-guide/concepts/async/index.md).</span></span>  
  
 <span data-ttu-id="27b55-110">Aşağıdaki örnek, bir dize olarak belirtilen bir Web sitesinin içeriklerini karşıdan yüklemek ve dizenin uzunluğu görüntülemek için zaman uyumsuz yöntemler kullanır.</span><span class="sxs-lookup"><span data-stu-id="27b55-110">The following example uses async methods to download the contents of a specified website as a string and to display the length of the string.</span></span> <span data-ttu-id="27b55-111">Örneğin, aşağıdaki iki yöntemi içerir.</span><span class="sxs-lookup"><span data-stu-id="27b55-111">The example contains the following two methods.</span></span>  
  
-   <span data-ttu-id="27b55-112">`startButton_Click`, hangi çağrıları `AccessTheWebAsync` ve sonucu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="27b55-112">`startButton_Click`, which calls `AccessTheWebAsync` and displays the result.</span></span>  
  
-   <span data-ttu-id="27b55-113">`AccessTheWebAsync`, bir dize olarak bir Web sitesinin içeriklerini karşıdan yükler ve dizenin uzunluğunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="27b55-113">`AccessTheWebAsync`, which downloads the contents of a website as a string and returns the length of the string.</span></span> <span data-ttu-id="27b55-114">`AccessTheWebAsync` zaman uyumsuz kullanan <xref:System.Net.Http.HttpClient> yöntemi <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>içeriğini indirmek için.</span><span class="sxs-lookup"><span data-stu-id="27b55-114">`AccessTheWebAsync` uses an asynchronous <xref:System.Net.Http.HttpClient> method, <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>, to download the contents.</span></span>  
  
 <span data-ttu-id="27b55-115">Numaralı ekran satırları, programın nasıl çalıştığını anlamanıza yardımcı olmak ve işaretlenmiş her noktada ne olacağını açıklamak için program boyunca stratejik noktalarda görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="27b55-115">Numbered display lines appear at strategic points throughout the program to help you understand how the program runs and to explain what happens at each point that is marked.</span></span> <span data-ttu-id="27b55-116">Görüntü satırları "Bir"ile "altı." olarak etiketlenmiştir</span><span class="sxs-lookup"><span data-stu-id="27b55-116">The display lines are labeled "ONE" through "SIX."</span></span> <span data-ttu-id="27b55-117">Etiketler, programın bu kod satırlarını ulaştığında sırayı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="27b55-117">The labels represent the order in which the program reaches these lines of code.</span></span>  
  
 <span data-ttu-id="27b55-118">Aşağıdaki kod, programın özetini gösterir.</span><span class="sxs-lookup"><span data-stu-id="27b55-118">The following code shows an outline of the program.</span></span>  
  
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
            String.Format("\r\nLength of the downloaded string: {0}.\r\n", contentLength);  
    }  
  
    async Task<int> AccessTheWebAsync()  
    {  
        // TWO  
        HttpClient client = new HttpClient();  
        Task<string> getStringTask =  
            client.GetStringAsync("http://msdn.microsoft.com");  
  
        // THREE                   
        string urlContents = await getStringTask;  
  
        // FIVE  
        return urlContents.Length;  
    }  
}  
```  
  
 <span data-ttu-id="27b55-119">"ONE"ila "SIX" arasındaki etiketli konumların her biri, programın geçerli durumuyla ilgili bilgileri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="27b55-119">Each of the labeled locations, "ONE" through "SIX," displays information about the current state of the program.</span></span> <span data-ttu-id="27b55-120">Aşağıdaki çıktı üretilmiştir.</span><span class="sxs-lookup"><span data-stu-id="27b55-120">The following output is produced.</span></span>  
  
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
  
## <a name="set-up-the-program"></a><span data-ttu-id="27b55-121">Program Ayarlama</span><span class="sxs-lookup"><span data-stu-id="27b55-121">Set Up the Program</span></span>  
 <span data-ttu-id="27b55-122">Bu konuda kullanan kodu MSDN sitesinden yükleyebilir veya size kendiniz oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="27b55-122">You can download the code that this topic uses from MSDN, or you can build it yourself.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="27b55-123">Yeni bilgisayarınızda yüklü veya örneği çalıştırmak için Visual Studio 2012 veya daha yeni ve .NET Framework 4.5 yüklü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="27b55-123">To run the example, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
### <a name="download-the-program"></a><span data-ttu-id="27b55-124">Programı indir</span><span class="sxs-lookup"><span data-stu-id="27b55-124">Download the Program</span></span>  
 <span data-ttu-id="27b55-125">Bu konu için uygulamayı indirebilirsiniz [zaman uyumsuz örneği: Zamanuyumsuz programlarda akış denetimi](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0).</span><span class="sxs-lookup"><span data-stu-id="27b55-125">You can download the application for this topic from [Async Sample: Control Flow in Async Programs](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0).</span></span> <span data-ttu-id="27b55-126">Aşağıdaki adımlar, açın ve programı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="27b55-126">The following steps open and run the program.</span></span>  
  
1.  <span data-ttu-id="27b55-127">İndirilen dosyanın sıkıştırmasını açın ve sonra Visual Studio'yu başlatın.</span><span class="sxs-lookup"><span data-stu-id="27b55-127">Unzip the downloaded file, and then start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="27b55-128">Menü çubuğunda, **dosya**, **açık**, **proje/çözüm**.</span><span class="sxs-lookup"><span data-stu-id="27b55-128">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
3.  <span data-ttu-id="27b55-129">Sıkıştırması açılmış örnek kodun bulunduğu klasöre gidin, çözüm (.sln) dosyasını açın ve sonra oluşturmak ve projeyi çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="27b55-129">Navigate to the folder that holds the unzipped sample code, open the solution (.sln) file, and then choose the F5 key to build and run the project.</span></span>  
  
### <a name="build-the-program-yourself"></a><span data-ttu-id="27b55-130">Programı kendiniz oluşturun</span><span class="sxs-lookup"><span data-stu-id="27b55-130">Build the Program Yourself</span></span>  
 <span data-ttu-id="27b55-131">Aşağıdaki Windows Presentation Foundation (WPF) projesi Bu konu için kod örneği içerir.</span><span class="sxs-lookup"><span data-stu-id="27b55-131">The following Windows Presentation Foundation (WPF) project contains the code example for this topic.</span></span>  
  
 <span data-ttu-id="27b55-132">Projeyi çalıştırmak için aşağıdaki adımları gerçekleştirin:</span><span class="sxs-lookup"><span data-stu-id="27b55-132">To run the project, perform the following steps:</span></span>  
  
1.  <span data-ttu-id="27b55-133">Visual Studio'yu başlatın.</span><span class="sxs-lookup"><span data-stu-id="27b55-133">Start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="27b55-134">Menü çubuğunda, **dosya**, **yeni**, **proje**.</span><span class="sxs-lookup"><span data-stu-id="27b55-134">On the menu bar, choose **File**, **New**, **Project**.</span></span>  
  
     <span data-ttu-id="27b55-135">**Yeni proje** iletişim kutusu açılır.</span><span class="sxs-lookup"><span data-stu-id="27b55-135">The **New Project** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="27b55-136">İçinde **yüklü şablonlar** bölmesinde seçin **Visual C#** ve ardından **WPF uygulaması** proje türleri listesinden.</span><span class="sxs-lookup"><span data-stu-id="27b55-136">In the **Installed Templates** pane, choose **Visual C#**, and then choose **WPF Application** from the list of project types.</span></span>  
  
4.  <span data-ttu-id="27b55-137">Girin `AsyncTracer` projesinin adı olarak seçip **Tamam** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="27b55-137">Enter `AsyncTracer` as the name of the project, and then choose the **OK** button.</span></span>  
  
     <span data-ttu-id="27b55-138">Yeni Proje görünür **Çözüm Gezgini**.</span><span class="sxs-lookup"><span data-stu-id="27b55-138">The new project appears in **Solution Explorer**.</span></span>  
  
5.  <span data-ttu-id="27b55-139">Visual Studio Kod Düzenleyicisi'nde seçin **MainWindow.xaml** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="27b55-139">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>  
  
     <span data-ttu-id="27b55-140">Sekme görünür değilse, nde MainWindow.xaml için kısayol menüsünü açın **Çözüm Gezgini**ve ardından **kodu görüntüle**.</span><span class="sxs-lookup"><span data-stu-id="27b55-140">If the tab isn’t visible, open the shortcut menu for MainWindow.xaml in **Solution Explorer**, and then choose **View Code**.</span></span>  
  
6.  <span data-ttu-id="27b55-141">İçinde **XAML** MainWindow.xaml görüntülemek için kodu aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="27b55-141">In the **XAML** view of MainWindow.xaml, replace the code with the following code.</span></span>  
  
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
  
     <span data-ttu-id="27b55-142">Bir metin kutusu ve bir düğme içeren basit bir pencere **tasarım** MainWindow.xaml görünümü.</span><span class="sxs-lookup"><span data-stu-id="27b55-142">A simple window that contains a text box and a button appears in the **Design** view of MainWindow.xaml.</span></span>  
  
7.  <span data-ttu-id="27b55-143">İçin bir başvuru eklemeniz <xref:System.Net.Http>.</span><span class="sxs-lookup"><span data-stu-id="27b55-143">Add a reference for <xref:System.Net.Http>.</span></span>  
  
8.  <span data-ttu-id="27b55-144">İçinde **Çözüm Gezgini**için MainWindow.xaml.cs kısayol menüsünü açın ve ardından **kodu görüntüle**.</span><span class="sxs-lookup"><span data-stu-id="27b55-144">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.cs, and then choose **View Code**.</span></span>  
  
9. <span data-ttu-id="27b55-145">MainWindow.xaml.cs kodu aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="27b55-145">In MainWindow.xaml.cs, replace the code with the following code.</span></span>  
  
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
                    String.Format("\r\nLength of the downloaded string: {0}.\r\n", contentLength);  
            }  
  
            async Task<int> AccessTheWebAsync()  
            {  
                resultsTextBox.Text += "\r\nTWO:   Entering AccessTheWebAsync.";  
  
                // Declare an HttpClient object.  
                HttpClient client = new HttpClient();  
  
                resultsTextBox.Text += "\r\n           Calling HttpClient.GetStringAsync.\r\n";  
  
                // GetStringAsync returns a Task<string>.   
                Task<string> getStringTask = client.GetStringAsync("http://msdn.microsoft.com");  
  
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
  
10. <span data-ttu-id="27b55-146">Programı çalıştırın ve ardından F5 tuşuna basın **Başlat** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="27b55-146">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
     <span data-ttu-id="27b55-147">Aşağıdaki çıktı görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="27b55-147">The following output should appear.</span></span>  
  
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
  
## <a name="trace-the-program"></a><span data-ttu-id="27b55-148">Programı İzle</span><span class="sxs-lookup"><span data-stu-id="27b55-148">Trace the Program</span></span>  
  
### <a name="steps-one-and-two"></a><span data-ttu-id="27b55-149">BİR ve ikinci adımlar</span><span class="sxs-lookup"><span data-stu-id="27b55-149">Steps ONE and TWO</span></span>  
 <span data-ttu-id="27b55-150">İlk iki görüntü satırı yolu olarak izleme `startButton_Click` çağrıları `AccessTheWebAsync`, ve `AccessTheWebAsync` zaman uyumsuz çağrı <xref:System.Net.Http.HttpClient> yöntemi <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>.</span><span class="sxs-lookup"><span data-stu-id="27b55-150">The first two display lines trace the path as `startButton_Click` calls `AccessTheWebAsync`, and `AccessTheWebAsync` calls the asynchronous <xref:System.Net.Http.HttpClient> method <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>.</span></span> <span data-ttu-id="27b55-151">Aşağıdaki resimde yöntemden yönteme çağrılar özetlenmektedir.</span><span class="sxs-lookup"><span data-stu-id="27b55-151">The following image outlines the calls from method to method.</span></span>  
  
 <span data-ttu-id="27b55-152">![BİR ve ikinci adımlar](../../../../csharp/programming-guide/concepts/async/media/asynctrace-onetwo.png "AsyncTrace ONETWO")</span><span class="sxs-lookup"><span data-stu-id="27b55-152">![Steps ONE and TWO](../../../../csharp/programming-guide/concepts/async/media/asynctrace-onetwo.png "AsyncTrace-ONETWO")</span></span>  
  
 <span data-ttu-id="27b55-153">Dönüş türü, her ikisi de `AccessTheWebAsync` ve `client.GetStringAsync` olduğu <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="27b55-153">The return type of both `AccessTheWebAsync` and `client.GetStringAsync` is <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="27b55-154">İçin `AccessTheWebAsync`, TResult bir tamsayı olduğu.</span><span class="sxs-lookup"><span data-stu-id="27b55-154">For `AccessTheWebAsync`, TResult is an integer.</span></span> <span data-ttu-id="27b55-155">İçin `GetStringAsync`, TResult olan bir dize.</span><span class="sxs-lookup"><span data-stu-id="27b55-155">For `GetStringAsync`, TResult is a string.</span></span> <span data-ttu-id="27b55-156">Zaman uyumsuz yöntem dönüş türleri hakkında daha fazla bilgi için bkz: [Async Return Types (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="27b55-156">For more information about async method return types, see [Async Return Types (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md).</span></span>  
  
 <span data-ttu-id="27b55-157">Bir görev döndüren zaman uyumsuz yöntem, Denetim arayana geri geçtiğinde bir görev örneği döndürür.</span><span class="sxs-lookup"><span data-stu-id="27b55-157">A task-returning async method returns a task instance when control shifts back to the caller.</span></span> <span data-ttu-id="27b55-158">Denetim, uyumsuz bir yöntemden arayanına döner ya da bir `await` çağrılan yöntem veya çağrılan yöntem sona erdiğinde işleciyle karşılaşıldığında.</span><span class="sxs-lookup"><span data-stu-id="27b55-158">Control returns from an async method to its caller either when an `await` operator is encountered in the called method or when the called method ends.</span></span> <span data-ttu-id="27b55-159">"Üç"ile "altı" etiketli görüntü satırları işlemin bu kısmında izleme.</span><span class="sxs-lookup"><span data-stu-id="27b55-159">The display lines that are labeled "THREE" through "SIX" trace this part of the process.</span></span>  
  
### <a name="step-three"></a><span data-ttu-id="27b55-160">Adım üç</span><span class="sxs-lookup"><span data-stu-id="27b55-160">Step THREE</span></span>  
 <span data-ttu-id="27b55-161">İçinde `AccessTheWebAsync`, zaman uyumsuz yöntemin <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> hedef Web sayfasının içeriğini indirmek için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="27b55-161">In `AccessTheWebAsync`, the asynchronous method <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> is called to download the contents of the target webpage.</span></span> <span data-ttu-id="27b55-162">Denetim döndüğü `client.GetStringAsync` için `AccessTheWebAsync` olduğunda `client.GetStringAsync` döndürür.</span><span class="sxs-lookup"><span data-stu-id="27b55-162">Control returns from `client.GetStringAsync` to `AccessTheWebAsync` when `client.GetStringAsync` returns.</span></span>  
  
 <span data-ttu-id="27b55-163">`client.GetStringAsync` Yöntemi bir görev için atanan bir dize döndürür `getStringTask` değişkeninde `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="27b55-163">The `client.GetStringAsync` method returns a task of string that’s assigned to the `getStringTask` variable in `AccessTheWebAsync`.</span></span> <span data-ttu-id="27b55-164">Örnek programdaki aşağıdaki satır çağrısını gösterir `client.GetStringAsync` atama.</span><span class="sxs-lookup"><span data-stu-id="27b55-164">The following line in the example program shows the call to `client.GetStringAsync` and the assignment.</span></span>  
  
```csharp  
Task<string> getStringTask = client.GetStringAsync("http://msdn.microsoft.com");  
```  
  
 <span data-ttu-id="27b55-165">Görevini, hedefi olarak düşünebilirsiniz `client.GetStringAsync` sonuçta gerçek bir dize oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="27b55-165">You can think of the task as a promise by `client.GetStringAsync` to produce an actual string eventually.</span></span> <span data-ttu-id="27b55-166">Bu arada, varsa `AccessTheWebAsync` dizeden bağımlı olmayan yapılacak çalışmaya sahipse `client.GetStringAsync`, iş devam edebilirsiniz ancak `client.GetStringAsync` bekler.</span><span class="sxs-lookup"><span data-stu-id="27b55-166">In the meantime, if `AccessTheWebAsync` has work to do that doesn't depend on the promised string from `client.GetStringAsync`, that work can continue while  `client.GetStringAsync` waits.</span></span> <span data-ttu-id="27b55-167">Örnekte, "Üç" etiketli, aşağıdaki çıktı satırları bağımsız iş yapma fırsatını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="27b55-167">In the example, the following lines of output, which are labeled "THREE," represent the opportunity to do independent work</span></span>  
  
```  
THREE: Back in AccessTheWebAsync.  
           Task getStringTask is started.  
           About to await getStringTask & return a Task<int> to startButton_Click.  
```  
  
 <span data-ttu-id="27b55-168">Aşağıdaki deyim ilerlemesini askıya alır `AccessTheWebAsync` olduğunda `getStringTask` beklenir.</span><span class="sxs-lookup"><span data-stu-id="27b55-168">The following statement suspends progress in `AccessTheWebAsync` when `getStringTask` is awaited.</span></span>  
  
```csharp  
string urlContents = await getStringTask;  
```  
  
 <span data-ttu-id="27b55-169">Aşağıdaki görüntüde, denetim akışı gösterilmektedir. `client.GetStringAsync` atamaya `getStringTask` ve oluşturulmasını `getStringTask` bir await işlecinin uygulamasına.</span><span class="sxs-lookup"><span data-stu-id="27b55-169">The following image shows the flow of control from `client.GetStringAsync` to the assignment to `getStringTask` and from the creation of `getStringTask` to the application of an await operator.</span></span>  
  
 <span data-ttu-id="27b55-170">![ÜÇ adım](../../../../csharp/programming-guide/concepts/async/media/asynctrace-three.png "AsyncTrace üç")</span><span class="sxs-lookup"><span data-stu-id="27b55-170">![Step THREE](../../../../csharp/programming-guide/concepts/async/media/asynctrace-three.png "AsyncTrace-Three")</span></span>  
  
 <span data-ttu-id="27b55-171">Await ifadesi askıya `AccessTheWebAsync` kadar `client.GetStringAsync` döndürür.</span><span class="sxs-lookup"><span data-stu-id="27b55-171">The await expression suspends `AccessTheWebAsync` until `client.GetStringAsync` returns.</span></span> <span data-ttu-id="27b55-172">Bu arada, Denetim çağırana döner `AccessTheWebAsync`, `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="27b55-172">In the meantime, control returns to the caller of `AccessTheWebAsync`, `startButton_Click`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="27b55-173">Genellikle, bir zaman uyumsuz yöntem çağrısı hemen bekler.</span><span class="sxs-lookup"><span data-stu-id="27b55-173">Typically, you await the call to an asynchronous method immediately.</span></span> <span data-ttu-id="27b55-174">Örneğin, aşağıdaki atama oluşturan ve sonra bekleyen önceki kodun yerini alabilir `getStringTask`: `string urlContents = await client.GetStringAsync("http://msdn.microsoft.com");`</span><span class="sxs-lookup"><span data-stu-id="27b55-174">For example, the following assignment could replace the previous code that creates and then awaits `getStringTask`: `string urlContents = await client.GetStringAsync("http://msdn.microsoft.com");`</span></span>  
>   
>  <span data-ttu-id="27b55-175">Bu konuda, await işleci, program aracılığıyla denetim akışını işaretleyen çıkış satırlarını yerleştirmek için daha sonra uygulanır.</span><span class="sxs-lookup"><span data-stu-id="27b55-175">In this topic, the await operator is applied later to accommodate the output lines that mark the flow of control through the program.</span></span>  
  
### <a name="step-four"></a><span data-ttu-id="27b55-176">Dördüncü adım</span><span class="sxs-lookup"><span data-stu-id="27b55-176">Step FOUR</span></span>  
 <span data-ttu-id="27b55-177">Bildirilen dönüş türü `AccessTheWebAsync` olduğu `Task<int>`.</span><span class="sxs-lookup"><span data-stu-id="27b55-177">The declared return type of `AccessTheWebAsync` is `Task<int>`.</span></span> <span data-ttu-id="27b55-178">Bu nedenle, `AccessTheWebAsync` olan askıya alındı, bir tamsayı görevi döndürür `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="27b55-178">Therefore, when `AccessTheWebAsync` is suspended, it returns a task of integer to `startButton_Click`.</span></span> <span data-ttu-id="27b55-179">Döndürülen görevin olmadığını anlamanız gereken `getStringTask`.</span><span class="sxs-lookup"><span data-stu-id="27b55-179">You should understand that the returned task isn’t `getStringTask`.</span></span> <span data-ttu-id="27b55-180">Döndürülen görevin askıya alınmış yönteminde yapılması kalan temsil eden tamsayı, yeni bir görevdir `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="27b55-180">The returned task is a new task of integer that represents what remains to be done in the suspended method, `AccessTheWebAsync`.</span></span> <span data-ttu-id="27b55-181">Görev bir vaadidir `AccessTheWebAsync` görev tamamlandığında bir tamsayı üretmek için.</span><span class="sxs-lookup"><span data-stu-id="27b55-181">The task is a promise from `AccessTheWebAsync` to produce an integer when the task is complete.</span></span>  
  
 <span data-ttu-id="27b55-182">Bu görev için aşağıdaki deyimi atar `getLengthTask` değişkeni.</span><span class="sxs-lookup"><span data-stu-id="27b55-182">The following statement assigns this task to the `getLengthTask` variable.</span></span>  
  
```csharp  
Task<int> getLengthTask = AccessTheWebAsync();  
```  
  
 <span data-ttu-id="27b55-183">Olarak `AccessTheWebAsync`, `startButton_Click` zaman uyumsuz görev sonuçlarına bağlı olmayan çalışmalar ile devam edebilir (`getLengthTask`) kadar görev beklenir.</span><span class="sxs-lookup"><span data-stu-id="27b55-183">As in `AccessTheWebAsync`, `startButton_Click` can continue with work that doesn’t depend on the results of the asynchronous task (`getLengthTask`) until the task is awaited.</span></span> <span data-ttu-id="27b55-184">Aşağıdaki çıktı satırları bu işi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="27b55-184">The following output lines represent that work.</span></span>  
  
```  
FOUR:  Back in startButton_Click.  
           Task getLengthTask is started.  
           About to await getLengthTask -- no caller to return to.  
```  
  
 <span data-ttu-id="27b55-185">İlerlemenizi `startButton_Click` zaman askıya `getLengthTask` beklenir.</span><span class="sxs-lookup"><span data-stu-id="27b55-185">Progress in `startButton_Click` is suspended when `getLengthTask` is awaited.</span></span> <span data-ttu-id="27b55-186">Aşağıdaki atama deyimi askıya `startButton_Click` kadar `AccessTheWebAsync` tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="27b55-186">The following assignment statement suspends `startButton_Click` until `AccessTheWebAsync` is complete.</span></span>  
  
```csharp  
int contentLength = await getLengthTask;  
```  
  
 <span data-ttu-id="27b55-187">Aşağıdaki çizimde, oklar seçeneğindeki await ifadesine içinde denetim akışını gösterir. `AccessTheWebAsync` bir değer atamaya `getLengthTask`, normal işlem tarafından izlenen `startButton_Click` kadar `getLengthTask` beklenir.</span><span class="sxs-lookup"><span data-stu-id="27b55-187">In the following illustration, the arrows show the flow of control from the await expression in `AccessTheWebAsync` to the assignment of a value to `getLengthTask`, followed by normal processing in `startButton_Click` until `getLengthTask` is awaited.</span></span>  
  
 <span data-ttu-id="27b55-188">![Dördüncü adım](../../../../csharp/programming-guide/concepts/async/media/asynctrace-four.png "AsyncTrace dört")</span><span class="sxs-lookup"><span data-stu-id="27b55-188">![Step FOUR](../../../../csharp/programming-guide/concepts/async/media/asynctrace-four.png "AsyncTrace-FOUR")</span></span>  
  
### <a name="step-five"></a><span data-ttu-id="27b55-189">Beşinci adım</span><span class="sxs-lookup"><span data-stu-id="27b55-189">Step FIVE</span></span>  
 <span data-ttu-id="27b55-190">Zaman `client.GetStringAsync` işleme işleminin tamamlandığından emin sinyalleri `AccessTheWebAsync` askıda durumundan çıkarılır ve bekleme ifadesinin ötesine devam edebilir.</span><span class="sxs-lookup"><span data-stu-id="27b55-190">When `client.GetStringAsync` signals that it’s complete, processing in `AccessTheWebAsync` is released from suspension and can continue past the await statement.</span></span> <span data-ttu-id="27b55-191">Aşağıdaki çıktı satırları işlemin sürdürülmesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="27b55-191">The following lines of output represent the resumption of processing.</span></span>  
  
```  
FIVE:  Back in AccessTheWebAsync.  
           Task getStringTask is complete.  
           Processing the return statement.  
           Exiting from AccessTheWebAsync.  
```  
  
 <span data-ttu-id="27b55-192">Return ifadesinin işleneni `urlContents.Length`, görevde depolanır, `AccessTheWebAsync` döndürür.</span><span class="sxs-lookup"><span data-stu-id="27b55-192">The operand of the return statement, `urlContents.Length`, is stored in the task that  `AccessTheWebAsync` returns.</span></span> <span data-ttu-id="27b55-193">Await ifadesi bu değeri alır. `getLengthTask` içinde `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="27b55-193">The await expression retrieves that value from `getLengthTask` in `startButton_Click`.</span></span>  
  
 <span data-ttu-id="27b55-194">Aşağıdaki görüntüde, sonraki denetim aktarımı gösterilmektedir `client.GetStringAsync` (ve `getStringTask`) getirildiğinden.</span><span class="sxs-lookup"><span data-stu-id="27b55-194">The following image shows the transfer of control after `client.GetStringAsync` (and `getStringTask`) are complete.</span></span>  
  
 <span data-ttu-id="27b55-195">![BEŞ adım](../../../../csharp/programming-guide/concepts/async/media/asynctrace-five.png "AsyncTrace beş")</span><span class="sxs-lookup"><span data-stu-id="27b55-195">![Step FIVE](../../../../csharp/programming-guide/concepts/async/media/asynctrace-five.png "AsyncTrace-FIVE")</span></span>  
  
 <span data-ttu-id="27b55-196">`AccessTheWebAsync` çalıştırır ve denetim döner `startButton_Click`, tamamlanması bekleniyor.</span><span class="sxs-lookup"><span data-stu-id="27b55-196">`AccessTheWebAsync` runs to completion, and control returns to `startButton_Click`, which is awaiting the completion.</span></span>  
  
### <a name="step-six"></a><span data-ttu-id="27b55-197">Altıncı adım</span><span class="sxs-lookup"><span data-stu-id="27b55-197">Step SIX</span></span>  
 <span data-ttu-id="27b55-198">Zaman `AccessTheWebAsync` tam işleme sinyalleri içindeki bekleme ifadesinin ötesine devam edebilir `startButton_Async`.</span><span class="sxs-lookup"><span data-stu-id="27b55-198">When `AccessTheWebAsync` signals that it’s complete, processing can continue past the await statement in `startButton_Async`.</span></span> <span data-ttu-id="27b55-199">Aslında, programın başka bir şey yapmak için vardır.</span><span class="sxs-lookup"><span data-stu-id="27b55-199">In fact, the program has nothing more to do.</span></span>  
  
 <span data-ttu-id="27b55-200">Aşağıdaki çıktı satırları içinde işlemin sürdürülmesini temsil etmektedir `startButton_Async`:</span><span class="sxs-lookup"><span data-stu-id="27b55-200">The following lines of output represent the resumption of processing in `startButton_Async`:</span></span>  
  
```  
SIX:   Back in startButton_Click.  
           Task getLengthTask is finished.  
           Result from AccessTheWebAsync is stored in contentLength.  
           About to display contentLength and exit.  
```  
  
 <span data-ttu-id="27b55-201">Await ifadesi alır `getLengthTask` içindeki return deyiminin işleneni olan bir tamsayı değer `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="27b55-201">The await expression retrieves from `getLengthTask` the integer value that’s the operand of the return statement in `AccessTheWebAsync`.</span></span> <span data-ttu-id="27b55-202">Aşağıdaki deyim, bu değeri atar `contentLength` değişkeni.</span><span class="sxs-lookup"><span data-stu-id="27b55-202">The following statement assigns that value to the `contentLength` variable.</span></span>  
  
```csharp  
int contentLength = await getLengthTask;  
```  
  
 <span data-ttu-id="27b55-203">Aşağıdaki görüntüde kadar denetimin dönüşü gösterilmektedir `AccessTheWebAsync` için `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="27b55-203">The following image shows the return of control from `AccessTheWebAsync` to `startButton_Click`.</span></span>  
  
 <span data-ttu-id="27b55-204">![ALTI adım](../../../../csharp/programming-guide/concepts/async/media/asynctrace-six.png "AsyncTrace altı")</span><span class="sxs-lookup"><span data-stu-id="27b55-204">![Step SIX](../../../../csharp/programming-guide/concepts/async/media/asynctrace-six.png "AsyncTrace-SIX")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27b55-205">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="27b55-205">See Also</span></span>

- [<span data-ttu-id="27b55-206">Zaman uyumsuz programlama ile async ve await (C#)</span><span class="sxs-lookup"><span data-stu-id="27b55-206">Asynchronous Programming with async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/index.md)  
- [<span data-ttu-id="27b55-207">Zaman uyumsuz dönüş türleri (C#)</span><span class="sxs-lookup"><span data-stu-id="27b55-207">Async Return Types (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/async-return-types.md)  
- [<span data-ttu-id="27b55-208">İzlenecek yol: async kullanarak Web'e erişme ve await (C#)</span><span class="sxs-lookup"><span data-stu-id="27b55-208">Walkthrough: Accessing the Web by Using async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)  
- [<span data-ttu-id="27b55-209">Zaman uyumsuz örneği: Zaman uyumsuz programlarda (C# ve Visual Basic) denetim akışı</span><span class="sxs-lookup"><span data-stu-id="27b55-209">Async Sample: Control Flow in Async Programs (C# and Visual Basic)</span></span>](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0)
