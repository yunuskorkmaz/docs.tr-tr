---
title: Zaman uyumsuz görevleri bir süre sonra iptal et (C#)
ms.date: 07/20/2015
ms.assetid: 194282c2-399f-46da-a7a6-96674e00b0b3
ms.openlocfilehash: e00ff51e987275c6c84822f7095c82ed03b53176
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595764"
---
# <a name="cancel-async-tasks-after-a-period-of-time-c"></a><span data-ttu-id="8bd44-102">Zaman uyumsuz görevleri bir süre sonra iptal et (C#)</span><span class="sxs-lookup"><span data-stu-id="8bd44-102">Cancel async tasks after a period of time (C#)</span></span>

<span data-ttu-id="8bd44-103">İşlemin bitmesini beklemek istemiyorsanız <xref:System.Threading.CancellationTokenSource.CancelAfter%2A?displayProperty=nameWithType> yöntemini kullanarak bir süre sonra zaman uyumsuz bir işlemi iptal edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8bd44-103">You can cancel an asynchronous operation after a period of time by using the  <xref:System.Threading.CancellationTokenSource.CancelAfter%2A?displayProperty=nameWithType> method if you don't want to wait for the operation to finish.</span></span> <span data-ttu-id="8bd44-104">Bu yöntem, `CancelAfter` ifadesi tarafından belirlenen süre içinde tamamlanmamış olan ilişkili görevlerin iptalini zamanlar.</span><span class="sxs-lookup"><span data-stu-id="8bd44-104">This method schedules the cancellation of any associated tasks that aren’t complete within the period of time that’s designated by the `CancelAfter` expression.</span></span>

<span data-ttu-id="8bd44-105">Bu örnek, bir Web sitesi listesini indirmek ve her birinin içerik uzunluğunu göstermek için [zaman uyumsuz bir görevi veyaC#görev listesini () iptal](./cancel-an-async-task-or-a-list-of-tasks.md) etmek üzere geliştirilmiş koda ekler.</span><span class="sxs-lookup"><span data-stu-id="8bd44-105">This example adds to the code that’s developed in [Cancel an Async Task or a List of Tasks (C#)](./cancel-an-async-task-or-a-list-of-tasks.md) to download a list of websites and to display the length of the contents of each one.</span></span>

> [!NOTE]
> <span data-ttu-id="8bd44-106">Örnekleri çalıştırmak için, bilgisayarınızda Visual Studio 2012 veya daha yeni bir sürümü ve .NET Framework 4,5 ya da daha yeni bir sürümü yüklü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8bd44-106">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>

## <a name="download-the-example"></a><span data-ttu-id="8bd44-107">Örneği indirin</span><span class="sxs-lookup"><span data-stu-id="8bd44-107">Download the example</span></span>

<span data-ttu-id="8bd44-108">Tüm Windows Presentation Foundation (WPF) projesini [zaman uyumsuz örnekten indirebilirsiniz: Uygulamanızı](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) hassas ayarlamalar yapın ve ardından aşağıdaki adımları izleyin.</span><span class="sxs-lookup"><span data-stu-id="8bd44-108">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span></span>

1. <span data-ttu-id="8bd44-109">İndirdiğiniz dosyayı sıkıştırmasını açın ve ardından Visual Studio 'Yu başlatın.</span><span class="sxs-lookup"><span data-stu-id="8bd44-109">Decompress the file that you downloaded, and then start Visual Studio.</span></span>

2. <span data-ttu-id="8bd44-110">Menü çubuğunda **Dosya** > **Aç** > **Proje/çözüm**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="8bd44-110">On the menu bar, choose **File** > **Open** > **Project/Solution**.</span></span>

3. <span data-ttu-id="8bd44-111">**Proje Aç** iletişim kutusunda, açtığınız örnek kodu tutan klasörü açın ve ardından AsyncFineTuningCS için çözüm (. sln) dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="8bd44-111">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningCS.</span></span>

4. <span data-ttu-id="8bd44-112">**Çözüm Gezgini**, **zaman** hatası ve ardından **Başlangıç projesi olarak ayarla**' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="8bd44-112">In **Solution Explorer**, open the shortcut menu for the **CancelAfterTime** project, and then choose **Set as StartUp Project**.</span></span>

5. <span data-ttu-id="8bd44-113">Projeyi çalıştırmak için **F5** tuşunu seçin.</span><span class="sxs-lookup"><span data-stu-id="8bd44-113">Choose the **F5** key to run the project.</span></span> <span data-ttu-id="8bd44-114">(Veya, projeyi hata ayıklamadan çalıştırmak için **CTRL**+**F5** tuşuna basın).</span><span class="sxs-lookup"><span data-stu-id="8bd44-114">(Or, press **Ctrl**+**F5** to run the project without debugging it).</span></span>

6. <span data-ttu-id="8bd44-115">Çıktının tüm Web siteleri, Web sitesi veya bazı Web siteleri için çıktıyı gösterebileceğini doğrulamak için programı birkaç kez çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="8bd44-115">Run the program several times to verify that the output might show output for all websites, no websites, or some web sites.</span></span>

<span data-ttu-id="8bd44-116">Projeyi indirmek istemiyorsanız, bu konunun sonundaki MainWindow.xaml.cs dosyasını gözden geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8bd44-116">If you don't want to download the project, you can review the MainWindow.xaml.cs file at the end of this topic.</span></span>

## <a name="build-the-example"></a><span data-ttu-id="8bd44-117">Örneği oluşturun</span><span class="sxs-lookup"><span data-stu-id="8bd44-117">Build the example</span></span>

<span data-ttu-id="8bd44-118">Bu konudaki örnek, bir görev listesini iptal etmek için [zaman uyumsuz bir görevi veya görev listesini (C#) iptal](./cancel-an-async-task-or-a-list-of-tasks.md) etmek üzere geliştirilmiş projeye ekler.</span><span class="sxs-lookup"><span data-stu-id="8bd44-118">The example in this topic adds to the project that's developed in [Cancel an Async Task or a List of Tasks (C#)](./cancel-an-async-task-or-a-list-of-tasks.md) to cancel a list of tasks.</span></span> <span data-ttu-id="8bd44-119">Örnek, aynı kullanıcı arabirimini kullanır, ancak **iptal** düğmesi açıkça kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="8bd44-119">The example uses the same UI, although the **Cancel** button isn’t used explicitly.</span></span>

<span data-ttu-id="8bd44-120">Örneği kendiniz oluşturmak için, "örneği Indirme" bölümündeki yönergeleri izleyin, ancak **Başlangıç projesi**olarak iptal eden ınlıftasks ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="8bd44-120">To build the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **CancelAListOfTasks** as the **StartUp Project**.</span></span> <span data-ttu-id="8bd44-121">Bu konudaki değişiklikleri bu projeye ekleyin.</span><span class="sxs-lookup"><span data-stu-id="8bd44-121">Add the changes in this topic to that project.</span></span>

<span data-ttu-id="8bd44-122">Görevler iptal edildi olarak işaretlenmeden önce en uzun süreyi belirtmek için, aşağıdaki örnekte gösterildiği gibi `CancelAfter` öğesine `startButton_Click`bir çağrı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="8bd44-122">To specify a maximum time before the tasks are marked as canceled, add a call to `CancelAfter` to `startButton_Click`, as the following example shows.</span></span> <span data-ttu-id="8bd44-123">Toplama, yıldız işareti ile işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="8bd44-123">The addition is marked with asterisks.</span></span>

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

 <span data-ttu-id="8bd44-124">Çıktının tüm Web siteleri, Web sitesi veya bazı Web siteleri için çıktıyı gösterebileceğini doğrulamak için programı birkaç kez çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="8bd44-124">Run the program several times to verify that the output might show output for all websites, no websites, or some web sites.</span></span> <span data-ttu-id="8bd44-125">Aşağıdaki çıktı bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="8bd44-125">The following output is a sample.</span></span>

```
Length of the downloaded string: 35990.

Length of the downloaded string: 407399.

Length of the downloaded string: 226091.

Downloads canceled.
```

## <a name="complete-example"></a><span data-ttu-id="8bd44-126">Örnek Tamam</span><span class="sxs-lookup"><span data-stu-id="8bd44-126">Complete example</span></span>

<span data-ttu-id="8bd44-127">Aşağıdaki kod, örnek için MainWindow.xaml.cs dosyasının tüm metinkodudur.</span><span class="sxs-lookup"><span data-stu-id="8bd44-127">The following code is the complete text of the MainWindow.xaml.cs file for the example.</span></span> <span data-ttu-id="8bd44-128">Yıldız işaretleri bu örnek için eklenen öğeleri işaretler.</span><span class="sxs-lookup"><span data-stu-id="8bd44-128">Asterisks mark the elements that were added for this example.</span></span>

<span data-ttu-id="8bd44-129">İçin <xref:System.Net.Http>bir başvuru eklemeniz gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="8bd44-129">Notice that you must add a reference for <xref:System.Net.Http>.</span></span>

<span data-ttu-id="8bd44-130">Projeyi [zaman uyumsuz örnekten indirebilirsiniz: Uygulamanızı](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)hassas bir şekilde ayarlama.</span><span class="sxs-lookup"><span data-stu-id="8bd44-130">You can download the project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>

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

## <a name="see-also"></a><span data-ttu-id="8bd44-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8bd44-131">See also</span></span>

- [<span data-ttu-id="8bd44-132">Async ve await (C#) ile zaman uyumsuz programlama</span><span class="sxs-lookup"><span data-stu-id="8bd44-132">Asynchronous Programming with async and await (C#)</span></span>](./index.md)
- [<span data-ttu-id="8bd44-133">İzlenecek yol: Async ve await (C#) kullanarak Web 'e erişme</span><span class="sxs-lookup"><span data-stu-id="8bd44-133">Walkthrough: Accessing the Web by Using async and await (C#)</span></span>](./walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="8bd44-134">Zaman uyumsuz bir görevi veya görev listesini iptal etme (C#)</span><span class="sxs-lookup"><span data-stu-id="8bd44-134">Cancel an Async Task or a List of Tasks (C#)</span></span>](./cancel-an-async-task-or-a-list-of-tasks.md)
- [<span data-ttu-id="8bd44-135">Zaman uyumsuz uygulamanızda ince ayar yapma (C#)</span><span class="sxs-lookup"><span data-stu-id="8bd44-135">Fine-Tuning Your Async Application (C#)</span></span>](./fine-tuning-your-async-application.md)
- [<span data-ttu-id="8bd44-136">Zaman uyumsuz örnek: Uygulamanızda ince ayar yapma</span><span class="sxs-lookup"><span data-stu-id="8bd44-136">Async Sample: Fine Tuning Your Application</span></span>](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
