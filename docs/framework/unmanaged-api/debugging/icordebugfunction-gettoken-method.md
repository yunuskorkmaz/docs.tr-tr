---
title: ICorDebugFunction::GetToken Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetToken
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetToken
helpviewer_keywords:
- ICorDebugFunction::GetToken method [.NET Framework debugging]
- GetToken method, ICorDebugFunction interface [.NET Framework debugging]
ms.assetid: c6bbf479-062e-48e9-9c70-0f92e293e36a
topic_type:
- apiref
ms.openlocfilehash: 4229d567fc4ced5e3b78b390ced29fb9ea60f93b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137839"
---
# <a name="icordebugfunctiongettoken-method"></a><span data-ttu-id="22098-102">ICorDebugFunction::GetToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="22098-102">ICorDebugFunction::GetToken Method</span></span>
<span data-ttu-id="22098-103">Bu işlev için meta veri belirtecini alır.</span><span class="sxs-lookup"><span data-stu-id="22098-103">Gets the metadata token for this function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22098-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="22098-104">Syntax</span></span>  
  
```cpp  
HRESULT GetToken (  
    [out] mdMethodDef *pMethodDef  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="22098-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="22098-105">Parameters</span></span>  
 `pMethodDef`  
 <span data-ttu-id="22098-106">dışı Bu işlevin meta verilerine başvuran `mdMethodDef` belirtece yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="22098-106">[out] A pointer to an `mdMethodDef` token that references the metadata for this function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="22098-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="22098-107">Requirements</span></span>  
 <span data-ttu-id="22098-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="22098-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="22098-109">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="22098-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="22098-110">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="22098-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="22098-111">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="22098-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
