---
title: "ICorProfilerCallback::AppDomainShutdownFinished Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.AppDomainShutdownFinished
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::AppDomainShutdownFinished
helpviewer_keywords:
- AppDomainShutdownFinished method [.NET Framework profiling]
- ICorProfilerCallback::AppDomainShutdownFinished method [.NET Framework profiling]
ms.assetid: 52794819-0a59-4bb1-a265-0f158cd5cd65
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 443f5cd48693d6ac3ce732746666bd2d5e3786fe
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallbackappdomainshutdownfinished-method"></a><span data-ttu-id="fb255-102">ICorProfilerCallback::AppDomainShutdownFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fb255-102">ICorProfilerCallback::AppDomainShutdownFinished Method</span></span>
<span data-ttu-id="fb255-103">Profil Oluşturucu uygulama etki alanı bir işlemden kaldırıldı bildirir.</span><span class="sxs-lookup"><span data-stu-id="fb255-103">Notifies the profiler that an application domain has been unloaded from a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb255-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fb255-104">Syntax</span></span>  
  
```  
HRESULT AppDomainShutdownFinished(  
    [in] AppDomainID appDomainId,  
    [in] HRESULT     hrStatus);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fb255-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fb255-105">Parameters</span></span>  
 `appDomainId`  
 <span data-ttu-id="fb255-106">[in] Uygulamanın derlemelerini depolandığı etki alanını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="fb255-106">[in] Identifies the domain in which the application's assemblies are stored.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="fb255-107">[in] Uygulama etki alanı başarıyla kaldırıldı olup olmadığını gösteren bir HRESULT.</span><span class="sxs-lookup"><span data-stu-id="fb255-107">[in] An HRESULT that indicates whether the application domain was unloaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fb255-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fb255-108">Remarks</span></span>  
 <span data-ttu-id="fb255-109">Değeri `appDomainId` sonra bir bilgi isteği için geçerli değil [Icorprofilercallback::appdomainshutdownstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomainshutdownstarted-method.md) yöntemi döndürür.</span><span class="sxs-lookup"><span data-stu-id="fb255-109">The value of `appDomainId` is not valid for an information request after the [ICorProfilerCallback::AppDomainShutdownStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomainshutdownstarted-method.md) method returns.</span></span>  
  
 <span data-ttu-id="fb255-110">Uygulama etki alanı kaldırılması, bazı bölümleri sonra devam edebilir `AppDomainCreationFinished` geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="fb255-110">Some parts of unloading the application domain might continue after the `AppDomainCreationFinished` callback.</span></span> <span data-ttu-id="fb255-111">HRESULT hata içinde `hrStatus` hata gösterir.</span><span class="sxs-lookup"><span data-stu-id="fb255-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="fb255-112">Ancak, bir başarı HRESULT içinde `hrStatus` yalnızca ilk uygulama etki alanı kaldırılması parçası başarılı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="fb255-112">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the application domain has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb255-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fb255-113">Requirements</span></span>  
 <span data-ttu-id="fb255-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fb255-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb255-115">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="fb255-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fb255-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fb255-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fb255-117">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fb255-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb255-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fb255-118">See Also</span></span>  
 [<span data-ttu-id="fb255-119">Icorprofilercallback arabirimi</span><span class="sxs-lookup"><span data-stu-id="fb255-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
