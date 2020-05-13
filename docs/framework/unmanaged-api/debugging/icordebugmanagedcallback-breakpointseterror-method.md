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
ms.openlocfilehash: 0fa25dd33223ad2a9521aed0917ce35a2a33fa2f
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213393"
---
# <a name="icordebugmanagedcallbackbreakpointseterror-method"></a><span data-ttu-id="cc0bc-102">ICorDebugManagedCallback::BreakpointSetError Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cc0bc-102">ICorDebugManagedCallback::BreakpointSetError Method</span></span>
<span data-ttu-id="cc0bc-103">Hata ayıklayıcısını, ortak dil çalışma zamanının, bir işlev tam zamanında (JıT) derlenmesinden önce ayarlanmış bir kesme noktasını doğru bir şekilde bağlamadığı konusunda bilgilendirir.</span><span class="sxs-lookup"><span data-stu-id="cc0bc-103">Notifies the debugger that the common language runtime was unable to accurately bind a breakpoint that was set before a function was just-in-time (JIT) compiled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc0bc-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cc0bc-104">Syntax</span></span>  
  
```cpp  
HRESULT BreakpointSetError (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] ICorDebugBreakpoint *pBreakpoint,  
    [in] DWORD                dwError  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cc0bc-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cc0bc-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="cc0bc-106">'ndaki İlişkisiz kesme noktasını içeren uygulama etki alanını temsil eden ICorDebugAppDomain nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="cc0bc-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contains the unbound breakpoint.</span></span>  
  
 `pThread`  
 <span data-ttu-id="cc0bc-107">'ndaki İlişkisiz kesme noktasını içeren iş parçacığını temsil eden ICorDebugThread nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="cc0bc-107">[in] A pointer to an ICorDebugThread object that represents the thread that contains the unbound breakpoint.</span></span>  
  
 `pBreakpoint`  
 <span data-ttu-id="cc0bc-108">'ndaki İlişkisiz kesme noktasını temsil eden ICorDebugBreakpoint nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="cc0bc-108">[in] A pointer to an ICorDebugBreakpoint object that represents the unbound breakpoint.</span></span>  
  
 `dwError`  
 <span data-ttu-id="cc0bc-109">'ndaki Hatayı gösteren bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="cc0bc-109">[in] An integer that indicates the error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cc0bc-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cc0bc-110">Remarks</span></span>  
 <span data-ttu-id="cc0bc-111">Verilen kesme noktası hiçbir şekilde isabet ettirilmeyecek.</span><span class="sxs-lookup"><span data-stu-id="cc0bc-111">The given breakpoint will never be hit.</span></span> <span data-ttu-id="cc0bc-112">Hata ayıklayıcı devre dışı bırakıp yeniden bağlamasını bilmelidir.</span><span class="sxs-lookup"><span data-stu-id="cc0bc-112">The debugger should deactivate and rebind it.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc0bc-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cc0bc-113">Requirements</span></span>  
 <span data-ttu-id="cc0bc-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cc0bc-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc0bc-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="cc0bc-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cc0bc-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="cc0bc-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cc0bc-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc0bc-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc0bc-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cc0bc-118">See also</span></span>

- [<span data-ttu-id="cc0bc-119">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cc0bc-119">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
