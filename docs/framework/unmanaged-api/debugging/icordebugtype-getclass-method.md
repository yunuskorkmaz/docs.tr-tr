---
title: ICorDebugType::GetClass Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetClass
helpviewer_keywords:
- ICorDebugType::GetClass method [.NET Framework debugging]
- GetClass method, ICorDebugType interface [.NET Framework debugging]
ms.assetid: 2644f48b-db3c-429f-ae62-76f1c98a1af5
topic_type:
- apiref
ms.openlocfilehash: 1cb9729f175a2e82e88386b0694467c6fe05636a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95684466"
---
# <a name="icordebugtypegetclass-method"></a><span data-ttu-id="ed312-102">ICorDebugType::GetClass Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ed312-102">ICorDebugType::GetClass Method</span></span>

<span data-ttu-id="ed312-103">Örneklenmiş genel türü temsil eden bir ICorDebugClass için bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="ed312-103">Gets an interface pointer to an ICorDebugClass that represents the uninstantiated generic type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed312-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="ed312-104">Syntax</span></span>  
  
```cpp  
HRESULT GetClass (  
    [out] ICorDebugClass   **ppClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ed312-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ed312-105">Parameters</span></span>  

 `ppClass`  
 <span data-ttu-id="ed312-106">dışı `ICorDebugClass` Örneklenmiş genel türü temsil eden bir arabirimin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ed312-106">[out] A pointer to the address of an `ICorDebugClass` interface that represents the uninstantiated generic type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ed312-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ed312-107">Remarks</span></span>  

 <span data-ttu-id="ed312-108">`GetClass` yalnızca belirli koşullar altında çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="ed312-108">`GetClass` can be called only under certain conditions.</span></span> <span data-ttu-id="ed312-109">Çağrılmadan önce [ICorDebugType:: GetType](icordebugtype-gettype-method.md) çağırın `GetClass` .</span><span class="sxs-lookup"><span data-stu-id="ed312-109">Call [ICorDebugType::GetType](icordebugtype-gettype-method.md) before calling `GetClass`.</span></span> <span data-ttu-id="ed312-110">`ICorDebugType::GetType`Element_type_class veya element_type_valuetype bir CorElementType değeri döndürürse, `GetClass` genel bir türün örneklenmemiş türünü almak için çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="ed312-110">If `ICorDebugType::GetType` returns a CorElementType value that is ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE, `GetClass` can be called to get the uninstantiated type for a generic type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ed312-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ed312-111">Requirements</span></span>  

 <span data-ttu-id="ed312-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ed312-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ed312-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ed312-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ed312-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="ed312-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ed312-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ed312-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
