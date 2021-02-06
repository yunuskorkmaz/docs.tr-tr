---
description: 'Şu konuda daha fazla bilgi edinin: ICorDebugHeapValue:: IsValid yöntemi'
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
ms.openlocfilehash: 27eca844170b31934cd32dad5cf5fccc0b0e324e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99660797"
---
# <a name="icordebugheapvalueisvalid-method"></a><span data-ttu-id="e483d-103">ICorDebugHeapValue::IsValid Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e483d-103">ICorDebugHeapValue::IsValid Method</span></span>

<span data-ttu-id="e483d-104">Bu ICorDebugHeapValue tarafından temsil edilen nesnenin geçerli olup olmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="e483d-104">Gets a value that indicates whether the object represented by this ICorDebugHeapValue is valid.</span></span>  
  
 <span data-ttu-id="e483d-105">Bu yöntem 2,0 .NET Framework sürümünde kullanımdan kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="e483d-105">This method has been deprecated in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e483d-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e483d-106">Syntax</span></span>  
  
```cpp  
HRESULT IsValid (  
    [out] BOOL    *pbValid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e483d-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e483d-107">Parameters</span></span>  

 `pbValid`  
 <span data-ttu-id="e483d-108">dışı Yığın üzerinde bu değerin geçerli olup olmadığını belirten bir Boolean değer işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="e483d-108">[out] A pointer to a Boolean value that indicates whether this value on the heap is valid.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e483d-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e483d-109">Remarks</span></span>  

 <span data-ttu-id="e483d-110">Değer çöp toplayıcı tarafından geri kazanımışsa geçersizdir.</span><span class="sxs-lookup"><span data-stu-id="e483d-110">The value is invalid if it has been reclaimed by the garbage collector.</span></span>  
  
 <span data-ttu-id="e483d-111">Bu yöntem kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="e483d-111">This method has been deprecated.</span></span> <span data-ttu-id="e483d-112">.NET Framework 2,0 ' de, tüm değerler [ICorDebugController:: Continue](icordebugcontroller-continue-method.md) çağrılana kadar geçerli olur, bu durumda değerler geçersiz kılınır.</span><span class="sxs-lookup"><span data-stu-id="e483d-112">In the .NET Framework 2.0, all values are valid until [ICorDebugController::Continue](icordebugcontroller-continue-method.md) is called, at which time the values are invalidated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e483d-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e483d-113">Requirements</span></span>  

 <span data-ttu-id="e483d-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e483d-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e483d-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e483d-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e483d-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e483d-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e483d-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e483d-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
