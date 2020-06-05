---
title: Zaman Uyumsuz Programlarda Denetim Akışı
ms.date: 07/20/2015
ms.assetid: b0443af7-c586-4cb0-b476-742ae4098a96
ms.openlocfilehash: 0c479b9dd2a691b1b353fac54ee3320a895b1c7f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396668"
---
# <a name="control-flow-in-async-programs-visual-basic"></a>Zaman uyumsuz programlarda denetim akışı (Visual Basic)

`Async`Ve anahtar sözcüklerini kullanarak zaman uyumsuz programları daha kolay bir şekilde yazabilir ve koruyabilirsiniz `Await` . Ancak, programınızın nasıl çalıştığını anlamıyorsanız sonuçlar sizi şaşırtabilir. Bu konu, denetim bir yöntemden diğerine ne zaman taşındığını ve her seferinde hangi bilgilerin aktarılacağını göstermek için basit bir zaman uyumsuz program aracılığıyla denetim akışını izler.

> [!NOTE]
> `Async`Ve `Await` anahtar sözcükleri Visual Studio 2012 ' de tanıtılmıştı.

Genel olarak [, zaman uyumsuz değiştirici içeren](../../../language-reference/modifiers/async.md) zaman uyumsuz kod içeren yöntemleri işaretlersiniz. Zaman uyumsuz değiştirici ile işaretlenmiş bir yöntemde, yöntemin, çağrılan zaman uyumsuz işlemin tamamlanmasını beklemek için bekleyeceği yeri belirtmek için [await (Visual Basic)](../../../language-reference/operators/await-operator.md) işlecini kullanabilirsiniz. Daha fazla bilgi için bkz. zaman uyumsuz [programlama, Async ve await (Visual Basic)](index.md).

Aşağıdaki örnek, belirtilen bir Web sitesinin içeriğini bir dize olarak indirmek ve dizenin uzunluğunu göstermek için zaman uyumsuz yöntemler kullanır. Örnek aşağıdaki iki yöntemi içerir.

- `startButton_Click`, sonucu çağırır `AccessTheWebAsync` ve görüntüler.

- `AccessTheWebAsync`, bir Web sitesinin içeriğini bir dize olarak indirir ve dizenin uzunluğunu döndürür. `AccessTheWebAsync`<xref:System.Net.Http.HttpClient>, içeriğini indirmek için zaman uyumsuz bir yöntem kullanır <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> .

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
            vbCrLf & $"Length of the downloaded string: {contentLength}." & vbCrLf

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

Bu konu için uygulamayı [zaman uyumsuz örnek: zaman uyumsuz programlarda denetim akışı '](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0)ndan indirebilirsiniz. Aşağıdaki adımlar programı açın ve çalıştırın.

1. İndirilen dosyayı sıkıştırmasını açın ve ardından Visual Studio 'Yu başlatın.

2. Menü çubuğunda **Dosya**, **Aç**, **Proje/çözüm**' ü seçin.

3. Sıkıştırılmış örnek kodu tutan klasöre gidin, çözüm (. sln) dosyasını açın ve ardından projeyi derlemek ve çalıştırmak için F5 tuşunu seçin.

### <a name="build-the-program-yourself"></a>Programı kendiniz oluşturun

Aşağıdaki Windows Presentation Foundation (WPF) projesi bu konunun kod örneğini içerir.

Projeyi çalıştırmak için aşağıdaki adımları gerçekleştirin:

1. Visual Studio’yu çalıştırın.

2. Menü çubuğunda **Dosya**, **Yeni**, **Proje**' yi seçin.

    **Yeni proje** iletişim kutusu açılır.

3. **Yüklü şablonlar** bölmesinde **Visual Basic**öğesini seçin ve ardından Proje türleri listesinden **WPF uygulaması** ' nı seçin.

4. `AsyncTracer`Projenin adı olarak girin ve **Tamam** düğmesini seçin.

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

7. İçin bir başvuru ekleyin <xref:System.Net.Http> .

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

İlk iki görüntüleme satırı yolu çağrı olarak izler `startButton_Click` `AccessTheWebAsync` ve `AccessTheWebAsync` zaman uyumsuz <xref:System.Net.Http.HttpClient> yöntemi çağırır <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> . Aşağıdaki görüntüde yönteminden yöntemine yapılan çağrılar özetlenmektedir.

![Adım BIR ve ıkı](../../../../csharp/programming-guide/concepts/async/media/asynctrace-onetwo.png "AsyncTrace-ONETWO")

Hem hem de öğesinin dönüş `AccessTheWebAsync` türü `client.GetStringAsync` <xref:System.Threading.Tasks.Task%601> . İçin `AccessTheWebAsync` , TResult bir tamsayıdır. İçin `GetStringAsync` , TResult bir dizedir. Zaman uyumsuz yöntem dönüş türleri hakkında daha fazla bilgi için bkz. [Async Return Types (Visual Basic)](async-return-types.md).

Bir görev döndüren zaman uyumsuz yöntem, Denetim çağırana geri dönzaman bir görev örneği döndürür. `Await`Çağrılan yöntemde bir işleçle karşılaşıldığında veya çağrılan yöntem sona erdiğinde, denetim zaman uyumsuz bir yöntemden çağırana döner. "Üç" ile "ALTıDAN" Etiketlenmiş görüntüleme satırları işlemin bu bölümünü izler.

### <a name="step-three"></a>Üçüncü adım

İçinde `AccessTheWebAsync` , zaman uyumsuz yöntemi <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> hedef Web sayfasının içeriğini indirmek için çağırılır. Denetim, ' den ' a döner `client.GetStringAsync` `AccessTheWebAsync` `client.GetStringAsync` .

`client.GetStringAsync`Yöntemi, içindeki değişkenine atanan bir dize görevi döndürür `getStringTask` `AccessTheWebAsync` . Örnek programda aşağıdaki satır, ve atama için çağrıyı gösterir `client.GetStringAsync` .

```vb
Dim getStringTask As Task(Of String) = client.GetStringAsync("https://msdn.microsoft.com")
```

Son olarak `client.GetStringAsync` gerçek bir dize oluşturmak için görevi bir Promise olarak düşünebilirsiniz. Bu sırada, bu, ' de `AccessTheWebAsync` taahhüt edilen dizeye bağlı değilse `client.GetStringAsync` , bu iş, bekleme sırasında devam edebilir `client.GetStringAsync` . Örnekte, "üç" olarak etiketlenen aşağıdaki çıktı satırları, bağımsız iş yapmak için fırsatı temsil eder

```console
THREE: Back in AccessTheWebAsync.
           Task getStringTask is started.
           About to await getStringTask & return a Task<int> to startButton_Click.
```

 Aşağıdaki ifade, `AccessTheWebAsync` ne zaman beklediğinde ' de ilerlemeyi askıya alır `getStringTask` .

```vb
Dim urlContents As String = Await getStringTask
```

Aşağıdaki görüntüde denetim akışını, `client.GetStringAsync` `getStringTask` `getStringTask` bir await işlecinin uygulamasına ve oluşturma işleminden öğesine kadar gösterir.

![Üçüncü adım](../../../../csharp/programming-guide/concepts/async/media/asynctrace-three.png "AsyncTrace-üç")

Await ifadesi `AccessTheWebAsync` dönüşene kadar askıya alır `client.GetStringAsync` . Bu sırada denetim, ' ın çağıranına döner `AccessTheWebAsync` `startButton_Click` .

> [!NOTE]
> Genellikle, zaman uyumsuz bir yöntem çağrısını hemen bekleolursunuz. Örneğin, aşağıdaki atama, oluşturan ve daha sonra bekleyen önceki kodun yerini alır `getStringTask` :`Dim urlContents As String = Await client.GetStringAsync("https://msdn.microsoft.com")`
>
> Bu konuda, Await işleci daha sonra Denetim akışını program aracılığıyla işaretleyen çıkış satırlarına uyum sağlayacak şekilde uygulanır.

### <a name="step-four"></a>4. adım

Tarafından belirtilen dönüş türü `AccessTheWebAsync` `Task(Of Integer)` . Bu nedenle, `AccessTheWebAsync` askıya alındığında, için bir tamsayı görevi döndürür `startButton_Click` . Döndürülen görevin olmadığını anlamalısınız `getStringTask` . Döndürülen görev, askıya alınan yöntemde ne yapılması gerektiğini temsil eden yeni bir tamsayı görevi `AccessTheWebAsync` . Görev `AccessTheWebAsync` tamamlandığında bir tamsayı üretmek için görevi bir taahhüddir.

Aşağıdaki ifade bu görevi `getLengthTask` değişkenine atar.

```vb
Dim getLengthTask As Task(Of Integer) = AccessTheWebAsync()
```

' De olduğu gibi `AccessTheWebAsync` , `startButton_Click` `getLengthTask` görev beklenene kadar zaman uyumsuz görevin () sonuçlarına bağlı olmayan çalışmaya devam edebilir. Aşağıdaki çıkış satırları bu işi temsil eder:

```console
FOUR:  Back in startButton_Click.
           Task getLengthTask is started.
           About to await getLengthTask -- no caller to return to.
```

İlerleme durumu `startButton_Click` `getLengthTask` , beklediğinde askıya alınır. Aşağıdaki atama açıklaması `startButton_Click` tamamlanana kadar askıya `AccessTheWebAsync` alınır.

```vb
Dim contentLength As Integer = Await getLengthTask
```

Aşağıdaki çizimde, oklar bir değerin atanması için içindeki Await ifadesinden denetim akışını gösterir `AccessTheWebAsync` `getLengthTask` ve ardından `startButton_Click` beklenene kadar normal işleme gelir `getLengthTask` .

![4. adım](../../../../csharp/programming-guide/concepts/async/media/asynctrace-four.png "AsyncTrace-dört")

### <a name="step-five"></a>5. adım

`client.GetStringAsync`İşlemin tamamlandığını işaret ederse, içindeki işleme askıya alma `AccessTheWebAsync` işleminden serbest bırakılır ve await ifadesinin ötesinde devam edebilir. Aşağıdaki çıktı satırları işleme sürdürme temsil eder:

```console
FIVE:  Back in AccessTheWebAsync.
           Task getStringTask is complete.
           Processing the return statement.
           Exiting from AccessTheWebAsync.
```

Return ifadesinin işleneni, `urlContents.Length` döndüren görevde saklanır `AccessTheWebAsync` . Await ifadesi bu değeri içindeki öğesinden alır `getLengthTask` `startButton_Click` .

Aşağıdaki görüntüde (ve) sonra denetimin aktarımı gösterilmektedir `client.GetStringAsync` `getStringTask` .

![5. adım](../../../../csharp/programming-guide/concepts/async/media/asynctrace-five.png "AsyncTrace-beş")

`AccessTheWebAsync`tamamlandı olarak çalışır ve denetimi ' a döner, `startButton_Click` Bu da tamamlamayı bekliyor.

### <a name="step-six"></a>Altı adım

`AccessTheWebAsync`İşlemin tamamlandığını işaret ederse, işleme ' de await ifadesinin ötesinde devam edebilir `startButton_Async` . Aslında programın daha fazla şey yoktur.

Aşağıdaki çıktı satırları içinde işleme sürdürme temsil eder `startButton_Async` :

```console
SIX:   Back in startButton_Click.
           Task getLengthTask is finished.
           Result from AccessTheWebAsync is stored in contentLength.
           About to display contentLength and exit.
```

Await ifadesi `getLengthTask` ' de return deyiminin işleneni olan Integer değerinden alır `AccessTheWebAsync` . Aşağıdaki ifade bu değeri `contentLength` değişkenine atar.

```vb
Dim contentLength As Integer = Await getLengthTask
```

Aşağıdaki görüntüde ' den ' e denetim dönüşü gösterilmektedir `AccessTheWebAsync` `startButton_Click` .

![Altı adım](../../../../csharp/programming-guide/concepts/async/media/asynctrace-six.png "AsyncTrace-altı")

## <a name="see-also"></a>Ayrıca bkz.

- [Async ve await ile zaman uyumsuz programlama (Visual Basic)](index.md)
- [Zaman uyumsuz dönüş türleri (Visual Basic)](async-return-types.md)
- [İzlenecek yol: Async ve await kullanarak Web 'e erişme (Visual Basic)](walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Async örneği: zaman uyumsuz programlarda denetim akışı (C# ve Visual Basic)](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0)
