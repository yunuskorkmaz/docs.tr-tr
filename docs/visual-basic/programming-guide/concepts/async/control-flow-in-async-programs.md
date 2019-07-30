---
title: Zaman uyumsuz programlarda denetim akışı (Visual Basic)
ms.date: 07/20/2015
ms.assetid: b0443af7-c586-4cb0-b476-742ae4098a96
ms.openlocfilehash: 265efde93cec87594a0407309b58b6bdf11817af
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630600"
---
# <a name="control-flow-in-async-programs-visual-basic"></a>Zaman uyumsuz programlarda denetim akışı (Visual Basic)

`Async` Ve`Await` anahtar sözcüklerini kullanarak zaman uyumsuz programları daha kolay bir şekilde yazabilir ve koruyabilirsiniz. Ancak, programınızın nasıl çalıştığını anlamıyorsanız sonuçlar sizi şaşırtabilir. Bu konu, denetim bir yöntemden diğerine ne zaman taşındığını ve her seferinde hangi bilgilerin aktarılacağını göstermek için basit bir zaman uyumsuz program aracılığıyla denetim akışını izler.

> [!NOTE]
> `Async` Ve`Await` anahtar sözcükleri Visual Studio 2012 ' de tanıtılmıştı.

Genel olarak, zaman [uyumsuz değiştirici içeren](../../../../visual-basic/language-reference/modifiers/async.md) zaman uyumsuz kod içeren yöntemleri işaretlersiniz. Zaman uyumsuz değiştirici ile işaretlenmiş bir yöntemde, yöntemin, çağrılan zaman uyumsuz işlemin tamamlanmasını beklemek için bekleyeceği yeri belirtmek için [await (Visual Basic)](../../../../visual-basic/language-reference/operators/await-operator.md) işlecini kullanabilirsiniz. Daha fazla bilgi için bkz. zaman uyumsuz [programlama, Async ve await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md).

Aşağıdaki örnek, belirtilen bir Web sitesinin içeriğini bir dize olarak indirmek ve dizenin uzunluğunu göstermek için zaman uyumsuz yöntemler kullanır. Örnek aşağıdaki iki yöntemi içerir.

- `startButton_Click`, sonucu çağırır `AccessTheWebAsync` ve görüntüler.

- `AccessTheWebAsync`, bir Web sitesinin içeriğini bir dize olarak indirir ve dizenin uzunluğunu döndürür. `AccessTheWebAsync`, içeriğini indirmek <xref:System.Net.Http.HttpClient> için zaman uyumsuz bir yöntem kullanır. <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>

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

Etiketlenmiş konumların her biri, "BIR"-"ALTıDA", programın geçerli durumuyla ilgili bilgileri görüntüler. Aşağıdaki çıktı oluşturulur.

```
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

Bu konu [için uygulamayı zaman uyumsuz örnekten indirebilirsiniz: Zaman uyumsuz programlarda](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0)denetim akışı. Aşağıdaki adımlar programı açın ve çalıştırın.

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

4. Projenin `AsyncTracer` adı olarak girin ve **Tamam** düğmesini seçin.

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

7. İçin <xref:System.Net.Http>bir başvuru ekleyin.

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

    Aşağıdaki çıktı görünmelidir.

    ```
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

![Adım bir ve iki](../../../../csharp/programming-guide/concepts/async/media/asynctrace-onetwo.png "Asynctrace-ONETWO")

Hem hem de `AccessTheWebAsync` `client.GetStringAsync`öğesinindönüş türü. <xref:System.Threading.Tasks.Task%601> İçin `AccessTheWebAsync`, TResult bir tamsayıdır. İçin `GetStringAsync`, TResult bir dizedir. Zaman uyumsuz yöntem dönüş türleri hakkında daha fazla bilgi için bkz. [Async Return Types (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md).

Bir görev döndüren zaman uyumsuz yöntem, Denetim çağırana geri dönzaman bir görev örneği döndürür. Çağrılan yöntemde bir `Await` işleçle karşılaşıldığında veya çağrılan yöntem sona erdiğinde, denetim zaman uyumsuz bir yöntemden çağırana döner. "Üç" ile "ALTıDAN" Etiketlenmiş görüntüleme satırları işlemin bu bölümünü izler.

### <a name="step-three"></a>Üçüncü adım

İçinde `AccessTheWebAsync`, zaman uyumsuz yöntemi <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> hedef Web sayfasının içeriğini indirmek için çağırılır. Denetim, ' `client.GetStringAsync` den `AccessTheWebAsync` `client.GetStringAsync` ' a döner.

Yöntemi, `getStringTask` içindeki`AccessTheWebAsync`değişkenine atanan bir dize görevi döndürür. `client.GetStringAsync` Örnek programda aşağıdaki satır, ve atama için `client.GetStringAsync` çağrıyı gösterir.

```vb
Dim getStringTask As Task(Of String) = client.GetStringAsync("https://msdn.microsoft.com")
```

Son olarak gerçek bir dize oluşturmak `client.GetStringAsync` için görevi bir Promise olarak düşünebilirsiniz. Bu sırada, bu, `AccessTheWebAsync` ' de taahhüt edilen `client.GetStringAsync`dizeye bağlı değilse, bu iş, bekleme sırasında `client.GetStringAsync` devam edebilir. Örnekte, "üç" olarak etiketlenen aşağıdaki çıktı satırları, bağımsız iş yapmak için fırsatı temsil eder

```
THREE: Back in AccessTheWebAsync.
           Task getStringTask is started.
           About to await getStringTask & return a Task<int> to startButton_Click.
```

 Aşağıdaki ifade, ne zaman `AccessTheWebAsync` beklediğinde `getStringTask` ' de ilerlemeyi askıya alır.

```vb
Dim urlContents As String = Await getStringTask
```

Aşağıdaki görüntüde denetim `client.GetStringAsync` `getStringTask` akışını, bir await işlecinin uygulamasına `getStringTask` ve oluşturma işleminden öğesine kadar gösterir.

![Üçüncü adım](../../../../csharp/programming-guide/concepts/async/media/asynctrace-three.png "Asynctrace-üç")

Await ifadesi dönüşene `AccessTheWebAsync` kadar `client.GetStringAsync` askıya alır. Bu sırada denetim, ' `AccessTheWebAsync` `startButton_Click`ın çağıranına döner.

> [!NOTE]
> Genellikle, zaman uyumsuz bir yöntem çağrısını hemen bekleolursunuz. Örneğin, aşağıdaki atama, oluşturan ve daha sonra bekleyen `getStringTask`önceki kodun yerini alır:`Dim urlContents As String = Await client.GetStringAsync("https://msdn.microsoft.com")`
>
> Bu konuda, Await işleci daha sonra Denetim akışını program aracılığıyla işaretleyen çıkış satırlarına uyum sağlayacak şekilde uygulanır.

### <a name="step-four"></a>4\. adım

`AccessTheWebAsync` Tarafından`Task(Of Integer)`belirtilen dönüş türü. Bu nedenle, askıya alındığında, için `startButton_Click`bir tamsayı görevi döndürür. `AccessTheWebAsync` Döndürülen görevin `getStringTask`olmadığını anlamalısınız. Döndürülen görev, `AccessTheWebAsync`askıya alınan yöntemde ne yapılması gerektiğini temsil eden yeni bir tamsayı görevi. Görev tamamlandığında bir tamsayı üretmek `AccessTheWebAsync` için görevi bir taahhüddir.

Aşağıdaki ifade bu görevi `getLengthTask` değişkenine atar.

```vb
Dim getLengthTask As Task(Of Integer) = AccessTheWebAsync()
```

' De `AccessTheWebAsync`olduğu `startButton_Click` gibi, görev beklenene kadar zaman uyumsuz görevin (`getLengthTask`) sonuçlarına bağlı olmayan çalışmaya devam edebilir. Aşağıdaki çıktı satırları bu işi temsil eder.

```
FOUR:  Back in startButton_Click.
           Task getLengthTask is started.
           About to await getLengthTask -- no caller to return to.
```

İlerleme durumu, beklediğinde `getLengthTask` askıya alınır. `startButton_Click` Aşağıdaki atama açıklaması tamamlanana kadar `startButton_Click` `AccessTheWebAsync` askıya alınır.

```vb
Dim contentLength As Integer = Await getLengthTask
```

Aşağıdaki `AccessTheWebAsync` çizimde, oklar bir `getLengthTask`değerin atanması için içindeki Await ifadesinden denetim akışını gösterir ve `startButton_Click` ardından beklenene kadar `getLengthTask` normal işleme gelir.

4\. ![adım](../../../../csharp/programming-guide/concepts/async/media/asynctrace-four.png "Asynctrace-dört")

### <a name="step-five"></a>5\. adım

`AccessTheWebAsync` İşlemin tamamlandığını `client.GetStringAsync` işaret ederse, içindeki işleme askıya alma işleminden serbest bırakılır ve await ifadesinin ötesinde devam edebilir. Aşağıdaki çıktı satırları işleme sürdürme temsil eder.

```
FIVE:  Back in AccessTheWebAsync.
           Task getStringTask is complete.
           Processing the return statement.
           Exiting from AccessTheWebAsync.
```

Return ifadesinin `urlContents.Length`işleneni, `AccessTheWebAsync` döndüren görevde saklanır. Await ifadesi bu değeri içindeki `getLengthTask` `startButton_Click`öğesinden alır.

Aşağıdaki görüntüde (ve `client.GetStringAsync` `getStringTask`) sonra denetimin aktarımı gösterilmektedir.

![5. adım](../../../../csharp/programming-guide/concepts/async/media/asynctrace-five.png "Asynctrace-beş")

`AccessTheWebAsync`tamamlandı olarak çalışır ve denetimi `startButton_Click`' a döner, bu da tamamlamayı bekliyor.

### <a name="step-six"></a>Altı adım

İşlemin tamamlandığını `startButton_Async`işaret ederse, işleme ' de await ifadesinin ötesinde devam edebilir. `AccessTheWebAsync` Aslında programın daha fazla şey yoktur.

Aşağıdaki çıktı satırları içinde `startButton_Async`işleme sürdürme temsil eder:

```
SIX:   Back in startButton_Click.
           Task getLengthTask is finished.
           Result from AccessTheWebAsync is stored in contentLength.
           About to display contentLength and exit.
```

Await ifadesi ' de `getLengthTask` `AccessTheWebAsync`return deyiminin işleneni olan Integer değerinden alır. Aşağıdaki ifade bu değeri `contentLength` değişkenine atar.

```vb
Dim contentLength As Integer = Await getLengthTask
```

Aşağıdaki görüntüde ' den `AccessTheWebAsync` ' e `startButton_Click`denetim dönüşü gösterilmektedir.

![Altı adım](../../../../csharp/programming-guide/concepts/async/media/asynctrace-six.png "Asynctrace-altı")

## <a name="see-also"></a>Ayrıca bkz.

- [Async ve await ile zaman uyumsuz programlama (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)
- [Zaman uyumsuz dönüş türleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md)
- [İzlenecek yol: Async ve await kullanarak Web 'e erişme (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Zaman uyumsuz örnek: Zaman uyumsuz programlarda denetim akışı (C# ve Visual Basic)](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0)
