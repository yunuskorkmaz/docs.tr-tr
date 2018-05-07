---
title: (Visual Basic) zaman uyumsuz programlarda denetim akışı
ms.date: 07/20/2015
ms.assetid: b0443af7-c586-4cb0-b476-742ae4098a96
ms.openlocfilehash: 2de9c00e5094a1c40e64bdf5215157867372be8c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="control-flow-in-async-programs-visual-basic"></a>(Visual Basic) zaman uyumsuz programlarda denetim akışı
Yazma ve kullanarak zaman uyumsuz programlar daha kolay korumak `Async` ve `Await` anahtar sözcükler. Programınızı nasıl çalıştığını anlamak yoktur, ancak, sonuçlar beklenmedik. Bu konu izlemeler her zaman bir yönteminden denetimi başka hangi bilgileri taşır göstermek için bir basit zaman uyumsuz program aracılığıyla denetim akışı aktarılır.  
  
> [!NOTE]
>  `Async` Ve `Await` anahtar sözcükler, Visual Studio 2012'de sunulmuştur.  
  
 Zaman uyumsuz koduyla içeren yöntemlerini işaretlemek genel olarak, [zaman uyumsuz](../../../../visual-basic/language-reference/modifiers/async.md) değiştiricisi. Zaman uyumsuz değiştiricisi ile işaretli bir yöntem içinde kullanabileceğiniz bir [bekleme (Visual Basic)](../../../../visual-basic/language-reference/operators/await-operator.md) burada bir çağrılan zaman uyumsuz işlemin tamamlanmasını beklemek için yöntem duraklayacağını belirtmek üzere işleci. Daha fazla bilgi için bkz: [zaman uyumsuz programlama uyumsuz ve bekleme (Visual Basic) ile](../../../../visual-basic/programming-guide/concepts/async/index.md).  
  
 Aşağıdaki örnek, bir dize olarak belirtilen bir Web sitesi içeriğini indirmek ve dize uzunluğu görüntülemek için zaman uyumsuz yöntemleri kullanır. Örneğin, aşağıdaki iki yöntem içerir.  
  
-   `startButton_Click`, hangi çağrıları `AccessTheWebAsync` ve sonucu görüntüler.  
  
-   `AccessTheWebAsync`, bir dize olarak bir Web sitesi içeriğini indirir ve dize uzunluğu döndürür. `AccessTheWebAsync` zaman uyumsuz bir kullanan <xref:System.Net.Http.HttpClient> yöntemi, <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>, içerik indirilemedi.  
  
 Program nasıl çalışacağını anlamanıza yardımcı olması için ve işaretlenmiş her noktada ne olacağını açıklamak için program boyunca stratejik noktalarda çizgiler görünür görüntü numaralı. Görüntü satırları "Bir"ile "altı." etiketli Etiketlerin program bu kod satırları ulaştığında sipariş temsil eder.  
  
 Aşağıdaki kod program bir özetini gösterir.  
  
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
            client.GetStringAsync("http://msdn.microsoft.com")  
  
        ' THREE  
        Dim urlContents As String = Await getStringTask  
  
        ' FIVE  
        Return urlContents.Length  
    End Function  
  
End Class  
```  
  
 "Bir"ile "altı," etiketli konumlardan her birindeki program geçerli durumu hakkındaki bilgileri görüntüler. Şu çıktı üretilir.  
  
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
 Bu konuda kullanan kodu MSDN'den yükleyebilir veya kendiniz oluşturabileceğiniz.  
  
> [!NOTE]
>  Örneği çalıştırmak için Visual Studio 2012 veya daha yeni ve .NET Framework 4.5 veya daha yeni bilgisayarınızda yüklü olmalıdır.  
  
### <a name="download-the-program"></a>Programı indir  
 Uygulama için bu konudan indirebilirsiniz [zaman uyumsuz örnek: zaman uyumsuz programlarda denetim akışı](http://go.microsoft.com/fwlink/?LinkId=255285). Aşağıdaki adımları açın ve programı çalıştırın.  
  
1.  İndirilen dosyanın sıkıştırmasını açın ve ardından Visual Studio'yu başlatın.  
  
2.  Menü çubuğunda seçin **dosya**, **açık**, **proje/çözüm**.  
  
3.  Sıkıştırması açılmış örnek kodu içeren klasöre gidin, çözüm (.sln) dosyasını açın ve F5 tuşuna projesini derlemeyi ve çalıştırmayı seçin.  
  
### <a name="build-the-program-yourself"></a>Program kendiniz yapı  
 Aşağıdaki Windows Presentation Foundation (WPF) projesi bu konuya yönelik kod örneği içerir.  
  
 Projeyi çalıştırmak için aşağıdaki adımları gerçekleştirin:  
  
1.  Visual Studio'yu başlatın.  
  
2.  Menü çubuğunda seçin **dosya**, **yeni**, **proje**.  
  
     **Yeni proje** iletişim kutusu açılır.  
  
3.  İçinde **yüklü şablonlar** bölmesinde seçin **Visual Basic**ve ardından **WPF uygulaması** proje türleri listesinden.  
  
4.  Girin `AsyncTracer` projesinin adı olarak ve ardından **Tamam** düğmesi.  
  
     Yeni Proje görünür **Çözüm Gezgini**.  
  
5.  Visual Studio Kod Düzenleyicisi'nde seçin **MainWindow.xaml** sekmesi.  
  
     Sekme görünür değilse, kısayol menüsünde MainWindow.xaml içinde açık **Çözüm Gezgini**ve ardından **görünümü kodu**.  
  
6.  İçinde **XAML** görüntülemek MainWindow.xaml, kodu aşağıdaki kodla değiştirin.  
  
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
  
     Bir düğmeyi ve bir metin kutusu içeren basit bir pencere görünür **tasarım** MainWindow.xaml görünümü.  
  
7.  İçin bir başvuru ekleyin <xref:System.Net.Http>.  
  
8.  İçinde **Çözüm Gezgini**MainWindow.xaml.vb için kısayol menüsünü açın ve ardından **görünümü kodu**.  
  
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
            Dim getStringTask As Task(Of String) = client.GetStringAsync("http://msdn.microsoft.com")  
  
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
  
10. Programını çalıştırın ve ardından için F5 tuşuna seçin **Başlat** düğmesi.  
  
     Şu çıktı görünür.  
  
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
  
## <a name="trace-the-program"></a>Program izleme  
  
### <a name="steps-one-and-two"></a>Birinci ve ikinci adımları  
 İlk iki görüntü satırları yolu olarak izleme `startButton_Click` çağrıları `AccessTheWebAsync`, ve `AccessTheWebAsync` zaman uyumsuz çağrıları <xref:System.Net.Http.HttpClient> yöntemi <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>. Aşağıdaki resimde yöntemi başka bir yöntem çağrıları özetlenmektedir.  
  
 ![Birinci ve ikinci adımları](../../../../csharp/programming-guide/concepts/async/media/asynctrace-onetwo.png "AsyncTrace ONETWO")  
  
 Dönüş türü, her ikisi de `AccessTheWebAsync` ve `client.GetStringAsync` olan <xref:System.Threading.Tasks.Task%601>. İçin `AccessTheWebAsync`, TResult bir tamsayı değil. İçin `GetStringAsync`, TResult olan bir dize. Zaman uyumsuz yöntem dönüş türleri hakkında daha fazla bilgi için bkz: [zaman uyumsuz dönüş türleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md).  
  
 Denetim çağırana geri geçtiğinde bir görev döndüren zaman uyumsuz yöntem bir görev örneği döndürür. Denetim bir zaman uyumsuz yöntemden çağırıcısına döndürür ya da zaman bir `Await` işleci çağrılan yöntemin veya çağrılan yöntemin sona erdiğinde karşılaştı. "Üç"ile "altı" etiketli görüntü satırları işleminin bu bölümü izleme.  
  
### <a name="step-three"></a>ÜÇ adım  
 İçinde `AccessTheWebAsync`, zaman uyumsuz yöntem <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> hedef Web sayfasının içeriğini indirmek için çağrılır. Denetim döndürür `client.GetStringAsync` için `AccessTheWebAsync` zaman `client.GetStringAsync` döndürür.  
  
 `client.GetStringAsync` Yöntemi döndürür göreve atanan dizesinin `getStringTask` değişkeni `AccessTheWebAsync`. Örnek program aşağıdaki satırda çağrı gösterilmektedir `client.GetStringAsync` ve atama.  
  
```vb  
Dim getStringTask As Task(Of String) = client.GetStringAsync("http://msdn.microsoft.com")  
```  
  
 Görevi tarafından bir promise olarak düşünebilirsiniz `client.GetStringAsync` gerçek bir dize sonunda üretmek için. Bu arada, varsa `AccessTheWebAsync` taahhüt dizeden bağımlı değil yapmak için iş `client.GetStringAsync`, iş devam edebilirsiniz ancak `client.GetStringAsync` bekler. Örnekte, "Üç" etiketli, aşağıdaki satırlar çıktı, bağımsız yapması için Fırsat temsil eder.  
  
```  
THREE: Back in AccessTheWebAsync.  
           Task getStringTask is started.  
           About to await getStringTask & return a Task<int> to startButton_Click.  
```  
  
 Aşağıdaki deyim ediyor askıya `AccessTheWebAsync` zaman `getStringTask` beklemenin.  
  
```vb  
Dim urlContents As String = Await getStringTask  
```  
  
 Aşağıdaki resimde denetim akışı gösterilmektedir `client.GetStringAsync` atamayı için `getStringTask` ve oluşturulmasından `getStringTask` bekleme operatörün uygulama.  
  
 ![ÜÇ adım](../../../../csharp/programming-guide/concepts/async/media/asynctrace-three.png "AsyncTrace üç")  
  
 Bekleme ifade askıya `AccessTheWebAsync` kadar `client.GetStringAsync` döndürür. Bu arada, Denetim çağırana döndürür `AccessTheWebAsync`, `startButton_Click`.  
  
> [!NOTE]
>  Genellikle, zaman uyumsuz bir yöntem çağrısı hemen bekler. Örneğin, aşağıdaki atama oluşturur ve ardından bekler önceki kod değiştirme `getStringTask`: `Dim urlContents As String = Await client.GetStringAsync("http://msdn.microsoft.com")`  
>   
>  Bu konuda, bekleme işleci programı aracılığıyla denetim akışı işaretlemek çıktı satırları uyum sağlamak için daha sonra uygulanır.  
  
### <a name="step-four"></a>DÖRT adım  
 Bildirilmiş dönüş türü `AccessTheWebAsync` olan `Task(Of Integer)`. Bu nedenle, `AccessTheWebAsync` olan askıya, tamsayı, bir görev döndürür `startButton_Click`. Döndürülen görev olmadığını anlamalısınız `getStringTask`. Yeni bir görev ne askıya alınmış yönteminde yapılması kalır gösteren tamsayı döndürülen görevdir `AccessTheWebAsync`. Promise gelen görevdir `AccessTheWebAsync` görev tamamlandığında, bir tamsayı üretmek için.  
  
 Bu görev aşağıdaki deyim atar `getLengthTask` değişkeni.  
  
```vb  
Dim getLengthTask As Task(Of Integer) = AccessTheWebAsync()  
```  
  
 Olarak `AccessTheWebAsync`, `startButton_Click` zaman uyumsuz görev sonuçlarına bağlı olmadığından iş devam edebilirsiniz (`getLengthTask`) görev beklemenin kadar. Aşağıdaki çıkış satırları o iş temsil eder.  
  
```  
FOUR:  Back in startButton_Click.  
           Task getLengthTask is started.  
           About to await getLengthTask -- no caller to return to.  
```  
  
 İlerlemenizi `startButton_Click` zaman askıya `getLengthTask` beklemenin. Aşağıdaki atama deyimini askıya `startButton_Click` kadar `AccessTheWebAsync` tamamlandı.  
  
```vb  
Dim contentLength As Integer = Await getLengthTask  
```  
  
 Aşağıdaki çizimde, bekleme ifadesinden denetim akışını okları Göster `AccessTheWebAsync` değerine atama `getLengthTask`, normal işlemde ardından `startButton_Click` kadar `getLengthTask` beklemenin.  
  
 ![DÖRT adım](../../../../csharp/programming-guide/concepts/async/media/asynctrace-four.png "AsyncTrace dört")  
  
### <a name="step-five"></a>BEŞ adımı  
 Zaman `client.GetStringAsync` tam olarak işleme olduğunu sinyalleri `AccessTheWebAsync` askı durumundan serbest ve bekleme deyimi devam edebilirsiniz. Çıktı aşağıdaki satırları işleme sürdürme temsil eder.  
  
```  
FIVE:  Back in AccessTheWebAsync.  
           Task getStringTask is complete.  
           Processing the return statement.  
           Exiting from AccessTheWebAsync.  
```  
  
 Return deyimi işleneni `urlContents.Length`, görevin depolanır, `AccessTheWebAsync` döndürür. Bu değerden bekleme ifade alır `getLengthTask` içinde `startButton_Click`.  
  
 Aşağıdaki resimde sonra Denetim aktarımını gösterilmiştir `client.GetStringAsync` (ve `getStringTask`) tamamlandığından.  
  
 ![BEŞ adım](../../../../csharp/programming-guide/concepts/async/media/asynctrace-five.png "AsyncTrace beş")  
  
 `AccessTheWebAsync` Tamamlama ve denetim çalışır döner `startButton_Click`, tamamlanması bekleniyor.  
  
### <a name="step-six"></a>Adım 6  
 Zaman `AccessTheWebAsync` işleme tam sinyalleri bekleme deyiminde geçmiş devam edebilir `startButton_Async`. Aslında, programın başka bir şey yapmak için vardır.  
  
 Çıktı aşağıdaki satırları işlemede sürdürme temsil eden `startButton_Async`:  
  
```  
SIX:   Back in startButton_Click.  
           Task getLengthTask is finished.  
           Result from AccessTheWebAsync is stored in contentLength.  
           About to display contentLength and exit.  
```  
  
 Bekleme ifade alır `getLengthTask` içindeki return deyimi işleneni tamsayı değeri `AccessTheWebAsync`. Aşağıdaki deyim bu değeri atar `contentLength` değişkeni.  
  
```vb  
Dim contentLength As Integer = Await getLengthTask  
```  
  
 Aşağıdaki resimde denetiminden dönüş gösterilmiştir `AccessTheWebAsync` için `startButton_Click`.  
  
 ![ALTI adım](../../../../csharp/programming-guide/concepts/async/media/asynctrace-six.png "AsyncTrace altı")  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Zaman uyumsuz programlama ile Async ve Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)  
 [Zaman uyumsuz dönüş türleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md)  
 [İzlenecek yol: Async kullanarak Web'e erişme ve bekleme (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)  
 [Zaman uyumsuz örnek: Denetim akışı zaman uyumsuz programlarda (C# ve Visual Basic)](http://go.microsoft.com/fwlink/?LinkId=255285)
