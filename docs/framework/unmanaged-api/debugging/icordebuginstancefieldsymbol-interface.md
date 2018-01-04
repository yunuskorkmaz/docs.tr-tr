---
title: ICorDebugInstanceFieldSymbol arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: a4a8f259-b83a-4425-ae8b-72b067dbc0d9
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0b13df0d70a36e475e87bae3152912e58a9f8443
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebuginstancefieldsymbol-interface"></a><span data-ttu-id="c2305-102">ICorDebugInstanceFieldSymbol arabirimi</span><span class="sxs-lookup"><span data-stu-id="c2305-102">ICorDebugInstanceFieldSymbol Interface</span></span>
<span data-ttu-id="c2305-103">Bir örnek alanındaki hata ayıklama sembol bilgilerini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c2305-103">Represents the debug symbol information for an instance field.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c2305-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="c2305-104">Methods</span></span>  
  
|<span data-ttu-id="c2305-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="c2305-105">Method</span></span>|<span data-ttu-id="c2305-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c2305-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c2305-107">GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c2305-107">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-getname-method.md)|<span data-ttu-id="c2305-108">Örnek alanın adını alır.</span><span class="sxs-lookup"><span data-stu-id="c2305-108">Gets the name of the instance field.</span></span>|  
|[<span data-ttu-id="c2305-109">GetOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c2305-109">GetOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-getoffset-method.md)|<span data-ttu-id="c2305-110">Bu örnek alanı kendi üst sınıfı'bayt uzaklığını alır.</span><span class="sxs-lookup"><span data-stu-id="c2305-110">Gets the offset in bytes of this instance field in its parent class.</span></span>|  
|[<span data-ttu-id="c2305-111">GetSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c2305-111">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-getsize-method.md)|<span data-ttu-id="c2305-112">Örnek alanı bayt cinsinden boyutu alır.</span><span class="sxs-lookup"><span data-stu-id="c2305-112">Gets the size in bytes of the instance field.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c2305-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c2305-113">Remarks</span></span>  
 <span data-ttu-id="c2305-114">`ICorDebugInstanceFieldSymbol` Arabirimi bir örnek alanındaki hata ayıklama sembol bilgilerini almak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c2305-114">The `ICorDebugInstanceFieldSymbol` interface is used to retrieve the debug symbol information for an instance field.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c2305-115">Bu arabirim yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c2305-115">This interface is available with .NET Native only.</span></span> <span data-ttu-id="c2305-116">Bu arabirim .NET yerel dışında Icordebug senaryoları için uygularsanız, ortak dil çalışma zamanı bu arabirim göz ardı eder.</span><span class="sxs-lookup"><span data-stu-id="c2305-116">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c2305-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c2305-117">Requirements</span></span>  
 <span data-ttu-id="c2305-118">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c2305-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2305-119">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c2305-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c2305-120">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c2305-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c2305-121">**.NET framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c2305-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2305-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c2305-122">See Also</span></span>  
 [<span data-ttu-id="c2305-123">ICorDebugStaticFieldSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c2305-123">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)  
 [<span data-ttu-id="c2305-124">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="c2305-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="c2305-125">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="c2305-125">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
