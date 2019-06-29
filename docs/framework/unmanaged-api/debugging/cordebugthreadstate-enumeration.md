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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ba2ee070b7d03efc830058014aa445bb1a3d4329
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67422259"
---
# <a name="cordebugthreadstate-enumeration"></a><span data-ttu-id="7edce-102">CorDebugThreadState Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="7edce-102">CorDebugThreadState Enumeration</span></span>
<span data-ttu-id="7edce-103">Hata ayıklama için bir iş parçacığı durumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="7edce-103">Specifies the state of a thread for debugging.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7edce-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7edce-104">Syntax</span></span>  
  
```  
typedef enum CorDebugThreadState {  
    THREAD_RUN,  
    THREAD_SUSPEND  
} CorDebugThreadState;  
```  
  
## <a name="members"></a><span data-ttu-id="7edce-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="7edce-105">Members</span></span>  
  
|<span data-ttu-id="7edce-106">Üye</span><span class="sxs-lookup"><span data-stu-id="7edce-106">Member</span></span>|<span data-ttu-id="7edce-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7edce-107">Description</span></span>|  
|------------|-----------------|  
|`THREAD_RUN`|<span data-ttu-id="7edce-108">İş parçacığı, ücretsiz, hata ayıklama olayı gerçekleşmediği sürece çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="7edce-108">The thread runs freely, unless a debug event occurs.</span></span>|  
|`THREAD_SUSPEND`|<span data-ttu-id="7edce-109">İş parçacığı çalıştıramazsınız.</span><span class="sxs-lookup"><span data-stu-id="7edce-109">The thread cannot run.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7edce-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7edce-110">Remarks</span></span>  
 <span data-ttu-id="7edce-111">Hata ayıklayıcı kullanan `CorDebugThreadState` bir iş parçacığının yürütmesini denetlemek için sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="7edce-111">The debugger uses the `CorDebugThreadState` enumeration to control a thread's execution.</span></span> <span data-ttu-id="7edce-112">Bir iş parçacığı durumunu kullanarak ayarlayabilirsiniz [Icordebugthread::setdebugstate](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-setdebugstate-method.md) veya [Icordebugcontroller::setallthreadsdebugstate](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-setallthreadsdebugstate-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="7edce-112">The state of a thread can be set by using the [ICorDebugThread::SetDebugState](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-setdebugstate-method.md) or [ICorDebugController::SetAllThreadsDebugState](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-setallthreadsdebugstate-method.md) method.</span></span>  
  
 <span data-ttu-id="7edce-113">Sağlanan bir geri çağırma [API'sini barındıran](../../../../docs/framework/unmanaged-api/hosting/index.md) kesintiye uğramış bir duruma gerekli olmadığı için ileti Pompalama, sağlar.</span><span class="sxs-lookup"><span data-stu-id="7edce-113">A callback provided to the [hosting API](../../../../docs/framework/unmanaged-api/hosting/index.md) enables message pumping, so an interrupted state is not needed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7edce-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7edce-114">Requirements</span></span>  
 <span data-ttu-id="7edce-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7edce-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7edce-116">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7edce-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7edce-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7edce-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7edce-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7edce-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7edce-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7edce-119">See also</span></span>

- [<span data-ttu-id="7edce-120">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="7edce-120">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
