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
ms.openlocfilehash: e20502cfd64e7e4e40bee0b815729e914c3dd4a2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54553717"
---
# <a name="streamwriterbuffereddatalost-mda"></a><span data-ttu-id="4fda3-102">streamWriterBufferedDataLost MDA</span><span class="sxs-lookup"><span data-stu-id="4fda3-102">streamWriterBufferedDataLost MDA</span></span>
<span data-ttu-id="4fda3-103">`streamWriterBufferedDataLost` Yönetilen hata ayıklama Yardımcısı (MDA) etkinleştirilmiş olduğunda bir <xref:System.IO.StreamWriter> için yazılmış ancak <xref:System.IO.StreamWriter.Flush%2A> veya <xref:System.IO.StreamWriter.Close%2A> yöntemi örneği önce sonradan çağrılmaz <xref:System.IO.StreamWriter> yok.</span><span class="sxs-lookup"><span data-stu-id="4fda3-103">The `streamWriterBufferedDataLost` managed debugging assistant (MDA) is activated when a <xref:System.IO.StreamWriter> is written to, but the <xref:System.IO.StreamWriter.Flush%2A> or <xref:System.IO.StreamWriter.Close%2A> method is not subsequently called before the instance of the <xref:System.IO.StreamWriter> is destroyed.</span></span> <span data-ttu-id="4fda3-104">Bu MDA etkinleştirildiğinde, çalışma zamanı arabelleğe alınan tüm veriler hala içinde var olup olmadığını belirler <xref:System.IO.StreamWriter>.</span><span class="sxs-lookup"><span data-stu-id="4fda3-104">When this MDA is enabled, the runtime determines whether any buffered data still exists within the <xref:System.IO.StreamWriter>.</span></span> <span data-ttu-id="4fda3-105">Arabelleğe alınan verileri varsa, bu MDA etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="4fda3-105">If buffered data does exist, the MDA is activated.</span></span> <span data-ttu-id="4fda3-106">Çağırma <xref:System.GC.Collect%2A> ve <xref:System.GC.WaitForPendingFinalizers%2A> yöntemleri sonlandırıcılar çalıştırmaya zorlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4fda3-106">Calling the <xref:System.GC.Collect%2A> and <xref:System.GC.WaitForPendingFinalizers%2A> methods can force finalizers to run.</span></span> <span data-ttu-id="4fda3-107">Sonlandırıcılar, aksi halde görünüşte rastgele zamanlarda ve muhtemelen hiçbir işlem çıkışı üzerinde çalışacaktır.</span><span class="sxs-lookup"><span data-stu-id="4fda3-107">Finalizers will otherwise run at seemingly arbitrary times, and possibly not at all on process exit.</span></span> <span data-ttu-id="4fda3-108">Sonlandırıcılar etkin bu MDA ile açıkça çalışan daha güvenilir bir şekilde bu tür bir sorunu yeniden oluşturmak için yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="4fda3-108">Explicitly running finalizers with this MDA enabled will help to more reliably reproduce this type of problem.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="4fda3-109">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="4fda3-109">Symptoms</span></span>  
 <span data-ttu-id="4fda3-110">A <xref:System.IO.StreamWriter> son 1 ila 4 KB veri bir dosyaya yazmaz.</span><span class="sxs-lookup"><span data-stu-id="4fda3-110">A <xref:System.IO.StreamWriter> does not write the last 1–4 KB of data to a file.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="4fda3-111">Sebep</span><span class="sxs-lookup"><span data-stu-id="4fda3-111">Cause</span></span>  
 <span data-ttu-id="4fda3-112"><xref:System.IO.StreamWriter> Dahili olarak veri arabelleği, gerektiren <xref:System.IO.StreamWriter.Close%2A> veya <xref:System.IO.StreamWriter.Flush%2A> yöntemi arabelleğe alınan verileri temel alınan veri deposuna yazacak şekilde çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="4fda3-112">The <xref:System.IO.StreamWriter> buffers data internally, which requires that the <xref:System.IO.StreamWriter.Close%2A> or <xref:System.IO.StreamWriter.Flush%2A> method be called to write the buffered data to the underlying data store.</span></span> <span data-ttu-id="4fda3-113">Varsa <xref:System.IO.StreamWriter.Close%2A> veya <xref:System.IO.StreamWriter.Flush%2A> uygun şekilde çağrılmaz; içinde arabelleğe alınan verileri <xref:System.IO.StreamWriter> örneği, değil beklenen şekilde yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="4fda3-113">If <xref:System.IO.StreamWriter.Close%2A> or <xref:System.IO.StreamWriter.Flush%2A> is not appropriately called, data buffered in the <xref:System.IO.StreamWriter> instance might not be written as expected.</span></span>  
  
 <span data-ttu-id="4fda3-114">Bu mda'nın yakalamalısınız kötü yazılmış koduna ilişkin bir örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="4fda3-114">The following is an example of poorly written code that this MDA should catch.</span></span>  
  
```csharp  
// Poorly written code.  
void Write()   
{  
    StreamWriter sw = new StreamWriter("file.txt");  
    sw.WriteLine("Data");  
    // Problem: forgot to close the StreamWriter.  
}  
```  
  
 <span data-ttu-id="4fda3-115">Bir çöp toplama tetikleyen ve ardından sonlandırıcılar tamamlanana kadar askıya önceki kod bu mda'nın daha güvenilir bir şekilde etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="4fda3-115">The preceding code will activate this MDA more reliably if a garbage collection is triggered and then suspended until finalizers have finished.</span></span> <span data-ttu-id="4fda3-116">Bu tür bir sorun izlemek için hata ayıklama derlemesinde önceki yönteminin sonuna aşağıdaki kodu ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4fda3-116">To track down this type of problem, you can add the following code to the end of the preceding method in a debug build.</span></span> <span data-ttu-id="4fda3-117">Bu MDA güvenilir bir şekilde etkinleştirmeye yardımcı olur, ancak Elbette sorunun nedenini düzeltmez.</span><span class="sxs-lookup"><span data-stu-id="4fda3-117">This will help to reliably activate the MDA, but of course it does not fix the cause of the problem.</span></span>  
  
```csharp
GC.Collect();  
GC.WaitForPendingFinalizers();  
```  
  
## <a name="resolution"></a><span data-ttu-id="4fda3-118">Çözüm</span><span class="sxs-lookup"><span data-stu-id="4fda3-118">Resolution</span></span>  
 <span data-ttu-id="4fda3-119">Çağırmanızı emin <xref:System.IO.StreamWriter.Close%2A> veya <xref:System.IO.StreamWriter.Flush%2A> üzerinde <xref:System.IO.StreamWriter> bir uygulama ya da bir örneği olduğu herhangi bir kod bloğuna kapatmadan önce bir <xref:System.IO.StreamWriter>.</span><span class="sxs-lookup"><span data-stu-id="4fda3-119">Make sure you call <xref:System.IO.StreamWriter.Close%2A> or <xref:System.IO.StreamWriter.Flush%2A> on the <xref:System.IO.StreamWriter> before closing an application or any code block that has an instance of a <xref:System.IO.StreamWriter>.</span></span> <span data-ttu-id="4fda3-120">Örneğiyle oluşturduğundan bu ulaşmak için en iyi mekanizmalardan biri bir C# `using` blok (`Using` Visual Basic'te), hangi emin olmanızı <xref:System.IO.StreamWriter.Dispose%2A> yazıcı için yöntemi çağrılır, doğru şekilde kapatıldığından kuşkulanılıyor örneğinde sonuç.</span><span class="sxs-lookup"><span data-stu-id="4fda3-120">One of the best mechanisms for achieving this is creating the instance with a C# `using` block (`Using` in Visual Basic), which will ensure the <xref:System.IO.StreamWriter.Dispose%2A> method for the writer is invoked, resulting in the instance being correctly closed.</span></span>  
  
```csharp
using(StreamWriter sw = new StreamWriter("file.txt"))   
{  
    sw.WriteLine("Data");  
}  
```  
  
 <span data-ttu-id="4fda3-121">Aşağıdaki kod aynı çözüm gösterir kullanarak `try/finally` yerine `using`.</span><span class="sxs-lookup"><span data-stu-id="4fda3-121">The following code shows the same solution, using `try/finally` instead of `using`.</span></span>  
  
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
  
 <span data-ttu-id="4fda3-122">Bu çözümlerin hiçbiri kullanılamaması durumunda (örneğin, bir <xref:System.IO.StreamWriter> statik içinde depolanan değişkeni ve kolayca çalıştırılamaz kod ömrü sona), ardından arama <xref:System.IO.StreamWriter.Flush%2A> üzerinde <xref:System.IO.StreamWriter> son kullanın ya da ayarı <xref:System.IO.StreamWriter.AutoFlush%2A> özelliğini `true` önce bu sorunun ilk kullanımını kaçınmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="4fda3-122">If neither of these solutions can be used (for example, if a <xref:System.IO.StreamWriter> is stored in a static variable and you cannot easily run code at the end of its lifetime), then calling <xref:System.IO.StreamWriter.Flush%2A> on the <xref:System.IO.StreamWriter> after its last use or setting the <xref:System.IO.StreamWriter.AutoFlush%2A> property to `true` before its first use should avoid this problem.</span></span>  
  
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
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="4fda3-123">Çalışma zamanı üzerindeki etkisi</span><span class="sxs-lookup"><span data-stu-id="4fda3-123">Effect on the Runtime</span></span>  
 <span data-ttu-id="4fda3-124">Bu mda'nın çalışma zamanı üzerinde etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="4fda3-124">This MDA has no effect on the runtime.</span></span>  
  
## <a name="output"></a><span data-ttu-id="4fda3-125">Çıkış</span><span class="sxs-lookup"><span data-stu-id="4fda3-125">Output</span></span>  
 <span data-ttu-id="4fda3-126">Bu ihlali oluştuğunu belirten bir ileti.</span><span class="sxs-lookup"><span data-stu-id="4fda3-126">A message indicating that this violation occurred.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="4fda3-127">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="4fda3-127">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <streamWriterBufferedDataLost />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4fda3-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4fda3-128">See also</span></span>
- <xref:System.IO.StreamWriter>
- [<span data-ttu-id="4fda3-129">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="4fda3-129">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
