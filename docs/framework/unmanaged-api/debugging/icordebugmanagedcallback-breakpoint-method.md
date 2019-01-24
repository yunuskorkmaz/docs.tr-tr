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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a1df57e82309d42092c38dfcdd8b65ccc2797f9a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54743290"
---
# <a name="icordebugmanagedcallbackbreakpoint-method"></a><span data-ttu-id="077a2-102">ICorDebugManagedCallback::Breakpoint Yöntemi</span><span class="sxs-lookup"><span data-stu-id="077a2-102">ICorDebugManagedCallback::Breakpoint Method</span></span>
<span data-ttu-id="077a2-103">Hata ayıklayıcı bir kesme oluştuğunda size bildirir.</span><span class="sxs-lookup"><span data-stu-id="077a2-103">Notifies the debugger when a breakpoint is encountered.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="077a2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="077a2-104">Syntax</span></span>  
  
```  
HRESULT Breakpoint (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] ICorDebugBreakpoint *pBreakpoint  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="077a2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="077a2-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="077a2-106">[in] Kesme noktasını içeren uygulama etki alanını temsil eden bir Icordebugappdomain nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="077a2-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contains the breakpoint.</span></span>  
  
 `pThread`  
 <span data-ttu-id="077a2-107">[in] Kesme noktasını içeren iş parçacığını temsil eden bir Icordebugthread nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="077a2-107">[in] A pointer to an ICorDebugThread object that represents the thread that contains the breakpoint.</span></span>  
  
 `pBreakpoint`  
 <span data-ttu-id="077a2-108">[in] Kesme noktasını temsil eden bir Icordebugbreakpoint nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="077a2-108">[in] A pointer to an ICorDebugBreakpoint object that represents the breakpoint.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="077a2-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="077a2-109">Requirements</span></span>  
 <span data-ttu-id="077a2-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="077a2-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="077a2-111">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="077a2-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="077a2-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="077a2-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="077a2-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="077a2-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="077a2-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="077a2-114">See also</span></span>
- [<span data-ttu-id="077a2-115">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="077a2-115">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
