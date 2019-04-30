---
title: 'Nasıl yapılır: (Visual Basic) Task.WhenAll kullanarak zaman uyumsuz izlenecek yolu genişletme'
ms.date: 07/20/2015
ms.assetid: c06d386d-e996-4da9-bf3d-05a3b6c0a258
ms.openlocfilehash: 7ad2d9cdd85a7bdb67bbf091a38274fd20e5a66f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61756513"
---
# <a name="how-to-extend-the-async-walkthrough-by-using-taskwhenall-visual-basic"></a>Nasıl yapılır: (Visual Basic) Task.WhenAll kullanarak zaman uyumsuz izlenecek yolu genişletme
İçinde zaman uyumsuz çözümün performansını artırabilirsiniz [izlenecek yol: Web kullanarak Async ve Await (Visual Basic) tarafından erişim](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md) kullanarak <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> yöntemi. Bu yöntem, zaman uyumsuz olarak görevleri topluluğu temsil edilen birden çok zaman uyumsuz işlemler bekler.  
  
 Web sitelerinin indirme hızlarının farklı izlenecek yolda etmiş olabilirsiniz. Bazen, Web siteleri, kalan tüm indirmeleri geciktirir çok yavaş biridir. Anlatımda oluşturduğunuz zaman uyumsuz çözümleri çalıştırdığınızda, program kolayca beklemek istemiyorsanız, ancak tüm indirmeleri aynı anda başlatmak ve devam etmek için beklemenize gerek kalmadan daha hızlı indirmeler izin vermek için daha iyi bir seçenek olacaktır sona erdirebilirsiniz ait  ertelendi.  
  
 Uyguladığınız `Task.WhenAll` yöntemi için bir görev koleksiyonu. Uygulamayı `WhenAll` koleksiyondaki her görev tamamlanıncaya kadar tam olmayan tek bir görev döndürür. Görevler paralel olarak çalışır gibigörünür, ancak hiçbir ek iş parçacığı oluşturulmaz. Görevler herhangi bir sırada tamamlayabilir.  
  
> [!IMPORTANT]
>  Aşağıdaki yordamlar içinde geliştirilen zaman uyumsuz uygulamaların uzantılarını açıklamaktadır [izlenecek yol: Zaman uyumsuz kullanarak Web'e erişme ve Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md). İzlenecek yolu tamamlayarak veya kodu indiriliyor tarafından uygulamalar geliştirebilirsiniz [geliştirici kodu örnekleri](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).  
>   
>  Örneği çalıştırmak için Visual Studio 2012 olmalıdır veya üzeri yüklü.  
  
### <a name="to-add-taskwhenall-to-your-geturlcontentsasync-solution"></a>GetURLContentsAsync çözümünüze Task.WhenAll eklemek için  
  
1. Ekleme `ProcessURLAsync` yöntemi içinde geliştirilen ilk uygulamaya [izlenecek yol: Zaman uyumsuz kullanarak Web'e erişme ve Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).  
  
    - Koddan indirdiyseniz [geliştirici kodu örnekleri](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f), AsyncWalkthrough projesini açın ve ardından eklemek `ProcessURLAsync` MainWindow.xaml.vb dosyasına.  
  
    - İzlenecek yolu tamamlayarak kodu geliştirdiyseniz, ekleme `ProcessURLAsync` içeren uygulamaya `GetURLContentsAsync` yöntemi. Bu uygulama için MainWindow.xaml.vb dosyası "Tam kod örnekleri" izlenecek yoldan"bölümündeki ilk örnektir.  
  
     `ProcessURLAsync` Yöntem gövdesindeki eylemleri birleştirir `For Each` içinde döngü `SumPageSizesAsync` özgün izlenecek yolda. Yöntemi zaman uyumsuz olarak bir bayt dizisi olarak belirtilen bir Web sitesinin içeriklerini karşıdan yükler ve ardından görüntüler ve bayt dizisinin uzunluğunu döndürür.  
  
    ```vb  
    Private Async Function ProcessURLAsync(url As String) As Task(Of Integer)  
  
        Dim byteArray = Await GetURLContentsAsync(url)  
        DisplayResults(url, byteArray)  
        Return byteArray.Length  
    End Function  
    ```  
  
2. Açıklama satırı yapın veya silin `For Each` içinde döngü `SumPageSizesAsync`aşağıdaki kodda gösterildiği gibi.  
  
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
  
3. Bir görev koleksiyonu oluşturun. Aşağıdaki kodu tanımlayan bir [sorgu](../../../../visual-basic/programming-guide/concepts/linq/index.md) , tarafından yürütüldüğünde <xref:System.Linq.Enumerable.ToArray%2A> yöntemi, her bir Web sitesinin içeriklerini indiren bir görev koleksiyonunu oluşturur. Sorgu çalışırken görevler başlatılır.  
  
     Yöntemine aşağıdaki kodu ekleyin `SumPageSizesAsync` bildiriminin `urlList`.  
  
    ```vb  
    ' Create a query.   
    Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =  
        From url In urlList Select ProcessURLAsync(url)  
  
    ' Use ToArray to execute the query and start the download tasks.  
    Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()  
    ```  
  
4. Uygulama `Task.WhenAll` görevler koleksiyonuna `downloadTasks`. `Task.WhenAll` Görevler koleksiyondaki tüm görevler tamamlandığında sona tek bir görev döndürür.  
  
     Aşağıdaki örnekte, `Await` ifade tek tamalanmasını görevin `WhenAll` döndürür. İfade bir her tamsayının indirilen bir Web sitesinin uzunluğu olduğu bir tamsayılar dizisi olarak değerlendirilir. Aşağıdaki kodu ekleyin `SumPageSizesAsync`, yalnızca önceki adımda eklediğiniz koddan sonra.  
  
    ```vb  
    ' Await the completion of all the running tasks.  
    Dim lengths As Integer() = Await Task.WhenAll(downloadTasks)  
  
    '' The previous line is equivalent to the following two statements.  
    'Dim whenAllTask As Task(Of Integer()) = Task.WhenAll(downloadTasks)  
    'Dim lengths As Integer() = Await whenAllTask  
    ```  
  
5. Son olarak, <xref:System.Linq.Enumerable.Sum%2A> tüm Web sitelerinin uzunluklarının toplamını hesaplamak için yöntemi. Aşağıdaki satırı ekleyin `SumPageSizesAsync`.  
  
    ```vb  
    Dim total = lengths.Sum()  
    ```  
  
### <a name="to-add-taskwhenall-to-the-httpclientgetbytearrayasync-solution"></a>HttpClient.GetByteArrayAsync çözümüne Task.WhenAll eklemek için  
  
1. Aşağıdaki sürümü ekleme `ProcessURLAsync` içinde geliştirilen ikinci uygulamaya [izlenecek yol: Zaman uyumsuz kullanarak Web'e erişme ve Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).  
  
    - Koddan indirdiyseniz [geliştirici kodu örnekleri](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f), AsyncWalkthrough_HttpClient projesini açın ve ardından eklemek `ProcessURLAsync` MainWindow.xaml.vb dosyasına.  
  
    - İzlenecek yolu tamamlayarak kodu geliştirdiyseniz, ekleme `ProcessURLAsync` kullanan uygulamaya `HttpClient.GetByteArrayAsync` yöntemi. Bu uygulama için MainWindow.xaml.vb dosyası "Tam kod örnekleri" izlenecek yoldan"bölümündeki ikinci örnektir.  
  
     `ProcessURLAsync` Yöntem gövdesindeki eylemleri birleştirir `For Each` içinde döngü `SumPageSizesAsync` özgün izlenecek yolda. Yöntemi zaman uyumsuz olarak bir bayt dizisi olarak belirtilen bir Web sitesinin içeriklerini karşıdan yükler ve ardından görüntüler ve bayt dizisinin uzunluğunu döndürür.  
  
     Tek farkı `ProcessURLAsync` yöntemdir önceki yordamda kullanımını <xref:System.Net.Http.HttpClient> örneği `client`.  
  
    ```vb  
    Private Async Function ProcessURLAsync(url As String, client As HttpClient) As Task(Of Integer)  
  
        Dim byteArray = Await client.GetByteArrayAsync(url)  
        DisplayResults(url, byteArray)  
        Return byteArray.Length  
    End Function  
    ```  
  
2. Açıklama satırı yapın veya silin `For Each` içinde döngü `SumPageSizesAsync`aşağıdaki kodda gösterildiği gibi.  
  
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
  
3. Tanımlayan bir [sorgu](../../../../visual-basic/programming-guide/concepts/linq/index.md) , tarafından yürütüldüğünde <xref:System.Linq.Enumerable.ToArray%2A> yöntemi, her bir Web sitesinin içeriklerini indiren bir görev koleksiyonunu oluşturur. Sorgu çalışırken görevler başlatılır.  
  
     Yöntemine aşağıdaki kodu ekleyin `SumPageSizesAsync` bildiriminin `client` ve `urlList`.  
  
    ```vb  
    ' Create a query.  
    Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =  
        From url In urlList Select ProcessURLAsync(url, client)  
  
    ' Use ToArray to execute the query and start the download tasks.  
    Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()  
    ```  
  
4. Ardından, uygulama `Task.WhenAll` görevler koleksiyonuna `downloadTasks`. `Task.WhenAll` Görevler koleksiyondaki tüm görevler tamamlandığında sona tek bir görev döndürür.  
  
     Aşağıdaki örnekte, `Await` ifade tek tamalanmasını görevin `WhenAll` döndürür. İşlem tamamlandığında `Await` ifade bir her tamsayının indirilen bir Web sitesinin uzunluğu olduğu bir tamsayılar dizisi olarak değerlendirilir. Aşağıdaki kodu ekleyin `SumPageSizesAsync`, yalnızca önceki adımda eklediğiniz koddan sonra.  
  
    ```vb  
    ' Await the completion of all the running tasks.  
    Dim lengths As Integer() = Await Task.WhenAll(downloadTasks)  
  
    '' The previous line is equivalent to the following two statements.  
    'Dim whenAllTask As Task(Of Integer()) = Task.WhenAll(downloadTasks)  
    'Dim lengths As Integer() = Await whenAllTask  
    ```  
  
5. Son olarak, <xref:System.Linq.Enumerable.Sum%2A> tüm Web sitelerinin uzunluklarının toplamını almak için yöntemi. Aşağıdaki satırı ekleyin `SumPageSizesAsync`.  
  
    ```vb  
    Dim total = lengths.Sum()  
    ```  
  
### <a name="to-test-the-taskwhenall-solutions"></a>Task.WhenAll çözümlerini test etmek için  
  
- Her çözüm için programı çalıştırmak için F5 tuşuna basın ve ardından **Başlat** düğmesi. Zaman uyumsuz çözümleri çıkışı çıktıya benzemelidir [izlenecek yol: Zaman uyumsuz kullanarak Web'e erişme ve Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md). Ancak, Web sitelerinin her seferinde farklı bir sırada görüntülendiğine dikkat edin.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kodu kullanan proje uzantılarını göstermektedir `GetURLContentsAsync` içeriği Web'den yüklemek için yöntemi.  
  
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
                "https://msdn.microsoft.com",  
                "https://msdn.microsoft.com/library/hh290136.aspx",  
                "https://msdn.microsoft.com/library/ee256749.aspx",  
                "https://msdn.microsoft.com/library/hh290138.aspx",  
                "https://msdn.microsoft.com/library/hh290140.aspx",  
                "https://msdn.microsoft.com/library/dd470362.aspx",  
                "https://msdn.microsoft.com/library/aa578028.aspx",  
                "https://msdn.microsoft.com/library/ms404677.aspx",  
                "https://msdn.microsoft.com/library/ff730837.aspx"  
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
        ' Strip off the "https://".  
        Dim displayURL = url.Replace("https://", "")  
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)  
    End Sub  
  
End Class  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod yöntemini kullanan proje uzantılarını göstermektedir `HttpClient.GetByteArrayAsync` içeriği Web'den yüklemek için.  
  
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
                "https://www.msdn.com",  
                "https://msdn.microsoft.com/library/hh290136.aspx",  
                "https://msdn.microsoft.com/library/ee256749.aspx",  
                "https://msdn.microsoft.com/library/hh290138.aspx",  
                "https://msdn.microsoft.com/library/hh290140.aspx",  
                "https://msdn.microsoft.com/library/dd470362.aspx",  
                "https://msdn.microsoft.com/library/aa578028.aspx",  
                "https://msdn.microsoft.com/library/ms404677.aspx",  
                "https://msdn.microsoft.com/library/ff730837.aspx"  
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
        ' Strip off the "https://".  
        Dim displayURL = url.Replace("https://", "")  
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)  
    End Sub  
  
End Class  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>
- [İzlenecek yol: Zaman uyumsuz kullanarak Web'e erişme ve Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
