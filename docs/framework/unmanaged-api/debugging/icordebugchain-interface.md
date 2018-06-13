---
title: Icordebugchain Interface1
ms.date: 03/30/2017
api_name:
- ICorDebugChain
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain
helpviewer_keywords:
- ICorDebugChain interface [.NET Framework debugging]
ms.assetid: f671f519-1cb3-4ae5-b9f1-abc5e783459f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 32889a8e8867fc42b48413463095dda423f26b85
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33409847"
---
# <a name="icordebugchain-interface1"></a><span data-ttu-id="938a7-102">Icordebugchain Interface1</span><span class="sxs-lookup"><span data-stu-id="938a7-102">ICorDebugChain Interface1</span></span>
<span data-ttu-id="938a7-103">Fiziksel veya mantıksal bir çağrı yığınının bir kesimini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="938a7-103">Represents a segment of a physical or logical call stack.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="938a7-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="938a7-104">Methods</span></span>  
  
|<span data-ttu-id="938a7-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="938a7-105">Method</span></span>|<span data-ttu-id="938a7-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="938a7-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="938a7-107">EnumerateFrames Yöntemi</span><span class="sxs-lookup"><span data-stu-id="938a7-107">EnumerateFrames Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-enumerateframes-method.md)|<span data-ttu-id="938a7-108">En son çerçeve ile başlayarak zincirde tüm yönetilen yığın çerçeveleri içeren bir numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="938a7-108">Gets an enumerator that contains all the managed stack frames in the chain, starting with the most recent frame.</span></span>|  
|[<span data-ttu-id="938a7-109">GetActiveFrame Yöntemi</span><span class="sxs-lookup"><span data-stu-id="938a7-109">GetActiveFrame Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getactiveframe-method.md)|<span data-ttu-id="938a7-110">Etkin alır (yani, en son) zinciri çerçevesi.</span><span class="sxs-lookup"><span data-stu-id="938a7-110">Gets the active (that is, most recent) frame on the chain.</span></span>|  
|[<span data-ttu-id="938a7-111">GetCallee Yöntemi</span><span class="sxs-lookup"><span data-stu-id="938a7-111">GetCallee Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getcallee-method.md)|<span data-ttu-id="938a7-112">Bu zincir tarafından çağrıldı zinciri alır.</span><span class="sxs-lookup"><span data-stu-id="938a7-112">Gets the chain that was called by this chain.</span></span>|  
|[<span data-ttu-id="938a7-113">GetCaller Yöntemi</span><span class="sxs-lookup"><span data-stu-id="938a7-113">GetCaller Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getcaller-method.md)|<span data-ttu-id="938a7-114">Bu zincir adlı zinciri alır.</span><span class="sxs-lookup"><span data-stu-id="938a7-114">Gets the chain that called this chain.</span></span>|  
|[<span data-ttu-id="938a7-115">GetContext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="938a7-115">GetContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getcontext-method.md)|<span data-ttu-id="938a7-116">Henüz uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="938a7-116">Not implemented.</span></span>|  
|[<span data-ttu-id="938a7-117">GetNext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="938a7-117">GetNext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getnext-method.md)|<span data-ttu-id="938a7-118">Çerçeve sonraki zincirine iş parçacığı alır.</span><span class="sxs-lookup"><span data-stu-id="938a7-118">Gets the next chain of frames for the thread.</span></span>|  
|[<span data-ttu-id="938a7-119">GetPrevious Yöntemi</span><span class="sxs-lookup"><span data-stu-id="938a7-119">GetPrevious Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getprevious-method.md)|<span data-ttu-id="938a7-120">Çerçeve önceki zincirine iş parçacığı alır.</span><span class="sxs-lookup"><span data-stu-id="938a7-120">Gets the previous chain of frames for the thread.</span></span>|  
|[<span data-ttu-id="938a7-121">GetReason Yöntemi</span><span class="sxs-lookup"><span data-stu-id="938a7-121">GetReason Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getreason-method.md)|<span data-ttu-id="938a7-122">Bu arama zincirini genesis nedeni alır.</span><span class="sxs-lookup"><span data-stu-id="938a7-122">Gets the reason for the genesis of this calling chain.</span></span>|  
|[<span data-ttu-id="938a7-123">GetRegisterSet Yöntemi</span><span class="sxs-lookup"><span data-stu-id="938a7-123">GetRegisterSet Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getregisterset-method.md)|<span data-ttu-id="938a7-124">Etkin bir parçası bu zincirinin ayarlamak kayıt alır.</span><span class="sxs-lookup"><span data-stu-id="938a7-124">Gets the register set for the active part of this chain.</span></span>|  
|[<span data-ttu-id="938a7-125">GetStackRange Yöntemi</span><span class="sxs-lookup"><span data-stu-id="938a7-125">GetStackRange Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getstackrange-method.md)|<span data-ttu-id="938a7-126">Yığın kesiminin adres aralığı için bu zincirini alır.</span><span class="sxs-lookup"><span data-stu-id="938a7-126">Gets the address range of the stack segment for this chain.</span></span>|  
|[<span data-ttu-id="938a7-127">GetThread Yöntemi</span><span class="sxs-lookup"><span data-stu-id="938a7-127">GetThread Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getthread-method.md)|<span data-ttu-id="938a7-128">Bu çağrı zinciri fiziksel iş parçacığı parçası alır.</span><span class="sxs-lookup"><span data-stu-id="938a7-128">Gets the physical thread this call chain is part of.</span></span>|  
|[<span data-ttu-id="938a7-129">IsManaged Yöntemi</span><span class="sxs-lookup"><span data-stu-id="938a7-129">IsManaged Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-ismanaged-method.md)|<span data-ttu-id="938a7-130">Yönetilen kod bu zincirini çalışır durumda olup olmadığını belirten bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="938a7-130">Gets a value that indicates whether this chain is running managed code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="938a7-131">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="938a7-131">Remarks</span></span>  
 <span data-ttu-id="938a7-132">Yığın çerçeveleri zincirindeki bitişik yığın alanı kaplar ve aynı iş parçacığı bağlam paylaşın.</span><span class="sxs-lookup"><span data-stu-id="938a7-132">The stack frames in a chain occupy contiguous stack space and share the same thread and context.</span></span> <span data-ttu-id="938a7-133">Bir zincir ya da yönetilen veya yönetilmeyen kod zincirleri temsil edebilir.</span><span class="sxs-lookup"><span data-stu-id="938a7-133">A chain may represent either managed or unmanaged code chains.</span></span> <span data-ttu-id="938a7-134">Boş bir `ICorDebugChain` örneği bir yönetilmeyen kod zinciri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="938a7-134">An empty `ICorDebugChain` instance represents an unmanaged code chain.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="938a7-135">Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="938a7-135">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="938a7-136">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="938a7-136">Requirements</span></span>  
 <span data-ttu-id="938a7-137">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="938a7-137">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="938a7-138">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="938a7-138">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="938a7-139">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="938a7-139">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="938a7-140">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="938a7-140">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="938a7-141">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="938a7-141">See Also</span></span>  
 [<span data-ttu-id="938a7-142">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="938a7-142">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
