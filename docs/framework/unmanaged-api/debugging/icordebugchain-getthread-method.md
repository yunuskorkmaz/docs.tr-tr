---
description: ': Icordebugzincirine:: GetThread metodu hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 090cb40c3681792ce4a30cd342e65dc02ac3f381
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99694930"
---
# <a name="icordebugchaingetthread-method"></a><span data-ttu-id="2f830-103">ICorDebugChain::GetThread Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2f830-103">ICorDebugChain::GetThread Method</span></span>

<span data-ttu-id="2f830-104">Bu çağrı zincirinin parçası olduğu fiziksel iş parçacığını alır.</span><span class="sxs-lookup"><span data-stu-id="2f830-104">Gets the physical thread this call chain is part of.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f830-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2f830-105">Syntax</span></span>  
  
```cpp  
HRESULT GetThread (  
    [out] ICorDebugThread    **ppThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2f830-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2f830-106">Parameters</span></span>  

 `ppThread`  
 <span data-ttu-id="2f830-107">dışı Bu çağrı zincirinin parçası olduğu fiziksel iş parçacığını temsil eden ICorDebugThread nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="2f830-107">[out] A pointer to an ICorDebugThread object that represents the physical thread this call chain is part of.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2f830-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2f830-108">Requirements</span></span>  

 <span data-ttu-id="2f830-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2f830-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2f830-110">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="2f830-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2f830-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="2f830-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2f830-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2f830-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
