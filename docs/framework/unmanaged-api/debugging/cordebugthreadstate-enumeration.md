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
ms.openlocfilehash: 1ff36e8ef6b7c02eea5b02bc22587bc3889df093
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133698"
---
# <a name="cordebugthreadstate-enumeration"></a><span data-ttu-id="2c9c5-102">CorDebugThreadState Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="2c9c5-102">CorDebugThreadState Enumeration</span></span>
<span data-ttu-id="2c9c5-103">Hata ayıklama için bir iş parçacığının durumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="2c9c5-103">Specifies the state of a thread for debugging.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c9c5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2c9c5-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugThreadState {  
    THREAD_RUN,  
    THREAD_SUSPEND  
} CorDebugThreadState;  
```  
  
## <a name="members"></a><span data-ttu-id="2c9c5-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="2c9c5-105">Members</span></span>  
  
|<span data-ttu-id="2c9c5-106">Üye</span><span class="sxs-lookup"><span data-stu-id="2c9c5-106">Member</span></span>|<span data-ttu-id="2c9c5-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2c9c5-107">Description</span></span>|  
|------------|-----------------|  
|`THREAD_RUN`|<span data-ttu-id="2c9c5-108">Bir hata ayıklama olayı gerçekleşmediği takdirde iş parçacığı serbestçe çalışır.</span><span class="sxs-lookup"><span data-stu-id="2c9c5-108">The thread runs freely, unless a debug event occurs.</span></span>|  
|`THREAD_SUSPEND`|<span data-ttu-id="2c9c5-109">İş parçacığı çalıştırılamıyor.</span><span class="sxs-lookup"><span data-stu-id="2c9c5-109">The thread cannot run.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2c9c5-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2c9c5-110">Remarks</span></span>  
 <span data-ttu-id="2c9c5-111">Hata ayıklayıcı, bir iş parçacığının yürütmesini denetlemek için `CorDebugThreadState` numaralandırmayı kullanır.</span><span class="sxs-lookup"><span data-stu-id="2c9c5-111">The debugger uses the `CorDebugThreadState` enumeration to control a thread's execution.</span></span> <span data-ttu-id="2c9c5-112">Bir iş parçacığının durumu [ICorDebugThread:: SetDebugState](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-setdebugstate-method.md) veya [ICorDebugController:: SetAllThreadsDebugState](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-setallthreadsdebugstate-method.md) yöntemi kullanılarak ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="2c9c5-112">The state of a thread can be set by using the [ICorDebugThread::SetDebugState](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-setdebugstate-method.md) or [ICorDebugController::SetAllThreadsDebugState](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-setallthreadsdebugstate-method.md) method.</span></span>  
  
 <span data-ttu-id="2c9c5-113">[BARıNDıRMA API](../../../../docs/framework/unmanaged-api/hosting/index.md) 'sine sunulan bir geri çağırma, ileti balonları, bu nedenle kesintiye uğramış bir durum gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="2c9c5-113">A callback provided to the [hosting API](../../../../docs/framework/unmanaged-api/hosting/index.md) enables message pumping, so an interrupted state is not needed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2c9c5-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2c9c5-114">Requirements</span></span>  
 <span data-ttu-id="2c9c5-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2c9c5-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c9c5-116">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="2c9c5-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2c9c5-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="2c9c5-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2c9c5-118">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c9c5-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c9c5-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2c9c5-119">See also</span></span>

- [<span data-ttu-id="2c9c5-120">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="2c9c5-120">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
