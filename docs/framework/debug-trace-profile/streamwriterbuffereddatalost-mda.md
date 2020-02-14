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
ms.openlocfilehash: 82940b40b302f4a928547f2e6a0c285727e13934
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216099"
---
# <a name="streamwriterbuffereddatalost-mda"></a><span data-ttu-id="d535c-102">streamWriterBufferedDataLost MDA</span><span class="sxs-lookup"><span data-stu-id="d535c-102">streamWriterBufferedDataLost MDA</span></span>
<span data-ttu-id="d535c-103">`streamWriterBufferedDataLost` yönetilen hata ayıklama Yardımcısı (MDA), bir <xref:System.IO.StreamWriter> yazıldığında etkinleştirilir, ancak <xref:System.IO.StreamWriter> örneği yok etmeden önce <xref:System.IO.StreamWriter.Flush%2A> veya <xref:System.IO.StreamWriter.Close%2A> yöntemi daha sonra çağrılmaz.</span><span class="sxs-lookup"><span data-stu-id="d535c-103">The `streamWriterBufferedDataLost` managed debugging assistant (MDA) is activated when a <xref:System.IO.StreamWriter> is written to, but the <xref:System.IO.StreamWriter.Flush%2A> or <xref:System.IO.StreamWriter.Close%2A> method is not subsequently called before the instance of the <xref:System.IO.StreamWriter> is destroyed.</span></span> <span data-ttu-id="d535c-104">Bu MDA etkin olduğunda, çalışma zamanı, arabelleğe alınmış verilerin <xref:System.IO.StreamWriter>içinde hala mevcut olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="d535c-104">When this MDA is enabled, the runtime determines whether any buffered data still exists within the <xref:System.IO.StreamWriter>.</span></span> <span data-ttu-id="d535c-105">Arabelleğe alınan veriler varsa, MDA etkin olur.</span><span class="sxs-lookup"><span data-stu-id="d535c-105">If buffered data does exist, the MDA is activated.</span></span> <span data-ttu-id="d535c-106"><xref:System.GC.Collect%2A> ve <xref:System.GC.WaitForPendingFinalizers%2A> yöntemlerinin çağrılması, sonlandırıcıları çalıştırmaya zorlayabilir.</span><span class="sxs-lookup"><span data-stu-id="d535c-106">Calling the <xref:System.GC.Collect%2A> and <xref:System.GC.WaitForPendingFinalizers%2A> methods can force finalizers to run.</span></span> <span data-ttu-id="d535c-107">Sonlandırıcılar, normalde Rastgele zamanlarda çalışır ve muhtemelen işlemden çıkılmaz.</span><span class="sxs-lookup"><span data-stu-id="d535c-107">Finalizers will otherwise run at seemingly arbitrary times, and possibly not at all on process exit.</span></span> <span data-ttu-id="d535c-108">Bu MDA etkin olan sonlandırıcıları açıkça çalıştırmak, bu tür bir sorunu daha güvenilir bir şekilde yeniden oluşturmaya yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="d535c-108">Explicitly running finalizers with this MDA enabled will help to more reliably reproduce this type of problem.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="d535c-109">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="d535c-109">Symptoms</span></span>  
 <span data-ttu-id="d535c-110"><xref:System.IO.StreamWriter>, bir dosyaya son 1 – 4 KB 'lık verileri yazmaz.</span><span class="sxs-lookup"><span data-stu-id="d535c-110">A <xref:System.IO.StreamWriter> does not write the last 1–4 KB of data to a file.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="d535c-111">Nedeni</span><span class="sxs-lookup"><span data-stu-id="d535c-111">Cause</span></span>  
 <span data-ttu-id="d535c-112"><xref:System.IO.StreamWriter> verileri dahili olarak arabelleğe alır, bu, arabelleğe alınan verileri temeldeki veri deposuna yazmak için <xref:System.IO.StreamWriter.Close%2A> veya <xref:System.IO.StreamWriter.Flush%2A> yönteminin çağrılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d535c-112">The <xref:System.IO.StreamWriter> buffers data internally, which requires that the <xref:System.IO.StreamWriter.Close%2A> or <xref:System.IO.StreamWriter.Flush%2A> method be called to write the buffered data to the underlying data store.</span></span> <span data-ttu-id="d535c-113"><xref:System.IO.StreamWriter.Close%2A> veya <xref:System.IO.StreamWriter.Flush%2A> uygun şekilde çağrılmamışsa, <xref:System.IO.StreamWriter> örneğinde arabelleğe alınan veriler beklenen şekilde yazılamaz.</span><span class="sxs-lookup"><span data-stu-id="d535c-113">If <xref:System.IO.StreamWriter.Close%2A> or <xref:System.IO.StreamWriter.Flush%2A> is not appropriately called, data buffered in the <xref:System.IO.StreamWriter> instance might not be written as expected.</span></span>  
  
 <span data-ttu-id="d535c-114">Aşağıda, bu MDA 'ın yakalandığı kötü yazılmış kodun bir örneği verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d535c-114">The following is an example of poorly written code that this MDA should catch.</span></span>  
  
```csharp  
// Poorly written code.  
void Write()   
{  
    StreamWriter sw = new StreamWriter("file.txt");  
    sw.WriteLine("Data");  
    // Problem: forgot to close the StreamWriter.  
}  
```  
  
 <span data-ttu-id="d535c-115">Önceki kod, bir atık toplama tetikleniyorsa ve sonlandırıcılar bitene kadar askıya alınırsa bu MDA 'ı daha güvenilir bir şekilde etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="d535c-115">The preceding code will activate this MDA more reliably if a garbage collection is triggered and then suspended until finalizers have finished.</span></span> <span data-ttu-id="d535c-116">Bu tür bir sorunu izlemek için aşağıdaki kodu bir hata ayıklama derlemesinde önceki metodun sonuna ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d535c-116">To track down this type of problem, you can add the following code to the end of the preceding method in a debug build.</span></span> <span data-ttu-id="d535c-117">Bu, MDA ' yi güvenilir bir şekilde etkinleştirmeye yardımcı olur, ancak elbette sorunun nedenini düzelmez.</span><span class="sxs-lookup"><span data-stu-id="d535c-117">This will help to reliably activate the MDA, but of course it does not fix the cause of the problem.</span></span>  
  
```csharp
GC.Collect();  
GC.WaitForPendingFinalizers();  
```  
  
## <a name="resolution"></a><span data-ttu-id="d535c-118">Çözüm</span><span class="sxs-lookup"><span data-stu-id="d535c-118">Resolution</span></span>  
 <span data-ttu-id="d535c-119">Bir uygulamayı veya bir <xref:System.IO.StreamWriter>örneğine sahip herhangi bir kod bloğunu kapatmadan önce <xref:System.IO.StreamWriter> <xref:System.IO.StreamWriter.Close%2A> veya <xref:System.IO.StreamWriter.Flush%2A> çağırdığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="d535c-119">Make sure you call <xref:System.IO.StreamWriter.Close%2A> or <xref:System.IO.StreamWriter.Flush%2A> on the <xref:System.IO.StreamWriter> before closing an application or any code block that has an instance of a <xref:System.IO.StreamWriter>.</span></span> <span data-ttu-id="d535c-120">Bunu elde etmek için en iyi mekanizmalardan biri, örneğin Visual Basic `using` bir C# blok (`Using`) oluşturarak Örneğin, yazıcı için <xref:System.IO.StreamWriter.Dispose%2A> yönteminin çağrılmasını ve örneğin doğru şekilde kapatılmasını sağlamak olacaktır.</span><span class="sxs-lookup"><span data-stu-id="d535c-120">One of the best mechanisms for achieving this is creating the instance with a C# `using` block (`Using` in Visual Basic), which will ensure the <xref:System.IO.StreamWriter.Dispose%2A> method for the writer is invoked, resulting in the instance being correctly closed.</span></span>  
  
```csharp
using(StreamWriter sw = new StreamWriter("file.txt"))   
{  
    sw.WriteLine("Data");  
}  
```  
  
 <span data-ttu-id="d535c-121">Aşağıdaki kod, `using`yerine `try/finally` kullanarak aynı çözümü gösterir.</span><span class="sxs-lookup"><span data-stu-id="d535c-121">The following code shows the same solution, using `try/finally` instead of `using`.</span></span>  
  
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
  
 <span data-ttu-id="d535c-122">Bu çözümlerin hiçbiri kullanılabilir (örneğin, bir <xref:System.IO.StreamWriter> statik bir değişkende depolanıyorsa ve yaşam süresinin sonunda kodu kolayca çalıştıramıyorsa), son kullanıldıktan sonra <xref:System.IO.StreamWriter> <xref:System.IO.StreamWriter.Flush%2A> çağırmak veya ilk kullanılmadan önce <xref:System.IO.StreamWriter.AutoFlush%2A> özelliğini `true` olarak ayarlamak bu sorundan kaçınmak zorunda kalmamak.</span><span class="sxs-lookup"><span data-stu-id="d535c-122">If neither of these solutions can be used (for example, if a <xref:System.IO.StreamWriter> is stored in a static variable and you cannot easily run code at the end of its lifetime), then calling <xref:System.IO.StreamWriter.Flush%2A> on the <xref:System.IO.StreamWriter> after its last use or setting the <xref:System.IO.StreamWriter.AutoFlush%2A> property to `true` before its first use should avoid this problem.</span></span>  
  
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
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="d535c-123">Çalışma zamanında etki</span><span class="sxs-lookup"><span data-stu-id="d535c-123">Effect on the Runtime</span></span>  
 <span data-ttu-id="d535c-124">Bu MDA çalışma zamanı üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="d535c-124">This MDA has no effect on the runtime.</span></span>  
  
## <a name="output"></a><span data-ttu-id="d535c-125">Çıktı</span><span class="sxs-lookup"><span data-stu-id="d535c-125">Output</span></span>  
 <span data-ttu-id="d535c-126">Bu ihlalin oluştuğunu belirten bir ileti.</span><span class="sxs-lookup"><span data-stu-id="d535c-126">A message indicating that this violation occurred.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="d535c-127">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="d535c-127">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <streamWriterBufferedDataLost />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d535c-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d535c-128">See also</span></span>

- <xref:System.IO.StreamWriter>
- [<span data-ttu-id="d535c-129">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="d535c-129">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
