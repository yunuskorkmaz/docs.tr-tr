---
title: ICorDebugStackWalk Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugStackWalk
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStackWalk
helpviewer_keywords:
- ICorDebugStackWalk interface [.NET Framework debugging]
ms.assetid: 16d695e8-975d-431b-8421-e9e6c3e3f476
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e33e9be112a6a10f89b88005496ce2e63dff2d54
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59080690"
---
# <a name="icordebugstackwalk-interface"></a><span data-ttu-id="ecd42-102">ICorDebugStackWalk Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ecd42-102">ICorDebugStackWalk Interface</span></span>
<span data-ttu-id="ecd42-103">İş parçacığının yığınındaki yönetilen yöntemleri veya çerçeveleri almak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="ecd42-103">Provides methods for getting the managed methods, or frames, on a thread’s stack.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ecd42-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="ecd42-104">Methods</span></span>  
  
|<span data-ttu-id="ecd42-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="ecd42-105">Method</span></span>|<span data-ttu-id="ecd42-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ecd42-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ecd42-107">GetContext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ecd42-107">GetContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md)|<span data-ttu-id="ecd42-108">Geçerli kare bağlamını döndürür `ICorDebugStackWalk` nesne.</span><span class="sxs-lookup"><span data-stu-id="ecd42-108">Returns the context for the current frame in the `ICorDebugStackWalk` object.</span></span>|  
|[<span data-ttu-id="ecd42-109">SetContext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ecd42-109">SetContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-setcontext-method.md)|<span data-ttu-id="ecd42-110">Kümeleri `ICorDebugStackWalk` iş parçacığı için geçerli bir bağlamı için geçerli bağlam nesnesi.</span><span class="sxs-lookup"><span data-stu-id="ecd42-110">Sets the `ICorDebugStackWalk` object’s current context to a valid context for the thread.</span></span>|  
|[<span data-ttu-id="ecd42-111">Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ecd42-111">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-next-method.md)|<span data-ttu-id="ecd42-112">Taşır `ICorDebugStackWalk` sonraki kareye nesne.</span><span class="sxs-lookup"><span data-stu-id="ecd42-112">Moves the `ICorDebugStackWalk` object to the next frame.</span></span>|  
|[<span data-ttu-id="ecd42-113">GetFrame Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ecd42-113">GetFrame Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getframe-method.md)|<span data-ttu-id="ecd42-114">Geçerli çerçevenin alır `ICorDebugStackWalk` nesne.</span><span class="sxs-lookup"><span data-stu-id="ecd42-114">Gets the current frame in the `ICorDebugStackWalk` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ecd42-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ecd42-115">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ecd42-116">Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="ecd42-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ecd42-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ecd42-117">Requirements</span></span>  
 <span data-ttu-id="ecd42-118">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ecd42-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ecd42-119">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ecd42-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ecd42-120">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ecd42-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ecd42-121">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ecd42-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecd42-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ecd42-122">See also</span></span>

- [<span data-ttu-id="ecd42-123">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="ecd42-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="ecd42-124">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="ecd42-124">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
