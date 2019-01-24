---
title: (Visual Basic) bir süre sonra zaman uyumsuz görevleri iptal etme
ms.date: 07/20/2015
ms.assetid: a48045a3-6a99-42af-b824-af340f0b9a5d
ms.openlocfilehash: a01ab79a2895bd9c5a8ae4782db06eb9dd5664a9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54580557"
---
# <a name="cancel-async-tasks-after-a-period-of-time-visual-basic"></a>(Visual Basic) bir süre sonra zaman uyumsuz görevleri iptal etme
Kullanarak bir süre sonra Zamanuyumsuz bir işlemi iptal edebilirsiniz <xref:System.Threading.CancellationTokenSource.CancelAfter%2A?displayProperty=nameWithType> işlemin tamamlanmasını beklemek istemiyorsanız yöntemi. Bu yöntem tarafından belirlenen süre içinde tam olmayan herhangi bir ilişkili görevin iptalini zamanlar `CancelAfter` ifade.  
  
 Bu örnek içinde geliştirilen koda eklenir [zaman uyumsuz bir görev veya biri listeyi görevler (Visual Basic) iptal](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md) Web sitesi listesini indirmek ve her birindeki içerik uzunluğunu görüntülemek için.  
  
> [!NOTE]
>  Örnekleri çalıştırmak için Visual Studio 2012 veya sonraki sürümünü ve .NET Framework 4.5 olmalıdır veya daha sonra bilgisayarınızda yüklü.  
  
## <a name="downloading-the-example"></a>Örneği indirme  
 Tüm Windows Presentation Foundation (WPF) projeden indirebileceğiniz [zaman uyumsuz örneği: Uygulamanıza ince](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) ve sonra aşağıdaki adımları izleyin.  
  
1.  İndirdiğiniz dosyanın sıkıştırmasını açın ve sonra Visual Studio'yu başlatın.  
  
2.  Menü çubuğunda, **dosya**, **açık**, **proje/çözüm**.  
  
3.  İçinde **Proje Aç** iletişim kutusunda, açtığınız örnek kodu barındıran klasörü açın ve ardından AsyncFineTuningVB için çözüm (.sln) dosyasını açın.  
  
4.  İçinde **Çözüm Gezgini**, kısayol menüsünü açın **CancelAfterTime** proje ve ardından **başlangıç projesi olarak ayarla**.  
  
5.  Projeyi çalıştırmak için F5 tuşuna basın.  
  
     Projeyi hata ayıklama olmadan çalıştırmak için Ctrl + F5 tuşlarını seçin.  
  
6.  Program çıkış tüm Web siteleri, hiçbir Web sitesi veya bazı web siteleri için çıktı gösterebildiğini doğrulamak için birkaç kez çalıştırın.  
  
 Projeyi indirmek istemiyorsanız, bu konunun sonunda MainWindow.xaml.vb dosyasını gözden geçirebilirsiniz.  
  
## <a name="building-the-example"></a>Örneği oluşturma  
 Bu konudaki örnek içinde geliştirilen projeye ekler [zaman uyumsuz bir görev veya biri listeyi görevler (Visual Basic) iptal](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md) Görevler listesini iptal etme. Örnekte aynı Arabirim kullanılmaktadır, ancak **iptal** düğmesi açıkça kullanılmaz.  
  
 Örneği oluşturmak için kendinize, adım adım "Örneği indirme" bölümündeki yönergeleri izleyin, ancak seçin **CancelAListOfTasks** olarak **başlangıç projesi**. Bu konuda, değişiklikleri bu projeye ekleyin.  
  
 Görevleri iptal edildi olarak işaretlenmeden önceki süre üst sınırını belirtmek için bir çağrı ekleyin `CancelAfter` için `startButton_Click`aşağıdaki örnekte gösterildiği gibi. Ayrıca, yıldız işareti ile işaretlenir.  
  
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
  
 Program çıkış tüm Web siteleri, hiçbir Web sitesi veya bazı web siteleri için çıktı gösterebildiğini doğrulamak için birkaç kez çalıştırın. Aşağıdaki çıktı bir örnektir.  
  
```  
Length of the downloaded string: 35990.  
  
Length of the downloaded string: 407399.  
  
Length of the downloaded string: 226091.  
  
Downloads canceled.  
```  
  
## <a name="complete-example"></a>Tam Örnek  
 Aşağıdaki örnek için MainWindow.xaml.vb dosyanın tam metni kodudur. Yıldız işaretleri, bu örnek için eklenen öğeleri işaretler.  
  
 İçin bir başvuru eklemeniz gerektiğini unutmayın <xref:System.Net.Http>.  
  
 Projeden indirebileceğiniz [zaman uyumsuz örneği: Uygulamanızı ince ayar](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).  
  
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
                String.Format(vbCrLf & "Length of the downloaded string: {0}." & vbCrLf, urlContents.Length)  
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
- [Zaman uyumsuz programlama ile Async ve Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)
- [İzlenecek yol: Zaman uyumsuz kullanarak Web'e erişme ve Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Zaman uyumsuz bir görev veya görevleri (Visual Basic) listesini iptal etme](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md)
- [(Visual Basic) Async uygulamanızda hassas ayar yapma](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md)
- [Zaman uyumsuz örneği: Uygulamanızda hassas ayar yapma](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
