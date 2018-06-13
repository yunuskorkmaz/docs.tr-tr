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
ms.openlocfilehash: 403adfbfe96558196e5ba64ddcbe0be637ba1b1c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33403259"
---
# <a name="icordebugarrayvaluegetelementtype-method"></a><span data-ttu-id="af2ab-102">ICorDebugArrayValue::GetElementType Metodu</span><span class="sxs-lookup"><span data-stu-id="af2ab-102">ICorDebugArrayValue::GetElementType Method</span></span>
<span data-ttu-id="af2ab-103">Dizideki öğeler basit türünü belirten bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="af2ab-103">Gets a value that indicates the simple type of the elements in the array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af2ab-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="af2ab-104">Syntax</span></span>  
  
```  
HRESULT GetElementType (  
    [out] CorElementType  *pType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="af2ab-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="af2ab-105">Parameters</span></span>  
 `pType`  
 <span data-ttu-id="af2ab-106">[out] Türünü gösteren CorElementType numaralandırması değerini gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="af2ab-106">[out] A pointer to a value of the CorElementType enumeration that indicates the type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af2ab-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="af2ab-107">Requirements</span></span>  
 <span data-ttu-id="af2ab-108">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="af2ab-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af2ab-109">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="af2ab-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="af2ab-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="af2ab-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="af2ab-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af2ab-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
