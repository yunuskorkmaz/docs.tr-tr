---
title: ICorDebugManagedCallback2::MDANotification Yöntemi
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4011932af6f4b058906c19566e4c1abe96b409db
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67762087"
---
# <a name="icordebugmanagedcallback2mdanotification-method"></a><span data-ttu-id="38964-102">ICorDebugManagedCallback2::MDANotification Yöntemi</span><span class="sxs-lookup"><span data-stu-id="38964-102">ICorDebugManagedCallback2::MDANotification Method</span></span>
<span data-ttu-id="38964-103">Kod yürütmeyi ayıklanmakta olan uygulamada yönetilen hata ayıklama Yardımcısı (MDA) karşılaştı bildirim sağlar.</span><span class="sxs-lookup"><span data-stu-id="38964-103">Provides notification that code execution has encountered a managed debugging assistant (MDA) in the application that is being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38964-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="38964-104">Syntax</span></span>  
  
```cpp  
HRESULT MDANotification(  
    [in] ICorDebugController  *pController,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugMDA         *pMDA  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="38964-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="38964-105">Parameters</span></span>  
 `pController`  
 <span data-ttu-id="38964-106">[in] Bir işlem sunan Icordebugcontroller arabirimi veya MDA gerçekleştiği uygulama etki alanı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="38964-106">[in] A pointer to an ICorDebugController interface that exposes the process or application domain in which the MDA occurred.</span></span>  
  
 <span data-ttu-id="38964-107">Her zaman bir bulguyu arabirimi sorgulayabilirsiniz ancak bir hata ayıklayıcı bir işlem veya bir uygulama etki alanı denetleyicisi olup olmadığı hakkında varsayımlar yapmamalısınız.</span><span class="sxs-lookup"><span data-stu-id="38964-107">A debugger should not make any assumptions about whether the controller is a process or an application domain, although it can always query the interface to make a determination.</span></span>  
  
 `pThread`  
 <span data-ttu-id="38964-108">[in] Yönetilen iş parçacığı hata ayıklama olayın gerçekleştiği kullanıma sunan bir Icordebugthread arabirimi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="38964-108">[in] A pointer to an ICorDebugThread interface that exposes the managed thread on which the debug event occurred.</span></span>  
  
 <span data-ttu-id="38964-109">MDA yönetilmeyen üzerinde oluştuysa iş parçacığı, değerini `pThread` null olacaktır.</span><span class="sxs-lookup"><span data-stu-id="38964-109">If the MDA occurred on an unmanaged thread, the value of `pThread` will be null.</span></span>  
  
 <span data-ttu-id="38964-110">İşletim sistemi (OS) iş parçacığı kimliği MDA nesnenin kendisini almanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="38964-110">You must get the operating system (OS) thread ID from the MDA object itself.</span></span>  
  
 `pMDA`  
 <span data-ttu-id="38964-111">[in] Bir işaretçi bir [Icordebugmda](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md) MDA bilgileri kullanıma sunan arabirim.</span><span class="sxs-lookup"><span data-stu-id="38964-111">[in] A pointer to an [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md) interface that exposes the MDA information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="38964-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="38964-112">Remarks</span></span>  
 <span data-ttu-id="38964-113">Bir MDA buluşsal bir uyarıdır ve arama dışında herhangi bir açık hata ayıklayıcı eylem gerektirmeyen [Icordebugcontroller::continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) ayıklanmakta olan uygulamanın yürütülmesini sürdürmek için.</span><span class="sxs-lookup"><span data-stu-id="38964-113">An MDA is a heuristic warning and does not require any explicit debugger action except for calling [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) to resume execution of the application that is being debugged.</span></span>  
  
 <span data-ttu-id="38964-114">Ortak dil çalışma zamanı (CLR) Mda'leri tetiklenir ve herhangi belirli MDA herhangi bir noktada hangi verilerin bulunduğu belirleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="38964-114">The common language runtime (CLR) can determine which MDAs are fired and which data is in any given MDA at any point.</span></span> <span data-ttu-id="38964-115">Bu nedenle, hata ayıklayıcıları belirli MDA desenleri gerektiren herhangi bir işlevsellik tasarlanmamış.</span><span class="sxs-lookup"><span data-stu-id="38964-115">Therefore, debuggers should not build any functionality requiring specific MDA patterns.</span></span>  
  
 <span data-ttu-id="38964-116">Mda'leri kuyruğa alınır ve kısa süre içinde MDA karşılaşıldıktan sonra gönderilir.</span><span class="sxs-lookup"><span data-stu-id="38964-116">MDAs may be queued and fired shortly after the MDA is encountered.</span></span> <span data-ttu-id="38964-117">Çalışma zamanı bu karşılaştığında MDA tetikleme yerine MDA tetikleme için güvenli bir noktadan ulaşana kadar beklenecek gerektiriyorsa Bu durum gerçekleşebilir.</span><span class="sxs-lookup"><span data-stu-id="38964-117">This could happen if the runtime needs to wait until it reaches a safe point for firing the MDA, instead of firing the MDA when it encounters it.</span></span> <span data-ttu-id="38964-118">Ayrıca, çalışma zamanı sıraya alınan geri çağırmalar (bir "ekleme" olay işleme benzer) tek bir kümedeki Mda'leri birkaç yangın anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="38964-118">It also means that the runtime may fire a number of MDAs in a single set of queued callbacks (similar to an "attach" event operation).</span></span>  
  
 <span data-ttu-id="38964-119">Başvuru için hata ayıklayıcı serbest bırakmalısınız bir `ICorDebugMDA` döndürme hemen sonra örnek `MDANotification` bir MDA tarafından kullanılan belleği geri dönüştürmek CLR izin vermek için geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="38964-119">A debugger should release the reference to an `ICorDebugMDA` instance immediately after returning from the `MDANotification` callback, to allow the CLR to recycle the memory consumed by an MDA.</span></span> <span data-ttu-id="38964-120">Birçok Mda'leri tetikleme, örneği serbest performansını artırabilir.</span><span class="sxs-lookup"><span data-stu-id="38964-120">Releasing the instance may improve performance if many MDAs are firing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38964-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="38964-121">Requirements</span></span>  
 <span data-ttu-id="38964-122">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="38964-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38964-123">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="38964-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="38964-124">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="38964-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="38964-125">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38964-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38964-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="38964-126">See also</span></span>

- [<span data-ttu-id="38964-127">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="38964-127">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="38964-128">ICorDebugManagedCallback2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="38964-128">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="38964-129">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="38964-129">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
