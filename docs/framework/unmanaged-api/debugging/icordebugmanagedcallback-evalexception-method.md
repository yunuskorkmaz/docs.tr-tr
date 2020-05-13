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
ms.openlocfilehash: 20a841006d51671a491e11c4e40287baf739d191
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209831"
---
# <a name="icordebugmanagedcallbackevalexception-method"></a><span data-ttu-id="1ba45-102">ICorDebugManagedCallback::EvalException Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1ba45-102">ICorDebugManagedCallback::EvalException Method</span></span>
<span data-ttu-id="1ba45-103">Hata ayıklayıcıya bir değerlendirmenin işlenmeyen bir özel durumla sonlandırıldığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="1ba45-103">Notifies the debugger that an evaluation has terminated with an unhandled exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ba45-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1ba45-104">Syntax</span></span>  
  
```cpp  
HRESULT EvalException (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread,  
    [in] ICorDebugEval      *pEval  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1ba45-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1ba45-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="1ba45-106">'ndaki Değerlendirmenin sonlandırıldığı uygulama etki alanını temsil eden ICorDebugAppDomain nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1ba45-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain in which the evaluation terminated.</span></span>  
  
 `pThread`  
 <span data-ttu-id="1ba45-107">'ndaki Değerlendirmenin sonlandırıldığı iş parçacığını temsil eden ICorDebugThread nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1ba45-107">[in] A pointer to an ICorDebugThread object that represents the thread in which the evaluation terminated.</span></span>  
  
 `pEval`  
 <span data-ttu-id="1ba45-108">'ndaki Değerlendirmeyi gerçekleştiren kodu temsil eden ıcorıncode Geval nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1ba45-108">[in] A pointer to an ICorDebugEval object that represents the code that performed the evaluation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ba45-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1ba45-109">Requirements</span></span>  
 <span data-ttu-id="1ba45-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1ba45-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ba45-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="1ba45-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1ba45-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="1ba45-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1ba45-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1ba45-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ba45-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1ba45-114">See also</span></span>

- [<span data-ttu-id="1ba45-115">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1ba45-115">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
