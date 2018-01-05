---
title: ICorDebugObjectValue::GetClass Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugObjectValue.GetClass
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugObjectValue::GetClass
helpviewer_keywords:
- ICorDebugObjectValue::GetClass method [.NET Framework debugging]
- GetClass method, ICorDebugObjectValue interface [.NET Framework debugging]
ms.assetid: 5be25292-8357-445f-a09b-f997c0de761c
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6135dd3806d72b59ce858fab9d0a0b6c3b1f11b6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugobjectvaluegetclass-method"></a><span data-ttu-id="a578c-102">ICorDebugObjectValue::GetClass Metodu</span><span class="sxs-lookup"><span data-stu-id="a578c-102">ICorDebugObjectValue::GetClass Method</span></span>
<span data-ttu-id="a578c-103">Bu nesne değeri sınıfını alır.</span><span class="sxs-lookup"><span data-stu-id="a578c-103">Gets the class of this object value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a578c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a578c-104">Syntax</span></span>  
  
```  
HRESULT GetClass (  
    [out] ICorDebugClass     **ppClass  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a578c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a578c-105">Parameters</span></span>  
 `ppClass`  
 <span data-ttu-id="a578c-106">[out] Bir işaretçi adresine "ICorDebugClass" nesnenin bu "ICorDebugObjectValue" nesnesiyle temsil edilen nesne değeri sınıfı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a578c-106">[out] A pointer to the address of an "ICorDebugClass" object that represents the class of the object value represented by this "ICorDebugObjectValue" object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a578c-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a578c-107">Remarks</span></span>  
 <span data-ttu-id="a578c-108">`GetClass` Ve [Icordebugvalue::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md) yöntemlerinin her bir değerin türü hakkında bilgi döndürür; bunların her ikisi de genel türler algılayan tarafından değiştirilen [Icordebugvalue2::getexacttype](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue2-getexacttype-method.md).</span><span class="sxs-lookup"><span data-stu-id="a578c-108">The `GetClass` and [ICorDebugValue::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md) methods each return information about the type of a value; they are both superseded by the generics-aware [ICorDebugValue2::GetExactType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue2-getexacttype-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a578c-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a578c-109">Requirements</span></span>  
 <span data-ttu-id="a578c-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a578c-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a578c-111">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a578c-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a578c-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a578c-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a578c-113">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a578c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a578c-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a578c-114">See Also</span></span>  
    
 
