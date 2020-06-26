---
title: dangerousThreadingAPI MDA
description: Geçerli iş parçacığından farklı bir iş parçacığında Thread. Suspend çağrıldığında etkinleştirilen dangerousThreadingAPI Managed hata ayıklama Yardımcısı 'nı (MDA) gözden geçirin.
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
ms.openlocfilehash: 9069ccb6f106c83db94f88bc464bc0888d28586c
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85416011"
---
# <a name="dangerousthreadingapi-mda"></a><span data-ttu-id="dee14-103">dangerousThreadingAPI MDA</span><span class="sxs-lookup"><span data-stu-id="dee14-103">dangerousThreadingAPI MDA</span></span>
<span data-ttu-id="dee14-104">`dangerousThreadingAPI`Yönetilen hata ayıklama Yardımcısı (MDA), <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> yöntem geçerli iş parçacığı dışında bir iş parçacığında çağrıldığında etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="dee14-104">The `dangerousThreadingAPI` managed debugging assistant (MDA) is activated when the <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> method is called on a thread other than the current thread.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="dee14-105">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="dee14-105">Symptoms</span></span>  
 <span data-ttu-id="dee14-106">Bir uygulama süresiz olarak yanıt vermemeye başlıyor veya askıda kalıyor.</span><span class="sxs-lookup"><span data-stu-id="dee14-106">An application is unresponsive or hangs indefinitely.</span></span> <span data-ttu-id="dee14-107">Sistem veya uygulama verileri, geçici olarak veya bir uygulama kapatıldıktan sonra bile öngörülemeyen bir durumda kalabilir.</span><span class="sxs-lookup"><span data-stu-id="dee14-107">System or application data might be left in an unpredictable state temporarily or even after an application has been shut down.</span></span> <span data-ttu-id="dee14-108">Bazı işlemler beklendiği gibi tamamlanmıyor.</span><span class="sxs-lookup"><span data-stu-id="dee14-108">Some operations are not completing as expected.</span></span>  
  
 <span data-ttu-id="dee14-109">Belirtiler, soruna bağlı rasgelelik nedeniyle büyük ölçüde farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="dee14-109">Symptoms can vary widely due to the randomness inherent to the problem.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="dee14-110">Nedeni</span><span class="sxs-lookup"><span data-stu-id="dee14-110">Cause</span></span>  
 <span data-ttu-id="dee14-111">İş parçacığı, yöntemi kullanılarak başka bir iş parçacığı tarafından zaman uyumsuz olarak askıya alındı <xref:System.Threading.Thread.Suspend%2A> .</span><span class="sxs-lookup"><span data-stu-id="dee14-111">A thread is asynchronously suspended by another thread using the <xref:System.Threading.Thread.Suspend%2A> method.</span></span> <span data-ttu-id="dee14-112">Bir işlemin ortasında olabilecek başka bir iş parçacığını askıya almanın ne zaman güvenli olduğunu belirlemenin bir yolu yoktur.</span><span class="sxs-lookup"><span data-stu-id="dee14-112">There is no way to determine when it is safe to suspend another thread which might be in the middle of an operation.</span></span> <span data-ttu-id="dee14-113">İş parçacığını askıya almak, verilerin bozulmasına veya ınvarıant 'ların bozulmasına yol açabilir.</span><span class="sxs-lookup"><span data-stu-id="dee14-113">Suspending the thread can result in the corruption of data or the breaking of invariants.</span></span> <span data-ttu-id="dee14-114">Bir iş parçacığının askıya alınma durumuna yerleştirilmesi ve yöntemi kullanılarak hiçbir şekilde sürdürülmemesi <xref:System.Threading.Thread.Resume%2A> , uygulamanın süresiz olarak askıda kalması ve muhtemelen uygulama verilerine zarar verebiliyor olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="dee14-114">Should a thread be placed into a suspended state and never resumed using the <xref:System.Threading.Thread.Resume%2A> method, the application can hang indefinitely and possibly damage application data.</span></span> <span data-ttu-id="dee14-115">Bu yöntemler artık kullanılmıyor olarak işaretlendi.</span><span class="sxs-lookup"><span data-stu-id="dee14-115">These methods have been marked as obsolete.</span></span>  
  
 <span data-ttu-id="dee14-116">Eşitleme temelleri hedef iş parçacığı tarafından tutuluyorsa, askıya alma sırasında tutuluyor olarak kalırlar.</span><span class="sxs-lookup"><span data-stu-id="dee14-116">If synchronization primitives are held by the target thread, they remain held during suspension.</span></span> <span data-ttu-id="dee14-117">Bu, kilitlenmeyle ilgili başka bir iş parçacığı olmalıdır, örneğin iş parçacığı, <xref:System.Threading.Thread.Suspend%2A> temel üzerinde bir kilit elde etmeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="dee14-117">This can lead to deadlocks should another thread, for example the thread performing the <xref:System.Threading.Thread.Suspend%2A>, attempt to acquire a lock on the primitive.</span></span> <span data-ttu-id="dee14-118">Bu durumda, sorun kendi kendine bir kilitlenme olarak bildirim gösterir.</span><span class="sxs-lookup"><span data-stu-id="dee14-118">In this situation, the problem manifests itself as a deadlock.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="dee14-119">Çözüm</span><span class="sxs-lookup"><span data-stu-id="dee14-119">Resolution</span></span>  
 <span data-ttu-id="dee14-120">Ve kullanımını gerektiren tasarımlardan kaçının <xref:System.Threading.Thread.Suspend%2A> <xref:System.Threading.Thread.Resume%2A> .</span><span class="sxs-lookup"><span data-stu-id="dee14-120">Avoid designs that require the use of <xref:System.Threading.Thread.Suspend%2A> and <xref:System.Threading.Thread.Resume%2A>.</span></span> <span data-ttu-id="dee14-121">İş parçacıkları arasındaki ortak işlem için,,, <xref:System.Threading.Monitor> <xref:System.Threading.ReaderWriterLock> <xref:System.Threading.Mutex> veya C# deyimleri gibi eşitleme temel öğelerini kullanın `lock` .</span><span class="sxs-lookup"><span data-stu-id="dee14-121">For cooperation between threads, use synchronization primitives such as <xref:System.Threading.Monitor>, <xref:System.Threading.ReaderWriterLock>, <xref:System.Threading.Mutex>, or the C# `lock` statement.</span></span> <span data-ttu-id="dee14-122">Bu yöntemleri kullanmanız gerekiyorsa, zaman penceresini küçültün ve iş parçacığı askıya alınma durumundayken yürütülen kod miktarını en aza indirin.</span><span class="sxs-lookup"><span data-stu-id="dee14-122">If you must use these methods, reduce the window of time and minimize the amount of code that executes while the thread is in a suspended state.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="dee14-123">Çalışma zamanında etki</span><span class="sxs-lookup"><span data-stu-id="dee14-123">Effect on the Runtime</span></span>  
 <span data-ttu-id="dee14-124">Bu MDA, CLR üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="dee14-124">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="dee14-125">Yalnızca tehlikeli iş parçacığı oluşturma işlemleriyle ilgili verileri raporlar.</span><span class="sxs-lookup"><span data-stu-id="dee14-125">It only reports data about dangerous threading operations.</span></span>  
  
## <a name="output"></a><span data-ttu-id="dee14-126">Çıktı</span><span class="sxs-lookup"><span data-stu-id="dee14-126">Output</span></span>  
 <span data-ttu-id="dee14-127">MDA, etkinleştirilmesinin nedeni olan tehlikeli iş parçacığı yöntemini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="dee14-127">The MDA identifies the dangerous threading method that caused it to be activated.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="dee14-128">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="dee14-128">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dangerousThreadingAPI />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="dee14-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="dee14-129">Example</span></span>  
 <span data-ttu-id="dee14-130">Aşağıdaki kod örneği <xref:System.Threading.Thread.Suspend%2A> , etkinleştirmesine neden olan yöntemine yapılan çağrıyı gösterir `dangerousThreadingAPI` .</span><span class="sxs-lookup"><span data-stu-id="dee14-130">The following code example demonstrates a call to the <xref:System.Threading.Thread.Suspend%2A> method that causes the activation of the `dangerousThreadingAPI`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="dee14-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dee14-131">See also</span></span>

- <xref:System.Threading.Thread>
- [<span data-ttu-id="dee14-132">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="dee14-132">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="dee14-133">lock Deyimi</span><span class="sxs-lookup"><span data-stu-id="dee14-133">lock Statement</span></span>](../../csharp/language-reference/keywords/lock-statement.md)
