---
title: 'Nasıl yapılır: Task. WhenAll (C#) kullanarak zaman uyumsuz izlenecek yolu genişletme'
ms.date: 07/20/2015
ms.assetid: f6927ef2-dc6c-43f8-bc82-bbeac42de423
ms.openlocfilehash: 5915a09123e6abb1bfb846c200a500a51302a104
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69924417"
---
# <a name="how-to-extend-the-async-walkthrough-by-using-taskwhenall-c"></a><span data-ttu-id="d64e3-102">Nasıl yapılır: Task. WhenAll (C#) kullanarak zaman uyumsuz izlenecek yolu genişletme</span><span class="sxs-lookup"><span data-stu-id="d64e3-102">How to: Extend the async Walkthrough by Using Task.WhenAll (C#)</span></span>
<span data-ttu-id="d64e3-103">[Gözden geçirmede zaman uyumsuz çözümün performansını artırabilirsiniz: Yöntemini kullanarakC#](./walkthrough-accessing-the-web-by-using-async-and-await.md) , Async ve await () kullanarak Web 'e erişme. <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="d64e3-103">You can improve the performance of the async solution in [Walkthrough: Accessing the Web by Using async and await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md) by using the <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="d64e3-104">Bu yöntem, bir görev koleksiyonu olarak temsil edilen birden çok zaman uyumsuz işlemi zaman uyumsuz olarak bekler.</span><span class="sxs-lookup"><span data-stu-id="d64e3-104">This method asynchronously awaits multiple asynchronous operations, which are represented as a collection of tasks.</span></span>  
  
 <span data-ttu-id="d64e3-105">Gözden geçirmede, Web sitelerinin farklı oranlarda indirdiğini fark etmiş olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d64e3-105">You might have noticed in the walkthrough that the websites download at different rates.</span></span> <span data-ttu-id="d64e3-106">Bazen Web sitelerinden biri çok yavaş olduğundan, kalan tüm indirmeleri gecikmekte.</span><span class="sxs-lookup"><span data-stu-id="d64e3-106">Sometimes one of the websites is very slow, which delays all the remaining downloads.</span></span> <span data-ttu-id="d64e3-107">Yönergede oluşturduğunuz zaman uyumsuz çözümleri çalıştırdığınızda, beklemek istemiyorsanız programı kolayca sonlandırabilir, ancak daha iyi bir seçenek, tüm indirmeleri aynı anda başlatıp daha hızlı karşıdan yüklemelerin devam etmesini sağlamak zorunda kalmadan devam edebilir.  gerekebilecek.</span><span class="sxs-lookup"><span data-stu-id="d64e3-107">When you run the asynchronous solutions that you build in the walkthrough, you can end the program easily if you don't want to wait, but a better option would be to start all the downloads at the same time and let faster downloads continue without waiting for the one that’s delayed.</span></span>  
  
 <span data-ttu-id="d64e3-108">`Task.WhenAll` Yöntemi bir görev koleksiyonuna uygularsınız.</span><span class="sxs-lookup"><span data-stu-id="d64e3-108">You apply the `Task.WhenAll` method to a collection of tasks.</span></span> <span data-ttu-id="d64e3-109">Uygulaması, koleksiyondaki `WhenAll` her görev tamamlanana kadar tamamlanmamış tek bir görev döndürür.</span><span class="sxs-lookup"><span data-stu-id="d64e3-109">The application of `WhenAll` returns a single task that isn’t complete until every task in the collection is completed.</span></span> <span data-ttu-id="d64e3-110">Görevler paralel olarak çalışır, ancak ek iş parçacığı oluşturulmaz.</span><span class="sxs-lookup"><span data-stu-id="d64e3-110">The tasks appear to run in parallel, but no additional threads are created.</span></span> <span data-ttu-id="d64e3-111">Görevler herhangi bir sırada tamamlanabilir.</span><span class="sxs-lookup"><span data-stu-id="d64e3-111">The tasks can complete in any order.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="d64e3-112">Aşağıdaki yordamlar, izlenecek yol içinde [geliştirilen zaman uyumsuz uygulamalara yönelik uzantıları anlatmaktadır: Async ve await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md)kullanarak Web 'e erişme.</span><span class="sxs-lookup"><span data-stu-id="d64e3-112">The following procedures describe extensions to the async applications that are developed in [Walkthrough: Accessing the Web by Using async and await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span> <span data-ttu-id="d64e3-113">Uygulamayı, izlenecek yolu tamamlayarak veya kodu [Geliştirici kodu örneklerinden](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)indirerek geliştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d64e3-113">You can develop the applications by either completing the walkthrough or downloading the code from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).</span></span>  
>   
>  <span data-ttu-id="d64e3-114">Örneği çalıştırmak için bilgisayarınızda Visual Studio 2012 veya sonraki bir sürümünün yüklü olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d64e3-114">To run the example, you must have Visual Studio 2012 or later installed on your computer.</span></span>  
  
### <a name="to-add-taskwhenall-to-your-geturlcontentsasync-solution"></a><span data-ttu-id="d64e3-115">GetURLContentsAsync çözümünüze Task. WhenAll eklemek için</span><span class="sxs-lookup"><span data-stu-id="d64e3-115">To add Task.WhenAll to your GetURLContentsAsync solution</span></span>  
  
1. <span data-ttu-id="d64e3-116">Yöntemi, `ProcessURLAsync` [izlenecek yolda geliştirilen ilk uygulamaya ekleyin: Async ve await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md)kullanarak Web 'e erişme.</span><span class="sxs-lookup"><span data-stu-id="d64e3-116">Add the `ProcessURLAsync` method to the first application that's developed in [Walkthrough: Accessing the Web by Using async and await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span>  
  
    - <span data-ttu-id="d64e3-117">Kodu [Geliştirici kodu örnekleri](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)' nden indirdiyseniz asyncwalkthrough projesini açın ve MainWindow.xaml.cs dosyasına ekleyin `ProcessURLAsync` .</span><span class="sxs-lookup"><span data-stu-id="d64e3-117">If you downloaded the code from  [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f), open the AsyncWalkthrough project, and then add `ProcessURLAsync` to the MainWindow.xaml.cs file.</span></span>  
  
    - <span data-ttu-id="d64e3-118">İzlenecek yolu tamamlayarak kodu geliştirdiyseniz, `ProcessURLAsync` `GetURLContentsAsync` yöntemini içeren uygulamaya ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d64e3-118">If you developed the code by completing the walkthrough, add `ProcessURLAsync` to the application that includes the `GetURLContentsAsync` method.</span></span> <span data-ttu-id="d64e3-119">Bu uygulama için MainWindow.xaml.cs dosyası, "Izlenecek yol içindeki tüm kod örnekleri" bölümünde yer aldığı ilk örnektir.</span><span class="sxs-lookup"><span data-stu-id="d64e3-119">The MainWindow.xaml.cs file for this application is the first example in the "Complete Code Examples from the Walkthrough" section.</span></span>  
  
     <span data-ttu-id="d64e3-120">Yöntemi, ilk izlenecek yolda içindeki `foreach` `SumPageSizesAsync` döngüsünün gövdesinde bulunan eylemleri birleştirir. `ProcessURLAsync`</span><span class="sxs-lookup"><span data-stu-id="d64e3-120">The `ProcessURLAsync` method consolidates the actions in the body of the `foreach` loop in `SumPageSizesAsync` in the original walkthrough.</span></span> <span data-ttu-id="d64e3-121">Yöntemi, belirtilen bir Web sitesinin içeriğini bir bayt dizisi olarak zaman uyumsuz olarak indirir ve bayt dizisinin uzunluğunu görüntüler ve döndürür.</span><span class="sxs-lookup"><span data-stu-id="d64e3-121">The method asynchronously downloads the contents of a specified website as a byte array, and then displays and returns the length of the byte array.</span></span>  
  
    ```csharp  
    private async Task<int> ProcessURLAsync(string url)  
    {  
        var byteArray = await GetURLContentsAsync(url);  
        DisplayResults(url, byteArray);  
        return byteArray.Length;  
    }  
    ```  
  
2. <span data-ttu-id="d64e3-122">Aşağıdaki kodun gösterdiği gibi, `foreach` içindeki `SumPageSizesAsync`döngüyü not edin veya silin.</span><span class="sxs-lookup"><span data-stu-id="d64e3-122">Comment out or delete the `foreach` loop in `SumPageSizesAsync`, as the following code shows.</span></span>  
  
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
  
3. <span data-ttu-id="d64e3-123">Bir görev koleksiyonu oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d64e3-123">Create a collection of tasks.</span></span> <span data-ttu-id="d64e3-124">Aşağıdaki kod, <xref:System.Linq.Enumerable.ToArray%2A> yöntemi tarafından yürütüldüğünde, her bir Web sitesinin içeriğini yükleyen bir görev koleksiyonu oluşturan bir [sorgu](../linq/index.md) tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d64e3-124">The following code defines a [query](../linq/index.md) that, when executed by the <xref:System.Linq.Enumerable.ToArray%2A> method, creates a collection of tasks that download the contents of each website.</span></span> <span data-ttu-id="d64e3-125">Sorgu değerlendirildiğinde görevler başlatılır.</span><span class="sxs-lookup"><span data-stu-id="d64e3-125">The tasks are started when the query is evaluated.</span></span>  
  
     <span data-ttu-id="d64e3-126">Bildirimi sonrasında yöntemine `SumPageSizesAsync` aşağıdaki kodu ekleyin. `urlList`</span><span class="sxs-lookup"><span data-stu-id="d64e3-126">Add the following code to method `SumPageSizesAsync` after the declaration of `urlList`.</span></span>  
  
    ```csharp  
    // Create a query.   
    IEnumerable<Task<int>> downloadTasksQuery =   
        from url in urlList select ProcessURLAsync(url);  
  
    // Use ToArray to execute the query and start the download tasks.  
    Task<int>[] downloadTasks = downloadTasksQuery.ToArray();  
    ```  
  
4. <span data-ttu-id="d64e3-127">Görev koleksiyonu için geçerlidir `Task.WhenAll`. `downloadTasks`</span><span class="sxs-lookup"><span data-stu-id="d64e3-127">Apply `Task.WhenAll` to the collection of tasks, `downloadTasks`.</span></span> <span data-ttu-id="d64e3-128">`Task.WhenAll`görev koleksiyonundaki tüm görevler tamamlandığında tamamlanan tek bir görev döndürür.</span><span class="sxs-lookup"><span data-stu-id="d64e3-128">`Task.WhenAll` returns a single task that finishes when all the tasks in the collection of tasks have completed.</span></span>  
  
     <span data-ttu-id="d64e3-129">Aşağıdaki örnekte, `await` ifadesi `WhenAll` döndüren tek görevin tamamlanmasını bekler.</span><span class="sxs-lookup"><span data-stu-id="d64e3-129">In the following example, the `await` expression awaits the completion of the single task that `WhenAll` returns.</span></span> <span data-ttu-id="d64e3-130">İfade, her tamsayının indirilen bir Web sitesinin uzunluğu olduğu bir tamsayılar dizisi olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="d64e3-130">The expression evaluates to an array of integers, where each integer is the length of a downloaded website.</span></span> <span data-ttu-id="d64e3-131">Önceki adımda eklediğiniz koddan hemen `SumPageSizesAsync`sonra aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d64e3-131">Add the following code to `SumPageSizesAsync`, just after the code that you added in the previous step.</span></span>  
  
    ```csharp  
    // Await the completion of all the running tasks.  
    int[] lengths = await Task.WhenAll(downloadTasks);  
  
    //// The previous line is equivalent to the following two statements.  
    //Task<int[]> whenAllTask = Task.WhenAll(downloadTasks);  
    //int[] lengths = await whenAllTask;  
    ```  
  
5. <span data-ttu-id="d64e3-132">Son olarak, tüm <xref:System.Linq.Enumerable.Sum%2A> Web sitelerinin uzunluklarının toplamını hesaplamak için yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="d64e3-132">Finally, use the <xref:System.Linq.Enumerable.Sum%2A> method to calculate the sum of the lengths of all the websites.</span></span> <span data-ttu-id="d64e3-133">Aşağıdaki satırı öğesine `SumPageSizesAsync`ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d64e3-133">Add the following line to `SumPageSizesAsync`.</span></span>  
  
    ```csharp  
    int total = lengths.Sum();  
    ```  
  
### <a name="to-add-taskwhenall-to-the-httpclientgetbytearrayasync-solution"></a><span data-ttu-id="d64e3-134">HttpClient. GetByteArrayAsync çözümüne Task. WhenAll eklemek için</span><span class="sxs-lookup"><span data-stu-id="d64e3-134">To add Task.WhenAll to the HttpClient.GetByteArrayAsync solution</span></span>  
  
1. <span data-ttu-id="d64e3-135">Aşağıdaki bir `ProcessURLAsync` sürümünü izlenecek yol içinde [geliştirilen ikinci uygulamaya ekleyin: Async ve await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md)kullanarak Web 'e erişme.</span><span class="sxs-lookup"><span data-stu-id="d64e3-135">Add the following version of `ProcessURLAsync` to the second application that's developed in [Walkthrough: Accessing the Web by Using async and await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span>  
  
    - <span data-ttu-id="d64e3-136">Kodu [Geliştirici kodu örnekleri](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)' nden indirdiyseniz, AsyncWalkthrough_HttpClient projesini açın ve MainWindow.xaml.cs dosyasına ekleyin `ProcessURLAsync` .</span><span class="sxs-lookup"><span data-stu-id="d64e3-136">If you downloaded the code from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f), open the AsyncWalkthrough_HttpClient project, and then add `ProcessURLAsync` to the MainWindow.xaml.cs file.</span></span>  
  
    - <span data-ttu-id="d64e3-137">İzlenecek yolu tamamlayarak kodu geliştirdiyseniz, `ProcessURLAsync` `HttpClient.GetByteArrayAsync` yöntemini kullanan uygulamaya ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d64e3-137">If you developed the code by completing the walkthrough, add `ProcessURLAsync` to the application that uses the `HttpClient.GetByteArrayAsync` method.</span></span> <span data-ttu-id="d64e3-138">Bu uygulama için MainWindow.xaml.cs dosyası, "Izlenecek yol ile ilgili tüm kod örnekleri" bölümünde yer aldığı ikinci örnektir.</span><span class="sxs-lookup"><span data-stu-id="d64e3-138">The MainWindow.xaml.cs file for this application is the second example in the "Complete Code Examples from the Walkthrough" section.</span></span>  
  
     <span data-ttu-id="d64e3-139">Yöntemi, ilk izlenecek yolda içindeki `foreach` `SumPageSizesAsync` döngüsünün gövdesinde bulunan eylemleri birleştirir. `ProcessURLAsync`</span><span class="sxs-lookup"><span data-stu-id="d64e3-139">The `ProcessURLAsync` method consolidates the actions in the body of the `foreach` loop in `SumPageSizesAsync` in the original walkthrough.</span></span> <span data-ttu-id="d64e3-140">Yöntemi, belirtilen bir Web sitesinin içeriğini bir bayt dizisi olarak zaman uyumsuz olarak indirir ve bayt dizisinin uzunluğunu görüntüler ve döndürür.</span><span class="sxs-lookup"><span data-stu-id="d64e3-140">The method asynchronously downloads the contents of a specified website as a byte array, and then displays and returns the length of the byte array.</span></span>  
  
     <span data-ttu-id="d64e3-141">Önceki yordamdaki `ProcessURLAsync` yöntemden tek fark, <xref:System.Net.Http.HttpClient> `client`örneği kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="d64e3-141">The only difference from the `ProcessURLAsync` method in the previous procedure is the use of the <xref:System.Net.Http.HttpClient> instance, `client`.</span></span>  
  
    ```csharp  
    async Task<int> ProcessURLAsync(string url, HttpClient client)  
    {  
        byte[] byteArray = await client.GetByteArrayAsync(url);  
        DisplayResults(url, byteArray);  
        return byteArray.Length;  
    }  
    ```  
  
2. <span data-ttu-id="d64e3-142">Aşağıdaki kodun gösterdiği gibi, `For Each` içindeki `foreach` `SumPageSizesAsync`veya döngüsünü açıklama veya silme.</span><span class="sxs-lookup"><span data-stu-id="d64e3-142">Comment out or delete the `For Each` or `foreach` loop in `SumPageSizesAsync`, as the following code shows.</span></span>  
  
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
  
3. <span data-ttu-id="d64e3-143"><xref:System.Linq.Enumerable.ToArray%2A> Yöntemi tarafından yürütüldüğünde, her bir Web sitesinin içeriğini yükleyen bir görev koleksiyonu oluşturan bir [sorgu](../linq/index.md) tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="d64e3-143">Define a [query](../linq/index.md) that, when executed by the <xref:System.Linq.Enumerable.ToArray%2A> method, creates a collection of tasks that download the contents of each website.</span></span> <span data-ttu-id="d64e3-144">Sorgu değerlendirildiğinde görevler başlatılır.</span><span class="sxs-lookup"><span data-stu-id="d64e3-144">The tasks are started when the query is evaluated.</span></span>  
  
     <span data-ttu-id="d64e3-145">Ve`client` bildirimindensonra`SumPageSizesAsync` yöntemine aşağıdaki kodu ekleyin. `urlList`</span><span class="sxs-lookup"><span data-stu-id="d64e3-145">Add the following code to method `SumPageSizesAsync` after the declaration of `client` and `urlList`.</span></span>  
  
    ```csharp  
    // Create a query.  
    IEnumerable<Task<int>> downloadTasksQuery =   
        from url in urlList select ProcessURLAsync(url, client);  
  
    // Use ToArray to execute the query and start the download tasks.  
    Task<int>[] downloadTasks = downloadTasksQuery.ToArray();  
    ```  
  
4. <span data-ttu-id="d64e3-146">Sonra, `Task.WhenAll` `downloadTasks`görev koleksiyonu için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="d64e3-146">Next, apply `Task.WhenAll` to the collection of tasks, `downloadTasks`.</span></span> <span data-ttu-id="d64e3-147">`Task.WhenAll`görev koleksiyonundaki tüm görevler tamamlandığında tamamlanan tek bir görev döndürür.</span><span class="sxs-lookup"><span data-stu-id="d64e3-147">`Task.WhenAll` returns a single task that finishes when all the tasks in the collection of tasks have completed.</span></span>  
  
     <span data-ttu-id="d64e3-148">Aşağıdaki örnekte, `await` ifadesi `WhenAll` döndüren tek görevin tamamlanmasını bekler.</span><span class="sxs-lookup"><span data-stu-id="d64e3-148">In the following example, the `await` expression awaits the completion of the single task that `WhenAll` returns.</span></span> <span data-ttu-id="d64e3-149">İşlem tamamlandığında, `await` ifade, her tamsayı indirilen bir Web sitesinin uzunluğu olduğu bir tamsayılar dizisi olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="d64e3-149">When complete, the `await` expression evaluates to an array of integers, where each integer is the length of a downloaded website.</span></span> <span data-ttu-id="d64e3-150">Önceki adımda eklediğiniz koddan hemen `SumPageSizesAsync`sonra aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d64e3-150">Add the following code to `SumPageSizesAsync`, just after the code that you added in the previous step.</span></span>  
  
    ```csharp  
    // Await the completion of all the running tasks.  
    int[] lengths = await Task.WhenAll(downloadTasks);  
  
    //// The previous line is equivalent to the following two statements.  
    //Task<int[]> whenAllTask = Task.WhenAll(downloadTasks);  
    //int[] lengths = await whenAllTask;  
    ```  
  
5. <span data-ttu-id="d64e3-151">Son olarak, tüm <xref:System.Linq.Enumerable.Sum%2A> Web sitelerinin uzunluklarının toplamını almak için yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="d64e3-151">Finally, use the <xref:System.Linq.Enumerable.Sum%2A> method to get the sum of the lengths of all the websites.</span></span> <span data-ttu-id="d64e3-152">Aşağıdaki satırı öğesine `SumPageSizesAsync`ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d64e3-152">Add the following line to `SumPageSizesAsync`.</span></span>  
  
    ```csharp  
    int total = lengths.Sum();
    ```  
  
### <a name="to-test-the-taskwhenall-solutions"></a><span data-ttu-id="d64e3-153">Task. WhenAll çözümlerini test etmek için</span><span class="sxs-lookup"><span data-stu-id="d64e3-153">To test the Task.WhenAll solutions</span></span>  
  
- <span data-ttu-id="d64e3-154">İki çözüm için, programı çalıştırmak için F5 tuşunu seçin ve ardından **Başlat** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="d64e3-154">For either solution, choose the F5 key to run the program, and then choose the **Start** button.</span></span> <span data-ttu-id="d64e3-155">Çıktı, [Gözden geçirmedeki zaman uyumsuz çözümlerin çıktısına benzer olmalıdır: Async ve await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md)kullanarak Web 'e erişme.</span><span class="sxs-lookup"><span data-stu-id="d64e3-155">The output should resemble the output from the async solutions in [Walkthrough: Accessing the Web by Using async and await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span> <span data-ttu-id="d64e3-156">Ancak, Web sitelerinin her seferinde farklı bir sırada görünmediğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="d64e3-156">However, notice that the websites appear in a different order each time.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d64e3-157">Örnek</span><span class="sxs-lookup"><span data-stu-id="d64e3-157">Example</span></span>  
 <span data-ttu-id="d64e3-158">Aşağıdaki kod, Web 'den içerik indirmek için `GetURLContentsAsync` yöntemini kullanan projenin uzantılarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d64e3-158">The following code shows the extensions to the project that uses the `GetURLContentsAsync` method to download content from the web.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="d64e3-159">Örnek</span><span class="sxs-lookup"><span data-stu-id="d64e3-159">Example</span></span>  
 <span data-ttu-id="d64e3-160">Aşağıdaki kod, Web 'den içerik indirmek için yöntemini `HttpClient.GetByteArrayAsync` kullanan projenin uzantılarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d64e3-160">The following code shows the extensions to the project that uses method `HttpClient.GetByteArrayAsync` to download content from the web.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d64e3-161">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d64e3-161">See also</span></span>

- <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>
- [<span data-ttu-id="d64e3-162">İzlenecek yol: Async ve await (C#) kullanarak Web 'e erişme</span><span class="sxs-lookup"><span data-stu-id="d64e3-162">Walkthrough: Accessing the Web by Using async and await (C#)</span></span>](./walkthrough-accessing-the-web-by-using-async-and-await.md)
