---
title: "Bir süre (C#) sonra zaman uyumsuz görevleri iptal etme"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 194282c2-399f-46da-a7a6-96674e00b0b3
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: eca4b411f8d8151b18c7e83be15191a843e628b4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="cancel-async-tasks-after-a-period-of-time-c"></a><span data-ttu-id="e20cd-102">Bir süre (C#) sonra zaman uyumsuz görevleri iptal etme</span><span class="sxs-lookup"><span data-stu-id="e20cd-102">Cancel Async Tasks after a Period of Time (C#)</span></span>
<span data-ttu-id="e20cd-103">Kullanarak zaman uyumsuz işlemi bir süre sonra iptal edebilirsiniz <xref:System.Threading.CancellationTokenSource.CancelAfter%2A?displayProperty=nameWithType> işlemin tamamlanmasını beklemek istemiyorsanız yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e20cd-103">You can cancel an asynchronous operation after a period of time by using the  <xref:System.Threading.CancellationTokenSource.CancelAfter%2A?displayProperty=nameWithType> method if you don't want to wait for the operation to finish.</span></span> <span data-ttu-id="e20cd-104">Bu yöntem tarafından belirlenen süre içinde tam olmayan herhangi bir ilişkili görevi iptali zamanlar `CancelAfter` ifade.</span><span class="sxs-lookup"><span data-stu-id="e20cd-104">This method schedules the cancellation of any associated tasks that aren’t complete within the period of time that’s designated by the `CancelAfter` expression.</span></span>  
  
 <span data-ttu-id="e20cd-105">Bu örnek da geliştirilmiş kod ekler [bir zaman uyumsuz görev veya bir liste görevleri (C#) iptal](../../../../csharp/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md) Web sitelerinin bir listesiyle indirmek ve her biri içeriğini uzunluğu görüntülemek için.</span><span class="sxs-lookup"><span data-stu-id="e20cd-105">This example adds to the code that’s developed in [Cancel an Async Task or a List of Tasks (C#)](../../../../csharp/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md) to download a list of websites and to display the length of the contents of each one.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e20cd-106">Örnekleri çalıştırmak için Visual Studio 2012 veya daha yeni ve .NET Framework 4.5 olmalıdır veya daha yeni bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="e20cd-106">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
## <a name="downloading-the-example"></a><span data-ttu-id="e20cd-107">Örnek indirme</span><span class="sxs-lookup"><span data-stu-id="e20cd-107">Downloading the Example</span></span>  
 <span data-ttu-id="e20cd-108">Tam Windows Presentation Foundation (WPF) projeden indirebilirsiniz [zaman uyumsuz örnek: ince ayar uygulamanız](http://go.microsoft.com/fwlink/?LinkId=255046) ve ardından aşağıdaki adımları izleyin.</span><span class="sxs-lookup"><span data-stu-id="e20cd-108">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](http://go.microsoft.com/fwlink/?LinkId=255046) and then follow these steps.</span></span>  
  
1.  <span data-ttu-id="e20cd-109">İndirdiğiniz dosyanın sıkıştırmasını ve Visual Studio'yu başlatın.</span><span class="sxs-lookup"><span data-stu-id="e20cd-109">Decompress the file that you downloaded, and then start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="e20cd-110">Menü çubuğunda seçin **dosya**, **açık**, **proje/çözüm**.</span><span class="sxs-lookup"><span data-stu-id="e20cd-110">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
3.  <span data-ttu-id="e20cd-111">İçinde **Proje Aç** iletişim kutusunda, sıkıştırması örnek kod tutan klasörü açın ve ardından AsyncFineTuningCS için çözüm (.sln) dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="e20cd-111">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningCS.</span></span>  
  
4.  <span data-ttu-id="e20cd-112">İçinde **Çözüm Gezgini**, kısayol menüsünü açın **CancelAfterTime** proje ve ardından **başlangıç projesi olarak ayarla**.</span><span class="sxs-lookup"><span data-stu-id="e20cd-112">In **Solution Explorer**, open the shortcut menu for the **CancelAfterTime** project, and then choose **Set as StartUp Project**.</span></span>  
  
5.  <span data-ttu-id="e20cd-113">Projeyi çalıştırmak için F5 tuşuna seçin.</span><span class="sxs-lookup"><span data-stu-id="e20cd-113">Choose the F5 key to run the project.</span></span>  
  
     <span data-ttu-id="e20cd-114">Hata ayıklama olmadan projeyi çalıştırmak için Ctrl + F5 anahtarları'i seçin.</span><span class="sxs-lookup"><span data-stu-id="e20cd-114">Choose the Ctrl+F5 keys to run the project without debugging it.</span></span>  
  
6.  <span data-ttu-id="e20cd-115">Program, çıktı tüm Web siteleri, hiçbir Web siteleri veya bazı web siteleri için çıktı gösterebilir doğrulamak için birkaç kez çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="e20cd-115">Run the program several times to verify that the output might show output for all websites, no websites, or some web sites.</span></span>  
  
 <span data-ttu-id="e20cd-116">Projenizi indirin istemiyorsanız, bu konunun sonundaki MainWindow.xaml.cs dosyasını gözden geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e20cd-116">If you don't want to download the project, you can review the MainWindow.xaml.cs file at the end of this topic.</span></span>  
  
## <a name="building-the-example"></a><span data-ttu-id="e20cd-117">Örnek oluşturma</span><span class="sxs-lookup"><span data-stu-id="e20cd-117">Building the Example</span></span>  
 <span data-ttu-id="e20cd-118">Bu konudaki örnek da geliştirilmiş projesine ekler [bir zaman uyumsuz görev veya bir liste görevleri (C#) iptal](../../../../csharp/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md) görev listesini iptal etme.</span><span class="sxs-lookup"><span data-stu-id="e20cd-118">The example in this topic adds to the project that's developed in [Cancel an Async Task or a List of Tasks (C#)](../../../../csharp/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md) to cancel a list of tasks.</span></span> <span data-ttu-id="e20cd-119">Örnek olsa da, aynı kullanıcı arabirimini kullanır **iptal** düğmesi değil kullanılan açıkça.</span><span class="sxs-lookup"><span data-stu-id="e20cd-119">The example uses the same UI, although the **Cancel** button isn’t used explicitly.</span></span>  
  
 <span data-ttu-id="e20cd-120">Örnek oluşturmak için kendiniz, adım adım "örnek indirme" bölümündeki yönergeleri izleyin, ancak seçin **CancelAListOfTasks** olarak **başlangıç projesi**.</span><span class="sxs-lookup"><span data-stu-id="e20cd-120">To build the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **CancelAListOfTasks** as the **StartUp Project**.</span></span> <span data-ttu-id="e20cd-121">Değişiklikleri bu konuda bu projeye ekleyin.</span><span class="sxs-lookup"><span data-stu-id="e20cd-121">Add the changes in this topic to that project.</span></span>  
  
 <span data-ttu-id="e20cd-122">Görev iptal edildi olarak işaretlenmiş önce maksimum süreyi belirtmek için bir çağrı ekleyin `CancelAfter` için `startButton_Click`, aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="e20cd-122">To specify a maximum time before the tasks are marked as canceled, add a call to `CancelAfter` to `startButton_Click`, as the following example shows.</span></span> <span data-ttu-id="e20cd-123">Ek yıldız işaretiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="e20cd-123">The addition is marked with asterisks.</span></span>  
  
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
  
 <span data-ttu-id="e20cd-124">Program, çıktı tüm Web siteleri, hiçbir Web siteleri veya bazı web siteleri için çıktı gösterebilir doğrulamak için birkaç kez çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="e20cd-124">Run the program several times to verify that the output might show output for all websites, no websites, or some web sites.</span></span> <span data-ttu-id="e20cd-125">Aşağıdaki çıkış bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="e20cd-125">The following output is a sample.</span></span>  
  
```  
Length of the downloaded string: 35990.  
  
Length of the downloaded string: 407399.  
  
Length of the downloaded string: 226091.  
  
Downloads canceled.  
```  
  
## <a name="complete-example"></a><span data-ttu-id="e20cd-126">Tam Örnek</span><span class="sxs-lookup"><span data-stu-id="e20cd-126">Complete Example</span></span>  
 <span data-ttu-id="e20cd-127">Aşağıdaki kod örneğin MainWindow.xaml.cs dosyasının tam metindir.</span><span class="sxs-lookup"><span data-stu-id="e20cd-127">The following code is the complete text of the MainWindow.xaml.cs file for the example.</span></span> <span data-ttu-id="e20cd-128">Yıldız işareti, bu örnek için eklenen öğeleri işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="e20cd-128">Asterisks mark the elements that were added for this example.</span></span>  
  
 <span data-ttu-id="e20cd-129">İçin bir başvuru eklemeniz gerekir fark <xref:System.Net.Http>.</span><span class="sxs-lookup"><span data-stu-id="e20cd-129">Notice that you must add a reference for <xref:System.Net.Http>.</span></span>  
  
 <span data-ttu-id="e20cd-130">Projeden indirebilirsiniz [zaman uyumsuz örnek: ince ayar uygulamanız](http://go.microsoft.com/fwlink/?LinkId=255046).</span><span class="sxs-lookup"><span data-stu-id="e20cd-130">You can download the project from [Async Sample: Fine Tuning Your Application](http://go.microsoft.com/fwlink/?LinkId=255046).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e20cd-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e20cd-131">See Also</span></span>  
 [<span data-ttu-id="e20cd-132">Zaman uyumsuz programlama ile async ve await (C#)</span><span class="sxs-lookup"><span data-stu-id="e20cd-132">Asynchronous Programming with async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/index.md)  
 [<span data-ttu-id="e20cd-133">İzlenecek yol: async kullanarak Web'e erişme ve await (C#)</span><span class="sxs-lookup"><span data-stu-id="e20cd-133">Walkthrough: Accessing the Web by Using async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)  
 [<span data-ttu-id="e20cd-134">Zaman uyumsuz görevi veya görev (C#) listesini iptal etme</span><span class="sxs-lookup"><span data-stu-id="e20cd-134">Cancel an Async Task or a List of Tasks (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md)  
 [<span data-ttu-id="e20cd-135">(C#) Async uygulamanızda hassas ayar yapma</span><span class="sxs-lookup"><span data-stu-id="e20cd-135">Fine-Tuning Your Async Application (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md)  
 [<span data-ttu-id="e20cd-136">Zaman uyumsuz örnek: İnce uygulamanızı ayarlama</span><span class="sxs-lookup"><span data-stu-id="e20cd-136">Async Sample: Fine Tuning Your Application</span></span>](http://go.microsoft.com/fwlink/?LinkId=255046)
