---
title: Birden çok zaman uyumsuz görev başlatma ve bunlar (C#) tamamlandıkça işleme
ms.date: 07/20/2015
ms.assetid: 25331850-35a7-43b3-ab76-3908e4346b9d
ms.openlocfilehash: 29dc629abae13bb7ba3a9b0cb87300e6d1cbe2d9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33333729"
---
# <a name="start-multiple-async-tasks-and-process-them-as-they-complete-c"></a><span data-ttu-id="2507d-102">Birden çok zaman uyumsuz görev başlatma ve bunlar (C#) tamamlandıkça işleme</span><span class="sxs-lookup"><span data-stu-id="2507d-102">Start Multiple Async Tasks and Process Them As They Complete (C#)</span></span>
<span data-ttu-id="2507d-103">Kullanarak <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>, aynı anda birden çok görevi başlatma ve bunlar tamamlandı yerine bunların başlatılan sırayla işlem onları tek tek işleme.</span><span class="sxs-lookup"><span data-stu-id="2507d-103">By using <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>, you can start multiple tasks at the same time and process them one by one as they’re completed rather than process them in the order in which they're started.</span></span>  
  
 <span data-ttu-id="2507d-104">Aşağıdaki örnek sorguda görevleri koleksiyonu oluşturmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="2507d-104">The following example uses a query to create a collection of tasks.</span></span> <span data-ttu-id="2507d-105">Her görev, belirtilen bir Web sitesi içeriğini indirir.</span><span class="sxs-lookup"><span data-stu-id="2507d-105">Each task downloads the contents of a specified website.</span></span> <span data-ttu-id="2507d-106">Her bir süre tekrarında döngü, awaited çağrısına `WhenAny` görev, kendi yükleme ilk bittikten koleksiyondaki görevlerin döndürür.</span><span class="sxs-lookup"><span data-stu-id="2507d-106">In each iteration of a while loop, an awaited call to `WhenAny` returns the task in the collection of tasks that finishes its download first.</span></span> <span data-ttu-id="2507d-107">Bu görev koleksiyondan kaldırıldı ve işlenebilir.</span><span class="sxs-lookup"><span data-stu-id="2507d-107">That task is removed from the collection and processed.</span></span> <span data-ttu-id="2507d-108">Daha fazla görev koleksiyon içerene kadar döngü tekrarlar.</span><span class="sxs-lookup"><span data-stu-id="2507d-108">The loop repeats until the collection contains no more tasks.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2507d-109">Örnekleri çalıştırmak için Visual Studio 2012 veya daha yeni ve .NET Framework 4.5 olmalıdır veya daha yeni bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="2507d-109">To run the examples, you must have Visual Studio 2012 or newer and  the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
## <a name="downloading-the-example"></a><span data-ttu-id="2507d-110">Örnek indirme</span><span class="sxs-lookup"><span data-stu-id="2507d-110">Downloading the Example</span></span>  
 <span data-ttu-id="2507d-111">Tam Windows Presentation Foundation (WPF) projeden indirebilirsiniz [zaman uyumsuz örnek: ince ayar uygulamanız](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) ve ardından aşağıdaki adımları izleyin.</span><span class="sxs-lookup"><span data-stu-id="2507d-111">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span></span>  
  
1.  <span data-ttu-id="2507d-112">İndirdiğiniz dosyanın sıkıştırmasını ve Visual Studio'yu başlatın.</span><span class="sxs-lookup"><span data-stu-id="2507d-112">Decompress the file that you downloaded, and then start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="2507d-113">Menü çubuğunda seçin **dosya**, **açık**, **proje/çözüm**.</span><span class="sxs-lookup"><span data-stu-id="2507d-113">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
3.  <span data-ttu-id="2507d-114">İçinde **Proje Aç** iletişim kutusunda, sıkıştırması örnek kod tutan klasörü açın ve ardından AsyncFineTuningCS için çözüm (.sln) dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="2507d-114">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningCS.</span></span>  
  
4.  <span data-ttu-id="2507d-115">İçinde **Çözüm Gezgini**, kısayol menüsünü açın **ProcessTasksAsTheyFinish** proje ve ardından **başlangıç projesi olarak ayarla**.</span><span class="sxs-lookup"><span data-stu-id="2507d-115">In **Solution Explorer**, open the shortcut menu for the **ProcessTasksAsTheyFinish** project, and then choose **Set as StartUp Project**.</span></span>  
  
5.  <span data-ttu-id="2507d-116">Projeyi çalıştırmak için F5 tuşuna seçin.</span><span class="sxs-lookup"><span data-stu-id="2507d-116">Choose the F5 key to run the project.</span></span>  
  
     <span data-ttu-id="2507d-117">Hata ayıklama olmadan projeyi çalıştırmak için Ctrl + F5 anahtarları'i seçin.</span><span class="sxs-lookup"><span data-stu-id="2507d-117">Choose the Ctrl+F5 keys to run the project without debugging it.</span></span>  
  
6.  <span data-ttu-id="2507d-118">Proje indirilen uzunlukları her zaman aynı sırada görünmüyor doğrulamak için birkaç kez çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="2507d-118">Run the project several times to verify that the downloaded lengths don't always appear in the same order.</span></span>  
  
 <span data-ttu-id="2507d-119">Projenizi indirin istemiyorsanız, bu konunun sonundaki MainWindow.xaml.cs dosyasını gözden geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2507d-119">If you don't want to download the project, you can review the MainWindow.xaml.cs file at the end of this topic.</span></span>  
  
## <a name="building-the-example"></a><span data-ttu-id="2507d-120">Örnek oluşturma</span><span class="sxs-lookup"><span data-stu-id="2507d-120">Building the Example</span></span>  
 <span data-ttu-id="2507d-121">Bu örnek da geliştirilmiş kod ekler [bir tamamlandı (C#) sonra geri kalan zaman uyumsuz görevleri iptal](../../../../csharp/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)[bir tamamlandı sonra geri kalan zaman uyumsuz görevleri iptal](http://msdn.microsoft.com/library/8e800b58-235a-44b7-a02c-fa4375591d76) ve aynı kullanıcı arabirimini kullanır.</span><span class="sxs-lookup"><span data-stu-id="2507d-121">This example adds to the code that’s developed in [Cancel Remaining Async Tasks after One Is Complete (C#)](../../../../csharp/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)[Cancel Remaining Async Tasks after One Is Complete](http://msdn.microsoft.com/library/8e800b58-235a-44b7-a02c-fa4375591d76) and uses the same UI.</span></span>  
  
 <span data-ttu-id="2507d-122">Örnek oluşturmak için kendiniz, adım adım "örnek indirme" bölümündeki yönergeleri izleyin, ancak seçin **CancelAfterOneTask** olarak **başlangıç projesi**.</span><span class="sxs-lookup"><span data-stu-id="2507d-122">To build the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **CancelAfterOneTask** as the **StartUp Project**.</span></span> <span data-ttu-id="2507d-123">İçin bu konudaki değişiklikleri eklemek `AccessTheWebAsync` projedeki yöntemi.</span><span class="sxs-lookup"><span data-stu-id="2507d-123">Add the changes in this topic to the `AccessTheWebAsync` method in that project.</span></span> <span data-ttu-id="2507d-124">Değişiklikler yıldız işaretiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="2507d-124">The changes are marked with asterisks.</span></span>  
  
 <span data-ttu-id="2507d-125">**CancelAfterOneTask** proje zaten bir sorgu içeriyor, çalıştırıldığında, görevleri koleksiyonu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2507d-125">The **CancelAfterOneTask** project already includes a query that, when executed, creates a collection of tasks.</span></span> <span data-ttu-id="2507d-126">Her çağrı `ProcessURLAsync` aşağıdaki kodda döndüren bir <xref:System.Threading.Tasks.Task%601> burada `TResult` bir tamsayıdır.</span><span class="sxs-lookup"><span data-stu-id="2507d-126">Each call to `ProcessURLAsync` in the following code returns a <xref:System.Threading.Tasks.Task%601> where `TResult` is an integer.</span></span>  
  
```csharp  
IEnumerable<Task<int>> downloadTasksQuery =  
    from url in urlList select ProcessURL(url, client, ct);  
```  
  
 <span data-ttu-id="2507d-127">Proje MainWindow.xaml.cs dosyasında aşağıdaki değişiklikleri `AccessTheWebAsync` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="2507d-127">In the MainWindow.xaml.cs file of the  project, make the following changes to the `AccessTheWebAsync` method.</span></span>  
  
-   <span data-ttu-id="2507d-128">Uygulayarak sorguyu yürütmek <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> yerine <xref:System.Linq.Enumerable.ToArray%2A>.</span><span class="sxs-lookup"><span data-stu-id="2507d-128">Execute the query by applying <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> instead of <xref:System.Linq.Enumerable.ToArray%2A>.</span></span>  
  
    ```csharp  
    List<Task<int>> downloadTasks = downloadTasksQuery.ToList();  
    ```  
  
-   <span data-ttu-id="2507d-129">Biraz eklemek koleksiyondaki her görev için aşağıdaki adımları gerçekleştirir döngü.</span><span class="sxs-lookup"><span data-stu-id="2507d-129">Add a while loop that performs the following steps for each task in the collection.</span></span>  
  
    1.  <span data-ttu-id="2507d-130">Çağrı bekler `WhenAny` kendi indirme tamamlamak için koleksiyondaki ilk görevi tanımlamak için.</span><span class="sxs-lookup"><span data-stu-id="2507d-130">Awaits a call to `WhenAny` to identify the first task in the collection to finish its download.</span></span>  
  
        ```csharp  
        Task<int> firstFinishedTask = await Task.WhenAny(downloadTasks);  
        ```  
  
    2.  <span data-ttu-id="2507d-131">Bu görev koleksiyondan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="2507d-131">Removes that task from the collection.</span></span>  
  
        ```csharp  
        downloadTasks.Remove(firstFinishedTask);  
        ```  
  
    3.  <span data-ttu-id="2507d-132">Bekler `firstFinishedTask`, bir çağrı tarafından döndürülen `ProcessURLAsync`.</span><span class="sxs-lookup"><span data-stu-id="2507d-132">Awaits `firstFinishedTask`, which is returned by a call to `ProcessURLAsync`.</span></span> <span data-ttu-id="2507d-133">`firstFinishedTask` Değişkeni, bir <xref:System.Threading.Tasks.Task%601> burada `TReturn` bir tamsayıdır.</span><span class="sxs-lookup"><span data-stu-id="2507d-133">The `firstFinishedTask` variable is a <xref:System.Threading.Tasks.Task%601> where `TReturn` is an integer.</span></span> <span data-ttu-id="2507d-134">Görev zaten tamamlandı, ancak uzunluğu indirilen Web sitesi, aşağıdaki örnekte gösterildiği gibi almak bekler.</span><span class="sxs-lookup"><span data-stu-id="2507d-134">The task is already complete, but you await it to retrieve the length of the downloaded website, as the following example shows.</span></span>  
  
        ```csharp  
        int length = await firstFinishedTask;  
        resultsTextBox.Text += String.Format("\r\nLength of the download:  {0}", length);  
        ```  
  
 <span data-ttu-id="2507d-135">Proje indirilen uzunlukları her zaman aynı sırada görünmüyor doğrulamak için birkaç kez çalıştırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="2507d-135">You should run the project several times to verify that the downloaded lengths don't always appear in the same order.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="2507d-136">Kullanabileceğiniz `WhenAny` küçük birkaç görev ile ilgili sorunları çözmek için örnekte açıklandığı gibi bir Döngüdeki.</span><span class="sxs-lookup"><span data-stu-id="2507d-136">You can use `WhenAny` in a loop, as described in the example, to solve problems that involve a small number of tasks.</span></span> <span data-ttu-id="2507d-137">Ancak, diğer yaklaşımlar görevler işlemek için çok sayıda varsa daha verimlidir.</span><span class="sxs-lookup"><span data-stu-id="2507d-137">However, other approaches are more efficient if you have a large number of tasks to process.</span></span> <span data-ttu-id="2507d-138">Daha fazla bilgi ve örnekler için bkz: [görevleri tamamlandıkça işleme](https://blogs.msdn.microsoft.com/pfxteam/2012/08/02/processing-tasks-as-they-complete/).</span><span class="sxs-lookup"><span data-stu-id="2507d-138">For more information and examples, see [Processing tasks as they complete](https://blogs.msdn.microsoft.com/pfxteam/2012/08/02/processing-tasks-as-they-complete/).</span></span>  
  
## <a name="complete-example"></a><span data-ttu-id="2507d-139">Tam Örnek</span><span class="sxs-lookup"><span data-stu-id="2507d-139">Complete Example</span></span>  
 <span data-ttu-id="2507d-140">Aşağıdaki kod örneğin MainWindow.xaml.cs dosyasının tam metindir.</span><span class="sxs-lookup"><span data-stu-id="2507d-140">The following code is the complete text of the MainWindow.xaml.cs file for the example.</span></span> <span data-ttu-id="2507d-141">Yıldız işareti, bu örnek için eklenen öğeleri işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="2507d-141">Asterisks mark the elements that were added for this example.</span></span>  
  
 <span data-ttu-id="2507d-142">İçin bir başvuru eklemeniz gerekir fark <xref:System.Net.Http>.</span><span class="sxs-lookup"><span data-stu-id="2507d-142">Notice that you must add a reference for <xref:System.Net.Http>.</span></span>  
  
 <span data-ttu-id="2507d-143">Projeden indirebilirsiniz [zaman uyumsuz örnek: ince ayar uygulamanız](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span><span class="sxs-lookup"><span data-stu-id="2507d-143">You can download the project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>  
  
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
  
namespace ProcessTasksAsTheyFinish  
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
            resultsTextBox.Clear();  
  
            // Instantiate the CancellationTokenSource.  
            cts = new CancellationTokenSource();  
  
            try  
            {  
                await AccessTheWebAsync(cts.Token);  
                resultsTextBox.Text += "\r\nDownloads complete.";  
            }  
            catch (OperationCanceledException)  
            {  
                resultsTextBox.Text += "\r\nDownloads canceled.\r\n";  
            }  
            catch (Exception)  
            {  
                resultsTextBox.Text += "\r\nDownloads failed.\r\n";  
            }  
  
            cts = null;  
        }  
  
        private void cancelButton_Click(object sender, RoutedEventArgs e)  
        {  
            if (cts != null)  
            {  
                cts.Cancel();  
            }  
        }  
  
        async Task AccessTheWebAsync(CancellationToken ct)  
        {  
            HttpClient client = new HttpClient();  
  
            // Make a list of web addresses.  
            List<string> urlList = SetUpURLList();  
  
            // ***Create a query that, when executed, returns a collection of tasks.  
            IEnumerable<Task<int>> downloadTasksQuery =  
                from url in urlList select ProcessURL(url, client, ct);  
  
            // ***Use ToList to execute the query and start the tasks.   
            List<Task<int>> downloadTasks = downloadTasksQuery.ToList();  
  
            // ***Add a loop to process the tasks one at a time until none remain.  
            while (downloadTasks.Count > 0)  
            {  
                    // Identify the first task that completes.  
                    Task<int> firstFinishedTask = await Task.WhenAny(downloadTasks);  
  
                    // ***Remove the selected task from the list so that you don't  
                    // process it more than once.  
                    downloadTasks.Remove(firstFinishedTask);  
  
                    // Await the completed task.  
                    int length = await firstFinishedTask;  
                    resultsTextBox.Text += String.Format("\r\nLength of the download:  {0}", length);  
            }  
        }  
  
        private List<string> SetUpURLList()  
        {  
            List<string> urls = new List<string>   
            {   
                "http://msdn.microsoft.com",  
                "http://msdn.microsoft.com/library/windows/apps/br211380.aspx",  
                "http://msdn.microsoft.com/library/hh290136.aspx",  
                "http://msdn.microsoft.com/library/dd470362.aspx",  
                "http://msdn.microsoft.com/library/aa578028.aspx",  
                "http://msdn.microsoft.com/library/ms404677.aspx",  
                "http://msdn.microsoft.com/library/ff730837.aspx"  
            };  
            return urls;  
        }  
  
        async Task<int> ProcessURL(string url, HttpClient client, CancellationToken ct)  
        {  
            // GetAsync returns a Task<HttpResponseMessage>.   
            HttpResponseMessage response = await client.GetAsync(url, ct);  
  
            // Retrieve the website contents from the HttpResponseMessage.  
            byte[] urlContents = await response.Content.ReadAsByteArrayAsync();  
  
            return urlContents.Length;  
        }  
    }  
}  
  
// Sample Output:  
  
// Length of the download:  226093  
// Length of the download:  412588  
// Length of the download:  175490  
// Length of the download:  204890  
// Length of the download:  158855  
// Length of the download:  145790  
// Length of the download:  44908  
// Downloads complete.  
```  
  
## <a name="see-also"></a><span data-ttu-id="2507d-144">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2507d-144">See Also</span></span>  
 <xref:System.Threading.Tasks.Task.WhenAny%2A>  
 [<span data-ttu-id="2507d-145">(C#) Async uygulamanızda hassas ayar yapma</span><span class="sxs-lookup"><span data-stu-id="2507d-145">Fine-Tuning Your Async Application (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md)  
 [<span data-ttu-id="2507d-146">Zaman uyumsuz programlama ile async ve await (C#)</span><span class="sxs-lookup"><span data-stu-id="2507d-146">Asynchronous Programming with async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/index.md)  
 [<span data-ttu-id="2507d-147">Zaman uyumsuz örnek: İnce uygulamanızı ayarlama</span><span class="sxs-lookup"><span data-stu-id="2507d-147">Async Sample: Fine Tuning Your Application</span></span>](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
