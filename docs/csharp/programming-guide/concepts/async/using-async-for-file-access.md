---
title: "Dosya erişimi için (C#) Async kullanma"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: bb018fea-5313-4c80-ab3f-7c24b2145bd9
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 7d6272baa9beae405148185abfebde84ca0cb7d5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="using-async-for-file-access-c"></a><span data-ttu-id="8d846-102">Dosya erişimi için (C#) Async kullanma</span><span class="sxs-lookup"><span data-stu-id="8d846-102">Using Async for File Access (C#)</span></span>
<span data-ttu-id="8d846-103">Async özelliği dosyalara erişmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8d846-103">You can use the async feature to access files.</span></span> <span data-ttu-id="8d846-104">Async özelliği kullanarak, geri çağrılar kullanarak veya birden çok yöntem veya lambda ifadeleri kodunuzu bölme olmadan zaman uyumsuz yöntemleri çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8d846-104">By using the async feature, you can call into asynchronous methods without using callbacks or splitting your code across multiple methods or lambda expressions.</span></span> <span data-ttu-id="8d846-105">Zaman uyumlu bir kod zaman uyumsuz hale getirmek için yalnızca zaman uyumlu yöntemi yerine zaman uyumsuz bir yöntem çağrısı ve birkaç anahtar sözcükleri kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="8d846-105">To make synchronous code asynchronous, you just call an asynchronous method instead of a synchronous method and add a few keywords to the code.</span></span>  
  
 <span data-ttu-id="8d846-106">Dosya erişim çağrıları asynchrony eklemek için aşağıdaki nedenlerden düşünebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="8d846-106">You might consider the following reasons for adding asynchrony to file access calls:</span></span>  
  
-   <span data-ttu-id="8d846-107">İşlemi başlatan kullanıcı Arabirimi iş parçacığı diğer işlemleri gerçekleştirmesi çünkü asynchrony UI uygulamaları daha esnek hale getirir.</span><span class="sxs-lookup"><span data-stu-id="8d846-107">Asynchrony makes UI applications more responsive because the UI thread that launches the operation can perform other work.</span></span> <span data-ttu-id="8d846-108">Kullanıcı Arabirimi iş parçacığı kod yürütülmelidir, (örneğin, 50'den fazla milisaniye) daha uzun bir zaman alır, UI g/ç tamamlanana ve kullanıcı Arabirimi iş parçacığı, yeniden klavye işlemek ve giriş ve diğer olayları fare kadar donabilir.</span><span class="sxs-lookup"><span data-stu-id="8d846-108">If the UI thread must execute code that takes a long time (for example, more than 50 milliseconds), the UI may freeze until the I/O is complete and the UI thread can again process keyboard and mouse input and other events.</span></span>  
  
-   <span data-ttu-id="8d846-109">İş parçacığı gereksinimini azaltarak ASP.NET ölçeklenebilirliğini ve diğer sunucu tabanlı uygulamalar asynchrony artırır.</span><span class="sxs-lookup"><span data-stu-id="8d846-109">Asynchrony improves the scalability of ASP.NET and other server-based applications by reducing the need for threads.</span></span> <span data-ttu-id="8d846-110">Uygulama yanıt başına adanmış bir iş parçacığı kullanır ve bir bin istekleri aynı anda işlenmekte, binlerce iş parçacığı gereklidir.</span><span class="sxs-lookup"><span data-stu-id="8d846-110">If the application uses a dedicated thread per response and a thousand requests are being handled simultaneously, a thousand threads are needed.</span></span> <span data-ttu-id="8d846-111">Zaman uyumsuz işlemleri genellikle bir iş parçacığı bekleme sırasında kullanmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="8d846-111">Asynchronous operations often don’t need to use a thread during the wait.</span></span> <span data-ttu-id="8d846-112">Varolan g/ç Tamamlama iş parçacığı kısa bir süre sonunda kullanırlar.</span><span class="sxs-lookup"><span data-stu-id="8d846-112">They use the existing I/O completion thread briefly at the end.</span></span>  
  
-   <span data-ttu-id="8d846-113">Dosya erişim işlemi gecikme geçerli koşullar altında çok düşük olabilir, ancak gecikme gelecekte önemli ölçüde artırabilir.</span><span class="sxs-lookup"><span data-stu-id="8d846-113">The latency of a file access operation might be very low under current conditions, but the latency may greatly increase in the future.</span></span> <span data-ttu-id="8d846-114">Örneğin, bir dosya dünya genelindeki bir sunucuya taşınması.</span><span class="sxs-lookup"><span data-stu-id="8d846-114">For example, a file may be moved to a server that's across the world.</span></span>  
  
-   <span data-ttu-id="8d846-115">Eklenen Async özelliği kullanılarak yükünü küçük.</span><span class="sxs-lookup"><span data-stu-id="8d846-115">The added overhead of using the Async feature is small.</span></span>  
  
-   <span data-ttu-id="8d846-116">Zaman uyumsuz görevleri kolayca paralel olarak çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="8d846-116">Asynchronous tasks can easily be run in parallel.</span></span>  
  
## <a name="running-the-examples"></a><span data-ttu-id="8d846-117">Örnekleri çalıştırma</span><span class="sxs-lookup"><span data-stu-id="8d846-117">Running the Examples</span></span>  
 <span data-ttu-id="8d846-118">Bu konudaki örnekler çalıştırmak için oluşturabileceğiniz bir **WPF uygulaması** veya **Windows Forms uygulaması** ve ardından ekleyin bir **düğmesini**.</span><span class="sxs-lookup"><span data-stu-id="8d846-118">To run the examples in this topic, you can create a **WPF Application** or a **Windows Forms Application** and then add a **Button**.</span></span> <span data-ttu-id="8d846-119">Düğmenin içinde `Click` olay, her örnekte ilk yöntemine bir çağrı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="8d846-119">In the button's `Click` event, add a call to the first method in each example.</span></span>  
  
 <span data-ttu-id="8d846-120">Aşağıdaki örneklerde, aşağıdakiler dahil `using` deyimleri.</span><span class="sxs-lookup"><span data-stu-id="8d846-120">In the following examples, include the following `using` statements.</span></span>  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Diagnostics;  
using System.IO;  
using System.Text;  
using System.Threading.Tasks;  
```  
  
## <a name="use-of-the-filestream-class"></a><span data-ttu-id="8d846-121">FILESTREAM sınıfının kullanın</span><span class="sxs-lookup"><span data-stu-id="8d846-121">Use of the FileStream Class</span></span>  
 <span data-ttu-id="8d846-122">Bu konuda kullanım örnekleri <xref:System.IO.FileStream> işletim sistemi düzeyinde gerçekleşmesi zaman uyumsuz g/ç neden olan bir seçenek olan sınıf.</span><span class="sxs-lookup"><span data-stu-id="8d846-122">The examples in this topic use the <xref:System.IO.FileStream> class, which has an option that causes asynchronous I/O to occur at the operating system level.</span></span> <span data-ttu-id="8d846-123">Bu seçeneği kullanarak, bir iş parçacığı havuzu iş parçacığı birçok durumda engelleme önleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8d846-123">By using this option, you can avoid blocking a ThreadPool thread in many cases.</span></span> <span data-ttu-id="8d846-124">Bu seçeneği etkinleştirmek için belirttiğiniz `useAsync=true` veya `options=FileOptions.Asynchronous` oluşturucu çağrısı bağımsız değişkeni.</span><span class="sxs-lookup"><span data-stu-id="8d846-124">To enable this option, you specify the `useAsync=true` or `options=FileOptions.Asynchronous` argument in the constructor call.</span></span>  
  
 <span data-ttu-id="8d846-125">Bu seçenek ile kullanamazsınız <xref:System.IO.StreamReader> ve <xref:System.IO.StreamWriter> doğrudan bir dosya yolu belirterek açarsanız.</span><span class="sxs-lookup"><span data-stu-id="8d846-125">You can’t use this option with <xref:System.IO.StreamReader> and <xref:System.IO.StreamWriter> if you open them directly by specifying a file path.</span></span> <span data-ttu-id="8d846-126">Ancak, bunları sağlarsanız, bu seçeneği kullanabilirsiniz bir <xref:System.IO.Stream> , <xref:System.IO.FileStream> açılan sınıfı.</span><span class="sxs-lookup"><span data-stu-id="8d846-126">However, you can use this option if you provide them a <xref:System.IO.Stream> that the <xref:System.IO.FileStream> class opened.</span></span> <span data-ttu-id="8d846-127">İş parçacığı havuzu iş parçacığı engellendi olsa bile, kullanıcı Arabirimi iş parçacığı bekleme sırasında engellenmiş değil çünkü zaman uyumsuz çağrılar UI uygulamalarında daha hızlı olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="8d846-127">Note that asynchronous calls are faster in UI apps even if a ThreadPool thread is blocked, because the UI thread isn’t blocked during the wait.</span></span>  
  
## <a name="writing-text"></a><span data-ttu-id="8d846-128">Metin yazma</span><span class="sxs-lookup"><span data-stu-id="8d846-128">Writing Text</span></span>  
 <span data-ttu-id="8d846-129">Aşağıdaki örnek metin bir dosyaya yazar.</span><span class="sxs-lookup"><span data-stu-id="8d846-129">The following example writes text to a file.</span></span> <span data-ttu-id="8d846-130">Her deyimi await, yöntem hemen çıkar.</span><span class="sxs-lookup"><span data-stu-id="8d846-130">At each await statement, the method immediately exits.</span></span> <span data-ttu-id="8d846-131">Dosya g/ç tamamlandığında yöntemi bekleme deyimi aşağıdaki ifadesine sürdürür.</span><span class="sxs-lookup"><span data-stu-id="8d846-131">When the file I/O is complete, the method resumes at the statement that follows the await statement.</span></span> <span data-ttu-id="8d846-132">Zaman uyumsuz değiştiricisi bekleme deyimini yöntemleri tanımında olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="8d846-132">Note that the async modifier is in the definition of methods that use the await statement.</span></span>  
  
```csharp  
public async void ProcessWrite()  
{  
    string filePath = @"temp2.txt";  
    string text = "Hello World\r\n";  
  
    await WriteTextAsync(filePath, text);  
}  
  
private async Task WriteTextAsync(string filePath, string text)  
{  
    byte[] encodedText = Encoding.Unicode.GetBytes(text);  
  
    using (FileStream sourceStream = new FileStream(filePath,  
        FileMode.Append, FileAccess.Write, FileShare.None,  
        bufferSize: 4096, useAsync: true))  
    {  
        await sourceStream.WriteAsync(encodedText, 0, encodedText.Length);  
    };  
}  
```  
  
 <span data-ttu-id="8d846-133">Deyim özgün örnek sahip `await sourceStream.WriteAsync(encodedText, 0, encodedText.Length);`, aşağıdaki iki deyimlerinin daraltmaya olduğu:</span><span class="sxs-lookup"><span data-stu-id="8d846-133">The original example has the statement `await sourceStream.WriteAsync(encodedText, 0, encodedText.Length);`, which is a contraction of the following two statements:</span></span>  
  
```csharp  
Task theTask = sourceStream.WriteAsync(encodedText, 0, encodedText.Length);  
await theTask;  
```  
  
 <span data-ttu-id="8d846-134">İlk ifade bir görev döndürür ve başlatmak dosya işleme neden olur.</span><span class="sxs-lookup"><span data-stu-id="8d846-134">The first statement returns a task and causes file processing to start.</span></span> <span data-ttu-id="8d846-135">Bekleme ikinci deyimiyle hemen çıkmak ve farklı bir görev dönmek yöntem neden olur.</span><span class="sxs-lookup"><span data-stu-id="8d846-135">The second statement with the await causes the method to immediately exit and return a different task.</span></span> <span data-ttu-id="8d846-136">Dosya daha sonra işleme tamamlandıktan sonra yürütme bekleme aşağıdaki deyim döndürür.</span><span class="sxs-lookup"><span data-stu-id="8d846-136">When the file processing later completes, execution returns to the statement that follows the await.</span></span> <span data-ttu-id="8d846-137">Daha fazla bilgi için bkz: [akış denetimi zaman uyumsuz programlarda (C#)](../../../../csharp/programming-guide/concepts/async/control-flow-in-async-programs.md).</span><span class="sxs-lookup"><span data-stu-id="8d846-137">For more information, see  [Control Flow in Async Programs (C#)](../../../../csharp/programming-guide/concepts/async/control-flow-in-async-programs.md).</span></span>  
  
## <a name="reading-text"></a><span data-ttu-id="8d846-138">Metin okuma</span><span class="sxs-lookup"><span data-stu-id="8d846-138">Reading Text</span></span>  
 <span data-ttu-id="8d846-139">Aşağıdaki örnek, bir dosyadan metin okur.</span><span class="sxs-lookup"><span data-stu-id="8d846-139">The following example reads text from a file.</span></span> <span data-ttu-id="8d846-140">Metin arabelleğe ve, bu durumda, içine yerleştirilen bir <xref:System.Text.StringBuilder>.</span><span class="sxs-lookup"><span data-stu-id="8d846-140">The text is buffered and, in this case, placed into a <xref:System.Text.StringBuilder>.</span></span> <span data-ttu-id="8d846-141">Farklı olarak önceki örnekte bekleme değerlendirmesi bir değer oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8d846-141">Unlike in the previous example, the evaluation of the await produces a value.</span></span> <span data-ttu-id="8d846-142"><xref:System.IO.Stream.ReadAsync%2A> Yöntemi döndürür bir <xref:System.Threading.Tasks.Task> \< <xref:System.Int32>>, bekleme değerlendirmesi üreten bir `Int32` değeri (`numRead`) işlemi tamamlandıktan sonra.</span><span class="sxs-lookup"><span data-stu-id="8d846-142">The <xref:System.IO.Stream.ReadAsync%2A> method returns a <xref:System.Threading.Tasks.Task>\<<xref:System.Int32>>, so the evaluation of the await produces an `Int32` value (`numRead`) after the operation completes.</span></span> <span data-ttu-id="8d846-143">Daha fazla bilgi için bkz: [zaman uyumsuz dönüş türleri (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="8d846-143">For more information, see [Async Return Types (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md).</span></span>  
  
```csharp  
public async void ProcessRead()  
{  
    string filePath = @"temp2.txt";  
  
    if (File.Exists(filePath) == false)  
    {  
        Debug.WriteLine("file not found: " + filePath);  
    }  
    else  
    {  
        try  
        {  
            string text = await ReadTextAsync(filePath);  
            Debug.WriteLine(text);  
        }  
        catch (Exception ex)  
        {  
            Debug.WriteLine(ex.Message);  
        }  
    }  
}  
  
private async Task<string> ReadTextAsync(string filePath)  
{  
    using (FileStream sourceStream = new FileStream(filePath,  
        FileMode.Open, FileAccess.Read, FileShare.Read,  
        bufferSize: 4096, useAsync: true))  
    {  
        StringBuilder sb = new StringBuilder();  
  
        byte[] buffer = new byte[0x1000];  
        int numRead;  
        while ((numRead = await sourceStream.ReadAsync(buffer, 0, buffer.Length)) != 0)  
        {  
            string text = Encoding.Unicode.GetString(buffer, 0, numRead);  
            sb.Append(text);  
        }  
  
        return sb.ToString();  
    }  
}  
```  
  
## <a name="parallel-asynchronous-io"></a><span data-ttu-id="8d846-144">Paralel zaman uyumsuz g/ç</span><span class="sxs-lookup"><span data-stu-id="8d846-144">Parallel Asynchronous I/O</span></span>  
 <span data-ttu-id="8d846-145">Aşağıdaki örnek, 10 metin dosyaları yazarak paralel işleme gösterir.</span><span class="sxs-lookup"><span data-stu-id="8d846-145">The following example demonstrates parallel processing by writing 10 text files.</span></span> <span data-ttu-id="8d846-146">Her bir dosyanın <xref:System.IO.Stream.WriteAsync%2A> yöntemi görevlerin bir listesi için daha sonra eklenen bir görev döndürür.</span><span class="sxs-lookup"><span data-stu-id="8d846-146">For each file, the <xref:System.IO.Stream.WriteAsync%2A> method returns a task that is then added to a list of tasks.</span></span> <span data-ttu-id="8d846-147">`await Task.WhenAll(tasks);` Deyimi yöntemi çıkar ve sürdürür dosyası işleme yöntemi içinde tüm görevleri tamamlayın.</span><span class="sxs-lookup"><span data-stu-id="8d846-147">The `await Task.WhenAll(tasks);` statement exits the method and resumes within the method when file processing is complete for all of the tasks.</span></span>  
  
 <span data-ttu-id="8d846-148">Tüm örnek kapatır <xref:System.IO.FileStream> içinde örnekler bir `finally` görevler tamamlandıktan sonra engelleyin.</span><span class="sxs-lookup"><span data-stu-id="8d846-148">The example closes all <xref:System.IO.FileStream> instances in a `finally` block after the tasks are complete.</span></span> <span data-ttu-id="8d846-149">Her varsa `FileStream` yerine oluşturulan bir `using` deyimi, `FileStream` görev tamamlanmadan önce elden.</span><span class="sxs-lookup"><span data-stu-id="8d846-149">If each `FileStream` was instead created in a `using` statement, the `FileStream` might be disposed of before the task was complete.</span></span>  
  
 <span data-ttu-id="8d846-150">Tüm performans artırma neredeyse tamamen paralel işleme ve zaman uyumsuz işleme olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="8d846-150">Note that any performance boost is almost entirely from the parallel processing and not the asynchronous processing.</span></span> <span data-ttu-id="8d846-151">Asynchrony avantajları şunlardır: birden çok iş parçacıklarını tie değil ve kullanıcı arabirimi iş parçacığını tie değil.</span><span class="sxs-lookup"><span data-stu-id="8d846-151">The advantages of asynchrony are that it doesn’t tie up multiple threads, and that it doesn’t tie up the user interface thread.</span></span>  
  
```csharp  
public async void ProcessWriteMult()  
{  
    string folder = @"tempfolder\";  
    List<Task> tasks = new List<Task>();  
    List<FileStream> sourceStreams = new List<FileStream>();  
  
    try  
    {  
        for (int index = 1; index <= 10; index++)  
        {  
            string text = "In file " + index.ToString() + "\r\n";  
  
            string fileName = "thefile" + index.ToString("00") + ".txt";  
            string filePath = folder + fileName;  
  
            byte[] encodedText = Encoding.Unicode.GetBytes(text);  
  
            FileStream sourceStream = new FileStream(filePath,  
                FileMode.Append, FileAccess.Write, FileShare.None,  
                bufferSize: 4096, useAsync: true);  
  
            Task theTask = sourceStream.WriteAsync(encodedText, 0, encodedText.Length);  
            sourceStreams.Add(sourceStream);  
  
            tasks.Add(theTask);  
        }  
  
        await Task.WhenAll(tasks);  
    }  
  
    finally  
    {  
        foreach (FileStream sourceStream in sourceStreams)  
        {  
            sourceStream.Close();  
        }  
    }  
}  
```  
  
 <span data-ttu-id="8d846-152">Kullanırken <xref:System.IO.Stream.WriteAsync%2A> ve <xref:System.IO.Stream.ReadAsync%2A> yöntemleri belirtebilirsiniz bir <xref:System.Threading.CancellationToken>, hangi işlemi Orta akışı iptal etmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8d846-152">When using the <xref:System.IO.Stream.WriteAsync%2A> and <xref:System.IO.Stream.ReadAsync%2A> methods, you can specify a <xref:System.Threading.CancellationToken>, which you can use to cancel the operation mid-stream.</span></span> <span data-ttu-id="8d846-153">Daha fazla bilgi için bkz: [Fine-Tuning zaman uyumsuz uygulamanız (C#)](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md) ve [yönetilen iş parçacıklarında iptal](../../../../standard/threading/cancellation-in-managed-threads.md).</span><span class="sxs-lookup"><span data-stu-id="8d846-153">For more information, see [Fine-Tuning Your Async Application (C#)](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md) and [Cancellation in Managed Threads](../../../../standard/threading/cancellation-in-managed-threads.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d846-154">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8d846-154">See Also</span></span>  
 [<span data-ttu-id="8d846-155">Zaman uyumsuz programlama ile async ve await (C#)</span><span class="sxs-lookup"><span data-stu-id="8d846-155">Asynchronous Programming with async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/index.md)  
 [<span data-ttu-id="8d846-156">Zaman uyumsuz dönüş türleri (C#)</span><span class="sxs-lookup"><span data-stu-id="8d846-156">Async Return Types (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/async-return-types.md)  
 [<span data-ttu-id="8d846-157">Denetim akışı zaman uyumsuz programlarda (C#)</span><span class="sxs-lookup"><span data-stu-id="8d846-157">Control Flow in Async Programs (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/control-flow-in-async-programs.md)
