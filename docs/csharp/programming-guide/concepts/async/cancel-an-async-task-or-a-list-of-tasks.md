---
title: "Zaman uyumsuz görevi veya görev (C#) listesini iptal etme"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: eec32dbb-70ea-4c88-bd27-fa2e34546914
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 78becece40b4b527869c593f8a1fe1eeba1f1f51
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="cancel-an-async-task-or-a-list-of-tasks-c"></a>Zaman uyumsuz görevi veya görev (C#) listesini iptal etme
Zaman uyumsuz uygulama tamamlanmasını beklemek istemiyorsanız, iptal etmek için kullanabileceğiniz bir düğme ayarlayabilirsiniz. Bu konudaki örnekler izleyerek bir Web sitesi içeriğini ya da Web sitelerinin bir listesini indirir bir uygulamaya iptal düğmesi ekleyebilirsiniz.  
  
 Kullanıcı arabirimini örneklerde, [Fine-Tuning zaman uyumsuz uygulamanız (C#)](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md) açıklar.  
  
> [!NOTE]
>  Örnekleri çalıştırmak için Visual Studio 2012 veya daha yeni ve .NET Framework 4.5 olmalıdır veya daha yeni bilgisayarınızda yüklü.  
  
##  <a name="BKMK_CancelaTask"></a>Bir görevi iptal etme  
 İlk örnek ilişkilendirir **iptal** tek indirme görev düğme. Uygulama içeriği indirirken düğmesini seçerseniz, indirme iptal edildi.  
  
### <a name="downloading-the-example"></a>Örnek indirme  
 Tam Windows Presentation Foundation (WPF) projeden indirebilirsiniz [zaman uyumsuz örnek: ince ayar uygulamanız](http://go.microsoft.com/fwlink/?LinkId=255046) ve ardından aşağıdaki adımları izleyin.  
  
1.  İndirdiğiniz dosyanın sıkıştırmasını ve Visual Studio'yu başlatın.  
  
2.  Menü çubuğunda seçin **dosya**, **açık**, **proje/çözüm**.  
  
3.  İçinde **Proje Aç** iletişim kutusunda, sıkıştırması örnek kod tutan klasörü açın ve ardından AsyncFineTuningCS için çözüm (.sln) dosyasını açın.  
  
4.  İçinde **Çözüm Gezgini**, kısayol menüsünü açın **CancelATask** proje ve ardından **başlangıç projesi olarak ayarla**.  
  
5.  Projeyi çalıştırmak için F5 tuşuna seçin.  
  
     Hata ayıklama olmadan projeyi çalıştırmak için Ctrl + F5 anahtarları'i seçin.  
  
 Projenizi indirin istemiyorsanız, bu konunun sonundaki MainWindow.xaml.cs dosyalarını gözden geçirebilirsiniz.  
  
### <a name="building-the-example"></a>Örnek oluşturma  
 Aşağıdaki değişiklikleri eklemek bir **iptal** düğmesi uygulamaya bir Web sitesi yükler. İndirme veya örnek oluşturmak istemiyorsanız, bu konunun sonunda "Tam örnekler" bölümündeki son ürün gözden geçirebilirsiniz. Kod değişiklikleri yıldızlar işaretleyin.  
  
 Örnek oluşturmak için kendiniz, adım adım "örnek indirme" bölümündeki yönergeleri izleyin, ancak seçin **StarterCode** olarak **başlangıç projesi** yerine **CancelATask** .  
  
 Ardından aşağıdaki değişiklikleri proje MainWindow.xaml.cs dosyasına ekleyin.  
  
1.  Bildirme bir `CancellationTokenSource` değişkeni `cts`, kapsamında erişim tüm yöntemleri için olmasıdır.  
  
    ```csharp  
    public partial class MainWindow : Window  
    {  
        // ***Declare a System.Threading.CancellationTokenSource.  
        CancellationTokenSource cts;  
    ```  
  
2.  İçin aşağıdaki olay işleyicisi ekleme **iptal** düğmesi. Olay işleyicisi kullanan <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> bildirmek için yöntemi `cts` kullanıcı iptal isteğinde bulunduğunda.  
  
    ```csharp  
    // ***Add an event handler for the Cancel button.  
    private void cancelButton_Click(object sender, RoutedEventArgs e)  
    {  
        if (cts != null)  
        {  
            cts.Cancel();  
        }  
    }  
    ```  
  
3.  Aşağıdaki değişiklikler olay işleyicisi yapma **Başlat** düğmesini `startButton_Click`.  
  
    -   Örneği `CancellationTokenSource`, `cts`.  
  
        ```csharp  
        // ***Instantiate the CancellationTokenSource.  
        cts = new CancellationTokenSource();  
        ```  
  
    -   Çağrısında `AccessTheWebAsync`, belirtilen bir Web sitesi içeriğini indirir, gönderme <xref:System.Threading.CancellationTokenSource.Token%2A?displayProperty=nameWithType> özelliği `cts` bağımsız değişken olarak. `Token` Özelliği iptal isteniyorsa ileti yayar. Kullanıcı yükleme işlemi iptal etmek seçerse, bir ileti görüntüler bir catch bloğu ekleyin. Aşağıdaki kod değişiklikleri gösterir.  
  
        ```csharp  
        try  
        {  
            // ***Send a token to carry the message if cancellation is requested.  
            int contentLength = await AccessTheWebAsync(cts.Token);  
            resultsTextBox.Text +=  
                String.Format("\r\nLength of the downloaded string: {0}.\r\n", contentLength);  
        }  
        // *** If cancellation is requested, an OperationCanceledException results.  
        catch (OperationCanceledException)  
        {  
            resultsTextBox.Text += "\r\nDownload canceled.\r\n";  
        }  
        catch (Exception)  
        {  
            resultsTextBox.Text += "\r\nDownload failed.\r\n";  
        }  
        ```  
  
4.  İçinde `AccessTheWebAsync`, kullanın <xref:System.Net.Http.HttpClient.GetAsync%28System.String%2CSystem.Threading.CancellationToken%29?displayProperty=nameWithType> , aşırı `GetAsync` yönteminde <xref:System.Net.Http.HttpClient> bir Web sitesi içeriğini indirmek için türü. Geçirmek `ct`, <xref:System.Threading.CancellationToken> parametresinin `AccessTheWebAsync`, ikinci bağımsız değişkeni olarak. Kullanıcı seçerse belirteç ileti taşır **iptal** düğmesi.  
  
     Aşağıdaki kod değişiklikleri gösterir `AccessTheWebAsync`.  
  
    ```csharp  
    // ***Provide a parameter for the CancellationToken.  
    async Task<int> AccessTheWebAsync(CancellationToken ct)  
    {  
        HttpClient client = new HttpClient();  
  
        resultsTextBox.Text +=  
            String.Format("\r\nReady to download.\r\n");  
  
        // You might need to slow things down to have a chance to cancel.  
        await Task.Delay(250);  
  
        // GetAsync returns a Task<HttpResponseMessage>.   
        // ***The ct argument carries the message if the Cancel button is chosen.  
        HttpResponseMessage response = await client.GetAsync("http://msdn.microsoft.com/library/dd470362.aspx", ct);  
  
        // Retrieve the website contents from the HttpResponseMessage.  
        byte[] urlContents = await response.Content.ReadAsByteArrayAsync();  
  
        // The result of the method is the length of the downloaded website.  
        return urlContents.Length;  
    }  
    ```  
  
5.  Program iptal etme, şu çıkışı üretir.  
  
    ```  
    Ready to download.  
    Length of the downloaded string: 158125.  
    ```  
  
     Seçerseniz **iptal** düğmesi program önce tamamlanır içerik indirme, program şu çıkışı üretir.  
  
    ```  
    Ready to download.  
    Download canceled.  
    ```  
  
##  <a name="BKMK_CancelaListofTasks"></a>Görev listesini iptal etme  
 Aynı ilişkilendirerek birçok görevleri iptal etmek için önceki örnekte genişletebilirsiniz `CancellationTokenSource` her görev örneği. Seçerseniz **iptal** düğmesi, henüz tam olmayan tüm görevler iptal.  
  
### <a name="downloading-the-example"></a>Örnek indirme  
 Tam Windows Presentation Foundation (WPF) projeden indirebilirsiniz [zaman uyumsuz örnek: ince ayar uygulamanız](http://go.microsoft.com/fwlink/?LinkId=255046) ve ardından aşağıdaki adımları izleyin.  
  
1.  İndirdiğiniz dosyanın sıkıştırmasını ve Visual Studio'yu başlatın.  
  
2.  Menü çubuğunda seçin **dosya**, **açık**, **proje/çözüm**.  
  
3.  İçinde **Proje Aç** iletişim kutusunda, sıkıştırması örnek kod tutan klasörü açın ve ardından AsyncFineTuningCS için çözüm (.sln) dosyasını açın.  
  
4.  İçinde **Çözüm Gezgini**, kısayol menüsünü açın **CancelAListOfTasks** proje ve ardından **başlangıç projesi olarak ayarla**.  
  
5.  Projeyi çalıştırmak için F5 tuşuna seçin.  
  
     Hata ayıklama olmadan projeyi çalıştırmak için Ctrl + F5 anahtarları'i seçin.  
  
 Projenizi indirin istemiyorsanız, bu konunun sonundaki MainWindow.xaml.cs dosyalarını gözden geçirebilirsiniz.  
  
### <a name="building-the-example"></a>Örnek oluşturma  
 Örneği genişletmek için kendiniz, adım adım "örnek indirme" bölümündeki yönergeleri izleyin, ancak seçin **CancelATask** olarak **başlangıç projesi**. Aşağıdaki değişiklikler bu projeye ekleyin. Yıldız işareti program değişiklikleri işaretleyin.  
  
1.  Web adresleri listesi oluşturmak için bir yöntem ekleyin.  
  
    ```csharp  
    // ***Add a method that creates a list of web addresses.  
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
    ```  
  
2.  Yöntem çağrısı `AccessTheWebAsync`.  
  
    ```csharp  
    // ***Call SetUpURLList to make a list of web addresses.  
    List<string> urlList = SetUpURLList();  
    ```  
  
3.  Aşağıdaki döngüde eklemek `AccessTheWebAsync` listede her web adresini işleyemedi.  
  
    ```csharp  
    // ***Add a loop to process the list of web addresses.  
    foreach (var url in urlList)  
    {  
        // GetAsync returns a Task<HttpResponseMessage>.   
        // Argument ct carries the message if the Cancel button is chosen.   
        // ***Note that the Cancel button can cancel all remaining downloads.  
        HttpResponseMessage response = await client.GetAsync(url, ct);  
  
        // Retrieve the website contents from the HttpResponseMessage.  
        byte[] urlContents = await response.Content.ReadAsByteArrayAsync();  
  
        resultsTextBox.Text +=  
            String.Format("\r\nLength of the downloaded string: {0}.\r\n", urlContents.Length);  
    }  
    ```  
  
4.  Çünkü `AccessTheWebAsync` değil yöntemi uzunlukları gereken her şeyi geri dönmek için görüntüler. Return deyimi kaldırın ve yöntemin dönüş türünü değiştir <xref:System.Threading.Tasks.Task> yerine <xref:System.Threading.Tasks.Task%601>.  
  
    ```csharp  
    async Task AccessTheWebAsync(CancellationToken ct)  
    ```  
  
     Yöntemi çağırın `startButton_Click` yerine bir ifadenin bir deyimi kullanarak.  
  
    ```csharp  
    await AccessTheWebAsync(cts.Token);  
    ```  
  
5.  Program iptal etme, şu çıkışı üretir.  
  
    ```  
    Length of the downloaded string: 35939.  
  
    Length of the downloaded string: 237682.  
  
    Length of the downloaded string: 128607.  
  
    Length of the downloaded string: 158124.  
  
    Length of the downloaded string: 204890.  
  
    Length of the downloaded string: 175488.  
  
    Length of the downloaded string: 145790.  
  
    Downloads complete.  
    ```  
  
     Seçerseniz **iptal** indirmeleri tam önce düğmesi, çıktı içerir önce iptal tamamlandı indirmeleri uzunlukları.  
  
    ```  
    Length of the downloaded string: 35939.  
  
    Length of the downloaded string: 237682.  
  
    Length of the downloaded string: 128607.  
  
    Downloads canceled.  
    ```  
  
##  <a name="BKMK_CompleteExamples"></a>Tam örnekleri  
 Aşağıdaki bölümler her önceki örnekler için kod içerir. İçin bir başvuru eklemeniz gerekir fark <xref:System.Net.Http>.  
  
 Projelerden indirebilirsiniz [zaman uyumsuz örnek: ince ayar uygulamanız](http://go.microsoft.com/fwlink/?LinkId=255046).  
  
### <a name="cancel-a-task-example"></a>Bir görev örneği iptal et  
 Aşağıdaki kod, tek bir görevi iptal eder örneğin tam MainWindow.xaml.cs dosyasıdır.  
  
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
  
// Add the following using directive for System.Threading.  
  
using System.Threading;  
namespace CancelATask  
{  
    public partial class MainWindow : Window  
    {  
        // ***Declare a System.Threading.CancellationTokenSource.  
        CancellationTokenSource cts;  
  
        public MainWindow()  
        {  
            InitializeComponent();  
        }  
  
        private async void startButton_Click(object sender, RoutedEventArgs e)  
        {  
            // ***Instantiate the CancellationTokenSource.  
            cts = new CancellationTokenSource();  
  
            resultsTextBox.Clear();  
  
            try  
            {  
                // ***Send a token to carry the message if cancellation is requested.  
                int contentLength = await AccessTheWebAsync(cts.Token);  
                resultsTextBox.Text +=  
                    String.Format("\r\nLength of the downloaded string: {0}.\r\n", contentLength);  
            }  
            // *** If cancellation is requested, an OperationCanceledException results.  
            catch (OperationCanceledException)  
            {  
                resultsTextBox.Text += "\r\nDownload canceled.\r\n";  
            }  
            catch (Exception)  
            {  
                resultsTextBox.Text += "\r\nDownload failed.\r\n";  
            }  
  
            // ***Set the CancellationTokenSource to null when the download is complete.  
            cts = null;   
        }  
  
        // ***Add an event handler for the Cancel button.  
        private void cancelButton_Click(object sender, RoutedEventArgs e)  
        {  
            if (cts != null)  
            {  
                cts.Cancel();  
            }  
        }  
  
        // ***Provide a parameter for the CancellationToken.  
        async Task<int> AccessTheWebAsync(CancellationToken ct)  
        {  
            HttpClient client = new HttpClient();  
  
            resultsTextBox.Text +=  
                String.Format("\r\nReady to download.\r\n");  
  
            // You might need to slow things down to have a chance to cancel.  
            await Task.Delay(250);  
  
            // GetAsync returns a Task<HttpResponseMessage>.   
            // ***The ct argument carries the message if the Cancel button is chosen.  
            HttpResponseMessage response = await client.GetAsync("http://msdn.microsoft.com/library/dd470362.aspx", ct);  
  
            // Retrieve the website contents from the HttpResponseMessage.  
            byte[] urlContents = await response.Content.ReadAsByteArrayAsync();  
  
            // The result of the method is the length of the downloaded website.  
            return urlContents.Length;  
        }  
    }  
  
    // Output for a successful download:  
  
    // Ready to download.  
  
    // Length of the downloaded string: 158125.  
  
    // Or, if you cancel:  
  
    // Ready to download.  
  
    // Download canceled.  
}  
```  
  
### <a name="cancel-a-list-of-tasks-example"></a>Görevler örneği listesini iptal etme  
 Aşağıdaki kod, görev listesini iptal eder örneğin tam MainWindow.xaml.cs dosyasıdır.  
  
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
  
// Add the following using directive for System.Threading.  
using System.Threading;  
  
namespace CancelAListOfTasks  
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
                // ***Small change in the display lines.  
                resultsTextBox.Text += "\r\nDownloads complete.";  
            }  
            catch (OperationCanceledException)  
            {  
                resultsTextBox.Text += "\r\nDownloads canceled.";  
            }  
            catch (Exception)  
            {  
                resultsTextBox.Text += "\r\nDownloads failed.";  
            }  
  
            // Set the CancellationTokenSource to null when the download is complete.  
            cts = null;  
        }  
  
        // Add an event handler for the Cancel button.  
        private void cancelButton_Click(object sender, RoutedEventArgs e)  
        {  
            if (cts != null)  
            {  
                cts.Cancel();  
            }  
        }  
  
        // Provide a parameter for the CancellationToken.  
        // ***Change the return type to Task because the method has no return statement.  
        async Task AccessTheWebAsync(CancellationToken ct)  
        {  
            // Declare an HttpClient object.  
            HttpClient client = new HttpClient();  
  
            // ***Call SetUpURLList to make a list of web addresses.  
            List<string> urlList = SetUpURLList();  
  
            // ***Add a loop to process the list of web addresses.  
            foreach (var url in urlList)  
            {  
                // GetAsync returns a Task<HttpResponseMessage>.   
                // Argument ct carries the message if the Cancel button is chosen.   
                // ***Note that the Cancel button can cancel all remaining downloads.  
                HttpResponseMessage response = await client.GetAsync(url, ct);  
  
                // Retrieve the website contents from the HttpResponseMessage.  
                byte[] urlContents = await response.Content.ReadAsByteArrayAsync();  
  
                resultsTextBox.Text +=  
                    String.Format("\r\nLength of the downloaded string: {0}.\r\n", urlContents.Length);  
            }  
        }  
  
        // ***Add a method that creates a list of web addresses.  
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
  
    // Output if you do not choose to cancel:  
  
    //Length of the downloaded string: 35939.  
  
    //Length of the downloaded string: 237682.  
  
    //Length of the downloaded string: 128607.  
  
    //Length of the downloaded string: 158124.  
  
    //Length of the downloaded string: 204890.  
  
    //Length of the downloaded string: 175488.  
  
    //Length of the downloaded string: 145790.  
  
    //Downloads complete.  
  
    // Sample output if you choose to cancel:  
  
    //Length of the downloaded string: 35939.  
  
    //Length of the downloaded string: 237682.  
  
    //Length of the downloaded string: 128607.  
  
    //Downloads canceled.  
}  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Threading.CancellationTokenSource>  
 <xref:System.Threading.CancellationToken>  
 [Zaman uyumsuz programlama ile async ve await (C#)](../../../../csharp/programming-guide/concepts/async/index.md)  
 [(C#) Async uygulamanızda hassas ayar yapma](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md)  
 [Zaman uyumsuz örnek: İnce uygulamanızı ayarlama](http://go.microsoft.com/fwlink/?LinkId=255046)
