---
title: Bir Görev Tamamlandıktan Sonra Geri Kalan Zaman Uyumsuz Görevleri İptal Etme
ms.date: 07/20/2015
ms.assetid: c928b5a1-622f-4441-8baf-adca1dde197f
ms.openlocfilehash: be716e98263c865adad3c197236467b2f48d7740
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396681"
---
# <a name="cancel-remaining-async-tasks-after-one-is-complete-visual-basic"></a><span data-ttu-id="617a2-102">Kalan zaman uyumsuz görevleri bir süre tamamlandıktan sonra iptal et (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="617a2-102">Cancel Remaining Async Tasks after One Is Complete (Visual Basic)</span></span>

<span data-ttu-id="617a2-103"><xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>Yöntemini bir ile birlikte kullanarak, bir <xref:System.Threading.CancellationToken> görev tamamlandığında kalan tüm görevleri iptal edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="617a2-103">By using the <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> method together with a <xref:System.Threading.CancellationToken>, you can cancel all remaining tasks when one task is complete.</span></span> <span data-ttu-id="617a2-104">`WhenAny`Yöntemi, bir görev koleksiyonu olan bir bağımsız değişken alır.</span><span class="sxs-lookup"><span data-stu-id="617a2-104">The `WhenAny` method takes an argument that’s a collection of tasks.</span></span> <span data-ttu-id="617a2-105">Yöntemi tüm görevleri başlatır ve tek bir görev döndürür.</span><span class="sxs-lookup"><span data-stu-id="617a2-105">The method starts all the tasks and returns a single task.</span></span> <span data-ttu-id="617a2-106">Koleksiyondaki herhangi bir görev tamamlandığında tek görev tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="617a2-106">The single task is complete when any task in the collection is complete.</span></span>

<span data-ttu-id="617a2-107">Bu örnek, bir iptal belirtecinin `WhenAny` , görev koleksiyonundan sona ermesini ve kalan görevleri iptal etmek için ilk görevi tutmak üzere ile birlikte nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="617a2-107">This example demonstrates how to use a cancellation token in conjunction with `WhenAny` to hold onto the first task to finish from the collection of tasks and to cancel the remaining tasks.</span></span> <span data-ttu-id="617a2-108">Her görev bir Web sitesinin içeriğini indirir.</span><span class="sxs-lookup"><span data-stu-id="617a2-108">Each task downloads the contents of a website.</span></span> <span data-ttu-id="617a2-109">Örnek, tamamlanacak ilk indirmenin içeriklerinin uzunluğunu görüntüler ve diğer indirmeleri iptal eder.</span><span class="sxs-lookup"><span data-stu-id="617a2-109">The example displays the length of the contents of the first download to complete and cancels the other downloads.</span></span>

> [!NOTE]
> <span data-ttu-id="617a2-110">Örnekleri çalıştırmak için, bilgisayarınızda Visual Studio 2012 veya daha yeni bir sürümü ve .NET Framework 4,5 ya da daha yeni bir sürümü yüklü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="617a2-110">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>

## <a name="downloading-the-example"></a><span data-ttu-id="617a2-111">Örnek indiriliyor</span><span class="sxs-lookup"><span data-stu-id="617a2-111">Downloading the Example</span></span>

<span data-ttu-id="617a2-112">Tüm Windows Presentation Foundation (WPF) projesini [zaman uyumsuz örnekten indirebilirsiniz: uygulamanızı Ince ayar](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) yapın ve ardından aşağıdaki adımları izleyin.</span><span class="sxs-lookup"><span data-stu-id="617a2-112">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span></span>

1. <span data-ttu-id="617a2-113">İndirdiğiniz dosyayı sıkıştırmasını açın ve ardından Visual Studio 'Yu başlatın.</span><span class="sxs-lookup"><span data-stu-id="617a2-113">Decompress the file that you downloaded, and then start Visual Studio.</span></span>

2. <span data-ttu-id="617a2-114">Menü çubuğunda **Dosya**, **Aç**, **Proje/çözüm**' ü seçin.</span><span class="sxs-lookup"><span data-stu-id="617a2-114">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>

3. <span data-ttu-id="617a2-115">**Proje Aç** iletişim kutusunda, açtığınız örnek kodu tutan klasörü açın ve ardından AsyncFineTuningVB için çözüm (. sln) dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="617a2-115">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningVB.</span></span>

4. <span data-ttu-id="617a2-116">**Çözüm Gezgini**' de, **ınkıfteronetask** projesinin kısayol menüsünü açın ve ardından **Başlangıç projesi olarak ayarla**' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="617a2-116">In **Solution Explorer**, open the shortcut menu for the **CancelAfterOneTask** project, and then choose **Set as StartUp Project**.</span></span>

5. <span data-ttu-id="617a2-117">Projeyi çalıştırmak için F5 tuşunu seçin.</span><span class="sxs-lookup"><span data-stu-id="617a2-117">Choose the F5 key to run the project.</span></span>

    <span data-ttu-id="617a2-118">Projeyi hata ayıklamadan çalıştırmak için CTRL + F5 tuşlarını seçin.</span><span class="sxs-lookup"><span data-stu-id="617a2-118">Choose the Ctrl+F5 keys to run the project without debugging it.</span></span>

6. <span data-ttu-id="617a2-119">İlk olarak farklı indirmelerin bitmesini doğrulamak için programı birkaç kez çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="617a2-119">Run the program several times to verify that different downloads finish first.</span></span>

<span data-ttu-id="617a2-120">Projeyi indirmek istemiyorsanız, bu konunun sonundaki MainWindow. xaml. vb dosyasını gözden geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="617a2-120">If you don't want to download the project, you can review the MainWindow.xaml.vb file at the end of this topic.</span></span>

## <a name="building-the-example"></a><span data-ttu-id="617a2-121">Örnek oluşturma</span><span class="sxs-lookup"><span data-stu-id="617a2-121">Building the Example</span></span>

<span data-ttu-id="617a2-122">Bu konudaki örnek, [zaman uyumsuz bir görevi Iptal etme](cancel-an-async-task-or-a-list-of-tasks.md) bölümünde geliştirilen projeye veya bir görev listesini iptal etmek Için bir görev listesine ekler.</span><span class="sxs-lookup"><span data-stu-id="617a2-122">The example in this topic adds to the project that's developed in [Cancel an Async Task or a List of Tasks](cancel-an-async-task-or-a-list-of-tasks.md) to cancel a list of tasks.</span></span> <span data-ttu-id="617a2-123">Örnek, aynı kullanıcı arabirimini kullanır, ancak **iptal** düğmesi açıkça kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="617a2-123">The example uses the same UI, although the **Cancel** button isn’t used explicitly.</span></span>

<span data-ttu-id="617a2-124">Örneği kendiniz oluşturmak için, "örneği Indirme" bölümündeki yönergeleri izleyin, ancak **Başlangıç projesi**olarak iptal eden **ınlıftasks** ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="617a2-124">To build the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **CancelAListOfTasks** as the **StartUp Project**.</span></span> <span data-ttu-id="617a2-125">Bu konudaki değişiklikleri bu projeye ekleyin.</span><span class="sxs-lookup"><span data-stu-id="617a2-125">Add the changes in this topic to that project.</span></span>

<span data-ttu-id="617a2-126">Bir Web sitesinin MainWindow. xaml. vb **dosyasında, içindeki** döngüden her bir Web sitesi için işleme adımlarını `AccessTheWebAsync` aşağıdaki zaman uyumsuz metoda taşıyarak geçişi başlatın.</span><span class="sxs-lookup"><span data-stu-id="617a2-126">In the MainWindow.xaml.vb file of the **CancelAListOfTasks** project, start the transition by moving the processing steps for each website from the loop in `AccessTheWebAsync` to the following async method.</span></span>

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

<span data-ttu-id="617a2-127">`AccessTheWebAsync`' De, bu örnek bir sorgu, <xref:System.Linq.Enumerable.ToArray%2A> Yöntem ve bir `WhenAny` dizi görev oluşturmak ve başlatmak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="617a2-127">In `AccessTheWebAsync`, this example uses a query, the  <xref:System.Linq.Enumerable.ToArray%2A> method, and the `WhenAny` method to create and start an array of tasks.</span></span> <span data-ttu-id="617a2-128">Dizi için olan uygulaması, `WhenAny` bir görev dizisinde tamamlamaya ulaşmak üzere ilk görevi değerlendiren tek bir görev döndürür.</span><span class="sxs-lookup"><span data-stu-id="617a2-128">The application of `WhenAny` to the array returns a single task that, when awaited, evaluates to the first task to reach completion in the array of tasks.</span></span>

<span data-ttu-id="617a2-129">İçinde aşağıdaki değişiklikleri yapın `AccessTheWebAsync` .</span><span class="sxs-lookup"><span data-stu-id="617a2-129">Make the following changes in `AccessTheWebAsync`.</span></span> <span data-ttu-id="617a2-130">Yıldız işaretleri kod dosyasındaki değişiklikleri işaretler.</span><span class="sxs-lookup"><span data-stu-id="617a2-130">Asterisks mark the changes in the code file.</span></span>

1. <span data-ttu-id="617a2-131">Döngüyü not edin veya silin.</span><span class="sxs-lookup"><span data-stu-id="617a2-131">Comment out or delete the loop.</span></span>

2. <span data-ttu-id="617a2-132">Yürütüldüğünde, genel görevlerden oluşan bir koleksiyon üreten bir sorgu oluşturun.</span><span class="sxs-lookup"><span data-stu-id="617a2-132">Create a query that, when executed, produces a collection of generic tasks.</span></span> <span data-ttu-id="617a2-133">Her çağrısı `ProcessURLAsync` <xref:System.Threading.Tasks.Task%601> , bir, bir `TResult` tamsayı olan bir döndürür.</span><span class="sxs-lookup"><span data-stu-id="617a2-133">Each call to `ProcessURLAsync` returns a <xref:System.Threading.Tasks.Task%601> where `TResult` is an integer.</span></span>

    ```vb
    ' ***Create a query that, when executed, returns a collection of tasks.
    Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =
        From url In urlList Select ProcessURLAsync(url, client, ct)
    ```

3. <span data-ttu-id="617a2-134">`ToArray`Sorguyu yürütmek ve görevleri başlatmak için çağırın.</span><span class="sxs-lookup"><span data-stu-id="617a2-134">Call `ToArray` to execute the query and start the tasks.</span></span> <span data-ttu-id="617a2-135">Bir `WhenAny` sonraki adımda yönteminin uygulaması sorguyu yürütür ve görevleri kullanmadan başlatır `ToArray` , ancak diğer yöntemler de çalışmayabilir.</span><span class="sxs-lookup"><span data-stu-id="617a2-135">The application of the `WhenAny` method in the next step would execute the query and start the tasks without using `ToArray`, but other methods might not.</span></span> <span data-ttu-id="617a2-136">En güvenli yöntem, sorgunun yürütülmesini açıkça zorlamaktır.</span><span class="sxs-lookup"><span data-stu-id="617a2-136">The safest practice is to force execution of the query explicitly.</span></span>

    ```vb
    ' ***Use ToArray to execute the query and start the download tasks.
    Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()
    ```

4. <span data-ttu-id="617a2-137">`WhenAny`Görevler koleksiyonunda çağırın.</span><span class="sxs-lookup"><span data-stu-id="617a2-137">Call `WhenAny` on the collection of tasks.</span></span> <span data-ttu-id="617a2-138">`WhenAny`bir `Task(Of Task(Of Integer))` veya döndürür `Task<Task<int>>` .</span><span class="sxs-lookup"><span data-stu-id="617a2-138">`WhenAny` returns a `Task(Of Task(Of Integer))` or `Task<Task<int>>`.</span></span>  <span data-ttu-id="617a2-139">Diğer bir deyişle, `WhenAny` tek veya bekleniyor bir görevi döndürür `Task(Of Integer)` `Task<int>` .</span><span class="sxs-lookup"><span data-stu-id="617a2-139">That is, `WhenAny` returns a task that evaluates to a single `Task(Of Integer)` or `Task<int>` when it’s awaited.</span></span> <span data-ttu-id="617a2-140">Bu tek görev, koleksiyondaki ilk görevin sona ermesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="617a2-140">That single task is the first task in the collection to finish.</span></span> <span data-ttu-id="617a2-141">Önce tamamlanan görev öğesine atanır `firstFinishedTask` .</span><span class="sxs-lookup"><span data-stu-id="617a2-141">The task that finished first is assigned to `firstFinishedTask`.</span></span> <span data-ttu-id="617a2-142">Türü, öğesinin `firstFinishedTask` <xref:System.Threading.Tasks.Task%601> `TResult` dönüş türü olduğu için bir tamsayıdır `ProcessURLAsync` .</span><span class="sxs-lookup"><span data-stu-id="617a2-142">The type of `firstFinishedTask` is <xref:System.Threading.Tasks.Task%601> where `TResult` is an integer because that's the return type of `ProcessURLAsync`.</span></span>

    ```vb
    ' ***Call WhenAny and then await the result. The task that finishes
    ' first is assigned to firstFinishedTask.
    Dim firstFinishedTask As Task(Of Integer) = Await Task.WhenAny(downloadTasks)
    ```

5. <span data-ttu-id="617a2-143">Bu örnekte, yalnızca ilk olarak sona erki görevi ilgileniyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="617a2-143">In this example, you’re interested only in the task that finishes first.</span></span> <span data-ttu-id="617a2-144">Bu nedenle, <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> kalan görevleri iptal etmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="617a2-144">Therefore, use <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> to cancel the remaining tasks.</span></span>

    ```vb
    ' ***Cancel the rest of the downloads. You just want the first one.
    cts.Cancel()
    ```

6. <span data-ttu-id="617a2-145">Son olarak, `firstFinishedTask` indirilen içeriğin uzunluğunu almak için Await.</span><span class="sxs-lookup"><span data-stu-id="617a2-145">Finally, await `firstFinishedTask` to retrieve the length of the downloaded content.</span></span>

    ```vb
    Dim length = Await firstFinishedTask
    resultsTextBox.Text &= vbCrLf & $"Length of the downloaded website:  {length}" & vbCrLf
    ```

<span data-ttu-id="617a2-146">İlk olarak farklı indirmelerin bitmesini doğrulamak için programı birkaç kez çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="617a2-146">Run the program several times to verify that different downloads finish first.</span></span>

## <a name="complete-example"></a><span data-ttu-id="617a2-147">Tam Örnek</span><span class="sxs-lookup"><span data-stu-id="617a2-147">Complete Example</span></span>

<span data-ttu-id="617a2-148">Aşağıdaki kod, örnek için tüm MainWindow. xaml. vb veya MainWindow.xaml.cs dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="617a2-148">The following code is the complete MainWindow.xaml.vb or MainWindow.xaml.cs file for the example.</span></span> <span data-ttu-id="617a2-149">Yıldız işaretleri bu örnek için eklenen öğeleri işaretler.</span><span class="sxs-lookup"><span data-stu-id="617a2-149">Asterisks mark the elements that were added for this example.</span></span>

<span data-ttu-id="617a2-150">İçin bir başvuru eklemeniz gerektiğini unutmayın <xref:System.Net.Http> .</span><span class="sxs-lookup"><span data-stu-id="617a2-150">Notice that you must add a reference for <xref:System.Net.Http>.</span></span>

<span data-ttu-id="617a2-151">Projeyi [zaman uyumsuz örnekten indirebilirsiniz: uygulamanızı hassas bir şekilde ayarlama](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span><span class="sxs-lookup"><span data-stu-id="617a2-151">You can download the project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>

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

## <a name="see-also"></a><span data-ttu-id="617a2-152">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="617a2-152">See also</span></span>

- <xref:System.Threading.Tasks.Task.WhenAny%2A>
- [<span data-ttu-id="617a2-153">Zaman uyumsuz uygulamanızda ince ayar yapma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="617a2-153">Fine-Tuning Your Async Application (Visual Basic)</span></span>](fine-tuning-your-async-application.md)
- [<span data-ttu-id="617a2-154">Async ve await ile zaman uyumsuz programlama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="617a2-154">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](index.md)
- [<span data-ttu-id="617a2-155">Zaman uyumsuz örnek: uygulamanıza Ince ayar yapma</span><span class="sxs-lookup"><span data-stu-id="617a2-155">Async Sample: Fine Tuning Your Application</span></span>](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
