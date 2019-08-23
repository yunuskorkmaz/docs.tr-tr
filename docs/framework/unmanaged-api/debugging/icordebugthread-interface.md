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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1517d686c50923f5599e33436e0ad6126e8be140
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923150"
---
# <a name="icordebugthread-interface"></a><span data-ttu-id="415f0-102">ICorDebugThread Arabirimi</span><span class="sxs-lookup"><span data-stu-id="415f0-102">ICorDebugThread Interface</span></span>
<span data-ttu-id="415f0-103">Bir işlemdeki bir iş parçacığını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="415f0-103">Represents a thread in a process.</span></span> <span data-ttu-id="415f0-104">Bir `ICorDebugThread` örneğin yaşam süresi, temsil ettiği iş parçacığının ömrü ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="415f0-104">The lifetime of an `ICorDebugThread` instance is the same as the lifetime of the thread it represents.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="415f0-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="415f0-105">Methods</span></span>  
  
|<span data-ttu-id="415f0-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="415f0-106">Method</span></span>|<span data-ttu-id="415f0-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="415f0-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="415f0-108">ClearCurrentException Yöntemi</span><span class="sxs-lookup"><span data-stu-id="415f0-108">ClearCurrentException Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-clearcurrentexception-method.md)|<span data-ttu-id="415f0-109">Bu yöntem uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="415f0-109">This method is not implemented.</span></span> <span data-ttu-id="415f0-110">Onu kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="415f0-110">Do not use it.</span></span>|  
|[<span data-ttu-id="415f0-111">CreateEval Yöntemi</span><span class="sxs-lookup"><span data-stu-id="415f0-111">CreateEval Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-createeval-method.md)|<span data-ttu-id="415f0-112">Bu `ICorDebugThread`, üzerinde çalışan bir ıcorınkıt geval nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="415f0-112">Creates an ICorDebugEval object that operates on this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="415f0-113">CreateStepper Yöntemi</span><span class="sxs-lookup"><span data-stu-id="415f0-113">CreateStepper Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-createstepper-method.md)|<span data-ttu-id="415f0-114">Bu `ICorDebugThread`, içindeki etkin çerçeve üzerinde Adımlama sağlayan bir ICorDebugStepper nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="415f0-114">Creates an ICorDebugStepper object that allows stepping through the active frame in this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="415f0-115">EnumerateChains Yöntemi</span><span class="sxs-lookup"><span data-stu-id="415f0-115">EnumerateChains Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-enumeratechains-method.md)|<span data-ttu-id="415f0-116">Bu `ICorDebugThread`, içindeki tüm yığın zincirlerini Içeren ICorDebugChainEnum numaralandırıcısı için bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="415f0-116">Gets an interface pointer to an ICorDebugChainEnum enumerator that contains all the stack chains in this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="415f0-117">GetActiveChain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="415f0-117">GetActiveChain Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getactivechain-method.md)|<span data-ttu-id="415f0-118">Bu `ICorDebugThread`, üzerinde etkin ıcordebugzincirine bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="415f0-118">Gets an interface pointer to the active ICorDebugChain on this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="415f0-119">GetActiveFrame Yöntemi</span><span class="sxs-lookup"><span data-stu-id="415f0-119">GetActiveFrame Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getactiveframe-method.md)|<span data-ttu-id="415f0-120">Bunun `ICorDebugThread`üzerinde etkin ICorDebugFrame 'e bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="415f0-120">Gets an interface pointer to the active ICorDebugFrame on this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="415f0-121">GetAppDomain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="415f0-121">GetAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getappdomain-method.md)|<span data-ttu-id="415f0-122">Şu anda yürütülmekte olan uygulama etki alanına `ICorDebugThread` bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="415f0-122">Gets an interface pointer to the application domain in which this `ICorDebugThread` is currently executing.</span></span>|  
|[<span data-ttu-id="415f0-123">GetCurrentException Yöntemi</span><span class="sxs-lookup"><span data-stu-id="415f0-123">GetCurrentException Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getcurrentexception-method.md)|<span data-ttu-id="415f0-124">Yönetilen kod tarafından şu anda oluşturulan bir özel durumu temsil eden ICorDebugValue nesnesine yönelik bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="415f0-124">Gets an interface pointer to an ICorDebugValue object that represents an exception currently being thrown by managed code.</span></span>|  
|[<span data-ttu-id="415f0-125">GetDebugState Yöntemi</span><span class="sxs-lookup"><span data-stu-id="415f0-125">GetDebugState Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getdebugstate-method.md)|<span data-ttu-id="415f0-126">Bunun `ICorDebugThread`geçerli hata ayıklama durumunu açıklayan bir CorDebugThreadState değeri alır.</span><span class="sxs-lookup"><span data-stu-id="415f0-126">Gets a CorDebugThreadState value that describes the current debug state of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="415f0-127">GetHandle Yöntemi</span><span class="sxs-lookup"><span data-stu-id="415f0-127">GetHandle Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-gethandle-method.md)|<span data-ttu-id="415f0-128">Bu `ICorDebugThread`öğesinin etkin bölümü için geçerli tanıtıcıyı alır.</span><span class="sxs-lookup"><span data-stu-id="415f0-128">Gets the current handle for the active part of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="415f0-129">GetID Yöntemi</span><span class="sxs-lookup"><span data-stu-id="415f0-129">GetID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getid-method.md)|<span data-ttu-id="415f0-130">Bu `ICorDebugThread`öğesinin etkin bölümünün geçerli işletim sistemi tanımlayıcısını alır.</span><span class="sxs-lookup"><span data-stu-id="415f0-130">Gets the current operating system identifier of the active part of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="415f0-131">GetObject Yöntemi</span><span class="sxs-lookup"><span data-stu-id="415f0-131">GetObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getobject-method.md)|<span data-ttu-id="415f0-132">Ortak dil çalışma zamanı (CLR) iş parçacığına bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="415f0-132">Gets an interface pointer to the common language runtime (CLR) thread.</span></span>|  
|[<span data-ttu-id="415f0-133">GetProcess Yöntemi</span><span class="sxs-lookup"><span data-stu-id="415f0-133">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getprocess-method.md)|<span data-ttu-id="415f0-134">Bu `ICorDebugThread` işlemin bir parçasını oluşturan işlem için bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="415f0-134">Gets an interface pointer to the process of which this `ICorDebugThread` forms a part.</span></span>|  
|[<span data-ttu-id="415f0-135">GetRegisterSet Yöntemi</span><span class="sxs-lookup"><span data-stu-id="415f0-135">GetRegisterSet Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getregisterset-method.md)|<span data-ttu-id="415f0-136">Bu `ICorDebugThread`ile ilişkili kayıt kümesine bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="415f0-136">Gets an interface pointer to the register set associated with this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="415f0-137">GetUserState Yöntemi</span><span class="sxs-lookup"><span data-stu-id="415f0-137">GetUserState Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getuserstate-method.md)|<span data-ttu-id="415f0-138">Bunun `ICorDebugThread`geçerli durumunu tanımlayan CorDebugUserState değerlerinin bit düzeyinde birleşimini alır.</span><span class="sxs-lookup"><span data-stu-id="415f0-138">Gets a bitwise combination of CorDebugUserState values that describe the current state of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="415f0-139">SetDebugState Yöntemi</span><span class="sxs-lookup"><span data-stu-id="415f0-139">SetDebugState Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-setdebugstate-method.md)|<span data-ttu-id="415f0-140">`CorDebugThreadState` Bunun`ICorDebugThread`hata ayıklama durumunu tanımlayan değerlerin bit düzeyinde birleşimini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="415f0-140">Sets a bitwise combination of `CorDebugThreadState` values that describe the debugging state of this `ICorDebugThread`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="415f0-141">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="415f0-141">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="415f0-142">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="415f0-142">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="415f0-143">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="415f0-143">Requirements</span></span>  
 <span data-ttu-id="415f0-144">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="415f0-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="415f0-145">**Üst bilgi** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="415f0-145">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="415f0-146">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="415f0-146">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="415f0-147">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="415f0-147">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="415f0-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="415f0-148">See also</span></span>

- [<span data-ttu-id="415f0-149">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="415f0-149">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
