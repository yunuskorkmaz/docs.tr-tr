---
title: ICorDebugStaticFieldSymbol Arabirimi
ms.date: 03/30/2017
ms.assetid: c0b93609-631e-4b15-878a-189ede922631
ms.openlocfilehash: b50b9c8435f19e1a77229f01dc85514f5f75c9f5
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791800"
---
# <a name="icordebugstaticfieldsymbol-interface"></a><span data-ttu-id="59b7d-102">ICorDebugStaticFieldSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="59b7d-102">ICorDebugStaticFieldSymbol Interface</span></span>
<span data-ttu-id="59b7d-103">Statik bir alan için hata ayıklama simgesi bilgisini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="59b7d-103">Represents the debug symbol information for a static field.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="59b7d-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="59b7d-104">Methods</span></span>  
  
|<span data-ttu-id="59b7d-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="59b7d-105">Method</span></span>|<span data-ttu-id="59b7d-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="59b7d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="59b7d-107">GetAddress Yöntemi</span><span class="sxs-lookup"><span data-stu-id="59b7d-107">GetAddress Method</span></span>](icordebugstaticfieldsymbol-getaddress-method.md)|<span data-ttu-id="59b7d-108">Statik alanın adresini alır.</span><span class="sxs-lookup"><span data-stu-id="59b7d-108">Gets the address of the static field.</span></span>|  
|[<span data-ttu-id="59b7d-109">GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="59b7d-109">GetName Method</span></span>](icordebugstaticfieldsymbol-getname-method.md)|<span data-ttu-id="59b7d-110">Statik alanın adını alır.</span><span class="sxs-lookup"><span data-stu-id="59b7d-110">Gets the name of the static field.</span></span>|  
|[<span data-ttu-id="59b7d-111">GetSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="59b7d-111">GetSize Method</span></span>](icordebugstaticfieldsymbol-getsize-method.md)|<span data-ttu-id="59b7d-112">Statik alanın bayt cinsinden boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="59b7d-112">Gets the size in bytes of the static field.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="59b7d-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="59b7d-113">Remarks</span></span>  
 <span data-ttu-id="59b7d-114">`ICorDebugStaticFieldSymbol` arabirimi, bir statik alana yönelik hata ayıklama simgesi bilgilerini almak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="59b7d-114">The `ICorDebugStaticFieldSymbol` interface is used to retrieve the debug symbol information for a static field.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="59b7d-115">Bu arabirim yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="59b7d-115">This interface is available with .NET Native only.</span></span> <span data-ttu-id="59b7d-116">Bu arabirimi .NET Native dışında ICorDebug senaryolarında uygularsanız, ortak dil çalışma zamanı bu arabirimi yoksayar.</span><span class="sxs-lookup"><span data-stu-id="59b7d-116">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="59b7d-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="59b7d-117">Requirements</span></span>  
 <span data-ttu-id="59b7d-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="59b7d-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="59b7d-119">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="59b7d-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="59b7d-120">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="59b7d-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="59b7d-121">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="59b7d-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59b7d-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="59b7d-122">See also</span></span>

- [<span data-ttu-id="59b7d-123">ICorDebugInstanceFieldSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="59b7d-123">ICorDebugInstanceFieldSymbol Interface</span></span>](icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="59b7d-124">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="59b7d-124">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="59b7d-125">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="59b7d-125">Debugging</span></span>](index.md)
