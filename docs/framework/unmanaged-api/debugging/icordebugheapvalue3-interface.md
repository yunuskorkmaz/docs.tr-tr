---
description: 'Daha fazla bilgi edinin: ICorDebugHeapValue3 Interface'
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
ms.openlocfilehash: 2483f74e2cfc105fd23c37af6ada467f17b9556b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791471"
---
# <a name="icordebugheapvalue3-interface"></a><span data-ttu-id="cb607-103">ICorDebugHeapValue3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cb607-103">ICorDebugHeapValue3 Interface</span></span>

<span data-ttu-id="cb607-104">Nesnelerin monitör kilit özelliklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="cb607-104">Exposes the monitor lock properties of objects.</span></span> <span data-ttu-id="cb607-105">Bu arabirim ICorDebugHeapValue ve ICorDebugHeapValue2 arabirimlerini genişletir.</span><span class="sxs-lookup"><span data-stu-id="cb607-105">This interface extends the ICorDebugHeapValue and ICorDebugHeapValue2 interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cb607-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="cb607-106">Methods</span></span>  
  
|<span data-ttu-id="cb607-107">Yöntem</span><span class="sxs-lookup"><span data-stu-id="cb607-107">Method</span></span>|<span data-ttu-id="cb607-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cb607-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cb607-109">GetThreadOwningMonitorLock Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cb607-109">GetThreadOwningMonitorLock Method</span></span>](icordebugheapvalue3-getthreadowningmonitorlock-method.md)|<span data-ttu-id="cb607-110">Bu nesne üzerinde izleyici kilidine sahip yönetilen iş parçacığını döndürür.</span><span class="sxs-lookup"><span data-stu-id="cb607-110">Returns the managed thread that owns the monitor lock on this object.</span></span>|  
|[<span data-ttu-id="cb607-111">GetMonitorEventWaitList Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cb607-111">GetMonitorEventWaitList Method</span></span>](icordebugheapvalue3-getmonitoreventwaitlist-method.md)|<span data-ttu-id="cb607-112">Bir izleyici kilidi ile ilişkili olayda sıraya alınan iş parçacıklarının sıralı bir listesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="cb607-112">Provides an ordered list of threads that are queued on the event that is associated with a monitor lock.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cb607-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cb607-113">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cb607-114">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="cb607-114">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb607-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cb607-115">Requirements</span></span>  

 <span data-ttu-id="cb607-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb607-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb607-117">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="cb607-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cb607-118">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="cb607-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cb607-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb607-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb607-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cb607-120">See also</span></span>

- [<span data-ttu-id="cb607-121">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="cb607-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="cb607-122">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="cb607-122">Debugging</span></span>](index.md)
