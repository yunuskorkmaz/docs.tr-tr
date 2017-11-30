---
title: "Nasıl yapılır: Task.WhenAll (C#) kullanarak tarafından izlenecek zaman uyumsuz genişletme"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: f6927ef2-dc6c-43f8-bc82-bbeac42de423
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: a83ceb8a58104cc7a4c177ce6c7df9aded8af7e1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-extend-the-async-walkthrough-by-using-taskwhenall-c"></a><span data-ttu-id="7aa1e-102">Nasıl yapılır: Task.WhenAll (C#) kullanarak tarafından izlenecek zaman uyumsuz genişletme</span><span class="sxs-lookup"><span data-stu-id="7aa1e-102">How to: Extend the async Walkthrough by Using Task.WhenAll (C#)</span></span>
<span data-ttu-id="7aa1e-103">Zaman uyumsuz çözümde performansını artırabilir [izlenecek yol: async kullanarak Web'e erişme ve await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md) kullanarak <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="7aa1e-103">You can improve the performance of the async solution in [Walkthrough: Accessing the Web by Using async and await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md) by using the <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="7aa1e-104">Bu yöntem, zaman uyumsuz olarak görevleri koleksiyonu temsil edilir birden çok zaman uyumsuz işlemleri bekler.</span><span class="sxs-lookup"><span data-stu-id="7aa1e-104">This method asynchronously awaits multiple asynchronous operations, which are represented as a collection of tasks.</span></span>  
  
 <span data-ttu-id="7aa1e-105">Web siteleri farklı hızlarda karşıdan kılavuzda fark.</span><span class="sxs-lookup"><span data-stu-id="7aa1e-105">You might have noticed in the walkthrough that the websites download at different rates.</span></span> <span data-ttu-id="7aa1e-106">Bazen, Web siteleri, kalan tüm indirmeleri gecikmeler çok yavaş biridir.</span><span class="sxs-lookup"><span data-stu-id="7aa1e-106">Sometimes one of the websites is very slow, which delays all the remaining downloads.</span></span> <span data-ttu-id="7aa1e-107">Kılavuzda oluşturacağınız zaman uyumsuz çözümleri çalıştırdığınızda, program kolayca beklemek istemiyorsanız, ancak aynı zamanda tüm indirmeleri başlatmak ve biri, beklemeden devam daha hızlı indirmeler izin vermek için daha iyi bir seçenek olacaktır sonlandırabilirsiniz 's  ertelendi.</span><span class="sxs-lookup"><span data-stu-id="7aa1e-107">When you run the asynchronous solutions that you build in the walkthrough, you can end the program easily if you don't want to wait, but a better option would be to start all the downloads at the same time and let faster downloads continue without waiting for the one that’s delayed.</span></span>  
  
 <span data-ttu-id="7aa1e-108">Uyguladığınız `Task.WhenAll` yöntemine görevleri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="7aa1e-108">You apply the `Task.WhenAll` method to a collection of tasks.</span></span> <span data-ttu-id="7aa1e-109">Uygulamayı `WhenAll` koleksiyondaki her görev tamamlanana kadar tamamlanmadıysa tek bir görev döndürür.</span><span class="sxs-lookup"><span data-stu-id="7aa1e-109">The application of `WhenAll` returns a single task that isn’t complete until every task in the collection is completed.</span></span> <span data-ttu-id="7aa1e-110">Paralel olarak çalıştırmak için görevler görüntülenir, ancak hiçbir ek iş parçacığı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="7aa1e-110">The tasks appear to run in parallel, but no additional threads are created.</span></span> <span data-ttu-id="7aa1e-111">Herhangi bir sırada görevleri gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7aa1e-111">The tasks can complete in any order.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7aa1e-112">Aşağıdaki yordamlar uzantıları da geliştirilmiş zaman uyumsuz uygulamalara açıklar [izlenecek yol: async kullanarak Web'e erişme ve await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="7aa1e-112">The following procedures describe extensions to the async applications that are developed in [Walkthrough: Accessing the Web by Using async and await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span> <span data-ttu-id="7aa1e-113">Kılavuzu tamamladıktan veya koddan indirme uygulamaları geliştirmek [Geliştirici kod örnekleri](http://go.microsoft.com/fwlink/?LinkId=255191).</span><span class="sxs-lookup"><span data-stu-id="7aa1e-113">You can develop the applications by either completing the walkthrough or downloading the code from [Developer Code Samples](http://go.microsoft.com/fwlink/?LinkId=255191).</span></span>  
>   
>  <span data-ttu-id="7aa1e-114">Örneği çalıştırmak için Visual Studio 2012 veya daha sonra bilgisayarınıza yüklenmiş olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7aa1e-114">To run the example, you must have Visual Studio 2012 or later installed on your computer.</span></span>  
  
### <a name="to-add-taskwhenall-to-your-geturlcontentsasync-solution"></a><span data-ttu-id="7aa1e-115">Task.WhenAll GetURLContentsAsync çözümünüze eklemek için</span><span class="sxs-lookup"><span data-stu-id="7aa1e-115">To add Task.WhenAll to your GetURLContentsAsync solution</span></span>  
  
1.  <span data-ttu-id="7aa1e-116">Ekleme `ProcessURLAsync` da geliştirilmiş ilk uygulamaya yöntemi [izlenecek yol: async kullanarak Web'e erişme ve await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="7aa1e-116">Add the `ProcessURLAsync` method to the first application that's developed in [Walkthrough: Accessing the Web by Using async and await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span>  
  
    -   <span data-ttu-id="7aa1e-117">Koddan yüklediyseniz [Geliştirici kod örnekleri](http://go.microsoft.com/fwlink/?LinkId=255191)AsyncWalkthrough projesini açın ve ardından ekleyin `ProcessURLAsync` MainWindow.xaml.cs dosyasına kayıt yapar.</span><span class="sxs-lookup"><span data-stu-id="7aa1e-117">If you downloaded the code from  [Developer Code Samples](http://go.microsoft.com/fwlink/?LinkId=255191), open the AsyncWalkthrough project, and then add `ProcessURLAsync` to the MainWindow.xaml.cs file.</span></span>  
  
    -   <span data-ttu-id="7aa1e-118">Kod gözden geçirme tamamlayarak geliştirdiyseniz eklemek `ProcessURLAsync` içeren uygulamaya `GetURLContentsAsync` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="7aa1e-118">If you developed the code by completing the walkthrough, add `ProcessURLAsync` to the application that includes the `GetURLContentsAsync` method.</span></span> <span data-ttu-id="7aa1e-119">İlk örnek "Tam kod örnekleri gelen izlenecek yolu" bölümünde bu uygulama için MainWindow.xaml.cs dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="7aa1e-119">The MainWindow.xaml.cs file for this application is the first example in the "Complete Code Examples from the Walkthrough" section.</span></span>  
  
     <span data-ttu-id="7aa1e-120">`ProcessURLAsync` Yöntemi birleştirir gövdesini Eylemler `foreach` içinde döngü `SumPageSizesAsync` özgün izlenecek adımları.</span><span class="sxs-lookup"><span data-stu-id="7aa1e-120">The `ProcessURLAsync` method consolidates the actions in the body of the `foreach` loop in `SumPageSizesAsync` in the original walkthrough.</span></span> <span data-ttu-id="7aa1e-121">Metodu zaman uyumsuz olarak bir bayt dizisi olarak belirtilen bir Web sitesi içeriğini indirir ve ardından görüntüler ve bayt dizisi uzunluğunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="7aa1e-121">The method asynchronously downloads the contents of a specified website as a byte array, and then displays and returns the length of the byte array.</span></span>  
  
    ```csharp  
    private async Task<int> ProcessURLAsync(string url)  
    {  
        var byteArray = await GetURLContentsAsync(url);  
        DisplayResults(url, byteArray);  
        return byteArray.Length;  
    }  
    ```  
  
2.  <span data-ttu-id="7aa1e-122">Out yorum yapmak veya silme `foreach` içinde döngü `SumPageSizesAsync`, aşağıdaki kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="7aa1e-122">Comment out or delete the `foreach` loop in `SumPageSizesAsync`, as the following code shows.</span></span>  
  
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
  
3.  <span data-ttu-id="7aa1e-123">Bir görev koleksiyonunu oluşturun.</span><span class="sxs-lookup"><span data-stu-id="7aa1e-123">Create a collection of tasks.</span></span> <span data-ttu-id="7aa1e-124">Aşağıdaki kodu tanımlayan bir [sorgu](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) , tarafından çalıştırıldığında <xref:System.Linq.Enumerable.ToArray%2A> yöntemi, her Web sitesi içeriğini indirme görevleri koleksiyonu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7aa1e-124">The following code defines a [query](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) that, when executed by the <xref:System.Linq.Enumerable.ToArray%2A> method, creates a collection of tasks that download the contents of each website.</span></span> <span data-ttu-id="7aa1e-125">Sorgu değerlendirildiğinde görevleri başlatılır.</span><span class="sxs-lookup"><span data-stu-id="7aa1e-125">The tasks are started when the query is evaluated.</span></span>  
  
     <span data-ttu-id="7aa1e-126">Yöntemine aşağıdaki kodu ekleyin `SumPageSizesAsync` bildirimi sonra `urlList`.</span><span class="sxs-lookup"><span data-stu-id="7aa1e-126">Add the following code to method `SumPageSizesAsync` after the declaration of `urlList`.</span></span>  
  
    ```csharp  
    // Create a query.   
    IEnumerable<Task<int>> downloadTasksQuery =   
        from url in urlList select ProcessURLAsync(url);  
  
    // Use ToArray to execute the query and start the download tasks.  
    Task<int>[] downloadTasks = downloadTasksQuery.ToArray();  
    ```  
  
4.  <span data-ttu-id="7aa1e-127">Uygulama `Task.WhenAll` görevleri koleksiyonu için `downloadTasks`.</span><span class="sxs-lookup"><span data-stu-id="7aa1e-127">Apply `Task.WhenAll` to the collection of tasks, `downloadTasks`.</span></span> <span data-ttu-id="7aa1e-128">`Task.WhenAll`görevlerin koleksiyonundaki tüm görevler tamamlandığında bittikten tek bir görev döndürür.</span><span class="sxs-lookup"><span data-stu-id="7aa1e-128">`Task.WhenAll` returns a single task that finishes when all the tasks in the collection of tasks have completed.</span></span>  
  
     <span data-ttu-id="7aa1e-129">Aşağıdaki örnekte, `await` ifade tek tamamlanmasını bekler, görev `WhenAll` döndürür.</span><span class="sxs-lookup"><span data-stu-id="7aa1e-129">In the following example, the `await` expression awaits the completion of the single task that `WhenAll` returns.</span></span> <span data-ttu-id="7aa1e-130">Dizisi her tamsayı indirilen bir Web sitesi uzunluğu olduğu, için ifadeyi hesaplar.</span><span class="sxs-lookup"><span data-stu-id="7aa1e-130">The expression evaluates to an array of integers, where each integer is the length of a downloaded website.</span></span> <span data-ttu-id="7aa1e-131">Aşağıdaki kodu ekleyin `SumPageSizesAsync`, yalnızca önceki adımda eklediğiniz koddan sonra.</span><span class="sxs-lookup"><span data-stu-id="7aa1e-131">Add the following code to `SumPageSizesAsync`, just after the code that you added in the previous step.</span></span>  
  
    ```csharp  
    // Await the completion of all the running tasks.  
    int[] lengths = await Task.WhenAll(downloadTasks);  
  
    //// The previous line is equivalent to the following two statements.  
    //Task<int[]> whenAllTask = Task.WhenAll(downloadTasks);  
    //int[] lengths = await whenAllTask;  
    ```  
  
5.  <span data-ttu-id="7aa1e-132">Son olarak, <xref:System.Linq.Enumerable.Sum%2A> tüm Web siteleri uzunlukları toplamı hesaplamak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="7aa1e-132">Finally, use the <xref:System.Linq.Enumerable.Sum%2A> method to calculate the sum of the lengths of all the websites.</span></span> <span data-ttu-id="7aa1e-133">Aşağıdaki satırı ekleyin `SumPageSizesAsync`.</span><span class="sxs-lookup"><span data-stu-id="7aa1e-133">Add the following line to `SumPageSizesAsync`.</span></span>  
  
    ```csharp  
    int total = lengths.Sum();  
    ```  
  
### <a name="to-add-taskwhenall-to-the-httpclientgetbytearrayasync-solution"></a><span data-ttu-id="7aa1e-134">Task.WhenAll HttpClient.GetByteArrayAsync çözüme eklemek için</span><span class="sxs-lookup"><span data-stu-id="7aa1e-134">To add Task.WhenAll to the HttpClient.GetByteArrayAsync solution</span></span>  
  
1.  <span data-ttu-id="7aa1e-135">Aşağıdaki sürümü eklemek `ProcessURLAsync` da geliştirilmiş ikinci uygulamaya [izlenecek yol: async kullanarak Web'e erişme ve await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="7aa1e-135">Add the following version of `ProcessURLAsync` to the second application that's developed in [Walkthrough: Accessing the Web by Using async and await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span>  
  
    -   <span data-ttu-id="7aa1e-136">Koddan yüklediyseniz [Geliştirici kod örnekleri](http://go.microsoft.com/fwlink/?LinkId=255191)AsyncWalkthrough_HttpClient projesini açın ve ardından ekleyin `ProcessURLAsync` MainWindow.xaml.cs dosyasına kayıt yapar.</span><span class="sxs-lookup"><span data-stu-id="7aa1e-136">If you downloaded the code from [Developer Code Samples](http://go.microsoft.com/fwlink/?LinkId=255191), open the AsyncWalkthrough_HttpClient project, and then add `ProcessURLAsync` to the MainWindow.xaml.cs file.</span></span>  
  
    -   <span data-ttu-id="7aa1e-137">Kod gözden geçirme tamamlayarak geliştirdiyseniz eklemek `ProcessURLAsync` kullanan uygulama için `HttpClient.GetByteArrayAsync` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="7aa1e-137">If you developed the code by completing the walkthrough, add `ProcessURLAsync` to the application that uses the `HttpClient.GetByteArrayAsync` method.</span></span> <span data-ttu-id="7aa1e-138">Bu uygulama için MainWindow.xaml.cs "Tam kod örnekleri gelen izlenecek yolu" bölümündeki ikinci örneğe dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="7aa1e-138">The MainWindow.xaml.cs file for this application is the second example in the "Complete Code Examples from the Walkthrough" section.</span></span>  
  
     <span data-ttu-id="7aa1e-139">`ProcessURLAsync` Yöntemi birleştirir gövdesini Eylemler `foreach` içinde döngü `SumPageSizesAsync` özgün izlenecek adımları.</span><span class="sxs-lookup"><span data-stu-id="7aa1e-139">The `ProcessURLAsync` method consolidates the actions in the body of the `foreach` loop in `SumPageSizesAsync` in the original walkthrough.</span></span> <span data-ttu-id="7aa1e-140">Metodu zaman uyumsuz olarak bir bayt dizisi olarak belirtilen bir Web sitesi içeriğini indirir ve ardından görüntüler ve bayt dizisi uzunluğunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="7aa1e-140">The method asynchronously downloads the contents of a specified website as a byte array, and then displays and returns the length of the byte array.</span></span>  
  
     <span data-ttu-id="7aa1e-141">Tek farkı `ProcessURLAsync` yöntemidir önceki yordamda kullanımını <xref:System.Net.Http.HttpClient> örneği `client`.</span><span class="sxs-lookup"><span data-stu-id="7aa1e-141">The only difference from the `ProcessURLAsync` method in the previous procedure is the use of the <xref:System.Net.Http.HttpClient> instance, `client`.</span></span>  
  
    ```csharp  
    async Task<int> ProcessURL(string url, HttpClient client)  
    {  
        byte[] byteArray = await client.GetByteArrayAsync(url);  
        DisplayResults(url, byteArray);  
        return byteArray.Length;  
    }  
    ```  
  
2.  <span data-ttu-id="7aa1e-142">Out yorum yapmak veya silme `For Each` veya `foreach` içinde döngü `SumPageSizesAsync`, aşağıdaki kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="7aa1e-142">Comment out or delete the `For Each` or `foreach` loop in `SumPageSizesAsync`, as the following code shows.</span></span>  
  
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
  
3.  <span data-ttu-id="7aa1e-143">Tanımlayan bir [sorgu](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) , tarafından çalıştırıldığında <xref:System.Linq.Enumerable.ToArray%2A> yöntemi, her Web sitesi içeriğini indirme görevleri koleksiyonu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7aa1e-143">Define a [query](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) that, when executed by the <xref:System.Linq.Enumerable.ToArray%2A> method, creates a collection of tasks that download the contents of each website.</span></span> <span data-ttu-id="7aa1e-144">Sorgu değerlendirildiğinde görevleri başlatılır.</span><span class="sxs-lookup"><span data-stu-id="7aa1e-144">The tasks are started when the query is evaluated.</span></span>  
  
     <span data-ttu-id="7aa1e-145">Yöntemine aşağıdaki kodu ekleyin `SumPageSizesAsync` bildirimi sonra `client` ve `urlList`.</span><span class="sxs-lookup"><span data-stu-id="7aa1e-145">Add the following code to method `SumPageSizesAsync` after the declaration of `client` and `urlList`.</span></span>  
  
    ```csharp  
    // Create a query.  
    IEnumerable<Task<int>> downloadTasksQuery =   
        from url in urlList select ProcessURL(url, client);  
  
    // Use ToArray to execute the query and start the download tasks.  
    Task<int>[] downloadTasks = downloadTasksQuery.ToArray();  
    ```  
  
4.  <span data-ttu-id="7aa1e-146">Ardından, uygulama `Task.WhenAll` görevleri koleksiyonu için `downloadTasks`.</span><span class="sxs-lookup"><span data-stu-id="7aa1e-146">Next, apply `Task.WhenAll` to the collection of tasks, `downloadTasks`.</span></span> <span data-ttu-id="7aa1e-147">`Task.WhenAll`görevlerin koleksiyonundaki tüm görevler tamamlandığında bittikten tek bir görev döndürür.</span><span class="sxs-lookup"><span data-stu-id="7aa1e-147">`Task.WhenAll` returns a single task that finishes when all the tasks in the collection of tasks have completed.</span></span>  
  
     <span data-ttu-id="7aa1e-148">Aşağıdaki örnekte, `await` ifade tek tamamlanmasını bekler, görev `WhenAll` döndürür.</span><span class="sxs-lookup"><span data-stu-id="7aa1e-148">In the following example, the `await` expression awaits the completion of the single task that `WhenAll` returns.</span></span> <span data-ttu-id="7aa1e-149">Tamamlandığında, `await` dizisi her tamsayı indirilen bir Web sitesi uzunluğu olduğu, için ifadeyi hesaplar.</span><span class="sxs-lookup"><span data-stu-id="7aa1e-149">When complete, the `await` expression evaluates to an array of integers, where each integer is the length of a downloaded website.</span></span> <span data-ttu-id="7aa1e-150">Aşağıdaki kodu ekleyin `SumPageSizesAsync`, yalnızca önceki adımda eklediğiniz koddan sonra.</span><span class="sxs-lookup"><span data-stu-id="7aa1e-150">Add the following code to `SumPageSizesAsync`, just after the code that you added in the previous step.</span></span>  
  
    ```csharp  
    // Await the completion of all the running tasks.  
    int[] lengths = await Task.WhenAll(downloadTasks);  
  
    //// The previous line is equivalent to the following two statements.  
    //Task<int[]> whenAllTask = Task.WhenAll(downloadTasks);  
    //int[] lengths = await whenAllTask;  
    ```  
  
5.  <span data-ttu-id="7aa1e-151">Son olarak, <xref:System.Linq.Enumerable.Sum%2A> tüm Web siteleri uzunlukları toplamını almak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="7aa1e-151">Finally, use the <xref:System.Linq.Enumerable.Sum%2A> method to get the sum of the lengths of all the websites.</span></span> <span data-ttu-id="7aa1e-152">Aşağıdaki satırı ekleyin `SumPageSizesAsync`.</span><span class="sxs-lookup"><span data-stu-id="7aa1e-152">Add the following line to `SumPageSizesAsync`.</span></span>  
  
    ```csharp  
    int total = lengths.Sum();
    ```  
  
### <a name="to-test-the-taskwhenall-solutions"></a><span data-ttu-id="7aa1e-153">Task.WhenAll çözümleri test etmek için</span><span class="sxs-lookup"><span data-stu-id="7aa1e-153">To test the Task.WhenAll solutions</span></span>  
  
-   <span data-ttu-id="7aa1e-154">Programı çalıştırmak için F5 tuşuna ya da çözüm için seçin ve ardından **Başlat** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="7aa1e-154">For either solution, choose the F5 key to run the program, and then choose the **Start** button.</span></span> <span data-ttu-id="7aa1e-155">Çıkış zaman uyumsuz çözümlerinde çıktısını benzemelidir [izlenecek yol: async kullanarak Web'e erişme ve await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="7aa1e-155">The output should resemble the output from the async solutions in [Walkthrough: Accessing the Web by Using async and await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span> <span data-ttu-id="7aa1e-156">Ancak, Web sitelerinin her zaman farklı bir sırada görüntülendiğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="7aa1e-156">However, notice that the websites appear in a different order each time.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7aa1e-157">Örnek</span><span class="sxs-lookup"><span data-stu-id="7aa1e-157">Example</span></span>  
 <span data-ttu-id="7aa1e-158">Aşağıdaki kod kullanan projeye uzantıları gösterir `GetURLContentsAsync` web sunucusundan içerik indirmek için yöntem.</span><span class="sxs-lookup"><span data-stu-id="7aa1e-158">The following code shows the extensions to the project that uses the `GetURLContentsAsync` method to download content from the web.</span></span>  
  
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
                string.Format("\r\n\r\nTotal bytes returned:  {0}\r\n", total);  
        }  
  
        private List<string> SetUpURLList()  
        {  
            List<string> urls = new List<string>   
            {   
                "http://msdn.microsoft.com",  
                "http://msdn.microsoft.com/library/windows/apps/br211380.aspx",  
                "http://msdn.microsoft.com/library/hh290136.aspx",  
                "http://msdn.microsoft.com/library/ee256749.aspx",  
                "http://msdn.microsoft.com/library/hh290138.aspx",  
                "http://msdn.microsoft.com/library/hh290140.aspx",  
                "http://msdn.microsoft.com/library/dd470362.aspx",  
                "http://msdn.microsoft.com/library/aa578028.aspx",  
                "http://msdn.microsoft.com/library/ms404677.aspx",  
                "http://msdn.microsoft.com/library/ff730837.aspx"  
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
            // Strip off the "http://".  
            var displayURL = url.Replace("http://", "");  
            resultsTextBox.Text += string.Format("\n{0,-58} {1,8}", displayURL, bytes);  
  
        }  
    }  
}  
```  
  
## <a name="example"></a><span data-ttu-id="7aa1e-159">Örnek</span><span class="sxs-lookup"><span data-stu-id="7aa1e-159">Example</span></span>  
 <span data-ttu-id="7aa1e-160">Aşağıdaki kod bir yöntem projesine uzantıları gösterir `HttpClient.GetByteArrayAsync` web sunucusundan içerik indirmek için.</span><span class="sxs-lookup"><span data-stu-id="7aa1e-160">The following code shows the extensions to the project that uses method `HttpClient.GetByteArrayAsync` to download content from the web.</span></span>  
  
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
                from url in urlList select ProcessURL(url, client);  
  
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
                string.Format("\r\n\r\nTotal bytes returned:  {0}\r\n", total);  
        }  
  
        private List<string> SetUpURLList()  
        {  
            List<string> urls = new List<string>   
            {   
                "http://msdn.microsoft.com",  
                "http://msdn.microsoft.com/library/hh290136.aspx",  
                "http://msdn.microsoft.com/library/ee256749.aspx",  
                "http://msdn.microsoft.com/library/hh290138.aspx",  
                "http://msdn.microsoft.com/library/hh290140.aspx",  
                "http://msdn.microsoft.com/library/dd470362.aspx",  
                "http://msdn.microsoft.com/library/aa578028.aspx",  
                "http://msdn.microsoft.com/library/ms404677.aspx",  
                "http://msdn.microsoft.com/library/ff730837.aspx"  
            };  
            return urls;  
        }  
  
        // The actions from the foreach loop are moved to this async method.  
        async Task<int> ProcessURL(string url, HttpClient client)  
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
            // Strip off the "http://".  
            var displayURL = url.Replace("http://", "");  
            resultsTextBox.Text += string.Format("\n{0,-58} {1,8}", displayURL, bytes);  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="7aa1e-161">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7aa1e-161">See Also</span></span>  
 <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="7aa1e-162">İzlenecek yol: async kullanarak Web'e erişme ve await (C#)</span><span class="sxs-lookup"><span data-stu-id="7aa1e-162">Walkthrough: Accessing the Web by Using async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
