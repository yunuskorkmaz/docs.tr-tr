---
title: Tam (C#) biridir sonra geri kalan zaman uyumsuz görevleri iptal etme
ms.date: 07/20/2015
ms.assetid: d3cebc74-c392-497b-b1e6-62a262eabe05
ms.openlocfilehash: baf757f7f7a71528dd5dc36b0f807eb452577a38
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61702730"
---
# <a name="cancel-remaining-async-tasks-after-one-is-complete-c"></a><span data-ttu-id="29311-102">Tam (C#) biridir sonra geri kalan zaman uyumsuz görevleri iptal etme</span><span class="sxs-lookup"><span data-stu-id="29311-102">Cancel Remaining Async Tasks after One Is Complete (C#)</span></span>
<span data-ttu-id="29311-103">Kullanarak <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> yöntemi ile birlikte bir <xref:System.Threading.CancellationToken>, bir görev tamamlandığında kalan tüm görevleri iptal edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="29311-103">By using the <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> method together with a <xref:System.Threading.CancellationToken>, you can cancel all remaining tasks when one task is complete.</span></span> <span data-ttu-id="29311-104">`WhenAny` Yöntemi bir görev koleksiyonu olan bir bağımsız değişken alır.</span><span class="sxs-lookup"><span data-stu-id="29311-104">The `WhenAny` method takes an argument that’s a collection of tasks.</span></span> <span data-ttu-id="29311-105">Bu yöntem tüm görevleri başlatır ve tek bir görev döndürür.</span><span class="sxs-lookup"><span data-stu-id="29311-105">The method starts all the tasks and returns a single task.</span></span> <span data-ttu-id="29311-106">Koleksiyondaki herhangi bir görev tamamlandığında tek bir görev tamamlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="29311-106">The single task is complete when any task in the collection is complete.</span></span>  
  
 <span data-ttu-id="29311-107">Bu örnek ile birlikte bir iptal belirteci kullanmayı gösteren `WhenAny` bitirilecek ilk göreve görevleri koleksiyonundan tamamlanması ve kalan görevleri iptal etmek için tutacak.</span><span class="sxs-lookup"><span data-stu-id="29311-107">This example demonstrates how to use a cancellation token in conjunction with `WhenAny` to hold onto the first task to finish from the collection of tasks and to cancel the remaining tasks.</span></span> <span data-ttu-id="29311-108">Her görev bir Web sitesinin içeriklerini karşıdan yükler.</span><span class="sxs-lookup"><span data-stu-id="29311-108">Each task downloads the contents of a website.</span></span> <span data-ttu-id="29311-109">Bu örnek, tamamlanacak ilk yüklemenin içeriğinin uzunluğunu görüntüler ve diğer yüklemeleri iptal eder.</span><span class="sxs-lookup"><span data-stu-id="29311-109">The example displays the length of the contents of the first download to complete and cancels the other downloads.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="29311-110">Yeni bilgisayarınızda yüklü veya örnekleri çalıştırmak için Visual Studio 2012 veya daha yeni ve .NET Framework 4.5 yüklü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="29311-110">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
## <a name="downloading-the-example"></a><span data-ttu-id="29311-111">Örneği indirme</span><span class="sxs-lookup"><span data-stu-id="29311-111">Downloading the Example</span></span>  
 <span data-ttu-id="29311-112">Tüm Windows Presentation Foundation (WPF) projeden indirebileceğiniz [zaman uyumsuz örneği: Uygulamanıza ince](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) ve sonra aşağıdaki adımları izleyin.</span><span class="sxs-lookup"><span data-stu-id="29311-112">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span></span>  
  
1. <span data-ttu-id="29311-113">İndirdiğiniz dosyanın sıkıştırmasını açın ve sonra Visual Studio'yu başlatın.</span><span class="sxs-lookup"><span data-stu-id="29311-113">Decompress the file that you downloaded, and then start Visual Studio.</span></span>  
  
2. <span data-ttu-id="29311-114">Menü çubuğunda, **dosya**, **açık**, **proje/çözüm**.</span><span class="sxs-lookup"><span data-stu-id="29311-114">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
3. <span data-ttu-id="29311-115">İçinde **Proje Aç** iletişim kutusunda, açtığınız örnek kodu barındıran klasörü açın ve ardından AsyncFineTuningCS için çözüm (.sln) dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="29311-115">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningCS.</span></span>  
  
4. <span data-ttu-id="29311-116">İçinde **Çözüm Gezgini**, kısayol menüsünü açın **CancelAfterOneTask** proje ve ardından **başlangıç projesi olarak ayarla**.</span><span class="sxs-lookup"><span data-stu-id="29311-116">In **Solution Explorer**, open the shortcut menu for the **CancelAfterOneTask** project, and then choose **Set as StartUp Project**.</span></span>  
  
5. <span data-ttu-id="29311-117">Projeyi çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="29311-117">Choose the F5 key to run the project.</span></span>  
  
     <span data-ttu-id="29311-118">Projeyi hata ayıklama olmadan çalıştırmak için Ctrl + F5 tuşlarını seçin.</span><span class="sxs-lookup"><span data-stu-id="29311-118">Choose the Ctrl+F5 keys to run the project without debugging it.</span></span>  
  
6. <span data-ttu-id="29311-119">Programın farklı yüklemeleri ilk son doğrulamak için birkaç kez çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="29311-119">Run the program several times to verify that different downloads finish first.</span></span>  
  
 <span data-ttu-id="29311-120">Projeyi indirmek istemiyorsanız, bu konunun sonunda MainWindow.xaml.cs dosyasını gözden geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="29311-120">If you don't want to download the project, you can review the MainWindow.xaml.cs file at the end of this topic.</span></span>  
  
## <a name="building-the-example"></a><span data-ttu-id="29311-121">Örneği oluşturma</span><span class="sxs-lookup"><span data-stu-id="29311-121">Building the Example</span></span>  
 <span data-ttu-id="29311-122">Bu konudaki örnek içinde geliştirilen projeye ekler [zaman uyumsuz bir görev veya bir liste görevleri (C#) iptal](../../../../csharp/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md) Görevler listesini iptal etme.</span><span class="sxs-lookup"><span data-stu-id="29311-122">The example in this topic adds to the project that's developed in [Cancel an Async Task or a List of Tasks (C#)](../../../../csharp/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md) to cancel a list of tasks.</span></span> <span data-ttu-id="29311-123">Örnekte aynı Arabirim kullanılmaktadır, ancak **iptal** düğmesi açıkça kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="29311-123">The example uses the same UI, although the **Cancel** button isn’t used explicitly.</span></span>  
  
 <span data-ttu-id="29311-124">Örneği oluşturmak için kendinize, adım adım "Örneği indirme" bölümündeki yönergeleri izleyin, ancak seçin **CancelAListOfTasks** olarak **başlangıç projesi**.</span><span class="sxs-lookup"><span data-stu-id="29311-124">To build the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **CancelAListOfTasks** as the **StartUp Project**.</span></span> <span data-ttu-id="29311-125">Bu konuda, değişiklikleri bu projeye ekleyin.</span><span class="sxs-lookup"><span data-stu-id="29311-125">Add the changes in this topic to that project.</span></span>  
  
 <span data-ttu-id="29311-126">MainWindow.xaml.cs dosyasındaki **CancelAListOfTasks** proje, her Web sitesi için işlenen adımları döngüden taşıyarak geçişi başlatın `AccessTheWebAsync` aşağıdaki zaman uyumsuz yönteme.</span><span class="sxs-lookup"><span data-stu-id="29311-126">In the MainWindow.xaml.cs file of the **CancelAListOfTasks** project, start the transition by moving the processing steps for each website from the loop in `AccessTheWebAsync` to the following async method.</span></span>  
  
```csharp  
/ ***Bundle the processing steps for a website into one async method.  
async Task<int> ProcessURLAsync(string url, HttpClient client, CancellationToken ct)  
{  
    // GetAsync returns a Task<HttpResponseMessage>.   
    HttpResponseMessage response = await client.GetAsync(url, ct);  
  
    // Retrieve the website contents from the HttpResponseMessage.  
    byte[] urlContents = await response.Content.ReadAsByteArrayAsync();  
  
    return urlContents.Length;  
}  
```  
  
 <span data-ttu-id="29311-127">İçinde `AccessTheWebAsync`, bu örnekte sorgu, <xref:System.Linq.Enumerable.ToArray%2A> yöntemi ve `WhenAny` oluşturmak ve bir dizi görev başlamak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="29311-127">In `AccessTheWebAsync`, this example uses a query, the  <xref:System.Linq.Enumerable.ToArray%2A> method, and the `WhenAny` method to create and start an array of tasks.</span></span> <span data-ttu-id="29311-128">Uygulamayı `WhenAny` dizisi için tek bir görev, bekletildiğinde döndürür dizideki görevlerin tamamlanmasına ulaşmak için ilk görev değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="29311-128">The application of `WhenAny` to the array returns a single task that, when awaited, evaluates to the first task to reach completion in the array of tasks.</span></span>  
  
 <span data-ttu-id="29311-129">Aşağıdaki değişiklikleri yapın `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="29311-129">Make the following changes in `AccessTheWebAsync`.</span></span> <span data-ttu-id="29311-130">Yıldız işaretleri kod dosyasındaki değişiklikleri işaretler.</span><span class="sxs-lookup"><span data-stu-id="29311-130">Asterisks mark the changes in the code file.</span></span>  
  
1. <span data-ttu-id="29311-131">Açıklama satırı yapın veya döngü silin.</span><span class="sxs-lookup"><span data-stu-id="29311-131">Comment out or delete the loop.</span></span>  
  
2. <span data-ttu-id="29311-132">Yürütüldüğünde, bir sorgu, oluşturun bir genel görev koleksiyonu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="29311-132">Create a query that, when executed, produces a collection of generic tasks.</span></span> <span data-ttu-id="29311-133">Her çağrı `ProcessURLAsync` döndürür bir <xref:System.Threading.Tasks.Task%601> burada `TResult` bir tamsayıdır.</span><span class="sxs-lookup"><span data-stu-id="29311-133">Each call to `ProcessURLAsync` returns a <xref:System.Threading.Tasks.Task%601> where `TResult` is an integer.</span></span>  
  
    ```csharp  
    // ***Create a query that, when executed, returns a collection of tasks.  
    IEnumerable<Task<int>> downloadTasksQuery =  
        from url in urlList select ProcessURLAsync(url, client, ct);  
    ```  
  
3. <span data-ttu-id="29311-134">Çağrı `ToArray` sorguyu ve görevleri başlatın.</span><span class="sxs-lookup"><span data-stu-id="29311-134">Call `ToArray` to execute the query and start the tasks.</span></span> <span data-ttu-id="29311-135">Uygulamayı `WhenAny` sonraki adımda yöntemi ve sorguyu kullanmadan başlangıç görevleri `ToArray`, ancak diğer yöntemler bunu yapmayabilir.</span><span class="sxs-lookup"><span data-stu-id="29311-135">The application of the `WhenAny` method in the next step would execute the query and start the tasks without using `ToArray`, but other methods might not.</span></span> <span data-ttu-id="29311-136">En güvenli yöntem sorgu yürütmesini açıkça zorla sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="29311-136">The safest practice is to force execution of the query explicitly.</span></span>  
  
    ```csharp  
    // ***Use ToArray to execute the query and start the download tasks.   
    Task<int>[] downloadTasks = downloadTasksQuery.ToArray();  
    ```  
  
4. <span data-ttu-id="29311-137">Çağrı `WhenAny` üzerinde bir görev koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="29311-137">Call `WhenAny` on the collection of tasks.</span></span> <span data-ttu-id="29311-138">`WhenAny` döndürür bir `Task(Of Task(Of Integer))` veya `Task<Task<int>>`.</span><span class="sxs-lookup"><span data-stu-id="29311-138">`WhenAny` returns a `Task(Of Task(Of Integer))` or `Task<Task<int>>`.</span></span>  <span data-ttu-id="29311-139">Diğer bir deyişle, `WhenAny` değerlendiren bir görev için tek bir döndüren `Task(Of Integer)` veya `Task<int>` beklendiği zaman.</span><span class="sxs-lookup"><span data-stu-id="29311-139">That is, `WhenAny` returns a task that evaluates to a single `Task(Of Integer)` or `Task<int>` when it’s awaited.</span></span> <span data-ttu-id="29311-140">Bu tek görev tamamlamak için koleksiyondaki ilk görevdir.</span><span class="sxs-lookup"><span data-stu-id="29311-140">That single task is the first task in the collection to finish.</span></span> <span data-ttu-id="29311-141">İlk önce Tamamlanan görevin atandığı `firstFinishedTask`.</span><span class="sxs-lookup"><span data-stu-id="29311-141">The task that finished first is assigned to `firstFinishedTask`.</span></span> <span data-ttu-id="29311-142">Türünü `firstFinishedTask` olduğu <xref:System.Threading.Tasks.Task%601> burada `TResult` dönüş türü olan bir tamsayı çünkü `ProcessURLAsync`.</span><span class="sxs-lookup"><span data-stu-id="29311-142">The type of `firstFinishedTask` is <xref:System.Threading.Tasks.Task%601> where `TResult` is an integer because that's the return type of `ProcessURLAsync`.</span></span>  
  
    ```csharp  
    // ***Call WhenAny and then await the result. The task that finishes   
    // first is assigned to firstFinishedTask.  
    Task<int> firstFinishedTask = await Task.WhenAny(downloadTasks);  
    ```  
  
5. <span data-ttu-id="29311-143">Bu örnekte, önce sona eren yalnızca görevle ilgilendiniz.</span><span class="sxs-lookup"><span data-stu-id="29311-143">In this example, you’re interested only in the task that finishes first.</span></span> <span data-ttu-id="29311-144">Bu nedenle, <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> kalan görevleri iptal etmek için.</span><span class="sxs-lookup"><span data-stu-id="29311-144">Therefore, use <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> to cancel the remaining tasks.</span></span>  
  
    ```csharp  
    // ***Cancel the rest of the downloads. You just want the first one.  
    cts.Cancel();  
    ```  
  
6. <span data-ttu-id="29311-145">Son olarak, await `firstFinishedTask` karşıdan yüklenen içeriğin uzunluğunu almak için.</span><span class="sxs-lookup"><span data-stu-id="29311-145">Finally, await `firstFinishedTask` to retrieve the length of the downloaded content.</span></span>  
  
    ```csharp  
    var length = await firstFinishedTask;  
    resultsTextBox.Text += $"\r\nLength of the downloaded website:  {length}\r\n";
    ```  
  
 <span data-ttu-id="29311-146">Programın farklı yüklemeleri ilk son doğrulamak için birkaç kez çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="29311-146">Run the program several times to verify that different downloads finish first.</span></span>  
  
## <a name="complete-example"></a><span data-ttu-id="29311-147">Tam Örnek</span><span class="sxs-lookup"><span data-stu-id="29311-147">Complete Example</span></span>  
 <span data-ttu-id="29311-148">Aşağıdaki kod örneği için tam MainWindow.xaml.cs dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="29311-148">The following code is the complete MainWindow.xaml.cs file for the example.</span></span> <span data-ttu-id="29311-149">Yıldız işaretleri, bu örnek için eklenen öğeleri işaretler.</span><span class="sxs-lookup"><span data-stu-id="29311-149">Asterisks mark the elements that were added for this example.</span></span>  
  
 <span data-ttu-id="29311-150">İçin bir başvuru eklemeniz gerektiğini unutmayın <xref:System.Net.Http>.</span><span class="sxs-lookup"><span data-stu-id="29311-150">Notice that you must add a reference for <xref:System.Net.Http>.</span></span>  
  
 <span data-ttu-id="29311-151">Projeden indirebileceğiniz [zaman uyumsuz örneği: Uygulamanızı ince ayar](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span><span class="sxs-lookup"><span data-stu-id="29311-151">You can download the project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>  
  
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
  
// Add a using directive and a reference for System.Net.Http.  
using System.Net.Http;  
  
// Add the following using directive.  
using System.Threading;  
  
namespace CancelAfterOneTask  
{  
    public partial class MainWindow : Window  
    {  
        // Declare a System.Threading.CancellationTokenSource.  
        CancellationTokenSource cts;  
  
        public MainWindow()  
        {  
            InitializeComponent();  
        }  
  
        private async void startButton_Click(object sender, RoutedEventArgs e)  
        {  
            // Instantiate the CancellationTokenSource.  
            cts = new CancellationTokenSource();  
  
            resultsTextBox.Clear();  
  
            try  
            {  
                await AccessTheWebAsync(cts.Token);  
                resultsTextBox.Text += "\r\nDownload complete.";  
            }  
            catch (OperationCanceledException)  
            {  
                resultsTextBox.Text += "\r\nDownload canceled.";  
            }  
            catch (Exception)  
            {  
                resultsTextBox.Text += "\r\nDownload failed.";  
            }  
  
            // Set the CancellationTokenSource to null when the download is complete.  
            cts = null;  
        }  
  
        // You can still include a Cancel button if you want to.  
        private void cancelButton_Click(object sender, RoutedEventArgs e)  
        {  
            if (cts != null)  
            {  
                cts.Cancel();  
            }  
        }  
  
        // Provide a parameter for the CancellationToken.  
        async Task AccessTheWebAsync(CancellationToken ct)  
        {  
            HttpClient client = new HttpClient();  
  
            // Call SetUpURLList to make a list of web addresses.  
            List<string> urlList = SetUpURLList();  
  
            // ***Comment out or delete the loop.  
            //foreach (var url in urlList)  
            //{  
            //    // GetAsync returns a Task<HttpResponseMessage>.   
            //    // Argument ct carries the message if the Cancel button is chosen.   
            //    // ***Note that the Cancel button can cancel all remaining downloads.  
            //    HttpResponseMessage response = await client.GetAsync(url, ct);  
  
            //    // Retrieve the website contents from the HttpResponseMessage.  
            //    byte[] urlContents = await response.Content.ReadAsByteArrayAsync();  
  
            //    resultsTextBox.Text +=  
            //        $"\r\nLength of the downloaded string: {urlContents.Length}.\r\n";
            //}  
  
            // ***Create a query that, when executed, returns a collection of tasks.  
            IEnumerable<Task<int>> downloadTasksQuery =  
                from url in urlList select ProcessURLAsync(url, client, ct);  
  
            // ***Use ToArray to execute the query and start the download tasks.   
            Task<int>[] downloadTasks = downloadTasksQuery.ToArray();  
  
            // ***Call WhenAny and then await the result. The task that finishes   
            // first is assigned to firstFinishedTask.  
            Task<int> firstFinishedTask = await Task.WhenAny(downloadTasks);  
  
            // ***Cancel the rest of the downloads. You just want the first one.  
            cts.Cancel();  
  
            // ***Await the first completed task and display the results.   
            // Run the program several times to demonstrate that different  
            // websites can finish first.  
            var length = await firstFinishedTask;  
            resultsTextBox.Text += $"\r\nLength of the downloaded website:  {length}\r\n";
        }  
  
        // ***Bundle the processing steps for a website into one async method.  
        async Task<int> ProcessURLAsync(string url, HttpClient client, CancellationToken ct)  
        {  
            // GetAsync returns a Task<HttpResponseMessage>.   
            HttpResponseMessage response = await client.GetAsync(url, ct);  
  
            // Retrieve the website contents from the HttpResponseMessage.  
            byte[] urlContents = await response.Content.ReadAsByteArrayAsync();  
  
            return urlContents.Length;  
        }  
  
        // Add a method that creates a list of web addresses.  
        private List<string> SetUpURLList()  
        {  
            List<string> urls = new List<string>   
            {   
                "https://msdn.microsoft.com",  
                "https://msdn.microsoft.com/library/hh290138.aspx",  
                "https://msdn.microsoft.com/library/hh290140.aspx",  
                "https://msdn.microsoft.com/library/dd470362.aspx",  
                "https://msdn.microsoft.com/library/aa578028.aspx",  
                "https://msdn.microsoft.com/library/ms404677.aspx",  
                "https://msdn.microsoft.com/library/ff730837.aspx"  
            };  
            return urls;  
        }  
    }  
    // Sample output:  
  
    // Length of the downloaded website:  158856  
  
    // Download complete.  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="29311-152">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="29311-152">See also</span></span>

- <xref:System.Threading.Tasks.Task.WhenAny%2A>
- [<span data-ttu-id="29311-153">(C#) Async uygulamanızda hassas ayar yapma</span><span class="sxs-lookup"><span data-stu-id="29311-153">Fine-Tuning Your Async Application (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md)
- [<span data-ttu-id="29311-154">Zaman uyumsuz programlama ile async ve await (C#)</span><span class="sxs-lookup"><span data-stu-id="29311-154">Asynchronous Programming with async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/index.md)
- [<span data-ttu-id="29311-155">Zaman uyumsuz örneği: Uygulamanızda hassas ayar yapma</span><span class="sxs-lookup"><span data-stu-id="29311-155">Async Sample: Fine Tuning Your Application</span></span>](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
