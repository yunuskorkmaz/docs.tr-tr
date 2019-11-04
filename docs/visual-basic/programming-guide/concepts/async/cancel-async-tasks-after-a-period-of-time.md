---
title: Zaman uyumsuz görevleri bir süre sonra iptal et (Visual Basic)
ms.date: 07/20/2015
ms.assetid: a48045a3-6a99-42af-b824-af340f0b9a5d
ms.openlocfilehash: 37cc1936dc9c55e0dadb4ccb57d549f3653a11b0
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73419830"
---
# <a name="cancel-async-tasks-after-a-period-of-time-visual-basic"></a>Zaman uyumsuz görevleri bir süre sonra iptal et (Visual Basic)

İşlemin bitmesini beklemek istemiyorsanız <xref:System.Threading.CancellationTokenSource.CancelAfter%2A?displayProperty=nameWithType> yöntemini kullanarak zaman uyumsuz bir işlemi bir süre sonra iptal edebilirsiniz. Bu yöntem, `CancelAfter` ifadesi tarafından belirlenen süre içinde tamamlanmamış olan ilişkili görevlerin iptalini zamanlar.

Bu örnek, bir Web sitesi listesini indirmek ve her birinin içindekilerin uzunluğunu göstermek için [zaman uyumsuz bir görevi veya görev listesini (Visual Basic) iptal](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md) etmek üzere geliştirilmiş koda ekler.

> [!NOTE]
> Örnekleri çalıştırmak için, bilgisayarınızda Visual Studio 2012 veya sonraki bir sürümü ve .NET Framework 4,5 veya üzeri bir sürümü yüklü olmalıdır.

## <a name="downloading-the-example"></a>Örnek indiriliyor

Tüm Windows Presentation Foundation (WPF) projesini [zaman uyumsuz örnekten indirebilirsiniz: uygulamanızı Ince ayar](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) yapın ve ardından aşağıdaki adımları izleyin.

1. İndirdiğiniz dosyayı sıkıştırmasını açın ve ardından Visual Studio 'Yu başlatın.

2. Menü çubuğunda **Dosya**, **Aç**, **Proje/çözüm**' ü seçin.

3. **Proje Aç** iletişim kutusunda, açtığınız örnek kodu tutan klasörü açın ve ardından AsyncFineTuningVB için çözüm (. sln) dosyasını açın.

4. **Çözüm Gezgini**, **zaman** hatası ve ardından **Başlangıç projesi olarak ayarla**' yı seçin.

5. Projeyi çalıştırmak için F5 tuşunu seçin.

     Projeyi hata ayıklamadan çalıştırmak için CTRL + F5 tuşlarını seçin.

6. Çıktının tüm Web siteleri, Web sitesi veya bazı Web siteleri için çıktıyı gösterebileceğini doğrulamak için programı birkaç kez çalıştırın.

 Projeyi indirmek istemiyorsanız, bu konunun sonundaki MainWindow. xaml. vb dosyasını gözden geçirebilirsiniz.

## <a name="building-the-example"></a>Örnek oluşturma

Bu konudaki örnek, bir görev listesini iptal etmek için [zaman uyumsuz bir görevi veya görev listesini iptal etmek (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md) için geliştirilmiş projeye ekler. Örnek, aynı kullanıcı arabirimini kullanır, ancak **iptal** düğmesi açıkça kullanılmaz.

Örneği kendiniz oluşturmak için, "örneği Indirme" bölümündeki yönergeleri izleyin, ancak **Başlangıç projesi**olarak iptal eden **ınlıftasks** ' ı seçin. Bu konudaki değişiklikleri bu projeye ekleyin.

Görevler iptal edildi olarak işaretlenmeden önce en uzun süreyi belirtmek için, aşağıdaki örnekte gösterildiği gibi `startButton_Click``CancelAfter` bir çağrı ekleyin. Toplama, yıldız işareti ile işaretlenir.

```vb
Private Async Sub startButton_Click(sender As Object, e As RoutedEventArgs)

    ' Instantiate the CancellationTokenSource.
    cts = New CancellationTokenSource()

    resultsTextBox.Clear()

    Try
        ' ***Set up the CancellationTokenSource to cancel after 2.5 seconds. (You
        ' can adjust the time.)
        cts.CancelAfter(2500)

        Await AccessTheWebAsync(cts.Token)
        resultsTextBox.Text &= vbCrLf & "Downloads complete."

    Catch ex As OperationCanceledException
        resultsTextBox.Text &= vbCrLf & "Downloads canceled." & vbCrLf

    Catch ex As Exception
        resultsTextBox.Text &= vbCrLf & "Downloads failed." & vbCrLf
    End Try

    ' Set the CancellationTokenSource to Nothing when the download is complete.
    cts = Nothing
End Sub
```

Çıktının tüm Web siteleri, Web sitesi veya bazı Web siteleri için çıktıyı gösterebileceğini doğrulamak için programı birkaç kez çalıştırın. Aşağıdaki çıktı bir örnektir:

```console
Length of the downloaded string: 35990.

Length of the downloaded string: 407399.

Length of the downloaded string: 226091.

Downloads canceled.
```

## <a name="complete-example"></a>Tam Örnek

Aşağıdaki kod, örnek için MainWindow. xaml. vb dosyasının tüm metinkodudur. Yıldız işaretleri bu örnek için eklenen öğeleri işaretler.

<xref:System.Net.Http>için bir başvuru eklemeniz gerektiğini unutmayın.

Projeyi [zaman uyumsuz örnekten indirebilirsiniz: uygulamanızı hassas bir şekilde ayarlama](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).

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
            ' ***Set up the CancellationTokenSource to cancel after 2.5 seconds. (You
            ' can adjust the time.)
            cts.CancelAfter(2500)

            Await AccessTheWebAsync(cts.Token)
            resultsTextBox.Text &= vbCrLf & "Downloads complete."

        Catch ex As OperationCanceledException
            resultsTextBox.Text &= vbCrLf & "Downloads canceled." & vbCrLf

        Catch ex As Exception
            resultsTextBox.Text &= vbCrLf & "Downloads failed." & vbCrLf
        End Try

        ' Set the CancellationTokenSource to Nothing when the download is complete.
        cts = Nothing
    End Sub

    ' You can still include a Cancel button if you want to.
    Private Sub cancelButton_Click(sender As Object, e As RoutedEventArgs)

        If cts IsNot Nothing Then
            cts.Cancel()
        End If
    End Sub

    ' Provide a parameter for the CancellationToken.
    ' Change the return type to Task because the method has no return statement.
    Async Function AccessTheWebAsync(ct As CancellationToken) As Task

        Dim client As HttpClient = New HttpClient()

        ' Call SetUpURLList to make a list of web addresses.
        Dim urlList As List(Of String) = SetUpURLList()

        ' Process each element in the list of web addresses.
        For Each url In urlList
            ' GetAsync returns a Task(Of HttpResponseMessage).
            ' Argument ct carries the message if the Cancel button is chosen.
            ' Note that the Cancel button can cancel all remaining downloads.
            Dim response As HttpResponseMessage = Await client.GetAsync(url, ct)

            ' Retrieve the website contents from the HttpResponseMessage.
            Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()

            resultsTextBox.Text &=
                vbCrLf & $"Length of the downloaded string: {urlContents.Length}." & vbCrLf
        Next
    End Function

    ' Add a method that creates a list of web addresses.
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

' Sample output:

' Length of the downloaded string: 35990.

' Length of the downloaded string: 407399.

' Length of the downloaded string: 226091.

' Downloads canceled.
```

## <a name="see-also"></a>Ayrıca bkz.

- [Async ve await ile zaman uyumsuz programlama (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)
- [İzlenecek yol: Async ve await kullanarak Web 'e erişme (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Zaman uyumsuz bir görevi veya görev listesini iptal etme (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md)
- [Zaman uyumsuz uygulamanızda ince ayar yapma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md)
- [Zaman uyumsuz örnek: uygulamanıza Ince ayar yapma](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
