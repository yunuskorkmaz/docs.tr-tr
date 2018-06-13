---
title: ICorDebugHeapValue3 Arabirimi
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1a59d8bce6ae565687e7ed906f6c14332f0c5c71
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33416838"
---
# <a name="icordebugheapvalue3-interface"></a><span data-ttu-id="8cc0f-102">ICorDebugHeapValue3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8cc0f-102">ICorDebugHeapValue3 Interface</span></span>
<span data-ttu-id="8cc0f-103">Nesnelerin monitör kilit özelliklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="8cc0f-103">Exposes the monitor lock properties of objects.</span></span> <span data-ttu-id="8cc0f-104">Bu arabirim Icordebugheapvalue ve Icordebugheapvalue2 arabirimleri genişletir.</span><span class="sxs-lookup"><span data-stu-id="8cc0f-104">This interface extends the ICorDebugHeapValue and ICorDebugHeapValue2 interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8cc0f-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="8cc0f-105">Methods</span></span>  
  
|<span data-ttu-id="8cc0f-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="8cc0f-106">Method</span></span>|<span data-ttu-id="8cc0f-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8cc0f-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8cc0f-108">GetThreadOwningMonitorLock Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8cc0f-108">GetThreadOwningMonitorLock Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue3-getthreadowningmonitorlock-method.md)|<span data-ttu-id="8cc0f-109">Bu nesne üzerinde İzleyici kilit sahibi yönetilen iş parçacığı döndürür.</span><span class="sxs-lookup"><span data-stu-id="8cc0f-109">Returns the managed thread that owns the monitor lock on this object.</span></span>|  
|[<span data-ttu-id="8cc0f-110">GetMonitorEventWaitList Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8cc0f-110">GetMonitorEventWaitList Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue3-getmonitoreventwaitlist-method.md)|<span data-ttu-id="8cc0f-111">İzleyici kilit ile ilişkili olay sıraya alınan iş parçacıkları sıralı bir listesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="8cc0f-111">Provides an ordered list of threads that are queued on the event that is associated with a monitor lock.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8cc0f-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8cc0f-112">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8cc0f-113">Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="8cc0f-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8cc0f-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8cc0f-114">Requirements</span></span>  
 <span data-ttu-id="8cc0f-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8cc0f-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8cc0f-116">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8cc0f-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8cc0f-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8cc0f-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8cc0f-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8cc0f-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8cc0f-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8cc0f-119">See Also</span></span>  
 [<span data-ttu-id="8cc0f-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="8cc0f-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="8cc0f-121">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="8cc0f-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
