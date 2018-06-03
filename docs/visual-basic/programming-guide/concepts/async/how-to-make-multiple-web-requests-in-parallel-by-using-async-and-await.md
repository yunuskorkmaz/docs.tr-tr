---
title: 'Nasıl yapılır: Async kullanarak birden çok Web isteğini paralel hale ve Await (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: a894b99b-7cfd-4a38-adfb-20d24f986730
ms.openlocfilehash: 4d4ccda6657dd4d889e8495fa000715c1f7a5ba6
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2018
ms.locfileid: "34728449"
---
# <a name="how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await-visual-basic"></a>Nasıl yapılır: Async kullanarak birden çok Web isteğini paralel hale ve Await (Visual Basic)
Bir zaman uyumsuz yönteminde oluşturuldukları görevleri başlatılır. [Bekleme](../../../../visual-basic/language-reference/operators/await-operator.md) işleci, burada işleme devam edemiyor görevi tamamlanana kadar yöntemi bir noktada göreve uygulanır. Genellikle, aşağıdaki örnekte gösterildiği gibi oluşturulduktan hemen sonra bir görev beklemenin.  
  
```vb  
Dim result = Await someWebAccessMethodAsync(url)  
```  
  
 Ancak, görev tamamlama sonrasında bağımlı değil programınızın gerçekleştirmek için diğer iş varsa, görev bekleniyor gelen görev oluşturma ayırabilirsiniz.  
  
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
  
 Bir görev başlatma ve onu bekleyen arasında diğer görevleri başlatabilirsiniz. Ek görevler örtük olarak paralel olarak çalışır, ancak hiçbir ek iş parçacığı oluşturulur.  
  
 Aşağıdaki programı üç zaman uyumsuz web yüklemeleri başlatır ve ardından bunları adlı sırada bekler. Bildirim, görevler, bunlar oluşturulan beklemenin ve sırayla her zaman son verme programı, çalıştırdığınızda. Bunlar, oluşturuldukları ve bekleme ifadeleri yöntemi erişmeden önce bir veya daha fazla görevleri son çalışmaya başlar.  
  
> [!NOTE]
>  Bu proje tamamlamak için Visual Studio 2012 veya sonraki sürümlerini ve .NET Framework 4.5 olmalıdır veya üstü yüklü.  
  
 Aynı anda birden çok görevi başlatan başka bir örnek için bkz: [nasıl yapılır: Task.WhenAll kullanarak (Visual Basic) tarafından zaman uyumsuz izlenecek yolu genişletme](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).  
  
 Bu örnekte kodunu indirebilirsiniz [Geliştirici kod örnekleri](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e).  
  
### <a name="to-set-up-the-project"></a>Projeyi ayarlamak için  
  
1.  WPF uygulamayı kurmak için aşağıdaki adımları tamamlayın. Ayrıntılı yönergeler için bu adımları bulabilirsiniz [izlenecek yol: Web kullanarak zaman uyumsuz ve bekleme (Visual Basic) tarafından erişme](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).  
  
    -   Bir düğmeyi ve bir metin kutusu içeren bir WPF uygulaması oluşturun. Düğme adının `startButton`ve metin kutusunun adı `resultsTextBox`.  
  
    -   İçin bir başvuru ekleyin <xref:System.Net.Http>.  
  
    -   MainWindow.xaml.vb dosyasına ekleyin bir `Imports` bildirimi `System.Net.Http`.  
  
### <a name="to-add-the-code"></a>Kod eklemek için  
  
1.  Tasarım penceresinde MainWindow.xaml, oluşturmak için düğmesini çift `startButton_Click` MainWindow.xaml.vb olay işleyicisi.  
  
2.  Aşağıdaki kodu kopyalayın ve gövdesine yapıştırın `startButton_Click` MainWindow.xaml.vb içinde.  
  
    ```vb  
    resultsTextBox.Clear()  
    Await CreateMultipleTasksAsync()  
    resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."  
    ```  
  
     Kod zaman uyumsuz bir yöntem çağırır `CreateMultipleTasksAsync`, uygulama sürücüler.  
  
3.  Aşağıdaki destek yöntemlerden projenize ekleyin:  
  
    -   `ProcessURLAsync` kullanan bir <xref:System.Net.Http.HttpClient> bir bayt dizisi olarak bir Web sitesi içeriğini indirmek için yöntem. Destek yöntemi `ProcessURLAsync` ardından görüntüler ve dizi uzunluğu döndürür.  
  
    -   `DisplayResults` bayt sayısını bayt dizisi, her URL için görüntüler. Bu görüntüler gösterir indirme her görev tamamlandığında.  
  
     Aşağıdaki yöntemlerden kopyalayabilir ve sonra yapıştırabilirsiniz `startButton_Click` MainWindow.xaml.vb olay işleyicisi.  
  
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
        ' Strip off the "http://".  
        Dim displayURL = url.Replace("http://", "")  
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)  
    End Sub  
    ```  
  
4.  Son olarak, yöntemi tanımlayın `CreateMultipleTasksAsync`, aşağıdaki adımları gerçekleştirir.  
  
    -   Yöntem bildiren bir `HttpClient` yöntemi erişimi için gereken nesne <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> içinde `ProcessURLAsync`.  
  
    -   Yöntem oluşturur ve üç görev türü başlatır <xref:System.Threading.Tasks.Task%601>, burada `TResult` bir tamsayıdır. Her görev bitirdiğinde `DisplayResults` görevin URL ve indirilen içeriği uzunluğunu görüntüler. Görevler zaman uyumsuz olarak çalıştığından, sonuçları görünme sırasını bildirilen siparişte farklı olabilir.  
  
    -   Yöntemi, her görevin tamamlanmasını bekler. Her `Await` işleci askıya yürütülmesi `CreateMultipleTasksAsync` awaited görevi tamamlanana kadar. Operatör çağrısı dönüş değerini de alır `ProcessURLAsync` tamamlanan her görev.  
  
    -   Tamamlanan görevler ve tamsayı değerlerini alınan yöntemi Web sitelerinin uzunlukları toplar ve sonucu görüntüler.  
  
     Aşağıdaki yöntem kopyalayın ve çözümünüze yapıştırın.  
  
    ```vb  
    Private Async Function CreateMultipleTasksAsync() As Task  
  
        ' Declare an HttpClient object, and increase the buffer size. The  
        ' default buffer size is 65,536.  
        Dim client As HttpClient =  
            New HttpClient() With {.MaxResponseContentBufferSize = 1000000}  
  
        ' Create and start the tasks. As each task finishes, DisplayResults   
        ' displays its length.  
        Dim download1 As Task(Of Integer) =  
            ProcessURLAsync("http://msdn.microsoft.com", client)  
        Dim download2 As Task(Of Integer) =  
            ProcessURLAsync("http://msdn.microsoft.com/library/hh156528(VS.110).aspx", client)  
        Dim download3 As Task(Of Integer) =  
            ProcessURLAsync("http://msdn.microsoft.com/library/67w7t67f.aspx", client)  
  
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
  
5.  Programını çalıştırın ve ardından için F5 tuşuna seçin **Başlat** düğmesi.  
  
     Program, üç görev her zaman aynı sırada son yok ve hangi son siparişin, bunlar oluşturulan beklemenin sırada mutlaka olmadığından emin doğrulamak için birkaç kez çalıştırın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, tam örnek içerir.  
  
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
            ProcessURLAsync("http://msdn.microsoft.com", client)  
        Dim download2 As Task(Of Integer) =  
            ProcessURLAsync("http://msdn.microsoft.com/library/hh156528(VS.110).aspx", client)  
        Dim download3 As Task(Of Integer) =  
            ProcessURLAsync("http://msdn.microsoft.com/library/67w7t67f.aspx", client)  
  
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
        ' Strip off the "http://".  
        Dim displayURL = url.Replace("http://", "")  
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)  
    End Sub  
End Class  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzlenecek yol: Async kullanarak Web'e erişme ve bekleme (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)  
 [Zaman uyumsuz programlama ile Async ve Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)  
 [Nasıl yapılır: Task.WhenAll (Visual Basic) kullanarak zaman uyumsuz izlenecek yolu genişletme](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)
