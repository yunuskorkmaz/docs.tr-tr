---
title: ICorDebugManagedCallback::EvalException Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.EvalException
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::EvalException
helpviewer_keywords:
- EvalException method [.NET Framework debugging]
- ICorDebugManagedCallback::EvalException method [.NET Framework debugging]
ms.assetid: d6036345-18a3-45c1-a302-b1c6f2dced9b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dbf12612bb432f8935d08bdeac0bbcb471c38c54
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67759631"
---
# <a name="icordebugmanagedcallbackevalexception-method"></a><span data-ttu-id="f48df-102">ICorDebugManagedCallback::EvalException Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f48df-102">ICorDebugManagedCallback::EvalException Method</span></span>
<span data-ttu-id="f48df-103">Hata ayıklayıcı, bir değerlendirme işlenmeyen bir özel durumla sona erdi bildirir.</span><span class="sxs-lookup"><span data-stu-id="f48df-103">Notifies the debugger that an evaluation has terminated with an unhandled exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f48df-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f48df-104">Syntax</span></span>  
  
```cpp  
HRESULT EvalException (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread,  
    [in] ICorDebugEval      *pEval  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f48df-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f48df-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="f48df-106">[in] Değerlendirme sonlandırıldı, uygulama etki alanını temsil eden bir Icordebugappdomain nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="f48df-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain in which the evaluation terminated.</span></span>  
  
 `pThread`  
 <span data-ttu-id="f48df-107">[in] Değerlendirme sonlandırıldı, iş parçacığı temsil eden bir Icordebugthread nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="f48df-107">[in] A pointer to an ICorDebugThread object that represents the thread in which the evaluation terminated.</span></span>  
  
 `pEval`  
 <span data-ttu-id="f48df-108">[in] Değerlendirme gerçekleştirilen kodunu temsil eden bir Icordebugeval nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="f48df-108">[in] A pointer to an ICorDebugEval object that represents the code that performed the evaluation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f48df-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f48df-109">Requirements</span></span>  
 <span data-ttu-id="f48df-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f48df-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f48df-111">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f48df-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f48df-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f48df-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f48df-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f48df-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f48df-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f48df-114">See also</span></span>

- [<span data-ttu-id="f48df-115">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f48df-115">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
