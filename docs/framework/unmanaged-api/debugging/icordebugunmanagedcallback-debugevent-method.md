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
ms.openlocfilehash: 6ec45004f5dd87983187690a0a4feefb35b05e85
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61748961"
---
# <a name="icordebugunmanagedcallbackdebugevent-method"></a><span data-ttu-id="bbb0b-102">ICorDebugUnmanagedCallback::DebugEvent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bbb0b-102">ICorDebugUnmanagedCallback::DebugEvent Method</span></span>
<span data-ttu-id="bbb0b-103">Hata ayıklayıcı, yerel bir olay harekete bildirir.</span><span class="sxs-lookup"><span data-stu-id="bbb0b-103">Notifies the debugger that a native event has been fired.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bbb0b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bbb0b-104">Syntax</span></span>  
  
```  
HRESULT DebugEvent (  
    [in] LPDEBUG_EVENT  pDebugEvent,  
    [in] BOOL           fOutOfBand  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bbb0b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bbb0b-105">Parameters</span></span>  
 `pDebugEvent`  
 <span data-ttu-id="bbb0b-106">[in] Yerel olay için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="bbb0b-106">[in] A pointer to the native event.</span></span>  
  
 `fOutOfBand`  
 <span data-ttu-id="bbb0b-107">[in] `true`yönetilmeyen bir olay gerçekleşene kadar hata ayıklayıcı çağrıları yönetilen işlem durumu etkileşim mümkün değildir, [Icordebugcontroller::continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md); Aksi takdirde `false`.</span><span class="sxs-lookup"><span data-stu-id="bbb0b-107">[in] `true`, if interaction with the managed process state is impossible after an unmanaged event occurs, until the debugger calls [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md); otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bbb0b-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bbb0b-108">Remarks</span></span>  
 <span data-ttu-id="bbb0b-109">Hatası ayıklanmakta olan iş parçacığı bir Win32 iş parçacığı, arabirimi hata ayıklama Win32 üyelerinin kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="bbb0b-109">If the thread being debugged is a Win32 thread, do not use any members of the Win32 debugging interface.</span></span> <span data-ttu-id="bbb0b-110">Çağırabilirsiniz `ICorDebugController::Continue` Win32 iş parçacığı üzerinde yalnızca ve yalnızca bir bant dışı olay devam.</span><span class="sxs-lookup"><span data-stu-id="bbb0b-110">You can call `ICorDebugController::Continue` only on a Win32 thread and only when continuing past an out-of-band event.</span></span>  
  
 <span data-ttu-id="bbb0b-111">`DebugEvent` Geri çağırma geri çağırmaları standart kurallarını izleyin değil.</span><span class="sxs-lookup"><span data-stu-id="bbb0b-111">The `DebugEvent` callback does not follow the standard rules for callbacks.</span></span> <span data-ttu-id="bbb0b-112">Çağırdığınızda `DebugEvent`işlem ham olması, işletim sistemi hata ayıklama durumunu durduruldu.</span><span class="sxs-lookup"><span data-stu-id="bbb0b-112">When you call `DebugEvent`, the process will be in the raw, OS-debug stopped state.</span></span> <span data-ttu-id="bbb0b-113">İşlem eşitlenmez.</span><span class="sxs-lookup"><span data-stu-id="bbb0b-113">The process will not be synchronized.</span></span> <span data-ttu-id="bbb0b-114">Eşitlenmiş durum iç içe geçmiş diğer sonuçlanabilir yönetilen kodu hakkında bilgi için isteklerini karşılamak için gerekli olduğunda otomatik olarak girer `DebugEvent` geri çağırmalar.</span><span class="sxs-lookup"><span data-stu-id="bbb0b-114">It will automatically enter the synchronized state when necessary to satisfy requests for information about managed code, which may result in other nested `DebugEvent` callbacks.</span></span>  
  
 <span data-ttu-id="bbb0b-115">Çağrı [Icordebugprocess::clearcurrentexception](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-clearcurrentexception-method.md) işlemi devam etmeden önce bir özel durum olayı yok saymak için işlem.</span><span class="sxs-lookup"><span data-stu-id="bbb0b-115">Call [ICorDebugProcess::ClearCurrentException](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-clearcurrentexception-method.md) on the process to ignore an exception event before continuing the process.</span></span> <span data-ttu-id="bbb0b-116">Bu yöntemin çağrılması DBG_CONTINUE DBG_EXCEPTION_NOT_HANDLED yerine devam isteği gönderir ve bant dışı kesme noktaları ve tek adımlı özel durumları otomatik olarak temizler.</span><span class="sxs-lookup"><span data-stu-id="bbb0b-116">Calling this method sends DBG_CONTINUE instead of DBG_EXCEPTION_NOT_HANDLED on the continue request, and automatically clears out-of-band breakpoints and single-step exceptions.</span></span> <span data-ttu-id="bbb0b-117">Bant dışı olayları, hatta ayıklanan uygulamayı durdurulmuş göründüğünde ve bekleyen bir bant dışı olay zaten mevcut olduğunda herhangi bir zamanda gelebilir.</span><span class="sxs-lookup"><span data-stu-id="bbb0b-117">Out-of-band events can come at any time, even when the application being debugged appears stopped and when an outstanding in-band event already exists.</span></span>  
  
 <span data-ttu-id="bbb0b-118">.NET Framework 2.0 sürümünde, hata ayıklayıcının hemen bir bant dışı kesme noktası olayı devam etmelidir.</span><span class="sxs-lookup"><span data-stu-id="bbb0b-118">In the .NET Framework version 2.0, the debugger should immediately continue past an out-of-band breakpoint event.</span></span> <span data-ttu-id="bbb0b-119">Hata ayıklayıcıyı kullanma [Icordebugprocess2::setunmanagedbreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md) ve [Icordebugprocess2::clearunmanagedbreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-clearunmanagedbreakpoint-method.md) eklemek ve kesme noktaları kaldırmak için yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="bbb0b-119">The debugger should be using the [ICorDebugProcess2::SetUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md) and [ICorDebugProcess2::ClearUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-clearunmanagedbreakpoint-method.md) methods to add and remove breakpoints.</span></span> <span data-ttu-id="bbb0b-120">Bu yöntemlerin herhangi bir bant dışı kesme noktası otomatik olarak atlar.</span><span class="sxs-lookup"><span data-stu-id="bbb0b-120">These methods will skip over any out-of-band breakpoints automatically.</span></span> <span data-ttu-id="bbb0b-121">Bu nedenle, dağıtılan yalnızca-bant kesme noktaları yönerge stream'de bir çağrı Win32 gibi zaten olan ham kesme noktaları olmalıdır `DebugBreak` işlevi.</span><span class="sxs-lookup"><span data-stu-id="bbb0b-121">Thus, the only out-of-band breakpoints that get dispatched should be raw breakpoints that are already in the instruction stream, such as a call to the Win32 `DebugBreak` function.</span></span> <span data-ttu-id="bbb0b-122">Kullanmaya çalışmayın `ICorDebugProcess::ClearCurrentException`, [Icordebugprocess::getthreadcontext](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthreadcontext-method.md), [Icordebugprocess::setthreadcontext](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-setthreadcontext-method.md), veya diğer herhangi bir üyesi [hata ayıklama API'si](../../../../docs/framework/unmanaged-api/debugging/index.md).</span><span class="sxs-lookup"><span data-stu-id="bbb0b-122">Do not try to use `ICorDebugProcess::ClearCurrentException`, [ICorDebugProcess::GetThreadContext](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthreadcontext-method.md), [ICorDebugProcess::SetThreadContext](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-setthreadcontext-method.md), or any other member of the [debugging API](../../../../docs/framework/unmanaged-api/debugging/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bbb0b-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bbb0b-123">Requirements</span></span>  
 <span data-ttu-id="bbb0b-124">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bbb0b-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bbb0b-125">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bbb0b-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bbb0b-126">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bbb0b-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bbb0b-127">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bbb0b-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbb0b-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bbb0b-128">See also</span></span>

- [<span data-ttu-id="bbb0b-129">ICorDebugUnmanagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bbb0b-129">ICorDebugUnmanagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-interface.md)
