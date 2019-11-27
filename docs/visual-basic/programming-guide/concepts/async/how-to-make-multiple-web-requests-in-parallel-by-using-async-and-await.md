---
title: 'Nasıl yapılır: Async ve Await Kullanarak Birden Çok Web İsteğini Paralel Hale Getirme'
ms.date: 07/20/2015
ms.assetid: a894b99b-7cfd-4a38-adfb-20d24f986730
ms.openlocfilehash: 616efca79312883f17ba837d17a5ee9c97d15b34
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346143"
---
# <a name="how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await-visual-basic"></a>Nasıl yapılır: Async ve await kullanarak birden çok Web Isteğini paralel hale getirme (Visual Basic)

Zaman uyumsuz bir yöntemde görevler oluşturulduğunda başlatılır. [Await](../../../../visual-basic/language-reference/operators/await-operator.md) işleci, görev bitene kadar işlemin devam edemediği yöntemdeki noktada göreve uygulanır. Aşağıdaki örnekte gösterildiği gibi, genellikle bir görev, oluşturulduktan hemen sonra beklediğinde.

```vb
Dim result = Await someWebAccessMethodAsync(url)
```

Ancak, programın gerçekleştirmeye yönelik başka bir işi olması durumunda görevin tamamlanmasına bağlı olmaması durumunda görevi bekleyen görev oluşturmayı ayırabilirsiniz.

```vb
' The following line creates and starts the task.
Dim myTask = someWebAccessMethodAsync(url)

' While the task is running, you can do other work that does not depend
' on the results of the task.
' . . . . .

' The application of Await suspends the rest of this method until the task is
' complete.
Dim result = Await myTask
```

Bir görevi başlatma ve bekleme arasında başka görevler de başlatabilirsiniz. Ek görevler dolaylı olarak paralel olarak çalışır, ancak ek iş parçacığı oluşturulmaz.

Aşağıdaki program, üç zaman uyumsuz Web yüklemesi başlatır ve ardından bunların çağrıldıkları sırayla bekler. Programı çalıştırdığınızda, görevlerin Oluşturulma sırasında ve bekledikleri sırada her zaman bitmediğine dikkat edin. Bunlar oluşturulduğunda çalışmaya başlar ve Yöntem await ifadelerine ulaşmadan önce bir veya daha fazla görev bitebilirler.

> [!NOTE]
> Bu projeyi tamamlayabilmeniz için, bilgisayarınızda Visual Studio 2012 veya üzeri ve .NET Framework 4,5 veya üzeri yüklü olmalıdır.

Aynı anda birden çok görevi Başlatan başka bir örnek için, bkz. [nasıl yapılır: Task. WhenAll kullanarak zaman uyumsuz Izlenecek yolu genişletme (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).

Bu örnek için kodu [Geliştirici kodu örneklerinden](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e)indirebilirsiniz.

### <a name="to-set-up-the-project"></a>Projeyi ayarlamak için

1. WPF uygulaması ayarlamak için aşağıdaki adımları izleyin. [Izlenecek yol: Async ve await (Visual Basic) kullanarak Web 'e erişmek](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)için bu adımlarla ilgili ayrıntılı yönergeleri bulabilirsiniz.

    - Metin kutusu ve düğme içeren bir WPF uygulaması oluşturun. Düğmeyi `startButton`adlandırın ve metin kutusu `resultsTextBox`adlandırın.

    - <xref:System.Net.Http>için bir başvuru ekleyin.

    - MainWindow. xaml. vb dosyasında, `System.Net.Http`için `Imports` bir ifade ekleyin.

### <a name="to-add-the-code"></a>Kodu eklemek için

1. MainWindow. xaml tasarım penceresinde, MainWindow. xaml. vb ' de `startButton_Click` olay işleyicisini oluşturmak için düğmeye çift tıklayın.

2. Aşağıdaki kodu kopyalayın ve MainWindow. xaml. vb içindeki `startButton_Click` gövdesine yapıştırın.

    ```vb
    resultsTextBox.Clear()
    Await CreateMultipleTasksAsync()
    resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."
    ```

     Kod, uygulamayı yönlendiren `CreateMultipleTasksAsync`bir zaman uyumsuz yöntemi çağırır.

3. Aşağıdaki destek yöntemlerini projeye ekleyin:

    - `ProcessURLAsync`, bir Web sitesinin içeriğini bir bayt dizisi olarak indirmek için bir <xref:System.Net.Http.HttpClient> yöntemi kullanır. `ProcessURLAsync` support yöntemi, sonra dizinin uzunluğunu gösterir ve döndürür.

    - `DisplayResults` her bir URL için bayt dizisindeki bayt sayısını görüntüler. Bu ekranda, her görevin indirilmesi tamamlandığında gösterilir.

     Aşağıdaki yöntemleri kopyalayın ve MainWindow. xaml. vb ' de `startButton_Click` olay işleyicisinden sonra yapıştırın.

    ```vb
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
    ```

4. Son olarak, aşağıdaki adımları gerçekleştiren `CreateMultipleTasksAsync`yöntemini tanımlayın.

    - Yöntemi, `ProcessURLAsync`<xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> yöntemine erişmeniz gereken `HttpClient` nesnesini bildirir.

    - Yöntemi <xref:System.Threading.Tasks.Task%601>türünde üç görev oluşturur ve başlatır; burada `TResult` bir tamsayıdır. Her görev bittiğinde `DisplayResults` görevin URL 'sini ve indirilen içeriklerin uzunluğunu görüntüler. Görevler zaman uyumsuz olarak çalıştığından, sonuçların göründüğü sıra, bildirildiği sırayla farklılık gösterebilir.

    - Yöntemi her görevin tamamlanmasını bekler. Her bir `Await` işleci, beklenen görev tamamlanana kadar `CreateMultipleTasksAsync` yürütmeyi askıya alır. İşleci, her tamamlanan görevden `ProcessURLAsync` çağrısından dönüş değerini de alır.

    - Görevler tamamlandığında ve tamsayı değerleri alınırsa, yöntemi web sitelerinin uzunluklarını toplar ve sonucu görüntüler.

     Aşağıdaki yöntemi kopyalayın ve çözümünüze yapıştırın.

    ```vb
    Private Async Function CreateMultipleTasksAsync() As Task

        ' Declare an HttpClient object, and increase the buffer size. The
        ' default buffer size is 65,536.
        Dim client As HttpClient =
            New HttpClient() With {.MaxResponseContentBufferSize = 1000000}

        ' Create and start the tasks. As each task finishes, DisplayResults
        ' displays its length.
        Dim download1 As Task(Of Integer) =
            ProcessURLAsync("https://msdn.microsoft.com", client)
        Dim download2 As Task(Of Integer) =
            ProcessURLAsync("https://msdn.microsoft.com/library/hh156528(VS.110).aspx", client)
        Dim download3 As Task(Of Integer) =
            ProcessURLAsync("https://msdn.microsoft.com/library/67w7t67f.aspx", client)

        ' Await each task.
        Dim length1 As Integer = Await download1
        Dim length2 As Integer = Await download2
        Dim length3 As Integer = Await download3

        Dim total As Integer = length1 + length2 + length3

        ' Display the total count for all of the websites.
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf &
                                             "Total bytes returned:  {0}" & vbCrLf, total)
    End Function
    ```

5. Programı çalıştırmak için F5 tuşunu seçin ve sonra **Başlat** düğmesini seçin.

     Üç görevin her zaman aynı sırada bitmeyeceğini ve bunların tamamların oluşturulma sırası ve bekledikleri sıra olması gerektiğini doğrulamak için programı birkaç kez çalıştırın.

## <a name="example"></a>Örnek

Aşağıdaki kod tam örneği içerir.

```vb
' Add the following Imports statements, and add a reference for System.Net.Http.
Imports System.Net.Http

Class MainWindow

    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click
        resultsTextBox.Clear()
        Await CreateMultipleTasksAsync()
        resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."
    End Sub

    Private Async Function CreateMultipleTasksAsync() As Task

        ' Declare an HttpClient object, and increase the buffer size. The
        ' default buffer size is 65,536.
        Dim client As HttpClient =
            New HttpClient() With {.MaxResponseContentBufferSize = 1000000}

        ' Create and start the tasks. As each task finishes, DisplayResults
        ' displays its length.
        Dim download1 As Task(Of Integer) =
            ProcessURLAsync("https://msdn.microsoft.com", client)
        Dim download2 As Task(Of Integer) =
            ProcessURLAsync("https://msdn.microsoft.com/library/hh156528(VS.110).aspx", client)
        Dim download3 As Task(Of Integer) =
            ProcessURLAsync("https://msdn.microsoft.com/library/67w7t67f.aspx", client)

        ' Await each task.
        Dim length1 As Integer = Await download1
        Dim length2 As Integer = Await download2
        Dim length3 As Integer = Await download3

        Dim total As Integer = length1 + length2 + length3

        ' Display the total count for all of the websites.
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf &
                                             "Total bytes returned:  {0}" & vbCrLf, total)
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

- [İzlenecek yol: Async ve await kullanarak Web 'e erişme (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Async ve await ile zaman uyumsuz programlama (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)
- [Nasıl yapılır: Task. WhenAll kullanarak zaman uyumsuz Izlenecek yolu genişletme (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)
