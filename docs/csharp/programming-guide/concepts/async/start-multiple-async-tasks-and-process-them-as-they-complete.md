---
title: Zaman uyumsuz görevleri tamamlandıkça işleme
ms.date: 09/12/2018
ms.assetid: 25331850-35a7-43b3-ab76-3908e4346b9d
ms.openlocfilehash: ec5729eaa8d63eb18b1ac4dea5820cbf834d001b
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53152376"
---
# <a name="start-multiple-async-tasks-and-process-them-as-they-complete-c"></a>Birden çok zaman uyumsuz görev başlatma ve bunlar (C#) tamamlandıkça işleme

Kullanarak <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>, birden çok görev aynı anda başlatmak ve bunların yerine gibi bunlar başlatıldığında sırayla işlenecekleri birer birer işlem.

Aşağıdaki örnek, bir görev koleksiyonu oluşturmak için bir sorgu kullanır. Her görev, belirtilen bir Web sitesinin içeriklerini karşıdan yükler. Her yinelemede while döngüsü, bekletilen çağrısı `WhenAny` görev, kendi indirmesi biten koleksiyonundaki görevleri döndürür. Bu görev koleksiyondan kaldırılır ve işlenir. Döngü koleksiyonda artık başka görev kalmayana kadar yinelenir.

> [!NOTE]
> Yeni bilgisayarınızda yüklü veya örnekleri çalıştırmak için (2012 veya sonrası) Visual Studio ve .NET Framework 4.5 yüklü olmalıdır.

## <a name="download-an-example-solution"></a>Bir örnek çözümü indirin

Tüm Windows Presentation Foundation (WPF) projeden indirebileceğiniz [zaman uyumsuz örneği: Uygulamanıza ince](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) ve sonra aşağıdaki adımları izleyin.

> [!TIP]
> Projeyi indirmek istemiyorsanız, bunun yerine bu konunun sonunda MainWindow.xaml.cs dosyasını gözden geçirebilirsiniz.

1.  Yüklediğiniz .zip dosyasından dosyaları ayıklayın ve sonra Visual Studio'yu başlatın.

2.  Menü çubuğunda, **dosya** > **açık** > **proje/çözüm**.

3.  İçinde **Proje Aç** iletişim kutusunda, indirdiğiniz örnek kodu barındıran klasörü açın ve ardından AsyncFineTuningCS için çözüm (.sln) dosyasını açın.

4.  İçinde **Çözüm Gezgini**, kısayol menüsünü açın **ProcessTasksAsTheyFinish** proje ve ardından **başlangıç projesi olarak ayarla**.

5.  Seçin **F5** programı çalıştırmak için anahtar (veya basın **Ctrl**+**F5** anahtarları, hata ayıklama olmadan programı çalıştırmak için).

6.  Proje, indirilen uzunlukların her zaman aynı sırada görüntülenmediğini doğrulamak için birkaç kez çalıştırın.

## <a name="create-the-program-yourself"></a>Programı kendiniz oluşturun

Bu örnek içinde geliştirilen koda eklenir [sonra bir tamamlandı (C#) kalan zaman uyumsuz görevleri iptal](../../../../csharp/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md), ve aynı kullanıcı arabirimini kullanır.

Kendiniz adım adım örnek oluşturmak için aşağıdaki yönergeleri izleyin [örneği indirme](../../../../csharp/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md#downloading-the-example) bölümünde, ancak ayarlanmış **CancelAfterOneTask** başlangıç projesi olarak. Bu konudaki değişiklikleri ekleyin `AccessTheWebAsync` projedeki yöntemi. Değişiklikler, yıldız işareti ile işaretlenir.

**CancelAfterOneTask** proje zaten bir sorgu içerir, çalıştırıldığında bir görev koleksiyonu oluşturur. Her çağrı `ProcessURLAsync` döndürür aşağıdaki kodda bir <xref:System.Threading.Tasks.Task%601>burada `TResult` bir tamsayıdır:

```csharp
IEnumerable<Task<int>> downloadTasksQuery = from url in urlList select ProcessURL(url, client, ct);
```

Proje MainWindow.xaml.cs dosyasında aşağıdaki değişiklikleri `AccessTheWebAsync` yöntemi.

-   Uygulayarak sorguyu yürütün <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> yerine <xref:System.Linq.Enumerable.ToArray%2A>.

    ```csharp
    List<Task<int>> downloadTasks = downloadTasksQuery.ToList();
    ```

-   Ekleme bir `while` döngü koleksiyondaki her görev için aşağıdaki adımları gerçekleştirir:

    1.  Bir çağrı bekler `WhenAny` karşıdan yüklemesini tamamlamak için koleksiyondaki ilk görevi tanımlamak için.

        ```csharp
        Task<int> firstFinishedTask = await Task.WhenAny(downloadTasks);
        ```

    2.  Bu görev koleksiyondan kaldırır.

        ```csharp
        downloadTasks.Remove(firstFinishedTask);
        ```

    3.  Bekler `firstFinishedTask`, bir çağrı tarafından döndürülen `ProcessURLAsync`. `firstFinishedTask` Değişken bir <xref:System.Threading.Tasks.Task%601> burada `TReturn` bir tamsayıdır. Görev zaten tamamlandıysa, ancak karşıdan yüklenen Web sitesi uzunluğunu aşağıdaki örnekte gösterildiği gibi almak için bekler.

        ```csharp
        int length = await firstFinishedTask;
        resultsTextBox.Text += $"\r\nLength of the download:  {length}";
        ```

İndirilen uzunlukların her zaman aynı sırada görüntülenmediğini doğrulamak için birkaç kez programı'nı çalıştırın.

> [!CAUTION]
> Kullanabileceğiniz `WhenAny` az sayıda görev içeren sorunlar çözmek için örnekte açıklandığı bir döngüde. Ancak, diğer yaklaşımlar çok sayıda işlemek için görevler varsa daha verimlidir. Daha fazla bilgi ve örnekler için bkz. [görevleri tamamlandıkça işleme](https://blogs.msdn.microsoft.com/pfxteam/2012/08/02/processing-tasks-as-they-complete/).

## <a name="complete-example"></a>Tam örnek

Aşağıdaki kod örneği için MainWindow.xaml.cs dosyasının tam metindir. Yıldız işaretleri, bu örnek için eklenen öğeleri işaretler. Ayrıca, bir başvuru için eklemeniz gereken Not <xref:System.Net.Http>.

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

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading.Tasks.Task.WhenAny%2A>
- [(C#) Async uygulamanızda hassas ayar yapma](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md)
- [Zaman uyumsuz programlama ile async ve await (C#)](../../../../csharp/programming-guide/concepts/async/index.md)
- [Zaman uyumsuz örneği: Uygulamanızda hassas ayar yapma](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)