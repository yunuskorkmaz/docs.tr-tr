---
title: 'Nasıl yapılır: Task.WhenAll (Visual Basic) kullanarak zaman uyumsuz izlenecek yolu genişletme'
ms.date: 07/20/2015
ms.assetid: c06d386d-e996-4da9-bf3d-05a3b6c0a258
ms.openlocfilehash: 12d195caa11cd33b4e450e5a57699da4037ed4a2
ms.sourcegitcommit: 3540f614fc94f77ca4ab58df66db2d0f4d52dfee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/01/2018
ms.locfileid: "34696357"
---
# <a name="how-to-extend-the-async-walkthrough-by-using-taskwhenall-visual-basic"></a>Nasıl yapılır: Task.WhenAll (Visual Basic) kullanarak zaman uyumsuz izlenecek yolu genişletme
Zaman uyumsuz çözümde performansını artırabilir [izlenecek yol: Web kullanarak zaman uyumsuz ve bekleme (Visual Basic) tarafından erişme](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md) kullanarak <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> yöntemi. Bu yöntem, zaman uyumsuz olarak görevleri koleksiyonu temsil edilir birden çok zaman uyumsuz işlemleri bekler.  
  
 Web siteleri farklı hızlarda karşıdan kılavuzda fark. Bazen, Web siteleri, kalan tüm indirmeleri gecikmeler çok yavaş biridir. Kılavuzda oluşturacağınız zaman uyumsuz çözümleri çalıştırdığınızda, program kolayca beklemek istemiyorsanız, ancak aynı zamanda tüm indirmeleri başlatmak ve biri, beklemeden devam daha hızlı indirmeler izin vermek için daha iyi bir seçenek olacaktır sonlandırabilirsiniz 's  ertelendi.  
  
 Uyguladığınız `Task.WhenAll` yöntemine görevleri koleksiyonu. Uygulamayı `WhenAll` koleksiyondaki her görev tamamlanana kadar tamamlanmadıysa tek bir görev döndürür. Paralel olarak çalıştırmak için görevler görüntülenir, ancak hiçbir ek iş parçacığı oluşturulur. Herhangi bir sırada görevleri gerçekleştirebilirsiniz.  
  
> [!IMPORTANT]
>  Aşağıdaki yordamlar uzantıları da geliştirilmiş zaman uyumsuz uygulamalara açıklar [izlenecek yol: Web kullanarak zaman uyumsuz ve bekleme (Visual Basic) tarafından erişme](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md). Kılavuzu tamamladıktan veya koddan indirme uygulamaları geliştirmek [Geliştirici kod örnekleri](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).  
>   
>  Örneği çalıştırmak için Visual Studio 2012 veya daha sonra bilgisayarınıza yüklenmiş olmalıdır.  
  
### <a name="to-add-taskwhenall-to-your-geturlcontentsasync-solution"></a>Task.WhenAll GetURLContentsAsync çözümünüze eklemek için  
  
1.  Ekleme `ProcessURLAsync` da geliştirilmiş ilk uygulamaya yöntemi [izlenecek yol: Web kullanarak zaman uyumsuz ve bekleme (Visual Basic) tarafından erişme](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).  
  
    -   Koddan yüklediyseniz [Geliştirici kod örnekleri](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)AsyncWalkthrough projesini açın ve ardından ekleyin `ProcessURLAsync` MainWindow.xaml.vb dosyasına kayıt yapar.  
  
    -   Kod gözden geçirme tamamlayarak geliştirdiyseniz eklemek `ProcessURLAsync` içeren uygulamaya `GetURLContentsAsync` yöntemi. İlk örnek "Tam kod örnekleri gelen izlenecek yolu" bölümünde bu uygulama için MainWindow.xaml.vb dosyasıdır.  
  
     `ProcessURLAsync` Yöntemi birleştirir gövdesini Eylemler `For Each` içinde döngü `SumPageSizesAsync` özgün izlenecek adımları. Metodu zaman uyumsuz olarak bir bayt dizisi olarak belirtilen bir Web sitesi içeriğini indirir ve ardından görüntüler ve bayt dizisi uzunluğunu döndürür.  
  
    ```vb  
    Private Async Function ProcessURLAsync(url As String) As Task(Of Integer)  
  
        Dim byteArray = Await GetURLContentsAsync(url)  
        DisplayResults(url, byteArray)  
        Return byteArray.Length  
    End Function  
    ```  
  
2.  Out yorum yapmak veya silme `For Each` içinde döngü `SumPageSizesAsync`, aşağıdaki kodda gösterildiği gibi.  
  
    ```vb  
    'Dim total = 0  
    'For Each url In urlList  
  
    '    Dim urlContents As Byte() = Await GetURLContentsAsync(url)  
  
    '    ' The previous line abbreviates the following two assignment statements.  
  
    '    ' GetURLContentsAsync returns a task. At completion, the task  
    '    ' produces a byte array.  
    '    'Dim getContentsTask As Task(Of Byte()) = GetURLContentsAsync(url)  
    '    'Dim urlContents As Byte() = Await getContentsTask  
  
    '    DisplayResults(url, urlContents)  
  
    '    ' Update the total.  
    '    total += urlContents.Length  
    'Next  
    ```  
  
3.  Bir görev koleksiyonunu oluşturun. Aşağıdaki kodu tanımlayan bir [sorgu](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) , tarafından çalıştırıldığında <xref:System.Linq.Enumerable.ToArray%2A> yöntemi, her Web sitesi içeriğini indirme görevleri koleksiyonu oluşturur. Sorgu değerlendirildiğinde görevleri başlatılır.  
  
     Yöntemine aşağıdaki kodu ekleyin `SumPageSizesAsync` bildirimi sonra `urlList`.  
  
    ```vb  
    ' Create a query.   
    Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =  
        From url In urlList Select ProcessURLAsync(url)  
  
    ' Use ToArray to execute the query and start the download tasks.  
    Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()  
    ```  
  
4.  Uygulama `Task.WhenAll` görevleri koleksiyonu için `downloadTasks`. `Task.WhenAll` görevlerin koleksiyonundaki tüm görevler tamamlandığında bittikten tek bir görev döndürür.  
  
     Aşağıdaki örnekte, `Await` ifade tek tamamlanmasını bekler, görev `WhenAll` döndürür. Dizisi her tamsayı indirilen bir Web sitesi uzunluğu olduğu, için ifadeyi hesaplar. Aşağıdaki kodu ekleyin `SumPageSizesAsync`, yalnızca önceki adımda eklediğiniz koddan sonra.  
  
    ```vb  
    ' Await the completion of all the running tasks.  
    Dim lengths As Integer() = Await Task.WhenAll(downloadTasks)  
  
    '' The previous line is equivalent to the following two statements.  
    'Dim whenAllTask As Task(Of Integer()) = Task.WhenAll(downloadTasks)  
    'Dim lengths As Integer() = Await whenAllTask  
    ```  
  
5.  Son olarak, <xref:System.Linq.Enumerable.Sum%2A> tüm Web siteleri uzunlukları toplamı hesaplamak için yöntem. Aşağıdaki satırı ekleyin `SumPageSizesAsync`.  
  
    ```vb  
    Dim total = lengths.Sum()  
    ```  
  
### <a name="to-add-taskwhenall-to-the-httpclientgetbytearrayasync-solution"></a>Task.WhenAll HttpClient.GetByteArrayAsync çözüme eklemek için  
  
1.  Aşağıdaki sürümü eklemek `ProcessURLAsync` da geliştirilmiş ikinci uygulamaya [izlenecek yol: Web kullanarak zaman uyumsuz ve bekleme (Visual Basic) tarafından erişme](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).  
  
    -   Koddan yüklediyseniz [Geliştirici kod örnekleri](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)AsyncWalkthrough_HttpClient projesini açın ve ardından ekleyin `ProcessURLAsync` MainWindow.xaml.vb dosyasına kayıt yapar.  
  
    -   Kod gözden geçirme tamamlayarak geliştirdiyseniz eklemek `ProcessURLAsync` kullanan uygulama için `HttpClient.GetByteArrayAsync` yöntemi. Bu uygulama için MainWindow.xaml.vb "Tam kod örnekleri gelen izlenecek yolu" bölümündeki ikinci örneğe dosyasıdır.  
  
     `ProcessURLAsync` Yöntemi birleştirir gövdesini Eylemler `For Each` içinde döngü `SumPageSizesAsync` özgün izlenecek adımları. Metodu zaman uyumsuz olarak bir bayt dizisi olarak belirtilen bir Web sitesi içeriğini indirir ve ardından görüntüler ve bayt dizisi uzunluğunu döndürür.  
  
     Tek farkı `ProcessURLAsync` yöntemidir önceki yordamda kullanımını <xref:System.Net.Http.HttpClient> örneği `client`.  
  
    ```vb  
    Private Async Function ProcessURLAsync(url As String, client As HttpClient) As Task(Of Integer)  
  
        Dim byteArray = Await client.GetByteArrayAsync(url)  
        DisplayResults(url, byteArray)  
        Return byteArray.Length  
    End Function  
    ```  
  
2.  Out yorum yapmak veya silme `For Each` içinde döngü `SumPageSizesAsync`, aşağıdaki kodda gösterildiği gibi.  
  
    ```vb  
    'Dim total = 0   
    'For Each url In urlList   
    '    ' GetByteArrayAsync returns a task. At completion, the task   
    '    ' produces a byte array.   
    '    Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)   
  
    '    ' The following two lines can replace the previous assignment statement.   
    '    'Dim getContentsTask As Task(Of Byte()) = client.GetByteArrayAsync(url)   
    '    'Dim urlContents As Byte() = Await getContentsTask   
  
    '    DisplayResults(url, urlContents)   
  
    '    ' Update the total.   
    '    total += urlContents.Length   
    'Next  
    ```  
  
3.  Tanımlayan bir [sorgu](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) , tarafından çalıştırıldığında <xref:System.Linq.Enumerable.ToArray%2A> yöntemi, her Web sitesi içeriğini indirme görevleri koleksiyonu oluşturur. Sorgu değerlendirildiğinde görevleri başlatılır.  
  
     Yöntemine aşağıdaki kodu ekleyin `SumPageSizesAsync` bildirimi sonra `client` ve `urlList`.  
  
    ```vb  
    ' Create a query.  
    Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =  
        From url In urlList Select ProcessURLAsync(url, client)  
  
    ' Use ToArray to execute the query and start the download tasks.  
    Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()  
    ```  
  
4.  Ardından, uygulama `Task.WhenAll` görevleri koleksiyonu için `downloadTasks`. `Task.WhenAll` görevlerin koleksiyonundaki tüm görevler tamamlandığında bittikten tek bir görev döndürür.  
  
     Aşağıdaki örnekte, `Await` ifade tek tamamlanmasını bekler, görev `WhenAll` döndürür. Tamamlandığında, `Await` dizisi her tamsayı indirilen bir Web sitesi uzunluğu olduğu, için ifadeyi hesaplar. Aşağıdaki kodu ekleyin `SumPageSizesAsync`, yalnızca önceki adımda eklediğiniz koddan sonra.  
  
    ```vb  
    ' Await the completion of all the running tasks.  
    Dim lengths As Integer() = Await Task.WhenAll(downloadTasks)  
  
    '' The previous line is equivalent to the following two statements.  
    'Dim whenAllTask As Task(Of Integer()) = Task.WhenAll(downloadTasks)  
    'Dim lengths As Integer() = Await whenAllTask  
    ```  
  
5.  Son olarak, <xref:System.Linq.Enumerable.Sum%2A> tüm Web siteleri uzunlukları toplamını almak için yöntemi. Aşağıdaki satırı ekleyin `SumPageSizesAsync`.  
  
    ```vb  
    Dim total = lengths.Sum()  
    ```  
  
### <a name="to-test-the-taskwhenall-solutions"></a>Task.WhenAll çözümleri test etmek için  
  
-   Programı çalıştırmak için F5 tuşuna ya da çözüm için seçin ve ardından **Başlat** düğmesi. Çıkış zaman uyumsuz çözümlerinde çıktısını benzemelidir [izlenecek yol: Web kullanarak zaman uyumsuz ve bekleme (Visual Basic) tarafından erişme](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md). Ancak, Web sitelerinin her zaman farklı bir sırada görüntülendiğine dikkat edin.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod kullanan projeye uzantıları gösterir `GetURLContentsAsync` web sunucusundan içerik indirmek için yöntem.  
  
```vb  
' Add the following Imports statements, and add a reference for System.Net.Http.  
Imports System.Net.Http  
Imports System.Net  
Imports System.IO  
  
Class MainWindow  
  
    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click  
  
        resultsTextBox.Clear()  
  
        ' One-step async call.  
        Await SumPageSizesAsync()  
  
        '' Two-step async call.  
        'Dim sumTask As Task = SumPageSizesAsync()  
        'Await sumTask  
  
        resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."  
    End Sub  
  
    Private Async Function SumPageSizesAsync() As Task  
  
        ' Make a list of web addresses.  
        Dim urlList As List(Of String) = SetUpURLList()  
  
        ' Create a query.   
        Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =  
            From url In urlList Select ProcessURLAsync(url)  
  
        ' Use ToArray to execute the query and start the download tasks.  
        Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()  
  
        ' You can do other work here before awaiting.  
  
        ' Await the completion of all the running tasks.  
        Dim lengths As Integer() = Await Task.WhenAll(downloadTasks)  
  
        '' The previous line is equivalent to the following two statements.  
        'Dim whenAllTask As Task(Of Integer()) = Task.WhenAll(downloadTasks)  
        'Dim lengths As Integer() = Await whenAllTask  
  
        Dim total = lengths.Sum()  
  
        'Dim total = 0  
        'For Each url In urlList  
  
        '    Dim urlContents As Byte() = Await GetURLContentsAsync(url)  
  
        '    ' The previous line abbreviates the following two assignment statements.  
  
        '    ' GetURLContentsAsync returns a task. At completion, the task  
        '    ' produces a byte array.  
        '    'Dim getContentsTask As Task(Of Byte()) = GetURLContentsAsync(url)  
        '    'Dim urlContents As Byte() = Await getContentsTask  
  
        '    DisplayResults(url, urlContents)  
  
        '    ' Update the total.  
        '    total += urlContents.Length  
        'NextNext  
  
        ' Display the total count for all of the web addresses.  
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf &  
                                             "Total bytes returned:  {0}" & vbCrLf, total)  
    End Function  
  
    Private Function SetUpURLList() As List(Of String)  
  
        Dim urls = New List(Of String) From  
            {  
                "http://msdn.microsoft.com",  
                "http://msdn.microsoft.com/library/hh290136.aspx",  
                "http://msdn.microsoft.com/library/ee256749.aspx",  
                "http://msdn.microsoft.com/library/hh290138.aspx",  
                "http://msdn.microsoft.com/library/hh290140.aspx",  
                "http://msdn.microsoft.com/library/dd470362.aspx",  
                "http://msdn.microsoft.com/library/aa578028.aspx",  
                "http://msdn.microsoft.com/library/ms404677.aspx",  
                "http://msdn.microsoft.com/library/ff730837.aspx"  
            }  
        Return urls  
    End Function  
  
    ' The actions from the foreach loop are moved to this async method.  
    Private Async Function ProcessURLAsync(url As String) As Task(Of Integer)  
  
        Dim byteArray = Await GetURLContentsAsync(url)  
        DisplayResults(url, byteArray)  
        Return byteArray.Length  
    End Function  
  
    Private Async Function GetURLContentsAsync(url As String) As Task(Of Byte())  
  
        ' The downloaded resource ends up in the variable named content.  
        Dim content = New MemoryStream()  
  
        ' Initialize an HttpWebRequest for the current URL.  
        Dim webReq = CType(WebRequest.Create(url), HttpWebRequest)  
  
        ' Send the request to the Internet resource and wait for  
        ' the response.  
        Using response As WebResponse = Await webReq.GetResponseAsync()  
            ' Get the data stream that is associated with the specified URL.  
            Using responseStream As Stream = response.GetResponseStream()  
                ' Read the bytes in responseStream and copy them to content.    
                ' CopyToAsync returns a Task, not a Task<T>.  
                Await responseStream.CopyToAsync(content)  
            End Using  
        End Using  
  
        ' Return the result as a byte array.  
        Return content.ToArray()  
    End Function  
  
    Private Sub DisplayResults(url As String, content As Byte())  
  
        ' Display the length of each website. The string format   
        ' is designed to be used with a monospaced font, such as  
        ' Lucida Console or Global Monospace.  
        Dim bytes = content.Length  
        ' Strip off the "http://".  
        Dim displayURL = url.Replace("http://", "")  
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)  
    End Sub  
  
End Class  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod bir yöntem projesine uzantıları gösterir `HttpClient.GetByteArrayAsync` web sunucusundan içerik indirmek için.  
  
```vb  
' Add the following Imports statements, and add a reference for System.Net.Http.  
Imports System.Net.Http  
Imports System.Net  
Imports System.IO  
  
Class MainWindow  
  
    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click  
  
        resultsTextBox.Clear()  
  
        '' One-step async call.  
        Await SumPageSizesAsync()  
  
        '' Two-step async call.  
        'Dim sumTask As Task = SumPageSizesAsync()  
        'Await sumTask  
  
        resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."  
    End Sub  
  
    Private Async Function SumPageSizesAsync() As Task  
  
        ' Declare an HttpClient object and increase the buffer size. The  
        ' default buffer size is 65,536.  
        Dim client As HttpClient =  
            New HttpClient() With {.MaxResponseContentBufferSize = 1000000}  
  
        ' Make a list of web addresses.  
        Dim urlList As List(Of String) = SetUpURLList()  
  
        ' Create a query.  
        Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =  
            From url In urlList Select ProcessURLAsync(url, client)  
  
        ' Use ToArray to execute the query and start the download tasks.  
        Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()  
  
        ' You can do other work here before awaiting.  
  
        ' Await the completion of all the running tasks.  
        Dim lengths As Integer() = Await Task.WhenAll(downloadTasks)  
  
        '' The previous line is equivalent to the following two statements.  
        'Dim whenAllTask As Task(Of Integer()) = Task.WhenAll(downloadTasks)  
        'Dim lengths As Integer() = Await whenAllTask  
  
        Dim total = lengths.Sum()  
  
        ''<snippet7>  
        'Dim total = 0  
        'For Each url In urlList  
        '    ' GetByteArrayAsync returns a task. At completion, the task  
        '    ' produces a byte array.  
        '    '<snippet31>  
        '    Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)  
        '    '</snippet31>  
  
        '    ' The following two lines can replace the previous assignment statement.  
        '    'Dim getContentsTask As Task(Of Byte()) = client.GetByteArrayAsync(url)  
        '    'Dim urlContents As Byte() = Await getContentsTask  
  
        '    DisplayResults(url, urlContents)  
  
        '    ' Update the total.  
        '    total += urlContents.Length  
        'NextNext  
  
        ' Display the total count for all of the web addresses.  
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf &  
                                             "Total bytes returned:  {0}" & vbCrLf, total)  
    End Function  
  
    Private Function SetUpURLList() As List(Of String)  
  
        Dim urls = New List(Of String) From  
            {  
                "http://www.msdn.com",  
                "http://msdn.microsoft.com/library/hh290136.aspx",  
                "http://msdn.microsoft.com/library/ee256749.aspx",  
                "http://msdn.microsoft.com/library/hh290138.aspx",  
                "http://msdn.microsoft.com/library/hh290140.aspx",  
                "http://msdn.microsoft.com/library/dd470362.aspx",  
                "http://msdn.microsoft.com/library/aa578028.aspx",  
                "http://msdn.microsoft.com/library/ms404677.aspx",  
                "http://msdn.microsoft.com/library/ff730837.aspx"  
            }  
        Return urls  
    End Function  
  
    Private Async Function ProcessURLAsync(url As String, client As HttpClient) As Task(Of Integer)  
  
        Dim byteArray = Await client.GetByteArrayAsync(url)  
        DisplayResults(url, byteArray)  
        Return byteArray.Length  
    End Function  
  
    Private Sub DisplayResults(url As String, content As Byte())  
  
        ' Display the length of each website. The string format   
        ' is designed to be used with a monospaced font, such as  
        ' Lucida Console or Global Monospace.  
        Dim bytes = content.Length  
        ' Strip off the "http://".  
        Dim displayURL = url.Replace("http://", "")  
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)  
    End Sub  
  
End Class  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>  
 [İzlenecek yol: Async kullanarak Web'e erişme ve bekleme (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
