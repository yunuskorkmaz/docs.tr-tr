---
title: 'Nasıl yapılır: Task.WhenAll Kullanarak Zaman Uyumsuz İzlenecek Yolu Genişletme'
ms.date: 07/20/2015
ms.assetid: c06d386d-e996-4da9-bf3d-05a3b6c0a258
ms.openlocfilehash: fb323852c83b1edf51396a0b800c2d54a833d0c0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396629"
---
# <a name="how-to-extend-the-async-walkthrough-by-using-taskwhenall-visual-basic"></a>Nasıl yapılır: Task. WhenAll kullanarak zaman uyumsuz Izlenecek yolu genişletme (Visual Basic)

Yöntemini kullanarak, zaman uyumsuz çözümün performansını, [zaman uyumsuz ve await (Visual Basic) kullanarak Web 'e](walkthrough-accessing-the-web-by-using-async-and-await.md) de artırabilirsiniz <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> . Bu yöntem, bir görev koleksiyonu olarak temsil edilen birden çok zaman uyumsuz işlemi zaman uyumsuz olarak bekler.

Gözden geçirmede, Web sitelerinin farklı oranlarda indirdiğini fark etmiş olabilirsiniz. Bazen Web sitelerinden biri çok yavaş olduğundan, kalan tüm indirmeleri gecikmekte. Yönergede oluşturduğunuz zaman uyumsuz çözümleri çalıştırdığınızda, beklemek istemiyorsanız programı kolayca sonlandırabilir, ancak daha iyi bir seçenek, tüm indirmeleri aynı anda başlatmak ve geciktirilen bir süre beklemeden daha hızlı karşıdan yüklemelerin devam etmesini sağlamak olacaktır.

`Task.WhenAll`Yöntemi bir görev koleksiyonuna uygularsınız. Uygulaması, `WhenAll` koleksiyondaki her görev tamamlanana kadar tamamlanmamış tek bir görev döndürür. Görevler paralel olarak çalışır, ancak ek iş parçacığı oluşturulmaz. Görevler herhangi bir sırada tamamlanabilir.

> [!IMPORTANT]
> Aşağıdaki yordamlarda, [Izlenecek yol: Async ve await (Visual Basic) kullanılarak Web 'e erişim](walkthrough-accessing-the-web-by-using-async-and-await.md)için geliştirilmiş zaman uyumsuz uygulamalara yönelik uzantılar açıklanır. Uygulamayı, izlenecek yolu tamamlayarak veya kodu [Geliştirici kodu örneklerinden](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)indirerek geliştirebilirsiniz.
>
> Örneği çalıştırmak için bilgisayarınızda Visual Studio 2012 veya sonraki bir sürümünün yüklü olması gerekir.

### <a name="to-add-taskwhenall-to-your-geturlcontentsasync-solution"></a>GetURLContentsAsync çözümünüze Task. WhenAll eklemek için

1. Yöntemi, `ProcessURLAsync` [izlenecek yol: Async ve Await (Visual Basic) kullanarak Web 'e erişme](walkthrough-accessing-the-web-by-using-async-and-await.md)bölümünde geliştirilen ilk uygulamaya ekleyin.

    - Kodu [Geliştirici kodu örneklerinden](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)Indirdiyseniz asyncwalkthrough projesini açın ve `ProcessURLAsync` MainWindow. xaml. vb dosyasına ekleyin.

    - İzlenecek yolu tamamlayarak kodu geliştirdiyseniz, `ProcessURLAsync` yöntemini içeren uygulamaya ekleyin `GetURLContentsAsync` . Bu uygulama için MainWindow. xaml. vb dosyası, "Izlenecek yol içindeki tüm kod örnekleri" bölümünde yer aldığı ilk örnektir.

     `ProcessURLAsync`Yöntemi, `For Each` ilk izlenecek yolda içindeki döngüsünün gövdesinde bulunan eylemleri birleştirir `SumPageSizesAsync` . Yöntemi, belirtilen bir Web sitesinin içeriğini bir bayt dizisi olarak zaman uyumsuz olarak indirir ve bayt dizisinin uzunluğunu görüntüler ve döndürür.

    ```vb
    Private Async Function ProcessURLAsync(url As String) As Task(Of Integer)

        Dim byteArray = Await GetURLContentsAsync(url)
        DisplayResults(url, byteArray)
        Return byteArray.Length
    End Function
    ```

2. `For Each` `SumPageSizesAsync` Aşağıdaki kodun gösterdiği gibi, içindeki döngüyü not edin veya silin.

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

3. Bir görev koleksiyonu oluşturun. Aşağıdaki kod, yöntemi tarafından [query](../linq/index.md) yürütüldüğünde <xref:System.Linq.Enumerable.ToArray%2A> , her bir Web sitesinin içeriğini yükleyen bir görev koleksiyonu oluşturan bir sorgu tanımlar. Sorgu değerlendirildiğinde görevler başlatılır.

     Bildirimi sonrasında yöntemine aşağıdaki kodu ekleyin `SumPageSizesAsync` `urlList` .

    ```vb
    ' Create a query.
    Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =
        From url In urlList Select ProcessURLAsync(url)

    ' Use ToArray to execute the query and start the download tasks.
    Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()
    ```

4. `Task.WhenAll`Görev koleksiyonu için geçerlidir `downloadTasks` . `Task.WhenAll`görev koleksiyonundaki tüm görevler tamamlandığında tamamlanan tek bir görev döndürür.

     Aşağıdaki örnekte, `Await` ifadesi döndüren tek görevin tamamlanmasını bekler `WhenAll` . İfade, her tamsayının indirilen bir Web sitesinin uzunluğu olduğu bir tamsayılar dizisi olarak değerlendirilir. `SumPageSizesAsync`Önceki adımda eklediğiniz koddan hemen sonra aşağıdaki kodu ekleyin.

    ```vb
    ' Await the completion of all the running tasks.
    Dim lengths As Integer() = Await Task.WhenAll(downloadTasks)

    '' The previous line is equivalent to the following two statements.
    'Dim whenAllTask As Task(Of Integer()) = Task.WhenAll(downloadTasks)
    'Dim lengths As Integer() = Await whenAllTask
    ```

5. Son olarak, <xref:System.Linq.Enumerable.Sum%2A> tüm Web sitelerinin uzunluklarının toplamını hesaplamak için yöntemini kullanın. Aşağıdaki satırı öğesine ekleyin `SumPageSizesAsync` .

    ```vb
    Dim total = lengths.Sum()
    ```

### <a name="to-add-taskwhenall-to-the-httpclientgetbytearrayasync-solution"></a>HttpClient. GetByteArrayAsync çözümüne Task. WhenAll eklemek için

1. Aşağıdaki sürümünü, `ProcessURLAsync` [izlenecek yol: Async ve Await (Visual Basic) kullanarak Web 'e erişme](walkthrough-accessing-the-web-by-using-async-and-await.md)bölümünde geliştirilen ikinci uygulamaya ekleyin.

    - Kodu [Geliştirici kodu örnekleri](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)' nden indirdiyseniz, AsyncWalkthrough_HttpClient projesini açın ve `ProcessURLAsync` MainWindow. xaml. vb dosyasına ekleyin.

    - İzlenecek yolu tamamlayarak kodu geliştirdiyseniz, `ProcessURLAsync` yöntemini kullanan uygulamaya ekleyin `HttpClient.GetByteArrayAsync` . Bu uygulama için MainWindow. xaml. vb dosyası, "Izlenecek yol ile ilgili tüm kod örnekleri" bölümünde yer aldığı ikinci örnektir.

     `ProcessURLAsync`Yöntemi, `For Each` ilk izlenecek yolda içindeki döngüsünün gövdesinde bulunan eylemleri birleştirir `SumPageSizesAsync` . Yöntemi, belirtilen bir Web sitesinin içeriğini bir bayt dizisi olarak zaman uyumsuz olarak indirir ve bayt dizisinin uzunluğunu görüntüler ve döndürür.

     `ProcessURLAsync`Önceki yordamdaki yöntemden tek fark <xref:System.Net.Http.HttpClient> , örneği kullanmaktır `client` .

    ```vb
    Private Async Function ProcessURLAsync(url As String, client As HttpClient) As Task(Of Integer)

        Dim byteArray = Await client.GetByteArrayAsync(url)
        DisplayResults(url, byteArray)
        Return byteArray.Length
    End Function
    ```

2. `For Each` `SumPageSizesAsync` Aşağıdaki kodun gösterdiği gibi, içindeki döngüyü not edin veya silin.

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

3. Yöntemi tarafından [query](../linq/index.md) yürütüldüğünde <xref:System.Linq.Enumerable.ToArray%2A> , her bir Web sitesinin içeriğini yükleyen bir görev koleksiyonu oluşturan bir sorgu tanımlayın. Sorgu değerlendirildiğinde görevler başlatılır.

     Ve bildiriminden sonra yöntemine aşağıdaki kodu ekleyin `SumPageSizesAsync` `client` `urlList` .

    ```vb
    ' Create a query.
    Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =
        From url In urlList Select ProcessURLAsync(url, client)

    ' Use ToArray to execute the query and start the download tasks.
    Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()
    ```

4. Sonra, `Task.WhenAll` görev koleksiyonu için geçerlidir `downloadTasks` . `Task.WhenAll`görev koleksiyonundaki tüm görevler tamamlandığında tamamlanan tek bir görev döndürür.

     Aşağıdaki örnekte, `Await` ifadesi döndüren tek görevin tamamlanmasını bekler `WhenAll` . İşlem tamamlandığında, `Await` ifade, her tamsayı indirilen bir Web sitesinin uzunluğu olduğu bir tamsayılar dizisi olarak değerlendirilir. `SumPageSizesAsync`Önceki adımda eklediğiniz koddan hemen sonra aşağıdaki kodu ekleyin.

    ```vb
    ' Await the completion of all the running tasks.
    Dim lengths As Integer() = Await Task.WhenAll(downloadTasks)

    '' The previous line is equivalent to the following two statements.
    'Dim whenAllTask As Task(Of Integer()) = Task.WhenAll(downloadTasks)
    'Dim lengths As Integer() = Await whenAllTask
    ```

5. Son olarak, <xref:System.Linq.Enumerable.Sum%2A> tüm Web sitelerinin uzunluklarının toplamını almak için yöntemini kullanın. Aşağıdaki satırı öğesine ekleyin `SumPageSizesAsync` .

    ```vb
    Dim total = lengths.Sum()
    ```

### <a name="to-test-the-taskwhenall-solutions"></a>Task. WhenAll çözümlerini test etmek için

İki çözüm için, programı çalıştırmak için F5 tuşunu seçin ve ardından **Başlat** düğmesini seçin. Çıktı, zaman uyumsuz çözümlerin çıktısına benzemelidir [: Async ve await kullanarak Web 'e erişme (Visual Basic)](walkthrough-accessing-the-web-by-using-async-and-await.md). Ancak, Web sitelerinin her seferinde farklı bir sırada görünmediğine dikkat edin.

## <a name="example"></a>Örnek

Aşağıdaki kod, `GetURLContentsAsync` Web 'den içerik indirmek için yöntemini kullanan projenin uzantılarını gösterir.

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

Aşağıdaki kod, `HttpClient.GetByteArrayAsync` Web 'den içerik indirmek için yöntemini kullanan projenin uzantılarını gösterir.

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
- [İzlenecek yol: Async ve await kullanarak Web 'e erişme (Visual Basic)](walkthrough-accessing-the-web-by-using-async-and-await.md)
