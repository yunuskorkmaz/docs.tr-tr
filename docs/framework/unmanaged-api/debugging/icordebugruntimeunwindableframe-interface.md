---
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
ms.openlocfilehash: 6619b8888588341f23a93b83865cd2e75cc9b3db
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95712020"
---
# <a name="icordebugruntimeunwindableframe-interface"></a><span data-ttu-id="5f84d-102">ICorDebugRuntimeUnwindableFrame Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5f84d-102">ICorDebugRuntimeUnwindableFrame Interface</span></span>

<span data-ttu-id="5f84d-103">Çerçeveyi geriye doğru izlemek için ortak dil çalışma zamanı (CLR) gerektiren yönetilmeyen yöntemler için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="5f84d-103">Provides support for unmanaged methods that require the common language runtime (CLR) to unwind a frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5f84d-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5f84d-104">Remarks</span></span>  

 <span data-ttu-id="5f84d-105">`ICorDebugRuntimeUnwindableFrame` , ICorDebugFrame arabiriminin özelleşmiş bir sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="5f84d-105">`ICorDebugRuntimeUnwindableFrame` is a specialized version of the ICorDebugFrame interface.</span></span> <span data-ttu-id="5f84d-106">Çalışma zamanının geçerli yığında bir çerçeveyi geriye doğru bir şekilde aşağı doğru bir şekilde geri kopyasını gerektiren yönetilmeyen yöntemler tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5f84d-106">It is used by unmanaged methods that require the runtime to unwind a frame on the current stack.</span></span> <span data-ttu-id="5f84d-107">Mevcut geri sarma kuralları, JıT derlenmiş kod kullanmadığından çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="5f84d-107">Existing unwinding conventions do not work, because they do not use JIT-compiled code.</span></span> <span data-ttu-id="5f84d-108">Hata ayıklayıcı beklenmeyen bir çerçeve gördüğünde, geri dönmek için [ıcordebugstackizlenecek:: Next](icordebugstackwalk-next-method.md) metodunu kullanmalıdır, ancak İnceleme kendisini gerçekleştirmelidir.</span><span class="sxs-lookup"><span data-stu-id="5f84d-108">When the debugger sees an unwindable frame, it should use the [ICorDebugStackWalk::Next](icordebugstackwalk-next-method.md) method to unwind it, but it should perform inspection itself.</span></span> <span data-ttu-id="5f84d-109">Hata ayıklayıcı bir aldığında `ICorDebugRuntimeUnwindableFrame` , çerçeve bağlamını almak Için [ıcordebugstackyürüme:: GetContext](icordebugstackwalk-getcontext-method.md) metodunu çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="5f84d-109">When the debugger receives an `ICorDebugRuntimeUnwindableFrame`, it can call the [ICorDebugStackWalk::GetContext](icordebugstackwalk-getcontext-method.md) method to retrieve the context of the frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5f84d-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5f84d-110">Requirements</span></span>  

 <span data-ttu-id="5f84d-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5f84d-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5f84d-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="5f84d-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5f84d-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="5f84d-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5f84d-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5f84d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f84d-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5f84d-115">See also</span></span>

- [<span data-ttu-id="5f84d-116">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="5f84d-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="5f84d-117">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="5f84d-117">Debugging</span></span>](index.md)
