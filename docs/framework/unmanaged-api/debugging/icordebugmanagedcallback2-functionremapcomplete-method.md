---
title: ICorDebugManagedCallback2::FunctionRemapComplete Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.FunctionRemapComplete
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::FunctionRemapComplete
helpviewer_keywords:
- FunctionRemapComplete method [.NET Framework debugging]
- ICorDebugManagedCallback2::FunctionRemapComplete method [.NET Framework debugging]
ms.assetid: 5396c4c3-4ec3-4e3a-a38d-d65b21f0a2fc
topic_type:
- apiref
ms.openlocfilehash: d49992b1f4b25586f6171a51b351a25d453560f2
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212158"
---
# <a name="icordebugmanagedcallback2functionremapcomplete-method"></a><span data-ttu-id="1e727-102">ICorDebugManagedCallback2::FunctionRemapComplete Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1e727-102">ICorDebugManagedCallback2::FunctionRemapComplete Method</span></span>
<span data-ttu-id="1e727-103">Kod yürütmenin düzenlenmiş bir işlevin yeni bir sürümüne geçirildiği hata ayıklayıcıya bildirir.</span><span class="sxs-lookup"><span data-stu-id="1e727-103">Notifies the debugger that code execution has switched to a new version of an edited function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e727-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1e727-104">Syntax</span></span>  
  
```cpp  
HRESULT FunctionRemapComplete (  
    [in] ICorDebugAppDomain   *pAppDomain,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugFunction    *pFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1e727-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1e727-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="1e727-106">'ndaki Düzenlenen işlevi içeren uygulama etki alanını temsil eden ICorDebugAppDomain nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1e727-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the edited function.</span></span>  
  
 `pThread`  
 <span data-ttu-id="1e727-107">'ndaki Yeniden eşleme kesme noktasının karşılaştığı iş parçacığını temsil eden ICorDebugThread nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1e727-107">[in] A pointer to an ICorDebugThread object that represents the thread on which the remap breakpoint was encountered.</span></span>  
  
 `pFunction`  
 <span data-ttu-id="1e727-108">'ndaki İş parçacığında çalışmakta olan işlevin sürümünü temsil eden ICorDebugFunction nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1e727-108">[in] A pointer to an ICorDebugFunction object that represents the version of the function currently running on the thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1e727-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1e727-109">Remarks</span></span>  
 <span data-ttu-id="1e727-110">Bu geri çağırma, hata ayıklayıcıya daha önce var olan herhangi bir step, yeniden oluşturma fırsatı sağlar.</span><span class="sxs-lookup"><span data-stu-id="1e727-110">This callback gives the debugger an opportunity to recreate any steppers that previously existed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1e727-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1e727-111">Requirements</span></span>  
 <span data-ttu-id="1e727-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1e727-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1e727-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="1e727-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1e727-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="1e727-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1e727-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1e727-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e727-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1e727-116">See also</span></span>

- [<span data-ttu-id="1e727-117">ICorDebugManagedCallback2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1e727-117">ICorDebugManagedCallback2 Interface</span></span>](icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="1e727-118">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1e727-118">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
