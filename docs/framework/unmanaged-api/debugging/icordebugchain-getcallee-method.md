---
title: ICorDebugChain::GetCallee Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetCallee
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetCallee method
helpviewer_keywords:
- ICorDebugChain::GetCallee method [.NET Framework debugging]
- GetCallee method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: 19560c79-abdc-4bdf-a5fe-eb362a59edc0
topic_type:
- apiref
ms.openlocfilehash: 5d28af09faae84b0482d438ae33f593f250490c1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73196334"
---
# <a name="icordebugchaingetcallee-method"></a><span data-ttu-id="3246c-102">ICorDebugChain::GetCallee Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3246c-102">ICorDebugChain::GetCallee Method</span></span>
<span data-ttu-id="3246c-103">Bu zincir tarafından çağrılan zinciri alır.</span><span class="sxs-lookup"><span data-stu-id="3246c-103">Gets the chain that was called by this chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3246c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3246c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCallee (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3246c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3246c-105">Parameters</span></span>  
 `ppChain`  
 <span data-ttu-id="3246c-106">dışı Çağrılan zinciri temsil eden bir ıcordebugzincirleri nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="3246c-106">[out] A pointer to the address of an ICorDebugChain object that represents the called chain.</span></span> <span data-ttu-id="3246c-107">Bu zincir Şu anda yürütüliyorsa (yani, bu zincir, çağrılan bir zincirin dönmesi beklenmez) `ppChain` null olur.</span><span class="sxs-lookup"><span data-stu-id="3246c-107">If this chain is currently executing (that is, if this chain is not waiting for a called chain to return), `ppChain` will be null.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3246c-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3246c-108">Remarks</span></span>  
 <span data-ttu-id="3246c-109">Bu zincir, yürütmeyi devam etmeden önce çağrılan zincirin döndürülmesini bekler.</span><span class="sxs-lookup"><span data-stu-id="3246c-109">This chain will wait for the called chain to return before it resumes execution.</span></span> <span data-ttu-id="3246c-110">Çağrılan zincir, çapraz iş parçacığı sıralanmış çağrılar söz konusu olduğunda başka bir iş parçacığında olabilir.</span><span class="sxs-lookup"><span data-stu-id="3246c-110">The called chain may be on another thread in the case of cross-thread marshaled calls.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3246c-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3246c-111">Requirements</span></span>  
 <span data-ttu-id="3246c-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3246c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3246c-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="3246c-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3246c-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="3246c-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3246c-115">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3246c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
