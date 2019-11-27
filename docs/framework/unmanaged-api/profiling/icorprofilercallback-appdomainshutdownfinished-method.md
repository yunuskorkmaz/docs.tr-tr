---
title: ICorProfilerCallback::AppDomainShutdownFinished Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AppDomainShutdownFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AppDomainShutdownFinished
helpviewer_keywords:
- AppDomainShutdownFinished method [.NET Framework profiling]
- ICorProfilerCallback::AppDomainShutdownFinished method [.NET Framework profiling]
ms.assetid: 52794819-0a59-4bb1-a265-0f158cd5cd65
topic_type:
- apiref
ms.openlocfilehash: 8ff7d5a593388bd3a584e031aea411dfdb6c9845
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445205"
---
# <a name="icorprofilercallbackappdomainshutdownfinished-method"></a><span data-ttu-id="e5a65-102">ICorProfilerCallback::AppDomainShutdownFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e5a65-102">ICorProfilerCallback::AppDomainShutdownFinished Method</span></span>
<span data-ttu-id="e5a65-103">Profil oluşturucuyu bir uygulama etki alanının bir işlemden kaldırılmış olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="e5a65-103">Notifies the profiler that an application domain has been unloaded from a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5a65-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e5a65-104">Syntax</span></span>  
  
```cpp  
HRESULT AppDomainShutdownFinished(  
    [in] AppDomainID appDomainId,  
    [in] HRESULT     hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e5a65-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e5a65-105">Parameters</span></span>  
 `appDomainId`  
 <span data-ttu-id="e5a65-106">'ndaki Uygulamanın derlemelerinin depolandığı etki alanını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e5a65-106">[in] Identifies the domain in which the application's assemblies are stored.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="e5a65-107">'ndaki Uygulama etki alanının başarıyla yüklenip yüklenmediğini gösteren bir HRESULT.</span><span class="sxs-lookup"><span data-stu-id="e5a65-107">[in] An HRESULT that indicates whether the application domain was unloaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e5a65-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e5a65-108">Remarks</span></span>  
 <span data-ttu-id="e5a65-109">`appDomainId` değeri, [ICorProfilerCallback:: AppDomainShutdownStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomainshutdownstarted-method.md) yöntemi döndürüldüğünden bir bilgi isteği için geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="e5a65-109">The value of `appDomainId` is not valid for an information request after the [ICorProfilerCallback::AppDomainShutdownStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomainshutdownstarted-method.md) method returns.</span></span>  
  
 <span data-ttu-id="e5a65-110">Uygulama etki alanını kaldırma işleminin bazı bölümleri `AppDomainCreationFinished` geri çağrısından sonra devam edebilir.</span><span class="sxs-lookup"><span data-stu-id="e5a65-110">Some parts of unloading the application domain might continue after the `AppDomainCreationFinished` callback.</span></span> <span data-ttu-id="e5a65-111">`hrStatus` HRESULT hatası, bir hatayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="e5a65-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="e5a65-112">Ancak `hrStatus` başarılı bir HRESULT, yalnızca uygulama etki alanını kaldırmayı ilk bölümünün başarılı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="e5a65-112">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the application domain has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5a65-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e5a65-113">Requirements</span></span>  
 <span data-ttu-id="e5a65-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e5a65-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5a65-115">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="e5a65-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e5a65-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e5a65-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e5a65-117">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e5a65-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5a65-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e5a65-118">See also</span></span>

- [<span data-ttu-id="e5a65-119">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e5a65-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
