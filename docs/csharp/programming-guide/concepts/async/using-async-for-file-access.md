---
title: Dosya erişimi için Async Kullanma (C#)
ms.date: 07/20/2015
ms.assetid: bb018fea-5313-4c80-ab3f-7c24b2145bd9
ms.openlocfilehash: 8e0a62c2263ed3fd11eb4accb54978ef439ac010
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396956"
---
# <a name="using-async-for-file-access-c"></a><span data-ttu-id="7c010-102">Dosya erişimi için Async Kullanma (C#)</span><span class="sxs-lookup"><span data-stu-id="7c010-102">Using Async for File Access (C#)</span></span>
<span data-ttu-id="7c010-103">Dosyalara erişmek için zaman uyumsuz özelliği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7c010-103">You can use the async feature to access files.</span></span> <span data-ttu-id="7c010-104">Async özelliğini kullanarak, geri çağırmaları kullanmadan veya kodunuzu birden çok yöntemde veya Lambda ifadelerinde bölmeden zaman uyumsuz yöntemlere çağrı yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7c010-104">By using the async feature, you can call into asynchronous methods without using callbacks or splitting your code across multiple methods or lambda expressions.</span></span> <span data-ttu-id="7c010-105">Zaman uyumlu kodu zaman uyumsuz yapmak için, zaman uyumlu bir yöntem yerine zaman uyumsuz bir yöntem çağırır ve koda birkaç anahtar sözcük eklemeniz yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="7c010-105">To make synchronous code asynchronous, you just call an asynchronous method instead of a synchronous method and add a few keywords to the code.</span></span>  
  
 <span data-ttu-id="7c010-106">Dosya erişim çağrılarına zaman uyumsuzluğu eklemek için aşağıdaki nedenleri göz önünde bulundurmanız gerekebilir:</span><span class="sxs-lookup"><span data-stu-id="7c010-106">You might consider the following reasons for adding asynchrony to file access calls:</span></span>  
  
- <span data-ttu-id="7c010-107">İşlemi başlatan kullanıcı arabirimi iş parçacığı başka bir iş gerçekleştirebildiğinden, asynchrony UI uygulamalarını daha hızlı hale getirir.</span><span class="sxs-lookup"><span data-stu-id="7c010-107">Asynchrony makes UI applications more responsive because the UI thread that launches the operation can perform other work.</span></span> <span data-ttu-id="7c010-108">UI iş parçacığının uzun zaman alan kodu yürütmesi gerekiyorsa (örneğin, 50 milisaniyeden fazla), g/ç tamamlanana kadar UI dondurabilir ve Kullanıcı arabirimi iş parçacığı klavye ve fare girişini ve diğer olayları yeniden işleyebilir.</span><span class="sxs-lookup"><span data-stu-id="7c010-108">If the UI thread must execute code that takes a long time (for example, more than 50 milliseconds), the UI may freeze until the I/O is complete and the UI thread can again process keyboard and mouse input and other events.</span></span>  
  
- <span data-ttu-id="7c010-109">Asynchrony, iş parçacıkları gereksinimini azaltarak ASP.NET ve diğer sunucu tabanlı uygulamaların ölçeklenebilirliğini geliştirir.</span><span class="sxs-lookup"><span data-stu-id="7c010-109">Asynchrony improves the scalability of ASP.NET and other server-based applications by reducing the need for threads.</span></span> <span data-ttu-id="7c010-110">Uygulama yanıt başına adanmış bir iş parçacığı kullanıyorsa ve bin istek aynı anda işleneiyorsa, bin iş parçacığı gerekir.</span><span class="sxs-lookup"><span data-stu-id="7c010-110">If the application uses a dedicated thread per response and a thousand requests are being handled simultaneously, a thousand threads are needed.</span></span> <span data-ttu-id="7c010-111">Zaman uyumsuz işlemlerin genellikle bekleme sırasında bir iş parçacığı kullanması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="7c010-111">Asynchronous operations often don’t need to use a thread during the wait.</span></span> <span data-ttu-id="7c010-112">Mevcut g/ç Tamamlama iş parçacığını kısa bir süre içinde kullanırlar.</span><span class="sxs-lookup"><span data-stu-id="7c010-112">They use the existing I/O completion thread briefly at the end.</span></span>  
  
- <span data-ttu-id="7c010-113">Bir dosya erişim işleminin gecikmesi geçerli koşullar altında çok düşük olabilir, ancak gecikme gelecekte büyük ölçüde artabilir.</span><span class="sxs-lookup"><span data-stu-id="7c010-113">The latency of a file access operation might be very low under current conditions, but the latency may greatly increase in the future.</span></span> <span data-ttu-id="7c010-114">Örneğin, bir dosya dünya genelinde bir sunucuya taşınabilir.</span><span class="sxs-lookup"><span data-stu-id="7c010-114">For example, a file may be moved to a server that's across the world.</span></span>  
  
- <span data-ttu-id="7c010-115">Zaman uyumsuz özelliği kullanmanın ek yükü küçüktür.</span><span class="sxs-lookup"><span data-stu-id="7c010-115">The added overhead of using the Async feature is small.</span></span>  
  
- <span data-ttu-id="7c010-116">Zaman uyumsuz görevler, paralel olarak kolayca çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="7c010-116">Asynchronous tasks can easily be run in parallel.</span></span>  
  
## <a name="running-the-examples"></a><span data-ttu-id="7c010-117">Örnekleri çalıştırma</span><span class="sxs-lookup"><span data-stu-id="7c010-117">Running the Examples</span></span>  
 <span data-ttu-id="7c010-118">Bu konudaki örnekleri çalıştırmak için bir **WPF uygulaması** veya **Windows Forms uygulaması** oluşturabilir ve sonra bir **düğme**ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7c010-118">To run the examples in this topic, you can create a **WPF Application** or a **Windows Forms Application** and then add a **Button**.</span></span> <span data-ttu-id="7c010-119">Düğmenin `Click` olayında, her örnekteki ilk yönteme bir çağrı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="7c010-119">In the button's `Click` event, add a call to the first method in each example.</span></span>  
  
 <span data-ttu-id="7c010-120">Aşağıdaki örneklerde aşağıdaki `using` yönergeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="7c010-120">In the following examples, include the following `using` directives.</span></span>  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Diagnostics;  
using System.IO;  
using System.Text;  
using System.Threading.Tasks;  
```  
  
## <a name="use-of-the-filestream-class"></a><span data-ttu-id="7c010-121">FILESTREAM sınıfının kullanımı</span><span class="sxs-lookup"><span data-stu-id="7c010-121">Use of the FileStream Class</span></span>  
 <span data-ttu-id="7c010-122">Bu konudaki örneklerde, <xref:System.IO.FileStream> zaman uyumsuz g/ç 'nin işletim sistemi düzeyinde oluşmasına neden olan bir seçeneğe sahip olan sınıfını kullanın.</span><span class="sxs-lookup"><span data-stu-id="7c010-122">The examples in this topic use the <xref:System.IO.FileStream> class, which has an option that causes asynchronous I/O to occur at the operating system level.</span></span> <span data-ttu-id="7c010-123">Bu seçeneği kullanarak, birçok durumda bir ThreadPool iş parçacığını engellemeyi önleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7c010-123">By using this option, you can avoid blocking a ThreadPool thread in many cases.</span></span> <span data-ttu-id="7c010-124">Bu seçeneği etkinleştirmek için, `useAsync=true` `options=FileOptions.Asynchronous` Oluşturucu çağrısında veya bağımsız değişkenini belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7c010-124">To enable this option, you specify the `useAsync=true` or `options=FileOptions.Asynchronous` argument in the constructor call.</span></span>  
  
 <span data-ttu-id="7c010-125">Bu seçeneği, <xref:System.IO.StreamReader> ve <xref:System.IO.StreamWriter> doğrudan bir dosya yolu belirterek açarsanız kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7c010-125">You can’t use this option with <xref:System.IO.StreamReader> and <xref:System.IO.StreamWriter> if you open them directly by specifying a file path.</span></span> <span data-ttu-id="7c010-126">Ancak, bu seçeneği, <xref:System.IO.Stream> sınıfının açık olduğunu bir şekilde sağlarsanız kullanabilirsiniz <xref:System.IO.FileStream> .</span><span class="sxs-lookup"><span data-stu-id="7c010-126">However, you can use this option if you provide them a <xref:System.IO.Stream> that the <xref:System.IO.FileStream> class opened.</span></span> <span data-ttu-id="7c010-127">Bekleme sırasında UI iş parçacığı engellenmediğinden, zaman uyumsuz çağrıların Kullanıcı arabirimi uygulamalarında daha hızlı olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="7c010-127">Note that asynchronous calls are faster in UI apps even if a ThreadPool thread is blocked, because the UI thread isn’t blocked during the wait.</span></span>  
  
## <a name="writing-text"></a><span data-ttu-id="7c010-128">Metin yazma</span><span class="sxs-lookup"><span data-stu-id="7c010-128">Writing Text</span></span>  
 <span data-ttu-id="7c010-129">Aşağıdaki örnek bir dosyaya metin yazar.</span><span class="sxs-lookup"><span data-stu-id="7c010-129">The following example writes text to a file.</span></span> <span data-ttu-id="7c010-130">Her await ifadesinde, yöntemi hemen çıkar.</span><span class="sxs-lookup"><span data-stu-id="7c010-130">At each await statement, the method immediately exits.</span></span> <span data-ttu-id="7c010-131">G/ç dosyası tamamlandığında, yöntemi await ifadesini izleyen deyimde devam eder.</span><span class="sxs-lookup"><span data-stu-id="7c010-131">When the file I/O is complete, the method resumes at the statement that follows the await statement.</span></span> <span data-ttu-id="7c010-132">Zaman uyumsuz değiştiricinin await ifadesini kullanan yöntemlerin tanımında olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="7c010-132">Note that the async modifier is in the definition of methods that use the await statement.</span></span>  
  
```csharp  
public async Task ProcessWriteAsync()  
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
  
 <span data-ttu-id="7c010-133">Özgün örnek, `await sourceStream.WriteAsync(encodedText, 0, encodedText.Length);` aşağıdaki iki deyimin bir örneği olan ifadesine sahiptir:</span><span class="sxs-lookup"><span data-stu-id="7c010-133">The original example has the statement `await sourceStream.WriteAsync(encodedText, 0, encodedText.Length);`, which is a contraction of the following two statements:</span></span>  
  
```csharp  
Task theTask = sourceStream.WriteAsync(encodedText, 0, encodedText.Length);  
await theTask;  
```  
  
 <span data-ttu-id="7c010-134">İlk ifade bir görev döndürür ve dosya işlemenin başlatılmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="7c010-134">The first statement returns a task and causes file processing to start.</span></span> <span data-ttu-id="7c010-135">Await ile ikinci ifade, yönteminin hemen çıkmasına ve farklı bir görev döndürmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="7c010-135">The second statement with the await causes the method to immediately exit and return a different task.</span></span> <span data-ttu-id="7c010-136">Dosya işleme daha sonra tamamlandığında, yürütme, await ' ı izleyen ifadeye geri döner.</span><span class="sxs-lookup"><span data-stu-id="7c010-136">When the file processing later completes, execution returns to the statement that follows the await.</span></span> <span data-ttu-id="7c010-137">Daha fazla bilgi için bkz. [zaman uyumsuz programlarda denetim akışı (C#)](./control-flow-in-async-programs.md).</span><span class="sxs-lookup"><span data-stu-id="7c010-137">For more information, see  [Control Flow in Async Programs (C#)](./control-flow-in-async-programs.md).</span></span>  
  
## <a name="reading-text"></a><span data-ttu-id="7c010-138">Metin okuma</span><span class="sxs-lookup"><span data-stu-id="7c010-138">Reading Text</span></span>  
 <span data-ttu-id="7c010-139">Aşağıdaki örnek bir dosyadaki metni okur.</span><span class="sxs-lookup"><span data-stu-id="7c010-139">The following example reads text from a file.</span></span> <span data-ttu-id="7c010-140">Metin, arabelleğe alınmış ve bu durumda bir öğesine yerleştirildi <xref:System.Text.StringBuilder> .</span><span class="sxs-lookup"><span data-stu-id="7c010-140">The text is buffered and, in this case, placed into a <xref:System.Text.StringBuilder>.</span></span> <span data-ttu-id="7c010-141">Önceki örnekte aksine, await 'ın değerlendirmesi bir değer oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7c010-141">Unlike in the previous example, the evaluation of the await produces a value.</span></span> <span data-ttu-id="7c010-142"><xref:System.IO.Stream.ReadAsync%2A>Yöntemi bir> döndürür <xref:System.Threading.Tasks.Task> \< <xref:System.Int32> , bu nedenle await 'ın değerlendirmesi `Int32` işlem tamamlandıktan sonra bir değer ( `numRead` ) oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7c010-142">The <xref:System.IO.Stream.ReadAsync%2A> method returns a <xref:System.Threading.Tasks.Task>\<<xref:System.Int32>>, so the evaluation of the await produces an `Int32` value (`numRead`) after the operation completes.</span></span> <span data-ttu-id="7c010-143">Daha fazla bilgi için bkz. [Async Return Types (C#)](./async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="7c010-143">For more information, see [Async Return Types (C#)](./async-return-types.md).</span></span>  
  
```csharp  
public async Task ProcessReadAsync()  
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
  
## <a name="parallel-asynchronous-io"></a><span data-ttu-id="7c010-144">Paralel zaman uyumsuz g/ç</span><span class="sxs-lookup"><span data-stu-id="7c010-144">Parallel Asynchronous I/O</span></span>  
 <span data-ttu-id="7c010-145">Aşağıdaki örnek, 10 metin dosyası yazarak paralel işlemeyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="7c010-145">The following example demonstrates parallel processing by writing 10 text files.</span></span> <span data-ttu-id="7c010-146">Her dosya için, <xref:System.IO.Stream.WriteAsync%2A> yöntemi bir görev listesine eklenen bir görevi döndürür.</span><span class="sxs-lookup"><span data-stu-id="7c010-146">For each file, the <xref:System.IO.Stream.WriteAsync%2A> method returns a task that is then added to a list of tasks.</span></span> <span data-ttu-id="7c010-147">`await Task.WhenAll(tasks);`Deyimden çıkılıyor ve tüm görevler için dosya işleme tamamlandığında yöntemi içinde devam eder.</span><span class="sxs-lookup"><span data-stu-id="7c010-147">The `await Task.WhenAll(tasks);` statement exits the method and resumes within the method when file processing is complete for all of the tasks.</span></span>  
  
 <span data-ttu-id="7c010-148">Örnek, <xref:System.IO.FileStream> `finally` görevler tamamlandıktan sonra bir bloktaki tüm örnekleri kapatır.</span><span class="sxs-lookup"><span data-stu-id="7c010-148">The example closes all <xref:System.IO.FileStream> instances in a `finally` block after the tasks are complete.</span></span> <span data-ttu-id="7c010-149">Her biri `FileStream` bir bildiriminde oluşturulduysa, `using` görev tamamlanmadan önce ' `FileStream` nin atımı bırakılmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="7c010-149">If each `FileStream` was instead created in a `using` statement, the `FileStream` might be disposed of before the task was complete.</span></span>  
  
 <span data-ttu-id="7c010-150">Herhangi bir performans artışının, zaman uyumsuz işlemden değil, paralel işlemden neredeyse tamamen olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="7c010-150">Note that any performance boost is almost entirely from the parallel processing and not the asynchronous processing.</span></span> <span data-ttu-id="7c010-151">Zaman uyumsuzluğu 'nin avantajları birden çok iş parçacığını bağlamaktır ve Kullanıcı arabirimi iş parçacığını bağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="7c010-151">The advantages of asynchrony are that it doesn’t tie up multiple threads, and that it doesn’t tie up the user interface thread.</span></span>  
  
```csharp  
public async Task ProcessWriteMultAsync()  
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
  
 <span data-ttu-id="7c010-152"><xref:System.IO.Stream.WriteAsync%2A>Ve yöntemlerini kullanırken, <xref:System.IO.Stream.ReadAsync%2A> <xref:System.Threading.CancellationToken> işlem orta-akış işlemini iptal etmek için kullanabileceğiniz bir belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7c010-152">When using the <xref:System.IO.Stream.WriteAsync%2A> and <xref:System.IO.Stream.ReadAsync%2A> methods, you can specify a <xref:System.Threading.CancellationToken>, which you can use to cancel the operation mid-stream.</span></span> <span data-ttu-id="7c010-153">Daha fazla bilgi için bkz. [yönetilen Iş parçacıklarında](../../../../standard/threading/cancellation-in-managed-threads.md) [zaman uyumsuz uygulamanızın (C#) ve Iptalinin ince ayar yapma](./fine-tuning-your-async-application.md) .</span><span class="sxs-lookup"><span data-stu-id="7c010-153">For more information, see [Fine-Tuning Your Async Application (C#)](./fine-tuning-your-async-application.md) and [Cancellation in Managed Threads](../../../../standard/threading/cancellation-in-managed-threads.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c010-154">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7c010-154">See also</span></span>

- [<span data-ttu-id="7c010-155">Async ve await ile zaman uyumsuz programlama (C#)</span><span class="sxs-lookup"><span data-stu-id="7c010-155">Asynchronous Programming with async and await (C#)</span></span>](./index.md)
- [<span data-ttu-id="7c010-156">Zaman uyumsuz dönüş türleri (C#)</span><span class="sxs-lookup"><span data-stu-id="7c010-156">Async Return Types (C#)</span></span>](./async-return-types.md)
- [<span data-ttu-id="7c010-157">Zaman uyumsuz programlarda denetim akışı (C#)</span><span class="sxs-lookup"><span data-stu-id="7c010-157">Control Flow in Async Programs (C#)</span></span>](./control-flow-in-async-programs.md)
