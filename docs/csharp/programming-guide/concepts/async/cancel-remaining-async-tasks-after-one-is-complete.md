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
# <a name="cancel-remaining-async-tasks-after-one-is-complete-c"></a>Bir Tamamlandıktan Sonra Kalan Async Görevlerini İptal Et (C#)
Bir <xref:System.Threading.CancellationToken>, <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> bir görev tamamlandığında kalan tüm görevleri iptal edebilirsiniz yöntemi kullanarak. Yöntem, `WhenAny` görevlerin bir koleksiyon bir argüman alır. Yöntem tüm görevleri başlatır ve tek bir görev döndürür. Koleksiyondaki herhangi bir görev tamamlandığında tek görev tamamlanır.  
  
 Bu örnek, görev koleksiyonundan bitirmek ve `WhenAny` kalan görevleri iptal etmek için ilk görevi tutmak için birlikte bir iptal belirteci nasıl kullanılacağını gösterir. Her görev bir web sitesinin içeriğini indirir. Örnek, tamamlamak için ilk karşıdan yüklemenin içeriğini gösterir ve diğer indirmeleri iptal eder.  
  
> [!NOTE]
> Örnekleri çalıştırmak için Visual Studio 2012 veya daha yeni ve .NET Framework 4.5 veya daha yeni bilgisayarınıza yüklü olması gerekir.  
  
## <a name="downloading-the-example"></a>Örneği İndirme  
 Windows Presentation Foundation (WPF) projesinin tamamını [Async Sample: Fine Tuning Application'dan](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) indirebilir ve ardından aşağıdaki adımları izleyebilirsiniz.  
  
1. İndirdiğiniz dosyayı sıkıştırın ve Visual Studio'yu başlatın.  
  
2. Menü çubuğunda **Dosya**, **Aç**, **Proje/Çözüm'ü**seçin.  
  
3. **Projeyi Aç** iletişim kutusunda, sıkıştırdığınız örnek kodu tutan klasörü açın ve ardından AsyncFineTuningCS için çözüm (.sln) dosyasını açın.  
  
4. **Solution**Explorer'da, **CancelAfterOneTask** projesinin kısayol menüsünü açın ve ardından **StartUp Project olarak ayarla'yı**seçin.  
  
5. Projeyi çalıştırmak için F5 tuşunu seçin.  
  
     Projeyi hata ayıklamadan çalıştırmak için Ctrl+F5 tuşlarını seçin.  
  
6. Farklı indirmelerin önce bitip bitdiğini doğrulamak için programı birkaç kez çalıştırın.  
  
 Projeyi indirmek istemiyorsanız, bu konunun sonundaki MainWindow.xaml.cs dosyasını gözden geçirebilirsiniz.  
  
## <a name="building-the-example"></a>Örnek Oluşturma  
 Bu konuyla ilgili örnek, görev listesini iptal etmek için Bir Async Görevi İptal Etme [veya Görev Listesi (C#)](./cancel-an-async-task-or-a-list-of-tasks.md) olarak geliştirilen projeye eklenir. **İptal** düğmesi açıkça kullanılmasa da, örnek aynı UI'yi kullanır.  
  
 Örneği adım adım oluşturmak için, "Örneği İndirme" bölümündeki yönergeleri izleyin, ancak **StartUp Project**olarak **CancelAListOfTasks'i** seçin. Bu konudaki değişiklikleri bu projeye ekleyin.  
  
 **CancelAListOfTasks** projesinin MainWindow.xaml.cs dosyasında, her web sitesi için işlem adımlarını `AccessTheWebAsync` döngüden aşağıdaki async yöntemine taşıyarak geçişi başlatın.  
  
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
  
 Bu `AccessTheWebAsync`örnekte, bir dizi <xref:System.Linq.Enumerable.ToArray%2A> görev oluşturmak `WhenAny` ve başlatmak için bir sorgu, yöntem ve yöntem kullanır. `WhenAny` Diziye uygulama, beklenildiğinde, görev dizisinde tamamlanmasına ulaşmak için ilk göreve değerlendiren tek bir görevi döndürür.  
  
 Aşağıdaki değişiklikleri `AccessTheWebAsync`yapın. Yıldız işaretleri kod dosyasındaki değişiklikleri işaretler.  
  
1. Yorum yapın veya döngüyü silin.  
  
2. Yürütüldüğünde genel görevler topluluğu oluşturan bir sorgu oluşturun. Her çağrı `ProcessURLAsync` bir <xref:System.Threading.Tasks.Task%601> `TResult` tamsayı olduğu bir yeri döndürür.  
  
    ```csharp  
    // ***Create a query that, when executed, returns a collection of tasks.  
    IEnumerable<Task<int>> downloadTasksQuery =  
        from url in urlList select ProcessURLAsync(url, client, ct);  
    ```  
  
3. Sorguyu yürütmek ve görevleri başlatmak için arayın. `ToArray` Bir sonraki `WhenAny` adımda yöntemin uygulanması sorguyu yürütmek ve `ToArray`kullanmadan görevleri başlatmak, ancak diğer yöntemler olmayabilir. En güvenli yöntem, sorgunun yürütülmesini açıkça zorlamaktır.  
  
    ```csharp  
    // ***Use ToArray to execute the query and start the download tasks.
    Task<int>[] downloadTasks = downloadTasksQuery.ToArray();  
    ```  
  
4. Görevlerin toplanmasını çağırın. `WhenAny` `WhenAny`bir `Task(Of Task(Of Integer))` veya `Task<Task<int>>`.  Diğer bir `WhenAny` diğer anda, tek `Task(Of Integer)` bir `Task<int>` göreve veya beklenen zamana değerlendiren bir görev döndürür. Bu tek görev, koleksiyonda tamamlanır ilk görevdir. İlk tamamlanan `firstFinishedTask`görev. Bu bir `firstFinishedTask` <xref:System.Threading.Tasks.Task%601> karşıcının olduğu yerdir, `TResult` çünkü bu `ProcessURLAsync`bir geri dönüş türüdür.  
  
    ```csharp  
    // ***Call WhenAny and then await the result. The task that finishes
    // first is assigned to firstFinishedTask.  
    Task<int> firstFinishedTask = await Task.WhenAny(downloadTasks);  
    ```  
  
5. Bu örnekte, yalnızca ilk bitiren görevle ilgileniyorsunuz. Bu nedenle, kalan görevleri iptal etmek için kullanın. <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType>  
  
    ```csharp  
    // ***Cancel the rest of the downloads. You just want the first one.  
    cts.Cancel();  
    ```  
  
6. Son olarak, indirilen içeriğin uzunluğunu almak için bekleyin. `firstFinishedTask`  
  
    ```csharp  
    var length = await firstFinishedTask;  
    resultsTextBox.Text += $"\r\nLength of the downloaded website:  {length}\r\n";
    ```  
  
 Farklı indirmelerin önce bitip bitdiğini doğrulamak için programı birkaç kez çalıştırın.  
  
## <a name="complete-example"></a>Tam Örnek  
 Aşağıdaki kod, örneğin MainWindow.xaml.cs dosyanın tamamıdır. Yıldız işaretleri, bu örnek için eklenen öğeleri işaretler.  
  
 Için bir başvuru eklemeniz <xref:System.Net.Http>gerektiğine dikkat edin.  
  
 Projeyi [Async Sample: Fine Tuning Application'dan](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)indirebilirsiniz.  
  
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
- [Async Uygulamanızda İnce Ayar (C#)](./fine-tuning-your-async-application.md)
- [Async ve await ile Asynchronous Programlama (C#)](./index.md)
- [Async Örnek: Uygulamanızı İyi Ayar](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
