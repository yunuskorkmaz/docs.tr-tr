---
title: ICorProfilerCallback::AssemblyUnloadFinished Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AssemblyUnloadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AssemblyUnloadFinished
helpviewer_keywords:
- AssemblyUnloadFinished method [.NET Framework profiling]
- ICorProfilerCallback::AssemblyUnloadFinished method [.NET Framework profiling]
ms.assetid: 53fca564-84b1-44d4-9e21-17a492d2aae7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0d757a0455992bc82ead922a5fbf4c71f11a9085
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33450875"
---
# <a name="icorprofilercallbackassemblyunloadfinished-method"></a><span data-ttu-id="624e4-102">ICorProfilerCallback::AssemblyUnloadFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="624e4-102">ICorProfilerCallback::AssemblyUnloadFinished Method</span></span>
<span data-ttu-id="624e4-103">Profil Oluşturucu bütünleştirilmiş kaldırıldı bildirir.</span><span class="sxs-lookup"><span data-stu-id="624e4-103">Notifies the profiler that an assembly has been unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="624e4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="624e4-104">Syntax</span></span>  
  
```  
HRESULT AssemblyUnloadFinished(  
    [in] AssemblyID assemblyId,  
    [in] HRESULT    hrStatus);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="624e4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="624e4-105">Parameters</span></span>  
 `assemblyId`  
 <span data-ttu-id="624e4-106">[in] Boşaltılıyor derlemeyi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="624e4-106">[in] Identifies the assembly that is being unloaded.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="624e4-107">[in] Derleme başarıyla kaldırıldı olup olmadığını gösteren bir HRESULT.</span><span class="sxs-lookup"><span data-stu-id="624e4-107">[in] An HRESULT that indicates whether the assembly was unloaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="624e4-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="624e4-108">Remarks</span></span>  
 <span data-ttu-id="624e4-109">Değeri `assemblyId` sonra bir bilgi isteği için geçerli değil [Icorprofilercallback::assemblyunloadstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyunloadstarted-method.md) yöntemi döndürür.</span><span class="sxs-lookup"><span data-stu-id="624e4-109">The value of `assemblyId` is not valid for an information request after the [ICorProfilerCallback::AssemblyUnloadStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyunloadstarted-method.md) method returns.</span></span>  
  
 <span data-ttu-id="624e4-110">Derleme kaldırılması, bazı bölümleri sonra devam edebilir `AssemblyUnloadFinished` geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="624e4-110">Some parts of unloading the assembly might continue after the `AssemblyUnloadFinished` callback.</span></span> <span data-ttu-id="624e4-111">HRESULT hata içinde `hrStatus` hata gösterir.</span><span class="sxs-lookup"><span data-stu-id="624e4-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="624e4-112">Ancak, bir başarı HRESULT içinde `hrStatus` yalnızca derleme kaldırılması ilk parçası başarılı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="624e4-112">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the assembly has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="624e4-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="624e4-113">Requirements</span></span>  
 <span data-ttu-id="624e4-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="624e4-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="624e4-115">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="624e4-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="624e4-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="624e4-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="624e4-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="624e4-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="624e4-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="624e4-118">See Also</span></span>  
 [<span data-ttu-id="624e4-119">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="624e4-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
