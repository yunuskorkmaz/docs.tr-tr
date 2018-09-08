---
title: Zaman uyumsuz dosya erişimi için (C#) kullanma
ms.date: 07/20/2015
ms.assetid: bb018fea-5313-4c80-ab3f-7c24b2145bd9
ms.openlocfilehash: bbaeb14d5c17665308932c26a0630f1e9e5dabdf
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44132551"
---
# <a name="using-async-for-file-access-c"></a><span data-ttu-id="41f0e-102">Zaman uyumsuz dosya erişimi için (C#) kullanma</span><span class="sxs-lookup"><span data-stu-id="41f0e-102">Using Async for File Access (C#)</span></span>
<span data-ttu-id="41f0e-103">Async özelliği dosyalara erişmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="41f0e-103">You can use the async feature to access files.</span></span> <span data-ttu-id="41f0e-104">Async özelliği'ni kullanarak geri çağırmaları kullanarak veya birden çok yöntemlerde veya lambda ifadelerinde kodunuzu bölme olmadan zaman uyumsuz yöntemleri çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="41f0e-104">By using the async feature, you can call into asynchronous methods without using callbacks or splitting your code across multiple methods or lambda expressions.</span></span> <span data-ttu-id="41f0e-105">Eş zamanlı kod zaman uyumsuz hale getirmek için yalnızca zaman uyumlu bir yöntem yerine zaman uyumsuz yöntemini çağırın ve birkaç anahtar sözcükler için kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="41f0e-105">To make synchronous code asynchronous, you just call an asynchronous method instead of a synchronous method and add a few keywords to the code.</span></span>  
  
 <span data-ttu-id="41f0e-106">Dosya erişim çağrıları zaman uyumsuzluğu eklemek için aşağıdaki nedenlerden düşünebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="41f0e-106">You might consider the following reasons for adding asynchrony to file access calls:</span></span>  
  
-   <span data-ttu-id="41f0e-107">İşlemi başlatan kullanıcı Arabirimi iş parçacığı başka işleri gerçekleştirebilirsiniz çünkü faaliyetler UI uygulamaları daha hızlı sağlar.</span><span class="sxs-lookup"><span data-stu-id="41f0e-107">Asynchrony makes UI applications more responsive because the UI thread that launches the operation can perform other work.</span></span> <span data-ttu-id="41f0e-108">UI iş parçacığı kod yürütülmesi gerekiyorsa (örneğin, 50'den fazla milisaniye) uzun zaman alan, UI ve UI iş parçacığı yeniden klavye işleyebilir ve giriş ve diğer olayları fare g/ç işlemi tamamlanana kadar donabilir.</span><span class="sxs-lookup"><span data-stu-id="41f0e-108">If the UI thread must execute code that takes a long time (for example, more than 50 milliseconds), the UI may freeze until the I/O is complete and the UI thread can again process keyboard and mouse input and other events.</span></span>  
  
-   <span data-ttu-id="41f0e-109">İş parçacıkları gereksinimini azaltarak ASP.NET ölçeklenebilirliğini ve diğer sunucu tabanlı uygulamalar faaliyetler artırır.</span><span class="sxs-lookup"><span data-stu-id="41f0e-109">Asynchrony improves the scalability of ASP.NET and other server-based applications by reducing the need for threads.</span></span> <span data-ttu-id="41f0e-110">Binlerce iş parçacıkları, adanmış bir iş parçacığı başına yanıt uygulama kullanıyorsa ve binlerce istekleri aynı anda işlenmekte gereklidir.</span><span class="sxs-lookup"><span data-stu-id="41f0e-110">If the application uses a dedicated thread per response and a thousand requests are being handled simultaneously, a thousand threads are needed.</span></span> <span data-ttu-id="41f0e-111">Zaman uyumsuz işlemler genellikle bir iş parçacığı bekleme sırasında kullanmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="41f0e-111">Asynchronous operations often don’t need to use a thread during the wait.</span></span> <span data-ttu-id="41f0e-112">Mevcut g/ç Tamamlama iş parçacığı kısa bir süre sonunda kullanırlar.</span><span class="sxs-lookup"><span data-stu-id="41f0e-112">They use the existing I/O completion thread briefly at the end.</span></span>  
  
-   <span data-ttu-id="41f0e-113">Bir dosya erişim işlemi gecikme süresini geçerli koşullar altında çok düşük olabilir ancak gecikme süresi gelecekte büyük ölçüde artırabilir.</span><span class="sxs-lookup"><span data-stu-id="41f0e-113">The latency of a file access operation might be very low under current conditions, but the latency may greatly increase in the future.</span></span> <span data-ttu-id="41f0e-114">Örneğin, bir dosya dünya genelindeki bir sunucuya taşınabilir.</span><span class="sxs-lookup"><span data-stu-id="41f0e-114">For example, a file may be moved to a server that's across the world.</span></span>  
  
-   <span data-ttu-id="41f0e-115">Ek yükü zaman uyumsuz özelliğini kullanarak küçük.</span><span class="sxs-lookup"><span data-stu-id="41f0e-115">The added overhead of using the Async feature is small.</span></span>  
  
-   <span data-ttu-id="41f0e-116">Zaman uyumsuz görevleri kolayca paralel olarak çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="41f0e-116">Asynchronous tasks can easily be run in parallel.</span></span>  
  
## <a name="running-the-examples"></a><span data-ttu-id="41f0e-117">Örnekleri çalıştırma</span><span class="sxs-lookup"><span data-stu-id="41f0e-117">Running the Examples</span></span>  
 <span data-ttu-id="41f0e-118">Bu konudaki örnekleri çalıştırmak için oluşturabileceğiniz bir **WPF uygulaması** veya **Windows Forms uygulaması** ve ardından eklemek bir **düğmesi**.</span><span class="sxs-lookup"><span data-stu-id="41f0e-118">To run the examples in this topic, you can create a **WPF Application** or a **Windows Forms Application** and then add a **Button**.</span></span> <span data-ttu-id="41f0e-119">Düğmenin içinde `Click` olay, her örnekte ilk yönteme bir çağrı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="41f0e-119">In the button's `Click` event, add a call to the first method in each example.</span></span>  
  
 <span data-ttu-id="41f0e-120">Aşağıdaki örneklerde, aşağıdakiler dahil `using` deyimleri.</span><span class="sxs-lookup"><span data-stu-id="41f0e-120">In the following examples, include the following `using` statements.</span></span>  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Diagnostics;  
using System.IO;  
using System.Text;  
using System.Threading.Tasks;  
```  
  
## <a name="use-of-the-filestream-class"></a><span data-ttu-id="41f0e-121">FILESTREAM sınıfının kullanımı</span><span class="sxs-lookup"><span data-stu-id="41f0e-121">Use of the FileStream Class</span></span>  
 <span data-ttu-id="41f0e-122">Bu konuda kullanım örnekleri <xref:System.IO.FileStream> işletim sistemi düzeyinde gerçekleşmesi zaman uyumsuz g/ç neden olan bir seçenek olduğu sınıf.</span><span class="sxs-lookup"><span data-stu-id="41f0e-122">The examples in this topic use the <xref:System.IO.FileStream> class, which has an option that causes asynchronous I/O to occur at the operating system level.</span></span> <span data-ttu-id="41f0e-123">Bu seçeneği kullanarak, çoğu durumda bir iş parçacığı havuzu iş parçacığını engelleme önleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="41f0e-123">By using this option, you can avoid blocking a ThreadPool thread in many cases.</span></span> <span data-ttu-id="41f0e-124">Bu seçeneği etkinleştirmek için belirttiğiniz `useAsync=true` veya `options=FileOptions.Asynchronous` Oluşturucusu çağrısında bağımsız değişken.</span><span class="sxs-lookup"><span data-stu-id="41f0e-124">To enable this option, you specify the `useAsync=true` or `options=FileOptions.Asynchronous` argument in the constructor call.</span></span>  
  
 <span data-ttu-id="41f0e-125">Bu seçeneği kullanamazsınız <xref:System.IO.StreamReader> ve <xref:System.IO.StreamWriter> doğrudan bir dosya yolu belirterek açarsanız.</span><span class="sxs-lookup"><span data-stu-id="41f0e-125">You can’t use this option with <xref:System.IO.StreamReader> and <xref:System.IO.StreamWriter> if you open them directly by specifying a file path.</span></span> <span data-ttu-id="41f0e-126">Ancak, bunları sağlarsanız, bu seçeneği kullanabilirsiniz bir <xref:System.IO.Stream> , <xref:System.IO.FileStream> sınıfı açılır.</span><span class="sxs-lookup"><span data-stu-id="41f0e-126">However, you can use this option if you provide them a <xref:System.IO.Stream> that the <xref:System.IO.FileStream> class opened.</span></span> <span data-ttu-id="41f0e-127">Bir iş parçacığı havuzu iş parçacığı engellenir bile, UI iş parçacığı, bekleme sırasında bloke değildir çünkü zaman uyumsuz çağrıları UI uygulamaları daha hızlı olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="41f0e-127">Note that asynchronous calls are faster in UI apps even if a ThreadPool thread is blocked, because the UI thread isn’t blocked during the wait.</span></span>  
  
## <a name="writing-text"></a><span data-ttu-id="41f0e-128">Metin yazma</span><span class="sxs-lookup"><span data-stu-id="41f0e-128">Writing Text</span></span>  
 <span data-ttu-id="41f0e-129">Aşağıdaki örnek, bir dosyaya metin yazar.</span><span class="sxs-lookup"><span data-stu-id="41f0e-129">The following example writes text to a file.</span></span> <span data-ttu-id="41f0e-130">Her deyim await, yöntem hemen çıkar.</span><span class="sxs-lookup"><span data-stu-id="41f0e-130">At each await statement, the method immediately exits.</span></span> <span data-ttu-id="41f0e-131">Dosya g/ç işlemi tamamlandığında, yöntem bekleme ifadesinin izleyen deyime sürdürür.</span><span class="sxs-lookup"><span data-stu-id="41f0e-131">When the file I/O is complete, the method resumes at the statement that follows the await statement.</span></span> <span data-ttu-id="41f0e-132">Zaman uyumsuz değiştirici bekleme ifadesinin yöntem tanımında olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="41f0e-132">Note that the async modifier is in the definition of methods that use the await statement.</span></span>  
  
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
  
 <span data-ttu-id="41f0e-133">Deyimi özgün örneğe sahip `await sourceStream.WriteAsync(encodedText, 0, encodedText.Length);`, aşağıdaki iki deyimi, bir kısaltma olduğundan:</span><span class="sxs-lookup"><span data-stu-id="41f0e-133">The original example has the statement `await sourceStream.WriteAsync(encodedText, 0, encodedText.Length);`, which is a contraction of the following two statements:</span></span>  
  
```csharp  
Task theTask = sourceStream.WriteAsync(encodedText, 0, encodedText.Length);  
await theTask;  
```  
  
 <span data-ttu-id="41f0e-134">İlk deyim, bir görev döndürür ve başlatmak, dosya işleme neden olur.</span><span class="sxs-lookup"><span data-stu-id="41f0e-134">The first statement returns a task and causes file processing to start.</span></span> <span data-ttu-id="41f0e-135">Await ile ikinci deyim, yöntem hemen çıkın ve farklı bir görev döndürür neden olur.</span><span class="sxs-lookup"><span data-stu-id="41f0e-135">The second statement with the await causes the method to immediately exit and return a different task.</span></span> <span data-ttu-id="41f0e-136">Dosya daha sonra işleme tamamlandıktan sonra yürütme bekleme takip eden deyime döndürür.</span><span class="sxs-lookup"><span data-stu-id="41f0e-136">When the file processing later completes, execution returns to the statement that follows the await.</span></span> <span data-ttu-id="41f0e-137">Daha fazla bilgi için [akış denetimi zaman uyumsuz programlarda (C#)](../../../../csharp/programming-guide/concepts/async/control-flow-in-async-programs.md).</span><span class="sxs-lookup"><span data-stu-id="41f0e-137">For more information, see  [Control Flow in Async Programs (C#)](../../../../csharp/programming-guide/concepts/async/control-flow-in-async-programs.md).</span></span>  
  
## <a name="reading-text"></a><span data-ttu-id="41f0e-138">Metin okuma</span><span class="sxs-lookup"><span data-stu-id="41f0e-138">Reading Text</span></span>  
 <span data-ttu-id="41f0e-139">Aşağıdaki örnek, bir dosyadan metin okur.</span><span class="sxs-lookup"><span data-stu-id="41f0e-139">The following example reads text from a file.</span></span> <span data-ttu-id="41f0e-140">Metin arabelleğe alınır ve bu durumda, içine yerleştirilen bir <xref:System.Text.StringBuilder>.</span><span class="sxs-lookup"><span data-stu-id="41f0e-140">The text is buffered and, in this case, placed into a <xref:System.Text.StringBuilder>.</span></span> <span data-ttu-id="41f0e-141">Önceki örnekte, farklı bir değer await değerlendirilmesiyle üretir.</span><span class="sxs-lookup"><span data-stu-id="41f0e-141">Unlike in the previous example, the evaluation of the await produces a value.</span></span> <span data-ttu-id="41f0e-142"><xref:System.IO.Stream.ReadAsync%2A> Yöntemi döndürür bir <xref:System.Threading.Tasks.Task> \< <xref:System.Int32>>, await değerlendirilmesiyle üreten bir `Int32` değeri (`numRead`) işlemi tamamlandıktan sonra.</span><span class="sxs-lookup"><span data-stu-id="41f0e-142">The <xref:System.IO.Stream.ReadAsync%2A> method returns a <xref:System.Threading.Tasks.Task>\<<xref:System.Int32>>, so the evaluation of the await produces an `Int32` value (`numRead`) after the operation completes.</span></span> <span data-ttu-id="41f0e-143">Daha fazla bilgi için [Async Return Types (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="41f0e-143">For more information, see [Async Return Types (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md).</span></span>  
  
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
  
## <a name="parallel-asynchronous-io"></a><span data-ttu-id="41f0e-144">Paralel zaman uyumsuz g/ç</span><span class="sxs-lookup"><span data-stu-id="41f0e-144">Parallel Asynchronous I/O</span></span>  
 <span data-ttu-id="41f0e-145">Aşağıdaki örnek, 10 metin dosyaları yazma tarafından paralel işleme gösterir.</span><span class="sxs-lookup"><span data-stu-id="41f0e-145">The following example demonstrates parallel processing by writing 10 text files.</span></span> <span data-ttu-id="41f0e-146">Her dosya için <xref:System.IO.Stream.WriteAsync%2A> yöntemi görevlerinin listesi için daha sonra eklenen bir görev döndürür.</span><span class="sxs-lookup"><span data-stu-id="41f0e-146">For each file, the <xref:System.IO.Stream.WriteAsync%2A> method returns a task that is then added to a list of tasks.</span></span> <span data-ttu-id="41f0e-147">`await Task.WhenAll(tasks);` Deyimi yöntemin çıkar ve sürdürür dosya işleme olduğunda yöntemi içindeki tüm görevlerin tamamlayın.</span><span class="sxs-lookup"><span data-stu-id="41f0e-147">The `await Task.WhenAll(tasks);` statement exits the method and resumes within the method when file processing is complete for all of the tasks.</span></span>  
  
 <span data-ttu-id="41f0e-148">Tüm örnek kapatır <xref:System.IO.FileStream> içinde örnekler bir `finally` görevler tamamlandıktan sonra engelleyin.</span><span class="sxs-lookup"><span data-stu-id="41f0e-148">The example closes all <xref:System.IO.FileStream> instances in a `finally` block after the tasks are complete.</span></span> <span data-ttu-id="41f0e-149">Her varsa `FileStream` yerine içinde oluşturulmuş bir `using` deyimi `FileStream` görev tamamlanmadan önce elden.</span><span class="sxs-lookup"><span data-stu-id="41f0e-149">If each `FileStream` was instead created in a `using` statement, the `FileStream` might be disposed of before the task was complete.</span></span>  
  
 <span data-ttu-id="41f0e-150">Herhangi bir performans artışının neredeyse tamamen paralel işleme ve olmayan uyumsuz olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="41f0e-150">Note that any performance boost is almost entirely from the parallel processing and not the asynchronous processing.</span></span> <span data-ttu-id="41f0e-151">Faaliyetler avantajları şunlardır: birden çok iş parçacıklarını tie değil ve kullanıcı arabirimi iş parçacığı ' tie değil.</span><span class="sxs-lookup"><span data-stu-id="41f0e-151">The advantages of asynchrony are that it doesn’t tie up multiple threads, and that it doesn’t tie up the user interface thread.</span></span>  
  
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
  
 <span data-ttu-id="41f0e-152">Kullanırken <xref:System.IO.Stream.WriteAsync%2A> ve <xref:System.IO.Stream.ReadAsync%2A> yöntemleri belirtebilirsiniz bir <xref:System.Threading.CancellationToken>, hangi işlemin ortasında akış iptal etmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="41f0e-152">When using the <xref:System.IO.Stream.WriteAsync%2A> and <xref:System.IO.Stream.ReadAsync%2A> methods, you can specify a <xref:System.Threading.CancellationToken>, which you can use to cancel the operation mid-stream.</span></span> <span data-ttu-id="41f0e-153">Daha fazla bilgi için [Fine-Tuning Async uygulamanızda (C#)](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md) ve [yönetilen iş parçacıklarında iptal](../../../../standard/threading/cancellation-in-managed-threads.md).</span><span class="sxs-lookup"><span data-stu-id="41f0e-153">For more information, see [Fine-Tuning Your Async Application (C#)](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md) and [Cancellation in Managed Threads](../../../../standard/threading/cancellation-in-managed-threads.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41f0e-154">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="41f0e-154">See Also</span></span>

- [<span data-ttu-id="41f0e-155">Zaman uyumsuz programlama ile async ve await (C#)</span><span class="sxs-lookup"><span data-stu-id="41f0e-155">Asynchronous Programming with async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/index.md)  
- [<span data-ttu-id="41f0e-156">Zaman uyumsuz dönüş türleri (C#)</span><span class="sxs-lookup"><span data-stu-id="41f0e-156">Async Return Types (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/async-return-types.md)  
- [<span data-ttu-id="41f0e-157">Denetim akışı zaman uyumsuz programlarda (C#)</span><span class="sxs-lookup"><span data-stu-id="41f0e-157">Control Flow in Async Programs (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/control-flow-in-async-programs.md)
