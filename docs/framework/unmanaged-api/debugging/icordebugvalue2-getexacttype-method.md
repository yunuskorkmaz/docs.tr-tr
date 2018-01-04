---
title: ICorDebugValue2::GetExactType Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugValue2.GetExactType
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugValue2::GetExactType
helpviewer_keywords:
- ICorDebugValue2::GetExactType method [.NET Framework debugging]
- GetExactType method [.NET Framework debugging]
ms.assetid: 8e9aae1b-d1b7-4b6e-b577-6faf36dcec85
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ad7d0e2ddcd8b66fd87cffa23204ae3b859f368c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugvalue2getexacttype-method"></a><span data-ttu-id="56f4e-102">ICorDebugValue2::GetExactType Metodu</span><span class="sxs-lookup"><span data-stu-id="56f4e-102">ICorDebugValue2::GetExactType Method</span></span>
<span data-ttu-id="56f4e-103">"ICorDebugType" nesneyi temsil eden bir arabirim işaretçisi alır <xref:System.Type> bu değer.</span><span class="sxs-lookup"><span data-stu-id="56f4e-103">Gets an interface pointer to an "ICorDebugType" object that represents the <xref:System.Type> of this value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56f4e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="56f4e-104">Syntax</span></span>  
  
```  
HRESULT GetExactType (  
    [out] ICorDebugType   **ppType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="56f4e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="56f4e-105">Parameters</span></span>  
 `ppType`  
 <span data-ttu-id="56f4e-106">[out] Adresine bir işaretçi bir `ICorDebugType` temsil eden nesne <xref:System.Type> bu "ICorDebugValue2" nesnesinin temsil ettiği değer.</span><span class="sxs-lookup"><span data-stu-id="56f4e-106">[out] A pointer to the address of an `ICorDebugType` object that represents the <xref:System.Type> of the value represented by this "ICorDebugValue2" object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="56f4e-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="56f4e-107">Remarks</span></span>  
 <span data-ttu-id="56f4e-108">Genel türler kullanan `GetExactType` yöntemi her ikisi de yerine geçiyor [Icordebugobjectvalue::getclass](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md) ve [Icordebugvalue::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md) yöntemleri, her bir değerin türü hakkındaki dönüş hangi bilgilerin .</span><span class="sxs-lookup"><span data-stu-id="56f4e-108">The generics-aware `GetExactType` method supersedes both the [ICorDebugObjectValue::GetClass](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md) and the [ICorDebugValue::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md) methods, each of which return information about the type of a value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56f4e-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="56f4e-109">Requirements</span></span>  
 <span data-ttu-id="56f4e-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="56f4e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="56f4e-111">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="56f4e-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="56f4e-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="56f4e-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="56f4e-113">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="56f4e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56f4e-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="56f4e-114">See Also</span></span>  
 
