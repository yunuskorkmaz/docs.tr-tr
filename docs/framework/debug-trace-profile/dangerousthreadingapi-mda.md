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
ms.openlocfilehash: d3fe7d11657c2f9edd1fea7ff639f878f993d6b1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174777"
---
# <a name="dangerousthreadingapi-mda"></a><span data-ttu-id="f2e02-102">dangerousThreadingAPI MDA</span><span class="sxs-lookup"><span data-stu-id="f2e02-102">dangerousThreadingAPI MDA</span></span>
<span data-ttu-id="f2e02-103">Yönetilen `dangerousThreadingAPI` hata ayıklama yardımcısı (MDA) <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> yöntem geçerli iş parçacığı dışında bir iş parçacığı çağrıldığında etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="f2e02-103">The `dangerousThreadingAPI` managed debugging assistant (MDA) is activated when the <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> method is called on a thread other than the current thread.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="f2e02-104">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="f2e02-104">Symptoms</span></span>  
 <span data-ttu-id="f2e02-105">Bir uygulama yanıt vermiyor veya süresiz olarak asılı.</span><span class="sxs-lookup"><span data-stu-id="f2e02-105">An application is unresponsive or hangs indefinitely.</span></span> <span data-ttu-id="f2e02-106">Sistem veya uygulama verileri geçici olarak veya bir uygulama kapatıldıktan sonra bile öngörülemeyen bir durumda bırakılabilir.</span><span class="sxs-lookup"><span data-stu-id="f2e02-106">System or application data might be left in an unpredictable state temporarily or even after an application has been shut down.</span></span> <span data-ttu-id="f2e02-107">Bazı işlemler beklendiği gibi tamamlanınmıyor.</span><span class="sxs-lookup"><span data-stu-id="f2e02-107">Some operations are not completing as expected.</span></span>  
  
 <span data-ttu-id="f2e02-108">Belirtiler büyük ölçüde soruna bağlı rasgelelik nedeniyle değişebilir.</span><span class="sxs-lookup"><span data-stu-id="f2e02-108">Symptoms can vary widely due to the randomness inherent to the problem.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="f2e02-109">Nedeni</span><span class="sxs-lookup"><span data-stu-id="f2e02-109">Cause</span></span>  
 <span data-ttu-id="f2e02-110">Bir iş <xref:System.Threading.Thread.Suspend%2A> parçacığı, yöntemi kullanarak başka bir iş parçacığı tarafından eş senkronize olarak askıya alınır.</span><span class="sxs-lookup"><span data-stu-id="f2e02-110">A thread is asynchronously suspended by another thread using the <xref:System.Threading.Thread.Suspend%2A> method.</span></span> <span data-ttu-id="f2e02-111">Bir işlemin ortasında olabilecek başka bir iş parçacığının ne zaman askıya alınabileceğini belirlemenin bir yolu yoktur.</span><span class="sxs-lookup"><span data-stu-id="f2e02-111">There is no way to determine when it is safe to suspend another thread which might be in the middle of an operation.</span></span> <span data-ttu-id="f2e02-112">İş parçacığının askıya alınması, verilerin bozulmasına veya değişmezlerin kırılması ile sonuçlanabilir.</span><span class="sxs-lookup"><span data-stu-id="f2e02-112">Suspending the thread can result in the corruption of data or the breaking of invariants.</span></span> <span data-ttu-id="f2e02-113">Bir iş parçacığı askıya alınmış bir duruma yerleştirilir <xref:System.Threading.Thread.Resume%2A> ve yöntemi kullanarak devam asla, uygulama süresiz olarak asmak ve büyük olasılıkla uygulama verilerine zarar verebilir.</span><span class="sxs-lookup"><span data-stu-id="f2e02-113">Should a thread be placed into a suspended state and never resumed using the <xref:System.Threading.Thread.Resume%2A> method, the application can hang indefinitely and possibly damage application data.</span></span> <span data-ttu-id="f2e02-114">Bu yöntemler eski olarak işaretlenmiştir.</span><span class="sxs-lookup"><span data-stu-id="f2e02-114">These methods have been marked as obsolete.</span></span>  
  
 <span data-ttu-id="f2e02-115">Senkronizasyon ilkel hedef iş parçacığı tarafından tutulursa, onlar süspansiyon sırasında tutulur.</span><span class="sxs-lookup"><span data-stu-id="f2e02-115">If synchronization primitives are held by the target thread, they remain held during suspension.</span></span> <span data-ttu-id="f2e02-116">Bu kilitlenmelere yol açabilir başka bir iş <xref:System.Threading.Thread.Suspend%2A>parçacığı, örneğin iş parçacığı gerçekleştiren , ilkel bir kilit elde etmek için girişimi.</span><span class="sxs-lookup"><span data-stu-id="f2e02-116">This can lead to deadlocks should another thread, for example the thread performing the <xref:System.Threading.Thread.Suspend%2A>, attempt to acquire a lock on the primitive.</span></span> <span data-ttu-id="f2e02-117">Bu durumda, sorun bir kilitlenme olarak kendini gösterir.</span><span class="sxs-lookup"><span data-stu-id="f2e02-117">In this situation, the problem manifests itself as a deadlock.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="f2e02-118">Çözüm</span><span class="sxs-lookup"><span data-stu-id="f2e02-118">Resolution</span></span>  
 <span data-ttu-id="f2e02-119">Kullanımı <xref:System.Threading.Thread.Suspend%2A> ve gerektiren tasarımlar <xref:System.Threading.Thread.Resume%2A>kaçının.</span><span class="sxs-lookup"><span data-stu-id="f2e02-119">Avoid designs that require the use of <xref:System.Threading.Thread.Suspend%2A> and <xref:System.Threading.Thread.Resume%2A>.</span></span> <span data-ttu-id="f2e02-120">İş parçacıkları arasındaki işbirliği için, " , <xref:System.Threading.Monitor> <xref:System.Threading.ReaderWriterLock>, <xref:System.Threading.Mutex>, veya `lock` C# deyimi gibi senkronizasyon ilkellerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="f2e02-120">For cooperation between threads, use synchronization primitives such as <xref:System.Threading.Monitor>, <xref:System.Threading.ReaderWriterLock>, <xref:System.Threading.Mutex>, or the C# `lock` statement.</span></span> <span data-ttu-id="f2e02-121">Bu yöntemleri kullanmanız gerekiyorsa, zaman penceresini azaltın ve iş parçacığı askıya alınmış durumdayken çalıştıran kod miktarını en aza indirin.</span><span class="sxs-lookup"><span data-stu-id="f2e02-121">If you must use these methods, reduce the window of time and minimize the amount of code that executes while the thread is in a suspended state.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="f2e02-122">Çalışma Süresi üzerindeki etkisi</span><span class="sxs-lookup"><span data-stu-id="f2e02-122">Effect on the Runtime</span></span>  
 <span data-ttu-id="f2e02-123">Bu MDA'nın CLR üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="f2e02-123">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="f2e02-124">Yalnızca tehlikeli iş parçacığı işlemleriyle ilgili verileri bildirir.</span><span class="sxs-lookup"><span data-stu-id="f2e02-124">It only reports data about dangerous threading operations.</span></span>  
  
## <a name="output"></a><span data-ttu-id="f2e02-125">Çıktı</span><span class="sxs-lookup"><span data-stu-id="f2e02-125">Output</span></span>  
 <span data-ttu-id="f2e02-126">MDA, etkinleştirilmesine neden olan tehlikeli iş parçacığı yöntemini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f2e02-126">The MDA identifies the dangerous threading method that caused it to be activated.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="f2e02-127">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="f2e02-127">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dangerousThreadingAPI />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="f2e02-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="f2e02-128">Example</span></span>  
 <span data-ttu-id="f2e02-129">Aşağıdaki kod örneği, <xref:System.Threading.Thread.Suspend%2A> `dangerousThreadingAPI`.'ın etkinleştirilmesine neden olan yönteme yapılan bir çağrıyı gösterir.</span><span class="sxs-lookup"><span data-stu-id="f2e02-129">The following code example demonstrates a call to the <xref:System.Threading.Thread.Suspend%2A> method that causes the activation of the `dangerousThreadingAPI`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f2e02-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f2e02-130">See also</span></span>

- <xref:System.Threading.Thread>
- [<span data-ttu-id="f2e02-131">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="f2e02-131">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="f2e02-132">lock Deyimi</span><span class="sxs-lookup"><span data-stu-id="f2e02-132">lock Statement</span></span>](../../csharp/language-reference/keywords/lock-statement.md)
