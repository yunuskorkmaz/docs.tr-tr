---
title: Kalan zaman uyumsuz görevleri bir süre tamamlandıktan sonra iptal et (Visual Basic)
ms.date: 07/20/2015
ms.assetid: c928b5a1-622f-4441-8baf-adca1dde197f
ms.openlocfilehash: 329c1eb738f065ae34540e9980c80d44248da05c
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73419797"
---
# <a name="cancel-remaining-async-tasks-after-one-is-complete-visual-basic"></a>Kalan zaman uyumsuz görevleri bir süre tamamlandıktan sonra iptal et (Visual Basic)

<xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> yöntemini bir <xref:System.Threading.CancellationToken>ile birlikte kullanarak, bir görev tamamlandığında kalan tüm görevleri iptal edebilirsiniz. `WhenAny` yöntemi bir görev koleksiyonu olan bir bağımsız değişken alır. Yöntemi tüm görevleri başlatır ve tek bir görev döndürür. Koleksiyondaki herhangi bir görev tamamlandığında tek görev tamamlanır.

Bu örnek, bir iptal belirtecinin, görev koleksiyonundan sona ermesi ve kalan görevleri iptal etmek için ilk görevi tutmak üzere `WhenAny` ile birlikte nasıl kullanılacağını gösterir. Her görev bir Web sitesinin içeriğini indirir. Örnek, tamamlanacak ilk indirmenin içeriklerinin uzunluğunu görüntüler ve diğer indirmeleri iptal eder.

> [!NOTE]
> Örnekleri çalıştırmak için, bilgisayarınızda Visual Studio 2012 veya daha yeni bir sürümü ve .NET Framework 4,5 ya da daha yeni bir sürümü yüklü olmalıdır.

## <a name="downloading-the-example"></a>Örnek indiriliyor

Tüm Windows Presentation Foundation (WPF) projesini [zaman uyumsuz örnekten indirebilirsiniz: uygulamanızı Ince ayar](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) yapın ve ardından aşağıdaki adımları izleyin.

1. İndirdiğiniz dosyayı sıkıştırmasını açın ve ardından Visual Studio 'Yu başlatın.

2. Menü çubuğunda **Dosya**, **Aç**, **Proje/çözüm**' ü seçin.

3. **Proje Aç** iletişim kutusunda, açtığınız örnek kodu tutan klasörü açın ve ardından AsyncFineTuningVB için çözüm (. sln) dosyasını açın.

4. **Çözüm Gezgini**' de, **ınkıfteronetask** projesinin kısayol menüsünü açın ve ardından **Başlangıç projesi olarak ayarla**' yı seçin.

5. Projeyi çalıştırmak için F5 tuşunu seçin.

    Projeyi hata ayıklamadan çalıştırmak için CTRL + F5 tuşlarını seçin.

6. İlk olarak farklı indirmelerin bitmesini doğrulamak için programı birkaç kez çalıştırın.

Projeyi indirmek istemiyorsanız, bu konunun sonundaki MainWindow. xaml. vb dosyasını gözden geçirebilirsiniz.

## <a name="building-the-example"></a>Örnek oluşturma

Bu konudaki örnek, [zaman uyumsuz bir görevi Iptal etme](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md) bölümünde geliştirilen projeye veya bir görev listesini iptal etmek Için bir görev listesine ekler. Örnek, aynı kullanıcı arabirimini kullanır, ancak **iptal** düğmesi açıkça kullanılmaz.

Örneği kendiniz oluşturmak için, "örneği Indirme" bölümündeki yönergeleri izleyin, ancak **Başlangıç projesi**olarak iptal eden **ınlıftasks** ' ı seçin. Bu konudaki değişiklikleri bu projeye ekleyin.

' **De, bir** Web sitesi için işleme adımlarını aşağıdaki zaman uyumsuz metoda taşıyarak, bu işlem için, ' ' ın MainWindow. xaml. vb dosyasında `AccessTheWebAsync` geçişi başlatın.

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

`AccessTheWebAsync`, bu örnek bir sorgu, <xref:System.Linq.Enumerable.ToArray%2A> yöntemi ve bir dizi görevi oluşturmak ve başlatmak için `WhenAny` yöntemini kullanır. Dizi `WhenAny` uygulaması, görev dizisinde tamamlamaya ulaşmak için ilk görevi değerlendiren tek bir görev döndürür.

`AccessTheWebAsync`' de aşağıdaki değişiklikleri yapın. Yıldız işaretleri kod dosyasındaki değişiklikleri işaretler.

1. Döngüyü not edin veya silin.

2. Yürütüldüğünde, genel görevlerden oluşan bir koleksiyon üreten bir sorgu oluşturun. Her `ProcessURLAsync` çağrısı, `TResult` bir tamsayı olduğu <xref:System.Threading.Tasks.Task%601> döndürür.

    ```vb
    ' ***Create a query that, when executed, returns a collection of tasks.
    Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =
        From url In urlList Select ProcessURLAsync(url, client, ct)
    ```

3. Sorguyu yürütmek ve görevleri başlatmak için `ToArray` çağırın. Sonraki adımda `WhenAny` yönteminin uygulaması, sorguyu yürütür ve `ToArray`kullanmadan görevleri başlatır, ancak diğer yöntemler de çalışmayabilir. En güvenli yöntem, sorgunun yürütülmesini açıkça zorlamaktır.

    ```vb
    ' ***Use ToArray to execute the query and start the download tasks.
    Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()
    ```

4. Görevler koleksiyonunda `WhenAny` çağırın. `WhenAny` `Task(Of Task(Of Integer))` veya `Task<Task<int>>`döndürür.  Diğer bir deyişle `WhenAny`, tek bir `Task(Of Integer)` değerlendiren veya `Task<int>` beklendiğinde bir görevi döndürüyor. Bu tek görev, koleksiyondaki ilk görevin sona ermesini sağlar. Önce tamamlanan görev `firstFinishedTask`atanır. `firstFinishedTask` türü, `ProcessURLAsync`dönüş türü olduğundan `TResult` bir tamsayı olduğu <xref:System.Threading.Tasks.Task%601>.

    ```vb
    ' ***Call WhenAny and then await the result. The task that finishes
    ' first is assigned to firstFinishedTask.
    Dim firstFinishedTask As Task(Of Integer) = Await Task.WhenAny(downloadTasks)
    ```

5. Bu örnekte, yalnızca ilk olarak sona erki görevi ilgileniyorsunuz. Bu nedenle, kalan görevleri iptal etmek için <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> kullanın.

    ```vb
    ' ***Cancel the rest of the downloads. You just want the first one.
    cts.Cancel()
    ```

6. Son olarak, indirilen içeriğin uzunluğunu almak için `firstFinishedTask` await.

    ```vb
    Dim length = Await firstFinishedTask
    resultsTextBox.Text &= vbCrLf & $"Length of the downloaded website:  {length}" & vbCrLf
    ```

İlk olarak farklı indirmelerin bitmesini doğrulamak için programı birkaç kez çalıştırın.

## <a name="complete-example"></a>Tam Örnek

Aşağıdaki kod, örnek için tüm MainWindow. xaml. vb veya MainWindow.xaml.cs dosyasıdır. Yıldız işaretleri bu örnek için eklenen öğeleri işaretler.

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
        ''        vbCrLf & $"Length of the downloaded string: {urlContents.Length}." & vbCrLf
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
        resultsTextBox.Text &= vbCrLf & $"Length of the downloaded website:  {length}" & vbCrLf
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

' Length of the downloaded website:  158856

' Download complete.
```

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading.Tasks.Task.WhenAny%2A>
- [Zaman uyumsuz uygulamanızda ince ayar yapma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md)
- [Async ve await ile zaman uyumsuz programlama (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)
- [Zaman uyumsuz örnek: uygulamanıza Ince ayar yapma](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
