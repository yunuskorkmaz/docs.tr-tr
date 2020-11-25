---
title: CorDebugThreadState Numaralandırması
ms.date: 03/30/2017
api_name:
- CorDebugThreadState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugThreadState
helpviewer_keywords:
- CorDebugThreadState enumeration [.NET Framework debugging]
ms.assetid: a3ccdf18-4ec6-494d-9024-48e5c8c724f5
topic_type:
- apiref
ms.openlocfilehash: 5eee2aee5873fe512136bc5407e395acdc31af29
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722615"
---
# <a name="cordebugthreadstate-enumeration"></a><span data-ttu-id="8ad62-102">CorDebugThreadState Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="8ad62-102">CorDebugThreadState Enumeration</span></span>

<span data-ttu-id="8ad62-103">Hata ayıklama için bir iş parçacığının durumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="8ad62-103">Specifies the state of a thread for debugging.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ad62-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="8ad62-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugThreadState {  
    THREAD_RUN,  
    THREAD_SUSPEND  
} CorDebugThreadState;  
```  
  
## <a name="members"></a><span data-ttu-id="8ad62-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="8ad62-105">Members</span></span>  
  
|<span data-ttu-id="8ad62-106">Üye</span><span class="sxs-lookup"><span data-stu-id="8ad62-106">Member</span></span>|<span data-ttu-id="8ad62-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8ad62-107">Description</span></span>|  
|------------|-----------------|  
|`THREAD_RUN`|<span data-ttu-id="8ad62-108">Bir hata ayıklama olayı gerçekleşmediği takdirde iş parçacığı serbestçe çalışır.</span><span class="sxs-lookup"><span data-stu-id="8ad62-108">The thread runs freely, unless a debug event occurs.</span></span>|  
|`THREAD_SUSPEND`|<span data-ttu-id="8ad62-109">İş parçacığı çalıştırılamıyor.</span><span class="sxs-lookup"><span data-stu-id="8ad62-109">The thread cannot run.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8ad62-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8ad62-110">Remarks</span></span>  

 <span data-ttu-id="8ad62-111">Hata ayıklayıcı, `CorDebugThreadState` bir iş parçacığının yürütmesini denetlemek için sabit listesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="8ad62-111">The debugger uses the `CorDebugThreadState` enumeration to control a thread's execution.</span></span> <span data-ttu-id="8ad62-112">Bir iş parçacığının durumu [ICorDebugThread:: SetDebugState](icordebugthread-setdebugstate-method.md) veya [ICorDebugController:: SetAllThreadsDebugState](icordebugcontroller-setallthreadsdebugstate-method.md) yöntemi kullanılarak ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="8ad62-112">The state of a thread can be set by using the [ICorDebugThread::SetDebugState](icordebugthread-setdebugstate-method.md) or [ICorDebugController::SetAllThreadsDebugState](icordebugcontroller-setallthreadsdebugstate-method.md) method.</span></span>  
  
 <span data-ttu-id="8ad62-113">[BARıNDıRMA API](../hosting/index.md) 'sine sunulan bir geri çağırma, ileti balonları, bu nedenle kesintiye uğramış bir durum gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="8ad62-113">A callback provided to the [hosting API](../hosting/index.md) enables message pumping, so an interrupted state is not needed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ad62-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8ad62-114">Requirements</span></span>  

 <span data-ttu-id="8ad62-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8ad62-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ad62-116">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="8ad62-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8ad62-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="8ad62-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8ad62-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ad62-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ad62-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8ad62-119">See also</span></span>

- [<span data-ttu-id="8ad62-120">Hata Ayıklama Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="8ad62-120">Debugging Enumerations</span></span>](debugging-enumerations.md)
