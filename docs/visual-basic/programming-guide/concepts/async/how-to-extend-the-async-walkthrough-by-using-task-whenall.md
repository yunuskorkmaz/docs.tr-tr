---
title: 'Nasıl yapılır: Task.WhenAll Kullanarak Zaman Uyumsuz İzlenecek Yolu Genişletme'
ms.date: 07/20/2015
ms.assetid: c06d386d-e996-4da9-bf3d-05a3b6c0a258
ms.openlocfilehash: 6df29a90ff0012564c6d966c8156434d25cacdb1
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74354240"
---
# <a name="how-to-extend-the-async-walkthrough-by-using-taskwhenall-visual-basic"></a>Nasıl yapılır: Task. WhenAll kullanarak zaman uyumsuz Izlenecek yolu genişletme (Visual Basic)

Zaman uyumsuz çözümün performansını şu şekilde artırabilirsiniz: <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> metodunu kullanarak [, Async ve await (Visual Basic) kullanarak Web 'e erişme](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md) . Bu yöntem, bir görev koleksiyonu olarak temsil edilen birden çok zaman uyumsuz işlemi zaman uyumsuz olarak bekler.

Gözden geçirmede, Web sitelerinin farklı oranlarda indirdiğini fark etmiş olabilirsiniz. Bazen Web sitelerinden biri çok yavaş olduğundan, kalan tüm indirmeleri gecikmekte. Yönergede oluşturduğunuz zaman uyumsuz çözümleri çalıştırdığınızda, beklemek istemiyorsanız programı kolayca sonlandırabilir, ancak daha iyi bir seçenek, tüm indirmeleri aynı anda başlatıp daha hızlı karşıdan yüklemelerin devam etmesini sağlamak zorunda kalmadan devam edebilir.  gerekebilecek.

`Task.WhenAll` yöntemini bir görev koleksiyonuna uygularsınız. `WhenAll` uygulaması, koleksiyondaki her görev tamamlanana kadar tamamlanmamış tek bir görev döndürür. Görevler paralel olarak çalışır, ancak ek iş parçacığı oluşturulmaz. Görevler herhangi bir sırada tamamlanabilir.

> [!IMPORTANT]
> Aşağıdaki yordamlarda, [Izlenecek yol: Async ve await (Visual Basic) kullanılarak Web 'e erişim](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)için geliştirilmiş zaman uyumsuz uygulamalara yönelik uzantılar açıklanır. Uygulamayı, izlenecek yolu tamamlayarak veya kodu [Geliştirici kodu örneklerinden](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)indirerek geliştirebilirsiniz.
>
> Örneği çalıştırmak için bilgisayarınızda Visual Studio 2012 veya sonraki bir sürümünün yüklü olması gerekir.

### <a name="to-add-taskwhenall-to-your-geturlcontentsasync-solution"></a>GetURLContentsAsync çözümünüze Task. WhenAll eklemek için

1. `ProcessURLAsync` yöntemini, [Izlenecek yol: Async ve await (Visual Basic) kullanarak Web 'e erişme](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)bölümünde geliştirilen ilk uygulamaya ekleyin.

    - Kodu [Geliştirici kodu örneklerinden](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)Indirdiyseniz asyncwalkthrough projesini açın ve sonra MainWindow. xaml. vb dosyasına `ProcessURLAsync` ekleyin.

    - İzlenecek yolu tamamlayarak kodu geliştirdiyseniz, `GetURLContentsAsync` yöntemini içeren uygulamaya `ProcessURLAsync` ekleyin. Bu uygulama için MainWindow. xaml. vb dosyası, "Izlenecek yol içindeki tüm kod örnekleri" bölümünde yer aldığı ilk örnektir.

     `ProcessURLAsync` yöntemi, özgün izlenecek yolda `SumPageSizesAsync` `For Each` döngüsünün gövdesinde eylemleri birleştirir. Yöntemi, belirtilen bir Web sitesinin içeriğini bir bayt dizisi olarak zaman uyumsuz olarak indirir ve bayt dizisinin uzunluğunu görüntüler ve döndürür.

    ```vb
    Private Async Function ProcessURLAsync(url As String) As Task(Of Integer)

        Dim byteArray = Await GetURLContentsAsync(url)
        DisplayResults(url, byteArray)
        Return byteArray.Length
    End Function
    ```

2. Aşağıdaki kodun gösterdiği gibi, `SumPageSizesAsync``For Each` döngüsünü açıklama veya silme.

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

3. Bir görev koleksiyonu oluşturun. Aşağıdaki kod, <xref:System.Linq.Enumerable.ToArray%2A> yöntemi tarafından yürütüldüğünde, her bir Web sitesinin içeriğini yükleyen bir görev koleksiyonu oluşturan bir [sorgu](../../../../visual-basic/programming-guide/concepts/linq/index.md) tanımlar. Sorgu değerlendirildiğinde görevler başlatılır.

     `urlList`bildiriminden sonra `SumPageSizesAsync` aşağıdaki kodu yöntemine ekleyin.

    ```vb
    ' Create a query.
    Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =
        From url In urlList Select ProcessURLAsync(url)

    ' Use ToArray to execute the query and start the download tasks.
    Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()
    ```

4. `Task.WhenAll`, `downloadTasks`görevleri koleksiyonuna uygulayın. `Task.WhenAll`, görevler koleksiyonundaki tüm görevler tamamlandığında tamamlanmış tek bir görev döndürür.

     Aşağıdaki örnekte `Await` ifadesi, `WhenAll` döndüren tek görevin tamamlanmasını bekler. İfade, her tamsayının indirilen bir Web sitesinin uzunluğu olduğu bir tamsayılar dizisi olarak değerlendirilir. Önceki adımda eklediğiniz koddan hemen sonra `SumPageSizesAsync`aşağıdaki kodu ekleyin.

    ```vb
    ' Await the completion of all the running tasks.
    Dim lengths As Integer() = Await Task.WhenAll(downloadTasks)

    '' The previous line is equivalent to the following two statements.
    'Dim whenAllTask As Task(Of Integer()) = Task.WhenAll(downloadTasks)
    'Dim lengths As Integer() = Await whenAllTask
    ```

5. Son olarak, tüm Web sitelerinin uzunluklarının toplamını hesaplamak için <xref:System.Linq.Enumerable.Sum%2A> yöntemini kullanın. `SumPageSizesAsync`için aşağıdaki satırı ekleyin.

    ```vb
    Dim total = lengths.Sum()
    ```

### <a name="to-add-taskwhenall-to-the-httpclientgetbytearrayasync-solution"></a>HttpClient. GetByteArrayAsync çözümüne Task. WhenAll eklemek için

1. Aşağıdaki `ProcessURLAsync` sürümünü, [Izlenecek yol: Async ve await (Visual Basic) kullanarak Web 'e erişme](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)bölümünde geliştirilen ikinci uygulamaya ekleyin.

    - Kodu [Geliştirici kodu örneklerinden](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)indirdiyseniz, AsyncWalkthrough_HttpClient projesini açın ve sonra MainWindow. xaml. vb dosyasına `ProcessURLAsync` ekleyin.

    - İzlenecek yolu tamamlayarak kodu geliştirdiyseniz, `HttpClient.GetByteArrayAsync` yöntemini kullanan uygulamaya `ProcessURLAsync` ekleyin. Bu uygulama için MainWindow. xaml. vb dosyası, "Izlenecek yol ile ilgili tüm kod örnekleri" bölümünde yer aldığı ikinci örnektir.

     `ProcessURLAsync` yöntemi, özgün izlenecek yolda `SumPageSizesAsync` `For Each` döngüsünün gövdesinde eylemleri birleştirir. Yöntemi, belirtilen bir Web sitesinin içeriğini bir bayt dizisi olarak zaman uyumsuz olarak indirir ve bayt dizisinin uzunluğunu görüntüler ve döndürür.

     Önceki yordamdaki `ProcessURLAsync` yönteminin tek farkı, `client`<xref:System.Net.Http.HttpClient> örneğinin kullanımı.

    ```vb
    Private Async Function ProcessURLAsync(url As String, client As HttpClient) As Task(Of Integer)

        Dim byteArray = Await client.GetByteArrayAsync(url)
        DisplayResults(url, byteArray)
        Return byteArray.Length
    End Function
    ```

2. Aşağıdaki kodun gösterdiği gibi, `SumPageSizesAsync``For Each` döngüsünü açıklama veya silme.

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

3. <xref:System.Linq.Enumerable.ToArray%2A> yöntemi tarafından yürütüldüğünde, her bir Web sitesinin içeriğini yükleyen bir görev koleksiyonu oluşturan bir [sorgu](../../../../visual-basic/programming-guide/concepts/linq/index.md) tanımlayın. Sorgu değerlendirildiğinde görevler başlatılır.

     `client` ve `urlList`bildiriminin ardından aşağıdaki kodu yöntemine ekleyin `SumPageSizesAsync`.

    ```vb
    ' Create a query.
    Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =
        From url In urlList Select ProcessURLAsync(url, client)

    ' Use ToArray to execute the query and start the download tasks.
    Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()
    ```

4. Sonra, `downloadTasks`görevleri koleksiyonuna `Task.WhenAll` uygulayın. `Task.WhenAll`, görevler koleksiyonundaki tüm görevler tamamlandığında tamamlanmış tek bir görev döndürür.

     Aşağıdaki örnekte `Await` ifadesi, `WhenAll` döndüren tek görevin tamamlanmasını bekler. İşlem tamamlandığında, `Await` ifade, her tamsayı indirilen bir Web sitesinin uzunluğu olduğu bir tamsayılar dizisi olarak değerlendirilir. Önceki adımda eklediğiniz koddan hemen sonra `SumPageSizesAsync`aşağıdaki kodu ekleyin.

    ```vb
    ' Await the completion of all the running tasks.
    Dim lengths As Integer() = Await Task.WhenAll(downloadTasks)

    '' The previous line is equivalent to the following two statements.
    'Dim whenAllTask As Task(Of Integer()) = Task.WhenAll(downloadTasks)
    'Dim lengths As Integer() = Await whenAllTask
    ```

5. Son olarak, tüm Web sitelerinin uzunluklarının toplamını almak için <xref:System.Linq.Enumerable.Sum%2A> yöntemini kullanın. `SumPageSizesAsync`için aşağıdaki satırı ekleyin.

    ```vb
    Dim total = lengths.Sum()
    ```

### <a name="to-test-the-taskwhenall-solutions"></a>Task. WhenAll çözümlerini test etmek için

İki çözüm için, programı çalıştırmak için F5 tuşunu seçin ve ardından **Başlat** düğmesini seçin. Çıktı, zaman uyumsuz çözümlerin çıktısına benzemelidir [: Async ve await kullanarak Web 'e erişme (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md). Ancak, Web sitelerinin her seferinde farklı bir sırada görünmediğine dikkat edin.

## <a name="example"></a>Örnek

Aşağıdaki kod, Web 'den içerik indirmek için `GetURLContentsAsync` yöntemini kullanan projenin uzantılarını gösterir.

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

Aşağıdaki kod, Web 'den içerik indirmek için `HttpClient.GetByteArrayAsync` yöntemi kullanan projenin uzantılarını gösterir.

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
- [İzlenecek yol: Async ve await kullanarak Web 'e erişme (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
