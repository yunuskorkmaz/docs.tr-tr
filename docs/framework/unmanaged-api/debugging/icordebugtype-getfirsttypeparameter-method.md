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
ms.openlocfilehash: be69636056d5510b72dbce39917f5e8d3b05cd87
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723980"
---
# <a name="icordebugtypegetfirsttypeparameter-method"></a><span data-ttu-id="be46e-102">ICorDebugType::GetFirstTypeParameter Yöntemi</span><span class="sxs-lookup"><span data-stu-id="be46e-102">ICorDebugType::GetFirstTypeParameter Method</span></span>

<span data-ttu-id="be46e-103"><xref:System.Type>Bu tarafından temsil edilen türün ilk parametresini temsil eden bir ICorDebugType için bir arabirim işaretçisi alır `ICorDebugType` .</span><span class="sxs-lookup"><span data-stu-id="be46e-103">Gets an interface pointer to an ICorDebugType that represents the first <xref:System.Type> parameter of the type represented by this `ICorDebugType`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be46e-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="be46e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFirstTypeParameter (  
    [out] ICorDebugType   **value  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="be46e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="be46e-105">Parameters</span></span>  

 `value`  
 <span data-ttu-id="be46e-106">dışı `ICorDebugType` İlk parametreyi temsil eden bir nesnenin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="be46e-106">[out] A pointer to the address of an `ICorDebugType` object that represents the first parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="be46e-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="be46e-107">Remarks</span></span>  

 <span data-ttu-id="be46e-108">`GetFirstTypeParameter` , türle ilgili ek bilgilerin en çok, tek bir tür parametresine sahip olduğu durumlarda çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="be46e-108">`GetFirstTypeParameter` can be called in cases where the additional information about the type involves, at most, one type parameter.</span></span> <span data-ttu-id="be46e-109">Özellikle, türü [ICorDebugType:: GetType](icordebugtype-gettype-method.md) yöntemiyle gösterildiği gibi bir ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF veya ELEMENT_TYPE_PTR ise kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="be46e-109">In particular, it can be used if the type is an ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF, or ELEMENT_TYPE_PTR, as indicated by the [ICorDebugType::GetType](icordebugtype-gettype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be46e-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="be46e-110">Requirements</span></span>  

 <span data-ttu-id="be46e-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="be46e-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be46e-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="be46e-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="be46e-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="be46e-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="be46e-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be46e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
