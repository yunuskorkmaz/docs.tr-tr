---
title: Bir Süre Sonra Async Görevlerini İptal Etme (C#)
ms.date: 07/20/2015
ms.assetid: 194282c2-399f-46da-a7a6-96674e00b0b3
ms.openlocfilehash: 110c4700d0d2afc87f9144bf258cdd4991f107f4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "70204341"
---
# <a name="cancel-async-tasks-after-a-period-of-time-c"></a>Belirli bir süre sonra async görevlerini iptal etme (C#)

İşlemin tamamlanmasını beklemek istemiyorsanız <xref:System.Threading.CancellationTokenSource.CancelAfter%2A?displayProperty=nameWithType> yöntemi kullanarak bir süre sonra bir eşzamanlı işlemi iptal edebilirsiniz. Bu yöntem, ifade tarafından belirlenen süre içinde tamamlanmamış ilişkili görevlerin iptalini `CancelAfter` planlar.

Bu örnek, web sitelerinin listesini indirmek ve her birinin içeriğinin uzunluğunu görüntülemek için [Bir Async Görevi İptal'de veya Görev Listesi'nde (C#)](./cancel-an-async-task-or-a-list-of-tasks.md) geliştirilen koda eklenir.

> [!NOTE]
> Örnekleri çalıştırmak için Visual Studio 2012 veya daha yeni ve .NET Framework 4.5 veya daha yeni bilgisayarınıza yüklü olması gerekir.

## <a name="download-the-example"></a>Örneği indirin

Windows Presentation Foundation (WPF) projesinin tamamını [Async Sample: Fine Tuning Application'dan](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) indirebilir ve ardından aşağıdaki adımları izleyebilirsiniz.

1. İndirdiğiniz dosyayı sıkıştırın ve Visual Studio'yu başlatın.

2. Menü çubuğunda **Dosya** > **Aç** > **Projesi/Çözümü'nü**seçin.

3. **Projeyi Aç** iletişim kutusunda, sıkıştırdığınız örnek kodu tutan klasörü açın ve ardından AsyncFineTuningCS için çözüm (.sln) dosyasını açın.

4. **Solution**Explorer'da, **CancelAfterTime** projesinin kısayol menüsünü açın ve ardından **StartUp Project olarak ayarla'yı**seçin.

5. Projeyi çalıştırmak için **F5** tuşunu seçin. (Veya, hata ayıklama olmadan projeçalıştırmak için **Ctrl**+**F5** tuşuna basın).

6. Çıktının tüm web siteleri, hiçbir web sitesi veya bazı web siteleri için çıktı gösterebileceğini doğrulamak için programı birkaç kez çalıştırın.

Projeyi indirmek istemiyorsanız, bu konunun sonundaki MainWindow.xaml.cs dosyasını gözden geçirebilirsiniz.

## <a name="build-the-example"></a>Örneği derleme

Bu konuyla ilgili örnek, görev listesini iptal etmek için Bir Async Görevi İptal Etme [veya Görev Listesi (C#)](./cancel-an-async-task-or-a-list-of-tasks.md) olarak geliştirilen projeye eklenir. **İptal** düğmesi açıkça kullanılmasa da, örnek aynı UI'yi kullanır.

Örneği adım adım oluşturmak için, "Örneği İndirme" bölümündeki yönergeleri izleyin, ancak **StartUp Project**olarak **CancelAListOfTasks'i** seçin. Bu konudaki değişiklikleri bu projeye ekleyin.

Görevler iptal edildiolarak işaretlenmeden önce en büyük süreyi `startButton_Click`belirtmek için, `CancelAfter` aşağıdaki örnekte görüldüğü gibi bir çağrı ekleyin. Ek yıldız işaretleri ile işaretlenir.

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

 Çıktının tüm web siteleri, hiçbir web sitesi veya bazı web siteleri için çıktı gösterebileceğini doğrulamak için programı birkaç kez çalıştırın. Aşağıdaki çıktı bir örnektir.

```output
Length of the downloaded string: 35990.

Length of the downloaded string: 407399.

Length of the downloaded string: 226091.

Downloads canceled.
```

## <a name="complete-example"></a>Tam örnek

Aşağıdaki kod, örnek için MainWindow.xaml.cs dosyasının tam metnidir. Yıldız işaretleri, bu örnek için eklenen öğeleri işaretler.

Için bir başvuru eklemeniz <xref:System.Net.Http>gerektiğine dikkat edin.

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

- [Async ve await ile Asynchronous Programlama (C#)](./index.md)
- [Walkthrough: Async kullanarak Web'e erişim ve bekleme (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Bir Async Görevi veya Görev Listesini İptal Etme (C#)](./cancel-an-async-task-or-a-list-of-tasks.md)
- [Async Uygulamanızda İnce Ayar (C#)](./fine-tuning-your-async-application.md)
- [Async Örnek: Uygulamanızı İyi Ayar](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
