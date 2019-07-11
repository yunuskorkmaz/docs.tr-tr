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
ms.openlocfilehash: a3ef4b284676608363281e04087f6435dcb1ef74
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67759844"
---
# <a name="icordebugmanagedcallbackbreakpointseterror-method"></a><span data-ttu-id="0cd88-102">ICorDebugManagedCallback::BreakpointSetError Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0cd88-102">ICorDebugManagedCallback::BreakpointSetError Method</span></span>
<span data-ttu-id="0cd88-103">Hata ayıklayıcı ortak dil çalışma zamanı öncesinde bir işlev yalnızca derlenmiş zamanında (JIT) ayarlanan bir kesme noktası doğru şekilde bağlanamıyor olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="0cd88-103">Notifies the debugger that the common language runtime was unable to accurately bind a breakpoint that was set before a function was just-in-time (JIT) compiled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0cd88-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0cd88-104">Syntax</span></span>  
  
```cpp  
HRESULT BreakpointSetError (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] ICorDebugBreakpoint *pBreakpoint,  
    [in] DWORD                dwError  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0cd88-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0cd88-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="0cd88-106">[in] İlişkisiz bir kesme noktası içeren uygulama etki alanını temsil eden bir Icordebugappdomain nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="0cd88-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contains the unbound breakpoint.</span></span>  
  
 `pThread`  
 <span data-ttu-id="0cd88-107">[in] İlişkisiz bir kesme noktası içeren iş parçacığını temsil eden bir Icordebugthread nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="0cd88-107">[in] A pointer to an ICorDebugThread object that represents the thread that contains the unbound breakpoint.</span></span>  
  
 `pBreakpoint`  
 <span data-ttu-id="0cd88-108">[in] İlişkisiz kesme noktasını temsil eden bir Icordebugbreakpoint nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="0cd88-108">[in] A pointer to an ICorDebugBreakpoint object that represents the unbound breakpoint.</span></span>  
  
 `dwError`  
 <span data-ttu-id="0cd88-109">[in] Hata gösteren bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="0cd88-109">[in] An integer that indicates the error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0cd88-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0cd88-110">Remarks</span></span>  
 <span data-ttu-id="0cd88-111">Belirtilen kesme noktası hiçbir zaman ulaşırsınız.</span><span class="sxs-lookup"><span data-stu-id="0cd88-111">The given breakpoint will never be hit.</span></span> <span data-ttu-id="0cd88-112">Hata ayıklayıcı, devre dışı bırakma ve onu yeniden bağlayın.</span><span class="sxs-lookup"><span data-stu-id="0cd88-112">The debugger should deactivate and rebind it.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0cd88-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0cd88-113">Requirements</span></span>  
 <span data-ttu-id="0cd88-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0cd88-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0cd88-115">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0cd88-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0cd88-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0cd88-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0cd88-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0cd88-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0cd88-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0cd88-118">See also</span></span>

- [<span data-ttu-id="0cd88-119">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0cd88-119">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
