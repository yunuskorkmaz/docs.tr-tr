---
title: Task.WhenAll (C#) kullanarak async walkthrough nasıl genişletilir
ms.date: 07/20/2015
ms.assetid: f6927ef2-dc6c-43f8-bc82-bbeac42de423
ms.openlocfilehash: afd7dda4e876b7faa54ae4a8e62d640d2b9aaf07
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "73970028"
---
# <a name="how-to-extend-the-async-walkthrough-by-using-taskwhenall-c"></a>Task.WhenAll (C#) kullanarak async walkthrough nasıl genişletilir

[Walkthrough: Accessing the Async'i kullanarak Web'e erişim ve](./walkthrough-accessing-the-web-by-using-async-and-await.md) <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> yöntemi kullanarak (C#) bekleme de kullanılabilir. Bu yöntem, görevler in bir koleksiyon olarak temsil edilen birden çok eşzamanlı işlem bekliyor.

Bu web sitelerinin farklı oranlarda indirmek olduğunu gözden geçirme sırasında fark etmiş olabilirsiniz. Bazen web sitelerinden biri çok yavaştır, bu da kalan tüm indirmeleri geciktirir. İzlenecek yol boyunca oluşturduğunuz eşzamanlı çözümleri çalıştırdığınızda, beklemek istemiyorsanız programı kolayca bitirebilirsiniz, ancak daha iyi bir seçenek tüm indirmeleri aynı anda başlatmak ve daha hızlı indirmelerin bekleyeni beklemeden devam etmesine izin vermektir. Gecikmeli.

`Task.WhenAll` Yöntemi görev koleksiyonuna uygularsınız. Koleksiyondaki `WhenAll` her görev tamamlanana kadar tamamlanmayan tek bir görevin uygulamasını döndürür. Görevler paralel olarak çalışır gibi görünür, ancak ek iş parçacığı oluşturulmaz. Görevler herhangi bir sırada tamamlanabilir.

> [!IMPORTANT]
> Aşağıdaki [yordamlar, Walkthrough: Access ingsync kullanarak web'e erişim ve (C#) bekleyen](./walkthrough-accessing-the-web-by-using-async-and-await.md)async uygulamalarına uzantıları açıklar. Uygulamaları, gözden geçirme yi tamamlayarak veya Geliştirici Kodu [Örneklerinden](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)kodu indirerek geliştirebilirsiniz.
>
> Örneği çalıştırmak için Visual Studio 2012'nin veya daha sonra bilgisayarınıza yüklenmiş olması gerekir.

### <a name="to-add-taskwhenall-to-your-geturlcontentsasync-solution"></a>GetURLContentsAsync çözümünüze Task.WhenAll eklemek için

1. Walkthrough'da geliştirilen ilk uygulamaya `ProcessURLAsync` yöntemi [ekleyin: Async kullanarak Web'e erişim ve bekleme (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md).

    - Kodu [Geliştirici Kodu Örneklerinden](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)indirdiyseniz, AsyncWalkthrough projesini açın `ProcessURLAsync` ve sonra MainWindow.xaml.cs dosyasına ekleyin.

    - Gözden geçirme yöntemini tamamlayarak kodu geliştirdiyseniz, `ProcessURLAsync` `GetURLContentsAsync` yöntemi içeren uygulamaya ekleyin. Bu uygulamanın MainWindow.xaml.cs dosyası, "İzbbölümünden Tam Kod Örnekleri" bölümündeki ilk örnektir.

    Yöntem, `ProcessURLAsync` özgün `foreach` `SumPageSizesAsync` izbinde döngü gövdesindeki eylemleri birleştirir. Yöntem, belirli bir web sitesinin içeriğini bir bayt dizisi olarak eş senkronize olarak indirir ve ardından bayt dizisinin uzunluğunu görüntüler ve döndürür.

    ```csharp
    private async Task<int> ProcessURLAsync(string url)
    {
        var byteArray = await GetURLContentsAsync(url);
        DisplayResults(url, byteArray);
        return byteArray.Length;
    }
    ```

2. Aşağıdaki kodun `foreach` gösterdiği `SumPageSizesAsync`gibi, döngüyü dışarı veya silin.

    ```csharp
    //var total = 0;
    //foreach (var url in urlList)
    //{
    //    byte[] urlContents = await GetURLContentsAsync(url);

    //    // The previous line abbreviates the following two assignment statements.
    //    // GetURLContentsAsync returns a Task<T>. At completion, the task
    //    // produces a byte array.
    //    //Task<byte[]> getContentsTask = GetURLContentsAsync(url);
    //    //byte[] urlContents = await getContentsTask;

    //    DisplayResults(url, urlContents);

    //    // Update the total.
    //    total += urlContents.Length;
    //}
    ```

3. Görevler koleksiyonu oluşturun. Aşağıdaki kod, <xref:System.Linq.Enumerable.ToArray%2A> yöntem tarafından yürütüldüğünde, her web sitesinin içeriğini karşıdan yükleyen bir görev koleksiyonu oluşturan bir [sorgu](../linq/index.md) tanımlar. Sorgu değerlendirildiğinde görevler başlatılır.

    ' nin beyanı `SumPageSizesAsync` ndan sonra yönteme aşağıdaki kodu ekleyin `urlList`

    ```csharp
    // Create a query.
    IEnumerable<Task<int>> downloadTasksQuery =
        from url in urlList select ProcessURLAsync(url);

    // Use ToArray to execute the query and start the download tasks.
    Task<int>[] downloadTasks = downloadTasksQuery.ToArray();
    ```

4. Görevlerin toplanması için `Task.WhenAll` `downloadTasks`uygulayın, . `Task.WhenAll`görevler koleksiyonundaki tüm görevler tamamlandığında tamamlanan tek bir görev döndürür.

    Aşağıdaki örnekte, `await` ifade döndüren `WhenAll` tek görevin tamamlanmasını bekler. İfade, her tamsaın indirilen bir web sitesinin uzunluğu olduğu bir tamsayı dizisine göre değerlendirilir. Önceki adımda `SumPageSizesAsync`eklediğiniz koddan hemen sonra, aşağıdaki kodu ekleyin.

    ```csharp
    // Await the completion of all the running tasks.
    int[] lengths = await Task.WhenAll(downloadTasks);

    //// The previous line is equivalent to the following two statements.
    //Task<int[]> whenAllTask = Task.WhenAll(downloadTasks);
    //int[] lengths = await whenAllTask;
    ```

5. Son olarak, <xref:System.Linq.Enumerable.Sum%2A> tüm web sitelerinin uzunluklarının toplamını hesaplamak için yöntemi kullanın. Aşağıdaki satırı `SumPageSizesAsync`ekleyin.

    ```csharp
    int total = lengths.Sum();
    ```

### <a name="to-add-taskwhenall-to-the-httpclientgetbytearrayasync-solution"></a>HttpClient.GetByteArrayAsync çözümüne Task.WhenAll eklemek için

1. Walkthrough'da `ProcessURLAsync` geliştirilen ikinci uygulamaya aşağıdaki sürümü [ekleyin: Async kullanarak Web'e erişim ve bekleme (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md).

    - Kodu [Geliştirici Kodu Örnekleri'nden](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)indirdiyseniz, AsyncWalkthrough_HttpClient projeyi `ProcessURLAsync` açın ve ardından MainWindow.xaml.cs dosyasına ekleyin.

    - Gözden geçirme yöntemini tamamlayarak kodu geliştirdiyseniz, `ProcessURLAsync` `HttpClient.GetByteArrayAsync` yöntemi kullanan uygulamaya ekleyin. Bu uygulama nın MainWindow.xaml.cs dosyası, "Walkthrough'dan Tam Kod Örnekleri" bölümündeki ikinci örnektir.

    Yöntem, `ProcessURLAsync` özgün `foreach` `SumPageSizesAsync` izbinde döngü gövdesindeki eylemleri birleştirir. Yöntem, belirli bir web sitesinin içeriğini bir bayt dizisi olarak eş senkronize olarak indirir ve ardından bayt dizisinin uzunluğunu görüntüler ve döndürür.

    Önceki yordamda `ProcessURLAsync` yöntemden tek <xref:System.Net.Http.HttpClient> fark, örneğin `client`kullanımıdır.

    ```csharp
    async Task<int> ProcessURLAsync(string url, HttpClient client)
    {
        byte[] byteArray = await client.GetByteArrayAsync(url);
        DisplayResults(url, byteArray);
        return byteArray.Length;
    }
    ```

2. Aşağıdaki kodun `For Each` gösterdiği `foreach` gibi, veya döngüyü `SumPageSizesAsync`silmek veya açıklama yapın.

    ```csharp
    //var total = 0;
    //foreach (var url in urlList)
    //{
    //    // GetByteArrayAsync returns a Task<T>. At completion, the task
    //    // produces a byte array.
    //    byte[] urlContent = await client.GetByteArrayAsync(url);

    //    // The previous line abbreviates the following two assignment
    //    // statements.
    //    Task<byte[]> getContentTask = client.GetByteArrayAsync(url);
    //    byte[] urlContent = await getContentTask;

    //    DisplayResults(url, urlContent);

    //    // Update the total.
    //    total += urlContent.Length;
    //}
    ```

3. Yöntem tarafından yürütüldüğünde, her web sitesinin içeriğini karşıdan yükleyen bir görev koleksiyonu oluşturan bir sorgu tanımlayın. [query](../linq/index.md) <xref:System.Linq.Enumerable.ToArray%2A> Sorgu değerlendirildiğinde görevler başlatılır.

    Beyannameden sonra yönteme `SumPageSizesAsync` aşağıdaki `client` kodu `urlList`ekleyin ve .

    ```csharp
    // Create a query.
    IEnumerable<Task<int>> downloadTasksQuery =
        from url in urlList select ProcessURLAsync(url, client);

    // Use ToArray to execute the query and start the download tasks.
    Task<int>[] downloadTasks = downloadTasksQuery.ToArray();
    ```

4. Ardından, `Task.WhenAll` görevlerin toplanması için `downloadTasks`uygulayın. `Task.WhenAll`görevler koleksiyonundaki tüm görevler tamamlandığında tamamlanan tek bir görev döndürür.

    Aşağıdaki örnekte, `await` ifade döndüren `WhenAll` tek görevin tamamlanmasını bekler. `await` İfade tamamlandığında, her tamsaın indirilen bir web sitesinin uzunluğu olduğu bir dizi tamsayıyı değerlendirir. Önceki adımda `SumPageSizesAsync`eklediğiniz koddan hemen sonra, aşağıdaki kodu ekleyin.

    ```csharp
    // Await the completion of all the running tasks.
    int[] lengths = await Task.WhenAll(downloadTasks);

    //// The previous line is equivalent to the following two statements.
    //Task<int[]> whenAllTask = Task.WhenAll(downloadTasks);
    //int[] lengths = await whenAllTask;
    ```

5. Son olarak, <xref:System.Linq.Enumerable.Sum%2A> tüm web sitelerinin uzunlukları toplamı almak için yöntemi kullanın. Aşağıdaki satırı `SumPageSizesAsync`ekleyin.

    ```csharp
    int total = lengths.Sum();
    ```

### <a name="to-test-the-taskwhenall-solutions"></a>Task.WhenAll çözümlerini test etmek için

- Her iki çözüm için de programı çalıştırmak için F5 tuşunu seçin ve ardından **Başlat** düğmesini seçin. Çıkış Walkthrough async çözümleri çıktı benzer [olmalıdır: async kullanarak Web'e erişim ve bekliyor (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md). Ancak, web sitelerinin her seferinde farklı bir sırada göründüğünü unutmayın.

## <a name="example"></a>Örnek

Aşağıdaki kod, web'den içerik indirmek `GetURLContentsAsync` için yöntemi kullanan proje uzantılarını gösterir.

```csharp
// Add the following using directives, and add a reference for System.Net.Http.
using System.Net.Http;
using System.IO;
using System.Net;

namespace AsyncExampleWPF_WhenAll
{
    public partial class MainWindow : Window
    {
        public MainWindow()
        {
            InitializeComponent();
        }

        private async void startButton_Click(object sender, RoutedEventArgs e)
        {
            resultsTextBox.Clear();

            // Two-step async call.
            Task sumTask = SumPageSizesAsync();
            await sumTask;

            // One-step async call.
            //await SumPageSizesAsync();

            resultsTextBox.Text += "\r\nControl returned to startButton_Click.\r\n";
        }

        private async Task SumPageSizesAsync()
        {
            // Make a list of web addresses.
            List<string> urlList = SetUpURLList();

            // Create a query.
            IEnumerable<Task<int>> downloadTasksQuery =
                from url in urlList select ProcessURLAsync(url);

            // Use ToArray to execute the query and start the download tasks.
            Task<int>[] downloadTasks = downloadTasksQuery.ToArray();

            // You can do other work here before awaiting.

            // Await the completion of all the running tasks.
            int[] lengths = await Task.WhenAll(downloadTasks);

            //// The previous line is equivalent to the following two statements.
            //Task<int[]> whenAllTask = Task.WhenAll(downloadTasks);
            //int[] lengths = await whenAllTask;

            int total = lengths.Sum();

            //var total = 0;
            //foreach (var url in urlList)
            //{
            //    byte[] urlContents = await GetURLContentsAsync(url);

            //    // The previous line abbreviates the following two assignment statements.
            //    // GetURLContentsAsync returns a Task<T>. At completion, the task
            //    // produces a byte array.
            //    //Task<byte[]> getContentsTask = GetURLContentsAsync(url);
            //    //byte[] urlContents = await getContentsTask;

            //    DisplayResults(url, urlContents);

            //    // Update the total.
            //    total += urlContents.Length;
            //}

            // Display the total count for all of the websites.
            resultsTextBox.Text +=
                $"\r\n\r\nTotal bytes returned:  {total}\r\n";
        }

        private List<string> SetUpURLList()
        {
            List<string> urls = new List<string>
            {
                "https://msdn.microsoft.com",
                "https://msdn.microsoft.com/library/windows/apps/br211380.aspx",
                "https://msdn.microsoft.com/library/hh290136.aspx",
                "https://msdn.microsoft.com/library/ee256749.aspx",
                "https://msdn.microsoft.com/library/hh290138.aspx",
                "https://msdn.microsoft.com/library/hh290140.aspx",
                "https://msdn.microsoft.com/library/dd470362.aspx",
                "https://msdn.microsoft.com/library/aa578028.aspx",
                "https://msdn.microsoft.com/library/ms404677.aspx",
                "https://msdn.microsoft.com/library/ff730837.aspx"
            };
            return urls;
        }

        // The actions from the foreach loop are moved to this async method.
        private async Task<int> ProcessURLAsync(string url)
        {
            var byteArray = await GetURLContentsAsync(url);
            DisplayResults(url, byteArray);
            return byteArray.Length;
        }

        private async Task<byte[]> GetURLContentsAsync(string url)
        {
            // The downloaded resource ends up in the variable named content.
            var content = new MemoryStream();

            // Initialize an HttpWebRequest for the current URL.
            var webReq = (HttpWebRequest)WebRequest.Create(url);

            // Send the request to the Internet resource and wait for
            // the response.
            using (WebResponse response = await webReq.GetResponseAsync())
            {
                // Get the data stream that is associated with the specified url.
                using (Stream responseStream = response.GetResponseStream())
                {
                    await responseStream.CopyToAsync(content);
                }
            }

            // Return the result as a byte array.
            return content.ToArray();

        }

        private void DisplayResults(string url, byte[] content)
        {
            // Display the length of each website. The string format
            // is designed to be used with a monospaced font, such as
            // Lucida Console or Global Monospace.
            var bytes = content.Length;
            // Strip off the "https://".
            var displayURL = url.Replace("https://", "");
            resultsTextBox.Text += $"\n{displayURL,-58} {bytes,8}";
        }
    }
}
```

## <a name="example"></a>Örnek

Aşağıdaki kod, web'den içerik indirmek `HttpClient.GetByteArrayAsync` için yöntem kullanan proje uzantılarını gösterir.

```csharp
// Add the following using directives, and add a reference for System.Net.Http.
using System.Net.Http;
using System.IO;
using System.Net;

namespace AsyncExampleWPF_HttpClient_WhenAll
{
    public partial class MainWindow : Window
    {
        public MainWindow()
        {
            InitializeComponent();
        }

        private async void startButton_Click(object sender, RoutedEventArgs e)
        {
            resultsTextBox.Clear();

            // One-step async call.
            await SumPageSizesAsync();

            // Two-step async call.
            //Task sumTask = SumPageSizesAsync();
            //await sumTask;

            resultsTextBox.Text += "\r\nControl returned to startButton_Click.\r\n";
        }

        private async Task SumPageSizesAsync()
        {
            // Make a list of web addresses.
            List<string> urlList = SetUpURLList();

            // Declare an HttpClient object and increase the buffer size. The
            // default buffer size is 65,536.
            HttpClient client = new HttpClient() { MaxResponseContentBufferSize = 1000000 };

            // Create a query.
            IEnumerable<Task<int>> downloadTasksQuery =
                from url in urlList select ProcessURLAsync(url, client);

            // Use ToArray to execute the query and start the download tasks.
            Task<int>[] downloadTasks = downloadTasksQuery.ToArray();

            // You can do other work here before awaiting.

            // Await the completion of all the running tasks.
            int[] lengths = await Task.WhenAll(downloadTasks);

            //// The previous line is equivalent to the following two statements.
            //Task<int[]> whenAllTask = Task.WhenAll(downloadTasks);
            //int[] lengths = await whenAllTask;

            int total = lengths.Sum();

            //var total = 0;
            //foreach (var url in urlList)
            //{
            //    // GetByteArrayAsync returns a Task<T>. At completion, the task
            //    // produces a byte array.
            //    byte[] urlContent = await client.GetByteArrayAsync(url);

            //    // The previous line abbreviates the following two assignment
            //    // statements.
            //    Task<byte[]> getContentTask = client.GetByteArrayAsync(url);
            //    byte[] urlContent = await getContentTask;

            //    DisplayResults(url, urlContent);

            //    // Update the total.
            //    total += urlContent.Length;
            //}

            // Display the total count for all of the web addresses.
            resultsTextBox.Text +=
                $"\r\n\r\nTotal bytes returned:  {total}\r\n";
        }

        private List<string> SetUpURLList()
        {
            List<string> urls = new List<string>
            {
                "https://msdn.microsoft.com",
                "https://msdn.microsoft.com/library/hh290136.aspx",
                "https://msdn.microsoft.com/library/ee256749.aspx",
                "https://msdn.microsoft.com/library/hh290138.aspx",
                "https://msdn.microsoft.com/library/hh290140.aspx",
                "https://msdn.microsoft.com/library/dd470362.aspx",
                "https://msdn.microsoft.com/library/aa578028.aspx",
                "https://msdn.microsoft.com/library/ms404677.aspx",
                "https://msdn.microsoft.com/library/ff730837.aspx"
            };
            return urls;
        }

        // The actions from the foreach loop are moved to this async method.
        async Task<int> ProcessURLAsync(string url, HttpClient client)
        {
            byte[] byteArray = await client.GetByteArrayAsync(url);
            DisplayResults(url, byteArray);
            return byteArray.Length;
        }

        private void DisplayResults(string url, byte[] content)
        {
            // Display the length of each web site. The string format
            // is designed to be used with a monospaced font, such as
            // Lucida Console or Global Monospace.
            var bytes = content.Length;
            // Strip off the "https://".
            var displayURL = url.Replace("https://", "");
            resultsTextBox.Text += $"\n{displayURL,-58} {bytes,8}";
        }
    }
}
```

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>
- [Walkthrough: Async kullanarak Web'e erişim ve bekleme (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md)
