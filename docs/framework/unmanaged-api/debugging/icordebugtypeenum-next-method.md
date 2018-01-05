---
title: "ICorDebugTypeEnum::Next Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugTypeEnum.Next
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugTypeEnum::Next
helpviewer_keywords:
- ICorDebugTypeEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugTypeEnum interface [.NET Framework debugging]
ms.assetid: d0fdeba3-c195-4ece-8caf-79b1f40025d2
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 53acf78450e455a4f9778b1e508d79a921e20ae9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugtypeenumnext-method"></a><span data-ttu-id="ca9e3-102">ICorDebugTypeEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ca9e3-102">ICorDebugTypeEnum::Next Method</span></span>
<span data-ttu-id="ca9e3-103">Belirtilen "ICorDebugType" örneklerinin sayısını alır `celt` gelen geçerli konumdan başlayarak numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="ca9e3-103">Gets the number of "ICorDebugType" instances specified by `celt` from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca9e3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ca9e3-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in]  ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugType *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ca9e3-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ca9e3-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="ca9e3-106">[in] Sayısı `ICorDebugType` alınacak örnekleri.</span><span class="sxs-lookup"><span data-stu-id="ca9e3-106">[in] The number of `ICorDebugType` instances to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="ca9e3-107">[out] Her biri işaret işaretçileri, bir dizi bir `ICorDebugType` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="ca9e3-107">[out] An array of pointers, each of which points to an `ICorDebugType` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="ca9e3-108">[out] İşaretçi sayısına `ICorDebugType` gerçekte döndürülen örnek.</span><span class="sxs-lookup"><span data-stu-id="ca9e3-108">[out] Pointer to the number of `ICorDebugType` instances actually returned.</span></span> <span data-ttu-id="ca9e3-109">Bu değer null ise `celt` biridir.</span><span class="sxs-lookup"><span data-stu-id="ca9e3-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ca9e3-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ca9e3-110">Requirements</span></span>  
 <span data-ttu-id="ca9e3-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ca9e3-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca9e3-112">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ca9e3-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ca9e3-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ca9e3-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ca9e3-114">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ca9e3-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca9e3-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ca9e3-115">See Also</span></span>  
 
