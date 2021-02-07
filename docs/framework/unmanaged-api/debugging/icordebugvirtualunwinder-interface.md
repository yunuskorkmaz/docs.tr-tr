---
description: 'Daha fazla bilgi edinin: ICorDebugVirtualUnwinder Interface'
title: ICorDebugVirtualUnwinder Arabirimi
ms.date: 03/30/2017
ms.assetid: a09e9ccc-0b37-43e3-95c1-bc5fa7ee5f42
ms.openlocfilehash: e941ace2e7f72c9f7956c03bae19f9b92094b338
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99738084"
---
# <a name="icordebugvirtualunwinder-interface"></a><span data-ttu-id="6354c-103">ICorDebugVirtualUnwinder Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6354c-103">ICorDebugVirtualUnwinder Interface</span></span>

<span data-ttu-id="6354c-104">Yığın geri sarma konusunda yardımcı olmak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="6354c-104">Provides methods to help in stack unwinding.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6354c-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="6354c-105">Methods</span></span>  
  
|<span data-ttu-id="6354c-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="6354c-106">Method</span></span>|<span data-ttu-id="6354c-107">Name</span><span class="sxs-lookup"><span data-stu-id="6354c-107">Name</span></span>|  
|------------|----------|  
|[<span data-ttu-id="6354c-108">GetContext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6354c-108">GetContext Method</span></span>](icordebugvirtualunwinder-getcontext-method.md)|<span data-ttu-id="6354c-109">Bu unwinder 'in geçerli bağlamını alır.</span><span class="sxs-lookup"><span data-stu-id="6354c-109">Gets the current context of this unwinder.</span></span>|  
|[<span data-ttu-id="6354c-110">Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6354c-110">Next Method</span></span>](icordebugvirtualunwinder-next-method.md)|<span data-ttu-id="6354c-111">Çağıranın bağlamına ilerletir.</span><span class="sxs-lookup"><span data-stu-id="6354c-111">Advances to the caller's context.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6354c-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6354c-112">Remarks</span></span>  

 <span data-ttu-id="6354c-113">Arabirim üyeleri, `ICorDebugVirtualUnwinder` yığın geri sarma konusunda yardımcı olmak için hata ayıklayıcı tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="6354c-113">The members of the `ICorDebugVirtualUnwinder` interface are implemented by the debugger to help in stack unwinding.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6354c-114">Bu arabirim yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6354c-114">This interface is available with .NET Native only.</span></span> <span data-ttu-id="6354c-115">Bu arabirimi .NET Native dışında ICorDebug senaryolarında uygularsanız, ortak dil çalışma zamanı bu arabirimi yoksayar.</span><span class="sxs-lookup"><span data-stu-id="6354c-115">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6354c-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6354c-116">Requirements</span></span>  

 <span data-ttu-id="6354c-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6354c-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6354c-118">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6354c-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6354c-119">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="6354c-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6354c-120">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6354c-120">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6354c-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6354c-121">See also</span></span>

- [<span data-ttu-id="6354c-122">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="6354c-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="6354c-123">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="6354c-123">Debugging</span></span>](index.md)
