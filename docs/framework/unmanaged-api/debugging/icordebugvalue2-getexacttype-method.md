---
title: ICorDebugValue2::GetExactType Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugValue2.GetExactType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue2::GetExactType
helpviewer_keywords:
- ICorDebugValue2::GetExactType method [.NET Framework debugging]
- GetExactType method [.NET Framework debugging]
ms.assetid: 8e9aae1b-d1b7-4b6e-b577-6faf36dcec85
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f1f8292a6964a6b25e228fcd07ab21a7ee5f5a04
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423338"
---
# <a name="icordebugvalue2getexacttype-method"></a><span data-ttu-id="a70da-102">ICorDebugValue2::GetExactType Metodu</span><span class="sxs-lookup"><span data-stu-id="a70da-102">ICorDebugValue2::GetExactType Method</span></span>
<span data-ttu-id="a70da-103">"ICorDebugType" nesneyi temsil eden bir arabirim işaretçisi alır <xref:System.Type> bu değer.</span><span class="sxs-lookup"><span data-stu-id="a70da-103">Gets an interface pointer to an "ICorDebugType" object that represents the <xref:System.Type> of this value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a70da-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a70da-104">Syntax</span></span>  
  
```  
HRESULT GetExactType (  
    [out] ICorDebugType   **ppType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a70da-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a70da-105">Parameters</span></span>  
 `ppType`  
 <span data-ttu-id="a70da-106">[out] Adresine bir işaretçi bir `ICorDebugType` temsil eden nesne <xref:System.Type> bu "ICorDebugValue2" nesnesinin temsil ettiği değer.</span><span class="sxs-lookup"><span data-stu-id="a70da-106">[out] A pointer to the address of an `ICorDebugType` object that represents the <xref:System.Type> of the value represented by this "ICorDebugValue2" object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a70da-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a70da-107">Remarks</span></span>  
 <span data-ttu-id="a70da-108">Genel türler kullanan `GetExactType` yöntemi her ikisi de yerine geçiyor [Icordebugobjectvalue::getclass](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md) ve [Icordebugvalue::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md) yöntemleri, her bir değerin türü hakkındaki dönüş hangi bilgilerin .</span><span class="sxs-lookup"><span data-stu-id="a70da-108">The generics-aware `GetExactType` method supersedes both the [ICorDebugObjectValue::GetClass](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md) and the [ICorDebugValue::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md) methods, each of which return information about the type of a value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a70da-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a70da-109">Requirements</span></span>  
 <span data-ttu-id="a70da-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a70da-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a70da-111">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a70da-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a70da-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a70da-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a70da-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a70da-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a70da-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a70da-114">See Also</span></span>  
 
