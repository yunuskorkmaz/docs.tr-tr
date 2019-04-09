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
ms.openlocfilehash: 0104a52c3aa206f86daff30d9d16298e6beae324
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59099462"
---
# <a name="icordebugcodegetfunction-method"></a><span data-ttu-id="e7fe0-102">ICorDebugCode::GetFunction Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e7fe0-102">ICorDebugCode::GetFunction Method</span></span>
<span data-ttu-id="e7fe0-103">"Bu"Icordebugcode"ile ilişkili ICorDebugFunction" alır.</span><span class="sxs-lookup"><span data-stu-id="e7fe0-103">Gets the "ICorDebugFunction" associated with this "ICorDebugCode".</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7fe0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e7fe0-104">Syntax</span></span>  
  
```  
HRESULT GetFunction (  
    [out] ICorDebugFunction **ppFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e7fe0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e7fe0-105">Parameters</span></span>  
 `ppFunction`  
 <span data-ttu-id="e7fe0-106">[out] İşlevin adresi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e7fe0-106">[out] A pointer to the address of the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e7fe0-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e7fe0-107">Remarks</span></span>  
 `ICorDebugCode` <span data-ttu-id="e7fe0-108">ve `ICorDebugFunction` bire bir ilişki korumak.</span><span class="sxs-lookup"><span data-stu-id="e7fe0-108">and `ICorDebugFunction` maintain a one-to-one relationship.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e7fe0-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e7fe0-109">Requirements</span></span>  
 <span data-ttu-id="e7fe0-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e7fe0-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7fe0-111">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e7fe0-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e7fe0-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e7fe0-112">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="e7fe0-113">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="e7fe0-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e7fe0-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e7fe0-114">See also</span></span>
