---
description: ': ICorDebugManagedCallback:: EvalException Yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 0938276a854020efa897499af8c0fd69c0541124
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790990"
---
# <a name="icordebugmanagedcallbackevalexception-method"></a><span data-ttu-id="d2a13-103">ICorDebugManagedCallback::EvalException Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d2a13-103">ICorDebugManagedCallback::EvalException Method</span></span>

<span data-ttu-id="d2a13-104">Hata ayıklayıcıya bir değerlendirmenin işlenmeyen bir özel durumla sonlandırıldığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="d2a13-104">Notifies the debugger that an evaluation has terminated with an unhandled exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2a13-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d2a13-105">Syntax</span></span>  
  
```cpp  
HRESULT EvalException (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread,  
    [in] ICorDebugEval      *pEval  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d2a13-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d2a13-106">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="d2a13-107">'ndaki Değerlendirmenin sonlandırıldığı uygulama etki alanını temsil eden ICorDebugAppDomain nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d2a13-107">[in] A pointer to an ICorDebugAppDomain object that represents the application domain in which the evaluation terminated.</span></span>  
  
 `pThread`  
 <span data-ttu-id="d2a13-108">'ndaki Değerlendirmenin sonlandırıldığı iş parçacığını temsil eden ICorDebugThread nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d2a13-108">[in] A pointer to an ICorDebugThread object that represents the thread in which the evaluation terminated.</span></span>  
  
 `pEval`  
 <span data-ttu-id="d2a13-109">'ndaki Değerlendirmeyi gerçekleştiren kodu temsil eden ıcorıncode Geval nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d2a13-109">[in] A pointer to an ICorDebugEval object that represents the code that performed the evaluation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d2a13-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d2a13-110">Requirements</span></span>  

 <span data-ttu-id="d2a13-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d2a13-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d2a13-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d2a13-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d2a13-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="d2a13-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d2a13-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d2a13-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2a13-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d2a13-115">See also</span></span>

- [<span data-ttu-id="d2a13-116">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d2a13-116">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
