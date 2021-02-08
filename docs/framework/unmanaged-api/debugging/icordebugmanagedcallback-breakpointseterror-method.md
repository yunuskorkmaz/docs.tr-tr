---
description: ': ICorDebugManagedCallback:: BreakpointSetError Yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: cf78b4dc06a71b6ac0eb4f653a00c1b3c6ae464b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791094"
---
# <a name="icordebugmanagedcallbackbreakpointseterror-method"></a><span data-ttu-id="7902f-103">ICorDebugManagedCallback::BreakpointSetError Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7902f-103">ICorDebugManagedCallback::BreakpointSetError Method</span></span>

<span data-ttu-id="7902f-104">Hata ayıklayıcısını, ortak dil çalışma zamanının, bir işlev tam zamanında (JıT) derlenmesinden önce ayarlanmış bir kesme noktasını doğru bir şekilde bağlamadığı konusunda bilgilendirir.</span><span class="sxs-lookup"><span data-stu-id="7902f-104">Notifies the debugger that the common language runtime was unable to accurately bind a breakpoint that was set before a function was just-in-time (JIT) compiled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7902f-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7902f-105">Syntax</span></span>  
  
```cpp  
HRESULT BreakpointSetError (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] ICorDebugBreakpoint *pBreakpoint,  
    [in] DWORD                dwError  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7902f-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7902f-106">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="7902f-107">'ndaki İlişkisiz kesme noktasını içeren uygulama etki alanını temsil eden ICorDebugAppDomain nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7902f-107">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contains the unbound breakpoint.</span></span>  
  
 `pThread`  
 <span data-ttu-id="7902f-108">'ndaki İlişkisiz kesme noktasını içeren iş parçacığını temsil eden ICorDebugThread nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7902f-108">[in] A pointer to an ICorDebugThread object that represents the thread that contains the unbound breakpoint.</span></span>  
  
 `pBreakpoint`  
 <span data-ttu-id="7902f-109">'ndaki İlişkisiz kesme noktasını temsil eden ICorDebugBreakpoint nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7902f-109">[in] A pointer to an ICorDebugBreakpoint object that represents the unbound breakpoint.</span></span>  
  
 `dwError`  
 <span data-ttu-id="7902f-110">'ndaki Hatayı gösteren bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="7902f-110">[in] An integer that indicates the error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7902f-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7902f-111">Remarks</span></span>  

 <span data-ttu-id="7902f-112">Verilen kesme noktası hiçbir şekilde isabet ettirilmeyecek.</span><span class="sxs-lookup"><span data-stu-id="7902f-112">The given breakpoint will never be hit.</span></span> <span data-ttu-id="7902f-113">Hata ayıklayıcı devre dışı bırakıp yeniden bağlamasını bilmelidir.</span><span class="sxs-lookup"><span data-stu-id="7902f-113">The debugger should deactivate and rebind it.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7902f-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7902f-114">Requirements</span></span>  

 <span data-ttu-id="7902f-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7902f-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7902f-116">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7902f-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7902f-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="7902f-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7902f-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7902f-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7902f-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7902f-119">See also</span></span>

- [<span data-ttu-id="7902f-120">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7902f-120">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
