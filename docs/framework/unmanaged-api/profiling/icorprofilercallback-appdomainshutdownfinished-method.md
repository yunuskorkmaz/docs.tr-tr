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
ms.openlocfilehash: ddb2d6eeb75a118a12f681b354f6feccd1231c64
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95685397"
---
# <a name="icorprofilercallbackappdomainshutdownfinished-method"></a><span data-ttu-id="16c73-102">ICorProfilerCallback::AppDomainShutdownFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="16c73-102">ICorProfilerCallback::AppDomainShutdownFinished Method</span></span>

<span data-ttu-id="16c73-103">Profil oluşturucuyu bir uygulama etki alanının bir işlemden kaldırılmış olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="16c73-103">Notifies the profiler that an application domain has been unloaded from a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16c73-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="16c73-104">Syntax</span></span>  
  
```cpp  
HRESULT AppDomainShutdownFinished(  
    [in] AppDomainID appDomainId,  
    [in] HRESULT     hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="16c73-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="16c73-105">Parameters</span></span>

- `appDomainId`

  <span data-ttu-id="16c73-106">\[' de], uygulamanın derlemelerinin depolandığı etki alanını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="16c73-106">\[in] Identifies the domain in which the application's assemblies are stored.</span></span>

- `hrStatus`

  <span data-ttu-id="16c73-107">\[içinde] uygulama etki alanının başarıyla yüklenip yüklenmediğini gösteren bir HRESULT.</span><span class="sxs-lookup"><span data-stu-id="16c73-107">\[in] An HRESULT that indicates whether the application domain was unloaded successfully.</span></span>

## <a name="remarks"></a><span data-ttu-id="16c73-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="16c73-108">Remarks</span></span>  

 <span data-ttu-id="16c73-109">Değeri, `appDomainId` [ICorProfilerCallback:: AppDomainShutdownStarted](icorprofilercallback-appdomainshutdownstarted-method.md) yönteminin döndürdüğü bir bilgi isteği için geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="16c73-109">The value of `appDomainId` is not valid for an information request after the [ICorProfilerCallback::AppDomainShutdownStarted](icorprofilercallback-appdomainshutdownstarted-method.md) method returns.</span></span>  
  
 <span data-ttu-id="16c73-110">Uygulama etki alanını kaldırma işleminin bazı bölümleri geri aramadan sonra devam edebilir `AppDomainCreationFinished` .</span><span class="sxs-lookup"><span data-stu-id="16c73-110">Some parts of unloading the application domain might continue after the `AppDomainCreationFinished` callback.</span></span> <span data-ttu-id="16c73-111">' De HRESULT hatası, `hrStatus` bir hatayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="16c73-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="16c73-112">Ancak, içinde başarılı bir HRESULT, `hrStatus` yalnızca uygulama etki alanını kaldırmayı ilk bölümünün başarılı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="16c73-112">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the application domain has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="16c73-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="16c73-113">Requirements</span></span>  

 <span data-ttu-id="16c73-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="16c73-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="16c73-115">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="16c73-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="16c73-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="16c73-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="16c73-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="16c73-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16c73-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="16c73-118">See also</span></span>

- [<span data-ttu-id="16c73-119">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="16c73-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
