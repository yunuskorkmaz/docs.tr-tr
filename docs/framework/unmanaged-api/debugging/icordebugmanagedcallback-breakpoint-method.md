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
ms.openlocfilehash: 381fdecfb2cb194cd1eb00a5b55db6fb89eeebbc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33413923"
---
# <a name="icordebugmanagedcallbackbreakpoint-method"></a><span data-ttu-id="fe631-102">ICorDebugManagedCallback::Breakpoint Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fe631-102">ICorDebugManagedCallback::Breakpoint Method</span></span>
<span data-ttu-id="fe631-103">Bir kesme noktası karşılaştı, hata ayıklayıcı size bildirir.</span><span class="sxs-lookup"><span data-stu-id="fe631-103">Notifies the debugger when a breakpoint is encountered.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe631-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fe631-104">Syntax</span></span>  
  
```  
HRESULT Breakpoint (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] ICorDebugBreakpoint *pBreakpoint  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fe631-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fe631-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="fe631-106">[in] Bir işaretçi Icordebugappdomain nesneye kesme içeren uygulama etki alanını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="fe631-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contains the breakpoint.</span></span>  
  
 `pThread`  
 <span data-ttu-id="fe631-107">[in] Bir işaretçi Icordebugthread nesneye kesme noktası içerdiğinden iş parçacığı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="fe631-107">[in] A pointer to an ICorDebugThread object that represents the thread that contains the breakpoint.</span></span>  
  
 `pBreakpoint`  
 <span data-ttu-id="fe631-108">[in] Bir işaretçi Icordebugbreakpoint nesneye kesme temsil eder.</span><span class="sxs-lookup"><span data-stu-id="fe631-108">[in] A pointer to an ICorDebugBreakpoint object that represents the breakpoint.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe631-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fe631-109">Requirements</span></span>  
 <span data-ttu-id="fe631-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fe631-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe631-111">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fe631-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fe631-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fe631-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fe631-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fe631-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe631-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fe631-114">See Also</span></span>  
 [<span data-ttu-id="fe631-115">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fe631-115">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
