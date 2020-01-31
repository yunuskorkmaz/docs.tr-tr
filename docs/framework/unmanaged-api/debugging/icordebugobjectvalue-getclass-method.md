---
title: ICorDebugObjectValue::GetClass Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugObjectValue.GetClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectValue::GetClass
helpviewer_keywords:
- ICorDebugObjectValue::GetClass method [.NET Framework debugging]
- GetClass method, ICorDebugObjectValue interface [.NET Framework debugging]
ms.assetid: 5be25292-8357-445f-a09b-f997c0de761c
topic_type:
- apiref
ms.openlocfilehash: d15938e94d647fd5fded23c72bdc200d198d21a7
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792698"
---
# <a name="icordebugobjectvaluegetclass-method"></a><span data-ttu-id="5c40d-102">ICorDebugObjectValue::GetClass Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5c40d-102">ICorDebugObjectValue::GetClass Method</span></span>
<span data-ttu-id="5c40d-103">Bu nesne değerinin sınıfını alır.</span><span class="sxs-lookup"><span data-stu-id="5c40d-103">Gets the class of this object value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c40d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5c40d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetClass (  
    [out] ICorDebugClass     **ppClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5c40d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5c40d-105">Parameters</span></span>  
 `ppClass`  
 <span data-ttu-id="5c40d-106">dışı Bu "ICorDebugObjectValue" nesnesi tarafından temsil edilen nesne değerinin sınıfını temsil eden "ICorDebugClass" nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5c40d-106">[out] A pointer to the address of an "ICorDebugClass" object that represents the class of the object value represented by this "ICorDebugObjectValue" object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5c40d-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5c40d-107">Remarks</span></span>  
 <span data-ttu-id="5c40d-108">`GetClass` ve [ICorDebugValue:: GetType](icordebugvalue-gettype-method.md) yöntemlerinin her biri bir değerin türü hakkında bilgi döndürür; Bunlar her ikisi de genel türler tarafından [ICorDebugValue2:: GetExactType](icordebugvalue2-getexacttype-method.md)ile değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="5c40d-108">The `GetClass` and [ICorDebugValue::GetType](icordebugvalue-gettype-method.md) methods each return information about the type of a value; they are both superseded by the generics-aware [ICorDebugValue2::GetExactType](icordebugvalue2-getexacttype-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c40d-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5c40d-109">Requirements</span></span>  
 <span data-ttu-id="5c40d-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5c40d-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c40d-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="5c40d-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5c40d-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="5c40d-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5c40d-113">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5c40d-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c40d-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5c40d-114">See also</span></span>
