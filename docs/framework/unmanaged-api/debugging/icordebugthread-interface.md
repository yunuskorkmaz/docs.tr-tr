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
ms.openlocfilehash: edcc0ebcadc1bd95574b0276bfd0e2d42e5474fd
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379816"
---
# <a name="icordebugthread-interface"></a><span data-ttu-id="9b091-102">ICorDebugThread Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9b091-102">ICorDebugThread Interface</span></span>
<span data-ttu-id="9b091-103">Bir işlemdeki bir iş parçacığını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="9b091-103">Represents a thread in a process.</span></span> <span data-ttu-id="9b091-104">Bir örneğin yaşam süresi, `ICorDebugThread` temsil ettiği iş parçacığının ömrü ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="9b091-104">The lifetime of an `ICorDebugThread` instance is the same as the lifetime of the thread it represents.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9b091-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="9b091-105">Methods</span></span>  
  
|<span data-ttu-id="9b091-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="9b091-106">Method</span></span>|<span data-ttu-id="9b091-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9b091-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9b091-108">ClearCurrentException Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9b091-108">ClearCurrentException Method</span></span>](icordebugthread-clearcurrentexception-method.md)|<span data-ttu-id="9b091-109">Bu yöntem uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="9b091-109">This method is not implemented.</span></span> <span data-ttu-id="9b091-110">Onu kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="9b091-110">Do not use it.</span></span>|  
|[<span data-ttu-id="9b091-111">CreateEval Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9b091-111">CreateEval Method</span></span>](icordebugthread-createeval-method.md)|<span data-ttu-id="9b091-112">Bu, üzerinde çalışan bir ıcorınkıt Geval nesnesi oluşturur `ICorDebugThread` .</span><span class="sxs-lookup"><span data-stu-id="9b091-112">Creates an ICorDebugEval object that operates on this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="9b091-113">CreateStepper Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9b091-113">CreateStepper Method</span></span>](icordebugthread-createstepper-method.md)|<span data-ttu-id="9b091-114">Bu, içindeki etkin çerçeve üzerinde Adımlama sağlayan bir ICorDebugStepper nesnesi oluşturur `ICorDebugThread` .</span><span class="sxs-lookup"><span data-stu-id="9b091-114">Creates an ICorDebugStepper object that allows stepping through the active frame in this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="9b091-115">EnumerateChains Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9b091-115">EnumerateChains Method</span></span>](icordebugthread-enumeratechains-method.md)|<span data-ttu-id="9b091-116">Bu, içindeki tüm yığın zincirlerini içeren ICorDebugChainEnum numaralandırıcısı için bir arabirim işaretçisi alır `ICorDebugThread` .</span><span class="sxs-lookup"><span data-stu-id="9b091-116">Gets an interface pointer to an ICorDebugChainEnum enumerator that contains all the stack chains in this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="9b091-117">GetActiveChain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9b091-117">GetActiveChain Method</span></span>](icordebugthread-getactivechain-method.md)|<span data-ttu-id="9b091-118">Bu, üzerinde etkin ıcordebugzincirine bir arabirim işaretçisi alır `ICorDebugThread` .</span><span class="sxs-lookup"><span data-stu-id="9b091-118">Gets an interface pointer to the active ICorDebugChain on this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="9b091-119">GetActiveFrame Metodu</span><span class="sxs-lookup"><span data-stu-id="9b091-119">GetActiveFrame Method</span></span>](icordebugthread-getactiveframe-method.md)|<span data-ttu-id="9b091-120">Bunun üzerinde etkin ICorDebugFrame 'e bir arabirim işaretçisi alır `ICorDebugThread` .</span><span class="sxs-lookup"><span data-stu-id="9b091-120">Gets an interface pointer to the active ICorDebugFrame on this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="9b091-121">GetAppDomain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9b091-121">GetAppDomain Method</span></span>](icordebugthread-getappdomain-method.md)|<span data-ttu-id="9b091-122">Şu anda yürütülmekte olan uygulama etki alanına bir arabirim işaretçisi alır `ICorDebugThread` .</span><span class="sxs-lookup"><span data-stu-id="9b091-122">Gets an interface pointer to the application domain in which this `ICorDebugThread` is currently executing.</span></span>|  
|[<span data-ttu-id="9b091-123">GetCurrentException Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9b091-123">GetCurrentException Method</span></span>](icordebugthread-getcurrentexception-method.md)|<span data-ttu-id="9b091-124">Yönetilen kod tarafından şu anda oluşturulan bir özel durumu temsil eden ICorDebugValue nesnesine yönelik bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="9b091-124">Gets an interface pointer to an ICorDebugValue object that represents an exception currently being thrown by managed code.</span></span>|  
|[<span data-ttu-id="9b091-125">GetDebugState Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9b091-125">GetDebugState Method</span></span>](icordebugthread-getdebugstate-method.md)|<span data-ttu-id="9b091-126">Bunun geçerli hata ayıklama durumunu açıklayan bir CorDebugThreadState değeri alır `ICorDebugThread` .</span><span class="sxs-lookup"><span data-stu-id="9b091-126">Gets a CorDebugThreadState value that describes the current debug state of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="9b091-127">GetHandle Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9b091-127">GetHandle Method</span></span>](icordebugthread-gethandle-method.md)|<span data-ttu-id="9b091-128">Bu öğesinin etkin bölümü için geçerli tanıtıcıyı alır `ICorDebugThread` .</span><span class="sxs-lookup"><span data-stu-id="9b091-128">Gets the current handle for the active part of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="9b091-129">GetID Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9b091-129">GetID Method</span></span>](icordebugthread-getid-method.md)|<span data-ttu-id="9b091-130">Bu öğesinin etkin bölümünün geçerli işletim sistemi tanımlayıcısını alır `ICorDebugThread` .</span><span class="sxs-lookup"><span data-stu-id="9b091-130">Gets the current operating system identifier of the active part of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="9b091-131">GetObject Metodu</span><span class="sxs-lookup"><span data-stu-id="9b091-131">GetObject Method</span></span>](icordebugthread-getobject-method.md)|<span data-ttu-id="9b091-132">Ortak dil çalışma zamanı (CLR) iş parçacığına bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="9b091-132">Gets an interface pointer to the common language runtime (CLR) thread.</span></span>|  
|[<span data-ttu-id="9b091-133">GetProcess Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9b091-133">GetProcess Method</span></span>](icordebugthread-getprocess-method.md)|<span data-ttu-id="9b091-134">Bu işlemin bir parçasını oluşturan işlem için bir arabirim işaretçisi alır `ICorDebugThread` .</span><span class="sxs-lookup"><span data-stu-id="9b091-134">Gets an interface pointer to the process of which this `ICorDebugThread` forms a part.</span></span>|  
|[<span data-ttu-id="9b091-135">GetRegisterSet Metodu</span><span class="sxs-lookup"><span data-stu-id="9b091-135">GetRegisterSet Method</span></span>](icordebugthread-getregisterset-method.md)|<span data-ttu-id="9b091-136">Bu ile ilişkili kayıt kümesine bir arabirim işaretçisi alır `ICorDebugThread` .</span><span class="sxs-lookup"><span data-stu-id="9b091-136">Gets an interface pointer to the register set associated with this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="9b091-137">GetUserState Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9b091-137">GetUserState Method</span></span>](icordebugthread-getuserstate-method.md)|<span data-ttu-id="9b091-138">Bunun geçerli durumunu tanımlayan CorDebugUserState değerlerinin bit düzeyinde birleşimini alır `ICorDebugThread` .</span><span class="sxs-lookup"><span data-stu-id="9b091-138">Gets a bitwise combination of CorDebugUserState values that describe the current state of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="9b091-139">SetDebugState Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9b091-139">SetDebugState Method</span></span>](icordebugthread-setdebugstate-method.md)|<span data-ttu-id="9b091-140">`CorDebugThreadState`Bunun hata ayıklama durumunu tanımlayan değerlerin bit düzeyinde birleşimini ayarlar `ICorDebugThread` .</span><span class="sxs-lookup"><span data-stu-id="9b091-140">Sets a bitwise combination of `CorDebugThreadState` values that describe the debugging state of this `ICorDebugThread`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9b091-141">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9b091-141">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9b091-142">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="9b091-142">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b091-143">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9b091-143">Requirements</span></span>  
 <span data-ttu-id="9b091-144">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9b091-144">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b091-145">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="9b091-145">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9b091-146">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="9b091-146">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9b091-147">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b091-147">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b091-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9b091-148">See also</span></span>

- [<span data-ttu-id="9b091-149">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="9b091-149">Debugging Interfaces</span></span>](debugging-interfaces.md)
