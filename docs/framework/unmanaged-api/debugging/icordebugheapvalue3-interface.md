---
title: ICorDebugHeapValue3 Arabirimi
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
- ICorDebugHeapValue3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue3
helpviewer_keywords:
- ICorDebugHeapValue3 interface [.NET Framework debugging]
ms.assetid: 9c421bb0-e647-4b2d-a986-f3d578cc7f20
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c7110ea2e39411d65d70ea14992959cdddc1d3bb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugheapvalue3-interface"></a><span data-ttu-id="a7f8e-102">ICorDebugHeapValue3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a7f8e-102">ICorDebugHeapValue3 Interface</span></span>
<span data-ttu-id="a7f8e-103">Nesnelerin monitör kilit özelliklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="a7f8e-103">Exposes the monitor lock properties of objects.</span></span> <span data-ttu-id="a7f8e-104">Bu arabirim Icordebugheapvalue ve Icordebugheapvalue2 arabirimleri genişletir.</span><span class="sxs-lookup"><span data-stu-id="a7f8e-104">This interface extends the ICorDebugHeapValue and ICorDebugHeapValue2 interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a7f8e-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="a7f8e-105">Methods</span></span>  
  
|<span data-ttu-id="a7f8e-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="a7f8e-106">Method</span></span>|<span data-ttu-id="a7f8e-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a7f8e-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a7f8e-108">GetThreadOwningMonitorLock Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a7f8e-108">GetThreadOwningMonitorLock Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue3-getthreadowningmonitorlock-method.md)|<span data-ttu-id="a7f8e-109">Bu nesne üzerinde İzleyici kilit sahibi yönetilen iş parçacığı döndürür.</span><span class="sxs-lookup"><span data-stu-id="a7f8e-109">Returns the managed thread that owns the monitor lock on this object.</span></span>|  
|[<span data-ttu-id="a7f8e-110">GetMonitorEventWaitList Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a7f8e-110">GetMonitorEventWaitList Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue3-getmonitoreventwaitlist-method.md)|<span data-ttu-id="a7f8e-111">İzleyici kilit ile ilişkili olay sıraya alınan iş parçacıkları sıralı bir listesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="a7f8e-111">Provides an ordered list of threads that are queued on the event that is associated with a monitor lock.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a7f8e-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a7f8e-112">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a7f8e-113">Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="a7f8e-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7f8e-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a7f8e-114">Requirements</span></span>  
 <span data-ttu-id="a7f8e-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a7f8e-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7f8e-116">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a7f8e-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a7f8e-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a7f8e-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a7f8e-118">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a7f8e-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7f8e-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a7f8e-119">See Also</span></span>  
 [<span data-ttu-id="a7f8e-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="a7f8e-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="a7f8e-121">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="a7f8e-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
