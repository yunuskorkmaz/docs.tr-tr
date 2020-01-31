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
ms.openlocfilehash: cb52150a17c9ec8f4bbc25c13b85bce56b221eeb
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791187"
---
# <a name="icordebugunmanagedcallbackdebugevent-method"></a><span data-ttu-id="2eb45-102">ICorDebugUnmanagedCallback::DebugEvent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2eb45-102">ICorDebugUnmanagedCallback::DebugEvent Method</span></span>
<span data-ttu-id="2eb45-103">Hata ayıklayıcıyı yerel bir olayın harekete geçirildiğinde bildirir.</span><span class="sxs-lookup"><span data-stu-id="2eb45-103">Notifies the debugger that a native event has been fired.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2eb45-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2eb45-104">Syntax</span></span>  
  
```cpp  
HRESULT DebugEvent (  
    [in] LPDEBUG_EVENT  pDebugEvent,  
    [in] BOOL           fOutOfBand  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2eb45-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2eb45-105">Parameters</span></span>  
 `pDebugEvent`  
 <span data-ttu-id="2eb45-106">'ndaki Yerel olaya yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="2eb45-106">[in] A pointer to the native event.</span></span>  
  
 `fOutOfBand`  
 <span data-ttu-id="2eb45-107">[in] `true`, yönetilmeyen bir olay oluştuktan sonra yönetilen işlem durumu ile etkileşim varsa, hata ayıklayıcı [ICorDebugController:: Continue](icordebugcontroller-continue-method.md)öğesine çağrı yapana kadar olanaksızdır; Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="2eb45-107">[in] `true`, if interaction with the managed process state is impossible after an unmanaged event occurs, until the debugger calls [ICorDebugController::Continue](icordebugcontroller-continue-method.md); otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2eb45-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2eb45-108">Remarks</span></span>  
 <span data-ttu-id="2eb45-109">Hata ayıklanmakta olan iş parçacığı bir Win32 iş parçacığı ise, Win32 hata ayıklama arabiriminin herhangi bir üyesini kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="2eb45-109">If the thread being debugged is a Win32 thread, do not use any members of the Win32 debugging interface.</span></span> <span data-ttu-id="2eb45-110">Yalnızca bir Win32 iş parçacığı üzerinde `ICorDebugController::Continue` ve yalnızca bant dışı bir olayı geçmiş olduğunda çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2eb45-110">You can call `ICorDebugController::Continue` only on a Win32 thread and only when continuing past an out-of-band event.</span></span>  
  
 <span data-ttu-id="2eb45-111">`DebugEvent` geri çağırması geri çağırmalar için standart kuralları uygulamaz.</span><span class="sxs-lookup"><span data-stu-id="2eb45-111">The `DebugEvent` callback does not follow the standard rules for callbacks.</span></span> <span data-ttu-id="2eb45-112">`DebugEvent`çağırdığınızda, işlem ham, işletim sistemi-hata ayıklama durdurulmuş durumunda olur.</span><span class="sxs-lookup"><span data-stu-id="2eb45-112">When you call `DebugEvent`, the process will be in the raw, OS-debug stopped state.</span></span> <span data-ttu-id="2eb45-113">İşlem eşitlenmez.</span><span class="sxs-lookup"><span data-stu-id="2eb45-113">The process will not be synchronized.</span></span> <span data-ttu-id="2eb45-114">Yönetilen kod hakkında bilgi isteklerini karşılamak için gerektiğinde otomatik olarak eşitlenmiş duruma girer, bu da diğer iç içe geçmiş `DebugEvent` geri çağırmalar oluşmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="2eb45-114">It will automatically enter the synchronized state when necessary to satisfy requests for information about managed code, which may result in other nested `DebugEvent` callbacks.</span></span>  
  
 <span data-ttu-id="2eb45-115">İşleme devam etmeden önce bir özel durum olayını yok saymak için [ICorDebugProcess:: ClearCurrentException](icordebugprocess-clearcurrentexception-method.md) ' i çağırın.</span><span class="sxs-lookup"><span data-stu-id="2eb45-115">Call [ICorDebugProcess::ClearCurrentException](icordebugprocess-clearcurrentexception-method.md) on the process to ignore an exception event before continuing the process.</span></span> <span data-ttu-id="2eb45-116">Bu yöntemin çağrılması devam isteğinde DBG_EXCEPTION_NOT_HANDLED yerine DBG_CONTINUE gönderir ve bant dışı kesme noktalarını ve tek adımlı özel durumları otomatik olarak temizler.</span><span class="sxs-lookup"><span data-stu-id="2eb45-116">Calling this method sends DBG_CONTINUE instead of DBG_EXCEPTION_NOT_HANDLED on the continue request, and automatically clears out-of-band breakpoints and single-step exceptions.</span></span> <span data-ttu-id="2eb45-117">Bant dışı olaylar herhangi bir zamanda, hata ayıklamakta olan uygulama durdurulduğunda ve bekleyen bant içi bir olay zaten mevcut olduğunda bile gelebilir.</span><span class="sxs-lookup"><span data-stu-id="2eb45-117">Out-of-band events can come at any time, even when the application being debugged appears stopped and when an outstanding in-band event already exists.</span></span>  
  
 <span data-ttu-id="2eb45-118">.NET Framework sürüm 2,0 ' de, hata ayıklayıcı hemen bir bant dışı kesme noktası olayını geçmiş olarak devam etmelidir.</span><span class="sxs-lookup"><span data-stu-id="2eb45-118">In the .NET Framework version 2.0, the debugger should immediately continue past an out-of-band breakpoint event.</span></span> <span data-ttu-id="2eb45-119">Hata ayıklayıcı, kesme noktaları eklemek ve kaldırmak için [ICorDebugProcess2:: SetUnmanagedBreakpoint](icordebugprocess2-setunmanagedbreakpoint-method.md) ve [ICorDebugProcess2:: ClearUnmanagedBreakpoint](icordebugprocess2-clearunmanagedbreakpoint-method.md) yöntemlerini kullanıyor olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2eb45-119">The debugger should be using the [ICorDebugProcess2::SetUnmanagedBreakpoint](icordebugprocess2-setunmanagedbreakpoint-method.md) and [ICorDebugProcess2::ClearUnmanagedBreakpoint](icordebugprocess2-clearunmanagedbreakpoint-method.md) methods to add and remove breakpoints.</span></span> <span data-ttu-id="2eb45-120">Bu yöntemler, tüm bant dışı kesme noktalarını otomatik olarak atlar.</span><span class="sxs-lookup"><span data-stu-id="2eb45-120">These methods will skip over any out-of-band breakpoints automatically.</span></span> <span data-ttu-id="2eb45-121">Bu nedenle, gönderilen tek bant dışı kesme noktaları, bir Win32 `DebugBreak` işlevine yapılan çağrı gibi yönerge akışında zaten bulunan ham kesme noktaları olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2eb45-121">Thus, the only out-of-band breakpoints that get dispatched should be raw breakpoints that are already in the instruction stream, such as a call to the Win32 `DebugBreak` function.</span></span> <span data-ttu-id="2eb45-122">`ICorDebugProcess::ClearCurrentException`, [ICorDebugProcess:: GetThreadContext](icordebugprocess-getthreadcontext-method.md), [ICorDebugProcess:: SetThreadContext](icordebugprocess-setthreadcontext-method.md)veya [hata ayıklama API](index.md)'sinin başka bir üyesini kullanmayı denemeyin.</span><span class="sxs-lookup"><span data-stu-id="2eb45-122">Do not try to use `ICorDebugProcess::ClearCurrentException`, [ICorDebugProcess::GetThreadContext](icordebugprocess-getthreadcontext-method.md), [ICorDebugProcess::SetThreadContext](icordebugprocess-setthreadcontext-method.md), or any other member of the [debugging API](index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2eb45-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2eb45-123">Requirements</span></span>  
 <span data-ttu-id="2eb45-124">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2eb45-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2eb45-125">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="2eb45-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2eb45-126">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="2eb45-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2eb45-127">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2eb45-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2eb45-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2eb45-128">See also</span></span>

- [<span data-ttu-id="2eb45-129">ICorDebugUnmanagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2eb45-129">ICorDebugUnmanagedCallback Interface</span></span>](icordebugunmanagedcallback-interface.md)
