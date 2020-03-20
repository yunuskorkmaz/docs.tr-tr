---
title: streamWriterBufferedDataLost MDA
ms.date: 03/30/2017
helpviewer_keywords:
- StreamWriter class, data buffering problems
- managed debugging assistants (MDAs), StreamWriter data buffering
- buffers, StreamWriter problems
- MDAs (managed debugging assistants), StreamWriter data buffering
- StreamWriter buffered data lost
- data buffering problems
- streamWriterBufferedDataLost MDA
ms.assetid: 6e5c07be-bc5b-437a-8398-8779e23126ab
ms.openlocfilehash: 18b2a5a95756ed125d26b2846c0b1ddc320463ea
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181735"
---
# <a name="streamwriterbuffereddatalost-mda"></a><span data-ttu-id="1d6c0-102">streamWriterBufferedDataLost MDA</span><span class="sxs-lookup"><span data-stu-id="1d6c0-102">streamWriterBufferedDataLost MDA</span></span>
<span data-ttu-id="1d6c0-103">Yönetilen `streamWriterBufferedDataLost` hata ayıklama yardımcısı (MDA) bir <xref:System.IO.StreamWriter> yazıldığında etkinleştirilir, ancak <xref:System.IO.StreamWriter.Flush%2A> veya <xref:System.IO.StreamWriter.Close%2A> yöntem daha sonra <xref:System.IO.StreamWriter> yok edilmeden önce çağrılmaz.</span><span class="sxs-lookup"><span data-stu-id="1d6c0-103">The `streamWriterBufferedDataLost` managed debugging assistant (MDA) is activated when a <xref:System.IO.StreamWriter> is written to, but the <xref:System.IO.StreamWriter.Flush%2A> or <xref:System.IO.StreamWriter.Close%2A> method is not subsequently called before the instance of the <xref:System.IO.StreamWriter> is destroyed.</span></span> <span data-ttu-id="1d6c0-104">Bu MDA etkinleştirildiğinde, çalışma zamanı arabelleğe alınan verilerin <xref:System.IO.StreamWriter>.</span><span class="sxs-lookup"><span data-stu-id="1d6c0-104">When this MDA is enabled, the runtime determines whether any buffered data still exists within the <xref:System.IO.StreamWriter>.</span></span> <span data-ttu-id="1d6c0-105">Arabelleğe alınan veriler varsa, MDA etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="1d6c0-105">If buffered data does exist, the MDA is activated.</span></span> <span data-ttu-id="1d6c0-106">Arama <xref:System.GC.Collect%2A> ve <xref:System.GC.WaitForPendingFinalizers%2A> yöntemleri sonlandırıcılar çalıştırmak için zorlayabilir.</span><span class="sxs-lookup"><span data-stu-id="1d6c0-106">Calling the <xref:System.GC.Collect%2A> and <xref:System.GC.WaitForPendingFinalizers%2A> methods can force finalizers to run.</span></span> <span data-ttu-id="1d6c0-107">Finalizers aksi takdirde görünüşte rasgele zamanlarda çalışacak ve muhtemelen hiç süreç çıkışında değil.</span><span class="sxs-lookup"><span data-stu-id="1d6c0-107">Finalizers will otherwise run at seemingly arbitrary times, and possibly not at all on process exit.</span></span> <span data-ttu-id="1d6c0-108">Bu MDA etkinleştirilmiş olan sonlandırıcıları açıkça çalıştırmak, bu tür bir sorunun daha güvenilir bir şekilde yeniden oluşturulmasına yardımcı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="1d6c0-108">Explicitly running finalizers with this MDA enabled will help to more reliably reproduce this type of problem.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="1d6c0-109">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="1d6c0-109">Symptoms</span></span>  
 <span data-ttu-id="1d6c0-110">A, <xref:System.IO.StreamWriter> bir dosyaya son 1-4 KB veri yazmaz.</span><span class="sxs-lookup"><span data-stu-id="1d6c0-110">A <xref:System.IO.StreamWriter> does not write the last 1–4 KB of data to a file.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="1d6c0-111">Nedeni</span><span class="sxs-lookup"><span data-stu-id="1d6c0-111">Cause</span></span>  
 <span data-ttu-id="1d6c0-112">Arabellekteki <xref:System.IO.StreamWriter> verileri dahili olarak, <xref:System.IO.StreamWriter.Close%2A> <xref:System.IO.StreamWriter.Flush%2A> arabelleğe alınan verileri temel veri deposuna yazmak için çağrılmasını gerektiren arabellekler.</span><span class="sxs-lookup"><span data-stu-id="1d6c0-112">The <xref:System.IO.StreamWriter> buffers data internally, which requires that the <xref:System.IO.StreamWriter.Close%2A> or <xref:System.IO.StreamWriter.Flush%2A> method be called to write the buffered data to the underlying data store.</span></span> <span data-ttu-id="1d6c0-113">Uygun <xref:System.IO.StreamWriter.Close%2A> <xref:System.IO.StreamWriter.Flush%2A> şekilde çağrılmazsa veya çağrılmazsa, <xref:System.IO.StreamWriter> örnekte arabelleğe alınan veriler beklendiği gibi yazılmayabilir.</span><span class="sxs-lookup"><span data-stu-id="1d6c0-113">If <xref:System.IO.StreamWriter.Close%2A> or <xref:System.IO.StreamWriter.Flush%2A> is not appropriately called, data buffered in the <xref:System.IO.StreamWriter> instance might not be written as expected.</span></span>  
  
 <span data-ttu-id="1d6c0-114">Aşağıda, bu MDA'nın yakalaması gereken kötü yazılmış kod örneği verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="1d6c0-114">The following is an example of poorly written code that this MDA should catch.</span></span>  
  
```csharp  
// Poorly written code.  
void Write()
{  
    StreamWriter sw = new StreamWriter("file.txt");  
    sw.WriteLine("Data");  
    // Problem: forgot to close the StreamWriter.  
}  
```  
  
 <span data-ttu-id="1d6c0-115">Bir çöp toplama tetiklenir ve sonlandırıcılar tamamlanana kadar askıya sonra önceki kod daha güvenilir bu MDA etkinleştirmek.</span><span class="sxs-lookup"><span data-stu-id="1d6c0-115">The preceding code will activate this MDA more reliably if a garbage collection is triggered and then suspended until finalizers have finished.</span></span> <span data-ttu-id="1d6c0-116">Bu tür bir sorunu izlemek için, hata ayıklama yapısında önceki yöntemin sonuna aşağıdaki kodu ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1d6c0-116">To track down this type of problem, you can add the following code to the end of the preceding method in a debug build.</span></span> <span data-ttu-id="1d6c0-117">Bu güvenilir MDA etkinleştirmek için yardımcı olacaktır, ama tabii ki sorunun nedenini düzeltmek değildir.</span><span class="sxs-lookup"><span data-stu-id="1d6c0-117">This will help to reliably activate the MDA, but of course it does not fix the cause of the problem.</span></span>  
  
```csharp
GC.Collect();  
GC.WaitForPendingFinalizers();  
```  
  
## <a name="resolution"></a><span data-ttu-id="1d6c0-118">Çözüm</span><span class="sxs-lookup"><span data-stu-id="1d6c0-118">Resolution</span></span>  
 <span data-ttu-id="1d6c0-119">Bir uygulamayı <xref:System.IO.StreamWriter.Close%2A> veya <xref:System.IO.StreamWriter.Flush%2A> bir <xref:System.IO.StreamWriter> <xref:System.IO.StreamWriter>'nin örneğini olan herhangi bir kod bloğunu kapatmadan önce veya üzerinde arama yaptığınızdan emin olun</span><span class="sxs-lookup"><span data-stu-id="1d6c0-119">Make sure you call <xref:System.IO.StreamWriter.Close%2A> or <xref:System.IO.StreamWriter.Flush%2A> on the <xref:System.IO.StreamWriter> before closing an application or any code block that has an instance of a <xref:System.IO.StreamWriter>.</span></span> <span data-ttu-id="1d6c0-120">Bunu başarmak için en iyi mekanizmalardan biri, yazarın `using` yönteminin`Using` <xref:System.IO.StreamWriter.Dispose%2A> çağrılmasını sağlayacak c# bloğu (Visual Basic)'de örneği oluşturmak tır ve bu da örneğin doğru şekilde kapatılmasıyla sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="1d6c0-120">One of the best mechanisms for achieving this is creating the instance with a C# `using` block (`Using` in Visual Basic), which will ensure the <xref:System.IO.StreamWriter.Dispose%2A> method for the writer is invoked, resulting in the instance being correctly closed.</span></span>  
  
```csharp
using(StreamWriter sw = new StreamWriter("file.txt"))
{  
    sw.WriteLine("Data");  
}  
```  
  
 <span data-ttu-id="1d6c0-121">Aşağıdaki kod, `try/finally` `using`yerine kullanarak aynı çözümü gösterir.</span><span class="sxs-lookup"><span data-stu-id="1d6c0-121">The following code shows the same solution, using `try/finally` instead of `using`.</span></span>  
  
```csharp
StreamWriter sw;  
try
{  
    sw = new StreamWriter("file.txt"));  
    sw.WriteLine("Data");  
}  
finally
{  
    if (sw != null)  
        sw.Close();  
}  
```  
  
 <span data-ttu-id="1d6c0-122">Bu çözümlerden hiçbiri kullanılamıyorsa (örneğin, <xref:System.IO.StreamWriter> a statik bir değişkende depolanıyorsa ve kodu ömrünün <xref:System.IO.StreamWriter.Flush%2A> sonunda <xref:System.IO.StreamWriter> kolayca çalıştıramıyorsanız), <xref:System.IO.StreamWriter.AutoFlush%2A> son `true` kullanımdan sonra gelene çağrı yapmak veya özelliği ilk kullanımdan önce ayarlamak bu sorunu önlemelidir.</span><span class="sxs-lookup"><span data-stu-id="1d6c0-122">If neither of these solutions can be used (for example, if a <xref:System.IO.StreamWriter> is stored in a static variable and you cannot easily run code at the end of its lifetime), then calling <xref:System.IO.StreamWriter.Flush%2A> on the <xref:System.IO.StreamWriter> after its last use or setting the <xref:System.IO.StreamWriter.AutoFlush%2A> property to `true` before its first use should avoid this problem.</span></span>  
  
```csharp
private static StreamWriter log;  
// static class constructor.  
static WriteToFile()
{  
    StreamWriter sw = new StreamWriter("log.txt");  
    sw.AutoFlush = true;  
  
    // Publish the StreamWriter for other threads.  
    log = sw;  
}  
```  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="1d6c0-123">Çalışma Süresi üzerindeki etkisi</span><span class="sxs-lookup"><span data-stu-id="1d6c0-123">Effect on the Runtime</span></span>  
 <span data-ttu-id="1d6c0-124">Bu MDA'nın çalışma zamanı üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="1d6c0-124">This MDA has no effect on the runtime.</span></span>  
  
## <a name="output"></a><span data-ttu-id="1d6c0-125">Çıktı</span><span class="sxs-lookup"><span data-stu-id="1d6c0-125">Output</span></span>  
 <span data-ttu-id="1d6c0-126">Bu ihlalin oluştuğunu belirten bir ileti.</span><span class="sxs-lookup"><span data-stu-id="1d6c0-126">A message indicating that this violation occurred.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="1d6c0-127">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="1d6c0-127">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <streamWriterBufferedDataLost />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1d6c0-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1d6c0-128">See also</span></span>

- <xref:System.IO.StreamWriter>
- [<span data-ttu-id="1d6c0-129">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="1d6c0-129">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
