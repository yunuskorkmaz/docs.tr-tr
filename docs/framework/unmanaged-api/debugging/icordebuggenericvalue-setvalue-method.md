---
title: ICorDebugGenericValue::SetValue Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugGenericValue.SetValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGenericValue::SetValue
helpviewer_keywords:
- ICorDebugGenericValue::SetValue method [.NET Framework debugging]
- SetValue method, ICorDebugGenericValue interface [.NET Framework debugging]
ms.assetid: ed4c6458-0435-44fc-8e78-8ba00be362f2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0b6907cdf78fc70c75ddd711cd8593427857b172
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67756896"
---
# <a name="icordebuggenericvaluesetvalue-method"></a><span data-ttu-id="5d64c-102">ICorDebugGenericValue::SetValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5d64c-102">ICorDebugGenericValue::SetValue Method</span></span>
<span data-ttu-id="5d64c-103">Yeni bir değer belirtilen arabellek kopyalar.</span><span class="sxs-lookup"><span data-stu-id="5d64c-103">Copies a new value from the specified buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d64c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5d64c-104">Syntax</span></span>  
  
```cpp  
HRESULT SetValue (  
    [in] void      *pFrom  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5d64c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5d64c-105">Parameters</span></span>  
 `pFrom`  
 <span data-ttu-id="5d64c-106">[in] Arabellek için işaretçi değeri kopyalanacak.</span><span class="sxs-lookup"><span data-stu-id="5d64c-106">[in] A pointer to the buffer from which to copy the value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5d64c-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5d64c-107">Remarks</span></span>  
 <span data-ttu-id="5d64c-108">Başvuru türleri için başvuru içeriği bir değerdir.</span><span class="sxs-lookup"><span data-stu-id="5d64c-108">For reference types, the value is the reference, not the content.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d64c-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5d64c-109">Requirements</span></span>  
 <span data-ttu-id="5d64c-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5d64c-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d64c-111">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5d64c-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5d64c-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5d64c-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5d64c-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5d64c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
