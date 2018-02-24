---
title: "Birden çok zaman uyumsuz görev başlatma ve bunlar (C#) tamamlandıkça işleme"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
ms.assetid: 25331850-35a7-43b3-ab76-3908e4346b9d
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: a5339e1d2d592f3ae2a2b5c0e4e96e2bff2df64c
ms.sourcegitcommit: cec0525b2121c36198379525e69aa5388266db5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/23/2018
---
# <a name="start-multiple-async-tasks-and-process-them-as-they-complete-c"></a>Birden çok zaman uyumsuz görev başlatma ve bunlar (C#) tamamlandıkça işleme
Kullanarak <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>, aynı anda birden çok görevi başlatma ve bunlar tamamlandı yerine bunların başlatılan sırayla işlem onları tek tek işleme.  
  
 Aşağıdaki örnek sorguda görevleri koleksiyonu oluşturmak için kullanır. Her görev, belirtilen bir Web sitesi içeriğini indirir. Her bir süre tekrarında döngü, awaited çağrısına `WhenAny` görev, kendi yükleme ilk bittikten koleksiyondaki görevlerin döndürür. Bu görev koleksiyondan kaldırıldı ve işlenebilir. Daha fazla görev koleksiyon içerene kadar döngü tekrarlar.  
  
> [!NOTE]
>  Örnekleri çalıştırmak için Visual Studio 2012 veya daha yeni ve .NET Framework 4.5 olmalıdır veya daha yeni bilgisayarınızda yüklü.  
  
## <a name="downloading-the-example"></a>Örnek indirme  
 Tam Windows Presentation Foundation (WPF) projeden indirebilirsiniz [zaman uyumsuz örnek: ince ayar uygulamanız](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) ve ardından aşağıdaki adımları izleyin.  
  
1.  İndirdiğiniz dosyanın sıkıştırmasını ve Visual Studio'yu başlatın.  
  
2.  Menü çubuğunda seçin **dosya**, **açık**, **proje/çözüm**.  
  
3.  İçinde **Proje Aç** iletişim kutusunda, sıkıştırması örnek kod tutan klasörü açın ve ardından AsyncFineTuningCS için çözüm (.sln) dosyasını açın.  
  
4.  İçinde **Çözüm Gezgini**, kısayol menüsünü açın **ProcessTasksAsTheyFinish** proje ve ardından **başlangıç projesi olarak ayarla**.  
  
5.  Projeyi çalıştırmak için F5 tuşuna seçin.  
  
     Hata ayıklama olmadan projeyi çalıştırmak için Ctrl + F5 anahtarları'i seçin.  
  
6.  Proje indirilen uzunlukları her zaman aynı sırada görünmüyor doğrulamak için birkaç kez çalıştırın.  
  
 Projenizi indirin istemiyorsanız, bu konunun sonundaki MainWindow.xaml.cs dosyasını gözden geçirebilirsiniz.  
  
## <a name="building-the-example"></a>Örnek oluşturma  
 Bu örnek da geliştirilmiş kod ekler [bir tamamlandı (C#) sonra geri kalan zaman uyumsuz görevleri iptal](../../../../csharp/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)[bir tamamlandı sonra geri kalan zaman uyumsuz görevleri iptal](http://msdn.microsoft.com/library/8e800b58-235a-44b7-a02c-fa4375591d76) ve aynı kullanıcı arabirimini kullanır.  
  
 Örnek oluşturmak için kendiniz, adım adım "örnek indirme" bölümündeki yönergeleri izleyin, ancak seçin **CancelAfterOneTask** olarak **başlangıç projesi**. İçin bu konudaki değişiklikleri eklemek `AccessTheWebAsync` projedeki yöntemi. Değişiklikler yıldız işaretiyle işaretlenir.  
  
 **CancelAfterOneTask** proje zaten bir sorgu içeriyor, çalıştırıldığında, görevleri koleksiyonu oluşturur. Her çağrı `ProcessURLAsync` aşağıdaki kodda döndüren bir <xref:System.Threading.Tasks.Task%601> burada `TResult` bir tamsayıdır.  
  
```csharp  
IEnumerable<Task<int>> downloadTasksQuery =  
    from url in urlList select ProcessURL(url, client, ct);  
```  
  
 Proje MainWindow.xaml.cs dosyasında aşağıdaki değişiklikleri `AccessTheWebAsync` yöntemi.  
  
-   Uygulayarak sorguyu yürütmek <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> yerine <xref:System.Linq.Enumerable.ToArray%2A>.  
  
    ```csharp  
    List<Task<int>> downloadTasks = downloadTasksQuery.ToList();  
    ```  
  
-   Biraz eklemek koleksiyondaki her görev için aşağıdaki adımları gerçekleştirir döngü.  
  
    1.  Çağrı bekler `WhenAny` kendi indirme tamamlamak için koleksiyondaki ilk görevi tanımlamak için.  
  
        ```csharp  
        Task<int> firstFinishedTask = await Task.WhenAny(downloadTasks);  
        ```  
  
    2.  Bu görev koleksiyondan kaldırır.  
  
        ```csharp  
        downloadTasks.Remove(firstFinishedTask);  
        ```  
  
    3.  Bekler `firstFinishedTask`, bir çağrı tarafından döndürülen `ProcessURLAsync`. `firstFinishedTask` Değişkeni, bir <xref:System.Threading.Tasks.Task%601> burada `TReturn` bir tamsayıdır. Görev zaten tamamlandı, ancak uzunluğu indirilen Web sitesi, aşağıdaki örnekte gösterildiği gibi almak bekler.  
  
        ```csharp  
        int length = await firstFinishedTask;  
        resultsTextBox.Text += String.Format("\r\nLength of the download:  {0}", length);  
        ```  
  
 Proje indirilen uzunlukları her zaman aynı sırada görünmüyor doğrulamak için birkaç kez çalıştırmanız gerekir.  
  
> [!CAUTION]
>  Kullanabileceğiniz `WhenAny` küçük birkaç görev ile ilgili sorunları çözmek için örnekte açıklandığı gibi bir Döngüdeki. Ancak, diğer yaklaşımlar görevler işlemek için çok sayıda varsa daha verimlidir. Daha fazla bilgi ve örnekler için bkz: [görevleri tamamlandıkça işleme](https://blogs.msdn.microsoft.com/pfxteam/2012/08/02/processing-tasks-as-they-complete/).  
  
## <a name="complete-example"></a>Tam Örnek  
 Aşağıdaki kod örneğin MainWindow.xaml.cs dosyasının tam metindir. Yıldız işareti, bu örnek için eklenen öğeleri işaretleyin.  
  
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
                    resultsTextBox.Text += String.Format("\r\nLength of the download:  {0}", length);  
            }  
        }  
  
        private List<string> SetUpURLList()  
        {  
            List<string> urls = new List<string>   
            {   
                "http://msdn.microsoft.com",  
                "http://msdn.microsoft.com/library/windows/apps/br211380.aspx",  
                "http://msdn.microsoft.com/library/hh290136.aspx",  
                "http://msdn.microsoft.com/library/dd470362.aspx",  
                "http://msdn.microsoft.com/library/aa578028.aspx",  
                "http://msdn.microsoft.com/library/ms404677.aspx",  
                "http://msdn.microsoft.com/library/ff730837.aspx"  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Threading.Tasks.Task.WhenAny%2A>  
 [(C#) Async uygulamanızda hassas ayar yapma](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md)  
 [Zaman uyumsuz programlama ile async ve await (C#)](../../../../csharp/programming-guide/concepts/async/index.md)  
 [Zaman uyumsuz örnek: İnce uygulamanızı ayarlama](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
