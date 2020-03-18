---
title: Dosya Erişimi için Async kullanma (C#)
ms.date: 07/20/2015
ms.assetid: bb018fea-5313-4c80-ab3f-7c24b2145bd9
ms.openlocfilehash: e6b0370049d9b9315de6a72d0e84c080aac12481
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69595538"
---
# <a name="using-async-for-file-access-c"></a><span data-ttu-id="65bef-102">Dosya Erişimi için Async kullanma (C#)</span><span class="sxs-lookup"><span data-stu-id="65bef-102">Using Async for File Access (C#)</span></span>
<span data-ttu-id="65bef-103">Dosyalara erişmek için async özelliğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="65bef-103">You can use the async feature to access files.</span></span> <span data-ttu-id="65bef-104">Async özelliğini kullanarak, geri arama kullanmadan veya kodunuzu birden çok yöntem veya lambda ifadeleri arasında bölmeden eşzamanlı yöntemlere çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="65bef-104">By using the async feature, you can call into asynchronous methods without using callbacks or splitting your code across multiple methods or lambda expressions.</span></span> <span data-ttu-id="65bef-105">Senkron kodu asynchronous yapmak için, eşzamanlı bir yöntem yerine asynchronous yöntemini aramanız ve koda birkaç anahtar kelime eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="65bef-105">To make synchronous code asynchronous, you just call an asynchronous method instead of a synchronous method and add a few keywords to the code.</span></span>  
  
 <span data-ttu-id="65bef-106">Dosya erişim çağrılarına eşitleme eklemek için aşağıdaki nedenleri düşünebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="65bef-106">You might consider the following reasons for adding asynchrony to file access calls:</span></span>  
  
- <span data-ttu-id="65bef-107">İşleyişi başlatan Kullanıcı Birikintisi iş parçacığı başka işler gerçekleştirebildiği için Kullanıcı Arası Uygulama uygulamalarını daha duyarlı hale getirir.</span><span class="sxs-lookup"><span data-stu-id="65bef-107">Asynchrony makes UI applications more responsive because the UI thread that launches the operation can perform other work.</span></span> <span data-ttu-id="65bef-108">UI iş parçacığıuzun zaman (örneğin, 50 milisaniyeden fazla) gerektiren kodu yürütmek gerekiyorsa, Kullanıcı Arabirimi G/Ç tamamlanana kadar donabilir ve Kullanıcı Arabirimi iş parçacığı klavye ve fare girişini ve diğer olayları yeniden işleyebilir.</span><span class="sxs-lookup"><span data-stu-id="65bef-108">If the UI thread must execute code that takes a long time (for example, more than 50 milliseconds), the UI may freeze until the I/O is complete and the UI thread can again process keyboard and mouse input and other events.</span></span>  
  
- <span data-ttu-id="65bef-109">Asynchrony iş parçacığı ihtiyacını azaltarak ASP.NET ve diğer sunucu tabanlı uygulamaların ölçeklenebilirliğini artırır.</span><span class="sxs-lookup"><span data-stu-id="65bef-109">Asynchrony improves the scalability of ASP.NET and other server-based applications by reducing the need for threads.</span></span> <span data-ttu-id="65bef-110">Uygulama yanıt başına özel bir iş parçacığı kullanıyorsa ve aynı anda binlerce istek işleniyorsa, bin iş parçacığı gerekir.</span><span class="sxs-lookup"><span data-stu-id="65bef-110">If the application uses a dedicated thread per response and a thousand requests are being handled simultaneously, a thousand threads are needed.</span></span> <span data-ttu-id="65bef-111">Eşzamanlı işlemler genellikle bekleme sırasında bir iş parçacığı kullanmak gerekmez.</span><span class="sxs-lookup"><span data-stu-id="65bef-111">Asynchronous operations often don’t need to use a thread during the wait.</span></span> <span data-ttu-id="65bef-112">Sonunda varolan G/Ç tamamlama iş parçacığıkısaca kullanırlar.</span><span class="sxs-lookup"><span data-stu-id="65bef-112">They use the existing I/O completion thread briefly at the end.</span></span>  
  
- <span data-ttu-id="65bef-113">Dosya erişim işleminin gecikmesi geçerli koşullar altında çok düşük olabilir, ancak gecikme si gelecekte büyük ölçüde artabilir.</span><span class="sxs-lookup"><span data-stu-id="65bef-113">The latency of a file access operation might be very low under current conditions, but the latency may greatly increase in the future.</span></span> <span data-ttu-id="65bef-114">Örneğin, bir dosya dünyanın dört bir yanındaki bir sunucuya taşınabilir.</span><span class="sxs-lookup"><span data-stu-id="65bef-114">For example, a file may be moved to a server that's across the world.</span></span>  
  
- <span data-ttu-id="65bef-115">Async özelliğini kullanmanın eklenen ek yükü küçüktür.</span><span class="sxs-lookup"><span data-stu-id="65bef-115">The added overhead of using the Async feature is small.</span></span>  
  
- <span data-ttu-id="65bef-116">Eşkenar tümleme görevleri paralel olarak kolayca çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="65bef-116">Asynchronous tasks can easily be run in parallel.</span></span>  
  
## <a name="running-the-examples"></a><span data-ttu-id="65bef-117">Örnekleri Çalıştırma</span><span class="sxs-lookup"><span data-stu-id="65bef-117">Running the Examples</span></span>  
 <span data-ttu-id="65bef-118">Bu konudaki örnekleri çalıştırmak için bir **WPF Uygulaması** veya **Windows Forms Uygulaması** oluşturabilir ve ardından bir **Düğme**ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="65bef-118">To run the examples in this topic, you can create a **WPF Application** or a **Windows Forms Application** and then add a **Button**.</span></span> <span data-ttu-id="65bef-119">Düğmenin `Click` durumunda, her örnekteki ilk yönteme bir çağrı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="65bef-119">In the button's `Click` event, add a call to the first method in each example.</span></span>  
  
 <span data-ttu-id="65bef-120">Aşağıdaki örneklerde aşağıdaki `using` ifadeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="65bef-120">In the following examples, include the following `using` statements.</span></span>  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Diagnostics;  
using System.IO;  
using System.Text;  
using System.Threading.Tasks;  
```  
  
## <a name="use-of-the-filestream-class"></a><span data-ttu-id="65bef-121">FileStream Sınıfının Kullanımı</span><span class="sxs-lookup"><span data-stu-id="65bef-121">Use of the FileStream Class</span></span>  
 <span data-ttu-id="65bef-122">Bu konudaki örnekler, <xref:System.IO.FileStream> işletim sistemi düzeyinde eşzamanlı G/Ç'nin oluşmasına neden olan bir seçenek olan sınıfı kullanır.</span><span class="sxs-lookup"><span data-stu-id="65bef-122">The examples in this topic use the <xref:System.IO.FileStream> class, which has an option that causes asynchronous I/O to occur at the operating system level.</span></span> <span data-ttu-id="65bef-123">Bu seçeneği kullanarak, birçok durumda bir ThreadPool iş parçacığı engelleme önleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="65bef-123">By using this option, you can avoid blocking a ThreadPool thread in many cases.</span></span> <span data-ttu-id="65bef-124">Bu seçeneği etkinleştirmek için, oluşturucu çağrısındaki `useAsync=true` bağımsız `options=FileOptions.Asynchronous` değişkeni belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="65bef-124">To enable this option, you specify the `useAsync=true` or `options=FileOptions.Asynchronous` argument in the constructor call.</span></span>  
  
 <span data-ttu-id="65bef-125">Bu seçeneği <xref:System.IO.StreamReader> <xref:System.IO.StreamWriter> bir dosya yolu belirterek doğrudan açarsanız kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="65bef-125">You can’t use this option with <xref:System.IO.StreamReader> and <xref:System.IO.StreamWriter> if you open them directly by specifying a file path.</span></span> <span data-ttu-id="65bef-126">Ancak, sınıfın açtığı bir seçeneği <xref:System.IO.Stream> <xref:System.IO.FileStream> sağlarsanız, bu seçeneği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="65bef-126">However, you can use this option if you provide them a <xref:System.IO.Stream> that the <xref:System.IO.FileStream> class opened.</span></span> <span data-ttu-id="65bef-127">Kullanıcı Birleşme işi bekleme sırasında engellenmediği için, Bir ThreadPool işi engellenemişolsa bile UI uygulamalarında asynchronous aramalarının daha hızolduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="65bef-127">Note that asynchronous calls are faster in UI apps even if a ThreadPool thread is blocked, because the UI thread isn’t blocked during the wait.</span></span>  
  
## <a name="writing-text"></a><span data-ttu-id="65bef-128">Metin Yazma</span><span class="sxs-lookup"><span data-stu-id="65bef-128">Writing Text</span></span>  
 <span data-ttu-id="65bef-129">Aşağıdaki örnek, bir dosyaya metin yazar.</span><span class="sxs-lookup"><span data-stu-id="65bef-129">The following example writes text to a file.</span></span> <span data-ttu-id="65bef-130">Her bekleyen deyiminde yöntem hemen çıkar.</span><span class="sxs-lookup"><span data-stu-id="65bef-130">At each await statement, the method immediately exits.</span></span> <span data-ttu-id="65bef-131">Dosya G/Ç tamamlandığında, yöntem bekleme deyimini izleyen deyimde devam eder.</span><span class="sxs-lookup"><span data-stu-id="65bef-131">When the file I/O is complete, the method resumes at the statement that follows the await statement.</span></span> <span data-ttu-id="65bef-132">Async değiştirici bekleme deyimini kullanan yöntemlerin tanımında olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="65bef-132">Note that the async modifier is in the definition of methods that use the await statement.</span></span>  
  
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
  
 <span data-ttu-id="65bef-133">Özgün örnekte, `await sourceStream.WriteAsync(encodedText, 0, encodedText.Length);`aşağıdaki iki ifadenin daralması olan ifade vardır:</span><span class="sxs-lookup"><span data-stu-id="65bef-133">The original example has the statement `await sourceStream.WriteAsync(encodedText, 0, encodedText.Length);`, which is a contraction of the following two statements:</span></span>  
  
```csharp  
Task theTask = sourceStream.WriteAsync(encodedText, 0, encodedText.Length);  
await theTask;  
```  
  
 <span data-ttu-id="65bef-134">İlk deyim bir görevi döndürür ve dosya işlemenin başlatılmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="65bef-134">The first statement returns a task and causes file processing to start.</span></span> <span data-ttu-id="65bef-135">Bekleme ile ikinci ifade yöntemin hemen çıkmak ve farklı bir görev dönmek için neden olur.</span><span class="sxs-lookup"><span data-stu-id="65bef-135">The second statement with the await causes the method to immediately exit and return a different task.</span></span> <span data-ttu-id="65bef-136">Dosya işleme daha sonra tamamlandığında, yürütme bekleme izleyen deyimi döndürür.</span><span class="sxs-lookup"><span data-stu-id="65bef-136">When the file processing later completes, execution returns to the statement that follows the await.</span></span> <span data-ttu-id="65bef-137">Daha fazla bilgi için [Async Programlarında Denetim Akışı (C#) 'ye](./control-flow-in-async-programs.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="65bef-137">For more information, see  [Control Flow in Async Programs (C#)](./control-flow-in-async-programs.md).</span></span>  
  
## <a name="reading-text"></a><span data-ttu-id="65bef-138">Okuma Metni</span><span class="sxs-lookup"><span data-stu-id="65bef-138">Reading Text</span></span>  
 <span data-ttu-id="65bef-139">Aşağıdaki örnekte bir dosyadaki metin okur.</span><span class="sxs-lookup"><span data-stu-id="65bef-139">The following example reads text from a file.</span></span> <span data-ttu-id="65bef-140">Metin arabelleğe alınarak bu durumda bir <xref:System.Text.StringBuilder>.</span><span class="sxs-lookup"><span data-stu-id="65bef-140">The text is buffered and, in this case, placed into a <xref:System.Text.StringBuilder>.</span></span> <span data-ttu-id="65bef-141">Önceki örnekte aksine, bekleme nin değerlendirilmesi bir değer üretir.</span><span class="sxs-lookup"><span data-stu-id="65bef-141">Unlike in the previous example, the evaluation of the await produces a value.</span></span> <span data-ttu-id="65bef-142">Yöntem <xref:System.IO.Stream.ReadAsync%2A> <xref:System.Threading.Tasks.Task> \< <xref:System.Int32> bir> döndürür, bu nedenle `Int32` beklemenin değerlendirilmesi işlem tamamlandıktan sonra bir değer (`numRead`) üretir.</span><span class="sxs-lookup"><span data-stu-id="65bef-142">The <xref:System.IO.Stream.ReadAsync%2A> method returns a <xref:System.Threading.Tasks.Task>\<<xref:System.Int32>>, so the evaluation of the await produces an `Int32` value (`numRead`) after the operation completes.</span></span> <span data-ttu-id="65bef-143">Daha fazla bilgi için [Bkz. Async İade Türleri (C#)](./async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="65bef-143">For more information, see [Async Return Types (C#)](./async-return-types.md).</span></span>  
  
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
  
## <a name="parallel-asynchronous-io"></a><span data-ttu-id="65bef-144">Paralel Asynchronous I/O</span><span class="sxs-lookup"><span data-stu-id="65bef-144">Parallel Asynchronous I/O</span></span>  
 <span data-ttu-id="65bef-145">Aşağıdaki örnek, 10 metin dosyası yazarak paralel işleme gösterir.</span><span class="sxs-lookup"><span data-stu-id="65bef-145">The following example demonstrates parallel processing by writing 10 text files.</span></span> <span data-ttu-id="65bef-146">Her dosya için <xref:System.IO.Stream.WriteAsync%2A> yöntem, görev listesine eklenen bir görevi döndürür.</span><span class="sxs-lookup"><span data-stu-id="65bef-146">For each file, the <xref:System.IO.Stream.WriteAsync%2A> method returns a task that is then added to a list of tasks.</span></span> <span data-ttu-id="65bef-147">İfade `await Task.WhenAll(tasks);` yöntemden çıkar ve tüm görevler için dosya işleme tamamlandığında yöntem içinde devam eder.</span><span class="sxs-lookup"><span data-stu-id="65bef-147">The `await Task.WhenAll(tasks);` statement exits the method and resumes within the method when file processing is complete for all of the tasks.</span></span>  
  
 <span data-ttu-id="65bef-148">Örnek, görevler <xref:System.IO.FileStream> tamamlandıktan sonra `finally` bloktaki tüm örnekleri kapatır.</span><span class="sxs-lookup"><span data-stu-id="65bef-148">The example closes all <xref:System.IO.FileStream> instances in a `finally` block after the tasks are complete.</span></span> <span data-ttu-id="65bef-149">Her `FileStream` biri bir `using` deyimde oluşturulduysa, `FileStream` görev tamamlanmadan önce atılabilir.</span><span class="sxs-lookup"><span data-stu-id="65bef-149">If each `FileStream` was instead created in a `using` statement, the `FileStream` might be disposed of before the task was complete.</span></span>  
  
 <span data-ttu-id="65bef-150">Herhangi bir performans artışının neredeyse tamamen paralel işlemeden geldiğini ve eşzamanlı işlemden olmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="65bef-150">Note that any performance boost is almost entirely from the parallel processing and not the asynchronous processing.</span></span> <span data-ttu-id="65bef-151">Eşsenkronizasyonun avantajları, birden çok iş parçacığı bağlamaması ve kullanıcı arabirimi iş parçacığı bağlamamasıdır.</span><span class="sxs-lookup"><span data-stu-id="65bef-151">The advantages of asynchrony are that it doesn’t tie up multiple threads, and that it doesn’t tie up the user interface thread.</span></span>  
  
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
  
 <span data-ttu-id="65bef-152">Ve yöntemleri kullanırken, işlemi <xref:System.Threading.CancellationToken>orta akışta iptal etmek için kullanabileceğiniz bir , belirtebilirsiniz. <xref:System.IO.Stream.ReadAsync%2A> <xref:System.IO.Stream.WriteAsync%2A></span><span class="sxs-lookup"><span data-stu-id="65bef-152">When using the <xref:System.IO.Stream.WriteAsync%2A> and <xref:System.IO.Stream.ReadAsync%2A> methods, you can specify a <xref:System.Threading.CancellationToken>, which you can use to cancel the operation mid-stream.</span></span> <span data-ttu-id="65bef-153">Daha fazla bilgi için, Yönetilen İş Parçacıklarında [Async Uygulamanızı (C#) İnce Ayar](./fine-tuning-your-async-application.md) la ve [İptal'e](../../../../standard/threading/cancellation-in-managed-threads.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="65bef-153">For more information, see [Fine-Tuning Your Async Application (C#)](./fine-tuning-your-async-application.md) and [Cancellation in Managed Threads](../../../../standard/threading/cancellation-in-managed-threads.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65bef-154">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="65bef-154">See also</span></span>

- [<span data-ttu-id="65bef-155">Async ve await ile Asynchronous Programlama (C#)</span><span class="sxs-lookup"><span data-stu-id="65bef-155">Asynchronous Programming with async and await (C#)</span></span>](./index.md)
- [<span data-ttu-id="65bef-156">Async İade Türleri (C#)</span><span class="sxs-lookup"><span data-stu-id="65bef-156">Async Return Types (C#)</span></span>](./async-return-types.md)
- [<span data-ttu-id="65bef-157">Async Programlarında Kontrol Akışı (C#)</span><span class="sxs-lookup"><span data-stu-id="65bef-157">Control Flow in Async Programs (C#)</span></span>](./control-flow-in-async-programs.md)
