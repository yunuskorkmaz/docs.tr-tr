---
title: ICorDebugObjectValue::GetClass Metodu
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0d403fe24f368a5cd05358cd589023a4c8710a37
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54587430"
---
# <a name="icordebugobjectvaluegetclass-method"></a><span data-ttu-id="7ccfb-102">ICorDebugObjectValue::GetClass Metodu</span><span class="sxs-lookup"><span data-stu-id="7ccfb-102">ICorDebugObjectValue::GetClass Method</span></span>
<span data-ttu-id="7ccfb-103">Bu nesne değeri sınıfı alır.</span><span class="sxs-lookup"><span data-stu-id="7ccfb-103">Gets the class of this object value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ccfb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7ccfb-104">Syntax</span></span>  
  
```  
HRESULT GetClass (  
    [out] ICorDebugClass     **ppClass  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7ccfb-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7ccfb-105">Parameters</span></span>  
 `ppClass`  
 <span data-ttu-id="7ccfb-106">[out] Bu "ICorDebugObjectValue" nesnesiyle temsil edilen nesne değeri sınıfını temsil eden bir "ICorDebugClass" nesnenin adresi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7ccfb-106">[out] A pointer to the address of an "ICorDebugClass" object that represents the class of the object value represented by this "ICorDebugObjectValue" object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7ccfb-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7ccfb-107">Remarks</span></span>  
 <span data-ttu-id="7ccfb-108">`GetClass` Ve [Icordebugvalue::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md) yöntemlerinin her bir değer türü hakkında bilgi döndürür; bunların her ikisi de genel türleri tanımayan tarafından değiştirilen [Icordebugvalue2::getexacttype](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue2-getexacttype-method.md).</span><span class="sxs-lookup"><span data-stu-id="7ccfb-108">The `GetClass` and [ICorDebugValue::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md) methods each return information about the type of a value; they are both superseded by the generics-aware [ICorDebugValue2::GetExactType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue2-getexacttype-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7ccfb-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7ccfb-109">Requirements</span></span>  
 <span data-ttu-id="7ccfb-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7ccfb-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7ccfb-111">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7ccfb-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7ccfb-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7ccfb-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7ccfb-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7ccfb-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ccfb-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7ccfb-114">See also</span></span>


