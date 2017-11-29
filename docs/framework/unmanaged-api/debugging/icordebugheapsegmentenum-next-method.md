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
ms.openlocfilehash: 655bc404003c4af3aa2ba934ee192b378caf2f2e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugheapsegmentenumnext-method"></a><span data-ttu-id="62014-102">ICorDebugHeapSegmentEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="62014-102">ICorDebugHeapSegmentEnum::Next Method</span></span>
<span data-ttu-id="62014-103">Belirtilen sayıda alır [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) Yönetilen yığın bellek bölgeler hakkında bilgiler içeren örnekleri.</span><span class="sxs-lookup"><span data-stu-id="62014-103">Gets the specified number of [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances that contain information about memory regions of the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62014-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="62014-104">Syntax</span></span>  
  
```  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_SEGMENT segments[],   
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="62014-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="62014-105">Parameters</span></span>  
 <span data-ttu-id="62014-106">celt</span><span class="sxs-lookup"><span data-stu-id="62014-106">celt</span></span>  
 <span data-ttu-id="62014-107">[in] Alınacak Segment sayısı.</span><span class="sxs-lookup"><span data-stu-id="62014-107">[in] The number of segments to be retrieved.</span></span>  
  
 <span data-ttu-id="62014-108">segmentler</span><span class="sxs-lookup"><span data-stu-id="62014-108">segments</span></span>  
 <span data-ttu-id="62014-109">[out] Her biri işaret işaretçileri, bir dizi bir [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) Yönetilen yığın bellekte bir bölge hakkında bilgi sağlayan nesne.</span><span class="sxs-lookup"><span data-stu-id="62014-109">[out] An array of pointers, each of which points to a [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) object that provides information about a region of memory in the managed heap.</span></span>  
  
 <span data-ttu-id="62014-110">pceltFetched</span><span class="sxs-lookup"><span data-stu-id="62014-110">pceltFetched</span></span>  
 <span data-ttu-id="62014-111">[out] Sayısını gösteren bir işaretçi [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) gerçekte döndürülen nesneleri `segments`.</span><span class="sxs-lookup"><span data-stu-id="62014-111">[out] A pointer to the number of [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objects actually returned in `segments`.</span></span> <span data-ttu-id="62014-112">Bu değer olabilir `null` varsa `celt` 1'dir.</span><span class="sxs-lookup"><span data-stu-id="62014-112">This value may be `null` if `celt` is 1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="62014-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="62014-113">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="62014-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="62014-114">Requirements</span></span>  
 <span data-ttu-id="62014-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="62014-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62014-116">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="62014-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="62014-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="62014-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="62014-118">**.NET framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="62014-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62014-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="62014-119">See Also</span></span>  
 [<span data-ttu-id="62014-120">Icordebugheapsegmentenum arabirimi</span><span class="sxs-lookup"><span data-stu-id="62014-120">ICorDebugHeapSegmentEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md)  
 [<span data-ttu-id="62014-121">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="62014-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
