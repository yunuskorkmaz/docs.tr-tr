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
ms.openlocfilehash: 8cc437f63621c451c0af796513d4646fe0668c00
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33418386"
---
# <a name="icordebugmanagedcallbackbreakpointseterror-method"></a><span data-ttu-id="58c96-102">ICorDebugManagedCallback::BreakpointSetError Yöntemi</span><span class="sxs-lookup"><span data-stu-id="58c96-102">ICorDebugManagedCallback::BreakpointSetError Method</span></span>
<span data-ttu-id="58c96-103">Hata ayıklayıcı ortak dil çalışma zamanı doğru sadece derlenmiş zamanında (JIT) bir işlevi olan önce bu ayarlanan bir kesme noktası bağlayamadı olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="58c96-103">Notifies the debugger that the common language runtime was unable to accurately bind a breakpoint that was set before a function was just-in-time (JIT) compiled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58c96-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="58c96-104">Syntax</span></span>  
  
```  
HRESULT BreakpointSetError (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] ICorDebugBreakpoint *pBreakpoint,  
    [in] DWORD                dwError  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="58c96-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="58c96-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="58c96-106">[in] Bir işaretçi Icordebugappdomain nesneye ilişkisiz kesme noktası içeren uygulama etki alanını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="58c96-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contains the unbound breakpoint.</span></span>  
  
 `pThread`  
 <span data-ttu-id="58c96-107">[in] Bir işaretçi Icordebugthread nesneye ilişkisiz kesme noktası içerdiğinden iş parçacığı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="58c96-107">[in] A pointer to an ICorDebugThread object that represents the thread that contains the unbound breakpoint.</span></span>  
  
 `pBreakpoint`  
 <span data-ttu-id="58c96-108">[in] Bir işaretçi Icordebugbreakpoint nesneye ilişkisiz kesme noktası temsil eder.</span><span class="sxs-lookup"><span data-stu-id="58c96-108">[in] A pointer to an ICorDebugBreakpoint object that represents the unbound breakpoint.</span></span>  
  
 `dwError`  
 <span data-ttu-id="58c96-109">[in] Hata gösteren tamsayı.</span><span class="sxs-lookup"><span data-stu-id="58c96-109">[in] An integer that indicates the error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="58c96-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="58c96-110">Remarks</span></span>  
 <span data-ttu-id="58c96-111">Verilen kesme noktası hiçbir zaman karşılaşır.</span><span class="sxs-lookup"><span data-stu-id="58c96-111">The given breakpoint will never be hit.</span></span> <span data-ttu-id="58c96-112">Hata ayıklayıcı devre dışı bırakın ve onu yeniden bağlayın.</span><span class="sxs-lookup"><span data-stu-id="58c96-112">The debugger should deactivate and rebind it.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="58c96-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="58c96-113">Requirements</span></span>  
 <span data-ttu-id="58c96-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="58c96-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="58c96-115">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="58c96-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="58c96-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="58c96-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="58c96-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="58c96-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58c96-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="58c96-118">See Also</span></span>  
 [<span data-ttu-id="58c96-119">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="58c96-119">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
