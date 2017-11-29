---
title: Icordebugthread Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread
helpviewer_keywords: ICorDebugThread interface [.NET Framework debugging]
ms.assetid: 3930fd9b-2bc3-4b72-80a0-b6eeb94d60c6
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 25b5c8f0720402cce56c69394c6fbe2fb70a6177
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugthread-interface1"></a><span data-ttu-id="a1dc0-102">Icordebugthread Interface1</span><span class="sxs-lookup"><span data-stu-id="a1dc0-102">ICorDebugThread Interface1</span></span>
<span data-ttu-id="a1dc0-103">Bir işlemdeki bir iş parçacığını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a1dc0-103">Represents a thread in a process.</span></span> <span data-ttu-id="a1dc0-104">Yaşam süresi bir `ICorDebugThread` örneğidir temsil ettiği iş parçacığı ömrü ile aynı.</span><span class="sxs-lookup"><span data-stu-id="a1dc0-104">The lifetime of an `ICorDebugThread` instance is the same as the lifetime of the thread it represents.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a1dc0-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="a1dc0-105">Methods</span></span>  
  
|<span data-ttu-id="a1dc0-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="a1dc0-106">Method</span></span>|<span data-ttu-id="a1dc0-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a1dc0-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a1dc0-108">ClearCurrentException yöntemi</span><span class="sxs-lookup"><span data-stu-id="a1dc0-108">ClearCurrentException Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-clearcurrentexception-method.md)|<span data-ttu-id="a1dc0-109">Bu yöntem uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="a1dc0-109">This method is not implemented.</span></span> <span data-ttu-id="a1dc0-110">Onu kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="a1dc0-110">Do not use it.</span></span>|  
|[<span data-ttu-id="a1dc0-111">CreateEval yöntemi</span><span class="sxs-lookup"><span data-stu-id="a1dc0-111">CreateEval Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-createeval-method.md)|<span data-ttu-id="a1dc0-112">Bu bilgisayarda çalışır Icordebugeval nesneyi oluşturur `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="a1dc0-112">Creates an ICorDebugEval object that operates on this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="a1dc0-113">CreateStepper yöntemi</span><span class="sxs-lookup"><span data-stu-id="a1dc0-113">CreateStepper Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-createstepper-method.md)|<span data-ttu-id="a1dc0-114">Bu etkin çerçevede doğruluk izin veren bir ICorDebugStepper nesnesi oluşturur `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="a1dc0-114">Creates an ICorDebugStepper object that allows stepping through the active frame in this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="a1dc0-115">EnumerateChains yöntemi</span><span class="sxs-lookup"><span data-stu-id="a1dc0-115">EnumerateChains Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-enumeratechains-method.md)|<span data-ttu-id="a1dc0-116">Arabirim işaretçisi bu tüm yığın zincirleri içeren bir Icordebugchainenum Numaralandırıcı alır `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="a1dc0-116">Gets an interface pointer to an ICorDebugChainEnum enumerator that contains all the stack chains in this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="a1dc0-117">GetActiveChain yöntemi</span><span class="sxs-lookup"><span data-stu-id="a1dc0-117">GetActiveChain Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getactivechain-method.md)|<span data-ttu-id="a1dc0-118">Bu bilgisayarda etkin Icordebugchain arabirimi işaretçisi alır `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="a1dc0-118">Gets an interface pointer to the active ICorDebugChain on this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="a1dc0-119">GetActiveFrame yöntemi</span><span class="sxs-lookup"><span data-stu-id="a1dc0-119">GetActiveFrame Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getactiveframe-method.md)|<span data-ttu-id="a1dc0-120">Bu bilgisayarda etkin Icordebugframe arabirimi işaretçisi alır `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="a1dc0-120">Gets an interface pointer to the active ICorDebugFrame on this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="a1dc0-121">GetAppDomain yöntemi</span><span class="sxs-lookup"><span data-stu-id="a1dc0-121">GetAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getappdomain-method.md)|<span data-ttu-id="a1dc0-122">Bu uygulama etki alanı için bir arabirim işaretçisi alır `ICorDebugThread` gerçekleştirmektedir.</span><span class="sxs-lookup"><span data-stu-id="a1dc0-122">Gets an interface pointer to the application domain in which this `ICorDebugThread` is currently executing.</span></span>|  
|[<span data-ttu-id="a1dc0-123">GetCurrentException yöntemi</span><span class="sxs-lookup"><span data-stu-id="a1dc0-123">GetCurrentException Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getcurrentexception-method.md)|<span data-ttu-id="a1dc0-124">Icordebugvalue nesneye şu anda yönetilen kod tarafından oluşturulan bir özel durum temsil eden bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="a1dc0-124">Gets an interface pointer to an ICorDebugValue object that represents an exception currently being thrown by managed code.</span></span>|  
|[<span data-ttu-id="a1dc0-125">GetDebugState yöntemi</span><span class="sxs-lookup"><span data-stu-id="a1dc0-125">GetDebugState Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getdebugstate-method.md)|<span data-ttu-id="a1dc0-126">Bu geçerli hata ayıklama durumu açıklayan bir CorDebugThreadState değeri alır `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="a1dc0-126">Gets a CorDebugThreadState value that describes the current debug state of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="a1dc0-127">GetHandle yöntemi</span><span class="sxs-lookup"><span data-stu-id="a1dc0-127">GetHandle Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-gethandle-method.md)|<span data-ttu-id="a1dc0-128">Geçerli işleme etkin bir parçası bu alır `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="a1dc0-128">Gets the current handle for the active part of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="a1dc0-129">GetID yöntemi</span><span class="sxs-lookup"><span data-stu-id="a1dc0-129">GetID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getid-method.md)|<span data-ttu-id="a1dc0-130">Bu etkin parçası geçerli işletim sistemi tanımlayıcısını alır `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="a1dc0-130">Gets the current operating system identifier of the active part of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="a1dc0-131">GetObject yöntemi</span><span class="sxs-lookup"><span data-stu-id="a1dc0-131">GetObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getobject-method.md)|<span data-ttu-id="a1dc0-132">Arabirim işaretçisi ortak dil çalışma zamanı (CLR) iş parçacığına alır.</span><span class="sxs-lookup"><span data-stu-id="a1dc0-132">Gets an interface pointer to the common language runtime (CLR) thread.</span></span>|  
|[<span data-ttu-id="a1dc0-133">GetProcess yöntemi</span><span class="sxs-lookup"><span data-stu-id="a1dc0-133">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getprocess-method.md)|<span data-ttu-id="a1dc0-134">Bu işlemin bir arabirim işaretçisi alır `ICorDebugThread` bir bölümünü oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a1dc0-134">Gets an interface pointer to the process of which this `ICorDebugThread` forms a part.</span></span>|  
|[<span data-ttu-id="a1dc0-135">GetRegisterSet yöntemi</span><span class="sxs-lookup"><span data-stu-id="a1dc0-135">GetRegisterSet Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getregisterset-method.md)|<span data-ttu-id="a1dc0-136">Bu ile ilişkilendirilen kayıt kümesi için bir arabirim işaretçisi alır `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="a1dc0-136">Gets an interface pointer to the register set associated with this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="a1dc0-137">GetUserState yöntemi</span><span class="sxs-lookup"><span data-stu-id="a1dc0-137">GetUserState Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getuserstate-method.md)|<span data-ttu-id="a1dc0-138">Bu geçerli durumunu açıklayan CorDebugUserState değerlerin Bitsel bir birleşimi alır `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="a1dc0-138">Gets a bitwise combination of CorDebugUserState values that describe the current state of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="a1dc0-139">SetDebugState yöntemi</span><span class="sxs-lookup"><span data-stu-id="a1dc0-139">SetDebugState Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-setdebugstate-method.md)|<span data-ttu-id="a1dc0-140">Bit düzeyinde bileşimini ayarlar `CorDebugThreadState` bu hata ayıklama durumunu açıklayan değerleri `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="a1dc0-140">Sets a bitwise combination of `CorDebugThreadState` values that describe the debugging state of this `ICorDebugThread`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a1dc0-141">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a1dc0-141">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a1dc0-142">Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="a1dc0-142">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a1dc0-143">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a1dc0-143">Requirements</span></span>  
 <span data-ttu-id="a1dc0-144">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a1dc0-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a1dc0-145">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a1dc0-145">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a1dc0-146">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a1dc0-146">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a1dc0-147">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a1dc0-147">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1dc0-148">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a1dc0-148">See Also</span></span>  
 [<span data-ttu-id="a1dc0-149">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="a1dc0-149">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
