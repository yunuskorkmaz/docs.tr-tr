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
ms.openlocfilehash: fcebe65b7f39dd2849946e445a694ad5e9b1a65d
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500487"
---
# <a name="icorprofilercallbackappdomaincreationstarted-method"></a><span data-ttu-id="98aee-102">ICorProfilerCallback::AppDomainCreationStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="98aee-102">ICorProfilerCallback::AppDomainCreationStarted Method</span></span>
<span data-ttu-id="98aee-103">Profil oluşturucuyu bir uygulama etki alanının oluşturulduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="98aee-103">Notifies the profiler that an application domain is being created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98aee-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="98aee-104">Syntax</span></span>  
  
```cpp  
HRESULT AppDomainCreationStarted(  
    [in] AppDomainID appDomainId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="98aee-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="98aee-105">Parameters</span></span>

- `appDomainId`

  <span data-ttu-id="98aee-106">\[' de] oluşturulmakta olan etki alanını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="98aee-106">\[in] Identifies the domain which is being created.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="98aee-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="98aee-107">Remarks</span></span>  
 <span data-ttu-id="98aee-108">ID, [ICorProfilerCallback:: AppDomainCreationFinished](icorprofilercallback-appdomaincreationfinished-method.md) yöntemi çağrılana kadar herhangi bir bilgi isteği için geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="98aee-108">The ID is not valid for any information request until the [ICorProfilerCallback::AppDomainCreationFinished](icorprofilercallback-appdomaincreationfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="98aee-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="98aee-109">Requirements</span></span>  
 <span data-ttu-id="98aee-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="98aee-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98aee-111">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="98aee-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="98aee-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="98aee-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="98aee-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="98aee-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98aee-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="98aee-114">See also</span></span>

- [<span data-ttu-id="98aee-115">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="98aee-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
