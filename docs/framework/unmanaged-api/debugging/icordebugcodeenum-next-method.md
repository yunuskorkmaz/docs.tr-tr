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
ms.openlocfilehash: e70f7ce9cd943fc3641eef710502ae7f50b369e1
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67748552"
---
# <a name="icordebugcodeenumnext-method"></a><span data-ttu-id="f5f1e-102">ICorDebugCodeEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f5f1e-102">ICorDebugCodeEnum::Next Method</span></span>
<span data-ttu-id="f5f1e-103">Numaralandırma, geçerli konumdan başlayarak belirtilen "ICorDebugCode" örnek sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="f5f1e-103">Gets the specified number of "ICorDebugCode" instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5f1e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f5f1e-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugCode *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f5f1e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f5f1e-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="f5f1e-106">[in] Sayısını `ICorDebugCode` alınacak örnekleri.</span><span class="sxs-lookup"><span data-stu-id="f5f1e-106">[in] The number of `ICorDebugCode` instances to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="f5f1e-107">[out] Bir dizi işaretçileri, her biri için işaret eden bir `ICorDebugCode` nesne.</span><span class="sxs-lookup"><span data-stu-id="f5f1e-107">[out] An array of pointers, each of which points to an `ICorDebugCode` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="f5f1e-108">[out] Bir işaretçi sayısına `ICorDebugCode` gerçekte döndürülen örnekleri.</span><span class="sxs-lookup"><span data-stu-id="f5f1e-108">[out] A pointer to the number of `ICorDebugCode` instances actually returned.</span></span> <span data-ttu-id="f5f1e-109">Bu değer null olabilir, `celt` biridir.</span><span class="sxs-lookup"><span data-stu-id="f5f1e-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5f1e-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f5f1e-110">Requirements</span></span>  
 <span data-ttu-id="f5f1e-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f5f1e-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5f1e-112">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f5f1e-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f5f1e-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f5f1e-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f5f1e-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5f1e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5f1e-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f5f1e-115">See also</span></span>
