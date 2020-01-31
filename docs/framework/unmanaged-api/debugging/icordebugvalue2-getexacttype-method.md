---
title: ICorDebugValue2::GetExactType Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugValue2.GetExactType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue2::GetExactType
helpviewer_keywords:
- ICorDebugValue2::GetExactType method [.NET Framework debugging]
- GetExactType method [.NET Framework debugging]
ms.assetid: 8e9aae1b-d1b7-4b6e-b577-6faf36dcec85
topic_type:
- apiref
ms.openlocfilehash: 6c5e5d1c9f734e097fc9e871d7a0cffdc9bb9138
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791133"
---
# <a name="icordebugvalue2getexacttype-method"></a><span data-ttu-id="d8755-102">ICorDebugValue2::GetExactType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d8755-102">ICorDebugValue2::GetExactType Method</span></span>
<span data-ttu-id="d8755-103">Bu değerin <xref:System.Type> temsil eden bir "ICorDebugType" nesnesine bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="d8755-103">Gets an interface pointer to an "ICorDebugType" object that represents the <xref:System.Type> of this value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8755-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d8755-104">Syntax</span></span>  
  
```cpp  
HRESULT GetExactType (  
    [out] ICorDebugType   **ppType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d8755-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d8755-105">Parameters</span></span>  
 `ppType`  
 <span data-ttu-id="d8755-106">dışı Bu "ICorDebugValue2" nesnesi tarafından temsil edilen değerin <xref:System.Type> temsil eden bir `ICorDebugType` nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d8755-106">[out] A pointer to the address of an `ICorDebugType` object that represents the <xref:System.Type> of the value represented by this "ICorDebugValue2" object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d8755-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d8755-107">Remarks</span></span>  
 <span data-ttu-id="d8755-108">Genel türler kullanan `GetExactType` yöntemi hem [ICorDebugObjectValue:: GetClass](icordebugobjectvalue-getclass-method.md) hem de [ICorDebugValue:: GetType](icordebugvalue-gettype-method.md) yöntemlerinin yerini alır, her biri bir değer türü hakkında bilgi döndürür.</span><span class="sxs-lookup"><span data-stu-id="d8755-108">The generics-aware `GetExactType` method supersedes both the [ICorDebugObjectValue::GetClass](icordebugobjectvalue-getclass-method.md) and the [ICorDebugValue::GetType](icordebugvalue-gettype-method.md) methods, each of which return information about the type of a value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8755-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d8755-109">Requirements</span></span>  
 <span data-ttu-id="d8755-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d8755-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8755-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d8755-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d8755-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="d8755-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d8755-113">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8755-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8755-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d8755-114">See also</span></span>
