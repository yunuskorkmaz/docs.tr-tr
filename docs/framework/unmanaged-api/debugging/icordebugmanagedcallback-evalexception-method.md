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
ms.openlocfilehash: 6c59ede004ce02ee3d14a448fc61d1c092bd0d61
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721276"
---
# <a name="icordebugmanagedcallbackevalexception-method"></a><span data-ttu-id="bc39b-102">ICorDebugManagedCallback::EvalException Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bc39b-102">ICorDebugManagedCallback::EvalException Method</span></span>

<span data-ttu-id="bc39b-103">Hata ayıklayıcıya bir değerlendirmenin işlenmeyen bir özel durumla sonlandırıldığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="bc39b-103">Notifies the debugger that an evaluation has terminated with an unhandled exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc39b-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="bc39b-104">Syntax</span></span>  
  
```cpp  
HRESULT EvalException (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread,  
    [in] ICorDebugEval      *pEval  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bc39b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bc39b-105">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="bc39b-106">'ndaki Değerlendirmenin sonlandırıldığı uygulama etki alanını temsil eden ICorDebugAppDomain nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="bc39b-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain in which the evaluation terminated.</span></span>  
  
 `pThread`  
 <span data-ttu-id="bc39b-107">'ndaki Değerlendirmenin sonlandırıldığı iş parçacığını temsil eden ICorDebugThread nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="bc39b-107">[in] A pointer to an ICorDebugThread object that represents the thread in which the evaluation terminated.</span></span>  
  
 `pEval`  
 <span data-ttu-id="bc39b-108">'ndaki Değerlendirmeyi gerçekleştiren kodu temsil eden ıcorıncode Geval nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="bc39b-108">[in] A pointer to an ICorDebugEval object that represents the code that performed the evaluation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bc39b-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bc39b-109">Requirements</span></span>  

 <span data-ttu-id="bc39b-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bc39b-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bc39b-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="bc39b-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bc39b-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="bc39b-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bc39b-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bc39b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc39b-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bc39b-114">See also</span></span>

- [<span data-ttu-id="bc39b-115">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bc39b-115">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
