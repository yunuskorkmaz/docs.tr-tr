---
title: Zaman uyumsuz bir görev veya görevleri (C#) listesini iptal etme
ms.date: 07/20/2015
ms.assetid: eec32dbb-70ea-4c88-bd27-fa2e34546914
ms.openlocfilehash: 01557bf80f40d4197d29ab05cfb4838f5d993a82
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59295750"
---
# <a name="cancel-an-async-task-or-a-list-of-tasks-c"></a>Zaman uyumsuz bir görev veya görevleri (C#) listesini iptal etme

Zaman uyumsuz bir uygulamanın bitmesini beklemek istemiyorsanız, iptal etmek için kullanabileceğiniz bir düğme ayarlayabilirsiniz. Bu konudaki örnekleri izleyerek, Web sitelerinin bir listesiyle ya da bir Web sitesinin içeriklerini indiren bir uygulama için bir iptal düğmesi ekleyebilirsiniz.

Kullanıcı arabirimini örneklerde, [Fine-Tuning Async uygulamanızda (C#)](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md) açıklar.

> [!NOTE]
> Yeni bilgisayarınızda yüklü veya örnekleri çalıştırmak için Visual Studio 2012 veya daha yeni ve .NET Framework 4.5 yüklü olmalıdır.

## <a name="cancel-a-task"></a>Bir görevi iptal etme

İlk örnek ilişkilendirir **iptal** tek bir yükleme göreviyle düğmesi. Uygulama içeriği karşıdan yüklerken düğmeyi seçerseniz, karşıdan yükleme iptal edildi.

### <a name="download-the-example"></a>Örneği indirme

Tüm Windows Presentation Foundation (WPF) projeden indirebileceğiniz [zaman uyumsuz örneği: Uygulamanıza ince](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) ve sonra aşağıdaki adımları izleyin.

1. İndirdiğiniz dosyanın sıkıştırmasını açın ve sonra Visual Studio'yu başlatın.

2. Menü çubuğunda, **dosya** > **açık** > **proje/çözüm**.

3. İçinde **Proje Aç** iletişim kutusunda, açtığınız örnek kodu barındıran klasörü açın ve ardından AsyncFineTuningCS için çözüm (.sln) dosyasını açın.

4. İçinde **Çözüm Gezgini**, kısayol menüsünü açın **CancelATask** proje ve ardından **başlangıç projesi olarak ayarla**.

5. Seçin **F5** projeyi çalıştırmak için anahtar (veya basın **Ctrl**+**F5** projeyi hata ayıklama olmadan çalıştırmak için).

> [!TIP]
> Projeyi indirmek istemiyorsanız, bu konunun sonunda MainWindow.xaml.cs dosyalarını gözden geçirebilirsiniz.

### <a name="build-the-example"></a>Örnek oluşturma
 Aşağıdaki değişiklikleri ekleyin bir **iptal** bir Web sitesi yükleyen bir uygulamaya düğmesi. İndirme veya örnek oluşturmak istemiyorsanız, bu konunun sonundaki "Tam örnekler" bölümünde yer alan son ürünü gözden geçirebilirsiniz. Yıldız işaretleri, koddaki değişiklikleri işaretler.

 Örneği oluşturmak için kendinize, adım adım "Örneği indirme" bölümündeki yönergeleri izleyin, ancak seçin **başlangıç projesi** olarak **başlangıç projesi** yerine **CancelATask** .

 Ardından bu projenin MainWindow.xaml.cs dosyasına aşağıdaki değişiklikleri ekleyin.

1. Bildirme bir `CancellationTokenSource` değişken `cts`, kendisine erişen tüm yöntemler için kapsam dahilinde olan.

    ```csharp
    public partial class MainWindow : Window
    {
        // ***Declare a System.Threading.CancellationTokenSource.
        CancellationTokenSource cts;
    ```

2. İçin aşağıdaki olay işleyicisini ekleyelim **iptal** düğmesi. Olay işleyicisi kullanır <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> yöntemi bildirmek için `cts` kullanıcı iptal isteğinde bulunduğunda.

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

3. Aşağıdaki değişiklikler olay işleyicisi yapma **Başlat** düğme `startButton_Click`.

    -   Örneği `CancellationTokenSource`, `cts`.

        ```csharp
        // ***Instantiate the CancellationTokenSource.
        cts = new CancellationTokenSource();
        ```

    -   Çağrısında `AccessTheWebAsync`, belirtilen bir Web sitesinin içeriklerini karşıdan yükler, gönderme <xref:System.Threading.CancellationTokenSource.Token%2A?displayProperty=nameWithType> özelliği `cts` bağımsız değişken olarak. `Token` Özelliği, iptal istenirse iletiyi yayar. Kullanıcı karşıdan yükleme işlemini iptal etmeyi seçerse ileti görüntüleyen bir catch bloğu ekleyin. Aşağıdaki kod değişiklikleri gösterir.

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

4. İçinde `AccessTheWebAsync`, kullanın <xref:System.Net.Http.HttpClient.GetAsync%28System.String%2CSystem.Threading.CancellationToken%29?displayProperty=nameWithType> aşırı yükünü `GetAsync` yönteminde <xref:System.Net.Http.HttpClient> bir Web sitesinin içeriklerini karşıdan yüklemek için türü. Geçirmek `ct`, <xref:System.Threading.CancellationToken> parametresinin `AccessTheWebAsync`, ikinci bağımsız değişken. Kullanıcı seçerse belirteç iletiyi taşır **iptal** düğmesi.

     Aşağıdaki kod değişiklikleri göstermektedir `AccessTheWebAsync`.

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

     Seçerseniz **iptal** düğmesi önce program içeriği karşıdan, program şu çıktıyı üretir.

    ```text
    Ready to download.
    Download canceled.
    ```

## <a name="cancel-a-list-of-tasks"></a>Görev listesini iptal etme

Aynı ilişkilendirerek birçok görevi iptal etmek için önceki örneği genişletebilirsiniz `CancellationTokenSource` her görev örneği. Seçerseniz **iptal** düğmesi, henüz tamamlanmamış tüm görevleri iptal.

### <a name="download-the-example"></a>Örneği indirme

Tüm Windows Presentation Foundation (WPF) projeden indirebileceğiniz [zaman uyumsuz örneği: Uygulamanıza ince](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) ve sonra aşağıdaki adımları izleyin.

1. İndirdiğiniz dosyanın sıkıştırmasını açın ve sonra Visual Studio'yu başlatın.

2. Menü çubuğunda, **dosya** > **açık** > **proje/çözüm**.

3. İçinde **Proje Aç** iletişim kutusunda, açtığınız örnek kodu barındıran klasörü açın ve ardından AsyncFineTuningCS için çözüm (.sln) dosyasını açın.

4. İçinde **Çözüm Gezgini**, kısayol menüsünü açın **CancelAListOfTasks** proje ve ardından **başlangıç projesi olarak ayarla**.

5. Seçin **F5** projeyi çalıştırmak için anahtar.

     Seçin **Ctrl**+**F5** projeyi hata ayıklama olmadan çalıştırmak için anahtarları.

Projeyi indirmek istemiyorsanız, bu konunun sonunda MainWindow.xaml.cs dosyalarını gözden geçirebilirsiniz.

### <a name="build-the-example"></a>Örnek oluşturma

Örneği genişletmek için kendiniz adım adım "Örneği indirme" bölümündeki yönergeleri izleyin, ancak seçin **CancelATask** olarak **başlangıç projesi**. Aşağıdaki değişiklikleri bu projeye ekleyin. Yıldız işaretleri, programdaki değişiklikleri işaretler.

1. Web adresleri listesi oluşturmak için bir yöntem ekleyin.

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

2. Yöntem çağrısı `AccessTheWebAsync`.

    ```csharp
    // ***Call SetUpURLList to make a list of web addresses.
    List<string> urlList = SetUpURLList();
    ```

3. İçine şu döngüyü ekleyin `AccessTheWebAsync` listesindeki her bir web adresini işlemek için.

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

4. Çünkü `AccessTheWebAsync` görüntüler uzunlukları, yöntemin herhangi bir şey getirmesi gerekmez. Return ifadesini kaldırın ve yöntemin dönüş türünü değiştirmek <xref:System.Threading.Tasks.Task> yerine <xref:System.Threading.Tasks.Task%601>.

    ```csharp
    async Task AccessTheWebAsync(CancellationToken ct)
    ```

     İçinden yöntemi çağırın `startButton_Click` ifade yerine bir deyim kullanarak.

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

     Seçerseniz **iptal** indirmeleri tam düğmesini, çıktı iptalden önce tamamlanan karşıdan yüklemelerin uzunluklarını içerir.

    ```text
    Length of the downloaded string: 35939.

    Length of the downloaded string: 237682.

    Length of the downloaded string: 128607.

    Downloads canceled.
    ```

## <a name="complete-examples"></a>Tam örnekler

Aşağıdaki bölümlerde her önceki örnek kodunu içerir. İçin bir başvuru eklemeniz gerektiğini unutmayın <xref:System.Net.Http>.

İçinden projeleri karşıdan yükleyebileceğiniz [zaman uyumsuz örneği: Uygulamanızı ince ayar](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).

### <a name="example---cancel-a-task"></a>Örnek - bir görev iptal

Aşağıdaki kod, tek bir görevi iptal eden örnek için tam MainWindow.xaml.cs dosyasıdır.

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

### <a name="example---cancel-a-list-of-tasks"></a>Örnek - görev listesini iptal etme

Aşağıdaki kod, bir Görevler listesini iptal eden örnek için tam MainWindow.xaml.cs dosyasıdır.

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
- [Zaman uyumsuz programlama ile async ve await (C#)](../../../../csharp/programming-guide/concepts/async/index.md)
- [(C#) Async uygulamanızda hassas ayar yapma](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md)
- [Zaman uyumsuz örneği: Uygulamanızda hassas ayar yapma](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
