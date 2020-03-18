---
title: Bir Süre Sonra Async Görevlerini İptal Etme (C#)
ms.date: 07/20/2015
ms.assetid: 194282c2-399f-46da-a7a6-96674e00b0b3
ms.openlocfilehash: 110c4700d0d2afc87f9144bf258cdd4991f107f4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "70204341"
---
# <a name="cancel-async-tasks-after-a-period-of-time-c"></a><span data-ttu-id="066f4-102">Belirli bir süre sonra async görevlerini iptal etme (C#)</span><span class="sxs-lookup"><span data-stu-id="066f4-102">Cancel async tasks after a period of time (C#)</span></span>

<span data-ttu-id="066f4-103">İşlemin tamamlanmasını beklemek istemiyorsanız <xref:System.Threading.CancellationTokenSource.CancelAfter%2A?displayProperty=nameWithType> yöntemi kullanarak bir süre sonra bir eşzamanlı işlemi iptal edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="066f4-103">You can cancel an asynchronous operation after a period of time by using the  <xref:System.Threading.CancellationTokenSource.CancelAfter%2A?displayProperty=nameWithType> method if you don't want to wait for the operation to finish.</span></span> <span data-ttu-id="066f4-104">Bu yöntem, ifade tarafından belirlenen süre içinde tamamlanmamış ilişkili görevlerin iptalini `CancelAfter` planlar.</span><span class="sxs-lookup"><span data-stu-id="066f4-104">This method schedules the cancellation of any associated tasks that aren’t complete within the period of time that’s designated by the `CancelAfter` expression.</span></span>

<span data-ttu-id="066f4-105">Bu örnek, web sitelerinin listesini indirmek ve her birinin içeriğinin uzunluğunu görüntülemek için [Bir Async Görevi İptal'de veya Görev Listesi'nde (C#)](./cancel-an-async-task-or-a-list-of-tasks.md) geliştirilen koda eklenir.</span><span class="sxs-lookup"><span data-stu-id="066f4-105">This example adds to the code that’s developed in [Cancel an Async Task or a List of Tasks (C#)](./cancel-an-async-task-or-a-list-of-tasks.md) to download a list of websites and to display the length of the contents of each one.</span></span>

> [!NOTE]
> <span data-ttu-id="066f4-106">Örnekleri çalıştırmak için Visual Studio 2012 veya daha yeni ve .NET Framework 4.5 veya daha yeni bilgisayarınıza yüklü olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="066f4-106">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>

## <a name="download-the-example"></a><span data-ttu-id="066f4-107">Örneği indirin</span><span class="sxs-lookup"><span data-stu-id="066f4-107">Download the example</span></span>

<span data-ttu-id="066f4-108">Windows Presentation Foundation (WPF) projesinin tamamını [Async Sample: Fine Tuning Application'dan](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) indirebilir ve ardından aşağıdaki adımları izleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="066f4-108">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span></span>

1. <span data-ttu-id="066f4-109">İndirdiğiniz dosyayı sıkıştırın ve Visual Studio'yu başlatın.</span><span class="sxs-lookup"><span data-stu-id="066f4-109">Decompress the file that you downloaded, and then start Visual Studio.</span></span>

2. <span data-ttu-id="066f4-110">Menü çubuğunda **Dosya** > **Aç** > **Projesi/Çözümü'nü**seçin.</span><span class="sxs-lookup"><span data-stu-id="066f4-110">On the menu bar, choose **File** > **Open** > **Project/Solution**.</span></span>

3. <span data-ttu-id="066f4-111">**Projeyi Aç** iletişim kutusunda, sıkıştırdığınız örnek kodu tutan klasörü açın ve ardından AsyncFineTuningCS için çözüm (.sln) dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="066f4-111">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningCS.</span></span>

4. <span data-ttu-id="066f4-112">**Solution**Explorer'da, **CancelAfterTime** projesinin kısayol menüsünü açın ve ardından **StartUp Project olarak ayarla'yı**seçin.</span><span class="sxs-lookup"><span data-stu-id="066f4-112">In **Solution Explorer**, open the shortcut menu for the **CancelAfterTime** project, and then choose **Set as StartUp Project**.</span></span>

5. <span data-ttu-id="066f4-113">Projeyi çalıştırmak için **F5** tuşunu seçin.</span><span class="sxs-lookup"><span data-stu-id="066f4-113">Choose the **F5** key to run the project.</span></span> <span data-ttu-id="066f4-114">(Veya, hata ayıklama olmadan projeçalıştırmak için **Ctrl**+**F5** tuşuna basın).</span><span class="sxs-lookup"><span data-stu-id="066f4-114">(Or, press **Ctrl**+**F5** to run the project without debugging it).</span></span>

6. <span data-ttu-id="066f4-115">Çıktının tüm web siteleri, hiçbir web sitesi veya bazı web siteleri için çıktı gösterebileceğini doğrulamak için programı birkaç kez çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="066f4-115">Run the program several times to verify that the output might show output for all websites, no websites, or some web sites.</span></span>

<span data-ttu-id="066f4-116">Projeyi indirmek istemiyorsanız, bu konunun sonundaki MainWindow.xaml.cs dosyasını gözden geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="066f4-116">If you don't want to download the project, you can review the MainWindow.xaml.cs file at the end of this topic.</span></span>

## <a name="build-the-example"></a><span data-ttu-id="066f4-117">Örneği derleme</span><span class="sxs-lookup"><span data-stu-id="066f4-117">Build the example</span></span>

<span data-ttu-id="066f4-118">Bu konuyla ilgili örnek, görev listesini iptal etmek için Bir Async Görevi İptal Etme [veya Görev Listesi (C#)](./cancel-an-async-task-or-a-list-of-tasks.md) olarak geliştirilen projeye eklenir.</span><span class="sxs-lookup"><span data-stu-id="066f4-118">The example in this topic adds to the project that's developed in [Cancel an Async Task or a List of Tasks (C#)](./cancel-an-async-task-or-a-list-of-tasks.md) to cancel a list of tasks.</span></span> <span data-ttu-id="066f4-119">**İptal** düğmesi açıkça kullanılmasa da, örnek aynı UI'yi kullanır.</span><span class="sxs-lookup"><span data-stu-id="066f4-119">The example uses the same UI, although the **Cancel** button isn’t used explicitly.</span></span>

<span data-ttu-id="066f4-120">Örneği adım adım oluşturmak için, "Örneği İndirme" bölümündeki yönergeleri izleyin, ancak **StartUp Project**olarak **CancelAListOfTasks'i** seçin.</span><span class="sxs-lookup"><span data-stu-id="066f4-120">To build the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **CancelAListOfTasks** as the **StartUp Project**.</span></span> <span data-ttu-id="066f4-121">Bu konudaki değişiklikleri bu projeye ekleyin.</span><span class="sxs-lookup"><span data-stu-id="066f4-121">Add the changes in this topic to that project.</span></span>

<span data-ttu-id="066f4-122">Görevler iptal edildiolarak işaretlenmeden önce en büyük süreyi `startButton_Click`belirtmek için, `CancelAfter` aşağıdaki örnekte görüldüğü gibi bir çağrı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="066f4-122">To specify a maximum time before the tasks are marked as canceled, add a call to `CancelAfter` to `startButton_Click`, as the following example shows.</span></span> <span data-ttu-id="066f4-123">Ek yıldız işaretleri ile işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="066f4-123">The addition is marked with asterisks.</span></span>

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

 <span data-ttu-id="066f4-124">Çıktının tüm web siteleri, hiçbir web sitesi veya bazı web siteleri için çıktı gösterebileceğini doğrulamak için programı birkaç kez çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="066f4-124">Run the program several times to verify that the output might show output for all websites, no websites, or some web sites.</span></span> <span data-ttu-id="066f4-125">Aşağıdaki çıktı bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="066f4-125">The following output is a sample.</span></span>

```output
Length of the downloaded string: 35990.

Length of the downloaded string: 407399.

Length of the downloaded string: 226091.

Downloads canceled.
```

## <a name="complete-example"></a><span data-ttu-id="066f4-126">Tam örnek</span><span class="sxs-lookup"><span data-stu-id="066f4-126">Complete example</span></span>

<span data-ttu-id="066f4-127">Aşağıdaki kod, örnek için MainWindow.xaml.cs dosyasının tam metnidir.</span><span class="sxs-lookup"><span data-stu-id="066f4-127">The following code is the complete text of the MainWindow.xaml.cs file for the example.</span></span> <span data-ttu-id="066f4-128">Yıldız işaretleri, bu örnek için eklenen öğeleri işaretler.</span><span class="sxs-lookup"><span data-stu-id="066f4-128">Asterisks mark the elements that were added for this example.</span></span>

<span data-ttu-id="066f4-129">Için bir başvuru eklemeniz <xref:System.Net.Http>gerektiğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="066f4-129">Notice that you must add a reference for <xref:System.Net.Http>.</span></span>

<span data-ttu-id="066f4-130">Projeyi [Async Sample: Fine Tuning Application'dan](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="066f4-130">You can download the project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>

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
                    $"\r\nLength of the downloaded string: {urlContents.Length}.\r\n";
            }
        }

        private List<string> SetUpURLList()
        {
            List<string> urls = new List<string>
            {
                "https://msdn.microsoft.com",
                "https://msdn.microsoft.com/library/windows/apps/br211380.aspx",
                "https://msdn.microsoft.com/library/hh290136.aspx",
                "https://msdn.microsoft.com/library/ee256749.aspx",
                "https://msdn.microsoft.com/library/ms404677.aspx",
                "https://msdn.microsoft.com/library/ff730837.aspx"
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

## <a name="see-also"></a><span data-ttu-id="066f4-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="066f4-131">See also</span></span>

- [<span data-ttu-id="066f4-132">Async ve await ile Asynchronous Programlama (C#)</span><span class="sxs-lookup"><span data-stu-id="066f4-132">Asynchronous Programming with async and await (C#)</span></span>](./index.md)
- [<span data-ttu-id="066f4-133">Walkthrough: Async kullanarak Web'e erişim ve bekleme (C#)</span><span class="sxs-lookup"><span data-stu-id="066f4-133">Walkthrough: Accessing the Web by Using async and await (C#)</span></span>](./walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="066f4-134">Bir Async Görevi veya Görev Listesini İptal Etme (C#)</span><span class="sxs-lookup"><span data-stu-id="066f4-134">Cancel an Async Task or a List of Tasks (C#)</span></span>](./cancel-an-async-task-or-a-list-of-tasks.md)
- [<span data-ttu-id="066f4-135">Async Uygulamanızda İnce Ayar (C#)</span><span class="sxs-lookup"><span data-stu-id="066f4-135">Fine-Tuning Your Async Application (C#)</span></span>](./fine-tuning-your-async-application.md)
- [<span data-ttu-id="066f4-136">Async Örnek: Uygulamanızı İyi Ayar</span><span class="sxs-lookup"><span data-stu-id="066f4-136">Async Sample: Fine Tuning Your Application</span></span>](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
