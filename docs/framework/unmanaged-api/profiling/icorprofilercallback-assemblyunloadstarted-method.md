---
title: ICorProfilerCallback::AssemblyUnloadStarted Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AssemblyUnloadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AssemblyUnloadStarted
helpviewer_keywords:
- ICorProfilerCallback::AssemblyUnloadStarted method [.NET Framework profiling]
- AssemblyUnloadStarted method [.NET Framework profiling]
ms.assetid: 6e47b7e5-0335-4dd3-8c42-d3c07d62b102
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3a45c757a9176c77c7dbf58333b66d9b26514265
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57471220"
---
# <a name="icorprofilercallbackassemblyunloadstarted-method"></a><span data-ttu-id="b9b44-102">ICorProfilerCallback::AssemblyUnloadStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b9b44-102">ICorProfilerCallback::AssemblyUnloadStarted Method</span></span>
<span data-ttu-id="b9b44-103">Profil Oluşturucu, bir derleme boşaltılıyor bildirir.</span><span class="sxs-lookup"><span data-stu-id="b9b44-103">Notifies the profiler that an assembly is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9b44-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b9b44-104">Syntax</span></span>  
  
```  
HRESULT AssemblyUnloadStarted(  
    [in] AssemblyID assemblyId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b9b44-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b9b44-105">Parameters</span></span>  
 `assemblyId`  
 <span data-ttu-id="b9b44-106">[in] Boşaltılıyor derlemeyi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b9b44-106">[in] Identifies the assembly that is being unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b9b44-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b9b44-107">Remarks</span></span>  
 <span data-ttu-id="b9b44-108">Değerini `assemblyId` sonra bir bilgi isteği için geçerli değil `AssemblyUnloadStarted` yöntemi döndürür; bu derleme hakkında bilgi almak için profil oluşturucu son şans budur.</span><span class="sxs-lookup"><span data-stu-id="b9b44-108">The value of `assemblyId` is not valid for an information request after the `AssemblyUnloadStarted` method returns — this is the profiler's last chance to get information about this assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b9b44-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b9b44-109">Requirements</span></span>  
 <span data-ttu-id="b9b44-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b9b44-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9b44-111">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b9b44-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b9b44-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b9b44-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b9b44-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b9b44-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9b44-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b9b44-114">See also</span></span>
- [<span data-ttu-id="b9b44-115">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b9b44-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="b9b44-116">AssemblyUnloadFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b9b44-116">AssemblyUnloadFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyunloadfinished-method.md)
