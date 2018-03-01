---
title: "ICorDebugGCReferenceEnum::Next Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugGCReferenceEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGCReferenceEnum::Next
helpviewer_keywords:
- Next method, ICorDebugGCReferenceEnum interface [.NET Framework debugging]
- ICorDebugGCReferenceEnum::Next method [.NET Framework debugging]
ms.assetid: 91b1345c-a94f-4ef8-9696-3823d06c6d05
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e61edea76b4e3be8a03000899b72d486163ceaf6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebuggcreferenceenumnext-method"></a><span data-ttu-id="339e8-102">ICorDebugGCReferenceEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="339e8-102">ICorDebugGCReferenceEnum::Next Method</span></span>
<span data-ttu-id="339e8-103">Belirtilen sayıda alır [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) çöpünün toplanma olacak nesneleri hakkında bilgi içeren örnekleri.</span><span class="sxs-lookup"><span data-stu-id="339e8-103">Gets the specified number of [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) instances that contain information about objects that will be garbage-collected.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="339e8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="339e8-104">Syntax</span></span>  
  
```  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_GC_REFERENCE roots[],   
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="339e8-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="339e8-105">Parameters</span></span>  
 <span data-ttu-id="339e8-106">celt</span><span class="sxs-lookup"><span data-stu-id="339e8-106">celt</span></span>  
 <span data-ttu-id="339e8-107">[in] Alınacak kökleri sayısı.</span><span class="sxs-lookup"><span data-stu-id="339e8-107">[in] The number of roots to be retrieved.</span></span>  
  
 <span data-ttu-id="339e8-108">kökler</span><span class="sxs-lookup"><span data-stu-id="339e8-108">roots</span></span>  
 <span data-ttu-id="339e8-109">[out] Her biri işaret işaretçileri, bir dizi bir [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) çöpünün toplanma olması için bir nesne kökünü temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="339e8-109">[out] An array of pointers, each of which points to a [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) object that represents the root of an object to be garbage-collected.</span></span>  
  
 <span data-ttu-id="339e8-110">pceltFetched</span><span class="sxs-lookup"><span data-stu-id="339e8-110">pceltFetched</span></span>  
 <span data-ttu-id="339e8-111">[out] Sayısını gösteren bir işaretçi [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) gerçekte döndürülen nesneleri `roots`.</span><span class="sxs-lookup"><span data-stu-id="339e8-111">[out] A pointer to the number of [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) objects actually returned in `roots`.</span></span> <span data-ttu-id="339e8-112">Bu değer olabilir `null` varsa `celt` 1'dir.</span><span class="sxs-lookup"><span data-stu-id="339e8-112">This value may be `null` if `celt` is 1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="339e8-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="339e8-113">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="339e8-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="339e8-114">Requirements</span></span>  
 <span data-ttu-id="339e8-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="339e8-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="339e8-116">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="339e8-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="339e8-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="339e8-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="339e8-118">**.NET framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="339e8-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="339e8-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="339e8-119">See Also</span></span>  
 [<span data-ttu-id="339e8-120">ICorDebugGCReferenceEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="339e8-120">ICorDebugGCReferenceEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md)  
 [<span data-ttu-id="339e8-121">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="339e8-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
