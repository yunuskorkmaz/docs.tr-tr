---
title: asynchronousThreadAbort MDA
ms.date: 03/30/2017
helpviewer_keywords:
- asynchronous thread aborts
- AsynchronousThreadAbort MDA
- managed debugging assistants (MDAs), asynchronous thread aborts
- threading [.NET Framework], managed debugging assistants
- MDAs (managed debugging assistants), asynchronous thread aborts
ms.assetid: 9ebe40b2-d703-421e-8660-984acc42bfe0
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 08f67ad363d0bd3efcc7a1eeedd1f48d3bae9407
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59114903"
---
# <a name="asynchronousthreadabort-mda"></a><span data-ttu-id="a3ca9-102">asynchronousThreadAbort MDA</span><span class="sxs-lookup"><span data-stu-id="a3ca9-102">asynchronousThreadAbort MDA</span></span>
<span data-ttu-id="a3ca9-103">`asynchronousThreadAbort` Yönetilen hata ayıklama Yardımcısı (MDA), başka bir diziye bir zaman uyumsuz iptal tanıtmak bir iş parçacığı girişiminde bulunduğunda etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="a3ca9-103">The `asynchronousThreadAbort` managed debugging assistant (MDA) is activated when a thread attempts to introduce an asynchronous abort into another thread.</span></span> <span data-ttu-id="a3ca9-104">Zaman uyumlu iş parçacığı iptalleri değil etkinleştirme `asynchronousThreadAbort` MDA.</span><span class="sxs-lookup"><span data-stu-id="a3ca9-104">Synchronous thread aborts do not activate the `asynchronousThreadAbort` MDA.</span></span>

## <a name="symptoms"></a><span data-ttu-id="a3ca9-105">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="a3ca9-105">Symptoms</span></span>
 <span data-ttu-id="a3ca9-106">İşlenmemiş bir uygulama kilitlenmeleri <xref:System.Threading.ThreadAbortException> zaman ana uygulama iş parçacığı durduruldu.</span><span class="sxs-lookup"><span data-stu-id="a3ca9-106">An application crashes with an unhandled <xref:System.Threading.ThreadAbortException> when the main application thread is aborted.</span></span> <span data-ttu-id="a3ca9-107">Yürütmeye devam etmek için uygulamayı olsaydı, sonuçları kilitlenen, büyük olasılıkla daha fazla veri bozulmasına neden olur uygulamadan daha kötü olabilir.</span><span class="sxs-lookup"><span data-stu-id="a3ca9-107">If the application were to continue to execute, the consequences might be worse than the application crashing, possibly resulting in further data corruption.</span></span>

 <span data-ttu-id="a3ca9-108">İşlemler atomik olacak şekilde tasarlanmış uygulama verileri öngörülemeyen durumda bırakarak kısmi tamamlandıktan sonra büyük olasılıkla kesilmiş.</span><span class="sxs-lookup"><span data-stu-id="a3ca9-108">Operations meant to be atomic have likely been interrupted after partial completion, leaving application data in an unpredictable state.</span></span> <span data-ttu-id="a3ca9-109">A <xref:System.Threading.ThreadAbortException> genellikle içinden bir özel durum beklenmiyor çıkabilecek yerlerde kod yürütülmesi görünüşte rastgele noktalarından oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="a3ca9-109">A <xref:System.Threading.ThreadAbortException> can be generated from seemingly random points in the execution of code, often in places from which an exception is not expected to arise.</span></span> <span data-ttu-id="a3ca9-110">Kod, bozuk bir durumda kaynaklanan böyle bir özel durum işleme kapasitesine sahip olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="a3ca9-110">The code might not be capable of handling such an exception, resulting in a corrupt state.</span></span>

 <span data-ttu-id="a3ca9-111">Belirtiler yaygın olarak sorun için devralınmış rastgeleliğinin nedeniyle değişebilir.</span><span class="sxs-lookup"><span data-stu-id="a3ca9-111">Symptoms can vary widely due to the randomness inherent to the problem.</span></span>

## <a name="cause"></a><span data-ttu-id="a3ca9-112">Sebep</span><span class="sxs-lookup"><span data-stu-id="a3ca9-112">Cause</span></span>
 <span data-ttu-id="a3ca9-113">Kod olarak adlandırılan bir iş parçacığındaki <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> yöntemi bir iş parçacığında zaman uyumsuz iş parçacığı iptal tanıtmak için hedef.</span><span class="sxs-lookup"><span data-stu-id="a3ca9-113">Code in one thread called the <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> method on a target thread to introduce an asynchronous thread abort.</span></span> <span data-ttu-id="a3ca9-114">Kod, çağrı yapar çünkü iş parçacığı iptal zaman uyumsuz <xref:System.Threading.Thread.Abort%2A> durdurma işleminin hedefi değerinden farklı bir iş parçacığı üzerinde çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="a3ca9-114">The thread abort is asynchronous because the code that makes the call to <xref:System.Threading.Thread.Abort%2A> is running on a different thread than the target of the abort operation.</span></span> <span data-ttu-id="a3ca9-115">Zaman uyumlu iş parçacığı iptalleri neden bir sorun nedeniyle iş parçacığı gerçekleştirme <xref:System.Threading.Thread.Abort%2A> burada uygulama durumunu tutarlı olduğundan yalnızca bir güvenli denetim noktası yapmış olmanız.</span><span class="sxs-lookup"><span data-stu-id="a3ca9-115">Synchronous thread aborts should not cause a problem because the thread performing the <xref:System.Threading.Thread.Abort%2A> should have done so only at a safe checkpoint where application state is consistent.</span></span>

 <span data-ttu-id="a3ca9-116">Hedef iş parçacığının yürütme öngörülemeyen noktalarında işlendiğinden zaman uyumsuz iş parçacığı iptalleri bir sorun var.</span><span class="sxs-lookup"><span data-stu-id="a3ca9-116">Asynchronous thread aborts present a problem because they are processed at unpredictable points in the target thread's execution.</span></span> <span data-ttu-id="a3ca9-117">Bunu önlemek için bu şekilde iptal bir iş parçacığı üzerinde çalışacak şekilde yazılmış kod işlemeye gerekir bir <xref:System.Threading.ThreadAbortException> uygulama verilerinin tutarlı bir duruma geri put dikkat ederek kodun neredeyse her satırı.</span><span class="sxs-lookup"><span data-stu-id="a3ca9-117">To avoid this, code written to run on a thread that might be aborted in this manner would need to handle a <xref:System.Threading.ThreadAbortException> at almost every line of code, taking care to put application data back into a consistent state.</span></span> <span data-ttu-id="a3ca9-118">Bu sorunla aklınızda yazılacak veya tüm olası koşullar karşı koruyan kod yazmak için kod beklenir gerçekçi değildir.</span><span class="sxs-lookup"><span data-stu-id="a3ca9-118">It is not realistic to expect code to be written with this problem in mind or to write code that protects against all possible circumstances.</span></span>

 <span data-ttu-id="a3ca9-119">Yönetilmeyen kodu çağırıyor ve `finally` blokları değil durdurulacak zaman uyumsuz olarak ancak hemen kategorilerine birinden Çıkışta.</span><span class="sxs-lookup"><span data-stu-id="a3ca9-119">Calls into unmanaged code and `finally` blocks will not be aborted asynchronously but immediately upon exit from one of these categories.</span></span>

 <span data-ttu-id="a3ca9-120">Nedeni sorunu devralınan rastgeleliğinin nedeniyle saptamak zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="a3ca9-120">The cause might be difficult to determine due to the randomness inherent to the problem.</span></span>

## <a name="resolution"></a><span data-ttu-id="a3ca9-121">Çözüm</span><span class="sxs-lookup"><span data-stu-id="a3ca9-121">Resolution</span></span>
 <span data-ttu-id="a3ca9-122">Zaman uyumsuz iş parçacığı iptalleri kullanılmasını gerektiren tasarım kodu özen gösterin.</span><span class="sxs-lookup"><span data-stu-id="a3ca9-122">Avoid code design that requires the use of asynchronous thread aborts.</span></span> <span data-ttu-id="a3ca9-123">Çeşitli yaklaşımlar daha uygun bir çağrı gerektirmeyen hedef iş parçacığı kesintinin <xref:System.Threading.Thread.Abort%2A>.</span><span class="sxs-lookup"><span data-stu-id="a3ca9-123">There are several approaches more appropriate for interruption of a target thread that do not require a call to <xref:System.Threading.Thread.Abort%2A>.</span></span> <span data-ttu-id="a3ca9-124">Ortak bir özellik gibi bir mekanizma tanıtmak için en güvenli olanıdır, hedef iş parçacığının isteği bir kesme sinyalini verir.</span><span class="sxs-lookup"><span data-stu-id="a3ca9-124">The safest is to introduce a mechanism, such as a common property, that signals the target thread to request an interrupt.</span></span> <span data-ttu-id="a3ca9-125">Hedef iş parçacığı güvenli belirli kontrol noktaları, sinyal denetler.</span><span class="sxs-lookup"><span data-stu-id="a3ca9-125">The target thread checks the signal at certain safe checkpoints.</span></span> <span data-ttu-id="a3ca9-126">Bir kesme istendi karşılaşırsa, düzgün bir şekilde kapanabilir.</span><span class="sxs-lookup"><span data-stu-id="a3ca9-126">If it notices that an interrupt has been requested, it can shut down gracefully.</span></span>

## <a name="effect-on-the-runtime"></a><span data-ttu-id="a3ca9-127">Çalışma zamanı üzerindeki etkisi</span><span class="sxs-lookup"><span data-stu-id="a3ca9-127">Effect on the Runtime</span></span>
 <span data-ttu-id="a3ca9-128">Bu mda'nın CLR üzerinde etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="a3ca9-128">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="a3ca9-129">Yalnızca veri zaman uyumsuz iş parçacığı iptalleri hakkında raporlar.</span><span class="sxs-lookup"><span data-stu-id="a3ca9-129">It only reports data about asynchronous thread aborts.</span></span>

## <a name="output"></a><span data-ttu-id="a3ca9-130">Çıkış</span><span class="sxs-lookup"><span data-stu-id="a3ca9-130">Output</span></span>
 <span data-ttu-id="a3ca9-131">MDA durdurma ve iptal işleminin hedefi olan iş parçacığının kimliği gerçekleştiren iş parçacığının kimliği bildirir.</span><span class="sxs-lookup"><span data-stu-id="a3ca9-131">The MDA reports the ID of the thread performing the abort and the ID of the thread that is the target of the abort.</span></span> <span data-ttu-id="a3ca9-132">Bu zaman uyumsuz iptali için sınırlı olduğundan bunlar hiçbir zaman aynı olmaz.</span><span class="sxs-lookup"><span data-stu-id="a3ca9-132">These will never be the same because this is limited to asynchronous aborts.</span></span>

## <a name="configuration"></a><span data-ttu-id="a3ca9-133">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="a3ca9-133">Configuration</span></span>

```xml
<mdaConfig>
  <assistants>
    <asynchronousThreadAbort />
  </assistants>
</mdaConfig>
```

## <a name="example"></a><span data-ttu-id="a3ca9-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="a3ca9-134">Example</span></span>
 <span data-ttu-id="a3ca9-135">Etkinleştirme `asynchronousThreadAbort` MDA, yalnızca bir çağrı gerektirir <xref:System.Threading.Thread.Abort%2A> ayrı bir çalışan iş parçacığı üzerinde.</span><span class="sxs-lookup"><span data-stu-id="a3ca9-135">Activating the `asynchronousThreadAbort` MDA requires only a call to <xref:System.Threading.Thread.Abort%2A> on a separate running thread.</span></span> <span data-ttu-id="a3ca9-136">Rastgele herhangi bir noktada iptal tarafından yarıda kesilebilir daha karmaşık işlemleri bir dizi olan işlevi iş parçacığının içeriği başlatırsanız, sonuçları göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="a3ca9-136">Consider the consequences if the contents of the thread start function were a set of more complex operations which might be interrupted at any arbitrary point by the abort.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="a3ca9-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a3ca9-137">See also</span></span>

- <xref:System.Threading.Thread>
- [<span data-ttu-id="a3ca9-138">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="a3ca9-138">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
