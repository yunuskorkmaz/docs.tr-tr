---
title: fatalExecutionEngineError MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: cda166645bad2ad7780da58c287880398605806f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="fatalexecutionengineerror-mda"></a><span data-ttu-id="05b63-102">fatalExecutionEngineError MDA</span><span class="sxs-lookup"><span data-stu-id="05b63-102">fatalExecutionEngineError MDA</span></span>
<span data-ttu-id="05b63-103">`fatalExecutionEngine``Error` Yönetilen hata ayıklama Yardımcısı (MDA), ortak dil çalışma zamanı (CLR) önemli bir hata algılandığında etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="05b63-103">The `fatalExecutionEngine``Error` managed debugging assistant (MDA) is activated when a fatal error in the common language runtime (CLR) has been detected.</span></span> <span data-ttu-id="05b63-104">İşlem sonlandırılacak.</span><span class="sxs-lookup"><span data-stu-id="05b63-104">The process will be terminated.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="05b63-105">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="05b63-105">Symptoms</span></span>  
 <span data-ttu-id="05b63-106">Beklenmeyen işlem sonlandırma.</span><span class="sxs-lookup"><span data-stu-id="05b63-106">Unexpected process termination.</span></span> <span data-ttu-id="05b63-107">CLR hata çeşitli nedenlerden dolayı olabileceği için diğer Belirtiler belirlenemiyor.</span><span class="sxs-lookup"><span data-stu-id="05b63-107">Other symptoms cannot be determined because a CLR failure can occur for a variety of reasons.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="05b63-108">Sebep</span><span class="sxs-lookup"><span data-stu-id="05b63-108">Cause</span></span>  
 <span data-ttu-id="05b63-109">CLR fatally bozuldu.</span><span class="sxs-lookup"><span data-stu-id="05b63-109">The CLR has been fatally corrupted.</span></span> <span data-ttu-id="05b63-110">Bu çoğunlukla gibi işlevler ve CLR geçersiz veri geçirme çağrıları hatalı biçimlendirilmiş platform çağırma olduğu sorunları sayıyla kaynaklanabilir veri bozulması kaynaklanır.</span><span class="sxs-lookup"><span data-stu-id="05b63-110">This is most often caused by data corruption, which can be caused by a number of problems, such as calls to malformed platform invoke functions and passing invalid data to the CLR.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="05b63-111">Çözüm</span><span class="sxs-lookup"><span data-stu-id="05b63-111">Resolution</span></span>  
 <span data-ttu-id="05b63-112">Ek Mda'lar etkinleştirme sorun belirlenmesine yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="05b63-112">Enabling additional MDAs might help identify the problem.</span></span> <span data-ttu-id="05b63-113">Aşağıdaki Mda'lar sorunu tanılamada özellikle yararlı olabilir:</span><span class="sxs-lookup"><span data-stu-id="05b63-113">The following MDAs can be particularly helpful in diagnosing the issue:</span></span>  
  
-   [<span data-ttu-id="05b63-114">invalidOverlappedToPinvoke</span><span class="sxs-lookup"><span data-stu-id="05b63-114">invalidOverlappedToPinvoke</span></span>](../../../docs/framework/debug-trace-profile/invalidoverlappedtopinvoke-mda.md)  
  
-   [<span data-ttu-id="05b63-115">overlappedFreeError</span><span class="sxs-lookup"><span data-stu-id="05b63-115">overlappedFreeError</span></span>](../../../docs/framework/debug-trace-profile/overlappedfreeerror-mda.md)  
  
-   [<span data-ttu-id="05b63-116">pInvokeStackImbalance</span><span class="sxs-lookup"><span data-stu-id="05b63-116">pInvokeStackImbalance</span></span>](../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md)  
  
-   [<span data-ttu-id="05b63-117">gcUnmanagedToManaged</span><span class="sxs-lookup"><span data-stu-id="05b63-117">gcUnmanagedToManaged</span></span>](../../../docs/framework/debug-trace-profile/gcunmanagedtomanaged-mda.md)  
  
-   [<span data-ttu-id="05b63-118">gcManagedToUnmanaged</span><span class="sxs-lookup"><span data-stu-id="05b63-118">gcManagedToUnmanaged</span></span>](../../../docs/framework/debug-trace-profile/gcmanagedtounmanaged-mda.md)  
  
-   [<span data-ttu-id="05b63-119">callbackOnCollectedDelegate</span><span class="sxs-lookup"><span data-stu-id="05b63-119">callbackOnCollectedDelegate</span></span>](../../../docs/framework/debug-trace-profile/callbackoncollecteddelegate-mda.md)  
  
-   [<span data-ttu-id="05b63-120">reportAvOnComRelease</span><span class="sxs-lookup"><span data-stu-id="05b63-120">reportAvOnComRelease</span></span>](../../../docs/framework/debug-trace-profile/reportavoncomrelease-mda.md)  
  
-   [<span data-ttu-id="05b63-121">invalidVariant</span><span class="sxs-lookup"><span data-stu-id="05b63-121">invalidVariant</span></span>](../../../docs/framework/debug-trace-profile/invalidvariant-mda.md)  
  
-   [<span data-ttu-id="05b63-122">invalidIUnknown</span><span class="sxs-lookup"><span data-stu-id="05b63-122">invalidIUnknown</span></span>](../../../docs/framework/debug-trace-profile/invalidiunknown-mda.md)  
  
-   [<span data-ttu-id="05b63-123">raceOnRCWCleanup</span><span class="sxs-lookup"><span data-stu-id="05b63-123">raceOnRCWCleanup</span></span>](../../../docs/framework/debug-trace-profile/raceonrcwcleanup-mda.md)  
  
-   [<span data-ttu-id="05b63-124">invalidFunctionPointerInDelegate</span><span class="sxs-lookup"><span data-stu-id="05b63-124">invalidFunctionPointerInDelegate</span></span>](../../../docs/framework/debug-trace-profile/invalidfunctionpointerindelegate-mda.md)  
  
-   [<span data-ttu-id="05b63-125">invalidGCHandleCookie</span><span class="sxs-lookup"><span data-stu-id="05b63-125">invalidGCHandleCookie</span></span>](../../../docs/framework/debug-trace-profile/invalidgchandlecookie-mda.md)  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="05b63-126">Çalışma zamanı etkisi</span><span class="sxs-lookup"><span data-stu-id="05b63-126">Effect on the Runtime</span></span>  
 <span data-ttu-id="05b63-127">Bu MDA çalışma zamanı davranışı üzerinde etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="05b63-127">This MDA has no effect on the runtime's behavior.</span></span>  
  
## <a name="output"></a><span data-ttu-id="05b63-128">Çıkış</span><span class="sxs-lookup"><span data-stu-id="05b63-128">Output</span></span>  
 <span data-ttu-id="05b63-129">Önemli hata, hatanın oluştuğu iş parçacığı kimliği ve hata kodu nedeniyle CLR işlevi adresi.</span><span class="sxs-lookup"><span data-stu-id="05b63-129">The address of the CLR function that caused the fatal error, the ID of the thread where the error occurred, and the error code.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="05b63-130">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="05b63-130">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <fatalExecutionEngineError />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="05b63-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="05b63-131">See Also</span></span>  
 <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A>  
 <xref:System.Runtime.ConstrainedExecution.Cer>  
 [<span data-ttu-id="05b63-132">Yönetilen hata ayıklama Yardımcıları ile hataları tanılama</span><span class="sxs-lookup"><span data-stu-id="05b63-132">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
