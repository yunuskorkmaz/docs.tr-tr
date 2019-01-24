---
title: ICorDebugCodeEnum::Next Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugCodeEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCodeEnum::Next
helpviewer_keywords:
- ICorDebugCodeEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugEnum interface [.NET Framework debugging]
ms.assetid: 644ece86-384d-4c63-9fba-52c789616ff7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 45caad20ef7d2dbe35e0381fb8cd697fc526398f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54529810"
---
# <a name="icordebugcodeenumnext-method"></a><span data-ttu-id="9bf65-102">ICorDebugCodeEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9bf65-102">ICorDebugCodeEnum::Next Method</span></span>
<span data-ttu-id="9bf65-103">Numaralandırma, geçerli konumdan başlayarak belirtilen "ICorDebugCode" örnek sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="9bf65-103">Gets the specified number of "ICorDebugCode" instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9bf65-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9bf65-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugCode *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9bf65-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9bf65-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="9bf65-106">[in] Sayısını `ICorDebugCode` alınacak örnekleri.</span><span class="sxs-lookup"><span data-stu-id="9bf65-106">[in] The number of `ICorDebugCode` instances to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="9bf65-107">[out] Bir dizi işaretçileri, her biri için işaret eden bir `ICorDebugCode` nesne.</span><span class="sxs-lookup"><span data-stu-id="9bf65-107">[out] An array of pointers, each of which points to an `ICorDebugCode` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="9bf65-108">[out] Bir işaretçi sayısına `ICorDebugCode` gerçekte döndürülen örnekleri.</span><span class="sxs-lookup"><span data-stu-id="9bf65-108">[out] A pointer to the number of `ICorDebugCode` instances actually returned.</span></span> <span data-ttu-id="9bf65-109">Bu değer null olabilir, `celt` biridir.</span><span class="sxs-lookup"><span data-stu-id="9bf65-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9bf65-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9bf65-110">Requirements</span></span>  
 <span data-ttu-id="9bf65-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9bf65-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9bf65-112">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9bf65-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9bf65-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9bf65-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9bf65-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9bf65-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bf65-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9bf65-115">See also</span></span>


