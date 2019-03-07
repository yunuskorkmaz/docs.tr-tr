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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ed5a7657affde335acf79952d77bbdb7ac42c7a0
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57490469"
---
# <a name="icordebugchaingetcallee-method"></a><span data-ttu-id="d33fe-102">ICorDebugChain::GetCallee Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d33fe-102">ICorDebugChain::GetCallee Method</span></span>
<span data-ttu-id="d33fe-103">Bu zincir tarafından çağrıldı zinciri alır.</span><span class="sxs-lookup"><span data-stu-id="d33fe-103">Gets the chain that was called by this chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d33fe-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d33fe-104">Syntax</span></span>  
  
```  
HRESULT GetCallee (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d33fe-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d33fe-105">Parameters</span></span>  
 `ppChain`  
 <span data-ttu-id="d33fe-106">[out] Çağrılan zincirini temsil eden bir Icordebugchain nesnenin adresi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d33fe-106">[out] A pointer to the address of an ICorDebugChain object that represents the called chain.</span></span> <span data-ttu-id="d33fe-107">Bu zincir (diğer bir deyişle, bu zincir döndürmek çağrılan bir zincirinde beklemiyorsa) şu anda yürütülüyorsa `ppChain` null olacaktır.</span><span class="sxs-lookup"><span data-stu-id="d33fe-107">If this chain is currently executing (that is, if this chain is not waiting for a called chain to return), `ppChain` will be null.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d33fe-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d33fe-108">Remarks</span></span>  
 <span data-ttu-id="d33fe-109">Bu zincir yürütmeyi devam ettirir önce döndürmek çağrılan zinciri için bekler.</span><span class="sxs-lookup"><span data-stu-id="d33fe-109">This chain will wait for the called chain to return before it resumes execution.</span></span> <span data-ttu-id="d33fe-110">Çağrılan zinciri sıralanmış iş parçacıkları arası çağrılar söz konusu olduğunda başka bir iş parçacığında olabilir.</span><span class="sxs-lookup"><span data-stu-id="d33fe-110">The called chain may be on another thread in the case of cross-thread marshaled calls.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d33fe-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d33fe-111">Requirements</span></span>  
 <span data-ttu-id="d33fe-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d33fe-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d33fe-113">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d33fe-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d33fe-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d33fe-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d33fe-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d33fe-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
