---
title: ICorDebugCode::GetFunction Metodu
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
ms.openlocfilehash: dd544619f9e5fb85a0b08b91ead8231ea25743cb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54651240"
---
# <a name="icordebugcodegetfunction-method"></a><span data-ttu-id="cebd6-102">ICorDebugCode::GetFunction Metodu</span><span class="sxs-lookup"><span data-stu-id="cebd6-102">ICorDebugCode::GetFunction Method</span></span>
<span data-ttu-id="cebd6-103">"Bu"Icordebugcode"ile ilişkili ICorDebugFunction" alır.</span><span class="sxs-lookup"><span data-stu-id="cebd6-103">Gets the "ICorDebugFunction" associated with this "ICorDebugCode".</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cebd6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cebd6-104">Syntax</span></span>  
  
```  
HRESULT GetFunction (  
    [out] ICorDebugFunction **ppFunction  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cebd6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cebd6-105">Parameters</span></span>  
 `ppFunction`  
 <span data-ttu-id="cebd6-106">[out] İşlevin adresi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="cebd6-106">[out] A pointer to the address of the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cebd6-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cebd6-107">Remarks</span></span>  
 <span data-ttu-id="cebd6-108">`ICorDebugCode` ve `ICorDebugFunction` bire bir ilişki korumak.</span><span class="sxs-lookup"><span data-stu-id="cebd6-108">`ICorDebugCode` and `ICorDebugFunction` maintain a one-to-one relationship.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cebd6-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cebd6-109">Requirements</span></span>  
 <span data-ttu-id="cebd6-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cebd6-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cebd6-111">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cebd6-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cebd6-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cebd6-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cebd6-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cebd6-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cebd6-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cebd6-114">See also</span></span>

