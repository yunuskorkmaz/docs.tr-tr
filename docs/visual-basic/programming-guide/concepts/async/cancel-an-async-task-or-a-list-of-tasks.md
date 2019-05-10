---
title: Zaman uyumsuz bir görev veya görevleri (Visual Basic) listesini iptal etme
ms.date: 07/20/2015
ms.assetid: a9ee1b71-5bec-4736-a1e9-448042dd7215
ms.openlocfilehash: 6422a7352e79f0f6de563ea08ba41d1803a2f377
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64624717"
---
# <a name="cancel-an-async-task-or-a-list-of-tasks-visual-basic"></a>Zaman uyumsuz bir görev veya görevleri (Visual Basic) listesini iptal etme
Zaman uyumsuz bir uygulamanın bitmesini beklemek istemiyorsanız, iptal etmek için kullanabileceğiniz bir düğme ayarlayabilirsiniz. Bu konudaki örnekleri izleyerek, Web sitelerinin bir listesiyle ya da bir Web sitesinin içeriklerini indiren bir uygulama için bir iptal düğmesi ekleyebilirsiniz.  
  
 Kullanıcı arabirimini örneklerde, [Fine-Tuning Async uygulamanızda (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md) açıklar.  
  
> [!NOTE]
>  Yeni bilgisayarınızda yüklü veya örnekleri çalıştırmak için Visual Studio 2012 veya daha yeni ve .NET Framework 4.5 yüklü olmalıdır.  
  
## <a name="BKMK_CancelaTask"></a> Bir görevi iptal etme  
 İlk örnek ilişkilendirir **iptal** tek bir yükleme göreviyle düğmesi. Uygulama içeriği karşıdan yüklerken düğmeyi seçerseniz, karşıdan yükleme iptal edildi.  
  
### <a name="downloading-the-example"></a>Örneği indirme  
 Tüm Windows Presentation Foundation (WPF) projeden indirebileceğiniz [zaman uyumsuz örneği: Uygulamanıza ince](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) ve sonra aşağıdaki adımları izleyin.  
  
1. İndirdiğiniz dosyanın sıkıştırmasını açın ve sonra Visual Studio'yu başlatın.  
  
2. Menü çubuğunda, **dosya**, **açık**, **proje/çözüm**.  
  
3. İçinde **Proje Aç** iletişim kutusunda, açtığınız örnek kodu barındıran klasörü açın ve ardından AsyncFineTuningVB için çözüm (.sln) dosyasını açın.  
  
4. İçinde **Çözüm Gezgini**, kısayol menüsünü açın **CancelATask** proje ve ardından **başlangıç projesi olarak ayarla**.  
  
5. Projeyi çalıştırmak için F5 tuşuna basın.  
  
     Projeyi hata ayıklama olmadan çalıştırmak için Ctrl + F5 tuşlarını seçin.  
  
 Projeyi indirmek istemiyorsanız, bu konunun sonunda MainWindow.xaml.vb dosyalarını gözden geçirebilirsiniz.  
  
### <a name="building-the-example"></a>Örneği oluşturma  
 Aşağıdaki değişiklikleri ekleyin bir **iptal** bir Web sitesi yükleyen bir uygulamaya düğmesi. İndirme veya örnek oluşturmak istemiyorsanız, bu konunun sonundaki "Tam örnekler" bölümünde yer alan son ürünü gözden geçirebilirsiniz. Yıldız işaretleri, koddaki değişiklikleri işaretler.  
  
 Örneği oluşturmak için kendinize, adım adım "Örneği indirme" bölümündeki yönergeleri izleyin, ancak seçin **başlangıç projesi** olarak **başlangıç projesi** yerine **CancelATask** .  
  
 Ardından bu projenin MainWindow.xaml.vb dosyasına aşağıdaki değişiklikleri ekleyin.  
  
1. Bildirme bir `CancellationTokenSource` değişken `cts`, kendisine erişen tüm yöntemler için kapsam dahilinde olan.  
  
    ```vb  
    Class MainWindow  
  
        ' ***Declare a System.Threading.CancellationTokenSource.  
        Dim cts As CancellationTokenSource  
    ```  
  
2. İçin aşağıdaki olay işleyicisini ekleyelim **iptal** düğmesi. Olay işleyicisi kullanır <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> yöntemi bildirmek için `cts` kullanıcı iptal isteğinde bulunduğunda.  
  
    ```vb  
    ' ***Add an event handler for the Cancel button.  
    Private Sub cancelButton_Click(sender As Object, e As RoutedEventArgs)  
  
        If cts IsNot Nothing Then  
            cts.Cancel()  
        End If  
    End Sub  
    ```  
  
3. Aşağıdaki değişiklikler olay işleyicisi yapma **Başlat** düğme `startButton_Click`.  
  
    - Örneği `CancellationTokenSource`, `cts`.  
  
        ```vb  
        ' ***Instantiate the CancellationTokenSource.  
        cts = New CancellationTokenSource()  
        ```  
  
    - Çağrısında `AccessTheWebAsync`, belirtilen bir Web sitesinin içeriklerini karşıdan yükler, gönderme <xref:System.Threading.CancellationTokenSource.Token%2A?displayProperty=nameWithType> özelliği `cts` bağımsız değişken olarak. `Token` Özelliği, iptal istenirse iletiyi yayar. Kullanıcı karşıdan yükleme işlemini iptal etmeyi seçerse ileti görüntüleyen bir catch bloğu ekleyin. Aşağıdaki kod değişiklikleri gösterir.  
  
        ```vb  
        Try  
            ' ***Send a token to carry the message if cancellation is requested.  
            Dim contentLength As Integer = Await AccessTheWebAsync(cts.Token)  
  
            resultsTextBox.Text &=  
                String.Format(vbCrLf & "Length of the downloaded string: {0}." & vbCrLf, contentLength)  
  
            ' *** If cancellation is requested, an OperationCanceledException results.  
        Catch ex As OperationCanceledException  
            resultsTextBox.Text &= vbCrLf & "Download canceled." & vbCrLf  
  
        Catch ex As Exception  
            resultsTextBox.Text &= vbCrLf & "Download failed." & vbCrLf  
        End Try  
        ```  
  
4. İçinde `AccessTheWebAsync`, kullanın <xref:System.Net.Http.HttpClient.GetAsync%28System.String%2CSystem.Threading.CancellationToken%29?displayProperty=nameWithType> aşırı yükünü `GetAsync` yönteminde <xref:System.Net.Http.HttpClient> bir Web sitesinin içeriklerini karşıdan yüklemek için türü. Geçirmek `ct`, <xref:System.Threading.CancellationToken> parametresinin `AccessTheWebAsync`, ikinci bağımsız değişken. Kullanıcı seçerse belirteç iletiyi taşır **iptal** düğmesi.  
  
     Aşağıdaki kod değişiklikleri göstermektedir `AccessTheWebAsync`.  
  
    ```vb  
    ' ***Provide a parameter for the CancellationToken.  
    Async Function AccessTheWebAsync(ct As CancellationToken) As Task(Of Integer)  
  
        Dim client As HttpClient = New HttpClient()  
  
        resultsTextBox.Text &=  
            String.Format(vbCrLf & "Ready to download." & vbCrLf)  
  
        ' You might need to slow things down to have a chance to cancel.  
        Await Task.Delay(250)  
  
        ' GetAsync returns a Task(Of HttpResponseMessage).   
        ' ***The ct argument carries the message if the Cancel button is chosen.  
        Dim response As HttpResponseMessage = Await client.GetAsync("https://msdn.microsoft.com/library/dd470362.aspx", ct)  
  
        ' Retrieve the website contents from the HttpResponseMessage.  
        Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()  
  
        ' The result of the method is the length of the downloaded website.  
        Return urlContents.Length  
    End Function  
    ```  
  
5. Programı iptal etmezseniz, aşağıdaki çıktıyı üretir.  
  
    ```  
    Ready to download.  
    Length of the downloaded string: 158125.  
    ```  
  
     Seçerseniz **iptal** düğmesi önce program içeriği karşıdan, program şu çıktıyı üretir.  
  
    ```  
    Ready to download.  
    Download canceled.  
    ```  
  
## <a name="BKMK_CancelaListofTasks"></a> Görev listesini iptal etme  
 Aynı ilişkilendirerek birçok görevi iptal etmek için önceki örneği genişletebilirsiniz `CancellationTokenSource` her görev örneği. Seçerseniz **iptal** düğmesi, henüz tamamlanmamış tüm görevleri iptal.  
  
### <a name="downloading-the-example"></a>Örneği indirme  
 Tüm Windows Presentation Foundation (WPF) projeden indirebileceğiniz [zaman uyumsuz örneği: Uygulamanıza ince](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) ve sonra aşağıdaki adımları izleyin.  
  
1. İndirdiğiniz dosyanın sıkıştırmasını açın ve sonra Visual Studio'yu başlatın.  
  
2. Menü çubuğunda, **dosya**, **açık**, **proje/çözüm**.  
  
3. İçinde **Proje Aç** iletişim kutusunda, açtığınız örnek kodu barındıran klasörü açın ve ardından AsyncFineTuningVB için çözüm (.sln) dosyasını açın.  
  
4. İçinde **Çözüm Gezgini**, kısayol menüsünü açın **CancelAListOfTasks** proje ve ardından **başlangıç projesi olarak ayarla**.  
  
5. Projeyi çalıştırmak için F5 tuşuna basın.  
  
     Projeyi hata ayıklama olmadan çalıştırmak için Ctrl + F5 tuşlarını seçin.  
  
 Projeyi indirmek istemiyorsanız, bu konunun sonunda MainWindow.xaml.vb dosyalarını gözden geçirebilirsiniz.  
  
### <a name="building-the-example"></a>Örneği oluşturma  
 Örneği genişletmek için kendiniz adım adım "Örneği indirme" bölümündeki yönergeleri izleyin, ancak seçin **CancelATask** olarak **başlangıç projesi**. Aşağıdaki değişiklikleri bu projeye ekleyin. Yıldız işaretleri, programdaki değişiklikleri işaretler.  
  
1. Web adresleri listesi oluşturmak için bir yöntem ekleyin.  
  
    ```vb  
    ' ***Add a method that creates a list of web addresses.  
    Private Function SetUpURLList() As List(Of String)  
  
        Dim urls = New List(Of String) From  
            {  
                "https://msdn.microsoft.com",  
                "https://msdn.microsoft.com/library/hh290138.aspx",  
                "https://msdn.microsoft.com/library/hh290140.aspx",  
                "https://msdn.microsoft.com/library/dd470362.aspx",  
                "https://msdn.microsoft.com/library/aa578028.aspx",  
                "https://msdn.microsoft.com/library/ms404677.aspx",  
                "https://msdn.microsoft.com/library/ff730837.aspx"  
            }  
        Return urls  
    End Function  
    ```  
  
2. Yöntem çağrısı `AccessTheWebAsync`.  
  
    ```vb  
    ' ***Call SetUpURLList to make a list of web addresses.  
    Dim urlList As List(Of String) = SetUpURLList()  
    ```  
  
3. İçine şu döngüyü ekleyin `AccessTheWebAsync` listesindeki her bir web adresini işlemek için.  
  
    ```vb  
    ' ***Add a loop to process the list of web addresses.  
    For Each url In urlList  
        ' GetAsync returns a Task(Of HttpResponseMessage).   
        ' Argument ct carries the message if the Cancel button is chosen.   
        ' ***Note that the Cancel button can cancel all remaining downloads.  
        Dim response As HttpResponseMessage = Await client.GetAsync(url, ct)  
  
        ' Retrieve the website contents from the HttpResponseMessage.  
        Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()  
  
        resultsTextBox.Text &=  
            String.Format(vbCrLf & "Length of the downloaded string: {0}." & vbCrLf, urlContents.Length)  
    Next  
    ```  
  
4. Çünkü `AccessTheWebAsync` görüntüler uzunlukları, yöntemin herhangi bir şey getirmesi gerekmez. Return ifadesini kaldırın ve yöntemin dönüş türünü değiştirmek <xref:System.Threading.Tasks.Task> yerine <xref:System.Threading.Tasks.Task%601>.  
  
    ```vb  
    Async Function AccessTheWebAsync(ct As CancellationToken) As Task  
    ```  
  
     İçinden yöntemi çağırın `startButton_Click` ifade yerine bir deyim kullanarak.  
  
    ```vb  
    Await AccessTheWebAsync(cts.Token)  
    ```  
  
5. Programı iptal etmezseniz, aşağıdaki çıktıyı üretir.  
  
    ```  
    Length of the downloaded string: 35939.  
  
    Length of the downloaded string: 237682.  
  
    Length of the downloaded string: 128607.  
  
    Length of the downloaded string: 158124.  
  
    Length of the downloaded string: 204890.  
  
    Length of the downloaded string: 175488.  
  
    Length of the downloaded string: 145790.  
  
    Downloads complete.  
    ```  
  
     Seçerseniz **iptal** indirmeleri tam düğmesini, çıktı iptalden önce tamamlanan karşıdan yüklemelerin uzunluklarını içerir.  
  
    ```  
    Length of the downloaded string: 35939.  
  
    Length of the downloaded string: 237682.  
  
    Length of the downloaded string: 128607.  
  
    Downloads canceled.  
    ```  
  
## <a name="BKMK_CompleteExamples"></a> Tam örnekler  
 Aşağıdaki bölümlerde her önceki örnek kodunu içerir. İçin bir başvuru eklemeniz gerektiğini unutmayın <xref:System.Net.Http>.  
  
 İçinden projeleri karşıdan yükleyebileceğiniz [zaman uyumsuz örneği: Uygulamanızı ince ayar](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).  
  
### <a name="cancel-a-task-example"></a>Bir görevi iptal etme örneği  
 Aşağıdaki kod, tek bir görevi iptal eden örnek için tam MainWindow.xaml.vb dosyasıdır.  
  
```vb  
' Add an Imports directive and a reference for System.Net.Http.  
Imports System.Net.Http  
  
' Add the following Imports directive for System.Threading.  
Imports System.Threading  
  
Class MainWindow  
  
    ' ***Declare a System.Threading.CancellationTokenSource.  
    Dim cts As CancellationTokenSource  
  
    Private Async Sub startButton_Click(sender As Object, e As RoutedEventArgs)  
        ' ***Instantiate the CancellationTokenSource.  
        cts = New CancellationTokenSource()  
  
        resultsTextBox.Clear()  
  
        Try  
            ' ***Send a token to carry the message if cancellation is requested.  
            Dim contentLength As Integer = Await AccessTheWebAsync(cts.Token)  
  
            resultsTextBox.Text &=  
                String.Format(vbCrLf & "Length of the downloaded string: {0}." & vbCrLf, contentLength)  
  
            ' *** If cancellation is requested, an OperationCanceledException results.  
        Catch ex As OperationCanceledException  
            resultsTextBox.Text &= vbCrLf & "Download canceled." & vbCrLf  
  
        Catch ex As Exception  
            resultsTextBox.Text &= vbCrLf & "Download failed." & vbCrLf  
        End Try  
  
        ' ***Set the CancellationTokenSource to Nothing when the download is complete.  
        cts = Nothing  
    End Sub  
  
    ' ***Add an event handler for the Cancel button.  
    Private Sub cancelButton_Click(sender As Object, e As RoutedEventArgs)  
  
        If cts IsNot Nothing Then  
            cts.Cancel()  
        End If  
    End Sub  
  
    ' ***Provide a parameter for the CancellationToken.  
    Async Function AccessTheWebAsync(ct As CancellationToken) As Task(Of Integer)  
  
        Dim client As HttpClient = New HttpClient()  
  
        resultsTextBox.Text &=  
            String.Format(vbCrLf & "Ready to download." & vbCrLf)  
  
        ' You might need to slow things down to have a chance to cancel.  
        Await Task.Delay(250)  
  
        ' GetAsync returns a Task(Of HttpResponseMessage).   
        ' ***The ct argument carries the message if the Cancel button is chosen.  
        Dim response As HttpResponseMessage = Await client.GetAsync("https://msdn.microsoft.com/library/dd470362.aspx", ct)  
  
        ' Retrieve the website contents from the HttpResponseMessage.  
        Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()  
  
        ' The result of the method is the length of the downloaded website.  
        Return urlContents.Length  
    End Function  
End Class  
  
' Output for a successful download:  
  
' Ready to download.  
  
' Length of the downloaded string: 158125.  
  
' Or, if you cancel:  
  
' Ready to download.  
  
' Download canceled.  
```  
  
### <a name="cancel-a-list-of-tasks-example"></a>Örnek Görevler listesini iptal etme  
 Aşağıdaki kod, bir Görevler listesini iptal eden örnek için tam MainWindow.xaml.vb dosyasıdır.  
  
```vb  
' Add an Imports directive and a reference for System.Net.Http.  
Imports System.Net.Http  
  
' Add the following Imports directive for System.Threading.  
Imports System.Threading  
  
Class MainWindow  
  
    ' Declare a System.Threading.CancellationTokenSource.  
    Dim cts As CancellationTokenSource  
  
    Private Async Sub startButton_Click(sender As Object, e As RoutedEventArgs)  
  
        ' Instantiate the CancellationTokenSource.  
        cts = New CancellationTokenSource()  
  
        resultsTextBox.Clear()  
  
        Try  
            ' ***AccessTheWebAsync returns a Task, not a Task(Of Integer).  
            Await AccessTheWebAsync(cts.Token)  
            '  ***Small change in the display lines.  
            resultsTextBox.Text &= vbCrLf & "Downloads complete."  
  
        Catch ex As OperationCanceledException  
            resultsTextBox.Text &= vbCrLf & "Downloads canceled." & vbCrLf  
  
        Catch ex As Exception  
            resultsTextBox.Text &= vbCrLf & "Downloads failed." & vbCrLf  
        End Try  
  
        ' Set the CancellationTokenSource to Nothing when the download is complete.  
        cts = Nothing  
    End Sub  
  
    ' Add an event handler for the Cancel button.  
    Private Sub cancelButton_Click(sender As Object, e As RoutedEventArgs)  
  
        If cts IsNot Nothing Then  
            cts.Cancel()  
        End If  
    End Sub  
  
    ' Provide a parameter for the CancellationToken.  
    ' ***Change the return type to Task because the method has no return statement.  
    Async Function AccessTheWebAsync(ct As CancellationToken) As Task  
  
        Dim client As HttpClient = New HttpClient()  
  
        ' ***Call SetUpURLList to make a list of web addresses.  
        Dim urlList As List(Of String) = SetUpURLList()  
  
        ' ***Add a loop to process the list of web addresses.  
        For Each url In urlList  
            ' GetAsync returns a Task(Of HttpResponseMessage).   
            ' Argument ct carries the message if the Cancel button is chosen.   
            ' ***Note that the Cancel button can cancel all remaining downloads.  
            Dim response As HttpResponseMessage = Await client.GetAsync(url, ct)  
  
            ' Retrieve the website contents from the HttpResponseMessage.  
            Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()  
  
            resultsTextBox.Text &=  
                String.Format(vbCrLf & "Length of the downloaded string: {0}." & vbCrLf, urlContents.Length)  
        Next  
    End Function  
  
    ' ***Add a method that creates a list of web addresses.  
    Private Function SetUpURLList() As List(Of String)  
  
        Dim urls = New List(Of String) From  
            {  
                "https://msdn.microsoft.com",  
                "https://msdn.microsoft.com/library/hh290138.aspx",  
                "https://msdn.microsoft.com/library/hh290140.aspx",  
                "https://msdn.microsoft.com/library/dd470362.aspx",  
                "https://msdn.microsoft.com/library/aa578028.aspx",  
                "https://msdn.microsoft.com/library/ms404677.aspx",  
                "https://msdn.microsoft.com/library/ff730837.aspx"  
            }  
        Return urls  
    End Function  
  
End Class  
  
' Output if you do not choose to cancel:  
  
' Length of the downloaded string: 35939.  
  
' Length of the downloaded string: 237682.  
  
' Length of the downloaded string: 128607.  
  
' Length of the downloaded string: 158124.  
  
' Length of the downloaded string: 204890.  
  
' Length of the downloaded string: 175488.  
  
' Length of the downloaded string: 145790.  
  
' Downloads complete.  
  
'  Sample output if you choose to cancel:  
  
' Length of the downloaded string: 35939.  
  
' Length of the downloaded string: 237682.  
  
' Length of the downloaded string: 128607.  
  
' Downloads canceled.  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading.CancellationTokenSource>
- <xref:System.Threading.CancellationToken>
- [Zaman uyumsuz programlama ile Async ve Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)
- [(Visual Basic) Async uygulamanızda hassas ayar yapma](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md)
- [Zaman uyumsuz örneği: Uygulamanızda hassas ayar yapma](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
