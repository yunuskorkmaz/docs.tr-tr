---
description: ': Icordebugstackyürüme arabirimi hakkında daha fazla bilgi'
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
ms.openlocfilehash: 27dcdfc90829a3a28d81ad28dce0cd4d1d674948
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99738097"
---
# <a name="icordebugstackwalk-interface"></a><span data-ttu-id="c20d3-103">ICorDebugStackWalk Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c20d3-103">ICorDebugStackWalk Interface</span></span>

<span data-ttu-id="c20d3-104">İş parçacığının yığınındaki yönetilen yöntemleri veya çerçeveleri almak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="c20d3-104">Provides methods for getting the managed methods, or frames, on a thread’s stack.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c20d3-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="c20d3-105">Methods</span></span>  
  
|<span data-ttu-id="c20d3-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="c20d3-106">Method</span></span>|<span data-ttu-id="c20d3-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c20d3-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c20d3-108">GetContext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c20d3-108">GetContext Method</span></span>](icordebugstackwalk-getcontext-method.md)|<span data-ttu-id="c20d3-109">Nesnedeki geçerli karenin bağlamını döndürür `ICorDebugStackWalk` .</span><span class="sxs-lookup"><span data-stu-id="c20d3-109">Returns the context for the current frame in the `ICorDebugStackWalk` object.</span></span>|  
|[<span data-ttu-id="c20d3-110">SetContext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c20d3-110">SetContext Method</span></span>](icordebugstackwalk-setcontext-method.md)|<span data-ttu-id="c20d3-111">`ICorDebugStackWalk`Nesnenin geçerli bağlamını iş parçacığı için geçerli bir bağlam olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="c20d3-111">Sets the `ICorDebugStackWalk` object’s current context to a valid context for the thread.</span></span>|  
|[<span data-ttu-id="c20d3-112">Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c20d3-112">Next Method</span></span>](icordebugstackwalk-next-method.md)|<span data-ttu-id="c20d3-113">`ICorDebugStackWalk`Nesneyi sonraki çerçeveye kaydırır.</span><span class="sxs-lookup"><span data-stu-id="c20d3-113">Moves the `ICorDebugStackWalk` object to the next frame.</span></span>|  
|[<span data-ttu-id="c20d3-114">GetFrame Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c20d3-114">GetFrame Method</span></span>](icordebugstackwalk-getframe-method.md)|<span data-ttu-id="c20d3-115">Nesnenin geçerli çerçevesini alır `ICorDebugStackWalk` .</span><span class="sxs-lookup"><span data-stu-id="c20d3-115">Gets the current frame in the `ICorDebugStackWalk` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c20d3-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c20d3-116">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c20d3-117">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="c20d3-117">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c20d3-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c20d3-118">Requirements</span></span>  

 <span data-ttu-id="c20d3-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c20d3-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c20d3-120">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c20d3-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c20d3-121">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="c20d3-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c20d3-122">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c20d3-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c20d3-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c20d3-123">See also</span></span>

- [<span data-ttu-id="c20d3-124">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="c20d3-124">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="c20d3-125">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="c20d3-125">Debugging</span></span>](index.md)
