---
title: ICorDebugVirtualUnwinder Arabirimi
ms.date: 03/30/2017
ms.assetid: a09e9ccc-0b37-43e3-95c1-bc5fa7ee5f42
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9db6b83e2feedd761b95dec455213051e37366e1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54684151"
---
# <a name="icordebugvirtualunwinder-interface"></a><span data-ttu-id="e7759-102">ICorDebugVirtualUnwinder Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e7759-102">ICorDebugVirtualUnwinder Interface</span></span>
<span data-ttu-id="e7759-103">Yığın geriye doğru izleme yardımcı olmak için yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="e7759-103">Provides methods to help in stack unwinding.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e7759-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="e7759-104">Methods</span></span>  
  
|<span data-ttu-id="e7759-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="e7759-105">Method</span></span>|<span data-ttu-id="e7759-106">Ad</span><span class="sxs-lookup"><span data-stu-id="e7759-106">Name</span></span>|  
|------------|----------|  
|[<span data-ttu-id="e7759-107">GetContext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e7759-107">GetContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvirtualunwinder-getcontext-method.md)|<span data-ttu-id="e7759-108">Bu unwinder geçerli bağlamı alır.</span><span class="sxs-lookup"><span data-stu-id="e7759-108">Gets the current context of this unwinder.</span></span>|  
|[<span data-ttu-id="e7759-109">Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e7759-109">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvirtualunwinder-next-method.md)|<span data-ttu-id="e7759-110">Arayanın bağlam ilerler.</span><span class="sxs-lookup"><span data-stu-id="e7759-110">Advances to the caller's context.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e7759-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e7759-111">Remarks</span></span>  
 <span data-ttu-id="e7759-112">Üyeleri `ICorDebugVirtualUnwinder` arabirimi yığın geriye doğru izleme yardımcı olmak için hata ayıklayıcı tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="e7759-112">The members of the `ICorDebugVirtualUnwinder` interface are implemented by the debugger to help in stack unwinding.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e7759-113">Bu arabirim yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e7759-113">This interface is available with .NET Native only.</span></span> <span data-ttu-id="e7759-114">Bu arabirim .NET Native dışında Icordebug senaryoları için uygularsanız, ortak dil çalışma zamanı bu arabirimi yoksayar.</span><span class="sxs-lookup"><span data-stu-id="e7759-114">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e7759-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e7759-115">Requirements</span></span>  
 <span data-ttu-id="e7759-116">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e7759-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7759-117">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e7759-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e7759-118">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e7759-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e7759-119">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e7759-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7759-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e7759-120">See also</span></span>
- [<span data-ttu-id="e7759-121">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="e7759-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="e7759-122">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="e7759-122">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
