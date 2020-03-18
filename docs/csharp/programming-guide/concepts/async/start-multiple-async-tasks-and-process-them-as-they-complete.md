---
title: Eşzamanlı görevleri tamamlarken işleme
ms.date: 09/12/2018
ms.assetid: 25331850-35a7-43b3-ab76-3908e4346b9d
ms.openlocfilehash: b618fd6bf80551231d2b285fd0e8aef688d00d93
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "71736725"
---
# <a name="start-multiple-async-tasks-and-process-them-as-they-complete-c"></a>Birden Çok Async Görevi Başlatın ve Tamamlanındıkları Gibi İşleyin (C#)

Kullanarak, <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>birden çok görevi aynı anda başlatabilir ve başlatıldıkları sırada işlemek yerine tamamlandıkları gibi tek tek işleyebilirsiniz.

Aşağıdaki örnekte, görev koleksiyonu oluşturmak için bir sorgu kullanır. Her görev, belirli bir web sitesinin içeriğini indirir. Bir while döngüsünün her yinelemesinde, önce `WhenAny` karşıdan yüklemeyi tamamlayan görevler koleksiyonundaki görevi döndürecek beklenen bir çağrı. Bu görev koleksiyondan kaldırılır ve işlenir. Döngü, koleksiyon başka görev içermeyene kadar yinelenir.

> [!NOTE]
> Örnekleri çalıştırmak için Visual Studio (2012 veya daha yeni) ve .NET Framework 4.5 veya daha yeni bilgisayarınıza yüklü olması gerekir.

## <a name="download-an-example-solution"></a>Örnek bir çözüm indirin

Windows Presentation Foundation (WPF) projesinin tamamını [Async Sample: Fine Tuning Application'dan](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) indirebilir ve ardından aşağıdaki adımları izleyebilirsiniz.

> [!TIP]
> Projeyi karşıdan indirmek istemiyorsanız, bunun yerine bu konunun sonundaki *MainWindow.xaml.cs* dosyayı gözden geçirebilirsiniz.

1. *.zip* dosyasından indirdiğiniz dosyaları ayıklayın ve Visual Studio'yu başlatın.

2. Menü çubuğunda **Dosya** > **Aç** > **Projesi/Çözümü'nü**seçin.

3. **Projeyi Aç** iletişim kutusunda, indirdiğiniz örnek kodu tutan klasörü açın ve ardından *AsyncFineTuningCS*/*AsyncFineTuningVB*için çözüm (*.sln*) dosyasını açın.

4. **Çözüm Gezgini'nde,** **ProcessTasksAsTheyFinish** projesi için kısayol menüsünü açın ve ardından **StartUp Project olarak ayarla'yı**seçin.

5. Programı hata ayıklama yla çalıştırmak için <kbd>F5</kbd> tuşunu seçin veya programı hata ayıklamadan çalıştırmak için <kbd>Ctrl</kbd>+<kbd>F5</kbd> tuşlarına basın.

6. İndirilen uzunlukların her zaman aynı sırada görünmediğini doğrulamak için projeyi birkaç kez çalıştırın.

## <a name="create-the-program-yourself"></a>Programı kendiniz oluşturun

Bu örnek, Bir Tamamlandıktan Sonra [Kalan Async Görevlerini İptal (C#)](cancel-remaining-async-tasks-after-one-is-complete.md)olarak geliştirilen kodu ekler ve aynı UI'yi kullanır.

Örneği adım adım oluşturmak [için, Örnek İndirme](cancel-remaining-async-tasks-after-one-is-complete.md#downloading-the-example) bölümündeki yönergeleri izleyin, ancak başlangıç projesi olarak **CancelAfterOneTask'ı** ayarlayın. Bu konudaki değişiklikleri bu `AccessTheWebAsync` projedeki yönteme ekleyin. Değişiklikler yıldız işaretleriyle işaretlenir.

**CancelAfterOneTask** projesi zaten yürütüldüğünde bir görev koleksiyonu oluşturan bir sorgu içerir. Aşağıdaki `ProcessURLAsync` koddaki her arama, <xref:System.Threading.Tasks.Task%601>bir `TResult` tamsayı olduğu bir , döndürür:

```csharp
IEnumerable<Task<int>> downloadTasksQuery = from url in urlList select ProcessURL(url, client, ct);
```

Projenin *MainWindow.xaml.cs* dosyasında, yöntemde `AccessTheWebAsync` aşağıdaki değişiklikleri yapın:

- <xref:System.Linq.Enumerable.ToArray%2A>Yerine uygulayarak <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> sorguyu yürütün

    ```csharp
    List<Task<int>> downloadTasks = downloadTasksQuery.ToList();
    ```

- Koleksiyondaki `while` her görev için aşağıdaki adımları gerçekleştiren bir döngü ekleyin:

    1. İndirmeyi tamamlamak `WhenAny` için koleksiyondaki ilk görevi belirlemek için bir çağrı bekler.

        ```csharp
        Task<int> firstFinishedTask = await Task.WhenAny(downloadTasks);
        ```

    2. Bu görevi koleksiyondan kaldırır.

        ```csharp
        downloadTasks.Remove(firstFinishedTask);
        ```

    3. Bekliyor `firstFinishedTask`, bir çağrı ile `ProcessURLAsync`döndürülür . `firstFinishedTask` Değişken bir <xref:System.Threading.Tasks.Task%601> tamsayı `TReturn` dır. Görev zaten tamamlandı, ancak aşağıdaki örnekte görüldüğü gibi, indirilen web sitesinin uzunluğunu almak için onu bekliyorsunuz. Görev `await` hatalı ise, ilk çocuk özel durum depolanan `AggregateException`atacaktır `Result` , hangi atmak `AggregateException`istiyorsunuz özelliği okuma aksine .

        ```csharp
        int length = await firstFinishedTask;
        resultsTextBox.Text += $"\r\nLength of the download:  {length}";
        ```

İndirilen uzunlukların her zaman aynı sırada görünmediğini doğrulamak için programı birkaç kez çalıştırın.

> [!CAUTION]
> Az sayıda `WhenAny` görev içeren sorunları çözmek için örnekte açıklandığı gibi bir döngüde kullanabilirsiniz. Ancak, işlemek için çok sayıda göreviniz varsa, diğer yaklaşımlar daha verimlidir. Daha fazla bilgi ve örnek için, [görevleri tamamlarken işleme ye](https://devblogs.microsoft.com/pfxteam/processing-tasks-as-they-complete/)bakın.

## <a name="complete-example"></a>Tam örnek

Aşağıdaki kod, örnek için *MainWindow.xaml.cs* dosyasının tam metnidir. Yıldız işaretleri, bu örnek için eklenen öğeleri işaretler. Ayrıca, <xref:System.Net.Http>için bir başvuru eklemeniz gerektiğini unutmayın.

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
- [Async Uygulamanızda İnce Ayar (C#)](fine-tuning-your-async-application.md)
- [Async ve await ile Asynchronous Programlama (C#)](index.md)
- [Async Örnek: Uygulamanızı İyi Ayar](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
