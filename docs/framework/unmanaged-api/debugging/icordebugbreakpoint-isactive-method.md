---
title: ICorDebugBreakpoint::IsActive Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugBreakpoint.IsActive
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBreakpoint::IsActive
helpviewer_keywords:
- ICorDebugBreakpoint::IsActive method [.NET Framework debugging]
- IsActive method, ICorDebugBreakpoint interface [.NET Framework debugging]
ms.assetid: 06e583d6-d88a-4ff5-bb95-5c48618a461c
topic_type:
- apiref
ms.openlocfilehash: 064f9727b221dd64a58f8cd5e103271e37020786
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730181"
---
# <a name="icordebugbreakpointisactive-method"></a><span data-ttu-id="d81f0-102">ICorDebugBreakpoint::IsActive Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d81f0-102">ICorDebugBreakpoint::IsActive Method</span></span>

<span data-ttu-id="d81f0-103">Bu, etkin olup olmadığını gösteren bir değer alır `ICorDebugBreakpoint` .</span><span class="sxs-lookup"><span data-stu-id="d81f0-103">Gets a value that indicates whether this `ICorDebugBreakpoint` is active.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d81f0-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="d81f0-104">Syntax</span></span>  
  
```cpp  
HRESULT IsActive (  
    [out] BOOL *pbActive  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d81f0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d81f0-105">Parameters</span></span>  

 `pbActive`  
 <span data-ttu-id="d81f0-106">[out] `true` Bu kesme noktası etkinse; Aksi takdirde, `false` .</span><span class="sxs-lookup"><span data-stu-id="d81f0-106">[out] `true` if this breakpoint is active; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d81f0-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d81f0-107">Requirements</span></span>  

 <span data-ttu-id="d81f0-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d81f0-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d81f0-109">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d81f0-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d81f0-110">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="d81f0-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d81f0-111">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d81f0-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
