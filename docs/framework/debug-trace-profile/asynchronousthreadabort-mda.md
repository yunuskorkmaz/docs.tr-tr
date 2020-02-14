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
ms.openlocfilehash: d0c78e6d52ae4a5b3a24e0bb4278b2e8a1b98751
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217587"
---
# <a name="asynchronousthreadabort-mda"></a><span data-ttu-id="74251-102">asynchronousThreadAbort MDA</span><span class="sxs-lookup"><span data-stu-id="74251-102">asynchronousThreadAbort MDA</span></span>
<span data-ttu-id="74251-103">`asynchronousThreadAbort` yönetilen hata ayıklama Yardımcısı (MDA), bir iş parçacığı başka bir iş parçacığına zaman uyumsuz bir iptal yapmayı denediğinde etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="74251-103">The `asynchronousThreadAbort` managed debugging assistant (MDA) is activated when a thread attempts to introduce an asynchronous abort into another thread.</span></span> <span data-ttu-id="74251-104">Zaman uyumlu iş parçacığı durdurulduğunda `asynchronousThreadAbort` MDA ' i etkinleştirmeyin.</span><span class="sxs-lookup"><span data-stu-id="74251-104">Synchronous thread aborts do not activate the `asynchronousThreadAbort` MDA.</span></span>

## <a name="symptoms"></a><span data-ttu-id="74251-105">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="74251-105">Symptoms</span></span>
 <span data-ttu-id="74251-106">Ana uygulama iş parçacığı iptal edildiğinde, bir uygulama işlenmemiş bir <xref:System.Threading.ThreadAbortException> kilitleniyor.</span><span class="sxs-lookup"><span data-stu-id="74251-106">An application crashes with an unhandled <xref:System.Threading.ThreadAbortException> when the main application thread is aborted.</span></span> <span data-ttu-id="74251-107">Uygulamanın yürütülmeye devam etmesi gerekiyorsa, sonuçlar uygulama kilitlenmesinin ardından büyük olasılıkla daha fazla veri bozulmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="74251-107">If the application were to continue to execute, the consequences might be worse than the application crashing, possibly resulting in further data corruption.</span></span>

 <span data-ttu-id="74251-108">Atomik olması amaçlanan işlemler kısmen tamamlandığında kesintiye uğratıldıktan sonra, uygulama verileri öngörülemeyen bir durumda bırakılır.</span><span class="sxs-lookup"><span data-stu-id="74251-108">Operations meant to be atomic have likely been interrupted after partial completion, leaving application data in an unpredictable state.</span></span> <span data-ttu-id="74251-109">Bir <xref:System.Threading.ThreadAbortException>, genellikle bir özel durumun meydana gelmesi beklenmediği yerlerde kodun yürütülmesindeki düzensiz rastgele noktalardan oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="74251-109">A <xref:System.Threading.ThreadAbortException> can be generated from seemingly random points in the execution of code, often in places from which an exception is not expected to arise.</span></span> <span data-ttu-id="74251-110">Kod böyle bir özel durumu işleyemeyebilir, bu durum bozuk bir duruma neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="74251-110">The code might not be capable of handling such an exception, resulting in a corrupt state.</span></span>

 <span data-ttu-id="74251-111">Belirtiler, soruna bağlı rasgelelik nedeniyle büyük ölçüde farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="74251-111">Symptoms can vary widely due to the randomness inherent to the problem.</span></span>

## <a name="cause"></a><span data-ttu-id="74251-112">Nedeni</span><span class="sxs-lookup"><span data-stu-id="74251-112">Cause</span></span>
 <span data-ttu-id="74251-113">Bir iş parçacığında, zaman uyumsuz bir iş parçacığı iptali tanıtmak için <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> yöntemi olarak adlandırılan kod.</span><span class="sxs-lookup"><span data-stu-id="74251-113">Code in one thread called the <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> method on a target thread to introduce an asynchronous thread abort.</span></span> <span data-ttu-id="74251-114"><xref:System.Threading.Thread.Abort%2A> çağrısını yapan kod, durdurma işleminin hedefinden farklı bir iş parçacığında çalıştığından iş parçacığı iptali zaman uyumsuzdur.</span><span class="sxs-lookup"><span data-stu-id="74251-114">The thread abort is asynchronous because the code that makes the call to <xref:System.Threading.Thread.Abort%2A> is running on a different thread than the target of the abort operation.</span></span> <span data-ttu-id="74251-115"><xref:System.Threading.Thread.Abort%2A> gerçekleştiren iş parçacığının yalnızca uygulama durumunun tutarlı olduğu güvenli bir denetim noktasında yapılması gerektiğinden, zaman uyumlu iş parçacığı iptal etmek soruna neden olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="74251-115">Synchronous thread aborts should not cause a problem because the thread performing the <xref:System.Threading.Thread.Abort%2A> should have done so only at a safe checkpoint where application state is consistent.</span></span>

 <span data-ttu-id="74251-116">Zaman uyumsuz thread, hedef iş parçacığının yürütmesindeki öngörülemeyen noktalarda işlendiği için bir sorun oluştu.</span><span class="sxs-lookup"><span data-stu-id="74251-116">Asynchronous thread aborts present a problem because they are processed at unpredictable points in the target thread's execution.</span></span> <span data-ttu-id="74251-117">Bunu önlemek için, bu şekilde durdurulmuş olabilecek bir iş parçacığında çalışmak üzere yazılan kodun, neredeyse her kod satırında bir <xref:System.Threading.ThreadAbortException> işlemesi ve uygulama verilerinin tutarlı bir duruma geri alınmasına dikkat etmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="74251-117">To avoid this, code written to run on a thread that might be aborted in this manner would need to handle a <xref:System.Threading.ThreadAbortException> at almost every line of code, taking care to put application data back into a consistent state.</span></span> <span data-ttu-id="74251-118">Kodun bu sorun ile yazılması veya tüm olası koşullara karşı koruyan bir kod yazmak için gerçekçi değildir.</span><span class="sxs-lookup"><span data-stu-id="74251-118">It is not realistic to expect code to be written with this problem in mind or to write code that protects against all possible circumstances.</span></span>

 <span data-ttu-id="74251-119">Yönetilmeyen koda yapılan çağrılar ve `finally` blokları zaman uyumsuz olarak durdurulmayacak, ancak bu kategorilerden birinden çıkmadan hemen sonra olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="74251-119">Calls into unmanaged code and `finally` blocks will not be aborted asynchronously but immediately upon exit from one of these categories.</span></span>

 <span data-ttu-id="74251-120">Sorunun, soruna bağlı rastgele bir durum nedeniyle belirlenmesi zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="74251-120">The cause might be difficult to determine due to the randomness inherent to the problem.</span></span>

## <a name="resolution"></a><span data-ttu-id="74251-121">Çözüm</span><span class="sxs-lookup"><span data-stu-id="74251-121">Resolution</span></span>
 <span data-ttu-id="74251-122">Zaman uyumsuz iş parçacığı iptal durumu kullanımını gerektiren kod tasarımını önleyin.</span><span class="sxs-lookup"><span data-stu-id="74251-122">Avoid code design that requires the use of asynchronous thread aborts.</span></span> <span data-ttu-id="74251-123"><xref:System.Threading.Thread.Abort%2A>çağrısı gerektirmeyen bir hedef iş parçacığının kesintiye uğramasını sağlamak için birkaç yaklaşım daha uygundur.</span><span class="sxs-lookup"><span data-stu-id="74251-123">There are several approaches more appropriate for interruption of a target thread that do not require a call to <xref:System.Threading.Thread.Abort%2A>.</span></span> <span data-ttu-id="74251-124">En güvenli, bir kesme istemek için hedef iş parçacığına işaret eden ortak bir özellik gibi bir mekanizma tanıtmaktır.</span><span class="sxs-lookup"><span data-stu-id="74251-124">The safest is to introduce a mechanism, such as a common property, that signals the target thread to request an interrupt.</span></span> <span data-ttu-id="74251-125">Hedef iş parçacığı belirli güvenli denetim noktalarında sinyali denetler.</span><span class="sxs-lookup"><span data-stu-id="74251-125">The target thread checks the signal at certain safe checkpoints.</span></span> <span data-ttu-id="74251-126">Bir kesmenin istenmiş olduğunu fark ederseniz, düzgün bir şekilde kapatılabilir.</span><span class="sxs-lookup"><span data-stu-id="74251-126">If it notices that an interrupt has been requested, it can shut down gracefully.</span></span>

## <a name="effect-on-the-runtime"></a><span data-ttu-id="74251-127">Çalışma zamanında etki</span><span class="sxs-lookup"><span data-stu-id="74251-127">Effect on the Runtime</span></span>
 <span data-ttu-id="74251-128">Bu MDA, CLR üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="74251-128">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="74251-129">Yalnızca zaman uyumsuz iş parçacığı iptal eden verileri raporlar.</span><span class="sxs-lookup"><span data-stu-id="74251-129">It only reports data about asynchronous thread aborts.</span></span>

## <a name="output"></a><span data-ttu-id="74251-130">Çıktı</span><span class="sxs-lookup"><span data-stu-id="74251-130">Output</span></span>
 <span data-ttu-id="74251-131">MDA, Abort işlemini gerçekleştiren iş parçacığının KIMLIĞINI ve iptal 'in hedefi olan iş parçacığının KIMLIĞINI bildirir.</span><span class="sxs-lookup"><span data-stu-id="74251-131">The MDA reports the ID of the thread performing the abort and the ID of the thread that is the target of the abort.</span></span> <span data-ttu-id="74251-132">Bu, zaman uyumsuz iptal ile sınırlandırdığı için hiçbir zaman aynı olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="74251-132">These will never be the same because this is limited to asynchronous aborts.</span></span>

## <a name="configuration"></a><span data-ttu-id="74251-133">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="74251-133">Configuration</span></span>

```xml
<mdaConfig>
  <assistants>
    <asynchronousThreadAbort />
  </assistants>
</mdaConfig>
```

## <a name="example"></a><span data-ttu-id="74251-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="74251-134">Example</span></span>
 <span data-ttu-id="74251-135">`asynchronousThreadAbort` MDA ' nin etkinleştirilmesi ayrı çalışan bir iş parçacığında yalnızca bir <xref:System.Threading.Thread.Abort%2A> çağrısı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="74251-135">Activating the `asynchronousThreadAbort` MDA requires only a call to <xref:System.Threading.Thread.Abort%2A> on a separate running thread.</span></span> <span data-ttu-id="74251-136">İş parçacığı başlatma işlevinin içerikleri, iptal tarafından herhangi bir rastgele noktada kesintiye uğramış olabilecek daha karmaşık işlemler kümesi olsaydı sonuçları göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="74251-136">Consider the consequences if the contents of the thread start function were a set of more complex operations which might be interrupted at any arbitrary point by the abort.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="74251-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="74251-137">See also</span></span>

- <xref:System.Threading.Thread>
- [<span data-ttu-id="74251-138">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="74251-138">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
