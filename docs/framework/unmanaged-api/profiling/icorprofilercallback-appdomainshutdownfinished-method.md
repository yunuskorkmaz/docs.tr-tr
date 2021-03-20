---
description: ': ICorProfilerCallback:: AppDomainShutdownFinished yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 8cd45f73741bd26cb54fa85d7d6a186ebaeab5d8
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2021
ms.locfileid: "104760697"
---
# <a name="icorprofilercallbackappdomainshutdownfinished-method"></a><span data-ttu-id="8eb7d-103">ICorProfilerCallback::AppDomainShutdownFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8eb7d-103">ICorProfilerCallback::AppDomainShutdownFinished Method</span></span>

<span data-ttu-id="8eb7d-104">Profil oluşturucuyu bir uygulama etki alanının bir işlemden kaldırılmış olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="8eb7d-104">Notifies the profiler that an application domain has been unloaded from a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8eb7d-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8eb7d-105">Syntax</span></span>  
  
```cpp  
HRESULT AppDomainShutdownFinished(  
    [in] AppDomainID appDomainId,  
    [in] HRESULT     hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8eb7d-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8eb7d-106">Parameters</span></span>

<span data-ttu-id="8eb7d-107">`appDomainId` 'ndaki Uygulamanın derlemelerinin depolandığı etki alanını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="8eb7d-107">`appDomainId` [in] Identifies the domain in which the application's assemblies are stored.</span></span>

<span data-ttu-id="8eb7d-108">`hrStatus` 'ndaki Uygulama etki alanının başarıyla yüklenip yüklenmediğini gösteren bir HRESULT.</span><span class="sxs-lookup"><span data-stu-id="8eb7d-108">`hrStatus` [in] An HRESULT that indicates whether the application domain was unloaded successfully.</span></span>

## <a name="remarks"></a><span data-ttu-id="8eb7d-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8eb7d-109">Remarks</span></span>  

 <span data-ttu-id="8eb7d-110">Değeri, `appDomainId` [ICorProfilerCallback:: AppDomainShutdownStarted](icorprofilercallback-appdomainshutdownstarted-method.md) yönteminin döndürdüğü bir bilgi isteği için geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="8eb7d-110">The value of `appDomainId` is not valid for an information request after the [ICorProfilerCallback::AppDomainShutdownStarted](icorprofilercallback-appdomainshutdownstarted-method.md) method returns.</span></span>  
  
 <span data-ttu-id="8eb7d-111">Uygulama etki alanını kaldırma işleminin bazı bölümleri geri aramadan sonra devam edebilir `AppDomainCreationFinished` .</span><span class="sxs-lookup"><span data-stu-id="8eb7d-111">Some parts of unloading the application domain might continue after the `AppDomainCreationFinished` callback.</span></span> <span data-ttu-id="8eb7d-112">' De HRESULT hatası, `hrStatus` bir hatayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="8eb7d-112">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="8eb7d-113">Ancak, içinde başarılı bir HRESULT, `hrStatus` yalnızca uygulama etki alanını kaldırmayı ilk bölümünün başarılı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="8eb7d-113">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the application domain has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8eb7d-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8eb7d-114">Requirements</span></span>  

 <span data-ttu-id="8eb7d-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8eb7d-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8eb7d-116">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="8eb7d-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8eb7d-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="8eb7d-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8eb7d-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8eb7d-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8eb7d-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8eb7d-119">See also</span></span>

- [<span data-ttu-id="8eb7d-120">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8eb7d-120">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
