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
ms.openlocfilehash: 9bde6f6e625476712c5af516491ab9dd29b7dea3
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052955"
---
# <a name="asynchronousthreadabort-mda"></a><span data-ttu-id="4fe3b-102">asynchronousThreadAbort MDA</span><span class="sxs-lookup"><span data-stu-id="4fe3b-102">asynchronousThreadAbort MDA</span></span>
<span data-ttu-id="4fe3b-103">Yönetilen `asynchronousThreadAbort` hata ayıklama Yardımcısı (MDA), bir iş parçacığı başka bir iş parçacığına zaman uyumsuz bir iptal uygulamayı denediğinde etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="4fe3b-103">The `asynchronousThreadAbort` managed debugging assistant (MDA) is activated when a thread attempts to introduce an asynchronous abort into another thread.</span></span> <span data-ttu-id="4fe3b-104">Zaman uyumlu iş parçacığı durdurulduğunda `asynchronousThreadAbort` MDA 'ı etkinleştirmeyin.</span><span class="sxs-lookup"><span data-stu-id="4fe3b-104">Synchronous thread aborts do not activate the `asynchronousThreadAbort` MDA.</span></span>

## <a name="symptoms"></a><span data-ttu-id="4fe3b-105">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="4fe3b-105">Symptoms</span></span>
 <span data-ttu-id="4fe3b-106">Ana uygulama iş parçacığı iptal edildiğinde <xref:System.Threading.ThreadAbortException> , bir uygulama işlenmemiş ile çöküyor.</span><span class="sxs-lookup"><span data-stu-id="4fe3b-106">An application crashes with an unhandled <xref:System.Threading.ThreadAbortException> when the main application thread is aborted.</span></span> <span data-ttu-id="4fe3b-107">Uygulamanın yürütülmeye devam etmesi gerekiyorsa, sonuçlar uygulama kilitlenmesinin ardından büyük olasılıkla daha fazla veri bozulmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="4fe3b-107">If the application were to continue to execute, the consequences might be worse than the application crashing, possibly resulting in further data corruption.</span></span>

 <span data-ttu-id="4fe3b-108">Atomik olması amaçlanan işlemler kısmen tamamlandığında kesintiye uğratıldıktan sonra, uygulama verileri öngörülemeyen bir durumda bırakılır.</span><span class="sxs-lookup"><span data-stu-id="4fe3b-108">Operations meant to be atomic have likely been interrupted after partial completion, leaving application data in an unpredictable state.</span></span> <span data-ttu-id="4fe3b-109">Bir <xref:System.Threading.ThreadAbortException> özel durumun meydana gelmesi beklenmediği yerlerde, kod yürütmesindeki düzensiz rastgele noktalarda oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="4fe3b-109">A <xref:System.Threading.ThreadAbortException> can be generated from seemingly random points in the execution of code, often in places from which an exception is not expected to arise.</span></span> <span data-ttu-id="4fe3b-110">Kod böyle bir özel durumu işleyemeyebilir, bu durum bozuk bir duruma neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="4fe3b-110">The code might not be capable of handling such an exception, resulting in a corrupt state.</span></span>

 <span data-ttu-id="4fe3b-111">Belirtiler, soruna bağlı rasgelelik nedeniyle büyük ölçüde farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="4fe3b-111">Symptoms can vary widely due to the randomness inherent to the problem.</span></span>

## <a name="cause"></a><span data-ttu-id="4fe3b-112">Sebep</span><span class="sxs-lookup"><span data-stu-id="4fe3b-112">Cause</span></span>
 <span data-ttu-id="4fe3b-113">Bir iş parçacığındaki kod, <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> zaman uyumsuz bir iş parçacığı iptali tanıtmak için bir hedef iş parçacığında yöntemi olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="4fe3b-113">Code in one thread called the <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> method on a target thread to introduce an asynchronous thread abort.</span></span> <span data-ttu-id="4fe3b-114">Çağrıyı <xref:System.Threading.Thread.Abort%2A> yapan kod, durdurma işleminin hedefinden farklı bir iş parçacığında çalıştığından, iş parçacığı iptali zaman uyumsuzdur.</span><span class="sxs-lookup"><span data-stu-id="4fe3b-114">The thread abort is asynchronous because the code that makes the call to <xref:System.Threading.Thread.Abort%2A> is running on a different thread than the target of the abort operation.</span></span> <span data-ttu-id="4fe3b-115">İşlemi gerçekleştiren iş parçacığının yalnızca uygulama durumunun tutarlı olduğu güvenli bir denetim noktasında <xref:System.Threading.Thread.Abort%2A> yapılması gerektiğinden, zaman uyumlu iş parçacığı iptal noktaları soruna neden olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="4fe3b-115">Synchronous thread aborts should not cause a problem because the thread performing the <xref:System.Threading.Thread.Abort%2A> should have done so only at a safe checkpoint where application state is consistent.</span></span>

 <span data-ttu-id="4fe3b-116">Zaman uyumsuz thread, hedef iş parçacığının yürütmesindeki öngörülemeyen noktalarda işlendiği için bir sorun oluştu.</span><span class="sxs-lookup"><span data-stu-id="4fe3b-116">Asynchronous thread aborts present a problem because they are processed at unpredictable points in the target thread's execution.</span></span> <span data-ttu-id="4fe3b-117">Bu durumdan kaçınmak için, bu şekilde durdurulmuş olabilecek bir iş parçacığında çalışmak üzere yazılan kodun, neredeyse her bir <xref:System.Threading.ThreadAbortException> kod satırında işlenmesi ve uygulama verilerinin tutarlı bir duruma geri alınmasına dikkat etmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="4fe3b-117">To avoid this, code written to run on a thread that might be aborted in this manner would need to handle a <xref:System.Threading.ThreadAbortException> at almost every line of code, taking care to put application data back into a consistent state.</span></span> <span data-ttu-id="4fe3b-118">Kodun bu sorun ile yazılması veya tüm olası koşullara karşı koruyan bir kod yazmak için gerçekçi değildir.</span><span class="sxs-lookup"><span data-stu-id="4fe3b-118">It is not realistic to expect code to be written with this problem in mind or to write code that protects against all possible circumstances.</span></span>

 <span data-ttu-id="4fe3b-119">Yönetilmeyen kod ve `finally` bloklara yapılan çağrılar zaman uyumsuz olarak iptal edilmez, ancak bu kategorilerden birinden çıkış yapıldığında hemen silinir.</span><span class="sxs-lookup"><span data-stu-id="4fe3b-119">Calls into unmanaged code and `finally` blocks will not be aborted asynchronously but immediately upon exit from one of these categories.</span></span>

 <span data-ttu-id="4fe3b-120">Sorunun, soruna bağlı rastgele bir durum nedeniyle belirlenmesi zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="4fe3b-120">The cause might be difficult to determine due to the randomness inherent to the problem.</span></span>

## <a name="resolution"></a><span data-ttu-id="4fe3b-121">Çözüm</span><span class="sxs-lookup"><span data-stu-id="4fe3b-121">Resolution</span></span>
 <span data-ttu-id="4fe3b-122">Zaman uyumsuz iş parçacığı iptal durumu kullanımını gerektiren kod tasarımını önleyin.</span><span class="sxs-lookup"><span data-stu-id="4fe3b-122">Avoid code design that requires the use of asynchronous thread aborts.</span></span> <span data-ttu-id="4fe3b-123">Çağrısı gerektirmeyen bir hedef iş parçacığının kesintiye uğraması için çok sayıda yaklaşım daha uygundur <xref:System.Threading.Thread.Abort%2A>.</span><span class="sxs-lookup"><span data-stu-id="4fe3b-123">There are several approaches more appropriate for interruption of a target thread that do not require a call to <xref:System.Threading.Thread.Abort%2A>.</span></span> <span data-ttu-id="4fe3b-124">En güvenli, bir kesme istemek için hedef iş parçacığına işaret eden ortak bir özellik gibi bir mekanizma tanıtmaktır.</span><span class="sxs-lookup"><span data-stu-id="4fe3b-124">The safest is to introduce a mechanism, such as a common property, that signals the target thread to request an interrupt.</span></span> <span data-ttu-id="4fe3b-125">Hedef iş parçacığı belirli güvenli denetim noktalarında sinyali denetler.</span><span class="sxs-lookup"><span data-stu-id="4fe3b-125">The target thread checks the signal at certain safe checkpoints.</span></span> <span data-ttu-id="4fe3b-126">Bir kesmenin istenmiş olduğunu fark ederseniz, düzgün bir şekilde kapatılabilir.</span><span class="sxs-lookup"><span data-stu-id="4fe3b-126">If it notices that an interrupt has been requested, it can shut down gracefully.</span></span>

## <a name="effect-on-the-runtime"></a><span data-ttu-id="4fe3b-127">Çalışma zamanında etki</span><span class="sxs-lookup"><span data-stu-id="4fe3b-127">Effect on the Runtime</span></span>
 <span data-ttu-id="4fe3b-128">Bu MDA, CLR üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="4fe3b-128">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="4fe3b-129">Yalnızca zaman uyumsuz iş parçacığı iptal eden verileri raporlar.</span><span class="sxs-lookup"><span data-stu-id="4fe3b-129">It only reports data about asynchronous thread aborts.</span></span>

## <a name="output"></a><span data-ttu-id="4fe3b-130">Çıkış</span><span class="sxs-lookup"><span data-stu-id="4fe3b-130">Output</span></span>
 <span data-ttu-id="4fe3b-131">MDA, Abort işlemini gerçekleştiren iş parçacığının KIMLIĞINI ve iptal 'in hedefi olan iş parçacığının KIMLIĞINI bildirir.</span><span class="sxs-lookup"><span data-stu-id="4fe3b-131">The MDA reports the ID of the thread performing the abort and the ID of the thread that is the target of the abort.</span></span> <span data-ttu-id="4fe3b-132">Bu, zaman uyumsuz iptal ile sınırlandırdığı için hiçbir zaman aynı olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="4fe3b-132">These will never be the same because this is limited to asynchronous aborts.</span></span>

## <a name="configuration"></a><span data-ttu-id="4fe3b-133">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="4fe3b-133">Configuration</span></span>

```xml
<mdaConfig>
  <assistants>
    <asynchronousThreadAbort />
  </assistants>
</mdaConfig>
```

## <a name="example"></a><span data-ttu-id="4fe3b-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="4fe3b-134">Example</span></span>
 <span data-ttu-id="4fe3b-135">`asynchronousThreadAbort` MDA <xref:System.Threading.Thread.Abort%2A> ' ın etkinleştirilmesi ayrı çalışan bir iş parçacığında yalnızca bir çağrısı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="4fe3b-135">Activating the `asynchronousThreadAbort` MDA requires only a call to <xref:System.Threading.Thread.Abort%2A> on a separate running thread.</span></span> <span data-ttu-id="4fe3b-136">İş parçacığı başlatma işlevinin içerikleri, iptal tarafından herhangi bir rastgele noktada kesintiye uğramış olabilecek daha karmaşık işlemler kümesi olsaydı sonuçları göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="4fe3b-136">Consider the consequences if the contents of the thread start function were a set of more complex operations which might be interrupted at any arbitrary point by the abort.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="4fe3b-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4fe3b-137">See also</span></span>

- <xref:System.Threading.Thread>
- [<span data-ttu-id="4fe3b-138">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="4fe3b-138">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
