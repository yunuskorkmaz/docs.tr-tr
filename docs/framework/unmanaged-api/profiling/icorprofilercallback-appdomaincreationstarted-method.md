---
title: ICorProfilerCallback::AppDomainCreationStarted Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AppDomainCreationStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AppDomainCreationStarted
helpviewer_keywords:
- AppDomainCreationStarted method [.NET Framework profiling]
- ICorProfilerCallback::AppDomainCreationStarted method [.NET Framework profiling]
ms.assetid: b2a8240b-07fe-4859-bb2b-7d3adbfa0a9f
topic_type:
- apiref
ms.openlocfilehash: 901546c80c3bee32afddfa8e8cffbd2b679bc43b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95685402"
---
# <a name="icorprofilercallbackappdomaincreationstarted-method"></a><span data-ttu-id="077c8-102">ICorProfilerCallback::AppDomainCreationStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="077c8-102">ICorProfilerCallback::AppDomainCreationStarted Method</span></span>

<span data-ttu-id="077c8-103">Profil oluşturucuyu bir uygulama etki alanının oluşturulduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="077c8-103">Notifies the profiler that an application domain is being created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="077c8-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="077c8-104">Syntax</span></span>  
  
```cpp  
HRESULT AppDomainCreationStarted(  
    [in] AppDomainID appDomainId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="077c8-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="077c8-105">Parameters</span></span>

- `appDomainId`

  <span data-ttu-id="077c8-106">\[' de] oluşturulmakta olan etki alanını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="077c8-106">\[in] Identifies the domain which is being created.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="077c8-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="077c8-107">Remarks</span></span>  

 <span data-ttu-id="077c8-108">ID, [ICorProfilerCallback:: AppDomainCreationFinished](icorprofilercallback-appdomaincreationfinished-method.md) yöntemi çağrılana kadar herhangi bir bilgi isteği için geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="077c8-108">The ID is not valid for any information request until the [ICorProfilerCallback::AppDomainCreationFinished](icorprofilercallback-appdomaincreationfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="077c8-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="077c8-109">Requirements</span></span>  

 <span data-ttu-id="077c8-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="077c8-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="077c8-111">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="077c8-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="077c8-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="077c8-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="077c8-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="077c8-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="077c8-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="077c8-114">See also</span></span>

- [<span data-ttu-id="077c8-115">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="077c8-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
