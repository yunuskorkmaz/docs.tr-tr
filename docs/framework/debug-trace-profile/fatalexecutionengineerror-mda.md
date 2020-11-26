---
title: fatalExecutionEngineError MDA
description: .NET 'teki fatalExecutionEngineError Managed hata ayıklama Yardımcısı 'nı (MDA) gözden geçirin ve bu durum beklenmeyen bir işlem sonlandırması nedeniyle etkinleştirilebilir.
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
ms.openlocfilehash: a9347338d53755b74b3ff291f75cb6b221134130
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96244281"
---
# <a name="fatalexecutionengineerror-mda"></a><span data-ttu-id="a2e2e-103">fatalExecutionEngineError MDA</span><span class="sxs-lookup"><span data-stu-id="a2e2e-103">fatalExecutionEngineError MDA</span></span>

<span data-ttu-id="a2e2e-104">`fatalExecutionEngineError`Yönetilen hata ayıklama Yardımcısı (MDA), ortak dil çalışma zamanında (CLR) önemli bir hata algılandığında etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="a2e2e-104">The `fatalExecutionEngineError` managed debugging assistant (MDA) is activated when a fatal error in the common language runtime (CLR) has been detected.</span></span> <span data-ttu-id="a2e2e-105">İşlem sonlandırılacak.</span><span class="sxs-lookup"><span data-stu-id="a2e2e-105">The process will be terminated.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="a2e2e-106">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="a2e2e-106">Symptoms</span></span>  

 <span data-ttu-id="a2e2e-107">Beklenmeyen işlem sonlandırma.</span><span class="sxs-lookup"><span data-stu-id="a2e2e-107">Unexpected process termination.</span></span> <span data-ttu-id="a2e2e-108">Çeşitli nedenlerden dolayı bir CLR hatası gerçekleşebildiğinden diğer belirtiler belirlenemez.</span><span class="sxs-lookup"><span data-stu-id="a2e2e-108">Other symptoms cannot be determined because a CLR failure can occur for a variety of reasons.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="a2e2e-109">Nedeni</span><span class="sxs-lookup"><span data-stu-id="a2e2e-109">Cause</span></span>  

 <span data-ttu-id="a2e2e-110">CLR 'nin bozulmuş olması.</span><span class="sxs-lookup"><span data-stu-id="a2e2e-110">The CLR has been fatally corrupted.</span></span> <span data-ttu-id="a2e2e-111">Bu, genellikle hatalı oluşturulmuş platform çağırma işlevlerine yapılan çağrılar ve CLR 'ye geçersiz veri geçirme gibi birçok sorun nedeniyle veri bozulması nedeniyle oluşur.</span><span class="sxs-lookup"><span data-stu-id="a2e2e-111">This is most often caused by data corruption, which can be caused by a number of problems, such as calls to malformed platform invoke functions and passing invalid data to the CLR.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="a2e2e-112">Çözüm</span><span class="sxs-lookup"><span data-stu-id="a2e2e-112">Resolution</span></span>  

 <span data-ttu-id="a2e2e-113">Ek Mdaları etkinleştirmek sorunu belirlemenize yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="a2e2e-113">Enabling additional MDAs might help identify the problem.</span></span> <span data-ttu-id="a2e2e-114">Aşağıdaki Mdalar, sorunu tanılamak için özellikle yararlı olabilir:</span><span class="sxs-lookup"><span data-stu-id="a2e2e-114">The following MDAs can be particularly helpful in diagnosing the issue:</span></span>  
  
- [<span data-ttu-id="a2e2e-115">invalidOverlappedToPinvoke</span><span class="sxs-lookup"><span data-stu-id="a2e2e-115">invalidOverlappedToPinvoke</span></span>](invalidoverlappedtopinvoke-mda.md)  
  
- [<span data-ttu-id="a2e2e-116">overlappedFreeError</span><span class="sxs-lookup"><span data-stu-id="a2e2e-116">overlappedFreeError</span></span>](overlappedfreeerror-mda.md)  
  
- [<span data-ttu-id="a2e2e-117">pInvokeStackImbalance</span><span class="sxs-lookup"><span data-stu-id="a2e2e-117">pInvokeStackImbalance</span></span>](pinvokestackimbalance-mda.md)  
  
- [<span data-ttu-id="a2e2e-118">gcUnmanagedToManaged</span><span class="sxs-lookup"><span data-stu-id="a2e2e-118">gcUnmanagedToManaged</span></span>](gcunmanagedtomanaged-mda.md)  
  
- [<span data-ttu-id="a2e2e-119">gcManagedToUnmanaged</span><span class="sxs-lookup"><span data-stu-id="a2e2e-119">gcManagedToUnmanaged</span></span>](gcmanagedtounmanaged-mda.md)  
  
- [<span data-ttu-id="a2e2e-120">callbackOnCollectedDelegate</span><span class="sxs-lookup"><span data-stu-id="a2e2e-120">callbackOnCollectedDelegate</span></span>](callbackoncollecteddelegate-mda.md)  
  
- [<span data-ttu-id="a2e2e-121">reportAvOnComRelease</span><span class="sxs-lookup"><span data-stu-id="a2e2e-121">reportAvOnComRelease</span></span>](reportavoncomrelease-mda.md)  
  
- [<span data-ttu-id="a2e2e-122">invalidVariant</span><span class="sxs-lookup"><span data-stu-id="a2e2e-122">invalidVariant</span></span>](invalidvariant-mda.md)  
  
- [<span data-ttu-id="a2e2e-123">invalidIUnknown</span><span class="sxs-lookup"><span data-stu-id="a2e2e-123">invalidIUnknown</span></span>](invalidiunknown-mda.md)  
  
- [<span data-ttu-id="a2e2e-124">raceOnRCWCleanup</span><span class="sxs-lookup"><span data-stu-id="a2e2e-124">raceOnRCWCleanup</span></span>](raceonrcwcleanup-mda.md)  
  
- [<span data-ttu-id="a2e2e-125">invalidFunctionPointerInDelegate</span><span class="sxs-lookup"><span data-stu-id="a2e2e-125">invalidFunctionPointerInDelegate</span></span>](invalidfunctionpointerindelegate-mda.md)  
  
- [<span data-ttu-id="a2e2e-126">invalidGCHandleCookie</span><span class="sxs-lookup"><span data-stu-id="a2e2e-126">invalidGCHandleCookie</span></span>](invalidgchandlecookie-mda.md)  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="a2e2e-127">Çalışma zamanında etki</span><span class="sxs-lookup"><span data-stu-id="a2e2e-127">Effect on the Runtime</span></span>  

 <span data-ttu-id="a2e2e-128">Bu MDA çalışma zamanının davranışı üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="a2e2e-128">This MDA has no effect on the runtime's behavior.</span></span>  
  
## <a name="output"></a><span data-ttu-id="a2e2e-129">Çıkış</span><span class="sxs-lookup"><span data-stu-id="a2e2e-129">Output</span></span>  

 <span data-ttu-id="a2e2e-130">Kritik hataya neden olan CLR işlevinin adresi, hatanın oluştuğu iş parçacığının KIMLIĞI ve hata kodu.</span><span class="sxs-lookup"><span data-stu-id="a2e2e-130">The address of the CLR function that caused the fatal error, the ID of the thread where the error occurred, and the error code.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="a2e2e-131">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="a2e2e-131">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <fatalExecutionEngineError />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a2e2e-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a2e2e-132">See also</span></span>

- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A>
- <xref:System.Runtime.ConstrainedExecution.Cer>
- [<span data-ttu-id="a2e2e-133">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="a2e2e-133">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
