---
title: (Visual Basic) dosya erişimi için Async kullanma
ms.date: 07/20/2015
ms.assetid: c989305f-08e3-4687-95c3-948465cda202
ms.openlocfilehash: 76abb5460bbadd234d761a0cce2f0082bb5894a9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54587508"
---
# <a name="using-async-for-file-access-visual-basic"></a><span data-ttu-id="952cf-102">(Visual Basic) dosya erişimi için Async kullanma</span><span class="sxs-lookup"><span data-stu-id="952cf-102">Using Async for File Access (Visual Basic)</span></span>
<span data-ttu-id="952cf-103">Async özelliği dosyalara erişmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="952cf-103">You can use the Async feature to access files.</span></span> <span data-ttu-id="952cf-104">Async özelliği'ni kullanarak geri çağırmaları kullanarak veya birden çok yöntemlerde veya lambda ifadelerinde kodunuzu bölme olmadan zaman uyumsuz yöntemleri çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="952cf-104">By using the Async feature, you can call into asynchronous methods without using callbacks or splitting your code across multiple methods or lambda expressions.</span></span> <span data-ttu-id="952cf-105">Eş zamanlı kod zaman uyumsuz hale getirmek için yalnızca zaman uyumlu bir yöntem yerine zaman uyumsuz yöntemini çağırın ve birkaç anahtar sözcükler için kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="952cf-105">To make synchronous code asynchronous, you just call an asynchronous method instead of a synchronous method and add a few keywords to the code.</span></span>  
  
 <span data-ttu-id="952cf-106">Dosya erişim çağrıları zaman uyumsuzluğu eklemek için aşağıdaki nedenlerden düşünebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="952cf-106">You might consider the following reasons for adding asynchrony to file access calls:</span></span>  
  
-   <span data-ttu-id="952cf-107">İşlemi başlatan kullanıcı Arabirimi iş parçacığı başka işleri gerçekleştirebilirsiniz çünkü faaliyetler UI uygulamaları daha hızlı sağlar.</span><span class="sxs-lookup"><span data-stu-id="952cf-107">Asynchrony makes UI applications more responsive because the UI thread that launches the operation can perform other work.</span></span> <span data-ttu-id="952cf-108">UI iş parçacığı kod yürütülmesi gerekiyorsa (örneğin, 50'den fazla milisaniye) uzun zaman alan, UI ve UI iş parçacığı yeniden klavye işleyebilir ve giriş ve diğer olayları fare g/ç işlemi tamamlanana kadar donabilir.</span><span class="sxs-lookup"><span data-stu-id="952cf-108">If the UI thread must execute code that takes a long time (for example, more than 50 milliseconds), the UI may freeze until the I/O is complete and the UI thread can again process keyboard and mouse input and other events.</span></span>  
  
-   <span data-ttu-id="952cf-109">İş parçacıkları gereksinimini azaltarak ASP.NET ölçeklenebilirliğini ve diğer sunucu tabanlı uygulamalar faaliyetler artırır.</span><span class="sxs-lookup"><span data-stu-id="952cf-109">Asynchrony improves the scalability of ASP.NET and other server-based applications by reducing the need for threads.</span></span> <span data-ttu-id="952cf-110">Binlerce iş parçacıkları, adanmış bir iş parçacığı başına yanıt uygulama kullanıyorsa ve binlerce istekleri aynı anda işlenmekte gereklidir.</span><span class="sxs-lookup"><span data-stu-id="952cf-110">If the application uses a dedicated thread per response and a thousand requests are being handled simultaneously, a thousand threads are needed.</span></span> <span data-ttu-id="952cf-111">Zaman uyumsuz işlemler genellikle bir iş parçacığı bekleme sırasında kullanmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="952cf-111">Asynchronous operations often don’t need to use a thread during the wait.</span></span> <span data-ttu-id="952cf-112">Mevcut g/ç Tamamlama iş parçacığı kısa bir süre sonunda kullanırlar.</span><span class="sxs-lookup"><span data-stu-id="952cf-112">They use the existing I/O completion thread briefly at the end.</span></span>  
  
-   <span data-ttu-id="952cf-113">Bir dosya erişim işlemi gecikme süresini geçerli koşullar altında çok düşük olabilir ancak gecikme süresi gelecekte büyük ölçüde artırabilir.</span><span class="sxs-lookup"><span data-stu-id="952cf-113">The latency of a file access operation might be very low under current conditions, but the latency may greatly increase in the future.</span></span> <span data-ttu-id="952cf-114">Örneğin, bir dosya dünya genelindeki bir sunucuya taşınabilir.</span><span class="sxs-lookup"><span data-stu-id="952cf-114">For example, a file may be moved to a server that's across the world.</span></span>  
  
-   <span data-ttu-id="952cf-115">Ek yükü zaman uyumsuz özelliğini kullanarak küçük.</span><span class="sxs-lookup"><span data-stu-id="952cf-115">The added overhead of using the Async feature is small.</span></span>  
  
-   <span data-ttu-id="952cf-116">Zaman uyumsuz görevleri kolayca paralel olarak çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="952cf-116">Asynchronous tasks can easily be run in parallel.</span></span>  
  
## <a name="running-the-examples"></a><span data-ttu-id="952cf-117">Örnekleri çalıştırma</span><span class="sxs-lookup"><span data-stu-id="952cf-117">Running the Examples</span></span>  
 <span data-ttu-id="952cf-118">Bu konudaki örnekleri çalıştırmak için oluşturabileceğiniz bir **WPF uygulaması** veya **Windows Forms uygulaması** ve ardından eklemek bir **düğmesi**.</span><span class="sxs-lookup"><span data-stu-id="952cf-118">To run the examples in this topic, you can create a **WPF Application** or a **Windows Forms Application** and then add a **Button**.</span></span> <span data-ttu-id="952cf-119">Düğmenin içinde `Click` olay, her örnekte ilk yönteme bir çağrı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="952cf-119">In the button's `Click` event, add a call to the first method in each example.</span></span>  
  
 <span data-ttu-id="952cf-120">Aşağıdaki örneklerde, aşağıdakiler dahil `Imports` deyimleri.</span><span class="sxs-lookup"><span data-stu-id="952cf-120">In the following examples, include the following `Imports` statements.</span></span>  
  
```vb  
Imports System  
Imports System.Collections.Generic  
Imports System.Diagnostics  
Imports System.IO  
Imports System.Text  
Imports System.Threading.Tasks  
```  
  
## <a name="use-of-the-filestream-class"></a><span data-ttu-id="952cf-121">FILESTREAM sınıfının kullanımı</span><span class="sxs-lookup"><span data-stu-id="952cf-121">Use of the FileStream Class</span></span>  
 <span data-ttu-id="952cf-122">Bu konuda kullanım örnekleri <xref:System.IO.FileStream> işletim sistemi düzeyinde gerçekleşmesi zaman uyumsuz g/ç neden olan bir seçenek olduğu sınıf.</span><span class="sxs-lookup"><span data-stu-id="952cf-122">The examples in this topic use the <xref:System.IO.FileStream> class, which has an option that causes asynchronous I/O to occur at the operating system level.</span></span> <span data-ttu-id="952cf-123">Bu seçeneği kullanarak, çoğu durumda bir iş parçacığı havuzu iş parçacığını engelleme önleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="952cf-123">By using this option, you can avoid blocking a ThreadPool thread in many cases.</span></span> <span data-ttu-id="952cf-124">Bu seçeneği etkinleştirmek için belirttiğiniz `useAsync=true` veya `options=FileOptions.Asynchronous` Oluşturucusu çağrısında bağımsız değişken.</span><span class="sxs-lookup"><span data-stu-id="952cf-124">To enable this option, you specify the `useAsync=true` or `options=FileOptions.Asynchronous` argument in the constructor call.</span></span>  
  
 <span data-ttu-id="952cf-125">Bu seçeneği kullanamazsınız <xref:System.IO.StreamReader> ve <xref:System.IO.StreamWriter> doğrudan bir dosya yolu belirterek açarsanız.</span><span class="sxs-lookup"><span data-stu-id="952cf-125">You can’t use this option with <xref:System.IO.StreamReader> and <xref:System.IO.StreamWriter> if you open them directly by specifying a file path.</span></span> <span data-ttu-id="952cf-126">Ancak, bunları sağlarsanız, bu seçeneği kullanabilirsiniz bir <xref:System.IO.Stream> , <xref:System.IO.FileStream> sınıfı açılır.</span><span class="sxs-lookup"><span data-stu-id="952cf-126">However, you can use this option if you provide them a <xref:System.IO.Stream> that the <xref:System.IO.FileStream> class opened.</span></span> <span data-ttu-id="952cf-127">Bir iş parçacığı havuzu iş parçacığı engellenir bile, UI iş parçacığı, bekleme sırasında bloke değildir çünkü zaman uyumsuz çağrıları UI uygulamaları daha hızlı olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="952cf-127">Note that asynchronous calls are faster in UI apps even if a ThreadPool thread is blocked, because the UI thread isn’t blocked during the wait.</span></span>  
  
## <a name="writing-text"></a><span data-ttu-id="952cf-128">Metin yazma</span><span class="sxs-lookup"><span data-stu-id="952cf-128">Writing Text</span></span>  
 <span data-ttu-id="952cf-129">Aşağıdaki örnek, bir dosyaya metin yazar.</span><span class="sxs-lookup"><span data-stu-id="952cf-129">The following example writes text to a file.</span></span> <span data-ttu-id="952cf-130">Her deyim await, yöntem hemen çıkar.</span><span class="sxs-lookup"><span data-stu-id="952cf-130">At each await statement, the method immediately exits.</span></span> <span data-ttu-id="952cf-131">Dosya g/ç işlemi tamamlandığında, yöntem bekleme ifadesinin izleyen deyime sürdürür.</span><span class="sxs-lookup"><span data-stu-id="952cf-131">When the file I/O is complete, the method resumes at the statement that follows the await statement.</span></span> <span data-ttu-id="952cf-132">Zaman uyumsuz değiştirici bekleme ifadesinin yöntem tanımında olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="952cf-132">Note that the async modifier is in the definition of methods that use the await statement.</span></span>  
  
```vb  
Public Async Sub ProcessWrite()  
    Dim filePath = "temp2.txt"  
    Dim text = "Hello World" & ControlChars.CrLf  
  
    Await WriteTextAsync(filePath, text)  
End Sub  
  
Private Async Function WriteTextAsync(filePath As String, text As String) As Task  
    Dim encodedText As Byte() = Encoding.Unicode.GetBytes(text)  
  
    Using sourceStream As New FileStream(filePath,  
        FileMode.Append, FileAccess.Write, FileShare.None,  
        bufferSize:=4096, useAsync:=True)  
  
        Await sourceStream.WriteAsync(encodedText, 0, encodedText.Length)  
    End Using  
End Function  
```  
  
 <span data-ttu-id="952cf-133">Deyimi özgün örneğe sahip `Await sourceStream.WriteAsync(encodedText, 0, encodedText.Length)`, aşağıdaki iki deyimi, bir kısaltma olduğundan:</span><span class="sxs-lookup"><span data-stu-id="952cf-133">The original example has the statement `Await sourceStream.WriteAsync(encodedText, 0, encodedText.Length)`, which is a contraction of the following two statements:</span></span>  
  
```vb  
Dim theTask As Task = sourceStream.WriteAsync(encodedText, 0, encodedText.Length)  
Await theTask  
```  
  
 <span data-ttu-id="952cf-134">İlk deyim, bir görev döndürür ve başlatmak, dosya işleme neden olur.</span><span class="sxs-lookup"><span data-stu-id="952cf-134">The first statement returns a task and causes file processing to start.</span></span> <span data-ttu-id="952cf-135">Await ile ikinci deyim, yöntem hemen çıkın ve farklı bir görev döndürür neden olur.</span><span class="sxs-lookup"><span data-stu-id="952cf-135">The second statement with the await causes the method to immediately exit and return a different task.</span></span> <span data-ttu-id="952cf-136">Dosya daha sonra işleme tamamlandıktan sonra yürütme bekleme takip eden deyime döndürür.</span><span class="sxs-lookup"><span data-stu-id="952cf-136">When the file processing later completes, execution returns to the statement that follows the await.</span></span> <span data-ttu-id="952cf-137">Daha fazla bilgi için [zaman uyumsuz programlarda (Visual Basic) denetim akışı](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md).</span><span class="sxs-lookup"><span data-stu-id="952cf-137">For more information, see  [Control Flow in Async Programs (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md).</span></span>  
  
## <a name="reading-text"></a><span data-ttu-id="952cf-138">Metin okuma</span><span class="sxs-lookup"><span data-stu-id="952cf-138">Reading Text</span></span>  
 <span data-ttu-id="952cf-139">Aşağıdaki örnek, bir dosyadan metin okur.</span><span class="sxs-lookup"><span data-stu-id="952cf-139">The following example reads text from a file.</span></span> <span data-ttu-id="952cf-140">Metin arabelleğe alınır ve bu durumda, içine yerleştirilen bir <xref:System.Text.StringBuilder>.</span><span class="sxs-lookup"><span data-stu-id="952cf-140">The text is buffered and, in this case, placed into a <xref:System.Text.StringBuilder>.</span></span> <span data-ttu-id="952cf-141">Önceki örnekte, farklı bir değer await değerlendirilmesiyle üretir.</span><span class="sxs-lookup"><span data-stu-id="952cf-141">Unlike in the previous example, the evaluation of the await produces a value.</span></span> <span data-ttu-id="952cf-142"><xref:System.IO.Stream.ReadAsync%2A> Yöntemi döndürür bir <xref:System.Threading.Tasks.Task> \< <xref:System.Int32>>, await değerlendirilmesiyle üreten bir `Int32` değeri (`numRead`) işlemi tamamlandıktan sonra.</span><span class="sxs-lookup"><span data-stu-id="952cf-142">The <xref:System.IO.Stream.ReadAsync%2A> method returns a <xref:System.Threading.Tasks.Task>\<<xref:System.Int32>>, so the evaluation of the await produces an `Int32` value (`numRead`) after the operation completes.</span></span> <span data-ttu-id="952cf-143">Daha fazla bilgi için [zaman uyumsuz dönüş türleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="952cf-143">For more information, see [Async Return Types (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span></span>  
  
```vb  
Public Async Sub ProcessRead()  
    Dim filePath = "temp2.txt"  
  
    If File.Exists(filePath) = False Then  
        Debug.WriteLine("file not found: " & filePath)  
    Else  
        Try  
            Dim text As String = Await ReadTextAsync(filePath)  
            Debug.WriteLine(text)  
        Catch ex As Exception  
            Debug.WriteLine(ex.Message)  
        End Try  
    End If  
End Sub  
  
Private Async Function ReadTextAsync(filePath As String) As Task(Of String)  
  
    Using sourceStream As New FileStream(filePath,  
        FileMode.Open, FileAccess.Read, FileShare.Read,  
        bufferSize:=4096, useAsync:=True)  
  
        Dim sb As New StringBuilder  
  
        Dim buffer As Byte() = New Byte(&H1000) {}  
        Dim numRead As Integer  
        numRead = Await sourceStream.ReadAsync(buffer, 0, buffer.Length)  
        While numRead <> 0  
            Dim text As String = Encoding.Unicode.GetString(buffer, 0, numRead)  
            sb.Append(text)  
  
            numRead = Await sourceStream.ReadAsync(buffer, 0, buffer.Length)  
        End While  
  
        Return sb.ToString  
    End Using  
End Function  
```  
  
## <a name="parallel-asynchronous-io"></a><span data-ttu-id="952cf-144">Paralel zaman uyumsuz g/ç</span><span class="sxs-lookup"><span data-stu-id="952cf-144">Parallel Asynchronous I/O</span></span>  
 <span data-ttu-id="952cf-145">Aşağıdaki örnek, 10 metin dosyaları yazma tarafından paralel işleme gösterir.</span><span class="sxs-lookup"><span data-stu-id="952cf-145">The following example demonstrates parallel processing by writing 10 text files.</span></span> <span data-ttu-id="952cf-146">Her dosya için <xref:System.IO.Stream.WriteAsync%2A> yöntemi görevlerinin listesi için daha sonra eklenen bir görev döndürür.</span><span class="sxs-lookup"><span data-stu-id="952cf-146">For each file, the <xref:System.IO.Stream.WriteAsync%2A> method returns a task that is then added to a list of tasks.</span></span> <span data-ttu-id="952cf-147">`Await Task.WhenAll(tasks)` Deyimi yöntemin çıkar ve sürdürür dosya işleme olduğunda yöntemi içindeki tüm görevlerin tamamlayın.</span><span class="sxs-lookup"><span data-stu-id="952cf-147">The `Await Task.WhenAll(tasks)` statement exits the method and resumes within the method when file processing is complete for all of the tasks.</span></span>  
  
 <span data-ttu-id="952cf-148">Tüm örnek kapatır <xref:System.IO.FileStream> içinde örnekler bir `Finally` görevler tamamlandıktan sonra engelleyin.</span><span class="sxs-lookup"><span data-stu-id="952cf-148">The example closes all <xref:System.IO.FileStream> instances in a `Finally` block after the tasks are complete.</span></span> <span data-ttu-id="952cf-149">Her varsa `FileStream` yerine içinde oluşturulmuş bir `Imports` deyimi `FileStream` görev tamamlanmadan önce elden.</span><span class="sxs-lookup"><span data-stu-id="952cf-149">If each `FileStream` was instead created in a `Imports` statement, the `FileStream` might be disposed of before the task was complete.</span></span>  
  
 <span data-ttu-id="952cf-150">Herhangi bir performans artışının neredeyse tamamen paralel işleme ve olmayan uyumsuz olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="952cf-150">Note that any performance boost is almost entirely from the parallel processing and not the asynchronous processing.</span></span> <span data-ttu-id="952cf-151">Faaliyetler avantajları şunlardır: birden çok iş parçacıklarını tie değil ve kullanıcı arabirimi iş parçacığı ' tie değil.</span><span class="sxs-lookup"><span data-stu-id="952cf-151">The advantages of asynchrony are that it doesn’t tie up multiple threads, and that it doesn’t tie up the user interface thread.</span></span>  
  
```vb  
Public Async Sub ProcessWriteMult()  
    Dim folder = "tempfolder\"  
    Dim tasks As New List(Of Task)  
    Dim sourceStreams As New List(Of FileStream)  
  
    Try  
        For index = 1 To 10  
            Dim text = "In file " & index.ToString & ControlChars.CrLf  
  
            Dim fileName = "thefile" & index.ToString("00") & ".txt"  
            Dim filePath = folder & fileName  
  
            Dim encodedText As Byte() = Encoding.Unicode.GetBytes(text)  
  
            Dim sourceStream As New FileStream(filePath,  
                FileMode.Append, FileAccess.Write, FileShare.None,  
                bufferSize:=4096, useAsync:=True)  
  
            Dim theTask As Task = sourceStream.WriteAsync(encodedText, 0, encodedText.Length)  
            sourceStreams.Add(sourceStream)  
  
            tasks.Add(theTask)  
        Next  
  
        Await Task.WhenAll(tasks)  
    Finally  
        For Each sourceStream As FileStream In sourceStreams  
            sourceStream.Close()  
        Next  
    End Try  
End Sub  
```  
  
 <span data-ttu-id="952cf-152">Kullanırken <xref:System.IO.Stream.WriteAsync%2A> ve <xref:System.IO.Stream.ReadAsync%2A> yöntemleri belirtebilirsiniz bir <xref:System.Threading.CancellationToken>, hangi işlemin ortasında akış iptal etmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="952cf-152">When using the <xref:System.IO.Stream.WriteAsync%2A> and <xref:System.IO.Stream.ReadAsync%2A> methods, you can specify a <xref:System.Threading.CancellationToken>, which you can use to cancel the operation mid-stream.</span></span> <span data-ttu-id="952cf-153">Daha fazla bilgi için [Fine-Tuning Async uygulamanızda (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md) ve [yönetilen iş parçacıklarında iptal](../../../../standard/threading/cancellation-in-managed-threads.md).</span><span class="sxs-lookup"><span data-stu-id="952cf-153">For more information, see [Fine-Tuning Your Async Application (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md) and [Cancellation in Managed Threads](../../../../standard/threading/cancellation-in-managed-threads.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="952cf-154">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="952cf-154">See also</span></span>
- [<span data-ttu-id="952cf-155">Zaman uyumsuz programlama ile Async ve Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="952cf-155">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/index.md)
- [<span data-ttu-id="952cf-156">Zaman uyumsuz dönüş türleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="952cf-156">Async Return Types (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md)
- [<span data-ttu-id="952cf-157">Zaman uyumsuz programlarda (Visual Basic) denetim akışı</span><span class="sxs-lookup"><span data-stu-id="952cf-157">Control Flow in Async Programs (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)
