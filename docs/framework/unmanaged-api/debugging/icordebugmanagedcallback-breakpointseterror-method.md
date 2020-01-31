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
ms.openlocfilehash: 67d4972ee38a54d43b4a096847cc61fa3402b042
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788432"
---
# <a name="icordebugmanagedcallbackbreakpointseterror-method"></a><span data-ttu-id="ec4fc-102">ICorDebugManagedCallback::BreakpointSetError Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ec4fc-102">ICorDebugManagedCallback::BreakpointSetError Method</span></span>
<span data-ttu-id="ec4fc-103">Hata ayıklayıcısını, ortak dil çalışma zamanının, bir işlev tam zamanında (JıT) derlenmesinden önce ayarlanmış bir kesme noktasını doğru bir şekilde bağlamadığı konusunda bilgilendirir.</span><span class="sxs-lookup"><span data-stu-id="ec4fc-103">Notifies the debugger that the common language runtime was unable to accurately bind a breakpoint that was set before a function was just-in-time (JIT) compiled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec4fc-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ec4fc-104">Syntax</span></span>  
  
```cpp  
HRESULT BreakpointSetError (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] ICorDebugBreakpoint *pBreakpoint,  
    [in] DWORD                dwError  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ec4fc-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ec4fc-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="ec4fc-106">'ndaki İlişkisiz kesme noktasını içeren uygulama etki alanını temsil eden ICorDebugAppDomain nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ec4fc-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contains the unbound breakpoint.</span></span>  
  
 `pThread`  
 <span data-ttu-id="ec4fc-107">'ndaki İlişkisiz kesme noktasını içeren iş parçacığını temsil eden ICorDebugThread nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ec4fc-107">[in] A pointer to an ICorDebugThread object that represents the thread that contains the unbound breakpoint.</span></span>  
  
 `pBreakpoint`  
 <span data-ttu-id="ec4fc-108">'ndaki İlişkisiz kesme noktasını temsil eden ICorDebugBreakpoint nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ec4fc-108">[in] A pointer to an ICorDebugBreakpoint object that represents the unbound breakpoint.</span></span>  
  
 `dwError`  
 <span data-ttu-id="ec4fc-109">'ndaki Hatayı gösteren bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="ec4fc-109">[in] An integer that indicates the error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ec4fc-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ec4fc-110">Remarks</span></span>  
 <span data-ttu-id="ec4fc-111">Verilen kesme noktası hiçbir şekilde isabet ettirilmeyecek.</span><span class="sxs-lookup"><span data-stu-id="ec4fc-111">The given breakpoint will never be hit.</span></span> <span data-ttu-id="ec4fc-112">Hata ayıklayıcı devre dışı bırakıp yeniden bağlamasını bilmelidir.</span><span class="sxs-lookup"><span data-stu-id="ec4fc-112">The debugger should deactivate and rebind it.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ec4fc-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ec4fc-113">Requirements</span></span>  
 <span data-ttu-id="ec4fc-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ec4fc-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec4fc-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ec4fc-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ec4fc-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="ec4fc-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ec4fc-117">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ec4fc-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec4fc-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ec4fc-118">See also</span></span>

- [<span data-ttu-id="ec4fc-119">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ec4fc-119">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
