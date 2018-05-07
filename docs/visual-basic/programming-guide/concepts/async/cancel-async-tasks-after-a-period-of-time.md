---
title: Bir süre (Visual Basic) sonra zaman uyumsuz görevleri iptal etme
ms.date: 07/20/2015
ms.assetid: a48045a3-6a99-42af-b824-af340f0b9a5d
ms.openlocfilehash: 1be9f976c68db41526aea2fbf250ecd8c4e9521e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="cancel-async-tasks-after-a-period-of-time-visual-basic"></a>Bir süre (Visual Basic) sonra zaman uyumsuz görevleri iptal etme
Kullanarak zaman uyumsuz işlemi bir süre sonra iptal edebilirsiniz <xref:System.Threading.CancellationTokenSource.CancelAfter%2A?displayProperty=nameWithType> işlemin tamamlanmasını beklemek istemiyorsanız yöntemi. Bu yöntem tarafından belirlenen süre içinde tam olmayan herhangi bir ilişkili görevi iptali zamanlar `CancelAfter` ifade.  
  
 Bu örnek da geliştirilmiş kod ekler [bir zaman uyumsuz görev veya bir liste görevleri (Visual Basic) iptal](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md) Web sitelerinin bir listesiyle indirmek ve her biri içeriğini uzunluğu görüntülemek için.  
  
> [!NOTE]
>  Örnekleri çalıştırmak için Visual Studio 2012 veya sonraki sürümünü ve .NET Framework 4.5 olmalıdır veya sonraki bir sürümü bilgisayarınızda yüklü.  
  
## <a name="downloading-the-example"></a>Örnek indirme  
 Tam Windows Presentation Foundation (WPF) projeden indirebilirsiniz [zaman uyumsuz örnek: ince ayar uygulamanız](http://go.microsoft.com/fwlink/?LinkId=255046) ve ardından aşağıdaki adımları izleyin.  
  
1.  İndirdiğiniz dosyanın sıkıştırmasını ve Visual Studio'yu başlatın.  
  
2.  Menü çubuğunda seçin **dosya**, **açık**, **proje/çözüm**.  
  
3.  İçinde **Proje Aç** iletişim kutusunda, sıkıştırması örnek kod tutan klasörü açın ve ardından AsyncFineTuningVB için çözüm (.sln) dosyasını açın.  
  
4.  İçinde **Çözüm Gezgini**, kısayol menüsünü açın **CancelAfterTime** proje ve ardından **başlangıç projesi olarak ayarla**.  
  
5.  Projeyi çalıştırmak için F5 tuşuna seçin.  
  
     Hata ayıklama olmadan projeyi çalıştırmak için Ctrl + F5 anahtarları'i seçin.  
  
6.  Program, çıktı tüm Web siteleri, hiçbir Web siteleri veya bazı web siteleri için çıktı gösterebilir doğrulamak için birkaç kez çalıştırın.  
  
 Projenizi indirin istemiyorsanız, bu konunun sonundaki MainWindow.xaml.vb dosyasını gözden geçirebilirsiniz.  
  
## <a name="building-the-example"></a>Örnek oluşturma  
 Bu konudaki örnek da geliştirilmiş projesine ekler [bir zaman uyumsuz görev veya bir liste görevleri (Visual Basic) iptal](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md) görev listesini iptal etme. Örnek olsa da, aynı kullanıcı arabirimini kullanır **iptal** düğmesi değil kullanılan açıkça.  
  
 Örnek oluşturmak için kendiniz, adım adım "örnek indirme" bölümündeki yönergeleri izleyin, ancak seçin **CancelAListOfTasks** olarak **başlangıç projesi**. Değişiklikleri bu konuda bu projeye ekleyin.  
  
 Görev iptal edildi olarak işaretlenmiş önce maksimum süreyi belirtmek için bir çağrı ekleyin `CancelAfter` için `startButton_Click`, aşağıdaki örnekte gösterildiği gibi. Ek yıldız işaretiyle işaretlenir.  
  
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
  
 Program, çıktı tüm Web siteleri, hiçbir Web siteleri veya bazı web siteleri için çıktı gösterebilir doğrulamak için birkaç kez çalıştırın. Aşağıdaki çıkış bir örnektir.  
  
```  
Length of the downloaded string: 35990.  
  
Length of the downloaded string: 407399.  
  
Length of the downloaded string: 226091.  
  
Downloads canceled.  
```  
  
## <a name="complete-example"></a>Tam Örnek  
 Aşağıdaki kod örneğin MainWindow.xaml.vb dosyasının tam metindir. Yıldız işareti, bu örnek için eklenen öğeleri işaretleyin.  
  
 İçin bir başvuru eklemeniz gerekir fark <xref:System.Net.Http>.  
  
 Projeden indirebilirsiniz [zaman uyumsuz örnek: ince ayar uygulamanız](http://go.microsoft.com/fwlink/?LinkId=255046).  
  
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
                "http://msdn.microsoft.com",  
                "http://msdn.microsoft.com/library/hh290138.aspx",  
                "http://msdn.microsoft.com/library/hh290140.aspx",  
                "http://msdn.microsoft.com/library/dd470362.aspx",  
                "http://msdn.microsoft.com/library/aa578028.aspx",  
                "http://msdn.microsoft.com/library/ms404677.aspx",  
                "http://msdn.microsoft.com/library/ff730837.aspx"  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Zaman uyumsuz programlama ile Async ve Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)  
 [İzlenecek yol: Async kullanarak Web'e erişme ve bekleme (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)  
 [Zaman uyumsuz görevi veya görev (Visual Basic) listesi iptal etme](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md)  
 [Async uygulamanızda (Visual Basic) hassas ayar yapma](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md)  
 [Zaman uyumsuz örnek: İnce uygulamanızı ayarlama](http://go.microsoft.com/fwlink/?LinkId=255046)
