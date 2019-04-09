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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 06e9c7af1c4a769bfb45a8e9f805d97b3bad94aa
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59174193"
---
# <a name="icordebugobjectvaluegetclass-method"></a><span data-ttu-id="044e4-102">ICorDebugObjectValue::GetClass Yöntemi</span><span class="sxs-lookup"><span data-stu-id="044e4-102">ICorDebugObjectValue::GetClass Method</span></span>
<span data-ttu-id="044e4-103">Bu nesne değeri sınıfı alır.</span><span class="sxs-lookup"><span data-stu-id="044e4-103">Gets the class of this object value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="044e4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="044e4-104">Syntax</span></span>  
  
```  
HRESULT GetClass (  
    [out] ICorDebugClass     **ppClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="044e4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="044e4-105">Parameters</span></span>  
 `ppClass`  
 <span data-ttu-id="044e4-106">[out] Bu "ICorDebugObjectValue" nesnesiyle temsil edilen nesne değeri sınıfını temsil eden bir "ICorDebugClass" nesnenin adresi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="044e4-106">[out] A pointer to the address of an "ICorDebugClass" object that represents the class of the object value represented by this "ICorDebugObjectValue" object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="044e4-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="044e4-107">Remarks</span></span>  
 <span data-ttu-id="044e4-108">`GetClass` Ve [Icordebugvalue::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md) yöntemlerinin her bir değer türü hakkında bilgi döndürür; bunların her ikisi de genel türleri tanımayan tarafından değiştirilen [Icordebugvalue2::getexacttype](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue2-getexacttype-method.md).</span><span class="sxs-lookup"><span data-stu-id="044e4-108">The `GetClass` and [ICorDebugValue::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md) methods each return information about the type of a value; they are both superseded by the generics-aware [ICorDebugValue2::GetExactType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue2-getexacttype-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="044e4-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="044e4-109">Requirements</span></span>  
 <span data-ttu-id="044e4-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="044e4-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="044e4-111">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="044e4-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="044e4-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="044e4-112">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="044e4-113">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="044e4-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="044e4-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="044e4-114">See also</span></span>
