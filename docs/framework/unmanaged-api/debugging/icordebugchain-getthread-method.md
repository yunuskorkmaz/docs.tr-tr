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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d05002ecdb903a1adfeea88930083ba472164324
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67745629"
---
# <a name="icordebugchaingetthread-method"></a><span data-ttu-id="e14dd-102">ICorDebugChain::GetThread Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e14dd-102">ICorDebugChain::GetThread Method</span></span>
<span data-ttu-id="e14dd-103">Bu çağrı zinciri fiziksel iş parçacığı parçası alır.</span><span class="sxs-lookup"><span data-stu-id="e14dd-103">Gets the physical thread this call chain is part of.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e14dd-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e14dd-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThread (  
    [out] ICorDebugThread    **ppThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e14dd-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e14dd-105">Parameters</span></span>  
 `ppThread`  
 <span data-ttu-id="e14dd-106">[out] Bir fiziksel iş parçacığını temsil eden bir Icordebugthread nesne bu çağrı zincirini parçası işaretçisidir.</span><span class="sxs-lookup"><span data-stu-id="e14dd-106">[out] A pointer to an ICorDebugThread object that represents the physical thread this call chain is part of.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e14dd-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e14dd-107">Requirements</span></span>  
 <span data-ttu-id="e14dd-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e14dd-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e14dd-109">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e14dd-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e14dd-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e14dd-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e14dd-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e14dd-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
