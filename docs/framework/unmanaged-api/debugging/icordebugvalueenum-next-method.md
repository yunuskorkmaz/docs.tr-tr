---
title: "ICorDebugValueEnum::Next Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugValueEnum.Next
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugValueEnum::Next
helpviewer_keywords:
- ICorDebugValueEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugValueEnum interface [.NET Framework debugging]
ms.assetid: f5ef94dd-dfee-49d3-a398-b110f8906dd8
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 71775db7134c8f376099b0820f4330602d3db0e6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugvalueenumnext-method"></a><span data-ttu-id="e1fb7-102">ICorDebugValueEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e1fb7-102">ICorDebugValueEnum::Next Method</span></span>
<span data-ttu-id="e1fb7-103">Geçerli konumdan başlayarak numaralandırma, belirtilen sayıda "ICorDebugValue" örneklerini alır.</span><span class="sxs-lookup"><span data-stu-id="e1fb7-103">Gets the specified number of "ICorDebugValue" instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1fb7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e1fb7-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in]  ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugValue *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e1fb7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e1fb7-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="e1fb7-106">[in] Sayısı `ICorDebugValue` alınacak örnekleri.</span><span class="sxs-lookup"><span data-stu-id="e1fb7-106">[in] The number of `ICorDebugValue` instances to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="e1fb7-107">[out] Her biri işaret işaretçileri, bir dizi bir `ICorDebugValue` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="e1fb7-107">[out] An array of pointers, each of which points to an `ICorDebugValue` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="e1fb7-108">[out] İşaretçi sayısına `ICorDebugValue` gerçekte döndürülen örnek.</span><span class="sxs-lookup"><span data-stu-id="e1fb7-108">[out] Pointer to the number of `ICorDebugValue` instances actually returned.</span></span> <span data-ttu-id="e1fb7-109">Bu değer null ise `celt` biridir.</span><span class="sxs-lookup"><span data-stu-id="e1fb7-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e1fb7-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e1fb7-110">Requirements</span></span>  
 <span data-ttu-id="e1fb7-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e1fb7-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e1fb7-112">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e1fb7-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e1fb7-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e1fb7-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e1fb7-114">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e1fb7-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1fb7-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e1fb7-115">See Also</span></span>  
    
 
