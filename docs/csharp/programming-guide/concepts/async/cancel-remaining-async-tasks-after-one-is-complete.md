---
title: Tam (C#) biridir sonra geri kalan zaman uyumsuz görevleri iptal etme
ms.date: 07/20/2015
ms.assetid: d3cebc74-c392-497b-b1e6-62a262eabe05
ms.openlocfilehash: baf757f7f7a71528dd5dc36b0f807eb452577a38
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59298675"
---
# <a name="cancel-remaining-async-tasks-after-one-is-complete-c"></a>Tam (C#) biridir sonra geri kalan zaman uyumsuz görevleri iptal etme
Kullanarak <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> yöntemi ile birlikte bir <xref:System.Threading.CancellationToken>, bir görev tamamlandığında kalan tüm görevleri iptal edebilirsiniz. `WhenAny` Yöntemi bir görev koleksiyonu olan bir bağımsız değişken alır. Bu yöntem tüm görevleri başlatır ve tek bir görev döndürür. Koleksiyondaki herhangi bir görev tamamlandığında tek bir görev tamamlanmıştır.  
  
 Bu örnek ile birlikte bir iptal belirteci kullanmayı gösteren `WhenAny` bitirilecek ilk göreve görevleri koleksiyonundan tamamlanması ve kalan görevleri iptal etmek için tutacak. Her görev bir Web sitesinin içeriklerini karşıdan yükler. Bu örnek, tamamlanacak ilk yüklemenin içeriğinin uzunluğunu görüntüler ve diğer yüklemeleri iptal eder.  
  
> [!NOTE]
>  Yeni bilgisayarınızda yüklü veya örnekleri çalıştırmak için Visual Studio 2012 veya daha yeni ve .NET Framework 4.5 yüklü olmalıdır.  
  
## <a name="downloading-the-example"></a>Örneği indirme  
 Tüm Windows Presentation Foundation (WPF) projeden indirebileceğiniz [zaman uyumsuz örneği: Uygulamanıza ince](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) ve sonra aşağıdaki adımları izleyin.  
  
1. İndirdiğiniz dosyanın sıkıştırmasını açın ve sonra Visual Studio'yu başlatın.  
  
2. Menü çubuğunda, **dosya**, **açık**, **proje/çözüm**.  
  
3. İçinde **Proje Aç** iletişim kutusunda, açtığınız örnek kodu barındıran klasörü açın ve ardından AsyncFineTuningCS için çözüm (.sln) dosyasını açın.  
  
4. İçinde **Çözüm Gezgini**, kısayol menüsünü açın **CancelAfterOneTask** proje ve ardından **başlangıç projesi olarak ayarla**.  
  
5. Projeyi çalıştırmak için F5 tuşuna basın.  
  
     Projeyi hata ayıklama olmadan çalıştırmak için Ctrl + F5 tuşlarını seçin.  
  
6. Programın farklı yüklemeleri ilk son doğrulamak için birkaç kez çalıştırın.  
  
 Projeyi indirmek istemiyorsanız, bu konunun sonunda MainWindow.xaml.cs dosyasını gözden geçirebilirsiniz.  
  
## <a name="building-the-example"></a>Örneği oluşturma  
 Bu konudaki örnek içinde geliştirilen projeye ekler [zaman uyumsuz bir görev veya bir liste görevleri (C#) iptal](../../../../csharp/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md) Görevler listesini iptal etme. Örnekte aynı Arabirim kullanılmaktadır, ancak **iptal** düğmesi açıkça kullanılmaz.  
  
 Örneği oluşturmak için kendinize, adım adım "Örneği indirme" bölümündeki yönergeleri izleyin, ancak seçin **CancelAListOfTasks** olarak **başlangıç projesi**. Bu konuda, değişiklikleri bu projeye ekleyin.  
  
 MainWindow.xaml.cs dosyasındaki **CancelAListOfTasks** proje, her Web sitesi için işlenen adımları döngüden taşıyarak geçişi başlatın `AccessTheWebAsync` aşağıdaki zaman uyumsuz yönteme.  
  
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
  
 İçinde `AccessTheWebAsync`, bu örnekte sorgu, <xref:System.Linq.Enumerable.ToArray%2A> yöntemi ve `WhenAny` oluşturmak ve bir dizi görev başlamak için yöntemi. Uygulamayı `WhenAny` dizisi için tek bir görev, bekletildiğinde döndürür dizideki görevlerin tamamlanmasına ulaşmak için ilk görev değerlendirir.  
  
 Aşağıdaki değişiklikleri yapın `AccessTheWebAsync`. Yıldız işaretleri kod dosyasındaki değişiklikleri işaretler.  
  
1. Açıklama satırı yapın veya döngü silin.  
  
2. Yürütüldüğünde, bir sorgu, oluşturun bir genel görev koleksiyonu oluşturur. Her çağrı `ProcessURLAsync` döndürür bir <xref:System.Threading.Tasks.Task%601> burada `TResult` bir tamsayıdır.  
  
    ```csharp  
    // ***Create a query that, when executed, returns a collection of tasks.  
    IEnumerable<Task<int>> downloadTasksQuery =  
        from url in urlList select ProcessURLAsync(url, client, ct);  
    ```  
  
3. Çağrı `ToArray` sorguyu ve görevleri başlatın. Uygulamayı `WhenAny` sonraki adımda yöntemi ve sorguyu kullanmadan başlangıç görevleri `ToArray`, ancak diğer yöntemler bunu yapmayabilir. En güvenli yöntem sorgu yürütmesini açıkça zorla sağlamaktır.  
  
    ```csharp  
    // ***Use ToArray to execute the query and start the download tasks.   
    Task<int>[] downloadTasks = downloadTasksQuery.ToArray();  
    ```  
  
4. Çağrı `WhenAny` üzerinde bir görev koleksiyonu. `WhenAny` Döndürür bir `Task(Of Task(Of Integer))` veya `Task<Task<int>>`.  Diğer bir deyişle, `WhenAny` değerlendiren bir görev için tek bir döndüren `Task(Of Integer)` veya `Task<int>` beklendiği zaman. Bu tek görev tamamlamak için koleksiyondaki ilk görevdir. İlk önce Tamamlanan görevin atandığı `firstFinishedTask`. Türünü `firstFinishedTask` olduğu <xref:System.Threading.Tasks.Task%601> burada `TResult` dönüş türü olan bir tamsayı çünkü `ProcessURLAsync`.  
  
    ```csharp  
    // ***Call WhenAny and then await the result. The task that finishes   
    // first is assigned to firstFinishedTask.  
    Task<int> firstFinishedTask = await Task.WhenAny(downloadTasks);  
    ```  
  
5. Bu örnekte, önce sona eren yalnızca görevle ilgilendiniz. Bu nedenle, <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> kalan görevleri iptal etmek için.  
  
    ```csharp  
    // ***Cancel the rest of the downloads. You just want the first one.  
    cts.Cancel();  
    ```  
  
6. Son olarak, await `firstFinishedTask` karşıdan yüklenen içeriğin uzunluğunu almak için.  
  
    ```csharp  
    var length = await firstFinishedTask;  
    resultsTextBox.Text += $"\r\nLength of the downloaded website:  {length}\r\n";
    ```  
  
 Programın farklı yüklemeleri ilk son doğrulamak için birkaç kez çalıştırın.  
  
## <a name="complete-example"></a>Tam Örnek  
 Aşağıdaki kod örneği için tam MainWindow.xaml.cs dosyasıdır. Yıldız işaretleri, bu örnek için eklenen öğeleri işaretler.  
  
 İçin bir başvuru eklemeniz gerektiğini unutmayın <xref:System.Net.Http>.  
  
 Projeden indirebileceğiniz [zaman uyumsuz örneği: Uygulamanızı ince ayar](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading.Tasks.Task.WhenAny%2A>
- [(C#) Async uygulamanızda hassas ayar yapma](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md)
- [Zaman uyumsuz programlama ile async ve await (C#)](../../../../csharp/programming-guide/concepts/async/index.md)
- [Zaman uyumsuz örneği: Uygulamanızda hassas ayar yapma](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
