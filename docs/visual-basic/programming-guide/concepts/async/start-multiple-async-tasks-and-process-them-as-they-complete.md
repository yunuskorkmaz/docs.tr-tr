---
title: Birden Çok Zaman Uyumsuz Görev Başlatma ve Görevleri Tamamlandıkça İşleme
ms.date: 07/20/2015
ms.assetid: 57ffb748-af40-4794-bedd-bdb7fea062de
ms.openlocfilehash: b14171196a95e9a6a12f6b13f6f17d3cfe352bce
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266852"
---
# <a name="start-multiple-async-tasks-and-process-them-as-they-complete-visual-basic"></a>Birden Çok Async Görevi Başlatın ve Tamamladıkları Gibi İşleyin (Visual Basic)
Kullanarak, <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>birden çok görevi aynı anda başlatabilir ve başlatıldıkları sırada işlemek yerine tamamlandıkları gibi tek tek işleyebilirsiniz.  
  
 Aşağıdaki örnekte, görev koleksiyonu oluşturmak için bir sorgu kullanır. Her görev, belirli bir web sitesinin içeriğini indirir. Bir while döngüsünün her yinelemesinde, önce `WhenAny` karşıdan yüklemeyi tamamlayan görevler koleksiyonundaki görevi döndürecek beklenen bir çağrı. Bu görev koleksiyondan kaldırılır ve işlenir. Döngü, koleksiyon başka görev içermeyene kadar yinelenir.  
  
> [!NOTE]
> Örnekleri çalıştırmak için Visual Studio 2012 veya daha yeni ve .NET Framework 4.5 veya daha yeni bilgisayarınıza yüklü olması gerekir.  
  
## <a name="downloading-the-example"></a>Örneği İndirme  
 Windows Presentation Foundation (WPF) projesinin tamamını [Async Sample: Fine Tuning Application'dan](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) indirebilir ve ardından aşağıdaki adımları izleyebilirsiniz.  
  
1. İndirdiğiniz dosyayı sıkıştırın ve Visual Studio'yu başlatın.  
  
2. Menü çubuğunda **Dosya**, **Aç**, **Proje/Çözüm'ü**seçin.  
  
3. **Projeyi Aç** iletişim kutusunda, sıkıştırdığınız örnek kodu tutan klasörü açın ve ardından AsyncFineTuningVB için çözüm (.sln) dosyasını açın.  
  
4. **Çözüm Gezgini'nde,** **ProcessTasksAsTheyFinish** projesi için kısayol menüsünü açın ve ardından **StartUp Project olarak ayarla'yı**seçin.  
  
5. Projeyi çalıştırmak için F5 tuşunu seçin.  
  
     Projeyi hata ayıklamadan çalıştırmak için Ctrl+F5 tuşlarını seçin.  
  
6. İndirilen uzunlukların her zaman aynı sırada görünmediğini doğrulamak için projeyi birkaç kez çalıştırın.  
  
 Projeyi indirmek istemiyorsanız, bu konunun sonundaki MainWindow.xaml.vb dosyasını inceleyebilirsiniz.  
  
## <a name="building-the-example"></a>Örnek Oluşturma  
 Bu örnek, [Bir Tamamlandıktan Sonra Kalan Async Görevlerini İptal Etme (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md) olarak geliştirilen ve aynı UI'yi kullanan koda ekler.  
  
 Örneği adım adım oluşturmak için, "Örneği İndirme" bölümündeki yönergeleri izleyin, ancak **StartUp Project**olarak **CancelAfterOneTask'ı** seçin. Bu konudaki değişiklikleri bu `AccessTheWebAsync` projedeki yönteme ekleyin. Değişiklikler yıldız işaretleriyle işaretlenir.  
  
 **CancelAfterOneTask** projesi zaten yürütüldüğünde bir görev koleksiyonu oluşturan bir sorgu içerir. Aşağıdaki `ProcessURLAsync` koddaki her arama <xref:System.Threading.Tasks.Task%601> bir `TResult` tamsayı yıkıntır döndürür.  
  
```vb  
Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =  
    From url In urlList Select ProcessURLAsync(url, client, ct)  
```  
  
 Projenin MainWindow.xaml.vb dosyasında yöntemde `AccessTheWebAsync` aşağıdaki değişiklikleri yapın.  
  
- <xref:System.Linq.Enumerable.ToArray%2A>Yerine uygulayarak <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> sorguyu yürütün  
  
    ```vb  
    Dim downloadTasks As List(Of Task(Of Integer)) = downloadTasksQuery.ToList()  
    ```  
  
- Koleksiyondaki her görev için aşağıdaki adımları gerçekleştiren bir while döngüsü ekleyin.  
  
    1. İndirmeyi tamamlamak `WhenAny` için koleksiyondaki ilk görevi belirlemek için bir çağrı bekler.  
  
        ```vb  
        Dim firstFinishedTask As Task(Of Integer) = Await Task.WhenAny(downloadTasks)  
        ```  
  
    2. Bu görevi koleksiyondan kaldırır.  
  
        ```vb  
        downloadTasks.Remove(firstFinishedTask)  
        ```  
  
    3. Bekliyor `firstFinishedTask`, bir çağrı ile `ProcessURLAsync`döndürülür . `firstFinishedTask` Değişken bir <xref:System.Threading.Tasks.Task%601> tamsayı `TReturn` dır. Görev zaten tamamlandı, ancak aşağıdaki örnekte görüldüğü gibi, indirilen web sitesinin uzunluğunu almak için onu bekliyorsunuz.  
  
        ```vb  
        Dim length = Await firstFinishedTask  
        resultsTextBox.Text &= String.Format(vbCrLf & "Length of the downloaded website:  {0}" & vbCrLf, length)  
        ```  
  
 İndirilen uzunlukların her zaman aynı sırada görünmediğini doğrulamak için projeyi birkaç kez çalıştırmalısınız.  
  
> [!CAUTION]
> Az sayıda `WhenAny` görev içeren sorunları çözmek için örnekte açıklandığı gibi bir döngüde kullanabilirsiniz. Ancak, işlemek için çok sayıda göreviniz varsa, diğer yaklaşımlar daha verimlidir. Daha fazla bilgi ve örnek için, [tamamlandıkça İşleme Görevleri'ne](https://devblogs.microsoft.com/pfxteam/processing-tasks-as-they-complete/)bakın.  
  
## <a name="complete-example"></a>Tam Örnek  
 Aşağıdaki kod, örnek için MainWindow.xaml.vb dosyasının tam metnidir. Yıldız işaretleri, bu örnek için eklenen öğeleri işaretler.  
  
 Için bir başvuru eklemeniz <xref:System.Net.Http>gerektiğine dikkat edin.  
  
 Projeyi [Async Sample: Fine Tuning Application'dan](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)indirebilirsiniz.  
  
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
  
        ' ***Create a query that, when executed, returns a collection of tasks.  
        Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =  
            From url In urlList Select ProcessURLAsync(url, client, ct)  
  
        ' ***Use ToList to execute the query and start the download tasks.
        Dim downloadTasks As List(Of Task(Of Integer)) = downloadTasksQuery.ToList()  
  
        ' ***Add a loop to process the tasks one at a time until none remain.  
        While downloadTasks.Count > 0  
            ' ***Identify the first task that completes.  
            Dim firstFinishedTask As Task(Of Integer) = Await Task.WhenAny(downloadTasks)  
  
            ' ***Remove the selected task from the list so that you don't  
            ' process it more than once.  
            downloadTasks.Remove(firstFinishedTask)  
  
            ' ***Await the first completed task and display the results.  
            Dim length = Await firstFinishedTask  
            resultsTextBox.Text &= String.Format(vbCrLf & "Length of the downloaded website:  {0}" & vbCrLf, length)  
        End While  
  
    End Function  
  
    ' Bundle the processing steps for a website into one async method.  
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
  
' Length of the download:  226093  
' Length of the download:  412588  
' Length of the download:  175490  
' Length of the download:  204890  
' Length of the download:  158855  
' Length of the download:  145790  
' Length of the download:  44908  
' Downloads complete.  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading.Tasks.Task.WhenAny%2A>
- [Async Uygulamanızda İnce Ayar (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md)
- [Async ve Await ile Asynchronous Programlama (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)
- [Async Örnek: Uygulamanızı İyi Ayar](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
