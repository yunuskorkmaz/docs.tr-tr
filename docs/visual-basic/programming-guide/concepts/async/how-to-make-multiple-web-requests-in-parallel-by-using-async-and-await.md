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
# <a name="how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await-visual-basic"></a><span data-ttu-id="2ec73-102">Nasıl yapılır: Async kullanarak birden çok Web isteğini paralel hale ve Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2ec73-102">How to: Make Multiple Web Requests in Parallel by Using Async and Await (Visual Basic)</span></span>
<span data-ttu-id="2ec73-103">Bir zaman uyumsuz yönteminde oluşturuldukları görevleri başlatılır.</span><span class="sxs-lookup"><span data-stu-id="2ec73-103">In an async method, tasks are started when they’re created.</span></span> <span data-ttu-id="2ec73-104">[Bekleme](../../../../visual-basic/language-reference/operators/await-operator.md) işleci, burada işleme devam edemiyor görevi tamamlanana kadar yöntemi bir noktada göreve uygulanır.</span><span class="sxs-lookup"><span data-stu-id="2ec73-104">The [Await](../../../../visual-basic/language-reference/operators/await-operator.md) operator is applied to the task at the point in the method where processing can’t continue until the task finishes.</span></span> <span data-ttu-id="2ec73-105">Genellikle, aşağıdaki örnekte gösterildiği gibi oluşturulduktan hemen sonra bir görev beklemenin.</span><span class="sxs-lookup"><span data-stu-id="2ec73-105">Often a task is awaited as soon as it’s created, as the following example shows.</span></span>  
  
```vb  
Dim result = Await someWebAccessMethodAsync(url)  
```  
  
 <span data-ttu-id="2ec73-106">Ancak, görev tamamlama sonrasında bağımlı değil programınızın gerçekleştirmek için diğer iş varsa, görev bekleniyor gelen görev oluşturma ayırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2ec73-106">However, you can separate creating the task from awaiting the task if your program has other work to accomplish that doesn’t depend on the completion of the task.</span></span>  
  
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
  
 <span data-ttu-id="2ec73-107">Bir görev başlatma ve onu bekleyen arasında diğer görevleri başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2ec73-107">Between starting a task and awaiting it, you can start other tasks.</span></span> <span data-ttu-id="2ec73-108">Ek görevler örtük olarak paralel olarak çalışır, ancak hiçbir ek iş parçacığı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="2ec73-108">The additional tasks implicitly run in parallel, but no additional threads are created.</span></span>  
  
 <span data-ttu-id="2ec73-109">Aşağıdaki programı üç zaman uyumsuz web yüklemeleri başlatır ve ardından bunları adlı sırada bekler.</span><span class="sxs-lookup"><span data-stu-id="2ec73-109">The following program starts three asynchronous web downloads and then awaits them in the order in which they’re called.</span></span> <span data-ttu-id="2ec73-110">Bildirim, görevler, bunlar oluşturulan beklemenin ve sırayla her zaman son verme programı, çalıştırdığınızda.</span><span class="sxs-lookup"><span data-stu-id="2ec73-110">Notice, when you run the program, that the tasks don’t always finish in the order in which they’re created and awaited.</span></span> <span data-ttu-id="2ec73-111">Bunlar, oluşturuldukları ve bekleme ifadeleri yöntemi erişmeden önce bir veya daha fazla görevleri son çalışmaya başlar.</span><span class="sxs-lookup"><span data-stu-id="2ec73-111">They start to run when they’re created, and one or more of the tasks might finish before the method reaches the await expressions.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2ec73-112">Bu proje tamamlamak için Visual Studio 2012 veya sonraki sürümlerini ve .NET Framework 4.5 olmalıdır veya üstü yüklü.</span><span class="sxs-lookup"><span data-stu-id="2ec73-112">To complete this project, you must have Visual Studio 2012 or higher and the .NET Framework 4.5 or higher installed on your computer.</span></span>  
  
 <span data-ttu-id="2ec73-113">Aynı anda birden çok görevi başlatan başka bir örnek için bkz: [nasıl yapılır: Task.WhenAll kullanarak (Visual Basic) tarafından zaman uyumsuz izlenecek yolu genişletme](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span><span class="sxs-lookup"><span data-stu-id="2ec73-113">For another example that starts multiple tasks at the same time, see [How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span></span>  
  
 <span data-ttu-id="2ec73-114">Bu örnekte kodunu indirebilirsiniz [Geliştirici kod örnekleri](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e).</span><span class="sxs-lookup"><span data-stu-id="2ec73-114">You can download the code for this example from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e).</span></span>  
  
### <a name="to-set-up-the-project"></a><span data-ttu-id="2ec73-115">Projeyi ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="2ec73-115">To set up the project</span></span>  
  
1.  <span data-ttu-id="2ec73-116">WPF uygulamayı kurmak için aşağıdaki adımları tamamlayın.</span><span class="sxs-lookup"><span data-stu-id="2ec73-116">To set up a WPF application, complete the following steps.</span></span> <span data-ttu-id="2ec73-117">Ayrıntılı yönergeler için bu adımları bulabilirsiniz [izlenecek yol: Web kullanarak zaman uyumsuz ve bekleme (Visual Basic) tarafından erişme](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="2ec73-117">You can find detailed instructions for these steps in [Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span>  
  
    -   <span data-ttu-id="2ec73-118">Bir düğmeyi ve bir metin kutusu içeren bir WPF uygulaması oluşturun.</span><span class="sxs-lookup"><span data-stu-id="2ec73-118">Create a WPF application that contains a text box and a button.</span></span> <span data-ttu-id="2ec73-119">Düğme adının `startButton`ve metin kutusunun adı `resultsTextBox`.</span><span class="sxs-lookup"><span data-stu-id="2ec73-119">Name the button `startButton`, and name the text box `resultsTextBox`.</span></span>  
  
    -   <span data-ttu-id="2ec73-120">İçin bir başvuru ekleyin <xref:System.Net.Http>.</span><span class="sxs-lookup"><span data-stu-id="2ec73-120">Add a reference for <xref:System.Net.Http>.</span></span>  
  
    -   <span data-ttu-id="2ec73-121">MainWindow.xaml.vb dosyasına ekleyin bir `Imports` bildirimi `System.Net.Http`.</span><span class="sxs-lookup"><span data-stu-id="2ec73-121">In the MainWindow.xaml.vb file, add an `Imports` statement for `System.Net.Http`.</span></span>  
  
### <a name="to-add-the-code"></a><span data-ttu-id="2ec73-122">Kod eklemek için</span><span class="sxs-lookup"><span data-stu-id="2ec73-122">To add the code</span></span>  
  
1.  <span data-ttu-id="2ec73-123">Tasarım penceresinde MainWindow.xaml, oluşturmak için düğmesini çift `startButton_Click` MainWindow.xaml.vb olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="2ec73-123">In the design window, MainWindow.xaml, double-click the button to create the `startButton_Click` event handler in MainWindow.xaml.vb.</span></span>  
  
2.  <span data-ttu-id="2ec73-124">Aşağıdaki kodu kopyalayın ve gövdesine yapıştırın `startButton_Click` MainWindow.xaml.vb içinde.</span><span class="sxs-lookup"><span data-stu-id="2ec73-124">Copy the following code, and paste it into the body of `startButton_Click` in MainWindow.xaml.vb.</span></span>  
  
    ```vb  
    resultsTextBox.Clear()  
    Await CreateMultipleTasksAsync()  
    resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."  
    ```  
  
     <span data-ttu-id="2ec73-125">Kod zaman uyumsuz bir yöntem çağırır `CreateMultipleTasksAsync`, uygulama sürücüler.</span><span class="sxs-lookup"><span data-stu-id="2ec73-125">The code calls an asynchronous method, `CreateMultipleTasksAsync`, which drives the application.</span></span>  
  
3.  <span data-ttu-id="2ec73-126">Aşağıdaki destek yöntemlerden projenize ekleyin:</span><span class="sxs-lookup"><span data-stu-id="2ec73-126">Add the following support methods to the project:</span></span>  
  
    -   <span data-ttu-id="2ec73-127">`ProcessURLAsync` kullanan bir <xref:System.Net.Http.HttpClient> bir bayt dizisi olarak bir Web sitesi içeriğini indirmek için yöntem.</span><span class="sxs-lookup"><span data-stu-id="2ec73-127">`ProcessURLAsync` uses an <xref:System.Net.Http.HttpClient> method to download the contents of a website as a byte array.</span></span> <span data-ttu-id="2ec73-128">Destek yöntemi `ProcessURLAsync` ardından görüntüler ve dizi uzunluğu döndürür.</span><span class="sxs-lookup"><span data-stu-id="2ec73-128">The support method, `ProcessURLAsync` then displays and returns the length of the array.</span></span>  
  
    -   <span data-ttu-id="2ec73-129">`DisplayResults` bayt sayısını bayt dizisi, her URL için görüntüler.</span><span class="sxs-lookup"><span data-stu-id="2ec73-129">`DisplayResults` displays the number of bytes in the byte array for each URL.</span></span> <span data-ttu-id="2ec73-130">Bu görüntüler gösterir indirme her görev tamamlandığında.</span><span class="sxs-lookup"><span data-stu-id="2ec73-130">This display shows when each task has finished downloading.</span></span>  
  
     <span data-ttu-id="2ec73-131">Aşağıdaki yöntemlerden kopyalayabilir ve sonra yapıştırabilirsiniz `startButton_Click` MainWindow.xaml.vb olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="2ec73-131">Copy the following methods, and paste them after the `startButton_Click` event handler in MainWindow.xaml.vb.</span></span>  
  
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
  
4.  <span data-ttu-id="2ec73-132">Son olarak, yöntemi tanımlayın `CreateMultipleTasksAsync`, aşağıdaki adımları gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="2ec73-132">Finally, define method `CreateMultipleTasksAsync`, which performs the following steps.</span></span>  
  
    -   <span data-ttu-id="2ec73-133">Yöntem bildiren bir `HttpClient` yöntemi erişimi için gereken nesne <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> içinde `ProcessURLAsync`.</span><span class="sxs-lookup"><span data-stu-id="2ec73-133">The method declares an `HttpClient` object,which you need  to access method <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> in `ProcessURLAsync`.</span></span>  
  
    -   <span data-ttu-id="2ec73-134">Yöntem oluşturur ve üç görev türü başlatır <xref:System.Threading.Tasks.Task%601>, burada `TResult` bir tamsayıdır.</span><span class="sxs-lookup"><span data-stu-id="2ec73-134">The method creates and starts three tasks of type <xref:System.Threading.Tasks.Task%601>, where `TResult` is an integer.</span></span> <span data-ttu-id="2ec73-135">Her görev bitirdiğinde `DisplayResults` görevin URL ve indirilen içeriği uzunluğunu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="2ec73-135">As each task finishes, `DisplayResults` displays the task's URL and the length of the downloaded contents.</span></span> <span data-ttu-id="2ec73-136">Görevler zaman uyumsuz olarak çalıştığından, sonuçları görünme sırasını bildirilen siparişte farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="2ec73-136">Because the tasks are running asynchronously, the order in which the results appear might differ from the order in which they were declared.</span></span>  
  
    -   <span data-ttu-id="2ec73-137">Yöntemi, her görevin tamamlanmasını bekler.</span><span class="sxs-lookup"><span data-stu-id="2ec73-137">The method awaits the completion of each task.</span></span> <span data-ttu-id="2ec73-138">Her `Await` işleci askıya yürütülmesi `CreateMultipleTasksAsync` awaited görevi tamamlanana kadar.</span><span class="sxs-lookup"><span data-stu-id="2ec73-138">Each `Await` operator suspends execution of `CreateMultipleTasksAsync` until the awaited task is finished.</span></span> <span data-ttu-id="2ec73-139">Operatör çağrısı dönüş değerini de alır `ProcessURLAsync` tamamlanan her görev.</span><span class="sxs-lookup"><span data-stu-id="2ec73-139">The operator also retrieves the return value from the call to `ProcessURLAsync` from each completed task.</span></span>  
  
    -   <span data-ttu-id="2ec73-140">Tamamlanan görevler ve tamsayı değerlerini alınan yöntemi Web sitelerinin uzunlukları toplar ve sonucu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="2ec73-140">When the tasks have been completed and the integer values have been retrieved, the method sums the lengths of the websites and displays the result.</span></span>  
  
     <span data-ttu-id="2ec73-141">Aşağıdaki yöntem kopyalayın ve çözümünüze yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="2ec73-141">Copy the following method, and paste it into your solution.</span></span>  
  
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
  
5.  <span data-ttu-id="2ec73-142">Programını çalıştırın ve ardından için F5 tuşuna seçin **Başlat** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="2ec73-142">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
     <span data-ttu-id="2ec73-143">Program, üç görev her zaman aynı sırada son yok ve hangi son siparişin, bunlar oluşturulan beklemenin sırada mutlaka olmadığından emin doğrulamak için birkaç kez çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="2ec73-143">Run the program several times to verify that the three tasks don’t always finish in the same order and that the order in which they finish isn't necessarily the order in which they’re created and awaited.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2ec73-144">Örnek</span><span class="sxs-lookup"><span data-stu-id="2ec73-144">Example</span></span>  
 <span data-ttu-id="2ec73-145">Aşağıdaki kod, tam örnek içerir.</span><span class="sxs-lookup"><span data-stu-id="2ec73-145">The following code contains the full example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2ec73-146">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2ec73-146">See Also</span></span>  
 [<span data-ttu-id="2ec73-147">İzlenecek yol: Async kullanarak Web'e erişme ve bekleme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2ec73-147">Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)  
 [<span data-ttu-id="2ec73-148">Zaman uyumsuz programlama ile Async ve Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2ec73-148">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/index.md)  
 [<span data-ttu-id="2ec73-149">Nasıl yapılır: Task.WhenAll (Visual Basic) kullanarak zaman uyumsuz izlenecek yolu genişletme</span><span class="sxs-lookup"><span data-stu-id="2ec73-149">How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)
