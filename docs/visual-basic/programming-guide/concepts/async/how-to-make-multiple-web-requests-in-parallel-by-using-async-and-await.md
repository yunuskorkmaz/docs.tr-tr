---
title: 'Nasıl yapılır: Async ve await kullanarak birden çok Web Isteğini paralel hale getirme (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: a894b99b-7cfd-4a38-adfb-20d24f986730
ms.openlocfilehash: 9241a54b4b0d1a8871ef496d44e1e6db5581af7b
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583160"
---
# <a name="how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await-visual-basic"></a><span data-ttu-id="9f21b-102">Nasıl yapılır: Async ve await kullanarak birden çok Web Isteğini paralel hale getirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9f21b-102">How to: Make Multiple Web Requests in Parallel by Using Async and Await (Visual Basic)</span></span>

<span data-ttu-id="9f21b-103">Zaman uyumsuz bir yöntemde görevler oluşturulduğunda başlatılır.</span><span class="sxs-lookup"><span data-stu-id="9f21b-103">In an async method, tasks are started when they’re created.</span></span> <span data-ttu-id="9f21b-104">[Await](../../../../visual-basic/language-reference/operators/await-operator.md) işleci, görev bitene kadar işlemin devam edemediği yöntemdeki noktada göreve uygulanır.</span><span class="sxs-lookup"><span data-stu-id="9f21b-104">The [Await](../../../../visual-basic/language-reference/operators/await-operator.md) operator is applied to the task at the point in the method where processing can’t continue until the task finishes.</span></span> <span data-ttu-id="9f21b-105">Aşağıdaki örnekte gösterildiği gibi, genellikle bir görev, oluşturulduktan hemen sonra beklediğinde.</span><span class="sxs-lookup"><span data-stu-id="9f21b-105">Often a task is awaited as soon as it’s created, as the following example shows.</span></span>

```vb
Dim result = Await someWebAccessMethodAsync(url)
```

<span data-ttu-id="9f21b-106">Ancak, programın gerçekleştirmeye yönelik başka bir işi olması durumunda görevin tamamlanmasına bağlı olmaması durumunda görevi bekleyen görev oluşturmayı ayırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9f21b-106">However, you can separate creating the task from awaiting the task if your program has other work to accomplish that doesn’t depend on the completion of the task.</span></span>

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

<span data-ttu-id="9f21b-107">Bir görevi başlatma ve bekleme arasında başka görevler de başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9f21b-107">Between starting a task and awaiting it, you can start other tasks.</span></span> <span data-ttu-id="9f21b-108">Ek görevler dolaylı olarak paralel olarak çalışır, ancak ek iş parçacığı oluşturulmaz.</span><span class="sxs-lookup"><span data-stu-id="9f21b-108">The additional tasks implicitly run in parallel, but no additional threads are created.</span></span>

<span data-ttu-id="9f21b-109">Aşağıdaki program, üç zaman uyumsuz Web yüklemesi başlatır ve ardından bunların çağrıldıkları sırayla bekler.</span><span class="sxs-lookup"><span data-stu-id="9f21b-109">The following program starts three asynchronous web downloads and then awaits them in the order in which they’re called.</span></span> <span data-ttu-id="9f21b-110">Programı çalıştırdığınızda, görevlerin Oluşturulma sırasında ve bekledikleri sırada her zaman bitmediğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="9f21b-110">Notice, when you run the program, that the tasks don’t always finish in the order in which they’re created and awaited.</span></span> <span data-ttu-id="9f21b-111">Bunlar oluşturulduğunda çalışmaya başlar ve Yöntem await ifadelerine ulaşmadan önce bir veya daha fazla görev bitebilirler.</span><span class="sxs-lookup"><span data-stu-id="9f21b-111">They start to run when they’re created, and one or more of the tasks might finish before the method reaches the await expressions.</span></span>

> [!NOTE]
> <span data-ttu-id="9f21b-112">Bu projeyi tamamlayabilmeniz için, bilgisayarınızda Visual Studio 2012 veya üzeri ve .NET Framework 4,5 veya üzeri yüklü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9f21b-112">To complete this project, you must have Visual Studio 2012 or higher and the .NET Framework 4.5 or higher installed on your computer.</span></span>

<span data-ttu-id="9f21b-113">Aynı anda birden çok görevi Başlatan başka bir örnek için, bkz. [nasıl yapılır: Task. WhenAll kullanarak zaman uyumsuz Izlenecek yolu genişletme (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span><span class="sxs-lookup"><span data-stu-id="9f21b-113">For another example that starts multiple tasks at the same time, see [How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span></span>

<span data-ttu-id="9f21b-114">Bu örnek için kodu [Geliştirici kodu örneklerinden](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e)indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9f21b-114">You can download the code for this example from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e).</span></span>

### <a name="to-set-up-the-project"></a><span data-ttu-id="9f21b-115">Projeyi ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="9f21b-115">To set up the project</span></span>

1. <span data-ttu-id="9f21b-116">WPF uygulaması ayarlamak için aşağıdaki adımları izleyin.</span><span class="sxs-lookup"><span data-stu-id="9f21b-116">To set up a WPF application, complete the following steps.</span></span> <span data-ttu-id="9f21b-117">[Izlenecek yol: Async ve await (Visual Basic) kullanarak Web 'e erişmek](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)için bu adımlarla ilgili ayrıntılı yönergeleri bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9f21b-117">You can find detailed instructions for these steps in [Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span>

    - <span data-ttu-id="9f21b-118">Metin kutusu ve düğme içeren bir WPF uygulaması oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9f21b-118">Create a WPF application that contains a text box and a button.</span></span> <span data-ttu-id="9f21b-119">Düğmeyi `startButton` adlandırın ve metin kutusu `resultsTextBox` adlandırın.</span><span class="sxs-lookup"><span data-stu-id="9f21b-119">Name the button `startButton`, and name the text box `resultsTextBox`.</span></span>

    - <span data-ttu-id="9f21b-120">@No__t_0 için bir başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="9f21b-120">Add a reference for <xref:System.Net.Http>.</span></span>

    - <span data-ttu-id="9f21b-121">MainWindow. xaml. vb dosyasında, `System.Net.Http` için `Imports` bir ifade ekleyin.</span><span class="sxs-lookup"><span data-stu-id="9f21b-121">In the MainWindow.xaml.vb file, add an `Imports` statement for `System.Net.Http`.</span></span>

### <a name="to-add-the-code"></a><span data-ttu-id="9f21b-122">Kodu eklemek için</span><span class="sxs-lookup"><span data-stu-id="9f21b-122">To add the code</span></span>

1. <span data-ttu-id="9f21b-123">MainWindow. xaml tasarım penceresinde, MainWindow. xaml. vb ' de `startButton_Click` olay işleyicisini oluşturmak için düğmeye çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="9f21b-123">In the design window, MainWindow.xaml, double-click the button to create the `startButton_Click` event handler in MainWindow.xaml.vb.</span></span>

2. <span data-ttu-id="9f21b-124">Aşağıdaki kodu kopyalayın ve MainWindow. xaml. vb içindeki `startButton_Click` gövdesine yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="9f21b-124">Copy the following code, and paste it into the body of `startButton_Click` in MainWindow.xaml.vb.</span></span>

    ```vb
    resultsTextBox.Clear()
    Await CreateMultipleTasksAsync()
    resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."
    ```

     <span data-ttu-id="9f21b-125">Kod, uygulamayı yönlendiren `CreateMultipleTasksAsync` bir zaman uyumsuz yöntemi çağırır.</span><span class="sxs-lookup"><span data-stu-id="9f21b-125">The code calls an asynchronous method, `CreateMultipleTasksAsync`, which drives the application.</span></span>

3. <span data-ttu-id="9f21b-126">Aşağıdaki destek yöntemlerini projeye ekleyin:</span><span class="sxs-lookup"><span data-stu-id="9f21b-126">Add the following support methods to the project:</span></span>

    - <span data-ttu-id="9f21b-127">`ProcessURLAsync`, bir Web sitesinin içeriğini bir bayt dizisi olarak indirmek için bir <xref:System.Net.Http.HttpClient> yöntemi kullanır.</span><span class="sxs-lookup"><span data-stu-id="9f21b-127">`ProcessURLAsync` uses an <xref:System.Net.Http.HttpClient> method to download the contents of a website as a byte array.</span></span> <span data-ttu-id="9f21b-128">@No__t_0 support yöntemi, sonra dizinin uzunluğunu gösterir ve döndürür.</span><span class="sxs-lookup"><span data-stu-id="9f21b-128">The support method, `ProcessURLAsync` then displays and returns the length of the array.</span></span>

    - <span data-ttu-id="9f21b-129">`DisplayResults` her bir URL için bayt dizisindeki bayt sayısını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="9f21b-129">`DisplayResults` displays the number of bytes in the byte array for each URL.</span></span> <span data-ttu-id="9f21b-130">Bu ekranda, her görevin indirilmesi tamamlandığında gösterilir.</span><span class="sxs-lookup"><span data-stu-id="9f21b-130">This display shows when each task has finished downloading.</span></span>

     <span data-ttu-id="9f21b-131">Aşağıdaki yöntemleri kopyalayın ve MainWindow. xaml. vb ' de `startButton_Click` olay işleyicisinden sonra yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="9f21b-131">Copy the following methods, and paste them after the `startButton_Click` event handler in MainWindow.xaml.vb.</span></span>

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

4. <span data-ttu-id="9f21b-132">Son olarak, aşağıdaki adımları gerçekleştiren `CreateMultipleTasksAsync` yöntemini tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="9f21b-132">Finally, define method `CreateMultipleTasksAsync`, which performs the following steps.</span></span>

    - <span data-ttu-id="9f21b-133">Yöntemi, `ProcessURLAsync` <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> yöntemine erişmeniz gereken `HttpClient` nesnesini bildirir.</span><span class="sxs-lookup"><span data-stu-id="9f21b-133">The method declares an `HttpClient` object,which you need  to access method <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> in `ProcessURLAsync`.</span></span>

    - <span data-ttu-id="9f21b-134">Yöntemi <xref:System.Threading.Tasks.Task%601> türünde üç görev oluşturur ve başlatır; burada `TResult` bir tamsayıdır.</span><span class="sxs-lookup"><span data-stu-id="9f21b-134">The method creates and starts three tasks of type <xref:System.Threading.Tasks.Task%601>, where `TResult` is an integer.</span></span> <span data-ttu-id="9f21b-135">Her görev bittiğinde `DisplayResults` görevin URL 'sini ve indirilen içeriklerin uzunluğunu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="9f21b-135">As each task finishes, `DisplayResults` displays the task's URL and the length of the downloaded contents.</span></span> <span data-ttu-id="9f21b-136">Görevler zaman uyumsuz olarak çalıştığından, sonuçların göründüğü sıra, bildirildiği sırayla farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="9f21b-136">Because the tasks are running asynchronously, the order in which the results appear might differ from the order in which they were declared.</span></span>

    - <span data-ttu-id="9f21b-137">Yöntemi her görevin tamamlanmasını bekler.</span><span class="sxs-lookup"><span data-stu-id="9f21b-137">The method awaits the completion of each task.</span></span> <span data-ttu-id="9f21b-138">Her bir `Await` işleci, beklenen görev tamamlanana kadar `CreateMultipleTasksAsync` yürütmeyi askıya alır.</span><span class="sxs-lookup"><span data-stu-id="9f21b-138">Each `Await` operator suspends execution of `CreateMultipleTasksAsync` until the awaited task is finished.</span></span> <span data-ttu-id="9f21b-139">İşleci, her tamamlanan görevden `ProcessURLAsync` çağrısından dönüş değerini de alır.</span><span class="sxs-lookup"><span data-stu-id="9f21b-139">The operator also retrieves the return value from the call to `ProcessURLAsync` from each completed task.</span></span>

    - <span data-ttu-id="9f21b-140">Görevler tamamlandığında ve tamsayı değerleri alınırsa, yöntemi web sitelerinin uzunluklarını toplar ve sonucu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="9f21b-140">When the tasks have been completed and the integer values have been retrieved, the method sums the lengths of the websites and displays the result.</span></span>

     <span data-ttu-id="9f21b-141">Aşağıdaki yöntemi kopyalayın ve çözümünüze yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="9f21b-141">Copy the following method, and paste it into your solution.</span></span>

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

5. <span data-ttu-id="9f21b-142">Programı çalıştırmak için F5 tuşunu seçin ve sonra **Başlat** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="9f21b-142">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>

     <span data-ttu-id="9f21b-143">Üç görevin her zaman aynı sırada bitmeyeceğini ve bunların tamamların oluşturulma sırası ve bekledikleri sıra olması gerektiğini doğrulamak için programı birkaç kez çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="9f21b-143">Run the program several times to verify that the three tasks don’t always finish in the same order and that the order in which they finish isn't necessarily the order in which they’re created and awaited.</span></span>

## <a name="example"></a><span data-ttu-id="9f21b-144">Örnek</span><span class="sxs-lookup"><span data-stu-id="9f21b-144">Example</span></span>

<span data-ttu-id="9f21b-145">Aşağıdaki kod tam örneği içerir.</span><span class="sxs-lookup"><span data-stu-id="9f21b-145">The following code contains the full example.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="9f21b-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9f21b-146">See also</span></span>

- [<span data-ttu-id="9f21b-147">İzlenecek yol: Async ve await kullanarak Web 'e erişme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9f21b-147">Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="9f21b-148">Async ve await ile zaman uyumsuz programlama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9f21b-148">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/index.md)
- [<span data-ttu-id="9f21b-149">Nasıl yapılır: Task. WhenAll kullanarak zaman uyumsuz Izlenecek yolu genişletme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9f21b-149">How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)
