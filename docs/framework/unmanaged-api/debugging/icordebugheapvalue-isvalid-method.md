---
title: ICorDebugHeapValue::IsValid Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue.IsValid
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue::IsValid
helpviewer_keywords:
- IsValid method [.NET Framework debugging]
- ICorDebugHeapValue::IsValid method [.NET Framework debugging]
ms.assetid: 68e20e62-203d-46d8-bb91-8d3c61cfacc3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 95532d6721467b482b1d79d611f8055b606bb4a5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33413514"
---
# <a name="icordebugheapvalueisvalid-method"></a><span data-ttu-id="b03e2-102">ICorDebugHeapValue::IsValid Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b03e2-102">ICorDebugHeapValue::IsValid Method</span></span>
<span data-ttu-id="b03e2-103">Bu Icordebugheapvalue tarafından temsil edilen nesne geçerli olup olmadığını belirten bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="b03e2-103">Gets a value that indicates whether the object represented by this ICorDebugHeapValue is valid.</span></span>  
  
 <span data-ttu-id="b03e2-104">Bu yöntem .NET Framework sürüm 2.0 kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="b03e2-104">This method has been deprecated in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b03e2-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b03e2-105">Syntax</span></span>  
  
```  
HRESULT IsValid (  
    [out] BOOL    *pbValid  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b03e2-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b03e2-106">Parameters</span></span>  
 `pbValid`  
 <span data-ttu-id="b03e2-107">[out] Yığında bu değerin geçerli olup olmadığını gösteren bir Boole değeri için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b03e2-107">[out] A pointer to a Boolean value that indicates whether this value on the heap is valid.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b03e2-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b03e2-108">Remarks</span></span>  
 <span data-ttu-id="b03e2-109">Çöp toplayıcı tarafından iadesi varsa değeri geçersiz.</span><span class="sxs-lookup"><span data-stu-id="b03e2-109">The value is invalid if it has been reclaimed by the garbage collector.</span></span>  
  
 <span data-ttu-id="b03e2-110">Bu yöntem kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="b03e2-110">This method has been deprecated.</span></span> <span data-ttu-id="b03e2-111">.NET Framework 2.0 tüm değerleri kadar geçerli [Icordebugcontroller::continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) , hangi saat değerleri geçersiz kılınan sırasında çağrılır.</span><span class="sxs-lookup"><span data-stu-id="b03e2-111">In the .NET Framework 2.0, all values are valid until [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) is called, at which time the values are invalidated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b03e2-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b03e2-112">Requirements</span></span>  
 <span data-ttu-id="b03e2-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b03e2-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b03e2-114">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b03e2-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b03e2-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b03e2-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b03e2-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b03e2-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
