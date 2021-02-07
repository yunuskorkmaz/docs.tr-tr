---
description: 'Bu konuda daha fazla bilgi edinin: ıcorıınfo Gruntimeunwindadbleframe arabirimi'
title: ICorDebugRuntimeUnwindableFrame Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugUnwindableFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugUnwindableFrame
helpviewer_keywords:
- ICorDebugUnwindableFrame interface [.NET Framework debugging]
ms.assetid: cd6a3982-6ed3-4909-808d-a66055e813e0
topic_type:
- apiref
ms.openlocfilehash: e83ede8265a400b30f2202115bf47aed6ea43e5e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99717816"
---
# <a name="icordebugruntimeunwindableframe-interface"></a><span data-ttu-id="69e76-103">ICorDebugRuntimeUnwindableFrame Arabirimi</span><span class="sxs-lookup"><span data-stu-id="69e76-103">ICorDebugRuntimeUnwindableFrame Interface</span></span>

<span data-ttu-id="69e76-104">Çerçeveyi geriye doğru izlemek için ortak dil çalışma zamanı (CLR) gerektiren yönetilmeyen yöntemler için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="69e76-104">Provides support for unmanaged methods that require the common language runtime (CLR) to unwind a frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="69e76-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="69e76-105">Remarks</span></span>  

 <span data-ttu-id="69e76-106">`ICorDebugRuntimeUnwindableFrame` , ICorDebugFrame arabiriminin özelleşmiş bir sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="69e76-106">`ICorDebugRuntimeUnwindableFrame` is a specialized version of the ICorDebugFrame interface.</span></span> <span data-ttu-id="69e76-107">Çalışma zamanının geçerli yığında bir çerçeveyi geriye doğru bir şekilde aşağı doğru bir şekilde geri kopyasını gerektiren yönetilmeyen yöntemler tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="69e76-107">It is used by unmanaged methods that require the runtime to unwind a frame on the current stack.</span></span> <span data-ttu-id="69e76-108">Mevcut geri sarma kuralları, JıT derlenmiş kod kullanmadığından çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="69e76-108">Existing unwinding conventions do not work, because they do not use JIT-compiled code.</span></span> <span data-ttu-id="69e76-109">Hata ayıklayıcı beklenmeyen bir çerçeve gördüğünde, geri dönmek için [ıcordebugstackizlenecek:: Next](icordebugstackwalk-next-method.md) metodunu kullanmalıdır, ancak İnceleme kendisini gerçekleştirmelidir.</span><span class="sxs-lookup"><span data-stu-id="69e76-109">When the debugger sees an unwindable frame, it should use the [ICorDebugStackWalk::Next](icordebugstackwalk-next-method.md) method to unwind it, but it should perform inspection itself.</span></span> <span data-ttu-id="69e76-110">Hata ayıklayıcı bir aldığında `ICorDebugRuntimeUnwindableFrame` , çerçeve bağlamını almak Için [ıcordebugstackyürüme:: GetContext](icordebugstackwalk-getcontext-method.md) metodunu çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="69e76-110">When the debugger receives an `ICorDebugRuntimeUnwindableFrame`, it can call the [ICorDebugStackWalk::GetContext](icordebugstackwalk-getcontext-method.md) method to retrieve the context of the frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="69e76-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="69e76-111">Requirements</span></span>  

 <span data-ttu-id="69e76-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="69e76-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="69e76-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="69e76-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="69e76-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="69e76-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="69e76-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="69e76-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69e76-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="69e76-116">See also</span></span>

- [<span data-ttu-id="69e76-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="69e76-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="69e76-118">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="69e76-118">Debugging</span></span>](index.md)
