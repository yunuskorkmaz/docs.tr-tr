---
title: ICorDebugValueEnum::Next Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugValueEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValueEnum::Next
helpviewer_keywords:
- ICorDebugValueEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugValueEnum interface [.NET Framework debugging]
ms.assetid: f5ef94dd-dfee-49d3-a398-b110f8906dd8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b24507c7cb0860fc04fa519c6bd95113483f629d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61993713"
---
# <a name="icordebugvalueenumnext-method"></a><span data-ttu-id="20321-102">ICorDebugValueEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="20321-102">ICorDebugValueEnum::Next Method</span></span>
<span data-ttu-id="20321-103">Numaralandırma, geçerli konumdan başlayarak belirtilen "ICorDebugValue" örnek sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="20321-103">Gets the specified number of "ICorDebugValue" instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20321-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="20321-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in]  ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugValue *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="20321-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="20321-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="20321-106">[in] Sayısını `ICorDebugValue` alınacak örnekleri.</span><span class="sxs-lookup"><span data-stu-id="20321-106">[in] The number of `ICorDebugValue` instances to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="20321-107">[out] Bir dizi işaretçileri, her biri için işaret eden bir `ICorDebugValue` nesne.</span><span class="sxs-lookup"><span data-stu-id="20321-107">[out] An array of pointers, each of which points to an `ICorDebugValue` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="20321-108">[out] İşaretçi sayısına `ICorDebugValue` gerçekte döndürülen örnekleri.</span><span class="sxs-lookup"><span data-stu-id="20321-108">[out] Pointer to the number of `ICorDebugValue` instances actually returned.</span></span> <span data-ttu-id="20321-109">Bu değer null olabilir, `celt` biridir.</span><span class="sxs-lookup"><span data-stu-id="20321-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20321-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="20321-110">Requirements</span></span>  
 <span data-ttu-id="20321-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="20321-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20321-112">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="20321-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="20321-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="20321-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="20321-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20321-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20321-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="20321-115">See also</span></span>
