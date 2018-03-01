---
title: ICorDebugType::GetFirstTypeParameter Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e963553bfeac2d659de8fc460a938d2d523b53e0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugtypegetfirsttypeparameter-method"></a><span data-ttu-id="384ad-102">ICorDebugType::GetFirstTypeParameter Metodu</span><span class="sxs-lookup"><span data-stu-id="384ad-102">ICorDebugType::GetFirstTypeParameter Method</span></span>
<span data-ttu-id="384ad-103">Arabirim işaretçisi ilk temsil eden bir Icordebugtype alır <xref:System.Type> bu tarafından temsil edilen türünde parametresi `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="384ad-103">Gets an interface pointer to an ICorDebugType that represents the first <xref:System.Type> parameter of the type represented by this `ICorDebugType`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="384ad-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="384ad-104">Syntax</span></span>  
  
```  
HRESULT GetFirstTypeParameter (  
    [out] ICorDebugType   **value  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="384ad-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="384ad-105">Parameters</span></span>  
 `value`  
 <span data-ttu-id="384ad-106">[out] Adresine bir işaretçi bir `ICorDebugType` ilk parametre temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="384ad-106">[out] A pointer to the address of an `ICorDebugType` object that represents the first parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="384ad-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="384ad-107">Remarks</span></span>  
 <span data-ttu-id="384ad-108">`GetFirstTypeParameter`Burada türüyle ilgili ek bilgileri, en fazla içerir durumda bir tür parametresi çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="384ad-108">`GetFirstTypeParameter` can be called in cases where the additional information about the type involves, at most, one type parameter.</span></span> <span data-ttu-id="384ad-109">Tür bir ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF veya ELEMENT_TYPE_PTR, ise özel olarak, belirtilen şekilde kullanılabilmesi için [Icordebugtype::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="384ad-109">In particular, it can be used if the type is an ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF, or ELEMENT_TYPE_PTR, as indicated by the [ICorDebugType::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="384ad-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="384ad-110">Requirements</span></span>  
 <span data-ttu-id="384ad-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="384ad-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="384ad-112">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="384ad-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="384ad-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="384ad-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="384ad-114">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="384ad-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
