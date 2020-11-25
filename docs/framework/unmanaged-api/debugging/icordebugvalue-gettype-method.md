---
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
ms.openlocfilehash: 06f403f0b653866428a41240f99833ec1180eb86
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731091"
---
# <a name="icordebugvaluegettype-method"></a><span data-ttu-id="276b5-102">ICorDebugValue::GetType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="276b5-102">ICorDebugValue::GetType Method</span></span>

<span data-ttu-id="276b5-103">Bu "ICorDebugValue" nesnesinin temel türünü alır.</span><span class="sxs-lookup"><span data-stu-id="276b5-103">Gets the primitive type of this "ICorDebugValue" object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="276b5-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="276b5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetType (  
    [out] CorElementType   *pType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="276b5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="276b5-105">Parameters</span></span>  

 `pType`  
 <span data-ttu-id="276b5-106">dışı Değerin türünü gösteren "CorElementType" sabit listesinin bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="276b5-106">[out] A pointer to a value of the "CorElementType" enumeration that indicates the value's type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="276b5-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="276b5-107">Remarks</span></span>  

 <span data-ttu-id="276b5-108">Nesne karmaşık bir çalışma zamanı türü ise, bu tür arabirimin uygun alt sınıfları aracılığıyla incelenebilir `ICorDebugValue` .</span><span class="sxs-lookup"><span data-stu-id="276b5-108">If the object is a complex run-time type, that type may be examined through the appropriate subclasses of the `ICorDebugValue` interface.</span></span> <span data-ttu-id="276b5-109">Örneğin, öğesinden devralan "ICorDebugObjectValue" `ICorDebugValue` karmaşık bir türü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="276b5-109">For example, "ICorDebugObjectValue", which inherits from `ICorDebugValue`, represents a complex type.</span></span>  
  
 <span data-ttu-id="276b5-110">`GetType`Ve [ICorDebugObjectValue:: GetClass](icordebugobjectvalue-getclass-method.md) metotları her biri bir değerin türü hakkında bilgi döndürür.</span><span class="sxs-lookup"><span data-stu-id="276b5-110">The `GetType` and [ICorDebugObjectValue::GetClass](icordebugobjectvalue-getclass-method.md) methods each return information about the type of a value.</span></span> <span data-ttu-id="276b5-111">Bunlar her ikisi de genel türler tarafından [ICorDebugValue2:: GetExactType](icordebugvalue2-getexacttype-method.md) yöntemi ile değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="276b5-111">They are both superseded by the generics-aware [ICorDebugValue2::GetExactType](icordebugvalue2-getexacttype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="276b5-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="276b5-112">Requirements</span></span>  

 <span data-ttu-id="276b5-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="276b5-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="276b5-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="276b5-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="276b5-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="276b5-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="276b5-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="276b5-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="276b5-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="276b5-117">See also</span></span>
