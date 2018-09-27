---
title: Bir süre (C#) sonra zaman uyumsuz görevleri iptal etme
ms.date: 07/20/2015
ms.assetid: 194282c2-399f-46da-a7a6-96674e00b0b3
ms.openlocfilehash: b95b87e1e93a9c8f8c74680a917a128d45172ed5
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/27/2018
ms.locfileid: "47397351"
---
# <a name="cancel-async-tasks-after-a-period-of-time-c"></a><span data-ttu-id="5419d-102">Bir süre (C#) sonra zaman uyumsuz görevleri iptal etme</span><span class="sxs-lookup"><span data-stu-id="5419d-102">Cancel async tasks after a period of time (C#)</span></span>

<span data-ttu-id="5419d-103">Kullanarak bir süre sonra Zamanuyumsuz bir işlemi iptal edebilirsiniz <xref:System.Threading.CancellationTokenSource.CancelAfter%2A?displayProperty=nameWithType> işlemin tamamlanmasını beklemek istemiyorsanız yöntemi.</span><span class="sxs-lookup"><span data-stu-id="5419d-103">You can cancel an asynchronous operation after a period of time by using the  <xref:System.Threading.CancellationTokenSource.CancelAfter%2A?displayProperty=nameWithType> method if you don't want to wait for the operation to finish.</span></span> <span data-ttu-id="5419d-104">Bu yöntem tarafından belirlenen süre içinde tam olmayan herhangi bir ilişkili görevin iptalini zamanlar `CancelAfter` ifade.</span><span class="sxs-lookup"><span data-stu-id="5419d-104">This method schedules the cancellation of any associated tasks that aren’t complete within the period of time that’s designated by the `CancelAfter` expression.</span></span>

<span data-ttu-id="5419d-105">Bu örnek içinde geliştirilen koda eklenir [zaman uyumsuz bir görev veya bir liste görevleri (C#) iptal](../../../../csharp/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md) Web sitesi listesini indirmek ve her birindeki içerik uzunluğunu görüntülemek için.</span><span class="sxs-lookup"><span data-stu-id="5419d-105">This example adds to the code that’s developed in [Cancel an Async Task or a List of Tasks (C#)](../../../../csharp/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md) to download a list of websites and to display the length of the contents of each one.</span></span>

> [!NOTE]
> <span data-ttu-id="5419d-106">Yeni bilgisayarınızda yüklü veya örnekleri çalıştırmak için Visual Studio 2012 veya daha yeni ve .NET Framework 4.5 yüklü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5419d-106">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>

## <a name="download-the-example"></a><span data-ttu-id="5419d-107">Örneği indirme</span><span class="sxs-lookup"><span data-stu-id="5419d-107">Download the example</span></span>

<span data-ttu-id="5419d-108">Tüm Windows Presentation Foundation (WPF) projeden indirebileceğiniz [zaman uyumsuz örneği: ince uygulamanıza](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) ve sonra aşağıdaki adımları izleyin.</span><span class="sxs-lookup"><span data-stu-id="5419d-108">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span></span>

1.  <span data-ttu-id="5419d-109">İndirdiğiniz dosyanın sıkıştırmasını açın ve sonra Visual Studio'yu başlatın.</span><span class="sxs-lookup"><span data-stu-id="5419d-109">Decompress the file that you downloaded, and then start Visual Studio.</span></span>

2.  <span data-ttu-id="5419d-110">Menü çubuğunda, **dosya** > **açık** > **proje/çözüm**.</span><span class="sxs-lookup"><span data-stu-id="5419d-110">On the menu bar, choose **File** > **Open** > **Project/Solution**.</span></span>

3.  <span data-ttu-id="5419d-111">İçinde **Proje Aç** iletişim kutusunda, açtığınız örnek kodu barındıran klasörü açın ve ardından AsyncFineTuningCS için çözüm (.sln) dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="5419d-111">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningCS.</span></span>

4.  <span data-ttu-id="5419d-112">İçinde **Çözüm Gezgini**, kısayol menüsünü açın **CancelAfterTime** proje ve ardından **başlangıç projesi olarak ayarla**.</span><span class="sxs-lookup"><span data-stu-id="5419d-112">In **Solution Explorer**, open the shortcut menu for the **CancelAfterTime** project, and then choose **Set as StartUp Project**.</span></span>

5.  <span data-ttu-id="5419d-113">Seçin **F5** projeyi çalıştırmak için anahtar.</span><span class="sxs-lookup"><span data-stu-id="5419d-113">Choose the **F5** key to run the project.</span></span> <span data-ttu-id="5419d-114">(Veya basın **Ctrl**+**F5** projeyi hata ayıklama olmadan çalıştırmak için).</span><span class="sxs-lookup"><span data-stu-id="5419d-114">(Or, press **Ctrl**+**F5** to run the project without debugging it).</span></span>

6.  <span data-ttu-id="5419d-115">Program çıkış tüm Web siteleri, hiçbir Web sitesi veya bazı web siteleri için çıktı gösterebildiğini doğrulamak için birkaç kez çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="5419d-115">Run the program several times to verify that the output might show output for all websites, no websites, or some web sites.</span></span>

<span data-ttu-id="5419d-116">Projeyi indirmek istemiyorsanız, bu konunun sonunda MainWindow.xaml.cs dosyasını gözden geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5419d-116">If you don't want to download the project, you can review the MainWindow.xaml.cs file at the end of this topic.</span></span>

## <a name="build-the-example"></a><span data-ttu-id="5419d-117">Örnek oluşturma</span><span class="sxs-lookup"><span data-stu-id="5419d-117">Build the example</span></span>

<span data-ttu-id="5419d-118">Bu konudaki örnek içinde geliştirilen projeye ekler [zaman uyumsuz bir görev veya bir liste görevleri (C#) iptal](../../../../csharp/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md) Görevler listesini iptal etme.</span><span class="sxs-lookup"><span data-stu-id="5419d-118">The example in this topic adds to the project that's developed in [Cancel an Async Task or a List of Tasks (C#)](../../../../csharp/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md) to cancel a list of tasks.</span></span> <span data-ttu-id="5419d-119">Örnekte aynı Arabirim kullanılmaktadır, ancak **iptal** düğmesi açıkça kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="5419d-119">The example uses the same UI, although the **Cancel** button isn’t used explicitly.</span></span>

<span data-ttu-id="5419d-120">Örneği oluşturmak için kendinize, adım adım "Örneği indirme" bölümündeki yönergeleri izleyin, ancak seçin **CancelAListOfTasks** olarak **başlangıç projesi**.</span><span class="sxs-lookup"><span data-stu-id="5419d-120">To build the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **CancelAListOfTasks** as the **StartUp Project**.</span></span> <span data-ttu-id="5419d-121">Bu konuda, değişiklikleri bu projeye ekleyin.</span><span class="sxs-lookup"><span data-stu-id="5419d-121">Add the changes in this topic to that project.</span></span>

<span data-ttu-id="5419d-122">Görevleri iptal edildi olarak işaretlenmeden önceki süre üst sınırını belirtmek için bir çağrı ekleyin `CancelAfter` için `startButton_Click`aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="5419d-122">To specify a maximum time before the tasks are marked as canceled, add a call to `CancelAfter` to `startButton_Click`, as the following example shows.</span></span> <span data-ttu-id="5419d-123">Ayrıca, yıldız işareti ile işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="5419d-123">The addition is marked with asterisks.</span></span>

```csharp
private async void startButton_Click(object sender, RoutedEventArgs e)
{
    // Instantiate the CancellationTokenSource.
    cts = new CancellationTokenSource();

    resultsTextBox.Clear();

    try
    {
        // ***Set up the CancellationTokenSource to cancel after 2.5 seconds. (You
        // can adjust the time.)
        cts.CancelAfter(2500);

        await AccessTheWebAsync(cts.Token);
        resultsTextBox.Text += "\r\nDownloads succeeded.\r\n";
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
```

 <span data-ttu-id="5419d-124">Program çıkış tüm Web siteleri, hiçbir Web sitesi veya bazı web siteleri için çıktı gösterebildiğini doğrulamak için birkaç kez çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="5419d-124">Run the program several times to verify that the output might show output for all websites, no websites, or some web sites.</span></span> <span data-ttu-id="5419d-125">Aşağıdaki çıktı bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="5419d-125">The following output is a sample.</span></span>

```
Length of the downloaded string: 35990.

Length of the downloaded string: 407399.

Length of the downloaded string: 226091.

Downloads canceled.
```

## <a name="complete-example"></a><span data-ttu-id="5419d-126">Tam örnek</span><span class="sxs-lookup"><span data-stu-id="5419d-126">Complete example</span></span>

<span data-ttu-id="5419d-127">Aşağıdaki kod örneği için MainWindow.xaml.cs dosyasının tam metindir.</span><span class="sxs-lookup"><span data-stu-id="5419d-127">The following code is the complete text of the MainWindow.xaml.cs file for the example.</span></span> <span data-ttu-id="5419d-128">Yıldız işaretleri, bu örnek için eklenen öğeleri işaretler.</span><span class="sxs-lookup"><span data-stu-id="5419d-128">Asterisks mark the elements that were added for this example.</span></span>

<span data-ttu-id="5419d-129">İçin bir başvuru eklemeniz gerektiğini unutmayın <xref:System.Net.Http>.</span><span class="sxs-lookup"><span data-stu-id="5419d-129">Notice that you must add a reference for <xref:System.Net.Http>.</span></span>

<span data-ttu-id="5419d-130">Projeden indirebileceğiniz [zaman uyumsuz örneği: ince uygulamanıza](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span><span class="sxs-lookup"><span data-stu-id="5419d-130">You can download the project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>

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

namespace CancelAfterTime
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
                // ***Set up the CancellationTokenSource to cancel after 2.5 seconds. (You
                // can adjust the time.)
                cts.CancelAfter(2500);

                await AccessTheWebAsync(cts.Token);
                resultsTextBox.Text += "\r\nDownloads succeeded.\r\n";
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

        // You can still include a Cancel button if you want to.
        private void cancelButton_Click(object sender, RoutedEventArgs e)
        {
            if (cts != null)
            {
                cts.Cancel();
            }
        }

        async Task AccessTheWebAsync(CancellationToken ct)
        {
            // Declare an HttpClient object.
            HttpClient client = new HttpClient();

            // Make a list of web addresses.
            List<string> urlList = SetUpURLList();

            foreach (var url in urlList)
            {
                // GetAsync returns a Task<HttpResponseMessage>.
                // Argument ct carries the message if the Cancel button is chosen.
                // Note that the Cancel button cancels all remaining downloads.
                HttpResponseMessage response = await client.GetAsync(url, ct);

                // Retrieve the website contents from the HttpResponseMessage.
                byte[] urlContents = await response.Content.ReadAsByteArrayAsync();

                resultsTextBox.Text +=
                    String.Format("\r\nLength of the downloaded string: {0}.\r\n", urlContents.Length);
            }
        }

        private List<string> SetUpURLList()
        {
            List<string> urls = new List<string>
            {
                "http://msdn.microsoft.com",
                "http://msdn.microsoft.com/library/windows/apps/br211380.aspx",
                "http://msdn.microsoft.com/library/hh290136.aspx",
                "http://msdn.microsoft.com/library/ee256749.aspx",
                "http://msdn.microsoft.com/library/ms404677.aspx",
                "http://msdn.microsoft.com/library/ff730837.aspx"
            };
            return urls;
        }
    }

    // Sample Output:

    // Length of the downloaded string: 35990.

    // Length of the downloaded string: 407399.

    // Length of the downloaded string: 226091.

    // Downloads canceled.
}
```

## <a name="see-also"></a><span data-ttu-id="5419d-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5419d-131">See also</span></span>

- [<span data-ttu-id="5419d-132">Zaman uyumsuz programlama ile async ve await (C#)</span><span class="sxs-lookup"><span data-stu-id="5419d-132">Asynchronous Programming with async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/index.md)
- [<span data-ttu-id="5419d-133">İzlenecek yol: async kullanarak Web'e erişme ve await (C#)</span><span class="sxs-lookup"><span data-stu-id="5419d-133">Walkthrough: Accessing the Web by Using async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="5419d-134">Zaman uyumsuz bir görev veya görevleri (C#) listesini iptal etme</span><span class="sxs-lookup"><span data-stu-id="5419d-134">Cancel an Async Task or a List of Tasks (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md)
- [<span data-ttu-id="5419d-135">(C#) Async uygulamanızda hassas ayar yapma</span><span class="sxs-lookup"><span data-stu-id="5419d-135">Fine-Tuning Your Async Application (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md)
- [<span data-ttu-id="5419d-136">Zaman uyumsuz örneği: Uygulamanıza ince</span><span class="sxs-lookup"><span data-stu-id="5419d-136">Async Sample: Fine Tuning Your Application</span></span>](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
