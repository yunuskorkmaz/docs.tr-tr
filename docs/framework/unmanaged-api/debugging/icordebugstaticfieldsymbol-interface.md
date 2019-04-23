---
title: ICorDebugStaticFieldSymbol Arabirimi
ms.date: 03/30/2017
ms.assetid: c0b93609-631e-4b15-878a-189ede922631
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 382f3fc9377c25379809badac0bc580c3593cbde
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59103902"
---
# <a name="icordebugstaticfieldsymbol-interface"></a><span data-ttu-id="9aab0-102">ICorDebugStaticFieldSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9aab0-102">ICorDebugStaticFieldSymbol Interface</span></span>
<span data-ttu-id="9aab0-103">Statik bir alan için hata ayıklama bilgilerini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="9aab0-103">Represents the debug symbol information for a static field.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9aab0-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="9aab0-104">Methods</span></span>  
  
|<span data-ttu-id="9aab0-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="9aab0-105">Method</span></span>|<span data-ttu-id="9aab0-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9aab0-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9aab0-107">GetAddress Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9aab0-107">GetAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-getaddress-method.md)|<span data-ttu-id="9aab0-108">Statik alan adresini alır.</span><span class="sxs-lookup"><span data-stu-id="9aab0-108">Gets the address of the static field.</span></span>|  
|[<span data-ttu-id="9aab0-109">GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9aab0-109">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-getname-method.md)|<span data-ttu-id="9aab0-110">Statik alan adını alır.</span><span class="sxs-lookup"><span data-stu-id="9aab0-110">Gets the name of the static field.</span></span>|  
|[<span data-ttu-id="9aab0-111">GetSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9aab0-111">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-getsize-method.md)|<span data-ttu-id="9aab0-112">Boyutu bayt cinsinden statik alanı alır.</span><span class="sxs-lookup"><span data-stu-id="9aab0-112">Gets the size in bytes of the static field.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9aab0-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9aab0-113">Remarks</span></span>  
 <span data-ttu-id="9aab0-114">`ICorDebugStaticFieldSymbol` Arabirimi statik bir alan için hata ayıklama bilgilerini almak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9aab0-114">The `ICorDebugStaticFieldSymbol` interface is used to retrieve the debug symbol information for a static field.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9aab0-115">Bu arabirim yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9aab0-115">This interface is available with .NET Native only.</span></span> <span data-ttu-id="9aab0-116">Bu arabirim .NET Native dışında Icordebug senaryoları için uygularsanız, ortak dil çalışma zamanı bu arabirimi yoksayar.</span><span class="sxs-lookup"><span data-stu-id="9aab0-116">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9aab0-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9aab0-117">Requirements</span></span>  
 <span data-ttu-id="9aab0-118">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9aab0-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9aab0-119">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9aab0-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9aab0-120">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9aab0-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9aab0-121">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9aab0-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9aab0-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9aab0-122">See also</span></span>

- [<span data-ttu-id="9aab0-123">ICorDebugInstanceFieldSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9aab0-123">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="9aab0-124">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="9aab0-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="9aab0-125">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="9aab0-125">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
