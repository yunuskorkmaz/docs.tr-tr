---
title: ICorDebugType::GetFirstTypeParameter Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetFirstTypeParameter
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetFirstTypeParameter
helpviewer_keywords:
- ICorDebugType::GetFirstTypeParameter method [.NET Framework debugging]
- GetFirstTypeParameter method [.NET Framework debugging]
ms.assetid: 35bb594f-af6a-4349-83fe-e98702674e03
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4d872e4a65c0556dddac468336e6a42dd7d7923c
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57477655"
---
# <a name="icordebugtypegetfirsttypeparameter-method"></a><span data-ttu-id="a70a7-102">ICorDebugType::GetFirstTypeParameter Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a70a7-102">ICorDebugType::GetFirstTypeParameter Method</span></span>
<span data-ttu-id="a70a7-103">İlk temsil eden bir Icordebugtype bir arabirim işaretçisi alır <xref:System.Type> bu tarafından temsil edilen bir türün parametresinin `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="a70a7-103">Gets an interface pointer to an ICorDebugType that represents the first <xref:System.Type> parameter of the type represented by this `ICorDebugType`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a70a7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a70a7-104">Syntax</span></span>  
  
```  
HRESULT GetFirstTypeParameter (  
    [out] ICorDebugType   **value  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a70a7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a70a7-105">Parameters</span></span>  
 `value`  
 <span data-ttu-id="a70a7-106">[out] Adresine bir işaretçi bir `ICorDebugType` ilk parametre temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="a70a7-106">[out] A pointer to the address of an `ICorDebugType` object that represents the first parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a70a7-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a70a7-107">Remarks</span></span>  
 <span data-ttu-id="a70a7-108">`GetFirstTypeParameter` Burada türü hakkında ek bilgiler, en fazla içerir durumda bir tür parametresi çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="a70a7-108">`GetFirstTypeParameter` can be called in cases where the additional information about the type involves, at most, one type parameter.</span></span> <span data-ttu-id="a70a7-109">Tür ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF veya ELEMENT_TYPE_PTR, ise özellikle tarafından belirtildiği şekilde kullanılabilmesi için [Icordebugtype::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="a70a7-109">In particular, it can be used if the type is an ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF, or ELEMENT_TYPE_PTR, as indicated by the [ICorDebugType::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a70a7-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a70a7-110">Requirements</span></span>  
 <span data-ttu-id="a70a7-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a70a7-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a70a7-112">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a70a7-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a70a7-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a70a7-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a70a7-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a70a7-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
