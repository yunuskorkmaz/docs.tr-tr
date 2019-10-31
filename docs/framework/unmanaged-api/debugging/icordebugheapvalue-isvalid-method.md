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
ms.openlocfilehash: 7edf0065fa7eb39dada167a682f2b634a438f1f3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138394"
---
# <a name="icordebugheapvalueisvalid-method"></a><span data-ttu-id="1b75c-102">ICorDebugHeapValue::IsValid Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1b75c-102">ICorDebugHeapValue::IsValid Method</span></span>
<span data-ttu-id="1b75c-103">Bu ICorDebugHeapValue tarafından temsil edilen nesnenin geçerli olup olmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="1b75c-103">Gets a value that indicates whether the object represented by this ICorDebugHeapValue is valid.</span></span>  
  
 <span data-ttu-id="1b75c-104">Bu yöntem 2,0 .NET Framework sürümünde kullanımdan kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="1b75c-104">This method has been deprecated in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b75c-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1b75c-105">Syntax</span></span>  
  
```cpp  
HRESULT IsValid (  
    [out] BOOL    *pbValid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1b75c-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1b75c-106">Parameters</span></span>  
 `pbValid`  
 <span data-ttu-id="1b75c-107">dışı Yığın üzerinde bu değerin geçerli olup olmadığını belirten bir Boolean değer işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="1b75c-107">[out] A pointer to a Boolean value that indicates whether this value on the heap is valid.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1b75c-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1b75c-108">Remarks</span></span>  
 <span data-ttu-id="1b75c-109">Değer çöp toplayıcı tarafından geri kazanımışsa geçersizdir.</span><span class="sxs-lookup"><span data-stu-id="1b75c-109">The value is invalid if it has been reclaimed by the garbage collector.</span></span>  
  
 <span data-ttu-id="1b75c-110">Bu yöntem kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="1b75c-110">This method has been deprecated.</span></span> <span data-ttu-id="1b75c-111">.NET Framework 2,0 ' de, tüm değerler [ICorDebugController:: Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) çağrılana kadar geçerli olur, bu durumda değerler geçersiz kılınır.</span><span class="sxs-lookup"><span data-stu-id="1b75c-111">In the .NET Framework 2.0, all values are valid until [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) is called, at which time the values are invalidated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b75c-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1b75c-112">Requirements</span></span>  
 <span data-ttu-id="1b75c-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1b75c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b75c-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="1b75c-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1b75c-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="1b75c-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1b75c-116">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b75c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
