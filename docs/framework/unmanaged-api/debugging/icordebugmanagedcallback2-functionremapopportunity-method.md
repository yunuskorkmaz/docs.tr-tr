---
title: "ICorDebugManagedCallback2::FunctionRemapOpportunity Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback2.FunctionRemapOpportunity
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback2::FunctionRemapOpportunity
helpviewer_keywords:
- FunctionRemapOpportunity method [.NET Framework debugging]
- ICorDebugManagedCallback2::FunctionRemapOpportunity method [.NET Framework debugging]
ms.assetid: 0d6471bc-ad9b-4b1d-a307-c10443918863
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8a8360913597dfb5156399a45f86d2cc1a9f453d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmanagedcallback2functionremapopportunity-method"></a><span data-ttu-id="320b2-102">ICorDebugManagedCallback2::FunctionRemapOpportunity Yöntemi</span><span class="sxs-lookup"><span data-stu-id="320b2-102">ICorDebugManagedCallback2::FunctionRemapOpportunity Method</span></span>
<span data-ttu-id="320b2-103">Hata ayıklayıcı kod yürütmeyi bir dizi noktası düzenlenen işlevi daha eski bir sürümünde ulaştı bildirir.</span><span class="sxs-lookup"><span data-stu-id="320b2-103">Notifies the debugger that code execution has reached a sequence point in an older version of an edited function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="320b2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="320b2-104">Syntax</span></span>  
  
```  
HRESULT FunctionRemapOpportunity (  
    [in] ICorDebugAppDomain   *pAppDomain,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugFunction    *pOldFunction,  
    [in] ICorDebugFunction    *pNewFunction,  
    [in] ULONG32              oldILOffset  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="320b2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="320b2-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="320b2-106">[in] Bir işaretçi Icordebugappdomain nesneye düzenlenen işlevi içeren uygulama etki alanını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="320b2-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the edited function.</span></span>  
  
 `pThread`  
 <span data-ttu-id="320b2-107">[in] Bir işaretçi Icordebugthread nesneye eşleme kesme noktası karşılaşıldı iş parçacığı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="320b2-107">[in] A pointer to an ICorDebugThread object that represents the thread on which the remap breakpoint was encountered.</span></span>  
  
 `pOldFunction`  
 <span data-ttu-id="320b2-108">[in] Bir işaretçi ICorDebugFunction nesneye iş parçacığı üzerinde çalışmakta olan işlevi sürümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="320b2-108">[in] A pointer to an ICorDebugFunction object that represents the version of the function that is currently running on the thread.</span></span>  
  
 `pNewFunction`  
 <span data-ttu-id="320b2-109">[in] Bir işaretçi ICorDebugFunction nesneye işlevi, en son sürümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="320b2-109">[in] A pointer to an ICorDebugFunction object that represents the latest version of the function.</span></span>  
  
 `oldILOffset`  
 <span data-ttu-id="320b2-110">[in] Yönerge işaretçisi işlevi eski bir sürümünde Microsoft Ara dili (MSIL) uzaklığı.</span><span class="sxs-lookup"><span data-stu-id="320b2-110">[in] The Microsoft intermediate language (MSIL) offset of the instruction pointer in the old version of the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="320b2-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="320b2-111">Remarks</span></span>  
 <span data-ttu-id="320b2-112">Bu geri çağırma hata ayıklayıcı çağırarak uygun yeni sürümü belirtilen işlev, yerinde yönerge işaretçisine yeniden eşlemek için bir fırsat sunar [Icordebugılframe2::RemapFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-remapfunction-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="320b2-112">This callback gives the debugger an opportunity to remap the instruction pointer to its proper place in the new version of the specified function by calling the [ICorDebugILFrame2::RemapFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-remapfunction-method.md) method.</span></span> <span data-ttu-id="320b2-113">Hata ayıklayıcı değil çağırırsanız `RemapFunction` çağırmadan önce [Icordebugcontroller::continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) yöntemi, çalışma zamanı eski kod yürütülmeye devam eder ve başka ateşlenir `FunctionRemapOpportunity` sonraki dizisi noktasına geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="320b2-113">If the debugger does not call `RemapFunction` before calling the [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) method, the runtime will continue to execute the old code and will fire another `FunctionRemapOpportunity` callback at the next sequence point.</span></span>  
  
 <span data-ttu-id="320b2-114">Bu geri çağırma hata ayıklayıcı S_OK dönene kadar verilen işlev daha eski bir sürümü yürütülen her çerçevesi için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="320b2-114">This callback will be invoked for every frame that is executing an older version of the given function until the debugger returns S_OK.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="320b2-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="320b2-115">Requirements</span></span>  
 <span data-ttu-id="320b2-116">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="320b2-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="320b2-117">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="320b2-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="320b2-118">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="320b2-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="320b2-119">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="320b2-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="320b2-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="320b2-120">See Also</span></span>  
 [<span data-ttu-id="320b2-121">Icordebugmanagedcallback2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="320b2-121">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 [<span data-ttu-id="320b2-122">Icordebugmanagedcallback arabirimi</span><span class="sxs-lookup"><span data-stu-id="320b2-122">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
