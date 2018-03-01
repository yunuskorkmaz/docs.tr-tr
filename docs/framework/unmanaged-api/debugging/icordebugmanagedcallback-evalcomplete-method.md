---
title: "ICorDebugManagedCallback::EvalComplete Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5715ffdf92e118b4cd16e919f10a8fdc02a06387
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallbackevalcomplete-method"></a><span data-ttu-id="1ee0f-102">ICorDebugManagedCallback::EvalComplete Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1ee0f-102">ICorDebugManagedCallback::EvalComplete Method</span></span>
<span data-ttu-id="1ee0f-103">Hata ayıklayıcı değerlendirme tamamlandığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="1ee0f-103">Notifies the debugger that an evaluation has been completed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ee0f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1ee0f-104">Syntax</span></span>  
  
```  
HRESULT EvalComplete (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread,  
    [in] ICorDebugEval      *pEval  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1ee0f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1ee0f-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="1ee0f-106">[in] Bir işaretçi Icordebugappdomain nesneye değerlendirme gerçekleştirilip gerçekleştirilmediğine uygulama etki alanını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="1ee0f-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain in which the evaluation was performed.</span></span>  
  
 `pThread`  
 <span data-ttu-id="1ee0f-107">[in] Bir işaretçi Icordebugthread nesneye değerlendirme gerçekleştirilip gerçekleştirilmediğine iş parçacığı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="1ee0f-107">[in] A pointer to an ICorDebugThread object that represents the thread in which the evaluation was performed.</span></span>  
  
 `pEval`  
 <span data-ttu-id="1ee0f-108">[in] Bir işaretçi Icordebugeval nesneye değerlendirme gerçekleştirilen kodunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="1ee0f-108">[in] A pointer to an ICorDebugEval object that represents the code that performed the evaluation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ee0f-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1ee0f-109">Requirements</span></span>  
 <span data-ttu-id="1ee0f-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1ee0f-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ee0f-111">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1ee0f-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1ee0f-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1ee0f-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1ee0f-113">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1ee0f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ee0f-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1ee0f-114">See Also</span></span>  
 [<span data-ttu-id="1ee0f-115">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1ee0f-115">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
