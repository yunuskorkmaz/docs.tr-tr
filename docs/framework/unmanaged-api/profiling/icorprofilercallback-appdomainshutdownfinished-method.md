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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c89a7671cde9e519d0fc66751ee8f95b34fe9039
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54669672"
---
# <a name="icorprofilercallbackappdomainshutdownfinished-method"></a><span data-ttu-id="ecd12-102">ICorProfilerCallback::AppDomainShutdownFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ecd12-102">ICorProfilerCallback::AppDomainShutdownFinished Method</span></span>
<span data-ttu-id="ecd12-103">Profil Oluşturucu, bir uygulama etki alanı bir işlemden olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="ecd12-103">Notifies the profiler that an application domain has been unloaded from a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ecd12-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ecd12-104">Syntax</span></span>  
  
```  
HRESULT AppDomainShutdownFinished(  
    [in] AppDomainID appDomainId,  
    [in] HRESULT     hrStatus);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ecd12-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ecd12-105">Parameters</span></span>  
 `appDomainId`  
 <span data-ttu-id="ecd12-106">[in] Uygulamanın derlemelerin saklandığı etki alanını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ecd12-106">[in] Identifies the domain in which the application's assemblies are stored.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="ecd12-107">[in] Uygulama etki alanı başarıyla kaldırılmış olup olmadığını gösteren bir HRESULT.</span><span class="sxs-lookup"><span data-stu-id="ecd12-107">[in] An HRESULT that indicates whether the application domain was unloaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ecd12-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ecd12-108">Remarks</span></span>  
 <span data-ttu-id="ecd12-109">Değerini `appDomainId` sonra bir bilgi isteği için geçerli değil [Icorprofilercallback::appdomainshutdownstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomainshutdownstarted-method.md) yöntemi döndürür.</span><span class="sxs-lookup"><span data-stu-id="ecd12-109">The value of `appDomainId` is not valid for an information request after the [ICorProfilerCallback::AppDomainShutdownStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomainshutdownstarted-method.md) method returns.</span></span>  
  
 <span data-ttu-id="ecd12-110">Uygulama etki alanı kaldırılması, bazı bölümleri sonra devam edebilir `AppDomainCreationFinished` geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="ecd12-110">Some parts of unloading the application domain might continue after the `AppDomainCreationFinished` callback.</span></span> <span data-ttu-id="ecd12-111">Bir hata HRESULT içinde `hrStatus` hata gösterir.</span><span class="sxs-lookup"><span data-stu-id="ecd12-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="ecd12-112">Ancak, bir başarı HRESULT içinde `hrStatus` yalnızca ilk bölümü, uygulama etki alanını kaldırma işleminin başarılı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="ecd12-112">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the application domain has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ecd12-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ecd12-113">Requirements</span></span>  
 <span data-ttu-id="ecd12-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ecd12-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ecd12-115">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ecd12-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ecd12-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ecd12-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ecd12-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ecd12-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecd12-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ecd12-118">See also</span></span>
- [<span data-ttu-id="ecd12-119">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ecd12-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
