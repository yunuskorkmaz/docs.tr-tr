---
title: ICorDebugStaticFieldSymbol Arabirimi
ms.date: 03/30/2017
ms.assetid: c0b93609-631e-4b15-878a-189ede922631
ms.openlocfilehash: 0891df1fc0528ff485605b2c4168fcff0adff990
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131700"
---
# <a name="icordebugstaticfieldsymbol-interface"></a><span data-ttu-id="1bc90-102">ICorDebugStaticFieldSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1bc90-102">ICorDebugStaticFieldSymbol Interface</span></span>
<span data-ttu-id="1bc90-103">Statik bir alan için hata ayıklama simgesi bilgisini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="1bc90-103">Represents the debug symbol information for a static field.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1bc90-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="1bc90-104">Methods</span></span>  
  
|<span data-ttu-id="1bc90-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="1bc90-105">Method</span></span>|<span data-ttu-id="1bc90-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1bc90-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1bc90-107">GetAddress Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1bc90-107">GetAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-getaddress-method.md)|<span data-ttu-id="1bc90-108">Statik alanın adresini alır.</span><span class="sxs-lookup"><span data-stu-id="1bc90-108">Gets the address of the static field.</span></span>|  
|[<span data-ttu-id="1bc90-109">GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1bc90-109">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-getname-method.md)|<span data-ttu-id="1bc90-110">Statik alanın adını alır.</span><span class="sxs-lookup"><span data-stu-id="1bc90-110">Gets the name of the static field.</span></span>|  
|[<span data-ttu-id="1bc90-111">GetSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1bc90-111">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-getsize-method.md)|<span data-ttu-id="1bc90-112">Statik alanın bayt cinsinden boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="1bc90-112">Gets the size in bytes of the static field.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1bc90-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1bc90-113">Remarks</span></span>  
 <span data-ttu-id="1bc90-114">`ICorDebugStaticFieldSymbol` arabirimi, bir statik alana yönelik hata ayıklama simgesi bilgilerini almak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1bc90-114">The `ICorDebugStaticFieldSymbol` interface is used to retrieve the debug symbol information for a static field.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1bc90-115">Bu arabirim yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1bc90-115">This interface is available with .NET Native only.</span></span> <span data-ttu-id="1bc90-116">Bu arabirimi .NET Native dışında ICorDebug senaryolarında uygularsanız, ortak dil çalışma zamanı bu arabirimi yoksayar.</span><span class="sxs-lookup"><span data-stu-id="1bc90-116">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1bc90-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1bc90-117">Requirements</span></span>  
 <span data-ttu-id="1bc90-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1bc90-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1bc90-119">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="1bc90-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1bc90-120">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="1bc90-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1bc90-121">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1bc90-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bc90-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1bc90-122">See also</span></span>

- [<span data-ttu-id="1bc90-123">ICorDebugInstanceFieldSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1bc90-123">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="1bc90-124">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="1bc90-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="1bc90-125">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="1bc90-125">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
