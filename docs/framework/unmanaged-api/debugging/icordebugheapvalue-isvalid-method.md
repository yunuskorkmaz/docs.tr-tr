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
ms.openlocfilehash: d9150d15ac183b65b87448424f265693ed7b7ab7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726586"
---
# <a name="icordebugheapvalueisvalid-method"></a><span data-ttu-id="e3e35-102">ICorDebugHeapValue::IsValid Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e3e35-102">ICorDebugHeapValue::IsValid Method</span></span>

<span data-ttu-id="e3e35-103">Bu ICorDebugHeapValue tarafından temsil edilen nesnenin geçerli olup olmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="e3e35-103">Gets a value that indicates whether the object represented by this ICorDebugHeapValue is valid.</span></span>  
  
 <span data-ttu-id="e3e35-104">Bu yöntem 2,0 .NET Framework sürümünde kullanımdan kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="e3e35-104">This method has been deprecated in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3e35-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="e3e35-105">Syntax</span></span>  
  
```cpp  
HRESULT IsValid (  
    [out] BOOL    *pbValid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e3e35-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e3e35-106">Parameters</span></span>  

 `pbValid`  
 <span data-ttu-id="e3e35-107">dışı Yığın üzerinde bu değerin geçerli olup olmadığını belirten bir Boolean değer işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="e3e35-107">[out] A pointer to a Boolean value that indicates whether this value on the heap is valid.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e3e35-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e3e35-108">Remarks</span></span>  

 <span data-ttu-id="e3e35-109">Değer çöp toplayıcı tarafından geri kazanımışsa geçersizdir.</span><span class="sxs-lookup"><span data-stu-id="e3e35-109">The value is invalid if it has been reclaimed by the garbage collector.</span></span>  
  
 <span data-ttu-id="e3e35-110">Bu yöntem kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="e3e35-110">This method has been deprecated.</span></span> <span data-ttu-id="e3e35-111">.NET Framework 2,0 ' de, tüm değerler [ICorDebugController:: Continue](icordebugcontroller-continue-method.md) çağrılana kadar geçerli olur, bu durumda değerler geçersiz kılınır.</span><span class="sxs-lookup"><span data-stu-id="e3e35-111">In the .NET Framework 2.0, all values are valid until [ICorDebugController::Continue](icordebugcontroller-continue-method.md) is called, at which time the values are invalidated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3e35-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e3e35-112">Requirements</span></span>  

 <span data-ttu-id="e3e35-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e3e35-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3e35-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e3e35-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e3e35-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e3e35-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e3e35-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e3e35-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
