---
title: "ICorDebugGCReferenceEnum::Next Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugGCReferenceEnum.Next
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugGCReferenceEnum::Next
helpviewer_keywords:
- Next method, ICorDebugGCReferenceEnum interface [.NET Framework debugging]
- ICorDebugGCReferenceEnum::Next method [.NET Framework debugging]
ms.assetid: 91b1345c-a94f-4ef8-9696-3823d06c6d05
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 55a02b88076d6097415d108d58f74565d1f426de
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebuggcreferenceenumnext-method"></a><span data-ttu-id="5470a-102">ICorDebugGCReferenceEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5470a-102">ICorDebugGCReferenceEnum::Next Method</span></span>
<span data-ttu-id="5470a-103">Belirtilen sayıda alır [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) çöpünün toplanma olacak nesneleri hakkında bilgi içeren örnekleri.</span><span class="sxs-lookup"><span data-stu-id="5470a-103">Gets the specified number of [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) instances that contain information about objects that will be garbage-collected.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5470a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5470a-104">Syntax</span></span>  
  
```  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_GC_REFERENCE roots[],   
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5470a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5470a-105">Parameters</span></span>  
 <span data-ttu-id="5470a-106">celt</span><span class="sxs-lookup"><span data-stu-id="5470a-106">celt</span></span>  
 <span data-ttu-id="5470a-107">[in] Alınacak kökleri sayısı.</span><span class="sxs-lookup"><span data-stu-id="5470a-107">[in] The number of roots to be retrieved.</span></span>  
  
 <span data-ttu-id="5470a-108">kökler</span><span class="sxs-lookup"><span data-stu-id="5470a-108">roots</span></span>  
 <span data-ttu-id="5470a-109">[out] Her biri işaret işaretçileri, bir dizi bir [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) çöpünün toplanma olması için bir nesne kökünü temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="5470a-109">[out] An array of pointers, each of which points to a [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) object that represents the root of an object to be garbage-collected.</span></span>  
  
 <span data-ttu-id="5470a-110">pceltFetched</span><span class="sxs-lookup"><span data-stu-id="5470a-110">pceltFetched</span></span>  
 <span data-ttu-id="5470a-111">[out] Sayısını gösteren bir işaretçi [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) gerçekte döndürülen nesneleri `roots`.</span><span class="sxs-lookup"><span data-stu-id="5470a-111">[out] A pointer to the number of [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) objects actually returned in `roots`.</span></span> <span data-ttu-id="5470a-112">Bu değer olabilir `null` varsa `celt` 1'dir.</span><span class="sxs-lookup"><span data-stu-id="5470a-112">This value may be `null` if `celt` is 1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5470a-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5470a-113">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5470a-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5470a-114">Requirements</span></span>  
 <span data-ttu-id="5470a-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5470a-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5470a-116">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5470a-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5470a-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5470a-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5470a-118">**.NET framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5470a-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5470a-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5470a-119">See Also</span></span>  
 [<span data-ttu-id="5470a-120">Icordebuggcreferenceenum arabirimi</span><span class="sxs-lookup"><span data-stu-id="5470a-120">ICorDebugGCReferenceEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md)  
 [<span data-ttu-id="5470a-121">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="5470a-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
