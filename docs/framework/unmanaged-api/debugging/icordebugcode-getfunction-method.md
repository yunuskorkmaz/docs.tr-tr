---
title: ICorDebugCode::GetFunction Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugCode.GetFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::GetFunction
helpviewer_keywords:
- GetFunction method, ICorDebugCode interface [.NET Framework debugging]
- ICorDebugCode::GetFunction method [.NET Framework debugging]
ms.assetid: c568b737-fdb2-4816-accd-051f5ab760f1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c5d8168649f6a0c75844da0ee68bf3782efc9024
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57483876"
---
# <a name="icordebugcodegetfunction-method"></a><span data-ttu-id="9c0c2-102">ICorDebugCode::GetFunction Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9c0c2-102">ICorDebugCode::GetFunction Method</span></span>
<span data-ttu-id="9c0c2-103">"Bu"Icordebugcode"ile ilişkili ICorDebugFunction" alır.</span><span class="sxs-lookup"><span data-stu-id="9c0c2-103">Gets the "ICorDebugFunction" associated with this "ICorDebugCode".</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c0c2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9c0c2-104">Syntax</span></span>  
  
```  
HRESULT GetFunction (  
    [out] ICorDebugFunction **ppFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9c0c2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9c0c2-105">Parameters</span></span>  
 `ppFunction`  
 <span data-ttu-id="9c0c2-106">[out] İşlevin adresi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="9c0c2-106">[out] A pointer to the address of the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9c0c2-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9c0c2-107">Remarks</span></span>  
 <span data-ttu-id="9c0c2-108">`ICorDebugCode` ve `ICorDebugFunction` bire bir ilişki korumak.</span><span class="sxs-lookup"><span data-stu-id="9c0c2-108">`ICorDebugCode` and `ICorDebugFunction` maintain a one-to-one relationship.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9c0c2-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9c0c2-109">Requirements</span></span>  
 <span data-ttu-id="9c0c2-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9c0c2-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9c0c2-111">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9c0c2-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9c0c2-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9c0c2-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9c0c2-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9c0c2-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c0c2-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9c0c2-114">See also</span></span>

