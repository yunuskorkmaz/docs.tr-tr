---
title: fatalExecutionEngineError MDA
ms.date: 03/30/2017
helpviewer_keywords:
- corrupted CLR
- fatal execution error
- terminated processes
- unexpected terminations
- fatal errors
- MDAs (managed debugging assistants), fatal errors
- process termination
- FatalExecutionEngineError MDA
- managed debugging assistants (MDAs), fatal errors
ms.assetid: 8b559e44-2393-4e4e-8160-7558d37a4a89
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f12b94198b88111d559cfe372c28bdbf4b37e3fe
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43742650"
---
# <a name="fatalexecutionengineerror-mda"></a><span data-ttu-id="f9f3f-102">fatalExecutionEngineError MDA</span><span class="sxs-lookup"><span data-stu-id="f9f3f-102">fatalExecutionEngineError MDA</span></span>
<span data-ttu-id="f9f3f-103">`fatalExecutionEngineError` Yönetilen hata ayıklama Yardımcısı (MDA), ortak dil çalışma zamanı (CLR) önemli bir hata algılandığında etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="f9f3f-103">The `fatalExecutionEngineError` managed debugging assistant (MDA) is activated when a fatal error in the common language runtime (CLR) has been detected.</span></span> <span data-ttu-id="f9f3f-104">İşlem sonlandırılacak.</span><span class="sxs-lookup"><span data-stu-id="f9f3f-104">The process will be terminated.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="f9f3f-105">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="f9f3f-105">Symptoms</span></span>  
 <span data-ttu-id="f9f3f-106">Beklenmeyen işlem sonlandırma.</span><span class="sxs-lookup"><span data-stu-id="f9f3f-106">Unexpected process termination.</span></span> <span data-ttu-id="f9f3f-107">CLR hata çeşitli nedenlerden dolayı ortaya çıkabileceğinden diğer belirtileri belirlenemiyor.</span><span class="sxs-lookup"><span data-stu-id="f9f3f-107">Other symptoms cannot be determined because a CLR failure can occur for a variety of reasons.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="f9f3f-108">Sebep</span><span class="sxs-lookup"><span data-stu-id="f9f3f-108">Cause</span></span>  
 <span data-ttu-id="f9f3f-109">CLR fatally bozulmuş.</span><span class="sxs-lookup"><span data-stu-id="f9f3f-109">The CLR has been fatally corrupted.</span></span> <span data-ttu-id="f9f3f-110">Bu çoğunlukla veri bozulması, işlevleri ve CLR ile geçersiz veri geçirme hatalı biçimlendirilmiş platform çağrıları çağırır gibi sorunları sayısına göre neden kaynaklanır.</span><span class="sxs-lookup"><span data-stu-id="f9f3f-110">This is most often caused by data corruption, which can be caused by a number of problems, such as calls to malformed platform invoke functions and passing invalid data to the CLR.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="f9f3f-111">Çözüm</span><span class="sxs-lookup"><span data-stu-id="f9f3f-111">Resolution</span></span>  
 <span data-ttu-id="f9f3f-112">Ek Mda'leri etkinleştirme, sorunun belirlenmesine yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="f9f3f-112">Enabling additional MDAs might help identify the problem.</span></span> <span data-ttu-id="f9f3f-113">Aşağıdaki Mda'leri özellikle sorunu tanılamada yararlı olabilir:</span><span class="sxs-lookup"><span data-stu-id="f9f3f-113">The following MDAs can be particularly helpful in diagnosing the issue:</span></span>  
  
-   [<span data-ttu-id="f9f3f-114">invalidOverlappedToPinvoke</span><span class="sxs-lookup"><span data-stu-id="f9f3f-114">invalidOverlappedToPinvoke</span></span>](../../../docs/framework/debug-trace-profile/invalidoverlappedtopinvoke-mda.md)  
  
-   [<span data-ttu-id="f9f3f-115">overlappedFreeError</span><span class="sxs-lookup"><span data-stu-id="f9f3f-115">overlappedFreeError</span></span>](../../../docs/framework/debug-trace-profile/overlappedfreeerror-mda.md)  
  
-   [<span data-ttu-id="f9f3f-116">pInvokeStackImbalance</span><span class="sxs-lookup"><span data-stu-id="f9f3f-116">pInvokeStackImbalance</span></span>](../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md)  
  
-   [<span data-ttu-id="f9f3f-117">gcUnmanagedToManaged</span><span class="sxs-lookup"><span data-stu-id="f9f3f-117">gcUnmanagedToManaged</span></span>](../../../docs/framework/debug-trace-profile/gcunmanagedtomanaged-mda.md)  
  
-   [<span data-ttu-id="f9f3f-118">gcManagedToUnmanaged</span><span class="sxs-lookup"><span data-stu-id="f9f3f-118">gcManagedToUnmanaged</span></span>](../../../docs/framework/debug-trace-profile/gcmanagedtounmanaged-mda.md)  
  
-   [<span data-ttu-id="f9f3f-119">callbackOnCollectedDelegate</span><span class="sxs-lookup"><span data-stu-id="f9f3f-119">callbackOnCollectedDelegate</span></span>](../../../docs/framework/debug-trace-profile/callbackoncollecteddelegate-mda.md)  
  
-   [<span data-ttu-id="f9f3f-120">reportAvOnComRelease</span><span class="sxs-lookup"><span data-stu-id="f9f3f-120">reportAvOnComRelease</span></span>](../../../docs/framework/debug-trace-profile/reportavoncomrelease-mda.md)  
  
-   [<span data-ttu-id="f9f3f-121">invalidVariant</span><span class="sxs-lookup"><span data-stu-id="f9f3f-121">invalidVariant</span></span>](../../../docs/framework/debug-trace-profile/invalidvariant-mda.md)  
  
-   [<span data-ttu-id="f9f3f-122">invalidIUnknown</span><span class="sxs-lookup"><span data-stu-id="f9f3f-122">invalidIUnknown</span></span>](../../../docs/framework/debug-trace-profile/invalidiunknown-mda.md)  
  
-   [<span data-ttu-id="f9f3f-123">raceOnRCWCleanup</span><span class="sxs-lookup"><span data-stu-id="f9f3f-123">raceOnRCWCleanup</span></span>](../../../docs/framework/debug-trace-profile/raceonrcwcleanup-mda.md)  
  
-   [<span data-ttu-id="f9f3f-124">invalidFunctionPointerInDelegate</span><span class="sxs-lookup"><span data-stu-id="f9f3f-124">invalidFunctionPointerInDelegate</span></span>](../../../docs/framework/debug-trace-profile/invalidfunctionpointerindelegate-mda.md)  
  
-   [<span data-ttu-id="f9f3f-125">invalidGCHandleCookie</span><span class="sxs-lookup"><span data-stu-id="f9f3f-125">invalidGCHandleCookie</span></span>](../../../docs/framework/debug-trace-profile/invalidgchandlecookie-mda.md)  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="f9f3f-126">Çalışma zamanı üzerindeki etkisi</span><span class="sxs-lookup"><span data-stu-id="f9f3f-126">Effect on the Runtime</span></span>  
 <span data-ttu-id="f9f3f-127">Bu MDA çalışma zamanı davranışı üzerinde etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="f9f3f-127">This MDA has no effect on the runtime's behavior.</span></span>  
  
## <a name="output"></a><span data-ttu-id="f9f3f-128">Çıkış</span><span class="sxs-lookup"><span data-stu-id="f9f3f-128">Output</span></span>  
 <span data-ttu-id="f9f3f-129">Önemli hata ve hatanın oluştuğu iş parçacığının kimliği hata kodu nedeniyle CLR işlevi adresi.</span><span class="sxs-lookup"><span data-stu-id="f9f3f-129">The address of the CLR function that caused the fatal error, the ID of the thread where the error occurred, and the error code.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="f9f3f-130">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="f9f3f-130">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <fatalExecutionEngineError />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f9f3f-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f9f3f-131">See Also</span></span>  
 <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A>  
 <xref:System.Runtime.ConstrainedExecution.Cer>  
 [<span data-ttu-id="f9f3f-132">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="f9f3f-132">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
