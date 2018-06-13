---
title: ICorDebugVirtualUnwinder Arabirimi
ms.date: 03/30/2017
ms.assetid: a09e9ccc-0b37-43e3-95c1-bc5fa7ee5f42
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bb04ac42b3cc77db3af53c87efb0d1f1f75da928
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33421291"
---
# <a name="icordebugvirtualunwinder-interface"></a><span data-ttu-id="487c6-102">ICorDebugVirtualUnwinder Arabirimi</span><span class="sxs-lookup"><span data-stu-id="487c6-102">ICorDebugVirtualUnwinder Interface</span></span>
<span data-ttu-id="487c6-103">Yığın geriye doğru izleme yardımcı olmak için yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="487c6-103">Provides methods to help in stack unwinding.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="487c6-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="487c6-104">Methods</span></span>  
  
|<span data-ttu-id="487c6-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="487c6-105">Method</span></span>|<span data-ttu-id="487c6-106">Ad</span><span class="sxs-lookup"><span data-stu-id="487c6-106">Name</span></span>|  
|------------|----------|  
|[<span data-ttu-id="487c6-107">GetContext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="487c6-107">GetContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvirtualunwinder-getcontext-method.md)|<span data-ttu-id="487c6-108">Bu unwinder geçerli bağlamını alır.</span><span class="sxs-lookup"><span data-stu-id="487c6-108">Gets the current context of this unwinder.</span></span>|  
|[<span data-ttu-id="487c6-109">Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="487c6-109">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvirtualunwinder-next-method.md)|<span data-ttu-id="487c6-110">Çağıranın içeriği ilerler.</span><span class="sxs-lookup"><span data-stu-id="487c6-110">Advances to the caller's context.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="487c6-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="487c6-111">Remarks</span></span>  
 <span data-ttu-id="487c6-112">Üyeleri `ICorDebugVirtualUnwinder` arabirimi yığını geriye doğru izleme yardımcı olmak için hata ayıklayıcı tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="487c6-112">The members of the `ICorDebugVirtualUnwinder` interface are implemented by the debugger to help in stack unwinding.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="487c6-113">Bu arabirim yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="487c6-113">This interface is available with .NET Native only.</span></span> <span data-ttu-id="487c6-114">Bu arabirim .NET yerel dışında Icordebug senaryoları için uygularsanız, ortak dil çalışma zamanı bu arabirim göz ardı eder.</span><span class="sxs-lookup"><span data-stu-id="487c6-114">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="487c6-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="487c6-115">Requirements</span></span>  
 <span data-ttu-id="487c6-116">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="487c6-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="487c6-117">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="487c6-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="487c6-118">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="487c6-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="487c6-119">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="487c6-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="487c6-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="487c6-120">See Also</span></span>  
 [<span data-ttu-id="487c6-121">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="487c6-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="487c6-122">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="487c6-122">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
