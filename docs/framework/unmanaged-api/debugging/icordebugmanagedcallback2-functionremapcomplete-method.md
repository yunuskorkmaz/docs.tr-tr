---
title: ICorDebugManagedCallback2::FunctionRemapComplete Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.FunctionRemapComplete
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::FunctionRemapComplete
helpviewer_keywords:
- FunctionRemapComplete method [.NET Framework debugging]
- ICorDebugManagedCallback2::FunctionRemapComplete method [.NET Framework debugging]
ms.assetid: 5396c4c3-4ec3-4e3a-a38d-d65b21f0a2fc
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4051c3f8300b02581c86642455954615d920c3ba
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33415447"
---
# <a name="icordebugmanagedcallback2functionremapcomplete-method"></a><span data-ttu-id="ef7c7-102">ICorDebugManagedCallback2::FunctionRemapComplete Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ef7c7-102">ICorDebugManagedCallback2::FunctionRemapComplete Method</span></span>
<span data-ttu-id="ef7c7-103">Hata ayıklayıcı kod yürütmeyi düzenlenen işlevi yeni bir sürüme geçirdi bildirir.</span><span class="sxs-lookup"><span data-stu-id="ef7c7-103">Notifies the debugger that code execution has switched to a new version of an edited function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef7c7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ef7c7-104">Syntax</span></span>  
  
```  
HRESULT FunctionRemapComplete (  
    [in] ICorDebugAppDomain   *pAppDomain,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugFunction    *pFunction  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ef7c7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ef7c7-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="ef7c7-106">[in] Bir işaretçi Icordebugappdomain nesneye düzenlenen işlevi içeren uygulama etki alanını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="ef7c7-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the edited function.</span></span>  
  
 `pThread`  
 <span data-ttu-id="ef7c7-107">[in] Bir işaretçi Icordebugthread nesneye eşleme kesme noktası karşılaşıldı iş parçacığı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="ef7c7-107">[in] A pointer to an ICorDebugThread object that represents the thread on which the remap breakpoint was encountered.</span></span>  
  
 `pFunction`  
 <span data-ttu-id="ef7c7-108">[in] Bir işaretçi ICorDebugFunction nesneye iş parçacığı üzerinde çalışmakta işlevi sürümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="ef7c7-108">[in] A pointer to an ICorDebugFunction object that represents the version of the function currently running on the thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ef7c7-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ef7c7-109">Remarks</span></span>  
 <span data-ttu-id="ef7c7-110">Bu geri çağırma hata ayıklayıcı önceden var olan tüm adımlayıcıların yeniden oluşturmak için fırsatı sunar.</span><span class="sxs-lookup"><span data-stu-id="ef7c7-110">This callback gives the debugger an opportunity to recreate any steppers that previously existed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ef7c7-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ef7c7-111">Requirements</span></span>  
 <span data-ttu-id="ef7c7-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ef7c7-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ef7c7-113">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ef7c7-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ef7c7-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ef7c7-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ef7c7-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ef7c7-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef7c7-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ef7c7-116">See Also</span></span>  
 [<span data-ttu-id="ef7c7-117">ICorDebugManagedCallback2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ef7c7-117">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 [<span data-ttu-id="ef7c7-118">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ef7c7-118">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
