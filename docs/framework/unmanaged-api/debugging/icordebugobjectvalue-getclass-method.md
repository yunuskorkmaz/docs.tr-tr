---
description: ': ICorDebugObjectValue:: GetClass yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 4ea6a47814777da934aa14bba947a047c075396c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99722223"
---
# <a name="icordebugobjectvaluegetclass-method"></a><span data-ttu-id="35220-103">ICorDebugObjectValue::GetClass Yöntemi</span><span class="sxs-lookup"><span data-stu-id="35220-103">ICorDebugObjectValue::GetClass Method</span></span>

<span data-ttu-id="35220-104">Bu nesne değerinin sınıfını alır.</span><span class="sxs-lookup"><span data-stu-id="35220-104">Gets the class of this object value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35220-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="35220-105">Syntax</span></span>  
  
```cpp  
HRESULT GetClass (  
    [out] ICorDebugClass     **ppClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="35220-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="35220-106">Parameters</span></span>  

 `ppClass`  
 <span data-ttu-id="35220-107">dışı Bu "ICorDebugObjectValue" nesnesi tarafından temsil edilen nesne değerinin sınıfını temsil eden "ICorDebugClass" nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="35220-107">[out] A pointer to the address of an "ICorDebugClass" object that represents the class of the object value represented by this "ICorDebugObjectValue" object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="35220-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="35220-108">Remarks</span></span>  

 <span data-ttu-id="35220-109">`GetClass`Ve [ICorDebugValue:: GetType](icordebugvalue-gettype-method.md) yöntemleri her biri bir değerin türü hakkında bilgi döndürür; bunların her ikisi de genel türler tarafından [ICorDebugValue2:: GetExactType](icordebugvalue2-getexacttype-method.md)tarafından yerine geçiyor.</span><span class="sxs-lookup"><span data-stu-id="35220-109">The `GetClass` and [ICorDebugValue::GetType](icordebugvalue-gettype-method.md) methods each return information about the type of a value; they are both superseded by the generics-aware [ICorDebugValue2::GetExactType](icordebugvalue2-getexacttype-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="35220-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="35220-110">Requirements</span></span>  

 <span data-ttu-id="35220-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="35220-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="35220-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="35220-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="35220-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="35220-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="35220-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="35220-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35220-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="35220-115">See also</span></span>
