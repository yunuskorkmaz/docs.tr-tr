---
title: Zaman uyumsuz programlarda denetim akışı (Visual Basic)
ms.date: 07/20/2015
ms.assetid: b0443af7-c586-4cb0-b476-742ae4098a96
ms.openlocfilehash: 74942ec3d293485ea6aae3940d1715af8de67c90
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71352122"
---
# <a name="control-flow-in-async-programs-visual-basic"></a>Zaman uyumsuz programlarda denetim akışı (Visual Basic)

@No__t-0 ve `Await` anahtar sözcüklerini kullanarak zaman uyumsuz programları yazabilir ve daha kolay bir şekilde koruyabilirsiniz. Ancak, programınızın nasıl çalıştığını anlamıyorsanız sonuçlar sizi şaşırtabilir. Bu konu, denetim bir yöntemden diğerine ne zaman taşındığını ve her seferinde hangi bilgilerin aktarılacağını göstermek için basit bir zaman uyumsuz program aracılığıyla denetim akışını izler.

> [!NOTE]
> @No__t-0 ve `Await` anahtar sözcükleri Visual Studio 2012 ' de tanıtılmıştı.

Genel olarak [, zaman uyumsuz değiştirici içeren](../../../../visual-basic/language-reference/modifiers/async.md) zaman uyumsuz kod içeren yöntemleri işaretlersiniz. Zaman uyumsuz değiştirici ile işaretlenmiş bir yöntemde, yöntemin, çağrılan zaman uyumsuz işlemin tamamlanmasını beklemek için bekleyeceği yeri belirtmek için [await (Visual Basic)](../../../../visual-basic/language-reference/operators/await-operator.md) işlecini kullanabilirsiniz. Daha fazla bilgi için bkz. zaman uyumsuz [programlama, Async ve await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md).

Aşağıdaki örnek, belirtilen bir Web sitesinin içeriğini bir dize olarak indirmek ve dizenin uzunluğunu göstermek için zaman uyumsuz yöntemler kullanır. Örnek aşağıdaki iki yöntemi içerir.

- `AccessTheWebAsync` ' i @no__t çağırır ve sonucu görüntüler.

- `AccessTheWebAsync`, bir Web sitesinin içeriğini bir dize olarak indirir ve dizenin uzunluğunu döndürür. `AccessTheWebAsync`, içeriği indirmek için zaman uyumsuz bir <xref:System.Net.Http.HttpClient> yöntemi <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> kullanır.

Numaralandırılmış görüntüleme satırları programın nasıl çalıştığını anlamanıza yardımcı olmak ve işaretlenen her bir noktada ne olduğunu açıklamak için programın tamamında stratejik noktalarda görünür. Görüntüleme satırları "BIR"-"altı" olarak etiketlenir. Etiketler, programın bu kod satırlarına ulaştığı sırayı temsil eder.

Aşağıdaki kod programın bir ana hattını gösterir.

```vb
Class MainWindow

    Private Async Sub StartButton_Click(sender As Object, e As RoutedEventArgs) Handles StartButton.Click

        ' ONE
        Dim getLengthTask As Task(Of Integer) = AccessTheWebAsync()

        ' FOUR
        Dim contentLength As Integer = Await getLengthTask

        ' SIX
        ResultsTextBox.Text &=
            String.Format(vbCrLf & "Length of the downloaded string: {0}." & vbCrLf, contentLength)

    End Sub

    Async Function AccessTheWebAsync() As Task(Of Integer)

        ' TWO
        Dim client As HttpClient = New HttpClient()
        Dim getStringTask As Task(Of String) =
            client.GetStringAsync("https://msdn.microsoft.com")

        ' THREE
        Dim urlContents As String = Await getStringTask

        ' FIVE
        Return urlContents.Length
    End Function

End Class
```

Etiketlenmiş konumların her biri, "BIR"-"ALTıDA", programın geçerli durumuyla ilgili bilgileri görüntüler. Aşağıdaki çıktı üretilir:

```console
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

## <a name="set-up-the-program"></a>Program Ayarlama

Bu konunun kullandığı kodu MSDN 'den indirebilirsiniz veya kendiniz oluşturabilirsiniz.

> [!NOTE]
> Örneği çalıştırmak için, bilgisayarınızda Visual Studio 2012 veya daha yeni bir sürümü ve .NET Framework 4,5 ya da daha yeni bir sürümü yüklü olmalıdır.

### <a name="download-the-program"></a>Programı indir

Bu konu için uygulamayı [Async örneğinden indirebilirsiniz: Zaman uyumsuz programlarda denetim akışı @ no__t-0. Aşağıdaki adımlar programı açın ve çalıştırın.

1. İndirilen dosyayı sıkıştırmasını açın ve ardından Visual Studio 'Yu başlatın.

2. Menü çubuğunda **Dosya**, **Aç**, **Proje/çözüm**' ü seçin.

3. Sıkıştırılmış örnek kodu tutan klasöre gidin, çözüm (. sln) dosyasını açın ve ardından projeyi derlemek ve çalıştırmak için F5 tuşunu seçin.

### <a name="build-the-program-yourself"></a>Programı kendiniz oluşturun

Aşağıdaki Windows Presentation Foundation (WPF) projesi bu konunun kod örneğini içerir.

Projeyi çalıştırmak için aşağıdaki adımları gerçekleştirin:

1. Visual Studio’yu çalıştırın.

2. Menü çubuğunda, **dosya**, **yeni**, **proje**.

    **Yeni proje** iletişim kutusu açılır.

3. **Yüklü şablonlar** bölmesinde **Visual Basic**öğesini seçin ve ardından Proje türleri listesinden **WPF uygulaması** ' nı seçin.

4. Projenin adı olarak `AsyncTracer` girin ve **Tamam** düğmesini seçin.

    Yeni proje **Çözüm Gezgini**görüntülenir.

5. Visual Studio Code düzenleyicisinde **MainWindow. xaml** sekmesini seçin.

    Sekme görünür değilse, **Çözüm Gezgini**' de MainWindow. xaml için kısayol menüsünü açın ve **kodu görüntüle**' yi seçin.

6. MainWindow. xaml ' nin **xaml** görünümünde, kodu aşağıdaki kodla değiştirin.

    ```vb
    <Window
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008" xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006" mc:Ignorable="d" x:Class="MainWindow"
        Title="Control Flow Trace" Height="350" Width="525">
        <Grid>
            <Button x:Name="StartButton" Content="Start" HorizontalAlignment="Left" Margin="221,10,0,0" VerticalAlignment="Top" Width="75"/>
            <TextBox x:Name="ResultsTextBox" HorizontalAlignment="Left" TextWrapping="Wrap" VerticalAlignment="Bottom" Width="510" Height="265" FontFamily="Lucida Console" FontSize="10" VerticalScrollBarVisibility="Visible" d:LayoutOverrides="HorizontalMargin"/>

        </Grid>
    </Window>
    ```

    Bir metin kutusu ve bir düğme içeren basit bir pencere, MainWindow. xaml **Tasarım** görünümünde görünür.

7. @No__t-0 için bir başvuru ekleyin.

8. **Çözüm Gezgini**, MainWindow. xaml. vb için kısayol menüsünü açın ve **kodu görüntüle**' yi seçin.

9. MainWindow. xaml. vb dosyasında, kodu aşağıdaki kodla değiştirin.

    ```vb
    ' Add an Imports statement and a reference for System.Net.Http.
    Imports System.Net.Http

    Class MainWindow

        Private Async Sub StartButton_Click(sender As Object, e As RoutedEventArgs) Handles StartButton.Click

            ' The display lines in the example lead you through the control shifts.
            ResultsTextBox.Text &= "ONE:   Entering StartButton_Click." & vbCrLf &
                "           Calling AccessTheWebAsync." & vbCrLf

            Dim getLengthTask As Task(Of Integer) = AccessTheWebAsync()

            ResultsTextBox.Text &= vbCrLf & "FOUR:  Back in StartButton_Click." & vbCrLf &
                "           Task getLengthTask is started." & vbCrLf &
                "           About to await getLengthTask -- no caller to return to." & vbCrLf

            Dim contentLength As Integer = Await getLengthTask

            ResultsTextBox.Text &= vbCrLf & "SIX:   Back in StartButton_Click." & vbCrLf &
                "           Task getLengthTask is finished." & vbCrLf &
                "           Result from AccessTheWebAsync is stored in contentLength." & vbCrLf &
                "           About to display contentLength and exit." & vbCrLf

            ResultsTextBox.Text &=
                String.Format(vbCrLf & "Length of the downloaded string: {0}." & vbCrLf, contentLength)
        End Sub

        Async Function AccessTheWebAsync() As Task(Of Integer)

            ResultsTextBox.Text &= vbCrLf & "TWO:   Entering AccessTheWebAsync."

            ' Declare an HttpClient object.
            Dim client As HttpClient = New HttpClient()

            ResultsTextBox.Text &= vbCrLf & "           Calling HttpClient.GetStringAsync." & vbCrLf

            ' GetStringAsync returns a Task(Of String).
            Dim getStringTask As Task(Of String) = client.GetStringAsync("https://msdn.microsoft.com")

            ResultsTextBox.Text &= vbCrLf & "THREE: Back in AccessTheWebAsync." & vbCrLf &
                "           Task getStringTask is started."

            ' AccessTheWebAsync can continue to work until getStringTask is awaited.

            ResultsTextBox.Text &=
                vbCrLf & "           About to await getStringTask & return a Task(Of Integer) to StartButton_Click." & vbCrLf

            ' Retrieve the website contents when task is complete.
            Dim urlContents As String = Await getStringTask

            ResultsTextBox.Text &= vbCrLf & "FIVE:  Back in AccessTheWebAsync." &
                vbCrLf & "           Task getStringTask is complete." &
                vbCrLf & "           Processing the return statement." &
                vbCrLf & "           Exiting from AccessTheWebAsync." & vbCrLf

            Return urlContents.Length
        End Function

    End Class
    ```

10. Programı çalıştırmak için F5 tuşunu seçin ve sonra **Başlat** düğmesini seçin.

    Aşağıdaki çıkışın görünmesi gerekir:

    ```console
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

İlk iki görüntüleme satırı, yolu `startButton_Click` `AccessTheWebAsync` ' i çağırır ve `AccessTheWebAsync` zaman uyumsuz <xref:System.Net.Http.HttpClient> yöntemi <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> ' ü çağırır. Aşağıdaki görüntüde yönteminden yöntemine yapılan çağrılar özetlenmektedir.

![Bir ve iki](../../../../csharp/programming-guide/concepts/async/media/asynctrace-onetwo.png "ASYNCTRACE-OneTwo") adımları

@No__t-0 ve `client.GetStringAsync` ' in dönüş türü <xref:System.Threading.Tasks.Task%601> ' dir. @No__t-0 için TResult bir tamsayıdır. @No__t-0 için TResult bir dizedir. Zaman uyumsuz yöntem dönüş türleri hakkında daha fazla bilgi için bkz. [Async Return Types (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md).

Bir görev döndüren zaman uyumsuz yöntem, Denetim çağırana geri dönzaman bir görev örneği döndürür. Çağrılan yöntemde bir `Await` işlecine rastlana veya çağrılan yöntem sona erdiğinde denetim zaman uyumsuz bir yöntemden çağırılacaktır. "Üç" ile "ALTıDAN" Etiketlenmiş görüntüleme satırları işlemin bu bölümünü izler.

### <a name="step-three"></a>Üçüncü adım

@No__t-0 ' da, hedef Web sayfasının içeriğini indirmek için <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> zaman uyumsuz yöntemi çağırılır. @No__t-2 ' i döndürdüğünde, denetim `client.GetStringAsync` ' dan `AccessTheWebAsync` ' e döndürür.

@No__t-0 yöntemi `AccessTheWebAsync` ' deki `getStringTask` değişkenine atanan bir dize görevi döndürür. Örnek programda aşağıdaki satır `client.GetStringAsync` ve atamaya yapılan çağrıyı gösterir.

```vb
Dim getStringTask As Task(Of String) = client.GetStringAsync("https://msdn.microsoft.com")
```

Son olarak gerçek bir dize oluşturmak için `client.GetStringAsync` ile görevi bir Promise olarak düşünebilirsiniz. Bu sırada, `AccessTheWebAsync` ' ı `client.GetStringAsync` ' den taahhüt edilen dizeye bağlı değilse, bu iş `client.GetStringAsync` beklerken devam edebilir. Örnekte, "üç" olarak etiketlenen aşağıdaki çıktı satırları, bağımsız iş yapmak için fırsatı temsil eder

```console
THREE: Back in AccessTheWebAsync.
           Task getStringTask is started.
           About to await getStringTask & return a Task<int> to startButton_Click.
```

 Aşağıdaki ifade, `getStringTask` beklendiğinde `AccessTheWebAsync` ' da ilerlemeyi askıya alır.

```vb
Dim urlContents As String = Await getStringTask
```

Aşağıdaki görüntüde, `client.GetStringAsync` ' dan `getStringTask` ' e atamaya ve `getStringTask` ' nin bir await işlecinin uygulamasına oluşturulmasıyla olan denetim akışı gösterilmektedir.

![Adım üç](../../../../csharp/programming-guide/concepts/async/media/asynctrace-three.png "Asynctrace-üç")

Await ifadesi `AccessTheWebAsync` `client.GetStringAsync` dönene kadar askıya alır. Bu sırada denetim, `AccessTheWebAsync`, `startButton_Click` ' i çağırana döner.

> [!NOTE]
> Genellikle, zaman uyumsuz bir yöntem çağrısını hemen bekleolursunuz. Örneğin, aşağıdaki atama, oluşturan önceki kodun yerini alır `getStringTask`: `Dim urlContents As String = Await client.GetStringAsync("https://msdn.microsoft.com")`
>
> Bu konuda, Await işleci daha sonra Denetim akışını program aracılığıyla işaretleyen çıkış satırlarına uyum sağlayacak şekilde uygulanır.

### <a name="step-four"></a>4\. adım

@No__t-0 ' ın belirtilen dönüş türü `Task(Of Integer)` ' dir. Bu nedenle, `AccessTheWebAsync` askıya alındığında, `startButton_Click` ' e kadar bir tamsayı görevi döndürür. Döndürülen görevin `getStringTask` olmadığını anlamalısınız. Döndürülen görev, askıya alınan yöntemde nelerin yapılabileceklerini temsil eden yeni bir tamsayı görevi `AccessTheWebAsync` ' dır. Görev tamamlandığında bir tamsayı üretmek için `AccessTheWebAsync` ' dan bir Promise olur.

Aşağıdaki ifade bu görevi `getLengthTask` değişkenine atar.

```vb
Dim getLengthTask As Task(Of Integer) = AccessTheWebAsync()
```

@No__t-0 ' da olduğu gibi, `startButton_Click`, görev beklenene kadar zaman uyumsuz görevin sonuçlarına bağlı olmayan çalışmalarla devam edebilir (`getLengthTask`). Aşağıdaki çıkış satırları bu işi temsil eder:

```console
FOUR:  Back in startButton_Click.
           Task getLengthTask is started.
           About to await getLengthTask -- no caller to return to.
```

@No__t-0 ' daki ilerleme, `getLengthTask` beklediğinde askıya alınır. @No__t-1 tamamlanana kadar aşağıdaki atama ekstresi `startButton_Click` ' ını askıya alır.

```vb
Dim contentLength As Integer = Await getLengthTask
```

Aşağıdaki çizimde, oklar, `getLengthTask` beklenene kadar, `AccessTheWebAsync` ' daki await ifadesinde denetim akışını `getLengthTask` ' e bir değer atamaya ve ardından `startButton_Click` ' de normal işlemeye göre gösterir.

![Adım dört](../../../../csharp/programming-guide/concepts/async/media/asynctrace-four.png "ASYNCTRACE-dört")

### <a name="step-five"></a>5\. adım

@No__t-0 ' ın tamamlandığını işaret ederse, `AccessTheWebAsync` ' deki işleme askıya alma işleminden yayımlanır ve await ifadesinin ötesinde devam edebilir. Aşağıdaki çıktı satırları işleme sürdürme temsil eder:

```console
FIVE:  Back in AccessTheWebAsync.
           Task getStringTask is complete.
           Processing the return statement.
           Exiting from AccessTheWebAsync.
```

@No__t-0 dönüş ifadesinin işleneni, `AccessTheWebAsync` ' in döndürdüğü görevde depolanır. Await ifadesi bu değeri `startButton_Click` ' deki `getLengthTask` ' dan alır.

Aşağıdaki görüntüde `client.GetStringAsync` ' dan (ve `getStringTask`) sonra denetimin aktarımı gösterilmektedir.

![Adım beş](../../../../csharp/programming-guide/concepts/async/media/asynctrace-five.png "ASYNCTRACE-beş")

`AccessTheWebAsync` tamamlanmayı çalışır ve denetim, `startButton_Click` ' e döner ve bu da tamamlamayı bekliyor.

### <a name="step-six"></a>Altı adım

@No__t-0 ' ın tamamlandığını işaret ederse, işleme `startButton_Async` ' deki await ifadesinin ötesinde devam edebilir. Aslında programın daha fazla şey yoktur.

Aşağıdaki çıktı satırları `startButton_Async` ' da işleme sürdürme temsil eder:

```console
SIX:   Back in startButton_Click.
           Task getLengthTask is finished.
           Result from AccessTheWebAsync is stored in contentLength.
           About to display contentLength and exit.
```

Await ifadesi `getLengthTask` ' dan `AccessTheWebAsync` ' deki return deyiminin işleneni olan Integer değerini alır. Aşağıdaki ifade, bu değeri `contentLength` değişkenine atar.

```vb
Dim contentLength As Integer = Await getLengthTask
```

Aşağıdaki görüntüde `AccessTheWebAsync` ' dan `startButton_Click` ' e denetim dönüşü gösterilmektedir.

![Adım altı](../../../../csharp/programming-guide/concepts/async/media/asynctrace-six.png "ASYNCTRACE-altı")

## <a name="see-also"></a>Ayrıca bkz.

- [Async ve await ile zaman uyumsuz programlama (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)
- [Zaman uyumsuz dönüş türleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md)
- [İzlenecek yol: Async ve await kullanarak Web 'e erişme (Visual Basic) ](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Zaman uyumsuz örnek: Zaman uyumsuz programlarda denetim akışı (C# ve Visual Basic) ](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0)
