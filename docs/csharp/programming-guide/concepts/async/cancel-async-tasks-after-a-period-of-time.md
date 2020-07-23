---
title: Zaman uyumsuz görevleri bir süre sonra iptal etme (C#)
description: Bu örnekteki bir süre içinde tamamlanmamış olan ilişkili görevlerin iptalini zamanlamak Için C# ' de CancellationTokenSource. Süreslafter yöntemini kullanın.
ms.date: 07/20/2015
ms.assetid: 194282c2-399f-46da-a7a6-96674e00b0b3
ms.openlocfilehash: f32af1d893c60ac17648f60fa3aa90adaa0383e8
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925299"
---
# <a name="cancel-async-tasks-after-a-period-of-time-c"></a>Zaman uyumsuz görevleri bir süre sonra iptal etme (C#)

İşlemin bitmesini beklemek istemiyorsanız yöntemini kullanarak bir süre sonra zaman uyumsuz bir işlemi iptal edebilirsiniz <xref:System.Threading.CancellationTokenSource.CancelAfter%2A?displayProperty=nameWithType> . Bu yöntem, ifadesi tarafından belirlenen süre içinde tamamlanmamış olan ilişkili görevlerin iptalini zamanlar `CancelAfter` .

Bu örnek, bir Web sitesi listesini indirmek ve her birinin içerik uzunluğunu göstermek için [zaman uyumsuz bir görevi veya bir görev listesi (C#) Iptal edildiğinde](./cancel-an-async-task-or-a-list-of-tasks.md) geliştirilen koda ekler.

> [!NOTE]
> Örnekleri çalıştırmak için, bilgisayarınızda Visual Studio 2012 veya daha yeni bir sürümü ve .NET Framework 4,5 ya da daha yeni bir sürümü yüklü olmalıdır.

## <a name="download-the-example"></a>Örneği indirin

Tüm Windows Presentation Foundation (WPF) projesini [zaman uyumsuz örnekten indirebilirsiniz: uygulamanızı Ince ayar](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) yapın ve ardından aşağıdaki adımları izleyin.

1. İndirdiğiniz dosyayı sıkıştırmasını açın ve ardından Visual Studio 'Yu başlatın.

2. Menü çubuğunda **Dosya**  >  **Aç**  >  **Proje/çözüm**' ı seçin.

3. **Proje Aç** iletişim kutusunda, açtığınız örnek kodu tutan klasörü açın ve ardından AsyncFineTuningCS için çözüm (. sln) dosyasını açın.

4. **Çözüm Gezgini**, **zaman** hatası ve ardından **Başlangıç projesi olarak ayarla**' yı seçin.

5. Projeyi çalıştırmak için **F5** tuşunu seçin. (Veya, **CTRL** + tuşuna basın Projeyi hata ayıklamadan çalıştırmak için **F5** ).

6. Çıktının tüm Web siteleri, Web sitesi veya bazı Web siteleri için çıktıyı gösterebileceğini doğrulamak için programı birkaç kez çalıştırın.

Projeyi indirmek istemiyorsanız, bu konunun sonundaki MainWindow.xaml.cs dosyasını gözden geçirebilirsiniz.

## <a name="build-the-example"></a>Örneği derleme

Bu konudaki örnek, bir görev listesini iptal etmek için [zaman uyumsuz bir görevi veya bir görev listesini (C#) Iptal etme](./cancel-an-async-task-or-a-list-of-tasks.md) bölümünde geliştirilen projeye ekler. Örnek, aynı kullanıcı arabirimini kullanır, ancak **iptal** düğmesi açıkça kullanılmaz.

Örneği kendiniz oluşturmak için, "örneği Indirme" bölümündeki yönergeleri izleyin, ancak **Başlangıç projesi**olarak iptal eden **ınlıftasks** ' ı seçin. Bu konudaki değişiklikleri bu projeye ekleyin.

Görevler iptal edildi olarak işaretlenmeden önce en uzun süreyi belirtmek için, `CancelAfter` `startButton_Click` Aşağıdaki örnekte gösterildiği gibi öğesine bir çağrı ekleyin. Toplama, yıldız işareti ile işaretlenir.

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

İçin bir başvuru eklemeniz gerektiğini unutmayın <xref:System.Net.Http> .

Projeyi [zaman uyumsuz örnekten indirebilirsiniz: uygulamanızı hassas bir şekilde ayarlama](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).

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

- [Async ve await ile zaman uyumsuz programlama (C#)](./index.md)
- [İzlenecek yol: Async ve await kullanarak Web 'e erişme (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Zaman uyumsuz bir görevi veya görev listesini iptal etme (C#)](./cancel-an-async-task-or-a-list-of-tasks.md)
- [Zaman uyumsuz uygulamanızda ince ayar yapma (C#)](./fine-tuning-your-async-application.md)
- [Zaman uyumsuz örnek: uygulamanıza Ince ayar yapma](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
