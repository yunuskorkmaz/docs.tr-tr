---
title: Zaman uyumsuz programlarda (Visual Basic) denetim akışı
ms.date: 07/20/2015
ms.assetid: b0443af7-c586-4cb0-b476-742ae4098a96
ms.openlocfilehash: 24a3ece8393fd739ff76fbe759a5572414ce5748
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54532532"
---
# <a name="control-flow-in-async-programs-visual-basic"></a>Zaman uyumsuz programlarda (Visual Basic) denetim akışı
Yazma ve zaman uyumsuz programları daha kolay kullanarak koruduğunuz `Async` ve `Await` anahtar sözcükleri. Ancak, nasıl programınızı anlamazsanız sonuçlar sizi şaşırtabilir. Bu konu, her zaman denetimi başka bir ve hangi bilgileri bir yöntemden diğerine taşır. göstermek için basit bir zamanuyumsuz program aracılığıyla denetim akışını aktarılır izler.  
  
> [!NOTE]
>  `Async` Ve `Await` anahtar sözcükleri Visual Studio 2012'de kullanıma sunulmuştur.  
  
 Genel olarak, zaman uyumsuz kodun yer aldığı yöntemleri işaretleyin [zaman uyumsuz](../../../../visual-basic/language-reference/modifiers/async.md) değiştiricisi. Zaman uyumsuz değiştiriciyle işaretlenmiş bir yöntemde, kullandığınız bir [Await (Visual Basic)](../../../../visual-basic/language-reference/operators/await-operator.md) burada yöntemin tamamlanması bir çağrılan zaman uyumsuz işlem için duraklatacağını belirtmek için işleci. Daha fazla bilgi için [Asynchronous Programming with Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md).  
  
 Aşağıdaki örnek, bir dize olarak belirtilen bir Web sitesinin içeriklerini karşıdan yüklemek ve dizenin uzunluğu görüntülemek için zaman uyumsuz yöntemler kullanır. Örneğin, aşağıdaki iki yöntemi içerir.  
  
-   `startButton_Click`, hangi çağrıları `AccessTheWebAsync` ve sonucu görüntüler.  
  
-   `AccessTheWebAsync`, bir dize olarak bir Web sitesinin içeriklerini karşıdan yükler ve dizenin uzunluğunu döndürür. `AccessTheWebAsync` zaman uyumsuz kullanan <xref:System.Net.Http.HttpClient> yöntemi <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>içeriğini indirmek için.  
  
 Numaralı ekran satırları, programın nasıl çalıştığını anlamanıza yardımcı olmak ve işaretlenmiş her noktada ne olacağını açıklamak için program boyunca stratejik noktalarda görüntülenir. Görüntü satırları "Bir"ile "altı." olarak etiketlenmiştir Etiketler, programın bu kod satırlarını ulaştığında sırayı temsil eder.  
  
 Aşağıdaki kod, programın özetini gösterir.  
  
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
  
 "ONE"ila "SIX" arasındaki etiketli konumların her biri, programın geçerli durumuyla ilgili bilgileri görüntüler. Aşağıdaki çıktı üretilmiştir.  
  
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
 Bu konuda kullanan kodu MSDN sitesinden yükleyebilir veya size kendiniz oluşturabilirsiniz.  
  
> [!NOTE]
>  Yeni bilgisayarınızda yüklü veya örneği çalıştırmak için Visual Studio 2012 veya daha yeni ve .NET Framework 4.5 yüklü olmalıdır.  
  
### <a name="download-the-program"></a>Programı indir  
 Bu konu için uygulamayı indirebilirsiniz [zaman uyumsuz örneği: Denetim akışı zaman uyumsuz programlarda](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0). Aşağıdaki adımlar, açın ve programı çalıştırın.  
  
1.  İndirilen dosyanın sıkıştırmasını açın ve sonra Visual Studio'yu başlatın.  
  
2.  Menü çubuğunda, **dosya**, **açık**, **proje/çözüm**.  
  
3.  Sıkıştırması açılmış örnek kodun bulunduğu klasöre gidin, çözüm (.sln) dosyasını açın ve sonra oluşturmak ve projeyi çalıştırmak için F5 tuşuna basın.  
  
### <a name="build-the-program-yourself"></a>Programı kendiniz oluşturun  
 Aşağıdaki Windows Presentation Foundation (WPF) projesi Bu konu için kod örneği içerir.  
  
 Projeyi çalıştırmak için aşağıdaki adımları gerçekleştirin:  
  
1.  Visual Studio’yu çalıştırın.  
  
2.  Menü çubuğunda, **dosya**, **yeni**, **proje**.  
  
     **Yeni proje** iletişim kutusu açılır.  
  
3.  İçinde **yüklü şablonlar** bölmesinde seçin **Visual Basic**ve ardından **WPF uygulaması** proje türleri listesinden.  
  
4.  Girin `AsyncTracer` projesinin adı olarak seçip **Tamam** düğmesi.  
  
     Yeni Proje görünür **Çözüm Gezgini**.  
  
5.  Visual Studio Kod Düzenleyicisi'nde seçin **MainWindow.xaml** sekmesi.  
  
     Sekme görünür değilse, nde MainWindow.xaml için kısayol menüsünü açın **Çözüm Gezgini**ve ardından **kodu görüntüle**.  
  
6.  İçinde **XAML** MainWindow.xaml görüntülemek için kodu aşağıdaki kodla değiştirin.  
  
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
  
     Bir metin kutusu ve bir düğme içeren basit bir pencere **tasarım** MainWindow.xaml görünümü.  
  
7.  İçin bir başvuru eklemeniz <xref:System.Net.Http>.  
  
8.  İçinde **Çözüm Gezgini**MainWindow.xaml.vb için kısayol menüsünü açın ve ardından **kodu görüntüle**.  
  
9. MainWindow.xaml.vb kodu aşağıdaki kodla değiştirin.  
  
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
  
10. Programı çalıştırın ve ardından F5 tuşuna basın **Başlat** düğmesi.  
  
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
  
## <a name="trace-the-program"></a>Programı İzle  
  
### <a name="steps-one-and-two"></a>BİR ve ikinci adımlar  
 İlk iki görüntü satırı yolu olarak izleme `startButton_Click` çağrıları `AccessTheWebAsync`, ve `AccessTheWebAsync` zaman uyumsuz çağrı <xref:System.Net.Http.HttpClient> yöntemi <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>. Aşağıdaki resimde yöntemden yönteme çağrılar özetlenmektedir.  
  
 ![BİR ve ikinci adımlar](../../../../csharp/programming-guide/concepts/async/media/asynctrace-onetwo.png "AsyncTrace ONETWO")  
  
 Dönüş türü, her ikisi de `AccessTheWebAsync` ve `client.GetStringAsync` olduğu <xref:System.Threading.Tasks.Task%601>. İçin `AccessTheWebAsync`, TResult bir tamsayı olduğu. İçin `GetStringAsync`, TResult olan bir dize. Zaman uyumsuz yöntem dönüş türleri hakkında daha fazla bilgi için bkz: [zaman uyumsuz dönüş türleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md).  
  
 Bir görev döndüren zaman uyumsuz yöntem, Denetim arayana geri geçtiğinde bir görev örneği döndürür. Denetim, uyumsuz bir yöntemden arayanına döner ya da bir `Await` çağrılan yöntem veya çağrılan yöntem sona erdiğinde işleciyle karşılaşıldığında. "Üç"ile "altı" etiketli görüntü satırları işlemin bu kısmında izleme.  
  
### <a name="step-three"></a>Adım üç  
 İçinde `AccessTheWebAsync`, zaman uyumsuz yöntemin <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> hedef Web sayfasının içeriğini indirmek için çağrılır. Denetim döndüğü `client.GetStringAsync` için `AccessTheWebAsync` olduğunda `client.GetStringAsync` döndürür.  
  
 `client.GetStringAsync` Yöntemi bir görev için atanan bir dize döndürür `getStringTask` değişkeninde `AccessTheWebAsync`. Örnek programdaki aşağıdaki satır çağrısını gösterir `client.GetStringAsync` atama.  
  
```vb  
Dim getStringTask As Task(Of String) = client.GetStringAsync("https://msdn.microsoft.com")  
```  
  
 Görevini, hedefi olarak düşünebilirsiniz `client.GetStringAsync` sonuçta gerçek bir dize oluşturmak için. Bu arada, varsa `AccessTheWebAsync` dizeden bağımlı olmayan yapılacak çalışmaya sahipse `client.GetStringAsync`, iş devam edebilirsiniz ancak `client.GetStringAsync` bekler. Örnekte, "Üç" etiketli, aşağıdaki çıktı satırları bağımsız iş yapma fırsatını temsil eder.  
  
```  
THREE: Back in AccessTheWebAsync.  
           Task getStringTask is started.  
           About to await getStringTask & return a Task<int> to startButton_Click.  
```  
  
 Aşağıdaki deyim ilerlemesini askıya alır `AccessTheWebAsync` olduğunda `getStringTask` beklenir.  
  
```vb  
Dim urlContents As String = Await getStringTask  
```  
  
 Aşağıdaki görüntüde, denetim akışı gösterilmektedir. `client.GetStringAsync` atamaya `getStringTask` ve oluşturulmasını `getStringTask` bir Await işlecinin uygulamasına.  
  
 ![ÜÇ adım](../../../../csharp/programming-guide/concepts/async/media/asynctrace-three.png "AsyncTrace üç")  
  
 Await ifadesi askıya `AccessTheWebAsync` kadar `client.GetStringAsync` döndürür. Bu arada, Denetim çağırana döner `AccessTheWebAsync`, `startButton_Click`.  
  
> [!NOTE]
>  Genellikle, bir zaman uyumsuz yöntem çağrısı hemen bekler. Örneğin, aşağıdaki atama oluşturan ve sonra bekleyen önceki kodun yerini alabilir `getStringTask`: `Dim urlContents As String = Await client.GetStringAsync("https://msdn.microsoft.com")`  
>   
>  Bu konuda, await işleci, program aracılığıyla denetim akışını işaretleyen çıkış satırlarını yerleştirmek için daha sonra uygulanır.  
  
### <a name="step-four"></a>Dördüncü adım  
 Bildirilen dönüş türü `AccessTheWebAsync` olduğu `Task(Of Integer)`. Bu nedenle, `AccessTheWebAsync` olan askıya alındı, bir tamsayı görevi döndürür `startButton_Click`. Döndürülen görevin olmadığını anlamanız gereken `getStringTask`. Döndürülen görevin askıya alınmış yönteminde yapılması kalan temsil eden tamsayı, yeni bir görevdir `AccessTheWebAsync`. Görev bir vaadidir `AccessTheWebAsync` görev tamamlandığında bir tamsayı üretmek için.  
  
 Bu görev için aşağıdaki deyimi atar `getLengthTask` değişkeni.  
  
```vb  
Dim getLengthTask As Task(Of Integer) = AccessTheWebAsync()  
```  
  
 Olarak `AccessTheWebAsync`, `startButton_Click` zaman uyumsuz görev sonuçlarına bağlı olmayan çalışmalar ile devam edebilir (`getLengthTask`) kadar görev beklenir. Aşağıdaki çıktı satırları bu işi temsil eder.  
  
```  
FOUR:  Back in startButton_Click.  
           Task getLengthTask is started.  
           About to await getLengthTask -- no caller to return to.  
```  
  
 İlerlemenizi `startButton_Click` zaman askıya `getLengthTask` beklenir. Aşağıdaki atama deyimi askıya `startButton_Click` kadar `AccessTheWebAsync` tamamlandı.  
  
```vb  
Dim contentLength As Integer = Await getLengthTask  
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
  
```vb  
Dim contentLength As Integer = Await getLengthTask  
```  
  
 Aşağıdaki görüntüde kadar denetimin dönüşü gösterilmektedir `AccessTheWebAsync` için `startButton_Click`.  
  
 ![ALTI adım](../../../../csharp/programming-guide/concepts/async/media/asynctrace-six.png "AsyncTrace altı")  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Zaman uyumsuz programlama ile Async ve Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)
- [Zaman uyumsuz dönüş türleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md)
- [İzlenecek yol: Zaman uyumsuz kullanarak Web'e erişme ve Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Zaman uyumsuz örneği: Denetim akışı zaman uyumsuz programlarda (C# ve Visual Basic)](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0)
