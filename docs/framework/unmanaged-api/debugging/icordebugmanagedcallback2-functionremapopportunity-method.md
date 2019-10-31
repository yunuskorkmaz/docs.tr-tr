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
ms.openlocfilehash: c6c361113a441df050a8e7cd5219819cc8332581
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131490"
---
# <a name="icordebugmanagedcallback2functionremapopportunity-method"></a><span data-ttu-id="67a15-102">ICorDebugManagedCallback2::FunctionRemapOpportunity Yöntemi</span><span class="sxs-lookup"><span data-stu-id="67a15-102">ICorDebugManagedCallback2::FunctionRemapOpportunity Method</span></span>
<span data-ttu-id="67a15-103">Kod yürütmenin, düzenlenmiş bir işlevin daha eski bir sürümündeki bir sıra noktasına ulaştığı hata ayıklayıcıya bildirir.</span><span class="sxs-lookup"><span data-stu-id="67a15-103">Notifies the debugger that code execution has reached a sequence point in an older version of an edited function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67a15-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="67a15-104">Syntax</span></span>  
  
```cpp  
HRESULT FunctionRemapOpportunity (  
    [in] ICorDebugAppDomain   *pAppDomain,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugFunction    *pOldFunction,  
    [in] ICorDebugFunction    *pNewFunction,  
    [in] ULONG32              oldILOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="67a15-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="67a15-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="67a15-106">'ndaki Düzenlenen işlevi içeren uygulama etki alanını temsil eden ICorDebugAppDomain nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="67a15-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the edited function.</span></span>  
  
 `pThread`  
 <span data-ttu-id="67a15-107">'ndaki Yeniden eşleme kesme noktasının karşılaştığı iş parçacığını temsil eden ICorDebugThread nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="67a15-107">[in] A pointer to an ICorDebugThread object that represents the thread on which the remap breakpoint was encountered.</span></span>  
  
 `pOldFunction`  
 <span data-ttu-id="67a15-108">'ndaki İş parçacığında çalışmakta olan işlevin sürümünü temsil eden ICorDebugFunction nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="67a15-108">[in] A pointer to an ICorDebugFunction object that represents the version of the function that is currently running on the thread.</span></span>  
  
 `pNewFunction`  
 <span data-ttu-id="67a15-109">'ndaki İşlevin en son sürümünü temsil eden ICorDebugFunction nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="67a15-109">[in] A pointer to an ICorDebugFunction object that represents the latest version of the function.</span></span>  
  
 `oldILOffset`  
 <span data-ttu-id="67a15-110">'ndaki İşlevin eski sürümündeki yönerge işaretçisinin Microsoft ara dili (MSIL) boşluğu.</span><span class="sxs-lookup"><span data-stu-id="67a15-110">[in] The Microsoft intermediate language (MSIL) offset of the instruction pointer in the old version of the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="67a15-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="67a15-111">Remarks</span></span>  
 <span data-ttu-id="67a15-112">Bu geri çağırma, [ICorDebugILFrame2:: RemapFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-remapfunction-method.md) metodunu çağırarak, yönerge işaretçisini belirtilen işlevin yeni sürümünde doğru yere yeniden eşlemek için bir fırsat sağlar.</span><span class="sxs-lookup"><span data-stu-id="67a15-112">This callback gives the debugger an opportunity to remap the instruction pointer to its proper place in the new version of the specified function by calling the [ICorDebugILFrame2::RemapFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-remapfunction-method.md) method.</span></span> <span data-ttu-id="67a15-113">Hata ayıklayıcı [ICorDebugController:: Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) metodunu çağırmadan önce `RemapFunction` çağırmadığından, çalışma zamanı eski kodu yürütmeye devam eder ve bir sonraki dizi noktasında başka bir `FunctionRemapOpportunity` geri çağırma işlemini harekete geçmeyecektir.</span><span class="sxs-lookup"><span data-stu-id="67a15-113">If the debugger does not call `RemapFunction` before calling the [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) method, the runtime will continue to execute the old code and will fire another `FunctionRemapOpportunity` callback at the next sequence point.</span></span>  
  
 <span data-ttu-id="67a15-114">Bu geri çağırma, belirtilen işlevin daha eski bir sürümünü yürüten her çerçeve için, hata ayıklayıcısı S_OK döndürene kadar çağrılacaktır.</span><span class="sxs-lookup"><span data-stu-id="67a15-114">This callback will be invoked for every frame that is executing an older version of the given function until the debugger returns S_OK.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="67a15-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="67a15-115">Requirements</span></span>  
 <span data-ttu-id="67a15-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="67a15-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="67a15-117">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="67a15-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="67a15-118">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="67a15-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="67a15-119">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="67a15-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67a15-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="67a15-120">See also</span></span>

- [<span data-ttu-id="67a15-121">ICorDebugManagedCallback2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="67a15-121">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="67a15-122">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="67a15-122">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
