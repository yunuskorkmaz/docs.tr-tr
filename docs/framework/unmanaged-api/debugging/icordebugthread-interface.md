---
description: ': ICorDebugThread arabirimi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 7e16fa2a82a004a5c85d60a278cdd14df6ab2300
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99658834"
---
# <a name="icordebugthread-interface"></a><span data-ttu-id="25338-103">ICorDebugThread Arabirimi</span><span class="sxs-lookup"><span data-stu-id="25338-103">ICorDebugThread Interface</span></span>

<span data-ttu-id="25338-104">Bir işlemdeki bir iş parçacığını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="25338-104">Represents a thread in a process.</span></span> <span data-ttu-id="25338-105">Bir örneğin yaşam süresi, `ICorDebugThread` temsil ettiği iş parçacığının ömrü ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="25338-105">The lifetime of an `ICorDebugThread` instance is the same as the lifetime of the thread it represents.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="25338-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="25338-106">Methods</span></span>  
  
|<span data-ttu-id="25338-107">Yöntem</span><span class="sxs-lookup"><span data-stu-id="25338-107">Method</span></span>|<span data-ttu-id="25338-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="25338-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="25338-109">ClearCurrentException Yöntemi</span><span class="sxs-lookup"><span data-stu-id="25338-109">ClearCurrentException Method</span></span>](icordebugthread-clearcurrentexception-method.md)|<span data-ttu-id="25338-110">Bu yöntem uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="25338-110">This method is not implemented.</span></span> <span data-ttu-id="25338-111">Onu kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="25338-111">Do not use it.</span></span>|  
|[<span data-ttu-id="25338-112">CreateEval Yöntemi</span><span class="sxs-lookup"><span data-stu-id="25338-112">CreateEval Method</span></span>](icordebugthread-createeval-method.md)|<span data-ttu-id="25338-113">Bu, üzerinde çalışan bir ıcorınkıt Geval nesnesi oluşturur `ICorDebugThread` .</span><span class="sxs-lookup"><span data-stu-id="25338-113">Creates an ICorDebugEval object that operates on this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="25338-114">CreateStepper Yöntemi</span><span class="sxs-lookup"><span data-stu-id="25338-114">CreateStepper Method</span></span>](icordebugthread-createstepper-method.md)|<span data-ttu-id="25338-115">Bu, içindeki etkin çerçeve üzerinde Adımlama sağlayan bir ICorDebugStepper nesnesi oluşturur `ICorDebugThread` .</span><span class="sxs-lookup"><span data-stu-id="25338-115">Creates an ICorDebugStepper object that allows stepping through the active frame in this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="25338-116">EnumerateChains Yöntemi</span><span class="sxs-lookup"><span data-stu-id="25338-116">EnumerateChains Method</span></span>](icordebugthread-enumeratechains-method.md)|<span data-ttu-id="25338-117">Bu, içindeki tüm yığın zincirlerini içeren ICorDebugChainEnum numaralandırıcısı için bir arabirim işaretçisi alır `ICorDebugThread` .</span><span class="sxs-lookup"><span data-stu-id="25338-117">Gets an interface pointer to an ICorDebugChainEnum enumerator that contains all the stack chains in this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="25338-118">GetActiveChain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="25338-118">GetActiveChain Method</span></span>](icordebugthread-getactivechain-method.md)|<span data-ttu-id="25338-119">Bu, üzerinde etkin ıcordebugzincirine bir arabirim işaretçisi alır `ICorDebugThread` .</span><span class="sxs-lookup"><span data-stu-id="25338-119">Gets an interface pointer to the active ICorDebugChain on this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="25338-120">GetActiveFrame Metodu</span><span class="sxs-lookup"><span data-stu-id="25338-120">GetActiveFrame Method</span></span>](icordebugthread-getactiveframe-method.md)|<span data-ttu-id="25338-121">Bunun üzerinde etkin ICorDebugFrame 'e bir arabirim işaretçisi alır `ICorDebugThread` .</span><span class="sxs-lookup"><span data-stu-id="25338-121">Gets an interface pointer to the active ICorDebugFrame on this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="25338-122">GetAppDomain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="25338-122">GetAppDomain Method</span></span>](icordebugthread-getappdomain-method.md)|<span data-ttu-id="25338-123">Şu anda yürütülmekte olan uygulama etki alanına bir arabirim işaretçisi alır `ICorDebugThread` .</span><span class="sxs-lookup"><span data-stu-id="25338-123">Gets an interface pointer to the application domain in which this `ICorDebugThread` is currently executing.</span></span>|  
|[<span data-ttu-id="25338-124">GetCurrentException Yöntemi</span><span class="sxs-lookup"><span data-stu-id="25338-124">GetCurrentException Method</span></span>](icordebugthread-getcurrentexception-method.md)|<span data-ttu-id="25338-125">Yönetilen kod tarafından şu anda oluşturulan bir özel durumu temsil eden ICorDebugValue nesnesine yönelik bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="25338-125">Gets an interface pointer to an ICorDebugValue object that represents an exception currently being thrown by managed code.</span></span>|  
|[<span data-ttu-id="25338-126">GetDebugState Yöntemi</span><span class="sxs-lookup"><span data-stu-id="25338-126">GetDebugState Method</span></span>](icordebugthread-getdebugstate-method.md)|<span data-ttu-id="25338-127">Bunun geçerli hata ayıklama durumunu açıklayan bir CorDebugThreadState değeri alır `ICorDebugThread` .</span><span class="sxs-lookup"><span data-stu-id="25338-127">Gets a CorDebugThreadState value that describes the current debug state of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="25338-128">GetHandle Yöntemi</span><span class="sxs-lookup"><span data-stu-id="25338-128">GetHandle Method</span></span>](icordebugthread-gethandle-method.md)|<span data-ttu-id="25338-129">Bu öğesinin etkin bölümü için geçerli tanıtıcıyı alır `ICorDebugThread` .</span><span class="sxs-lookup"><span data-stu-id="25338-129">Gets the current handle for the active part of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="25338-130">GetID Yöntemi</span><span class="sxs-lookup"><span data-stu-id="25338-130">GetID Method</span></span>](icordebugthread-getid-method.md)|<span data-ttu-id="25338-131">Bu öğesinin etkin bölümünün geçerli işletim sistemi tanımlayıcısını alır `ICorDebugThread` .</span><span class="sxs-lookup"><span data-stu-id="25338-131">Gets the current operating system identifier of the active part of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="25338-132">GetObject Metodu</span><span class="sxs-lookup"><span data-stu-id="25338-132">GetObject Method</span></span>](icordebugthread-getobject-method.md)|<span data-ttu-id="25338-133">Ortak dil çalışma zamanı (CLR) iş parçacığına bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="25338-133">Gets an interface pointer to the common language runtime (CLR) thread.</span></span>|  
|[<span data-ttu-id="25338-134">GetProcess Yöntemi</span><span class="sxs-lookup"><span data-stu-id="25338-134">GetProcess Method</span></span>](icordebugthread-getprocess-method.md)|<span data-ttu-id="25338-135">Bu işlemin bir parçasını oluşturan işlem için bir arabirim işaretçisi alır `ICorDebugThread` .</span><span class="sxs-lookup"><span data-stu-id="25338-135">Gets an interface pointer to the process of which this `ICorDebugThread` forms a part.</span></span>|  
|[<span data-ttu-id="25338-136">GetRegisterSet Metodu</span><span class="sxs-lookup"><span data-stu-id="25338-136">GetRegisterSet Method</span></span>](icordebugthread-getregisterset-method.md)|<span data-ttu-id="25338-137">Bu ile ilişkili kayıt kümesine bir arabirim işaretçisi alır `ICorDebugThread` .</span><span class="sxs-lookup"><span data-stu-id="25338-137">Gets an interface pointer to the register set associated with this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="25338-138">GetUserState Yöntemi</span><span class="sxs-lookup"><span data-stu-id="25338-138">GetUserState Method</span></span>](icordebugthread-getuserstate-method.md)|<span data-ttu-id="25338-139">Bunun geçerli durumunu tanımlayan CorDebugUserState değerlerinin bit düzeyinde birleşimini alır `ICorDebugThread` .</span><span class="sxs-lookup"><span data-stu-id="25338-139">Gets a bitwise combination of CorDebugUserState values that describe the current state of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="25338-140">SetDebugState Yöntemi</span><span class="sxs-lookup"><span data-stu-id="25338-140">SetDebugState Method</span></span>](icordebugthread-setdebugstate-method.md)|<span data-ttu-id="25338-141">`CorDebugThreadState`Bunun hata ayıklama durumunu tanımlayan değerlerin bit düzeyinde birleşimini ayarlar `ICorDebugThread` .</span><span class="sxs-lookup"><span data-stu-id="25338-141">Sets a bitwise combination of `CorDebugThreadState` values that describe the debugging state of this `ICorDebugThread`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="25338-142">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="25338-142">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="25338-143">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="25338-143">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25338-144">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="25338-144">Requirements</span></span>  

 <span data-ttu-id="25338-145">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="25338-145">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25338-146">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="25338-146">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="25338-147">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="25338-147">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="25338-148">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25338-148">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25338-149">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="25338-149">See also</span></span>

- [<span data-ttu-id="25338-150">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="25338-150">Debugging Interfaces</span></span>](debugging-interfaces.md)
