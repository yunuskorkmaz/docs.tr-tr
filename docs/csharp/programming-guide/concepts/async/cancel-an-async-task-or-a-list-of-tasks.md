---
title: Zaman uyumsuz bir görevi veya görev listesini iptal etme (C#)
description: Zaman uyumsuz bir uygulamayı tamamlanmadan önce iptal eden bir düğme eklemek için bu örnekleri kullanın. Bu C# uygulaması bir veya daha fazla Web sitesinin içeriğini indirir.
ms.date: 07/20/2015
ms.assetid: eec32dbb-70ea-4c88-bd27-fa2e34546914
ms.openlocfilehash: 21bdbc3bc7c3b752fab160429d71356fb87d9976
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925352"
---
# <a name="cancel-an-async-task-or-a-list-of-tasks-c"></a>Zaman uyumsuz bir görevi veya görev listesini iptal etme (C#)

Bir zaman uyumsuz uygulamayı, bitmesini beklemek istemiyorsanız iptal etmek için kullanabileceğiniz bir düğme ayarlayabilirsiniz. Bu konudaki örnekleri izleyerek, bir Web sitesinin veya Web sitesi listesinin içeriğini yükleyen bir uygulamaya iptal düğmesi ekleyebilirsiniz.

Örnekler, [zaman uyumsuz uygulamanızı (C#)](./fine-tuning-your-async-application.md) açıklayan kullanıcı arabirimini kullanır.

> [!NOTE]
> Örnekleri çalıştırmak için, bilgisayarınızda Visual Studio 2012 veya daha yeni bir sürümü ve .NET Framework 4,5 ya da daha yeni bir sürümü yüklü olmalıdır.

## <a name="cancel-a-task"></a>Bir görevi iptal etme

İlk örnek, **iptal** düğmesini tek bir indirme göreviyle ilişkilendirir. Uygulama içerik indirirken düğmeyi seçerseniz, indirme iptal edilir.

### <a name="download-the-example"></a>Örneği indirin

Tüm Windows Presentation Foundation (WPF) projesini [zaman uyumsuz örnekten indirebilirsiniz: uygulamanızı Ince ayar](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) yapın ve ardından aşağıdaki adımları izleyin.

1. İndirdiğiniz dosyayı sıkıştırmasını açın ve ardından Visual Studio 'Yu başlatın.

2. Menü çubuğunda **Dosya**  >  **Aç**  >  **Proje/çözüm**' ı seçin.

3. **Proje Aç** iletişim kutusunda, açtığınız örnek kodu tutan klasörü açın ve ardından AsyncFineTuningCS için çözüm (. sln) dosyasını açın.

4. **Çözüm Gezgini**' de,,,, Iptal eden **görev** projesi için kısayol menüsünü açın ve ardından **Başlangıç projesi olarak ayarla**' yı seçin.

5. Projeyi çalıştırmak için **F5** tuşuna basın (veya, **Ctrl** + Projeyi hata ayıklamadan çalıştırmak için CTRL**F5** tuşlarına basın).

> [!TIP]
> Projeyi indirmek istemiyorsanız, bu konunun sonundaki MainWindow.xaml.cs dosyalarını gözden geçirebilirsiniz.

### <a name="build-the-example"></a>Örneği derleme
 Aşağıdaki değişiklikler bir Web sitesini indiren uygulamaya bir **iptal** düğmesi ekler. Örneği indirmek veya derlemek istemiyorsanız, bu konunun sonundaki "tüm örnekler" bölümünde son ürünü gözden geçirebilirsiniz. Yıldız işaretleri koddaki değişiklikleri işaretler.

 Örneği kendiniz oluşturmak için, "örneği Indirme" bölümündeki yönergeleri izleyin, ancak **Başlangıç projesi** olarak, **1. aşama yerine** **startercode** ' u seçin.

 Ardından, bu projenin MainWindow.xaml.cs dosyasına aşağıdaki değişiklikleri ekleyin.

1. `CancellationTokenSource` `cts` Kendisine erişen tüm yöntemler için kapsam içinde olan bir değişken bildirin.

    ```csharp
    public partial class MainWindow : Window
    {
        // ***Declare a System.Threading.CancellationTokenSource.
        CancellationTokenSource cts;
    ```

2. **İptal** düğmesi için aşağıdaki olay işleyicisini ekleyin. Olay işleyicisi, <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> Kullanıcı iptali istediğinde bildirimde bulunan yöntemini kullanır `cts` .

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

3. **Başlat** düğmesi için olay işleyicisinde aşağıdaki değişiklikleri yapın `startButton_Click` .

    - , İçin örneğini oluşturun `CancellationTokenSource` `cts` .

        ```csharp
        // ***Instantiate the CancellationTokenSource.
        cts = new CancellationTokenSource();
        ```

    - `AccessTheWebAsync`Belirtilen bir Web sitesinin içeriğini yükleyen çağrısında, <xref:System.Threading.CancellationTokenSource.Token%2A?displayProperty=nameWithType> özelliğini `cts` bağımsız değişken olarak gönderin. `Token`Özelliği, iptal isteniyorsa iletiyi yayar. Kullanıcı indirme işlemini iptal etmeyi seçerse bir ileti görüntüleyen bir catch bloğu ekleyin. Aşağıdaki kod değişiklikleri gösterir.

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

4. İçinde `AccessTheWebAsync` , <xref:System.Net.Http.HttpClient.GetAsync%28System.String%2CSystem.Threading.CancellationToken%29?displayProperty=nameWithType> `GetAsync` <xref:System.Net.Http.HttpClient> bir Web sitesinin içeriğini indirmek için türünde yönteminin aşırı yüklemesini kullanın. `ct` <xref:System.Threading.CancellationToken> `AccessTheWebAsync` İkinci bağımsız değişken olarak, parametresini geçirin. Kullanıcı **iptal** düğmesini seçerse, belirteç iletiyi taşır.

     Aşağıdaki kod, içindeki değişiklikleri gösterir `AccessTheWebAsync` .

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

5. Programı iptal ederseniz, aşağıdaki çıktıyı üretir.

    ```text
    Ready to download.
    Length of the downloaded string: 158125.
    ```

     Program içeriği indirmeyi bitirmeden **iptal** düğmesini seçerseniz, program aşağıdaki çıktıyı üretir.

    ```text
    Ready to download.
    Download canceled.
    ```

## <a name="cancel-a-list-of-tasks"></a>Görev listesini iptal etme

Aynı örneği her görevle ilişkilendirerek, daha fazla görevi iptal etmek için önceki örneği genişletebilirsiniz `CancellationTokenSource` . **İptal** düğmesini seçerseniz, henüz tamamlanmamış tüm görevleri iptal edersiniz.

### <a name="download-the-example"></a>Örneği indirin

Tüm Windows Presentation Foundation (WPF) projesini [zaman uyumsuz örnekten indirebilirsiniz: uygulamanızı Ince ayar](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) yapın ve ardından aşağıdaki adımları izleyin.

1. İndirdiğiniz dosyayı sıkıştırmasını açın ve ardından Visual Studio 'Yu başlatın.

2. Menü çubuğunda **Dosya**  >  **Aç**  >  **Proje/çözüm**' ı seçin.

3. **Proje Aç** iletişim kutusunda, açtığınız örnek kodu tutan klasörü açın ve ardından AsyncFineTuningCS için çözüm (. sln) dosyasını açın.

4. **Çözüm Gezgini**' de,,,,,,,, iptal eden bir **Proje projesi için** kısayol menüsünü açın ve **Başlangıç projesi olarak ayarla**' yı seçin.

5. Projeyi çalıştırmak için **F5** tuşunu seçin.

     **Ctrl** + Projeyi hata ayıklamadan çalıştırmak için CTRL**F5** tuşlarını seçin.

Projeyi indirmek istemiyorsanız, bu konunun sonundaki MainWindow.xaml.cs dosyalarını gözden geçirebilirsiniz.

### <a name="build-the-example"></a>Örneği derleme

Örneği kendiniz genişletmek için, "örneği Indirme" bölümündeki yönergeleri izleyin, ancak **Başlangıç projesi** **olarak iptal** eden ' i seçin. Aşağıdaki değişiklikleri bu projeye ekleyin. Yıldız işaretleri programdaki değişiklikleri işaretler.

1. Web adreslerinin bir listesini oluşturmak için bir yöntem ekleyin.

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

2. İçindeki yöntemi çağırın `AccessTheWebAsync` .

    ```csharp
    // ***Call SetUpURLList to make a list of web addresses.
    List<string> urlList = SetUpURLList();
    ```

3. `AccessTheWebAsync`Listesindeki her bir Web adresini işlemek için aşağıdaki döngüsünü ekleyin.

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

4. `AccessTheWebAsync`, Uzunlukları gösterdiği için yöntemin herhangi bir şey döndürmesi gerekmez. Return ifadesini kaldırın ve yöntemin dönüş türünü yerine olarak değiştirin <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601> .

    ```csharp
    async Task AccessTheWebAsync(CancellationToken ct)
    ```

     Bir `startButton_Click` ifadesi yerine deyimi kullanarak yöntemini çağırın.

    ```csharp
    await AccessTheWebAsync(cts.Token);
    ```

5. Programı iptal ederseniz, aşağıdaki çıktıyı üretir.

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

     İndirmeler tamamlanmadan önce **iptal** düğmesini seçerseniz, çıkış, iptalden önce tamamlanan indirmelerin uzunluklarını içerir.

    ```text
    Length of the downloaded string: 35939.

    Length of the downloaded string: 237682.

    Length of the downloaded string: 128607.

    Downloads canceled.
    ```

## <a name="complete-examples"></a>Tüm örnekler

Aşağıdaki bölümler, önceki örneklerin her birine ilişkin kodu içerir. İçin bir başvuru eklemeniz gerektiğini unutmayın <xref:System.Net.Http> .

Projeleri [zaman uyumsuz örnekten indirebilirsiniz: uygulamanızı hassas bir şekilde ayarlama](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).

### <a name="example---cancel-a-task"></a>Örnek-bir görevi Iptal etme

Aşağıdaki kod, tek bir görevi iptal eden örnek için tüm MainWindow.xaml.cs dosyasıdır.

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

### <a name="example---cancel-a-list-of-tasks"></a>Örnek-görev listesini Iptal etme

Aşağıdaki kod, bir görev listesini iptal eden örnek için tüm MainWindow.xaml.cs dosyasıdır.

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
- [Async ve await ile zaman uyumsuz programlama (C#)](./index.md)
- [Zaman uyumsuz uygulamanızda ince ayar yapma (C#)](./fine-tuning-your-async-application.md)
- [Zaman uyumsuz örnek: uygulamanıza Ince ayar yapma](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
