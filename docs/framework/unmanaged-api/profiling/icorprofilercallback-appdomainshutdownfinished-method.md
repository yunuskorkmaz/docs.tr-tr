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
ms.openlocfilehash: 0851ac33a2bac4fcf727cf09e5225f6b83481b50
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866682"
---
# <a name="icorprofilercallbackappdomainshutdownfinished-method"></a><span data-ttu-id="b1a70-102">ICorProfilerCallback::AppDomainShutdownFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b1a70-102">ICorProfilerCallback::AppDomainShutdownFinished Method</span></span>
<span data-ttu-id="b1a70-103">Profil oluşturucuyu bir uygulama etki alanının bir işlemden kaldırılmış olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="b1a70-103">Notifies the profiler that an application domain has been unloaded from a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1a70-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b1a70-104">Syntax</span></span>  
  
```cpp  
HRESULT AppDomainShutdownFinished(  
    [in] AppDomainID appDomainId,  
    [in] HRESULT     hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b1a70-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b1a70-105">Parameters</span></span>

- `appDomainId`

  <span data-ttu-id="b1a70-106">\[içinde], uygulamanın derlemelerinin depolandığı etki alanını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b1a70-106">\[in] Identifies the domain in which the application's assemblies are stored.</span></span>

- `hrStatus`

  <span data-ttu-id="b1a70-107">\[) uygulama etki alanının başarıyla yüklenip yüklenmediğini gösteren bir HRESULT.</span><span class="sxs-lookup"><span data-stu-id="b1a70-107">\[in] An HRESULT that indicates whether the application domain was unloaded successfully.</span></span>

## <a name="remarks"></a><span data-ttu-id="b1a70-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b1a70-108">Remarks</span></span>  
 <span data-ttu-id="b1a70-109">`appDomainId` değeri, [ICorProfilerCallback:: AppDomainShutdownStarted](icorprofilercallback-appdomainshutdownstarted-method.md) yöntemi döndürüldüğünden bir bilgi isteği için geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="b1a70-109">The value of `appDomainId` is not valid for an information request after the [ICorProfilerCallback::AppDomainShutdownStarted](icorprofilercallback-appdomainshutdownstarted-method.md) method returns.</span></span>  
  
 <span data-ttu-id="b1a70-110">Uygulama etki alanını kaldırma işleminin bazı bölümleri `AppDomainCreationFinished` geri çağrısından sonra devam edebilir.</span><span class="sxs-lookup"><span data-stu-id="b1a70-110">Some parts of unloading the application domain might continue after the `AppDomainCreationFinished` callback.</span></span> <span data-ttu-id="b1a70-111">`hrStatus` HRESULT hatası, bir hatayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="b1a70-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="b1a70-112">Ancak `hrStatus` başarılı bir HRESULT, yalnızca uygulama etki alanını kaldırmayı ilk bölümünün başarılı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="b1a70-112">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the application domain has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1a70-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b1a70-113">Requirements</span></span>  
 <span data-ttu-id="b1a70-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b1a70-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1a70-115">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="b1a70-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b1a70-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="b1a70-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b1a70-117">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1a70-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1a70-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b1a70-118">See also</span></span>

- [<span data-ttu-id="b1a70-119">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b1a70-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
