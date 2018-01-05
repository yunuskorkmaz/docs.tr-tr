---
title: "ICorDebugHeapSegmentEnum::Next Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: Next
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugHeapSegmentEnum::Next
helpviewer_keywords:
- ICorDebugHeapSegmentEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugHeapSegmentEnum interface [.NET Framework debugging]
ms.assetid: 51625fd0-7399-49c7-b22b-5dfb05451fe6
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7f8e197bb5d31635e4abc8e8bc6e3d62eb7632be
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugheapsegmentenumnext-method"></a><span data-ttu-id="6e838-102">ICorDebugHeapSegmentEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6e838-102">ICorDebugHeapSegmentEnum::Next Method</span></span>
<span data-ttu-id="6e838-103">Belirtilen sayıda alır [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) Yönetilen yığın bellek bölgeler hakkında bilgiler içeren örnekleri.</span><span class="sxs-lookup"><span data-stu-id="6e838-103">Gets the specified number of [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances that contain information about memory regions of the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e838-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6e838-104">Syntax</span></span>  
  
```  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_SEGMENT segments[],   
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6e838-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6e838-105">Parameters</span></span>  
 <span data-ttu-id="6e838-106">celt</span><span class="sxs-lookup"><span data-stu-id="6e838-106">celt</span></span>  
 <span data-ttu-id="6e838-107">[in] Alınacak Segment sayısı.</span><span class="sxs-lookup"><span data-stu-id="6e838-107">[in] The number of segments to be retrieved.</span></span>  
  
 <span data-ttu-id="6e838-108">segmentler</span><span class="sxs-lookup"><span data-stu-id="6e838-108">segments</span></span>  
 <span data-ttu-id="6e838-109">[out] Her biri işaret işaretçileri, bir dizi bir [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) Yönetilen yığın bellekte bir bölge hakkında bilgi sağlayan nesne.</span><span class="sxs-lookup"><span data-stu-id="6e838-109">[out] An array of pointers, each of which points to a [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) object that provides information about a region of memory in the managed heap.</span></span>  
  
 <span data-ttu-id="6e838-110">pceltFetched</span><span class="sxs-lookup"><span data-stu-id="6e838-110">pceltFetched</span></span>  
 <span data-ttu-id="6e838-111">[out] Sayısını gösteren bir işaretçi [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) gerçekte döndürülen nesneleri `segments`.</span><span class="sxs-lookup"><span data-stu-id="6e838-111">[out] A pointer to the number of [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objects actually returned in `segments`.</span></span> <span data-ttu-id="6e838-112">Bu değer olabilir `null` varsa `celt` 1'dir.</span><span class="sxs-lookup"><span data-stu-id="6e838-112">This value may be `null` if `celt` is 1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6e838-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6e838-113">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6e838-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6e838-114">Requirements</span></span>  
 <span data-ttu-id="6e838-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6e838-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6e838-116">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6e838-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6e838-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6e838-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6e838-118">**.NET framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6e838-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e838-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6e838-119">See Also</span></span>  
 [<span data-ttu-id="6e838-120">ICorDebugHeapSegmentEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6e838-120">ICorDebugHeapSegmentEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md)  
 [<span data-ttu-id="6e838-121">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="6e838-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
