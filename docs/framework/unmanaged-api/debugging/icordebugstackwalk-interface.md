---
title: ICorDebugStackWalk Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugStackWalk
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugStackWalk
helpviewer_keywords: ICorDebugStackWalk interface [.NET Framework debugging]
ms.assetid: 16d695e8-975d-431b-8421-e9e6c3e3f476
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 018ed69e52efd21ca25029284c70f1c8493d877f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugstackwalk-interface"></a><span data-ttu-id="3fb9d-102">ICorDebugStackWalk Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3fb9d-102">ICorDebugStackWalk Interface</span></span>
<span data-ttu-id="3fb9d-103">İş parçacığının yığınındaki yönetilen yöntemleri veya çerçeveleri almak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="3fb9d-103">Provides methods for getting the managed methods, or frames, on a thread’s stack.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3fb9d-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="3fb9d-104">Methods</span></span>  
  
|<span data-ttu-id="3fb9d-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="3fb9d-105">Method</span></span>|<span data-ttu-id="3fb9d-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3fb9d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3fb9d-107">GetContext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3fb9d-107">GetContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md)|<span data-ttu-id="3fb9d-108">Geçerli kare bağlamının döndürür `ICorDebugStackWalk` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="3fb9d-108">Returns the context for the current frame in the `ICorDebugStackWalk` object.</span></span>|  
|[<span data-ttu-id="3fb9d-109">SetContext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3fb9d-109">SetContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-setcontext-method.md)|<span data-ttu-id="3fb9d-110">Ayarlar `ICorDebugStackWalk` nesnenin iş parçacığı için geçerli bir bağlam için geçerli bağlam.</span><span class="sxs-lookup"><span data-stu-id="3fb9d-110">Sets the `ICorDebugStackWalk` object’s current context to a valid context for the thread.</span></span>|  
|[<span data-ttu-id="3fb9d-111">Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3fb9d-111">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-next-method.md)|<span data-ttu-id="3fb9d-112">Taşır `ICorDebugStackWalk` sonraki çerçeveye nesne.</span><span class="sxs-lookup"><span data-stu-id="3fb9d-112">Moves the `ICorDebugStackWalk` object to the next frame.</span></span>|  
|[<span data-ttu-id="3fb9d-113">GetFrame Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3fb9d-113">GetFrame Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getframe-method.md)|<span data-ttu-id="3fb9d-114">Geçerli çerçeve alır `ICorDebugStackWalk` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="3fb9d-114">Gets the current frame in the `ICorDebugStackWalk` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3fb9d-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3fb9d-115">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3fb9d-116">Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="3fb9d-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3fb9d-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3fb9d-117">Requirements</span></span>  
 <span data-ttu-id="3fb9d-118">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3fb9d-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3fb9d-119">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3fb9d-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3fb9d-120">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3fb9d-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3fb9d-121">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3fb9d-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fb9d-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3fb9d-122">See Also</span></span>  
 [<span data-ttu-id="3fb9d-123">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="3fb9d-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="3fb9d-124">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="3fb9d-124">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
