---
title: ICorDebugChain::GetThread Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetThread
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetThread
helpviewer_keywords:
- GetThread method, ICorDebugChain interface [.NET Framework debugging]
- ICorDebugChain::GetThread method [.NET Framework debugging]
ms.assetid: b3390319-6366-418c-ba80-b552ac4dfc1e
topic_type:
- apiref
ms.openlocfilehash: ad220289b45078130a0a41e67373fd3384ae9682
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724422"
---
# <a name="icordebugchaingetthread-method"></a><span data-ttu-id="c52c9-102">ICorDebugChain::GetThread Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c52c9-102">ICorDebugChain::GetThread Method</span></span>

<span data-ttu-id="c52c9-103">Bu çağrı zincirinin parçası olduğu fiziksel iş parçacığını alır.</span><span class="sxs-lookup"><span data-stu-id="c52c9-103">Gets the physical thread this call chain is part of.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c52c9-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="c52c9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThread (  
    [out] ICorDebugThread    **ppThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c52c9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c52c9-105">Parameters</span></span>  

 `ppThread`  
 <span data-ttu-id="c52c9-106">dışı Bu çağrı zincirinin parçası olduğu fiziksel iş parçacığını temsil eden ICorDebugThread nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c52c9-106">[out] A pointer to an ICorDebugThread object that represents the physical thread this call chain is part of.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c52c9-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c52c9-107">Requirements</span></span>  

 <span data-ttu-id="c52c9-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c52c9-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c52c9-109">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c52c9-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c52c9-110">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="c52c9-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c52c9-111">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c52c9-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
