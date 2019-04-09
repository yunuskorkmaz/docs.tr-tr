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
ms.openlocfilehash: 27d5b8e0127971cc3a46560590fd9d95f0ffd1f0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59151027"
---
# <a name="icordebugmanagedcallbackbreakpointseterror-method"></a><span data-ttu-id="12590-102">ICorDebugManagedCallback::BreakpointSetError Yöntemi</span><span class="sxs-lookup"><span data-stu-id="12590-102">ICorDebugManagedCallback::BreakpointSetError Method</span></span>
<span data-ttu-id="12590-103">Hata ayıklayıcı ortak dil çalışma zamanı öncesinde bir işlev yalnızca derlenmiş zamanında (JIT) ayarlanan bir kesme noktası doğru şekilde bağlanamıyor olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="12590-103">Notifies the debugger that the common language runtime was unable to accurately bind a breakpoint that was set before a function was just-in-time (JIT) compiled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12590-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="12590-104">Syntax</span></span>  
  
```  
HRESULT BreakpointSetError (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] ICorDebugBreakpoint *pBreakpoint,  
    [in] DWORD                dwError  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="12590-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="12590-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="12590-106">[in] İlişkisiz bir kesme noktası içeren uygulama etki alanını temsil eden bir Icordebugappdomain nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="12590-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contains the unbound breakpoint.</span></span>  
  
 `pThread`  
 <span data-ttu-id="12590-107">[in] İlişkisiz bir kesme noktası içeren iş parçacığını temsil eden bir Icordebugthread nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="12590-107">[in] A pointer to an ICorDebugThread object that represents the thread that contains the unbound breakpoint.</span></span>  
  
 `pBreakpoint`  
 <span data-ttu-id="12590-108">[in] İlişkisiz kesme noktasını temsil eden bir Icordebugbreakpoint nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="12590-108">[in] A pointer to an ICorDebugBreakpoint object that represents the unbound breakpoint.</span></span>  
  
 `dwError`  
 <span data-ttu-id="12590-109">[in] Hata gösteren bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="12590-109">[in] An integer that indicates the error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="12590-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="12590-110">Remarks</span></span>  
 <span data-ttu-id="12590-111">Belirtilen kesme noktası hiçbir zaman ulaşırsınız.</span><span class="sxs-lookup"><span data-stu-id="12590-111">The given breakpoint will never be hit.</span></span> <span data-ttu-id="12590-112">Hata ayıklayıcı, devre dışı bırakma ve onu yeniden bağlayın.</span><span class="sxs-lookup"><span data-stu-id="12590-112">The debugger should deactivate and rebind it.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="12590-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="12590-113">Requirements</span></span>  
 <span data-ttu-id="12590-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="12590-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12590-115">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="12590-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="12590-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="12590-116">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="12590-117">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="12590-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="12590-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="12590-118">See also</span></span>

- [<span data-ttu-id="12590-119">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="12590-119">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
