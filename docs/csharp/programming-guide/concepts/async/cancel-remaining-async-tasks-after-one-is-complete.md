---
title: Bir Tamamlandıktan Sonra Kalan Async Görevlerini İptal Et (C#)
ms.date: 07/20/2015
ms.assetid: d3cebc74-c392-497b-b1e6-62a262eabe05
ms.openlocfilehash: e829254c1cd47da16b14aa9c2c90312a97b4b581
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79169980"
---
# <a name="cancel-remaining-async-tasks-after-one-is-complete-c"></a><span data-ttu-id="d6894-102">Bir Tamamlandıktan Sonra Kalan Async Görevlerini İptal Et (C#)</span><span class="sxs-lookup"><span data-stu-id="d6894-102">Cancel Remaining Async Tasks after One Is Complete (C#)</span></span>
<span data-ttu-id="d6894-103">Bir <xref:System.Threading.CancellationToken>, <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> bir görev tamamlandığında kalan tüm görevleri iptal edebilirsiniz yöntemi kullanarak.</span><span class="sxs-lookup"><span data-stu-id="d6894-103">By using the <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> method together with a <xref:System.Threading.CancellationToken>, you can cancel all remaining tasks when one task is complete.</span></span> <span data-ttu-id="d6894-104">Yöntem, `WhenAny` görevlerin bir koleksiyon bir argüman alır.</span><span class="sxs-lookup"><span data-stu-id="d6894-104">The `WhenAny` method takes an argument that’s a collection of tasks.</span></span> <span data-ttu-id="d6894-105">Yöntem tüm görevleri başlatır ve tek bir görev döndürür.</span><span class="sxs-lookup"><span data-stu-id="d6894-105">The method starts all the tasks and returns a single task.</span></span> <span data-ttu-id="d6894-106">Koleksiyondaki herhangi bir görev tamamlandığında tek görev tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="d6894-106">The single task is complete when any task in the collection is complete.</span></span>  
  
 <span data-ttu-id="d6894-107">Bu örnek, görev koleksiyonundan bitirmek ve `WhenAny` kalan görevleri iptal etmek için ilk görevi tutmak için birlikte bir iptal belirteci nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d6894-107">This example demonstrates how to use a cancellation token in conjunction with `WhenAny` to hold onto the first task to finish from the collection of tasks and to cancel the remaining tasks.</span></span> <span data-ttu-id="d6894-108">Her görev bir web sitesinin içeriğini indirir.</span><span class="sxs-lookup"><span data-stu-id="d6894-108">Each task downloads the contents of a website.</span></span> <span data-ttu-id="d6894-109">Örnek, tamamlamak için ilk karşıdan yüklemenin içeriğini gösterir ve diğer indirmeleri iptal eder.</span><span class="sxs-lookup"><span data-stu-id="d6894-109">The example displays the length of the contents of the first download to complete and cancels the other downloads.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d6894-110">Örnekleri çalıştırmak için Visual Studio 2012 veya daha yeni ve .NET Framework 4.5 veya daha yeni bilgisayarınıza yüklü olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d6894-110">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
## <a name="downloading-the-example"></a><span data-ttu-id="d6894-111">Örneği İndirme</span><span class="sxs-lookup"><span data-stu-id="d6894-111">Downloading the Example</span></span>  
 <span data-ttu-id="d6894-112">Windows Presentation Foundation (WPF) projesinin tamamını [Async Sample: Fine Tuning Application'dan](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) indirebilir ve ardından aşağıdaki adımları izleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d6894-112">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span></span>  
  
1. <span data-ttu-id="d6894-113">İndirdiğiniz dosyayı sıkıştırın ve Visual Studio'yu başlatın.</span><span class="sxs-lookup"><span data-stu-id="d6894-113">Decompress the file that you downloaded, and then start Visual Studio.</span></span>  
  
2. <span data-ttu-id="d6894-114">Menü çubuğunda **Dosya**, **Aç**, **Proje/Çözüm'ü**seçin.</span><span class="sxs-lookup"><span data-stu-id="d6894-114">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
3. <span data-ttu-id="d6894-115">**Projeyi Aç** iletişim kutusunda, sıkıştırdığınız örnek kodu tutan klasörü açın ve ardından AsyncFineTuningCS için çözüm (.sln) dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="d6894-115">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningCS.</span></span>  
  
4. <span data-ttu-id="d6894-116">**Solution**Explorer'da, **CancelAfterOneTask** projesinin kısayol menüsünü açın ve ardından **StartUp Project olarak ayarla'yı**seçin.</span><span class="sxs-lookup"><span data-stu-id="d6894-116">In **Solution Explorer**, open the shortcut menu for the **CancelAfterOneTask** project, and then choose **Set as StartUp Project**.</span></span>  
  
5. <span data-ttu-id="d6894-117">Projeyi çalıştırmak için F5 tuşunu seçin.</span><span class="sxs-lookup"><span data-stu-id="d6894-117">Choose the F5 key to run the project.</span></span>  
  
     <span data-ttu-id="d6894-118">Projeyi hata ayıklamadan çalıştırmak için Ctrl+F5 tuşlarını seçin.</span><span class="sxs-lookup"><span data-stu-id="d6894-118">Choose the Ctrl+F5 keys to run the project without debugging it.</span></span>  
  
6. <span data-ttu-id="d6894-119">Farklı indirmelerin önce bitip bitdiğini doğrulamak için programı birkaç kez çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="d6894-119">Run the program several times to verify that different downloads finish first.</span></span>  
  
 <span data-ttu-id="d6894-120">Projeyi indirmek istemiyorsanız, bu konunun sonundaki MainWindow.xaml.cs dosyasını gözden geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d6894-120">If you don't want to download the project, you can review the MainWindow.xaml.cs file at the end of this topic.</span></span>  
  
## <a name="building-the-example"></a><span data-ttu-id="d6894-121">Örnek Oluşturma</span><span class="sxs-lookup"><span data-stu-id="d6894-121">Building the Example</span></span>  
 <span data-ttu-id="d6894-122">Bu konuyla ilgili örnek, görev listesini iptal etmek için Bir Async Görevi İptal Etme [veya Görev Listesi (C#)](./cancel-an-async-task-or-a-list-of-tasks.md) olarak geliştirilen projeye eklenir.</span><span class="sxs-lookup"><span data-stu-id="d6894-122">The example in this topic adds to the project that's developed in [Cancel an Async Task or a List of Tasks (C#)](./cancel-an-async-task-or-a-list-of-tasks.md) to cancel a list of tasks.</span></span> <span data-ttu-id="d6894-123">**İptal** düğmesi açıkça kullanılmasa da, örnek aynı UI'yi kullanır.</span><span class="sxs-lookup"><span data-stu-id="d6894-123">The example uses the same UI, although the **Cancel** button isn’t used explicitly.</span></span>  
  
 <span data-ttu-id="d6894-124">Örneği adım adım oluşturmak için, "Örneği İndirme" bölümündeki yönergeleri izleyin, ancak **StartUp Project**olarak **CancelAListOfTasks'i** seçin.</span><span class="sxs-lookup"><span data-stu-id="d6894-124">To build the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **CancelAListOfTasks** as the **StartUp Project**.</span></span> <span data-ttu-id="d6894-125">Bu konudaki değişiklikleri bu projeye ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d6894-125">Add the changes in this topic to that project.</span></span>  
  
 <span data-ttu-id="d6894-126">**CancelAListOfTasks** projesinin MainWindow.xaml.cs dosyasında, her web sitesi için işlem adımlarını `AccessTheWebAsync` döngüden aşağıdaki async yöntemine taşıyarak geçişi başlatın.</span><span class="sxs-lookup"><span data-stu-id="d6894-126">In the MainWindow.xaml.cs file of the **CancelAListOfTasks** project, start the transition by moving the processing steps for each website from the loop in `AccessTheWebAsync` to the following async method.</span></span>  
  
```csharp  
// ***Bundle the processing steps for a website into one async method.  
async Task<int> ProcessURLAsync(string url, HttpClient client, CancellationToken ct)  
{  
    // GetAsync returns a Task<HttpResponseMessage>.
    HttpResponseMessage response = await client.GetAsync(url, ct);  
  
    // Retrieve the website contents from the HttpResponseMessage.  
    byte[] urlContents = await response.Content.ReadAsByteArrayAsync();  
  
    return urlContents.Length;  
}  
```  
  
 <span data-ttu-id="d6894-127">Bu `AccessTheWebAsync`örnekte, bir dizi <xref:System.Linq.Enumerable.ToArray%2A> görev oluşturmak `WhenAny` ve başlatmak için bir sorgu, yöntem ve yöntem kullanır.</span><span class="sxs-lookup"><span data-stu-id="d6894-127">In `AccessTheWebAsync`, this example uses a query, the  <xref:System.Linq.Enumerable.ToArray%2A> method, and the `WhenAny` method to create and start an array of tasks.</span></span> <span data-ttu-id="d6894-128">`WhenAny` Diziye uygulama, beklenildiğinde, görev dizisinde tamamlanmasına ulaşmak için ilk göreve değerlendiren tek bir görevi döndürür.</span><span class="sxs-lookup"><span data-stu-id="d6894-128">The application of `WhenAny` to the array returns a single task that, when awaited, evaluates to the first task to reach completion in the array of tasks.</span></span>  
  
 <span data-ttu-id="d6894-129">Aşağıdaki değişiklikleri `AccessTheWebAsync`yapın.</span><span class="sxs-lookup"><span data-stu-id="d6894-129">Make the following changes in `AccessTheWebAsync`.</span></span> <span data-ttu-id="d6894-130">Yıldız işaretleri kod dosyasındaki değişiklikleri işaretler.</span><span class="sxs-lookup"><span data-stu-id="d6894-130">Asterisks mark the changes in the code file.</span></span>  
  
1. <span data-ttu-id="d6894-131">Yorum yapın veya döngüyü silin.</span><span class="sxs-lookup"><span data-stu-id="d6894-131">Comment out or delete the loop.</span></span>  
  
2. <span data-ttu-id="d6894-132">Yürütüldüğünde genel görevler topluluğu oluşturan bir sorgu oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d6894-132">Create a query that, when executed, produces a collection of generic tasks.</span></span> <span data-ttu-id="d6894-133">Her çağrı `ProcessURLAsync` bir <xref:System.Threading.Tasks.Task%601> `TResult` tamsayı olduğu bir yeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="d6894-133">Each call to `ProcessURLAsync` returns a <xref:System.Threading.Tasks.Task%601> where `TResult` is an integer.</span></span>  
  
    ```csharp  
    // ***Create a query that, when executed, returns a collection of tasks.  
    IEnumerable<Task<int>> downloadTasksQuery =  
        from url in urlList select ProcessURLAsync(url, client, ct);  
    ```  
  
3. <span data-ttu-id="d6894-134">Sorguyu yürütmek ve görevleri başlatmak için arayın. `ToArray`</span><span class="sxs-lookup"><span data-stu-id="d6894-134">Call `ToArray` to execute the query and start the tasks.</span></span> <span data-ttu-id="d6894-135">Bir sonraki `WhenAny` adımda yöntemin uygulanması sorguyu yürütmek ve `ToArray`kullanmadan görevleri başlatmak, ancak diğer yöntemler olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="d6894-135">The application of the `WhenAny` method in the next step would execute the query and start the tasks without using `ToArray`, but other methods might not.</span></span> <span data-ttu-id="d6894-136">En güvenli yöntem, sorgunun yürütülmesini açıkça zorlamaktır.</span><span class="sxs-lookup"><span data-stu-id="d6894-136">The safest practice is to force execution of the query explicitly.</span></span>  
  
    ```csharp  
    // ***Use ToArray to execute the query and start the download tasks.
    Task<int>[] downloadTasks = downloadTasksQuery.ToArray();  
    ```  
  
4. <span data-ttu-id="d6894-137">Görevlerin toplanmasını çağırın. `WhenAny`</span><span class="sxs-lookup"><span data-stu-id="d6894-137">Call `WhenAny` on the collection of tasks.</span></span> <span data-ttu-id="d6894-138">`WhenAny`bir `Task(Of Task(Of Integer))` veya `Task<Task<int>>`.</span><span class="sxs-lookup"><span data-stu-id="d6894-138">`WhenAny` returns a `Task(Of Task(Of Integer))` or `Task<Task<int>>`.</span></span>  <span data-ttu-id="d6894-139">Diğer bir `WhenAny` diğer anda, tek `Task(Of Integer)` bir `Task<int>` göreve veya beklenen zamana değerlendiren bir görev döndürür.</span><span class="sxs-lookup"><span data-stu-id="d6894-139">That is, `WhenAny` returns a task that evaluates to a single `Task(Of Integer)` or `Task<int>` when it’s awaited.</span></span> <span data-ttu-id="d6894-140">Bu tek görev, koleksiyonda tamamlanır ilk görevdir.</span><span class="sxs-lookup"><span data-stu-id="d6894-140">That single task is the first task in the collection to finish.</span></span> <span data-ttu-id="d6894-141">İlk tamamlanan `firstFinishedTask`görev.</span><span class="sxs-lookup"><span data-stu-id="d6894-141">The task that finished first is assigned to `firstFinishedTask`.</span></span> <span data-ttu-id="d6894-142">Bu bir `firstFinishedTask` <xref:System.Threading.Tasks.Task%601> karşıcının olduğu yerdir, `TResult` çünkü bu `ProcessURLAsync`bir geri dönüş türüdür.</span><span class="sxs-lookup"><span data-stu-id="d6894-142">The type of `firstFinishedTask` is <xref:System.Threading.Tasks.Task%601> where `TResult` is an integer because that's the return type of `ProcessURLAsync`.</span></span>  
  
    ```csharp  
    // ***Call WhenAny and then await the result. The task that finishes
    // first is assigned to firstFinishedTask.  
    Task<int> firstFinishedTask = await Task.WhenAny(downloadTasks);  
    ```  
  
5. <span data-ttu-id="d6894-143">Bu örnekte, yalnızca ilk bitiren görevle ilgileniyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="d6894-143">In this example, you’re interested only in the task that finishes first.</span></span> <span data-ttu-id="d6894-144">Bu nedenle, kalan görevleri iptal etmek için kullanın. <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="d6894-144">Therefore, use <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> to cancel the remaining tasks.</span></span>  
  
    ```csharp  
    // ***Cancel the rest of the downloads. You just want the first one.  
    cts.Cancel();  
    ```  
  
6. <span data-ttu-id="d6894-145">Son olarak, indirilen içeriğin uzunluğunu almak için bekleyin. `firstFinishedTask`</span><span class="sxs-lookup"><span data-stu-id="d6894-145">Finally, await `firstFinishedTask` to retrieve the length of the downloaded content.</span></span>  
  
    ```csharp  
    var length = await firstFinishedTask;  
    resultsTextBox.Text += $"\r\nLength of the downloaded website:  {length}\r\n";
    ```  
  
 <span data-ttu-id="d6894-146">Farklı indirmelerin önce bitip bitdiğini doğrulamak için programı birkaç kez çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="d6894-146">Run the program several times to verify that different downloads finish first.</span></span>  
  
## <a name="complete-example"></a><span data-ttu-id="d6894-147">Tam Örnek</span><span class="sxs-lookup"><span data-stu-id="d6894-147">Complete Example</span></span>  
 <span data-ttu-id="d6894-148">Aşağıdaki kod, örneğin MainWindow.xaml.cs dosyanın tamamıdır.</span><span class="sxs-lookup"><span data-stu-id="d6894-148">The following code is the complete MainWindow.xaml.cs file for the example.</span></span> <span data-ttu-id="d6894-149">Yıldız işaretleri, bu örnek için eklenen öğeleri işaretler.</span><span class="sxs-lookup"><span data-stu-id="d6894-149">Asterisks mark the elements that were added for this example.</span></span>  
  
 <span data-ttu-id="d6894-150">Için bir başvuru eklemeniz <xref:System.Net.Http>gerektiğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="d6894-150">Notice that you must add a reference for <xref:System.Net.Http>.</span></span>  
  
 <span data-ttu-id="d6894-151">Projeyi [Async Sample: Fine Tuning Application'dan](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d6894-151">You can download the project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d6894-152">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d6894-152">See also</span></span>

- <xref:System.Threading.Tasks.Task.WhenAny%2A>
- [<span data-ttu-id="d6894-153">Async Uygulamanızda İnce Ayar (C#)</span><span class="sxs-lookup"><span data-stu-id="d6894-153">Fine-Tuning Your Async Application (C#)</span></span>](./fine-tuning-your-async-application.md)
- [<span data-ttu-id="d6894-154">Async ve await ile Asynchronous Programlama (C#)</span><span class="sxs-lookup"><span data-stu-id="d6894-154">Asynchronous Programming with async and await (C#)</span></span>](./index.md)
- [<span data-ttu-id="d6894-155">Async Örnek: Uygulamanızı İyi Ayar</span><span class="sxs-lookup"><span data-stu-id="d6894-155">Async Sample: Fine Tuning Your Application</span></span>](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
