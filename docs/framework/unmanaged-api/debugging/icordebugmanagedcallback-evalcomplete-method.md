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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a874646a6746a9b2fc8ce597e6c1ca47340c199a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67759651"
---
# <a name="icordebugmanagedcallbackevalcomplete-method"></a><span data-ttu-id="38448-102">ICorDebugManagedCallback::EvalComplete Yöntemi</span><span class="sxs-lookup"><span data-stu-id="38448-102">ICorDebugManagedCallback::EvalComplete Method</span></span>
<span data-ttu-id="38448-103">Hata ayıklayıcı, bir değerlendirme tamamlandığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="38448-103">Notifies the debugger that an evaluation has been completed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38448-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="38448-104">Syntax</span></span>  
  
```cpp  
HRESULT EvalComplete (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread,  
    [in] ICorDebugEval      *pEval  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="38448-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="38448-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="38448-106">[in] Değerlendirme gerçekleştirildiği uygulama etki alanını temsil eden bir Icordebugappdomain nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="38448-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain in which the evaluation was performed.</span></span>  
  
 `pThread`  
 <span data-ttu-id="38448-107">[in] Değerlendirme gerçekleştirildiği iş parçacığını temsil eden bir Icordebugthread nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="38448-107">[in] A pointer to an ICorDebugThread object that represents the thread in which the evaluation was performed.</span></span>  
  
 `pEval`  
 <span data-ttu-id="38448-108">[in] Değerlendirme gerçekleştirilen kodunu temsil eden bir Icordebugeval nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="38448-108">[in] A pointer to an ICorDebugEval object that represents the code that performed the evaluation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38448-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="38448-109">Requirements</span></span>  
 <span data-ttu-id="38448-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="38448-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38448-111">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="38448-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="38448-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="38448-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="38448-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38448-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38448-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="38448-114">See also</span></span>

- [<span data-ttu-id="38448-115">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="38448-115">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
