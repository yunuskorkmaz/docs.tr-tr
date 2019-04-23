---
title: Zaman uyumsuz görevleri tamamlandıkça işleme
ms.date: 09/12/2018
ms.assetid: 25331850-35a7-43b3-ab76-3908e4346b9d
ms.openlocfilehash: 335eb5dce74a7f0a2b8af550250105d460212b6a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59304864"
---
# <a name="start-multiple-async-tasks-and-process-them-as-they-complete-c"></a><span data-ttu-id="22b30-102">Birden çok zaman uyumsuz görev başlatma ve bunlar (C#) tamamlandıkça işleme</span><span class="sxs-lookup"><span data-stu-id="22b30-102">Start Multiple Async Tasks and Process Them As They Complete (C#)</span></span>

<span data-ttu-id="22b30-103">Kullanarak <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>, birden çok görev aynı anda başlatmak ve bunların yerine gibi bunlar başlatıldığında sırayla işlenecekleri birer birer işlem.</span><span class="sxs-lookup"><span data-stu-id="22b30-103">By using <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>, you can start multiple tasks at the same time and process them one by one as they’re completed rather than process them in the order in which they're started.</span></span>

<span data-ttu-id="22b30-104">Aşağıdaki örnek, bir görev koleksiyonu oluşturmak için bir sorgu kullanır.</span><span class="sxs-lookup"><span data-stu-id="22b30-104">The following example uses a query to create a collection of tasks.</span></span> <span data-ttu-id="22b30-105">Her görev, belirtilen bir Web sitesinin içeriklerini karşıdan yükler.</span><span class="sxs-lookup"><span data-stu-id="22b30-105">Each task downloads the contents of a specified website.</span></span> <span data-ttu-id="22b30-106">Her yinelemede while döngüsü, bekletilen çağrısı `WhenAny` görev, kendi indirmesi biten koleksiyonundaki görevleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="22b30-106">In each iteration of a while loop, an awaited call to `WhenAny` returns the task in the collection of tasks that finishes its download first.</span></span> <span data-ttu-id="22b30-107">Bu görev koleksiyondan kaldırılır ve işlenir.</span><span class="sxs-lookup"><span data-stu-id="22b30-107">That task is removed from the collection and processed.</span></span> <span data-ttu-id="22b30-108">Döngü koleksiyonda artık başka görev kalmayana kadar yinelenir.</span><span class="sxs-lookup"><span data-stu-id="22b30-108">The loop repeats until the collection contains no more tasks.</span></span>

> [!NOTE]
> <span data-ttu-id="22b30-109">Yeni bilgisayarınızda yüklü veya örnekleri çalıştırmak için (2012 veya sonrası) Visual Studio ve .NET Framework 4.5 yüklü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="22b30-109">To run the examples, you must have Visual Studio (2012 or newer) and the .NET Framework 4.5 or newer installed on your computer.</span></span>

## <a name="download-an-example-solution"></a><span data-ttu-id="22b30-110">Bir örnek çözümü indirin</span><span class="sxs-lookup"><span data-stu-id="22b30-110">Download an example solution</span></span>

<span data-ttu-id="22b30-111">Tüm Windows Presentation Foundation (WPF) projeden indirebileceğiniz [zaman uyumsuz örneği: Uygulamanıza ince](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) ve sonra aşağıdaki adımları izleyin.</span><span class="sxs-lookup"><span data-stu-id="22b30-111">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span></span>

> [!TIP]
> <span data-ttu-id="22b30-112">Projeyi indirmek istemiyorsanız, bunun yerine bu konunun sonunda MainWindow.xaml.cs dosyasını gözden geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="22b30-112">If you don't want to download the project, you can review the MainWindow.xaml.cs file at the end of this topic instead.</span></span>

1. <span data-ttu-id="22b30-113">Yüklediğiniz .zip dosyasından dosyaları ayıklayın ve sonra Visual Studio'yu başlatın.</span><span class="sxs-lookup"><span data-stu-id="22b30-113">Extract the files that you downloaded from the .zip file, and then start Visual Studio.</span></span>

2. <span data-ttu-id="22b30-114">Menü çubuğunda, **dosya** > **açık** > **proje/çözüm**.</span><span class="sxs-lookup"><span data-stu-id="22b30-114">On the menu bar, choose **File** > **Open** > **Project/Solution**.</span></span>

3. <span data-ttu-id="22b30-115">İçinde **Proje Aç** iletişim kutusunda, indirdiğiniz örnek kodu barındıran klasörü açın ve ardından AsyncFineTuningCS için çözüm (.sln) dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="22b30-115">In the **Open Project** dialog box, open the folder that holds the sample code you downloaded, and then open the solution (.sln) file for AsyncFineTuningCS.</span></span>

4. <span data-ttu-id="22b30-116">İçinde **Çözüm Gezgini**, kısayol menüsünü açın **ProcessTasksAsTheyFinish** proje ve ardından **başlangıç projesi olarak ayarla**.</span><span class="sxs-lookup"><span data-stu-id="22b30-116">In **Solution Explorer**, open the shortcut menu for the **ProcessTasksAsTheyFinish** project, and then choose **Set as StartUp Project**.</span></span>

5. <span data-ttu-id="22b30-117">Seçin **F5** programı çalıştırmak için anahtar (veya basın **Ctrl**+**F5** anahtarları, hata ayıklama olmadan programı çalıştırmak için).</span><span class="sxs-lookup"><span data-stu-id="22b30-117">Choose the **F5** key to run the program (or, press **Ctrl**+**F5** keys to run the program without debugging it).</span></span>

6. <span data-ttu-id="22b30-118">Proje, indirilen uzunlukların her zaman aynı sırada görüntülenmediğini doğrulamak için birkaç kez çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="22b30-118">Run the project several times to verify that the downloaded lengths don't always appear in the same order.</span></span>

## <a name="create-the-program-yourself"></a><span data-ttu-id="22b30-119">Programı kendiniz oluşturun</span><span class="sxs-lookup"><span data-stu-id="22b30-119">Create the program yourself</span></span>

<span data-ttu-id="22b30-120">Bu örnek içinde geliştirilen koda eklenir [sonra bir tamamlandı (C#) kalan zaman uyumsuz görevleri iptal](../../../../csharp/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md), ve aynı kullanıcı arabirimini kullanır.</span><span class="sxs-lookup"><span data-stu-id="22b30-120">This example adds to the code that’s developed in [Cancel Remaining Async Tasks after One Is Complete (C#)](../../../../csharp/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md), and it uses the same UI.</span></span>

<span data-ttu-id="22b30-121">Kendiniz adım adım örnek oluşturmak için aşağıdaki yönergeleri izleyin [örneği indirme](../../../../csharp/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md#downloading-the-example) bölümünde, ancak ayarlanmış **CancelAfterOneTask** başlangıç projesi olarak.</span><span class="sxs-lookup"><span data-stu-id="22b30-121">To build the example yourself, step by step, follow the instructions in the [Downloading the Example](../../../../csharp/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md#downloading-the-example) section, but set **CancelAfterOneTask** as the startup project.</span></span> <span data-ttu-id="22b30-122">Bu konudaki değişiklikleri ekleyin `AccessTheWebAsync` projedeki yöntemi.</span><span class="sxs-lookup"><span data-stu-id="22b30-122">Add the changes in this topic to the `AccessTheWebAsync` method in that project.</span></span> <span data-ttu-id="22b30-123">Değişiklikler, yıldız işareti ile işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="22b30-123">The changes are marked with asterisks.</span></span>

<span data-ttu-id="22b30-124">**CancelAfterOneTask** proje zaten bir sorgu içerir, çalıştırıldığında bir görev koleksiyonu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="22b30-124">The **CancelAfterOneTask** project already includes a query that, when executed, creates a collection of tasks.</span></span> <span data-ttu-id="22b30-125">Her çağrı `ProcessURLAsync` döndürür aşağıdaki kodda bir <xref:System.Threading.Tasks.Task%601>burada `TResult` bir tamsayıdır:</span><span class="sxs-lookup"><span data-stu-id="22b30-125">Each call to `ProcessURLAsync` in the following code returns a <xref:System.Threading.Tasks.Task%601>, where `TResult` is an integer:</span></span>

```csharp
IEnumerable<Task<int>> downloadTasksQuery = from url in urlList select ProcessURL(url, client, ct);
```

<span data-ttu-id="22b30-126">Proje MainWindow.xaml.cs dosyasında aşağıdaki değişiklikleri `AccessTheWebAsync` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="22b30-126">In the MainWindow.xaml.cs file of the project, make the following changes to the `AccessTheWebAsync` method.</span></span>

-   <span data-ttu-id="22b30-127">Uygulayarak sorguyu yürütün <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> yerine <xref:System.Linq.Enumerable.ToArray%2A>.</span><span class="sxs-lookup"><span data-stu-id="22b30-127">Execute the query by applying <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> instead of <xref:System.Linq.Enumerable.ToArray%2A>.</span></span>

    ```csharp
    List<Task<int>> downloadTasks = downloadTasksQuery.ToList();
    ```

-   <span data-ttu-id="22b30-128">Ekleme bir `while` döngü koleksiyondaki her görev için aşağıdaki adımları gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="22b30-128">Add a `while` loop that performs the following steps for each task in the collection:</span></span>

    1.  <span data-ttu-id="22b30-129">Bir çağrı bekler `WhenAny` karşıdan yüklemesini tamamlamak için koleksiyondaki ilk görevi tanımlamak için.</span><span class="sxs-lookup"><span data-stu-id="22b30-129">Awaits a call to `WhenAny` to identify the first task in the collection to finish its download.</span></span>

        ```csharp
        Task<int> firstFinishedTask = await Task.WhenAny(downloadTasks);
        ```

    2.  <span data-ttu-id="22b30-130">Bu görev koleksiyondan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="22b30-130">Removes that task from the collection.</span></span>

        ```csharp
        downloadTasks.Remove(firstFinishedTask);
        ```

    3.  <span data-ttu-id="22b30-131">Bekler `firstFinishedTask`, bir çağrı tarafından döndürülen `ProcessURLAsync`.</span><span class="sxs-lookup"><span data-stu-id="22b30-131">Awaits `firstFinishedTask`, which is returned by a call to `ProcessURLAsync`.</span></span> <span data-ttu-id="22b30-132">`firstFinishedTask` Değişken bir <xref:System.Threading.Tasks.Task%601> burada `TReturn` bir tamsayıdır.</span><span class="sxs-lookup"><span data-stu-id="22b30-132">The `firstFinishedTask` variable is a <xref:System.Threading.Tasks.Task%601> where `TReturn` is an integer.</span></span> <span data-ttu-id="22b30-133">Görev zaten tamamlandıysa, ancak karşıdan yüklenen Web sitesi uzunluğunu aşağıdaki örnekte gösterildiği gibi almak için bekler.</span><span class="sxs-lookup"><span data-stu-id="22b30-133">The task is already complete, but you await it to retrieve the length of the downloaded website, as the following example shows.</span></span>

        ```csharp
        int length = await firstFinishedTask;
        resultsTextBox.Text += $"\r\nLength of the download:  {length}";
        ```

<span data-ttu-id="22b30-134">İndirilen uzunlukların her zaman aynı sırada görüntülenmediğini doğrulamak için birkaç kez programı'nı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="22b30-134">Run the program several times to verify that the downloaded lengths don't always appear in the same order.</span></span>

> [!CAUTION]
> <span data-ttu-id="22b30-135">Kullanabileceğiniz `WhenAny` az sayıda görev içeren sorunlar çözmek için örnekte açıklandığı bir döngüde.</span><span class="sxs-lookup"><span data-stu-id="22b30-135">You can use `WhenAny` in a loop, as described in the example, to solve problems that involve a small number of tasks.</span></span> <span data-ttu-id="22b30-136">Ancak, diğer yaklaşımlar çok sayıda işlemek için görevler varsa daha verimlidir.</span><span class="sxs-lookup"><span data-stu-id="22b30-136">However, other approaches are more efficient if you have a large number of tasks to process.</span></span> <span data-ttu-id="22b30-137">Daha fazla bilgi ve örnekler için bkz. [görevleri tamamlandıkça işleme](https://blogs.msdn.microsoft.com/pfxteam/2012/08/02/processing-tasks-as-they-complete/).</span><span class="sxs-lookup"><span data-stu-id="22b30-137">For more information and examples, see [Processing tasks as they complete](https://blogs.msdn.microsoft.com/pfxteam/2012/08/02/processing-tasks-as-they-complete/).</span></span>

## <a name="complete-example"></a><span data-ttu-id="22b30-138">Tam örnek</span><span class="sxs-lookup"><span data-stu-id="22b30-138">Complete example</span></span>

<span data-ttu-id="22b30-139">Aşağıdaki kod örneği için MainWindow.xaml.cs dosyasının tam metindir.</span><span class="sxs-lookup"><span data-stu-id="22b30-139">The following code is the complete text of the MainWindow.xaml.cs file for the example.</span></span> <span data-ttu-id="22b30-140">Yıldız işaretleri, bu örnek için eklenen öğeleri işaretler.</span><span class="sxs-lookup"><span data-stu-id="22b30-140">Asterisks mark the elements that were added for this example.</span></span> <span data-ttu-id="22b30-141">Ayrıca, bir başvuru için eklemeniz gereken Not <xref:System.Net.Http>.</span><span class="sxs-lookup"><span data-stu-id="22b30-141">Also, take note that you must add a reference for <xref:System.Net.Http>.</span></span>

<span data-ttu-id="22b30-142">Projeden indirebileceğiniz [zaman uyumsuz örneği: Uygulamanızı ince ayar](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span><span class="sxs-lookup"><span data-stu-id="22b30-142">You can download the project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>

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
                    resultsTextBox.Text += $"\r\nLength of the download:  {length}";
            }
        }

        private List<string> SetUpURLList()
        {
            List<string> urls = new List<string>
            {
                "https://msdn.microsoft.com",
                "https://msdn.microsoft.com/library/windows/apps/br211380.aspx",
                "https://msdn.microsoft.com/library/hh290136.aspx",
                "https://msdn.microsoft.com/library/dd470362.aspx",
                "https://msdn.microsoft.com/library/aa578028.aspx",
                "https://msdn.microsoft.com/library/ms404677.aspx",
                "https://msdn.microsoft.com/library/ff730837.aspx"
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

## <a name="see-also"></a><span data-ttu-id="22b30-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="22b30-143">See also</span></span>

- <xref:System.Threading.Tasks.Task.WhenAny%2A>
- [<span data-ttu-id="22b30-144">(C#) Async uygulamanızda hassas ayar yapma</span><span class="sxs-lookup"><span data-stu-id="22b30-144">Fine-Tuning Your Async Application (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md)
- [<span data-ttu-id="22b30-145">Zaman uyumsuz programlama ile async ve await (C#)</span><span class="sxs-lookup"><span data-stu-id="22b30-145">Asynchronous Programming with async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/index.md)
- [<span data-ttu-id="22b30-146">Zaman uyumsuz örneği: Uygulamanızda hassas ayar yapma</span><span class="sxs-lookup"><span data-stu-id="22b30-146">Async Sample: Fine Tuning Your Application</span></span>](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)