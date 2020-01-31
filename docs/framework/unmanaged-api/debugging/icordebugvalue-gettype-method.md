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
ms.openlocfilehash: 7def2bd2c0f3ab501fdb918a0e9a7ee154159b78
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791150"
---
# <a name="icordebugvaluegettype-method"></a><span data-ttu-id="41db9-102">ICorDebugValue::GetType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="41db9-102">ICorDebugValue::GetType Method</span></span>
<span data-ttu-id="41db9-103">Bu "ICorDebugValue" nesnesinin temel türünü alır.</span><span class="sxs-lookup"><span data-stu-id="41db9-103">Gets the primitive type of this "ICorDebugValue" object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41db9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="41db9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetType (  
    [out] CorElementType   *pType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="41db9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="41db9-105">Parameters</span></span>  
 `pType`  
 <span data-ttu-id="41db9-106">dışı Değerin türünü gösteren "CorElementType" sabit listesinin bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="41db9-106">[out] A pointer to a value of the "CorElementType" enumeration that indicates the value's type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="41db9-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="41db9-107">Remarks</span></span>  
 <span data-ttu-id="41db9-108">Nesne karmaşık bir çalışma zamanı türü ise, bu tür `ICorDebugValue` arabiriminin uygun alt sınıfları aracılığıyla incelenebilir.</span><span class="sxs-lookup"><span data-stu-id="41db9-108">If the object is a complex run-time type, that type may be examined through the appropriate subclasses of the `ICorDebugValue` interface.</span></span> <span data-ttu-id="41db9-109">Örneğin, `ICorDebugValue`devralan "ICorDebugObjectValue" karmaşık bir türü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="41db9-109">For example, "ICorDebugObjectValue", which inherits from `ICorDebugValue`, represents a complex type.</span></span>  
  
 <span data-ttu-id="41db9-110">`GetType` ve [ICorDebugObjectValue:: GetClass](icordebugobjectvalue-getclass-method.md) metotları her biri bir değerin türü hakkında bilgi döndürür.</span><span class="sxs-lookup"><span data-stu-id="41db9-110">The `GetType` and [ICorDebugObjectValue::GetClass](icordebugobjectvalue-getclass-method.md) methods each return information about the type of a value.</span></span> <span data-ttu-id="41db9-111">Bunlar her ikisi de genel türler tarafından [ICorDebugValue2:: GetExactType](icordebugvalue2-getexacttype-method.md) yöntemi ile değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="41db9-111">They are both superseded by the generics-aware [ICorDebugValue2::GetExactType](icordebugvalue2-getexacttype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41db9-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="41db9-112">Requirements</span></span>  
 <span data-ttu-id="41db9-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="41db9-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41db9-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="41db9-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="41db9-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="41db9-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="41db9-116">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41db9-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41db9-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="41db9-117">See also</span></span>
