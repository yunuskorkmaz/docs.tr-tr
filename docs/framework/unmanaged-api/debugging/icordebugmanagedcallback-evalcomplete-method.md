---
description: ': ICorDebugManagedCallback:: Evaltamamlamaya Me yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 729b00bc630ef5d6e508b75bd6483580f1dd75b5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791042"
---
# <a name="icordebugmanagedcallbackevalcomplete-method"></a><span data-ttu-id="44e4c-103">ICorDebugManagedCallback::EvalComplete Yöntemi</span><span class="sxs-lookup"><span data-stu-id="44e4c-103">ICorDebugManagedCallback::EvalComplete Method</span></span>

<span data-ttu-id="44e4c-104">Hata ayıklayıcıya bir değerlendirmenin tamamlandığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="44e4c-104">Notifies the debugger that an evaluation has been completed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44e4c-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="44e4c-105">Syntax</span></span>  
  
```cpp  
HRESULT EvalComplete (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread,  
    [in] ICorDebugEval      *pEval  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="44e4c-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="44e4c-106">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="44e4c-107">'ndaki Değerlendirmede gerçekleştirilen uygulama etki alanını temsil eden ICorDebugAppDomain nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="44e4c-107">[in] A pointer to an ICorDebugAppDomain object that represents the application domain in which the evaluation was performed.</span></span>  
  
 `pThread`  
 <span data-ttu-id="44e4c-108">'ndaki Değerlendirmede gerçekleştirilen iş parçacığını temsil eden ICorDebugThread nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="44e4c-108">[in] A pointer to an ICorDebugThread object that represents the thread in which the evaluation was performed.</span></span>  
  
 `pEval`  
 <span data-ttu-id="44e4c-109">'ndaki Değerlendirmeyi gerçekleştiren kodu temsil eden ıcorıncode Geval nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="44e4c-109">[in] A pointer to an ICorDebugEval object that represents the code that performed the evaluation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="44e4c-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="44e4c-110">Requirements</span></span>  

 <span data-ttu-id="44e4c-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="44e4c-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="44e4c-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="44e4c-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="44e4c-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="44e4c-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="44e4c-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="44e4c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44e4c-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="44e4c-115">See also</span></span>

- [<span data-ttu-id="44e4c-116">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="44e4c-116">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
