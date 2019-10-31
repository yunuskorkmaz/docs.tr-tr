---
title: ICorDebugManagedCallback::Breakpoint Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.Breakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::Breakpoint
helpviewer_keywords:
- ICorDebugManagedCallback::Breakpoint method [.NET Framework debugging]
- Breakpoint method [.NET Framework debugging]
ms.assetid: 60b279b0-a726-46d2-8c53-76986a007ebb
topic_type:
- apiref
ms.openlocfilehash: 8a4f7d4f422d80d044bcb92065dbefc7f421a069
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122597"
---
# <a name="icordebugmanagedcallbackbreakpoint-method"></a><span data-ttu-id="5e9fe-102">ICorDebugManagedCallback::Breakpoint Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5e9fe-102">ICorDebugManagedCallback::Breakpoint Method</span></span>
<span data-ttu-id="5e9fe-103">Bir kesme noktasıyla karşılaşıldığında hata ayıklayıcıya bildirir.</span><span class="sxs-lookup"><span data-stu-id="5e9fe-103">Notifies the debugger when a breakpoint is encountered.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e9fe-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5e9fe-104">Syntax</span></span>  
  
```cpp  
HRESULT Breakpoint (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] ICorDebugBreakpoint *pBreakpoint  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5e9fe-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5e9fe-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="5e9fe-106">'ndaki Kesme noktasını içeren uygulama etki alanını temsil eden ICorDebugAppDomain nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5e9fe-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contains the breakpoint.</span></span>  
  
 `pThread`  
 <span data-ttu-id="5e9fe-107">'ndaki Kesme noktasını içeren iş parçacığını temsil eden ICorDebugThread nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5e9fe-107">[in] A pointer to an ICorDebugThread object that represents the thread that contains the breakpoint.</span></span>  
  
 `pBreakpoint`  
 <span data-ttu-id="5e9fe-108">'ndaki Kesme noktasını temsil eden ICorDebugBreakpoint nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5e9fe-108">[in] A pointer to an ICorDebugBreakpoint object that represents the breakpoint.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5e9fe-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5e9fe-109">Requirements</span></span>  
 <span data-ttu-id="5e9fe-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5e9fe-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e9fe-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="5e9fe-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5e9fe-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="5e9fe-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5e9fe-113">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5e9fe-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e9fe-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5e9fe-114">See also</span></span>

- [<span data-ttu-id="5e9fe-115">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5e9fe-115">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
