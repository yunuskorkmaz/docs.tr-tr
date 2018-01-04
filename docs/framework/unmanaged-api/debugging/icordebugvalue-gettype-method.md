---
title: ICorDebugValue::GetType Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugValue.GetType
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugValue::GetType
helpviewer_keywords:
- ICorDebugValue::GetType method [.NET Framework debugging]
- GetType method, ICorDebugValue interface [.NET Framework debugging]
ms.assetid: 41e2d503-e1f1-407b-abe0-6a29adb3e0d1
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2a79ef332361fdaa3a23cc4e13daa8b4a8303d2c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugvaluegettype-method"></a><span data-ttu-id="dfc11-102">ICorDebugValue::GetType Metodu</span><span class="sxs-lookup"><span data-stu-id="dfc11-102">ICorDebugValue::GetType Method</span></span>
<span data-ttu-id="dfc11-103">Bu "ICorDebugValue" nesne temel türünü alır.</span><span class="sxs-lookup"><span data-stu-id="dfc11-103">Gets the primitive type of this "ICorDebugValue" object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dfc11-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dfc11-104">Syntax</span></span>  
  
```  
HRESULT GetType (  
    [out] CorElementType   *pType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dfc11-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="dfc11-105">Parameters</span></span>  
 `pType`  
 <span data-ttu-id="dfc11-106">[out] Değerin türünü gösteren "CorElementType" numaralandırma değerini gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="dfc11-106">[out] A pointer to a value of the "CorElementType" enumeration that indicates the value's type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dfc11-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dfc11-107">Remarks</span></span>  
 <span data-ttu-id="dfc11-108">Nesne karmaşık bir çalışma zamanı tür ise, bu tür uygun sınıfları incelenmesi `ICorDebugValue` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="dfc11-108">If the object is a complex run-time type, that type may be examined through the appropriate subclasses of the `ICorDebugValue` interface.</span></span> <span data-ttu-id="dfc11-109">"Hangi devraldığı Örneğin, Icordebugobjectvalue", `ICorDebugValue`, karmaşık bir türü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="dfc11-109">For example, "ICorDebugObjectValue", which inherits from `ICorDebugValue`, represents a complex type.</span></span>  
  
 <span data-ttu-id="dfc11-110">`GetType` Ve [Icordebugobjectvalue::getclass](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md) yöntemlerinin her bir değerin türü hakkında bilgi döndürür.</span><span class="sxs-lookup"><span data-stu-id="dfc11-110">The `GetType` and [ICorDebugObjectValue::GetClass](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md) methods each return information about the type of a value.</span></span> <span data-ttu-id="dfc11-111">Bunların her ikisi de genel türler algılayan tarafından değiştirilen [Icordebugvalue2::getexacttype](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue2-getexacttype-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="dfc11-111">They are both superseded by the generics-aware [ICorDebugValue2::GetExactType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue2-getexacttype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dfc11-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dfc11-112">Requirements</span></span>  
 <span data-ttu-id="dfc11-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dfc11-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dfc11-114">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dfc11-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dfc11-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dfc11-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dfc11-116">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dfc11-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dfc11-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="dfc11-117">See Also</span></span>  
 
