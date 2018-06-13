---
title: Tam (C#) biridir sonra geri kalan zaman uyumsuz görevleri iptal etme
ms.date: 07/20/2015
ms.assetid: d3cebc74-c392-497b-b1e6-62a262eabe05
ms.openlocfilehash: 22a29dec90dcbbd24ff1a6081fd7bf1d56d6ac0e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33327430"
---
# <a name="cancel-remaining-async-tasks-after-one-is-complete-c"></a>Tam (C#) biridir sonra geri kalan zaman uyumsuz görevleri iptal etme
Kullanarak <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> yöntemi ile birlikte bir <xref:System.Threading.CancellationToken>, bir görev tamamlandığında, kalan tüm görevler iptal edebilirsiniz. `WhenAny` Yöntemi görevleri koleksiyonu olmayan bir bağımsız değişken alır. Bu yöntem, tüm görevleri başlatır ve tek bir görev döndürür. Koleksiyondaki herhangi bir görev tamamlandığında, tek bir görev tamamlanır.  
  
 Bu örnek bir iptal belirteci ile birlikte kullanımı gösterilmiştir `WhenAny` için ilk görev görevler koleksiyonundan tamamlamak için ve diğer görevleri iptal etmek için tutmak için. Her görev, bir Web sitesi içeriğini indirir. Örnek tamamlamak için ilk yükleme içeriğini uzunluğu görüntüler ve diğer yüklemeleri iptal eder.  
  
> [!NOTE]
>  Örnekleri çalıştırmak için Visual Studio 2012 veya daha yeni ve .NET Framework 4.5 olmalıdır veya daha yeni bilgisayarınızda yüklü.  
  
## <a name="downloading-the-example"></a>Örnek indirme  
 Tam Windows Presentation Foundation (WPF) projeden indirebilirsiniz [zaman uyumsuz örnek: ince ayar uygulamanız](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) ve ardından aşağıdaki adımları izleyin.  
  
1.  İndirdiğiniz dosyanın sıkıştırmasını ve Visual Studio'yu başlatın.  
  
2.  Menü çubuğunda seçin **dosya**, **açık**, **proje/çözüm**.  
  
3.  İçinde **Proje Aç** iletişim kutusunda, sıkıştırması örnek kod tutan klasörü açın ve ardından AsyncFineTuningCS için çözüm (.sln) dosyasını açın.  
  
4.  İçinde **Çözüm Gezgini**, kısayol menüsünü açın **CancelAfterOneTask** proje ve ardından **başlangıç projesi olarak ayarla**.  
  
5.  Projeyi çalıştırmak için F5 tuşuna seçin.  
  
     Hata ayıklama olmadan projeyi çalıştırmak için Ctrl + F5 anahtarları'i seçin.  
  
6.  Programı farklı yüklemeler ilk son doğrulamak için birkaç kez çalıştırın.  
  
 Projenizi indirin istemiyorsanız, bu konunun sonundaki MainWindow.xaml.cs dosyasını gözden geçirebilirsiniz.  
  
## <a name="building-the-example"></a>Örnek oluşturma  
 Bu konudaki örnek da geliştirilmiş projesine ekler [bir zaman uyumsuz görev veya bir liste görevleri (C#) iptal](../../../../csharp/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md) görev listesini iptal etme. Örnek olsa da, aynı kullanıcı arabirimini kullanır **iptal** düğmesi değil kullanılan açıkça.  
  
 Örnek oluşturmak için kendiniz, adım adım "örnek indirme" bölümündeki yönergeleri izleyin, ancak seçin **CancelAListOfTasks** olarak **başlangıç projesi**. Değişiklikleri bu konuda bu projeye ekleyin.  
  
 MainWindow.xaml.cs dosyasındaki **CancelAListOfTasks** proje, her Web sitesi için işlem adımları döngüde taşıma tarafından geçiş başlatma `AccessTheWebAsync` aşağıdaki async yöntemi için.  
  
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
  
 İçinde `AccessTheWebAsync`, bu örnek bir sorgu kullanır <xref:System.Linq.Enumerable.ToArray%2A> yöntemi ve `WhenAny` oluşturma ve görev dizisi başlatma yöntemi. Uygulamayı `WhenAny` dizisi için tek bir görev, beklemenin zaman döndürür görev dizisindeki tamamlanmasından ulaşmak için ilk görev değerlendirir.  
  
 Aşağıdaki değişiklikleri yapın `AccessTheWebAsync`. Yıldız işareti kod dosyasındaki değişiklikleri işaretleyin.  
  
1.  Out yorum yapmak veya döngü silin.  
  
2.  Bir sorgu, yürütülen oluşturduğunuzda genel görevleri koleksiyonu oluşturur. Her çağrı `ProcessURLAsync` döndüren bir <xref:System.Threading.Tasks.Task%601> burada `TResult` bir tamsayıdır.  
  
    ```csharp  
    // ***Create a query that, when executed, returns a collection of tasks.  
    IEnumerable<Task<int>> downloadTasksQuery =  
        from url in urlList select ProcessURLAsync(url, client, ct);  
    ```  
  
3.  Çağrı `ToArray` sorguyu yürütmek ve görevleri başlatın. Uygulamayı `WhenAny` yöntemi bir sonraki adımda ve sorguyu yürütmek kullanmadan görevlerini başlatmak `ToArray`, ancak diğer yöntemleri görünmeyebilir. Sorgunun yürütülmesi, açıkça zorlamak için en güvenli yöntemdir bakın.  
  
    ```csharp  
    // ***Use ToArray to execute the query and start the download tasks.   
    Task<int>[] downloadTasks = downloadTasksQuery.ToArray();  
    ```  
  
4.  Çağrı `WhenAny` görevleri koleksiyonu. `WhenAny` döndüren bir `Task(Of Task(Of Integer))` veya `Task<Task<int>>`.  Diğer bir deyişle, `WhenAny` tek bir değerlendiren bir görev döndürür `Task(Of Integer)` veya `Task<int>` zaman beklemenin. Bu tek ilk görevi tamamlamak için koleksiyondaki bir görevdir. İlk tamamlandı görev atandığı `firstFinishedTask`. Türü `firstFinishedTask` olan <xref:System.Threading.Tasks.Task%601> nerede `TResult` , dönüş türü tamsayı olmadığından `ProcessURLAsync`.  
  
    ```csharp  
    // ***Call WhenAny and then await the result. The task that finishes   
    // first is assigned to firstFinishedTask.  
    Task<int> firstFinishedTask = await Task.WhenAny(downloadTasks);  
    ```  
  
5.  Bu örnekte, yalnızca ilk bittikten görevdeki ilgilendiğiniz. Bu nedenle kullanmak <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> kalan görevleri iptal etmek için.  
  
    ```csharp  
    // ***Cancel the rest of the downloads. You just want the first one.  
    cts.Cancel();  
    ```  
  
6.  Son olarak, await `firstFinishedTask` indirilen içerik uzunluğu alınamadı.  
  
    ```csharp  
    var length = await firstFinishedTask;  
    resultsTextBox.Text += String.Format("\r\nLength of the downloaded website:  {0}\r\n", length);  
    ```  
  
 Programı farklı yüklemeler ilk son doğrulamak için birkaç kez çalıştırın.  
  
## <a name="complete-example"></a>Tam Örnek  
 Aşağıdaki kod, örneğin tam MainWindow.xaml.cs dosyasıdır. Yıldız işareti, bu örnek için eklenen öğeleri işaretleyin.  
  
 İçin bir başvuru eklemeniz gerekir fark <xref:System.Net.Http>.  
  
 Projeden indirebilirsiniz [zaman uyumsuz örnek: ince ayar uygulamanız](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).  
  
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
            //        String.Format("\r\nLength of the downloaded string: {0}.\r\n", urlContents.Length);  
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
            resultsTextBox.Text += String.Format("\r\nLength of the downloaded website:  {0}\r\n", length);  
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
                "http://msdn.microsoft.com",  
                "http://msdn.microsoft.com/library/hh290138.aspx",  
                "http://msdn.microsoft.com/library/hh290140.aspx",  
                "http://msdn.microsoft.com/library/dd470362.aspx",  
                "http://msdn.microsoft.com/library/aa578028.aspx",  
                "http://msdn.microsoft.com/library/ms404677.aspx",  
                "http://msdn.microsoft.com/library/ff730837.aspx"  
            };  
            return urls;  
        }  
    }  
    // Sample output:  
  
    // Length of the downloaded website:  158856  
  
    // Download complete.  
}  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Threading.Tasks.Task.WhenAny%2A>  
 [(C#) Async uygulamanızda hassas ayar yapma](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md)  
 [Zaman uyumsuz programlama ile async ve await (C#)](../../../../csharp/programming-guide/concepts/async/index.md)  
 [Zaman uyumsuz örnek: İnce uygulamanızı ayarlama](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
