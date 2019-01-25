---
title: ICorDebugManagedCallback2::FunctionRemapOpportunity Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.FunctionRemapOpportunity
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::FunctionRemapOpportunity
helpviewer_keywords:
- FunctionRemapOpportunity method [.NET Framework debugging]
- ICorDebugManagedCallback2::FunctionRemapOpportunity method [.NET Framework debugging]
ms.assetid: 0d6471bc-ad9b-4b1d-a307-c10443918863
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 86736f885e40e553195cf2a5f84575a5384e6b60
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54564714"
---
# <a name="icordebugmanagedcallback2functionremapopportunity-method"></a><span data-ttu-id="b4b99-102">ICorDebugManagedCallback2::FunctionRemapOpportunity Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b4b99-102">ICorDebugManagedCallback2::FunctionRemapOpportunity Method</span></span>
<span data-ttu-id="b4b99-103">Hata ayıklayıcı, yürütmeyi bir dizi noktası düzenlenmiş bir işlevin daha eski bir sürümünde ulaştı bildirir.</span><span class="sxs-lookup"><span data-stu-id="b4b99-103">Notifies the debugger that code execution has reached a sequence point in an older version of an edited function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4b99-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b4b99-104">Syntax</span></span>  
  
```  
HRESULT FunctionRemapOpportunity (  
    [in] ICorDebugAppDomain   *pAppDomain,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugFunction    *pOldFunction,  
    [in] ICorDebugFunction    *pNewFunction,  
    [in] ULONG32              oldILOffset  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b4b99-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b4b99-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="b4b99-106">[in] İşlev düzenlendi içeren uygulama etki alanını temsil eden bir Icordebugappdomain nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="b4b99-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the edited function.</span></span>  
  
 `pThread`  
 <span data-ttu-id="b4b99-107">[in] Kesme noktası eşleme tespit edildi iş parçacığını temsil eden bir Icordebugthread nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="b4b99-107">[in] A pointer to an ICorDebugThread object that represents the thread on which the remap breakpoint was encountered.</span></span>  
  
 `pOldFunction`  
 <span data-ttu-id="b4b99-108">[in] İş parçacığı üzerinde çalışmakta olan işlevin sürümünü temsil eden bir ICorDebugFunction nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="b4b99-108">[in] A pointer to an ICorDebugFunction object that represents the version of the function that is currently running on the thread.</span></span>  
  
 `pNewFunction`  
 <span data-ttu-id="b4b99-109">[in] İşlevin en son sürümünü temsil eden bir ICorDebugFunction nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="b4b99-109">[in] A pointer to an ICorDebugFunction object that represents the latest version of the function.</span></span>  
  
 `oldILOffset`  
 <span data-ttu-id="b4b99-110">[in] Microsoft Ara dili (MSIL) yönerge işaretçisinin işlevi'nın eski sürümünde uzaklığı.</span><span class="sxs-lookup"><span data-stu-id="b4b99-110">[in] The Microsoft intermediate language (MSIL) offset of the instruction pointer in the old version of the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b4b99-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b4b99-111">Remarks</span></span>  
 <span data-ttu-id="b4b99-112">Bu geri çağırma, hata ayıklayıcı çağırarak uygun onun yerine yeni sürümü, belirtilen işlev için yönerge işaretçisini yeniden eşlemek için bir fırsat sağlar. [Icordebugılframe2::RemapFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-remapfunction-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b4b99-112">This callback gives the debugger an opportunity to remap the instruction pointer to its proper place in the new version of the specified function by calling the [ICorDebugILFrame2::RemapFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-remapfunction-method.md) method.</span></span> <span data-ttu-id="b4b99-113">Hata ayıklayıcı değil çağırırsanız `RemapFunction` çağırmadan önce [Icordebugcontroller::continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) yöntemi, çalışma zamanı, eski kod yürütülmeye devam eder ve başka ateşlenir `FunctionRemapOpportunity` sonraki dizisi noktasına geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="b4b99-113">If the debugger does not call `RemapFunction` before calling the [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) method, the runtime will continue to execute the old code and will fire another `FunctionRemapOpportunity` callback at the next sequence point.</span></span>  
  
 <span data-ttu-id="b4b99-114">Bu geri çağırma, hata ayıklayıcı S_OK döndürür kadar verilen işlevin daha eski bir sürümünü yürüten her karede çağrılır.</span><span class="sxs-lookup"><span data-stu-id="b4b99-114">This callback will be invoked for every frame that is executing an older version of the given function until the debugger returns S_OK.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4b99-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b4b99-115">Requirements</span></span>  
 <span data-ttu-id="b4b99-116">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b4b99-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b4b99-117">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b4b99-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b4b99-118">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b4b99-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b4b99-119">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b4b99-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4b99-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b4b99-120">See also</span></span>
- [<span data-ttu-id="b4b99-121">ICorDebugManagedCallback2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b4b99-121">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="b4b99-122">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b4b99-122">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
