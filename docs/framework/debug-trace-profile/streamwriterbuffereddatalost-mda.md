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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c3dcdd329318d48efa203d2b9dcbfe3501d94b3e
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052275"
---
# <a name="streamwriterbuffereddatalost-mda"></a><span data-ttu-id="b5006-102">streamWriterBufferedDataLost MDA</span><span class="sxs-lookup"><span data-stu-id="b5006-102">streamWriterBufferedDataLost MDA</span></span>
<span data-ttu-id="b5006-103"><xref:System.IO.StreamWriter.Flush%2A> <xref:System.IO.StreamWriter> <xref:System.IO.StreamWriter> <xref:System.IO.StreamWriter.Close%2A> Yönetilen hata ayıklama Yardımcısı (MDA), öğesine yazıldığında etkinleştirilir, ancak ya da yöntemi daha sonra örneği yok edildiğinde çağrılır. `streamWriterBufferedDataLost`</span><span class="sxs-lookup"><span data-stu-id="b5006-103">The `streamWriterBufferedDataLost` managed debugging assistant (MDA) is activated when a <xref:System.IO.StreamWriter> is written to, but the <xref:System.IO.StreamWriter.Flush%2A> or <xref:System.IO.StreamWriter.Close%2A> method is not subsequently called before the instance of the <xref:System.IO.StreamWriter> is destroyed.</span></span> <span data-ttu-id="b5006-104">Bu MDA etkin olduğunda, çalışma zamanı, arabelleğe alınmış verilerin hala içinde <xref:System.IO.StreamWriter>varolup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="b5006-104">When this MDA is enabled, the runtime determines whether any buffered data still exists within the <xref:System.IO.StreamWriter>.</span></span> <span data-ttu-id="b5006-105">Arabelleğe alınan veriler varsa, MDA etkin olur.</span><span class="sxs-lookup"><span data-stu-id="b5006-105">If buffered data does exist, the MDA is activated.</span></span> <span data-ttu-id="b5006-106"><xref:System.GC.Collect%2A> Ve<xref:System.GC.WaitForPendingFinalizers%2A> yöntemlerini çağırmak, sonlandırıcıları çalıştırmaya zorlayabilir.</span><span class="sxs-lookup"><span data-stu-id="b5006-106">Calling the <xref:System.GC.Collect%2A> and <xref:System.GC.WaitForPendingFinalizers%2A> methods can force finalizers to run.</span></span> <span data-ttu-id="b5006-107">Sonlandırıcılar, normalde Rastgele zamanlarda çalışır ve muhtemelen işlemden çıkılmaz.</span><span class="sxs-lookup"><span data-stu-id="b5006-107">Finalizers will otherwise run at seemingly arbitrary times, and possibly not at all on process exit.</span></span> <span data-ttu-id="b5006-108">Bu MDA etkin olan sonlandırıcıları açıkça çalıştırmak, bu tür bir sorunu daha güvenilir bir şekilde yeniden oluşturmaya yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="b5006-108">Explicitly running finalizers with this MDA enabled will help to more reliably reproduce this type of problem.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="b5006-109">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="b5006-109">Symptoms</span></span>  
 <span data-ttu-id="b5006-110">A <xref:System.IO.StreamWriter> bir dosyaya son 1 – 4 KB veri yazmaz.</span><span class="sxs-lookup"><span data-stu-id="b5006-110">A <xref:System.IO.StreamWriter> does not write the last 1–4 KB of data to a file.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="b5006-111">Sebep</span><span class="sxs-lookup"><span data-stu-id="b5006-111">Cause</span></span>  
 <span data-ttu-id="b5006-112">Verileri dahili olarak arabelleğe <xref:System.IO.StreamWriter.Close%2A> <xref:System.IO.StreamWriter.Flush%2A> alır. Bu, ya da yönteminin, arabelleğe alınan verileri temeldeki veri deposuna yazmak üzere çağrılması gerekir. <xref:System.IO.StreamWriter></span><span class="sxs-lookup"><span data-stu-id="b5006-112">The <xref:System.IO.StreamWriter> buffers data internally, which requires that the <xref:System.IO.StreamWriter.Close%2A> or <xref:System.IO.StreamWriter.Flush%2A> method be called to write the buffered data to the underlying data store.</span></span> <span data-ttu-id="b5006-113">Ya da <xref:System.IO.StreamWriter.Flush%2A> uygun bir şekilde çağrılmamışsa <xref:System.IO.StreamWriter> , örnekte ara belleğe alınan veriler beklenen şekilde yazılmayabilir. <xref:System.IO.StreamWriter.Close%2A></span><span class="sxs-lookup"><span data-stu-id="b5006-113">If <xref:System.IO.StreamWriter.Close%2A> or <xref:System.IO.StreamWriter.Flush%2A> is not appropriately called, data buffered in the <xref:System.IO.StreamWriter> instance might not be written as expected.</span></span>  
  
 <span data-ttu-id="b5006-114">Aşağıda, bu MDA 'ın yakalandığı kötü yazılmış kodun bir örneği verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="b5006-114">The following is an example of poorly written code that this MDA should catch.</span></span>  
  
```csharp  
// Poorly written code.  
void Write()   
{  
    StreamWriter sw = new StreamWriter("file.txt");  
    sw.WriteLine("Data");  
    // Problem: forgot to close the StreamWriter.  
}  
```  
  
 <span data-ttu-id="b5006-115">Önceki kod, bir atık toplama tetikleniyorsa ve sonlandırıcılar bitene kadar askıya alınırsa bu MDA 'ı daha güvenilir bir şekilde etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="b5006-115">The preceding code will activate this MDA more reliably if a garbage collection is triggered and then suspended until finalizers have finished.</span></span> <span data-ttu-id="b5006-116">Bu tür bir sorunu izlemek için aşağıdaki kodu bir hata ayıklama derlemesinde önceki metodun sonuna ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b5006-116">To track down this type of problem, you can add the following code to the end of the preceding method in a debug build.</span></span> <span data-ttu-id="b5006-117">Bu, MDA ' yi güvenilir bir şekilde etkinleştirmeye yardımcı olur, ancak elbette sorunun nedenini düzelmez.</span><span class="sxs-lookup"><span data-stu-id="b5006-117">This will help to reliably activate the MDA, but of course it does not fix the cause of the problem.</span></span>  
  
```csharp
GC.Collect();  
GC.WaitForPendingFinalizers();  
```  
  
## <a name="resolution"></a><span data-ttu-id="b5006-118">Çözüm</span><span class="sxs-lookup"><span data-stu-id="b5006-118">Resolution</span></span>  
 <span data-ttu-id="b5006-119">Bir uygulamayı veya bir <xref:System.IO.StreamWriter.Close%2A> <xref:System.IO.StreamWriter> <xref:System.IO.StreamWriter.Flush%2A> örneğine<xref:System.IO.StreamWriter>sahip herhangi bir kod bloğunu kapatmadan önce veya ' de ' i çağırdığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="b5006-119">Make sure you call <xref:System.IO.StreamWriter.Close%2A> or <xref:System.IO.StreamWriter.Flush%2A> on the <xref:System.IO.StreamWriter> before closing an application or any code block that has an instance of a <xref:System.IO.StreamWriter>.</span></span> <span data-ttu-id="b5006-120">Bunu elde etmek için en iyi mekanizmalardan biri, örneğin C# `using` , yazıcı <xref:System.IO.StreamWriter.Dispose%2A> yönteminin çağrılmasını ve`Using` örneğin doğru şekilde kapatılmasını sağlamak için bir blok (Visual Basic) ile örneği oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="b5006-120">One of the best mechanisms for achieving this is creating the instance with a C# `using` block (`Using` in Visual Basic), which will ensure the <xref:System.IO.StreamWriter.Dispose%2A> method for the writer is invoked, resulting in the instance being correctly closed.</span></span>  
  
```csharp
using(StreamWriter sw = new StreamWriter("file.txt"))   
{  
    sw.WriteLine("Data");  
}  
```  
  
 <span data-ttu-id="b5006-121">Aşağıdaki kod, `try/finally` `using`yerine kullanılarak aynı çözümü gösterir.</span><span class="sxs-lookup"><span data-stu-id="b5006-121">The following code shows the same solution, using `try/finally` instead of `using`.</span></span>  
  
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
  
 <span data-ttu-id="b5006-122">Bu çözümlerin hiçbiri kullanılabilir değilse <xref:System.IO.StreamWriter> (örneğin, bir statik değişkende depolanıyorsa ve yaşam süresinin sonunda kodu kolayca çalıştıramıyorsa), <xref:System.IO.StreamWriter.Flush%2A> <xref:System.IO.StreamWriter> en son kullanımı veya ayarı <xref:System.IO.StreamWriter.AutoFlush%2A> ilk kullanımı `true` öncesindeki özelliğin bu sorundan kaçınmak gerekir.</span><span class="sxs-lookup"><span data-stu-id="b5006-122">If neither of these solutions can be used (for example, if a <xref:System.IO.StreamWriter> is stored in a static variable and you cannot easily run code at the end of its lifetime), then calling <xref:System.IO.StreamWriter.Flush%2A> on the <xref:System.IO.StreamWriter> after its last use or setting the <xref:System.IO.StreamWriter.AutoFlush%2A> property to `true` before its first use should avoid this problem.</span></span>  
  
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
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="b5006-123">Çalışma zamanında etki</span><span class="sxs-lookup"><span data-stu-id="b5006-123">Effect on the Runtime</span></span>  
 <span data-ttu-id="b5006-124">Bu MDA çalışma zamanı üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="b5006-124">This MDA has no effect on the runtime.</span></span>  
  
## <a name="output"></a><span data-ttu-id="b5006-125">Çıkış</span><span class="sxs-lookup"><span data-stu-id="b5006-125">Output</span></span>  
 <span data-ttu-id="b5006-126">Bu ihlalin oluştuğunu belirten bir ileti.</span><span class="sxs-lookup"><span data-stu-id="b5006-126">A message indicating that this violation occurred.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="b5006-127">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="b5006-127">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <streamWriterBufferedDataLost />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b5006-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b5006-128">See also</span></span>

- <xref:System.IO.StreamWriter>
- [<span data-ttu-id="b5006-129">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="b5006-129">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
