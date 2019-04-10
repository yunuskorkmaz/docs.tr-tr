---
title: dangerousThreadingAPI MDA
ms.date: 03/30/2017
helpviewer_keywords:
- suspending threads
- DangerousThreadingAPI MDA
- managed debugging assistants (MDAs), dangerous threading operations
- threading [.NET Framework], suspending
- MDAs (managed debugging assistants), dangerous threading operations
- Suspend method
- threading [.NET Framework], managed debugging assistants
ms.assetid: 3e5efbc5-92e4-4229-b31f-ce368a1adb96
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 46b0add67fc6bc139ef02e09190670870749d4c7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59218309"
---
# <a name="dangerousthreadingapi-mda"></a><span data-ttu-id="8bd5e-102">dangerousThreadingAPI MDA</span><span class="sxs-lookup"><span data-stu-id="8bd5e-102">dangerousThreadingAPI MDA</span></span>
<span data-ttu-id="8bd5e-103">`dangerousThreadingAPI` Yönetilen hata ayıklama Yardımcısı (MDA) etkinleştirilmiş olduğunda <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> geçerli iş parçacığı dışında bir iş parçacığında yöntemi çağrılır.</span><span class="sxs-lookup"><span data-stu-id="8bd5e-103">The `dangerousThreadingAPI` managed debugging assistant (MDA) is activated when the <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> method is called on a thread other than the current thread.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="8bd5e-104">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="8bd5e-104">Symptoms</span></span>  
 <span data-ttu-id="8bd5e-105">Uygulama yanıt vermiyor veya süresiz olarak askıda kalır.</span><span class="sxs-lookup"><span data-stu-id="8bd5e-105">An application is unresponsive or hangs indefinitely.</span></span> <span data-ttu-id="8bd5e-106">Sistem veya uygulama verileri, geçici veya bir uygulama bile kapatıldı sonra öngörülemeyen durumda kalmayabilir.</span><span class="sxs-lookup"><span data-stu-id="8bd5e-106">System or application data might be left in an unpredictable state temporarily or even after an application has been shut down.</span></span> <span data-ttu-id="8bd5e-107">Beklendiği gibi bazı işlemler Tamamlanıyor değil.</span><span class="sxs-lookup"><span data-stu-id="8bd5e-107">Some operations are not completing as expected.</span></span>  
  
 <span data-ttu-id="8bd5e-108">Belirtiler yaygın olarak sorun için devralınmış rastgeleliğinin nedeniyle değişebilir.</span><span class="sxs-lookup"><span data-stu-id="8bd5e-108">Symptoms can vary widely due to the randomness inherent to the problem.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="8bd5e-109">Sebep</span><span class="sxs-lookup"><span data-stu-id="8bd5e-109">Cause</span></span>  
 <span data-ttu-id="8bd5e-110">Bir iş parçacığı başka bir iş parçacığı kullanarak zaman uyumsuz olarak askıya <xref:System.Threading.Thread.Suspend%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="8bd5e-110">A thread is asynchronously suspended by another thread using the <xref:System.Threading.Thread.Suspend%2A> method.</span></span> <span data-ttu-id="8bd5e-111">Ortasında bir işlem olabilir. başka bir iş parçacığını askıya alma güvenli olduğunda belirlemek için hiçbir yolu yoktur.</span><span class="sxs-lookup"><span data-stu-id="8bd5e-111">There is no way to determine when it is safe to suspend another thread which might be in the middle of an operation.</span></span> <span data-ttu-id="8bd5e-112">İş parçacığını askıya alma, veri bozulması veya okuduğunuzda sonlandırılmasını neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="8bd5e-112">Suspending the thread can result in the corruption of data or the breaking of invariants.</span></span> <span data-ttu-id="8bd5e-113">Bir iş parçacığı bir askıya alınma durumuna ve hiçbir zaman sürdürüldü kullanarak yerleştirilmesi gereken <xref:System.Threading.Thread.Resume%2A> yöntemi, uygulama süresiz olarak askıda ve büyük olasılıkla uygulama verileri zarar verebilir.</span><span class="sxs-lookup"><span data-stu-id="8bd5e-113">Should a thread be placed into a suspended state and never resumed using the <xref:System.Threading.Thread.Resume%2A> method, the application can hang indefinitely and possibly damage application data.</span></span> <span data-ttu-id="8bd5e-114">Bu yöntemler eski olarak işaretlendi.</span><span class="sxs-lookup"><span data-stu-id="8bd5e-114">These methods have been marked as obsolete.</span></span>  
  
 <span data-ttu-id="8bd5e-115">Eşitleme temellerine hedef iş parçacığı tarafından tutulan, askıya alma sırasında tutulan kalırlar.</span><span class="sxs-lookup"><span data-stu-id="8bd5e-115">If synchronization primitives are held by the target thread, they remain held during suspension.</span></span> <span data-ttu-id="8bd5e-116">Bu başka bir iş parçacığı, örneğin iş parçacığı gerçekleştirmek için kilitlenmeleri açabilir <xref:System.Threading.Thread.Suspend%2A>, temel bir kilidi edinmeye çalışın.</span><span class="sxs-lookup"><span data-stu-id="8bd5e-116">This can lead to deadlocks should another thread, for example the thread performing the <xref:System.Threading.Thread.Suspend%2A>, attempt to acquire a lock on the primitive.</span></span> <span data-ttu-id="8bd5e-117">Bu durumda, sorunu Kilitlenme ortaya çıkmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8bd5e-117">In this situation, the problem manifests itself as a deadlock.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="8bd5e-118">Çözüm</span><span class="sxs-lookup"><span data-stu-id="8bd5e-118">Resolution</span></span>  
 <span data-ttu-id="8bd5e-119">Kullanımını zorunlu tasarımları önlemek <xref:System.Threading.Thread.Suspend%2A> ve <xref:System.Threading.Thread.Resume%2A>.</span><span class="sxs-lookup"><span data-stu-id="8bd5e-119">Avoid designs that require the use of <xref:System.Threading.Thread.Suspend%2A> and <xref:System.Threading.Thread.Resume%2A>.</span></span> <span data-ttu-id="8bd5e-120">İş parçacıkları arasında işbirliği için eşitleme temellerine gibi kullanın <xref:System.Threading.Monitor>, <xref:System.Threading.ReaderWriterLock>, <xref:System.Threading.Mutex>, veya C# `lock` deyimi.</span><span class="sxs-lookup"><span data-stu-id="8bd5e-120">For cooperation between threads, use synchronization primitives such as <xref:System.Threading.Monitor>, <xref:System.Threading.ReaderWriterLock>, <xref:System.Threading.Mutex>, or the C# `lock` statement.</span></span> <span data-ttu-id="8bd5e-121">Bu yöntemler kullanmanız gerekirse, zaman penceresi azaltın ve iş parçacığının askıya alınmış durumda olduğu sürece yürütür kod miktarını en aza indirir.</span><span class="sxs-lookup"><span data-stu-id="8bd5e-121">If you must use these methods, reduce the window of time and minimize the amount of code that executes while the thread is in a suspended state.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="8bd5e-122">Çalışma zamanı üzerindeki etkisi</span><span class="sxs-lookup"><span data-stu-id="8bd5e-122">Effect on the Runtime</span></span>  
 <span data-ttu-id="8bd5e-123">Bu mda'nın CLR üzerinde etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="8bd5e-123">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="8bd5e-124">Yalnızca veri tehlikeli iş parçacığı oluşturma işlemleri hakkında raporlar.</span><span class="sxs-lookup"><span data-stu-id="8bd5e-124">It only reports data about dangerous threading operations.</span></span>  
  
## <a name="output"></a><span data-ttu-id="8bd5e-125">Çıkış</span><span class="sxs-lookup"><span data-stu-id="8bd5e-125">Output</span></span>  
 <span data-ttu-id="8bd5e-126">MDA etkinleştirilmesi neden tehlikeli iş parçacığı yöntemi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="8bd5e-126">The MDA identifies the dangerous threading method that caused it to be activated.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="8bd5e-127">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="8bd5e-127">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dangerousThreadingAPI />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="8bd5e-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="8bd5e-128">Example</span></span>  
 <span data-ttu-id="8bd5e-129">Aşağıdaki kod örneği için bir çağrı gösterir <xref:System.Threading.Thread.Suspend%2A> etkinleştirilmesinden neden yöntemi `dangerousThreadingAPI`.</span><span class="sxs-lookup"><span data-stu-id="8bd5e-129">The following code example demonstrates a call to the <xref:System.Threading.Thread.Suspend%2A> method that causes the activation of the `dangerousThreadingAPI`.</span></span>  
  
```csharp
using System.Threading;  
void FireMda()  
{  
Thread t = new Thread(delegate() { Thread.Sleep(1000); });  
    t.Start();  
    // The following line activates the MDA.  
    t.Suspend();   
    t.Resume();  
    t.Join();  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="8bd5e-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8bd5e-130">See also</span></span>

- <xref:System.Threading.Thread>
- [<span data-ttu-id="8bd5e-131">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="8bd5e-131">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="8bd5e-132">lock Deyimi</span><span class="sxs-lookup"><span data-stu-id="8bd5e-132">lock Statement</span></span>](~/docs/csharp/language-reference/keywords/lock-statement.md)
