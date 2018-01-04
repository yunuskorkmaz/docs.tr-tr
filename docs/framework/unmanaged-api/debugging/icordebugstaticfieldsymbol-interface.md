---
title: ICorDebugStaticFieldSymbol arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: c0b93609-631e-4b15-878a-189ede922631
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a25e19bf43d852670bc5f4f491fb25707395e04a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugstaticfieldsymbol-interface"></a><span data-ttu-id="2294f-102">ICorDebugStaticFieldSymbol arabirimi</span><span class="sxs-lookup"><span data-stu-id="2294f-102">ICorDebugStaticFieldSymbol Interface</span></span>
<span data-ttu-id="2294f-103">Statik bir alana hata ayıklama sembol bilgilerini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="2294f-103">Represents the debug symbol information for a static field.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2294f-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="2294f-104">Methods</span></span>  
  
|<span data-ttu-id="2294f-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="2294f-105">Method</span></span>|<span data-ttu-id="2294f-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2294f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2294f-107">GetAddress Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2294f-107">GetAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-getaddress-method.md)|<span data-ttu-id="2294f-108">Statik alan adresini alır.</span><span class="sxs-lookup"><span data-stu-id="2294f-108">Gets the address of the static field.</span></span>|  
|[<span data-ttu-id="2294f-109">GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2294f-109">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-getname-method.md)|<span data-ttu-id="2294f-110">Statik alanın adını alır.</span><span class="sxs-lookup"><span data-stu-id="2294f-110">Gets the name of the static field.</span></span>|  
|[<span data-ttu-id="2294f-111">GetSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2294f-111">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-getsize-method.md)|<span data-ttu-id="2294f-112">Statik alanının bayt cinsinden boyutu alır.</span><span class="sxs-lookup"><span data-stu-id="2294f-112">Gets the size in bytes of the static field.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2294f-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2294f-113">Remarks</span></span>  
 <span data-ttu-id="2294f-114">`ICorDebugStaticFieldSymbol` Arabirimi statik bir alan için hata ayıklama simgesi bilgi almak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2294f-114">The `ICorDebugStaticFieldSymbol` interface is used to retrieve the debug symbol information for a static field.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2294f-115">Bu arabirim yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="2294f-115">This interface is available with .NET Native only.</span></span> <span data-ttu-id="2294f-116">Bu arabirim .NET yerel dışında Icordebug senaryoları için uygularsanız, ortak dil çalışma zamanı bu arabirim göz ardı eder.</span><span class="sxs-lookup"><span data-stu-id="2294f-116">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2294f-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2294f-117">Requirements</span></span>  
 <span data-ttu-id="2294f-118">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2294f-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2294f-119">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2294f-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2294f-120">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2294f-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2294f-121">**.NET framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2294f-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2294f-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2294f-122">See Also</span></span>  
 [<span data-ttu-id="2294f-123">ICorDebugInstanceFieldSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2294f-123">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)  
 [<span data-ttu-id="2294f-124">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="2294f-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="2294f-125">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="2294f-125">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
