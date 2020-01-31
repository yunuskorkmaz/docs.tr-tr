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
ms.openlocfilehash: b227b374021136e78f7f061d235eb18eca5b9515
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791482"
---
# <a name="icordebugthread-interface"></a><span data-ttu-id="10150-102">ICorDebugThread Arabirimi</span><span class="sxs-lookup"><span data-stu-id="10150-102">ICorDebugThread Interface</span></span>
<span data-ttu-id="10150-103">Bir işlemdeki bir iş parçacığını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="10150-103">Represents a thread in a process.</span></span> <span data-ttu-id="10150-104">Bir `ICorDebugThread` örneğinin kullanım ömrü, temsil ettiği iş parçacığının yaşam süresi ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="10150-104">The lifetime of an `ICorDebugThread` instance is the same as the lifetime of the thread it represents.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="10150-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="10150-105">Methods</span></span>  
  
|<span data-ttu-id="10150-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="10150-106">Method</span></span>|<span data-ttu-id="10150-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="10150-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="10150-108">ClearCurrentException Yöntemi</span><span class="sxs-lookup"><span data-stu-id="10150-108">ClearCurrentException Method</span></span>](icordebugthread-clearcurrentexception-method.md)|<span data-ttu-id="10150-109">Bu yöntem uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="10150-109">This method is not implemented.</span></span> <span data-ttu-id="10150-110">Onu kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="10150-110">Do not use it.</span></span>|  
|[<span data-ttu-id="10150-111">CreateEval Yöntemi</span><span class="sxs-lookup"><span data-stu-id="10150-111">CreateEval Method</span></span>](icordebugthread-createeval-method.md)|<span data-ttu-id="10150-112">Bu `ICorDebugThread`çalışan bir ıcorınkıt Geval nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="10150-112">Creates an ICorDebugEval object that operates on this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="10150-113">CreateStepper Yöntemi</span><span class="sxs-lookup"><span data-stu-id="10150-113">CreateStepper Method</span></span>](icordebugthread-createstepper-method.md)|<span data-ttu-id="10150-114">Bu `ICorDebugThread`etkin çerçeve üzerinde Adımlama sağlayan bir ICorDebugStepper nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="10150-114">Creates an ICorDebugStepper object that allows stepping through the active frame in this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="10150-115">EnumerateChains Yöntemi</span><span class="sxs-lookup"><span data-stu-id="10150-115">EnumerateChains Method</span></span>](icordebugthread-enumeratechains-method.md)|<span data-ttu-id="10150-116">Bu `ICorDebugThread`tüm yığın zincirlerini içeren ICorDebugChainEnum numaralandırıcısı için bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="10150-116">Gets an interface pointer to an ICorDebugChainEnum enumerator that contains all the stack chains in this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="10150-117">GetActiveChain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="10150-117">GetActiveChain Method</span></span>](icordebugthread-getactivechain-method.md)|<span data-ttu-id="10150-118">Bu `ICorDebugThread`etkin ıcordebugzincirine yönelik bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="10150-118">Gets an interface pointer to the active ICorDebugChain on this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="10150-119">GetActiveFrame Yöntemi</span><span class="sxs-lookup"><span data-stu-id="10150-119">GetActiveFrame Method</span></span>](icordebugthread-getactiveframe-method.md)|<span data-ttu-id="10150-120">Bu `ICorDebugThread`etkin ICorDebugFrame 'e bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="10150-120">Gets an interface pointer to the active ICorDebugFrame on this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="10150-121">GetAppDomain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="10150-121">GetAppDomain Method</span></span>](icordebugthread-getappdomain-method.md)|<span data-ttu-id="10150-122">Bu `ICorDebugThread` Şu anda yürütüldüğü uygulama etki alanına bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="10150-122">Gets an interface pointer to the application domain in which this `ICorDebugThread` is currently executing.</span></span>|  
|[<span data-ttu-id="10150-123">GetCurrentException Yöntemi</span><span class="sxs-lookup"><span data-stu-id="10150-123">GetCurrentException Method</span></span>](icordebugthread-getcurrentexception-method.md)|<span data-ttu-id="10150-124">Yönetilen kod tarafından şu anda oluşturulan bir özel durumu temsil eden ICorDebugValue nesnesine yönelik bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="10150-124">Gets an interface pointer to an ICorDebugValue object that represents an exception currently being thrown by managed code.</span></span>|  
|[<span data-ttu-id="10150-125">GetDebugState Yöntemi</span><span class="sxs-lookup"><span data-stu-id="10150-125">GetDebugState Method</span></span>](icordebugthread-getdebugstate-method.md)|<span data-ttu-id="10150-126">Bu `ICorDebugThread`geçerli hata ayıklama durumunu açıklayan bir CorDebugThreadState değeri alır.</span><span class="sxs-lookup"><span data-stu-id="10150-126">Gets a CorDebugThreadState value that describes the current debug state of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="10150-127">GetHandle Yöntemi</span><span class="sxs-lookup"><span data-stu-id="10150-127">GetHandle Method</span></span>](icordebugthread-gethandle-method.md)|<span data-ttu-id="10150-128">Bu `ICorDebugThread`etkin bölümü için geçerli tanıtıcıyı alır.</span><span class="sxs-lookup"><span data-stu-id="10150-128">Gets the current handle for the active part of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="10150-129">GetID Yöntemi</span><span class="sxs-lookup"><span data-stu-id="10150-129">GetID Method</span></span>](icordebugthread-getid-method.md)|<span data-ttu-id="10150-130">Bu `ICorDebugThread`etkin bölümünün geçerli işletim sistemi tanımlayıcısını alır.</span><span class="sxs-lookup"><span data-stu-id="10150-130">Gets the current operating system identifier of the active part of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="10150-131">GetObject Yöntemi</span><span class="sxs-lookup"><span data-stu-id="10150-131">GetObject Method</span></span>](icordebugthread-getobject-method.md)|<span data-ttu-id="10150-132">Ortak dil çalışma zamanı (CLR) iş parçacığına bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="10150-132">Gets an interface pointer to the common language runtime (CLR) thread.</span></span>|  
|[<span data-ttu-id="10150-133">GetProcess Yöntemi</span><span class="sxs-lookup"><span data-stu-id="10150-133">GetProcess Method</span></span>](icordebugthread-getprocess-method.md)|<span data-ttu-id="10150-134">Bu `ICorDebugThread` bir parçasını oluşturan işlem için bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="10150-134">Gets an interface pointer to the process of which this `ICorDebugThread` forms a part.</span></span>|  
|[<span data-ttu-id="10150-135">GetRegisterSet Yöntemi</span><span class="sxs-lookup"><span data-stu-id="10150-135">GetRegisterSet Method</span></span>](icordebugthread-getregisterset-method.md)|<span data-ttu-id="10150-136">Bu `ICorDebugThread`ilişkili kayıt kümesine bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="10150-136">Gets an interface pointer to the register set associated with this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="10150-137">GetUserState Yöntemi</span><span class="sxs-lookup"><span data-stu-id="10150-137">GetUserState Method</span></span>](icordebugthread-getuserstate-method.md)|<span data-ttu-id="10150-138">Bu `ICorDebugThread`geçerli durumunu tanımlayan CorDebugUserState değerlerinin bit düzeyinde birleşimini alır.</span><span class="sxs-lookup"><span data-stu-id="10150-138">Gets a bitwise combination of CorDebugUserState values that describe the current state of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="10150-139">SetDebugState Yöntemi</span><span class="sxs-lookup"><span data-stu-id="10150-139">SetDebugState Method</span></span>](icordebugthread-setdebugstate-method.md)|<span data-ttu-id="10150-140">Bu `ICorDebugThread`hata ayıklama durumunu tanımlayan `CorDebugThreadState` değerlerinin bit düzeyinde birleşimini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="10150-140">Sets a bitwise combination of `CorDebugThreadState` values that describe the debugging state of this `ICorDebugThread`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="10150-141">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="10150-141">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="10150-142">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="10150-142">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="10150-143">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="10150-143">Requirements</span></span>  
 <span data-ttu-id="10150-144">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="10150-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="10150-145">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="10150-145">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="10150-146">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="10150-146">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="10150-147">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="10150-147">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10150-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="10150-148">See also</span></span>

- [<span data-ttu-id="10150-149">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="10150-149">Debugging Interfaces</span></span>](debugging-interfaces.md)
