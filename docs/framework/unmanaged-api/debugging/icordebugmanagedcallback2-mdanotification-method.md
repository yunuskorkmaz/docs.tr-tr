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
ms.openlocfilehash: ab3819d5c33f090fda1ca9c3dccb5d08ab8f84cc
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131454"
---
# <a name="icordebugmanagedcallback2mdanotification-method"></a><span data-ttu-id="bc66b-102">ICorDebugManagedCallback2::MDANotification Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bc66b-102">ICorDebugManagedCallback2::MDANotification Method</span></span>
<span data-ttu-id="bc66b-103">Kod yürütmenin ayıklanmakta olan uygulamada yönetilen hata ayıklama Yardımcısı (MDA) ile karşılaştığından bildirim sağlar.</span><span class="sxs-lookup"><span data-stu-id="bc66b-103">Provides notification that code execution has encountered a managed debugging assistant (MDA) in the application that is being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc66b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bc66b-104">Syntax</span></span>  
  
```cpp  
HRESULT MDANotification(  
    [in] ICorDebugController  *pController,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugMDA         *pMDA  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bc66b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bc66b-105">Parameters</span></span>  
 `pController`  
 <span data-ttu-id="bc66b-106">'ndaki ICorDebugController arabirimine, MDA 'ın üzerinde oluştuğu işlem veya uygulama etki alanını sunan bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="bc66b-106">[in] A pointer to an ICorDebugController interface that exposes the process or application domain in which the MDA occurred.</span></span>  
  
 <span data-ttu-id="bc66b-107">Hata ayıklayıcı, denetleyicinin bir işlem veya uygulama etki alanı olup olmadığı konusunda herhangi bir varsayımda bulunmamalıdır, ancak her zaman bir belirleme yapmak üzere arabirimi sorgulayabilir.</span><span class="sxs-lookup"><span data-stu-id="bc66b-107">A debugger should not make any assumptions about whether the controller is a process or an application domain, although it can always query the interface to make a determination.</span></span>  
  
 `pThread`  
 <span data-ttu-id="bc66b-108">'ndaki Hata ayıklama olayının gerçekleştiği yönetilen iş parçacığını sunan ICorDebugThread arabirimine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="bc66b-108">[in] A pointer to an ICorDebugThread interface that exposes the managed thread on which the debug event occurred.</span></span>  
  
 <span data-ttu-id="bc66b-109">Bir yönetilmeyen iş parçacığında MDA oluştuysa, `pThread` değeri null olur.</span><span class="sxs-lookup"><span data-stu-id="bc66b-109">If the MDA occurred on an unmanaged thread, the value of `pThread` will be null.</span></span>  
  
 <span data-ttu-id="bc66b-110">MDA nesnesinden işletim sistemi (OS) iş parçacığı KIMLIĞI almalısınız.</span><span class="sxs-lookup"><span data-stu-id="bc66b-110">You must get the operating system (OS) thread ID from the MDA object itself.</span></span>  
  
 `pMDA`  
 <span data-ttu-id="bc66b-111">'ndaki MDA bilgisini sunan bir [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md) arabirimine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="bc66b-111">[in] A pointer to an [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md) interface that exposes the MDA information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bc66b-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bc66b-112">Remarks</span></span>  
 <span data-ttu-id="bc66b-113">Bir MDA, buluşsal bir uyarıdır ve [ICorDebugController::](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) ' i çağırmak dışında herhangi bir açık hata ayıklayıcı eylemi gerektirmez ve hata ayıklanmakta olan uygulamanın yürütülmesini sürdürmek Için devam edin.</span><span class="sxs-lookup"><span data-stu-id="bc66b-113">An MDA is a heuristic warning and does not require any explicit debugger action except for calling [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) to resume execution of the application that is being debugged.</span></span>  
  
 <span data-ttu-id="bc66b-114">Ortak dil çalışma zamanı (CLR) hangi Mdaların tetikleyeceğini ve hangi herhangi bir MDA hangi verilerin herhangi bir noktada olduğunu tespit edebilir.</span><span class="sxs-lookup"><span data-stu-id="bc66b-114">The common language runtime (CLR) can determine which MDAs are fired and which data is in any given MDA at any point.</span></span> <span data-ttu-id="bc66b-115">Bu nedenle, hata ayıklayıcılar, belirli MDA desenleri gerektiren herhangi bir işlev derlenmemelidir.</span><span class="sxs-lookup"><span data-stu-id="bc66b-115">Therefore, debuggers should not build any functionality requiring specific MDA patterns.</span></span>  
  
 <span data-ttu-id="bc66b-116">MDAs 'ler kuyruğa alınmış ve kısa bir süre sonra da tetiklenebilir.</span><span class="sxs-lookup"><span data-stu-id="bc66b-116">MDAs may be queued and fired shortly after the MDA is encountered.</span></span> <span data-ttu-id="bc66b-117">Bunun nedeni, çalışma zamanının mda ' ı tetiklemenin bir güvenli noktaya ulaşıncaya kadar beklemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="bc66b-117">This could happen if the runtime needs to wait until it reaches a safe point for firing the MDA, instead of firing the MDA when it encounters it.</span></span> <span data-ttu-id="bc66b-118">Ayrıca, çalışma zamanının tek bir sıraya alınmış geri çağırmalar kümesinde ("iliştirme" olay işlemine benzer) çok sayıda MDAs tetikleneceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="bc66b-118">It also means that the runtime may fire a number of MDAs in a single set of queued callbacks (similar to an "attach" event operation).</span></span>  
  
 <span data-ttu-id="bc66b-119">Hata ayıklayıcı, CLR 'nin bir MDA tarafından tüketilen belleği geri dönüştürmesini sağlamak için `MDANotification` geri çağrısından geri dönmeden hemen sonra bir `ICorDebugMDA` örneğine başvuruyu serbest bırakmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bc66b-119">A debugger should release the reference to an `ICorDebugMDA` instance immediately after returning from the `MDANotification` callback, to allow the CLR to recycle the memory consumed by an MDA.</span></span> <span data-ttu-id="bc66b-120">Birçok MDAs tetikleme durumunda örneği serbest bırakmak performansı iyileştirebilir.</span><span class="sxs-lookup"><span data-stu-id="bc66b-120">Releasing the instance may improve performance if many MDAs are firing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bc66b-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bc66b-121">Requirements</span></span>  
 <span data-ttu-id="bc66b-122">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bc66b-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bc66b-123">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="bc66b-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bc66b-124">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="bc66b-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bc66b-125">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bc66b-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc66b-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bc66b-126">See also</span></span>

- [<span data-ttu-id="bc66b-127">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="bc66b-127">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="bc66b-128">ICorDebugManagedCallback2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bc66b-128">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="bc66b-129">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bc66b-129">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
