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
ms.openlocfilehash: 602bcd12d1fd4c5806de6db81252731baa447b7b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59120022"
---
# <a name="icordebugmanagedcallbackevalexception-method"></a><span data-ttu-id="508f2-102">ICorDebugManagedCallback::EvalException Yöntemi</span><span class="sxs-lookup"><span data-stu-id="508f2-102">ICorDebugManagedCallback::EvalException Method</span></span>
<span data-ttu-id="508f2-103">Hata ayıklayıcı, bir değerlendirme işlenmeyen bir özel durumla sona erdi bildirir.</span><span class="sxs-lookup"><span data-stu-id="508f2-103">Notifies the debugger that an evaluation has terminated with an unhandled exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="508f2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="508f2-104">Syntax</span></span>  
  
```  
HRESULT EvalException (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread,  
    [in] ICorDebugEval      *pEval  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="508f2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="508f2-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="508f2-106">[in] Değerlendirme sonlandırıldı, uygulama etki alanını temsil eden bir Icordebugappdomain nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="508f2-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain in which the evaluation terminated.</span></span>  
  
 `pThread`  
 <span data-ttu-id="508f2-107">[in] Değerlendirme sonlandırıldı, iş parçacığı temsil eden bir Icordebugthread nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="508f2-107">[in] A pointer to an ICorDebugThread object that represents the thread in which the evaluation terminated.</span></span>  
  
 `pEval`  
 <span data-ttu-id="508f2-108">[in] Değerlendirme gerçekleştirilen kodunu temsil eden bir Icordebugeval nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="508f2-108">[in] A pointer to an ICorDebugEval object that represents the code that performed the evaluation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="508f2-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="508f2-109">Requirements</span></span>  
 <span data-ttu-id="508f2-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="508f2-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="508f2-111">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="508f2-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="508f2-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="508f2-112">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="508f2-113">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="508f2-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="508f2-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="508f2-114">See also</span></span>

- [<span data-ttu-id="508f2-115">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="508f2-115">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
