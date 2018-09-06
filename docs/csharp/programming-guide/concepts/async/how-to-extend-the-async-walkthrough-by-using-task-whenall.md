---
title: 'Nasıl yapılır: zaman uyumsuz izlenecek yolu Task.WhenAll (C#) kullanarak genişletme'
ms.date: 07/20/2015
ms.assetid: f6927ef2-dc6c-43f8-bc82-bbeac42de423
ms.openlocfilehash: 241bd6baf0c1133ba7603da433a7cdf8d36748c0
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43881084"
---
# <a name="how-to-extend-the-async-walkthrough-by-using-taskwhenall-c"></a>Nasıl yapılır: zaman uyumsuz izlenecek yolu Task.WhenAll (C#) kullanarak genişletme
İçinde zaman uyumsuz çözümün performansını artırabilirsiniz [izlenecek yol: async kullanarak Web'e erişme ve await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md) kullanarak <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> yöntemi. Bu yöntem, zaman uyumsuz olarak görevleri topluluğu temsil edilen birden çok zaman uyumsuz işlemler bekler.  
  
 Web sitelerinin indirme hızlarının farklı izlenecek yolda etmiş olabilirsiniz. Bazen, Web siteleri, kalan tüm indirmeleri geciktirir çok yavaş biridir. Anlatımda oluşturduğunuz zaman uyumsuz çözümleri çalıştırdığınızda, program kolayca beklemek istemiyorsanız, ancak tüm indirmeleri aynı anda başlatmak ve devam etmek için beklemenize gerek kalmadan daha hızlı indirmeler izin vermek için daha iyi bir seçenek olacaktır sona erdirebilirsiniz ait  ertelendi.  
  
 Uyguladığınız `Task.WhenAll` yöntemi için bir görev koleksiyonu. Uygulamayı `WhenAll` koleksiyondaki her görev tamamlanıncaya kadar tam olmayan tek bir görev döndürür. Görevler paralel olarak çalışır gibigörünür, ancak hiçbir ek iş parçacığı oluşturulmaz. Görevler herhangi bir sırada tamamlayabilir.  
  
> [!IMPORTANT]
>  Aşağıdaki yordamlar içinde geliştirilen zaman uyumsuz uygulamaların uzantılarını açıklamaktadır [izlenecek yol: async kullanarak Web'e erişme ve await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md). İzlenecek yolu tamamlayarak veya kodu indiriliyor tarafından uygulamalar geliştirebilirsiniz [geliştirici kodu örnekleri](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).  
>   
>  Örneği çalıştırmak için Visual Studio 2012 olmalıdır veya üzeri yüklü.  
  
### <a name="to-add-taskwhenall-to-your-geturlcontentsasync-solution"></a>GetURLContentsAsync çözümünüze Task.WhenAll eklemek için  
  
1.  Ekleme `ProcessURLAsync` yöntemi içinde geliştirilen ilk uygulamaya [izlenecek yol: async kullanarak Web'e erişme ve await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).  
  
    -   Koddan indirdiyseniz [geliştirici kodu örnekleri](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f), AsyncWalkthrough projesini açın ve ardından eklemek `ProcessURLAsync` MainWindow.xaml.cs dosyasına.  
  
    -   İzlenecek yolu tamamlayarak kodu geliştirdiyseniz, ekleme `ProcessURLAsync` içeren uygulamaya `GetURLContentsAsync` yöntemi. Bu uygulama için MainWindow.xaml.cs dosyası "Tam kod örnekleri" izlenecek yoldan"bölümündeki ilk örnektir.  
  
     `ProcessURLAsync` Yöntem gövdesindeki eylemleri birleştirir `foreach` içinde döngü `SumPageSizesAsync` özgün izlenecek yolda. Yöntemi zaman uyumsuz olarak bir bayt dizisi olarak belirtilen bir Web sitesinin içeriklerini karşıdan yükler ve ardından görüntüler ve bayt dizisinin uzunluğunu döndürür.  
  
    ```csharp  
    private async Task<int> ProcessURLAsync(string url)  
    {  
        var byteArray = await GetURLContentsAsync(url);  
        DisplayResults(url, byteArray);  
        return byteArray.Length;  
    }  
    ```  
  
2.  Açıklama satırı yapın veya silin `foreach` içinde döngü `SumPageSizesAsync`aşağıdaki kodda gösterildiği gibi.  
  
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
  
3.  Bir görev koleksiyonu oluşturun. Aşağıdaki kodu tanımlayan bir [sorgu](../../../../csharp/programming-guide/concepts/linq/index.md) , tarafından yürütüldüğünde <xref:System.Linq.Enumerable.ToArray%2A> yöntemi, her bir Web sitesinin içeriklerini indiren bir görev koleksiyonunu oluşturur. Sorgu çalışırken görevler başlatılır.  
  
     Yöntemine aşağıdaki kodu ekleyin `SumPageSizesAsync` bildiriminin `urlList`.  
  
    ```csharp  
    // Create a query.   
    IEnumerable<Task<int>> downloadTasksQuery =   
        from url in urlList select ProcessURLAsync(url);  
  
    // Use ToArray to execute the query and start the download tasks.  
    Task<int>[] downloadTasks = downloadTasksQuery.ToArray();  
    ```  
  
4.  Uygulama `Task.WhenAll` görevler koleksiyonuna `downloadTasks`. `Task.WhenAll` Görevler koleksiyondaki tüm görevler tamamlandığında sona tek bir görev döndürür.  
  
     Aşağıdaki örnekte, `await` ifade tek tamalanmasını görevin `WhenAll` döndürür. İfade bir her tamsayının indirilen bir Web sitesinin uzunluğu olduğu bir tamsayılar dizisi olarak değerlendirilir. Aşağıdaki kodu ekleyin `SumPageSizesAsync`, yalnızca önceki adımda eklediğiniz koddan sonra.  
  
    ```csharp  
    // Await the completion of all the running tasks.  
    int[] lengths = await Task.WhenAll(downloadTasks);  
  
    //// The previous line is equivalent to the following two statements.  
    //Task<int[]> whenAllTask = Task.WhenAll(downloadTasks);  
    //int[] lengths = await whenAllTask;  
    ```  
  
5.  Son olarak, <xref:System.Linq.Enumerable.Sum%2A> tüm Web sitelerinin uzunluklarının toplamını hesaplamak için yöntemi. Aşağıdaki satırı ekleyin `SumPageSizesAsync`.  
  
    ```csharp  
    int total = lengths.Sum();  
    ```  
  
### <a name="to-add-taskwhenall-to-the-httpclientgetbytearrayasync-solution"></a>HttpClient.GetByteArrayAsync çözümüne Task.WhenAll eklemek için  
  
1.  Aşağıdaki sürümü ekleme `ProcessURLAsync` içinde geliştirilen ikinci uygulamaya [izlenecek yol: async kullanarak Web'e erişme ve await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).  
  
    -   Koddan indirdiyseniz [geliştirici kodu örnekleri](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f), AsyncWalkthrough_HttpClient projesini açın ve ardından eklemek `ProcessURLAsync` MainWindow.xaml.cs dosyasına.  
  
    -   İzlenecek yolu tamamlayarak kodu geliştirdiyseniz, ekleme `ProcessURLAsync` kullanan uygulamaya `HttpClient.GetByteArrayAsync` yöntemi. Bu uygulama için MainWindow.xaml.cs dosyası "Tam kod örnekleri" izlenecek yoldan"bölümündeki ikinci örnektir.  
  
     `ProcessURLAsync` Yöntem gövdesindeki eylemleri birleştirir `foreach` içinde döngü `SumPageSizesAsync` özgün izlenecek yolda. Yöntemi zaman uyumsuz olarak bir bayt dizisi olarak belirtilen bir Web sitesinin içeriklerini karşıdan yükler ve ardından görüntüler ve bayt dizisinin uzunluğunu döndürür.  
  
     Tek farkı `ProcessURLAsync` yöntemdir önceki yordamda kullanımını <xref:System.Net.Http.HttpClient> örneği `client`.  
  
    ```csharp  
    async Task<int> ProcessURL(string url, HttpClient client)  
    {  
        byte[] byteArray = await client.GetByteArrayAsync(url);  
        DisplayResults(url, byteArray);  
        return byteArray.Length;  
    }  
    ```  
  
2.  Açıklama satırı yapın veya silin `For Each` veya `foreach` içinde döngü `SumPageSizesAsync`aşağıdaki kodda gösterildiği gibi.  
  
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
  
3.  Tanımlayan bir [sorgu](../../../../csharp/programming-guide/concepts/linq/index.md) , tarafından yürütüldüğünde <xref:System.Linq.Enumerable.ToArray%2A> yöntemi, her bir Web sitesinin içeriklerini indiren bir görev koleksiyonunu oluşturur. Sorgu çalışırken görevler başlatılır.  
  
     Yöntemine aşağıdaki kodu ekleyin `SumPageSizesAsync` bildiriminin `client` ve `urlList`.  
  
    ```csharp  
    // Create a query.  
    IEnumerable<Task<int>> downloadTasksQuery =   
        from url in urlList select ProcessURL(url, client);  
  
    // Use ToArray to execute the query and start the download tasks.  
    Task<int>[] downloadTasks = downloadTasksQuery.ToArray();  
    ```  
  
4.  Ardından, uygulama `Task.WhenAll` görevler koleksiyonuna `downloadTasks`. `Task.WhenAll` Görevler koleksiyondaki tüm görevler tamamlandığında sona tek bir görev döndürür.  
  
     Aşağıdaki örnekte, `await` ifade tek tamalanmasını görevin `WhenAll` döndürür. İşlem tamamlandığında `await` ifade bir her tamsayının indirilen bir Web sitesinin uzunluğu olduğu bir tamsayılar dizisi olarak değerlendirilir. Aşağıdaki kodu ekleyin `SumPageSizesAsync`, yalnızca önceki adımda eklediğiniz koddan sonra.  
  
    ```csharp  
    // Await the completion of all the running tasks.  
    int[] lengths = await Task.WhenAll(downloadTasks);  
  
    //// The previous line is equivalent to the following two statements.  
    //Task<int[]> whenAllTask = Task.WhenAll(downloadTasks);  
    //int[] lengths = await whenAllTask;  
    ```  
  
5.  Son olarak, <xref:System.Linq.Enumerable.Sum%2A> tüm Web sitelerinin uzunluklarının toplamını almak için yöntemi. Aşağıdaki satırı ekleyin `SumPageSizesAsync`.  
  
    ```csharp  
    int total = lengths.Sum();
    ```  
  
### <a name="to-test-the-taskwhenall-solutions"></a>Task.WhenAll çözümlerini test etmek için  
  
-   Her çözüm için programı çalıştırmak için F5 tuşuna basın ve ardından **Başlat** düğmesi. Zaman uyumsuz çözümleri çıkışı çıktıya benzemelidir [izlenecek yol: async kullanarak Web'e erişme ve await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md). Ancak, Web sitelerinin her seferinde farklı bir sırada görüntülendiğine dikkat edin.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kodu kullanan proje uzantılarını göstermektedir `GetURLContentsAsync` içeriği Web'den yüklemek için yöntemi.  
  
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
                string.Format("\r\n\r\nTotal bytes returned:  {0}\r\n", total);  
        }  
  
        private List<string> SetUpURLList()  
        {  
            List<string> urls = new List<string>   
            {   
                "http://msdn.microsoft.com",  
                "http://msdn.microsoft.com/library/windows/apps/br211380.aspx",  
                "http://msdn.microsoft.com/library/hh290136.aspx",  
                "http://msdn.microsoft.com/library/ee256749.aspx",  
                "http://msdn.microsoft.com/library/hh290138.aspx",  
                "http://msdn.microsoft.com/library/hh290140.aspx",  
                "http://msdn.microsoft.com/library/dd470362.aspx",  
                "http://msdn.microsoft.com/library/aa578028.aspx",  
                "http://msdn.microsoft.com/library/ms404677.aspx",  
                "http://msdn.microsoft.com/library/ff730837.aspx"  
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
            // Strip off the "http://".  
            var displayURL = url.Replace("http://", "");  
            resultsTextBox.Text += string.Format("\n{0,-58} {1,8}", displayURL, bytes);  
  
        }  
    }  
}  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod yöntemini kullanan proje uzantılarını göstermektedir `HttpClient.GetByteArrayAsync` içeriği Web'den yüklemek için.  
  
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
                from url in urlList select ProcessURL(url, client);  
  
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
                string.Format("\r\n\r\nTotal bytes returned:  {0}\r\n", total);  
        }  
  
        private List<string> SetUpURLList()  
        {  
            List<string> urls = new List<string>   
            {   
                "http://msdn.microsoft.com",  
                "http://msdn.microsoft.com/library/hh290136.aspx",  
                "http://msdn.microsoft.com/library/ee256749.aspx",  
                "http://msdn.microsoft.com/library/hh290138.aspx",  
                "http://msdn.microsoft.com/library/hh290140.aspx",  
                "http://msdn.microsoft.com/library/dd470362.aspx",  
                "http://msdn.microsoft.com/library/aa578028.aspx",  
                "http://msdn.microsoft.com/library/ms404677.aspx",  
                "http://msdn.microsoft.com/library/ff730837.aspx"  
            };  
            return urls;  
        }  
  
        // The actions from the foreach loop are moved to this async method.  
        async Task<int> ProcessURL(string url, HttpClient client)  
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
            // Strip off the "http://".  
            var displayURL = url.Replace("http://", "");  
            resultsTextBox.Text += string.Format("\n{0,-58} {1,8}", displayURL, bytes);  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.

- <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>  
- [İzlenecek yol: async kullanarak Web'e erişme ve await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
