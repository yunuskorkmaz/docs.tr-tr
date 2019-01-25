---
title: 'Nasıl yapılır: Zaman uyumsuz kullanarak birden çok Web isteğini paralel hale getirme ve Await (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: a894b99b-7cfd-4a38-adfb-20d24f986730
ms.openlocfilehash: 526ef4c14649c1840b8c310af45de9b5095909de
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54495959"
---
# <a name="how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await-visual-basic"></a>Nasıl yapılır: Zaman uyumsuz kullanarak birden çok Web isteğini paralel hale getirme ve Await (Visual Basic)
Yük oluşturulduğunda bir zaman uyumsuz yönteminde görevler oluşturulduklarında başlatılır. [Await](../../../../visual-basic/language-reference/operators/await-operator.md) işleci işlemenin devam edemediği görev tamamlanana kadar yöntem noktasındaki göreve uygulanır. Genellikle, aşağıdaki örnekte gösterildiği gibi oluşturulduktan hemen sonra bir görev beklenir.  
  
```vb  
Dim result = Await someWebAccessMethodAsync(url)  
```  
  
 Ancak, görev öğesinin tamamlanmasına bağımlı değildir, programınızın gerçekleştirilecek başka işleri varsa, görevi bekleme işleminden görev oluşturma ayırabilirsiniz.  
  
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
  
 Bir görev başlatma ve bekleme arasında başka görevler başlatabilirsiniz. Ek görevler, örtülü olarak paralel olarak çalışır, ancak hiçbir ek iş parçacığı oluşturulmaz.  
  
 Aşağıdaki program üç zaman uyumsuz web yüklemesini başlatır ve ardından bunları adlı sırayla bekler. Bu görev sırası, bunlar oluşturulan bekleniyor ve her zaman tamamlanmıyor programı çalıştırdığınızda dikkat edin. Oluşturuldukları ve yöntem bekleme ifadelerine ulaşmadan önce bir veya birkaç görev bitebilir çalışmaya başlayın.  
  
> [!NOTE]
>  Bu projeyi tamamlamak için Visual Studio 2012 veya üzeri ve .NET Framework 4.5 olmalıdır veya üzeri yüklü.  
  
 Aynı anda birden çok görevi başlatan başka bir örnek için bkz [nasıl yapılır: (Visual Basic) Task.WhenAll kullanarak zaman uyumsuz izlenecek yolu genişletme](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).  
  
 Bu örnekte kodunu indirebilirsiniz [geliştirici kodu örnekleri](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e).  
  
### <a name="to-set-up-the-project"></a>Projeyi kurmak için  
  
1.  Bir WPF uygulaması ayarlamak için aşağıdaki adımları tamamlayın. İçinde bu adımlara ilişkin ayrıntılı yönergeleri bulabilirsiniz [izlenecek yol: Zaman uyumsuz kullanarak Web'e erişme ve Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).  
  
    -   Bir metin kutusu ve bir düğmeyi içeren bir WPF uygulaması oluşturun. Düğmeyi adlandırın `startButton`ve metin kutusunu adlandırın `resultsTextBox`.  
  
    -   İçin bir başvuru eklemeniz <xref:System.Net.Http>.  
  
    -   MainWindow.xaml.vb dosyasına ekleyin bir `Imports` bildirimi `System.Net.Http`.  
  
### <a name="to-add-the-code"></a>Kod eklemek için  
  
1.  Tasarım penceresinde, MainWindow.xaml oluşturmak için düğmeyi çift tıklatın `startButton_Click` MainWindow.xaml.vb olay işleyicisi.  
  
2.  Aşağıdaki kodu kopyalayın ve gövdesine yapıştırın `startButton_Click` MainWindow.xaml.vb içinde.  
  
    ```vb  
    resultsTextBox.Clear()  
    Await CreateMultipleTasksAsync()  
    resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."  
    ```  
  
     Kod, zaman uyumsuz bir yöntem çağırır `CreateMultipleTasksAsync`, uygulama sürücüleri.  
  
3.  Projeye şu destek yöntemlerini ekleyin:  
  
    -   `ProcessURLAsync` kullanan bir <xref:System.Net.Http.HttpClient> bir bayt dizisi olarak bir Web sitesinin içeriklerini karşıdan yüklemek için yöntemi. Destek yöntemi daha `ProcessURLAsync` ardından görüntüler ve dizinin uzunluğunu döndürür.  
  
    -   `DisplayResults` bayt sayısı, her bir URL için bayt dizisindeki görüntüler. Bu görüntüler gösterir her bir görevin indirmeyi bitirmesini.  
  
     Aşağıdaki yöntemleri kopyalayın ve sonra bunları yapıştırın `startButton_Click` MainWindow.xaml.vb olay işleyicisi.  
  
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
  
4.  Son olarak, yöntemi tanımlayan `CreateMultipleTasksAsync`, aşağıdaki adımları gerçekleştirir.  
  
    -   Yöntem bir `HttpClient` yöntemi erişimi için gereken nesne <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> içinde `ProcessURLAsync`.  
  
    -   Yöntemi oluşturur ve başlatır türünde üç görev <xref:System.Threading.Tasks.Task%601>burada `TResult` bir tamsayıdır. Her görev bittikçe `DisplayResults` görevin URL'sini ve karşıdan yüklenen içeriklerin uzunluğunu görüntüler. Görevler zaman uyumsuz olarak çalıştığından, sonuçların görüntülenme sırasını bildirilmiş sırasından farklı olabilir.  
  
    -   Yöntem her görevin tamamlanmasını bekler. Her `Await` işleci yürütmesini askıya alır `CreateMultipleTasksAsync` beklenen görev bitinceye kadar. İşleci ayrıca çağrısından dönen değer alır `ProcessURLAsync` her tamamlanan görevden.  
  
    -   Görevler tamamlandığında ve tamsayı değerleri alındığında, yöntem Web sitelerinin uzunluklarını toplar ve sonucu görüntüler.  
  
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
  
5.  Programı çalıştırın ve ardından F5 tuşuna basın **Başlat** düğmesi.  
  
     Program üç görevin her zaman aynı sırada tamamlanmıyor ve hangi sıranın mutlaka, bunlar oluşturulan bekleniyor ve sırasını olmadığını doğrulamak için birkaç kez çalıştırın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod tam örneği içermektedir.  
  
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
- [İzlenecek yol: Zaman uyumsuz kullanarak Web'e erişme ve Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Zaman uyumsuz programlama ile Async ve Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)
- [Nasıl yapılır: (Visual Basic) Task.WhenAll kullanarak zaman uyumsuz izlenecek yolu genişletme](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)
