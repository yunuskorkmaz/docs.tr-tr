---
title: ICorDebugManagedCallback::EvalComplete Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.EvalComplete
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::EvalComplete
helpviewer_keywords:
- ICorDebugManagedCallback::EvalComplete method [.NET Framework debugging]
- EvalComplete method [.NET Framework debugging]
ms.assetid: f74ab4eb-cd1b-407c-a66d-8ec0d85647f3
topic_type:
- apiref
ms.openlocfilehash: d29f4095a1d615285f4c4ff30e36b91404036949
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788408"
---
# <a name="icordebugmanagedcallbackevalcomplete-method"></a><span data-ttu-id="6afe1-102">ICorDebugManagedCallback::EvalComplete Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6afe1-102">ICorDebugManagedCallback::EvalComplete Method</span></span>
<span data-ttu-id="6afe1-103">Hata ayıklayıcıya bir değerlendirmenin tamamlandığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="6afe1-103">Notifies the debugger that an evaluation has been completed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6afe1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6afe1-104">Syntax</span></span>  
  
```cpp  
HRESULT EvalComplete (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread,  
    [in] ICorDebugEval      *pEval  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6afe1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6afe1-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="6afe1-106">'ndaki Değerlendirmede gerçekleştirilen uygulama etki alanını temsil eden ICorDebugAppDomain nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="6afe1-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain in which the evaluation was performed.</span></span>  
  
 `pThread`  
 <span data-ttu-id="6afe1-107">'ndaki Değerlendirmede gerçekleştirilen iş parçacığını temsil eden ICorDebugThread nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="6afe1-107">[in] A pointer to an ICorDebugThread object that represents the thread in which the evaluation was performed.</span></span>  
  
 `pEval`  
 <span data-ttu-id="6afe1-108">'ndaki Değerlendirmeyi gerçekleştiren kodu temsil eden ıcorıncode Geval nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="6afe1-108">[in] A pointer to an ICorDebugEval object that represents the code that performed the evaluation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6afe1-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6afe1-109">Requirements</span></span>  
 <span data-ttu-id="6afe1-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6afe1-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6afe1-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6afe1-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6afe1-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="6afe1-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6afe1-113">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6afe1-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6afe1-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6afe1-114">See also</span></span>

- [<span data-ttu-id="6afe1-115">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6afe1-115">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
