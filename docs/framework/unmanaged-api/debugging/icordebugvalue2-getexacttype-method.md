---
description: 'Daha fazla bilgi edinin: ICorDebugValue2:: GetExactType yöntemi'
title: ICorDebugValue2::GetExactType Yöntemi
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
ms.openlocfilehash: d0ef08b119106ced89ec2094b5bf67d0c874b6bc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99690316"
---
# <a name="icordebugvalue2getexacttype-method"></a><span data-ttu-id="cdc86-103">ICorDebugValue2::GetExactType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cdc86-103">ICorDebugValue2::GetExactType Method</span></span>

<span data-ttu-id="cdc86-104">Bu değerin değerini temsil eden bir "ICorDebugType" nesnesine bir arabirim işaretçisi alır <xref:System.Type> .</span><span class="sxs-lookup"><span data-stu-id="cdc86-104">Gets an interface pointer to an "ICorDebugType" object that represents the <xref:System.Type> of this value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cdc86-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cdc86-105">Syntax</span></span>  
  
```cpp  
HRESULT GetExactType (  
    [out] ICorDebugType   **ppType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cdc86-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cdc86-106">Parameters</span></span>  

 `ppType`  
 <span data-ttu-id="cdc86-107">dışı `ICorDebugType` <xref:System.Type> Bu "ICorDebugValue2" nesnesinin temsil ettiği değeri temsil eden nesnenin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="cdc86-107">[out] A pointer to the address of an `ICorDebugType` object that represents the <xref:System.Type> of the value represented by this "ICorDebugValue2" object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cdc86-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cdc86-108">Remarks</span></span>  

 <span data-ttu-id="cdc86-109">Genel türler kullanan `GetExactType` Yöntem hem [ICorDebugObjectValue:: GetClass](icordebugobjectvalue-getclass-method.md) hem de [ICorDebugValue:: GetType](icordebugvalue-gettype-method.md) yöntemlerinin yerine, her biri bir değer türü ile ilgili bilgileri döndürür.</span><span class="sxs-lookup"><span data-stu-id="cdc86-109">The generics-aware `GetExactType` method supersedes both the [ICorDebugObjectValue::GetClass](icordebugobjectvalue-getclass-method.md) and the [ICorDebugValue::GetType](icordebugvalue-gettype-method.md) methods, each of which return information about the type of a value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cdc86-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cdc86-110">Requirements</span></span>  

 <span data-ttu-id="cdc86-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cdc86-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cdc86-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="cdc86-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cdc86-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="cdc86-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cdc86-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cdc86-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cdc86-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cdc86-115">See also</span></span>
