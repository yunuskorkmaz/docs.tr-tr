---
title: ICorDebugObjectValue::IsValueClass Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugObjectValue.IsValueClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectValue::IsValueClass
helpviewer_keywords:
- ICorDebugObjectValue::IsValueClass method [.NET Framework debugging]
- IsValueClass method [.NET Framework debugging]
ms.assetid: 13d89a4a-5d9d-4a79-9600-5e2a98c3d166
topic_type:
- apiref
ms.openlocfilehash: 0682c0786182422587adb976ff6bc2455b9e5cdc
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128941"
---
# <a name="icordebugobjectvalueisvalueclass-method"></a><span data-ttu-id="0f99d-102">ICorDebugObjectValue::IsValueClass Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0f99d-102">ICorDebugObjectValue::IsValueClass Method</span></span>
<span data-ttu-id="0f99d-103">Bu nesne değerinin bir değer türü olup olmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="0f99d-103">Gets a value that indicates whether this object value is a value type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f99d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0f99d-104">Syntax</span></span>  
  
```cpp  
HRESULT IsValueClass (  
    [out] BOOL               *pbIsValueClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0f99d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0f99d-105">Parameters</span></span>  
 `pbIsValueClass`  
 <span data-ttu-id="0f99d-106">dışı Bu "ICorDebugObjectValue" ile temsil edilen nesne değeri, başvuru türü yerine bir değer türü ise `true` Boolean değeri işaretçisi; Aksi takdirde, `pbIsValueClass` `false`.</span><span class="sxs-lookup"><span data-stu-id="0f99d-106">[out] A pointer to a Boolean value that is `true` if the object value, represented by this "ICorDebugObjectValue", is a value type rather than a reference type; otherwise, `pbIsValueClass` is `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0f99d-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0f99d-107">Requirements</span></span>  
 <span data-ttu-id="0f99d-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0f99d-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0f99d-109">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="0f99d-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0f99d-110">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="0f99d-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0f99d-111">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0f99d-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f99d-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0f99d-112">See also</span></span>
