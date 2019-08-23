---
title: Tamamlandıktan sonra kalan zaman uyumsuz görevleri iptal et (C#)
ms.date: 07/20/2015
ms.assetid: d3cebc74-c392-497b-b1e6-62a262eabe05
ms.openlocfilehash: 81aed54d4854ad505971fbf85cf9a080a7c392d1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69922010"
---
# <a name="cancel-remaining-async-tasks-after-one-is-complete-c"></a><span data-ttu-id="06fda-102">Tamamlandıktan sonra kalan zaman uyumsuz görevleri iptal et (C#)</span><span class="sxs-lookup"><span data-stu-id="06fda-102">Cancel Remaining Async Tasks after One Is Complete (C#)</span></span>
<span data-ttu-id="06fda-103"><xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> Yöntemini bir<xref:System.Threading.CancellationToken>ile birlikte kullanarak, bir görev tamamlandığında kalan tüm görevleri iptal edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="06fda-103">By using the <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> method together with a <xref:System.Threading.CancellationToken>, you can cancel all remaining tasks when one task is complete.</span></span> <span data-ttu-id="06fda-104">Yöntemi `WhenAny` , bir görev koleksiyonu olan bir bağımsız değişken alır.</span><span class="sxs-lookup"><span data-stu-id="06fda-104">The `WhenAny` method takes an argument that’s a collection of tasks.</span></span> <span data-ttu-id="06fda-105">Yöntemi tüm görevleri başlatır ve tek bir görev döndürür.</span><span class="sxs-lookup"><span data-stu-id="06fda-105">The method starts all the tasks and returns a single task.</span></span> <span data-ttu-id="06fda-106">Koleksiyondaki herhangi bir görev tamamlandığında tek görev tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="06fda-106">The single task is complete when any task in the collection is complete.</span></span>  
  
 <span data-ttu-id="06fda-107">Bu örnek, bir iptal belirtecinin, görev koleksiyonundan sona ermesini ve `WhenAny` kalan görevleri iptal etmek için ilk görevi tutmak üzere ile birlikte nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="06fda-107">This example demonstrates how to use a cancellation token in conjunction with `WhenAny` to hold onto the first task to finish from the collection of tasks and to cancel the remaining tasks.</span></span> <span data-ttu-id="06fda-108">Her görev bir Web sitesinin içeriğini indirir.</span><span class="sxs-lookup"><span data-stu-id="06fda-108">Each task downloads the contents of a website.</span></span> <span data-ttu-id="06fda-109">Örnek, tamamlanacak ilk indirmenin içeriklerinin uzunluğunu görüntüler ve diğer indirmeleri iptal eder.</span><span class="sxs-lookup"><span data-stu-id="06fda-109">The example displays the length of the contents of the first download to complete and cancels the other downloads.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="06fda-110">Örnekleri çalıştırmak için, bilgisayarınızda Visual Studio 2012 veya daha yeni bir sürümü ve .NET Framework 4,5 ya da daha yeni bir sürümü yüklü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="06fda-110">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
## <a name="downloading-the-example"></a><span data-ttu-id="06fda-111">Örnek indiriliyor</span><span class="sxs-lookup"><span data-stu-id="06fda-111">Downloading the Example</span></span>  
 <span data-ttu-id="06fda-112">Tüm Windows Presentation Foundation (WPF) projesini [zaman uyumsuz örnekten indirebilirsiniz: Uygulamanızı](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) hassas ayarlamalar yapın ve ardından aşağıdaki adımları izleyin.</span><span class="sxs-lookup"><span data-stu-id="06fda-112">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span></span>  
  
1. <span data-ttu-id="06fda-113">İndirdiğiniz dosyayı sıkıştırmasını açın ve ardından Visual Studio 'Yu başlatın.</span><span class="sxs-lookup"><span data-stu-id="06fda-113">Decompress the file that you downloaded, and then start Visual Studio.</span></span>  
  
2. <span data-ttu-id="06fda-114">Menü çubuğunda **Dosya**, **Aç**, **Proje/çözüm**' ü seçin.</span><span class="sxs-lookup"><span data-stu-id="06fda-114">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
3. <span data-ttu-id="06fda-115">**Proje Aç** iletişim kutusunda, açtığınız örnek kodu tutan klasörü açın ve ardından AsyncFineTuningCS için çözüm (. sln) dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="06fda-115">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningCS.</span></span>  
  
4. <span data-ttu-id="06fda-116">**Çözüm Gezgini**' de, ınkıfteronetask projesinin kısayol menüsünü açın ve ardından **Başlangıç projesi olarak ayarla**' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="06fda-116">In **Solution Explorer**, open the shortcut menu for the **CancelAfterOneTask** project, and then choose **Set as StartUp Project**.</span></span>  
  
5. <span data-ttu-id="06fda-117">Projeyi çalıştırmak için F5 tuşunu seçin.</span><span class="sxs-lookup"><span data-stu-id="06fda-117">Choose the F5 key to run the project.</span></span>  
  
     <span data-ttu-id="06fda-118">Projeyi hata ayıklamadan çalıştırmak için CTRL + F5 tuşlarını seçin.</span><span class="sxs-lookup"><span data-stu-id="06fda-118">Choose the Ctrl+F5 keys to run the project without debugging it.</span></span>  
  
6. <span data-ttu-id="06fda-119">İlk olarak farklı indirmelerin bitmesini doğrulamak için programı birkaç kez çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="06fda-119">Run the program several times to verify that different downloads finish first.</span></span>  
  
 <span data-ttu-id="06fda-120">Projeyi indirmek istemiyorsanız, bu konunun sonundaki MainWindow.xaml.cs dosyasını gözden geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="06fda-120">If you don't want to download the project, you can review the MainWindow.xaml.cs file at the end of this topic.</span></span>  
  
## <a name="building-the-example"></a><span data-ttu-id="06fda-121">Örnek oluşturma</span><span class="sxs-lookup"><span data-stu-id="06fda-121">Building the Example</span></span>  
 <span data-ttu-id="06fda-122">Bu konudaki örnek, bir görev listesini iptal etmek için [zaman uyumsuz bir görevi veya görev listesini (C#) iptal](./cancel-an-async-task-or-a-list-of-tasks.md) etmek üzere geliştirilmiş projeye ekler.</span><span class="sxs-lookup"><span data-stu-id="06fda-122">The example in this topic adds to the project that's developed in [Cancel an Async Task or a List of Tasks (C#)](./cancel-an-async-task-or-a-list-of-tasks.md) to cancel a list of tasks.</span></span> <span data-ttu-id="06fda-123">Örnek, aynı kullanıcı arabirimini kullanır, ancak **iptal** düğmesi açıkça kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="06fda-123">The example uses the same UI, although the **Cancel** button isn’t used explicitly.</span></span>  
  
 <span data-ttu-id="06fda-124">Örneği kendiniz oluşturmak için, "örneği Indirme" bölümündeki yönergeleri izleyin, ancak **Başlangıç projesi**olarak iptal eden ınlıftasks ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="06fda-124">To build the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **CancelAListOfTasks** as the **StartUp Project**.</span></span> <span data-ttu-id="06fda-125">Bu konudaki değişiklikleri bu projeye ekleyin.</span><span class="sxs-lookup"><span data-stu-id="06fda-125">Add the changes in this topic to that project.</span></span>  
  
 <span data-ttu-id="06fda-126">"MainWindow.xaml.cs & lt; & lt; & lt; & lt; & lt; 3} dosya dosyasında, içindeki `AccessTheWebAsync` her bir Web sitesi için işleme adımlarını aşağıdaki zaman uyumsuz metoda taşıyarak geçişi başlatın.</span><span class="sxs-lookup"><span data-stu-id="06fda-126">In the MainWindow.xaml.cs file of the **CancelAListOfTasks** project, start the transition by moving the processing steps for each website from the loop in `AccessTheWebAsync` to the following async method.</span></span>  
  
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
  
 <span data-ttu-id="06fda-127">' `AccessTheWebAsync`De, bu örnek bir sorgu <xref:System.Linq.Enumerable.ToArray%2A> , yöntem ve `WhenAny` bir dizi görev oluşturmak ve başlatmak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="06fda-127">In `AccessTheWebAsync`, this example uses a query, the  <xref:System.Linq.Enumerable.ToArray%2A> method, and the `WhenAny` method to create and start an array of tasks.</span></span> <span data-ttu-id="06fda-128">Dizi için olan `WhenAny` uygulaması, bir görev dizisinde tamamlamaya ulaşmak üzere ilk görevi değerlendiren tek bir görev döndürür.</span><span class="sxs-lookup"><span data-stu-id="06fda-128">The application of `WhenAny` to the array returns a single task that, when awaited, evaluates to the first task to reach completion in the array of tasks.</span></span>  
  
 <span data-ttu-id="06fda-129">İçinde `AccessTheWebAsync`aşağıdaki değişiklikleri yapın.</span><span class="sxs-lookup"><span data-stu-id="06fda-129">Make the following changes in `AccessTheWebAsync`.</span></span> <span data-ttu-id="06fda-130">Yıldız işaretleri kod dosyasındaki değişiklikleri işaretler.</span><span class="sxs-lookup"><span data-stu-id="06fda-130">Asterisks mark the changes in the code file.</span></span>  
  
1. <span data-ttu-id="06fda-131">Döngüyü not edin veya silin.</span><span class="sxs-lookup"><span data-stu-id="06fda-131">Comment out or delete the loop.</span></span>  
  
2. <span data-ttu-id="06fda-132">Yürütüldüğünde, genel görevlerden oluşan bir koleksiyon üreten bir sorgu oluşturun.</span><span class="sxs-lookup"><span data-stu-id="06fda-132">Create a query that, when executed, produces a collection of generic tasks.</span></span> <span data-ttu-id="06fda-133">Her çağrısı `ProcessURLAsync` ,`TResult` bir, <xref:System.Threading.Tasks.Task%601> bir tamsayı olan bir döndürür.</span><span class="sxs-lookup"><span data-stu-id="06fda-133">Each call to `ProcessURLAsync` returns a <xref:System.Threading.Tasks.Task%601> where `TResult` is an integer.</span></span>  
  
    ```csharp  
    // ***Create a query that, when executed, returns a collection of tasks.  
    IEnumerable<Task<int>> downloadTasksQuery =  
        from url in urlList select ProcessURLAsync(url, client, ct);  
    ```  
  
3. <span data-ttu-id="06fda-134">Sorguyu `ToArray` yürütmek ve görevleri başlatmak için çağırın.</span><span class="sxs-lookup"><span data-stu-id="06fda-134">Call `ToArray` to execute the query and start the tasks.</span></span> <span data-ttu-id="06fda-135">Bir `WhenAny` sonraki adımda yönteminin uygulaması sorguyu yürütür ve görevleri kullanmadan `ToArray`başlatır, ancak diğer yöntemler de çalışmayabilir.</span><span class="sxs-lookup"><span data-stu-id="06fda-135">The application of the `WhenAny` method in the next step would execute the query and start the tasks without using `ToArray`, but other methods might not.</span></span> <span data-ttu-id="06fda-136">En güvenli yöntem, sorgunun yürütülmesini açıkça zorlamaktır.</span><span class="sxs-lookup"><span data-stu-id="06fda-136">The safest practice is to force execution of the query explicitly.</span></span>  
  
    ```csharp  
    // ***Use ToArray to execute the query and start the download tasks.   
    Task<int>[] downloadTasks = downloadTasksQuery.ToArray();  
    ```  
  
4. <span data-ttu-id="06fda-137">Görevler `WhenAny` koleksiyonunda çağırın.</span><span class="sxs-lookup"><span data-stu-id="06fda-137">Call `WhenAny` on the collection of tasks.</span></span> <span data-ttu-id="06fda-138">`WhenAny`bir `Task(Of Task(Of Integer))` veya`Task<Task<int>>`döndürür.</span><span class="sxs-lookup"><span data-stu-id="06fda-138">`WhenAny` returns a `Task(Of Task(Of Integer))` or `Task<Task<int>>`.</span></span>  <span data-ttu-id="06fda-139">Diğer bir deyişle `WhenAny` , tek `Task(Of Integer)` veya `Task<int>` bekleniyor bir görevi döndürür.</span><span class="sxs-lookup"><span data-stu-id="06fda-139">That is, `WhenAny` returns a task that evaluates to a single `Task(Of Integer)` or `Task<int>` when it’s awaited.</span></span> <span data-ttu-id="06fda-140">Bu tek görev, koleksiyondaki ilk görevin sona ermesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="06fda-140">That single task is the first task in the collection to finish.</span></span> <span data-ttu-id="06fda-141">Önce tamamlanan görev öğesine `firstFinishedTask`atanır.</span><span class="sxs-lookup"><span data-stu-id="06fda-141">The task that finished first is assigned to `firstFinishedTask`.</span></span> <span data-ttu-id="06fda-142">Türü `firstFinishedTask` <xref:System.Threading.Tasks.Task%601> `ProcessURLAsync`, öğesinin dönüş türü olduğu için bir tamsayıdır. `TResult`</span><span class="sxs-lookup"><span data-stu-id="06fda-142">The type of `firstFinishedTask` is <xref:System.Threading.Tasks.Task%601> where `TResult` is an integer because that's the return type of `ProcessURLAsync`.</span></span>  
  
    ```csharp  
    // ***Call WhenAny and then await the result. The task that finishes   
    // first is assigned to firstFinishedTask.  
    Task<int> firstFinishedTask = await Task.WhenAny(downloadTasks);  
    ```  
  
5. <span data-ttu-id="06fda-143">Bu örnekte, yalnızca ilk olarak sona erki görevi ilgileniyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="06fda-143">In this example, you’re interested only in the task that finishes first.</span></span> <span data-ttu-id="06fda-144">Bu nedenle, <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> kalan görevleri iptal etmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="06fda-144">Therefore, use <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> to cancel the remaining tasks.</span></span>  
  
    ```csharp  
    // ***Cancel the rest of the downloads. You just want the first one.  
    cts.Cancel();  
    ```  
  
6. <span data-ttu-id="06fda-145">Son olarak, `firstFinishedTask` indirilen içeriğin uzunluğunu almak için Await.</span><span class="sxs-lookup"><span data-stu-id="06fda-145">Finally, await `firstFinishedTask` to retrieve the length of the downloaded content.</span></span>  
  
    ```csharp  
    var length = await firstFinishedTask;  
    resultsTextBox.Text += $"\r\nLength of the downloaded website:  {length}\r\n";
    ```  
  
 <span data-ttu-id="06fda-146">İlk olarak farklı indirmelerin bitmesini doğrulamak için programı birkaç kez çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="06fda-146">Run the program several times to verify that different downloads finish first.</span></span>  
  
## <a name="complete-example"></a><span data-ttu-id="06fda-147">Tam Örnek</span><span class="sxs-lookup"><span data-stu-id="06fda-147">Complete Example</span></span>  
 <span data-ttu-id="06fda-148">Aşağıdaki kod, örnek için tüm MainWindow.xaml.cs dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="06fda-148">The following code is the complete MainWindow.xaml.cs file for the example.</span></span> <span data-ttu-id="06fda-149">Yıldız işaretleri bu örnek için eklenen öğeleri işaretler.</span><span class="sxs-lookup"><span data-stu-id="06fda-149">Asterisks mark the elements that were added for this example.</span></span>  
  
 <span data-ttu-id="06fda-150">İçin <xref:System.Net.Http>bir başvuru eklemeniz gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="06fda-150">Notice that you must add a reference for <xref:System.Net.Http>.</span></span>  
  
 <span data-ttu-id="06fda-151">Projeyi [zaman uyumsuz örnekten indirebilirsiniz: Uygulamanızı](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)hassas bir şekilde ayarlama.</span><span class="sxs-lookup"><span data-stu-id="06fda-151">You can download the project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="06fda-152">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="06fda-152">See also</span></span>

- <xref:System.Threading.Tasks.Task.WhenAny%2A>
- [<span data-ttu-id="06fda-153">Zaman uyumsuz uygulamanızda ince ayar yapma (C#)</span><span class="sxs-lookup"><span data-stu-id="06fda-153">Fine-Tuning Your Async Application (C#)</span></span>](./fine-tuning-your-async-application.md)
- [<span data-ttu-id="06fda-154">Async ve await (C#) ile zaman uyumsuz programlama</span><span class="sxs-lookup"><span data-stu-id="06fda-154">Asynchronous Programming with async and await (C#)</span></span>](./index.md)
- [<span data-ttu-id="06fda-155">Zaman uyumsuz örnek: Uygulamanızda ince ayar yapma</span><span class="sxs-lookup"><span data-stu-id="06fda-155">Async Sample: Fine Tuning Your Application</span></span>](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
