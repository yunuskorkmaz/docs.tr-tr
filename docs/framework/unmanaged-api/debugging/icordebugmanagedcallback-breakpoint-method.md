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
ms.openlocfilehash: d8e62499a813419ecc30924624da553ca9f2c7b2
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213406"
---
# <a name="icordebugmanagedcallbackbreakpoint-method"></a><span data-ttu-id="efc40-102">ICorDebugManagedCallback::Breakpoint Yöntemi</span><span class="sxs-lookup"><span data-stu-id="efc40-102">ICorDebugManagedCallback::Breakpoint Method</span></span>
<span data-ttu-id="efc40-103">Bir kesme noktasıyla karşılaşıldığında hata ayıklayıcıya bildirir.</span><span class="sxs-lookup"><span data-stu-id="efc40-103">Notifies the debugger when a breakpoint is encountered.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="efc40-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="efc40-104">Syntax</span></span>  
  
```cpp  
HRESULT Breakpoint (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] ICorDebugBreakpoint *pBreakpoint  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="efc40-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="efc40-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="efc40-106">'ndaki Kesme noktasını içeren uygulama etki alanını temsil eden ICorDebugAppDomain nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="efc40-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contains the breakpoint.</span></span>  
  
 `pThread`  
 <span data-ttu-id="efc40-107">'ndaki Kesme noktasını içeren iş parçacığını temsil eden ICorDebugThread nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="efc40-107">[in] A pointer to an ICorDebugThread object that represents the thread that contains the breakpoint.</span></span>  
  
 `pBreakpoint`  
 <span data-ttu-id="efc40-108">'ndaki Kesme noktasını temsil eden ICorDebugBreakpoint nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="efc40-108">[in] A pointer to an ICorDebugBreakpoint object that represents the breakpoint.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="efc40-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="efc40-109">Requirements</span></span>  
 <span data-ttu-id="efc40-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="efc40-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="efc40-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="efc40-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="efc40-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="efc40-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="efc40-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="efc40-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efc40-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="efc40-114">See also</span></span>

- [<span data-ttu-id="efc40-115">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="efc40-115">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
