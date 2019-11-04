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
# <a name="cancel-remaining-async-tasks-after-one-is-complete-visual-basic"></a><span data-ttu-id="45b54-102">Kalan zaman uyumsuz görevleri bir süre tamamlandıktan sonra iptal et (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="45b54-102">Cancel Remaining Async Tasks after One Is Complete (Visual Basic)</span></span>

<span data-ttu-id="45b54-103"><xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> yöntemini bir <xref:System.Threading.CancellationToken>ile birlikte kullanarak, bir görev tamamlandığında kalan tüm görevleri iptal edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="45b54-103">By using the <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> method together with a <xref:System.Threading.CancellationToken>, you can cancel all remaining tasks when one task is complete.</span></span> <span data-ttu-id="45b54-104">`WhenAny` yöntemi bir görev koleksiyonu olan bir bağımsız değişken alır.</span><span class="sxs-lookup"><span data-stu-id="45b54-104">The `WhenAny` method takes an argument that’s a collection of tasks.</span></span> <span data-ttu-id="45b54-105">Yöntemi tüm görevleri başlatır ve tek bir görev döndürür.</span><span class="sxs-lookup"><span data-stu-id="45b54-105">The method starts all the tasks and returns a single task.</span></span> <span data-ttu-id="45b54-106">Koleksiyondaki herhangi bir görev tamamlandığında tek görev tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="45b54-106">The single task is complete when any task in the collection is complete.</span></span>

<span data-ttu-id="45b54-107">Bu örnek, bir iptal belirtecinin, görev koleksiyonundan sona ermesi ve kalan görevleri iptal etmek için ilk görevi tutmak üzere `WhenAny` ile birlikte nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="45b54-107">This example demonstrates how to use a cancellation token in conjunction with `WhenAny` to hold onto the first task to finish from the collection of tasks and to cancel the remaining tasks.</span></span> <span data-ttu-id="45b54-108">Her görev bir Web sitesinin içeriğini indirir.</span><span class="sxs-lookup"><span data-stu-id="45b54-108">Each task downloads the contents of a website.</span></span> <span data-ttu-id="45b54-109">Örnek, tamamlanacak ilk indirmenin içeriklerinin uzunluğunu görüntüler ve diğer indirmeleri iptal eder.</span><span class="sxs-lookup"><span data-stu-id="45b54-109">The example displays the length of the contents of the first download to complete and cancels the other downloads.</span></span>

> [!NOTE]
> <span data-ttu-id="45b54-110">Örnekleri çalıştırmak için, bilgisayarınızda Visual Studio 2012 veya daha yeni bir sürümü ve .NET Framework 4,5 ya da daha yeni bir sürümü yüklü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="45b54-110">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>

## <a name="downloading-the-example"></a><span data-ttu-id="45b54-111">Örnek indiriliyor</span><span class="sxs-lookup"><span data-stu-id="45b54-111">Downloading the Example</span></span>

<span data-ttu-id="45b54-112">Tüm Windows Presentation Foundation (WPF) projesini [zaman uyumsuz örnekten indirebilirsiniz: uygulamanızı Ince ayar](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) yapın ve ardından aşağıdaki adımları izleyin.</span><span class="sxs-lookup"><span data-stu-id="45b54-112">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span></span>

1. <span data-ttu-id="45b54-113">İndirdiğiniz dosyayı sıkıştırmasını açın ve ardından Visual Studio 'Yu başlatın.</span><span class="sxs-lookup"><span data-stu-id="45b54-113">Decompress the file that you downloaded, and then start Visual Studio.</span></span>

2. <span data-ttu-id="45b54-114">Menü çubuğunda **Dosya**, **Aç**, **Proje/çözüm**' ü seçin.</span><span class="sxs-lookup"><span data-stu-id="45b54-114">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>

3. <span data-ttu-id="45b54-115">**Proje Aç** iletişim kutusunda, açtığınız örnek kodu tutan klasörü açın ve ardından AsyncFineTuningVB için çözüm (. sln) dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="45b54-115">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningVB.</span></span>

4. <span data-ttu-id="45b54-116">**Çözüm Gezgini**' de, **ınkıfteronetask** projesinin kısayol menüsünü açın ve ardından **Başlangıç projesi olarak ayarla**' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="45b54-116">In **Solution Explorer**, open the shortcut menu for the **CancelAfterOneTask** project, and then choose **Set as StartUp Project**.</span></span>

5. <span data-ttu-id="45b54-117">Projeyi çalıştırmak için F5 tuşunu seçin.</span><span class="sxs-lookup"><span data-stu-id="45b54-117">Choose the F5 key to run the project.</span></span>

    <span data-ttu-id="45b54-118">Projeyi hata ayıklamadan çalıştırmak için CTRL + F5 tuşlarını seçin.</span><span class="sxs-lookup"><span data-stu-id="45b54-118">Choose the Ctrl+F5 keys to run the project without debugging it.</span></span>

6. <span data-ttu-id="45b54-119">İlk olarak farklı indirmelerin bitmesini doğrulamak için programı birkaç kez çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="45b54-119">Run the program several times to verify that different downloads finish first.</span></span>

<span data-ttu-id="45b54-120">Projeyi indirmek istemiyorsanız, bu konunun sonundaki MainWindow. xaml. vb dosyasını gözden geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="45b54-120">If you don't want to download the project, you can review the MainWindow.xaml.vb file at the end of this topic.</span></span>

## <a name="building-the-example"></a><span data-ttu-id="45b54-121">Örnek oluşturma</span><span class="sxs-lookup"><span data-stu-id="45b54-121">Building the Example</span></span>

<span data-ttu-id="45b54-122">Bu konudaki örnek, [zaman uyumsuz bir görevi Iptal etme](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md) bölümünde geliştirilen projeye veya bir görev listesini iptal etmek Için bir görev listesine ekler.</span><span class="sxs-lookup"><span data-stu-id="45b54-122">The example in this topic adds to the project that's developed in [Cancel an Async Task or a List of Tasks](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md) to cancel a list of tasks.</span></span> <span data-ttu-id="45b54-123">Örnek, aynı kullanıcı arabirimini kullanır, ancak **iptal** düğmesi açıkça kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="45b54-123">The example uses the same UI, although the **Cancel** button isn’t used explicitly.</span></span>

<span data-ttu-id="45b54-124">Örneği kendiniz oluşturmak için, "örneği Indirme" bölümündeki yönergeleri izleyin, ancak **Başlangıç projesi**olarak iptal eden **ınlıftasks** ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="45b54-124">To build the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **CancelAListOfTasks** as the **StartUp Project**.</span></span> <span data-ttu-id="45b54-125">Bu konudaki değişiklikleri bu projeye ekleyin.</span><span class="sxs-lookup"><span data-stu-id="45b54-125">Add the changes in this topic to that project.</span></span>

<span data-ttu-id="45b54-126">' **De, bir** Web sitesi için işleme adımlarını aşağıdaki zaman uyumsuz metoda taşıyarak, bu işlem için, ' ' ın MainWindow. xaml. vb dosyasında `AccessTheWebAsync` geçişi başlatın.</span><span class="sxs-lookup"><span data-stu-id="45b54-126">In the MainWindow.xaml.vb file of the **CancelAListOfTasks** project, start the transition by moving the processing steps for each website from the loop in `AccessTheWebAsync` to the following async method.</span></span>

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

<span data-ttu-id="45b54-127">`AccessTheWebAsync`, bu örnek bir sorgu, <xref:System.Linq.Enumerable.ToArray%2A> yöntemi ve bir dizi görevi oluşturmak ve başlatmak için `WhenAny` yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="45b54-127">In `AccessTheWebAsync`, this example uses a query, the  <xref:System.Linq.Enumerable.ToArray%2A> method, and the `WhenAny` method to create and start an array of tasks.</span></span> <span data-ttu-id="45b54-128">Dizi `WhenAny` uygulaması, görev dizisinde tamamlamaya ulaşmak için ilk görevi değerlendiren tek bir görev döndürür.</span><span class="sxs-lookup"><span data-stu-id="45b54-128">The application of `WhenAny` to the array returns a single task that, when awaited, evaluates to the first task to reach completion in the array of tasks.</span></span>

<span data-ttu-id="45b54-129">`AccessTheWebAsync`' de aşağıdaki değişiklikleri yapın.</span><span class="sxs-lookup"><span data-stu-id="45b54-129">Make the following changes in `AccessTheWebAsync`.</span></span> <span data-ttu-id="45b54-130">Yıldız işaretleri kod dosyasındaki değişiklikleri işaretler.</span><span class="sxs-lookup"><span data-stu-id="45b54-130">Asterisks mark the changes in the code file.</span></span>

1. <span data-ttu-id="45b54-131">Döngüyü not edin veya silin.</span><span class="sxs-lookup"><span data-stu-id="45b54-131">Comment out or delete the loop.</span></span>

2. <span data-ttu-id="45b54-132">Yürütüldüğünde, genel görevlerden oluşan bir koleksiyon üreten bir sorgu oluşturun.</span><span class="sxs-lookup"><span data-stu-id="45b54-132">Create a query that, when executed, produces a collection of generic tasks.</span></span> <span data-ttu-id="45b54-133">Her `ProcessURLAsync` çağrısı, `TResult` bir tamsayı olduğu <xref:System.Threading.Tasks.Task%601> döndürür.</span><span class="sxs-lookup"><span data-stu-id="45b54-133">Each call to `ProcessURLAsync` returns a <xref:System.Threading.Tasks.Task%601> where `TResult` is an integer.</span></span>

    ```vb
    ' ***Create a query that, when executed, returns a collection of tasks.
    Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =
        From url In urlList Select ProcessURLAsync(url, client, ct)
    ```

3. <span data-ttu-id="45b54-134">Sorguyu yürütmek ve görevleri başlatmak için `ToArray` çağırın.</span><span class="sxs-lookup"><span data-stu-id="45b54-134">Call `ToArray` to execute the query and start the tasks.</span></span> <span data-ttu-id="45b54-135">Sonraki adımda `WhenAny` yönteminin uygulaması, sorguyu yürütür ve `ToArray`kullanmadan görevleri başlatır, ancak diğer yöntemler de çalışmayabilir.</span><span class="sxs-lookup"><span data-stu-id="45b54-135">The application of the `WhenAny` method in the next step would execute the query and start the tasks without using `ToArray`, but other methods might not.</span></span> <span data-ttu-id="45b54-136">En güvenli yöntem, sorgunun yürütülmesini açıkça zorlamaktır.</span><span class="sxs-lookup"><span data-stu-id="45b54-136">The safest practice is to force execution of the query explicitly.</span></span>

    ```vb
    ' ***Use ToArray to execute the query and start the download tasks.
    Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()
    ```

4. <span data-ttu-id="45b54-137">Görevler koleksiyonunda `WhenAny` çağırın.</span><span class="sxs-lookup"><span data-stu-id="45b54-137">Call `WhenAny` on the collection of tasks.</span></span> <span data-ttu-id="45b54-138">`WhenAny` `Task(Of Task(Of Integer))` veya `Task<Task<int>>`döndürür.</span><span class="sxs-lookup"><span data-stu-id="45b54-138">`WhenAny` returns a `Task(Of Task(Of Integer))` or `Task<Task<int>>`.</span></span>  <span data-ttu-id="45b54-139">Diğer bir deyişle `WhenAny`, tek bir `Task(Of Integer)` değerlendiren veya `Task<int>` beklendiğinde bir görevi döndürüyor.</span><span class="sxs-lookup"><span data-stu-id="45b54-139">That is, `WhenAny` returns a task that evaluates to a single `Task(Of Integer)` or `Task<int>` when it’s awaited.</span></span> <span data-ttu-id="45b54-140">Bu tek görev, koleksiyondaki ilk görevin sona ermesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="45b54-140">That single task is the first task in the collection to finish.</span></span> <span data-ttu-id="45b54-141">Önce tamamlanan görev `firstFinishedTask`atanır.</span><span class="sxs-lookup"><span data-stu-id="45b54-141">The task that finished first is assigned to `firstFinishedTask`.</span></span> <span data-ttu-id="45b54-142">`firstFinishedTask` türü, `ProcessURLAsync`dönüş türü olduğundan `TResult` bir tamsayı olduğu <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="45b54-142">The type of `firstFinishedTask` is <xref:System.Threading.Tasks.Task%601> where `TResult` is an integer because that's the return type of `ProcessURLAsync`.</span></span>

    ```vb
    ' ***Call WhenAny and then await the result. The task that finishes
    ' first is assigned to firstFinishedTask.
    Dim firstFinishedTask As Task(Of Integer) = Await Task.WhenAny(downloadTasks)
    ```

5. <span data-ttu-id="45b54-143">Bu örnekte, yalnızca ilk olarak sona erki görevi ilgileniyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="45b54-143">In this example, you’re interested only in the task that finishes first.</span></span> <span data-ttu-id="45b54-144">Bu nedenle, kalan görevleri iptal etmek için <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> kullanın.</span><span class="sxs-lookup"><span data-stu-id="45b54-144">Therefore, use <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> to cancel the remaining tasks.</span></span>

    ```vb
    ' ***Cancel the rest of the downloads. You just want the first one.
    cts.Cancel()
    ```

6. <span data-ttu-id="45b54-145">Son olarak, indirilen içeriğin uzunluğunu almak için `firstFinishedTask` await.</span><span class="sxs-lookup"><span data-stu-id="45b54-145">Finally, await `firstFinishedTask` to retrieve the length of the downloaded content.</span></span>

    ```vb
    Dim length = Await firstFinishedTask
    resultsTextBox.Text &= vbCrLf & $"Length of the downloaded website:  {length}" & vbCrLf
    ```

<span data-ttu-id="45b54-146">İlk olarak farklı indirmelerin bitmesini doğrulamak için programı birkaç kez çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="45b54-146">Run the program several times to verify that different downloads finish first.</span></span>

## <a name="complete-example"></a><span data-ttu-id="45b54-147">Tam Örnek</span><span class="sxs-lookup"><span data-stu-id="45b54-147">Complete Example</span></span>

<span data-ttu-id="45b54-148">Aşağıdaki kod, örnek için tüm MainWindow. xaml. vb veya MainWindow.xaml.cs dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="45b54-148">The following code is the complete MainWindow.xaml.vb or MainWindow.xaml.cs file for the example.</span></span> <span data-ttu-id="45b54-149">Yıldız işaretleri bu örnek için eklenen öğeleri işaretler.</span><span class="sxs-lookup"><span data-stu-id="45b54-149">Asterisks mark the elements that were added for this example.</span></span>

<span data-ttu-id="45b54-150"><xref:System.Net.Http>için bir başvuru eklemeniz gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="45b54-150">Notice that you must add a reference for <xref:System.Net.Http>.</span></span>

<span data-ttu-id="45b54-151">Projeyi [zaman uyumsuz örnekten indirebilirsiniz: uygulamanızı hassas bir şekilde ayarlama](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span><span class="sxs-lookup"><span data-stu-id="45b54-151">You can download the project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>

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

## <a name="see-also"></a><span data-ttu-id="45b54-152">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="45b54-152">See also</span></span>

- <xref:System.Threading.Tasks.Task.WhenAny%2A>
- [<span data-ttu-id="45b54-153">Zaman uyumsuz uygulamanızda ince ayar yapma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="45b54-153">Fine-Tuning Your Async Application (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md)
- [<span data-ttu-id="45b54-154">Async ve await ile zaman uyumsuz programlama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="45b54-154">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/index.md)
- [<span data-ttu-id="45b54-155">Zaman uyumsuz örnek: uygulamanıza Ince ayar yapma</span><span class="sxs-lookup"><span data-stu-id="45b54-155">Async Sample: Fine Tuning Your Application</span></span>](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
