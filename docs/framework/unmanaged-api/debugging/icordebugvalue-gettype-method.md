---
title: ICorDebugValue::GetType Metodu
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b4d2ba850ffc6e49cf330174dda9524c7bac4549
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54709201"
---
# <a name="icordebugvaluegettype-method"></a><span data-ttu-id="fa9c3-102">ICorDebugValue::GetType Metodu</span><span class="sxs-lookup"><span data-stu-id="fa9c3-102">ICorDebugValue::GetType Method</span></span>
<span data-ttu-id="fa9c3-103">Bu "ICorDebugValue" nesnenin temel türünü alır.</span><span class="sxs-lookup"><span data-stu-id="fa9c3-103">Gets the primitive type of this "ICorDebugValue" object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa9c3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fa9c3-104">Syntax</span></span>  
  
```  
HRESULT GetType (  
    [out] CorElementType   *pType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fa9c3-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fa9c3-105">Parameters</span></span>  
 `pType`  
 <span data-ttu-id="fa9c3-106">[out] "CorElementType" numaralandırma değerinin türü belirten bir değer için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="fa9c3-106">[out] A pointer to a value of the "CorElementType" enumeration that indicates the value's type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fa9c3-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fa9c3-107">Remarks</span></span>  
 <span data-ttu-id="fa9c3-108">Uygun adornerset'in alt nesne karmaşık bir çalışma zamanı tür ise, bu tür incelenmesi `ICorDebugValue` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="fa9c3-108">If the object is a complex run-time type, that type may be examined through the appropriate subclasses of the `ICorDebugValue` interface.</span></span> <span data-ttu-id="fa9c3-109">"Öğesinden devralan gibi Icordebugobjectvalue", `ICorDebugValue`, karmaşık bir türü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="fa9c3-109">For example, "ICorDebugObjectValue", which inherits from `ICorDebugValue`, represents a complex type.</span></span>  
  
 <span data-ttu-id="fa9c3-110">`GetType` Ve [Icordebugobjectvalue::getclass](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md) yöntemlerinin her bir değer türü hakkında bilgi döndürür.</span><span class="sxs-lookup"><span data-stu-id="fa9c3-110">The `GetType` and [ICorDebugObjectValue::GetClass](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md) methods each return information about the type of a value.</span></span> <span data-ttu-id="fa9c3-111">Bunların her ikisi de genel türleri tanımayan tarafından değiştirilen [Icordebugvalue2::getexacttype](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue2-getexacttype-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="fa9c3-111">They are both superseded by the generics-aware [ICorDebugValue2::GetExactType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue2-getexacttype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fa9c3-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fa9c3-112">Requirements</span></span>  
 <span data-ttu-id="fa9c3-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fa9c3-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fa9c3-114">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fa9c3-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fa9c3-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fa9c3-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fa9c3-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fa9c3-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa9c3-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fa9c3-117">See also</span></span>

