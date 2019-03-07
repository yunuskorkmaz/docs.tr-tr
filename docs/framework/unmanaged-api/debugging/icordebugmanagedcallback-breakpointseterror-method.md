---
title: ICorDebugManagedCallback::BreakpointSetError Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.BreakpointSetError
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::BreakpointSetError
helpviewer_keywords:
- BreakpointSetError method [.NET Framework debugging]
- ICorDebugManagedCallback::BreakpointSetError method [.NET Framework debugging]
ms.assetid: f2b773a4-c4d0-429c-9717-51d6e2ed86af
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0baecc56df18a8ce346f5c4a9f52dd4006583867
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57476405"
---
# <a name="icordebugmanagedcallbackbreakpointseterror-method"></a><span data-ttu-id="a20b3-102">ICorDebugManagedCallback::BreakpointSetError Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a20b3-102">ICorDebugManagedCallback::BreakpointSetError Method</span></span>
<span data-ttu-id="a20b3-103">Hata ayıklayıcı ortak dil çalışma zamanı öncesinde bir işlev yalnızca derlenmiş zamanında (JIT) ayarlanan bir kesme noktası doğru şekilde bağlanamıyor olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="a20b3-103">Notifies the debugger that the common language runtime was unable to accurately bind a breakpoint that was set before a function was just-in-time (JIT) compiled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a20b3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a20b3-104">Syntax</span></span>  
  
```  
HRESULT BreakpointSetError (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] ICorDebugBreakpoint *pBreakpoint,  
    [in] DWORD                dwError  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a20b3-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a20b3-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="a20b3-106">[in] İlişkisiz bir kesme noktası içeren uygulama etki alanını temsil eden bir Icordebugappdomain nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="a20b3-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contains the unbound breakpoint.</span></span>  
  
 `pThread`  
 <span data-ttu-id="a20b3-107">[in] İlişkisiz bir kesme noktası içeren iş parçacığını temsil eden bir Icordebugthread nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="a20b3-107">[in] A pointer to an ICorDebugThread object that represents the thread that contains the unbound breakpoint.</span></span>  
  
 `pBreakpoint`  
 <span data-ttu-id="a20b3-108">[in] İlişkisiz kesme noktasını temsil eden bir Icordebugbreakpoint nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="a20b3-108">[in] A pointer to an ICorDebugBreakpoint object that represents the unbound breakpoint.</span></span>  
  
 `dwError`  
 <span data-ttu-id="a20b3-109">[in] Hata gösteren bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="a20b3-109">[in] An integer that indicates the error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a20b3-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a20b3-110">Remarks</span></span>  
 <span data-ttu-id="a20b3-111">Belirtilen kesme noktası hiçbir zaman ulaşırsınız.</span><span class="sxs-lookup"><span data-stu-id="a20b3-111">The given breakpoint will never be hit.</span></span> <span data-ttu-id="a20b3-112">Hata ayıklayıcı, devre dışı bırakma ve onu yeniden bağlayın.</span><span class="sxs-lookup"><span data-stu-id="a20b3-112">The debugger should deactivate and rebind it.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a20b3-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a20b3-113">Requirements</span></span>  
 <span data-ttu-id="a20b3-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a20b3-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a20b3-115">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a20b3-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a20b3-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a20b3-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a20b3-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a20b3-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a20b3-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a20b3-118">See also</span></span>
- [<span data-ttu-id="a20b3-119">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a20b3-119">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
