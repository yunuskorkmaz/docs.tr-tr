---
title: "ICorProfilerCallback::AssemblyLoadStarted Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.AssemblyLoadStarted
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::AssemblyLoadStarted
helpviewer_keywords:
- ICorProfilerCallback::AssemblyLoadStarted method [.NET Framework profiling]
- AssemblyLoadStarted method [.NET Framework profiling]
ms.assetid: 67e8209d-a0ca-4118-a6e6-c1ee0abc2221
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 48453532177b1e619f4f863e7297345566637d4f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackassemblyloadstarted-method"></a><span data-ttu-id="19fc5-102">ICorProfilerCallback::AssemblyLoadStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="19fc5-102">ICorProfilerCallback::AssemblyLoadStarted Method</span></span>
<span data-ttu-id="19fc5-103">Profil Oluşturucu bütünleştirilmiş yüklendiği bildirir.</span><span class="sxs-lookup"><span data-stu-id="19fc5-103">Notifies the profiler that an assembly is being loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19fc5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="19fc5-104">Syntax</span></span>  
  
```  
HRESULT AssemblyLoadStarted(  
    [in] AssemblyID assemblyId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="19fc5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="19fc5-105">Parameters</span></span>  
 `assemblyId`  
 <span data-ttu-id="19fc5-106">[in] Yüklenmekte derlemeyi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="19fc5-106">[in] Identifies the assembly that is being loaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="19fc5-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="19fc5-107">Remarks</span></span>  
 <span data-ttu-id="19fc5-108">Değeri `assemblyId` kadar bilgi isteği için geçerli değil [Icorprofilercallback::assemblyloadfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyloadfinished-method.md) yöntemi çağrılır.</span><span class="sxs-lookup"><span data-stu-id="19fc5-108">The value of `assemblyId` is not valid for an information request until the [ICorProfilerCallback::AssemblyLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyloadfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="19fc5-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="19fc5-109">Requirements</span></span>  
 <span data-ttu-id="19fc5-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="19fc5-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="19fc5-111">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="19fc5-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="19fc5-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="19fc5-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="19fc5-113">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="19fc5-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19fc5-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="19fc5-114">See Also</span></span>  
 [<span data-ttu-id="19fc5-115">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="19fc5-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
