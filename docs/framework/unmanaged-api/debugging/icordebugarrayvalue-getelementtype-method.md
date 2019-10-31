---
title: ICorDebugArrayValue::GetElementType Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.GetElementType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::GetElementType
helpviewer_keywords:
- ICorDebugArrayValue::GetElementType method [.NET Framework debugging]
- GetElementType method [.NET Framework debugging]
ms.assetid: ed71961e-ae9b-4dfc-9554-06637696d697
topic_type:
- apiref
ms.openlocfilehash: d4de3405f84bfc08f7e1519bc7f9604eb1f5a14e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73088298"
---
# <a name="icordebugarrayvaluegetelementtype-method"></a><span data-ttu-id="cfbf9-102">ICorDebugArrayValue::GetElementType Metodu</span><span class="sxs-lookup"><span data-stu-id="cfbf9-102">ICorDebugArrayValue::GetElementType Method</span></span>
<span data-ttu-id="cfbf9-103">Dizideki öğelerin basit türünü gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="cfbf9-103">Gets a value that indicates the simple type of the elements in the array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cfbf9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cfbf9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetElementType (  
    [out] CorElementType  *pType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cfbf9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cfbf9-105">Parameters</span></span>  
 `pType`  
 <span data-ttu-id="cfbf9-106">dışı Türü gösteren CorElementType numaralandırması değerine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="cfbf9-106">[out] A pointer to a value of the CorElementType enumeration that indicates the type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cfbf9-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cfbf9-107">Requirements</span></span>  
 <span data-ttu-id="cfbf9-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cfbf9-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cfbf9-109">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="cfbf9-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cfbf9-110">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="cfbf9-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cfbf9-111">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cfbf9-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
