---
title: Kalan zaman uyumsuz görevleri bir tane tamamlandıktan sonra iptal etme (C#)
description: Bu örnekte bir görev tamamlandığında kalan tüm görevleri iptal etmek Için, Task. WhenAny yöntemini C# içindeki CancellationToken ile birlikte kullanın.
ms.date: 07/20/2015
ms.assetid: d3cebc74-c392-497b-b1e6-62a262eabe05
ms.openlocfilehash: 6de60c8faa93752961e3703a042885a71972cc4a
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925298"
---
# <a name="cancel-remaining-async-tasks-after-one-is-complete-c"></a>Kalan zaman uyumsuz görevleri bir tane tamamlandıktan sonra iptal etme (C#)
<xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>Yöntemini bir ile birlikte kullanarak, bir <xref:System.Threading.CancellationToken> görev tamamlandığında kalan tüm görevleri iptal edebilirsiniz. `WhenAny`Yöntemi, bir görev koleksiyonu olan bir bağımsız değişken alır. Yöntemi tüm görevleri başlatır ve tek bir görev döndürür. Koleksiyondaki herhangi bir görev tamamlandığında tek görev tamamlanır.  
  
 Bu örnek, bir iptal belirtecinin `WhenAny` , görev koleksiyonundan sona ermesini ve kalan görevleri iptal etmek için ilk görevi tutmak üzere ile birlikte nasıl kullanılacağını gösterir. Her görev bir Web sitesinin içeriğini indirir. Örnek, tamamlanacak ilk indirmenin içeriklerinin uzunluğunu görüntüler ve diğer indirmeleri iptal eder.  
  
> [!NOTE]
> Örnekleri çalıştırmak için, bilgisayarınızda Visual Studio 2012 veya daha yeni bir sürümü ve .NET Framework 4,5 ya da daha yeni bir sürümü yüklü olmalıdır.  
  
## <a name="downloading-the-example"></a>Örnek indiriliyor  
 Tüm Windows Presentation Foundation (WPF) projesini [zaman uyumsuz örnekten indirebilirsiniz: uygulamanızı Ince ayar](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) yapın ve ardından aşağıdaki adımları izleyin.  
  
1. İndirdiğiniz dosyayı sıkıştırmasını açın ve ardından Visual Studio 'Yu başlatın.  
  
2. Menü çubuğunda **Dosya**, **Aç**, **Proje/çözüm**' ü seçin.  
  
3. **Proje Aç** iletişim kutusunda, açtığınız örnek kodu tutan klasörü açın ve ardından AsyncFineTuningCS için çözüm (. sln) dosyasını açın.  
  
4. **Çözüm Gezgini**' de, **ınkıfteronetask** projesinin kısayol menüsünü açın ve ardından **Başlangıç projesi olarak ayarla**' yı seçin.  
  
5. Projeyi çalıştırmak için F5 tuşunu seçin.  
  
     Projeyi hata ayıklamadan çalıştırmak için CTRL + F5 tuşlarını seçin.  
  
6. İlk olarak farklı indirmelerin bitmesini doğrulamak için programı birkaç kez çalıştırın.  
  
 Projeyi indirmek istemiyorsanız, bu konunun sonundaki MainWindow.xaml.cs dosyasını gözden geçirebilirsiniz.  
  
## <a name="building-the-example"></a>Örnek oluşturma  
 Bu konudaki örnek, bir görev listesini iptal etmek için [zaman uyumsuz bir görevi veya bir görev listesini (C#) Iptal etme](./cancel-an-async-task-or-a-list-of-tasks.md) bölümünde geliştirilen projeye ekler. Örnek, aynı kullanıcı arabirimini kullanır, ancak **iptal** düğmesi açıkça kullanılmaz.  
  
 Örneği kendiniz oluşturmak için, "örneği Indirme" bölümündeki yönergeleri izleyin, ancak **Başlangıç projesi**olarak iptal eden **ınlıftasks** ' ı seçin. Bu konudaki değişiklikleri bu projeye ekleyin.  
  
 "MainWindow.xaml.cs & lt; & lt; & lt; & lt; & lt; 3} dosya **dosyasında, içindeki** her bir Web sitesi için işleme adımlarını `AccessTheWebAsync` aşağıdaki zaman uyumsuz metoda taşıyarak geçişi başlatın.  
  
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
  
 `AccessTheWebAsync`' De, bu örnek bir sorgu, <xref:System.Linq.Enumerable.ToArray%2A> Yöntem ve bir `WhenAny` dizi görev oluşturmak ve başlatmak için yöntemini kullanır. Dizi için olan uygulaması, `WhenAny` bir görev dizisinde tamamlamaya ulaşmak üzere ilk görevi değerlendiren tek bir görev döndürür.  
  
 İçinde aşağıdaki değişiklikleri yapın `AccessTheWebAsync` . Yıldız işaretleri kod dosyasındaki değişiklikleri işaretler.  
  
1. Döngüyü not edin veya silin.  
  
2. Yürütüldüğünde, genel görevlerden oluşan bir koleksiyon üreten bir sorgu oluşturun. Her çağrısı `ProcessURLAsync` <xref:System.Threading.Tasks.Task%601> , bir, bir `TResult` tamsayı olan bir döndürür.  
  
    ```csharp  
    // ***Create a query that, when executed, returns a collection of tasks.  
    IEnumerable<Task<int>> downloadTasksQuery =  
        from url in urlList select ProcessURLAsync(url, client, ct);  
    ```  
  
3. `ToArray`Sorguyu yürütmek ve görevleri başlatmak için çağırın. Bir `WhenAny` sonraki adımda yönteminin uygulaması sorguyu yürütür ve görevleri kullanmadan başlatır `ToArray` , ancak diğer yöntemler de çalışmayabilir. En güvenli yöntem, sorgunun yürütülmesini açıkça zorlamaktır.  
  
    ```csharp  
    // ***Use ToArray to execute the query and start the download tasks.
    Task<int>[] downloadTasks = downloadTasksQuery.ToArray();  
    ```  
  
4. `WhenAny`Görevler koleksiyonunda çağırın. `WhenAny`bir `Task(Of Task(Of Integer))` veya döndürür `Task<Task<int>>` .  Diğer bir deyişle, `WhenAny` tek veya bekleniyor bir görevi döndürür `Task(Of Integer)` `Task<int>` . Bu tek görev, koleksiyondaki ilk görevin sona ermesini sağlar. Önce tamamlanan görev öğesine atanır `firstFinishedTask` . Türü, öğesinin `firstFinishedTask` <xref:System.Threading.Tasks.Task%601> `TResult` dönüş türü olduğu için bir tamsayıdır `ProcessURLAsync` .  
  
    ```csharp  
    // ***Call WhenAny and then await the result. The task that finishes
    // first is assigned to firstFinishedTask.  
    Task<int> firstFinishedTask = await Task.WhenAny(downloadTasks);  
    ```  
  
5. Bu örnekte, yalnızca ilk olarak sona erki görevi ilgileniyorsunuz. Bu nedenle, <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> kalan görevleri iptal etmek için kullanın.  
  
    ```csharp  
    // ***Cancel the rest of the downloads. You just want the first one.  
    cts.Cancel();  
    ```  
  
6. Son olarak, `firstFinishedTask` indirilen içeriğin uzunluğunu almak için Await.  
  
    ```csharp  
    var length = await firstFinishedTask;  
    resultsTextBox.Text += $"\r\nLength of the downloaded website:  {length}\r\n";
    ```  
  
 İlk olarak farklı indirmelerin bitmesini doğrulamak için programı birkaç kez çalıştırın.  
  
## <a name="complete-example"></a>Tam Örnek  
 Aşağıdaki kod, örnek için tüm MainWindow.xaml.cs dosyasıdır. Yıldız işaretleri bu örnek için eklenen öğeleri işaretler.  
  
 İçin bir başvuru eklemeniz gerektiğini unutmayın <xref:System.Net.Http> .  
  
 Projeyi [zaman uyumsuz örnekten indirebilirsiniz: uygulamanızı hassas bir şekilde ayarlama](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).  
  
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
- [Zaman uyumsuz uygulamanızda ince ayar yapma (C#)](./fine-tuning-your-async-application.md)
- [Async ve await ile zaman uyumsuz programlama (C#)](./index.md)
- [Zaman uyumsuz örnek: uygulamanıza Ince ayar yapma](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
