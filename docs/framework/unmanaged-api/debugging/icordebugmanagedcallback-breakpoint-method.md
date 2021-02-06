---
description: ': ICorDebugManagedCallback:: Breakpoint yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: dd4339294d8c4061c89bbb0ba7023b313e06102f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99660606"
---
# <a name="icordebugmanagedcallbackbreakpoint-method"></a><span data-ttu-id="35081-103">ICorDebugManagedCallback::Breakpoint Yöntemi</span><span class="sxs-lookup"><span data-stu-id="35081-103">ICorDebugManagedCallback::Breakpoint Method</span></span>

<span data-ttu-id="35081-104">Bir kesme noktasıyla karşılaşıldığında hata ayıklayıcıya bildirir.</span><span class="sxs-lookup"><span data-stu-id="35081-104">Notifies the debugger when a breakpoint is encountered.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35081-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="35081-105">Syntax</span></span>  
  
```cpp  
HRESULT Breakpoint (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] ICorDebugBreakpoint *pBreakpoint  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="35081-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="35081-106">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="35081-107">'ndaki Kesme noktasını içeren uygulama etki alanını temsil eden ICorDebugAppDomain nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="35081-107">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contains the breakpoint.</span></span>  
  
 `pThread`  
 <span data-ttu-id="35081-108">'ndaki Kesme noktasını içeren iş parçacığını temsil eden ICorDebugThread nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="35081-108">[in] A pointer to an ICorDebugThread object that represents the thread that contains the breakpoint.</span></span>  
  
 `pBreakpoint`  
 <span data-ttu-id="35081-109">'ndaki Kesme noktasını temsil eden ICorDebugBreakpoint nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="35081-109">[in] A pointer to an ICorDebugBreakpoint object that represents the breakpoint.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="35081-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="35081-110">Requirements</span></span>  

 <span data-ttu-id="35081-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="35081-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="35081-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="35081-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="35081-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="35081-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="35081-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="35081-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35081-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="35081-115">See also</span></span>

- [<span data-ttu-id="35081-116">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="35081-116">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
