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
ms.openlocfilehash: 4dbc042143e68dc962eb21b2bf741cbaefc1977e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122352"
---
# <a name="icordebugtypegetfirsttypeparameter-method"></a><span data-ttu-id="000c4-102">ICorDebugType::GetFirstTypeParameter Yöntemi</span><span class="sxs-lookup"><span data-stu-id="000c4-102">ICorDebugType::GetFirstTypeParameter Method</span></span>
<span data-ttu-id="000c4-103">Bu `ICorDebugType`tarafından temsil edilen türün ilk <xref:System.Type> parametresini temsil eden bir ICorDebugType için bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="000c4-103">Gets an interface pointer to an ICorDebugType that represents the first <xref:System.Type> parameter of the type represented by this `ICorDebugType`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="000c4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="000c4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFirstTypeParameter (  
    [out] ICorDebugType   **value  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="000c4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="000c4-105">Parameters</span></span>  
 `value`  
 <span data-ttu-id="000c4-106">dışı İlk parametreyi temsil eden bir `ICorDebugType` nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="000c4-106">[out] A pointer to the address of an `ICorDebugType` object that represents the first parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="000c4-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="000c4-107">Remarks</span></span>  
 <span data-ttu-id="000c4-108">`GetFirstTypeParameter`, türüyle ilgili ek bilgilerin, en çok bir tür parametresine sahip olduğu durumlarda çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="000c4-108">`GetFirstTypeParameter` can be called in cases where the additional information about the type involves, at most, one type parameter.</span></span> <span data-ttu-id="000c4-109">Özellikle, türü [ICorDebugType:: GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) yönteminde gösterildiği gıbı bir element_type_array, element_type_szarray, ELEMENT_TYPE_BYREF veya ELEMENT_TYPE_PTR ise kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="000c4-109">In particular, it can be used if the type is an ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF, or ELEMENT_TYPE_PTR, as indicated by the [ICorDebugType::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="000c4-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="000c4-110">Requirements</span></span>  
 <span data-ttu-id="000c4-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="000c4-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="000c4-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="000c4-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="000c4-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="000c4-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="000c4-114">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="000c4-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
