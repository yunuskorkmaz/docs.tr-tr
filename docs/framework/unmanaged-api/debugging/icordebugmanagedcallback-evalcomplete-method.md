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
ms.openlocfilehash: 3243429f52bda58953296c4bb32624440792ad02
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54636475"
---
# <a name="icordebugmanagedcallbackevalcomplete-method"></a><span data-ttu-id="52f92-102">ICorDebugManagedCallback::EvalComplete Yöntemi</span><span class="sxs-lookup"><span data-stu-id="52f92-102">ICorDebugManagedCallback::EvalComplete Method</span></span>
<span data-ttu-id="52f92-103">Hata ayıklayıcı, bir değerlendirme tamamlandığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="52f92-103">Notifies the debugger that an evaluation has been completed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52f92-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="52f92-104">Syntax</span></span>  
  
```  
HRESULT EvalComplete (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread,  
    [in] ICorDebugEval      *pEval  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="52f92-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="52f92-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="52f92-106">[in] Değerlendirme gerçekleştirildiği uygulama etki alanını temsil eden bir Icordebugappdomain nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="52f92-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain in which the evaluation was performed.</span></span>  
  
 `pThread`  
 <span data-ttu-id="52f92-107">[in] Değerlendirme gerçekleştirildiği iş parçacığını temsil eden bir Icordebugthread nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="52f92-107">[in] A pointer to an ICorDebugThread object that represents the thread in which the evaluation was performed.</span></span>  
  
 `pEval`  
 <span data-ttu-id="52f92-108">[in] Değerlendirme gerçekleştirilen kodunu temsil eden bir Icordebugeval nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="52f92-108">[in] A pointer to an ICorDebugEval object that represents the code that performed the evaluation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="52f92-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="52f92-109">Requirements</span></span>  
 <span data-ttu-id="52f92-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="52f92-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="52f92-111">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="52f92-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="52f92-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="52f92-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="52f92-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="52f92-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52f92-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="52f92-114">See also</span></span>
- [<span data-ttu-id="52f92-115">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="52f92-115">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
