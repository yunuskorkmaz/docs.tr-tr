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
ms.openlocfilehash: 878a57514af34730049864f17f4853c1237904c2
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379968"
---
# <a name="icordebugtypegetclass-method"></a><span data-ttu-id="f908b-102">ICorDebugType::GetClass Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f908b-102">ICorDebugType::GetClass Method</span></span>
<span data-ttu-id="f908b-103">Örneklenmiş genel türü temsil eden bir ICorDebugClass için bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="f908b-103">Gets an interface pointer to an ICorDebugClass that represents the uninstantiated generic type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f908b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f908b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetClass (  
    [out] ICorDebugClass   **ppClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f908b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f908b-105">Parameters</span></span>  
 `ppClass`  
 <span data-ttu-id="f908b-106">dışı `ICorDebugClass`Örneklenmiş genel türü temsil eden bir arabirimin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f908b-106">[out] A pointer to the address of an `ICorDebugClass` interface that represents the uninstantiated generic type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f908b-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f908b-107">Remarks</span></span>  
 <span data-ttu-id="f908b-108">`GetClass`yalnızca belirli koşullar altında çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="f908b-108">`GetClass` can be called only under certain conditions.</span></span> <span data-ttu-id="f908b-109">Çağrılmadan önce [ICorDebugType:: GetType](icordebugtype-gettype-method.md) çağırın `GetClass` .</span><span class="sxs-lookup"><span data-stu-id="f908b-109">Call [ICorDebugType::GetType](icordebugtype-gettype-method.md) before calling `GetClass`.</span></span> <span data-ttu-id="f908b-110">`ICorDebugType::GetType`Element_type_class veya element_type_valuetype bir CorElementType değeri döndürürse, `GetClass` genel bir türün örneklenmemiş türünü almak için çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="f908b-110">If `ICorDebugType::GetType` returns a CorElementType value that is ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE, `GetClass` can be called to get the uninstantiated type for a generic type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f908b-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f908b-111">Requirements</span></span>  
 <span data-ttu-id="f908b-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f908b-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f908b-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f908b-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f908b-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="f908b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f908b-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f908b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
