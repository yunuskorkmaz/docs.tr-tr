---
title: Async Programlarında Kontrol Akışı (C#)
ms.date: 07/20/2015
ms.assetid: fc92b08b-fe1d-4d07-84ab-5192fafe06bb
ms.openlocfilehash: 99f80a86f14179c5f270064a9f96e35f8611ef13
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "70204448"
---
# <a name="control-flow-in-async-programs-c"></a>Async programlarında kontrol akışı (C#)

Anahtar kelimeleri kullanarak eşzamanlı programları daha kolay `async` yazabilir `await` ve sürdürebilirsiniz. Ancak, programınızın nasıl çalıştığını anlamazsanız sonuçlar sizi şaşırtabilir. Bu konu, denetimin bir yöntemden diğerine ne zaman taşındığını ve her seferinde hangi bilgilerin aktarıldığını göstermek için basit bir async programı aracılığıyla denetim akışını izler.

Genel olarak, [async (C#)](../../../language-reference/keywords/async.md) değiştirici ile asynchronous kodu içeren yöntemleri işaretlersiniz. Async değiştirici ile işaretlenmiş bir yöntemde, yöntemin tamamlanmasını beklemek için nerede duraklatılır söyleniyor belirtmek için bir [bekleme (C#)](../../../language-reference/operators/await.md) işleci kullanabilirsiniz. Daha fazla bilgi için, [async ile Asynchronous Programming bakın ve bekliyor (C#)](./index.md).

Aşağıdaki örnek, belirli bir web sitesinin içeriğini dize olarak indirmek ve dize uzunluğunu görüntülemek için async yöntemlerini kullanır. Örnek, aşağıdaki iki yöntemi içerir.

- `startButton_Click`, sonucu `AccessTheWebAsync` arar ve görüntüler.

- `AccessTheWebAsync`, bir web sitesinin içeriğini dize olarak indirir ve dize uzunluğunu döndürür. `AccessTheWebAsync`içeriğini indirmek için <xref:System.Net.Http.HttpClient> bir <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>eşzamanlı yöntem kullanır.

Program boyunca stratejik noktalarda numaralanmış ekran çizgileri görünür ve programın nasıl çalıştığını anlamanıza ve işaretlenen her noktada neler olduğunu açıklamanıza yardımcı olur. Ekran çizgileri "Bİr" ile "ALTI" arasında etiketlenir. Etiketler, programın bu kod satırlarına ulaşma sırasını temsil ediyor.

Aşağıdaki kod, programın anahatlarını gösterir.

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

Etiketli konumların her biri, "BİR" ile "ALTI" arasında, programın geçerli durumu hakkında bilgi görüntüler. Aşağıdaki çıktı üretilir:

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

Bu konunun kullandığı kodu MSDN'den indirebilir veya kendiniz oluşturabilirsiniz.

> [!NOTE]
> Örneği çalıştırmak için Visual Studio 2012 veya daha yeni ve .NET Framework 4.5 veya daha yeni bilgisayarınıza yüklü olması gerekir.

### <a name="download-the-program"></a>Programı indirin

Bu konu yla ilgili uygulamayı [Async Sample: Control Flow in Async Programs'dan](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0)indirebilirsiniz. Aşağıdaki adımlar programı açın ve çalıştırın.

1. İndirilen dosyanın zip'ini açın ve Ardından Visual Studio'yu başlatın.

2. Menü çubuğunda **Dosya** > **Aç** > **Projesi/Çözümü'nü**seçin.

3. Sıkıştırılmamış örnek kodu tutan klasöre gidin, çözüm (.sln) dosyasını açın ve ardından projeyi oluşturmak ve çalıştırmak için **F5** tuşunu seçin.

### <a name="create-the-program-yourself"></a>Programı Kendiniz oluşturun

Aşağıdaki Windows Sunu Temeli (WPF) projesi, bu konu için kod örneğini içerir.

Projeyi çalıştırmak için aşağıdaki adımları gerçekleştirin:

1. Visual Studio’yu çalıştırın.

2. Menü çubuğunda**Yeni** > **Proje** **yi seçin.** > 

     **Yeni Proje** iletişim kutusu açılır.

3. **Yüklü** > **Görsel C#** > **Windows Masaüstü** kategorisini seçin ve ardından proje şablonları listesinden **WPF Uygulamasını** seçin.

4. Projenin `AsyncTracer` adı olarak girin ve sonra **Tamam** düğmesini seçin.

     Yeni proje Çözüm **Gezgini'nde**görünür.

5. Visual Studio Code Editor'da **MainWindow.xaml** sekmesini seçin.

     Sekme görünmüyorsa, **Solution Explorer'da**MainWindow.xaml için kısayol menüsünü açın ve ardından **Kodu Görüntüle'yi**seçin.

6. MainWindow.xaml'ın **XAML** görünümünde kodu aşağıdaki kodla değiştirin.

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

     MainWindow.xaml'ın **Tasarım** görünümünde metin kutusu ve düğme içeren basit bir pencere görüntülenir.

7. Için <xref:System.Net.Http>bir başvuru ekleyin.

8. **Çözüm Gezgini'nde,** MainWindow.xaml.cs için kısayol menüsünü açın ve ardından **Kodu Görüntüle'yi**seçin.

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

10. Programı çalıştırmak için **F5** tuşunu seçin ve ardından **Başlat** düğmesini seçin.

    Şu çıktı görünür:

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

### <a name="steps-one-and-two"></a>Bir ve İkİ Adım

İlk iki görüntü satırı yolu `startButton_Click` `AccessTheWebAsync`çağrı `AccessTheWebAsync` olarak izler ve <xref:System.Net.Http.HttpClient> eşsenkronize yöntemi <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>çağırır. Aşağıdaki resimde yöntemden yönteme çağrılar özetleniyor.

![Bir ve İkİ Adım](./media/asynctrace-onetwo.png "AsyncTrace-ONETWO")

Her ikisinin `AccessTheWebAsync` de `client.GetStringAsync` <xref:System.Threading.Tasks.Task%601>dönüş türü ve . Için `AccessTheWebAsync`, TResult bir sayıdır. Için `GetStringAsync`, TResult bir dizedir. Async yöntemi iade türleri hakkında daha fazla bilgi [için, Bkz. Async Return Types (C#)](./async-return-types.md).

Görev döndüren async yöntemi, denetim arayana geri kaydığında bir görev örneği döndürür. Denetim, çağrılan yöntemde bir `await` işleçle karşılaşıldığında veya çağrılan yöntem sona erdiğinde async yönteminden arayana geri döner. "ALTI" ile "ÜÇ" etiketli ekran çizgileri işlemin bu bölümünü izler.

### <a name="step-three"></a>Üçüncü Adım

, `AccessTheWebAsync`asynchronous yöntemi <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> hedef web sayfasının içeriğini indirmek için denir. Denetim döndüğünden `AccessTheWebAsync` `client.GetStringAsync` ne zaman ait sayılsın. `client.GetStringAsync`

 Yöntem, `client.GetStringAsync` `getStringTask` `AccessTheWebAsync`'deki değişkene atanan dize görevini döndürür Örnek programdaki aşağıdaki satır, atamaya yapılan çağrıyı `client.GetStringAsync` ve atamayı gösterir.

```csharp
Task<string> getStringTask = client.GetStringAsync("https://msdn.microsoft.com");
```

 Görevi, sonunda gerçek bir dize üreterek `client.GetStringAsync` bir söz olarak düşünebilirsiniz. Bu arada, `AccessTheWebAsync` bu iş varsa bu söz dize bağlı `client.GetStringAsync`değildir , bu `client.GetStringAsync` iş beklerken devam edebilirsiniz. Örnekte, "ÜÇ" olarak etiketlenen aşağıdaki çıktı satırları, bağımsız çalışma yapma fırsatını temsil

```output
THREE: Back in AccessTheWebAsync.
           Task getStringTask is started.
           About to await getStringTask & return a Task<int> to startButton_Click.
```

 Aşağıdaki ifade, beklenen `AccessTheWebAsync` zaman `getStringTask` ilerlemeyi askıya adatır.

```csharp
string urlContents = await getStringTask;
```

 Aşağıdaki resimde, bir bekleme `client.GetStringAsync` işlecinin `getStringTask` `getStringTask` uygulanmasına ve oluşturulmasına kadar denetim akışı gösterilmektedir.

 ![Üçüncü Adım](./media/asynctrace-three.png "AsyncTrace-Üç")

 Bekleyen ifade dönene `client.GetStringAsync` kadar askıya alınır. `AccessTheWebAsync` Bu arada, kontrol arayan döner `AccessTheWebAsync` `startButton_Click`, .

> [!NOTE]
> Genellikle, hemen bir eşzamanlı yöntem için çağrı bekliyor. Örneğin, aşağıdaki atama oluşturan önceki kodu değiştirebilir ve sonra `getStringTask`bekliyor:`string urlContents = await client.GetStringAsync("https://msdn.microsoft.com");`
>
> Bu konuda, program aracılığıyla denetim akışını işaretleyen çıkış hatlarını karşılamak için bekleme işleci daha sonra uygulanır.

### <a name="step-four"></a>Dördüncü Adım

Beyan edilen dönüş `AccessTheWebAsync` `Task<int>`türü. Bu nedenle, askıya alındığınızda, `AccessTheWebAsync` tamsayı görevini `startButton_Click`döndürür. Döndürülen görevin `getStringTask`. Döndürülen görev, askıya alınan yöntemde yapılması gerekenleri temsil eden yeni `AccessTheWebAsync`bir tamsayı görevidir. Görev tamamlandığında bir `AccessTheWebAsync` tamsayı üretmek için bir sözdür.

Aşağıdaki deyim, bu görevi `getLengthTask` değişkene atar.

```csharp
Task<int> getLengthTask = AccessTheWebAsync();
```

 Olduğu `AccessTheWebAsync`gibi `startButton_Click` , görev beklenene kadar eşzamanlı görevin sonuçlarına bağlı`getLengthTask`olmayan çalışmalara devam edebilir . Aşağıdaki çıktı satırları bu çalışmayı temsil ediyor.

```output
FOUR:  Back in startButton_Click.
           Task getLengthTask is started.
           About to await getLengthTask -- no caller to return to.
```

 Beklenen `startButton_Click` ilerleme `getLengthTask` askıya alınır. Aşağıdaki atama deyimi `startButton_Click` tamamlanana kadar `AccessTheWebAsync` askıya alınır.

```csharp
int contentLength = await getLengthTask;
```

 Aşağıdaki resimde, oklar bekleme ifadesinden bir değerin `AccessTheWebAsync` atanmasına `getLengthTask`kadar denetim akışını gösterir , `startButton_Click` beklenene kadar `getLengthTask` normal işleme takip eder.

 ![Dördüncü Adım](./media/asynctrace-four.png "AsyncTrace-DÖRT")

### <a name="step-five"></a>Adım BEŞ

`client.GetStringAsync` Sinyaller tamamlandığında, işlem `AccessTheWebAsync` askıya alındı ve bekleme deyimini geçmeye devam edebilir. Aşağıdaki çıktı satırları işlemin yeniden başlamasını temsil emzdir.

```output
FIVE:  Back in AccessTheWebAsync.
           Task getStringTask is complete.
           Processing the return statement.
           Exiting from AccessTheWebAsync.
```

 İade deyiminin operand'ı, `urlContents.Length`döndüren `AccessTheWebAsync` görevde depolanır. Bekleyen ifade bu değeri `getLengthTask` 'den `startButton_Click`alır.

 Aşağıdaki resim, (ve) `client.GetStringAsync` `getStringTask`tamamlandıktan sonra denetim aktarımını gösterir.

 ![Adım BEŞ](./media/asynctrace-five.png "AsyncTrace-BEŞ")

 `AccessTheWebAsync`tamamlanmasını sağlar ve denetim `startButton_Click`tamamlanmayı bekleyen e dönüşlere döner.

### <a name="step-six"></a>Altıncı Adım

`AccessTheWebAsync` Tamamlandığında, işleme bekleme deyimini `startButton_Async`'de geçmiş olarak devam edebilir. Aslında, programın yapacak başka bir şeyi yok.

Aşağıdaki çıktı satırları aşağıdaki işlemin `startButton_Async`devamını temsil eden:

```output
SIX:   Back in startButton_Click.
           Task getLengthTask is finished.
           Result from AccessTheWebAsync is stored in contentLength.
           About to display contentLength and exit.
```

 Bekleyen ifade, `getLengthTask` `AccessTheWebAsync`'deki iade deyiminin operand'ı olan sonda değerinden alır. Aşağıdaki deyim, bu değeri `contentLength` değişkene atar.

```csharp
int contentLength = await getLengthTask;
```

 Aşağıdaki resimde denetimin 'den `AccessTheWebAsync` `startButton_Click`'e geri dönüşü gösterilmektedir

 ![Altıncı Adım](./media/asynctrace-six.png "AsyncTrace-ALTI")

## <a name="see-also"></a>Ayrıca bkz.

- [Async ve await ile Asynchronous Programlama (C#)](./index.md)
- [Async İade Türleri (C#)](./async-return-types.md)
- [Walkthrough: Async kullanarak Web'e erişim ve bekleme (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Async Örnek: Async Programları (C # ve Visual Basic) Kontrol Akışı](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0)
