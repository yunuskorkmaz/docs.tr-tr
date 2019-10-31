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
ms.openlocfilehash: 217ca0a850926e5f697340cece264c6ed442a9bb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125639"
---
# <a name="icordebugcodegetfunction-method"></a><span data-ttu-id="cc1f7-102">ICorDebugCode::GetFunction Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cc1f7-102">ICorDebugCode::GetFunction Method</span></span>
<span data-ttu-id="cc1f7-103">Bu "ICorDebugCode" ile ilişkili "ICorDebugFunction" öğesini alır.</span><span class="sxs-lookup"><span data-stu-id="cc1f7-103">Gets the "ICorDebugFunction" associated with this "ICorDebugCode".</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc1f7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cc1f7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunction (  
    [out] ICorDebugFunction **ppFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cc1f7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cc1f7-105">Parameters</span></span>  
 `ppFunction`  
 <span data-ttu-id="cc1f7-106">dışı İşlevin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="cc1f7-106">[out] A pointer to the address of the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cc1f7-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cc1f7-107">Remarks</span></span>  
 <span data-ttu-id="cc1f7-108">`ICorDebugCode` ve `ICorDebugFunction` bire bir ilişki bakımını sağlar.</span><span class="sxs-lookup"><span data-stu-id="cc1f7-108">`ICorDebugCode` and `ICorDebugFunction` maintain a one-to-one relationship.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc1f7-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cc1f7-109">Requirements</span></span>  
 <span data-ttu-id="cc1f7-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cc1f7-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc1f7-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="cc1f7-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cc1f7-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="cc1f7-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cc1f7-113">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc1f7-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
