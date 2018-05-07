---
title: Birden çok zaman uyumsuz görev başlatma ve bunlar (Visual Basic) tamamlandıkça işleme
ms.date: 07/20/2015
ms.assetid: 57ffb748-af40-4794-bedd-bdb7fea062de
ms.openlocfilehash: 54bf83e9812ee048581df4f99901edd23eaec886
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="start-multiple-async-tasks-and-process-them-as-they-complete-visual-basic"></a>Birden çok zaman uyumsuz görev başlatma ve bunlar (Visual Basic) tamamlandıkça işleme
Kullanarak <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>, aynı anda birden çok görevi başlatma ve bunlar tamamlandı yerine bunların başlatılan sırayla işlem onları tek tek işleme.  
  
 Aşağıdaki örnek sorguda görevleri koleksiyonu oluşturmak için kullanır. Her görev, belirtilen bir Web sitesi içeriğini indirir. Her bir süre tekrarında döngü, awaited çağrısına `WhenAny` görev, kendi yükleme ilk bittikten koleksiyondaki görevlerin döndürür. Bu görev koleksiyondan kaldırıldı ve işlenebilir. Daha fazla görev koleksiyon içerene kadar döngü tekrarlar.  
  
> [!NOTE]
>  Örnekleri çalıştırmak için Visual Studio 2012 veya daha yeni ve .NET Framework 4.5 olmalıdır veya daha yeni bilgisayarınızda yüklü.  
  
## <a name="downloading-the-example"></a>Örnek indirme  
 Tam Windows Presentation Foundation (WPF) projeden indirebilirsiniz [zaman uyumsuz örnek: ince ayar uygulamanız](http://go.microsoft.com/fwlink/?LinkId=255046) ve ardından aşağıdaki adımları izleyin.  
  
1.  İndirdiğiniz dosyanın sıkıştırmasını ve Visual Studio'yu başlatın.  
  
2.  Menü çubuğunda seçin **dosya**, **açık**, **proje/çözüm**.  
  
3.  İçinde **Proje Aç** iletişim kutusunda, sıkıştırması örnek kod tutan klasörü açın ve ardından AsyncFineTuningVB için çözüm (.sln) dosyasını açın.  
  
4.  İçinde **Çözüm Gezgini**, kısayol menüsünü açın **ProcessTasksAsTheyFinish** proje ve ardından **başlangıç projesi olarak ayarla**.  
  
5.  Projeyi çalıştırmak için F5 tuşuna seçin.  
  
     Hata ayıklama olmadan projeyi çalıştırmak için Ctrl + F5 anahtarları'i seçin.  
  
6.  Proje indirilen uzunlukları her zaman aynı sırada görünmüyor doğrulamak için birkaç kez çalıştırın.  
  
 Projenizi indirin istemiyorsanız, bu konunun sonundaki MainWindow.xaml.vb dosyasını gözden geçirebilirsiniz.  
  
## <a name="building-the-example"></a>Örnek oluşturma  
 Bu örnek da geliştirilmiş kod ekler [bir tamamlandı (Visual Basic) sonra geri kalan zaman uyumsuz görevleri iptal](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md) ve aynı kullanıcı arabirimini kullanır.  
  
 Örnek oluşturmak için kendiniz, adım adım "örnek indirme" bölümündeki yönergeleri izleyin, ancak seçin **CancelAfterOneTask** olarak **başlangıç projesi**. İçin bu konudaki değişiklikleri eklemek `AccessTheWebAsync` projedeki yöntemi. Değişiklikler yıldız işaretiyle işaretlenir.  
  
 **CancelAfterOneTask** proje zaten bir sorgu içeriyor, çalıştırıldığında, görevleri koleksiyonu oluşturur. Her çağrı `ProcessURLAsync` aşağıdaki kodda döndüren bir <xref:System.Threading.Tasks.Task%601> burada `TResult` bir tamsayıdır.  
  
```vb  
Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =  
    From url In urlList Select ProcessURLAsync(url, client, ct)  
```  
  
 Proje MainWindow.xaml.vb dosyasında aşağıdaki değişiklikleri `AccessTheWebAsync` yöntemi.  
  
-   Uygulayarak sorguyu yürütmek <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> yerine <xref:System.Linq.Enumerable.ToArray%2A>.  
  
    ```vb  
    Dim downloadTasks As List(Of Task(Of Integer)) = downloadTasksQuery.ToList()  
    ```  
  
-   Biraz eklemek koleksiyondaki her görev için aşağıdaki adımları gerçekleştirir döngü.  
  
    1.  Çağrı bekler `WhenAny` kendi indirme tamamlamak için koleksiyondaki ilk görevi tanımlamak için.  
  
        ```vb  
        Dim firstFinishedTask As Task(Of Integer) = Await Task.WhenAny(downloadTasks)  
        ```  
  
    2.  Bu görev koleksiyondan kaldırır.  
  
        ```vb  
        downloadTasks.Remove(firstFinishedTask)  
        ```  
  
    3.  Bekler `firstFinishedTask`, bir çağrı tarafından döndürülen `ProcessURLAsync`. `firstFinishedTask` Değişkeni, bir <xref:System.Threading.Tasks.Task%601> burada `TReturn` bir tamsayıdır. Görev zaten tamamlandı, ancak uzunluğu indirilen Web sitesi, aşağıdaki örnekte gösterildiği gibi almak bekler.  
  
        ```vb  
        Dim length = Await firstFinishedTask  
        resultsTextBox.Text &= String.Format(vbCrLf & "Length of the downloaded website:  {0}" & vbCrLf, length)  
        ```  
  
 Proje indirilen uzunlukları her zaman aynı sırada görünmüyor doğrulamak için birkaç kez çalıştırmanız gerekir.  
  
> [!CAUTION]
>  Kullanabileceğiniz `WhenAny` küçük birkaç görev ile ilgili sorunları çözmek için örnekte açıklandığı gibi bir Döngüdeki. Ancak, diğer yaklaşımlar görevler işlemek için çok sayıda varsa daha verimlidir. Daha fazla bilgi ve örnekler için bkz: [işleme görevleri bunlar tam olarak](http://go.microsoft.com/fwlink/?LinkId=260810).  
  
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
  
' Length of the download:  226093  
' Length of the download:  412588  
' Length of the download:  175490  
' Length of the download:  204890  
' Length of the download:  158855  
' Length of the download:  145790  
' Length of the download:  44908  
' Downloads complete.  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Threading.Tasks.Task.WhenAny%2A>  
 [Async uygulamanızda (Visual Basic) hassas ayar yapma](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md)  
 [Zaman uyumsuz programlama ile Async ve Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)  
 [Zaman uyumsuz örnek: İnce uygulamanızı ayarlama](http://go.microsoft.com/fwlink/?LinkId=255046)
