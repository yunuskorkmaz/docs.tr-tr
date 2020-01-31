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
ms.openlocfilehash: ac91a9c662a82c5ab870d01cb4b5d87c7af6b6ba
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76782067"
---
# <a name="icordebugmanagedcallbackbreakpoint-method"></a><span data-ttu-id="c5a1a-102">ICorDebugManagedCallback::Breakpoint Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c5a1a-102">ICorDebugManagedCallback::Breakpoint Method</span></span>
<span data-ttu-id="c5a1a-103">Bir kesme noktasıyla karşılaşıldığında hata ayıklayıcıya bildirir.</span><span class="sxs-lookup"><span data-stu-id="c5a1a-103">Notifies the debugger when a breakpoint is encountered.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5a1a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c5a1a-104">Syntax</span></span>  
  
```cpp  
HRESULT Breakpoint (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] ICorDebugBreakpoint *pBreakpoint  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c5a1a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c5a1a-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="c5a1a-106">'ndaki Kesme noktasını içeren uygulama etki alanını temsil eden ICorDebugAppDomain nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c5a1a-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contains the breakpoint.</span></span>  
  
 `pThread`  
 <span data-ttu-id="c5a1a-107">'ndaki Kesme noktasını içeren iş parçacığını temsil eden ICorDebugThread nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c5a1a-107">[in] A pointer to an ICorDebugThread object that represents the thread that contains the breakpoint.</span></span>  
  
 `pBreakpoint`  
 <span data-ttu-id="c5a1a-108">'ndaki Kesme noktasını temsil eden ICorDebugBreakpoint nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c5a1a-108">[in] A pointer to an ICorDebugBreakpoint object that represents the breakpoint.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5a1a-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c5a1a-109">Requirements</span></span>  
 <span data-ttu-id="c5a1a-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c5a1a-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5a1a-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c5a1a-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c5a1a-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="c5a1a-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c5a1a-113">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c5a1a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5a1a-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c5a1a-114">See also</span></span>

- [<span data-ttu-id="c5a1a-115">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c5a1a-115">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
