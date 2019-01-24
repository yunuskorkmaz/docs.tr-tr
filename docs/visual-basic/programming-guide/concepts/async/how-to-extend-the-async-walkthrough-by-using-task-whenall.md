---
title: 'Nasıl yapılır: (Visual Basic) Task.WhenAll kullanarak zaman uyumsuz izlenecek yolu genişletme'
ms.date: 07/20/2015
ms.assetid: c06d386d-e996-4da9-bf3d-05a3b6c0a258
ms.openlocfilehash: 80fbe824d62b439fe6f015704bc32194e104cd85
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54619311"
---
# <a name="how-to-extend-the-async-walkthrough-by-using-taskwhenall-visual-basic"></a><span data-ttu-id="7b120-102">Nasıl yapılır: (Visual Basic) Task.WhenAll kullanarak zaman uyumsuz izlenecek yolu genişletme</span><span class="sxs-lookup"><span data-stu-id="7b120-102">How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)</span></span>
<span data-ttu-id="7b120-103">İçinde zaman uyumsuz çözümün performansını artırabilirsiniz [izlenecek yol: Web kullanarak Async ve Await (Visual Basic) tarafından erişim](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md) kullanarak <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="7b120-103">You can improve the performance of the async solution in [Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md) by using the <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="7b120-104">Bu yöntem, zaman uyumsuz olarak görevleri topluluğu temsil edilen birden çok zaman uyumsuz işlemler bekler.</span><span class="sxs-lookup"><span data-stu-id="7b120-104">This method asynchronously awaits multiple asynchronous operations, which are represented as a collection of tasks.</span></span>  
  
 <span data-ttu-id="7b120-105">Web sitelerinin indirme hızlarının farklı izlenecek yolda etmiş olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7b120-105">You might have noticed in the walkthrough that the websites download at different rates.</span></span> <span data-ttu-id="7b120-106">Bazen, Web siteleri, kalan tüm indirmeleri geciktirir çok yavaş biridir.</span><span class="sxs-lookup"><span data-stu-id="7b120-106">Sometimes one of the websites is very slow, which delays all the remaining downloads.</span></span> <span data-ttu-id="7b120-107">Anlatımda oluşturduğunuz zaman uyumsuz çözümleri çalıştırdığınızda, program kolayca beklemek istemiyorsanız, ancak tüm indirmeleri aynı anda başlatmak ve devam etmek için beklemenize gerek kalmadan daha hızlı indirmeler izin vermek için daha iyi bir seçenek olacaktır sona erdirebilirsiniz ait  ertelendi.</span><span class="sxs-lookup"><span data-stu-id="7b120-107">When you run the asynchronous solutions that you build in the walkthrough, you can end the program easily if you don't want to wait, but a better option would be to start all the downloads at the same time and let faster downloads continue without waiting for the one that’s delayed.</span></span>  
  
 <span data-ttu-id="7b120-108">Uyguladığınız `Task.WhenAll` yöntemi için bir görev koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="7b120-108">You apply the `Task.WhenAll` method to a collection of tasks.</span></span> <span data-ttu-id="7b120-109">Uygulamayı `WhenAll` koleksiyondaki her görev tamamlanıncaya kadar tam olmayan tek bir görev döndürür.</span><span class="sxs-lookup"><span data-stu-id="7b120-109">The application of `WhenAll` returns a single task that isn’t complete until every task in the collection is completed.</span></span> <span data-ttu-id="7b120-110">Görevler paralel olarak çalışır gibigörünür, ancak hiçbir ek iş parçacığı oluşturulmaz.</span><span class="sxs-lookup"><span data-stu-id="7b120-110">The tasks appear to run in parallel, but no additional threads are created.</span></span> <span data-ttu-id="7b120-111">Görevler herhangi bir sırada tamamlayabilir.</span><span class="sxs-lookup"><span data-stu-id="7b120-111">The tasks can complete in any order.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7b120-112">Aşağıdaki yordamlar içinde geliştirilen zaman uyumsuz uygulamaların uzantılarını açıklamaktadır [izlenecek yol: Zaman uyumsuz kullanarak Web'e erişme ve Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="7b120-112">The following procedures describe extensions to the async applications that are developed in [Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span> <span data-ttu-id="7b120-113">İzlenecek yolu tamamlayarak veya kodu indiriliyor tarafından uygulamalar geliştirebilirsiniz [geliştirici kodu örnekleri](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).</span><span class="sxs-lookup"><span data-stu-id="7b120-113">You can develop the applications by either completing the walkthrough or downloading the code from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).</span></span>  
>   
>  <span data-ttu-id="7b120-114">Örneği çalıştırmak için Visual Studio 2012 olmalıdır veya üzeri yüklü.</span><span class="sxs-lookup"><span data-stu-id="7b120-114">To run the example, you must have Visual Studio 2012 or later installed on your computer.</span></span>  
  
### <a name="to-add-taskwhenall-to-your-geturlcontentsasync-solution"></a><span data-ttu-id="7b120-115">GetURLContentsAsync çözümünüze Task.WhenAll eklemek için</span><span class="sxs-lookup"><span data-stu-id="7b120-115">To add Task.WhenAll to your GetURLContentsAsync solution</span></span>  
  
1.  <span data-ttu-id="7b120-116">Ekleme `ProcessURLAsync` yöntemi içinde geliştirilen ilk uygulamaya [izlenecek yol: Zaman uyumsuz kullanarak Web'e erişme ve Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="7b120-116">Add the `ProcessURLAsync` method to the first application that's developed in [Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span>  
  
    -   <span data-ttu-id="7b120-117">Koddan indirdiyseniz [geliştirici kodu örnekleri](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f), AsyncWalkthrough projesini açın ve ardından eklemek `ProcessURLAsync` MainWindow.xaml.vb dosyasına.</span><span class="sxs-lookup"><span data-stu-id="7b120-117">If you downloaded the code from  [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f), open the AsyncWalkthrough project, and then add `ProcessURLAsync` to the MainWindow.xaml.vb file.</span></span>  
  
    -   <span data-ttu-id="7b120-118">İzlenecek yolu tamamlayarak kodu geliştirdiyseniz, ekleme `ProcessURLAsync` içeren uygulamaya `GetURLContentsAsync` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="7b120-118">If you developed the code by completing the walkthrough, add `ProcessURLAsync` to the application that includes the `GetURLContentsAsync` method.</span></span> <span data-ttu-id="7b120-119">Bu uygulama için MainWindow.xaml.vb dosyası "Tam kod örnekleri" izlenecek yoldan"bölümündeki ilk örnektir.</span><span class="sxs-lookup"><span data-stu-id="7b120-119">The MainWindow.xaml.vb file for this application is the first example in the "Complete Code Examples from the Walkthrough" section.</span></span>  
  
     <span data-ttu-id="7b120-120">`ProcessURLAsync` Yöntem gövdesindeki eylemleri birleştirir `For Each` içinde döngü `SumPageSizesAsync` özgün izlenecek yolda.</span><span class="sxs-lookup"><span data-stu-id="7b120-120">The `ProcessURLAsync` method consolidates the actions in the body of the `For Each` loop in `SumPageSizesAsync` in the original walkthrough.</span></span> <span data-ttu-id="7b120-121">Yöntemi zaman uyumsuz olarak bir bayt dizisi olarak belirtilen bir Web sitesinin içeriklerini karşıdan yükler ve ardından görüntüler ve bayt dizisinin uzunluğunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="7b120-121">The method asynchronously downloads the contents of a specified website as a byte array, and then displays and returns the length of the byte array.</span></span>  
  
    ```vb  
    Private Async Function ProcessURLAsync(url As String) As Task(Of Integer)  
  
        Dim byteArray = Await GetURLContentsAsync(url)  
        DisplayResults(url, byteArray)  
        Return byteArray.Length  
    End Function  
    ```  
  
2.  <span data-ttu-id="7b120-122">Açıklama satırı yapın veya silin `For Each` içinde döngü `SumPageSizesAsync`aşağıdaki kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="7b120-122">Comment out or delete the `For Each` loop in `SumPageSizesAsync`, as the following code shows.</span></span>  
  
    ```vb  
    'Dim total = 0  
    'For Each url In urlList  
  
    '    Dim urlContents As Byte() = Await GetURLContentsAsync(url)  
  
    '    ' The previous line abbreviates the following two assignment statements.  
  
    '    ' GetURLContentsAsync returns a task. At completion, the task  
    '    ' produces a byte array.  
    '    'Dim getContentsTask As Task(Of Byte()) = GetURLContentsAsync(url)  
    '    'Dim urlContents As Byte() = Await getContentsTask  
  
    '    DisplayResults(url, urlContents)  
  
    '    ' Update the total.  
    '    total += urlContents.Length  
    'Next  
    ```  
  
3.  <span data-ttu-id="7b120-123">Bir görev koleksiyonu oluşturun.</span><span class="sxs-lookup"><span data-stu-id="7b120-123">Create a collection of tasks.</span></span> <span data-ttu-id="7b120-124">Aşağıdaki kodu tanımlayan bir [sorgu](../../../../visual-basic/programming-guide/concepts/linq/index.md) , tarafından yürütüldüğünde <xref:System.Linq.Enumerable.ToArray%2A> yöntemi, her bir Web sitesinin içeriklerini indiren bir görev koleksiyonunu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7b120-124">The following code defines a [query](../../../../visual-basic/programming-guide/concepts/linq/index.md) that, when executed by the <xref:System.Linq.Enumerable.ToArray%2A> method, creates a collection of tasks that download the contents of each website.</span></span> <span data-ttu-id="7b120-125">Sorgu çalışırken görevler başlatılır.</span><span class="sxs-lookup"><span data-stu-id="7b120-125">The tasks are started when the query is evaluated.</span></span>  
  
     <span data-ttu-id="7b120-126">Yöntemine aşağıdaki kodu ekleyin `SumPageSizesAsync` bildiriminin `urlList`.</span><span class="sxs-lookup"><span data-stu-id="7b120-126">Add the following code to method `SumPageSizesAsync` after the declaration of `urlList`.</span></span>  
  
    ```vb  
    ' Create a query.   
    Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =  
        From url In urlList Select ProcessURLAsync(url)  
  
    ' Use ToArray to execute the query and start the download tasks.  
    Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()  
    ```  
  
4.  <span data-ttu-id="7b120-127">Uygulama `Task.WhenAll` görevler koleksiyonuna `downloadTasks`.</span><span class="sxs-lookup"><span data-stu-id="7b120-127">Apply `Task.WhenAll` to the collection of tasks, `downloadTasks`.</span></span> <span data-ttu-id="7b120-128">`Task.WhenAll` Görevler koleksiyondaki tüm görevler tamamlandığında sona tek bir görev döndürür.</span><span class="sxs-lookup"><span data-stu-id="7b120-128">`Task.WhenAll` returns a single task that finishes when all the tasks in the collection of tasks have completed.</span></span>  
  
     <span data-ttu-id="7b120-129">Aşağıdaki örnekte, `Await` ifade tek tamalanmasını görevin `WhenAll` döndürür.</span><span class="sxs-lookup"><span data-stu-id="7b120-129">In the following example, the `Await` expression awaits the completion of the single task that `WhenAll` returns.</span></span> <span data-ttu-id="7b120-130">İfade bir her tamsayının indirilen bir Web sitesinin uzunluğu olduğu bir tamsayılar dizisi olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="7b120-130">The expression evaluates to an array of integers, where each integer is the length of a downloaded website.</span></span> <span data-ttu-id="7b120-131">Aşağıdaki kodu ekleyin `SumPageSizesAsync`, yalnızca önceki adımda eklediğiniz koddan sonra.</span><span class="sxs-lookup"><span data-stu-id="7b120-131">Add the following code to `SumPageSizesAsync`, just after the code that you added in the previous step.</span></span>  
  
    ```vb  
    ' Await the completion of all the running tasks.  
    Dim lengths As Integer() = Await Task.WhenAll(downloadTasks)  
  
    '' The previous line is equivalent to the following two statements.  
    'Dim whenAllTask As Task(Of Integer()) = Task.WhenAll(downloadTasks)  
    'Dim lengths As Integer() = Await whenAllTask  
    ```  
  
5.  <span data-ttu-id="7b120-132">Son olarak, <xref:System.Linq.Enumerable.Sum%2A> tüm Web sitelerinin uzunluklarının toplamını hesaplamak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="7b120-132">Finally, use the <xref:System.Linq.Enumerable.Sum%2A> method to calculate the sum of the lengths of all the websites.</span></span> <span data-ttu-id="7b120-133">Aşağıdaki satırı ekleyin `SumPageSizesAsync`.</span><span class="sxs-lookup"><span data-stu-id="7b120-133">Add the following line to `SumPageSizesAsync`.</span></span>  
  
    ```vb  
    Dim total = lengths.Sum()  
    ```  
  
### <a name="to-add-taskwhenall-to-the-httpclientgetbytearrayasync-solution"></a><span data-ttu-id="7b120-134">HttpClient.GetByteArrayAsync çözümüne Task.WhenAll eklemek için</span><span class="sxs-lookup"><span data-stu-id="7b120-134">To add Task.WhenAll to the HttpClient.GetByteArrayAsync solution</span></span>  
  
1.  <span data-ttu-id="7b120-135">Aşağıdaki sürümü ekleme `ProcessURLAsync` içinde geliştirilen ikinci uygulamaya [izlenecek yol: Zaman uyumsuz kullanarak Web'e erişme ve Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="7b120-135">Add the following version of `ProcessURLAsync` to the second application that's developed in [Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span>  
  
    -   <span data-ttu-id="7b120-136">Koddan indirdiyseniz [geliştirici kodu örnekleri](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f), AsyncWalkthrough_HttpClient projesini açın ve ardından eklemek `ProcessURLAsync` MainWindow.xaml.vb dosyasına.</span><span class="sxs-lookup"><span data-stu-id="7b120-136">If you downloaded the code from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f), open the AsyncWalkthrough_HttpClient project, and then add `ProcessURLAsync` to the MainWindow.xaml.vb file.</span></span>  
  
    -   <span data-ttu-id="7b120-137">İzlenecek yolu tamamlayarak kodu geliştirdiyseniz, ekleme `ProcessURLAsync` kullanan uygulamaya `HttpClient.GetByteArrayAsync` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="7b120-137">If you developed the code by completing the walkthrough, add `ProcessURLAsync` to the application that uses the `HttpClient.GetByteArrayAsync` method.</span></span> <span data-ttu-id="7b120-138">Bu uygulama için MainWindow.xaml.vb dosyası "Tam kod örnekleri" izlenecek yoldan"bölümündeki ikinci örnektir.</span><span class="sxs-lookup"><span data-stu-id="7b120-138">The MainWindow.xaml.vb file for this application is the second example in the "Complete Code Examples from the Walkthrough" section.</span></span>  
  
     <span data-ttu-id="7b120-139">`ProcessURLAsync` Yöntem gövdesindeki eylemleri birleştirir `For Each` içinde döngü `SumPageSizesAsync` özgün izlenecek yolda.</span><span class="sxs-lookup"><span data-stu-id="7b120-139">The `ProcessURLAsync` method consolidates the actions in the body of the `For Each` loop in `SumPageSizesAsync` in the original walkthrough.</span></span> <span data-ttu-id="7b120-140">Yöntemi zaman uyumsuz olarak bir bayt dizisi olarak belirtilen bir Web sitesinin içeriklerini karşıdan yükler ve ardından görüntüler ve bayt dizisinin uzunluğunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="7b120-140">The method asynchronously downloads the contents of a specified website as a byte array, and then displays and returns the length of the byte array.</span></span>  
  
     <span data-ttu-id="7b120-141">Tek farkı `ProcessURLAsync` yöntemdir önceki yordamda kullanımını <xref:System.Net.Http.HttpClient> örneği `client`.</span><span class="sxs-lookup"><span data-stu-id="7b120-141">The only difference from the `ProcessURLAsync` method in the previous procedure is the use of the <xref:System.Net.Http.HttpClient> instance, `client`.</span></span>  
  
    ```vb  
    Private Async Function ProcessURLAsync(url As String, client As HttpClient) As Task(Of Integer)  
  
        Dim byteArray = Await client.GetByteArrayAsync(url)  
        DisplayResults(url, byteArray)  
        Return byteArray.Length  
    End Function  
    ```  
  
2.  <span data-ttu-id="7b120-142">Açıklama satırı yapın veya silin `For Each` içinde döngü `SumPageSizesAsync`aşağıdaki kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="7b120-142">Comment out or delete the `For Each` loop in `SumPageSizesAsync`, as the following code shows.</span></span>  
  
    ```vb  
    'Dim total = 0   
    'For Each url In urlList   
    '    ' GetByteArrayAsync returns a task. At completion, the task   
    '    ' produces a byte array.   
    '    Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)   
  
    '    ' The following two lines can replace the previous assignment statement.   
    '    'Dim getContentsTask As Task(Of Byte()) = client.GetByteArrayAsync(url)   
    '    'Dim urlContents As Byte() = Await getContentsTask   
  
    '    DisplayResults(url, urlContents)   
  
    '    ' Update the total.   
    '    total += urlContents.Length   
    'Next  
    ```  
  
3.  <span data-ttu-id="7b120-143">Tanımlayan bir [sorgu](../../../../visual-basic/programming-guide/concepts/linq/index.md) , tarafından yürütüldüğünde <xref:System.Linq.Enumerable.ToArray%2A> yöntemi, her bir Web sitesinin içeriklerini indiren bir görev koleksiyonunu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7b120-143">Define a [query](../../../../visual-basic/programming-guide/concepts/linq/index.md) that, when executed by the <xref:System.Linq.Enumerable.ToArray%2A> method, creates a collection of tasks that download the contents of each website.</span></span> <span data-ttu-id="7b120-144">Sorgu çalışırken görevler başlatılır.</span><span class="sxs-lookup"><span data-stu-id="7b120-144">The tasks are started when the query is evaluated.</span></span>  
  
     <span data-ttu-id="7b120-145">Yöntemine aşağıdaki kodu ekleyin `SumPageSizesAsync` bildiriminin `client` ve `urlList`.</span><span class="sxs-lookup"><span data-stu-id="7b120-145">Add the following code to method `SumPageSizesAsync` after the declaration of `client` and `urlList`.</span></span>  
  
    ```vb  
    ' Create a query.  
    Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =  
        From url In urlList Select ProcessURLAsync(url, client)  
  
    ' Use ToArray to execute the query and start the download tasks.  
    Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()  
    ```  
  
4.  <span data-ttu-id="7b120-146">Ardından, uygulama `Task.WhenAll` görevler koleksiyonuna `downloadTasks`.</span><span class="sxs-lookup"><span data-stu-id="7b120-146">Next, apply `Task.WhenAll` to the collection of tasks, `downloadTasks`.</span></span> <span data-ttu-id="7b120-147">`Task.WhenAll` Görevler koleksiyondaki tüm görevler tamamlandığında sona tek bir görev döndürür.</span><span class="sxs-lookup"><span data-stu-id="7b120-147">`Task.WhenAll` returns a single task that finishes when all the tasks in the collection of tasks have completed.</span></span>  
  
     <span data-ttu-id="7b120-148">Aşağıdaki örnekte, `Await` ifade tek tamalanmasını görevin `WhenAll` döndürür.</span><span class="sxs-lookup"><span data-stu-id="7b120-148">In the following example, the `Await` expression awaits the completion of the single task that `WhenAll` returns.</span></span> <span data-ttu-id="7b120-149">İşlem tamamlandığında `Await` ifade bir her tamsayının indirilen bir Web sitesinin uzunluğu olduğu bir tamsayılar dizisi olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="7b120-149">When complete, the `Await` expression evaluates to an array of integers, where each integer is the length of a downloaded website.</span></span> <span data-ttu-id="7b120-150">Aşağıdaki kodu ekleyin `SumPageSizesAsync`, yalnızca önceki adımda eklediğiniz koddan sonra.</span><span class="sxs-lookup"><span data-stu-id="7b120-150">Add the following code to `SumPageSizesAsync`, just after the code that you added in the previous step.</span></span>  
  
    ```vb  
    ' Await the completion of all the running tasks.  
    Dim lengths As Integer() = Await Task.WhenAll(downloadTasks)  
  
    '' The previous line is equivalent to the following two statements.  
    'Dim whenAllTask As Task(Of Integer()) = Task.WhenAll(downloadTasks)  
    'Dim lengths As Integer() = Await whenAllTask  
    ```  
  
5.  <span data-ttu-id="7b120-151">Son olarak, <xref:System.Linq.Enumerable.Sum%2A> tüm Web sitelerinin uzunluklarının toplamını almak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="7b120-151">Finally, use the <xref:System.Linq.Enumerable.Sum%2A> method to get the sum of the lengths of all the websites.</span></span> <span data-ttu-id="7b120-152">Aşağıdaki satırı ekleyin `SumPageSizesAsync`.</span><span class="sxs-lookup"><span data-stu-id="7b120-152">Add the following line to `SumPageSizesAsync`.</span></span>  
  
    ```vb  
    Dim total = lengths.Sum()  
    ```  
  
### <a name="to-test-the-taskwhenall-solutions"></a><span data-ttu-id="7b120-153">Task.WhenAll çözümlerini test etmek için</span><span class="sxs-lookup"><span data-stu-id="7b120-153">To test the Task.WhenAll solutions</span></span>  
  
-   <span data-ttu-id="7b120-154">Her çözüm için programı çalıştırmak için F5 tuşuna basın ve ardından **Başlat** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="7b120-154">For either solution, choose the F5 key to run the program, and then choose the **Start** button.</span></span> <span data-ttu-id="7b120-155">Zaman uyumsuz çözümleri çıkışı çıktıya benzemelidir [izlenecek yol: Zaman uyumsuz kullanarak Web'e erişme ve Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="7b120-155">The output should resemble the output from the async solutions in [Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span> <span data-ttu-id="7b120-156">Ancak, Web sitelerinin her seferinde farklı bir sırada görüntülendiğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="7b120-156">However, notice that the websites appear in a different order each time.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7b120-157">Örnek</span><span class="sxs-lookup"><span data-stu-id="7b120-157">Example</span></span>  
 <span data-ttu-id="7b120-158">Aşağıdaki kodu kullanan proje uzantılarını göstermektedir `GetURLContentsAsync` içeriği Web'den yüklemek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="7b120-158">The following code shows the extensions to the project that uses the `GetURLContentsAsync` method to download content from the web.</span></span>  
  
```vb  
' Add the following Imports statements, and add a reference for System.Net.Http.  
Imports System.Net.Http  
Imports System.Net  
Imports System.IO  
  
Class MainWindow  
  
    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click  
  
        resultsTextBox.Clear()  
  
        ' One-step async call.  
        Await SumPageSizesAsync()  
  
        '' Two-step async call.  
        'Dim sumTask As Task = SumPageSizesAsync()  
        'Await sumTask  
  
        resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."  
    End Sub  
  
    Private Async Function SumPageSizesAsync() As Task  
  
        ' Make a list of web addresses.  
        Dim urlList As List(Of String) = SetUpURLList()  
  
        ' Create a query.   
        Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =  
            From url In urlList Select ProcessURLAsync(url)  
  
        ' Use ToArray to execute the query and start the download tasks.  
        Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()  
  
        ' You can do other work here before awaiting.  
  
        ' Await the completion of all the running tasks.  
        Dim lengths As Integer() = Await Task.WhenAll(downloadTasks)  
  
        '' The previous line is equivalent to the following two statements.  
        'Dim whenAllTask As Task(Of Integer()) = Task.WhenAll(downloadTasks)  
        'Dim lengths As Integer() = Await whenAllTask  
  
        Dim total = lengths.Sum()  
  
        'Dim total = 0  
        'For Each url In urlList  
  
        '    Dim urlContents As Byte() = Await GetURLContentsAsync(url)  
  
        '    ' The previous line abbreviates the following two assignment statements.  
  
        '    ' GetURLContentsAsync returns a task. At completion, the task  
        '    ' produces a byte array.  
        '    'Dim getContentsTask As Task(Of Byte()) = GetURLContentsAsync(url)  
        '    'Dim urlContents As Byte() = Await getContentsTask  
  
        '    DisplayResults(url, urlContents)  
  
        '    ' Update the total.  
        '    total += urlContents.Length  
        'NextNext  
  
        ' Display the total count for all of the web addresses.  
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf &  
                                             "Total bytes returned:  {0}" & vbCrLf, total)  
    End Function  
  
    Private Function SetUpURLList() As List(Of String)  
  
        Dim urls = New List(Of String) From  
            {  
                "https://msdn.microsoft.com",  
                "https://msdn.microsoft.com/library/hh290136.aspx",  
                "https://msdn.microsoft.com/library/ee256749.aspx",  
                "https://msdn.microsoft.com/library/hh290138.aspx",  
                "https://msdn.microsoft.com/library/hh290140.aspx",  
                "https://msdn.microsoft.com/library/dd470362.aspx",  
                "https://msdn.microsoft.com/library/aa578028.aspx",  
                "https://msdn.microsoft.com/library/ms404677.aspx",  
                "https://msdn.microsoft.com/library/ff730837.aspx"  
            }  
        Return urls  
    End Function  
  
    ' The actions from the foreach loop are moved to this async method.  
    Private Async Function ProcessURLAsync(url As String) As Task(Of Integer)  
  
        Dim byteArray = Await GetURLContentsAsync(url)  
        DisplayResults(url, byteArray)  
        Return byteArray.Length  
    End Function  
  
    Private Async Function GetURLContentsAsync(url As String) As Task(Of Byte())  
  
        ' The downloaded resource ends up in the variable named content.  
        Dim content = New MemoryStream()  
  
        ' Initialize an HttpWebRequest for the current URL.  
        Dim webReq = CType(WebRequest.Create(url), HttpWebRequest)  
  
        ' Send the request to the Internet resource and wait for  
        ' the response.  
        Using response As WebResponse = Await webReq.GetResponseAsync()  
            ' Get the data stream that is associated with the specified URL.  
            Using responseStream As Stream = response.GetResponseStream()  
                ' Read the bytes in responseStream and copy them to content.    
                ' CopyToAsync returns a Task, not a Task<T>.  
                Await responseStream.CopyToAsync(content)  
            End Using  
        End Using  
  
        ' Return the result as a byte array.  
        Return content.ToArray()  
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
  
## <a name="example"></a><span data-ttu-id="7b120-159">Örnek</span><span class="sxs-lookup"><span data-stu-id="7b120-159">Example</span></span>  
 <span data-ttu-id="7b120-160">Aşağıdaki kod yöntemini kullanan proje uzantılarını göstermektedir `HttpClient.GetByteArrayAsync` içeriği Web'den yüklemek için.</span><span class="sxs-lookup"><span data-stu-id="7b120-160">The following code shows the extensions to the project that uses method `HttpClient.GetByteArrayAsync` to download content from the web.</span></span>  
  
```vb  
' Add the following Imports statements, and add a reference for System.Net.Http.  
Imports System.Net.Http  
Imports System.Net  
Imports System.IO  
  
Class MainWindow  
  
    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click  
  
        resultsTextBox.Clear()  
  
        '' One-step async call.  
        Await SumPageSizesAsync()  
  
        '' Two-step async call.  
        'Dim sumTask As Task = SumPageSizesAsync()  
        'Await sumTask  
  
        resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."  
    End Sub  
  
    Private Async Function SumPageSizesAsync() As Task  
  
        ' Declare an HttpClient object and increase the buffer size. The  
        ' default buffer size is 65,536.  
        Dim client As HttpClient =  
            New HttpClient() With {.MaxResponseContentBufferSize = 1000000}  
  
        ' Make a list of web addresses.  
        Dim urlList As List(Of String) = SetUpURLList()  
  
        ' Create a query.  
        Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =  
            From url In urlList Select ProcessURLAsync(url, client)  
  
        ' Use ToArray to execute the query and start the download tasks.  
        Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()  
  
        ' You can do other work here before awaiting.  
  
        ' Await the completion of all the running tasks.  
        Dim lengths As Integer() = Await Task.WhenAll(downloadTasks)  
  
        '' The previous line is equivalent to the following two statements.  
        'Dim whenAllTask As Task(Of Integer()) = Task.WhenAll(downloadTasks)  
        'Dim lengths As Integer() = Await whenAllTask  
  
        Dim total = lengths.Sum()  
  
        ''<snippet7>  
        'Dim total = 0  
        'For Each url In urlList  
        '    ' GetByteArrayAsync returns a task. At completion, the task  
        '    ' produces a byte array.  
        '    '<snippet31>  
        '    Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)  
        '    '</snippet31>  
  
        '    ' The following two lines can replace the previous assignment statement.  
        '    'Dim getContentsTask As Task(Of Byte()) = client.GetByteArrayAsync(url)  
        '    'Dim urlContents As Byte() = Await getContentsTask  
  
        '    DisplayResults(url, urlContents)  
  
        '    ' Update the total.  
        '    total += urlContents.Length  
        'NextNext  
  
        ' Display the total count for all of the web addresses.  
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf &  
                                             "Total bytes returned:  {0}" & vbCrLf, total)  
    End Function  
  
    Private Function SetUpURLList() As List(Of String)  
  
        Dim urls = New List(Of String) From  
            {  
                "https://www.msdn.com",  
                "https://msdn.microsoft.com/library/hh290136.aspx",  
                "https://msdn.microsoft.com/library/ee256749.aspx",  
                "https://msdn.microsoft.com/library/hh290138.aspx",  
                "https://msdn.microsoft.com/library/hh290140.aspx",  
                "https://msdn.microsoft.com/library/dd470362.aspx",  
                "https://msdn.microsoft.com/library/aa578028.aspx",  
                "https://msdn.microsoft.com/library/ms404677.aspx",  
                "https://msdn.microsoft.com/library/ff730837.aspx"  
            }  
        Return urls  
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
  
## <a name="see-also"></a><span data-ttu-id="7b120-161">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7b120-161">See also</span></span>

- <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>
- [<span data-ttu-id="7b120-162">İzlenecek yol: Zaman uyumsuz kullanarak Web'e erişme ve Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7b120-162">Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
