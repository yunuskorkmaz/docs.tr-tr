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
ms.openlocfilehash: a1f4964c89aa3b658c57946d4b5a0327797118f1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728712"
---
# <a name="icordebugheapvalue3-interface"></a><span data-ttu-id="d99fe-102">ICorDebugHeapValue3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d99fe-102">ICorDebugHeapValue3 Interface</span></span>

<span data-ttu-id="d99fe-103">Nesnelerin monitör kilit özelliklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="d99fe-103">Exposes the monitor lock properties of objects.</span></span> <span data-ttu-id="d99fe-104">Bu arabirim ICorDebugHeapValue ve ICorDebugHeapValue2 arabirimlerini genişletir.</span><span class="sxs-lookup"><span data-stu-id="d99fe-104">This interface extends the ICorDebugHeapValue and ICorDebugHeapValue2 interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d99fe-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="d99fe-105">Methods</span></span>  
  
|<span data-ttu-id="d99fe-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="d99fe-106">Method</span></span>|<span data-ttu-id="d99fe-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d99fe-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d99fe-108">GetThreadOwningMonitorLock Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d99fe-108">GetThreadOwningMonitorLock Method</span></span>](icordebugheapvalue3-getthreadowningmonitorlock-method.md)|<span data-ttu-id="d99fe-109">Bu nesne üzerinde izleyici kilidine sahip yönetilen iş parçacığını döndürür.</span><span class="sxs-lookup"><span data-stu-id="d99fe-109">Returns the managed thread that owns the monitor lock on this object.</span></span>|  
|[<span data-ttu-id="d99fe-110">GetMonitorEventWaitList Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d99fe-110">GetMonitorEventWaitList Method</span></span>](icordebugheapvalue3-getmonitoreventwaitlist-method.md)|<span data-ttu-id="d99fe-111">Bir izleyici kilidi ile ilişkili olayda sıraya alınan iş parçacıklarının sıralı bir listesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="d99fe-111">Provides an ordered list of threads that are queued on the event that is associated with a monitor lock.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d99fe-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d99fe-112">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d99fe-113">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="d99fe-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d99fe-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d99fe-114">Requirements</span></span>  

 <span data-ttu-id="d99fe-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d99fe-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d99fe-116">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d99fe-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d99fe-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="d99fe-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d99fe-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d99fe-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d99fe-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d99fe-119">See also</span></span>

- [<span data-ttu-id="d99fe-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="d99fe-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="d99fe-121">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="d99fe-121">Debugging</span></span>](index.md)
