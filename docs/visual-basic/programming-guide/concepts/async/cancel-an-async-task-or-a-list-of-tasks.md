---
title: Zaman uyumsuz bir görevi veya görev listesini iptal etme (Visual Basic)
ms.date: 07/20/2015
ms.assetid: a9ee1b71-5bec-4736-a1e9-448042dd7215
ms.openlocfilehash: 89a78e9e423ab4cce9fd3627ec433072ade238dc
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73419862"
---
# <a name="cancel-an-async-task-or-a-list-of-tasks-visual-basic"></a>Zaman uyumsuz bir görevi veya görev listesini iptal etme (Visual Basic)

Bir zaman uyumsuz uygulamayı, bitmesini beklemek istemiyorsanız iptal etmek için kullanabileceğiniz bir düğme ayarlayabilirsiniz. Bu konudaki örnekleri izleyerek, bir Web sitesinin veya Web sitesi listesinin içeriğini yükleyen bir uygulamaya iptal düğmesi ekleyebilirsiniz.

Örnekler, [zaman uyumsuz uygulamanızı (Visual Basic) ayrıntılı olarak ayarlamaya](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md) yönelik kullanıcı arabirimini kullanır.

> [!NOTE]
> Örnekleri çalıştırmak için, bilgisayarınızda Visual Studio 2012 veya daha yeni bir sürümü ve .NET Framework 4,5 ya da daha yeni bir sürümü yüklü olmalıdır.

## <a name="BKMK_CancelaTask"></a>Bir görevi iptal etme

İlk örnek, **iptal** düğmesini tek bir indirme göreviyle ilişkilendirir. Uygulama içerik indirirken düğmeyi seçerseniz, indirme iptal edilir.

### <a name="downloading-the-example"></a>Örnek indiriliyor

Tüm Windows Presentation Foundation (WPF) projesini [zaman uyumsuz örnekten indirebilirsiniz: uygulamanızı Ince ayar](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) yapın ve ardından aşağıdaki adımları izleyin.

1. İndirdiğiniz dosyayı sıkıştırmasını açın ve ardından Visual Studio 'Yu başlatın.

2. Menü çubuğunda **Dosya**, **Aç**, **Proje/çözüm**' ü seçin.

3. **Proje Aç** iletişim kutusunda, açtığınız örnek kodu tutan klasörü açın ve ardından AsyncFineTuningVB için çözüm (. sln) dosyasını açın.

4. **Çözüm Gezgini**' de,,,, Iptal eden **görev** projesi için kısayol menüsünü açın ve ardından **Başlangıç projesi olarak ayarla**' yı seçin.

5. Projeyi çalıştırmak için F5 tuşunu seçin.

     Projeyi hata ayıklamadan çalıştırmak için CTRL + F5 tuşlarını seçin.

 Projeyi indirmek istemiyorsanız, bu konunun sonundaki MainWindow. xaml. vb dosyalarını gözden geçirebilirsiniz.

### <a name="building-the-example"></a>Örnek oluşturma

Aşağıdaki değişiklikler bir Web sitesini indiren uygulamaya bir **iptal** düğmesi ekler. Örneği indirmek veya derlemek istemiyorsanız, bu konunun sonundaki "tüm örnekler" bölümünde son ürünü gözden geçirebilirsiniz. Yıldız işaretleri koddaki değişiklikleri işaretler.

Örneği kendiniz oluşturmak için, "örneği Indirme" bölümündeki yönergeleri izleyin, ancak **Başlangıç projesi** olarak, **1. aşama yerine** **startercode** ' u seçin.

Ardından, bu projenin MainWindow. xaml. vb dosyasına aşağıdaki değişiklikleri ekleyin.

1. Kendisine erişen tüm yöntemler için kapsam içinde olan bir `CancellationTokenSource` değişken `cts`bildirin.

    ```vb
    Class MainWindow

        ' ***Declare a System.Threading.CancellationTokenSource.
        Dim cts As CancellationTokenSource
    ```

2. **İptal** düğmesi için aşağıdaki olay işleyicisini ekleyin. Olay işleyicisi, Kullanıcı iptali istediğinde `cts` bilgilendirmek için <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> yöntemini kullanır.

    ```vb
    ' ***Add an event handler for the Cancel button.
    Private Sub cancelButton_Click(sender As Object, e As RoutedEventArgs)

        If cts IsNot Nothing Then
            cts.Cancel()
        End If
    End Sub
    ```

3. **Başlat** düğmesi için olay işleyicisinde aşağıdaki değişiklikleri yapın `startButton_Click`.

    - `CancellationTokenSource``cts`örneğini oluşturun.

      ```vb
      ' ***Instantiate the CancellationTokenSource.
      cts = New CancellationTokenSource()
      ```

    - Belirtilen bir Web sitesinin içeriğini indiren `AccessTheWebAsync`çağrısında, `cts` <xref:System.Threading.CancellationTokenSource.Token%2A?displayProperty=nameWithType> özelliğini bağımsız değişken olarak gönderin. `Token` özelliği, iptal isteniyorsa iletiyi yayar. Kullanıcı indirme işlemini iptal etmeyi seçerse bir ileti görüntüleyen bir catch bloğu ekleyin. Aşağıdaki kod değişiklikleri gösterir.

      ```vb
      Try
          ' ***Send a token to carry the message if cancellation is requested.
          Dim contentLength As Integer = Await AccessTheWebAsync(cts.Token)

          resultsTextBox.Text &=
              vbCrLf & $"Length of the downloaded string: {contentLength}." & vbCrLf

          ' *** If cancellation is requested, an OperationCanceledException results.
      Catch ex As OperationCanceledException
          resultsTextBox.Text &= vbCrLf & "Download canceled." & vbCrLf

      Catch ex As Exception
          resultsTextBox.Text &= vbCrLf & "Download failed." & vbCrLf
      End Try
      ```

4. `AccessTheWebAsync`, bir Web sitesinin içeriğini indirmek için <xref:System.Net.Http.HttpClient> türünde `GetAsync` yönteminin <xref:System.Net.Http.HttpClient.GetAsync%28System.String%2CSystem.Threading.CancellationToken%29?displayProperty=nameWithType> aşırı yüklemesini kullanın. İkinci bağımsız değişken olarak `AccessTheWebAsync`<xref:System.Threading.CancellationToken> parametresini `ct`geçirin. Kullanıcı **iptal** düğmesini seçerse, belirteç iletiyi taşır.

    Aşağıdaki kod `AccessTheWebAsync`değişiklikleri gösterir.

    ```vb
    ' ***Provide a parameter for the CancellationToken.
    Async Function AccessTheWebAsync(ct As CancellationToken) As Task(Of Integer)

        Dim client As HttpClient = New HttpClient()

        resultsTextBox.Text &= vbCrLf & "Ready to download." & vbCrLf

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

5. Programı iptal ederseniz aşağıdaki çıktıyı üretir:

    ```console
    Ready to download.
    Length of the downloaded string: 158125.
    ```

    Program içeriği indirmeyi bitirmeden **iptal** düğmesini seçerseniz, program aşağıdaki çıktıyı üretir:

    ```console
    Ready to download.
    Download canceled.
    ```

## <a name="BKMK_CancelaListofTasks"></a>Görev listesini iptal etme

Aynı `CancellationTokenSource` örneğini her görevle ilişkilendirerek, daha fazla görevi iptal etmek için önceki örneği genişletebilirsiniz. **İptal** düğmesini seçerseniz, henüz tamamlanmamış tüm görevleri iptal edersiniz.

### <a name="downloading-the-example"></a>Örnek indiriliyor

Tüm Windows Presentation Foundation (WPF) projesini [zaman uyumsuz örnekten indirebilirsiniz: uygulamanızı Ince ayar](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) yapın ve ardından aşağıdaki adımları izleyin.

1. İndirdiğiniz dosyayı sıkıştırmasını açın ve ardından Visual Studio 'Yu başlatın.

2. Menü çubuğunda **Dosya**, **Aç**, **Proje/çözüm**' ü seçin.

3. **Proje Aç** iletişim kutusunda, açtığınız örnek kodu tutan klasörü açın ve ardından AsyncFineTuningVB için çözüm (. sln) dosyasını açın.

4. **Çözüm Gezgini**' de,,,,,,,, iptal eden bir **Proje projesi için** kısayol menüsünü açın ve **Başlangıç projesi olarak ayarla**' yı seçin.

5. Projeyi çalıştırmak için F5 tuşunu seçin.

     Projeyi hata ayıklamadan çalıştırmak için CTRL + F5 tuşlarını seçin.

 Projeyi indirmek istemiyorsanız, bu konunun sonundaki MainWindow. xaml. vb dosyalarını gözden geçirebilirsiniz.

### <a name="building-the-example"></a>Örnek oluşturma

Örneği kendiniz genişletmek için, "örneği Indirme" bölümündeki yönergeleri izleyin, ancak **Başlangıç projesi** **olarak iptal** eden ' i seçin. Aşağıdaki değişiklikleri bu projeye ekleyin. Yıldız işaretleri programdaki değişiklikleri işaretler.

1. Web adreslerinin bir listesini oluşturmak için bir yöntem ekleyin.

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

2. `AccessTheWebAsync`yöntemi çağırın.

    ```vb
    ' ***Call SetUpURLList to make a list of web addresses.
    Dim urlList As List(Of String) = SetUpURLList()
    ```

3. Listedeki her bir Web adresini işlemek için aşağıdaki döngüyü `AccessTheWebAsync` ekleyin.

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
            vbCrLf & $"Length of the downloaded string: {urlContents.Length}." & vbCrLf
    Next
    ```

4. `AccessTheWebAsync` uzunlukları gösterdiği için yöntemin herhangi bir şey döndürmesi gerekmez. Return ifadesini kaldırın ve yöntemin dönüş türünü <xref:System.Threading.Tasks.Task%601>yerine <xref:System.Threading.Tasks.Task> olarak değiştirin.

    ```vb
    Async Function AccessTheWebAsync(ct As CancellationToken) As Task
    ```

    Bir ifadesi yerine deyimi kullanarak `startButton_Click` yöntemi çağırın.

    ```vb
    Await AccessTheWebAsync(cts.Token)
    ```

5. Programı iptal ederseniz aşağıdaki çıktıyı üretir:

    ```console
    Length of the downloaded string: 35939.

    Length of the downloaded string: 237682.

    Length of the downloaded string: 128607.

    Length of the downloaded string: 158124.

    Length of the downloaded string: 204890.

    Length of the downloaded string: 175488.

    Length of the downloaded string: 145790.

    Downloads complete.
    ```

    İndirmeler tamamlanmadan önce **iptal** düğmesini seçerseniz, çıkış, iptalden önce tamamlanan indirmelerin uzunluklarını içerir.

    ```console
    Length of the downloaded string: 35939.

    Length of the downloaded string: 237682.

    Length of the downloaded string: 128607.

    Downloads canceled.
    ```

## <a name="BKMK_CompleteExamples"></a>Tüm örnekler

Aşağıdaki bölümler, önceki örneklerin her birine ilişkin kodu içerir. <xref:System.Net.Http>için bir başvuru eklemeniz gerektiğini unutmayın.

Projeleri [zaman uyumsuz örnekten indirebilirsiniz: uygulamanızı hassas bir şekilde ayarlama](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).

### <a name="cancel-a-task-example"></a>Bir görev örneğini iptal etme

Aşağıdaki kod, tek bir görevi iptal eden örnek için tüm MainWindow. xaml. vb dosyasıdır.

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
                vbCrLf & $"Length of the downloaded string: {contentLength}." & vbCrLf

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
            vbCrLf & "Ready to download." & vbCrLf

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

### <a name="cancel-a-list-of-tasks-example"></a>Görev listesini iptal etme örneği

Aşağıdaki kod, bir görev listesini iptal eden örnek için tüm MainWindow. xaml. vb dosyasıdır.

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
                vbCrLf & $"Length of the downloaded string: {urlContents.Length}." & vbCrLf
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
- [Async ve await ile zaman uyumsuz programlama (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)
- [Zaman uyumsuz uygulamanızda ince ayar yapma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md)
- [Zaman uyumsuz örnek: uygulamanıza Ince ayar yapma](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
