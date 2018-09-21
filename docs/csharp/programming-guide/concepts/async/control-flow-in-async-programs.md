---
title: Denetim akışı zaman uyumsuz programlarda (C#)
ms.date: 07/20/2015
ms.assetid: fc92b08b-fe1d-4d07-84ab-5192fafe06bb
ms.openlocfilehash: 49123dde51acaa82a2d8fa7d27fdf27087675034
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/21/2018
ms.locfileid: "46532223"
---
# <a name="control-flow-in-async-programs-c"></a>Denetim akışı zaman uyumsuz programlarda (C#)

Yazma ve zaman uyumsuz programları daha kolay kullanarak koruduğunuz `async` ve `await` anahtar sözcükleri. Ancak, nasıl programınızı anlamazsanız sonuçlar sizi şaşırtabilir. Bu konu, her zaman denetimi başka bir ve hangi bilgileri bir yöntemden diğerine taşır. göstermek için basit bir zamanuyumsuz program aracılığıyla denetim akışını aktarılır izler.

Genel olarak, zaman uyumsuz kodun yer aldığı yöntemleri işaretleyin [async (C#)](../../../../csharp/language-reference/keywords/async.md) değiştiricisi. Zaman uyumsuz değiştiriciyle işaretlenmiş bir yöntemde, kullandığınız bir [await (C#)](../../../../csharp/language-reference/keywords/await.md) burada yöntemin tamamlanması bir çağrılan zaman uyumsuz işlem için duraklatacağını belirtmek için işleci. Daha fazla bilgi için [Asynchronous Programming with async ve await (C#)](../../../../csharp/programming-guide/concepts/async/index.md).

Aşağıdaki örnek, bir dize olarak belirtilen bir Web sitesinin içeriklerini karşıdan yüklemek ve dizenin uzunluğu görüntülemek için zaman uyumsuz yöntemler kullanır. Örneğin, aşağıdaki iki yöntemi içerir.

-   `startButton_Click`, hangi çağrıları `AccessTheWebAsync` ve sonucu görüntüler.

-   `AccessTheWebAsync`, bir dize olarak bir Web sitesinin içeriklerini karşıdan yükler ve dizenin uzunluğunu döndürür. `AccessTheWebAsync` zaman uyumsuz kullanan <xref:System.Net.Http.HttpClient> yöntemi <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>içeriğini indirmek için.

Numaralı ekran satırları, programın nasıl çalıştığını anlamanıza yardımcı olmak ve işaretlenmiş her noktada ne olacağını açıklamak için program boyunca stratejik noktalarda görüntülenir. Görüntü satırları "Bir"ile "altı." olarak etiketlenmiştir Etiketler, programın bu kod satırlarını ulaştığında sırayı temsil eder.

Aşağıdaki kod, programın özetini gösterir.

```csharp
public partial class MainWindow : Window
{
    // . . .
    private async void startButton_Click(object sender, RoutedEventArgs e)
    {
        // ONE
        Task<int> getLengthTask = AccessTheWebAsync();

        // FOUR
        int contentLength = await getLengthTask;

        // SIX
        resultsTextBox.Text +=
            String.Format("\r\nLength of the downloaded string: {0}.\r\n", contentLength);
    }

    async Task<int> AccessTheWebAsync()
    {
        // TWO
        HttpClient client = new HttpClient();
        Task<string> getStringTask =
            client.GetStringAsync("http://msdn.microsoft.com");

        // THREE
        string urlContents = await getStringTask;

        // FIVE
        return urlContents.Length;
    }
}
```

"ONE"ila "SIX" arasındaki etiketli konumların her biri, programın geçerli durumuyla ilgili bilgileri görüntüler. Aşağıdaki çıkış üretilir:

```text
ONE:   Entering startButton_Click.
           Calling AccessTheWebAsync.

TWO:   Entering AccessTheWebAsync.
           Calling HttpClient.GetStringAsync.

THREE: Back in AccessTheWebAsync.
           Task getStringTask is started.
           About to await getStringTask & return a Task<int> to startButton_Click.

FOUR:  Back in startButton_Click.
           Task getLengthTask is started.
           About to await getLengthTask -- no caller to return to.

FIVE:  Back in AccessTheWebAsync.
           Task getStringTask is complete.
           Processing the return statement.
           Exiting from AccessTheWebAsync.

SIX:   Back in startButton_Click.
           Task getLengthTask is finished.
           Result from AccessTheWebAsync is stored in contentLength.
           About to display contentLength and exit.

Length of the downloaded string: 33946.
```

## <a name="set-up-the-program"></a>Program ayarlama

Bu konuda kullanan kodu MSDN sitesinden yükleyebilir veya size kendiniz oluşturabilirsiniz.

> [!NOTE]
> Yeni bilgisayarınızda yüklü veya örneği çalıştırmak için Visual Studio 2012 veya daha yeni ve .NET Framework 4.5 yüklü olmalıdır.

### <a name="download-the-program"></a>Programı indir

Bu konu için uygulamayı indirebilirsiniz [zaman uyumsuz örneği: Zamanuyumsuz programlarda akış denetimi](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0). Aşağıdaki adımlar, açın ve programı çalıştırın.

1.  İndirilen dosyanın sıkıştırmasını açın ve sonra Visual Studio'yu başlatın.

2.  Menü çubuğunda, **dosya** > **açık** > **proje/çözüm**.

3.  Çözüm (.sln) dosyasını aç sıkıştırması açılmış örnek kodun bulunduğu klasöre gidin ve ardından **F5** anahtarı oluşturun ve projeyi çalıştırın.

### <a name="create-the-program-yourself"></a>Programı kendiniz oluşturun

Aşağıdaki Windows Presentation Foundation (WPF) projesi Bu konu için kod örneği içerir.

Projeyi çalıştırmak için aşağıdaki adımları gerçekleştirin:

1.  Visual Studio'yu başlatın.

2.  Menü çubuğunda, **dosya** > **yeni** > **proje**.

     **Yeni proje** iletişim kutusu açılır.

3.  Seçin **yüklü** > **Visual C#** > **Windows Masaüstü** kategori seçip **WPF uygulaması** Proje şablonları listesinden.

4.  Girin `AsyncTracer` projesinin adı olarak seçip **Tamam** düğmesi.

     Yeni Proje görünür **Çözüm Gezgini**.

5.  Visual Studio Kod Düzenleyicisi'nde seçin **MainWindow.xaml** sekmesi.

     Sekme görünür değilse, nde MainWindow.xaml için kısayol menüsünü açın **Çözüm Gezgini**ve ardından **kodu görüntüle**.

6.  İçinde **XAML** MainWindow.xaml görüntülemek için kodu aşağıdaki kodla değiştirin.

    ```csharp
    <Window
            xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
            xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
            xmlns:d="http://schemas.microsoft.com/expression/blend/2008" xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006" mc:Ignorable="d" x:Class="AsyncTracer.MainWindow"
            Title="Control Flow Trace" Height="350" Width="592">
        <Grid>
            <Button x:Name="startButton" Content="Start
    " HorizontalAlignment="Left" Margin="250,10,0,0" VerticalAlignment="Top" Width="75" Height="24"  Click="startButton_Click" d:LayoutOverrides="GridBox"/>
            <TextBox x:Name="resultsTextBox" HorizontalAlignment="Left" TextWrapping="Wrap" VerticalAlignment="Bottom" Width="576" Height="265" FontFamily="Lucida Console" FontSize="10" VerticalScrollBarVisibility="Visible" Grid.ColumnSpan="3"/>
        </Grid>
    </Window>
    ```

     Bir metin kutusu ve bir düğme içeren basit bir pencere **tasarım** MainWindow.xaml görünümü.

7.  İçin bir başvuru eklemeniz <xref:System.Net.Http>.

8.  İçinde **Çözüm Gezgini**için MainWindow.xaml.cs kısayol menüsünü açın ve ardından **kodu görüntüle**.

9. MainWindow.xaml.cs kodu aşağıdaki kodla değiştirin.

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

    // Add a using directive and a reference for System.Net.Http;
    using System.Net.Http;

    namespace AsyncTracer
    {
        public partial class MainWindow : Window
        {
            public MainWindow()
            {
                InitializeComponent();
            }

            private async void startButton_Click(object sender, RoutedEventArgs e)
            {
                // The display lines in the example lead you through the control shifts.
                resultsTextBox.Text += "ONE:   Entering startButton_Click.\r\n" +
                    "           Calling AccessTheWebAsync.\r\n";

                Task<int> getLengthTask = AccessTheWebAsync();

                resultsTextBox.Text += "\r\nFOUR:  Back in startButton_Click.\r\n" +
                    "           Task getLengthTask is started.\r\n" +
                    "           About to await getLengthTask -- no caller to return to.\r\n";

                int contentLength = await getLengthTask;

                resultsTextBox.Text += "\r\nSIX:   Back in startButton_Click.\r\n" +
                    "           Task getLengthTask is finished.\r\n" +
                    "           Result from AccessTheWebAsync is stored in contentLength.\r\n" +
                    "           About to display contentLength and exit.\r\n";

                resultsTextBox.Text +=
                    String.Format("\r\nLength of the downloaded string: {0}.\r\n", contentLength);
            }

            async Task<int> AccessTheWebAsync()
            {
                resultsTextBox.Text += "\r\nTWO:   Entering AccessTheWebAsync.";

                // Declare an HttpClient object.
                HttpClient client = new HttpClient();

                resultsTextBox.Text += "\r\n           Calling HttpClient.GetStringAsync.\r\n";

                // GetStringAsync returns a Task<string>.
                Task<string> getStringTask = client.GetStringAsync("http://msdn.microsoft.com");

                resultsTextBox.Text += "\r\nTHREE: Back in AccessTheWebAsync.\r\n" +
                    "           Task getStringTask is started.";

                // AccessTheWebAsync can continue to work until getStringTask is awaited.

                resultsTextBox.Text +=
                    "\r\n           About to await getStringTask and return a Task<int> to startButton_Click.\r\n";

                // Retrieve the website contents when task is complete.
                string urlContents = await getStringTask;

                resultsTextBox.Text += "\r\nFIVE:  Back in AccessTheWebAsync." +
                    "\r\n           Task getStringTask is complete." +
                    "\r\n           Processing the return statement." +
                    "\r\n           Exiting from AccessTheWebAsync.\r\n";

                return urlContents.Length;
            }
        }
    }
    ```

10. Seçin **F5** programı çalıştırmak için anahtar ve ardından **Başlat** düğmesi.

    Aşağıdaki çıktı görünür:

    ```text
    ONE:   Entering startButton_Click.
               Calling AccessTheWebAsync.

    TWO:   Entering AccessTheWebAsync.
               Calling HttpClient.GetStringAsync.

    THREE: Back in AccessTheWebAsync.
               Task getStringTask is started.
               About to await getStringTask & return a Task<int> to startButton_Click.

    FOUR:  Back in startButton_Click.
               Task getLengthTask is started.
               About to await getLengthTask -- no caller to return to.

    FIVE:  Back in AccessTheWebAsync.
               Task getStringTask is complete.
               Processing the return statement.
               Exiting from AccessTheWebAsync.

    SIX:   Back in startButton_Click.
               Task getLengthTask is finished.
               Result from AccessTheWebAsync is stored in contentLength.
               About to display contentLength and exit.

    Length of the downloaded string: 33946.
    ```

## <a name="trace-the-program"></a>Programı İzle

### <a name="steps-one-and-two"></a>BİR ve ikinci adımlar

İlk iki görüntü satırı yolu olarak izleme `startButton_Click` çağrıları `AccessTheWebAsync`, ve `AccessTheWebAsync` zaman uyumsuz çağrı <xref:System.Net.Http.HttpClient> yöntemi <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>. Aşağıdaki resimde yöntemden yönteme çağrılar özetlenmektedir.

![BİR ve ikinci adımlar](../../../../csharp/programming-guide/concepts/async/media/asynctrace-onetwo.png "AsyncTrace ONETWO")

Dönüş türü, her ikisi de `AccessTheWebAsync` ve `client.GetStringAsync` olduğu <xref:System.Threading.Tasks.Task%601>. İçin `AccessTheWebAsync`, TResult bir tamsayı olduğu. İçin `GetStringAsync`, TResult olan bir dize. Zaman uyumsuz yöntem dönüş türleri hakkında daha fazla bilgi için bkz: [Async Return Types (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md).

Bir görev döndüren zaman uyumsuz yöntem, Denetim arayana geri geçtiğinde bir görev örneği döndürür. Denetim, uyumsuz bir yöntemden arayanına döner ya da bir `await` çağrılan yöntem veya çağrılan yöntem sona erdiğinde işleciyle karşılaşıldığında. "Üç"ile "altı" etiketli görüntü satırları işlemin bu kısmında izleme.

### <a name="step-three"></a>Adım üç

İçinde `AccessTheWebAsync`, zaman uyumsuz yöntemin <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> hedef Web sayfasının içeriğini indirmek için çağrılır. Denetim döndüğü `client.GetStringAsync` için `AccessTheWebAsync` olduğunda `client.GetStringAsync` döndürür.

 `client.GetStringAsync` Yöntemi bir görev için atanan bir dize döndürür `getStringTask` değişkeninde `AccessTheWebAsync`. Örnek programdaki aşağıdaki satır çağrısını gösterir `client.GetStringAsync` atama.

```csharp
Task<string> getStringTask = client.GetStringAsync("http://msdn.microsoft.com");
```

 Görevini, hedefi olarak düşünebilirsiniz `client.GetStringAsync` sonuçta gerçek bir dize oluşturmak için. Bu arada, varsa `AccessTheWebAsync` dizeden bağımlı olmayan yapılacak çalışmaya sahipse `client.GetStringAsync`, iş devam edebilirsiniz ancak `client.GetStringAsync` bekler. Örnekte, "Üç" etiketli, aşağıdaki çıktı satırları bağımsız iş yapma fırsatını temsil eder.

```
THREE: Back in AccessTheWebAsync.
           Task getStringTask is started.
           About to await getStringTask & return a Task<int> to startButton_Click.
```

 Aşağıdaki deyim ilerlemesini askıya alır `AccessTheWebAsync` olduğunda `getStringTask` beklenir.

```csharp
string urlContents = await getStringTask;
```

 Aşağıdaki görüntüde, denetim akışı gösterilmektedir. `client.GetStringAsync` atamaya `getStringTask` ve oluşturulmasını `getStringTask` bir await işlecinin uygulamasına.

 ![ÜÇ adım](../../../../csharp/programming-guide/concepts/async/media/asynctrace-three.png "AsyncTrace üç")

 Await ifadesi askıya `AccessTheWebAsync` kadar `client.GetStringAsync` döndürür. Bu arada, Denetim çağırana döner `AccessTheWebAsync`, `startButton_Click`.

> [!NOTE]
> Genellikle, bir zaman uyumsuz yöntem çağrısı hemen bekler. Örneğin, aşağıdaki atama oluşturan ve sonra bekleyen önceki kodun yerini alabilir `getStringTask`: `string urlContents = await client.GetStringAsync("http://msdn.microsoft.com");`
>
> Bu konuda, await işleci, program aracılığıyla denetim akışını işaretleyen çıkış satırlarını yerleştirmek için daha sonra uygulanır.

### <a name="step-four"></a>Dördüncü adım

Bildirilen dönüş türü `AccessTheWebAsync` olduğu `Task<int>`. Bu nedenle, `AccessTheWebAsync` olan askıya alındı, bir tamsayı görevi döndürür `startButton_Click`. Döndürülen görevin olmadığını anlamanız gereken `getStringTask`. Döndürülen görevin askıya alınmış yönteminde yapılması kalan temsil eden tamsayı, yeni bir görevdir `AccessTheWebAsync`. Görev bir vaadidir `AccessTheWebAsync` görev tamamlandığında bir tamsayı üretmek için.

Bu görev için aşağıdaki deyimi atar `getLengthTask` değişkeni.

```csharp
Task<int> getLengthTask = AccessTheWebAsync();
```

 Olarak `AccessTheWebAsync`, `startButton_Click` zaman uyumsuz görev sonuçlarına bağlı olmayan çalışmalar ile devam edebilir (`getLengthTask`) kadar görev beklenir. Aşağıdaki çıktı satırları bu işi temsil eder.

```
FOUR:  Back in startButton_Click.
           Task getLengthTask is started.
           About to await getLengthTask -- no caller to return to.
```

 İlerlemenizi `startButton_Click` zaman askıya `getLengthTask` beklenir. Aşağıdaki atama deyimi askıya `startButton_Click` kadar `AccessTheWebAsync` tamamlandı.

```csharp
int contentLength = await getLengthTask;
```

 Aşağıdaki çizimde, oklar seçeneğindeki await ifadesine içinde denetim akışını gösterir. `AccessTheWebAsync` bir değer atamaya `getLengthTask`, normal işlem tarafından izlenen `startButton_Click` kadar `getLengthTask` beklenir.

 ![Dördüncü adım](../../../../csharp/programming-guide/concepts/async/media/asynctrace-four.png "AsyncTrace dört")

### <a name="step-five"></a>Beşinci adım

Zaman `client.GetStringAsync` işleme işleminin tamamlandığından emin sinyalleri `AccessTheWebAsync` askıda durumundan çıkarılır ve bekleme ifadesinin ötesine devam edebilir. Aşağıdaki çıktı satırları işlemin sürdürülmesini temsil eder.

```
FIVE:  Back in AccessTheWebAsync.
           Task getStringTask is complete.
           Processing the return statement.
           Exiting from AccessTheWebAsync.
```

 Return ifadesinin işleneni `urlContents.Length`, görevde depolanır, `AccessTheWebAsync` döndürür. Await ifadesi bu değeri alır. `getLengthTask` içinde `startButton_Click`.

 Aşağıdaki görüntüde, sonraki denetim aktarımı gösterilmektedir `client.GetStringAsync` (ve `getStringTask`) getirildiğinden.

 ![BEŞ adım](../../../../csharp/programming-guide/concepts/async/media/asynctrace-five.png "AsyncTrace beş")

 `AccessTheWebAsync` çalıştırır ve denetim döner `startButton_Click`, tamamlanması bekleniyor.

### <a name="step-six"></a>Altıncı adım

Zaman `AccessTheWebAsync` tam işleme sinyalleri içindeki bekleme ifadesinin ötesine devam edebilir `startButton_Async`. Aslında, programın başka bir şey yapmak için vardır.

Aşağıdaki çıktı satırları içinde işlemin sürdürülmesini temsil etmektedir `startButton_Async`:

```
SIX:   Back in startButton_Click.
           Task getLengthTask is finished.
           Result from AccessTheWebAsync is stored in contentLength.
           About to display contentLength and exit.
```

 Await ifadesi alır `getLengthTask` içindeki return deyiminin işleneni olan bir tamsayı değer `AccessTheWebAsync`. Aşağıdaki deyim, bu değeri atar `contentLength` değişkeni.

```csharp
int contentLength = await getLengthTask;
```

 Aşağıdaki görüntüde kadar denetimin dönüşü gösterilmektedir `AccessTheWebAsync` için `startButton_Click`.

 ![ALTI adım](../../../../csharp/programming-guide/concepts/async/media/asynctrace-six.png "AsyncTrace altı")

## <a name="see-also"></a>Ayrıca bkz.

- [Zaman uyumsuz programlama ile async ve await (C#)](../../../../csharp/programming-guide/concepts/async/index.md)
- [Zaman uyumsuz dönüş türleri (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md)
- [İzlenecek yol: async kullanarak Web'e erişme ve await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Zaman uyumsuz örneği: Zaman uyumsuz programlarda (C# ve Visual Basic) denetim akışı](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0)
