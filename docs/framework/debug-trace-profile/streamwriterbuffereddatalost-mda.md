---
title: streamWriterBufferedDataLost MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- StreamWriter class, data buffering problems
- managed debugging assistants (MDAs), StreamWriter data buffering
- buffers, StreamWriter problems
- MDAs (managed debugging assistants), StreamWriter data buffering
- StreamWriter buffered data lost
- data buffering problems
- streamWriterBufferedDataLost MDA
ms.assetid: 6e5c07be-bc5b-437a-8398-8779e23126ab
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: fa6b64d37052c40dbef83a25b622e415f6946c1e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="streamwriterbuffereddatalost-mda"></a><span data-ttu-id="2cbe5-102">streamWriterBufferedDataLost MDA</span><span class="sxs-lookup"><span data-stu-id="2cbe5-102">streamWriterBufferedDataLost MDA</span></span>
<span data-ttu-id="2cbe5-103">`streamWriterBufferedDataLost` Yönetilen hata ayıklama Yardımcısı (MDA) etkinleştirilmiş olduğunda bir <xref:System.IO.StreamWriter> için yazılmış ancak <xref:System.IO.StreamWriter.Flush%2A> veya <xref:System.IO.StreamWriter.Close%2A> yöntemi sonradan çağrılmaz örneğini önce <xref:System.IO.StreamWriter> yok.</span><span class="sxs-lookup"><span data-stu-id="2cbe5-103">The `streamWriterBufferedDataLost` managed debugging assistant (MDA) is activated when a <xref:System.IO.StreamWriter> is written to, but the <xref:System.IO.StreamWriter.Flush%2A> or <xref:System.IO.StreamWriter.Close%2A> method is not subsequently called before the instance of the <xref:System.IO.StreamWriter> is destroyed.</span></span> <span data-ttu-id="2cbe5-104">Bu MDA etkinleştirildiğinde, çalışma zamanı herhangi bir arabelleğe alınan veri hala içinde var olup olmadığının <xref:System.IO.StreamWriter>.</span><span class="sxs-lookup"><span data-stu-id="2cbe5-104">When this MDA is enabled, the runtime determines whether any buffered data still exists within the <xref:System.IO.StreamWriter>.</span></span> <span data-ttu-id="2cbe5-105">Arabelleğe alınan verileri mevcut değilse MDA etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="2cbe5-105">If buffered data does exist, the MDA is activated.</span></span> <span data-ttu-id="2cbe5-106">Çağırma <xref:System.GC.Collect%2A> ve <xref:System.GC.WaitForPendingFinalizers%2A> yöntemleri çalıştırmak için sonlandırıcılar zorlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2cbe5-106">Calling the <xref:System.GC.Collect%2A> and <xref:System.GC.WaitForPendingFinalizers%2A> methods can force finalizers to run.</span></span> <span data-ttu-id="2cbe5-107">Sonlandırıcılar, aksi halde görünen rasgele zamanlarda ve büyük olasılıkla hiç işlem Çıkışta çalışacaktır.</span><span class="sxs-lookup"><span data-stu-id="2cbe5-107">Finalizers will otherwise run at seemingly arbitrary times, and possibly not at all on process exit.</span></span> <span data-ttu-id="2cbe5-108">Açıkça sonlandırıcılar etkin bu MDA ile çalışan bu tür sorunlar daha güvenilir bir şekilde oluşturmaya yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="2cbe5-108">Explicitly running finalizers with this MDA enabled will help to more reliably reproduce this type of problem.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="2cbe5-109">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="2cbe5-109">Symptoms</span></span>  
 <span data-ttu-id="2cbe5-110">A <xref:System.IO.StreamWriter> son 1 – 4 KB'lık verinin bir dosyaya yazmaz.</span><span class="sxs-lookup"><span data-stu-id="2cbe5-110">A <xref:System.IO.StreamWriter> does not write the last 1–4 KB of data to a file.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="2cbe5-111">Sebep</span><span class="sxs-lookup"><span data-stu-id="2cbe5-111">Cause</span></span>  
 <span data-ttu-id="2cbe5-112"><xref:System.IO.StreamWriter> Dahili olarak, veri arabelleği, gerektiren <xref:System.IO.StreamWriter.Close%2A> veya <xref:System.IO.StreamWriter.Flush%2A> yöntemi, temel alınan veri deposuna arabelleğe alınan veri yazmak için çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="2cbe5-112">The <xref:System.IO.StreamWriter> buffers data internally, which requires that the <xref:System.IO.StreamWriter.Close%2A> or <xref:System.IO.StreamWriter.Flush%2A> method be called to write the buffered data to the underlying data store.</span></span> <span data-ttu-id="2cbe5-113">Varsa <xref:System.IO.StreamWriter.Close%2A> veya <xref:System.IO.StreamWriter.Flush%2A> uygun şekilde çağrılmaz, içinde arabelleğe alınan verileri <xref:System.IO.StreamWriter> örneği değil yazılmaya beklendiği gibi.</span><span class="sxs-lookup"><span data-stu-id="2cbe5-113">If <xref:System.IO.StreamWriter.Close%2A> or <xref:System.IO.StreamWriter.Flush%2A> is not appropriately called, data buffered in the <xref:System.IO.StreamWriter> instance might not be written as expected.</span></span>  
  
 <span data-ttu-id="2cbe5-114">Bu MDA catch kötü yazılmış kodun bir örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="2cbe5-114">The following is an example of poorly written code that this MDA should catch.</span></span>  
  
```csharp  
// Poorly written code.  
void Write()   
{  
    StreamWriter sw = new StreamWriter("file.txt");  
    sw.WriteLine("Data");  
    // Problem: forgot to close the StreamWriter.  
}  
```  
  
 <span data-ttu-id="2cbe5-115">Çöp toplama tetiklenen ve sonlandırıcılar bitinceye kadar sonra askıya önceki kod bu MDA daha güvenilir bir şekilde etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="2cbe5-115">The preceding code will activate this MDA more reliably if a garbage collection is triggered and then suspended until finalizers have finished.</span></span> <span data-ttu-id="2cbe5-116">Bu tür sorunlar izlemek için hata ayıklama derlemesi içinde önceki yönteminin sonuna aşağıdaki kod ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2cbe5-116">To track down this type of problem, you can add the following code to the end of the preceding method in a debug build.</span></span> <span data-ttu-id="2cbe5-117">Bu, güvenilir bir şekilde MDA etkinleştirmek için yardımcı olur, ancak Elbette sorunun nedenini gideremiyor.</span><span class="sxs-lookup"><span data-stu-id="2cbe5-117">This will help to reliably activate the MDA, but of course it does not fix the cause of the problem.</span></span>  
  
```csharp
GC.Collect();  
GC.WaitForPendingFinalizers();  
```  
  
## <a name="resolution"></a><span data-ttu-id="2cbe5-118">Çözüm</span><span class="sxs-lookup"><span data-stu-id="2cbe5-118">Resolution</span></span>  
 <span data-ttu-id="2cbe5-119">Çağırmanız emin olun <xref:System.IO.StreamWriter.Close%2A> veya <xref:System.IO.StreamWriter.Flush%2A> üzerinde <xref:System.IO.StreamWriter> bir uygulama veya bir örneğine sahip herhangi bir kod bloğuna kapatmadan önce bir <xref:System.IO.StreamWriter>.</span><span class="sxs-lookup"><span data-stu-id="2cbe5-119">Make sure you call <xref:System.IO.StreamWriter.Close%2A> or <xref:System.IO.StreamWriter.Flush%2A> on the <xref:System.IO.StreamWriter> before closing an application or any code block that has an instance of a <xref:System.IO.StreamWriter>.</span></span> <span data-ttu-id="2cbe5-120">Bunu elde etmek için en iyi mekanizmalardan biri oluştururken örnek bir C# ile `using` blok (`Using` Visual Basic'te), emin olun <xref:System.IO.StreamWriter.Dispose%2A> yazıcı için yöntem çağrıldığında, doğru kapatılan örneğinde kaynaklanan.</span><span class="sxs-lookup"><span data-stu-id="2cbe5-120">One of the best mechanisms for achieving this is creating the instance with a C# `using` block (`Using` in Visual Basic), which will ensure the <xref:System.IO.StreamWriter.Dispose%2A> method for the writer is invoked, resulting in the instance being correctly closed.</span></span>  
  
```csharp
using(StreamWriter sw = new StreamWriter("file.txt"))   
{  
    sw.WriteLine("Data");  
}  
```  
  
 <span data-ttu-id="2cbe5-121">Aşağıdaki kod aynı çözüm gösterir kullanarak `try/finally` yerine `using`.</span><span class="sxs-lookup"><span data-stu-id="2cbe5-121">The following code shows the same solution, using `try/finally` instead of `using`.</span></span>  
  
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
  
 <span data-ttu-id="2cbe5-122">Bu çözümlerin hiçbiri kullanılıp kullanılamayacağını (örneğin, bir <xref:System.IO.StreamWriter> statik içinde depolanan değişken ve kolayca çalıştıramaz kodu çalışma süresi sonunda), ardından çağırma <xref:System.IO.StreamWriter.Flush%2A> üzerinde <xref:System.IO.StreamWriter> son kullanın veya ayar sonra <xref:System.IO.StreamWriter.AutoFlush%2A> özelliğine `true` önce ilk kullanımı bu sorunu kaçınmalısınız.</span><span class="sxs-lookup"><span data-stu-id="2cbe5-122">If neither of these solutions can be used (for example, if a <xref:System.IO.StreamWriter> is stored in a static variable and you cannot easily run code at the end of its lifetime), then calling <xref:System.IO.StreamWriter.Flush%2A> on the <xref:System.IO.StreamWriter> after its last use or setting the <xref:System.IO.StreamWriter.AutoFlush%2A> property to `true` before its first use should avoid this problem.</span></span>  
  
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
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="2cbe5-123">Çalışma zamanı etkisi</span><span class="sxs-lookup"><span data-stu-id="2cbe5-123">Effect on the Runtime</span></span>  
 <span data-ttu-id="2cbe5-124">Bu MDA çalışma zamanı üzerinde etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="2cbe5-124">This MDA has no effect on the runtime.</span></span>  
  
## <a name="output"></a><span data-ttu-id="2cbe5-125">Çıkış</span><span class="sxs-lookup"><span data-stu-id="2cbe5-125">Output</span></span>  
 <span data-ttu-id="2cbe5-126">Bu ihlali oluştuğunu belirten bir ileti.</span><span class="sxs-lookup"><span data-stu-id="2cbe5-126">A message indicating that this violation occurred.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="2cbe5-127">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="2cbe5-127">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <streamWriterBufferedDataLost />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2cbe5-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2cbe5-128">See Also</span></span>  
 <xref:System.IO.StreamWriter>  
 [<span data-ttu-id="2cbe5-129">Yönetilen hata ayıklama Yardımcıları ile hataları tanılama</span><span class="sxs-lookup"><span data-stu-id="2cbe5-129">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
