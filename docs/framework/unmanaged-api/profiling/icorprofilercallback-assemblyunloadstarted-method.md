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
ms.openlocfilehash: 10475831be02bd4a958da84b7b75409cf3ad4097
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33450531"
---
# <a name="icorprofilercallbackassemblyunloadstarted-method"></a><span data-ttu-id="68854-102">ICorProfilerCallback::AssemblyUnloadStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="68854-102">ICorProfilerCallback::AssemblyUnloadStarted Method</span></span>
<span data-ttu-id="68854-103">Profil Oluşturucu bütünleştirilmiş yüklenmemiş olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="68854-103">Notifies the profiler that an assembly is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68854-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="68854-104">Syntax</span></span>  
  
```  
HRESULT AssemblyUnloadStarted(  
    [in] AssemblyID assemblyId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="68854-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="68854-105">Parameters</span></span>  
 `assemblyId`  
 <span data-ttu-id="68854-106">[in] Boşaltılıyor derlemeyi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="68854-106">[in] Identifies the assembly that is being unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="68854-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="68854-107">Remarks</span></span>  
 <span data-ttu-id="68854-108">Değeri `assemblyId` sonra bir bilgi isteği için geçerli değil `AssemblyUnloadStarted` yöntemi döndürür — bu bu derleme hakkında bilgi almak için Profil Oluşturucu'nın son şansınızdır.</span><span class="sxs-lookup"><span data-stu-id="68854-108">The value of `assemblyId` is not valid for an information request after the `AssemblyUnloadStarted` method returns — this is the profiler's last chance to get information about this assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="68854-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="68854-109">Requirements</span></span>  
 <span data-ttu-id="68854-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="68854-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68854-111">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="68854-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="68854-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="68854-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="68854-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="68854-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68854-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="68854-114">See Also</span></span>  
 [<span data-ttu-id="68854-115">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="68854-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="68854-116">AssemblyUnloadFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="68854-116">AssemblyUnloadFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyunloadfinished-method.md)
