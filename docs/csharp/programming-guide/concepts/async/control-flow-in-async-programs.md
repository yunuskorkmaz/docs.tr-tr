---
title: Zaman uyumsuz programlarda denetim akışı (C#)
ms.date: 07/20/2015
ms.assetid: fc92b08b-fe1d-4d07-84ab-5192fafe06bb
ms.openlocfilehash: 99f80a86f14179c5f270064a9f96e35f8611ef13
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70204448"
---
# <a name="control-flow-in-async-programs-c"></a>Zaman uyumsuz programlarda denetim akışı (C#)

`async` Ve`await` anahtar sözcüklerini kullanarak zaman uyumsuz programları daha kolay bir şekilde yazabilir ve koruyabilirsiniz. Ancak, programınızın nasıl çalıştığını anlamıyorsanız sonuçlar sizi şaşırtabilir. Bu konu, denetim bir yöntemden diğerine ne zaman taşındığını ve her seferinde hangi bilgilerin aktarılacağını göstermek için basit bir zaman uyumsuz program aracılığıyla denetim akışını izler.

Genel olarak, [Async (C#)](../../../language-reference/keywords/async.md) değiştiricisiyle zaman uyumsuz kod içeren yöntemleri işaretlersiniz. Zaman uyumsuz değiştirici ile işaretlenmiş bir yöntemde, yöntemin, çağrılan zaman uyumsuz işlemin tamamlanmasını beklemek için bekleyeceği yeri belirtmek için [await (C#)](../../../language-reference/operators/await.md) işlecini kullanabilirsiniz. Daha fazla bilgi için bkz. [Async ve await (C#) Ile zaman uyumsuz programlama](./index.md).

Aşağıdaki örnek, belirtilen bir Web sitesinin içeriğini bir dize olarak indirmek ve dizenin uzunluğunu göstermek için zaman uyumsuz yöntemler kullanır. Örnek aşağıdaki iki yöntemi içerir.

- `startButton_Click`, sonucu çağırır `AccessTheWebAsync` ve görüntüler.

- `AccessTheWebAsync`, bir Web sitesinin içeriğini bir dize olarak indirir ve dizenin uzunluğunu döndürür. `AccessTheWebAsync`, içeriğini indirmek <xref:System.Net.Http.HttpClient> için zaman uyumsuz bir yöntem kullanır. <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>

Numaralandırılmış görüntüleme satırları programın nasıl çalıştığını anlamanıza yardımcı olmak ve işaretlenen her bir noktada ne olduğunu açıklamak için programın tamamında stratejik noktalarda görünür. Görüntüleme satırları "BIR"-"altı" olarak etiketlenir. Etiketler, programın bu kod satırlarına ulaştığı sırayı temsil eder.

Aşağıdaki kod programın bir ana hattını gösterir.

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
            $"\r\nLength of the downloaded string: {contentLength}.\r\n";
    }

    async Task<int> AccessTheWebAsync()
    {
        // TWO
        HttpClient client = new HttpClient();
        Task<string> getStringTask =
            client.GetStringAsync("https://msdn.microsoft.com");

        // THREE
        string urlContents = await getStringTask;

        // FIVE
        return urlContents.Length;
    }
}
```

Etiketlenmiş konumların her biri, "BIR"-"ALTıDA", programın geçerli durumuyla ilgili bilgileri görüntüler. Aşağıdaki çıktı üretilir:

```output
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

## <a name="set-up-the-program"></a>Programı ayarlama

Bu konunun kullandığı kodu MSDN 'den indirebilirsiniz veya kendiniz oluşturabilirsiniz.

> [!NOTE]
> Örneği çalıştırmak için, bilgisayarınızda Visual Studio 2012 veya daha yeni bir sürümü ve .NET Framework 4,5 ya da daha yeni bir sürümü yüklü olmalıdır.

### <a name="download-the-program"></a>Programı indir

Bu konu [için uygulamayı zaman uyumsuz örnekten indirebilirsiniz: Zaman uyumsuz programlarda](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0)denetim akışı. Aşağıdaki adımlar programı açın ve çalıştırın.

1. İndirilen dosyayı sıkıştırmasını açın ve ardından Visual Studio 'Yu başlatın.

2. Menü çubuğunda **Dosya** > **Aç** > **Proje/çözüm**' ı seçin.

3. Sıkıştırılmış örnek kodu tutan klasöre gidin, çözüm (. sln) dosyasını açın ve ardından projeyi derlemek ve çalıştırmak için **F5** tuşunu seçin.

### <a name="create-the-program-yourself"></a>Programı kendiniz oluşturun

Aşağıdaki Windows Presentation Foundation (WPF) projesi bu konunun kod örneğini içerir.

Projeyi çalıştırmak için aşağıdaki adımları gerçekleştirin:

1. Visual Studio’yu çalıştırın.

2. Menü çubuğunda, **dosya** > **yeni** > **proje**.

     **Yeni proje** iletişim kutusu açılır.

3. Yüklü > olan**Visual C#**  Windows MasaüstükategorisiniseçinveardındanprojeşablonlarılistesindenWPFuygulaması'nıseçin. > 

4. Projenin `AsyncTracer` adı olarak girin ve **Tamam** düğmesini seçin.

     Yeni proje **Çözüm Gezgini**görüntülenir.

5. Visual Studio Code düzenleyicisinde **MainWindow. xaml** sekmesini seçin.

     Sekme görünür değilse, **Çözüm Gezgini**' de MainWindow. xaml için kısayol menüsünü açın ve **kodu görüntüle**' yi seçin.

6. MainWindow. xaml ' nin **xaml** görünümünde, kodu aşağıdaki kodla değiştirin.

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

     Bir metin kutusu ve bir düğme içeren basit bir pencere, MainWindow. xaml **Tasarım** görünümünde görünür.

7. İçin <xref:System.Net.Http>bir başvuru ekleyin.

8. **Çözüm Gezgini**' de, MainWindow.xaml.cs için kısayol menüsünü açın ve **kodu görüntüle**' yi seçin.

9. MainWindow.xaml.cs ' de, kodu aşağıdaki kodla değiştirin.

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
                    $"\r\nLength of the downloaded string: {contentLength}.\r\n";
            }

            async Task<int> AccessTheWebAsync()
            {
                resultsTextBox.Text += "\r\nTWO:   Entering AccessTheWebAsync.";

                // Declare an HttpClient object.
                HttpClient client = new HttpClient();

                resultsTextBox.Text += "\r\n           Calling HttpClient.GetStringAsync.\r\n";

                // GetStringAsync returns a Task<string>.
                Task<string> getStringTask = client.GetStringAsync("https://msdn.microsoft.com");

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

10. Programı çalıştırmak için **F5** tuşunu seçin ve sonra **Başlat** düğmesini seçin.

    Aşağıdaki çıktı görüntülenir:

    ```output
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

## <a name="trace-the-program"></a>Programı izleme

### <a name="steps-one-and-two"></a>Adım BIR ve ıkı

İlk iki görüntüleme satırı `startButton_Click` yolu çağrı `AccessTheWebAsync`olarak izler ve `AccessTheWebAsync` zaman uyumsuz <xref:System.Net.Http.HttpClient> yöntemi <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>çağırır. Aşağıdaki görüntüde yönteminden yöntemine yapılan çağrılar özetlenmektedir.

![Adım bir ve iki](./media/asynctrace-onetwo.png "Asynctrace-ONETWO")

Hem hem de `AccessTheWebAsync` `client.GetStringAsync`öğesinindönüş türü. <xref:System.Threading.Tasks.Task%601> İçin `AccessTheWebAsync`, TResult bir tamsayıdır. İçin `GetStringAsync`, TResult bir dizedir. Zaman uyumsuz yöntem dönüş türleri hakkında daha fazla bilgi için bkz. [Async ReturnC#Types ()](./async-return-types.md).

Bir görev döndüren zaman uyumsuz yöntem, Denetim çağırana geri dönzaman bir görev örneği döndürür. Çağrılan yöntemde bir `await` işleçle karşılaşıldığında veya çağrılan yöntem sona erdiğinde, denetim zaman uyumsuz bir yöntemden çağırana döner. "Üç" ile "ALTıDAN" Etiketlenmiş görüntüleme satırları işlemin bu bölümünü izler.

### <a name="step-three"></a>Üçüncü adım

İçinde `AccessTheWebAsync`, zaman uyumsuz yöntemi <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> hedef Web sayfasının içeriğini indirmek için çağırılır. Denetim, ' `client.GetStringAsync` den `AccessTheWebAsync` `client.GetStringAsync` ' a döner.

 Yöntemi, `getStringTask` içindeki`AccessTheWebAsync`değişkenine atanan bir dize görevi döndürür. `client.GetStringAsync` Örnek programda aşağıdaki satır, ve atama için `client.GetStringAsync` çağrıyı gösterir.

```csharp
Task<string> getStringTask = client.GetStringAsync("https://msdn.microsoft.com");
```

 Son olarak gerçek bir dize oluşturmak `client.GetStringAsync` için görevi bir Promise olarak düşünebilirsiniz. Bu sırada, bu, `AccessTheWebAsync` ' de taahhüt edilen `client.GetStringAsync`dizeye bağlı değilse, bu iş, bekleme sırasında `client.GetStringAsync` devam edebilir. Örnekte, "üç" olarak etiketlenen aşağıdaki çıktı satırları, bağımsız iş yapmak için fırsatı temsil eder

```output
THREE: Back in AccessTheWebAsync.
           Task getStringTask is started.
           About to await getStringTask & return a Task<int> to startButton_Click.
```

 Aşağıdaki ifade, ne zaman `AccessTheWebAsync` beklediğinde `getStringTask` ' de ilerlemeyi askıya alır.

```csharp
string urlContents = await getStringTask;
```

 Aşağıdaki görüntüde denetim `client.GetStringAsync` `getStringTask` akışını, bir await işlecinin uygulamasına `getStringTask` ve oluşturma işleminden öğesine kadar gösterir.

 ![Üçüncü adım](./media/asynctrace-three.png "Asynctrace-üç")

 Await ifadesi dönüşene `AccessTheWebAsync` kadar `client.GetStringAsync` askıya alır. Bu sırada denetim, ' `AccessTheWebAsync` `startButton_Click`ın çağıranına döner.

> [!NOTE]
> Genellikle, zaman uyumsuz bir yöntem çağrısını hemen bekleolursunuz. Örneğin, aşağıdaki atama, oluşturan ve daha sonra bekleyen `getStringTask`önceki kodun yerini alır:`string urlContents = await client.GetStringAsync("https://msdn.microsoft.com");`
>
> Bu konuda, Await işleci daha sonra Denetim akışını program aracılığıyla işaretleyen çıkış satırlarına uyum sağlayacak şekilde uygulanır.

### <a name="step-four"></a>4\. adım

`AccessTheWebAsync` Tarafından`Task<int>`belirtilen dönüş türü. Bu nedenle, askıya alındığında, için `startButton_Click`bir tamsayı görevi döndürür. `AccessTheWebAsync` Döndürülen görevin `getStringTask`olmadığını anlamalısınız. Döndürülen görev, `AccessTheWebAsync`askıya alınan yöntemde ne yapılması gerektiğini temsil eden yeni bir tamsayı görevi. Görev tamamlandığında bir tamsayı üretmek `AccessTheWebAsync` için görevi bir taahhüddir.

Aşağıdaki ifade bu görevi `getLengthTask` değişkenine atar.

```csharp
Task<int> getLengthTask = AccessTheWebAsync();
```

 ' De `AccessTheWebAsync`olduğu `startButton_Click` gibi, görev beklenene kadar zaman uyumsuz görevin (`getLengthTask`) sonuçlarına bağlı olmayan çalışmaya devam edebilir. Aşağıdaki çıktı satırları bu işi temsil eder.

```output
FOUR:  Back in startButton_Click.
           Task getLengthTask is started.
           About to await getLengthTask -- no caller to return to.
```

 İlerleme durumu, beklediğinde `getLengthTask` askıya alınır. `startButton_Click` Aşağıdaki atama açıklaması tamamlanana kadar `startButton_Click` `AccessTheWebAsync` askıya alınır.

```csharp
int contentLength = await getLengthTask;
```

 Aşağıdaki `AccessTheWebAsync` çizimde, oklar bir `getLengthTask`değerin atanması için içindeki Await ifadesinden denetim akışını gösterir ve `startButton_Click` ardından beklenene kadar `getLengthTask` normal işleme gelir.

 4\. ![adım](./media/asynctrace-four.png "Asynctrace-dört")

### <a name="step-five"></a>5\. adım

`AccessTheWebAsync` İşlemin tamamlandığını `client.GetStringAsync` işaret ederse, içindeki işleme askıya alma işleminden serbest bırakılır ve await ifadesinin ötesinde devam edebilir. Aşağıdaki çıktı satırları işleme sürdürme temsil eder.

```output
FIVE:  Back in AccessTheWebAsync.
           Task getStringTask is complete.
           Processing the return statement.
           Exiting from AccessTheWebAsync.
```

 Return ifadesinin `urlContents.Length`işleneni, `AccessTheWebAsync` döndüren görevde saklanır. Await ifadesi bu değeri içindeki `getLengthTask` `startButton_Click`öğesinden alır.

 Aşağıdaki görüntüde (ve `client.GetStringAsync` `getStringTask`) sonra denetimin aktarımı gösterilmektedir.

 ![5. adım](./media/asynctrace-five.png "Asynctrace-beş")

 `AccessTheWebAsync`tamamlandı olarak çalışır ve denetimi `startButton_Click`' a döner, bu da tamamlamayı bekliyor.

### <a name="step-six"></a>Altı adım

İşlemin tamamlandığını `startButton_Async`işaret ederse, işleme ' de await ifadesinin ötesinde devam edebilir. `AccessTheWebAsync` Aslında programın daha fazla şey yoktur.

Aşağıdaki çıktı satırları içinde `startButton_Async`işleme sürdürme temsil eder:

```output
SIX:   Back in startButton_Click.
           Task getLengthTask is finished.
           Result from AccessTheWebAsync is stored in contentLength.
           About to display contentLength and exit.
```

 Await ifadesi ' de `getLengthTask` `AccessTheWebAsync`return deyiminin işleneni olan Integer değerinden alır. Aşağıdaki ifade bu değeri `contentLength` değişkenine atar.

```csharp
int contentLength = await getLengthTask;
```

 Aşağıdaki görüntüde ' den `AccessTheWebAsync` ' e `startButton_Click`denetim dönüşü gösterilmektedir.

 ![Altı adım](./media/asynctrace-six.png "Asynctrace-altı")

## <a name="see-also"></a>Ayrıca bkz.

- [Async ve await (C#) ile zaman uyumsuz programlama](./index.md)
- [Zaman uyumsuz dönüş türleriC#()](./async-return-types.md)
- [İzlenecek yol: Async ve await (C#) kullanarak Web 'e erişme](./walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Zaman uyumsuz örnek: Zaman uyumsuz programlarda denetim akışı (C# ve Visual Basic)](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0)
