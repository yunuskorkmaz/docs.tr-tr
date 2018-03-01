---
title: ICorDebugFunction::GetModule Metodu
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
- ICorDebugFunction.GetModule
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetModule
helpviewer_keywords:
- ICorDebugFunction::GetModule method [.NET Framework debugging]
- GetModule method, ICorDebugFunction interface [.NET Framework debugging]
ms.assetid: 5031a5d3-2564-412a-9007-e36d4631308a
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 59808b2a1de969f7d530a1be4cb500fc32cec33f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugfunctiongetmodule-method"></a><span data-ttu-id="4eb3d-102">ICorDebugFunction::GetModule Metodu</span><span class="sxs-lookup"><span data-stu-id="4eb3d-102">ICorDebugFunction::GetModule Method</span></span>
<span data-ttu-id="4eb3d-103">Bu işlevin tanımlı olduğu modülü alır.</span><span class="sxs-lookup"><span data-stu-id="4eb3d-103">Gets the module in which this function is defined.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4eb3d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4eb3d-104">Syntax</span></span>  
  
```  
HRESULT GetModule (  
    [out] ICorDebugModule **ppModule  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4eb3d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4eb3d-105">Parameters</span></span>  
 `ppModule`  
 <span data-ttu-id="4eb3d-106">[out] Bu işlevin tanımlı olduğu modülü temsil eden bir Icordebugmodule nesne adresini gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="4eb3d-106">[out] A pointer to the address of an ICorDebugModule object that represents the module in which this function is defined.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4eb3d-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4eb3d-107">Requirements</span></span>  
 <span data-ttu-id="4eb3d-108">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4eb3d-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4eb3d-109">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4eb3d-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4eb3d-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4eb3d-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4eb3d-111">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4eb3d-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
