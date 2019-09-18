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
ms.openlocfilehash: 3fd58ae8f73fd932df641ea96a44ff618dd139e2
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052800"
---
# <a name="fatalexecutionengineerror-mda"></a><span data-ttu-id="16562-102">fatalExecutionEngineError MDA</span><span class="sxs-lookup"><span data-stu-id="16562-102">fatalExecutionEngineError MDA</span></span>
<span data-ttu-id="16562-103">`fatalExecutionEngineError` Yönetilen hata ayıklama Yardımcısı (MDA), ortak dil çalışma zamanında (CLR) önemli bir hata algılandığında etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="16562-103">The `fatalExecutionEngineError` managed debugging assistant (MDA) is activated when a fatal error in the common language runtime (CLR) has been detected.</span></span> <span data-ttu-id="16562-104">İşlem sonlandırılacak.</span><span class="sxs-lookup"><span data-stu-id="16562-104">The process will be terminated.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="16562-105">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="16562-105">Symptoms</span></span>  
 <span data-ttu-id="16562-106">Beklenmeyen işlem sonlandırma.</span><span class="sxs-lookup"><span data-stu-id="16562-106">Unexpected process termination.</span></span> <span data-ttu-id="16562-107">Çeşitli nedenlerden dolayı bir CLR hatası gerçekleşebildiğinden diğer belirtiler belirlenemez.</span><span class="sxs-lookup"><span data-stu-id="16562-107">Other symptoms cannot be determined because a CLR failure can occur for a variety of reasons.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="16562-108">Sebep</span><span class="sxs-lookup"><span data-stu-id="16562-108">Cause</span></span>  
 <span data-ttu-id="16562-109">CLR 'nin bozulmuş olması.</span><span class="sxs-lookup"><span data-stu-id="16562-109">The CLR has been fatally corrupted.</span></span> <span data-ttu-id="16562-110">Bu, genellikle hatalı oluşturulmuş platform çağırma işlevlerine yapılan çağrılar ve CLR 'ye geçersiz veri geçirme gibi birçok sorun nedeniyle veri bozulması nedeniyle oluşur.</span><span class="sxs-lookup"><span data-stu-id="16562-110">This is most often caused by data corruption, which can be caused by a number of problems, such as calls to malformed platform invoke functions and passing invalid data to the CLR.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="16562-111">Çözüm</span><span class="sxs-lookup"><span data-stu-id="16562-111">Resolution</span></span>  
 <span data-ttu-id="16562-112">Ek Mdaları etkinleştirmek sorunu belirlemenize yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="16562-112">Enabling additional MDAs might help identify the problem.</span></span> <span data-ttu-id="16562-113">Aşağıdaki Mdalar, sorunu tanılamak için özellikle yararlı olabilir:</span><span class="sxs-lookup"><span data-stu-id="16562-113">The following MDAs can be particularly helpful in diagnosing the issue:</span></span>  
  
- [<span data-ttu-id="16562-114">invalidOverlappedToPinvoke</span><span class="sxs-lookup"><span data-stu-id="16562-114">invalidOverlappedToPinvoke</span></span>](invalidoverlappedtopinvoke-mda.md)  
  
- [<span data-ttu-id="16562-115">overlappedFreeError</span><span class="sxs-lookup"><span data-stu-id="16562-115">overlappedFreeError</span></span>](overlappedfreeerror-mda.md)  
  
- [<span data-ttu-id="16562-116">pInvokeStackImbalance</span><span class="sxs-lookup"><span data-stu-id="16562-116">pInvokeStackImbalance</span></span>](pinvokestackimbalance-mda.md)  
  
- [<span data-ttu-id="16562-117">gcUnmanagedToManaged</span><span class="sxs-lookup"><span data-stu-id="16562-117">gcUnmanagedToManaged</span></span>](gcunmanagedtomanaged-mda.md)  
  
- [<span data-ttu-id="16562-118">gcManagedToUnmanaged</span><span class="sxs-lookup"><span data-stu-id="16562-118">gcManagedToUnmanaged</span></span>](gcmanagedtounmanaged-mda.md)  
  
- [<span data-ttu-id="16562-119">callbackOnCollectedDelegate</span><span class="sxs-lookup"><span data-stu-id="16562-119">callbackOnCollectedDelegate</span></span>](callbackoncollecteddelegate-mda.md)  
  
- [<span data-ttu-id="16562-120">reportAvOnComRelease</span><span class="sxs-lookup"><span data-stu-id="16562-120">reportAvOnComRelease</span></span>](reportavoncomrelease-mda.md)  
  
- [<span data-ttu-id="16562-121">invalidVariant</span><span class="sxs-lookup"><span data-stu-id="16562-121">invalidVariant</span></span>](invalidvariant-mda.md)  
  
- [<span data-ttu-id="16562-122">invalidIUnknown</span><span class="sxs-lookup"><span data-stu-id="16562-122">invalidIUnknown</span></span>](invalidiunknown-mda.md)  
  
- [<span data-ttu-id="16562-123">raceOnRCWCleanup</span><span class="sxs-lookup"><span data-stu-id="16562-123">raceOnRCWCleanup</span></span>](raceonrcwcleanup-mda.md)  
  
- [<span data-ttu-id="16562-124">invalidFunctionPointerInDelegate</span><span class="sxs-lookup"><span data-stu-id="16562-124">invalidFunctionPointerInDelegate</span></span>](invalidfunctionpointerindelegate-mda.md)  
  
- [<span data-ttu-id="16562-125">invalidGCHandleCookie</span><span class="sxs-lookup"><span data-stu-id="16562-125">invalidGCHandleCookie</span></span>](invalidgchandlecookie-mda.md)  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="16562-126">Çalışma zamanında etki</span><span class="sxs-lookup"><span data-stu-id="16562-126">Effect on the Runtime</span></span>  
 <span data-ttu-id="16562-127">Bu MDA çalışma zamanının davranışı üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="16562-127">This MDA has no effect on the runtime's behavior.</span></span>  
  
## <a name="output"></a><span data-ttu-id="16562-128">Çıkış</span><span class="sxs-lookup"><span data-stu-id="16562-128">Output</span></span>  
 <span data-ttu-id="16562-129">Kritik hataya neden olan CLR işlevinin adresi, hatanın oluştuğu iş parçacığının KIMLIĞI ve hata kodu.</span><span class="sxs-lookup"><span data-stu-id="16562-129">The address of the CLR function that caused the fatal error, the ID of the thread where the error occurred, and the error code.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="16562-130">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="16562-130">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <fatalExecutionEngineError />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="16562-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="16562-131">See also</span></span>

- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A>
- <xref:System.Runtime.ConstrainedExecution.Cer>
- [<span data-ttu-id="16562-132">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="16562-132">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
