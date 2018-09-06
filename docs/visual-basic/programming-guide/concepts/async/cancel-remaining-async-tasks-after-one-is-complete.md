---
title: Tam (Visual Basic) biridir sonra geri kalan zaman uyumsuz görevleri iptal etme
ms.date: 07/20/2015
ms.assetid: c928b5a1-622f-4441-8baf-adca1dde197f
ms.openlocfilehash: 5dab0c4aa14710fe78d2473675aea8b8c8bb73b9
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43874803"
---
# <a name="cancel-remaining-async-tasks-after-one-is-complete-visual-basic"></a><span data-ttu-id="a4885-102">Tam (Visual Basic) biridir sonra geri kalan zaman uyumsuz görevleri iptal etme</span><span class="sxs-lookup"><span data-stu-id="a4885-102">Cancel Remaining Async Tasks after One Is Complete (Visual Basic)</span></span>
<span data-ttu-id="a4885-103">Kullanarak <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> yöntemi ile birlikte bir <xref:System.Threading.CancellationToken>, bir görev tamamlandığında kalan tüm görevleri iptal edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a4885-103">By using the <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> method together with a <xref:System.Threading.CancellationToken>, you can cancel all remaining tasks when one task is complete.</span></span> <span data-ttu-id="a4885-104">`WhenAny` Yöntemi bir görev koleksiyonu olan bir bağımsız değişken alır.</span><span class="sxs-lookup"><span data-stu-id="a4885-104">The `WhenAny` method takes an argument that’s a collection of tasks.</span></span> <span data-ttu-id="a4885-105">Bu yöntem tüm görevleri başlatır ve tek bir görev döndürür.</span><span class="sxs-lookup"><span data-stu-id="a4885-105">The method starts all the tasks and returns a single task.</span></span> <span data-ttu-id="a4885-106">Koleksiyondaki herhangi bir görev tamamlandığında tek bir görev tamamlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="a4885-106">The single task is complete when any task in the collection is complete.</span></span>  
  
 <span data-ttu-id="a4885-107">Bu örnek ile birlikte bir iptal belirteci kullanmayı gösteren `WhenAny` bitirilecek ilk göreve görevleri koleksiyonundan tamamlanması ve kalan görevleri iptal etmek için tutacak.</span><span class="sxs-lookup"><span data-stu-id="a4885-107">This example demonstrates how to use a cancellation token in conjunction with `WhenAny` to hold onto the first task to finish from the collection of tasks and to cancel the remaining tasks.</span></span> <span data-ttu-id="a4885-108">Her görev bir Web sitesinin içeriklerini karşıdan yükler.</span><span class="sxs-lookup"><span data-stu-id="a4885-108">Each task downloads the contents of a website.</span></span> <span data-ttu-id="a4885-109">Bu örnek, tamamlanacak ilk yüklemenin içeriğinin uzunluğunu görüntüler ve diğer yüklemeleri iptal eder.</span><span class="sxs-lookup"><span data-stu-id="a4885-109">The example displays the length of the contents of the first download to complete and cancels the other downloads.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a4885-110">Yeni bilgisayarınızda yüklü veya örnekleri çalıştırmak için Visual Studio 2012 veya daha yeni ve .NET Framework 4.5 yüklü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a4885-110">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
## <a name="downloading-the-example"></a><span data-ttu-id="a4885-111">Örneği indirme</span><span class="sxs-lookup"><span data-stu-id="a4885-111">Downloading the Example</span></span>  
 <span data-ttu-id="a4885-112">Tüm Windows Presentation Foundation (WPF) projeden indirebileceğiniz [zaman uyumsuz örneği: ince uygulamanıza](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) ve sonra aşağıdaki adımları izleyin.</span><span class="sxs-lookup"><span data-stu-id="a4885-112">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span></span>  
  
1.  <span data-ttu-id="a4885-113">İndirdiğiniz dosyanın sıkıştırmasını açın ve sonra Visual Studio'yu başlatın.</span><span class="sxs-lookup"><span data-stu-id="a4885-113">Decompress the file that you downloaded, and then start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="a4885-114">Menü çubuğunda, **dosya**, **açık**, **proje/çözüm**.</span><span class="sxs-lookup"><span data-stu-id="a4885-114">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
3.  <span data-ttu-id="a4885-115">İçinde **Proje Aç** iletişim kutusunda, açtığınız örnek kodu barındıran klasörü açın ve ardından AsyncFineTuningVB için çözüm (.sln) dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="a4885-115">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningVB.</span></span>  
  
4.  <span data-ttu-id="a4885-116">İçinde **Çözüm Gezgini**, kısayol menüsünü açın **CancelAfterOneTask** proje ve ardından **başlangıç projesi olarak ayarla**.</span><span class="sxs-lookup"><span data-stu-id="a4885-116">In **Solution Explorer**, open the shortcut menu for the **CancelAfterOneTask** project, and then choose **Set as StartUp Project**.</span></span>  
  
5.  <span data-ttu-id="a4885-117">Projeyi çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="a4885-117">Choose the F5 key to run the project.</span></span>  
  
     <span data-ttu-id="a4885-118">Projeyi hata ayıklama olmadan çalıştırmak için Ctrl + F5 tuşlarını seçin.</span><span class="sxs-lookup"><span data-stu-id="a4885-118">Choose the Ctrl+F5 keys to run the project without debugging it.</span></span>  
  
6.  <span data-ttu-id="a4885-119">Programın farklı yüklemeleri ilk son doğrulamak için birkaç kez çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="a4885-119">Run the program several times to verify that different downloads finish first.</span></span>  
  
 <span data-ttu-id="a4885-120">Projeyi indirmek istemiyorsanız, bu konunun sonunda MainWindow.xaml.vb dosyasını gözden geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a4885-120">If you don't want to download the project, you can review the MainWindow.xaml.vb file at the end of this topic.</span></span>  
  
## <a name="building-the-example"></a><span data-ttu-id="a4885-121">Örneği oluşturma</span><span class="sxs-lookup"><span data-stu-id="a4885-121">Building the Example</span></span>  
 <span data-ttu-id="a4885-122">Bu konudaki örnek içinde geliştirilen projeye ekler [zaman uyumsuz bir görev veya görevleri listeleyin iptal](https://msdn.microsoft.com/library/d6e4e801-df64-4705-98fc-df725a577fb0) Görevler listesini iptal etme.</span><span class="sxs-lookup"><span data-stu-id="a4885-122">The example in this topic adds to the project that's developed in [Cancel an Async Task or a List of Tasks](https://msdn.microsoft.com/library/d6e4e801-df64-4705-98fc-df725a577fb0) to cancel a list of tasks.</span></span> <span data-ttu-id="a4885-123">Örnekte aynı Arabirim kullanılmaktadır, ancak **iptal** düğmesi açıkça kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="a4885-123">The example uses the same UI, although the **Cancel** button isn’t used explicitly.</span></span>  
  
 <span data-ttu-id="a4885-124">Örneği oluşturmak için kendinize, adım adım "Örneği indirme" bölümündeki yönergeleri izleyin, ancak seçin **CancelAListOfTasks** olarak **başlangıç projesi**.</span><span class="sxs-lookup"><span data-stu-id="a4885-124">To build the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **CancelAListOfTasks** as the **StartUp Project**.</span></span> <span data-ttu-id="a4885-125">Bu konuda, değişiklikleri bu projeye ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a4885-125">Add the changes in this topic to that project.</span></span>  
  
 <span data-ttu-id="a4885-126">MainWindow.xaml.vb dosyasındaki **CancelAListOfTasks** proje, her Web sitesi için işlenen adımları döngüden taşıyarak geçişi başlatın `AccessTheWebAsync` aşağıdaki zaman uyumsuz yönteme.</span><span class="sxs-lookup"><span data-stu-id="a4885-126">In the MainWindow.xaml.vb file of the **CancelAListOfTasks** project, start the transition by moving the processing steps for each website from the loop in `AccessTheWebAsync` to the following async method.</span></span>  
  
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
  
 <span data-ttu-id="a4885-127">İçinde `AccessTheWebAsync`, bu örnekte sorgu, <xref:System.Linq.Enumerable.ToArray%2A> yöntemi ve `WhenAny` oluşturmak ve bir dizi görev başlamak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="a4885-127">In `AccessTheWebAsync`, this example uses a query, the  <xref:System.Linq.Enumerable.ToArray%2A> method, and the `WhenAny` method to create and start an array of tasks.</span></span> <span data-ttu-id="a4885-128">Uygulamayı `WhenAny` dizisi için tek bir görev, bekletildiğinde döndürür dizideki görevlerin tamamlanmasına ulaşmak için ilk görev değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="a4885-128">The application of `WhenAny` to the array returns a single task that, when awaited, evaluates to the first task to reach completion in the array of tasks.</span></span>  
  
 <span data-ttu-id="a4885-129">Aşağıdaki değişiklikleri yapın `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="a4885-129">Make the following changes in `AccessTheWebAsync`.</span></span> <span data-ttu-id="a4885-130">Yıldız işaretleri kod dosyasındaki değişiklikleri işaretler.</span><span class="sxs-lookup"><span data-stu-id="a4885-130">Asterisks mark the changes in the code file.</span></span>  
  
1.  <span data-ttu-id="a4885-131">Açıklama satırı yapın veya döngü silin.</span><span class="sxs-lookup"><span data-stu-id="a4885-131">Comment out or delete the loop.</span></span>  
  
2.  <span data-ttu-id="a4885-132">Yürütüldüğünde, bir sorgu, oluşturun bir genel görev koleksiyonu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a4885-132">Create a query that, when executed, produces a collection of generic tasks.</span></span> <span data-ttu-id="a4885-133">Her çağrı `ProcessURLAsync` döndürür bir <xref:System.Threading.Tasks.Task%601> burada `TResult` bir tamsayıdır.</span><span class="sxs-lookup"><span data-stu-id="a4885-133">Each call to `ProcessURLAsync` returns a <xref:System.Threading.Tasks.Task%601> where `TResult` is an integer.</span></span>  
  
    ```vb  
    ' ***Create a query that, when executed, returns a collection of tasks.  
    Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =  
        From url In urlList Select ProcessURLAsync(url, client, ct)  
    ```  
  
3.  <span data-ttu-id="a4885-134">Çağrı `ToArray` sorguyu ve görevleri başlatın.</span><span class="sxs-lookup"><span data-stu-id="a4885-134">Call `ToArray` to execute the query and start the tasks.</span></span> <span data-ttu-id="a4885-135">Uygulamayı `WhenAny` sonraki adımda yöntemi ve sorguyu kullanmadan başlangıç görevleri `ToArray`, ancak diğer yöntemler bunu yapmayabilir.</span><span class="sxs-lookup"><span data-stu-id="a4885-135">The application of the `WhenAny` method in the next step would execute the query and start the tasks without using `ToArray`, but other methods might not.</span></span> <span data-ttu-id="a4885-136">En güvenli yöntem sorgu yürütmesini açıkça zorla sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="a4885-136">The safest practice is to force execution of the query explicitly.</span></span>  
  
    ```vb  
    ' ***Use ToArray to execute the query and start the download tasks.   
    Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()  
    ```  
  
4.  <span data-ttu-id="a4885-137">Çağrı `WhenAny` üzerinde bir görev koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="a4885-137">Call `WhenAny` on the collection of tasks.</span></span> <span data-ttu-id="a4885-138">`WhenAny` döndürür bir `Task(Of Task(Of Integer))` veya `Task<Task<int>>`.</span><span class="sxs-lookup"><span data-stu-id="a4885-138">`WhenAny` returns a `Task(Of Task(Of Integer))` or `Task<Task<int>>`.</span></span>  <span data-ttu-id="a4885-139">Diğer bir deyişle, `WhenAny` değerlendiren bir görev için tek bir döndüren `Task(Of Integer)` veya `Task<int>` beklendiği zaman.</span><span class="sxs-lookup"><span data-stu-id="a4885-139">That is, `WhenAny` returns a task that evaluates to a single `Task(Of Integer)` or `Task<int>` when it’s awaited.</span></span> <span data-ttu-id="a4885-140">Bu tek görev tamamlamak için koleksiyondaki ilk görevdir.</span><span class="sxs-lookup"><span data-stu-id="a4885-140">That single task is the first task in the collection to finish.</span></span> <span data-ttu-id="a4885-141">İlk önce Tamamlanan görevin atandığı `firstFinishedTask`.</span><span class="sxs-lookup"><span data-stu-id="a4885-141">The task that finished first is assigned to `firstFinishedTask`.</span></span> <span data-ttu-id="a4885-142">Türünü `firstFinishedTask` olduğu <xref:System.Threading.Tasks.Task%601> burada `TResult` dönüş türü olan bir tamsayı çünkü `ProcessURLAsync`.</span><span class="sxs-lookup"><span data-stu-id="a4885-142">The type of `firstFinishedTask` is <xref:System.Threading.Tasks.Task%601> where `TResult` is an integer because that's the return type of `ProcessURLAsync`.</span></span>  
  
```vb  
' ***Call WhenAny and then await the result. The task that finishes   
' first is assigned to firstFinishedTask.  
Dim firstFinishedTask As Task(Of Integer) = Await Task.WhenAny(downloadTasks)  
```  
  
5.  <span data-ttu-id="a4885-143">Bu örnekte, önce sona eren yalnızca görevle ilgilendiniz.</span><span class="sxs-lookup"><span data-stu-id="a4885-143">In this example, you’re interested only in the task that finishes first.</span></span> <span data-ttu-id="a4885-144">Bu nedenle, <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> kalan görevleri iptal etmek için.</span><span class="sxs-lookup"><span data-stu-id="a4885-144">Therefore, use <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> to cancel the remaining tasks.</span></span>  
  
```vb  
' ***Cancel the rest of the downloads. You just want the first one.  
cts.Cancel()  
```  
  
6.  <span data-ttu-id="a4885-145">Son olarak, await `firstFinishedTask` karşıdan yüklenen içeriğin uzunluğunu almak için.</span><span class="sxs-lookup"><span data-stu-id="a4885-145">Finally, await `firstFinishedTask` to retrieve the length of the downloaded content.</span></span>  
  
```vb  
Dim length = Await firstFinishedTask  
resultsTextBox.Text &= String.Format(vbCrLf & "Length of the downloaded website:  {0}" & vbCrLf, length)  
```  
  
 <span data-ttu-id="a4885-146">Programın farklı yüklemeleri ilk son doğrulamak için birkaç kez çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="a4885-146">Run the program several times to verify that different downloads finish first.</span></span>  
  
## <a name="complete-example"></a><span data-ttu-id="a4885-147">Tam Örnek</span><span class="sxs-lookup"><span data-stu-id="a4885-147">Complete Example</span></span>  
 <span data-ttu-id="a4885-148">Aşağıdaki kod örneği için tam MainWindow.xaml.vb veya MainWindow.xaml.cs dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="a4885-148">The following code is the complete MainWindow.xaml.vb or MainWindow.xaml.cs file for the example.</span></span> <span data-ttu-id="a4885-149">Yıldız işaretleri, bu örnek için eklenen öğeleri işaretler.</span><span class="sxs-lookup"><span data-stu-id="a4885-149">Asterisks mark the elements that were added for this example.</span></span>  
  
 <span data-ttu-id="a4885-150">İçin bir başvuru eklemeniz gerektiğini unutmayın <xref:System.Net.Http>.</span><span class="sxs-lookup"><span data-stu-id="a4885-150">Notice that you must add a reference for <xref:System.Net.Http>.</span></span>  
  
 <span data-ttu-id="a4885-151">Projeden indirebileceğiniz [zaman uyumsuz örneği: ince uygulamanıza](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span><span class="sxs-lookup"><span data-stu-id="a4885-151">You can download the project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>  
  
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
        ''        String.Format(vbCrLf & "Length of the downloaded string: {0}." & vbCrLf, urlContents.Length)  
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
        resultsTextBox.Text &= String.Format(vbCrLf & "Length of the downloaded website:  {0}" & vbCrLf, length)  
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
                "http://msdn.microsoft.com",  
                "http://msdn.microsoft.com/library/hh290138.aspx",  
                "http://msdn.microsoft.com/library/hh290140.aspx",  
                "http://msdn.microsoft.com/library/dd470362.aspx",  
                "http://msdn.microsoft.com/library/aa578028.aspx",  
                "http://msdn.microsoft.com/library/ms404677.aspx",  
                "http://msdn.microsoft.com/library/ff730837.aspx"  
            }  
        Return urls  
    End Function  
  
End Class  
  
' Sample output:  
  
' Length of the downloaded website:  158856  
  
' Download complete.  
```  
  
## <a name="see-also"></a><span data-ttu-id="a4885-152">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a4885-152">See Also</span></span>  
 <xref:System.Threading.Tasks.Task.WhenAny%2A>  
 [<span data-ttu-id="a4885-153">(Visual Basic) Async uygulamanızda hassas ayar yapma</span><span class="sxs-lookup"><span data-stu-id="a4885-153">Fine-Tuning Your Async Application (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md)  
 [<span data-ttu-id="a4885-154">Zaman uyumsuz programlama ile Async ve Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a4885-154">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/index.md)  
 [<span data-ttu-id="a4885-155">Zaman uyumsuz örneği: Uygulamanıza ince</span><span class="sxs-lookup"><span data-stu-id="a4885-155">Async Sample: Fine Tuning Your Application</span></span>](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
