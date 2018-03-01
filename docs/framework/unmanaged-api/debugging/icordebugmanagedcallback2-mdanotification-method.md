---
title: "ICorDebugManagedCallback2::MDANotification Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugManagedCallback2.MDANotification
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::MDANotification
helpviewer_keywords:
- MDANotification method [.NET Framework debugging]
- ICorDebugManagedCallback2::MDANotification method [.NET Framework debugging]
ms.assetid: 93f79627-bd31-4f4f-b95d-46a032a52fe4
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5a58e286feb3387557d0a37c463f2af67abf8cc5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallback2mdanotification-method"></a><span data-ttu-id="3a457-102">ICorDebugManagedCallback2::MDANotification Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3a457-102">ICorDebugManagedCallback2::MDANotification Method</span></span>
<span data-ttu-id="3a457-103">Kod yürütmeyi ayıklanacak uygulamasında yönetilen hata ayıklama Yardımcısı (MDA) karşılaştı bildirim sağlar.</span><span class="sxs-lookup"><span data-stu-id="3a457-103">Provides notification that code execution has encountered a managed debugging assistant (MDA) in the application that is being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a457-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3a457-104">Syntax</span></span>  
  
```  
HRESULT MDANotification(  
    [in] ICorDebugController  *pController,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugMDA         *pMDA  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3a457-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3a457-105">Parameters</span></span>  
 `pController`  
 <span data-ttu-id="3a457-106">[in] Bir işlem sunan Icordebugcontroller arabirimi veya MDA oluştuğu uygulama etki alanı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="3a457-106">[in] A pointer to an ICorDebugController interface that exposes the process or application domain in which the MDA occurred.</span></span>  
  
 <span data-ttu-id="3a457-107">Her zaman bir belirlenmesi için arabirimi sorgulayabilirsiniz olsa da bir hata ayıklayıcısı bir işlem veya bir uygulama etki alanı denetleyici olup olmadığına dair varsayımlar yapmamalısınız.</span><span class="sxs-lookup"><span data-stu-id="3a457-107">A debugger should not make any assumptions about whether the controller is a process or an application domain, although it can always query the interface to make a determination.</span></span>  
  
 `pThread`  
 <span data-ttu-id="3a457-108">[in] Hata ayıklama olayın oluştuğu yönetilen iş parçacığı kullanıma sunan bir Icordebugthread arabirimi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="3a457-108">[in] A pointer to an ICorDebugThread interface that exposes the managed thread on which the debug event occurred.</span></span>  
  
 <span data-ttu-id="3a457-109">MDA yönetilmeyen üzerinde oluştuysa iş parçacığı, değeri `pThread` null olur.</span><span class="sxs-lookup"><span data-stu-id="3a457-109">If the MDA occurred on an unmanaged thread, the value of `pThread` will be null.</span></span>  
  
 <span data-ttu-id="3a457-110">İşletim sistemi (OS) iş parçacığı kimliği MDA nesnesinin kendisi almanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3a457-110">You must get the operating system (OS) thread ID from the MDA object itself.</span></span>  
  
 `pMDA`  
 <span data-ttu-id="3a457-111">[in] Bir işaretçi bir [Icordebugmda](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md) MDA bilgi kullanıma sunan arabirim.</span><span class="sxs-lookup"><span data-stu-id="3a457-111">[in] A pointer to an [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md) interface that exposes the MDA information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3a457-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3a457-112">Remarks</span></span>  
 <span data-ttu-id="3a457-113">Bir MDA buluşsal bir uyarıdır ve arama dışında herhangi bir açık hata ayıklayıcı eylem gerektirmez [Icordebugcontroller::continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) ayıklanacak uygulamanın yürütülmesini sürdürmek için.</span><span class="sxs-lookup"><span data-stu-id="3a457-113">An MDA is a heuristic warning and does not require any explicit debugger action except for calling [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) to resume execution of the application that is being debugged.</span></span>  
  
 <span data-ttu-id="3a457-114">Ortak dil çalışma zamanı (CLR) Mda'lar tetiklenir ve herhangi bir noktada verilen tüm MDA hangi verilerin bulunduğu belirleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3a457-114">The common language runtime (CLR) can determine which MDAs are fired and which data is in any given MDA at any point.</span></span> <span data-ttu-id="3a457-115">Bu nedenle, hata ayıklayıcıları belirli MDA desenleri gerektiren herhangi bir işlevsellik oluşturup değil.</span><span class="sxs-lookup"><span data-stu-id="3a457-115">Therefore, debuggers should not build any functionality requiring specific MDA patterns.</span></span>  
  
 <span data-ttu-id="3a457-116">Mda'lar sıraya alındı ve kısa süre içinde MDA karşılaştı sonra gönderilir.</span><span class="sxs-lookup"><span data-stu-id="3a457-116">MDAs may be queued and fired shortly after the MDA is encountered.</span></span> <span data-ttu-id="3a457-117">Çalışma zamanı bu karşılaştığında MDA tetikleme yerine MDA tetikleme için güvenli bir noktası ulaşana kadar bekleyin gerekiyorsa, bu durum oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="3a457-117">This could happen if the runtime needs to wait until it reaches a safe point for firing the MDA, instead of firing the MDA when it encounters it.</span></span> <span data-ttu-id="3a457-118">Ayrıca, çalışma zamanı numarasında sıraya alınan geri aramalar ("Ekle" olay işlem için benzer) tek bir dizi Mda'lar yangın anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="3a457-118">It also means that the runtime may fire a number of MDAs in a single set of queued callbacks (similar to an "attach" event operation).</span></span>  
  
 <span data-ttu-id="3a457-119">Bir hata ayıklayıcısı referansı serbest bırakmalısınız bir `ICorDebugMDA` döndürme hemen sonra örneği `MDANotification` bir MDA tarafından tüketilen bellek geri dönüştürmek CLR izin vermek için geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="3a457-119">A debugger should release the reference to an `ICorDebugMDA` instance immediately after returning from the `MDANotification` callback, to allow the CLR to recycle the memory consumed by an MDA.</span></span> <span data-ttu-id="3a457-120">Birçok Mda'lar tetikleme varsa örnek serbest performansını artırabilir.</span><span class="sxs-lookup"><span data-stu-id="3a457-120">Releasing the instance may improve performance if many MDAs are firing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3a457-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3a457-121">Requirements</span></span>  
 <span data-ttu-id="3a457-122">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3a457-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a457-123">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3a457-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3a457-124">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3a457-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3a457-125">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a457-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a457-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3a457-126">See Also</span></span>  
 [<span data-ttu-id="3a457-127">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="3a457-127">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="3a457-128">ICorDebugManagedCallback2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3a457-128">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 [<span data-ttu-id="3a457-129">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3a457-129">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
