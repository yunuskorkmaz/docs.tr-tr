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
ms.openlocfilehash: 0c8a4421b716614081368755388bd2ab8d8fe22e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugstackwalk-interface"></a><span data-ttu-id="b9489-102">ICorDebugStackWalk Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b9489-102">ICorDebugStackWalk Interface</span></span>
<span data-ttu-id="b9489-103">İş parçacığının yığınındaki yönetilen yöntemleri veya çerçeveleri almak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="b9489-103">Provides methods for getting the managed methods, or frames, on a thread’s stack.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b9489-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="b9489-104">Methods</span></span>  
  
|<span data-ttu-id="b9489-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="b9489-105">Method</span></span>|<span data-ttu-id="b9489-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b9489-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b9489-107">GetContext yöntemi</span><span class="sxs-lookup"><span data-stu-id="b9489-107">GetContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md)|<span data-ttu-id="b9489-108">Geçerli kare bağlamının döndürür `ICorDebugStackWalk` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="b9489-108">Returns the context for the current frame in the `ICorDebugStackWalk` object.</span></span>|  
|[<span data-ttu-id="b9489-109">SetContext yöntemi</span><span class="sxs-lookup"><span data-stu-id="b9489-109">SetContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-setcontext-method.md)|<span data-ttu-id="b9489-110">Ayarlar `ICorDebugStackWalk` nesnenin iş parçacığı için geçerli bir bağlam için geçerli bağlam.</span><span class="sxs-lookup"><span data-stu-id="b9489-110">Sets the `ICorDebugStackWalk` object’s current context to a valid context for the thread.</span></span>|  
|[<span data-ttu-id="b9489-111">Next yöntemi</span><span class="sxs-lookup"><span data-stu-id="b9489-111">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-next-method.md)|<span data-ttu-id="b9489-112">Taşır `ICorDebugStackWalk` sonraki çerçeveye nesne.</span><span class="sxs-lookup"><span data-stu-id="b9489-112">Moves the `ICorDebugStackWalk` object to the next frame.</span></span>|  
|[<span data-ttu-id="b9489-113">GetFrame yöntemi</span><span class="sxs-lookup"><span data-stu-id="b9489-113">GetFrame Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getframe-method.md)|<span data-ttu-id="b9489-114">Geçerli çerçeve alır `ICorDebugStackWalk` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="b9489-114">Gets the current frame in the `ICorDebugStackWalk` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b9489-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b9489-115">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b9489-116">Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="b9489-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b9489-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b9489-117">Requirements</span></span>  
 <span data-ttu-id="b9489-118">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b9489-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9489-119">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b9489-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b9489-120">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b9489-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b9489-121">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b9489-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9489-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b9489-122">See Also</span></span>  
 [<span data-ttu-id="b9489-123">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="b9489-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="b9489-124">Hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="b9489-124">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
