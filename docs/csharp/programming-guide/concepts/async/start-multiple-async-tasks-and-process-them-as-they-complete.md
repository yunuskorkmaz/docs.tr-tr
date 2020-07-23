---
title: Zaman uyumsuz görevleri tamamlarlar işleme
description: Bu örnek, birden çok görevi başlatmak ve sonuçlarını tamamlandığında işlem sırasında işlemek yerine sonuçları işlemek Için C# ' de Task. WhenAny 'ın nasıl kullanılacağını gösterir.
ms.date: 09/12/2018
ms.assetid: 25331850-35a7-43b3-ab76-3908e4346b9d
ms.openlocfilehash: a7cfa0bdf783fe9bb735241ca398fde7895f1493
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925156"
---
# <a name="start-multiple-async-tasks-and-process-them-as-they-complete-c"></a><span data-ttu-id="cf474-103">Birden çok zaman uyumsuz görev başlatma ve bunları tamamlarsa Işleme (C#)</span><span class="sxs-lookup"><span data-stu-id="cf474-103">Start Multiple Async Tasks and Process Them As They Complete (C#)</span></span>

<span data-ttu-id="cf474-104">Kullanarak <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> , aynı anda birden çok görev başlatabilir ve bunları, başlatıldıkları sırada işlemek yerine, bir kez işlem tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="cf474-104">By using <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>, you can start multiple tasks at the same time and process them one by one as they’re completed rather than process them in the order in which they're started.</span></span>

<span data-ttu-id="cf474-105">Aşağıdaki örnek, bir görev koleksiyonu oluşturmak için bir sorgu kullanır.</span><span class="sxs-lookup"><span data-stu-id="cf474-105">The following example uses a query to create a collection of tasks.</span></span> <span data-ttu-id="cf474-106">Her görev belirtilen bir Web sitesinin içeriğini indirir.</span><span class="sxs-lookup"><span data-stu-id="cf474-106">Each task downloads the contents of a specified website.</span></span> <span data-ttu-id="cf474-107">Bir while döngüsünün her yinelemesinde, geri beklenmiş bir çağrı, `WhenAny` önce indirmeyi izleyen görevler koleksiyonundaki görevi döndürür.</span><span class="sxs-lookup"><span data-stu-id="cf474-107">In each iteration of a while loop, an awaited call to `WhenAny` returns the task in the collection of tasks that finishes its download first.</span></span> <span data-ttu-id="cf474-108">Bu görev koleksiyondan kaldırılır ve işlenir.</span><span class="sxs-lookup"><span data-stu-id="cf474-108">That task is removed from the collection and processed.</span></span> <span data-ttu-id="cf474-109">Döngü, koleksiyon daha fazla görev içerene kadar yinelenir.</span><span class="sxs-lookup"><span data-stu-id="cf474-109">The loop repeats until the collection contains no more tasks.</span></span>

> [!NOTE]
> <span data-ttu-id="cf474-110">Örnekleri çalıştırmak için, bilgisayarınızda Visual Studio (2012 veya üzeri) ve .NET Framework 4,5 ya da daha yeni bir sürümü yüklü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="cf474-110">To run the examples, you must have Visual Studio (2012 or newer) and the .NET Framework 4.5 or newer installed on your computer.</span></span>

## <a name="download-an-example-solution"></a><span data-ttu-id="cf474-111">Örnek çözüm indirin</span><span class="sxs-lookup"><span data-stu-id="cf474-111">Download an example solution</span></span>

<span data-ttu-id="cf474-112">Tüm Windows Presentation Foundation (WPF) projesini [zaman uyumsuz örnekten indirebilirsiniz: uygulamanızı Ince ayar](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) yapın ve ardından aşağıdaki adımları izleyin.</span><span class="sxs-lookup"><span data-stu-id="cf474-112">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span></span>

> [!TIP]
> <span data-ttu-id="cf474-113">Projeyi indirmek istemiyorsanız, bunun yerine bu konunun sonundaki *MainWindow.xaml.cs* dosyasını gözden geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cf474-113">If you don't want to download the project, you can review the *MainWindow.xaml.cs* file at the end of this topic instead.</span></span>

1. <span data-ttu-id="cf474-114">İndirdiğiniz dosyaları *. zip* dosyasından ayıklayın ve ardından Visual Studio 'yu başlatın.</span><span class="sxs-lookup"><span data-stu-id="cf474-114">Extract the files that you downloaded from the *.zip* file, and then start Visual Studio.</span></span>

2. <span data-ttu-id="cf474-115">Menü çubuğunda **Dosya**  >  **Aç**  >  **Proje/çözüm**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="cf474-115">On the menu bar, choose **File** > **Open** > **Project/Solution**.</span></span>

3. <span data-ttu-id="cf474-116">**Proje Aç** iletişim kutusunda, indirdiğiniz örnek kodu tutan klasörü açın ve ardından *AsyncFineTuningCS\*\*.sln* / *AsyncFineTuningVB*için çözüm (. sln) dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="cf474-116">In the **Open Project** dialog box, open the folder that holds the sample code you downloaded, and then open the solution (*.sln*) file for *AsyncFineTuningCS*/*AsyncFineTuningVB*.</span></span>

4. <span data-ttu-id="cf474-117">**Çözüm Gezgini**' de, **Processtasksastheyıfinish** projesinin kısayol menüsünü açın ve ardından **Başlangıç projesi olarak ayarla**' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="cf474-117">In **Solution Explorer**, open the shortcut menu for the **ProcessTasksAsTheyFinish** project, and then choose **Set as StartUp Project**.</span></span>

5. <span data-ttu-id="cf474-118">Programı hata ayıklamayla çalıştırmak için <kbd>F5</kbd> tuşunu seçin veya <kbd>Ctrl</kbd> + programı hata ayıklamadan çalıştırmak için CTRL<kbd>F5</kbd> tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="cf474-118">Choose the <kbd>F5</kbd> key to run the program with debugging or, press <kbd>Ctrl</kbd>+<kbd>F5</kbd> keys to run the program without debugging it.</span></span>

6. <span data-ttu-id="cf474-119">İndirilen uzunluklarının her zaman aynı sırada görünmediğini doğrulamak için projeyi birkaç kez çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="cf474-119">Run the project several times to verify that the downloaded lengths don't always appear in the same order.</span></span>

## <a name="create-the-program-yourself"></a><span data-ttu-id="cf474-120">Programı kendiniz oluşturun</span><span class="sxs-lookup"><span data-stu-id="cf474-120">Create the program yourself</span></span>

<span data-ttu-id="cf474-121">Bu örnek, [bir tane tamamlandıktan sonra kalan zaman uyumsuz görevleri Iptal etme](cancel-remaining-async-tasks-after-one-is-complete.md)bölümünde geliştirilen koda ekler (C#) ve aynı kullanıcı arabirimini kullanır.</span><span class="sxs-lookup"><span data-stu-id="cf474-121">This example adds to the code that’s developed in [Cancel Remaining Async Tasks after One Is Complete (C#)](cancel-remaining-async-tasks-after-one-is-complete.md), and it uses the same UI.</span></span>

<span data-ttu-id="cf474-122">Örneği kendiniz oluşturmak için, örnek ' i [karşıdan yükleme](cancel-remaining-async-tasks-after-one-is-complete.md#downloading-the-example) bölümündeki yönergeleri izleyin, ancak başlangıç projesi olarak, bir **erteleme görevi** ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="cf474-122">To build the example yourself, step by step, follow the instructions in the [Downloading the Example](cancel-remaining-async-tasks-after-one-is-complete.md#downloading-the-example) section, but set **CancelAfterOneTask** as the startup project.</span></span> <span data-ttu-id="cf474-123">Bu konudaki değişiklikleri bu `AccessTheWebAsync` projedeki yöntemine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="cf474-123">Add the changes in this topic to the `AccessTheWebAsync` method in that project.</span></span> <span data-ttu-id="cf474-124">Değişiklikler yıldız işaretiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="cf474-124">The changes are marked with asterisks.</span></span>

<span data-ttu-id="cf474-125">Bu **görev** projesi, yürütüldüğünde bir görev koleksiyonu oluşturduğunda zaten bir sorgu içeriyor.</span><span class="sxs-lookup"><span data-stu-id="cf474-125">The **CancelAfterOneTask** project already includes a query that, when executed, creates a collection of tasks.</span></span> <span data-ttu-id="cf474-126">Aşağıdaki kodda öğesine yapılan her çağrı `ProcessURLAsync` <xref:System.Threading.Tasks.Task%601> , bir `TResult` tam sayı olan bir döndürür:</span><span class="sxs-lookup"><span data-stu-id="cf474-126">Each call to `ProcessURLAsync` in the following code returns a <xref:System.Threading.Tasks.Task%601>, where `TResult` is an integer:</span></span>

```csharp
IEnumerable<Task<int>> downloadTasksQuery = from url in urlList select ProcessURL(url, client, ct);
```

<span data-ttu-id="cf474-127">Projenin *MainWindow.xaml.cs* dosyasında, yönteminde aşağıdaki değişiklikleri yapın `AccessTheWebAsync` :</span><span class="sxs-lookup"><span data-stu-id="cf474-127">In the *MainWindow.xaml.cs* file of the project, make the following changes to the `AccessTheWebAsync` method:</span></span>

- <span data-ttu-id="cf474-128">Yerine uygulayarak sorguyu yürütün <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> <xref:System.Linq.Enumerable.ToArray%2A> .</span><span class="sxs-lookup"><span data-stu-id="cf474-128">Execute the query by applying <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> instead of <xref:System.Linq.Enumerable.ToArray%2A>.</span></span>

    ```csharp
    List<Task<int>> downloadTasks = downloadTasksQuery.ToList();
    ```

- <span data-ttu-id="cf474-129">`while`Koleksiyondaki her görev için aşağıdaki adımları gerçekleştiren bir döngü ekleyin:</span><span class="sxs-lookup"><span data-stu-id="cf474-129">Add a `while` loop that performs the following steps for each task in the collection:</span></span>

    1. <span data-ttu-id="cf474-130">Bu, `WhenAny` indirme işleminin sona ermesi için koleksiyondaki ilk görevi tanımlamak üzere öğesine bir çağrıyı bekler.</span><span class="sxs-lookup"><span data-stu-id="cf474-130">Awaits a call to `WhenAny` to identify the first task in the collection to finish its download.</span></span>

        ```csharp
        Task<int> firstFinishedTask = await Task.WhenAny(downloadTasks);
        ```

    2. <span data-ttu-id="cf474-131">Bu görevi koleksiyondan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="cf474-131">Removes that task from the collection.</span></span>

        ```csharp
        downloadTasks.Remove(firstFinishedTask);
        ```

    3. <span data-ttu-id="cf474-132">`firstFinishedTask`Bir çağrısıyla döndürülen await `ProcessURLAsync` .</span><span class="sxs-lookup"><span data-stu-id="cf474-132">Awaits `firstFinishedTask`, which is returned by a call to `ProcessURLAsync`.</span></span> <span data-ttu-id="cf474-133">`firstFinishedTask`Değişkeni bir <xref:System.Threading.Tasks.Task%601> WHERE `TReturn` tamsayıdır.</span><span class="sxs-lookup"><span data-stu-id="cf474-133">The `firstFinishedTask` variable is a <xref:System.Threading.Tasks.Task%601> where `TReturn` is an integer.</span></span> <span data-ttu-id="cf474-134">Görev zaten tamamlanmış, ancak aşağıdaki örnekte gösterildiği gibi, indirilen Web sitesinin uzunluğunu almak için bu işlemi beklediniz.</span><span class="sxs-lookup"><span data-stu-id="cf474-134">The task is already complete, but you await it to retrieve the length of the downloaded website, as the following example shows.</span></span> <span data-ttu-id="cf474-135">Görev hata verdiyse, ' `await` de bulunan `AggregateException` özelliği okumaktan farklı olarak, içinde depolanan ilk alt özel durumu oluşturur `Result` `AggregateException` .</span><span class="sxs-lookup"><span data-stu-id="cf474-135">If the task is faulted, `await` will throw the first child exception stored in the `AggregateException`, unlike reading the `Result` property which would throw the `AggregateException`.</span></span>

        ```csharp
        int length = await firstFinishedTask;
        resultsTextBox.Text += $"\r\nLength of the download:  {length}";
        ```

<span data-ttu-id="cf474-136">İndirilen uzunluklarının her zaman aynı sırada görünmediğini doğrulamak için programı birkaç kez çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="cf474-136">Run the program several times to verify that the downloaded lengths don't always appear in the same order.</span></span>

> [!CAUTION]
> <span data-ttu-id="cf474-137">`WhenAny`Az sayıda görevle ilgili sorunları gidermek için örnekte açıklandığı gibi bir döngüde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cf474-137">You can use `WhenAny` in a loop, as described in the example, to solve problems that involve a small number of tasks.</span></span> <span data-ttu-id="cf474-138">Ancak, işlemek için çok sayıda göreviniz varsa diğer yaklaşımlar daha etkilidir.</span><span class="sxs-lookup"><span data-stu-id="cf474-138">However, other approaches are more efficient if you have a large number of tasks to process.</span></span> <span data-ttu-id="cf474-139">Daha fazla bilgi ve örnek için bkz. [görevleri tamamladıklarında işleme](https://devblogs.microsoft.com/pfxteam/processing-tasks-as-they-complete/).</span><span class="sxs-lookup"><span data-stu-id="cf474-139">For more information and examples, see [Processing tasks as they complete](https://devblogs.microsoft.com/pfxteam/processing-tasks-as-they-complete/).</span></span>

## <a name="complete-example"></a><span data-ttu-id="cf474-140">Örnek Tamam</span><span class="sxs-lookup"><span data-stu-id="cf474-140">Complete example</span></span>

<span data-ttu-id="cf474-141">Aşağıdaki kod, örnek için *MainWindow.xaml.cs* dosyasının tüm metinkodudur.</span><span class="sxs-lookup"><span data-stu-id="cf474-141">The following code is the complete text of the *MainWindow.xaml.cs* file for the example.</span></span> <span data-ttu-id="cf474-142">Yıldız işaretleri bu örnek için eklenen öğeleri işaretler.</span><span class="sxs-lookup"><span data-stu-id="cf474-142">Asterisks mark the elements that were added for this example.</span></span> <span data-ttu-id="cf474-143">Ayrıca, için bir başvuru eklemeniz gerektiğini unutmayın <xref:System.Net.Http> .</span><span class="sxs-lookup"><span data-stu-id="cf474-143">Also, take note that you must add a reference for <xref:System.Net.Http>.</span></span>

<span data-ttu-id="cf474-144">Projeyi [zaman uyumsuz örnekten indirebilirsiniz: uygulamanızı hassas bir şekilde ayarlama](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span><span class="sxs-lookup"><span data-stu-id="cf474-144">You can download the project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>

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

## <a name="see-also"></a><span data-ttu-id="cf474-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cf474-145">See also</span></span>

- <xref:System.Threading.Tasks.Task.WhenAny%2A>
- [<span data-ttu-id="cf474-146">Zaman uyumsuz uygulamanızda ince ayar yapma (C#)</span><span class="sxs-lookup"><span data-stu-id="cf474-146">Fine-Tuning Your Async Application (C#)</span></span>](fine-tuning-your-async-application.md)
- [<span data-ttu-id="cf474-147">Async ve await ile zaman uyumsuz programlama (C#)</span><span class="sxs-lookup"><span data-stu-id="cf474-147">Asynchronous Programming with async and await (C#)</span></span>](index.md)
- [<span data-ttu-id="cf474-148">Zaman uyumsuz örnek: uygulamanıza Ince ayar yapma</span><span class="sxs-lookup"><span data-stu-id="cf474-148">Async Sample: Fine Tuning Your Application</span></span>](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
