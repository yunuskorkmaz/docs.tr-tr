---
title: ICorDebugChain Arabirimi
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
ms.openlocfilehash: 01dded47fca26df11781153eb45693057a25ad01
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59220714"
---
# <a name="icordebugchain-interface"></a><span data-ttu-id="e602f-102">ICorDebugChain Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e602f-102">ICorDebugChain Interface</span></span>

<span data-ttu-id="e602f-103">Fiziksel veya mantıksal bir çağrı yığınının bir kesimini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e602f-103">Represents a segment of a physical or logical call stack.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e602f-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="e602f-104">Methods</span></span>  
  
|<span data-ttu-id="e602f-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="e602f-105">Method</span></span>|<span data-ttu-id="e602f-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e602f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e602f-107">EnumerateFrames Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e602f-107">EnumerateFrames Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-enumerateframes-method.md)|<span data-ttu-id="e602f-108">En son çerçeve ile başlayan zincirindeki tüm yönetilen yığın çerçevesi içeren bir numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="e602f-108">Gets an enumerator that contains all the managed stack frames in the chain, starting with the most recent frame.</span></span>|  
|[<span data-ttu-id="e602f-109">GetActiveFrame Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e602f-109">GetActiveFrame Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getactiveframe-method.md)|<span data-ttu-id="e602f-110">Etkin alır (yani, en son) zincirindeki çerçeve.</span><span class="sxs-lookup"><span data-stu-id="e602f-110">Gets the active (that is, most recent) frame on the chain.</span></span>|  
|[<span data-ttu-id="e602f-111">GetCallee Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e602f-111">GetCallee Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getcallee-method.md)|<span data-ttu-id="e602f-112">Bu zincir tarafından çağrıldı zinciri alır.</span><span class="sxs-lookup"><span data-stu-id="e602f-112">Gets the chain that was called by this chain.</span></span>|  
|[<span data-ttu-id="e602f-113">GetCaller Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e602f-113">GetCaller Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getcaller-method.md)|<span data-ttu-id="e602f-114">Bu zincir denir zinciri alır.</span><span class="sxs-lookup"><span data-stu-id="e602f-114">Gets the chain that called this chain.</span></span>|  
|[<span data-ttu-id="e602f-115">GetContext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e602f-115">GetContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getcontext-method.md)|<span data-ttu-id="e602f-116">Henüz uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="e602f-116">Not implemented.</span></span>|  
|[<span data-ttu-id="e602f-117">GetNext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e602f-117">GetNext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getnext-method.md)|<span data-ttu-id="e602f-118">Çerçeve sonraki zincirini iş parçacığı alır.</span><span class="sxs-lookup"><span data-stu-id="e602f-118">Gets the next chain of frames for the thread.</span></span>|  
|[<span data-ttu-id="e602f-119">GetPrevious Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e602f-119">GetPrevious Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getprevious-method.md)|<span data-ttu-id="e602f-120">Çerçeve önceki zincirini iş parçacığı alır.</span><span class="sxs-lookup"><span data-stu-id="e602f-120">Gets the previous chain of frames for the thread.</span></span>|  
|[<span data-ttu-id="e602f-121">GetReason Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e602f-121">GetReason Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getreason-method.md)|<span data-ttu-id="e602f-122">Bu çağrı zincirinin genesis nedenini alır.</span><span class="sxs-lookup"><span data-stu-id="e602f-122">Gets the reason for the genesis of this calling chain.</span></span>|  
|[<span data-ttu-id="e602f-123">GetRegisterSet Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e602f-123">GetRegisterSet Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getregisterset-method.md)|<span data-ttu-id="e602f-124">Bu zincir etkin parçası için kaydı alır.</span><span class="sxs-lookup"><span data-stu-id="e602f-124">Gets the register set for the active part of this chain.</span></span>|  
|[<span data-ttu-id="e602f-125">GetStackRange Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e602f-125">GetStackRange Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getstackrange-method.md)|<span data-ttu-id="e602f-126">Yığın kesiminin adres aralığı için bu zincir alır.</span><span class="sxs-lookup"><span data-stu-id="e602f-126">Gets the address range of the stack segment for this chain.</span></span>|  
|[<span data-ttu-id="e602f-127">GetThread Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e602f-127">GetThread Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getthread-method.md)|<span data-ttu-id="e602f-128">Bu çağrı zinciri fiziksel iş parçacığı parçası alır.</span><span class="sxs-lookup"><span data-stu-id="e602f-128">Gets the physical thread this call chain is part of.</span></span>|  
|[<span data-ttu-id="e602f-129">IsManaged Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e602f-129">IsManaged Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-ismanaged-method.md)|<span data-ttu-id="e602f-130">Bu zincir yönetilen kod çalışır durumda olup olmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="e602f-130">Gets a value that indicates whether this chain is running managed code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e602f-131">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e602f-131">Remarks</span></span>  
 <span data-ttu-id="e602f-132">Yığın çerçevelerini zincirindeki, bitişik yığın alanı kaplayan ve aynı iş parçacığı ve içerik paylaşın.</span><span class="sxs-lookup"><span data-stu-id="e602f-132">The stack frames in a chain occupy contiguous stack space and share the same thread and context.</span></span> <span data-ttu-id="e602f-133">Zinciri ya da yönetilen veya yönetilmeyen koda zincirleri temsil edebilir.</span><span class="sxs-lookup"><span data-stu-id="e602f-133">A chain may represent either managed or unmanaged code chains.</span></span> <span data-ttu-id="e602f-134">Boş bir `ICorDebugChain` örneği bir yönetilmeyen kod zincirini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e602f-134">An empty `ICorDebugChain` instance represents an unmanaged code chain.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e602f-135">Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="e602f-135">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e602f-136">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e602f-136">Requirements</span></span>  
 <span data-ttu-id="e602f-137">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e602f-137">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e602f-138">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e602f-138">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e602f-139">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e602f-139">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e602f-140">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e602f-140">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e602f-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e602f-141">See also</span></span>

- [<span data-ttu-id="e602f-142">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="e602f-142">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
