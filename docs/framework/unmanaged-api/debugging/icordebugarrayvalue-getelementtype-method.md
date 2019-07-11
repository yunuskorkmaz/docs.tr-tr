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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8e0159ce6ad1087838681214533d386f4d44cee2
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67737465"
---
# <a name="icordebugarrayvaluegetelementtype-method"></a><span data-ttu-id="60222-102">ICorDebugArrayValue::GetElementType Metodu</span><span class="sxs-lookup"><span data-stu-id="60222-102">ICorDebugArrayValue::GetElementType Method</span></span>
<span data-ttu-id="60222-103">Basit dizideki öğelerin türünü belirten bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="60222-103">Gets a value that indicates the simple type of the elements in the array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60222-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="60222-104">Syntax</span></span>  
  
```cpp  
HRESULT GetElementType (  
    [out] CorElementType  *pType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="60222-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="60222-105">Parameters</span></span>  
 `pType`  
 <span data-ttu-id="60222-106">[out] CorElementType numaralandırma türü gösteren bir değer için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="60222-106">[out] A pointer to a value of the CorElementType enumeration that indicates the type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="60222-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="60222-107">Requirements</span></span>  
 <span data-ttu-id="60222-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="60222-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60222-109">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="60222-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="60222-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="60222-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="60222-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="60222-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
