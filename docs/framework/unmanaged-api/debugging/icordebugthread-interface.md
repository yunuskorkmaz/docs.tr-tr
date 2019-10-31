---
title: ICorDebugThread Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugThread
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread
helpviewer_keywords:
- ICorDebugThread interface [.NET Framework debugging]
ms.assetid: 3930fd9b-2bc3-4b72-80a0-b6eeb94d60c6
topic_type:
- apiref
ms.openlocfilehash: c7333f4210d0a2ec4ff71a0fac0ea00068fecc57
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133504"
---
# <a name="icordebugthread-interface"></a><span data-ttu-id="51f1e-102">ICorDebugThread Arabirimi</span><span class="sxs-lookup"><span data-stu-id="51f1e-102">ICorDebugThread Interface</span></span>
<span data-ttu-id="51f1e-103">Bir işlemdeki bir iş parçacığını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="51f1e-103">Represents a thread in a process.</span></span> <span data-ttu-id="51f1e-104">Bir `ICorDebugThread` örneğinin kullanım ömrü, temsil ettiği iş parçacığının yaşam süresi ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="51f1e-104">The lifetime of an `ICorDebugThread` instance is the same as the lifetime of the thread it represents.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="51f1e-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="51f1e-105">Methods</span></span>  
  
|<span data-ttu-id="51f1e-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="51f1e-106">Method</span></span>|<span data-ttu-id="51f1e-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="51f1e-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="51f1e-108">ClearCurrentException Yöntemi</span><span class="sxs-lookup"><span data-stu-id="51f1e-108">ClearCurrentException Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-clearcurrentexception-method.md)|<span data-ttu-id="51f1e-109">Bu yöntem uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="51f1e-109">This method is not implemented.</span></span> <span data-ttu-id="51f1e-110">Onu kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="51f1e-110">Do not use it.</span></span>|  
|[<span data-ttu-id="51f1e-111">CreateEval Yöntemi</span><span class="sxs-lookup"><span data-stu-id="51f1e-111">CreateEval Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-createeval-method.md)|<span data-ttu-id="51f1e-112">Bu `ICorDebugThread`çalışan bir ıcorınkıt Geval nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="51f1e-112">Creates an ICorDebugEval object that operates on this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="51f1e-113">CreateStepper Yöntemi</span><span class="sxs-lookup"><span data-stu-id="51f1e-113">CreateStepper Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-createstepper-method.md)|<span data-ttu-id="51f1e-114">Bu `ICorDebugThread`etkin çerçeve üzerinde Adımlama sağlayan bir ICorDebugStepper nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="51f1e-114">Creates an ICorDebugStepper object that allows stepping through the active frame in this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="51f1e-115">EnumerateChains Yöntemi</span><span class="sxs-lookup"><span data-stu-id="51f1e-115">EnumerateChains Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-enumeratechains-method.md)|<span data-ttu-id="51f1e-116">Bu `ICorDebugThread`tüm yığın zincirlerini içeren ICorDebugChainEnum numaralandırıcısı için bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="51f1e-116">Gets an interface pointer to an ICorDebugChainEnum enumerator that contains all the stack chains in this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="51f1e-117">GetActiveChain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="51f1e-117">GetActiveChain Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getactivechain-method.md)|<span data-ttu-id="51f1e-118">Bu `ICorDebugThread`etkin ıcordebugzincirine yönelik bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="51f1e-118">Gets an interface pointer to the active ICorDebugChain on this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="51f1e-119">GetActiveFrame Yöntemi</span><span class="sxs-lookup"><span data-stu-id="51f1e-119">GetActiveFrame Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getactiveframe-method.md)|<span data-ttu-id="51f1e-120">Bu `ICorDebugThread`etkin ICorDebugFrame 'e bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="51f1e-120">Gets an interface pointer to the active ICorDebugFrame on this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="51f1e-121">GetAppDomain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="51f1e-121">GetAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getappdomain-method.md)|<span data-ttu-id="51f1e-122">Bu `ICorDebugThread` Şu anda yürütüldüğü uygulama etki alanına bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="51f1e-122">Gets an interface pointer to the application domain in which this `ICorDebugThread` is currently executing.</span></span>|  
|[<span data-ttu-id="51f1e-123">GetCurrentException Yöntemi</span><span class="sxs-lookup"><span data-stu-id="51f1e-123">GetCurrentException Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getcurrentexception-method.md)|<span data-ttu-id="51f1e-124">Yönetilen kod tarafından şu anda oluşturulan bir özel durumu temsil eden ICorDebugValue nesnesine yönelik bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="51f1e-124">Gets an interface pointer to an ICorDebugValue object that represents an exception currently being thrown by managed code.</span></span>|  
|[<span data-ttu-id="51f1e-125">GetDebugState Yöntemi</span><span class="sxs-lookup"><span data-stu-id="51f1e-125">GetDebugState Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getdebugstate-method.md)|<span data-ttu-id="51f1e-126">Bu `ICorDebugThread`geçerli hata ayıklama durumunu açıklayan bir CorDebugThreadState değeri alır.</span><span class="sxs-lookup"><span data-stu-id="51f1e-126">Gets a CorDebugThreadState value that describes the current debug state of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="51f1e-127">GetHandle Yöntemi</span><span class="sxs-lookup"><span data-stu-id="51f1e-127">GetHandle Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-gethandle-method.md)|<span data-ttu-id="51f1e-128">Bu `ICorDebugThread`etkin bölümü için geçerli tanıtıcıyı alır.</span><span class="sxs-lookup"><span data-stu-id="51f1e-128">Gets the current handle for the active part of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="51f1e-129">GetID Yöntemi</span><span class="sxs-lookup"><span data-stu-id="51f1e-129">GetID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getid-method.md)|<span data-ttu-id="51f1e-130">Bu `ICorDebugThread`etkin bölümünün geçerli işletim sistemi tanımlayıcısını alır.</span><span class="sxs-lookup"><span data-stu-id="51f1e-130">Gets the current operating system identifier of the active part of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="51f1e-131">GetObject Yöntemi</span><span class="sxs-lookup"><span data-stu-id="51f1e-131">GetObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getobject-method.md)|<span data-ttu-id="51f1e-132">Ortak dil çalışma zamanı (CLR) iş parçacığına bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="51f1e-132">Gets an interface pointer to the common language runtime (CLR) thread.</span></span>|  
|[<span data-ttu-id="51f1e-133">GetProcess Yöntemi</span><span class="sxs-lookup"><span data-stu-id="51f1e-133">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getprocess-method.md)|<span data-ttu-id="51f1e-134">Bu `ICorDebugThread` bir parçasını oluşturan işlem için bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="51f1e-134">Gets an interface pointer to the process of which this `ICorDebugThread` forms a part.</span></span>|  
|[<span data-ttu-id="51f1e-135">GetRegisterSet Yöntemi</span><span class="sxs-lookup"><span data-stu-id="51f1e-135">GetRegisterSet Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getregisterset-method.md)|<span data-ttu-id="51f1e-136">Bu `ICorDebugThread`ilişkili kayıt kümesine bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="51f1e-136">Gets an interface pointer to the register set associated with this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="51f1e-137">GetUserState Yöntemi</span><span class="sxs-lookup"><span data-stu-id="51f1e-137">GetUserState Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getuserstate-method.md)|<span data-ttu-id="51f1e-138">Bu `ICorDebugThread`geçerli durumunu tanımlayan CorDebugUserState değerlerinin bit düzeyinde birleşimini alır.</span><span class="sxs-lookup"><span data-stu-id="51f1e-138">Gets a bitwise combination of CorDebugUserState values that describe the current state of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="51f1e-139">SetDebugState Yöntemi</span><span class="sxs-lookup"><span data-stu-id="51f1e-139">SetDebugState Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-setdebugstate-method.md)|<span data-ttu-id="51f1e-140">Bu `ICorDebugThread`hata ayıklama durumunu tanımlayan `CorDebugThreadState` değerlerinin bit düzeyinde birleşimini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="51f1e-140">Sets a bitwise combination of `CorDebugThreadState` values that describe the debugging state of this `ICorDebugThread`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="51f1e-141">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="51f1e-141">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="51f1e-142">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="51f1e-142">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="51f1e-143">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="51f1e-143">Requirements</span></span>  
 <span data-ttu-id="51f1e-144">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="51f1e-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="51f1e-145">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="51f1e-145">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="51f1e-146">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="51f1e-146">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="51f1e-147">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="51f1e-147">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51f1e-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="51f1e-148">See also</span></span>

- [<span data-ttu-id="51f1e-149">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="51f1e-149">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
