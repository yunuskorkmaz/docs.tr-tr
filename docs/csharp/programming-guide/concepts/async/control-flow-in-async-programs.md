---
title: "Denetim akışı zaman uyumsuz programlarda (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: fc92b08b-fe1d-4d07-84ab-5192fafe06bb
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 7a13763b2eeec93e7db7ca770c4d52b4a2ba768c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="control-flow-in-async-programs-c"></a><span data-ttu-id="52512-102">Denetim akışı zaman uyumsuz programlarda (C#)</span><span class="sxs-lookup"><span data-stu-id="52512-102">Control Flow in Async Programs (C#)</span></span>
<span data-ttu-id="52512-103">Yazma ve kullanarak zaman uyumsuz programlar daha kolay korumak `async` ve `await` anahtar sözcükler.</span><span class="sxs-lookup"><span data-stu-id="52512-103">You can write and maintain asynchronous programs more easily by using the `async` and `await` keywords.</span></span> <span data-ttu-id="52512-104">Programınızı nasıl çalıştığını anlamak yoktur, ancak, sonuçlar beklenmedik.</span><span class="sxs-lookup"><span data-stu-id="52512-104">However, the results might surprise you if you don't understand how your program operates.</span></span> <span data-ttu-id="52512-105">Bu konu izlemeler her zaman bir yönteminden denetimi başka hangi bilgileri taşır göstermek için bir basit zaman uyumsuz program aracılığıyla denetim akışı aktarılır.</span><span class="sxs-lookup"><span data-stu-id="52512-105">This topic traces the flow of control through a simple async program to show you when control moves from one method to another and what information is transferred each time.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="52512-106">`async` Ve `await` anahtar sözcükler, Visual Studio 2012'de sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="52512-106">The `async` and `await` keywords were introduced in Visual Studio 2012.</span></span>  
  
 <span data-ttu-id="52512-107">Zaman uyumsuz koduyla içeren yöntemlerini işaretlemek genel olarak, [async (C#)](../../../../csharp/language-reference/keywords/async.md) değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="52512-107">In general, you mark methods that contain asynchronous code with the [async (C#)](../../../../csharp/language-reference/keywords/async.md) modifier.</span></span> <span data-ttu-id="52512-108">Zaman uyumsuz değiştiricisi ile işaretli bir yöntem içinde kullanabileceğiniz bir [await (C#)](../../../../csharp/language-reference/keywords/await.md) burada bir çağrılan zaman uyumsuz işlemin tamamlanmasını beklemek için yöntem duraklayacağını belirtmek üzere işleci.</span><span class="sxs-lookup"><span data-stu-id="52512-108">In a method that's marked with an async modifier, you can use an [await (C#)](../../../../csharp/language-reference/keywords/await.md) operator to specify where the method pauses to wait for a called asynchronous process to complete.</span></span> <span data-ttu-id="52512-109">Daha fazla bilgi için bkz: [zaman uyumsuz programlama ile async ve await (C#)](../../../../csharp/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="52512-109">For more information, see [Asynchronous Programming with async and await (C#)](../../../../csharp/programming-guide/concepts/async/index.md).</span></span>  
  
 <span data-ttu-id="52512-110">Aşağıdaki örnek, bir dize olarak belirtilen bir Web sitesi içeriğini indirmek ve dize uzunluğu görüntülemek için zaman uyumsuz yöntemleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="52512-110">The following example uses async methods to download the contents of a specified website as a string and to display the length of the string.</span></span> <span data-ttu-id="52512-111">Örneğin, aşağıdaki iki yöntem içerir.</span><span class="sxs-lookup"><span data-stu-id="52512-111">The example contains the following two methods.</span></span>  
  
-   <span data-ttu-id="52512-112">`startButton_Click`, hangi çağrıları `AccessTheWebAsync` ve sonucu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="52512-112">`startButton_Click`, which calls `AccessTheWebAsync` and displays the result.</span></span>  
  
-   <span data-ttu-id="52512-113">`AccessTheWebAsync`, bir dize olarak bir Web sitesi içeriğini indirir ve dize uzunluğu döndürür.</span><span class="sxs-lookup"><span data-stu-id="52512-113">`AccessTheWebAsync`, which downloads the contents of a website as a string and returns the length of the string.</span></span> <span data-ttu-id="52512-114">`AccessTheWebAsync`zaman uyumsuz bir kullanan <xref:System.Net.Http.HttpClient> yöntemi, <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>, içerik indirilemedi.</span><span class="sxs-lookup"><span data-stu-id="52512-114">`AccessTheWebAsync` uses an asynchronous <xref:System.Net.Http.HttpClient> method, <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>, to download the contents.</span></span>  
  
 <span data-ttu-id="52512-115">Program nasıl çalışacağını anlamanıza yardımcı olması için ve işaretlenmiş her noktada ne olacağını açıklamak için program boyunca stratejik noktalarda çizgiler görünür görüntü numaralı.</span><span class="sxs-lookup"><span data-stu-id="52512-115">Numbered display lines appear at strategic points throughout the program to help you understand how the program runs and to explain what happens at each point that is marked.</span></span> <span data-ttu-id="52512-116">Görüntü satırları "Bir"ile "altı." etiketli</span><span class="sxs-lookup"><span data-stu-id="52512-116">The display lines are labeled "ONE" through "SIX."</span></span> <span data-ttu-id="52512-117">Etiketlerin program bu kod satırları ulaştığında sipariş temsil eder.</span><span class="sxs-lookup"><span data-stu-id="52512-117">The labels represent the order in which the program reaches these lines of code.</span></span>  
  
 <span data-ttu-id="52512-118">Aşağıdaki kod program bir özetini gösterir.</span><span class="sxs-lookup"><span data-stu-id="52512-118">The following code shows an outline of the program.</span></span>  
  
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
  
 <span data-ttu-id="52512-119">"Bir"ile "altı," etiketli konumlardan her birindeki program geçerli durumu hakkındaki bilgileri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="52512-119">Each of the labeled locations, "ONE" through "SIX," displays information about the current state of the program.</span></span> <span data-ttu-id="52512-120">Şu çıktı üretilir.</span><span class="sxs-lookup"><span data-stu-id="52512-120">The following output is produced.</span></span>  
  
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
  
## <a name="set-up-the-program"></a><span data-ttu-id="52512-121">Program Ayarlama</span><span class="sxs-lookup"><span data-stu-id="52512-121">Set Up the Program</span></span>  
 <span data-ttu-id="52512-122">Bu konuda kullanan kodu MSDN'den yükleyebilir veya kendiniz oluşturabileceğiniz.</span><span class="sxs-lookup"><span data-stu-id="52512-122">You can download the code that this topic uses from MSDN, or you can build it yourself.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="52512-123">Örneği çalıştırmak için Visual Studio 2012 veya daha yeni ve .NET Framework 4.5 veya daha yeni bilgisayarınızda yüklü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="52512-123">To run the example, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
### <a name="download-the-program"></a><span data-ttu-id="52512-124">Programı indir</span><span class="sxs-lookup"><span data-stu-id="52512-124">Download the Program</span></span>  
 <span data-ttu-id="52512-125">Uygulama için bu konudan indirebilirsiniz [zaman uyumsuz örnek: zaman uyumsuz programlarda denetim akışı](http://go.microsoft.com/fwlink/?LinkId=255285).</span><span class="sxs-lookup"><span data-stu-id="52512-125">You can download the application for this topic from [Async Sample: Control Flow in Async Programs](http://go.microsoft.com/fwlink/?LinkId=255285).</span></span> <span data-ttu-id="52512-126">Aşağıdaki adımları açın ve programı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="52512-126">The following steps open and run the program.</span></span>  
  
1.  <span data-ttu-id="52512-127">İndirilen dosyanın sıkıştırmasını açın ve ardından Visual Studio'yu başlatın.</span><span class="sxs-lookup"><span data-stu-id="52512-127">Unzip the downloaded file, and then start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="52512-128">Menü çubuğunda seçin **dosya**, **açık**, **proje/çözüm**.</span><span class="sxs-lookup"><span data-stu-id="52512-128">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
3.  <span data-ttu-id="52512-129">Sıkıştırması açılmış örnek kodu içeren klasöre gidin, çözüm (.sln) dosyasını açın ve F5 tuşuna projesini derlemeyi ve çalıştırmayı seçin.</span><span class="sxs-lookup"><span data-stu-id="52512-129">Navigate to the folder that holds the unzipped sample code, open the solution (.sln) file, and then choose the F5 key to build and run the project.</span></span>  
  
### <a name="build-the-program-yourself"></a><span data-ttu-id="52512-130">Program kendiniz yapı</span><span class="sxs-lookup"><span data-stu-id="52512-130">Build the Program Yourself</span></span>  
 <span data-ttu-id="52512-131">Aşağıdaki Windows Presentation Foundation (WPF) projesi bu konuya yönelik kod örneği içerir.</span><span class="sxs-lookup"><span data-stu-id="52512-131">The following Windows Presentation Foundation (WPF) project contains the code example for this topic.</span></span>  
  
 <span data-ttu-id="52512-132">Projeyi çalıştırmak için aşağıdaki adımları gerçekleştirin:</span><span class="sxs-lookup"><span data-stu-id="52512-132">To run the project, perform the following steps:</span></span>  
  
1.  <span data-ttu-id="52512-133">Visual Studio'yu başlatın.</span><span class="sxs-lookup"><span data-stu-id="52512-133">Start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="52512-134">Menü çubuğunda seçin **dosya**, **yeni**, **proje**.</span><span class="sxs-lookup"><span data-stu-id="52512-134">On the menu bar, choose **File**, **New**, **Project**.</span></span>  
  
     <span data-ttu-id="52512-135">**Yeni proje** iletişim kutusu açılır.</span><span class="sxs-lookup"><span data-stu-id="52512-135">The **New Project** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="52512-136">İçinde **yüklü şablonlar** bölmesinde seçin **Visual C#**ve ardından **WPF uygulaması** proje türleri listesinden.</span><span class="sxs-lookup"><span data-stu-id="52512-136">In the **Installed Templates** pane, choose **Visual C#**, and then choose **WPF Application** from the list of project types.</span></span>  
  
4.  <span data-ttu-id="52512-137">Girin `AsyncTracer` projesinin adı olarak ve ardından **Tamam** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="52512-137">Enter `AsyncTracer` as the name of the project, and then choose the **OK** button.</span></span>  
  
     <span data-ttu-id="52512-138">Yeni Proje görünür **Çözüm Gezgini**.</span><span class="sxs-lookup"><span data-stu-id="52512-138">The new project appears in **Solution Explorer**.</span></span>  
  
5.  <span data-ttu-id="52512-139">Visual Studio Kod Düzenleyicisi'nde seçin **MainWindow.xaml** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="52512-139">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>  
  
     <span data-ttu-id="52512-140">Sekme görünür değilse, kısayol menüsünde MainWindow.xaml içinde açık **Çözüm Gezgini**ve ardından **görünümü kodu**.</span><span class="sxs-lookup"><span data-stu-id="52512-140">If the tab isn’t visible, open the shortcut menu for MainWindow.xaml in **Solution Explorer**, and then choose **View Code**.</span></span>  
  
6.  <span data-ttu-id="52512-141">İçinde **XAML** görüntülemek MainWindow.xaml, kodu aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="52512-141">In the **XAML** view of MainWindow.xaml, replace the code with the following code.</span></span>  
  
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
  
     <span data-ttu-id="52512-142">Bir düğmeyi ve bir metin kutusu içeren basit bir pencere görünür **tasarım** MainWindow.xaml görünümü.</span><span class="sxs-lookup"><span data-stu-id="52512-142">A simple window that contains a text box and a button appears in the **Design** view of MainWindow.xaml.</span></span>  
  
7.  <span data-ttu-id="52512-143">İçin bir başvuru ekleyin <xref:System.Net.Http>.</span><span class="sxs-lookup"><span data-stu-id="52512-143">Add a reference for <xref:System.Net.Http>.</span></span>  
  
8.  <span data-ttu-id="52512-144">İçinde **Çözüm Gezgini**MainWindow.xaml.cs için kısayol menüsünü açın ve ardından **görünümü kodu**.</span><span class="sxs-lookup"><span data-stu-id="52512-144">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.cs, and then choose **View Code**.</span></span>  
  
9. <span data-ttu-id="52512-145">MainWindow.xaml.cs kodu aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="52512-145">In MainWindow.xaml.cs, replace the code with the following code.</span></span>  
  
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
  
10. <span data-ttu-id="52512-146">Programını çalıştırın ve ardından için F5 tuşuna seçin **Başlat** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="52512-146">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
     <span data-ttu-id="52512-147">Şu çıktı görünür.</span><span class="sxs-lookup"><span data-stu-id="52512-147">The following output should appear.</span></span>  
  
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
  
## <a name="trace-the-program"></a><span data-ttu-id="52512-148">Program izleme</span><span class="sxs-lookup"><span data-stu-id="52512-148">Trace the Program</span></span>  
  
### <a name="steps-one-and-two"></a><span data-ttu-id="52512-149">Birinci ve ikinci adımları</span><span class="sxs-lookup"><span data-stu-id="52512-149">Steps ONE and TWO</span></span>  
 <span data-ttu-id="52512-150">İlk iki görüntü satırları yolu olarak izleme `startButton_Click` çağrıları `AccessTheWebAsync`, ve `AccessTheWebAsync` zaman uyumsuz çağrıları <xref:System.Net.Http.HttpClient> yöntemi <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>.</span><span class="sxs-lookup"><span data-stu-id="52512-150">The first two display lines trace the path as `startButton_Click` calls `AccessTheWebAsync`, and `AccessTheWebAsync` calls the asynchronous <xref:System.Net.Http.HttpClient> method <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>.</span></span> <span data-ttu-id="52512-151">Aşağıdaki resimde yöntemi başka bir yöntem çağrıları özetlenmektedir.</span><span class="sxs-lookup"><span data-stu-id="52512-151">The following image outlines the calls from method to method.</span></span>  
  
 <span data-ttu-id="52512-152">![Birinci ve ikinci adımları](../../../../csharp/programming-guide/concepts/async/media/asynctrace-onetwo.png "AsyncTrace ONETWO")</span><span class="sxs-lookup"><span data-stu-id="52512-152">![Steps ONE and TWO](../../../../csharp/programming-guide/concepts/async/media/asynctrace-onetwo.png "AsyncTrace-ONETWO")</span></span>  
  
 <span data-ttu-id="52512-153">Dönüş türü, her ikisi de `AccessTheWebAsync` ve `client.GetStringAsync` olan <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="52512-153">The return type of both `AccessTheWebAsync` and `client.GetStringAsync` is <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="52512-154">İçin `AccessTheWebAsync`, TResult bir tamsayı değil.</span><span class="sxs-lookup"><span data-stu-id="52512-154">For `AccessTheWebAsync`, TResult is an integer.</span></span> <span data-ttu-id="52512-155">İçin `GetStringAsync`, TResult olan bir dize.</span><span class="sxs-lookup"><span data-stu-id="52512-155">For `GetStringAsync`, TResult is a string.</span></span> <span data-ttu-id="52512-156">Zaman uyumsuz yöntem dönüş türleri hakkında daha fazla bilgi için bkz: [zaman uyumsuz dönüş türleri (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="52512-156">For more information about async method return types, see [Async Return Types (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md).</span></span>  
  
 <span data-ttu-id="52512-157">Denetim çağırana geri geçtiğinde bir görev döndüren zaman uyumsuz yöntem bir görev örneği döndürür.</span><span class="sxs-lookup"><span data-stu-id="52512-157">A task-returning async method returns a task instance when control shifts back to the caller.</span></span> <span data-ttu-id="52512-158">Denetim bir zaman uyumsuz yöntemden çağırıcısına döndürür ya da zaman bir `await` işleci çağrılan yöntemin veya çağrılan yöntemin sona erdiğinde karşılaştı.</span><span class="sxs-lookup"><span data-stu-id="52512-158">Control returns from an async method to its caller either when an `await` operator is encountered in the called method or when the called method ends.</span></span> <span data-ttu-id="52512-159">"Üç"ile "altı" etiketli görüntü satırları işleminin bu bölümü izleme.</span><span class="sxs-lookup"><span data-stu-id="52512-159">The display lines that are labeled "THREE" through "SIX" trace this part of the process.</span></span>  
  
### <a name="step-three"></a><span data-ttu-id="52512-160">ÜÇ adım</span><span class="sxs-lookup"><span data-stu-id="52512-160">Step THREE</span></span>  
 <span data-ttu-id="52512-161">İçinde `AccessTheWebAsync`, zaman uyumsuz yöntem <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> hedef Web sayfasının içeriğini indirmek için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="52512-161">In `AccessTheWebAsync`, the asynchronous method <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> is called to download the contents of the target webpage.</span></span> <span data-ttu-id="52512-162">Denetim döndürür `client.GetStringAsync` için `AccessTheWebAsync` zaman `client.GetStringAsync` döndürür.</span><span class="sxs-lookup"><span data-stu-id="52512-162">Control returns from `client.GetStringAsync` to `AccessTheWebAsync` when `client.GetStringAsync` returns.</span></span>  
  
 <span data-ttu-id="52512-163">`client.GetStringAsync` Yöntemi döndürür göreve atanan dizesinin `getStringTask` değişkeni `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="52512-163">The `client.GetStringAsync` method returns a task of string that’s assigned to the `getStringTask` variable in `AccessTheWebAsync`.</span></span> <span data-ttu-id="52512-164">Örnek program aşağıdaki satırda çağrı gösterilmektedir `client.GetStringAsync` ve atama.</span><span class="sxs-lookup"><span data-stu-id="52512-164">The following line in the example program shows the call to `client.GetStringAsync` and the assignment.</span></span>  
  
```csharp  
Task<string> getStringTask = client.GetStringAsync("http://msdn.microsoft.com");  
```  
  
 <span data-ttu-id="52512-165">Görevi tarafından bir promise olarak düşünebilirsiniz `client.GetStringAsync` gerçek bir dize sonunda üretmek için.</span><span class="sxs-lookup"><span data-stu-id="52512-165">You can think of the task as a promise by `client.GetStringAsync` to produce an actual string eventually.</span></span> <span data-ttu-id="52512-166">Bu arada, varsa `AccessTheWebAsync` taahhüt dizeden bağımlı değil yapmak için iş `client.GetStringAsync`, iş devam edebilirsiniz ancak `client.GetStringAsync` bekler.</span><span class="sxs-lookup"><span data-stu-id="52512-166">In the meantime, if `AccessTheWebAsync` has work to do that doesn't depend on the promised string from `client.GetStringAsync`, that work can continue while  `client.GetStringAsync` waits.</span></span> <span data-ttu-id="52512-167">Örnekte, "Üç" etiketli, aşağıdaki satırlar çıktı, bağımsız yapması için Fırsat temsil eder.</span><span class="sxs-lookup"><span data-stu-id="52512-167">In the example, the following lines of output, which are labeled "THREE," represent the opportunity to do independent work</span></span>  
  
```  
THREE: Back in AccessTheWebAsync.  
           Task getStringTask is started.  
           About to await getStringTask & return a Task<int> to startButton_Click.  
```  
  
 <span data-ttu-id="52512-168">Aşağıdaki deyim ediyor askıya `AccessTheWebAsync` zaman `getStringTask` beklemenin.</span><span class="sxs-lookup"><span data-stu-id="52512-168">The following statement suspends progress in `AccessTheWebAsync` when `getStringTask` is awaited.</span></span>  
  
```csharp  
string urlContents = await getStringTask;  
```  
  
 <span data-ttu-id="52512-169">Aşağıdaki resimde denetim akışı gösterilmektedir `client.GetStringAsync` atamayı için `getStringTask` ve oluşturulmasından `getStringTask` bekleme operatörün uygulama.</span><span class="sxs-lookup"><span data-stu-id="52512-169">The following image shows the flow of control from `client.GetStringAsync` to the assignment to `getStringTask` and from the creation of `getStringTask` to the application of an await operator.</span></span>  
  
 <span data-ttu-id="52512-170">![ÜÇ adım](../../../../csharp/programming-guide/concepts/async/media/asynctrace-three.png "AsyncTrace üç")</span><span class="sxs-lookup"><span data-stu-id="52512-170">![Step THREE](../../../../csharp/programming-guide/concepts/async/media/asynctrace-three.png "AsyncTrace-Three")</span></span>  
  
 <span data-ttu-id="52512-171">Bekleme ifade askıya `AccessTheWebAsync` kadar `client.GetStringAsync` döndürür.</span><span class="sxs-lookup"><span data-stu-id="52512-171">The await expression suspends `AccessTheWebAsync` until `client.GetStringAsync` returns.</span></span> <span data-ttu-id="52512-172">Bu arada, Denetim çağırana döndürür `AccessTheWebAsync`, `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="52512-172">In the meantime, control returns to the caller of `AccessTheWebAsync`, `startButton_Click`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="52512-173">Genellikle, zaman uyumsuz bir yöntem çağrısı hemen bekler.</span><span class="sxs-lookup"><span data-stu-id="52512-173">Typically, you await the call to an asynchronous method immediately.</span></span> <span data-ttu-id="52512-174">Örneğin, aşağıdaki atama oluşturur ve ardından bekler önceki kod değiştirme `getStringTask`:`string urlContents = await client.GetStringAsync("http://msdn.microsoft.com");`</span><span class="sxs-lookup"><span data-stu-id="52512-174">For example, the following assignment could replace the previous code that creates and then awaits `getStringTask`: `string urlContents = await client.GetStringAsync("http://msdn.microsoft.com");`</span></span>  
>   
>  <span data-ttu-id="52512-175">Bu konuda, bekleme işleci programı aracılığıyla denetim akışı işaretlemek çıktı satırları uyum sağlamak için daha sonra uygulanır.</span><span class="sxs-lookup"><span data-stu-id="52512-175">In this topic, the await operator is applied later to accommodate the output lines that mark the flow of control through the program.</span></span>  
  
### <a name="step-four"></a><span data-ttu-id="52512-176">DÖRT adım</span><span class="sxs-lookup"><span data-stu-id="52512-176">Step FOUR</span></span>  
 <span data-ttu-id="52512-177">Bildirilmiş dönüş türü `AccessTheWebAsync` olan `Task<int>`.</span><span class="sxs-lookup"><span data-stu-id="52512-177">The declared return type of `AccessTheWebAsync` is `Task<int>`.</span></span> <span data-ttu-id="52512-178">Bu nedenle, `AccessTheWebAsync` olan askıya, tamsayı, bir görev döndürür `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="52512-178">Therefore, when `AccessTheWebAsync` is suspended, it returns a task of integer to `startButton_Click`.</span></span> <span data-ttu-id="52512-179">Döndürülen görev olmadığını anlamalısınız `getStringTask`.</span><span class="sxs-lookup"><span data-stu-id="52512-179">You should understand that the returned task isn’t `getStringTask`.</span></span> <span data-ttu-id="52512-180">Yeni bir görev ne askıya alınmış yönteminde yapılması kalır gösteren tamsayı döndürülen görevdir `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="52512-180">The returned task is a new task of integer that represents what remains to be done in the suspended method, `AccessTheWebAsync`.</span></span> <span data-ttu-id="52512-181">Promise gelen görevdir `AccessTheWebAsync` görev tamamlandığında, bir tamsayı üretmek için.</span><span class="sxs-lookup"><span data-stu-id="52512-181">The task is a promise from `AccessTheWebAsync` to produce an integer when the task is complete.</span></span>  
  
 <span data-ttu-id="52512-182">Bu görev aşağıdaki deyim atar `getLengthTask` değişkeni.</span><span class="sxs-lookup"><span data-stu-id="52512-182">The following statement assigns this task to the `getLengthTask` variable.</span></span>  
  
```csharp  
Task<int> getLengthTask = AccessTheWebAsync();  
```  
  
 <span data-ttu-id="52512-183">Olarak `AccessTheWebAsync`, `startButton_Click` zaman uyumsuz görev sonuçlarına bağlı olmadığından iş devam edebilirsiniz (`getLengthTask`) görev beklemenin kadar.</span><span class="sxs-lookup"><span data-stu-id="52512-183">As in `AccessTheWebAsync`, `startButton_Click` can continue with work that doesn’t depend on the results of the asynchronous task (`getLengthTask`) until the task is awaited.</span></span> <span data-ttu-id="52512-184">Aşağıdaki çıkış satırları o iş temsil eder.</span><span class="sxs-lookup"><span data-stu-id="52512-184">The following output lines represent that work.</span></span>  
  
```  
FOUR:  Back in startButton_Click.  
           Task getLengthTask is started.  
           About to await getLengthTask -- no caller to return to.  
```  
  
 <span data-ttu-id="52512-185">İlerlemenizi `startButton_Click` zaman askıya `getLengthTask` beklemenin.</span><span class="sxs-lookup"><span data-stu-id="52512-185">Progress in `startButton_Click` is suspended when `getLengthTask` is awaited.</span></span> <span data-ttu-id="52512-186">Aşağıdaki atama deyimini askıya `startButton_Click` kadar `AccessTheWebAsync` tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="52512-186">The following assignment statement suspends `startButton_Click` until `AccessTheWebAsync` is complete.</span></span>  
  
```csharp  
int contentLength = await getLengthTask;  
```  
  
 <span data-ttu-id="52512-187">Aşağıdaki çizimde, bekleme ifadesinden denetim akışını okları Göster `AccessTheWebAsync` değerine atama `getLengthTask`, normal işlemde ardından `startButton_Click` kadar `getLengthTask` beklemenin.</span><span class="sxs-lookup"><span data-stu-id="52512-187">In the following illustration, the arrows show the flow of control from the await expression in `AccessTheWebAsync` to the assignment of a value to `getLengthTask`, followed by normal processing in `startButton_Click` until `getLengthTask` is awaited.</span></span>  
  
 <span data-ttu-id="52512-188">![DÖRT adım](../../../../csharp/programming-guide/concepts/async/media/asynctrace-four.png "AsyncTrace dört")</span><span class="sxs-lookup"><span data-stu-id="52512-188">![Step FOUR](../../../../csharp/programming-guide/concepts/async/media/asynctrace-four.png "AsyncTrace-FOUR")</span></span>  
  
### <a name="step-five"></a><span data-ttu-id="52512-189">BEŞ adımı</span><span class="sxs-lookup"><span data-stu-id="52512-189">Step FIVE</span></span>  
 <span data-ttu-id="52512-190">Zaman `client.GetStringAsync` tam olarak işleme olduğunu sinyalleri `AccessTheWebAsync` askı durumundan serbest ve bekleme deyimi devam edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="52512-190">When `client.GetStringAsync` signals that it’s complete, processing in `AccessTheWebAsync` is released from suspension and can continue past the await statement.</span></span> <span data-ttu-id="52512-191">Çıktı aşağıdaki satırları işleme sürdürme temsil eder.</span><span class="sxs-lookup"><span data-stu-id="52512-191">The following lines of output represent the resumption of processing.</span></span>  
  
```  
FIVE:  Back in AccessTheWebAsync.  
           Task getStringTask is complete.  
           Processing the return statement.  
           Exiting from AccessTheWebAsync.  
```  
  
 <span data-ttu-id="52512-192">Return deyimi işleneni `urlContents.Length`, görevin depolanır, `AccessTheWebAsync` döndürür.</span><span class="sxs-lookup"><span data-stu-id="52512-192">The operand of the return statement, `urlContents.Length`, is stored in the task that  `AccessTheWebAsync` returns.</span></span> <span data-ttu-id="52512-193">Bu değerden bekleme ifade alır `getLengthTask` içinde `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="52512-193">The await expression retrieves that value from `getLengthTask` in `startButton_Click`.</span></span>  
  
 <span data-ttu-id="52512-194">Aşağıdaki resimde sonra Denetim aktarımını gösterilmiştir `client.GetStringAsync` (ve `getStringTask`) tamamlandığından.</span><span class="sxs-lookup"><span data-stu-id="52512-194">The following image shows the transfer of control after `client.GetStringAsync` (and `getStringTask`) are complete.</span></span>  
  
 <span data-ttu-id="52512-195">![BEŞ adım](../../../../csharp/programming-guide/concepts/async/media/asynctrace-five.png "AsyncTrace beş")</span><span class="sxs-lookup"><span data-stu-id="52512-195">![Step FIVE](../../../../csharp/programming-guide/concepts/async/media/asynctrace-five.png "AsyncTrace-FIVE")</span></span>  
  
 <span data-ttu-id="52512-196">`AccessTheWebAsync`Tamamlama ve denetim çalışır döner `startButton_Click`, tamamlanması bekleniyor.</span><span class="sxs-lookup"><span data-stu-id="52512-196">`AccessTheWebAsync` runs to completion, and control returns to `startButton_Click`, which is awaiting the completion.</span></span>  
  
### <a name="step-six"></a><span data-ttu-id="52512-197">Adım 6</span><span class="sxs-lookup"><span data-stu-id="52512-197">Step SIX</span></span>  
 <span data-ttu-id="52512-198">Zaman `AccessTheWebAsync` işleme tam sinyalleri bekleme deyiminde geçmiş devam edebilir `startButton_Async`.</span><span class="sxs-lookup"><span data-stu-id="52512-198">When `AccessTheWebAsync` signals that it’s complete, processing can continue past the await statement in `startButton_Async`.</span></span> <span data-ttu-id="52512-199">Aslında, programın başka bir şey yapmak için vardır.</span><span class="sxs-lookup"><span data-stu-id="52512-199">In fact, the program has nothing more to do.</span></span>  
  
 <span data-ttu-id="52512-200">Çıktı aşağıdaki satırları işlemede sürdürme temsil eden `startButton_Async`:</span><span class="sxs-lookup"><span data-stu-id="52512-200">The following lines of output represent the resumption of processing in `startButton_Async`:</span></span>  
  
```  
SIX:   Back in startButton_Click.  
           Task getLengthTask is finished.  
           Result from AccessTheWebAsync is stored in contentLength.  
           About to display contentLength and exit.  
```  
  
 <span data-ttu-id="52512-201">Bekleme ifade alır `getLengthTask` içindeki return deyimi işleneni tamsayı değeri `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="52512-201">The await expression retrieves from `getLengthTask` the integer value that’s the operand of the return statement in `AccessTheWebAsync`.</span></span> <span data-ttu-id="52512-202">Aşağıdaki deyim bu değeri atar `contentLength` değişkeni.</span><span class="sxs-lookup"><span data-stu-id="52512-202">The following statement assigns that value to the `contentLength` variable.</span></span>  
  
```csharp  
int contentLength = await getLengthTask;  
```  
  
 <span data-ttu-id="52512-203">Aşağıdaki resimde denetiminden dönüş gösterilmiştir `AccessTheWebAsync` için `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="52512-203">The following image shows the return of control from `AccessTheWebAsync` to `startButton_Click`.</span></span>  
  
 <span data-ttu-id="52512-204">![ALTI adım](../../../../csharp/programming-guide/concepts/async/media/asynctrace-six.png "AsyncTrace altı")</span><span class="sxs-lookup"><span data-stu-id="52512-204">![Step SIX](../../../../csharp/programming-guide/concepts/async/media/asynctrace-six.png "AsyncTrace-SIX")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52512-205">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="52512-205">See Also</span></span>  
 [<span data-ttu-id="52512-206">Zaman uyumsuz programlama ile async ve await (C#)</span><span class="sxs-lookup"><span data-stu-id="52512-206">Asynchronous Programming with async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/index.md)  
 [<span data-ttu-id="52512-207">Zaman uyumsuz dönüş türleri (C#)</span><span class="sxs-lookup"><span data-stu-id="52512-207">Async Return Types (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/async-return-types.md)  
 [<span data-ttu-id="52512-208">İzlenecek yol: async kullanarak Web'e erişme ve await (C#)</span><span class="sxs-lookup"><span data-stu-id="52512-208">Walkthrough: Accessing the Web by Using async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)  
 [<span data-ttu-id="52512-209">Zaman uyumsuz örnek: Denetim akışı zaman uyumsuz programlarda (C# ve Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="52512-209">Async Sample: Control Flow in Async Programs (C# and Visual Basic)</span></span>](http://go.microsoft.com/fwlink/?LinkId=255285)
