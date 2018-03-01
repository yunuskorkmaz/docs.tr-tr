---
title: "ICorDebugBreakpoint::Activate Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugBreakpoint.Activate
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBreakpoint::Activate
helpviewer_keywords:
- ICorDebugBreakpoint::Activate method [.NET Framework debugging]
- Activate method [.NET Framework debugging]
ms.assetid: e30c29f7-3f19-4081-b572-a731aa14cd44
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ef0880c40cb09b836938f253447f5ffeaaec207b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugbreakpointactivate-method"></a><span data-ttu-id="f0823-102">ICorDebugBreakpoint::Activate Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f0823-102">ICorDebugBreakpoint::Activate Method</span></span>
<span data-ttu-id="f0823-103">Bu etkin durumunu ayarlar `ICorDebugBreakpoint`.</span><span class="sxs-lookup"><span data-stu-id="f0823-103">Sets the active state of this `ICorDebugBreakpoint`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0823-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f0823-104">Syntax</span></span>  
  
```  
HRESULT Activate (  
    [in] BOOL bActive  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f0823-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f0823-105">Parameters</span></span>  
 `bActive`  
 <span data-ttu-id="f0823-106">[in] Bu değer ayarlanırsa `true` durumu etkin olarak; belirtmek için Aksi takdirde, bu değer ayarlanırsa `false`.</span><span class="sxs-lookup"><span data-stu-id="f0823-106">[in] Set this value to `true` to specify the state as active; otherwise, set this value to `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0823-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f0823-107">Requirements</span></span>  
 <span data-ttu-id="f0823-108">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f0823-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0823-109">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f0823-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f0823-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f0823-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f0823-111">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f0823-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
