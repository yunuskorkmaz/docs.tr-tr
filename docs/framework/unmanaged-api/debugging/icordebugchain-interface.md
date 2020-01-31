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
ms.openlocfilehash: f4bacfe94178ea78b1c3afd15a2e100076c38a84
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76777991"
---
# <a name="icordebugchain-interface"></a><span data-ttu-id="65450-102">ICorDebugChain Arabirimi</span><span class="sxs-lookup"><span data-stu-id="65450-102">ICorDebugChain Interface</span></span>

<span data-ttu-id="65450-103">Fiziksel veya mantıksal bir çağrı yığınının bir kesimini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="65450-103">Represents a segment of a physical or logical call stack.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="65450-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="65450-104">Methods</span></span>  
  
|<span data-ttu-id="65450-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="65450-105">Method</span></span>|<span data-ttu-id="65450-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="65450-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="65450-107">EnumerateFrames Yöntemi</span><span class="sxs-lookup"><span data-stu-id="65450-107">EnumerateFrames Method</span></span>](icordebugchain-enumerateframes-method.md)|<span data-ttu-id="65450-108">En son kareyle başlayarak zincirdeki tüm yönetilen yığın çerçevelerini içeren bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="65450-108">Gets an enumerator that contains all the managed stack frames in the chain, starting with the most recent frame.</span></span>|  
|[<span data-ttu-id="65450-109">GetActiveFrame Yöntemi</span><span class="sxs-lookup"><span data-stu-id="65450-109">GetActiveFrame Method</span></span>](icordebugchain-getactiveframe-method.md)|<span data-ttu-id="65450-110">Zincirdeki etkin (yani en son) çerçeveyi alır.</span><span class="sxs-lookup"><span data-stu-id="65450-110">Gets the active (that is, most recent) frame on the chain.</span></span>|  
|[<span data-ttu-id="65450-111">GetCallee Yöntemi</span><span class="sxs-lookup"><span data-stu-id="65450-111">GetCallee Method</span></span>](icordebugchain-getcallee-method.md)|<span data-ttu-id="65450-112">Bu zincir tarafından çağrılan zinciri alır.</span><span class="sxs-lookup"><span data-stu-id="65450-112">Gets the chain that was called by this chain.</span></span>|  
|[<span data-ttu-id="65450-113">GetCaller Yöntemi</span><span class="sxs-lookup"><span data-stu-id="65450-113">GetCaller Method</span></span>](icordebugchain-getcaller-method.md)|<span data-ttu-id="65450-114">Bu zinciri çağıran zinciri alır.</span><span class="sxs-lookup"><span data-stu-id="65450-114">Gets the chain that called this chain.</span></span>|  
|[<span data-ttu-id="65450-115">GetContext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="65450-115">GetContext Method</span></span>](icordebugchain-getcontext-method.md)|<span data-ttu-id="65450-116">Uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="65450-116">Not implemented.</span></span>|  
|[<span data-ttu-id="65450-117">GetNext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="65450-117">GetNext Method</span></span>](icordebugchain-getnext-method.md)|<span data-ttu-id="65450-118">İş parçacığı için bir sonraki çerçeve zincirini alır.</span><span class="sxs-lookup"><span data-stu-id="65450-118">Gets the next chain of frames for the thread.</span></span>|  
|[<span data-ttu-id="65450-119">GetPrevious Yöntemi</span><span class="sxs-lookup"><span data-stu-id="65450-119">GetPrevious Method</span></span>](icordebugchain-getprevious-method.md)|<span data-ttu-id="65450-120">İş parçacığı için önceki çerçeve zincirini alır.</span><span class="sxs-lookup"><span data-stu-id="65450-120">Gets the previous chain of frames for the thread.</span></span>|  
|[<span data-ttu-id="65450-121">GetReason Yöntemi</span><span class="sxs-lookup"><span data-stu-id="65450-121">GetReason Method</span></span>](icordebugchain-getreason-method.md)|<span data-ttu-id="65450-122">Bu çağrı zincirinin Genesin nedenini alır.</span><span class="sxs-lookup"><span data-stu-id="65450-122">Gets the reason for the genesis of this calling chain.</span></span>|  
|[<span data-ttu-id="65450-123">GetRegisterSet Yöntemi</span><span class="sxs-lookup"><span data-stu-id="65450-123">GetRegisterSet Method</span></span>](icordebugchain-getregisterset-method.md)|<span data-ttu-id="65450-124">Bu zincirin etkin bölümü için kayıt kümesini alır.</span><span class="sxs-lookup"><span data-stu-id="65450-124">Gets the register set for the active part of this chain.</span></span>|  
|[<span data-ttu-id="65450-125">GetStackRange Yöntemi</span><span class="sxs-lookup"><span data-stu-id="65450-125">GetStackRange Method</span></span>](icordebugchain-getstackrange-method.md)|<span data-ttu-id="65450-126">Bu zincir için yığın segmentinin adres aralığını alır.</span><span class="sxs-lookup"><span data-stu-id="65450-126">Gets the address range of the stack segment for this chain.</span></span>|  
|[<span data-ttu-id="65450-127">GetThread Yöntemi</span><span class="sxs-lookup"><span data-stu-id="65450-127">GetThread Method</span></span>](icordebugchain-getthread-method.md)|<span data-ttu-id="65450-128">Bu çağrı zincirinin parçası olduğu fiziksel iş parçacığını alır.</span><span class="sxs-lookup"><span data-stu-id="65450-128">Gets the physical thread this call chain is part of.</span></span>|  
|[<span data-ttu-id="65450-129">IsManaged Yöntemi</span><span class="sxs-lookup"><span data-stu-id="65450-129">IsManaged Method</span></span>](icordebugchain-ismanaged-method.md)|<span data-ttu-id="65450-130">Bu zincirin yönetilen kodu çalıştırıp çalıştırmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="65450-130">Gets a value that indicates whether this chain is running managed code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="65450-131">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="65450-131">Remarks</span></span>  
 <span data-ttu-id="65450-132">Bir zincirdeki yığın çerçeveleri bitişik yığın alanı kaplar ve aynı iş parçacığını ve bağlamı paylaşır.</span><span class="sxs-lookup"><span data-stu-id="65450-132">The stack frames in a chain occupy contiguous stack space and share the same thread and context.</span></span> <span data-ttu-id="65450-133">Bir zincir, yönetilen ya da yönetilmeyen kod zincirlerini temsil edebilir.</span><span class="sxs-lookup"><span data-stu-id="65450-133">A chain may represent either managed or unmanaged code chains.</span></span> <span data-ttu-id="65450-134">Boş bir `ICorDebugChain` örneği, yönetilmeyen bir kod zincirini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="65450-134">An empty `ICorDebugChain` instance represents an unmanaged code chain.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="65450-135">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="65450-135">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65450-136">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="65450-136">Requirements</span></span>  
 <span data-ttu-id="65450-137">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65450-137">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65450-138">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="65450-138">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="65450-139">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="65450-139">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="65450-140">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65450-140">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65450-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="65450-141">See also</span></span>

- [<span data-ttu-id="65450-142">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="65450-142">Debugging Interfaces</span></span>](debugging-interfaces.md)
