---
title: Bir Async Görevi veya Görev Listesini İptal Etme (C#)
ms.date: 07/20/2015
ms.assetid: eec32dbb-70ea-4c88-bd27-fa2e34546914
ms.openlocfilehash: 93526f772f79e993767fd8f29087b6caf4e29468
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69595724"
---
# <a name="cancel-an-async-task-or-a-list-of-tasks-c"></a>Eşitleme görevini veya görev listesini iptal etme (C#)

Tamamlanmasını beklemek istemiyorsanız, bir async uygulamasını iptal etmek için kullanabileceğiniz bir düğme ayarlayabilirsiniz. Bu konudaki örnekleri izleyerek, bir web sitesinin veya web sitelerinin listesini indiren bir uygulamaya iptal düğmesi ekleyebilirsiniz.

Örnekler, [Async Uygulamanızı (C#) İnce Ayarlanın](./fine-tuning-your-async-application.md) açıklandığı Kullanıcı Birikintisi'ni kullanır.

> [!NOTE]
> Örnekleri çalıştırmak için Visual Studio 2012 veya daha yeni ve .NET Framework 4.5 veya daha yeni bilgisayarınıza yüklü olması gerekir.

## <a name="cancel-a-task"></a>Görevi iptal etme

İlk örnek, **İptal** düğmesini tek bir indirme göreviyle ilişkilendirer. Uygulama içerik indirirken düğmeyi seçerseniz, indirme iptal edilir.

### <a name="download-the-example"></a>Örneği indirin

Windows Presentation Foundation (WPF) projesinin tamamını [Async Sample: Fine Tuning Application'dan](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) indirebilir ve ardından aşağıdaki adımları izleyebilirsiniz.

1. İndirdiğiniz dosyayı sıkıştırın ve Visual Studio'yu başlatın.

2. Menü çubuğunda **Dosya** > **Aç** > **Projesi/Çözümü'nü**seçin.

3. **Projeyi Aç** iletişim kutusunda, sıkıştırdığınız örnek kodu tutan klasörü açın ve ardından AsyncFineTuningCS için çözüm (.sln) dosyasını açın.

4. **Solution**Explorer'da, **CancelATask** projesinin kısayol menüsünü açın ve ardından **StartUp Project olarak ayarla'yı**seçin.

5. Projeyi çalıştırmak için **F5** tuşunu seçin (veya projeyi hata ayıklamadan çalıştırmak için **Ctrl**+**F5** tuşuna basın).

> [!TIP]
> Projeyi indirmek istemiyorsanız, bu konunun sonundaki MainWindow.xaml.cs dosyalarını gözden geçirebilirsiniz.

### <a name="build-the-example"></a>Örneği derleme
 Aşağıdaki değişiklikler, bir web sitesini indiren bir uygulamaya **İptal** düğmesi ekler. Örneği indirmek veya oluşturmak istemiyorsanız, bu konunun sonundaki "Örnekleri Tamamla" bölümündeki son ürünü inceleyebilirsiniz. Yıldız işaretleri koddaki değişiklikleri işaretler.

 Örneği adım adım oluşturmak için, "Örneği İndirme" bölümündeki yönergeleri izleyin, ancak **CancelATask**yerine **Başlangıç Projesi** olarak **Başlangıç Kodu'nu** seçin.

 Ardından, bu projenin MainWindow.xaml.cs dosyasına aşağıdaki değişiklikleri ekleyin.

1. Bir `CancellationTokenSource` değişken `cts`bildirin, bu ona erişen tüm yöntemler için kapsamdadır.

    ```csharp
    public partial class MainWindow : Window
    {
        // ***Declare a System.Threading.CancellationTokenSource.
        CancellationTokenSource cts;
    ```

2. **İptal** düğmesi için aşağıdaki olay işleyicisini ekleyin. Olay işleyicisi, kullanıcı `cts` iptal istediğinde durumu bildirmek için <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> yöntemi kullanır.

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

3. **Başlat** düğmesi için olay işleyicisinde aşağıdaki `startButton_Click`değişiklikleri yapın.

    - Instantiate `CancellationTokenSource`, `cts`.

        ```csharp
        // ***Instantiate the CancellationTokenSource.
        cts = new CancellationTokenSource();
        ```

    - Belirli bir `AccessTheWebAsync`web sitesinin içeriğini indiren çağrıda, <xref:System.Threading.CancellationTokenSource.Token%2A?displayProperty=nameWithType> bir `cts` argüman olarak özelliğini gönderin. İptal `Token` istenirse özellik iletiyi yayır. Kullanıcı indirme işlemini iptal etmeyi seçerse ileti görüntüleyen bir catch bloğu ekleyin. Aşağıdaki kod değişiklikleri gösterir.

        ```csharp
        try
        {
            // ***Send a token to carry the message if cancellation is requested.
            int contentLength = await AccessTheWebAsync(cts.Token);
            resultsTextBox.Text += $"\r\nLength of the downloaded string: {contentLength}.\r\n";
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

4. `AccessTheWebAsync`In, bir <xref:System.Net.Http.HttpClient.GetAsync%28System.String%2CSystem.Threading.CancellationToken%29?displayProperty=nameWithType> web sitesinin `GetAsync` içeriğini <xref:System.Net.Http.HttpClient> indirmek için türünde yöntemin aşırı yüklenmesini kullanın. Pass `ct`, <xref:System.Threading.CancellationToken> parametresi `AccessTheWebAsync`, ikinci bağımsız değişken olarak. Kullanıcı **İptal** düğmesini seçerse belirteç iletiyi taşır.

     Aşağıdaki kod' daki `AccessTheWebAsync`değişiklikleri gösterir.

    ```csharp
    // ***Provide a parameter for the CancellationToken.
    async Task<int> AccessTheWebAsync(CancellationToken ct)
    {
        HttpClient client = new HttpClient();

        resultsTextBox.Text += "\r\nReady to download.\r\n";

        // You might need to slow things down to have a chance to cancel.
        await Task.Delay(250);

        // GetAsync returns a Task<HttpResponseMessage>.
        // ***The ct argument carries the message if the Cancel button is chosen.
        HttpResponseMessage response = await client.GetAsync("https://msdn.microsoft.com/library/dd470362.aspx", ct);

        // Retrieve the website contents from the HttpResponseMessage.
        byte[] urlContents = await response.Content.ReadAsByteArrayAsync();

        // The result of the method is the length of the downloaded website.
        return urlContents.Length;
    }
    ```

5. Programı iptal etmezseniz, aşağıdaki çıktıyı üretir.

    ```text
    Ready to download.
    Length of the downloaded string: 158125.
    ```

     Program içeriği indirmeyi tamamlamadan önce **İptal** düğmesini seçerseniz, program aşağıdaki çıktıyı üretir.

    ```text
    Ready to download.
    Download canceled.
    ```

## <a name="cancel-a-list-of-tasks"></a>Görev listesini iptal etme

Önceki örneği, her görevle aynı `CancellationTokenSource` örneği ilişkilendirerek birçok görevi iptal etmek için genişletebilirsiniz. **İptal** düğmesini seçerseniz, henüz tamamlanmamış tüm görevleri iptal emiş olursunuz.

### <a name="download-the-example"></a>Örneği indirin

Windows Presentation Foundation (WPF) projesinin tamamını [Async Sample: Fine Tuning Application'dan](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) indirebilir ve ardından aşağıdaki adımları izleyebilirsiniz.

1. İndirdiğiniz dosyayı sıkıştırın ve Visual Studio'yu başlatın.

2. Menü çubuğunda **Dosya** > **Aç** > **Projesi/Çözümü'nü**seçin.

3. **Projeyi Aç** iletişim kutusunda, sıkıştırdığınız örnek kodu tutan klasörü açın ve ardından AsyncFineTuningCS için çözüm (.sln) dosyasını açın.

4. **Solution**Explorer'da, **CancelAListOfTasks** projesinin kısayol menüsünü açın ve ardından **StartUp Project olarak ayarla'yı**seçin.

5. Projeyi çalıştırmak için **F5** tuşunu seçin.

     Projeyi hata ayıklamadan çalıştırmak için **Ctrl**+**F5** tuşlarını seçin.

Projeyi indirmek istemiyorsanız, bu konunun sonundaki MainWindow.xaml.cs dosyalarını gözden geçirebilirsiniz.

### <a name="build-the-example"></a>Örneği derleme

Örneği adım adım genişletmek için, "Örneği İndirme" bölümündeki yönergeleri izleyin, ancak **StartUp Project**olarak **CancelATask'ı** seçin. Bu projeye aşağıdaki değişiklikleri ekleyin. Yıldız işaretleri programdaki değişiklikleri işaretler.

1. Web adreslerinin listesini oluşturmak için bir yöntem ekleyin.

    ```csharp
    // ***Add a method that creates a list of web addresses.
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
    ```

2. Yöntemi ' `AccessTheWebAsync`de çağırın.

    ```csharp
    // ***Call SetUpURLList to make a list of web addresses.
    List<string> urlList = SetUpURLList();
    ```

3. Listedeki her `AccessTheWebAsync` web adresini işlemek için aşağıdaki döngüyü ekleyin.

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
            $"\r\nLength of the downloaded string: {urlContents.Length}.\r\n";
    }
    ```

4. Uzunlukları `AccessTheWebAsync` görüntülediği için, yöntemin hiçbir şeyi döndürmesine gerek yoktur. İade deyimini kaldırın ve yöntemin dönüş <xref:System.Threading.Tasks.Task> türünü <xref:System.Threading.Tasks.Task%601>yerine değiştirin.

    ```csharp
    async Task AccessTheWebAsync(CancellationToken ct)
    ```

     İfade yerine `startButton_Click` deyim kullanarak yöntemi çağırın.

    ```csharp
    await AccessTheWebAsync(cts.Token);
    ```

5. Programı iptal etmezseniz, aşağıdaki çıktıyı üretir.

    ```text
    Length of the downloaded string: 35939.

    Length of the downloaded string: 237682.

    Length of the downloaded string: 128607.

    Length of the downloaded string: 158124.

    Length of the downloaded string: 204890.

    Length of the downloaded string: 175488.

    Length of the downloaded string: 145790.

    Downloads complete.
    ```

     İndirmeler tamamlanmadan önce **İptal** düğmesini seçerseniz, çıktı iptalden önce tamamlanan indirmelerin uzunluklarını içerir.

    ```text
    Length of the downloaded string: 35939.

    Length of the downloaded string: 237682.

    Length of the downloaded string: 128607.

    Downloads canceled.
    ```

## <a name="complete-examples"></a>Tam örnekler

Aşağıdaki bölümler, önceki örneklerin her biri için kodu içerir. Için bir başvuru eklemeniz <xref:System.Net.Http>gerektiğine dikkat edin.

Projeleri [Async Sample: Fine Tuning Your Application'dan](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)indirebilirsiniz.

### <a name="example---cancel-a-task"></a>Örnek - Görevi iptal etme

Aşağıdaki kod, tek bir görevi iptal eden örnek için dosya MainWindow.xaml.csnın tamamıdır.

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
                    $"\r\nLength of the downloaded string: {contentLength}.\r\n";
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

            resultsTextBox.Text += "\r\nReady to download.\r\n";

            // You might need to slow things down to have a chance to cancel.
            await Task.Delay(250);

            // GetAsync returns a Task<HttpResponseMessage>.
            // ***The ct argument carries the message if the Cancel button is chosen.
            HttpResponseMessage response = await client.GetAsync("https://msdn.microsoft.com/library/dd470362.aspx", ct);

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

### <a name="example---cancel-a-list-of-tasks"></a>Örnek - Görev listesini iptal etme

Aşağıdaki kod, görev listesini iptal eden örnek için MainWindow.xaml.cs dosyanın tamamıdır.

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
                    $"\r\nLength of the downloaded string: {urlContents.Length}.\r\n";
            }
        }

        // ***Add a method that creates a list of web addresses.
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

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading.CancellationTokenSource>
- <xref:System.Threading.CancellationToken>
- [Async ve await ile Asynchronous Programlama (C#)](./index.md)
- [Async Uygulamanızda İnce Ayar (C#)](./fine-tuning-your-async-application.md)
- [Async Örnek: Uygulamanızı İyi Ayar](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
