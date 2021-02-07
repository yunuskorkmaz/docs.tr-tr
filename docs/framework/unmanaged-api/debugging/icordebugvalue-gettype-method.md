---
description: ': ICorDebugValue:: GetType yöntemi hakkında daha fazla bilgi edinin'
title: ICorDebugValue::GetType Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugValue.GetType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue::GetType
helpviewer_keywords:
- ICorDebugValue::GetType method [.NET Framework debugging]
- GetType method, ICorDebugValue interface [.NET Framework debugging]
ms.assetid: 41e2d503-e1f1-407b-abe0-6a29adb3e0d1
topic_type:
- apiref
ms.openlocfilehash: 750e73634683a03e811d2756cc62c16b6dcea3de
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99690333"
---
# <a name="icordebugvaluegettype-method"></a><span data-ttu-id="62780-103">ICorDebugValue::GetType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="62780-103">ICorDebugValue::GetType Method</span></span>

<span data-ttu-id="62780-104">Bu "ICorDebugValue" nesnesinin temel türünü alır.</span><span class="sxs-lookup"><span data-stu-id="62780-104">Gets the primitive type of this "ICorDebugValue" object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62780-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="62780-105">Syntax</span></span>  
  
```cpp  
HRESULT GetType (  
    [out] CorElementType   *pType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="62780-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="62780-106">Parameters</span></span>  

 `pType`  
 <span data-ttu-id="62780-107">dışı Değerin türünü gösteren "CorElementType" sabit listesinin bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="62780-107">[out] A pointer to a value of the "CorElementType" enumeration that indicates the value's type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="62780-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="62780-108">Remarks</span></span>  

 <span data-ttu-id="62780-109">Nesne karmaşık bir çalışma zamanı türü ise, bu tür arabirimin uygun alt sınıfları aracılığıyla incelenebilir `ICorDebugValue` .</span><span class="sxs-lookup"><span data-stu-id="62780-109">If the object is a complex run-time type, that type may be examined through the appropriate subclasses of the `ICorDebugValue` interface.</span></span> <span data-ttu-id="62780-110">Örneğin, öğesinden devralan "ICorDebugObjectValue" `ICorDebugValue` karmaşık bir türü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="62780-110">For example, "ICorDebugObjectValue", which inherits from `ICorDebugValue`, represents a complex type.</span></span>  
  
 <span data-ttu-id="62780-111">`GetType`Ve [ICorDebugObjectValue:: GetClass](icordebugobjectvalue-getclass-method.md) metotları her biri bir değerin türü hakkında bilgi döndürür.</span><span class="sxs-lookup"><span data-stu-id="62780-111">The `GetType` and [ICorDebugObjectValue::GetClass](icordebugobjectvalue-getclass-method.md) methods each return information about the type of a value.</span></span> <span data-ttu-id="62780-112">Bunlar her ikisi de genel türler tarafından [ICorDebugValue2:: GetExactType](icordebugvalue2-getexacttype-method.md) yöntemi ile değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="62780-112">They are both superseded by the generics-aware [ICorDebugValue2::GetExactType](icordebugvalue2-getexacttype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="62780-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="62780-113">Requirements</span></span>  

 <span data-ttu-id="62780-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="62780-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62780-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="62780-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="62780-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="62780-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="62780-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="62780-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62780-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="62780-118">See also</span></span>
