---
title: Tam (Visual Basic) biridir sonra geri kalan zaman uyumsuz görevleri iptal etme
ms.date: 07/20/2015
ms.assetid: c928b5a1-622f-4441-8baf-adca1dde197f
ms.openlocfilehash: 5dab0c4aa14710fe78d2473675aea8b8c8bb73b9
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43874803"
---
# <a name="cancel-remaining-async-tasks-after-one-is-complete-visual-basic"></a>Tam (Visual Basic) biridir sonra geri kalan zaman uyumsuz görevleri iptal etme
Kullanarak <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> yöntemi ile birlikte bir <xref:System.Threading.CancellationToken>, bir görev tamamlandığında kalan tüm görevleri iptal edebilirsiniz. `WhenAny` Yöntemi bir görev koleksiyonu olan bir bağımsız değişken alır. Bu yöntem tüm görevleri başlatır ve tek bir görev döndürür. Koleksiyondaki herhangi bir görev tamamlandığında tek bir görev tamamlanmıştır.  
  
 Bu örnek ile birlikte bir iptal belirteci kullanmayı gösteren `WhenAny` bitirilecek ilk göreve görevleri koleksiyonundan tamamlanması ve kalan görevleri iptal etmek için tutacak. Her görev bir Web sitesinin içeriklerini karşıdan yükler. Bu örnek, tamamlanacak ilk yüklemenin içeriğinin uzunluğunu görüntüler ve diğer yüklemeleri iptal eder.  
  
> [!NOTE]
>  Yeni bilgisayarınızda yüklü veya örnekleri çalıştırmak için Visual Studio 2012 veya daha yeni ve .NET Framework 4.5 yüklü olmalıdır.  
  
## <a name="downloading-the-example"></a>Örneği indirme  
 Tüm Windows Presentation Foundation (WPF) projeden indirebileceğiniz [zaman uyumsuz örneği: ince uygulamanıza](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) ve sonra aşağıdaki adımları izleyin.  
  
1.  İndirdiğiniz dosyanın sıkıştırmasını açın ve sonra Visual Studio'yu başlatın.  
  
2.  Menü çubuğunda, **dosya**, **açık**, **proje/çözüm**.  
  
3.  İçinde **Proje Aç** iletişim kutusunda, açtığınız örnek kodu barındıran klasörü açın ve ardından AsyncFineTuningVB için çözüm (.sln) dosyasını açın.  
  
4.  İçinde **Çözüm Gezgini**, kısayol menüsünü açın **CancelAfterOneTask** proje ve ardından **başlangıç projesi olarak ayarla**.  
  
5.  Projeyi çalıştırmak için F5 tuşuna basın.  
  
     Projeyi hata ayıklama olmadan çalıştırmak için Ctrl + F5 tuşlarını seçin.  
  
6.  Programın farklı yüklemeleri ilk son doğrulamak için birkaç kez çalıştırın.  
  
 Projeyi indirmek istemiyorsanız, bu konunun sonunda MainWindow.xaml.vb dosyasını gözden geçirebilirsiniz.  
  
## <a name="building-the-example"></a>Örneği oluşturma  
 Bu konudaki örnek içinde geliştirilen projeye ekler [zaman uyumsuz bir görev veya görevleri listeleyin iptal](https://msdn.microsoft.com/library/d6e4e801-df64-4705-98fc-df725a577fb0) Görevler listesini iptal etme. Örnekte aynı Arabirim kullanılmaktadır, ancak **iptal** düğmesi açıkça kullanılmaz.  
  
 Örneği oluşturmak için kendinize, adım adım "Örneği indirme" bölümündeki yönergeleri izleyin, ancak seçin **CancelAListOfTasks** olarak **başlangıç projesi**. Bu konuda, değişiklikleri bu projeye ekleyin.  
  
 MainWindow.xaml.vb dosyasındaki **CancelAListOfTasks** proje, her Web sitesi için işlenen adımları döngüden taşıyarak geçişi başlatın `AccessTheWebAsync` aşağıdaki zaman uyumsuz yönteme.  
  
```vb  
' ***Bundle the processing steps for a website into one async method.  
Async Function ProcessURLAsync(url As String, client As HttpClient, ct As CancellationToken) As Task(Of Integer)  
  
    ' GetAsync returns a Task(Of HttpResponseMessage).   
    Dim response As HttpResponseMessage = Await client.GetAsync(url, ct)  
  
    ' Retrieve the website contents from the HttpResponseMessage.  
    Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()  
  
    Return urlContents.Length  
End Function  
```  
  
 İçinde `AccessTheWebAsync`, bu örnekte sorgu, <xref:System.Linq.Enumerable.ToArray%2A> yöntemi ve `WhenAny` oluşturmak ve bir dizi görev başlamak için yöntemi. Uygulamayı `WhenAny` dizisi için tek bir görev, bekletildiğinde döndürür dizideki görevlerin tamamlanmasına ulaşmak için ilk görev değerlendirir.  
  
 Aşağıdaki değişiklikleri yapın `AccessTheWebAsync`. Yıldız işaretleri kod dosyasındaki değişiklikleri işaretler.  
  
1.  Açıklama satırı yapın veya döngü silin.  
  
2.  Yürütüldüğünde, bir sorgu, oluşturun bir genel görev koleksiyonu oluşturur. Her çağrı `ProcessURLAsync` döndürür bir <xref:System.Threading.Tasks.Task%601> burada `TResult` bir tamsayıdır.  
  
    ```vb  
    ' ***Create a query that, when executed, returns a collection of tasks.  
    Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =  
        From url In urlList Select ProcessURLAsync(url, client, ct)  
    ```  
  
3.  Çağrı `ToArray` sorguyu ve görevleri başlatın. Uygulamayı `WhenAny` sonraki adımda yöntemi ve sorguyu kullanmadan başlangıç görevleri `ToArray`, ancak diğer yöntemler bunu yapmayabilir. En güvenli yöntem sorgu yürütmesini açıkça zorla sağlamaktır.  
  
    ```vb  
    ' ***Use ToArray to execute the query and start the download tasks.   
    Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()  
    ```  
  
4.  Çağrı `WhenAny` üzerinde bir görev koleksiyonu. `WhenAny` döndürür bir `Task(Of Task(Of Integer))` veya `Task<Task<int>>`.  Diğer bir deyişle, `WhenAny` değerlendiren bir görev için tek bir döndüren `Task(Of Integer)` veya `Task<int>` beklendiği zaman. Bu tek görev tamamlamak için koleksiyondaki ilk görevdir. İlk önce Tamamlanan görevin atandığı `firstFinishedTask`. Türünü `firstFinishedTask` olduğu <xref:System.Threading.Tasks.Task%601> burada `TResult` dönüş türü olan bir tamsayı çünkü `ProcessURLAsync`.  
  
```vb  
' ***Call WhenAny and then await the result. The task that finishes   
' first is assigned to firstFinishedTask.  
Dim firstFinishedTask As Task(Of Integer) = Await Task.WhenAny(downloadTasks)  
```  
  
5.  Bu örnekte, önce sona eren yalnızca görevle ilgilendiniz. Bu nedenle, <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> kalan görevleri iptal etmek için.  
  
```vb  
' ***Cancel the rest of the downloads. You just want the first one.  
cts.Cancel()  
```  
  
6.  Son olarak, await `firstFinishedTask` karşıdan yüklenen içeriğin uzunluğunu almak için.  
  
```vb  
Dim length = Await firstFinishedTask  
resultsTextBox.Text &= String.Format(vbCrLf & "Length of the downloaded website:  {0}" & vbCrLf, length)  
```  
  
 Programın farklı yüklemeleri ilk son doğrulamak için birkaç kez çalıştırın.  
  
## <a name="complete-example"></a>Tam Örnek  
 Aşağıdaki kod örneği için tam MainWindow.xaml.vb veya MainWindow.xaml.cs dosyasıdır. Yıldız işaretleri, bu örnek için eklenen öğeleri işaretler.  
  
 İçin bir başvuru eklemeniz gerektiğini unutmayın <xref:System.Net.Http>.  
  
 Projeden indirebileceğiniz [zaman uyumsuz örneği: ince uygulamanıza](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).  
  
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
            Await AccessTheWebAsync(cts.Token)  
            resultsTextBox.Text &= vbCrLf & "Download complete."  
  
        Catch ex As OperationCanceledException  
            resultsTextBox.Text &= vbCrLf & "Download canceled." & vbCrLf  
  
        Catch ex As Exception  
            resultsTextBox.Text &= vbCrLf & "Download failed." & vbCrLf  
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
  
        '' Comment out or delete the loop.  
        ''For Each url In urlList  
        ''    ' GetAsync returns a Task(Of HttpResponseMessage).   
        ''    ' Argument ct carries the message if the Cancel button is chosen.   
        ''    ' Note that the Cancel button can cancel all remaining downloads.  
        ''    Dim response As HttpResponseMessage = Await client.GetAsync(url, ct)  
  
        ''    ' Retrieve the website contents from the HttpResponseMessage.  
        ''    Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()  
  
        ''    resultsTextBox.Text &=  
        ''        String.Format(vbCrLf & "Length of the downloaded string: {0}." & vbCrLf, urlContents.Length)  
        ''Next  
  
        ' ***Create a query that, when executed, returns a collection of tasks.  
        Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =  
            From url In urlList Select ProcessURLAsync(url, client, ct)  
  
        ' ***Use ToArray to execute the query and start the download tasks.   
        Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()  
  
        ' ***Call WhenAny and then await the result. The task that finishes   
        ' first is assigned to firstFinishedTask.  
        Dim firstFinishedTask As Task(Of Integer) = Await Task.WhenAny(downloadTasks)  
  
        ' ***Cancel the rest of the downloads. You just want the first one.  
        cts.Cancel()  
  
        ' ***Await the first completed task and display the results  
        ' Run the program several times to demonstrate that different  
        ' websites can finish first.  
        Dim length = Await firstFinishedTask  
        resultsTextBox.Text &= String.Format(vbCrLf & "Length of the downloaded website:  {0}" & vbCrLf, length)  
    End Function  
  
    ' ***Bundle the processing steps for a website into one async method.  
    Async Function ProcessURLAsync(url As String, client As HttpClient, ct As CancellationToken) As Task(Of Integer)  
  
        ' GetAsync returns a Task(Of HttpResponseMessage).   
        Dim response As HttpResponseMessage = Await client.GetAsync(url, ct)  
  
        ' Retrieve the website contents from the HttpResponseMessage.  
        Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()  
  
        Return urlContents.Length  
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
  
' Length of the downloaded website:  158856  
  
' Download complete.  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Threading.Tasks.Task.WhenAny%2A>  
 [(Visual Basic) Async uygulamanızda hassas ayar yapma](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md)  
 [Zaman uyumsuz programlama ile Async ve Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)  
 [Zaman uyumsuz örneği: Uygulamanıza ince](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
