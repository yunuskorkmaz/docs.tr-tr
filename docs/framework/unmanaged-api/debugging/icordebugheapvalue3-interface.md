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
ms.openlocfilehash: 5add6da1ace372ecf6e513902bbf98f5f79c6778
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210403"
---
# <a name="icordebugheapvalue3-interface"></a><span data-ttu-id="9e76a-102">ICorDebugHeapValue3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9e76a-102">ICorDebugHeapValue3 Interface</span></span>
<span data-ttu-id="9e76a-103">Nesnelerin monitör kilit özelliklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="9e76a-103">Exposes the monitor lock properties of objects.</span></span> <span data-ttu-id="9e76a-104">Bu arabirim ICorDebugHeapValue ve ICorDebugHeapValue2 arabirimlerini genişletir.</span><span class="sxs-lookup"><span data-stu-id="9e76a-104">This interface extends the ICorDebugHeapValue and ICorDebugHeapValue2 interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9e76a-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="9e76a-105">Methods</span></span>  
  
|<span data-ttu-id="9e76a-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="9e76a-106">Method</span></span>|<span data-ttu-id="9e76a-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9e76a-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9e76a-108">GetThreadOwningMonitorLock Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9e76a-108">GetThreadOwningMonitorLock Method</span></span>](icordebugheapvalue3-getthreadowningmonitorlock-method.md)|<span data-ttu-id="9e76a-109">Bu nesne üzerinde izleyici kilidine sahip yönetilen iş parçacığını döndürür.</span><span class="sxs-lookup"><span data-stu-id="9e76a-109">Returns the managed thread that owns the monitor lock on this object.</span></span>|  
|[<span data-ttu-id="9e76a-110">GetMonitorEventWaitList Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9e76a-110">GetMonitorEventWaitList Method</span></span>](icordebugheapvalue3-getmonitoreventwaitlist-method.md)|<span data-ttu-id="9e76a-111">Bir izleyici kilidi ile ilişkili olayda sıraya alınan iş parçacıklarının sıralı bir listesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="9e76a-111">Provides an ordered list of threads that are queued on the event that is associated with a monitor lock.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9e76a-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9e76a-112">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9e76a-113">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="9e76a-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e76a-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9e76a-114">Requirements</span></span>  
 <span data-ttu-id="9e76a-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9e76a-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e76a-116">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="9e76a-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9e76a-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="9e76a-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9e76a-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9e76a-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e76a-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9e76a-119">See also</span></span>

- [<span data-ttu-id="9e76a-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="9e76a-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="9e76a-121">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="9e76a-121">Debugging</span></span>](index.md)
