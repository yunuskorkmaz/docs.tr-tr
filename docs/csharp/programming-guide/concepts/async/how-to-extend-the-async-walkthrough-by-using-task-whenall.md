---
title: 'Nasıl yapılır: Task.WhenAll (C#) kullanarak tarafından izlenecek zaman uyumsuz genişletme'
ms.date: 07/20/2015
ms.assetid: f6927ef2-dc6c-43f8-bc82-bbeac42de423
ms.openlocfilehash: 4bdd3f32d2fa502de8ada352c522198a89a17f97
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-extend-the-async-walkthrough-by-using-taskwhenall-c"></a>Nasıl yapılır: Task.WhenAll (C#) kullanarak tarafından izlenecek zaman uyumsuz genişletme
Zaman uyumsuz çözümde performansını artırabilir [izlenecek yol: async kullanarak Web'e erişme ve await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md) kullanarak <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> yöntemi. Bu yöntem, zaman uyumsuz olarak görevleri koleksiyonu temsil edilir birden çok zaman uyumsuz işlemleri bekler.  
  
 Web siteleri farklı hızlarda karşıdan kılavuzda fark. Bazen, Web siteleri, kalan tüm indirmeleri gecikmeler çok yavaş biridir. Kılavuzda oluşturacağınız zaman uyumsuz çözümleri çalıştırdığınızda, program kolayca beklemek istemiyorsanız, ancak aynı zamanda tüm indirmeleri başlatmak ve biri, beklemeden devam daha hızlı indirmeler izin vermek için daha iyi bir seçenek olacaktır sonlandırabilirsiniz 's  ertelendi.  
  
 Uyguladığınız `Task.WhenAll` yöntemine görevleri koleksiyonu. Uygulamayı `WhenAll` koleksiyondaki her görev tamamlanana kadar tamamlanmadıysa tek bir görev döndürür. Paralel olarak çalıştırmak için görevler görüntülenir, ancak hiçbir ek iş parçacığı oluşturulur. Herhangi bir sırada görevleri gerçekleştirebilirsiniz.  
  
> [!IMPORTANT]
>  Aşağıdaki yordamlar uzantıları da geliştirilmiş zaman uyumsuz uygulamalara açıklar [izlenecek yol: async kullanarak Web'e erişme ve await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md). Kılavuzu tamamladıktan veya koddan indirme uygulamaları geliştirmek [Geliştirici kod örnekleri](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).  
>   
>  Örneği çalıştırmak için Visual Studio 2012 veya daha sonra bilgisayarınıza yüklenmiş olmalıdır.  
  
### <a name="to-add-taskwhenall-to-your-geturlcontentsasync-solution"></a>Task.WhenAll GetURLContentsAsync çözümünüze eklemek için  
  
1.  Ekleme `ProcessURLAsync` da geliştirilmiş ilk uygulamaya yöntemi [izlenecek yol: async kullanarak Web'e erişme ve await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).  
  
    -   Koddan yüklediyseniz [Geliştirici kod örnekleri](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)AsyncWalkthrough projesini açın ve ardından ekleyin `ProcessURLAsync` MainWindow.xaml.cs dosyasına kayıt yapar.  
  
    -   Kod gözden geçirme tamamlayarak geliştirdiyseniz eklemek `ProcessURLAsync` içeren uygulamaya `GetURLContentsAsync` yöntemi. İlk örnek "Tam kod örnekleri gelen izlenecek yolu" bölümünde bu uygulama için MainWindow.xaml.cs dosyasıdır.  
  
     `ProcessURLAsync` Yöntemi birleştirir gövdesini Eylemler `foreach` içinde döngü `SumPageSizesAsync` özgün izlenecek adımları. Metodu zaman uyumsuz olarak bir bayt dizisi olarak belirtilen bir Web sitesi içeriğini indirir ve ardından görüntüler ve bayt dizisi uzunluğunu döndürür.  
  
    ```csharp  
    private async Task<int> ProcessURLAsync(string url)  
    {  
        var byteArray = await GetURLContentsAsync(url);  
        DisplayResults(url, byteArray);  
        return byteArray.Length;  
    }  
    ```  
  
2.  Out yorum yapmak veya silme `foreach` içinde döngü `SumPageSizesAsync`, aşağıdaki kodda gösterildiği gibi.  
  
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
  
3.  Bir görev koleksiyonunu oluşturun. Aşağıdaki kodu tanımlayan bir [sorgu](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) , tarafından çalıştırıldığında <xref:System.Linq.Enumerable.ToArray%2A> yöntemi, her Web sitesi içeriğini indirme görevleri koleksiyonu oluşturur. Sorgu değerlendirildiğinde görevleri başlatılır.  
  
     Yöntemine aşağıdaki kodu ekleyin `SumPageSizesAsync` bildirimi sonra `urlList`.  
  
    ```csharp  
    // Create a query.   
    IEnumerable<Task<int>> downloadTasksQuery =   
        from url in urlList select ProcessURLAsync(url);  
  
    // Use ToArray to execute the query and start the download tasks.  
    Task<int>[] downloadTasks = downloadTasksQuery.ToArray();  
    ```  
  
4.  Uygulama `Task.WhenAll` görevleri koleksiyonu için `downloadTasks`. `Task.WhenAll` görevlerin koleksiyonundaki tüm görevler tamamlandığında bittikten tek bir görev döndürür.  
  
     Aşağıdaki örnekte, `await` ifade tek tamamlanmasını bekler, görev `WhenAll` döndürür. Dizisi her tamsayı indirilen bir Web sitesi uzunluğu olduğu, için ifadeyi hesaplar. Aşağıdaki kodu ekleyin `SumPageSizesAsync`, yalnızca önceki adımda eklediğiniz koddan sonra.  
  
    ```csharp  
    // Await the completion of all the running tasks.  
    int[] lengths = await Task.WhenAll(downloadTasks);  
  
    //// The previous line is equivalent to the following two statements.  
    //Task<int[]> whenAllTask = Task.WhenAll(downloadTasks);  
    //int[] lengths = await whenAllTask;  
    ```  
  
5.  Son olarak, <xref:System.Linq.Enumerable.Sum%2A> tüm Web siteleri uzunlukları toplamı hesaplamak için yöntem. Aşağıdaki satırı ekleyin `SumPageSizesAsync`.  
  
    ```csharp  
    int total = lengths.Sum();  
    ```  
  
### <a name="to-add-taskwhenall-to-the-httpclientgetbytearrayasync-solution"></a>Task.WhenAll HttpClient.GetByteArrayAsync çözüme eklemek için  
  
1.  Aşağıdaki sürümü eklemek `ProcessURLAsync` da geliştirilmiş ikinci uygulamaya [izlenecek yol: async kullanarak Web'e erişme ve await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).  
  
    -   Koddan yüklediyseniz [Geliştirici kod örnekleri](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)AsyncWalkthrough_HttpClient projesini açın ve ardından ekleyin `ProcessURLAsync` MainWindow.xaml.cs dosyasına kayıt yapar.  
  
    -   Kod gözden geçirme tamamlayarak geliştirdiyseniz eklemek `ProcessURLAsync` kullanan uygulama için `HttpClient.GetByteArrayAsync` yöntemi. Bu uygulama için MainWindow.xaml.cs "Tam kod örnekleri gelen izlenecek yolu" bölümündeki ikinci örneğe dosyasıdır.  
  
     `ProcessURLAsync` Yöntemi birleştirir gövdesini Eylemler `foreach` içinde döngü `SumPageSizesAsync` özgün izlenecek adımları. Metodu zaman uyumsuz olarak bir bayt dizisi olarak belirtilen bir Web sitesi içeriğini indirir ve ardından görüntüler ve bayt dizisi uzunluğunu döndürür.  
  
     Tek farkı `ProcessURLAsync` yöntemidir önceki yordamda kullanımını <xref:System.Net.Http.HttpClient> örneği `client`.  
  
    ```csharp  
    async Task<int> ProcessURL(string url, HttpClient client)  
    {  
        byte[] byteArray = await client.GetByteArrayAsync(url);  
        DisplayResults(url, byteArray);  
        return byteArray.Length;  
    }  
    ```  
  
2.  Out yorum yapmak veya silme `For Each` veya `foreach` içinde döngü `SumPageSizesAsync`, aşağıdaki kodda gösterildiği gibi.  
  
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
  
3.  Tanımlayan bir [sorgu](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) , tarafından çalıştırıldığında <xref:System.Linq.Enumerable.ToArray%2A> yöntemi, her Web sitesi içeriğini indirme görevleri koleksiyonu oluşturur. Sorgu değerlendirildiğinde görevleri başlatılır.  
  
     Yöntemine aşağıdaki kodu ekleyin `SumPageSizesAsync` bildirimi sonra `client` ve `urlList`.  
  
    ```csharp  
    // Create a query.  
    IEnumerable<Task<int>> downloadTasksQuery =   
        from url in urlList select ProcessURL(url, client);  
  
    // Use ToArray to execute the query and start the download tasks.  
    Task<int>[] downloadTasks = downloadTasksQuery.ToArray();  
    ```  
  
4.  Ardından, uygulama `Task.WhenAll` görevleri koleksiyonu için `downloadTasks`. `Task.WhenAll` görevlerin koleksiyonundaki tüm görevler tamamlandığında bittikten tek bir görev döndürür.  
  
     Aşağıdaki örnekte, `await` ifade tek tamamlanmasını bekler, görev `WhenAll` döndürür. Tamamlandığında, `await` dizisi her tamsayı indirilen bir Web sitesi uzunluğu olduğu, için ifadeyi hesaplar. Aşağıdaki kodu ekleyin `SumPageSizesAsync`, yalnızca önceki adımda eklediğiniz koddan sonra.  
  
    ```csharp  
    // Await the completion of all the running tasks.  
    int[] lengths = await Task.WhenAll(downloadTasks);  
  
    //// The previous line is equivalent to the following two statements.  
    //Task<int[]> whenAllTask = Task.WhenAll(downloadTasks);  
    //int[] lengths = await whenAllTask;  
    ```  
  
5.  Son olarak, <xref:System.Linq.Enumerable.Sum%2A> tüm Web siteleri uzunlukları toplamını almak için yöntemi. Aşağıdaki satırı ekleyin `SumPageSizesAsync`.  
  
    ```csharp  
    int total = lengths.Sum();
    ```  
  
### <a name="to-test-the-taskwhenall-solutions"></a>Task.WhenAll çözümleri test etmek için  
  
-   Programı çalıştırmak için F5 tuşuna ya da çözüm için seçin ve ardından **Başlat** düğmesi. Çıkış zaman uyumsuz çözümlerinde çıktısını benzemelidir [izlenecek yol: async kullanarak Web'e erişme ve await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md). Ancak, Web sitelerinin her zaman farklı bir sırada görüntülendiğine dikkat edin.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod kullanan projeye uzantıları gösterir `GetURLContentsAsync` web sunucusundan içerik indirmek için yöntem.  
  
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
 Aşağıdaki kod bir yöntem projesine uzantıları gösterir `HttpClient.GetByteArrayAsync` web sunucusundan içerik indirmek için.  
  
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
 <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>  
 [İzlenecek yol: async kullanarak Web'e erişme ve await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
