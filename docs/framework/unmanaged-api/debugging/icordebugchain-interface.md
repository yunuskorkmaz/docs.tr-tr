---
description: 'Şu konuda daha fazla bilgi edinin: ıcordebugzincirleri arabirimi'
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
ms.openlocfilehash: 391c9a3e54d06d303728da5ab7f105bc8e2558ef
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99661213"
---
# <a name="icordebugchain-interface"></a><span data-ttu-id="ff371-103">ICorDebugChain Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ff371-103">ICorDebugChain Interface</span></span>

<span data-ttu-id="ff371-104">Fiziksel veya mantıksal bir çağrı yığınının bir kesimini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="ff371-104">Represents a segment of a physical or logical call stack.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ff371-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="ff371-105">Methods</span></span>  
  
|<span data-ttu-id="ff371-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="ff371-106">Method</span></span>|<span data-ttu-id="ff371-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ff371-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ff371-108">EnumerateFrames Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ff371-108">EnumerateFrames Method</span></span>](icordebugchain-enumerateframes-method.md)|<span data-ttu-id="ff371-109">En son kareyle başlayarak zincirdeki tüm yönetilen yığın çerçevelerini içeren bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="ff371-109">Gets an enumerator that contains all the managed stack frames in the chain, starting with the most recent frame.</span></span>|  
|[<span data-ttu-id="ff371-110">GetActiveFrame Metodu</span><span class="sxs-lookup"><span data-stu-id="ff371-110">GetActiveFrame Method</span></span>](icordebugchain-getactiveframe-method.md)|<span data-ttu-id="ff371-111">Zincirdeki etkin (yani en son) çerçeveyi alır.</span><span class="sxs-lookup"><span data-stu-id="ff371-111">Gets the active (that is, most recent) frame on the chain.</span></span>|  
|[<span data-ttu-id="ff371-112">GetCallee Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ff371-112">GetCallee Method</span></span>](icordebugchain-getcallee-method.md)|<span data-ttu-id="ff371-113">Bu zincir tarafından çağrılan zinciri alır.</span><span class="sxs-lookup"><span data-stu-id="ff371-113">Gets the chain that was called by this chain.</span></span>|  
|[<span data-ttu-id="ff371-114">GetCaller Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ff371-114">GetCaller Method</span></span>](icordebugchain-getcaller-method.md)|<span data-ttu-id="ff371-115">Bu zinciri çağıran zinciri alır.</span><span class="sxs-lookup"><span data-stu-id="ff371-115">Gets the chain that called this chain.</span></span>|  
|[<span data-ttu-id="ff371-116">GetContext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ff371-116">GetContext Method</span></span>](icordebugchain-getcontext-method.md)|<span data-ttu-id="ff371-117">Uygulanmaz.</span><span class="sxs-lookup"><span data-stu-id="ff371-117">Not implemented.</span></span>|  
|[<span data-ttu-id="ff371-118">GetNext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ff371-118">GetNext Method</span></span>](icordebugchain-getnext-method.md)|<span data-ttu-id="ff371-119">İş parçacığı için bir sonraki çerçeve zincirini alır.</span><span class="sxs-lookup"><span data-stu-id="ff371-119">Gets the next chain of frames for the thread.</span></span>|  
|[<span data-ttu-id="ff371-120">GetPrevious Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ff371-120">GetPrevious Method</span></span>](icordebugchain-getprevious-method.md)|<span data-ttu-id="ff371-121">İş parçacığı için önceki çerçeve zincirini alır.</span><span class="sxs-lookup"><span data-stu-id="ff371-121">Gets the previous chain of frames for the thread.</span></span>|  
|[<span data-ttu-id="ff371-122">GetReason Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ff371-122">GetReason Method</span></span>](icordebugchain-getreason-method.md)|<span data-ttu-id="ff371-123">Bu çağrı zincirinin Genesin nedenini alır.</span><span class="sxs-lookup"><span data-stu-id="ff371-123">Gets the reason for the genesis of this calling chain.</span></span>|  
|[<span data-ttu-id="ff371-124">GetRegisterSet Metodu</span><span class="sxs-lookup"><span data-stu-id="ff371-124">GetRegisterSet Method</span></span>](icordebugchain-getregisterset-method.md)|<span data-ttu-id="ff371-125">Bu zincirin etkin bölümü için kayıt kümesini alır.</span><span class="sxs-lookup"><span data-stu-id="ff371-125">Gets the register set for the active part of this chain.</span></span>|  
|[<span data-ttu-id="ff371-126">GetStackRange Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ff371-126">GetStackRange Method</span></span>](icordebugchain-getstackrange-method.md)|<span data-ttu-id="ff371-127">Bu zincir için yığın segmentinin adres aralığını alır.</span><span class="sxs-lookup"><span data-stu-id="ff371-127">Gets the address range of the stack segment for this chain.</span></span>|  
|[<span data-ttu-id="ff371-128">GetThread Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ff371-128">GetThread Method</span></span>](icordebugchain-getthread-method.md)|<span data-ttu-id="ff371-129">Bu çağrı zincirinin parçası olduğu fiziksel iş parçacığını alır.</span><span class="sxs-lookup"><span data-stu-id="ff371-129">Gets the physical thread this call chain is part of.</span></span>|  
|[<span data-ttu-id="ff371-130">IsManaged Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ff371-130">IsManaged Method</span></span>](icordebugchain-ismanaged-method.md)|<span data-ttu-id="ff371-131">Bu zincirin yönetilen kodu çalıştırıp çalıştırmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="ff371-131">Gets a value that indicates whether this chain is running managed code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ff371-132">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ff371-132">Remarks</span></span>  

 <span data-ttu-id="ff371-133">Bir zincirdeki yığın çerçeveleri bitişik yığın alanı kaplar ve aynı iş parçacığını ve bağlamı paylaşır.</span><span class="sxs-lookup"><span data-stu-id="ff371-133">The stack frames in a chain occupy contiguous stack space and share the same thread and context.</span></span> <span data-ttu-id="ff371-134">Bir zincir, yönetilen ya da yönetilmeyen kod zincirlerini temsil edebilir.</span><span class="sxs-lookup"><span data-stu-id="ff371-134">A chain may represent either managed or unmanaged code chains.</span></span> <span data-ttu-id="ff371-135">Boş bir `ICorDebugChain` örnek, yönetilmeyen bir kod zincirini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="ff371-135">An empty `ICorDebugChain` instance represents an unmanaged code chain.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ff371-136">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="ff371-136">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff371-137">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ff371-137">Requirements</span></span>  

 <span data-ttu-id="ff371-138">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ff371-138">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff371-139">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ff371-139">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ff371-140">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="ff371-140">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ff371-141">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff371-141">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff371-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ff371-142">See also</span></span>

- [<span data-ttu-id="ff371-143">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="ff371-143">Debugging Interfaces</span></span>](debugging-interfaces.md)
