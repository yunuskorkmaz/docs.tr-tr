---
title: "ICorProfilerCallback::AssemblyUnloadStarted Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.AssemblyUnloadStarted
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::AssemblyUnloadStarted
helpviewer_keywords:
- ICorProfilerCallback::AssemblyUnloadStarted method [.NET Framework profiling]
- AssemblyUnloadStarted method [.NET Framework profiling]
ms.assetid: 6e47b7e5-0335-4dd3-8c42-d3c07d62b102
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9984cff1d3c4013d66bc9eb7dbe5dbe7b61d2ba3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackassemblyunloadstarted-method"></a><span data-ttu-id="65ec4-102">ICorProfilerCallback::AssemblyUnloadStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="65ec4-102">ICorProfilerCallback::AssemblyUnloadStarted Method</span></span>
<span data-ttu-id="65ec4-103">Profil Oluşturucu bütünleştirilmiş yüklenmemiş olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="65ec4-103">Notifies the profiler that an assembly is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65ec4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="65ec4-104">Syntax</span></span>  
  
```  
HRESULT AssemblyUnloadStarted(  
    [in] AssemblyID assemblyId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="65ec4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="65ec4-105">Parameters</span></span>  
 `assemblyId`  
 <span data-ttu-id="65ec4-106">[in] Boşaltılıyor derlemeyi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="65ec4-106">[in] Identifies the assembly that is being unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="65ec4-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="65ec4-107">Remarks</span></span>  
 <span data-ttu-id="65ec4-108">Değeri `assemblyId` sonra bir bilgi isteği için geçerli değil `AssemblyUnloadStarted` yöntemi döndürür — bu bu derleme hakkında bilgi almak için Profil Oluşturucu'nın son şansınızdır.</span><span class="sxs-lookup"><span data-stu-id="65ec4-108">The value of `assemblyId` is not valid for an information request after the `AssemblyUnloadStarted` method returns — this is the profiler's last chance to get information about this assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65ec4-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="65ec4-109">Requirements</span></span>  
 <span data-ttu-id="65ec4-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65ec4-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65ec4-111">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="65ec4-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="65ec4-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="65ec4-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="65ec4-113">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65ec4-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65ec4-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="65ec4-114">See Also</span></span>  
 [<span data-ttu-id="65ec4-115">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="65ec4-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="65ec4-116">AssemblyUnloadFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="65ec4-116">AssemblyUnloadFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyunloadfinished-method.md)
