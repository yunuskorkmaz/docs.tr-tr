---
title: asynchronousThreadAbort MDA
description: Bir iş parçacığı zaman uyumsuz bir iptal işlemini başka bir iş parçacığına koymaya çalıştığında, Asynchronousthreadavbort yönetilen hata ayıklama Yardımcısı 'nın (MDA) nasıl etkinleştirildiğini gözden geçirin.
ms.date: 03/30/2017
helpviewer_keywords:
- asynchronous thread aborts
- AsynchronousThreadAbort MDA
- managed debugging assistants (MDAs), asynchronous thread aborts
- threading [.NET Framework], managed debugging assistants
- MDAs (managed debugging assistants), asynchronous thread aborts
ms.assetid: 9ebe40b2-d703-421e-8660-984acc42bfe0
ms.openlocfilehash: 469372d57d9c21198353d171fec16458691eb25d
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85415673"
---
# <a name="asynchronousthreadabort-mda"></a><span data-ttu-id="4b219-103">asynchronousThreadAbort MDA</span><span class="sxs-lookup"><span data-stu-id="4b219-103">asynchronousThreadAbort MDA</span></span>
<span data-ttu-id="4b219-104">`asynchronousThreadAbort`Yönetilen hata ayıklama Yardımcısı (MDA), bir iş parçacığı başka bir iş parçacığına zaman uyumsuz bir iptal uygulamayı denediğinde etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="4b219-104">The `asynchronousThreadAbort` managed debugging assistant (MDA) is activated when a thread attempts to introduce an asynchronous abort into another thread.</span></span> <span data-ttu-id="4b219-105">Zaman uyumlu iş parçacığı durdurulduğunda MDA 'ı etkinleştirmeyin `asynchronousThreadAbort` .</span><span class="sxs-lookup"><span data-stu-id="4b219-105">Synchronous thread aborts do not activate the `asynchronousThreadAbort` MDA.</span></span>

## <a name="symptoms"></a><span data-ttu-id="4b219-106">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="4b219-106">Symptoms</span></span>
 <span data-ttu-id="4b219-107"><xref:System.Threading.ThreadAbortException>Ana uygulama iş parçacığı iptal edildiğinde, bir uygulama işlenmemiş ile çöküyor.</span><span class="sxs-lookup"><span data-stu-id="4b219-107">An application crashes with an unhandled <xref:System.Threading.ThreadAbortException> when the main application thread is aborted.</span></span> <span data-ttu-id="4b219-108">Uygulamanın yürütülmeye devam etmesi gerekiyorsa, sonuçlar uygulama kilitlenmesinin ardından büyük olasılıkla daha fazla veri bozulmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="4b219-108">If the application were to continue to execute, the consequences might be worse than the application crashing, possibly resulting in further data corruption.</span></span>

 <span data-ttu-id="4b219-109">Atomik olması amaçlanan işlemler kısmen tamamlandığında kesintiye uğratıldıktan sonra, uygulama verileri öngörülemeyen bir durumda bırakılır.</span><span class="sxs-lookup"><span data-stu-id="4b219-109">Operations meant to be atomic have likely been interrupted after partial completion, leaving application data in an unpredictable state.</span></span> <span data-ttu-id="4b219-110">Bir <xref:System.Threading.ThreadAbortException> özel durumun meydana gelmesi beklenmediği yerlerde, kod yürütmesindeki düzensiz rastgele noktalarda oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="4b219-110">A <xref:System.Threading.ThreadAbortException> can be generated from seemingly random points in the execution of code, often in places from which an exception is not expected to arise.</span></span> <span data-ttu-id="4b219-111">Kod böyle bir özel durumu işleyemeyebilir, bu durum bozuk bir duruma neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="4b219-111">The code might not be capable of handling such an exception, resulting in a corrupt state.</span></span>

 <span data-ttu-id="4b219-112">Belirtiler, soruna bağlı rasgelelik nedeniyle büyük ölçüde farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="4b219-112">Symptoms can vary widely due to the randomness inherent to the problem.</span></span>

## <a name="cause"></a><span data-ttu-id="4b219-113">Nedeni</span><span class="sxs-lookup"><span data-stu-id="4b219-113">Cause</span></span>
 <span data-ttu-id="4b219-114">Bir iş parçacığındaki kod, <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> zaman uyumsuz bir iş parçacığı iptali tanıtmak için bir hedef iş parçacığında yöntemi olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="4b219-114">Code in one thread called the <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> method on a target thread to introduce an asynchronous thread abort.</span></span> <span data-ttu-id="4b219-115">Çağrıyı yapan kod, <xref:System.Threading.Thread.Abort%2A> durdurma işleminin hedefinden farklı bir iş parçacığında çalıştığından, iş parçacığı iptali zaman uyumsuzdur.</span><span class="sxs-lookup"><span data-stu-id="4b219-115">The thread abort is asynchronous because the code that makes the call to <xref:System.Threading.Thread.Abort%2A> is running on a different thread than the target of the abort operation.</span></span> <span data-ttu-id="4b219-116">İşlemi gerçekleştiren iş parçacığının <xref:System.Threading.Thread.Abort%2A> yalnızca uygulama durumunun tutarlı olduğu güvenli bir denetim noktasında yapılması gerektiğinden, zaman uyumlu iş parçacığı iptal noktaları soruna neden olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="4b219-116">Synchronous thread aborts should not cause a problem because the thread performing the <xref:System.Threading.Thread.Abort%2A> should have done so only at a safe checkpoint where application state is consistent.</span></span>

 <span data-ttu-id="4b219-117">Zaman uyumsuz thread, hedef iş parçacığının yürütmesindeki öngörülemeyen noktalarda işlendiği için bir sorun oluştu.</span><span class="sxs-lookup"><span data-stu-id="4b219-117">Asynchronous thread aborts present a problem because they are processed at unpredictable points in the target thread's execution.</span></span> <span data-ttu-id="4b219-118">Bu durumdan kaçınmak için, bu şekilde durdurulmuş olabilecek bir iş parçacığında çalışmak üzere yazılan kodun <xref:System.Threading.ThreadAbortException> , neredeyse her bir kod satırında işlenmesi ve uygulama verilerinin tutarlı bir duruma geri alınmasına dikkat etmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="4b219-118">To avoid this, code written to run on a thread that might be aborted in this manner would need to handle a <xref:System.Threading.ThreadAbortException> at almost every line of code, taking care to put application data back into a consistent state.</span></span> <span data-ttu-id="4b219-119">Kodun bu sorun ile yazılması veya tüm olası koşullara karşı koruyan bir kod yazmak için gerçekçi değildir.</span><span class="sxs-lookup"><span data-stu-id="4b219-119">It is not realistic to expect code to be written with this problem in mind or to write code that protects against all possible circumstances.</span></span>

 <span data-ttu-id="4b219-120">Yönetilmeyen kod ve `finally` bloklara yapılan çağrılar zaman uyumsuz olarak iptal edilmez, ancak bu kategorilerden birinden çıkış yapıldığında hemen silinir.</span><span class="sxs-lookup"><span data-stu-id="4b219-120">Calls into unmanaged code and `finally` blocks will not be aborted asynchronously but immediately upon exit from one of these categories.</span></span>

 <span data-ttu-id="4b219-121">Sorunun, soruna bağlı rastgele bir durum nedeniyle belirlenmesi zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="4b219-121">The cause might be difficult to determine due to the randomness inherent to the problem.</span></span>

## <a name="resolution"></a><span data-ttu-id="4b219-122">Çözüm</span><span class="sxs-lookup"><span data-stu-id="4b219-122">Resolution</span></span>
 <span data-ttu-id="4b219-123">Zaman uyumsuz iş parçacığı iptal durumu kullanımını gerektiren kod tasarımını önleyin.</span><span class="sxs-lookup"><span data-stu-id="4b219-123">Avoid code design that requires the use of asynchronous thread aborts.</span></span> <span data-ttu-id="4b219-124">Çağrısı gerektirmeyen bir hedef iş parçacığının kesintiye uğraması için çok sayıda yaklaşım daha uygundur <xref:System.Threading.Thread.Abort%2A> .</span><span class="sxs-lookup"><span data-stu-id="4b219-124">There are several approaches more appropriate for interruption of a target thread that do not require a call to <xref:System.Threading.Thread.Abort%2A>.</span></span> <span data-ttu-id="4b219-125">En güvenli, bir kesme istemek için hedef iş parçacığına işaret eden ortak bir özellik gibi bir mekanizma tanıtmaktır.</span><span class="sxs-lookup"><span data-stu-id="4b219-125">The safest is to introduce a mechanism, such as a common property, that signals the target thread to request an interrupt.</span></span> <span data-ttu-id="4b219-126">Hedef iş parçacığı belirli güvenli denetim noktalarında sinyali denetler.</span><span class="sxs-lookup"><span data-stu-id="4b219-126">The target thread checks the signal at certain safe checkpoints.</span></span> <span data-ttu-id="4b219-127">Bir kesmenin istenmiş olduğunu fark ederseniz, düzgün bir şekilde kapatılabilir.</span><span class="sxs-lookup"><span data-stu-id="4b219-127">If it notices that an interrupt has been requested, it can shut down gracefully.</span></span>

## <a name="effect-on-the-runtime"></a><span data-ttu-id="4b219-128">Çalışma zamanında etki</span><span class="sxs-lookup"><span data-stu-id="4b219-128">Effect on the Runtime</span></span>
 <span data-ttu-id="4b219-129">Bu MDA, CLR üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="4b219-129">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="4b219-130">Yalnızca zaman uyumsuz iş parçacığı iptal eden verileri raporlar.</span><span class="sxs-lookup"><span data-stu-id="4b219-130">It only reports data about asynchronous thread aborts.</span></span>

## <a name="output"></a><span data-ttu-id="4b219-131">Çıktı</span><span class="sxs-lookup"><span data-stu-id="4b219-131">Output</span></span>
 <span data-ttu-id="4b219-132">MDA, Abort işlemini gerçekleştiren iş parçacığının KIMLIĞINI ve iptal 'in hedefi olan iş parçacığının KIMLIĞINI bildirir.</span><span class="sxs-lookup"><span data-stu-id="4b219-132">The MDA reports the ID of the thread performing the abort and the ID of the thread that is the target of the abort.</span></span> <span data-ttu-id="4b219-133">Bu, zaman uyumsuz iptal ile sınırlandırdığı için hiçbir zaman aynı olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="4b219-133">These will never be the same because this is limited to asynchronous aborts.</span></span>

## <a name="configuration"></a><span data-ttu-id="4b219-134">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="4b219-134">Configuration</span></span>

```xml
<mdaConfig>
  <assistants>
    <asynchronousThreadAbort />
  </assistants>
</mdaConfig>
```

## <a name="example"></a><span data-ttu-id="4b219-135">Örnek</span><span class="sxs-lookup"><span data-stu-id="4b219-135">Example</span></span>
 <span data-ttu-id="4b219-136">`asynchronousThreadAbort`Mda ' ın etkinleştirilmesi <xref:System.Threading.Thread.Abort%2A> ayrı çalışan bir iş parçacığında yalnızca bir çağrısı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="4b219-136">Activating the `asynchronousThreadAbort` MDA requires only a call to <xref:System.Threading.Thread.Abort%2A> on a separate running thread.</span></span> <span data-ttu-id="4b219-137">İş parçacığı başlatma işlevinin içerikleri, iptal tarafından herhangi bir rastgele noktada kesintiye uğramış olabilecek daha karmaşık işlemler kümesi olsaydı sonuçları göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="4b219-137">Consider the consequences if the contents of the thread start function were a set of more complex operations which might be interrupted at any arbitrary point by the abort.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="4b219-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4b219-138">See also</span></span>

- <xref:System.Threading.Thread>
- [<span data-ttu-id="4b219-139">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="4b219-139">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
