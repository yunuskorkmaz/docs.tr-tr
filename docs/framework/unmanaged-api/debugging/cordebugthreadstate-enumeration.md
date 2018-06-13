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
ms.openlocfilehash: ba8bca6d14308284c869b923853f7e27e045bca5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33402945"
---
# <a name="cordebugthreadstate-enumeration"></a><span data-ttu-id="2661a-102">CorDebugThreadState Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="2661a-102">CorDebugThreadState Enumeration</span></span>
<span data-ttu-id="2661a-103">Hata ayıklama için bir iş parçacığı durumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="2661a-103">Specifies the state of a thread for debugging.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2661a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2661a-104">Syntax</span></span>  
  
```  
typedef enum CorDebugThreadState {  
    THREAD_RUN,  
    THREAD_SUSPEND  
} CorDebugThreadState;  
```  
  
## <a name="members"></a><span data-ttu-id="2661a-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="2661a-105">Members</span></span>  
  
|<span data-ttu-id="2661a-106">Üye</span><span class="sxs-lookup"><span data-stu-id="2661a-106">Member</span></span>|<span data-ttu-id="2661a-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2661a-107">Description</span></span>|  
|------------|-----------------|  
|`THREAD_RUN`|<span data-ttu-id="2661a-108">Hata ayıklama olayı oluşmadığı sürece ücretsiz olarak, iş parçacığı çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="2661a-108">The thread runs freely, unless a debug event occurs.</span></span>|  
|`THREAD_SUSPEND`|<span data-ttu-id="2661a-109">İş parçacığı çalıştırılamıyor.</span><span class="sxs-lookup"><span data-stu-id="2661a-109">The thread cannot run.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2661a-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2661a-110">Remarks</span></span>  
 <span data-ttu-id="2661a-111">Hata ayıklayıcı kullanan `CorDebugThreadState` bir iş parçacığının yürütme denetlemek için numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="2661a-111">The debugger uses the `CorDebugThreadState` enumeration to control a thread's execution.</span></span> <span data-ttu-id="2661a-112">Bir iş parçacığı durumu kullanarak ayarlayabilirsiniz [Icordebugthread::setdebugstate](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-setdebugstate-method.md) veya [Icordebugcontroller::setallthreadsdebugstate](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-setallthreadsdebugstate-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="2661a-112">The state of a thread can be set by using the [ICorDebugThread::SetDebugState](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-setdebugstate-method.md) or [ICorDebugController::SetAllThreadsDebugState](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-setallthreadsdebugstate-method.md) method.</span></span>  
  
 <span data-ttu-id="2661a-113">Sağlanan bir geri çağırma [API barındırma](../../../../docs/framework/unmanaged-api/hosting/index.md) kesintiye uğramış bir durum gerekli olmadığı için ileti Pompalama, sağlar.</span><span class="sxs-lookup"><span data-stu-id="2661a-113">A callback provided to the [hosting API](../../../../docs/framework/unmanaged-api/hosting/index.md) enables message pumping, so an interrupted state is not needed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2661a-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2661a-114">Requirements</span></span>  
 <span data-ttu-id="2661a-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2661a-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2661a-116">**Başlık:** CorDebug.idl, CorDegug.h</span><span class="sxs-lookup"><span data-stu-id="2661a-116">**Header:** CorDebug.idl, CorDegug.h</span></span>  
  
 <span data-ttu-id="2661a-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2661a-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2661a-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2661a-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2661a-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2661a-119">See Also</span></span>  
 [<span data-ttu-id="2661a-120">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="2661a-120">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
