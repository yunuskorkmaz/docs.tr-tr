---
description: 'Bu konuda daha fazla bilgi edinin: CorDebugThreadState numaralandırması'
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
ms.openlocfilehash: 0cf83ee31547e49ccc7d09e0ab4ee85548688b36
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99661815"
---
# <a name="cordebugthreadstate-enumeration"></a><span data-ttu-id="1551b-103">CorDebugThreadState Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="1551b-103">CorDebugThreadState Enumeration</span></span>

<span data-ttu-id="1551b-104">Hata ayıklama için bir iş parçacığının durumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="1551b-104">Specifies the state of a thread for debugging.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1551b-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="1551b-105">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugThreadState {  
    THREAD_RUN,  
    THREAD_SUSPEND  
} CorDebugThreadState;  
```  
  
## <a name="members"></a><span data-ttu-id="1551b-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="1551b-106">Members</span></span>  
  
|<span data-ttu-id="1551b-107">Üye</span><span class="sxs-lookup"><span data-stu-id="1551b-107">Member</span></span>|<span data-ttu-id="1551b-108">Description</span><span class="sxs-lookup"><span data-stu-id="1551b-108">Description</span></span>|  
|------------|-----------------|  
|`THREAD_RUN`|<span data-ttu-id="1551b-109">Bir hata ayıklama olayı gerçekleşmediği takdirde iş parçacığı serbestçe çalışır.</span><span class="sxs-lookup"><span data-stu-id="1551b-109">The thread runs freely, unless a debug event occurs.</span></span>|  
|`THREAD_SUSPEND`|<span data-ttu-id="1551b-110">İş parçacığı çalıştırılamıyor.</span><span class="sxs-lookup"><span data-stu-id="1551b-110">The thread cannot run.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1551b-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1551b-111">Remarks</span></span>  

 <span data-ttu-id="1551b-112">Hata ayıklayıcı, `CorDebugThreadState` bir iş parçacığının yürütmesini denetlemek için sabit listesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="1551b-112">The debugger uses the `CorDebugThreadState` enumeration to control a thread's execution.</span></span> <span data-ttu-id="1551b-113">Bir iş parçacığının durumu [ICorDebugThread:: SetDebugState](icordebugthread-setdebugstate-method.md) veya [ICorDebugController:: SetAllThreadsDebugState](icordebugcontroller-setallthreadsdebugstate-method.md) yöntemi kullanılarak ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="1551b-113">The state of a thread can be set by using the [ICorDebugThread::SetDebugState](icordebugthread-setdebugstate-method.md) or [ICorDebugController::SetAllThreadsDebugState](icordebugcontroller-setallthreadsdebugstate-method.md) method.</span></span>  
  
 <span data-ttu-id="1551b-114">[BARıNDıRMA API](../hosting/index.md) 'sine sunulan bir geri çağırma, ileti balonları, bu nedenle kesintiye uğramış bir durum gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="1551b-114">A callback provided to the [hosting API](../hosting/index.md) enables message pumping, so an interrupted state is not needed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1551b-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1551b-115">Requirements</span></span>  

 <span data-ttu-id="1551b-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1551b-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1551b-117">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="1551b-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1551b-118">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="1551b-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1551b-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1551b-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1551b-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1551b-120">See also</span></span>

- [<span data-ttu-id="1551b-121">Hata Ayıklama Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="1551b-121">Debugging Enumerations</span></span>](debugging-enumerations.md)
