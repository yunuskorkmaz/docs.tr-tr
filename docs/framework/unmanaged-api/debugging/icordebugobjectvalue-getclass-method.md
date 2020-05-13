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
ms.openlocfilehash: b0e8fd162ccc1cfc944fb870f493febfe2e5ef42
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83207679"
---
# <a name="icordebugobjectvaluegetclass-method"></a><span data-ttu-id="f3862-102">ICorDebugObjectValue::GetClass Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f3862-102">ICorDebugObjectValue::GetClass Method</span></span>
<span data-ttu-id="f3862-103">Bu nesne değerinin sınıfını alır.</span><span class="sxs-lookup"><span data-stu-id="f3862-103">Gets the class of this object value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3862-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f3862-104">Syntax</span></span>  
  
```cpp  
HRESULT GetClass (  
    [out] ICorDebugClass     **ppClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f3862-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f3862-105">Parameters</span></span>  
 `ppClass`  
 <span data-ttu-id="f3862-106">dışı Bu "ICorDebugObjectValue" nesnesi tarafından temsil edilen nesne değerinin sınıfını temsil eden "ICorDebugClass" nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f3862-106">[out] A pointer to the address of an "ICorDebugClass" object that represents the class of the object value represented by this "ICorDebugObjectValue" object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f3862-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f3862-107">Remarks</span></span>  
 <span data-ttu-id="f3862-108">`GetClass`Ve [ICorDebugValue:: GetType](icordebugvalue-gettype-method.md) yöntemleri her biri bir değerin türü hakkında bilgi döndürür; bunların her ikisi de genel türler tarafından [ICorDebugValue2:: GetExactType](icordebugvalue2-getexacttype-method.md)tarafından yerine geçiyor.</span><span class="sxs-lookup"><span data-stu-id="f3862-108">The `GetClass` and [ICorDebugValue::GetType](icordebugvalue-gettype-method.md) methods each return information about the type of a value; they are both superseded by the generics-aware [ICorDebugValue2::GetExactType](icordebugvalue2-getexacttype-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3862-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f3862-109">Requirements</span></span>  
 <span data-ttu-id="f3862-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f3862-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3862-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f3862-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f3862-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="f3862-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f3862-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f3862-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3862-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f3862-114">See also</span></span>
