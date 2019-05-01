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
ms.openlocfilehash: db322bbdc7293410968542d0d22c572edb87795a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61993987"
---
# <a name="icordebugthread-interface"></a><span data-ttu-id="4b09a-102">ICorDebugThread Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4b09a-102">ICorDebugThread Interface</span></span>
<span data-ttu-id="4b09a-103">Bir işlemdeki bir iş parçacığını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="4b09a-103">Represents a thread in a process.</span></span> <span data-ttu-id="4b09a-104">Yaşam süresi bir `ICorDebugThread` örneğidir ömrü, temsil ettiği iş parçacığı ile aynı.</span><span class="sxs-lookup"><span data-stu-id="4b09a-104">The lifetime of an `ICorDebugThread` instance is the same as the lifetime of the thread it represents.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4b09a-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="4b09a-105">Methods</span></span>  
  
|<span data-ttu-id="4b09a-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="4b09a-106">Method</span></span>|<span data-ttu-id="4b09a-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4b09a-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4b09a-108">ClearCurrentException Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4b09a-108">ClearCurrentException Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-clearcurrentexception-method.md)|<span data-ttu-id="4b09a-109">Bu yöntem uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="4b09a-109">This method is not implemented.</span></span> <span data-ttu-id="4b09a-110">Onu kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="4b09a-110">Do not use it.</span></span>|  
|[<span data-ttu-id="4b09a-111">CreateEval Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4b09a-111">CreateEval Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-createeval-method.md)|<span data-ttu-id="4b09a-112">Bu, çalışan Icordebugeval nesne oluşturur `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="4b09a-112">Creates an ICorDebugEval object that operates on this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="4b09a-113">CreateStepper Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4b09a-113">CreateStepper Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-createstepper-method.md)|<span data-ttu-id="4b09a-114">Bu etkin çerçeveye üzerinden Adımlama izin veren bir ICorDebugStepper nesnesi oluşturur `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="4b09a-114">Creates an ICorDebugStepper object that allows stepping through the active frame in this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="4b09a-115">EnumerateChains Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4b09a-115">EnumerateChains Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-enumeratechains-method.md)|<span data-ttu-id="4b09a-116">Bu yığın zincirlerini içeren bir Icordebugchainenum Numaralandırıcı için bir arabirim işaretçisi alır `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="4b09a-116">Gets an interface pointer to an ICorDebugChainEnum enumerator that contains all the stack chains in this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="4b09a-117">GetActiveChain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4b09a-117">GetActiveChain Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getactivechain-method.md)|<span data-ttu-id="4b09a-118">Bu etkin Icordebugchain için bir arabirim işaretçisi alır `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="4b09a-118">Gets an interface pointer to the active ICorDebugChain on this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="4b09a-119">GetActiveFrame Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4b09a-119">GetActiveFrame Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getactiveframe-method.md)|<span data-ttu-id="4b09a-120">Bu etkin Icordebugframe için bir arabirim işaretçisi alır `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="4b09a-120">Gets an interface pointer to the active ICorDebugFrame on this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="4b09a-121">GetAppDomain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4b09a-121">GetAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getappdomain-method.md)|<span data-ttu-id="4b09a-122">Bu uygulama etki alanı için bir arabirim işaretçisi alır `ICorDebugThread` gerçekleştirmektedir.</span><span class="sxs-lookup"><span data-stu-id="4b09a-122">Gets an interface pointer to the application domain in which this `ICorDebugThread` is currently executing.</span></span>|  
|[<span data-ttu-id="4b09a-123">GetCurrentException Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4b09a-123">GetCurrentException Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getcurrentexception-method.md)|<span data-ttu-id="4b09a-124">Şu anda yönetilen kod tarafından oluşturulan bir özel durum temsil eden bir Icordebugvalue nesne için bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="4b09a-124">Gets an interface pointer to an ICorDebugValue object that represents an exception currently being thrown by managed code.</span></span>|  
|[<span data-ttu-id="4b09a-125">GetDebugState Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4b09a-125">GetDebugState Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getdebugstate-method.md)|<span data-ttu-id="4b09a-126">Bu, geçerli hata ayıklama durumunu açıklayan bir CorDebugThreadState değerini alır `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="4b09a-126">Gets a CorDebugThreadState value that describes the current debug state of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="4b09a-127">GetHandle Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4b09a-127">GetHandle Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-gethandle-method.md)|<span data-ttu-id="4b09a-128">Bu, etkin parçası için geçerli bir tanıtıcı alır `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="4b09a-128">Gets the current handle for the active part of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="4b09a-129">GetID Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4b09a-129">GetID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getid-method.md)|<span data-ttu-id="4b09a-130">Bu etkin parçası geçerli işletim sistemi tanımlayıcısını alır `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="4b09a-130">Gets the current operating system identifier of the active part of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="4b09a-131">GetObject Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4b09a-131">GetObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getobject-method.md)|<span data-ttu-id="4b09a-132">Ortak dil çalışma zamanı (CLR) iş parçacığına bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="4b09a-132">Gets an interface pointer to the common language runtime (CLR) thread.</span></span>|  
|[<span data-ttu-id="4b09a-133">GetProcess Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4b09a-133">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getprocess-method.md)|<span data-ttu-id="4b09a-134">Bu işlemi bir arabirim işaretçisi alır `ICorDebugThread` bir bölümünü oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4b09a-134">Gets an interface pointer to the process of which this `ICorDebugThread` forms a part.</span></span>|  
|[<span data-ttu-id="4b09a-135">GetRegisterSet Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4b09a-135">GetRegisterSet Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getregisterset-method.md)|<span data-ttu-id="4b09a-136">Bu ile ilişkilendirilen kayıt kümesi için bir arabirim işaretçisi alır `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="4b09a-136">Gets an interface pointer to the register set associated with this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="4b09a-137">GetUserState Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4b09a-137">GetUserState Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getuserstate-method.md)|<span data-ttu-id="4b09a-138">Bu geçerli durumunu açıklayan CorDebugUserState değerlerinin bit tabanı bir bileşimine alır `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="4b09a-138">Gets a bitwise combination of CorDebugUserState values that describe the current state of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="4b09a-139">SetDebugState Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4b09a-139">SetDebugState Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-setdebugstate-method.md)|<span data-ttu-id="4b09a-140">Bitsel bir birleşimi ayarlar `CorDebugThreadState` bu hata ayıklama durumunu açıklayan değerleri `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="4b09a-140">Sets a bitwise combination of `CorDebugThreadState` values that describe the debugging state of this `ICorDebugThread`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4b09a-141">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4b09a-141">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4b09a-142">Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="4b09a-142">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4b09a-143">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4b09a-143">Requirements</span></span>  
 <span data-ttu-id="4b09a-144">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4b09a-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4b09a-145">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4b09a-145">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4b09a-146">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4b09a-146">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4b09a-147">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4b09a-147">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b09a-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4b09a-148">See also</span></span>

- [<span data-ttu-id="4b09a-149">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="4b09a-149">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
