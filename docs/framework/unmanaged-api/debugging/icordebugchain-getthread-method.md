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
ms.openlocfilehash: 28b54026c8743f31a420e164944f60709e2e271b
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894365"
---
# <a name="icordebugchaingetthread-method"></a><span data-ttu-id="975f2-102">ICorDebugChain::GetThread Yöntemi</span><span class="sxs-lookup"><span data-stu-id="975f2-102">ICorDebugChain::GetThread Method</span></span>
<span data-ttu-id="975f2-103">Bu çağrı zincirinin parçası olduğu fiziksel iş parçacığını alır.</span><span class="sxs-lookup"><span data-stu-id="975f2-103">Gets the physical thread this call chain is part of.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="975f2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="975f2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThread (  
    [out] ICorDebugThread    **ppThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="975f2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="975f2-105">Parameters</span></span>  
 `ppThread`  
 <span data-ttu-id="975f2-106">dışı Bu çağrı zincirinin parçası olduğu fiziksel iş parçacığını temsil eden ICorDebugThread nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="975f2-106">[out] A pointer to an ICorDebugThread object that represents the physical thread this call chain is part of.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="975f2-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="975f2-107">Requirements</span></span>  
 <span data-ttu-id="975f2-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="975f2-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="975f2-109">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="975f2-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="975f2-110">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="975f2-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="975f2-111">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="975f2-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
