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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59174219"
---
# <a name="icordebugvalueenumnext-method"></a><span data-ttu-id="0a60f-102">ICorDebugValueEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0a60f-102">ICorDebugValueEnum::Next Method</span></span>
<span data-ttu-id="0a60f-103">Numaralandırma, geçerli konumdan başlayarak belirtilen "ICorDebugValue" örnek sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="0a60f-103">Gets the specified number of "ICorDebugValue" instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a60f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0a60f-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in]  ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugValue *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0a60f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0a60f-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="0a60f-106">[in] Sayısını `ICorDebugValue` alınacak örnekleri.</span><span class="sxs-lookup"><span data-stu-id="0a60f-106">[in] The number of `ICorDebugValue` instances to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="0a60f-107">[out] Bir dizi işaretçileri, her biri için işaret eden bir `ICorDebugValue` nesne.</span><span class="sxs-lookup"><span data-stu-id="0a60f-107">[out] An array of pointers, each of which points to an `ICorDebugValue` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="0a60f-108">[out] İşaretçi sayısına `ICorDebugValue` gerçekte döndürülen örnekleri.</span><span class="sxs-lookup"><span data-stu-id="0a60f-108">[out] Pointer to the number of `ICorDebugValue` instances actually returned.</span></span> <span data-ttu-id="0a60f-109">Bu değer null olabilir, `celt` biridir.</span><span class="sxs-lookup"><span data-stu-id="0a60f-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0a60f-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0a60f-110">Requirements</span></span>  
 <span data-ttu-id="0a60f-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0a60f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0a60f-112">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0a60f-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0a60f-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0a60f-113">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="0a60f-114">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="0a60f-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="0a60f-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0a60f-115">See also</span></span>
