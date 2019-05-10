---
title: 'Nasıl yapılır: Zaman uyumsuz izlenecek yolu Task.WhenAll kullanarak genişletme (C#)'
ms.date: 07/20/2015
ms.assetid: f6927ef2-dc6c-43f8-bc82-bbeac42de423
ms.openlocfilehash: 8e1f617040bd902ab53500fbfeeafff35677280a
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64583422"
---
# <a name="how-to-extend-the-async-walkthrough-by-using-taskwhenall-c"></a><span data-ttu-id="aba96-102">Nasıl yapılır: Zaman uyumsuz izlenecek yolu Task.WhenAll kullanarak genişletme (C#)</span><span class="sxs-lookup"><span data-stu-id="aba96-102">How to: Extend the async Walkthrough by Using Task.WhenAll (C#)</span></span>
<span data-ttu-id="aba96-103">İçinde zaman uyumsuz çözümün performansını artırabilirsiniz [izlenecek yol: Zaman uyumsuz kullanarak Web'e erişme ve await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md) kullanarak <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="aba96-103">You can improve the performance of the async solution in [Walkthrough: Accessing the Web by Using async and await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md) by using the <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="aba96-104">Bu yöntem, zaman uyumsuz olarak görevleri topluluğu temsil edilen birden çok zaman uyumsuz işlemler bekler.</span><span class="sxs-lookup"><span data-stu-id="aba96-104">This method asynchronously awaits multiple asynchronous operations, which are represented as a collection of tasks.</span></span>  
  
 <span data-ttu-id="aba96-105">Web sitelerinin indirme hızlarının farklı izlenecek yolda etmiş olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="aba96-105">You might have noticed in the walkthrough that the websites download at different rates.</span></span> <span data-ttu-id="aba96-106">Bazen, Web siteleri, kalan tüm indirmeleri geciktirir çok yavaş biridir.</span><span class="sxs-lookup"><span data-stu-id="aba96-106">Sometimes one of the websites is very slow, which delays all the remaining downloads.</span></span> <span data-ttu-id="aba96-107">Anlatımda oluşturduğunuz zaman uyumsuz çözümleri çalıştırdığınızda, program kolayca beklemek istemiyorsanız, ancak tüm indirmeleri aynı anda başlatmak ve devam etmek için beklemenize gerek kalmadan daha hızlı indirmeler izin vermek için daha iyi bir seçenek olacaktır sona erdirebilirsiniz ait  ertelendi.</span><span class="sxs-lookup"><span data-stu-id="aba96-107">When you run the asynchronous solutions that you build in the walkthrough, you can end the program easily if you don't want to wait, but a better option would be to start all the downloads at the same time and let faster downloads continue without waiting for the one that’s delayed.</span></span>  
  
 <span data-ttu-id="aba96-108">Uyguladığınız `Task.WhenAll` yöntemi için bir görev koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="aba96-108">You apply the `Task.WhenAll` method to a collection of tasks.</span></span> <span data-ttu-id="aba96-109">Uygulamayı `WhenAll` koleksiyondaki her görev tamamlanıncaya kadar tam olmayan tek bir görev döndürür.</span><span class="sxs-lookup"><span data-stu-id="aba96-109">The application of `WhenAll` returns a single task that isn’t complete until every task in the collection is completed.</span></span> <span data-ttu-id="aba96-110">Görevler paralel olarak çalışır gibigörünür, ancak hiçbir ek iş parçacığı oluşturulmaz.</span><span class="sxs-lookup"><span data-stu-id="aba96-110">The tasks appear to run in parallel, but no additional threads are created.</span></span> <span data-ttu-id="aba96-111">Görevler herhangi bir sırada tamamlayabilir.</span><span class="sxs-lookup"><span data-stu-id="aba96-111">The tasks can complete in any order.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="aba96-112">Aşağıdaki yordamlar içinde geliştirilen zaman uyumsuz uygulamaların uzantılarını açıklamaktadır [izlenecek yol: Zaman uyumsuz kullanarak Web'e erişme ve await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="aba96-112">The following procedures describe extensions to the async applications that are developed in [Walkthrough: Accessing the Web by Using async and await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span> <span data-ttu-id="aba96-113">İzlenecek yolu tamamlayarak veya kodu indiriliyor tarafından uygulamalar geliştirebilirsiniz [geliştirici kodu örnekleri](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).</span><span class="sxs-lookup"><span data-stu-id="aba96-113">You can develop the applications by either completing the walkthrough or downloading the code from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).</span></span>  
>   
>  <span data-ttu-id="aba96-114">Örneği çalıştırmak için Visual Studio 2012 olmalıdır veya üzeri yüklü.</span><span class="sxs-lookup"><span data-stu-id="aba96-114">To run the example, you must have Visual Studio 2012 or later installed on your computer.</span></span>  
  
### <a name="to-add-taskwhenall-to-your-geturlcontentsasync-solution"></a><span data-ttu-id="aba96-115">GetURLContentsAsync çözümünüze Task.WhenAll eklemek için</span><span class="sxs-lookup"><span data-stu-id="aba96-115">To add Task.WhenAll to your GetURLContentsAsync solution</span></span>  
  
1. <span data-ttu-id="aba96-116">Ekleme `ProcessURLAsync` yöntemi içinde geliştirilen ilk uygulamaya [izlenecek yol: Zaman uyumsuz kullanarak Web'e erişme ve await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="aba96-116">Add the `ProcessURLAsync` method to the first application that's developed in [Walkthrough: Accessing the Web by Using async and await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span>  
  
    - <span data-ttu-id="aba96-117">Koddan indirdiyseniz [geliştirici kodu örnekleri](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f), AsyncWalkthrough projesini açın ve ardından eklemek `ProcessURLAsync` MainWindow.xaml.cs dosyasına.</span><span class="sxs-lookup"><span data-stu-id="aba96-117">If you downloaded the code from  [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f), open the AsyncWalkthrough project, and then add `ProcessURLAsync` to the MainWindow.xaml.cs file.</span></span>  
  
    - <span data-ttu-id="aba96-118">İzlenecek yolu tamamlayarak kodu geliştirdiyseniz, ekleme `ProcessURLAsync` içeren uygulamaya `GetURLContentsAsync` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="aba96-118">If you developed the code by completing the walkthrough, add `ProcessURLAsync` to the application that includes the `GetURLContentsAsync` method.</span></span> <span data-ttu-id="aba96-119">Bu uygulama için MainWindow.xaml.cs dosyası "Tam kod örnekleri" izlenecek yoldan"bölümündeki ilk örnektir.</span><span class="sxs-lookup"><span data-stu-id="aba96-119">The MainWindow.xaml.cs file for this application is the first example in the "Complete Code Examples from the Walkthrough" section.</span></span>  
  
     <span data-ttu-id="aba96-120">`ProcessURLAsync` Yöntem gövdesindeki eylemleri birleştirir `foreach` içinde döngü `SumPageSizesAsync` özgün izlenecek yolda.</span><span class="sxs-lookup"><span data-stu-id="aba96-120">The `ProcessURLAsync` method consolidates the actions in the body of the `foreach` loop in `SumPageSizesAsync` in the original walkthrough.</span></span> <span data-ttu-id="aba96-121">Yöntemi zaman uyumsuz olarak bir bayt dizisi olarak belirtilen bir Web sitesinin içeriklerini karşıdan yükler ve ardından görüntüler ve bayt dizisinin uzunluğunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="aba96-121">The method asynchronously downloads the contents of a specified website as a byte array, and then displays and returns the length of the byte array.</span></span>  
  
    ```csharp  
    private async Task<int> ProcessURLAsync(string url)  
    {  
        var byteArray = await GetURLContentsAsync(url);  
        DisplayResults(url, byteArray);  
        return byteArray.Length;  
    }  
    ```  
  
2. <span data-ttu-id="aba96-122">Açıklama satırı yapın veya silin `foreach` içinde döngü `SumPageSizesAsync`aşağıdaki kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="aba96-122">Comment out or delete the `foreach` loop in `SumPageSizesAsync`, as the following code shows.</span></span>  
  
    ```csharp  
    //var total = 0;  
    //foreach (var url in urlList)  
    //{  
    //    byte[] urlContents = await GetURLContentsAsync(url);  
  
    //    // The previous line abbreviates the following two assignment statements.  
    //    // GetURLContentsAsync returns a Task<T>. At completion, the task  
    //    // produces a byte array.  
    //    //Task<byte[]> getContentsTask = GetURLContentsAsync(url);  
    //    //byte[] urlContents = await getContentsTask;  
  
    //    DisplayResults(url, urlContents);  
  
    //    // Update the total.            
    //    total += urlContents.Length;  
    //}  
    ```  
  
3. <span data-ttu-id="aba96-123">Bir görev koleksiyonu oluşturun.</span><span class="sxs-lookup"><span data-stu-id="aba96-123">Create a collection of tasks.</span></span> <span data-ttu-id="aba96-124">Aşağıdaki kodu tanımlayan bir [sorgu](../../../../csharp/programming-guide/concepts/linq/index.md) , tarafından yürütüldüğünde <xref:System.Linq.Enumerable.ToArray%2A> yöntemi, her bir Web sitesinin içeriklerini indiren bir görev koleksiyonunu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="aba96-124">The following code defines a [query](../../../../csharp/programming-guide/concepts/linq/index.md) that, when executed by the <xref:System.Linq.Enumerable.ToArray%2A> method, creates a collection of tasks that download the contents of each website.</span></span> <span data-ttu-id="aba96-125">Sorgu çalışırken görevler başlatılır.</span><span class="sxs-lookup"><span data-stu-id="aba96-125">The tasks are started when the query is evaluated.</span></span>  
  
     <span data-ttu-id="aba96-126">Yöntemine aşağıdaki kodu ekleyin `SumPageSizesAsync` bildiriminin `urlList`.</span><span class="sxs-lookup"><span data-stu-id="aba96-126">Add the following code to method `SumPageSizesAsync` after the declaration of `urlList`.</span></span>  
  
    ```csharp  
    // Create a query.   
    IEnumerable<Task<int>> downloadTasksQuery =   
        from url in urlList select ProcessURLAsync(url);  
  
    // Use ToArray to execute the query and start the download tasks.  
    Task<int>[] downloadTasks = downloadTasksQuery.ToArray();  
    ```  
  
4. <span data-ttu-id="aba96-127">Uygulama `Task.WhenAll` görevler koleksiyonuna `downloadTasks`.</span><span class="sxs-lookup"><span data-stu-id="aba96-127">Apply `Task.WhenAll` to the collection of tasks, `downloadTasks`.</span></span> <span data-ttu-id="aba96-128">`Task.WhenAll` Görevler koleksiyondaki tüm görevler tamamlandığında sona tek bir görev döndürür.</span><span class="sxs-lookup"><span data-stu-id="aba96-128">`Task.WhenAll` returns a single task that finishes when all the tasks in the collection of tasks have completed.</span></span>  
  
     <span data-ttu-id="aba96-129">Aşağıdaki örnekte, `await` ifade tek tamalanmasını görevin `WhenAll` döndürür.</span><span class="sxs-lookup"><span data-stu-id="aba96-129">In the following example, the `await` expression awaits the completion of the single task that `WhenAll` returns.</span></span> <span data-ttu-id="aba96-130">İfade bir her tamsayının indirilen bir Web sitesinin uzunluğu olduğu bir tamsayılar dizisi olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="aba96-130">The expression evaluates to an array of integers, where each integer is the length of a downloaded website.</span></span> <span data-ttu-id="aba96-131">Aşağıdaki kodu ekleyin `SumPageSizesAsync`, yalnızca önceki adımda eklediğiniz koddan sonra.</span><span class="sxs-lookup"><span data-stu-id="aba96-131">Add the following code to `SumPageSizesAsync`, just after the code that you added in the previous step.</span></span>  
  
    ```csharp  
    // Await the completion of all the running tasks.  
    int[] lengths = await Task.WhenAll(downloadTasks);  
  
    //// The previous line is equivalent to the following two statements.  
    //Task<int[]> whenAllTask = Task.WhenAll(downloadTasks);  
    //int[] lengths = await whenAllTask;  
    ```  
  
5. <span data-ttu-id="aba96-132">Son olarak, <xref:System.Linq.Enumerable.Sum%2A> tüm Web sitelerinin uzunluklarının toplamını hesaplamak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="aba96-132">Finally, use the <xref:System.Linq.Enumerable.Sum%2A> method to calculate the sum of the lengths of all the websites.</span></span> <span data-ttu-id="aba96-133">Aşağıdaki satırı ekleyin `SumPageSizesAsync`.</span><span class="sxs-lookup"><span data-stu-id="aba96-133">Add the following line to `SumPageSizesAsync`.</span></span>  
  
    ```csharp  
    int total = lengths.Sum();  
    ```  
  
### <a name="to-add-taskwhenall-to-the-httpclientgetbytearrayasync-solution"></a><span data-ttu-id="aba96-134">HttpClient.GetByteArrayAsync çözümüne Task.WhenAll eklemek için</span><span class="sxs-lookup"><span data-stu-id="aba96-134">To add Task.WhenAll to the HttpClient.GetByteArrayAsync solution</span></span>  
  
1. <span data-ttu-id="aba96-135">Aşağıdaki sürümü ekleme `ProcessURLAsync` içinde geliştirilen ikinci uygulamaya [izlenecek yol: Zaman uyumsuz kullanarak Web'e erişme ve await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="aba96-135">Add the following version of `ProcessURLAsync` to the second application that's developed in [Walkthrough: Accessing the Web by Using async and await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span>  
  
    - <span data-ttu-id="aba96-136">Koddan indirdiyseniz [geliştirici kodu örnekleri](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f), AsyncWalkthrough_HttpClient projesini açın ve ardından eklemek `ProcessURLAsync` MainWindow.xaml.cs dosyasına.</span><span class="sxs-lookup"><span data-stu-id="aba96-136">If you downloaded the code from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f), open the AsyncWalkthrough_HttpClient project, and then add `ProcessURLAsync` to the MainWindow.xaml.cs file.</span></span>  
  
    - <span data-ttu-id="aba96-137">İzlenecek yolu tamamlayarak kodu geliştirdiyseniz, ekleme `ProcessURLAsync` kullanan uygulamaya `HttpClient.GetByteArrayAsync` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="aba96-137">If you developed the code by completing the walkthrough, add `ProcessURLAsync` to the application that uses the `HttpClient.GetByteArrayAsync` method.</span></span> <span data-ttu-id="aba96-138">Bu uygulama için MainWindow.xaml.cs dosyası "Tam kod örnekleri" izlenecek yoldan"bölümündeki ikinci örnektir.</span><span class="sxs-lookup"><span data-stu-id="aba96-138">The MainWindow.xaml.cs file for this application is the second example in the "Complete Code Examples from the Walkthrough" section.</span></span>  
  
     <span data-ttu-id="aba96-139">`ProcessURLAsync` Yöntem gövdesindeki eylemleri birleştirir `foreach` içinde döngü `SumPageSizesAsync` özgün izlenecek yolda.</span><span class="sxs-lookup"><span data-stu-id="aba96-139">The `ProcessURLAsync` method consolidates the actions in the body of the `foreach` loop in `SumPageSizesAsync` in the original walkthrough.</span></span> <span data-ttu-id="aba96-140">Yöntemi zaman uyumsuz olarak bir bayt dizisi olarak belirtilen bir Web sitesinin içeriklerini karşıdan yükler ve ardından görüntüler ve bayt dizisinin uzunluğunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="aba96-140">The method asynchronously downloads the contents of a specified website as a byte array, and then displays and returns the length of the byte array.</span></span>  
  
     <span data-ttu-id="aba96-141">Tek farkı `ProcessURLAsync` yöntemdir önceki yordamda kullanımını <xref:System.Net.Http.HttpClient> örneği `client`.</span><span class="sxs-lookup"><span data-stu-id="aba96-141">The only difference from the `ProcessURLAsync` method in the previous procedure is the use of the <xref:System.Net.Http.HttpClient> instance, `client`.</span></span>  
  
    ```csharp  
    async Task<int> ProcessURLAsync(string url, HttpClient client)  
    {  
        byte[] byteArray = await client.GetByteArrayAsync(url);  
        DisplayResults(url, byteArray);  
        return byteArray.Length;  
    }  
    ```  
  
2. <span data-ttu-id="aba96-142">Açıklama satırı yapın veya silin `For Each` veya `foreach` içinde döngü `SumPageSizesAsync`aşağıdaki kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="aba96-142">Comment out or delete the `For Each` or `foreach` loop in `SumPageSizesAsync`, as the following code shows.</span></span>  
  
    ```csharp  
    //var total = 0;  
    //foreach (var url in urlList)  
    //{  
    //    // GetByteArrayAsync returns a Task<T>. At completion, the task  
    //    // produces a byte array.  
    //    byte[] urlContent = await client.GetByteArrayAsync(url);  
  
    //    // The previous line abbreviates the following two assignment  
    //    // statements.  
    //    Task<byte[]> getContentTask = client.GetByteArrayAsync(url);  
    //    byte[] urlContent = await getContentTask;  
  
    //    DisplayResults(url, urlContent);  
  
    //    // Update the total.  
    //    total += urlContent.Length;  
    //}  
    ```  
  
3. <span data-ttu-id="aba96-143">Tanımlayan bir [sorgu](../../../../csharp/programming-guide/concepts/linq/index.md) , tarafından yürütüldüğünde <xref:System.Linq.Enumerable.ToArray%2A> yöntemi, her bir Web sitesinin içeriklerini indiren bir görev koleksiyonunu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="aba96-143">Define a [query](../../../../csharp/programming-guide/concepts/linq/index.md) that, when executed by the <xref:System.Linq.Enumerable.ToArray%2A> method, creates a collection of tasks that download the contents of each website.</span></span> <span data-ttu-id="aba96-144">Sorgu çalışırken görevler başlatılır.</span><span class="sxs-lookup"><span data-stu-id="aba96-144">The tasks are started when the query is evaluated.</span></span>  
  
     <span data-ttu-id="aba96-145">Yöntemine aşağıdaki kodu ekleyin `SumPageSizesAsync` bildiriminin `client` ve `urlList`.</span><span class="sxs-lookup"><span data-stu-id="aba96-145">Add the following code to method `SumPageSizesAsync` after the declaration of `client` and `urlList`.</span></span>  
  
    ```csharp  
    // Create a query.  
    IEnumerable<Task<int>> downloadTasksQuery =   
        from url in urlList select ProcessURLAsync(url, client);  
  
    // Use ToArray to execute the query and start the download tasks.  
    Task<int>[] downloadTasks = downloadTasksQuery.ToArray();  
    ```  
  
4. <span data-ttu-id="aba96-146">Ardından, uygulama `Task.WhenAll` görevler koleksiyonuna `downloadTasks`.</span><span class="sxs-lookup"><span data-stu-id="aba96-146">Next, apply `Task.WhenAll` to the collection of tasks, `downloadTasks`.</span></span> <span data-ttu-id="aba96-147">`Task.WhenAll` Görevler koleksiyondaki tüm görevler tamamlandığında sona tek bir görev döndürür.</span><span class="sxs-lookup"><span data-stu-id="aba96-147">`Task.WhenAll` returns a single task that finishes when all the tasks in the collection of tasks have completed.</span></span>  
  
     <span data-ttu-id="aba96-148">Aşağıdaki örnekte, `await` ifade tek tamalanmasını görevin `WhenAll` döndürür.</span><span class="sxs-lookup"><span data-stu-id="aba96-148">In the following example, the `await` expression awaits the completion of the single task that `WhenAll` returns.</span></span> <span data-ttu-id="aba96-149">İşlem tamamlandığında `await` ifade bir her tamsayının indirilen bir Web sitesinin uzunluğu olduğu bir tamsayılar dizisi olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="aba96-149">When complete, the `await` expression evaluates to an array of integers, where each integer is the length of a downloaded website.</span></span> <span data-ttu-id="aba96-150">Aşağıdaki kodu ekleyin `SumPageSizesAsync`, yalnızca önceki adımda eklediğiniz koddan sonra.</span><span class="sxs-lookup"><span data-stu-id="aba96-150">Add the following code to `SumPageSizesAsync`, just after the code that you added in the previous step.</span></span>  
  
    ```csharp  
    // Await the completion of all the running tasks.  
    int[] lengths = await Task.WhenAll(downloadTasks);  
  
    //// The previous line is equivalent to the following two statements.  
    //Task<int[]> whenAllTask = Task.WhenAll(downloadTasks);  
    //int[] lengths = await whenAllTask;  
    ```  
  
5. <span data-ttu-id="aba96-151">Son olarak, <xref:System.Linq.Enumerable.Sum%2A> tüm Web sitelerinin uzunluklarının toplamını almak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="aba96-151">Finally, use the <xref:System.Linq.Enumerable.Sum%2A> method to get the sum of the lengths of all the websites.</span></span> <span data-ttu-id="aba96-152">Aşağıdaki satırı ekleyin `SumPageSizesAsync`.</span><span class="sxs-lookup"><span data-stu-id="aba96-152">Add the following line to `SumPageSizesAsync`.</span></span>  
  
    ```csharp  
    int total = lengths.Sum();
    ```  
  
### <a name="to-test-the-taskwhenall-solutions"></a><span data-ttu-id="aba96-153">Task.WhenAll çözümlerini test etmek için</span><span class="sxs-lookup"><span data-stu-id="aba96-153">To test the Task.WhenAll solutions</span></span>  
  
- <span data-ttu-id="aba96-154">Her çözüm için programı çalıştırmak için F5 tuşuna basın ve ardından **Başlat** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="aba96-154">For either solution, choose the F5 key to run the program, and then choose the **Start** button.</span></span> <span data-ttu-id="aba96-155">Zaman uyumsuz çözümleri çıkışı çıktıya benzemelidir [izlenecek yol: Zaman uyumsuz kullanarak Web'e erişme ve await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="aba96-155">The output should resemble the output from the async solutions in [Walkthrough: Accessing the Web by Using async and await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span> <span data-ttu-id="aba96-156">Ancak, Web sitelerinin her seferinde farklı bir sırada görüntülendiğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="aba96-156">However, notice that the websites appear in a different order each time.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aba96-157">Örnek</span><span class="sxs-lookup"><span data-stu-id="aba96-157">Example</span></span>  
 <span data-ttu-id="aba96-158">Aşağıdaki kodu kullanan proje uzantılarını göstermektedir `GetURLContentsAsync` içeriği Web'den yüklemek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="aba96-158">The following code shows the extensions to the project that uses the `GetURLContentsAsync` method to download content from the web.</span></span>  
  
```csharp  
// Add the following using directives, and add a reference for System.Net.Http.  
using System.Net.Http;  
using System.IO;  
using System.Net;  
  
namespace AsyncExampleWPF_WhenAll  
{  
    public partial class MainWindow : Window  
    {  
        public MainWindow()  
        {  
            InitializeComponent();  
        }  
  
        private async void startButton_Click(object sender, RoutedEventArgs e)  
        {  
            resultsTextBox.Clear();  
  
            // Two-step async call.  
            Task sumTask = SumPageSizesAsync();  
            await sumTask;  
  
            // One-step async call.  
            //await SumPageSizesAsync();  
  
            resultsTextBox.Text += "\r\nControl returned to startButton_Click.\r\n";  
        }  
  
        private async Task SumPageSizesAsync()  
        {  
            // Make a list of web addresses.  
            List<string> urlList = SetUpURLList();  
  
            // Create a query.   
            IEnumerable<Task<int>> downloadTasksQuery =   
                from url in urlList select ProcessURLAsync(url);  
  
            // Use ToArray to execute the query and start the download tasks.  
            Task<int>[] downloadTasks = downloadTasksQuery.ToArray();  
  
            // You can do other work here before awaiting.  
  
            // Await the completion of all the running tasks.  
            int[] lengths = await Task.WhenAll(downloadTasks);  
  
            //// The previous line is equivalent to the following two statements.  
            //Task<int[]> whenAllTask = Task.WhenAll(downloadTasks);  
            //int[] lengths = await whenAllTask;  
  
            int total = lengths.Sum();  
  
            //var total = 0;  
            //foreach (var url in urlList)  
            //{  
            //    byte[] urlContents = await GetURLContentsAsync(url);  
  
            //    // The previous line abbreviates the following two assignment statements.  
            //    // GetURLContentsAsync returns a Task<T>. At completion, the task  
            //    // produces a byte array.  
            //    //Task<byte[]> getContentsTask = GetURLContentsAsync(url);  
            //    //byte[] urlContents = await getContentsTask;  
  
            //    DisplayResults(url, urlContents);  
  
            //    // Update the total.            
            //    total += urlContents.Length;  
            //}  
  
            // Display the total count for all of the websites.  
            resultsTextBox.Text +=  
                $"\r\n\r\nTotal bytes returned:  {total}\r\n";
        }  
  
        private List<string> SetUpURLList()  
        {  
            List<string> urls = new List<string>   
            {   
                "https://msdn.microsoft.com",  
                "https://msdn.microsoft.com/library/windows/apps/br211380.aspx",  
                "https://msdn.microsoft.com/library/hh290136.aspx",  
                "https://msdn.microsoft.com/library/ee256749.aspx",  
                "https://msdn.microsoft.com/library/hh290138.aspx",  
                "https://msdn.microsoft.com/library/hh290140.aspx",  
                "https://msdn.microsoft.com/library/dd470362.aspx",  
                "https://msdn.microsoft.com/library/aa578028.aspx",  
                "https://msdn.microsoft.com/library/ms404677.aspx",  
                "https://msdn.microsoft.com/library/ff730837.aspx"  
            };  
            return urls;  
        }  
  
        // The actions from the foreach loop are moved to this async method.  
        private async Task<int> ProcessURLAsync(string url)  
        {  
            var byteArray = await GetURLContentsAsync(url);  
            DisplayResults(url, byteArray);  
            return byteArray.Length;  
        }  
  
        private async Task<byte[]> GetURLContentsAsync(string url)  
        {  
            // The downloaded resource ends up in the variable named content.  
            var content = new MemoryStream();  
  
            // Initialize an HttpWebRequest for the current URL.  
            var webReq = (HttpWebRequest)WebRequest.Create(url);  
  
            // Send the request to the Internet resource and wait for  
            // the response.  
            using (WebResponse response = await webReq.GetResponseAsync())  
            {  
                // Get the data stream that is associated with the specified url.  
                using (Stream responseStream = response.GetResponseStream())  
                {  
                    await responseStream.CopyToAsync(content);  
                }  
            }  
  
            // Return the result as a byte array.  
            return content.ToArray();  
  
        }  
  
        private void DisplayResults(string url, byte[] content)  
        {  
            // Display the length of each website. The string format   
            // is designed to be used with a monospaced font, such as  
            // Lucida Console or Global Monospace.  
            var bytes = content.Length;  
            // Strip off the "https://".  
            var displayURL = url.Replace("https://", "");  
            resultsTextBox.Text += $"\n{displayURL,-58} {bytes,8}";
        }
    }  
}  
```  
  
## <a name="example"></a><span data-ttu-id="aba96-159">Örnek</span><span class="sxs-lookup"><span data-stu-id="aba96-159">Example</span></span>  
 <span data-ttu-id="aba96-160">Aşağıdaki kod yöntemini kullanan proje uzantılarını göstermektedir `HttpClient.GetByteArrayAsync` içeriği Web'den yüklemek için.</span><span class="sxs-lookup"><span data-stu-id="aba96-160">The following code shows the extensions to the project that uses method `HttpClient.GetByteArrayAsync` to download content from the web.</span></span>  
  
```csharp  
// Add the following using directives, and add a reference for System.Net.Http.  
using System.Net.Http;  
using System.IO;  
using System.Net;  
  
namespace AsyncExampleWPF_HttpClient_WhenAll  
{  
    public partial class MainWindow : Window  
    {  
        public MainWindow()  
        {  
            InitializeComponent();  
        }  
  
        private async void startButton_Click(object sender, RoutedEventArgs e)  
        {  
            resultsTextBox.Clear();  
  
            // One-step async call.  
            await SumPageSizesAsync();  
  
            // Two-step async call.  
            //Task sumTask = SumPageSizesAsync();  
            //await sumTask;  
  
            resultsTextBox.Text += "\r\nControl returned to startButton_Click.\r\n";  
        }  
  
        private async Task SumPageSizesAsync()  
        {  
            // Make a list of web addresses.  
            List<string> urlList = SetUpURLList();  
  
            // Declare an HttpClient object and increase the buffer size. The  
            // default buffer size is 65,536.  
            HttpClient client = new HttpClient() { MaxResponseContentBufferSize = 1000000 };  
  
            // Create a query.  
            IEnumerable<Task<int>> downloadTasksQuery =   
                from url in urlList select ProcessURLAsync(url, client);  
  
            // Use ToArray to execute the query and start the download tasks.  
            Task<int>[] downloadTasks = downloadTasksQuery.ToArray();  
  
            // You can do other work here before awaiting.  
  
            // Await the completion of all the running tasks.  
            int[] lengths = await Task.WhenAll(downloadTasks);  
  
            //// The previous line is equivalent to the following two statements.  
            //Task<int[]> whenAllTask = Task.WhenAll(downloadTasks);  
            //int[] lengths = await whenAllTask;  
  
            int total = lengths.Sum();  
  
            //var total = 0;  
            //foreach (var url in urlList)  
            //{  
            //    // GetByteArrayAsync returns a Task<T>. At completion, the task  
            //    // produces a byte array.  
            //    byte[] urlContent = await client.GetByteArrayAsync(url);  
  
            //    // The previous line abbreviates the following two assignment  
            //    // statements.  
            //    Task<byte[]> getContentTask = client.GetByteArrayAsync(url);  
            //    byte[] urlContent = await getContentTask;  
  
            //    DisplayResults(url, urlContent);  
  
            //    // Update the total.  
            //    total += urlContent.Length;  
            //}  
  
            // Display the total count for all of the web addresses.  
            resultsTextBox.Text +=  
                $"\r\n\r\nTotal bytes returned:  {total}\r\n";
        }  
  
        private List<string> SetUpURLList()  
        {  
            List<string> urls = new List<string>   
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
            };  
            return urls;  
        }  
  
        // The actions from the foreach loop are moved to this async method.  
        async Task<int> ProcessURLAsync(string url, HttpClient client)  
        {  
            byte[] byteArray = await client.GetByteArrayAsync(url);  
            DisplayResults(url, byteArray);  
            return byteArray.Length;  
        }  
  
        private void DisplayResults(string url, byte[] content)  
        {  
            // Display the length of each web site. The string format   
            // is designed to be used with a monospaced font, such as  
            // Lucida Console or Global Monospace.  
            var bytes = content.Length;  
            // Strip off the "https://".  
            var displayURL = url.Replace("https://", "");  
            resultsTextBox.Text += $"\n{displayURL,-58} {bytes,8}";
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="aba96-161">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aba96-161">See also</span></span>

- <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>
- [<span data-ttu-id="aba96-162">İzlenecek yol: Zaman uyumsuz kullanarak Web'e erişme ve await (C#)</span><span class="sxs-lookup"><span data-stu-id="aba96-162">Walkthrough: Accessing the Web by Using async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
