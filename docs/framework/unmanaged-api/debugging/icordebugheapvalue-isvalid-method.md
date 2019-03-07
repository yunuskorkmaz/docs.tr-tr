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
ms.openlocfilehash: 6e1edb1d25a62a9a689c397339740e563d986c8b
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57478771"
---
# <a name="icordebugheapvalueisvalid-method"></a><span data-ttu-id="270ad-102">ICorDebugHeapValue::IsValid Yöntemi</span><span class="sxs-lookup"><span data-stu-id="270ad-102">ICorDebugHeapValue::IsValid Method</span></span>
<span data-ttu-id="270ad-103">Bu Icordebugheapvalue tarafından temsil edilen nesnenin geçerli olup olmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="270ad-103">Gets a value that indicates whether the object represented by this ICorDebugHeapValue is valid.</span></span>  
  
 <span data-ttu-id="270ad-104">Bu yöntem .NET Framework 2.0 sürümünde kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="270ad-104">This method has been deprecated in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="270ad-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="270ad-105">Syntax</span></span>  
  
```  
HRESULT IsValid (  
    [out] BOOL    *pbValid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="270ad-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="270ad-106">Parameters</span></span>  
 `pbValid`  
 <span data-ttu-id="270ad-107">[out] Yığındaki bu değerin geçerli olup olmadığını belirten Boolean bir değer için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="270ad-107">[out] A pointer to a Boolean value that indicates whether this value on the heap is valid.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="270ad-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="270ad-108">Remarks</span></span>  
 <span data-ttu-id="270ad-109">Çöp toplayıcısı tarafından iadesi, değeri geçersiz.</span><span class="sxs-lookup"><span data-stu-id="270ad-109">The value is invalid if it has been reclaimed by the garbage collector.</span></span>  
  
 <span data-ttu-id="270ad-110">Bu yöntem kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="270ad-110">This method has been deprecated.</span></span> <span data-ttu-id="270ad-111">.NET Framework 2.0 sürümünde, tüm kadar geçerli değerler [Icordebugcontroller::continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) , hangi zaman geçersiz değerler sırasında çağrılır.</span><span class="sxs-lookup"><span data-stu-id="270ad-111">In the .NET Framework 2.0, all values are valid until [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) is called, at which time the values are invalidated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="270ad-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="270ad-112">Requirements</span></span>  
 <span data-ttu-id="270ad-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="270ad-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="270ad-114">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="270ad-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="270ad-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="270ad-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="270ad-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="270ad-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
