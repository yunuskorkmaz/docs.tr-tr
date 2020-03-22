---
title: Birden Çok Zaman Uyumsuz Görev Başlatma ve Görevleri Tamamlandıkça İşleme
ms.date: 07/20/2015
ms.assetid: 57ffb748-af40-4794-bedd-bdb7fea062de
ms.openlocfilehash: b14171196a95e9a6a12f6b13f6f17d3cfe352bce
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266852"
---
# <a name="start-multiple-async-tasks-and-process-them-as-they-complete-visual-basic"></a><span data-ttu-id="37955-102">Birden Çok Async Görevi Başlatın ve Tamamladıkları Gibi İşleyin (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="37955-102">Start Multiple Async Tasks and Process Them As They Complete (Visual Basic)</span></span>
<span data-ttu-id="37955-103">Kullanarak, <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>birden çok görevi aynı anda başlatabilir ve başlatıldıkları sırada işlemek yerine tamamlandıkları gibi tek tek işleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="37955-103">By using <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>, you can start multiple tasks at the same time and process them one by one as they’re completed rather than process them in the order in which they're started.</span></span>  
  
 <span data-ttu-id="37955-104">Aşağıdaki örnekte, görev koleksiyonu oluşturmak için bir sorgu kullanır.</span><span class="sxs-lookup"><span data-stu-id="37955-104">The following example uses a query to create a collection of tasks.</span></span> <span data-ttu-id="37955-105">Her görev, belirli bir web sitesinin içeriğini indirir.</span><span class="sxs-lookup"><span data-stu-id="37955-105">Each task downloads the contents of a specified website.</span></span> <span data-ttu-id="37955-106">Bir while döngüsünün her yinelemesinde, önce `WhenAny` karşıdan yüklemeyi tamamlayan görevler koleksiyonundaki görevi döndürecek beklenen bir çağrı.</span><span class="sxs-lookup"><span data-stu-id="37955-106">In each iteration of a while loop, an awaited call to `WhenAny` returns the task in the collection of tasks that finishes its download first.</span></span> <span data-ttu-id="37955-107">Bu görev koleksiyondan kaldırılır ve işlenir.</span><span class="sxs-lookup"><span data-stu-id="37955-107">That task is removed from the collection and processed.</span></span> <span data-ttu-id="37955-108">Döngü, koleksiyon başka görev içermeyene kadar yinelenir.</span><span class="sxs-lookup"><span data-stu-id="37955-108">The loop repeats until the collection contains no more tasks.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="37955-109">Örnekleri çalıştırmak için Visual Studio 2012 veya daha yeni ve .NET Framework 4.5 veya daha yeni bilgisayarınıza yüklü olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="37955-109">To run the examples, you must have Visual Studio 2012 or newer and  the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
## <a name="downloading-the-example"></a><span data-ttu-id="37955-110">Örneği İndirme</span><span class="sxs-lookup"><span data-stu-id="37955-110">Downloading the Example</span></span>  
 <span data-ttu-id="37955-111">Windows Presentation Foundation (WPF) projesinin tamamını [Async Sample: Fine Tuning Application'dan](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) indirebilir ve ardından aşağıdaki adımları izleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="37955-111">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span></span>  
  
1. <span data-ttu-id="37955-112">İndirdiğiniz dosyayı sıkıştırın ve Visual Studio'yu başlatın.</span><span class="sxs-lookup"><span data-stu-id="37955-112">Decompress the file that you downloaded, and then start Visual Studio.</span></span>  
  
2. <span data-ttu-id="37955-113">Menü çubuğunda **Dosya**, **Aç**, **Proje/Çözüm'ü**seçin.</span><span class="sxs-lookup"><span data-stu-id="37955-113">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
3. <span data-ttu-id="37955-114">**Projeyi Aç** iletişim kutusunda, sıkıştırdığınız örnek kodu tutan klasörü açın ve ardından AsyncFineTuningVB için çözüm (.sln) dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="37955-114">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningVB.</span></span>  
  
4. <span data-ttu-id="37955-115">**Çözüm Gezgini'nde,** **ProcessTasksAsTheyFinish** projesi için kısayol menüsünü açın ve ardından **StartUp Project olarak ayarla'yı**seçin.</span><span class="sxs-lookup"><span data-stu-id="37955-115">In **Solution Explorer**, open the shortcut menu for the **ProcessTasksAsTheyFinish** project, and then choose **Set as StartUp Project**.</span></span>  
  
5. <span data-ttu-id="37955-116">Projeyi çalıştırmak için F5 tuşunu seçin.</span><span class="sxs-lookup"><span data-stu-id="37955-116">Choose the F5 key to run the project.</span></span>  
  
     <span data-ttu-id="37955-117">Projeyi hata ayıklamadan çalıştırmak için Ctrl+F5 tuşlarını seçin.</span><span class="sxs-lookup"><span data-stu-id="37955-117">Choose the Ctrl+F5 keys to run the project without debugging it.</span></span>  
  
6. <span data-ttu-id="37955-118">İndirilen uzunlukların her zaman aynı sırada görünmediğini doğrulamak için projeyi birkaç kez çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="37955-118">Run the project several times to verify that the downloaded lengths don't always appear in the same order.</span></span>  
  
 <span data-ttu-id="37955-119">Projeyi indirmek istemiyorsanız, bu konunun sonundaki MainWindow.xaml.vb dosyasını inceleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="37955-119">If you don't want to download the project, you can review the MainWindow.xaml.vb file at the end of this topic.</span></span>  
  
## <a name="building-the-example"></a><span data-ttu-id="37955-120">Örnek Oluşturma</span><span class="sxs-lookup"><span data-stu-id="37955-120">Building the Example</span></span>  
 <span data-ttu-id="37955-121">Bu örnek, [Bir Tamamlandıktan Sonra Kalan Async Görevlerini İptal Etme (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md) olarak geliştirilen ve aynı UI'yi kullanan koda ekler.</span><span class="sxs-lookup"><span data-stu-id="37955-121">This example adds to the code that’s developed in [Cancel Remaining Async Tasks after One Is Complete (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md) and uses the same UI.</span></span>  
  
 <span data-ttu-id="37955-122">Örneği adım adım oluşturmak için, "Örneği İndirme" bölümündeki yönergeleri izleyin, ancak **StartUp Project**olarak **CancelAfterOneTask'ı** seçin.</span><span class="sxs-lookup"><span data-stu-id="37955-122">To build the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **CancelAfterOneTask** as the **StartUp Project**.</span></span> <span data-ttu-id="37955-123">Bu konudaki değişiklikleri bu `AccessTheWebAsync` projedeki yönteme ekleyin.</span><span class="sxs-lookup"><span data-stu-id="37955-123">Add the changes in this topic to the `AccessTheWebAsync` method in that project.</span></span> <span data-ttu-id="37955-124">Değişiklikler yıldız işaretleriyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="37955-124">The changes are marked with asterisks.</span></span>  
  
 <span data-ttu-id="37955-125">**CancelAfterOneTask** projesi zaten yürütüldüğünde bir görev koleksiyonu oluşturan bir sorgu içerir.</span><span class="sxs-lookup"><span data-stu-id="37955-125">The **CancelAfterOneTask** project already includes a query that, when executed, creates a collection of tasks.</span></span> <span data-ttu-id="37955-126">Aşağıdaki `ProcessURLAsync` koddaki her arama <xref:System.Threading.Tasks.Task%601> bir `TResult` tamsayı yıkıntır döndürür.</span><span class="sxs-lookup"><span data-stu-id="37955-126">Each call to `ProcessURLAsync` in the following code returns a <xref:System.Threading.Tasks.Task%601> where `TResult` is an integer.</span></span>  
  
```vb  
Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =  
    From url In urlList Select ProcessURLAsync(url, client, ct)  
```  
  
 <span data-ttu-id="37955-127">Projenin MainWindow.xaml.vb dosyasında yöntemde `AccessTheWebAsync` aşağıdaki değişiklikleri yapın.</span><span class="sxs-lookup"><span data-stu-id="37955-127">In the MainWindow.xaml.vb file of the  project, make the following changes to the `AccessTheWebAsync` method.</span></span>  
  
- <span data-ttu-id="37955-128"><xref:System.Linq.Enumerable.ToArray%2A>Yerine uygulayarak <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> sorguyu yürütün</span><span class="sxs-lookup"><span data-stu-id="37955-128">Execute the query by applying <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> instead of <xref:System.Linq.Enumerable.ToArray%2A>.</span></span>  
  
    ```vb  
    Dim downloadTasks As List(Of Task(Of Integer)) = downloadTasksQuery.ToList()  
    ```  
  
- <span data-ttu-id="37955-129">Koleksiyondaki her görev için aşağıdaki adımları gerçekleştiren bir while döngüsü ekleyin.</span><span class="sxs-lookup"><span data-stu-id="37955-129">Add a while loop that performs the following steps for each task in the collection.</span></span>  
  
    1. <span data-ttu-id="37955-130">İndirmeyi tamamlamak `WhenAny` için koleksiyondaki ilk görevi belirlemek için bir çağrı bekler.</span><span class="sxs-lookup"><span data-stu-id="37955-130">Awaits a call to `WhenAny` to identify the first task in the collection to finish its download.</span></span>  
  
        ```vb  
        Dim firstFinishedTask As Task(Of Integer) = Await Task.WhenAny(downloadTasks)  
        ```  
  
    2. <span data-ttu-id="37955-131">Bu görevi koleksiyondan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="37955-131">Removes that task from the collection.</span></span>  
  
        ```vb  
        downloadTasks.Remove(firstFinishedTask)  
        ```  
  
    3. <span data-ttu-id="37955-132">Bekliyor `firstFinishedTask`, bir çağrı ile `ProcessURLAsync`döndürülür .</span><span class="sxs-lookup"><span data-stu-id="37955-132">Awaits `firstFinishedTask`, which is returned by a call to `ProcessURLAsync`.</span></span> <span data-ttu-id="37955-133">`firstFinishedTask` Değişken bir <xref:System.Threading.Tasks.Task%601> tamsayı `TReturn` dır.</span><span class="sxs-lookup"><span data-stu-id="37955-133">The `firstFinishedTask` variable is a <xref:System.Threading.Tasks.Task%601> where `TReturn` is an integer.</span></span> <span data-ttu-id="37955-134">Görev zaten tamamlandı, ancak aşağıdaki örnekte görüldüğü gibi, indirilen web sitesinin uzunluğunu almak için onu bekliyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="37955-134">The task is already complete, but you await it to retrieve the length of the downloaded website, as the following example shows.</span></span>  
  
        ```vb  
        Dim length = Await firstFinishedTask  
        resultsTextBox.Text &= String.Format(vbCrLf & "Length of the downloaded website:  {0}" & vbCrLf, length)  
        ```  
  
 <span data-ttu-id="37955-135">İndirilen uzunlukların her zaman aynı sırada görünmediğini doğrulamak için projeyi birkaç kez çalıştırmalısınız.</span><span class="sxs-lookup"><span data-stu-id="37955-135">You should run the project several times to verify that the downloaded lengths don't always appear in the same order.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="37955-136">Az sayıda `WhenAny` görev içeren sorunları çözmek için örnekte açıklandığı gibi bir döngüde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="37955-136">You can use `WhenAny` in a loop, as described in the example, to solve problems that involve a small number of tasks.</span></span> <span data-ttu-id="37955-137">Ancak, işlemek için çok sayıda göreviniz varsa, diğer yaklaşımlar daha verimlidir.</span><span class="sxs-lookup"><span data-stu-id="37955-137">However, other approaches are more efficient if you have a large number of tasks to process.</span></span> <span data-ttu-id="37955-138">Daha fazla bilgi ve örnek için, [tamamlandıkça İşleme Görevleri'ne](https://devblogs.microsoft.com/pfxteam/processing-tasks-as-they-complete/)bakın.</span><span class="sxs-lookup"><span data-stu-id="37955-138">For more information and examples, see [Processing Tasks as they complete](https://devblogs.microsoft.com/pfxteam/processing-tasks-as-they-complete/).</span></span>  
  
## <a name="complete-example"></a><span data-ttu-id="37955-139">Tam Örnek</span><span class="sxs-lookup"><span data-stu-id="37955-139">Complete Example</span></span>  
 <span data-ttu-id="37955-140">Aşağıdaki kod, örnek için MainWindow.xaml.vb dosyasının tam metnidir.</span><span class="sxs-lookup"><span data-stu-id="37955-140">The following code is the complete text of the MainWindow.xaml.vb file for the example.</span></span> <span data-ttu-id="37955-141">Yıldız işaretleri, bu örnek için eklenen öğeleri işaretler.</span><span class="sxs-lookup"><span data-stu-id="37955-141">Asterisks mark the elements that were added for this example.</span></span>  
  
 <span data-ttu-id="37955-142">Için bir başvuru eklemeniz <xref:System.Net.Http>gerektiğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="37955-142">Notice that you must add a reference for <xref:System.Net.Http>.</span></span>  
  
 <span data-ttu-id="37955-143">Projeyi [Async Sample: Fine Tuning Application'dan](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="37955-143">You can download the project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>  
  
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
            resultsTextBox.Text &= vbCrLf & "Downloads complete."  
  
        Catch ex As OperationCanceledException  
            resultsTextBox.Text &= vbCrLf & "Downloads canceled." & vbCrLf  
  
        Catch ex As Exception  
            resultsTextBox.Text &= vbCrLf & "Downloads failed." & vbCrLf  
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
  
        ' ***Create a query that, when executed, returns a collection of tasks.  
        Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =  
            From url In urlList Select ProcessURLAsync(url, client, ct)  
  
        ' ***Use ToList to execute the query and start the download tasks.
        Dim downloadTasks As List(Of Task(Of Integer)) = downloadTasksQuery.ToList()  
  
        ' ***Add a loop to process the tasks one at a time until none remain.  
        While downloadTasks.Count > 0  
            ' ***Identify the first task that completes.  
            Dim firstFinishedTask As Task(Of Integer) = Await Task.WhenAny(downloadTasks)  
  
            ' ***Remove the selected task from the list so that you don't  
            ' process it more than once.  
            downloadTasks.Remove(firstFinishedTask)  
  
            ' ***Await the first completed task and display the results.  
            Dim length = Await firstFinishedTask  
            resultsTextBox.Text &= String.Format(vbCrLf & "Length of the downloaded website:  {0}" & vbCrLf, length)  
        End While  
  
    End Function  
  
    ' Bundle the processing steps for a website into one async method.  
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
  
' Length of the download:  226093  
' Length of the download:  412588  
' Length of the download:  175490  
' Length of the download:  204890  
' Length of the download:  158855  
' Length of the download:  145790  
' Length of the download:  44908  
' Downloads complete.  
```  
  
## <a name="see-also"></a><span data-ttu-id="37955-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="37955-144">See also</span></span>

- <xref:System.Threading.Tasks.Task.WhenAny%2A>
- [<span data-ttu-id="37955-145">Async Uygulamanızda İnce Ayar (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="37955-145">Fine-Tuning Your Async Application (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md)
- [<span data-ttu-id="37955-146">Async ve Await ile Asynchronous Programlama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="37955-146">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/index.md)
- [<span data-ttu-id="37955-147">Async Örnek: Uygulamanızı İyi Ayar</span><span class="sxs-lookup"><span data-stu-id="37955-147">Async Sample: Fine Tuning Your Application</span></span>](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
