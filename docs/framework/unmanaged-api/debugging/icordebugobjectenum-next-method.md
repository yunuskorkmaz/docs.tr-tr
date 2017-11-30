---
title: "ICorDebugObjectEnum::Next Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugObjectEnum.Next
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugObjectEnum::Next
helpviewer_keywords:
- Next method, ICorDebugObjectEnum interface [.NET Framework debugging]
- ICorDebugObjectEnum::Next method [.NET Framework debugging]
ms.assetid: 10093e3d-26b6-4ad7-8ef3-bbf66243fc02
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 72195dbf74639d5799bb96754019dddf0f30101a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugobjectenumnext-method"></a><span data-ttu-id="e6d4c-102">ICorDebugObjectEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e6d4c-102">ICorDebugObjectEnum::Next Method</span></span>
<span data-ttu-id="e6d4c-103">Geçerli konumdan başlayarak numaralandırması nesneleri belirtilen sayıdaki göreli sanal adresleri (RVAs) alır.</span><span class="sxs-lookup"><span data-stu-id="e6d4c-103">Gets the relative virtual addresses (RVAs) of the specified number of objects from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6d4c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e6d4c-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]    
        CORDB_ADDRESS objects[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e6d4c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e6d4c-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="e6d4c-106">[in] Alınacak nesne sayısı.</span><span class="sxs-lookup"><span data-stu-id="e6d4c-106">[in] The number of objects to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="e6d4c-107">[out] Her biri bir CORDB_ADDRESS nesnesine işaret eden bir dizi işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="e6d4c-107">[out] An array of pointers, each of which points to a CORDB_ADDRESS object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="e6d4c-108">[out] İşaretçi gerçekte döndürülen nesne sayısı.</span><span class="sxs-lookup"><span data-stu-id="e6d4c-108">[out] Pointer to the number of objects actually returned.</span></span> <span data-ttu-id="e6d4c-109">Bu değer null ise `celt` biridir.</span><span class="sxs-lookup"><span data-stu-id="e6d4c-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e6d4c-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e6d4c-110">Requirements</span></span>  
 <span data-ttu-id="e6d4c-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e6d4c-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e6d4c-112">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e6d4c-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e6d4c-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e6d4c-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e6d4c-114">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e6d4c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6d4c-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e6d4c-115">See Also</span></span>  
 
