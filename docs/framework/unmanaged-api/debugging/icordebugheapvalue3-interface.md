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
ms.openlocfilehash: 08a9bc8aa4aa70ad6b01c58abccd145ae43d8a52
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54568304"
---
# <a name="icordebugheapvalue3-interface"></a><span data-ttu-id="f5095-102">ICorDebugHeapValue3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f5095-102">ICorDebugHeapValue3 Interface</span></span>
<span data-ttu-id="f5095-103">Nesnelerin monitör kilit özelliklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="f5095-103">Exposes the monitor lock properties of objects.</span></span> <span data-ttu-id="f5095-104">Icordebugheapvalue ve Icordebugheapvalue2 arabirimi bu arabirim genişletir.</span><span class="sxs-lookup"><span data-stu-id="f5095-104">This interface extends the ICorDebugHeapValue and ICorDebugHeapValue2 interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f5095-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="f5095-105">Methods</span></span>  
  
|<span data-ttu-id="f5095-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="f5095-106">Method</span></span>|<span data-ttu-id="f5095-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f5095-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f5095-108">GetThreadOwningMonitorLock Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f5095-108">GetThreadOwningMonitorLock Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue3-getthreadowningmonitorlock-method.md)|<span data-ttu-id="f5095-109">Bu nesne izleme kilidi sahibi yönetilen iş parçacığı döndürür.</span><span class="sxs-lookup"><span data-stu-id="f5095-109">Returns the managed thread that owns the monitor lock on this object.</span></span>|  
|[<span data-ttu-id="f5095-110">GetMonitorEventWaitList Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f5095-110">GetMonitorEventWaitList Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue3-getmonitoreventwaitlist-method.md)|<span data-ttu-id="f5095-111">Monitör kilit ile ilişkili olay sıraya alınan iş parçacıkları sıralı bir listesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="f5095-111">Provides an ordered list of threads that are queued on the event that is associated with a monitor lock.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f5095-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f5095-112">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f5095-113">Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="f5095-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5095-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f5095-114">Requirements</span></span>  
 <span data-ttu-id="f5095-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f5095-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5095-116">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f5095-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f5095-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f5095-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f5095-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5095-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5095-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f5095-119">See also</span></span>
- [<span data-ttu-id="f5095-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="f5095-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="f5095-121">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="f5095-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
