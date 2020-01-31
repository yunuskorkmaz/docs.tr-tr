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
ms.openlocfilehash: a6283d699263dc9b79e457010f31923f77443129
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791887"
---
# <a name="icordebugstackwalk-interface"></a><span data-ttu-id="eb33a-102">ICorDebugStackWalk Arabirimi</span><span class="sxs-lookup"><span data-stu-id="eb33a-102">ICorDebugStackWalk Interface</span></span>
<span data-ttu-id="eb33a-103">İş parçacığının yığınındaki yönetilen yöntemleri veya çerçeveleri almak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="eb33a-103">Provides methods for getting the managed methods, or frames, on a thread’s stack.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="eb33a-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="eb33a-104">Methods</span></span>  
  
|<span data-ttu-id="eb33a-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="eb33a-105">Method</span></span>|<span data-ttu-id="eb33a-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="eb33a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="eb33a-107">GetContext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="eb33a-107">GetContext Method</span></span>](icordebugstackwalk-getcontext-method.md)|<span data-ttu-id="eb33a-108">`ICorDebugStackWalk` nesnesindeki geçerli karenin bağlamını döndürür.</span><span class="sxs-lookup"><span data-stu-id="eb33a-108">Returns the context for the current frame in the `ICorDebugStackWalk` object.</span></span>|  
|[<span data-ttu-id="eb33a-109">SetContext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="eb33a-109">SetContext Method</span></span>](icordebugstackwalk-setcontext-method.md)|<span data-ttu-id="eb33a-110">`ICorDebugStackWalk` nesnenin geçerli bağlamını iş parçacığı için geçerli bir bağlam olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="eb33a-110">Sets the `ICorDebugStackWalk` object’s current context to a valid context for the thread.</span></span>|  
|[<span data-ttu-id="eb33a-111">Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="eb33a-111">Next Method</span></span>](icordebugstackwalk-next-method.md)|<span data-ttu-id="eb33a-112">`ICorDebugStackWalk` nesnesini sonraki çerçeveye kaydırır.</span><span class="sxs-lookup"><span data-stu-id="eb33a-112">Moves the `ICorDebugStackWalk` object to the next frame.</span></span>|  
|[<span data-ttu-id="eb33a-113">GetFrame Yöntemi</span><span class="sxs-lookup"><span data-stu-id="eb33a-113">GetFrame Method</span></span>](icordebugstackwalk-getframe-method.md)|<span data-ttu-id="eb33a-114">`ICorDebugStackWalk` nesnesindeki geçerli çerçeveyi alır.</span><span class="sxs-lookup"><span data-stu-id="eb33a-114">Gets the current frame in the `ICorDebugStackWalk` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eb33a-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="eb33a-115">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="eb33a-116">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="eb33a-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb33a-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="eb33a-117">Requirements</span></span>  
 <span data-ttu-id="eb33a-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eb33a-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb33a-119">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="eb33a-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="eb33a-120">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="eb33a-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eb33a-121">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb33a-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb33a-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eb33a-122">See also</span></span>

- [<span data-ttu-id="eb33a-123">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="eb33a-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="eb33a-124">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="eb33a-124">Debugging</span></span>](index.md)
