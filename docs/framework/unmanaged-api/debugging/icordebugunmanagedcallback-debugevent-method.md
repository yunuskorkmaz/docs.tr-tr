---
title: ICorDebugUnmanagedCallback::DebugEvent Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugUnmanagedCallback.DebugEvent
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugUnmanagedCallback::DebugEvent
helpviewer_keywords:
- DebugEvent method [.NET Framework debugging]
- ICorDebugUnmanagedCallback::DebugEvent method [.NET Framework debugging]
ms.assetid: be9cab04-65ec-44d5-a39a-f90709fdd043
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 51ccc7b1b50613f0d2b44a9e101314128782c412
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423136"
---
# <a name="icordebugunmanagedcallbackdebugevent-method"></a><span data-ttu-id="b6c2c-102">ICorDebugUnmanagedCallback::DebugEvent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b6c2c-102">ICorDebugUnmanagedCallback::DebugEvent Method</span></span>
<span data-ttu-id="b6c2c-103">Hata ayıklayıcı yerel olay harekete olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="b6c2c-103">Notifies the debugger that a native event has been fired.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6c2c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b6c2c-104">Syntax</span></span>  
  
```  
HRESULT DebugEvent (  
    [in] LPDEBUG_EVENT  pDebugEvent,  
    [in] BOOL           fOutOfBand  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b6c2c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b6c2c-105">Parameters</span></span>  
 `pDebugEvent`  
 <span data-ttu-id="b6c2c-106">[in] Yerel olay için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b6c2c-106">[in] A pointer to the native event.</span></span>  
  
 `fOutOfBand`  
 <span data-ttu-id="b6c2c-107">[in] `true`, yönetilmeyen bir olay gerçekleşene kadar hata ayıklayıcı çağrıları yönetilen işlem durumu ile etkileşimi mümkün değildir, [Icordebugcontroller::continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md); Aksi halde, `false`.</span><span class="sxs-lookup"><span data-stu-id="b6c2c-107">[in] `true`, if interaction with the managed process state is impossible after an unmanaged event occurs, until the debugger calls [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md); otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b6c2c-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b6c2c-108">Remarks</span></span>  
 <span data-ttu-id="b6c2c-109">Ayıklanacak iş parçacığı bir Win32 iş parçacığı ise arabirimi hata ayıklama tüm üyeleri Win32 kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="b6c2c-109">If the thread being debugged is a Win32 thread, do not use any members of the Win32 debugging interface.</span></span> <span data-ttu-id="b6c2c-110">Çağırabilirsiniz `ICorDebugController::Continue` yalnızca bir iş parçacığında Win32 ve yalnızca bir bant dışı olay etmeden.</span><span class="sxs-lookup"><span data-stu-id="b6c2c-110">You can call `ICorDebugController::Continue` only on a Win32 thread and only when continuing past an out-of-band event.</span></span>  
  
 <span data-ttu-id="b6c2c-111">`DebugEvent` Geri çağırma geri aramalar için standart kuralları izleyin değil.</span><span class="sxs-lookup"><span data-stu-id="b6c2c-111">The `DebugEvent` callback does not follow the standard rules for callbacks.</span></span> <span data-ttu-id="b6c2c-112">Çağırdığınızda `DebugEvent`işlemi ham olacaktır, işletim sistemi hata ayıklama durduruldu durumu.</span><span class="sxs-lookup"><span data-stu-id="b6c2c-112">When you call `DebugEvent`, the process will be in the raw, OS-debug stopped state.</span></span> <span data-ttu-id="b6c2c-113">İşlem eşitlenmeyecek.</span><span class="sxs-lookup"><span data-stu-id="b6c2c-113">The process will not be synchronized.</span></span> <span data-ttu-id="b6c2c-114">Otomatik olarak diğer iç içe geçmiş sonuçlanabilir yönetilen kodu hakkında bilgi için istekleri karşılamak için gerekli olduğunda eşitlenmiş durumuna girer `DebugEvent` geri aramalar.</span><span class="sxs-lookup"><span data-stu-id="b6c2c-114">It will automatically enter the synchronized state when necessary to satisfy requests for information about managed code, which may result in other nested `DebugEvent` callbacks.</span></span>  
  
 <span data-ttu-id="b6c2c-115">Çağrı [Icordebugprocess::clearcurrentexception](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-clearcurrentexception-method.md) işleme işlemi devam etmeden önce bir özel durum olayı yoksay.</span><span class="sxs-lookup"><span data-stu-id="b6c2c-115">Call [ICorDebugProcess::ClearCurrentException](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-clearcurrentexception-method.md) on the process to ignore an exception event before continuing the process.</span></span> <span data-ttu-id="b6c2c-116">Bu yöntemi çağırmadan DBG_EXCEPTION_NOT_HANDLED yerine DBG_CONTINUE devam isteği gönderir ve bant dışı kesme noktaları ve tek adımlı özel durumları otomatik olarak temizler.</span><span class="sxs-lookup"><span data-stu-id="b6c2c-116">Calling this method sends DBG_CONTINUE instead of DBG_EXCEPTION_NOT_HANDLED on the continue request, and automatically clears out-of-band breakpoints and single-step exceptions.</span></span> <span data-ttu-id="b6c2c-117">Bant dışı olayları herhangi bir zamanda bile ayıklanacak uygulama durdurulmuş görüntülendiğinde ve bekleyen bant dışı olaya zaten mevcut olduğunda gelebilir.</span><span class="sxs-lookup"><span data-stu-id="b6c2c-117">Out-of-band events can come at any time, even when the application being debugged appears stopped and when an outstanding in-band event already exists.</span></span>  
  
 <span data-ttu-id="b6c2c-118">.NET Framework sürüm 2. 0'da, hata ayıklayıcı hemen bir bant dışı kesme noktası olay devam etmelidir.</span><span class="sxs-lookup"><span data-stu-id="b6c2c-118">In the .NET Framework version 2.0, the debugger should immediately continue past an out-of-band breakpoint event.</span></span> <span data-ttu-id="b6c2c-119">Hata ayıklayıcıyı kullanma [Icordebugprocess2::setunmanagedbreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md) ve [Icordebugprocess2::clearunmanagedbreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-clearunmanagedbreakpoint-method.md) yöntemleri eklemek ve kesme noktaları kaldırmak için.</span><span class="sxs-lookup"><span data-stu-id="b6c2c-119">The debugger should be using the [ICorDebugProcess2::SetUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md) and [ICorDebugProcess2::ClearUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-clearunmanagedbreakpoint-method.md) methods to add and remove breakpoints.</span></span> <span data-ttu-id="b6c2c-120">Bu yöntemler tüm bant dışı kesme noktaları otomatik olarak atlar.</span><span class="sxs-lookup"><span data-stu-id="b6c2c-120">These methods will skip over any out-of-band breakpoints automatically.</span></span> <span data-ttu-id="b6c2c-121">Bu nedenle, dağıtılan yalnızca-bant kesme noktaları Win32 çağrısı gibi yönerge akış zaten bulunan ham kesme noktaları olmalıdır `DebugBreak` işlevi.</span><span class="sxs-lookup"><span data-stu-id="b6c2c-121">Thus, the only out-of-band breakpoints that get dispatched should be raw breakpoints that are already in the instruction stream, such as a call to the Win32 `DebugBreak` function.</span></span> <span data-ttu-id="b6c2c-122">Kullanmaya çalışmayın `ICorDebugProcess::ClearCurrentException`, [Icordebugprocess::getthreadcontext](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthreadcontext-method.md), [Icordebugprocess::setthreadcontext](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-setthreadcontext-method.md), veya diğer herhangi bir üyenin [hata ayıklama API'si](../../../../docs/framework/unmanaged-api/debugging/index.md).</span><span class="sxs-lookup"><span data-stu-id="b6c2c-122">Do not try to use `ICorDebugProcess::ClearCurrentException`, [ICorDebugProcess::GetThreadContext](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthreadcontext-method.md), [ICorDebugProcess::SetThreadContext](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-setthreadcontext-method.md), or any other member of the [debugging API](../../../../docs/framework/unmanaged-api/debugging/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6c2c-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b6c2c-123">Requirements</span></span>  
 <span data-ttu-id="b6c2c-124">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b6c2c-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6c2c-125">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b6c2c-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b6c2c-126">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b6c2c-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b6c2c-127">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6c2c-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6c2c-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b6c2c-128">See Also</span></span>  
 [<span data-ttu-id="b6c2c-129">ICorDebugUnmanagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b6c2c-129">ICorDebugUnmanagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-interface.md)
