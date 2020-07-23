---
title: Task. WhenAll kullanarak zaman uyumsuz izlenecek yolu genişletme (C#)
description: Task. WhenAll kullanarak C# ' de zaman uyumsuz çözüm performansını geliştirmeyi öğrenin. Bu yöntem, birden çok zaman uyumsuz işlemi zaman uyumsuz olarak bekler.
ms.date: 07/20/2015
ms.assetid: f6927ef2-dc6c-43f8-bc82-bbeac42de423
ms.openlocfilehash: 275f4aeca854f8938642dbea40bf7fd9dc5362d9
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925221"
---
# <a name="how-to-extend-the-async-walkthrough-by-using-taskwhenall-c"></a><span data-ttu-id="92d02-104">Task. WhenAll kullanarak zaman uyumsuz izlenecek yolu genişletme (C#)</span><span class="sxs-lookup"><span data-stu-id="92d02-104">How to extend the async walkthrough by using Task.WhenAll (C#)</span></span>

<span data-ttu-id="92d02-105">Zaman uyumsuz çözümün performansını şu şekilde artırabilirsiniz: yöntemini kullanarak [, Async ve await (C#) kullanarak Web 'e erişme](./walkthrough-accessing-the-web-by-using-async-and-await.md) <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="92d02-105">You can improve the performance of the async solution in [Walkthrough: Accessing the Web by Using async and await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md) by using the <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="92d02-106">Bu yöntem, bir görev koleksiyonu olarak temsil edilen birden çok zaman uyumsuz işlemi zaman uyumsuz olarak bekler.</span><span class="sxs-lookup"><span data-stu-id="92d02-106">This method asynchronously awaits multiple asynchronous operations, which are represented as a collection of tasks.</span></span>

<span data-ttu-id="92d02-107">Gözden geçirmede, Web sitelerinin farklı oranlarda indirdiğini fark etmiş olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="92d02-107">You might have noticed in the walkthrough that the websites download at different rates.</span></span> <span data-ttu-id="92d02-108">Bazen Web sitelerinden biri çok yavaş olduğundan, kalan tüm indirmeleri gecikmekte.</span><span class="sxs-lookup"><span data-stu-id="92d02-108">Sometimes one of the websites is very slow, which delays all the remaining downloads.</span></span> <span data-ttu-id="92d02-109">Yönergede oluşturduğunuz zaman uyumsuz çözümleri çalıştırdığınızda, beklemek istemiyorsanız programı kolayca sonlandırabilir, ancak daha iyi bir seçenek, tüm indirmeleri aynı anda başlatmak ve geciktirilen bir süre beklemeden daha hızlı karşıdan yüklemelerin devam etmesini sağlamak olacaktır.</span><span class="sxs-lookup"><span data-stu-id="92d02-109">When you run the asynchronous solutions that you build in the walkthrough, you can end the program easily if you don't want to wait, but a better option would be to start all the downloads at the same time and let faster downloads continue without waiting for the one that’s delayed.</span></span>

<span data-ttu-id="92d02-110">`Task.WhenAll`Yöntemi bir görev koleksiyonuna uygularsınız.</span><span class="sxs-lookup"><span data-stu-id="92d02-110">You apply the `Task.WhenAll` method to a collection of tasks.</span></span> <span data-ttu-id="92d02-111">Uygulaması, `WhenAll` koleksiyondaki her görev tamamlanana kadar tamamlanmamış tek bir görev döndürür.</span><span class="sxs-lookup"><span data-stu-id="92d02-111">The application of `WhenAll` returns a single task that isn’t complete until every task in the collection is completed.</span></span> <span data-ttu-id="92d02-112">Görevler paralel olarak çalışır, ancak ek iş parçacığı oluşturulmaz.</span><span class="sxs-lookup"><span data-stu-id="92d02-112">The tasks appear to run in parallel, but no additional threads are created.</span></span> <span data-ttu-id="92d02-113">Görevler herhangi bir sırada tamamlanabilir.</span><span class="sxs-lookup"><span data-stu-id="92d02-113">The tasks can complete in any order.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="92d02-114">Aşağıdaki yordamlar, [Izlenecek yol: Async ve await (C#) kullanılarak Web 'e erişim](./walkthrough-accessing-the-web-by-using-async-and-await.md)için geliştirilmiş, zaman uyumsuz uygulamalara yönelik uzantıları anlatmaktadır.</span><span class="sxs-lookup"><span data-stu-id="92d02-114">The following procedures describe extensions to the async applications that are developed in [Walkthrough: Accessing the Web by Using async and await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span> <span data-ttu-id="92d02-115">Uygulamayı, izlenecek yolu tamamlayarak veya kodu [Geliştirici kodu örneklerinden](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)indirerek geliştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="92d02-115">You can develop the applications by either completing the walkthrough or downloading the code from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).</span></span>
>
> <span data-ttu-id="92d02-116">Örneği çalıştırmak için bilgisayarınızda Visual Studio 2012 veya sonraki bir sürümünün yüklü olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="92d02-116">To run the example, you must have Visual Studio 2012 or later installed on your computer.</span></span>

### <a name="to-add-taskwhenall-to-your-geturlcontentsasync-solution"></a><span data-ttu-id="92d02-117">GetURLContentsAsync çözümünüze Task. WhenAll eklemek için</span><span class="sxs-lookup"><span data-stu-id="92d02-117">To add Task.WhenAll to your GetURLContentsAsync solution</span></span>

1. <span data-ttu-id="92d02-118">Yöntemi, `ProcessURLAsync` [izlenecek yol: Async ve await (C#) kullanarak Web 'e erişme](./walkthrough-accessing-the-web-by-using-async-and-await.md)bölümünde geliştirilen ilk uygulamaya ekleyin.</span><span class="sxs-lookup"><span data-stu-id="92d02-118">Add the `ProcessURLAsync` method to the first application that's developed in [Walkthrough: Accessing the Web by Using async and await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span>

    - <span data-ttu-id="92d02-119">Kodu [Geliştirici kodu örnekleri](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)' nden Indirdiyseniz asyncwalkthrough projesini açın ve `ProcessURLAsync` MainWindow.xaml.cs dosyasına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="92d02-119">If you downloaded the code from  [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f), open the AsyncWalkthrough project, and then add `ProcessURLAsync` to the MainWindow.xaml.cs file.</span></span>

    - <span data-ttu-id="92d02-120">İzlenecek yolu tamamlayarak kodu geliştirdiyseniz, `ProcessURLAsync` yöntemini içeren uygulamaya ekleyin `GetURLContentsAsync` .</span><span class="sxs-lookup"><span data-stu-id="92d02-120">If you developed the code by completing the walkthrough, add `ProcessURLAsync` to the application that includes the `GetURLContentsAsync` method.</span></span> <span data-ttu-id="92d02-121">Bu uygulama için MainWindow.xaml.cs dosyası, "Izlenecek yol içindeki tüm kod örnekleri" bölümünde yer aldığı ilk örnektir.</span><span class="sxs-lookup"><span data-stu-id="92d02-121">The MainWindow.xaml.cs file for this application is the first example in the "Complete Code Examples from the Walkthrough" section.</span></span>

    <span data-ttu-id="92d02-122">`ProcessURLAsync`Yöntemi, `foreach` ilk izlenecek yolda içindeki döngüsünün gövdesinde bulunan eylemleri birleştirir `SumPageSizesAsync` .</span><span class="sxs-lookup"><span data-stu-id="92d02-122">The `ProcessURLAsync` method consolidates the actions in the body of the `foreach` loop in `SumPageSizesAsync` in the original walkthrough.</span></span> <span data-ttu-id="92d02-123">Yöntemi, belirtilen bir Web sitesinin içeriğini bir bayt dizisi olarak zaman uyumsuz olarak indirir ve bayt dizisinin uzunluğunu görüntüler ve döndürür.</span><span class="sxs-lookup"><span data-stu-id="92d02-123">The method asynchronously downloads the contents of a specified website as a byte array, and then displays and returns the length of the byte array.</span></span>

    ```csharp
    private async Task<int> ProcessURLAsync(string url)
    {
        var byteArray = await GetURLContentsAsync(url);
        DisplayResults(url, byteArray);
        return byteArray.Length;
    }
    ```

2. <span data-ttu-id="92d02-124">`foreach` `SumPageSizesAsync` Aşağıdaki kodun gösterdiği gibi, içindeki döngüyü not edin veya silin.</span><span class="sxs-lookup"><span data-stu-id="92d02-124">Comment out or delete the `foreach` loop in `SumPageSizesAsync`, as the following code shows.</span></span>

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

3. <span data-ttu-id="92d02-125">Bir görev koleksiyonu oluşturun.</span><span class="sxs-lookup"><span data-stu-id="92d02-125">Create a collection of tasks.</span></span> <span data-ttu-id="92d02-126">Aşağıdaki kod, yöntemi tarafından [query](../linq/index.md) yürütüldüğünde <xref:System.Linq.Enumerable.ToArray%2A> , her bir Web sitesinin içeriğini yükleyen bir görev koleksiyonu oluşturan bir sorgu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="92d02-126">The following code defines a [query](../linq/index.md) that, when executed by the <xref:System.Linq.Enumerable.ToArray%2A> method, creates a collection of tasks that download the contents of each website.</span></span> <span data-ttu-id="92d02-127">Sorgu değerlendirildiğinde görevler başlatılır.</span><span class="sxs-lookup"><span data-stu-id="92d02-127">The tasks are started when the query is evaluated.</span></span>

    <span data-ttu-id="92d02-128">Bildirimi sonrasında yöntemine aşağıdaki kodu ekleyin `SumPageSizesAsync` `urlList` .</span><span class="sxs-lookup"><span data-stu-id="92d02-128">Add the following code to method `SumPageSizesAsync` after the declaration of `urlList`.</span></span>

    ```csharp
    // Create a query.
    IEnumerable<Task<int>> downloadTasksQuery =
        from url in urlList select ProcessURLAsync(url);

    // Use ToArray to execute the query and start the download tasks.
    Task<int>[] downloadTasks = downloadTasksQuery.ToArray();
    ```

4. <span data-ttu-id="92d02-129">`Task.WhenAll`Görev koleksiyonu için geçerlidir `downloadTasks` .</span><span class="sxs-lookup"><span data-stu-id="92d02-129">Apply `Task.WhenAll` to the collection of tasks, `downloadTasks`.</span></span> <span data-ttu-id="92d02-130">`Task.WhenAll`görev koleksiyonundaki tüm görevler tamamlandığında tamamlanan tek bir görev döndürür.</span><span class="sxs-lookup"><span data-stu-id="92d02-130">`Task.WhenAll` returns a single task that finishes when all the tasks in the collection of tasks have completed.</span></span>

    <span data-ttu-id="92d02-131">Aşağıdaki örnekte, `await` ifadesi döndüren tek görevin tamamlanmasını bekler `WhenAll` .</span><span class="sxs-lookup"><span data-stu-id="92d02-131">In the following example, the `await` expression awaits the completion of the single task that `WhenAll` returns.</span></span> <span data-ttu-id="92d02-132">İfade, her tamsayının indirilen bir Web sitesinin uzunluğu olduğu bir tamsayılar dizisi olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="92d02-132">The expression evaluates to an array of integers, where each integer is the length of a downloaded website.</span></span> <span data-ttu-id="92d02-133">`SumPageSizesAsync`Önceki adımda eklediğiniz koddan hemen sonra aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="92d02-133">Add the following code to `SumPageSizesAsync`, just after the code that you added in the previous step.</span></span>

    ```csharp
    // Await the completion of all the running tasks.
    int[] lengths = await Task.WhenAll(downloadTasks);

    //// The previous line is equivalent to the following two statements.
    //Task<int[]> whenAllTask = Task.WhenAll(downloadTasks);
    //int[] lengths = await whenAllTask;
    ```

5. <span data-ttu-id="92d02-134">Son olarak, <xref:System.Linq.Enumerable.Sum%2A> tüm Web sitelerinin uzunluklarının toplamını hesaplamak için yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="92d02-134">Finally, use the <xref:System.Linq.Enumerable.Sum%2A> method to calculate the sum of the lengths of all the websites.</span></span> <span data-ttu-id="92d02-135">Aşağıdaki satırı öğesine ekleyin `SumPageSizesAsync` .</span><span class="sxs-lookup"><span data-stu-id="92d02-135">Add the following line to `SumPageSizesAsync`.</span></span>

    ```csharp
    int total = lengths.Sum();
    ```

### <a name="to-add-taskwhenall-to-the-httpclientgetbytearrayasync-solution"></a><span data-ttu-id="92d02-136">HttpClient. GetByteArrayAsync çözümüne Task. WhenAll eklemek için</span><span class="sxs-lookup"><span data-stu-id="92d02-136">To add Task.WhenAll to the HttpClient.GetByteArrayAsync solution</span></span>

1. <span data-ttu-id="92d02-137">Aşağıdaki sürümünü, `ProcessURLAsync` [izlenecek yol: Async ve await (C#) kullanarak Web 'e erişme](./walkthrough-accessing-the-web-by-using-async-and-await.md)bölümünde geliştirilen ikinci uygulamaya ekleyin.</span><span class="sxs-lookup"><span data-stu-id="92d02-137">Add the following version of `ProcessURLAsync` to the second application that's developed in [Walkthrough: Accessing the Web by Using async and await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span>

    - <span data-ttu-id="92d02-138">Kodu [Geliştirici kodu örnekleri](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)' nden indirdiyseniz, AsyncWalkthrough_HttpClient projesini açın ve sonra `ProcessURLAsync` MainWindow.xaml.cs dosyasına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="92d02-138">If you downloaded the code from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f), open the AsyncWalkthrough_HttpClient project, and then add `ProcessURLAsync` to the MainWindow.xaml.cs file.</span></span>

    - <span data-ttu-id="92d02-139">İzlenecek yolu tamamlayarak kodu geliştirdiyseniz, `ProcessURLAsync` yöntemini kullanan uygulamaya ekleyin `HttpClient.GetByteArrayAsync` .</span><span class="sxs-lookup"><span data-stu-id="92d02-139">If you developed the code by completing the walkthrough, add `ProcessURLAsync` to the application that uses the `HttpClient.GetByteArrayAsync` method.</span></span> <span data-ttu-id="92d02-140">Bu uygulama için MainWindow.xaml.cs dosyası, "Izlenecek yol ile ilgili tüm kod örnekleri" bölümünde yer aldığı ikinci örnektir.</span><span class="sxs-lookup"><span data-stu-id="92d02-140">The MainWindow.xaml.cs file for this application is the second example in the "Complete Code Examples from the Walkthrough" section.</span></span>

    <span data-ttu-id="92d02-141">`ProcessURLAsync`Yöntemi, `foreach` ilk izlenecek yolda içindeki döngüsünün gövdesinde bulunan eylemleri birleştirir `SumPageSizesAsync` .</span><span class="sxs-lookup"><span data-stu-id="92d02-141">The `ProcessURLAsync` method consolidates the actions in the body of the `foreach` loop in `SumPageSizesAsync` in the original walkthrough.</span></span> <span data-ttu-id="92d02-142">Yöntemi, belirtilen bir Web sitesinin içeriğini bir bayt dizisi olarak zaman uyumsuz olarak indirir ve bayt dizisinin uzunluğunu görüntüler ve döndürür.</span><span class="sxs-lookup"><span data-stu-id="92d02-142">The method asynchronously downloads the contents of a specified website as a byte array, and then displays and returns the length of the byte array.</span></span>

    <span data-ttu-id="92d02-143">`ProcessURLAsync`Önceki yordamdaki yöntemden tek fark <xref:System.Net.Http.HttpClient> , örneği kullanmaktır `client` .</span><span class="sxs-lookup"><span data-stu-id="92d02-143">The only difference from the `ProcessURLAsync` method in the previous procedure is the use of the <xref:System.Net.Http.HttpClient> instance, `client`.</span></span>

    ```csharp
    async Task<int> ProcessURLAsync(string url, HttpClient client)
    {
        byte[] byteArray = await client.GetByteArrayAsync(url);
        DisplayResults(url, byteArray);
        return byteArray.Length;
    }
    ```

2. <span data-ttu-id="92d02-144">`For Each` `foreach` Aşağıdaki kodun gösterdiği gibi, içindeki veya döngüsünü açıklama veya silme `SumPageSizesAsync` .</span><span class="sxs-lookup"><span data-stu-id="92d02-144">Comment out or delete the `For Each` or `foreach` loop in `SumPageSizesAsync`, as the following code shows.</span></span>

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

3. <span data-ttu-id="92d02-145">Yöntemi tarafından [query](../linq/index.md) yürütüldüğünde <xref:System.Linq.Enumerable.ToArray%2A> , her bir Web sitesinin içeriğini yükleyen bir görev koleksiyonu oluşturan bir sorgu tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="92d02-145">Define a [query](../linq/index.md) that, when executed by the <xref:System.Linq.Enumerable.ToArray%2A> method, creates a collection of tasks that download the contents of each website.</span></span> <span data-ttu-id="92d02-146">Sorgu değerlendirildiğinde görevler başlatılır.</span><span class="sxs-lookup"><span data-stu-id="92d02-146">The tasks are started when the query is evaluated.</span></span>

    <span data-ttu-id="92d02-147">Ve bildiriminden sonra yöntemine aşağıdaki kodu ekleyin `SumPageSizesAsync` `client` `urlList` .</span><span class="sxs-lookup"><span data-stu-id="92d02-147">Add the following code to method `SumPageSizesAsync` after the declaration of `client` and `urlList`.</span></span>

    ```csharp
    // Create a query.
    IEnumerable<Task<int>> downloadTasksQuery =
        from url in urlList select ProcessURLAsync(url, client);

    // Use ToArray to execute the query and start the download tasks.
    Task<int>[] downloadTasks = downloadTasksQuery.ToArray();
    ```

4. <span data-ttu-id="92d02-148">Sonra, `Task.WhenAll` görev koleksiyonu için geçerlidir `downloadTasks` .</span><span class="sxs-lookup"><span data-stu-id="92d02-148">Next, apply `Task.WhenAll` to the collection of tasks, `downloadTasks`.</span></span> <span data-ttu-id="92d02-149">`Task.WhenAll`görev koleksiyonundaki tüm görevler tamamlandığında tamamlanan tek bir görev döndürür.</span><span class="sxs-lookup"><span data-stu-id="92d02-149">`Task.WhenAll` returns a single task that finishes when all the tasks in the collection of tasks have completed.</span></span>

    <span data-ttu-id="92d02-150">Aşağıdaki örnekte, `await` ifadesi döndüren tek görevin tamamlanmasını bekler `WhenAll` .</span><span class="sxs-lookup"><span data-stu-id="92d02-150">In the following example, the `await` expression awaits the completion of the single task that `WhenAll` returns.</span></span> <span data-ttu-id="92d02-151">İşlem tamamlandığında, `await` ifade, her tamsayı indirilen bir Web sitesinin uzunluğu olduğu bir tamsayılar dizisi olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="92d02-151">When complete, the `await` expression evaluates to an array of integers, where each integer is the length of a downloaded website.</span></span> <span data-ttu-id="92d02-152">`SumPageSizesAsync`Önceki adımda eklediğiniz koddan hemen sonra aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="92d02-152">Add the following code to `SumPageSizesAsync`, just after the code that you added in the previous step.</span></span>

    ```csharp
    // Await the completion of all the running tasks.
    int[] lengths = await Task.WhenAll(downloadTasks);

    //// The previous line is equivalent to the following two statements.
    //Task<int[]> whenAllTask = Task.WhenAll(downloadTasks);
    //int[] lengths = await whenAllTask;
    ```

5. <span data-ttu-id="92d02-153">Son olarak, <xref:System.Linq.Enumerable.Sum%2A> tüm Web sitelerinin uzunluklarının toplamını almak için yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="92d02-153">Finally, use the <xref:System.Linq.Enumerable.Sum%2A> method to get the sum of the lengths of all the websites.</span></span> <span data-ttu-id="92d02-154">Aşağıdaki satırı öğesine ekleyin `SumPageSizesAsync` .</span><span class="sxs-lookup"><span data-stu-id="92d02-154">Add the following line to `SumPageSizesAsync`.</span></span>

    ```csharp
    int total = lengths.Sum();
    ```

### <a name="to-test-the-taskwhenall-solutions"></a><span data-ttu-id="92d02-155">Task. WhenAll çözümlerini test etmek için</span><span class="sxs-lookup"><span data-stu-id="92d02-155">To test the Task.WhenAll solutions</span></span>

- <span data-ttu-id="92d02-156">İki çözüm için, programı çalıştırmak için F5 tuşunu seçin ve ardından **Başlat** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="92d02-156">For either solution, choose the F5 key to run the program, and then choose the **Start** button.</span></span> <span data-ttu-id="92d02-157">Çıktı, [Izlenecek yol: Async ve await (C#) kullanarak Web 'e erişmek](./walkthrough-accessing-the-web-by-using-async-and-await.md)için zaman uyumsuz çözümlerin çıktısına benzer olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="92d02-157">The output should resemble the output from the async solutions in [Walkthrough: Accessing the Web by Using async and await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span> <span data-ttu-id="92d02-158">Ancak, Web sitelerinin her seferinde farklı bir sırada görünmediğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="92d02-158">However, notice that the websites appear in a different order each time.</span></span>

## <a name="example"></a><span data-ttu-id="92d02-159">Örnek</span><span class="sxs-lookup"><span data-stu-id="92d02-159">Example</span></span>

<span data-ttu-id="92d02-160">Aşağıdaki kod, `GetURLContentsAsync` Web 'den içerik indirmek için yöntemini kullanan projenin uzantılarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="92d02-160">The following code shows the extensions to the project that uses the `GetURLContentsAsync` method to download content from the web.</span></span>

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

## <a name="example"></a><span data-ttu-id="92d02-161">Örnek</span><span class="sxs-lookup"><span data-stu-id="92d02-161">Example</span></span>

<span data-ttu-id="92d02-162">Aşağıdaki kod, `HttpClient.GetByteArrayAsync` Web 'den içerik indirmek için yöntemini kullanan projenin uzantılarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="92d02-162">The following code shows the extensions to the project that uses method `HttpClient.GetByteArrayAsync` to download content from the web.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="92d02-163">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="92d02-163">See also</span></span>

- <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>
- [<span data-ttu-id="92d02-164">İzlenecek yol: Async ve await kullanarak Web 'e erişme (C#)</span><span class="sxs-lookup"><span data-stu-id="92d02-164">Walkthrough: Accessing the Web by Using async and await (C#)</span></span>](./walkthrough-accessing-the-web-by-using-async-and-await.md)
