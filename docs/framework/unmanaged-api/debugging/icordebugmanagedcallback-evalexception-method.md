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
ms.openlocfilehash: 3ae93081bd201f745fa47bc01a9c6fcbf6e9f63c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76781868"
---
# <a name="icordebugmanagedcallbackevalexception-method"></a><span data-ttu-id="ff932-102">ICorDebugManagedCallback::EvalException Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ff932-102">ICorDebugManagedCallback::EvalException Method</span></span>
<span data-ttu-id="ff932-103">Hata ayıklayıcıya bir değerlendirmenin işlenmeyen bir özel durumla sonlandırıldığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="ff932-103">Notifies the debugger that an evaluation has terminated with an unhandled exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff932-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ff932-104">Syntax</span></span>  
  
```cpp  
HRESULT EvalException (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread,  
    [in] ICorDebugEval      *pEval  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ff932-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ff932-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="ff932-106">'ndaki Değerlendirmenin sonlandırıldığı uygulama etki alanını temsil eden ICorDebugAppDomain nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ff932-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain in which the evaluation terminated.</span></span>  
  
 `pThread`  
 <span data-ttu-id="ff932-107">'ndaki Değerlendirmenin sonlandırıldığı iş parçacığını temsil eden ICorDebugThread nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ff932-107">[in] A pointer to an ICorDebugThread object that represents the thread in which the evaluation terminated.</span></span>  
  
 `pEval`  
 <span data-ttu-id="ff932-108">'ndaki Değerlendirmeyi gerçekleştiren kodu temsil eden ıcorıncode Geval nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ff932-108">[in] A pointer to an ICorDebugEval object that represents the code that performed the evaluation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff932-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ff932-109">Requirements</span></span>  
 <span data-ttu-id="ff932-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ff932-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff932-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ff932-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ff932-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="ff932-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ff932-113">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff932-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff932-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ff932-114">See also</span></span>

- [<span data-ttu-id="ff932-115">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ff932-115">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
