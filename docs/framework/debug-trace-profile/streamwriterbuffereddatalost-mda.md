---
title: streamWriterBufferedDataLost MDA
description: Bir StreamWriter bir dosyaya son 1 – 4 KB 'lık verileri yazmazsa etkinleştirebileceğiniz streamWriterBufferedDataLost yönetilen hata ayıklama Yardımcısı 'nı (MDA) gözden geçirin.
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
ms.openlocfilehash: 0c10ea6bb9dc0aaafa2ac1798696579af7592895
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803497"
---
# <a name="streamwriterbuffereddatalost-mda"></a><span data-ttu-id="b94b2-103">streamWriterBufferedDataLost MDA</span><span class="sxs-lookup"><span data-stu-id="b94b2-103">streamWriterBufferedDataLost MDA</span></span>
<span data-ttu-id="b94b2-104">`streamWriterBufferedDataLost`Yönetilen hata ayıklama Yardımcısı (MDA), <xref:System.IO.StreamWriter> öğesine yazıldığında etkinleştirilir, ancak <xref:System.IO.StreamWriter.Flush%2A> ya da <xref:System.IO.StreamWriter.Close%2A> yöntemi daha sonra örneği yok <xref:System.IO.StreamWriter> edildiğinde çağrılır.</span><span class="sxs-lookup"><span data-stu-id="b94b2-104">The `streamWriterBufferedDataLost` managed debugging assistant (MDA) is activated when a <xref:System.IO.StreamWriter> is written to, but the <xref:System.IO.StreamWriter.Flush%2A> or <xref:System.IO.StreamWriter.Close%2A> method is not subsequently called before the instance of the <xref:System.IO.StreamWriter> is destroyed.</span></span> <span data-ttu-id="b94b2-105">Bu MDA etkin olduğunda, çalışma zamanı, arabelleğe alınmış verilerin hala içinde varolup olmadığını belirler <xref:System.IO.StreamWriter> .</span><span class="sxs-lookup"><span data-stu-id="b94b2-105">When this MDA is enabled, the runtime determines whether any buffered data still exists within the <xref:System.IO.StreamWriter>.</span></span> <span data-ttu-id="b94b2-106">Arabelleğe alınan veriler varsa, MDA etkin olur.</span><span class="sxs-lookup"><span data-stu-id="b94b2-106">If buffered data does exist, the MDA is activated.</span></span> <span data-ttu-id="b94b2-107"><xref:System.GC.Collect%2A>Ve yöntemlerini çağırmak, <xref:System.GC.WaitForPendingFinalizers%2A> sonlandırıcıları çalıştırmaya zorlayabilir.</span><span class="sxs-lookup"><span data-stu-id="b94b2-107">Calling the <xref:System.GC.Collect%2A> and <xref:System.GC.WaitForPendingFinalizers%2A> methods can force finalizers to run.</span></span> <span data-ttu-id="b94b2-108">Sonlandırıcılar, normalde Rastgele zamanlarda çalışır ve muhtemelen işlemden çıkılmaz.</span><span class="sxs-lookup"><span data-stu-id="b94b2-108">Finalizers will otherwise run at seemingly arbitrary times, and possibly not at all on process exit.</span></span> <span data-ttu-id="b94b2-109">Bu MDA etkin olan sonlandırıcıları açıkça çalıştırmak, bu tür bir sorunu daha güvenilir bir şekilde yeniden oluşturmaya yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="b94b2-109">Explicitly running finalizers with this MDA enabled will help to more reliably reproduce this type of problem.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="b94b2-110">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="b94b2-110">Symptoms</span></span>  
 <span data-ttu-id="b94b2-111">A bir <xref:System.IO.StreamWriter> dosyaya son 1 – 4 KB veri yazmaz.</span><span class="sxs-lookup"><span data-stu-id="b94b2-111">A <xref:System.IO.StreamWriter> does not write the last 1–4 KB of data to a file.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="b94b2-112">Nedeni</span><span class="sxs-lookup"><span data-stu-id="b94b2-112">Cause</span></span>  
 <span data-ttu-id="b94b2-113"><xref:System.IO.StreamWriter>Verileri dahili olarak arabelleğe alır. Bu, <xref:System.IO.StreamWriter.Close%2A> ya da <xref:System.IO.StreamWriter.Flush%2A> yönteminin, arabelleğe alınan verileri temeldeki veri deposuna yazmak üzere çağrılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="b94b2-113">The <xref:System.IO.StreamWriter> buffers data internally, which requires that the <xref:System.IO.StreamWriter.Close%2A> or <xref:System.IO.StreamWriter.Flush%2A> method be called to write the buffered data to the underlying data store.</span></span> <span data-ttu-id="b94b2-114"><xref:System.IO.StreamWriter.Close%2A>Ya da <xref:System.IO.StreamWriter.Flush%2A> uygun bir şekilde çağrılmamışsa, örnekte ara belleğe alınan veriler <xref:System.IO.StreamWriter> beklenen şekilde yazılmayabilir.</span><span class="sxs-lookup"><span data-stu-id="b94b2-114">If <xref:System.IO.StreamWriter.Close%2A> or <xref:System.IO.StreamWriter.Flush%2A> is not appropriately called, data buffered in the <xref:System.IO.StreamWriter> instance might not be written as expected.</span></span>  
  
 <span data-ttu-id="b94b2-115">Aşağıda, bu MDA 'ın yakalandığı kötü yazılmış kodun bir örneği verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="b94b2-115">The following is an example of poorly written code that this MDA should catch.</span></span>  
  
```csharp  
// Poorly written code.  
void Write()
{  
    StreamWriter sw = new StreamWriter("file.txt");  
    sw.WriteLine("Data");  
    // Problem: forgot to close the StreamWriter.  
}  
```  
  
 <span data-ttu-id="b94b2-116">Önceki kod, bir atık toplama tetikleniyorsa ve sonlandırıcılar bitene kadar askıya alınırsa bu MDA 'ı daha güvenilir bir şekilde etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="b94b2-116">The preceding code will activate this MDA more reliably if a garbage collection is triggered and then suspended until finalizers have finished.</span></span> <span data-ttu-id="b94b2-117">Bu tür bir sorunu izlemek için aşağıdaki kodu bir hata ayıklama derlemesinde önceki metodun sonuna ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b94b2-117">To track down this type of problem, you can add the following code to the end of the preceding method in a debug build.</span></span> <span data-ttu-id="b94b2-118">Bu, MDA ' yi güvenilir bir şekilde etkinleştirmeye yardımcı olur, ancak elbette sorunun nedenini düzelmez.</span><span class="sxs-lookup"><span data-stu-id="b94b2-118">This will help to reliably activate the MDA, but of course it does not fix the cause of the problem.</span></span>  
  
```csharp
GC.Collect();  
GC.WaitForPendingFinalizers();  
```  
  
## <a name="resolution"></a><span data-ttu-id="b94b2-119">Çözüm</span><span class="sxs-lookup"><span data-stu-id="b94b2-119">Resolution</span></span>  
 <span data-ttu-id="b94b2-120"><xref:System.IO.StreamWriter.Close%2A> <xref:System.IO.StreamWriter.Flush%2A> <xref:System.IO.StreamWriter> Bir uygulamayı veya bir örneğine sahip herhangi bir kod bloğunu kapatmadan önce veya ' de ' i çağırdığınızdan emin olun <xref:System.IO.StreamWriter> .</span><span class="sxs-lookup"><span data-stu-id="b94b2-120">Make sure you call <xref:System.IO.StreamWriter.Close%2A> or <xref:System.IO.StreamWriter.Flush%2A> on the <xref:System.IO.StreamWriter> before closing an application or any code block that has an instance of a <xref:System.IO.StreamWriter>.</span></span> <span data-ttu-id="b94b2-121">Bunu elde etmek için en iyi mekanizmalardan biri, örneğin, `using` `Using` <xref:System.IO.StreamWriter.Dispose%2A> Yazıcı yönteminin çağrılmasını ve örneğin doğru şekilde kapatılmasını sağlamak için bir C# bloğu (Visual Basic) ile örneği oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="b94b2-121">One of the best mechanisms for achieving this is creating the instance with a C# `using` block (`Using` in Visual Basic), which will ensure the <xref:System.IO.StreamWriter.Dispose%2A> method for the writer is invoked, resulting in the instance being correctly closed.</span></span>  
  
```csharp
using(StreamWriter sw = new StreamWriter("file.txt"))
{  
    sw.WriteLine("Data");  
}  
```  
  
 <span data-ttu-id="b94b2-122">Aşağıdaki kod, yerine kullanılarak aynı çözümü gösterir `try/finally` `using` .</span><span class="sxs-lookup"><span data-stu-id="b94b2-122">The following code shows the same solution, using `try/finally` instead of `using`.</span></span>  
  
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
  
 <span data-ttu-id="b94b2-123">Bu çözümlerin hiçbiri kullanılabilir değilse (örneğin, bir <xref:System.IO.StreamWriter> statik değişkende depolanıyorsa ve yaşam süresinin sonunda kodu kolayca çalıştıramazsınız), <xref:System.IO.StreamWriter.Flush%2A> <xref:System.IO.StreamWriter> son kullanımı bittikten sonra veya <xref:System.IO.StreamWriter.AutoFlush%2A> özelliği `true` ilk kullanılmadan önce olarak ayarlamak için bu sorundan kaçının.</span><span class="sxs-lookup"><span data-stu-id="b94b2-123">If neither of these solutions can be used (for example, if a <xref:System.IO.StreamWriter> is stored in a static variable and you cannot easily run code at the end of its lifetime), then calling <xref:System.IO.StreamWriter.Flush%2A> on the <xref:System.IO.StreamWriter> after its last use or setting the <xref:System.IO.StreamWriter.AutoFlush%2A> property to `true` before its first use should avoid this problem.</span></span>  
  
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
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="b94b2-124">Çalışma zamanında etki</span><span class="sxs-lookup"><span data-stu-id="b94b2-124">Effect on the Runtime</span></span>  
 <span data-ttu-id="b94b2-125">Bu MDA çalışma zamanı üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="b94b2-125">This MDA has no effect on the runtime.</span></span>  
  
## <a name="output"></a><span data-ttu-id="b94b2-126">Çıktı</span><span class="sxs-lookup"><span data-stu-id="b94b2-126">Output</span></span>  
 <span data-ttu-id="b94b2-127">Bu ihlalin oluştuğunu belirten bir ileti.</span><span class="sxs-lookup"><span data-stu-id="b94b2-127">A message indicating that this violation occurred.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="b94b2-128">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="b94b2-128">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <streamWriterBufferedDataLost />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b94b2-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b94b2-129">See also</span></span>

- <xref:System.IO.StreamWriter>
- [<span data-ttu-id="b94b2-130">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="b94b2-130">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
