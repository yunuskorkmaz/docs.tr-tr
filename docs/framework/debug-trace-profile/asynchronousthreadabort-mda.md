---
title: asynchronousThreadAbort MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- asynchronous thread aborts
- AsynchronousThreadAbort MDA
- managed debugging assistants (MDAs), asynchronous thread aborts
- threading [.NET Framework], managed debugging assistants
- MDAs (managed debugging assistants), asynchronous thread aborts
ms.assetid: 9ebe40b2-d703-421e-8660-984acc42bfe0
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ecd99b098a619d4ad132432f4fd163d32598c2ba
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="asynchronousthreadabort-mda"></a><span data-ttu-id="01912-102">asynchronousThreadAbort MDA</span><span class="sxs-lookup"><span data-stu-id="01912-102">asynchronousThreadAbort MDA</span></span>
<span data-ttu-id="01912-103">`asynchronousThreadAbort` Yönetilen hata ayıklama Yardımcısı (MDA) başka bir iş parçacığı içinde zaman uyumsuz iptal tanıtmak bir iş parçacığı çalıştığında etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="01912-103">The `asynchronousThreadAbort` managed debugging assistant (MDA) is activated when a thread attempts to introduce an asynchronous abort into another thread.</span></span> <span data-ttu-id="01912-104">Zaman uyumlu iş parçacığı iptalleri değil etkinleştirme `asynchronousThreadAbort` MDA.</span><span class="sxs-lookup"><span data-stu-id="01912-104">Synchronous thread aborts do not activate the `asynchronousThreadAbort` MDA.</span></span>

## <a name="symptoms"></a><span data-ttu-id="01912-105">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="01912-105">Symptoms</span></span>
 <span data-ttu-id="01912-106">Bir uygulama işlenmeyen bir çöküyor <xref:System.Threading.ThreadAbortException> ana uygulama iş parçacığı durduruldu zaman.</span><span class="sxs-lookup"><span data-stu-id="01912-106">An application crashes with an unhandled <xref:System.Threading.ThreadAbortException> when the main application thread is aborted.</span></span> <span data-ttu-id="01912-107">Uygulamayı çalıştırmak devam etmek için olsaydı, sonuçları kilitlenen, büyük olasılıkla daha fazla veri bozulmasına neden olur uygulamadan daha zayıf olabilir.</span><span class="sxs-lookup"><span data-stu-id="01912-107">If the application were to continue to execute, the consequences might be worse than the application crashing, possibly resulting in further data corruption.</span></span>

 <span data-ttu-id="01912-108">Atomik olma amacını işlemleri uygulama verilerini öngörülemeyen durumda bırakarak kısmi tamamlandıktan sonra büyük olasılıkla kesilmiş.</span><span class="sxs-lookup"><span data-stu-id="01912-108">Operations meant to be atomic have likely been interrupted after partial completion, leaving application data in an unpredictable state.</span></span> <span data-ttu-id="01912-109">A <xref:System.Threading.ThreadAbortException> genellikle içinden bir özel durum beklenmiyor çıkabilecek yerlerde kod yürütmeyi rasgele gibi görünen noktalarından oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="01912-109">A <xref:System.Threading.ThreadAbortException> can be generated from seemingly random points in the execution of code, often in places from which an exception is not expected to arise.</span></span> <span data-ttu-id="01912-110">Kod bozuk durumda kaynaklanan böyle bir özel durum işleme yeteneği olan olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="01912-110">The code might not be capable of handling such an exception, resulting in a corrupt state.</span></span>

 <span data-ttu-id="01912-111">Belirtiler yaygın olarak sorun için devralınan rastgele nedeniyle değişebilir.</span><span class="sxs-lookup"><span data-stu-id="01912-111">Symptoms can vary widely due to the randomness inherent to the problem.</span></span>

## <a name="cause"></a><span data-ttu-id="01912-112">Sebep</span><span class="sxs-lookup"><span data-stu-id="01912-112">Cause</span></span>
 <span data-ttu-id="01912-113">Adlı tek bir iş parçacığı kodda <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> bir zaman uyumsuz iş parçacığı durdurma tanıtmak için bir hedef iş parçacığı üzerinde yöntemi.</span><span class="sxs-lookup"><span data-stu-id="01912-113">Code in one thread called the <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> method on a target thread to introduce an asynchronous thread abort.</span></span> <span data-ttu-id="01912-114">Çağrı yapar kodu iş parçacığı durdurma zaman uyumsuz olduğundan <xref:System.Threading.Thread.Abort%2A> iptal etme işlemi hedefinin daha farklı bir iş parçacığı üzerinde çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="01912-114">The thread abort is asynchronous because the code that makes the call to <xref:System.Threading.Thread.Abort%2A> is running on a different thread than the target of the abort operation.</span></span> <span data-ttu-id="01912-115">Zaman uyumlu iş parçacığı iptalleri neden olmaz bir sorun olduğundan iş parçacığı gerçekleştirme <xref:System.Threading.Thread.Abort%2A> uygulama durumu olduğu tutarlı yalnızca bir güvenli denetim noktası yapmış olmanız.</span><span class="sxs-lookup"><span data-stu-id="01912-115">Synchronous thread aborts should not cause a problem because the thread performing the <xref:System.Threading.Thread.Abort%2A> should have done so only at a safe checkpoint where application state is consistent.</span></span>

 <span data-ttu-id="01912-116">Hedef iş parçacığının yürütme öngörülemeyen noktalarında işlendiğinden zaman uyumsuz iş parçacığı iptalleri bir sorun var.</span><span class="sxs-lookup"><span data-stu-id="01912-116">Asynchronous thread aborts present a problem because they are processed at unpredictable points in the target thread's execution.</span></span> <span data-ttu-id="01912-117">Bunu önlemek için bu şekilde iptal bir iş parçacığı üzerinde çalıştırmak için yazılan kod işlemeye gerekir bir <xref:System.Threading.ThreadAbortException> uygulama verilerinin tutarlı bir duruma geri getirir dikkat ederek kodunun neredeyse her satırı.</span><span class="sxs-lookup"><span data-stu-id="01912-117">To avoid this, code written to run on a thread that might be aborted in this manner would need to handle a <xref:System.Threading.ThreadAbortException> at almost every line of code, taking care to put application data back into a consistent state.</span></span> <span data-ttu-id="01912-118">Kod bu sorunla aklınızda yazılacak veya tüm olası durumlarda karşı korur kod yazmaya beklediğiniz gerçekçi değildir.</span><span class="sxs-lookup"><span data-stu-id="01912-118">It is not realistic to expect code to be written with this problem in mind or to write code that protects against all possible circumstances.</span></span>

 <span data-ttu-id="01912-119">Yönetilmeyen kod çağrılarını ve `finally` blokları değil durdurulacak zaman uyumsuz olarak ancak hemen Bu kategorilerden birini Çıkışta.</span><span class="sxs-lookup"><span data-stu-id="01912-119">Calls into unmanaged code and `finally` blocks will not be aborted asynchronously but immediately upon exit from one of these categories.</span></span>

 <span data-ttu-id="01912-120">Neden sorunu devralınmış rastgele nedeniyle belirlemek zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="01912-120">The cause might be difficult to determine due to the randomness inherent to the problem.</span></span>

## <a name="resolution"></a><span data-ttu-id="01912-121">Çözüm</span><span class="sxs-lookup"><span data-stu-id="01912-121">Resolution</span></span>
 <span data-ttu-id="01912-122">Zaman uyumsuz iş parçacığı iptalleri kullanılmasını gerektiren kod tasarım kaçının.</span><span class="sxs-lookup"><span data-stu-id="01912-122">Avoid code design that requires the use of asynchronous thread aborts.</span></span> <span data-ttu-id="01912-123">Çeşitli yaklaşımlar Kesinti yapılan bir çağrı gerektirmeyen hedef iş parçacığı için daha uygun <xref:System.Threading.Thread.Abort%2A>.</span><span class="sxs-lookup"><span data-stu-id="01912-123">There are several approaches more appropriate for interruption of a target thread that do not require a call to <xref:System.Threading.Thread.Abort%2A>.</span></span> <span data-ttu-id="01912-124">Ortak bir özelliği gibi bir mekanizma tanıtmak için güvenli olduğundan, kesme istemek için hedef iş parçacığı işaret eder.</span><span class="sxs-lookup"><span data-stu-id="01912-124">The safest is to introduce a mechanism, such as a common property, that signals the target thread to request an interrupt.</span></span> <span data-ttu-id="01912-125">Hedef iş parçacığı güvenli belirli kontrol noktaları, sinyal denetler.</span><span class="sxs-lookup"><span data-stu-id="01912-125">The target thread checks the signal at certain safe checkpoints.</span></span> <span data-ttu-id="01912-126">Kesme istendi belirlerse, düzgün bir şekilde kapanabilir.</span><span class="sxs-lookup"><span data-stu-id="01912-126">If it notices that an interrupt has been requested, it can shut down gracefully.</span></span>

## <a name="effect-on-the-runtime"></a><span data-ttu-id="01912-127">Çalışma zamanı etkisi</span><span class="sxs-lookup"><span data-stu-id="01912-127">Effect on the Runtime</span></span>
 <span data-ttu-id="01912-128">Bu MDA CLR üzerinde etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="01912-128">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="01912-129">Yalnızca veri zaman uyumsuz iş parçacığı iptalleri hakkında raporlar.</span><span class="sxs-lookup"><span data-stu-id="01912-129">It only reports data about asynchronous thread aborts.</span></span>

## <a name="output"></a><span data-ttu-id="01912-130">Çıkış</span><span class="sxs-lookup"><span data-stu-id="01912-130">Output</span></span>
 <span data-ttu-id="01912-131">MDA durdurma ve durdurma hedefidir iş parçacığı kimliği gerçekleştiren iş parçacığı kimliği bildirir.</span><span class="sxs-lookup"><span data-stu-id="01912-131">The MDA reports the ID of the thread performing the abort and the ID of the thread that is the target of the abort.</span></span> <span data-ttu-id="01912-132">Bu zaman uyumsuz iptalleri sınırlı olduğundan bu asla aynı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="01912-132">These will never be the same because this is limited to asynchronous aborts.</span></span>

## <a name="configuration"></a><span data-ttu-id="01912-133">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="01912-133">Configuration</span></span>

```xml
<mdaConfig>
  <assistants>
    <asynchronousThreadAbort />
  </assistants>
</mdaConfig>
```

## <a name="example"></a><span data-ttu-id="01912-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="01912-134">Example</span></span>
 <span data-ttu-id="01912-135">Etkinleştirme `asynchronousThreadAbort` MDA gerektirir sadece bir çağrı <xref:System.Threading.Thread.Abort%2A> ayrı çalışan iş parçacığı üzerinde.</span><span class="sxs-lookup"><span data-stu-id="01912-135">Activating the `asynchronousThreadAbort` MDA requires only a call to <xref:System.Threading.Thread.Abort%2A> on a separate running thread.</span></span> <span data-ttu-id="01912-136">İş parçacığı içeriğini durdurma tarafından herhangi rastgele bir noktada kesilebilir daha karmaşık işlemleri kümesi olan işlevi başlatırsanız sonuçları göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="01912-136">Consider the consequences if the contents of the thread start function were a set of more complex operations which might be interrupted at any arbitrary point by the abort.</span></span>

```csharp
using System.Threading;
void FireMda()
{
    Thread t = new Thread(delegate() { Thread.Sleep(1000); });
    t.Start();
    // The following line activates the MDA.
    t.Abort();
    t.Join();
}
```

## <a name="see-also"></a><span data-ttu-id="01912-137">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="01912-137">See Also</span></span>
 <span data-ttu-id="01912-138"><xref:System.Threading.Thread>[Yönetilen hata ayıklama Yardımcıları ile hataları tanılama](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)</span><span class="sxs-lookup"><span data-stu-id="01912-138"><xref:System.Threading.Thread> [Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)</span></span>
