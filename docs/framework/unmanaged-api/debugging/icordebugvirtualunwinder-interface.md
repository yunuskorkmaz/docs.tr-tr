---
title: ICorDebugVirtualUnwinder Arabirimi
ms.date: 03/30/2017
ms.assetid: a09e9ccc-0b37-43e3-95c1-bc5fa7ee5f42
ms.openlocfilehash: 59ecf3da4b44af7b04dec26fbc3ea182c185d04a
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396449"
---
# <a name="icordebugvirtualunwinder-interface"></a><span data-ttu-id="dd0ee-102">ICorDebugVirtualUnwinder Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dd0ee-102">ICorDebugVirtualUnwinder Interface</span></span>
<span data-ttu-id="dd0ee-103">Yığın geri sarma konusunda yardımcı olmak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="dd0ee-103">Provides methods to help in stack unwinding.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="dd0ee-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="dd0ee-104">Methods</span></span>  
  
|<span data-ttu-id="dd0ee-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="dd0ee-105">Method</span></span>|<span data-ttu-id="dd0ee-106">Name</span><span class="sxs-lookup"><span data-stu-id="dd0ee-106">Name</span></span>|  
|------------|----------|  
|[<span data-ttu-id="dd0ee-107">GetContext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dd0ee-107">GetContext Method</span></span>](icordebugvirtualunwinder-getcontext-method.md)|<span data-ttu-id="dd0ee-108">Bu unwinder 'in geçerli bağlamını alır.</span><span class="sxs-lookup"><span data-stu-id="dd0ee-108">Gets the current context of this unwinder.</span></span>|  
|[<span data-ttu-id="dd0ee-109">Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dd0ee-109">Next Method</span></span>](icordebugvirtualunwinder-next-method.md)|<span data-ttu-id="dd0ee-110">Çağıranın bağlamına ilerletir.</span><span class="sxs-lookup"><span data-stu-id="dd0ee-110">Advances to the caller's context.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dd0ee-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dd0ee-111">Remarks</span></span>  
 <span data-ttu-id="dd0ee-112">Arabirim üyeleri, `ICorDebugVirtualUnwinder` yığın geri sarma konusunda yardımcı olmak için hata ayıklayıcı tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="dd0ee-112">The members of the `ICorDebugVirtualUnwinder` interface are implemented by the debugger to help in stack unwinding.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="dd0ee-113">Bu arabirim yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="dd0ee-113">This interface is available with .NET Native only.</span></span> <span data-ttu-id="dd0ee-114">Bu arabirimi .NET Native dışında ICorDebug senaryolarında uygularsanız, ortak dil çalışma zamanı bu arabirimi yoksayar.</span><span class="sxs-lookup"><span data-stu-id="dd0ee-114">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dd0ee-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dd0ee-115">Requirements</span></span>  
 <span data-ttu-id="dd0ee-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dd0ee-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dd0ee-117">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="dd0ee-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dd0ee-118">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="dd0ee-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dd0ee-119">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dd0ee-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd0ee-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dd0ee-120">See also</span></span>

- [<span data-ttu-id="dd0ee-121">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="dd0ee-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="dd0ee-122">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="dd0ee-122">Debugging</span></span>](index.md)
