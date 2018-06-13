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
ms.openlocfilehash: dff7a42cac7002e170e8da3c3505fe37bd5eb85f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33418769"
---
# <a name="icordebugobjectvaluegetclass-method"></a><span data-ttu-id="f0e50-102">ICorDebugObjectValue::GetClass Metodu</span><span class="sxs-lookup"><span data-stu-id="f0e50-102">ICorDebugObjectValue::GetClass Method</span></span>
<span data-ttu-id="f0e50-103">Bu nesne değeri sınıfını alır.</span><span class="sxs-lookup"><span data-stu-id="f0e50-103">Gets the class of this object value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0e50-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f0e50-104">Syntax</span></span>  
  
```  
HRESULT GetClass (  
    [out] ICorDebugClass     **ppClass  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f0e50-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f0e50-105">Parameters</span></span>  
 `ppClass`  
 <span data-ttu-id="f0e50-106">[out] Bir işaretçi adresine "ICorDebugClass" nesnenin bu "ICorDebugObjectValue" nesnesiyle temsil edilen nesne değeri sınıfı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f0e50-106">[out] A pointer to the address of an "ICorDebugClass" object that represents the class of the object value represented by this "ICorDebugObjectValue" object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f0e50-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f0e50-107">Remarks</span></span>  
 <span data-ttu-id="f0e50-108">`GetClass` Ve [Icordebugvalue::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md) yöntemlerinin her bir değerin türü hakkında bilgi döndürür; bunların her ikisi de genel türler algılayan tarafından değiştirilen [Icordebugvalue2::getexacttype](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue2-getexacttype-method.md).</span><span class="sxs-lookup"><span data-stu-id="f0e50-108">The `GetClass` and [ICorDebugValue::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md) methods each return information about the type of a value; they are both superseded by the generics-aware [ICorDebugValue2::GetExactType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue2-getexacttype-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0e50-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f0e50-109">Requirements</span></span>  
 <span data-ttu-id="f0e50-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f0e50-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0e50-111">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f0e50-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f0e50-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f0e50-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f0e50-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f0e50-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0e50-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f0e50-114">See Also</span></span>  
    
 
