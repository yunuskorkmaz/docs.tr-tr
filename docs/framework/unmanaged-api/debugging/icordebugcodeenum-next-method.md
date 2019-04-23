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
ms.openlocfilehash: 5db87cd4ad965654b63a68828cd088b8d2f7d07c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59113054"
---
# <a name="icordebugcodeenumnext-method"></a><span data-ttu-id="4c58a-102">ICorDebugCodeEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4c58a-102">ICorDebugCodeEnum::Next Method</span></span>
<span data-ttu-id="4c58a-103">Numaralandırma, geçerli konumdan başlayarak belirtilen "ICorDebugCode" örnek sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="4c58a-103">Gets the specified number of "ICorDebugCode" instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c58a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4c58a-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugCode *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4c58a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4c58a-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="4c58a-106">[in] Sayısını `ICorDebugCode` alınacak örnekleri.</span><span class="sxs-lookup"><span data-stu-id="4c58a-106">[in] The number of `ICorDebugCode` instances to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="4c58a-107">[out] Bir dizi işaretçileri, her biri için işaret eden bir `ICorDebugCode` nesne.</span><span class="sxs-lookup"><span data-stu-id="4c58a-107">[out] An array of pointers, each of which points to an `ICorDebugCode` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="4c58a-108">[out] Bir işaretçi sayısına `ICorDebugCode` gerçekte döndürülen örnekleri.</span><span class="sxs-lookup"><span data-stu-id="4c58a-108">[out] A pointer to the number of `ICorDebugCode` instances actually returned.</span></span> <span data-ttu-id="4c58a-109">Bu değer null olabilir, `celt` biridir.</span><span class="sxs-lookup"><span data-stu-id="4c58a-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4c58a-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4c58a-110">Requirements</span></span>  
 <span data-ttu-id="4c58a-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4c58a-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4c58a-112">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4c58a-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4c58a-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4c58a-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4c58a-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4c58a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c58a-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4c58a-115">See also</span></span>
