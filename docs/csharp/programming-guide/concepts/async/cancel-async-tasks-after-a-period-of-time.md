---
title: Zaman uyumsuz görevleri bir süre sonra iptal et (C#)
ms.date: 07/20/2015
ms.assetid: 194282c2-399f-46da-a7a6-96674e00b0b3
ms.openlocfilehash: 110c4700d0d2afc87f9144bf258cdd4991f107f4
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70204341"
---
# <a name="cancel-async-tasks-after-a-period-of-time-c"></a>Zaman uyumsuz görevleri bir süre sonra iptal et (C#)

İşlemin bitmesini beklemek istemiyorsanız <xref:System.Threading.CancellationTokenSource.CancelAfter%2A?displayProperty=nameWithType> yöntemini kullanarak bir süre sonra zaman uyumsuz bir işlemi iptal edebilirsiniz. Bu yöntem, `CancelAfter` ifadesi tarafından belirlenen süre içinde tamamlanmamış olan ilişkili görevlerin iptalini zamanlar.

Bu örnek, bir Web sitesi listesini indirmek ve her birinin içerik uzunluğunu göstermek için [zaman uyumsuz bir görevi veyaC#görev listesini () iptal](./cancel-an-async-task-or-a-list-of-tasks.md) etmek üzere geliştirilmiş koda ekler.

> [!NOTE]
> Örnekleri çalıştırmak için, bilgisayarınızda Visual Studio 2012 veya daha yeni bir sürümü ve .NET Framework 4,5 ya da daha yeni bir sürümü yüklü olmalıdır.

## <a name="download-the-example"></a>Örneği indirin

Tüm Windows Presentation Foundation (WPF) projesini [zaman uyumsuz örnekten indirebilirsiniz: Uygulamanızı](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) hassas ayarlamalar yapın ve ardından aşağıdaki adımları izleyin.

1. İndirdiğiniz dosyayı sıkıştırmasını açın ve ardından Visual Studio 'Yu başlatın.

2. Menü çubuğunda **Dosya** > **Aç** > **Proje/çözüm**' ı seçin.

3. **Proje Aç** iletişim kutusunda, açtığınız örnek kodu tutan klasörü açın ve ardından AsyncFineTuningCS için çözüm (. sln) dosyasını açın.

4. **Çözüm Gezgini**, **zaman** hatası ve ardından **Başlangıç projesi olarak ayarla**' yı seçin.

5. Projeyi çalıştırmak için **F5** tuşunu seçin. (Veya, projeyi hata ayıklamadan çalıştırmak için **CTRL**+**F5** tuşuna basın).

6. Çıktının tüm Web siteleri, Web sitesi veya bazı Web siteleri için çıktıyı gösterebileceğini doğrulamak için programı birkaç kez çalıştırın.

Projeyi indirmek istemiyorsanız, bu konunun sonundaki MainWindow.xaml.cs dosyasını gözden geçirebilirsiniz.

## <a name="build-the-example"></a>Örneği oluşturun

Bu konudaki örnek, bir görev listesini iptal etmek için [zaman uyumsuz bir görevi veya görev listesini (C#) iptal](./cancel-an-async-task-or-a-list-of-tasks.md) etmek üzere geliştirilmiş projeye ekler. Örnek, aynı kullanıcı arabirimini kullanır, ancak **iptal** düğmesi açıkça kullanılmaz.

Örneği kendiniz oluşturmak için, "örneği Indirme" bölümündeki yönergeleri izleyin, ancak **Başlangıç projesi**olarak iptal eden ınlıftasks ' ı seçin. Bu konudaki değişiklikleri bu projeye ekleyin.

Görevler iptal edildi olarak işaretlenmeden önce en uzun süreyi belirtmek için, aşağıdaki örnekte gösterildiği gibi `CancelAfter` öğesine `startButton_Click`bir çağrı ekleyin. Toplama, yıldız işareti ile işaretlenir.

```csharp
private async void startButton_Click(object sender, RoutedEventArgs e)
{
    // Instantiate the CancellationTokenSource.
    cts = new CancellationTokenSource();

    resultsTextBox.Clear();

    try
    {
        // ***Set up the CancellationTokenSource to cancel after 2.5 seconds. (You
        // can adjust the time.)
        cts.CancelAfter(2500);

        await AccessTheWebAsync(cts.Token);
        resultsTextBox.Text += "\r\nDownloads succeeded.\r\n";
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
```

 Çıktının tüm Web siteleri, Web sitesi veya bazı Web siteleri için çıktıyı gösterebileceğini doğrulamak için programı birkaç kez çalıştırın. Aşağıdaki çıktı bir örnektir.

```output
Length of the downloaded string: 35990.

Length of the downloaded string: 407399.

Length of the downloaded string: 226091.

Downloads canceled.
```

## <a name="complete-example"></a>Örnek Tamam

Aşağıdaki kod, örnek için MainWindow.xaml.cs dosyasının tüm metinkodudur. Yıldız işaretleri bu örnek için eklenen öğeleri işaretler.

İçin <xref:System.Net.Http>bir başvuru eklemeniz gerektiğini unutmayın.

Projeyi [zaman uyumsuz örnekten indirebilirsiniz: Uygulamanızı](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)hassas bir şekilde ayarlama.

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

namespace CancelAfterTime
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
                // ***Set up the CancellationTokenSource to cancel after 2.5 seconds. (You
                // can adjust the time.)
                cts.CancelAfter(2500);

                await AccessTheWebAsync(cts.Token);
                resultsTextBox.Text += "\r\nDownloads succeeded.\r\n";
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

        // You can still include a Cancel button if you want to.
        private void cancelButton_Click(object sender, RoutedEventArgs e)
        {
            if (cts != null)
            {
                cts.Cancel();
            }
        }

        async Task AccessTheWebAsync(CancellationToken ct)
        {
            // Declare an HttpClient object.
            HttpClient client = new HttpClient();

            // Make a list of web addresses.
            List<string> urlList = SetUpURLList();

            foreach (var url in urlList)
            {
                // GetAsync returns a Task<HttpResponseMessage>.
                // Argument ct carries the message if the Cancel button is chosen.
                // Note that the Cancel button cancels all remaining downloads.
                HttpResponseMessage response = await client.GetAsync(url, ct);

                // Retrieve the website contents from the HttpResponseMessage.
                byte[] urlContents = await response.Content.ReadAsByteArrayAsync();

                resultsTextBox.Text +=
                    $"\r\nLength of the downloaded string: {urlContents.Length}.\r\n";
            }
        }

        private List<string> SetUpURLList()
        {
            List<string> urls = new List<string>
            {
                "https://msdn.microsoft.com",
                "https://msdn.microsoft.com/library/windows/apps/br211380.aspx",
                "https://msdn.microsoft.com/library/hh290136.aspx",
                "https://msdn.microsoft.com/library/ee256749.aspx",
                "https://msdn.microsoft.com/library/ms404677.aspx",
                "https://msdn.microsoft.com/library/ff730837.aspx"
            };
            return urls;
        }
    }

    // Sample Output:

    // Length of the downloaded string: 35990.

    // Length of the downloaded string: 407399.

    // Length of the downloaded string: 226091.

    // Downloads canceled.
}
```

## <a name="see-also"></a>Ayrıca bkz.

- [Async ve await (C#) ile zaman uyumsuz programlama](./index.md)
- [İzlenecek yol: Async ve await (C#) kullanarak Web 'e erişme](./walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Zaman uyumsuz bir görevi veya görev listesini iptal etme (C#)](./cancel-an-async-task-or-a-list-of-tasks.md)
- [Zaman uyumsuz uygulamanızda ince ayar yapma (C#)](./fine-tuning-your-async-application.md)
- [Zaman uyumsuz örnek: Uygulamanızda ince ayar yapma](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
