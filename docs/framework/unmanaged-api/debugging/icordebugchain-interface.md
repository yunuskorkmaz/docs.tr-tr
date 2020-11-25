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
ms.openlocfilehash: a0285970a8a42c078aa663579e1d5998d0d1c037
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724461"
---
# <a name="icordebugchain-interface"></a><span data-ttu-id="12b46-102">ICorDebugChain Arabirimi</span><span class="sxs-lookup"><span data-stu-id="12b46-102">ICorDebugChain Interface</span></span>

<span data-ttu-id="12b46-103">Fiziksel veya mantıksal bir çağrı yığınının bir kesimini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="12b46-103">Represents a segment of a physical or logical call stack.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="12b46-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="12b46-104">Methods</span></span>  
  
|<span data-ttu-id="12b46-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="12b46-105">Method</span></span>|<span data-ttu-id="12b46-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="12b46-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="12b46-107">EnumerateFrames Yöntemi</span><span class="sxs-lookup"><span data-stu-id="12b46-107">EnumerateFrames Method</span></span>](icordebugchain-enumerateframes-method.md)|<span data-ttu-id="12b46-108">En son kareyle başlayarak zincirdeki tüm yönetilen yığın çerçevelerini içeren bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="12b46-108">Gets an enumerator that contains all the managed stack frames in the chain, starting with the most recent frame.</span></span>|  
|[<span data-ttu-id="12b46-109">GetActiveFrame Metodu</span><span class="sxs-lookup"><span data-stu-id="12b46-109">GetActiveFrame Method</span></span>](icordebugchain-getactiveframe-method.md)|<span data-ttu-id="12b46-110">Zincirdeki etkin (yani en son) çerçeveyi alır.</span><span class="sxs-lookup"><span data-stu-id="12b46-110">Gets the active (that is, most recent) frame on the chain.</span></span>|  
|[<span data-ttu-id="12b46-111">GetCallee Yöntemi</span><span class="sxs-lookup"><span data-stu-id="12b46-111">GetCallee Method</span></span>](icordebugchain-getcallee-method.md)|<span data-ttu-id="12b46-112">Bu zincir tarafından çağrılan zinciri alır.</span><span class="sxs-lookup"><span data-stu-id="12b46-112">Gets the chain that was called by this chain.</span></span>|  
|[<span data-ttu-id="12b46-113">GetCaller Yöntemi</span><span class="sxs-lookup"><span data-stu-id="12b46-113">GetCaller Method</span></span>](icordebugchain-getcaller-method.md)|<span data-ttu-id="12b46-114">Bu zinciri çağıran zinciri alır.</span><span class="sxs-lookup"><span data-stu-id="12b46-114">Gets the chain that called this chain.</span></span>|  
|[<span data-ttu-id="12b46-115">GetContext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="12b46-115">GetContext Method</span></span>](icordebugchain-getcontext-method.md)|<span data-ttu-id="12b46-116">Uygulanmaz.</span><span class="sxs-lookup"><span data-stu-id="12b46-116">Not implemented.</span></span>|  
|[<span data-ttu-id="12b46-117">GetNext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="12b46-117">GetNext Method</span></span>](icordebugchain-getnext-method.md)|<span data-ttu-id="12b46-118">İş parçacığı için bir sonraki çerçeve zincirini alır.</span><span class="sxs-lookup"><span data-stu-id="12b46-118">Gets the next chain of frames for the thread.</span></span>|  
|[<span data-ttu-id="12b46-119">GetPrevious Yöntemi</span><span class="sxs-lookup"><span data-stu-id="12b46-119">GetPrevious Method</span></span>](icordebugchain-getprevious-method.md)|<span data-ttu-id="12b46-120">İş parçacığı için önceki çerçeve zincirini alır.</span><span class="sxs-lookup"><span data-stu-id="12b46-120">Gets the previous chain of frames for the thread.</span></span>|  
|[<span data-ttu-id="12b46-121">GetReason Yöntemi</span><span class="sxs-lookup"><span data-stu-id="12b46-121">GetReason Method</span></span>](icordebugchain-getreason-method.md)|<span data-ttu-id="12b46-122">Bu çağrı zincirinin Genesin nedenini alır.</span><span class="sxs-lookup"><span data-stu-id="12b46-122">Gets the reason for the genesis of this calling chain.</span></span>|  
|[<span data-ttu-id="12b46-123">GetRegisterSet Metodu</span><span class="sxs-lookup"><span data-stu-id="12b46-123">GetRegisterSet Method</span></span>](icordebugchain-getregisterset-method.md)|<span data-ttu-id="12b46-124">Bu zincirin etkin bölümü için kayıt kümesini alır.</span><span class="sxs-lookup"><span data-stu-id="12b46-124">Gets the register set for the active part of this chain.</span></span>|  
|[<span data-ttu-id="12b46-125">GetStackRange Yöntemi</span><span class="sxs-lookup"><span data-stu-id="12b46-125">GetStackRange Method</span></span>](icordebugchain-getstackrange-method.md)|<span data-ttu-id="12b46-126">Bu zincir için yığın segmentinin adres aralığını alır.</span><span class="sxs-lookup"><span data-stu-id="12b46-126">Gets the address range of the stack segment for this chain.</span></span>|  
|[<span data-ttu-id="12b46-127">GetThread Yöntemi</span><span class="sxs-lookup"><span data-stu-id="12b46-127">GetThread Method</span></span>](icordebugchain-getthread-method.md)|<span data-ttu-id="12b46-128">Bu çağrı zincirinin parçası olduğu fiziksel iş parçacığını alır.</span><span class="sxs-lookup"><span data-stu-id="12b46-128">Gets the physical thread this call chain is part of.</span></span>|  
|[<span data-ttu-id="12b46-129">IsManaged Yöntemi</span><span class="sxs-lookup"><span data-stu-id="12b46-129">IsManaged Method</span></span>](icordebugchain-ismanaged-method.md)|<span data-ttu-id="12b46-130">Bu zincirin yönetilen kodu çalıştırıp çalıştırmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="12b46-130">Gets a value that indicates whether this chain is running managed code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="12b46-131">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="12b46-131">Remarks</span></span>  

 <span data-ttu-id="12b46-132">Bir zincirdeki yığın çerçeveleri bitişik yığın alanı kaplar ve aynı iş parçacığını ve bağlamı paylaşır.</span><span class="sxs-lookup"><span data-stu-id="12b46-132">The stack frames in a chain occupy contiguous stack space and share the same thread and context.</span></span> <span data-ttu-id="12b46-133">Bir zincir, yönetilen ya da yönetilmeyen kod zincirlerini temsil edebilir.</span><span class="sxs-lookup"><span data-stu-id="12b46-133">A chain may represent either managed or unmanaged code chains.</span></span> <span data-ttu-id="12b46-134">Boş bir `ICorDebugChain` örnek, yönetilmeyen bir kod zincirini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="12b46-134">An empty `ICorDebugChain` instance represents an unmanaged code chain.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="12b46-135">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="12b46-135">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="12b46-136">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="12b46-136">Requirements</span></span>  

 <span data-ttu-id="12b46-137">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="12b46-137">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12b46-138">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="12b46-138">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="12b46-139">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="12b46-139">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="12b46-140">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="12b46-140">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12b46-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="12b46-141">See also</span></span>

- [<span data-ttu-id="12b46-142">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="12b46-142">Debugging Interfaces</span></span>](debugging-interfaces.md)
