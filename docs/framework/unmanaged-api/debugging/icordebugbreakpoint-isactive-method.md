---
description: ': ICorDebugBreakpoint:: IsActive yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 49e98ccc3722c37b3ff5968215ef3f658601ea10
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99711797"
---
# <a name="icordebugbreakpointisactive-method"></a><span data-ttu-id="75e57-103">ICorDebugBreakpoint::IsActive Yöntemi</span><span class="sxs-lookup"><span data-stu-id="75e57-103">ICorDebugBreakpoint::IsActive Method</span></span>

<span data-ttu-id="75e57-104">Bu, etkin olup olmadığını gösteren bir değer alır `ICorDebugBreakpoint` .</span><span class="sxs-lookup"><span data-stu-id="75e57-104">Gets a value that indicates whether this `ICorDebugBreakpoint` is active.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75e57-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="75e57-105">Syntax</span></span>  
  
```cpp  
HRESULT IsActive (  
    [out] BOOL *pbActive  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="75e57-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="75e57-106">Parameters</span></span>  

 `pbActive`  
 <span data-ttu-id="75e57-107">[out] `true` Bu kesme noktası etkinse; Aksi takdirde, `false` .</span><span class="sxs-lookup"><span data-stu-id="75e57-107">[out] `true` if this breakpoint is active; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="75e57-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="75e57-108">Requirements</span></span>  

 <span data-ttu-id="75e57-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="75e57-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="75e57-110">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="75e57-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="75e57-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="75e57-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="75e57-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="75e57-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
